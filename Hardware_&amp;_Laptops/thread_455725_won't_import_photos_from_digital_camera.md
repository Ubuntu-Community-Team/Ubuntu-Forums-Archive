---
title: "won't import photos from digital camera"
date: 2007-05-26
forum: Hardware &amp; Laptops
---

### Post by meggie9385 on 2007-05-26
I can't get my computer to import my photos from my digital camera.  Every time I receive the following message: An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.  I have a Kodak EasyShare C533, if that helps.

---

### Post by swudee on 2007-05-27
Hi

Which version of Ubuntu are you using? Feisty (7.04)?
Which program are you using to download the photos?
GTKam?  You could try some others such as Digikam.

Some more info would help:D

---

### Post by meggie9385 on 2007-06-02
I am using 7.04 and I am not sure what I am using to download them (gthumb maybe?).  I am very new to ubuntu and am pretty much feeling my way around.  Pretty much I am just using the standard import photos program.

---

### Post by linux_author on 2007-06-02
- i posted the following a couple hours ago (having just gone through this):

- appears to be a common problem for *some* cameras... am running edgy on a notebook..

- while my sony dsc-s700 has no problems, i encountered significant obstacles with a new canon a570is...

- the error reared its ugly head as soon as i attached and powered on:

"...unable to attach device..."

my solution:

1. turn off auto-import: System->Prefs->Removable Drives->camera tab

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

