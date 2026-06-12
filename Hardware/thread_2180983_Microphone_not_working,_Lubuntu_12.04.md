---
title: "Microphone not working, Lubuntu 12.04"
date: 2013-10-15
forum: Hardware
---

### Post by lubo2 on 2013-10-15
Apologies if there is another thread that covers this, I did search but saw nothing relevant so I may have overlooked it. If this belongs in another sub-forum, move it there as long as you notify me in some way (I think my email address should be visible in case I haven't logged into the forums to check).

I have Lubuntu 12.04 installed on the following hardware:

Asus P4B motherboard
P4 2 Ghz
512 MB RAM
etc. (I think from the specific chipsets and drivers, the other components are of little interest for the purpose of this post, except the audio hardware, which is 82801BA ICH2 with AC97 if I recall, but I can check when I log in to Lubuntu next time if needed. It is built in to the motherboard, not a separate sound card, and if you find the specs for the motherboard they should confirm what it is.)

Most things really work quite well, but there's always an exception, isn't there. The microphone plugged into the rear jack on the tower, makes no sound, either with arecord or in Skype. I have Pulse Audio Server and PAVU control installed, I've tried adjusting alsamixer, unchecked the option in Skype to adjust levels which is reputedly buggy, but all I get is silence (or input so low I can't hear it, so it's silent to me). I'd be happy to provide any diagnostic information needed (lshw, arecord -l, etc.) I'd like to get my microphone working in Skype. Of note, it works fine on another computer in Mac OS X, so the microphone hardware is fine, and it works fine in Bodhi Linux, so their sound configuration probably has something different (better) OOTB.

Suggestions, tips welcome.

---

### Post by mörgæs on 2013-10-15
Welcome to the fora.

First of all I recommend a fresh install of Lubuntu 13.10, as 12.04 is out of support in a few weeks. After that it's time to focus on the microphone.

---

### Post by lubo2 on 2013-10-20
If it was simply a question of getting it working right now, without regard to having it work (not much) later, when 13.10 is no longer supported, that would be one thing. Not exactly what I call a good solution, more of a work-around. But I had no luck with that, either. I just tried Lubuntu 13.10 live via USB, it refuses to get past the boot splash. Something similar to what I wrote about Bohdi Linux here: [#1]("http://forums.bodhilinux.com/index.php?/topic/9351-installation-troubles-with-live-usb/page__view__findpost__p__76614"). Simply stunning to me that as near as I can tell neither Ubuntu nor Lubuntu 12.04 (or Lubuntu 13.04 for that matter) handles the microphone properly out of the box on what was very common hardware not too long ago, and no I don't believe were talking about raising a volume slider or unmuting, I tried many permutations of that to no avail. I think something more along the lines of hacking text config files or ripping out pulse audio and installing alsa maybe, but that is a best guess since nothing less drastic has worked so far. And yet this is not considered a big enough bug to delay release of a so called LTS? I'm beginning to think Ubuntu's quality peaked around 10.04 and has been headed for the trash can since, and Unity and other flashy gimmicks aside, see little proof to the contrary. Pity I can't reinstall 10.04 now. I might hope 14.04 will be better, but I always thought the line "the next version is better than the last" was how Microsoft salesmen suckered people into paying again, and not very worthy of open source.

---

### Post by Yellow Pasque on 2013-10-20
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> And yet this is not considered a big enough bug to delay release of a so called LTS?
LMAO. If they delayed release for bugs specific to everyone's hardware, then 12.04 still wouldn't be released. Your expectations are a bit unrealistic..

---

### Post by mörgæs on 2013-10-24
A post from the thread has been jailed. 

Temüjin's post was not referring to original poster's or other persons' hardware, it was describing the way Buntu and operative systems in general are released: On a certain date and not after a certain number of tests. It has only happened once that Ubuntu got delayed and it's not likely to happen again.

An operative system will have lots of bugs at release date. There are three ways of mitigating:

- take part in testing and report bugs during development
- wait some weeks or a month after release before installing
- read the release notes 

By the way, 13.10 is not long term support. It only has the normal nine months.

---

### Post by Yellow Pasque on 2013-10-25
Sorry if my comment was perceived as antagonistic and caused a rant. My backup system's sound card (Xonar DG) doesn't work with front headphone jack or have mic function, so I realize these things are frustrating. Post the info I linked to in the last post and we will see if there's a workaround.

---

