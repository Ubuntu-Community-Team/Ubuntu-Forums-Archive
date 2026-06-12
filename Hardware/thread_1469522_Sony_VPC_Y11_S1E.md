---
title: "Sony VPC Y11 S1E"
date: 2010-05-02
forum: Hardware
---

### Post by mecrip on 2010-05-02
Hi there!

I have finally got lucid lynx working on this laptop and i'm posting a little guide about the current status:

what is not working out-of-the-box:
[LIST=1]
[*]Internal microphone
[*]Sound output
[*]headphones / speaker switching
[*]screen backlight brightness control
[*]screen flickering
[/LIST]
Everything else seems to work. Not bad for a new model.. i think that is just matter of time before everything will works correctly!

**audio**
The audio hardware is managed by hda-intel and i think that this configuration (reported as ALC275) is still not completely managed.
However, i got the sound output working by installing the latest linux-alsa-driver-modules-2.6.32-21-generic from the ubuntu-audio-dev ppa.
Just add the ppa from here and install the latest modules package with apt-get:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa")

Unfortunately the following bugs remain active:
[LIST]
[*]when i attach the headphones the speakers are not muted
[*]the internal microphone is not working
[/LIST]

**screen**
In the default configuration the screen sometimes has a flicker, it seem to depends on KMS. 
The solution is easy: 
just put the following parameters in /etc/default/grub to disable the splash screen and the KMS.
```
GRUB_CMDLINE_LINUX_DEFAULT="nosplash nomodeset"
```
After setting this just run ```
sudo update-grub
```
This will prevent the kernel from setting a high resolution mode for the console but it will disable the nice booting splash screen.

Regarding the backlight brightness it seem that the xorg video drivers for the intel gma aren't able to manage it. The keys fn+F5 and fn+F6 are correctly detected but no change happens in the brighness. The solution is provided here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2102075.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2102075.html")
Basically it will let ACPI to handle the fn+F5 and fn+F6 events. It will let you to manually set the brightness but it won't allow the gnome-power-manager to set it automatically so no idle-dimming or can occour.

---

