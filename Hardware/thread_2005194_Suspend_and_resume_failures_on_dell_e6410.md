---
title: "Suspend and resume failures on dell e6410"
date: 2012-06-17
forum: Hardware
---

### Post by Kristof A on 2012-06-17
Hi all,

I recently installed Xubuntu 12.04 (64 bit), coming from Ubuntu 10.04 (64 bit). I did a fresh install, no upgrade.  When using Ubuntu 10.04 I had no issues with suspend/resume when closing the laptop lid.  

Since being upgraded to Xubuntu 12.04 Suspend/resume sometimes works, sometimes it does not work.

When it does not work it is most often that 'wake up' / resume that fails however sometimes it is also suspend that fails (power light stays on and does not start flashing).

When suspend/resume does not work the screen stays black when I open the laptop lid and I don't get password prompt. Pressing keys, pressing power button does not help. The only thing I can do in that case is holding power button till laptop powers down and I have to restart.

Attached you can find 4 files:

suspend_fails_syslog.txt: Part of syslog that shows log in case suspend fails.
suspend_fails_pm-suspend.txt: Part of pm-suspend log that shows log in case suspend fails
resume-failed_syslog.txt.gz: Part of syslog that shows log in case resume fails.
resume-failed_pm-suspend.txt: Part of pm-suspend log that shows log in case resume fails.


Thanks in advance for giving your time!
Kristof

---

### Post by Toz on 2012-06-17
Hello and welcome to the forums.

I notice that you're using the nouveau driver for your nvidia card. Have you tried the proprietary driver?

---

### Post by Kristof A on 2012-06-17
When using Ubuntu 10.04 I indeed used the nvidia driver. My main reason to use the nouveau driver now was to be able to use xrandr to be able to easily switch between laptop only or external screen / projector. And because I would think issues with the nouveau driver would be more quickly solved...

But may be I should try out disper which supports nvidia driver...

The thing is that nothing in syslog or pm-suspend looks like it is a graphics card issue as far as I can tell?

---

### Post by Toz on 2012-06-17
Suspend generally works better with the proprietary drivers. You could try a deeper debug of the suspend process using the instructions [here]("https://wiki.ubuntu.com/DebuggingKernelSuspend"). It might yield a better clue as to where the hold up is in the process.

---

### Post by Kristof A on 2012-06-17
I followed your tip and installed the Nvidia proprietary driver (295.40). I did some work this afternoon and suspend/resumed several times and so far everything worked fine! So it might have been the Nouveau driver...  The battery life also seems better with the Nvidia driver. I'll give an update later next week after some more intense usage. Normally it failed to resume about 1 time out of 4 so I have good hope!

And I use disper now and still can use keyboard shortcuts to switch between external monitor, laptop screen only or projector. So I'm all happy for now :)

---

### Post by Toz on 2012-06-17
Glad to hear it works (hopefully). When you're satisfied that the issue is resolved, please make this thread as Solved for the Thread Tools link above.

---

### Post by Kristof A on 2012-06-20
From Sunday till today my laptop worked fine. Used it 8 hours a day, several times suspend/resume during the day and hibernating for the night.

But this afternoon I ran in the case again where the laptop did not properly suspend. When I closed the laptop lid the power light kept on and it did not give me the log-in screen when I opened the lid. The only thing I could do was power it down...

So suspending/hibernate is a lot more stable since using the Nvidia driver! But apparently there is still another issue... I compared logs again between succeeding suspend/wake up and failing suspend / wake up and noticed that following is missing from syslog when suspend fails:

Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070195] e1000e 0000:00:19.0: BAR 0: set to [mem 0xd9600000-0xd961ffff] (PCI address [0xd9600000-0xd961ffff])
Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070205] e1000e 0000:00:19.0: BAR 1: set to [mem 0xd9680000-0xd9680fff] (PCI address [0xd9680000-0xd9680fff])
Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070213] e1000e 0000:00:19.0: BAR 2: set to [io  0x8040-0x805f] (PCI address [0x8040-0x805f])
Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070243] e1000e 0000:00:19.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070276] e1000e 0000:00:19.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
Jun 20 09:00:25 BE1LXL-101081 kernel: [71177.070363] e1000e 0000:00:19.0: PME# disabled

These are also the last log lines of a succesful suspend, before wake-up.
In case suspend fails the last syslog lines (before reboot) are:

Jun 20 16:01:14 BE1LXL-101081 wpa_supplicant[1104]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jun 20 16:01:14 BE1LXL-101081 dbus[918]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun 20 16:01:15 BE1LXL-101081 NetworkManager[958]: <info> (wlan0): cleaning up...
Jun 20 16:01:15 BE1LXL-101081 NetworkManager[958]: <info> (wlan0): taking down device.
Jun 20 16:01:15 BE1LXL-101081 NetworkManager[958]: <info> (eth0): carrier now OFF (device state 10)
Jun 20 16:01:16 BE1LXL-101081 kernel: [91941.545559] usb 2-1.2: USB disconnect, device number 20
Jun 20 16:01:18 BE1LXL-101081 acpid: client 24452[0:0] has disconnected


Does this mean that the Ethernet driver did not properly suspend? Version of the driver (e1000e) is : Intel(R) PRO/1000 Network Driver - 1.5.1-k

---

### Post by Kristof A on 2012-06-20
My Ethernet controller is:


Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)

---

### Post by Toz on 2012-06-20
What is the kernel module it is using:
```
sudo lspci -vnn | grep -A20 -i ethernet
```
...should help to identify it.

You can try having pm-utils unload the module prior to suspend and reload during resume to see if helps. To do so, create a file called **/etc/pm/config.d/config**
```
gksudo leafpad /etc/pm/config.d/config
```
...with the following content:
```
SUSPEND_MODULES="<name_of_module>"
```
...replacing <name_of_module> with the actual module name for the e1000e card.

---

### Post by Kristof A on 2012-07-10
Since I had a memory upgrade more than a week ago I had no suspend/hibernate/resume problems anymore. So possibly my problems were also hardware related.

My previous post on the suspend failure of the network driver is probably wrong. I have seen situations in log file where I did not had all output as explained and still suspend/resume went fine.

But so switching to the Nvidia driver definitely helped improving suspend/hibernate/resume stability.

Thanks!

---

