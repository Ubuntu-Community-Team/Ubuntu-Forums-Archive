---
title: "Apt-get/Synaptic/Update problem (Solved)"
date: 2005-11-23
forum: General Help
---

### Post by riskbreaker927 on 2005-11-23
So yesterday I was updating my computer using that little tool that shows up in the system tray to alert you that there's updates... at the same time, however, I was trying to read some files off a burnt DVD (which I later determined was a coaster.) Because of this bad disc, Ubuntu crashed and I had to do a hard reset (even exiting the X system and typing reboot didn't allow me to do a soft reset because I kept getting buffer error messages from the DVD drive.) Unfortunately this happened during the installation phase of the update; everything had already downloaded, but not everything was fully installed and the progress had come to a stall (presumably because of all the buffer error messages.)

I was able to get back into Ubuntu, but now I cannot use the update tool to finish the update because whenever I go into it I get an error message that an instance Synaptic or Aptitude was still running. What do I have to do to fix it?

Edit: Oh, I got it. I went into Synaptic and looked closer at the error message, noticing it was different from the one I get in the update tool. It told me to run "dpkg --configure -a", and that solved the problem. Do you think you could find a way to place a similar message in the update tool?

---

