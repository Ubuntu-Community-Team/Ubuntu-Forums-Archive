---
title: "Hibernates when unplugged - HELP!"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by the_maassk on 2006-06-06
This morning when I unplugged my laptop from mains, it automatically went into hibernation. This was not there till last night. Here is what I did last:

Because 'laptop_mode' was always showing up as disabled, I followed the advice on a thread on the forums to do a 

*sudo touch /var/run/laptop-mode-enable*

Laptop_mode showed up as 'enabled' after that. But this morning I realized that the 'hibernate' problem came in. I tried looking back for the file and it is not there any more. I disabled laptop_mode, but the problem persists. I tried to reconfigure laptop-mode-tools, but nothing came of it. I was planning to remove and reinstall the package, but it asks me to remove a lot of other packages including ubuntu-desktop!

Help !!! ](*,)

---

### Post by Patsoe on 2006-06-06
I can't specifically help, but if you want to reconfigure a package to its defaults, you don't have to uninstall it: type "sudo dpkg-reconfigure <package-name>" in a terminal and you should be fine.

Before you go ahead, you might want to read more about all the options of the dpkg-reconfigure command - I'd suggest to do that first. There's a lot of power in the dpkg commands.

Great stuff isn't it? :)

---

### Post by the_maassk on 2006-06-06
Thanks ...but I already tried 'reconfigure'. But because it didn't work, I thought I'd remove and install the package again.

Any other ideas ?? (I'm going to hit the road soon and can't afford to let this issue bog me down :( )

---

### Post by Patsoe on 2006-06-06
Hmmm sorry, no. 

I think unplugging the AC cord is an ACPI event, which triggers a script. Hibernating is also handled by an ACPI script - maybe something got messed up there (but that would have involved you messing it up I suppose :-k ). If you want to look through the acpi event things, they're at /etc/acpi.

---

### Post by thegnu on 2006-06-06
I concur that it's an ACPI event.  What does dmesg tell you happened right after you come back from hibernation mode?

figure out which of these is the actions you need to edit, because it's one of these scripts, each of which in turn runs scripts located in /etc/acpi/:
```
thegnu@mux:~$ ls /etc/acpi/events/
ac                     ibm-sleepbtn               sony-volume-down
asus-a6u-touchpad      ibm-videobtn               sony-volume-up
asus-internet          ibm-wireless               tosh-battery
asus-lock              lenovo-lockbtn             tosh-brightness-down
asus-mail              lenovo-touchpad            tosh-brightness-up
asus-media-eject       lidbtn                     tosh-hibernate
asus-media-next        panasonic-brightness-down  tosh-ibutton
asus-media-play-pause  panasonic-brightness-up    tosh-lock
asus-media-prev        panasonic-hibernatebtn     tosh-mail
asus-media-stop        panasonic-lockbtn          tosh-media
asus-touchpad          panasonic-sleepbtn         tosh-mute
asus-volume-down       powerbtn                   tosh-next
asus-volume-mute       sleepbtn                   tosh-play
asus-volume-up         sony-brightness-down       tosh-prev
asus-wireless          sony-brightness-up         tosh-sleep
battery                sony-hibernate             tosh-stop
ibm-hibernatebtn       sony-mute                  tosh-wireless
ibm-lockbtn            sony-sleep                 tosh-www

```

The info I got to come to this conclusion is here [http://members.westnet.com.au/rbirdman/acpi.html](http://members.westnet.com.au/rbirdman/acpi.html)

---

### Post by the_maassk on 2006-06-07
As suggested, I looked through the scripts. My 'battery' event calls 'power.sh' script. Went through it, but did not notice anything funny that would trigger a hibernation. Can you post your power.sh so that I can compare against it?

On another note - I also upgraded the laptop-mode-tools package using the one from the original package developer. It rewrote laptop.conf file but again, going through it, I did not find anything interesting to help me sort this out.

Another thing I noticed - If I boot up on battery and then plug in the mains - the display dims as it would, when you switch from mains to battery! Funny behaviour - looks like the 'ac' and 'battery' events are being interchangably detected.

---

### Post by the_maassk on 2006-06-08
I had to bump this in case anyone who can help, missed it!

---

### Post by Patsoe on 2006-06-08
The display dimming thing happens here too, and both in Ubuntu and WinXP. I think it just sets your backlight to whichever setting it had when you were on batteries for the last time. It's not a bug, it's a feature :)

I've attached my power.sh which should be completely default (though I changed the extension so the forum accepts it). Hope it helps.

---

### Post by the_maassk on 2006-06-09
I think you missed reading the line - the dimming happens the 'other way round' - it dims when I plug in the mains. I understand the dimming (and it was normal) when I was switching to battery...but this is the reverse of what was happening (as if the power state is being toggle-read).

Anyways...I compared the power.sh and there is no difference. I am thinking of removing and reinstall all acpi and laptop-mode packages (drastic...I know ...but do not seem to have a solution!)

Wish me luck!

---

### Post by Patsoe on 2006-06-09
[QUOTE=the_maassk]I think you missed reading the line - the dimming happens the 'other way round' [/QUOTE]

Nope, I didn't miss that :) The thing is, when I have been using my laptop on the mains in the evening, so the screen was dim, and then do some work on battery power in the morning, with the screen bright, and then plug back into the mains, I get exactly that: the screen dims to the setting it was at in the evening.

> Wish me luck!
Good luck! :)

---

### Post by togume on 2006-06-12
I have a hp DV1000, same as the Compaq, and it seems to be doing the same. It's replicable; every time the laptop is running on AC and it's disconnected it hibernates automatically... Quite weird...

---

### Post by Patsoe on 2006-06-12
I'm thinking that maybe the acpi-system is just detecting the wrong event? So it's not wrong in the scripts, it's just that the kernel receives the wrong signal when you pull the AC plug...?

You can look in the file /var/log/acpid to see what event is being received when you do the unplugging (look at the date+time when you unplug, then after restarting you can scroll through the file - every event is time labeled to the second).

---

### Post by togume on 2006-06-23
Good idea Patsoe. Have not done that yet, but I did find a workaround. 

The way it was responding led me to believe that it was thinking that it had no more battery power and thus hibernated. I went to the Power Management setting and under battery told it to do "nothing" when the battery power was critical. Off course, the problem is that now all work will be lost when it goes down, hard...

For now this works... More digging is necessary to actually fix this problem.

Tomás

---

### Post by the_maassk on 2006-07-05
I did try what togume suggested. Sadly, it does not work for me. I diasbled all 'power management' like features from the power-manager. But the condition persists :(

---

### Post by johnzilla on 2006-07-12
I have an HP dv1000, I recently started experiencing this problem and narrowed it down to the power management setting for the laptop lid.

When set to suspend when the lid was closed, my laptop would suspend when the power was unplugged.  When set to do nothing when the lid was closed, the problem ceased.

Of course, now I have to use the sleep key before I close the lid, but atleast it's less annoying than having to wake from a suspended state when I move.

If anyone's interested, this is what was logged in /var/log/acpid on a power-disconnect:

```
[Wed Jul 12 21:24:59 2006] received event "button/power PWRF 00000080 00000001"
[Wed Jul 12 21:24:59 2006] notifying client 4452[108:108]
[Wed Jul 12 21:24:59 2006] executing action "/etc/acpi/powerbtn.sh"
[Wed Jul 12 21:24:59 2006] BEGIN HANDLER MESSAGES
[Wed Jul 12 21:24:59 2006] END HANDLER MESSAGES
[Wed Jul 12 21:24:59 2006] action exited with status 0
[Wed Jul 12 21:24:59 2006] completed event "button/power PWRF 00000080 00000001"
[Wed Jul 12 21:25:01 2006] received event "battery BAT0 00000080 00000001"
[Wed Jul 12 21:25:01 2006] notifying client 4452[108:108]
[Wed Jul 12 21:25:01 2006] executing action "/etc/acpi/power.sh"
[Wed Jul 12 21:25:01 2006] BEGIN HANDLER MESSAGES
[Wed Jul 12 21:25:01 2006] END HANDLER MESSAGES
[Wed Jul 12 21:25:01 2006] action exited with status 0
[Wed Jul 12 21:25:01 2006] completed event "battery BAT0 00000080 00000001"
```

/etc/acpi/power.sh is the script that handles AC power disconnects, as you mentionned.  I'm going to play around with this a bit and see what happens. Let you know how it turns out. :-k 

- John

---

### Post by Akita on 2006-07-12
FWIW, disabling the lid close event fixes it here too.

---

### Post by johnzilla on 2006-07-12
Okay, so here's the fix for me, ymmv... Using your text edit of choice, edit the file /etc/default/acpi-support. (of course you'll need to use sudo, otherwise you won't have access)

right at the very bottom is the line:

```
ENABLE_LAPTOP_MODE=false
```

change this to:

```
ENABLE_LAPTOP_MODE=true
```

As you'll read, there is a comment in the acpi-support file that says setting ENABLE_LAPTOP_MODE=true may cause some systems to crash, so this likely won't work for everyone.  I imagine this is a bug that will be ironed out in a future version.

-John

---

