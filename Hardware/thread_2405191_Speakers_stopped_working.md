---
title: "Speakers stopped working"
date: 2018-11-02
forum: Hardware
---

### Post by luxocrypto on 2018-11-02
My monitor has built-in speakers. It's connected to my desktop using HDMI. Speakers work fine, connection is audio jack. Ubuntu v18.


  Audio stopped working a few days ago. The only thing I can think of is the  connection of the monitor to the desktop: I changed that to DisplayPort. Could this be  related?



Here's what I did: $ pacmd, followed by >>> list-sinks. I noticed my sound car was SUSPENDED. This is because my Power Saving settings. So I made the 50alsa script from this page: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)  
This morning I checked and the audio card is RUNNING. But no audio...  When I go to Settings > Sound everything looks OK. Output volume is  ON. When I open Chrome and FF and Youtube I see both in the list of  applications. Again, soundcard, speakers, everything *should* work. It worked fine up until I changed my monitor from HDMI to DisplayPort...

---

### Post by #&amp;thj^% on 2018-11-02
Did  you by chance notice at the top of page:>>_"Warning /!\ As of 2012, much of the information on this page is outdated. Please refer to the official sound debugging guide and Ubuntu Audio Development team's pages for more up-to-date information."_

I'm not sure what you followed is harmful (To your sound system) though. ;)
I have a thought though, lets look at the output from:
```
grep "Codec:" /proc/asound/card*/codec*

```
Mine shows:
```
grep "Codec:" /proc/asound/card*/codec*
/proc/asound/card0/codec#0:Codec: Realtek ALC3202
/proc/asound/card0/codec#3:Codec: Intel PantherPoint HDMI

```
You may have to try tripping a few options in pulseaudio volume control.

---

### Post by slickymaster on 2018-11-02
Thread moved to **Hardware** for a better fit

---

### Post by luxocrypto on 2018-11-02
Mine shows:

Codec: Analog Devices AD1984A

I don't have Pulse installed - should I?

---

### Post by luxocrypto on 2018-12-04
I have found it myself:
- when connecting the Benq monitor to my PC using Displayport the monitor works fine, but the built-in speakers don't work.
- when connecting my Benq monitor to my PC using HDMI the monitor works fine, and the built-in speakers work fine, too.

Weird, isn't it?

---

