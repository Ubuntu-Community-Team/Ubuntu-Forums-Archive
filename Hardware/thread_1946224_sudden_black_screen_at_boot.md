---
title: "sudden black screen at boot"
date: 2012-03-24
forum: Hardware
---

### Post by s44 on 2012-03-24
Hi everyone.

Yesterday, I was watching a video with vlc ; transmission and firefox were running too. Suddenly, the screen froze, I was still hearing the audio from the video but everything else had gone numb. I've been having some firefox issues lately, but no system freezing (ever).

This time, no mouse moving, no keyboard answer, impossible to go to a console by ctrl+alt+f1, but the fan was spinning faster and faster, the temperature was getting over the threshold and then I hit the power button for the deadly 10 seconds to let it cool down.

Since then, **I have grub launching** (fortunately, that's why I can write now, because my 32bits ubuntu is still working) but as soon as the os boots (recovery or not), **after a few messages the screen goes black.** I can't figure out reading the dmesg where it happens. I think the startup process goes on after that black out but I'm not sure what happens. **The screen is black but I still can get the light brighter or darker**, it's not a lighting problem, it's a black screen display (like a blue screen... but black u_u)

I thought it might be a hard drive problem, but fsck says **my disk is clean** and I can mount every partition and read the contents.

I thought it might be an acpi problem because when I look up "black screen linux" that's what I get, but people talking about that are usually new installers, and I've got my linux running for years on this laptop, and I didn't make any updates since last boot so I think it's not an update problem, and as I've never managed to compile a kernel in 15 years, I am very much afraid of having to try it to get my corrected version of dsdt (yes, I've done the work to correct my dsdt file just in case) into my kernel.

[I]Anyway, as i can't run my problematic os, I don't know how I could copy dsdt.hex into the kernel variable ($sys/include?) anyway, and compile.
[/I]
I'm including my dmesg, in case it helps.

What I'm asking for:
[B]- can you, by reading my dmesg, understand what is my problem?
- do I really have to remake my kernel or might there be another solution?[/B]

---

### Post by s44 on 2012-03-24
Okay, so **I've managed to solve my problem**, I'm gonna try and find the solved button for this thread, but before that I'm going to explain how, even though noone had the kindness to drop bye in those few hours.

I still don't know why I had this issue, and I forgot to mention I'm running the beta version of skype which is taking loads of resources (2.5% of cpu while not on chat!) and maybe it bugged my system in some way.

I finally managed to boot the rescue version of my system (don't know why) and it stopped after mentionning an acpi asset. So I supposed I was right in my attempts to find an acpi oriented solution and got back to google about that, thinking maybe modprobe could save me from recompiling the kernel (I couldn't chroot for some reason so it would have been difficult anyway). And there was my answer. I **modprobe**'d every module I could think of, related to acpi. **(thermal, ac, battery, fan, acpi-cpufreq, button, processor**) Some of them were loaded, some not. And then I was able to boot properly without anymore difficulty.

This was my first post on a linux forum, the very first time in all those years I thought I couldn't find the answer by myself. Fortunately for me I was able to find it in the end, since this problem doesn't seem to rush any interest. I would have appreciated something like "you can find your solution looking for modprobe on google" if anyone of you had thought it was too obvious a solution to even take some seconds to answer.

Anyway, I want to thank the users of this (and many others) forum **for the help they gave me without even knowing it for the past 15 years. Thank you.**

---

