---
title: "How to access encrypted LVM drive?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by jbrice on 2009-07-02
I have just done a clean encrypted re-install of Ubuntu Jaunty on a laptop that was using an encrypted install of Hardy (both done using the standard encrypted partition + LVM method as on the "alternate" CD.

As the re-install was done on a new hard disk, I would like to be able to mount the old Hardy encrypted drive via an external SATA/USB adapter gizmo and be able to directly access files - e.g. config and data - to enable me to migrate stuff from Hardy to Jaunty.

Would some kind person - who understands this better than I - please provide the detailed steps needed to mount and unlock the old Hardy encrypted disk.

TIA

---

### Post by Herman on 2009-07-02
Here's a link that should help you, 
**[Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html")**

If you still need more help, don't be shy to post here again and ask. 

If you found the link helpful it would also be nice if you could post back and say so.
The web page's author might happen to see your post some day. :)

---

### Post by jbrice on 2009-07-02
Herman,
Very many thanks for the pointer to that. It is a rather cryptic how-to for someone like myself - in the Linux tradition I guess :)
However I have picked my way through and it's now working for me.

Following the procedure given:
> Install required packages using the following command

sudo apt-get install lvm2 cryptsetup

probe required module using the following command

sudo modprobe dm-crypt

As I was already using an encrypted file system on the Jaunty host system, the above steps were not necessary in my case - Synaptic confirmed that these packages already installed.

> sudo cryptsetup luksOpen /dev/hda5 crypt1

Enter your passphrase. You should get the following message:

key slot 0 unlocked.
Command successful.
If not, something has gone wrong.
On plugging in the SATA->USB adapter, a pop-up appeared  - "Unlock Encrypted Data" - requesting the passphrase for the drive. This appears appears to do the same as the above command line input (new feature on Jaunty?)

> Scan for volume groups

sudo vgscan --mknodes
sudo vgchange -ay

REMEMBER the name of the volume group, as you will need it later.

The first action showed the two volume groups, one used by the host system LV and the second by the LV on the USB-connected drive. (Both LVs having the same name would seems to be a potential problem? :( )

> Create a mount point

sudo mkdir /volume

mount the encrypted volume to the mountpoint you just created.

sudo mount /dev/paulb-desktop/root /volume

The volume is mounted, now you can chroot or whatever else you need to do. If you would like to open the gnome file manager for writing to it issue the following command:

sudo nautilus /volume

I created a new folder - /media/disk1/ to act as a mount point for a logical volume, and mounted it thus:

mount /dev/volume_name/lv_name /media/disk1

and - behold - the disk contents appear at /media/disk1
:)

I happened to know that the logical volume name ("lv_name" above) that contained the old installation was "root" - but otherwise I would have had to use:
sudo ls /dev/volume-name/
to see the name(s) of the logical volumes on the encrypted part of that drive.

---

### Post by Herman on 2009-07-03
Thanks for your reply, jbrice.
It took a while for me to get around to it, but I tried it too and I had a little trouble at the end of that how-to as well. 

For the sake of anyone finding this thread in the future, if you're not sure what to enter for,```
sudo mount /dev/[COLOR=Red]paulb-desktop[/COLOR]/root /volume
```Use 'sudo ls /dev/',```
 sudo ls /dev/
``` and hopefully you should see the name of your volume group there somewhere, (which you would probably remember from earlier).
In my case, the 'volume-name' is the name I gave my operating system, mine's called 'beagle'.

Then use 'sudo ls /dev/<volume-name>/'
```
sudo ls /dev/beagle/
```For an answer from that command I got 'root' and 'swap1'. So, 'root' is quite likely right for everyone.

---

### Post by xhaansx on 2011-02-03
Could someone help me understand the line "sudo cryptsetup luksOpen /dev/hda5 crypt1"? Where "/dev/hda5" goes, is that the path of the device on which you have files you'd like to access? I typed in "sudo cryptsetup luksOpen /media/fb7bf747-[...]/home crypt1" and it responded: "Cannot open device /media/fb7bf747-[...]/home for read-only access."

Sorry not trying to hi-jack, but I also just posted this thread (which helps explain my dilemma): [http://ubuntuforums.org/showthread.php?t=1681285](http://ubuntuforums.org/showthread.php?t=1681285) (it's urgent).

---

### Post by Herman on 2011-02-04
:) Hello xhaansx,
If you're using a reasonably recent version of Ubuntu, you can probably skip most of those old commands. I don't think it's necessary for us to use all those commands now, or at least not under normal everyday circumstances. The original posts in this thread are quite old, dated July 2009.
Probably the only command we still need is 'sudo apt-get install lvm2 cryptsetup'.

At least for me, after I have those packages installed my Ubuntu Maverick Meerkat, Lucid Lynx and possibly Karmic too I think, will open a LUKS encrypted volume without any more commands.

To test that I just plugged in a USB external flash memory stick which contains a Ubuntu installation with separate partitions for root, usr, tmp, var and home.
A sign came up in my Maverick Meerkat operating system saying something like  'Enter a password to unlock the volume'.
I entered the password, and then another sign came up telling me  'Unable to mount 16GB LVM2 Physical Volume', so I clicked (OK).
Then I went 'Places --> 'Removable Media', and all my encrypted file systems appeared in the list there, and I simply clicked on the one I wanted to look in for the file system to be mounted and a browser window to open and reveal my files. :)

EDIT: You might also need to do 'sudo modprobe dm-crypt', I'm not sure, but anyway it's pretty easy now, simpler for the user than it was when this thread was started.

---

