---
title: "Help! Hanging USB means no optical mouse or modem."
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by conal on 2007-04-12
Hello there

A small problem has  developed on my old toshiba 7020ct laptop (running xubuntu). I have only one usb port (and no standard mouse socket) so I need the usb port to plug in a 4 way splitter, into which I plug an optical mouse, a speedtouch dsl modem and occasionally a usb memory stick. 

However, the usb has started to hang while I'm acessing files, so I can't use the internet, and unfortunatly the bulit in keyboard-mouse is slightly broken. I use the laptop for my work as a graphic designer so a proper mouse is essential. 

The problem occours when accessing files. It happens when I'm using Thunar file manager or if I try to open a file from an application such as Firefox.

I think it has something to do with the computer looking for the memory stick. Ever since I named the memory stick 'G41' on a friends Windows PC, my laptop looks for it when I'm searching for files. The memory stick seems to be permenantly listed as /media/G41 no matter if it's plugged in or not. I've tried deleting this directory recursively but it keeps re-appearing.  

If anyone has had this problem before and knows how to fix it please let me know!

Many thanks

Conal

---

### Post by mvaranda on 2007-04-14
My Toshiba was working fine with 6.06 but USB started freezing after upgrading to 6.10.

The fix that worked for my machine was the following:

sudo gedit /boot/grub/menu.lst

change boot option (red):

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

I hope it helps.
Take care

---

### Post by conal on 2007-04-17
Mvaranda,

I've not had the chance to  try this - unfortunatly my laptop has started crashing  after the login screen (leaving nothing but a cursor for company). So, I'll have to fix that before I can try anything. 

The joys of old technology...

Thanks for your input!

Conal

---

