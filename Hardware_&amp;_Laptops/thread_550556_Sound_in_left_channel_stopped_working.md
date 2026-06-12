---
title: "Sound in left channel stopped working"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by checkeredshawn on 2007-09-14
I was watching a video on YouTube and the audio was working fine then suddenly my left headphone stopped working.  I booted into Windows and played a song and the left worked fine.  The left channel on PCM and Master is definitely not muted.

---

### Post by linuxwizard on 2007-09-15
You didn't post any info on what sound card you are using or what type headphones. What version of Ubuntu are you using ? If you are using Feisty did you install all of the latest updates ? I see their are alot of issues with sound. You might want to check Launchpad to see if a bug has been reported on your issue or sound card.

---

### Post by Deffexor on 2007-11-25
Checkeredshawn: I think I may have a solution because the same problem plagued me for a while, too. I ran into this problem on Ubuntu 7.10 on a Dell Inspiron 6400, but I imagine it probably affects more than just this laptop.

Here's my solution:
1) In the Upper right corner of the Gnome desktop is an icon that looks like a speaker, Double-Click on it. A window should pop up that says something like  "Volume Control: HDA Intel (Alsa Mixer)"  [well, at least that's what it said for my computer]

2) Click on "File" => "Change Device"

3) Pick the Device that is *not* selected.  [In my case, it said "SigmaTel STAC 9200 (OSS Mixer)"]

4) If your problem is the same as mine, you'll notice that the left channel is set to the bottom (effectively off) while the right channel is just above the bottom.

5) Click on the "Chain Link" icon to "break" the link between the channels. Set both to the bottom and then click the "Chain Link" icon again to fix the link between the channels. Then slide the volume up to your desired level.

6) After that, I set the Selected Device back to the HDA Intel (Alsa Mixer)  -- From what I understand, the ALSA Mixer is the newer (better?) Linux audio mixer driver/software.

Hope this helps!

---

### Post by chalewa on 2007-12-10
> **Deffexor said:**
> Checkeredshawn: I think I may have a solution because the same problem plagued me for a while, too. I ran into this problem on Ubuntu 7.10 on a Dell Inspiron 6400, but I imagine it probably affects more than just this laptop.

Here's my solution:
1) In the Upper right corner of the Gnome desktop is an icon that looks like a speaker, Double-Click on it. A window should pop up that says something like  "Volume Control: HDA Intel (Alsa Mixer)"  [well, at least that's what it said for my computer]

2) Click on "File" => "Change Device"

3) Pick the Device that is *not* selected.  [In my case, it said "SigmaTel STAC 9200 (OSS Mixer)"]

4) If your problem is the same as mine, you'll notice that the left channel is set to the bottom (effectively off) while the right channel is just above the bottom.

5) Click on the "Chain Link" icon to "break" the link between the channels. Set both to the bottom and then click the "Chain Link" icon again to fix the link between the channels. Then slide the volume up to your desired level.

6) After that, I set the Selected Device back to the HDA Intel (Alsa Mixer)  -- From what I understand, the ALSA Mixer is the newer (better?) Linux audio mixer driver/software.

Hope this helps!


totally fixed my left channel static issue thanks a lot

---

