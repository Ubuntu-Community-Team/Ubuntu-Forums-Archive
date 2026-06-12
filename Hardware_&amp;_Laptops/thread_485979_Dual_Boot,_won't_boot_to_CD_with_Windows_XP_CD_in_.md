---
title: "Dual Boot, won't boot to CD with Windows XP CD in drive"
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by billwrtr on 2007-06-27
I have an HP zv6000 laptop. I have Feisty 64 bit co-existing quite well up to now in a dual boot with Windows XP Pro SP2. 

Here's the problem:
Windows has some corrupt system files. To fix it, I want to boot to the Windows XP CD to do a Windows reinstall. 

Something in the dual boot stuff won't allow me to boot to the Windows CD. I can boot to that CD on another computer. I can pop a different (not dual boot) hard drive in the laptop, and I can boot to the Windows CD in this laptop. Ergo, the problem in somewhere around Grub, disallowing a boot to the Windows OS CD. 

Anyone have any ideas on what to fix? (before I get desperate and wipe the hard drive clean and decide whether I want to try again with the dual boot configuration or what.)

Thanks in advance.

Bill

---

### Post by BobLand on 2007-06-27
Does your bios have the correct boot order?  The first boot device should be the cdrom.  If you're not sure how to do this, reboot the machine and enter setup.  On some machines the del key gets you there.  On others it could any key so watch the screen very carefully.

Once you get there you should see a tab with something like Boot.  Understand that my experience is with a very old bios and that's the way it works on my machine.

Assuming you get there, you should find a page or selection that allows you to set the boot order.  Once you do that, save the settings and the machine should reboot.  Make sure the cd is in the drive.  You should be good to go.

If this is all to obvious...sorry.  Better to be redundant then WTF????

BTW, I'm having a similar problem.  Partition Magic trashed my boot partition and Windows is having a fit.  I've been doing this all day and still not there...

bobland

---

### Post by billwrtr on 2007-06-27
> **BobLand said:**
> Does your bios have the correct boot order?  The first boot device should be the cdrom.  
bobland

Sorry, I forgot to add that detail. Other bootable CD's boot fine on the laptop. Just the Windows OS CD creates the problem.

---

### Post by xzero1 on 2007-06-27
Booting from a cd does not require a hard drive. Your xp cd is probably checking for something on your hard drive and does not like something. It is probably doing this to protect your hard drive contents.

---

### Post by billwrtr on 2007-06-27
> **xzero1 said:**
> Booting from a cd does not require a hard drive. Your xp cd is probably checking for something on your hard drive and does not like something. It is probably doing this to protect your hard drive contents.


Agreed. So the question is, "What could it be seeing that it doesn't like? And is there a way to get rid of it?"

---

### Post by xzero1 on 2007-06-28
Not sure, but here is my working theory:
Grub has replaced your master boot record with something unknown to xp. When booting xp, it makes xp believe the original MBR is there. The MBR must be restored or cleared. The problem is the MBR contains your partition table! 

I have a similar problem (xp wont boot) and my plan is: 
back up the first track of the hd to usb drive,
extract the partition table information (print it),
clear the MBR with xp recovery cd (which boots for me)
get xp to boot hopefully without a full reinstall
reinsert the partition table info manually
install grub (but not to MBR) ?? [http://linux.ioerror.us/2006/01/where-should-you-install-grub/]("http://linux.ioerror.us/2006/01/where-should-you-install-grub/")
see what happens

Since I can at least boot the live cd or dos, I should be safe enough.
For background info I recommend this link;
[http://mirror.href.com/thestarman/asm/mbr/index.html#PT]("http://mirror.href.com/thestarman/asm/mbr/index.html#PT")

---

