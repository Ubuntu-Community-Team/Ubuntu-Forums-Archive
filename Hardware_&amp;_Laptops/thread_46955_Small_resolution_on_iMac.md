---
title: "Small resolution on iMac"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by 1lowprixgt on 2005-07-06
I had this old 333 iMac just sitting here with OS 8.1, so I decided to do something useful with it and install Ubuntu when my new cd's came. The installation went very smooth and ran into no errors... Until it actually booted. All of the programs seem to work normally and smooth as far as I can tell. My only problem has been with the screen resolution, which was one of the first things i went to adjust. When I got into it, and went to change the size, it only allowed one size... 512x384. I know the iMac's are capable of up to 1024x768 (what I was running 8.1 with). I have searched and searched for a suitable driver, but cannot find anything. Does anybody have any suggestions as to what I can do before i completly loose it?  ](*,) .

Thanks,
Josh

---

### Post by 1lowprixgt on 2005-07-12
yea... *thanks everyone for your help*...  :roll: (*yea, right*...), but I have solved the problem myself!

if anyone is having the same problems with mac's running a small screen resolution and run across this post... here is what i did:

Ctrl+Alt+F1
login username & password
(type) sudo nano /etc/X11/xorg.conf
scroll down to "Screen"
change DefaultDepth to 16 rather than 24.
Ctrl+X
Y to save
Ctrl+Alt+F7
Ctrl+Alt+Backspace

This has since changed my iMac's resolution to a wonderful 1024x768.  \\:D/ 

Now it is actually useful for something! 

THANKS UBUNTU!  :grin:

---

