---
title: "USB auto-mount"
date: 2019-08-04
forum: Hardware
---

### Post by n2te on 2019-08-04
I'm trying to figure out how to configure my Ubuntu (18.04) (not Ubuntu server) on my Dell notebook PC which I take when I travel to auto-mount a 128Gb SanDisk USB stick (FAT32 format) when hot-inserted into the USB slot. It's cumbersome to open a terminal each time and manually walk thru the same steps (lsusb, fdisk -l, mkdir, mount, etc ...) to mount and gain access to the stick. I'd much rather configure an auto-mount operation and be done with it each time it's hot-inserted into the USB slot on my Dell notebook. It's cumbersome to open a terminal each time and manually walk thru the same steps (lsusb, fdisk -l, mount, etc ...) in order to gain access to the device each time. My interest here is auto-mounting, not manually mounting. I did ask for some advice on a FB group but none of the suggestions (though quite informative) that folks gave to me have worked out. (Quite a few folks said, "Auto-mount works fine for me right out of the Ubuntu box!") Here's what I've learned so far:

~ If I try and boot the machine from a cold power-up state WITH the USB stick ALREADY inserted the PC hangs after I see the Dell Latitude logo quick opening splash screen pop up. Boot goes nowhere after that. Thus I have to turn off the machine, remove the stick, and then power the machine back on again. Not sure if this is related to my problem.
~ The lsusb cmd DOES show my USB device when it is inserted into the USB port. However none of my file managers list it as a mounted external removable media entity. (i.e. Dolphin, Nautilus, Nemo, etc ...)
~ I've been advised by some that USB auto-mounting does occur right-out-of-the-box in Ubuntu. No user intervention required. Not on mine it doesn't. Is there a utility or cmd that will allow me to reset the USB port in order to get that Ubuntu out-of-the-box default functionality and maybe auto-mount will work?
~ I see there's a utility called 'usbmount' but I can't figure out IF and HOW I can use it as the descriptions I find for this utility appear to indicate that it's ONLY for Ubuntu server which is not what I'm running. 
~ I see that there's something called 'gnome-volume-manager' and 'gnome-volume-properties' but I'm unable to launch either of those to see if that would help solve my problem. I get an error 'command not found'.
~ I've been advised by some that I should open 'DISKS' and click on my USB drive and configure it there to auto-mount. Only one problem. The 'DISKS' user interface page doesn't even list my USB disk and thus I can't configure something that it doesn't see.
~ I've been advised by some that my USB stick is probably bad. However I CAN manually mount the USB stick and I CAN read from and write files to the stick on my notebook. And the same stick works fine on my iMac machine running OSX and Parallels/Win7. No problems there. Auto-mounts just fine and R/W's perfect on either side of the 'house', OSX or Parallels VM. So I'm assuming that the stick is probably functionally OK.
~ I've been advised that I may have inadvertently disabled or blacklisted my USB device and thus auto-mounting will not occur. Is there a way I can check for this? Using 'compiz', 'dconf' or 'gnome-control-center'? Is there a utility to check?

~ The current contents of my '/etc/fstab' file is:

  # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=0ff86fdd-c7a4-47fd-ad5a-8d5600be5f8d /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0


My apologies if I haven't done enough research into this problem to find a solution. I know it drives many bonkers when someone asks for help and hasn't tried to solve the issue on their own. But frankly with the degree of linux knowledge that I do have, I feel that I'm stuck at this point. Any suggestions?

---

### Post by Dennis N on 2019-08-04
As a point of information, can you confirm you have more than one file manager installed?

---

### Post by rbmorse on 2019-08-04
Also verify the stick is formatted FAT32 and not ex-fat. 

Ubuntu does not support exfat out of the box, but you can install the exfat-fuse and exfat-utils packages (you need both) from repository.  I've had mixed success using them.

---

### Post by ajgreeny on 2019-08-04
As rbmorse has mentioned exfat filesystems in the post above, it is worth pointing out that by default, most USB or flash memory cards of 64G or above, so probably your 128Gb SanDisk USB will be formatted to exfat when purchased, at least partly because it has a larger file-size limit than fat32.

You will have to either format it to some other filesystem, (fat32, ntfs, ext# [for Linux only] ) or try installing those two packages rbmorse spoke of.

I've never used exfat so can not tell you anything aba similarout the likely success of using exfat in Linux, but I know some users have had success.

---

### Post by n2te on 2019-08-04
The stick IS formated FAT32. At least that's what my OSX and Win7 machines tell me. ..... When I posted this question for assistance on FB, eventually the responses stopped and I could only conclude that this problem was not fixable. There MUST be a solution. If anything, this problem which I would think is quite simple to fix but I guess not, is really intriguing me. I continue to ask for suggestions. There's gotta be an answer.

---

### Post by TheFu on 2019-08-04
> **n2te said:**
> The stick IS formated FAT32. At least that's what my OSX and Win7 machines tell me. ..... When I posted this question for assistance on FB, eventually the responses stopped and I could only conclude that this problem was not fixable. There MUST be a solution. If anything, this problem which I would think is quite simple to fix but I guess not, is really intriguing me. I continue to ask for suggestions. There's gotta be an answer.

**Did you actually install the packages mentioned above or not?**  Ignoring helpful suggestions doesn't help anyone.

I use **autofs** to handle mounting of external storage, on-demand.  It doesn't mount partitions until they are requested and only keeps them mounted for the time it is actually used.  I use the LABEL option to control which stick gets mounted where.  With autofs, we have control over the mount options just like we were mounting it manually.

---

### Post by brian_p on 2019-08-05
> **TheFu said:**
> I use **autofs** to handle mounting of external storage, on-demand.  It doesn't mount partitions until they are requested and only keeps them mounted for the time it is actually used.  I use the LABEL option to control which stick gets mounted where.  With autofs, we have control over the mount options just like we were mounting it manually.

Along the same lines as this suggestion: n2te could take a look at *Accessing the Package Archive* at [https://wiki.debian.org/Installation+Archive+USBStick](https://wiki.debian.org/Installation+Archive+USBStick).

---

### Post by n2te on 2019-08-05
FYI, I DON'T ignore HELPFUL suggestions. I did not install those 2 packages thus far because, as I previously mentioned, both my OSX and Win7 machines indicate that the stick is currently formatted as FAT32. Would both of those machines report formatting of FAT32 if, in fact they were exFAT and not FAT32? Therefore I concluded that there was no need to install two packages to handle an exFAT stick if the stick was not that format. Seemed like a reasonable assumption to me. Thus, I wasn't ignoring a helpful suggestion. Just trying to think through my issue in an informed manner rather than poking at it blindly not understanding what I was doing.  I'm not an experienced Linux superuser. Thus I have to walk before I walk before I run.  I'll research autofs next and learn how that utility works and try that to see if it solves my auto-mount problem. Thanks.

---

### Post by brian_p on 2019-08-06
Which two packages? The method I recommended requires no extra packages. Everything is on your system already and takes about 15 minutes  (including a possible reboot) to set up. We take it you will report back?

---

### Post by n2te on 2019-08-06
> **brian_p said:**
> Which two packages? The method I recommended requires no extra packages. Everything is on your system already and takes about 15 minutes  (including a possible reboot) to set up. We take it you will report back?

I will certainly report back. There's quite a bit of information on that page but with my lack of linux expertise and experience it may take me a bit of time to understand how to use that info to successfully have a USB stick auto-mount. But I will try. My apologies if my response time to report back is slow. I'm not working on this problem on a full time basis. Thanks. I certainly appreciate your suggestion.
[COLOR=#0000ff]
[I]The techniques described on this page have the objectives of 
[/I][/COLOR]
[LIST]
[*][COLOR=#0000ff]*Producing an automated installation of a Debian operating system from a USB stick. *
[/COLOR] 
[*][I][COLOR=#0000ff]Having the USB stick also hold a Debian archive to allow package installation from it after the OS has been installed. [/COLOR]
[/I] 
[/LIST]

---

### Post by Autodave on 2019-08-07
All of my USB sticks are formatted NTFS and I have never had a problem with any of them being recognized.

---

### Post by ajgreeny on 2019-08-07
> **Autodave said:**
> All of my USB sticks are formatted NTFS and I have never had a problem with any of them being recognized.
Not a good idea if you have no Windows OS to repair them if necessary; just about all you could do in Ubuntu is to reformat them if the NTFS needed a chkdisk.

---

### Post by #&amp;thj^% on 2019-08-07
I too use the NTFS format.
Well I do it all the time with, "ntfs-3g". Then run the ntfsfix command on your NTFS partition.

For example only:
```

ntfsfix /dev/hda6
```

You can use -b and -d option together. -b tries to fix bad clusters and -d to fix dirty states. So the command can be
```

sudo ntfsfix -b -d /dev/sda6
```

--help shows them
```

ntfsfix v2017.3.23 (libntfs-3g)

Usage: ntfsfix [options] device
    Attempt to fix an NTFS partition.

    -b, --clear-bad-sectors Clear the bad sector list
    -d, --clear-dirty       Clear the volume dirty flag
    -h, --help              Display this help
    -n, --no-action         Do not write anything
    -V, --version           Display version information

```
unfortunately the ntfsfix tool is very limited compared to Microsoft's chkdsk. 
```
DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

```
Then for those hard to reach problems, fix the NTFS partition running chkdsk off [Hiren's BootCD]("https://www.hirensbootcd.org/").

---

### Post by Morbius1 on 2019-08-07
Isn't it kind of irrelevant what filesystem he has on these USB devices?

His system doesn't automount them. It's not clear if his system even knows it is attached.

Attach the device and run the following command:
```
sudo blkid -c /dev/null
```
Does it list your device?

---

