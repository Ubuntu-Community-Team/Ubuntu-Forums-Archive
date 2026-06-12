---
title: "Help with RAID PLEASEEEE!!"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by shahzafar on 2006-08-29
My system Specs:
Intel Celeron 1.2GHz with 256MB RAM
40GB ATA HDD
250GB external USB drive.

I installed ubuntu 6.06 server on the 40GB HDD and I selected option 2 while installing which partitioned my drive and installed ubuntu on one and the other is available for data storage. I was also able to mount the 250GB external HDD.
Now, I bought an Adaptec 1210SA RAID controller and two 250GB SATA drives and am trying to setup RAID1 with them. I used the Adaptec BIOS utility and configured RAID1 on it. Now, when I boot into the kernel, it recognizes the disks(new 250 GB SATA) and shows two disks individually. Should I mount both of them? Should I use dmraid and configure the RAID1 again? Can I setup RAID1 in my present scenario? With the 40GB primary drive, 250GB external HDD and these 2 new HDD's?
I am new to all this, so please try to help me.
I read a lot of posts about configuring RAID on ubuntu, but all of them talk about configuring new system and installing ubuntu to the RAID. I already have a server running and want to add two more disks to it in RAID1 configuration. Can this be done? Should I just have the two 250GB SATA drives and remove all other drives? Please help!!!!

I am just using this as a NAS for my home. 
Thanking you in advance,
Zafar.

---

### Post by John.Michael.Kane on 2006-08-29
Use the [**gparted-livecd**]("http://gparted.sourceforge.net/livecd.php") format/partition the space as your see fit,and mount it with the filesystem of your choice.

you should then be able to reboot,and have the system see,and use the drives.

**Note:**the adaptec 1210SA is software RAID, provided by the BIOS on the card. so you should not have to install any drivers.

---

### Post by shahzafar on 2006-08-29
I downloaded the ubuntu 6.06 server CD from ubuntu.com. For gparted-LiveCD should I download the Ubuntu Desktop CD?

---

### Post by John.Michael.Kane on 2006-08-29
you can get the gparted live-cd from here [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by gerbman on 2006-08-30
I found myself in a similar situation. I had a 40GB drive and two new 250GB SATA drives. In the end, it was simplest to ditch the 40GB drive and install a fresh copy of Ubuntu in a RAID 1 configuration using the two 250GB drives. It's pretty simple to do using the alternate install, and using 'mdadm' to monitor the array is very easy. You should also be able to use 'mdadm' to add a RAID 1 array to your existing system, but I don't have experience doing that (check the help screens).

---

### Post by the_ace on 2006-10-02
I have a RAID 1 configuration also using the Adaptec 1210SA. I have WinXP already installed on the array. Will I be able to use the alternate CD to install Dapper alongside WinXP? I already have the partitions setup from my previous install before I installed the RAID controller.

---

### Post by mgmiller on 2006-10-02
RAID can be challanging.  Most of the pci raid cards are not "real raid"  They are "fake raid".  the same way a pci winmodem is not a real modem.  You can get these cards to work as raid with some configuration work.  You are using your OS and cpu to handle the RAID duties.  A better way to do it is to use a real hardware RAID card that is linux friendly.  This offloads all the work onto the card and is transparent to the OS.  If you use one of these, you hook up the 2 drives, set up the RAID array in the cards bios and then install Ubuntu.  Ubuntu will only see 1 drive, which is correct.  The array should appear as only one drive.  A good, modestly priced card for this purpose is made by 3com.  It is model #80062LPKIT.  You can get it from newegg.com for about US $124.00.

You can read many linux/BSD Unix reviews of this card here:  [http://www.newegg.com/Product/CustratingReview.asp?item=N82E16816116030"]("http://www.newegg.com/Product/CustratingReview.asp?item=N82E16816116030"")

To read a LOT about linux RAID and many different cards with explanations about which are "real" and which are "fake",  follow this link:
[http://linuxmafia.com/faq/Hardware/sata.html]("http://linuxmafia.com/faq/Hardware/sata.html")

---

### Post by jon schroeder on 2006-10-06
mgmMiller hit it dead on.  I recently went with an inexpensive 'RAID' card and went through the BIOS set-up only to find that UBUNTU saw TWO SATA 300GB hard drives instead of one.  I will continue to explore configuration solutions in order to get a RAID 1 set up.  In the mean time I will be using a CRON job to back up data from one hard drive to the other.

Updated link for the RAID card mentioned: [http://www.newegg.com/Product/Product.asp?Item=N82E16816116030](http://www.newegg.com/Product/Product.asp?Item=N82E16816116030)

If anyone has any ideas on UBUNTU RAID1 configuration using a Rosewill RC209 ( [http://rosewill.com/Product/product.aspx?productId=433](http://rosewill.com/Product/product.aspx?productId=433) ) and two SATA drives [/dev/sda & /dev/sdb].  Ubuntu 6.06 already installed on seperate hard drive and I am adding these two hard drives as storage. ](*,)

---

### Post by Robbyx on 2006-12-27
> **mgmiller said:**
> RAID can be challanging.  Most of the pci raid cards are not "real raid"  They are "fake raid".  the same way a pci winmodem is not a real modem.  You can get these cards to work as raid with some configuration work.  You are using your OS and cpu to handle the RAID duties.  A better way to do it is to use a real hardware RAID card that is linux friendly.  This offloads all the work onto the card and is transparent to the OS.  If you use one of these, you hook up the 2 drives, set up the RAID array in the cards bios and then install Ubuntu.  Ubuntu will only see 1 drive, which is correct.  The array should appear as only one drive.  A good, modestly priced card for this purpose is made by 3com.  It is model #80062LPKIT.  You can get it from newegg.com for about US $124.00.



I am going up the wall trying to get my system stable. At the moment I have Win2k using a small part of a software windows raided drive. The balance is not formatted. 

I also have another drive that has Ub on it but there seems to be an electrical problem with that drive so I want to move Ub to the raid drive.

I have found a UK source for the 

3ware 8006-2LP - Storage controller (RAID) - 2 Channel - SATA-150 low profile - 150 MBps - RAID 0, 1, JBOD - PCI 64. I presume this is the same as you recommend above.

The firm gives no support just a low price. That's Ok because others charge a high price with useless support.

I presume I have to forget about my existing Ub installation and start anew on the raid drive. In broad terms what do I have to do to install this card and have it working on a new system? 

Robin

---

