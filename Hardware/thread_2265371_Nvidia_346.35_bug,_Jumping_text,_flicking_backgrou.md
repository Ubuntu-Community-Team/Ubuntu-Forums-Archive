---
title: "Nvidia 346.35 bug, Jumping text, flicking background, flasing between tabs firefox."
date: 2015-02-14
forum: Hardware
---

### Post by kingdominsight on 2015-02-14
([COLOR=#ff8c00]Apologies in advance for using the wrong terminologies, i'm new to linux[/COLOR])
Not sure where to post this. 
 Clean install of Nvidia 346.35 though Synaptic. OS 14.04. GTX 750sc graphics card.
[COLOR=#008000]
3d acceleration is absolutely wonderful[/COLOR] given the cards low watt consumption.
However in 2d when using various overlaying windows, mainly Firefox web browser, background images or windows will flicker. Some pages the text will jump up and down, <- :confused: very odd. And sometimes it just goes nuts when the mouse pointer is placed just between two tabs or when a new tab taking a long time to load.

ive been trying to research this issue, but due to not knowing the correct terms for accurate searching iv'e gotten little results.
The closest bug report i can find to it, in symptoms, is #1288747 
I'm not very good with the Linux jargon enough to totally understand the cause and or solution that is, aside from using older drivers.

Any thoughts on this?

---

### Post by kingdominsight on 2015-02-15
OK,, i think i have found a bandaid of a fix, not necessarily solved,, but it seems to be working. I installed Compizconfig Setting manager. Then in the "Utility/workarounds" menu I enabled "Force full screen redraws (buffer swap) on repaint"  seems to be working.   guess i'll tag this as solved unless it creates more problems

---

### Post by aljosa2 on 2015-02-15
[https://bugs.launchpad.net/compiz/+bug/1288747](https://bugs.launchpad.net/compiz/+bug/1288747)

Christopher Townsend (townsend) wrote on 2014-12-08:
Well, we finally have an agreement in place with Nvidia for get their patch into Compiz trunk. Since this bug is really caused by what's in bug #269904, I'm going to dup this bug to that one. I'll comment in that bug as necessary.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904)

Stephen M. Webb (bregma) wrote: 

- This bug is fixed in Compiz release 0.9.12.1 (currently available in Ubuntu "Vivid Vervet")
- This bug has also been fixed in the Ubuntu package compiz-1:0.9.11.3+14.04.20150122-0ubuntu1,
   currently in the trusty-proposed pocket and migrating soon to the trusty-updates pocket (and Ubuntu 14.04.2 LTS)
- The fix for this bug will appear in Compiz release 0.9.11.3 when it gets released in the near future

---

### Post by kingdominsight on 2015-02-15
My Compiz version is 0.9.11.3.  Apparently the bug is still there in fully updated 14.04.1

---

### Post by aljosa2 on 2015-02-16
[COLOR=#333333][FONT=monospace]From the same source:

[/FONT][/COLOR]https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904/comments/367
[I][COLOR=#333333][FONT=monospace]
"A Brief Note on Compiz Versions:[/FONT][/COLOR][COLOR=#333333][FONT=monospace]
Neither Compiz 0.9.11.3 nor Compiz 0.9.11.4 have been released by upstream yet regardless of how Ubuntu versions its packages, athough one of the devs incorrectly changed the Compiz version string to match the Ubuntu package version".[/FONT][/COLOR][/I]

---

