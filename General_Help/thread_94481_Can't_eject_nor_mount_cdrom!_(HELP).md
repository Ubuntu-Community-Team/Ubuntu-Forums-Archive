---
title: "Can't eject nor mount cdrom! (HELP?)"
date: 2005-11-24
forum: General Help
---

### Post by Binnikemasken on 2005-11-24
Hi everyone!
I've been using Ubuntu for a little while now and haven't got any major problems until now.

(The thing is I got bored of not playing anything so I thought I could download Cedega and install a game.)

So I installed Cedega and then inserted the first Diablo 2 disc :)
Everything seemed to work as planned 'til the real installation started and it asked me to switch disc. And that's exactly what I tried, but I couldn't eject the cdrom.
After trying a few things I decided to abort the installation and skip this whole "game scene". But I didn't, and it turned out I tried again.

This time it didn't even read anything from the disc. And this happened several times. I took another disc with some series in to see if it was something wrong with the game disc, and TADA(!): it didn't work either. But the problem now was that I couldn't eject the disc at all.

I rebooted the computer and tried again, but then this error message appeared: "eject: unable to eject, invalid argument"
When I tried to open the cdrom by double clicking in the window system this message appeared: "Indicated UDI is not a mountable volume".
Mounting and ejecting doesn't work in any kind of way now...

Hope you understand what I'm writing :)
If it's necessary to know the computer also crashed once when I tried to eject the cdrom after the second boot...
Well, I've been using CD's before and it worked properly then. But now something really weird turned up. So, what's the problem here?! :confused: 

I'd appreciate any help!
Thanks

---

### Post by Ocxic on 2005-11-24
Try unmounting the device and any links to it
 use "mount -L" (LOWER CASE L) to list all of your currently mounted device's and paths
code:

sudo umount /dev/"your cdrom here"
or
sudo umount /media/"your cdrom here"

/code

and try turning "cd eject monitoring" on or off in cedega

---

### Post by jeffreyvergara.NET on 2005-11-24
you can also use the hardware eject button using this:

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

---

### Post by Binnikemasken on 2005-11-24
Well. When I list all the mounted devices the cdrom isn't in that list.
And when I try to mount/unmount it doesn't work. All it says is that no medium is found when I try to mount, or that there is no device mounted when I try to unmount...

Nothing happens when I write this: sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'

And this is driving me nuts, cause I really need to use the cdrom now...

---

### Post by Drifter on 2005-11-24
I have the same problem with cdrom drives.  I have been trying to find out how to get this fixed for sometime now.  Can anyone help us with this, it seems that people only look at the posts with this problem but don't seem to give any help on it.  My mount -l list is below, anyone know what this means and can u explain so we can understand it.  Thanks;

david@ubuntudlt:~$ mount -l
/dev/hdb1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=david)

---

### Post by Binnikemasken on 2005-11-24
I forced the cd-rom to open now.
But now it seems like the cd-rom is totally dead.

I inserted a windows cd and booted, but no reaction and everything booted up as normal.

Now I don't know what to do to see if this whole thing works at all... Any suggestions?

---

### Post by arphe_el on 2005-12-02
try using this command from the root terminal 

sudo eject /media/cdrom0

hope this helps cheers :-)

---

### Post by arphe_el on 2005-12-02
I would like to post this question on how to share eject cd priveledges to other users since it only support the root users.

any help are appreciated :)

---

### Post by rabidpilot on 2008-05-23
I installed Diable 2 on ubuntu with out any issues.

I entered in terminal window  wine d:\install.exe and then I was able to eject the disks.

---

