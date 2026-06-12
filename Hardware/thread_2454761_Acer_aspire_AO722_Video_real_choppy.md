---
title: "Acer aspire AO722 Video real choppy"
date: 2020-12-05
forum: Hardware
---

### Post by ssulaco on 2020-12-05
I purchased the Aspire back in 2012 I believe and shortly after I uninstalled Windows and loaded Lubuntu,(currently running 16.04 Xenial 64 bit)...Im wanting to see if upgrading the driver on this chip will help in playing .mkv videos,(they stutter and are choppy in VLC and other players)....Went to additional drivers to see if there was a newer version there but there was nothing...Does that mean I'm out of luck?...Or maybe my Aspire is just lacking Horsepower to run certain videos?  Thanks in advance,

---

### Post by CatKiller on 2020-12-05
> **ssulaco said:**
> (currently running 16.04 Xenial 64 bit)...Im wanting to see if upgrading the driver on this chip will help in playing .mkv videos,(they stutter and are choppy in VLC and other players)
MKV is just the container: it doesn't tell you anything about the video that's inside. In particular, it doesn't tell you whether the encoding is one that your hardware can accelerate the decoding of. VLC, particularly old VLC, doesn't support using hardware to accelerate playback; mpv got that capability earlier. Your CPU is too weak to be able to decode well in software.

The way to get newer drivers is to upgrade the OS. The LTS of the Ubuntu flavours only lasts for 3 years, so you need to upgrade anyway: your Lubuntu 16.04 ran out of support last year.

---

### Post by Autodave on 2020-12-05
Your Aspire could be "aspiring" to be replaced. :-)  Do you have the specs for that machine or at least a model # that we can look up?

---

### Post by ssulaco on 2020-12-05
> **CatKiller said:**
> Your CPU is too weak to be able to decode well in software.
The way to get newer drivers is to upgrade the OS. The LTS of the Ubuntu flavours only lasts for 3 years, so you need to upgrade anyway: your Lubuntu 16.04 ran out of support last year.
Thank you CatKiller.....Yes I knew it was not supported anymore but didnt even think about the driver updates..It seems to play .mp4 files better than .mkv
Im using ffmpeg to convert an .mkv to .mp4. Ill post to let you know how it works.

> **Autodave said:**
> Your Aspire could be "aspiring" to be replaced. :-)  Do you have the specs for that machine or at least a model # that we can look up?
Thank you Autodave..CPU is an AMD dual-core C60, 2 gb DDR3 memory,....I too believe CPU is not able to handle Videos anymore but thought upgrading the video driver might just help out.

Thank you both again.

---

### Post by guiverc on 2020-12-06
I'll repeat that Lubuntu [16.04 LTS ]("https://lubuntu.me/xenial-5-released/")is *end-of-life*. 

You mention a dual core CPU, 2gb DDR3 memory... I tested Lubuntu releases up to 19.04 using single core processors and 1gb DDR1 memory (i386 only, boxes as old as from 2003) and use more modern c2d (& better) boxes for all [amd64] releases up to the current *development* release (now 2GB is the minimum memory used in testing). I don't see why you're opting for the EOL release.

LTS releases come with two software stacks, ie. the GA kernel (4.4) or the HWE kernel (4.15) which allows you to have a later software stack (and thus later kernel modules [*drivers*]). You didn't specify which stack you're using, but that gives you two options for any LTS release.

Next if you're suffering tearing etc, there are options you can change for most video stacks (radeon, intel etc), let alone using compton.  Because of the EOL release I won't offer more beyond those hints.

---

### Post by ssulaco on 2020-12-06
Just finished upgrading to 18.04 LTS,...Curious thing is that I've discovered not all .mkv video files are the same,...Some will play fine on my Acer while others do not, Of the ones that do not I am in the process of using  "HandBrake" Transcoder which spits out a .m4v. Which plays great in VLC and MPV media player.

---

### Post by CelticWarrior on 2020-12-06
> **ssulaco said:**
> Curious thing is that I've discovered not all .mkv video files are the same

Absolutely, but why are you surpised? You were told exactly that yeasterday. Please read post #2. Quoting:
> [COLOR=#000000]MKV is just the container: it doesn't tell you anything about the video that's inside. In particular, it doesn't tell you whether the encoding is one that your hardware can accelerate the decoding of.[/COLOR]

---

