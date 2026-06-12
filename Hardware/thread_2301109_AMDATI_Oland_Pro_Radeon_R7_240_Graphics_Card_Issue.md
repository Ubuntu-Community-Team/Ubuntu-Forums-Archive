---
title: "AMD/ATI Oland Pro Radeon R7 240 Graphics Card Issues"
date: 2015-10-30
forum: Hardware
---

### Post by kyrachris on 2015-10-30
I recently installed a new graphics card and it worked fine for a while. I lost access to the virtual consoles using CTRL+ALT+F1..F6 when switching to the proprietary drivers. I would really like to get access to that again. I tried editing a few GRUB values regarding the terminal, but none of those brought the consoles back. I know that the consoles are running because I've  blindly logged in and run commands (e.g., "touch imhere" and the file shows up).

I've been playing a few steam games, and they seem to be working just fine. (Mark of the Ninja, FTL, Kairo, Brutal Legend, to name a few.)

I'm also experiencing issues with Firefox and YouTube. The videos freeze and I'm unable to stop them from playing for several seconds. This is using HTML5. It works fine on Chrome, except when hardware acceleration is <disabled>. I've tried toggling several about:config values in Firefox, and even tried safe mode, but it's all the same.

And now today I'm having huge lag issues, even while I type this post. I can write entire sentences before the monitor displays what's been written. Steam games are laggy today too.

FWIW, I got a score of 15 using glmark2. I'm going to try the free driver to see if it helps, but I doubt I'll be able to use Steam.

---

### Post by kyrachris on 2015-10-30
I tried the free driver and got a score of 54 on glmark2. Not great, but better.

I also saw that AMD released a new driver about a month ago.

[http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64](http://support.amd.com/en-us/download/desktop?os=Ubuntu+x86+64)

Maybe I should try that.

---

### Post by QIII on 2015-10-30
Which release of Ubuntu are you using?

---

### Post by kyrachris on 2015-10-30
Ubuntu 15.04, but now that you mention it, I see there's a new release available. I only noticed it when I logged in via SSH from another computer. (Why isn't there a notification system for updates like this??)

Perhaps that will help clear up the issues I've been having?

---

### Post by QIII on 2015-10-30
There is a notification system, but you may not have it set.

No.  Upgrading to 15.10 would be a bad idea at this point because there is a bug in the fglrx installer.

I'm on my cell phone right now, so can't answer in detail.  Your performance with fglrx should be much better than that.

---

### Post by kyrachris on 2015-10-30
BTW, I'm using Gnome, so I'm not sure if the bug affects it.

---

### Post by QIII on 2015-10-30
The DE has nothing to do with the bug.

---

### Post by kyrachris on 2015-11-01
Well, I upgraded before I got the note about the bug, so I immediately reverted to the open source drivers once the upgrade completed. I read the bug and tried the wily-proposed update, and it worked just fine.

However, I still have all the same problems with YouTube and the graphics results being very poor. The card is new to the machine, and it appeared that everything installed right when I first got it (except for losing the consoles). Other than that, I haven't really done anything with the AMD CCC other than look at specifications. 

Any help getting the consoles back and improving the graphical results would be greatly appreciated.

---

### Post by kyrachris on 2015-11-10
I decided to do a few tests. First, I thought perhaps Gnome was somehow eating up GPU resources, so I tried Gnome Classic. Then I tried various states of the browsers I've been using. Here are the results:

glmark2 Scores
Gnome Classic: 1400
Gnome (normal): 1378
Gnome with Firefox (Gmail, Google Calendar, Old Reader): 37
Gnome with Gedit and Keepass2: 1400
Gnome with Chrome (YouTube frontpage): 1324
Gnome with Chrome (Gmail, Google Calendar, Old Reader): 31

So now I'm a bit astonished. This problem has changed from "Why is my graphics card out of whack?" to "Why the heck are my browsers killing my GPU performance?"

Although I'd still like to get my virtual consoles (CTRL + ALT + F1...F6) back. I've tried adding GRUB_TERMINAL=console and GRUB_GFXMODE=640x480 in /etc/default/grub to no effect. Any suggestions on that issue would be appreciated.

---

