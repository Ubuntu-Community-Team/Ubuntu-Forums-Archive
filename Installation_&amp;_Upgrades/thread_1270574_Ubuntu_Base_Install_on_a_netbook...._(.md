---
title: "Ubuntu Base Install on a netbook.... :("
date: 2009-09-19
forum: Installation &amp; Upgrades
---

### Post by ugriffin on 2009-09-19
Recently I convinced one of my friends to switch his Acer Aspire One from Windows to Ubuntu. All was set, and I took the netbook home.

So, I made a LiveUSB, and tried to install. The installation crashed at 56%. After fixing the HD itself for sector errors and lots of junk, I downloaded the Alternate CD. It installed the Base system, and then failed after a while on the next step. Good, I've got a basic Linux system on the netbook, all I need to do is install ubuntu-desktop. Easy.

Problem is, apt-get and aptitude (remember I'm running from a terminal... this is a minimal install) don't download the packages (even though the thing is connected to the net... it pings properly.), they ask for "ubuntu 9.04 "Jaunty Jackalope" i386 on "/cdrom/"

ok.

sudo mount -o loop /iso for the cd/ /media/cdrom/

Fail. It still asks for the CD

sudo mount -o loop /iso for the cd/ /cdrom/

Fail. It still asks.


Now what? I've got a useless system (from the typical user's viewpoint) and I can't hand it in like that.


Please... help. Can I somehow force apt to download instead of stupidly requesting the cd? What...on....earth can I do? I'd prefer if you helped me bring this install to a typical ubuntu one... freaky install methods probably won't work and anyways there has to be a way.

Thanks in advance, help me recruit a new Linux convert. :guitar:

---

### Post by Sirhanz on 2009-09-19
Its been ages since I did a terminal install of a gui in ubuntu, I have a netbook and ran into the same issues, I used eaasypeasy.

---

### Post by earthpigg on 2009-09-19
how are you making these LiveUSB's?

---

### Post by earthpigg on 2009-09-19
the three basic ways are:

1. unetbootin
2. dd the .img file over
3. ubuntu's usb startup disk creator


dont ask me why, but for some unfathonable reason i myself have found one or two of the above to fail while the remaining one worked perfectly on a given computer.

---

### Post by ugriffin on 2009-09-19
used LiveUSB creator.

---

