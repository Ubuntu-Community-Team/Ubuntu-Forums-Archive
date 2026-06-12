---
title: "Asus laptop audio problems"
date: 2016-12-06
forum: Hardware
---

### Post by helpme1230 on 2016-12-06
Hi, I have an old asus x550c that I have installed ubuntu onto, I want to use the microphone in on the laptop instead of the inbuilt laptop microphone, I have used a 3.5 mm splitter for combo 3.5mm jacks (4 pins) as it is for both headphone out and speaker out of the laptop, The issue is it is not detecting the external microphone when I plug it in, the interesting part is that it detects the headphones when they are plugged in but not the microphone, The interesting part is that when the laptop used to run windows the audio manager would detect the microphone plugged in so I assume it's a driver issue? 


The splitter I am using [https://www.amazon.co.uk/WER-Headsets-Headphone-Microphone-Plugs-3-5mm/dp/B014H6WNCK/ref=sr_1_1?ie=UTF8&qid=1481052127&sr=8-1&keywords=WER+Headset+Adapter+for+Headsets+with+Separate+Headphone+%2F+Microphone+Plugs-3.5mm+4+Pin+to+2x+3+Pin+3.5mm+M%2Ff](https://www.amazon.co.uk/WER-Headsets-Headphone-Microphone-Plugs-3-5mm/dp/B014H6WNCK/ref=sr_1_1?ie=UTF8&qid=1481052127&sr=8-1&keywords=WER+Headset+Adapter+for+Headsets+with+Separate+Headphone+%2F+Microphone+Plugs-3.5mm+4+Pin+to+2x+3+Pin+3.5mm+M%2Ff)   

Thanks.

---

### Post by helpme1230 on 2016-12-09
> **helpme1230 said:**
> Hi, I have an old asus x550c that I have installed ubuntu onto, I want to use the microphone in on the laptop instead of the inbuilt laptop microphone, I have used a 3.5 mm splitter for combo 3.5mm jacks (4 pins) as it is for both headphone out and speaker out of the laptop, The issue is it is not detecting the external microphone when I plug it in, the interesting part is that it detects the headphones when they are plugged in but not the microphone, The interesting part is that when the laptop used to run windows the audio manager would detect the microphone plugged in so I assume it's a driver issue? 


The splitter I am using [https://www.amazon.co.uk/WER-Headsets-Headphone-Microphone-Plugs-3-5mm/dp/B014H6WNCK/ref=sr_1_1?ie=UTF8&qid=1481052127&sr=8-1&keywords=WER+Headset+Adapter+for+Headsets+with+Separate+Headphone+%2F+Microphone+Plugs-3.5mm+4+Pin+to+2x+3+Pin+3.5mm+M%2Ff](https://www.amazon.co.uk/WER-Headsets-Headphone-Microphone-Plugs-3-5mm/dp/B014H6WNCK/ref=sr_1_1?ie=UTF8&qid=1481052127&sr=8-1&keywords=WER+Headset+Adapter+for+Headsets+with+Separate+Headphone+%2F+Microphone+Plugs-3.5mm+4+Pin+to+2x+3+Pin+3.5mm+M%2Ff)   

Thanks.

Thread bump

---

### Post by Yellow Pasque on 2016-12-09
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
I don't know if I'll personally be able to help since I don't have a ton of knowledge with input/microphones (especially when pulseaudio gets involved), but maybe we'll see something in the output.

---

### Post by helpme1230 on 2016-12-09
Here is the information from the alsainfo.  [http://www.alsa-project.org/db/?f=e5934a490bc37dcebc0c83ea2b615ad9ed498493](http://www.alsa-project.org/db/?f=e5934a490bc37dcebc0c83ea2b615ad9ed498493)

[LIST] 
[/LIST]

---

### Post by helpme1230 on 2016-12-09
To clarify, the external microphone is NOT detected when plugged in however it will detect headphones when I plug them in, I am using this splitter which is a combo splitter 4 pin appropriate for the combo 3.5mm jack on the laptop.
 [IMG]http://i.imgur.com/jwuKXdN.png[/IMG]

---

### Post by Yellow Pasque on 2016-12-10
```
[   37.175031] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC270: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[   37.175037] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   37.175049] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   37.175051] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[   37.175053] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[   37.175056] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x19
```

```
sudo apt-get install alsa-tools-gui
sudo hdajackretask
```

I kind of suspect pin 0x18 might be the key, but it's a shot in the dark. I'm sorry I can't be more specific :\

---

