---
title: "Wireless Card Suddenly Stopped"
date: 2010-05-05
forum: Hardware
---

### Post by j4collin on 2010-05-05
I have a Lenovo laptop with a Broadcom Corporation BCM4312 802.11b/g (rev 01) wireless card.  Up until yesterday, it was working fine with Lucid, but suddenly it failed.  I had to downgrade all the way to Jaunty in order to use it, and even upgrading from Jaunty to Karmic killed it.

Any ideas on where to start debugging?

---

### Post by Jim_in_Omaha on 2010-05-05
> **j4collin said:**
> I have a Lenovo laptop with a Broadcom Corporation BCM4312 802.11b/g (rev 01) wireless card.  Up until yesterday, it was working fine with Lucid, but suddenly it failed.  I had to downgrade all the way to Jaunty in order to use it, and even upgrading from Jaunty to Karmic killed it.

Any ideas on where to start debugging?

I'm running a Dell E6400 with 10.04 64bit on a USB drive since the internal is loaded with you know what for work. Since installing 10.04 I have been working to find a solution for the wireless dropping after a random time like many others.

During the trouble shooting something was updated or changed and it would not see the Broadcom 4322 when booting up. Did several suggestions. The one thing is it would say in the hardware drivers under Administration that the driver was active but not being used.

Well I was scoping out this site:
[http://97.95.43.80:10080/580/]("http://97.95.43.80:10080/580/")
and while poking on the suggested commands I noticed that my wireless light would come on and then it would lock onto the router.

After several reboots of testing to find the right one, I found this (and I should have remembered it from before)
sudo modprobe wl
would make the wifi light come on and it would lock in. So in a pursuit of random troubleshooting I noticed that site mentions the blacklisted drivers. I also then remembered working with that before. 

In the /etc/modprobe.d I found that the broadcom was blacklisted. I deleted that and rebooted, still no wifi. So I deleted the entry for ndiswrapper.conf and rebooted. It worked. 

I know I tried the ndiswrapper with a XP .inf file and it locked up. But that did not kill it. This all happened after I did a update yesterday.

Take a look at the article and perhaps it may help...

Heres the text from the article that helped me the most:

> This was getting annoying so today I googled for a solution and found that a lot of other folks were having this same issue. I found several 'solutions' but none of them worked for me. Finally I came upon this workaround that, for now, fixes the problem for me.

Blacklist ssb. Open a terminal and type this

echo blacklist ssb | sudo tee -a /etc/modprobe.d/blacklist.conf

The echo just outputs whatever is typed afterwards. The tee command with option -a appends the file in question by adding a line with the output given to it. The |, also known as the pipe, makes the tee command take the output from the echo command to work its magic with.

Now you need to edit rc.local and add the following code at the end.

From a terminal type this

gksudo gedit /etc/rc.local

and add this just before "exit 0"

modprobe wl

Test it

Restart Ubuntu and, hopefully, your wireless connection will be ready for you again.

Good luck.

---

### Post by asantos on 2010-07-27
Hi. This is my first post.
My wireless was working properly in my laptop dell insipiron with Lucid. Suddenly it stopped, after a routine upgrade. I use ubuntu in this laptop since version eight and something. So, before try the capital solution I decided to review the installed software. I figured out that a long time ago I installed third party hardware drivers for wireless, not officialy supported by ubuntu. I removed this hardware driver and after a reboot the wireless is working again.

I hope it can be useful for someone.

Anderson Santos

---

### Post by clconway on 2010-10-21
I had a similar problem with my BCM4312 card: on upgrade to linux-image-2.6.32.25-generic it stopped working altogether. Removing the "Broadcom STA" (proprietary) driver and installing the "Broadcom B43" (free) driver fixed it.

---

