---
title: "power management settings ignored"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by 1jackjack on 2007-11-24
Hi all. Im using an Acer Aspire 3020 Laptop (ATI x700 graphics card), running Ubuntu 7.10. All I want is for my screen to turn off after 10 mins idle time, but whatever settings i use in Power Management are ignored! Any ideas would be greatly appreciated!

Thanks,
Jack

p.s. in screensaver preferences, i have 'regard computer as idle after' set to 1min (lowest setting)
but have unchecked 'activate screensaver when computer is idle', as i want the monitor off...

in power management settings>ac power, i have 'put display to sleep' set to 2mins (lowest setting), but nothing ever happens...

---

### Post by Linicks on 2007-11-24
I had similar issues with my Inspiron 6400 - the backlight never turned off.

As a test, run:

xset 10 20 30

That should standby after 10 seconds, suspend after 20 seconds, and OFF after 30 seconds.

To reset back:

xset 0 0 0 

I solved my issue as I now use fluxbox, and installed xlock.

Nick

---

### Post by 1jackjack on 2007-11-25
If i try xset 10 20 30 i get:
xset:  unknown option 10

usage:  xset [-display host:dpy] option ...
then all the options you can add...

any other ideas? maybe there is an alternative to the power management program?
thanks

---

### Post by Linicks on 2007-11-25
Sorry... bum steer from me :(

xset dpms 10 20 30

Nick

---

### Post by 1jackjack on 2007-11-25
'xset dpms 10 20 30' gives no output, and doesnt do anything after 10 seconds...

was trying other combinations, and thought this might be relevant:
'xset dpms force off' gives output:
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  146 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  

I guess this means it doesnt know how to turn off my screen?!
I read in another thread that sometimes it helps to run this command:
'export DISPLAY=:0' and if I do that, then do 'xset dpms force off', my monitor turns off!

Im lost... any ideas whats happening/what to do?
Thanks a lot

---

### Post by Linicks on 2007-11-25
> **1jackjack said:**
>  

I guess this means it doesnt know how to turn off my screen?!
I read in another thread that sometimes it helps to run this command:
'export DISPLAY=:0' and if I do that, then do 'xset dpms force off', my monitor turns off!

Im lost... any ideas whats happening/what to do?
Thanks a lot

Ummm, yes, this is the issue, I think.  It looks like your DISPLAY is not exported.  This should be done at startx

From a fresh restart of X, issue the output of:

export | grep -i display

Example - here is mine:

```
nick@palantir:~$ export | grep -i display
declare -x DISPLAY=":0.0"
```

Nick

---

### Post by 1jackjack on 2007-11-25
jack@pato:~$ export | grep -i display
declare -x DISPLAY=":1.0"

I think I need to change something... hehe
should I add that 'export DISPLAY=:0' command somewhere, so it runs at login?

Thanks

---

### Post by Linicks on 2007-11-25
Well, I don't know where Ubuntu exports that in the first place, so we need somebody who knows that.

Secondly it could be another app running AFTER export DISPLAY=:0.0 changing it to :1.0

I don't know.

A quick fix could be to run the export command from rc.local

Nick

---

### Post by 1jackjack on 2007-11-25
Thanks for your help. Do you mean the rc.local in /etc/ or in /etc/init.d/ ??
I tried adding the line to both, then restarting, and still i get that error when i run 'xset dpms force off'

any other ideas?
thanks

---

### Post by Linicks on 2007-11-25
```
jack@pato:~$ export | grep -i display
 declare -x DISPLAY=":1.0"
```

I don't know.  We need to find why the above is set and where from.

If you set DISPLAY=:0.0 and then try normal power settings, do they work then?

Nick

---

### Post by 1jackjack on 2007-11-26
No, they don't sadly. I feel like it's localised to the terminal where I set it, as only in that terminal will 'xset dpms force off' work...

Thanks for your time anyway...
:(

---

### Post by 1jackjack on 2007-11-27
> [QUOTE]jack@pato:~$ export | grep -i display
declare -x DISPLAY=":1.0"

I don't know. We need to find why the above is set and where from.[/QUOTE]

Still no solution to this problem...
Anyone know anything about this?

Thanks

---

### Post by puikku on 2007-12-08
Hi,

I have similiar problems on IBM X40. Neither display nor laptop doesn't go to sleep by timers. Screensaver works. I've tried to change the idle timer from screesaver settings ranging in few minutes but it doesnt have any effect. Also power management timers don't seen to have any efect. After an hour an battery power it was still happily running when it should have went to sleep after 10 minutes... Very irritating problems.

I've been thinking of installing previous ubuntu as at least some basic stuff appears to work better on it on my laptop.

---

