---
title: "LIRC devinput busted after upgrade to 17.04. Kernel issue?"
date: 2017-05-19
forum: Hardware
---

### Post by halfer2 on 2017-05-19
I have been using the same IR reciever and remote for my HTPC build since 15.10 - I achieved this using LIRC with a custom lircd.conf. 
Recently, after I upgraded to **17.04**, LIRC became unresponsive. After reading the logs and googling the issues I stumbled [upon this]("https://bugzilla.redhat.com/show_bug.cgi?id=662071").
(quoting the report here)
> I had a **Fedora 12**, on which lirc was working fine. Philips (I think) OVU4003/00 IR receiver, Harmony One remote (device type set to Plex Player), mostly used for controlling XBMC.Then I did a clean Fedora 14, restored my /etc/lirc/lircd.conf, but it doesn't work anymore. I see signals being received with mode2, but irw doesn't show anything.


Steps to Reproduce:


Start lirc, which produces in the log:
lircd-0.8.7[9819]: lircd(devinput) ready, using /var/run/lirc/lircd


Then start irw:


lircd-0.8.7[9819]: accepted new client on /var/run/lirc/lircd
lircd-0.8.7[9819]: initializing '/dev/lirc0'
lircd-0.8.7[9819]: can't get exclusive access to events coming from `/dev/lirc0' interface


Pressing buttons on the remote gives me a lot of:


lircd-0.8.7[9819]: error reading '/dev/lirc0'
lircd-0.8.7[9819]: error reading '/dev/lirc0'


Fedora is up-to-date, using lirc from the Fedora repository. As I said, it worked just fine with Fedora 12.
> An update about this bug: the error about exclusive access occurs when **LIRC_DRIVER=devinput**.When setting **LIRC_DRIVER=default**, using the same lircd.conf that I used with Fedora 12, I don't get the error anymore, but the remote **still doesn't work properly**.


A few buttons are recognized constantly by irw (e.g. LargeUp, LargeDown - see attached conf), other buttons are recognized only occasionally. Most buttons don't work though.
I don't know if this is the same issue or should be reported as a separate one.


 The issues seemed to be identical: and the "solution" provided actually yielded the same results with my setup (which is a newer LIRC build on a different OS) - the remote starts "working" but not all button presses work all the time; to be exact, it seems in my case that LIRC almost "falls asleep", so it will ignore all the button presses unless you make them around 4-5 times in succession really fast (making 1 click per 2 seconds doesn't "wake it up"). After that, all the button presses get recognized without issues.

I tried launching "irw" to check that it's not just the applications ignoring LIRC, and actually LIRC being at fault here, and it confirmed it: when the machine it in it's "glitched" state (asleep) irw doesn't report any button presses until you "wake LIRC up" with a quick succession of button presses.

Unfortunately, as far as I understand, the issue reported on that forum was eventually fixed on kernel level - and I think that leaves me basically helpless

Here are my LIRC related files, just in case
[lirc_options.conf]("https://pastebin.com/nHCrw2Pb") (the file with the LIRC_DRIVER setting that makes the remote work, but dodgily so)
[hardware.conf]("https://pastebin.com/Hu98c2sG")
[lircd.conf]("https://pastebin.com/RYZpuJqa")

Sure hope I posted in the correct forum.
Thanks in advance!

---

### Post by halfer2 on 2017-05-25
Bump

---

### Post by apos on 2017-05-28
Hi halfer2,

> lircd-0.8.7[9819]: error reading '/dev/lirc0'
lircd-0.8.7[9819]: error reading '/dev/lirc0'

I have the same problems and found no solution yet ...

Greets Axel

---

### Post by halfer2 on 2017-06-03
I had to switch to ir-keytable because of this, and it's been a pretty crappy experience for me - input lag with some buttons is bigger, stuff like irexec is out of the question, so only one keymap for the whole system, instead of per application, like I could do with LIRC and IRExec

---

