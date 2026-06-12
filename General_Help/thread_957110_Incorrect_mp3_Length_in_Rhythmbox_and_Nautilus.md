---
title: "Incorrect mp3 Length in Rhythmbox and Nautilus"
date: 2008-10-23
forum: General Help
---

### Post by Altay_H on 2008-10-23
The title explains my problem rather well. Rythmbox displays the length of some of my mp3s incorrectly. It will play them correctly though. If it's too short, the track bar will simply stop at the end while the song continues to play. If it's too long, the song will end before the track bar does. Based on various posts I've read, I believe the issue lies with the bitrate of the mp3s. However, I can't find a way to change it. Is there an easy way to correct this problem?

I managed to get Rhythmbox to display the correct length by using Audio Tag Tool to edit the Length tags of each file, then removing them from Rhythmbox, then importing them back. I only did this for 3 of my files because it's a bit of a pain. Nautilus still displays the wrong length. Here's one example:

File size: 1.7 MB (1808054 bytes)
Codec: MPEG 2 Audio, Layer 3 (MP3)
Bitrate: 8 kbps
Duration: 30 minutes 6 seconds (according to Nautilus)
Actual Length: 3 minutes 42 seconds

Any ideas on how to actually make this file the correct length? Is the bitrate incorrect, or is the problem elsewhere? Is there an easy solution?

---

### Post by shawnrgr on 2008-10-25
The problem is with VBR mp3's

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/271755](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/271755)

---

### Post by Altay_H on 2008-10-25
So is there an easy way to switch my VBR mp3s to CBR to fix the problem? Is there a better way to resolve the issue? Is Intrepid Ibex likely to fix the problem? Are the next releases of Nautilus and Rythmbox likely to solve the problem?

---

### Post by RhysU on 2009-06-20
vbrfix (available through aptitude) will fix problematic files.  Just round it today.

---

### Post by TheBigBakedBean on 2010-09-28
Incorrect lengths can happen in CBR MP3s as well.  This is due to an incorrect value in the 'length' tag.

Removing this tag should solve the problem. I'm not aware of any GUI mp3 tag-editing software that allows you to edit the 'length' tag, but if you're brave enough, you can write a perl script that uses MP3::Info ([FONT="Courier New"]libmp3-info-perl[/FONT]) to remove it.  If not, there's a Windows program called Mp3Tag (works in wine) that is capable of removing the 'length' tag.

I also mentioned this solution in a thread entitled [MP3 and wrong length]("http://ubuntuforums.org/showthread.php?p=9899788#post9899788").

---

