---
title: "No direct rendering on other display"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by argie on 2007-07-02
I just installed the stock Ubuntu 7.04 Feisty Fawn and then updated and upgraded. I can use desktop effects just fine, and everything works well. The problem comes when I switch users. When I switch users, the second user who logs in doesn't have direct rendering and as a consequence I cannot run Desktop Effects (If I do, I get a blank white screen on logging in and rotating the cube is slow, and all the sides of the cube are blank).

I use a Compaq NX 7300 and the graphics are on-board Intel 945. Is it possible for me to get direct rendering on the other displays as well? Typing "glxinfo | grep direct" on the second screen says "Direct Rendering: No"

While the other user is logged in the first user still has direct rendering.

---

### Post by prshah on 2007-10-08
Hi I was running into the same problem. I made a little change to my /etc/X11/xorg.conf file: 

===
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true" ==> added these 
	VideoRam	131072                             ==> two lines
EndSection
===
Now both users can use "desktop effects". But note that before adding these lines, neither user could use "desktop Effects"-- white screen result.

An additional point; I am using the updated intel drivers.. not i810. How do you update the drivers? Well I forgot, but these forums contain the answer. sudo apt-get install *something...*

Hope this helps
Cheers

---

