---
title: "Can't mount floppy..."
date: 2008-09-06
forum: Hardware
---

### Post by tracetheace on 2008-09-06
Every time I try to mount the floppy by:

# mount /media/floppy
It returns this error:
mount: /dev/fd0 is not a valid block device

I've checked
# lsmod | grep floppy
returns
floppy     59588  0

I've also checked
dmesg | grep -i floppy
returns
[   32.062220] Floppy drive(s): fd0 is 1.44M

Can anyone help me with this?
Thanks.

---

### Post by wandalalakers on 2008-09-06
check your fstab file.  post your fstab

---

### Post by edumavi on 2008-10-03
> **tracetheace said:**
> Every time I try to mount the floppy by:

# mount /media/floppy
It returns this error:
mount: /dev/fd0 is not a valid block device

I've checked
# lsmod | grep floppy
returns
floppy     59588  0

I've also checked
dmesg | grep -i floppy
returns
[   32.062220] Floppy drive(s): fd0 is 1.44M

Can anyone help me with this?
Thanks.
Same here, I don't even see The Floppy Drive in the File Browser.
I've tried in two computers already, and still the same.
I'm not an advanced user of Ubuntu.

I am using Intrepid Beta

Intel Celeron D 3.06 - Biostar Motherboard - Nvidia 7300 video card

---

### Post by cariboo on 2008-10-03
Your floppies should be automounted, just like a usb device. If it isn't working, try another disk. I stopped using floppies when the quality of the disks got so bad that even preformatted disks didn't work anymore without formatting them first, and then they would only work in the computer they were formaated on. I have 51/4 Floppies from the late 80' that work better than what is available now.

JIm

---

### Post by earthwarrior on 2008-10-28
I found this in another thread and it worked for me.

The floppy modules does not get loaded automatically in Intrepid. Check to see if the floppy module is loaded by typing in a terminal:

Code:

lsmod | grep floppy

If the module is loaded you should see some out put with the word floppy in it. If you don't see any output insert the floppy module:

Code:

sudo modprobe floppy

You should now be able to use your floppy drive. 

I also installed fdutils which can automatically mount the floppy drive.

---

### Post by satellitex86 on 2009-01-10
That fixed it for me.
Thanks a lot!

---

### Post by alienexplorers on 2009-01-14
If you enter terminal and type:
> sudo gedit /etc/modules
and add at the end of the file floppy and save it, it will do the modprobe floppy automatically.

---

### Post by archolman on 2009-03-14
[SIZE=2]
[/SIZE][SIZE=2][B]The information in here has solved my problem!
 Thanks all;)[/B][/SIZE]

---

### Post by shields on 2009-04-09
> **earthwarrior said:**
> 
The floppy modules does not get loaded automatically in Intrepid. Check to see if the floppy module is loaded by typing in a terminal:

Code:

lsmod | grep floppy

If the module is loaded you should see some out put with the word floppy in it. If you don't see any output insert the floppy module:

Code:

sudo modprobe floppy

You should now be able to use your floppy drive. 

That ROCKS! Thanks! :guitar:

---

