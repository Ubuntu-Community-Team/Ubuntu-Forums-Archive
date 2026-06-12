---
title: "Screen turns off after visiting certain web-pages"
date: 2014-10-18
forum: Hardware
---

### Post by duruttye on 2014-10-18
Hey guys!

After having issues on my Ubuntu 14.04 with Gnome, I decided, that I erase everything from my laptop (dell vostro a860) - including the unused windows - and start from scratch.
After formating and making new partition, my completely fresh Xubuntu 14.04.1 is just turning off my screen after accessing this: [https://support.google.com/chrome/answer/95346?hl=en](https://support.google.com/chrome/answer/95346?hl=en) and clicking on the install button. Before I removed the gnome version it was doing the same when I was trying to install an add-on on chrome.
Now, what I tried so far:
-Live usb-s: lubuntu, gnome3 do exactly the same on the laptop.
-unplugged everything (second monitor, usb splitter, usb to jack adaptor, usb mouse) still does the same.
-when it's off, it's woring perfectly, except the fact that I can't see anything(second monitor just turns off, with no signal, Caps Lock works). What I do, is I try to get in tty, **blind of course**, and restart from there if I can, or I just press the power button until it shuts down.
-with the intel driver it does the same
-apport doesn't really register anything.

It's getting a little bit frustrating, and I have to try it all the time. It's like havin something on your tounge, I always have to check if it's still there...
I'm not sure if it's important, but I changed the hdd a few years back and I also changed the CPU a couple of months ago.


On a different note, it's been 4 years since I last posted here! That's proof on how far ubuntu has come and how good this forum works!

Thanks guys!

---

### Post by Vladlenin5000 on 2014-10-18
Hi, welcome back.

Just one preliminary question: How does it work (or worked) in Windows? Have you had the chance to test that other OS after the CPU upgrade (the HDD should have no bearing in this issue)?

---

### Post by duruttye on 2014-10-19
I actually changed it a few months back and both ubuntu and windows worked fine with it for aproximatelly 4 months, I started the windows 2 or three times during this period.
I am also monitoring the temperature of the CPU and under normal usage is around 45-50C, heavy usage 75C. I can't see why the CPU would do something like this.
I can reproduce it every time. The screen freezez for a few seconds, then it turns off, but afterwards eveyrthing works fine, as far is I can tell. The music is still on, I can Alt-Tab to a terminal and reboot it from there by blindly typing in sudo reboot and then the password.

Thank for looking!

---

### Post by Vladlenin5000 on 2014-10-19
The temps aren't bad but not ideal either...
A newer more powerful CPU may or may not work fine - notebooks' motherboards are much less "forgiving" than their desktop counterparts - and it may work fine for some time but then create another hardware issues due to the system being "stressed" beyond what it was originally tested for. Your symptom is consistent with either a GPU or a voltage regulator intermittent failure. The root cause may or may not be the aforementioned "stress".
Other hardware failures unrelated to the upgraded hardware are also possible due to "old age".

I suggest you test it with the Dell 32 Bit Diagnostics (AKA "Dell Diags") -> Download the .exe file in a Windows computer (or VM) and run the auto-extract; open the extracted folder and then the "readme" file where you'll find instructions for making a bootable USB pendrive. Boot it and follow instructions to run the full tests.

---

### Post by duruttye on 2014-10-20
Thank you for your response!

Unfortunatelly there is no windows on this computer anymore. Or fortunatelly... whatever you might prefer.

The upgrade wasn't that big. I swapped my original Intel T2410 (2 GHz) with an Intel T7500 (2.2 GHz) processor, the difference is not that much.


Do you still think it's possible that it's related to the change? If yes, is it damaged for good, or putting the old CPU back will solve the problem?
I'll deffinitelly buy another laptop, but I still have the original CPU and I would like to donate the laptop for a charity with the right information with it.

Thanks again!

---

### Post by WinEunuchs2Unix on 2014-10-20
I might be a little off-base here but my gut tells me:

1) Don't click on the link that locks up your machine.
2) Get google chrome instead from Ubuntu Software Centre / Center.
3) If that doesn't work then yes put your old CPU back in.

I think it is ill-advised to put a new CPU in any machine these days (20 years ago sure ok whatever).  You can buy a used machine from 2 years ago if saving money is the objective.

---

### Post by duruttye on 2014-10-28
Hey!

1. as I found out since then, there are many things that lock up the laptop, that I can't really avoid
2. I got it in the meantime
3. taking it apart again might be the only solution now, but I have to take out everything to get to it again :)

As I said earlier, I don't think that the upgrade was that big, but then again, I'm no expert :)

Thanks for the reply guys!

---

