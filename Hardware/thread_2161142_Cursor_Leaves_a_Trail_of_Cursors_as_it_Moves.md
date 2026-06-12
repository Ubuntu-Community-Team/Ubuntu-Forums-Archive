---
title: "Cursor Leaves a Trail of Cursors as it Moves"
date: 2013-07-09
forum: Hardware
---

### Post by maglax on 2013-07-09
I am not 100% sure this belongs in hardware as this may not be a hardware problem. If it doesn't notify and move this thread.

I just Finished doing an install of an older computer and the only problem I am having this run through is that the mouse leaves a trail of cursors as it moves. It only occasionally refreshes.

Note: Had to do the alternative install, with the other on I kept receiving ubi-partman failed returned error code 10.

Specs:
     Hard Drive: 640gb (split between two drives 320 each)
     CPU: Pentium 4 (I think its an earlier one)
     RAM: ~1gb
     Graphics card: __________________ (I believe the part number is g7700.2 and its a gateway computer)

Note: It was just recently upgraded from 20gb hdd and .5gb ram.

---

### Post by TNFrank on 2013-07-09
You probably need to go in and reset your mouse settings.  You can set it up to leave a trail, you just need to uncheck the box so it won't leave a trail.

---

### Post by maglax on 2013-07-09
I'm not sure that is the problem but I will try it. Thank you. (:

---

### Post by maglax on 2013-07-09
Well I know the trail your talking about and this does not seem like it since the trail only disappears when the screen around refreshes. So maybe it is a cursor refresh error. How would one fix that?

---

### Post by TNFrank on 2013-07-10
If the trail is persistent then it's something else all together. The setting just leaves a short trail that disappears so it's probably something other then settings.

---

### Post by maglax on 2013-07-10
Yeah that is what I thought. Which brings me back to this post.

"[COLOR=#000000]So maybe it is a cursor refresh error. How would one fix that?"

[/COLOR]I hope I do not need a new graphics card as well.[COLOR=#000000][/COLOR]

---

### Post by Yellow Pasque on 2013-07-10
Post the /var/log/Xorg.0.log (use [ code ][ /code ] tags)

---

### Post by maglax on 2013-07-10
I would post the log file here except even on my fastest computer (my home built (: ) it will not upload. So i decided to use pastbin. Here is the [link]("http://pastebin.com/rzaCuVMD").


Text link: [http://pastebin.com/rzaCuVMD](http://pastebin.com/rzaCuVMD)

---

### Post by TNFrank on 2013-07-10
Maybe not so much a new graphics card but a new driver for it might not hurt. I'd look up any driver updates that you can find for it and install them, maybe that'll help.

---

### Post by maglax on 2013-07-10
Okay then thank you. I will be back if it does not but I think it should. :)

---

### Post by Yellow Pasque on 2013-07-10
So you're using a TNT2 (nvidia nv05) and the open-source nouveau driver. I didn't see any matching bugs: [https://bugs.freedesktop.org/buglist.cgi?short_desc=cursor&query_format=advanced&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=RESOLVED&bug_status=VERIFIED&bug_status=CLOSED&bug_status=NEEDINFO&bug_status=PLEASETEST&short_desc_type=allwordssubstr&component=Driver%2Fnouveau&product=xorg](https://bugs.freedesktop.org/buglist.cgi?short_desc=cursor&query_format=advanced&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=RESOLVED&bug_status=VERIFIED&bug_status=CLOSED&bug_status=NEEDINFO&bug_status=PLEASETEST&short_desc_type=allwordssubstr&component=Driver%2Fnouveau&product=xorg)

I would try to turn off cursor acceleration. Make an /etc/X11/xorg.conf with the following contents:
```
Section "Device"
        Identifier "Configured Video Device"
        Option "HWCursor" "false"
EndSection

Section "Monitor"
        Identifier "Configured Monitor"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Monitor "Configured Monitor"
        Device "Configured Video Device"
EndSection
#trailing line
```

Log out after you make it to restart X.

---

### Post by maglax on 2013-07-12
Okay thank you Temujin. I will try that as well and post if that does not work.
As an note of the driver update: Gateway no longer supports my computer (my computer has a 10 digit serial number Gateway now asks for 11 -____-)

---

### Post by maglax on 2013-07-12
After Attempting that code it cause my Xserver to crash. -___- I suspect that is not good. Could I have typed something wrong?
I am going go to recovery from my install disk to reset it.

---

### Post by maglax on 2013-07-12
Interesting, interesting, interesting! After a reinstall it worked! 
Note: changes written to disks were the os and swap space.
Note: one drive contains root the other contains /home.
[SIZE=7]Thank you Temujin and also TNFrank for all your help!
[/SIZE][SIZE=2]Marking as  Solved![/SIZE]

---

### Post by maglax on 2013-07-13
Update: I now know what cause it to do this. It was the software update. Is there a patch I can use to fix this?

---

### Post by Yellow Pasque on 2013-07-13
> It was the software update.
Which one? Kernel update?

---

### Post by maglax on 2013-07-13
security updates: a few Linux kernel items                          Lubuntu base
Other updates:    software and updates 
                          software updater
                          synaptic package manager
                          lubuntu base           

Ask me if you need to know which kernel items or packages contained in one of those. I did not list everything under those packages because of the amount of items.

---

### Post by Yellow Pasque on 2013-07-13
I'm not really sure what to tell you then. If you could figure out which update does it, that would help. The first thing I would try is booting the old kernel. If it's still doing it, file a bug against xserver-xorg-video-nouveau

---

### Post by maglax on 2013-07-13
ok I will install the kernel updates one by one

---

### Post by maglax on 2013-07-13
Okay all the kernel updates have been installed (none of which yielding problems) and I'm looking at the X ones are there any keywords I should look for?

---

