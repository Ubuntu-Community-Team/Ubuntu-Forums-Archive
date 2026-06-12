---
title: "Enquiry on duel booting set up."
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Robotnic on 2009-05-06
Hi

I'm new to ubuntu and have started to duel boot with XP today. Have already installed Hardy Heron as a friend gave it to me on a cd. Want to keep XP alongside firstly because i'm not 100 confident ubuntu will be right for me just yet and secondly because my wife is even less convinced. Firstly I want to enquire if my set up seems ok to someone who knows what they are doing. 

Total HD size 112 gb

58 gb NTFS partition currently allocated to XP (51 gb used) basically I just put that to one side as it has all of our personal files still on there. 

36 gb EXT3 partition put aside for shared files (so far). Also intending to keep my settings for ubuntu stored here for ease of upgrade. 

15 gb EXT3 partition with Ubuntu installed on it (currently taking up 2gb)

750 mb SWAP

This kind of set up was recommend on a website [html]http://www.psychocats.net/ubuntu/partition[/html] in conjunction with a program for reading the EXT3 drives in XP. I downloaded Ext2fsd for this purpose. Once I move personal files across to the shared partition I'm hoping to shrink the XP partition down to a more reasonable size. 

I have got this far and now I read somewhere that this way might be dangerous as there is potential for data loss (which I really don't want!) and I am considering changing my shared partition to FAT32. Do I need a shared partition at all? Further reading suggests that Ubuntu can read and write between EXT3 and NTFS anyway and that the shared partition is just security. Is this true?

I just want to be able to switch between XP and Ubuntu and access my files easily enough from either without hassle or a big risk of data loss. Any advice?

Thanks

Nic

---

### Post by zvacet on 2009-05-06
Yes,Ubunt ucan read and write ext3 (of course) and NTFS.With   Ext2fsd  you should be O.K.

---

### Post by Robotnic on 2009-05-07
Thanks zvacet. I'll investigate working without a shared partition in more depth. 

Nic

---

