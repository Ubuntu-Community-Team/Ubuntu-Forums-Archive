---
title: "Can Ubuntu be installed on a HP DV5 1170...?"
date: 2009-03-10
forum: Hardware
---

### Post by AlexVader on 2009-03-10
Hi Forum

Has anyone managed to install Ubuntu on an HP Dv5 1170...?

I am asking bcause I plan to buy this lap, but it comes with the W%%&$# Vista  nstalled and MicrosHit IS NOT AN OPTION.

So I was considering to install Ubuntu 8.10 or 8.04 or 7.10 in the AMD64 architecture.

Do I have to tweak the bios for the laptop to recognise my install DVD? or can I just put it in the DVD reader and go on with the install...?

How about restricted drivers for the hardware...?

I am planning to switch from my old Asus F3JR, Ubuntu compatibility is 100%, but hardware ( shitty plastic construction of the Laptop ) is a sad joke...  :-(

Would You advise me to buy this HP Dv5 1170... for Engineering applications use under Ubuntu OS...?


Best regards

Alexandre


So here is the thing:

Installing Ubuntu 8.10 AMD 64 in a HP Pavillion Dv5 1170, specs are :

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9600M GT (rev a1)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

Graphics card and Wireless are configured out of the box


Had a small trouble ( guess it is something to do with kernel and loading the module of my wired connection ) Installing and configuring ProEngineer Wildfire 3 for Linux: The license manager would not lock with my ethernet unless i was connected...  solved it like this : 

Quote :

[B]zika  	December 20th, 2008 02:13 AM
Re: Ubuntu 8.10 Network Manager Doesn't Recognize Wired Network Device
 
this is what worked for me in october when I updated from 8.04 to 8.10 and lost all networking also:

Code:
sudo nano /etc/network/interfaces
then make this file look like:

Code:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface DHCP
auto eth0
iface eth0 inet dhcp
or, if You need static address:
Code:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface static
auto eth0
iface eth0 inet static
    address xxx.xxx.xxx.xxx
    netmask xxx.xxx.xxx.xxx
    gateway xxx.xxx.xxx.xxx
    broadcast xxx.xxx.xxx.xxx
andcode] sudo nano /etc/resolv.conf[/code] and make it look like:
Code:
nameserver xxx.xxx.xxx.xxx
with Your DNS ...

then restart networking (or start, since it's not working) with:

Code:
sudo /etc/init.d/networking restart
or
Code:
sudo ifdown eth0
sudo ifup eth0
that way You might see a orange triangle on Network manager or no NM at all but have working connection. You can prevent NM from showing up by disableing it in Preferences->Sessions->uncheck Network Manager.

hope You'll have lasting network connection and forget about NM.
[/B]

I did not yet try to solve some strange sound in the speakers at shutdown, nor did i test the suspend to ram/hibernate features...

I only need the basic functionalities for this laptop, my work with it is as a Mechanical Engineer, meaning that having the GPU working, as well as my wireless to install/upgrade packages as well as the full power of the AMD64 OS is enough for my needs...  :-D

Hope this helps

Alex

---

### Post by knattlhuber on 2009-03-10
Hi Alexandre
I'm not familiar with that particular laptop.
What graphics and WLAN card does it use? These two components are the ones that may cause problems.
Generally speaking HP laptops/desktops work fairly well under Linux (I have 3 HP computers myself running Ubuntu).
You don't have to do any tweaks to have it recognize the Ubuntu CD/DVD.
I don't know about engineering applications under Linux, sorry.
My personal opinion re: the architecture: Go with the 32-bit version. I used AMD64 for 6 months and the little problems that come with it (Java, Flash, the odd application that doesn't support 64-bit etc..) offset the speed gain for me. Just my 2c worth.

---

### Post by AlexVader on 2009-03-10
Hi there,

The GPU is a NVIDIA GeForce 9600M GT, and the WLAN is a WLAN 802.11b/g.

I Have already all my engineering apps for Linux, they all run OK under 7.10 x32,

Pro Engineer, OpenFOAM, Fluent, Adina, Matlab and ABAQUS plus a lot of "in-House" specifically built codes to deal with Detonation, Fluid Structural Optimization, and the like.

My "Thing" with AMD64 is that X32 cannot ( can it...?! ) access the 4GB RAM, ( i plan to increase it to 8GB if needed ) and my applications are "HardCore" memory and processor intensive : A simple simulation of a Diesel Engine in-cylinder ignition with chemical kinetics and CFD modelling can take days to complete ( lucky me that can interrupt and make a restart... :-) ) and a low resolution mesh can take one GB of RAM, High resolution meshes are dealt with in the Lab Cluster...


Can a X32 Distro "reach" for my actual 4GB ram...?

---

### Post by Dark_Stang on 2009-03-10
x86 isn't going to utilize 4+Gb of memory. I'd suggest trying 8.04 x64 first. If it's a new laptop it's not like you're going to lose that much data if you mess up partitioning anyway.

---

### Post by AlexVader on 2009-03-10
Thanx a lot for the hint  :-)

I will buy this lap this or maybe next week...

I'll tell here how it went on, the install.

BRGDS

Alex

---

### Post by Dark_Stang on 2009-03-10
> **AlexVader said:**
> Thanx a lot for the hint  :-)

I will buy this lap this or maybe next week...

I'll tell here how it went on, the install.

BRGDS

Alex
Do report back how it goes. As far as I know, I was the first person to run Linux on the exact model of laptop that I have. It's a little scary but once I got 7.10 up and running on it smoothly I blew Windows away. I've been happy ever since.

---

### Post by knattlhuber on 2009-03-10
> **AlexVader said:**
> Hi there,

The GPU is a NVIDIA GeForce 9600M GT, and the WLAN is a WLAN 802.11b/g.

My "Thing" with AMD64 is that X32 cannot ( can it...?! ) access the 4GB RAM, ( i plan to increase it to 8GB if needed ) and my applications are "HardCore" memory and processor intensive

Can a X32 Distro "reach" for my actual 4GB ram...?

In that case, by all means use the AMD64 version.
The NVIDIA card should work fine. For the WLAN, it depends on the chipset that the card uses. I googled the laptop and I couldn't find any more details than what you listed. It's probably gonna be OK, you can get pretty much any standard WLAN card working under Linux.. it's just that some require more effort than others to get them to work..

---

### Post by knattlhuber on 2009-03-10
It looks as if the WLAN card used in that laptop is a Broadcom:
[http://www.laptoprepairparts.com/html/details.asp?ref=1970&category=boards](http://www.laptoprepairparts.com/html/details.asp?ref=1970&category=boards)

I never had a WLAN card with a Broadcom chipset but it seems they are a pain in the rear. Maybe somebody else can comment on that?

---

### Post by superubu on 2009-03-10
l got a similar machine few days ago , same wlan 802,11ng ,amd 64bit ect....needs a bit of extra work but seems everything is going well :

dont waste time with the winzoz drivers wlan works with( iwlwifi-5000-ucode-5.4.A.11.tar.gz) , you will need unistall and reinstall the drivers every times you turn off the pc (not the reboot only shut down) unless you don t blacklist original drivers

i m still working on the 3d effect ..i must turn off magic effect when i wacth movie

can not reconize integrated microfone but the web is ok 

all the rest seems fine ....l m still checking the macchine let s keep in contact after you will buy the monster !!!

---

### Post by AlexVader on 2009-03-11
Hi Knattlhuber,

U mean Broadcom is a pain in the *** like what...?! reliability issues, configuration issues, linux drivers availability...?

BRGDS

Alex

---

### Post by AlexVader on 2009-03-11
Hi Superubu,

So, just tell me which 'buntu did u install? 7.10, 8.04 or 8.10...?
Doesn't the kernel module get loaded at boot time ?

Is there no restricted driver for this wlan yet...?

BRGDS

Alex

---

### Post by AlexVader on 2009-03-11
Hi DarkStang...
 
As soon as i get my hands on the lap i'll get back in touch...

First time install will be to an external USB w/ 100 GB using the Alternate version of 8.10 AMD64...

BRGDS

---

### Post by AlexVader on 2009-03-11
Hi DarkStang

As soon as I lay my hands over the "device" I will keep the forum informed on the progress...

My first attempt will be to install to an external USB HDD w/ 100Gigs, using the 8.10 AMD64 Alternate installer...

BRGDS

---

### Post by knattlhuber on 2009-03-11
Hi Alex
I have never used a Broadcom WLAN card so I don't have any first hand experience. From what I read on these forums it seems though that *some models* require a lot of tweaking before they work under Linux.
Mind you, I'm not even sure if that laptop in question uses a Broadcom chipset. The link that I posted shows that other HP DV5 models obviously use it, but that may of course change anytime.
What superubu meant I guess was that you have to blacklist the default WLAN driver to make the new one (whichever that is..) work. Otherwise, the Ubuntu kernel will fall back on the old drivers. I'm not sure though why that would happen only after shutdown and not a reboot..

---

### Post by knattlhuber on 2009-03-11
superubu, would you mind running

```
lspci | grep Network
```

in a terminal and post the output?

---

### Post by AlexVader on 2009-03-14
Hi Knattlhuber

Well :-D, seems our friend superubu is afraid of what lspci | grep Network may do to his system lol....  :-)

Changing subject, I am getting way scared of this crapware called 802.11b/g...  :-(

Is it true that there are no linux drivers available to this Wirless card...  ?

Man, it is in times like this that I really hate Bill Gates with all my guts...  >-0

so... no wirless for Ubuntu with a 802.11b/g...   without resorting to ndiswrapper.. at least...

Do you think it would be a wiser choice to shift from the HP Dv5 1170 to the HP Dv7 1160...?

At least, the wifi card is an Intel WiFi Link 5100...


What do you suggest me to do...?

Thanks in advance...

Alex

---

### Post by orethrius on 2009-03-14
Technically speaking, ndiswrapper *is* a restricted extra: it loads drivers that are only legally utilized with a valid copy of Windows, though I doubt it's ever been specified that you need to have that "valid copy" loaded (or even on your machine, but that's an almost unacceptably loose interpretation). ;)

If you're going for a totally free and functional system, depending on the chipset, b43 or b44 might be of some relief; otherwise, as I've said before, ndiswrapper is okay as a stop-gap (unless people seriously suggest that Broadcom users go without decent wireless because of politics).

---

### Post by AlexVader on 2009-03-14
Hi Orethrius

Where do I download the b43 or b44 drivers from...? I did not find it in the wirleless drivers link in BroadCom home page...

Alex

---

### Post by jocko on 2009-03-14
> **AlexVader said:**
> so... no wirless for Ubuntu with a 802.11b/g...   without resorting to ndiswrapper.. at least...
802.11b/g is not a specific wireless card, it just tells which standards it uses for wireless communication.
My Intel PRO/Wireless 3945ABG (which uses the 802.11a/b/g standards) works perfectly well under ubuntu.
To be sure there will be no problems, you need to find out exactly which wireless card the laptop has.

---

### Post by AlexVader on 2009-03-14
Thks for yr reply...

I am just watching from the specs...

Hp site info on the DV5 1170 just states it is a BroadCom 802.11b/g WLAN...

And as far as I can see in the forum.. BroadCom Wireless Cards are a pain in the ***...  BroadCom releases no drivers for it...  :-(

---

### Post by Dark_Stang on 2009-03-14
> **knattlhuber said:**
> It looks as if the WLAN card used in that laptop is a Broadcom:
[http://www.laptoprepairparts.com/html/details.asp?ref=1970&category=boards](http://www.laptoprepairparts.com/html/details.asp?ref=1970&category=boards)

I never had a WLAN card with a Broadcom chipset but it seems they are a pain in the rear. Maybe somebody else can comment on that?
I've never had any issues setting up broadcom cards. Either the kernel drivers work or you can use ndiswrapper with the windows drivers.

---

### Post by Rayne_ on 2009-03-15
I am currently using a HP Dv5 1000 series laptop with the NVidia 9600 and Intel Corporation PRO/Wireless 5100 AGN wireless card. After enabling the restricted drivers for the video card, graphics effects worked fine. I am using 64bit version and installed the 32bit libs for the few applications that aren't working with the 64bit system. Wireless card worked right after install. The volume slide and mute buttons work perfectly as well. The only parts I am still working on fixing is the built in microphone, HDMI output, TV Tuner and card reader. I am currently working on those now, if you are interested in solutions (should I find them) let me know and I can post them for you.

---

### Post by AlexVader on 2009-03-15
Hi Rayne_

I pretty much appreciate yr help, but I think u wont be able to help me with the crooked issue: The BroadCom 802.11b/g thing;  Like you said, you are the lucky owner of a laptop that posesses a wifi card for which there exists a restricted driver... unlike me ( I am not yet, I will only buy the laptop in 4 days...) 

I am seriously considering buying the HP Dv7 1160 instead of the Dv5 1170 just because of this...   

Does Ubuntu ( 8.04 or 8.10 ) has any kind of support for BroadCom wifi...?

So far I have found nothing...     :-(

Alex

---

### Post by orethrius on 2009-03-16
> **AlexVader said:**
> Hi Orethrius

Where do I download the b43 or b44 drivers from...? I did not find it in the wirleless drivers link in BroadCom home page...

Alex

You won't be able to pick those up from Broadcom, they're restricted third-party drivers.  It all comes back to needing the archived drivers from Broadcom, since you can use b43-fwcutter (**sudo apt-get install b43-fwcutter**) to cut the firmware you need, or use ndiswrapper to load the Windows drivers.  To do that, though, you'll need a tool called **cabextract** to run against the driver archive; it's a part of the WINE project, and should be in the main repositories.

Incidentally, from [this document](http://h10032.www1.hp.com/ctg/Manual/c01550108.pdf) (HP manual link), the system you're looking at uses a Broadcom 4312 chipset.  I can attest to the fact that ndiswrapper works fine with the 4318, but I can't be sure about the 4312 (though there's not much variance; for a time I used the 4311 drivers with little difficulty).

Additional Resources:
[Ubuntu Forums thread](http://ubuntuforums.org/showthread.php?t=652999)
[Driver Download](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe) (HP Direct FTP link)

It seems that we would share a common driver in bcmwl5.inf until the open driver team for Broadcom cards figures out the rest of the chipset.  I'd love to toss debugs their way if anyone bothered to ask for them. :)

---

### Post by AlexVader on 2009-03-16
Ok Orethrius,

Think I found a possible ( less tweaky ) solution... :

According to that document in the link, all Intel laptops come with the BroadCom thing, while the AMD laptops come with the Atheros thing.

The trade off is that the AMD laptops ship with an ATI Mobility Radeon HD 3450 GPU, instead of the Nvidia...


As far as I could figure out in the forum, there exists a restricted driver for Atheros in Ubuntu, unlike with BroadCom...

...Also, as far as i understand, the AMD Turion X2 is a real 64 bit architecture, unlike the Intel Core 2 Duo P8600 which is only EMT... ( doesn't fully support 64 bits instructions.. )

Since the target use for my laptop will be heavy and intensive numeric simulations for engineering ( Computational Fluid Dynamics, CAD and Finite Elements Analysis ), i guess that the HP Dv5 1210 is probably a wiser chice...  wouldn't you agree on this...?

Only concern here is that some of the proprietary software I use is supported under Intel EM64T architectures or AMD Opteron Atchitctures... The issue then is :  Do AMD Turion X2 ZM82 CPU support the instruction set of AMD Opteron ...?

Alex


Alex

---

### Post by orethrius on 2009-03-16
> **AlexVader said:**
> According to that document in the link, all Intel laptops come with the BroadCom thing, while the AMD laptops come with the Atheros thing.

I thought that when I first checked page 5, too.  However, if you check page 4, it's a bit more clear:
* Intel models only ship with Broadcom.
* AMD models can ship with Atheros OR Broadcom.

[quote=AlexVader]The trade off is that the AMD laptops ship with an ATI Mobility Radeon HD 3450 GPU, instead of the Nvidia...[/quote]

Right, that much is in-line with the document.

[quote=AlexVader]As far as I could figure out in the forum, there exists a restricted driver for Atheros in Ubuntu, unlike with BroadCom...[/quote]

I think it really all comes down to whether you're concerned with keeping the kernel itself untainted by proprietary code or licenses.  If you use Broadcom, you'll probably have to use closed drivers for immediate full functionality; if you use Atheros, you'll have to deal with licensing issues regarding software patents on the code itself.

As for the rest of your post, unfortunately you've left my area of experience, and all I can offer are uneducated guesses.

---

### Post by Dark_Stang on 2009-03-19
Are you sure it's a 4312? If it is...
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)

---

### Post by AlexVader on 2009-03-19
Hi Dark_Stang

I think i can work things out... watch this... :

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

BTW, bought my lappy this morning...  :-)

When I get back from TKD training, I will bkup my Vistugh OS ( so as not to void warranty in case I need to reinstall that crap ) and try my Live DVD 8.10 installer to see how it goes on...

I'll keep in touch just to say how it went on...  :-)

BRGDS

Alex

---

### Post by AlexVader on 2009-03-20
Hi Forum,

I Have been thorough testing my lappy using Vistugh tools, just to get sure if it was shipped without any kind flaw, also created my bkup DVDs so as not to void warranty.

Just before I nuke the MShit partitions away from my HDD, I will try with the alternate installers, ( they allow me to write the MBR to an external HDD, and install Ubuntu to an external medium... Will start 'buntu testing this night, and will take my weekend through... )

Ran the 8.04 AMD64 liveDVD installer and it warned me I should use the wl restricted driver...  but wifi neworks were not identified.

Will try the 8.10 AMD64 LiveDVD and the 9.04 Desktop LiveCD ( it is a live CD, right... ?! )

Monday I will report some ( wishful ) good news... :-)

Alex

---

### Post by AlexVader on 2009-03-20
Hi Forum

BREAKING NIEWZ :

Ubuntu 9.04 Desktop AMD64 Nightly Build successfully recognised graphics card, and Wireless in my HP Dv5 1170....  :-D

When is stable release scheduled to take place  ... ?

Alex

---

### Post by Dark_Stang on 2009-03-20
> **AlexVader said:**
> Hi Forum

BREAKING NIEWZ :

Ubuntu 9.04 Desktop AMD64 Nightly Build successfully recognised graphics card, and Wireless in my HP Dv5 1170....  :-D

When is stable release scheduled to take place  ... ?

Alex
That is good news. Here is the release schedule for 9.04.
[https://wiki.ubuntu.com/JauntyReleaseSchedule](https://wiki.ubuntu.com/JauntyReleaseSchedule)

Is the wireless up and running?

---

### Post by AlexVader on 2009-03-21
Hi Dark_Stang

Yup, Wireless works like a charm... GPU gives me the 1280x800 out of the box...

Now I will play with past distros...  like 8.10, 8.04, 7.10 and 7.04...

I want my lappy to be the fastest m*f*cking number crunching device among the PhD ppl laptops in my department...  :-)

Necessary steps are :

1.Avoiding a heavy kernel with lots of unneeded stuff.
2.Recompiling the kernel
3.Staying the f away from KDE's and Gnomes... using WindowMaker, or FluxBox

3.Recompile my OpenSource codes with tweaked flags for boosted performance...

but I have seen some remarks concerning degradation of performance in the more recent versions of Ubuntu... according to a Phoronix benchmark test, the fastest of all 'buntus was the 7.04 AMD64...

If i could manage to get 7.04 to use my wireless and my GPU...  :-)  Already have the Nvidia driver for ia64 arch, but i still dunno if kernel of 7.04 will accept the module compiled with broadCom BCM4312 firmware driver...

Do you have any experience on this...?

BRGDS

Alex

---

### Post by Dark_Stang on 2009-03-22
As far as I'm concerned, I think most of the degradation comes from the more intense desktop environments. 6.04, 6.10, and 7.04 didn't really have heavy desktop environments. 7.10, 8.04, 8.10, and 9.04 all use much heavier GUIs. My installs start from 8.04 minimal. This loads the kernal, apt-get, vi, and a few other packages. Then on top of that I install everything else I want... gnome-core, vpnc, powernowd, hotkeys, compiz, etc.

That being said, I like compiz. If I didn't have compiz my boot time (from after the POST screen to my desktop) would be 15-18 seconds. Compiz adds another 20 seconds to my boot time. If you want it light and fast, I'd say install Ubuntu minimal then get fluxbox and just run with it. On my old Acer Aspire 2005wlmi that I had I used to run 6.10 with fluxbox to keep it fast. However now I'm sitting on a laptop with plenty of poewr, so I like to keep it fancy.

As far as compiling kernels go... I used to do it. I did it on the Acer. I wanted to keep a custom k7 kernel to keep it fast. But now that I'm running a 64bit AMD processor, I just install the AMD64 kernel. I compiled a kernel once for this laptop a long time ago, and didn't feel any difference. Actually it became more of a pain because I had to be really careful about what packages I was updating or I might break my setup.

And for compiling/recompiling software, go for it if you want to. But be prepared to wait a long time for certain things to compile. I'm an impatient person... that being said, I'm also a computer science major trying to specialize in operating systems and software devolpment (c/c++, java, scheme, prolog, whatever). I understand that if you compile everything from source you're going to have an amazingly fast computer and everything is going to run great. However... I've also been stuck in dependancy hell. I've hacked things together. I can hack things together. But to be honest, what's important to me is simple... I just want it to work... I want it to work well, work fast, work right the first time, work right every time after that, and work now.

If I had more free time I might feel differently. However as a full time student and as a full time employee working for a very well dressed nationwide computer task force, my free time is null.

Edit: As far as the bcm-fwcutter stuff goes, not sure how that works if that's what you're using. I also don't know what kernel 7.04 is up to these days, so it may or may not have the latest broadcom drivers in it natively. However you could definitely use ndiswrapper for it, but you'll have limited functionality of the wireless card.

---

### Post by AlexVader on 2009-03-22
Hi Forum

SUCCESS  :-D

I have successfully installed 8.10 AMD64 on my HP Dv5 1170

GPU and wireless work out of the box....

I will now test if my proprietary software that used to work in 7.10 will work here...  but this is a whole different issue...

Open Source Software will sure work... it will be recompiled...

Best regards

Alex

---

### Post by Dark_Stang on 2009-03-26
Don't forget to write up a how-to guide if it requires any extra hacking. Also, edit your first post if you can so people don't have to search through several pages to know whether or not this works.

---

### Post by AlexVader on 2009-03-27
Hi Dark_Stang

I guess that i am satisfied with the lappy and compatibility with Ubuntu 8.10 AMD64, wrote a short summary anyway...

Thx a lot ...  :-)

Alex

---

### Post by Zemren on 2009-06-28
Hi everyone, i navigated to this thread due to the fact that i experience poor performance in graphics and wlan, im a first time linux user running ubuntu jaunty on my HP dv5 1037 and my question is what "Ubuntu 9.04 Desktop AMD64 Nightly Build"  that was reffered to in this thread is?
Please remember im a first time user aswell so be eduocational when explaining.

---

### Post by K3N8 on 2009-06-30
> **Zemren said:**
> Hi everyone, i navigated to this thread due to the fact that i experience poor performance in graphics and wlan, im a first time linux user running ubuntu jaunty on my HP dv5 1037 and my question is what "Ubuntu 9.04 Desktop AMD64 Nightly Build"  that was reffered to in this thread is?
Please remember im a first time user aswell so be eduocational when explaining.Hi,

I have tried several ubuntu versions for my HP Pavilion dv7 laptop. Ubuntu 8.10 Intrepid 64 bit is the one that works the best for my laptop. After installing Ubuntu don't forget to install linux-backports-modules-intrepid-generic. That package will make sure that WLAN works.

Good luck,

Alexander

---

### Post by Zemren on 2009-07-05
> **K3N8 said:**
> Hi,

I have tried several ubuntu versions for my HP Pavilion dv7 laptop. Ubuntu 8.10 Intrepid 64 bit is the one that works the best for my laptop. After installing Ubuntu don't forget to install linux-backports-modules-intrepid-generic. That package will make sure that WLAN works.

Good luck,

Alexander

Hi Alexander and thanks for the tip i will try it out, since i posted in this thread i have switched to the amd64 version but that made no difference at all, while downloading i reach the same speed as im used to but while surfing the web its significally slower than windows. Also the graphics are way of, while watching a movie in vlc i cant move the window without problems and launching to full screen takes for ever with poor fps.

Well ill try go for 8.10 to see if that makes any difference, thanks.

---

