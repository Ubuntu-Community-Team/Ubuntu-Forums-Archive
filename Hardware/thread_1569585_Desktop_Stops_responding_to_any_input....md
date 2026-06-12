---
title: "Desktop Stops responding to any input..."
date: 2010-09-06
forum: Hardware
---

### Post by Kushal S. Pandya on 2010-09-06
Hello everyone,

I'm using Acer Aspire 4930 laptop, and currently using Ubuntu 10.04 with Kernel 2.6.32-24 Generic. Everything worked fine before last Kernel update. After I updated my laptop on 3-Sept-2010 which also purposed a Kernel update, it now sometimes stops working and refuses to respond any of the inputs.
               The problem occurs unpredictably and I all can do to recover my desktop is by turning off the laptop switch. The desktop doesn't freezes like any application (getting Gray when stops responding), the only symptom I see is that my laptop's Caps-lock indicator LED starts blinking and mouse pointer doesn't move at all and also keyboard stops working. I guess the problem is with the drivers. Please help me out...:confused:

---

### Post by SriNarayanan on 2010-10-20
**Freese - blinking caps and scroll lock - acpi**  			 			 			 		   		 		 		Sony Vaio EB 16 FG - running ubuntu 10.10  froze while resuming from dimmed screen with blinking scroll lock and  caps log LED.

The scenario was this :-
I just downloaded the acpi using synaptic package manager.
Then installed laptop mode tool using synaptic.

*cat* /proc/sys/vm/laptop_mode
0

Means its not yet enabled.

But decided to remove it .(read  drive spin up and down is not good for HDD)

Had left the laptop for some time , it dimmed screen . When I resumed it froze.
No mouse movement.only blinking caps and scroll.

Just wondering if acpi is the culprit,since haven't seen this behaviour before and it happened after removing  laptop mode tools

It happened again , this time while playing a movie on totum .
I was running top on another terminal just to see cpu usage .

Now remove acpi , let me see if it happens again after the removal.

Also I am using a USB mouse , may be it has something to do ?

---

### Post by Kushal S. Pandya on 2010-10-20
Well, I had this problem only due to Chrome browser, and my computer used to freeze only if I start the Chrome, this was the case with Lucid, and only if Chrome is setup to sync all my browsing data with my Google account, otherwise it worked fine.

But, I guess that in your problem, it has something to do with PCI drivers, not USB mouse, as you suspected. Have you made clean uninstall of laptop-mode-tools package? Also after you uninstall it or any of its left configuration from synaptic. Run following commands.

```

sudo update-grub2
sudo update-initramfs -u

```

Also have look at these threads...

[http://ubuntuforums.org/showthread.php?t=1478787]("http://ubuntuforums.org/showthread.php?t=1478787")
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765")

---

### Post by SriNarayanan on 2010-10-21
> **Kushal S. Pandya said:**
> Well, I had this problem only due to Chrome browser, and my computer used to freeze only if I start the Chrome, this was the case with Lucid, and only if Chrome is setup to sync all my browsing data with my Google account, otherwise it worked fine.

But, I guess that in your problem, it has something to do with PCI drivers, not USB mouse, as you suspected. Have you made clean uninstall of laptop-mode-tools package? Also after you uninstall it or any of its left configuration from synaptic. Run following commands.

```

sudo update-grub2
sudo update-initramfs -u

```Also have look at these threads...

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)


As of now , after the removal of acpi the problem has not reoccured .
I am yet to try the thing u mentioned.
Will do that if it happens again.

---

### Post by SriNarayanan on 2010-10-22
> **SriNarayanan said:**
> As of now , after the removal of acpi the problem has not reoccured .
I am yet to try the thing u mentioned.
Will do that if it happens again.
Sorry folks , just today had another kernel panic , also just now came to know that this system behaviour is called kernel panic

see if this help

[http://ubuntuforums.org/showthread.php?t=1603231](http://ubuntuforums.org/showthread.php?t=1603231)

---

