---
title: "Ubuntu Freezing at Random times"
date: 2005-11-30
forum: General Help
---

### Post by aznboi on 2005-11-30
Hi. I have an IBM thinkpad with Ubuntu on it, and at random times, ubuntu wil just freeze and i cant move anything. The mouse stops moving everythig stops. I have to reboot and that is very annoying. Anyone have any ideas? Thnx

---

### Post by Qrk on 2005-11-30
Try ctrl-alt-backspace to restart X. Its easier than rebooting. 

Your problem may be helped by a different x.org driver. Of course, the issue may be elsewhere too, but the underlying Linux system usually quite stable.

---

### Post by aznboi on 2005-11-30
ok next time it freezes on me i will try that. Thnx

---

### Post by aznboi on 2005-12-01
My ubuntu just froze again, and i tried the CTRL+ALT+backspace and it didnt work. Thnx anyways tho, any other ideas?

---

### Post by aysiu on 2005-12-01
How much RAM do you have?

Regardless of the answer, you may want to look into XFCE--as a lightweight desktop environment, it doesn't suck up as much RAM, and it's also more stable than Gnome or KDE.

---

### Post by aznboi on 2005-12-01
i have 256... ill look into XFCE thnx.

---

### Post by aznboi on 2005-12-09
i tried xfce, but my system still freezes at random times... i guess ill have to reinstall ubuntu....

---

### Post by DrBair on 2005-12-09
Can you post the device section of xorg.conf file? I had a similar problem on my thinkpad and it was due to an option on the radeon driver.

---

### Post by doitashimashite on 2005-12-09
If you re-install, try to enter this parameter at boottime:

noapic nolapic

Good luck!

("Good luck" not being part of the parameter ;-)

---

### Post by kaamos on 2005-12-09
I had this on a Dell with dma issues.. Never got the dma-thing fixed, but "dpkg-reconfigure linux-image-$(uname -r)" solved the freezing completely. So you might want to try this..

Good luck, and I hope this helps!

---

### Post by aznboi on 2005-12-09
[QUOTE=DrBair]Can you post the device section of xorg.conf file? I had a similar problem on my thinkpad and it was due to an option on the radeon driver.[/QUOTE]

how do i do this? I'm sitll quite a bit of a n00b lol.

same goes for this post lol
> If you re-install, try to enter this parameter at boottime:

noapic nolapic

> I had this on a Dell with dma issues.. Never got the dma-thing fixed, but "dpkg-reconfigure linux-image-$(uname -r)" solved the freezing completely. So you might want to try this..

Good luck, and I hope this helps!

ill try that now thnx


Thnx alot for everyone's help

---

### Post by arctic on 2005-12-09
It is a kernel bug related to dma/udma problems resulting in dma-timeouts and sometimes constant freezes. It is already assigned for the kernel-dev team.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=19865](http://bugzilla.ubuntu.com/show_bug.cgi?id=19865)

---

### Post by aznboi on 2005-12-09
did this:
```
dpkg-reconfigure linux-image-$(uname -r)
```, seemed like it was working, then just a couple minutes ago it froze on me! i think ill reinstall ubuntu some time soon...ugh

---

### Post by aznboi on 2005-12-09
[QUOTE=arctic]It is a kernel bug related to dma/udma problems resulting in dma-timeouts and sometimes constant freezes. It is already assigned for the kernel-dev team.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=19865](http://bugzilla.ubuntu.com/show_bug.cgi?id=19865)[/QUOTE]

read some of that, but havent found any fixes... do u kno of any?

---

### Post by Lux Perpetua on 2005-12-10
[QUOTE=DrBair]Can you post the device section of xorg.conf file? I had a similar problem on my thinkpad and it was due to an option on the radeon driver.[/QUOTE]Would you mind elaborating on this? I've had the same problem on my ThinkPad, and I narrowed it down to something graphics card/driver related. 

aznboi, are you using one of the fglrx drivers by any chance? Regarding xorg.conf, you should have a text file **/etc/X11/xorg.conf** on your system. That file contains one or more sections that look like ```
Section "Device"
...
EndSection
```Open that file in gedit or your favorite text editor and post all of the "Device" sections. 
[QUOTE=arctic]It is a kernel bug related to dma/udma problems resulting in dma-timeouts and sometimes constant freezes. It is already assigned for the kernel-dev team.
[http://bugzilla.ubuntu.com/show_bug.cgi?id=19865](http://bugzilla.ubuntu.com/show_bug.cgi?id=19865)[/QUOTE]It looks like that bug is hard drive-related...is this correct? In my case, the hard drive wasn't the problem. I was able to log into my laptop from another computer and access my files, all while the screen was frozen solid.

---

### Post by kaamos on 2005-12-10
[QUOTE=aznboi]read some of that, but havent found any fixes... do u kno of any?[/QUOTE]

You could try editing the hdparm.conf file (sudo gedit /etc/hdparm.conf) and disabling dma for all your hard drives. Like this:
```

/dev/hda {
	dma = off
}

```
If you have two drives just add the same for hdb and so on.. This is not a "real" solution, but I might get the system to be stable. And help you figure out what is causing these freezes. Also check if you have any dma-related errors in "dmesg | grep DMA" or "cat /var/log/messages | grep DMA"

By the way, does anyone know if this bug has been fixed in the newer kernel versions?

---

### Post by aznboi on 2005-12-10
^^ thnx will try that

---

### Post by arctic on 2005-12-10
> By the way, does anyone know if this bug has been fixed in the newer kernel versions?It is not solved. Take a look at the dates in the bugzilla-log and you will see that it was just assigned to the kernel-dev team some days ago.
> It looks like that bug is hard drive-related...is this correct? In my case, the hard drive wasn't the problem. I was able to log into my laptop from another computer and access my files, all while the screen was frozen solid.Yes, that bug is harddisk/kernel related. Check your /var/log/messages folder in order to find out if your problem is really hdd related or if it is a prob with Xorg, as you claim.

---

### Post by damp on 2005-12-10
I'm experiencing something similar with a Dell Latitude C600 notebook.  The "freezing" seems to happen during disk access.  I've only noticed it in X/Gnome.  I've run Gentoo and Slackware Linux on this laptop without problems, so I'm thinking that it's a dma/ide driver... of course, there's no kernel source installed by default... and lots of loaded modules.  :D

More as it develops.

-damp-

---

### Post by Lux Perpetua on 2005-12-10
[QUOTE=arctic]Yes, that bug is harddisk/kernel related. Check your /var/log/messages folder in order to find out if your problem is really hdd related or if it is a prob with Xorg, as you claim.[/QUOTE]It still freezes randomly (infrequently), but I can reproduce the freeze by System Tools->New Login->Cancel, and then run "glxinfo" from a console. Freezes every time, but only if ATI's proprietary fglrx driver is in use. (Sorry, this is still Hoary; hopefully, it doesn't make too much of a difference.)

---

### Post by damp on 2005-12-11
The problem was the cpu scaling modules.  Removed them all and boom.  Problem averted.  "Problem solved" would include making use of the cpu frequency scaling to save battery power.

---

### Post by etola on 2005-12-11
> The problem was the cpu scaling modules. Removed them all and boom. Problem averted. "Problem solved" would include making use of the cpu frequency scaling to save battery power.

and how did you did that ?

---

### Post by arctic on 2005-12-18
[QUOTE=arctic]It is not solved. Take a look at the dates in the bugzilla-log and you will see that it was just assigned to the kernel-dev team some days ago.
[/QUOTE]Bug has been fixed in 2.6.15 kernel, now available for Dapper Flight 2. Update at your own risk.

---

### Post by TudorB on 2005-12-24
A how to on freezes would be cool!

---

### Post by mayankgarg1 on 2005-12-25
Hi everybody
I hv upgraded my 5.04 to 5.10 yesterday and after that I face these problems
1 Screen resolution max avaliable is 1024*768, Icould not get 1280*800 or any other even i have tried to reconfigure xorg.conf.
System gives error message Postinst customisation will change.
2  Synaptic, Disks-admin, users-admin freezes after giveing root password in "run as diff User"
Please help

---

### Post by mike123456 on 2005-12-25
I am having similar problem when i try to run my vimicro usb webcam from gnome messenger,it locks up and nothing moves,would anyone know how i can get my webcam to work?

---

