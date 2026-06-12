---
title: "Unable to Mount Partition"
date: 2010-07-13
forum: Hardware
---

### Post by guy.komaclo on 2010-07-13
[FONT=Arial Narrow][SIZE=3][B]:frown:
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 1 in /etc/fstab is bad
mount: can't find /dev/sda4 in /etc/fstab or /etc/mtab[/B][/SIZE][/FONT]

---

### Post by Morbius1 on 2010-07-13
Why not post the contents of your fstab so we can all see what "Line 1" is. You might want to post the output of another commands as well.

```
cat /etc/fstab
sudo blkid -c /dev/null
```

---

### Post by guy.komaclo on 2010-07-13
thanks for your prompt reply.

I'm still have the same problem

I typed the command and I received the same message.

Here are what appear to the screen when I add the commands you gave 

cat /etc/fstab
UUID=90EEE603EEE5E188 /media/Tsunami Shango_ ntfs-3g remount,dirsync,users,nodev,sync 1 0
UUID=7a11e666-a525-454c-a149-692dd326a0b3 / ext4 defaults 0 1
UUID=f2e98ee6-5cfc-4cf7-a784-bf056478280c swap swap sw 0 0
hurricane@hurricane-laptop:~$ sudo blkid -c /dev/null
[sudo] password for hurricane: 
/dev/sda1: LABEL="Windows" UUID="5E288EA64FC9C6D0" TYPE="ntfs" 
/dev/sda4: LABEL="Tsunami Shango" UUID="90EEE603EEE5E188" TYPE="ntfs" 
/dev/sda5: UUID="7a11e666-a525-454c-a149-692dd326a0b3" TYPE="ext4" 
/dev/sda6: LABEL="Ubuntu Backup" UUID="e6f09905-02d8-48e5-af0f-f0a4dd1b6751" TYPE="ext4" 
/dev/sda7: UUID="f2e98ee6-5cfc-4cf7-a784-bf056478280c" TYPE="swap"

---

### Post by Morbius1 on 2010-07-13
>  /dev/sda4: LABEL="Tsunami Shango" UUID="90EEE603EEE5E188" TYPE="ntfs" > UUID=90EEE603EEE5E188 /media/Tsunami Shango_ ntfs-3g  remount,dirsync,users,nodev,sync 1 0For one thing, you can't have spaces in the mountpoint in fstab. At least not the way you're doing it. Spaces must be represented by "\040" - that's zero - 4 - zero.

So the line should look like this:
```
UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g  remount,dirsync,users,nodev,sync 1 0
```

---

### Post by guy.komaclo on 2010-07-13
I don't know how to modify the line.


> **Morbius1 said:**
> For one thing, you can't have spaces in the mountpoint in fstab. At least not the way you're doing it. Spaces must be represented by "\040" - that's zero - 4 - zero.

So the line should look like this:
```
UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g  remount,dirsync,users,nodev,sync 1 0
```

---

### Post by drs305 on 2010-07-13
You can mount your real / partition via the LiveCD if you are not able to boot to your normal installation.

Boot to the LiveCD desktop, then run these commands:
```
sudo mount /dev/sda5 /mnt
gksu gedit /mnt/etc/fstab
```

You can now edit your fstab file, making the recommended changes. If you aren't sure exactly how to change the line, just put a **#** symbol at the start of the Tsunami line to make it inactive and you can then deal with it once you can boot normally. 

When you are done, save the file, then return to the terminal window and
```
sudo umount /dev/sda5
```
and reboot.

---

### Post by Morbius1 on 2010-07-14
> **guy.komaclo said:**
> I don't know how to modify the line.
Open Terminal and type
```
gksu gedit /etc/fstab
```Find the following line:
                             > UUID=90EEE603EEE5E188 /media/Tsunami Shango_ ntfs-3g   remount,dirsync,users,nodev,sync 1 0                 
And add the \040 so that it looks exactly like this:
> UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g   remount,dirsync,users,nodev,sync 1 0                       [COLOR=Blue]And remember that \040 is a zero - 4 - zero.[/COLOR]

Save the file, exit gedit, and back in the terminal type
```
sudo mount -a
```

---

### Post by drs305 on 2010-07-14
If you are unable to boot you in the newer releases of Ubuntu you should be given the option to press "S" to skip mounting the "bad" partition. If not, the LiveCD method should work to correct fstab.

If you are already running Ubuntu normally when you have the problem, the advice by others on how to fix the fstab setting should work (without the need for the LiveCD).

From a running normal install, you should be able to check whether the setting is now correct by opening a terminal and running the following commands. The first will attempt to umount all fstab-related partitions. You will get "busy" messages for system partitions - that is ok.

The second command will attempt to mount all the partitions listed in fstab (unless designated 'noauto'). If the fstab settings are correct, the partitions will be mounted and there should be no messages after running the command (every partition mounted correctly).
```

sudo umount -a
sudo mount -a
```

---

### Post by guy.komaclo on 2010-07-14
Here are the messages error, I am receiving on my screen

hurricane@hurricane-laptop:~$ sudo umount -a
[sudo] password for hurricane: 
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
hurricane@hurricane-laptop:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad


This is what I found in the fstab file

UUID=90EEE603EEE5E188 /040media/Tsunami Shango_ ntfs-3g remount,dirsync,users,nodev,sync 1 0
UUID=7a11e666-a525-454c-a149-692dd326a0b3 / ext4 defaults 0 1
UUID=f2e98ee6-5cfc-4cf7-a784-bf056478280c swap swap sw 0 0

---

### Post by drs305 on 2010-07-14
Those are the expected results until you make the changes mentioned by others. Just make the edit to the first line in fstab as they recommended and save the file. Morbius1 tells you what you need to do in post #7.

If you do it correctly, you will get the same results from the *unmount* command but should see nothing (no messages) when you run the second.

---

### Post by Morbius1 on 2010-07-14
You have the [COLOR=Blue]\040[/COLOR] in the wrong place:
What you have is this:
> UUID=90EEE603EEE5E188 [COLOR=Blue]/040[/COLOR]media/Tsunami Shango_ ntfs-3g  remount,dirsync,users,nodev,sync 1 0What you need to have is this:
>                               UUID=90EEE603EEE5E188 /media/Tsunami[COLOR=Blue]\040[/COLOR]Shango_ ntfs-3g    remount,dirsync,users,nodev,sync 1 0                      And that's just to remove the mount point error.

---

### Post by guy.komaclo on 2010-07-16
I was away for two days.
I tried again this morning with the correction and here are the messages below:

hurricane@hurricane-laptop:~$ sudo umount -a
umount: /var/run: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev/shm: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /dev: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
hurricane@hurricane-laptop:~$ sudo mount -a
Remounting is not supported at present. You have to umount volume and then mount it once again.


You will also find the content of fstab below
UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g remount,dirsync,users,nodev,sync 1 0
UUID=7a11e666-a525-454c-a149-692dd326a0b3 / ext4 defaults 0 1
UUID=f2e98ee6-5cfc-4cf7-a784-bf056478280c swap swap sw 0 0

---

### Post by guy.komaclo on 2010-07-16
Error mounting: mount exited with exit code 1: helper failed with:
Remounting is not supported at present. You have to umount volume and then mount it once again.

---

### Post by Morbius1 on 2010-07-16
Do yourself a favor and redo the entire line from this:
>  UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g  remount,dirsync,users,nodev,sync 1 0To this:
```
UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs defaults 0 0
```

---

### Post by drs305 on 2010-07-16
> **guy.komaclo said:**
> Error mounting: mount exited with exit code 1: helper failed with:
Remounting is not supported at present. You have to umount volume and then mount it once again.

Let's clean up your fstab to just the basic mount options and see if that works:

> UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g defaults 0 0

---

### Post by Morbius1 on 2010-07-16
Great minds think alike it seems :D

---

### Post by guy.komaclo on 2010-07-16
You always know when some great minds comes together.:D
The results speak by themselves.
It works.
Thank you very much Guys
:popcorn:
;)

---

### Post by drs305 on 2010-07-16
Glad it's fixed.

If you want a bit more control over the ntfs partition, you can make yourself the owner of the partition when it mounts. Assuming you are user 1000 (check with "id" in terminal), you can alter it with this setting:

> 
UUID=90EEE603EEE5E188 /media/Tsunami\040Shango_ ntfs-3g defaults,uid=1000 0 0 

There are additional settings you may want. Here is a good explanation of many of them by bodhi.zazen:
[Understanding fstab]("http://ubuntuforums.org/showthread.php?&t=283131")

Also, would you please mark the thread "SOLVED" via the 'Thread Tools' link at the top right of the first post.  (Hint: When you try changing the settings and it breaks again you can go to the same link and remove the "SOLVED" tag  ;-)  )

---

