---
title: "[SOLVED] sony walkman"
date: 2008-11-24
forum: Hardware
---

### Post by Bigneil on 2008-11-24
I recently gubIed up my computer. it's all fixed now:), Except for one wee thing. MP3's. I have lost them, i had about half my collection on cd to start with any way. :guitar:

But the ones that i downloaded are lost, except for my sony walkman mp3 player NW-A 808 it's one of the ones that uses Sonicstage software in windows. It still has loads of music on it, but i can not transfer it back to my pc because it thinks that my pc is a different one.

I wondered if there was a simple way to copy them back using ubuntu???

When i plugged the walkman in, it recognised it, and auto mounted. but the files on it were unrecognisable to ubuntu. i am pretty sure that i have all the available codecs and stuff??

---

### Post by mikewhatever on 2008-11-24
Can you post the output of the following command with the device plugged in.
**sudo fdisk -l**

---

### Post by Bigneil on 2008-11-24
[ATTACH]94023[/ATTACH]

Here we go. it is showing up as /dev/sdc


here is what the files onside look like.

[ATTACH]94026[/ATTACH]

---

### Post by mikewhatever on 2008-11-24
There may be two problems. First, although the device seems to be recognized, no file system is specified, could be something Sony specific. You may need additional firmware to be able to manage the device. Second, OMG file extension is definitely Sony specific ([http://filext.com/file-extension/OMA](http://filext.com/file-extension/OMA)) and I couldn't find any mention of it in the repositories. It looks like you do need a special program for that format in Windows.

Hope I am wrong, but your case appears to be a clear example of the vendor lock. With that kind of products, you need to use whatever the vendor had chosen to support.

---

### Post by Bigneil on 2008-11-24
Thank you for taking the time to look at my problem. :)

the files were all converted by sonicstage as it was applying them to the walkman, so they are definately sony specific. 

It is not that much of an issue. i can still listen to them.

I might just go and see if there is any sort of work around in xp, using the sonicstage software. but that is just such a hassle.

Actually i should contact sony ask their advice.

---

### Post by mikewhatever on 2008-11-24
Let me clarify, can you play those files in Ubuntu? Is the only problem just with moving them around?

---

### Post by Bigneil on 2008-11-25
> **mikewhatever said:**
> Let me clarify, can you play those files in Ubuntu? Is the only problem just with moving them around?

No, i can't play them in Ubuntu, i meant that i can still listen to them on the walkman. the trouble is, i can not move them back to the pc using the provided 'Sonicstage' software. But maybe i can move them copy and paste style. they were originally in my music folder in a separate directory.(now lost).  perhaps using my ubuntu i can create a new directory and copy them to it. But perhps the copywriting that sony have put on the tracks will still scupper me.

I will investigate further and try copying them to see what happens. i will also try a couple of different media players to try and play them and make sure i have all the codecs.

The sonicstage software converted them from mp3 to ATRAC as it was applying them to the walkman. i had set it to do this because i found i could get double the quantity of songs on it.
 

Ultimatley i would like to have it running sweetly, transfering tracks back and forth. But for now i would just like to recover the tracks on it back to the computer,  i thought that it might be easier than running photorec on my old hard drive and then trawling through thousands of files to recover them.

(I minced up my daul boot last week, and as i tried to fix it, i got into more and more of a pickle. In the end i just removed the hard drive so that i didn't do any more harm to it. reinstalled my OS's onto a spare drive i had. And i have been Photorecing on it ever since. but there were soooooooooooooo many mp3's.)

---

### Post by Bigneil on 2008-11-25
I have used 'testdisk' to magically fix the wonky hard drive, :guitar:

recovering mp3's is no longer an issue. but it would be nice to get the walkman working in ubuntu. i don't think it will, unless i can find a way to Use sincstage which only runs in windows. i have heard of Wine but it sounds really tricky for a non techie?

---

### Post by mikewhatever on 2008-11-27
Well, hope there is a way.
You know, your experience reminded me of something I considered buying a few years back. It was an iRiver's mp3 player with good reviews and recommendations, but, it needed special software to manage files and, wouldn't allow copying media files from the player back to any computer. In the end, I got a different player without those silly restrictions, but it was really hard to pick the right one. Companies do not advertise their product's restrictions, but only whatever they deem is good.

---

### Post by Bigneil on 2008-11-27
LOL, I really like the mp3 player. but it was a present, and i didn't have a choice. Just like you, i would have chosen one that was more interchangable between computers and OS's.

I'm gonna mark solved for now, and go study, and try to learn more about Ubuntu and build up some experience of dealing with linux before i have another think about mp3 players.

On the up side, i have figured out how to get my wireless working, which puts me (and my Ubuntu} back in good stead with my wife because there is no longer a 20 foot long ethernet cable trailed accross the living room floor. LOL 

Thanks again for your time:)

bigneil

---

### Post by Stosskraft on 2009-10-05
Hey just wanted to bump this, I have the same problem with my Soy Walkman and way to get the files on the walkman converted to a playable format.

---

