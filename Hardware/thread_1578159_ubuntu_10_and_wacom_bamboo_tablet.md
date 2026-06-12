---
title: "ubuntu 10 and wacom bamboo tablet"
date: 2010-09-20
forum: Hardware
---

### Post by kaminal on 2010-09-20
Hello

I have a bamboo wacom table and would like to have it work with ubuntu 10.4 on a Toshiba laptop

Thank you for your help i am new at all this

---

### Post by Favux on 2010-09-20
Hi kaminal,

Welcome to Ubuntu forums!

Which model Bamboo tablet do you have?  Is it one of the newer ones with touch?

---

### Post by kaminal on 2010-09-20
hello favux!

it is a bamboo fun tablet
it does not have a touch device that i can tell
only a circle zoom at top  which you activate wit your hand with 4 buttons 2 on each side
it also came with a mouse that sits on top of the tablet and works like a regular mouse
the cd driver says:

pen tablet driver v.5.1.0 WIN/5.1.0 MAC

it works in windows (i have a dual booth an want to use only ubuntu for the internet)

thank you for your help

---

### Post by kaminal on 2010-09-20
hello favux!

it also has in the bottom side:

bamboo fun
model CTE-650

---

### Post by Favux on 2010-09-20
Alright, that should work out of the box.  Have you checked in Synaptic Package Manager that xserver-xorg-input-wacom is installed?  If it isn't have Synaptics install it and reboot.

---

### Post by kaminal on 2010-09-22
thank you

Yes the xserver-xorg-input-wacom package is installed in the synaptic

When I put in a usb flash drive ubunto does not recognize it either, windows does

I wonder if the problems are related

---

### Post by Favux on 2010-09-22
That would imply a problem with usb, wouldn't it?

Let's see if the wacom.ko (usb kernel module) is loading.  Enter in a terminal:
```
lsmod | grep wacom
```
and let's look at the output.

---

### Post by kaminal on 2010-09-22
I typed the lsmod | grep wacom command in the terminal and there was no output

thank you

---

### Post by Favux on 2010-09-22
Ok, it sounds like the wacom.ko isn't autoloading.  To confirm you have a wacom.ko, which you should, enter in a terminal:
```
modinfo -n wacom
```
The output should show the path.

If it is there add "wacom" (without the quotes) to the end of the file 'modules' in "/etc/":
```
gksudo gedit /etc/modules
```
and reboot.

---

### Post by kaminal on 2010-09-23
great!

there is a path:

/lib/modules/2.6.32-21-generic/kernel/drivers/input/tablet/wacom.ko


i also added "wacom" without quotes at the end of /etc/modules

then I rebooted 

but my tablet still is not working

I am excited I can understand and follow your directions

could it be that because the tablet runs on windows 7 it blocks it in ubuntu?

thank you!

---

### Post by Favux on 2010-09-23
Hi kaminal,

> could it be that because the tablet runs on windows 7 it blocks it in ubuntu?
No, but that is important because it tells us your hardware works and the problem is with linux.

So does any usb device work with your Toshiba laptop in linux?

---

### Post by kaminal on 2010-09-23
Sorry but no

under the places menu I only see computer and the hard drive
thanks

---

### Post by Favux on 2010-09-23
Try in a terminal:
```
sudo modprobe usbhid
```
and then check the usb devices again.

---

### Post by kaminal on 2010-09-24
I did
i did not get any from the toutput from terminal

i then restarted ubuntu with the usb flash and usb wacom plugss off and nothing happend

restarted again with the usbs already in place and the little light in the usb flash drive blinked and the zoom light in the wacom table lighted up too

but then i do no see them listed under the places menu nor does the wacom work

thanks

---

### Post by kaminal on 2010-09-30
Hello!

Can you still help me?

thank you

---

### Post by kaminal on 2010-09-30
Hello!

when I type 

more /proc/bus/input/devices

under N (for name) it lists "Power Buttom" instead of the wacom model

If you can not help would you please make a referral?

thank you

---

### Post by Favux on 2010-09-30
Well I don't understand why no usb device works in linux.  We know it isn't the hardware/tablet, because it works in Windows.  By the same token it can't be the tablet and the usb flash driver are usb 2.0 and the Toshiba only has usb 1.1 ports because again they work with Windows.

So somehow you appear to have a defective install of Ubutnu 10.4 Lucid.  That's what you have correct?  The vanilla install and not something else?

---

### Post by kaminal on 2010-10-03
Sure!

I can try that.

Thank you

---

### Post by kaminal on 2010-11-03
Hello!

Just to let you know that I installed the notebook edition of ubuntu with the wacom tablet and the mouse on top of it attached from the get go

It worked!

Thank you for your help.

---

