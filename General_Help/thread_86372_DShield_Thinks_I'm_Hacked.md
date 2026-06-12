---
title: "DShield Thinks I'm Hacked"
date: 2005-11-05
forum: General Help
---

### Post by reuben on 2005-11-05
On [http://dshield.org/](http://dshield.org/) you can check if you appear to be hacked, based on your IP address appearing in honey traps (I think). I tried it; it says that my IP has occurred 41 times in their DB. Most of the target ports are 6881, which of course is bittorrent, and is used by Azureus. Does this mean that somebody is hacking me *through* bittorrent, or are their records just out to lunch?

---

### Post by Remmelas on 2005-11-05
The first thing that screems to mind for me is, how do they deal with dynamic IP allocation from ISPs?  Seems possible to me that if someone assigned your current ip address before you was 'hacked'(whatever that may mean to the dshield people), that could be why u r listed.

---

### Post by Arktis on 2005-11-05
Is there a way to check how old the entries in the database are?  Also, the requirement they give for being put in the database "accessing other machines in a manner that their firewalls log as hostile." is pretty open.  If someone had their firewall set to log bittorrent connections as hostile and you happen to cross paths while he/she is stupidly messing with the same torrent as you with their firewall still on, then apparently you'll get put in the database.  That's what it sounds like to me.

On another note, did you guys see this

> Date: Mon, 7 Feb 2005 16:25:43 -0500

This user has been locked in the trunk of a 1980 Cadillac along with his PC and has been driven up and down a very bumpy road for several hrs and we believe that the problem is now resolved.

Thank you for the report

...on the main page?  :smile:

---

### Post by david_finlayson on 2005-11-06
[QUOTE=reuben]On [http://dshield.org/](http://dshield.org/) you can check if you appear to be hacked, based on your IP address appearing in honey traps (I think). I tried it; it says that my IP has occurred 41 times in their DB. Most of the target ports are 6881, which of course is bittorrent, and is used by Azureus. Does this mean that somebody is hacking me *through* bittorrent, or are their records just out to lunch?[/QUOTE]

First off, DShield is a giant database of firewall logs, not honeypots. People submit their logs daily and DShields analyzes them for odd patterns. Apparently, your computer (your IP address really) has attempted to connect with one or more DShield users' computer(s) on port 6881 a number of times. As you point out, this isn't necessarily an indication of you being hacked. For example, Windows boxes send out network traffic to find neighboring computers, printers broadcast their IP, etc. All of them would be in the DShield database. If the traffic from your computer is normal and nobody cares that your knocking on port 6881, then no problem. 

DShield picks up the zombie boxes when they start hammering the net. You've probably got little to worry about. (Though bittorrent IS an access point into your machine).

---

### Post by Qrk on 2005-11-06
Survival time:

Windows		285 min
Unix	           11084 min

From those numbers I don't think you have anything to worry about, on Ubuntu at least.

---

