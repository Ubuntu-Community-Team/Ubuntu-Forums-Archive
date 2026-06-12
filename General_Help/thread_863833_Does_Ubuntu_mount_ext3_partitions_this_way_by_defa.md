---
title: "Does Ubuntu mount ext3 partitions this way by default?"
date: 2008-07-18
forum: General Help
---

### Post by plamen_todoroff on 2008-07-18
havoque@aspire-s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=104bb2df-a926-45b4-b756-715b06577e41 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=37a6ab9b-0c8e-454f-9eab-8d0153b17c3d /boot           ext3    relatime        0       2
# /dev/sda7
UUID=5bb507e7-812e-4f39-8da7-375ccc159862 /home           ext3    relatime        0       2
# /dev/sda12
UUID=920AE0BD0AE09F89 /media/alpha    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=6082994082991C1A /media/arcade   ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda13
UUID=34C2F179C2F13FA2 /media/betta    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=61e2abac-cf42-4ded-b819-7d70b73f8220 /media/boottest ext3    relatime        0       2
# /dev/sda15
UUID=4EE81322E81307BB /media/delta    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda14
UUID=4096027896026EAA /media/gamma    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda11
UUID=943b3de3-bbd5-4b6c-aad9-630b5dbc9192 /media/hometest ext3    relatime        0       2
# /dev/sda2
UUID=3434C68334C64816 /media/longhorn ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=8A2AFC19E49BED2A /media/pqservice ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda10
UUID=329cf29f-4b9d-4a5d-80b3-bc0a77d1f426 /media/roottest ext3    relatime        0       2
# /dev/sda8
UUID=832c67fc-f4d0-49a4-9bdf-4fae1182c2f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#downwards added by me...
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
havoque@aspire-s:~$ 

--------------------------------------------------------------------------

havoque@aspire-s:~$ sudo fdisk -l
[sudo] password for havoque: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x74544c10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275        9629    67111537+   7  HPFS/NTFS
/dev/sda3            9630       29977   163445310    5  Extended
/dev/sda4           29978       30402     3399680   12  Compaq diagnostics
/dev/sda5            9630        9760     1052226   83  Linux
/dev/sda6            9761       12110    18876343+  83  Linux
/dev/sda7           12111       15765    29358756   83  Linux
/dev/sda8           15766       16026     2096451   82  Linux swap / Solaris
/dev/sda9           16027       16157     1052226   83  Linux
/dev/sda10          16158       18507    18876343+  83  Linux
/dev/sda11          18508       19812    10482381   83  Linux
/dev/sda12          19813       22423    20972826    7  HPFS/NTFS
/dev/sda13          22424       25034    20972826    7  HPFS/NTFS
/dev/sda14          25035       27645    20972826    7  HPFS/NTFS
/dev/sda15          27646       29977    18731758+   7  HPFS/NTFS
havoque@aspire-s:~$ 

---------------------------------------------------------------------

havoque@aspire-s:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 104bb2df-a926-45b4-b756-715b06577e41 -> ../../sda6
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 329cf29f-4b9d-4a5d-80b3-bc0a77d1f426 -> ../../sda10
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 3434C68334C64816 -> ../../sda2
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 34C2F179C2F13FA2 -> ../../sda13
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 37a6ab9b-0c8e-454f-9eab-8d0153b17c3d -> ../../sda5
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 4096027896026EAA -> ../../sda14
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 4EE81322E81307BB -> ../../sda15
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 5bb507e7-812e-4f39-8da7-375ccc159862 -> ../../sda7
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 6082994082991C1A -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 61e2abac-cf42-4ded-b819-7d70b73f8220 -> ../../sda9
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 832c67fc-f4d0-49a4-9bdf-4fae1182c2f0 -> ../../sda8
lrwxrwxrwx 1 root root 10 2008-07-18 07:06 8A2AFC19E49BED2A -> ../../sda1
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 920AE0BD0AE09F89 -> ../../sda12
lrwxrwxrwx 1 root root 11 2008-07-18 07:06 943b3de3-bbd5-4b6c-aad9-630b5dbc9192 -> ../../sda11
havoque@aspire-s:~$ 

------------------------------------------------------

This is almost untouched clean Ubuntu 8.04 installation. While installing I chose the advanced partitioning option and mounted all my partitions manually. All mounted to /media/*some-partition-name*. I'm not talking about /boot, / & /home here. 

sda 9,10 and 11 are ext3 partitions that I made with gparted livecd before installing Ubuntu (for testing other distros). These partitions have mountpoints /media/boottest, /media/roottest & /media/hometest.

I can read/write to the ntfs partitions w/o problems. The problem is that I recently found that I can't create a folder or write a file on these 3 ext3 partitions (I decided to use them for storage now, not for testing).

I checked the permissions of all the mount points in /media (including the ntfs ones) and they are all owned by root. The difference between the ext3 ones and the ntfs ones is the *Group* permissions (see attachments).

Before installing Ubuntu I thought that I would be having ntfs connected problems but it seems to be the opposite. **Does Ubuntu mount ext3 partitions this way by default?** I doubt that I have done something wrong after installation, because I haven't touched anything partition-related post-install.

I hope my English is not so bad. If you really are willing to help, I'll post any info you want.

For all you others, please don't ruine this thread with "Why do you need so much partitions?" questions.

Thanks.

---

### Post by logos34 on 2008-07-18
Run these two commands for sda9-11 (for 'user' use your own and change mount point)

> sudo chown -R user:user /media/boottest
sudo chmod -R 755 /media/boottest

---

### Post by plamen_todoroff on 2008-07-18
Thank you for the quick reply, but I still didn't get it if this is Ubuntu's default behaviour or the problem is in my system.

If Ubuntu does that by default, wouldn't running these two commands compromize the default Ubuntu security policy? I guess, if this is the default action for mounting ext3 partitions, the Ubuntu developers had done it so for some reason?

Why this doesn't affect ntfs partitions? They are absolutely usable right after installation.

---

### Post by mc4man on 2008-07-18
You may see the difference between ntfs and ext.3 a little more clearly if in properties look under the volume tab.
The default 'behavior' i like is when you don't mount your add. partitions at boot, just as needed. Then you can use Authorizations to give yourself (and/or others)  full read, write ,mount and unmount permissions.(or block) It's a one time step with option to remember authentication (no password) or not (password every time). Very well set up and simple. See screenshot


Edit: there are some other very interesting parts in Authorizations and there does seem some room for 'growth' there down the line

---

### Post by logos34 on 2008-07-19
I believe that they should be mounting at boot with full rw access ('defaults'), since you created them before installation, and they're included in in fstab.  So I would say no, this is not normal behavior.  But it's perfectly safe to run those commands

---

### Post by plamen_todoroff on 2008-07-19
Thank you, guys.

But all this rises another question. What could have gone wrong that I had those ext3 partitions mounted that way?

As a read the forums it seems that a lot of members have similar issues with ext3 partitions.

---

### Post by plamen_todoroff on 2008-07-19
I'm really really sorry for posting again so soon, but I'm in a hurry and really need to know what have gone wrong. Also what the 755 number will do exactly? And for *user* I should use the login name or just the name (see attachment)?

Can't I just change some options in *fstab* and add the "*defaults*" parameter to the ext3 lines (obviously it's missing), or is it just for ntfs ones?

---

### Post by logos34 on 2008-07-19
here's part of mine:

> # /dev/sda6
UUID=92e1dc9c-0758-408a-873b-48ba419e8e88 /home ext3 relatime 0 2
# /dev/sda5
UUID=b27dd180-0abb-432d-a090-993ce0e5e72a /media/hda5 ext3 defaults 0 2Don't add it, just replace 'relatime' with 'defaults' (= rw, suid, dev, exec, auto, nouser, async)

[http://www.tuxfiles.org/linuxhelp/fstab.html#four](http://www.tuxfiles.org/linuxhelp/fstab.html#four)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by bodhi.zazen on 2008-07-19
Actually you should leave "relatime" , it improves performance.

Just add in the settings you want.

For linux native file systems, mount the partition, then use chmod and chown

```
sudo chown user.user /mount/point
sudo chmod 770 /mount/point
```

This is a one-time configuration :)

---

### Post by plamen_todoroff on 2008-07-20
There are quite different parts in the codes you guys wrote, also the spelling is different, and the numbers...

I'm not sure which lines of code to enter in the terminal, the bodhi.zazen's or logos34's. I'm not sure what to enter for *user*. Did you see my attachment from the last post?

I thought that I'll need to change the permissions, or fstab. And now bodhi.zazen says to add the settings in fstab, and to change permissions afterwards?

I'm lost. Help. Explain... I don't feel confortable just entering something in terminal that I don't understand. Why do the numbers in your commands differ?

---

### Post by dcstar on 2008-07-20
> **plamen_todoroff said:**
> 
........
sda 9,10 and 11 are ext3 partitions that I made with gparted livecd before installing Ubuntu (for testing other distros). These partitions have mountpoints **/media**/boottest, **/media**/roottest & **/media**/hometest.

I can read/write to the ntfs partitions w/o problems. The problem is that I recently found that I can't create a folder or write a file on these 3 ext3 partitions (I decided to use them for storage now, not for testing).
.......


The "problem" may be that you are mounting these partitions in a Ubuntu system use directory - /media. This is where Ubuntu creates its own mount points for detected external hardware by the HAL and probably isn't really intended for users to start adding in their own in there.

If you created mount points and mounted these somewhere in your own user tree then it may well work better.

---

### Post by logos34 on 2008-07-20
> **plamen_todoroff said:**
> There are quite different parts in the codes you guys wrote, also the spelling is different, and the numbers...

I'm not sure which lines of code to enter in the terminal, the bodhi.zazen's or logos34's. I'm not sure what to enter for *user*. Did you see my attachment from the last post?

I thought that I'll need to change the permissions, or fstab. And now bodhi.zazen says to add the settings in fstab, and to change permissions afterwards?


> **bodhi.zazen said:**
> 
```
sudo chown [COLOR=Red]user.user[/COLOR] /mount/point
sudo chmod 770 /mount/point
```

The period '.' is a typo; should be a colon.  You can certainly use 77**0** instead--'0' if you want to completely shut out any other users from even read and execute access.

So if your username is 'havoque', try either 

>  			 				sudo chown -R [COLOR=Blue]havoque[/COLOR][COLOR=Blue]:havoque[/COLOR] /media/boottest 
sudo chmod -R 755 /media/boottest
('755'=  the owner/user 'havoque' has -rwx- (read+write+execute) access; group and others r-x only)

or

sudo chmod -R 770 /media/boottest 
(user and group -rwx- access; others none)


Get as fancy as you want with the options in fstab.  Just a simple relatime or defaults works fine for me.  (there a small performance gain with it, like bodhi.zazen says, which is why I adopted it (along with noatime) back in feisty, after having read [this article]("http://lwn.net/Articles/244829/").  It's now standard.

---

### Post by bodhi.zazen on 2008-07-20
> **logos34 said:**
> The period '.' is a typo; should be a colon.

Although I make my share of typos, in this case the . is not a typo, try it out :lolflag::

user.group is easier to type then user:group :twisted:

---

### Post by plamen_todoroff on 2008-07-20
Oooook, so one final question before entering the codes.

I decided not to change anything in fstab because Ubuntu already had put the *relatime* parameter in there (I'd like not to mess with the *defaults*).

From all your answers about permissions I think I want me and group to have rwx, and others to have r-x. So I guess the number has to be 775?

What will the group name be according to your lines of code, will it be *havoque* (user:user = havoque:havoque, havoque is the owner, and havoque is the group?) Because I looked under System/Administration/Users & Groups and it seems that I'm NOT a member of the group "*havoque*"!

I looked at the ntfs partitions properties (I don't have any problems with them) and their owner is *root*, but the group is *plugdev*. I looked under System/Administration/Users & Groups again and there is no a "*plugdev*" group there!

What's going on? Seems that for ntfs partitions some non-existent group called *plugdev* has rwx and they work fine.

Shouldn't I assign the ext3 partitions to the *plugdev* group, not to group *havoque*? The lines will become something like that:

```
sudo chown -R root:plugdev /media/boottest
sudo chmod -R 775 /media/boottest
```

Thus all partitions (ntfs and ext3) will remain owned by *root*, and ext3s will be assigned to the *plugdev* group (ext3 and ntfs will have the same properties and all will work fine)?

](*,)

Please look againt at the screenshots of both types of partition properties in the screenshots I posted earlier. Won't it just work if I make ext3's properties the same as ntfs's?

---

### Post by logos34 on 2008-07-20
> **bodhi.zazen said:**
> Although I make my share of typos, in this case the . is not a typo, try it out :lolflag::

user.group is easier to type then user:group :twisted:

wow, you're right.  I've never seen that usage, though.

> CHOWN(1)

NAME
       chown - change file owner and group

SYNOPSIS
       chown [OPTION]... [OWNER][:[GROUP]] FILE...
       chown [OPTION]... --reference=RFILE FILE...

---

### Post by bodhi.zazen on 2008-07-20
> **plamen_todoroff said:**
> Oooook, so one final question before entering the codes.

LOL, defaults were ment to be changed :twisted:

Seriously though, back up system files before you edit them. Then use comments to indicate changes you made or original lines (I almost never actually delete anything from system files).

Comments start with a #

> # Original line
# Change mount options
new line

If the defaults are working, no need to change, but if they are not, by all means change away. The changes on this thread are easily undone.

To see what groups you belong to, in a terminal type either *id[/i\ or [i]groups*.

I would make the partitions, once mounted, owned by your user and the group "users" (After doing this for a long time I like to be more restrictive with permissions.).

Last , ownership and permissions on fat and ntfs are different, these are set at the time of mounting the partition.

I suggest you look at this link :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

