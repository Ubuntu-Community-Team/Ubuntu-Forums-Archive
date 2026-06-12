---
title: "No more power management ! Help"
date: 2008-01-07
forum: Hardware &amp; Laptops
---

### Post by damsosor on 2008-01-07
Hi all,
first of all congratulation for the great OS and for the hudge forum.
I'm using Gutsy/gnome on a HP dv2000 laptop, and since the last update I've lost the "battery mode" settings in my power management window. What shall I do ? It used to work great beafore that (about a month ago ?) !
Of course I searched in the forums and got some help on the french ubuntu forum, but it didn't solve my problem.
Here it goes : I have working applets to change CPU frequency and show battery charge/discharge, but in my power management window, the page concerning the battery mode disappeared. Only DC mode and general settings remain. The screen brightness no longer changes by itself, the cpu freq is no more managed, and the notification area no longer shows the battery discharge.
When I run the powertop tool, it says "no acpi information available", but everything is properly installed ! ACPI, APMD, laptop-mode, powernow, cpufreq, etc.
Please help me, I'm going crazy about that ! I can control everything manually, but have no more global policy, it's very annoying to start in "performance mode" and have no more info about the battery in the notification area.
Here's the discussion on the french ubuntu forum : [http://forum.ubuntu-fr.org/viewtopic.php?pid=1439020]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1439020")

I don't understand..... thx in advance for help ! Ubuntu rules anyways !

---

### Post by netrex on 2008-01-07
I have the same problem running ubuntu 7.10 on ASUS laptop.

But my case has some differences:

1.I have not noticed before, but now i got "apm: BIOS not found" in a dmesg output.
2.ACPI, ACPId is running normally.
3.Such tools like powertop also run perfectly.
4.AMDd is no starting, because it can't load apm.ko kernel module.

My notebook always shows that it is running on AC, even if it is runnung on batteries.
It doesn't notify me, when i plug/unplug AC cable.

Before an update, everything was working fine. gnome-power-maneger applet showed battery and had "battery mode" in a settings.

Is it necessary for gnome-power-manager to be apmd running?
Thanks...

---

### Post by damsosor on 2008-01-07
UP !

I've tried lots of things but nothing worked. Anyone has an idea ?

---

### Post by netrex on 2008-01-08
I got it!

Now i can see "battery mode", in a options. And my laptop shows me when it runs on battery and when on AC power...

I did following:

1. Compiled new version of gnome-power-manager (2.20.1) and installed it (may be this step is not needed)
2. restarted HAL (/etc/init.d/hal restart)
3. Restarted gnome session

After that i was able to control battery mode...

After reboot, i have to do all these step again... I don't know why, but i have to restart HAL.
Maybe somebody knows how to avoid it?

---

### Post by netrex on 2008-01-08
I dont think this is a right way, but i added string
"/etc/init.d/hal restart"
in a /etc/rc.local

Now all is working fine...
But, i think, this solution is not very good...

---

### Post by damsosor on 2008-01-08
Thx !
I reinstalled gnome-power-manager and hal in synaptic and then restarted my gnome session 'alt+ctrl+backspace) andeverything's back to normal.
Pfiou ! That was long !
Thanks again. See ya' !

---

### Post by damsosor on 2008-01-08
Euh, after trying, it only works once ! Everytime I restart I have to do that again !
And on top of that, the screen brightness no longer changes when I unplug the AC adapter.....
I suppose there's a bug that will soon be corrected.....

---

### Post by netrex on 2008-01-08
To solve it, i added string
"/etc/init.d/hal restart"
to /etc/rc.local

Did you try that?

---

### Post by Yellow Pasque on 2008-01-08
> **damsosor said:**
> And on top of that, the screen brightness no longer changes when I unplug the AC adapter.....
I suppose there's a bug that will soon be corrected.....

Type the following in a terminal;
```
gconf-editor
```
Now pull down the arrows for /apps/gnome-power-manager.  Here you can access all the power-manager settings. For example, you can click on the backlight folder and you'll see "brightness battery" and "brightness ac".

---

### Post by VO1HL on 2008-01-11
I am having the same problem on a Toshiba R500. This is an orgasmatron portable! After loading Gutsy from Live CD the Power Manager showed "On AC" and "On Battery" and the settings worked as you would expect. Great!! Wonderful!!! Then I loaded compriz-fusion (really cool!! even impressed the wife!!) and - perhaps coincidentally - the "On Battery" tab disappeared from the Power Manager. Like you, the machine appears to be running on AC always. Unplugging from AC does not indicate in anyway. ACPI -V shows the expected values for battery charge, temperature and whether the AC is present or not.

I have read the forums until my eyes bled!! Frustrating enough I thought I should nuke this install and re-install from Live CD. ((Or even [[ULP!]] go to XP - yeachhhhh)).

I have tried the hal restart idea but - and this is odd! - in /etc/init.d I can plainly see the executable hal but when I try to invoke it I get back: sudo: hal: command not found and there is no man entry for hal either. Hmmmmmmm...

I am new to this so please have patience with me!

Any help gratefully received.

73,
Larry

---

### Post by Yellow Pasque on 2008-01-11
hal's the name of a file, not a command. In this case, use something like:
sudo sh hal
I think you might also need to type the word 'start' as an argument after 'hal', though I'm not sure.

> Then I loaded compriz-fusion (really cool!!)
As someone who reveres function over form, I'm shocked at the number of people that install this crap. I really hope this "eye candy at the cost of a fully-functioning system" trend dies soon.

---

### Post by netrex on 2008-01-12
I also use compiz-fusion...
Maybe only compiz-fusion users have this problem?

---

### Post by VO1HL on 2008-01-12
Thanks very much Temujin for the info on hal. 

I did as you suggested and just like netrex I get back the battery icon and a left click shows the battery information. However, this is not working like it did when I first installed Gutsy. Now when I right click on the icon I see the "General" and "On AC" tabs but not the "On Battery" tab (even though I am on battery).

So restarting hal 'sort of' fixes it for the session.

netrex... Further to your question, I have been wondering the same thing and Temujin's comment is to the point. The compiz-fusion thingie is pretty and cool but doesn't really add much value (other than being able to show up Windows users!!). I'd much rather have the power management working correctly.

Perhaps I will reinstall Gutsy and see if (or when!) the power management goes wonky without compiz. Can anyone offer their comments about this strategy??? Anyone else take this step? Is there any way to reload the O/S while maintaining my data files?

Any help gratefully received.

73,
Larry

---

