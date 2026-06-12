---
title: "/dev/hda1 not detected or some such nonsense"
date: 2005-10-14
forum: Hardware &amp; Laptops
---

### Post by beefsprocket on 2005-10-14
So I've upgraded from Hoary to Breezy using apt-get and the local university mirror (fast). Problem is that the kernel upgrade to 2.6.12-9-23 or whatever it is (I removed it) totally b0rked my system. Upon booting the new kernel that gets installed by default, I am quickly dropped to an ash shell, my computer claiming that it cannont find /dev/hda1. 

/dev/hda1 works quite well with 2.6.11-1-k7 as well as 2.6.10 series kernels. I am quite confused by this, as I had also tested a 2.6.12-9-22 or previous kernel without any problems whatsoever.

Anyone else had this problem?

---

### Post by beefsprocket on 2005-10-15
After much backing up and a clean install, I'm no better off that I was before with my upgrade from Hoary to Breezy. Again, a clean install of Kubuntu 5.10 has not fixed this problem. What changed between 2.6.12-9.22 and 2.6.12-9.23 kernels? Why does every other distribution run just fine on my computer except Kubuntu/Ubuntu with that particular kernel. I can't use any utilities to adjust my apt sources to downgrade, and the thought of chrooting through a knoppix or equivalent disc isn't appealing when debian, suse, mandriva, and fedora all work without any troubles whatsoever. Even Kubuntu Preview, RC1, RC2 worked without any hassle. 

Again, /dev/hda1 isn't being detected by the kernel properly. Grub is perfectly configured.

Anyone have any thoughts or experience with this problem?

---

### Post by taurus on 2005-10-15
If one kernel that doesn't, then use another one UNLESS you have to use that specific kernel!!!  By the way, what is the exact error message about your /dev/hda1 from the kernel?  Also, a copy of your /boot/grub/menu.lst would be nice...

---

### Post by beefsprocket on 2005-10-15
If I could boot into more than an ash shell and access the programs on my disc, then I would have no problem using another kernel. The computer hangs immediately after uncompressing the kernel (and initrd).

I can't post the grub.conf as I can't boot the machine to get web access. Suffice to say that on /dev/hda1 I have installed Kubuntu 5.10. /dev/hda2 is swap. Grub shows (as it should) (hd0,0) and root=/dev/hda1

At a complete loss here.

---

### Post by dmallery on 2005-10-16
hi

i just posted my similar problem.  check to see if the installer is naming your disks in the right sequence.  mine had the two hard disks ending up as sde and sdf and all the usb connections getting sda thru sdd.

the boot process gets them right, but the system you installed wants the main disks to be sde and sdf so it all ends in a shell.

i have no idea how to fix this.  misery loves company...

dave mallery

---

### Post by beefsprocket on 2005-10-17
I think it names my discs correctly -- I'm wondering if it has anything to do with ext3 filesystem? I think I'll try reiserfs and see what happens.

Edit: See this thread for another user with the same problem. [http://ubuntuforums.org/showthread.php?p=419773&posted=1](http://ubuntuforums.org/showthread.php?p=419773&posted=1)

---

### Post by dmallery on 2005-10-18
AN ANSWER:  i removed my add-in usb2.0 card and did a full install.

works!!!

then i re-installed and perfection strikes!!

many thanks to a gentlemen on the ubuntu-user list.

i will try to post this on the bugzilla... it is a clear installer bug.

dave mallery

---

### Post by bubba on 2005-10-22
Couldn't find my /dev/sda1 after upgrade from hoary to breezy.... but I believe it is because legacy megaraid support is broken in 2.6.12.  

Sorta sucks that something worked in 2.6.10, but not in 2.6.12.

---

