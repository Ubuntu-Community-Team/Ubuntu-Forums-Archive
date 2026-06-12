---
title: "How to copy files to an Android cell phone"
date: 2020-06-20
forum: Hardware
---

### Post by robertcull1 on 2020-06-20
I can copy files from the cell phone with this command:


```
$ cp /run/user/$UID/gvfs/mtp*/Phone/Download/file /home/robert/Desktop

```

I can make a directory with "mkdir", if I change to that directory:

```
$ cd [COLOR=#000000][FONT=&amp]/run/user/$UID/gvfs/mtp*/Phone/Download[/FONT][/COLOR]
$ ls
temp.txt
$ mkdir temp
$ ls
temp temp.txt

```

I can delete a directory:

```
$ rmdir temp
$ ls
temp.txt
$

```

And I can delete a file:

```
$ rm temp.txt
$ ls
$

```

But I can't copy files to the cell phone with this command:


```
$ cp /home/robert/Desktop/file /run/user/$UID/gvfs/mtp*/Phone/Download
cp: failed to access '/run/user/1000/gvfs/mtp:host=%5Busb%3A001%2C004%5D/Phone/Download': Permission denied

```

Can someone please help?

---

### Post by TheFu on 2020-06-20
Don't use the mtp protocol if you want to use cli. it isn't a real mount. Most Linux file managers can use MTP to copy files over but it is usually slow. With a USB connection, you can use adb.  adb is handy for all sorts of things, like backing up the phone and data.  adb push/pull/sync/backup

Are you network connected or USB connected?  Normal network protocols can be used. Just setup the server on the android device if that is the way you want to handle it.  ssh, rsync, scp, sftp can all be used.

There are other tools that do screen sharing and transfers - KDE-Connect or GSConnect or scrscp (a snap package). [https://github.com/KDE/kdeconnect-android](https://github.com/KDE/kdeconnect-android) [https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect](https://www.omgubuntu.co.uk/2018/11/connect-android-ubuntu-gsconnect) [https://github.com/Genymobile/scrcpy](https://github.com/Genymobile/scrcpy)

And there are intermediate server/cloudy things that can be used like nextcloud, owncloud, seafile, and the big privacy-sucking offers from google, msft, dropbox, and others.  These aren't push - they are pull or sync.  

Or just pull the microSD storage out, connect it to the PC and use local copies, then put it back into the phone/tablet.

---

### Post by robertcull1 on 2020-06-21
Is there a simple how-to for adb?

---

### Post by webaake on 2020-06-21
Set up samba share on your PC and install a file manager on your Android. CX File Explorer works fine for me on my Android, but there are others as well.

The ADB approach is cumbersome compared to setting up a samba share.

---

### Post by T6&amp;sfpER35% on 2020-06-21
i just connect my phone (huawei p8 lite) with usb ,swipe down on phone and select files .
i can move,paste ,copy ,delete,rename ect. anything.
pc to phone or phone to pc ,doesn't matter.

---

### Post by TheFu on 2020-06-21
> **webaake said:**
> Set up samba share on your PC and install a file manager on your Android. CX File Explorer works fine for me on my Android, but there are others as well.

The ADB approach is cumbersome compared to setting up a samba share.

I believe the OP wants to script stuff, not point-n-click.  adb is very scriptable, especially if using a "sync".

The simple adb help is in the manpages installed on your box.  [http://manpages.ubuntu.com/manpages/focal/man1/adb.1.html](http://manpages.ubuntu.com/manpages/focal/man1/adb.1.html) is a copy, but may become out of date compared to the actual manpage on the system which gets installed with every adb update. Some setup is necessary to use adb, like the device needs to be in developer mode and has to be unlocked and given permission to allow access over USB/network.

Samba stopped working for me from Android due to recent changes in the samba defaults on Ubuntu. Some of the apps use a very old samba-NT implementation that has next to zero security. The samba guys have finally made that support non-default.  I only spent about 20 minutes trying to solve it, but failed.  I use other methods 99% of the time anyways.

---

### Post by siepo on 2020-06-23
You can also build a fuse filesystem on top of adb; see [https://github.com/spion/adbfs-rootless]("https://github.com/spion/adbfs-rootless") . This way you can properly mount your cell phone.

---

