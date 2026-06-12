---
title: "Network manager and volume notification area icons invisible upon Karmic upgrade"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Jenda on 2009-11-06
I upgraded from 9.04 to 9.10 and, apart from a few other quirks that I've already managed to resolve, I still have an issue with notification area icons. The network manager and sound icons... well, they have no icons. They are there, can be clicked and work, but display as blank spaces on the panel. Does anyone know how to fix this?

These solutions don't work:
- rebooting/logging out and in/restarting X
- adding the notification area applet to panel (it's there, if I add it, the new one has the same problem)
- starting nm-applet and the volume applet manually (they are running)

Thanks!

---

### Post by maddocks on 2009-11-06
same here but i just ran fusion-icon from the terminal and its icon does show up ill add it to startup and see if it keeps its icon after restarting X. I wish i could right click on nm-applet or sound applet and change settings for the launcher and see if changing the icon hekp

---

### Post by Jenda on 2009-11-09
Two reboots later, the icons are there. I'll see if they stay or disappear again.

---

### Post by mavros on 2009-11-11
Same here a more or less random combination of icons are shown in the notification area. Some are even shown twice in some instances:  Sound is nearly always there sometimes twice. Battery is also there twice in many cases. Network is seldom there which is particularly annoying if you often change wireless networks.  The only solution is removing it from the panel and installing/adding the widget again.

---

### Post by Sennaista on 2009-11-12
Same issue here. Icons not shown and/or shown twice.

---

### Post by Jenda on 2009-11-14
Well, my icons don't appear twice, and it's always the same two icons: sound and network. However, it seems to me that it only gets borked if I use my external monitor (which is 90 percent of the time, unfortunately).

---

### Post by PauGNU on 2009-11-15
Same here!

---

### Post by Jenda on 2009-11-15
I honestly hope you folks have different issues... because mine was caused by a transparent panel and a beige desktop background :D The icons are intirely invisible on one of default Karmic wallpapers if the panel is transparent, it's just a sign of utter lameness that I haven't realized this before &#12484;

---

### Post by Digital Magi on 2009-11-21
I have had this problem intermittently as well. As I type this I have 2 volume icons (only 1 of which is functional) and no icon for wireless networking (but wireless is working fine)

This changes between reboots, no particular pattern that I can detect.

I can fix it by right-clicking and removing the "notification area" and then adding it back, makes the icons for sound & network right again.

---

### Post by jeremy on 2009-11-21
I have exactly the same (small but irritating) problem.

---

### Post by smirnoffjr on 2009-11-21
> **Digital Magi said:**
> I have had this problem intermittently as well. As I type this I have 2 volume icons (only 1 of which is functional) and no icon for wireless networking (but wireless is working fine)

This changes between reboots, no particular pattern that I can detect.

I can fix it by right-clicking and removing the "notification area" and then adding it back, makes the icons for sound & network right again.

Same for me sometimes on two computers. Need bugreport?

---

### Post by delta_one_ on 2009-11-24
I am having a similar problem. Often my network icon disappears, being replaced by a non-functional sound icon (left or right clicking on it does the same as just clicking on the panel).
As with Digital Magi, I can fix it by removing "notification area" from the panel and adding it again.

---

### Post by Digital Magi on 2009-11-25
Just as an experiment, I moved the notification area to the bottom panel next to the workplace icons. In this position the icons remain stable between reboots. No idea why this works, but so far it does.

---

### Post by EssBee on 2009-11-26
Exactly the same problem here. Okay it's not major, but it is very annoying and it doesn't help when I'm trying to demonstrate Ubuntu to other people.

Again, I'm using dual screen, with a monitor plugged into my laptop and compiz.

I upgraded to 9.10 from 9.04 using synaptic.

---

### Post by Pungero on 2009-11-27
> **Digital Magi said:**
> I have had this problem intermittently as well. As I type this I have 2 volume icons (only 1 of which is functional) and no icon for wireless networking (but wireless is working fine)

This changes between reboots, no particular pattern that I can detect.

I can fix it by right-clicking and removing the "notification area" and then adding it back, makes the icons for sound & network right again.

I have exactly the same problem with my eeePC, which is running Ubuntu Netbook Remix and connected to Internet via WLAN. My desktop computer, which is running normal Ubuntu 9.10 and is always connected to Internet via ethernet, has never shown this kind of behavior.

Could this problem be related to computers using wireless networks or UNR?

---

### Post by delta_one_ on 2009-11-27
> **Pungero said:**
> 
Could this problem be related to computers using wireless networks or UNR?

I would not think so, as I have the problem with my computer which is running desktop edition and is connected to a wired network. 

A number of people (including me) with this problem are using multiple monitors though. It could be related to that?

---

### Post by Digital Magi on 2009-11-28
> **delta_one_ said:**
> I would not think so, as I have the problem with my computer which is running desktop edition and is connected to a wired network. 

A number of people (including me) with this problem are using multiple monitors though. It could be related to that?

Don't think so. My desktop is set up with 2 monitors, no problem. My laptop is the one with the icon problem, only one screen there.

---

### Post by b00ka on 2009-11-30
Hi, same problem here - 
It seems to mainly be the network icon which is the problem, but the network connects as normal.  The only way I have found to fix is to stop the notification area applet and restart it.
 I haven't tried putting on the lower bar yet - I'll try that, but not sure if I want my Ubuntu starting to look like window$, with the notification area on the bottom. ;)

Surely someone has a fix that works permanently, or is this a bug that needs reporting???

---

### Post by sportsdude81 on 2009-12-01
Same problem here. Network icon is replaced with bluetooth icon.  it is still functional though.  It seems to mimic the icon to the left of it, if you guys are saying it mimics the sound icon.  Although I turned my mouse off today before start up and the network icon was just blank.

Update: After a reboot icon was blank and completely lost functionality.  Is there a bug report for this?

---

### Post by Velophile on 2009-12-03
I had the same problem, it appears to have been fixed by removing the icon I had added to the panel between the notification area and the clock.

The notification area's behaved itself since I moved the icon over to be next to the menus.

---

### Post by Ubuntero100 on 2009-12-05
> **mavros said:**
> Same here a more or less random combination of icons are shown in the notification area. Some are even shown twice in some instances:  Sound is nearly always there sometimes twice. Battery is also there twice in many cases. Network is seldom there which is particularly annoying if you often change wireless networks.  The only solution is removing it from the panel and installing/adding the widget again.


Exactly the same here. More often than not i have two volume icons but not network connection  icon.

So annoying.

---

### Post by pierce_g on 2009-12-07
I've been having this problem too. I think it might be related to the visual effects settings. The problem only showed up when I switched my visual effects from "None" to "Normal" today. When I changed it back to "None" again, the problem disappeared.

---

### Post by emotionlovesyou on 2009-12-07
Switching the visual effects to "none" seems to work fine. This is a lame fix, however, because we all love the visual effects and someone should fine a better solution. It's a necessary sacrifice, though, at this point for the sake of usability. Also you may try removing the notification area from the panel and then re-adding it, but that's another weird fix and doesn't always work.

---

### Post by pierce_g on 2009-12-07
[This bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/449910") is sort of vague, but it addresses the problem sufficiently enough.

---

### Post by solemnavalanche on 2009-12-11
For people looking for an actual fix, someone on the bug report posted this kludgy but effective workaround. 

Create a script with the following lines:

#!/bin/bash
killall gnome-panel

Go to System->Preferences->Startup Applications and add the script.

The script kills the panel, which restarts automatically. Because it happens right at startup, the effect is quite invisible. Works for me, anyway.

---

### Post by Popaul on 2009-12-21
There's a bug report #432589 that seems to match this issue, pretty old though:
[https://bugs.launchpad.net/gnome-panel/+bug/432589](https://bugs.launchpad.net/gnome-panel/+bug/432589)
I have similar problem, just that the sound icon will never come up again, whatever I do.

---

### Post by Popaul on 2009-12-21
Actually... may not be a bug. Check the System/Preferences/Start-Up Applications:
 - verify that network manager is ticked on, etc... all the things that should appear in the notification areas should be ticked on in this dialog.
And also make sure that, in tab "options" the box for 'Automatically remember running applications ..." is ticked, so that your settings will be fixed for the next bootsw as well.

---

### Post by danb1974 on 2009-12-25
It's a bug - I too had to switch off desktop effects, otherwise network manager icon was non-functional on initial (auto)login (either doubling the volume control icon or just a blank space but non-responsive to clicks)

A logout + login (without rebooting) would fix it, so would sudo killall gnome-panel

Now the question is whose fault is it, nm-applet, compiz or notification area

---

### Post by Ticatla on 2009-12-25
Hi! Same problem, I think. No icon appears and there is no menu after clicking in the area. No volume, battery icon or network manager. This seems to specially affect the network manager because my wireless doesn't connect automatically. I have to use nm-applet on the terminal so it reacts and I can connect. It is useless to turn on and off my wifi card. If I connect the Ethernet cable the icon do appears. 

Restarting doesn't work, neither adding again or moving the notification area. 

Quite annoying. Help, please.

---

### Post by chr0n0 on 2010-01-14
Hey everybody.  I fixed it - at least for myself.  What I believe led to this was when I moved some of the 'locked' panel items around.  I have been agonizing over this for two or three weeks now, and after reading this thread, I had an idea.  Here is what I did.  Please bear with me; the reboots seem a little excessive, but seemed to help me (finally) resolve this issue.

First, I rearranged my panel to have:
(from *right* to *left*, and locked in place)
1. The 'power' button which allows you to restart, log off, etc...
2. The notification area
3. The clock

Second, I disabled 'Volume Control' and 'Network Manager' in 'Startup Applications' (System->Preferences->Startup Applications) then I rebooted.

*******Before proceeding, be sure that you are able to manually configure a network interface because after the following step you will *NOT* automatically connect to your network*******

Third, I opened a terminal and did
```
sudo apt-get remove network-manager network-manager-gnome
```
Once that finished, I rebooted.

*******Keep in mind that you will need to manually configure an interface to connect to the internet to reinstall these packages in a moment*******

Fourth, I opened a terminal and did
```
sudo apt-get install network-manager network-manager-gnome
```
then rebooted.

Fifth, I added 'Volume Control' and 'Network Manager' back to 'Startup Applications'  then rebooted.

On subsequent reboots it has not acted up again.  Hopefully others get similar results to what I have.  Cheers.

---

### Post by hoare on 2010-02-03
> **solemnavalanche said:**
> For people looking for an actual fix, someone on the bug report posted this kludgy but effective workaround. 

Create a script with the following lines:

#!/bin/bash
killall gnome-panel

Go to System->Preferences->Startup Applications and add the script.

The script kills the panel, which restarts automatically. Because it happens right at startup, the effect is quite invisible. Works for me, anyway.

this works for me - thank you!!!!! , but still it would be nice to have a real fix

---

