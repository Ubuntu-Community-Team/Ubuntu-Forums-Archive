---
title: "Battery Drains While Laptop Off - HP Pavillion g6"
date: 2012-09-03
forum: Hardware
---

### Post by mark bower on 2012-09-03
HP Pavillion g6 notebook - brand new

I have tried everything below and still get approximately 15%/24hr battery drain with the laptop turned off via shutdown - condition for extended non-use.  I believe I have succeeded in shutting down both wifi and wake-on-lan.  If true, then there is some other demand on the battery.

1) HP technical support @ 800 474.6836 was no help - said never heard of the drain problem for off condition
2) BIOS settings for Wake On Lan(WOL) do not exist
3) A/C disconnected, R&R battery
4) Shutdown via:  press Restart, press ESC @ BIOS msg, press Off Btn
5) Disabled wifi from the tool tray
6) /etc/init.d/halt changed line "halt -d -f $netdown $poweroff $hddown" to read " halt -d -f -i $netdown $hddown"
7) ethtool shows "Wake-on: g".   in /etc/network/interfaces the "interfaces" file showed only the following two lines:
	auto lo	
	iface lo inet loopback
i added to the "interfaces file" the line "up ethtool -s eth0 wol d" ; the ubuntu documentation in link below suggests  "d" should disable WOL:

	[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

8 "wol" is seen in the following file & applicable lines

	/etc/network/interfaces:  up ethtool -s eth0 wol d  (i added this line)
	/etc/network/interfaces~:  up ethtool -s eth0 wol d (this line was already there)
	/etc/network/if-up.d/ethtool:  there are 3 interesting lines, what do they mean?
		# WOL has an optional pass-key
		set -- $IF_ETHERNET_WOL		
		SETTINGS = "$SETTINGS${1:+ wol $1}${2:+ sopass $2}" . 1: + wol
9) Entered directly at the cmd line:  "ethtool -s eth0 wol d".  **Finally**, "ethtool eth0" shows wol to be disabled with comment "Cannot get wake-on-lan settings:  Operation not permitted".  The comment is the same after reboot, ie "Cannot get wake-on-lan . . .".
10) Also ran "ifconfig eth0 down"

Is there something else I should be trying to shut down, and how?

mark bower

---

### Post by ahallubuntu on 2012-09-03
Are you talking about Standby or Shut Down?  When Shut Down, the power is OFF, everything the operating system can control is OFF.  You need not try to shut down anything in Ubuntu.

If you mean Standby (where the computer resumes quickly, without rebooting), then understand that some power drain is normal because the laptop is still using some power in Standby.

Even when completely OFF, the battery will lose some charge over time but 15% a day sounds excessive.  Is this an old laptop?  Laptop batteries do degrade over time, and after a couple of years a battery might not be able to hold its full charge.

Otherwise, you could be talking about a design defect in the laptop.  With an HP laptop, that would not completely surprise me.

---

### Post by mark bower on 2012-09-03
I edited my first post to indicate the HP Pavillion g6 is a brand new computer and off condition is via shutdown.  The battery out of the computer remains at 100% for at least a week.  The drain problem with computer off is reported by many, but none of the presumed solutions have worked for me.  In almost every case reported on line, when Windows 7 or such is used vs the linux os, batteries do not drain.  Persons have done a direct contrast between the two systems and thus the problem seems to lie in the linux kernel.

mark bower

---

### Post by mark bower on 2012-09-03
Following yet another suggestion I did the following:

1) "cat /sys/class/net/eth0/device/power/wakeup" and it says enabled.
2) add to /etc/rc.local the line "/usr/sbin/ethtool -s eth0 wol d"
3) reboot
4) run line 1) again and it still says enabled.

mark bower

---

### Post by mark bower on 2012-09-06
yet another suggestion that fails to work.

1) add to "/etc/rc.local" the following line: "/sbin/ethtool -s eth0 wol d".  (this assumes ethtool is installed at /sbin)
2) then check for diabling with the following: "cat /sys/class/net/eth0/device/power/wakeup.  it should say disabled; but it says "enabled".

surely there is something that can be disabled to stop the drain.  i am getting close to the point of temporarily putting XP on the laptop just to prove that it is a linux issue as others have stated.

mark bower

---

### Post by mark bower on 2012-09-08
o.k., I could not get Win XP to install.  So I replaced Linux Mint on the laptop with Ubu 12.04 LTS, modified by installing Gnome Classic(not sure if this is necessary) and then Mate 1.2(this essentially returns the DE to what I liked in 10.10 - can't stand Unity).

With 12.04 LTS on the laptop, the battery drains as before when the laptop is shutdown.

Surely there is something that can be disabled to stop the battery drain?

mark bower

---

### Post by mark bower on 2012-09-11
bumping for a hoped for solution.

---

### Post by afulldeck on 2012-09-11
I'm sitting here with my engineering hat on. Let's restart for a second: 
 
a) battery out of the machine it still remains charge? If so, how are you checking that it is 100% charge a voltmeter? 
 
b) If you truly want to prove it a linux problem, you can do it the old fashion way. You could jumper the battery to laptop and measure the current drain. Then you know either (a) its hardware and there is a short (or a failed component) on the output of the charging circuit for the battery. You would have to pull the charging circuit and send it back. Or if you had a heat sensor you could probably trace it. If a was negative then its  (b) software where something isn't turned off. And Ubuntu has a problem.

---

### Post by mark bower on 2012-09-11
thanks for the response.  some comments: it sounds like you may not be familiar with laptop batteries, or at least the battery on the model i have? there are 8 contacts placed in between fins.  while not impossible to make contact with them with the battery outside of the computer, it would be highly impractical to parallel all of them to the computer at the same time, would really need some mating connectors.  i verified that the battery does not lose charge out side of the laptop by 1st fully charging the battery as seen by the 100% battery icon, removing the battery for a week or so, then replacing the battery and observing that i have, or nearly have, 100% charge - again according to the icon.  

others have reported that the Ubu kernel is the problem and that it was resolved when they boot windows.  however, i am conducting this thread in the hopes that some guru knows a work around or a tweak for the kernel.  a final thot, i suppose i could zero the HD, then turn the computer on and see what happens, say after a few dys.  then load Ubu back on and look at the batt voltage.  however, this also seems a bit impractical.  bottom line, i need a fix for using linux.

mark bower

---

### Post by mark bower on 2012-09-13
bumping for a hoped for solution.

---

### Post by davidryderuk on 2012-09-14
Hi,
You said in point 9 that you ran:
```
ethtool -s eth0 wol d
```

and the terminal reported:

```
Cannot get current wake-on-lan settings: Operation not permitted
  not setting wol
```

Did you use sudo, to get the necessary privilidges?

```
sudo ethtool -s eth0 wol d
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'm not sure how you could run the script as root every time you boot, or whether that would actually be necessary. Maybe try adding the command to rc.local?

[http://ubuntuforums.org/showthread.php?t=1822137](http://ubuntuforums.org/showthread.php?t=1822137)

---

### Post by davidryderuk on 2012-09-14
Sorry, I just realised I read your first post wrong, and it was the 'ethtool eth0' command which threw up the permission error.Did you use sudo to run the 'ethtool -s eth0 wol d' command? Could you post the result of the 'ethtool eth0' command after using sudo?

---

### Post by mark bower on 2012-09-14
I am not totally sure of your question?  I put the cmd "ethtool -s eth0 wol d" in /etc/rc.local by first gaining root privileges with sudo su, then a gedit of the rc.local file.  Then running "ethool eth0" I get the following:

Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
Cannot get link status: Operation not permitted

I now put Ubuntu 12.04 LTS(overlaid with Gnome classic and Mate 1.2) on the laptop, modified /etc/rc.local with the WOL line, and get the same message as above.  This indicates WOL is disabled?  

Drain for this setup with laptop off & Ubu 12.04 is approximately 8%/24hr.

mark bower

---

### Post by mark bower on 2012-09-17
I am now conducting maybe the ultimate test:  
I have "zeroed" the HD and thus no OS is on the laptop.  I will let the laptop sit for 10 dys.  So with no OS on the laptop, I would expect the battery to drain only 2% if the OS is at fault.  But if the battery drains excessively with no OS present, then the hardware is at fault.  

Recall that the laptop loses about 8% per day when 12.04 is on the laptop. 

At the end of the 10 dy period, I will install 12.04 LTS and after installation, see what is left of the battery.  If by chance the laptop does not boot on the battery, then of course this means the battery drain exceeded the estimated 80% and is due solely to the Pavillion g6 hardware/firmware.  If, on the other hand, 12.04 installs, then assuming that it takes maybe 30% of battery capacity to install 12.04, I would expect the battery might have maybe 68% (100 -2 -30) of capacity remaining.  Will report back.

BTW I tried to install Win XP again with the "zeroed" HD and it balked again.

---

### Post by mark bower on 2012-09-25
I completed an 8-3/4 day period of laptop off, no OS on the laptop, and battery charged to 100%.  After 1.8 hours of fiddling with various install attempts, I finally got 12.04 LTS 32 bit installed again and noted battery remaining at 28%.   Based on previously reported observations when Ubuntu is on board, the computer battery would be nearly drained after 8 & 3/4 days with no activity except booting to observe battery drain.  By contrast, the 28% capacity still remaining after intensive use in OS install attempts on a zeroed HD, conclusively(almost) suggests that it is the OS that causes the draining, not a HP hardware issue.

So just to be consistent and sure, I am now testing battery loss versus time with 12.04 LTS 32 bit on board and laptop off.  I will check remaining percent capacity from day to day, and when the battery drops below 28% I will terminate and report back.

It still looks like a solution other than disabling WOL is needed to solve the Ubuntu drain problem.

---

### Post by meditatingfrog on 2012-09-25
The problem could be the BIOS.  It could have been specifically designed to work well with Windows and not well with Linux.

Since the BIOS isn't open source, there really isn't a way to prove it with 100% certainty (and since i don't know anybody that can read source code), but i can say that i had battery issues with a toshiba laptop, and after a lot of struggle, i have come to the conclusion that it is likely a BIOS problem, since nobody else had the problems i had.  

FWIW, i asked myself what kinds of laptops Linux developers use, and it appears to not be toshiba.

---

### Post by mark bower on 2012-09-25
@ meditatingfrog
thanks for your response.  i believe you are the first to respond on having experienced this type of problem.  depending on how much of the thread you plowed thru, i was disappointed that i could not get WinXP to install in order to compare to Ubuntu, especially since some have reported that the problem went away when they used Win7 and such.  At any rate, if my laptop goes from 100% to below 28% in 8-9 dys with Ubuntu on it, that will be conclusive that the OS is involved, and as you state, maybe an "unfriendly" interaction with the BIOS.

---

### Post by mark bower on 2012-10-11
Following is a summary of tests I have done to date.  In case 4) I show a 2.5% loss per 24hr. This is tolerable, but still not desirable.  It would seem the original drain problem may have been caused by Mate 1.2 on top of Gnome Classic?

```

				Test
_Condition	        	Period	                Drain(%)/24hr_
1)Batt removed                  7dys			0
2)No OS on computer		8-3/4dys		0  
3)OS+Gnome			~ 4dys		 	17
Classic+Mate 1.2#
4)OS+Gnome Classic		9dys			2.3 
```

Comments:
2)This is an assumed 0% drain.  The HD was "zeroed" so no OS.  After 8-1/2 days, I tried to get 64bit 12.04LTS to installed, but had trouble.  So installed 32bit 12.04LTS.  The total time of "monkeying around" with the laptop on was 1.8 hours; during this time I assume intensive use based on the fact that a significant portion of the 1.8 hrs the HD was running and that installing makes heavy demands.  When 12.04 32bit booted at 1.8 hours, the battery indicator indicated 28% remaining.

3)For this condition "ethtool -s eth0 wol d"  was added to /etc/rc.local so that terminal command "ethtool eth0" states: "Cannot get wake-on-lan settings:  Operation not permitted".

4)For this condition "ethtool -s eth0 wol d" was added as in 3) with same resultant msg.

---

### Post by alfa9 on 2012-12-05
[FONT="Courier New"]I'm sorry for reviving this thread. But I have a similar issue and didn't want to start a new one.

I have a Dv7000 and my battery used to last +4 hours with Windows  7 Ultimate SP1, now I installed Ubuntu 12.04 four months ago, and I have noticed it has done something to my battery. It now lasts 40 minutes, maybe an hour. I had Win7 for 3 years, and haven't changed anything in the hardware (ATI 512MB, 4 GB, 360GB HDD). I used to leave my laptop on with W7 when simulating, downloading. But now with Ubuntu I always turn it off since I had not found the simulation software until last week (had to get a new license). And I always unplug the mouse, external HDD, etc...

It's really disturbing the fact that I might have to buy a new battery just for testing U12.04 for 4 months.

Have you found any solution to this problem at all??[/FONT]

---

### Post by sourav_d on 2012-12-13
Hi, just visited this thread. I have also experienced the exact same problem of battery drain while laptop was shutdown. My laptop was a HP Mini 110. I initially had WinXP installer in it and didn't experience any such problem. Only after switching to Ubuntu full time I started noticing battery drain. There's been some discussions regarding this and as I vaguely remember someone suggested there's a patch that fixed it in Debian kernels. But the issue recurred and was reopened. Nothing conclusive came out of this thread (probably it still appears in Google search). I posted once in this very forum stating the problem, but no good reply came. Found out that some hacks exist to remedy the problem - like forced shutdown after restarting the laptop or removing the battery after shutdown and putting it back. 

Being utterly frustrated with this battery problem (I travel a lot), I switched to other distros, like Mint, Fedora, Debian (and even Bodhi) - but all had the same problem. The problem, strangely did not occur on one of my old Acer laptop though, so figured its the HP hardware. 

Last month switched to Windows 8 from Ubuntu 12.04 and I don't have that battery drain issue any more.

---

### Post by Giveingitago on 2012-12-14
> **mark bower said:**
> @ meditatingfrog
thanks for your response.  i believe you are the first to respond on having experienced this type of problem.  depending on how much of the thread you plowed thru, i was disappointed that i could not get WinXP to install in order to compare to Ubuntu, especially since some have reported that the problem went away when they used Win7 and such.  At any rate, if my laptop goes from 100% to below 28% in 8-9 dys with Ubuntu on it, that will be conclusive that the OS is involved, and as you state, maybe an "unfriendly" interaction with the BIOS.

Hi Mark,
I have the same problem on my new (5 week old) HP ENVY 6 1006sa Sleekbook. I've been investigating and trying to contribute to this thread:

[http://ubuntuforums.org/showthread.php?t=2072741](http://ubuntuforums.org/showthread.php?t=2072741)

While my Sleekbook is in warranty I'm dual booting Win 7 and Ubuntu 12.10 (Unity desktop). I've done the Win 7 and Ubuntu comparison, Win7: 4% per 24hrs , ubuntu: ~17% per 24hrs. I'm still investigating, will cross link if I find anything. 

Dave

---

### Post by mark bower on 2013-01-10
@sourav_d
your results from switching from 12.04 to Win 8 seems rather conclusive that 12.04(linux kernel?) is the problem.

@ Giveingitago et al
i believe i am now doing the utltimate test:  1)connect to AC power, 2)install and charge battery to 100%, 3) remove battery, 4)zero the HD so no operating system, 5)turn off and remove AC power, 6)reinstall battery, 7)wait 30 dys, 7)remove battery, 8)connect to AC power, 9)reinstall operating system(via AC source), 10)reinstall battery, 11)check battery level.

this test should prove if the OS is the culprit once and for all.  i will report back in early Feb. Of course in my case not liking unity, i have to install gnome classic after 12.04 which comes with unity.

---

### Post by Giveingitago on 2013-01-13
For my HP Sleekbook, I've logged this as an Ubuntu Kernel bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098697](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1098697)

---

### Post by mark bower on 2013-10-09
Maybe my final blast on laptop battery drain that may be helpful to others: 1) a summary of data from tests, and 2) a link to a method that worked for me.

Again, my system is an HP Pavillion g6, Ubuntu 12.04 LTS with Gnome Classic overlay. The BIOS on this computer does not have power options to turn things off versus what other posters have reported whereby their BIOSs have power turn off options.

At the beginning of each test the battery was charged to 100% capacity. Booting was always done with connection to AC; immediately after boot I looked at the battery capacity via battery icon (in top tray)>battery>Laptop Battery>scroll to read percent capacity remaining.

The conclusions I draw from my tests are the following: 1) the battery alone has a very low self discharge rate, 2) the computer in "WOL g" mode causes a very high rate of battery discharge and 3) "WOL d" mode results in about 2% battery discharge per day. 2% is not good in my opinion; .5% would be much better for a person who leaves the computer unattended for a month or so at a time.

I also did a hardware only test (not included here) which seemed to indicate that with no OS on board, there was a very low rate of discharge. However, I did not control the test well so this is only an assumption, ie, if no operating system on board the battery only discharges at its stand alone self discharge rate. And if this is true, it "says" again that "WOL d" does not eliminate some other unknown discharge action. Following are the test results:

[table="width: 500"]
[tr]
	[td]**Test**[/td]
	[td]**# of test days**[/td]
	[td]**% charge remaining**[/td]
	[td]**% loss/day average**[/td]
[/tr]
[tr]
	[td]Batt charged,removed for dys, then reinstalled to test[/td]
	[td]7[/td]
	[td]100[/td]
	[td]0[/td]
[/tr]
[tr]
	[td]WOL g --> WOL d[/td]
	[td]5[/td]
	[td]90.2[/td]
	[td]1.96[/td]
[/tr]
[tr]
	[td]repeat above longer period[/td]
	[td]10[/td]
	[td]80.0[/td]
	[td]2.0[/td]
[/tr]
[tr]
	[td]WOL d --> WOL g[/td]
	[td]6[/td]
	[td]0[/td]
	[td]>16.6[/td]
[/tr]
[tr]
	[td]repeat above shorter period[/td]
	[td]1[/td]
	[td]82.3[/td]
	[td]17.7[/td]
[/tr]
[tr]
	[td]WOL g --> WOL d[/td]
	[td]6[/td]
	[td]88.1[/td]
	[td]1.98[/td]
[/tr]
[/table]


The following link by Hectic Geek is the key to what worked for me to reduce the daily discharge rate to 2%. Essentially he describes how to copy the "disable-wol" file to /etc/pm/power.d and specifies the line in it to modify "WOL g" to "WOL d".* Then for each boot, "WOL d" is active. If anyone has problems with the link, I can repeat the essential code in another response to this thread.

[http://www.hecticgeek.com/2012/09/di...n-your-laptop/](http://www.hecticgeek.com/2012/09/di...n-your-laptop/)

---

### Post by stan-saraczewski-yahoo on 2014-02-05
I'm having the same problem with my G6 - your url at the end of the post is not found now - would you pls msg me to assist ? Thank you very much. I was considering buying a new battery then read your post...

---

### Post by jonhoover1 on 2014-09-02
Could this have something to do with Intel's Smart Connect technology?  When I had that installed on  Windows, my laptop would turn on for several minutes, several times a day.  Now, I am currently seeing that problem with Ubuntu/Linux Mint.  If so, is there a way to disable Smart Connect in Linux?

EDIT: There is an option in BIOS to turn off Smart Connect.  Will try that and see if it stops draining my battery.

---

