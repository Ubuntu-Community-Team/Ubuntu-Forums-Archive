---
title: "can a primary partition be changed to logical"
date: 2008-08-11
forum: General Help
---

### Post by johnlvs2run on 2008-08-11
Ubuntu is on a primary partition, and swap on the 2nd one.  
I'd like to move Ubuntu to a logical partition.

Also, I'd like to move thunderbird email to /home.

Are these possible, or do I need to wipe the disk and start over.

---

### Post by LowSky on 2008-08-11
any reason for the change? I am assuming the Ubuntu is on a Extended logical partition right? Why not just keep things the way they are? Do you need more space?

you can move the data but you will need to change all the reference point for the boot record.

I don't know what you mean by moving T-bird to your /home folder? Your user Data is already there under /.mozilla or /.thunderbird

---

### Post by logos34 on 2008-08-11
post the output of:

sudo fdisk -l

df -h

Like LowSky said, what is your goal?

---

### Post by johnlvs2run on 2008-08-11
> **LowSky said:**
> any reason for the change? I am assuming the Ubuntu is on a Extended logical partition right? Why not just keep things the way they are? Do you need more space?

No, Ubuntu is on a primary partition.  
I'd like to move it to an extended partition, in order to be able to add more distributions, and primary boot and home partitions.

> you can move the data but you will need to change all the reference point for the boot record.
Thanks.  Anywhere you can direct me to find out how to do this?

> I don't know what you mean by moving T-bird to your /home folder? Your user Data is already there under /.mozilla or /.thunderbird
I mean to a primary home, so all the distributions can use it, like this.

1-  boot 150mg
2-  swap 1gb
3-  extended 60gb
.. 5- ubuntu
.. 6- mint
.. 7- arch
.. 8- debian
.. 9- other
4-  /home 20gb

---

### Post by johnlvs2run on 2008-08-11
> **logos34 said:**
> post the output of:

sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd59ad59a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686   83  Linux
/dev/sda2            5100        5233     1076355   82  Linux swap / Solaris

> df -hFilesystem            Size  Used Avail Use% Mounted on
/dev/sda1              39G  4.5G   33G  12% /
varrun                887M  100K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
procbususb            887M   40K  887M   1% /proc/bus/usb
udev                  887M   40K  887M   1% /dev
devshm                887M   12K  887M   1% /dev/shm
lrm                   887M   39M  848M   5% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       39G  4.5G   33G  12% /home/john/.gvfs

---

### Post by LowSky on 2008-08-11
Why do you need a boot partition? SWAP can take up space on a extended partition as well. I assume you listed Mint and Debian for reference, as there is no point to really want to use them(both are very simular and all are based on Debain).

as for T-bird you will really need to install on every OS, but the user file can be saved and used for each distro.

Using one Home partition per distro will get very messy. I would be careful.

---

### Post by logos34 on 2008-08-11
Lowsky is right about sharing /home.  Don't do it.  But it's still a good idea to move to a separate /home for ubuntu.

If you want to switch to a separate /home(see link on how to do that in my signature), you won't be needing all that room on /, so shrink it down to maybe ~8 GB.  Use Gparted on the ubuntu live cd--can't be mounted during resize.  Then create an extended partition out of the remaining disk space, make an ext3 and linux-swap (same size as originals) inside.  You can subdivide the rest up to your heart's content for other distros.  Copy / and /swap to new logical partition, again using Gparted [copying/moving]("http://gparted.sourceforge.net/larry/move/move.htm") function.  

Reinstall grub to the mbr, pointing to new / (see link my sig).  The 'find' command will return two 'root' locations--you obviously do not want to use '(hd0,0)', the old one.  You're using UUIDs, which do not change when cloning a partition, so you shouldn't need to edit /boot/grub/menu.lst or /etc/fstab.

---

### Post by estyles on 2008-08-11
This is my opinion, so take it as you will:

If you're going to be booting multiple Linux distro's, you absolutely do want a separate /boot partition - that way your grub stage 1 will be the same for all distros - you don't want a distro to modify its own grub file, and they you can't find it because your MBR is pointing at a different menu.lst.  You don't want a separate /home partition because it won't be of much use to you, but you *do* want a Data partition.  Create a partition as big as possible (leaving about 10GB per linux distro - less if you know what you're doing and think you're okay with less) and label it as Data.  I think the command for labeling a volume is e2label.  Labelling the volume is optional, but makes things easier.

Edit your fstab to mount the Data partition at /home/username/Data (also add the /boot partition, and run sudo mount -a to mount them) and move all of your non-hidden folders from your home directory to the Data directory.  You might want to move some hidden folders like ~/.wine and ~/.VirtualBox - stuff that takes up a lot of space and/or might be useful in other distros.  Then make links to those directories and copy them to your home directory (make sure to change the names to be identical to the original names, particularly for any hidden files - wine will look for its settings in ~/.wine, not ~/Link\ to\ .wine).  

Now you have a separate Data partition that is available to all of your distros.  In every other distro you will need to edit your fstab and copy over the symbolic links to the Data drive.  I've found this to be the best way to multi-boot, IMHO.

If anyone wants more detailed instructions on how to do this, post here and I'll be happy to expand on that.

---

### Post by johnlvs2run on 2008-08-11
> **LowSky said:**
> as for T-bird you will really need to install on every OS, but the user file can be saved and used for each distro.
Could you explain what you mean by this.

> Reinstall grub to the mbr, pointing to new / (see link my sig).  The 'find' command will return two 'root' locations--you obviously do not want to use '(hd0,0)', the old one.  You're using UUIDs, which do not change when cloning a partition, so you shouldn't need to edit /boot/grub/menu.lst or /etc/fstab.
I will use this for reference.  Thanks.

---

### Post by johnlvs2run on 2008-08-11
> **estyles said:**
> You don't want a separate /home partition because it won't be of much use to you, but you *do* want a Data partition.

If anyone wants more detailed instructions on how to do this, post here and I'll be happy to expand on that.

Estyles, thank you, that is very helpful.

I'd definitely be appreciative of more expansion of that.

Back to my original question, do I have to delete ubuntu and start over, to get it from the primary to a logical partition?

---

### Post by estyles on 2008-08-11
Well, for one thing, lots of people have their own ideas of what works for them.  Also, you'll get people giving you advice who have a different situation than you, so the advice may be valid for them but not for what you're trying to do.  Others just give bad advice... ;)

Having done the multi-boot thing, I can tell you that a separate /boot partition is a very good idea.  It doesn't have to be a primary partition - it can be a logical partition, but it should be separate and mounted at /boot in each distro.

A /home partition is not particularly useful, because sharing your settings across multiple distros doesn't work that well.  Sharing your *data* across multiple distros is a very good idea.  That's why I suggest creating a Data partition and mounting it at /home/username/Data, and creating symbolic links to the folders contained therein.  For what you are trying to do, I can almost guarantee that it will save you a lot of headaches over what you're doing.

I've tried it several different ways myself - with a separate /home partition, with separate partitions for each different type of data, etc...  A data partition, IMHO, works by far the best, it just requires a little bit of setup.  And yeah, I've repartitioned my drive many, many times trying to get that perfect setup.  Which wasn't really necessary, but having it less than perfect just bugged me...  :)

---

### Post by logos34 on 2008-08-11
> **estyles said:**
> If you're going to be booting multiple Linux distro's, you absolutely do want a separate /boot partition - that way your grub stage 1 will be the same for all distros - you don't want a distro to modify its own grub file, and they you can't find it because your MBR is pointing at a different menu.lst. 

Not to be argumentative here, but I respectfully disagree.

What I think johnlvs2riun should consider instead of a separate /boot is a [**dedicated grub partition**]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), using [configfile or chainloader entries]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems") for the other OS's--that way kernel updates and/or changes to each distros menu.lst will not confuse things.  Set it and forget it.  Also, it takes up a lot less room because it's not holding all the kernels, just the master (ubuntu) menu.lst.

Data or separate /home partition, either way, but an ubuntu /home (just that--not one for each of the additional OSs!) has other advantages, and besides, you could always put symlinks (ln -s) in the other OS home directories, pointing to ubuntu /home, where you could dump all your saved stuff and downloads, etc.

So my 2 cents is make a dedicated grub, ubuntu /home, shrink and copy /, and have fun.

---

### Post by estyles on 2008-08-11
True, a dedicated grub partition lets you set and forget instead of manually editing your menu.lst each time you upgrade a kernel.  It does have that advantage.  I don't really like it because it puts an extra layer of grub menus on boot up, and I prefer to manually edit my menu.lst to keep it cleaned up.  Either way I think you'd be fine.  What you really don't want is grub set up in your MBR pointing at one distro's menu.lst file, because that just confuses things.  Personally, I like mounting the Boot partition to /boot in all distros.

I'm not sure what other advantages an Ubuntu /home partition has, and why those advantages don't apply to other partitions.  I just really wouldn't want to make a separate /home partition for *every* distro, and sharing the same /home directory isn't really an option.  So if a separate Ubuntu /home is the way you want to go, then yes, you definitely should make symbolic links to the directories inside that home directory.  I like my way better, but whatever floats your boat.

---

### Post by mc4man on 2008-08-11
After keeping to some general 'good partitiong' strategy's  what you do is dependent of personal preferences and what best suits your setup and tasks you perform. For example I tri-boot xp and 2 linux on dual hdds. Because i do alot of video, graphics work I need to create ways for each Os to work cross-drive , and have an easy way to create, delete, rename logical drives as needed. So what's good for me may be of no great use to you.

As far as the orig. question, yes you'd need to redo ubuntu to install to a logical vs. the primary it's in now. (maybe there's a way to change and move a primary to a logical and into an extended, I wouldn't bother if such method exists

---

### Post by johnlvs2run on 2008-08-11
> **estyles said:**
> Now you have a separate Data partition that is available to all of your distros.  In every other distro you will need to edit your fstab and copy over the symbolic links to the Data drive.  I've found this to be the best way to multi-boot, IMHO.

Estyles, that's how I'd like to do the partitioning.

Could you give an example of how this would apply to thunderbird email, i.e. how would I move the TB files to the data partition.

Then I could reinstall ubuntu and tb in their own logical partition.

---

### Post by estyles on 2008-08-11
> **johnlvs2run said:**
> Could you give an example of how this would apply to thunderbird email, i.e. how would I move the TB files to the data partition.

Well, I haven't done this for thunderbird, or even for evolution.  I would think that you could copy over your .mozilla folder and make a symbolic link to .mozilla in your /home directory, although I know that firefox uses a different pseudo-random string for each user profile, so that might not work right.  I would do a search for porting over thunderbird information and see if anyone else has a good solution for using email across multiple OSes.  When I get home maybe I'll do some playing around to see if I can get it to work with evolution (since I don't use thunderbird), and will post my results.

---

### Post by estyles on 2008-08-11
Well, it looks like thunderbird stores its profiles in ~/.mozilla-thunderbird (I still have the settings folder because Mint has thunderbird installed by default, but I hate it so I uninstalled and use evolution instead).  It looks like it should work to just copy that folder to your Data folder and create a symbolic link with the same name in your home folder.  Worst comes to worst, you might have to edit the "profiles.ini" file in that directory and make sure it points to the right profile - I wouldn't try that unless you open your thunderbird and your messages aren't there.  In any case, I can't guarantee it will work, but it seems worth a try.

---

### Post by johnlvs2run on 2008-08-11
> **estyles said:**
> It looks like it should work to just copy that folder to your Data folder and create a symbolic link with the same name in your home folder.

Thanks.  I'll give it a go and post back.

---

### Post by johnlvs2run on 2008-08-13
I've been reading the grub guides and, from the point of view of someone trying to learn how to make a grub partition rather than someone who knows every little detail about grub, they are totally confusing.  After spending a couple of weeks reading them, I'm no closer to being able to make a grub partition.  It would be helpful to see step#1 do this, step#2 do this, step#3 do this etc etc.

What I'd like to do is roughly as follows.
1) make a data partition;
2) move thunderbird and pidgin files to data partition;
3) make a grub partition;
4) delete ubuntu from primary partition;
5) install ubuntu, mint, etc to logical partitions;
6) adjust grub to boot any of the distros that I choose.

1) is a data partition just an empty ext3 partition?
2) don't know - need steps
3) don't know - need steps
4) fine
5) fine
6) don't know - need steps

Suggestions appreciated.  Thanks.

---

### Post by oldos2er on 2008-08-13
Is there some particular reason you don't want grub in the MBR?

---

### Post by estyles on 2008-08-13
@oldos2er - he wants grub installed to the MBR, and have it bring up a menu which lets him boot either to Windows, or to any Linux distro.  When booting to the Linux distro, he wants (I believe) for it to bring up the Grub menu for that particular distro.  This lets each distro manage its own menu.lst, so he doesn't have to manually edit his menu.lst - it's basically fire and forget (though you probably will have to edit the menu.lst on the main grub partition, but it shouldn't be too difficult).

I don't have any experience with creating a separate grub partition, so I will remain silent on that until and unless I give it a try and see how it goes.  For the data partition, just make an empty ext3 partition as big as possible.  If you're doing this from scratch, it should be best to put it in the extended partition (mine is in a primary partition due to random chance).  Copy any of your data that you want to be available to all distros to the data partition.  For stuff like thunderbird, you want to copy the ~/.mozilla-thunderbird/ directory.  For many other programs, you'll want to look for their settings directories, which start with a '.'.  Don't go crazy copying settings directories, because a lot of things will have different settings based on your distro.  If you find something that you want to copy settings over after you install a new distro and it isn't already on the Data partition, you can always mount your other /home directory and copy the folder over to your new /home directory.  You will probably need to do ```
mkdir UbuntuDrive
sudo mount /dev/sdaWHATEVER ~/UbuntuDrive
sudo cp -r UbuntuDrive/.WHATEVERYOUWANTTOCOPY ~/.
sudo chown -R USERNAME:USERNAME ~/.WHATEVERYOUWANTTOCOPY
chmod u+rw ~/.WHATEVERYOUWANTTOCOPY

```
To make it so that you own that directory and have read/write privleges to it.  I think that code is correct - someone please correct me if I put something wrong in there.  (replace all of the CAPS stuff with the proper names)

Anyway, for stuff that is on the Data partition, once you setup a new distro, you want to edit your fstab to have the following line:```
#shared data partition
/dev/sdaWHATEVER	/home/USERNAME/Data	auto	defaults	0	0
```

You want to make symbolic links to everything in your Data directory in your home directory.  The easiest way I know to do this is mount your Data directory (if you don't want to restart, after modding your fstab, type "sudo mount -a"), then browse to it.  Press Ctrl-H to see hidden files, select all and right-click, choose "Make Link".  This will be slightly different in different distros.  Then select those links, Ctrl-X to cut them, then browse to your home directory and Ctrl-V to paste them.  You'll need to rename them to remove the "Link to" in the name - if the directory already exists, you must delete the original directory first.  I know there is a way to do cp -l to make symbolic links, but when I try to do it, it says it can't do it for directories, so I always do it the GUI way.  If you find that you don't have read/write access to the files (for some reason, I always don't, even though my fstab defaults are set to rw and user...), you'll have to chmod the files.  I tend to chmod them for "all" access, since I intend my Data to be available to anyone who uses my computer.  You may have to modify this.
```
sudo chmod -R a+rw ~/Data
```

Okay, I *think* that should do it for mounting a data partition.  It is a little complicated, but it works for me.  Someone please let me know if I missed a step or put bad code in there somewhere, or if there's an easier way...

---

### Post by johnlvs2run on 2008-08-13
> **oldos2er said:**
> Is there some particular reason you don't want grub in the MBR?

No reason at all, thought that's what I was trying to do.  
People post a lot about having a 150 mg primary partition for grub.
I was trying to set this up, but whatever is the easiest and works well is fine with me.  

Thanks again, Estyles.  
I'll take some time to work through that and post back.

---

### Post by oldos2er on 2008-08-14
> **johnlvs2run said:**
> No reason at all, thought that's what I was trying to do.  
People post a lot about having a 150 mg primary partition for grub.
I was trying to set this up, but whatever is the easiest and works well is fine with me.  
  

 I'm still having trouble understanding. In most Linux versions (that i'm aware of), you are given the choice to install grub (or lilo) in the MBR, in the /root partition, or not at all. I've never heard of a Linux that requires you to create an MBR partition ahead of time.

 Also, the MBR is not a partition in the true sense of the word; it's not counted as a primary (or any other type of) partition.

---

### Post by VMC on 2008-08-14
> **oldos2er said:**
> I'm still having trouble understanding. In most Linux versions (that i'm aware of), you are given the choice to install grub (or lilo) in the MBR, in the /root partition, or not at all. I've never heard of a Linux that requires you to create an MBR partition ahead of time.

 Also, the MBR is not a partition in the true sense of the word; it's not counted as a primary (or any other type of) partition.

I tend to agree with you here. It appears they are making this way more complicated than it should be. The OP is really not asking for our opinion but has stated what he wants. For me the "Kissable" approach is to have one partition per Distro, plus a Swap partition. I don't adhere to the old style of multiple partitions per Linux distros. I back up my /home directory and other stuff off site, and don't go by the theory "what if you loose etc, etc". I've never in all my years lost a partition, but I have had defective hard drives. Then ALL partitions are lost. I back up each partition off-site. I've heard all the reasons for and against. This is just my approach.

---

### Post by oldos2er on 2008-08-14
Maybe the OP should read [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

---

### Post by estyles on 2008-08-14
> **oldos2er said:**
> I'm still having trouble understanding. In most Linux versions (that i'm aware of), you are given the choice to install grub (or lilo) in the MBR, in the /root partition, or not at all. I've never heard of a Linux that requires you to create an MBR partition ahead of time.

 Also, the MBR is not a partition in the true sense of the word; it's not counted as a primary (or any other type of) partition.

I think you're confusing the grub files and the grub bootloader.  The bootloader can go in the MBR and/or in any other partitions boot record.  When the bootloader in MBR loads, it looks for a menu.lst and, for linux distros, kernel images.  If you choose to simply install grub regularly, then each additional distro that you install will overwrite grub in the MBR, and point it at the menu.lst in its own partition.  Some distros will look for other distros to include, some won't.  If and when you upgrade your kernel, changes will be made to the menu.lst and /boot directory of whatever OS you are currently running.  This may or may not be the /boot directory that the bootloader in the MBR is looking for.  In short, it's a recipe for random chaos, and I doubt you could possibly end up with an organized system that is bootable into all of your OSes, other than by sheer luck, or by keeping all of those /boot directories synced manually.  If you install the OSes in the proper order and all of them handle parallel GNU/Linux OSes properly, then you may start off with a system the way you want it, but if you do any kernel upgrades or install any OS that doesn't handle other OSes properly, then it will get screwed up in a hurry.

The way I handle this is to mount a separate /boot partition that contains all kernel images, and update my menu.lst by hand.  There is also a way to create a grub partition with its own menu.lst.  The menu then would look something like this:

1) Ubuntu -> load up the menu.lst from /dev/sda3, kernel images for Ubuntu are kept there, and Ubuntu manages its own /boot directory.

2) Linux Mint -> load up the menu.lst from /dev/sda4, kernel images for Mint are kept there, and Mint manages its own /boot directory.

3) OpenSUSE -> load up the menu.lst from /dev/sda5, kernel images for SUSE are kept there, and SUSE manages its own /boot directory.

4) Windows -> the usual menu.lst entry for Windows, which sets /dev/sda1 active and then runs chainloader


As for Data files, unless you work on different files in different OSes, you want certain data files to be shared.  You can either keep all the Data files with one OS and then mount that drive and make symbolic links in each other OS, or you can create a Data partition (my preferred, because it doesn't necessarily involve backing up and transferring files if you upgrade or switch that primary OS) and do the same.

I don't know if the benefits of multi-booting are really worth all the extra work - I tend to gravitate toward one distro and not really boot up the others much if at all.  I've now taken to trying out new distros in a VM instead of installing them and multi-booting - although if I think I might like a different distro, I'll multi-boot it and then maybe eventually switch to it full-time.  

Like I said, I don't know if it's worth it, but if the OP *wants* to multi-boot and try to do it as seemlessly as possible, it's kind of a complicated process, and there doesn't seem to be a good tutorial for it anywhere.

---

### Post by oldos2er on 2008-08-15
Ok, I get it now. Sorry for being dense.

 I've had three different Linux OSes installed at one time. The easiest way for me is to not allow the second and third ones to install grub or lilo, and edit menu.lst by hand. FWIW.

---

