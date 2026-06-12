---
title: "Network issues"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by indianatom on 2005-05-16
Hello, I'm using a dell 700m in combination with whereami to configure my nic and my ipw 2200.  However, I have some issues that I cannot seem to solve.  

1.  When I boot up with my nic connected to our router, the nic is assigned an ip address, but I cannot ping the gateway, nor can I access any internet.

2.  On bootup whereami states that another instance of whereami is running and that it will exit, but if the nic is not connected to the router, the wireless will work fine.

Here is what my detect.conf file looks like (sorry if it's a little long):

```
# It is a good idea to default to somewhere...
default lan

# Test for the presence of an ethernet connection plugged into eth1
testmii eth1 lan

if lan
  # If the testmii at the top was successful
	set INTERFACE eth1
	always notat w_eth0,wlan,wdhcp,eth0
   testdhcp    eth1,'*.*.*.*'    dhcp
else
  # If the testmii at the top failed
	modprobe ipw2200 w_eth0
fi

if w_eth0
  set INTERFACE eth0
  testap scan wlan
fi

# If we have found at least some WLAN APs in the vicinity, find out
# if we can do anything with any of them
if wlan
  testap      ebluff154,7961-686F-6F                     ebluff154,wdhcp
  testap      UCSD  													UCSD,wdhcp
  testap 	  Petra													Petra,wdhcp
  # # If there's anything there at all, try and DHCP off it
	testap      .+                  wdhcp
fi

# So it seems we should try and get DHCP off a WLAN AP
if wdhcp
	testdhcp    '*.*.*.*'    dhcp
fi

# And if we have DHCP (wired or wireless) we want to make
# a decision as to which LAN that is, exactly.
if dhcp
  # testdhcp    192.168.5.*     waiheke
  # testdhcp    192.168.7.*     tauranga
  # testdhcp    192.168.10.*    wellington
  # testdhcp    192.168.55.3*   picton
  # # Note that we only get here, if the one above is _unsuccessful_
  # testdhcp    192.168.55.*    rakaia
fi
``` 

I think I have a feeling for how Whereami works, but any help and/or suggestions would be greatly appreciated.  Thank you  :grin:

---

### Post by pestilence4hr on 2005-08-19
[QUOTE=indianatom]Hello, I'm using a dell 700m in combination with whereami to configure my nic and my ipw 2200.  However, I have some issues that I cannot seem to solve.  

1.  When I boot up with my nic connected to our router, the nic is assigned an ip address, but I cannot ping the gateway, nor can I access any internet.

2.  On bootup whereami states that another instance of whereami is running and that it will exit, but if the nic is not connected to the router, the wireless will work fine.[/QUOTE]

I'm currently battling whereami on my 700m.   I'm not having the same problems you're having (i don't think), but thought I'd suggest that you try using the --scriptdebug option to figure out what's going on.  What I have been doing is:
```

sudo whereami --scriptdebug shutdown
sudo whereami --scriptdebug
```

This will give you a much clearer idea of what is going wrong.  To me, it sounds more like you are misconfiguring your wired interface rather than a whereami problem, but I can't say with this amount of information.

I'm having problems with testmii and testarp not working properly, related to their dependence on the interface being up.  Doubt this is the same problem.

---

