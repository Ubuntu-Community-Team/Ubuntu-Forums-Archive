---
title: "Access to external hard drive after reboot"
date: 2013-11-11
forum: Hardware
---

### Post by ABCraine on 2013-11-11
I have an external hard drive that I like to keep plugged into my linux/ubuntu machine.
This is a home machine and we have 2 super-users/sys-admins/whatever you want to call 'em
When I am logged in, and plug the external drive in, I own it.
When the system reboots, and the drive is still plugged in, my partner owns it (my partner's name is
alphabetically before mine.  I would rather not bogus my login to force it to come first if I don't have to).
My partner and I belong to the same group, but the ownership of the hard drive comes back as
drwx------ 

How do I force a reboot to make the external drive either a) mine or b) have the correct ownership
so that I can access, no matter who owns it.

I'm not too familiar with sys-admin work, so please be specific (e.g. I saw someone mention how
it was mounted, but I don't know how to figure that out.  I plug it in and it works, or doesn't, as the 
case may be)

R

---

### Post by TheFu on 2013-11-11
You need to mount it like a normal internal drive - using the /etc/fstab.
Then you can set the permissions on the mount point to whatever you need.
If both users need r/w access, it would be a good idea to create a new group and put BOTH you and the other ID into that group, force the group to be the default for that storage.

I'm not good at providing detail directions, sorry for my failure. These links should help.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.howtogeek.com/howto/36845/the-beginners-guide-to-managing-users-and-groups-in-linux/](http://www.howtogeek.com/howto/36845/the-beginners-guide-to-managing-users-and-groups-in-linux/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ABCraine on 2013-11-11
Thanks, I'm almost there. I modified the fstab with the UUID, my mount location, for type I used ntfs (since that is what I saw when i did: sudo blkid), then for options I used:  auto,rw,user

When I tried it, I get:
drwxrwxrwx 1 root   root 

which tells me it is owned by root, with rwx for everyone.  So how do I make it owned by Me, with rwx for MyGroup?

R

---

### Post by TheFu on 2013-11-11
NTFS??????   That changes things.  You'll need to modify the mount options for the owner and group - but realize that NTFS permissions means next to nothing to Linux. Anyone can take the drive and mount it with whatever privileges they want.  **chmod/chown commands are ignored. ** Only the permissions in the mount options matter.

If the storage will be connected all the time, I would strongly suggest reformat to a Linux-file system. You can still share the storage over the network with Windows machines using samba.  If you are dual booting, stay NTFS and deal with these issues at mount time.  I hope this is only for data, not programs, 'cause NTFS sucks at that.

Also, in case it isn't clear - do not grab the drive and walk off if it is mounted. It must be umounted before unplugging it from a running system to avoid corrupt files, directories and other internal structures.

---

### Post by ABCraine on 2013-11-11
Many thanks.  I've got what I wanted.  (And yes, I'm aware that you don't "just pull the plug" when it's mounted like this.  Good reminder anyway.)

R

---

