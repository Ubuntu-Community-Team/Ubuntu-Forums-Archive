---
title: "Mount problem"
date: 2010-07-03
forum: Hardware
---

### Post by JuricaG on 2010-07-03
Hello everybody!

I'm quite new to Ubuntu and I'm really happy with it for the last couple of weeks I've been using it.

Few days ago, I tried application called **PySDM** to add the option of auto-mount for my **NTFS** partitions. Unfortunately, now I cannot unmount these parttions and apps like Rhytmbox or Shotwell cannot access them. Everytime the try to open files from the partition or unmount it I get the message:


> Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda5 from /media/sda5

Please help, I don't know how to solve the problem!

---

### Post by JuricaG on 2010-07-03
OK, I tried to change settings in PyDSM, but nothing works. My apps cannot the access the files, partitions are useless.

HELP!

---

### Post by artemyv on 2010-07-03
> **JuricaG said:**
>  Everytime the try to open files from the partition or unmount it I get the message:!
use 

```
sudo umount
```

command

---

### Post by Morbius1 on 2010-07-03
Post the output of the following commands so we can see what pysdm has done to you:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by JuricaG on 2010-07-03
> **Morbius1 said:**
> Post the output of the following commands so we can see what pysdm has done to you:

```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

This is what I got from the commands:

> /dev/sda1: UUID="838a86c6-5691-4d92-b4bd-62b55d5c9d75" TYPE="ext4" 
/dev/sda5: LABEL="My Documents" UUID="5EDD056635B113E5" TYPE="ntfs" 
/dev/sda6: LABEL="Igre i Video" UUID="7B8FDB4B606B1186" TYPE="ntfs" 
/dev/sda7: UUID="2c4c84d0-d53c-4925-8c05-86716205ff66" TYPE="swap" 

and

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
/dev/sda1                                  /            ext4  errors=remount-ro             0  1  
# swap was on /dev/sda7 during installation
UUID=2c4c84d0-d53c-4925-8c05-86716205ff66  none         swap  sw                            0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,umask=000,user  0  0  
/dev/sda6                                  /media/sda6  ntfs  nls=iso8859-1,umask=000,user  0  0  


---

### Post by Morbius1 on 2010-07-03
First of all the whole point of putting something in fstab to to enable to enable the system to automatically mount the partitions on boot and automatically unmount them at shutdown. If you want the ability to unmount them as a regular user then don't put anything in fstab for those partitions.

Anyway, to correct PysDM:
Change this
> /dev/sda5                                  /media/sda5  ntfs   nls=iso8859-1,umask=000[COLOR=Blue],[COLOR=Black]user[/COLOR] [/COLOR] 0  0  
/dev/sda6                                  /media/sda6  ntfs   nls=iso8859-1,umask=000[COLOR=Blue],[COLOR=Black]user[/COLOR][/COLOR]  0  0                        to this:
```
/dev/sda5 /media/sda5  ntfs defaults,nls=utf8,umask=000  0  0  
/dev/sda6 /media/sda6  ntfs defaults,nls=utf8,umask=000  0  0
```Actually you don't need the umask=000 for ntfs because it's in the defaults, but I like to keep it there just because someone may change the defaults.

---

### Post by JuricaG on 2010-07-03
> **Morbius1 said:**
> First of all the whole point of putting something in fstab to to enable to enable the system to automatically mount the partitions on boot and automatically unmount them at shutdown. If you want the ability to unmount them as a regular user then don't put anything in fstab for those partitions.

Anyway, to correct PysDM:
Change this
to this:
```
/dev/sda5 /media/sda5  ntfs defaults,nls=utf8,umask=000  0  0  
/dev/sda6 /media/sda6  ntfs defaults,nls=utf8,umask=000  0  0
```Actually you don't need the umask=000 for ntfs because it's in the defaults, but I like to keep it there just because someone may change the defaults.

This didn't solve the problem. On restart partitions appear to be mounted automatically, but apps don't recognize them (Rhythmbox can't open the songs, etc.)

What should I do?

I would like to make the partitions mount automatically on startup, but that apps like Rhythmbox or Shotwell can recognize them.

---

### Post by Morbius1 on 2010-07-03
Doing a quick search of the forums ( I don't have any idea what Rhythmbox is ), it appears that it needs to have you as the owner of the partition. Why that should matter - I do not know.

So to make you the owner instead of root add uid=1000 to the list of options ( you might as well add a gid=46 while you're at it ) so it ultimately looks like this:
```
/dev/sda5 /media/sda5  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0  
/dev/sda6 /media/sda6  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0
```Save fstab, and back in the terminal execute these in sequence:
```
sudo umount /media/sda5
sudo umount /media/sda6
sudo mount -a

```No need to reboot. See if you app is happy.

---

### Post by JuricaG on 2010-07-03
> **Morbius1 said:**
> Doing a quick search of the forums ( I don't have any idea what Rhythmbox is ), it appears that it needs to have you as the owner of the partition. Why that should matter - I do not know.

So to make you the owner instead of root add uid=1000 to the list of options ( you might as well add a gid=46 while you're at it ) so it ultimately looks like this:
```
/dev/sda5 /media/sda5  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0  
/dev/sda6 /media/sda6  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0
```Save fstab, and back in the terminal execute these in sequence:
```
sudo umount /media/sda5
sudo umount /media/sda6
sudo mount -a

```No need to reboot. See if you app is happy.

Thank you for trying, but it didn't work. I get this message when I try to mount from Nautilus after unmounting from terminal. 

> Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda5 on /media/sda5

Anyway, after I did the commands you gave me, app still doesn't recognize the partitions. Just to be sure, I'm posting a copy of my fstab.

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid           0  0  
/dev/sda1                                  /            ext4  errors=remount-ro             0  1  
# swap was on /dev/sda7 during installation
UUID=2c4c84d0-d53c-4925-8c05-86716205ff66  none         swap  sw                            0  0  
/dev/sda5 /media/sda5  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0  
/dev/sda6 /media/sda6  ntfs defaults,nls=utf8,umask=000,uid=1000,gid=46  0  0

---

### Post by Morbius1 on 2010-07-03
I simply don't understand why you are unmounting and mounting this partition. The following is not an error message:
>  mount: only root can mount /dev/sda5 on /media/sda5                      It's a statement of fact. Only root can mount. If you don't want to have it mount automatically don't put it in fstab.

As for your app not having access to the mountpoint - I don't know. I'll do a search on Rhythmbox and see what comes up.

---

### Post by rykel on 2010-07-03
I had this problem on Lucid and I solved it in 6 steps.

Simply purge 3rd party drive managers (eg. Storage Device Manager), comment out all the NTFS lines in /etc/fstab, delete all the mountpoint folders in /media (eg. /media/sdx1), do a "sudo blkid", reboot, plug in the devices and let Ubuntu auto-detect/auto-setup the UUID of the devices.

The problem seems to be due to the fact that Lucid does NOT use /dev to identify devices anymore, and uses UUID instead.

I hope that helps!

---

### Post by Morbius1 on 2010-07-03
>  The problem seems to be due to the fact that Lucid does NOT use /dev to  identify devices anymore, and uses UUID instead.That is an incorrect statement. You can use /dev/sdxy, UUID, or LABEL to identify the partition. I may be reading more into the OP's postings than he meant but it appears that the partition mounts just fine. The problem is one applications inability to access the partition.

---

### Post by JuricaG on 2010-07-03
> **Morbius1 said:**
> That is an incorrect statement. You can use /dev/sdxy, UUID, or LABEL to identify the partition. I may be reading more into the OP's postings than he meant but it appears that the partition mounts just fine. The problem is one applications inability to access the partition.

Yes, after editing settings in fstab, partitions mount automatically on startup and I can read/write on them. The problem is that applications like Rhythmbox (media player) or Shotwell (photo manager) are not able to recognize the files on them anymore. And this happened after I used PySDM.

---

### Post by Morbius1 on 2010-07-03
JuricaG, 

Well, we've pretty much removed all traces of what Pysdm did to yo so let's try a different approach. Let's create a symbolic link from the /media partition to your Music folder:

Open up Nautilus and press F3 so it splits into two panels.
On the left panel open up /home/your_username/Music
On the right panel go to /media/sda5/wherever_your_music_folder_is
Select Ctrl+Shift while selecting the music folder on sda5 and drag it to your Music folder

You should end up with a "Link to ..." in your Music folder. Does your app see it now?

There has to be something about Rhythmbox that's going over my head ( which is really easy to do ). If you can read and write to the partition then I don't understand why an application you're running can't do the same.

---

### Post by JuricaG on 2010-07-03
Hallo Morbius1,

I tried to create link on Music folder but this doesn't work. I realized that all my Music, Photos and Documents folder don't appear anymore on Places menu. I used **Tweak Ubuntu** to change the default location for these folders (Music, Photos, Documents, Downloads) and I've put them on sda6. It is very likely that when I changed the fstab with PySDM, apps and Ubuntu couldn't find these folders anymore, since they were on the partitions I've changed settings for. I've tried to change the location of these folders (Music etc) to their original locations, but this doesn't work! :-(

Maybe this is why apps such as Rhythmbox won't open my music anymore. I can access the files just ok with Nautilus, but something is wrong with specified folders. Is there anyway to reverse this??

**My God, I've totally screwed up my PC!!!! HELP!!!**

---

### Post by Morbius1 on 2010-07-03
There's a listing for Rhythmbox and it's default folder in gconf. Maybe the answer is in there:

From a terminal type:
```
gconf-editor
```then go to: /apps/rhythmbox/library_locations

Double click "library_locations" and you can change the location to sda6 or wherever it is now.

---

### Post by JuricaG on 2010-07-04
> **Morbius1 said:**
> There's a listing for Rhythmbox and it's default folder in gconf. Maybe the answer is in there:

From a terminal type:
```
gconf-editor
```then go to: /apps/rhythmbox/library_locations

Double click "library_locations" and you can change the location to sda6 or wherever it is now.

I fixed the Rhythmbox problem, change the listings for library and now everything's working fine.  Partitions are mounted on boot and it's working great!

Thanks for your help!

---

