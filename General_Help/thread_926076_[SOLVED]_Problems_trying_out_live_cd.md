---
title: "[SOLVED] Problems trying out live cd"
date: 2008-09-21
forum: General Help
---

### Post by Snowybob on 2008-09-21
Forgive my total ignorance, I am totally new to linux and have heard so many times that it work looking at these days as you no longer have to worry so much about learning the command line stuff as with distributions like Ubuntu you can load straight to the desktop.

I downloaded the ubuntu-8.04.1-desktop-i386.iso file and carried out the hash check and all was OK. I tried to boot from the live cd and got the error suggesting to boot with the noapic option, which meat nothing to me but searched around and found how to do that. I can now boot to a command prompt.. I think! it reads;
Busybox v1.13 (Debian 1:1.1.3-5 ubuntu12) Built in shell (ash)
Enter help for a list of commands

I did type help and return but don't see anything there which helps me. Where oh where is the desktop. I did not think it would be this difficult after what I have read. 

Can anyone tell me if I should be doing something else or what I need to rype next to load the desktop? Thanks in anticipation.

---

### Post by kokkus on 2008-09-21
Did you burn the CD on the lowest rite (1x I suppose) ?
If you do a search on this forum that seams to always be the problem if a live CD doesn't boot right.
So burn it on lowest speed.
And, are your system i386 or x86?
i386 is intel 386 processor.

---

### Post by Crafty Kisses on 2008-09-21
You may have to use the alternate CD.

---

### Post by Snowybob on 2008-09-21
Hi Kokkus, thanks for such a fast response.

No I did not burnat 1x speed as I did not think this was the problem. I have read that it is quite uasual to have to use 'noapic' but when it loads to a prompt I thought I might need to then type something else rather than there being a cd problem, I will try to re burn the cd at the lowest speed possible.

I have an Intel processor by the way, so i386 is the correct .iso.

---

### Post by Snowybob on 2008-09-21
Codename, can you tell me what the difference is with the alternate cd. Thanks.

---

### Post by MetalFanLiam on 2008-09-21
The alternative CD doesn't use the LiveCD option, instead using a text-based install, hence allowing older and/or less powerful computers to install.

This may solve your problem, it may not. Maybe when the terminal appears (after you've added the 'noapic' option) you could enter "startx" (without the ") to start your X server. Then install normally.

---

### Post by kokkus on 2008-09-21
Do you use a laptop? If so I suggest an alternative CD.
The desktop version is avalable for normal 700mb CD and therefor useful for people without a dvd-rom.
Burn the DVD release of the alternative CD.
It autodetects your system, plus it has more program then the 700mb release.

---

### Post by kokkus on 2008-09-21
But with no live CD.

---

### Post by Snowybob on 2008-09-21
Thanks all of you so far for your help.

I particularly wanted to run from live cd at the moment, 'cos I want to see what it looks/feels like before I make any descisions about partitioning my drive and installing. I am using a HP box with a 2.8ghz processor and 1g ram, so I don't think there is a problem with the machine not being powerful.

Am I using 'noapic' correctly at boot from cd??
when I get the initial screen I select English then type f6, at the prompt I type noapic then return. Is this correct?

---

### Post by kokkus on 2008-09-21
OK please give me your PC details.
Then we can tell you which CD that works best for your system.
Forexample, if you have less then 152mb ram I wouldn't even try to use a live CD, /home/remastersys/remastersys/custom.isoess its xubuntu.

---

### Post by Snowybob on 2008-09-21
I burned a new cd at the lowest burn speed available 16x. I tried everything again - ended up having to use noapic again.
When I got to the command prompt I typed 'startx' but the command is not recognised.

Any more ideas? 'cos i'm totally stuck with this.

---

### Post by kokkus on 2008-09-21
As I told you, give us your computer details like how much RAM and which processor etc.
This can help us find the right live cd solution for your PC.
It seams too be a problem with RAM on your PC.
THis shouldn't be a problem if you have more then 512mb.
I386 should also work fine if you run intel processor.

---

### Post by Snowybob on 2008-09-21
Thanks,

I have previously mentioned my PC details. It is a HP machine with 2.8 Ghz processor and 1Gb of ram

---

### Post by Snowybob on 2008-09-21
I forgot to mention the processor is an Intel

---

### Post by kokkus on 2008-09-21
Sounds like a very great PC. 
Did you download the iso file from ubuntu's site or some private homemade livecd from a website or friend? 
Maybe the problem is the booting system that comes with the iso file.
That shouldnt be a problem if you downloaded it from ubuntu's websites.

---

### Post by Snowybob on 2008-09-21
Yes it's a reasonably new PC. I did download from Ubuntu. 

Am I doing the right thing just by typing noapic after going to the prompt at f6??

---

### Post by kokkus on 2008-09-21
You shouldn't type anything when booting ubuntu from a live CD.
Take a look at this video clip on youtube to see how it should be done.
[http://www.youtube.com/watch?v=ZOMwcEDqig8](http://www.youtube.com/watch?v=ZOMwcEDqig8)

---

### Post by Snowybob on 2008-09-21
If I just put the cd in and restart to boot from the cd I get the message:
kernel panic - not syncing IO-apic + timer does not work boot with apic=debug and send report then try booting with the noapic option.

I don't know how to do the report as it is the middle of the boot from the cd, so I just tried to noapic option.

Does any of this make sense.. it doesn't to me.

---

### Post by kokkus on 2008-09-21
Hmm. And you are sure you burned the cd with 1x?
THis error has nothing to do with your PC.
It's a problem with the iso file you burned it from or the way the cd was burned.
OK. If you can give me 12 hours I can upload an iso file I know works. (tried it on 2 PCs).
The file is a dvd iso on 2 GB so it will take me some time to upload the file.

---

### Post by lian1238 on 2008-09-22
You might want to try out [_Feisty Fawn_]("http://releases.ubuntu.com/7.04/") or [_Gutsy Gibbon_]("http://releases.ubuntu.com/7.10/").

---

### Post by Snowybob on 2008-09-22
Lian 1238,

Thanks for that. I may be on the wrong lines, but I thought that the later version might be the best for a newer PC. I have read somewhere that some of the newer machines do have problems - that's why I tried 'noapic' but either I am doing something wrong or you can't use it for booting from and running from the CD. 

I will download Gutsy Gibbon and give that a go

---

### Post by Snowybob on 2008-09-22
I have now burned 3 copies of the CD none of which will load live CD on my PC. I have managed to try the CDs on another PC and it loads live PC fine. Something about my PC will not allow live CD to work.

---

### Post by kokkus on 2008-09-22
And you are sure CD rom stands before Hard Driver ?
Check with another bootable cd (like windows) if it allows you to boot the CD.

---

### Post by Snowybob on 2008-09-22
The machine does actually boot and loads the initial screen, I select English then I have the screen with the various options on the 'F' keys at the bottom of the screen and the options in the middle of the screen, the first option being load live CD. I select that option and I then get a message which says bios bug load using noapic, which is where I started this thread. 

There seems to be something about my PC which is stopping the live CD from loading presumably the bios and am trying to find if anyone knows what or why.

---

### Post by kokkus on 2008-09-22
Sounds superwaired. But what if you just download and burn the alternative version and install it?
If you want to test it before actually use it you can install your new ubuntu and set the partition to let's sey 20GB. Then you can just delete the partition with the installation cd when you're finish with the testing, and then install it on the whole disk or as a dual boot if you still want to use windows next to ubuntu.

---

### Post by ju2wheels on 2008-09-22
Sometimes you need to update the bios on your machine as well before it will boot with Hardy, but this doesnt need to be done on many machines as they typically work fine. The fact that its complaining about the timer and noapic means its either your BIOS or your hardware isnt supported (unless you try the alternate cd and then customize the settings).

Is your Intel processor 64bit or 32bit? I know you stated the speed before but its important to distinguish because your pc may not behave properly with a 32bit Ubuntu sometimes if it is a 64bit processor.

Can you tell us the model of your HP, for example is it an HP Pavilion and what number is it?

---

### Post by Snowybob on 2008-09-23
My machine is an HP Pavillion t3320uk and as far as I am aware it is a 32bit processor. At least it came pre-loaded with windows 32bit. If I need to update my bios how difficult is that and what is the procedure?

---

### Post by lian1238 on 2008-09-23
> **ju2wheels said:**
> Sometimes you need to update the bios on your machine as well before it will boot with Hardy, ...
Snowybob said he tried older versions which yield the same error.

---

### Post by lian1238 on 2008-09-23
Here's an old thread with the same problem.

[http://ubuntuforums.org/showthread.php?t=763054](http://ubuntuforums.org/showthread.php?t=763054)

---

### Post by Interpreter on 2008-09-23
I didn't read the entire thread, but you guys ever considered Wubi an option?

[http://wubi-installer.org/]("http://wubi-installer.org/")

---

### Post by Snowybob on 2008-09-24
Hi interpreter I tried Wubi, went through the installation, rebooted but there is no sign of Ubuntu other than a folder created on my drive. in the Ubuntu folder there is a folder called winboot with a file wubildr.exe which I thought I might have to run. If I do run this I get a message 'The NTVDM CPU has encountered an illegal instruction'

Any more ideas?

---

### Post by Interpreter on 2008-09-24
Nah mine always worked the way its supposed to work.
If you've tried messing with CDs for days by now...., is there some sort of lan installation or somesuch so you could bybass that CD sh!t, even if it means alot of network hassle?

---

### Post by Snowybob on 2008-09-24
I have now got the boot option at startup (don't know what happened b4)

Problem is I get the same result as booting from the CD -'Use noapic' message - see earlier in thread. I guess it would now be possible to edit the config files (or whatever they are in linux but have not got a clue. Don't know which file(s) or what to do with them. I guess there's something about my machine's bios that linux does not like!

---

### Post by Interpreter on 2008-09-24
Which is why I think of thinking outside the box, maybe there's some way that doesnt fix, but bypass the bios stuff. Will have a google looksee during lunchbreak...

---

### Post by Snowybob on 2008-09-24
Thanks very much to all who made suggestions. In the end I went to HP and discovered there was a bios update and found out how to apply it. 

Tried to boot from CD, no problems and I now have Ubuntu and Windows XP dual booting succesfully - time to evaluate.

---

