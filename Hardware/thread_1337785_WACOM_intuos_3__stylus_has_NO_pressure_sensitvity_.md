---
title: "WACOM intuos 3 : stylus has NO pressure sensitvity In Karmic"
date: 2009-11-25
forum: Hardware
---

### Post by popiutyress on 2009-11-25
Hello,
I am having trouble getting my Intuos 3 tablet to work in Karmic.
There is no pressure sensitivity in Gimp and Inscape. I have configured the input devices to screen for stylus, eraser, pad and cursor. The erasor works perfectly with pressure and all.

I wouls apreciate all suggestions as to how to fix this.
Many thanks !

---

### Post by Favux on 2009-11-25
Hi popiutyress,

That doesn't make much sense.  If the eraser has pressure so should the stylus tip.  Does the stylus tip work in Windows or on a Mac?  I ask because I have seen a few cases where the tip of the stylus was broken.

That said what does your wacom.fdi look like?  Also is you Intuos 3 tablet usb or serial?

---

### Post by popiutyress on 2009-11-26
Hi Favux,
I have used the tablet before in Windows, Mac os X and in Hardy (with settings in xorg.conf) and it worked fine.

As for my wacom.fdi, I have tried using the both the orginal one that leaves "xsetwacom list dev" empty and the alternative one you suggest that I found here : [http://ubuntuforums.org/showpost.php?p=8367540&postcount=391]("http://ubuntuforums.org/showpost.php?p=8367540&postcount=391")

And which ever one I use I end up with the same results in Gimp and Inkscape which is what I am finding confusing. 

My guess is I made the mistake of installing the wacom_utility from here : [http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0]("http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0") 

Although I have tried to completely remove it (including configuration files) with Synaptic Packadge manager, I suspect it must have screwed something up. But what I have not idea.

My Intuos 3 is a USB tablet.

Thanks for sharing any ideas you have as to how to fix this!

---

### Post by Favux on 2009-11-26
Hi popiutyress,

My understanding is that utility only works on the default wacom.fdi from Jaunty.  It won't work with the one I posted and I don't know about the Karmic one.  I would also check xorg.conf and see if any Wacom entries have occurred there.

Do we know where the utility puts its .fdi?  Check say "/etc/hal/fdi/policy/" and make sure a custom_wacom.fdi hasn't shown up that is messing things up for you.

---

### Post by popiutyress on 2009-11-26
OK I have fixed it !
yes the utility only works with the original system .fdi file, I am using  xsetwacom and wacomcpl.

For some reason by restauring the default input devices configuration and restarting Gimp and Re setting all the devices to screen made it work. I have tried in Inkscape and it is working too.

Thanks for the support !

---

### Post by Favux on 2009-11-26
Hi popiutyress,

Great!  Nice job.  You're welcome.

---

