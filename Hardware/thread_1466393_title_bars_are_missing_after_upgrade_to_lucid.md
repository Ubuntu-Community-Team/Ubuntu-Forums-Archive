---
title: "title bars are missing after upgrade to lucid"
date: 2010-04-30
forum: Hardware
---

### Post by dumas33 on 2010-04-30
After upgrading to Lucid and rebooting there are no title bars in open programs. If I change visual effects to normal or extra, titl ebar appears.

Unfortunately, after restarting system visual effects are reset to 'none' again. So each time the system starts I need to go to Appearance to enable visual effects to get title bars. How to fix it?

Laptop is Dell Lattitude E6400, with nvidia quadro NVS160M video card. I use proprietary drivers (version current, according 'Hardware Drivers').

---

### Post by dumas33 on 2010-04-30
It seems that the problem is in user settings in Home dir.
I created new user to check if it is same problem with fresh home settings, and guess what, there are no title bar problem in empty home dir.

Should I delete some settings files in my home dir?
Any suggestions?

---

### Post by cjnkns on 2010-04-30
Same issue here - hopefully a fix comes soon.

---

### Post by drpjkurian on 2010-05-02
Hi
I have the same problem as Dumas. If it is a bug, how to do bug report?

---

### Post by drpjkurian on 2010-05-02
Hi
I have two display managers namely Gnome and KDE. well I was able to solve in KDE by removing Compiz. In Gnome it still persists..

---

### Post by dumas33 on 2010-05-02
I don't know how but I solved it. I was playing around with hidden folders in home. After moving .config to home/tmp_conf and restarting PC visual effects worked fine. I deleted few folders of old uninstalled programs in tmp_conf and moved it back to .config.

So far visual effect works fine. Sorry for not writing down folder names I deleted, I just forgot them. But hope you have an idea how fix problem (please make back up of .config before starting deletions)

---

### Post by darkmakozu on 2010-05-03
I fixed the issue by adding 

/usr/bin/compiz

To the list of start up applications.

Something that is annoying me however is that the mail applet options keeps appearing on log in, all the time.

---

### Post by drpjkurian on 2010-05-04
hi I fixed the problem in GNOME by removing all the files in .config folder in Home. but now i am not able to activate the ' extra effects' in visual effects.

---

### Post by eric_son on 2010-05-04
> **darkmakozu said:**
> I fixed the issue by adding 

/usr/bin/compiz

To the list of start up applications.


Hey thanks!  That was just what I needed.

Kinda odd though.    Before I applied the fix you mentioned, I noticed the following:
1) Logging off then logging on again seems to fix the window title bar problem. 
2) Listing the active processes at first boot shows that /usr/bin/compiz is already running.  But there are no window title bars.  Strange.

But hey...your solution works. :)

---

### Post by sauma on 2010-05-05
I have the opposite problem. I only have title bars when visual effects are off. When I turn them on, the bars go away. I created a new user to test and this wasn't a problem.

Any ideas? I've been looking around here but can't find anything that really matches my dilemma...

---

### Post by weissed on 2010-05-05
I've updated some packages yesterday in Synaptic (don't remember exactly what was there to update, I just marked all upgrades and then applied them) and today when I started the computer the problem seems to be fixed.

---

### Post by uboops on 2010-05-09
> **cjnkns said:**
> Same issue here - hopefully a fix comes soon.
Hello, soon but when, do you have any others information sources ?
Because I've updated some packages today via Synaptic but the problem remains.

FI:Similar bug here:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/577482](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/577482)

An other link (in French):
[http://forum.ubuntu-fr.org/viewtopic.php?id=392517](http://forum.ubuntu-fr.org/viewtopic.php?id=392517)

> **darkmakozu said:**
> I fixed the issue by adding 
/usr/bin/compiz
To the list of start up applications...
Hello,
I have tried this solution but it does not work each time, so this bug remains here...
Ubuntu 32 Lucid v10.04 - kernel 2.6.32.22-generic-pae

my video card = ATI Technologies Inc RV730XT [Radeon HD 4670]

PS: maybe this bug is due to the status of the free Radeon drivers (not already done at 100%) ?
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)
[http://www.x.org/wiki/radeonhd](http://www.x.org/wiki/radeonhd)

---

### Post by Scott O'Nanski on 2010-05-13
System >> Preferences >> Appearance;

Click "Visual Effects" Tab

Select "None" to turn off Compiz.

Then,

Select "Extra" to turn Compiz back on.


Problem solved.

---

### Post by uboops on 2010-05-13
> **Scott O'Nanski said:**
> System >> Preferences >> Appearance;
Click "Visual Effects" Tab
Select "None" to turn off Compiz.
Then,
Select "Extra" to turn Compiz back on.
Problem solved.
I have already tried this workaround (also known into the French forum), but sometime after some reboot the problem came up again, so does not solve the issue.

---

### Post by johnathanamber on 2010-05-17
Hey everyone!

This is something that I've been seeing since Jaunty.

I have run both the 32bit and 64 bit of Karmic and Lucid, they both have this issue.

I've been working on making a minimal installation. Thus far it is working great!

I've got Gnome installed, can connect to the internet via wired or wireless.

I've installed the latest NVidia drivers.

However the titlebar is still missing. So I can't switch between programs nor am I able to move them around.

Yes, yes the Menu > System > Prefences > Appearance > Visual thingy... no go. All three options are disabled.

So since this is something that I've been experiencing since Jaunty... I want to know when a basic titlebar fix will be setup when issues like this arise with whatever the issue is... either theme based, video based, etc.

it sounds like a basic and fundamental thing to need.

BTW, yes before even going for a minimal installation... this happened with the ISOs that I've downloaded from Ubuntu.com.

Anyone have any ideas as to how to fix this WITHOUT having to go through the Appearance menu item?

Right now I am using the Radiance theme and it is still a problem.

Finally, yes it has to be reset everytime I reboot when I used the ISOs.

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-05-17
OK, installing compiz fixed the 'Appearance' disable issue.

Question... why do you need compiz to get the titlebar? Shouldn't it be standard with Gnome?

I have not rebooted yet to see if that has been fixed or not.

Thank you and God bless,
Johanthan

---

### Post by f.zacka on 2010-06-12
Hi all, new to the forum. After hours of looking and trying different things, I have found the cause at least to my problem which sounds similar to yours as the "Title Bars" went missing after an update. In startup applications, I found Devils Pie application set to run with the parameters 
 
(Maximize)
(undecorate)
(focus)
 
After removing this from startup then doing a restart, it has fixed the problem.
Hope I've mentioned this in the right place.
Hope it helps                 ](*,)

---

### Post by avbweb on 2010-07-23
There has been posted a bug for this problem and several workarounds at launchpad.net:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/577482](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/577482)

You can show that you suffer from this bug by clicking "Does this bug affect you?".

---

### Post by joyson20 on 2010-07-26
> **darkmakozu said:**
> I fixed the issue by adding 

/usr/bin/compiz

To the list of start up applications.

Thank you..It worked for me....

---

