---
title: "Intel 852MG w/ 800 x 600 resolution"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by abijah on 2006-08-18
I have a laptop with a Intel 852MG chipset.
The native resolution is 800 x 600, but with winXP installed i normally get 1024 x 768.

I downloaded "dri-I915-v1.1-20041217.i386.rpm" from intel.
then i did
```

sudo apt-get install alien
sudo alien <filname.rpm>
sudo dpkg -i <filename.deb>
sudo apt-get update
sudo apt-get upgrade

```
and used the installer to get "915resolution"

Thanks to [http://absolutebeginner.wordpress.com/](http://absolutebeginner.wordpress.com/)

but i still can't get a 1024 x 768 screen resolution

---

### Post by Derek Djons on 2006-08-18
The problem might be hidden within 915resolution. The little app is script based which means you have to edit a config file. 

Did you just install 915resolution and let it be or did you also tried configuring it?

---

### Post by abijah on 2006-08-18
I just let it be.

---

### Post by patrickfromspain on 2006-08-18
I have toshiba L10 with an intel 852gm and ubuntu set up 1024x768 just fine.

---

### Post by Derek Djons on 2006-08-18
> **abijah said:**
> I just let it be.

I just read your message but I can't reply the whole procedure right now (late, sleep, work). I will write down what you have to do tomorrow. 915resolution is a small app with a config file which has to be edited. But where and when I will post that tomorrow here (unless someone beats me to it).

---

### Post by Derek Djons on 2006-08-19
Sorry for the delay but here it comes:

To setup 915resolution you have to do the following terminal work:

```

$ sudo 915resolution -l

```

The output you will receive in the terminal is quite simple. 915resolution determines the graphical chipset and it's capabilities. Than it presents you with modes which you can select. 

Before you select a mode you have to edit the 915resolution config file. There you have to write down which modus you are going to use (for example 5c) and specify the resolution (for example xreso means the horizontal resolution and yreso means the vertical resolution 1400x1050) and bit (for example 16-bit, 24-bit or 32-bit).
```

$ sudo gedit /etc/default/915resolution

```
After you have saved the file there's only one thing left to do, selecting the mode using 915resolution itself.
```

$ sudo 915resolution mode xreso yreso

```

After the patch is complete the only thing you have to do is restart GDM (Graphic Display Manager) using CTRL + ALT + BACKSPACE or restart Ubuntu Linux and login again. It should work then!

Please let me know if it works!

NOTE: It may occur that 915resolution displays modes which your notebook can't use technically. So if your max. is 1024x768 don't patch it to 1400x1050. It will either crash your xserver-xorg or in the worst case it can damage your graphical card / screen.

---

