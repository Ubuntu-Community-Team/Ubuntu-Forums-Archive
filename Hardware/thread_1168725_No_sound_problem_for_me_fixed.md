---
title: "No sound problem for me fixed"
date: 2009-05-24
forum: Hardware
---

### Post by Khar136 on 2009-05-24
Hi, Ever since upgrading from Ubuntu 7.04 I have had problems with no sound in Ubuntu. Here is what I have tried:

- Installed alsamixer (just run it from a terminal after installing, or try running "alsamixer -Dhw") and ran it to make sure that the channels are not muted and volumes are maxed. This was originally the cause of very soft sound under Ubuntu 7.04.

- Turning off system sounds, some people think there may be a timing conflict.

- Restarted pulseaudio using "pkill pulseaudio; sleep 2; pulseaudio -vv". I can see in the terminal window that it prints out a bunch of information whenever a sound file is played or I run anything to do with sound.

- Ran programs like VLC, audacity etc. They all play sounds fine and show volumes and sound levels, but I hear nothing.

- Went to the sound control and tried checking or unchecking the earphones option.

- I finally installed a clean 9.04 64-bit on the machine, still no sound.

None of the ideas in any forums worked. So I booted Windows XP (I am using WUBI) and had a look at the NVidia audio controller application. The sound card has at least six connections where you can plug things into it (front, sides, back speakers, earphone, microphone, you name it). The odd thing is, that it is not clear what to plug in where. You take the speaker and plug it into a different outlet, and the audio application opens up a window and asks "What did you just plugged into the pink outlet? Pick from the list below". It then changes the pictures it displays to make it look like, yes, you should be plugging in the speakers wherever you just plugged them in. It is almost as if you can plug things into any connection on it and it works, as long as you tell it whats plugged into it. It also remembers somehow and only ever asks once. Under Windows I can plug the speaker into just about any outlet and it will keep playing.

So after fiddling around with this, I finally managed to get sound under Ubuntu. Under Windows I had moved the speaker cable into a different connection on the sound card, but the sound now works under Ubuntu even after a cold Ubuntu boot. Do note that if I uncheck the "earphones" checkbox in Ubuntu, that the sound disappears again. So obviously Ubuntu's sound control thinks my speaker is plugged into whatever it somehow decided is the "earphones" outlet.

Now this solution may sound obvious, but I have not thought about the Windows audio applet or the fact that it was never clear where to plug what into the sound card, because it had always worked and I had just left it at what I originally did.

Now why it stopped working after Ubuntu 7.04 is another mystery.

But it almost looks to me like earlier versions of the Ubuntu software either turned all the sound output channels on, or was smarter about detecting what was plugged in where, or something which it no longer does.

Any thoughts about this? Is there by chance some sort of configuration program you can run, like the XP one, that shows you where it thinks you have things plugged into your sound card, or possibly even lets you tell it what is plugged in? Alsamixer shows front, surround, center etc. but how does it decide which connection at the back of the sound card is which? They are not marked in any way other than that each is a different colour.

Ubuntu is great, thank you for all the wonderful support!! I do see a lot of forums about people who cant get the sound to work, which is a little sad. Also, the flash player related crashes in firefox are a little vexing, but I havent seen them on 9.04 yet (maybe now that I have sound).

Further information:

For other people looking into debugging sound issues and reading this, I only just discovered this link, which is perhaps better than trying random things from the forums (which I have done for some time with no luck, other than the alsamixer volume one). So if you are reading this to troubleshoot your sound not working, try this link for sure:

[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)

In my case, if any sound configuration guru reads this and has any insights or can mention anything of interest or use (please), alsa-info.sh gives this:

[http://www.alsa-project.org/db/?f=35d3eacd72333f2f6585395c050b7b1c614a10a5](http://www.alsa-project.org/db/?f=35d3eacd72333f2f6585395c050b7b1c614a10a5)

aplay -l gives:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v | less gives:

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7260
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at fe9f4000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

---

### Post by Khar136 on 2009-05-24
What would be nice is if someone could tell me how to figure out what the sound card connections are by default. How do I know if the green one is the one Ubuntu thinks is the front speaker one or not?

Alternatively, if there is a way to tell the sound driver to send sound to all the speaker and earphone outlets, I dont know if that makes sense or not.

I am glad I got it working, it would be nice to understand it a little better.

---

### Post by Khar136 on 2009-05-24
This link also seems handy: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

