---
title: "Help me with this mice"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by firebladeavril on 2006-07-31
I am a total nOOb:( i don't know wht is my mouse's model no. but it's a logitech(bought it in 1991).In windows 98 when i checked in the device manager it said it's installed in SerialV (COM1).when i install ubuntu 5.04 everything worked fine except for the mouse.It does't move or respond in anyway.i am really annoyed.I searched on the net and got some stuff like typing "sudo dpkg-reconfigure xserver-xfree86" in the terminal but when i input this it says that xfree86 is not installed.Anyone please help .It would be really greatful.:smile:

---

### Post by Jussi Kukkonen on 2006-07-31
As a general rule I'd say you should probably upgrade to the newest Ubuntu   (6.06) unless you have a good reason not to: the device support is better.
> .I searched on the net and got some stuff like typing "sudo dpkg-reconfigure xserver-xfree86" in the terminal


In 5.04 and newer that would be 
```
sudo dpkg-reconfigure xserver-xorg
```
Not sure if it'll help -- be prepared to answer some questions about your hardware...

---

### Post by firebladeavril on 2006-08-01
well i tried it and it did work thx for ur help:D
My mouse is up and running.....

---

