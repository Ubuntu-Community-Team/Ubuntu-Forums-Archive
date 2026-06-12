---
title: "External drives no longer mount"
date: 2009-12-12
forum: Hardware
---

### Post by intangodelta on 2009-12-12
Hi, I'm running 9.10, and external usb drives are no longer being detected and mounted automatically. I can see the devices if I run Palimpsest disk utility, but the option to mount them is not available.

I have been working on getting a scanner to work today, and made a small modification to /lib/udev/rules.d/50-udev-default.rules in order to sort out some permissions problems as advised in the thread at [http://ubuntuforums.org/showpost.php?p=8234452&postcount=8](http://ubuntuforums.org/showpost.php?p=8234452&postcount=8)

I have tried to see whether reversing this change would help, but after the advised reboot, the file appears to have reverted to its original version - I've used diff to compare the current version with the backup and it returns no results, so I'm pretty baffled.

Finally, I tried reinstalling udev via Synaptic but no change.

Anyone got any ideas?
Thanks

---

### Post by intangodelta on 2009-12-28
<bump> - anyone got any ideas? I plugged in my Nikon DSLR today and that was recognized and mounted ok, so it just looks like USB drives and SD/SDHC cards at the moment.

---

### Post by SecretCode on 2009-12-29
Idea: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

---

### Post by intangodelta on 2009-12-29
SecretCode - thanks, I've gone through all the suggestions in that page now, and all the setting appear to be correct. The various drives all mount manually, just the automount is failing. There doesn't appear to be any error showing in the output from dmesg either.

Any other ideas?
Thanks

---

### Post by SecretCode on 2009-12-29
Does *sudo mount -a* work, after the system has booted? What's in your fstab?

---

### Post by intangodelta on 2009-12-29
No, sudo mount -a doesn't seem to do anything, and produces no errors either. My fstab is:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d94c2255-3aac-4ee1-8d61-34e0f36a00b8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3a8741e5-e3f9-45d7-8c20-a35890519df3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```

---

### Post by SecretCode on 2009-12-29
OK, ignore the mount and fstab questions ... you mean autodetecting drives when they are plugged in, not when they are booted, don't you? Sorry. 

Did you look at
> open a terminal and type gconf-editor followed by the [Enter] key.

Browse to /apps/nautilus/preferences/media_automount. 

What are the settings for the various media... keys there?

---

### Post by intangodelta on 2009-12-29
Yes, I checked the media... keys, they are:

media_automount = ticked (tried clearing and resetting this)
media_automount_open = ticked (I tried this unticked too)
media_autorun_never = unticked (tried this both ways)
media_autorun_x_content_ignore = [x-content/software, x-content/audio-cdda, x-content/audio-player]
media_autorun_x_content_open_folder = []
media_autorun_x_content_start_app = [x-content/software. x-content/video-dvd, x-content/audio-cdda, x-content/audio-player]

---

### Post by SecretCode on 2009-12-29
No more ideas from me ... anyone else?

---

### Post by SecretCode on 2009-12-29
Wait - I just saw **devkit-disks** mentioned in [this thread](http://ubuntuforums.org/showthread.php?p=8576176#post8576176)

Check out the man page - it's got all sorts of options for displaying drives properties and monitoring events. Might help.

---

### Post by intangodelta on 2009-12-29
Thanks for trying. devkit-disks was interesting to look at, especially the --monitor option, but it didn't give me much more than I already knew - the drive is connecting and being detected but just doesn't automount.

OK, anyone else have any ideas? I'm really trying to avoid a reinstallation here!

---

