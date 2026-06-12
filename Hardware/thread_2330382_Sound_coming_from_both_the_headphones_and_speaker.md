---
title: "Sound coming from both the headphones and speaker"
date: 2016-07-11
forum: Hardware
---

### Post by krishna.988 on 2016-07-11
When I plugin my headphones through the front jack in my desktop my  speaker does not auto mute and sound comes from both in Ubuntu 16.04.

When I open the alsamixer program through terminal, I see that automute option is missing. 

When I use SLED 12 SP1 the alsamixer program shows automute and is  enabled, and also when I plug-in my headphones the speaker automutes,  the same is true with Windows 7 and Windows 10.

btw my soundcard is Realtek ALC833.

My question is why the Automute option is missing?

---

### Post by krishna.988 on 2016-07-14
Any suggestion or solution to the above issue?

---

### Post by Bucky Ball on 2016-07-14
Install Pulseaudio Volume Control and have a look there. More comprehensive than the alsamixer.

---

### Post by krishna.988 on 2016-07-14
I did but did not find the Automute option. btw it is ALC833

---

### Post by Bucky Ball on 2016-07-14
There is no automute function. You need to configure PAVC correctly and it should take care of that for you. 

Open PAVC, get an audio stream going (play music or vid clip with audio)> open Output tab> in the drop down, select the device you want the audio to output to. 

With the audio stream running, check the 'Playback' tab and see what the output device is in the drop-down there. Experiment and see if you can't get it happening the way you want it.

If you succeed, stop the audio stream. Reboot and see if your changes have stuck by plugging in your headphones again. 

Using PAVC you should be able to route the playback to the headphones only. Perhaps you have Output set to speakers and Playback set to headphones or there is something other happening with the config there. Have a further check.

---

### Post by krishna.988 on 2016-07-14
In the play back tab I don't see drop down to headphones whereas I see headphones dropdown in output tab but when i select headphones dropdown I still here sound thro' speakers even though i have muted line out. Any other suggestion

---

### Post by Bucky Ball on 2016-07-14
Yes, one more thought. The last tab in PAVC is 'Configuration'. What do you have the second section, 'Built-in Audio', set to? It should be 'Profile: Analogue Stereo Duplex'. Is it?

---

### Post by krishna.988 on 2016-07-14
Analog stereo duplex

---

### Post by krishna.988 on 2016-07-19
[**[COLOR=#C61919][B]Bucky Ball**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=504316"),

Any other suggestions?

---

### Post by Bucky Ball on 2016-07-19
Yes. [Here's a similar thread]("https://ubuntuforums.org/showthread.php?t=2330713&page=2&p=13518591&viewfull=1#post13518591") I've been posting in. Start at the post I've linked to, if that doesn't give you some ideas and get you going, read on to blackhawk's post (where they have posted a lot of pics you might relate to) then my next post #13.

Let us know here how you went (please don't post there re. this but by all means add anything you think might help and subscribe to the thread as it may end up being the same solution ... do you have two identical entries for HDMI in your Configuration tab??? :)).

---

