---
title: "How to move /usr to a new drive?"
date: 2009-01-23
forum: Hardware
---

### Post by silverbullet007 on 2009-01-23
I've run into a situation here.. I tried pulling the Intrepid upgrade from home here and have ran into a space issue. i.e. I dont have enough.

So I'd like to move my /usr to my secondary drive which has over 160gigs free.  I've goggled a little bit but most of the info I found pertained to either different distros.. or was outdated.

So I tried searhing for "move /usr" to no avail either.  So I'm asking the masters of ubuntu.. is there a reletively painless way to perform this move?

Thanks!

Here's my current fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d27c5727-0319-46f4-b3f8-29e488992f04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a66d42d-3729-4b6b-a552-7efa25f6ab9b /home           ext3    relatime        0       2
# /dev/sda2
UUID=6a2491d4-6629-454c-aad3-0db187063279 none            swap    sw              0       0
# /dev/sdb2
UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

And df- h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.9G  4.1G  584M  88% /
varrun                1.7G  232K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   72K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1             225G   34G  180G  16% /home
gvfs-fuse-daemon      4.9G  4.1G  584M  88% /home/allanon/.gvfs
/dev/sdb1             231G   51G  169G  24% /media/disk
allanon@sputnik:/etc$

---

### Post by jocko on 2009-01-24
I think it should be possible.
What you would need to do is, in this order (make sure you have a functional live cd before you start, you will need it when you want to delete the old /usr folder and if you need to recover in case this fails):

1. Make a new partition (ext3) on the target hard drive (use gparted).
2. Mount the new partition (I'll use /media/usr in my example below, but any mount point will do).```
sudo mkdir /media/usr/
sudo mount /dev/sdb[COLOR=Red]3[/COLOR] /media/usr [COLOR=Red]#or whatever /dev/sdXY is your new partition[/COLOR]
```3. Copy everything from your current /usr directory to the root of the new partition (but do NOT delete the original /usr folder yet).
To copy from the terminal:```
sudo cp -rv /usr/* /media/usr/
```4. Make a new entry in your /etc/fstab for the new partition. Duplicate the line for your "/" file system (sda3), but change the uuid to the correct one for your new partition and set the mount point to "/usr". the uuid can be found in the output of:```
ls -l /dev/disk/by-uuid/
```5. Reboot and make absolutely sure everything works and that the new /usr partition is really used.
6. When you are sure everything works the way it should, boot a live cd, mount the partition containing your ubuntu "/" file system. Delete the contents of the old /usr folder.

If you need more details on some of the steps, just post a question in this thread and I or someone else will try to help.
And: any problems that arise before step 6 are easily fixed by simply commenting out or deleting the new line in fstab, but after step 6 there is no easy way back.

---

### Post by silverbullet007 on 2009-01-24
Ok cool.. following your instructions jocko..

Shrunk /media/disk and created new ext3 part /media/disk-1.  Coppied entire contents of /usr to /media/disk-1/usr/, compared property panes of both, total number of files the same and total size the same.

allanon@sputnik:/$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-01-24 13:26 2947f429-8da2-4c68-acbe-a838ffd4162c -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 6a2491d4-6629-454c-aad3-0db187063279 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 7a66d42d-3729-4b6b-a552-7efa25f6ab9b -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 d27c5727-0319-46f4-b3f8-29e488992f04 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-01-24 13:09 f9ad24bc-db09-48d2-9316-95e50ca7c9e2 -> ../../sdb1
allanon@sputnik:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.9G  4.1G  563M  89% /
varrun                1.7G  232K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   76K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1             225G   34G  180G  16% /home
gvfs-fuse-daemon      4.9G  4.1G  563M  89% /home/allanon/.gvfs
/dev/sdb1             214G   53G  152G  26% /media/disk
/dev/sdb2              18G  3.1G   14G  19% /media/disk-1
allanon@sputnik:/$ 


Modified fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d27c5727-0319-46f4-b3f8-29e488992f04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a66d42d-3729-4b6b-a552-7efa25f6ab9b /home           ext3    relatime        0       2
# /dev/sda2
UUID=6a2491d4-6629-454c-aad3-0db187063279 none            swap    sw              0       0
# /dev/sdb2
UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb2
UUID=2947f429-8da2-4c68-acbe-a838ffd4162c /usr            ext3    relatime,errors=remount-ro 0       1

So I need to reboot... how do I make sure it works?  Thats the step that's confusing me.

---

### Post by jocko on 2009-01-24
> **silverbullet007 said:**
> Coppied entire contents of /usr to[COLOR=Red] /media/disk-1/usr/[/COLOR], compared property panes of both, total number of files the same and total size the same.That's wrong. As I said, everything that was in /usr have to be directly in the root of the new partition (/media/disk-1/, NOT /media/disk-1/[COLOR=Red]usr/[/COLOR], as that would result in everything ending up in /usr/[COLOR=Red]usr/[/COLOR] instead of just /usr/ after rebooting with the new fstab)... so move everything from /media/disk-1/usr to /media/disk-1/ before you reboot. Otherwise things will probably go bad... If you have already rebooted you should probably have failed to boot up properly, so boot up a live cd...

> **silverbullet007 said:**
> 
allanon@sputnik:/$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-01-24 13:26 2947f429-8da2-4c68-acbe-a838ffd4162c -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 6a2491d4-6629-454c-aad3-0db187063279 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 7a66d42d-3729-4b6b-a552-7efa25f6ab9b -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-19 20:26 d27c5727-0319-46f4-b3f8-29e488992f04 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-01-24 13:09 f9ad24bc-db09-48d2-9316-95e50ca7c9e2 -> ../../sdb1
allanon@sputnik:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.9G  4.1G  563M  89% /
varrun                1.7G  232K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   76K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1             225G   34G  180G  16% /home
gvfs-fuse-daemon      4.9G  4.1G  563M  89% /home/allanon/.gvfs
/dev/sdb1             214G   53G  152G  26% /media/disk
/dev/sdb2              18G  3.1G   14G  19% /media/disk-1
allanon@sputnik:/$ 


Modified fstab to:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d27c5727-0319-46f4-b3f8-29e488992f04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a66d42d-3729-4b6b-a552-7efa25f6ab9b /home           ext3    relatime        0       2
# /dev/sda2
UUID=6a2491d4-6629-454c-aad3-0db187063279 none            swap    sw              0       0
# /dev/sdb2
UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb2
UUID=2947f429-8da2-4c68-acbe-a838ffd4162c /usr            ext3    relatime,errors=remount-ro 0       1

So I need to reboot... how do I make sure it works?  Thats the step that's confusing me.
As far as I can see the fstab entry should work. Once you have fixed the problem above, you should be able to reboot and see from the output of "mount" or "df -h" that your /dev/sdb2 is mounted as /usr. As long as the directory tree and all file and folder permissions on the /usr partition are exactly the same as in your original /usr folder, everything will work exactly as before. Then you should be able to empty the original /usr folder in your /dev/sda3 partition (but you will only access it from a live cd).

---

### Post by silverbullet007 on 2009-01-24
Sorry I was in a hurry (had the UPS for my blade chassis at work die).  There is no /usr/usr/... the full path to the usr files is /media/disk-1/usr/  thats it.  I verified before posting cause I know that a dbl-usr path would be wrong.

Cool on the rest, I'm going to d/l and burn a new live cd while Im here and give it a whirl tonight.

Thanks for your expert help bro!

[I]allanon@sputnik:/media/disk-1$ ls
lost+found  usr
allanon@sputnik:/media/disk-1$ cd usr
allanon@sputnik:/media/disk-1/usr$ ls
bin  games  include  java  lib  lib32  local  NX  sbin  share  src  X11R6[/I]

---

### Post by jocko on 2009-01-24
> **silverbullet007 said:**
> Sorry I was in a hurry (had the UPS for my blade chassis at work die).  There is no /usr/usr/... the full path to the usr files is /media/disk-1/usr/  thats it.  I verified before posting cause I know that a dbl-usr path would be wrong.

Cool on the rest, I'm going to d/l and burn a new live cd while Im here and give it a whirl tonight.

Thanks for your expert help bro!

[I]allanon@sputnik:/media/disk-1$ ls
lost+found  usr
allanon@sputnik:/media/disk-1$ cd usr
allanon@sputnik:/media/disk-1/usr$ ls
bin  games  include  java  lib  lib32  local  NX  sbin  share  src  X11R6[/I]
That's what's wrong. There should be no /media/disk-1/usr. As the partition will be mounted as /usr, the files and folders from your original /usr directory MUST be DIRECTLY on /media/disk-1, not in a subfolder called /usr. If you have it in /media/disk-1/usr, it will become /usr/usr after rebooting with your new fstab, and that will very likely leave you with an unbootable system.
You should see this:
```
allanon@sputnik:/media/disk-1$ ls
bin  games  include  java  lib  lib32  local  NX  sbin  share  src  X11R6
```NOT this:```
allanon@sputnik:/media/disk-1$ ls
lost+found  usr
```Again: The partition which you now have temporarily mounted as /media/disk-1 should not *contain* the new /usr folder it should *be* the new /usr folder...
**And to avoid one more problem:**
When you boot with a live cd and want to remove the old /usr folder, just remove the contents of the folder but leave it there (or remove it and create a new, empty, /usr folder). It needs to be there as mount point for your new /usr partition.

---

### Post by silverbullet007 on 2009-01-24
Oh crap ok I get you now ;)

so it'd prolly be easier to just del what I've got in /media/disk-1 and recopy. OK I guess I was just misunderstanding what you were typing.  I'll make that change now.

Silly question here.. can I rm the /media/disk-1/usr folder?  It seems only root has access to anything other than viewing the contents.

---

### Post by silverbullet007 on 2009-01-24
Ok just rebooted after copying the contents of /usr to the correct location of /media/disk-1/  however now the other partition of /media/disk is nt mountable.  I get "Error *org.freedesktop.DBus.Error.AccessDenied*"

Now df -h shows:

[I]allanon@sputnik:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             4.9G  4.1G  567M  88% /
varrun                1.7G  220K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G   76K  1.7G   1% /dev
devshm                1.7G   24K  1.7G   1% /dev/shm
lrm                   1.7G   39M  1.6G   3% /lib/modules/2.6.24-23-generic/volatile
/dev/sda1             225G   34G  180G  16% /home
/dev/sdb2              18G  5.8G   11G  35% /usr
gvfs-fuse-daemon      4.9G  4.1G  567M  88% /home/allanon/.gvfs
allanon@sputnik:~$ [/I]

So for some reason that entire drive is not mountable.. and it doesnt show up under the above command.

Did I do something wrong?  There were two partitions on that drive with only the one supposed to be mounted as /usr

---

### Post by silverbullet007 on 2009-01-24
very strange.. now I can't sudo commands.. 

[I]allanon@sputnik:~$ sudo gparted
sudo: must be setuid root
[/I]

---

### Post by silverbullet007 on 2009-01-25
Ok resolved the non-sudo issue by:

Reboot into recovery mode
dropped to a root shell
chown root:root /usr/bin/sudo
chmod 4755 /use/bin/sudo
reboot


Works now.  I still need to figure out what caused the first partition on my /media/disk to become un-mountable and disappear from df -h

---

### Post by silverbullet007 on 2009-01-25
Ok I can forcefully mount sdb1 to /mnt/disk1 (after creating the folder disk1).. But it disappeared as a choice listed under "Computer".

---

### Post by silverbullet007 on 2009-01-25
OK wait.. should my fstab list two entries for teh same device?

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d27c5727-0319-46f4-b3f8-29e488992f04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a66d42d-3729-4b6b-a552-7efa25f6ab9b /home           ext3    relatime        0       2
# /dev/sda2
UUID=6a2491d4-6629-454c-aad3-0db187063279 none            swap    sw              0       0
# /dev/sdb2
UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb2
UUID=2947f429-8da2-4c68-acbe-a838ffd4162c /usr            ext3    relatime,errors=remount-ro 0       1
[/I]

According to both gparted and ls -l /dev/disk/by-uuid, I only have one /sdb2.. and it's not swap.  Its mounted as /usr

allanon@sputnik:/mnt$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 2947f429-8da2-4c68-acbe-a838ffd4162c -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 6a2491d4-6629-454c-aad3-0db187063279 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 7a66d42d-3729-4b6b-a552-7efa25f6ab9b -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 d27c5727-0319-46f4-b3f8-29e488992f04 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-01-24 23:36 f9ad24bc-db09-48d2-9316-95e50ca7c9e2 -> ../../sdb1
allanon@sputnik:/mnt$ 


Could that swap line in fstab be invalid?

---

### Post by jocko on 2009-01-25
> **silverbullet007 said:**
> very strange.. now I can't sudo commands.. 

[I]allanon@sputnik:~$ sudo gparted
sudo: must be setuid root
[/I]

> **silverbullet007 said:**
> Ok resolved the non-sudo issue by:

Reboot into recovery mode
dropped to a root shell
chown root:root /usr/bin/sudo
chmod 4755 /use/bin/sudo
reboot


Works now.  I still need to figure out what caused the first partition on my /media/disk to become un-mountable and disappear from df -h

I'm guessing the mounting problem is the same as the sudo problem. When you copied the /usr folder, you did not preserve the permissions of the files. You probably need to copy the files again with a different method. I noticed that neither nautilus nor the "cp" command will normally preserve group and owner, but I think I've found a way.

1. Boot from a live cd.
2. Open up a terminal and become root (don't close this terminal until you are done with all steps):
```
sudo -i
```
3. Make sure you know which partition is which. Check the output of:
```
ls -la /dev/disk/by-uuid/
```And:```
fdisk -l
```I will give commands that assume /dev/[COLOR=Red]sda3[/COLOR] is your ubuntu / file system and /dev/[COLOR=Blue]sdb2[/COLOR] is your new /usr partition, but remember that this may sometimes be different between boots.
2. Mount your partitions like this (**do NOT use any other method to mount**):
```
mkdir /media/[COLOR=Red]sda3[/COLOR]
mkdir /media/[COLOR=Blue]sdb2[/COLOR]
mount /dev/[COLOR=Red]sda3[/COLOR] /media[COLOR=Red][COLOR=Black]/[/COLOR]sda3[/COLOR]
mount /dev/[COLOR=Blue]sdb2[/COLOR] /media[COLOR=Blue][COLOR=Black]/[/COLOR]sdb2[/COLOR]

```
3. Delete everything in the /[COLOR=Blue]sdb2[/COLOR] partition:
```
rm -rf /media/[COLOR=Blue]sdb2/[/COLOR]*
```
4. Make sure root is the owner of the /sdb2 partition (I think this should already be true, but it won't hurt...):```
chown -R root:root /media[COLOR=Blue]/sdb2/[/COLOR]

```4. Copy everything from the old /usr to the /[COLOR=Blue]sdb2[/COLOR] partition (do NOT use any other method to copy, this is the only one I have found that preserves the group permissions):
```
cp -rv --preserve=all /media/[COLOR=Red]sda3/[/COLOR]usr/* /media/[COLOR=Blue]sdb2/[/COLOR]
```

If you just copy/paste these commands (but possibly changing the [COLOR=Red][COLOR=Black]/[/COLOR]sda3[/COLOR] and /[COLOR=Blue]sda2[/COLOR] if you need to), I think everything should work.

---

### Post by jocko on 2009-01-25
> **silverbullet007 said:**
> OK wait.. should my fstab list two entries for teh same device?

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=d27c5727-0319-46f4-b3f8-29e488992f04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=7a66d42d-3729-4b6b-a552-7efa25f6ab9b /home           ext3    relatime        0       2
# /dev/sda2
UUID=6a2491d4-6629-454c-aad3-0db187063279 none            swap    sw              0       0
# /dev/sdb2
UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb2
UUID=2947f429-8da2-4c68-acbe-a838ffd4162c /usr            ext3    relatime,errors=remount-ro 0       1
[/I]

According to both gparted and ls -l /dev/disk/by-uuid, I only have one /sdb2.. and it's not swap.  Its mounted as /usr

allanon@sputnik:/mnt$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 2947f429-8da2-4c68-acbe-a838ffd4162c -> ../../sdb2
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 6a2491d4-6629-454c-aad3-0db187063279 -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 7a66d42d-3729-4b6b-a552-7efa25f6ab9b -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-01-24 23:26 d27c5727-0319-46f4-b3f8-29e488992f04 -> ../../sda3
lrwxrwxrwx 1 root root 10 2009-01-24 23:36 f9ad24bc-db09-48d2-9316-95e50ca7c9e2 -> ../../sdb1
allanon@sputnik:/mnt$ 


Could that swap line in fstab be invalid?
It is no problem having two lines saying "# /dev/sdb2". That's just comments that does not do anything. The important thing is that the uuid is correct. But I notice that your fstab lists two swap partitions, and the one with UUID=e6b14e94-3e4a-fca6-0a21-a8f8c42c3232 is not listed by your "ls -l /dev/disk/by-uuid". If you only have one swap partition, delete the entry for the second one.

---

### Post by silverbullet007 on 2009-01-25
Awesome.. thanks so much for those instructions.  I followed them and had no problems.  Now I'm back in my usual login.. how do I check to see if my programs are being ran from the new drive?  Or how can I check to see if it's safe to remove the /usr contents?

---

### Post by jocko on 2009-01-26
> **silverbullet007 said:**
> Awesome.. thanks so much for those instructions.  I followed them and had no problems.  Now I'm back in my usual login.. how do I check to see if my programs are being ran from the new drive?  Or how can I check to see if it's safe to remove the /usr contents?

You should see in the output of "mount" or "df -h" that your sdb2 partition is mounted as /usr. If it is, everything should be ok.

---

### Post by silverbullet007 on 2009-01-26
Ok well thats the output Im getting at this time...  Let me ask a silly questions here.  In my mind I was thinking that I could install an app, lets say Gnome-games.  Then go look in the games folder on both /usr and /dev/sdb2/games and see in which folder the games are in to determine which usr folder is actually being used at this time.

---

### Post by jocko on 2009-01-27
> **silverbullet007 said:**
> Ok well thats the output Im getting at this time...  Let me ask a silly questions here.  In my mind I was thinking that I could install an app, lets say Gnome-games.  Then go look in the games folder on both /usr and /dev/sdb2/games and see in which folder the games are in to determine which usr folder is actually being used at this time.
Sure, you can do that (from a live cd). But as long as your /dev/sdb2 is mounted as /usr, there is no way the files in the original /usr folder can be used. Another way you can do it to be really sure nothing is wrong, is to boot up from a live cd and:
```
sudo mkdir /media/sda3
sudo mount /dev/sda3 /media/sda3
sudo mv /media/sda3/usr /media/sda3/usr.bak
sudo mkdir /media/sda3/usr
```
This will rename the original /usr folder and make a new, empty folder which will serve as mount point for the sdb2 partition. When you reboot and see that things are working as they should you can remove the old /usr foder by:
```
sudo rm -rf /usr.bak
```

---

### Post by silverbullet007 on 2009-01-27
Woot! Worked like a champ.  Thanks so much for all your help.  I've already upgraded to Intrepid and ran into the Network Manager bug.

Anyway I learned alot from this so thanks again.

---

### Post by jocko on 2009-01-27
> **silverbullet007 said:**
> Woot! Worked like a champ.  Thanks so much for all your help.  I've already upgraded to Intrepid and ran into the Network Manager bug.

Anyway I learned alot from this so thanks again.
You are welcome! I'm glad I could help.

---

