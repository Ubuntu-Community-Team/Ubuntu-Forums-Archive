---
title: "Samsung YP-Q1"
date: 2009-09-20
forum: Hardware
---

### Post by racerXazn on 2009-09-20
Hey Guys,

I'm trying to mount my Samsung YP-Q1 Mp3 player to my computer and rip the music off of it, however Linux won't mount my device (I can't see it, but the device says its USB connected)

Any recommended programs for using mp3 players in Linux?

I don't seem to know how/if I can change the format of the player into MTP format btw.

I have the latest install of ubuntu.

Thanks for reading,

~racerXazn

---

### Post by swisskoala on 2009-11-05
same problem here. Ubuntu mounts though, but filesize exeeds limit.....so can't add delete songs

swisskoala

---

### Post by anthony2010 on 2009-11-05
Hi.

I have this player too and Ive made some progress but not much...

First, install rhythmbox. Then go to edit / plugins / then select 'potable players - MTP'

I did this an hour ago and now I can see whats on the player. The Q1 shows up nicely and I can see whats on the device.

Unfortunately, Im yet to get the thing to play whats on the device, so if you guys do this and figure out the next bit, post here! Perhaps we can work as a team on this one.

Fiddly beastie isn't it this Q1 ? :)

ant.

p.s I should probably mention that im running Ubuntu Studio. Not sure if thats relevant but thought I'd say.

---

### Post by anthony2010 on 2009-11-05
Here I am again, I think Ive cracked it.

ok, go into synaptic package manager and in the search bar, type 'mtp'

You will see mtp tools and also mtpfs. Check both of those then apply changes.

You should then be able to see the Q1 in 'Places' on your menu bar. If you right click, you get an error message but if you left click... marvellous thiungs happen :) you get a window open showing all the files on the player, just drag n drop what you want into the floder you like.

Job done!

---

### Post by swisskoala on 2009-11-05
hmm, in the mean time I checked photo's at my SD card.....plugging in my Q1 again and think what happens...he opens the folder with photo's......something very strange about this mounting od cards and devices.... sometimes it mounts, sometimes it doesn't....but still....if it mounts and I want to open the folder music it says: file size limit exeeded. arrrrgggg!!!

---

### Post by swisskoala on 2009-11-06
"the folder contents could not be displayed"

"Sorry, could not display all the contents of "Music": Failed to get file list: -8: Fixed limit exceeded"

This is the error message after I try to open  the music file in Rythmbox

What to do?

---

### Post by anthony2010 on 2009-11-06
ah.

Forget rhythmbox at this stage. Its ok but wont do anything other that 'see' whats on this samsung.

If you do whats suggested above in synaptic, you should find the Q1 appears under 'places' in your main menu.

This way, you can open the files and drop n drag.

It worked for me. Then again, Im using ubuntu studio, not sure if that could be the difference?

I know this next comment goes against the grain but you may want to update the firmware for your Q1 on the samsung website. You will need a windows machine for this. 
(unfortunately)

Good luck!

---

### Post by seppbrandy on 2009-11-22
Hallo
i have ubuntu 9.10 amd64 installed.
I had some problems with my YP-Q1 until the firmware upgrade. 
Now everything is working. Mount, drag and copy, listen to music inside the Q1, etc...
Take care.

---

