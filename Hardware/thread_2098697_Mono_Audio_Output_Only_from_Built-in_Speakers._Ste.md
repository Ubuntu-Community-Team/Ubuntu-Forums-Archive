---
title: "Mono Audio Output Only from Built-in Speakers. Stereo with Headphones."
date: 2012-12-27
forum: Hardware
---

### Post by os2 on 2012-12-27
A peculiar problem.

I have this problem under Ubuntu, Mythbuntu (12.04) and OpenSuse 12.2.

I am only getting Mono audio-output from my built-in notebook speakers. If I plug in a set of headphones into the output-jack, I get Stereo.

Both speakers work fine and the problem is not there under any version of Windows.

I would like to reconfigure my speaker setup in Linux. Can someone explain how to do it?

The audio chip is an Analog-Devices-1981.

):P

---

### Post by Yellow Pasque on 2012-12-27
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by os2 on 2012-12-27
[http://www.alsa-project.org/db/?f=496c6239cdb3e4611292d53b2ee0649cce4cfbd2](http://www.alsa-project.org/db/?f=496c6239cdb3e4611292d53b2ee0649cce4cfbd2)

---

### Post by os2 on 2012-12-27
Perhaps to shed more light on this. Numerous other people seem to have had issues with audio being output from only one speaker. Let's disregard those cases where there was a faulty speaker or line connection.

In this case, it's not that audio is Mono per-se, but both channels are being routed to a single speaker rather than the two speakers.

The audio is noticeably more tiny under Linux than under XP/Vista/7. Not to mention it sounding awful.

As I mentioned, plugging a set of headphones you hear stereo.

---

### Post by os2 on 2012-12-28
Just to provide a little more input on this.

It seems the speaker hardware is working in stereo. It's the Windows drivers which provide some sort of a software-equalizer to better emulate a stereo output. Which is why the audio sounds like Stereo under Windows and Mono/tiny under Linux.

Any more views/suggestions appreciated on this.

---

