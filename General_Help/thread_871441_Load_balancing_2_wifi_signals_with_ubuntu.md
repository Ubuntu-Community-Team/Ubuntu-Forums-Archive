---
title: "Load balancing 2 wifi signals with ubuntu?"
date: 2008-07-26
forum: General Help
---

### Post by flashuni on 2008-07-26
Does anyone know of any software/tutorials on load balancing 2 or more wifi signals in ubuntu.

Thanks, flashuni:KS

---

### Post by jimv on 2008-07-27
Woah...is that even possible?  Because that would be sweet.

---

### Post by oneporter on 2008-07-27
> **jimv said:**
> Woah...is that even possible?  Because that would be sweet.

My thoughts exactly.

---

### Post by tamoneya on 2008-07-27
this probably isnt what you are looking for but if you had two wireless cards (does anyone have two wireless cards) you could then connect to one network each and then bond the two connections.  Then use the bound connection for you internet.  Ubuntu should balance the load itself.

---

### Post by minstn on 2008-10-06
i guess the question was about having 2 separate ssids on the same WiFi card, similar to what FON ([www.fon.com](www.fon.com)) has. another thread for this topic is here: [http://ubuntuforums.org/showthread.php?t=939613](http://ubuntuforums.org/showthread.php?t=939613)

---

### Post by e30drift on 2008-10-16
I see where you are going with this...

I want to build a gateway/router/firewall server that will have multiple wifi connections.  

What I have been trying to do is to load balance all 4 connections.  

I found some tutorials around the tubes that might help.  In theory, a network adapter is a network adapter regardless if you're using wifi or cat5, so it should work on any WAN/LAN connection.

Here is what i found:
[http://lartc.org/howto/index.html]("http://lartc.org/howto/index.html")

---

### Post by andersja on 2009-06-30
Any success with this? 

Related problems with 2 wifi cards:
[http://ubuntuforums.org/showthread.php?t=1076863]("http://ubuntuforums.org/showthread.php?t=1076863")

---

### Post by t4thfavor on 2009-06-30
If you do this on one wifi card you will not have any speed benefit as the wireless pipe can only hold as m uch as it can hold no matter how many ssid's it has. You will however probably notice a speed drop due to the radio "context switching" between ssid's.

This is best done with multi radio devices, and even then its iffy due to channel contention (there are only 3 real channels)

---

### Post by andersja on 2009-08-05
Still though - if I have a laptop with built-in wifi but want to use a USB-wifi-dogle with a cantenna to extend range. How can I easily flip between them (or can they both operate at the same time without interfering?? or do I need to disable the built-in card in BIOS??

---

