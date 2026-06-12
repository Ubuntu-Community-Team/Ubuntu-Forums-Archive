---
title: "Problems with digital camera recognition"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by oxidas on 2007-05-28
I`ll try to provide as many details as possible:

Version: Feisty 7.04 
Model: Panasonic Lumix dmc-tz1 
Connection: USB

I tried to use gtkam, picasa, gthumb,digikam and none worked. I connect the camera, the recognition window pops up and recognizes it as a different panasonic model (Panasonic  DMC-FZ20). And afterwards it shows that there are no photos in the camera and thus fails to import them.

---

### Post by hessiess on 2007-05-30
try using a memery card reader

---

### Post by reckless2k2 on 2007-05-30
memory card reader is an option because unfortunately not every camera works in linux. BUT, you should be able to still read the filesystem regardless not using the camera programs. In the filesystem nautilus window see if it recognizes the device which it should. then navigate in and copy/paste the files to you home directory then open the camera editing programs pointing to that area in home where you saved them.

---

### Post by linux_author on 2007-06-02
- appears to be a common problem for *some* cameras... am running edgy on a notebook..

- while my sony dsc-s700 has no problems, i encountered significant obstacles with a new canon a570is...

- the error reared its ugly head as soon as i attached and powered on:

"...unable to attach device..."

my solution:

1. turn off auto-import:  System->Prefs->Removable Drives->camera tab

2. run gtkam as root (attempting connection as regular user failed)... so i came up with a short script (named download_canon and saved under /usr/local/bin) containing:

sudo gphoto2 -P
sudo chown [myusername]:[mygroup] *.JPG

3. for example, after attaching and turning on the camera:

mkdir temp
cd temp
download_canon

(which will download all pics to current dir, then change user and group ownership of the pics)

hth!

p.s. at first i thought this was a libusb error, but i believe that gphoto2* is slightly horked (or behind in support) for some current and/or newer cameras?

---

