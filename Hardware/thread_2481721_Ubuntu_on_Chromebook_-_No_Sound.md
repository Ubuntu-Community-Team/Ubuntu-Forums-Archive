---
title: "Ubuntu on Chromebook - No Sound"
date: 2022-12-07
forum: Hardware
---

### Post by jwandta on 2022-12-07
I just completed Ubuntu install on internal sd Chromebook 2 Toshiba (2014) As is a common issue there is no sound. I have tried every conceivable thing to fix this including countless terminal entries. I gave up and installed Mint instead and to my surprise the sound worked out of the box even during the "Try" mode off the usb. However I really want to use Ubuntu for my go to. There has to be a fix if the sound works in Mint...Any suggestions? Thanks.

---

### Post by coffeecat on 2022-12-07
Post moved to its own thread into a support forum from here: [https://ubuntuforums.org/showthread.php?t=2478106](https://ubuntuforums.org/showthread.php?t=2478106)

@jwandta, you posted to an old abandoned thread, started by a drive-by poster who has not been back since the day they joined, posted to a chat forum clearly headed by a large red banner asking posters needing technical help not to post there.... Also, please start your own threads. You can always link back to what you think may be relevant ones. 

Please state the release of Ubuntu you have been trying unsuccessfully, and the release of Mint that you used successfully. It's possible that the two had different kernels, hence different drivers, but in any case this information would be needed by those offering support.

---

### Post by jwandta on 2022-12-07
I looked around and couldn't find where to/howto start my own thread on this subject.

---

### Post by TheFu on 2022-12-07
> **jwandta said:**
> I just completed Ubuntu install on internal sd Chromebook 2 Toshiba (2014) As is a common issue there is no sound. I have tried every conceivable thing to fix this including countless terminal entries. I gave up and installed Mint instead and to my surprise the sound worked out of the box even during the "Try" mode off the usb. However I really want to use Ubuntu for my go to. There has to be a fix if the sound works in Mint...Any suggestions? Thanks.

I had a Chromebook 2 from 2015 and don't remember any sound issues with Ubuntu.  I'm guessing that you haven't setup the pulse audio config ... or running commands without understanding what they do (which says more about pulse-audio's CLI interface than you), could be the cause.  IME, the easiest way to deal with sound is
a) run a supported Ubuntu release. 
b) run the sound-troubleshooter script and past the results.
c) wait for an expert to review it.  This would typically happen in a subforum for audio/media.

d) if you can't wait, you can run pavucontrol (may need to install it) and work from the far right tab towards the left tabs.  Only setup the single output you want to work - usually analog speakers, and move left to the next output control tab.  Ensure the selected output is enabled, not muted and set the gain to 100%.  Move to the left-most tab where it shows applications and try to play an audio file.  Set the volume for that specific application as desired in that tab only.

If you have a microphone, to the same, just with the microphone/recording tabs instead.

The rules are simple.  Start in the far right tab, enable the specific hardware you want and move left in the tabls.  With recordings, you'll likely want to reduce the gain to avoid distortion from the microphone pickup.

Once you have everything set. Don't change it. Only deal with the far left tabs.

If you need both analog and HDMI outputs to be supported, be prepared to enable/disable the hardware in the far right tab, as needed, then work through setting the gain levels and output volumes again each time.

Once you get tired of that, you can use the pacmd and pactl tools from a shell/script to make changes easier. I'll leave that for you to figure out.  When I join video calls, I have a few different tiny scripts that set the default microphone and output (speakers or headset) for each different type of video-chat program. They are each a little different and the perfect levels/gain are a little different too.

---

### Post by jwandta on 2022-12-07
Mint sound works out of the box, Ubuntu (any flavor)..no sound on Toshiba Chromebook 2 (2014) I ran Pulse audio, didn't help. I don't want to use a work around, if the sound works perfectly in Mint, it should work in Ubuntu. Someone out there knows how to do that, I'll wait and see if that someone drops by. Prize winning comment so far on the subject.. "How did you get Ubuntu on a Chromebook..?

---

### Post by TheFu on 2022-12-07
> **jwandta said:**
> Mint sound works out of the box, Ubuntu (any flavor)..no sound on Toshiba Chromebook 2 (2014) I ran Pulse audio, didn't help. I don't want to use a work around, if the sound works perfectly in Mint, it should work in Ubuntu. Someone out there knows how to do that, I'll wait and see if that someone drops by. Prize winning comment so far on the subject.. "How did you get Ubuntu on a Chromebook..?

Since I didn't have the same issue on my Toshiba Chromebook, I assumed is what something odd about yours or the setup after running commands.

Linux Mint is a fine distro. If it works for your needs, use it.  I'm considering moving my workstations to Mint to avoid some new things that Canonical is forcing, much like they did previously.  For a few years, Canonical heads down a direction that I disagree with, then they find that the world isn't in agreement with their vision and abandon all that effort.  Sadly, it takes many years before this happens.  I can only hope that it happens quicker this time.

For example, PulseAudio is being replaced with Pipe-something. Sadly, the Pipe-something is just another tool over Pulse, sorta like how Pulse us  a tool over ALSA.

"I ran Pulse Audio" is vague to me. There are a number of programs with pulse in the  name, so I don't know what you've done or even if you tried what was suggested.  If you seek help, but don't do what was asked, help will end.  Good luck.

---

### Post by guiverc on 2022-12-07
> **jwandta said:**
> Mint sound works out of the box, Ubuntu (any flavor)..no sound on Toshiba Chromebook 2 (2014) I ran Pulse audio, didn't help. I don't want to use a work around, if the sound works perfectly in Mint, it should work in Ubuntu. Someone out there knows how to do that, I'll wait and see if that someone drops by. Prize winning comment so far on the subject.. "How did you get Ubuntu on a Chromebook..?

If it works "*out of the box*" box in Linux Mint, I'd use that to have it work in Ubuntu as well given Linux Mint is a Ubuntu based system.   ie. take note of the release details (*you didn't provide*) of Linux Mint, the kernel stack choice made by the Linux Mint system you're using, and use the same Ubuntu release & kernel stack and you'll get the identical result - ie. it'll work.

You didn't provide specifics as to what Linux Mint system worked, as that detail is where I'd start.

FYI:   If I can find any GNU/Linux system work on a piece of hardware, I'm of the opinion that I can make any other GNU/Linux system work equally well if I can be bothered...   I just explore what's in the '*software stack*' of what worked, and duplicate that in the other system.. With Linux Mint & Ubuntu that'll be 'super easy', but it works with other systems too, eg. Fedora, OpenSuSE, Debian, Ubuntu, etc... Finding what '*works*' is the largest hurdle for hardware - and your Linux Mint system provides that.  Look at the specifics in the *software stack *such as release details, kernel choice (GA? HWE?) etc.  It's the specific details that help, not generic terms such as '*distroname*'.

---

### Post by jwandta on 2022-12-08
Never-mind, I'll just use Mint. Thanks

---

### Post by jwandta on 2022-12-09
The issues of no sound on Toshiba Chromebook 2 after Ubuntu install solved... I was using 20.04.. Wiped and installed 22.04.. Wala...Sound. I also found the answers are not on these forums..LOL. Toodlelu

---

### Post by coffeecat on 2022-12-09
> **jwandta said:**
> The issues of no sound on Toshiba Chromebook 2 after Ubuntu install solved... I was using 20.04.. Wiped and installed 22.04.. Wala...Sound. I also found the answers are not on these forums..LOL. Toodlelu

Well, well, well. Had you bothered to answer the question I asked 2 days ago...

> **coffeecat said:**
> 
Please state the release of Ubuntu you have been trying unsuccessfully, and the release of Mint that you used successfully. It's possible that the two had different kernels, hence different drivers, but in any case this information would be needed by those offering support.

... you might have got there quicker. It sounds as though it is as I suspected. Different kernels and different drivers. The kernel in Ubuntu 22.04 is a later one than in 20.04 (if you don't have hardware enablement stack on 20.04*), and probably has the driver you need. I also suspect that the release of Mint that worked is based on Ubuntu 22.04, which is why it worked. But as you won't say, then we can't know.

* - (complicated story. It partly depends on which point release you installed 20.04 from but, again, you don't/won't say.) 

Word of advice for when using a forum: when someone asks you for information, have the courtesy to provide it. It's in your own best interest.

---

### Post by jwandta on 2022-12-09
You are correct and I stand corrected. I couldn't see how it would have mattered. O had tried 22 previously some months ago and found it un-stable so I thought to be using the best latest release in 20. My mistake.

---

