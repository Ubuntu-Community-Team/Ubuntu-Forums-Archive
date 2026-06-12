---
title: "Ultraportable Recommendations under Gutsy"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by nodeless on 2007-10-16
I'm looking for a really sturdy ultraportable (lots of travel to and from the office) to last me for the next several years, but it's difficult to find information on the options I'm looking into.

I've basically narrowed my choices down to the Panasonic W7, the Vaio TZ, and the Lenovo X61. I'm leaning towards the Vaio and the Panasonic (especially the Panasonic) for battery life, although it seems like I'll have the best community support with something more common like the Thinkpad. Also, the Fujitsu T2010 looks pretty good... Again, I'm looking for something really sturdy and well-built.

Anyhow, does anyone have any experience running Gutsy on these models? I know that Feisty was troublesome on these, but I'm hoping that Gutsy has better out-of-the-box support?

Thanks!!

---

### Post by RedGreen on 2007-10-20
> **nodeless said:**
> I'm looking for a really sturdy ultraportable (lots of travel to and from the office) to last me for the next several years, but it's difficult to find information on the options I'm looking into.

I've basically narrowed my choices down to the Panasonic W7, the Vaio TZ, and the Lenovo X61. I'm leaning towards the Vaio and the Panasonic (especially the Panasonic) for battery life, although it seems like I'll have the best community support with something more common like the Thinkpad. Also, the Fujitsu T2010 looks pretty good... Again, I'm looking for something really sturdy and well-built.

Anyhow, does anyone have any experience running Gutsy on these models? I know that Feisty was troublesome on these, but I'm hoping that Gutsy has better out-of-the-box support?

Thanks!!

When it comes to sturdy laptops Thinkpads are very hard to beat. I own an X61s and this thing is a rock, it is going to last a very long time and is not going to fall apart. I have not used to many laptops in my day but I still highly recommend the X61 Thinkpads, they are going to hold up to what you throw at them. And being able to get about 6 hours of use from one battery charge (with the 8 cell battery) really comes in handy.

A lot works right out of the box with Gutsy (list from thinkwiki.com):
works:
    *  3D rendering
    * Hot keys: sound, brightness, keyboard light, monitor, suspend
    * LAN
    * WLAN
    * ACPI, battery monitor
    * Sound card
    * Bluetooth 
does not work:
    *  suspend fails: seemingly due to the ipw3945 ethernet driver
    * Trackpoint's mouse wheel emulation 
    * Desktop Effects

What doesnt work there are fixes for, I have not been able to get all of the possible compiz effects working well but the cube works fine as well as most everything else. The reason Desktop Effects does not work out of box is because the X3100 graphics are blacklisted, this is mainly due to an issue playing video while its enabled (video wont play). There are workarounds for this problem.

I have posted a partial list in the Thinkpad specific forums for how I got things working: [http://forum.thinkpads.com/viewtopic.php?t=50949](http://forum.thinkpads.com/viewtopic.php?t=50949)

Good luck making your decision, if you have any questions about the X61 be sure to let me know.

---

### Post by jsully1 on 2007-10-20
I can't sing the praises of the thinkpad enough - I have a T60 that's held up insanely well.  A coworker of mine has the X61 and he's been impressed by it.  My only complaint is that the screen resolution is a bit low, but you're going to run into that with most ultraportables.  If you're looking outside of the thinkpad, take a look at the Dell XPS, and the Sony Vaio Ultraportables.  I've owned both in the past and they're quite good.  The reason I keep going back to the thinkpad though is for the build quality and the Trackpoint - the little red nub thing.

Also worth noting that absolutely everything (wireless, graphics card, bluetooth, screen resolution) has worked out of the box with my thinkpad T60 since 6.04.  Getting suspend to work properly sometimes takes a few minutes, but other than that it's great.

---

### Post by RedGreen on 2007-10-20
> **jsully1 said:**
> I can't sing the praises of the thinkpad enough - I have a T60 that's held up insanely well.  A coworker of mine has the X61 and he's been impressed by it.  My only complaint is that the screen resolution is a bit low, but you're going to run into that with most ultraportables.  If you're looking outside of the thinkpad, take a look at the Dell XPS, and the Sony Vaio Ultraportables.  I've owned both in the past and they're quite good.  The reason I keep going back to the thinkpad though is for the build quality and the Trackpoint - the little red nub thing.

Also worth noting that absolutely everything (wireless, graphics card, bluetooth, screen resolution) has worked out of the box with my thinkpad T60 since 6.04.  Getting suspend to work properly sometimes takes a few minutes, but other than that it's great.

Your right about the screen resolution, 11024x768 is a little low for a 12" screen. But once you get used to it is is very usable. And if your good at taking advantage of multiple desktops you wont feel like you need more space. It is also worth considering merging your panels into one for a little more space. Also, a lot of people go for the X6x tablet versions which have an SXGA LCD with a much higher resolution (might be an option for an SXGA+ screen but I dont recall).

The trackpoint is the reason I would have to be dragged to any other input on a laptop kicking and screaming. Only having to move your hand a fraction of an inch to go from typing to moving around the cursor is great. Also, having a third mouse button is really nice.

---

### Post by andrewkk on 2007-10-20
I'll second all that the others have said about ThinkPads. I love my X60.

Do check out thinkwiki.org, it does an excellent job of covering many of the picky little things that require extra effort to make work properly.

---

### Post by melocotone on 2007-10-20
I have a Vaio TZ11MN (80GB / 1Gb) with a dual partition Vista/Ubuntu 7.04. 
7.04 works much better than Vista but the web cam is not detected and the built-in SD/SDHC reader is also not detected. Not a big deal, as an USB reader works perfectly.

Yesterday I burned 7.10 on a CD and tried it on the TZ. Unfortunately the sound is not working under 7.10 while it it is working perfectly under 7.04. It has to do with the 82801G (ICH7 family) High definition audio controller that seems to be broken under 7.10 !

Thus for the time being I will not upgrade until I find some solution for that...

---

### Post by kiloecho7 on 2007-11-01
My vote is in for the Thinkpad x61s.  It's definitely built like a rock.  I'm dual booting Vista and an encrypted Ubuntu 7.10 and the only qualm I have at this point is the battery life.  I get upwards of 7 hours in Vista and 4.5 in Ubuntu.  Everything works out of the box except for any specialized screensaver makes x crash.  I've began a wiki on the x61s on the Ubuntu Team Wiki but it is not terribly up to date.  Happy to answer any questions you might have.

---

### Post by linguini on 2007-11-02
I'm using Gutsy on a ThinkPad X61, and almost everything works. Occasionally there are some problems when waking the computer from sleep (wireless not working, or the computer simply doesn't wake up properly), but this doesn't happen often. Overall, I'm very happy; and given how new this model is, it works much better with Linux than what I expected.

---

