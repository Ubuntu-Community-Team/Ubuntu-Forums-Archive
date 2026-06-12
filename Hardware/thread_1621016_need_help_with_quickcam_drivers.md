---
title: "need help with quickcam drivers"
date: 2010-11-13
forum: Hardware
---

### Post by zf1223 on 2010-11-13
I've been using Ubuntu for a few months now, and have been getting progressively more comfortable with it. But one of the few things I still need my Windows computer for is Skype. I've installed it on this machine, but Ubuntu won't recognize my webcam (Logitech Quickcam). Reading around, I've tried installing all sorts of things to help it recognize the device, but to no avail. The driver it seems to need is uvcvideo, but the setup is more complicated than I'm used to. The easiest guide to installing it went something like this:

type svn checkout [http://svn.berlios.de/svnroot/repos/linux-uvc/](http://svn.berlios.de/svnroot/repos/linux-uvc/) in terminal,
after that installs, type cd linux-uvc/linux-uvc/trunk/,
then type make,
then type sudo make install,
and finally type modprobe uvcvideo

But I can't seem to make it past the first step. Everytime I try to do it, it asks for a username and password. I even went to berlios.de and registered a developer account and activated it, just to try and download this, but to no avail.
How can I get the first part done? And if uvcvideo is not the answer, what driver do I need to install to use the webcam?

---

