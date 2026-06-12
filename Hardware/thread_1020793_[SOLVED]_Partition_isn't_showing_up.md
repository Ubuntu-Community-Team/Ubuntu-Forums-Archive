---
title: "[SOLVED] Partition isn't showing up"
date: 2008-12-24
forum: Hardware
---

### Post by Dumbestcrayon on 2008-12-24
Its not a big deal but when I start up my computer my partition "Stuff" isn't listed on my desktop and if I try to play some music it doesn't show that the music is available. I have to go to Place>Stuff and open the folder before it will show on the desktop and show the music in Rhythmbox. Its kind of annoying to have to open the drive every time I start my computer.


Any ideas?

---

### Post by balaknair on 2008-12-24
If it's an NTFS partition, you can use a tool named ntfs-config to configure it to mount automatically every time you boot up Ubuntu.

An illustrated guide with screenshots is available here:
[http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig](http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig)

---

### Post by Dumbestcrayon on 2008-12-25
> **balaknair said:**
> If it's an NTFS partition, you can use a tool named ntfs-config to configure it to mount automatically every time you boot up Ubuntu.

An illustrated guide with screenshots is available here:
[http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig](http://www.psychocats.net/ubuntu/mountwindows#ntfsconfig)

Its not NTFS its ext3.

I think I found where to do it I just don't know how.
Under properties > Volume > Settings > Mount Point, File System, Mount Options.


Im thinkin something goes in Mount Options but I'm not sure.

---

### Post by balaknair on 2008-12-25
You need to edit your fstab file to set it to mount automatically.

In a terminal, type
```
sudo fdisk -l
```

This shows you the available partitions.

For illustration's sake I'll assume that 'Stuff' is on sda3. So it would look a bit like this

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      XXXX        XXXX        XXXX   83  Linux
/dev/sda2          XXXX        XXXX        XXXX   82  Linux swap / Solaris
/dev/sda3          XXXX        XXXX        XXXX   83  Linux

Next,

Alt-F2--> gksudo gedit /etc/fstab--> Add this line
```
/dev/sda3 [put the location that you want it mounted here] ext3 defaults,auto 0 0
```

for eg: 
```
/dev/sda3 /media/Stuff ext3 defaults,auto 0 0

```

will automatically mount the partition sda3, and the mount point will be called 'Stuff'

Just remember to replace the 'sda3' I've used in the example with whatever you see the partition to be in 'fdisk -l'

---

### Post by balaknair on 2008-12-25
Update: There is a GUI tool to do this as well- PySDM

For a guide/howto on PySDM-
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by Dumbestcrayon on 2008-12-25
> **balaknair said:**
> You need to edit your fstab file to set it to mount automatically.

In a terminal, type
```
sudo fdisk -l
```

This shows you the available partitions.

For illustration's sake I'll assume that 'Stuff' is on sda3. So it would look a bit like this

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      XXXX        XXXX        XXXX   83  Linux
/dev/sda2          XXXX        XXXX        XXXX   82  Linux swap / Solaris
/dev/sda3          XXXX        XXXX        XXXX   83  Linux

Next,

Alt-F2--> gksudo gedit /etc/fstab--> Add this line
```
/dev/sda3 [put the location that you want it mounted here] ext3 defaults,auto 0 0
```

for eg: 
```
/dev/sda3 /media/Stuff ext3 defaults,auto 0 0

```

will automatically mount the partition sda3, and the mount point will be called 'Stuff'

Just remember to replace the 'sda3' I've used in the example with whatever you see the partition to be in 'fdisk -l'


Actually I googled it and I figured it out.

I did sudo mount and found what the drive is labeled (/dev/sda5)
then I did sudo gedit /etc/fstab
I added this line to the bottom.

```
/dev/sda5 	/media/Stuff  	ext3  	defaults  	0       0
```

Once I came back to post this as solved I found your replies.

Thanks for the replies they would have helped if I didn't already google it.

:)

---

### Post by balaknair on 2008-12-25
Great

Glad you were able to fix it.

Happy holidays

---

