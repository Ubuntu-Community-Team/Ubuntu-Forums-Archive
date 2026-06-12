---
title: "Bash Script to disable throttle on Core 2 Duo"
date: 2011-01-19
forum: Hardware
---

### Post by pamandonald on 2011-01-19
My laptop is BenQ R56, it has Core 2Duo processor. the problem is when running on battery the cpu automaticly enable it's 50% throttling feature (for battery life reason) but it become annoying me because it's performance is not enough to using firefox, in addition on-demand default up threshold is 95 % which give me dual core performance with 500MHz. i had used the script in forum to change default on-demand threshold to 55%, it's good. but i want to disable throttling completely, now manually i used a script to disable throttling:

#!/bin/bash
sleep 3
g=1
while [ $g -le 2 ]
do
sleep 5
echo 0 > /proc/acpi/processor/CPU0/throttling
sleep 10
echo 0 > /proc/acpi/processor/CPU1/throttling
sleep 10
done

the problem is this script doesn't detect when i was logout, so the second login give me two script running  which lead to a race condition. (the throttling  i gave permission as user):D

so i ask help from you guys, to give me a clue to insert logout detection in this script

thanx in advance
Greeting from Danang
Indonesia

---

### Post by pamandonald on 2011-02-01
ah, i found the solution 
[http://ubuntuforums.org/showthread.php?t=25857](http://ubuntuforums.org/showthread.php?t=25857)

I:p can add the code into the file:
/etc/gdm/PostSession/Default

---

### Post by pamandonald on 2011-04-27
wah, i found that the echo command should be after the cat command, thanks to [http://superuser.com/questions/81053/acpi-throttling-in-ubuntu](http://superuser.com/questions/81053/acpi-throttling-in-ubuntu), now the echo script always run perfect, withaout cat command sometime echo command failed

here is the script: (may be someone need it)


#!/bin/bash
sleep 10
g=1
while [ $g -le 2 ]
do
cat /proc/acpi/processor/CPU0/throttling
sleep 1
echo 1 > /proc/acpi/processor/CPU0/throttling
sleep 10
cat /proc/acpi/processor/CPU1/throttling
sleep 1
echo 1 > /proc/acpi/processor/CPU1/throttling
sleep 10
done

---

