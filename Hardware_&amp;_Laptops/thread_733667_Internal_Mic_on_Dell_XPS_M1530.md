---
title: "Internal Mic on Dell XPS M1530"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-03-24
I have been trying to get the internal mic working on my Dell XPS M1530 in ubuntu. I have tried two guides so far, neither worked. First I installed some back port packages from dell as explained here:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

Then I used another guide that installed some alsa software but also said specificly not to do what I had just done. That is explained here:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4425938](http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4425938)

Nothing has worked so far. The last guide tells me to go to the alsa mixer and set the digital input source to digital mic 1 but that option is not available.

How do I get this mic working?

---

### Post by BandD on 2008-03-24
Could you post the result of this code run in a terminal:

```
lspci | grep Audio
```

I know that you have an Intel HDA card, but it'll help to know which model exactly.

You can also check out these two threads:

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

and

[http://ohioloco.ubuntuforums.org/showthread.php?t=530374]("http://ohioloco.ubuntuforums.org/showthread.php?t=530374")

Which helped me to get my mic working with an Intel HDA ICH6 card.

---

### Post by JaggedOne on 2008-03-24
Here is the output of the command you told me to run.

> 
sam@seXPS:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


I did the first parts of those two guides. No good. I got lost going through the first guide though at this point:
>     *

      You should open a file in ALSA documentation. This file is here (replace KERNEL_VERSION with your kernel's version!):

/usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt

If you didn't have this file, for version 2.6.22, you can check out [WWW] this link or you can find ALSA-Configuration.txt in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.x.x directory you created.

    *

      Search for your model, and take a look at its types, for example I found the following lines for ALC260:

hp              HP machines
hp-3013         HP machines (3013-variant)
fujitsu         Fujitsu S7020
acer            Acer TravelMate
basic           fixed pin assignment (old default model)
auto            auto-config reading BIOS (default)

Read all of them and try to find the one which is more similar to your sound card, for example if you have a laptop, you can choose "acer".

    *

      Open /etc/modprobe.d/alsa-base with the following command:

sudo nano /etc/modprobe.d/alsa-base

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)):

options snd-hda-intel model=MODEL


I couldn't find that documenation file the guide instructed me to find. The alternative link it provided confused me.

I ran this command like it said::
> cat /proc/asound/card0/codec#* | grep Codec
and go this output:
> Codec: SigmaTel STAC9228

It wants me to add this option to my alsa-base file:
> options snd-hda-intel model=MODEL
But I don't know what to put in for MODEL.

---

### Post by BandD on 2008-03-24
The alternative link takes you to ALL the optional modules that are supported in the Linux Kernel.  If you search down the list a bit (or use your brower's FIND feature) you'll find the Intel HDA section and if you search down a little more for STAC9228 and you'll find this:

```
STAC9227/9228/9229/927x
  ref		Reference board
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  dell-3stack	Dell Dimension E520
```

I'm not sure of the exact set up of your model, but the 'dell-3stack' might work out for you.  Your options for MODEL are anything in that left column.  So give 'em a shot, one by one with a restart inbetween each one and see if you have any luck.

You also might want to make sure that the alsamixer levels are up to a reasonable level for all the capture options AFTER you restart.  Just go to the terminal and type alsamixer.  It'll bring up a graphical equalizer-ish thing.  Hit TAB once to go from PLAYBACK to CAPTURE.  Make sure nothing is muted there and that the levels are set reasonably.

EDIT:  I came across this on the openSUSE forums that deals basically with the exact same thing it'll at least give you more info:  [http://www.suseforums.net/index.php?showtopic=47396#]("http://www.suseforums.net/index.php?showtopic=47396#")  see post #4

---

### Post by jespdj on 2008-03-27
[HOWTO: XPS M1530 internal microphone (resolved)](http://ubuntuforums.org/showthread.php?t=702642)

---

