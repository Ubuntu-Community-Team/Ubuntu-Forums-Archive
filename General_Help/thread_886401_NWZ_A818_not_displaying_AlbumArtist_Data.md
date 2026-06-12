---
title: "NWZ A818 not displaying Album/Artist Data"
date: 2008-08-11
forum: General Help
---

### Post by bryanp on 2008-08-11
OS = 7.10. 
Sony NWZ-A818 mounts OK.  Ripped CD using Rythmbox to MP3 with VBR set to =4
Album Artist: Robert Miles
Album Title: Dreamland
Navigated to Places > Music > Robert Miles. Dragged and Dropped the folder to the Sony.

The Sony displays track titles correctly, but gives Album and Artist as Unknown. 
Tracks play OK.

As a Newbie to Ubuntu, not sure what I have done wrong. Searched all the various forums and can't se any info, but may have missed it. 
Don't want to go to Hardy until the HAL bug is fixed and released.

Can anyone point me in the right direction?
many thanks

---

### Post by bryanp on 2008-08-15
OK, Either I'm just too impatient, or no one else has come across this issue before, which would also explain the lack of info on various forums. If any one knows anything about this, I would be grateful for a pointer in the right direction
Many thanks in advance

---

### Post by bryanp on 2008-08-15
OK, did some more checking and some more reading. Installed Easytag and reconfigured the ID3v2 tag from 2.4 to 2.3. Apparently the Sony NWZ A818 can't read a 2.4 tag.

Deleted the 'Unknown' album, dragged and dropped the 'new' tagged version and hey presto. All back working.

Hope my experience helps someone!

---

### Post by dthuk on 2009-01-03
Thank you so much for this tip. I have been going around in circles for some time with my daughter's Sony NWZ-E436. It would automount but I lost all album/artist info when I dragged and dropped. 

I tried JSymphonic which after a bit of work did transfer some files but with the same problem. I never could get Rhythmbox or Amarok to see the player at all.

So, once again thanks for this. I just wonder if there is some way to get the older tag version used automatically when ripping CDs.

---

### Post by Skiro'n on 2009-01-04
Just a few words to say that JSymphonic will NOT work with NWZ-A818 or NWZ-E436 models since they are MTP/UMS (expect for Japanese version) and they don't need SonicStage. (JSymphonic is an alternative to SonicStage...)

And, I use K3B to rip CDs, but I really don't know which tag version it is using or if it can be configured...

---

### Post by bryanp on 2009-01-05
Glad to have been of help. I never could get Easytag to auto create the tags in 2.3. Just lived with the problem and updated on every new album created. 
Someone may know differently and if they do, please say so.
 
However from my (limited) experience, there is so much conflicting advice on various forums then when I find something that works for me, I'll just stick with it.

---

