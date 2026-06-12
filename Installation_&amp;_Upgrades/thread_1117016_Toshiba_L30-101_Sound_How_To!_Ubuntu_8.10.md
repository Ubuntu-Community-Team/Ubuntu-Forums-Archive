---
title: "Toshiba L30-101 Sound How To! Ubuntu 8.10"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by yogiman_uk on 2009-04-05
After installing Ubuntu 8.10 on my brothers Toshiba L30-101 I found that there was no sound from the speakers or the headphone socket.  After searching the forums I could find no specific instructions for this particular laptop so I thought I would post a simple guide.

1. Edit the alsa-base file:-
[B]
sudo gedit /etc/modprobe.d/alsa-base[/B]

Paste these two lines into the file:-

[B]options snd-hda-intel model=6stack-digout
options snd-hda-intel model=dallas
[/B]
Place them just above the line:-

#Ubuntu #62691, enable MPU for snd-cmipci

Save the file and then reboot the laptop.

2. Once the laptop has restarted open a terminal and type:-

**alsamixer**

Once the Mixer Utility loads use the **arrow keys** to move around on this screen. On anything you see double MM on press the **M key** and maximize the volume. Do this to anything with the double MM.

Then once you have done this, press **Esc**.

3. Double click the speaker on the top launcher panel and that should open the Mixer. Locate the slider for the Surround and then un-mute it and put the sliders to maximum. Then close the Mixer.

That's it you should now have sound from your speakers and your headphone socket.

If you don't I can only assume that your L30 has a different chipset than the L30-101.

Hope this helps somebody.

Cheers


Yogiman!

---

