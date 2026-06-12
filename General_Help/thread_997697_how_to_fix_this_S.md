---
title: "how to fix this :S"
date: 2008-11-30
forum: General Help
---

### Post by markomk on 2008-11-30
when i run airodump-ng eth2 this shows me :S

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211
or ARPHRD_IEEE80211_PRISM instead.  Make sure RFMON is enabled:
run 'ifconfig eth2 up; iwconfig eth2 mode Monitor channel <#>'

---

### Post by jpkotta on 2008-11-30
You should use a better title in the future.  Something at least indicating it is a problem with airodump-ng, and not, say, Firefox.  It is also better to put it in the networking category, as this is a networking problem.

Have you tried just doing what it says?  You'll need to prefix the commands with sudo.  
```
sudo ifconfig eth2 up; sudo iwconfig eth2 mode Monitor channel *number*
```

---

### Post by markomk on 2008-11-30
> **jpkotta said:**
> You should use a better title in the future.  Something at least indicating it is a problem with airodump-ng, and not, say, Firefox.  It is also better to put it in the networking category, as this is a networking problem.

Have you tried just doing what it says?  You'll need to prefix the commands with sudo.  
```
sudo ifconfig eth2 up; sudo iwconfig eth2 mode Monitor channel *number*
```

well i though that i have problem with wireless drivers :S
i have already use commands with sudo,but the problem is same :S

btw when i use ...sudo iwconfig eth2 mode Monitor channel *number*
i got this:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth2 ; Invalid argument.

---

### Post by jpkotta on 2008-11-30
Just to be sure, you're substituting an actual number for the word *number*, right?

It is entirely possible that the problem is in the drivers, in the sense that they don't implement Monitor mode.  You have different hardware than I do, and my hardware is elsewhere right now, so I can't play with it yet.

---

### Post by binbash on 2008-11-30
dude you should read aircrack-ng howto.First you have to change the mod to monitor.Aircrack-ng 's official website is perfect place ;)

---

