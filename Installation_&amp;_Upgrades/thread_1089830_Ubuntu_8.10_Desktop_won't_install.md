---
title: "Ubuntu 8.10 Desktop won't install"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by Koradhil on 2009-03-07
I am attempting to install Ubuntu (desktop) on my homeserver. This is my first hands-on encounter with Ubuntu, so don't shoot me.
Here's the specs:
- Foxconn mainboard, AMD socket AM2
- AMD Sempron 3400 CPU
- 1GB DDR2 RAM
- 2x Samsung Spinpoint F1 1TB harddisks
- Some old CDR drive
- Onboard graphics / audio

The harddisks are brand new, straight out of the box so not formatted or partitioned yet.

When I try to install Ubuntu from CD, the installation hangs in the first stages. At some point I get this message:

[FONT="Courier New"]Loading, please wait.
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)[/FONT]

After this I can type commands, but I have no clue what to do here.

Can anyone help?

---

### Post by taurus on 2009-03-07
Here are the steps you need to take to ensure you install Ubuntu successfully.

1.  Run a checksum to check the integrity of the ISO image right after you've downloaded it.

2.  Run the ISO image as an image with a slow speed like 4x.

3.  At the initial boot screen, pick the check cd for defects option to make sure the CD is good.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight](https://help.ubuntu.com/community/BurningIsoHowto?highlight)

---

### Post by Koradhil on 2009-03-07
I've downloaded the ISO from [here](http://ubuntu-nl.org/getubuntu/download). I ran a checksum with winMD5sum, which returned f9cdb7e9ad85263dde17f8fc81a6305b, so it's a valid ubuntu-8.10-desktop-amd64.iso.

I burned it at max speed (24x I think). I'll burn it again at 4x.

---

### Post by Keez on 2009-03-07
I'm having the same issue.  Brand new hard drive, right out of box, but I don't get the loading message.  When installed, it asks for the log in and then hangs.  From a live CD it gives the log in tone and then hangs.  I ran the MD5 and it checked, and I have burned the ISO three times now with the last at 2X.  No improvement.  I feel your pain.

---

### Post by Koradhil on 2009-03-08
I've burned it at 4x, and tried using a different CD drive for reading as well (the one I used at first was really old), but again I get the BusyBox, only this time it also gives error messages (something with I/O read on IDE channel somecode).

I also tried installing Dapper using the original CD (one I ordered). This will actually boot into Ubuntu, but when I try to install, it keeps loading the drive selection tool.

I'm going to try to run a Windows XP installation to format my harddisks. I guess it will require reformatting when installing Ubuntu, but at least my drives will have partitions and not just be raw disks.

---

### Post by raulozzi on 2009-03-08
While I was installing it on my computer it hung as well although it was not a brand new hard drive. When it hung I was going to press CTRL ALT DELETE and I noticed when I pressed CTRL it started working again.

---

### Post by kthari85 on 2009-03-21
Yes, my friend too was having the same problem installing Ubuntu 8.10 on his AMD 64bit and 32bit desktop.
I was not able to go to his home and check whats the real problem ?
This is what he says ...
1 ) Installed ubuntu through wubi from windows.
2 ) Restarted and tried to login . The blue screen was there and stuck there. No response.

The next time I told him to check the CD for defects . It has none .
Tried to login with out installation . Again stucks .
Tried to install from the beginning itself. Same effect . But I was not having a trouble installing in Intel Core 2 Duo.
The CD was got through free shipping. I searched the forums , dont get an answer. Anyone knows mail me 2.

---

