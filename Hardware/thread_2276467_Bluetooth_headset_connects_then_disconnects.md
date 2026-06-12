---
title: "Bluetooth headset connects then disconnects"
date: 2015-05-02
forum: Hardware
---

### Post by b00n on 2015-05-02
I have an Intel NUC with both an internal WiFi/Bluetooth adapter and an external Bluetooth adapter.  With the internal adapter, I can turn on a Bluetooth headset and it auto-connects.  With the external adapter (configred as described here: [http://ubuntuforums.org/showthread.php?t=2276242](http://ubuntuforums.org/showthread.php?t=2276242)), it does not auto-connect, though I can connect it  manually by going to [FONT=courier new]System Preferences > Bluetooth[/FONT], select the headset, and click [FONT=courier new]Connection > On[/FONT].

I found [http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset](http://metricrat.co.uk/xubuntu-bluetooth-blueman-automatic-device-connection-audioheadset) which notes [FONT=courier new]/etc/bluetooth/audio.conf[/FONT] has an option [FONT=courier new]AutoConnect[/FONT] which is unset by default.  I changed it to [FONT=courier new]AutoConnect=true[/FONT].  What I observe now is when I turn on the headset, the setting goes from [FONT=courier new]Connection > Off[/FONT] to [FONT=courier new]Connection > On[/FONT] and then after a second or so back to [FONT=courier new]Connection > Off[/FONT].  If I manually move it to [FONT=courier new]Connection > On[/FONT], it stays connected.

(Maybe it was flip-flopping before and I just did not have system preferences open so I did not see it.)

(The page [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) mentions [FONT=courier new]/etc/default/bluetooth[/FONT] but I do not see one.  I'm guessing the page is old and should be the same as above.)

The headset is the only Bluetooth device I am using currently, so I do not know if other Bluetooth devices have the same behavior.

Any suggestions how to debug this?  Manual works, but is a hassle; and, based on the internal adapter's behavior, it should be possible to connect automatically.

---

### Post by Lemuel_Blen on 2015-05-02
try updating the driver.

---

### Post by jeremy31 on 2015-05-02
Unpair the headset, then ```
sudo pactl load-module module-bluetooth-discover
```  Then see if you can pair and use the headset as an audio device

---

### Post by b00n on 2015-05-02
> **Lemuel_Blen said:**
> try updating the driver.

I forgot to say: Ubuntu 14.04, 64-bit, all the latest stuff (according to Software Updater), and a pretty stock install.

So among other things: I think I am already running up-to-date drivers.

---

### Post by b00n on 2015-05-02
> **jeremy31 said:**
> Unpair the headset, then ```
sudo pactl load-module module-bluetooth-discover
```  Then see if you can pair and use the headset as an audio device

Thanks!  I unpaired the headset, but then [FONT=courier new]sudo pactl load-module module-bluetooth-discover[/FONT] exited with an error.  I rebooted and then the command worked.  At that point I re-paired the headset, and I can turn the headset on and off, and it will connect and disconnect as desired.

However, this does not survive reboots.  That is, I have to repeat the command after rebooting.

  Browsing around on the web (now that I know what I'm looking for, thanks!) I found


[LIST]
[*]For some folks, "do it once and then it stays done".  That is, on reboot they do not need to repeat it.  Not me, though. 
[*]There should be an entry in [FONT=courier new]/etc/pulse/default.pa[/FONT] that loads the module (see [http://askubuntu.com/questions/366032/pulseaudio-not-detecting-bluetooth-headset-automatically](http://askubuntu.com/questions/366032/pulseaudio-not-detecting-bluetooth-headset-automatically) for details).  And, indeed, I have one.  There was also a bug that was unloading some stuff automatically causing this to not work, but it looks like it has been fixed (see above and also [https://github.com/blueman-project/blueman/issues/64](https://github.com/blueman-project/blueman/issues/64) for details). 
[/LIST]

I am also a bit confused because it connects automatically with the internal adapter, but not the external one.

What should I do to further debug this, and (pending a root cause fix) what can I do to make it "stick" across reboots?  I can imagine adding the above to some init file -- but it obviously needs to be after a point where the PulseAudio server is ready willing and able to accept the command.

---

### Post by jeremy31 on 2015-05-02
Are you using blueman?  Interface looks like this 
[IMG]http://community.linuxmint.com/img/screenshots/blueman.png[/IMG]

And there is a bug in it that will unload module-bluetooth-discover during boot

---

### Post by b00n on 2015-05-02
> **jeremy31 said:**
> Are you using blueman?

Yes, I was trying to debug another problem and had installed it.  I just now uninstalled it, did a reboot, and the headset now connects automatically.  Thanks!

---

