---
title: "Headphone jack not working"
date: 2008-04-25
forum: Hardware
---

### Post by sammydlm on 2008-04-25
Hello all.  I tried this once before with no success, but I would like to try once more.  I have an Everex NC1502 laptop with a Via processor with integrated audio.  Ever since I installed Ubuntu 7.10 on it, I have not gotten any audio from my headphone jack.  Yesterday I upgraded to 8.04 hoping that it would fix the headphone jack problem, but it is still the same.  Audio through the internal speaker works fine and when I plug headphones in, the audio through the speaker stops, but nothing is heard through the headphones.  When I unplug the headphones, the audio returns to the speaker.  My headphone jack works just fine in Windows.  I like Ubuntu very much, but not having the headphone jack for VOIP and listening to music in public places is a problem for me.  Can anyone help?  I am very new to Linux, so please try to dumb things down for me and be as specific as possible.  Thanks in advance.

---

### Post by LaRoza on 2008-04-25
> **sammydlm said:**
> Hello all.  I tried this once before with no success, but I would like to try once more.  I have an Everex NC1502 laptop with a Via processor with integrated audio.  Ever since I installed Ubuntu 7.10 on it, I have not gotten any audio from my headphone jack.  Yesterday I upgraded to 8.04 hoping that it would fix the headphone jack problem, but it is still the same.  Audio through the internal speaker works fine and when I plug headphones in, the audio through the speaker stops, but nothing is heard through the headphones.  When I unplug the headphones, the audio returns to the speaker.  My headphone jack works just fine in Windows.  I like Ubuntu very much, but not having the headphone jack for VOIP and listening to music in public places is a problem for me.  Can anyone help?  I am very new to Linux, so please try to dumb things down for me and be as specific as possible.  Thanks in advance.

Get asoundconf-gtk and run it, and see if that helps.

```

sudo aptitude install asoundconf-gtk

```

Run it with the command:

```

asoundconf-gtk

```

---

### Post by sammydlm on 2008-04-25
I did it and it came up with a screen asking me to select a default sound card.  The two choices are VT82XX and PulseAudio.  Which should I select?

---

### Post by LaRoza on 2008-04-25
> **sammydlm said:**
> I did it and it came up with a screen asking me to select a default sound card.  The two choices are VT82XX and PulseAudio.  Which should I select?

Either :-) If it doesn't work, try the other.

---

### Post by sammydlm on 2008-04-25
Selecting either one did not work for my headphone jack.  I also forgot to mention before that when I go to the alsamixer, there is only Master Front, PCM, Front, Microphone, Capture, Capture1, and Digital-- no headphones.  I have messed around with all of the levels to see if anything would affect the headphone volume, but nothing worked.  Any other suggestions?

---

### Post by sammydlm on 2008-04-27
I just wanted to follow up-- does anybody have any other suggestions?

---

### Post by sammydlm on 2008-06-02
Hi all.  I just wanted to follow up and say that my headphone problem was finally solved!  Here is the link to the bug with instructions on how to solve it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/184314)

Hope it helps...  Thanks!

---

### Post by mastermatt63 on 2008-06-05
did this help u sammydlm?

---

### Post by sammydlm on 2008-06-07
The short answer is yes.  I recommend that you read through the entire discussion from my last posted link and see what I eventually did in the end.  You have to follow a series of steps and while doing it, I actually missed one little thing, so I had to go back and do it again.  In the end, it worked just fine and I finally had, for the first time, a headphone volume level control in the mixer.  Just so you know, when it first shows up it is muted, so make sure to unmute it!

---

