---
title: "Editing /etc/fstab in LiveCD"
date: 2005-11-16
forum: General Help
---

### Post by andrewsawyer on 2005-11-16
Hiya,

I hope someone can help me with this.

I would like to make a permanent entry into the /etc/fstab file on the LiveCD, so that it can mount /dev/sda1 as /home.

I have extracted the filesystem.cloop to extracted_fs, and mounted this.  If I chroot into the mounted extracted_fs file, and then type 'nano /etc/fstab' I can see that it is empty - I assume it automatically adds stuff on the fly as it boots. /etc/mtab does have some entries however.

So can I just add the mount point details into the fstab file, or will this get written over each time the computer is rebooted?  My reasoning for this is that I would like to access all my data in my /home directory when using the LiveCD until I can work out how to get a LiveUSB up and running.

Any help with this would be very much appreciated.

Andy

---

### Post by kruz on 2005-11-16
haha from what i read
if your always booting the live cd
save urself time and just type it
cuz u will have to 
extract the original iso
edit that one file
compile the iso
and remake it with gator to where u have all the same attributes
booting etc.....

then burn it again

just type it out is all i can say
or keep a floppy in ur computer with that command in a shell script
lol
then ull have to mount ur floppy if it doesnt mount it though

not worth the effort

---

### Post by andrewsawyer on 2005-11-16
What do you mean - just type it?

Just type it where?

Basically, my /home partition is currently on a USB disk.  That way, I always have my upto date data with me.

Now while we haven't yet worked out how to make a LiveUSB (but I'm working on it), it would be nice to be able to use Ubuntu where ever I am.  Carrying a usb disk and a CD-R is much easier than carrying a laptop!

It's not like I use the LiveCD all the time - mostly I use my own computer, with Ubuntu installed.  I use the LiveCD just like anyone else - it's handy to have around to show other people etc, or do work while away from my desk.  I would however like all my settings (themes etc) to be available when I boot it, and these are all kept in the /~ directory.

So yes, I could just boot the cd and mount the USB into /mnt to get access to my data, but this wouldn't configure Ubuntu how I like it each time - I'd still get the standard setup.

I hope this clarifies.  Please let me know what you mean by 'type it'.

Andy

P.S. - as far as all the hassle you talk about, I have already extracted the filesystem.cloop.  I can just edit it (where ever I need to), recompress it, make the iso and burn.  I figure a couple of hours of work all in one go to save repeated post-boot configurations every time I load the LiveCD is well worth the effort.

---

