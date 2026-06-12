---
title: "Avahi-Daemon errors; please help!"
date: 2008-08-05
forum: General Help
---

### Post by runneri.q on 2008-08-05
I have installed ubuntu hardy heron on my pc recently and have not been able to get the internet working. I have an awlh3025 by airlink. I put my settings in, i.e. passphrase, type of security (WPA), but it still doesn't work. Also after these attempts I shut my computer off and the next time I turn it back on again, it didn't start correctly and while booting it stopped and said:
"Starting Avahi mDNS/DNS-SD daemon avahi-daemon [FAIL]
Timeout reached while waiting for return value
Could not receive return value from daemon process."
Eventually it skips this and completes booting, however after I enter my username and password, and am logging in, a window pops up saying,
"There was an error starting the GNOME setting daemon

Some things such as themes, sounds, or background settings may not work correctly.

The last error was.

Did not receive a reply possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply. The reply timeout expired, or the network connection was broken.

GNOME will still try to restart the settings daemon next time you log on."

if any one could help it would be greatly appreciated...

---

### Post by lionel47 on 2008-08-05
Your card uses the Ralink chipset.  Follow [this thread]("http://ubuntuforums.org/showthread.php?t=400236") to install and use the serialmonkey drivers.  It should work.  Anyway, it worked for me.

---

### Post by runneri.q on 2008-08-07
PROBLEM SOLVED!!!! NDISwrapper was the trick... all i had to do was get internet access through an ethernet cable go to synaptic package manager, go to search and type in NDISwrapper and mark ndistgtk for installation, then once its installed go to system, administration, and windows wireless driver option at the bottom, install an xp driver for you pci wlan card, and then use the wireless network manager in the right corner... please ask any questions if need

---

### Post by 80aless on 2008-12-22
Hi, Thanks, I will try this as soon as I will have a connection. But my problem is that I cannot log in at all. If I press Ctrl+Alt+Del it hangs at "Stopping firewall ufw ...", then I can only force the computer to shut down. What I can do is to log in in the 2.6.27-7 kernel and not in the default 2.6.27-9 ( I do not know what the difference is). I also have problems with internet (a month ago it worked,the drivers were installed with ndiswrapper,now I cannot enable wireless with the nm-applet). A guy here posts a patch, I will try it in these days:
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/116984](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/116984)

Regards
ale

---

