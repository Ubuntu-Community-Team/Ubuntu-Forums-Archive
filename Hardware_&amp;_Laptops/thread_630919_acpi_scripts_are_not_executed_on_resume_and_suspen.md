---
title: "acpi scripts are not executed on resume and suspend"
date: 2007-12-03
forum: Hardware &amp; Laptops
---

### Post by dpchemist on 2007-12-03
Ubuntu 7.10, Thinkpad T61

I I have a strange problem with scripts in /etc/acpi/resume.d and /etc/acpi/suspend.d

First, I tried to add a new script in there (measuring battery capacity before and after suspend) but it did not work. (I used sudo install for that, so it was executable).

After that I tried to automatically restart Network  Manager on resume and added this line to existing /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh:

```
#!/bin/sh
. /usr/share/acpi-support/state-funcs
setLEDThinkpadSuspending 0
**NetworkManager restart**

```

However, it did not work.
Then I commented out the line *setLEDThinkpadSuspending 0* in that script (it turns off suspend LED on the laptop after resume). The funny thing is that after resume that LED indicator still turned off with commented line in the script.

Is it possible to track down what scripts are executed on suspend and resume? There is nothing helpful in /var/log/acpid. For now it seems that these scripts are not executed at all :confused:

Thanks in advance.

---

### Post by wahr on 2008-02-19
I'm having this problem too.

Im trying to place a script to restart my networking and it's not being run (testing echoes to a file).

neither for that matter are any of the other scripts which were already there.

how do I get the script to execute?

---

### Post by reacocard on 2008-02-19
you are taking the wrong path to making a script for acpi. the correct way is to make a full new script in /etc/acpi/suspend.d and /etc/acpi/resume.d. to take the OP's problem for an example, the files would be something like this:

/etc/acpi/suspend.d/53-stop-nm.sh:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager stop
```

/etc/acpi/resume.d/64-start-nm.sh:
```
#!/bin/sh
/etc/dbus-1/event.d/25NetworkManager start
```

then do
```
sudo chmod +x /etc/acpi/suspend.d/53-stop-nm.sh
sudo chmod +x /etc/acpi/resume.d/64-start-nm.sh
```

the numbers in the filename indicates the order it appears in the suspend/resume process, take a look at the other scripts to get an idea of what happens when. The chmod commands make the scripts executable so that acpi can actually run them.

---

### Post by wahr on 2008-02-19
I put your suggestions thrugh hours of thorough testing.. the scripts are definitely not running at all from /etc/acpi/resume.d

how do i fix this, or is there another place to put scripts to be executed on resume?

---

### Post by reacocard on 2008-02-20
> **wahr said:**
> I put your suggestions thrugh hours of thorough testing.. the scripts are definitely not running at all from /etc/acpi/resume.d

how do i fix this, or is there another place to put scripts to be executed on resume?

if there're not executing, either you did something wrong or your acpi scripts are messed up.

---

### Post by wahr on 2008-02-20
I don't know what's fulfilling their function (probably gnome-power-manager), but I added echo comments into a file and nothing came out, implying none of them actually executed.  Further, one of the comments I added should have made my fan very very loud if it had executed.

While I'd like to diagnose the problem and solve it, I just want to run these scripts on resume.

assistance would be greatly appreciated.  until then I'll be cycling those 3 commands on a dedicated shell

---

### Post by reacocard on 2008-02-20
> **wahr said:**
> I don't know what's fulfilling their function (probably gnome-power-manager), but I added echo comments into a file and nothing came out, implying none of them actually executed.  Further, one of the comments I added should have made my fan very very loud if it had executed.

While I'd like to diagnose the problem and solve it, I just want to run these scripts on resume.

assistance would be greatly appreciated.  until then I'll be cycling those 3 commands on a dedicated shell

hm. try editing resume.sh and prepare.sh, put an echo to file in as the first command in the file. If that's not executing, something higher up the suspend chain isn't working normally.

as for gnome-power-manager, while it does some prep on it's own it eventually just calls the acpi scripts to do the actual suspension, so unless you changed it to use a different backend at some point that part should be fine.

---

### Post by wahr on 2008-02-21
it appears both sleep.sh and resume.sh are not running as well.  I ran them manually as root and they placed comments in my little log file just fine.

I hope youre still around : )

---

### Post by reacocard on 2008-02-21
> **wahr said:**
> it appears both sleep.sh and resume.sh are not running as well.  I ran them manually as root and they placed comments in my little log file just fine.

I hope youre still around : )

that's very strange, and implies something at a higher level isn't using the normal methods.

here's the chain of events in suspending as I understand it:
gnome-power-manager -> sends dbus message to hal
hal -> executes /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
hal-system-power-suspend-linux -> executes /etc/acpi/sleep.sh

you can try testing those scripts, see where it's failing. let me know how it goes.

---

### Post by wahr on 2008-02-21
never mind I apparently cant read.. will update this post as I test

---

### Post by wahr on 2008-02-21
from my tracing through these scripts, those hal scripts don't call acpi at all, they send a call to /usr/sbin/pm-suspend (and a linked file pm-suspend-hybrid), which moves to scripts in /usr/lib/pm-utils/sleep.d
I'm thinking I might need yours which call acpi as a replacement?, or your guidance in that regard?

UPDATE: placing properly formatted scripts into sleep.d (which serves as both sleep and wake) will result in their execution in this process.
I'd still like to convert my computer's resume process to acpi though.

---

### Post by reacocard on 2008-02-21
> **wahr said:**
> from my tracing through these scripts, those hal scripts don't call acpi at all, they send a call to /usr/sbin/pm-suspend (and a linked file pm-suspend-hybrid), which moves to scripts in /usr/lib/pm-utils/sleep.d
I'm thinking I might need yours which call acpi as a replacement?, or your guidance in that regard?

UPDATE: placing properly formatted scripts into sleep.d (which serves as both sleep and wake) will result in their execution in this process.
I'd still like to convert my computer's resume process to acpi though.

hm, are you using hardy? if so, then they must have changed to using pm-utils by default, in which case using sleep.d is the correct way to go.

---

### Post by dtk_ on 2008-02-21
Hey guys.
I am having -somewhat- the same problem.
I want my notebook (Acer TravelMate) to xlock before suspending. Not too unusal that wish, is it?
I am running Xubuntu 7.10 Gutsy Gibbon.
So I checked out /etc/acpi/sleep.sh. If I put an ```
echo 'This is /etc/acpi/sleep.sh' >> /var/log/acpid
``` into it, it is executed when suspending my notebook via Fn+F4 (didn't check out the standard shutdown dialogue, yet). If I put ```
xlock &
``` right behind it, it isn't executed, though -.- No errors in /var/log/acpid.
But then again, if I execute the script manually via ```
/etc/acpi/sleep.sh force
``` from a root shell, xlock is executed. Is that weird, or am I just missing something obvious? It's just 2 consecutive lines, so if the xlock command was in some if branch, so would be the echo :-/
Additionally, the call to xlock seems to be syntactically correct, as it works when calling the script directly. Sry, dudes, I just don't get it :-|
Maybe you can give me a hint what to check next.
Thx in advance
dtk

PS As far as I can see, /etc/acpi/events/sleepbtn is not executed, as setting ```
action=/usr/bin/xterm
``` doesn't seem to influence the suspend process at all. -.-

---

### Post by wahr on 2008-02-22
i've never messed around with xubuntu, but I know /etc/acpi/sleep.sh simply calls on the scripts in sleep.d and resume.d in ubuntu.

If you are placing scripts in there and theyre not executing, I'd repeat the diagnosis steps I did.
-echo statements in the other scripts in the directory
if it doesnt work try the ones in the pm sleep.d directory.
(this may seem condescending, but just want to get everything I can think of out of the way) -- remember when adding scripts into these directories to make sure they begin with a number 

wish I could offer more to you but im just a computer literate newbie poking around myself : P

---

### Post by b.q.wemer on 2008-02-25
Hi,

placing the scripts in sleep.d works for me, too. Obviously those things have changed in Hardy. 

Many many thanks for that.

Greets

---

