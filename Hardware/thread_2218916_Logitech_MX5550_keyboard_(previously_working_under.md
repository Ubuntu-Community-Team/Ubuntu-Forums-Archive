---
title: "Logitech MX5550 keyboard (previously working under older versions) broken in 14.04"
date: 2014-04-22
forum: Hardware
---

### Post by Not_Comfortable on 2014-04-22
So I've been using a Logitech Revolution MX5500 keyboard and Mouse combo for 5-6 years without issue, including with versions of Ubuntu dating back to the 12.x releases. The connection uses a USB 2.0 dongle with some sort of proprietary wireless or bluetooth implementation to connect like all logitech peripherals. I went ahead and wiped my 13.10 build and did a fresh install of 14.04, but got to the username/password setup screen and noticed a problem. All lowercase keys and numbers work just fine, however when I hold shift, only some of the keys will become uppercase and only some of the symbols will work. When this occurs, it doesn't put in the lowercase or number version, it just doesn't detect a stroke so it's blank. 

A specific example of this occurred when I was entering my city. I went to type "Washington, DC", but it wouldn't recognize the uppercase D. I solved that problem by just using the capslock and figured it was a result of a little setup screen bug. 

then I got to my password, and setup one containing an exclamation mark (!). The number 1 worked just fine, but holding shift to create the exclamation mark didn't work. Of course, in this case, capslock could not solve it. I went ahead and created a simple password and finished setup, hoping I could just change it after the fact.

Upon logging on to my new build, I opened up gedit and did some testing. All of the same problems from the setup manfiested themselves there. It's not a random problem, as only specific keys don't work when holding the shift button. 

I pulled out a wired usb logitech keyboard and am using that for now, but this keyboard sucks compared to the MX5500, so I'd like to find a solution. I've googled bugs relating to that model endlessly but have found nothing. I also tried pulling the batteries, resycning the connection and changing the usb port the dongle uses. Being such a specific model of keyboard and such a new release of ubuntu, there hasn't been much in the way of finding other people experiencing the problem. 

I'm still using the mouse from the combo and that dongle without issue. 

Did something change with the usb drivers/keyboard detection with this release? I'm setup for U.S. English style keyboard by the way. If this post would be better suited for another subforum, please let me know and I'll move it. 



Thanks!

edit: I should add, I'm running on physical hardware utilizing an Intel i7-3930k, Asus P9X79 DELUXE mobo, Corsair SSD drive, 16GB memory and an AMD 6950 GPU. This system has been functioning fine for 2.5 years with Ubuntu.

---

### Post by cincibluer6 on 2014-04-30
There has got to be something. I am using an M525 mouse and it just stops working randomly and won't restart til I put the receiver in another port.
I think something recently borked the USB support for stuff like this. It definitely is Ubuntu though as I dual boot Win7 on it and that is still perfectly fine with the mouse.
Also, using lsusb still has the Logitech receiver listed even when it stops.

Subscribing.

---

### Post by trag on 2014-04-30
Dry installing 'Solaar' logitech unified bluetooth driver for Linux, it may help.
sudo add-apt-repository ppa:daniel.pavel/solaar

sudo apt-get update && sudo apt-get install solaar



Those using GNOME Shell should swap the last command for:



sudo apt-get update && sudo apt-get install solaar-gnome3

good luck
trag

---

### Post by cincibluer6 on 2014-05-04
Thanks mate. Plugged it into my Windows desktop for a bit and now it seems to work fine back on my laptop. Will try the BT driver if the issue arises again.

---

### Post by mcse2000ca on 2014-05-04
Done this and says no logitech receiver found.
What happened to the hidpoint project so we can have a graphical setup tool instead of manipulating text files for this.

---

