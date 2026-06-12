---
title: "Correctly burning the Ubuntu ISO"
date: 2005-12-14
forum: Installation &amp; Upgrades
---

### Post by Jennifer_Lyn on 2005-12-14
so sorry to do this if i'm repeating already answered questions, but i can't seem to find the info i need and i've been at this for hours now. 

trying to burn an iso of a download (tried regular download and torrent with the same results). i'm on an xp machine, tried iso recorder and cdburner xp with same results. 

when i run md5sum, i get more errors than you can shake a stick at. 

my intention is to run ubantu on an old g3 clamshell ibook. got as far as the copying process before it stopped and told me i ran out of disk space, not true, of course. read somewhere on the forums that this might be due to a corrupted disc and sure enough, corruption city.

so my question is, is it my xp machine being difficult in trying to burn a powerpc install and corrupting the files or am i doing something wrong here?

any options besides waiting an undetermined number of months for shipit to get me a set of discs? anyone able to help me breath new life into my sturdy, little ibook buddy?

---

### Post by aysiu on 2005-12-14
[QUOTE=Jennifer_Lyn]
when i run md5sum, i get more errors than you can shake a stick at.[/QUOTE] This is your only real problem--your ISO got corrupted during download. Is your connection slow? I'm wondering why it's corrupted.

Is there another computer you can download it from? What area/country do you live in? Ubuntu users are often willing to burn and ship CDs to other users (just as courtesy). I'm sure one could PM you and set that up.

You don't have a friend or acquaintance or anyone else with a broadband internet connection?

---

### Post by codejunkie on 2005-12-14
[QUOTE=Jennifer_Lyn]so sorry to do this if i'm repeating already answered questions, but i can't seem to find the info i need and i've been at this for hours now. 

trying to burn an iso of a download (tried regular download and torrent with the same results). i'm on an xp machine, tried iso recorder and cdburner xp with same results. 

when i run md5sum, i get more errors than you can shake a stick at. 

my intention is to run ubantu on an old g3 clamshell ibook. got as far as the copying process before it stopped and told me i ran out of disk space, not true, of course. read somewhere on the forums that this might be due to a corrupted disc and sure enough, corruption city.

so my question is, is it my xp machine being difficult in trying to burn a powerpc install and corrupting the files or am i doing something wrong here?

any options besides waiting an undetermined number of months for shipit to get me a set of discs? anyone able to help me breath new life into my sturdy, little ibook buddy?[/QUOTE]
when burning the iso, you can't use the built in burner in windows xp, it just burns the image to the disk in one big chunk you need to use something like nero, it will have an option like burn image to disk this will extract the files from the iso image and burn them to the cd. also burning the iso at a slower speed helps 2x-4x seems to be the way to go, and for the md5sums you run the check on the .iso file, not the cd if that helps any. run the md5check on the .iso file and if you are still getting errors it's most likely a bad image if the .iso file is bad you'll have to download another image.

---

### Post by amohanty on 2005-12-14
And in case you dont have access to a cd burning software like Nero or Roxio, you can use the windows port of cdrecord:
[http://demosten.com/cdrfe/](http://demosten.com/cdrfe/)

Just remember to burn at 1x only. Takes a long time but works. For me somehow Ubuntu isos dont quite come out right if burnt at higher speeds in windows.

HTH

---

### Post by aysiu on 2005-12-14
[QUOTE=Jennifer_Lyn]i'm on an xp machine, tried iso recorder and cdburner xp with same results.[/QUOTE] Am I the only one who read that the OP has already tried using CDBurnerXP--software that's perfectly capable of burning ISOs as disk images?

---

### Post by amohanty on 2005-12-14
> Am I the only one who read that the OP has already tried using CDBurnerXP--software that's perfectly capable of burning ISOs as disk images?

whoops! though OP was referring to the builtin explorer based burner plugin.

---

### Post by aysiu on 2005-12-14
[QUOTE=amohanty]whoops! though OP was referring to the builtin explorer based burner plugin.[/QUOTE] Actually, I can see how you might think that. Never mind. [CDBurnerXP](http://www.cdburnerxp.se/help/english/burniso) is a freeware and quite sophisticated.

---

### Post by codejunkie on 2005-12-14
[QUOTE=aysiu]Am I the only one who read that the OP has already tried using CDBurnerXP--software that's perfectly capable of burning ISOs as disk images?[/QUOTE]
that's what happens when you don't use windows, you missunderstand what apps windows users are talking about i guess.

---

### Post by Jennifer_Lyn on 2005-12-14
thanks for the suggestions all!

haven't run md5sum on the iso. the first time i tried it, it seemed to lock the machine up. how do i get to the text file that it needs to read on the iso? when i  try to navigate to the file, it only shows up when i choose 'all files' in the pull down menu. sorry to be such a noob with this. i'll get better, i promise!

also, i do have a cable broadband connection, the download was pretty fast and i tried a regular download and a bitTorrent download. both got the same errors. 

i burned the disk at 8x, then 4x. haven't tried 1x, but i'll give that a shot. 
if anyone lives in/around north nj or nyc and is willing to get me a disc, drop me a pm and i'd be forever grateful!

---

### Post by aysiu on 2005-12-14
Verifying an ISO image:
[http://www.linuxiso.org/viewdoc.php/verifyiso.html](http://www.linuxiso.org/viewdoc.php/verifyiso.html)

The MD5SUMs:
[http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS](http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS)

---

### Post by Nancy on 2005-12-14
Run md5sum on the iso that you download, before burning it.  Takes a while to run, give it a minute or two before deciding it is hung up.  

I don't have any trouble downloading with Internet Explorer, but have been told that it doesn't always play nice with download formats.  If that could be the problem then you might web surf for more info.  

Like other posters said, you have to burn the image not as one big file, but expanded.  In Roxio, I use File/Record CD from CD image..." then select the iso file.

---

### Post by Jennifer_Lyn on 2005-12-15
okay, did the checksum on the iso and it is fine. when i try to run it on the disc, i get this message:

The checksum file you have selected contains one or more ASCII generated sums. 

it then gives me the web address for more information. went to the site and while it explains, briefly what the message means, it doesn't really seem to give me any info on why it's a problem.

i told it to go ahead and run the verification anyway. it finds tons of errors, most of which end with the note that 'file \xyz\etc. does not exist'. most of those missing files have the word 'binary' somewhere in their file name. 

so i guess at this point the question is, am i sunk trying to burn off my windows machine or is there some way to get this disc to burn properly?

i'm just about ready to spend the 8 bucks and buy the discs online.

---

### Post by amohanty on 2005-12-15
Well as aysiu mentioned if you post your location I am sure somebody would be willing to burn you a copy and mail it to you. If you are somewhere in the CA, OR, NV area I would be more than willing to do it for you.

HTH

---

### Post by Jennifer_Lyn on 2005-12-15
thanks so much for the offer. sadly, i'm in nj.

just went ahead and ordered a copy, quite cheaply, too. i think i've already spent more in frisbee discs. i figure it's just gonna be simpler that way.

thanks again for all your suggestions everyone. i'm sure you'll be seeing me pop in with other questions once i get through the actual install!

---

