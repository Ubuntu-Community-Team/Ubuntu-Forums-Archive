---
title: "ICEautohity?"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by bmenge on 2009-07-05
I just upgraded to 8.10 and got this error while booting. 

could not update /home/brian/.ICEauthority

as well as

Problem with configurations server
(/usr/libgconf2-4/gconf-sanity-check-2 exited with status 256)

This causes the system to hang with no results, indefinitely.  

Any ideas?

I am running off of a live cd now hoping to find a fix.

---

### Post by taurus on 2009-07-05
Mount the partition where / is (or /home if you have a separate /home partition).  Then, have a look at the permissions/ownership of /home/brian/.ICEauthority.

```

ls -la /mnt/ubuntu/home/brian/.ICEauthority
```
Assuming you have mounted the partition to /mnt/ubuntu.

---

### Post by izizzle on 2009-07-05
Boot into a shell prompt and do the following:

run the following command: ```
sudo chown brian:brian /home/brian/.ICEauthority
```

then run ```
sudo reboot
```

I think this should fix it.

---

### Post by bmenge on 2009-07-05
Is this what I need to be looking at?

```
ubuntu@ubuntu:~$ sudo ls -la /media/disk-1/home/brian/.ICEauthority
-rw------- 1 1000 1000 6954 2009-07-05 19:26 /media/disk-1/home/brian/.ICEauthority

```

---

### Post by bmenge on 2009-07-05
Izizzle I tried that earlier and that made no change

---

### Post by taurus on 2009-07-05
How about

```
ls -la /media/disk-1/home/brian
```

---

### Post by bmenge on 2009-07-05
```
ubuntu@ubuntu:/media/disk-1/home$ ls -la /media/disk-1/home/brian
ls: cannot access /media/disk-1/home/brian/.: Permission denied
ls: cannot access /media/disk-1/home/brian/..: Permission denied
ls: cannot access /media/disk-1/home/brian/.ssh: Permission denied
ls: cannot access /media/disk-1/home/brian/smallgrassvalley.jpeg: Permission denied
ls: cannot access /media/disk-1/home/brian/.update-manager-core: Permission denied
ls: cannot access /media/disk-1/home/brian/Examples: Permission denied
ls: cannot access /media/disk-1/home/brian/.lgames: Permission denied
ls: cannot access /media/disk-1/home/brian/.themes: Permission denied
ls: cannot access /media/disk-1/home/brian/.gimp-2.4: Permission denied
ls: cannot access /media/disk-1/home/brian/grassvalleyview.jpeg: Permission denied
ls: cannot access /media/disk-1/home/brian/.mozilla: Permission denied
ls: cannot access /media/disk-1/home/brian/grassvalleyview.xcf: Permission denied
ls: cannot access /media/disk-1/home/brian/flower.tiff: Permission denied
ls: cannot access /media/disk-1/home/brian/.kino-history: Permission denied
ls: cannot access /media/disk-1/home/brian/.update-notifier: Permission denied
ls: cannot access /media/disk-1/home/brian/.nautilus: Permission denied
ls: cannot access /media/disk-1/home/brian/.devede: Permission denied
ls: cannot access /media/disk-1/home/brian/grassvalleyview.tiff: Permission denied
ls: cannot access /media/disk-1/home/brian/.kinorc: Permission denied
ls: cannot access /media/disk-1/home/brian/PCB.00006743.backup: Permission denied
ls: cannot access /media/disk-1/home/brian/.esd_auth: Permission denied
ls: cannot access /media/disk-1/home/brian/.cups: Permission denied
ls: cannot access /media/disk-1/home/brian/desktopbackround.jpeg: Permission denied
ls: cannot access /media/disk-1/home/brian/.amsn: Permission denied
ls: cannot access /media/disk-1/home/brian/.turboprint: Permission denied
ls: cannot access /media/disk-1/home/brian/.spumux: Permission denied
ls: cannot access /media/disk-1/home/brian/.bash_history: Permission denied
ls: cannot access /media/disk-1/home/brian/.blender: Permission denied
ls: cannot access /media/disk-1/home/brian/.unlimitedftp: Permission denied
ls: cannot access /media/disk-1/home/brian/.mcoprc: Permission denied
ls: cannot access /media/disk-1/home/brian/.macromedia: Permission denied
ls: cannot access /media/disk-1/home/brian/Desktop: Permission denied
ls: cannot access /media/disk-1/home/brian/.galeon: Permission denied
ls: cannot access /media/disk-1/home/brian/.qt: Permission denied
ls: cannot access /media/disk-1/home/brian/.java: Permission denied
ls: cannot access /media/disk-1/home/brian/.tomboy.log: Permission denied
ls: cannot access /media/disk-1/home/brian/.metacity: Permission denied
ls: cannot access /media/disk-1/home/brian/.gconf: Permission denied
ls: cannot access /media/disk-1/home/brian/.openoffice.org2: Permission denied
ls: cannot access /media/disk-1/home/brian/.picasa: Permission denied
ls: cannot access /media/disk-1/home/brian/.gvfs: Permission denied
ls: cannot access /media/disk-1/home/brian/.vectoroids-state: Permission denied
ls: cannot access /media/disk-1/home/brian/.loki: Permission denied
ls: cannot access /media/disk-1/home/brian/.eclipse: Permission denied
ls: cannot access /media/disk-1/home/brian/.mplayer: Permission denied
ls: cannot access /media/disk-1/home/brian/.gphoto: Permission denied
ls: cannot access /media/disk-1/home/brian/.icons: Permission denied
ls: cannot access /media/disk-1/home/brian/.kchmviewer: Permission denied
ls: cannot access /media/disk-1/home/brian/.pulse: Permission denied
ls: cannot access /media/disk-1/home/brian/.realsoft: Permission denied
ls: cannot access /media/disk-1/home/brian/.wapi: Permission denied
ls: cannot access /media/disk-1/home/brian/Alice: Permission denied
ls: cannot access /media/disk-1/home/brian/.crossword.cfg: Permission denied
ls: cannot access /media/disk-1/home/brian/.xsession-errors: Permission denied
ls: cannot access /media/disk-1/home/brian/.xwelltris: Permission denied
ls: cannot access /media/disk-1/home/brian/Documents: Permission denied
ls: cannot access /media/disk-1/home/brian/.gnome: Permission denied
ls: cannot access /media/disk-1/home/brian/.gconfd: Permission denied
ls: cannot access /media/disk-1/home/brian/.googleearth: Permission denied
ls: cannot access /media/disk-1/home/brian/.local: Permission denied
ls: cannot access /media/disk-1/home/brian/.pulse-cookie: Permission denied
ls: cannot access /media/disk-1/home/brian/splist.txt: Permission denied
ls: cannot access /media/disk-1/home/brian/.transmission: Permission denied
ls: cannot access /media/disk-1/home/brian/desktopbackround.xcf: Permission denied
ls: cannot access /media/disk-1/home/brian/.dbus: Permission denied
ls: cannot access /media/disk-1/home/brian/.gnome2: Permission denied
ls: cannot access /media/disk-1/home/brian/.adobe: Permission denied
ls: cannot access /media/disk-1/home/brian/.gnome2_private: Permission denied
ls: cannot access /media/disk-1/home/brian/.gksu.lock: Permission denied
ls: cannot access /media/disk-1/home/brian/.cache: Permission denied
ls: cannot access /media/disk-1/home/brian/.ICEauthority: Permission denied
ls: cannot access /media/disk-1/home/brian/.kompozer: Permission denied
ls: cannot access /media/disk-1/home/brian/Pictures: Permission denied
ls: cannot access /media/disk-1/home/brian/.fontconfig: Permission denied
ls: cannot access /media/disk-1/home/brian/.tomboy: Permission denied
ls: cannot access /media/disk-1/home/brian/.gnupg: Permission denied
ls: cannot access /media/disk-1/home/brian/pytrainer-1.5: Permission denied
ls: cannot access /media/disk-1/home/brian/.VirtualBox: Permission denied
ls: cannot access /media/disk-1/home/brian/.atrisrc: Permission denied
ls: cannot access /media/disk-1/home/brian/.kde: Permission denied
ls: cannot access /media/disk-1/home/brian/Music: Permission denied
ls: cannot access /media/disk-1/home/brian/amsn_received: Permission denied
ls: cannot access /media/disk-1/home/brian/.config: Permission denied
ls: cannot access /media/disk-1/home/brian/.recently-used: Permission denied
ls: cannot access /media/disk-1/home/brian/PCB.00006754.backup: Permission denied
ls: cannot access /media/disk-1/home/brian/.recently-used.xbel: Permission denied
ls: cannot access /media/disk-1/home/brian/f4l-0.2: Permission denied
ls: cannot access /media/disk-1/home/brian/googleearth: Permission denied
ls: cannot access /media/disk-1/home/brian/google-earth: Permission denied
ls: cannot access /media/disk-1/home/brian/get_photots: Permission denied
ls: cannot access /media/disk-1/home/brian/.wine: Permission denied
ls: cannot access /media/disk-1/home/brian/.sudo_as_admin_successful: Permission denied
ls: cannot access /media/disk-1/home/brian/.hugin: Permission denied
ls: cannot access /media/disk-1/home/brian/Templates: Permission denied
ls: cannot access /media/disk-1/home/brian/.gtk-bookmarks: Permission denied
ls: cannot access /media/disk-1/home/brian/.thumbnails: Permission denied
ls: cannot access /media/disk-1/home/brian/.gstreamer-0.10: Permission denied
ls: cannot access /media/disk-1/home/brian/.evolution: Permission denied
ls: cannot access /media/disk-1/home/brian/sunrise: Permission denied
ls: cannot access /media/disk-1/home/brian/.mcop: Permission denied
ls: cannot access /media/disk-1/home/brian/.pokerth: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? .adobe
d????????? ? ? ? ?                ? Alice
d????????? ? ? ? ?                ? .amsn
d????????? ? ? ? ?                ? amsn_received
-????????? ? ? ? ?                ? .atrisrc
-????????? ? ? ? ?                ? .bash_history
d????????? ? ? ? ?                ? .blender
d????????? ? ? ? ?                ? .cache
d????????? ? ? ? ?                ? .config
-????????? ? ? ? ?                ? .crossword.cfg
d????????? ? ? ? ?                ? .cups
d????????? ? ? ? ?                ? .dbus
d????????? ? ? ? ?                ? Desktop
-????????? ? ? ? ?                ? desktopbackround.jpeg
-????????? ? ? ? ?                ? desktopbackround.xcf
-????????? ? ? ? ?                ? .devede
d????????? ? ? ? ?                ? Documents
d????????? ? ? ? ?                ? .eclipse
-????????? ? ? ? ?                ? .esd_auth
d????????? ? ? ? ?                ? .evolution
l????????? ? ? ? ?                ? Examples
d????????? ? ? ? ?                ? f4l-0.2
-????????? ? ? ? ?                ? flower.tiff
d????????? ? ? ? ?                ? .fontconfig
d????????? ? ? ? ?                ? .galeon
d????????? ? ? ? ?                ? .gconf
d????????? ? ? ? ?                ? .gconfd
-????????? ? ? ? ?                ? get_photots
d????????? ? ? ? ?                ? .gimp-2.4
-????????? ? ? ? ?                ? .gksu.lock
d????????? ? ? ? ?                ? .gnome
d????????? ? ? ? ?                ? .gnome2
d????????? ? ? ? ?                ? .gnome2_private
d????????? ? ? ? ?                ? .gnupg
l????????? ? ? ? ?                ? googleearth
d????????? ? ? ? ?                ? .googleearth
d????????? ? ? ? ?                ? google-earth
d????????? ? ? ? ?                ? .gphoto
-????????? ? ? ? ?                ? grassvalleyview.jpeg
-????????? ? ? ? ?                ? grassvalleyview.tiff
-????????? ? ? ? ?                ? grassvalleyview.xcf
d????????? ? ? ? ?                ? .gstreamer-0.10
-????????? ? ? ? ?                ? .gtk-bookmarks
d????????? ? ? ? ?                ? .gvfs
-????????? ? ? ? ?                ? .hugin
-????????? ? ? ? ?                ? .ICEauthority
d????????? ? ? ? ?                ? .icons
d????????? ? ? ? ?                ? .java
d????????? ? ? ? ?                ? .kchmviewer
d????????? ? ? ? ?                ? .kde
d????????? ? ? ? ?                ? .kino-history
-????????? ? ? ? ?                ? .kinorc
d????????? ? ? ? ?                ? .kompozer
d????????? ? ? ? ?                ? .lgames
d????????? ? ? ? ?                ? .local
d????????? ? ? ? ?                ? .loki
d????????? ? ? ? ?                ? .macromedia
d????????? ? ? ? ?                ? .mcop
-????????? ? ? ? ?                ? .mcoprc
d????????? ? ? ? ?                ? .metacity
d????????? ? ? ? ?                ? .mozilla
d????????? ? ? ? ?                ? .mplayer
d????????? ? ? ? ?                ? Music
d????????? ? ? ? ?                ? .nautilus
d????????? ? ? ? ?                ? .openoffice.org2
-????????? ? ? ? ?                ? PCB.00006743.backup
-????????? ? ? ? ?                ? PCB.00006754.backup
d????????? ? ? ? ?                ? .picasa
d????????? ? ? ? ?                ? Pictures
d????????? ? ? ? ?                ? .pokerth
d????????? ? ? ? ?                ? .pulse
-????????? ? ? ? ?                ? .pulse-cookie
d????????? ? ? ? ?                ? pytrainer-1.5
d????????? ? ? ? ?                ? .qt
d????????? ? ? ? ?                ? .realsoft
-????????? ? ? ? ?                ? .recently-used
-????????? ? ? ? ?                ? .recently-used.xbel
-????????? ? ? ? ?                ? smallgrassvalley.jpeg
-????????? ? ? ? ?                ? splist.txt
d????????? ? ? ? ?                ? .spumux
d????????? ? ? ? ?                ? .ssh
-????????? ? ? ? ?                ? .sudo_as_admin_successful
d????????? ? ? ? ?                ? sunrise
d????????? ? ? ? ?                ? Templates
d????????? ? ? ? ?                ? .themes
d????????? ? ? ? ?                ? .thumbnails
d????????? ? ? ? ?                ? .tomboy
-????????? ? ? ? ?                ? .tomboy.log
d????????? ? ? ? ?                ? .transmission
d????????? ? ? ? ?                ? .turboprint
d????????? ? ? ? ?                ? .unlimitedftp
d????????? ? ? ? ?                ? .update-manager-core
d????????? ? ? ? ?                ? .update-notifier
-????????? ? ? ? ?                ? .vectoroids-state
d????????? ? ? ? ?                ? .VirtualBox
d????????? ? ? ? ?                ? .wapi
d????????? ? ? ? ?                ? .wine
-????????? ? ? ? ?                ? .xsession-errors
d????????? ? ? ? ?                ? .xwelltris
ubuntu@ubuntu:/media/disk-1/home$ 


```

---

### Post by taurus on 2009-07-05
Which release did you run before you upgraded to 8.10?  

What are the outputs of these commands?

```
sudo /media/disk-1/etc/fstab
df -h
ls -la /media/disk-1/home
```

---

### Post by bmenge on 2009-07-05
I will run those now I had this problem that never got resolved[http://ubuntuforums.org/showthread.php?t=965584]("http://ubuntuforums.org/showthread.php?t=965584")

I just ignored it and hit ok, I am guessing now that I should have taken care of it before I upgraded.  

```
ubuntu@ubuntu:/media/disk-1/home$ sudo /etc/fstab
sudo: /etc/fstab: command not found

```

```
ubuntu@ubuntu:/media/disk-1/home$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.3G   17M  1.3G   2% /lib/modules/2.6.24-19-generic/volatile
tmpfs                 1.3G   17M  1.3G   2% /lib/modules/2.6.24-19-generic/volatile
varrun                1.3G  100K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G   80K  1.3G   1% /dev
devshm                1.3G   52K  1.3G   1% /dev/shm
tmpfs                 1.3G   16K  1.3G   1% /tmp
gvfs-fuse-daemon      1.3G   21M  1.3G   2% /home/ubuntu/.gvfs
/dev/sdb1              28G  318M   27G   2% /media/disk
/dev/sda3              15G   13G  1.5G  90% /media/disk-1
/dev/sda1              13G   13G  455M  97% /media/disk-2
/dev/sda7              39G   28G  9.7G  74% /media/disk-3
/dev/sda6             3.9G   72M  3.6G   2% /media/disk-4

```

```
ubuntu@ubuntu:/media/disk-1/home$ ls -la /media/disk-1/home
total 20
drwxr-xr-x  3 root root  4096 2008-07-26 17:22 .
drwxrwxrwx 24 root root  4096 2009-07-05 19:13 ..
drw-r--r-- 70 1000 1000 12288 2009-07-05 19:27 brian

```

I am not sure if it was 8.04 that I was running, or not I think it was.

---

### Post by taurus on 2009-07-05
```
sudo fdisk -l
cat /media/disk-1/etc/fstab
```
And by the way, your $HOME, /home/brian, should have an executable if you want to change to it.  As of right now, you can't.

> **[COLOR="Red"]drw-[/COLOR]**r--r-- 70 1000 1000 12288 2009-07-05 19:27 brian

```
sudo chmod 744 /media/disk-1/home/brian
ls -la /media/disk-1/home
```

---

### Post by bmenge on 2009-07-05
```
 sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc772c772

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1657    13309821    7  HPFS/NTFS
/dev/sda2            1658        1912     2048287+   b  W95 FAT32
/dev/sda3            1913        3824    15358140   83  Linux
/dev/sda4            3825        9729    47431912+   5  Extended
/dev/sda5            3825        4079     2048256   82  Linux swap / Solaris
/dev/sda6            4080        4589     4096543+  83  Linux
/dev/sda7            4590        9729    41287018+  83  Linux

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52226094

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3649    29310561    7  HPFS/NTFS
```

was "cat /media/disk-1/etc/fdisk" a command you wanted me to check?

```
cat /media/disk-1/etc/fdisk
cat: /media/disk-1/etc/fdisk: No such file or directory

```

```
ubuntu@ubuntu:/media/disk-1$ sudo chmod 744 /media/disk-1/home/brian
ubuntu@ubuntu:/media/disk-1$ ls -la /media/disk-1/home
ls: cannot access /media/disk-1/home/.: Permission denied
ls: cannot access /media/disk-1/home/..: Permission denied
ls: cannot access /media/disk-1/home/brian: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
d????????? ? ? ? ?                ? brian
ubuntu@ubuntu:/media/disk-1$ sudo ls -la /media/disk-1/home
total 20
drwxr--r--  3 root root  4096 2008-07-26 17:22 .
drwxrwxrwx 24 root root  4096 2009-07-05 22:10 ..
drwxr--r-- 70 1000 1000 12288 2009-07-05 21:12 brian
```

---

### Post by taurus on 2009-07-05
You don't have an executable to look in /media/disk-1/home/brian since you are currently logged in as ubuntu, not brian.  Reboot (from the harddrive) and see what happens when you log in as brian?

---

### Post by bmenge on 2009-07-05
ok so I got to the log in screen and got an error message.

"Your home directory is listed as '/home/brian'
but it does not appear to exist.  Do you want 
to log in with the /(root) directory as your home
directory?  Its is unlikely anything will work 
unless you use failsafe session."

both yes and no as responses, 

Yes got me no where the first time, then I rebooted and tried no.  I was given the option to log in when clicking no and changed to fail safe gnome.  once it started to load it then got hung up again.  I tried a few times with no change.

---

### Post by taurus on 2009-07-05
Boot into recovery mode from GRUB menu and post the outputs of these commands.

```
cat /etc/fstab
tail /etc/passwd
ls -la /home
```

---

### Post by bmenge on 2009-07-05
[IMG]http://i23.photobucket.com/albums/b387/bmenge/img_3608.jpg[/IMG]

[IMG]http://i23.photobucket.com/albums/b387/bmenge/img_3607.jpg[/IMG]

---

### Post by bmenge on 2009-07-07
[IMG]http://i23.photobucket.com/albums/b387/bmenge/img_3609.jpg[/IMG]

---

