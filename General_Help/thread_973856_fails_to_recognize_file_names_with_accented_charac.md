---
title: "fails to recognize file names with accented characters"
date: 2008-11-07
forum: General Help
---

### Post by Thorjelly on 2008-11-07
My problem is:

I have a 500GB hard drive nearly full with various sorts of media, but especially films.

Unlike most Americans, I enjoy foreign films. So some of these file names have accented characters in them.

I am moving my files to a 1TB hard drive because 500GB is no longer sufficient to hold my files.

When trying to copy files in Dolphin, it kept complaining that it could not write the file for each file that had an accented character.

So, alright. That's pretty dumb. But I decide to copy everything anyway, and once done, I loaded up my Windows guest VM running in Sun VirtualBox and used a file sync program on it to sync up the rest of the files.

Now the new hard drive has all the files from the old hard drive. I Great! In Windows, I can power down my HD and power it back up and they're there, I can play them off of the hard drive, etc. Except, now Linux still refuses to see any of the files that I had synchronized in Windows.

I'd like to note that in my original 500GB hard drive, Dolphin saw the accented files perfectly fine.

What the heck? Someone please respond soon. I am using 64-bit Kubuntu 8.10.

---

### Post by Thorjelly on 2008-11-07
*bumps* Please someone help?

---

### Post by michaelzap on 2008-11-07
I've had this problem also, although I could usually access the files (in Gnome) but accented and other special characters would be scrambled between Windows and Ubuntu. The issue is different character encoding between the systems, and I've never quite been able to straighten it out. You can try mounting your drive using a specific character set, and I think that there's also a tool for batch converting file names to UTF-8 (which may or may not show up properly in Windows afterwards, but is at least a more universal standard).

---

### Post by tagbre on 2008-11-07
This happend to me with the first Ubuntu releases, I'm a spanish speaker, I solved it by mounting the drives as UTF-8. I don't have to make this adjustment nowadays. 
I think mounting your new drive as UTF-8 will do it.

---

### Post by greyblitz on 2008-11-12
How can you mount the drive as UTF-8?

---

### Post by tagbre on 2008-11-12
> **greyblitz said:**
> How can you mount the drive as UTF-8?

Just add utf8 to the mount options for that device in your fstab file.
Example: dev/hda2 / ext2 rw,utf8 0 0

---

### Post by michaelzap on 2008-11-12
> **greyblitz said:**
> How can you mount the drive as UTF-8?

I do it in my etc/fstab file like so:
//192.168.0.120/archivos /mnt/tooga cifs credentials=/home/zap/.smbpasswd,uid=zap,iocharset=utf8 0 0

---

