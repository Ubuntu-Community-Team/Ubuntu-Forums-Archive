---
title: "would this hardware work as a home server?"
date: 2013-12-22
forum: Hardware
---

### Post by squakie on 2013-12-22
Looking at some way to have a centralized storage and backup server available only in-house - I assume that's what it would be if connected to the router on our Xfinity cable/phone/internet access device.  I know the hard disk would need to be a LOT bigger and hopefully a 2nd for shadowing, but would[ this ]("http://www.microcenter.com/product/422944/DC5800_Desktop_Computer_Refurbished")hardware be a good base system (remembering I would change out the drives)?

What type of information is available for the absolute beginner wanting to set up a media/storage/backup server for use on a home local network?

Thank you.

---

### Post by ian-weisser on 2013-12-23
> **squakie said:**
> would[ this ]("http://www.microcenter.com/product/422944/DC5800_Desktop_Computer_Refurbished")hardware be a good base system?

Assuming the fans aren't too loud, and it doesn't eat too much power, sure.
It's quite a bit more powerful than my own headless media/backup server.
Simply serving files does not take a lot of CPU.

> **squakie said:**
>  What type of information is available for the absolute beginner wanting to set up a media/storage/backup server for use on a home local network?

It's okay to experiment and change your mind. I wiped my (backed-up) data twice in the first six months because I changed my mind about an application or a networking method.

Start with one service at a time. Document ALL your changes and settings, and keep your documentation current.
I keep a folder in ~/ for each service with links to all the config and custom files, and a text file of notes.

Think security. It's an always-on server. Use ssh keys and all the other customary protections.

---

### Post by mörgæs on 2013-12-23
> **ian-weisser said:**
> 
Simply serving files does not take a lot of CPU.


+1. Heavy stuff like games, browser or media player runs in a GUI.

I wouldn't buy anything new for a server, just use whatever old hardware you have around.

---

### Post by caymus on 2013-12-25
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228](http://www.newegg.com/Product/Product.aspx?Item=N82E16813157228)

i use this for 24/7 30watts, & 38watts if you watch h264 with gpu decoding.

The "cons" transfert files with aes 256 bit, cpu is bottleneck, you can achieve 16 000 KB/s max

without encryption ~ 38 000 KB/s

It is enough for media streaming.
It is ok for a little ESXI server
It is ok if you watch movies only by gpu decoding.

Size your hardware to you reals needs.

A pentium dual core is fine to do almost everything, but this is nearly 3X more energy consuming... 24/7/365 .... $$$ at end of the year.

PS: if you use WM on tiny hardware like this, dont hope more than LXDE or fluxbox

---

### Post by heir4c on 2013-12-25
> PS: if you use WM on tiny hardware like this, dont hope more than LXDE or fluxbox 
?? I have the same E350 as you on my ASUS motherboard and I use Ubuntu 14.04 on it. (Without a extra Graphics card) I play even a movie with this. 
And with the dual core who squakie gives in his link he can also use Unity on it. But there is no need for that because it will be a server.

@squakie, I find that a little bit expensive for a second hand pc. Is there no secondhand website where you can buy stuff from individuals of your country (I don't now where you live)? Ok, it is with warranty but for the 90 days...

---

### Post by 1clue on 2013-12-25
Can't tell you how many times I've done this sort of thing.  I have a couple questions about your priorities:
[LIST=1]
[*]Do you want a project to keep you busy, or do you just want something that works?
[*]Is price really that much of an object?
[*]What services are included in "home server?"
[LIST=1]
[*]File server?
[*]Music?
[*]Home movies?
[*]DVD/media center?
[*]Searchable documentation archive?
[*]Scanner?
[*]iPad/iPod/android clients?
[*]Windows clients?
[*]Mac clients?
[*]...
[/LIST]

[*]How many devices are you talking about?  A recent survey of my home with just my wife and I yielded 27 active devices.  ***Edit:** That includes Windows, Linux, Mac OS, Android and whatever TV sets and BluRay has, a printer, and a couple other random net-aware devices.  Not represented:  iOS.*
[/LIST]

Now if you intend this project to learn how to set up services, or you just have the hardware laying around, then fine.  I'm all for that.  Do it on Linux, read up on a bunch of stuff and get working.

If you just want a nice central place to put all your family's stuff, then consider a Synology NAS, or something else similar.  They get down into the same price range as what you showed us.  They'll be more expensive after you add drives, but it will just work.  You stick the drives in, plug in the NIC, turn it on and go hit the web page, it's serving in more formats than you knew there were.  It's probably using the same software you'd set up too.

That said, a lot can be said for a NAS with a removable disk drive so you can back up to it and take that backup off site.

---

### Post by caymus on 2013-12-26
@[**[COLOR=#000000]heir4c[/COLOR]**]("http://ubuntuforums.org/member.php?u=739011")

Yes Unity work on it, but it is a little to much bloatware to use this DE, many hours, with reactive behaviours.
It is more confortable with openBox or lxde from a minimal iso cd instalation.

I have say this only, in the case he would use te E350 for something else after a moment.

For gpu accel i speek about the ati gpu integrated to the motherboard to.

cpu cannot handle h264 1080p very well. With gpu accel enable & ```
xvba-va-driver libva-glx1 libva-x11-1 vainfo
``` 1080p work like a charm

@1clue

For synology NAS, this is a computer.
The cheapest are not able to handle more than 8000 KB/s because low power arm, risc or mips cpu are bottleneck.

Middle & High performance synology NAS are pentium computers packaged in a NAS solution, he can do the same with freeNAS or something else on a pentium or amd.
Or by building is NAS from minimal distros.

If he know about how to do, i dont recommand to buy a all made NAS solution.
Else a solution like synology is maybe not bad.

If this is a professional NAS he must look at /proc/cpuinfo
flags: aes(cpu have specific instructions to handle aes encryption for file transfert) else this is alot of extra work for the cpu.

Most of I7 or xeon processor handle this instruction, sometime there is a chipset on motherboard to handle this, on arm, mips, risc cpu, also.
If you go for a low power NAS, low cost, cpu is bottleneck, you cannot make files transfert faster than a 10/100 nic, while they put gigalan 10/100/1000 nic on the package, for commercial impact.

So E350 with 38 000KB/s (without encryption file transfert) is a good choice for a low electrical power NAS to deserve the familly.
For the 1rst comptuter [**[COLOR=#000000]squakie[/COLOR]**]("http://ubuntuforums.org/member.php?u=1741485") show this is more powerfull, but after 365 days, the electricity cost difference is $, with 3 numbers vs E350.

I know because i run a HP proliant DL380-g5 also who consume "only" 165 Watts
The pentium you are looking is between 80-125 Watts.

Now he only need to choose what he need really.

---

### Post by 1clue on 2013-12-26
@caymus,

I do NOT want to start a huge debate on this and detract from the OP's thread.

My Synology recommendation is based on a small bit of experience.  With FreeNAS I've heard complaints about not being able to take advantage of some newer hardware.  I mentioned Synology would be more expensive, but frankly how much more depends on the buyer.  For me, the hardware cost would put me in the $1000-$1500 range anyway, USD.

My point was that, if the OP wants to build something personally then go ahead, I'm not going to naysay that at all.  Been there done that lots of times.

If the object is to have a working solution for most likely scenarios and clients, if you consider your time worth something then that quickly pays for a commercial product.  Go ahead and figure your time to build a box, install some NAS software on it (ubuntu, FreeNAS, whatever) and then pay yourself a working wage for all the time you spend messing with it before it works right.  You're gonna hit $500 USD in no time flat, just for labor costs without hardware costs for a basic machine.  There's no way I'd be able to reproduce a commercially viable NAS setup for the money it would take to buy one.  The same is true for the guys who sell them.  They do it once, then make them by the thousands and install that same image on there.

I don't know about you or the OP, but there are a LOT of other projects I'd rather work on than something with a hands-down better solution than I could come up with on my own.  Frankly right now if it were my setup, even though I've done this a bunch of times, I'd go buy a decent Synology.  I already have one, it was a snap to set up and it was doing its job less than 30 minutes after I opened the box.  I'd do it this way again without hesitation.  It supports Mac, Windows, Linux, Android, iOS, http, ftp, whatever.  The one I got supports virtual machine images.  You want add-ons?  They can be downloaded and installed no problem, don't even need an IT guy.

Again, if the OP has a desire to learn or wants a challenge, then I'm all for that too.  I don't have a clear indication from the OP what the priorities are, which is why I suggested a prebuilt NAS.  I mentioned Synology because that's the brand I chose for myself.

---

### Post by caymus on 2013-12-26
Yes I completely agree with you, I'm just saying that without knowing his level of knowledge of gnu/linux, BSD, IT admin, networking etc:

> 
[COLOR=#ff0000]If he know about how to do, i dont recommand to buy a all made NAS solution.
Else a solution like synology is maybe not bad.[/COLOR] (or say in another way: [COLOR=#ff0000]maybe a good idea[/COLOR])


for FreeNas this is only a freeBSD prebuild with a nice nginx gui around NAS tools, for corporate hardware or non exotique hardware, no problem.
For exotic hardware for home users, freeNAS not being able to take advantage of some newer hardware, yes this is the case with *BSD & to a lesser extend, for gnu/linux also.

But this is another story... (FreeNAS is maybe not a good exemple, because zil/zfs as default, for home usage...)

   What I mean is, if he know realy well the subject, he only need 1 hour to do a corporate grade NAS from scratch, key in hands.
 Else if he need to learn before, spend dozens or  hundreds hours, he have more chance to buy a already made key in hand NAS as synology, I agree with you.

---

### Post by 1clue on 2013-12-26
@squakie,
Having read back at your points, I'm going to lay down a few ideas for my personal solutions to your stated problems.  I've been an IT professional since the 90s, and have gone through a lot of tech for backups and storage and servers.

**Backups**:  I use a removable drive.  Right now, I have a "slot load" bay in my Linux tower, it's a SATA bay that I can just plug a plain-old internal drive in as though it were a tape cartridge.  It has an eject button.  I have a few cartridges, but you should figure on at least two.  You can use a plug-in USB drive if you really want to, but IMO that's extra expense and extra complexity, for a not-very-reliable data connection and a tendency for the drive to "sleep" at inopportune times.  Oh yeah, don't use WD green drives.  4 failures in 1 year, on my personal equipment.  Out of 4 drives total.  Just saying.
Here's the process.  I'm referring to the backup disk as a "cartridge" even if you're using something else:
[LIST=1]
[*]Never leave a cartridge in the drive when you're not backing up.
[LIST=1]
[*]The whole point of a backup is to remove it from your system, take it elsewhere and store it in case something bad happens to your server.
[*]If you don't remove it, it's not a backup.  It's a copy, just as prone to error as anything else on your computer.
[*]RAID is not a backup because you don't remove it.  It prevents data loss if a drive fails, but that's one of many possible data loss scenarios.
[*]If your computer takes a lightning bolt, or a cut power line, or a brownout, or power supply failure, fire, burglary or any number of other disasters, then your "in place" backup is probably dead too.
[/LIST]

[*]Every so often (you say when) you plug a cartridge into the slot.
[*]Make a new folder at the drive's root level.  (2013-12-26 for example)
[*]If you estimate that there is not sufficient room on the drive, delete the oldest backup.
[*]Copy files into that folder from everywhere you want to save data from.  I use the format 'hostname/path/to/data' so I can figure out exactly where the data came from.
[*]Don't use compression or any sort of application.
[*]Don't back up the operating system.  You can get that back pretty easy.  It's your data that matters.
[*]If you're backing up databases or music libraries or something, back them up as exported files or something portable, meaning any version of the common app can read the backup.
[*]You CAN script the backup if you like, but keep in mind that if you change your directory layout you'll break your script.
[*]When the backup is finished, eject it and put it someplace safe.  Like a different building.
[*]When you return, take the oldest cartridge in your set back to your server for use next time.
[/LIST]

Here's my rationale:
I've bought several tape backups over the years.  That stopped when I finally had to use one of the backups, and found out that none of the backups I made could actually be restored as usable data.  There was an article on this years ago, how when you came up with your backup scheme the first thing you should do is restore a backup to see what came out.  Too late for me, but something I enthusiastically read because of my own little disaster.

I've used CDROMs and network scripts and special backup software and compression.  At some point you'll have to use the backup.  If your special software is on the drive that failed, and your backup has the "backup" of that software, you're screwed.

If you use some compression algorithm, you wind up with a big file full of other files, and if that gets corrupted you lost everything.  If you don't use anything fancy, and your drive is a plain old disk drive, then you can stick it in ANY linux box and find the exact file you lost, you can copy all the related stuff from that backup or you can pick and choose files.  No training, no planning necessary.  Works on anything.

When you have a drive failure, you want the latest backup, NOW.  You're in a rush and you just need to get it.  Don't make it complicated.

**Storage/servers**:
For media and file servers, I figure this is the last thing you really want to do and it's such a universal problem with dozens of happy solutions.  Furthermore, chances are you're a semi-normal household and have android or iOS mobile devices, and maybe a Mac or Windows box, along with your Linux setup(s).  Getting all that stuff to work together, get access to the same files and folders, that's actual work.  Why bother?  Get something that does it out of the box.  FreeNAS and Synology and most other NAS setups have media servers and built-in search engines and a whole lot of extras that either come with it or are available for free, or in some cases if you want it fancy you have to pay for it.

Again, since you haven't responded with your intent here:  **If you WANT to do this by hand and learn something, then ignore everything I've said in this thread.**  Except the part about backup drives in this post.  I'll put that basic procedure down against anything anyone else can come up with.

There is absolutely nothing wrong with building it by hand.  But expect to pay more than the commercial product, if not in money then in time spent.  The advantage here is that you will know how, it will not be a mystery and you might actually use it in your work at some point.

---

### Post by squakie on 2013-12-28
Well, there are 3 computers currently - one Windos XP that I hope to get the person involved switched over to Linux before April, a Windows 7 PC and currently my Ubutnu 13.10 desktop.  There are also 3 Raspberry Pis acting as media centers and each currently has its own USB hard disk for media storage.  I have XBMC on my Ubuntu box and use an external 2tb USB drive (ntfs) so in case something happens I can still access the media files other than just in Linux.  There are 4 different tablets in the loop as well.

I also worked as a systems programmer and tech support from mainframes to minis to micros and networking from proprietary to ethernet lans.  This was all in the 1970 to 1996 time frame.  I have pretty much forgotten everything I ever knew.  So, my golas are:

- to learn
- to act as a centralized backup solution
- hopefully (haven't tried streaming to a Pi yet) having a centralized media storage/server instead of individual disks at each media system
- document storage
- I would also like to learn more about the server software itself, the various types of web interfaces to it and from it, which I believe includes things like online database access, PHP (??), etc..  I just plain don't know anymore, so I need to start over at the basics.  I have already done Samba sharing with no problem (except with Windows 8, but that's documented).

So, that's what I can think of if it helps anyone.  I'm pretty much thinking back to my IT days when a server was a catch-all do-all box.

---

### Post by 1clue on 2013-12-29
OK that's a big help.

If you worked with IBM hardware during that time, especially more recently, we could talk the same language.  I worked in AS/400 and RS/6000 land for a few years, maybe 10 or 15 years ago.

So I'm getting the feeling from your most recent post that you're interested in the diversion.  That's fine, as long as you don't need something up and running right away.

Personally I stay away from refurbished equipment if possible for anything I'm going to spend a lot of time on, or anything that I need to rely on.  For all the reasons you heard about in your IT career.

I'm going to make a recommendation, assuming you have financial resources to do it:  Get a bigger box, and install KVM/QEMU on it.  Then, on top of that, put all your servers and services in as guest VMs.  I wouldn't buy anything that's not capable of 12g or more as a server anymore.  I make heavy use of VMs in my work, and they give you all sorts of freedom.  For example:
[LIST=1]
[*]You can build a server for one conceptual thing, or some number of related things without risking damage to other services.
[*]You can upgrade/modify/reboot one of the virtual servers without affecting other services.
[*]You can try for a better install of something you did that didn't turn out quite like you'd hoped.
[*]You can experiment with out-of-the-box storage solutions like FreeNAS, without being stuck with it for other servers.  Then if you don't like it, or part of it, you can install another VM to take over whatever you didn't like.
[*]There's always some other type of server to try, or even a desktop OS.  Put it on as a VM and you can try it out no problem.
[*]You can mix operating systems, even Windows if you want.
[*]You make better use of your hardware to have VMs on it.
[/LIST]

---

