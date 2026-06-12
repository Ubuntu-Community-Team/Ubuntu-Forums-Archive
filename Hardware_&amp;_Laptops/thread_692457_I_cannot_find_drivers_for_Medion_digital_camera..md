---
title: "I cannot find drivers for Medion digital camera."
date: 2008-02-09
forum: Hardware &amp; Laptops
---

### Post by Giant Speck on 2008-02-09
I need some help.

My mother gave me her old camera that she purchased at an Aldi grocery store a few weeks back.

It's a Medion MD 6136 digital camera.

I've tried to look online for drivers for it, but alas, the only drivers available are for Windows XP and earlier.

Is there anything I can do? Because I have pictures on there that I want to put on my computer.

Thanks in advance!

Jesse

---

### Post by SonicSteve on 2008-02-09
Are the pictures on a removable memory card? If they are you can use a memory card reader. I find it works better than using the camera anyhow. 
Another option is to use the preferences>hardware information program to find out what kind of chipset the camera is using. That at least helps in determining a possible driver solution. 

What I do is open the program, then plug the usb device in, then unplug it. I do that until I find the device listing. Then you can find chipset information out from the various bits of info in the listing. Once I have the chipset information I search the Ubuntu forums for other people how may have had the problems. If that fails I try searching Google, for "Linux and name of chipset" It hasn't always been very successful but it's worth a shot.

---

### Post by xeth_delta on 2008-02-09
> **Giant Speck said:**
> I need some help.

My mother gave me her old camera that she purchased at an Aldi grocery store a few weeks back.

It's a Medion MD 6136 digital camera.

I've tried to look online for drivers for it, but alas, the only drivers available are for Windows XP and earlier.

Is there anything I can do? Because I have pictures on there that I want to put on my computer.

Thanks in advance!

Jesse

Is a USB cable provided with the camera? Most likely. Look into the manual of the camera (you can search for one on the producer's website, if you don't have one), you should look for information on how to configure it to behave like a Mass storage device, when connected via USB.
That way you will not need any drivers, you will just have to connect the camera to the computer and copy the pictures.

[EDIT] You can also try to look if camera and pictures administration programs recognize it. For instance in KDE I use digikam, and my Sony camera is in the database.

---

### Post by SonicSteve on 2008-02-09
I did some looking for information about these cameras and unfortunately I came up with pretty much bupkiss. I couldn't even find a company website.
As the previous post said if it has some settings where it can be configured to act as a mass storage device that is your best bet. Some cameras do this automatically, some do it by changing a setting in the camera menus. 
If the pictures are on a removable flash card, you could for sure use a flash/memory card reader that plugs into your USB ports and read the card that way. If the pics are in the internal memory and this camera proves to be difficult, I would say install it into a friends computer and retrieve them. Then get a 256mb flash card for this thing (quite inexpensive) and hopefully your camera will automatically store them on the card. Then you can use a card reader to simply cut and paste them into a folder on your computer.

---

### Post by Giant Speck on 2008-02-09
I'll try your advice about the mass media device.

Another tidbit of information:
The camera does not use flash cards.  Rather, it uses a special, probably outdated card called a SmartMedia card.

---

### Post by oldsoundguy on 2008-02-09
there are card readers out there that are virtually universal .. 10 in 1 .. 9  in 1 .. USB.  I have a couple of them mounted in Linux boxes and they read all kinds of stuff (most of my stuff is SD or CF) and ARE supported.  The KEY is not only can the card be READ, but where are you sending the picture.  Gimp is great as an editor and, of course, it is free and already IN the Ubuntu program ready to be installed.

---

### Post by SonicSteve on 2008-02-09
I can't speak for it's quality but... this one reads smart media. 

Tigerdirect
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1431862&CatId=942](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1431862&CatId=942)
or if you prefer amazon (this is the UK site)
[http://www.amazon.co.uk/SmartMedia-Cards-Memory-Readers/b?ie=UTF8&node=564502](http://www.amazon.co.uk/SmartMedia-Cards-Memory-Readers/b?ie=UTF8&node=564502)

---

### Post by SonicSteve on 2008-02-09
> **Giant Speck said:**
> I'll try your advice about the mass media device.

Another tidbit of information:
The camera does not use flash cards.  Rather, it uses a special, probably outdated card called a SmartMedia card.

These from what wikipedia says are some of the first Flash memory cards. They just didn't catch on. If the smart card can come out and the pics are indeed on it all you'll need is a card reader and you'll be off to the races.

EDIT
I bet one of the reasons they didn't catch on was there size and price.  I recently bought a 1gb Micro SD card for the same price as I've seen for a new 128mb smart media card. Yikes! Perhaps this is one of those special cases where demand for a retired technology has kept it's price high.

---

### Post by Giant Speck on 2008-02-11
I figured out the solution to my problem.

I had the camera set to PC Camera mode.

In order to use it as a mass storage device, it must be in a different mode when connecting it to the computer.

---

### Post by xeth_delta on 2008-02-11
> **Giant Speck said:**
> I figured out the solution to my problem.

I had the camera set to PC Camera mode.

In order to use it as a mass storage device, it must be in a different mode when connecting it to the computer.

So, it is working now, isn't it? Great! In that case, please mark the thread as solved.

---

