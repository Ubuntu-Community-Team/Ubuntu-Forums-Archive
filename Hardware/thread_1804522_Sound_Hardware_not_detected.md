---
title: "Sound Hardware not detected"
date: 2011-07-14
forum: Hardware
---

### Post by baconednarwhal on 2011-07-14
Noob here. My sound was working perfectly until yesterday. I think the updates from updates manager screwed it up. I have a dell XPS 15 running Ubuntu 11.04
And my problem is that in the sound properties it only shows the hardware for HDMI out, which means that my headphones jack/ speaker and even the internal mic don't work
I don't remember what the other hardware was.
I tried some fixes that I saw around like inserting an option line in the /etc/modprobe.d/alsa-base.conf and reloading alsa but that didn't help

[IMG]http://i.imgur.com/Fx64z.png[/IMG]

---

### Post by lidex on 2011-07-14
You have the hdmi digital stereo output as your profile, try selecting analog stereo duplex. If no options other than hdmi appear in profiles post the terminal output of this command:
```
aplay -l
```

---

### Post by baconednarwhal on 2011-07-14
so i just rebooted my computer since I posted and now the HDMI out is missing too so now the aplay -l output is blank
```
aplay -l
**** List of PLAYBACK Hardware Devices ****
```

---

### Post by baconednarwhal on 2011-07-14
also here's the output for lspci
```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)

```

---

### Post by lidex on 2011-07-14
Something's borked. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by baconednarwhal on 2011-07-14
[http://www.alsa-project.org/db/?f=422e50ec517533198e76f38dc20c2f501578bb5b]("http://www.alsa-project.org/db/?f=422e50ec517533198e76f38dc20c2f501578bb5b")

---

### Post by lidex on 2011-07-15
Before we go any further, edit alsa-base.conf to remove the model switch you added, reboot and run the script again.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Remove this line:
```
options snd-hda-intel model=generic
```

---

### Post by baconednarwhal on 2011-07-15
Hey so I decided to boot in the windows to see if it was working there. But it wasn't so I think it might be a bigger hardware issue than just ubuntu. Thanks for your help. I'll mark this as solved as of now and try to figure it out with dell.  Thanks again!

---

### Post by omlx2 on 2011-09-05
i have same problem ,,my sound was working but it stop suddenly
[http://www.alsa-project.org/db/?f=b7b0f90c8af6bd4a70d6666f4939bb0d333f3faf](http://www.alsa-project.org/db/?f=b7b0f90c8af6bd4a70d6666f4939bb0d333f3faf)
hope to find the solution here

---

### Post by lidex on 2011-09-18
> **omlx2 said:**
> i have same problem ,,my sound was working but it stop suddenly
[http://www.alsa-project.org/db/?f=b7b0f90c8af6bd4a70d6666f4939bb0d333f3faf](http://www.alsa-project.org/db/?f=b7b0f90c8af6bd4a70d6666f4939bb0d333f3faf)
hope to find the solution here

Remove the edit to alsa-base.conf, specifically the line beginning with "options snd-hda-intel". Next follow the link in my sig to upgrade alsa.

---

