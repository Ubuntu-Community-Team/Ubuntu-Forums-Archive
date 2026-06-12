---
title: "HP ENVY dv6t-7200 Install"
date: 2013-03-03
forum: Hardware
---

### Post by Robbobden on 2013-03-03
Hello Demercel,  I just ordered the same PC for myself.   It's supposed to ship this coming Tuesday, Mar 5th.   I'm also hoping there are no show stoppers with Ubuntu.   I have read that NVIDIA Optimus technology might be just too new for Ubuntu.   I've looked at the Bumblebee Project (here:  [http://bumblebee-project.org/](http://bumblebee-project.org/)) and hope that's the answer for the possible graphics problem.  If you don't mind, I'll piggy back here to report how it goes with my HP Envy when it arrives.

RDL

---

### Post by Robbobden on 2013-03-03
There's a report on this forum already, but I think he had the AMD graphics instead of NVIDIA:

[http://ubuntuforums.org/showthread.php?t=2041457](http://ubuntuforums.org/showthread.php?t=2041457)

RDL

---

### Post by Robbobden on 2013-03-09
My PC arrived from China yesterday.  I spent a couple hours with it, first making a backup DVD set (6 DVDs), then activating Windows 8 and getting MS updates to it.   BTW, this is the HP Envy DV6t-7300 Quad Edition.  I think it's fairly new.  Maybe just marketed this year.   The attached .png shows how it's optioned.   In BIOS, it shows Legacy Support (disabled), and Secure Boot (enabled).   BIOS is InsydeH20 F.22.  It's partitioned thus:  400MB Recovery, 260MB EFI System Partition, 672GB NTFS (C drive), 26GB NTFS Recovery OEM Partition.  That's Disk 0.   There's a Disk 1 of 8GB which I haven't got a clue where it is or what it's used for.  And a CD-ROM 0.   The 32GBSSD doesn't show up anywhere in any screen but it's used as a start-up cache.   There's a BIOS entry where you can disable it.   So, today, I tried running two Ubuntu LiveCD/DVDs.   I have the 12.04.2 64-bit iso (on CD) and 12.10 64-bit iso (on DVD).   They're both supposed to be UEFI compliant or capable.   Neither will run.  Both present a Grub menu where you can select try, install or check disc for defects.   The 12.10 has one additional Grub entry.   It's OEM install for manufacturers.  What's that ?   When I select try Ubuntu on 12.04.2, the error: couldn't read file, you need to load the kernel first appears.   When I select try Ubuntu on 12.10, error: failure reading sector 0x5b500 comes up.   When I enable Legacy Support in BIOS (which automatically disables Secure Boot), both Live CD/DVDs boot up ok.   Wireless on this PC works right away on both.   Zipped around the Internet like you wouldn't think you were using a Live CD/DVD !    Beats Audio seems ok; I briefly watched and listened to a YouTube video.  I haven't checked anything else yet.   If I didn't need a Windows OS for a couple things, I'd wipe the HDD, change the BIOS setting for Legacy Support and load up Ubuntu.   I might try to get Ubuntu on a USB and see how things work that way first.   If anyone knows a way to run an Ubuntu LiveCD without having to tweak the BIOS, I'd appreciate a note here.   Oh, and I'm thinking maybe I could run Ubuntu within VirtualBox on Windows 8.  

RDL

---

### Post by Robbobden on 2013-03-10
Here's some more info:  As I said above, enabling Legacy Support (which automatically disables Secure Boot), allows booting up the 12.04.2 and 12.10 Live CD/DVDs.   But, with BIOS options set this way, Ubuntu 12.04 (non-UEFI) will not boot.   AND, I can't get any tools on CD to boot like Parted Magic or Image for Linux or Boot IT Next Generation.    It won't boot a copy of Windows XP either.    You hear the optical drive spin up, then Windows 8 loads.   That shouldn't happen with Legacy Support enabled/Secure Boot disabled.    I might put a call in to HP tech support but I'll probably waste my time.   I have a 21 day window to RMA this PC.   I'll spend a week or more at this, then think about returning it.

Help !!

RDL

---

### Post by Robbobden on 2013-03-10
Just got off the phone with HP technical support.   When I explained what my problem was, I was informed HP doesn't support use of their product that way.   No tech support, no discussion about the BIOS/UEFI.   This was their 1st tier support at 800 474-6836.  Doesn't surprise me at all.

RDL

---

### Post by Robbobden on 2013-03-11
More info:  Even though Secure Boot is disabled and Legacy Support enabled in BIOS, you can't just pop a bootable CD or DVD in the optical drive and expect it to boot up.   As the machine starts to come up, hit F9.   That gets you startup options.  You can boot from OS boot manager, boot from EFI file or notebook HD or USB or CDROM.  From there I can get Ubuntu 12.04 (non-EFI) to boot up as well as Parted Magic and other tools on CD.   Windows XP DVD also starts up as it should.  Getting somewhere now !  Since I have a 6-DVD backup of Windows 8 now, I think I'll wipe the HD and then try a clean install of Ubuntu 12.04.2.  

RDL

---

### Post by Robbobden on 2013-03-11
Now that I can run Parted Magic, I see what HP did with the 32G SSD I bought for $50.   They created one 8G partition probably for the startup cache and that's why it shows up as Disk 1 in the Windows 8 disk management screen.  The rest, 23G, is unallocated.  It's showing up as /dev/sdb.   BTW here's how the HD is partitioned as seen by Parted Magic:
sda1 ntfs 400MB recovery
sda2 fat32 260MB ESP
sda3 unknown 128MB (msftres ?)
sda4 ntfs 672GB C:
sda5 ntfs 26G recovery
unallocated 4MB 

Also showing in Parted Magic are 3 LVM logical devices:
/dev/dm-0 22G
/dev/dm-1 8G
/dev/dm-2 699G

My Boot It Next Generation shows the whole thing GPT and won't define individual partions as Parted Magic does.

RDL

---

### Post by Robbobden on 2013-03-11
That didn't work.  After I set up the msdos partitions the way I wanted, (for Ubuntu 12.04.2 64-bit), the installation started then I got a pop-up window containing this blivit:  "/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted - possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table ?   Yes or No."   I clicked No, then the install halted and I had to power cycle the PC.  Where were the GPT signatures ?  I deleted all the partitions and created a new partition table.  I googled this and found a link here about bogus corruption warning:  [http://lists.gnu.org/archive/html/bug-parted/2012-03/msg00024.html](http://lists.gnu.org/archive/html/bug-parted/2012-03/msg00024.html)

I'm restoring the Windows 8 OS now.   I'll pick it up again afterwards.

RDL

---

### Post by Robbobden on 2013-03-11
Back up now with Windows 8.  It took 3 hours to restore the factory default from the 6-DVD set !   So, what I did next was to go into Windows 8 disk management and shrink the C: drive down from 688G to 100G.   Then, I set Legacy Support to enable in BIOS.   Popped the Ubuntu 12.04.2 64-bit DVD in the optical drive and re booted.  Entered F9 to get to the boot option menu.  Arrowed down to boot from CDROM.  The DVD booted up Ubuntu (without giving me a Grub menu this time) to the screen where you select Try or Install.   I clicked install and when it asked me how to install, I selected "alongside Windows 8."    I didn't worry about the fact that there were already 4 partitions; figured GPT would manage that.  The installation finished in 30,40 minutes.   Asked me to restart and up came Windows 8.   Disk Management shows the F: drive now with RAW data.   Here's a screenshot taken of the partitions from Parted Magic.  sda 6,7,8 added for Ubuntu, boot,root, and swap.   Now, to be able to actually boot Ubuntu up ??   

I had to leave BIOS set for Legacy Support (also disables Secure Boot automatically).   Power up PC and hit F9 to change boot device order (that's what it says at the bottom of the screen when you press F9).  I get a brief look at the RST screen (that never appeared before - has to do with the 32G cache I think).  Then the "Boot Option Menu" appears.  Arrow down to Notebook Hard Drive and hit enter.  Up comes Grub 1.99-21ubuntu3.9.  With the following entries:

Ubuntu, with Linux 3.5.0-23-generic
Ubuntu, with Linux 3.5.0-23-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 8 (loader) (on /dev/sda4)
Windows Recovery Environment (loader) (on /dev/sda5)

When I arrow down to Windows 8 loader, I get the Windows Boot Manager black screen w/white text telling me Windows boot failed to start.  And also "the boot config data for your PC is missing or contains errors."  Had to restart from there to get back to Grub.

But, when I select the top entry for Ubuntu, Ubuntu boots up in about 20 seconds to the lightdm greeting screen !!   

I've been trying to get to this point for 3 or 4 days.   Now, I can evaluate Ubuntu on this PC for issues like how wireless reacts after suspend, if the audio works ok, and how the discrete grahpics card performs.   More to follow.

RDL

---

### Post by Robbobden on 2013-03-27
So, after wiping the HDD, I booted up Ubuntu 12.04.2 LTS and installed it again.   I had the installer set up the partitions, GPT, exactly as in thread #14 above.   Other than disabling RST in BIOS, making sure the 32G SSD wasn't in Raid 0 config (did this by creating a new standard partition table on it (/dev/sdb) using Parted Magic),  nothing else was done.   Note:  On this PC, if you don't add the /boot efi partition, you will definitely get this when you restart:  "No Bootable Device".   How to add this partition ?  Just add a 50MB partition with file type boot efi, not ext2, ext4 or swap.  Easy.  I added it last so it may not matter where on the HDD that partition goes. 

It's important to note that when I installed this version of Ubuntu to the HP Envy dv6t-7300, the wireless button was inoperative after the installation.   That PC seems to need a separate wireless button driver (and you can download that driver from the HP web site - for Windows 8) whereas this Pavilion may not.   You don't see a wireless button driver for this Pavilion when you look on the HP site.   Other than the discrete NVIDIA 650M GPU which I haven't tested yet, there are no problems that I can see.   Audio, wireless, touchpad, backlit keyboard, suspend all work well.

On to VirtualBox now .....

RDL

---

### Post by Robbobden on 2013-03-27
I followed these instructions when I installed VirtualBox on my 32-bit Desktop PC:

1. Download the Linux file from VirtualBox website.   The file depends on your Linux distro and whether you have 32 or 64-bit CPU
2. Navigate to where you downloaded the file and:   sudo dpkg -i [file name]
3. sudo apt-get update
4. sudo apt-get install libsdl-net1.2-dev
   [For the GUI.  Now the Oracle VM Virtual Box appears in system
   tools]
5. sudo apt-get install dkms
   [Dynamic kernel module support. With dkms installed, the
   VirtualBox should always work automatically, and automatically
   rebuild when the host kernel gets an update]

But for Ubuntu 12.04.2 in this 64-bit Pavilion, I just followed steps 1-3.  The libsdl-net1.2-dev and dkms must be part of the 12.04.2 installation.

I set up Win7 in VirtualBox.  This YouTube video seems pretty ok to follow.   [http://www.youtube.com/watch?v=ZaHbmbrqjvQ](http://www.youtube.com/watch?v=ZaHbmbrqjvQ)    I inserted my Windows 7 OEM DVD and 30 minutes later it was installed !   There was one snag however.  I got this blivit message right off:

"VT-x/AMD-V hardwre acceleration has been enabled, but is not operational.  Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.  Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer."

I thought I remembered seeing something like this in BIOS.  Sure enough, there's a menu entry entitled 'Virtualization Technology, disable or enable'.  It was disabled.  The item specific help text said this:  "Hardware VT enables a processor feature for running multiple simultaneous Virtual Machines allowing secialized software applications to run in full isolation of each other.  HP recommends that this feature remain disabled unless specialized applications are being used."  I enabled Virtualization Technology.   Problem solved.   

After using Ubuntu and Windows in dual-boot for a long time, this seems more elegant to me.   Not having to restart to get from one to the other is certainly convenient.   We'll see how it goes though.  When I finish getting everything set up the way I normally do, I'll post some screen shots for anyone who's interested.   I use Cairo-Dock instead of Unity and a pretty ok Conky.  Note:  No Win7 specific drivers needed either.  Cool !!

RDL

---

### Post by Robbobden on 2013-03-27
Couple attachments here - two screenshots of the new Pavilion dv6t-7000.  The first is the Ubuntu desktop.   The quad core i7-3610 has a temp sensor in each core.  I got the temps to display in Conky using lm-sensors.   The temps stay just under 120F normally with little or no activity.   I watched the entire Red Box video, "Company of Heros" earlier tonight on Ubuntu.   Maybe a 5-6 degree increase during the whole film.   According to the readout, temps aren't high until 188F, and critical at 221F.   Man, that is hot.  BGA failure time if you get that hot.  The 2nd shows Win7 open to the login screen.   After guest additions installed, the resolution improved a lot.   It'll fill the entire screen if you want.   I like it the way it shows so I can mouse access Ubuntu if I need to.  Also after guest additions are installed, you can set up a shared folder between Ubuntu and Win7.  Worked well the first time.   But after shutdown and start up, the network drive didn't reconnect and up popped a window telling you all about it.   Googled this and it's a bug it seems.   You have to re-map the drive to get the folders to share.  Couple minutes to do that.   Bummer !   

I need to get Google Earth loaded up.   For some reason it's not installing.   After that, I'll make an image of everything using Image for Linux.   If I'm allowed, I'll keep posting here regarding the discrete GPU.   It's not a high priority now, though.   I don't know what demercel, (the OP here),  thinks about his dv6t-7200 with Windows 8.  Or if he's even gone back to check replys to his post.   But, I appreciate the moderators letting me use this as a kind of personal blog !! 

RDL

---

### Post by oldfred on 2013-03-27
@robbobden
If you want I can move all your posts and reponses to your own thread and add one post for demercel to find it. Since topic was originally same PC I left it, but you now have hijacked thread, so it might be better to be your own.

Moved from this original thread.
[http://ubuntuforums.org/showthread.php?t=2120660](http://ubuntuforums.org/showthread.php?t=2120660)

---

### Post by Robbobden on 2013-03-28
Fine with me ....

RDL

---

### Post by Robbobden on 2013-03-28
To continue (on my own post - Thanks ! OldFred)....

Ubuntu 12.04.2 LTS works great on this PC, but I'm getting no 3D with Unity. (At the greeter screen, I can select Cairo Dock or Unity).  And I've noticed in Cairo Dock the only option in configuration/behaviour is on click: Animation.   With my 5-year old desktop PC,  I see on mouse hover, on click, and on appearance/disappearance.  Each of those categories gives me animation and effects.   I don't think the onboard GPU on this dv6t-7000 is set up for accelerated graphics.  The graphics for this PC should be cutting edge, but all I can get is 2D.   Why ?  Any one have any experience with this ?

BTW, I just got back from here:   [http://eternalvoid.net/tutorials/linux-optimus-gt650m/](http://eternalvoid.net/tutorials/linux-optimus-gt650m/)    where I tried the Bumblebee workaround for the discrete GPU on this PC, the NVIDIA 650M.   I followed the step-by-step but the test at the end,  'optirun glxspheres',   failed.

---

### Post by avataraang on 2013-04-26
Hey Rob,
  Thanks for sharing your experience out here. Now you were trying to dual boot. I wanted to know from your experience if a clean install will be more smooth sailing. I noticed that you contemplated doing this towards the end. I have this setup on my current laptop. Ubuntu precise with windows 7 vbox and all is good. I want to upgrade my laptop to this envy quad core to the same setup I have now with possibly have all SSD hard drives.

So I would 
1) switch legacy support in bios. 
2) Blow off windohs completely 
3) install ubuntu on the entire drive.
4) copy over my win 7 vm from backup.

I wanted to confirm that most of the problems you were running into is because of trying to dual boot. I am almost close to ditching the envy as an option to show my vote against HP aligning with m$ with this UEFI crap.

---

