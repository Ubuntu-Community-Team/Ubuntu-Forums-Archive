---
title: "How to put Ubuntu 10.10 into Standby (S1) mod ?"
date: 2011-01-31
forum: Hardware
---

### Post by kapetr on 2011-01-31
Hello, 

I'm using desktop PC and need the Standby mod.

> 
$ cat /proc/acpi/sleep 
S0 S1 S4 S5 


Fist terminology:

ACPI S0 = on
ACPI S1 = standby (low cpu, monitor off)
ACPI S3 = Suspend to RAM (except of memory all is turned Off)
ACPI S4 = Suspend to disk (Ram2Disk and Off)


So even if my BIOS does not support S3 (STR), Ubuntu make this working.
BTW how ?!

**But how to enter S1 (Standby) mod ?**

pm-utils do not include nothing like "pm-standby"!
Gnome power management (e.g. power buton) let me select only STR/STD (S3/S4).

I had try also ```
xset dpms force off

```

but in few seconds (or sometimes immediately) monitor goes on (without any action of me) ?! What is the wakeup event ?!

__So - how to enter S1 mod or at least switch off monitors in Ubuntu ? [/U]

I have try google - but all info are very confusing.

--kapetr

---

### Post by kapetr on 2011-02-01
I nobody there, who wants and knows how to switch monitors into sleep mode ?

I have test, that if I allow GNOME PM to switch off Monitors after e.g. 10 min - then it works and Monitors stay sleeping up to I move mouse or something ...

Also there is no system problem to put monitors into sleep, but 

**how to do it manually ?**

*--kapetr*

---

### Post by kapetr on 2011-02-04
nobody ?

Please help.

---

### Post by kapetr on 2011-02-08
Is there really nobody knowing ACPI in Ubuntu ?

---

### Post by kapetr on 2011-02-18
nobody knows or nobody needs ?

---

### Post by kapetr on 2011-02-25
My **"Do it yourself"** solution.

I had discuss with Author of gnome-pm - without success - he things only useful pm mod is S3, other points of view do not have any chance :-( 

So authors of ACPI power saving modes can offer S1, manufacturers of HW can implement it, but if there is by [gpm] no want to allow freedom of choice for users ...

So the simplest is to do what pm-utils do in the final:

**echo -n "standby" >/sys/power/state ** as root.

> BTW: do not try "sudo echo ..." - it do not work. Now I know why not :-)
(Nobody is perfect :-)
If with sudo, then <sudo bash -c "echo ...">


But it works partially - e.g. monitor stays ON. The problem is, that pm-utils do before it some hooks. So better way is:

to **modify pm-utils scrips** - just a few rows. I made a new symlink to pm-action called **pm-standby** and the changes you can see in attachments. Maybe is it not very clean, but as simple hack it works.

_Note:_ Other solution is of course to allow in BIOS just "S1" instead of "S1&S3", but it is the same bad solution, that do not let you free choice - since then you have only S1, not S3. And S3 is useful - better for longer sleeps as S1 is better for shorter one.

I hope it will help someone ...

--kapetr

---

### Post by Henk Poley on 2011-03-07
Maybe I'm missing something, but couldn't you add the `xset dpms off` as a hibernate sleep hook in /etc/pm/sleep.d?

See: [http://manpages.ubuntu.com/manpages/lucid/man8/pm-suspend.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/pm-suspend.8.html)

---

### Post by kapetr on 2011-03-15
If you mean to use just this hook for S1 (instead of use hooks of S3) ...
maybe it would be enough.

But with hooks of S3 it works, so I use it "as it is".

BTW - the "xset dpms force off" works not in Ubuntu - see 

[http://ubuntuforums.org/showthread.php?t=1681648](http://ubuntuforums.org/showthread.php?t=1681648)

So it is the other reason, why I do not try it as hook for S1.

--kapetr

---

### Post by bingel on 2011-04-16
...and resume? How do you resume? I can resume only by power button. Are you able to resume through mouse or keyboard event?

---

### Post by kapetr on 2011-04-18
Yes - key press or mouse move wakeups the maschine.
--kapetr

---

