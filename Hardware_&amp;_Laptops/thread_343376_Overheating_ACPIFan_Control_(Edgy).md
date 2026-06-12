---
title: "Overheating: ACPI/Fan Control (Edgy)"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by sadams on 2007-01-21
Hi All,

NOTE: Previously posted in the "General Help" forum [[http://ubuntuforums.org/showthread.php?t=341163]](http://ubuntuforums.org/showthread.php?t=341163]) but have received no responses - hence I am reposting here (Hardware & Laptops) as perhaps it is more appropriate.

If I am posting this in the wrong way or wrong place or doing something inappropriate or overly dumb please help me out and let me know :-)
Is it something I should take to Launchpad ??

Quick Summary.
I have a problem regarding overheating/acpi control of the CPU fan.
Essentially: when the temp gets hot it seems the CPU fan cannot be activated, resulting in the temp warning siren going off and the temp rising and rising as reported in /proc files.

This (or something like it) has been reported elsewhere but I believe not properly addressed/fixed - correct me if I am wrong

Below is a full report - I hope it helps.

1) Intro:
=========
I have witnessed this a few times and have a reproducible case.
I have done some initial research (googling/forum searching) and this has been reported/discussed - however it seems people have treated it as a problem with the message, rather than a an actual problem with the acpi/fan control.

I think this is potentially a dangerous problem as it could cause overheating (and consequent hardware damage?)

Some system info:
-----------------
Running Edgy
uname -a
Linux shaft 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

from: cpuinfo
------
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping : 9
cpu MHz : 3007.288
cache size : 512 KB
-------

from: /proc/acpi/thermal_zone/THRM
----------------------
% more *
::::::::::::::
cooling_mode
::::::::::::::
cooling mode: active
::::::::::::::
polling_frequency
::::::::::::::
<polling disabled>
::::::::::::::
state
::::::::::::::
state: ok
::::::::::::::
temperature
::::::::::::::
temperature: 49 C
::::::::::::::
trip_points
::::::::::::::
critical (S5): 100 C
active[0]: 85 C: devices=0xdffe3bd0
---------

2) Problem description
======================
When I run something CPU intensive (i.e. wav => mp3 encoding with lame) for a period of time (a few minutes plus) I get the following symptoms:
a) CPU load at 50% (is 100% of a virtual CPU) as expected for Hyper Threading P4
b) Temp reported in /proc/acpi/thermal_zone/THRM/temperature climbs/increments steadily as job continues
c) when temp reaches 85C (the threshold in trip_points file) warnings are generated in /var/log/messages:
------------
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:51:59 shaft kernel: [18129602.424000] ACPI: Unable to turn cooling device [dffe3bd0] 'on'
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Transitioning device [FAN] to D0
Jan 17 18:52:00 shaft kernel: [18129602.732000] ACPI: Unable to turn cooling device [dffe3bd0] 'on'
------------

d) A minute or two later there is an "alarm sound" from the PC speaker (i.e. NOT the audio system) - a scary "siren like sound".... my machine is in pain... it is calling to me.... it needs help !!!
e) If I ^Z (suspend) the job in the shell.... obviously the CPU usage drops to nothing... and I watch the reported temp decline back to a steady state.
f) if I resume the job (fg in shell) the process is repeated (temp climbs - log file messages - alarm sounds)


3) Conclusions:
===============
I believe that the message reported is a genuine one... in that the system detects the temp threshold correctly, and attempts to start the fan. For some reason (I have no idea why) this fails.... and is reported accordingly in the log file. If I do not intervene (i.e. suspend job) the temp climbs and climbs.. my machine screams in pain (er.. issues audible alert).
Would this go on until a melt down ?
Is it dangerous ?

It certainly seems straightforward to me.
It certainly has only occurred since I move to Edgy (previously ran Warty and Hoary on same machine - never had this).


4) FIX IT!
==========
Can someone give an authoritative reply to this - or tell me how (else) I should report it ?

Many thanks - Steve

---

### Post by tweedledee on 2007-01-21
If you're just relying on the BIOS to control the fan, you may have mixed success (I have never had the BIOS work reliably, in Linux or otherwise, to control fan speeds).  It might help to try the approach in this thread: [http://www.ubuntuforums.org/showthread.php?t=42737](http://www.ubuntuforums.org/showthread.php?t=42737).

---

### Post by sadams on 2007-01-22
Hi,
Thanks for the interest and response tweedledee.

RE: "If you're just relying on the BIOS to control the fan"

I don't understand what you mean, my perspective is...:

It seems to me the OS is correctly detecting an increase in temperature, and (correctly?) attempting to "turn on" the fan ("cooling device"), resulting in a failure and appropriate log file messages.

Are you suggesting this does not work, somehow is not intended/expected to work?

I would really appreciate a steer on this from somebody who really understands "how this is intended to work" and can confirm my interpretation of the events and log entries, or alternatively can explain my misunderstanding and interpret them correctly.

Many thanks,
 Steve.

---

### Post by sadams on 2007-02-06
Hello,
This is another appeal for help - I feel kinda ignored and "out in the cold" (sniff).

2 weeks after posting this here I haven't had either:
 i) A useful reply which addresses the issue
or
 ii) Suggestions/pointers (or even flames!) telling where to take this or where to stick it !

It seems an important issue to me (potential h/w damage) - imagine if you switched a family member over to ubuntu only to have them get a serious overheating problem on their PC!

I am an occasional user of this forum, and am aware that it is possible I am "doing something wrong/dumb". I am also aware of the reputation of the ubuntu-community as being welcoming and helpful.
So - please can someone take an interest.. if you can't solve the technical issue at least help with suggestions of where to go next... and critique/comment on my post and suggest how / where I should report a similar issue next time.

Many thanks for any interest :-)
Steve.

---

### Post by ebababi on 2007-02-24
Hi!

Your problem looks like a standard dash - thermal conductor - fan failure case.

Proof on this can be considered the CPU's idle temperature, which is too high.

1. Check that all fans are working.
2. Give a blow to the heat pipes with compressed air so to remove the dust.
3. Replace the thermal conductor paste between the CPU and the heat pipes

You can ignore the ACPI warning if you will see with your eyes the fans working ([https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63550](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63550)).

Sorry for the bad english...

---

### Post by yemu on 2007-02-28
oh man, i've found your post by accident, and i must say, you've just saved my day! i had a terrible problem with my notebook fan (turning on all the time). i took your advice and blew in air vent hole in the back of the laptop (i didn't have compressed air). big dust cloud went through the hole and suddenly my notebbok became completly quiet! 
thanks!

---

### Post by Heliix on 2007-03-03
hi to all.
here is a possibly useful command to turn on the fan manually:

# echo "on" > /proc/acpi/fan/FAN/state
to turn it off again, use:
# echo "3" > /proc/acpi/fan/FAN/state 
(note: really "3", not "off" or "0" or ...)

it worked for me on HP Omnibook  6100 with Ubuntu Breezy
but it doesn't work on my new laptop MSI MegaBook S271 with Edgy as /proc/acpi/fan/ is an empty directory
I also didn't succeed in setting lm-sensors (no chips were detected) :( 

can someone help me or give me any hint? where could I set the temperature at which the fan is turned automatically on?
thanks in advance.

---

### Post by sadams on 2007-03-08
Hello again,

Note I have also contributed to a Launchpad bug log on this - although it is currently being ignored. Apparently there is insufficient resource for it to be "triaged" prior to being assigned to somebody, or alternatively refuted as a bug and closed down.

See: [https://launchpad.net/ubuntu/+source/acpid/+bug/71465](https://launchpad.net/ubuntu/+source/acpid/+bug/71465)

I have read the point mentioned by "ebababi" (thanks for taking an interest).
If I read you correctly, you seem to be saying:
 "Regardless of the log file messages, I have previously seen overheating problems due to poorly performing or damaged fans. That must be your problem too - fix your fan"

Whilst this makes sense (of course!) if the fan is the problem - it does not address the issue of the OS reporting it cannot switch on the fan - a problem which only appears to manifest on edgy.

i.e. 
  i) System gets "busy"... CPU runs hotter
 ii) System notices temp raise - this is right and normal
iii) System decides it's time to switch on the fan once the threshold reached - again, normal & sane behaviour
 iv) System fails to switch on fan *AND* reports the error in the correct place (messages file)

So... if my fan is broken/clogged/under-performing... of course it would fail to cool my machine. However, if the OS is unable to "turn it on" when needed (as the message says) then THAT is a bug/feature/problem with the OS.

"ebababi" seems to suggest I should ignore the messages file messages - or do I misunderstand ?

Also you say:
[INDENT]Proof on this can be considered the CPU's idle temperature, which is too high.[/INDENT]
Based on what ?
Are you suggesting that the one "snapshot" of the system temp taken when writing this up (and my PC was busy) is in some way indicative of the system's default or average running temp?
I don't understand why you would assume that... and you seem to jump to a conclusion based on a flawed assumption (please correct me if I am wrong).

Please can somebody who really understands this - i.e. "How is this mechanism intended to work" make an authoritative statement.

Re Heliix & cat > state
Does not work for me.

 [INDENT]
root@shaft:FAN> pwd/proc/acpi/fan/FAN
root@shaft:FAN> cat state
status:                  off
root@shaft:FAN> echo "on" > state 
bash: echo: write error: Exec format error
root@shaft:FAN> cat state 
status:                  off
root@shaft:FAN> echo "on" > /proc/acpi/fan/FAN/state
bash: echo: write error: Exec format error
root@shaft:FAN> 
root@shaft:FAN> echo "status:                  on" > state 
bash: echo: write error: Invalid argument[/INDENT]

Also tried to vi it (could not write the file) and created a version in /tmp then "copy it on top" - 
[INDENT]root@shaft:FAN> cp /tmp/state- state 
cp: writing `state': Invalid argument[/INDENT]


Thanks again for any interest & comments.
I am frustrated that neither here or on launchpad has anyone who claims to understand the process (how it is intended to work) been able to make a response and explain this.

Am I doing something wrong?
Is there nobody here who understands this?
Are there people who could explain this but for some reason not interested/motivated to do so?

What do I need to do to make progress ???

Cheers, Steve.

---

### Post by godvalve on 2007-04-03
Any luck on this yet dude? 

dmesg shows that the system fan in my laptop fails to start as well. Perhaps the lack of help we are getting on this is because not enough people realize that they are also having the same problem. I will have to stick to Vista on my toshiba Satellite A100 until this gets sorted out. :sad:

[17179572.976000] ACPI: Thermal Zone [TZ00] (50 C)
[17179572.976000] ACPI: Invalid passive threshold
[17179572.980000] ACPI: Transitioning device [FAN0] to D0
[17179572.980000] ACPI: Transitioning device [FAN0] to D0
[17179572.980000] ACPI: Unable to turn cooling device [dffe243c] 'on'
[17179572.980000] ACPI: Thermal Zone [TZ01] (44 C)

And again at:

[17179594.696000] ACPI: Transitioning device [FAN0] to D0
[17179594.696000] ACPI: Transitioning device [FAN0] to D0
[17179594.696000] ACPI: Unable to turn cooling device [dffe243c] 'on'
[17179594.704000] ACPI: Transitioning device [FAN0] to D0
[17179594.704000] ACPI: Transitioning device [FAN0] to D0
[17179594.704000] ACPI: Unable to turn cooling device [dffe243c] 'on'

---

### Post by gibarian on 2007-04-14
I'm having the exact same issue. Overheating almost every time I've been using the laptop for an extended amount of time.

Toshiba Satellite A100 as well.

---

### Post by godvalve on 2007-04-21
Maybe this will help:

Under Wiindows vista the little fan at the bottom of the laptop runs at two speeds. When the system is idle, the fan runs at a slow ebb and a faint wind can be felt from the exhaust port. When the system is under load, the fan ramps up its speed and the exhaust wind picks up in force/pressure. Under Fiesty, this fan only runs at the low ebb speed. The fan never ramps up and after some amout of use, the laptop starts to get really hot. Here's hoping that the next version of Ubuntu "Just works."

---

### Post by corrrnbread on 2007-04-24
i'm a new user to linux, i currently have xubuntu feisty dual booted with windows xp, i'm pretty sure i'm having a similar problem... whenever my computer boots up or i load windows, the fan runs normally, but as soon as the xubuntu startup screen shows up, my fan stops. i previously had this problem with edgy, but i never realized until i recently upgraded to feisty. i just assumed my fan wasn't needed. but i see those same error msgs in the log about "transitioning device" and "unable to turn cooling device on". according to /proc/acpi/thermal_zone/THRM/temperature, it says -267 C... i really am confused about this whole issue, i'm sure that my fan needs to run, it runs almost constantly in xp. also, i'm not sure if this is related, but my computer has been locking up since i upgraded to feisty, could it be related to the cpu starting to overheat? thank you in advance for trying to help a :confused:  girl like me!

---

### Post by Harii on 2007-06-20
I'm having the same thing happen.
if i use Debian or Mepis my laptop works very cool.
I'm using feisty on a Gateway 1200 Solo.

---

### Post by karlseith on 2007-06-27
I also am having the same problem on a Gateway 6510GZ laptop and all searches take me to threads like this; dead ends.  Last week I swapped out Win XP for Ubuntu 7.04 on my laptop and cant believe how hot it gets now. I literally cant leave the computer in my lap for more than 10 minutes after startup. I can't keep the computer operating at temps like this for long. Does anyone know of a way to lower the threshold for the operating temp??? 

karl@karl-laptop:~$   acpi -V
     Thermal 1: ok, 52.0 degrees C
  AC Adapter 1: on-line


Thanks,
Karl

---

### Post by Caprica_Resistance on 2007-11-15
I have Toshiba A100, the same problem here.

ACPI: Transitioning device [FAN0] to D0
ACPI: Transitioning device [FAN0] to D0
ACPI: Unable to turn cooling device [df807b40] 'on'

This is strange however, at least in my case with some time the logs chenge in some kind of that:

ACPI: Transitioning device [FAN0] to D0
ACPI: Transitioning device [FAN0] to D0
ACPI: Unable to turn cooling device [df807b40] 'off'

So as you can see, some times it cannot be turn **'on'** the other time **'off'**.
The fan seems to work, if temperature rises I can hear how it is speeding up. I have installed **computertemp** to look how temperature is changing:). We will see...

I have got this problem on Debian(etch) and Fedora8 too, so it is not only Ubuntu issue.
I have got a theory that because there is CoreDuo in my Laptop OS is assuming two CPU, maybe it is also supposing tha there should be two fans and tries to turn the other on and off:) Though as I say it may be rubbish:).

I have a favour to ask all of you that have a laptop to give command **dmesg | less** and search for that kind of log, it can be quite hidden. Maybe this problem is more common that it seemed to be, but it is not just very noticeable.

---

