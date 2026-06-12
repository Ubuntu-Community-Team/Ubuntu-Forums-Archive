---
title: "Fresh boot faster than recovering from hibernate"
date: 2008-08-24
forum: General Help
---

### Post by kwc01 on 2008-08-24
Hello,

I've struggled for months trying to resolve hibernate and suspend issues on all three (different) desktop configurations and have met with limited success.  

This latest one has me pretty stumped--is there anyone who can help?

Here's what is happening: A fresh boot takes 1:06 minutes on my Asus M2N-MX SE PLUS system in Ubuntu 8.04.  Recovering from hibernate takes 1:28 minutes.

Most of this time (more than 50 seconds) is spent with these two lines displayed on the screen:

31.5xxx   i8042 kbd 00:0a: activation failed
31.5xxx   i8042 aux 00:0b: activation failed

When it finally recovers, all works properly.

Two questions:
1. What is the fix for the "activation failed" errors?
2. Is there a way to determine what my system is doing during that 50 seconds or so, and how would I fix that?

[I]Edit: With respect to the second question, I ran dmesg and discovered that at 38 seconds, these messages are logged:
  eth0: no link during initialization
  ADDRCONF(NETDEV_UP): eth0: Link is not ready

Then it waits... and the next log entry occurs at ~83 seconds.[/I]  


Thank you,
kwc

---

### Post by bthoward on 2008-08-24
Does ETH0 have a network connected to it?  Perhaps try connecting something so that it can get an address and move on.  It may be trying to bring up the network card and having to time out.  I doubt that has anything to do with why resuming takes longer than a cold boot.  I've never timed it but my lappy I think takes longer to resume than to boot but if I had things I was doing then the hibernate is a welcome extra bit of time as it brings me right back to where I was.

---

### Post by kwc01 on 2008-08-24
Actually, when I run the network tools, the network device 'eth0:' is not connected to anything.  However, "eth0:avahi" is connected to the LAN.

How can I keep the boot sequence from attempting 'eth0'?

---

