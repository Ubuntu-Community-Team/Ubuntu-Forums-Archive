---
title: "Sound card not found (Realtek High Definition Audio)"
date: 2007-08-03
forum: Hardware &amp; Laptops
---

### Post by carsten on 2007-08-03
Hi
just bougt a new comp that came with vista, and ofc i coldnt wait to trash it for ubuntu, but unlike my laptop, it didnt find my audio card. In windows its called Realtek High Definition Audio. Any1 know how to install the driver for this one?

---

### Post by rsambuca on 2007-08-03
The Realtek audio should work out-of-the-box with feisty.  What does it say when you enter

lspci 

in the terminal?

---

### Post by ddrichardson on 2007-08-03
If its the revision 2 firmware you're out of luck. They don't work and I've been hoping for an ALSA update that addresses it for a while.

There are several threads where some people have had some success by compiling the 1.0.14a drivers or by appending lines to alsa-base but for most people these don't work.

The good news however is that there seems to be some progress with this firmware recently and it looks like there is progress.

---

### Post by carsten on 2007-08-04
I couldnt post from linux, since my network card stopped working there :S but the line about audio states:

Audio Device: Nvidia Corporation unknown device 03f0

---

### Post by ddrichardson on 2007-08-04
My card is a nVidia MCP51 using Realtek AC880 Codec - it looks like you have the same one. There has been more progress with this driver but it still not functioning. The best anyone seems to achieved is output from the headphone socket.

I have to admit I gave up and bought a USB speaker for my laptop. There are literaly hundreds of threads on this forum and others about these sound cards, but none of the suggestion work on this chipset and I'm afraid its over to ALSA to develop a driver.

Don't be lulled into a false sense of security by Realtek - they offer a driver for Linux but its actually the same one from the 1.0.9 ALSA release and doesn't work with the nVidia cards. I haven't tried the nVidia nForce drivers because they stopped producing them a while ago saying that the kernel now supported it. It doesn't.

---

### Post by carsten on 2007-08-04
i think its really sad that an operating system which ppl wants to be a real alternative to windows, dont even support the most basics of hardware. Its not like this sound card is state of the art or anything....oh well back to waiting agian

---

### Post by ddrichardson on 2007-08-04
To be fair - its nothing to do with the operating system, its to do with the hardware manufacturers and ALSA, not Ubuntu.

Manufacturers are quick to release Windows drivers but not Linux based driver support.

---

### Post by carsten on 2007-08-04
I know its not  ubuntu and much of the blame lies at the manufactures, but still, linux has been around since '91 and the main thinng bugging the system, is lack of drivers - this much be because, the manufacturers is not finding the system attractable enough to support. And i find this odd, because its a great system...just hope we can get past these problems soon...

---

### Post by carsten on 2007-08-04
btw its an nforce 430 chipset

---

### Post by fredj on 2007-08-05
Alsa does support many of the Realtek chipsets. My AC888 worked with Feisty with no problems.
You have to realize that there are many sound cards which still have no Windows Vista support
(and probably never will have) before you start posting nonsense about Linux. Have you ever
really tried installing Windows on a computer or have you only ever bought it pre-installed. All
the sound card drivers in Linux have to be written by the effort of volunteers. I have several
PCs that I would not dare to install Vista on because I know that the sound card drivers do not
exist and never will exist.  

Sorry to rant on about this but I am so tired with these sanctimonious creeps who post saying
that Ubuntu is supposed to work 'out of the box' when they have never done anything to help it
work.

Now lets investigate your sound card. Open a terminal and type 'sudo lshw -class sound' and
post the output from that here. Then also type sudo cat /etc/asound/card0/codec\#* and post
the output from that here.

---

### Post by ddrichardson on 2007-08-05
I'm not being sanctimonious - I'm stating a fact. The nVidia cards have a strange pinout configuration that differs from both Realtek and Sigmatel's pinout datasheets. There is some conflict between the part of the card that produces the output and the soft modem. This has never been resolved and I and many others have tried altering the structures for the driver without much luck.

I've even tried outputing bits incrementaly to all addresses and still cannot overcome this issue. nVidia could help this situation by providing a revised pinout description but as yet haven't replied to my emails.

While I agree that many people whinge without having tried to do anything themselves, you hae to appreciate that Ubuntu is marketed and aimed squarely as a desktop replacement and that any new user is going to frown upon something that works in Windows but not in Ubuntu.

If we as users spent half as much time pestering hardware manufacturers to support alternative OSs as we do helping people asking questions already answered on the forums we might get somewhere.

---

### Post by twistadias on 2007-08-05
Hey guys

im having a similiar problem. just installed ubuntu( my first time) and im baffled at why the sound isnt working.

its a realtek alc861 chipset on a nvidia mobo.

funny thing is that the drivers are installed perfectly. i even installed the mp3 codecs and all that.

the songs play but ther isn't any sound comming out. its not on mute or anything. i went into the advanced properties, by double-clicking on the speaker icon, and increased the speaker volume all the way up.

---

### Post by carsten on 2007-08-05
Well, im not saying it should work of the box, but if the system wants to be real competitor to windows, hardware  has to be supported, and yes the manufacturers have a responsilibity here - else ppl just move to something they know work. That said, since the chipset is not supported i also have no network support in linux, so i will have to find a way to give to the information  - i will return shortly

---

### Post by fredj on 2007-08-05
Carsten I wasn't accusing you of being sanctimonious but some of the other replies to your
post were a bit hard to take. However you have to realise that Ubuntu is not being marketed 
as anything. It's not a commercial product, its free and you are free to adopt it or pay for an
alternative. With regard to your wireless problems there are not many different wireless
chipsets many of them are troublesome in Linux but most of the probelms can be sorted out.
Post that in the wireless and networking forum. To find out which wireless chipset you have
and which driver is being loaded for it open a terminal and type sudo lshw -class network.
Post the result from that in the Wireless and Networking forum.

It may be that there is still no support for your sound chipset in Alsa as yet, just as there is no
proper support for many Creative sound cards in Windows Vista. If you have XP or Vista
drivers for your soundcard and you want it to work now then you may have no alternative 
except to pay for one of these operating systems. You could always run a dual boot system
until Alsa has had a chance to catch up.

Realtek do offer a Linux driver on their website for the ACL880 so at least they are trying.

---

### Post by ddrichardson on 2007-08-06
> **fredj said:**
> Realtek do offer a Linux driver on their website for the ACL880 so at least they are trying.

As I said in an earlier post, the Realtek 880 driver is the ALSA driver or at least a version from 9.0.0 - It doesn't work. While I commend them for supporting Linux, this along with their wireless drivers are hopelessly out of date. The RTL8185L driver for example doesn't compile due to several pointer errors in the source!

If you check boot messages there is an entry regarding accessing memory for the softmodem link - other than this the system acts as if there is sound, only there isn't.

The really annoying thing is that I know its just a question of getting the correct pinouts configured.

One of the problems is to do with confusion between the hardware, codec and the softmodem. Not to mention that the same hardware is masquerading under several different chipset names by several different manufacturers.

---

### Post by fredj on 2007-08-06
Well none of this really helps. What have you done to configure sound in the Alsa mixer for
example? Have you been to the File->Change device menu to make sure that the correct
device is selected. Have you used the File->Preferences Menu to add all the possible volume
controls and switches for playback and record?
Have you opened a terminal and typed Sudo lshw -class sound to see what driver is being
loaded. All you have really told us so far is that sound doesn't work and that this proves the
Alsa driver doesn't work. It doesn't prove anything.

---

### Post by ddrichardson on 2007-08-07
Sir, given the fact that I have spent several months writing a driver is it really likely that I haven't tried to unmute channels in or select the correct device? I wasn't the one who started this thread. The output of lshw -class sound has already shown that the other chaps soundcard is nVidia and if you check the hundreds of other threads and bug reports with ALSA regarding nVidia based sound cards you will see all the usual trite information about settings, recompiling the latest ALSA and defining alsa-base doesn't work.

I only pointed out that this codec and driver is known to be extremely problematic and that the likelihood of getting it working is negligible until more people with the problematic hardware log bug reports.

---

### Post by fredj on 2007-08-08
I don't know what you have already tried until you tell me. What really puzzles me though is
that I see all sorts or reports of people getting their Nvidia ALC880 soundcards working on 
all sorts of flavours of linux under Alsa so I am at a loss to think what could be different about
your particular card.

---

### Post by ddrichardson on 2007-08-08
If you wish to help Carson then crack on - but all I need is an si3054 datasheet ;-). The ALC880 codec is not the problem - its the nvidia hardware. As I'm sure you know there are two parts to the soundcard the firmware and the codec and in the case of nVidia the si3054  modem chipset.

The codec is fine, as I've said. I'm not sure where you've found working cards but there are these bugs registered with ALSA - [3036]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3036"), [2948]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2948") and many others with different manufacturers cards.

As I've stated the problem relates to the integrated modem which utilises the sigmatel 9200 codec (also known as ALC880) and how it interfaces with the chipset most of us working with the driver bugs suspect that there is a bit to control switching between the ALC880 codec and the si3054 modem chip. However, although there is a datasheet available for the soundcard there is not one available for the modem.

There are problems with this codec as well. Some cards, particularly on HP machines work except for the mic and headphone ports. Some work except they produce a high frequency whine. Most cards output the sound via the mic port rather than the speakers and this can be fixed by patching the driver. Some cards - particularly on ASUS boards work if the card type is specified directly in alsa-base.

However the nVidia HDA Realtek doesn't work at all, and as yet no-one has managed to get anywhere with it on any Gateway based system.

Given that Carson's card is an unrecognised nVidia HDA model - his chances of getting it working are at present unlikely. Like I said I've been juggling with this for months and getting nowhere fast.

Thanks for trying to help but what I'm trying to get across is that this isn't a quick fix - its a major bug that even ALSA are toiling to fix.

---

### Post by fredj on 2007-08-09
ddrichardson I would be happy to send you a copy of the technical documentation for the
si3054 but it is easily obtainable from the Silicon Labs website. Let me know if you need a copy.

---

### Post by ddrichardson on 2007-08-09
Sorry I should be more clear - I've checked out the si3054 datasheet from the site you mention. But typically for this infernal chipset there now appears to be a further spanner in the works in that there are two interfaces configured by the chipset to interact with the HDA or AC97.

We may have been (;-)) working in the wrong direction with this as the problem may lay more in the Si3054's driver - we always suspected it to be inhibiting the soundcard - I now wonder if it is addressing the wrong interface.

This would explain why some configurations function and some don't.

---

### Post by fredj on 2007-08-10
Yes I noticed that the modem chip could be used either in a HDA or 97 type sound setup. Makes
sense to be versatile from the manufacturers point of view. I take it the sound setup on the 
Gateway is HDA. I will do some more searching around myself and let you know if I find anything
useful. Has anybody tried the OSS drivers on this rather than the ones from Alsa which only
emulate OSS.

---

### Post by ddrichardson on 2007-08-10
We've tried OSS - which seems successful with most Reateks except the nVidia with the si modem chipset. Still has the same problems with the mic input though. Cheers.

---

