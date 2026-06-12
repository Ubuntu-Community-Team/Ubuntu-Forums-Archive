---
title: "Hibernate, dual-boot, and flushing the file cache"
date: 2008-10-28
forum: General Help
---

### Post by Ng Oon-Ee on 2008-10-28
Hi all,

Just managed to lose a day's work (from what I've read, I've been lucky it was only a day's work) from my laptop. Here's a step-by-step guide to doing that:-

1) Hibernate one of your dual-boot OSes (Ubuntu in my case)
2) Boot into your other OS (Vista in my case) and do some work, save some files, etc. Hibernate it as well, just to complicate things.
3) Boot into the hibernated Ubuntu. Changes you've made while in your other OS aren't saved, and if you're unlucky the partition itself is corrupted and needs repairing. If you have shared data (such as firefox/thunderbird/pidgin profiles, all of which I use) you'll have to clean them up as well.

I had no idea what had happened, at first, till I realized that this was the first time I'd actually booted into another OS while my main one (Ubuntu) was hibernated (since hibernate never worked for me pre-Intrepid RC). So I've been reading what I could find online, and it seems that no1 knows how to hibernate in a dual-boot.

The main problem here is that when hibernating, the OS (Ubuntu or Windows) saves a file cache (probably of the FAT, or is that an outdated acronym?). [This old thread]("http://ubuntuforums.org/showthread.php?t=32457&highlight=hibernate+dual+boot") describes one forum member's attempts at a solution (which worked, for him, in XP).

Somehow, if the file cache is the only problem, I would have thought it would be possible to instruct the OS to, when hibernating, flush it prior to the hibernate (as done in the above thread). Does anyone know how to do this, at least in Linux/Ubuntu? Then I could hibernate my main OS, I use Vista infrequently enough that I could care less whether it takes a long time to start up.

Ideas appreciated :)

---

### Post by dcstar on 2008-10-28
> **Ng Oon-Ee said:**
> 
\........
Somehow, if the file cache is the only problem, I would have thought it would be possible to instruct the OS to, when hibernating, flush it prior to the hibernate (as done in the above thread). Does anyone know how to do this, at least in Linux/Ubuntu? Then I could hibernate my main OS, I use Vista infrequently enough that I could care less whether it takes a long time to start up.


The command "sync" will flush all pending disk writes in Unix/Linux, but it is problematic when you are essentially simultaneously mounting filesystems with two working O/Ss. You should not be doing it, and the problems you have experienced are exactly why you shouldn't be doing it.

If you want to use two OSs, then install something like VMWare server and run the other OS inside a VM.

---

### Post by Ng Oon-Ee on 2008-10-28
Hey, thanks for answering dcstar :)

> **dcstar said:**
> The command "sync" will flush all pending disk writes in Unix/Linux, but it is problematic when you are essentially simultaneously mounting filesystems with two working O/Ss. You should not be doing it, and the problems you have experienced are exactly why you shouldn't be doing it.

I understand the problems with simultaneous mounting, and the dangers of not properly un-mounting (which basically just consists of flushing the cache anyway). However, I'm unsure exactly why a hibernated system should keep 'possession' of a disk, unless its a disk containing system information or currently open programs. For example, if I had a separate partition containing only mp3s, I'd expect ideally that I could initiate a hibernate when I have no program open which accesses those mp3s and the system would not need to keep that disk (or its access table) in its memory.

If anyone could clear up exactly why OSes need to do this? I'm really quite confused.

> If you want to use two OSs, then install something like VMWare server and run the other OS inside a VM.

That wouldn't be possible in certain cases. For example, I use Ubuntu almost exclusively, except for my sound recording, where I'm very used to Adobe Audition and various Linux alternatives have limitations, such as not being able to work with mp3s (Ardour) or not working well with pulseaudio (Audacity). Running Windows in a VM would incur a lot of overhead which directly affects the quality of my recordings (having 5-6 tracks already playing while recording an overlay is problematic if the VM suddenly slows down when I'm almost done with a particular track, causing me to have to redo it. Latency would probably increase as well, but for my purposes that's easily dealt with.

This isn't really meant as a rebuttal, I agree that for most applications (specifically running 'that last app'), a virtualized Windows installation (let's leave legality out of it) is the way to go. Or Wine, which is my preferred method. Unfortunately, for some applications, such as mine, its not really an option.

---

