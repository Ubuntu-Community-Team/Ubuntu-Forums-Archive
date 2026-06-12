---
title: "Lenovo U160: how do I disable SSC?"
date: 2011-07-12
forum: Hardware
---

### Post by gamma-andromedae on 2011-07-12
Hello everybody,
 
yesterday, I quite successfully installed Ubuntu 11.04 (64bit) on my Lenovo U160.
 
So far, I've encountered only two (obviously well-known) compatibility issues.
 
The WLAN problem was easily solved by blacklisting acer_wmi.
 
The second issue, concerning the U160 resuming from suspend mode with a backlit, but blank screen, can, as far as I understand the related discussions, be worked around by putting the line
 
options i915.lvds_use_ssc=0
 
in some config file in /etc/modprobe.d ... is that correct so far?
 
What I (as a newbie) don't understand is *where* exactly I have to put this line?
 
Is it OK to create a new file 'i915-disable-ssc.conf' inside modprobe.d that contains just that one line!? Or do I have to 'sudo nano' this line to another, already existing config file!?
 
Thank you for any hint and kind regards,
 
gamma-andromedae
Wedel near Hamburg, Germany

---

### Post by SunMade on 2011-07-13
I disabled both suspend and and hibernate this way:

1. open a terminal window pressing [COLOR=Red]ctrl-alt-t[/COLOR]

2. copy-paste or type this:
[COLOR=Red]gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy[/COLOR]

3. In the text find the [COLOR=Red]<allow_active>[/COLOR] tag and change [COLOR=Red]"yes"[/COLOR] to [COLOR=Red]"no"[/COLOR] for both suspend and hibernate

4. save the text and reboot


Also I blacklisted acer_wmi this way:

1. open a terminal window pressing [COLOR=Red]ctrl-alt-t[/COLOR]

2. copy-paste or type this:
[COLOR=Red]gksudo gedit /etc/modprobe.d/blacklist.conf[/COLOR]

3. In the text insert this line:
[COLOR=Red]blacklist acer_wmi[/COLOR]

4. save the text and reboot

BUT still the BCM4313 wifi was hardware blocked!!! (rfkill list). 
Finally I found this so-called "hardware button" blocking the wifi in some special Lenovo popup-menu i windows 7 when you press Fn-F5

So I need to have the windows 7 that came with this Lenovo laptop installed only to switch on my wifi if it somehow gets hardware blocked again - very annoying and waste of diskspace.

In windows 7 partition handling I managed to shrink windows and recovery, so I have 350GB left for ubuntu (dual-boot). My harddrive is 500GB originally.

---

### Post by gamma-andromedae on 2011-07-13
Hi SunMade,
 
thanks for your suggestions.
 
For me, just blacklisting acer_wmi worked fine. No further problems with WLAN!
 
(Having to keep Win 7 just for that purpose is sad indeed. I decided to delete all NTFS partitions during the Ubuntu setup.)
 
Concerning suspend & hibernate, I do not want to disable but to *use* them. So, I'll try the modprobe hack first, later today.
 
Kind regards!

---

### Post by gamma-andromedae on 2011-07-14
In order to fix the blank screen after resume problem, yesterday I wrote a new file 'i915-disable-ssc.conf' into /etc/modprobe.d containing the single line
 
options i915.lvds_use_ssc=0
 
and restarted. Unfortunately, this did NOT fix the resume problem for me.
 
Any ideas what might still be going wrong here, or what I am doing wrong!?

---

### Post by mp80 on 2011-08-03
I found that following what was posted [here]("http://forums.linuxmint.com/viewtopic.php?f=49&t=75306") solved the problem - it's pretty much what you have already tried, but with a bit extra. In /etc/modprobe.d I created the file i915-disable-ssc.conf containing the line:

options i915 modeset=1 lvds_use_ssc=0

I then ran:

sudo update-initramfs -k all -u

and restarted. Now if I resume for a suspend the screen works as expected again - although it took a few seconds to return from black! I'm not sure if it's including "modeset=1", or running update-initramfs that helped over what you'd previously done, but hopefully this will work for you.

---

