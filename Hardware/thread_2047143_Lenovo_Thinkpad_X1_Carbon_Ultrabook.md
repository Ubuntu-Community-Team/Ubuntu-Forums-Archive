---
title: "Lenovo Thinkpad X1 Carbon Ultrabook"
date: 2012-08-24
forum: Hardware
---

### Post by dpjg on 2012-08-24
I wonder whether there is anybody, who tried to run Ubuntu or any other linux distribution on the new Lenovo Thinkpad X1 Carbon Ultrabook yet? I am seriously considering to buy it, and was wondering whether it works flawlessly.

Thx!

dpjg

[B]
[UPDATE] [/B]For impatient fellows not wanting to read the whole thread, it seems that th X1 Carbon works flawlessly with Ubuntu: [https://ftbeowulf.wordpress.com/2012/08/30/lenovo-x1-carbon/](https://ftbeowulf.wordpress.com/2012/08/30/lenovo-x1-carbon/)

---

### Post by undoIT on 2012-08-25
I plan on purchasing an X1 Carbon at some point in the near future. I'll report back my findings after I get it.

---

### Post by dpjg on 2012-08-25
Thanks [undoIT]("http://ubuntuforums.org/member.php?u=378934"), I will do the same in case I am quicker than you ;)

---

### Post by loklaan on 2012-08-27
I am considering getting it as well!

But, I prefer not to use Windows... So I'm looking forward to the findings of people getting this sleek machine!

---

### Post by undoIT on 2012-08-28
> **loklaan said:**
> I am considering getting it as well!

But, I prefer not to use Windows... So I'm looking forward to the findings of people getting this sleek machine!

I wish Lenovo and other manufacturers would make the option available to have systems shipped WITHOUT Windows and provide feedback functionality during the ordering process where customers could specify which OS they intend to install once they receive their new system. I do not want to pay for a Windows license. I wouldn't use Windows if you paid me. I already have a developer copy of XP which is fine for testing my websites in POS Internet Explorer 7. And, I don't want to support artificially inflating Windows market share numbers.

I do have relationships with most of the major manufacturers. I think I'll reach out to my contacts and ask them to pass along this suggestion now that I have ranted :)

---

### Post by loklaan on 2012-08-28
> **undoIT said:**
> I do have relationships with most of the major manufacturers. I think I'll reach out to my contacts and ask them to pass along this suggestion now that I have ranted :)

If that works out or you only manage to forgo the 'Windows Tax' on a new machine, I would be *well* interested in your contacts. :) Goodluck.

I am still very eager to hear Ubuntu user experiences on the X1 Carbon!

---

### Post by norfair on 2012-08-28
I ordered the X1 Carbon a couple of weeks ago, and am just awaiting delivery - there's been a delay of some kind due to hardware shortages/demand it seems. 

I plan on loading Ubuntu 12.04 as soon as I get it; before I even see that nasty bloated Lenovo/Windows nonsense. I bought Ubuntu stickers direct from Canonical and received some free ones from System76. I'm ready!!

So, here's hoping I get the laptop very soon, and that Ubuntu loads and runs flawlessly. It should, as it is certified to work well on the X1 (sans carbon). All of the innards seem Ubuntu friendly, too, not that that means anything of course.

It looks like an amazing machine with just about everything I've been waiting for - anti-glare screen, lightweight, backlit keyboard, glass touchpad, non-Apple look, legendary Thinkpad keyboard, track point (hopefully it's Ubuntu friendly by default), and good battery life. What more could one want? Well, a lower price, a brighter, IPS screen, and Ubuntu preloaded by default, I guess. ;)

If I don't get irritated with Lenovo over the delay and cancel (or rather, should the delay carry on further and they handle it poorly), I'll happily be back here to report my success/failure.

---

### Post by undoIT on 2012-08-28
> **norfair said:**
> I ordered the X1 Carbon a couple of weeks ago, and am just awaiting delivery - there's been a delay of some kind due to hardware shortages/demand it seems. 

I plan on loading Ubuntu 12.04 as soon as I get it; before I even see that nasty bloated Lenovo/Windows nonsense. I bought Ubuntu stickers direct from Canonical and received some free ones from System76. I'm ready!!

So, here's hoping I get the laptop very soon, and that Ubuntu loads and runs flawlessly...

I own a T410s and a T420s. The Linux compatibility on these machines and other Lenovo systems I have installed on has been fantastic. I am expecting a smooth experience with the X1 Carbon when I get it.

---

### Post by loklaan on 2012-08-29
> **norfair said:**
> So, here's hoping I get the laptop very soon, and that Ubuntu loads and runs flawlessly. It should, as it is certified to work well on the X1 (sans carbon). All of the innards seem Ubuntu friendly, too, not that that means anything of course.

The touchpad in the X1 Carbon has made huge advancements. I hope these can be experienced under Linux! Thats about the only thing that might suffer, not counting combo conflicts.

---

### Post by undoIT on 2012-08-29
> **loklaan said:**
> The touchpad in the X1 Carbon has made huge advancements. I hope these can be experienced under Linux! Thats about the only thing that might suffer, not counting combo conflicts.

Do you know if it is a Synaptic pad? The touchpad on my Macbook Air works pretty well, although not all the gestures are supported and touchegg hasn't been updated for 12.04. When touchegg is working, that touchpad is excellent. I have had troubles tyring to configure mtrack.

---

### Post by dpjg on 2012-08-31
Good news! Seems to work:

[https://ftbeowulf.wordpress.com/2012/08/30/lenovo-x1-carbon/](https://ftbeowulf.wordpress.com/2012/08/30/lenovo-x1-carbon/)

---

### Post by ginsu0 on 2012-09-11
I received my X1 Carbon a few days ago and installed 12.04 right away. Most of the hardware works out-of-the-box, but I'm finding a few problems.

1. The most annoying problem is with the iwlwifi driver for the Centrino 6205, as there is no Ethernet port on this laptop, and I did not order the USB-Ethernet adapter:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623)

The driver suffers from known issues involving unreliable connections. These are apparently mitigated by disabling 802.11n, and this seems to be the default behaviour, because I can't connect to any networks above 802.11g speeds (even after loading the kernel module with disable_11n=0). To make matters worse, what is reported as 54 Mbits/s I measured to be closer to 13 Mbits/s.

Connections also sometimes become unresponsive (with full signal bars), requiring me to manually reconnect to the wireless network.

2. The system is occasionally unresponsive when coming out of suspend. More often than that, the wifi refuses to connect to any network after waking up. Either of these require a reboot.

3. It seems that the fingerprint reader (Upek 147e:2020) does not yet have a linux driver:

[http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=235&Posts=0](http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=235&Posts=0)

4. The tp_smapi kernel module that exposes some hardware/firmware features of Thinkpads does not yet support this laptop. However, I did have luck setting battery charge limits using the tpacpi-bat tool, which is part of tpbattstat-applet. The applet only runs under Gnome, but I used the included command-line tool to do this.

**UPDATE:**
After connecting to other routers, I see the wifi speed is going above 54 Mbit/s. So this bug probably has something to do with the combination of the Centrino 6205 and my home router. When I get some time I'll probably try putting DD-WRT on the router to see if that resolves it. 

Also, it seems that the occasional freezing after suspend is a known touchpad problem affecting multiple devices. Today I was able to launch a console to reboot the machine.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/976198](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/976198)

---

### Post by afulldeck on 2012-09-11
How's the heat off this box if you run video all day? Does it stay cool like the T430 or get hot like T400?

---

### Post by ginsu0 on 2012-09-11
> **afulldeck said:**
> How's the heat off this box if you run video all day? Does it stay cool like the T430 or get hot like T400?

Temperature stays in the low 60s playing high-bitrate 1080p video with VLC. That's with VA-API enabled, and CPU utilization (1 core) between 60-90% on the i5-3427U.

The bottom and left side get warm, but the fan ramps up only a few hundred RPM more. Overall, quite silent no matter what I throw at it.

---

### Post by afulldeck on 2012-09-11
> **ginsu0 said:**
> Temperature stays in the low 60s playing high-bitrate 1080p video with VLC. That's with VA-API enabled, and CPU utilization (1 core) between 60-90% on the i5-3427U.
 
The bottom and left side get warm, but the fan ramps up only a few hundred RPM more. Overall, quite silent no matter what I throw at it.
 
Okay, now I'm salivating. Need to get me a cool running Carbon ultrabook.......

---

### Post by ginsu0 on 2012-09-25
> **ginsu0 said:**
> I received my X1 Carbon a few days ago and installed 12.04 right away. Most of the hardware works out-of-the-box, but I'm finding a few problems.

1. The most annoying problem is with the iwlwifi driver for the Centrino 6205, as there is no Ethernet port on this laptop, and I did not order the USB-Ethernet adapter:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1011623)

The driver suffers from known issues involving unreliable connections. These are apparently mitigated by disabling 802.11n, and this seems to be the default behaviour, because I can't connect to any networks above 802.11g speeds (even after loading the kernel module with disable_11n=0). To make matters worse, what is reported as 54 Mbits/s I measured to be closer to 13 Mbits/s.

Connections also sometimes become unresponsive (with full signal bars), requiring me to manually reconnect to the wireless network.

2. The system is occasionally unresponsive when coming out of suspend. More often than that, the wifi refuses to connect to any network after waking up. Either of these require a reboot.

3. It seems that the fingerprint reader (Upek 147e:2020) does not yet have a linux driver:

[http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=235&Posts=0](http://darkblue.homeip.net/fingerprint/Forum/topic.php?TopicId=235&Posts=0)

4. The tp_smapi kernel module that exposes some hardware/firmware features of Thinkpads does not yet support this laptop. However, I did have luck setting battery charge limits using the tpacpi-bat tool, which is part of tpbattstat-applet. The applet only runs under Gnome, but I used the included command-line tool to do this.

**UPDATE:**
After connecting to other routers, I see the wifi speed is going above 54 Mbit/s. So this bug probably has something to do with the combination of the Centrino 6205 and my home router. When I get some time I'll probably try putting DD-WRT on the router to see if that resolves it. 

Also, it seems that the occasional freezing after suspend is a known touchpad problem affecting multiple devices. Today I was able to launch a console to reboot the machine.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/976198](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/976198)

I figured out that the wireless issues were related to the Centrino card refusing to connect above 54mbits/s on the 2.4 GHz band, even with 802.11n-only routers. I bridged a second router that works on 5 GHz, and have been getting 300mbits/s ever since. So it seems that the Intel drivers are working fine. I've read some speculation that it comes down to Intel's strict adherence to the final 802.11n spec.

---

### Post by FrancoNero on 2012-10-10
SO HERE IS A FIRST IMPRESSION REVIEW - DUE TO LACK OF SUCH. ENJOY


Second day running 12.10 on an X1 Carbon.

Installation: Beta 2 wouldnt install, so I tried with a daily build. More success. All hardware detected without a problem. Installation was done in under 15min. Please not that due to UEFI (I read that somewhere) u need to use the 64bit Ubuntu (no idea why anyone still uses 32bit).

Booting: Mine has 8gig RAM, I swear it boots in under 5 seconds!

Display: I dont like the colors that much, after having been with a shiny Macbook Air for over a year. Maybe it can be adjusted in Gnome somewhere. The distance between the pixels is noticeable, as reported in many reviews. That is a shame, would be a great Display otherwise.

Touchpad: Nice feeling, gestures supported. Only problem that it is one noisy and sloppily attached part. That severly dents the overall impression and it is an annoying sound. But hey, I only use the Nipple anyhow...

Power supply: The AC adapter is enormous. No idea whose idea that was. Basically it is as big as those that came with ThinkPads 10 years ago...

Fan/Noise: I find it very loud, there is a constant high pitch humming and fan goes up regularly without much reason. I think this could be tuned. Any ideas? What libraries do I have to install? Thinkfan?

Heat: laptop gets quite warm in the peripheral areas. But then again, so does the MacBook Air (but that one gets warm around the Escape Key).

Vents: The ASUS and Apple Machines are the only innovative ones out there, all others including this one have a grill at the bottom and one on the left. I already see the machine dying in a couple months due to dust getting in and it being asphyxated because it use it like LAPtop.... poor engineering

WiFi: No problems

Bluetooth: Detected. But I havent tested it.

Battery: The First test today (first time on battery since purchase) I got about 4h, I hope this gets better. I am open to tuning tips!

Keyboard: VERY nice, but I find it a bit loud and heavy. Just have to get used to it after the butter writing machine that was the macbook air. Some Keys are very nicely placed and some thought went into it. The keyboard can be lit, albeit not the auxiliary buttons such as volume control.

Sound: Quite nice, even for music. Surely nothing audiophile.

Headset/Mike: Not tested yet (will update this review)

Overall: A very light, thin, very robust, matte chassis, matte display laptop with a 14 inch screen in a 13 inch machine. Highly Ubuntu compatible Ultrabook. A few very clear engineering flaws (display, touchpad, AC adapter, vent/fans) that will forever prevent this from being a true MacBook Air killer, but probably among the best Thinkpads yet.

Questions?

And most of all, do you have tips for me (fan control, battery optimization)?

---

### Post by karlstad on 2012-10-10
> **FrancoNero said:**
> 
Fan/Noise: I find it very loud, there is a constant high pitch humming and fan goes up regularly without much reason. I think this could be tuned. Any ideas? What libraries do I have to install? Thinkfan?


You could try installing [Jupiter]("http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html") or [indicator-cpufreq]("https://launchpad.net/~artfwo/+archive/ppa"), which makes it possible to manually adjust the CPU frequency and how it's dynamically adjusted.

> **FrancoNero said:**
> 
WiFi: No problems


How about 802.11n networks? Does that work okay? And do you have a mobile broadband card built-in? If you do, are you able to test it?

> **FrancoNero said:**
> 
Battery: The First test today (first time on battery since purchase) I got about 4h, I hope this gets better. I am open to tuning tips!


Did you adjust the brightness on the screen when you tested this? And the CPU frequency? That normally helps.

---

### Post by FrancoNero on 2012-10-10
Hi

I chose the model without mobile broadband. I have not tested it with an x11n network.

I did adjust the screen brightness slightly, not the CPU frequency.
Which brings me to your first answer: I dont want to manually have to adjust anything. I am familiar with Jupiter and aside from the temperature information I find it a fairly useless piece of software. Also I dont think the CPU is the problem, but the fan. If I am not doing anything, and the fan goes on, I hardly think it is because the CPU is so busy? But I am open to try a few things. However I think Ubuntu's strength is in its out-of-the-box-iness :)

---

### Post by bkfitz on 2012-10-12
My X1 is set to arrive on Monday... based on the previous posts, I'm still trying to decide the following:

- 64bit or 32bit (I got the base model with 4g ram and 256SSD)
- 12.04 or 12.10 ubuntu (CLASSIC mode - can't stand unity or g3)

Especially curious about the WIFI N problems... would rather run 12.04 for the LTS... can you guys find out what driver version you are running on 12.04 and 12.10?

---

### Post by FrancoNero on 2012-10-12
64bit. there is NO reason to do otherwise, and some report that u need 64bit to cope with the UEFI boot.

12.10, MUCH better compatibility and why use a half-year old OS if you can use the latest?

---

### Post by OrangeCrate on 2012-10-12
Ubuntu maintains a list of certified hardware. I see the X1 is on the list...

[http://www.ubuntu.com/certification/hardware/201104-7945/](http://www.ubuntu.com/certification/hardware/201104-7945/)

---

### Post by litiform on 2012-10-12
I wish Lenovo would stop trying to copy Apple laptops.

I've always liked Thinkpad laptops better than Apple. But Lenovo keeps changing the thinkpads to be more and more Apple like nad in the process making the Thinkpads less and less good.

---

### Post by dpjg on 2012-10-14
@[OrangeCrate]("http://ubuntuforums.org/member.php?u=210301"): your link refers to the Lenovo X1, and not the Lenovo X1 Carbon as far as I can see.

---

### Post by OrangeCrate on 2012-10-14
> **dpjg said:**
> @[OrangeCrate]("http://ubuntuforums.org/member.php?u=210301"): your link refers to the Lenovo X1, and not the Lenovo X1 Carbon as far as I can see.

Yes, I know it does. The Carbon is just a new model in the X Series for Lenovo. What you should have extracted from my post, is that they all share the same new generation components, and though the "Carbon" is not yet specifically tested, the link I referred you to is for Ubuntu Certified Hardware, which contains many Lenovo model laptops and notebooks. Since the components are same/similar, the X1 and the X1 Carbon will perform enough alike to offer the suggestion that if one can install and use Ubuntu 12.04 without problems on an older model, it would be worth looking at a newer model if it shares many, if not all of the same specifications. I guess I would have thought you would have made that association on your own, but, apparently not.

---

### Post by cprofitt on 2012-10-16
For the 'record' the unit I tested on was the X1 Carbon, not the original X1.

---

### Post by FrancoNero on 2012-10-16
Really need to do something about fan noise. That **** is annoying as hell. It's basically on, constantly. And no, I dont want to fiddle around with thinkfan, it's "linux for human beings", I dont want to have to fiddle around with this in order to quiet this fan down :)

Battery time is also not great....

---

### Post by emdeem on 2012-10-16
Anyone find a way to get the fingerprint reader to work under Ubuntu?  It looks like the newer reader it uses is still not supported in Linux.

---

### Post by FrancoNero on 2012-10-20
havent tried that one.
does anyone know a really simple trick to shut up the fan? ;)

---

### Post by bkfitz on 2012-10-22
X1 carbon with 12.04 LTS 64bit and TRIM enabled:

Everything (that I use) works great except fingerprint reader.  Fingerprint GUI from PPA's says "Device Not Found".  

Other than that it rocks... this machine boots in 8-10 seconds!!!!!

PS - fan might be on 24/7, but it's pretty darn quiet... didn't even notice it until I read the thread.

---

### Post by FrancoNero on 2012-10-22
depends on the definition of quiet, if quiet means off or inaudible, then it's definitely not quiet ;)

also gets quite hot...  

why did you enable TRIM? and what's the battery time you get out of your machine?

---

### Post by loklaan on 2012-10-22
> **FrancoNero said:**
> 
why did you enable TRIM?

An OS with [TRIM]("http://en.wikipedia.org/wiki/TRIM") protects the computers SSD from slowly degrading write speeds, but it is known to lower the life of the SSD.

...8 seconds boot time sounds gooood!

---

### Post by FrancoNero on 2012-10-23
In fact I  manage less than 8 seconds (8GB RAM)

---

### Post by ep66 on 2012-10-24
Guys are you having video driver provblems since upgrading to Quantal??

I am having constant crashes since then, like every 2h one :(

See:

[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1070656](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1070656)

If anyone on quantal is NOT having this, please let me know.

kubuntu-quantal on stock 3.5.0-17 kernel

---

### Post by FrancoNero on 2012-10-24
I have no problems. But I have always been running Quantal on it. Worked out of the box.

---

### Post by ep66 on 2012-10-24
Interesting.

Are you suspending/resuming a lot?

---

### Post by FrancoNero on 2012-10-24
yes, I only really shut down the machine before I go to sleep, and not often that rule I stick to.

Folding the laptop (suspend) and opening to continue working (resume) I do many many time and it works flawlessly.

have you done a fresh install of quantal64bit or did you run an update?

---

### Post by ep66 on 2012-10-24
This was an update from a fresh Precise, with which I had no problems at all :(

dmesg|grep drm on your machine shows no hangcheck errors of any sort?

And no graphic artifacts of any sort either, like suddenly white blocks on part of the screen or dissappearing text that can only be made visible after selecting it?
This heals itself, by eg CTRL-ALT-F1 and back to X with ALT-F7, but not really ideal :(

---

### Post by emdeem on 2012-10-24
Has anyone tried adjusting the color calibration?  I tried the icc profile discussed at [https://plus.google.com/110166527124367568225/posts/bLg18FtS8KZ](https://plus.google.com/110166527124367568225/posts/bLg18FtS8KZ), but it looks even worse (to me at least).

---

### Post by ep66 on 2012-10-24
That is a profile for the T430s, no the X1 Carbon.
The X1C has a completely different display.
I got myself that colorhug device today will play around with it in the coming days and can post some results here.

If I get my darn system back to stable :( :(

So nobody else has issues?

---

### Post by emdeem on 2012-10-24
> **ep66 said:**
> That is a profile for the T430s, no the X1 Carbon.
The X1C has a completely different display.

Ah, OK thanks.  I thought I had read somewhere that the T430 and X1C used the same panel.

---

### Post by FrancoNero on 2012-10-24
ep66,

I advise you to try a fresh install of quantal64bit on this machine to make sure the upgrade didnt cause the problems. I have none of the problems you are referring to.

in terms of color profile. i would love to adjust this as well, the colors per default look very bland...

---

### Post by ep66 on 2012-10-25
memtest revealed 8mn errors :( :( :(
seems I was sent a brand new machine with faulty ram, just my luck...

---

### Post by FrancoNero on 2012-10-25
sorry to hear.

quality assurance is not a lenovo strength. i plan on writing an extensive blog post on that soon. there are a lot of minor details wrong with this machine that more quality testing could have prevented, and better company policies.

for example: why the hell is the AC adaptor so damn huge?

---

### Post by FrancoNero on 2012-11-05
Update:

I now tested the HDMI out: No problems, just UI-wise, it would be nice to make it easier to switch between different audio outputs etc.

Today for the first time I encountered that bug where touchpad/thinkpoint were unavailable upon wakeup. But closing and reopening solved it. Haven't checked after today's massive kernel update.

Still annoyingly much fan noise and activity. Any tips appreciated.

Overall, not very impressed with battery life...





To give my identity away, I blogged about this machine here:

[http://www.sebastian-haselbeck.de/lenovo-needs-to-eat-its-own-dog-food/](http://www.sebastian-haselbeck.de/lenovo-needs-to-eat-its-own-dog-food/)

---

### Post by zackiv31 on 2012-11-18
Anyone got the USB->ethernet adapter working?  I'm talking about "Lenovo USB 2.0 Ethernet Adapter" Model: U2L100P-Y1, the one that may have been included with your laptop.  I plug it in, and all I see in lsusb is :

```

Bus 001 Device 004: ID 17ef:7203 Lenovo 

```

---

### Post by FrancoNero on 2012-11-18
sorry, not using the lenovo one, so I can't say...

---

### Post by hicolour on 2012-11-21
> **FrancoNero said:**
> Update:

To give my identity away, I blogged about this machine here:

[http://www.sebastian-haselbeck.de/lenovo-needs-to-eat-its-own-dog-food/](http://www.sebastian-haselbeck.de/lenovo-needs-to-eat-its-own-dog-food/)

Nice review, could you add some photos, especially I would like to see the display ?

Second question is about performance - did you try to run vritualbox or vmware virtual machine?. I wonder how the memory will be utilized and if the primary system will be responsive.
I'm planning to buy X1 with 8GB ram and i7 but based on my experience it may be not enough to comfortably work on main OS and on the virtual machine.

---

### Post by FrancoNero on 2012-11-21
hi

i'll try to take some pictures this weekend.

havent run a VM so far. i have the i5/8gig version. I am not sure how much an ultrabook really stacks up as a developer environment....

---

### Post by hicolour on 2012-11-21
thanks a lot, ultrabook maybe is not good idea for photo/video processing but for programming should be enough ;) - unfortunately only macbook is more powerful and has similar size - but I would prefer to work on thinkpad with ubuntu on board

---

### Post by Redsandro on 2012-11-22
Anyone have the same problem?

Thinkpad Carbon X1 + Ubuntu 12.04 => Flawless
Thinkpad Carbon X1 + Ubuntu 12.10 => Trackpoint not working

I noticed this on the LiveCD (on USB ofcourse :P) when I wanted to install the newer version, so now I dare not install.

---

### Post by pmorton on 2012-12-12
I can't get the Carbon X1 to boot from Ubuntu on a USB flash drive. I've switched it on to Legacy boot, but to no effect. My USB flash drive is ok and boots fine on another laptop. Has anyone experience this problem with the Carbon X1? I see that many here manged to load Ubuntu onto the machine. Any suggestions why I'm experiencing this problem?

---

### Post by emdeem on 2012-12-12
> **pmorton said:**
> I can't get the Carbon X1 to boot from Ubuntu on a USB flash drive. I've switched it on to Legacy boot, but to no effect. My USB flash drive is ok and boots fine on another laptop. Has anyone experience this problem with the Carbon X1? I see that many here manged to load Ubuntu onto the machine. Any suggestions why I'm experiencing this problem?

No problem booting from a live Raring (64-bit) USB stick with default BIOS settings.

---

### Post by Redsandro on 2012-12-12
No problem booting Linux Mint 14 Cinnamon 64 bit from USB created with Unetbootin using default factory settings on the laptop.

---

### Post by pmorton on 2012-12-13
> **Redsandro said:**
> No problem booting Linux Mint 14 Cinnamon 64 bit from USB created with Unetbootin using default factory settings on the laptop.

I made the same USB boot drive with Mint Cinnamon 64, and put the Carbon X1 back to Lenovo's factory condition. I get up the Boot Menu and it gives me the choice of booting from the internal Sandisk hard drive (Windows) or the USB drive, as Sandisk Cruser Blade, on which Mint 14 resides (the latter loads up ok from my desktop). When I choose the USB drive to boot from, the screen flashes and it goes back to the Boot Menu without doing anything. Any further ideas?

---

### Post by Redsandro on 2012-12-13
I didn't pay much attention because for me it immediately worked.
Using F8 or F10 or sth to get the boot options, and then choose USB. I don't know why it won't work for you. :(

These are just guesses and might seem silly.

Maybe you need to use the other USB port? (There are two)
Maybe your USB stick is incompatible with booting? Try a different brand.
Maybe your USB stick is formatted improperly for the bootable iso to work? Format as FAT16 and use Unetbootin on it. Or FAT32?

---

### Post by pmorton on 2012-12-13
Thanks; I've checked all of these to avail, except that the USB flash drive may be the problem insofar as it's a Sandisk, like the hard drive - the machine could be having problems with that. I'll try another drive.

---

### Post by pmorton on 2012-12-14
Changed the USB drive to another make, and it now boots!

Not the end of the problem, though.

Tried to install Ubuntu alongside Windows. Let me reduce the size of the Windows partition, but the freed-up unallocated space then registered as 'unuseable'. So I gave up on that and overwrote windows. That went well, until I tried to boot Ubuntu from the internal solid state drive, only to find the BIOS won't now boot from that drive!

It all seems to be to do with secure booting, which is a big pain to deal with. Lenovo's support (UK 01475 897 163) say that in addition to switching Secure Boot in the BIOS to 'Disabled', in the Restart/Load Setup Defaults menu, the item 'OS Optimise Defaults' needs to be set to 'Disabled' too. Yet to try it.

---

### Post by pmorton on 2012-12-16
> **pmorton said:**
> Lenovo's support (UK 01475 897 163) say that in addition to switching Secure Boot in the BIOS to 'Disabled', in the Restart/Load Setup Defaults menu, the item 'OS Optimise Defaults' needs to be set to 'Disabled' too. Yet to try it.

That did it - I've now got Ubuntu running, having overwritten Windows.

---

### Post by ehabh on 2012-12-27
One question to the guys that own a x1 carbon how good is the build quality. I had a T420 and it was aweful the case croaked at some points and the keyboard had a few keys that made noises above that after about 2 years it started to randomly shutdown.
I mean lenovo are not cheap and  I do not know if I should give them another chance? Feedback wanted :)

---

### Post by flocsy on 2012-12-31
Hi, I just got mine unboxed today. I booted Linux Mint 14 from USB, but then I see that all 4 partitions are used. I am trying to install Linux but would prefer to leave Windows untouched (except shrinking it's size) to have a dual boot environment. Does anyone have any idea how could that be achieved?

These are the partitions:

sda1 ntfs    SYSTEM_DRV        1.46GB
sda2 ntfs    Windows7_OS     215GB
sda3 ntfs    Lenovo_Recovery  14GB
sda4 unknown                   8GB
unallocated                    1GB
(I was suggested that sda4 is for hibernation)

---

### Post by pmorton on 2012-12-31
Re build quality, I have no complaints with  the Carbon X1. Re dual booting, I tried that myself by attempting to unallocate Windows drive space, but couldn't get that to work. The problem seemed to relate to the inbuilt Intel boot protection. I eventually gave up and installed from scratchLinux Mint (sorry, Canonical, but this distro had an edge in my view not only in appearance but in reliability), and am very happy with the result. In particular, sleep mode and the touch pad, including 2 finger scrolling, work well.

---

### Post by flocsy on 2013-01-06
I managed to shrink the Windows7 partition, then I wrote down the start and end cylinders in fdisk of the recovery partition, then deleted the partition in fdisk, created an extended partition (has to be bigger. Actually it has to start before the recovery partition's beginning, because of the way the logical partitions are stored in an extended partition) in the whole area (end of the windows7 + the recovery). Then created a logical partition in the exact start-, end positions of the original. Then I could add another logical partitions for the Linux root and swap (only for hibernation) in the place that was freed by the shunk win7. At the end tested and the recovery partition still seems to work (can boot it and it starts to load the files, so it looks it' still functional.)

---

### Post by zackiv31 on 2013-01-08
> **ehabh said:**
> One question to the guys that own a x1 carbon how good is the build quality. I had a T420 and it was aweful the case croaked at some points and the keyboard had a few keys that made noises above that after about 2 years it started to randomly shutdown.
I mean lenovo are not cheap and  I do not know if I should give them another chance? Feedback wanted :)

I've had this machine for a couple months now.  It's fantastic for development.  I have an i5/8gb/128gb of which I wiped and installed xubuntu 12.10.  It flies.  Boots up in <10 seconds.  Don't need much space at all for ubuntu obviously.. 20gb /, 100gb /home, and I added a 64gb SD card for media.

I don't think I needed the 8gb for Web Development... Chrome + FireFox w/ 20 tabs, ST2 and a bunch of terminals... doesn't ever reach above 3gb used.  If you're going to do any more, or anything with VMs you might like the extra headroom at 8gb.  I'm going to install XP in virtualbox w/ Photoshop tonight just to see how it performs.  I personally know I won't upgrade for another couple years, so the 8gb was worth it more then shelling out for the 256gb SSD.

Oh ya, and I'm coming from a T60p -> X61 SXGA+ -> X1C ... this was the only logical choice, and a beautiful upgrade.

---

### Post by merrickweb on 2013-03-07
> **flocsy said:**
> Hi, I just got mine unboxed today. I booted Linux Mint 14 from USB, but then I see that all 4 partitions are used. I am trying to install Linux but would prefer to leave Windows untouched (except shrinking it's size) to have a dual boot environment. Does anyone have any idea how could that be achieved?

These are the partitions:

sda1 ntfs    SYSTEM_DRV        1.46GB
sda2 ntfs    Windows7_OS     215GB
sda3 ntfs    Lenovo_Recovery  14GB
sda4 unknown                   8GB
unallocated                    1GB
(I was suggested that sda4 is for hibernation)


I needed to do exactly the same thing. Here is what I did.


1) bought a cheap dvd burner and a spindle of DVDs from Amazon
2) set it up and double clicked the recovery partition
3) chose make recovery and boot discs (it took 4 dvds)
4) chose recover space.  This automatically freed up the space and merged the recovery partition with the Windows7_OS partition

now you have 3 primary partitions meaning you can install linux

The way I did it was to follow these instructions here:

[http://www.youtube.com/watch?v=PvP_4J2MUEc](http://www.youtube.com/watch?v=PvP_4J2MUEc)

basically you shrink the windows 7 partition in the disc manager on windows (right click computer >manage>disk management>right click on the win 7 partition > shrink volume)
I chose 20 gigs for Ubuntu (20000) megs
Then I used a bootable USB drive with Ubuntu on it (I downloaded precise penguin and used the linux live windows app to make it [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/))
After powering down windows and sticking the USB stick in the machine
I clicked F12 to temporarily boot on the USB stick
Then I started the Installation process 
I chose the something else option under Installation type, added a 1 gig (1000 meg) swap partition as logical partition
then i made the rest the partition for ubuntu

It might seem confusing but if you watch the video I posted it will be really simple.

So far I am loving my x1 carbon and ubuntu is rocking on it!

---

### Post by Bashar &quot; on 2013-04-01
anybody knows if the Touch screen model works flawlessly with ubuntu too?

---

### Post by Redsandro on 2013-04-02
X1 Carbon comes with touch screen now?

Mine does not have a touchscreen. Is this new or are you mistaken?

---

### Post by trivialpackets on 2013-04-02
There is a new release of the X1 Carbon Touch that I've been eyeing.  

[Link]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/catalog.workflow:category.details?current-catalog-id=12F0696583E04D86B9B79B0FEC01C087&current-category-id=6E9E54C0CB3A5CE321C8D1466B302411")

> **Redsandro said:**
> X1 Carbon comes with touch screen now?

Mine does not have a touchscreen. Is this new or are you mistaken?

---

### Post by Redsandro on 2013-04-02
You gotta be kidding me, this thing I'm on is brand new and now it's old! :P

Btw > Our apologies

The page you requested is not available.

---

### Post by Bashar &quot; on 2013-04-02
> **Redsandro said:**
> You gotta be kidding me, this thing I'm on is brand new and now it's old! :P

Btw

yes there is :-) and this is the correct [link]("http://www.lenovo.com/products/us/laptop/thinkpad/x-series/x1-carbon-touch/")

---

### Post by Redsandro on 2013-04-02
Thanks. Looks awesome. The 'old' Carbon X1 is an awesome laptop. Although the vertical screen viewing angle is terrible, which pisses me off, because the cheaper MacBook Air and even the newer ones with Retina are a lot better screenwise, AND CHEAPER. Unfortunately I can't buy one, because giving money to Apple would make me hypocritical.

---

### Post by ahmed_saad on 2014-02-11
thanx:)
[Arab New Tech]("http://arabnewtech.com/")

---

