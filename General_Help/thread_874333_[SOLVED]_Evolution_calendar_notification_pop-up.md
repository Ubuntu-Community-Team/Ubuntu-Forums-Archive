---
title: "[SOLVED] Evolution calendar notification pop-up"
date: 2008-07-29
forum: General Help
---

### Post by the real omni on 2008-07-29
Hi,

Currently evolution only displays a 5-second popup alert window for calendar appointment alarms. A tiny tray icon also appears, but I keep my tray hidden so the tray icon is useless.

I don't spend every waking minute of every waking day at the computer - a lot of the time I just check in periodically to see if I have any notification of new e-mails or if there are any appointment notifications.

I hunted and hunted and found this in the archives: [http://ubuntuforums.org/showthread.php?t=444342]("http://ubuntuforums.org/showthread.php?t=444342")

I've tried everything listed on that page and the pop-up notification window still disappears after 5 seconds.

Is it possible for me to just recompile the code, with the 5-second timeout value changed to 50000 seconds or something like that? If so, can anyone point me to what file and what line within the file I should look for in order to find the value to change before I recompile? If I do that, will I have to recompile manually with every new evolution update in order to stay current?

Is there a solution that anyone has found for this problem that wouldn't involve recompiling?

What I'd ideally like to have happen is to bypass the tray icon and popup notification bubble altogether, and just have evolution present the dialog that comes up when you click on the evolution alert icon in the system tray.

Any help would be appreciated!

---

### Post by rbmorse on 2008-07-29
When you enter the set alarm dialog, you can tell Evolution to run a program instead of flashing the popup.  tell it to start anything that will remind you of the appointment...like an editor with a message telling you to check your calendar for appointments, or something.

In my case, I tell Evo to start gedit and then in the arguments dialog line I entered alarm.txt

The file alarm.txt is in the root directory (/) and contains a line saying "This is an Evolution generated reminder message. Please check your calendar"

I suppose you could enter "evolution" in the program line and "calendar" in the arguments line and had it pop up your evolution calendar, but I haven't tried that.

---

### Post by the real omni on 2008-07-29
> **rbmorse said:**
> When you enter the set alarm dialog, you can tell Evolution to run a program instead of flashing the popup.  tell it to start anything that will remind you of the appointment...like an editor with a message telling you to check your calendar for appointments, or something.

I thought about doing that but then there's no convenient way to snooze the alarm like you can do with the dialog that pops up when you click the alert icon in the tray.

I either need to have that dialog pop up automatically or I need to edit the code to make the notification bubble stay up long. Problem is I don't know how to make the dialog pop up without the tray icon being clicked, and I don't know where in the code to look for what I need to change. 

Instructions for either of those two options would set me in the direction I need to go.

---

### Post by rbmorse on 2008-07-30
You can set the number of repeats and the repeat interval in the set alarm dialog.

---

### Post by the real omni on 2008-07-30
> **rbmorse said:**
> You can set the number of repeats and the repeat interval in the set alarm dialog.

In theory, but that's adding unnecessary steps and thus wasting time and it still isn't an effective solution because you have to put in some absurd number of repeats, then specify 5 then change 'minutes' to 'seconds'. And then if you're out of town over the weekend it's still ultimately useless for a monday morning meeting alert because even if you specify a huge number like 5000 repeats, that still only works out to 6 hours. If you routinely go out of town for 2-5 days, that means for EVERY SINGLE appointment you'd need to schedule a repeat of like 600,000 times. 

I'm trying to REDUCE the amount of monkeying around, not INCREASE it.

(note: the caps aren't meant to make me sound like a condescending dick, just there for emphasis.. take no offense!)

Ssooo... quasi-effective workarounds are _all_ right out of the question. I'm looking for an actual solution.

Anyone have any solutions?

Anyone know the contact info for an evo developer so I can ask them where I should look for the line of code that I'd have to change to recompile the way I want?

Many thanks

---

### Post by the real omni on 2008-08-15
(bump)

Still hoping someone can tell me where I can find the evolution source code and where to look for the variable/constant that controls how long the alert/notification popup stays on screen.

Any help would be greatly appreciated!

---

### Post by timzak on 2008-08-18
Sorry I have no solution for you, but this was the main reason I recently switched back to Thunderbird with the Lightning calendar extension.  There were many things I loved about Evolution, but the fact that it cannot pop up a calendar reminder in your face, was difficult to work around.  That old thread you linked was something I wish I would have found earlier to try, but I just spent a bunch of time migrating back to Thunderbird, so I'm not about to give Evolution another try.

Good luck!

---

### Post by hggdh on 2008-08-22
> **the real omni said:**
> (bump)

Still hoping someone can tell me where I can find the evolution source code and where to look for the variable/constant that controls how long the alert/notification popup stays on screen.

Any help would be greatly appreciated!

This thread was brought to my attention by an email to devel-discuss linking to it.

I will try to answer some of your questions:

1. Evolution development is done at Gnome; apart from some 4 local patches, we distribute Evolution pretty much as upstream delivers it.

2. You can always call on IRC, at irc.gnome.org, #evolution. There are always people hanging there, and most developers are there. Just remember -- ask your questions, and wait... patiently ;-)

3. You probably can get what you want/need by resetting the GConf entry "/apps/evolution/calendar/notify/notify_with_tray" (as stated in the old forum thread you referenced). There is *no* configuration dialog for that. YMMV, I do not schedule calendars, so I do not really know.

4. The code you may want to look at is *probably* at evolution/calendar/gui/alarm-notify (in case the gconf change above does not work). You can get the Evolution current source for your Ubuntu distribution by:

4.1 adding the source repositories (System/Administration/Software Sources, and then check on "Source code"; close Software Sources;
4.2 on a terminal, issue:
```
cd /somewhereYouWant
sudo apt-get update
sudo apt-get build-dep evolution
apt-get source evolution
```
5. after changing whatever you want to change (I personally suggest creating a patch under ./debian/patches, and bumping the version to something else), you can build it by issuing, on a terminal:
```
cd /somewhereYouWant
apt-get -b evolution
```
6. Install the newly-created packages:

I hope this helps,

---

### Post by the real omni on 2008-09-23
ROFL ROFL ROFL

Holy cow.

Ok well the post that I referenced did in fact have the solution, just not phrased well enough to describe the fix properly.

To anyone else who wants to make Evolution just pop up the alert dialog with the snooze button directly instead of a tray alert, here's the fix:

1) ALT+F2 for a run dialog, and type 'gconf-editor'

2) navigate to apps/evolution/calendar/notify

3) de-select the 'notify_with_tray' entry.

That's it! Don't re-select notify_with_tray, just leave it deselected. That will tell Evolution to just bypass the tray notification and throw the alert dialog at you right away! :)

---

### Post by nc_jed on 2009-07-27
I wanted to say thanks.  This thread is > 1 year old and still providing assistance.  Cannot say thanks in the original thread because it is > 2 years old, but you get an A for the assist.

- Jed

---

### Post by Noo 2 Ubuntoo on 2009-08-20
I wanted to echo nc_ jed's thanks - yep I had exactly the same problem and what an easy fix it is, once you find out how! The thread is old butstill providing valuable help.

---

### Post by ricojonah on 2009-09-11
> **nc_jed said:**
> I wanted to say thanks.  This thread is > 1 year old and still providing assistance.  Cannot say thanks in the original thread because it is > 2 years old, but you get an A for the assist.

- Jed

Ditto. This was the single, most-annoying issue that I've had with Evolution for a while now. Evolution has been my mail/task/cal client of choice for a while now; thanks to this, I'll be using it for a while longer!

Thanks!:D

---

### Post by ddvanrooy on 2010-06-23
Yes I agree. I 've been looking for a fix like this for a long time. Great stuff. Thanks !

---

### Post by gnaag on 2010-11-14
Thaks. There shoul be a place to store such tips centrally on the web.

---

### Post by Andrew_P on 2012-03-29
> **the real omni said:**
> ... to make Evolution just pop up the alert dialog with the snooze button directly instead of a tray alert, here's the fix:

1) ALT+F2 for a run dialog, and type 'gconf-editor'

2) navigate to apps/evolution/calendar/notify

3) de-select the 'notify_with_tray' entry.

That's it! Don't re-select notify_with_tray, just leave it deselected. That will tell Evolution to just bypass the tray notification and throw the alert dialog at you right away! :)

Another way in Evolution 2.28.3 (for Ubuntu 10.04 Lucid Lynx) is to go into Edit > Preferences > Calendar and Tasks > Alarms and un-check the "Display alarms in notification area only" box.  This causes a persistent window to pop up in addition to the 5-second fade-away notifier on the screen.  From there you can dismiss it manually by clicking on one of the buttons in the window.

---

