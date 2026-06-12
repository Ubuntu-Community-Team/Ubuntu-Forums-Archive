---
title: "xubuntu gui install on 192mbram compaq"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by jrmink on 2007-09-28
I have a compaq presario 1800T and I have been trying to get an os on it that runs smoothly.  Now have really worked.  So I want to put xubuntu on but I have some problems installing.  When I use the gui live install cd I get all the way to the desktop and in xfce or w/e and I can see the install and homefolder icons and everything but the problem is my screen is like cut in half.  I was still able to manage to run the install even with the screen messed up but it errored sometime during the install.  My laptop has an ATI graphics card...is my graphics card supported under xubuntu? 

Again its like xubuntu thinks im running dual screens or something and its seperated in the middle.

I know there is a text install but I havent been able to successfully burn a text install copy.

Cheer

---

### Post by scrooge_74 on 2007-09-28
You probably are talking about the alternate CD.

About the screen resolution, probably the system is not detecting the correct driver.  You can manually change it from the command line type sudo dpkg-reconfigure xserver-xorg

If your card is ATI there should be an open source ATI driver in the list so you can use that one and latter on use the  close source drivers.  But you may have problems since that cards is not well supported (but AMD says they are going to support them more)

Hardware is supported not under Xubuntu, but on Linux in general.  Xubuntu is just a version of Ubuntu which instead of using Gnome as the GUI uses Xfce4

---

### Post by jrmink on 2007-09-28
Well it probably actually is the screen resolution but I dont know what the screen resolution should be for my laptop.  If anyone could tell me that would be great.

---

### Post by scrooge_74 on 2007-09-28
just do a general search for a review of that particular model and you will know right away

---

### Post by jrmink on 2007-09-29
I know but I am way too lazy for that.

---

