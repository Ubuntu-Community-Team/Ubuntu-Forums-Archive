---
title: "External Sound Card"
date: 2005-11-26
forum: Hardware &amp; Laptops
---

### Post by SimoneDice on 2005-11-26
Hello

I have searched, but been unable to find any definitive information on this within the forums or online.  I am currently running Ubuntu Breezy on a Dell Precision M60 and everything is working great.  However, I would like to add a 5.1 surround sound speaker system to my computer.  For this to work, it would be best to use a 5.1 sound card.

I have found a 5.1 audio card that connects through USB and have included the name of it below.

Creative USB Sound Blaster Live! 24Bit External Sound Card - 70SB049000000

I have a couple of questions.

1: I believe this is supported in Linux by my searches.  Has anyone had any experience with this and will this work?

2: Will having 2 sound cards be a problem?

3: Does anyone know of anything that I should be concerned about that I haven't included in this post?

Any help would be greatly appreciated.  Since it costs around $55, it would be nice to know if it will for sure not work or if this solution I am proposing is not the best route.

S-

---

### Post by amohanty on 2005-11-27
I have an A8N-SLI which comes with a built in AC-97 sound thingamajig. I also have a n Audigy 2ZS (PCI). 

In my default setup I disabled AC-97 audio via my BIOS and I have full 5.1 SS on my Logitech thingy via the Audigy. Just for the heck of it I enabled the AC-97 and aside from having to setup the output in Multimedia Selector I did not have to do anything. However please be warned that the above experience should in no way construed to be any form of solid testing and I would advise turning of the on board audio.

HTH
AM

---

### Post by XXFCTEXX on 2005-12-08
I have a USB Soundblaster and if you had it plugged in while you installed Ubuntu it should have installed the driver. It may recognize it just by using hotplug, but you have to go to your sound settings and select it.

You just go to -System> Preferences> Sound- and then find the "default soundcard" field and select your Sound Blaster. 

The only problem is that anything other than system sounds does not work. Games in Cedega and music from Streamtuner does not play for some reason only system sounds. :(

---

