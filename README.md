# YUTNGLE‑hook

🛡️ 一款适用于 KernelSU / APatch 的安卓防护模块

依靠 LD‑PRELOAD 动态库拦截 `rm`、`dd`、`unlinkat`、`renameat`等高风险破坏性系统调用。
开机自动扫描本地 Shell 脚本并且注入防护沙箱，卸载时自动回滚全部修改，不留残留。

## ✨功能清单
- 劫持 libc 系统调用，拦截删除、重命名、块设备写入等高危操作
- 开机自动扫描 `/data/adb`、`/data/local`、`/system/etc`目录下所有 `.sh`脚本，自动注入 LD‑PRELOAD
- 全部修改自动备份，卸载模块自动还原脚本原始内容
- 日志持久化输出：`/storage/emulated/0/Android/protect_log.txt`
- 防护模式：轻度模式 / Root完整防护模式自动切换
- KPM内核模块加载校验

## 📋ABI支持
- ✅ arm64‑v8a（AArch64）
- ✅ armeabi‑v7a
- ✅ armeabi（由armeabi‑v7a二进制兼容支持）
- ❌ x86 / x86_64 暂不支持

## 📌系统最低要求
- Android 7.0 （API‑24）及以上版本
- KernelSU / APatch（Magisk可运行用户态拦截逻辑，**KPM内核模块无法使用**）

## 📥安装方式
1. 下载本项目 Release 发布的模块zip安装包
2. KernelSU / APatch模块页面选择刷入zip
3. 重启设备
4. 查看日志：`/storage/emulated/0/Android/protect_log.txt`

## ⚠️注意事项
1. 当前仅提供arm64‑v8a编译产物，32位版本需要自行编译补充
2. LD‑PRELOAD只能拦截用户态进程，无法拦截内核态行为
3. 32位程序没有对应so库的时候可以绕过防护
4. 直接命令行执行的一次性shell指令不会被脚本注入逻辑覆盖


## ✨开机保护
1.如果手机安装了格机模块，该防护模块会拦截格机，在拦截格机的过程中，开机时间会变长一点，所有防护开机直接生效，如果要关闭防护，卸载模块即可


## 📞联系方式
作者QQ：3891131966
作者微信：He_Lan123456
