---
title: "Restarting wifi on T400"
date: 2008-11-05
forum: Hardware
---

### Post by kikazaru on 2008-11-05
How can I restart my wifi? I have a T400 Lenovo, and the wifi works fine until I suspend, or use the Fn F5 button to turn it off. After that I can't get it back without restarting. The strange thing is, it was working (I was using the Fn F5 control to turn of blue tooth, and it toggles through all four settings of wifi and bluetooth on/off) but it stopped for some reason. 

Is there a command I can use to restart the wifi? -The wifi light doesn't come back on at all after it's been disabled for some reason. (The problem is not the wifi switch on the computer itself).

(Intrepid Ibex 8.10)

---

### Post by fstonedahl on 2008-11-08
I was having somewhat similar problems (on a T400 with ubuntu 8.10, with the ABG card, using the madwifi drivers.)  Namely, it had trouble reconnecting after a suspend.  It seemed like running "dhclient" from the command line helped sometimes, but it could have been random luck too.  I also wondered if the failure to reconnect was reated to the keychain thing that stores wireless network passwords.  My problem might have been different.  

In any case, currently my wireless doesn't work at all (possibly because I upgraded my kernel), so I guess I'll go start my own thread about that.  :-/

---

