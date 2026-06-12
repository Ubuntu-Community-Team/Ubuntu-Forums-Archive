---
title: "Skype mouse conflict"
date: 2009-05-27
forum: Hardware
---

### Post by dadrivr on 2009-05-27
Whenever I make a call in skype, my mouse freezes until the call is terminated.  I have the same problem as the person in the following thread:
[http://ubuntuforums.org/showthread.php?t=740073](http://ubuntuforums.org/showthread.php?t=740073)

Any ideas?  Any help would be greatly appreciated.  Thanks!

---

### Post by dmizer on 2009-05-27
Rather than opening skype from the menu by clicking on the icon, please open skype via the command line like so:
```
skype
```

---

### Post by dadrivr on 2009-05-27
I tried opening Skype in the terminal, but the problem still persists.  Any ideas?  Thanks again.

---

### Post by dmizer on 2009-05-27
When skype crashed with mouse use, was/is there any output in the terminal?

---

### Post by dadrivr on 2009-05-28
I get the following output in the terminal (both when I run skype and after the mouse freezes when I make a call):

```
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
```

---

### Post by dmizer on 2009-05-28
You're using a bluetooth headset? Is the bluetooth headset USB?

---

### Post by dmizer on 2009-05-28
Try starting skype with this command:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
See if it fixes your problem.

[SIZE="1"]Source here: [http://doc.ubuntu-fr.org/faire_fonctionner_sa_webcam_avec_les_logiciel_de_communication#version_simple](http://doc.ubuntu-fr.org/faire_fonctionner_sa_webcam_avec_les_logiciel_de_communication#version_simple)
Bug report here: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/361615](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/361615)[/SIZE]

---

### Post by dadrivr on 2009-05-28
I tried opening skype using the above command, but I get the same output in the terminal, and the mouse problem still persists.

I am using a Plantronics DSP 500 headset.  I don't think it's a bluetooth headset - it is USB and there's no mention of bluetooth (or its icon) anywhere on the headset.

---

