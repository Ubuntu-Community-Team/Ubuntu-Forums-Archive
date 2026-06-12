---
title: "Asked By Others: Format NTFS Partition"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-09-05
Why post on a thread already asked by others?  Because nobody has given an answer that really works.  Let's say you either want to format or reformat an NTFS partition while under Ubuntu.  What you get told is use QParted or QTParted with ntfsprogs, use a Windows install disk and its method of formatting before installing, or get an install for Mandrake and use it to the point where you designate a partition to format and what format to use.

Bad news, pretty much.  I had qparted, but somehow it did not let me do a format, and trying to add ntfsprogs, only to lose qparted.  I tried both a Windows 2000 Pro and a Windows XP Pro install disk, and neither worked, because the partition to reformat is on my 2nd drive, and the partitions on my first drive are all Ext3 and swap.  So Windows balks, only letting me delete the partition, and then only sets up a raw partition (no formatting).

Hey, if there is a simple and elegant way to do this, then just spell it out for the benefit of the rest of us.  You know, step by step by step.

The only thing I can think of right now (other than rushing to download Mandrake and try DiskDrake) is to start another Ubuntu install, select the third partitioning option (Manual), pick out the partition in question, designated it for NTFS, and see if that partitioner will do the trick.  Note that I only want to designate and format an NTFS partition, not to actually install another version of Ubuntu on this PC.  I figure three installs already meets all foreseeable needs.

Alright you bright-eyed individuals, show us some of the brilliance kept behind those peepers and let's get this thing resolved.

---

### Post by falconindy on 2009-09-05
No offense, but the first result on Google by searching "linux format NTFS" returned a result **on this forum**.

If you want something technical, run `man mkfs.ntfs` from the command line.

---

### Post by imhotep59 on 2009-09-05
I have found a method on the french ubuntu forum.
Install the package ntfsprogs
```
sudo apt-get install ntfsprogs
```
Then, gparted should make the job.

---

### Post by Bartender on 2009-09-05
I've used a GParted LiveCD to format NTFS several times.  Never had a problem.  

I don't know why you'd even mess with ntfsprogs.

Follow the link below my sig, download the latest stable .iso, burn the image to a CD, boot from the CD.

How hard was that?

---

### Post by oldefoxx on 2009-09-05
In order read:  No offense taken, Your French reads as excellent English, and thanks for the link and information.  By the way, using Ubuntu 9.04, after waiting a lengthly period for the partitioner to start, I was unhappy to find that you can use FAT16 or FAT32 and other
file system types, but ntfs is not an option.  Oh, well.

See, saying something like found first** on this forum** sounds meaningful, but only if that posting had been sufficiently detailed and complete.  And I already had said that the earlier thread did not strike me as adequate.

Please note that to read and write to ntfs partitions while under Linux (and of course this includes Ubuntu), it's best to use the driver set named ntfs-3g as part of the /etc/fstab table entries (this is where the operating system finds out which drives to use, how to access them, and incidently, what file system is in use with that drive).  You search out ntfs-3g, you will find that versions are available for various operating systems, meaning your options to migrate off of Windows has been extended by that much.  Yet it also allows you to retain some aspects of Windows, even Windows itself, when it serves you to do so.

I also looked for partitioning software in one search, and there are some possibilities listed, in case you prefer to go in that direction.
I used to use Partition Magic, which served well for a time, but there are so many pieces of software out there, you have to ask yourself, Do I need to pay for any if so much is now offered for free?  I suspect this is a question that occurs to others as well.

In case we lost you a ways back, any time someone shows you commands to enter, especially those that start with the word "sudo ", these are to either be typed is as shown or copied and pasted into a place where you enter commands, often referred to as a Terminal or Terminal Console, or just Console Window.  People forget to mention this, so how do you find or open a Console Window?  With Ubuntu, it is listed under Applications/Accessories/Terminal.  If you enable a root terminal later on, it will show up under Applications/System/Root Terminal.  You can use either one.  Entering either "sudo su" or "sudo -s" means you stay logged in as superuser, which gives you the same rights as root, what Windows users would consider someone with Administrator powers.  Copying is either done with Ctrl+C or Ctrl+Shirt+C, and in a Terminal Window, the Paste is done with Shift+Insert.  Not quite the same as with Windows, but not too hard to remember and do.

---

### Post by presence1960 on 2009-09-05
> **Bartender said:**
> I've used a GParted LiveCD to format NTFS several times.  Never had a problem.  

I don't know why you'd even mess with ntfsprogs.

Follow the link below my sig, download the latest stable .iso, burn the image to a CD, boot from the CD.

How hard was that?

+1

That's what I do and it works perfectly every time. Gparted Live CD for all your partitioning needs except resizing Vista OS partition- here is a [link]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") to the documented yet unresolved bug when resizing Vista with anything other than Vista's disk management utility. Note - sometimes it works and other times it does not rendering Vista unbootable.

---

### Post by imhotep59 on 2009-09-06
To oldefoxx, 
I have to say that I don't understand why your NTFS option remains unavalaible. I have used this method on my laptop with Ubuntu 8.04 and it works well. My desktop environnement is Gnome but I think it is not important. Was ntfsprogs correctly installed before you launched gparted with no error message ? Did you unmount your partition before trying to format ?

---

### Post by oldefoxx on 2009-09-07
That gparted.iso image turned the trick.  It allowed me to pick any partition and modify it.  You can not only change partition sizes and have them change format, but you can label them as well (the gparted feature that loads under Ubuntu lacks some of these features, reporting that they are not supported by the back end).

But here is a biggie:  It does what neither Ubuntu nor Windows can do on their own.  But before I get into that, let's describe on of the difficulties of access ntfs partitions under any form of Linux, even Ubuntu.  A bit of background first:

Windows has several unique rules concerning folder and file naming, and path usage.  It began with an 8.3 rule under DOS, which is now referred to as the short file name, or SFN rule.  Some characters are allowed, some not, and special use is make of others.  Later, Windows moved on to the long file name set of rules, and imposed two other considerations.  The maximum length of a folder or file name, and the maximum length for a path designation and use (a combination of both folders and and ending file name).  Lengths vary to a degree from one Windows version to another, and we won't deal with that here.  In some cases, you can opt to replace all LFNs with their SFN counterparts, but few like to do this, because you cannot go back the other way.  And the SFN counterparts use a special arrangement of the final part of the 8.3 (or actually 11 character rule), to mark that they are unique and relate to a LFN.  It works, but it is rather weird in some ways.

The Windows did something that was not a good idea at all, which is create a particular folder called Documents and Settings, and each user has a subfolder with that user's Full Given Name, and these host a bunch of subfolders and files for personal settings and data.  So you get some really long path names at times.  The most obvious time is when you add favorites or preferred links under a web browser, because some of these don't offer an actual site name, so the browser just picks up the first sentence to use as the name, and this can result in very long paths, and Windows cannot handle these.

All that makes Windows somewhat odd to anyone following Unix or Linux.  Another thing is that Windows treats uppercase and lowercase letters the same, so a name that looks different to us, say 32bitfax, can also be spelled 32BitFax or 32BITFAX, and to Windows this is the same name.  Bun many other computer dialects treats each one as being different.

Now say you have several sources of folders and file names that appear under NTFS, and Windows shows it can't combine or deal with them properly, and you decide to have a go using Ubuntu and its ntfs-32 support, and it looks much more promising.  So that is a start.  But if Linux treats 32BITFAX, 32BitFax, and 32bitfax differently, each would be copied independently to the new drive or partition.  And if you then tried to mount that drive or partition under Windows, which wants to see each variation as being for the same folder or file, how do you think it can distinguish one from the other?  Fact is, it can't, you can't, and you now no longer have a drive structure with unique designations to any file, but rather unintended duplications.

Seems like there is a tool needed, that works under Linux, but deals with the inconsistencies of Windows naming and forcefully matches one iteration of a folder or file designation to another, so that no matter how your sources for these folders and files had them assembled, you can reconstruct a new drive structure that again assures that each folder and file has a unique designation, even when accessed from Windows.

This might seem simple enough on the face of it, but don't forget that Windows actually has two forms for referencing folders or files, the SFN and the LFN.  Some sources might have SFN references, and others have LFN equivalents.  You may have to track down each SFN on any source, and be prepared to substitute the LFN if also found, even to assigning that LFN to another source with a similar SFN in the same location.  See, locations are important, because a certain SFN may seem identical to another, but the paths to each are then a part of the screening process as to whether they are likely the same file or not.

Painful, isn't it?  And take it a bit further.  Maybe the date and the size of the file should count as to whether they match another, and maybe the person running this program wants some options, like (and these are just some possible choices):

(1) Keep LFN if possible
(2) Keep larger file if different
(3) Keep newest file found
(4) Keep oldest file found
(5) Change name to UPPERCASE
(6) Change name to lowercase
(7) Keep first mixed case variation on name
(8) Don't delete duplicates found, but change name as designated and
    add an extention (such as -a00 to -z99) in the order found and
    checked.

Before I recognized that I was being hammered by these issues, I had spent two days trying to build a single 1 Terabyte target drive.  Somehow in reviewing what I had this morning, my ntfs volume corrupted under Ubuntu (file was missing).  The drive was recognized as a USB-drive, but nothing could be done with it.  Under Windows, the drive mounted, but could not be accessed.  Even Disk Manager was unable to see it.  I turned back to gparted on the iso, and that was able to recognize a mount the drive, reformat it, and give it a new label.  That doesn't say much to Ubuntu's backend or Windows support, does it?  So this is definately a good tool to have on hand.

While the nature of the matter has evolved, I can't really say that it is fully resolved.  Anybody that wants to move away from Windows is not likely to forego all the files and data gathered thus far, but it is not simply a matter of finding equivalent programs and processes, but accomidating what is there to be had from our old systems and setups.  And where Windows has been shown to be weak and lacking, we need something better to not only replace it, but to overcome that weakness or lack.

---

### Post by presence1960 on 2009-09-07
oldefoxx, while i migrated about 36 GB of data from windows to Ubuntu, I still have about 22 Gb in a shared NTFS partition and have never had the problem you are describing. And that includes 3 different versions installed to the windows partition 5 times. I have been through XP, Vista, Windows 7, Vista & now back to XP.

I agree Gparted Live CD is a great tool to have in the arsenal.

---

### Post by oldefoxx on 2009-09-07
I've got data structures, source code, applications, development tools, libraries, and what have you that date back about two decades.  I have code related to every version of DOS since 3.1 and every version of Windows, from 3.1 on up.   I've supported many PCs and made use of others over that time, and it has been my habit to keep backups in depth.  As I said, an initial count of the folders and files in my collection is close to 500,000. I agree this might be the extreme case, but there are likely others faced with the same type of problem, and more so if they, like I, had extensive involvement with an in-house shop or network.  I use enough of these that the smallest hard drive that I currently employ is 320 GB in size, and that only keeps a portion of what I have on hand.  So to mention storage requirements in the mere tens of megs just tells me that you don't quite fathom what I have to cope with.

Over that time, some practices have changed.  I moved from the 8.3 naming format to the long format where needed, and reluctantly adopted the whole LFN concept because others used it, seeing no reason not to.  Now I am faced with trying to bring these disparative practices together at last and still retain the unique distinctions needed to keep unrelated folders and files apart, but let others merge if there is sufficient reason to do so.  And I don't want to have to resort to doing it all manually, meaning I see the need for tools to handle such tasks as instructed.  I could write such a tool in PowerBasic, but that is a Windows Only development tool, and shown inadequate to cope with problems that Windows may be confronted with.
You ever try to copy a group of files under Windows, or delete them from within the GUI?  It may look like it is working until Windows encounters an unexpected condition, such as a shared file, at which point it just fails.  You ever try to run a chkdsk on a Windows drive that is in use by the system?  You are given a choice, to either schedule a chkdsk for the next reboot, or forget the whole thing.

If you have not faced such problems, then count yourself lucky or extremely fortunate.  And don't make light of the fact that others have not only faced such problems, but have struggled to deal with them as best we were allowed.  If such problems can be resolved under Linux, then I would be more inclined to look at Linux as the eventual replacer for Windows, because it would just be better in these areas of concern.

---

### Post by Bartender on 2009-09-08
Jeepers, oldefoxx, maybe we need to work on our manners...

presence1960 took the time to help and you talk down to him.

It certainly sounds like you know what you're talking about with all that SFN and LFN stuff.    

However, if it's something that only comes up with the very few people who are hoarding several decades' worth of work, you have to understand the developers aren't going to drop everything and work on it.  Besides, the devs don't spend time on the forums.  At least write a bug if you feel that strongly about it.  I have a feeling it'll get about as much attention as dial-up does.

---

### Post by ronparent on 2009-09-08
+1 Bartender

Great points.

---

### Post by oldefoxx on 2009-09-08
I did not consider it a question of talking down to someone, but rather showing the likely relationship of our different viewpoints.  I was a career computer support guy, dealing with mainframes, workstations, LANs, WANs, digital telephone switches, into which areas personal computers finally ventured.  I won't say I've done it all, because my first venture into LSI support showed me that the days of knowing every component and every circuit in some piece of equipment was long passed me.  And I've met many far brighter and more knowledgeable than I ever was.  So call me third tier from the top of my profession.  Good enough for technical support, but lacking in real engineering and design skills.

But that type of involvement puts everything in a different framework.  We had shades of Unix and such to contend with, and Linux just looked like a fairly easy and cheep way to teach and practice Unix fundamentals.  You get it on a PC, you could try to play with it a bit, but it was not a GUI language and seemed harder to learn than DOS.  This was back before and during the time when Microsoft and IBM were pursuing the OS/2 dream.  When they split over whether a 286 or 386 was essentially required, and Microsoft started producing the first of its Windows series, that is when the Ziff-Davis Publications took up position behind Windows and began promoting it in every new magazine they produced.  There are still those that claim that in some respects, OS/2 was better.

A GUI-based OS was relatively new in the workplace.  I mean you had SPARC workstations that ran GUI, but controlling screen size, resolution, color, and overwrites made them pale to the fineness of what either OS/2 or Windows could do, which became most apparent with Windows 95 (belatedly showing us the insufficiency of Windows 286, 386, 3.0, and 3.1).  Windows NT was a real push to move the OS ahead, but demanded too much processor and memory.  Then they came out with Windows 98.  This was the crowd pleaser.  Yet this was still just a 16-bit OS, not fully capable of managing multiple tasks well, and the next target was Windows 2000, which was relayering NT 4 with the added features from 95/98.  Still too demanding for many when it came to equipment buy, but with effort they rolled it up into XP, and now the days of 16-bit hardware, OSes, and Applications were clearly numbered.  You probably know most the rest of the history to date.

Now how did this effect those of us in the workplace?  We were put in the position of relearning, keeping up, and finding new ways to use the new tools provided.  So there was a gradual but big impact.  I chose as my thesis for a management program to try and show how PCs were effecting the bottom line, because a bunch of old style CEOs and CFOs were't getting the message.  Whst they were only concerned with was TCO, or total cost of ownership, not how it was changing and reducing the organization,
or that fewer and less well trained staffers were now getting more work done.  I never wrote the thesis because of a dispute with the University over the idea of writing a thesis on a topic that they were not familiar with.

Some of you see the PC as primarily a fun tool, or a basic communications and news-oriented tool.  My viewpoint is shaped to see the PC as a tool of productivity, both to the organization and to the user and developer.  What's the best production OS?  Not Windows, because of its exposed flaws over time, which Microsoft shows no real incentive to return to and fix.  Not Unix, which to most people is too buried in and obscure language to be more than passingly useful.  But Linux is finally showing what it is capable of, and Ubuntu is at the forefront.

And that is a part of my reason for writing posts like this.  To show oversights and points of need, things that actually can hold Linux or Ubuntu back, because of some failure to perceive the need and act accordingly.  I want Ubuntu to succeed, and it may succeed dispite recognition of this lack, but I would rather that it be dealt with, somehow.

There is nothing that says anything in Ubuntu needs to be fixed.  In my time, anyone with the right programming skills was free to look at a problem and attempt to write a utility program to deal with it.  You could even make contests out of the need and effort involved.  But personal interest in programming seems to be on the skids these days, because people perceive no future in it.  Too many programming jobs sent overseas, too many companies hope that they can just find off the shelf software to do what they need, and only the game programmers perceive a ready market out there.  Pushing hard enough at programming, you might learn something of interest about yourself, such as:

(1)  You can succeed if you are persistent enough
(2)  Staying tuned to the subject, you begin to see patterns or
approaches that might just work.
(3)  Your best programs are the ones you worked hardest at, because you begin to see how you extend yourself to meet the need.
(4)  In the hands of the user, your programs now enable others to work as though they were you at your dead level best.

Now having said all that, is there still some perceived need for me to apologize to someone?  If so, then let me add that I am sorry, and let it go at that.  You determined what the insult was, so you now decide what purpose the apology serves.

Yes, I am smiling, but the wryness of the situation has something to do with that.

---

### Post by presence1960 on 2009-09-08
oldefoxx I did not take it as a putdown. I used to keep everything also, although not from as far back as you, but starting with windows 3.1. I just last summer dumped a whole bunch of software (most of which I can't remember the names and could not use anymore). it just made no sense to hold onto them any longer.

But I can understand why you want to hold onto that stuff. No offense taken.

---

### Post by oldefoxx on 2009-09-08
Well Presence1960, it's decent of you to put it that way.  My parents were avid collectors of all manner of outdated stuff, like old TVs and appliances, furniture, magazines, newspapers, articles of clothing and shoes, something that growing up I did not like but had to accept.  Only that wasn't going to happen to me.  But programmable calculators and programmable computers came on the scene when I was approaching my 30s, and that pretty much became the exception.  Now old might seem outdated and obsolete, but this is not always the case.  Some of the most sought after books on computers and computer languages date back to a time when it was all pretty new, and the topics were covered better, both in more depth and in more detail.  Ever heard of a gray scale?  It is a method of coding a rotating disk so that only one bit needs to be changed in each new position, therefore no problem with aligning a photoreader so that all bits trigger at the same precise point.  How about using electromagnetics in place of traqnsistor circuits?  Ever study boolian math or logic?  Why do we need shift registers in computer design?

But to get back on point, if we want to see a Window' Legacy where something better takes its place, we have to contemplate the move of everything old to something newer and better.  If you can't offer that, and what is old is still needed, then you cut deeply into the possibility of simply screening off the old.
For example, aside from legaqcy support for DOS and Windows, why mess with wine at all?  Even VM exists mostly to provide for a protected zone that can include one or more distant OSes and their Applications.

I can't answer for everything, every need or every emergence of an issue, but I can point to the fact that inconsistencies between Linux handling of things and either DOS or Windows handling of things is not good.  But it can be dealt with, if someone really pays attention.  If Windows is unable to do a specific task, and some part of the Linux world is suited to it, then the advantage of having Linux do it over Windows should become more and more apparent.  You wiped out much of your outdated data, which is fine.  But there will be more as time goes on, and a part of what I'm trying to do here is show that this is something many as time progresses.  Do you want to lose your documents, written works, emails, addresses simply because they were or are part of Your World of Windows?  How about being able to move anything new back to your world of old in and effort to keep the two in sync?  Seems like at some point all this should take on some significance.

---

### Post by oldefoxx on 2009-09-09
Hey, I'm not trying to be the last word on all this.  After all, it is just my observations and opinions here.  I can't even swear I got all the facts in the same order that they actually occurred, but they did pretty much happened.

While waiting to hear from others in terms of replies, and possible steerage going forward, I keep reviewing my situation myself.  What might work, at least in part, is to revert to Windows when copying files from one partition to the terabyte drive.  Then repeat for each of the other source partitions.  I would have to use a client Windows install for the machine being targeted, but let Windows do what it can do, then if I need something more, the PowerBasic tools might come into play where then needed.  This could work.  I have to start over again anyway, because the gparted.iso left me with a clean terabyte drive.

But working with a client and using multiple partitions and drives means working out some issues.  By itself, the client version really only sees a few devices, some not quite real.  A local C drive, a CD-ROM D drive, a monitor, a keyboard, a mouse, a network card, and the allocated memory.  With Settings in VirtualBox, you can enable more.  With the VBoxGuestAdditions.iso, you can get better service out of what it already knows about.  But then, what do you do about other drives and partitions?  In general, you enable them as shared folders or possibly as USB-connected external drives.

The problem is, what's shared is not enough sometimes.  The default is Read Only access, and even with Read/Write access, you are not the owner of that device.  This is something that can be dealt with apparently, at least according to some hints involving something called smb.conf, but no clear instructions.  I found eight smb.conf files in a file search, and the instructions are not real clear on a few points.  Adding a USB device might seem easier, but if the VirtualBox does not show you the device you need to reference, you nay have to add a USB filter and put necessary data into the fields offered.  I've run across this before, but you are not now talking about the fact that it might be a Western Digital drive, but the USB interface card itself that attaches to the drive, so how do you find out what that really is?  Looks like I am back to trying to do some more research on answers, tools, and approaches.  Would that I could do everything once and never forget, but there is too much to learn.

---

### Post by drs305 on 2009-09-09
> **Bartender said:**
> I've used a GParted LiveCD to format NTFS several times.  Never had a problem.  

I don't know why you'd even mess with ntfsprogs.

Follow the link below my sig, download the latest stable .iso, burn the image to a CD, boot from the CD.

Just some background for people who may be using an old version of gparted or an older release of Ubuntu. Gparted at one time did not have the capability to format NTFS *until you installed ntfsprogs*. Once that was installed, gparted could use it to format NTFS partitions.

You can check to see if your version supports NTFS partitioning (the verion of gparted on Ubuntu has for about the last year and a half or so I believe; the Gparted CD even longer) from the main menu: View, Filesystem Support.

But +1 on burning a copy of the Gparted or SystemRescue CD, which has up-to-date versions of a lot of useful utilities.

---

### Post by oldefoxx on 2009-09-10
I have yet to attempt a repeat of my consolidation projert on the terabyte drive under a Windows' client.  I have located some articles to research using the search words virtualbox shared folders and virtualbox usb devices OR drives.

What's holding me up is four things:  My concern over the whole health care issue before Congress, and my increasing bitterness towards certain party members and their rash assumptions of their rights and privileges.  I won't turn this into a political spectrum, but I was pleased to hear one person speak up in denial of what a certain lead figure was not only saying, but insisting on.  I find I have not trust in that second person, and so respect the man with the courage and convictions to shout out what he did, when he did.  That he apologized later is not unexpected, but no one else exibited any similar repulsion, though some may have shared it.  That is number one.

Number two is a question I poised to the creator of HotBasic and others who follow his HotBasic and HotBasic_Linux groups on Yahoo!  He affirmed that what I might seek to do with PowerBasic, but only for Windows, was do-able with HotBasic, and thereby for either Windows or Linux.  Though I've little experience with HotBasic, that did please me very much.  You can begin with a Windows version if no complications have yet emerged, but then moving on to Linux means you can also deal with any arrived at complications if you encounter or caused any at an earlier stage.  It's sometimes knowing that something is possible and how to best approach it that can be all important.

Number three is that while I believe the first stage of all this merging of several source ntfs partitions is possible under a Windows client, it foregos the opportunity to get that needed utility developed, and I am asking myself if I really want to do that or not.
Hard call to make, and my physical health is about 20% of what it should be.

Number four is that my email structuring and collection is all askew at the moment, and I have to work through Cox's WebMail for the present, rather than pull the email down to my local PC.  I know how to get around this, but I've fragmented email accounts on several PCs and want to consolidate them together.  That involves some trial and error, as the email client lacks suitable tools for merging and synchronizing multiple accounts together.  So my reading of email and response presently takes a good bit longer than normal.

Oh, I should add that I check for new posts, with a small hope that someone can offer a quick and easy way to get where I am trying to go.  After all, it is a big world out there, and there are lots of players in the game.

---

### Post by presence1960 on 2009-09-10
> **oldefoxx said:**
> 
What's holding me up is four things:  My concern over the whole health care issue before Congress, and my increasing bitterness towards certain party members and their rash assumptions of their rights and privileges.  I won't turn this into a political spectrum, but I was pleased to hear one person speak up in denial of what a certain lead figure was not only saying, but insisting on.  I find I have not trust in that second person, and so respect the man with the courage and convictions to shout out what he did, when he did.  That he apologized later is not unexpected, but no one else exibited any similar repulsion, though some may have shared it.  That is number one.



There really is no room for this in here. It is against forum policy to discuss politics, and for good reason. Our members come from a broad spectrum of countries, nationalities, race, occupations and religions. To speak of such things can & will cause controversy, even among those who really don't care about American politics, like say someone from Indonesia. It will also cause problems for those who do care and feel differently than you do. I have found in life if you want an argument start a discussion about politics or religion with someone who didn't ask about it. It is best if we stick to what we do well and the reason this community exists.

I just thought it necessary to let you know this.

---

### Post by oldefoxx on 2009-09-11
I've had a really bad year of it healthwise, nearly dying on some occasions.  In fact, I'm told that technically I was dead at one point, but have no memory of that period.  I only mentioned it because this has become an important issue in my life, and I feel that politics as such should play no part in what now happens.  But of course they always do, And I don't like that, and resent those that treat it as a ploy.  So yes, I agree in principle with those that would rather not discuss such matters, but it does occupy my time and attention more than it normally would.  I intend to say no more about it, just wanted to give cause for my own lack of real initiative and effort in the matter under discussion.  I'm more accustomed to doing than to explaining what needs to be done and why.  Do no more said on that topic.


Have you noted that if you lose or have a critical boot file corrupted, that Windows won't boot?  Sometimes going to Safe Mode will let you circumvent the problem, but other times it won't.  Trying to figure out which file might be the culprit is a task in itself.  Even trying to repair or restore Windows from an install disk often will just not deal with the problem at hand.  Have you likewise noted that Linux invariably does somehow get started, even when things are not quite right?  That is one of the strongest features I've noted about Linux in general.  You can get to some point, and then struggle on from there, though you may still not be sure of what to do next.  Now we find sites on the internet that specialize in carrying all manner of drivers, DLLs, and other necessary files for Windows recovery, even providing tools to help determine what needs to be done or replaced, but often there is a charge involved.  Other times we phrase queries or searches, hoping that a search will take us to a forum where a similar problem got resolved.  

Some of these approaches work well for Linux as well, and some searches lead to answers, but not where you expect them.  I mean that you search the Ubuntu sites and find no answer, then a broader search that covers Linux in general may get you there.  I would say that about 50 percent of my searches go beyond the Ubuntu forums as I struggle to find answers.  But the Ubuntu forums are a great starting point.

Fact is, since I do return here often, I usually search first for my user name, and this shows me posts or threads that I've participated in previously.  It doesn't really flag if there have been any new responses to that thread, but it's not hard to check them out.

Were I to venture a suggestion for Ubuntu, then I think I would suggest that it depart from the Linux scene slightly and treat all FAT and NTFS file structures as being akin to DOS and Windows.  Now by this, I mean that it would default to treating folder and file names as having case insensitivity, that text files defaultedly are stored with the 0A0D line terminations, and that the use of "\" in place of "/" be accepted in path statements.  I'm not exactly sure of what should be done about the lack of ready recognition of the current drive and directory as the path default, but even that could be considered I suppose.

We've discussed a number of things on the Yahoo groups related to HotBasic over time, and one thing a lot of people seem keenly interested in is the idea that with cross compilers, a single program could be written and compiled to run on any supported OS, like both Windows and Linux. However, there are many differences between these, and this is just one of those areas.  Another is that much of what can be done with Windows involves the well documented API calls provided for many tasks, and there is not what you might call any direct equivalents with Linux.  This appears to be an area where wine and other emulators attempt to reach out and fill.  Do they work?  Depends on what you need done and the nature of the programs involved.

A frequent question is, why Ubuntu when we have Windows?  Or, is there need for both?  Everybody has their own answer.  To me, Windows is the past and Ubuntu the future.  I'm sure others see it the other way around, or some other variation.  Arguments against Vista and Windows 7 have been that the OS already does enough, and that further enhancements are both unnecessary and defeatist in nature, since many of those new features already exist in other forms.  My quarrels with Windows have been that it isn't as good as it should be for what it does.  And with Windows, it is not just a new OS, it is a new everything before it is all over.

I guess I am through talking for now.  I've some other matters to attend to at present, if I am up to them.  Sorry if I offended anyone along the way.  That was not my intent.

---

### Post by presence1960 on 2009-09-11
I was not offended. We have guidelines in here for reasons that are not apparent to all members. But those guidelines keep this community strong despite the vast spectrum of kinds of people that belong to it. if we stick to our purpose in being here we will thrive. if we discuss other matters especially ones controversial in nature we will divide ourselves into many factions. Our strength as a community is our singleness of purpose.

---

### Post by drs305 on 2009-09-11
> **oldefoxx said:**
> 
Fact is, since I do return here often, I usually search first for my user name, and this shows me posts or threads that I've participated in previously.  It doesn't really flag if there have been any new responses to that thread, but it's not hard to check them out.

From the way you describe it, you may not know you can automatically subscribe to your posts/threads. You do it via the User Control Panel, Edit Options, and then find the Default Thread Subscription Mode. You can set it a variety of ways. I chose No Email Subscription and made a FF shortcut that immediately shows any thread with a response. You can also get there via Quick Links > Subscribed Threads.

Once you are logged in your subscription address should be:
[http://ubuntuforums.org/subscription.php]("http://ubuntuforums.org/subscription.php")

Hope you are looking forward to a better year ahead.

---

### Post by oldefoxx on 2009-09-16
Been a bit busy.  For starters, I set my brother-in-law up with Ubuntu 8.04, VirtualBox, and Windows 2000 Pro over a year ago to try and keep his PC from too many attacks.  Of course my health took a dive, and he got into trouble anyway.  After telling him for months to just bring it to the house and I would revive it, he finally did so.  And it was a bit of a mess.  For some reason (and by some method) he had gotten something called Privacy Center running on it, and when you don't have all the necessary resources, that is a real stinker of a program because it would cause Windows to hang without firing up Explorer.exe.  You could use the Task Manager to kill the offending program, then start up Explorer as a new task, but he's not the kind of guy you steer towards workarounds.

So I started trying to clean up his PC, one problem at a time.  The big thing was to try to preserve his email.  But solving each problem just meant finding more, and I was not happy with this.  It was not only taking up time, but many of the problems seemed to be related to the type of sites he made a practice of visiting.  I'm not trying to sit in judgement here, but many of the worse sites for visiting are not just bad for their known content, but for the harmful hidden payloads that they try to get you to accept as well.  It's like you are fair game just because you offend your willingness to seek these sites out.

I finally got upset to the point of deciding to start all over, meaning junking everything and moving him up to the latest versions of Ubuntu and VirtualBox, and doing a complete reinstall of Windows 2000 Pro, but this time making more memory and virtual drive space available.  Yet I had some hardware issue, one being that I am currently out of spare ethernet cables, and had to move a UDB to LAN connector over from one of my other PCs.  Every time I got things really moving on the restructured PC, for some reason, it would quit recognizing that USB to LAN connector properly, and I could find no good way around it.  Plug N' Play could see it, I could get the right driver to reinstall, but then it would not work.  This problem just kept repeating itself.  All I could see is that it worked fine after the installs, but somehow lost footage later on.  Could it possibly be related to the VBoxGuestAdditions?  Didn't seem so, but what was the root cause?  And could I get around it somehow?

First thing was, rule out the USB to LAN connector.  So I borrowed a ethernet patch cable from my nephew, but I still could not make a connection with everything set up.  Looked like no choice but to start all over again.

But then it occurred to me, maybe it was not anything directly related to the ~/.VirtualBox/HardDisks/ VDI file, which is my local drive, maybe it was something gone wrong in the ~/.VirtualBox/Machines configuration file.  How could I check this?  VirtualBox lets you use an existing VDI file and all its content in place of creating a new one, but a change in VirtualBox's design now does not let you use the same VDI image file for two or more instances of a client.  It uses the file's UUID as a means of preventing this.  So now can you create a copy of a VDI image file with a different name and UUID?  Was this possible?  I had to look into it.

Copying the existing VDI file was not hard.  You pick your Home folder under Places, then tag the View Hidden Files checkbox, and scroll down until you find the folder .VirtualBox.  You click on this and should see a couple of folders, HardDisks and Machines.  Due to some naming changes, some older versions of Ubuntu will have the .VirtualBox folder under Desktop instead, and you may see the folders Machines and VDI inside it.  Whichever appears, it is the VDI or HardDisks folder that you click on next.

Now you should see the corresponding .vdi files for any clients you have set up already.  So you do you copy one?  Easy.  Right click on it, choose Copy, pick an open area in the same folder and right click, then pick Paste.  It will create an exact duplicate, but add the word (copy) into the file name.  You don't want to leave spaces or the parentheses in a file name, so what I do then is rename the file and replace the (copy) with -1 or some other identifier.  So if I made a copy of a file called Win2KSP4.vdi, it would automatcially become Win2KSP4 (copy).vdi, and I would rename it then to Win2KSP4-1.vdi.

The next step is to change the file's UUID internally, and there is a surprisingly easy way to do this.  What I did was search using the term change vdi uuid, and this is what I found:

[http://forums.virtualbox.org/viewtopic.php?p=33678](http://forums.virtualbox.org/viewtopic.php?p=33678)
[http://www.schnuckelig.eu/blog/change-uuid-virtualbox-vdi-20090114](http://www.schnuckelig.eu/blog/change-uuid-virtualbox-vdi-20090114)
[http://guozspace.spaces.live.com/blog/cns!3D076D772D2E9CCE!399.entry](http://guozspace.spaces.live.com/blog/cns!3D076D772D2E9CCE!399.entry)
[http://www.giannistsakiris.com/index.php/2009/05/06/virtualbox-how-to-change-the-uuid-of-virtual-disk-vdi/](http://www.giannistsakiris.com/index.php/2009/05/06/virtualbox-how-to-change-the-uuid-of-virtual-disk-vdi/)

Each of the above (and others) tell you the same thing essentially:  Use this command in a console window (stick a sudo in front if need be):

VBoxManage internalcommands setvdiuuid */path/to/virtualdisk.vdi*

Which in my case would look like this: **VBoxManage internalcommands setvdiuuid Win2KSP4-1.vdi**

Then in setting up a new client, you just indicate you want to use an existing hard drive, you will be shown a screen of all the VDIs in the VDI or HardDisks folder, and if what you want isn't there, you can use Add and search your file system for it.  It should be here though, if you copied back into the same folder.

Now I removed the USB to LAN connector, added the ethernet cable to connect to my router, and guess what?  My network came up fine and works, so it must have been something that got screwed up in the Machines settings.  I deleted the original client. and set it up again using the original image, and it cleaned up as well.

Is that the end of the story?  Not quite.  Seems Microsoft's Update process is undergoing change.  XP still works (I guess), but now you are not allowed to update Windows 2000 anymore.  This situation has persisted for more than two days.  I did find that you can ask to be included in any hotfixes for Windows 2000 after SP4, but you have to provide your email address and await approval and notices of when these become available.  Then you manually have to fetch and apply them.  Not sure about Office 2000, as I was still able to fetch and apply those manually after searching for Office 2000 Updates.  I guess the idea is to make updating more painful and thereby force people to consider just paying full price for product replacements.  Heck, we can already see that moving to Ubuntu is way cheaper still.

---

### Post by oldefoxx on 2009-09-18
Good news, for them that want Windows (I guess).  I see claims that Windows 7 is drawing some praise from critics and users.  Me, I am happy enough with Ubuntu and VirtualBox, and where I want it, an earlier version of Windows as client.

Here is the real thing:  Enabling extra drives as Shared Folders is pretty simple under VirtualBox, and then under your client version of Windows, you can check My Network Places, see the Entire Network, and then check out the //VirtualBox/ drives, and easily map them as Network Drives so that they show up under My Computer as well.  Your choice as whether these are to be Read Only or for both Read and Write.

The USB Drives, if you have any, are added under VirtualBox's USB Settings, and reflect the drives found in Ubuntu under Places/Computer or Places/Removable Media.  These show up under Computer if they mount automatically on startup, or Removable Media otherwise (assuming that they show up).  Remember, for VirtualBox to recognize USB devices, you may have to set up filters for each under its USB Settings and give it some basic information about the USB Interface being used.  If you don't have this information, you may have to search for it online.  The best way then of copying the contents of any drive to any other is to search for a folder named System Volume Information and tag it, then under Edit, choose to reverse your selection.  In this way you do not try to copy over the contents of this one folder, as it only pertains to the drive that it is found on, not the one being copied to.

Finding a USB drive under a Windows host, rather than a client, can be a bit more challenging.  If you plug it in and turn it on, it should be added as part of the USB Icon that shows up on the right lower side of the toolbar.  Fine, so that you right click on this icon and verify that it shows up in the list of devices.  But you click on My Computer, and maybe it does not show up there at all.  And you wonder why.  Perhaps it is because the USB drive lacks formatting, or was formatted using with something like gparted.iso, outside of Windows.  The thing then is to get into the Disk Management under Windows (Settings/Control Panel/Administrative Tools/Disk Management) and find the missing drive on the right side.  If it needs to be partitioned and formatted, you will see this there.  If already partitioned and formatted, you have the option to assign a path and drive letter to the drive.  Windows seems unable to deal with a drive otherwise, so best do this.

Working with a client install of Windows and a host version of Windows differs in another respect.  During the copy process, with Ubuntu and VirtualBox in charge, the screen has a tendency to freeze.  You can move the mouse or press a shift key to get it to resume, but the freeze repeats over and over.  I found a simple way to avoid this is to put a bit of weight on a shift key so that it stays depressed, and then the freeze does not occur. 

Using Windows to copy ntfs volumes together tends to rule out some complications that can happen if attemped under Linux.  The differences involved have been spelled out earlier.  Some of those complications could easily mean that future efforts to access those volumes from Windows would be jeapordized  But Windows has some limitations of its own, mainly that some path and file combinations are too long to be subject to a typical copy process.  If true, then how does Windows typically deal with these?

The answer is that when running under Windows, if you managed to get into Command Line mode (perhaps by using Start/Run/cmd), you will see that you are likely positioned at c:\Documents and Settings\Your Account Name\.  What this signifies is that many references made from within Windows has this as the current folder, and if what is involved is based on the current folder, Windows does not require that this portion of the path need be reentered, which saves a fair number of characters.  Some programs also work from the current drive and folder, and as a result, their paths may also be shorter.  But the copy and move processes do not have this benefit, and that is where Windows can error.

Do how would a copy or move process be structured to overcome this limitation?  You can parse a path statement to give you the drive and each folder in turn, and then position to that as the current folder.  You can take the target drive and attempt to position to the same current folder, and create the folder if missing.  In this way you can end up with both drives set so that each has the same current folder, then you just copy all the files found in the source to the target drive.  Among the listed files found there, you may also find a smattering of subfolders, which you verify as not being files, and repeat the parsing and positioning for each in turn.  In this way you should be able to skirt Windows' path and filename size limitations.

Not particularly hard if you understand the basic process.  Of course you have to deal with certain other issues as well, such as files that are flagged as System, Hidden, Read Only, dated, and so on.  You may also want to include some automatic decision points as well, such as whether to recopy two matching files, keep the larger of two files, keep the more recent or dated file, things like that.  You may wonder what might be the best means of creating such a process.  Actually, there are several ways, or computer languages that could be used.  Some form or BASIC might be an example.  This would tend to be a procedure-oriented process, so user interactions could be minimized.  I've mentioned PowerBASIC and HotBasic previously, but there are other choices as well, such as VisualBASIC, QBASIC, PureBasic, even Rapid-Q.  Others might prefer other language options.

---

### Post by 73ckn797 on 2009-09-18
> **bartender said:**
> i've used a gparted livecd to format ntfs several times.  Never had a problem.

+1

---

### Post by oldefoxx on 2009-09-19
Been thinking about writing my own copy folder  and file routine, but not sure it would be postable and shareable on these forums..Then woke this morning with another approach in my thoughts.

The idea is, to just use a flexible backup and restore program to get the job done.  You can backup any drive, but for the restore, you just select to restore by folders and files, and deliver these to a different drive.  You should also have the choice of overwriting existing copies or not.  A good example of a program that can do this is Acronis' True Image.  Later versions of True Image also let's you mount backed up drive images under temporary drive letters.  That might mean you could try copying certain folders and files from that temporary drive to another.  Of course, if Windows has to struggle with path and file names that are too long, this will probably jam up as well.

 Acronis is not free, but not terribly expensive.  Some backup and restore software may be free, but you need the ability to restore by folders and files. because restoring a whole drive image means essentially reformatting the target drive and loosing everything that is already stored there.  This would not work for merging the contents of several drives together on one drive.

---

### Post by oldefoxx on 2009-09-20
Well, the really good news is that using TrueImage works as well as I could expect.  I'm doing one drive backups at a time, then restoring them by folders and files to the Terabyte drive.  I could do them all at once, but this was an exploritory effort.  So far I've done this with five drives on one PC, meaning I am about half way home.

A couple of tricks i worked out with each effort.  I can exclude certain files or folders, both in the backup and in the restore process, and I exclude System Volume Information and TempBack.tib, The first exclusion was explained beforehand.  The second is the temporary backup file I intend to use.  The last would probably be excluded anyway, but why take chances?  Doing the Active partition, I got hits on two log files, and on a later sometimes active partition I got hits on Documents and Settings.  By hits I just mean that TrueImage had a problem with copying them, and wanted to know what I wanted to do about it.  I just told it to Ignore All, and it went on from there.

The other trick is where to put the folders and files.  If you indicate Original Location, that means going back onto the original drive as well.  Not what we want here.  So you indicate New Location instead.  But then you must also check the box saying Restore Absolute Paths, because this means that the exact pack (except for a change in the drive letter) will be employed.  The drive letter will then be determined by which drive you elect to restore to.  If you don't do this, and leave this box unchecked, then pick a different destination drive, the old drive letter will then be added to the start of the path, like a path designated d:\ then becomes d\, and a d folder added to the new drive where everything then goes.

Do it right, and it all works great.  Get it wrong, and you may wish you had made real backups of everything, or at least the destination drive, in case you suddenly find yourself wanting to start over.

---

### Post by oldefoxx on 2009-09-20
Hmmm.  I started with the drives on my second PC, and since Windows is only installed as a client here, I have to work from within Ubuntu for the most part.  The biggest problem to start with is that Networked Drives do not show up as choices for backup or restore under the Home version of Acronis TrueImage.  Yet that is the choice provided by VirtualBox.

So how to deal with that?  The immediate answer is to just boot the PC using a Recovery CD made with TrueImage, and this works, for recognizing all the drives.   But the Recovery version does not include certain choices, such as designating whether to replace existing files or not, to exclude any files, or to do an Ignore All if an error is encountered.  So the trick here is just make a full backup of any one drive or combination of drives, then for the Restore phase, boot back into Ubuntu, start up VirtualBox, start the Windows client, then fire up TrueImage and point it towards the backed up image.  More work, takes longer, but it works.

---

### Post by oldefoxx on 2009-09-22
Hmmm.  I thought it was time to put a wrap on this.  But fate deemed otherwise.  I got to a large hard disk to include on the destination drive, got it set up as described above, but TrueImage keeps failing with some sort of a System Error.  No details on what the error is.  I let the system go ahead and send an error report to Microsoft, not that I expect any sort of a response from them or a fix, but again an indication of the lack of real support for Windows, especially older versions.  Same problem under both Windows 2000 and XP.

Next I decided to search for some way to copy files with really long file names.  It's a known issue, but I then found a couple of articles on ways around it.  One is RoboCopy, and a later version called RichCopy.  They both come from the staff with Microsoft, and are really there for Windows 2003 Server, but I downloaded RichCopy and got it to install.  Let's see what it does when I try using it.

The other thing I decided to do was to use CHKDSK /f w: to make sure nothing bad had affected my Terabyte destination drive.  It did fix a few problems the first time, but everything looks shipshape now.  I used Start/Run/cmd to reach a point where I could enter the CHKDSK command.  I tried ntfsfix after installing ntfsprogs in Ubuntu, but you first have to make sure the drive to be checked is unmounted, and you have to use the device name as it appears under /dev/.  All it does is tell if it had some sort of problem, and suggest you run CHKDSK to find and fix it if one was found.

A recent copy of RichCopy can be found and downloaded from Softpedia:
[http://www.softpedia.com/get/System/File-Management/Microsoft-RichCopy.shtml](http://www.softpedia.com/get/System/File-Management/Microsoft-RichCopy.shtml)

---

### Post by oldefoxx on 2009-09-23
RichCopy lacks some icons when used with Windows 2000 or XP, but the essential ones seem to be there.  It ran for a good while, then died when a supposed file on the souce was not where reported.  I saw no way to continue the program at that point, and that left me with the question of what to do next.

I decided to run chkdsk on all the ntfs drives on that PC, but that is the one that does not have Windows installed on the first drive, so Windows does not install or run there as host.  Puzzlement.  I finally stuck a CD made with BartPE with Windows XP and SP2 in and booted that up, then used Go and entered the command line mode and typed in chkdsk /f and each drive letter with ":" in turn, one by one, but the only drive to show a problem was the next to last, not the drive I was copying from.

So what now?  I'm not sure.  It's a puzzlement for sure.  In a way, TrueImage makes it worse by putting into question whether the OS is adequate for the job at hand.  But it is not like I have a real choice in terms of OSes at this point.  I'm tryng to go with what I have on hand.

---

### Post by oldefoxx on 2009-09-25
Did a bit more online searching, and chanced upon this link:

[http://www.google.com/Top/Computers/Software/File_Management/File_Comparison/Windows/](http://www.google.com/Top/Computers/Software/File_Management/File_Comparison/Windows/)

I've noted other product listings here that might sub for RichCopy and TrueImage in terms of merging the contents of two or more ntfs partitions together following Windows' rules.  These are, as noted, different from those used with Linux distributions.  I guess it will take some experimentaion and evaluation to see if any will suffice for the purpose.

---

