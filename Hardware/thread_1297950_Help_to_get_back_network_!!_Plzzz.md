---
title: "Help to get back network !! Plzzz"
date: 2009-10-22
forum: Hardware
---

### Post by Vibin Lakshman on 2009-10-22
I tried to mount my drive , and after that before unmounting I tried to delete the mounted folder , then start these problems
After reboot forcefully

1.Before logging in , pops up a window 
User's $HOME/.dmrc file being ignored. File should be owned by user and have 644 permission , file should be owned by user not others

2. After showing desktop , another window pops up

Failed to apply network settings

org.freedesktop.DBUs.Error.spawn.PermissioInvalid:
The permission of setuid helper isnt correct
You might not be able to connect to bluetooth network via this machine

After that I cant login as root or as sudo . And restart option , shutdown all are absent after these , internet cant get accessed 

Please help me to solve this problem , I browsing thru now Windows(Which I hate):(

---

### Post by Giblet5 on 2009-10-22
Log off.

Flip to the console via CtrlAltF1.

Log in.

Type ```
sudo chown -R _user_:_user_ /home/_user_
exit
``` where _user_ is your login name.

Flip back to the login window via CtrlAltF7.

Log in.

Better? If so, mark this (SOLVED).

---

### Post by Vibin Lakshman on 2009-10-22
No I cant enter my root shell , its showing err
sudo:must be setuid root

What to do ? I cant do it in recovery mode too

---

### Post by Giblet5 on 2009-10-22
> **Vibin Lakshman said:**
> No I cant enter my root shell , its showing err
sudo:must be setuid root

What to do ? I cant do it in recovery mode too


Whoops.

Did you try to move this stuff to a FAT32 or NTFS drive? It's acting like all the permissions are wrong. You didn't explain clearly what you were trying to do, nor what you did do...


Boot from a LiveCD in "Try it" mode.

Open a terminal window.

Type in: ```
sudo fdisk -l
```

One of the listed partions will be "ext3". Make note of the device. We'll assume that was "/dev/sda2", but use the correct one...

```
sudo mount /dev/sda2 /mnt -text3
ls -l /mnt/usr/bin/sudo
``` *should* look like: ```
-rwsr-xr-x 2 root root 143656 2009-06-22 12:15 /usr/bin/sudo
```

If the mode and ownership don't match that, you need to backup your data and reinstall Ubuntu.

Do you have a Windows partition? The fdisk command above will have displayed which device that is. Let's assume it was /dev/sda1 and that it's really big.

```
sudo mkdir /mnt2
sudo mount /dev/sda1 /mnt2 -tntfs
cd /mnt
tar cjf /mnt2/emerg-backup.tar.bz2 home
```

That'll take awhile, but you'll have a backup.

Now, reinstall Ubuntu.

Then open a terminal window and mount that Windows partition with the backup on it, and restore the backup: ```
sudo mount /dev/sda1 /mnt -tntfs
cd /
sudo tar xjf /mnt/emerg-backup.tar.bz2
sudo chown -R $LOGNAME:$LOGNAME $HOME
```

That will put you close to where you were...

---

### Post by Vibin Lakshman on 2009-10-22
OK !! Lets see what will it happened , i had formatted my Ubuntu with ext4 , any problem in that , I have sys rescue cd which supports ext4 , hope it will work .

See you Sir after 30- 35 minutes , by the way thanks for the quick replies

---

### Post by Vibin Lakshman on 2009-10-22
The mode and ownership is like
-rwxrwxrwx 1 root root  .... 

Seems like I need to reinstall , right? Hmm.. Is there any other option , I have just did to delete the mounted directory made that into full permission mode , that is /mnt_direc to 777 mode .. Then all started suddenly

---

