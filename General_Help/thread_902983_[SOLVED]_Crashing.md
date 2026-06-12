---
title: "[SOLVED] Crashing"
date: 2008-08-27
forum: General Help
---

### Post by bamu07 on 2008-08-27
Hello, i've had a problem ever since 8.04 came out, and i've not been able to solve it, it's big time frustrating, i hope someone can help.

After awhile of uptime, Ubuntu will become entirely unresponsive. I'll open firefox, the little "Firefox is starting..." window will appear on my taskbar, and then it'll go away. If i open any applications, they fail to open. What's weirdest is if i open a terminal, it is just a white block with a window decoration. Not only that, if i shut it down by ctrl+alt+dlt, it beeps about 15 times before actually shutting down. I'm quite sick of this problem, it makes me love windows so much, and i don't want to.

any help would be appreciated.

---

### Post by Crafty Kisses on 2008-08-27
Could be a RAM issue, post the results of this command > top

---

### Post by bamu07 on 2008-08-27
[http://pastebin.com/m1d4b8090](http://pastebin.com/m1d4b8090)

---

### Post by StewartM on 2008-08-27
> **bamu07 said:**
> Hello, i've had a problem ever since 8.04 came out, and i've not been able to solve it, it's big time frustrating, i hope someone can help.

After awhile of uptime, Ubuntu will become entirely unresponsive. I'll open firefox, the little "Firefox is starting..." window will appear on my taskbar, and then it'll go away. If i open any applications, they fail to open. What's weirdest is if i open a terminal, it is just a white block with a window decoration. Not only that, if i shut it down by ctrl+alt+dlt, it beeps about 15 times before actually shutting down. I'm quite sick of this problem, it makes me love windows so much, and i don't want to.

any help would be appreciated.


For what it's worth, I'm having close to the same experience on my Zareason Limbo 2440 desktop. Except I lose sound entirely after I reboot Gnome after a ctrl-alt-backspace. It brings up the splash screen in silence. Only a reboot solves the issue.

I don't know how to issue a report because I can't get the terminal window to show what processes are running while in the Gnome.

This is not going to make me love windows (darned little chance of that), but what's a little frustrating is that Feisty never did this. I am getting the impression that we're gaining features in Ubuntu's progression but we are losing some of Linux's famed stability in the process. Just my 2c.

StewartM

---

### Post by StewartM on 2008-08-27
> **Codename said:**
> Could be a RAM issue, post the results of this command > top

Don't you have to go to the terminal to do this? I tried to open a terminal to see what processes were running (and if I could kill a process) but when this happens the terminal becomes non-responsive too. Only a reboot solves the issue.

The next time this happens, I'd be happy to try to get any information that will help identify this problem. This tends to happen after leaving Hardy running for extended periods.

I could dig through any logs if anyone could point me in the right direction. Right now in my home directory I'm not seeing anything illustrative yet.

-StewartM

---

### Post by bamu07 on 2008-08-27
See, the reason i don't think it's my ram is because 7.10 didn't do this at all, and i left that running for weeks at a time, but i may be wrong. Wish i could find a solution to this problem. It's system-breaking.

And it happens to me too after an extended uptime, it's so annoying.

---

### Post by StewartM on 2008-08-28
> **bamu07 said:**
> See, the reason i don't think it's my ram is because 7.10 didn't do this at all, and i left that running for weeks at a time, but i may be wrong. Wish i could find a solution to this problem. It's system-breaking.

And it happens to me too after an extended uptime, it's so annoying.

I don't think it's your RAM either,because it would also have to be my RAM. And I have 3G on a new computer. The fact that we are experiencing pretty much the same error points to a bug, either in our particular set-ups or in GNOME in general.

The next time it happens on my end I'm going to see if I can ctrl-alt-backspace, get the login screen, and then do an alt-f1 (which I think will give me a GUI-less login). Then I can try starting gnome with the with the gdm command and see if that works. (I'm searching and I think that this gets everything right, someone please correct me if wrong).

Alternatively even without sound I could try logging back in the GUI, and typing in the "top" and the ps commands and see (if the terminal responds) where I'm at.

Lastly, I am wondering if this is Firefox related. Since I have my Firefox profile running from an encrypted container, I could try dismounting the container (which breaks the Firefox link) and then restarting the GUI. If I get back everything OK then somehow this might be related to firefox, maybe even the firefox-flash bug. 

Are you running firefox?

-StewartM

---

### Post by bamu07 on 2008-08-28
I am using firefox. On a side note, i did MemTest86 for like 15 hours...12 passes...no errors. Gotta be something else.

---

### Post by bamu07 on 2008-08-30
I seem to have found the problem, StewartM. After checking logs, i found out that PulseAudio was erroring constantly; after disabling it, i haven't had enough uptime to make sure ( 12 hours now, usually it'd have crashed by now but theres been rare occasions where its went this long ), But disabling pulseaudio seems to have made my system much snappier regardless, totem works now and my cpu usage is much lower; java also works now, didn't work before i dropped pulse. Maybe this will help you too.

---

### Post by StewartM on 2008-09-03
> **bamu07 said:**
> I seem to have found the problem, StewartM. After checking logs, i found out that PulseAudio was erroring constantly; after disabling it, i haven't had enough uptime to make sure ( 12 hours now, usually it'd have crashed by now but theres been rare occasions where its went this long ), But disabling pulseaudio seems to have made my system much snappier regardless, totem works now and my cpu usage is much lower; java also works now, didn't work before i dropped pulse. Maybe this will help you too.

Thanks. I had been running for a number of days trying to see if this re-occurred, w/o success until just now. This was not for lack of trying...one day I inadvertently hit "shutdown" instead of "logoff" and broke a session, and another time a streak of uptime was broken by a power outage. It's hard to find out about a bug that takes forever to collect data on and is hard to collect data on when it does occur.

Just within the hour it re-occurred, after 3 days of running. And the first symptom (for me) is that you lose sound, trying to play something on Rhythmbox produces nothing (either "X"s on the playlist, or simply no response) so your answer makes sense. When I tried to log out through the GUI, the "Stop" button produces no response. 

So, I hit a CLT+ALT+BACKSPACE and got to a soundless login screen. I found out that I could log in (w/o sound) OK as my other users on this box, but not as the user that had experienced the problem. Then I did a ALT+CTL+F1, bypassed the GUI, and logged in to type in the "top" command as that user. There was only one process running that was non-root, and that was very generic (couldn't remember which), so I was stumped.

I had my sound settings set at "Autodetect" which was generic. I have, now on your recommendation, switched to ALSA for all modes and see if this solves the problem. If it does, we need to file a bug report.

-StewartM

---

### Post by bamu07 on 2008-09-06
Absolutely; let me know if it solves your case.

---

### Post by StewartM on 2008-09-08
> **bamu07 said:**
> Absolutely; let me know if it solves your case.

So far, no problems observed after being logged in almost 2 days.

I am going to switch off the machine this morning, but next weekend it should be up for almost 3 days. I'll see what I can do to stress the system (sound-wise, playing music via Rhythmbox and Deezer using Flash).

-StewartM

---

### Post by mkvnmtr on 2008-09-08
I don't know if this will help but when I first installed 8.04.1 I had problems with high CPU usage and really slow Firefox speeds. I never got to the point of a crash but it was not right. I finally added and removed so much software just to see what it was like that I decided to reinstall and quit playing around. On this install everything is perfect. I have never had Firefox work so fast and the whole system is very stable. I think that some update fixed the problem when applied before using the system. Or maybe it was something if Firefox that they fixed, The install took only an hour and this time I knew exactly what I wanted to add.

---

