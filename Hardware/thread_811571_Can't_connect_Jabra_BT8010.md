---
title: "Can't connect Jabra BT8010"
date: 2008-05-29
forum: Hardware
---

### Post by montgoss on 2008-05-29
I can't get my headset (BT8010) to pair with my desktop (8.04).

I put the headset into pairing mode.  From "Bluetooth Applet 0.25" icon, if I select "Browse Devices", I see "Jabra BT8010" in the list.  Clicking "Connect" here throws an error, but I believe that's because this dialog is for file transfers and such that the headset wouldn't support.  From what I've read, I should instead go to "Preferences" and "Services" tab and select "Audio service".  It is marked as running, but the headset doesn't show up in the list when I highlight "Audio service".  So, I fall back to the command line...

```
montgoss@montgoss-desktop:~$ hcitool scan
Scanning ...
	00:1A:45:1C:58:DE	Jabra BT8010
montgoss@montgoss-desktop:~$ sudo hidd --connect  00:1A:45:1C:58:DE
Can't get device information: Success
montgoss@montgoss-desktop:~$ sudo hcitool cc 00:1A:45:1C:58:DE
montgoss@montgoss-desktop:~$ sudo hcitool auth 00:1A:45:1C:58:DE
HCI authentication request failed: Connection timed out
montgoss@montgoss-desktop:~$ sudo hciconfig hci0 reset
montgoss@montgoss-desktop:~$ sudo hcitool cc 00:1A:45:1C:58:DE
montgoss@montgoss-desktop:~$ sudo hcitool auth 00:1A:45:1C:58:DE
HCI authentication request failed: Connection timed out
```
If I do the "hcitool auth" a split second after the "hcitool cc", I see a little bubble popup from the Bluetooth Applet icon that has a button saying "Enter passkey".  That bubble disappears very quickly.  The one time I managed to click the button before the bubble disappeared, I did get a dialog to enter the passkey.  But that dialog auto-closed before I had a chance to enter the passkey.  I think my system is just toying with me.  :confused:

Any ideas?  Any other info you need?

---

### Post by poserslipjack on 2008-06-14
Hey,

Any luck getting your Jabra BT8010 headset working with Hardy? Once I added something like...

```

pcm.a2dp {
	 type bluetooth
	 device 00:11:22:33:44:55
	 profile "a2dp"
}

```

..to my ~/.asoundc, I could make it pair (through the GUI) just by starting up an application that requests the right profile.  The easy way is...

```

aplay -D a2dp

```

...where the -D argument matches whatever came after the "pcm." in your ~/.asoundrc profile for the device.  This command will hang, of course, since you're not actually giving it a file to play...but it serves to initiate the pairing.  You can kill aplay with Ctrl-C.

Or, you can do it the fun way.  Redirect gstreamer to that same device...

```

gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "alsasink device=a2dp"

```

...then start up rhythmbox and play a track.  It should prompt you for a passkey, and then begin playing through the headset when it's ready.  You can return gstreamer to normal with...

```

gconftool --type string --set /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```

Unfortunately, I can't get this same trick to work with a bi-directional (SCO-encoded?) headset profile.  It's the opposite nightmare from Gutsy, where headsets worked, but a2dp stereo bluetooth was a big pain.  *shrug*  

Anyway, I've added...

```

pcm.headset {
	 type bluetooth
	 device 00:11:22:33:44:55
	 profile "headset"
}

```

...to my ~/.asoundrc as well, then I fire up Skype (which doesn't use gstreamer, so there's no need to worry about all that gconftool nonsense), and I am immediately prompted about the bluetooth pairing.  

(To make sure, before starting Skype, I removed the previous pairing by right-clicking the bluetooth icon in the system panel and going to Preferences > Services > Audio Services > Jabra BT8010 > Remove > Delete, then clicking the first panel, selecting Jabra BT8010, clicking Disconnect, then Delete > Delete.  I also removed all pairings from the headset itself by clicking menu button on top of the device, scrolling to Settings, clicking the wheel-button, scrolling to paired devices, clicking the wheel-button, clicking the wheel-button again on "Delete All," then clicking it one final time on "Are you sure?"

After Skype starts up, I right-click the Skype icon in the system panel, go to Options, click on Sound Devices, set "Sound Out" to "headset," Click Apply, then click 'Make a test call."  Again, everything works fine.  If your system microphone is unmuted in alsamixer, you can even record your voice (through the system mic), and listen to it play back (through the headset).

Unfortunately, the headset microphone doesn't seem to work.  If I go back to the Sound Devices window, choose "default" for Sound Out and "headset" for Sound In, Apply, and click "Make a test call," I can hear fine through my system speakers, but audio-capture fails. (And, after that, Skype appears injured.  I had to kill -9 it....)

Presumably, a simpler test would be...

arecord -D headset -f S16_LE -r 16000 ~/tmp.wav
<talk into the mic for a while>
<ctrl-c>
aplay -D headset -f S16_LE -r 16000 ~/tmp.wav

...which gives the same results.  The aplay command works if there is an appropriate .wav file to, but the arecord command fails, even if that is the command that initiates the bluetooth binding.

Thoughts?

---

### Post by AcIDx0 on 2008-10-05
After long searching I found a lead:
[http://forum.xda-developers.com/showthread.php?t=302202&page=6](http://forum.xda-developers.com/showthread.php?t=302202&page=6)

What this guy basically says, is that due to that BT8010 has multiple profile support (read a2dp and headset), it gets confused on how the hell you are trying to use a mike with a2dp. 
I think the answer is that we should change the "profile" in .asoundrc  from "auto" to specific profile. Any linux gurus to guide us here?

---

