---
title: "help installing Debian"
date: 2008-08-20
forum: General Help
---

### Post by eival on 2008-08-20
i cant find a forum on the debian.org site, an i know ubuntu is built from it.

an i wanted to try it out, but after downloading the iso file and burning to a disc(like ive done for numerous os') i cant get the disc to boot in my VM or my actuall laptop when restarting.

ive already checked the boot order and the CD drive is set to boot first. but i never get a "press any key to boot from CD" message, it jus spins the disc first, then goes strait to the ubuntu loading screen.

i checked the debian.org/faq for issues with booting and their only answer to why it wouldnt be booting is cause the person unpacked the iso file then burned them to disc, but i didnt do that. i burned the iso properly.



so any help will be appreciated. 
mods sorry if this is in the wrong thread.

---

### Post by HermanAB on 2008-08-20
Run md5sum and verify that the CD is OK.  If not (very likely) reburn it at a slower speed.  Anyhoo, with a VM, you don't need an actual CD, just set the CDROM device to point at the ISO file.

Cheers,

Herman

---

### Post by bodhi.zazen on 2008-08-20
You need to set your BIOS to boot from CD before hard drive.

It you have done that, most likely you have a bad iso or burn as suggested by HermanAB.

Check your MD5 sums

---

### Post by LowSky on 2008-08-20
remember to burn as an ISO CD, just burning it to a DATA CD won't do anything

---

### Post by eival on 2008-08-20
> **HermanAB said:**
> Run md5sum and verify that the CD is OK.  If not (very likely) reburn it at a slower speed.  Anyhoo, with a VM, you don't need an actual CD, just set the CDROM device to point at the ISO file.

Cheers,

Herman

to run md5sum do i use Alt+F2 and enter that in there?
cause that does nothing, i also tried "run in terminal" but it just clears the directory an all i get is a blank terminal an a cursor.

i have an md5sum file on the disc tho.

heres a screen cap of the disc when i open it up in ubuntu.
an yuo can see the intact iso file that i burned using braseo, is on the desktop aswell.

[http://i34.tinypic.com/2r5fd6q.png](http://i34.tinypic.com/2r5fd6q.png)


does anything look out of the ordinary?

this is the first OS thats givin me an issue in terms of just booting/installing, so i dont know what to do.

---

### Post by todak on 2008-08-20
You downloaded CD-6, which is just a cd full of packages so that  you can download them locally without being connected to a network. Download CD-1 which is the base bootable debian system! :)

---

### Post by eival on 2008-08-20
> **todak said:**
> You downloaded CD-6, which is just a cd full of packages so that  you can download them locally without being connected to a network. Download CD-1 which is the base bootable debian system! :)

:mad:

wow, i thought the numbers were just cause it was hosted by a different server or sumthin

okay, ill download disc 1, thanks.

---

