---
title: "Problems with wireless mouse and touchpad, Can't edit xorg.conf to solve it"
date: 2009-01-23
forum: Hardware
---

### Post by turboswede on 2009-01-23
This is very odd. I have been  on ubuntu 8.10 for a few weeks now (enjoying it I think, some annoying teething problems) and my mouse has been fine. I broke the left and right click buttons on my laptops touchpad a few years ago (apparently you shouldn't pour irn bru and gin on it... its like glue) so Ive always been using a usb mouse instead. This was fine on ubuntu too, until a few days ago.  Now my mouse is almost constantly on left click. Im highlighting things, creating new folders everywhere, deleting things as i type them... its a real nightmare. Right now it is in a 'lull' phase, it seems fine for a while, but it always comes back. I can't really work out when the problem started, so i'll just list the changes i made, in rough order, that i think may have caused it.

* I tried disabling clicking on the touchpad... I can't find the setting anywhere now, so I have no idea how I did it.

* I switched to a wireless keyboard and mouse, but the problem started before that.

I figured maybe the touchpad is constantly on click (it is glued stuck i suppose) nd thats whats causing problems? I tried following some guides to edit the xorg.conf file ([http://www.lazytechguy.com/2008/01/disabling-touchpad-at-will.html](http://www.lazytechguy.com/2008/01/disabling-touchpad-at-will.html)), but the input device section is no where to be found. I then tried installing gsynaptics, a GUI  frontend, but this also requires i edit xorg.conf first.

Where the hell is the section? it is simply not there.

Is there anything else that could be causing this problem? A very dumb noob just asking for a little help. My last problem (VPN... i guess I can understand why  noone wanted to touch that) didnt get a single reply.

Many thanks, and sorry for the awful spelling, but I am occassionally deleting text now (mouse is bonkers again) and im just trying to type as fast as i can.


Hardware:

sony viao vgn sz2m

had a: hp/logitech m-uv98 usb wired mouse

now have: trust wireless usb keyboard/mouse

---

### Post by martinbaselier on 2009-01-23
Intrepid uses xorg 7.4 and xorg.conf is no longer used for setting up the touchpad. It's instead handled by hal. 
You should create a new file in /etc/hal/fdi/policy/
For example touchpad.fdi or synaptics.fdi

```

sudo gedit /etc/hal/fdi/policy/synaptics.fdi

```
and paste the following text:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
   <match key="info.capabilities" contains="input.touchpad">
     <merge key="input.x11_options.MaxTapTime" type="string">0</merge>
   </match>
 </device>
</deviceinfo>

```
This will disable tapping on the touchpad.

---

### Post by turboswede on 2009-01-24
A quick restart and that seems to be working, many thanks.

On the down side, I have not had the problem since I wrote my last post, so I can't be sure that this solved it. Is there anyway to completely disable the touchpad? Im just worried that is wasn't the tapping that may have been dodgy and causing the problem, but the sticky left click button.

I suppose this is solved, but I cant be sure. For the benefit of the doubt, I think I'll mark it solved if someone can tell me how to completely disable the touchpad (or atlest the left click).

Many thanks for the quick reply Martin!

---

### Post by turboswede on 2009-01-26
Been a few days now, and either way, the problem has stopped! :D

Many thanks again Martin. 

I think I read a thread somewhere that said that thanks and 'SOLVED' buttons have been disabled?

Just to say it's SOLVED then. thanks!

---

