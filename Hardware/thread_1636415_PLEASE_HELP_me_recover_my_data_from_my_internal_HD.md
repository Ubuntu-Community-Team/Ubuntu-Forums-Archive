---
title: "PLEASE HELP me recover my data from my internal HDD by utilizing my external HDD plz"
date: 2010-12-03
forum: Hardware
---

### Post by djpurity on 2010-12-03
Here is a quick run-down of my problem, and what I want to do in order to fix it. Please bear in mind my UNIX and Linux skills are quite rusty, and I've only had to recently try to unearth the mounds of dust from them in my own shell I run called my brain.

I have an ACER ASPIRE 5251-1805, which came pre-installed with WINDOWS 7 64-BIT Home Deluxe (whatever, it's all the same), and after a short confrontation with my lazy laptop, we got into a bit of a physical altercation. Basically, the computer police had to be called and put a restraining order in between me and my laptop, and this has caused me a world of heartbreak and misery trying to win this bastard back.

Basically, I've tried the whole "Microsoft Answers" forum showcase showdown crap, and nothing has really helped. It appears at least in my opinion, to be a problem with the master boot record (MBR) and all that file allocation table (FAT) stuff, or the partitioning data. Or all of the above.

The reason I conclude that is that like most shipped-off Windows-pre-installed laptops, there was no physical Recovery or Installation DVD that came with the system, which would make a whole world of sense. But because Microsoft is renown for its dollars and not it sense, I have 2 partitions on my 250 GB l'il firecracker of a HDD: one is the SYSTEM RESERVED labeled one, the one that remains hidden until such a time arises as this, when a repair needs to be attempted by the computer without the use of the Recovery or Installation boot DVD. I actually downloaded my own image of the Recovery CD/DVD and have that as well, and running Startup Repair is just not working out for me and doing that whole "let's do it Microsoft's suggested way" thing just isn't cutting it, just like listening to the advice of that stupid paperclip.

So now that I got a cope of Ubuntu 10.10, I am able to run a "live" working version of its O/S, with its extreme limitations, of course. I would love to actually be able to just install the full working version of Ubuntu and be done with it, but I actually have a lot of good, decent memories on that ol' file system on that HDD. I have so much work, effort, blood, sweat, and not-so-many tears, but enough that I will not format or overwrite the computer in any way that could result in possibly losing any line that may be still thrown out linking it to the sinking ship of that partition.

In Ubuntu, the SYSTEM RESERVED recovery partition shows up just fine and mount. It is the other partition part that fails to mount. It says "Opening..." and "You can quit this at any time by clicking cancel" or something like that, because it is taking so long to try to mount, and basically, in the end, there is no fantastic or miraculous mounting of any sort, and I get a message much like:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Anyway, I have just gotten an entirely brand new Seagate external USB 2.0 HDD. It is connected to my laptop and it mounts just fabulously, and what I want to ultimately do in the longrun is this:


[LIST=1]
[*]Be able to locate the data on my partition that is having problems
[*]Back up the data by saving it by either burning it or putting it on the external HDD
[/LIST]

OR 
alternately I could see myself as:

[LIST=1]
[*]Being able to install a fully working version of Ubuntu on the external HDD
[*]Boot from the external HDD using Ubuntu full version
[*]Then find a way to access the partition of the HDD that exists inside my laptop
[*]Recover and burn off the saved Windows data from that point on from inside Ubuntu rather than trying to work using this "live" running O/S off this DVD, which really is making me sad in the face
[/LIST]
So is there anyone that can help me achieve either of my goals of recoverying my data? At this point, I am not so much a huge fan of restoring my system to whatever state it was once in; I would be quite happy to just recover the data I need and then format the hard drive completely with either Windows 7 again or Ubuntu, either one, or both, or whatever, I don't care, as long as I get in the end two things:

[LIST=1]
[*]My data that must be saved and recovered
[*]A fully working and running Operating System on a fully working laptop
[/LIST]
It really is that simple. So basically, can I install Ubuntu to my external HDD without affecting the boot records and file allocation tables and pointers and records and all that of the main internal hard drive where all this lovely and valuable delightfully refreshing data is being kept prisoner for quite a hefty ransom? I do promise to continue seeking therapy and counseling for my anger management and I swear never to lay a finger on my laptop in anger again, officers.

THANK YOU FOR ANY AND ALL SUPPORT AND HELP. Remember, I haven't used UNIX and Linux since I was back in college, which was a long time ago. Okay, not a very long time ago. I did graduate just 7 years ago. But back in the days I was using those O/S's as my main O/S's and shells, rather, were closer to 1996-1999.

So consider me a little rusty.

THANKS AGAIN!

---

### Post by mastablasta on 2010-12-03
your rescue disk is supposed to be created from your restore parittion.
 
you got it elsehwere and tried to repair the MBR by booting with rescue disk, going to conosle and uising the fixmbr. this didn't work. you also say that you can't mount the disk. 
 
this could have something do do with the start of partition being damaged.
 
I think repairs can be done... there are a couple of windows programmes out there that work. i once had a bad shutdown and destroyed partition and some disk doctor or something similar saved me. i would have to check my home ocmputer. basically it repairs the tables. maybe something similar could be done with g-parted (default Ubuntu disk utility).
 
once oyu repair this you should see your data and transfer them to your new disk.

---

