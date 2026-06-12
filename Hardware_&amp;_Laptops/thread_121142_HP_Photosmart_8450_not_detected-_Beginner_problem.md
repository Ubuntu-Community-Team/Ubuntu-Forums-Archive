---
title: "HP Photosmart 8450 not detected- Beginner problem"
date: 2006-01-24
forum: Hardware &amp; Laptops
---

### Post by ras on 2006-01-24
Not sure this should go in Beginner talk or not...

I'm new to Linux and can't get my local usb attached HP Photosmart 8450 printer to print.  I added it through:  System -> Administration -> Printing, and selected the HP Photosmart 8400 series through the menus.  I even downloaded the driver (hpijs.ppd) into my home directory and pointed to it after hitting the "install driver" button.

Now, the printer properties show that it is "ready", but under the connections tab, it shows the printer port as: "hp no_device_found".  Also, the box showing detected printers indicates that no printer is detected.

Did I put the driver in the wrong place, i.e. does it need to be in a specific depository?

Please help.

---

### Post by Turin Turambar on 2006-01-24
Sorry, I don't own that printer and can only advise you to try different settings and connections. But first, be sure that the installation of driver was successful. I have a Canon i350 printer and when I had to specify the connection method, I chose USB. I was wrong - it was USB/LP0!

---

### Post by MetalMusicAddict on 2006-01-24
I have this printer. I bought it because it works great with linux and you can even enable all the advanced settings like in windows with it. Im still working on this though because its connected to the server Im rebuilding.

You shouldnt need to download anything. After you tell it what make and model it will default to **hpijs.ppd** in a little dropdown box. Thats what you want. It shouldnt download anyplace.

Ill post back if you still have the problem. Its late here. :)

---

### Post by ras on 2006-01-25
[QUOTE=MetalMusicAddict]I have this printer. I bought it because it works great with linux and you can even enable all the advanced settings like in windows with it. Im still working on this though because its connected to the server Im rebuilding.

You shouldnt need to download anything. After you tell it what make and model it will default to **hpijs.ppd** in a little dropdown box. Thats what you want. It shouldnt download anyplace.

Ill post back if you still have the problem. Its late here. :)[/QUOTE]
It's still not working.  Maybe it is because it is low on ink.  In windows, a warning message about low ink pops up, but still prints ok.  In ubuntu, nothing happens.  It says the job is printing, but really its not.

---

