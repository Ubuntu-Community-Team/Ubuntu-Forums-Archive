---
title: "Lenovo Thinkpad T400 wireless causes laptop to crash"
date: 2009-02-09
forum: Hardware
---

### Post by wirawan0 on 2009-02-09
Hi T400-ers,

I seem to have intermittent problem with the Thinkpad T400 wireless card. My card is Intel Wi-Fi 5100, which is working fine with iwlagn driver. I use Intrepid Ibex (Xubuntu) 8.10, the 64-bit variant. However I encountered quite a bit of troubling errors with this wireless card.

First of all, the driver could crash when I reboot or shutdown the computer. It seemed like when the network manager is asked to terminate, then the iwlagn driver crashes. I describe it more fully here: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/325426](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/325426) . Nobody has responded to this bug report yet, as of the time of writing. I spoke to another T400 owner (UK model, while mine is US model), he said he never had such kind of trouble.  (Here's his website for your reference: [http://www.ratman99uk.co.uk/lenovo-t400.html](http://www.ratman99uk.co.uk/lenovo-t400.html) ).

Last week and this week I found even more strange problem, related to the laptop itself crashing due to my playing around with the wireless card. Here's my hand-written log:

```

Date: 20090205

Was trying to disable/enable wireless, etc.
Don't remember what I did; perhaps Fn+F5 and other keys as well.
The computer hung by itself, and caps lock light blinking.
Had to do cold start.

After start, the wireless behaving strangely:
* before "ifconfig wlan0 up", the wireless light is off
* after "ifconfig wlan0 up", the wireless light is on
* after "ifconfig wlan0 down", the wireless light is off -- never like this   before! Wireless light is usually always on all the time unless we press the Fn+F5 key.
* connection to my wireless ESSID network is not working.
* But in Vista the wireless connection is fine!
* reboot with Linux doesn't help.

Final workaround:
* turn off the wireless switch (hard switch)
* turn on the wireless switch (hard switch)
* wireless worked again!

```

Then the second thing happened to me today, which is also bizzare.

```

Date: 20090209

Today I had another wireless error.
I brought the computer up from sleep (suspend). The wireless switch was off
all the time before this.
With hardware wireless switch turned OFF (my mistake!), I tried to turn on
the wireless interface (wlan0) using `ifup' program. When I did that, I
encountered the following error:

Error for wireless request "Set ESSID" (8B1A):
   SET filed on device wlan0 ; Resource temporarily unavailable.

...(DHCP program's message)

wmaster0: unknown hardware address type 801.

...(trying to get IP address, which is futile)

Before this returns to shell, I turned on the wireless switch then ^C the
program.

Then I ifdown the wlan0 and tried to ifup it again. Guess what happened?
The computer hung, the caps lock blinked. And the computer became useless
until I force it to shutdown by holding the power switch.

The error message in /var/log/kern.log is not that helpful; there is
nothing more than expected:

   Feb  9 10:00:56 wirawan1 kernel: [55618.265262] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
   Feb  9 10:00:56 wirawan1 kernel: [55618.265569] iwlagn: Radio disabled by HW RF Kill switch
   Feb  9 10:00:56 wirawan1 kernel: [55618.308027] iwlagn: WARNING: Requesting MAC access during RFKILL wakes up NIC
   Feb  9 10:00:56 wirawan1 kernel: [55618.312008] iwlagn: MAC is in deep sleep!
   Feb  9 10:00:56 wirawan1 kernel: [55618.359349] ADDRCONF(NETDEV_UP): wlan0: link is not ready
   Feb  9 10:00:56 wirawan1 kernel: [55618.372565] iwlagn: WARNING: Requesting MAC access during RFKILL wakes up NIC
   Feb  9 10:00:56 wirawan1 kernel: [55618.417280] wlan0: Failed to config new SSID to the low-level driver
   Feb  9 10:00:56 wirawan1 kernel: [55618.376539] iwlagn: MAC is in deep sleep!
   Feb  9 10:00:56 wirawan1 kernel: [55618.421577] wlan0: Failed to config new SSID to the low-level driver
   Feb  9 10:00:56 wirawan1 kernel: [55618.421579] wlan0: Failed to config new BSSID to the low-level driver
   Feb  9 10:00:56 wirawan1 kernel: [55618.421829] wlan0: authenticate with AP 00:14:6c:17:a2:98
   Feb  9 10:00:56 wirawan1 kernel: [55618.620149] wlan0: authenticate with AP 00:14:6c:17:a2:98
   Feb  9 10:00:56 wirawan1 kernel: [55618.651642] NET: Registered protocol family 17
   Feb  9 10:00:56 wirawan1 kernel: [55618.820553] wlan0: authenticate with AP 00:14:6c:17:a2:98
   Feb  9 10:00:57 wirawan1 kernel: [55619.020136] wlan0: authentication with AP 00:14:6c:17:a2:98 timed out



```

I retried the steps above to see if I can reproduce the same crash.
This did not happen again.
This makes me wonder if it is a sign of defective hardware.

If anyone has comment, please let me know. This is troublesome.

Wirawan

---

### Post by Shankha on 2009-02-17
I have the same configuration, face the same problems, and I have also noticed an additional strange problem. Sometimes the wireless driver stops responding, but the machine still works. However something happens to the keyboard driver: and if I press a key once, after a delay of about 2 seconds, it repeats at least 500 times on the screen. 

It always happens only when the wireless stops working. I haven't been able to reproduce it consistently. Next time it happens, I am going to store the system state and upload it here.

---

### Post by lionstone on 2009-02-20
Hi- I ran into a bit of a snaffu here-  I am running Ubuntu 8.10 64-bit on  a lenovo thinkpad t400. I just installed updates for the first time in a few weeks, rebooted, and suddenly my computer has suddenly lost networking. I only have wireless here so testing ethernet is unfortuantely not an option.

i don't know much about wireless commandline programs but 'lo' was the only parameter appearing when i tried tabbing after typing ifup. Anyone have any idea what this update this was related to? (When I tried running it, it said it was already configured. ) I am almost 100% certain this was related to one of the recent updates. I have not had a single problem with Ubuntu wireless on this machine before now after running it fine since the fall.

All help appreciated. Thanks!

---

### Post by wirawan0 on 2009-02-20
Dear shanka and lionstone,

I'm glad that somebody else experiences a similar kind of problem; so it is not isolated to my own laptop. It is quite weird that only certain T400 laptops have it. Maybe the kind of configuration, the specific version of the motherboard, etc. affect the bug. If you have some more log (or system state like Shanka is saying) please post it here!

A workaround to this problem would be to "rmmod iwlagn" before the /etc/rc0.d/S20sendsigs shutdown sequence. But this is a very dirty hack.

I will post something else when I have time fooling around with this problem again.

On Shanka's comment regarding keyboard: I did encounter similar problem, too. I use manual ifup/ifdown to control my network. That is fine, except that when I ifdown the interface, the computer seems to be "hung" for 1 sec or so. And if I type something during that time, then one of the letter would be repeated indefinitely until I pressed something else. So indeed there is some bad interaction between network and keyboard driver, which I cannot fully explain.

Wirawan

---

### Post by wirawan0 on 2009-03-11
Lionstone: Do you still not have networking? Did you see the hardware in lspci? Is there something suspicious in dmesg output, or /var/log/kern.log? Please post relevant portions if you suspect something with the wireless or ethernet.

Wirawan

---

### Post by andreag on 2009-06-14
Exactly same problem with Latitude E6400, with 5300 Intel wireless card.

---

### Post by SaintDanBert on 2010-09-06
My hardware is the Intel 4965AGN installed to a Lenovo Thinkpad X61-tablet.

The driver, **iwlagn** crashes for me as well.  I do not have the kernel and driver skills to debug this, but it seems that if something wants to "suspend" this driver -- sometimes screen saver, low-power sleep, low-power hibernate, operator requested sleep, operator requested hibernate, close lid sleep, etc. -- the driver will routinely crash.

Under Ubuntu Jaunty (v9.04) I have iwlagn v1.3.27-ks and things are stable.

Under Ubuntu Lucid (v10.04) I have iwlagn v1.3.27-ks [highlight]-- same edition --[/highlight] and the crash happens several times during each eight hour shift.

Merci d'avance,
~~~ 0;-Dan

---

