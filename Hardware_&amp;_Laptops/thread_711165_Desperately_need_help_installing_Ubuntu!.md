---
title: "Desperately need help installing Ubuntu!"
date: 2008-02-29
forum: Hardware &amp; Laptops
---

### Post by killer_d76 on 2008-02-29
i have recieved my copy of Ubuntu 7.10 few days ago, and i would like to thank you all guys!, but i can't install it my Neo Empriva Laptop!... everytime i tried to install it.. i can see "cannot allocate..." or something.. and bios bugs found!.. then it reboot itself all over again :( , can anybody help me here?.. pplleeaassseee...

---

### Post by taurus on 2008-02-29
What is the spec of your laptop?

---

### Post by killer_d76 on 2008-03-01
thanks for the quick reply.. here's the specs of my laptop:

Neo Empriva

Microsoft Windows XP Professional Version 2002
Service Pack @

Intel Celeron
520 @ 1.60Ghz
520MB of RAM
80GB Hard Disk Drive

i really wanted to install Ubuntu or perhaps dual boot my computer.. thanks in advance!

---

### Post by seshomaru samma on 2008-03-01
It could be that the install media is damaged
I would suggest downloading another iSO ,burning it as slow speed and checking it for errors on boot (it has that option on start up)
If you still get that error -write down excatly what it is and paste it here
btw- what graphics card do you have?

---

### Post by killer_d76 on 2008-03-01
seshomaru samma,

right now am downloading xubuntu.. 

but we were able to install the ubuntu on my friends laptop (Neo Centrino.. older version of my laptop) using same live cd?!.. i was trying to get the error message and it doesn't pause even if i click "pause/break" button.. what i can only remember with the error that flash on the screen is something like this:

[ 18.340415] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[ 18.340467] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0

and bios bugs found!.. 

graphics card?.. am not sure, if look on my device manager and looking at the display adapters  here's what i presume my laptop grahipcs card is using:

Mobile Inte(R) 945GM Express Chipset Family

and i found this message right below the ubuntu back-up folder when i tried running the wubi-cdboot on the cd installer see attached file ( original title of this txt is drwtsn32.log but i change it because i was not able to attach it here)

thanks

---

### Post by seshomaru samma on 2008-03-01
i would actually recommend downloading the alternate CD
also try booting with the parameter:
```
pci=routeirq
```
(you need to write this command when ubuntu boots )
if this doesnt work try this:
```
acpi=off
```

---

### Post by killer_d76 on 2008-03-02
seshomaru samma,

thanks for all the help, i'll try your suggestion as soon as i downloaded the alternate cd (which taking me years to download the file!).. but i'll try to do your suggestion using the live cd first and i'll keep you posted guys!.. thanks for the help ;)

-arvin

---

### Post by killer_d76 on 2008-03-04
seshomaru samma,

thank you sooo.. mmuuccchh!!!... :guitar:

this thing rocks!.. i was able to install Ubuntu on my Neo Empriva!.. by following your very simple instruction and i am using it right now and looking forward to discover more about this great OS! 

- arvin

---

### Post by seshomaru samma on 2008-03-08
good


just interested, did you use the first command? the second? or just booted of the alternate CD?

---

