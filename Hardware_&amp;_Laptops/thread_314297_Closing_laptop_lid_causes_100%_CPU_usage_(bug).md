---
title: "Closing laptop lid causes 100% CPU usage (bug?)"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by Tachyon_ on 2006-12-07
I didn't make launchpad bug report or anything yet, because I'm sure bug this serious -It could break a laptop, couldn't it?- would have been reported. That's why I am believing that this could have something to do with my computer.

So, I have Kubuntu edgy, no beryl and no applications running. The computer is quite new, Fujitsu Amilo with Core Duo. I set up powermanager to do nothing or lock the screen when lid is closed. Every single time closing a lid causes cpu usage to jump immediately to 100%. When I open the screen after a short break, Power manager just informs: "Lid closed, doing nothing now". Does it go to loop or something? The most interesting this is that, when I close the lid so barely that the screen goes of, but don't slam it down, the usage stays at few percent.

I notice this by leaving my laptop to run over night. It shutdown every single night. When I installed superkaramba theme, I clearly see the usage:

[http://img515.imageshack.us/img515/3919/snapshot2nv4.png](http://img515.imageshack.us/img515/3919/snapshot2nv4.png)

It would be nice to inform about a bug, or get a solution to problem only bothering my laptop.

---

### Post by zoryn on 2006-12-29
It seems to be a problem in acpid. It appears to occur mostly in Acers. If you "sudo killall acpid" the cpu stays quiet.
The problem appears to be, when the lid is closed, the system continuously reports "lid closed", and it hogs all the cpu. Even when the lid is already opened, it takes a while to process all the "lid closed" reports.
If only there was a way to disable the lid events in acpid...

---

### Post by Tachyon_ on 2006-12-30
**SOLVED**

Since you informed me that the problem was with acpid, I googled out what the whole acpi thing was, found the customicing acpid scripts ThinkWiki site, and then commented out the event and action in the file which determines acpid event for lid screen close.

So, the code would be:
cd /etc/acpi/events
sudo nano lidbtn (Or you can open it with kate or gedit)
### Comment out, that means add #, at the front of event and action
Press CTRL+O, then Y (Saves the file, you can also save it with gedit or kate)
CTRL+X closes nano

Kill acpi in order for changes to take effect:
sudo kill -SIGHUP `pidof acpid`

now I have acpid, CPU stays at 1-5%, BIOS (If I'm correct) swiches off the screen. Note that I just figured out what the whole acpid (acpi daemon?) was, so I'm not totally sure what I'm doing, but it seems to work ;)

---

### Post by dm1024 on 2007-02-13
Same thing with Asus A6Tc & Ubuntu Feisty. 
I've commented those strings.
Now CPU usage is 30% for both cores (dual-core CPU).

---

### Post by nicolasdiogo on 2007-11-12
hi,

i am using a A6Tc laptop with Gutsy and having a horrible time.
could you tell what your kernel boot parameters are?

thanks in advance,

---

