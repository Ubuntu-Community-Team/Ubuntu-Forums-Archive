---
title: "Wondershaper won't give me my bandwidth back!"
date: 2008-09-13
forum: General Help
---

### Post by Alucard-sama on 2008-09-13
I recently used wondershaper to throttle my network interface down to 10kb/s in order to use a VOIP box while using the net and it worked fine.
The problem is now I can't get it to go back up, "sudo wondershaper clear [interface name]" didn't work and neither did "sudo wondershaper [interface name]" followed by speeds higher than I need.
"sudo aptitude purge wondershaper" didn't help either.

Anybody know how this can be fixed?

---

### Post by Neo_The_User on 2008-09-13
Fix it with destroying the settings you made with the program or keeping the settings / speed you selected while having your bandwidth back?

---

### Post by Alucard-sama on 2008-09-13
> **Neo_The_User said:**
> Fix it with destroying the settings you made with the program or keeping the settings / speed you selected while having your bandwidth back?

Lolwot?

---

### Post by cariboo on 2008-09-13
I just had a look at the readme file it says:

> If you want to remove the shaper from the interface, run 'wshaper stop'. To see status information, run 'wshaper status'

that should solve your problem.

Jim

---

### Post by Neo_The_User on 2008-09-13
Do you care if you lose all your changes you made to Wondershaper or not? If you don't care about that, then I can help you. I spent about 3 days trying to figure out where ubuntu hides all the configuration files for all the applications so if you need to erase the config files for wondershaper (like if you want your computer the same way it was before you even installed wondershaper) I can do help you.

To erase all traces of wondershaper ever being on your computer and getting everything back the way it was then erase the following files from their directories using gksudo nautilus or deleting them via terminal.

/usr/share/doc/wondershaper
/usr/sbin/wondershaper
/usr/share/man/man8/wondershaper.8.gz
/var/lib/dkpkg/info/wondershaper.list
/var/lib/dpkg/info/wondershaper.md5sums

P.S. doing a complete removal of any application via synaptic does not erase the configuration files (at least not once for me)

---

### Post by Alucard-sama on 2008-09-13
> **cariboo907 said:**
> I just had a look at the readme file it says:



that should solve your problem.

Jim

"command not found"

---

### Post by Neo_The_User on 2008-09-13
> **Alucard-sama said:**
> "command not found"

Try this

wondershaper stop 

To see status information, run 

wondershaper status

---

### Post by Alucard-sama on 2008-09-14
> **Neo_The_User said:**
> Try this

wondershaper stop 

To see status information, run 

wondershaper status

"Cannot find device 'stop'"
"Cannot find device 'stop'"

---

### Post by Alucard-sama on 2008-09-14
> **Neo_The_User said:**
> Do you care if you lose all your changes you made to Wondershaper or not? If you don't care about that, then I can help you. I spent about 3 days trying to figure out where ubuntu hides all the configuration files for all the applications so if you need to erase the config files for wondershaper (like if you want your computer the same way it was before you even installed wondershaper) I can do help you.

To erase all traces of wondershaper ever being on your computer and getting everything back the way it was then erase the following files from their directories using gksudo nautilus or deleting them via terminal.

/usr/share/doc/wondershaper
/usr/sbin/wondershaper
/usr/share/man/man8/wondershaper.8.gz
/var/lib/dkpkg/info/wondershaper.list
/var/lib/dpkg/info/wondershaper.md5sums

P.S. doing a complete removal of any application via synaptic does not erase the configuration files (at least not once for me)

Purge has deleted all these files already and deleting them manually didn't help either.

---

### Post by Neo_The_User on 2008-09-14
AH HA! try this!

wondershaper eth0 stop

if it doesn't work replace eth0 with whatever interface you use for networking (eth1 etc etc)

---

### Post by Alucard-sama on 2008-09-14
> **Neo_The_User said:**
> AH HA! try this!

wondershaper eth0 stop

if it doesn't work replace eth0 with whatever interface you use for networking (eth1 etc etc)

No luck either... :(

---

### Post by whazooo on 2008-09-14
Dude, Didnt you say you purged wondershaper from your machine?

well if so, wondershaper eth0 stop wont work.


1. type in a terminal;
locate wondershaper

if you find no instance of wondershaper bianary

2. then ps aux |grep wondershaper
kill the process

3 either reboot

3a. or reinstall wondershaper and use the commands that the others gave you

---

### Post by Alucard-sama on 2008-09-15
Still no luck :(
This is driving me nuts.

---

### Post by mazter on 2009-01-05
I don't know if you are still experiencing same crappy situation but I just experienced same issue and resolved it only switching the args.

wondershaper clear eth0

I was doing wondershaper eth0 clear and it was saying 'succesfully cleared' but doing nothing. Now, it is fully cleared.

---

