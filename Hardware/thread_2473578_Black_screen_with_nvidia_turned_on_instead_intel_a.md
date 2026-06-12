---
title: "Black screen with nvidia turned on instead intel and Failed to initialize NVML: Drive"
date: 2022-04-07
forum: Hardware
---

### Post by eluator on 2022-04-07
I have a problem on Ubuntu 20.04 with nvidia drivers. 


I started from the black screen ubuntu and it turned out that problem was in the memory overflow of logs (seems) and `sudo apt-get autoclean` worked. 


But during the problem solving I did something like this: `sudo apt purge *nvidia*`. After this I tried install nvidia driver by NVIDIA-Linux-x86_64-510.54.run which was download from official nvidia site. It didn't work and I also tried an installation with `apt` and `ubuntu drivers autoinstall`. Now I have black screen when I turned on nvidia but with `sudo prime-select intel` graphics works normally. 


When I call `nvidia-smi` I get `Failed to initialize NVML: Driver/library version mismatch` but this ([https://forums.developer.nvidia.com/t/failed-to-initialize-nvml-driver-library-version-mismatch/190421](https://forums.developer.nvidia.com/t/failed-to-initialize-nvml-driver-library-version-mismatch/190421)) decision doesn't work to me.


After this I tried [https://forums.developer.nvidia.com/t/failed-to-initialize-nvml-driver-library-version-mismatch/50910](https://forums.developer.nvidia.com/t/failed-to-initialize-nvml-driver-library-version-mismatch/50910) and gained good nvidia-smi answers with 510 driver and 11.6 cuda but Nvidia Geforce Off. But after rebooting I got black screen and nvidia-smi answers in console this: `NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.`


![bug-startx|665x499](upload://njqkfMYfkF4brQb7wnmF0BiLKJw.jpeg)


Also I have a problem with `sowtware & updates` application:
`software-properties-dbus crashed with request_unixsocket`
or `software-properties-gtk crashed with dbus-exceptions.` Reinstalling some packages like `python3-six`, `python3-certifi`, `python3-requests`, `python3-idna`, `python3-chardet`, `python3-urllib3` and `software-properties-gtk` doesn't work. `software-properties-qt` works but reinstalling drivers by it doesn't help with nvidia problem described above.


[nvidia-bug-report.log.gz|attachment](upload://18jyQ6Y9aKJIh9GaFkFaa2fKgoY.gz) (1.8 KB)


So because of this problem I can't use cuda for ML, please, help)

Upd.
[COLOR=#000000]Solution was found on the nvidia forum here:[/COLOR]
[https://forums.developer.nvidia.com/...ismatch/210594]("https://forums.developer.nvidia.com/t/black-screen-with-nvidia-turned-on-instead-intel-and-failed-to-initialize-nvml-driver-library-version-mismatch/210594")

---

### Post by #&amp;thj^% on 2022-04-07
My best suggestion from wisdom, purge all your downloaded nvidia drivers.
and run
```
ubuntu-drivers devices
```

---

### Post by eluator on 2022-04-07
I already tried [COLOR=#525252][FONT=Consolas]sudo apt purge nvidia* libnvidia* and reinstalled cuda and `[/FONT][/COLOR]nvidia-driver-510`.
`ubuntu-drivers devices` gives this:
WARNING:root:_pkg_get_support nvidia-driver-510-server: package has invalid Support PBheader, cannot determine support level
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001F95sv00001028sd000009E1bc03sc00i00
vendor   : NVIDIA Corporation
manual_install: True
driver   : nvidia-driver-470-server - distro non-free
driver   : nvidia-driver-470 - distro non-free recommended
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-510-server - distro non-free
driver   : nvidia-driver-510 - third-party non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

---

### Post by #&amp;thj^% on 2022-04-07
Ok  we need to get on the same page here.
That warning that you are faced with looks like the downloaded driver (manual_install: True), and not the one from Ubuntu Repo's
I can't help you if we are doing two different methods.
BTW your recommended driver is : **nvidia-driver-470 - distro non-free recommended** and not 510.

---

### Post by eluator on 2022-04-07
Ok, sorry for stupid question but for verifying: how can I purely uninstall 510 and install 470?)
I'm slightly confusing because I can't see any deferences in [COLOR=#000000]ubuntu-drivers devices [/COLOR]when I delete 510 or install it

---

### Post by #&amp;thj^% on 2022-04-07
the above should work as well as an init3 session, killing X
<snipped poster vanished>
I may sound cryptic here, but you did install it right, the same way except:
```
sudo ./NVIDIA-Linux-x86-510.19.run --uninstall
```
To uninstall the CUDA Toolkit, run the uninstallation script provided in the bin directory of the toolkit. By default, it is located in /usr/local/cuda-11.0/bin:
Change all versions to what you now have. EG>NVIDIA-Linux-x86-5XX.19. and cuda-XX.0
```
sudo /usr/local/cuda-11.0/bin/cuda-uninstaller
```
To uninstall the NVIDIA Driver, run nvidia-uninstall:

```
sudo /usr/bin/nvidia-uninstall
```
I see your fairly new here, probably best to stay with all your software and drivers from what's in your package manager.
And one more to be safe:
```
sudo apt remove --purge '^nvidia-.*'
```
Reboot before you try to install the 470 driver.
If you agree with the recommendation feel free to use:
```
sudo ubuntu-drivers autoinstall
```
Good Luck

---

### Post by eluator on 2022-04-08
Hello) thank you very much for the detailed answer!
But I stuck with the cuda uninstall cause I have three cuda paths: cuda-11/   cuda-11.5/ cuda-11.6/ and noone has cuda-uninstaller in the bin directory.
cuda-11.6/bin direcory for example looks so:
usr/local/cuda-11.6/bin$ ls -la
total 86684
drwxr-xr-x  3 root root     4096 &#1072;&#1087;&#1088;  7 19:20 .
drwxr-xr-x 16 root root     4096 &#1072;&#1087;&#1088;  7 19:20 ..
-rwxr-xr-x  1 root root    88800 &#1084;&#1072;&#1088;  9 06:20 bin2c
lrwxrwxrwx  1 root root        4 &#1084;&#1072;&#1088;  9 05:54 computeprof -> nvvp
-rwxr-xr-x  1 root root      115 &#1084;&#1072;&#1088;  9 08:46 compute-sanitizer
drwxr-xr-x  2 root root     4096 &#1072;&#1087;&#1088;  7 19:19 crt
-rwxr-xr-x  1 root root  5957192 &#1084;&#1072;&#1088;  9 06:20 cudafe++
-rwxr-xr-x  1 root root 13585248 &#1084;&#1072;&#1088;  9 06:12 cuda-gdb
-rwxr-xr-x  1 root root   778360 &#1084;&#1072;&#1088;  9 06:12 cuda-gdbserver
-rwxr-xr-x  1 root root   356336 &#1084;&#1072;&#1088;  9 06:06 cuda-memcheck
-rwxr-xr-x  1 root root    75880 &#1084;&#1072;&#1088;  9 05:59 cu++filt
-rwxr-xr-x  1 root root   245072 &#1084;&#1072;&#1088;  9 06:27 cuobjdump
-rwxr-xr-x  1 root root   277600 &#1084;&#1072;&#1088;  9 06:20 fatbinary
-rwxr-xr-x  1 root root     2974 &#1084;&#1072;&#1088; 18 20:39 ncu
-rwxr-xr-x  1 root root     2577 &#1084;&#1072;&#1088; 18 20:39 ncu-ui
-rwxr-xr-x  1 root root     1580 &#1084;&#1072;&#1088;  9 06:02 nsight_ee_plugins_manage.sh
-rwxr-xr-x  1 root root       82 &#1084;&#1072;&#1088; 18 20:39 nsight-sys
-rwxr-xr-x  1 root root      751 &#1084;&#1072;&#1088; 18 20:39 nsys
-rwxr-xr-x  1 root root      104 &#1084;&#1072;&#1088; 18 20:39 nsys-exporter
-rwxr-xr-x  1 root root      739 &#1084;&#1072;&#1088; 18 20:39 nsys-ui
-rwxr-xr-x  1 root root  6477920 &#1084;&#1072;&#1088;  9 06:20 nvcc
-rwxr-xr-x  1 root root   654928 &#1084;&#1072;&#1088;  9 06:20 __nvcc_device_query
-rw-r--r--  1 root root      417 &#1084;&#1072;&#1088;  9 06:20 nvcc.profile
-rwxr-xr-x  1 root root 33542440 &#1084;&#1072;&#1088;  9 21:26 nvdisasm
-rwxr-xr-x  1 root root 10555496 &#1084;&#1072;&#1088;  9 06:20 nvlink
lrwxrwxrwx  1 root root        6 &#1084;&#1072;&#1088; 18 20:39 nv-nsight-cu -> ncu-ui
lrwxrwxrwx  1 root root        3 &#1084;&#1072;&#1088; 18 20:39 nv-nsight-cu-cli -> ncu
-rwxr-xr-x  1 root root  5677088 &#1084;&#1072;&#1088;  9 06:21 nvprof
-rwxr-xr-x  1 root root   109504 &#1084;&#1072;&#1088;  9 06:05 nvprune
-rwxr-xr-x  1 root root      285 &#1084;&#1072;&#1088;  9 05:54 nvvp
-rwxr-xr-x  1 root root 10299856 &#1084;&#1072;&#1088;  9 06:20 ptxas

---

### Post by #&amp;thj^% on 2022-04-08
> **eluator said:**
> Hello) thank you very much for the detailed answer!
But I stuck with the cuda uninstall cause I have three cuda paths: cuda-11/   cuda-11.5/ cuda-11.6/ and noone has cuda-uninstaller in the bin directory.
cuda-11.6/bin direcory for example looks so:
```
usr/local/cuda-11.6/bin$ ls -la
total 86684
drwxr-xr-x  3 root root     4096 &#1072;&#1087;&#1088;  7 19:20 .
drwxr-xr-x 16 root root     4096 &#1072;&#1087;&#1088;  7 19:20 ..
-rwxr-xr-x  1 root root    88800 &#1084;&#1072;&#1088;  9 06:20 bin2c
lrwxrwxrwx  1 root root        4 &#1084;&#1072;&#1088;  9 05:54 computeprof -> nvvp
-rwxr-xr-x  1 root root      115 &#1084;&#1072;&#1088;  9 08:46 compute-sanitizer
drwxr-xr-x  2 root root     4096 &#1072;&#1087;&#1088;  7 19:19 crt
-rwxr-xr-x  1 root root  5957192 &#1084;&#1072;&#1088;  9 06:20 cudafe++
-rwxr-xr-x  1 root root 13585248 &#1084;&#1072;&#1088;  9 06:12 cuda-gdb
-rwxr-xr-x  1 root root   778360 &#1084;&#1072;&#1088;  9 06:12 cuda-gdbserver
-rwxr-xr-x  1 root root   356336 &#1084;&#1072;&#1088;  9 06:06 cuda-memcheck
-rwxr-xr-x  1 root root    75880 &#1084;&#1072;&#1088;  9 05:59 cu++filt
-rwxr-xr-x  1 root root   245072 &#1084;&#1072;&#1088;  9 06:27 cuobjdump
-rwxr-xr-x  1 root root   277600 &#1084;&#1072;&#1088;  9 06:20 fatbinary
-rwxr-xr-x  1 root root     2974 &#1084;&#1072;&#1088; 18 20:39 ncu
-rwxr-xr-x  1 root root     2577 &#1084;&#1072;&#1088; 18 20:39 ncu-ui
-rwxr-xr-x  1 root root     1580 &#1084;&#1072;&#1088;  9 06:02 nsight_ee_plugins_manage.sh
-rwxr-xr-x  1 root root       82 &#1084;&#1072;&#1088; 18 20:39 nsight-sys
-rwxr-xr-x  1 root root      751 &#1084;&#1072;&#1088; 18 20:39 nsys
-rwxr-xr-x  1 root root      104 &#1084;&#1072;&#1088; 18 20:39 nsys-exporter
-rwxr-xr-x  1 root root      739 &#1084;&#1072;&#1088; 18 20:39 nsys-ui
-rwxr-xr-x  1 root root  6477920 &#1084;&#1072;&#1088;  9 06:20 nvcc
-rwxr-xr-x  1 root root   654928 &#1084;&#1072;&#1088;  9 06:20 __nvcc_device_query
-rw-r--r--  1 root root      417 &#1084;&#1072;&#1088;  9 06:20 nvcc.profile
-rwxr-xr-x  1 root root 33542440 &#1084;&#1072;&#1088;  9 21:26 nvdisasm
-rwxr-xr-x  1 root root 10555496 &#1084;&#1072;&#1088;  9 06:20 nvlink
lrwxrwxrwx  1 root root        6 &#1084;&#1072;&#1088; 18 20:39 nv-nsight-cu -> ncu-ui
lrwxrwxrwx  1 root root        3 &#1084;&#1072;&#1088; 18 20:39 nv-nsight-cu-cli -> ncu
-rwxr-xr-x  1 root root  5677088 &#1084;&#1072;&#1088;  9 06:21 nvprof
-rwxr-xr-x  1 root root   109504 &#1084;&#1072;&#1088;  9 06:05 nvprune
-rwxr-xr-x  1 root root      285 &#1084;&#1072;&#1088;  9 05:54 nvvp
-rwxr-xr-x  1 root root 10299856 &#1084;&#1072;&#1088;  9 06:20 ptxas
```

Most of us won't even bother reading text from the terminal without wrapping them in code tags like I just did for you.
See my signature to learn how to use **code tags**
What a mess you have there. (We all here have done things like this before)
I suggest you head back over to the Nvidia site for help now. (Or re-install your Os again, and start fresh)

---

### Post by eluator on 2022-04-09
I gor clean answer for the `dpkg -l |grep nvidia` and `ls -l /lib/x86_64-linux-gnu/*nvidia* /lib/x86_64-linux-gnu/libcuda*`and rebooted  but an error with Software&Updates happens again:

> sudo software-properties-gtk
ERROR:dbus.proxies:Introspect error on :1.98:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
File "/usr/bin/software-properties-gtk", line 100, in <module>
app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 222, in __init__
self.backend.Reload();
File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
return self._proxy_method(*args, **keywords)
File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 141, in __call__
return self._connection.call_blocking(self._named_service,
File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.98 was not provided by any .service files

I also tried to install drivers in the another ways:
1. `sudo ubuntu-drivers autoinstall` + [https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)
2. `sudo apt install nvidia-driver-510 nvidia-dkms-510` + [https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=20.04&target_type=deb_local)
But when I turned on nvidia the black screen appeared anyway.
I don't understand why in the nvidia cuda-downloads I can only get instruction for the installation of version 510 but `ubuntu-drivers autoinstall` gives me version 470.


Can you please help me again?)

---

### Post by #&amp;thj^% on 2022-04-09
No, CUDA 11.5 or higher is not compatible with your current configuration.
[list]
    [*]Remove CUDA 11.5 and Nvidia 470

    [*]Reinstalled Nvidia 470 using Software & Updates Additional Drivers tab

    [*]Install CUDA 11.4[/list]
@ eluator I'm not trying to brush you off, you have a mess that I will surely break your system with my suggestions.
The Nvidia forums would be the first place i went to for help.
My Best suggestion is to back-up all your personal and needed files, and start fresh and clean.
Then install the drivers from software manager. 
The cuda install can be solved after all that happens.>>>[https://gist.github.com/kmhofmann/cee7c0053da8cc09d62d74a6a4c1c5e4](https://gist.github.com/kmhofmann/cee7c0053da8cc09d62d74a6a4c1c5e4)

---

### Post by eluator on 2022-04-09
Ok, thank you! You already helped me alot)

---

### Post by eluator on 2022-04-12
Solution was found on the nvidia forum here:
[https://forums.developer.nvidia.com/t/black-screen-with-nvidia-turned-on-instead-intel-and-failed-to-initialize-nvml-driver-library-version-mismatch/210594](https://forums.developer.nvidia.com/t/black-screen-with-nvidia-turned-on-instead-intel-and-failed-to-initialize-nvml-driver-library-version-mismatch/210594)

---

### Post by #&amp;thj^% on 2022-04-12
> **eluator said:**
> Solution was found on the nvidia forum here:
[https://forums.developer.nvidia.com/t/black-screen-with-nvidia-turned-on-instead-intel-and-failed-to-initialize-nvml-driver-library-version-mismatch/210594](https://forums.developer.nvidia.com/t/black-screen-with-nvidia-turned-on-instead-intel-and-failed-to-initialize-nvml-driver-library-version-mismatch/210594)

Good Work eluator, also thanks for posting your solution.
Please consider marking this one as **[Solved]** this would help other seeking advise.

---

