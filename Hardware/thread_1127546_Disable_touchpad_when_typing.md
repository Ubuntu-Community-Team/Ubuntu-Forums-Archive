---
title: "Disable touchpad when typing"
date: 2009-04-16
forum: Hardware
---

### Post by infamousnation on 2009-04-16
Hello

I have been working on resolving my issue for some time and have had no luck with following the advise that I have been able to find.

I have a Asus eeepc 1000HA running Intrepid 8.10.  I am attempting to disable the touchpad while I am typing by using the syndaemon.  I have it configured where I can toggle the touchpad by pressing a button, but I would really like to automate this feature.

I tried to  enable shmconfig by creating a profile
/etc/hal/fdi/policy/shmconfig.fdi
that contains:
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

I restarted my computer.  Tried to start syndaemon and was told I needed to enable shmconfig.  I tried starting gsynaptics and got the same message.  I'm guessing that I did something wrong when I tried to setup this profile.  I don't know much about the hal.  Any help would be appreciated as accidently clicking my mouse while trying to type is extremely annoying but I do not want to disable tapping.  I am aware that enabling shmconfig is a security risk, but I'm willing to open myself to an exploit if I can make my life more enjoyable.  If anyone knows of a way to toggle the touchpad automatically on keyboard use without shmconfig, let me know.
Do I have to somehow give permission to syndaemon to be able to use the shmconfig?

i also tried inserting
Section "InputDevice"
        Identifier      "SynPS/2 Synaptics TouchPad"
        Driver          "synaptics"
        Option          "CorePointer"
        Option          "Device"              "/dev/psaux"
        Option          "Protocol"            "auto-dev" 
        Option          "SHMConfig"           "true" 
EndSection
into my /etc/x11/xorg.config with no sucess

---

### Post by sgosnell on 2009-04-16
Read [this thread](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236).  On my 900, this works: ```
syndaemon -i 0.5 - S -d
```.  Change the 0.5 to the time of your choice, and note that there is a space between - and S.

---

### Post by schlort on 2009-04-24
To enable SHMConfig on Intrepid and Jaunty, the following is correct:

Use your preferred text editor (as root) to edit /etc/hal/fdi/policy/shmconfig.fdi
(i.e. sudo nano /etc/hal/fdi/policy/shmconfig.fdi )
It should contain --
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>

```


I use amd64 and there is a bug which causes syndaemon to never start.  The latest attempt on Jaunty failed with the error:
> X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  140 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12

To remedy this, install the fixed synaptics driver from William Grant's PPA repo.  

For Intrepid (8.10):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu intrepid main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=0.15.2-0ubuntu7~wgrant3
```

For Jaunty (9.04):
```
echo -e "\n## Syndaemon 64-bit Fix PPA (wgrant)\ndeb http://ppa.launchpad.net/wgrant/ubuntu jaunty main" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 294bb98049fed1dd96e4915c2a7ceb1d8a626b42
sudo aptitude update
sudo aptitude install xserver-xorg-input-synaptics=1.1.0-0ppa2~wgrant3
```

---

### Post by magicke on 2009-04-28
hmm...being a nontechie user, i used a small app called touchfreeze to do this for me. I used the Synaptic package manager on a hardy install.

Touchfreeze docks in your system tray and disables your touchpad
while typing. It re-enables your touchpad when typing stops, using a
configurable delay time.

Canonical does not provide updates for touchfreeze. Some updates may be provided by the Ubuntu community.

Too bad for me that the touchpad on my acer aspire 4530 stopped working after I upgraded to Jaunty. The app is still there on Jaunty though so I guess it should still work.

Hope this helps someone.

---

### Post by yoasif on 2009-04-28
> **magicke said:**
> Too bad for me that the touchpad on my acer aspire 4530 stopped working after I upgraded to Jaunty. i just submitted a bug about this issue, see if you can comment and add anything that i missed.

[https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/368985](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/368985)

---

