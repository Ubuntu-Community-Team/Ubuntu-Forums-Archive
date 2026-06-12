---
title: "Nvidia Optimus(vsync issue) on Ubuntu 16.04."
date: 2016-04-22
forum: Hardware
---

### Post by hectorsales on 2016-04-22
Hi, I have installed Ubuntu 16.04 version for two weeks .. and I have not managed to run nvidia drivers correctly. I tried with bumblebee (loop at login) and nvidia-prime (vsync issue).

[SIZE=3]**A) Bumblebee(decapreted way on ubuntu 16.04, the project is not update since 2013).**[/SIZE]

**1 Step: Install bumblebee and nvidia.**

```
$ Sudo apt-get install nvidia-bumblebee bumblebee primus nvidia nvidia-settings-361


```

**Step 2: Edit the file /etc/modules.**

> add

i915
bbswitch



**Step 3: Edit the file /etc/modprobe.d/bumblebee.conf.**

> # 361
blacklist nvidia-361
nvidia-361-blacklist updates
nvidia-experimental blacklist-361



**Step 4: edit the file /etc/bumblebee/bumblebee.conf.**

# (See also the driver-specific sections below)
**Driver = nvidia**
.......................................... ..
Section ## With nvidia driver specific options, only parsed if Driver = nvidia
[Driver-nvidia]
# Module name to load, defaults to empty or unset if Driver
**KernelDriver = nvidia-361**
PMMethod = auto
# Colon-separated path to the nvidia libraries
**LibraryPath = /usr/lib/nvidia-361:/usr/lib32/nvidia-361**
# Comma-separated path of the directory and the container containing nvidia_drv.so
# Default Xorg modules path
**XorgModulePath = /usr/lib/nvidia-361/xorg,/usr/lib/xorg/modules**
XorgConfFile = /etc/bumblebee/xorg.conf.nvidia

**Step 5:**

```
$ sudo gpasswd -a $ USER bumblebee


```
[B]
Step 6:[/B]

```
$ sudo enable systemctl bumblebeed


```
[B]
Step 7:[/B]

```
$ sudo reboot


```


[B]I try login but i can not do (login loop)...Curiously, this method worked for me with Ubuntu 15.10, with the same nvidia-driver version.
[/B]
**[SIZE=3]B) Nvidia-Prime (Methode recommend).[/SIZE]**

```
$ sudo apt-get install nvidia-361 nvidia-prime
```

Login succes but when i switch to nvidia card (from nvidia-settings),  awful tearing.

I have investigate ..and i have bad news..:icon_frown::icon_frown:

Patched are comming ..but we need kernel 4.5, xorg patch (1.19) and nvidia patch.

[https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/3](https://devtalk.nvidia.com/default/topic/775691/linux/vsync-issue-nvidia-prime-ux32vd-with-gt620-m-/3)


Regards.

---

### Post by anon24 on 2016-04-22
This seems to be related to my thread as well. I am also getting really bad tearing. 

I'm not sure what bumblebee is or what it does. I've asked a few times on my thread and no one seems to answer.

I hope that Nvidia actually does  get on this. It's extremely distracted.

It'd be nice if the driver and Nvidia X Server Settings just worked without tearing instead of having to type in a bunch of lines of code in order to get it to work. :/

Hell, when I change over to Intel for power saving mode there is no tearing whatsoever.

Oh well, hopefully we'll get to that point soon.

---

