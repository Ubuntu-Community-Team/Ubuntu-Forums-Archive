---
title: "Sansa Clip with Linux and Windows"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by melto on 2007-12-28
Hi!
I bought me a Sansa Clip a few days ago.
My problem is, that I cannot see the files I put onto the player with Linux on Windows and on Linux I cannot see the files I put onto the player with Windows.
The funniest thing about it is, that I can see all files on the player.
Thats quite weird. Can anyone tell me why I cannot see all files with my Linux box?
Thanks a lot!
Melto

---

### Post by snickers295 on 2008-01-02
I'm not sure but i think windows writes a map file on stuff like that and every time it writes a file, it adds to that map but linux does not add to that map.
this is just a theory

---

### Post by hwttdz on 2008-02-27
Out of curiosity where did you put the files in linux, I can't seem to see any of the files I put on using linux though the player.

Edit: Create a file in the root of the player named .is_audio_player
Open the file and insert the line
audio_folders=MUSIC/,RECORD/

From: [http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803](http://forums.sandisk.com/sansa/board/message?board.id=clip&message.id=2803)

---

### Post by mikecomua on 2008-05-15
Guys, I have FORMATTED my Sansa Clip and know Ubuntu only sees it in /media/SANSA CLIP. It works with Windows. Any help please?

---

### Post by yetiARC on 2008-05-21
Out of the box, my Clip was recognized by Ubunty (Gutsy) as a USB device; I could copy files into the MUSIC directory, but the player didn't show or play these files when disconnected from the computer

here's what worked for me:
- in the settings, I found that my Clip came with old firmware (01.01.18)
- unfortunately, San Disk only offers a Windows program to update the firmware
- plugged the player into a WinXP PC and installed it (IMPORTANT: USB mode has to be set to MSC in the player settings to make it work !!!) 
- installed the San Disk update program on the Windows machine and followed instructions to update the player firmware
- firmware got updated to 01.01.29
- in Ubuntu, I can now drag and drop files into the player directories without a problem

---

### Post by sliderule on 2008-05-24
Excellent, now I can finally use my sansa clip.

Mine had firmware version 1.01.20, which didn't work at all with ubuntu.

1.01.29 did the trick! :guitar:

---

### Post by Versusnja on 2008-06-07
> **yetiARC said:**
> 
- unfortunately, San Disk only offers a Windows program to update the firmware

You do not need a Win PC to upgrade.
What you should do in Linux:
1. Put the player on hold
2. press and hold for 4-5 sec. the central button
3. connect the player to the linux box
4. copy the firmware into the root folder
5. disconnect.

voila. the player will restart and refresh your audio library.
hope this helps.

---

### Post by sorba on 2008-06-22
4. copy the firmware into the root folder


I found my latest firmware at : 
[http://www.anythingbutipod.com/forum/showthread.php?t=22669]("http://www.anythingbutipod.com/forum/showthread.php?t=22669")

Worked like a charm. 
I think there is a difference between the  ..a  and  ..e  versions. I used the 1.01.29a and it worked for me, the radio part still worked too.

---

### Post by hank freid news on 2008-07-02
I also Formatted Sansa Clip and know Ubuntu only sees it in /media/SANSA CLIP. It works with Windows.

---

### Post by ariel on 2008-07-06
> **sorba said:**
> 4. copy the firmware into the root folder


I found my latest firmware at : 
[http://www.anythingbutipod.com/forum/showthread.php?t=22669](http://www.anythingbutipod.com/forum/showthread.php?t=22669)

Worked like a charm. 
I think there is a difference between the  ..a  and  ..e  versions. I used the 1.01.29a and it worked for me, the radio part still worked too.


SanDisk has a forum thread where they post their latest firmware, and instructions on how to load it in linux, it is here:

[http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720&view=by_date_ascending&page=1](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=6720&view=by_date_ascending&page=1)

Also it appears that MTP mode is not supported at all for linux. This was a bit surprising for me since I've seen "MTP" plugins for both rythmbox and banshee for a while now. Somehow those plugins don't seem to be compatible with this little player.

This is the thread where they say Linux is MSC-only: [http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=7582](http://forums.sandisk.com/sansa/board/message?board.id=clip&thread.id=7582)

If there is a trick to get MTP to work I'd like to know! ... in rythmbox and banshee, draggin' and droppin' a .flac file into the MTP or iPOD Player causes the file to be converted on the fly which is nice for lossless audio users.

---

