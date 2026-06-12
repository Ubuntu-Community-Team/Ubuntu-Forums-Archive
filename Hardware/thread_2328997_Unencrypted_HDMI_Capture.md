---
title: "Unencrypted HDMI Capture"
date: 2016-06-26
forum: Hardware
---

### Post by Blair_Vidakovich on 2016-06-26
Forgive me if I am doubling up on a thread already dealing with this topic. I cannot find anything relevant by searching.

I have been using the trusty old Hauppauge HD PVR to capture composite video for a while now. Ubuntu is perfect for this task.

I am using PAL source equipment, and the HD PVR captures at NTSC frame-rates, so when I capture 25 FPS PAL, I get 24.975, which leads to audio sync issues. This is very frustrating, but I have some work-arounds in post-production.

My question is, are there any better analogue composite capture cards or external capture boxes for Ubuntu linux?

I am also interested in capturing 1080p unencrypted HDMI video from my game consoles. Is there a capture box compatible with Ubuntu that does that?

Thanks for your time.

---

### Post by TheFu on 2016-06-27
Other threads about HDMI capture below. OTOH, don't really deal with PAL here, so YMMV.  I have purchased PAL DVDs and ripped them - love the higher resolution than NTSC DVDs.

[http://ubuntuforums.org/showthread.php?t=2298378&highlight=hdmi+recording](http://ubuntuforums.org/showthread.php?t=2298378&highlight=hdmi+recording)
[http://ubuntuforums.org/showthread.php?t=2301101&highlight=hdmi+recording](http://ubuntuforums.org/showthread.php?t=2301101&highlight=hdmi+recording)

Short answer is that if stereo audio is sufficient, then US$80 solves the recording issue.

If you need 5.1 DD audio, it becomes a more expensive issue - $350+.  I've burned out 3 Haupauge 1512 devices (Windows only). 2 during the warranty period, so cannot recommend these. Plus they don't support DD+, just DD and AC3 passthru.  Hauppauge provided me with alpha drivers for the 1512, but not the correct model (seems they make 3 models based on different chips). Never got any of it working, though it did compile. 

Been using a standalone HDMI recording box for about 9 months now. No computer needed except to merge the recorded files back together and edit. This box makes huge (barely compressed) videos in h.264/aac/mp4 containers.  Re-compression reduces the files from 10G to 2G (or smaller) - I use handbrake.

If you must have a Linux computer in the mix for recording, Blackmagic PCIx cards seem to be the best. None of the USB connected devices I've seen support Linux, but haven't looked in about 6 months.  For non-HiDef captures, there are lots and lots of other options.

A friend just sent me this link: [https://blog.benjojo.co.uk/post/cheap-hdmi-capture-for-linux](https://blog.benjojo.co.uk/post/cheap-hdmi-capture-for-linux)  Don't know **anything** about it.

---

