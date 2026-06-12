---
title: "New to linux, got a problem already."
date: 2009-07-20
forum: Hardware
---

### Post by gnomerocks on 2009-07-20
I am dual booting windows and Ubuntu 9.04, and for the most part i am loving linux. But, i seem to have run into a problem, and have no idea how to get it resolved.

My problem, is that my laptop, an acer aspire 5100, suddenly and without warning locks up, the screen goes to either a random solid color, or sometimes weird random patterns that look like areas of "tv static", and areas of black mingled together. I can only guess my video card, a ati radeon xpress 1100m, is freezing up inside linux. In windows it works fine, and i can leave it plugged in doing bit torrent downloads for *days*. I am pretty sure its not video card itself going bad since windows has no issues with it.

I found [this]("https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/368049/comments/21"), talking about the same card i have freezing, but dealing with desktop effects being enabled, which i have had turned off all along (they are needless the way i see it).

release 9.04 jaunty, kernel linux 2.6.28-14-generic, gnome 2.26.1

system:
memory: 3.0 GiB (2 sticks 2 GB DDR2 each, factory matched pair)
processor 0: AMD Turion 64 X2 Mobile Technology TL-50
processor 1: AMD Turion 64 X2 Mobile Technology TL-50

phoenix bios bios 3.13
Ubuntu is running on a primary partition, ext3, 2 GiB swap area primary partition.

Any help here would be great. It stinks that i can hardly use linux becuase of fear of locking up and loosing all my progress. Until i get this resolved, it is back to \/\/|/\/|)()\/\/$ i go.:(

EDIT: I was wrong, the link a gave is for a different card, so ignore that. Oops.

---

### Post by quixote on 2009-07-21
Are you running 64-bit Jaunty?  (Also, minor point, you have 4GB system memory, not 3, right?)

What happens when you reboot?  Do you get filesystem errors that need correcting before the boot proceeds, or is everything normal?

Is there any pattern to when the lock up happens?  Eg: you tried to stream video, or flash, or you had Firefox open with a zillion tabs, or playing a game, or any other pattern at all?

---

### Post by cooper77z on 2009-07-21
I don't know, but since I have been running ubuntu os's when my computer works overly hard my cd player in the clock radio skips a beat. No kidding.

---

### Post by gnomerocks on 2009-07-22
> **quixote said:**
> Are you running 64-bit Jaunty?  (Also, minor point, you have 4GB system memory, not 3, right?)

What happens when you reboot?  Do you get filesystem errors that need correcting before the boot proceeds, or is everything normal?

Is there any pattern to when the lock up happens?  Eg: you tried to stream video, or flash, or you had Firefox open with a zillion tabs, or playing a game, or any other pattern at all?
No, its 32 bit. No errors to file system, at least i do not think so. I just hold in the power button, and press it again, and in a few seconds i'm back at my desktop. Any pattern? huh, well i was running transmission bit torrent a couple times when it happened, but it has also happened almost as soon as i get a mouse cursor on the screen, before the desktop loads all the way. Yes i do use at least 5-8 tabs in firefox most the time, but can not see why this would crash my system...

---

### Post by quixote on 2009-07-22
The reason for all the questions is that there can be about a gazillion reasons for lockup: overloaded memory (not likely in your case with 3 or 4GB), memory leaks (something Firefox used to be famous for, especially with lots of open tabs, or when playing flash, or whatever, but recent versions (3 and higher) are much better about it), graphics card problems, the [jaunty 64-bit bug]("http://ubuntuforums.org/showthread.php?t=1145967") (not in your case since you're running 32-bit).

Since it can happen even before the desktop loads, it could well be something to do with the graphics card and the driver xorg.conf is trying to use.  I'm out of my depth on that, but maybe somebody else can suggest ways to diagnose / troubleshoot / or ask a more precise question.

One thing I did want to say is that when you have to shut down by pushing the power button (aka "hard reset") the system can't do it's normal shutdown housekeeping and garbage is left lying around.  You want, if at all possible, to do a normal shutdown the next time it boots up well enough to give you a chance.  Then, after you push the "on" button, if it wants to do a hard disk check, say yes.  And if it wants to fix errors, likewise.

---

### Post by gnomerocks on 2009-07-22
No it has never wanted to do a disk check, it always boots back up fine, until it decides to freeze again.

one thing i forgot to mention in my first post is that it sometimes does this on startup, just as soon as the mouse cursor is visible and the desktop is still loading. Other times i can use linux for upwards of 6 hours no problem. As far as what i am doing when it happens, usually transmission downloads, or browsing in firefox. I keep about 5-8 tabs open all the time. Cpu usage and memory usage are around 20-25% cpu, and 8-10% memory during these "download parties".

---

### Post by ecmatter on 2009-07-22
Check System > Administration > Hardware Drivers

I've had problems like you describe when the proprietary graphics driver is enabled (in my case, ATI Accelerated Graphics Driver)

If you have a graphics driver listed and enabled, disable it and see if that helps.

---

### Post by cooper77z on 2009-07-22
The problem might not be ubuntu. About 15 years ago I had a friend who was into computers and I asked him if viruses could actually infect RAM and Processors. He said, "Yes" But he may have been mistaken. How do you feel about this issue and could a previoius virus be infecting his RAM or Processor, or other on board hardware?

Maybe, just defective hardware??? Maybe try the same install on a clean machine?

---

### Post by gnomerocks on 2009-07-22
ecmatter, i did that just now, and the only listed is Alternate Atheros "madwifi" driver, not activated. There is no driver listed for video card. I want to say though that if i go to desktop, right click > Change Desktop Background > (visual effects tab), and turn on effects, they work. It looks my card does not need any drivers? Or is there any reason why it really _would_ be using a driver, but not showing up in my hardware drivers list? At any rate, i have turned off effects again, seems silly to waste cpu on that when its better used other places.

---

### Post by gnomerocks on 2009-07-22
you mean like root kits? I have heard of those, but never (thankfully) had one. But have had my share of other malware in windows, and thats with avant, ccleaner, hijack this!, & sygate personal firewall. Can anyone recommend a free root kit detector/remover, just to be on the safe(r) side of things?

---

### Post by cooper77z on 2009-07-22
I have had problems with madwifi, it says the install is deprecating my system in the terminal, so I don't use it. What does depricating mean, in ubuntu terminal speak? Maybe madwifi is to blame for the prblemos? Is your system deprecated?

---

### Post by ecmatter on 2009-07-22
> **gnomerocks said:**
> ecmatter, i did that just now, and the only listed is Alternate Atheros "madwifi" driver, not activated. There is no driver listed for video card. I want to say though that if i go to desktop, right click > Change Desktop Background > (visual effects tab), and turn on effects, they work. It looks my card does not need any drivers? Or is there any reason why it really _would_ be using a driver, but not showing up in my hardware drivers list? At any rate, i have turned off effects again, seems silly to waste cpu on that when its better used other places.

Those are proprietary drivers listed in 'Hardware Drivers'.  If you don't have one listed, that means you're using the open-source driver supplied by Ubuntu.

.

---

### Post by cooper77z on 2009-07-22
Maybe you have some windows malware limiting linux' use of video card? If you stay on windows and this is actually the case, you will continue to function with the virus. Just guessing.

---

### Post by quixote on 2009-07-24
Is the virus theory plausible?  Even one that managed to reside in firmware would have to interact with the OS to do anything.  And if it's a "foreign" OS to the Windows virus, all it can do is sit there.  What am I missing?

I guess all we have so far is that your ATI card and ubuntu aren't on very good terms.  I'm pretty sure that to fix that you have to get deep into the weeds, but there are some reasonable-looking step by step instructions starting here: [http://ubuntuforums.org/showthread.php?t=592805&highlight=ATI](http://ubuntuforums.org/showthread.php?t=592805&highlight=ATI)

I found that via this post: [http://ubuntuforums.org/showpost.php?p=3665225&postcount=8](http://ubuntuforums.org/showpost.php?p=3665225&postcount=8), and earlier in the thread the suggestion is to use "fglrxinfo" to see whether your default driver is correctly installed.  Fglrxinfo itself has to be installed first, so none of this is a one-command solution, but the whole tedious process might well get you there.  At least, we can hope!  :?

Given that you can't get graphics drivers to work reliably, the commands should probably best be (carefully!) entered in recovery mode (select "root with netowrking").  Since you're already root, there's no need for "sudo" in front of commands.

---

### Post by gnomerocks on 2009-07-25
I have done fglrxinfo in a terminal, which has said that it can be installed via 'apt-get install xorg-driver-fglrx'. I did that, and then re-ran fglrxinfo, and it has told me: 
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4

I suppose the next thing i should do is follow those guides, but to be honest, i am lost when reading those, and they do not even seem to be using my version ubuntu, or even the same type of card. Instead, i will simply wait until the next version of ubuntu is released and try that. In the mean time, i might go check out ubuntu 8.10 and 8.04, just to see if those play nice or not. And, if after trying 8.10, 8.04, and 9.10 (when it gets here), if i still can not get things working right, i will simply have no choice other then to simply continue using windows, save up some money, and buy a pc with ubuntu on it from the factory...

---

### Post by Jimk33 on 2009-07-25
Hello,
 
I am also having problems with lock ups of Jaunty 9.04. This is my first use of any Linux distro, and first installed it 2 days ago. My system is an AMD 64X2 4200, with 2gb of ram, an nVidia 7300 graphics card. Hard drives are an 80gb IDE, a 500gb SATA, and a 250gb SATA. I built the system myself 2 to 3 years ago, and have generally had no problems. I recently did a clean install of Windows just to clean out junk from the registry, which I generally do about twice a year, and decided to try Linux.
 
I checked the download hash, confirmed that the cd I burned was okay, and just followed the instructions for installing Jaunty 9.04. I've tried both the 32 bit and 64 bit versions, and tried installing on SATA and IDE drives, a stand-alone clean install of Ubuntu, and as a dual boot with Windows. I even tried swaping out hard drives to see if the problem was related to a hard drive issue. I have lock up problems with every configuration.
 
I really can't give much information about what's going on when the lock up occurs, because it usually happens within about 15 to 30 minutes after I boot in to Ubuntu. It has happened while browsing in Firefox, and when I was trying to change background setting, so it appears random. I doubt that the CPU is overloaded, because I've never had an opportunity to actually start any applications. As others have noted, the computer is completely unresponsive, so there's no opportunity for an orderly shutdown, and I do not get a message about doing a disk check on reboot.
 
My experience with computers dates back to an Atari 800, and an Intel 386, and built two water cooled systems, so I like to think I'm pretty knowledgeable about computer hardware and Windows, but am completely new to Ubuntu or any Linux distro, so some handholding is probably going to be necessary at least as to Linux.
 
I've reviewed the other comments on this issue, and tried those recommendations, but they don't seem to help. As I write, it occurs to me that I am not sure whether the problems occur before installation of the new nVidia graphics drivers that Ubuntu recommends. I'll try reinstalling Jaunty 9.04, and postpone updating graphics drivers to see if that has any effect. It says the driver is needed for 3d graphics, which I really would like to include. 
 
Any thoughts would be greatly appreciated.
 
Thanks for any help,
Jim

---

### Post by oldsoundguy on 2009-07-25
no need for malware removers in Linux.  No such thing as a "carry over" type virus when you switched to Linux. (you can still have a Windows issue if you are running a dual boot or a virtual or running stuff in Wine .. but your scanner(s) for that need to reside WITH the programs .. since they are .exe files in the first place and will only run there.)
You problem sounds like it may be either in the MEMORY CHIP (one of them) or in the controller chip (which is is ON BOARD)

A good series of stress tests using a (free) self booting disk such as Hirren's Boot CD or The Ultimate Boot Disk can tell you a  whole LOT about the condition of the hardware on your computer.  Not ALL problems can be blamed on the software.

---

### Post by quixote on 2009-07-25
gnomerocks: *follow those guides, but to be honest, i am lost when reading those*  Yeah.  I know just how you feel.  :)

Oldsoundguy's suggestions are very good.  (Why didn't I think of that?)  One simple way of testing memory is to just run the memtest option on bootup.  It can miss things, but if it doesn't, you have an answer.  Now, given that you don't have the problems under Windows, and do under Linux, I personally wouldn't think "hardware" but Linux does treat chips a bit differently, and sometimes detects faults where Windows doesn't.  That makes for a more graceful failure sometimes, since you have more warning, but it's still no fun.

Btw, there are extensive compatibility lists. You don't have to buy pre-installed unless you want to. :D  I can't find Ubuntu's current list, but [this page]("https://help.ubuntu.com/9.04/installation-guide/i386/hardware-supported.html") has some information, and also links to [Linux on Laptops]("http://www.linux-laptop.net/") which has more models listed than you want to know.

---

### Post by gnomerocks on 2009-07-27
> **gnomerocks said:**
> I have done fglrxinfo in a terminal, which has said that it can be installed via 'apt-get install xorg-driver-fglrx'. I did that, and then re-ran fglrxinfo, and it has told me: 
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4

I suppose the next thing i should do is follow those guides, but to be honest, i am lost when reading those, and they do not even seem to be using my version ubuntu, or even the same type of card. Instead, i will simply wait until the next version of ubuntu is released and try that. In the mean time, i might go check out ubuntu 8.10 and 8.04, just to see if those play nice or not. And, if after trying 8.10, 8.04, and 9.10 (when it gets here), if i still can not get things working right, i will simply have no choice other then to simply continue using windows, save up some money, and buy a pc with ubuntu on it from the factory...
The reason i have not been here on the forum lately is that after doing that, i rebooted, and could not get back to the desktop, **everytime, **I tried _10_ _times_.... So, i went back to windows, and download ubuntu 8.10
So far everything is fine, not one lock up, and been running on it for 27 hours straight now. Under restricted drivers, there was already a listing for ATI/AMD propietary FGLRX graphics driver. _This *never appeared for me*_ in 9.04, even after installing it from the terminal (see above). My system is working great, and now i am just left sitting here scratching my head why i had such a bad time with 9.04, and hoping andpraying that 9.10 will be a little nicer to me when it is released.

---

### Post by quixote on 2009-07-27
Glad to hear you got intrepid running well again!  Too much of an adventure.  If I were you, I'd look to see whether a bug report has been filed on this. [https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)  After you start, eg just type "fglrx" into the Summary line, there's an opportunity to search for similar bugs. (Scan the dates, and look for recent reports.)  You may need to have an account to get to that screen.  If so, register.  They need to hear from users!

If none of the existing bugs sound similar, file a  bug report.  As I say, they need to hear about these problems!

---

### Post by rgb1701 on 2009-07-27
To rule out the memory chips, you should run memtest+ for 72 hrs and see if you get memory errors.

The Ubuntu CD should have a Memory Test pick at bootup, whiich launches memtest+.  If not, download the memtest+ boot cd iso

[http://www.memtest.org/#downiso](http://www.memtest.org/#downiso)

burn and reboot

I've had cases where Linux finds bad memory and Windows does not- it appears Windows is too dumb and just keeps on chugging with bad memory ;)

It could also be an overheating GPU.  The Linux ATI driver could be working the GPU harder than windows, which is why it could overheat in one OS but not the other (while not gaming).

Try a video card stress test in Windows and see if it locks up the machine, like a graphics heavy game.

---

### Post by cooper77z on 2009-07-27
Great! I am glad you solved your problem. I am running 2 monitors on a laptop in Hardy and once in a while the laptop monitor gets the colors mixed up, but I can fix it by disabling and then re enabling the second monitor. :) Ubuntu just has quirky stuff, I guess we will have to accept it.

---

