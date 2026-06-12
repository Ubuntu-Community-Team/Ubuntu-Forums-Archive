---
title: "P965 + Hi-Def Audio"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by bonestonne on 2007-07-26
Ok, so i use windows more than linux for my main computer needs, so i'm much more used to having drivers for main hardware, and definitive manufacturer support, so when it comes down to me switching to Linux almost 100%, i'm at a standstill right now.
Normally i use Adobe Audition for multitrack audio recording, as i record my radio shows from home rather than in-studio, so i have more of a listener final copy. well, i have an MSI Neo P965 motherboard, with Realtek Hi Definition audio. recently, i've come up with two problems.

1) I cannot playback any audio [in Audacity, i cannot select a playback device]

2) no matter what input device i choose from the list, i constantly get an error message saying that it cannot connect with the device.

in my older computer [which has no onboard audio and relies on a Soundblaster Live] Audacity works fine, and i have used it in the past.

i've searched for drivers or anything that can help me, but couldn't find anything. tomorrow i'm going to install Ubuntu Studio on my older computer to see if Ardour is easier to use that way, but i don't want to have to format my drive and start over on this drive [i finally got flash player working].

I'm using Ubuntu Feisty 7.04 updated completely, 64 bit, with a Pentium D 940 [3.2ghz dual core] and 1 gig of DDR2 RAM. this system is much faster than my other system, however i need both working by the first week of september. this system wont be used to record any shows unless i can get Audacity working in linux, as i plan on phasing windows out completely on this drive and just using linux [i'll just eat the windows partition and remove its entry from grub]. i will then just emulate windows when its necessary.

thanks in advanced for anyone's help. without a solid recording mixer to show me all the channels i don't know where to start, i've been using linux for quite some time, but phasing out windows is something i'm only beginning to do [as certain programs cost quite some money and id like to keep them in use for a little longer until i find perfect substitutes].

---

### Post by bonestonne on 2007-07-27
found a solution:
update ALSA [advanced linux sound architecture] to lastest version [1.0.14rc4].

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

in Audacity, set recording device as Surround40, playback will depend on what you normally use.

---

### Post by fredj on 2007-07-27
A very useful post. Thanks for sharing your solution.

---

