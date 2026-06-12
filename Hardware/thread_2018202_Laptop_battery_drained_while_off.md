---
title: "Laptop battery drained while off"
date: 2012-07-06
forum: Hardware
---

### Post by lonekingc4 on 2012-07-06
Hi,

I am using Ubuntu 12.04 (64 bit) in my HP Pavilion g6 laptop. I am facing a problem though. Every time I turn off the laptop, even with the battery fully charged, the next time I turn it on, the charge seems to be dropped significantly. If it is off for 7-8 days, then the battery is drained completely and it won't turn on at all.

I found out that if I take off the battery after I turn it off and put it back in after about 10 seconds, then the charge does not drop even after a few days.

I used Ubuntu 11.10 in the same laptop before and it had the same problem. But strangely, when I dual booted Linux Mint, and gave it a test run about this battery issue, it didn't have this problem at all. Even more strange is that I use Ubuntu 12.04 in my netbook as well and it doesn't cause the problem there.

So it seems like for some reason, this problem only occurs in my laptop running Ubuntu. So any idea why this might happen and how/if I can fix this?

Cheers and thanks :D

---

### Post by Redblade20XX on 2012-07-06
Seems to be a Wake-On-Lan problem. 

WOL is a method to wake up your computer when suspended by sending a magic packet. I had a similar problem and it was due to wake-on-lan being enabled when the computer is shutdown thus using power for the network card and killing my battery.

Look into your BIOS for a setting to disable. If there isn't, you'll probably have to make a script to disable it on shutdown.

- Red

---

### Post by mark bower on 2012-08-24
Pavillion g6, Linux Mint.  I have the same problem with the fully charged battery going to 0% within 13 dys(probably less).  Called HP and tech(he said he checked with lead techs) said they were not familiar with the problem.

I modified the line "-d -f $netdown $poweroff $hddown" in /etc/init.d/halt to read "-d -f -i $poweroff $hddown".  This was suggested, but does not work.  I am currently trying the suggestion to disable wifi before shutting down the laptop.  I can find nothing in the BIOS that would help.

Next (if previous does not work) I am going to try the suggestion of no A/C connection,removing and reinstalling battery which has been suggested.

Any other suggestions are welcome.

(I use Ubuntu 10.10 on my PCs, trying out Linux Mint on the laptop, and may return to 10.10 for the laptop, or 12.04 with modified desktop)

---

### Post by mark bower on 2012-08-30
bump for notice

---

### Post by dandnsmith on 2012-08-31
I have certainly noticed a current drain if I shutdown my netbook with wifi still on. Other than that I have nothing to add, I'm afraid.

---

### Post by jonnyboysmithy on 2012-08-31
Same problem, on hp pavilion dv6023. I thought it was normal. Apparently not.

---

### Post by mark bower on 2012-08-31
I have tried a number of options that I gathered here and there as remedies - with no success. I realize that the problem may be other than wifi or WOL, but control of these functions are stated as a cure for some persons.

Things tried that do stop battery drain on my Pavillion g6:
1) A/C disconnected, R&R battery
2) Shutdown via:  press Restart, press ESC @ BIOS msg, press Off Btn
3) Disabled wifi from the tool tray
4) BIOS settings for Wake On Lan(WOL) do not exist
5) /etc/init.d/halt changed line "halt -d -f $netdown $poweroff $hddown" to read " halt -d -f -i $netdown $hddown"
6) HP technical support @ 800 474.6836 was no help - said never heard of the drain problem for off condition
7) ethtool showed "Wake-on: g".   in /etc/network/interfaces the "interfaces" file showed only the following two lines:
	auto lo	
	iface lo inet loopback
i added to "interfaces" the line "up ethtool -s eth0 wol d" ; note "d" not "g" - the ubuntu documentation suggests only "g" should not be a WOL enable.  pls see link below which details enabling.

	[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

o.k.  open for more options/ideas.
mark bower

---

### Post by mark bower on 2012-09-01
o.k.  i have updated a bit - see below.  "sudo ethtool eth0" still shows "Wake-on:  g", which suggests the WOL is still enabled.  There must be some other file(s) other than those i have found which are enabling it?

Things tried that do not work:
1) A/C disconnected, R&R battery
2) Shutdown via:  press Restart, press ESC @ BIOS msg, press Off Btn
3) Disabled wifi from the tool tray
4) BIOS settings for Wake On Lan(WOL) do not exist
5) /etc/init.d/halt changed line "halt -d -f $netdown $poweroff $hddown" to read " halt -d -f -i $netdown $hddown"
6) HP technical support @ 800 474.6836 was no help - said never heard of the drain problem for off condition
7) ethtool shows "Wake-on: g".   in /etc/network/interfaces the "interfaces" file showed only the following two lines:
	auto lo	
	iface lo inet loopback
i added to the "interfaces file" the line "up ethtool -s eth0 wol d" ; note "d" not "g" - the ubuntu documentation in link below suggests  "d" should disable WOL:

	[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

8) "wol" is seen in the following file & applicable lines

/etc/network/interfaces:  up ethtool -s eth0 wol d  (i added this line)
/etc/network/interfaces~:  up ethtool -s eth0 wol d (this line was aready there)
/etc/network/if-up.d/ethtool:  there are 3 interesting lines, what do they mean?
	# WOL has an optional pass-key
	set -- $IF_ETHERNET_WOL		
	SETTINGS = "$SETTINGS${1:+ wol $1}${2:+ sopass $2}"  . 1: + wol

so still seeking help.  mark b

---

### Post by lonekingc4 on 2013-01-12
Thanks all for your advises.

I just remove the battery after I turn the laptop off and put it back again. That is the only solution that seems to work for me.

Cheers :D

---

### Post by rauli on 2013-08-01
I have a Toshiba Satellite L755-1DR laptop and ubuntu 12.04 64bit. I also had battery drain. I turned of "sleep and charge" in the bios and now I don't have battery drain. "Sleep and charge" makes it possible to have power in one of the usb ports while the laptop is off. I don't nead that, so problem solved for me.

---

### Post by mark bower on 2013-10-09
This is my last blast on battery drain that may be helpful to others:  1) a summary of data from tests, and 2) a link to a method that worked for me.  

Again, my system is an HP Pavillion g6, Ubuntu 12.04 LTS with Gnome Classic overlay.  The BIOS on this computer does not have power options to turn things off versus what other posters have reported whereby their BIOSs have power turn off options.

At the beginning of each test the battery was charged to 100% capacity.   Booting was always done with connection to AC; immediately after boot I looked at the battery capacity via battery icon (in top tray)>battery>Laptop Battery>scroll to read percent capacity remaining.

The conclusions I draw from my tests are the following:  1) the battery alone has a very low self discharge rate, 2) the computer in "WOL g" mode causes a very high rate of battery discharge and 3) "WOL d" mode results in about 2% battery discharge per day.  2% is not good in my opinion; .5% would be much better for a person who leaves the computer unattended for a month or so at a time.

I also did a hardware only test (not included here) which seemed to indicate that with no OS on board, there was a very low rate of discharge.  However, I did not control the test well so this is only an assumption, ie, if no operating system on board the battery only discharges at its stand alone self discharge rate.  And if this is true, it would mean there is something remaining in Ubuntu-computer interaction that causes the 2%/dy discharge rate even with "WOL d" mode.  Following are the test results:

                                    [TABLE]
[TR]
[TD][B][U]Test
[/U][/B][/TD]
[TD]**_# of test days_**[/TD]
[TD]**_% charge remaining_**[/TD]
[TD]**_% loss/day average_**[/TD]
[/TR]
[TR]
[TD]Batt charged,removed for dys, then reinstalled[/TD]
[TD]7[/TD]
[TD]100[/TD]
[TD]0[/TD]
[/TR]
[TR]
[TD]WOL g --> WOL d[/TD]
[TD]5[/TD]
[TD]90.2[/TD]
[TD]1.96[/TD]
[/TR]
[TR]
[TD]repeat above longer period[/TD]
[TD]10[/TD]
[TD]80[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]WOL d --> WOL g[/TD]
[TD]6[/TD]
[TD]0[/TD]
[TD]>16.6[/TD]
[/TR]
[TR]
[TD]repeat above shorter period[/TD]
[TD]1[/TD]
[TD]82.3[/TD]
[TD]17.7[/TD]
[/TR]
[TR]
[TD]WOL g --> WOL d[/TD]
[TD]6[/TD]
[TD]88.1[/TD]
[TD]1.98[/TD]
[/TR]
[/TABLE]
    

The following link by Hectic Geek is the key to what worked for me.  Essentially he describes how to copy the "disable-wol" file to /etc/pm/power.d and specifies the line in it to modify "WOL g" to "WOL d".  Then for each boot, "WOL d" is active.

[http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/)

---

