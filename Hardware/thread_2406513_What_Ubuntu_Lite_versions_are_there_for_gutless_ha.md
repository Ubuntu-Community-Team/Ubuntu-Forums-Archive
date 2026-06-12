---
title: "What Ubuntu Lite versions are there for gutless hardware?"
date: 2018-11-21
forum: Hardware
---

### Post by hennmann on 2018-11-21
Other than using Puppy what possible Lite versions of Ubuntu fit my requirements?
This is what I have and was lacking from new, an Acer Aspire One 533 (2009/10 vintage) and has 2 GB of RAM (used to be 1), an Intel Atom 455 1.66 Ghz single core processor and this is also a 64 bit processor with Win10 64 running on one of the partitions as an experiment.
I upgraded the 250 GB HHD to a 1 TB SSD which really helped due to the snail 5400RPM it previously had. Also this Acer Aspire One 533 originally has Win 7 Starter on it and even this so called basic version of 7 ran like a sloth with 1 GB of RAM so I upgraded it to the supposed max 2 GB  and this changed the Sloth into a Bionic Turtle, 1GB was a bad idea from the beginning and 2 created a sweeter tasting Lemon.
Since this Netbook exceeds the minimum system requirements in a somewhat pathetic way and the Intel Atom bomb is a 64 capable device possibly increasing options what is a good Ubuntu version that would work great in this Netbook? 
I have 3 partitions with 10 on one, 7 on the other and the 3rd for a future Linux install and presently there is a Win 10 boot loader giving me the choice of 7 or 10.

Now as for old hardware I also have an HP Omnibook Xe3 with a P III 800 and a whopping 128 megs of RAM and as an experiment ran Puppy 4.3.1 on it with surprising results such as running faster than the original Win 2000 Pro it was sold new with. Due to the meager speck of RAM running Live is a dead horse so I set up a 300 meg Swap in the tiny 20 GB HHD and installed Puppy on the drive and just having the swap made an incredible difference! Mandrake 7.0 from 2000/1 also is at home on this HP as well but as we all know Mandrake, then becoming Mandriva is now extinct but anyway my options are much greater for the Aspire!

---

### Post by kc1di on 2018-11-22
I think you will find that Lubuntu may work on that machine.  other than that I would suggest something with xfce or lxde desktops. good luck in your search. 
Give anti-x a try it may surprise you.  (though it's not a ubuntu derivative.)

---

### Post by ajgreeny on 2018-11-22
Lubuntu 18.04 should work on that as kc1di says; I use it on a lower spec machine with only 1GB ram and an Atom 270 at 1.6GHz, and whilst it runs pretty slowly, it is fine for email and browsing use, even for watching video as long as its not high resolution, HD video.

---

### Post by kurt18947 on 2018-11-22
On your HP Omnibook, I have a machine of lower spec (PIII 660(?)  w/ 512 RAM)running Q4OS. It's a Debian based distro running the Trinity desktop and is quite light on resources. For your other machine I'd agree with Xubuntu or one of the Lubuntu flavors. There is a LXQT flavor of Lubuntu recently released.

---

### Post by hennmann on 2018-11-22
The Acer Aspire One 533 has an Atom 455 1.66ghz and 2 gb or RAM Win 7 Starter is fair but in reality hardware I have soars like an eagle with XP with the tiny system requirements and 7 is nothing more than a resource hog!! Vista was much worse bringing hi end systems to a crawl! 10 is even worse with much unnecessary crap running in the background. I believe I tried Ubuntu 18.04 on my drive by itself with not bad results but with Win7&10 on there I would like to be sure before installing just to have to reinstall something else. I guess another alternative is to stick in a USB with the OS on it and place a second USB and permanently install it like a HHD with swap for a more accurate tryout as I don't have an external USB drive yet. I guess I should break down and purchase one for times like these and backing up systems! Just having a swap makes an incredible difference compared to live and the HP with so little ram was a good example! Even Mandrake 7 from 2000/1 runs great on it but Mandrake is extinct. Just because it is d doesn't mean it's no good. The newer OS's are forcing us to always upgrade just to have more whistles and bells we really don't always need.

---

### Post by him610 on 2018-11-22
I have a similar, but older (BIOS 2008) AAO 110L (upgraded from 512KB to 1,5GB RAM) that runs great on Xubuntu 18.04.1. You must be realistic in your expectations though. I use my AAO 110L as my primary travel machine. Lubuntu should run well on yours also.

---

### Post by hennmann on 2018-11-22
Lubuntu 18.10 looks very promising as I run it Live and I didn't have to configure ethernet at all, and my Wifi is working great. 
Xenialpup64-7.5 is also fantastic and snappier I might add but doesnt support 32 bit computers like my IBM Thinkpad with 1280 megs of RAM and Intel 1500M processor. The biggest PITA is the PAE and newer flavors that support 32 abort and cry about PAE It's a PAEn in the @$$
Ubuntu 16.04.5 is somewhat sluggish like 18.0.4 in live but installed I'm not sure otherwise Lubuntu and Xenialpup are the best performers in Live. 
Now the older Puppy  Anita OS4.3.1 soared like eagles on both the Aspire and IBM but the internet browser wouldn't open but is very presentable. The earlier version of this 4.3.1 also worked very well on my old HP with the PIII800 and 128 megs of RAM and performed better than Win 2000. It is sad when older versions that rocked on smaller hardware are "discontinued" and should be able to be updated like the supported OS.

> **ajgreeny said:**
> Lubuntu 18.04 should work on that as kc1di says; I use it on a lower spec machine with only 1GB ram and an Atom 270 at 1.6GHz, and whilst it runs pretty slowly, it is fine for email and browsing use, even for watching video as long as its not high resolution, HD video.
Are you running this live or do you have it installed permanently on the hard drive? Permanently installing with a swap was the only way I could get Puppy 4.3.1 to run on my HP OmniBook XE3 with 128 megs of RAM and a PII800. It worked like it belonged on the HP as did extinct Mandrake 7.0
My slight advantage over your machine is 2 gigs and an Atom N455@1.66ghz. If I didn't know any better I would venture a guess and think you were running a slightly older Acer Aspire One that had XP or Linpus Lite on it?? I procrastinated too long and these were discontinued and ended up with the Win 7 Starter. The Linpus fascinated me being a gui slave despite the complaints about it but in reality a small Icon on the bottom corner allowed the gui desktop to be toggled to a conventional Linux desktop. I think I'm going to install 18.0.4 on this Acer to see if any improvement results instead of live. If I don't @*%! things up I can always install a lighter version later.

> **him610 said:**
> I have a similar, but older (BIOS 2008) AAO 110L (upgraded from 512KB to 1,5GB RAM) that runs great on Xubuntu 18.04.1. You must be realistic in your expectations though. I use my AAO 110L as my primary travel machine. Lubuntu should run well on yours also.
Oh believe me I'm realistic because picture Win7 Starter running on 1 gb of RAM and I limped this AAO for a long time and the SSD and 2 gb did wonders for the "Blue Circle of Sloth" and OMG!! What a miserable job to swap RAM without damaging the finish around the Keyboard while it is unsnapped from the retainers to lift out.
This is also my travel machine and spare backup in case I'm doing a major wipe and reload on my 970A SLI Krait edition with an FX8370 and I just got this and my Gigabyte M68MTS2 Rev 1.3 with an Athlon 640x4
It is amusing what we put up with for so long as I used to use my MSI K8TNeo2 with an FX5700LE AGP video card that I purchased new in 04 and only 4 years ago I threw a Toledo 4800+x2 (used of course) into it.

---

### Post by sudodus on 2018-11-23
> **hennmann said:**
> Lubuntu 18.10 looks very promising as I run it Live and I didn't have to configure ethernet at all, and my Wifi is working great. 

I suggest that you try Lubuntu 18.04.1 LTS as well as 18.10. [Try live before deciding what to install](https://ubuntuforums.org/showthread.php?t=2230389). Lubuntu is the lightest of the Ubuntu family flavours (much lighter than standard Ubuntu also as installed).
> 
Xenialpup64-7.5 is also fantastic and snappier I might add but doesnt support 32 bit computers like my IBM Thinkpad with 1280 megs of RAM and Intel 1500M processor. The biggest PITA is the PAE and newer flavors that support 32 abort and cry about PAE It's a PAEn in the @$$

Lubuntu (and the other Ubuntu flavours) can use the [boot option forcepae](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) to make it run on IBM Thinkpads with Pentium M processors with PAE capability but without PAE flag. Otherwise you can use Debian (or debian derivatives for example ToriOS) i386 versions with non-pae kernels. I think they are still released.
> 
Ubuntu 16.04.5 is somewhat sluggish like 18.0.4 in live but installed I'm not sure otherwise Lubuntu and Xenialpup are the best performers in Live. 

Try Lubuntu installed or persistent live in both cases with swap. I think you will like it.
> 
Now the older Puppy  Anita OS4.3.1 soared like eagles on both the Aspire and IBM but the internet browser wouldn't open but is very presentable. The earlier version of this 4.3.1 also worked very well on my old HP with the PIII800 and 128 megs of RAM and performed better than Win 2000. It is sad when older versions that rocked on smaller hardware are "discontinued" and should be able to be updated like the supported OS.

See also this thread, [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by ajgreeny on 2018-11-23
> **hennmann said:**
> Are you running this live or do you have it installed permanently on the hard drive? Permanently installing with a swap was the only way I could get Puppy 4.3.1 to run on my HP OmniBook XE3 with 128 megs of RAM and a PII800. It worked like it belonged on the HP as did extinct Mandrake 7.0
My slight advantage over your machine is 2 gigs and an Atom N455@1.66ghz. If I didn't know any better I would venture a guess and think you were running a slightly older Acer Aspire One that had XP or Linpus Lite on it?? I procrastinated too long and these were discontinued and ended up with the Win 7 Starter. The Linpus fascinated me being a gui slave despite the complaints about it but in reality a small Icon on the bottom corner allowed the gui desktop to be toggled to a conventional Linux desktop. I think I'm going to install 18.0.4 on this Acer to see if any improvement results instead of live. If I don't @*%! things up I can always install a lighter version later.
It is installed to hard drive and runs very well though not very fast.

The machine is a re-badged MSI 100U Netbook from UK company Novatech who produced this X10 - 10.1" Intel Atom N270 1Gb 160Gb Hard Drive back in 2010-2011.
It runs as you would expect of a machine with those specs, ie, good enough for browsing, email and video/music playing.

---

### Post by hennmann on 2018-11-23
Well I would say this is snail vs Olympic Snail
[http://cpuboss.com/cpus/Intel-Atom-N455-vs-Intel-Atom-N270](http://cpuboss.com/cpus/Intel-Atom-N455-vs-Intel-Atom-N270)
I will install Windoze Office 2007 Pro on my Krait,, and Gigglebyte,  setup Outlook Distress and transfer my PST backup file as to completely transfer all of my emails, contacts etc. and experiment on this Acer Despire One 533 because it has Win 7 Starter (Mild Sloth edition) Win10 Ult(Severe Sloth bordering on Snail on a cold day Edition) and a blank partition for a Linux flavor. I will see if everything sets up properly in case something gets bodged or knackered. The only thing of concern is I'm running a Win10 bootloader and hopefully Linux cooperates. 
As we are doing this response currently I'm running Zorin 12.4 Lite to see what it is like and for a so called lite it is somewhat sluggish compared to Lubuntu or Puppy but it is the same setup etc. as Ubuntu being a Blue flavor instead of purple with the startup menu. If all goes well I can always rip it out by the roots, install the Beaver for a test (what happened to the Penguin??) and If I fall asleep Lubuntu or a Dog. Windows has become sooooooo bad that people are attempting to decrapafy it using NLite. This is why we need Lite linux versions and I wish it wasn't too much to ask for a Puppy or Lulu for Ubuntu that looks the same with a Beaver on the desktopbut is Old Fogy computer friendly

---

### Post by kurt18947 on 2018-11-24
I just created a live USB of the LubuntuQT flavor. It used 480 MB. RAM and looks quite good. The GUI is traditional and it comes with mainstream apps.

---

### Post by hennmann on 2018-12-02
Xenenial Pup 7.5 is also available in 32 bit as well. I was informed about this on the Puppy Linux forum. 
NOW correct me if I'm wrong but it would appear much of the burden on older or smaller hardware using the latest and "greatest" OS  is WHAT is started up when the OS is initially started. A good indicator of this is on Windoze just take a peek into the processes running using "task manager". A bunch of garbage that is not needed until needed idling in the background. I have in the past disabled some of this crap by disabling it at the startup which can be done. Here is food for thought on this crap running when it need not be:
Go around your house and turn on your drier, A/C, all appliances etc. whether you need them or not so that "when you actually need them" they will be running and you won't have to wait a second or two for them to start! Sound far fetched? Not likely because the Xenial Pup has graphics comparible to Win 10 on my little Acer Despire One but boots and runs very fast all around. Win 10 has much crap running in the background making many users using NLite software to Decrapify it to a much needed "lite" version. It is no wonder why we need to upgrade hardware due to becoming slow. Vista was an excellent example. Hardware that flew with XP crawled with Vista and Windows 7 is very similar except it is a sweeter tasting lemon! What are we accomplishing here other than providing job security and income for hardware companies? Yes newer is faster, more efficient? and perhaps better but for many uses the older hardware was more than enough. Oh and is your CPU compatible? Minimum system requirements are far lower than my socket 939 4800+x2 Toledo Athlon but OH the CPU is supported for 32 bit but not 64 bit even though this is a true 64 bit processor. Sounds like Apple all over again when in order to keep your CS UNIX version "legal" you have to pay 3-4x the money for "their" hardware.

---

### Post by freemedia2018 on 2018-12-02
Your choice of desktop / window manager makes a great difference. If I take Refracta and then install IceWM, then I run free -m, it only takes 70m of ram on startup. 

If you then run a browser with noscript, 2gb of ram is very reasonable. It's awful that the web uses so much ram. YouTube is pretty modest compared to say, a Discourse forum. Very happy Ubuntu forums chose vBulletin over that mess.

---

### Post by hennmann on 2018-12-02
And then there are the ones with advertising video etc. or an extreme amount of garbage and graphics OMG! If you are using a cell to locate something it can be painfully and neeeeeeedlessly slow sucking up data usually with a limit to keep the monthly bill down!! Sad to say a number of flavors are very slow to start even before the browser is selected and oh yes have coffee on hand to keep yourself awake as things sloth along. This is Win10 on smaller hardware and apparently Microshaft has a lite version but is only available on their hardware I.E. Laptops. Hmmmmm is this Apple I see?

---

### Post by freemedia2018 on 2018-12-02
> **hennmann said:**
> Hmmmmm is this Apple?

It's GAFA-- Google, Apple, Facebook, Amazon.

---

### Post by anarchy-x on 2018-12-10
I'll have to jump on the bandwagon here and suggest Lubuntu. If you want a full LXQT experience get the latest, if you don't care and prefer the stability of an LTS and LXDE then stick with that. My Dell Latitude d630 runs Lubuntu 18.10 well.

There's also Linux Mint Debian Edition.

---

### Post by hennmann on 2018-12-30
After all is said and done I tried a number of flavors on my Acer with that anemic little Intel N455 Atombomb. Surprisingly the only top performer was Puppy Linux but during install I had problems with the boot loader and Windows or Pup wouldn't boot so in went Lubuntu to properly try it out. Windows came back to life and Lubuntu also was also running fine.

Now to my surprise is Lubuntu ran faster but in reality not surprisingly faster than Ubuntu 18.04.1. Also it wouldn't recognize or allow me access to my Windoze or spare NTFS partition I set up for storage that could be used by BOTH Windoze and Ubuntu. NTFS is mentioned as being able to be used by both.
Basically quite stripped down of goodies to say the least. In went Ubuntu 18.04.1 and yes it is a bit slower but very usable. A fair comparison would be Lubuntu is like driving a faster stripped down little rough riding economy  $h!tbox car with only a radio for options and Ubuntu is like a heavier luxury car filled with many accessories, options, and a smoother ride and less acceleration! A bit dramatic some might think but other members pointed out using Ubuntu on earlier smaller hardware than mine and getting on by.

In reality the software is just becoming more inefficient and more and more resource hungry and Win 10 is a perfect example of this! We shouldn't have to keep shoveling out more money for faster, bigger, more expensive hardware when it used to work very well in the past! I'm reminded of this when I purchased a new PIII450 with a whopping 6.4gb hhd in 1999 for $1000, and my Athlon 64 bit 3500+ in 2004 for another $1200 which I could barely afford but oh yes "supported" software is discontinued and this is years later after I purchased a used 4800+x2 CPU.
 I had Win7 Starter Edition dual booted with Win 10, (Win 10 bootloader)  and as the British would say everything got bodged when I attempted a triple boot with Ubuntu. No loss as it forced me to rip Win10 out by the roots and in reality brought my Acer down to a useless crawl all the while it made my computer look APPy like a damn smart phone instead of a PC!! I also upgraded my Win7 Starter to Home Premium as it gave me more options as well. Win 7 Starter Edition compared to Win 7 Home Premium is like Lubuntu and Ubuntu

---

### Post by sudodus on 2018-12-30
The choice of operating system depends pretty much on how you intend to use it. For example, Lubuntu is much better at playing video than standard Ubuntu in many old and/or weak computers. But there are advantages with standard Ubuntu too, and I understand that you have discovered enough of them to prefer standard Ubuntu :-)

Too bad you had problems with Puppy. It is often a good alternative, when all Ubuntu family flavours have too heavy footprints. By the way, have you tried TinyCore and CorePlus?

---

### Post by hennmann on 2018-12-30
No I haven't as there are many flavors out there!
One thing I had problems with on my IBM Thinkpad with an Intel M series 1.5ghz processor was that damn PAE problem! Some menus gave me the option of force pae many did not and would ramrod it directly into installation or live mode just to be aborted telling me to use force DUH pretty hard if you cannot!! Obviously a bug if a menu wont pop up?? Linux Lite, Zorin Lite 32bit, Ubuntu and a number of others fell into this category. Due to this and that past security scandal requiring patches I have acquired a dislike for Intel kind of like Apple with all of their shenanigans and older iPhones. Also AMD was 64 bit way before Intel which also gives more options as many OS are now 64 bit. I could run 64 bit on my socket 939 Athlon years ago!
The PAE was more of a nuisance and annoyance than my HP with 128 megs of RAM and not having USB as a boot option but PLop in the floppy drive got me around this. 
If the older software could run on older hardware with great results, Mandrake 7 was a great example of this with all software packages as well, why can't newer? It is sad when older Linux versions cannot be updated and when I was trying various versions to figure out what would work without that stupid PAE nag I had some that would install updates surprisingly but only so far. And then there is that asinine CPU not supported with Win 10!!! My Athlon 4800+ fell in this category where 32 BIT is allowed but not 64 bit. Older Intel and AMD with capabilities exceeding the so called minimal requirements. Total rubbish including so called "minimum system requirements" which my Acer exceeded but became a sloth or worse a snail in cold weather.

---

### Post by hennmann on 2018-12-30
Oh before I forget! The only problem with Ubuntu 18.04.1 on my Acer is the live worked very well all around but when it came to installation all went well except for the first time startup and under the Ubuntu logo with the dots, the cursor for my rodent would appear, then the cursor would freeze. Not knowing any better a reinstall did the same thing so I used the boot options, did a system update and now I use the Acer to respond to this thread.

---

