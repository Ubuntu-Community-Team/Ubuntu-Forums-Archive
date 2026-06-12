---
title: "How To: Dual-Boot Ubuntu 7.10 and XP Pro on a Dell 1420"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Dodger USMC on 2008-03-23
How to Dual-Boot Ubuntu 7.10 and XP Pro on a Dell 1420n

A few days ago (March 2008) I purchased a Dell 1420 preloaded with Ubuntu 7.10 (Gutsy). It came with a 2.2 Ghz P4, 4GB RAM, 160GB SATA HDD, Wireless-N, and integrated Webcam. Now this is my first experience into any Linux environment, and I found myself fairly lost as to how to dual boot with XP. The following is a step by step guide on how I took an out-of-the-box 1420 with Ubuntu 7.10 and put XP Pro on it too.

Note: When this system came to me, the partition table looked like so: 
/sda1 FAT16 80MB (Dell's Restore Partition)
/sda2 FAT32 5GB (Dell's Restore Image)
/sda3 EXT3 140GB (Primary Ubuntu Boot partition)
/sda4 – Extended partition
 /sda5 EXT3 5.8GB (Swap Partition)

Since I knew that I did NOT want Ubuntu and XP to co-exist on a single partition, the first thing I did was to boot off the live-CD and shrink the Ubuntu installation by about half. This now left me with an un-formated chunk of 70GB on the drive. 

Great says I, so now I reboot, pop in the XP CD,  but it cannot find any hard disks. Hmm. I finally figure out that XP doesn't recognize the 160GB SATA drive that came with the Laptop. I went to Dell's site and downloaded the SATA drivers (320KB) and then downloaded a program called nLite. This article: [http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml](http://news.softpedia.com/news/Install-Windows-XP-On-SATA-Without-a-Floppy-F6-47807.shtml) helped me out immensely. 

Once I had the Driver on the XP disk, I booted up the XP disk and try to format... but NO! I have reached my 4 partition limit. To make this section very short, I ended up having to remove a partition in order to allow window to allow me to make a new partition. Since the Dell reinstallation image is readily available online to download, I booted off the live-CD and I chose to wipe both the FAT16 and FAT32 partitions. Afterward a trusted friend told me that any FAT16 partition is a security risk, though I have yet to confirm that.

So now I have a 5.1GB unpartitioned space, the 70GB Ubuntu partition, the 70GB unpartitioned space, and then the 5.8 GB Swap. In order to avoid problems with the leading 5 gigs of emptyness, I chose to grow the Ubuntu partition by the 5 GB. This alone took about 2 and a half hours, so go get some lunch.

Once the grow completed, I again booted off the windows CD. This time it let me format the partition. So now I have XP installed, and the system will boot into XP. Almost there!

I restarted and booted off the live-CD, and now I needed to reinstall GRUB on the Master Boot Record.  After a great deal of trial and error, this is what to do: First run Gparted off the live-CD and right click on the NTFS partition (this is windows) and click on manage flags. Uncheck the 'boot' option. Now right click on the EXT3 partition (this is Ubuntu), click on manage flags, and this time check the 'boot' option. Now to reinstall GRUB, I opened a terminal window and typed:
sudo grub
find /boot/grub/stage1 <- showed me the current boot partition
root (hd0,0) <- changed the active partition to the first one (Ubuntu)
setup (hd0) <- installed GRUB to it

At this point I rebooted with a smug look on my face only to be presented with an “ERROR 17” message. I discovered that this basically means your computer is saying, “I cant find any operating systems!! Help PLZ!” For the next hour or so I played with the GRUB loader, and with the GRUB loader in Ubuntu, with almost no effect. That is until I stumbled upon this guide over at APCMag: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp) and it explained how to get GRUB to remember all these things I was telling it. It turns out that for some reason, GRUB didn't see my partition tables correctly and needed to be told proper what to do. That's right – proper.

From the failed ERROR 17 window, I entered into the GRUB setup screen, hit 'e' to edit the lines, and modified the first line that read 'root (hd0,2)' to read 'root (hd0,0)'. Since (hd0,2) is now the swap partition, there was my error. Now that the line reads 'root (hd0,0)' I hit the 'b' key to boot and Ubuntu loaded without a problem. 

Now to change the GRUB files to remember that I want hd0,0. Open a terminal and type:
sudo gedit /boot/grub/menu.lst
This opened a text configuration file for GRUB. I scrolled all the way to the bottom until I found the section where it read:
title	Ubuntu 7.10
root 	(hd0,2) <- Ha HA!
And here I changed it to (hd0,0).

Then I make a new boot option by typing:
title	Windows XP Pro
root	(hd0,1)
makeactive
chainloader	+1
This sets up a new option in the GRUB loader to allow XP to boot up without a hitch.

Whew. Finally done. A quick note: This setup made XP install to the F: drive. It makes some installs a bit weird, and thought you might like a heads-up.

I hope someone out there finds this article useful!

Semper Fidelis!
-Dodger

---

