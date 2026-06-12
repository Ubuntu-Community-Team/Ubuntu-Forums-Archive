---
title: "audio and video help"
date: 2005-06-01
forum: Hardware &amp; Laptops
---

### Post by jeremytaylor on 2005-06-01
Hi,
I've installed Hoary hedgehog on my new ASUS W3V laptop and am having a few problems.

Firstly I can't get any sound. My system uses the intel 915 chipset with the intel high definition audio chip built in. I found the page in the ubuntu wiki about using the high definition audio [http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto](http://www.ubuntulinux.org/wiki/HdaIntelSoundHowto)
but when i run alsaconf it can't find my audio chip. I've tried the suggestion in note 3 on that page to no avail. Any suggestions would be very kindly received.

Secondly my laptop has a ati mobility x600 graphics chip. From what I understand the propiertry ati fglrx driver isn't going to work with this so at the minute i just have the xorg "ati" driver.... which is fine for most thing 2-D. Although getting a proper driver that does the 3D stuff too would be nice I'm not hoping for that too soon but what I would really like would be to be able to use the VGA out with another monitor or a projector or whatever. As it is it doesn't do anything at all if I just plug it in while the machine is running and if I plug in a monitor before I switch on then everything goes to that display. grrr,

well thanks for any help anyone can give
yours
Jeremy

---

### Post by ming0 on 2005-06-02
Have you gotten any of this figured out yet!? I just ordered this laptop, and hope to use ubuntu on it too. 

It looks like one sweet machine :)

Please post any details of things that work well, or don't work w/ the laptop.

Thanks in advance ;)

---

### Post by jeremytaylor on 2005-06-04
Well it's a really nice machine. So far most things seem to work with ubuntu but I haven't really tested much of it. The installation is fine it deals with the sata drives and the pci-express graphics and widescreen display without a worry.

If you use KDE you have to turn off kmilo which is supposed to help with all the custum buttons but instead just shoots sill messages at you such as the lcd is now off.

Still not fixed the sound or the vga out. 

If you're willing to use redhat instead then I found that core 4 test 2 works fine though you have to fiddle with the xorg.conf to get the widescreen working.

Jeremy

---

### Post by jeremytaylor on 2005-06-04
scratch that i got sound working.... dvd's look so good on this screen.

I don't quite know why it didn't work before.... I just went through the instructions in the Wiki again and tada! It's rather quiet but it's that in windows too.... these built in sound systems have no omph at all.

Jeremy

---

