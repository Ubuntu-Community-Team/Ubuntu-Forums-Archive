---
title: "External HDD: Cannot set permissions"
date: 2010-02-09
forum: Hardware
---

### Post by Ageris on 2010-02-09
Hi

I have three external HDDs (NTFS) hooked up to my media center running Ubuntu 9.10. I have set up some accounts for use with proftpd so I can share my stuff with others, but they cannot access the files. This worked fine in 9.04. I have tracked the problem down to file permissions. It seems I am unable to change permissions for any file/folder on the drives. Current permissions allow owner (me) full access, but nothing for group or other and whenever I try to change this (using chmod or GUI) nothing happens, not even an error.

I have looked around for several solutions, but as I am a relative newbie when it comes to terminal commands I have had no success.

If anyone could help me out I would greatly appreciate it.

---

### Post by Ageris on 2010-02-09
bump

---

### Post by Ageris on 2010-02-10
Last bump

Anybody?

---

### Post by Lilonius on 2010-02-11
I have more or less same problem. I want to share my external drives using Samba and i can't since i can not change the permissions to the files/folders or partitions in the external USB NTFS HDD. I tried a lot of tips/tricks provided on different threads in the forum but they just don't seam to work. 

Is this a bug?

---

### Post by Morbius1 on 2010-02-11
**Ageris**, I've been debating with myself for 2 days now on responding to your post because I was hoping that someone would have a better idea than the following. I don't think there's an easy answer for your dilemma.

(1) There has been a change to how Ubuntu automounts external ntfs USB devices. Before it would mount with root being the owner and permissions to read / write to everyone. Now it mounts with you as owner and read / write to you only.

(2) chmod and chown do not work on any windows filesystems so that's not going to help you.

(3) If this was a FAT32 usb device the solution was simple. Create a line in fstab that mounted it with the permissions you wanted. For example:
> UUID=DA9056C19056A3B3 /media/ExtHD vfat user,umask=000,utf8,flush,noauto 0 0This would allow whoever ( user ) plugged  the device in ( noauto ) to become the owner with read / write permissions to everyone ( umask=000 ). Unfortunately it doesn't work with NTFS.

The closest you can get to this approach is to create a line in fstab that looks like this:
> UUID=DA9056C19056A3B3 /media/ExtHD ntfs defaults,umask=000,utf8,flush 0 0But this becomes a management issue. The devices have to be turned on before you boot into the box it's attached to. And it cannot be unmounted by the user but only by root.

(4) You could mount it by hand through the terminal:
> sudo mount -t ntfs UUID=DA9056C19056A3B3 /media/ExtHDAnd then unmount it by hand:
> sudo umount /media/ExtHDBut when you first turn the usb device on it will automatically mount by itself with the wrong permissions. So you have to first unmount the automounts before you mount them through the terminal.

**Lilonius**, you have a completely different problem because you're using Samba. In your case it has a solution. You might want to look at this: [http://ubuntuforums.org/showpost.php?p=8807176&postcount=2](http://ubuntuforums.org/showpost.php?p=8807176&postcount=2)

---

