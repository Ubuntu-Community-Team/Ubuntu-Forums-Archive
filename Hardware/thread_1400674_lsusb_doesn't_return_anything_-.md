---
title: "lsusb doesn't return anything :-/"
date: 2010-02-07
forum: Hardware
---

### Post by dodjob on 2010-02-07
Hi everyone!
Well I've tried to plug my Canon Eos 400D on my laptop.
Nothing happend and when I've tried to start a lsusb in a terminal it just return.. nothing. (not hanging.. just get back to the command line).
The usb works well normally, I've a usb mouse, I can plug usb storage devices.. everything works except this F#$%!! Camera :-(
My config is a Karmic with XX.X:XX.19 kernel (with XX:XX:17 it wasn't working as well) 
My Hardware is a Dell studio 1555
I hope getting some help :-(
Regards,
Dodjob

---

### Post by IcarusR on 2010-02-07
Have you tried lsusb without camera plugged in ?

May be simpler to use a USB card reader & put camera card in that.

---

### Post by dodjob on 2010-02-07
Hi IcarusR,
Well Lsub without the camera plugged give the same result...
The worst is that I've a virtualbox with Xp on.. and it's working!! without problem.
Use a card reader.. mm Canon has made the things well it's a Compact flash and my computer doesn't have such (hudge) hole ;-)
Actually, even if I'm quite a Noob i'm not please to have something not working on my Machine. I would like to find a workaround to get it working. On my jaunty on my desktop PC it's working without problem.
Thanks for the reply!
Dodjob.

---

### Post by dodjob on 2010-02-10
Anybody with this problem?

---

### Post by dodjob on 2010-03-09
Ähm.. I think I can bump :-/
I cannot be the only one without lsusb working :-(

---

### Post by Fafler on 2010-03-09
Maybe ```
sudo mount -t usbdevfs none /proc/bus/usb
``` could help. But i'm not sure why it should be broken on your system. Or if it should even help.

---

### Post by dodjob on 2010-03-09
Hi,
thanks for the answer... It cannot work :-/
I don't have any "/usb" in "Bus" folder...
 
the answer is so really not original :-/

mount: mount point /proc/bus/usb does not exist

I have a second computer and it's working without any problems.

---

### Post by dodjob on 2010-03-09
I've forget to add that in my virtualbox /xp the usb are working without problem.. :-/

---

### Post by dodjob on 2010-03-17
re bUMp ;-)

---

### Post by conradin on 2010-03-17
perhaps try reinstalling the package usbutils that lsusb belongs to. See synaptic package manager.

---

### Post by dodjob on 2010-03-21
Hi,
 thanks for the reply but this was the first thing have made. I think I will wait one month and hope the Lynx will be wiser with my usb :-D
Regards,
Dodjob

---

### Post by dodjob on 2010-06-29
Well I've updated to Lynx.. but the big cat didn't help me :-/ If anyone can lend a little help there. I would be quite released from a big weight.
To condensate the inputs:
[LIST]
[*]My Canon eos won't mount
[*]It's found by the usb selection from my virtualbox
[*]it's usable under my shitty emulated Xp
[*]lsusb don't return anything
[*]I don't have a folder usb in /proc/bus folder
[/LIST]
Hope someone can help :-)
Cheers!,
dodjob

---

