---
title: "My OmniSystems webcam working with gstreamer. How to make it work for camorama etc"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by lethalamby on 2008-03-15
I installed my OmniSystems web cam drivers by installing uvcvideo module into the kernel.
As such I am able to view my webcam input in the gstreamer-properties in test mode.
the pipeline it creates looks like

                v4l2src device="/dev/video0"

but when I use utilities like camorama, camstreamer the error msg is something like this

" No Channel Info available"

the output of lsusb is

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

I have a Dell Inspiron 1525.

Can neone make my webcam usable in live chat softwares and/or normal photo/video clicks

Please help me

---

### Post by linuxwizard on 2008-03-15
Camorama does not support v4l2. I don't know anything on Camstreamer never used. Try Ekiga or Cheese see if they will work for you.

---

### Post by lethalamby on 2008-03-17
cheese did not work either..
I would have replied earlier had it not been for the forum logging me in and redirecting me back to login page :x

---

### Post by linuxwizard on 2008-03-17
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings.
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

### Post by lethalamby on 2008-03-28
Ekiga is able to display my webcam image :)

But still I do not want it for video chat.
I like to play with my webcam pics 
something wat cheese can do but alas cheese is not working.

ne other suggestions for a software :(

---

### Post by linuxwizard on 2008-03-29
Atleast we know the cam does work with Ekiga. I have only used Cheese a few times don't care much for it, no setting to work with. Not sure why you are having issues with Cheese.

But from here > [http://live.gnome.org/Cheese/FAQ](http://live.gnome.org/Cheese/FAQ) >  My webcam works with gstreamer, but does not with cheese... What's wrong?

Try to change from xvimagesink to ximagesink or vice-versa, maybe that does the wonder.

Good Luck

---

