---
title: "Scrolling on ThinkPad T400"
date: 2011-02-04
forum: Hardware
---

### Post by neverdusted on 2011-02-04
Hey everyone. 
I use Ubuntu on my ThinkPad T400 to work. The thing is that I deactivated the touchpad, and I'm using the red button of the center instead (I hope you know what I mean).

When using touchpad I have no problems to scroll vertically, but with the red button (don't know its name), the 3rd button just doesn't work. I hope that someone understand my problem. I need to be able to scroll without using the right part of the pad. Something like holding the middle button and moving the cursor up and down.



Thank you !

---

### Post by NFblaze on 2011-02-04
I dont think you can scroll with the red button (aka the Trackpoint button)

I dont have a Thinkpad with me here though upon doing a Google search I've seen two ways:

tp-scroll([http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Graphical_Frontends](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#Graphical_Frontends)) seems to be the oldest method and poorly available.
though linux trackpoint utilities @ ([http://www.slac.stanford.edu/~strauman/pers/tp4utils/index.html](http://www.slac.stanford.edu/~strauman/pers/tp4utils/index.html)).

If I were you I would open Synaptic and search for packages regarding Trackpoint or Thinkpad also. Let us know how you turn out

---

### Post by schum3,1415 on 2011-02-07
Hi there,

I found a tool, with which one you can enable scrolling with your trackpoint device:
[GPointing Device Settings]("http://live.gnome.org/GPointingDeviceSettings")

You can download it via the Ubuntu Software Center and it will be installed in System->Preferences->Pointing device

Just choose: "enable wheel emulation" and choose "button: 2"
Now you can scroll by holding down the middle button and using the trackpoint.

More info on: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

### Post by fido1357 on 2011-03-05
> **schum3,1415 said:**
> Hi there,

I found a tool, with which one you can enable scrolling with your trackpoint device:
[GPointing Device Settings]("http://live.gnome.org/GPointingDeviceSettings")

You can download it via the Ubuntu Software Center and it will be installed in System->Preferences->Pointing device

Just choose: "enable wheel emulation" and choose "button: 2"
Now you can scroll by holding down the middle button and using the trackpoint.

More info on: [http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Thanks for that. I'm an ubuntu newbie using an R50e. I'd been trying and failing to do this through the terminal but this worked perfectly.

---

