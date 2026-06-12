---
title: "DELL Vostro 1014 |||||| Cannot Select Audio Input Source (Microphone)"
date: 2010-04-19
forum: Hardware
---

### Post by linuxyogi on 2010-04-19
Hi, 

[B]Problem has changed after an alsa upgrade.

Getting the mic to work is not the need of the hour anymore. [/B]

I installed Ubuntu 10.04 on my friend's Dell Vostro 1014.

The problem is

When a headphone is plugged into the headphone jack there is no audio . Previously (i.e. before upgrading alsa the headphone jack was outputting audio but the problem was that sound was coming from both the headphones & the internal speaker simultaneously.

---

### Post by linuxyogi on 2010-04-19
This is the laptop ---------- 

[[SIZE="5"][SIZE="4"]**http://www1.ap.dell.com/in/en/business/notebooks/laptop-vostro-1014/pd.aspx?refid=laptop-vostro-1014&cs=inbsd1&s=bsd**[/SIZE][/SIZE]]("http://www1.ap.dell.com/in/en/business/notebooks/laptop-vostro-1014/pd.aspx?refid=laptop-vostro-1014&cs=inbsd1&s=bsd")

---

### Post by linuxyogi on 2010-08-09
These are the details of the laptop --------

uname -a
Linux mylaptop 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux



aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0



dpkg -l |grep alsa
ii alsa-base 1.0.22.1+dfsg-0ubuntu3 ALSA driver configuration files
ii alsa-firmware-loaders 1.0.22-0ubuntu1 ALSA software loaders for specific hardware
ii alsa-oss 1.0.17-3 ALSA wrapper for OSS applications
ii alsa-source 1.0.22.1+dfsg-0ubuntu3 ALSA driver sources
ii alsa-tools 1.0.22-0ubuntu1 Console based ALSA utilities for specific hardware
ii alsa-tools-gui 1.0.22-0ubuntu1 GUI based ALSA utilities for specific hardware
ii alsa-utils 1.0.22-0ubuntu5 ALSA utilities
ii bluez-alsa 4.60-0ubuntu8 Bluetooth audio support
ii gstreamer0.10-alsa 0.10.28-1 GStreamer plugin for ALSA


head -n 1 /proc/asound/card*/codec#*
Codec: Conexant CX20583 (Pebble HSF)

---

### Post by lidex on 2010-08-09
Try this. If it doesn't work there are other model options to try. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by linuxyogi on 2010-08-12
> **lidex said:**
> Try this. If it doesn't work there are other model options to try. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=laptop position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Tried "options snd-hda-intel model=laptop position_fix=1 enable=yes".
Still no audio from the headphone jack.

Also tried the following  ---

options snd-hda-intel index=-2 model=dell-laptop
options snd-hda-intel index=-2 model=laptop

but no luck. 

:(

Ready to try other options.:-k

I noticed that the inbuilt speaker of the laptop is nothing but the left channel.

pavumeter shows activity in both L & R channels.

About choosing a profile in pavucontrol : None worked. I mean I tried all the profiles one by one but none made the headphone jack to output audio.

I have raised all the controls of the alsa mixer to high after choosing the soundcard.

Tell me something, was upgrading alsa a wrong move. The headphone jack is what he uses to connect his 2.1.
He is not entirely happy, you know. I should have asked you first.  

Also, what should I select in  gstreamer-properties ? Alsa or Pulse ?
I tried both, hoping one of those may solve the issue. Both produces sound but only through the inbuilt speaker.
 
It will be very nice if give me 3-4 options (at a time) to try because I get to configure that laptop only once a week & my fried is not a tech guy. I actually asked him to mail me his alsa-base.conf which I modified & mailed him back. Then he replaced the old one with this one. I by the way wrote all the commands which he copy pasted.

---

### Post by linuxyogi on 2010-08-13
Where are you? ):P

---

### Post by lidex on 2010-08-13
> **linuxyogi said:**
> Where are you? ):P
Working ridiculous hours.
These are not the correct syntax:
> Also tried the following ---
options snd-hda-intel index=-2 model=dell-laptop
options snd-hda-intel index=-2 model=laptop

It should look like this:
```
options snd-hda-intel model=dell-laptop
```
So those aren't going to work for you. I would, for the moment, leave gstreamer on pulse. Try this in alsa-base.conf:
```
options snd-hda-intel model=dell-vostro
```
Make sure to remove any other switches you may have added. Reboot. No help?
Use the link in my sig to upgrade alsa to v 1.0.23

---

### Post by linuxyogi on 2010-08-14
> **lidex said:**
> Working ridiculous hours.
Try this in alsa-base.conf:
```
options snd-hda-intel model=dell-vostro
```
Make sure to remove any other switches you may have added. Reboot. No help?
Use the link in my sig to upgrade alsa to v 1.0.23

First of all THANKS.

Unfortunately "options snd-hda-intel model=dell-laptop" didn't work.
What happens is after reboot alsamixer won't appear anymore.
I am very sorry but I don't remember the error code of alsamixer exactly.
He is gone with his laptop. But I think it printed something like "directory not found".
The rest is same.

[CENTER]
_About Alsa Upgrade_[/CENTER]
I have already upgraded this laptop's alsa installation using your script. That was the very first thing I did. Before upgrading alsa the problem was that sound was coming simultaneously from both the inbuilt speaker & headphone. After alsa upgrade there is no audio from the  headphone jack. The inbuilt speaker is playing as usual.

If you are too busy please take your time to respond. This can wait.

---

### Post by lidex on 2010-08-14
Did you try dell-vostro?

---

### Post by linuxyogi on 2010-08-14
> **lidex said:**
> Did you try dell-vostro?

Yes, **dell-vostro**
Sorry for the confusion.

---

### Post by lidex on 2010-08-15
Normally when there is a jacke-sense issue, choosing the correct model in alsa-base.conf does the trick, but then that option needs to be enabled. Using gnome-alsamixer, you can do that.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by linuxyogi on 2010-08-16
> **lidex said:**
> 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

All the elements were already enabled. I just deselect/reselected them.
All the levels were high already. I moved them just to check if there is any audio from the headphone jack. But still no audio.
:cry:




```
options snd-hda-intel model=dell-vostro
```


*Because dell-vostro didn't work. I actually removed it. Am I supposed to open gnome-alsamixer with this line included in alsa-base-conf ?*

---

### Post by lidex on 2010-08-16
I'll give you two options. Either use the alsa-upgrade link in my sig and get v 1.0.23 or use this link to install the linuxant drivers. I'm leaning toward the latter.
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by linuxyogi on 2010-08-16
> **lidex said:**
> I'll give you two options. Either use the alsa-upgrade link in my sig and get v 1.0.23 

Trust me, I have already done that.

1. download the script and save it somewhere
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0

No errors.

Again, before running this script both the internal speaker & the headphone jack were playing sound simultanously. After running the script mentioned in your signature the headphone jack is now totally mute. 

> **lidex said:**
> use this link to install  the linuxant drivers. I'm leaning toward the latter. 

Okay, I will try that or I'll just tell him that the audio hardware of his laptop is "partially supported" on linux which not entirely incorrect.

Thanks for all your support so far.
 In future, if you find a solution regarding this specific hardware kindly visit this thread & post the link.

Thanks again.

---

### Post by lidex on 2010-08-17
I think I can trust you, but did you try the alsa-base.conf edits with v 1.0.23?
As for linuxant, it should work. In any event have a look at this page and file a bug report so this can get fixed:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by linuxyogi on 2010-08-17
> **lidex said:**
> I think I can trust you, but did you try the alsa-base.conf edits with v 1.0.23? 

I actually upgraded alsa using your script before writing about this problem in my surround sound thread. I thought let's upgrade alsa and if that doesn't solve the issue then I will write about it here. So, then wasn't I editing the alsa-base.conf edits with v 1.0.23 ?

---

### Post by lidex on 2010-08-17
> **linuxyogi said:**
> I actually upgraded alsa using your script before writing about this problem in my surround sound thread. I thought let's upgrade alsa and if that doesn't solve the issue then I will write about it here. So, then wasn't I editing the alsa-base.conf edits with v 1.0.23 ?

According to post #3, you have version 1.0.22.1

---

### Post by linuxyogi on 2010-08-17
> **lidex said:**
> According to post #3, you have version 1.0.22.1

Open the alsa upgrade script with a text editor & you will find this ------------

This script is not compliant to Ubuntu official .deb package handling. This script overwrites the existing files and modules.
# [COLOR=Red]You won't see any changes on the revisions if you run e.g. synaptics..[/COLOR]
# If there are official ALSA updates supplied by Ubuntu repositories or kernel changes, these will overwrite your manual ALSA upgrade - 
# you need to re-run this script in this case.
# [COLOR=Red]You can check the Alsa revision by typing "cat /proc/asound/version" or "alsactl --version" or the utils by "aplay --version" [/COLOR]

I guess this is probably why "dpkg -l |grep alsa" is not showing  the latest version.
Just to avoid confusion I will post the output of  [COLOR=Black]"[/COLOR][COLOR=Black]cat /proc/asound/version" or "alsactl --version[/COLOR]" as suggested by the author of the script, next time my friend visits with his laptop.

---

### Post by linuxyogi on 2010-08-27
After installing the linuxant driver sound is back on the headphone jack but it still doesn't mute the internal speaker upon jack insertion. 

Anyways, at least sound is restored.

Thanks.

---

### Post by cazo on 2010-10-13
For everyone on Maverick Meerkat, Dell Vostro 1410, I just made:

a) [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)
b) install .deb (you can get a warn, go ahead!)
c) replace in /etc/modprob.d/alsa.conf
options snd-hda-intel model=dell position_fix=0 enable=yes
by
options snd-hda-intel model=dell-vostro position_fix=0 enable=yes
d) rebbot

and anything works fine!

thx all

---

### Post by leoharvey on 2010-11-21
Thank you.  I had the same issue and merely added the line of code you suggested....problem solved.

---

### Post by lidex on 2010-11-21
> **cazo said:**
> For everyone on Maverick Meerkat, Dell Vostro 1410, I just made:

a) [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)
b) install .deb (you can get a warn, go ahead!)
c) replace in [COLOR="Red"]/etc/modprob.d/alsa.conf[/COLOR]
options snd-hda-intel model=dell position_fix=0 enable=yes
by
options snd-hda-intel model=dell-vostro position_fix=0 enable=yes
d) rebbot
and anything works fine!
thx all

That filename should actually be:
```
/etc/modprobe.d/alsa-base.conf
```

---

