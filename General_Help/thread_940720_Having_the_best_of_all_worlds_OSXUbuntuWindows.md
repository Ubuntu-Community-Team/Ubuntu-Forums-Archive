---
title: "Having the best of all worlds: OSX/Ubuntu/Windows"
date: 2008-10-07
forum: General Help
---

### Post by K0NY on 2008-10-07
I've just put together a "dream pc" for myself consisting of:

Intel DP35DP Motherboard
Intel Core 2 Quad 2.4ghz CPU
4GB of OCZ DDR2
EVGA Geforce GTX260 PCI-E video card
2 x Samsung 1TB HDD 7200RPM (for a striped RAID config)

Originally, I considered running Ubuntu exclusively on it and maybe using a virtualized Windows XP or OSX to play around with. However, gaming is pretty high on my list of stuff I'd like to do with this computer. So I'm not sure what would be the best way to set it up.

Am I better off with a dual boot of Ubuntu and Vista with a virtual OSX Leopard getting installed down the road? Or should I dual boot OSX and Ubuntu then buy a Vista disk later to run in a virtualized capacity?

I've read that WIndows server 2008 actually performs better for gaming than Vista and is generally more efficient. Could getting that instead of Vista or OSX be a better solution?

At this point my options are wide open and I'm not sure what would be best for this system. With my current hardware are there choices which are simply not practical or too difficult to setup?

Thanks for your help.

---

### Post by Idefix82 on 2008-10-07
I would not use Vista in any scenario. It's buggy and a lot of software does not run on Vista. And it is really hard on the resources, which is not ideal if you want to play resource hungry games.

I would say the best two options are either Dual boot with XP and Ubuntu or run Wine. I don't play games myself but I have read more and more often that Wine is increasingly compatible with most Windows software and games.

Since installing Windows on top of Ubuntu is a bit of a pain (not much) I would go with a dual boot setup to start with, then try Wine and if that works then delete XP again, as soon as you are sure that you don't need it.

---

### Post by mixmaster on 2008-10-07
I'd second the advice to use XP instead of Vista.  However, I am doubtful about the ability of wine to play most of the high performance games and I think unless you find futzing around with wine configurations as much fun as actually playing the games you would do better with dual boot.  Of course, if everything you want to play is supported by cedega you could go that route.

---

### Post by davidryder on 2008-10-07
> **Idefix82 said:**
> I would not use Vista in any scenario. It's buggy and a lot of software does not run on Vista. And it is really hard on the resources, which is not ideal if you want to play resource hungry games.

I would say the best two options are either Dual boot with XP and Ubuntu or run Wine. I don't play games myself but I have read more and more often that Wine is increasingly compatible with most Windows software and games.

Since installing Windows on top of Ubuntu is a bit of a pain (not much) I would go with a dual boot setup to start with, then try Wine and if that works then delete XP again, as soon as you are sure that you don't need it.

On any high-performance machine with 4gb of RAM and almost a gig of video RAM resources aren't going to be a problem. 

That said, as a gamer myself, there is no practical alternative to Windows. WINE simply isn't worth the effort to hack every time I install a new game and I already have Vista on my HTPC and it has worked fine. 

On a machine that fast I would definitely run Vista. It looks nicer than XP and networking has been recoded from the ground up - making networking way easier than XP. Plus, WinFS won't be shipped with XP.

EDIT: Sorry I didn't clarify, but my perfect setup given your circumstances would be Vista & Ubuntu in a dual-boot system. I couldn't still imagine needing OSX after that. But if you just wanted to play with it you could run it in a VM.

---

### Post by jerome1232 on 2008-10-07
Vista still uses ntfs, no winfs to be found, but vista has one thing xp doesn't dx10. If you are going to use this machine primarily for gaming there's not much the other OS's offer over Windows. A few good commercial games are available for Linux and OSX.

---

### Post by davidryder on 2008-10-07
> **jerome1232 said:**
> Vista still uses ntfs, no winfs to be found, but vista has one thing xp doesn't dx10. If you are going to use this machine primarily for gaming there's not much the other OS's offer over Windows. A few good commercial games are available for Linux and OSX.

I didn't say Vista uses WinFS. Vista *will* use WinFS, and *when* shipped, XP *won't* get.

---

### Post by rhololkeolke on 2008-10-07
I would recommend dual booting instead of running windows in a virtual machine.  Just make sure you install windows and then ubuntu otherwise you'll have to reinstall grub.  I personally don't use Vista but if you plan on playing new games that's the OS they will start coming out for.  Also as jerome1232 said,"Vista has dx10".  If you want to be able to access your ext partitions I recommend installing this on the windows side [http://www.fs-driver.org/](http://www.fs-driver.org/).  It works great for me and it is a big time saver as you don't have to reboot if you need a file from the ubuntu side.

---

### Post by jerome1232 on 2008-10-07
> **davidryder said:**
> I didn't say Vista uses WinFS. Vista *will* use WinFS, and *when* shipped, XP *won't* get.

It's the subtle differences that always get me, I know Vista was supposed to have it, I just figured It got pushed back 'till their next OS release.

---

### Post by davidryder on 2008-10-07
> **jerome1232 said:**
> It's the subtle differences that always get me, I know Vista was supposed to have it, I just figured It got pushed back 'till their next OS release.

I know :(

I hope they are kicking themselves in the **** for not shipping Vista with WinFS. One of my professors (MSDN admin) swears it's coming in SP2... though I won't hold my breath.

---

### Post by K0NY on 2008-10-08
Thanks to everyone for their opinions. I'll probably install Windows Server 2008 then Ubuntu for the dual-boot using Grub.

I was looking at the triple-boot option using a 3rd party boot manager software, but since I don't have experience with any of them, I don't know which would be worth a purchase. If anyone had any suggestions, I'd appreciate it.

I'm leaning now towards Server instead of Vista because it seems to have a few less bugs but most of the advantages of Vista. I really wanted a fully functional OSX install to play with but since that will be an added expense, I'll probably hold off and use it as a VM down the road if there isn't a simple boot manager solution to get it implemented as a boot option.

---

### Post by fjgaude on 2008-10-08
> **K0NY said:**
> Thanks to everyone for their opinions. I'll probably install Windows Server 2008 then Ubuntu for the dual-boot using Grub.

I was looking at the triple-boot option using a 3rd party boot manager software, but since I don't have experience with any of them, I don't know which would be worth a purchase. If anyone had any suggestions, I'd appreciate it.

I'm leaning now towards Server instead of Vista because it seems to have a few less bugs but most of the advantages of Vista. I really wanted a fully functional OSX install to play with but since that will be an added expense, I'll probably hold off and use it as a VM down the road if there isn't a simple boot manager solution to get it implemented as a boot option.

Isn't it true you can't install OSX on any hardware that isn't purchased from Apple?

---

### Post by jerome1232 on 2008-10-08
It used to be only installable on a power pc architecture, now apples use intel chipsets.

Usually you would buy a Mac machine and install Windows alongside it though.

---

### Post by phidia on 2008-10-08
> **fjgaude said:**
> Isn't it true you can't install OSX on any hardware that isn't purchased from Apple?

It's actually illegal to install OS X on anything not build by Apple.
Check out the EULA on any OS X disk, and it's not allowed to ask questions about those types of violations in the forums.

---

### Post by davidryder on 2008-10-08
> **fjgaude said:**
> Isn't it true you can't install OSX on any hardware that isn't purchased from Apple?

Legally, yes that is true. There are however a lot of hacks for it (which all suck IMO).

---

### Post by bravo351 on 2008-10-08
Kony:

I was slightly disappointed to find so much work involved in configuring the Windows emulator in my Hardy (but I wouldn't trade my Linux back for all the wealth of Avarice rofl), so holding on to my Vista in the dual boot config is currently my only option for gaming.  The closest I ever got Wine to running my Grand Theft Auto- San Andreas was 3fps, and that's on nVidia GeForce 8500 with 1/2 a gig, so I still have work to do if I want to cut the tether.

That being said, I dialed my Vista HP SP1 in pretty tight before I cut it loose, but with all the speed tricks, the dialed back Aero engine, etc.., I still never enjoyed the same speed I had with my XP pro.  Couldn't tell you anything about Server 2008, but when I get back to wanting to run my Halo, I'll slap XP back in there and live with my Dx9.

Oh, and BTW, AWESOME 64 setup!!!  Best of luck to ya!

---

### Post by K0NY on 2008-10-09
Thanks for all the replies. I'm generally a fan of XP over Vista as well. However, I'm looking to take advantage of the 64 bit hardware I bought, including the 4GB of RAM. Currently, the only way to really maximize performance is with a truly 64bit OS. Leopard and Vista both fall into that category, though Leopard works with RAM a bit better. Since I want to run games though, Windows has to be there, so the one I've chosen is Server 2008 for its hardware optimization.

As for the legal issues of running OS X, I believe I fall within the grey area because I am an IT professional looking to explore some application development within OS X. So my "hackintosh" will serve as a 'homework helper' for testing out the apps we build at the office.

FYI: I'm taking some cues from the quad booting guide found here:
[http://wiki.osx86project.org/wiki/index.php/Quad_booting](http://wiki.osx86project.org/wiki/index.php/Quad_booting)

Since I have virgin drives to play with, I'm going to attempt the triple boot at first. If that doesn't work out so well, then I'll fall back on installing Server 2008 followed by Ubuntu.

---

### Post by Flynn555 on 2008-10-09
i have vista on my notebook and its no fun :(

---

