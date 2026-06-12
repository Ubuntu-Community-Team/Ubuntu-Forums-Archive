---
title: "Use separate drive as /home/user/Videos ?"
date: 2008-08-04
forum: General Help
---

### Post by T0mmy on 2008-08-04
I have my root-folder on /dev/sda1, and home-folder on /dev/sdb1.
I also got a third drive, /dev/sdc1 which I want mounted as my Video-folder, so when I enter Home and double-click Videos, I will see the content on sdc1.

Both fstab and mount-command will do this, but not exactly the way I want.

When I use fstab or manually mount it, sdc1 shows as mounted in the Places-menu, and also on my Desktop. In the Places-menu the Video-folder also gets renamed to "400GB Media". In Nautilus bookmarks-menu and browser-window, the folder is named Video, which is what I want.

the lost+found-folder is also visible in the Video-folder. Any way to avoid this?


How do I mount the drive as my Video-folder without having it in Places and on Desktop?


Even though my Home-folder is on a separate drive, it doesn't show up as mounted, so I think it should be possible.

---

### Post by drs305 on 2008-08-04
If you put the mount point in somewhere other than /media it shouldn't show on the desktop. /mnt is the old default...

To hide the 'lost+found' folder, you can make a text file in the same directory called '.hidden'.  Inside the file you can type the names of any files or folders in the same directory that you don't want to see when the 'View Hidden' option is not selected.

As far as Places, you can create a shortcut to the file. I don't think it's going to show up in Places automatically if you change the mount point but I'm not positive. You can also label the partition and mount it that way and it will display the label name. To label an ext3 partition the command is:
```

tune2fs -L <label> <dev>

```

---

### Post by T0mmy on 2008-08-04
Thanks for the ".hidden" tips!

I've tried to mount it to both /media/disk and /home/user/Videos, but it always appears on Desktop and in Places-menu.

Are there any mount options that could do the trick? When I tried with fstab i used default options.

I was hoping there was a possibility to hide what was really going on, and just have my Video-folder displaying the contents on sdc1. Too bad the disk appears on both Desktop and Places-menu.

I really hope someone has a solution...

---

### Post by drs305 on 2008-08-04
This command hides mounted volumes from appearing on the desktop. Values are true and false:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

---

### Post by T0mmy on 2008-08-04
> **drs305 said:**
> This command hides mounted volumes from appearing on the desktop. Values are true and false:
```
gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

But this command will also hide normally mounted cdrom and usb-drives, right?


I've found some bug-reports that may affect my situation, but I can't understand why it can't be done, since it's already working for my home-folder.

[https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/159707](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/159707)
[http://bugzilla.gnome.org/show_bug.cgi?id=325476](http://bugzilla.gnome.org/show_bug.cgi?id=325476)
[https://answers.launchpad.net/ubuntu/+question/16593](https://answers.launchpad.net/ubuntu/+question/16593)

I'm still hoping for a solution.

---

### Post by drs305 on 2008-08-04
> **T0mmy said:**
> But this command will also hide normally mounted cdrom and usb-drives, right?


Yes it will. If I can come up with a solution I'll append this post.

---

### Post by derrick81787 on 2008-08-04
> **T0mmy said:**
> When I use fstab or manually mount it, sdc1 shows as mounted in the Places-menu, and also on my Desktop.

I didn't think that this was the normal behavior.  I could be wrong though.  Do you mind posting the line in your /etc/fstab that you used to mount the drive?  I'd like to take a look at it.

- Derrick

---

### Post by T0mmy on 2008-08-04
I've now found a solution/workaround:

1 - Mount the drive in /mnt (i.e. /mnt/disk), which will prevent the drive from appearing both on Desktop and in Places-menu ([http://ubuntuforums.org/showthread.php?t=114369](http://ubuntuforums.org/showthread.php?t=114369))

2 - Delete the original Videos-folder in /home (remember to backup the folders content before you do so), and make a symbolic link with the name Videos which in my case points to the folder Videos on the mounted drive (/mnt/disk/Videos).

Result: The drive is invisible on Desktop and in Places-menu. It's original location is /mnt/disk, and you are free to create a symbolic link from wherever you want

If the original Videos-folder (the one you deleted) disappears from the Places-menu, you can add the new symbolic link through Nautilus -> Bookmarks -> Edit Bookmarks

---

