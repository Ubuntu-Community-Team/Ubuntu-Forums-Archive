---
title: "No GUI.."
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by dropstitch on 2007-05-22
Hello there.. I've just attempted to install Ubuntu Studio on my Acer Aspire 7112Wsi laptop. This is my first Linux installation, but I've ran a LiveCD of Kororra XGL on this machine before, so I know my graphics card (an Intel GM45 Mobile Chipset) is supported.

My problem is, as soon as I boot into it, it doesn't give me any error messages.. instead it boots straight into a command line interface rather than going to the GUI. Is there any way to load drivers onto it.. or force it to load the GUI? This is very frustrating and I'd appreciate any help anybody can offer!

Thanks =]

---

### Post by dropstitch on 2007-05-23
So much for support.

---

### Post by Jussi01 on 2007-05-23
Hi, 

Usually its polite to wait at least 24 hours for support - this way you make sure everyone around the world has had a chance to take a look. 

As to your question, try typing

```
 startx
``` 

at that command line. it maybe you graphics drivers are not working properly, so if that doesnt work, try:

```
sudo dpkg-reconfigure xserver-xorg
```

and select the vesa driver when asked. If you are unsure of any of the questions answer the default.

Hope this helps

Jussi

---

### Post by dropstitch on 2007-05-23
Hey there, apologies for the short temprement, this is getting really frustrating now.

Thanks for your help, but unfortunately it hasn't really done anything.

When I typed in xstart it gave me this error..

```

-bash: startx: command not found

```

..and when I typed in..

```

sudo dpkg-reconfigure xserver-xorg

```

..I got this!

```

Package "xserver-xorg" is not installed and no info is available.
Use dpkg --info (= dpkg-deb --contents) to list their contents.
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg is not installed.
carl@ubuntulaptop:~$

```

Argh this is really getting to me now =[  .. can anybody help?

Again, I'm using an Intel 945GM Graphics Chipset, which I know Linux supports. I have the RPM? file format of it's drivers, and a how-to guide of how to convert it using an "alien" command to get it to work with debian/Ubuntu, but as it's in command line mode I've no idea how to get it into the file system or install it, let alone configure it =[

Any help appreciated!

---

### Post by Jussi01 on 2007-05-25
Hmm, really sorry I havent been back sooner. It sounds as though you didnt finish installing the stuff from the disk. Could you try installing again as it sounds like you have only installed the base part of things. (not the gui.) there are 2 parts of the install, the base and then the part where you select audio, graphics video or all 3. 

So yeah, try installing again and make sure it completes all the way.

Ill check this thread regularly to make sure your helped as much as possible.

Jussi

---

### Post by discmaster on 2007-05-25
> It sounds as though you didnt finish installing the stuff from the diskSounds like that; I would suggest the same, run the install again, take your time & ensure that it go the whole way to finish.

Good Luck! :)

---

### Post by btesec on 2007-05-28
> **discmaster said:**
> Sounds like that; I would suggest the same, run the install again, take your time & ensure that it go the whole way to finish.

Good Luck! :)

I think the problem is the video card since I have the same problem.  check this wiki at the Ubuntus Studio site it guides u through the installation [https://help.ubuntu.com/community/UbuntuStudio/Installation](https://help.ubuntu.com/community/UbuntuStudio/Installation)   u should choose the fresh install link.

My pc has the SIS 650_......740 video card  can anyone tell me if they have a similar version.  In the installation process it after I try to install the software packages it tells me it could install an application. it doesn't shoes the screen for choosing the screen resolution as shown in the wiki.

can anyone help

thanks.

---

