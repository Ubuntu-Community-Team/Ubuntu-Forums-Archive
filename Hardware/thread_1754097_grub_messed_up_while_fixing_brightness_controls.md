---
title: "grub messed up while fixing brightness controls?"
date: 2011-05-09
forum: Hardware
---

### Post by caspian915 on 2011-05-09
Hi all,

I have a Samsung N145 netbook dual booting Windows 7 and Ubuntu 10.04 Netbook Remix, or rather, it *was* booting UNR until I tried to deal with the brightness controls issue. I followed [this thread]("http://ubuntuforums.org/showthread.php?t=1397371") which told me to check out [this thread]("http://ubuntuforums.org/showthread.php?t=1313390") (for Dell comps oddly) with a suggested work-around that I've reposted below. I backed up grub before making the change, made it and restarted, and now when I select Ubuntu in the boot menu, all I get a lonely, blinking cursor. Pressing enter just pushes it down the screen. 

I *can* but into "recovery mode", which brings me to a terminal prompt, and I can login from there. But I'm admittedly a noob with linux, so there's only so much I understand about the terminal right now. My guess is that I could access and re-edit grub from there, but since I first edited it via gedit (aka, in GUI mode), I have no idea what I'm doing.

1) Can someone help me quickly fix this? (or am I screwed and left no option but to boot to GParted Live CD and re-format/re-install Ubuntu?)

2) Can someone point me to a thread that helps me fix the brightness controls? I've tried searching for a way, followed one of the links in google, and the suggested answer screwed the pooch. This is a pitfall of searching first before just asking in the forums...

thanks,

- sps

*****************************************

This is what I followed:

> Open up the Terminal. Type:

     Code:
     sudo gedit /etc/default/grub 
to change the bootloader settings. Find the line that says:

     Quote:
                                                 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"                                 
and change it so it says:

     Quote:
                                                 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"                                 
(that's the letter "l", not the number "1").

Save and close the file.

Then run in the terminal:

     Code:
     sudo update-grub 
and then reboot and enjoy working brightness keys!

---

