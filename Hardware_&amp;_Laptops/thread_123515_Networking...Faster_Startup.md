---
title: "Networking...Faster Startup?"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by wsmoser2004 on 2006-01-30
I have Kubuntu installed on a laptop, which means that sometimes I am not connected to any network at all (wireless or wired).  However, when I start the laptop into Kubuntu, if I am not connected to a wired network, the laptop takes about a minute longer to start up.  I am guessing that this has something to do with the DHCP timeout.  (I'm new to Linux, so that's a guess for me.)

I searched these forums, and found out about something called **ifplugd**, and that sounded great!  So I installed this package...with limited success.  Before **ifplugd**, startup would stop for one minute on **Waiting for network interface to come up...**; now with **ifplugd**, it skips right past **Waiting for network interface to come up...** but waits for a minute on **Configuring network interfaces...**.  (Note that this is only when the laptop is unplugged from the network.)  As the laptop starts up, I see a line that says **Starting Network Interface Plugging Daemon**, so I'm guessing that **ifplugd** is running.  Also, I can use **ifplugstatus** on the command line and it will tell me whether or not eth0 (the wired interface) is unplugged or not (and the status that it reports is correct).

Also, I was under the impression that **ifplugd** would automatically configure the network interface if I plugged in a network cable after the laptop was up and running.  It does not appear to do that...I've waited 30 seconds or so after plugging in the network cable, and I still do not seem to be able to use the Internet.  I have to manually run **dhclient** to gain connectivity.

I think the problem may just be that I do not know how to set up **ifplugd** correctly.  So any help there would be appreciated...

Also....(and this may be a stretch) my friend who runs Gentoo helped me set up my wireless with **wpa_supplicant**.  Now I have a script that I can click on that will automatically bring up my wireless card and connect to my school's network.  Is there any way that **ifplugd** can work with wireless so that as soon as I turn the wireless switch on, it will connect to the network?  Starting this script isn't difficult, but it would be handy if I could connect automatically.

Thanks!

---

### Post by wsmoser2004 on 2006-02-03
OK, a little update...

Startup pauses on EITHER **Waiting for network interface to come up...** or **Configuring network interfaces...** regardless of whether the laptop is plugged in to the network.  The amount of time it waits is considerably shorter when it is plugged in, but it is still 7-8 seconds.  

Any ideas?

---

