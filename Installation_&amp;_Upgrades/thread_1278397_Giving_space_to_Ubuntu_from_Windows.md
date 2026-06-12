---
title: "Giving space to Ubuntu from Windows"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by zeycus on 2009-09-29
Hi! In my laptop I had a HD with 2 parts (linked as C: and D). I succesfully installed installed Ubuntu in the 2nd, with a nice Grub that lets me choose between my old WindowsXP and my new Ubuntu 9.04. I have /root, /home and swap mounted in /dev/hda2 /dev/hda3 and /dev/hda4

After a while I realized that the part for Windows is too big, I would like to have more room for Ubuntu, less for Windows. I thought I can use partition magic, move the files to the beginning of C: and create a new part with the end, that could be used in Ubuntu. My questions:

1) If I split what is now the first part (Windows) in two, will Ubuntu stop booting from the Grub menu? Maybe this is naive, I assumed that a new /dev/hda2 will appear, and that was before was /dev/hda2 will become /dev/hda3, etc.

2) If Ubuntu will boot yet, can I just format /dev/hda2 (assuming this will be the new part) and mount there my files? I thought that long ago, abount Linux, I read that the /root must be in the first part of Linux. But I am probably wrong...

Thanks in advance!

---

### Post by rreese6 on 2009-09-29
ok let me direct you to a site about dual booting;

also I would first defrag windows a few times then I would use a Linux LIVECD to boot up and run a program called gparted.
Gparted can resize your Windows partition. then you can resize and move the other Linux partions to your liking to eat up the new space. no need to make another partion, the "/root" partition should be "/"
they are both know as root but the "/" means root of the file system.

here is the link: [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/~herman546/index.html") 

let us know how things are coming along

---

### Post by zeycus on 2009-09-29
Thanks a lot for the pointer, rreese6, there is much information there. I will go through it carefully, I really don't want to spoil anything!

---

