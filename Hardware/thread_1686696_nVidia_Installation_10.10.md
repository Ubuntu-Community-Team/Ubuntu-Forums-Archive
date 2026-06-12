---
title: "nVidia Installation 10.10"
date: 2011-02-12
forum: Hardware
---

### Post by mark bower on 2011-02-12
I am trying to get nVIDIA drivers installed on a legacy video card (Video-88PCI-16 by Jaton):
- I install the card.  The monitor is connected to the M/B video.  The system boots to a black screen only, no BIOS.  
- If I move the video connection to the card, the system boots thru BIOS, then hangs with a bunch of error msgs, ending in "(initramfs)".
- With the card not installed so that Ubu boots, and I try and install the nVIDIA driver(a .run file) suggested for the card, the installation errors in "no NVIDIA graphics adapter found - which of course is correct.  So,

Two Questions:

1) How do I get the system to boot with the NVIDIA card installed in its PCI slot so that when installing the NVIDIA.run file it sees the adaptor? (The M/B video is an Intel chipset) 

2) There are a number of nVidia libraries seen via Syn Pkg Mgr.  Should things work by only installing the .run from NVIDIA or might some of the libraries also be required to be installed?

I want to avoid breaking my system if possible.

Also, looking for recommendations for a PCI video card that works out of the box (and still available).  I am not a gamer, just need good standard graphics.  I would like to use a card supported by native drivers and avoid the fuss as an option. 

mark bower

---

### Post by jerrrys on 2011-02-12
i run pci and there cheap, 20 bucks and up on eBay.  only thing to watch for is the made in china 6800 series, they had problems

---

### Post by mark bower on 2011-02-13
gonna try again

I downloaded NVIDIA-Linux-x86-71.86.14-pkg1.run.  I need this pkg to run a legacy video card (Jaton Controls "Video-88PCI-16")

With this video card and monitor connected to it, a fresh 10.10 install will only go as far as the "Ubuntu . . . . ." screen.  W/O the card installed, 10.10 detects and works O.K. using the MB video VGA port.  

I tried installing the run file using the M/B video, with the intent of making the software installs, then planned to shut down and reboot with the video card installed.  But at some point the .run installation stops with a message "[1312.994130 NVRM: No NVIDIA graphics adapter found].  And of course, this is correct because the card is not installed.

So how do I do it.  With the video card installed, system hangs.  With video card out, do not get anywhere because .run is looking for the video card.

mark bower

---

### Post by mark bower on 2011-02-13
bump

---

### Post by cascade9 on 2011-02-14
I think that the 71.xx drivers wont work at all with the xorg version in 10.10 (or any other current version, apart from 8.04) 

So even if you get around the hanging problem you still wont be able to install the drivers.

---

### Post by cascade9 on 2011-02-14
Multipule threads, reported so a mod/admin can fix them into one thread.

---

### Post by howefield on 2011-02-14
Threads merged.

---

### Post by mark bower on 2011-02-14
@cascade

thanks for your comments. it is suggested at nVidia.com(I believe), that the 71.xx driver has been updated to work, but not sure about this. The driver is suggested based on the nVIDIA input options at their website, ie, Legacy, TNT and TNT2 series, Linux 32bit.  I am hoping for some additional comments/wisdom.

(things seemed buggy, so reason for multiple posts, did not intend to cause trouble)

mark bower

---

### Post by grahammechanical on 2011-02-14
May I re-state the problem? The built in video adapter in the motherboard is not functioning so you have installed a PCI video card but Ubuntu does not load to the desktop because it is not configured for the replacement video card. Am I guessing right?

I do not know that answer but I suggest that you research booting into a command line console and try to configure the X-server. You need to access the GRUB menu at boot up.

Perhaps you need to change a setting in the BIOS to disable the onboard video card and enable the one in the PCI slot. These are just some thoughts. I may be barking up the wrong tree. Sorry.

Regards.

---

### Post by mark bower on 2011-02-15
@grahammechanical

I seem to not be stating the situation as clearly as possible.  No, the M/B video works just fine (Intel chip).  An AGP card (nVidia) I have works just fine. It is the older Jaton PCI video card that makes the trouble.  Normally I would just move on, but I have 3 or 4 of the Jaton PCI cards which I used in XP on two PC's, and I have one PC not yet assembled.

So the usual problem, a video card works in XP, but not in Ubuntu.

Your 2nd suggestion may be the path, since with the card in the boot makes it to "Ubuntu . . . . ." screen, so surely it would make it to a cmd line console (I do not know how to do that, but can learn)

Lastly, I looked in the BIOS, but did not see anything that might work as an option - but then, doesn't mean it isn't there.

mark bower

---

### Post by cascade9 on 2011-02-15
> **mark bower said:**
> @cascade

thanks for your comments. it is suggested at nVidia.com(I believe), that the 71.xx driver has been updated to work, but not sure about this. The driver is suggested based on the nVIDIA input options at their website, ie, Legacy, TNT and TNT2 series, Linux 32bit.  I am hoping for some additional comments/wisdom.


Nope, it hasnt. 

> 
X doesn't start when configured to use nvidia using nvidia-glx-legacy-71xx
71.86.14-1 due to the current X.Org server video driver API not being
supported by the 71xx series

==-+-=nvidia-glx-legacy-71xx                          | 71.86.14-1
nvidia-kernel-legacy-71xx-dkms                  | 71.86.14-1
nvidia-kernel-legacy-71xx-source                | 71.86.14-1
nvidia-kernel-common                            | 20100522+1
xserver-xorg                                    | 1:7.5+6
xserver-xorg-core                               | 2:1.7.7-4


[http://us.generation-nt.com/bug-596471-nvidia-glx-legacy-71xx-incompatible-current-x-org-server-help-200337291.html](http://us.generation-nt.com/bug-596471-nvidia-glx-legacy-71xx-incompatible-current-x-org-server-help-200337291.html)

Thats from a debian sid/squeeze bug report, but it doesnt really matter- 10.10 is using a much later version of xserver-xorg-core (2:1.9.0) and the same basic version of xsever-xorg (1:7.5+6). 

I'd have to dig around a lot to find it, but I know that of the nvforums one of the staff has said that 71.xx (and 96.xx IIRC) will not be updated to use the newer xserver versions. That was quite some time ago as well.....

---

### Post by mark bower on 2011-02-15
@cascade 9

well, thank you ever so much for your additional comments.  based on your post, i will waste no more time trying to get the older Jaton PCI video cards to work and will either shelve the cards (possible XP use) or off to e-waste.  For the record should someone else access this post, we are talking about the Jaton Control "Video-88PCI-16 card".

mark bower

---

### Post by cascade9 on 2011-02-16
Just because the nvidia drivers wont work with that card (at least with newer xorg versions) doesnt mean they are useless. There is still the .nv driver, at least for the time being, and there is also nouveau. 

That wont help with the problem you are having with whatever computer you are using not booting properly with the card in (intel 8XX chipset by any chance?). I wouldnt waste any more time there, I'd also hang onto the cards just in case. Mind you, I have about 8 cards in my spare parts box, so maybe I'm not the best person to listen to :lolflag:

---

### Post by mark bower on 2011-02-16
you are correct.  the M/B video chipset is Intel 82865G.  i have 3 of the industrial M/Bs which I paid about $600 ea for, so i could get M/Bs with ISA slots as well as PCI.

mark bower

---

### Post by cascade9 on 2011-02-17
Therewas  possibly more than 1 manufacturer who made those 'industrial' P4 motherboards with ISA slots, so maybe my experience with them is not typical......but the one I used I found very picky, and had pretty limited BIOS options. In particular, it was very choosy about RAM. 

They were harder to work with that any 'standard' P4 motherboard I've ever used.

---

### Post by mark bower on 2011-02-17
in my case, the M/B (Advantech AIMB-742) has served all my needs except for the video limitation.  The limitation shows when my menu routine written in FreeBASIC does not function properly when going to screen resolutions lower than the native screen resolution. This is proved when I use a video card that 10.10 (actually starting with 9.04) does accept, and that video card works well for all but very low resolutions, below 640 by 480 - and of course this is not really a limitation since practically no one would go to that low of a resolution anymore.

i have ordered another AGP video card like the one i have that works, and another card with ATI Radeon chipset to see if native 10.10 drivers will operate that card as well.  i am sort of stocking up when AGP (and maybe later a PCI video card) no longer are made for these legacy slots.  Best Buy now only sells PCI-express video cards, same for Fry's Electronics.  i am expecting to use the AIMB-742 boards for maybe the rest of my life - that gives me almost 35 years to go!

mark bower

---

### Post by cascade9 on 2011-02-18
> **mark bower said:**
> i have ordered another AGP video card like the one i have that works, and another card with ATI Radeon chipset to see if native 10.10 drivers will operate that card as well.  i am sort of stocking up when AGP (and maybe later a PCI video card) no longer are made for these legacy slots.  Best Buy now only sells PCI-express video cards, same for Fry's Electronics.  i am expecting to use the AIMB-742 boards for maybe the rest of my life - that gives me almost 35 years to go!

mark bower

A noble quest. I doubt you will get 35 years out of the setup, but I wish you good luck ;) 

BTW, the 6XXX or 7XXX nvidia cards are going to be easier to run into the future then 5XXX/FX, or earlier cards (which are already a pain with ubuntu). ATI/AMD AGP doesnt have any offical linux support, but may well work out to be easier to keep going the long run.

---

### Post by mark bower on 2011-02-18
interesting, while i never mentioned the AGP card that works for me, in fact, it is an nVidia FX5500(you refer to this series).  Ubuntu appears to detect and load the correct nVidia libraries for the FX5500.  I only use the card for 2D.  but now I am warned that i may anticipate downstream support problems for FX55xx - oh boy.  i'll report back re the ATI card.  if Ubu does not auto detect and set it up like the FX5500, i will probably return it.

and to make a correction, my M/Bs with CPU cost (including tax) close to $350 each, not $600 as i said previously.

and to 35 years, well, sort of joking, but i am not one to race to the latest and best when it comes to computers.

mark bower

---

### Post by cascade9 on 2011-02-19
> **mark bower said:**
> interesting, while i never mentioned the AGP card that works for me, in fact, it is an nVidia FX5500(you refer to this series).  Ubuntu appears to detect and load the correct nVidia libraries for the FX5500.  I only use the card for 2D.  but now I am warned that i may anticipate downstream support problems for FX55xx - oh boy.

and to 35 years, well, sort of joking, but i am not one to race to the latest and best when it comes to computers.


So far there have been no issues with the FX seires and ubuntu. The main way you could get trouble is if/when the FX series starts to 'lag' behind the newer xorg versions (the way that the 96.xx drivers have done lately), or get support for newer xorgs totally dropped (the way that the 71.xx seires drivers have). Or if/when wayland hits. 

Hopefully the drivers/xorg issue doesnt become a problem (I wouldnt expect that to start happening for a while yet). Wayland....well, if canonical is thinking, wayland wont be around till the drivers issue with that is sorted as well . IIRC wayland will need KMS (kernel mode switching), and from what I've seen nvidia will NOT be supporting KMS with the proprietary drivers, and the open soruce nouveau drivers has very poor KMS support currently. 

Sorry if I worried you, and hopefuly that clear things up a little. If you want to know more or stil have concerns I'm more than happy to give you more information ;) 

I'm not one to race to the newest platform either...I prefer to let some other schmuck deal with the 'new hardware' issues that always crop up.

---

### Post by mark bower on 2011-02-19
o.k.  i received my HIS Radeon 9250 AGP card and it seems to work o.k. for my FreeBasic graphics.  Actually, Tiger Direct sent me a 9000 vs the 9250, but again, no apparent problem for me.

Wayland, Unity, X windows is a bit over my head, althoh I read Wikipedia re Wayland to get the flavor.  Yes, it appears that one has to wait until things shake out.  in the meantime, i have converted to Ubuntu for all except doing taxes, and ACAD.

mark bower

---

### Post by cascade9 on 2011-02-20
> **mark bower said:**
> o.k.  i received my HIS Radeon 9250 AGP card and it seems to work o.k. for my FreeBasic graphics.  Actually, Tiger Direct sent me a 9000 vs the 9250, but again, no apparent problem for me.

Thats not that bad. There are minor differences between the 9000 and 9250, but nothign that major. 

> **mark bower said:**
> Wayland, Unity, X windows is a bit over my head, althoh I read Wikipedia re Wayland to get the flavor.  Yes, it appears that one has to wait until things shake out.  in the meantime, i have converted to Ubuntu for all except doing taxes, and ACAD.

Yeah, its not worth worring about right now. Que serra serra. 

Good luck with your new card ;)

---

