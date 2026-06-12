---
title: "Dynamic configuration to make a static path"
date: 2008-06-04
forum: Hardware
---

### Post by frogitts on 2008-06-04
Here's the situation:

I use Skype, which has a habit of virutally removing all of my usb devices and then instantaneously plugging them back in. This results in my webcame being disconnected, the call being dropped, and my external hard drive being disconnected. Then, after finishing the call, I often want to play a game (Neverwinter Nights - thank you Blizzard!) that is installed on the external hard drive.

Neverwinter Nights looks for the path /media/ExternalHD, which is where my hard drive normally mounts. It is normally recognized as sdb1 and then 'routed' there.

However, when being unplugged and plugged back in, it gets remounted as sdc1, is not rerouted to /media/ExternalHD, and cannot be. There's an annoying little link remaining in Places and on my desktop to the ExternalHD in /media/ExternalHD which doesn't exist. There's no way to remove that icon. Also, even though /media/ExternalHD doesn't exist (the reason I can't delete it), I can't create a folder called "ExternalHD" through the Storage Device Manager. Logging out doesn't fix this; only a reboot does, and I'm getting sick of rebooting Ubuntu.

I just noticed that Storage Device Manager has dynamic configuration tools allowing it to recognize a device based on its characteristics, not on its location in /dev. However, none of these options seem to actually do anything. Anyone know how I can harness that power to get my External hard drive (the only MAXTOR device I own) to always mount to /media/ExternalHD?

---

### Post by frogitts on 2008-06-05
Well, I've done some more toying around and I'm still lost, but I'll post what I've tried so that others can try other things.

I thought it would be a good idea to use the UUID of the drive in fstab instead of the mount path, since the mount path can change but the UUID stays the same (right? does it?).

So I did, after removing the entries for /sdb1 and /sdc1 that I had in fstab, and restarted the computer. The drive mounted just fine. It even mounted well when I unmounted it, plugged it into another usb port, and mounted it again. However, it failed when I unplugged it without mounting it (which is what Skype does to my drive, effectively) because it won't let me mount it at all. I have two ExternalHDs listed - when I click on the one as root, I get the error that FUSE failed to access the mountpoint /media/ExternalHD, I/O error, and when  I click the other as root, I get "Error: Error stating file '/media/ExternalHD': Input/output error
Please select another viewer and try again."

Some other fun errors I get:
When I click on the remaining ExternalHD on my desktop, I get told "Couldn't display '/media/ExternalHD'. There is no application installed for this file type"
From the places menu, one of the two ExternalHDs: "Could not open location 'file:///media/ExternalHD'"

And my all time favorite, from trying to create a folder called "ExternalHD" in /media through the Storage Device Manager (since the place is obviously taken but no folder of this name exists):
"The folder could not be created. Error removing file: File exists."
Let me translate into English: I can't create this folder because I can't remove a file because the file I want to remove exists. Does that mean if the file didn't exist, it would be able to remove the nonexistent file and create the folder? :) I'm sure this means something to someone, but to me it's just hilarious.




So I'm back at square one, because when I had /dev/sdb1 and /dev/sdc1 configured in Storage Device Manager, I could at least mount them without being root, which is a really annoying thing to have to do, especially since I don't know how to build ntfs-3g with FUSE support or whatever.

Anyway, to restate my question a little more clearly, I think I'm really looking for a way to free up the name /media/ExternalHD when the drive that is mounted there gets unplugged without my permission so that I can remount the same drive to that same location without causing an error.

---

### Post by frogitts on 2008-06-05
Well, I have some exciting news! I realized that although all of the graphical interfaces to mounting/unmounting refuse to unmount a directory in /dev that isn't reflected in /media, I can still use the sudo umount command to remove the /dev entry! So I made this little script called 'fixhd' that only works for me, but that I'll post here for posterity if anyone else runs into a similar problem. Note that this script also remounts the drive after being unplugged and plugged back in. I don't really understand why this has to be done, I feel like there should be a way to do this automatically. The device has to be unplugged and plugged back in because it is now assigned to /dev/sdc1, but needs to be assigned to /dev/sdb1, and it won't release /dev/sdc1 until manually unplugged - on being plugged back in, it attaches to /dev/sdb1 because that's the first one available now that the script has freed it up.

To use this on your computer, replace every instance of /de v/sdb1 with your target /dev directory, replace /dev/sdc1 with the directory you don't want the drive to attach to (even though it does anyway), replace /media/ExternalHD with the target mount point for your drive, and replace ntfs with your file system. (And, of course, save it in a file with a useful name like 'fixhd' in /usr/bin and run chmod +x on it.)

```

#!/bin/bash

sudo umount /dev/sdb1
sudo umount /dev/sdc1
echo -n "Please remove and reinsert the usb cable for the External Hard Drive. Wait until the drive is recognized, and then press any key to continue."
read a
sudo mount -t ntfs /dev/sdb1 /media/ExternalHD
```

After all this, I still think there should be a way to make my system realize that this specific device with this specific UUID and specific characteristics needs to ALWAYS be mounted at this mount point, thus no other system should be mounted there and I should be prompted to remove any system found on that mountpoint if a conflict is encountered.

Now to figure out a way to get the thing to stop saying "Unprivileged user can not mount NTFS block devices using the external FUSE library". Anyone know how to rebuild ntfs-3g with integrated fuse support and make it setuid root? This is really the only reason for the last line of the script.

---

