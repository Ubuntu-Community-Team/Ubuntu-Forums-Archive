---
title: "Filesystems Rant"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by Dave_is_sexy on 2005-06-21
I don't get it. 

Of all the filesystems that are condisered popular.. quite a lot are open source. and quite a lot aren't. 

Wouldn't it help linux's cause to have ONE of it's filesystems accessible (ie read / write) from windows? I mean there's no way i'm putting my stuff on fat32.. but it seems to be the only option.

Ex2? no
EX3? no
JFS? no
XFS? no
ReiserFS? no
and of course Reiser4 isn't ready yet (be a good kick start for it though)

And why can't linux write to NTFS? The source is available for that (leaked). I have it if anyone would like to read it.

There's a wrapper in linux for the windows NTFS driver (Captive). Which is the obvious solution.. erm, why isn't there one the other way round? Wrinting something for windows can only help linux's cause.

A way of accessing (fully) a hardrive from either windows or linux. It's not like linux is going to do well from making this hard. 

It could be said that the problem isn't with linux, it's with windows - but it doesn't matter cos windows rules the world. The way to improve linux's compatibility with the world is to take some of that opensource and write a windows driver with it.

---

### Post by silentbob on 2005-06-21
[QUOTE=Dave_is_sexy]Wouldn't it help linux's cause to have ONE of it's filesystems accessible (ie read / write) from windows? I mean there's no way i'm putting my stuff on fat32.. but it seems to be the only option.

Ex2? no
EX3? no
JFS? no
XFS? no
ReiserFS? no
and of course Reiser4 isn't ready yet (be a good kick start for it though)[/quote]
Try [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) for reading ext2fs partitions under Windows.

There is [rfstool](http://p-nand-q.com/download/rfstool.html) for reading ReiserFS files sytems under Windows and also a neat [GUI](http://yareg.akucom.de/) for it.

[QUOTE=Dave_is_sexy]And why can't linux write to NTFS? The source is available for that (leaked). I have it if anyone would like to read it.[/quote]
I think that would be copyright infringement and very much frowned upon by the Open Source community. As for writing to NTFS I believe there is a the ability to do that, albeit it is still experiemental, there is some info [here](http://bisqwit.iki.fi/story/howto/ntfs/) which may help.

HTH :-)

---

### Post by Dave_is_sexy on 2005-06-21
Yeah but we can see how it works with the microsoft code.. and could just write some different code to do the same thing

---

### Post by az on 2005-06-21
"And why can't linux write to NTFS? The source is available for that (leaked). I have it if anyone would like to read it."

I think that what was leaked is seveal years old.  the microsoft company has changde the spcs since then.  They change the specs often excatly because of open source.  You need to complain to them.



"There's a wrapper in linux for the windows NTFS driver (Captive). Which is the obvious solution.. erm, why isn't there one the other way round? Wrinting something for windows can only help linux's cause."

If it was stable and if you could distribute the proprietairy dll, it would be in use.


"A way of accessing (fully) a hardrive from either windows or linux. It's not like linux is going to do well from making this hard. "

I think there is a tool in Breezy which will set up your fstab and get all other partitions on your hd.  Right now, you have to manually add them to fstab, or add them when the installer sets up your partition - you set them up with a label and tell the installer to not touch them.

You would be surprised how well linux has been doing.  Go and install a distribution from just two years ago.  Maybe that will give you some idea of what linux will look like in two years from now...

---

### Post by PhilippWollermann on 2005-06-21
Umm.. there is ext2 IFS for Windows (Freeware), which does EXATCLY what you would like to see.. providing read / write funtionality for Ext2/Ext3 in Windows with Drive Letter Access. And it seems pretty stable too. You can find it here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Philipp

---

### Post by desdinova on 2005-06-21
[QUOTE=Dave_is_sexy]Yeah but we can see how it works with the microsoft code.. and could just write some different code to do the same thing[/QUOTE]

Which is still considered copyright infringement - 


The reason why there are several FS's is diversity - each has different strengths. Besides its hardly Linux's fault if no one has written a MS driver for it. Although there is explorefs as I recall

---

### Post by desdinova on 2005-06-21
[QUOTE=azz]
You would be surprised how well linux has been doing. Go and install a distribution from just two years ago. Maybe that will give you some idea of what linux will look like in two years from now...[/QUOTE]

Anyone like an Original copy of Red Hat 4.2, or 5.0 for x86/Sparc/Alpha ;-) Thene you can see how far we've come... I should still have my original discs somewhere when I bought them new l-)

---

### Post by Dave_is_sexy on 2005-06-21
Yeah I already have Corel linux, I've seen how much it's changed. 

Thing is; everyone's always saying that the best way to use linux today is to dual boot with windows - reasons are obvious.

If that's the goal (which is a good goal, linux has some awesome uses, and so does windows), then where are we expected to keep our data? There is no whre to put it except crappy fat32. 

I wouldn't concentrate on writing an ntfs driver or the like - that'll be too ambitious for me, and from all accounts too ambitious for everyone else too. Instead I'd simply look at how ex2 was turned into ex3 and do the same for fat32. making Jfat32.. a journalised fat system which is the easiest thing in the world to write drivers for for any os. 

..and all the replies will say "why do you want to do that? ntfs is already journalised and so is ex3"

Incidently it's nice to se an ex2 windows driver. of course that's no better than fat, and is actually likely to cause problems since it uses a seperate journalising file to the standard ex3 method. which ought to make both journal files wrong. 

I'm blatently going to have to make a fat32 partition and put shared config files etc on it (eg bookmarks)... but i shouldn't have to. There should be a good way of doing that. (I'm gonna give Captive a try this evening - even if it's just to credit the guy's effort).

Does anyone know why ubuntu wont install to a non-native filesystem? I'm sure i got a distro to last year. Probably Mandrake.

---

### Post by jaykleg on 2005-06-21
Frankly, I think dual (or multiple) booting is for people who REALLY like to suffer.

 ](*,) 

When I want to write on the file system of one operating system from within another operating system I do it over a network, the way the gods of computing intended. Much safer than dinking around with a journaling file system from a place that wasn't intended to support it. File systems live on the hairy edge of disaster anyway. Why ask for trouble?

You can even do the over-the-network thing on a single machine -- by using a virtual machine with shared networking. Install VMWare on a Linux machine and stick Windows on a virtual machine. Or install either VMWare or VPC on a Windows machine and install Linux on a virtual machine. For learning Linux I'm using VPC2004 running under WinXP with Ubuntu installed on a virtual machine. I can crap up the Linux install and replace it immediately by just replacing the container of the Linux OS. (Or by reinstalling Linux on the virtual machine if I figure I want to change something in the way Linux was installed in the virtual machine in the first place.)

I'm lazy, and I don't like dealing with the slings and arrows of jealous boot managers. I think that virtual machines are a lot easier to deal with.

Just thought I'd mention an easier, if somewhat more expensive, way to do the same thing. It has some other advantages over dual booting.

---

### Post by davahmet on 2005-06-21
[QUOTE=Dave_is_sexy]I don't get it. 

Of all the filesystems that are condisered popular.. quite a lot are open source. and quite a lot aren't. 

Wouldn't it help linux's cause to have ONE of it's filesystems accessible (ie read / write) from windows? I mean there's no way i'm putting my stuff on fat32.. but it seems to be the only option.

Ex2? no
EX3? no
JFS? no
XFS? no
ReiserFS? no
and of course Reiser4 isn't ready yet (be a good kick start for it though)[/QUOTE]

The open source community certainly cannot, nor should we force open filesystem standards upon anyone.  Since the filesystems are open, Microsoft is perfectly free to allow Windows to recognize and work with Linux filesystems, but has opted to not do so.  While your frustration is understandable, no one in the F/LOSS community is in a position to make Microsoft work with us.

> And why can't linux write to NTFS? The source is available for that (leaked). I have it if anyone would like to read it.


There are a lot of technical reasons why Linux has difficulty writing to NTFS, and some of which because NTFS is not open, therefore the specifications are not open for general use.  As far as using the leaked source code -- not only is that extraordinarily unethical, but any open source developer who viewed such code would be unable to ever submit open source again -- ever.  Because of the way that Microsoft and simlilar proprietary software vendors use legal systems and IP law as some for of lottery, the open source community has to be very very diligent about source code contamination.

> There's a wrapper in linux for the windows NTFS driver (Captive). Which is the obvious solution.. erm, why isn't there one the other way round? Wrinting something for windows can only help linux's cause. 

I believe you answered your own question.  Since only Microsoft has the authority to include such benefit in Windows, and it would help Linux, it's not very likely to happen anytime soon.

> 
A way of accessing (fully) a hardrive from either windows or linux. It's not like linux is going to do well from making this hard. 


Linux has not made this hard. Microsoft has.

> 
It could be said that the problem isn't with linux, it's with windows - but it doesn't matter cos windows rules the world. The way to improve linux's compatibility with the world is to take some of that opensource and write a windows driver with it.

Yes, it could.  And no, having market dominance is not the same as 'ruling the world'.  If it were, then the internet would work only on netBIOS instead of an open TCP/IP stack, email would work only through Outlook, and interoperability would only mean that your Excel data could be transferred to Word.

---

### Post by Dave_is_sexy on 2005-06-21
OK all good points from everyone. But i still think that it'd be sensible to write a windows driver for like reiserfs or something. That's not against any rules.

Too bad about viewing the source code = no mroe open sorce stuff. That's well harsh.

---

### Post by az on 2005-06-21
[QUOTE=Dave_is_sexy]OK all good points from everyone. But i still think that it'd be sensible to write a windows driver for like reiserfs or something. That's not against any rules.

Too bad about viewing the source code = no mroe open sorce stuff. That's well harsh.[/QUOTE]


So go ahead and write one!  

And, no, I certanly do not recommend dual-booting.  Windows offers me much less than Linux does.  I would not purchase a copy of windows with my next computer nor have I for a very long time.

---

### Post by desdinova on 2005-06-21
[QUOTE=Dave_is_sexy]
Too bad about viewing the source code = no mroe open sorce stuff. That's well harsh.[/QUOTE]

If you're a Linux Kernel Developer (for example) the last thing you want is for your contributions to lay yourself open to a lawsuit that could cripple Linux. Its what SCO is trying to claim wat has happened, or at least I THINK it's what they are claiming - not even they seem to know now.

MS has proved itself quite capable of hitting below the belt, the Kerberos issue with Win2000 springs to mind. Not all of the interoperability issues are the fault of Linux - MS has a vested interest in not allowing Linux into the party.....

---

### Post by davahmet on 2005-06-21
[QUOTE=Dave_is_sexy]OK all good points from everyone. But i still think that it'd be sensible to write a windows driver for like reiserfs or something. That's not against any rules.[/QUOTE]

You are right that it would not be against the rules to independently write a Windows drievr to use Reiser, or ext3. But the question naturally comes to mind of why would anyone?  Honestly I am trying to understand what advantage NTFS has that would make it a benefit for a Linux user/developer, and I'm drawing a blank.  Just being able to read Linux filesystems from Windows is not much of an incentive for someone who doesn't use Windows.  Regardless, anyone is free to create such a driver, but I think there are just very few people that see it as any benefit.

> 
Too bad about viewing the source code = no mroe open sorce stuff. That's well harsh.

Yes, it is.  But in a world where software patents cover not only implementations of code, but abstract ideas behind program development, and you have predatory companies that use the law as a weapon against open source, developers have to be very very diligent when it comes to viewing source code.  Even reading just the comment lines of closed code can have dire consequences.

---

### Post by gil-galad on 2005-06-21
[QUOTE=Dave_is_sexy]OK all good points from everyone. But i still think that it'd be sensible to write a windows driver for like reiserfs or something. That's not against any rules.

Too bad about viewing the source code = no mroe open sorce stuff. That's well harsh.[/QUOTE]
 Someone wrote a windows driver for reading ext3, the standard linux file system.  I don't have a link handy, but one of my friends who dual boots uses it all the time.  

I don't really see the problem here.  ;)

---

### Post by geearf on 2005-06-22
[QUOTE=PhilippWollermann]Umm.. there is ext2 IFS for Windows (Freeware), which does EXATCLY what you would like to see.. providing read / write funtionality for Ext2/Ext3 in Windows with Drive Letter Access. And it seems pretty stable too. You can find it here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

Philipp[/QUOTE]
Thanks a lot for this, no i might transform my fat32 partition in a ext3 tonight (i almost never use windows anymore, but i wanted to keep some room for usual stuff like mails, bookmarks and so for both OS).

---

