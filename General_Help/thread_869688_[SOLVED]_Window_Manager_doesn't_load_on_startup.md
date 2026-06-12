---
title: "[SOLVED] Window Manager doesn't load on startup"
date: 2008-07-25
forum: General Help
---

### Post by hidinginthemountains on 2008-07-25
For the past few weeks (since doing I-don't-know-what-change) Compiz does not start when I log in. There is only one workspace, and I have no window decorations. The best I can figure is that this started shortly after I gegan using Emerald, but it worked fine the first few times I logged in after that.

As a work around I have Compiz Fusion Icon on my panel, from which I "Reload Window Manger". Following that, everything is just fine (Compiz, Emerald, etc. ...all good).

I had posted in [this related thread]("http://ubuntuforums.org/showthread.php?p=5452953#post5452953"), but was asked to start a fresh one since the OP had marked it as solved.

I would really appreciate some help on this. Any hints as to what I should be looking at, or posting here for reference would be great.

I'm running Ubuntu 8.04 on a Toshiba laptop.

---

### Post by northern lights on 2008-07-25
Navigate to "System > Preferences > Sessions" and add compiz to the Startup Programs.

Either using the command "compiz" or "compiz --replace".

---

### Post by hidinginthemountains on 2008-07-25
I just tried that, unfortunately it made no difference.

I did notice something strange though. I removed conduit (I don't use it, so...) from the startup applications (same dialogue box as above), but it still started following my reboot. Any possible relation between these two occurrences?

---

### Post by infiniah on 2008-07-25
same

---

### Post by overdrank on 2008-07-26
> **hidinginthemountains said:**
> I just tried that, unfortunately it made no difference.

I did notice something strange though. I removed conduit (I don't use it, so...) from the startup applications (same dialogue box as above), but it still started following my reboot. Any possible relation between these two occurrences?

Hi on the third tab in sessions, Sessions options do you automatically remember apps  checked?

---

### Post by hidinginthemountains on 2008-07-26
No, I've always manually clicked-the-button, and left that unchecked. I'll go and click-the-button now, restart, and see if that does it.

---

### Post by hidinginthemountains on 2008-07-26
I saved the session, then rebooted (I don't know that I need to reboot as opposed to just logout-login ...but old Windows habits can die hard). Same as last time, problem persists. Conduit still starts as well, even though I removed all references I could find to it. Conduit isn't really my problem here, but its behavior does seem to indicate that my changes aren't happening.

Is there a particular file where this config information is stored? Am I right in thinking that the Sessions dialogue only applies to my account? Could there be a more "Global" system-wide configuration that is overriding these changes?

Thanks for continuing to try and help.

---

### Post by hidinginthemountains on 2008-07-27
I should also note (since my last boot reminded me) that occasionally one or both of my panels don't show up after logging in.

I seem to recall having some issue back with 7.10 where I needed to change the boot order of some things because they were trying to start at the same time...could this be the same type of problem?

---

### Post by RuleMaker on 2008-07-27
Try to create a launcher with command:
"compiz --replace"
And then add that launcher to startup, System->Preferences->Sessions->Startup

---

### Post by hidinginthemountains on 2008-07-27
That's what I did in accordance with northern lights' reply (second in thread), isn't it?

---

### Post by northern lights on 2008-07-27
> **hidinginthemountains said:**
> That's what I did in accordance with northern lights' reply (second in thread), isn't it?
yup. redundant.

> **hidinginthemountains said:**
> I should also note (since my last boot reminded me) that occasionally one or both of my panels don't show up after logging in
If you're panel(s) are/is gone, run ```
gnome-panel
``` to restore.

As for the conduit/compiz issue i ain't so sure what's happening, lemme think about it.

---

### Post by hidinginthemountains on 2008-07-31
The Panels thing is a lesser problem for me (bigger than my suspend-hibernate-doesn't-work <does anybody's?>, but smaller than the window manager not starting). One other bit of behavior regarding it though, the panel(s) only fail to load following signing in after logging out. If it is my first sign in after a fresh boot, they always appear.

Any answers on what files contain the load order for things like windows managers, decorations, and whatnot? And (where) are they different for a specific user vs. globally?

Thanks for taking shots at this.

---

### Post by hidinginthemountains on 2008-07-31
[This issue]("http://forum.compiz-fusion.org/showthread.php?t=7495") could be related. Though the post is regarding Suse, I ran the same command and got this:

```
ps -ef | grep comp
mercer   10216     1  0 04:04 ?        00:00:00 /bin/sh /usr/bin/compiz --replace
mercer   10274 10216  0 04:04 ?        00:01:06 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --replace core ccp
mercer   13161 13129  0 14:05 pts/0    00:00:00 grep comp

```

Here's another bit as per that link:
```
locate -ir 'compiz-manager$'
/etc/xdg/compiz/compiz-manager
/usr/bin/compiz-manager

```

Maybe there's a hint in there I'm missing?

---

### Post by hidinginthemountains on 2008-07-31
The following is an excerpt from my [FONT="Courier New"]usr/bin/compiz-decorator[/FONT]

```
#
# Default to gtk/kde(4)-window-decorator
#
USE_EMERALD="no"
DECORATOR=""

#Do not leave users without decoration if decorator fails
if [ "$DESKTOP_SESSION" = "kde" ]; then
    FALLBACKWM="${KWIN}"
else
    FALLBACKWM="${METACITY}"
fi
FALLBACKWM_OPTIONS=" --replace"
```

...am I reading this wrong in thinking that it should read:
```
USE_EMERALD="*yes*"
DECORATOR="*<something>*"
```

---

### Post by liquidthex on 2008-08-06
Any updates on this? I'm having the same issue.. It just refuses to start on login.

I do have compiz and emerald setup to run through a script run from sessions.

I did notice something odd:
When I log out and log back in it starts up just fine.
But when I login for the first time after booting it does not.

---

### Post by hidinginthemountains on 2008-08-06
well, "unfortunately" I do have a bit of an update.

As of a couple days ago, my computer "fixed itself". I have no idea what went right. It just suddenly started working properly. I didn't get any updates that I think would impact it. I really wish I could offer you some hints. I'll go back and peek at some config files to see if I can find out what changed. I'll post again before I mark this as [SOLVED]...

the only thing I notice as different is that now I get:
```
mercer@nexus-6:~$ ps -ef | grep comp
mercer    6182  6141  0 17:01 pts/0    00:00:00 gedit /usr/bin/compiz-decorator
mercer    6256  6221  0 17:04 pts/1    00:00:00 grep comp
mercer   14182     1  0 Aug04 ?        00:00:00 /bin/sh /usr/bin/compiz --replace
mercer   14240 14182  1 Aug04 ?        00:29:10 /usr/bin/compiz.real --ignore-desktop-hints --replace --indirect-rendering --replace core ccp

```

---

### Post by liquidthex on 2008-08-07
Well I think I fixed it (for me anyways) here's what I did:

TL;DR Put it in /etc/gdm/PostLogin/Default instead of the Sessions window.

1) Remove any compiz/emerald entries from your System->Preferences->Sessions.
2) Create a new file, name it something like startcompiz.sh and put the following:
```
#!/bin/sh
compiz --replace &
emerald --replace &
```
3) Save the file to some directory, in this example we'll say /usr/local/sbin/startcompiz.sh
4) In a console, do the following:
```
sudo chmod +x /usr/local/sbin/startcompiz.sh
cd /etc/gdm/PostLogin
sudo mv Default.sample Default
```
5) Open /etc/gdm/PostLogin/Default in a text editor (sudo gedit /etc/gdm/PostLogin/Default)
6) Type the path and filename to your new script in the file:
```
/usr/local/sbin/startcompiz.sh
```
7) Save & Exit
8) Reboot & Enjoy

---

### Post by hidinginthemountains on 2008-08-07
Well, seeing as I don't have a problem anymore, and *you* don't have a problem anymore (nice solution btw, wonder if it would've worked for me?), maybe I should just mark this as [SOLVED] and anyone who has related issues can just link to this from a new thread if they want. Is that the proper way to handle this around here? If so, my next question becomes, how do I mark this as [SOLVED]? :)

---

### Post by overdrank on 2008-08-07
> **hidinginthemountains said:**
> Well, seeing as I don't have a problem anymore, and *you* don't have a problem anymore (nice solution btw, wonder if it would've worked for me?), maybe I should just mark this as [SOLVED] and anyone who has related issues can just link to this from a new thread if they want. Is that the proper way to handle this around here? If so, my next question becomes, how do I mark this as [SOLVED]? :)

Hi and you can mark it solved using the thread tools and also look at the link in my signature.

---

### Post by hidinginthemountains on 2008-08-07
I could swear I had looked in the Thread Tools before and didn't see it. Thanks!

---

### Post by cika.mancic on 2008-09-20
Not working.
It bugs all my compyz settings...
:confused:

---

### Post by ubuntopia on 2008-11-03
Hi all!
 Thanks to everyones posts I was able to figure out what was causing the problem and thus removed it. Now I just need to figure out why it caused this issue.
 My prob started after I created a startup Session for Compiz Fusion Icon and after a reboot the problem became apparent. I too had the same prob with Compiz settings being disabled and additionally, like some of the others, my Screenlets were all over the place and the individual screenlets themselves didnt look quite right.
 Now, one thing I eventually noticed (after a few restarts) was that Compiz (e.g. Cube effect) did actually function as soon as I logged on, but after a few seconds the problem occurred. So I'm thinking the problem occurs as soon as the system starts up the Compiz Fusion Icon.
 To solve (well actually just a work around) the problem I deleted the session for the Fusion Icon. Tested by rebooting and all is now as it should be.

I'll post back once/if I've sussed why Fusion Icon is causing the issue.

Cheers!

---

### Post by ubuntopia on 2008-11-03
Okay I found the solution rather quickly and a simple one it is. :)

The Command I had originally used for my Comp Fusion Icon Session was: fusion-icon 
I got this command off another post as being a noob I didnt know what to put here. But if you look at the properties of Compiz Fusion Icon (under /usr/share/applications) the command is actually:
```
fusion-icon --no-start
```

So I created a new session with this command and tested by logging/off on. All good!
Performed a system restart also. All good!!
Screenlets have been stable also!!!
The Compiz Fusion Icon is present in the Panel and functioning too.

---

### Post by alsamman on 2008-11-07
> **ubuntopia said:**
> Okay I found the solution rather quickly and a simple one it is. :)

The Command I had originally used for my Comp Fusion Icon Session was: fusion-icon 
I got this command off another post as being a noob I didnt know what to put here. But if you look at the properties of Compiz Fusion Icon (under /usr/share/applications) the command is actually:
```
fusion-icon --no-start
```

So I created a new session with this command and tested by logging/off on. All good!
Performed a system restart also. All good!!
Screenlets have been stable also!!!
The Compiz Fusion Icon is present in the Panel and functioning too.
Great Job!

And to the OP: The reason why I marked my thread as [SOLVED] is because the same thing happened to me as what happened to you; it fixed itself. However, this was on Hardy and now I moved to Intrepid and I got this problem again and thanks to ubuntopia, it works perfectly.

---

### Post by madone1 on 2009-01-31
[FONT="Comic Sans MS"]Thank you very much, it works for me, and I can now make conky "sleep" only 1 second in startup.sh file[/FONT]:popcorn:

---

### Post by osarusan on 2009-12-28
I had this problem too, and was baffled by it. Making a new startup launcher solves it, but I still was trying to figure out why it got messed up in the first place, rather than just throwing in a launcher.

I still don't know why it got messed up, but I found one clue. The "Appearance" settings from System>Preferences somehow got set back to "Non" from having full effects. This meant that Compiz was being loaded, but also disabled, leaving no Window manager. I re-enabled Desktop effects in that GUI menu, and now it loads perfectly again, no startup script necessary.

---

### Post by myoldhouse on 2010-01-11
My problems with lost window decorations occurred under both compiz and metacity and would seem to happen randomly, but once lost, nothing would bring the window decorations back except using "metacity --replace" as one of the startup scripts.

I finally had enough and decided to track this thing down and I found that sitting in my home directory under ./local/share/applications there were two files that were the root cause. One was named compiz.desktop and the other was named metacity.desktop. Deleting, renaming or moving those two files restores normal window decorations under both compiz and metacity.

I don't know what generates those files and puts them there but I know what to do to get window decorations back if they go missing - I look for those two files in ./local/share/applications and I delete them and I'm good until the next time they appear, which could be in days, weeks or months.

Your mileage may vary, but it won't hurt to try this if nothing else works for you in restoring your window decorations under either compiz or metacity.

PS My system is Ubuntu 9.10 AMD64 but I had this problem under 9.04 AMD64 as well and the fix worked for both of them.

---

### Post by Krzysztow on 2010-10-11
Thanks alot for a hint. It worked like a charm. And even now, everything loads faster. 
Thanks again, however it's wierd that things like this happened.

---

### Post by Krzysztow on 2010-10-11
> **myoldhouse said:**
> My problems with lost window decorations occurred under both compiz and metacity and would seem to happen randomly, but once lost, nothing would bring the window decorations back except using "metacity --replace" as one of the startup scripts.

I finally had enough and decided to track this thing down and I found that sitting in my home directory under ./local/share/applications there were two files that were the root cause. One was named compiz.desktop and the other was named metacity.desktop. Deleting, renaming or moving those two files restores normal window decorations under both compiz and metacity.

I don't know what generates those files and puts them there but I know what to do to get window decorations back if they go missing - I look for those two files in ./local/share/applications and I delete them and I'm good until the next time they appear, which could be in days, weeks or months.

Your mileage may vary, but it won't hurt to try this if nothing else works for you in restoring your window decorations under either compiz or metacity.

PS My system is Ubuntu 9.10 AMD64 but I had this problem under 9.04 AMD64 as well and the fix worked for both of them.

There is a wikipage about compiz, which discusses such a behavior. So what is needed is to change the entry in a compiz.desktop file.

[http://wiki.archlinux.org/index.php/Compiz#Autostart_.28without_.22fusion-icon.22.29](http://wiki.archlinux.org/index.php/Compiz#Autostart_.28without_.22fusion-icon.22.29)

I'll try it, hope this helps as well.

------------------------
After some time:

It occured that changing compiz.desktop file doesn't work. However what should work (it works for me for metacity) is that in one of these files 
compiz.desktop
or
metacity.desktop

the property hidden should be set to false. In the other file it should be true. 
According to [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html) if the "Hidden=true" exists, then something, which *.dekstop file references to, existed at some point in the past and not anymore. In my case for both these file I had true value. So Windows manager was not loaded for any of them. When I enabled metacity (hidden=false), then everything is ok. I have already turn on and off the computer for few times and this is still ok. 

When there were no files (removed) then some default settings were chosen and managers were launched.

Regards,
Krzysztow.

---

