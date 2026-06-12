---
title: "buntu 7.10 beta failed to reboot after successful installation on Acer Aspire 5520 G"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by Auckland on 2007-10-02
First of all, I couldn't install Ubuntu 7.04 (neither i386 nor amd 64) "official release" on my new notebook (Acer Aspire 5520 G), thus I tried to install the beta version of Ubuntu 7.10 i386 (the amd 64 version doesn't work at all). The live cd was loaded very slowly but I finally managed to install Ubuntu successfully. I was asked to reboot the system and remove the live cd. I did as I was told but Ubuntu failed to start. The following error message appeared on the screen:
"Busy Box V1.1.3 (Debian 1:1.1.3-5 Ubuntu 4) Built-in Shell (ash)
Enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off (initramfs)"

I suspect that it's a hardware compatibility issue i.e PCI bug. I have noticed a PCI error message while the machine was booting but I couldn't write it down; the message appeared and vanished within a second!

I'll provide you with the following hardware information:
Acer Aspire 5520 G
AMD Turion 64 Mobile Technology MK-38 (2.2 GHz, 512 KB L2 cache)
Up to 384 MB Nvidia Ge Force 8400M G Turbo Cache
1 GB DDR2
15.4 WXGA Acer Crystal Brite LCD (8ms 1220 nits)
120 GB HDD
DVD-Super Multi double layer
802.11 b/g WLAN

Any help or suggestion is appreciated.

---

### Post by DAVVOX on 2007-11-04
Hello, I have the Aspire as5520 (without the G) and got the same issue. I read that the problem is related with the bios configuration, the HD is sata and uses the AHCI specification, the recomendation is to disable this option. No luck, in my laptop the bios doesn't allow to change almost anything. hope you have better luck. I change from ubuntu 7.10 to linuxMint 3.1 (that is distro ubuntu-based), after the instalation got the same message. 
Now I'm using openSUSE 10.3 very stable and complete distribution, 
 At this moment:
1. webcam - ok
2. NIC - ok
3. Nvidia - ok (after installing drivers from nvida website and compiling the kernel)
4. Compiz-Fusion - ok 
5. Sound - no (working on it)
6. Wireless - no (working on it)
Good luck!

---

### Post by naelr on 2007-11-20
I also just purchased an Aspire 5520-5716.  I thought I did enough research to be sure linux would install just fine.  I was wrong.  It does install just fine it however does not boot.  I would assume I am having the same problem with the AHCI that DAVVOX talked about.  I was wondering if any kind of fix had come about.  I love what Ubuntu and Kubuntu have done for the community and would love to use Kubuntu on my new laptop.  I understand that OpenSuse works on this laptop except for sound and network.  I am sure I would have no problem finding a fix for these problems but I would prefer to use a deb based system.  Any help would be greatly apprecaited.  If I could just get it to boot.

Naelr

---

### Post by naelr on 2007-11-26
I have also tried other distros on this laptop.  Fedora 8 was a bust basically the same problem.  Installs just fine will not boot.  Suse 10.3 can't even install it because it cannot find the mouse nor the keyboard.  So I can't select any options to even start the install.

Naelr...

PS  BUMP!!!

---

### Post by shade73 on 2007-11-28
Busybox shell happens in both regular and single user mode. I haven't found a solution yet.  However, I did have the mouse and keyboard issue in OpenSUSE 10.3 and a simple reboot made it work the next time.  I have wireless working in SUSE but I haven't played around with my sound yet.  I want a debian based distro (and debian didn't work for the same reason ubuntu didn't).  I had originally thought it might be the partition setup but it wasn't. Gentoo looked like it might work but refused to recognize either of the network cards.  Sabayon, fedora 8, ubuntu 7.04, 7.10 were all no go.  Any suggestions would be awesome :P.  I've been trying to figure out why it is exactly that SUSE works when nothing else does.  Once I figure that out maybe I can fix it.  I would assume it would have to be a kernel module that SUSE includes that the rest do not.

---

### Post by naelr on 2007-11-28
the problem is the kernel build.  I was working on reloading and grabbed the wrong CD.. I installed fiesty and the thing booted no problem.  it was kernel 2.6.20-14 I think and on the updates it went to 2.6.20-16 after fiesty completely updated it would still boot.  I then upgraded to gutsy and it kept the 2.6.20-16 kernel but went ahead and installed 2.6.22-something .. which will give me the busybox every time.  My laptop is currently working I just commented out the 2.6.22 kernel in /boot/grub/menu.lst.  I am not happy with it but I will run the older kernel until something better comes along.  I cannot get sound or wifi to work but this was a step in the right direction.

Naelr

---

### Post by shade73 on 2007-11-28
ahh perfect thanks.  I must not have tried feisty before successfully (I had one distro that kept dying at 78% and I bet it was feisty).  At any rate I burned a new feisty CD and it works fine now.  I'm doing the upgrade now and I'm going to make sure to stick with the 20.16 kernel.  

Btw, If you're still struggling with the wireless what I had to do was grab the newest ndiswrapper and the 5007 windows driver .inf .. blacklist the ath_pci driver (b/c it recognizes it as a 5006 and it's actually a 5007) and then modprobe it in and then wireless worked fine in openSuSE.  There was a really good article on how to do it.
([http://ubuntuforums.org/showthread.php?t=512828&page=10](http://ubuntuforums.org/showthread.php?t=512828&page=10) -- about half way down the page John Mandrake list step by step how to do it).


Sound I never tackled so I'm not sure.

thanks for the help :)

---

### Post by naelr on 2007-11-29
I didn't have sound no matter what I did until I installed this 

[http://ubuntuforums.org/showthread.php?t=623874&highlight=zen+kernel](http://ubuntuforums.org/showthread.php?t=623874&highlight=zen+kernel)

Now I have sound but my ndiswrapper for my wireless stopped working..
If I can get ndiswrapper working again as well as my nvidia driver I will be totally happy with this laptop.

naelr

---

