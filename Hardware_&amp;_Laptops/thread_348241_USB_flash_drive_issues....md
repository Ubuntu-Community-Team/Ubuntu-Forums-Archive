---
title: "USB flash drive issues..."
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by astronerd on 2007-01-28
Hello all, 
   I am trying to move some music from my Edgy desktop to my macbook with a San Disk 512 USB flash drive.  When I try to either erase info on it, or add anything on it I get an error saying "Cant perform action, disk is read only"   So I went to the properties and permissions and tried to change them there to be read and write.  No luck.  Anyone know what I can do and why this is acting this way?  I just want to trade files between computers with this....
Thanks

---

### Post by xmastree on 2007-01-28
It's not one of those with a write protect switch is it?

Failing that, try writing to it as root.

What filesystem is on it?

---

### Post by hal10000 on 2007-01-28
First look at your usbstick and see if there is a swich for write-protection.

Then from a terminal window do: [COLOR="Red"]mount[/COLOR] and see if there's a line similar to this one:
```

/dev/sdb1 on /media/usbdisk type vfat ([COLOR="Red"]rw[/COLOR],nosuid,nodev,quiet,shortname=mixed,[COLOR="Red"]uid=1000[/COLOR],[COLOR="Red"]gid=1000[/COLOR],[COLOR="Red"]umask=077[/COLOR],iocharset=utf8)

```
some of the values between the brackets may differ, but the red colored entries should be the same on your line. If this is not, then post the output.

As xmastree mentioned, as a first try you can mount it with root permission to check if it's not a hardware problem, but for permanent usage it's better to get it work without root permissions.

---

### Post by astronerd on 2007-01-28
Here is the needed part of my mount command..

/dev/sdb2 on /media/UNTITLED type hfsplus (rw,nosuid,nodev,uid=1000,gid=1000)

It seems that I should have rw access...
And if there is a switch for write protection on this thing, I cant find it.  
As for mounting with root priv.  I would like to be able to do this(if necessary) using the nautilus gui, instead of having to transfer the files via the command line.  I have files all over, and it would just be easier for me to click and drag, how can I have root priv while using nautilus? 
Thanks

---

### Post by hal10000 on 2007-01-28
Of course you should be able to use it via nautilus (or another file manager).
But first we have to find out where the problem is. It seems to be located in your hfsplus filesystem.
I found this link [http://www.ipodlinux.org/Installation_from_Linux_Hfsplus](http://www.ipodlinux.org/Installation_from_Linux_Hfsplus) where the following is mentioned:
> 
The linux hfsplus driver can read and write just fine, and is good for normal use, however it should be noted that it will mount read-only if the filesystem contains journaling or case-support. Both of which are not fully supported by the linux driver, and without a patch will cause it to mount read-only for safety. I recommend reformatting the ipod without journaling support so that this does not happen

Perhaps you should save the data on your usbdisk and reformat it without journaling support.

If you have problems in reformatting (or repartitioning) your usbdisk tell us here, and we try to do it together.

---

### Post by astronerd on 2007-01-28
Ok, I read that site and "tried" to reformat the USB using this command 

mkfs.hfsplus -v /dev/sdb2

but it said "bash: mkfs.hfsplus: command not found"

Sorry, but i dont have much experience formating in linux, so any help would be appreciated.
Thanks for all the help so far...

---

### Post by hal10000 on 2007-01-28
I just found a package that might fit your needs: hfsplus
You can install it e.g. by using [COLOR="Red"]sudo apt-get install hfsplus[/COLOR] from a command line. I don't know much about this package, but maybe it can solve your problem.

---

### Post by astronerd on 2007-01-28
I just installed hfsplus and nothing seems to have changed.  I read the man pages, and it didnt have much, just said that I should be able to use mounted mac paritions now.  So I did a google search on this, and it seems to be the same as the previous Ipod pages in terms of how to's...
  So I dont know if I am doing something wrong with this hfsplus(I unmounted the usb drive, then tried to change permissions again, still nothing) but its still not working.
again, thanks alot for your patience and help

---

### Post by xmastree on 2007-01-28
As it's Mac format, you might get better answers in the mac forum:
[http://ubuntuforums.org/forumdisplay.php?f=133](http://ubuntuforums.org/forumdisplay.php?f=133)

---

### Post by hal10000 on 2007-01-28
Just to be sure that it's not a problem of your user, mount it as root (of course after unmounting it first):[COLOR="Red"]sudo mount -t hfsplus /dev/sdb2 /mnt[/COLOR]
 and write (or delete) a file as root: [COLOR="Red"]touch /mnt/testfile.txt[/COLOR] This creates a zero length file on your usbdisk (if it works).

---

### Post by astronerd on 2007-01-28
Unmounted the drive, the tried this:
 sudo mount -t hfsplus /dev/sdb2 /mnt
mount: special device /dev/sdb2 does not exist

So I dont know whats goign on.  I did find alot of hfsplus stuff in the archives, so I will take a look at it later on. Thanks for all the help, I will post back what happens later when I get a chance.
Thanks again

---

### Post by hal10000 on 2007-01-28
When you plug in and off your usbdisk several times, it can happen, that your device is noticed with different dev/cenames (e.g. /dev/sdb2 and after plugoff and in again maybe /dev/sda2).
You can find the current name of your device [COLOR="Red"]with sudo fdisk -l[/COLOR] and then mount the device with the name listed.

But if you follow one of these threads you might have luck: 
[http://ubuntuforums.org/showthread.php?t=173438&highlight=howto+mount+HFS+volumes+as+writable](http://ubuntuforums.org/showthread.php?t=173438&highlight=howto+mount+HFS+volumes+as+writable)
[http://www.ubuntuforums.org/showthread.php?t=123785&highlight=hfs](http://www.ubuntuforums.org/showthread.php?t=123785&highlight=hfs)

---

