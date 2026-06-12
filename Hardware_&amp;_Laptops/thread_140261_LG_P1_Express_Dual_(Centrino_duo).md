---
title: "LG P1 Express Dual (Centrino duo)"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by Burkey on 2006-03-05
Well, got a new toy, first I want to say this is an awesome laptop...

Intel Core T2400 (dual core 1.8Ghz)
15.4" bright widescreen (1280x800)
1394
USB 2.0
1G DDR2 Dual channel
512Mb ATI X1400
100Gb SATA
Numeric keypad
Bluetooth
Intel 3945ABG wireless
Agere ET-1310x Gigabit LAN
5 in 1 Card reader
Realtek High Def audio
Super-Mulit DVD (DVD+/- RW RAM and Dual layer)
Fingerprint reader

Now, Hoary can not detect any of the network interfaces on install (so I did not install) but I am keen to get Ubuntu on this baby, I will not be rushing to do it as ATI's driver does not yet support the X1400, the Wireless drivers are in beta still and I think the Ethernet is in newer kernels.

I was hoping someone else here has one, or even has some constructive comments.  Bear in mind I WANT to run Linux but I also play World of Warcraft and some computer games.  The Gaming will probably suffer a little but it is easier for my programming under Linux, I also am not overly keen on dual-booting.

So fire away any thoughts or additional pieces on this puzzle!

---

### Post by gmc on 2006-03-05
Hi Burkey,

   You'll have to use Dapper. Hoary/Breezy are not upto date enough. I had the same problem with my Acer 5672. 

G.

---

### Post by Burkey on 2006-03-06
Thanks mate, about to start pulling it down.

How well does you're Core do?  I assume you are using an SMP kernel?  And was that automatic or did you have to change kernels?

---

### Post by gmc on 2006-03-06
Hi Burkey,

[QUOTE=Burkey]Thanks mate, about to start pulling it down.

How well does you're Core do?  I assume you are using an SMP kernel?  And was that automatic or did you have to change kernels?[/QUOTE]

The dual core works very well, Ubuntu is pretty nappy with my T2300. As for the kernel, no I had to install the smp enabled kernel.

G.

---

### Post by gmc on 2006-03-08
Hi Burkey,

[QUOTE=Burkey]Thanks mate, about to start pulling it down.

How well does you're Core do?  I assume you are using an SMP kernel?  And was that automatic or did you have to change kernels?[/QUOTE]

How are you making out with Dapper? I know getting Xorg working here required a little tinkering. 

G.

---

### Post by Burkey on 2006-03-09
Actually I just got back home from Taiwan and am going to start the ISO downloading as soon as I find it.. will post back how I go with it :-)

---

### Post by Burkey on 2006-03-10
Got both the livecd and install down, trying to boot on live first but end up that it cannot mount the rootfs, exact error:

mount: Mounting /dev/loop0 on /rofs failed: Invalid argument

Any ideas?

---

### Post by snyderg on 2006-03-10
I have a new Dell E1705 - 
T2400 Core Duo
1 Gb Dual Channel DDR2
nVidia go 7800 256 Mb
Intel Pro 3945 Wireless - Still can't get this to work.
Integrated NIC
80 Gb SATA HDD
17" Screen WXGA

Everything works great but wireless. Sound is a little scratchy.

5.10 Breezy - Dual boot w/XP (have to for my Blackberry)
Kernel - 2.6.12-10-686-smp

---

### Post by gmc on 2006-03-10
Hi Guys,

Sounds like the mount error your talking about is on the LiveCD. If that's the case, then I would suggest maybe the burn is bad. Have you tried the install version (do a cd check before trying to install it though).

G.

---

### Post by Burkey on 2006-03-17
Downloaded the latest dapper livecd and burnt it, the system booted but cannot get X to start :-(

Looks like it was trying to start it up using the "ati" driver in xorg.conf.

Otherwise the wireless has no driver, there was some errors about the hard drive (it is a SATA drive but looked like Dapper was trying to mount /dev/hda) hmm now that I think of it maybe it was referring to the Optical drive... did not get to play much as I was ushed for time.

Interstingly it seemed to load drivers for my 5in1 card reader!? Thought that would not be supported.

---

### Post by bwanab on 2006-03-21
[QUOTE=Burkey]Downloaded the latest dapper livecd and burnt it, the system booted but cannot get X to start :-(

Looks like it was trying to start it up using the "ati" driver in xorg.conf.

Otherwise the wireless has no driver, there was some errors about the hard drive (it is a SATA drive but looked like Dapper was trying to mount /dev/hda) hmm now that I think of it maybe it was referring to the Optical drive... did not get to play much as I was ushed for time.

Interstingly it seemed to load drivers for my 5in1 card reader!? Thought that would not be supported.[/QUOTE]

For X you need to use the Vesa driver until ATI puts out a driver for x1400. There is a thread for the Acer 5672WLMi that has instructions for wireless if your machine has the 3945 chipset: [http://www.ubuntuforums.org/showthread.php?t=121125]("http://www.ubuntuforums.org/showthread.php?t=121125")

---

### Post by Burkey on 2006-04-02
Much appreciated bwanab, I will read the wireless thread, do you think it would be easier to get the wireless or the wired working first?  I guess I want a "correct" way instead of just an "easy" way as I do not want upgrades to the system to break what I have done.

April.. fingers are crossed for a new ATI driver to come out soon, looking at 1024x768 on a 1280x768 LCD is making my eyes bleed!

---

