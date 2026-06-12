---
title: "external NTFS drive mount issues with Hardy Heron"
date: 2008-10-04
forum: Hardware
---

### Post by nickstar on 2008-10-04
Hi guys,

I'm totally new to Ubuntu, and even though I thought I knew a bit about computers, linux has definitely shown me my limits :)

so. im using 8.04 and I installed ntfs-config 0.5.5. I've got an external USB drive that is formatted in NTFS, as it was my main storage drive when I was using win xp.

however every time i plug the drive in, or try to access it through Places>Freeagent Drive I get the message 'Invalid mount option when attempting to mount the volume'.

Ive had a bit of a sift through related problems on these forums, but theres a lot i dont understand. unfortunately ive been to busy to educate myself on the linux file system and how linux mounts drives so thats a huge black hole in my very limited knowledge base.

what makes my problem unique however, is the fact that if I first have my usb memory stick plugged into one of the other USB ports on my laptop (Dell Inspiron 1300), then I CAN access the freeagent drive and everything is apples.

Ive only got version 0.5.5 of ntfs-config. I know there is a 1.0.1 version out there, but all I can find are the versions suitable for earlier versions of ubuntu.

synaptics shows that ive got version 1.2216 of ntfs-3g.

if some one could please help me on this one, id be ever so greatful. Im really busy at the moment and I cant afford to spend a couple of hours digging and troubleshooting. thanks so much in advance!

---

### Post by nickstar on 2008-10-05
any tips anyone? please?

---

### Post by olsonco on 2008-10-31
nickstar,

I'm surprised noone has replied to your question yet.  

I think the solution is fairly simple, the kind of thing that will probably be fixed in future versions of Ubuntu.  

Intrepid Ibex was just released ... you may want to upgrade to see if it fixes the problem.  To upgrade from Hardy Heron to Intrepid Ibex, type Alt-F2, then type "update-manager -d" (without the quotes).   It should tell you "New distribution release '8.10' is available."  Just hit the "Upgrade" button.

But I'm running Hardy Heron and had a similar problem.  If you don't want to take the time and trouble to upgrade yet, I found a solution here that worked for me:

[http://ge.ubuntuforums.com/showthread.php?p=5397041](http://ge.ubuntuforums.com/showthread.php?p=5397041)

Since you mention you're new to Linux, I'll step through the process.

1) Open a terminal (Applications -> Accessories -> Terminal)
2) Backup the file /etc/fstab (in case you break something) 
3) Then as the root user ("sudo" means to run a command as root) edit the file.  

The lines you type in the terminal for steps (2) and (3) are

sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab

When you use the sudo password, it will ask you for a password.  Use your normal user's password, not the root password.  Nano is a text editing application like Notepad in Windows.  Your original /etc/fstab should look something like the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=54186cd3-c4c0-463f-b2ef-6318bff79a94 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9c92723e-97cd-4e8d-962a-7b17a0be0970 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Comment out the line starting /dev/sdb1 and save the file.  Your new /etc/fstab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=54186cd3-c4c0-463f-b2ef-6318bff79a94 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9c92723e-97cd-4e8d-962a-7b17a0be0970 none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Heron seems to have a problem recognizing USB drives because it wants to mount them to the /dev/sdb1 device as a CD, only CDs have different kinds of file systems than USB drives.  

I'm not sure if the fact that your filesystem is NTFS will cause additional problems, so if that doesn't fix your problem, be sure to post a follow up and I'll look into it in more detail.

Hope this helps!

---

### Post by nickstar on 2008-11-11
hi oslonco,

why thank you very much! I had abandoned the problem due to time constraints, but decided to check out the thread this afternoon. I followed your walkthrough and it worked! One hash in difference and it works straight out of the box! a pleasant surprise on a tuesday night. thanks a lot!

---

