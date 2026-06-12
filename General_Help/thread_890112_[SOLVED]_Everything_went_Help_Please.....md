---
title: "[SOLVED] Everything went Help Please...."
date: 2008-08-14
forum: General Help
---

### Post by gato333 on 2008-08-14
ok im really worry i dont want to have reinstall Ubuntu one more time to fix things im a beginner i know a lottt about windows not so much about Linux i love it but i have bad luck with it.
Ok here is the problem i was downloading packages or whatever you call it from the sypnatic and i was trying to open a game with Wine and it crashed and the computer kinda restarted by itself that was it now graphics are bad, no wireless at all,everything super slow please i dont know what to do help.

---

### Post by gato333 on 2008-08-14
Ok in case someone is gonna  make a comment about this i fixed the slowness but i cant bring back the wireless is not even showing up in the restricted

---

### Post by gato333 on 2008-08-14
Well never had much luck with Forums, well whatever i figured it out on my own i looked in a really helpful place is called Google if this can help anyone. 

what i did was i deleted Wine and all the Packages i was downloading from Sypnatic restarted and that took care of the Graphic and slowness problem, then after that i did sudo aptitude update, sudo aptitude upgrade the upgrade clean all the old files left by the deleted packages.

Then i used a very useful tool is called bcm43xx-0.3.2-internet this thing resetted a whole bunch of things with the ndiswrappers and the Windows drivers and a few more things, restarted and here i am posting again from my Wireless. 

Hope this help anyone.

---

