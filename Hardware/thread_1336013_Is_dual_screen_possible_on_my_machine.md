---
title: "Is dual screen possible on my machine?"
date: 2009-11-24
forum: Hardware
---

### Post by izak on 2009-11-24
Hi all

Before I start trying to get an apparently difficult ting to work, I want to check whether it is possible at all: 

I want to have two screens attached to my PC, (although only one need be active at a time). 

My PC has two video (VGA) outputs: 
1) one from the onboard port (not in use at the moment -- if I plug a monitor in there nothing happens),
2) one from the Gforce2 installed in an AGP slot (configured via xorg.conf to work with my LCD TV). 

Can I use both of these simultaneously, or does one need a single card with two outputs for dual display? Judging by [the wiki page]("https://help.ubuntu.com/community/XineramaHowTo"), that would seem to be the case...

---

### Post by izak on 2009-11-25
Any thoughts?

Based on the wiki discrition, it would seem as if one needs one card with two outputs (as opposed to an output on the card and an output on the motherboard)? 

On the otherhand, this sort of set up would work in Windows, so I cannot see why it should not be able to work in linux?

Getting it to work might be a different issue...

---

### Post by izak on 2009-11-26
Bump,

So no one has any ideas whether one can use ubuntu with two monitors using both VGA outputs from both onboard and a video card?

---

### Post by KeLa on 2009-11-26
If there is no changes what was couple years ago then you can't use them both if they are requiring different drivers (eg nvidia and ati not working same time)

If both display adapters works with the same drivers then it's possible.

---

### Post by Grenage on 2009-11-26
It 'can' work, but I've not done it myself.  You'll have to settle for proprietary drivers on only one card, here's an example:

[http://ryonsherman.wordpress.com/2009/02/10/multiple-monitor-setup-using-both-nvidia-and-ati-video-cards-in-linux/](http://ryonsherman.wordpress.com/2009/02/10/multiple-monitor-setup-using-both-nvidia-and-ati-video-cards-in-linux/)

---

### Post by izak on 2009-11-27
Thanks for the reply.  I am glad to know it might be possible and will look into xinemera.

---

