---
title: "My computer can't find anything outside the desktop!"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by T_Stormcrowe on 2005-10-08
I finally got "Hoary to install, but it can't find the floppy drive. It's a legacy fd. Does anyone know about any dependency or compatibility issues? The other thing is that the 'puter only has 64meg RAM currently. Is it possibly a  RAM issue?Here are the errors I got in install: Ubuntu desktop-cdrom//pool/main/p/pyopengl/python.24.......
dependency problem python-openg-l
dpkg error-desktop
 I am a newbie with linux and am impressed at this point that I even got the desktop and games working! I can't seem to access the peripheral hdwr like cdrom and floppie disk drive.......HELP!:confused:

---

### Post by T_Stormcrowe on 2005-10-12
Not trying to pester here, but I really could use some help! How about someone taking pity on a newbie and make some suggestions on what my next step needs to be! :confused: 

[QUOTE=T_Stormcrowe]I finally got "Hoary to install, but it can't find the floppy drive. It's a legacy fd. Does anyone know about any dependency or compatibility issues? The other thing is that the 'puter only has 64meg RAM currently. Is it possibly a  RAM issue?Here are the errors I got in install: Ubuntu desktop-cdrom//pool/main/p/pyopengl/python.24.......
dependency problem python-openg-l
dpkg error-desktop
 I am a newbie with linux and am impressed at this point that I even got the desktop and games working! I can't seem to access the peripheral hdwr like cdrom and floppie disk drive.......HELP!:confused:[/QUOTE]

---

### Post by wylfing on 2005-10-12
If you choose Places > Computer from the main toolbar, do you see the floppy and CD drive?

---

### Post by T_Stormcrowe on 2005-10-13
[QUOTE=wylfing]If you choose Places > Computer from the main toolbar, do you see the floppy and CD drive?[/QUOTE]
Yes, I do, The properties also come up as well. Am I perhaps using the wrong procedure when I try to access data? I have been trying to access the floppy through open file command and all I get is the desktop. Now when I go through Places>Computer, I see all peripheral hardware. Hmm!:confused:

---

### Post by T_Stormcrowe on 2005-10-13
[QUOTE=wylfing]If you choose Places > Computer from the main toolbar, do you see the floppy and CD drive?[/QUOTE]
All right, to continue, I get the window "Unable to mount" when I try to open floppy from there.  If I try to open cdrom, I get the prompt to use the "Broken" filter. I take it I have config problems? If so, what do I do about them?

---

### Post by T_Stormcrowe on 2005-10-16
Still hoping for help here folks! Have patience with the newbie please![QUOTE=T_Stormcrowe]All right, to continue, I get the window "Unable to mount" when I try to open floppy from there.  If I try to open cdrom, I get the prompt to use the "Broken" filter. I take it I have config problems? If so, what do I do about them?[/QUOTE]

---

### Post by wylfing on 2005-10-17
Sorry -- I must have failed to subscribe to this thread. Didn't mean to leave you high and dry :)

I'm not sure whether you have 2 different issues or not. Some people's floppy drives apparently have the ability to signal whether there's a disk inserted. Mine's probably too old, and maybe yours is too, because when I put a disk in nothing happens, and it won't mount when I double-click the floppy icon. The "solution" (other than stop using floppies) is to open a terminal and use the command [FONT="Courier New"][COLOR="DimGray"]mount /media/floppy0[/COLOR][/FONT]. If you have the Places > Computer window open, the icon for the floppy should change and you should have access to the disk.

When you're done using the floppy, you have to explicitly unmount it. Fortunately, this works properly. Just right-click the floppy icon and choose Unmount volume.

About the CD: this shouldn't be such a problem. You should be able to insert a CD into the drive and have an icon appear on the Desktop, and a nice Nautilus window should display the contents of the disc. So for the CD:

1. Are you sure there's a valid disc in the drive? Try a few different discs and see if any of them are autodetected.

2. If nothing gets autodetected, it could be that your CD drive is broken. It could also be that your drive is so old that it does not have auto-insert notification (much like our floppy drives seem to lack that feature).

As a last resort, put a CD into the drive, open a terminal, and type [FONT="Courier New"][COLOR="DimGray"]mount /media/cdrom0[/COLOR][/FONT] and see what happens.

---

### Post by jdtanner on 2005-10-17
Sounds like a similar problem to the one described in the following thread

[http://ubuntuforums.org/showthread.php?t=76481&highlight=mount+icon+desktop](http://ubuntuforums.org/showthread.php?t=76481&highlight=mount+icon+desktop)

JohnT

---

### Post by wylfing on 2005-10-17
Yep, that's the same thing. I'm quite sure it has to do with most internal floppy drives being unable to detect when a disk is inserted. It is solveable by mounting on the command line, but looks good that you've filed a bug report.

---

### Post by T_Stormcrowe on 2005-10-17
[QUOTE=wylfing]Yep, that's the same thing. I'm quite sure it has to do with most internal floppy drives being unable to detect when a disk is inserted. It is solveable by mounting on the command line, but looks good that you've filed a bug report.[/QUOTE]
Thank you both, gentlemen! I appreciate your responses and I'll let you know what the result is soo!:D

---

### Post by T_Stormcrowe on 2005-10-19
[QUOTE=T_Stormcrowe]Thank you both, gentlemen! I appreciate your responses and I'll let you know what the result is soo!:D[/QUOTE]
I'm happy to say my cdrom issue is solved! Still having floppie prblms, but I am getting around that by creating a virtual drive in a closed yahoo group for file storage! This will do til I replace the floppie with something more modern like a USB zip or flash drive!:)

---

### Post by T_Stormcrowe on 2005-10-20
OK, as I said, cdrom working, but the floppy still won't mount, even going through terminal. I tried it with different floppies as well. I wonder if my fd is bad? What ya think, just get a USB dev like a zip or maybe use a flash drive and dock of some type? My other 'puter has docks for all types of flash so this might be an option.:confused: Any advice for me, anyone? 
[QUOTE=T_Stormcrowe]Thank you both, gentlemen! I appreciate your responses and I'll let you know what the result is soo!:D[/QUOTE]

---

### Post by wylfing on 2005-10-22
Getting a flash drive is probably a good move. They're dirt cheap and hold, what, hundreds of floppies worth of data.

---

