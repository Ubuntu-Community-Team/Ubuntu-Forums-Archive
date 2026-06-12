---
title: "HP G60 Laptop - Wireless disabled on startup"
date: 2012-04-13
forum: Hardware
---

### Post by Billy Ng on 2012-04-13
My HP G60 laptop has a button that enables and disables the wireless adapter.  I've never had need to touch that button in the few weeks since I've moved from Win 7 to Ubuntu 11.10.

Two days ago I needed to whip out the laptop at work, had a network port to plug it into, and hit that button to disable the wireless - now it refuses to come on by default.

Did a bit of searching yesterday, found a few threads on the subject but nothing seems to resolve the issue for me.  First up was the rfkill idea:

```
$ sudo rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```

This is what shows up on boot.  Once I tap the button physically, then enable wireless, these all switch to "no" and I'm off and running, but that's really annoying.

Another thread opined that it might be my NetworkManager.state file, but I verified that it looks good and even renamed it and let it generate new:

```
$ cat /var/lib/NetworkManager/NetworkManager.state 

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

Any ideas?  Again, wireless was enabled by default for weeks, right up until the very first time I hit the button.  Now, even though I shut down with wireless enabled/on and working (as it is right now as I'm typing this to you), it keeps going back to being off after a restart.  I can clearly see my wireless indicator light go orange (dead) during shut down which I don't remember it doing previously.

--Billy

---

