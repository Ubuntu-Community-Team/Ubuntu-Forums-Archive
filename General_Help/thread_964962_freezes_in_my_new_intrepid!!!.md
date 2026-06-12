---
title: "freezes in my new intrepid!!!"
date: 2008-10-31
forum: General Help
---

### Post by kboy on 2008-10-31
Hi, 
i've installed today the new intrepid ubuntu, since then I've experienced 4 freezes all caused by the same factor (or so it seems), all of them required hard boots.

here is the message from the system log from the last freeze:
```

Oct 31 13:41:11 my-ubunutu pulseaudio[615]: main.c sterlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted

Oct 31 13:41:11 my-ubunutu pulseaudio[615]: main.c sterlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

```

all of the other freezes had the same entry. it seems that the cause of the freezes is pulse audio, so i've removed pulse audio, but the freezes still continue with the same message.

what else can i do????
if I may add, I've experienced freezes with ubuntu hardy and gusty but the reason was my graphics card not the audio engine.

thanks

---

### Post by kboy on 2008-10-31
anyone???

---

### Post by bgilbert on 2008-10-31
I have the exact same problem. Intrepid keeps locking up after about 10-15 inutes, and I have to perform a hard restart. After looking at my system logs, I notice the exact same error that you seem to be getting as well involving pulse audio.

However, I do not think this is what is causing the problem, mine at least. Looking at my logs, the last thing that I see under syslog before the freeze is this:

```
Oct 31 09:47:38 bgilbert-laptop NetworkManager: <WARN> nm_device_wifi_set_ssid(): error setting SSID to '(null)' for device wlan2: Invalid argument
```

After completely disabling networking, I have been running ubuntu for about 40 min. so far (Longest since I updated), so unless this is a fluke it appears the Network Manager is the culprit. The only problem is I kinda need that thing, anyone have any suggestions?

Thanks in advance

---

### Post by cryptecks on 2008-10-31
I'm having the exact same problem, I hit the switch on my laptop to turn off wifi (and thereby disable networking), and I've been up twice as long as before.

---

### Post by carpex on 2008-10-31
Probably related to this
[http://ubuntuforums.org/showthread.php?t=832383&page=17](http://ubuntuforums.org/showthread.php?t=832383&page=17)

and this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/291044)

---

### Post by cryptecks on 2008-10-31
I would think that this is the exact same issue, as all the symptoms make sense.

---

### Post by bgilbert on 2008-10-31
Yea, I think so too. I also noticed that my caps lock light flashes on and off while its locked up....pretty odd.

---

### Post by kboy on 2008-11-03
I DON'T KNOW WHAT TO DO!!!
the freezes continue, is there no solution?!?!?
in the begining of this thread i said that when it freezes there is a message about the pulse audio failure in system log. but now there are no messages and the freezes continue.
Is there some kind of diagnostic I can do to isolate the problem????

I'm really getting tired from this Ubuntu freezes, and I'm afraid that all these hard boots will damage my hardware.

---

### Post by jordilin on 2008-11-03
There is a new kernel update in the update manager. I had a freeze the second day of installing Intrepid, apparently with this same audio problem. After upgrading kernel I haven't had anymore problems.

---

### Post by kboy on 2008-11-03
> **jordilin said:**
> There is a new kernel update in the update manager. I had a freeze the second day of installing Intrepid, apparently with this same audio problem. After upgrading kernel I haven't had anymore problems.

My current kernel version is 2.6.27-7-generic. is there something better???
From what i know i've updated the kernel right after the install, together with all of the other updates.

---

### Post by jordilin on 2008-11-03
> **kboy said:**
> My current kernel version is 2.6.27-7-generic. is there something better???
From what i know i've updated the kernel right after the install, together with all of the other updates.

don't know, but I have the same version of kernel, but I have a kernel update, maybe some patch or fix. Go to System-Administration-Update Manager and check.

---

### Post by kboy on 2008-11-03
My kernel is updated....
I'll appreciate any other possible solutions.

---

### Post by carpex on 2008-11-03
I think its related to this bug

[https://bugs.launchpad.net/ubuntu/+bug/276990](https://bugs.launchpad.net/ubuntu/+bug/276990)

Its related to the wireless drivers in the kernel that ships with 8.10. Upgrading the kernel (with the backports) probably fixes it.

---

### Post by crunchyblack on 2008-11-05
Carpex, while trying that fix you posted I noticed something really odd.  While trying to type out the commands needed for the fix, every time I pressed "tab" my computer went into one of these lockups...  I tried 6 times in a row, as soon as I pressed tab, it froze.  I finally applied the fix, pressed tab and sure enough, it froze. No idea what's going on here.

---

### Post by kboy on 2008-11-05
I guess everyone here has a different reason for the freezes...

it seems that my freezes started from the pulse audio problem but when I uninstalled it, the problem continued from a different reason.
this the entry in syslog from the first freeze today, 8 more freezes with the same entry occured in the last 3 hours...

```

Nov  5 10:28:15 my-ubuntu gnome-session[5666]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager' 

Nov  5 10:28:26 my-ubuntu gnome-session[5666]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout 

Nov  5 10:28:36 my-ubuntu gnome-session[5666]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 

```

I've tried to google some of the information but i couldn't find anything helpful.
I hope someone here will help me in resolving this issue.

---

### Post by ajc4002 on 2008-11-05
I have the same (or similar?) random freezes, with pulse audio errors in the system log. Upgrading the kernel didn't help.

It occurs at apparently at random, but seems somewhat more frequent if I'm using ssh with x forwarding.

I also retain full keyboard and mouse control. I can move between applications with alt-tab and desktops with alt-control. Indeed the applications are still working: using the keyboard I can navigate to new pages in firefox, it's just all of the GUI elements which aren't responding to the mouse. Restarting x with alt-control-backspace solves the problem temporarily. Are other people's like this?

It's difficult to tell whether this is a bug in x, gnome, hal..., but it sure is annoying.

---

### Post by crunchyblack on 2008-11-05
kboy, im sorry to disappoint you, but this has been happening to me ever since hardy came out... I thought it would be fixed with intrepid, but it's not.  Back to gutsy or windows XP I guess.

---

