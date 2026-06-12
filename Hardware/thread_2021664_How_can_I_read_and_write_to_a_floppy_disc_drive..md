---
title: "How can I read and write to a floppy disc drive."
date: 2012-07-09
forum: Hardware
---

### Post by Johnread on 2012-07-09
I am running Ubuntu 11.10 and it will not show an icon on the desktop when my floppy drive is attached although it does show the floppy drive in Disc Utility.

How can I read and write to a floppy ?  Assistance would be appreciated as I have a number of floppys I wish to transfer to a flash drive.

---

### Post by Double.J on 2012-07-09
Hi there!

Are you able to see/access the floppy through the file manager?

Second are you able to mount the floopy(s) using the terminal? you'd use something like

```
 
sudo mkdir /media/[COLOR=Red]newfolder[/COLOR]
sudo mount /dev/[COLOR=Magenta]fd0[/COLOR] media/[COLOR=Red]newfolder[/COLOR] [COLOR=Blue]-vfat[/COLOR]
```[COLOR=Black]
where
[COLOR=Red]newfolder[/COLOR] whater you want the folder to mount it at to be called.. 
[COLOR=Magenta]fd0[/COLOR] replace with the name of the floppy disk drive in disk utility.. it's probably fd0
[COLOR=Lime][COLOR=Blue]-vfat[/COLOR] [/COLOR]assumes they're windows formatted?

If you just want to make some images of the floppy disks - for example if they are bootable floppys - you can create images of the floppys using the dd command.

Hope it helps!
[/COLOR]

---

### Post by coffeecat on 2012-07-09
@Johnread, I've not tried reading a floppy for some little while and haven't tested this in 11.10, but this udisks command should do it:

```
udisks --mount /dev/fd0
```

You don't have to create a mountpoint if you use udisks. Be aware that floppy writing is somewhat different from what you would be used to in Windows and you need to ensure that writes have been flushed from the buffer before physically removing the disc. More here:

[http://ubuntuforums.org/showpost.php?p=11244050&postcount=2](http://ubuntuforums.org/showpost.php?p=11244050&postcount=2)

---

