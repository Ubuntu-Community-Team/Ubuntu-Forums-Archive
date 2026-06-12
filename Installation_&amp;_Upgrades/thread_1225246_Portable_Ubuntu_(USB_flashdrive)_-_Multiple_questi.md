---
title: "Portable Ubuntu (USB flashdrive) - Multiple questions..."
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by Veazer on 2009-07-28
I would like to create a portable Ubuntu installation on a USB flash drive and I have a few questions for those who have ventured down this path or have any advice.


[LIST=1]
[*]Should I use a live version with persistence or install to the USB drive? The live versions seem to be aimed at temporary use/testing and I’ve had issues installing new apps and features from repositories. It seems like performance should be higher for a real installation as well. I’d like to avoid the live version for these reasons, any reason I shouldn’t? Or is installation only an option for use on one machine, like windows?
[*]I would like as much of the file system encrypted as possible, with the internet cache and user docs obviously most critical to be encrypted. Ideally, I would like systemwide encryption similar to how Truecrypt can be setup on windows, requesting a password before bootup. From what I have read, this is possible with [LUKS]("http://ubuntuforums.org/showthread.php?t=1205287") now. Would this be the best way to go?
[*]I am worried that some users will have issues booting to the USB drive, so I’d like to have the option of running from Windows. The usbuntu live creator does this by adding a virtual box installation and using FAT32, BUT it only (?) works for live versions as I understand it. Would it be possible to do a full install and still take advantage of this? I assume that needed virtualbox functionality means i am force to use FAT32 for the entire drive. The portable OS will likely be used in a few older machines, should i opt for a lighter distro like Xubuntu?
[/LIST]

---

### Post by Mighty_Joe on 2009-07-28
> **Veazer said:**
> 
Should I use a live version with persistence or install to the USB drive. . . It seems like performance should be higher for a real installation as well. 
A full install is faster than the Live CD, if only because the Live CD is compressed.

> **Veazer said:**
> 
Or is installation only an option for use on one machine, like windows?
I've used my full install on a USB flash drive on several systems without any problems.

> **Veazer said:**
> 
I would like as much of the file system encrypted as possible, 

I haven't messed with encryption.

> **Veazer said:**
> 
I am worried that some users will have issues booting to the USB drive, so I&#8217;d like to have the option of running from Windows.  
I'm not sure what you mean.  Are you running Ubuntu in a VM or Windows in a VM?  From the flash drive?
I know for a fact that Ubuntu requires a Linux file system for a full install and will not let you mount / or /home on a FAT32 partition.

> **Veazer said:**
> 
should i opt for a lighter distro like Xubuntu?

Depends on the specifications.  Xubuntu is good for machines that have between 256 and 512Mb of memory and a relatively recent processor.  If you have less than that, best look at DSL or Puppy.

---

### Post by aquateen.carl on 2009-08-04
So it is possible to do a full install of ubuntu onto a usb drive then plug the usb drive into other systems and boot. I just tried this with hardy and then plug into another system but it just sat at grub. I tested on the machine I installed from worked fine. However, the other machine has an amd processor and the original is an intel dual core.

I've been trying to get this to work all day. I started with this 
article here: [http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive]("http://rudd-o.com/en/linux-and-free-software/a-better-way-to-create-a-customized-ubuntu-live-usb-drive"). Which worked fine, but the issue is I can only make the persistent file system a maximum of 4gb. That just won't do for programs and my data; especially since I have 320gb usb drive I'm using for this. I can't even create a home outside the capser-rw file because of the fat32 issue you mentioned. 

I think what Veazer is talking about in regards to the virtualization is something like this:
[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/]("http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/") but on a usb drive. I too would to do this but I think it would be too much for a usb port ;)

What do you think?

---

### Post by Mighty_Joe on 2009-08-05
> **aquateen.carl said:**
> So it is possible to do a full install of ubuntu onto a usb drive then plug the usb drive into other systems and boot. 


I've only tested two computers, both HP's.  [YMMV]("http://en.wiktionary.org/wiki/your_mileage_may_vary")

> **aquateen.carl said:**
> 
I have 320gb usb drive I'm using for this. I can't even create a home outside the capser-rw file because of the fat32 issue you mentioned. 

So you're using a USB hard drive (as opposed to flash drive)? You could probably create different partitions and mount those once Ubuntu starts up.

> **aquateen.carl said:**
> 
I think what Veazer is talking about in regards to the virtualization is something like this:


That just looks like instructions to install VirtualBox.  I think Veazer is looking for a backup way to start Ubuntu if the system in question can't boot the USB drive.  
The way I parse his question, I think he wants to boot Windows, then run Ubuntu in the VM using the USB drive.  I know VMware will not boot from USB. I don't know about VirtualBox.  It sounds like it [cannot and the work-around is non-trivial]("http://agnipulse.com/2009/07/boot-your-usb-drive-in-virtualbox/")

---

### Post by aquateen.carl on 2009-08-05
When I got to work I plugged my usb drive into my machine (intel p4 single core with HT) and it worked fine. Both the original system I did the installation on, and my work machine were Dell's though. This was the whole reason I was trying this; so I'm happy. I just followed this guide: 
[http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/"). My guess is I should be able to encrypt the drive as well, which is something I was also interested in doing. Now if I get laid off or leave for another job can easily take my stuff and configured admin tools with me. :-\" Plus, it
will allow me to be become more proficient in *NIX since I'll be primarily
using this and nothing else. 

Thanks for the quick reply.

---

