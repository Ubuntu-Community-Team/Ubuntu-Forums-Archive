---
title: "Virtual CD-rom for use with Synaptic"
date: 2010-09-29
forum: Hardware
---

### Post by kklungre on 2010-09-29
Hi

My Asus eee 1001PX haven't got a cd-rom, which makes downloading packages with synaptic a bit tricky. (A bit tricky for me at least).

I used this line to mount the .iso file (found it on the forum)

sudo mount -o loop -t iso9660 kilde.iso /media/cdrom

What can I do to make synaptic locate the 'cd-rom' I've just created?

---

### Post by snowpine on 2010-09-29
Hi kklungre, is there a reason you do not simply download and install packages from the online Ubuntu repository? This is the default behavior I would recommend for most users, unless you have a specific concern that prevents you from doing so?

---

### Post by kklungre on 2010-09-29
> **snowpine said:**
> Hi kklungre, is there a reason you do not simply download and install packages from the online Ubuntu repository? This is the default behavior I would recommend for most users, unless you have a specific concern that prevents you from doing so?

I use EasyPeasy (That's a version of Ubuntu right? :| I'm quite new at this Linux malarkey), and when I try to install ndisgtk using synaptic I'm told to insert the EasyPeasy-1.6 cd.

If there is a way to just do it via online sources I'd be thrilled.

---

### Post by snowpine on 2010-09-29
> **kklungre said:**
> I use EasyPeasy (That's a version of Ubuntu right? :| I'm quite new at this Linux malarkey), and when I try to install ndisgtk using synaptic I'm told to insert the EasyPeasy-1.6 cd.

If there is a way to just do it via online sources I'd be thrilled.

No, EasyPeasy is not supported here (they probably have their own forum, I just don't know)... in Ubuntu, you would go to the System menu and choose Administration, Software Sources. Then, uncheck the box for the Ubuntu CD-ROM. Perhaps a similar fix will work in EasyPeasy?

---

### Post by kklungre on 2010-09-29
> **snowpine said:**
> No, EasyPeasy is not supported here (they probably have their own forum, I just don't know)... in Ubuntu, you would go to the System menu and choose Administration, Software Sources. Then, uncheck the box for the Ubuntu CD-ROM. Perhaps a similar fix will work in EasyPeasy?

Opened Software Sources and unchecked the cdrom box. :D I think EasyPeasy is pretty much the same as Ubuntu for eee laptops. A friend of mine installed it.

Can I add the .iso file, or the folder I mounted the .iso-file to as a source?

Thanks for the help, seems like I'm making progress.

---

### Post by snowpine on 2010-09-29
The command "apt-cdrom" can be used to mount a CD (or CD image) as a repository:

[http://linux.die.net/man/8/apt-cdrom](http://linux.die.net/man/8/apt-cdrom)

I don't use it myself as I have a good internet connection.

---

### Post by kklungre on 2010-09-29
> **snowpine said:**
> The command "apt-cdrom" can be used to mount a CD (or CD image) as a repository:

[http://linux.die.net/man/8/apt-cdrom](http://linux.die.net/man/8/apt-cdrom)

I don't use it myself as I have a good internet connection.

Thanks, I'll try it out. :)

---

