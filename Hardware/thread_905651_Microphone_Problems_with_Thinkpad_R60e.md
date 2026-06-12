---
title: "Microphone Problems with Thinkpad R60e"
date: 2008-08-30
forum: Hardware
---

### Post by shay_ts on 2008-08-30
How do I make the integrated microphone work?

It seems like the system recognizes it, because when I enable the microphone in the volum control it makes an awful noise.

Can anyone help?

Thanks!

---

### Post by eggdeng on 2008-08-30
I have always had to do the following to get my microphone to work on ubuntu.

```
sudo gedit /etc/esound/esd.conf
```

Replace the contents with the following. (Back up the file first in case you should want to revert.)


```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

Save the file and reboot.

Make sure your Sound recorder / Volume Control settings are consistent. If you choose Capture as your record-from-input option, then max the volume for Capture on the recording tab of the Volume Control applet. On the options tab, choose Mic as your input source if you are using an external microphone.

---

### Post by shay_ts on 2008-08-30
> **eggdeng said:**
> I have always had to do the following to get my microphone to work on ubuntu.

```
sudo gedit /etc/esound/esd.conf
```

Replace the contents with the following. (Back up the file first in case you should want to revert.)


```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

Save the file and reboot.

Make sure your Sound recorder / Volume Control settings are consistent. If you choose Capture as your record-from-input option, then max the volume for Capture on the recording tab of the Volume Control applet. On the options tab, choose Mic as your input source if you are using an external microphone.

Thank you very much dear friend! I succeeded eventually using the graphic tools (I'm a newbie) :)

---

