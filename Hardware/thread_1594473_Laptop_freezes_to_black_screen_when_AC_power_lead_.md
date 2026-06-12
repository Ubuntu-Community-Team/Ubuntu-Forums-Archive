---
title: "Laptop freezes to black screen when AC power lead removed"
date: 2010-10-12
forum: Hardware
---

### Post by JosephWheatley on 2010-10-12
Got a clean install of Ubuntu 10.10 Maverick with all updates on installation.

I simply pull out the power lead on my Packard Bell MZ35 laptop and as the black popup notification appears telling me about my battery status the screen goes blank with a frozen cursor. 
The same happens if I start up on battery. There is no problem until the moment that the wireless connects again and the black pop-up notification appears I get the same black screen with frozen mouse cursor.

I have to resort to a hard restart each time.

Everything works fine plugged in i.e. LAN is wired and power is plugged in.

Tried the advice here [http://ubuntuforums.org/showthread.php?p=9266363#post9266363](http://ubuntuforums.org/showthread.php?p=9266363#post9266363)
But it has not made a difference.

My wireless card is Ralink RT2561/RT61 rev B 802.11g

[COLOR=#000000][FONT=Arial]***Using Comments #50 and #54 from ***[/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745) [COLOR=#000000][FONT=Arial]***I did the following to prevent the freezes on my Packard Bell MZ35***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I created an empty file by right clicking on the desktop and choosing "Create Document" and then "Empty File"***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***Then I gave the file the name***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***pcie_aspm***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I repeated this to create another empty file called***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***wireless***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***The two files were be copied to the folder /etc/pm/power.d***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I started the terminal with the command ctrl-alt-T***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***navigated to the Desktop folder with***[/FONT][/COLOR]

```
cd Desktop
```
[COLOR=#000000][FONT=Arial]***and pasted in this command***[/FONT][/COLOR]

```
sudo cp pcie_aspm /etc/pm/power.d
```
[COLOR=#000000][FONT=Arial]***followed by***[/FONT][/COLOR]
```

sudo cp wireless /etc/pm/power.d
```
[COLOR=#000000][FONT=Arial]***Once this had been done I pulled out the power lead and found my laptop no longer crashed.***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***I  think a restart is necessary as within an hour my computer performed a  bizarre reboot that must have been caused by confusing the pm-utils***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***I have had no such crashes since.***[/FONT][/COLOR]


It has been reported here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/666852)
and here [https://bugs.launchpad.net/ubuntu/+bug/669044](https://bugs.launchpad.net/ubuntu/+bug/669044)

  [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/comments/37"]
[/URL]

---

### Post by Sense on 2010-10-13
I have exactly the same problem on exactly the same type of laptop. I can confirm that this only happens when you connect are are connected when the AC power lead is unplugged and you're running on battery power.

---

### Post by toker_tok on 2010-10-16
i have a similar issue. I am medion akoya e1210 with 10.10 running. When i remove the ac, it says critical battery, i say cancel and it runs fine. Until the screen goes to sleep(by the way screensaver does not run), at which time all is over, all is frozen. cannot ssh. need a hard start. Pretty annoying for laptop---kind of need to be able to use it on battery power.

---

### Post by tavito on 2010-10-19
I have the same problem with a different laptop: Samsung Q310 and a Nvidia 9200 graphical card.

In my case, to get to this situation I tried to solve a few other problems. Let me tell you the background:

I upgraded my installation from Ubuntu 10.04 and everything seemed to work fine. Then I tried enabling desktop effects, so I had to enable the proprietary drivers.

After doing this, the Screen brightness applet stopped working, and if I tried to use the FN keys plus the increase / decrease brightness special key, my keyboard would get blocked. Also the screen would not dim when on battery.

Then I disabled the proprietary drivers (trying to go back to the previous status) and the screen would dim and the brightness applet would work. But the keyboard would get blocked anyway if I used the FN key to try to decrease or increase the brightness, as before.

Then I started installing / uninstalling newer versions of the proprietary drivers from "nvidia vdpau" repository, and discovered [this thread]("http://ubuntuforums.org/showpost.php?p=9494941&postcount=8"). At some point something fixed the issue with the screen brightness and the proprietary drivers, but I'm still having the keyboard locked up when using the FN key to increase / decrease the brightness, and in addition when the screen dims below half the normal brightness (which can happen with the screen brightness applet or when unplugging the AC), my screen turns completely black, and freezes, so I can't do anything with it, as described by the users above.

Any suggestion on how to fix this would really be appreciated :)

---

### Post by mrspacklecrisp on 2010-10-19
I'm having issues with my netbook acting strangely in relation to whether or not it detects the power chord to be plugged in, but I'm in 10.04. This comes after a recent update. It's not quite the same, but it is causing serious problems. This happens regardless of whether not a charged battery is in.

[http://ubuntuforums.org/showthread.php?p=9997941#post9997941](http://ubuntuforums.org/showthread.php?p=9997941#post9997941)

---

### Post by jljansen on 2010-10-24
I've the same problem as above after upgrading from 10.04 to 10.10!
If on battery I can start my laptop but after login to ubuntu the screen goes black, mouse freezes and num & caps lock keep blinking. A hard reset is necessary to reboot.
The laptop works fine when plugged in. But when I take the power plug out it freezes as described above. When I disable the wireless  card (through function key) and then take the power plug out everything works fine till I put the wireless card back on!

I've MEDION AKOYA which is almost the same as a MSI S271. The wireless card (Ralink RT2561/RT61) has always been the problem with upgrades! Anyone has an idea how to fix it?

---

### Post by toph on 2010-10-29
Hello.

I am also having problems with 10.10 when on battery power. I am using an MSI U210 laptop(specs in signature). Everything works fine when plugged in. However, on battery power, I have issues. Sometimes (most of the time)10.10 won't boot completely. It'll freeze up after the splash screen and before it loads completely. Sometimes, I get the splash screen, then a black screen with blinking cursor. When it does boot completely, it will freeze up when on for a while (I assume when it wants to sleep or when the screensaver wants to start). I've also noticed that it'll freeze up when I try to switch desktops or when I run Gwibber. Also, if I have Gwibber set to run t start, I'll freeze on boot up. Also, when I am plugged in and remove the plug, I get the critical battery warning, but cancel out of it and all is fine (until the first freeze).

Let me know if more details are needed.

- Chris

---

### Post by toph on 2010-10-30
Seems like [a big problem]("http://ubuntuforums.org/showthread.php?t=1596096&highlight=laptop+freezes+battery").

---

### Post by jljansen on 2010-10-31
I've filled a bugreport which you can find [here]("https://bugs.launchpad.net/ubuntu/+bug/669044"). Hopefully you all can take the time to add some additional details! Hopefully this will speed up an possible solution!

---

### Post by MiroDz on 2010-10-31
I upgraded my Ubuntu 64-bit from 10.04 to 10.10 (by upgrade process) yesterday, everything seemed to work perfectly until I removed the AC power lead. Shortly after I noticed that wifi disconnected and after 5 seconds or so laptop totally crashed with the white screen. Nothing helped but hard power off... I repeated the same few times more - always the same result - wifi disconnects and then hard lockup with white/black/purple/colorfull pattern on LCD.

Then I made the clean install of 10.10 but finished with the same problem...

I tried to start OS while only on battery, it managed to get the login screen and then crashed...

I've assumed that 10.10 is unusable for me at the moment and installed back the 10.04 from the backup - everything is OK. So the problem is definitely with 10.10.

My basic HW info: Dell Vostro 1000, AMD TurionX2 2000MHz, 6GB DDR2, ATi Xpress 1150 Chipset (= RS485 NB + SB600 NB), Intel Wireless WiFi Link 4965AGN

I do suspect the problem is in 10.10 kernel or intel wifi driver or ubuntu power-management software.

10.04 works fine on my laptop which is almost nonstop on (running BOINC).

---

### Post by fiepel on 2010-11-24
Count me in as an affected user.

I have Medion Akoya E1210.
Upgraded from 10.4 to 10.10 and tried a lot to fix the problem.

When I boot with AC power connected, everything is fine (wifi) and resume also works.
When I boot on battery power, everything fine except after resume Wifi will not connect.

After a resume: when I remove the power cord, I first get a warning that the battery is extremely low (however it also indicates that it is 98% full). At that moment also wifi disconnects and goes on searching for a network forever. If I leave the cord unplugged the system crashes eventually. When I plug the power back in, wifi connects again.

Very weird....

---

### Post by toph on 2010-11-27
I tried this and it worked for me. I can now boot from battery.

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

I hope it works for some of you.

Chris

---

### Post by spantch101 on 2011-01-05
ok .. seems the problem has been with the pm-utils in synaptic if you are having this issue check synaptic and see if you are running 1.4... if you are remove it and reinstall older version 1.3 here [http://packages.ubuntu.com/de/lucid/all/pm-utils/download](http://packages.ubuntu.com/de/lucid/all/pm-utils/download) fixed my problem... i just unplugged my laptop and its running perfectly... thanks to aspera for this info on launchpad :) hope this works for you...after install of 1.3 reboot just in case ...let me know how it works out for you.

---

### Post by JosephWheatley on 2011-01-11
Thanks this has solved the problem for me.
Where did you find this out?

Also my laptop still won't return from suspend. Is this related to pm-utils?

---

### Post by JosephWheatley on 2011-01-29
[COLOR=#000000][FONT=Arial][B][I]I reverted back pm-utils 1.4 after trying pm-utils 1.3 which worked but I like the following workaround
Using Comments #50 and #54 from [/I][/B][/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745) [COLOR=#000000][FONT=Arial]***I did the following to prevent the freezes on my Packard Bell MZ35***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I created an empty file by right clicking on the desktop and choosing "Create Document" and then "Empty File"***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***Then I gave the file the name***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***pcie_aspm***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I repeated this to create another empty file called***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***wireless***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***The two files were be copied to the folder /etc/pm/power.d***[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]***I started the terminal with the command ctrl-alt-T***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***navigated to the Desktop folder with***[/FONT][/COLOR]

```
cd Desktop
```[COLOR=#000000][FONT=Arial]***and pasted in this command***[/FONT][/COLOR]

```
sudo cp pcie_aspm /etc/pm/power.d
```[COLOR=#000000][FONT=Arial]***followed by***[/FONT][/COLOR]
```

sudo cp wireless /etc/pm/power.d
```[COLOR=#000000][FONT=Arial]***Once this had been done I pulled out the power lead and found my laptop no longer crashed.***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***I  think a restart is  necessary as within an hour my computer performed a  bizarre reboot that  must have been caused by confusing the pm-utils***[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]***I have had no such crashes since.***[/FONT][/COLOR]

---

### Post by cjwebster on 2011-04-21
I was experiencing the same issue on my Dell Vostro until I Followed the instructions in the original post and it seems to have resolved the issue for me too.

I'm running the following: Dell Vostro 3700 i5 8Gb RAM, Broadcom wireless, 
Ubuntu 10.10 64bit

---

### Post by JosephWheatley on 2012-11-09
It seems to me that pm-utils is the trouble maker here

Even in12.04 I still have issues when the power management is turned on when I take the power lead out. The wireless breaks up and losses connection.

---

