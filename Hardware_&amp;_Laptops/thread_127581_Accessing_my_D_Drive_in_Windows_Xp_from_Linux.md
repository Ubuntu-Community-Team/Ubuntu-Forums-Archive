---
title: "Accessing my D: Drive in Windows Xp from Linux"
date: 2006-02-09
forum: Hardware &amp; Laptops
---

### Post by caven80 on 2006-02-09
hello Everyone,

I have dual booted my acer latop with ubuntu and xp prof.

Its a single hard disk, which has 2 partition in Xp. C: and D:.

Please can anyone tell me how i can access these drives from ubuntu.

Also both those drives are formatted with NTFS. Is this ok??

Any help will be appreaciated.

Caven

---

### Post by el3ktro on 2006-02-09
Linux can only READ from NTFS due to licencing/patenting issues etc. To read-access your D: drive you have to find out which partition number it is and then you can mount it in Linux. If you add a line to /etc/fstab for your NTFS drive then it wll always be mounted in Ubuntu. If you tell me the partition number of your D: drive then I can help you.

Tom

---

### Post by taurus on 2006-02-09
Try something like this

sudo mkdir /mnt/c /mnt/d
sudo mount -t ntfs /dev/hda1 /mnt/c
sudo mount -t ntfs /dev/hda2 /mnt/d
df -h

You will now see both of your NTFS drives on the list and you can access them under /mnt/c (for first partition) and /mnt/d (for second partition).

---

### Post by caven80 on 2006-02-09
Hi taurus,

i tried the above steps, but it tells me either the drive is already mounted or its busy, when i listed using df -h, i saw one hd3 and hd1.

on my desktop there is one folder HD1, but i cannot open it. it says permission denied.

i am the only user on ubuntu and still get the $ promt in the terminal, how can i switch to root?? (#)

Also those directories i created (/mnt/c and /mnt/d) are empty.

Please help

---

### Post by aysiu on 2006-02-09
See the fourth link of my signature.

---

### Post by caven80 on 2006-02-09
thanks there..it Worked!!!!

jus one thing more.

why do i hav to keep typing 'sudo' before evry command??\
how can i switch to root??

thanks again..

Ciao

---

### Post by jonathanm on 2006-02-09
add uid=[username] into the options of your fstab, where it should read defaults, that should do it

---

### Post by aysiu on 2006-02-09
[QUOTE=caven80]thanks there..it Worked!!!!

jus one thing more.

why do i hav to keep typing 'sudo' before evry command??\
how can i switch to root??

thanks again..

Ciao[/QUOTE] Read the third link of my signature.

---

### Post by NoJock on 2006-02-09
[QUOTE=taurus]Try something like this

sudo mkdir /mnt/c /mnt/d
sudo mount -t ntfs /dev/hda1 /mnt/c
sudo mount -t ntfs /dev/hda2 /mnt/d
df -h

You will now see both of your NTFS drives on the list and you can access them under /mnt/c (for first partition) and /mnt/d (for second partition).[/QUOTE]

I have a simular probleb but my drive is fat32 first and then ntsf but neater show up on the desk top. help would be nice..
also my floppy will not mount at all. howeve all mount in knoppix and simply mepis. I just like the way  Umbutu looks.

---

### Post by el3ktro on 2006-02-09
You can use the same commands - just adopt them to your needs. When you want to mount a FAT partition, you have to use the argument "-t vfat" instead.


Tom

---

### Post by NoJock on 2006-02-09
[QUOTE=el3ktro]You can use the same commands - just adopt them to your needs. When you want to mount a FAT partition, you have to use the argument "-t vfat" instead.


Tom[/QUOTE]
Lee here the make directory works but when i do sudo mount -t vfat /dev/hda1/c 
the return is a promt for usage adnd quite lenthy.

---

### Post by NoJock on 2006-02-09
Ok im using the Live CD and that did not work. Thanks

---

### Post by LordBug on 2006-02-09
Mount follows the format of:

"mount {options} {device} {mountpoint}"

So, for FAT, you'd do something like this:

"mount -t vfat /dev/hda1 /mnt/fat"  (please note this is only an example!)

You'll need to provide the valid device and mountpoint for your setup.

---

### Post by caven80 on 2006-02-10
[QUOTE=jonathanm]add uid=[username] into the options of your fstab, where it should read defaults, that should do it[/QUOTE]


Hi..

I followed the above quoted method to always be logged on as root and peform any commands without typing da word 'sudo'.

Now i cannot boot into Ubuntu..its giving me some error, so i booted into Ubuntu -recovery mode, and tried to restore the fstab file, which i had backed up earlier, n it says 'Read Only, Cannot Write to File'..

Please Help!!!

---

### Post by el3ktro on 2006-02-16
[QUOTE=caven80]Hi..

I followed the above quoted method to always be logged on as root and peform any commands without typing da word 'sudo'.

Now i cannot boot into Ubuntu..its giving me some error, so i booted into Ubuntu -recovery mode, and tried to restore the fstab file, which i had backed up earlier, n it says 'Read Only, Cannot Write to File'..

Please Help!!![/QUOTE]

You're getting something wrong here. The quoted method (uid=xxx) dosn't let you be "logged in as root". Ok please tell us:

Which device is your D: partition: Is it /dev/hda1, hda2, hda3 ...? If it is your SECOND partition on your harddrive, which is very likely then it's /dev/hda2.

Now, create a directory where you want your Windows files from D: to be, e.g. type

"mkdir /media/windows" or "mkdir /media/data" or "mkdir /media/d_drive" or whatever. Let's assume you have the latter, /media/d_drive, then you can mount your Windows partition like this:

sudo mount -t vfat /dev/hda2 /media/d_drive

This WILL work, if it doesn not, then your FAT partition is somehow corrupted. If you want to automatically mount your D: partition on every boot, then put the following line into your etc/fstab:

/dev/hda2     /media/d_drive     vfat     uid=1000,gid=1000     0 0

This will mount the partition whenever your computer boots. The uid and gid arguments tell mount to give you the ownership of the mounted files.


Tom

---

### Post by lucipherous on 2006-02-16
I know a lot of guys have already helped u with the problem. My suggestion would be to read this page

[http://easylinux.info/wiki/Ubuntu#Windows](http://easylinux.info/wiki/Ubuntu#Windows)

Its simple to understand and should have answers to all ur queries.

---

