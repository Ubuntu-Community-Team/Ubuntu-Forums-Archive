---
title: "Bluetooth headset"
date: 2008-09-16
forum: Hardware
---

### Post by dagring on 2008-09-16
I have a nokia bluetooth headset. The headset is paired and appears in the list of bonded devices. The problem is that I can't find the device anywhere in the sound settings. Maybe I look at the wrong places, but the goal of attaching the heaset (+built in mic) is to use it with Skype. 

Can anybody give me a hint where I can set up the headset?

dagring

---

### Post by whymichael on 2008-10-02
I am trying to do the same thing. I'm not there yet, but I do have all of my computer's audio playing through my headset using PulseAudio. I don't know if this is the best way to do this, but it works for me.

**Install PulseAudio**
[http://wiki.archlinux.org/index.php/PulseAudio]("http://wiki.archlinux.org/index.php/PulseAudio")

**Setup PusleAudio to manage all/most of your audio streams**
Note that this is a revised version of the guide. You should be able to ignore the original unless you have problems:
[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

**Setup PulseAudio to redirect all of you audio streams from you sound card**
Run "PulseAudio Device Chooser > Configure Local Sound Server"
Match my settings:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=87075&stc=1&d=1222989301[/IMG]

**Tell ALSA where your headset is located**
[Change the red text as necessary]
Edit "/home/[COLOR="Red"]michael[/COLOR]/.asoundrc" so that it looks like:
```

# ALSA library configuration file

pcm.auto {
    type bluetooth
    device [COLOR="Red"]00:1C:EF:04:DF:FB [/COLOR] [COLOR="Red"]## This is the MAC address of your headset[/COLOR]
    profile "auto"
}


# Include settings that are under the control of asoundconf(1).
# (To disable these settings, comment out this line.)
</home/michael/.asoundrc.asoundconf>

```


At this point if you run ```
pactl load-module module-alsa-sink device=auto
``` under terminal. PulseAudio will connect to your headset (A restart maybe required). If you open the "Device Chooser > Volume Control" GUI, you can manually toggle individual audio streams from your speakers to your headset by right clicking on them. 

**Optional**
I recommend creating a bash script for connecting to your headset. The script can then automaticly run when you login and/or you can create a launcher to connect if your headset was not on at login:

```
sudo gedit /usr/bin/PulseAudioConnectBluetooth.sh
```

Copy, paste, and save the following into the file
```

#!/bin/sh
pactl load-module module-alsa-sink device=auto

```

Exit and make the script executable with:
```
sudo chmod 755 /usr/bin/PulseAudioConnectBluetooth.sh
```

**To connect your headset at startup:**
   System > Preferences > Sessions > Add
   Paste "PulseAudioConnectBluetooth.sh" into the "Command" text box

**To create a launcher for connecting your headset:**
   Right click your "Applications" menu
   Edit Menus > New Item
   Paste "PulseAudioConnectBluetooth.sh" into the "Command" text box


**If you want all audio streams to go to your headset by default**
In terminal enter:
```
sudo gedit /etc/pulse/client.conf
```

Change the line "; default-sink =" to "default-sink = alsa_output.auto"

Save.

Michael

---

### Post by dagring on 2008-10-05
Thanx for your reply. I tried a similar approach to the problem before you answered the thread. I got it working, but the quality of the sound was terrible. I do not know whether this is caused by my BT headset because it's three years old, or if this is caused by wrong setup. 

I don't mind making a little adjustments to files, installing programs etcetera, but I mind a lot of that stuff at the same time. It's too much for my capacity. I can't understand why they doesn't make an easy setup for this. There must be a lot of people using Skype or some other client for doing web calls?

dagr

---

### Post by whymichael on 2008-10-05
My sound quality is fine, but I can't get the microphone to work. Did you get your microphone working?

---

### Post by dagring on 2008-10-05
Yes I got it working. I am not quite sure how I got it working, but I made this .asoundrc file:

---------
pcm.bluetooth {
   type bluetooth
   device 	00:08:C6:4A:57:45	
profile "auto"
}
------------
That's it. I played with some of these test trying to find my bluetooth devices and so on, suddenly the BT headset appeared as an option in Skype, and it workeed! When I called my son over Skype with the headset, he said: -Daddy, it sounds like you're in a war zone! 

I think this technology isn't ripe yet, but its frustrating and glorious when you get it working.

Is your headset paired?


dagr:)

---

