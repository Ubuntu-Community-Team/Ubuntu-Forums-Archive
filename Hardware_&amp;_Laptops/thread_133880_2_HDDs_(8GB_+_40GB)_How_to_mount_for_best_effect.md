---
title: "2 HDDs (8GB + 40GB) How to mount for best effect?"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Captain Irony on 2006-02-20
I have a primary 8GB and a slave 40GB drive and I am not sure the best way to set this up. I have already gotten my 8GB as my /boot and my /home folder is on it. Is there a good way to make the 40gb accessible for use as my main storage and installation directory without losing what I have installed allready?

It has been 15 years since I last picked up any form of -nix system, so please be gentle with your suggestions. I have looked at the VLM guide and, honestly, it does not make any sense to me yet. :???: 

Thanks for any help you can throw my way

---

### Post by evilgold on 2006-02-21
with ubuntu's installer its pretty easy to setup an lvm... but that would require you format your drives. How big is your home folder? Could you burn it? 

Another more complicated thing you could do, is setup your 40gig as an lvm, and install ubuntu to that, then copy over your files, and add the 8gig drive to the volume.

Besides the man pages, the best guide to LVM is here: [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by akiro.yamamoto on 2006-02-21
Right now I have a 120GB Slave IDE drive mounted as /media/data here is my fstab entry:
/dev/hdb1       /media/data ext3    defaults        0       2
So far no problems, I use the drive to store downloads, scratch space for DVD backups (DVD Decrypter / DVD Shrink). My games are installed here. It's like an extra home directory. ;)
Hmmmm! I should have mounted it as my /home directory, but what the hell, when I move to Dapper I'll think about it.

---

### Post by Captain Irony on 2006-02-21
[QUOTE=evilgold]with ubuntu's installer its pretty easy to setup an lvm... but that would require you format your drives. How big is your home folder? Could you burn it? 

Another more complicated thing you could do, is setup your 40gig as an lvm, and install ubuntu to that, then copy over your files, and add the 8gig drive to the volume.

Besides the man pages, the best guide to LVM is here: [http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)[/QUOTE]

Honestly, this is the link that did not make any sense to me. I already have my 40gig as an lvm. if I copy over the entire root directory to it, can I remount it as /root? If so, what would be my best fstab entry for that?

---

### Post by evilgold on 2006-02-22
[QUOTE=Captain Irony]Honestly, this is the link that did not make any sense to me. I already have my 40gig as an lvm. if I copy over the entire root directory to it, can I remount it as /root? If so, what would be my best fstab entry for that?[/QUOTE]


Okay here's what you do. Get an ubuntu install CD,  Choose the option "erase entire disk and use LVM: IDE..(your 40gb drive). This should setup an LVM on your 40gig, with a small /boot partition and the remaining space as / and swap. Then edit your partitions (i think you can tell it NO when it asks if you want to write changes) so that your 8gig is also mounted somewhere like /mnt/8gig. (or you could also just add it to fstab after the install). Anyways...

Install ubutu that way, and copy the files you want to save from your 8gig to your 40gig once its all done.

then read this [http://www.tldp.org/HOWTO/LVM-HOWTO/initdisks.html](http://www.tldp.org/HOWTO/LVM-HOWTO/initdisks.html)
and this
[http://www.tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html](http://www.tldp.org/HOWTO/LVM-HOWTO/addpvstovg.html)


which will tell you how to first make the disk a logical volume, and then add that to your current volume.  (you may or maynot need to do this from a liveCD, if you do the ubuntu live cd has all the lvm tools.)

---

