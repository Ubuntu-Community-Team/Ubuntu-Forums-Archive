---
title: "Middle-Click Shouldn't Mean &quot;Paste&quot;"
date: 2008-07-17
forum: General Help
---

### Post by Jesdisciple on 2008-07-17
I habitually use my mouse-wheel to scroll, but Ubuntu seems to map a middle-click to "paste," so I often end up pasting stuff multiple times and usually in the wrong place.  How can I de-map that?

Thanks!

---

### Post by damis648 on 2008-07-17
It only pastes when an item is highlighted. If you were to highlight this sentence, it would copy over with a middle mouse button without actually a ctrl+c or right click>copy. Just make sure nothing is highlighted. That is all I can thank of. I actually find it quite useful. I do that habitually.

---

### Post by Subban on 2008-07-17
Someone may be along soon to correct me, but as far as I know the middle click to paste is a Linux wide 'default' covering many if not all variants and just Ubuntu furthermore it has always behaved that way.

I may be wrong here but I think its a feature of the X server and not readily changeable. One possibility might be to map the middle button to the left button in xorg.conf but I don't have time to dig into that right now but I hope it at leasts give you something more to look into.

---

### Post by tact on 2008-07-17
> **Jesdisciple said:**
> I habitually use my mouse-wheel to scroll, but Ubuntu seems to map a middle-click to "paste," so I often end up pasting stuff multiple times and usually in the wrong place.  How can I de-map that?

Thanks!


You have me confused. A middle click is one action.  Rolling the wheel (to scroll) - its not clicking the wheel down.  different actions, different results.

rolling the wheel to scroll is not a linux paste command.   Pressing the wheel down toclick it is a different action and is mapped to paste any highlighted text.


don't press down on the wheel so hard when you are scrolling and you wont paste anything

---

### Post by pofigster on 2008-07-17
I'm pretty sure it's actually a Gnome action, not a Linux thing.  The nice thing about it, it uses a different clipboard than Ctrl-C does, so you can have multiple things copying and pasting at the same time.

And yeah, it is a little weird that your rolling the mouse wheel pastes, is your mouse super sensitive about the click?

---

### Post by mali2297 on 2008-07-17
It is a feature in the X window system. 

There does not seem to be any standard way of disabling it, but there is a workaround posted here:
[http://ubuntuforums.org/showthread.php?t=355110](http://ubuntuforums.org/showthread.php?t=355110)

---

### Post by Jesdisciple on 2008-07-17
> **tact said:**
> You have me confused. A middle click is one action.  Rolling the wheel (to scroll) - its not clicking the wheel down.  different actions, different results.

rolling the wheel to scroll is not a linux paste command.   Pressing the wheel down toclick it is a different action and is mapped to paste any highlighted text.

don't press down on the wheel so hard when you are scrolling and you wont paste anythingYou know, I've always had this problem.  When I had a Super Nintendo and then an N64 as a kid, my controller always wore out before my brother's.  It shows up in my handwriting too, which is one of the main reasons I use the computer so much in the first place.  (Note that I don't grip my mouse like I did those video game controllers, but it's the same problem.)  So basically, I'm going to be doing this and my computer should get over it.

Thanks for the link, mali.  I tried that workaround, but now I can't use my long lost autoscrolling which that same thread brought back to me - and worse yet, I lost the easy way to Open Link in New Window...  Is there another way, by any chance?

---

### Post by mali2297 on 2008-07-17
> **Jesdisciple said:**
> 
Thanks for the link, mali.  I tried that workaround, but now I can't use my long lost autoscrolling which that same thread brought back to me - and worse yet, I lost the easy way to Open Link in New Window...  Is there another way, by any chance?

By *autoscrolling*, you mean that you have set the middle mouse button in Firefox to work as in Windows?
The workaround completely disables the middle button, so it makes sense that that does not work any more.

I don't know of any way to just unmap the paste feature from the middle button. Not *globally*, that is. But as with Firefox, it might be done *locally* within a certain application.

---

### Post by tact on 2008-07-17
> **Jesdisciple said:**
> You know, I've always had this problem.  When I had a Super Nintendo and then an N64 as a kid, my controller always wore out before my brother's.  It shows up in my handwriting too, which is one of the main reasons I use the computer so much in the first place.  (Note that I don't grip my mouse like I did those video game controllers, but it's the same problem.)  So basically, I'm going to be doing this and my computer should get over it.


When you get used to how you can (in linux generally) just highlight a piece of text and paste it by clicking the scrollwheel it is really fast and excellent. 

Compare to the windows-method most people are use to - where you highlight the text, right click, select copy ...then have to right click an select paste to complete the action.  (this method also works in linux generally)

anyways...  don't hit the scrolwheel so hard and you won't be accidently pasting text in documents etc...

to open any link in firefox in another tab (or separate window if you configure it so) you just click the link with the scrollwheel.  default functionality.  very cool.  

cheers

---

