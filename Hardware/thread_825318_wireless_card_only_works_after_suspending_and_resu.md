---
title: "wireless card only works after suspending and resuming laptop."
date: 2008-06-10
forum: Hardware
---

### Post by jman_121 on 2008-06-10
Hello my name is Jeremy, 

  This is actually my first post in the Ubuntu forum.:KS I have been using various versions of Linux for a while now. Anyway, on to the question. 1) Has anyone ever experienced this problem before?  and 2) does anyone know how to get around this. I will provide any and all documentation required for debugging (dmesg, etc.). I have never heard of this happening before. The hardware is: 08:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02). The laptop is an Everex KR3200w. I am using Hardy Heron. I have tried multiple times and  different methods to get this integrated wireless card to work with no avail. I just happened to let the computer suspend and resume by using the power button, poof the light magically came on. It really isn't a huge deal for me, but I figured that I would through it out there. Like I said before just post for any info that may be required. Thanks in advance. :)

              Jeremy

---

### Post by jman_121 on 2008-06-11
This is my dmesg output (note: this is the entire output after a boot up sequence then suspending and resuming the laptop.) 

      
       Jeremy

---

### Post by markir on 2008-07-18
I am seeing this as well - however on an Asus pro31j (same as f3jr I think). The wireless card in this case is Intel 3945ABG.I saw some other postings about how this could be connected with using a static ip in the network setup for wlan - however in my case I'm using dhcp.

(this is a much better problem than the usual one of no wireless *after* suspend!).

P.s: my first post as well.

---

### Post by warp99 on 2008-07-18
It could be an error when the networking boot script runs. I have this problem with my Atheros AR2413 card. The way around this is to place a small script inside your /etc/rc.local file like this: 

```
# Restart wireless networking due to an Atheros driver error
/sbin/ifdown ath0 2> /dev/null
/sbin/ifup ath0 2> /dev/null 
```

the '2> /dev/null' portion can be omitted since it only suppresses any error messages. Just use 'sudo gedit /etc/rc.local' to add the script. If needed replace 'ath0' with the system name of your card.

Edit:
In the rc.local file place the script between '# By default this script does nothing' and 'exit 0'.

---

### Post by markir on 2008-07-18
Thanks! - I tried running:

ifdown wlan0
ifup wlan0

immediately after boot + logging on - and yes, it fixes the issue! I'll patch my /etc/rc.local (actually this looks like the sort of thing to go in /etc/rcS.d/networking, but I'm new to Ubuntu so I'll stick to the easy but possibly less than elegant fix)

---

### Post by warp99 on 2008-07-18
> **markir said:**
> ... I'm new to Ubuntu so I'll stick to the easy but possibly less than elegant fix)

Well Debian AFAIK doesn't use the rc.local script so normally your scripts would go in /etc/init.d then you would use the command 'update-rc.d' to set the runlevels and boot order.

For small items like restarting services or other little tweaks that need to run as root the rc.local script is just convenient since it runs at the end of all of the normal boot scripts.

---

