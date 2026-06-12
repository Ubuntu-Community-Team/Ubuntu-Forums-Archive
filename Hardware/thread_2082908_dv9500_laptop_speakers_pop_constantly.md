---
title: "dv9500 laptop speakers pop constantly"
date: 2012-09-02
forum: Hardware
---

### Post by ThatPoshGirl on 2012-09-02
I also have an HP Pavillion d7 and no "power_save" in the file. I use a second monitor route sound through the HDMI. The sound through the hdmi, so I don't know why the speakers are doing anything at all.

ETA. Okay, the solution [here]("http://askubuntu.com/questions/162419/how-do-i-fix-laptop-speakers-popping-when-no-sound-is-playing"), which is basically just a different path to the same solution, seems to have worked for me.

---

### Post by Deadman81 on 2012-11-08
I'm currently using a gateway laptop that i installed ubuntu on as the primary OS and i've attempted to utilize the solutions provided here but the issue is that when i attempt to run the command prompt for the gksudo edit line. I find nothing that states "power_saver=", even using the ctr+f finds nothing related to this. Currently i'm running ubuntu 12.04. I'm not sure what's causing the speakers to pop but it's really annoying in so much as i can't find a cause or the fix. I tried the google chrome fix, and no change. the only time i get the popping sound is when the laptop is running off battery alone and when no audio is being used. If i start rhythm box playing it stops. Same with if I start a movie playing it stops, as long as the speakers are in use it doesn't pop at all. But as soon as the speakers are no longer in use it starts popping again. Any Help would be greatly appreciated!

---

### Post by varunendra on 2012-11-10
> **Deadman81 said:**
> I find nothing that states "power_saver="What if you manually add that line into the file and reboot -
```
echo -e "#\npower_saver=0" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```Or try the [askubuntu link]("http://askubuntu.com/questions/162419/how-do-i-fix-laptop-speakers-popping-when-no-sound-is-playing") that *PoshGirl* gave above. I think the above line in alsa-base.conf should do automatically what that script in the link does manually.

PS:
The solution posted by colin there contains a minor typo in the last command "sudo ./[COLOR=Red]**audo**[/COLOR]-power-save-off". It is obviously "sudo ./**aud[COLOR=Red]i[/COLOR]o**-power-save-off".

Let's hope this solution keeps working for all !

---

