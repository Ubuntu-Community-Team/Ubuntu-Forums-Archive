---
title: "[SOLVED] Toolbar transparent and inactive window transparent questions"
date: 2008-11-28
forum: General Help
---

### Post by kostasls on 2008-11-28
Hello everyone
I decided to use linux and have putted ubuntu 8.10 in my old laptop for first time :)

After a few problems in the end with lot of reading and playing around i finished setting up everything working :D 
Then the time to customize my desktop came and again after a lot of reading,searching and playing got almost as perfect as i wanted :)

My desktop looks like this right now and here are my questions that couldnt find a solution yet:( 

**1.** I want to make my top toolbar very transparent like as you see in the icon panel and in the space before the battery icon but i need the stuff like applications,places and the icons to <b>be visible!</b>The way i do it now with compiz when i set the opacity low everything disappears. I have seen that in some screenshots of others those are clear visible but havent figured out how to do it :( 
any idea?

**2.** I want my inactive window to be transparent or half transparent! I have Emerald themer, i have played with the settings there but it doesnt seem to affect them at all :( Any idea why is that happening? What can i do?

I also read about an app called trans-inactive but couldnt find it to download and install it.

thanks for any solutions
Konstantinos a new happy ubuntu user ! :D

Dektop screenshot
[[IMG]http://img135.imageshack.us/img135/7967/almost2ij6.th.png[/IMG]](http://img135.imageshack.us/my.php?image=almost2ij6.png)

---

### Post by Wartender on 2008-11-29
well you could always take out GIMP and make an image that is the size of your toolbar (probably the first number of your screen resolution [mine is 1280]x24 (or the thickness of your toolbar), and make it all transparent. then you measure how long the space that applications,places,system takes with the ruler screenlet (if you don't have screenlets you can download them with synaptic, search screenlets) and make that part of your toolbar trnaslucent, or opaque, or however you want it, and then save the image as a .png and use it as your toolbar image (right-click the toolbar and hit properties, then the background tab and click background image.)

for the transparent inactive windows use compizconfig setting manager (search compizconfig in synaptic) and activate the ADD helper effect , and in misc. options set the opacity.

phew. hope that helps.

---

### Post by kostasls on 2008-12-01
hey Wartender
thanks a lot :D

for the active /inactive windows i cant believe it that was so simple and couldnt find it even after two days searching for it on the net :P


about the toolbar i show about this way somewhere but i thought it was too much trouble so for now i just delete it and made a small one with just few icons :P

thanks again

---

### Post by Wartender on 2008-12-01
you're welcome, (you might want to *cough* thank me with that litle button there *cough*), but anyway i think i understood wrong what you meant about the toolbar, try right-clicking, properties, background tab, and use solid color making the opacity zero, if you meant you wanted a non-transparent background under the buttons etc. so you can read them then tell me i can make an image like that on GIMP. (you have to tell me what color you want the non-transparent part to be, or if you want it to be a gradient (transition from one color to another) or anything.

and no problem. :)

---

