---
title: "Airplane mode on when powering up the computer"
date: 2021-06-19
forum: Hardware
---

### Post by georgesgiralt on 2021-06-19
Hello All
On my new Lenovo 15G2 ITL machine, running Ubuntu 20.04.2 LTS, now, when I power up the laptop, the airplane mode is on. 
It was not like that when I got the computer a few weeks back. Airplane mode was off and the Bluetooth mouse was running fine.
Then, the Bluetooth was shut down on boot up for a while (I had to log in to turn it on and get the mouse working.
Then, since a week, the WiFi also is off on boot up. 
I can't find a hardware reason for this and nothing wrong in the BIOS about this. I Can't find a reason on the syslog messages about that either. 
So I need your help and advice on what to check to troubleshoot this annoying behavior.
Many thanks in advance for your help !
Have a nice day and stay safe !

---

### Post by TheFu on 2021-06-22
I vaguely remember there being a difference in how networking is handled.  There is system-level controls which can start networking before a login happens and there are per-user network controls, which doesn't connect until a user session is active.  The second is more convenient for laptops, since individual non-sudo users can manage wifi connections. It also lets the system save the battery by disconnecting wifi and bt connections when they aren't active.

But I could be wrong.

By any chance, were any power settings modified recently? Perhaps power-saving mode?

---

### Post by georgesgiralt on 2021-06-23
Hello TheFu !
You were right. My problem came from a power saving software set to "extreme". The software I installed a few days ago is slimbookbattery from Slimbook Ubuntu laptop maker from Spain.

---

