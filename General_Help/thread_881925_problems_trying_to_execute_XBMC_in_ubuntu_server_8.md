---
title: "problems trying to execute XBMC in ubuntu server 8.04.1"
date: 2008-08-06
forum: General Help
---

### Post by perfmode on 2008-08-06
Let me preface this by saying I am completely new to linux.

I'm trying to get XBMC running on my Dell Inspiron 6000 laptop on Ubuntu Server 8.04.1.

To start XBMC, I type the following commands in command line:
```

$ cd XBMC
$ ./xbmc.bin

```

Everytime I do that, I get this error:
```

Cannot get root display. Is X11 running and is your DISPLAY variable set?

```

I have gnome-core installed.

What should I try to do next?

How do I configure XBMC (or my graphics card) to output video through the s-video port on my laptop? I have Intel 915GM integrated graphics.

---

### Post by brujoand on 2008-12-13
Well.. To show graphical stuff like windows and borders, linux needs the X server. Now in your case, X11 isn't running and your display variable is therefor not set.. 

> 
sudo apt-get install xserver-xorg

should install most of the stuff you need, or atleast get you started, To start X just type "sudo startx" in the terminal and your set. Now you can go do a ./xbmc.bin

---

