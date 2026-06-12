---
title: "How can we make a laptop detect and switch to an external screen when the lid closed?"
date: 2008-05-29
forum: Hardware
---

### Post by marshall.robert on 2008-05-29
Hello,

When I am in Windows XP and I have an external monitor plugged into my laptop (The video card it runs is a GeForce 8600GT.) and the lid is closed, the drivers can detect if a screen is plugged in and use it instead of the laptop screen.

I was wondering if the same functionality could be implemented in Ubuntu...

If it's possible then it would be exellent, I currently use XP more because of this feature and I would rather not.

If you don't think it is possible, could you please explain why?

Thanks

-rob

---

### Post by bigken on 2008-05-29
try using the Fn key with f8

---

### Post by marshall.robert on 2008-05-29
Nope, nothing.

---

### Post by marshall.robert on 2008-06-02
so, yeah... my original question?

---

### Post by bigken on 2008-06-03
I think you need to install the nvidia tools not to sure of the correct name search the forum

its in synaptic **nvidia-settings**

---

### Post by marshall.robert on 2008-06-03
yeah, i have that, what im looking for is the ability to automatically switch to an external screen when the laptop lid is closed...

so it goes kinda like:

close lid
look for external screen
if external screen present
   set default output to external screen and draw to it
else
(just turn off screen)/(do nothing)
end.

would this sort of thing be possible?

if it is i recon it would be a good thing to include, making ubuntu/linux better and 'more ready' for the laptop.

im sure this kind of a thing would depend on the drivers, so i spose it would be driver specific, but that shouldnt stop the idea being implemented on more than just an nvidia card, for example.

if im not putting things across clearly then please say and ill try and reword its a little...


-rob

---

### Post by bigken on 2008-06-03
i dont think you can just shut the lid Im sure you have to enable something in the nvidia settings for duel monitors or select the external as your default monitor 

anyhow Im off to me feather godd night and good luck

---

### Post by marshall.robert on 2008-06-03
maybe, ill edit this post tomorrow with what i find out after some tinkering...

Sorry i didnt edit on time, i was a bit lost with other things.

but i have got it to work but using gksudo nvidia-settings, then detect displays, then enabling the external as a separate x screenn, then disabling the laptop screen, then saving the xorg conf (not after backing up the current file) and then using ctrl+alt+backspace to restart X and that has worked.

its a bit of a long winded approach but i thought perhaps a script could be made to run that just copies the backed up file and vise verca then restarts x when conditions are met?

---

### Post by marshall.robert on 2008-06-07
bump

---

