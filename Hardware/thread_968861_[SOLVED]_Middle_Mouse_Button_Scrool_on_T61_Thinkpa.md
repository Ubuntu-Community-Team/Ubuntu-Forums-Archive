---
title: "[SOLVED] Middle Mouse Button Scrool on T61 Thinkpad"
date: 2008-11-03
forum: Hardware
---

### Post by era86 on 2008-11-03
Greetings!

I tried following the tutorial I found on the T61 wiki for 8.04 to get my middle button to work as a scroll button, but it doesn't work on Xubuntu 8.10.  Does anyone know how to get this working?  Thanks in advanced

---

### Post by era86 on 2008-11-03
Bump.  Anyone know how to do this?  I tried editing xorg.conf and restarting, but it doesn't work.

---

### Post by Whoopie on 2008-11-03
If you use Intrepid, have a look at [http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Scrolling_with_Trackpoint)

---

### Post by era86 on 2008-11-03
Thanks Whoopie for the reply.  I managed to do some searching to find out how to get it to work.  After following the link:

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Scrolling_with_Trackpoint)

But, the middle trackpoint quits after suspend/hibernate.  I managed to fix this by doing the following:

> 



Ok, just to make this clear for those attempting to apply this patch,
follow these instructions, the instructions I gave above was for
getting a version from git where this problem doesn't exist.

sudo apt-get build-dep xserver-xorg-input-evdev
apt-get source xserver-xorg-input-evdev
cd xserver-xorg-input-evdev-2.0.99+git20080912
patch -p1 < /path/to/preinit.diff
./autogen --prefix=/usr
make
sudo make install

Restart the X server.

Post results here along with the problem you were experiencing before
the patch and any eventual problems after the patch.



---

### Post by David_G_D on 2008-11-18
I'm trying to follow the above instructions, but I can't find the file preinit.diff anywhere on my file system.  Do I have to create that file, of is it in a place where "find" won't be able to see it?

Thanks in advance,
David

---

### Post by russlar on 2008-11-18
Try this:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61#Emulate_Wheel_.28Middle-click_scrolling.29]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61#Emulate_Wheel_.28Middle-click_scrolling.29")

>   Emulate Wheel (Middle-click scrolling)

Michael Vogt described how to get middle-click scrolling to work again in Intrepid. Xorg.conf is not used to configure mice and keyboards anymore, but evdev is. This makes the configuration of middle-click scrolling a little bit different than previous versions of Ubuntu. In terminal:

sudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi

Past and save the following code, which will give vertical wheel emulation only:

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>


---

### Post by aspanis on 2008-11-18
it also worked for me on a X60s
thanx !!!

---

### Post by gustav.franzsen on 2008-11-21
Works like a charm for my Z60m and Intrepid

Thnx!!

---

### Post by arielt1985 on 2009-01-06
> **russlar said:**
> Try this:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61#Emulate_Wheel_.28Middle-click_scrolling.29]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_8.10_(Intrepid_Ibex)_on_a_ThinkPad_T61#Emulate_Wheel_.28Middle-click_scrolling.29")

I followed these instructions, and the middle button scroll doens't work on my X32. Should I install something else? I'm using hardy.

Thanks,
Ariel

---

### Post by oldguy51 on 2009-01-12
My thanks to russlar also, it worked for my T23.  I spent about 4 hours reading before I found a fix that worked!

---

