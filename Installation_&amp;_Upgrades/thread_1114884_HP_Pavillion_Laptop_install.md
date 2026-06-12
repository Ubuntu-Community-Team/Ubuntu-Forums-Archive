---
title: "HP Pavillion Laptop install"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by Thermalsocks on 2009-04-03
I am trying, unsuccessfully, to instal Ubuntu 8.10 on an HP Pavillion DV5-1110em laptop as a dual boot with Windows Vista.  I have tried the 64 bit version and the 32 bit version but both hang after I select the install option from the menu.  I have tried to select safe video mode and I have searched the forums and help etc.. but can't seem to get it to go...anyone any ideas or should I just give up and try another linux os like Suse?

---

### Post by wfeltmate on 2009-04-03
I have the DV5-1008ca and I was able to install Ubuntu just fine. What version are you trying to install and did you verify the md5 of the iso you downloaded or ran the Verify media option before installing?

---

### Post by Thermalsocks on 2009-04-03
Thanks for your help...

I am trying to install ubuntu version 8.10 32 bit (ubuntu-8.10-desktop-i386.iso).

I checked the CD MD5 it's ok.

but...after booting the CD and the menu page, selecting any option causes a hang, including install.

I turned off quiet and splash but only one line of install was shown at the top if the screen with a never ending line of full stops, I powered off after 2 hours of this, obviously nothing was happening.

I had previously freed up a partition on my Vista C: drive and have 55 GB available for ubuntu.

NOTE: I have successfully installed the same version on an HP desktop with no problems at all...took about 20 mins and is brillient !

I was hoping to use the 64 bit version as the Laptop is AMD X2 turion processor but this ubuntu 64 bit version also hangs in exactly the same way on install.

the full laptop spec...(it's brand new)

Processor AMD x2 Turion
Memory: 3 GB
ATI graphics (with hdmi)
Blue ray DVD/CDrom drive
250 GB  Sata hard drive
eSata port
Wifi
Built in webcam
and the usual other devices...usb, ethernet, modem etc...

---

### Post by Pasdar on 2009-04-03
I have the same exact issue on my laptop:

Asus X56TR-AP039C
T64 X2 RM-70, 4GB, 15.4", ATI Radeon 3470, 320GB

I just get a black screen and thats it, I have to hard boot. I will attempt to run the LiveCD again upon release of 9.04.

---

### Post by Thermalsocks on 2009-04-03
I have just updated the bios from f.11 to f.31, but it made no difference....

I have no confidence that ubuntu 9.04 (or whatever the new version when released will be) will be any better...

I will also buy some top quality CD blanks...and burn it on different computers and cd drives...with different software...you never know.

;)

---

### Post by Pasdar on 2009-04-03
I don't think there is anything wrong with your burnt files on the current CD or your current CDr brand. I think Ubuntu is not compatible with new laptops. Though It seems to be very compatible with old laptops.

I kinda had the same issue when I tried to install a difference version of Windows on my laptop, what solved that issue was by setting the HD in bios to "Native IDE".

---

### Post by Simian Man on 2009-04-03
You can try the alternate CD.  It will not have a GUI during the install process though.  And try booting other distros to see if that works.

---

### Post by Thermalsocks on 2009-04-03
Firstly I'd like to thank everyone in the Ubunto community for their help in this matter...I have however resolved it in part.

The problem was media...I went out and purchased some new Sony 700mb cd-r 1x-48x disks and I burnt the .iso image to that media and low and behold it booted and started the installation !!!

I have however come across another problem in that the partitioning operation (4 of 7) in Ubuntu did not see the partition I had reserved for it when, using Vista, I shrank my Windows Vista partition(which previuosly occupied the whole disk) and instead Ubuntu tried to re-partition the remaining Vista partition but failed.  So I have aborted the attempt and will try again.

I will post the final outcome here for anyone who is interested.

My thanks again to those who have posted helpful comments here.

Ubuntu rules !!!

---

### Post by Mark Phelps on 2009-04-03
> **Thermalsocks said:**
>  and instead Ubuntu tried to re-partition the remaining Vista partition but failed.

Did you format the other partition (the one you made room for) using Vista? If so, it probably formatted it as NTFS -- and Ubuntu won't install on an NTFS partition.

Boot from the LiveCD, open the Partition Editor (System --> Administration --> Partition Editor) and remove the new NTFS partition.

When you restart the Ubuntu installer, it should see the unallocated space and allow you to install to it.

---

### Post by Thermalsocks on 2009-04-03
Thanks Mark,

Actually what I did in the end was to remove the partition in Vista and make the whole disk Vista again (expanded) and then I let Ubuntu pick 50GB for itself during the Ubuntu install...this seemed to work and now.... I have a 64 bit ubuntu 8.10 dual bootable with Vista on my laptop :D  Whooohooooo !!!

Now all I have to sort out is wireless wifi and/or t-mobile 3G mobile broadband...neither works at the moment so I can't do the updates but I'll get there, I feel the caffine fueled plus 6 spoonfuls of sugar rush of success is just around the corner :)

It's worth it when you get there so anyone else having trouble installing on a laptop just keep going, keep trying...and keep smiling :D

---

