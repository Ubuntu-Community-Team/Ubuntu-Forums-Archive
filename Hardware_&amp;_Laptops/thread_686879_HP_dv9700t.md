---
title: "HP dv9700t"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by pblanton on 2008-02-03
I have just ordered a customized HP dv9700t laptop and I am waiting for it to be delivered.

The one I ordered has two 120GB, 7200 RPM drives in it and I was hoping I could install Gutsy on one of the drives until I can prove that it will run acceptably on the machine. I want the drivers for all of the laptop's goodies to work as expected before I delete the Vista partition and go 100% Ubuntu. That is my goal, to delete Vista with XP (extreme prejudice). :mad:

I am a software architect and spend most of my time developing for .NET, but I run my development environment (XP) in a VMWare image. I use Gutsy as the host operating system on my current laptop (a Dell XPS Gen2) and it runs fine, but it is time to replace my laptop and am hoping that Gutsy will run and properly drive the new machine. I always have trouble and head-pain installing Ubuntu on a new machine, but once its up and running I am always happier with it than I am on Windows.

The current sticky threads about the HP laptops say that Gutsy doesn't work right on the dv9700t's closest relative, the dv9500t. :(

I guess what I'd like to do is to create a new website or page somewhere that contains a how-to for installing ubuntu on each current model laptop in the market. I don;t want to dig through a huge thread reading questions and answers, I want a nice, formatted, how-to that is built from people's real-life experiences with the process.

I am willing to offer my new machine as a guinea pig for the dv9700t how-to, I just need help geting this started. :)

---

### Post by CalcProgrammer1 on 2008-04-12
Are you still trying to install Ubuntu on this PC?  I just ordered a dv9700t with C2D T9300 (2.5GHz/6MB L2), 3GB DDR2 RAM, nVidia 512MB 8600M GS, 17" 1680x1050 LCD, Intel Pro Wireless + Bluetooth, and HP ExpressCard TV Tuner.

I don't plan on completely wiping Vista (this is going to be my college laptop, and I'll probably need M$ Office, etc.)  but I do want to run Ubuntu on it.  If you've gotten it to work, please explain how well it works (what did it take to make it work, etc.).

From what I've read, I don't see why it wouldn't work, as I've looked up Linux compatibility for Intel Pro Wireless, 8600M GS card, etc. and most all of the dv9700t's components are Linux-compatible.  Maybe if Gutsy doesn't support it, Hardy will (I'll have Hardy before I get the machine anyways, so that's what will go on it).

EDIT:

Once I get mine, I'd be glad to help write a how-to or tutorial page on installing certain things.

---

### Post by Hammerheart on 2008-04-13
I have a dv9700t that I ordered a couple months ago.  I had a few problems Gutsy(dont remember what anymore) but everything works flawlessly out of the box with Hardy.  I used the gparted boot cd to repartition my hard drives to keep a Vista partition as well.

---

### Post by CalcProgrammer1 on 2008-04-20
I finally got my dv9700t (it's incredible!!!!!!!) and I tried Ubuntu 8.04 Alpha 3 (the only CD of 8.04 I had).  It seems to work very well (Wireless supported without restricted drivers?!? I haven't experienced the awesomeness of Intel yet!) and I hope the 8600M GS is supported by nVidia's driver, but I don't think it'll be an issue considering how good the nVidia driver is.  I haven't installed it yet, but I plan on getting rid of the stupid "recovery partition" (burned DVD's already, so I can backup from those) and turning it into a Linux partition when 8.04 releases in a few days.

I still haven't checked to see if the webcam, fingerprint reader, or ExpressCard TV tuner work in Ubuntu yet, but I'll try those when 8.04 comes out.

---

### Post by BrokenPoet on 2008-04-23
Any updates on how the dv9700t's are shaking out?  I am considering a setup that matches CalcProgrammer's (T9300 CPU, Nvidia 8600), but haven't made the plunge yet.

---

### Post by pblanton on 2008-04-25
> **BrokenPoet said:**
> Any updates on how the dv9700t's are shaking out?  I am considering a setup that matches CalcProgrammer's (T9300 CPU, Nvidia 8600), but haven't made the plunge yet.

Yeah! It's a dream with 8.04. I bought the version with two drives so that I could experiment with ubuntu on it. I prefer to run Linux as my main OS. Since I am a .NET developer though, I must run Windows most of the time. I do it with VMWare.

My concern was that the nifty features of the HP laptop wouldn't work under Linux so I kept Vista on my first drive and installed Hardy Beta on the second. Everything tested so far works flawlessly! 

The fancy touch sensitive volume, stop, pause, play ff and rw buttons all work perfectly with Hardy, right out of the box.

The webcam also works perfectly. I haven't yet tested the microphone, but I assume it will work because it's not that complicated a piece of hardware. I also haven't tested the fingerprint reader, but I expect it will take some convincing to get it to work. Not a huge loss, but I'd still like to have it available.

I have since ugraded to the official release of Ubuntu 8.04 and things are sweet. I am going to run it like this for a couple of weeks, and if everything continues to work as well, I'll blow away MS Vista and use that drive for my VMWare images.

While everything tested so far works fine, the transition isn't without difficulties, as described below.

One problem is that I installed the 64-bit version of Hardy, and Skype isn't available for 64-bit Linux. Obviously Linux doesn't have the same 32-bit compatability layer that Windows does, so I just get an error during installation, that the 64-bit platform is not supported. Bad Skype!

Since I use Skype all day long, I will need to run it in a Windows virtual machine until I can get a 64-bit version. Or, does anybody know how to run a 32-bit application on 64-bit linux?

I presume that 32-bit Ubuntu users won't have a problem with Skype, especially since I have always had no problems using Skype in Linux before I switched to 64-bit; but what's the point of having a 64-bit laptop if you are going to run a 32-bit OS?

I also had trouble with my Microsoft Bluetooth Notebook Mouse 5000. I solved it here...

[http://www.siberian.ws/linux/microsoft-bluetooth-notebook-mouse-5000-in-ubuntu-linux/](http://www.siberian.ws/linux/microsoft-bluetooth-notebook-mouse-5000-in-ubuntu-linux/)

Read the comments though, because the instructions aren't complete, and there is an OBEX error in Hardy that I commented about a fix to down below.

My laptop?
A customized HP DV9700t with...

- Intel(R) Core(TM) 2 Duo Processor T7500 (2.20 GHz, 4 MB L2 Cache, 800MHz FSB) 
- 17.0" WSXGA+ HD BrightView Widescreen Display (1680 x 1050) 
- 4GB DDR2 System Memory (2 Dimm) ordered with 2 and upgraded myself. much cheaper than ordering with 4.
- 256MB NVIDIA GeForce 8400M GS 
- Radiance Imprint Finish 
- Fingerprint Reader + Webcam + Microphone
- Intel(R) PRO/Wireless 4965AGN Network w / BluetoothTM
- 240GB 7200RPM SATA Dual Hard Drive (120GB x 2) 
- HD-DVD ROM with SuperMulti DVD+/-R/RW Double Layer

Here's a pic of it running Hardy Heron:
[IMG]http://alilimbali.com/images/lappy.jpg[/IMG]

I can't recommend the HP dv9700t highly enough. It is the best laptop I have ever had. :)

Good Luck!

---

### Post by #Reistlehr- on 2008-04-26
yeah nothing but kernel panics with the dv9700z (AMD) with hardy

---

### Post by pblanton on 2008-04-26
I'm sorry to hear that. I used to use only AMD processors back in the P4 days. I wonder what causes Hardy's kernel to be so panicky.

My Intel-based dv9700t has been running now for days without a hitch.

---

### Post by blumagic on 2008-05-04
I have been using dual booting with Gutsy for the past couple of months. I am wondering if Hardy acutally has figured out suspend and sleep mode with this laptop.

thanks,
blu.....

---

### Post by DrViper on 2008-05-06
> **pblanton said:**
> Yeah! It's a dream with 8.04. I bought the version with two drives so that I could experiment with ubuntu on it. I prefer to run Linux as my main OS. Since I am a .NET developer though, I must run Windows most of the time. I do it with VMWare.

Hello,
Recently I bought a HP DV9700t CTO like yours, but with GForce 8600 and Lightscribe DVDRW.
I need know about:
*Fingerprint Reader
*Webcam
*Microphone
*Quicktouch buttons
*Remote Control.
*Bluetooth
Are these itens working in Ubuntu?
Are your ubuntu x64?
Regards

---

### Post by #Reistlehr- on 2008-05-12
Remote control and bluetooth work out of the box. most likley the microphone works, its just most likley muted by default. webcam should work using how to's on the forums. Quicktouch work also, with the default applications (ex: rythmbox). Fingerprint reader is not supported that i know of.

---

### Post by Cheshirecat86 on 2008-06-23
Hi, guys!
I've got a problem. Maybe you could help?
I have HP dv9700t laptop.
I have always been using Windows OS, but recently decided to try Linux.
I downloaded the Ubuntu image file (ubuntu-8.04-desktop-i386.iso), burnt it to DVD disk.
Then I restarted my laptop and booted using this disk.
After I had chosen to start the live Linux (without installing it).
 It first showed me the Ubuntu Logo animation and then black screen with many error messages. I have tested my memory (in case that was a memory problem), but it didn't find any errors.
 I have attached a photo of my screen with those messages on it.

 Could you help me please, I see the guys in this thread have the same laptop as me and no problems running Ubuntu. What is wrong here?
  By the way, I didn't try to install it. First I want to know the reason of this mistake.

My laptop's configuration:
HP dv9700t
Intel Core 2 Duo T9300 2.5 GHz
Ram 2GB
Dual HDD 120Gbx2=240Gb total 7200rpm
Video Nvidia 8600M GS 512Mb
Wi-fi BGN
Bluetooth
Fingerprint scanner
6 cell battery
17'' 1650x1080 display

THANK YOU IN ADVANCE!

---

### Post by Cheshirecat86 on 2008-06-23
By the way I tried downloading and burning the iso twice, but it didn't help. :confused:

---

