---
title: "Problem Installing Ubuntu Server 18.04.4 on a Super Boot Drive"
date: 2020-04-14
forum: Hardware
---

### Post by odd135 on 2020-04-14
The hardware in question is a MyDigital SSD Super Boot Drive plugged into an M.2 to SATA adapter. Installation fails with the most recent message being "updating initramfs configuration." The message claims that the failure is because of a bug and includes a log report, but I couldn't figure out how to get it off of the machine in order to post it here. The steps to recreate this error:
[LIST=1]
[*]Fully wipe the aforesaid SSD 
[*]Create a USB installation drive for Ubuntu Server 18.xx.x using rufus 
[*]Press enter/select all default options, skip extra features, enter computer name/username/password 
[*]Start installation 
[/LIST]
Behavior after my "failed" installation failure is very odd; I am able to boot into Ubuntu Server on the SSD, but not log in. Also, after about a minute, whatever is on the screen resets to the original login prompt.

Now, a list of relevant but confusing facts:
[LIST]
[*]After attempting an installation with this SSD, a second attempt using the same hardware, same USB installer, and same version of Ubuntu with a different hard drive results in a successful installation 
[*]Because the computer in question has a wired internet connection, I'm able to send a bug report with a log file, however, 
[*]I originally attempted this about a year ago (with Ubuntu Server 18.04.2), encountered the same bug, and sent a bug report through the installer then. The fact that I'm encountering the same bug now indicates to me that this is a problem with the hardware, and not a bug in need of fixing 
[*]The same SSD on the same hardware ran an 18.xx.x version of Ubuntu Desktop perfectly well. In fact, I'm going to be switching back to this for the time being, even though I'd rather use Ubuntu Server, since I don't need a gui for my purposes 
[/LIST]

Any help would be appreciated. If it seems that the paring of Ubuntu Server and my Super Boot Drive was never meant to be, then I suppose that I'll stick this particular SSD in the incompatible hardware sticky and move on.

---

