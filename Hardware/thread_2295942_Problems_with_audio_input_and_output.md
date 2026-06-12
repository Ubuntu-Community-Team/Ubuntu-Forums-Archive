---
title: "Problems with audio input and output"
date: 2015-09-22
forum: Hardware
---

### Post by Aaron_Lennard on 2015-09-22
I recently completed a clean install to 15.04 and I have been having problems with my audio, I use a set of ear buds on my computer and they work fine for me. At some point my computer started to show in sound options that it couldn't find an audio input or output device (an old web-cam I use for audio) but for some reason it kept on working in my applications, even though it doesn’t display any devices connected I can still hear in VLC, Firefox and civ 5 amongst others. Because of this I only just saw the muted speaker on my toolbar because I couldn't edit my volume except while the app had a toggle for it. This hasn't been a problem however until now when Skype can no longer give or record audio. Also I today installed team speak to find it can record audio as well. I have no idea what's going on so any help would be great thanks!

---

### Post by Yellow Pasque on 2015-09-22
It sounds like pulseaudio isn't running correctly.
This is the first thing I would try
```
rm -r ~/.config/pulse*
pulseaudio -k  #this will give an error if pulseaudio isn't running at all
pulseaudio    #this will give an error if pulseaudio is already running
```

Also, you can alter volume using alsamixer until you fix the issue:
```
alsamixer
```

---

