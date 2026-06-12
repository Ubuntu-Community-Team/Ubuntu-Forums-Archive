---
title: "Can I have two hard drives? one for programs one for data?"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by sulien on 2006-03-02
I'm wondering if anyone can tell me if it's possible to use a second internal hard drive to store data. How do I do it? Simply install the second hard drive? :confused:

---

### Post by frodon on 2006-03-02
Yes, simply plug your second harddrive, and then mount it : [http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

This example is for FAT32 partitions but it's quite the same way for NTFS, ext3, reiserFS, ...
Obviously if it's a new harddrive you have to create some partitions before mounting it, to do that you could use some tools like Gparted if you want a GUI apps or fdisk if you like command lines.

---

### Post by jcornuz on 2006-03-02
Hi !

In my opinion, that's a good setup - that's what I do, anyway :-)

What I did was to link the second harddrive (/media/sdb1 - or whatever) to a directory (say "data") in my home dir. So I just click on "data" to access my... datas.

So you can b0rk your programs and not loose your datas :-) Another thing is that the system should be quicker when you are loading a big file and a program at the same time (opening a big photo with gimp) since it reads from two drives.

Take care.

Joel

---

### Post by sulien on 2006-03-03
well, I seemed to have screwed up royally. How the heck do I access the master or the slave. After installing the second drive it would not boot up and I ended by installing twice over trying to partition the entire new drive as ubuntu ext3 filesystem while leaving the ubuntu OS on the master drive. How exactly did I fail and how can I correct my mistakes. :cry: :cry: :cry: :cry: :cry: :cry: :cry: :confused:

All I want is the ubuntu OS with all my programs on the master drive and just a simple filesystem to store my data on the slave drive without any fancy OS or any programs on it. Is this possible?

---

### Post by tmahmood on 2006-03-03
Hi

Do you get any error messages like >boot disk Failure
if yes then better check which drive is master and which drive is slave. the drive which contains ubuntu installation should be master and other one slave. 

if you are having trouble with GRUB please provide the error message if you are getting any
bye

---

### Post by sulien on 2006-03-04
hi, yes

I receive a system boot disk error strike any key message
there was an error 21 at one point and I think an error 1713 at another. I'm installing ubuntu on both drives for now but I don't know how to switch between them or how to start with the master drive at bootup.

---

### Post by sulien on 2006-03-04
error is PXE-E61

---

### Post by sulien on 2006-03-04
okay I discovered how to browse the master drive but not how to make it the default bootup drive. someone please help me? \\:D/ :-k :cry:

---

### Post by handy on 2006-03-04
With some motherboards, you can set the **boot priority** of the **Hard Disk Drives** in the BIOS. 

So this means that at boot-up, you can choose by going into the BIOS, (usually by holding down the **Delete** key) which one will be the boot disk, if of course there are more than one HDD connected to the Motherboard.  

Masters & slaves are starting to become redundant due to the proliferation of serial drive controllers on our Motherboards these days.

So, you may find it helpful to have a look for this in your BIOS.  Try looking in the **Advanced BIOS Features** section of your BIOS.

Not all Motherboards support this feature, & older ones just don't!

I hope this helps?

---

