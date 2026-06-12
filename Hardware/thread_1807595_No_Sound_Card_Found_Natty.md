---
title: "No Sound Card Found Natty"
date: 2011-07-19
forum: Hardware
---

### Post by loaba on 2011-07-19
Help - sound card seems to have disappeared entirely

```
aplay -l | grep card
aplay: device_list:240: no soundcards found...
```

When I first installed 11.04, everything was fine. Now I've got nothing at all.

I am running on an HP Pavillion dv-7 and I just need to know where to begin. I have tried re-installing alsa via synaptic.

---

### Post by loaba on 2011-07-19
```
********@****:~$ wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh
--2011-07-19 06:46:59--  http://alsa-project.org/alsa-info.sh
Resolving alsa-project.org... 77.48.224.243
Connecting to alsa-project.org|77.48.224.243|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh [following]
--2011-07-19 06:47:14--  http://git.alsa-project.org/?p=alsa-driver.git;a=blob_plain;f=utils/alsa-info.sh
Resolving git.alsa-project.org... 77.48.224.243
Reusing existing connection to alsa-project.org:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `alsa-info.sh'

    [  <=>                                  ] 27,247      64.9K/s   in 0.4s    

2011-07-19 06:47:17 (64.9 KB/s) - `alsa-info.sh' saved [27247]

ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See './alsa-info.sh --help' for command line options.

cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/sbin/alsactl: save_state:1519: No soundcards found...
cat: /tmp/alsa-info.72G14lSyin/alsactl.tmp: No such file or directory
```

---

### Post by loaba on 2011-07-19
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and then....

sudo apt-get install linux-sound-base alsa-base alsa-utils


And we're fixed.

---

### Post by jkcunningham on 2011-08-08
Nicely done. Thanks

--Jeff

---

### Post by cfirpo99 on 2011-08-08
Hey Im also running Natty and I have no sound. BUT it seems that my modules are loaded.  Can someone please help out?


carlos@Gateway:~$ aplay -l | grep card
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
carlos@Gateway:~$

---

### Post by cfirpo99 on 2011-08-08
Ok so I knew that the sound mods were loaded by running the basic checks in terminal, all I had to do was keep ticking around with the sound preferences.  BUT you need to select the right combination between the hardware tab and the output tab.  In my case the hardware profile is "analog stereo output", then on the output tab, the connector type is "analog output LFE/no amplifier.   

Im happy!

---

