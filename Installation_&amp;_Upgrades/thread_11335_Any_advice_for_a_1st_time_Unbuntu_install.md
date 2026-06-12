---
title: "Any advice for a 1st time Unbuntu install?"
date: 2005-01-16
forum: Installation &amp; Upgrades
---

### Post by wingnut2292 on 2005-01-16
:?:  Hello!  my name is Ian, and I am hoping to switch from Suse9.1 to Ubuntu.  While i'm not a stranger to Linux, or Operating Systems in general, I was wondering if any sesoned pros have any advice to impart.  I plan to partition my HD in a davance w/ QTparted (form Knoppix) and have Grub as my bootstrap loder.  What file system should I use? Ext3, Riser, Xfs?  I figured I should post here now to avoid a post here later. 

Thanks in advance!  :D

---

### Post by wallijonn on 2005-01-16
I prefer EXT3 because reiserfs supposedly always keeps the disk rotating and xfs is really made for large databases.

Going from SUSE to Ubuntu may either be a pleasant surprise or a shock as GNOME does things a little differently and you'll have to tweak, tweak, tweak to install everything you want in Ubuntu as opposed to removing packages in SUSE. 

Having been on SUSE9.0 I have no temptation to try SUSE9.2, not if I have to remove Mozilla to install Firefox, remove KDEOffice, ABIWord, et. al., etc. I used to love Konqueror but now prefer a browser that is not integrated into the desktop. 

After you download some themes, GDMs, icon sets, etc., and install xine, you should be all set up with a fine looking & performing desktop. Since you already use Evolution you'll be ahead of the curve, not having to install Thunderbird. 

Just make sure that you make full use of the HOWTO/FAQ section and hope that you do have a motherboard that isn't completely supported.

---

### Post by Xian on 2005-01-16
I use Reiserfs but Ext3 is fine as well. If you are already using SuSE then just use the partitioner in YaST to set your disk for Ubuntu. It provides an excellent GUI for parted, auto-copies all your changes to /etc/fstab, and even creates the proper mount directories. Of course, if you are dumping it completely I suppose it woudn't really matter.

---

### Post by Lynx on 2005-01-17
Going from suse to Ubuntu was a wonderous experience for me. Suse was my first experience with Linux and I was sorely disappointed as I was not able to customize nearly as much as I expected from linux and changing from KDE to gnome was awful. Gnome was a beautiful experience for me and I didn't have trouble with anything on the install. I have been able to customize everything I desired though I love Gnome's default layout with only minor tweaks to the superficial system. Anything I have needed to do has been swift and painless once I have found out generally how to accomplish it. I am still a linux n00b though and have yet to really delve into the system but I can say that my switch was very pleasing.

---

