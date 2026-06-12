---
title: "chmod/chown help"
date: 2008-08-21
forum: General Help
---

### Post by Florida Cracker on 2008-08-21
Hello to all,
I have been using Ubuntu for about 5 months now and really like it. Yesterday I added another hard drive to my box and followed some steps I found posted on a site which had some adverse effects. The problem occured when I got to
sudo chown -R userid:userid /nas2
sudo chmod -R 755 /nas2
My user id is dad so I typed dad:dad. 
Well now I have no sudo abilities, nor do I have internet access. From what I have been reading, I need to reinstall the system, which is not a problem, but would like to know if there is an easy fix. When I sudo, it says must be root. I did remove the nas/2 file that the instructions stated to create and also replaced the modified fstab file with a backup copy.
I got the instructions from [www.xawk.com/ubuntu-add-hard-drive.html](www.xawk.com/ubuntu-add-hard-drive.html).
Thank you for reading and for any advice.

---

### Post by rjack on 2008-08-21
Those commands cannot break thing that hard.

Maybe you mistyped the chmod command?

Check your ~/.bash_history and look if the command you typed contains any spurious whitespace. Example: "sudo chmod -R 755 / nas2" (notice the space after "/").

If your permissions are screwed up there's no easy way to get the correct permission back and reinstalling the system is probably the fastest way.

---

### Post by silkstone on 2008-08-21
I agree with rjack - what you did shouldn't have messed it up unless you left a space after / and therefore changed the permissions of all the system files.

When you come round to doing all this again, create the new mount point under either /mnt or /media - don't create it under / as you have done.

So your new mount point will be, for example, /media/newdrive

If the mount point is under /media, an icon for the drive will appear on your desktop. If it's under /mnt, there will be no icon.

---

### Post by eotakos on 2008-08-21
if you mis-typed something and you actually changed all the permissions under /  ... it is ugly....

if your worry is that you can't perform sudo operations, you should check the sudoers file ; have a look here : 

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

this doc also contains the default sudoers so you will know if something is wrong there. By default the sudo command gives you all the power you will ever need if you are member of the admin group (as well as to every other member)

Good Luck!

---

### Post by Florida Cracker on 2008-08-21
Thank you very much for the tips, I anticipated a system restore was...'at hand', just wanted to be sure.

---

