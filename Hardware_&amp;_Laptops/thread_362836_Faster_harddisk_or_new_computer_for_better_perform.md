---
title: "Faster harddisk or new computer for better performance?"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by fbn on 2007-02-16
Hi,

I'm thinking about buying a new faster harddisk for my 2 years old computer at home. Running Edgy Eft it seems that the harddisk is too slow for applications like Open Office.

Which harddisk would you prefer for best performance? (size does not matter, small is okay)

Or will buying a whole new computer be the better solution?

Regards,
  Frank

---

### Post by DrNick on 2007-02-16
Hi there

It's very possible that the hard disk itself isn't the bottleneck.  It's more likely that adding extra RAM will give you better performance benifits than swapping out the disk, and also possibly be a cheaper upgrade.  OpenOffice.org, despite being a good office suite, is pretty hungry in terms of system specs - RAM in particular.  If you're running with 256MB RAM or less, I'd recommend upgrading to 512MB, or possibly even more.

Also, it may be the case that you can achieve better I/O performance with your existing disk.  On some controllers, settings such as DMA are disabled by default, even though the drive and controller support them.  A program called 'hdparm' can be used to set various options for your drive and controller which could potentially double it's I/O performance.  A very good guide to using it can be found on the Gentoo Linux Wiki at this address:

[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

Ignore the bit about installing hdparm, as the 'emerge' package management system is specific to Gentoo Linux.  If it's not already available on your system, then typing

sudo apt-get install hdparm

will install and set up the package for you.

Happy tweaking...

---

### Post by PurplePenguin on 2007-02-16
DrNick's right.  He didn't go to Hollywood Upstairs Medical College for nothing! :)

If you're running something like OpenOffice, take a look at your hard drive activity light (if you've got one) on your computer.  If you're running less than 512MB of RAM, I can guarantee that you'll see that light pretty much just staying on.   That's your hard drive's swap space in action.   You can probably hear it hitting your hard drive all the time, too.  

I've got an old computer (AMD 1200) that runs Edgy very, very well after adding a 512 MB stick to the 128 that it started with.  I'm a believer in RAM being the single best upgrade for a computer. :)

If you run into some extra cash down the road, though, 200GB hard drives are ridiculously cheap these days.  I bought one for CDN $70.  It won't speed up your computer, but you'll be able to hold a lot more on it, and that's always a good thing.  But get that AFTER you upgrade your RAM.

---

### Post by fbn on 2007-02-16
Hi,

I have 1 GB RAM in my computer :-)

But I see a lot of harddisk activity (LED blinks) while booting, logging into Gnome for the first time, starting epiphany, starting and using Open Office ... 

So many things read from harddisk so I thought buying a smaller but faster one will improve performance.

It would be great to have super fast 10 GB harddisk for the operating system and the applications and the 200 GB harddisk for the data. But I don't know of such a 10 GB super fast harddisk ...

---

### Post by Stef@n on 2007-02-16
FBN,

What's the hardrive you're currently using (brand, size, rpm's)? Preferebly post your system specs. We need some systeminfo to give good advice. Otherwise all you get are shots in the dark.

Gr.

---

### Post by logos34 on 2007-02-16
OO is a heavy program (I use Abiword whenever I can), and if you don't have a lot of RAM takes forever to load...You should have 512MB ram, 768mb (better), and ideally 1GB.  If you want a really fast disk you might consider a WD Raptor (74GB and 150GB)--10,000rpm fast seek times and average data transers in the 70-80MB/s range...But they're about 40% more per gb and run hotter and a bit louder than your typical 7200...A RAID 1 setup might be a better option--data redundancy with the added benefit of nearly double the read times (write speeds same as single disk).  I've been considering the latter for a while now.  The new perpendicular technology desktop drives are also a bit faster, and not much more expensive.

---

### Post by fbn on 2007-02-16
it's a Maxtor 6Y160M0 harddisk.

specs: 7200 rpm, Serial-ATA, 3,5", 9 ms access time, 8 MByte buffer.

RAID1 was a thing I've also thought about but I have a barebone system which only allows one harddisk.

Are there no faster (but therefore maybe smaller) harddisks available?

---

### Post by fbn on 2007-02-16
is it possible that the disk is too much fragmented? I've created one big partition for Ubuntu (no windows, but a swap partition) and there are a lot of files on it ...

---

### Post by kevinlyfellow on 2007-02-16
Unlikely, ext2 doesn't become too fragmented over time.

post up what hdparm says about you disk speeds assuming the os is installed on /dev/hda
```
sudo hdparm -tT /dev/hda
```

This will give us an idea if it is the hd speed thats causing the problem.  OO.O is a slow program keep in mind, but it should be usable after it takes forever to start up.  You can try to disable the java options in openoffice, which may speed things up.  There is also memory management options you can use.  I've used OpenOffice on my old desktop for several years without a problem, 1 GHz procssor 512 Mb ram and an hd that was just plain SLOW, it should work with your two year old.  Is there any other apps that seem to run sluggish?

---

### Post by esaym on 2007-02-17
CPU speed has to do with it too.  I find good response times above 2ghz :)

---

### Post by fbn on 2007-02-17
websites seem to be slow sometimes (not the connection speed, the way sites are build in browser or scrolling large sites). don't know if this is harddisk related but my feeling tells me that very often it relays to the harddisk (logging into gnome or starting the computer or starting applications)

video card is an nvidia GeForce 6600 GT with nVidia driver enabled. cpu is P4 3.2Ghz with hyper threading enabled.

harddisk (it's an SATA disk)

hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   3776 MB in  2.00 seconds = 1888.37 MB/sec
 Timing buffered disk reads:  160 MB in  3.03 seconds =  52.73 MB/sec

---

### Post by kevinlyfellow on 2007-02-17
hmmm... thats a thinker, your system seems like it should run without a hitch.  My best guess would be that it has to do with memory management.  Check top to make sure that when running an app its not dumping tons of stuff into the swap.  If thats the case, you can change the swappiness and that could help.  Also, have you installed the 686 kernel?  On some systems it can make a big difference in performance.

---

### Post by fbn on 2007-02-17
50MB of swap are used, swap partition is 1 GB in size.

I don't have a 686 kernel, I have the Ubuntu default kernel:
Linux xpc 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

I thought that with Edgy there is no need any more to switch to a different kernel?

---

### Post by kevinlyfellow on 2007-02-17
your completely right about the kernel :-b  I just installed edgy yesterday, and I did notice something different about the way the kernel was handled.

well 50 megs in the swap is nothing really, so I guess we can rule that out.  But in case your interested, here's an article on tweaking ubuntu, in it, it suggests changing your swappiness to zero (doesn't use the swap drive).  This may prevent some writes to the disk for you.  It also has other suggestions for optimizing you disk

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

---

### Post by Mike'sHardLinux on 2007-02-17
fbn, how long does it take to load O.O. (I assume you're talking specifically about the Word Processor). O.O. is known to take a bit to load, but it definitely shouldn't be like 30 seconds.

You haven't really stated specifically in what way things are slow. Are you saying that once O.O. is loaded, there is lag, for instance when you type, is there a noticeable delay to when the letter is displayed?

The slow website is a little tougher. How fast is your internet connection? Are you using an ethernet cable, or WIFI? If WIFI, are you getting a good quality signal? What web browser are you using? I assume Firefox. Are page loads slow even when not multitasking? There will always be times when websites seem to load slow, but are you meaning they are ridiculously slow( like minutes?)

All the things you mention about hard drive activity during bootup, logging into Gnome, loading programs are all normal. Those things have to be loaded from the hard drive to memory; doesn't matter how fast your system is. And it will always look like a lot of HD activity because it is.

Your read/write are only a little slower than mine, but not unusual. Here's mine for reference:
/dev/sda:
 Timing cached reads:   4388 MB in  2.00 seconds = 2194.50 MB/sec
 Timing buffered disk reads:  212 MB in  3.01 seconds =  70.39 MB/sec

I am having a feeling that maybe you are just used to the speed of your computer, and so it seems slower now that the newness is gone.....Or if there are some real issues, you haven't mentioned anything concrete, hence we have to make a bunch of educated guesses.

If you simply aren't happy with the performance, and it seems hard drive related, get a Raptor. AFAIK, those are the fastest SATA drives available.

---

### Post by fbn on 2007-02-18
> **Mike'sHardLinux said:**
> fbn, how long does it take to load O.O. (I assume you're talking specifically about the Word Processor). O.O. is known to take a bit to load, but it definitely shouldn't be like 30 seconds.

You haven't really stated specifically in what way things are slow. Are you saying that once O.O. is loaded, there is lag, for instance when you type, is there a noticeable delay to when the letter is displayed?

The slow website is a little tougher. How fast is your internet connection? Are you using an ethernet cable, or WIFI? If WIFI, are you getting a good quality signal? What web browser are you using? I assume Firefox. Are page loads slow even when not multitasking? There will always be times when websites seem to load slow, but are you meaning they are ridiculously slow( like minutes?)

All the things you mention about hard drive activity during bootup, logging into Gnome, loading programs are all normal. Those things have to be loaded from the hard drive to memory; doesn't matter how fast your system is. And it will always look like a lot of HD activity because it is.

Your read/write are only a little slower than mine, but not unusual. Here's mine for reference:
/dev/sda:
 Timing cached reads:   4388 MB in  2.00 seconds = 2194.50 MB/sec
 Timing buffered disk reads:  212 MB in  3.01 seconds =  70.39 MB/sec

I am having a feeling that maybe you are just used to the speed of your computer, and so it seems slower now that the newness is gone.....Or if there are some real issues, you haven't mentioned anything concrete, hence we have to make a bunch of educated guesses.

If you simply aren't happy with the performance, and it seems hard drive related, get a Raptor. AFAIK, those are the fastest SATA drives available.

OO takes about 25 seconds to load. typing is okay, but scrolling a print preview is bad and cpu spins up to 100% (not related to harddisk but i'm not sure)

The lag on scrolling large websites has nothing to do with the internet connection, it happens if a site is finished loading and then I start scrolling on it.

I'll try with a Raptor in April when Feisty is out, I want to have a brand new installation and that fits in well with a new harddisk :)

I just have that feeling that the computer is slow on Ubuntu while it has to do things with the harddisk and I was wondering if there is something to improve this. Maybe some harddisks or configurations are better for Linux kernels and some others are not ...

---

### Post by fbn on 2007-02-18
> **kevinlyfellow said:**
> your completely right about the kernel :-b  I just installed edgy yesterday, and I did notice something different about the way the kernel was handled.

well 50 megs in the swap is nothing really, so I guess we can rule that out.  But in case your interested, here's an article on tweaking ubuntu, in it, it suggests changing your swappiness to zero (doesn't use the swap drive).  This may prevent some writes to the disk for you.  It also has other suggestions for optimizing you disk

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

Thanks for the link, I'll have a look on that! But the developers will for sure choose the fastest performance settings as defaults, right?

---

### Post by timcredible on 2007-02-18
> **fbn said:**
> OO takes about 25 seconds to load. typing is okay, but scrolling a print preview is bad and cpu spins up to 100% (not related to harddisk but i'm not sure)

whoa!!  that's bad.  my amd 3200 w/ 1gb ram and 200gb ide hard drive takes 6 seconds to load oo.  oo does a dns query when it starts, so if you don't have an internet connection, it takes a long time to load while the dns query timesout.

 you should run top from the command line to see if there's any i/o slowness, or if it's all cpu.

---

### Post by Mike'sHardLinux on 2007-02-18
> **fbn said:**
> OO takes about 25 seconds to load. typing is okay, but scrolling a print preview is bad and cpu spins up to 100% (not related to harddisk but i'm not sure)

Wow! That is far too long. Mine takes about 3 -4 seconds. From what timcredible said, this could be related somehow to your network or internet connection. If not, I would say this isn't so much a hardware performance issue as much as there may be something wrong with a config, possibly some defective hardware, or maybe a compatibility issue (not likely.)

> **fbn said:**
> The lag on scrolling large websites has nothing to do with the internet connection, it happens if a site is finished loading and then I start scrolling on it.

This if kind of a guess, but are you sure you have direct rendering enabled? If you don't already know how, type this at the console: ```
glxinfo | grep "direct rendering"
``` You want it to say direct rendering: Yes

> **fbn said:**
> I'll try with a Raptor in April when Feisty is out, I want to have a brand new installation and that fits in well with a new harddisk :)

I just have that feeling that the computer is slow on Ubuntu while it has to do things with the harddisk and I was wondering if there is something to improve this. Maybe some harddisks or configurations are better for Linux kernels and some others are not ...

Now, we're starting to get a better idea that there really is a problem. I either missed that part, or you hadn't really said the stuff about laggy scrolling and the load time in O.O. is too long, even for a slower system.

---

### Post by kevinlyfellow on 2007-02-18
> **fbn said:**
> Thanks for the link, I'll have a look on that! But the developers will for sure choose the fastest performance settings as defaults, right?

Sometimes, sometimes not.  It really depends on what you do with your computer and what hardware you have.    Usually the defaults are great for most people

---

### Post by treesurf on 2007-02-18
> **Mike'sHardLinux said:**
> 


This if kind of a guess, but are you sure you have direct rendering enabled? If you don't already know how, type this at the console: ```
glxinfo | grep "direct rendering"
``` You want it to say direct rendering: Yes



I have been following this thread because I also have similar problems with the loading of OO.  It takes about 30 seconds on my desktop (1.2 Ghz Celeron, 372MB RAM).  I do not, however, have problems scrolling through web pages.

 I tried the above command and discovered that direct rendering is set to No.  Is this something I should change?  If so, how?

Thanks.

---

### Post by fbn on 2007-02-19
Internet connection is up an running all the time ... I'll check with IO while starting and also will try the Raptor harddisk.

---

### Post by jotagab on 2007-02-19
Why don't you check /var/log/messages and /var/log/syslog to see if you have some sort of recurring error message?
I disabled ipv6 (by adding the line 'blacklist ipv6' in /etc/modprobe.d/blacklist) because I saw too many related error messages in those log files; turns out that this problem was actually slowing down DNS translations.

---

### Post by fbn on 2007-02-20
> **jotagab said:**
> Why don't you check /var/log/messages and /var/log/syslog to see if you have some sort of recurring error message?
I disabled ipv6 (by adding the line 'blacklist ipv6' in /etc/modprobe.d/blacklist) because I saw too many related error messages in those log files; turns out that this problem was actually slowing down DNS translations.

there are no recurring error messages in the log files. network connection is okay, i can not think of having an issue with the network speed ... 

is it possible that a harddisk gets fragmented on Linux or that it gets slower over time because of more and more (also very big) files on it?

maybe the harddisk itself is on the way to get damaged but still no error messages in the logs ...

---

### Post by jotagab on 2007-02-20
Well, for me it seems that the problem could come from both software or hardware, now it's up to you to figure out how much time you want to spend on solving the issue...
I'd try installing a different OS (like Windows or BSD) to confirm that it's a hardware problem (OpenOffice exists for both of them, so it would be easy to compare performances). If the problem did persist I'd try to replace the components one by one (starting with the hard disk) to see from where it comes from (even using an older disk, or borrowing one from a friend). It could also be the SATA controller on the motherboard.
If with the other OSes the computer runs fine, it's a Linux/Ubuntu problem: just try to install a different distribution/version/kernel.
If you're already thinking of buying a new hard disk I guess you already started to backup your data, so some extra day (or two) of testing won't hurt. Besides, if the disk in on its way out, formatting it might reveal the problem...

Cheers!

---

### Post by fbn on 2007-02-20
the last time I had windows xp on this computer was a year ago (but with same hardware) :-)

openoffice was never installed on winxp because I used it on Linux but other applications like firefox were faster on winxp.

the whole behavior seems to be faster with windows than linux/ubuntu. starting firefox for example or scrolling (not loading, so it's not the connection) websites which are full of images or text or media content.

maybe it's the hardware (sata driver or nvidia driver on linux versus windows) or just my feeling, but i had this feeling on more than one computers.

anyway this is my working computer and i dont want to mess up too many with replacing hardware components or installing different distros / operating systems ... I'll get me a Raptor harddisk when Feisty comes out and try with a brand new installation.

What are your experiences with Open Office or Firefox or Thunderbird or ... on Windows compared to Linux/Ubuntu? Just like I've mentioned, scrolling large/big sites in Firefox (after they are fully loaded) or starting and using open office (loading print preview and scrolling it seems to eat 100% cpu on linux). Is it just me or my computers?

---

### Post by jotagab on 2007-02-23
When I switched from XP to Linux I also had the feeling that sometimes Firefox seemed less smooth. Regarding the application loading time I didn't notice much difference (although I didn't have many programs to compare...). However I think that my slooooow hard disk (4200rpm :P) acts like a crutch in whatever OS I install.
However my laptop, as a whole, seems more responsive with Ubuntu than with XP. It's just an OS, not a religion (for me anyway), so just use what's best for you (eh, even if it's from Microsoft...).

---

