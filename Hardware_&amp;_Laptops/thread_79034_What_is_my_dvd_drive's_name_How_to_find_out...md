---
title: "What is my dvd drive's name? How to find out.."
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-19
Hi..
I need to know the name of my dvd drive to slow it down..
The code need the following info...
ex...{eject /mnt/cdrom -t -x 8} 8 means the speed, but the /mnt/cdrom is not where the dvd drive is? It says unable to find dev /mnt/cdrom......This is where I got it..

[http://www.nn.iij4u.or.jp/~tutimura/eject/index.en.html](http://www.nn.iij4u.or.jp/~tutimura/eject/index.en.html)

IDE "primary master" Its the only drive on the IDE. Is where the only dvd drive is (no other dvd or cdroms)

HDD is SATA.

If I put a dvd in and mount it..

-Nothing in the MNT folder

-In the MEDIA folder there is cdrom and cdrom0 folder.. In fact it says cdrom is a link to cdrom0 (I have no cdrom drives only the 1 dvd).
There is nothing in either anyway

-In DEV folder, there is cdrom,cdrw,dvd,dvdrw all say (link to hda block).

-In HDA  it says (block device) but has 0 MB. 

-In the dvd it makes on the desktop when mounted it says...HDA in the name section. And location says / (media)...
In the META info tab for this it says...base URL file:///media/cdrom0
And Device Node is /dev/hda

---

