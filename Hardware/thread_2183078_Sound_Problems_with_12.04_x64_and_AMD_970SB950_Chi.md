---
title: "Sound Problems with 12.04 x64 and AMD 970/SB950 Chipset Board - Yes more problems..."
date: 2013-10-23
forum: Hardware
---

### Post by lah-ca on 2013-10-23
Hi,

I have a sound card problem, which I will eventually get to discussing somewhere below.  This issue may or may not be part and parcel of the larger issues with the 970/SB950 chip-set and x64 Linux.

 But first let me vent.  I am really pissed off, mostly at myself, for buying a Gibabyte 970A-D3P board (AMD 970/SB950 chipset).  If I had done due diligence, I would have run away screaming.  Secondly I am ticked with AMD.  And I am also ticked with Gigabyte.  But back to myself, I have gotten so used to things just working with contemporary Linux distros that I did not research hardware before buying.  And I was in a real hurry when I bought the board - a minor emergency.  This board is probably the last Gigabyte or AMD-based board I will ever buy.  If you are listening, Gigabyte and AMD, note that consumers vote with their wallets and that PC sales are at a historical 5-year low.  You can't afford to put out boards like the 970A-D3P.  It is reasonable to expect support for contemporary operating systems, and major Linux distros are main-stream enough now, especially among the sort of people who build systems from parts, that you cannot ignore this market.

OK.  Rant over.  Now let me talk about general problems before I get to the sound card issue.

I have overcome most problems with the non-functionality of this board/chipset and 12.04 x64, thanks largely to the bitter experience of others who kindly documented their work here in this forum, notably user monkblah in this thread: [http://ubuntuforums.org/showthread.php?t=2111223&page=3](http://ubuntuforums.org/showthread.php?t=2111223&page=3)

To help others (like me) who may have wandered here in wild-eyed desperation (rather than to steal the thunder of those more knowledgeable than me) I will go over general issues here:

1. The installation wizard for 12.04 x64 cannot create and mount the partitions it needs.  I solved this by changing the disk controller settings in the BIOS from the default IDE to SATA.  Others claim to have solved this by disabling UEFI - I did not try this.

2. The USB2 ports do not work at all (or work intermittently and erratically) after/during installation.  The onboard NIC (Broadcom in my case) does not work at all. These are related issues.  Credit to monkblah for the workaround here: enable IOMMU in the BIOS (see link above).  Also ref: [http://en.wikipedia.org/wiki/IOMMU](http://en.wikipedia.org/wiki/IOMMU)  Note that enabling this seems to slow the POST/Boot sequence by several seconds.

So in summary if you have a board with an AMD 970/SB950 chipset and are hell-bent on installing 12.04 x64, (1) update the BIOS to whatever is current (eventually this may preclude the need for the following steps), (2) change the disk controller settings to SATA (or disable UEFI - can't personally vouch for this UEFI solution), and (3) enable IOMMU in the BIOS (thanks again, monkblah) - then put the installation CD in the optical drive and go.  It should all then be relatively painless.

OK.  Now back to the reason for this post, the sound card.  Mostly it works, but I cannot get any of the input jacks to function.  I have done a lot of the normal things, such as install the Alsa mixer and unmute the inputs which are muted by default, but .... no go ....

Any ideas?  

I may just disable the onboard sound chipset and put in a good but older PCI card.  

 I am tired.  My forehead is bleeding from contact with the edge of my workbench - it took me a while to come to my senses and come here looking for help with the general and more dysfunctional issues (help which I found).  Now the sound card.

:rolleyes:

Edit: forgot to mention sound chipset: VIA VT2021

---

### Post by lah-ca on 2013-10-29
Bump!

I have tried everything in the trouble shooting guides for sound.  Most of the advice/guidance  is inappropriate as there is sound - the sound card works, mostly.  There is sound from the optical drive, games, sound and video clips, etc.  It is just that none of the input jacks work - no line in, no mics.

 I got used a SB Audigy 2 (ex-Dell OEM).  I am reasonably confident that disabling the onboard sound chipset and plugging the Audigy 2 in will resolve the problem here.  But I thought I would bump this thread back up to the top of the stack again.  A real reply on how to get the VIA VT2021 chipset to work completely might be educational for me.

):P

---

### Post by lah-ca on 2013-12-06
Resolved and not resolved.  The input jacks for the VIA chipset still do not work.  The SB Audigy 2 inputs work perfectly.

---

