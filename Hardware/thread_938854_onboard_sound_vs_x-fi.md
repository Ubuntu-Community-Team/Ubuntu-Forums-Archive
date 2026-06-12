---
title: "onboard sound vs x-fi"
date: 2008-10-05
forum: Hardware
---

### Post by tumble on 2008-10-05
Well I currently have a pc running both Ubuntu 8.04 and WinXp, I have a creative X-fi, pci version too, and on-board sound turned off. Does anyone one know if i can turn back on the on-board sound to work in ubuntu( while keeping the X-fi plugged in) and it not cause problems in XP? The windows driver for it isnt installed anymore.

cheers

---

### Post by markbuntu on 2008-10-05
Yes, you can do that. Just make the onboard card the default device. More on multiple sound cards here:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

Set the onboard to index=0 using the above guide. for now, X-Fi cards are big pain.

---

### Post by tumble on 2008-10-06
many thanks.

---

### Post by go_beep_yourself on 2008-10-13
Do you have speakers hooked up to both cards or do you switch the wires of your speakers between sound cards each time you boot a different OS on your system?

---

### Post by madman_lxl on 2008-10-13
I've been dual booting a few systems all with x-fi cards and run Ubuntu 8.04 with OSS to run them. Setup guide  [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

Might be easier than having two sets of speakers or changing them about.

---

### Post by go_beep_yourself on 2008-10-23
> **madman_lxl said:**
> I've been dual booting a few systems all with x-fi cards and run Ubuntu 8.04 with OSS to run them. Setup guide  [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

Check with the alsa-dev mailing list archives for the past month. The oss driver for xfi has been ported to alsa. The module is called snd-sbxfi. They need people to be testers and report bugs in order to make the driver better, so try it out.

> Might be easier than having two sets of speakers or changing them about.

My onboard high def 6 channel (yes, works with my logitech g51 5.1 surround sound speakers in Ubuntu and Windows just fine) was easier to do and had a higher sample rate than those of xfi cards, so I RMA my xfi pcie soundblaster xfi titanium back to newegg. Creatives tech support were assholes when I mentioned their Linux beta driver to them. They denied having one and refused to look at the webpage with it. If I were to manage to get OSS4.1 rcX to work with the xfi (didnt support my newer xfi pcie model) then it still wouldn't of been worth it with only 2 channel audio (same as stereo). Instead, I Linux crashed when issuing the oss commands soundon and soundoff and not even their developers could help. Creative is garbage and should be boycotted by all Linux users. Newegg is not charging me a 15% restocking fee for returning because I've been such a loyal customer. I'll use the refund money to get a 768gb or more sata2 seagate drive to have automated rsync backups for my raid 0 running Ubuntu on 2x320gb sata2 seagates :)

ANYBODY WHO DOES NOT SUPPORT LINUX, I DO NOT SUPPORT THEM

---

