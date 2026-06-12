---
title: "Upgrade to 9.04 ran afoul of moodle"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by cposubs on 2009-05-07
I am new to Linux and recently installed Ubuntu in a dual-boot configuration on my desktop. My existing OS was Windows XP, SP3. I was enjoying the use of my "new system". :guitar: After a while, I received a notification on screen (I was running Linux at the time) that 9.04 was available for downloading. I agreed and started the download/installation. 
 
Everything went fine until the system encountered the Moodle program that I installed for "tinkering with" later on. At this point, the system predicted installation complete in 2 minutes and asked for my FQDN. Since I am not running Ubuntu as a server, I attempted to bypass this information... Bad choice.
 
Now, Ubuntu will not fully boot. I get to a white screen and the OS will not finish loading. The HD seek indicator LED becomes inactive. [-o<
 
Do I need to run an ISO image that I have of 9.04 to remove Moodle? Would it be better to just reinstall 9.04 from the image? Will that impact my Windows partition?What would you recommend? :confused:
 
Thanks ahead of time...
 
Bruce
(aka CPOsubs)

---

### Post by Kareeser on 2009-05-07
Moodle server?

What is the output of the command "hostname"?

(I'm going to fully admit I'm grasping at straws here...)

---

### Post by cposubs on 2009-05-07
Don't remember and my Linux is "Tango Uniform."

---

### Post by HyRax on 2009-05-07
> **cposubs said:**
> Everything went fine until the system encountered the Moodle program that I installed for "tinkering with" later on. At this point, the system predicted installation complete in 2 minutes and asked for my FQDN. Since I am not running Ubuntu as a server, I attempted to bypass this information... Bad choice.
 

By default, any standalone workstation's FQDN is machinename.local so if you called your PC "fred", it's FQDN would be fred.local ok?

As for the stuffed install, cut your losses and just reinstall from scratch. Since you're not worried about losing Moodle, just do a straight install. If your /home is on a separate partition, Ubuntu will happily preserve whatever you've got there via manual partitioning, and don't worry about Windows - Ubuntu will see it and deal with it accordingly with the GRUB menu.

---

### Post by cposubs on 2009-05-08
Thanks!  I'll let you know what happens!

---

### Post by aarav on 2009-06-30
hi
I have the same problem. When I upgraded my Ubuntu, I lost my Moodle which was being hosted on my Ubuntu machine. Do I have to uninstall and reinstall Moodle or could it be a minor problem with some components of Apache, Perl or MySql, how do i test this.
aarav

---

