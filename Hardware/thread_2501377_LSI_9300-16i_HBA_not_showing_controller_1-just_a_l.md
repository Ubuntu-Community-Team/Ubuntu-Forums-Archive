---
title: "LSI 9300-16i HBA not showing controller 1-just a little help needed"
date: 2024-10-04
forum: Hardware
---

### Post by sgt-mike on 2024-10-04
Bought this HBA LSI 9300-16i. 

According to the configuration it is a Avago Brand (woohoo true LSI) , when it arrived it was already in IT mode so worked well setting up ZFS. 
I had a reboot on the recently built NFS server and seen a glimpse of a bios error on the card, so I pressed ctl-c to see what's up. That is when I noticed that 1 controller was missing. Before this I always noticed controller 0 and 1 in the boot order, when I went into the configuration setup prior.

While I had it in the config mode prior to it dumping controller 1. I noticed the bios version was 8.15.000.000 , and the firmware was version 7. something (I had a fail on writing it down). 

Luckily when I purchased this I have already down loaded the bios and firmware from broadcom's site for both of the cards I ordered the 8i and the 16i. Just in case one showed up in IR mode.

Another plus is at the same time I ordered this one I had ordered a extra LSI 9300-8i (Inspur) so I do have a back up when I am forced to flash the bios and firmware. 

While I have flashed MFM /SCSI drives in the past I haven't done it since mid 1980's so I am leery maybe overly cautious is more accurate. So if anyone would be so kind to say hey PM when you do this if you get stuck I'd be grateful.

Like I stated I do have a spare limp along HBA on the side for when I attempt this. (<<<not installed yet)

Now my understanding is that the 16i version is in layman's term just basically two 9300-8i controllers on one card. And right now it (9300-16i) is running on one controller using ports 2 and 3 (controller 0). Port 0 and 1 (controller1) will not show up nor pickup any drive connected to it. 

Because the 16i was running I in my haste of hey a new toy didn't update the bios or firmware.  
 
Now I do have a Ubuntu box (dell optiplex 3010 with a i5 3gen) not doing anything at the moment. Which in my mind it is best to disconnect the boot drive, boot into the  USB drive to do the flashing.  Thoughts?

I reviewed this git hub post dealing with flashing a 8i which the 16i should be the same procedure just different bios and firmware
[https://github.com/EverLand1/9300-8i_IT-Mode?tab=readme-ov-file](https://github.com/EverLand1/9300-8i_IT-Mode?tab=readme-ov-file) 
 seemed pretty straight forward kinda. 
 I used that guide to do the Boot USB but used the correct firmware and bios files for the 16i. (but I did use the file from there bootx64.efi NOT SURE if it makes a difference in a 16i, as I couldn't locate that file from the broadcom files for the affected card). Thoughts? advice?

But in the post the author mentioned to place a jumper on the raid controller pin. I didn't notice a raid controller pin on the 16i. I'll scour the manual again to see if I just overlooked it.

I also looked here [https://www.truenas.com/community/resources/detailed-newcomers-guide-to-crossflashing-lsi-9211-9300-9305-9311-9400-94xx-hba-and-variants.54/](https://www.truenas.com/community/resources/detailed-newcomers-guide-to-crossflashing-lsi-9211-9300-9305-9311-9400-94xx-hba-and-variants.54/) as a reference as well.  
Is anyone aware of a tutorial that addresses the 16 directly /specifically? 
Thank you in advance

---

### Post by sgt-mike on 2024-10-04
OK went through the flashing process ... painful ... yep Broadcom's software confirmed that a controller is not operational that caused a bunch of errors from -c 0, -c 1 took the firmware and the bios updates like a champ. 
And 1 still is operational. wonder how long that controller will last?
my choices are 
a. return for a refund and reorder
b. get a expander in order to support my drives
c. do both a and b
d. just return it and order a expander with the refund.
e. run two HBA's 

not crazy about using two HBA's although can be done. likely hood of a conflict is pretty good.
I seem to be drawing the bad ones in the 16i's talk about bad luck... 1st one was DOA, second one worked for less than a week.

---

### Post by sgt-mike on 2024-10-05
Just a update on the HBA:
being stubborn I kept up with the LSI 9300-16i 
Finally got to access the bad controller as well as the one that was running via LSI tools flashed the bios and firmware looked like success ...  worked a couple of times now back to original state.

But in the mean time of that occurring I reached out to the company they said that they will send a replacement out. I thanked them, I was very skeptical of them actually doing that but they sent the tracking info .... yep they did I was shocked!!!!!!!!!!!!!! 

If some of ya'll have been following some of my other post I'm trying out ZFS, with the HBA failure it has caused other issues. I completely lost 1 pool, the drive are there and I don't know why it happened. But not too troubled anyway as I was soon going to tear down the pools anyway and add more drives to them. Which the FedEx person should be dropping off today which the way my luck is running the drive will be 520 or 420 sector which I'll address that and get them prepped for my intended pools. <<[COLOR=#0000cd] update [/COLOR][COLOR=#006400]they was 512 sectors right now sg_formatting them in preparation of the Z2 pool figuring on 6 drive wide[/COLOR]
The other issue was all of a sudden my root drives filled up, which thanks to this forum I found the issue and corrected it, saving me from the standard MS answer "just re-install everything".

 I suspect many are not viewing most of the new post s as they  had in the past because the news of the forum going to a transition. But I would like to respectfully point out this right here is why I have stated my opinion to stay the course. Assistance..... The other form of communications that Ubuntu has doesn't do what this site does.

---

