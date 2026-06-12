---
title: "Toshiba Satellite M35X-S149 - Wifi trouble - ping works, web gives lots of &quot;RX-ERR&quot;'s"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by Greg Alt on 2005-04-27
I installed Ubuntu 5.04 on my laptop, and I must say I was amazed at how easy and painless it was for everything except wifi.  I have a Toshiba Satellite M35X-S149 with built-in Atheros wifi, and I have it set up for dual-boot with Windows XP.

The short version is:  wifi works perfect under windows.  Under linux, I had some trouble getting it to work at all, but now it mostly works.  Ping works fine on all the sites I tried.  I've been able to download megs of packages with synaptic with no trouble.  But web surfing is very hit or miss -- most pages time out, but I can sometimes get them to load if I try several times in a row - though it's generally easier to reboot under windows, go to the webpage, save it, reboot to linux and then view it... :)

Using the pulldown menu, I opened the networking tool, and the problem appears to be a large number of "reception errors", clicking up at the rate of 2+ per second, with received packets coming in much slower.  Using netstat, it shows a large number of "RX-ERR" which I understand is the same thing as "reception error" in the other tool.  There are no transmission errors or encryption errors.

I've only tried this on my home wifi access point, and currently it is not connected to any other computers in my house, just 256Kb DSL to the internet.  The access point is an Actiontec GT701, configured to use 64bit WEP (10 hex digits)

I've scoured the net for anyone having similar problems with no luck -- one site claims to have the same laptop I have with wifi being autoconfigured with no problems:
[http://www.duluth.umn.edu/~salu0005/linux_installation.html](http://www.duluth.umn.edu/~salu0005/linux_installation.html)

I imagine the problem is that I made some mistake manually configuring wifi, though all the HOWTOs seem to think that once you get ping working, everything must be fine.  I also suspect that the reason autoconfiguration didn't work is because I'm using WEP, but I'm not sure how I could reset my wifi setup and try the autoconfiguration again after turning off WEP on my access point.

Any help would be greatly appreciated, including pointers to possible explanations for what RX-ERRs might mean and how one might go about narrowing down the problem.  Currently I seem to have hit a brick wall.

Thanks

---

