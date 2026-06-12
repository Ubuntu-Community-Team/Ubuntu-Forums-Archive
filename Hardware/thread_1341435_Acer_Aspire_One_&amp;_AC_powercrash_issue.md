---
title: "Acer Aspire One &amp; AC power/crash issue"
date: 2009-11-29
forum: Hardware
---

### Post by Thinkwritemute on 2009-11-29
Computer: Acer Aspire One (160gb)
OS: Ubuntu Netbook Remix 9.10


Problem: When I plug or unplug the AC power cord Ubuntu goes into suspended mode. The Networking App dies, the Sound dies, the computer enters a suspended mode (Pulsing orange power button).

Hitting any key wakes the computer back up. The computer then repeats the above and then freezes. Pressing any key does nothing. Pressing the power button seems to turn the machine off then restart it, with all the windows and applications still in place as if nothing ever happened.

Obviously since this is a netbook this is a problem. Netbooks need to be able to easily switch from battery to AC.


Any ideas, guys?

---

### Post by nicoalmontec on 2009-11-29
I've got this same problem, I have an AspireOne netbook like yours, I 've been asking and researching for a while now and I cant find a solution. 

Can anyone please give us a feedback on this?

---

### Post by Aearenda on 2009-11-29
Can you confirm which AA1 you have - look for the 'Model No' on the sticker underneath. Mine says 'ZG5'. 

What BIOS version do you have? It should show this if you press F2 at boot time.

What battery settings do you have for battery mode in the power manager? (system->power manager)

EDIT: Looks like you might have hit [bug 425411]("https://bugs.launchpad.net/ubuntu/karmic/+source/gnome-power-manager/+bug/425411").

---

### Post by Thinkwritemute on 2009-11-29
Model: KAV60
BIOS: Don't know (Will check)

Here's a log of power manager (attached.

---

### Post by Aearenda on 2009-11-29
KAV60 is also known as an Aspire One D250 or AOD250. Unfortunately, mine is older, so probably not directly comparable.

There was a problem with double-suspending on mine during Karmic beta, but I haven't hit it recently. It certainly doesn't happen for me when removing AC power. 

There's a line in the log you provided that says ```
TI:16:10:15	TH:0x9f84168	FI:gpm-manager.c	FN:gpm_manager_action_suspend,446
 - suspending, reason: The lid has been closed on ac power.
```
Did you close the lid then?

EDIT 2: Please post the output from running this in a terminal: ```
cat ~/.gconf/apps/gnome-power-manager/buttons/%gconf.xml
```


EDIT 1: By the way, rather than forcing the system off with the power button, try this when it freezes:

1. Hold down ALT and SYSRQ and press K.
   If the GUI restarts at this point, log in again and off you go.

2. Hold down ALT and SYSRQ and press and release these keys in order, holding ALT and SYSRQ right through: REISUB
   This makes the kernel do a safe emergency reboot.

---

### Post by Thinkwritemute on 2009-11-29
No, I didn't close the lid. I wonder why it would think that?


What is the SYSRQ button?

---

### Post by wilee-nilee on 2009-11-29
> **Thinkwritemute said:**
> No, I didn't close the lid. I wonder why it would think that?


What is the SYSRQ button?

It is a dual button on your keyboard, 4th from the right at the top on my acer. Also if you use that shutdown method reisub give a few seconds between each key hit. Also reisuo=o=off the 
b=reboot or boot.

---

### Post by Aearenda on 2009-11-29
SYSRQ (System request) is the same key as PRTSC (print screen). Wilee-nilee was right to warn about the delay between keys (thanks).

I suggest you set the power manager settings for both power and bettery to do nothing automatically for the present - lets see if we can stop the undesirable behaviour first. I suspect the underlying issue is a bug as I said before.

To do this:
1. Start the power manager UI from either system->preferences->power manager or by right-clicking the power icon at top right.
2. On the 'AC Power' tab, set the sleep option to 'never', and the lid option to 'do nothing'.
3. On the 'Battery Power' tab, set the 'sleep when inactive' to 'never', and the lid option to 'do nothing'.
4. On the 'general' tab, set the power action to 'ask me'.

Now see what happens when you remove the AC power....

---

### Post by Thinkwritemute on 2009-11-29
There was no "Do nothing" option, but there was a "Blank Screen".

As soon as I unplugged the screen went blank (once).

Looks like it's a bug where unplugging == closing lid.

---

### Post by Aearenda on 2009-11-29
Ah yes, the do-nothing option is missing in the ui - you have to set it in gconf-editor, like so:

1. Press ALT and F2 to bring up the 'run command' box.
2. Type 'gconf-editor' (without the quotes) and press ENTER.
3. Find /apps/gnome-power-manager/buttons/ in the tree on the left.
4. Double-click 'lid_ac' in the right pane.
5. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
6. Double-click 'lid_battery' in the right pane.
7. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
8. Close the editor.

That aside, we now have a system that no longer suspends when power is removed, and it certainly sounds as if it is the lid close action that is the problem. If the gconf settings I just gave prevent the screen blank as well, that seems to confirm it.

So, next I would put the sleep options for both AC and battery power back to how you want them, but leave the lid settings as they are, and see if the power removal action causes any undesired effects.

What we really need to do after that is to go into the power management innards and find out more, as the bug I mentioned above suggests, but I have to go out now and won't have the time to help you with that this week. You could either (1) start a new thread with a title such as "AC Power removal triggers lid switch action" or (2) Search for an existing bug that matches more accurately in launchpad, and start a new one if none.

By the way, on my AA1, Fn and F6 make the screen blank, so the lid switch isn't really essential.

---

### Post by gian unr on 2009-12-07
It worked for me, Acer Aspire One D250. now it doesn't freezes anymore when switching power...thanks a lot!

Gian

---

### Post by wilee-nilee on 2009-12-07
> **gian unr said:**
> It worked for me, Acer Aspire One D250. now it doesn't freezes anymore when switching power...thanks a lot!

Gian

Same here never thought of gconf, I had only had to unplug or plug a couple of times.

---

### Post by basotl on 2009-12-19
I also have two AOD250 that had this issue. Using the above fix is a nice work around for the undesired behavior.

---

### Post by anthonyk007 on 2009-12-31
Bought mine Acer D250 yesterday and had the same problem, but it went away after I downloaded and upgraded the latest BIOS version 1.25 (mine came with version 1.02) via Acer Support website (I also upgraded Intel Chipset Driver at the same time though it is less likely to be the culprit). I can now use any settings in Power Management without problem. 

Hope that helps.

Anthony

---

### Post by basotl on 2010-01-06
> **anthonyk007 said:**
> Bought mine Acer D250 yesterday and had the same problem, but it went away after I downloaded and upgraded the latest BIOS version 1.25 (mine came with version 1.02) via Acer Support website (I also upgraded Intel Chipset Driver at the same time though it is less likely to be the culprit). I can now use any settings in Power Management without problem. 

Hope that helps.

Anthony

Did the Bios update exe work via Wine or were you using Windows during the Bios update?

---

### Post by anthonyk007 on 2010-01-10
Mine is dual boot xp/Ubuntu so it was done via xp.

---

### Post by Morten Hattesen on 2010-02-13
> **Aearenda said:**
> Ah yes, the do-nothing option is missing in the ui - you have to set it in gconf-editor, like so:

1. Press ALT and F2 to bring up the 'run command' box.
2. Type 'gconf-editor' (without the quotes) and press ENTER.
3. Find /apps/gnome-power-manager/buttons/ in the tree on the left.
4. Double-click 'lid_ac' in the right pane.
5. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
6. Double-click 'lid_battery' in the right pane.
7. Type 'nothing' (without the quotes) into the box that pops up, and press ENTER.
8. Close the editor.

That aside, we now have a system that no longer suspends when power is removed, and it certainly sounds as if it is the lid close action that is the problem. If the gconf settings I just gave prevent the screen blank as well, that seems to confirm it.

So, next I would put the sleep options for both AC and battery power back to how you want them, but leave the lid settings as they are, and see if the power removal action causes any undesired effects.

What we really need to do after that is to go into the power management innards and find out more, as the bug I mentioned above suggests, but I have to go out now and won't have the time to help you with that this week. You could either (1) start a new thread with a title such as "AC Power removal triggers lid switch action" or (2) Search for an existing bug that matches more accurately in launchpad, and start a new one if none.

By the way, on my AA1, Fn and F6 make the screen blank, so the lid switch isn't really essential.

This works great for me. But it would really be nice to be able to find a proper solution to allow suspend mode with the Acer Aspire D250 on lid-close.

How can I help in getting this solved?

/Morten

---

### Post by Objekt on 2010-05-11
This issue is still around.  I noticed it on an Acer Aspire One D250 running Ubuntu Netbook Remix 9.10.  I've had the netbook for several months and have kept it updated religiously, but it still does the "hibernate upon unplugging AC adapter while powered up" thing.  A press of the power button brings it back quickly, but it's not supposed to work that way.

I wasn't aware of the gconf fix given above, so I'll have to try it next time I have access to the machine (it was a belated Xmas gift for someone last weekend).

For a while, I thought it was just me, or that I had unintentionally set the power savings in a strange way.  I gather I'm not the only one seeing the problem.

---

### Post by Aearenda on 2010-05-11
It seems to me that the BIOS upgrade mentioned in post 14 is the real fix - the gconf settings I posted are only a circumvention of the problem. I can't be sure as my Aspire One is a different model.

---

### Post by Objekt on 2010-05-12
I confirmed last night that the problem also happens with my AAO D150-1920.  

BIOS does seem to be where it's at.  I updated the BIOS on my two Aspire Ones immediately after buying them last fall, but haven't checked for new BIOS since then.  I see now that there have been a couple of BIOS updates for both D150 and D250 models since then.

Update:
I flashed the newest BIOS (1.13 I think) on my D150 last night.  The "hibernate when plugged in/unplugged" bug is GONE!  Time to update the D250 as well.

FWIW, you can run the "DOS" version of Acer's BIOS update off a FreeDOS boot volume.  I used a USB stick, formatted with FreeDOS 1.0 using Unetbootin.

---

### Post by gian unr on 2010-11-16
That solution still works for me...note that since last year I switched to desktop edition.

I couldn´t stand UNR bugs anymore!!!

Have good one everyone:guitar:

---

