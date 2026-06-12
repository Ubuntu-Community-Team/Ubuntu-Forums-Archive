---
title: "Compiz performance and Nvidia settings"
date: 2008-08-12
forum: General Help
---

### Post by Sain on 2008-08-12
Hi! I have one quite bizarre problem. In Ubuntu 7.10 Compiz worked fine for me, but now on my Hardy fresh install it seems slower, and dropping frames. 
I though it was "normal" until I played with nvidia-settings and whoa! Suddenly Compiz ran smooth as silk, nearly perfect! But that was until i restarted my computer.

Long story short: it turned out that I don't need to do anything in nvidia-settings actually! All I need is just to **start** nvidia-settings, and Compiz will work better, until the next restart.

Question is: what does nvidia-settings do at startup that makes Compiz run smoother?? Doest it load something in the memory, does it resets some settings, what??

Did someone else notice this? BTW, I'm using Nvidia 173.14.12 drivers and Compiz 0.7.6, but this seems to be the case with default drivers and Compiz as well. 

Computer is P4 3.0 GHZ, Abit AA8 i925X motherboard, Geforce8600 GT card, 2 GB RAM etc...

---

### Post by tuxxy on 2008-08-12
That is unusual, amybe you could add nvidias-settings to your sessions for now atleast then it will seem ok.

---

### Post by Sain on 2008-08-12
I've done that, but it doesn't actually solve the problem... 

Now everytime Ubuntu starts nvidia-settings control panel pops up :D

---

### Post by ArtF10 on 2008-08-12
> **Sain said:**
> I've done that...everytime Ubuntu starts nvidia-settings control panel pops up :D

Could you please post how you did that?  I am also using an Nvidia card and it would certainly help if you could post what you did to get this.

---

### Post by Sain on 2008-08-12
Do what? Added nvidia-settings to run at startup? You can do that in Sessions properties (System->Prefrences->Sessions). Just click ADD button and type "nvidia-settings" in command box.

But the question is does this affect you too? Does Compiz run any better when you start nvidia-settings?

---

### Post by ArtF10 on 2008-08-12
> **Sain said:**
> Do what? Added nvidia-settings to run at startup? You can do that in Sessions properties (System->Prefrences->Sessions). Just click ADD button and type "nvidia-settings" in command box.

But the question is does this affect you too? Does Compiz run any better when you start nvidia-settings?

Thanks for clarifying that.  It was very helpful.

I will give it a try and let you know...probably in a few days though(sorry).

---

### Post by Sain on 2008-08-13
[http://onlyubuntu.blogspot.com/2008/06/howto-improve-nvidia-laptop-graphics.html](http://onlyubuntu.blogspot.com/2008/06/howto-improve-nvidia-laptop-graphics.html)

Could this be it?

---

### Post by ArtF10 on 2008-08-13
Sorry, I'm talking about a desktop.  Why is that setting laptop specific?

And will this work if Envy installed?

---

### Post by Sain on 2008-08-14
I don't know, but some use this for desktops too... Doesn't make any difference in my case however. 

It shouldn't interfere with envy.

---

