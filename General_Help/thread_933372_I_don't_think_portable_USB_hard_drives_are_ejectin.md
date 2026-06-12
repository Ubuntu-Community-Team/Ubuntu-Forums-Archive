---
title: "I don't think portable USB hard drives are ejecting properly"
date: 2008-09-29
forum: General Help
---

### Post by Excalibre on 2008-09-29
I have this general difficulty with ejecting portable USB hard drives -- I have a thumb drive, an external hard drive, and an iPod, and none of them seem to eject properly, whether I do it from the command line or from within Nautilus. For instance, the LED on the thumb drive that normally turns off if I "safely remove" it in Windows stays lit even after ejecting, either in Nautilus or after running "eject" in a terminal. With my iPod, the thing never displays the screen it's supposed to that says it's disconnected.

Does anyone know anything about this? I've never actually had any problems as far as I know, but it's still a bit worrisome.

---

### Post by C.S.Cameron on 2008-09-29
Does the drive disappear from the desktop when you do this.
 Have you tried right clicking the drive on he desktop and selecting unmount volume?

---

### Post by Excalibre on 2008-09-29
> **C.S.Cameron said:**
> Does the drive disappear from the desktop when you do this.
 Have you tried right clicking the drive on he desktop and selecting unmount volume?
They don't show up on my desktop. I think I turned that off at some point, but I don't remember how. Or maybe they never did. I don't remember -- I know they did in Gutsy, but I installed Hardy from scratch and I don't remember whether anything ever showed up on my desktop.

---

### Post by C.S.Cameron on 2008-09-29
How about if you open file browser go to /media and right click the drive there?

---

### Post by Excalibre on 2008-09-29
> **C.S.Cameron said:**
> How about if you open file browser go to /media and right click the drive there?
It doesn't eject properly. The lights stay on, the iPod doesn't display its disconnected screen, etc.

---

### Post by C.S.Cameron on 2008-09-29
Out of curiosity I have tried un-mounting three thumbdrives.
a Lexar, a Kingston and a Transcend.
The Transcend was the only one with full time light.
They all seemed to un-mount ok from the desktop, /media and computer:///.
Computer:/// still showed the partitions but said they were unmounted.
The light on the transcend stays light even when unmounted.
Almost be nice to get an obnoxious sound if done wrong, like in windows.

I think, (Hope), that if the drive is shown as unmounted in Places, Computer, it is probably ok to yank out.
Sorry, anything more technical is above my knowledge level.

---

### Post by Whiffle on 2008-09-29
Its related to the way Linux does things, versus the way Windows does things.  Actually I don't know how windows does things exactly.  But, if you want the ipod to say its not connected, the thumb drives lights to shutoff, try unloading the usb-storage module.  Thats the only way I know how to do it.  That said, as long as they're unmounted, they're safe to remove in all cases.  I've been doing it that way for years and not had any issues.

---

### Post by fragos on 2008-09-29
When you unmount a USB drive the light will stay on until all the pending writes are performed. Drives that don't show up on the desktop are still seen in the "places" drop down even if not mounted.

---

### Post by mc4man on 2008-09-29
> They don't show up on my desktop
In the configuration editor that can be set - see screen
Either from the system tools menu (disabled by default 
) or ALT+F2 enter gconf-editor.
the setting is in apps -> nautilus -> desktop

For ipod - r. click on icon -eject

---

### Post by clearnitesky on 2008-11-22
I found this solution for use with external usb hard drives. 

   1. Safely eject from Konqueror/Nautilus
   2. Enter root via su command
   3. sdparm –command=sync /dev/sdc
   4. sdparm –command=stop /dev/sdc

(obviously, you need to substitute "/dev/sdc" for the location of your drive, for me this was "/dev/disk/by-label/ext_drive", but I'm using Debian, so it could be different for you)

---

