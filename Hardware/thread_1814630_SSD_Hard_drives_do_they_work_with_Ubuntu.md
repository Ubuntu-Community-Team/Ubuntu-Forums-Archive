---
title: "SSD Hard drives do they work with Ubuntu"
date: 2011-07-29
forum: Hardware
---

### Post by speedball1 on 2011-07-29
I would like to install a SSD in the below build but I have noticed in Newegg reviews that a lot of people are having problems with the operating systems even windows recognizing or remembering the drive . I have not seen any reviews where some one has used them on Ubuntu .

Does any one know if they will work with Ubuntu and can you suggest any brands 

Any help is appreciated 

System Build:
Case HAF 932
Mother Board :EVGA Classified X58
Video Card: EVGA GT-430
CPU: Intel i7-950
Hard Drive: WD 650Gig SATA III
CPU Fan Cooler Master  V8
1. LG Blue Ray DVD Read/Writer/Light Scribe
2. ASUS DVD/CD Read/writer
PWR Supply: Corsair Pro 850

Thanks ken

---

### Post by oldfred on 2011-07-30
Someone had major issues with an SSD that was preconfigured as a RAID device. Do not remember brand nor model.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

---

### Post by movieman on 2011-07-30
I also recommend ensuring that /tmp, /var/tmp and /var/log are mounted as RAM disks (tmpfs). That does mean that you won't have logs after a crash, but you don't want too many random writes occurring to burn through the available write cycles.

---

### Post by joshgura on 2011-07-30
how do you set tmp and stuff as ram disks pray tell?

---

### Post by JRV on 2011-07-30
This is two atricles I found on the [http://forum.eeeuser.com](http://forum.eeeuser.com) website.


Four Tweaks for Using Linux with Solid State Drives

Published in September 4th, 2008
Posted by Tom in tips

SSDs (solid state drives) are great. They’re shock resistant, consume less power, produce less heat, and have very fast seek times. If you have a computer with an SSD, such as an Eee PC, there are some tweaks you can make to increase performance and extend the life of the disk.

   1. The simplest tweak is to mount volumes using the noatime option. 
      By default Linux will write the last accessed time attribute to files. 
      This can reduce the life of your SSD by causing a lot of writes. 
      The noatime mount option turns this off.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Ubuntu uses the relatime option by default. For your SSD partitions (formatted as ext3), 
      replace relatime with noatime in fstab. Reboot for the changes to take effect.

-------------------------------------------------------------------

   2. Using a ramdisk instead of the SSD to store temporary files will speed things up,
      but will cost you a few megabytes of RAM.

         Open your fstab file:
         gksudo gedit /etc/fstab

      Add this line to fstab to mount /tmp (temporary files) as tmpfs (temporary file system):

      tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

      Reboot for the changes to take effect. Running df, you should see a new line with /tmp mounted on tmpfs:

      tmpfs 513472 30320 483152 6% /tmp

--------------------------------------------------------------------------------------------------------

   3. Firefox puts its cache in your home partition. 
      By moving this cache in RAM you can speed up Firefox and reduce disk writes. 
      Complete the previous tweak to mount /tmp in RAM, and you can put the cache there as well.

      Open about:config in Firefox. Right click in an open area and create a new string value 
      called browser.cache.disk.parent_directory. Set the value to /tmp/$USER/firefox-tmp.

-------------------------------------------------------------------------------------

   4. An I/O scheduler decides which applications get to write to the disk when. 
      Because SSDs are so different than a spinning hard drive, not all I/O schedulers work well with SSDs.

      The default I/O scheduler in Linux is cfq, completely fair queuing. cfq is works well on hard disks, 
      but I’ve found it to cause problems on my Eee PC’s SSD. While writing a large file to disk, 
      any other application which tries to write hang until the other write finishes.

      The I/O scheduler can be changed on a per-drive basis without rebooting. 
      Run this command to get the current scheduler for a disk and the alternative options:

         cat /sys/block/sda/queue/scheduler

      You’ll probably have four options, the one in brackets is currently being used by the disk 
      specified in the previous command:

      noop anticipatory deadline [cfq]

      Two of these are better suited to SSD drives: noop and deadline. 
      Using one of these in the same situation, the application will still hang but only 
      for a few seconds instead of until the disk is free again. Not great, but much better than cfq.

      Here’s how to change the I/O scheduler of a disk to deadline:

         echo deadline > /sys/block/sda/queue/scheduler

      (Note: the above command needs to be run as root, but sudo does not work with it on my system. 
       Run sudo -i if you have a problem to get a root prompt.)

      You can replace sda with the disk you want to change, and deadline with any of the available schedulers. 
      This change is temporary and will be reset when you reboot.

      If you’re using the deadline scheduler, there’s another option you can change for the SSD. 
      This command is also temporary and also is a per-disk option:

         echo 1 > /sys/block/sda/queue/iosched/fifo_batch

      You can apply the scheduler you want to all your drives by adding a boot parameter in GRUB. 
      The menu.lst file is regenerated whenever the kernel is updated, which would wipe out your change. 
      Instead of this way, I added commands to rc.local to do the same thing.

         Open rc.local:
         sudo gedit /etc/rc.local

      Put any lines you add before the exit 0. I added six lines for my Eee PC, 
      three to change sda (small SSD), sdb (large SSD), and sdc (SD card) to deadline, 
      and three to get the fifo_batch option on each:

         echo deadline > /sys/block/sda/queue/scheduler
         echo deadline > /sys/block/sdb/queue/scheduler
         echo deadline > /sys/block/sdc/queue/scheduler   
         echo 1 > /sys/block/sda/queue/iosched/fifo_batch
         echo 1 > /sys/block/sdb/queue/iosched/fifo_batch
         echo 1 > /sys/block/sdc/queue/iosched/fifo_batch

      Reboot to run the new rc.local file.

      [update] Commenter dondad has pointed out that it’s possible to add boot parameters 
      to menu.lst that won’t be wiped out by an upgrade. Open menu.lst (Remember to make a 
      backup of this file before you edit it):

         sudo gedit /boot/grub/menu.lst

      The kopt line gives the default parameters to boot Linux with. Mine looks like this:

      # kopt=root=UUID=6722605f-677c-4d22-b9ea-e1fb0c7470ee ro

      Don’t uncomment this line. Just add any extra parameters you would like. 
      To change the I/O scheduler, use the elevator option:

      elevator=deadline

      Append that to the end of the kopt line. Save and close menu.lst. 
      Then you need to run update-grub to apply your change to the whole menu:

         sudo update-grub[end update] 

      Want to know how fast your SSD or other storage device is? 
      Using hdparm you can test the read performance of your disk:
  
         sudo hdparm -t /dev/sda

      The 4 GB SSD on my Eee PC 901 gets about 33 MB/s. 
      My desktop PC’s hard drive gets about 78 MB/s. 
      (What hdparm doesn’t show is that the seek time for an SSD is much, much lower than a hard disk.)


------------------------------------------------------------------

Turn off Journaling in EXT4

First thing's first, we can confirm that our ext4 partition is running a journal with

  sudo dumpe2fs /dev/sdaX | grep has_journal

Disabling journaling is rather easy, the only drag is that to make structural changes to a filesystem, 
the filesystem cannot be mounted with read/write privileges. So, run a live cd and hit

  sudo tune2fs -O ^has_journal /dev/sdaX

And it's done. Now when you boot, the change will be noted and the disk will be checked for errors. 
When the system is finally up we can run this again to confirm that in fact ext4 is running without a journal

  sudo dumpe2fs /dev/sdaX | grep has_journal

should now return nothing.

With this quick fix, no more constant IO peaks. I can now watch youtube videos without constant freezes.

---

