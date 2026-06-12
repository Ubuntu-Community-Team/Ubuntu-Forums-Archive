---
title: "iptables question"
date: 2008-07-20
forum: General Help
---

### Post by dapim on 2008-07-20
what is the difference beetween this two statement in a firewall shell script 
, what impact the $ make in the beggining of each line?

iptables -A INPUT -p tcp -m tcp --sport 143 -j ACCEPT


$iptables -A INPUT -p tcp -m tcp --sport 143 -j ACCEPT

---

### Post by cprofitt on 2008-07-21
from my limited experience the $ is used for accessing a variable, but not seen it used like this... in this context it almost makes it look like a comment, but that is not what I am used too.

My guess is the second line would be all screwed up and not work correctly if it was in a script file.

---

### Post by Rocket2DMn on 2008-07-21
If you are looking at a website to get that command, the $ symbol is often used to tell you that the following text is part of a command.  If you look at your terminal, you generally see that the least character before the cursor is the $ sign.

If it is attached to something (usually in capital letters), then it is a variable.

---

### Post by bodhi.zazen on 2008-07-21
> **dapim said:**
> what is the difference beetween this two statement in a firewall shell script 
, what impact the $ make in the beggining of each line?

iptables -A INPUT -p tcp -m tcp --sport 143 -j ACCEPT


$iptables -A INPUT -p tcp -m tcp --sport 143 -j ACCEPT

In a script, it is always ideal to run a command with the full path, especially if the script is to be run as root.

$ = variables. Usually you write variables in call caps, although you do not need to.

So, amongst other things, early in the script :

IPTABLES='/sbin/iptables'

Then in your script, all iptables with :

$IPTABLES

1. Less typing # still readable

2. More secure

---

### Post by cprofitt on 2008-07-21
bodhi_zazen and rocket2DMn: thanks for the clarifications.

---

