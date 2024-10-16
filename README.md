# Trick

## 1. Using a Proxy to Download Hugging Face Models in Mainland China

In Mainland China, accessing Hugging Face models can be problematic due to connection issues. To overcome this, you can modify Hugging Face's `file_download.py` file to use a proxy, allowing seamless model downloads.

This guide explains how to modify the file located in your Python virtual environment's `huggingface_hub` package.

### Steps:

#### 1. Locate the `file_download.py` File

You need to find the file in your Python environment. If you're using a virtual environment, you can locate it with the following path:

```cmd
<Virtual Environment Path>/Lib/site-packages/huggingface_hub/file_download.py
```

Make sure to replace `<Virtual Environment Path>` with the path of your actual Python environment.

For example, on Windows:

```
C:\path\to\your\env\Lib\site-packages\huggingface_hub\file_download.py
```

On Linux or macOS:

```bash
/path/to/your/env/lib/pythonX.X/site-packages/huggingface_hub/file_download.py
```

#### 2. Modify `file_download.py` to Use a Proxy

Once you've located the file, you need to add proxy settings to the download code. Open `file_download.py` in an editor and locate the portion of code where the model is downloaded using `requests.get()`.

Add the following lines to set up a proxy:

```python
proxies = {
    "http": "http://your_proxy_address:port",
    "https": "http://your_proxy_address:port"
}

response = requests.get(url, proxies=proxies, ...)
```

Replace `"http://your_proxy_address:port"` with your actual proxy server address and port.

For example:

```python
proxies = {
    "http": "http://127.0.0.1:7890",
    "https": "http://127.0.0.1:7890"
}
```

This configuration allows `requests` to route through the proxy when downloading the model.

#### 3. Save the Changes

After modifying the file, save your changes and close the editor.

#### 4. Verify the Setup

To verify that the modification works, try downloading a model from Hugging Face using the modified environment. The requests should now go through the proxy, allowing you to bypass any connectivity restrictions.