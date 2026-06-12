---
title: "Toshiba laptop won't reboot until Battery removed"
date: 2009-05-07
forum: Hardware
---

### Post by mikeincal on 2009-05-07
Hello all,

I am encountering an issue with an older Toshiba laptop model # P25-s676. It has a 3.4 P4 and 1 GB of Ram at the moment and also has a Nvidia GOforce 5700 video card on top of the typical stuff (wireless, IR, DVD, etc) that you would find in a laptop.

The problem is that after installing Ubuntu (tried versions 7.10, 8.04, 8.10, and lastly 9.04) the computer will not reboot or power down successfully. When it shuts down the PC will not reboot until ALL power is removed, including the battery. The only thing that occurs upon starting the PC is the power button will light up. No HD indicators or screen lights will. I always get one chance to turn it on after removing power before this happens. I have tried the laptop on battery only and also with the wireless off. Everything else seems to work, though I can never concentrate on the fine details due to this odd problem. The BIOS on this model is extremely limited and does not have the feature set of most BIOSs.

I have searched the Internet and have found this issue mentioned, but absolutely no resolutions to this.

I must note that the Windows partition does not experience this issue and reboots as expected. I have installed Ubuntu on numerous computers and have been able to overcome every issue that I have encountered, until now.

Anything would help at this point, Thanks!!

---

### Post by chellrose on 2009-05-07
Can you shut it down by holding the power button?  Can you then reboot it the same way?

If so, you might check here:

[http://ubuntuforums.org/archive/index.php/t-628109.html](http://ubuntuforums.org/archive/index.php/t-628109.html)

See if you can view it.  It's bringing up a blank page on my machine. :(

But, I had the same problem on my Toshiba when I installed 8.04.  Let me see if I can dig up the steps I took to fix it...

I'd advise against taking out the battery while the power is on. :)

---

### Post by mikeincal on 2009-05-07
Hi,

I can shut the laptop down by holding down the power button, but the subsequent power ups result in the same semi-dead state as before. It happens on cold and warm boots after the initial shut down from Ubuntu.

Strangely enough the link that you provided is also blank for me as well. :o

---

### Post by chellrose on 2009-05-07
OK, it sounds like you may be having the same problem I was experiencing.

What version of Ubuntu are you currently using, BTW?

Can you post the kernel list from /boot/grub/menu.lst?  That is, the section that begins with something like

```

title           Ubuntu 9.04, kernel 2.6.28-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=b477687b-33c6-4f36-a5e6-c3dbfee10e7c ro quiet splash rootflags=data=writeback 
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

```

... and from there to the end of the file.  You should have a couple of Ubuntu kernels as well as a Windows listing.

(or it may start with something similar for Windows, depending which is your default boot OS.)

---

### Post by mikeincal on 2009-05-07
I am currently running 9.04, please see the OS list below from my menu.lst.

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		abc30fc6-fac3-4b0f-a283-b329852241b9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=abc30fc6-fac3-4b0f-a283-b329852241b9 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		abc30fc6-fac3-4b0f-a283-b329852241b9
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=abc30fc6-fac3-4b0f-a283-b329852241b9 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		abc30fc6-fac3-4b0f-a283-b329852241b9
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by chellrose on 2009-05-07
Great, thanks for the additional info.

Back up your /boot/grub/menu.lst and /etc/modules files first.  (Just in case.)  E.g.

```

sudo cp /boot/grub/menu.lst ~/menu.lst.bak
sudo cp /etc/modules ~/modules.bak

```

Then:

1. In the line beginning with "kernel" for your FIRST kernel above, add to the end of the line "rootflags=data=writeback".  Don't change the others.  So the first entry would now look like

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        abc30fc6-fac3-4b0f-a283-b329852241b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=abc30fc6-fac3-4b0f-a283-b329852241b9 ro quiet splash [COLOR=Magenta]rootflags=data=writeback[/COLOR]
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```

Then, add to the end of your /etc/modules file the line

```

apm power_off=1

```

After that, see if reboot works properly.  Note that you may have to reboot it once to get it to recognize the changes, so if your first reboot doesn't work, try it one more time.  Hopefully it will see them the first time, though.

If that doesn't work at all, then I know of one more thing to try.

---

### Post by mikeincal on 2009-05-07
Gave it a shot and dropped those lines in and rebooted a few times.

Do you have that one more thing handy?:)

---

### Post by chellrose on 2009-05-07
It didn't work?  :(

I was able to dig up a Google-cached version of the page I tried to post initially.  This is what fixed the problem initially for me, but after a kernel upgrade I had to change it to the rootflags version.

Anyhow, in your /boot/grub/menu.lst file... go to that first kernel listing again, and replace "rootflags=data=writeback" with "acpi=off apm=power_off".  So...

```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        abc30fc6-fac3-4b0f-a283-b329852241b9
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=abc30fc6-fac3-4b0f-a283-b329852241b9 ro quiet splash [COLOR=Magenta]acpi=off apm=power_off[/COLOR]
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

```

Don't change anything in /etc/modules; it should still have the line "apm power_off=1".

Here's the Google-cache version of that original page; see the third post.
[http://209.85.173.132/search?q=cache:hHgQmd-ClZ4J:ubuntuforums.org/archive/index.php/t-628109.html+%22hardy+shutdown+doesn%27t%22+AND+%22does+not+power+off%22&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a](http://209.85.173.132/search?q=cache:hHgQmd-ClZ4J:ubuntuforums.org/archive/index.php/t-628109.html+%22hardy+shutdown+doesn%27t%22+AND+%22does+not+power+off%22&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)

Keep in mind that this was written for Hardy... but my /boot/grub/menu.lst file hasn't changed since the upgrade to Jaunty, and I haven't encountered any problems.

Crossing my fingers. :)

---

### Post by mikeincal on 2009-05-07
Well gave it a shot, and unfortunately it didn't work. I read through the bug report and couldn't find anything else related.

Thank you for your help so far. If you have anything else up your sleeve I'd love to hear it. Oddly enough my other Toshiba (L25-S119) works just fine but it is quite a bit different.

Time to close up and try again in the a.m.:D

---

### Post by chellrose on 2009-05-07
That's odd.

Did you just install Jaunty on your laptop, or did you have an older version first, then do an upgrade?  If the latter, did reboot work on your older version of Ubuntu?

This may sound dumb, but does ordinary shutdown work properly?  If so... it's a bit of a pain, but that may be a good temporary workaround -- just use shutdown and then hit the power button to bring it back up.

Otherwise, I'm out of ideas right now, and a quick Google search didn't turn up anything either.  But, I will let you know if I come across anything else.

Sorry I couldn't be more helpful. :(

Good luck.

---

### Post by mikeincal on 2009-05-08
I agree completely odd.

I have tried numerous versions on this laptop over the last couple of years, and have done complete installs each time. Nothing has worked and I have tried each released version on this since 7.10.

Unfortunately it affects both a reboot and a shutdown/power up procedure. I can shut it down and come back to it a week later and when I turn it on, nothing but a blue power button.

I am dumbfounded as to why Ubuntu would interfere with something as simple as a power down and a power up. I would imagine that the BIOS should at least handle the power up sequence. It would make more sense to me if I could boot up normally and Ubuntu would fail to load. What kills me is that the Windows partition does not exhibit this issue.

Thank you for your help it was certainly most appreciated. :KS

---

### Post by RogerLK on 2009-11-14
I just came across this thread after searching for a solution for my problem. I had experienced an issue similar to what mikeincal describes with a Toshiba NB205 netbook. The original XP installation had no problem shutting the system down and then reboot by switching the netbook back on, or directly restarting with "restart". I was not able to do any of this with either Jaunty or Karmic. Shutdown always worked. A restart of the system always resulted in a total hang at the initial BIOS splash screen. So did a power on after the system had just been shut down. The only thing to boot the system again, was either to remove external power and battery and let the netbook sit for at least 10 minutes (after which time it would start up normally), or just wait long enough (= over night) before switching the system back on.
I have read this thread and have tried all suggestions - to no avail. Finally, it occurred to me that this may be more of a hardware/firmware problem than a problem with the OS. I searched the Toshiba support pages and found that the BIOS version in my netbook was the first official release and had since been updated twice (let that sink in, I own the netbook for only 3 weeks now, there is possibly a huge number of those out there in stores with the original BIOS). Between my 1.20 version and the updates to 1.50 and then 1.60 was a whole laundry list of changes, including several specifically geared towards Linux. 

Long story short:
I downloaded the BIOS image, flashed the new version into my computer and all shutdown/reboot/restart problems were completely gone. Since the update I have run at least 50 restart and shutdown/reboot cycles (for no other reason than to try) and didn't have a single problem. I will likely not remove the battery again until it needs to be replaced...

Conclusion 1: everybody (including myself) is always quick to blame the OS for problems (it did work with Windows, didn't it?) What must be understood, though, is that hardware manufacturers focus their work on Windows and provide all the necessary proprietary drivers to make even hardware with flawed firmware work. A shoddy BIOS may then not appear as such - unless you load an OS that does not have the luxury of direct driver support from the hardware maker. I have to say thanks to Toshiba for fixing the BIOS problems, rather than just considering it fixed with WIN drivers.

Conclusion 2: if there is a boot problem that clearly occurs before the OS specific functions can kick in (or even then): check your BIOS version and compare to the latest release from the manufacturer. Updating to the latest version may save some headaches later... Even if the latest BIOS is already a few years old - it may still be much younger than what's working in your computer.

Enough said!

---

