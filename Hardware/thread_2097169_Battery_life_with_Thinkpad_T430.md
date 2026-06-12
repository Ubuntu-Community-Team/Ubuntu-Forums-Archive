---
title: "Battery life with Thinkpad T430"
date: 2012-12-22
forum: Hardware
---

### Post by pschyska on 2012-12-22
Hey Forums,

I was wondering if anyone has experiences with the current T430 Thinkpads and Ubuntu 12.10 or 12.4.
Background: I just got a X1 Carbon and was so disappointed by battery life - couldn't get idle power drain down below 12w when idling with reduced screen brightness, no radio and ubuntu 2d and after applying the common tweaks laptop-mode-tools, powertop GOOD things, and i915 kernel params stuff.
This machine wouldn't last longer than 2-2,5 hours for my usage (web development).
Long story short: I haven't given up Thinkpads alltogether and was looking at the larger devices. I like their keyboards, trackpoints and durability.
Does anyone own a T430 and get good batery life with it? Please write your processor model, applied tweaks and powertop usage when idling.

Thank you very much,
Paul

P.S.: Does anyone know if there is noticable differences in power consumption between the Ivy-Bridge i5s and i7s? I.e. i5-3210M, i5-3320M, i5-3360M, i7-3520M. Would I get significantly different battery life off them in day-to-day usage? I guess the faster processors draw more power at load, but they are also finished faster. So I supposed it comes down to idle power usage

---

### Post by offgridguy on 2012-12-22
I know this doesn't answer your question but i have found with my thinkpad L512
i get less Batt. life with12.04 than with windows 7.
2 to 2 1/2 hours would be maximum for me.
    I have read other threads that suggest the same thing with other makes of
laptops as well.  I like ubuntu and continue to use it, but it is not easy on resources.

---

### Post by pschyska on 2012-12-22
Yes, that seems to be a common problem.

The T430 with 9-cell appears to be the notebook in my profile which has the highest battery life (94wh) though. If that's not enough you can even add another 94wh slice battery ;)

I'm kinda spoiled by the macbook pro's ability to run you through a working day on a single charge

---

### Post by offgridguy on 2012-12-22
> **pschyska said:**
> 

I'm kinda spoiled by the macbook pro's ability to run you through a working day on a single charge
Wow, i'm impressed, i had no idea that kind of battery life was available with a laptop.
    Do you know if the same would hold true for the macbook air ?
edit; I noticed the P.S. of your original post, i am not sure if a more powerful processer
would use significantly more battery. My understanding is that the monitor is the single
largest user and depending on the amount of graphics you are using will draw proportionatly
more power.
    Personally i don't like using a dim screen even though it saves power, i also don't
like to slow down the performance even though that saves power as well.

---

### Post by pschyska on 2012-12-22
I feel bad about getting someone attracted to apple devices in my first thread on this forums :-D
I've never used a MBA but I heard from friends and colleagues that the battery life is actually very impressive for a device this slim.
I.e.: [http://osxdaily.com/2012/06/26/battery-life-on-macbook-air-2012-is-better-than-advertised/](http://osxdaily.com/2012/06/26/battery-life-on-macbook-air-2012-is-better-than-advertised/)

I'm afraid that this doesn't hold true when using ubuntu though :-( When I installed Ubuntu on my machine the battery life dropped in half at least.
I know the current Macs are very similar to PCs, but I can imagine there are some differences in the hardware still, and I guess the available drivers are not very good. When booting Windows on Macs, the battery life is allegedly not great either.
The good battery life might be an effect of Apple controlling both hardware and software. I guess that's why the most PCs shipped with Windows have a worse battery life in Linux.

OT: I'm looking at the Dell Latitude E6430. It's damn ugly, heavy but gets good reviews for battery life and keyboard, which are my main priorities.

---

### Post by tgalati4 on 2012-12-22
I have an older thinkpad (T43p) and I compiled my own kernel with voltage tweaks enabled.  I use PHCtool to undervolt and thinkpad fan control to lower the fan speeds as well as dynamic clocking the ATI video card.  I still only get 2 hours on a 6-cell battery.  Watt-savings when from 22-24 watts to 17-18 watts.  At least now the battery life is on par with WinXP Pro.  You can buy a battery that fits in the DVD bay.  It roughly doubles battery life.  So now you are at 4 hours.

---

### Post by offgridguy on 2012-12-22
I have been looking at macs for some time now, this battery life factor for me is a 
huge selling point.
   As my username suggests, we live entirely off-grid, powering our home entirely
on solar power.  At this time of year power consumption is not a small issue.
    I could always curtail my computer use.:(:(

The Dell sounds good too.

edit: actually one reason i am interested in the MBA is another member in the forum thought the macbook pro was overkill, simply
more computer than needed, and he is a far more advanced user than i.

---

### Post by offgridguy on 2012-12-22
tgalati4, this is new info to me, thanks.

---

### Post by pschyska on 2012-12-22
tgalati4 thanks for your answer. For the current models Ultrabay batteries are only available for T430s, and even with this the power is lower than then T430 with 9cell (70 Wh vs 90 Wh or so).
The nine-cell will make then T430 bulkier than it already is though. Also, all of the T4x0 models as well as the X1C suffer from pretty bad display quality problems. I could notice a flicker in gray areas and a screen door effect on my X1C, and the T4x0 screens are said to be worse. I could live with mediocore screen, but not for /that/ pricetag :-)
Just ordered the Dell, but am prepared to send it back if it proves to be a failure too. So if you have other suggestions :-)
I'll report back once it arrives!

---

### Post by pschyska on 2012-12-22
> **offgridguy said:**
> 
   As my username suggests, we live entirely off-grid, powering our home entirely on solar power.
edit: actually one reason i am interested in the MBA is another member in the forum thought the macbook pro was overkill, simply
more computer than needed, and he is a far more advanced user than i.

Heh, that's quite an interesting perspective on power consumption :-)
I don't understand what he meant by more computer needed, it's a good machine, but I don't dig the keyboard, the looks and also not the OS. As I said it doesn't work quite well with Ubuntu. I had trackpad issues and battery life, as I said.

I don't know your usage pattern, so it might be OSX is perfectly good for you. Here in germany you can return every item ordered online within 14 days, so why not give it a try and order one?

---

### Post by offgridguy on 2012-12-23
Hello pschyska; I noticed in your post you mentioned bad display quality issues, myL512 has the same problem, enough reason for me never to buy another lenovo.Regarding the mac and dual boot, apparently that can be a problem, there is some info on that in this thread.  [http://ubuntuforums.org/showthread.php?t=2081105&page=2](http://ubuntuforums.org/showthread.php?t=2081105&page=2)  I did some checking and found there is very little price difference between the macbook pro and the MBA, so i would probably opt for the pro, larger screen for one thing.   If i did dual boot i would use virtual box as suggested in the above thread, another learning curve as i am not familiar with virtual box.:)

Edit; looking at the specs. for the Dell, looks good, i assume you are going for the 9 cell Batt?
Very interested in how you like it,please let me know, Private message okay.

---

### Post by pschyska on 2012-12-25
Sure, I'll let you know. It's coming 31.12. :-)
I ordered it with a 6cell, but I will get an additional 9cell too.
That way I can have my machine a bit lighter, but can take both batteries with me when I travel. The X1C, like most ultrabooks, doesn't allow swapping batteries. (btw, both the MBP and MBA have non-replaceable batteries, so bad :-().oar
I also looked at the 6430s, which is a 13,3" body like the 6330, but has a 14" screen (like X1C). However, there is no HD display avaiable and I think resolution would be too low with 1366x768 on 14". I got the 1600x900 panel for my 6430.
You can find a very nice review on: [http://www.notebookcheck.net/Review-Dell-Latitude-E6430-Notebook.81780.0.html](http://www.notebookcheck.net/Review-Dell-Latitude-E6430-Notebook.81780.0.html) 
Skip the part about the bad display, they also tested the HD panel in the 6330 (linked in test), which sounded quite nice.

On the MBs, I think you should look at the 13" **retina** model. I heard very good things from it. However, in addition to the battery not removable/replaceable by the user, they even soldered the RAM on the board. I hate this trend. So be sure to get enough when you order :-)

---

### Post by tgalati4 on 2012-12-26
Mac's are so difficult to repair, they might as well weld them shut.  I was not aware of the Lenovo display problems, but there has been a trend of lower build quality since IBM sold the Thinkpad line to Lenovo.  And yes, it is the same manufacturer that IBM used to make Thinkpads, but you don't have IBM quality control or design standards.

Mac's work great and generally have good battery life.  Just buy Apple Care and you are good for 3 years.  After that, any repair means throw it in the trash.

---

### Post by pschyska on 2012-12-27
It depends on the type of repair obviously, but yes, some repairs are not worth it because of costs (like mobo, I guess). However, things like replacing battery or SSD shouldn't be too bad. You have to bring it in to an Apple Store or send the machine though. My main problem with the retina and air macs is that you can't get a cheap SSD like for most computers, you can't upgrade the RAM at all (I don't even think it's possibly in an Apple Store), and you can't take a replacement battery for  longer travels with you.
The keyboards are good, though not best-in-class, the screen are good, though glossy. The build quality is stellar. You pay a premium for any accessories.
OSX turns more and more into a jail, i.e. you can't install Software outside of the apple app store by default - configurable, but still: wtf?. If you get an aftermarket SSD, Apple won't send TRIM. They String-match the model name and search for APPLE SSD in it, else they just disable it, for no good technical reason. APPLE SSDs of course cost at least twice the price, just like the standard RAM they use. There is a fix though (nulling the APPLE SSD string in the kernel module, which will match any SSD model name), has to be applied after every OSX update.
Apple tries to force their users more and more to use their products, and their products only. I expect they remove Google sync capabilities from their default mail, calendar and contacts to force users to use iPhones and the iCloud service soon...
As a developer, the OS is not very optimal. There is no real package manager, they change the compiler toolchain virtually every XCode release - Which is a multi-GB download where you get the whole Objective-C, Cocoa, iOS development stack, just to get a working gcc. Well, it used to be gcc, then it was llvm-gcc, no they changed it again to clang. The third-party package managers (homebrew, macports) are constantly trying to keep up and patch up their ports to make it compile again.
The UI also gets more and more redicoulous. A iOS-like Launchpad, which serves no function as you can reach every program with only a few keystrokes through Spotlight. The default view on the Finder (file explorer) is "All my files". Yes, that's the view I have been waiting for, now I can finally see all my ~2 million source files in my home folder in a nice expose; fail.

To sum up - OSX sucks, Linux is a so-so experience on macs (battery life, touchpad quirks), Hardware is made intentionally hard to service, premium price, stellar build quality, touchpad best-in-class in OSX. If you can live with the fact that you have to hack up stuff to make the system work, or you don't use the machine for software development they work reasonably well.

Edit: Looks like I kanged my own thread here lol. Still looking for a great Linux laptop with matte screen and replaceable battery with good life. My Dell E6430 will arrive tomorrow as it seems, I will report back how it's going. I fear the machine will be too bulky for me though... I plan to drive to a shop today to see the Lenovo X230.

The screen is said to be good (matte IPS 12,5"), battery life is OK and lots of options because of replaceable battery (4,6,9 cells available), slice battery available, docking port, very good keyboard, good perf. with 3rd gen i7.
I realized that screen size might be fine as it should be enough to hack in vim while traveling or read technical documentation, and I'll have it attached to a 24" anyways while stationary.

---

### Post by offgridguy on 2012-12-28
Not a real flattering endoresment for apple. Maybe i should rethink this.

---

### Post by pschyska on 2013-01-08
Ha, it's been a while :-) Happy new year everyone.
The Dell is quite nice, but too heavy and big for me. I don't really like the trackpoint - no one beats Lenovo on this it seems. The keyboard and screen are OK, but not great. The power consumption is low and the battery life is long, and the device is mostly silent.

I've finally settled for a X230, as it seemed to be the best compromise in portability and function. They keyboard is great and the trackpoint is great, too. The screen is good (albeit small) - however, as it's an matte IPS panel the quality is good - at least for thinkpad standards. Lenovo appearently has huge problems with their screens up to 14" lateley it seems. They all suffer from screen door effects and bad colors/contrast. I hope they will do something in this area soon. I would have gotten a T430s probably if the screen weren't so bad (it's kind of a gamble as they have 3 suppliers and 1 of them is said to be OK...).

I only tested the machine in store though, my configuration will arrive on Thursday. Will report back :-)

---

### Post by pschyska on 2013-01-12
Hey forums,

I got my X230 finally, and I must say it's almost perfect. The screen is good and I had no driver issues at all with 12.10. I installed TLP for power tweaks and battery life seems to be quite nice with the 6cell (I estimate 4h+). It's beautiful machine, however it died completely on day two of using it. When I plugged in the powr adapter it instantly turned off and won't turn on. I hope it's just bad luck :-)
Will continue my Ubuntu adventure when it's repaired.

---

### Post by tgalati4 on 2013-01-12
Not a ringing endorsement for Lenovo either.

---

### Post by br0adband on 2013-01-12
Not sure that any of this matters but I'll toss the info out there just in case it's useful to someone.

My current hardware is a trusty rock solid Dell Latitude E6400 - I've also got a ThinkPad T60 just for the record, but this is related to the E6400 specifically.

I have it currently running Windows 7 Pro x64 and I have a 6-cell battery, 9-cell battery, and also the "battery slice" available for this model of Latitude (shared with some other models like the E6410, etc). Using a combination of the most current drivers (I check for new updated drivers weekly, just kinda paranoid about it I suppose), undervolting the P8700 CPU (Core 2 Duo @ 2.53 GHz, Penryn class), and bringing the display brightness down to about 50% I can manage the following runtimes (with Wi-Fi enabled/connected):

6-cell alone: ~4 hours
9-cell alone: -7 hours
6-cell + slice = ~11 hours
9-cell + slice = ~15 hours

Now the ~ there means in my testing I was within 15-20 minutes of the stated amounts on either side, and I did spend a few days doing nothing but testing the battery life. My testing basis is load a 720p video clip I have stored on a network server accessed using Wi-Fi (the Intel 5100 Wi-Fi card in the E6400, 11n mode). It's the Avatar movie trailer, taken direct from Blu-ray from the original 1080p .m2ts file, compressed to 1280x720 using HandBrake, h.264 video stream with 2 channel stereo 192Kbps AAC audio, High Profile Level 4.1, average bitrate on playback is 13Mbps) and play it using MPC-HC set to repeat and playing in maximized window mode (not true fullscreen). So not only am I playing an HD video clip but the content itself is being pulled wirelessly so that adds to the power requirements.

The batteries I have are all "new" in the sense that I just recently replaced the original factory ones that came when I got this laptop in mid 2010 from Dell. I picked up brand new never used OEM batteries (meaning the real Dell batteries and not cheap Chinese knockoffs) from an eBay seller that shipped from the US - again, not cheap Chinese knockoff batteries. These are the real deal from Dell, just not sold by Dell directly.

Once the batteries arrived I used BatteryBar (a cool Windows tool) to check the actual wear on each battery individually and each one showed 0% wear - they literally were brand new and had never been used before, *ever* so I guess I lucked out in that respect.

My quest right now is to get Ubuntu 12.04 installed, upgraded, and running as solidly and completely as I can (having issues with hardware video acceleration, just posted another thread about that because it too can dramatically help with battery life in some respects), and of course maximizing the potential battery life as much as I possibly can using tools like powertop and PHC, etc.

I haven't done any testing yet and probably won't until I can resolve the HWA issues (hopefully) but I suspect that by default Ubuntu will suffer in terms of battery life - hence the hope that with tweaks and adjustments of all kinds that I might be able to manage getting within 10% of the times I can and did achieve using Windows 7.

I'd love to get another more current ThinkPad at some point, probably a T410 at most because I simply can't tolerate 16:9 panels at this point (have a 1440x900 in this Dell Latitude E6400). And this is also a CCFL backlight - there were some E6400 units that offered an LED backlight iirc, maybe I might look into that as well.

Anyway, there's some info I figured I'd toss out there. Yes, this is a "beast" when I have the 9-cell + slice active, it adds to the weight of it but, when I think of the near guaranteed 15 hours of battery life with that setup, I could care less about another pound or two I'll end up carrying around. :)

The basic gist of this for me is: buying a brand new machine these days isn't necessarily the best idea for a variety of reasons. Even with the newest generation processors using less power, the SSDs using somewhat less power, LED backlit displays using less power, and so on... I doubt I'm gonna get ~15 hours of continuous usage from anything I can buy right now today for less than $1000 - and it could probably be a lot more if I was actually using it the entire time but the looping video test is the most efficient I suppose).

Just my two cents, with a lot of spare change to boot... :D

---

### Post by offgridguy on 2013-01-12
:)br0adband, thanks for the input here.  I appreciate the effort you went to to test this out
and then itemize it here.

---

### Post by br0adband on 2013-01-12
> **offgridguy said:**
> brOadband, thanks for the input here.  I appreciate the effort you went to to test this out
and then itemize it here.

Just for the record it's a zero (0) not a capital O. ;)

(and no you're not the first...)

But yep, this old workhorse machine is probably the best laptop I've ever owned. I have a Latitude D630 here as well - that boots Windows 8 in 7.2 seconds off a 5400 rpm hard drive, go figure. :P

---

### Post by E@zyVG on 2013-03-11
I have T430s and now running openSUSE 12.2 (3.4.x kernel). Out of box my idle was about 9W-10W (no discrete, i5-3320M) and with Powertop 2.0 suggestions (tunnable=good) it fell to around 8W and with SSD instead of HDD it is close to 7W.

So with standard battery I get about 4.5 hours and with extra UltraBay 3-cell over 7 hours - WiFi On (active surfing), multitasking and screen @60%.

Check the following video - a good one and if needed also make tweaks to laptop-mode config file:
[http://hak5.org/episodes/hak5-1225](http://hak5.org/episodes/hak5-1225)

Hope that helps.

Screenshot with lots of tabs in Firefox:
[IMG]https://lh3.googleusercontent.com/-IGlkUc-M1A0/UTjRhydN0iI/AAAAAAAABtM/l65GSaXPcQQ/s1463/snapshot2.png[/IMG]

---

### Post by dani.behzi2 on 2013-10-24
Please consider that T430 uses an optimus-enabled VGA card. Did you installed bumblebee and try to turn the useless Nvidia card off via bbswitch to see how it affects on the battery life?

---

