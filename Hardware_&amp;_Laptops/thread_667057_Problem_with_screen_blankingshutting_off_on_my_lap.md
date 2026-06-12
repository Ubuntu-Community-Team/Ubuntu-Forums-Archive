---
title: "Problem with screen blanking/shutting off on my laptop"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by bitter_mike on 2008-01-14
Hey all,

I've got a Dell Inspiron E1505, running Ubuntu 7.10. I've got an ATI Mobility Radeon X1400 and I'm using the restricted ATI driver. My problem is that no matter what settings I adjust in the screensaver preferences and power saving options, my screen blanks (is still powered on, but is totally black) after about 10 minutes. After about 30, the monitor does shut off, but only after 30 minutes of idle time. It won't even shut off when I close the lid.

I've tried adjusting the settings in the power manager to never blank my screen, regardless of idle time, I've tried adjusting the time longer and I've made sure screen savers are disabled and still, it blanks after 10 minutes of idle time. Ideally, I'd like to know how to change it so it never blanks due to idleness and to actually fully turn off (the monitor, not the computer) when I close the lid. I've tried this command:

xset dpms force off

and I get an error. Any help would be appreciated. Thanks.

---

### Post by bitter_mike on 2008-01-15
Anyone?

---

### Post by Defender23 on 2008-01-15
I have that laptop and have no problems. But my friend used to have the old model of the Inspiron 6400 or whatever it is. He started having the same issues with his laptop the screen just blanks it was a hardware issue he had to call Dell up and get them to fix it for him. He also did some research and foundout that Dell Inspiron its a common problem with them.
I hope that helps you in some way

---

### Post by bitter_mike on 2008-01-15
Well I know it functions perfectly in Windows XP and responds to the settings I change there. That leads me to believe its a software problem.

---

### Post by Defender23 on 2008-01-15
I would try a little test unless you have been using windows at the same time I would try spending like 30 minutes on windows doing stuff to see if you get the same problem. Otherwise I would say try reinstalling ubuntu. Because I seriously don't have any problems running ubuntu and I have the same specs as you it looks like.

---

### Post by Yellow Pasque on 2008-01-15
Ubuntu's power prefs are rather lacking IMHO. All your power settings can be accessed through a program called gconf-editor, so fire up a terminal and type in 'sudo gconf-editor'

Once you've got that up follow this path: /apps/gnome-power-manager/timeout/sleep_display_ac
Change that value to 0 to disable the display shutting off. You'll also see other useful things like the lid_ac key in the 'buttons' folder that you can set to blank to turn the display off.

---

### Post by bitter_mike on 2008-01-15
There's a lot of really cool options in there (thank you) but changing them doesn't do anything. The lid setting is already set to blank (it doesn't blank when I close the lid) and adjusting the timeout before the display goes to sleep doesn't change anything either. There's gotta be something else over riding the settings. I just wish I knew what.

---

### Post by Yellow Pasque on 2008-01-16
Perhaps the X settings are overriding it.

It could also be a problem with HAL.

---

### Post by bitter_mike on 2008-01-16
Do you know where X's settings for that are set? Or if they can be set at all.

---

### Post by Yellow Pasque on 2008-01-16
> **bitter_mike said:**
> Do you know where X's settings for that are set? Or if they can be set at all.
Try looking at this post. The file referred to is /etc/X11/xorg.conf
[http://ubuntuforums.org/showpost.php?p=4094012&postcount=18](http://ubuntuforums.org/showpost.php?p=4094012&postcount=18)

---

### Post by bitter_mike on 2008-01-16
I looked at that post and gave it a try, but no good. I checked the xorg.conf man file and it says that those options can be set manually by using the command xset. I tried that and got this error:

mike@blackhole:~$ xset dpms force standby
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  146 (DPMS)
  Minor opcode of failed request:  6 (DPMSForceLevel)
  Serial number of failed request:  10
  Current serial number in output stream:  12

I get that no matter which option I try (standby, suspend, off and even on). Anyone know what it means?

---

### Post by Yellow Pasque on 2008-01-16
Are you using *Option "DPMS"* in the Monitor section of your xorg.conf?

---

### Post by bitter_mike on 2008-01-16
Yup. At first the option was set like this:

Option       "DPMS"

That didn't work and in the man file it said that variable was a boolean so I tried this:

Option       "DPMS"        "true"

And that didn't work either.

---

### Post by Yellow Pasque on 2008-01-16
Try removing it or setting it to false and restarting. Then, you should hopefully be able to use xset.

---

### Post by bitter_mike on 2008-01-17
I'm checked the man file again and it was pretty clear that you wanted that on to enable the screen's power saving features (turning it off after being idle for a while).

But I tried it anyways and got the exact same errors as above.

---

### Post by usergroup81 on 2008-01-17
I also have an E1505 with ati X1300. I use to get blank screen every ten minutes even watching movies in full screen.  After diggin around I tried the method of adding the following to my /etc/X11/xorg.conf file that Temüjin mentioned 	

> Section "ServerFlags"
  Option "BlankTime" "0"
  Option "StandbyTime" "0"
  Option "SuspendTime" "0"
  Option "OffTime" "0"
EndSection

For the lid not powering down when you close it, try this link, it worked for me. Remember backup all your files that you are modifying!!!

[http://ubuntuforums.org/showpost.php?p=1903680&postcount=4]("http://ubuntuforums.org/showpost.php?p=1903680&postcount=4")

The blank screen goes away now but when it's idle the screensaver kicks in but the screen doesn't turn off at all until I close my lid. I'm wondering if I can change the "OffTime" to 200 or something else to see if it'll work.

---

### Post by bitter_mike on 2008-01-17
Ya, I already gave that a try but no dice. I'd bet $20 that its the fglrx driver thats causing the problem. It makes my display really nice, but it has some known bugs that prevent the computer from hibernating or going into standby.

---

### Post by usergroup81 on 2008-01-18
What about Catalyst 7.12? I tried it out with Envy, but had major video playback problems so I reverted back to 7.11 in the Repo instead.

---

### Post by bitter_mike on 2008-01-20
What is Catalyst? As far as I know, I'm not using it.

---

