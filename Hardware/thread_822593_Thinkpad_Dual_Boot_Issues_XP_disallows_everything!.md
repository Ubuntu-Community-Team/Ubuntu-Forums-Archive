---
title: "Thinkpad: Dual Boot Issues: XP disallows everything!"
date: 2008-06-08
forum: Hardware
---

### Post by experttease on 2008-06-08
At least, I think this is a dual boot issue, as it has occurred since installing linux on my Thinkpad R51 with XP Pro.

I'll start by showing you the error messages I get when booting up windows.
[ATTACH]73374[/ATTACH]
[ATTACH]73375[/ATTACH]

Now here is the heart of the issue: when I try to run any program (.exe) I get the message shown in this image: 
[ATTACH]73377[/ATTACH]

Since almost everything you do needs a program, I get this message for anything I do, so I have to give up and shut down, but I can't even do that!:
[ATTACH]73376[/ATTACH]

...so I log out and then am able to shut down (originaly I was not able to shut down even by this method and had to hold down the system off button).


I post this in the  Ubuntu forums because I hope that other linux users have either experienced the same thing or have some experience with XP and also because the problem arose after dual booting. 

I will explain the link between Ubuntu and XP with this problem, which has altered over this past month or so, for example, to start with I only experienced the problem in XP, it was acting a bit funny and whenever it started up it tried to install AVG, which I hadn't tried to install myself. Then a bit later the .exe issue began and I couldn't do anything. Then, I found the problem had found its way to Ubuntu when my shared NTFS partition had disappeared when I started it up one day. The issue was resolved only a few days later by booting the live installation disc (to clear the "I'm using this drive, get your grubby hands off" tag which windows must have applied but failed to un-apply after a hairy, forced shut-down). At this stage I got the message in Ubuntu of something like: "Windows is using this drive, please shutdown Windows before mounting this drive". SLowly this problem ceased to appear in Ubuntu, and now I can see, read and write to both NTFS drives. The problem on XP remains.

In Windows task Manager (which for some reason does load...) I found these two processes which I don't recognise:

isass.exe
smss.exe

Could a virus be stealing my Permissions to the windows drives? I believe it to be a permissions issue at some level or other but have been unable to resolve it.

I would very much like to avoid reinstalling XP, as this would mean I have to reinstall Ubuntu as well and I'm only just getting to grips with Linux and have things working the way I want them! To reinstall XP I would have to use one of the Thinkvantage Rescue and Recovery backups I made and this would wipe the HDD.

Thanks in advance, I would be very grateful for any help.

Ian

p.s. please suggest/move this to a better location if necessary, I was unsure on this count.

---

