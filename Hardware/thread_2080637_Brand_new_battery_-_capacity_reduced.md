---
title: "Brand new battery - capacity reduced"
date: 2012-11-04
forum: Hardware
---

### Post by 23senick on 2012-11-04
I've installed Ubuntu 12.04 twice on a Samsung Chromebook 550. All works really well, but I've noticed that after a couple of days on both machines the battery isn't charging to full capacity.  It's design capacity is 50.3Wh, but both times it's charged to only 94.1% (47.4Wh).  And when I revert to ChromeOS the battery is also stuck on 94.1% maximum charge.  

I have Ubuntu on 2 other laptops, both batteries are still at or near 100% after several months.  

Anyone got any ideas why the Chromebook battery has reduced capacity after no more than a few days?  Is some software protecting the battery? Some incompatibility?  An issue for Chromebooks only, or other products, especially Samsung?  Thoughts welcome!

---

### Post by 23senick on 2012-11-20
Anyone got any thoughts..?

---

### Post by 23senick on 2012-11-28
Just had a private message from someone who seems to have same issue.  From now on I will only charge it up switched off.  

If anyone has ideas about why battery would lose capacity, do let me know please!   

By the way, I used the "Chrubuntu" script to install it - others who are more adept will have worked out how to do it themselves.

---

### Post by 2F4U on 2012-11-28
I don't know this particular hardware, but it may be a setting in the BIOS or in the charging logic of the laptop to prevent overcharging and therefore damaging the battery.

---

### Post by krstec on 2013-05-13
Hi

Did you find any solution to this? I am having the same issue on my chromebook 5 550. Mine got stuck on 46.2W. The strange thing is that it did this from the first time i used it with Ubuntu. 

Does the battery get worse with time? Could it be really that the battery does not fully charge or it is just that the battery meter shows wrong after a full charge?

Thanks in advance!

---

### Post by pqwoerituytrueiwoq on 2013-05-13
[**[COLOR=#000000]@krstec[/COLOR]**]("http://ubuntuforums.org/member.php?u=1820828") you may want to try the 3.9 kernel, full chromebook hardware support was added to the kernel in that version
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
yes batteries do degrade over time, this happens with all rechargeable batteries, to get the most out of a battery run it dry before charging it and charge it to 100% when you do charge it, dont leave it plugged in to the laptop when you are not using it
also check the MAH rating on the battery, higher numbers means the battery will last longer

---

### Post by snafu006 on 2013-05-13
First can you tell the spec of your computer: NVM found

then try this [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html) 
```
**Ubuntu (and Linux Mint, etc.) users  can install TLP by using its official PPA. Add the PPA and install TLP  using the following commands:**

sudo add-apt-repository ppa:linrunner/tlp 
sudo apt-get update 
sudo apt-get install tlp tlp-rdw

TLP will automatically start  upon  system startup, but to avoid having to restart the system to get it  running for the first time, you can start it (required only the first  time) using the following command:

sudo tlp start
[B]
There are some optional packages you can install for some extra features:[/B]

[LIST]
[*]*smartmontools* - needed to display disk drive S.M.A.R.T. data; 
[*]*ethtool* - needed to disable wake on lan. 
[/LIST]

Install these tools (available in the Ubuntu repositories) using the following command:

sudo apt-get install smartmontools ethtool
[B]
There are also some ThinkPad only, optional packages you may need:[/B]

[LIST]
[*]*tp-smapi-dkms* - needed for battery charge thresholds and ThinkPad specific status output of tlp-stat; 
[*]*acpi-call-tools* -  acpi-call is needed for battery charge thresholds on Sandy Bridge and newer models (X220/T420, X230/T430, etc.). 
[/LIST]

Install these packages using the following command:

sudo apt-get install tp-smapi-dkms acpi-call-tools
```


also have you install lm-sensors

sudo apt-get lm-sensors
sudo sensors-detect

and power-top is a good terminal 
[http://www.webupd8.org/2012/08/install-powertop-21-in-ubuntu-1204.html](http://www.webupd8.org/2012/08/install-powertop-21-in-ubuntu-1204.html)

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install powertop

Run powertop sounds like something is eatting up your power or your charger is bad

---

### Post by krstec on 2013-05-15
> **pqwoerituytrueiwoq said:**
> [**[COLOR=#000000]@krstec[/COLOR]**]("http://ubuntuforums.org/member.php?u=1820828") you may want to try the 3.9 kernel, full chromebook hardware support was added to the kernel in that version
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)
yes batteries do degrade over time, this happens with all rechargeable batteries, to get the most out of a battery run it dry before charging it and charge it to 100% when you do charge it, dont leave it plugged in to the laptop when you are not using it
also check the MAH rating on the battery, higher numbers means the battery will last lo tnger

Yes for sure i understand they degrade, but 15% loss of battery life after 10 days of use and maybe 5-10 charges does not add up. I will try to uppdate the Kernal as you suggest, that would for sure be a good idea!

Many thanks for the link!

---

### Post by 23senick on 2013-05-16
I haven't tried tweaking software or different kernels - too complex for me. I'm also not convinced about kernel 3.9 - the S550 Chromebook runs on 4.0.  

I don't have a solution, but I do have a way to prevent further battery degradation (and if you are starting with a 100% battery hopefully it will maintain it).

Basically, I only charge the Chromebook when it is either switched off or running ChromeOS.  I don't ever plug it in when running Ubuntu.  Been doing this for several months and battery has not deteriorated any further.  

It's a minor inconvenience, given that for £300 I got a stylish ultrafast Ubuntu machine with 8 hour battery life.

---

### Post by krstec on 2013-05-21
Yes i get your point and i do trust in that the problem could be related to bad charging, As said before i think the problem can be related to over discharge of the battery. When switching to ubuntu i forgot to put the option to turn the laptop if when the battery charge goes low.  This can have maybe damaged my battery, twice dumb as i was i runned the battery to complete zero. 

It is a shame that ubuntu does not have a better charging management, but well, for the low price of 250 i will have to live with it. I only wish there will be a new chromebook soon with a intel processor for a decent price. The acer7 is to fatty and uggly for my likes.

However I am not sure either that it actually is not just a defect battery from the beginning, never used the chromebook at all in chromeos ( i switched to ubuntu directly the first day) so maybe will try to get a repair if it degrades fast now, even thought i know they are not typically having the battery on warranty...

What do you mean by the S550 chromebook running 4.0, dont get that one? To uppdate the kernel to 3.9 is very easy but did not see any difference.

---

### Post by 23senick on 2013-05-23
Did you install using the Chrubuntu script? If yes, I don't think it was to do with the over discharge you mentioned. My S550 never got low.  And it isn't a problem with Ubuntu generally - I have other "normal" laptops running it without problems. The fact is using the Chrubuntu script to install Ubuntu (as I did) means you are using non-standard stuff.  I tried asking the person who created it what the problem is on their website but didn't get a response.

You also asked about the Linux kernel.  As far as I understand it, the Chrubuntu script uses the ChromeOS kernel, which is 4.0.  Try going into system monitor, click on the tab "system" and you see the kernel version, mine has always been 3.4.0. I suspect it would be safe to remove the kernel installed with Ubuntu (mine is on 3.2.43) as I don't think it's used - but I haven't been brave enough to try!

---

### Post by krstec on 2013-05-29
Hi

Yes I used the chrubuntu script and installed the latest tnyga verison. I managed to uppdate my kernel i think once before as a trial, but to be honest I have no clue what that would improve, for sure me I did not see any effect.

My worries with the discharge question was that the sleep option/power of option when battery is low was dissabled when i first installed chrubuntu. My concern was that the battery has been pulled so low until it shut down its power, rather than ubuntu feeling that the battery is low and turning the laptop of. If that scenario did/can happen, i dont find it completely unlikely that the battery voltage could have gotten so low so the cells got damage.

However, as it appears so few persons are experience this problem (not many reporting having any problem atleast) I would not complety rule out a battey problem. As you say, you have runed ubuntu before on other laptops without any problems :-)

---

