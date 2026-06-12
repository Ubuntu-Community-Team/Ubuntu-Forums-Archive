---
title: "having problems when i moved hdd to other pc"
date: 2010-01-07
forum: Hardware
---

### Post by leonne on 2010-01-07
Hey 
I was planning on moving my ubuntu os to my other computer. Instead of installing every thing i thought if i just switch the hdd that it would work fine. well when i start up the pc, everything seems to load fine but then it seems to go into something like terminal mode which just has line of text, which asks me to login, i try but never works. the window seems to blink in and out and after like 30 sec the screen goes blank. I tried it on different computer but same thing. I put it back into the original pc and works fine so I have no idea why this is happening.

I even installed ubunto on the other hdd thinking maybe it needs to config the hardware. It worked fine but when i switched the hdd same thing happen

---

### Post by sanderj on 2010-01-07
I think the problem is the X server settings, for example because on the original computer you have installed a binary driver for your video card.

So, in the original computer, remove that special driver and/or setting.

If that doesn't work, you could try one of the following the commands in the CLI mode on the other computer:

dpkg-reconfigure xserver-xorg
xfix

Please let know if this helps.

---

### Post by leonne on 2010-01-07
Hey 
thanks that worked but now its acting weird like when i type su in terminal and then password it says i am not permitted to do this, also it seems like it cant connect to the internet. When i login to root and tried to go into network it said i am not aloud to view data or something. I just see in the top right that the computer is trying to connect online, but its a wired internet so should be instant. Any idea whats going on?

Thanks

---

### Post by ronniestamps on 2010-01-07
The problem with what you did is vast, and symptoms will be completely different from computer to computer. All hardware... soundcard, video card, ethernet, etc, have addresses so the operating system knows where everything is and how to communicate. When you took the hard drive out of your computer and put it into the new one, everything was in the wrong place. Because this addressing varies from computer to computer, the results will never be the same, unless everything is EXACTLY the same, in which case it will work just fine. Your best bet is to install a fresh copy of your operating system whenever you intend on switching computers. BTW, this is not an Ubuntu specific issue, this is with ALL operating systems.

Not bashing you (this is a simple and common mistake), but this reminds me of something...

"Why is there never enough time to do it right, but always enough time to do it twice?"

---

### Post by leonne on 2010-01-07
o ok thank, well i did install linux on a different hdd when it was hooked up to that pc and i got the same error with the root. At first it was working fine then when i tried to transfer data from the other hdd this all started i guess ill reinstall it again.

---

