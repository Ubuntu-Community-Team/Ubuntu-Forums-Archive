---
title: "Moving to Ubuntu, can I retain queues in Azureus, emails etc?"
date: 2008-11-20
forum: General Help
---

### Post by JGB on 2008-11-20
I'd like to move to Ubuntu, and I don't have a problem running my programs within a virtual computer, although I'd much prefer to have them run intergrated(with wine or something similar if possible I suppose)
right now my main drive is partitioned 3 ways, vista on one, ubuntu on another and a storage partition as the third.  
with xp on a separate 500gb drive.
I've just got set up with vista on the insistence of a friend that it is all better and functional now.  After setting it all up I now realize that I still hate it just as much as before the updates.  However after all the work to migrate my stuff over, I'd rather not do it all over again if I can just run applications from their current locations for now, at least for ones like Vuze, thunderbird, itunes etc.  or if I could move them over without losing all the queue in Vuze, emails from thunderbird(again, thanks to vista) or library from itunes.
I've read about making the desktop seamless with XP, but I didn't find information anywhere on whether or not it would allow me to keep the settings etc that I want.


Thanks




my computer is using:
 amd 4400 processor, asus m2n-e Sli motherboard, asus 8800 GTS video card and a Geforce FX5500 to run my third monitor. 4gb of ram, 3x1tb wd green drives 1x500gb seagate baracuda drive.

---

### Post by gnivler on 2008-12-03
Hey there.  It sounds like you should be able to migrate all the data you mentioned from your vista partition without too much effort.  Check your \Users\YourAccountName\AppData, there are Local, LocalLow and Roaming subfolders contained there.  Different applications will store their own directories in either Local or Roaming, in my experience.  If you copy the relevant data to the proper target location on your ubuntu filesystem and possibly massage it a little bit, it should be "cross platform".  Vuze stores your config in ~/.azureus (.azureus in home directory).  Some plugins for the actual program exist inside the program folder, and some in the profile directory.  Probably best to copy that configuration in the target layout.  You will probably need to adjust the file paths also, since the configuration will actually show C:\Whatever.  Important tip when messing with torrents and save locations etc, is just to make sure you Stop the torrent before doing it.  Check data files exist and force-recheck functions may come in handy also.

Thunderbird should be quite a bit simpler, just copy the profile data in the proper subdirectory in your home folder in ubuntu.. maybe something like ~/.mozilla or ~/.thunderbird I'm not sure.  As for your tunes, you should be able to find the music path inside the program settings itself, then just do whatever you want with the data store.  Sorry but I have no clue how well itunes as an application will work with ubuntu, with wine or otherwise.  The VM might do the trick though.  Keep in mind with a VM you will have to actually copy the data to the VM somehow since the hard drive file will start blank.

---

