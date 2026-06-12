---
title: "Same old installation problem"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by Kriegor on 2008-12-10
Hi fellow ubuntu users. I couldn't find the solution for this problem in the other threads so I'm making a new one...

I have tried... the ubuntu live cd, the ubuntu 8.10 alternate install cd, the official ubuntu dvd, the 64bits alternate install cd and even a usb boot drive created with the official dvd...

...and I cannot install ubuntu on my desktop pc! When i use a text based install I get the "media change error" asking for the ubuntu cd... when I use a live cd, it just stops on the loading bar, and hangs in there, as the cd drive stops spinning :mad:

Fist I was thinking it was a cd drive problem, so i used the usb... but the same old problem again...

It's sad for me, because I really like ubuntu and the desktop pc is my main machine... I am using OpenSuse until i get ubuntu to work, any ideas? #-o

Thanks in advance... Btw, my computer is a stock Aspire M1100...
AMD Athlon 64X2 Dual core 2ghz
Ati Radeon 1250
Generic acer multi drive (or smtg =O)
etc etc

---

### Post by Kevbert on 2008-12-10
Have you burnt your own CDs ? Checked the downloaded ISO checksum ?  Have you tried booting and changed any of the boot parameters ? See this [COLOR="Red"][page]("https://help.ubuntu.com/community/BootOptions")[/COLOR]. I believe you need to try adding pci=noapci to get the PC running.

---

### Post by Kriegor on 2008-12-10
Yes I have burnt my own cds, checked the checksum and tried to burn some in low speed... but I got the same problem every time :?
I am now using the official ubuntu dvd.

Just after your reply I tried the pci=noacpi parameter, but still the same problem :sad: thanks for the support :)

EDIT:

without the quiet and splash parameters I see that the live cd boot stops at something like:

.......end trace........ /sbin/modprole abnormal exit

---

### Post by Kevbert on 2008-12-10
Is the error reported something like this:
```
udevd-event [1410]: run_program: '/sbin/modprobe' abnormal exit.
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash).
Enter 'help' for a list of built-in commands.
(initramfs)_ 
```
If you have onboard LAN it may be worth seeing that if you disable it via the bios you no longer get the problem. I believe you are seeing this [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/231226").

---

### Post by Kriegor on 2008-12-10
The error is just something like this:

```
udevd-event [1410]: run_program: '/sbin/modprobe' abnormal exit.

```

And it stops there. 

I was not able to disable the onboard lan via bios, the only option I saw relatively to it was something like... "Onboard lan wake-up - Disabled" ](*,) 

Thanks for the support Kevbert :D
(Sorry about my english... lack of practice ;D)

---

### Post by Kevbert on 2008-12-11
Your English is excellent. I'm surprised how good everyone's English is on the forum seeing as in many cases English is not their native tongue.
The other possibility for your problem is the make of hard disk drive. Seagate drives have reported to cause problems.  
Try booting by editing the boot line with pci=noacpi, you can find out how to do that [COLOR="Red"][here]("https://help.ubuntu.com/community/BootOptions")[/COLOR].  
You may need to report the problem on [COLOR="Red"][launchpad]("https://launchpad.net/")[/COLOR]. In order to do this you'll need to register there.  In your bug report you'll need to include your Ubuntu version, what you've done to try to rectify the problem and cross reference it to this thread.
Good luck
Kevin.

---

### Post by Kriegor on 2008-12-11
Gee thanks Kevin :mrgreen:, I'll do as you say, but by the way, I have already tried to boot with the pci=noacpi parameter with no favorable results.

I'll keep trying until I get this done, because I really love ubuntu and I want to use it everytime I use a PC \\:D/

---

