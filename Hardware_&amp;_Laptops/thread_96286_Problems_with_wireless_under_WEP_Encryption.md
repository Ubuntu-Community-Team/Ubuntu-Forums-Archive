---
title: "Problems with wireless under WEP Encryption"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by coderasm on 2005-11-28
Hello, I'm Phil.  I recently bought a Gateway MX3560.  I've installed Ubuntu 5.10 and am having problems with my wireless connection.  My wireless hardware is Intel PRO/Wireless 2200BG Network Connection (WM3B2200BG).  My router is a brand new netgear router.  Without any encryption on my router I am able to gain full internet access through my router from my laptop wirelessly.  When I change my router to any encryption method, my laptop still sees a wireless signal, but will not connect to the internet.  I've done everything correctly by having the wireless settings as DHCP, HEX key and have entered in the key correctly.  Should I update the driver?  I noticed Ubuntu 5.10 was released on 10/13/05 and there is a more recent driver that was released on 10/20/05.  Any help would be greatly appreciated.  If I am not able fix this problem, has anyone used another linux distro and known to have full wireless capabilities using this same wireless hardware? Thankyou

---

### Post by `GooZ´ on 2005-11-28
maybe try installing network-manager, you'll find it in the universe repositories

---

### Post by fog on 2005-11-28
> sudo ifconfig [COLOR="Red"]ath0 [/COLOR]down
sudo iwpriv [COLOR="Red"]ath0[/COLOR] authmode 2
sudo ifconfig [COLOR="Red"]ath0[/COLOR] up

[COLOR="Red"]ath0[/COLOR] is my network, use yours.
Today I solve the same problem for my wireless network.
Use WEP key and mac addresses for more security.

---

### Post by coderasm on 2005-11-28
Thanks for the help.  I tried your commands Fog, but authmode 2 was not recognized as a command.  Which package is the authmode command attached to?

---

### Post by fog on 2005-11-29
**authmode** is an Authentication mode
> sudo iwpriv ath0 authmode 1 <---- **open authentication**
sudo iwpriv ath0 authmode 2 <---- **shared key authentication**
sudo iwpriv ath0 authmode 3 <---- **802.1x authentication** 
not a command.
Take a look here: 
[http://ubuntuforums.org/showthread.php?t=95862](http://ubuntuforums.org/showthread.php?t=95862)

Is WEP the right authentication method for your hardware?

---

