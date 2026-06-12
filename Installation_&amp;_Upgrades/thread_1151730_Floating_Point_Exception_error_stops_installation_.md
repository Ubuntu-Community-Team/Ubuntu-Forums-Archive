---
title: "Floating Point Exception error stops installation when ISO booted from HDD"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by danushk on 2009-05-07
Hi,

I managed to boot my Ubuntu.ISO  from my local hard disk fat32 partition. :)

i extracted   vmlinuz and initrd.gz files and put them into same partition as ubuntu.iso file and after that rebooted and  went into Grub Command Line.

There i did following commands to make the ISO boot.

grub > kernel (hd0,7)/boot/vmlinuz

grub > initrd  (hd0,7)/boot/initrd.gz

grub > boot

after these command executed ,  it leads to the ubuntu installation screen and i can choose my keyboard layout ,  the location of my country  and some other screen.

Once they are done ,  then it moves to Hardware Detection screen,  but before that it shows me an error in red text  on top left corner of the screen as "floating point exception" , and then an infinite code loop begins to run which moves from hardware detecting screen back to error screen  forever.  So installer does not proceed :(

i am really struggling to get an ISO mounted and booted from Hard Disk and get it installed.  Yet  hurdles are on my way.

So please help me to solve this problem and make Ubuntu install in a system without burning and wasting CDs.

---

### Post by dandnsmith on 2009-05-07
How are you making the rest of the files from the iso available to the install process?

---

### Post by danushk on 2009-05-07
i tried this using a guide.

and it has mentioned that Grub is supposed to be scanning for ISO because latest Grub can read ISO file format. :)

So Grub must be scanning and found the ISO image which was in the same folder as kernel and initrd.gz files. I believe that is why the  first few installation screens were loaded before hardware detection. 

its just my assumption.

now only a workaround to this exception problem is needed to proceed with installation. :)

---

### Post by dandnsmith on 2009-05-08
Can you post a link to the guide you used - might throw some light for me.
Without it, I feel a little sceptical about the whole thing (having a naturally suspicious nature from years of customers problems).

---

