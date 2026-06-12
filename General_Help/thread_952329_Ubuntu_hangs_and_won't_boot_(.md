---
title: "Ubuntu hangs and won't boot :("
date: 2008-10-19
forum: General Help
---

### Post by sdibias on 2008-10-19
Hello my friends as you can see I'm new to the forums, unfortunatley as you can also see by the title of this thread, not on best terms.

To make a long story short I'm running Ubuntu 8.04 on a Dell Latitide D610 and it's been running perfectly for the last few months. I'm not sure what happened today however I can no longer boot into Ubuntu :(

Basically when I power up my machine I see the Ubuntu splash screen, but once that goes away there is only a blinking cursor in the top left corner of the black screen. I let it sit for 15 minutes and still nothing.

I just rebooted into recovery mode and attempted to start Xwindows using the "startx" command but to no avail, running sudo fdisk /dev/sda (p) showed my paritions so I booted to the LiveCD and I can see all of my data.

Does anyone have any ideas on how I can repair Ubuntu? I would hate to have to reinstall if at all possible. Any help you can provide it much appreciated

---

### Post by Ryadt on 2008-10-19
Try ```
xfix
```

---

### Post by Yellow Pasque on 2008-10-19
If X is not starting, we need to examine the /var/log/Xorg.0.log file for the cause and then go from there...

---

### Post by qwerty98311 on 2008-10-19
i am having the same problem as of about two hours ago.
i can log into into kdm and icewm using my login,and i can login under my sons account (which i just set up earlier today)with gnome and it works fine,but if i try to login with gnome using my account, i get the log in screen,after i log in, my desktop appears for a second and then i get kicked back to the login screen....if anyone knows what do do speak up! im a linux neewbie and i have no clue what to try next

---

### Post by sdibias on 2008-10-19
qwerty98311 our problems are a little different since I never even get to a login screen. If I were you I would start a new thread detailing your issue, the people here are more than willing to help!

Ryadt - I ran xfix from within the Recovery Menu and received the following error

```

cp: cannot create regular file '/etc/X11/xorg.conf.20081019082522' Read-only file system

```

Temüjin - At this point I dropped to a root shell prompt and examined the Xorg log using 

```

vi /var/log/Xorg.0.log

```

I'm not really sure what I'm looking for in this log file but here are a few that jumped out at me.

```

[COLOR="Blue"](WW) fglrx(0): could not detect X server version (query_status=-3[/COLOR]

[COLOR="Blue"](WW0 AIGLX: 3 driver claims to not support visual (Hex code)[/COLOR]

[COLOR="Blue"]Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated. Please convert your driver/module to use dixLookupDrawable().[/COLOR]

(II) XAA: Evicting pixmaps
(II) fglrx(0): Shutdown CMMQS
(EE) fglrx(0): [drm] failed to remove DRM signal handler
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes SAREA (hex) (hex)
(II) fglrx(0): [drm] Closed DRM master.

```

Does any of that mean anything relevant to my situation? Anything else I should be looking for or can try?

---

### Post by sdibias on 2008-10-19
I need to get this thing running before tomorrow morning since I'm supposed to be doing a presentation from this laptop in the morning. I have th ability to backup my data and reinstall but I was really looking forward to figuring out what went wrong and why. If anyone has any other ideas I will give them a try.

Anyone?

---

### Post by oilchangeguy on 2008-10-19
> **sdibias said:**
> Hello my friends as you can see I'm new to the forums, unfortunatley as you can also see by the title of this thread, not on best terms.

To make a long story short I'm running Ubuntu 8.04 on a Dell Latitide D610 and it's been running perfectly for the last few months. I'm not sure what happened today however I can no longer boot into Ubuntu :(

Basically when I power up my machine I see the Ubuntu splash screen, but once that goes away there is only a blinking cursor in the top left corner of the black screen. I let it sit for 15 minutes and still nothing.

I just rebooted into recovery mode and attempted to start Xwindows using the "startx" command but to no avail, running sudo fdisk /dev/sda (p) showed my paritions so I booted to the LiveCD and I can see all of my data.

Does anyone have any ideas on how I can repair Ubuntu? I would hate to have to reinstall if at all possible. Any help you can provide it much appreciated

what did you do to the computer prior to this problem? i see you have another thread about an open office problem.

---

### Post by sdibias on 2008-10-19
That's not my thread I just replied to someone elses.

Yesterday I installed Virtual Box so that I could install XP into a VM, however after trying to run the install I noticed my CDROM drive wouldn't automatically mount. I attempted to mount it manually 

```

sudo mount /media/cdrom0

```

This gave me errors so I tried mounting it using the GUI and neither would work. After ejecting the CD multiple times Ubuntu mounted the drive and I attempted to install XP as a VM, but I kept getting read errors on the disk. 

At this point I was sure that the CDROM drive was having issues reading media but somewhere in the process of troubleshooting I must have modified something that killed my Ubuntu.

Is there anyway to reset GNOME and get X running again?

---

