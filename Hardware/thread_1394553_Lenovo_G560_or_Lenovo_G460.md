---
title: "Lenovo G560 or Lenovo G460"
date: 2010-01-30
forum: Hardware
---

### Post by avilella on 2010-01-30
Hi,

Has anyone installed Linux on a Lenovo G560 or G460?

Cheers.

---

### Post by quixote on 2010-02-01
Have you already checked the [laptop compatibility lists]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo_IBM")?

---

### Post by karansarao on 2010-08-20
Got a Lenovo g460 with Win 7 Home edition preinstalled, downloaded and installed Ubuntu on the first day, I am using Linux after 7 years so a lot has changed (coming from Redhat hair pulling days), installation was a piece of cake after some partition struggling in Windows to get some space.

GRUB works fine , gives dual boot options (default is Linux, have forgotten how to change it, should not be difficult), installed VLC, Audacious, Skype and a few other thingies to get it Media ready, synaptics and debian packages make everything easy.

A few problems:

HDMI Output: hooked up a cable to my Full HD TV, some figuring out but then it worked, however sound still comes out of laptop, for the life of me, I could not figure out how to get the audio out from my TV and not Laptop.

jack sense: Also found out jack sense is well jacked, tried a whole lot of things to get jack sense to work, only ended up screwing something so now even if headphone is plugged in, no sound comes from headphone now only inbuilt speakers, have no idea how to roll back. (If Somebody can help in how to do a clean reinstall of audio drivers or this ALSA thingie with "Dummy can do it" instructions ! and how to get jacksense to work...thanks in advance)

Battery: apparently it just powered down without any warning, hibernate or anything, i guess some settings to lauch actions at 5% or 3% are required, havent figured it out yet.



If i can get the above to work, I am ready to kick Windows!!

---

### Post by amissot on 2010-09-28
hi, i have a lenovo g560 and have exactly the same problems expet sound come out of my head phones but also comes out of my speakers. help would be appreciated.

---

### Post by quixote on 2010-09-30
Re grub: changing the default OS is fairly simple:  [Grub2 docs on configuration]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202").  There's even a gui called "startup-manager" that one can install, although editing one word in /etc/default/grub as per the link seems simpler to me.

I'm terrible on all the multimedia stuff.  When I was fighting with my own sound problems, the [ubuntu wiki]("https://help.ubuntu.com/community/HdaIntelSoundHowto") was helpful, but be careful to follow instructions for lucid since a lot has changed and jaunty instructions won't always work.  Karmic often will.

Power down without warning is not normal.  The commonest cause is that the computer was overheating. You can add a "computer temperature monitor" to the panel and see whether that's really the problem.  If so get one of those cooling bases for laptops.

(Ah, yes, RedHat.  That was where I started too.  Remember having to install a whole damn repos' worth just to get one package or sit there for hours ticking and unticking boxes?)

---

### Post by LorDeadshade on 2010-10-15
Hi,

French user (so excuse me for my perfectible English) of a G560, I have the same problem with jack and headphones, I'm searching for a solution, but if someone have it I'm interesting ;)

---

### Post by dotsha on 2010-12-24
I found that appending to /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel model=thinkpad

... worked for me on Ubuntu 10.10 on G460.

I got the answer from "fabrizzio" at [http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728).

---

### Post by LorDeadshade on 2011-01-06
Thank you very much, it work on my G560 !

---

### Post by Langsdorf on 2011-01-08
headphone jack is now working, but the mic stopped working :-(

if you have problems with random freezes, waking up from hibernate and standby (doesn't wake up, just the cursor is blinking or the screen is staying dark), then this might help you:

```
sudo nano /etc/default/acpi-support
```

change "POST_VIDEO=true" to "false"

---

### Post by Stratok on 2011-02-02
Same problem, ubuntu 10.10, jack works after adding:

options snd-hda-intel model=thinkpad

to /etc/modprobe.d/alsa-base.conf

but internal mic stops workind, but external works.

To get everything working I had to use HDA Analyzer:
it can be used with this 2 lines of code: 
   wget -O run.py [http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)

Quick run: 
   sudo python run.py

Settings as follows:
for (card-0) codec-1
node 0x1f:
audio output:0x10
"out" should be unchecked, but if you check it you will get sound from both, lap speakers and jack simultaneously, If you someday want that.
To get the internal mic working it is more tricky:
node0x14 aud_in:
in connection list select "audio Selector 0x17"

node0x17 aud_sel:
select pin complex 0x1a in connection list,
and move both "val" sliders to 2,3 or 4  to get mic boost, 3 works fine for me.

node 0x1a pin:
check "in" in widget control and change VREF to 80 using the dropdown list. 

close, and don't revert settings. (it will ask you if you want to...)


Now internal mic should be working, but when you plug and unplug an external mic, internal gets disabled, and you need to repeat the instructions to get it working again.
Settings change back to default on every reboot, but Ive not been able to turn this set of instructions into a script or get this settings saved, any ideas?

---

### Post by nilankaraja on 2011-03-19
Hi Stratok,

I have been looking at this thread since my laptop has the same problem.
And when I repeat the things you said I was able to make the headphone jack working but again the internal mic stopped working. When I use hda analyzer and put the setting you said it started working. but the setting go away after reboot..
 
In this link 

[http://ubuntuforums.org/showthread.php?t=1618138](http://ubuntuforums.org/showthread.php?t=1618138)

Some guy has fixed the error with hda analyzer and put it in a one line command using a tool called "hda-verb"

I am not able to do it myself and get it to work. But I think you can try.
If you have succeeded please tell us too.

:D

Nilanka

---

### Post by nilankaraja on 2011-03-19
Hi Everyone,

I fixed the sound problem by adding few lines to the /etc/rc.local file

Now the mic-jack and the internal mic work even after reboot. Used the method used in the thread I posted earlier (hda-verb tool)

My rc.local file looks like this now: If some one can tell if there's a better way that adding this to rc.local file please tell me. :D

[FONT="Courier New"]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x14 SET_CONNECT_SEL 0
/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x17 SET_CONNECT_SEL 0
/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x17 SET_PIN_WIDGET_CONTROL 3
exit 0[/FONT]

---

### Post by xenico on 2011-03-24
That solution helped me, until there was another alsa update yesterday. Today I hear sound just from speakerboxes with the headphones plugged in...
Does any one have a hint how to solve that issue?

thanks,
xenico

---

### Post by qednick on 2011-04-06
Just bought mine over the weekend. Really really pleased so far.

It came with Win7 pre-installed. Took a full 2 mins or so to boot up and about 1 full minute to shut down. During my "brief" Win7 experience, I tried to launch Internet Explorer. I clicked the icon only to be presented with a round spinning icon. I clicked several times - no luck. About 2 minutes later, 6 I.E. windows suddenly appeared. So much for a dual boot system... I just got out my Xubuntu install disk and wiped the damned thing!!

Only quirks I noticed after install were black screen (even though live CD worked great). So I promptly reinstalled again but this time made sure I was hard-wired to the internet so updates can be downloaded during install. 

After that, everything worked great. Wireless. DVD burner. Track pad with two-finger scrolling. Sound input/output (inc. headphone jack). Web cam. Only thing I haven't tried yet is the sound on the HDMI output (as mentioned by other poster). 

So I'm not sure if it's because I installed Xubuntu rather than full-blown Ubuntu but I haven't experienced any of the other issues mentioned on this thread.

On another note... I installed Virtual Box with WinXP (occasionally I have to go to the dark side for programming purposes). With the base 2 gig of ram, it runs WinXP in VB far faster than it did Win7 natively. 

Overall, I am EXTREMELY pleased with the G560 and would highly recommend one to anyone planning to get a low-cost but fast linux laptop. I ordered a full 8GB of ram which should arrive tomorrow by UPS. So next step will be to see how upgrading goes.

---

### Post by nilankaraja on 2011-04-12
Hi Xenio, I am using a fully updates kubuntu 10.10 version with alsa verion 1.0.23+dfsg-1ubuntu4 (synaptic says) The solution helped me and my headphone jack and external mic works even now.

---

### Post by marce99 on 2011-04-14
Hi, well, first of all, i'm new with all this linux stuff. I tried Ubuntu 10.10 32bits on my lenovo g560. Everything was perfect, in order to have wifi i had upgrade drivers, and that was all. My first problem was with the sound, which i repaired reading one of the answers below. But then i started getting error messages every time i uninstalled or installed new programs. These errors where always related to the same file, i don't remember it's exact name, I think it was linux conexant (sth related to audio drivers). So i read that some people removed the drivers and then installed them again in order to solve the problem, so to rom i decided to reinstall the whole thing. When i removed it i had no more errors, even emesene started working (it couldn't connect before). A user had the same experience so far. The problem was reinstalling the sound drivers again. I get errors in the same step always. The worst thing is that i don't know which is exactly the name of my sound car. On windows seven, through aida64, i got conexant cx20585 or intel high definition audio... but i cannot make this thing work again. I'm thinking of format... maybe stay with windows seven and XP as a second option, because my linux experience with this notebook was terrible... maybe i should try my old desktop pc. (before trying this ubuntu 10.10 x32bits, i tried open suse 64bits, and i had problems with wifi.)
The guide I used is this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 Maybe it'll help someone else, i know it's a good guide, but I keep getting errors every time i try with sth different.

My other problem is that i have to use the same command always that i turn on my notebook using the battery in order to get wifi working well:
sudo iwconfig eth1 power off

I only want to make sound work again, so if someone know for other possible solution, please let me know.

---

### Post by f3dja on 2011-07-14
> **nilankaraja said:**
> Hi Everyone,

I fixed the sound problem by adding few lines to the /etc/rc.local file

Now the mic-jack and the internal mic work even after reboot. Used the method used in the thread I posted earlier (hda-verb tool)

My rc.local file looks like this now: If some one can tell if there's a better way that adding this to rc.local file please tell me. :D

[FONT=Courier New]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will &quot;exit 0&quot; on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x14 SET_CONNECT_SEL 0
/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x17 SET_CONNECT_SEL 0
/usr/local/bin/hda-verb /dev/snd/hwC0D1 0x17 SET_PIN_WIDGET_CONTROL 3
exit 0[/FONT]

try: 
hda-verb /dev/snd/hwC0D1 0x14 SET_CONNECT_SEL 0 
hda-verb /dev/snd/hwC0D1 0x17 SET_CONNECT_SEL 0 
hda-verb /dev/snd/hwC0D1 0x17 SET_AMP_GAIN_MUTE 0xb003 
 instead!

---

### Post by nilankaraja on 2011-07-14
> **f3dja said:**
> try: 
hda-verb /dev/snd/hwC0D1 0x14 SET_CONNECT_SEL 0 
hda-verb /dev/snd/hwC0D1 0x17 SET_CONNECT_SEL 0 
hda-verb /dev/snd/hwC0D1 0x17 SET_AMP_GAIN_MUTE 0xb003 
 instead!

Hi f3dja,

My lenovo g460 sound works fine with no problems with current changes. Can you please tell me what's the advantage of adding the above lines? I see only the last line is different.
Thank you.

---

### Post by f3dja on 2011-07-15
Well,  the internal mic-in of my g560 was not working... About 1 year ago I applied the headfon jack fix (options snd-hda-intel model=ideapad to alsa-base.conf); I can't remember if the mic-in was working back then... but now (ubuntu 10.10) it did not work! I googled and found this post; i ran the hda-analyzer ([http://www.alsa-project.org/hda-analyzer.py](http://www.alsa-project.org/hda-analyzer.py)) and realized that the settings proposed by Stratok fixed the problem; however these settings were lost after reboot.  I tried your fix; however the last line (hda-verb /dev/snd/hwC0D1 0x17 SET_PIN_WIDGET_CONTROL 3) did not do anything on my system. Changing the line to (hda-verb /dev/snd/hwC0D1 0x17 SET_AMP_GAIN_MUTE 0xb003) did the trick for me since it enabled the mic "boost". (It sets the "val" sliders in node0x17 to 3).   Fedja

---

### Post by pneaveill on 2011-08-06
Cannot find it now, but saw a couple of months ago somewhere that the Lenovo may use any of several audio chipsets.  Mine in particular uses the ```
conexant cx 20585 and the Intel IbexPeak hdmi.
```  I ran the previous stuff and the jack is not working properly in ubuntu, but works fine in win7.

-------- edit ------------

[http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-G460-Linux-driver/m-p/307728) reveals this:

```

Add to end of file /etc/modprobe.d/alsa-base.conf the follow line:
 
options snd-hda-intel model=thinkpad
```


Not certain why it worked this time and not previously, but is working. Thanks

---

