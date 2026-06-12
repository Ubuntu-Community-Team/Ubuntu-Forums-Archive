---
title: "I need basic webcam-help"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by croaken on 2009-10-28
I am a very new user of ubuntu, i dont even know which version i am using...
But i have installed some programs though, with help from instructions on the net.
But i can't find any instructions for a beginner like me about how to install my webcam on ubuntu.
I have a Logitech QuickCam 8.4.8 here, and an installationCD, on which it says it can be used on Mac OS and Windows...
Does that mean i cant use it on ubuntu?
I really have no idea what to do, it cant read the CD and nothing happens when i plug in the webcam.. Please give me instructions! Is there anything i can do? or cant i use this cam?

---

### Post by i.r.id10t on 2009-10-28
Nope - you want the pwc drivers, should be included, if not check this site out: [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)

---

### Post by croaken on 2009-10-28
I don't get it.. 
as i said i'm a very beginner...
What was this link and how do i use it together with the cam?
Do i just write all those codes in the terminal and then everything will work?

---

### Post by croaken on 2009-10-28
Please?

---

### Post by croaken on 2009-10-28
Please? It cant be that hard to help me, right? :)

---

### Post by BarisBlaq on 2009-10-28
I'm a noob too, but Cheese worked for me.

From top menu-System-Administraiton-Synaptic

Type "cheese" in search box, install the package.

Theni it should be on the "Sound Video" list on main menu.. It runs fine with me embedded laptop cam.

Hope that helps

---

### Post by Iowan on 2009-10-28
Someone needs a little patience - bumping every hour (or two) is a bit much. 
I borrowed _Ubuntu Kung Fu_ from the library - there was a tip for checking your webcam.  I've since returned the book and forgot the tip... but did some searching to find something similar. [This]("http://my.opera.com/ubuntunerd1/blog/ubuntu-tips") site has a section (Use Find: to search for **webcam**) on getting a webcam to work in Ubuntu. > Get your webcam working in Ubuntu

Open a terminal window and type:

gstreamer-properties


Click the Video tab and click the Test button under the Default Input heading. A video window should appear showing what the webcam sees. If you receive an error, try selecting the Video for Linux (v4l) option from the Plugin drop-
down list. If you still receive an error, the webcam is probably incompatible with Ubuntu. Note that once the selection is made in the Plugin dropdown list so that the webcam works, all applications that use webcams (such as Ekiga or Cheese) will be able to utilize it.

---

### Post by Tomatosoup on 2009-10-28
My Logitech Quickam 9000 Pro (or something?) works out of the box on Ubuntu 9.10 RC. At least, the video. Don't know about the sound.

---

### Post by croaken on 2009-10-30
BarisBlaq: I guess i can only use this program when the computer already've found the cam.. right now what i need is to install the cam on the pc so i can use it...

Iowan: I didn't find any such section. I searched and looked through.. is it still there? It sounded to be just what i need!

---

### Post by croaken on 2009-10-30
oh, Iowan i'm sorry i just found it! :D let's hope it works!

---

