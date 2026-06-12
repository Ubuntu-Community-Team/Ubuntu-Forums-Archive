---
title: "Dell Inspiron Duo Touch Screen"
date: 2010-12-28
forum: Hardware
---

### Post by Non.Cents on 2010-12-28
I got a new Dell Duo for Christmas and have installed Ubuntu Netbook 10.10 on it. It runs great..... if this were a regular netbook. What does not work is the touch screen. Every touch on the screen goes to the top left corner. This is not an unheard of issue (I have read other threads) but found no real solution. The accelerometer does not seem to work either, but as I have read that is a driver issue and I am not sure if the drivers exist yet for Ubuntu.

The windows 7 install this comp comes with is sluggish and ungainly. Ubuntu is sexy (and its ubuntu :P), and would be more so with the touch functionality.

Thanks in advance

---

### Post by Non.Cents on 2010-12-28
I found the answer on another thread [here]("http://ubuntuforums.org/showthread.php?t=1628232&page=8") for anyone who is interested,

> Re: Who Plans on getting a Dell inspiron Duo and installing Ubuntu?
Looks like some other people have the same issue with the eGalax Touch Screen and ubuntu. There is a document on how to get it work here.. I am still playing with it

[http://ubuntuforums.org/archive/index.php/t-1613000.html](http://ubuntuforums.org/archive/index.php/t-1613000.html)

Got it to work!

Login and open termina
Type sudo gedit /etc/default/grub
find the line that says
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Replace with: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0x0eef:0x725e:0x40"

Save and close geditor.
Run sudo update-grub
Reboot.. Everything is working
__________________
--Shartke
Last edited by shartke; 13 Hours Ago at 04:41 AM.. Reason: Fixed it 

---

### Post by robertjan88 on 2010-12-31
> **Non.Cents said:**
> I found the answer on another thread [here]("http://ubuntuforums.org/showthread.php?t=1628232&page=8") for anyone who is interested,

Im also considdering buying the duo. Does it fully function now with multitouch and as pad?

Thanks!

---

### Post by Non.Cents on 2010-12-31
No, not yet, but single touch does work. still ironing out a few minor kinks but I personally think its pretty cool. Check [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1628232") for some comments from others who have the device, and the ironing out of the touch issue.

---

### Post by Kirboosy on 2011-01-04
Here is the new thread. [http://ubuntuforums.org/showthread.php?t=1658635](http://ubuntuforums.org/showthread.php?t=1658635)

Hopefully you find it helpful. :)

---

