---
title: "Lost my hard drive after booting ubuntu"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by CAPTAIN RON FL on 2005-01-22
Well, I thought everything was going pretty good.  I installed Ubuntu on a box with ME.  Dual boots fine. Learned how to add the programs I need. Everything looking good.

So, I decide it is time to put it on a new emachine that has Xp on it. It is a T2893  intel 330 celeron D 2.66 ; 80 gb hdd; 512 ram.

First thing I did was put in Mandrake 10.1 ce and resized the drive. I gave XP 20 gb and the rest free space.

Poped out the Mandrake cd and poped in Ubuntu cd [ the one they sent me.. not an iso burn]. did all the things I did to put Ubuntu on the older box with ME on it.  I took the cd out and let it reboot. That is where it got stucked. It will no longer boot up. I tooked the hard drive out and put it in as a slave on another computer with XP on it and it sees the drive. It sees the XP side and I can open it by explore.  I know that I must have done something wrong with the boot loader. I know that it asked me where to put the boot loader and I probably put it in the wrong place.

Can any one help me get it to work again? Thanks, Ron

---

### Post by CAPTAIN RON FL on 2005-01-23
Does any one know how to get XP to boot again after the mbr gets messed up ....also the computer does not see the drive??

Thanks , Ron

---

### Post by shmonkey on 2005-01-23
fdisk /mbr

---

### Post by CAPTAIN RON FL on 2005-01-24
I wish I could fdisk/mbr .

for some reason It can't see the drive.

Any other help?????

Thanks, Ron

---

### Post by piedamaro on 2005-01-24
I had a similar problem with an old 10GB drive. After installing windows on it, the drive was no more recognized from the bios (the bios hung totally). I had to unplug the disc, deactivate manually the LBA for that disc in yhe bios, the replug it and reboot. (lba IS avilable according to hdparm). Weird!

---

### Post by J. S. Jackson on 2005-01-24
You'll need to use the FIXMBR command in windows XP recovery console.

1. Boot with your Windows XP in the drive.
2. When the main menu appears.  Press R (repair) to enter the recovery console.
3. You'll be asked which install of windows you wish to enter (you'll need your admin password)
4. At prompt you need to type FIXMBR
5. You'll get some dire warnings about the risk of using this command to overwrite the MBR.
6. Hopefully all went as planned, and your windows mbr is restored.

I have used this once before, and it worked, although MS cautions that it can fail.

Do NOT use fdisk, as you already found out, it does not understand linux partitions.

****I suggest you do a google search using words like: fixmbr, linux, xp, grub, etc. to double check my instructions.  It has been some months since I did it, and I'm going from memory.****

---

### Post by Gary Powers on 2005-01-24
Ron, I am watching this thread as I am going through the very same process with the same machine, T2984.  It will not even boot from a recovery disk.  I have called the manufacturer and am about to return the machine.  If you discover a solution, let me know.  At the moment, I have pulled the CMOS battery out and am hoping it will reset.

Gary

---

### Post by CAPTAIN RON FL on 2005-01-25
It is true it will not see the recovery cd and will not see the hard drive. 

I can put in BeatrIX live cd without the hard drive hooked up ... and a couple of others too.... and it works fine. 

I have hooked up a floppy drive ... no problems.  I found at bootdisk.com where I could down load a floppy to fix it??? only problem is that the floppy has to be made on another XP machine which I do not have [ have one but it will not take a floppy drive].  If you can Gary try that.

I have even taken out the battery for the cmos with out any luck.

I hope someone comes up with an answer.

You can also go here to follow the treads on this.


[http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=2005.1;action=display;num=1106067660](http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=2005.1;action=display;num=1106067660)


[http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=2005.1;action=display;num=1102998989](http://www.watsky.net/cgi-bin/yabb/YaBB.cgi?board=2005.1;action=display;num=1102998989)


Thanks, Ron

---

### Post by xalphas on 2005-01-26
hi;

maybe you can use this link [http://www.sysresccd.org/index.en.php](http://www.sysresccd.org/index.en.php)
it helped me many times in these situations.

And also FIXMBR solution i tested it last month. It Works. 

goodluck

---

### Post by CAPTAIN RON FL on 2005-01-27
xalphas,

I have another xp machine that I put the drive in as slave an I can see and open everything on the drive. The problem is I do not know what to change to to fix it. 

Thanks, Ron


WELL, tired of the problems. I have ordered a new motherboard from newegg. Should be here next week. Then we will see who laughs last Mr Bill!!!

---

### Post by machiner on 2005-01-27
start from the top:

boot to your bios. Let your bios auto detect your drives.

Pop in your winxp disk after your bios sees your drive  - boot to rescue and then fixmbr.

Another thing you might have to do is pop in a linux rescue disc..boot it - run qtparted and INITIALIZE your XP drive.  THen reboot into the winxp rescue mode and fixmbr.

let us know.

"First thing I did was put in Mandrake 10.1 ce and resized the drive. I gave XP 20 gb and the rest free space."

you hosed it this way. Ubuntu had nothing to do with your troubles.

A poster suggested booting to winxp and using rescue - try it. Otherwise you're in for a new install of winxp.

What makes you think resizing a drive with a mandrake utility is a good idea?

Look I feel for ya - really. But leave the mandrake stuff to mandrake and the NT stuff to NT.  Get yourself NTFS reaiser, unless your drives are formatted fat32 -- why run NT then?

---

### Post by CAPTAIN RON FL on 2005-01-27
The problem is that my bios won't do that. it refuse to reset. I have even taken out the cmos battery. I have to start the box up first with out the hard drive hooked up. I have power to it. After I get it to turn on I then hook up the drive and no matter what I do it refuses to see it. 

Here are some pics of my bios:

[http://home.adelphia.net/~us22go/P1273766.JPG](http://home.adelphia.net/~us22go/P1273766.JPG)

[http://home.adelphia.net/~us22go/P1273767.JPG](http://home.adelphia.net/~us22go/P1273767.JPG)

[http://home.adelphia.net/~us22go/P1273768.JPG](http://home.adelphia.net/~us22go/P1273768.JPG)

[http://home.adelphia.net/~us22go/P1273769.JPG](http://home.adelphia.net/~us22go/P1273769.JPG)

[http://home.adelphia.net/~us22go/P1273770.JPG](http://home.adelphia.net/~us22go/P1273770.JPG)

[http://home.adelphia.net/~us22go/P1273771.JPG](http://home.adelphia.net/~us22go/P1273771.JPG)

I know there has to be a way to fix this.

I have decided to give up and have ordered a new mother board from newegg.

I am so tired of the problems. I figure this will be an easy out. 
I will wipe the drive then I will put ME or 98 on it.... maybe even 2000pro on the fat side. No more ntfs for me. 

If some one comes up with an answer before than I will be happy to try it. So far nothing works.

Thanks, Ron

---

### Post by Gary Powers on 2005-01-27
Ron, I replaced the hard drive and everything is now fine.  After replacing it, I put the old HD as a slave and I still could not boot the machine with it in there.  Manufacturer sent me a new hard drive which I am installing right now, will then partition and add Ubuntu to the new drive.  So I will have a 60mg drive as master, an 80mg drive as #2 and an external 80 meg SCSI.  God knows what I will do with all that storage, but .......

Gary

---

### Post by Gary Powers on 2005-01-27
Another thought here, Ron:  I think the problem has to do with laying GRUB over LILO.  Exactly how that screws the brains out of the HD I don't know, but can't think of anything else and we both had that in common.

Gary

---

### Post by CAPTAIN RON FL on 2005-01-27
Gary.

That's strange. I tried a new hard drive and it would not see it either. That is why I am getting new motherboard. What did you do to get the new hard drive from emachines? I might try that route.
 Thanks, Ron

---

### Post by Gary Powers on 2005-01-27
Damn!  I just completed the process and it's the same thing.  I did a complete install on WinXP, upgraded through SP2, loaded PartitionMagic and resized the NTFS partition, installed Ubuntu (with GRUB) and my new HD went bye-bye!

I took it out, moved the other "new" HD to primary and am reinstalling WinXP.  I will see if I can save the other HD, then do a fresh install of Ubuntu only and see what happens.  I have Ubuntu running on my other machine (an HP), but it's beginning to scare me!

Gary

---

### Post by CAPTAIN RON FL on 2005-01-27
I think the answer is going to be a new motherboard.
 
I am replacing it with an intel that looks just like the emachine so everything should work?????  I am thinking that it is something in the bios writen there by XP and emachines.

At least I will be rid of the big "E".

I am so tired of yanking hard drives out and putting them in different boxes trying to get this to work.

I am using a PIII to do this on and it dual boots ME and Ubuntu no problem.

---

### Post by Voersek on 2005-01-28
I've had the same thing happen two times on the same PC.I thought I would lose Windows XP.I had problems from changing second hard drive.I didn't know the hard drive CD wasn't compatible with a bootloader other than Windows.After Upates to SP1 or SP2 the "R" recovery console on the original CD won't work.You must first choose "Install",then on the next screen you will get another chance to use "R".At this time it should go into recovery comsole.You can fixmbr and fixboot.Do a repair install.It will save your files but lose your updates.Also a few programs might be broken and require reinstalling.It's not too common and I had good luck with mine.

---

### Post by Voersek on 2005-01-28
Oh yeah FIIXMBR and FIXBOOT won't fix the priblem ,you'll still need a rescue install after changing the XP partition size.But using the "R" on the second screen of rescue console will allow you to save your XP files.

---

### Post by CAPTAIN RON FL on 2005-01-28
It won't go that far. It locks up at the big E. The only way to make the box to work is unplug the hard drive. 

I think that I have found a way around this. 

I am using the box right now. This is what I did. 

I have another XP [amd] box and a new maxtor 120 gb hdd. I put the hdd in and ran maxtor and made it boatable. It copied the hdd over to the new hdd.

I then took it out and put it in the emachine box.  I put the restore dvd in and ran it.

I tried the first restore and it did not work. I then did the hard restore and it worked.

Now if I can find away to copy it over to the hdd that came with the box it will work. The problem is that it is a western digital and not a maxtor so I do not have the same choices.  The maxtor cd will not work with the western digital.

Well I am going to play with it now.

Thanks, Ron

---

### Post by CAPTAIN RON FL on 2005-01-28
**** NEW UPDATE****


GOT IT WORKING :grin:  :-D 

OK this is what I did:


I down loaded the western digital program to my other XP [amd] box.  
 
I then used Ubuntu to delete everything on the drive. 
 
I then used western digital to copy everything from the amd hdd to the emachine hdd. 
 
I put the hdd in the E box along with the recovery dvd. Ran the recovery in the full restore which is the second choice. 
 
Every thing is up and running... in fact I am using it right now.  
 
I found the western digital to be a clone of the maxtor program.  
 
I still would like to put BeatrIX or ubuntu on it.... however there seems to be a problem with this box as others have told me they had the same problem with theirs. 
 
I am thinking that I might try the maxtor hdd to do it and see what happens... now that I know how to get it back up and running. I am even thinking about dual booting with both hdd.  
 
I am first going to try a single boot with the new BeatrIX that I just down loaded. 
 
THANKS EVERY ONE, Ron

---

### Post by Gary Powers on 2005-01-28
I am going to give up and send the box back to the manufacturere.  There is obviously something wrong with the motherboard and I think I will let them sort it out.

I also think that when I get it back, I will install BootMagic and just not mess with GRUB on this machine.  LILO, incidentally, has worked just fine on the eMachine.

Gary

---

### Post by CAPTAIN RON FL on 2005-01-28
Gary,

I think that it won't do any good to send it back. I think what the problem is that Mr Bill has put something in the bios[embeded] or emachine has or both. 

I will find out for sure when the new mother board comes from newegg. It is a direct replacemeant of the emachine board... just not with all their crap in the bios.

Any way I tried to boot ubuntu again by itself.. no dice. 
 Had to go through the whole thing again. 

 I am now running on the maxtor hdd I have with suse live dvd going. I am giving thought to trying to down load it to the hdd. 

So far it won't let me put anything but xp back on. 

Every time I try to boot something different it takes me 1 1/2 hrs to fix it back again. 

If you want to wait, I think the new motherboard should be here by Wed. evening. I will let you know right away by email if you want. PM me with it if you like.

We'll get this figured out one way or another.

Ron

---

### Post by vadude on 2005-01-28
[QUOTE=CAPTAIN RON FL]Does any one know how to get XP to boot again after the mbr gets messed up ....also the computer does not see the drive??

Thanks , Ron[/QUOTE]

YES!!!  Turn your computer off then turn it back on. While it is coming up insert  your original WINXP disk in the CD-ROM drive. It will ask if you want to boot from CD - hit return to select this option (you must watch the screen closely at this point cause it doesn't give  you very long to select booting from CD. A non-graphical Windows will be installed and it will stop and give you three options. Select the second one (Recover Windows ...) by hitting R. It will then go through a few steps and ask you what type of Windows you wish to install. Enter the numeral 1 and hit return. You will get the follwing prompt:

    c:\Windows

Type "fixmbr". 

It will ask you if you really want to do it. Answer yes and hit Enter. It will then reset the master boot record. 

Turn the computer off. Turn it back on and while it is coming up then remove the WinXP disk and let it continue to boot.

---

### Post by CAPTAIN RON FL on 2005-01-28
vadude,

I wish it was that easy. It locks up before you can put the cd in. 
Thanks for trying but that was the first thing tried.... It will not use the restore dvd until the hdd has been wiped clean and cloned on another xp box. This has to do with the emachine motherboard. 

I went in to bios and slowed down the boot time, made it stop to ask how I want to boot. None of these things and a hundred others have failed. I am pretty sure I know what is wrong and how to fix it now. It keeps coming back to the motherboard as I have said in other posts.

Thanks, Ron

---

### Post by Gary Powers on 2005-01-28
I'll be watching for your reply Ron and appreciate your sharing!

I have dual booted on this machine with WinXP and Mandrake/Slackware/SUSE all with no problems.  I think that they all use the LILO boot program, so I am focused on GRUB as the culprit.  I expect to get the machine back with my drives replaced and that will be OK.  I am thinking about trying to use BootMagic in place of GRUB; any thoughts on that?

I wonder whether we are the only two having problems with eMachines?

Where are you getting that new motherboard?

Gary

---

### Post by CAPTAIN RON FL on 2005-01-29
Gary,
 I got the new board from 

Go here:

[http://www.newegg.com/app/ViewProductDesc.asp?description=13-121-225&depa=0](http://www.newegg.com/app/ViewProductDesc.asp?description=13-121-225&depa=0)

They said that it should be here on: 

Feb 2, 2005 by 4:30 pm

I tried to get it to work with Mandrake 10.1 ce both dual booting and and by itself and it won't. 

Which version did you use.? 

I think that I might try the latest suse live dvd. 

Let me know about the different versions you used. I will try and use them and see what happens.

Thanks, Ron

---

### Post by Gary Powers on 2005-01-29
Mandrake 10.1, Slackware 10 and SUSE 9.2 (whatever the most recent).

Gary

---

### Post by CAPTAIN RON FL on 2005-01-29
Gary,

If you can get that up and dual booting, there must be more wrong with mine.

I just finished getting the hdd back to xp and now I am going to play some more with it.

Did you use the live dvd , regular dvd, or the mini install with suse?  I want  to try and do the same thing you did to see if it will work on my end. 

Thanks, Ron

---

### Post by CAPTAIN RON FL on 2005-01-29
Gary;

It worked. I was able to put suse 9.2 on my maxtor hdd.
 I will have to try dual booting and using the hdd that came with it.

Thanks, Ron

---

### Post by Gary Powers on 2005-01-30
Ron:

Both the Maxtor I purchased and the Western Digital that came with the eMachine have behaved the same way when I installed GRUB, so I figure it's not a fluky drive, but something in the BIOS or motherboard.

Gary

---

### Post by CAPTAIN RON FL on 2005-02-01
OK

    It looks like I found a fix for getting ubuntu on my computer. 

I made a "How To"  on how I did it. It seems the kernel and my motherboard do not like the installer in Ubuntu.

 Although it does not show Ubuntu it does show BeatrIX which is a slim down Ubuntu so it should work the same. Try it ... you might like it. I am using both Ubuntu and BeatrIX. Go here to see how I did it. Be sure you use Suse 9.2 dvd. Suse 9.2 Live and Mini Install do not work.

[http://ron33403.tripod.com/](http://ron33403.tripod.com/)

Hope this helps.

Thanks, Ron

---

### Post by Gary Powers on 2005-02-01
Ok, I bookmarked it, Ron and thanks!  My machine is on it's way back to the manufacturer, but as soon as it is back I will try it.

Did you ever get that new motherboard?

Gary

---

### Post by CAPTAIN RON FL on 2005-02-06
Gary,

 Got the new motherboard. But everything has been going so well I have not changed it yet. I will sometime this week just because I do not like the big "E".
 Ron

---

### Post by thestarman on 2005-02-07
[QUOTE=Gary Powers]Damn!  I just completed the process and it's the same thing.  I did a complete install on WinXP, upgraded through SP2, loaded PartitionMagic and resized the NTFS partition, installed Ubuntu (with GRUB) and my new HD went bye-bye!

I took it out, moved the other "new" HD to primary and am reinstalling WinXP.  I will see if I can save the other HD, then do a fresh install of Ubuntu only and see what happens.  I have Ubuntu running on my other machine (an HP), but it's beginning to scare me!    Gary[/QUOTE]

Why are you bothering to RESIZE???  Just install to part of the drive, leaving empty space after it!!!

Dan

---

### Post by Gary Powers on 2005-02-07
I guess that's a fair question Dan and I don't remember exactly what the thought process was at that point, but then again .... why not?  I believe I was trying to keep the NTFS partition as small as possible and leave more room for Linux.

I bought the stuff for a new computer and it should arrive today.  I am going to load Win2K rather than XP and try that.

Seems to be quite a few problems with GRUB.  I'm wondering about substituting LILO!?

Gary

---

### Post by CAPTAIN RON FL on 2005-02-08
Gary

Well here I go I am going to switch every thing tonight.
 I think I will use ME. I might put 2000pro on but I had some problems with drivers with that one.

Ron

---

### Post by Gary Powers on 2005-02-08
Ron:

I "built" my first computer last night.  Sort of got the idea from you and replacing that mother board.  Took about three hours; this evening I put Win2K on it, then used PartitionMagic to reduce the the 120mg partition to 30 and put Ubuntu on the remainder.  Works perfectly!!!!!! I've spent the evening setting Ubuntu up as I want it and am pretty much finished.

I really do prefer this distro to all the others I have tried over the past 10 weeks and will stick with it now.  Hopefully Hoary will work on my notebook and I will be able to get rid of Xandros (which is good, but slow).

Anyway, thanks for the inspirationn and let us know how your work tonight turns out.

Gary

---

### Post by CAPTAIN RON FL on 2005-02-11
Gary

 Got my new board all up and running. The only thing that I could not get right is the fan on the cpu runs wide open.

 My fix was to repace it with a larger ... slower... cooler fan. So far so good. 

Have XP and Ubuntu dual booting.  \\:D/  I am going to start over with a new hdd and build my own case. Probably change over to ME as I can strip IE and Outlook Express out of it.

I like BeatrIX the best as it is a stripped down Ubuntu. The only thing I could not get to work is the usb card reader.  I had the same problem with Ubuntu but I managed to finally get it to work.  
Now I do not remember what I did to get it to work. ](*,) 

You can go here to check out BeatrIX:

[http://www.watsky.net/cgi-bin/yabb/YaBB.cgi](http://www.watsky.net/cgi-bin/yabb/YaBB.cgi)

I plan to switch back to BeatrIX when they do there next release. It's suppose to have usb fixed by then. It is a lot easier to add to an OS rather than subtract the programs you do not want. Any way check it out you might like it.

Ron

---

### Post by Gary Powers on 2005-02-11
Good to hear you're back up and running clean.  I do have Beatrix, but have not had much chance to work with it.

Got my eMachine back this evening and I can't tell exactly what all they replaced, but apparently the memory and something else.  I think that I am going to just let it sit there for awhile and be a Windows box.

I think that since I began to explore this "free" operating system about 10 weeks ago, I've spent about $2000 dollars on computers and hard drives :-) , though I must say it has rekindled by interest in computers again.

Do you have any experience with gdesklets or any of the other eye candy for Gnome?

Gary

---

### Post by Gary Powers on 2005-02-11
Ron:

Good to hear that you are up and running clean!  I do have Beatrix, but have only booted it up once.  I will explore it a bit further.  Also thinking about trying out Gentoo.

I got my eMachine back from the manufacturer this evening and they replaced the memory and something else .... not sure what.  I've got WinXP setup on it, but I am just not ready to go for the dual boot yet.

In the past 10 weeks while exploring this "free" operating system, I've spent nearly $2000 on computers and hard drives.

Hey, do you have any experience with gdesklets and other eye candy for GNOME?

Gary

---

### Post by CAPTAIN RON FL on 2005-02-12
Gee, let me see... I bought two emachines , the one you have and a different one with amd 3000+. I got a Toshiba Laptop. Then a Maxtor 120gb hdd. A couple of wireless pcima cards....still have not gotten them to work with linux. A 17" Xerox lcd monitor. A new dvd cd drive to copy dvd's and cd's. Oh and of course a new motherboard that I really did not need. Not to mention all the dvd's and cd's etc.

Yep , I understand your pain.  :wink: 

I started back in Nov. Can't say I have'nt had fun. I am glad I did. I just wish there was better info. on how to do things. Like for gdesklets. There is no real how to do it thingie. I need to add things to my web page and I can find plenty of how to's for any of the ftp"s for M$. Downloaded gftp and I am still trying to figure how to use it to change pictures and text.

People write all these great programs with no or little explanation on how to use them. Too bad.

Anyway to answer your question ....no I have not played with gdesklets yet.

Cheers, Ron

---

### Post by CAPTAIN RON FL on 2005-02-12
I forgot to add I bought a mp3 player back in Nov. and still do not know how to use it. 
I had planed to down load a bunch of music from that Russian site where it cost about nickel per song.... have'nt learned how to do that either.

I am waiting to learn Ubuntu enough to do it that way instead of lerning how on M$ then turning around and learning how on linux. ](*,) 

Cheers, Ron

---

### Post by Gary Powers on 2005-02-12
Ron:

Yeah, I am working on the gdesklets right now.  Gonna post for some help shortly.  

My eMachine is the same as before it's trip back to the manufacturer, but I am tired of arguing, so I am going to buy a motherboard, install it and get on with life.  Eventually it will go to a son who teaches high school journalism and never has enough computers in the class room.

My wife and I each have Toshiba notebooks and I dual boot mine with Xandrox Linux.  It is a little slow, but recognizes my wireless set up.  Good machines.

Gary

---

### Post by CAPTAIN RON FL on 2005-02-13
Gary,
 That is the only problem I 've had with my notebook... wireless... But I think almost everyone is having the same problems. I am waiting for someone to say I got this card , did this and it works with my toshiba notebook.

Any way I am about finish with this box and ready to turn it over to my sister. I gave her an older box with Me and ubuntu on it to see what would happen. So far she has been able to do most things. I have to get her another printer that will work with linux. After that I have to figure a way for her to fax things.. never done it with linux. In fact I have not seen much info on it.

Cheers, Ron

---

### Post by Kayn on 2005-03-22
Hello every body,first of all, let me say,who said "ubuntu"  :?:  Just one and half week,i received the bundle of 10 CDs of ubuntu from ubuntu,and was happy and just after 10 minutes coz that was for making coffee and to relax and start to install ''lovely'' ubuntu,so did it on the second time,as the first time when i tried,the partition system was too much complicated,so with the second time i allowed it to do each and every thing byitself (automatically).Am i forgetting to say that i installed this on my new computer with windows XP home edition,but as every body is saying here,my this same problem which ''Ron"you are facing,started in the same way with the rebooting,and then there was no windows XP,at all.Sorry to say that i am not that expert as you peoples are,am just a layman in this field,but am tired of this MICRO & SOFT imperialist,so was thinking,if ubuntu is realy that handy,nice and smooth,as,it looks like,so will say bye bye to micro & soft.so then there was,at that time only ubuntu on my machine,,it is ok for me,,,so i went then to make internet connection,which in my case ubuntu was not able to install my software for my adsl internet provider,alcatel speedtouch adsl modem and their driver updating page says,that alcatel support linux.So for trying 4 days,installing and reinstalling ubunto and XP again and again but all is useless,am reading all these posts you peoples are posting here since then,and also consulted different peoples,some body said,to update my BIOS,and after all research,on the "error message'' what i am geting for trying to install my own XP again,all showed that it is the fault of this corrupted/damaged MBR.
Now,the solution for that,as Ron,you described,those 6 floppy disks for for rebooting and then reinstalling XP,is also useless,as i did it just now,and after rebooting am getting the same error message "Error loading operating system".
Now any body from the ubuntu team can tell us,what to do,at least to get our windows xp back on track,or in my case,after installing ubunto what i do to install my internet connection software with ubuntu.
LOL,,,,,till now this ubuntu cost me €800 for a laptop,which i did not need,but ubuntu gave me this headach,and today a usb floppy drive as my this laptop was without station:A.and also bought a Disk editor € 100, =D>  so till now ubuntu cost me € 900.  :cry: 
Lets wait and see,may be some body will come with the solution.
Love this community of ubuntu.

Kayn. :cry:

---

### Post by CAPTAIN RON FL on 2005-03-22
Kayn,

If you already have Xp install fresh... Go down load Mandrake 10.1 ce.  Use this to divide up your hdd. I made Xp 20 gb and 20 gb for linux. Now go down load suse 9.2 cd.  Do a full install with Suse. When done check to see if both will boot.  Now do a full install of ubuntu over the Suse install. That should do it. ;) 

 I am getting ready to do the same thing with a new Toshiba laptop tomorrow. 

cheers, Ron

---

### Post by Kayn on 2005-03-23
Good morning every body from here.

No,Ron,no,my PC is still not working,it is still in the same old position which i got after installing ubuntu and then after rebooting,and when became tired,tried to install again and again XP,but it did not allow me to install XP,but now if i try to install ubuntu,it can by automatic installation option.When i try to install XP,the situation is like this.
1) Configured BIOS to boot from cd rom.
2) Now Windows XP Home cd rom is inserted and restarted computer.
3) Computer rebooted,and asked me to push any key to start,so did it.
4)Got Windows setup screen,and setup started copying files.
5) Next screen,windows XP Home Edition Setup.and again coppying files processed.
6)Now,it said,setup is controlling hard disk.
7) Setup copied files to the windows installation folder.
8) Now setup is initialising windows configuration.
9) Rebooted.
10)And here is the problem,so now installation of XP can not go further,or in the other sense,which i learned here,that it can not see the place or partition or hard disk where to install XP,and i am getting this '' error message '' ..............Fout tijdens laden van besturingssysteem.,,,,,,, this is in dutch, so it means,,Error loading operating system.And studying here and elswhere especially on microsoft site,,that is "error message'' related to corrupted/damaged MBR.
Now did that 6 floppy disks booting way also,but the same problem still exist.

So,looks like ''Ubuntu" hate this micro & soft imerialist.
Now in the second situation on this very same disk,if i want to install ubuntu it goes all well till the end,it install itself,but then the problem is i can not find how to install my ADSL modem to connect to internet,so now here ubuntu is also useless.

Now my question or questions,
1) How i get back my XP.
If that is not possible??????
2) How i install my modem in ubuntu to get internet connection while using ubuntu as my operating system.

Hope ubuntu team will help us or will help ubuntu.........

Love this ubuntu community.

Kayn.

---

