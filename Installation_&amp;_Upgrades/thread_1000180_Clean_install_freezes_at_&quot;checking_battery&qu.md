---
title: "Clean install freezes at &quot;checking battery&quot; after first update."
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by MiD-AwE on 2008-12-02
Hi all,

I've completed a clean install of 8.10 and it appeared to install properly; I even installed the nvidia drivers. After I ran the first update, I was told to reboot, so I did. Now I can't boot into ubuntu 8.10. Everything starts as it should, I choose ubuntu from grub (I've even selected the previous kernal just  in case) but after the boot begins it freezes at "checking battery" I left this for over 30 minutes but still nothing.

I have no problem reinstalling but I don't expect any other results as I've tried this twice already.

What should I be doing to get beyond this?

AMD 64 x2 4600+ nvidia 6100 & 7600GS 2GB RAM (triple boot XP, Vista, ?Ubuntu?)

-this setup worked with 8.04 (although I've recently added third monitor, I have not attempted to configure X11 to use it)

:confused:

UPDATE: After digging around other forums I found a recommendation that worked for me. Thanks to Chuck Mahon, for this tidbit.

Do a LSPCI command and find the PCI Bus ID address for your NVIDIA card (your primary card if you have multiple cards
Add the BusID statement to your xorg.conf.

example:

Section "Device"
BusID "1:0:0" <-change to your PCI Bus ID - do not copy & paste
EndSection

Answer provided here: [http://www.ubuntugeek.com/common-pro...x-upgrade.html](http://www.ubuntugeek.com/common-pro...x-upgrade.html)

After following these instructions I was able to enable the nvidia restricted drivers without the "checking battery" freeze. 3D acceleration is working.

Hope this helps.

---

### Post by Partyboi2 on 2008-12-02
Have you tried adding some boot options? Try adding noapic or acpi=off if you have not already done so.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by MiD-AwE on 2008-12-03
> **Partyboi2 said:**
> Have you tried adding some boot options? Try adding noapic or acpi=off if you have not already done so.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Thanks Partyboi2, I gave your suggestion a try and still no good. This setup was working with 8.04. I only added the third display the adapter and all was already connected. I have, since your suggestion, switched to the xorg.conf.failsafe and still no change, system still hangs at "checking battery state".
 
I am going to reinstal 8.10 this time I'll not activate nvidia driver and then I reboot without installing updates, just to test if it is an update that is causing the freeze. If all goes well I'll instal all updates and reboot again. This should tell me if it is my display adapter for the third display causing the freeze somehow, or just 8.10. If it's 8.10 then I'll reinstal 8.04 and wait for the next release; unless, someone has another suggestion.

---

### Post by djohns505 on 2008-12-07
I am having this same problem.  After a clean install, I tried updating and then installing the nvidia drivers, tried versions 96, 173, and 177 all with the result, "checking battery state".

I wonder if it may be our setup.  Does yours match something like mine?  I suspect it may have something to do with the different cards types.  I have two 640MB 8800GTS's, however one is the SSC and the other is the orignal.  They are connected with the SLI bridge.  If your video setup is different from that, then maybe its a problem with the driver?

---

### Post by MiD-AwE on 2008-12-08
djohns505, I am using older hardware but I have read that as long as the cards use the same driver there should be no issue. We are both experiencing this problem so I assume it is a result of Ubuntu's apparent inability to utilize a multi-display adapter setup. I have heard other mention that they have successfully setup and used SLI with Ubuntu and my setup DID work with 8.04. It seems that this is an 8.10 issue but I am not able to narrow this to a point that I can successfully report a bug if it is.
 
Alberto Milone's website doesn't seem to have any mention of known issue similar to this we are experiencing. I hoping that someone else will see this thread and be able to provide some guidance.
 
I have a few other issues which may or may not be related. During a fresh install I setup all mount points as I normally would, but Ubuntu seems to have not accepted them because after the install finished no preset mounts exist. I'll have to remount them.
 
I did not reinstall the Nvidia non-free drivers and I have a working installation of Ubuntu utilizing only on of my three monitors and of coarse no opengl acceleration.

---

### Post by MiD-AwE on 2008-12-08
I believe what makes this issue so difficult to accept is that it prevents any chance of booting. I'm unable work with it. Any hope of reparing or circumventing the issue is lost when I'm unable to successfully boot. I could at least work with a command line if I could get past the "checking battery state".
 
I can see the Loading Gnome Desktop Environment but it never happens. I've been experimenting with multiple displays for a long time but this is the first time I've attempted multi-dispaly adapters in GNU/Linux. Hopefully someone will notice this thread with more experience and suggestions.
 
:confused:

---

### Post by djohns505 on 2008-12-10
So far the only thing that I have been able to do to get me on ubuntu again was to install 8.04...  I noticed though that when 8.04 got installed, the nvidia driver version that got installed was 169.  I wonder if you try installing that driver version on 8.10 it might work?

---

### Post by djohns505 on 2008-12-10
Nevermind, I just tried to install the 169 version and I got the same result...  Looks like its exactly as you said about it not being able to handle a multi display setup.  Hopefully I'm wrong because I would love to be able to use 8.10 with hardware acceleration...

---

### Post by tjkeatts on 2008-12-18
I am having the same issue here as well. I have two Nvidia cards hooked in SLi I tried the recommended version 177 driver and my computer froze after displaying "*Checking Battery State". Let me know if there is anything you have figured out or system information that you need to help narrow the search. BTW I am not using multiple displays.

---

### Post by djohns505 on 2009-02-15
Found a solution that works for me from this thread finally:

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

The first solution that Spinalcracker lists is the one that worked for me.

---

### Post by Victormd on 2009-02-15
The "problem" is that you have 2 graphics cards and Ubuntu doesn't know which one to use... check [this link]("http://ubuntuforums.org/showthread.php?t=1055430") to see how to fix it (post #10 of page 1).

---

### Post by MiD-AwE on 2009-02-16
:popcorn: After digging around other forums I found this recommendation that worked for me. Thanks to Chuck Mahon, for this tidbit.

"Do a LSPCI command and find the PCI Bus ID address for your NVIDIA card (your primary card if you have multiple cards...place a Busid statement"

Section "Device"
BusID "1:0:0" <-change to your PCI Bus ID - do not copy & paste
EndSection

Answer provided here: [http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

---

