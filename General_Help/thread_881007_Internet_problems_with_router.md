---
title: "Internet problems with router"
date: 2008-08-05
forum: General Help
---

### Post by kwakkwak on 2008-08-05
Hello guys.
I installed the latest ubuntu and I'm having a problem. When I'm connected directly to the internet, everything is ok, I can surf the internet on ubuntu ... everything works. But when im connected to my router, I can't acces the internet. But on windows, I can. I used to have this on older versions of ubuntu too. I just can't access the internet when on ubuntu and when behind router. My router is D-Link DI-604.
I hope anyone has a solution for this! Greetz :KS

---

### Post by Qchan on 2008-08-05
> **kwakkwak said:**
> Hello guys.
I installed the latest ubuntu and I'm having a problem. When I'm connected directly to the internet, everything is ok, I can surf the internet on ubuntu ... everything works. But when im connected to my router, I can't acces the internet. But on windows, I can. I used to have this on older versions of ubuntu too. I just can't access the internet when on ubuntu and when behind router. My router is D-Link DI-604.
I hope anyone has a solution for this! Greetz :KS

[b][color=darkred]
Can you get online if you were to connect your PC directly to your modem under Ubuntu?
[/b][/color]

---

### Post by kwakkwak on 2008-08-05
Yes I can, and now after trying some more: when I am behind the router and I start firefox, when I wait 20 minutes, it would load google. But I can't do apt-get or surf properly.
But I can surf at full speed when directly to my modem.
Any more help?
Cheers =)

---

### Post by tdcdodger on 2008-08-05
For the following suggestions, please note that I have only used the server edition of ubuntu, thus I am not sure how to configure these features using the gui.

Are you are getting an IP address from your router. Is DHCP enabled on the network interface that is connected to the router? 

Is your DNS properly configured? One easy way to test this is to use nslookup to see if you can resolve and IP for google.ca

If you can't resolve an IP, that means your DNS is not configured properly, or that your are not connected to the internet as a whole.

---

### Post by MALEADt on 2008-08-05
Hi all,

(I have tested kwakkwak's network too, so have some knowledge about it)

> Are you are getting an IP address from your router. Is DHCP enabled on the network interface that is connected to the router?
Affirmative, the computer receives it's IP and DNS servers from the router's DHCP. That DNS is his ISP's, as the router has no DNS caching capabilities.
I tried changing the DNS servers to an alternative (OpenDNS), but this didn't help. This kinda rules out DNS problems.

However, I need to add something to what kwakkwak said: in fact the internet *might sometimes* work *a very tiny bit*. Browsing the web does not work (or very rarely and extremely unstabel), but an *aptitude upgrade* <might> work sometimes. Funny stuff is that when it works, updates get pulled in at the maximum speed (which is ~1500kbs). I also checked for duplicate IP's, and specifically picked an static ip out the DHCP's range, without any luck. Also, an *ifconfig* didn't show up any packet loss or other problems.

EDIT: if I recall correctly, kwakkwak did had identical problems on a previous computer, so it does not seem to be driver-related.


I'm out of ideas, can't imaging what else it could be. Guess I overlooked something :)
Maybe I'll dump some packets to see if the router is secretly complaining about something, or mark differences between a Windows request and Linux request (which there shouldn't be).

---

### Post by kwakkwak on 2008-08-05
Yes, all what MALEADt sais is correct. It's true that I had this also on other computers. But I used the same router.
Cheers

---

### Post by cowboyup6983 on 2008-08-05
if you are dual booting can u go into windows configure your internet to work with the router. then boot into ubuntu and you shouldnt have to do anything for the internet to work. lets say if i had to reset router for some reason, i would have to boot into windows to configure all my settings and once im back online, switch back to ubuntu and im all set.

---

### Post by kwakkwak on 2008-08-05
My internet works fine when under windows, it also works on my mac, but when I switch to ubuntu, it doesn't anymore.

---

### Post by markthecarp on 2008-08-05
> **kwakkwak said:**
> My internet works fine when under windows, it also works on my mac, but when I switch to ubuntu, it doesn't anymore.

kwakkwak are you using a wireless or wired connection?

---

### Post by kwakkwak on 2008-08-05
Hello,
I am using wired connection.

---

### Post by kwakkwak on 2008-08-05
Hey guys, I'm sorry that I have to bump this topic. But I really need to get this ubuntu working by tomorrow. So do you think there is any method to solve this? Or do you think I should just buy a new router? Cuz if that what is needed I'll just do that. I need to get this running. Cheers

---

### Post by markthecarp on 2008-08-05
Well that rules out flacky wireless. Strange problem sir.

---

### Post by kwakkwak on 2008-08-05
I guess I just buy a new router then? :/
Anyone has some advice for a good brand?
I don't know much about routers...

---

### Post by kwakkwak on 2008-08-06
problem solved, bought a new router.
cheers

---

