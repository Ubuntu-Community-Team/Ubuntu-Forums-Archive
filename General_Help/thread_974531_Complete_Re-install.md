---
title: "Complete Re-install?"
date: 2008-11-07
forum: General Help
---

### Post by ZootHornRollo on 2008-11-07
Hi,

i have a machine set up as an audio player.  All i use it for is playing music through the m-audio audiophile 2496 into my Yamaha DSP-A5 amp.

Up until this week it was running Ubuntu 7.10 without any issues.  I upgraded to 8.04 just for the sake of keeping it a little more current. 

However, i can no longer use it for the purpose for which it is intended.  I can no longer play audio files.   I have around 250GB of FLAC stored on the HD and so far i have found three tracks that play - admittedly i have not tried them all!.  

I primarily use Exaile as a player but get an error 99% of the time :

```
'NoneType' object has no attribute 'songs'
```

the tracks that do play are noisy and have bursts of white noise throughout which seem to be in time with the music - faster music = more frequent bursts of white noise.

there is nothing in the playlist area, no tabs, no headers...

i tried amorak, which quickly flicks through each track in the playlist without playing them.

i tried banshee but it does nothing when i press play.

I have since tried to play direct from CD, no disc is detected.  DVD's are not detected.  All programs act like no disc inserted.

i have asked for help on the multimedia forum but no reply [http://ubuntuforums.org/showthread.php?t=972783](http://ubuntuforums.org/showthread.php?t=972783).

My last resort is a complete reinstall but this would mean having to get all my CD's back onto the HD again (i have the FLAC files backed up on DVDs).

When i installed Ubuntu i just went with the default disc partitions which has left me with one big main partition - correct me if i'm wrong, i'm not on the machine right now - which contains both the OS install and all my FLAC files.  Can i create another partition and move the FLAC onto it then reinstall the OS on the remaining partition?

or is there a better way to reinstall the OS?

if i have to wipe it all and start again, then fair enough.  Luckily i have almost all my collection backed up on FLAC DVDs so it would not be quite as bad as starting again.

I i do reinstall what is best way for me to partition my 500GB HD?  I am still pretty much a Linux noob so take it easy! :)

any help apprecieted.

I'm at the stage of just wiping all and starting again if no better solution is available to me.

---

### Post by CatKiller on 2008-11-07
I don't have a concrete solution for you, I'm afraid, but I do recall that people were having some problems with the configuration of PulseAudio that came with 8.04. I don't know if that got fixed with later updates to 8.04. You could try using System -> Preferences -> Sound to select ALSA as the output device. Or you could upgrade again to 8.10, which has a more mature PulseAudio setup.

Or it could be something else entirely. Does Amarok give any useful information in the Terminal if you launch it from there?

Failing that, if you've enough hard drive space free then it is possible to create a new partition for your files. You'll need to boot from the Ubuntu cd to do so, since you can't resize the partition that contains the program that you're using to resize the partition.

Boot from the cd and select System -> Administration -> Partition Editor. Resize your existing partition by dragging the right edge of the box that represents it to the left. Create a new partition in the free space you've made. If you're lucky, there was enough space free to contain all the files on this new partition, in which case you can copy them all across. If you're unlucky, the new partition will only contain some of them, in which case you'll need to copy the files across that you can, then boot from the cd again to re-size both partitions, then copy the rest over. If you're **really** unlucky, you'll need to do this multiple times.

There is plenty of information on this forum about the /etc/fstab file that configures which partitions are mounted at bootup, and where they are mounted. You'll probably want to do this so that you don't have to manually mount your new partition every time.

If you get stuck, post about it and someone should be able to talk you through it.

---

### Post by ZootHornRollo on 2008-11-08
Many thanks for taking the time to reply.

I'll try resizing the partitions as you say and hope that works.

Will let you know how i get on.

Cheers.

---

### Post by sirebral on 2008-11-08
A complete re-install?

Not likely the best solution.  As the above poster has stated their have been problems with pulse audio.

You might try resetting, or you might try turning off an audio software and turning it back on.  My guess is the problem is an audio driven problem and you don't need to re install just find out what is conflicting.

---

### Post by SPr on 2008-11-08
How about reinstalling Ubuntu 7.10? At least you knew it worked and it will be supported for a long time yet.

IMO if this computer never does anything except play music - no internet activity etc - then keeping the OS up to date isn't particularly important. I would not bother upgrading the OS but just let it keep on doing what it does until it falls to bits from over work :). If it ain't broke don't mend it.

Did you make a back up of the OS before upgrading?

---

### Post by ZootHornRollo on 2008-11-08
Thanks.

Changing the settings in System/Pref/Sound to ALSA (i changesd them all from auto to alsa) has got all my music players (amarok, rythymbox and banshee) to play fine except exaile is still returning the same 'NoneType' error listed in my first post.

another issue - whilst all other players are inporting what i think is my entire collection, rythymbox has a big list of songs which had errors importing?  it seems to be whole albums that it cannot open.  not a big problem as i have other players working.

at least i have some tunes back again!  Thanks for your help guys.

if all settles down i may try resizing the partitions anyway just in case a big problem comes up in the future and i do have to reinstall.

i'd still like to get exaile working as that is my prefered player but i'll see if they can help on the Exaile forum (have already posted there) now that the issue is isolated to Exaile.

once again, thanks for taking the time to help.

---

### Post by ZootHornRollo on 2008-11-08
> **SPr said:**
> How about reinstalling Ubuntu 7.10? At least you knew it worked and it will be supported for a long time yet.

IMO if this computer never does anything except play music - no internet activity etc - then keeping the OS up to date isn't particularly important. I would not bother upgrading the OS but just let it keep on doing what it does until it falls to bits from over work :). If it ain't broke don't mend it.

Did you make a back up of the OS before upgrading?

no, no back up of OS - unless it does it by default?

i take your point about not keeping up to date but i do use it for internet for downloading music..  but yes, if it ain't broke don't fix it!!!   lesson learned.

---

### Post by SPr on 2008-11-08
> **ZootHornRollo said:**
> i take your point about not keeping up to date but i do use it for internet for downloading music.. 

I understand why it would be best to keep the OS current then :)

> **ZootHornRollo said:**
> but yes, if it ain't broke don't fix it!!!   lesson learned.
LOL Lessons learned the hard way are remembered for a long time.

---

### Post by ZootHornRollo on 2008-11-08
i am still having issues with the CD/DVD drive not detecting any discs.

any ideas what could be wrong there?

if i insert a disc, be it CD or DVD, it is not detected.  If i got to Computer and right click the drive and select open i get 'unable to mount location - no media in the drive'

---

