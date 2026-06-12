---
title: "Ubuntu Installation Problem"
date: 2008-12-12
forum: Installation &amp; Upgrades
---

### Post by crl0901 on 2008-12-12
I'm trying to install Ubuntu 8.10.  I've downloaded and burnt the ISO to a CD-R, checked the disk for errors and nothing came back.  I'm installing it on a P4 3GHz machine with a 120GB HD, 2GB ram, and integrated Intel graphics (8465g ?, can't remember).  When I pop the disc in, I select English and choose Install Ubuntu.  It takes awhile to load everything, in fact, it's really slow.  Once everything's loaded, I get to a black screen with the X-shaped cursor and nothing happens.  It just sits there.

Any ideas?

---

### Post by wpshooter on 2008-12-12
If you are trying to install from the desktop (live CD version) of Ubuntu then try installing using the safe graphics mode.  If that does not work then download and try installing from the ALTERNATE (text based) version of Ubuntu.

Good luck.

---

### Post by crl0901 on 2008-12-12
> **wpshooter said:**
> If you are trying to install from the desktop (live CD version) of Ubuntu then try installing using the safe graphics mode.  If that does not work then download and try installing from the ALTERNATE (text based) version of Ubuntu.

Good luck.

Yeah, I tried installing in Safe Graphics mode and that didn't work, got the same result.  The text-based install is a separate download or is it included in the standard disc?

EDIT:  Nevermind, found it on the download page.  I'll give it a try.  Thanks.

---

### Post by Ifaistos on 2008-12-12
It might sound weird, but I had kind of the same problem and I solved it this way :

I booted with parted magic and deleted all the partitions that were there.
I don't want Ubuntu to be able to find any ready made partitions, even if they are from another linux installation, even if they are from a previously failed installation.

Then I booted from the Ubuntu ISO, and asked from it's partition manager to create the partitions.

If you fail the first time for any reason, and you try again, you have to repeat the procedure.

I REALLY don't know why it worked for me!!
I hope it works for you too. :-)

---

### Post by rickcool on 2008-12-12
> **crl0901 said:**
> I'm trying to install Ubuntu 8.10.  I've downloaded and burnt the ISO to a CD-R, checked the disk for errors and nothing came back.  I'm installing it on a P4 3GHz machine with a 120GB HD, 2GB ram, and integrated Intel graphics (8465g ?, can't remember).  When I pop the disc in, I select English and choose Install Ubuntu.  It takes awhile to load everything, in fact, it's really slow.  Once everything's loaded, I get to a black screen with the X-shaped cursor and nothing happens.  It just sits there.

Any ideas?
Hi there,I have exactly the same problem as you have,I have an Asus MSN570SLI Mobo,AMD64 X2 5200+ and an WD 150GB Velociraptor.I also mention that I have 3 partitions on this hdd and one is with windows XP.I select install and after a while I receive a black screen...nothing further...Anybody solved this problem?

---

### Post by crl0901 on 2008-12-13
Well, I'm using the alternate install disc now.  I've gotten past the partitioning section and it's installing, but it's been on "Scanning the CD-rom" at 12% for awhile now.  CD drive keeps spinning up, then spinning down, then spinning up, then spinning down, etc.  I'm gonna keep letting it run and see what happens.

---

### Post by abn91c on 2008-12-13
> **crl0901 said:**
> I'm trying to install Ubuntu 8.10.  I've downloaded and burnt the ISO to a CD-R, checked the disk for errors and nothing came back.  I'm installing it on a P4 3GHz machine with a 120GB HD, 2GB ram, and integrated Intel graphics (8465g ?, can't remember).  When I pop the disc in, I select English and choose Install Ubuntu.  It takes awhile to load everything, in fact, it's really slow.  Once everything's loaded, I get to a black screen with the X-shaped cursor and nothing happens.  It just sits there.

Any ideas?

your problem is you i845 video card, you will need to remove compiz ctrl+alt+f1 will get you to the prompt, then

sudo apt-get remove compiz compiz
sudo apt-get remove compiz compiz-core

---

### Post by crl0901 on 2008-12-13
> **abn91c said:**
> your problem is you i845 video card, you will need to remove compiz ctrl+alt+f1 will get you to the prompt, then

sudo apt-get remove compiz compiz
sudo apt-get remove compiz compiz-core

Are you sure?  Compiz has nothing to do with the installation, does it?

---

