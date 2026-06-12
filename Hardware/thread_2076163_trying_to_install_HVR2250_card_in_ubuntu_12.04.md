---
title: "trying to install HVR2250 card in ubuntu 12.04"
date: 2012-10-25
forum: Hardware
---

### Post by Dougustine on 2012-10-25
okay, I have searched forums and everything and the closest to success is this webpage
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

I think the driver is compatible and I have started installing it and found general success following the instruction until this paragraph:

**Note: this method (as of 2012/03/02) will only give NTSC for analog TV, the driver does not have PAL support. You can at this point patch your code with the patch here: [http://thread.gmane.org/gmane.linux.drivers.video-input-infrastructure/26212/focus=26524](http://thread.gmane.org/gmane.linux.drivers.video-input-infrastructure/26212/focus=26524). A bit of fiddling is needed to apply the patch in the newer kernels, but I have it working with 3.2.1. Apply the patch to the linux subdirectory of the git archive (after calling ./build.sh), and then call ./build again (or just make). --- patch for 3.2.1-gentoo kernel: [https://github.com/reinhrst/nl.claude.tools/tree/2594dd91cb81a3c905a53b9168f52a42e317cd1f/misc](https://github.com/reinhrst/nl.claude.tools/tree/2594dd91cb81a3c905a53b9168f52a42e317cd1f/misc)**

how do I apply this patch? where do I put it? I need this card to work so if this is the wrong path please let me know and I will try again somewhere else(I unistall unbuntu after every failure and try again)

---

