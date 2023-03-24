# Mac从头开始环境搭建 stable-diffusion 
1、Mac基础环境
brew安装：为什么镜像也很慢！ 参考：https://www.cnblogs.com/wang715100018066/p/16460399.html
conda：使用conda activate sdwebui

2、hugging face模型下载：参考：https://zhuanlan.zhihu.com/p/475260268
7G的模型文件比较大，建议使用glf下载，不然会非常慢，而且容易中断


执行./webui.sh报错：

https://stackoverflow.com/questions/40183108/python-packages-hash-not-matching-whilst-installing-using-pip

【ERROR: THESE PACKAGES DO NOT MATCH THE HASHES FROM THE REQUIREMENTS FILE. If you have updated the package versions, please update the hashes. Otherwise, examine the package contents carefully; someone may have tampered with them.
    torch==1.12.1 from https://files.pythonhosted.org/packages/71/08/dc7e078f035d17c7cecc8cae81cc450827eb95cd59785346663aafb17d90/torch-1.12.1-cp39-none-macosx_10_9_x86_64.whl#sha256=bfec2843daa654f04fda23ba823af03e7b6f7650a873cdb726752d0e3718dada:
        Expected sha256 bfec2843daa654f04fda23ba823af03e7b6f7650a873cdb726752d0e3718dada
             Got        f46711b67a16500c10e51086b5736534a0dbebddf63a76f2d60b633ede364ecc】
             
             
             
 【ERROR: Wheel 'torch' located at /private/var/folders/y4/n7td2q0j17z05x_dh370gqb00000gn/T/pip-unpack-806lgvan/torch-1.12.1-cp310-none-macosx_10_9_x86_64.whl is invalid.】
 
解决： https://appdividend.com/2023/01/30/how-to-fix-error-torch-has-an-invalid-wheel-in-python/#:~:text=To%20fix%20the%20ERROR%3A%20torch%20has%20an%20invalid,command%3A%20pip%20install%20torch%3D%3D%3D1.7.0%20torchvision%3D%3D%3D0.8.1%20torchaudio%3D%3D%3D0.7.0%20-f%20https%3A%2F%2Fdownload.pytorch.org%2Fwhl%2Ftorch_stable.html

通过conda手动安装pytorch：
【CondaError: Downloaded bytes did not match Content-Length                       
  url: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/osx-64/pytorch-1.12.1-cpu_py310h32957a8_0.tar.bz2                                        
  target_path: /usr/local/anaconda3/pkgs/pytorch-1.12.1-cpu_py310h32957a8_0.tar.bz2                                                                             
  Content-Length: 62134524                                                      
  downloaded bytes: 48348922  】
超时添加镜像：
https://blog.csdn.net/feifei3211/article/details/80361227
https://www.bbsmax.com/A/KE5QDLwqJL/

【fatal: unable to access 'https://github.com/Stability-AI/stablediffusion.git/': HTTP/2 stream 1 was not closed cleanly before end of the underlying stream】
解决：修改launch.py:链接加上--http1.1
【    openclip_package = os.environ.get('OPENCLIP_PACKAGE', "git+https://github.com/mlfoundations/open_clip.git@bb6e834e9c70d9c27d0dc3ecedeebeaeb1ffad6b --http1.1")
】


最后！ 什么都不用改，就等等等！！！ 重试重试重试！！ 实在不行手动安装！！ 读launch.py文件！！！


ldm问题：
launc.py中几个clone的仓库都需要进入仓库根目录pip install -e .

参考文档：参考：https://www.bilibili.com/read/cv21908940?from=articleDetail
