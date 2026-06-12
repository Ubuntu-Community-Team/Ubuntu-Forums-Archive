---
title: "Asus c523n chromebook no audio (dummy audio)"
date: 2021-12-20
forum: Hardware
---

### Post by cha0sthe0ry on 2021-12-20
Let me begin by saying that I have tried the links I could find:

[https://www.reddit.com/r/Ubuntu/comments/m2ey0l/chromebook_with_ubuntu_2004_says_dummy_output/](https://www.reddit.com/r/Ubuntu/comments/m2ey0l/chromebook_with_ubuntu_2004_says_dummy_output/)

[https://askubuntu.com/questions/57810/how-to-fix-no-soundcards-found](https://askubuntu.com/questions/57810/how-to-fix-no-soundcards-found)

[https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a](https://gist.github.com/jeremy-breidenbach/92fc648ed2590ff9cd3a0ae57ed98e4a)

I have replaced the asound.state file and tried the command line items listed therein,  with no luck.

this is my output for lspci:

lspci -v | grep -A7 -i "audio"
00:0e.0 Multimedia audio controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster (rev 0b)
	Subsystem: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Audio Cluster
	Flags: bus master, fast devsel, latency 0, IRQ 25
	Memory at c2b18000 (64-bit, non-prefetchable) [size=16K]
	Memory at c2900000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: snd_soc_skl
	Kernel modules: snd_hda_intel, snd_soc_skl, snd_sof_pci

I can't get this sound card to be recognized in alsa. Any ideas?  Thanks in advance.

---

### Post by TheFu on 2021-12-20
Chromebooks run ChromeOS and have their own support.  Typically, their answers come down to "powerwash" or "reload the OS", IME.  ChromeOS isn't Ubuntu.

If you've loaded an Ubuntu onto the chromebook, then please run the sound-troubleshooter script. Links to it are pinned to the top of the Multimedia sub-forum here. Experts should be able to parse the output from that script and provide exactly the answer.  I know the script is on the UbuntuForums github page, but I don't recall exactly where that is. Google finds it.

---

