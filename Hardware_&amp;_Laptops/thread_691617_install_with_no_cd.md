---
title: "install with no cd"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by pyrforos on 2008-02-08
hi guys
Here is the thing.I have 2 laptops.The first is ok. The problem is with the other one.
It has no cdrom, no ethernet card, neather a floppy drive or has the possibility to boot from usb.
If i want to install ubuntu  or xubuntu on that machine how it can be done?
Is there a way somehow , to take the hdd from one , plug it in the other one , boot from one live cd , install what i have to install  , and then take tha hdd an plug it back to the other laptop?


PS1 Noob here guys... so pleaaaaase  have patience..
PS2 Sorry about my english...

---

### Post by pmshirey on 2008-02-08
does this laptop have a serial connection?

Tell me you have replied through a private message or I can not respond to your reply.
(I visit over 100 threads a day, and reply to 75% of them):guitar:

---

### Post by lank23 on 2008-02-08
Do you have a boot from lan option "PXE" in the bios?

If so here is a nice wiki on how to make it work.

[HTML]http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install[/HTML]

lank23

---

### Post by pyrforos on 2008-02-09
@ lank23 
Dont have lan port...

@pmshirey
Not serial port either

---

### Post by lank23 on 2008-02-09
you can try and use vmware and install ubuntu on the drive from within vmware.
I have done this before and managed to get to work, but I had to edit grub files due that the drive was in a usb case and seen as /dev/sda1 instead of /dev/hda1when i used vmware.

---

### Post by lank23 on 2008-02-23
did you get it to work?

---

### Post by tango_ninja on 2008-02-23
have you tried swapping the drives and installing ubuntu on the machine with the cd drive (as you suggested) ? it would only take a sec to figure out..

---

