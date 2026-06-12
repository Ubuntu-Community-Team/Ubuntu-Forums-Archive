---
title: "Help in upgrading from 8.04 to 8.10"
date: 2009-03-23
forum: Installation &amp; Upgrades
---

### Post by ambdeep on 2009-03-23
Is there any way by which we can upgrade ubuntu 8.04 to 8.10 using the disc.......I have the disc which I got from canonical and not the alternate upgrade disc.......if not is there a way of completely formatting then installing 8.10 but not deleting any of my software of settings?
Thanks in advance!

---

### Post by stumbleUpon on 2009-03-23
You can network upgrade to 8.10 and you wont loose (most of) your installed applications that way.

See here

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Else if you want to do clean install of 8.10 but want to get back the same packages as before, you can get the list of installed applications into a file using

dpkg --get-selections > installed-software

Save the file installed-software and copy it to an external media (usb/cd). Then after the fresh install do

dpkg --set-selections < installed-software

followed by

dselect

See here [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by ambdeep on 2009-03-23
yes.....but is there a way that i need not download everything agan......thanks for replying anyways!!!!!!

---

### Post by stumbleUpon on 2009-03-23
I think not. Package versions of installed software are usually different for different releases and hence you will need to download them again.

But 8.04 is a LTS version. So you can be assured that it will be supported for quite some time (upto 2011). So why dont you stick with what you have. Probably you have downloaded lots of packages already.

---

### Post by ambdeep on 2009-03-23
I do actually....but 8.04 doesnt support dvds with format UTF 2.5(the ones written on vista) and i cant seem to find a patch to make it run on 8.04 so i thought of upgrading as 8.10 has the support for it.
If you do know how to patch up 8.04 please let me know.

---

### Post by stumbleUpon on 2009-03-23
This page might help.

[https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD](https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD)

Have you got mplayer installed? If not, try that.

I cant help you anymore, if the above does not work. Sorry.

---

### Post by ambdeep on 2009-03-23
Thanks....ive already tried the above link....it doesnt work :(

---

