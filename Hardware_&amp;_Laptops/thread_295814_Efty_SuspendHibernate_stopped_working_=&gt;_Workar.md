---
title: "Efty: Suspend/Hibernate stopped working =&gt; Workaround"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by hendribuntu on 2006-11-08
Hello people,

I have something I would like to share with you. Maybe there'd be a better place to write (or even file a bug report), but I haven't found out.

The situation was the following:
Dell D600 laptop - upgraded to edgy from dapper (earlier upgraded from breezy).

Suspend and Hibernate worked for me flawlessy in dapper. However, when upgrading to the Edgy Eft it stopped working. I figured out the hibernate UUID issue and fixed that one. However, it still did not work.

The Symptoms:
When trying to Suspend/Hibernate, the screen faded out but did not actually shut down. When moving the mouse, the X-LOCK wanted a password. The keyboard DID NOT work anymore (couldnt type..) so a reboot was necessary after that.. However, manually doing "echo 3 > /proc/acpi/sleep" or "echo mem > /sys/..something" DID work flawlessy.

The fix:
I manually tracked the problem with introducing 'logger -t acpi-debug "SOME  DEBUG POINT"' lines into the sleep scripts. Finally, I found the line that broke the suspending. It is:
INTERFACES=`/sbin/ifconfig | awk '/^[^ ]+/ {print $1}'`
in the file /etc/acpi/suspend.d/55-down-interfaces.sh.

The question:
I still do not understand why this line breaks my suspending. When I manually call it, it gives me "eth0 eth1 lo" as result. I commented the line and changed it manually to INTERFACES="eth0 lo". My /sbin/ifconfig output is attached, so you might be able to figure out something that I couldnt..

Cheers,
Hendrik

PS: it might be nice if someone could point me out where to file a bug report?

the ifconfig output:
eth0      Link encap:Ethernet  HWaddr 00:0A:AB:0A:3B:61  
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fa0a:ab61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1637057 (1.5 MiB)  TX bytes:341502 (333.4 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:90:4A:A1:EF:61  
          inet6 addr: fe80::290:4bff:feb2:8e61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3093 errors:0 dropped:109 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386203 (377.1 KiB)  TX bytes:8400 (8.2 KiB)
          Interrupt:5 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75440 (73.6 KiB)  TX bytes:75440 (73.6 KiB)

---

### Post by Ramses on 2006-11-16
Hi!

/etc/acpi/suspend.d/55-down-interfaces.sh file is part of acpi-support package. You should make a bug report about that package to launchpad.
I have similar problem with HP Omnibook vt6200. I couldn't still find out where suspend/hibernation stops in my case.

---

### Post by hendribuntu on 2006-11-20
Hi,

somehow, that work-around seems only to have worked for a couple of days. The same problem still exists and I have not yet been able to debug it. Hibernation somehow leads to an immediate wake-up, but suspend works with the 'echo' trick.

Cheers,
Hendrik

---

### Post by dpward on 2007-04-07
I've also got a Dell Latitude D600 running Ubuntu Edgy Eft (6.10), and I've been experiencing the same problem.  Attempting to suspend the laptop was cause the screen to fade to black but not power off, and the laptop kept running.  Moving the touchpad would cause the Xorg unlock dialog to appear, but I could no longer type anything with the keyboard to unlock the display (although the touchpad still worked).

I made the change you suggested to the /etc/acpi/suspend.d/55-down-interfaces.sh script, and I was suddenly able to suspend my computer and resume it.  The keyboard worked when the computer resumed.  However as pointed out, this fix was actually only intermittent.  Sometimes my laptop will fully suspend, but then other times it will just hang on a black screen without powering off the LCD.  When it suspends and resumes successfully, then it may have other problems...for example it then won't fully power off when I try to shut down the computer...it hangs after the Ubuntu splash screen disappears.

I've noticed that if I suspend my laptop while on the Ubuntu login screen (using the Options button in the lower-left corner), it always works.  However, after it resumes and I attempt to login, it will then hang during the login with an empty gray box in the upper-left corner.

Maybe the networking script was only one bug?  I was wondering if you tried your logging method further to see if you found something else in the scripts that is hanging it up?  (Once I have enough time to mess with it some more I might try that myself as well.)

Thanks for the help.

---

