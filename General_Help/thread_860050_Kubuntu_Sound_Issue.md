---
title: "Kubuntu Sound Issue"
date: 2008-07-15
forum: General Help
---

### Post by virus2 on 2008-07-15
Hi all,

I recently installed Kubuntu7.0 on my machine which already has Winxp(dual boot).I installed it without any hassles and after loging into kubuntu,I heard the short login sound in kubuntu,_which made me think that audio is working fine._
Now,I was able to log into windows as well as kubuntu.However,I did not pay much attention to kubuntu after installing it.I occasionally just booted kubuntu to check whether it is running,but did not change anything to its configuration.Each time I logged into it,I heard the login sound.

Now,Just 1 month back,my motherboard(HIS) got faulty and I had to replace it with a new one.The new MB is not HIS,but it is compatible with Intel Chip.
After replacing this motherboard,I was not able to login into any OS(neither XP nor Kubuntu).
So,i repaired XP through repair option of XP bootable CD.After repairing XP,i was able to use XP AS WELL AS KUBUNTU(though i did not make anything to kubuntu),but the only thing i noticed abnormal in kubuntu is the login sound,which no longer can be heard.
After this,I devoted much of my time to kubuntu,copied some mp3 files to it,but on playing the same through default AMAROK,i always get message as "No mp3 support is available.Do you want to add it".If I click yes,then nothing happens and amarok just goes into 'Not reponding' mode.

[U]Now,my question is:Whether this sound issue in kubuntu is due to the new motherboard or is amarok not configured properly on my system.
Even if it is amarok issue,I should be able to listen to login sound of kubuntu.[/U].Is there any sound file in kubuntu that we can try to play as reference to indicate sound drivers issue.
In XP,i installed the new MB drivers,but Iam not aware whether the same thing needs to be done in kubuntu as well.If yes,then how to do that as the MB CD contains exe files for almost all drivers.

Any one...pls help me........

---

### Post by cmnorton on 2008-07-15
Go to the sound icon. Click on it and ask for mixer. Is PCM's slider all the way down?
You may have a different problem, but that's worth a looksie.

---

### Post by virus2 on 2008-07-16
All the sliders are set to maximum level.......
I doubted amarok...so,i ununstalled and installed it back,but no success.
Amarok still complains "No mp3 support available".
Do I need to install lixine-extracodecs separately or do they get installed automatically while installing amarok???

Thanks!!

---

### Post by cmnorton on 2008-07-16
> **virus2 said:**
> All the sliders are set to maximum level.......
I doubted amarok...so,i ununstalled and installed it back,but no success.
Amarok still complains "No mp3 support available".
Do I need to install lixine-extracodecs separately or do they get installed automatically while installing amarok???

Thanks!!

I got that no mp3 support available but then said yes, when I was prompted to install mp3 support.

---

### Post by virus2 on 2008-07-17
Well,the problem is resolved.:)
I installed libxine-extracodecs manually through command shell and it also installed,along with it,all other dependencies like libxine1-ffmpeg,etc.
After that,just tried to play an mp3 file and it started playing directly into amarok without any issue.
What a silly mistake that was!!!
I was under the impression that installing amarok also installs all the necessary codecs.
Well,thanks anyway for your replies,i can now enjoy listening music in kubuntu and side by side learning the various other features of this OS.
Iam now planning to spend maximum time on this OS.pls suggest any good ebook for kubuntu,which i can download and learn the various features and practically implementing at the same time(side by side listening to music)

Thanks!!!!!!!1:guitar::guitar:

---

