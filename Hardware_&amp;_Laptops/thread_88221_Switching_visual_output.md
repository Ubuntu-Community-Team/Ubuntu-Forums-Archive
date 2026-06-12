---
title: "Switching visual output"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by Declan on 2005-11-09
I don't know if the subject title communicates the question or not.
I was advised by this website, that I hadn't posted on the forums for several wekks, and was invited to post again. Handy, said I, for I just happen to have a question.  Part of the reason for the silence was the fact that I was trying out Suse 10 for a while.  But I moved back to Ubuntu, and found myself far more at home once again.

But I did have a problem today.  In relation to data projection.  I was getting the visual output sent only to the projector, and not to the laptops display.  So I booted into Windows (which is what I do sometimes for testing purposes).  A little poking around revealed that I could toggle between display outputs using FN + F5 or something like that.  It worked nicely.  I also noticed that the laptop went into hibernation automatically after a certain length of time unattended.  I can't get anything like that to happen on Ubuntu.
So, armed with this new information, I went back to Ubuntu, and proceeded to press those same keys, during boot up.  During boot up this appeared to work, but after boot up the FN = F5 thing caesed doing anything.  It is strange that it would do it during bootup, but not afterwards.  
Any ideas on how to manage this?

Declan

---

### Post by ranf on 2005-11-09
[QUOTE=Declan]So, armed with this new information, I went back to Ubuntu, and proceeded to press those same keys, during boot up.  During boot up this appeared to work, but after boot up the FN = F5 thing caesed doing anything.  It is strange that it would do it during bootup, but not afterwards.  
[/QUOTE]
Try this from a terminal:
```
sudo /etc/init.d/hotkey-setup stop
```
Then press Fn+F5 again. Does this help in any way?

---

### Post by Declan on 2005-11-11
Thanks for that.  I executed that command, but I can't test it for the moment, since I have given the projector back.  But I'm grateful for the help.

Declan

---

