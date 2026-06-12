---
title: "Ubuntu does not start - (initramfs) error"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by lejuan on 2009-05-20
I cannot start Ubuntu 9.04 in my notebook (an HP Pavilion dv2-1025es with AMD Athlon Neo 1.6 GHz), neither from CD or USB key. The error messages are as follows:

[COLOR="Blue"]ata1: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory
BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
(initramfs)[/COLOR]

Start process stops here.
Other linux distros work properly in my notebook (including Molinux 4.2, which is based on Ubuntu 8.10) and, of course the Ubuntu CD works in other computers.

Some suggestion?

---

### Post by napi1234 on 2009-05-20
hi,
yeah same as me..
i am new ubuntu user and  i try install ubuntu 9.04 in my amd 2 core 64 bit machine.
i have download and burn the installer to cd but it does not working.
when i try to boot from the cd to install ubuntu to my pc the same massage appear..

can somebody give the solution?

thanks..

---

### Post by theOtherMarino on 2009-05-21
Hello,

Drop to a terminal, and try "dpkg --audit"

Paste the results here.

Marino

---

### Post by fomaa on 2009-05-21
I have the same problem.
```

(initramfs) dpkg --audit
/bin/sh: dpkg: not found
```

---

### Post by dmeehl on 2009-05-21
Is this during the install? I have a similar problem during the install except i get no error messgaes. I just get dropped to the (initramfs) prompt..

---

### Post by lejuan on 2009-05-21
Yes, it is during the starting process. The "modprobe" error messages appear very soon, then you get the Ubuntu logo and the moving bar, and after some time, the process stops with the [COLOR="Blue"]"(initramfs)" [/COLOR]prompt.

There is no possibility of opening a terminal and try "dpkg --audit".

(NOTE 1: I have tried both 32-bit and 64-bit versions of Ubuntu 9.04, with the same result - fail to start)

(NOTE 2: In the same PC, Ubuntu 8.04 also stops at the [COLOR="Blue"]"(initramfs)" [/COLOR]prompt. Here, the error message is: [COLOR="Red"]udevd-event[1519]: run_program: '/sbin/modprobe' abnormal exit[/COLOR])

---

### Post by lejuan on 2009-05-22
It is amazing! I have succesfully applied the method proposed by **Bonser **at [http://ubuntuforums.org/showthread.php?t=1165715](http://ubuntuforums.org/showthread.php?t=1165715), i.e.:

[COLOR="DarkGreen"]Using an USB memory instead of a CD, if you quickly remove and re-insert the pendrive while the Ubuntu logo and the moving bar are present, Ubuntu starts OK.[/COLOR]

P.S.: I have also tried an external (USB) CD reader. If you unplug and plug again the CD reader while the Ubuntu logo is running, Ubuntu also starts OK.

I wonder if there is a more "civilized" way of starting Ubuntu.

---

### Post by neylitalo on 2009-05-22
I can second the hack proposed by Bonster (and shared by lejuan). It worked for me. Who'd have guessed?

---

### Post by lejuan on 2009-05-23
All of us who suffer this problem have an AMD 64-bit CPU?

---

### Post by fomaa on 2009-05-23
> **lejuan said:**
> All of us who suffer this problem have an AMD 64-bit CPU?
Yes, i have an amd-64 cpu. but iso file is for i386 processors.

---

### Post by istar9 on 2009-05-26
yes have a 64bit chip and have this problem.
 
My question. all of us haveing this problem useing sata drives ? 
 
It seems its looseing ability to mount Cd-rom and drives somehow dureing installation process.

---

### Post by dmeehl on 2009-05-26
I have a laptop with a 32 bit processor. Although I have not tried this solution yet. I will try it tonight and let you know.

---

### Post by dmeehl on 2009-05-26
Nope, this solution absolutely did not work for me.

---

### Post by istar9 on 2009-05-27
Ok farthest I have gotten so far has been with this USB Booting Tactic. 

What i Did was Take 2gb Flash Drive, used UNetbootin and took it to the 64bit Alternate ISO and had it load it to there. 

While Motherboard is on SATA Mode, It boots up and runs fine. However This showed me after it got to the detecting hardware step, the only thing it found was the USB device.. my Sata Drives HD1 / HD2 / CD Rom was not detected ;/ ... Hence shows my issue with the CD rom installing. 

Two other modes my MB has is 

ACHI Mode .. - Never boots from USB hangs 
RAID Mode .. - Hangs at booting USB - Raid setup mode is mirrored

Next attempt is flashing the drive to do the LIVE bootup with out install to see if i can run the desktop and maybe be able see the internet for commands and search out the disks from there. But not sure if that will solve booting problems. 

Ubuntu is winning the rounds so far =/

---

### Post by nbv4 on 2009-06-03
> **dmeehl said:**
> Nope, this solution absolutely did not work for me.

me neither :(

When I pull the USB drive out during the loading screen, I get this:

```

end_request: I/O error, dev fd0, sector 0
Buffer I/O error on device fd0, logical block 0

```

over and over again

---

### Post by paraflou on 2009-06-27
i have the same problem! i have a core2duo and downloaded the amd64 iso file and tried to boot from installer cd several times and a usb stick but it appeared the same message to me! actually i have upgraded to 9.04 but i have i386 installed. i want to install 9.04 amd64! is it worthy or leave it this way??? anyway the install problem remains. any help????

---

### Post by Subpoena on 2009-07-31
The USB-drive-yanking trick worked perfectly for me. Unplug it during the "cylon effect" screen and plug it back in quickly.

It's weird, and I have no idea how it works, but it works.

---

### Post by Dmole on 2009-09-04
I had this problem (initramfs/ash no error message) on a Pentium 3 and solved it by helping the bios see my IDE hard drive.... I think you all should enter this as a bug on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) stating that ubuntu at least needs to be a bit more verbose before dumping people in initramfs/ash.

---

### Post by albertotapia on 2010-05-14
Hey it worked for me.... gracias!!

---

