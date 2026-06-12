---
title: "fixed fglrx suspend"
date: 2008-10-26
forum: General Help
---

### Post by ezzieyguywuf on 2008-10-26
The following worked for me in order to get fglrx to suspend and resume successfully with compiz! open /usr/lib/hal/scripts/linux/hal-system-power-susped-linux and in the last if statement, after the comment about how they only support pm-utils, add a line before /usr/sbin/pm-suspend and type in 'sleep 5' without quotes (i don't know if lower sleep values will work, though i'm sure they will. please, experiment and let me know!). Then, on the next line (the /usr/sbin/pm-suspend) add '--quirk-radeon-on' without quotes. now save! suspend and resume should work!

the only problem i have is with my wireless not coming back on properly. i don't know what the problem is and am hoping one of you ubuntu gurus can. i was eventually able to connect after repeatedly trying to connect, but gnome-power-manager is confused and thinks that i am connected to a 'wired connection' when really its wireless. any help would be helpful. hope this helps other users!!!

update: the wireless problems seems to be an isolated incident. I have been able to repeadetdly Suspend and resume without any wireless issues. 

update: it appears that consecutive suspend-resume cycles breaks my solution. I think it may have something to do with my comp not being done running through the  resume scripts before i've hit suspend again. What i mean is that everything *looks* like its all done resuming, but potentially there could still be stuff going on in the background. I will experiment further and let you guys know what I find.

---

### Post by ezzieyguywuf on 2008-10-28
*bump* i'd like to hear other people's feedback on whether or not this works for them...

---

### Post by tw33 on 2008-11-04
Didn't work for me.
I'm not sure radeon-on is even a valid quirk, only radeon-off.
pm-suspend doesn't work whatever I do (it just closes x and freezes with a cursor blinking in the corner) and frankly I'm bored of fiddling with it.
probably gonna stick with shitty vista until it gets fixed, unless someone has any decent suggestions.
btw: Intrepid with Radeon 3100 - fglrx seems to be the culprit, otherwise its the rtl8187b wireless card, how can I even find out?

*edit*
FIXED IT!! WOOOOO turns out it was nothing to do with fglrx (which works ok, little slow to turn the screen back on is all)
it was the rtl8187b card that was messing me up, i fixed it by doing adding:
unload_modules="rtl8187" in /etc/pm/config.d/modules

---

### Post by gatman3 on 2008-11-16
Nope, didn't work for me.  Resume locked up with a partially garbaged up screen, just like without this tweak.  I have a Mobility Radeon HD 3650.  Otherwise, suspend and hibernate work great as long as compiz isn't enabled and hasn't been enabled since the last boot.

---

### Post by Zer0Nin3r on 2008-11-16
> **ezzieyguywuf said:**
> 
the only problem i have is with my wireless not coming back on properly.


Does utilizing '*ifconfig up/down*' from the console work after your resume?  While I have problems with suspending and hibernating, sometimes it helps to "reset" the wifi.

---

