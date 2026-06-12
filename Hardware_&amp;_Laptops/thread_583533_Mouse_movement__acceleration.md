---
title: "Mouse movement / acceleration"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by VinylPusher on 2007-10-20
I've a slight issue regarding mouse acceleration that seems to have been the bane of every Linux distro I have ever used. Years ago, I could cope with it but I now have tendonitis and my mousing habits receive a lot of attention!

I have a very sensitive (2600dpi) Evoluent Vertical Mouse which has been of great benefit to me over the past few months. I use a 1920x1200 display, so using a sensitive mouse is really nice and reduces the strain on my wrist.

However, the problem I have with Ubuntu 7.10 (and every other distro before it, from different vendors) is that there is no simple option to completely turn off mouse acceleration whilst leaving sensitivity at its highest (i.e, 1 pixel = 1 unit of measure of movement from the mouse).

I tried turning acceleration all the way down, but this had the crazy effect of *decelerating* my mouse cursor when I moved my mouse faster!

Knowing Linux a little, I believe it probable that a text config file exists which I could potentially hand-edit to make my mouse act in a sensible way (ie, like in Windows when 'enhance pointer precision' is off and 'mouse speed' is set to the middle setting).

Can anyone please help, because this is very frustrating and all but negates the benefit of my rather expensive mouse!

**EDIT** Just remembered, my mouse has a fourth and fifth button that default (in Windows) to be a 'back' and 'forward' button in many applications (Opera, IE, Outlook, Explorer). In Ubuntu, the fourth button acts as 'paste from clipboard' and the fifth button merely acts the same as the right mouse button. Is this also configurable somewhere?

---

### Post by frafu on 2007-10-21
Hello, 

First of all, I don't know a direct solution to your problem. But maybe, you could do a search with the following keywords here in the forums (upper right input field): 
mouse acceleration sensitivity

I tried that search and it turned out among many others, the [this thread]("http://ubuntuforums.org/showthread.php?t=251582&highlight=mouse+acceleration+sensitivity").

Further, a few months there was also [this interesting posting]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-December/023121.html") in the mailing list. But don't ask me how to use it. I am afraid that it will require much more knowledge that a normal user can provide. 

Have a nice day. 

Francesco

---

### Post by VinylPusher on 2007-10-22
'xset m 1 0' appears to work.

I put this in my ~/.xinitrc but it doesn't seem to work. At least it's progress though.

My only other issue now is the mouse button mapping, but I guess that's less of an accessability issue and more of a general hardware one.

---

### Post by frafu on 2007-10-22
Hello, 

I am moving this thread to the Hardware and Laptops forum. There, you might have a better chance to get replies. 

Have a nice day. 

Francesco

---

### Post by Landslide on 2007-12-11
The problem is that in Gnome, the controls for "Sensitivity" and "Acceleration" are labeled as each other. Sensitivity controls acceleration and vice versa. Try setting Acceleration at its highest and Sensitivity at its lowest.

---

