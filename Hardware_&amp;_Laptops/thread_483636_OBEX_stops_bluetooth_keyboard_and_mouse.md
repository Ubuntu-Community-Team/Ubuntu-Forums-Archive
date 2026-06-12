---
title: "OBEX stops bluetooth keyboard and mouse"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by karlhm76 on 2007-06-24
Hi everyone,

I have a reasonably fresh install of Feisty and everything is almost working just the way I had it before. However I have just added the ability to copy files to and from my mobile phone via bluetooth. I installed gnome-bluetooth and the obex library to do this.

I restarted bluetooth and now I have the ability to right click on a file and choose send to bluetooth (obex). However when I do this my bluetooth keyboard and mouse immediately stop working, even if I don't copy anything. All I have to do is open the send-to window and they stop.

I know it is a bluetooth issue because I can connect a regular PS2 or USB keyboard and mouse and they work. OBEX is stopping my bluetooth keyboard and mouse from working. It's as if it is taking control of the bluetooth adaptor from the keyboard and mouse.

If I open a terminal and try sudo hcitool scan or sudo hidd --connect, both don't find anything. hcitool  displays a connection timeout error, and hidd seems to do nothing - although its probably getting the same timeout error.

Can anyone help?

---

