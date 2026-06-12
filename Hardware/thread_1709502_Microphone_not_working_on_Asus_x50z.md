---
title: "Microphone not working on Asus x50z"
date: 2011-03-18
forum: Hardware
---

### Post by mattasus on 2011-03-18
I have an ASUS x50z with a realtec ALC662 LSI sound card, my mic is unmuted, and changed the settings in alsamixer, alsamixer tells me I have HDA ATI SB soundcard. 

I'm running Ubuntu 10.10 and before I had Windows vista where the mic was working.

I tried sudo apt-get install linux-alsa-driver-modules-$(uname -r), the install worked. But still no sound from my mic. Speakers are fine!

I also did the command: unbuntu report bug which brought me into launchpad but I think all that does is to help report bugs, maybe I'm just a newbie.

From another similar topic in this forum I tried replacing the file; snd-hda-codec-conexant.ko but it won't allow me because of a permission issue

I also did this using Terminal="Applications->Accessories->Terminal"
Code:
echo "options snd-hda-intel model=asus-mode3" | sudo tee -a /etc/modprobe.d/alsa-base.conf

Then I rebooted and still no sound input, after each of these tests I check the input level to see if there is any activity and I also do the skype test call.

---

