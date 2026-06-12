---
title: "partition problems"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by 900donuts on 2007-03-13
how do i get my spare partitions to mount on boot up:confused: 

i tried the ubuntu desktop guide and folowed the instructions and it didn't do any thing

and i had to undo my changes to get one of the partitions to mount at all (the other was unaffected)

its clear they left something out of the guide

 could some one tell me what to do?:confused:

---

### Post by milton1 on 2007-03-13
partitions listed in fstab should mount on boot.

you can mkdir a mount point and mount the drive manually at first to make sure it mounts properly

sudo mount -t (filetype) (partition) (mount point)

---

### Post by gray-squirrel on 2007-03-13
> **900donuts said:**
> how do i get my spare partitions to mount on boot up:confused: 

i tried the ubuntu desktop guide and folowed the instructions and it didn't do any thing

and i had to undo my changes to get one of the partitions to mount at all (the other was unaffected)

its clear they left something out of the guide

 could some one tell me what to do?:confused:

Would you be able to post the contents of [FONT="Courier New"]/etc/fstab[/FONT]?  That way we can try to help find any errors, if there are any.  Thanks.

---

### Post by 900donuts on 2007-03-13
the partitions already mount properly when i do it manuley but when i folowed the instructions in the system documentation these problems occured

1. when i went to make a back up of fstab through the terminal it said that the file didn't exist

2. when i typed in the command to open the file in gedit through the terminal it opened but a message also poped up in the terminal saying something about WARNING and certifacation

3. i made the changes and rebooted the paritions didn't mount (so i tried manual) and i couldn't mount one of them until i undid my changes

---

### Post by gray-squirrel on 2007-03-13
> **900donuts said:**
> the partitions already mount properly when i do it manuley but when i folowed the instructions in the system documentation these problems occured

1. when i went to make a back up of fstab through the terminal it said that the file didn't exist

2. when i typed in the command to open the file in gedit through the terminal it opened but a message also poped up in the terminal saying something about WARNING and certifacation

3. i made the changes and rebooted the paritions didn't mount (so i tried manual) and i couldn't mount one of them until i undid my changes

Are you reading the documentation for Dapper or Edgy?  If it's the documentation for Edgy, there is a new way of mounting partitions; [UUIDs]("http://www.ubuntuforums.org/showpost.php?p=1309814&postcount=10") are used instead of the usual device names like [FONT="Courier New"]/dev/hda1[/FONT] in [FONT="Courier New"]/etc/fstab[/FONT].  I noticed that because when I installed Edgy alongside Dapper and then booted into Edgy, I could not access anything except what was in [FONT="Courier New"]/[/FONT] (which excluded [FONT="Courier New"]/home[/FONT] because it was on another partition).  I fixed it (and how is kind of off-topic for this thread), but this change is one reason why I was asking about [FONT="Courier New"]fstab[/FONT].  Without that being posted, I couldn't tell you exactly how to set it up so that all the partitions you want access to will mount on boot, or if there was anything wrong at all.  (I may have misunderstood what you were saying, though. . .)

You can use UUIDs or device names in [FONT="Courier New"]/etc/fstab[/FONT] if you're using Edgy, but as far as I know UUIDs were never used in Dapper, so that might be why not all of your partitions mounted.

Try ```
sudo cp /etc/fstab /etc/fstab.backup
``` to make a backup.  Then ```
sudo nano /etc/fstab
``` from the terminal or find the equivalent of Run Program (from the K Start Menu, I don't remember the Gnome equivalent anymore) and type ```
gksudo gedit /etc/fstab
```  If you run programs from the terminal you will see messages quite often which will help you if the program crashes and you need to file a bug report.

Tip: you can also try [FONT="Courier New"]sudo mount -a[/FONT] after editing [FONT="Courier New"]/etc/fstab[/FONT] to attempt to mount your partitions without rebooting, which can save you some time.

---

### Post by 900donuts on 2007-03-13
ok i folowed your instructions every thing works fine so far im going to re boot and see if the things mount

---

### Post by 900donuts on 2007-03-13
woot! it works 

for future refrence the documentation only covers setting up windows partions to mount anyone tring to get a second hard drive to mount like i did should folow the line of code in fstab that details your normal partition as a guide

thanks:) :) :lolflag:

---

### Post by gray-squirrel on 2007-03-14
You're welcome.  Glad to see things work out for you.  :grin:

---

