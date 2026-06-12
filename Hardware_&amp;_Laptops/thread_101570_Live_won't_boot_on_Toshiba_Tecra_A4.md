---
title: "Live won't boot on Toshiba Tecra A4"
date: 2005-12-10
forum: Hardware &amp; Laptops
---

### Post by loub on 2005-12-10
Hi everyone,

I have a Toshiba Tecra A4 laptop, brand new.
I've tried to run the live CD before installing to check that everything is fine, and it's not...
If I boot without any options, I get a black screen and nothing happens.
I've tried, after looking on the forum to boot with the option
```
vga=771 noapic nolapic
```
it works better, I can see the loading screen of Ubuntu (the orange one with the logo), but then I get an error message, he can't seem to load the Server X.
The message is then partially covered in black and I get the "ubuntu@ubuntu$" command line. I'll try to copy it here if i'm quick enough ;) 

For info, the live CD I have is the official one (5.10) and I tested it on another computer, so I don't think it's the problem.

I saw other options on the forum, I'll try them and I'll keep you informed.

Thanks

---

### Post by loub on 2005-12-11
Hi,

I managed to get to the error message of the X server, and this is what I got:

(I only put the link to the image because it's a little big)

[Image]("http://terminales2001.ifrance.com/IMG_6815.jpg")

---

### Post by loub on 2005-12-11
After looking on several web pages, I edited the xorg.conf file with many different options.

The only thing thaht did work, is the vesa driver...

Now that the server X is loaded, I'll try to upgrade to the official ATI drivers...

If anyone has suggestions to do so...

---

### Post by Ana Carolina on 2005-12-12
Hi...
Were you able to fix this problem?
I was able to install ubuntu 5.10 in my toshiba satellite A45 series but I can't reboot ... I also see the black window

Ana

---

### Post by elrajrep on 2005-12-12
Ubuntu 5.10 boots on my Acer laptop with Ati X700 videocard -then "**blackscreen**".

Anyone know how to fix this problem`?

---

