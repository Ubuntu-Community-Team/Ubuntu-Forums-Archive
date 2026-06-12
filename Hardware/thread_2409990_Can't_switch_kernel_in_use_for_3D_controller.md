---
title: "Can't switch kernel in use for 3D controller"
date: 2019-01-09
forum: Hardware
---

### Post by talgatbaytleu on 2019-01-09
Hi guys,
I'm using Ubuntu 18.04. I have installed NVidia drivers-384 (I tried this version cause others also did't work). And now I've got several problems:

1) (GeForce MX150) NVidia X-server doesn't display all settings:
[ATTACH=CONFIG]282158[/ATTACH]

2) 3D controller: NVIDIA Corporation GP108M [GeForce MX150] (rev a1)Subsystem: Acer Incorporated [ALI] GP108M [GeForce MX150]
Kernel driver in use: nouveau
Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

Should nvidia module be in use?

I already tried:
$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo update-initramfs -u
$ sudo reboot

P/S don't be strict, I'm a rookie in Linux world:)

---

### Post by talgatbaytleu on 2019-01-16
[COLOR=#000000][FONT=Verdana]Okey, I've solved this issue myself[/FONT][/COLOR][COLOR=#000000]:)

[/COLOR][COLOR=#000000][FONT=Verdana]Soo... I'll left my solution here step by step:[/FONT][/COLOR][COLOR=#000000]

[/COLOR][B][FONT=Verdana]1) Firstly insert the nouveau into the blacklist:
[/FONT][/B][FONT=menlo, monaco, monospace][COLOR=#000000]
[/COLOR][/FONT][FONT=menlo, monaco, monospace][COLOR=#000000]$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

[/COLOR][/FONT][B][COLOR=#000000][FONT=&quot]Confirm the content of the new modprobe config file:
[/FONT][/COLOR][/B][FONT=menlo, monaco, monospace][COLOR=#000000]
$ cat /etc/modprobe.d/blacklist-nvidia-nouveau.conf
blacklist nouveau
options nouveau modeset=0
$ sudo update-initramfs -u
$ sudo reboot

[/COLOR][/FONT][B]2)Then find out corresponding drivers on [https://www.nvidia.ru/Download/index.aspx?lang=ru](https://www.nvidia.ru/Download/index.aspx?lang=ru) and download .run file
(It's [/B][FONT=menlo, monaco, monospace][COLOR=#000000]**convenient to save it **[/COLOR][/FONT][B]home directory.)

[/B][B]3)After that ran UEFI(BIOS) and disable "secure boot" cause it interrupted NVidia drivers to be installed.

[/B][B]4)Install prerequisites:

[/B]$ sudo dpkg --add-architecture i386
$ sudo apt update
$ sudo apt install build-essential libc6:i386
[B]
5)Reboot the system before next step. Then change to runlevel 3 ([/B]After executing the following linux command [COLOR=#000000][FONT=&quot]the display server will stop, therefore make sure you save all your current work ( if any ) before you proceed)[/FONT][/COLOR][B]:
[/B]
$ sudo telinit 3

Press ALT+CTRL+F1 then opened TTY1 session and logged in.

Then start installation of NVIDIA:

$ sudo bash NV..(tab)

Confirme all. After installation done reboot the system. Then configure NVidia-X-Server.

P/S: As I already said I'm a newbie and I just described my way of solution for my hardware. Try it if you want, Good Luck!!!:):):)

---

### Post by talgatbaytleu on 2019-02-02
also do NOT forget to lock drivers in order to avoid updates.

[COLOR=#2F4F4F][FONT=monospace]sudo apt-mark hold nvidia-410 (your version)[/FONT][/COLOR]

---

### Post by talgatbaytleu on 2019-02-02
also do NOT forget to lock drivers in order to avoid updates.

[COLOR=#2F4F4F][FONT=monospace]sudo apt-mark hold nvidia-410 (your version)[/FONT][/COLOR]

---

