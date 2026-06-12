---
title: "Help! My usb is not detected!"
date: 2008-09-29
forum: Hardware
---

### Post by karagorge on 2008-09-29
I have a big problem. Today when i inserted my usb apacer my ubuntu didn't find it so i tried to connect my mp4 player but it wasn't found as well. Before i inserted them both on the same usb port i connected the printer. Can the printer be the problem? I tried connecting the mobile phone and it worked. Why the usb and mp4 won't work? What should i do? Please help...

---

### Post by Herman on 2008-09-29
Try opening Gnome Partition Editor without the USB devices plugged in.
You might have to install Gnome Partition Editor if you don't already have it installed,
```
sudo apt-get install gparted
```Then open GParted (also called Gnome Partition Editor), 'System'-->'Administration'-->'Partition Editor'.

With Gnome Partition Editor open, plug in your USB device and click 'GParted'-->'Refresh Devices', or press 'ctrl'+'r' keys.

Try that and see if it helps.

---

### Post by karagorge on 2008-09-29
I installed the Gpartitioner and pluged the usb. I refreshed it like 10 times but the usb wasn't found. Thanks anyway...

---

### Post by Herman on 2008-09-29
Okay, sorry, it worked for me once, maybe I was just lucky.

Do they show up in the output from the command 'sudo fdisk -lu'?
```
sudo fdisk -lu
```

Do they have an LED light and does it light up?

---

### Post by karagorge on 2008-09-29
I have tried the code and it showed my hard disk and some partitions from it. Yes the usb has little LED light and it flashes once every 5 seconds. The mp4 charges perfectly throught the usb but the ubuntu can't find it.

I am begginer in ubuntu. This is my first run. Can i have done something to disable the usb? On the same usb port my printer and my phone worked.

Yesterday my usb worked...

---

### Post by Herman on 2008-09-29
Well my wife's USB did something like that a few days ago because she left her laptop running until it ran out of batteries. I was afraid the USB was dead too there, for a while, but I was lucky, it magically came back to life again when I tired that GParted trick I already told you about. Sorry it didn't work for you though. I was hoping it would.

The main thing is not to just unplug yor USBs, but to right-click the icon first and click 'unmount', so if there are files queued up wating to be written to the disc, (like cars at an intersection waiting for a green light), they will be written to disc and finished and the file system's journal can be updated and closed properly.

Apart from that I don't know what could be wrong.
I think you should do some experiments to try to find out, like see if the same USB will work in some other computer maybe, or is it just Ubuntu? Or just Ubuntu in this computer, or is it always this USB device, no matter what computer or what operating system you plug it into? Or is it the USB port? (Tyr plugging it into a different port).

If the light is flashing that is a good sign, there is hope.

---

### Post by DeeZiD on 2008-09-29
I have the same problem.
The only way to work around seems to disable ehci_hcd (the fullspeed USB2.0 driver) :(

Try the following:```
rmmod ehci_hcd
```

---

### Post by Herman on 2008-11-25
> Try opening Gnome Partition Editor without the USB devices plugged in.
You might have to install Gnome Partition Editor if you don't already have it installed,
     Code:
     sudo apt-get install gparted 
Then open GParted (also called Gnome Partition Editor), 'System'-->'Administration'-->'Partition Editor'.

With Gnome Partition Editor open, plug in your USB device and click 'GParted'-->'Refresh Devices', or press 'ctrl'+'r' keys.:) That trick has worked for me again and fixed two more USB flash memory sticks that I though were dead for sure.
Sometimes it takes a lot of repeated attempts, and I don't know why this works, but don't throw away your old 'dead' USB flash memory sticks too soon.
They may eventually come back to life if you keep on trying.

Regards, Herman :)

---

### Post by gutorjo on 2008-12-06
I have a notebook running Ubuntu 8.04. When I attach an external HD in one USB it works fine. If I change the HD to another USB, its not recognized. I want to use two pendrive, but its not working. When I boot on windows, all USB works fine.

---

