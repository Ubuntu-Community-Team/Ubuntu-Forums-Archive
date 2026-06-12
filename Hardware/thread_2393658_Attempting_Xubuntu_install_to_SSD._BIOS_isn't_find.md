---
title: "Attempting Xubuntu install to SSD. BIOS isn't finding SSD"
date: 2018-06-06
forum: Hardware
---

### Post by kirbo719 on 2018-06-06
Attempting to install Xubuntu v16.04.3 LTS to a new WD Blue 500gb SSD in an ancient Dell Inspiron 1525 with 3gb RAM.

Steps taken:

On another Xubuntu computer, using a USB3 - SATA cable, used GPARTED to partition (gpt) the SSD, then format one large partition as Ext4. No problem, there was nothing remarkable about the process. I was able to mount and view that volume in file manager on that machine.

Installed the SSD in old Dell Inspiron 1525 laptop. Selected AHCI. Upon boot, obtained error "Cannot find an operating hard disk. Try to re-seat the hard drive."

Booting Xenial Xerus from live CD, then attempting to install the OS, obtain message "Xubuntu needs nn GB to install. This machine has 0 gb," etc.

This certainly seems like a mechanical/physical-contact issue of the SSD not seating itself correctly into the SATA and power socket. But plugging-in a 2-1/2" drive in the socket is pretty fool proof. And, there was no need to apply force when seating the SSD.

SATA II is backward-compatible with SATA I - I think? This is a 9-year-old laptop, and probably SATA I. 

Before I take the back off the laptop, I thought I would throw this to the brain trust to see if I'm forgetting anything prepping the SSD for use.

Thanks in advance!

Bob

---

### Post by Autodave on 2018-06-06
Sounds like a bad cable or SSD to me.  But before you remove the back again, try this: disconnect power cord. Remove battery. Leave battery out for 5 minutes. Make sure that there is NOTHING connected to any port! Re-install battery after 5 minutes and see if the SSD is found then.

---

### Post by Yellow Pasque on 2018-06-07
The Inspiron 1525 supports SATA 3.0 Gbps (on both Intel and ATI/AMD models).

I would update the BIOS to the latest version (A17)
Also note that you should be using a spacer if your SSD came with one: [https://en.wikipedia.org/wiki/Dell_Inspiron_1525#Upgrade](https://en.wikipedia.org/wiki/Dell_Inspiron_1525#Upgrade)

---

### Post by oldfred on 2018-06-07
If using gpt with BIOS boot you need a 1 or 2MB unformatted partition with the bios_grub flag.
It can be anywhere on drive, but must be within first 2TiB of a drive. (not an issue for you).

Grub will not correctly install to the protective MBR of the gpt drive without the bios_grub.

       However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img. 
   In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

---

### Post by Yellow Pasque on 2018-06-07
@oldfred: Would a new 500GB SSD come partitioned with GPT?

---

### Post by oldfred on 2018-06-07
New drives are not partitioned, you need to do that first.

I use gparted, but you can use gdisk.
        Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or
sudo parted /dev/sda mklabel gpt 

      
 GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Yellow Pasque on 2018-06-08
Oh, sorry. I missed the part where the OP said s/he partitioned it using GPT. I would opt for classic MBR for least hassle.

Yeah, I like those rodsbooks links too.

---

### Post by oldfred on 2018-06-08
There are several knowledgeable users, that post here and prefer the now very old MBR. It is well known.
But UEFI needs gpt.

And the author of gdisk used to post here and converted me to gpt back in 2010 with BIOS boot. I like that all partitions are primary, limit of 128 primary partitions vs 4 or no hassle on adding partitions. I also like that it has backup at end of drive. Sometimes able to recover a drive where beginning is overwritten.

---

### Post by Autodave on 2018-06-08
It just bothers me that the BIOS isn't seeing the HD: regardless of how it is/isn't formatted.

---

### Post by oldfred on 2018-06-08
If BIOS/UEFI does not see a drive, then usually a hardware issue.
First check connectors, sometimes they come loose. Or are broken.
Otherwise may be drive failure.

And if BIOS/UEFI does not see a drive, then no operating system will be able to see it.
But they are two entries typically in BIOS/UEFI. One is that drive is mounted using AHCI, not IDE nor RAID, and the other is whether configured as bootable and then shown in boot menu.

---

### Post by kirbo719 on 2018-06-12
Indeed - just as the error message stated - it was a hardware issue. The SSD was not seating itself in the SATA socket inside the Inspiron 1525 laptop computer.

I loosened the laptop's bottom cover, and RAM memory panel, enough to be able to view the insertion of the SSD. It certainly did want to slide under the socket. With just slight reorientation as I inserted the SSD, it successfully mated to the SATA socket, the computer acknowledged the new hardware, and I was able to install Xubuntu v18.04 LTS 64-bit. 

Thanks all for your contributions. I have some questions about partitioning with GPT.  (The machine takes 2+ minutes to boot with "time out" error messages I will document elsewhere as appropriate.)

---

### Post by kirbo719 on 2018-06-12
OldFred: After reading an article about SSD "provisioning" I left some 40gb unallocated on the SSD.

Now, however, just from the context of one of your replies, I infer GPT may not be the preferred partitioning protocol for an Ext4/linux install. In gparted, that and "dos" or "msdos" were the only protocols that looked familiar. Which protocol would you recommend?

I did the install -- 64-bit version of Bionic Beaver -- and am getting boot time errors "atomic handler... flip... timed out" although after 2 or 3 minutes it does boot into the OS.  I videod a boot and will transcribe the actual error msgs and post appropriately if other threads don't point out the solution to this issue.

With only 3gb RAM, I'm thinking this elderly laptop might be a good candidate for a 32-bit install.

Thank you in advance for your thoughts.

---

### Post by Autodave on 2018-06-12
Running Xubuntu 18.04 on a similar machine with an SSD: 22 seconds boot time.

I used the entire drive: no dual boot. I left the installer do everything: ERASE ENTIRE DISK AND INSTALL XUBUNTU. No fancy partitioning: just as simple as it gets.

---

### Post by kirbo719 on 2018-06-12
I think not. It was unreadable by a Win9 machine and by a Xubuntu v16nn machine.

---

### Post by kirbo719 on 2018-06-12
OldFred: Thanks for the EUFI link.
Recently bought some old, cheap Dell refurbs (Optiplex7010), the first machines I've used offering EUFI. I attempted EUFI installing Xubuntu v16.nn 64-bit and there were enough error msgs during install I reverted to BIOS. I will study up on EUFI.

---

### Post by kirbo719 on 2018-06-12
AutoDave:
Upgrading this old Inspiron1525 with an SSD is hobby stuff. I can blow it up and start over and may do as you have done. I will say: once this geriatric laptop DOES boot -- she's fast!
Just FYI, here's how I typically partition:
/
/home
/mnt/backup
(and for this SSD, about 40gb unpartitioned for future "provisioning" use by the SSD as memory wears out and fails).

---

