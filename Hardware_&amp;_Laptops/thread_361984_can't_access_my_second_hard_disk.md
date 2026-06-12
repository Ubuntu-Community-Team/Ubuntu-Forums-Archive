---
title: "can't access my second hard disk"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by FreddyFrogg on 2007-02-15
Hi all,

I am a new linux user.
 I was recently running Fedora Core 6 where everything was working perfectly. then disaster, overnight my main OS hard disk stopped working.

I perchased a new hard disk and installed ubuntu 6.06. The system runs great. All the drives are shown with icons, including the second disk. however i can't access any of the data on it. I get a some kind of permissions error.
 when I check the disk properties, the permissions are set to "unkown" for the user and group.

Oh by the way, I don't seem to have a root user. 
 
All my important data is stored on my second hard disk. I really need to try to save this disk.

your help will be much apreciated.

---

### Post by amo-ej1 on 2007-02-15
you can access root related command by prefixing them with 'sudo' (e.g. sudo apt-get update en privode your user password).

Well, so the 'broken' harddisk doesn't show ? I'd suggest looking in dmesg for errors while accessing it and trying to manually mount it (man mount) and look for errors that it spits out.

---

### Post by FreddyFrogg on 2007-02-15
thanks for the sudo thing,

I did not have the drive listed when I typed mount in terminal.
The mount works in the manual way, it is listed now when I type mount.

What is "dmesg" and how do I access it.

---

