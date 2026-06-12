---
title: "Beginner for new laptop - Thinking of Dell 15.6'' - i5-5200U with Intel HD Graphics"
date: 2015-06-29
forum: Hardware
---

### Post by sixtyfootersdude on 2015-06-29
Good Evening,

I am a Ubuntu beginner looking to setup my first machine.  I have never installed Ubuntu or Linux, but have worked on Linux boxes and am 
familiar with the command line, package managers, etc.  

I am buying a new machine and want to make sure that it will have reasonable Ubuntu support.  

This is the machine I am currently looking at: 

    [http://www.bestbuy.ca/en-ca/product/dell-dell-15-6-touchscreen-laptop-silver-touch-intel-core-i5-5200u-1tb-hdd-12gb-ram-windows-8-1-i5548-5000slv/10361616.aspx?path=b9d121a2ad8a4903e96e6fe5f6ecd6dcen02](http://www.bestbuy.ca/en-ca/product/dell-dell-15-6-touchscreen-laptop-silver-touch-intel-core-i5-5200u-1tb-hdd-12gb-ram-windows-8-1-i5548-5000slv/10361616.aspx?path=b9d121a2ad8a4903e96e6fe5f6ecd6dcen02)

When that when link inevitably dies, here are the specs: 

------------

Dell 15.6" Touchscreen Laptop - Silver Touch (Intel Core i5-5200U/1TB HDD/12GB RAM/Windows 8.1)

Model # - i5548-5000SLV 
Price   - $700.89

------------

Display
Screen Size - 15.6 in
Native Screen Resolution - 1920 x 1080
LED Backlit Display - Yes
Touchscreen Display - Yes
3D Capable Display - No
Convertible/Hybrid Display - No


Processor
Processor Type - 5th Generation Intel Core i5-5200U Processor (3M Cache; up to 2.70 GHz)
Processor Cores - 2
Processor Speed - 2.2 GHz
Processor Cache - 3MB


Storage & Memory
Hard Drive Capacity - 1TB 5400 RPM SATA Hard Drive
Hard Drive Speed (Revolutions Per Minute) - 5400RPM
SSD Function - Not Applicable
Solid-State Hybrid Drive - No
RAM Size - 12GB Dual Channel DDR3L 1600MHz (8GBx1 + 4GBx1)
RAM Type - DDR3
RAM Speed - 1600 MHz
Optical Drive - Optical Drive Not included
Built-in Memory Card Reader - Yes
Memory Card Reader-Compatible Memory Types - SD; SDHC; SD 3.0; MS/MS Pro


Graphics
Graphics Chipset - Intel HD Graphics 5500
Video Memory Configuration - Integrated


Audio
Speaker Wattage - Varies
Integrated Microphone - Yes
Microphone Input - Yes
Digital Audio Output - Yes
Hardware Volume Control - Yes


Inputs & Outputs
Webcam - 720p
Keyboard Language - Bilingual
Backlit Keyboard - No
Type of Pointing Device - Touch Pad
USB 2.0 Ports - 1
USB 3.0 Ports - 2
VGA Output - No
HDMI Output - Yes
HDCP Compliant - No
IEEE 1394 Input/Output - No
eSATA Port - No
ExpressCard/34 Input - No
ExpressCard/54 Input - No
IR Receiver - No
Other Input or Output Ports - HDMI 1.4a; USB 3.0 (2); USB 2.0 (1); Security Slot; Media Card Reader (SD; SDHC; SD 3.0; MS/MS Pro); Headphone/Microphone


Networking
Integrated Wi-Fi - Intel Centrino Wireless-AC 3160 + Bluetooth 4.0
Integrated Bluetooth - Intel Centrino-AC 3160 + BT


Power
Approximate Battery Life - Varies
Battery Type - 3-cell Lithium Ion (43WHr) Battery
Battery - Number of Cells - 3
Battery - Capacity - 43 Wh


Software
Pre-loaded Operating System
W8.1 Eng/Frn No Lbl; CAN
Operating System Language
Bilingual
Loaded Software
Microsoft Office Trial (OHT13M)

------------


I have done some googling for the Model number of of the box but didn't find anything especially interesting in regards to Ubuntu support.

I have also looked in the Ubuntu certified hardware list but haven't found anything: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

I guess to summarize, this is my question: 

    * Is there any reason this won't be a good computer to run Ubuntu on?  Anything obvious that I have missed?

    * Is there a better machine to run Ubuntu on?  I know about System 76 and am currently not interested in there machines, because 
        the price is not extremely compeditive and I probably do need a windows license every once and a while anyways.  Sounds like
        in the cases of returns, they are also a major hassle.  Plus Canadian/USA exchange rate isn't great right now.

    * Support for an external monitor, the trackpad?  

    * Support for the touch screen, web cam?  
    
    * There isn't a disk drive, problem?

    * More generally, what do I need to think about when choosing a machine to run Ubuntu on?  

Thanks!

Jake

---

### Post by sixtyfootersdude on 2015-06-29
Edit: I guess that I should also check to see if there will be wireless issues.

---

### Post by weatherman2 on 2015-06-29
Why not install Ubuntu first on the computer you have now?  You can always install it on a small external hard drive or even a flash drive, without disturbing Windows.  Just one caution: pay careful attention to the target hard drive where Grub will be installed during Ubuntu installation on an external drive.

Best Buy probably won't allow this, but you might find a store that will let you boot a live USB of Ubuntu, so you can see how well it works before you buy it.  If it doesn't work, you should be able to figure out which wireless card it has (try the command "sudo lshw -C network") and note it down, then figure out later from web searching how difficult it is to install drivers for that card.  FYI, these laptops with the same model number may be sold with different wireless cards.  Dell has done this routinely in the past, where different versions of the same laptop may have an Intel or Broadcom or Atheros wireless card.  The one you list above comes with an Intel wireless card, and I have used them in numerous Ubuntu laptops with excellent results.

Something else I always consider with a new laptop: how difficult is it to upgrade the hard drive?  This one has a 1TB hard drive, but many of us prefer to upgrade that to an SSD, as SSD prices have continued to fall. Sometimes you can access a laptop hard drive easily from the bottom of the laptop by removing a panel and a few screws; other times you have to take the thing completely apart which can be a big hassle and too daunting for some to attempt.  Every laptop design is different.  In a Dell, you may also want to upgrade the internal wireless card - someday, anyway - if it is easy to access.  Once you can physically access the card, replacing it is usually very easy, at least with a Dell and some other brands (not HP or Lenovo).  This laptop as you list it supposedly has an Intel Centrino 3160 AC card - slower than the Intel 7260 which is 2x2 not 1x1 with wireless connections to your router. 

For the OS, I would try to stick to an LTS version (like Ubuntu 14.04.2) if you are new to Ubuntu because it is supported for years (until 2019) whereas Ubuntu 15.04 is supported for only nine months - then you will be forced to upgrade if you want continued support.

---

### Post by sixtyfootersdude on 2015-06-29
Thanks for the reply!

I am planning on upgrading my machine anyways, and don't want to mess around with my current machine.  It is very dated and is ready to be retired.  

The drive and Wifi replacement is an interesting question.  Will consider that.  

Overall, if I pull the trigger on this machine what do you think the chances are that it will work?  I don't mind putting in a couple hours fighting with configuration to get setup.

Thanks for the LTS version tip.  Will probably go with that for the extended support option.  Seems like a good option.

---

### Post by weatherman2 on 2015-06-30
This is fairly new hardware - the Broadwell/5th generation i5 + chipset - and I always expect a few issues with the latest hardware in Linux.  However, Dell does have a history of selling Ubuntu on some of its machines, which makes it more likely that a new Dell laptop will work with Ubuntu.  And I have had good luck with Intel wireless cards.  So I suspect you will be OK, especially with Ubuntu 14.04.2.  If not, hope that 15.04 works better, even though it is not an LTS version.  (14.04.3 should come out at some point and that may work better if 14.04.2. doesn't.)

Are you planning to keep Windows 8.1 as a dual-boot option?  If so, that may cause extra complications regarding UEFI, though I haven't had to deal with that since 12.04 - maybe it is easier to deal with now.

Either way, I am extra cautious with a brand new machine, and usually the first thing I do before I even boot it is to make an image backup of the existing hard drive.  I use Clonezilla or other image tools to make such backups, to an external hard drive.  That way, I can always restore the machine to factory settings in case I ever wish to return it or, later, sell it.  (As much as I love Linux and dislike Windows, it is much easier to sell a used machine with Windows on it.)  If you think you are going to erase Windows and go 100% Ubuntu, you might keep the factory restore partition intact at very least so you can do a factory restore to Windows more easily.


Speaking of return it: Best Buy in the US has a decent return policy, I think - not sure what their policies are in Canada, if you are really going to order from them, but if it doesn't work out well with Ubuntu it might be nice to have the option to return it for a refund.

---

### Post by ajgreeny on 2015-06-30
If you are not dual booting with Win8.1 the UEFI boot should not present too many problems; you should even be able to use legacy BIOS/CSM or whatever Dell calls it, but if dual booting you will have to keep the boot system the same as it is now for Win8.1.

Read carefully through all the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which should help you with this in both the dual boot and single boot situations, and then come back with any more queries you may have.

---

### Post by sixtyfootersdude on 2015-06-30
@[weatherman2]("http://ubuntuforums.org/member.php?u=1931279")

Thanks for the response.  I am planning on dual booting, because I occasionally and rarely need to use windows.  I will make an image backup of the existing drive so I can restore.  That is a good trick.  What is the easiest way to do that?  Can I do it using the windows OS installed on the box?  Do I need to remove the drive and use another computer to make the image?  What about restoring?  

@[ajgreeny]("http://ubuntuforums.org/member.php?u=27747") 

Thanks for the link to the UEFI boot section.  I am planning on duel booting.  I have breezed through the UEFI doc and am planning on reading it in more detail post purchase.  Is this a reasonable plan?  Is this something I need to fully understand in order to purchase the computer or just to install Ubuntu?  

------------

Thanks for all the great replies.  This is an awesome community.  I am excited to join.

---

### Post by oldfred on 2015-06-30
While I normally suggest LTS and use LTS versions myself, with a very new system like that you may need to install 15.04. The 14.04 is now up to .2, so it has many of the updates.

Intel is one of the better vendors at updating code for its new processors, video chips & support software. But that has to get released into the kernel, then a distribution like Ubuntu has to then include that new release into its distribution. That can take a while depending on timing of releases. For those with older distributions but needing the newest kernel or video software there are ppas that have the newest and then easier to reinstall into an older verison.

I did just purchase a new Dell SFF small form factor system. The install of 15.04 was the easiest I have had even with UEFI complications. It just worked.
But I followed the full set of backup procedures we have posted and system suggested. I did a Dell backup, a Windows backup and a full backup with Macrium. But that took 5 DVDs and two flash drives. Dell was 3 DVD, Windows needed an 8GB flash drive, and Macrium the 32GB flash drive(used about 25GB). And with Macrium I created two DVD, one Linux boot and recover and one Windows PE boot & recovery.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

Because of other things & going to store, the backups took 3 days. I then use Windows to shrink the NTFS partition (maybe should have done before Macrium backup?) and rebooted so it could run its chkdsk.
I then used gparted to create the partitions I wanted for Ubuntu.

Ubuntu install to hard drive took about 10 Minutes and in reboot, it just worked. :)

---

### Post by weatherman2 on 2015-06-30
I used Clonezilla on the last Dell Windows 8 system I worked on to do a full backup.  Then to test it, I swapped in a spare laptop hard drive, restored the Clonezilla image to it, and booted it and it worked fine, so I figured I didn't need anything else.  Of course, not everyone has a spare laptop hard drive laying around - but they are handy to have.

---

