---
title: "Installation Issues nx9420"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by dg88 on 2007-04-20
I recently tried to install the new Ubuntu Feisty on my laptop after deciding to finally get rid of that last piece of windows. but once it got to starting the x-server it gave me an error wich ill post here once i get another look at it.  it didnt even work with the original 6.10 disc i used the first time i installed it on my laptop.

hardware:
Hp nx9420 laptop with all original.
ATI radeon mobile 256mb
80gb sata harddrive

ask if you need more info and ill provide as i can.

ill take any and all help i can get so thanks for the help

---

### Post by indigomm on 2007-04-20
I'm having what sounds like exactly the same problem on an nc8430. I've tried updating the BIOS to the latest version, but doesn't make any difference. I've also tried burning a new CD downloaded directly from Canonical but it gives the same problem.

HP Compaq nc8430, ATI Mobility Radeon X1600, 1GB RAM, 80GB HDD - all as shipped from factory

I'm a little surprised since I managed to boot the 7.04 beta live CD - I didn't install it, but at least it booted.

My stack trace (all retyped by hand - hopefully no errors)

/usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c5d91]
[0xffffe420]
/usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
/usr/X11R6/bin/X(main+0x27b) [0x807456b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7db7ebc]
/usr/X11R6/bin/X(FontFileCompleteXLFD+0x1e1) [0x8073ab1]

---

### Post by dg88 on 2007-04-20
a dist-upgrade upgrades to feisty but now that the graphics-card works properly i can finally get rid of windows and the only way to di that is to remove everything and repartition everything. i think... if someone has any suggestions on merging the to partitions, keeping the linux, without reinstalling im listening.

---

### Post by the_toddster on 2007-04-27
I was unable to boot the Feisty live CD on my nx9420, even though I've been running Edgy for a few months. The xserver crashed and the display was so jacked I couldn't get enough information to do any troubleshooting.

The distribution upgrade died with an error about the dmsetup, for which I've opened bug #109625.

---

### Post by the_toddster on 2007-04-27
dg88,

How is your drive partioned now? What do you need to save from your Windows partion?

---

### Post by dg88 on 2007-04-28
the_toddster: i booted from an gparted livecd and changed it all. now im only running Ubuntu. it took almost a day to do it but its well worth it.

---

### Post by cjv on 2007-04-29
Hi there,

I've also a factory HP Compaq nc8430:

- ATI Mobility Radeon X1600 PCI-Express x16
- 2GB RAM DDR2 dual-channel 2 x 1Gb PC2-5300 (333 MHz) 5-5-5-15-20
- Seagate Momentus 7200.1 ST 980825AS harddisk - 80 GB - SATA-150
- Intel Core Duo T2400
- Intel i945PM motherboard

It's been running Edgy for a while without problems. Now I tried a CLEAN installation of Feisty, but Live CD doesn't boot, even in save graphics mode, or even with VGA parameters.

It boots from CD, then I choose the method, then Ubuntu splash screen appears (with status bar moving) and then some message text appears describing some error.

If anyone has installed 7.04 on this computer: which image did you used? How did you did it?

I first tried ubuntu-7.04-desktop-i386.iso, using also save graphics mode, and VGA on 1024x760 32 bits. I've tried also ubuntu-7.04-alternate-i386.iso and installation goes fine in text mode, but then the installed OS (Ubuntu) refuses to boot (??). Using grub on MBR of only SATA disk. I've always checked the md5's.

Any help would be appreciated.

Carlos

---

### Post by cjv on 2007-04-29
Hi again,

I did a photo of the screen when frozen and now I'm writing it down if it's of help for anybody:

BusyBox v1.1.3 (Deian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [   24.808000] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action ....
 0x2 frozen
[   24.808000] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 ....
ata 36 in
[   30.804000] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   30.804000] ata5.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 ....
ata 36 in

Hope that clarifies something for someone (not for me!) :confused: 

Carlos

---

### Post by Wobedraggled on 2007-05-03
I have the same laptop, guessing there is no fix as of yet.

---

### Post by robertmcox on 2007-05-16
I cannot speak to 32-bit, but for 64-bit, the live/desktop CD gives me the same problems.

The alternate install AMD64 works like a champ, absolutely no problems, worked since RC, including the dual boot (actually triple over here).

Pretty bizarre becuase the X server installed works fine, it's just the livecd that has the problem.

---

### Post by dg88 on 2007-05-24
robertmcox: are you using the nx9420? let me know if you do so i can get rid of grub and boot straight into ubuntu

---

### Post by digitalpure on 2007-05-24
from reading the forums, it appears that there is a X.org issue with Fiesty and ATI drivers that is causing the video problems.   I understand that in the command line you can reconfigure your X and it should work great.  If anyone has a nx9420 and can post your X config file so that we can use that it would rock.

---

### Post by dg88 on 2007-05-31
> **digitalpure said:**
> from reading the forums, it appears that there is a X.org issue with Fiesty and ATI drivers that is causing the video problems.   I understand that in the command line you can reconfigure your X and it should work great.  If anyone has a nx9420 and can post your X config file so that we can use that it would rock.

i second that

---

### Post by ivanox1972 on 2007-06-08
Still no solution? Its really strange...

---

### Post by piricoco on 2007-07-24
Hi guys! This is my first post :)

The problem is the video card Ati x***
I successfully installed Kubuntu Feisty following **[*this*](http://ubuntuforums.org/showthread.php?t=414194&highlight=Many+people+are+having+problems+installing+Ubuntu+7.04)** howto

Now I'm looking for some information regarding ACPI support for my HP nc8430...
I'm a newbie, but it seems not fine working with my notebook :(

Greetings from Italy!

---

### Post by dg88 on 2007-09-03
ill post the xorg.conf i am currently running on.

gonna reinstall this sucker tonight. ill let you know how it all goes.

---

### Post by cjsteele on 2007-09-29
I have an nx9420 and have successfully gotten it to work with Fiesty.  I have created an entry in the Ubuntu Wiki to chronicle some of that work.  I have also aggregated much of this information on my own web-site at intertrusion.com.

---

### Post by cjsteele on 2007-09-29
I'm using the nvidia-glx driver with great success.  I have also conquered the ACPI woes that many nx9420 users have experienced.  I've got an entry describing this on the Ubuntu wiki as well as on my website at intertrusion.com.

---

### Post by qwerion on 2007-10-14
> **cjsteele said:**
> I'm using the nvidia-glx driver with great success.  I have also conquered the ACPI woes that many nx9420 users have experienced.  I've got an entry describing this on the Ubuntu wiki as well as on my website at intertrusion.com.

please, can u give link to ubuntu wiki entry

---

