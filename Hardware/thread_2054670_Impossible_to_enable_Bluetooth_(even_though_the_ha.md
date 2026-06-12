---
title: "Impossible to enable Bluetooth (even though the hardware is on)"
date: 2012-09-07
forum: Hardware
---

### Post by recent convert on 2012-09-07
Hi! I'm having a problem that I see is quite common, but I still can't find an answer in the forums.
I just installed Ubuntu 12.04 (dual boot, kept Windows just  in case) on my new Acer Aspire One 756-877. As soon as I installed it I  also installed the Broadcom driver, since wifi wasn't working, and that  solved it right away. But when I tried Bluetooth, I had a problem that I  see is quite recurring: 

-The hardware is on (and working fine under Windows)
-The icon shows up on the menu, giving me the options of turning  Bluetooth on or off, and then just "Bluetooth preferences". 

-I can apparently turn it on that way, which only lights up the icon but  makes no difference at all (and doesn't give any other options in the  Bluetooth menu)
-When I open "Bluetooth preferences" (whether Bluetooth is apparently on  or off, it makes no difference), it says it's disabled and will not let  me slide the button to enable it. I've rebooted, but nothing happens. -The material is Broadcom and the port (if it's relevant at all) is  Port_#0001.Hub_#0003
  I tried the following commands suggested in other similar questions, with no result at all:
  
[LIST]
[*]sudo dmesg | grep blue and
[*]sudo service bluetooth start and
[*]sudo /etc/init.d/bluetooth start
[/LIST]
  Any other clues on what I can do? Thanks for your time!

---

### Post by recent convert on 2012-09-10
(By the way, when I said that the commands gave no result, what I meant to say is that they say that it is already working)

---

