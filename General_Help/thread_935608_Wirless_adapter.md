---
title: "Wirless adapter?"
date: 2008-10-01
forum: General Help
---

### Post by Fc1032 on 2008-10-01
Hi all!

I recently put ubuntu on all my computers. So far all is working fine on the wired computers (i.e the physically connected computers). However, on the old laptop, i do not have wireless therefore, i use a D-Link DWL G112 wireless adapter. The device seems to work fine, it can detect my wireless network and other wireless networks around my house.

The problem occurs when i try to join a network. I try to connect to my home network, which has a WEP code/passcode on it. I type in the code, it does some 'configuring' but does not connect. It asks for my password again and again but is never actually connected. (I have the wireless adapter literally next to the wireless router)

Furthermore, i tried connecting to other networks without a passcode, but it doesn't work either. Is it a problem with the router? or wireless adapter? I have not configure either on install... (the router and modem worked fine OTB, so i did no configuring.)

Thank you! (I really do mean it!!:))

---

### Post by Fc1032 on 2008-10-01
Anyone? :(

---

### Post by Fc1032 on 2008-10-01
Bump...

---

### Post by Yellow Pasque on 2008-10-01
Some commands to help diagnose (try to connect to an unecrypted network before running iwconfig):
```
sudo lshw -C network
iwconfig
cat /etc/network/interfaces
```

---

### Post by Fc1032 on 2008-10-08
Thanks! I got the wireless adapter to work! Although, the reception is pretty weak (even though I am next to the router, it shows 67%) it works!

Thank you~~:KS

---

