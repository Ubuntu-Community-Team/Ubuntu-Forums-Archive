---
title: "CD/DVD drive won't open"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by Solus on 2005-04-29
If I put anything but an audio CD into my drive, I won't be able to get it open again unless I reboot and open the drive while its in the process of shutting down or rebooting.  It seems like its mounted but its not.  Any suggestions?

---

### Post by brk3 on 2005-04-29
Sure its not mounted? Try right clicking the icon for the drive and selecting 'eject'..

---

### Post by Solus on 2005-04-29
Thanks.  I found that right click -> eject thing an hour after I posted.  I've never seen that before so I didn't think about doing it. I did it on accident.

---

### Post by magicfab on 2005-04-29
You can also type "eject" in a terminal window.

---

### Post by Psquared on 2005-04-29
I found that out too. The eject button on the CDRom/DVD does not work on my laptop and I can only open it by right clicking on the desktop icon. 

Is this a security feature so you won't eject while the CD is playing or is it something that was overlooked?

---

### Post by orion_114 on 2005-05-04
I am having the same problem. I can eject the disc by right clicking on it and selecting eject, but the actual eject button on both my disc drives don't work. I had the same problem on another machine with Hoary. Is this a bug ?

ps. I know its pretty arbitrary, but it scares off newies a bit. My girlfriend was freaked out. She thought she had broken my drive! lol !  :smile:

---

### Post by DutchLau on 2005-05-04
Hi again,

What about this error message?

> eject: unable to eject, last error: Invalid argument (From Terminal)

or  

> eject: unable to eject, last error: Invalid argument (From Gnome)

What can I do about this? I have a CD stuck in the drive, but I don't want to have to reboot just to get it out.

---

### Post by superhac007 on 2005-05-04
Strictly for the hardcore......

```

# rmmod ide_cd
# rmmod cdrom

# modprobe cdrom lockdoor=0
# modprobe ide_cd

```

Insert disk....then press eject....

---

### Post by spartas on 2005-05-04
[QUOTE=DutchLau]Hi again,

What about this error message?

 (From Terminal)

or  

 (From Gnome)

What can I do about this? I have a CD stuck in the drive, but I don't want to have to reboot just to get it out.[/QUOTE]

Occasionally I've gotten that before (usually after mounting/unmounting the CD).  In that situation, you have to use the following command

```

sudo eject

```

---

### Post by DutchLau on 2005-05-04
WoW No way!  :razz: 

At first I was skeptical but this actually worked! Simple & highly effective. Thanks man!

Greets,

DutchLau

EDIT: That's hilarious though, that you need access as a superuser to take your CD out of the drive. LoL

EDIT2: It still gives the error message, but it DOES eject  :grin:

---

### Post by Lin4win on 2005-05-04
[QUOTE=superhac007]Strictly for the hardcore......

```

# rmmod ide_cd
# rmmod cdrom

# modprobe cdrom lockdoor=0
# modprobe ide_cd

```

Insert disk....then press eject....[/QUOTE]

Dude you rock!  This has been driving me NUTZ!

---

### Post by Psquared on 2005-05-04
[QUOTE=superhac007]Strictly for the hardcore......

```

# rmmod ide_cd
# rmmod cdrom

# modprobe cdrom lockdoor=0
# modprobe ide_cd

```

Insert disk....then press eject....[/QUOTE]

You mean just type this in a terminal and it changes the setting to allow the button to work? Is it only valid for that session or is the change permanent?

---

### Post by superhac007 on 2005-05-04
[QUOTE=Psquared]You mean just type this in a terminal and it changes the setting to allow the button to work? Is it only valid for that session or is the change permanent?[/QUOTE]

If you type that at the prompt its only good for the session... aka reboot and its gone.  

If you want  to make it stick read this post on parameter passing: [http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear](http://www.ubuntuforums.org/showthread.php?p=6003&mode=linear)

---

