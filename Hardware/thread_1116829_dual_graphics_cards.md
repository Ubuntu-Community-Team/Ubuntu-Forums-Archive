---
title: "dual graphics cards"
date: 2009-04-05
forum: Hardware
---

### Post by ipburbank on 2009-04-05
My rig has an abit ip35 pro, and in the master graphics card slot I have a geforce 9800gx2. I tried to put the slave card in, being a e-geforce 9600 GT but upon doing so ubuntu boots, I can see the loading bar, but then asks me for my username/password in a shell. The command

```
startx
```

tells me that the server has had a fatal error, being there is no display. I would love to run both of these at the same time, and infact the live cd and windows run fine.

~Any help is appreciated, Istvan.

---

### Post by elysion on 2009-04-05
Have you tried running sudo dpkg-reconfigure xserver-xorg? If you are lucky that might help. What do you have in your /etc/X11/xorg.conf? I guess you could get the setup working by editing that.

Here's what I have in my xorg.conf: [http://pastebin.com/m6966b171](http://pastebin.com/m6966b171)
Hope that helps!

-elysion

---

### Post by ipburbank on 2009-04-05
while i was stuck in that bash thing I did try that, to no avail.

However note that by removing the second card I was with no further changes able to boot into my system as usual.

---

### Post by elysion on 2009-04-05
Which version of ubuntu are you using? Can you post the xorg.conf somewhere?

---

### Post by norwoods on 2009-04-05
nvidia has an extensive README for each driver version.  google nvidia REEADME driver.version (google nvidia 185.13) to find a README.  the nvidia 185.13 driver is in intrepid main repository for now.

---

### Post by ipburbank on 2009-04-05
Here is my xorg: 

[http://pastebin.com/f4197bf12](http://pastebin.com/f4197bf12)

Is it the graphics driver that is doing it? I un-installed the driver before inserting the new card...

---

