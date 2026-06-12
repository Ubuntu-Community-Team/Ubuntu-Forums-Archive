---
title: "Toshiba 2210XCDS Display problem"
date: 2005-04-09
forum: Hardware &amp; Laptops
---

### Post by jama687 on 2005-04-09
I recently have received the installation cd's of Ubuntu, and I am new to this Linux based Operative system (a windows user that recently opened the eyes)  made the installation to  my laptop. 

Evertything was easy. But the problem is with my display... I see at the low part of my screen a fuzzy-line from side to side... 

I've change the resolution from 800x600 to 640x480 but it just got worst, the screen shrunk and some colofur lines appeared at the right part, so i leave it at 800x600 but with the fuzzy lines at the bottom. 

The video :
Trident Cyber 9525, with 2.5MB...

Help please...   :-|

---

### Post by marxamuel on 2005-11-27
[QUOTE=jama687]I recently have received the installation cd's of Ubuntu, and I am new to this Linux based Operative system (a windows user that recently opened the eyes)  made the installation to  my laptop. 

Evertything was easy. But the problem is with my display... I see at the low part of my screen a fuzzy-line from side to side... 

I've change the resolution from 800x600 to 640x480 but it just got worst, the screen shrunk and some colofur lines appeared at the right part, so i leave it at 800x600 but with the fuzzy lines at the bottom. 

The video :
Trident Cyber 9525, with 2.5MB...

Help please...   :-|[/QUOTE]

I got the same thing on my 2210xcds, too

---

### Post by scrimp212 on 2006-04-25
I have this same problem with my Toshiba 2595CDS that has the same video card Trident Cyber 9525DVD. Ive been trying to look for a driver, but cannot find one

---

### Post by scrimp212 on 2006-05-01
Hey, I was able to fix the problem. Go to the file xorg.conf in /etc/X11 dir and look for a line that goes:

**please create a copy of the file: xorg.conf just in case it doesnt work on your machine**

driver: "trident" and change that to driver: "vesa" using the command:

sudo gedit xorg.conf then make the changes and then save the file.

Do a restart and then you should notice that the lines at the bottom are gone

---

