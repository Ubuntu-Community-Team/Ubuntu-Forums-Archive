---
title: "Cant use Bluetooth A2DP, only 'telephone mode'"
date: 2017-04-16
forum: Hardware
---

### Post by docdoc2 on 2017-04-16
When connecting my Sony sb20 bluetooth receiver for my headphones, Ubuntu keeps being stuck in telephone dublex(HSP/HFP) (why does this mode exist anyway?), i cant change to normal mode, A2DP. I was able to do that in the past by playing around with reconnecting, deleting and finding device, but this also wont work anymore. Any other device connects normally to my headset, also Windows did on the same computer.Everytime i choose A2DB in the sound settings, it just jumps back to telephone mode when i close and reopen the settings menu.I need to use bluetooth because my audio jack is damaged.  Please help!

---

### Post by docdoc2 on 2017-04-16
OK i found a solution, had to edit /etc/bluetooth/audio.conf and change Disable=Socket HFP=false MaxConnected=2

---

### Post by docdoc2 on 2017-04-16
OK, so now that the computer was asleep the problem is back. It just wont change to normal mode, i have no idea how to repoduce the solution

---

