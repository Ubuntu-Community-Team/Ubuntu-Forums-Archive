---
title: "installing on external HDD. help pls!!!"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by youngunix on 2009-05-14
Hi, 
 
i've always wanted to use unix/linux but i didnt have the means. now that i do have a gateway running on Vista home-premium with 3GB RAM & 250GB HD, i want to leave my internal HD alone, so i bought a 750GB external HDD, i partitioned it in 3. 
(F:)=415gb for storage. (G:)=189gb<<i want to install OpenSuse 11.1 on this one, and (H:)=98gb<<on this one i'd like to install Ubuntu 9.04. i trired already but i failed. 
i'd like your help...i already have the bootable cds of ubuntu and opensuse....
 
thxxxxx

---

### Post by logos34 on 2009-05-14
what do you mean, 'failed'?  Details...

Boot the live cd and run this in terminal (and post output):

sudo fdisk -l

You might follow [this guide]("http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/") to instaling ubuntu on external usb (it says it's for flash drives, but the principle is the same for drives in usb enclosures).

---

### Post by youngunix on 2009-05-14
i mean when i use "boot menu" to chose where to boot from, there's the external USB drive listed on the list, but not the partitions on it...i formatted the (H) drive where i had ubuntu 8.10 on it. now i have ubuntu 9.04 that i want to install on drive (H).....so how do i set the "boot menu" to display the partitions? or the installation includes that option?????

---

### Post by logos34 on 2009-05-14
Not sure if you're referring to Bios boot priority or what.

Just follow the guide I gave you, it will get the grub bootloader correct, and you only need choose the boot device at starup...As to installing to the right target partition, look at [this]("http://www.psychocats.net/ubuntu/installing")...Select option "Specify partitions manually (advanced)'>point it to 98 gb partiiton

---

### Post by youngunix on 2009-05-14
something weird just happened, i booted the pc from the cd to install it, it was Xubuntu which is not wat i want..and it opened the OS with the options and everything that looks like the pic(attch) i can use it even it didnt install it..does that have to do with the ubuntu i tried to run b4, cuz now there's "windows vista" and "ubuntu" under it on the boot window(u know which one..)

---

### Post by youngunix on 2009-05-15
btw i tried the steps on the guide u posted, and i get an error "H is not a removable flash drive".....

---

### Post by -kg- on 2009-05-15
In all actuality, you got ahead of yourself when you created those partitions.  It is much easier to do this with the partition editor in the installer itself.

For instance, you say you created three partitions; two for your installations and one for storage.  Did you create a swap partition?  That is fairly well required, and the partitioner will not let you forget it during installation.  The swap partition should be approximately 1 1/2 X the amount of RAM you have installed.

It would probably be easiest on you to delete the two partitions you created for your installations (leave the one for storage) and create your partitions at install time.  I don't know whether OpenSUSE supports ext4 (or whether you want to use it with Jaunty), but if it doesn't (and you want to use it with Jaunty) I would install SUSE first.

I am unfamiliar with SUSE or how it's installer handles things, but if there is a manual partitioning selection, select it, then once the screen comes up select the free space on your external 750 GB drive.  Make your swap partition first, making it the size I indicated above and format it as swap.  Common convention is to put it at the very end of the drive.

Then make the ext3 (or ext4, if it supports it and you want to use it) partition, making it the size you wish it to be and mount it as root ("/").  If you want a separate /home partition, you will want to make your root around 15 or 20 GB, and create another partition to take up the remainder of the total space you desire.  Format this as ext3 (or ext4) and mark it as "/home".

Once you have finished the SUSE installation and confirmed that it is properly installed and working, repeat this process for Jaunty and install it.  You shouldn't need to create another swap partition; they should be able to share the same swap space.  When you install Jaunty, it will install it's own version of GRUB in the MBR, and it should autodetect all the bootable partitions in your system.

Now, the only reason I told you to install SUSE first is because of the file system formatting that I have mentioned.  If SUSE doesn't yet support ext4 and you wish to use it with Jaunty, I'm not entirely sure that SUSE's GRUB installer would recognize the ext4 filesystem and might not include it in the GRUB menu.

Jaunty's will, and will recognize SUSE's ext3 as well.  If you just want to go with the default and use ext3, it doesn't matter which order you install them...it will work either way.  I do know, though, that Jaunty *will use* an existing swap partition without having to do anything special.

I just visited the SUSE website and found that SUSE doesn't yet support ext4, so if you want to experiment with ext4 with Jaunty, you will definitely need to install it last so that Jaunty's GRUB is installed at the last.

For more comprehensive information on partitioning operations, see [How To Partition]("https://help.ubuntu.com/community/HowtoPartition") in the Community Wiki.

---

### Post by youngunix on 2009-05-15
thxx in advance "-kg-"!!! u r right i think i went way ahead of myself by partitioning the HDD. i'm gonna take easy this time, i will put back the HDD the way i got it & fix the MBR. "swap partition" is kind of a new "option" for me, do u mind explaining how do i make a "swap partition"? and what's the difference between it and regular partitions i made???

note*: the 750GB HD is now the way i got before.

---

### Post by logos34 on 2009-05-15
> **youngunix said:**
> do u mind explaining how do i make a "swap partition"? and what's the difference between it and regular partitions i made???

Use the installer partitioner or Gparted back on the desktop to create a primary partition, type 'linux-swap', mountpoint '/swap'. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by youngunix on 2009-05-16
okkk, it took 25hrs to f***ing formatt the whole 750gb HD, now i partitioned it(without formatting) and i booted from the installation CD and when i got to the window where it asks to chose which partition you want to use, there's ONLY my internal HD, GRRRRRRRRRRR!!!!damnnnnnnnnnnnnn
i dont usually do this but i'm gonna give up on installing it on the external HD since it's impossible i guess...thx for your time guys.

---

### Post by -kg- on 2009-05-17
Don't give up quite yet.

It's late now (for me), but I'm going to put a Live CD in my laptop with my external hard drive hooked up and see what's going on.  I could *swear* that I had the option of installing to it, but I could be wrong.

Did you see anything at the top (right, I think) that indicated that you were looking at sda?  I *think* that if you click on that, you will be able to select the physical hard drive that you want to install on.  Check that out before you absolutely give up on it.

---

### Post by -kg- on 2009-05-17
OK, I slipped one of my Jaunty install disks into my laptop and brought it to the Manual Partion Selection screen.  In my laptop, I have two internal hard drives and my 1 TB external hard drive plugged in to the USB port.

All of the hard drives were displayed on the Manual Partitioning screen; sda, which is the Master hard drive...sdb, which is the internal Slave drive...and sdc, which is the external drive.  These are displayed in lines below the graphical representation at the top of the screen.

Under the lines that represent the hard drives themselves are sub-lines that represent the partitions and the free space on each of these drives.  You can cause these sub-lines to disappear by clicking on the arrows beside the main hard drive lines.

When you highlight one of the hard drive lines, the graphical representation will change to the hard drive you have selected.  Unlike using straight GPartEd, you cannot select the part of the hard drive you want to perform operations on by clicking on it in the graphics; you must click on the appropriate line below it.

Now, I see that I told you to install SUSE first.  Is that what you did?  If that's the case, I can't really say that it wasn't the fault of the SUSE Installer that it didn't see your external drive.  I have zero experience with that distro.

You might want to try installing Jaunty first just so you can get a Linux installation on your computer and get it going.  SUSE *can* be installed later.  SUSE doesn't recognize ext4 partitions, so if you can do without it, you might want to take the default file system type of ext3 for the Jaunty installation.  That way, when you install SUSE (or whatever distro) it's GRUB installer will recognize the Jaunty installation and include it in the GRUB menu.

If you just *want* to use ext4 (and I wouldn't blame you; I'm using it), all is not lost.  When you make your other installation (and assuming it doesn't recognize the ext4 format), just use the Jaunty Live CD to reinstall Jaunty's GRUB in the MBR.  There are a number of posts on this forum that will tell you how to do so, and re-installation of Jaunty's GRUB will ensure that all of the installed OSes are recognized.

---

### Post by youngunix on 2009-05-18
ok! i actually didn't give up :-P. i ran live cd on a Dell pc that's running XP pro. SP3, and tried to install it on my external HD, "IT ACTUALLY WORKED.." i managed to make a swap, root, and /home (ext3) and it installed on my ext. HD. BUT that Dell now can't boot XP, at the boot it says Grub error 21, i noticed it's a comon problem. so now i am making an XP bootable cd to fix that pc(**** if not i'll get my *** kicked, it's not mine..) so help me out here guys. if i boot from that CD and run recovery, type in "1" for "C" the partition i need to fix, <<what's the admin pass? is it the user's pass or i just click "enter" without entering anything??>> then type "fixboot" then "Y", then "fixmbr" then "Y" then "exit". will this process fix the Grub problem and uninstall it, and XP won't loose any data, right???? :-)
 
Also, how can i NOW run ubuntu from my external HD on MY VISTA PC THAT I COULDN'T USE TO INSTALL UBUNTU ON THE EXTERNAL HD WITHOUT MESSING MY VISTA BOOTLOADER OR NETHING AS SUCH...???

---

### Post by ruehara on 2009-05-18
Depending on what you want to do with the Ubuntu distro, you may like to have a look at Sun's Virtualbox. They distribute it free for home use and it allows you to set up fully functioning virtual machines under your host OS. These can reside quite happily on your external HDD.

In my case, my brand new Dell XPS came with Vista on it. It was such a dog that I set up Ubuntu in a VM and eventually decided to totally clean out the PC, install Ubuntu as the host OS and also as a guest OS. From this I simply migrated all the stuff I had accumulated (emails etc) into the host OS and now I am running XP under Ubuntu just for the couple of apps I use which aren't available in Linux yet.

---

### Post by youngunix on 2009-05-18
i simply want to use Ubuntu form my external HD and my PC as a host for it, and when i remove the external HD, i want it to seem like nothing happened, and booting vista without issues..

---

### Post by logos34 on 2009-05-18
> **youngunix said:**
> if i boot from that CD and run recovery, type in "1" for "C" the partition i need to fix, <<what's the admin pass? is it the user's pass or i just click "enter" without entering anything??>> then type "fixboot" then "Y", then "fixmbr" then "Y" then "exit". will this process fix the Grub problem and uninstall it, and XP won't loose any data, right???? :-)

yes, exactly
 
> Also, how can i NOW run ubuntu from my external HD on MY VISTA PC THAT I COULDN'T USE TO INSTALL UBUNTU ON THE EXTERNAL HD WITHOUT MESSING MY VISTA BOOTLOADER OR NETHING AS SUCH...???

Restore grub bootloader to the MBR of the external hard disk (see link below). For 'setup' step use the same '(hdx,y)' as output by the 'find' command.  Then boot the external by selecting it as the boot device in the BIOS.


> **youngunix said:**
> i simply want to use Ubuntu form my external HD and my PC as a host for it, and when i remove the external HD, i want it to seem like nothing happened, and booting vista without issues..

if you do it like above, the two bootloaders will be separate, each on a separate drive.

---

### Post by ruehara on 2009-05-19
> **youngunix said:**
> i simply want to use Ubuntu form my external HD and my PC as a host for it, and when i remove the external HD, i want it to seem like nothing happened, and booting vista without issues..


I'd strongly suggest you take a look at Sun's Virtualbox. You would load the app itself on your main HDD and the Virtual Machine(s) on your external. Vista would not be affected in the slightest and you would only launch Virtualbox when you have the external drive attached. This also gives you the option to try out as many OSs as you wish at any time.

---

### Post by youngunix on 2009-05-19
i tired to install Virtualbox but it wants to to reset my network connection...why is that????
 
Nevermind, i chose the option to install it when needed.
ok, now, do you mind telling me in a simplest way possible how to set up the virtualbox so i can use the ubuntu on the external HD???

---

### Post by ruehara on 2009-05-19
> **youngunix said:**
> 
ok, now, do you mind telling me in a simplest way possible how to set up the virtualbox so i can use the ubuntu on the external HD???

If your external HDD is eSata, you can install virtualbox on that. All your VMs will also be installed on it too.

The way I do it (I switched from MS Windows to Linux after my new computer from Dell came preinstalled with Vista and no options) is to

[INDENT]
[LIST=1]
[*]I installed VirtualBox on my internal HDD under Ubuntu
[*]Created an XP VM with minimum disc space
[*]My external HDD is designated as a shared drive which just happens to contain nothing but my Windows apps and data
[*]In the VM configuration I specify the root folder (i.e. top level) of the external drive as a shared folder
[*]When I run the XP VM, all my apps, downloads,data etc. are stored in the shared folder (and subfolders).
[/LIST]
[/INDENT]I usually work from home and on the rare occasions when I go into the office, my PC there is set up in a similar fashion except that it has an XP O/S. I simply connect my external HDD, fire up Virtualbox and voila! everything is just where I need it.

---

