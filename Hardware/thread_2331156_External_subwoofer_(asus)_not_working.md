---
title: "External subwoofer (asus) not working"
date: 2016-07-19
forum: Hardware
---

### Post by LK_gandalf_ on 2016-07-19
Hello, I just installed ubuntu 16.04 on my asus N550JK which comes with a nice external subwoofer. Unfortunatelu, audio is not working very well, and I never managed to get this work in the past year on the past versions of ubuntu.
If I select 2.1 audio, the left and right are correctly tested, but when I click test for the subwoofer I hear a hiss/crackle sound. So it is recognized in some way, but not correctly.
Does someone know how to fix this?
Thanks :)

......:~$ lspci | grep Audio
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)

[ATTACH=CONFIG]270184[/ATTACH]

---

### Post by LK_gandalf_ on 2016-07-26
Anyone who could provide some tips? Thanks.

---

### Post by LK_gandalf_ on 2016-09-11
I give an up, since the post is from July.

---

### Post by takion on 2016-11-03
Hi there, follow the link to [askubuntu]("https://askubuntu.com/questions/189304/no-sound-from-external-subwoofer-sonic-master-on-an-asus-n76vm")  , hope this solve your problem, if not maybe take a look at the [archwiki]("https://wiki.archlinux.org/index.php/ASUS_N55SF#Audio").

---

### Post by LK_gandalf_ on 2016-11-05
Hi, and thanks for the links. I had already tried some of those, but I am now trying again after I installed the latest 16.04.

The first fix does not work. If I add **options snd-hda-intel model=asus-mode4** to the file */etc/modprobe.d/alsa-base.conf *
What I get is:
- In 2.1 when I do the audio test in setting, I get front right and left correct, but for the subwoofer I just get a background noise (such as when you don't get a radio channel)
- In 4.0 I get the subwoofer working as a "rear right"
- In normal analogic I get the subwoofer working together with "front right"

---

### Post by LK_gandalf_ on 2016-11-05
I tired the other fix and nothing change, still getting only noise from the subwoofer :(

---

### Post by takion on 2016-11-05
mmm, the best solution i had found is get right speaker and subwoofer working together, as you posted above, using hdajackretask included in the package alsa-tools-gui. If you find another solution, let us know.  if you are interested in follow the steps for do this, take a look [here ]("https://ubuntuforums.org/showthread.php?t=2217683")

---

### Post by LK_gandalf_ on 2016-11-19
Hi, thanks for the link. I am not sure that what pin is the right one, but on the link they say that the best configuration is to get the subwoofer work as rear right channel.
I got this with a 4.0 mode, but still it's not really a subwoofer, just a third speaker. I think the objective is to get the subwoofer work in 2.1, but now what I get when testing it in this configuration is only background noise.

Not sure which one of the many pins can be the right one, and how to make it work :(
[ATTACH=CONFIG]272246[/ATTACH]

---

### Post by shersk on 2016-11-19
Hi,

I have the same sound card and have the same experiences. There should be a real solution for this sound card, to make the subwoofer work as intended, not as "rear right" or somthing. To be more specific, I experimented with HDAJackRetask and managed to get the subwoofer to work by an enormously complex rerouting of the connections, but it messed up the audio system, as I couldn't use the microphone and headphones normally. 

I believe that some of the post and comments you find on the internet, people think they have the subwoofer working when it's not actually working. I have a dual boot Xubutu 16.04 and Windows 8, and in windows I can hear how much better the sound quality is when the subwoofer is working as intended. It gives a much much richer sound. People should not claim to know that it's working just because there are some sounds coming out of the subwoofer. It needs to be operated the way it's designed for and compliment the sound that is produced. I managed to accomplish this, but it required such a complex rerouting of pins in HDAJackRetask which made the laptop useless in other ways, that it just wasn't worth the effort.

I'm no computer programmer, so I'm hoping that the subwoofer problem will be solved by people who know how to do this, but I must say, it has been a long wait. Over two years now. It is one of those stale issues in Ubuntu which never gets resolved for some reason. Like connection bonding - another issue which just sits there like a big black hole and nobody can be bothered.

---

