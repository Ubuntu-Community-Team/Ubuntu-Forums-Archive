---
title: "Dial-Up problem dialing but not connecting"
date: 2005-11-20
forum: General Help
---

### Post by libbyz on 2005-11-20
After managing to make my winmodem work, I can dial my ISP but I cannot establish connection using wvdial. 
Here's the output of wvdial: 

--> WvDial: Internet dialer version 1.54.0 
--> Initializing modem. 
--> Sending: ATZ 
ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 
ATQ0 V1 E1 S0=0 &C1 &D2 
OK 
--> Sending: ATX3 
ATX3 
OK 
--> Modem initialized. 
--> Idle Seconds = 300, disabling automatic reconnect. 
--> Sending: ATDTwhatever 
--> Waiting for carrier. 
ATDTwhatever 
CONNECT 49333 NoEC 
--> Carrier detected. Waiting for prompt. 
--> Don't know what to do! Starting pppd and hoping for the best. 
--> Starting pppd at Sun Nov 20 15:44:22 2005 
--> pid of pppd: 22512 
--> Using interface ppp0 
--> Using interface ppp0 
--> Disconnecting at Sun Nov 20 15:44:52 2005 
--> The PPP daemon has died: PPP negotiation failed (exit code = 10) 
--> man pppd explains pppd error codes in more detail. 
--> I guess that's it for now, exiting 
--> The PPP daemon has died. (exit code = 10) 

The exit code 10 according to man pages means: 
PPP daemon: 
10 The PPP negotiation failed, that is, it didn't reach the point 
where at least one network protocol (e.g. IP) was running. 

However using dmesg I can see that all the required services run when the PC is booted: 

# dmesg|grep IP 
[4294671.581000] IP: routing cache hash table of 8192 buckets, 64Kbytes 
[4294713.038000] IPv6 over IPv4 tunneling driver 
[4294723.588000] eth0: no IPv6 routers present 
[4296254.249000] CSLIP: code copyright 1989 Regents of the University of California 

# dmesg|grep TCP 
[4294671.581000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes) 
[4294671.582000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes) 
[4294671.582000] TCP: Hash tables configured (established 262144 bind 65536) 

# dmesg|grep PPP 
[4296254.251000] PPP generic driver version 2.4.2 

The modem is detected during startup: 
# dmesg|grep tty 
... 
[4294700.981000] ttyLTM0 at I/O 0xbc00 (irq = 10) is a Lucent/Agere Modem 

I've also tried pppconfig, but when executing pon nothing happens! I've set correctly the modem setting... 

I've read many posts,manuals,books, I have googled it but still can't solve the problem of connecting to the Internet. Does anyone have any ideas what might be wrong? 

Thank you for your attention, 
Libb

---

