---
title: "How to mount hfsplus partition?"
date: 2009-02-21
forum: Hardware
---

### Post by HanDuo on 2009-02-21
Hi everybody,

I want to auto mount a hfs+ (journaling is off) partition (in my case: /sda3) to be used as a shared Volume with ubuntu 8.10 and OSX 10.5. Under OSX it (of course) mounts automatically. Under ubuntu I can only mount it via the desktop-gui (/media/myHFS+Volume), but only if nothing about the partition (sda3) is said within the fstab-file.

Here is what I tried so far:

Editing /etc/fstab-file with something like:


```
/dev/sda3 /mnt/myHFSplusVolume hfsplus ro,exec,noauto,users 0 0
```
In fact I tried several fstab configurations (e.g. with fstab set to default settings etc.)

Another thing I tried was to mount the volume via the desktop-gui and then to open/edit the volume "properties". Here one can also edit the mount point and other things. The result was the same like with editing the fstab-file. The volume was not visible any longer on the desktop or I got the message "unable to mount volume". 
When editing things via "properties" nothing was written to the fstab-file. So I now wonder were changes under "properties" are going to be written to?

According to [[COLOR="Blue"]this documentation[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2346494#post2346494") I also tried to mount/unmount the partition via the console/terminal. 
But then I get the message that the volume does not exist. 

Can anybody tell me why I can mount the volume via the desktop-gui but not via shell or why fstab might not work? 

Under OSX I have put volume settings to read/write everybody. 

Thanks for thinking about this.

Andreas

---

### Post by HanDuo on 2009-02-21
Sorry!

I overlooked that I have to create a directory that will hold the mounted disk. 

Now I am able to mount it via shell.

---

