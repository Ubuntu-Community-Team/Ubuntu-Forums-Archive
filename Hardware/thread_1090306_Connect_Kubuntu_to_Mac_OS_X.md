---
title: "Connect Kubuntu to Mac OS X"
date: 2009-03-08
forum: Hardware
---

### Post by birkopf on 2009-03-08
Dear All,

My girlfriend messed up her Mac (not her fault obviously... ;) )

I am going to erase her Mac and install new system. 
At the moment she has that small 13" Mac Book with Mac OS X (Tiger) and I want to install newer Leopard. I have Kubuntu 8.04 64bit.

1. Does anyone have any tips how to do it safely ?

Before doing it I need to transfer her personal data to my laptop. 

2. Can I connect those two computers via network cable? 

3. Can someone write me step-by-step how to connect them? 
(I don't really know Mac but both are based on Unix so it should be possible)

---

### Post by Tommmyboy on 2009-04-10
Hi, while it's true both Linux and Mac are Unix cousins, that's just it: they are cousins. If they make babies, there could be birth defects. :lolflag: So before we go messin' with the gene pool, let's keep it all in the family because you have all the tools you need it sounds like to do this from her laptop directly. There is a way to involve to a Linux box, but I would use that as my secondary solution; I'll tell you how to do that at the end.

WORD OF WARNING: Do not attempt to back up any thing in the system folder or library folder, the first two sub level folders on the computer, with the intent on manually restoring them; this could cause serious problems later on with permissions and possibly a disk failure. 

You don't describe the problem much - you mention you're not familiar with Macs so I wonder if you've investigated different alternatives over at support.apple.com in the users forums for possible solutions to what ails her machine. It could be as simple as repairing permissions or repairing the disk (you can do both in the Disk Utility program in the Utility folder inside the Applications folder) or clearing the NVRAM (Intel) or PVRAM (PPC) (see instructions on doing this at [http://support.apple.com/kb/HT1379?viewlocale=en_US](http://support.apple.com/kb/HT1379?viewlocale=en_US)  ) so to best help you, I'm going to be pretty detailed - by no means do I intend to insult your intelligence if something seems so basic to you, I just want to make sure I can get you the info you need in one fowl swoop.

First of all gather your back up medium: DVD or CDR or hard disk.

If the machine can at least boot up, go in, gather all of her data files together into one main folder (it doesn't matter if they are in sub folders or not, or the original locations of items - although if your GF wants everything back where it was, she should really use option 2 below.) If the folder size is enough to fit on one of your mediums, then just drag the folder over to a disk if its external or chose select the folder and then go to Applications/Utilities and open disk utility. Drag her file of stuff into the left hand bar window and click on the burn icon at the top of the page. If her folder size is bigger than the media can contain, you can compress it into a disk image, it usually reduces the file size about 20-30%. Scroll down and look and for the three stars *** on how to make a compressed disk image, only you'll be making a compressed image of a folder, rather than a disk, so just swap out the word disk for folder.

And there's solution number 1. 

If her MacBook can still power up - she can't get the apple screen or log  log in or she gets the never ending blue screen - it doesn't need to be able to get to the Apple logo screen or the log in screen, it just needs to turn on - use either her Tiger install CD or the new Leopard DVD to boot from. Again, you'll also need some form of media - CD-ROM if her hard drive space used is relatively small, DVD if she has a DVD burner in her machine, they hold a fair amount of files. If she's got the full I think its 75 gigs in those machines This requires a bit of swiftness here... hold the "C" key down as you power up the machine. As soon as you hear it whirl into motion, continue to hold the "C" key down and immediately slide the CD or DVD into the MacBook, it should readily just suck it up. Once the gray screen appears, you can release the "C" key. I think all the MacBooks are Intel so the CD/DVD shoot boot pretty fast. If it's powerpc you might be waiting 8-10 minutes, staring at a black screen wondering if it's doing anything. It is in fact, you just need to wait.  

So because you've booted off the installation CD/DVD, an installation process is obviously going to start. But you can get yourself out of installation and into the temporary Finder, by just following onscreen instructions. 

Up on the menu bar you'll see a couple different apps - open Disk Utility and have your external drive or blank CD/DVD to go to insert or plug in. This time, you are going to back up the entire disk - yeah this sounds drastic and time consuming and annoying, but trust me your gf will be happy in the end when she realizes she forgot to about a couple docs she really needs; when I do my weekly back ups, I use this method exclusively because not only does it back up the entire contents of my drive, it also gives me a bootable image should my drive crash and I need to repair. In addition to being a bootable disk image, it is also a mountable disk image, meaning I can open it on my desktop just like any other folder. 

***Go ahead and select the Disk in the left column that your GF is having trouble, click the blue unmount button, then go to the File menu, choose New then choose whatever the name of her Disk is. It'll give you a dialog as to where you want to save it, make sure you choose the compressed option at the bottom of the dialog box. let it work... it takes a long time to burn, anywhere from 2 to 3 hours. But in my opinion it is worth the peace of mind, not only for something like your case, where my files are all over the place and I may forget a file or something that's uber important, but also incase my disk crashes - it takes 45 minutes to restore everything back to normal - it sure beats a clean install and having to reinstall apps all over again. 

Lastly there is the Linux solution - the one involving a Linux box - it might perhaps be the easiest one as well. But since I am no expert on file system types (Apple is HFS+, Linux is ext2 or ext 3 I can't give my total thumbs up, maybe you know more than I do and can make the decision easier. What's concerning is that Apple doesn't even seem to acknowledge the existence of Linux file systems at sll, I do recommend it as last resort. That being said, I have had limited success ( meaning limited in time, not degree of success) in dragging native Mac/Windows multimedia files - Quicktime movies, Real Player Movies, MPEG movies - from my Apple formatted. The external Firewire drive shows right up onto the Ubuntu desktop and they play as if I were watching them on a Mac. So perhaps this solution would work for you: using a Firewire cable to connect your Linux box to the Mac. You don't say what sort of machine you have and I know PC's only had firewire very briefly and I think only Vaios had them. To make that set up work though, what you need to do is start the Mac in what's called target mode, simply hold the "T" key down while you power up the machine and keep it depressed until you see an orange graphic start bouncing around the screen. You can then access the mac as you would any other drive. One problem I have had though with hooking Mac drives up to Linux boxes is permissions; I have this one external disk, partioned once, it's never had a permissions problems because it contains just media files on one partition and back up files (disk images .dmg) on the other partition, and for whatever reason, one partition will not open saying I don't have permission and the other will. and the persons when I look at them on the mac are identical. So hopefully if this is the route you go, you won't have that problem. 

So you are well prepared, the MacBook has one single firewire port (that's definitely the fastest sort of storage) and two USB. I would expect something like 75 gigs to transfer over firewire in just about 2-3 hours. If you have a wireless connection at home you can avoid the issue of file systems altogether. Because I have always had firewire, I've never used a USB so I have no idea if they are fast or not. 

Hopefully this helps - it know it sounds awfully tedious ala backing up. but it is a safer way to handle her data. I'm 36 and I have used Macs exclusively at home from the age of 15 and I had never had disk failure or crash, EVER, except of course at work on windows machines, so I just poo-poo'ed all those people who are like "back up back up back up!" I'd install new  systems without backing up, repartition without backing up. I was always thought it would never happen to me. Then one night, it was the day after Christmas last year, statistics finally caught up with me and my laptop crashed. Luckily/unluckily, it was brand new... so it didn't have like a legacy of documents, data, and apps going back like the last 8 or 9 years, even longer, with OS X like my desktop does. In fact, I had just started using Time Machine, the backup feature that comes with OS X - which is good for backing up everything outside of the system files, but only like once a month. So I just lost a months worth data - not too bad - and got the rest back. The killer was reinstalling my apps. Just about all of them are freeware or shareware so that was no big deal but having to go through and find them all again on the web, download, etc. And somehow Time Machine didn't save my library file with all my  preferences for my programs which I could have used once they ewere reinstalled. I lost 5 years worth of bookmarks that started out in Explorer and ended up in Firefox. 

So now I back up once a week - I think that's a fair amount given my needs and how important things are. If I have something I am working on that is uber important or confidential, I usually store it in the cloud for safe keeping - WebDAV has made online storage so easy.  I also make two copies of my back up - I've read sad sad stories about people who's systems have died and they had religiously backed up all the time, one copy each time, and just being devastated when  they go to restore the back up to discover it has been corrupted somehow. 

Ok, that's probably way more than you ever wanted to read, but best of luck and I hope things work out ok.

Oh, lemme leave you with the good word: your idea to do a clean install of leopard is right on the money, that's a great idea because I just did an upgrade on my desktop which is a Power PC,. the last gen G5, and while for the most part it is ok, only now & again things seem a little sluggish and I get what we call the spinning beach ball much more often than I do on my Intel laptop, which iu guess would the Windows equivalent of the spinning hour glass.

-Tom

---

### Post by birkopf on 2009-04-19
> **Tommmyboy said:**
> Hi, while it's true both Linux and Mac are Unix cousins, that's just it: they are cousins. If they make babies, there could be birth defects. :lolflag:

-Tom

Tom that's a hell a lot of a txt ;-)
Thank you very much!

---

