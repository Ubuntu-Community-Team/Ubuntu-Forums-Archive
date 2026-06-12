---
title: "Fujitsu Siemens S7020 wifi and ShutDown problem"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by Zeratul7 on 2006-06-29
Hi,

I just installed Dapper on my Fujitsu Siemens S7020 and I am having these two problems.

1. Wifi problem:
I find can find all networks but I cannot connect to them. I tried to connect with ubuntu's standard network manager and with wifi radar and neither of them worked. In Breezy everything worked fine. Wifi router model is Linksys WRT54G with DD-WRT software. When I connect to this router via wireline port then network works.

2. Shut down problem:
When I use the "Shut Down" button in gnome, it shuts down all processes (no failures), monitor goes black, but still cpu is working. I didn't have either of these problems in Breezy.

I really do not want to go back to Windows or Breezy so any help would be appreciated.

---

### Post by Zeratul7 on 2006-07-02
Come on guys, don't make me swith my distro :( 
I really like Ubuntu.

---

### Post by Eversmann on 2006-07-05
Maybe nobody replied because they don't know, or just searching on the forum you can get a solution.

You didn't post the hardware you use on the laptop, for example, what card are you trying to run. The ap isn't really a helpful information from a start.

Be really sure the wifi is enabled. In fujitsu-siemens laptop, looks like the wifi is enabled by software. Try Ndiswrapper and post more details about your problem.

---

### Post by Zeratul7 on 2006-07-05
Wireless card is Intel 2200BG

* Yes, my Wifi is enabled, otherwise it doesn't show available networks. Same network works when I boot windows (and also works with Breesy).

BTW, how can I try to connect to a Wifi network via command line in order to view some errors?

---

### Post by ThrobbingBrain66 on 2006-07-05
The shutdown issue was already reported as a bug back before Dapper was released.

I have the same problem, but no solution as of yet...

---

### Post by cracker on 2006-07-05
What type of encryption does your network use? Make sure you configure that part of it, and enter the correct passkey/network keys.

---

### Post by Zeratul7 on 2006-07-06
I tried with WEP and without any encription at all and it didn't work either way.

---

### Post by Eversmann on 2006-07-06
I had a problem on my amilo laptop that i could browse networks, but couldn't associate to them.

The thing was i had a partially enabled wifi on the laptop. Having an intel wifi card things should be easier.

Actually with that information i don't know how to help ya. Post dmesg result here, do some more test..... we need clues ;-)

---

### Post by Zeratul7 on 2006-07-19
[4294691.862000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294691.862000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294691.862000] Warning: PCI driver ipw2200 has a struct device_driver shutdown  method, please update!

I think this should be the problem?
How can this be fixed?

---

