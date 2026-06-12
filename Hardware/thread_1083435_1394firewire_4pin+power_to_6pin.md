---
title: "1394/firewire: 4pin+power to 6pin?"
date: 2009-02-28
forum: Hardware
---

### Post by minsf on 2009-02-28
i have a 4 pin IEEE 1394 (firewire) port that i would really like to use to connect to my portable hard drive. 

problem is i cannot find a 3 way cable power+4pin to 6pin (or 9 pin). (all my searches yield simple 4pin to 6pin which cannot poser the device)

my question is if it is easy to make something like that by hand (that is, to take 6pin to 6pin cable, separate the power wires and connect the other 4 to a 4pin connector.)

could anyone tell me how to identify the power pins out of the 6?

does firewire work well with ubuntu?

(I have usb 1.1 at about 1MB/s, so every normal backup takes days to complete. i also have 9pin serial port, 25hole paralel port, 15hole video, ps/2, 7pin s-video, irDA v1.1, and 200 pin docking port, but i doubt if i can do anything useful with those. thus, the 1394 seems like my best shot)

EDIT: full specifications here: [www.dell.com/downloads/us/products/latit/c840_spec.pdf](www.dell.com/downloads/us/products/latit/c840_spec.pdf)

---

### Post by jerrrys on 2009-03-01
Hi minsf:

first..even using a 1.1 usb, it shouldnt take days to back up. what software are you using?

if im reading your post right, you are trying to hook a usb to firewire?
if you are; as far as i know that wont work. and while im on firewire im going to guess that you got firewire400 which will give you a higher xfer rate, but really nothing to write home about. so if backup is taking days, your probally not going to be happy with this.

does firewire work well with ubuntu? maybe... maybe not:
[http://www.linux1394.org/hcl.php?class_id=15](http://www.linux1394.org/hcl.php?class_id=15)

if you can buy such a cable check this place out:
[http://www.usbgear.com/USB-PCI-PCMCIA.html](http://www.usbgear.com/USB-PCI-PCMCIA.html)

and last, there are serial to usb and even parallel to usb converters. i have not used either, just know such things exist

goodluck

---

### Post by minsf on 2009-03-01
first, thanks a lot for your reply!
no, i'm not trying to hook usb to firewire or something like that. i know this is impossible. i just want to use the firewire port on my laptop INSTEAD of a slow usb port. i think you are right and this is firewire 400 indeed. it should theoretically give me (a bit) faster rate. currently, with 1MB/s it takes _a day to backup 80GB_... if the firewire gives me 6-12MB/s it would take just a few hours (nothing to write home about, but it is at least sane).

i did not know that i need a special software to run usb or firewire, could you tell me more about this? i am running a standard ubuntu 8.10 and i thought that the uhci modules come built in, but you may be right and maybe i just need to install something, i dont know

regarding the link to the usb cards, since i have a laptop they tend to be a bit expensive ($60-$70), but my real problem with these is that my two pcmcia slots are kinda close to each other, so i cannot seem to plug in these cards if i also want to use my wireless card (also pcmcia) at the same time... :(

would serial to usb or parallel to usb be any faster?

really appreciate your help!

EDIT: if you meant a backup software- i'm just copying files with cp or dd

---

### Post by 00b00nt00 on 2009-03-01
You're right. An 80GB backup would take over 22 hours with USB 1.1!

I think you have three options:

1) Continue using USB 1.1.

2) Buy a Firewire hard disk with its own power supply.

3) Continue using USB, but reduce the amount of data you have to back up, or do it incrementally (surely you don't need to back up 80GB of data every time).

---

