---
title: "FN + wireless key + Inspiron 1300/B130"
date: 2009-03-14
forum: Hardware
---

### Post by greyhawk on 2009-03-14
Hello folks. 
Newbie Linux user here. I've installed Ubuntu 8.10 on a Dell Inspiron 1300/B130 and so far I'm very impressed. Everything works but one thing: All the Function keys work as they should but I can't get the wireless to switch on with the FN + F2 key. There are no other hardware 'switches' on the laptop to activate it. I've opened Terminal and typed in the command 'sudo lshw -c network' and Ubuntu sees the wireless card (Broadcom BCM4318) but it's listed as 'disabled'. Am I hooped or is there an app or driver which will activate the FN + wireless key on this laptop ?
Thanks in advance for any suggestions.

Greyhawk

---

### Post by greyhawk on 2009-03-14
Any ideas ? Anyone ?

---

### Post by jonnyara on 2009-06-09
Are you still using 8.10? 

I have this laptop, and I don't think this is an issue with the FN + wireless key. I think that the issue is that you do not have the correct kernel modules.

Have a look at ndiswrapper, this should solve your problems on 8.10

---

