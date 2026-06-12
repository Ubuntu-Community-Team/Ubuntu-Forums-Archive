---
title: "Touchpad Click Not Responding"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by motion parallax on 2008-01-24
My touchpad tap-to-click only responds 50% of the time.  It seems like it works more often if I press down more firmly, but this may just be in my head.  

I installed gsynaptics, edited the xorg.conf file, and it seems that it's working better, but not all the way.  

Does anyone know how to increase the responsiveness of my touchpad?  

By the way, I'm very new to Linux, so my understanding is limited (though growing).

---

### Post by LaRoza on 2008-01-25
You should give the specific computer model and Ubuntu version.

---

### Post by motion parallax on 2008-01-25
I apologize.  

Acer 5610-4537 Laptop
Intel Core Duo 1.73 GHz
1GB DDR2 RAM

Running Gutsy 7.10 and Vista dual boot.

---

### Post by rocko_mtv on 2008-01-25
Take a look at this link below.  Scroll down to the section titled "Additional Settings".  If your xorg.conf has these options listed you can adjust them to your taste.  If it doesn't contain them you can add them to the list of options.  The link provides some hints to tweak the settings.  Look through the contents

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Be sure to create a backup of your current working xorg.conf file before changing any thing in it. I believe the backup command is: 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup

If you get anything wrong in the xorg.conf you may have bootup issues requiring you restore your xorg.conf from the backup file you created above.  I believe that command is:

sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf

You are in the right place to get this resolved.  The support I have received from others in this forum is just tremendous.  

I hope this helps you?

---

### Post by motion parallax on 2008-01-25
Wow, the link has a wealth of information.  I tried a few of the settings and I already notice a difference.  

Thank you very, very much.

---

### Post by ugm6hr on 2008-01-25
> **motion parallax said:**
> Wow, the link has a wealth of information.  I tried a few of the settings and I already notice a difference.  

Thank you very, very much.

There is more info available right on your computer!

```
man synaptics
```

---

### Post by rocko_mtv on 2008-01-25
Wow, even a noob like me can be helpful from time to time.  There is definitely hope for us FNG's!  

"Motion" you should be getting your TP "dialed in" between that link's info  and ugm6hr's command to bring up the TP manual.  

Oh great Ubuntu Master Roaster I will soak up all knowledge you present here within and apply it accordingly.   Todays tip is like learning a new keyboard shortcut that saves buku time.

Rocko bows and graciously  says,  "Thank you ugm6hr."

Thanks,
Rick

---

### Post by ugm6hr on 2008-01-25
> **rocko_mtv said:**
> Wow, even a noob like me can be helpful from time to time.  There is definitely hope for us FNG's!  

I was a noob once too!  This forum runs on people passing on knowledge they have picked up when learning themselves, cos no one was born an Ubuntu expert...

But, that *man <command>* thing is worth remembering.  It works for almost every command in Terminal.  Much easier to research advice on your own computer than with google!

---

### Post by motion parallax on 2008-01-25
Very true. The man synaptic command showed me FingerLow, FingerHigh, MaxTapMove, and Clicktime, which I think are the main culprits.  The site that was linked helped me set the whole thing up.  

I plan to learn a lot of this on my own and with research, but I'd like to get my laptop to the point where I can use it comfortably first.  Of course, the discomfort can be motivating :)

Thanks again, everybody.

---

