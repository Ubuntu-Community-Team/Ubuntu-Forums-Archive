---
title: "Making sure the iptables rules are saved"
date: 2008-08-29
forum: General Help
---

### Post by kavon89 on 2008-08-29
I followed [this guide]("https://help.ubuntu.com/community/Internet/ConnectionSharing#Configure%20NAT") to set up my server as a gateway and I have specifically linked the rules that you add to iptables there.

Thing is, how do I know these rules will remain saved through a reboot? Is there a file I can check or edit to make them permanent?

---

### Post by p_quarles on 2008-08-29
To list rules:
```
sudo iptables -L -v
```
The short answer to your question, though, is no, setting rules in iptables will not save them from session to session by default. You'll need a script that implements them, or alternatively a list of the rules which can restored via iptables-restore. 

I don't have the exact syntax in front of me at the moment, but a search will find them. I know that I have posted a procedure for saving and restoring rules here in the past.

---

### Post by kavon89 on 2008-08-29
I found by searching that I pretty much just copy the current iptables settings thing with:

sudo sh -c "iptables-save > /etc/iptables.up.rules"

then add this line to /etc/network/interfaces under one of the interfaces (doesn't matter):

pre-up iptables-restore < /etc/iptables.up.rules


I'm posting this anyone else searching for this solution. I'm going to go try rebooting my server. :)

---

### Post by kavon89 on 2008-08-29
Didn't work, instead I added the rules to /etc/rc.local file to be run on boot.

---

