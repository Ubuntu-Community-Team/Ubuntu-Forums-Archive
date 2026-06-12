---
title: "Wacom Bamboo 9.04 Installation problem."
date: 2009-10-14
forum: Hardware
---

### Post by Rany Albeg on 2009-10-14
Hi all , 

Just bought a new wacom bamboo pen.
Before i bought the tablet i was looking in many threads and reading a lot about how this tablet works in Ubuntu Jaunty.

I plugged the tablet using USB cable into my Dell Inspiron laptop.
There is a light coming from the tablet near the active area , so i understand it is working properly.

Im very confused.
I dont know if it is a driver problem or just a configuration issue.

Im using Ubuntu 9.04 with 2.6.28-15-generic kernel.

----

I keep a lot of important stuff in my laptop so i decided to give it a try and install the linuxwacom-0.8.4-3 ( the latest one as i seem to understand ) driver on my second -not-so-important-old computer.
Following a tutorial i edited the /etc/X11/xorg.conf file with the wanted features and now when i restart the computer i can only log in using the terminal , which is fine for me to fix the problem and restore the settings i've changed , since i backed up xorg.conf.
But now the screen turns black and i cant see what im doing.

Well , i dont really care of the above problem , i just want to be able to use my bamboo with Ubuntu 9.04 in a safe way without messing up my laptop because i keep a lot of important data ( i'll always use backups but dont want to reinstall and fix the computer while the main problem now is the Wacom tablet)
 
I know that there are many tutorials about it but , really , i just cant understand what to do and get really confused as i read more about it.

Please , give me a direction and briefly explain me the problem.

Thank you very much in advance.
Have a nice day.

---

### Post by Favux on 2009-10-14
Hi Rany Albeg,

While you can use the xorg.conf in Jaunty you're "suppose" to use the HAL/.fdi method.  Using the xorg.conf means you'd give up usb hot plugging.  Also the xorg.conf can be tricky in Jaunty.  The syntax has to be just right.

What model of Bamboo did you buy?  It might be new enough that it isn't yet supported by the linuxwacom drivers in Jaunty.  Even new enough that the new 0.8.3 doesn't support it.

The Vendor ID should be Wacom = 056a.  So what is the Product ID?  Try in a terminal:
```
lsusb
```
and you could look in lshal using Find = wacom:
```
lshal>lshal.txt
```

---

### Post by Rany Albeg on 2009-10-15
Hi, Favux.

Thank you for the quick response.
The command's output seems to be fine :

```
lsusb | grep -i wacom :

  Bus 006 Device 007: ID 056a:00d4 Wacom Co., Ltd 

cat lshal.txt | grep -i wacom :

  info.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor = 'Wacom Co., Ltd'  (string)
```

As i mentioned before : it will be nice of you for giving me just a good direction / a source where i can follow a manual which will help me solve the problem.

Thank you very much.

---

### Post by Favux on 2009-10-15
Hi Rany Albeg,

As I thought your new Wacom Bamboo Pen (Product ID 00d4) isn't supported by linuxwacom yet.

The closest to a manual I can direct you to is this thread:  [http://ubuntuforums.org/showthread.php?t=1290251](http://ubuntuforums.org/showthread.php?t=1290251)  We are trying to add your Bamboo and the 00d1 to linuxwacom.  We are almost there.  With luck 0.8.4-4 will support your tablet.

Hope this helps.

---

### Post by Rany Albeg on 2009-10-15
Hi Favux.

I guess i will wait in patient till the above driver will come.
So I'LL BE BACK!

I want to thank you very much for helping me and other people in the Ubuntu community ( as i can see in many posts ).

Have a nice day :)

---

### Post by Rany Albeg on 2009-10-15
Hi again , 

I decided to install VBox and give it a try.
So i installed Win XP and the driver for the tablet.

I visited every link in google ( "USB device 9.04 ubuntu wacom...").
I tried all(!) solutions but without success.
Win XP refuses to recognize my tablet.

So i was wondering if because of the fact that the Wacom isn't supported yet on my Ubuntu , it can not share the device with other OS.

What do you say guys? Favux?

Thank you.

---

### Post by Rany Albeg on 2009-11-19
*bump*

Hi again.
Well , i moved to 9.10 and i still have the same problem.
I thought that it will recognize the device and it will work , but i just cant work with my tablet on Ubuntu 9.04 or 9.10 and it is very annoying.

So , after a month , im back to ask you guys if you know about a new way to solve this problem.
I searched for a solution and i still dont see a way to get my Bamboo to work.

Thanks.

---

### Post by Favux on 2009-11-19
Hi Rany Albeg,

You can use the link above to go to post #2 which has the link to kgingeri's HOW TO.  That will get the stylus, stylus buttons, and the eraser working.

On a new experimental thread we now have everything working!  We're fine tuning it right now.  See this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1321238").  Remember this is even more experimental than the first thread.

---

