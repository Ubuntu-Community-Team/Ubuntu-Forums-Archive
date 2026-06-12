---
title: "USB Thumb drive won't save"
date: 2006-01-27
forum: Hardware &amp; Laptops
---

### Post by vishnu on 2006-01-27
Hi there.  I have recently migrated to Linux from Windows after years of just playing with Linux.  Ubuntu rocks and I'm loving using it as main OS.
I only have one small problem.
I have a USB thumb drive MP3 player.  When I copy files to it in Windows I "eject" it via the system tray which makes sure all the files have been written.  There seems to be no such function in Ubuntu and when I unplug my thumb drive it doesn't remember what I copied to it.  I tried unmounting and it doesn't work.  What is the correct way of unplugging a USB drive in Linux and making sure all files have been written?

Many thanks

---

### Post by xmastree on 2006-01-27
When you connect it, it should appear on the desktop.
Right click the icon and there should be an 'unmount volume' option.

That's with gnome.

---

### Post by vishnu on 2006-01-27
Doesn't seem to work.  I leave it for a while after unmounting but when I check the device all the files i deleted are still there and the new ones aren't copied over.
If it helps I'm using a 128MB Smartdisk Rover

---

### Post by vishnu on 2006-01-27
AHHHHH
On further inspection it looks like I can copy files but not delete.  No worries for now as I can delete them from the player using the firmware.
Many thanks.

p.s. If someone knows a way to delete stuff successfully from the USB drive in Linux that would be great.

---

### Post by xmastree on 2006-01-27
Try deleting them as root.

---

### Post by vishnu on 2006-01-28
YEah that's the strange thing.  I'll delete and files will appear deleted - I can even unplug then replug the device in but it will report that whilst the drive is empty, there is no room for extra files.

---

### Post by xmastree on 2006-01-28
Try to show hidden files on it. there may be a .trash folder containing what you thought you had deleted.

---

### Post by vishnu on 2006-01-28
DOH!!!! <slaps head> Of course!! Did the trick.  Thanks a lot.

---

