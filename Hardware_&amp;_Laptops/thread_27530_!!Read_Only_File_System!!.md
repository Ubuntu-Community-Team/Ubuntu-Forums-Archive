---
title: "!!??Read Only File System??!!"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by benplaut on 2005-04-16
never mind- solved :razz: (i'll put it in the HOWTO)

---

### Post by wavecite on 2005-04-16
I cant find where can i read you solution here.. help!!!

---

### Post by benplaut on 2005-04-16
[QUOTE=wavecite]I cant find where can i read you solution here.. help!!![/QUOTE]

woops, i tried to post it in the 5 min the server was down :grin:

ok:

1. get a LiveCD distro and boot into it

2. Back up /home directory on your primary partition (usually hda1)

3. in a Terminal, type ```
# fsck /dev/hda1
``` (replace hda1 with whatever your affected partition is. If you're not sure, it's probably hda1)

4. Answer "yes" to everything

5. Reboot (without LiveCD), and hope it works :) (it did for me)

---

### Post by wavecite on 2005-04-16
[QUOTE=benplaut]woops, i tried to post it in the 5 min the server was down :grin:

ok:

1. get a LiveCD distro and boot into it

2. Back up /home directory on your primary partition (usually hda1)

3. in a Terminal, type ```
# fsck /dev/hda1
``` (replace hda1 with whatever your affected partition is. If you're not sure, it's probably hda1)

4. Answer "yes" to everything

5. Reboot (without LiveCD), and hope it works :) (it did for me)[/QUOTE]

I have my usb external hdd which is mounted as a **/media/usbdrive**,  but the problem arise when i use to uncompress all of my tar file there and everytime  I use the command **tar** and  it always says that my file is a read only permission. I changed my owner permission using **chmod 777** but still i can't access my external drive.

---

### Post by wavecite on 2005-04-16
up...

---

### Post by benplaut on 2005-04-17
i really dunno... i'm no expert on this, i just searched the forums  :roll:

---

### Post by burquedout on 2006-10-27
I am having the same problem with my external drive and I can't seem to figure it out.  I can't back it up because I don't have a hard drive to back up 300 gigs of data that is on my external.  Can anyone help because it was working a few days ago and now It wont.

---

