---
title: "No Sound After Fresh 18.04 Install"
date: 2018-06-15
forum: Hardware
---

### Post by promet on 2018-06-15
Hi,

So, new one on me. After struggling with no sound on recent, otherwise pretty cooperative, 18.04 install I found I had no audio. :(

Apps', and card output meters are, "pumping" though. So, good sign, must be something simple, right? After fidgeting with the (excellent):

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_7](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_7)

and all sorts of Pulseaudio, Alsa, etc. (the usual suspects) apps and configs. I thought to myself...,"mehhh...couldn't hurt, right?" and merely reached up to the headphone output on the back of the builtin sound port of my (Asus) desktop machine, unplugged and re-plugged it. Sound...

NOTE: of course, I'm not saying it's that simple, necessarily, a lot of what I tinkered with before may have swayed the odds in my favor. I just thought I'd point this out though, because, after *many* Ubuntu post-install/post-upgrade audio tinkerings I have done, this is the first one where "manual hardware disconnect/reconnect" played any part (that I was able to suss out anyway).

This will now become my first "troubleshooting step" for audio though \\:D/.

BTW, this is an:

```
[TABLE="class: node"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]multimedia[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Audio device[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]SBx00 Azalia (Intel HDA)[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Advanced Micro Devices, Inc. [AMD/ATI][/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]14.2[/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"]pci@0000:00:14.2[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]40[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]64 bits[/TD]
[/TR]
[TR]
[TD="class: first"]clock:[/TD]
[TD="class: second"]33MHz[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]pm bus_master cap_list[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] driver[/TD]
[TD]=[/TD]
[TD]snd_hda_intel[/TD]
[/TR]
[TR]
[TD="class: sub-first"] latency[/TD]
[TD]=[/TD]
[TD]32[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD="class: first"]resources:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] irq[/TD]
[TD]:[/TD]
[TD]16[/TD]
[/TR]
[TR]
[TD="class: sub-first"] memory[/TD]
[TD]:[/TD]
[TD]fe400000-fe403fff[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

```

This is the builtin audio device for the (Asus Computer):

```
[TABLE="class: node"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]core[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]Motherboard[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]M5A99FX PRO R2.0[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]ASUSTeK COMPUTER INC.[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]0[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]Rev 1.xx[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"]130106736200071[/TD]
[/TR]
[TR]
[TD="class: first"]slot:[/TD]
[TD="class: second"]To be filled by O.E.M.[/TD]
[/TR]
[/TABLE]

```


Hope this ends up being of some use.

Best!

---

### Post by Autodave on 2018-06-15
Never over look the simple. I had a friend that once spent over a week trying to find out why his sound wasn't working any more (WinXP). After talking to him on the phone and asking him if the speakers were plugged in and powered on, I made a trip over to his house. They were plugged in, but to the microphone jack!

Another simple fix to remember on a laptop: before trying to figure out why something that was working previously is not working now: power down, disconnect EVERY cable including power cable, remove battery, wait ten minutes, reassemble and try. My success rate on that is over 50%.

---

### Post by dalekky on 2018-08-13
I have the same sound card built into an MSI motherboard. I can't get any of the analog 6 channel sockets to work or even appear in the sound settings as selectable options. I can only get the digtial/s/pdif_out port to work (2 channel)

Kind of makes having a 6 channel speaker setup redundant.

Unplugging and replugging did not magically make the connections suddenly become alive unfortunately.
I have been unable to find a solution. I have a launchpad question here with full details - [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/672087](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/672087)

So far no one has commented.

---

### Post by dalekky on 2018-08-13
haha... Ironically, I just discovered that my issue was also caused by one wrong lead in the wrong socket. (Front speakers plugged into side surround). Returning the front speakers lead to the correct socket instantly made the proper sound options appear in the settings.

---

