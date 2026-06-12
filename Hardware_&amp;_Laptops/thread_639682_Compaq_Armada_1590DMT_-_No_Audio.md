---
title: "Compaq Armada 1590DMT - No Audio"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by iissmart on 2007-12-13
Hi, I have a Compaq Armada 1590DMT, and I got Ubuntu 7.10 Installed using the Alternate install CD, and selected "Install A Command-Line System". After finally getting it set up to a comfortable level, I realized I had no audio, and Ubuntu doesn't even detect a sound card. After looking at [THIS]("http://ubuntuforums.org/showthread.php?t=102&highlight=ess1878") thread, and lots of google searches, I found that this laptop has an ESS1878 sound card in it. But why doesn't Ubuntu autodetect it?

After doing the 3 commands the user in the above thread says he used to get sound to work:
```
sudo modprobe snd-es18xx
sudo modprobe snd-mixer-oss
sudo modprobe snd-pcm-oss
```It still doesn't seem to work, unless I'm forgetting something. Nothing relating to audio or sound shows up in lspci, but when I do lspnp I get this:
```
...
00:10 ESS0004 (unknown)
00:11 ESS1878 (unknown)
...
```It doesn't change after I do the 3 above commands either. Is there any way to get audio to work on this laptop?

---

