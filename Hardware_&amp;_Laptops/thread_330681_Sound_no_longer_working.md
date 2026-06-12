---
title: "Sound no longer working"
date: 2007-01-03
forum: Hardware &amp; Laptops
---

### Post by scratched on 2007-01-03
I just moved from Breezy Badger to a fresh reformat & install of Edgy Eft. After I restored my files, I tried using my TV tuner card. In Breezy Badger, I got sound (thanks to a small shell script) but no video.

In Edgy, I am getting video, but the sound is no longer working. I got the sound to work in Breezy with a shell script I found in this old forum post:
[http://ubuntuforums.org/showthread.php?t=172085]("http://ubuntuforums.org/showthread.php?t=172085")

I don't know much about sound in Ubuntu so I don't have any clue what this script does, all I know is it worked in Breezy and it doesn't in Edgy. Here is the script I'm using:

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute
```

[COLOR="Red"]**[SIZE="4"]UPDATE:[/SIZE]**[/COLOR] As soon as I posted this I thought of how to fix it. I needed the `sox` package to use the script. All I had to do was type this in a terminal:
```
sudo apt-get install sox
```

---

