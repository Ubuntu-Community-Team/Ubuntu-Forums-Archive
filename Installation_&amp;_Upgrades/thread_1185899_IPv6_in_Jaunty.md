---
title: "IPv6 in Jaunty"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by seventynine on 2009-06-12
GRRRRRRR....

Which smart guy suggested to enable IPv6 in kernel and set it to first preference over IPv4? Since upgrading to Jaunty today I've had a constant headache trying to make the internet slowdown go away. Now I'm seriously thinking of switching back to windows xp after 3 years of Ubuntu on my desktop. 


So far:
- Internet works fine from other PC's. Rules out ISP/Router.
- Driver works, confirmed. Open source atheros anyway.
- Issue not app specific (ie. Firefox, Opera, Pidgin, Evoluton, Apt) all experience slowdown. Web pages like news.google.com taking around 10 seconds to load. Used to take 1 sec. Same with pidgin. And others.
- Tried the following to disable IPv6 (unsuccessful in all):
     + Set 1 to /proc/sys/net/ipv6/conf/all/disable_ipv6
     + Tried the following approach recommended somewhere:
            sysctl -w net.ipv6.conf.ath0.disable_ipv6=1
     + Added ipv6.disable=1 to /boot/grub/menu.lst  

All the searching and effort, and still IPv6 is on. Seems that there's nothing short of kernal recompile I can do to disable IPv6. Really feel like smackin the guy who decided that this should go in kernel AND be the default option AND could not be disabled by a simple command. This is  not mature as far as decision-making goes.

Yes some people will say thats the problem of ISP not supporting ipv6. And yes ultimately it is. But complaining isn't going to get it fixed in a few days. If you have worked in a corporation you know that evaluation, procurement, design, implementation, coordination of anything is a months long task. Maybe I am supposed to wait and get nothing done while something gets fixed. Or switch and get everything working now? Thought about going back to Intrepid, but what happens when I upgrade and one of the upgrades is the new ipv6-by-default-linux-kernel?

Now I am starting to feel like linux is not a mature platform yet despite all its other positives.

---

### Post by Brandon Williams on 2009-06-13
Is there something specific indicating that this is an IPv6 problem? Are you seeing IPv6 packets being sent? Or IPv6 connections being opened by your apps? Or AAAA DNS requests? If you tell us what you see that indicates the slowdown is related to IPv6, we might be able to offer helpful suggestestions.

---

### Post by christer74 on 2009-06-20
Hi!

I'm on a Aopen i965GMt-LA motheboard using 9.04 and have networking issues, maybe related to ipv6.

Problem is that networking freezes and ipv6 CANNOT be disabled in current 9.04 kernels. 
After reading some forums and bug lists it seems it's a bug in current 9.04 kernels (2.6.28-11 and -13, not ubuntu, the kernel itself). 

So what is happening?
I get about 5-10 minutes of network uptime. Thereafter "the big freeze" sets in. 
-Restart networking resolves the freeze and networking is ok for another 5-10 minutes.

I tried to manually updating to kernel 2.6.30 and problem is gone.
Also with 2.6.30 ipv6 could easily be removed (with above methods), and networking is rock solid again.

To me it seems that current 2.6.28-11 and -13 kernels have some networking issues.

Hopefully we will get a kernel update soon!
Also using 8.10 networking worked flawless.

//chris

---

