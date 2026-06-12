---
title: "i need help with an external hard drive please"
date: 2012-12-15
forum: Hardware
---

### Post by iamrandy on 2012-12-15
i have 12.04 and i just got this wd 320gb external and it won't let me copy anything to it can someone please help

---

### Post by TOMBSTONEV2 on 2012-12-15
sudo chown your user name /media/name of drive

or sudo chmod 777 /media/name of drive

There is also a storage device manager called Pysdm, it automatically adjusts settings for the drive. I have never used it myself. I think "sudo apt-get install pysdm" will install it for you if you wanted to go that route.

I believe this should do the trick.

---

### Post by oldfred on 2012-12-16
What format is external drive? 

Did you partition it? Or did it come already formatted and partitioned? We have seen a few users with drives without partitions, but formated. They then work like an old floppy drive, but many things then do not work as there are no partitions.

Post this with drive connected.

sudo fdisk -lu

Many find labelling the partitions helps. You can use Disk Utility to label the partitions.

---

### Post by Bucky Ball on 2012-12-16
*Thread moved to **Hardware***

---

### Post by rajhanschinmay on 2012-12-16
To mount the drive, click on the drive in explorer.
or use command
sudo mount /dev/sda1 /media/drive_name

where sda1 is the first partition of the disk.

To know which is which drive, use command:
df

To give all access to read, write and execute, use the following command.
sudo chmod 777 /media/drive_name

Thank you.

---

### Post by iamrandy on 2012-12-16
ok this is what i got[ATTACH]228768[/ATTACH]

---

### Post by john vaughan on 2012-12-16
Hi, I had the same problem and made a post under General Help and received a reply that worked perfectly. Look for the post entitled "logging in as root"  posted about 35 minutes ago by john vaughan and the reply by Coffecat works perfectly.

---

### Post by oldfred on 2012-12-16
I think part of the issue is spaces.

In you terminal command line you need a space after the 777.

And in your mounting, it looks like it is automounting by label but you have spaces in your labels. Linux does not like spaces and you often have to put entire label in quotes or escape the space to make it work correctly.

       I learned a while back to stop using spaces. Use CamelCase or under_score or just onename. Windows will work without the spaces and it makes things a lot simpler in Linux.

---

### Post by iamrandy on 2012-12-17
ok i got it to work thank you guys i appreciate it proof again this forum is all about helping each other out  i've not had a problem go unsolved yet

---

