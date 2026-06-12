---
title: "Internet Problem"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by appoloin on 2006-01-13
Hi guys,

Sorry to bother you all. Im a very vergin on linux as i been a windows eversinc my first pc but got sick ot the virus and windows problem.

Anyway, a wonderful person name penie was cool enough to drop me ubuntu at my work place and now installed in my computer. But having problem on the internet.

When i click on firefox, it seems not to detect that i have internet hence cant upgrade or sync on clock.

found the area where i can ping.. and it seems to ping but when i look down it shows that its not connected to the internet.. so question is, is it internet connected? i dont know..

Please help me. i will attach screenshot of the network area to give you guys an idea..

---

### Post by greenway on 2006-01-13
[QUOTE=appoloin]Hi guys,

Sorry to bother you all. Im a very vergin on linux as i been a windows eversinc my first pc but got sick ot the virus and windows problem.

Anyway, a wonderful person name penie was cool enough to drop me ubuntu at my work place and now installed in my computer. But having problem on the internet.

When i click on firefox, it seems not to detect that i have internet hence cant upgrade or sync on clock.

found the area where i can ping.. and it seems to ping but when i look down it shows that its not connected to the internet.. so question is, is it internet connected? i dont know..

Please help me. i will attach screenshot of the network area to give you guys an idea..[/QUOTE]

Hi there, 

For starters, for us to help you we really need more info...

Start by posting the output of the command "sudo ifconfig" and your /etc/network/interfaces file

---

### Post by gravediggers on 2006-01-13
Some people have a problem with Firefox that it hangs for ages then doesn't connect. I'm not sure if this is your problem, as I can't see what the results of your ping are!

What You can try is to type about:config in the address bar of firefox, then in the bar near the top that says filters type network, and there should be an entry that says some thing like "network.dns.ipV6.disable". Click on this entry, Right click, and choose the option "Toggle". This should set it to True.

Then try again and see what you get!

---

