---
title: "Configuring The Pointing Stick in Ubuntu"
date: 2009-11-03
forum: Hardware
---

### Post by ARom on 2009-11-03
I have a Lenovo T400.

The pointing stick works, but it is very slow, unusable. 

The touchpad works just fine and can be configured by adjusting the mouse speed and sensitivity.

How to I speed up the pointing stick? (my preffered choice of navigation)

---

### Post by mastertimothy on 2009-11-04
I'm also interested in configuring this device.  I have a ThinkPad W700.  My stick and mouse buttons (left and right) work.  However I would like to get the middle mouse button to work.  And maybe get the click feature when you press on the stick.

---

### Post by ARom on 2009-11-06
Anyone? Please help folks.

---

### Post by shadowimmage on 2009-11-06
There's a solution here: [http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html](http://psung.blogspot.com/2008/09/scrolling-with-thinkpads-trackpoint-in.html) (Taken from [http://ubuntuforums.org/showthread.php?t=1304643&highlight=thinkpad+middle+click](http://ubuntuforums.org/showthread.php?t=1304643&highlight=thinkpad+middle+click))

Also if you like GUI interfaces for modifying the scroll settings, there's:
[http://live.gnome.org/GPointingDeviceSettings](http://live.gnome.org/GPointingDeviceSettings)

Which can be installed through syanptic, just search the package name. For me, there wasn't a shortcut made in any of my menus, so you'll need to create your own menu entry wherever you like it, I put mine under preferences with the other mouse options. 

And note, for the trackpoint, you want the scroll emulation button to be on button 2 (gpointing-device-settings defaults to 4... I have no idea what button 4 is, but it's not the middle one.

Hope this helps. And thanks should go to [hurzel]("http://ubuntuforums.org/member.php?u=940006") for the thread post linked above, which is where I got this info.

---

### Post by whalebus on 2009-11-06
I used this tip from Thinkwiki.

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

I have a T400 with integrated graphics & 1440x900 display running 9.04.  The point stick and 3rd button scrolling work great for me.

---

