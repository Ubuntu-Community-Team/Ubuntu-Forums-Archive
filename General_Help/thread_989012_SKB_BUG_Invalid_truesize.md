---
title: "SKB BUG: Invalid truesize"
date: 2008-11-21
forum: General Help
---

### Post by ykanello on 2008-11-21
Dear all,
I am running Linux 2.6.22-14-sparc64 sparc64 GNU/Linux on a Sparc V120.
Its a typical system with the Ultrasparc IIe Hummingbird cpu.

I am getting a kernel message in the /var/log/kernel.log which I cannot understand nor I know if its anything alarming or not. 

kern.log:Nov 21 09:10:08 fatme kernel: [417890.173779] SKB BUG: Invalid truesize (360) len=192, sizeof(sk_buff)=232


I have search in some forums and I have seen few people with similar message but no response after that. 
anyone else had the same problem?
Thanks in advance,
Y.

---

### Post by 1hunter8 on 2008-12-02
I agree with you!![img]http://links.longhainet.com/haha.jpg[/img]-----------------------------------------------------------------------------------------------------------------------------------Signed Network: Not A Bad Man, A Woman Does Not Love!Recommendation:[Slot Machine](http://www.macrown.com/slot_machine.asp) / [Vending Machine](http://www.macrown.com/vending_machine.asp) / [Casino Machine](http://www.macrown.com/casino_machine.asp) / [Arcade Machine](http://www.macrown.com/arcade_machine.asp) / [Gumball Machine](http://www.macrown.com/gumball_machine.asp)

---

### Post by 60hbe16es52 on 2009-01-12
there are four kinds of jewelry,[wholesale jewelry](http://www.jewelryol.com/),[fashion jewelry](http://www.jewelryol.com/),[handmade jewelry](http://www.jewelryol.com/) and [costume jewelry](http://www.jewelryol.com/) ,which one do you like ?

---

### Post by gyterpena on 2009-03-29
Having similar problem message is 
  SKB BUG: Invalid truesize (1592) len=1422, sizeof(sk_buff)=184
I was able to replicate it. It happens only when I'm streaming video through openvpn connection. It does not seem to cause any other problems then completely spamming syslog.

Is it possible to disable logging for this event?

---

### Post by ykanello on 2009-03-31
> **gyterpena said:**
> Having similar problem message is 
  SKB BUG: Invalid truesize (1592) len=1422, sizeof(sk_buff)=184
I was able to replicate it. It happens only when I'm streaming video through openvpn connection. It does not seem to cause any other problems then completely spamming syslog.

Is it possible to disable logging for this event?

So I would assume has to do with the network driver then.
As I do not stream anything, just have a lot of snmp queries (O&M server).

but is it really that?

---

### Post by gyterpena on 2009-03-31
According to this [thread ]("http://bugzilla.kernel.org/show_bug.cgi?id=10996") it is caused by ipsec or openvpn traffic and should be fixed in 2.6.27.20 and 26.28.8.

Edit 1.4.2009: I also found that ftp traffic does not trigger it.

---

### Post by ykanello on 2009-04-03
Isn't this bug for X86 cpu's?
This is running on a Niagara... :(

---

