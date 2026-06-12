---
title: "Feisty cold boot problem on IBM T22"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by mango42 on 2007-08-14
Hi,

As in my previous post today, I would like to start by saying again a very very heartfelt THANKYOU to all you dedicated volunteer programmers who have made this brilliant Linux version accessible to those who don't (or in my case, no longer) want to get their hands dirty. [some personal background in the p.s.]

I feel extremely diffident in posting problems here but in this instance I have drawn a complete blank after searching this forum and wiki. Scroogle just gives me:-

"site:ubuntu.com Feisty T22 cold boot problem - Google Search

Google returned no results for this search. "

Ok. I installed Feisty on this IBM T22 Win2k machine from the alternate CD after many fruitless attempts with the LiveCD. When it came to partitioning I was given no option to resize the existing 20Gb ntfs system, so I backed out, rebooted into Win2k and used Partition Magic 7 to free up 8Gb for Ubuntu. Fine, next Feisty install attempt worked and I arrived on Gnome, doubly amazed that Ubuntu could actually access the Win2k partition as well.

However, after shutting the machine down and cold booting via Grub 1.5, Feisty got stuck just after the orange bar finished filling but before the brief screen corruption and mouse appearance. Blank screen, no keyboard combination would wake it up (not even CtlAlt F2 or Del) After a day or two, I realised that Feisty would boot fine ONLY IF I booted into Win2k first (is this some kinda karma?? :)

Could someone please help me to the magic words that will enable Grub to cold boot into Feisty? Or is it the dreaded Savage graphics drivers (1024x768:24bit) that cause this issue?

Thanks in advance - if only to point me to a web page that has unfortunately escaped my search terms so far!

I also have very weird issues with USB and frozen keyboard but will leave that for another day.

mango

ps. (Just personal stuff) - Back in the mid eighties a group of us got together to produce a nationwide gamma radiation monitoring service after discovering that the Govt/Siemens network was never going to be truly accessible to the general public. We had to build both the hardware & software from scratch on Unix and CPM machines. It took seven of us 5 years of voluntary work, sometimes 16 hours a day, to get it fully up and running. [www.weatherprobe.co.uk](www.weatherprobe.co.uk)

By this time, two volunteers had had nervous breakdowns (mainly from having to fend off MI5 and NRPB bods who weren't at all happy with our little project!) and by the 6th year I had to quit as coding and hardware debugging was making me physically ill. These days I still get a bad feeling whenever I even think about code! This makes me quintupally grateful to all you coders who have made Ubuntu possible. It is so heart warming to see that large-scale voluntary cooperation can still produce such positive and beneficial results. Thank you all once again; it has totally restored my interest in computers as genuinely useful tools for the layman.

 WWW? World Without Windows!

---

### Post by mango42 on 2007-08-17
Just a bump although I'm not too surprised no-one has been able to help with this :(

---

### Post by mango42 on 2007-09-19
For a relative newcomer to the wonderful world of Ubuntu, I don't think Grub is the place to start experimenting, do you?

Yet I still have this extremely annoying problem noted in my posts below.

Could someone knowledgeable **please** point me to a page that explains in lay terms how to modify Grub so I don't have to boot into rotten old Windoze every time I cold boot?

I like Ubuntu so much that if I cannot get this problem solved I will join those pushing for non-US companies like Toshiba to offer machines with Ubuntu pre-installed.

Thanks for your patience with a Linux rookie!

---

### Post by ted209 on 2007-11-26
I'm afraid I can't help, except to say that I think I have the same problem.

Every time I boot my T22 from cold, it freezes on a blank screen after the splash. If I restart, it may do it once more, but on a second restart, ubuntu starts fine.

Exactly the same think happened when I first tried ubuntu a couple of years ago. I mentioned it in the comments of my blog at the time:
[http://ubuntuthinkpad.blogspot.com/](http://ubuntuthinkpad.blogspot.com/)
I think I only had this problem when I installed the proper driver for the video card (it was fine with no 3d acceleration).

Can anyone else shed light on this - it just seems weird that a computer needs to "warm up" before it will run ubuntu!!

Ed

---

### Post by cosmolee on 2007-12-01
I don't think it has anything to do with being warm or cold.   I've booted into recovery-mode, then just let the T22 sit there for a while.  Then I try to boot into graphical, but I still have the same problem.  Sometimes it seems the only way to get the thing up is to reboot 4 times.

:confused:

---

### Post by cosmolee on 2007-12-05
This might be of some help...

Although I haven't found a solution to the problem, I find that "suspend" does seem to work with my T22.  The only problem is that my PCMCIA DLink WiFi card needs to be reset - WiFi doesn't come up again after suspend.  I also have to use `wlassistant` to reset the wifi card.

It's still a pain, but less so than rebooting 4 times before I get the GUI to login.  

HTH.

---

### Post by quietas on 2007-12-07
That is really quite odd. I'm actually typing on my T22 atm while it does the 7.04 to 7.10 upgrade via the Update Manager.

I have had a few weird issues where it sometimes seems to freeze during boot. I left it alone and it loaded after some unknown long amount of time once. After that I just powered it off manually and restarted with no issues when it has happened since then.

No idea if it matters I am running 384 MB ram instead of the default and a Dlink PC-Card since I have no internal network card.

---

### Post by ted209 on 2007-12-16
Well, I seem to have fixed the unreliable boot problem on my T22!!

I followed instructions here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T20)

This was to fix 3d graphics acceleration which was not working. I believe I didn't have to change any of my configuration, but I did have to do this:

***Make sure the package libgl1-mesa-dri is installed***

Now 3d acceleration works and my laptop ALWAYS boots! It's worth a try.

Ed

---

### Post by mango42 on 2007-12-18
Responses much appreciated - thanks.

Suspend works most of the time now in Feisty - one way around the problem for sure, except Totem misbehaves on resume.

I'm still no further forward except to suspect the sound driver although why that should be reset by booting into W2k first is beyond me... Any attempt to get into a terminal prior to X start seems unworkable so no dmesg help either.

I suppose it is a bit much expecting such an old box to behave.

I've found an excellent program called AptOnCD that .iso's all Feisty upgrades, so I'll probably lobotomise this T22 soon, reinstall Win98 from the IBM disk then try again with Ubuntu, already my favourite OS ever.

---

