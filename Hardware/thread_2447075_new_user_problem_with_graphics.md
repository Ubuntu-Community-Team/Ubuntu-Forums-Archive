---
title: "new user problem with graphics"
date: 2020-07-12
forum: Hardware
---

### Post by aes0 on 2020-07-12
Hi, Yesterday, I installed ubuntu 20. on a 128 gb flash drive and this loads on a windows 7 HP desktop machine. 

But, the graphics are not right, low resolution, moving the mouse to various things leads to things like the date menu not displaying properly, other stuff gets
similarly messed up, which I believe to be a driver issue. The graphics card is:

Nvidia Ge Force 7500LE.

This is my first adventure with Ubuntu so likely many of my troubles are through lack of experience. I have searched and tried remedies from several sites with no success, likely because 
I am very unfamiliar with command lines and also because I do not have a systematic way to proceed and I am getting ideas from older versions 
that may no longer be relevant and this leaves so many questions  that I am not focused towards a solution.

So a few questions: 

Is the usb drive arrangement ok for fixing this issue or does it need to install on the hard drive ?

I can create a terminal window with alt, ctrl... sometimes clear, other times messed up, part sloping at 45 degrees,  command line horizontal and I can type to it. 
Should I try and boot to a terminal window and fix the issue before booting to the GUI?

How can I find out what the correct driver is and how should I download and install it?

Thank you in advance for any help.

---

### Post by kc1di on 2020-07-12
Hi Welcome to Ubuntu,

With Nvidia Graphic card you'll need to do some things to get it to work properly.  1.  you need to attach the ```
nomodeset
``` parameter to the end of the boot line. when you boot.
Like this. 
Follow the instructions [given here.]("https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu")

If and when you install the system you can make that permanent by editing the /etc/default/grub file (do a search for how to online.)  or you can install the correct driver for the Nvidia card by going to 
Additional driver tab of the software and update app.  (note: you would need to be connected via Ethernet cable for that to work)  Good Luck.

---

### Post by CatKiller on 2020-07-12
> **aes0 said:**
> Nvidia Ge Force 7500LE.

That is very old, and is not supported by current Nvidia drivers. The last branch that supported that device was the 304 branch. That was available in 16.04, and was available for 18.04 through the external graphics drivers PPA, but is not available for 20.04. 16.04 is supported until April 2021, and 18.04 is supported until April 2023.

The alternative to using more current hardware or an older release is to use the open source nouveau driver, which comes built in but is significantly less well-developed than the proprietary Nvidia driver, in contrast to those for AMD (which used to have a proprietary driver, but now uses an open source driver) or Intel (which has always only used an open source driver), whose open source drivers perform very well.

---

### Post by aes0 on 2020-07-12
Thanks for the replies. I won't be using the machine for playing games. If possible I would like to use it for simple video edits using open shot or similar, but I don't have enough experience to know if the machine can do this. It seems to be able to use it on windows 7, but I only installed it and checked it would run, doing no editing. If it can't do that I might find it useful for uploading to youtube video files made by iMovie as it has a ethernet connection and this would free up my MacBook rather than have to leave it by the modem for many hours. Another application I thought to use it for was to run a cnc desktop router via Universal Gcode Sender. As I say I don't know if I am asking too much of it and if so please let me know and I will find some other way.

So unless I am completely wasting my time (please say if so) I would like to try with the nouveau driver.

I have followed the links kindly provided by kc1di and after some experimentation, found that I could enter something called boot: I reached this by pressing escape to first get to the menu that allows me to specify the the usb drive as the boot source and then just afterwards pressing and holding the right (not the left) shift key.

However, once in boot: nothing works. If I press e it says:

Loading e... failed: No such file or directory

If I type ls I get the same with ls replacing e

I have found no way out of this place other than pulling out the power cord, cntrl x has no effect, just same error message.

I am likely missing something obvious here, but I all I can find is that grub is a subdirectory of boot and yet where I am just
seems to be limbo, no executable commands, no command way out.

Thank you for your help

---

### Post by CatKiller on 2020-07-12
> **aes0 said:**
> So unless I am completely wasting my time (please say if so) I would like to try with the nouveau driver.
Well, you're using the nouveau driver now.

It wouldn't be my choice. Trying to run brand-new Linux on that hardware, particularly as a new user, is going to be a significant uphill struggle. Sticking with a (still supported) release that gives you access to the proprietary driver, or changing the hardware to something that's supported by the version that you want to use, will give you a much smoother time.

---

### Post by aes0 on 2020-07-12
Thank you!

I looked at the hardware cost of a new graphics card and it doesn't seem economic to discard what I have and go for a new one, especially when a new mini PC can now be had at relatively low cost that would replace the whole thing for a more compact and powerful system.
 
I will try the 18.04 version, no sense trying to do something that would be a uphill struggle and wouldn't be the first choice of an experienced user.

Thank you for your help!

---

### Post by Yellow Pasque on 2020-07-12
> **aes0 said:**
> I will try the 18.04 version

Make sure it is 18.04**.1**
Also, see: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1737750](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-304/+bug/1737750)

---

### Post by aes0 on 2020-07-12
Thank you, I would have been pained by 18.04.

Regards,

---

### Post by mastablasta on 2020-07-13
i guess you have a temporary solution.

however in your case i would stay on windows 7 if you have good GPU support there. just make sure you secure it and lock it down as much as you can (i suggest Comodo+avast combo along with latest Firefox browser with noscript addon). i stayed on XP like that until last year. i would still be there, but software support was dwindling and it took PC 10 minutes to boot. Still old game work really well there, so i dual booted.

for video editing you need strong CPU, but you also need some descent GPU hardware acceleration. as you find out the latest mini pcs and machines offer both at relatively low price.
i don't know what kind of CPU you currently have but getting nvidia GT 1030 or similarly powered AMD card would also take care of the issue.

---

### Post by aes0 on 2020-07-13
The computer was bequeathed to me by a neighbours family after he died. He hardly used it and I don't have much of a feel for how powerful it is and whether it is worth messing with, but thought to give it a try as my preferred option of an iMac or a second MacBook air is expensive although it would be nice to stay in the Apple eco-system. The machine I was given is a HP with
an Intel(R) Pentium(R) D CPU 2.8 GHz, with 3 GB of memory and a 32 bit operating system and has windows 7 Service Pack 1. Looking at eBay a nvidia GT 1030 looks like about £70 which is now a fair chunk of a mini PC with an intel mini including ubuntu 20. available for £149:
 [https://www.ebay.co.uk/itm/Fanless-Intel-W8-Pro-Mini-PC-Linux-Ubuntu-20-04-4GB-RAM-64GB-eMMC-4K-HDMI-WIFI/254646219534?_trkparms=aid%3D111001%26algo%3DREC.SEED%26ao%3D1%26asc%3D20160811114145%26meid%3D7d4f5490906245db8b576511df1b9462%26pid%3D100667%26rk%3D5%26rkt%3D8%26mehot%3Dnone%26sd%3D274306841167%26itm%3D254646219534%26pmt%3D0%26noa%3D1%26pg%3D2334524%26brand%3DIntel&_trksid=p2334524.c100667.m2042](https://www.ebay.co.uk/itm/Fanless-Intel-W8-Pro-Mini-PC-Linux-Ubuntu-20-04-4GB-RAM-64GB-eMMC-4K-HDMI-WIFI/254646219534?_trkparms=aid%3D111001%26algo%3DREC.SEED%26ao%3D1%26asc%3D20160811114145%26meid%3D7d4f5490906245db8b576511df1b9462%26pid%3D100667%26rk%3D5%26rkt%3D8%26mehot%3Dnone%26sd%3D274306841167%26itm%3D254646219534%26pmt%3D0%26noa%3D1%26pg%3D2334524%26brand%3DIntel&_trksid=p2334524.c100667.m2042)

Any comments much appreciated.

Meanwhile I have been trying to install 18.04.1 via a pen drive but have run into trouble:

I have downloaded 18.04.1 and using Rufus 3.11.1678. I set things to create the image on the pen drive and it says:
"The image uses Syslinux 6.03/20171017
Two additional files must be downloaded."
I type y and it creates the directory syslinux-6.03 with sub directory 21071017 in the rufus_files, but then says "Failed to down load file"

Not sure how to proceed to over come this.

Regards,

---

### Post by mastablasta on 2020-07-13
> **aes0 said:**
> The computer was bequeathed to me by a neighbours family after he died. He hardly used it and I don't have much of a feel for how powerful it is and whether it is worth messing with, but thought to give it a try as my preferred option of an iMac or a second MacBook air is expensive although it would be nice to stay in the Apple eco-system. The machine I was given is a HP with
an Intel(R) Pentium(R) D CPU 2.8 GHz, with 3 GB of memory and a 32 bit operating system and has windows 7 Service Pack 1. Looking at eBay a nvidia GT 1030 looks like about £70 which is now a fair chunk of a mini PC with an intel mini including ubuntu 20. available for £149:
 [https://www.ebay.co.uk/itm/Fanless-Intel-W8-Pro-Mini-PC-Linux-Ubuntu-20-04-4GB-RAM-64GB-eMMC-4K-HDMI-WIFI/254646219534?_trkparms=aid%3D111001%26algo%3DREC.SEED%26ao%3D1%26asc%3D20160811114145%26meid%3D7d4f5490906245db8b576511df1b9462%26pid%3D100667%26rk%3D5%26rkt%3D8%26mehot%3Dnone%26sd%3D274306841167%26itm%3D254646219534%26pmt%3D0%26noa%3D1%26pg%3D2334524%26brand%3DIntel&_trksid=p2334524.c100667.m2042](https://www.ebay.co.uk/itm/Fanless-Intel-W8-Pro-Mini-PC-Linux-Ubuntu-20-04-4GB-RAM-64GB-eMMC-4K-HDMI-WIFI/254646219534?_trkparms=aid%3D111001%26algo%3DREC.SEED%26ao%3D1%26asc%3D20160811114145%26meid%3D7d4f5490906245db8b576511df1b9462%26pid%3D100667%26rk%3D5%26rkt%3D8%26mehot%3Dnone%26sd%3D274306841167%26itm%3D254646219534%26pmt%3D0%26noa%3D1%26pg%3D2334524%26brand%3DIntel&_trksid=p2334524.c100667.m2042)

Any comments much appreciated.


you are correct. it might even still have an AGP port and these are hard to get these days. if win7 works reasonably well on it i would stay on it and just secure it. besides you are not planning to do web research on it so it should be safe. Maybe save up for one of the mini PC especially if you need space. the miniPC you linked is not really something you want to edit movies on. they are ideal to watch movies on or other things.

 for video editing you need strong CPU (Ryzen 5 or Core i5) and as much ram as you can (preferably at least 8 GB). for GPU you can use the chip on the CPU. these days they are strong enough for light video editing, but they need ram available. 
intel NUC are ideal as they are small and work well with linux, but they are pricey. There are some Asus with Ryzens, but i don't know how well they handle linux and they are still not cheap. you could also build your own. people over at kodi forums know more about these. as i remember there is a good website that sells all kinds of ITX and other small motherbaords in UK. i can't remember the name, but i remember they had lot of info available.
another option is to get a used small form factor PC and upgrade that with RAM if necessary.

the Pentium D could act as home server with large drives inside to store media. you don't need GUI for that and you can hide it somewhere in the corner. GUI can be over website and for that you don't need strong GPU ( actually you don't need any GPU). the D were not really a good CPU. still in this case the nvidia seems to be the one causing troubles. Radeon (AMD) had descent support for old chips and they already helped developers with drivers before. but support for newer chips was not as good as nvidia before. now they decided to go full opensource so support is quite good for new chips as well.

> 
Meanwhile I have been trying to install 18.04.1 via a pen drive but have run into trouble:

I have downloaded 18.04.1 and using Rufus 3.11.1678. I set things to create the image on the pen drive and it says:
"The image uses Syslinux 6.03/20171017
Two additional files must be downloaded."
I type y and it creates the directory syslinux-6.03 with sub directory 21071017 in the rufus_files, but then says "Failed to down load file"

Not sure how to proceed to over come this.

Regards,

i got that message when using Yumi and Unetbootin. so i used Balena Etcher and it worked well with 18.04 and this year with 20.04: [https://www.balena.io/etcher/](https://www.balena.io/etcher/)
also make sure the downloaded file is a good one.

by the way first PC i put Ubuntu on was also an inherited PC i got 11 years ago. it was old with some kind of unregistered winxp. no one else really wanted it but i saw some potential. after i got frustrated with winXP i added ubuntu on it and started learning. i then upgraded it a bit, but it gave me issues due to motherboard. this year we set it aside and got a new one.

---

### Post by tea for one on 2020-07-13
> **aes0 said:**
>  HP with
an Intel(R) Pentium(R) D CPU 2.8 GHz, with 3 GB of memory and a 32 bit operating system and has windows 7 Service Pack 1. Regards,

Can you determine if the PC can use a 64 bit OS?

[https://support.microsoft.com/en-us/office/determine-whether-your-computer-is-running-a-32-bit-version-or-64-bit-version-of-the-windows-operating-system-aac162a1-0cb3-46f2-888f-2f22897396ce?ui=en-us&rs=en-us&ad=us](https://support.microsoft.com/en-us/office/determine-whether-your-computer-is-running-a-32-bit-version-or-64-bit-version-of-the-windows-operating-system-aac162a1-0cb3-46f2-888f-2f22897396ce?ui=en-us&rs=en-us&ad=us)

---

### Post by aes0 on 2020-07-13
[COLOR=#000000][INDENT]Can you determine if the PC can use a 64 bit OS?

[https://support.microsoft.com/en-us/...rs=en-us&ad=us]("https://support.microsoft.com/en-us/office/determine-whether-your-computer-is-running-a-32-bit-version-or-64-bit-version-of-the-windows-operating-system-aac162a1-0cb3-46f2-888f-2f22897396ce?ui=en-us&rs=en-us&ad=us")

This says 32 bit operating system.
Does this mean I can't run ubuntu 18.4.1?

Regards,[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by tea for one on 2020-07-13
Unfortunately, a 32 bit PC needs a 32 bit Operating system.

I think some of the older flavours of the Ubuntu family have 32 bit  iso downloads but I'm not sure which ones.

Probably Xubuntu and Lubuntu 18.04 versions.

Here is another alternative for an OS based on Ubuntu but not part of the family.

[https://peppermintos.com/guide/downloading/](https://peppermintos.com/guide/downloading/)

---

### Post by Yellow Pasque on 2020-07-13
> **aes0 said:**
> This says 32 bit operating system.
Does this mean I can't run ubuntu 18.4.1?

No. It just determines whether your Windows version is 32-bit or 64-bit. It doesn't tell you whether the hardware is 64-bit capable.

> an Intel(R) Pentium(R) D CPU 2.8 GHz

The CPU is 64-bit capable, but not all corresponding motherboards from that era were. So the question is: What motherboard (or exact model of HP) do you have?

---

### Post by aes0 on 2020-07-13
Using the 32 bit version of Etcher from GitHub I was able to make my 128 Gb usb bootable for the 64 bit version of 18.04.1 and it then ran beautiful, graphics clear and no problems.

I haven't checked the motherboard details but as it runs the 64 bit Ubuntu that checks that question for me.

I have now downloaded the openshot video editor, but not yet tried to edit any video as I have to do some other jobs first, but hope to try later.

Overall I am super impressed with Ubuntu and the support here. I have had a hill climb through ignorance on my part to get to this point but I have learned some stuff and maybe this PC will do me for a while.

Thank you to everyone for the help, I could not have got here without you.

---

### Post by tea for one on 2020-07-13
That's good news - Can you mark the thread as solved?

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by aes0 on 2020-07-13
Well I came back all enthusiastic and then I found that Chrome crashed and this somehow removed oneshot and then when I used dropbox to bring over a small video, direct from my iPhone, only about 8 Megabytes. I found that Ubuntu could not play it saying: "No add on codecs are available for the h.264 (high Profile) decoder format... and then it crashed and the whole system stopped. Earler Thunderbird crashed and caused a system hang up.

It may be all due to the use of the pen drive operating system but it has so distressed me that I am coming to the conclusion that it is not going to do what I want and painful to the wallet as it will be that I will have to go Apple. What I was planning to do I could have completed in 30 minutes with out trying hard on an Apple system, having all my devices accessing iCloud is much more convenient than dropbox and although crashes do occasionally happen on my MacBook, the general experience is excellent.

Sorry things have turned so poorly for my experiment despite all the excellent help I got. Maybe there is something obvious that I am doing wrong that some one can quickly spot but as is I am thinking to abandon this experiment.

Regards,

---

### Post by CatKiller on 2020-07-13
> **aes0 said:**
> What I was planning to do I could have completed in 30 minutes with out trying hard on an Apple system, having all my devices accessing iCloud is much more convenient than dropbox and although crashes do occasionally happen on my MacBook, the general experience is excellent.

Good luck installing macOS on that machine.

---

### Post by Yellow Pasque on 2020-07-13
Why are you running on a pen drive?
Did you even install Nvidia 304 driver? That was the point of using 18.04, correct?

> "No add on codecs are available for the h.264 (high Profile) decoder format...
What program were you trying to use to play it?

---

### Post by aes0 on 2020-07-13
No I would not be putting Mac on this machine. 

If I go the Apple route I will have to either buy an iMac or another MacBook, probably a second hand model as my 2015 MacBook air is plenty good enough for video editing, so I don't need a new machine, but tying up my current MacBook for uploads to YouTube that take hours and having to swap from the video editing to other applications and back again, is not great for my productivity and my ways of working. I would prefer to have one machine for the video stuff and another for more general work, two different places to sit to avoid all the shuffling and moving of stuff as I switch between jobs. As things are I can't use small slots of time effectively and I am trying to be more productive.

I really wanted to use this machine, but my experiments have convinced me that it just is not capable of doing what I need, which is a great pity. I can still use it to drive my cnc milling machine, but otherwise it seems that it is not powerful enough/reliable enough at least with a GUI to do what I want to do and most of the stuff I do is not suited to command line type applications.

I may have more of a play with the Win 7 that I have left on the machine and see if I can use that, although i hate the need to re-boot with windows and I fear the security. I was told that win10 is currently free and looking at the specs needed for 10 this machine can probably run it, so that would be another option. I can handle relative slowness, but the crashes and lockups I have had with Ubuntu have been great sinks of time and then when I struggled through I found it could not open the video files which are just off an iPhone 7+.

Regards,

---

### Post by aes0 on 2020-07-13
[COLOR=#000000]Why are you running on a pen drive?[/COLOR]
[COLOR=#000000]Did you even install Nvidia 304 driver? That was the point of using 18.04, correct?[/COLOR]

[COLOR=#000000]I am running on a pen drive in case I ever wanted to mess with windows 7 and it may be that this is the issue.[/COLOR]

Yes, I installed 18.04.1 and it has no graphics issues at all, just lovely display.

I moved the video file over with dropbox. It couldn't open it on Ubuntu, so I moved it to downloads and then the editor oneshot and both gave the errors I described.

Regards,

---

### Post by mastablasta on 2020-07-14
> **aes0 said:**
>  What I was planning to do I could have completed in 30 minutes with out trying hard on an Apple system, having all my devices accessing iCloud is much more convenient than dropbox and although crashes do occasionally happen on my MacBook, the general experience is excellent.



well buy a computer system with linux preloaded and the experience will be more or less the same.
or use a fully compatible and well supported hardware - again the experience is good. 

i just wrestled with a windows game to get it running on linux. an interesting and amazing option - to run something made for completely different operating system. i wanted to end the struggle and started thinking that maybe i should save some money for windows 10. anyway as i searched the answer for specific errors, i found numerous posts of people complaining these games don't run on windows 10. and the issue was the same. in the end they couldn't make it work on win 10 (it only worked on vista, 7 and 8), but i could make it work on linux. so i again abandoned the idea of installing win10 (at least for now).

---

### Post by aes0 on 2020-07-14
I spent a good amount of time experimenting to see if I could edit video on the machine using windows 7 and the same oneshot editing package. I managed to get a little further on windows 7 than I did on Ubuntu, but it refused to let me create a full hd file of 1920x1080 and the process was very slow and clunky.
My conclusion is that the hardware of the computer I was given isn't powerful enough to do what I want. Almost certainly on a new machine Ubuntu would be fine, but I was hoping to get some life out of the machine I was given, but sadly not.
I will study and save up and get something with better hardware and keep the machine for running my cnc mill.

Thank you to everyone who helped me with my experiment. I didn't get the answer I wanted but I got an answer that sets my mind at rest, showing that I am not being silly going after something better before having verified that what I have can't do the required job.

---

### Post by mastablasta on 2020-07-17
to get the job done in a descent manner you need i5 or Ryzen 5 with as much RAM as you can afford. that's it. the onboard GPU is strong enough nowadays. But if oyu can afford you can also splurge there (e.g. getting a gaming one on sale).

kid bought (i assembled) older Ryzen 7 2xxx series for nearly the same price as new (well at the time) Ryzen 5 and it flies. i canibalized the old PC of parts that were useful, got some fast ram and got an older generation entry gaming card on sale for half price. all in all it was a reasonably cheap purchase (500EUR+100 EUR for monitor also on sale at half price). i5 have about 10000-14000 points on benchmark (depends on what model), this ryzen 7 has 15700 points. with more cores it is ideal for video editing. well he mostly uses it to play games and watch youtube.

---

