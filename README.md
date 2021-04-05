# chipsec-test

## Intro

本项目是 Intel Chipsec 测试环境搭建方法记录，基于 [v1.6.0](https://github.com/chipsec/chipsec/archive/refs/tags/1.6.0.zip) 版本

## Completed Package

为方便测试，这里有成品可供取用

### UEFI drive

将U盘格式化成 FAT32 后，将 [chipsec-uefi.zip]() 解压到U盘根目录

[Basic Usage](https://chipsec.github.io/Running-Chipsec.html#running-chipsec)

### Windows package

[chipsec-win.zip]()

[Basic Usage](https://chipsec.github.io/Running-Chipsec.html#running-chipsec)

## Building steps

### UEFI drive building

1. 格式化U盘成FAT32格式
2. 在U盘中新建路径 `/efi/boot`
3. 下载文件 `https://github.com/tianocore/edk2/blob/UDK2018/ShellBinPkg/UefiShell/X64/Shell.efi`
4. 重命名 `Shell.efi` 为 `Bootx64.efi` 并放到 `/efi/boot` 路径
5. 解压 `__install__/UEFI/chipsec_uefi_[x64|i586|IA32].zip` 到U盘根目录
6. 解压 [Chipsec](https://github.com/chipsec/chipsec/archive/refs/tags/1.6.0.zip) 到U盘

### Windows Installation (depend on network)

**安装依赖**

1. 安装 [Python3.7](https://www.python.org/ftp/python/3.7.9/python-3.7.9-amd64.exe) 或更高版本，建议勾选“Add Python to PATH”
2. 安装 Python 库,（CMD执行以下命令）
>```
>pip install pywin32
>pip install setuptools
>```
3. 下载安装 [Visual Studio](https://visualstudio.microsoft.com/zh-hans/thank-you-downloading-visual-studio/?sku=Community&rel=16#)，选择并安装“使用 C++ 的桌面开发”工作负荷，会自动包含 Windows SDK
4. Update Windows SDK to [10.0.19041.16385](https://go.microsoft.com/fwlink/p/?linkid=2120843)（可选）
5. Install [Windows Driver Kit](https://go.microsoft.com/fwlink/?linkid=2128854)
6. 安装 Spectre 缓解库
>在 Visual Studio 中勾选单个组件 `Spectre 缓解库` 安装
>```
>例如：
>中文版 MSVC v142 - VS 2019 C++ x64/x86 Spectre 缓解库
>英文版 MSVC v142 - VS 2019 C++ x64/x86 Spctre-mitigated libs
>```

**Building**

1. [获取软件包](https://github.com/chipsec/chipsec/archive/refs/tags/1.6.0.zip)
2. 管理员运行 CMD 进入软件包目录，执行 `python setup.py build_ext -i`

### Reference

https://chipsec.github.io

### Feedback

hi # raoyi.net

### License

遵从 EDK II、Intel Chipsec、Microsoft Visual Studio、WDK 等项目原有的许可条款