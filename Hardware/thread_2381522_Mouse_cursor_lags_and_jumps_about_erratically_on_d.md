---
title: "Mouse cursor lags and jumps about erratically on desktop!"
date: 2018-01-02
forum: Hardware
---

### Post by cybrsaylr on 2018-01-02
At first thought it was a defect with my wireless mouse. Bought a new mouse and this weird lag and jumping about cursor issue still happened! Tried a couple other mice I use on another PC and laptops I have and this weird jumping around and lag still occurs. 

Anyone have and idea what is causing this? It happens with the Dell i7 desktop running 16.04 LTS in my signature.

---

### Post by cybrsaylr on 2018-01-03
Thought I may have fixed this mouse lag/jumping issue in my i7 desktop but it returned a few minutes ago.

Here's what i have.
i7 desktop has 3 drives, 1 HDD and 2 SSDs.

On those 3 drives there are 5 OSs, Ubuntu 12.04, Ubuntu 14.04, Ubuntu 16.04, Windows 7 and Windows 10 and they all have been running and playing well with each other for years with no problems. 

Booted up in each of those other OSs in the above order to see if this lag/jump issue was in them also. It was in the 3 Ubuntu OSs and Widows 7 but Windows 10 ran fine with no mouse lag/jumping about!

Then went back into Ubuntu 16.04 and the lag/jumping was still there.
Then ran BleachBit and BleachBit as Administrator and lag/jumping mouse issue seemed to go away. All seemed normal again with the mouse for a day. 
Earlier today all was still normal. Then a few minutes ago I come back to my i7, wake it up and mouse is acting jumpy and lag has returned.

Anyone have any idea what may be causing this mouse issue and what the remedy to fix this is?

---

### Post by cybrsaylr on 2018-01-08
Been doing some trouble shooting on this issue last couple days, since getting zero help or ideas from this board. 

Last night I tried plugging the wireless mouse receiver into other USB ports. A couple of the other USB ports on front of the i7 did nothing to resolve this mouse lag. 
Originally had always used USB ports on desktop front for wireless mice.
However since using a USB port on the i7 rear panel  last night, the mouse jumpy & lag issue seems to be fixed! 

Anyone have any input on this?

Hoping this discovery, fixed this very annoying problem.

---

### Post by vbotka-9 on 2018-04-08
In my case the problem disappeared when I disabled lm-sensor provider in psensor [http://wpitchoune.net/psensor/](http://wpitchoune.net/psensor/). I reported the issue on github [https://github.com/groeck/lm-sensors/issues/99](https://github.com/groeck/lm-sensors/issues/99)

---

### Post by stewartnjohnston on 2018-09-12
I had a very similar problem and I traced it to my USB hub.  When I removed the USB hub my mouse jitter/jerk problem went any.  The weird thing is the first few months I had this hub plugged in I did not have this problem.  So either the hardware or drive has gone bad.  I do miss my hub.

It is possible that an upgrade was pushed on me and that has broken the USB driver.  I have not tested other OSs (Windows).

I will continue to experiment.

Good Luck!

Stewart

---

### Post by lerudd on 2018-12-10
@cybrsaylr, that seems to have done it for my jumpy mouse as well -- i had it plugged into a USB3 port on a USB3 extension cable, and it just started jumping around a couple days after reconfiguring it to this hardware. i read your post and thought, yep, need to try this. swapped to a USB2 port (different driver) and baddabing. immediately no jumpiness. thanks for posting your trevails

---

### Post by lerudd on 2019-01-14
> **lerudd said:**
> @cybrsaylr, that seems to have done it for my jumpy mouse as well -- i had it plugged into a USB3 port on a USB3 extension cable, and it just started jumping around a couple days after reconfiguring it to this hardware. i read your post and thought, yep, need to try this. swapped to a USB2 port (different driver) and baddabing. immediately no jumpiness. thanks for posting your trevails

update: i was wrong. mine continues to do this despite the switch. it seems to do it when i first log in, and over time it seems to become better during the session. sometimes it's so bad i consider changing distros. the lag is immensely frustrating. i have updated to kernel 4.20 and that is of no help.

---

### Post by strixtux on 2019-01-18
I had a comparable issue on a Dell inspiron 1525. My workaround: boot the shleptop without USB-mouse, plug it when the machine is up and enjoy life.18.10 Ubuntu Studio.

---

### Post by teknopaul on 2019-08-13
This can be that the mouse is running out of battery, if its wireless.

---

### Post by DuckHook on 2019-08-13
Please do not necromance old threads. Original thread author has long since left the building.

*Thread closed.*

---

