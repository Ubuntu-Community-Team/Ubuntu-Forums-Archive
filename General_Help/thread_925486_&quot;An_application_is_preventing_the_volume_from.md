---
title: "&quot;An application is preventing the volume from being umounted&quot;  Help!?"
date: 2008-09-20
forum: General Help
---

### Post by Modax42 on 2008-09-20
I'm trying to install Baldur's Gate II, my favourite windows game, under wine.  Problem is, BGII comes on 4 CDs and the installation process requires all 4 to be used during setup.  When the wizard asks for the next CD, and I press the eject button, I get the "application preventing volume from being unmounted" message. So I'm kinda stuck. :confused:

Basically, is there a command to override the application I can use to eject the disk?  Or does anyone have any other ideas of how I can get this to work?

If someone can help me with this I'd be so grateful!

---

### Post by lordadi on 2008-09-20
Right click on any menu bar and click add to panel. After that select the Disk mounter. When you are installing the game, after the first disk, click the disk in the applet you just added and select eject, this will both unmount the disk and eject it. The unmounting should, hopefully, take care of the "An application is preventing the volume from being umounted" thing and let you on your way.

If not, post back and we will see how we can help.

Lordadi.

---

### Post by mc4man on 2008-09-20
A lot of people use the command > wine eject in the terminal.
I prefer to run the install like this, it maintains the proper path for the remaining cd's. When prompted for the next cd just use the eject button on the drive. (doing it this way you retain control of the drive)
```

wine [COLOR="Red"]D[/COLOR]:\[COLOR="Red"]setup.exe[/COLOR]
```

adjust red to match drive (as shown in winecfg -> drives) and the install command (as seen on cd

---

### Post by Modax42 on 2008-09-20
I tried 

"Sudo umount -f /media/BG_CD1"

in the terminal, but this gives me the message

"umount2: device or resource is busy
 umount: /media/BG2_CD1: device is busy"
](*,)

There simply MUST be a way to get around this.  Its such a simple, dumb glitch, there has to be a solution.  Otherwise my relationship with Ubuntu will become very strained.

---

### Post by Modax42 on 2008-09-20
> **mc4man said:**
> A lot of people use the command  in the terminal.
I prefer to run the install like this, it maintains the proper path for the remaining cd's. When prompted for the next cd just use the eject button on the drive. (doing it this way you retain control of the drive)
```

wine [COLOR="Red"]D[/COLOR]:\[COLOR="Red"]setup.exe[/COLOR]
```

adjust red to match drive (as shown in winecfg -> drives) and the install command (as seen on cd


Thank you so much! Its working now. We posted simultaneously, so I didn't see your message while I was composing mine.  So you can disregard my last message.:D

---

### Post by King8000 on 2009-01-06
Hi

I had the same problem, and while running the setup from terminal didn't work for me, using wine eject did. (More detail at the WINE wiki, [http://wiki.winehq.org/eject](http://wiki.winehq.org/eject)

wine eject d:

and it worked great :)

---

