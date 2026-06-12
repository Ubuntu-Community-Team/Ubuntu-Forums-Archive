---
title: "Acer laptop high pitch noise when on A/C power"
date: 2007-12-05
forum: Hardware &amp; Laptops
---

### Post by trash on 2007-12-05
Anybody else with Acer Aspire hearing a high pitch noise only when the power cord is plugged in?

No noise in Vista
:~$ uname -r
2.6.22-14-generic

---

### Post by thegnu on 2007-12-05
I could be wrong, but it's probably capacitor whine, which I think means you can't do anything about it:

[http://www.google.com/search?q=capacitor+whine&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=capacitor+whine&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by trash on 2007-12-05
hmmm maybe my hearing is overly sensitive lol... I do still find it strange that the noise is only there when in linux and not there in windows. But since I am not experiencing any other problems like overheating... though i did just realize that my fan is always running in linux.

EDIT: and just as i finished writing that my fan shut off for about 5 seconds and then went back on.

---

### Post by David_H on 2008-04-09
Hi,

I've been experiencing the same problem, I didn't notice it in the small time I had Win XP on the laptop. I've read elsewhere it may be something to do with CPU throttles, but it seems odd it only happens on AC power.
I'll post if I find a fix.

Cheers,
Dave

---

### Post by deerhunter308 on 2008-04-28
I got the same thing tonight...........loaded the released Hardy Heron and I got the high pitched whine.....only happens with Linux...........XP is ok

Acer 5520-5334......stock hardware.........downgraded from Vista Home Basic to XP Pro

---

### Post by dasunst3r on 2008-04-28
I haven't taken apart an Acer power adapter, but I am learning about power electronics in my electrical engineering career.  As someone mentioned, it may be capacitor whine, or it may be a poorly-designed DC-DC switching circuit (you'd want to do switching at... say... 100 KHz).

For more information, have a look here: [http://users.ece.utexas.edu/~kwasinski/_5_EE362L_MOSFET_Firing_Circuit_PPT_Spring%2008.ppt](http://users.ece.utexas.edu/~kwasinski/_5_EE362L_MOSFET_Firing_Circuit_PPT_Spring%2008.ppt)

---

### Post by eznet on 2008-05-11
I have the same problem with my DV6000T.  The only solution that I have found is to [limit the processor power states]("http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises#Limit_ACPI_CPU_power_states"), which I learned about at thinkwiki.

Basically you need to do the following:
-Press Alt+F2 to bring up the "Run Application" window.
```
gksudo gedit /etc/init.d/acpid
```
-Enter your password
-Press ctrl+F to bring up the find dialog and search for 'load_modules()' (without ')
-At the end of the load_modules() function, (immediately after '"$PRINTK" > /proc/sys/kernel/printk') add:
```
echo 2 > /sys/module/processor/parameters/max_cstate
```
-Save the file and reboot Ubuntu and the noise should be gone (if it is the same problem).

-Matt

---

### Post by eznet on 2008-05-14
Ok, so I was wrong... This used to work, but no longer works with the newer kernels...  Here is where I am currently:
[http://www.mail-archive.com/linux-acpi%40vger.kernel.org/msg10354.html](http://www.mail-archive.com/linux-acpi%40vger.kernel.org/msg10354.html)

---

### Post by trash on 2008-05-14
When this thread re-surfaced I had to think why the noise doesn't bother me anymore... since i first posted I have stopped using windows and thought maybe i had become used to the sound.. but I just remembered I changed my power bar at some point, can't say if that is the reason but I do not have that hight pitched sound anymore... maybe somebody else can try a new powerbar and tell us if it worked.

---

### Post by eznet on 2008-05-19
Yea, mine is intermittent and is admittedly no where near as bad as it used to be with my old r3240 running Daper.  Even though it isn't as bad, sometimes it does bug me, though rarely.  I just kinda wish I could resolve the issue completely. Used to be that max_cstate was the answer, but no more... 
There is continued discussion on launchpad about it in various bug reports, but it really only seems to affect some models of laptops (seemingly, most recently Acers)... Who knows... I will not let it bug me too much.. As long as I have music on, I don't notice it... and like I said, it is intermittent anyways, so sometimes it isn't even audible... Small price to pay for so much free goodness I guess :)

-Matt

---

