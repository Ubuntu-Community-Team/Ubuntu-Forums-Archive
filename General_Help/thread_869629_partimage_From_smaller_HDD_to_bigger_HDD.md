---
title: "partimage: From smaller HDD to bigger HDD"
date: 2008-07-25
forum: General Help
---

### Post by mdsharp24 on 2008-07-25
Right now I have a Dell laptop with a 100GB HDD (/dev/sda1), and df shows only 4.3 GB used.

I routinely create a backup to a single image file on an external USB drive using partimage. In addition, I backed up my MBR using dd if=/dev/sda of=/my/external/USB/drive/backup-sda.mbr count=1 bs=512

I of course did all this booted into a Live CD.

Now, I am anticipating getting a new laptop in about a month and will want to restore the data. I realize doing so to a smaller disk is difficult if not impossible, but I understand going from smaller to larger isn't so hard. I have no doubt my new box will be well over a 100GB HDD.

So, I want to make sure I have the correct steps down in restoring an image made on one box to another box with a bigger HDD.

On the new computer, lets assume it's a 200 GB HDD.

1. I will boot using a Live CD and zero out the partition (likely it will come with Windows) and use gparted to make one large ext3fs partition. Lets assume the new box is /dev/hda1. I would use dd if=/dev/zero of=/dev/hda

2. Having a disk with no MBR and no data on a 200GB ext3fs drive, I would then restore the old computers MBR

3. Using partimage, restore the image created from the old computer.

4. Use gparted to resize the partition back out to 200GB.

5. edite menu.1st (GRUB) to reflect /dev/hda1 instead of /dev/sda1

Am I on the right track?

---

### Post by logos34 on 2008-07-25
if / sda1 was ~100gb, then that's size you should make the new partition, otherwise you will end up wasting space (more info in Partimage usage docs).  Restore the image to the new partition hda1 or whatever, restore grub or just reinstall it (see link my in my sig) to the mbr of the new drive and away you go.  If menu.lst is using "root=UUID=" format then you don't have to worry about hda vs. sda

Now resize / to take up the remaining space

---

### Post by mdsharp24 on 2008-07-25
Ah ok, let me see if I get this straight. When I get my new laptop that will likely come with windows, I will install a fresh copy of Ubuntu and use gparted to shrink the partition to the exact size of the computer I made the partimage image. This is the output of sflist and df -Th on computer now:

df -Th:

/dev/sda1     ext3    109G  4.9G   98G   5% /
varrun       tmpfs    471M  120K  471M   1% /var/run
varlock      tmpfs    471M     0  471M   0% /var/lock
udev         tmpfs    471M   52K  471M   1% /dev
devshm       tmpfs    471M   48K  471M   1% /dev/shm
lrm          tmpfs    471M   44M  427M  10% /lib/modules/2.6.24-19-generic/volatile

sflist -d /dev/sda:

/dev/sda1 : start=       63, size=228797667, Id=83, bootable

So, if I shrink the new computers HDD to the specs above, then re-install the mbr I made using 'dd if=/dev/sda of=/my/external/USB/drive/backup-sda.mbr count=1 bs=512' and finally using partimage to restore the actual image... I can then reboot into the live filesystem from the Live CD to check things out, then boot again from the LiveCD and reclaim lost space using gparted?

---

### Post by dcstar on 2008-07-25
> **mdsharp24 said:**
> Right now I have a Dell laptop with a 100GB HDD (/dev/sda1), and df shows only 4.3 GB used.

I routinely create a backup to a single image file on an external USB drive using partimage. In addition, I backed up my MBR using dd if=/dev/sda of=/my/external/USB/drive/backup-sda.mbr count=1 bs=512
.....

Please note that the MBR only takes the first 446 bytes, and then things like the Primary Partition table are also in the area up until 512 bytes -  so you are also backing up that too and can overwrite a Partition Table if you restore the whole 512 bytes!

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by unutbu on 2008-07-25
Will the new laptop have the same kind of video card as the current laptop? If your current laptop has an ATI card and your new laptop has an NVIDIA card, for example, then your /etc/X11/xorg.conf would have to be changed. 

There might be other details that would need to be changed as well. 

It might be easier to just backup your data, and then do a clean install from a LiveCD.

You can also store all of your installed packages on CD/DVD or external drive using the aptoncd package. Then you can the copy over the .debs and reinstall the packages...

You might find this CLI method interesting too:
[http://ubuntuforums.org/showthread.php?t=819396&highlight=dependencies](http://ubuntuforums.org/showthread.php?t=819396&highlight=dependencies)

---

### Post by mdsharp24 on 2008-07-25
**dcstar**, ok well you just educated me on something I didn't know. So, I will backup a new MBR now for the future HDD using: 'dd if=/dev/sda of=/my/external/USB/drive/backup-sda.mbr count=1 bs=446

Thanks for that bit of information.

**unutbu**, also good things to consider thanks. I really hate admitting this, but I have a compaq 7500US amd64 and even though I hate Compaq (it was a gift) the Nvidia video/networking and Conexant sound under Ubuntu has been great. Maybe Compaq only sucks under windows :)  I will be sure to backup vendor specific stuff like xorg.conf and others as well. I have no doubt after I restore the old image on the new laptop there will be some configurations that need to be changed. I may even try to stay with the same vendor on the new laptop when it comes to sound/video/networking.

---

### Post by stanley82 on 2008-07-25
Export all your emails stuff and bookmarks on the old machine and remember where you put them.

---

