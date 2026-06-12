---
title: "Available updates installation failed"
date: 2005-11-11
forum: General Help
---

### Post by wyles55 on 2005-11-11
Guys,

 I'm just a newbie in Linux, my problem is I can't install any available updates even if I use synaptics manager.( It starts downloading then continued installing the package then after few minutes , it stops as if the process was already finished.) But when I checked none were installed and the updates notifier still says the same numbers of available updates. Anyone please? I use dual boot OS ubuntu/win98, with partition size 6.0G/14.0G respectively. Duron 1GHZ w/ 128mb  RAM. Thanks in advance for your help. I am really willing to learn Linux and I think ubuntu is the best for me to start with.

---

### Post by taurus on 2005-11-11
What happens when you run these from a terminal?

sudo apt-get update
sudo apt-get upgrade

---

### Post by Galoot on 2005-11-11
I've had the same problem as the OP since last night, though it may have been longer as I was away from the computer for a week. This is with Hoary, not Breezy.

I wasn't in a hurry to update, so I tried again today with the same results.

*sudo apt-get update* and *sudo apt-get upgrade* worked for me.

---

