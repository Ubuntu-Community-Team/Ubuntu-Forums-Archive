---
title: "Ubuntu 11.04 hangs constantly"
date: 2011-05-04
forum: Hardware
---

### Post by ganesh3 on 2011-05-04
Hi,
I have recently installed Ubuntu 11.04 & removed Windows 7.

Whenever I get connected to a wireless network and open the browser ( Google chrome or Firefox)to go to a site, Ubuntu OS hangs.

I dont know what is causing this but I would like your help in understanding the reasons and ways to rectify it.

Please let me know if you need any further information.

Thanks,

Ganesh Bhat

---

### Post by mörgæs on 2011-05-04
Here is what is worth knowing of Wubi:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2011-05-04
> **ganesh3 said:**
> Hi,
I have recently installed Ubuntu 11.04 from Windows 7.

Whenever I get connected to a wireless network and open the browser ( Google chrome or Firefox)to go to a site, Ubuntu OS hangs.

I dont know what is causing this but I would like your help in understanding the reasons and ways to rectify it.

Please let me know if you need any further information.

Thanks,

Ganesh Bhat
Actually hanging has nothing to do with Wubi. It did have grub problems on 10.04 and 10.10 but this does not affect 11.04.

It's likely some device that isn't linux friendly. Please post the specs of your machine e.g. brand/model, graphics card, wireless card.

---

### Post by ganesh3 on 2011-05-04
> **mörgæs said:**
> Here is what is worth knowing of Wubi:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

I am extremely sorry, I didnt mean to say that Ubuntu is installed on Windows. I have removed Windows 7 and installed Ubuntu 11.04. It is the only OS on my Laptop.

---

### Post by ganesh3 on 2011-05-04
> **bcbc said:**
> Actually hanging has nothing to do with Wubi. It did have grub problems on 10.04 and 10.10 but this does not affect 11.04.

It's likely some device that isn't linux friendly. Please post the specs of your machine e.g. brand/model, graphics card, wireless card.

Machine specs: 4GB RAM, Intel i3 Processor M350 2.27GHz, 16GB swap Space
Brand: Dell, Model: Inspiron 1558

64-Bit Ubuntu on 64-bit Hardware.

Wireless Configuration:
[COLOR=#000000][FONT=Times New Roman]

description:Wireless interfaceproduct:BCM43224 802.11a/b/g/nvendor:Broadcom Corporation[COLOR=#000000][FONT=Times New Roman]

wireless=IEEE 802.11abgn[/FONT][/COLOR]
[/FONT][/COLOR]
Let me know if you need any further information.

Thanks,

Ganesh Bhat.

---

### Post by bcbc on 2011-05-04
Try here: [http://ubuntuforums.org/showthread.php?t=1662765](http://ubuntuforums.org/showthread.php?t=1662765)
It refers to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/+index?comments=all)

See if that helps.

---

### Post by ganesh3 on 2011-05-04
> **bcbc said:**
> Try here: [http://ubuntuforums.org/showthread.php?t=1662765](http://ubuntuforums.org/showthread.php?t=1662765)
It refers to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/+index?comments=all)

See if that helps.

I am beginner at Linux and Ubuntu.

After going through the bug section, it is very difficult for me to do what is stated there as people do check status of some components and processes which I am not familiar with as this is my first time

This bug was reported in 10.10 as well as 11.04.

Is a document available which suggests a step by step approach to handle this as there are too many suggestions to try out and different process to check.

Also, can you please provide me with the set of commands to run for comment 50 as I can understand the semantics of what is being said. 

Please let me know.

---

### Post by bcbc on 2011-05-04
Why don't you try the simplest first. Boot, hold down SHIFT to get the grub menu, press 'e' to edit the first entry, use arrow keys to get to "quiet splash" and change it to "quiet splash pcie_aspm=off" (no double quotes). Hit CTRL+x to boot.

See if it freezes. That's step 1 and it's the easiest to do.

If it works you need to make it permanent. But first see if it works. 

See here for some background on boot workarounds: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by bcbc on 2011-05-04
Also consider trying [10.04.2]("http://releases.ubuntu.com/10.04.2/") - since you're new to Ubuntu it's might be less hassle.

---

### Post by ganesh3 on 2011-05-05
> **bcbc said:**
> Why don't you try the simplest first. Boot, hold down SHIFT to get the grub menu, press 'e' to edit the first entry, use arrow keys to get to "quiet splash" and change it to "quiet splash pcie_aspm=off" (no double quotes). Hit CTRL+x to boot.

See if it freezes. That's step 1 and it's the easiest to do.

If it works you need to make it permanent. But first see if it works. 

See here for some background on boot workarounds: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Hi,

I have tried what you suggested. But it has changed the way Ubuntu UI looks. I am attaching the screenshot (top menubar becomes grey rather than being black)

Although I am still checking if it hangs, I wouldn't want to consider this given that it changes UI.

Please let me know if this is an expected change.


Thanks,

Ganesh Bhat

---

### Post by ganesh3 on 2011-05-05
> **bcbc said:**
> Also consider trying [10.04.2]("http://releases.ubuntu.com/10.04.2/") - since you're new to Ubuntu it's might be less hassle.

I would rather learn than switch to a easier version. Anyways I saw the thread posted earlier about the hangs, I suppose this version too has the problems.

---

### Post by bcbc on 2011-05-06
I find it unlikely that the boot option has changed the colour of the top panel. But... you're the one with the computer. If you have questions you'd do best to post on the bug and see if someone there responds.

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg08476.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg08476.html)
> 	pcie_aspm=	[PCIE] Forcibly enable or disable PCIe Active State Power
+	 Management.
+	 off	Disable ASPM.
+	 force	Enable ASPM even on devices that claim not to support it.
+	 WARNING: Forcing ASPM on may cause system lockups.
+
pcmv=	 [HW,PCMCIA] BadgePAD 4

---

### Post by ganesh3 on 2011-05-12
> **bcbc said:**
> I find it unlikely that the boot option has changed the colour of the top panel. But... you're the one with the computer. If you have questions you'd do best to post on the bug and see if someone there responds.

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg08476.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-09/msg08476.html)

Thanks.
 
The UI change seem to be a one off as changing the code again did not change the UI colour.

The patch/code is working. Would like to know how do I make it permanent?

Awaiting reply.


Regards,

Ganesh Bhat.

---

### Post by bcbc on 2011-05-12
> **ganesh3 said:**
> Thanks.
 
The UI change seem to be a one off as changing the code again did not change the UI colour.

The patch/code is working. Would like to know how do I make it permanent?

Awaiting reply.


Regards,

Ganesh Bhat.
That's good to hear. This thread clearly explains with screenshots how to make boot options permanent: [ How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by frodowiz on 2011-05-13
> **ganesh3 said:**
> Hi,
I have recently installed Ubuntu 11.04 & removed Windows 7.

Whenever I get connected to a wireless network and open the browser ( Google chrome or Firefox)to go to a site, Ubuntu OS hangs.

I dont know what is causing this but I would like your help in understanding the reasons and ways to rectify it.

Please let me know if you need any further information.

Thanks,

Ganesh Bhat

ubu 11.04
just read this as i have a similar problem. i boot fine. when i open firefox or switch to dash for the first time i cant type anything- it hangs. if i click the  top panel the screen seems to move up a bit and all is well.. very weird.. never had this happen in 3 years.. this began after  some update but i couldnt say which. just curious why the screen moves a few pixels up and everything becomes ok..

---

