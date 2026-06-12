---
title: "bumblebee on dell xps17 l702x (15.04)"
date: 2015-05-12
forum: Hardware
---

### Post by tom183 on 2015-05-12
I installed bumblebee using
```
$ sudo apt-get install bumblebee bumblebee-nvidia
```
then rebooted

when running 
```
$ optirun glxgears
```
for the first time lightdm crashed and restarted
before lightdm restarted there was a message "[COLOR=#000000]Starting ACPI daemon"

[/COLOR]I blacklisted the intel driver
after that lightdm would not restart after crashing sitting at the service start screen or whatever you call that

I tried several versions of the nvidia driver and nouveau
rebooting and purging many times

Disheartened, about to give up, I notice something on the boot screen:
ACPI PCC probe failed

After a brief google session and several failed fixes I updated the kernel to version 4.0 and rebooted

The computer booted into desktop but with only 1024x786 resolution instead of the native 1200x900
Optimistically, i start up a terminal and type
```
$ optirun glxgears
```

Behold, it works, running with 900 or so fps

After some more googling i find if I run Xdiagnose it should resolve my resolution error
It does

bumblebee stops working
same error as before
one sleepless night, back where I started (minus ACPI PCC probe failed)

Any tips anyone can give me would be greatly appreciated
I can post outputs later on in the day when I get back to my computer but I dont know what will be useful

---

### Post by tom183 on 2015-05-14
So I managed to fix this.

```
sudo apt-get remove --purge nvidia-* bumblebee bumblebee-nvidia xserver-xorg-video-nouveau
```

I then removed the new version of the kernel I installed and installed the original standard version
rebooted

```
sudo apt-get install nvidia-current bumblebee bumblebee-nvidia
ls /usr/lib/nv*
 this returned:
 nvidia nvidia-304
sudo vi /etc/bumblebee/bumblebee.conf
```
change all references of 'nvidia-current' to 'nvidia-304'

reboot

It appears that the nvidia-current package installs a driver named 'nvidia-304' and not a driver named 'nvidia-current'
I first tried several of the newer drivers that just gave me trouble before eventually deciding to just go with what is standard.

The 'ACPI PCC probe failed' message returned after downgrading the kernel back to the default installed version but doesnt appear to affect performance or the ability to use the discreet card

---

