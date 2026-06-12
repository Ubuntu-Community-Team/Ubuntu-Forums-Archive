---
title: "Laptop that works with Ubuntu"
date: 2006-05-13
forum: Hardware &amp; Laptops
---

### Post by ronan on 2006-05-13
Hi everybody

I want to buy a laptop at the end of summer.

I would like to install Ubuntu on it.

Which ones will be better ?

Can you share your experiences about your laptops and Ubuntu.


Thanks

---

### Post by MetalMusicAddict on 2006-05-13
Please search the forum for many threads on this subject.

---

### Post by bluto on 2006-05-15
I just installed Dapper flight 7 on a dell B130, low end laptop (512MB ram, 1.5 GHZ celeron M, 60  GB drive, 15.5" screen) and the performance is outstanding.  With just a little digging  in this forum I was able to get the 1280 x 800 screen resolution and sound working in an hour.  I am a software developer and use the notebook as backup for my desktop work and for traveling. The compile times are very respectable.  This is a low end notebook, $530 if you look thru the Dell sale stuff.

---

### Post by K.Mandla on 2006-05-15
I've had good luck with most of the Dell systems I've worked with too. I'm using a heavily modified Inspiron 8000 now, but I've also put Breezy and Dapper on an M170 and a 600m. The worst situation was with pre-Pentium III machines, but that was a kernel issue, and not the fault of Ubuntu.

---

### Post by Sef on 2006-05-16
Go with system76, they install Ubuntu on your system for you, so you know everything works.

[http://system76.com/]("http://system76.com/")

---

### Post by jturnbul on 2006-05-16
i use a toshiba m30 with zero problems

---

### Post by Mr Fat Bat on 2006-05-16
Running a Dell 6400 Dual core 2 GHz, Wifi and ATI Graphics with no hitches except the damned card reader (see sig below =)

---

### Post by mips on 2006-05-16
[QUOTE=ronan]Hi everybody

I want to buy a laptop at the end of summer.

I would like to install Ubuntu on it.

Which ones will be better ?

Can you share your experiences about your laptops and Ubuntu.


Thanks[/QUOTE]

What is your budget ?
What are your needs/requirements/spec ?

---

### Post by frodon on 2006-05-16
Don't forget to have a look the wiki and the UDSF, you will get useful informations : 

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)
[http://doc.gwos.org/index.php/HCL](http://doc.gwos.org/index.php/HCL)

---

### Post by shrimphead on 2006-05-16
asus M5N for the win

just updated to dapper and the machine couldn't be better if it tried :lol:

---

### Post by ronan on 2006-05-17
Hi

Thank you everbody for your answers.:) 

Blitto: Can you give me more information about your laptop ?
Did you customize it on Dell online store ?
Does the DVD playing work well ?
Does Wifi worked out of the box ?
Have you any problem with hibernation, standby mode ....

Which link did you follow in order to get your screen working as you wanted ?

Thank you

My budget is 1000$ but cheaper is better. 800$ will be great.

I would like to know if 1,7Ghz with 512MB RAM is enough for ubuntu and Gnome/KDE ?

Pentium M or Celeron M ? or AMD ?

Thank you

---

### Post by bluto on 2006-05-17
Hi Ronan,

The only customization was to increase the disk to 60MB.  I have ordered an additional 512MB ram from a third party which hasn't arrived yet, but I don't think it is really necessary for most uses. In my case it is handy for software development, just speeds up compiles, etc.
 
The DVD is working fine.

I have not configured the Wifi yet, as my home office is hardwired, but I am sure it won't work out of the box.  The Dell 1370 Wifi card uses a Broadcom chip set, which will require the NDIS wrapper to configure properly, but shouldn't present much difficulty.

I did have some difficulty with hibernation and standby, but with the latest Dapper updates this seems to be resolved.
 
To get the screen working at full resolution (1280 x 800) I did the following:

 1. installed 915resolution using apt-get
	 sudo apt-get install 915resolution
 
 2. changed these values in /etc/default/915resolution 
 
 	MODE=49
 	XRESO=1280
 	YRESO=800

 3. changed the Monitor section in  /etc/X11/xorg.conf  as follows:
 
 HorizSync 	28-64
 VertRefresh 	43-60
 Modeline 	"1280x800" 80.58 1280 1344 1480 1680 800 801 804 827

4.  To eliminate the Synaptics touchpad tapping feature, I located the section:
	Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	
	by adding this Option line:

	Option 		"MaxTapTime" 		"0"
 
 All in all, this notebook offers a lot of bang for the buck.  Let me know what you decide.

Bluto

---

### Post by ronan on 2006-05-17
Thank you Bluto for your quick answers.

I was wandering if you chose the DVD burner as option and if you now that it works well on ubuntu

Do you experience lags while you are using nautilus and firefox for example ?

Also i would like to know if the Sound works proprely.
I dont know if you use skype, but if it is the case, can you receive call while you are listenning music ?

Sorry to ask you so many questions
Maybe you can answer me by writin an entry for the B130 on the wiki.

Thanks

Ronan

---

### Post by bluto on 2006-05-17
Hi Ronan,

I didn't buy the DVD burner upgrade, I already have a DVD burner on my desktop box, so I wanted to save the $.  The sound worked properly without any tweaking, but from browsing this forum I think there may be a problem with the headphones not killing the onboard speakers.  I haven't had a chance to test that yet.  I use Konqueror, and haven't experienced any sound lags or drop outs while browing and listening to CDs, but keep in mind I only have been using this system for a week.  Some extensive long term use may prove differently.  this is one of the reasons I ordered a 512MB memory module, to bring the total ram up to 1GB. I found it much cheaper to get the ram module from a third party  ($40) rather than from Dell.  I don't use skype, so I can't answer that one. Once I've had some time with this notebook I'll look into a wiki entry.

Bluto

---

### Post by carlos123 on 2006-05-17
I bought a Toshiba M70-DL3 with 512 MB Ram and an 80 GB hard disk.  A modern wireless card built in.  A super multi-DVD and CD burner.  

Ubuntu 5.10 did not have the proper driver to use my wireless card but installing 6.06 had it  and did the trick.  You can also get the driver and intall it yourself.  

The laptop fan does not seem to be coming on as much as under Windows xp and the laptop appears to be running hot though I need to check up on this more.  

Other than that no problems so far.  

Get KNOPPIX, download, and burn to a CD.  Take it to stores and ask respectfully if you can test a laptop by loading KNOPPIX (boots off the CD) and see if things work in the store before you buy (of course my laptop would not have worked without the latest driver for my wireless card but I tested KNOPPIX on a newer version of the TOSHIBA's and it worked fine so I had pretty good suspicion that it would work ok on mine too).  

Oh I paid $941.00 CA for it (about $900.00 US I think).  Sweet!

Carlos

---

### Post by wbmj on 2006-05-18
Dell Latitude D810 1.7Ghz 2gig of RAM 80gig SATA HD.
Widescreen, wireless and DVD burner work out of the box

---

