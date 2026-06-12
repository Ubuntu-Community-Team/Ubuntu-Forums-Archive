---
title: "Another cheap webcam microphone fail..."
date: 2020-09-29
forum: Hardware
---

### Post by dodgy geezer on 2020-09-29
Here I am, a newbie with a cheap USB webcam - video works but not sound.  The hardware works under Win10, so it's a Ubuntu issue.

lsusb recognises the hardware as 'Jieli Technology USB PHY 2.0'.   This matches the recognised hardware under the Sound Devices, which gives me a choice of Multichannel USB PHY 2.0 or Microphone USB PHY 2.0.  Video works fine under Chese, but there is no mike sound. Microsoft Teams (which I got the webcam for) states that the 'microphone does not work. 

There seem to be two bits of controling software in Ubuntu - AlsaMixer and PulseAudio. I had unmuted on as much as I could find, when I noticed an odd setting in Alsamixer.  It said that the sound card it was using was Nvidia, but in the lists of possible soundcards were the magic words 'USB PHY 2.0'.  

I selected these, but that did not make things work. Because every time I left AlsaMixer using ESC, the setting just reverted to NVidia.  I tried using sudo alsactrl store, but that didn't seem to make any difference...

Has anyone got any other ideas of things I could change - or how to make that alsamixer setting stick?

Thanks....

---

### Post by TheFu on 2020-09-29
You can fight with this thing, or get a logitech c270 and have it "just work." How much is your time worth? Logitech webcams seem to be back in stock around here.

Microphones are not sound cards. don't confuse them with the speakers.

---

### Post by dodgy geezer on 2020-09-30
Thanks for the rapid response!

Just having it work would be fine - but it would do little for my Linux education!  I'm not sure how you think I am confusing a mike with a speaker - both the bits of software I mentioned seem to have input (mike) and output (speaker) services clearly defined.  But trying to understand why you made that comment will help me learn a bit more about the Ubuntu system.

I don't seem to be able to 'save' settings in alsamixer, even with 'sudo alsacrtl save'. And the issue with the webcam mike might be that it is stereo, while MS Teams apparently wants mono.  But when I just look at the basic software drivers (if that's what they are called) I see that the mike is recognised, but does not seem to produce output at the O/S level.

At the moment I have plugged in another webcam with a mono mike, and am using that mike, together with the first webcam's video.  And I would simply like to understand enough about the system to troubleshoot the mike recognition, but lack of function....

---

### Post by TheFu on 2020-09-30
A mic cannot be used to listen.  In audio - or pulseAudio - which is what all Ubuntus use, audio devices are either a "sink" or a "source".
sink == speakers
source == mic
In the audio settings, never forget that.  If you see a microphone on the "sink" page, then the microphone driver isn't working as it should.

Forget alsamixer.  ALSA is still used below PulseAudio, but let pulse do all the management for the ALSA stuff. Don't mix.

I know nothing of MS-teams. Fortunately, my work doesn't use Microsoft anything.

PulseAudio has this default setup that always tries to use the last audio device connected.  But if the drivers are bad, then that will be useless.
You can throw some commands at pulse audio if you like. That's why I asked if you just wanted a solution that worked or if you wanted to fight with this.  Most people just want the solution that works today and for the next 5 yrs.  If you have to fight with the HW today, it is likely that will continue with every new kernel for the next 5 yrs.

Anyways, I've posted pactl and pacmd examples in these forums a few times in the last 6 months.  Those show how to get a list of devices for sinks and sources, how to set the default device for each and how to choose the device to be used.  Whether any of that is useful to your specific device is a completely different question.  How much is your time worth?

Good luck.

---

### Post by CelticWarrior on 2020-09-30
Another thing I don't understand about your ordeal is why you keep insisting on using webcam integrated microphones that are crap even when they work. The cheapest microphone in the dollar shop is better. I mean the standard "toy like" analogue microphone with an audio jack connected to your integrated sound chip (you do have one, right?) or the same mike in an headset combo. Any integrated microphone in any laptop also much better. And if you want next level quality even the cheapest USB (digital) microphone will do wonder and work OOB.

---

### Post by dodgy geezer on 2020-09-30
@TheFu - [COLOR=#000000][I]That's why I asked if you just wanted a solution that worked or if you wanted to fight with this. Most people just want the solution that works today and for the next 5 yrs. If you have to fight with the HW today, it is likely that will continue with every new kernel for the next 5 yrs.
[/I]
I'm all in favour of a solution that works - but I like to know WHY it works.  There are certainly limits to the depth I would like to go to, but I find that the easiest way for me to gain the knowledge I want is to address the problem. Even if I get nowhere in solvinmg it, I will have learned more about the systems and the commands needed to examine them.  I shall look for your [/COLOR][COLOR=#000000]pactl and pacmd examples.... and thanks in advance for them....[/COLOR][COLOR=#000000]

@CelticWarrior - [/COLOR][COLOR=#000000]*The cheapest microphone in the dollar shop is better*

[/COLOR][COLOR=#000000]Very probably. I had nice little one on an arm until one of my sons took it,  and i probably have some potted mikes in my bit box that I could plug into the 'line in'.  And for any real work i would probably use a headphone combo which has a handy mute switch.  But I still feel much happier knowing WHY something does not work...


[/COLOR]

---

### Post by TheFu on 2020-09-30
> but I like to know WHY it works.
Because the hardware is well tested and the drivers are mature, so it works.

TL;DR:
I've never had luck getting any simple mic working with desktop Ubuntu through the mic/headphone jack. I've tried with about 5 different mic setups over the years.  Most of the time, the amplification was too low so the inputs were always much too soft. The first USB mic I used, worked really well. It is a Samson GoMic ($25). This mic is just a little better for audio than the logitech webcams. If you are doing professional interviews, it is a starter mic.  For 3-4x more, there is the Yeti mic which provides a little bit warmer sound, but no more clarity in my testing. On video calls, people say the GoMic is a tiny bit clearer, but don't mind the C270 or C920 webcam audio at all.

I also have a Plantronics USB headset. This is for gaming with 7.1 surround. I find the weight and big cans inconvenient. I don't game much. When I was first learning to use PulseAudio, it was nice to have a single device to tweak in the **pavucontrol** application. It didn't take long to learn to make any working audio devices work together on the system.  

I haven't learned to send audio between systems, so I can have a centrally controlled music server that plays the same audio to 3 different rooms concurrently. That is possible with Pulse, but I'm just not at that level yet.

[https://www.linux.com/training-tutorials/weekend-project-using-pulseaudio-share-sound-across-all-your-computers/](https://www.linux.com/training-tutorials/weekend-project-using-pulseaudio-share-sound-across-all-your-computers/)
[https://www.freedesktop.org/wiki/Software/PulseAudio/](https://www.freedesktop.org/wiki/Software/PulseAudio/)

---

### Post by dodgy geezer on 2020-10-01
[COLOR=#000000]*Because the hardware is well tested and the drivers are mature, so it works.*

Er...OK.  I'm rather old-school - I like to know where my bytes are going.  When I started working on computers you needed to be aware of the head position on the disk drives if you wanted to code for good fast sorts, and in those days you wanted to know where your electrons were going...[/COLOR]

---

### Post by TheFu on 2020-10-01
I programed on IBM DOS mainframes in 360-ASM, but that doesn't matter any more than the F66 punch cards used on later systems.

If you can find the driver source, then feel free to modify it for your needs or fix it and provide a patch to the world.

---

### Post by dodgy geezer on 2020-10-02
I fear that we must agree to differ. I simply wanted to dig somewhat deeper into the Linux system in order to understand a bit more about the structure -  neither rejecting all knowledge in favour of just buying compatible products, nor involving myself sufficiently in development so as to be able to contribute acceptable code. Surely that is not an unreasonable position?

---

### Post by CelticWarrior on 2020-10-02
I think it boils down to native drivers.
Most USB audio devices, input or output, just work thanks to a "generic USB audio device driver" that has been around for donkey's years. A few devices for reasons know only by the vendors have some sort of "value added" or just a deviation from the industry standard. This ones are different enough to need a different driver. Windows seems to support a wider range of variants then the homologous Linux driver. Examples are microphones and speakers that are recognized but don't work or speakers that only emit noise or have an annoying humming noise on top of the sound they should be emitting. But in Windows they "just work".

---

### Post by richardcarter on 2020-12-21
[QUOTE=TheFu;13989449]You can fight with this thing, or get a logitech c270 and have it "just work." How much is your time worth? Logitech webcams seem to be back in stock around here.

I have a Logitech C270 webcam, running the latest distro release, and it is having all sorts of stupid problems and doesn't "just work."   I don't think anything ever with Linux "just works."  The microphone rate is by default incorrect and is 3X too fast and the audio sounds like Alvin and the stupid Chipmunks.  I had to edit /etc/pulse/default.pa and manually add the device and the correct rate.  Then, the microphone wouldn't work with most applications, and most specifically with Google Chrome because the webcam audio is mono but Linux thinks it's a stereo webcam and has two channels when there should only be one, so I also had to edit that same file to specify the USB webcam microphone was mono and not multichannel/stereo. It still isn't working most of the time and has to constantly be unplugged and reconnected all the time to reset and work.  And the webcam video is giving me many challenges/annoying pixelated horizontal lines and colorful squares.

So... no.  It doesn't "just work," even with a Logitech C270 webcam.  Linux is so fun...


edit: sorryyyy, I was just a bit frustrated after having spent so many hours on this.  &#9684;_&#9684;   Thank you, wildmanne39.

Also... this isn't solely a Linux problem: I've used this webcam/microphone for years now and have always encountered countless problems, including the wrong rate "chipmunk effect" on Windows. It seems no matter the OS, if I'm going to be using this webcam, I'm going to just always have to get used to the fact that it will have to constantly be disconnected and reconnected in order to function. :-/

---

### Post by cristian64 on 2021-06-13
After applying the [https://bugs.archlinux.org/task/68141](https://bugs.archlinux.org/task/68141) patch to the  Linux kernel, I got my USB PHY 2.0 webcam's microphone "working".

Previously, it would record only some sort of funny noise. With this patch applied, it gets the input audio *right* (*).

Documentation for building the kernel in Ubuntu: [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel)


(*)  However, even after amplifying the input audio to maximum level  allowed, the input audio is still way too low. I only get the correct  amplitude if I speak directly to the webcam (5 cm distance or so).  Obviously, that makes the microphone/webcam useless. One wouldn't use  both the webcam and the microphone at the same time... Unless you want  to capture your lips while speaking, which would be an odd use case.

---

### Post by cristian64 on 2021-06-13
I managed to amplify the microphone's volume to a reasonable level with:

[FONT=courier new]pacmd set-source-volume <index> <volume>[/FONT]

Use [FONT=Courier New]pacmd list-sources[/FONT] to figure out the index of the source.

In my case, the the command I ran was:

[FONT=Courier New]pacmd set-source-volume 5 140000[/FONT]

I wish I could have set it a bit higher, but white noise increases notably beyond that level.

---

