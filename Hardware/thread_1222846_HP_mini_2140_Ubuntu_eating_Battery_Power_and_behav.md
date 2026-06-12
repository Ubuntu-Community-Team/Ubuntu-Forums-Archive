---
title: "HP mini 2140: Ubuntu eating Battery Power and behaving sluggish"
date: 2009-07-25
forum: Hardware
---

### Post by Sörnäinen on 2009-07-25
Hej hej, 

finally switched to Ubuntu, after having a flirt with Linux for many years and using Mac OSX and Windows so far. :)

Installation was without any problems on my HP mini 2140 - once i found out i have to disable the "Dual Core Support" in the BIOS of my PC. Most things worked out of the box, although i had to reduce the "eyecandy" of Gnome to get a proper working experience. 

But that's the problem: The whole system is slightly sluggish and slow, and it eats a LOT of battery power. With windows i had something like 3,5 hours of battery life without WLAN, now with Ubuntu it´s only 2 hours. 

I guess there should be a way to make the system a bit slimmer? Does anybody have a hint for me? I would be very thankful! 

With greetings from Helsinki!

---

### Post by mikewhatever on 2009-07-25
There are many things to try and tweak, but first, I think it's important to find out what processes are the most taxing. Run the following command and note CPU usage: ps aux.
If you want others to review it, run **ps aux > Desktop/processes.txt**, and then attach the processes.txt file from your desktop to the next post.

---

### Post by Sörnäinen on 2009-07-25
Hello Mike, that was a FAST answer, thank you. 
And it's funny to watch the way Linux users think - just writing a process list to a text file on the desktop via the terminal. No Mac or Windows User would start with that idea. 

I attached the process file - i had some files open since i was working, but i guess that shouldn't be a big problem, at least i hope so. 

Thanks for any hints! 


(I hope the attaching worked, at least it looked like it)

---

### Post by mikewhatever on 2009-07-25
Well, there is nothing unusual with your processes. Have you installed the Netbook Remix or the regular Desktop version? I found UNR very sluggish on a Dell mini 10, unlike the regular interface.

The easiest thing to try to save power is System->Preferences->Gnome Power Management. You can adjust screen brightness on AC and battery, as well as the time  to turn of the screen.

One other thing is to use Intel's lpia architecture.
[http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/](http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/)
There is an Ubuntu port for lpia, but that would require redownloading and reinstalling. There is no graphical installer for lpia, not a show stopper but something to be aware of.
[http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso)

You could also try both disk and cpu power management, but these particular areas is not very user friendly, at least if we go by the standards of Windows users.

---

### Post by Sörnäinen on 2009-07-25
> **mikewhatever said:**
> Well, there is nothing unusual with your processes. Have you installed the Netbook Remix or the regular Desktop version? I found UNR very sluggish on a Dell mini 10, unlike the regular interface.

The easiest thing to try to save power is System->Preferences->Gnome Power Management. You can adjust screen brightness on AC and battery, as well as the time  to turn of the screen.

One other thing is to use Intel's lpia architecture.
[http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/](http://software.intel.com/en-us/articles/low-power-on-intel-architecture-research-project/)
There is an Ubuntu port for lpia, but that would require redownloading and reinstalling. There is no graphical installer for lpia, not a show stopper but something to be aware of.
[http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso](http://cdimage.ubuntu.com/ports/releases/9.04/release/ubuntu-9.04-alternate-lpia.iso)

You could also try both disk and cpu power management, but these particular areas is not very user friendly, at least if we go by the standards of Windows users.

Thanks for the hints - the Intel Ipia looks a bit too experimental for me as a bloody starter with Linux. It would most likely not survive updates, would it? I am reading inside it. Well, since there is a complete installation disk already... hm. 

I installed the regular Ubuntu 9.04, since the UNR looked terrible to me about the Interface. Really not my way of working with a PC, i need a real desktop and real windows, that made me angry after some minutes already. 

I wonder if it could help if i switch from Gnome to Xubuntu? I learned that this is not so difficult, it could safe ressources?

---

### Post by mikewhatever on 2009-07-25
Yes, Xubuntu is a good idea. It's not feather light, but should still be lighter then Ubuntu. 
I didn't hear anything bad about lpia, yet, haven't tried it either.
There are also quite a few startup processes and services that might be disabled in Ubunutu, which I tend to do on my notebook. It's all gui based, and I'll post a list next time I get a chance to boot it.

---

### Post by Sörnäinen on 2009-07-26
Thank you, Mike, i try it with Xubuntu - as far as i got it it should be easy to install it with the Packet Manager, and i still should be able to start the Gnome GUI, right? 

I will try that.

---

