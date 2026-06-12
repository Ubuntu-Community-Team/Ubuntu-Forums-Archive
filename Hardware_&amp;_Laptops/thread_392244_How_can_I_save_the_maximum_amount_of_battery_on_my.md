---
title: "How can I save the maximum amount of battery on my laptop?"
date: 2007-03-24
forum: Hardware &amp; Laptops
---

### Post by Davigetto on 2007-03-24
Hello, I have a laptop with ubuntu, and I believe that I can save more battery that nowadays it is saving.

In Windows, battery lasts 3 h, and on ubuntu, 3:20 h. What methods can I follow to save more battery on Gnome? (What programs spend lots of resources, CPU scaling, some configurations...)

Give me some tips, please.

Greetings and sorry for my bad english :)

---

### Post by SoggyCornflake on 2007-03-24
> **Davigetto said:**
> Hello, I have a laptop with ubuntu, and I believe that I can save more battery that nowadays it is saving.
<snipped>
Give me some tips, please.

Greetings and sorry for my bad english :)
Your English is much better than my Italian <-- My guess on your native tongue.:) 

It may seem wrong, but I'd start by getting as much RAM in the laptop as possible.  That's because the more ram you have, the less you need to access your hard drive- less spin up and spin down of the hard drive.

Try to not run lots of differnt programs at once.  _ less swapping  of data.  

Try to not run many graphic intensive programs.

if you must connect to the internet, try using standard ethernet, not wireless LAN.

Don't use a screen saver - just force a suspend instead.  Screen savers tend to be graphic intensive at times.  (You can choose one that blanks the screen but forcing a suspend would save a bit more power.)

---

### Post by Davigetto on 2007-03-24
really thanks for your tips, but tell me a thing:

> It may seem wrong, but I'd start by getting as much RAM in the laptop as possible. That's because the more ram you have, the less you need to access your hard drive- less spin up and spin down of the hard drive.

I have 1 GB RAM, it's cool?

---

### Post by SoggyCornflake on 2007-03-24
> **Davigetto said:**
> I have 1 GB RAM, it's cool?

You have more than I do so I'm guessing yes.

Just to be sure, bring up your system monitor program (Monitor del System?) and select the resouces option and see how much swap memory is being used.  (Right now, about half of my 750 MB is being used.)  If for some reason you're seeing lots of swap file usage, that should tell you to buy more RAM, but like I said, you have more than me. :)

---

### Post by hardyn on 2007-03-24
well... my experience is as follows...

linux isnt very good for power management with notbooks yet, but does appear to be getting better.

enable laptop mode in gnome, this will apply a very agressive power saving scheme to the harddisk, this isn't good, but it can be adjusted; there are posts on how to do this, that is where i found out how to do it.

if you have an intel wireless card,,, there is also a post on how to enable power saving mode, it does not do this by default, and even after you run the script it doesn't really work very well... a bug as been filed, but is not getting any love.

most of the OSS video drives have been designed for desktops, not for notebooks, and do no GPU scaling... the radeon driver tries, the DRI driver tries, nether of the nvidia ones do.  im sure the intel driver does too, being fully open source, but i have not had a laptop with intel graphics.

as far as hardware that is about all i can think of... now... how you use it makes a pretty big difference...

3:20 is pretty good for most 15" notebooks... soo unless you were getting alot more under windows, don't expect too much.

disable wireless when you are not using it.
dim the screen to as comfortably low as possible.
don't run the optical drive.

disabling the wifi and dimming the screen is good for about 45min on my machine.

good luck.

---

