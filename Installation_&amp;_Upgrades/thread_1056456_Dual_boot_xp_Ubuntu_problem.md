---
title: "Dual boot xp Ubuntu problem"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by bben46 on 2009-01-31
The Ubuntu 8.10 install CD will not allow installing anywhere except on my existing XP Hard drive. As that drive belongs to my employer, I need to install to a different physical hard drive. Is there a way to do this?

---

### Post by logos34 on 2009-01-31
Choose 'manual' instead of 'guided' partioning option

---

### Post by inobe on 2009-01-31
make sure that your bios setting are correct and the disk you intend to install on is configured correctly..


my suggesting would be to bios boot, this will prevent bootloaders problems !


example: disconnect the windows drive

make sure the raw drive is connected

install ubuntu on the raw drive

if everything boots fine' shut down and connect the windows drive

enter the bios and enable the drive you wish to boot

example image only: to disable a hard drive, selecting none will remove the drive from booting [http://www.dancetech.com/aa_dt_new/articles/pc_build_xp2000_kt333/drives/bios_disk_setup/build_pc_xp2000_bios_primary_slave_details_alter_done.jpg](http://www.dancetech.com/aa_dt_new/articles/pc_build_xp2000_kt333/drives/bios_disk_setup/build_pc_xp2000_bios_primary_slave_details_alter_done.jpg)

just a suggestion :)

---

### Post by bben46 on 2009-01-31
@Inobe
Tried that. I got the Ubuntu installed and working, then hooked up the other drive - It would only boot XP. Tried GAG boot loader, it recognized the ubuntu disk, but would not boot it. Message was Sector Boot not found or invalid.When it booted into XP, it would not recognize the Ubuntu disk.

@Logos.
Tried manual - Got as far as prepare partitions. got message No root file system is defined. And no information on what that means or how to go about defining a root file system.

---

### Post by norcim on 2009-01-31
"No root file system is defined"

one step before you got this message you should have seen a list of all your partitions. At that point you must pick one and set is as the root (" / " -without the quotes)

"then hooked up the other drive - It would only boot XP"
You will need to log into LiveCD and install grub. In short you will...

Use gpart to look at all your drives and their partitions (ex. /dev/sda1)
go to System -> Adminstration -> gparttion  (use the upper right box to choose disks
take note of your xp and your ubuntu partion numbers.
---in grub /dev/sda1  (your first hd and first partion) is (hd0,0)
---        /dev/sdb2   (second hd and second partion is (hd1, 1)... etc

While you are still in gpart, find your ubuntu partition and mount it
-right click and choose mount. A new window should open with the mount location.
Click on the address bar to see the folder location (example /media/some_name)

You will need to install and edit grub menu
Open a terminal:
> sudo apt-get install grub
>sudo gedit /boot/grub/menu.lst    # you will edit this to list a boot menu
                                   # do a search to find out how or read that file

Last: in Terminal: 
> sudo grub
  >find /etc/grub/stage1     #you will get a list of hard drive partitions
   (hd0,0)                   #example (hd0,0) #this is harddrive 1 partition 1
   (hd1,1)
  >setup (hd0,)              #pick the Ubuntu installed partion
  >root (hd0)
  >quit
>

---

### Post by bben46 on 2009-01-31
I didn't see that option anywhere. I'll go back and look again.

Thanks

---

### Post by inobe on 2009-01-31
it's because xp is set to master, if you disable the xp drive' the next drive will boot.


saves both disks' especially the most important business disk !

side note: i have the exact setup: i simply enter the bios and change the windows drive from none to enable, save and exit' windows boots

---

### Post by bben46 on 2009-01-31
Thanks guys, that last one did it, It booted right up after I figured out the grub. I'm going to knock off for the night. I'll probably be back tomorrow when I start trying to get the dual monitor working.

---

### Post by bben46 on 2009-02-01
Thanks for the help, but. Sorry guys, this is just not ready for prime time. The promise was "You don't have to use the command line or know anything about Linux to set it up." Not so! 
1. unable to get it to dual boot XP & Ubuntu on separate drives - I could get one or the other, not both.

2. Unable to get dual monitor to work, conflicting information on this one. 

3. After getting the Ubuntu to boot by - going into a command line and changing grub. When I tried to get my XP back, it cashed. When I tried to use the XP repair option, it was borked by grub trying to start and giving an error.

4. I just spent 6 hours figuring out how to remove the grub and reinstalling XP, and now Ubuntu is gone again. This time for good I'm afraid. I had a lot of hope this would work. I am not a big fan of MS, but it recognizes almost all of my hardware out of the box, runs my dual monitor system with no command line tweaks. 

I didn't even get a chance to try a lot of my hardware, such as scanner, bluetooth headset, cannon camera or fingerprint reader.

I may try again with an older laptop I am trying to set up for my mother to use as a email box. It should work better for that - If it recognizes the hardware.

Thanks again for trying to help.

---

### Post by norcim on 2009-02-01
If you are willing to give it another try let us know. You are not far from a functional Ubuntu dual install. My instructions were probably missing more details...

---

