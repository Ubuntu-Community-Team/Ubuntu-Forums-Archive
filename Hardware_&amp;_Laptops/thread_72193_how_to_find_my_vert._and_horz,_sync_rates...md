---
title: "how to find my vert. and horz, sync rates.."
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-10-05
Hi.
I have my ati drivers installed but need to raise the refresh rate..
I think i can change the vert and horz sync rates to allow for the higher refresh rates..
I cant seem to rember how to find whta the monitors rates are though..
Can anyoe point me in that direction
?
thanx

---

### Post by aysiu on 2005-10-05
Go to your monitor manufacturer's website and find your monitor's manual.

---

### Post by mlomker on 2005-10-05
> I think i can change the vert and horz sync rates to allow for the higher refresh rates..


That's a lot harder than it sounds.  The fglrx driver communicates with the monitor (if it is modern enough to support plug-and-play) and sets the highest setting that they can agree on.  In order to change that setting you have to create a custom **modeline**.  I've literally spent hours experimenting until I get it right and that's *with* the monitor manual in my hand.

I'd leave it alone unless you have lots of free time.  ;-)

---

### Post by aysiu on 2005-10-05
Although I believe you should take mlomker's caution to heart, that isn't everyone's experience. All I did was look up the ranges at Viewsonic's website, *sudo gedit /etc/X11/xorg.conf*, add in the values, and reboot, and everything was cool.

---

### Post by floyd27 on 2005-10-05
ok..
i found the ranges on the website.
i changed the values and they have "taken" but i still can only get a max of 60 hz refresh rate..

i found they were..
Hor 30-70
vert 50-150
higher than was origionally there... and i used Kate instead of gedit..if that matters
they are now listed in the config file as that but its not doing anything...
if anyone can point me in another direction i have time....:)

btw..  [http://www.powerstartpc.com/scripts/details.asp?PRDCODE=MN-FP-17](http://www.powerstartpc.com/scripts/details.asp?PRDCODE=MN-FP-17)

here it is.....

---

### Post by floyd27 on 2005-10-05
i can increase the rate if i lower res to 1024 but tings are way too big..
if that matters :)

---

### Post by floyd27 on 2005-10-05
I found this in a post..
I dont have a nvidia card but i thin it might work?
what do you think?









Now, if you have an nVidia card and you're sure your monitor will support that resolution, run the following in the terminal:

sudo gedit /etc/X11/xorg.conf

Scroll down to the "Device" section, and add this:

Option "IgnoreEDID" "True"

This will make the drivers ignore what the monitor says its maximum resolution is. BE CAREFUL, this could damage your monitor (but in my experience, it never did anything to me )

---

### Post by mlomker on 2005-10-05
[QUOTE=floyd27]I found this in a post..
I dont have a nvidia card but i thin it might work?
what do you think?
[/QUOTE]

It has never worked when I've tried it.

---

### Post by floyd27 on 2005-10-05
your right...... no go........

What if i increased the hor and vert a little over what its in the web site..?
i dont want to hurt anything though..
im gona continue reading a link i found on this..
ill let you  know

---

### Post by floyd27 on 2005-10-05
sudo pico /etc/X11/XF86Config-4

using this code i found that the vert and horz rates are the old "lower" values?
is this right..?
Whe i edited the file with 

gedit /etc/X11/xorg.conf

it took the new ranges and its still listed with the new ones after a restart.. but no higher rates.
The post went on to say setup your sudo fglrxconfig file..
I didnt go ahead withthat yet.. whated to see if there is even a good reason to?
what do you guys think..

---

