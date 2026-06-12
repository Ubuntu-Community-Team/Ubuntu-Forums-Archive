---
title: "What is the fastest disk writing format?"
date: 2017-02-11
forum: Hardware
---

### Post by Autodave on 2017-02-11
I am putting together a new machine for recording audio. I am interested in knowing what to format the drive to that will have the quickest write times.  The machine will have 2 HDs: one to handle running Audacity and the second one for recording.  Speed of writing to the disk is the most important thing that I need.  I will be recording 18 channels via USB cable from board to PC. What formatting should I use for the recording disk?

Thanks in advance!

---

### Post by ajgreeny on 2017-02-11
I suspect the limiting factor will be the USB cable not the filesystem you choose, all of which will be fast enough for what you need.

---

### Post by Autodave on 2017-02-11
Actually, I have a machine doing this job now. The USB is not the issue: recording 18 tracks at once, at .wav quality is the issue. A 15 minute recording uses about 5 - 6 gig of HD space.  A 5,400 RPM HD will not keep up: I must use a 7,200. Further, I go with the one that has the largest cache on board. I am on my 5th build right now and it always comes down to how much I can get the HD to accept at a time. Processor speed and RAM seem to have little impact on it.

Current machine is only a 2.8 dual core w/4 gig RAM.  I have used a 3.4 quad core w/8 gig RAM, and still had probs because of the HD not being able to keep up. That is why I am interested in knowing what format would be the fastest to write to.  I know that I could always go to an SSD, but since this is a "donated" machine, I am trying to not go that route and use one of the many HDs laying around my PC workbench.

---

### Post by ajgreeny on 2017-02-11
In that case the problem is not the filesystem used but the fact that you have a spinning disk.

It sounds as if you need to consider using a large SSD to write to as you mention, and that will be a lot faster.

---

### Post by Autodave on 2017-02-11
I understand that completely, but I am still the one funding this endeavor. Until I can have all SSDs in my own machines, I can't afford one fot that machine. That is why I was wandering what type of formatting would be best for speed.

---

### Post by The Cog on 2017-02-11
I doubt if there is much difference between filesystems in that respect. It may help to go with a raid array and stripe the data across a number of disks though. A second disk should double your throughput.

---

### Post by oldfred on 2017-02-11
Some comparisons, but type of data written makes a difference. 
And some file system settings may slow write but make for more reliability. Write before journal may give speed, but you are not sure data is there until journal is updated.
 see man tune2fs 

Depends a lot on type of data written. Small files, large files, text, database etc.
So different tests give somewhat different results.But overall ext4 seems to be better.

[http://www.phoronix.com/scan.php?page=article&item=4fs-linux-4649&num=1](http://www.phoronix.com/scan.php?page=article&item=4fs-linux-4649&num=1)

---

### Post by Bucky Ball on 2017-02-11
> **The Cog said:**
> I doubt if there is much difference between filesystems in that respect. It may help to go with a raid array and stripe the data across a number of disks though. A second disk should double your throughput.

RAID can get awfully confusing, and inconvenient, on a home DAW. :)

Main reason is because you want apps on one drive, any sound samples you are using on another and to be recording, preferably on a blank drive.

@Autodave: if you are not going for the disk plan above, then that could be a problem. If you are running your recording apps and recording onto the same drive, and that drive is a 5400, then there's your issue. Ideally you should have three or four drives in there. One for the OS and apps, one to record to, one for VST instruments and effects if you're using them and another for mixdowns from the audio apps to finished product.

That's a basic set up. If you're running the machine with one 5400 drive and trying to record 18 tracks at once, then that is the problem. I have three 7200rpm drives for recording, mixdowns and backups and an SSD for OS and apps. (Some people run apps on a separate drive too). Yes, audio recording on a home computer can be done 'on the cheap', but it comes with the limitations of that frugality. Sounds like you're after pro results on a bespoke computer. Unlikely, but some result is definitely possible.

18 tracks at once? Live? What are you recording? Perhaps a few more details of that and we might have some other suggestions.

---

### Post by Autodave on 2017-02-12
I am recording a church service: particularly the music end of it. Keyboard, drums (dual mics), up to 5 guitars, up to 8 singers. I know that fewer mics would be ideal, but this is what comes through the Allen & Heath mixer. I have 2 HDs in the machine: both 7,200 RPM. One runs Audacity and the other records.

This morning, I had installed System Load Monitor and watched it closely. Again, running on a 2.8 dual core, 4 gig RAM, 32 bit system. My CPU usage never exceeded 35%, memory was at 372 meg, swap at 0. So obviously, the PC is not the issue as far as speed or memory. The only other thing it can be is the rate at which the HD writes.  I am still using Audacity 2.0.5 because the newer version will not keep pace at all: I lose a second or 2 at a time, get many strange sounds, etc. Went back to 2.0.5 and life is good. I record at 44.1, 32 bit float, and medium sampling.  What I get is good: good enough for what I need. If I go up in the sampling or the mhz, then I start having problems. I was just wandering if a different file system was quicker than another so that I could go to a faster sampling rate.

---

### Post by TheFu on 2017-02-12
> **Autodave said:**
> I understand that completely, but I am still the one funding this endeavor. Until I can have all SSDs in my own machines, I can't afford one fot that machine. That is why I was wandering what type of formatting would be best for speed.

XFS and ext4 are the fastest file systems, but those improvements are highly dependent on the workload.  XFS has some limitations that might be an issue, so for most people, ext4 is the best answer.  Also, using LVM would help for many reasons, but nothing will help anywhere as much as using SSDs.  We're talking 1% by changing a file system and 99% by switching to FAST SSDs, not the cheap consumer versions.

RAID 0 or 01 should make things faster, but only with a quality RAID card, which I suspect you cannot afford. RAID without a RAID card isn't faster.

My first suggestion is to gather data about the true performance seen and required.  Facts are important.  Without facts, you get opinions and guesses.  

Also, RAM should help with disk buffering, until the RAM is full. This buffering is automatic, but might be tunable somehow. I don't know.

Another option is to use a ramdisk, so more RAM will be needed. If you need to save 5 minutes of 18 tracks then the arithmetic should be easy for the amount of RAM necessary to hold that. NOTHING will be faster than RAM. 

You can use a different program, not audacity. There are multi-track recorders for Linux which are highly recommended by the users.  If you don't write with WAV, rather use something like vorbis, then the amount of data written will be drastically reduced and the CPU will get more work.  Trade-offs.

Lastly, reduce the samples to 22khz. Writing half the data should help with the disk I/O issue, if that truly is the issue.

---

### Post by Autodave on 2017-02-12
[I]You can use a different program, not audacity. There are multi-track recorders for Linux which are highly recommended by the users.  If you don't write with WAV, rather use something like vorbis, then the amount of data written will be drastically reduced and the CPU will get more work.  Trade-offs.
[/I]
There are other ones out there and I have tried a few of them to varying degrees of success. Several problems with all of them: they are all much more complicated than Audacity to use: MUCH more. And, they all have a lot of things included in them that I just don't need or want.

*Lastly, reduce the samples to 22khz. Writing half the data should help with the disk I/O issue, if that truly is the issue.*

I understand that, too. Remember (I said before) that I am currently recording at WAV level and I am recording it w/o a problem. I was just interested in knowing if a particular file system had a large advantage over another one file system as far as writing speed was concerned. What and how I am recording right now is sufficient and I can live with it forever......I was just wandering if I could go better on the cheap. :-)

Thanks all of you who responded!

---

