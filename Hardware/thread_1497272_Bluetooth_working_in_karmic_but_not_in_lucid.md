---
title: "Bluetooth working in karmic but not in lucid"
date: 2010-05-30
forum: Hardware
---

### Post by bOiKIDZ on 2010-05-30
I have my built in bluetooth device(Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode))  in my laptop. To power on the bluetooth device, im pressing fn + F12. It is working in windows XP and Ubuntu 9.10 Karmic but i cant power it on in Ubuntu Lucid. All the operating system I use are 32bit.


Having blueman and Gnome bluetooth manager causes the problem. I removed blueman and restarted the bluetooth by 
sudo /etc/init.d/bluetooth restart

---

### Post by bOiKIDZ on 2010-05-31
update. I have updated the kernel from 2.6.32-21 to 2.6.32-22 and I can now enable my bluetooth device but It is not detected by bluetooth manager or if it is detected, the bluetooth in tray is continuously blinking.

---

### Post by ajayramak on 2010-09-04
Hey.

I have encountered the same problem with gnome bluetooth manager and Blueman. I found a trick to work with, but it would be better if somebody gives a permanent solution. Keep the bluetooth off by  hardware, open the properties of the gnome bluetooth manager( right click on the icon in the indicator applet), you will see a huge button with 'Turn Bluetooth On', press that and immediately switch your bluetooth on by hardware(by pressing F12 I suppose, cause I have a Dell Inspiron with a separate switch). I must work. I did for me.

Hope this will work.
Again I maintain that if someone got a proper fix, it would be better.

Ajay

---

