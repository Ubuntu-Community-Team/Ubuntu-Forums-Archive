---
title: "how do I get my LCD flat pannell monitor to work?"
date: 2008-10-16
forum: General Help
---

### Post by princerameses on 2008-10-16
... it's e-machines.

using tinyme linux.

---

### Post by shawnrgr on 2008-10-16
Thats not nearly specific enough, what have you done so far? Are you getting x errors? Model number of monitor? Max screen resolution.

---

### Post by princerameses on 2008-10-16
Model: 500pw
Produst #: E15t4w

Maximum resolution? I don't know.

I don't know if there's any eroors, because I can't see anything. the screen is black. (I think it says something like no signal imput or something like that)

---

### Post by princerameses on 2008-10-17
[http://s4.tinypic.com/314cjgh.jpg](http://s4.tinypic.com/314cjgh.jpg)

I changed it to the flat pannel one for 1024 x 768 and got something on the flat screen monitor, but it was just the dialod box asking tif I want to keep the changes. The background was multi- colors so I said no.

Which one do I choose, or must I do something else?

---

### Post by shawnrgr on 2008-10-17
If your getting multicolored blocks on the screen then you probably haven't installed nvidia/ati drivers... did you install all the restricted drivers that were available to you after install?

---

### Post by princerameses on 2008-10-17
No I didn't. What drivers do I need and how do I get them? I am not familiar with TinyMe, so try to be specific please. =)

---

### Post by princerameses on 2008-10-17
Oh, and how do I change my mouse pointer in PC Linux OS? Anyone know?

---

### Post by princerameses on 2008-10-17
still need help. =)

---

### Post by ronnielsen1 on 2008-10-17
A monitor should just work. I'd be more inclined to think we either have a bad monitor, a bad video card or something is not connected. Is there another computer you can test this on?

---

### Post by shawnrgr on 2008-10-17
I get multicolored blocks on my 24in if I don't have nvidia-gls installed.

---

### Post by princerameses on 2008-10-17
Ok, so under graphical card or server (I don't remember what it says) I go to NVIDIA, and then what one do I choose? Am I on the right path.


My monitor works fine with windows, it's just any linux distro that it says "frequency out of range". It's a black screen with those words. But I adjusted it to to "flat panel monitor and I saw the dialog box, but there was a multi-colored background.

---

### Post by rmjohnson144 on 2008-10-17
> **princerameses said:**
> [http://s4.tinypic.com/314cjgh.jpg](http://s4.tinypic.com/314cjgh.jpg)

I changed it to the flat pannel one for 1024 x 768 and got something on the flat screen monitor, but it was just the dialod box asking tif I want to keep the changes. The background was multi- colors so I said no.

Which one do I choose, or must I do something else?

If you were able to read the dialog box I'd think you need to say yes.  maybe the background is supposed to be grabled?  But if you can read the type, then I'd think you should go from there and then install the drivers.  

Go to nvidia or was it ati and download the linux driver and install it, they should have a good install text file.

If I remeber correctly I just downloaded the driver to my desktop then opened up a terminal window and typed

sudo cd Desktop
sudo sh ./name_of_nvidia_driver.run

and then it installed.  I had a little trouble with my ATI driver install and I ended up installing envyng and it installs the latest drivers for you.

Good luck
-=Mark=-

---

### Post by princerameses on 2008-10-17
Ok, is that all I need to know, or is there going to be other options for downloading? I have NVIDIA stuff on here:

[http://s4.tinypic.com/3ts83.jpg](http://s4.tinypic.com/3ts83.jpg)

---

### Post by princerameses on 2008-10-17
This needs bumping.

---

### Post by princerameses on 2008-10-17
An error occurred:
(EE) No devices detected.


Try to change some parameters

What does this mean? o.O

I tried to change the graphic card to NVIDIA GeForce FX.

What do I need to do? *cry*

---

### Post by princerameses on 2008-10-17
Ok, it's working now. (I went ahead and tried some stuff myself since help was slow) But it's squished. I need the reolution: 1280 x 800 and that's not a default res.. If I go to 'other' then I get an option for 1280 x 800, but there's another number there, too. 16 or something. What does that mean? It didn't work when I tested it.

---

