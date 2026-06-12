---
title: "kernel update, slow boot"
date: 2009-12-16
forum: Hardware
---

### Post by pokeyflan on 2009-12-16
Hello All:

Since my last update, I'm experiencing a very, very slow boot up (about 15 minutes).

I have 8.04LTS on a Compaq Presario V3000.
I have tried editing GRUB from 'ro quiet splash' to 'ro'

I also read that the 2.6.24 kernels have drivers built-in for my wifi card (Intel 3945ABG) & created /etc/modprobe.d/iwl3945 with contents of:
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1

Then deleted file /etc/modprobe.d/ipw3945 & rebooted.
This didn't solve the problem -- still slow.

Once the computer boots, everything works fine.
Any suggestions?
(& thanks in advance!)

--chris

---

### Post by SteveDee on 2009-12-16
Have you tried looking at the messages log for clues?

You can view the log directly at; /var/log/messages

...or (on 9.10) via System > Administrator > Log File Viewer > messages

---

### Post by pokeyflan on 2009-12-17
System messages from my most current log-on:

[IMG]/Desktop/screenshot.png[/IMG]

--chris

---

### Post by pokeyflan on 2009-12-17
Let me try that again....

---

### Post by SteveDee on 2009-12-17
> **pokeyflan said:**
> Let me try that again....

OK, the first thing for me to say is that the info in this log is as bewildering to me as it probably is to you. However, it is worth focussing in on the lines where the system appears to be burning time.

For example, most of the early tasks are completed within 36 seconds, then you hit:-

```
Dec 16 08:00:51 pokey-laptop pppd[12167]: Timeout waiting for PADO packets
```

Your system has 10 retries (at 65 second intervals) before giving up.
I typed the phrase; "Timeout waiting for PADO packets" into IXQUICK and it found several pages of info. I suggest you start by doing the same and see if any of this is relevant to your configuration.

pppd is the Point to Point Protocol Daemon, and it looks like your system is having problems connecting to the network/internet. This is probably due to an issue with wireless/driver/kernel/take-your-pick.

I'm having a wireless problem on 9.10 with kernel 2.6.31-16 on my Dell Inspiron 500, in that I may have to reboot 4 or 5 times before I get lucky and my wifi works. My work-around has been to switch back to the previous kernel 2.6.31-15. I'll just wait for the next kernel update and see if its any better...lifes too short to worry about every little thing!

Hope this helps, good luck.

---

### Post by JBAlaska on 2009-12-17
Since the Intel 3945ABG works "outta the box" in Karmic...back up your /home and do a clean install of 9.10..should work a treat.

---

### Post by pokeyflan on 2009-12-17
> **JBAlaska said:**
> Since the Intel 3945ABG works "outta the box" in Karmic...back up your /home and do a clean install of 9.10..should work a treat.

Actually, I've been considering that... but was just hoping there might be a way to revive my current set-up before a re/new install.

And Steve -- yes I am "bewildered" by all this code! But i do think it's got something to do with the wifi driver-kernel interaction. Probably far above my abilities for sorting out!

Thanks, Folks............chris

---

### Post by SteveDee on 2009-12-18
> **pokeyflan said:**
> Actually, I've been considering that... but was just hoping there might be a way to revive my current set-up before a re/new install.

And Steve -- yes I am "bewildered" by all this code! But i do think it's got something to do with the wifi driver-kernel interaction. Probably far above my abilities for sorting out!

Thanks, Folks............chris

If your last update (which left you with this problem) included a kernel update, I'd suggest you try booting with the previous version.

The easiest way to do this depends on whether the Grub menu is accessible when you boot. If it is then you simply select the previous version.

If your system does not show the Grub menu (because the display/timeout is set to 0) you could install the Startup Manager and then change the default kernel from there (e.g. menu System > Administration > Startup-Manager > Boot Options).

It looks like you are deliberately running an LTS (very wise in my opinion) so its worth trying to put this problem right, rather than switch to Karmic which currently comes with its own set of problems. If you want to upgrade to a more up-to-date and stable version, I'd recommend 9.04 at this point in time.

---

