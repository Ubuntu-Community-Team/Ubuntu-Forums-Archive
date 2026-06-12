---
title: "&quot;Cannot mount partition&quot; GRUB and adding Fedora."
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by Mr Connolly on 2009-09-30
So basically I've been at this for a few hours now. Basically I'm trying to add Fedora to the GRUB that Ubuntu installed - I sorta expected it to be there afterwards but it wasn't so hey.

What led up to this situation was the following; my processor melted the hinges that held the heatsink on it falls off when the PC is on and hell basically follows (I don't wanna into this really), this in turn killed my Windows install. I decide to install Ubuntu and back up all I can to my Fedora installation so I, being a silly monkey back it up to my user folder.
I get into Fedora and find I cannot access my Fedora user folder due to obvious permission errors.

So now I sit here trying to figure out how I can boot Fedora from GRUB because its being an **** hah...

My current GRUB menu.lst for Fedora reads; 

title         Fedora (2.6.29.2-126.fc11.x86_64)
root         (hd0,3)
kernel         /vmlinuz-2.6.29.2-126.fc11.x86_64 ro root=/dev/vg_f11fabio/lv_root rhgb quiet
initrd         /initrd-2.6.29.2-126.fc11.x86_64.img

When I boot this it goes "hah no" and tells me the partition cannot be mounted...

Sorry if this is an overly repeated question or anything just any real help would wholy be appreciated so I can get my stuff back sometime soon... hah.

---

### Post by VanCardboardbox on 2009-09-30
What version of Ubuntu did you install? Your menu.lst shows that Fedora is version 11. If you installed an older version of Ub it could be that the GRUB installation Ub gave you is not playing nice with an ext4 partition. I have experienced this. 

Try booting with a Fedora 11 live CD and reinstalling GRUB from that.

---

### Post by Mr Connolly on 2009-09-30
Oh sorry, that is the Fedora 11 section I copied from it, I'll paste the whole thing from the first instance of Ubuntu to the last.

Ubuntu 9.04 btw.
```

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        09245bb5-b16e-41b8-8cc8-f4ca703774e1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=09245bb5-b16e-41b8-8cc8-f4ca703774e1 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        09245bb5-b16e-41b8-8cc8-f4ca703774e1
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=09245bb5-b16e-41b8-8cc8-f4ca703774e1 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        09245bb5-b16e-41b8-8cc8-f4ca703774e1
kernel        /boot/memtest86+.bin
quiet

title         Fedora (2.6.29.2-126.fc11.x86_64)
root         (hd0,3)
kernel         /vmlinuz-2.6.29.2-126.fc11.x86_64 ro root=/dev/vg_f11fabio/lv_root rhgb quiet
initrd         /initrd-2.6.29.2-126.fc11.x86_64.img

```I have Fedora 11 installed and Ubuntu 9.04 installed. Fedora 11 was first followed by Ubuntu 9.04 (Fedora was at the same time as I had Windows originally) I also am using EXT3 for both Ubuntu and Fedora. So =/

Also if possible I'd like to avoid having to burn CD's due to the fact I have none and I don't get paid for a few days yet (student life is lovely).

---

