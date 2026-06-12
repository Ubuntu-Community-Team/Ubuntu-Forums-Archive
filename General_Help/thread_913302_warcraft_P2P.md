---
title: "warcraft P2P"
date: 2008-09-07
forum: General Help
---

### Post by Juggercat on 2008-09-07
hello there all!
well... i installed wine and i can play warcraft perfectly on it... but when i try to connect to a private server it wont connect...
now from my experience with windows i can only assume this is a firewall problem... so i would like to ask how to open the ports for warcraft 3 which are 6112...

thx in advance for any help possible!


edit--

should i install firestarter, which is aparently easier to manage? if so do i have to delete the old one or do something weird? srry for so many questions im new to linux :S

well... ill keep googgling..thx

---

### Post by jerome1232 on 2008-09-07
Are you trying to connect to a friends computer which is hosting the game? 

If so he would need to open up his firewall/forward ports on his router.

Warcraft 3 (client side) shouldn't require any inbound ports on your computer, on Ubuntu, iptables (the firewall) is permissive (allows all connections outgoing and incoming) by default anyways.

If this is just some server somewhere are you sure you have the ip correct?

---

### Post by Juggercat on 2008-09-07
no, im trying to connect to a private server somewhere... and im pretty sure its teh correct ip... so i dunno :S
i guess i better check again... thx

---

### Post by ByteJuggler on 2008-09-07
What do you mean exactly, with "private server"?

---

### Post by Juggercat on 2008-09-07
um, i suppose its a hosted by some guy... 
unofficial server in any case...

---

### Post by ByteJuggler on 2008-09-07
> **Juggercat said:**
> um, i suppose its a hosted by some guy... 
unofficial server in any case...

Some guy on the internet?  Can other people connect to him successfully?   He needs to have his firewall configured properly for people to be able to connect to him, as another poster has stated.  If others cannot connect to him then that would suggest that the problem is be his end.

---

### Post by jerome1232 on 2008-09-07
> **Juggercat said:**
> um, i suppose its a hosted by some guy... 
unofficial server in any case...

So good trouble shooting, I'd try and connect from another computer (maybe call up a friend and see if they can connect), I'd also try and connect to other servers.

My bet is this is a server side error, either it's down or missconfigured.

---

### Post by Juggercat on 2008-09-07
cant be, ive been playing on this server few days ago for years...  and ive tried to connect to other servers and the same thing happens... it just says connecting and stays there... some servers that are offline it wont even say connecting... immediatly says it cant connect... so im assuming they are online the other ones

---

