---
title: "Speed"
date: 2010-06-26
forum: Hardware
---

### Post by komputerkurt on 2010-06-26
Hi, I'm looking to change over to Ubuntu, and I'm wondering what effects it would have on my computer. 

Right now my computer runs a Single core 1.7ghz:mad: AMD athlon XP with a 128 mb ATI radeon 9200SE graphics card with 768 mb of RAM, a Ralink wireless internet card and a 160GB hard drive. 

I currently have Windows XP with Kaspersky Internet security, ATI catalyst (c), Dropbox, logitech setpoint, and a C-media mixer (sound card drivers). 

I'm going to try to find all those things for linux but my main concern is all my games that I play are only for windows. I've heard about "WINE" to emulate windows on my linux. 

I'm wondering if using this will make my computer so slow that it won't be able to play my games anymore. What sort of effect will this have on my computer? Will the games run faster, normally or slower/incapable? Is there a lighter version of the WINE so I can run all my games? 

I'd also probably have to install them on the emulated XP, I'm not sure how well that would work out as it puts things in Local Settings and stuff.

Could you guys help me out with this dilemma?

---

### Post by marshmallow1304 on 2010-06-26
It is quite possible that Ubuntu may be snappier than XP on that hardware, especially without the added weight of Kapersky.  If you find Ubuntu to be too slow, there is always [Xubuntu]("http://www.xubuntu.org/"), which is designed to be lighter to run on older hardware.

Wine is an excellent resource, but it's not perfect.  Performance depends on the particular game.  Luckily, there is a [database of applications]("http://appdb.winehq.org/") that lists how well many applications run in Wine.  For some games (such as WoW), performance has been reported to be greater running in Wine than natively in Windows.

Wine is fairly intelligent with how it handles Windows folders.  Wine keeps its "C: drive" in a folder in your home directory (/home/<user>/.wine/drive_c) and links the "My Documents" folder in the virtual C: drive to /home/<user>.


If you have the hard drive space, the best step forward may be a [dual-boot]("https://help.ubuntu.com/community/WindowsDualBoot"), so that you can keep Windows around as a failsafe and for any games that don't run up to par in Wine.

---

### Post by Revolutionary101 on 2010-06-26
I have been using Ubuntu for over a year now on my laptop with a 1.6 GHz single core Pentium M CPU, integrated graphics, and 1 GB of RAM. Ubuntu is definitely faster than Windows XP ever was.

If you are looking to have all your games work when you transition to Ubuntu, you might be disappointed. Yes, Wine can run some Windows games but it is not the holy grail when it comes to running Windows games on Ubuntu.

Although, Ubuntu does have some games that run natively on it. Some examples of these games are OpenArena (A game similar to Quake), Alien Arena (kinda like OpenArena but with better graphics). Ubuntu also has many other great games that run natively on it that I haven't even mentioned.

Also, I wouldn't recommend diving straight into Ubuntu (This would mean wiping your HDD and completely converting to Ubuntu). Instead, I would suggest install Ubuntu via Wubi which is a nice way to try Ubuntu on your computer. It lets you try Ubuntu, yet it still keeps Windows in case you want to go back.

---

### Post by komputerkurt on 2010-06-26
Well I'm actually running Windows XP on a obsolete and almost full 20 GB HDD which is another reason for me to switch over. 

What I'd do would have my current user with everything on it then another bare-bones account in case I can't play some of my games, I haven't looked into this yet but the game I really want to work is [crossfire]("http://crossfire.z8games.com") which also runs HGHW game watcher and XTrap when it runs, to prevent hacking which I'm not sure if WINE would step in or not which is why I'll have the bare-bones XP account(because this user takes 5 mins to start up, ROFL but not so funny when you just need to check your email...).

EDIT: I have now checked on the game's forum and found [this]("http://forum.z8games.com/showthread.php?t=39803&highlight=linux") (refer to the last post for the answer)... looks like I'll be needing that second account in Windows. I'll look into other games but I'm not duly concerned about them. Looks like I was right about XTrap not working with WINE... the game probably would though. 

Also I would like to know more about some Linux things.
1. Is there a keyboard shortcut to the CPU monitor like in windows XP
2. Is BERYL a theme for Linux and would it slow down my computer considerably if I used it?

---

### Post by Revolutionary101 on 2010-06-26
> **komputerkurt said:**
> Well I'm actually running Windows XP on a obsolete and almost full 20 GB HDD which is another reason for me to switch over.

If you only have a 20 GB HDD I suggest you upgrade, especially if you are going to be using two operating systems that would take up at least 12 GB out of the 20 GB. You could buy a cheap HDD to upgrade with.

To answer your questions:

1. By default there is no shortcut to a CPU monitor. Although you can change that. I currently have my computer setup to open a task manager/CPU monitor when I press Ctrl+Alt+Delete. Unlike in Windows you can customize pretty much anything in Ubuntu, including shortcuts.

2. Beryl is the name of an old eye candy management system for Linux. Currently, Beryl, itself, no longer exists. It is now part of a thing called Compiz Fusion. Compiz Fusion lets you enable almost any cool effect for Linux, for example the 3D desktop effect. I have it enabled and I can barely notice a difference in performance on my old laptop.

---

### Post by komputerkurt on 2010-06-26
Ok good. I have 2 HDD lol. My 2nd one I bought used and it still had files on it lol. I could have soooooo totally screwed the previous owner over especially since it was a work at home computer judging by the remote connection shortcuts. They gotta have saved some passwords lol. NOTE THAT I DIDN'T I just made sure there weren't any viruses. Also it was the shop's fault for not wiping the HDD, so it also tried booting from that one first causing a lot of trouble.
EDIT: Also does linux tend to break down after using it for a while like XP? On my computer explorer is screwed up bad... when I try to open downloaded programs my computer slows down soooooo much the only way I can open it is if I do then I hit CTRLALTDELETE and then wait a minute for the task manager to pop up which opens the setup/ windows component. FML

---

### Post by Revolutionary101 on 2010-06-27
> **komputerkurt said:**
> Ok good. I have 2 HDD lol. My 2nd one I bought used and it still had files on it lol. I could have soooooo totally screwed the previous owner over especially since it was a work at home computer judging by the remote connection shortcuts. They gotta have saved some passwords lol.

I would not suggest doing that. However, as long as you got a bigger HDD to install on your computer that is good.

P.S. Just for further reference, the Ubuntu community and the forum moderators look down upon talking about messing with other peoples files to harm them. It is against the Ubuntu code of conduct and a good way to get your thread closed. But thats just a warning, be glad that a forum moderator didn't catch that.

---

### Post by komputerkurt on 2010-06-27
Arggggg the iso takes so long to download... I hope theres a P2P version...
EDIT:awww man I couldn't find one... anyone know of a good one or is that breaking the rules?

---

### Post by Revolutionary101 on 2010-06-27
Here is a link that will take you to where you can download Ubuntu via Bit torrent aka P2P.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

---

### Post by komputerkurt on 2010-06-27
shhhhh don't say that frowned upon name on any legal forums!
anyways I'm typing this from my gaming profile user which took 
[SIZE=7]1 hour[/SIZE] to "personalize settings". dam computer...

EDIT: Thanks for the link, although I'm only getting about 20kbps faster...

---

### Post by cascade9 on 2010-06-27
> **komputerkurt said:**
> shhhhh don't say that frowned upon name on any legal forums!

EDIT: Thanks for the link, although I'm only getting about 20kbps faster...

What, 'bittorrent'? 

Its not a problem, that is a 100% legal torrent, and its not the only one. 

I get a LOT more speed from torrents than from direct d/l. Torrenting any major linux .iso I normally max out my conenction speed, or pretty close (getting 2MB/sec +).

---

### Post by komputerkurt on 2010-06-27
Yes most forums don't like that name even though it has some legal torrents there are far more illegal ones. Anyways, for some reason (probably the time at night) I only got 110kbps :(((((
My last ubuntu question before I'm confident enough to install it... can you choose which drive to install it on? My C drive is the 20 GB one and with the new user it has 500mb left on it :P . My E drive has 70GB left on it and if I cleaned it up probably much more.
EDIT:IS anybody going to answer that simple question or will I have to find out myself :P ?
Also will installing linux overwrite the My Documents or Program Files folders on my E drive?

---

### Post by komputerkurt on 2010-06-27
[http://www.youtube.com/watch?v=J0GQeyaAyyE](http://www.youtube.com/watch?v=J0GQeyaAyyE)

so if I created a small partition would it try to install everything in that small partition? or does linux work as the system in a separate virtual disk with files put into another? Would WINE use that partition?

---

### Post by komputerkurt on 2010-06-27
also which one should I download so I can install it after installing ubuntu?
[http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

---

### Post by cascade9 on 2010-06-27
> **komputerkurt said:**
> Yes most forums don't like that name even though it has some legal torrents there are far more illegal ones. 
 
 This isntr that sort of forum. Swearing? Bad, mkay (see, if I type *** it censors it). Torrents? Porvided that you arent doing the 'get yo warez here' posts, its fine here. 
 
 > **komputerkurt said:**
> Anyways, for some reason (probably the time at night) I only got 110kbps :(((((
 
 Probably your torrent isnt setup right. Or your ISP is throttling torrents. :( 
 
 > **komputerkurt said:**
> My last ubuntu question before I'm confident enough to install it... can you choose which drive to install it on? My C drive is the 20 GB one and with the new user it has 500mb left on it :P . My E drive has 70GB left on it and if I cleaned it up probably much more.
 EDIT:IS anybody going to answer that simple question or will I have to find out myself :P ?
 Also will installing linux overwrite the My Documents or Program Files folders on my E drive?
 
 Err...not to sure, you would be doing a WUBI install and I've never done one of those. 


> **komputerkurt said:**
> also which one should I download so I can install it after installing ubuntu?
[http://www.avast.com/linux-home-edition#tab4](http://www.avast.com/linux-home-edition#tab4)

The deb package....if you decide that you want antivirus on ubuntu. There are no linux viruses 'in the wild' so you dont need an antivius with linux distros.

---

### Post by komputerkurt on 2010-06-27
Well this was on my new user account and it didn't complete the bandwidth test but it was set to 80 peers and I've gotten 1mbps before which is my max. What about rpm and tar.bz2 files?

---

### Post by cascade9 on 2010-06-27
RPM = red hat package manager. 
Tar.bz2 will be the source coce. 

Its possible to install RMP files into debian based systems (like ubuntu) but its not something you would do unless that is the only choice. Its also more than possible to compile from the source code with ubuntu, but its a lot easier to install from a deb (debian package manager file) if it is avaible.

---

### Post by komputerkurt on 2010-06-27
well I'm a total linux noob so could you give me a link on how to use rpm and those tar files because those are the only option for some. I think I'll put linux on right now.

---

### Post by komputerkurt on 2010-06-27
ok so I just installed ubuntu after 2 hours of trying to open the installer (remember how it took 1 hour to make personalized settings) and now I need to access the windows E drive aka the one where it got partitioned... I can't find it lol. I guess I'm going to have to reboot into windows and move them over to access them for now.

---

### Post by Revolutionary101 on 2010-06-27
> **komputerkurt said:**
> well I'm a total linux noob so could you give me a link on how to use rpm and those tar files because those are the only option for some. I think I'll put linux on right now.

Here is a link that should explain how to install rpm files.

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

Here is a link that should explain how to install .tar files.

[http://ubuntuforums.org/showthread.php?t=246092](http://ubuntuforums.org/showthread.php?t=246092)

.tar files are just like .zip files on windows. They are just a compressed folder with a bunch of files in them. I have to say that it is a lot easier to install a .rpm file. Also if you are ever installing something that doesn't come in the Ubuntu repositories try and find a .deb file. They are just like how .exe is for Windows, but .deb files are for Ubuntu.

Another thing that you may want to know about Ubuntu (and other Linux distros). It has things called repositories. Repositories contain thousands of programs that you can download and install, all from one place (its like that App Store for the iPhone, but free). This is a lot easier than searching the web for programs, like you would with Windows. Bottom line is, try and find a program in the repositories because it can save you some headaches.

---

### Post by komputerkurt on 2010-06-27
where should I extract a program to in the file system? So far I'm very impressed by Ubuntu

---

### Post by Revolutionary101 on 2010-06-27
For a tar file I would suggest you extract it to your home folder. It just makes it easier when you have to install it via the terminal.

---

### Post by komputerkurt on 2010-06-27
wow I've also noticed a difference in speed my "busy light" on my computer rarely turns red even though right now about 100% of my CPU is being used. I was going to upgrade it to a strobe light before since it blinked every tenth of a second lol. Right now I'm updating things and installing WINE.
So about Compiz... how do I get it and enable it?

---

### Post by Revolutionary101 on 2010-06-27
Go to Applications>Ubuntu Software Center. Once that windows pops up search for "ccsm" (without quotes). Then select the first option that pops up. It should have an icon of a box with a red squiggly on it. Then just click install to install it.

---

### Post by komputerkurt on 2010-06-27
thank you guys, I now know how to use linux way better!

---

### Post by Revolutionary101 on 2010-06-27
I am glad I could help.

---

