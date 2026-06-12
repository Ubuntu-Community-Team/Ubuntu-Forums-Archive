---
title: "Install problems"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Fireman1224 on 2009-04-24
Installation hangs and cmd line comes up with:

INFO: task hid2hci:1018 blocked for more than 120 seconds.
"echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.

I keep getting this with LiveCD, Install, and Upgrade.

Please Help!!!

---

### Post by antikristian on 2009-04-24
It looks like the hid2hci module is preventing the upgrade. Do you have a bluetooth mouse or keyboard? Or a bluetooth dongle?

---

### Post by BucketOfZen on 2009-04-26
I have the same issue, except it says "hid2hci:4051" rather than 1018.

I do not have any bluetooth adapters/dongles, etc.

Is there any way to disable this module at the beginning?

---

### Post by antikristian on 2009-04-26
My mistake, it's not a module, but a program that sets bluetooth modules into hid mode for keyboards and mice.

Do a ```
ps -A | grep hid2hci
``` To see if the program is running.

---

### Post by tdmoore on 2009-04-26
I too have the same issue.

antikristian: the code above, can you clarify please?  Is that an "L" lower case after the A?

Not really sure what I should look for so appreciate the help.

---

### Post by antikristian on 2009-04-26
It's a pipe. on my keyboard (norwegian) it's located next to the numbers row at the top. It pipes the output of the ps -A command to the grep hid2hci command that selects lines (if there are any available) that match.

You can also just run ls -A but then you would have to sort through it manually to find hid2hci.

---

### Post by tdmoore on 2009-04-26
Thanks...I have absolutely no idea honestly what you are talking about.

Running dual boot with Win XP, I was able to boot into 9.04 using the lower option in the boot menu.

One of my printers is no longer able to work, and I am working on that little nuisance, however I hope to get into full boot mode on the next try.

Appreciate the reply...take care and all the best.

---

### Post by BucketOfZen on 2009-04-27
I decided to do a clean install of 8.10 (ended up doing an install of 8.04 instead, whoops) so I'm currently on the second upgrade of the night, hopefully I'll have 9.04 running smoothly shortly.

It's just a shame it didn't work straight away.

---

### Post by antikristian on 2009-04-28
Typo: I meant ```
ps -A
```

My point was, you can run ps -A (which shows all running programs) and use an operator to redirect the output: If I run ps -A I get a long list containing stuff like:```
....
 3128 ?        00:00:00 wpa_supplicant
 3130 ?        00:00:00 nm-system-setti
 3134 ?        00:00:00 avahi-daemon
 3135 ?        00:00:00 avahi-daemon
 3162 ?        00:00:00 cupsd
 3190 ?        00:00:00 system-tools-ba
 3265 ?        00:00:00 atd
 3294 ?        00:00:00 cron
 3466 tty1     00:00:00 getty
...
```

Bash (the shell) has a set of built in commands and operators, pipe (|) is an operator and looks like two lines on top of each other on the keyboard, and looks like a slighter larger l on your screen. You can see the difference here: l|I (small L, pipe and capitol i)

Grep is a filter that filters out a line which matches the search term, so the command ```
ps -A | grep cron
``` will produce output this way:

```
 3294 ?        00:00:00 cron

```

Just thought I'd try to clarify what I meant;-)

---

### Post by quickgold192 on 2009-06-18
In case you hadn't solved it yet, I had the same issue and solved (avoided) it:
I had a Logitech USB wireless mouse/keyboard plugged in when I was having the problem, so I unplugged it and rebooted (this was the first boot after a fresh install from a LiveDVD). This time it booted just fine. Now the problem has gone away, even if I boot with USB devces plugged in.

---

### Post by tdmoore on 2009-06-25
quickgold 192,

Interesting and something I will try.

I have NO WIRELESS devices other than for internet, keyboard and mouse are USB running through a 8 port USB hub.
Maybe....maybe disconnecting this as you have done will assist here.

I can run Ubuntu through the 2.27 kernel but the not top choice in GRUB (2.28??).

Worth a try anyway to see what happens.

Thanks for the tip.

To: antikristian - sorry, not a techie guy so the output you have above is too far above my head.  Appreciate the help though.

---

