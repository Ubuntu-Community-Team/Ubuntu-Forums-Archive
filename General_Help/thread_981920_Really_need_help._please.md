---
title: "Really need help. please"
date: 2008-11-14
forum: General Help
---

### Post by manus76 on 2008-11-14
I run windows(sorry) and it won't load up anymore...bsod. i was told to try and load linux to access my hard drive and manually restore the system. i am running ubuntu from a cd but i cannot copy files from my hard drive as i don't have permission. i tried the sudo command but it says it is a read only system. i have 2 years of work on this computer and i really need it. if someone could help i would really appreciate it and promise to dual boot future computers from now on.

thanks

---

### Post by mikewhatever on 2008-11-14
Try the following:
press alt+f2
type **sudo nautilus**

This should open the file browser with admin privileges.

---

### Post by manus76 on 2008-11-14
Hey,

Still won't let me copy. Can't change permissions. i am totally new to ubuntu so maybe i'm missing something easy...

---

### Post by The Cog on 2008-11-14
As mikewhatever says, **sudo nautilus** will get you a file explorer that has full admin rights. Using this, you should be able to click on the Computer button and then on one of the drive icons to open your Windows disk.

I guess the best move would be to copy all your important files to a USB drive or stick. If you plug a USB drive in, another nautilus window should open and you can drag/drop files or folders between the two.

I don't understand what you might be trying to do that would get you an error message saying about a read-only system. What were you trying to copy where, and exactly what sudo command did you try?

---

### Post by manus76 on 2008-11-14
Trying to copy files in my xp drive as i can't load windows. i'm only running ubuntu from the cd, would this be the problem?

---

### Post by black3ug on 2008-11-14
If you're running a live cd, then think you won't be able to copy your files to the desktop, if that's what you are trying to do. do what Cog says, use a usb flash drive for your backup operation.

---

### Post by The Cog on 2008-11-14
Trying to copy them to what? It is possible that your windows disk has been mounted readonly which would explain a read-only error if you tried to copy files **to** the windows disk. If you are trying to copy files **from** the windows disk to somewhere else, what is that somewhere else?

---

### Post by manus76 on 2008-11-14
I'm trying to copy restore files from one folder to another on my hard drive but it says that the drive is read only. I could copy them to a usb but i then can't copy them back on...

---

### Post by manus76 on 2008-11-14
when i open sudo nautilus it is open on the root folder. is there a way of opening it on the filesystem ie. /media/disk. or am i being daft?

i really appreciate the help...

---

### Post by mikewhatever on 2008-11-14
> **manus76 said:**
> when i open sudo nautilus it is open on the root folder. is there a way of opening it on the filesystem ie. /media/disk. or am i being daft?

i really appreciate the help...

You can navigate to /media/disk, or try **sudo nautilus /media/disk**.

---

### Post by manus76 on 2008-11-14
It still says that i'm on a read only disk...

---

### Post by The Cog on 2008-11-14
OK, I see what you are trying to do.

You can probably open nautilus straight on /media/disk with the command nautilus /media/disk, but it's probably not worth the effort. And /media/disk won't even contain anything until you have clicked the disk icon in Computer to make it mount.

As for the readonly issue, you may be stuck there. I believe that Linux will mount an NTFS disk in readonly if it is marked as not having been cleanly unmounted (i.e. improper shutdown). I don't know of a way to overcome this. It's a safety feature to prevent Linux from really screwing up an already possibly damaged disk (MS don't publish the full NTFS spec remember). The only way to overcome it that I know of is to get Windows to run a chkdisk on it, which is not likely to happen in your situation. The chkdisk would mark the disk as clean again.

I really think the safest option is to copy your important files to external media like USB drive or stick, before trying any repair procedure on the damaged windows disk. With 2 years work at stake, you shouldn't be playing fast and loose with it.

---

### Post by manus76 on 2008-11-14
Cheers people. I'll see what i can do with backing up files. If you think of anything later please let me know. Really appreciate it. I now know why you prefer linux.

manus

---

### Post by The Cog on 2008-11-14
It occurs to me that these commands might get your disk mounted read/write:
```
sudo mkdir /media/windows
sudo mount -o umask=0 -w /dev/sda1 /media/windiws
```
which would mount it in /mnt (as opposed to under /media). **sudo umount /mnt** will un-mount it again.  You might need to say sda2 instead of sda1, depending on which partition your windows is on - sda1 might be a manufacturers "recovery" partition.

If the above still mounts it read-only, I really don't know how to overcome that in Ubuntu. There are system rescue CDs that might do the trick, but you may have trouble downloading and burning one of those while only running on a live CD anyway.

---

### Post by TeXtonyx on 2008-11-14
You might have gotten an error like missing hal.dll. You think that
if you copy hal.dll or whatever file to Windows it will fix it. It
won't. Those error messages are very general. 

I think it is a good idea to copy files to a usb stick. My Documents
and your email. Use Google to find out what directory your email
client keeps all its files in and copy it. Also if your browser
links are important, copy the folders which contain them and your
Desktop. Now to what caused the blue screen of death, BSOD.

Have you tried the normal recovery things like tapping F8 and
choosing last know good configuration. Did you exhaust the Windows
recovery techniques first. Linux is good for saving your files, 
but _not_ good for repairing Windows.  

Unless you have a bad hard drive, you are in good shape. Even bad
memory is easy to fix with new. If nothing critical like your
motherboard is damaged you will do ok if you have your XP install
disk. Do a repair install. That means you will do a non-destructive
install which makes a C:\Windows.000 directory which functions 
instead of your old C:\Windows directory. Only a few data folders
are erased, I think My Documents is one of them. But nearly all
the data folders will be intact. You lose most of your applications
however, they will need to be reinstalled. The system never works
quite as well as it used to. 

Your problem is not that you didn't dual boot, though that is a
good practice in case you need to download something to help
fix the other OS etc. The problem is that you didn't already have
a backup. You might escape this situation, but there are 
catastrophic events like lightning strikes that will crisp your
hard drive and other stuff. Then there is no recovery of data. 

You better get your data onto a usb stick first because there is
no guarantee that the repair install will work; it depends upon
what caused the BSOD in the first place. If you have a desktop
a second drive will allow you clone your first (good)drive for a 
backup which isn't the perfect solution but good enough.

---

