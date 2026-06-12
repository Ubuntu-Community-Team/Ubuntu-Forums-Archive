---
title: "Nvidia 256.35 and 256.44 Major problem"
date: 2010-08-04
forum: Hardware
---

### Post by phazixc on 2010-08-04
I'm Running:-

Toshiba q505 888

Ubuntu 10.04 lucid 64Bit

Core 7i q740
Nvidia Gts 360m 1gb
4 Gb Ram 


I Updated to 256.35 = Excellent / perfect

Then my updates from X-swat and Xorg Egders updated to 256.44 this = my world falling apart.

My system completely locks up / hags / kills its self within 4 mins of logging in. 

If I load anything I.E wine to run a game. 

It really doesnt like that... My problem is i'm only a year into ubuntu and I have done manual updates before, but what im doing isnt working as I have tried purge remove nvidia .44 and disabling the two ppa's then manually installing .35 ..

BUT

when I start the gdm = great it works, then when I restart = not great....because I'm on failsafe graphics and the x sever setting not in menu (if it is in menu then theres nothing in there; apart from that msg to restart X) and when I load Hardware drivers the nvidia card isnt there..

I would like to think that some of your reading this are laughing because you are what I would call a pro in the ubuntu area and that you could / will post a detailed step by step to help me install .35 through the x-swat or x-org egder ppa or even manually download it and install it that way, so when I restart it works, and more to the point I can keep those two ppa's in my system so when i hit the update button I can see ubuntu wants to update to .44 which I WONT DO....

One year into ubuntu and I haven't logged into windows since.

As I find theres always someone will to help fix something in ubuntu..

anyway thats that, Mr/Mrs pro.... can you post that guide please.

P.S im currently on Linux-x86_64 NVIDIA Driver Version: 195.36.24 Server Version Number: 11.0 and Server Vendor Version: 1.8.2 NV-CONTROL Version: 1.22
gnome 2.30.2 and kernel linux 2.6.32-24 generic
platform X86_64



Thanks

---

### Post by 23dornot23d on 2010-08-04
This is all I usually do to get the Nvidia Drivers working  .... [LINK]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/")

I currently run the 256.35 = Excellent / perfect one too .....

was after the later one .... [256.44]("http://www.nvnews.net/vbulletin/showthread.php?t=153575") ..... but not added it yet .... seems like a pre-release here.

Usually you can just pick the ones you want ,, within Synaptic
as long as you have purged all the old Nvidia files and also have the current kernel and headers installed
the version will usually builds with the Nvidia driver you have picked ...... 

are there any [bug reports this is all I found wine]("http://permalink.gmane.org/gmane.comp.emulators.wine.user/67591") .. seems relatively new ... sometimes they give more information as to why its happening.


SYSTEM - ADMINISTRATION - HARDWARE drivers ....... select current.

( do you have some PPA's that are overriding the official ones ? if so they may need to be disabled to get  the
drivers that you want )

_____________________________________________________________________________________

> 

thanks ill check it out now thanks again

the only thing with that link is it say to add PPA x-swat I have that  but when i run the update all it want to do is install 256.44 not  256.35.

how do i get 256.35 on my system through the ppa cannt I..

also would   


sudo apt-get purge remove nvidia-* 

work to completely remove nvidia drivers and how do I update the kernel and header


thanhks
You need to follow this ...... 

$ sudo aptitude install build-essential linux-headers-2.6.32-24 generic
[LIST=1]
[*]**Open your favorite terminal *(ie. Applications->Accessories->Terminal) *and uninstall any and all nvidia components installed.**$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] purge nvidia[COLOR=#000000]*****[/COLOR]
[*]**Next we need to blacklist “nouveau”.  Do so by adding the following into */etc/modprobe.d/blacklist.conf* with your favorite text editor.**blacklist nouveau
[*]**Install the latest official stable driver from the repository**$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get**[/COLOR] [COLOR=#c20cb9]**install**[/COLOR] nvidia-current
[*]**Next we’ll load the Nvidia kernel module**$ [COLOR=#c20cb9]**sudo**[/COLOR] modprobe nvidia-current
[*]**Verify it’s successful entry via lsmod like so**$ [COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**lsmod**[/COLOR] [COLOR=#000000]**|**[/COLOR] [COLOR=#c20cb9]**grep**[/COLOR] [COLOR=#660033]-i[/COLOR] nvidia
[*]**And one last step, we must create the Nvidia configuration file.**$ [COLOR=#c20cb9]**sudo**[/COLOR] nvidia-xconfig
[/LIST]
There, all better?  Let me know if it worked well for you, and if not I’ll do my best to help!



[B][COLOR=Red]Keep your questions in this thread ,,,, the other thread is a different problem as they are adding
a new graphics card ...... the only driver needed is the current nvidia one.
 ( now they seem to be getting sidetracked into using the same 256.44 driver )[/COLOR]
[/B]

---

### Post by phazixc on 2010-08-05
Yeah I undertstand what you have told me and have installed "current" before....

I basic decided to clear install just to see if was the drivers .44 and it is...



now if I dont have those ppa's int he source list then the current would = 195

with the ppas it Now = .44 and not 256.35

so thats what Im trying to work out how to install 256.35 not 256.44

---

### Post by 23dornot23d on 2010-08-06
Ok sorry ..... took so long to respond ... (think there was a problem yesterday with the database.)

I am running Maverick development version .... and the current for that is 256.35.

With it being development I am not sure if you need the latest kernel and then
the 256.35 drivers , [URL="http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html"]maybe someone else can advise you on that for LUCID 10.04
[/URL] 
[COLOR=Red]The other option is to load up a separate version of Maverick 10.10 for testing, which is how
I got to run them ..... [LINK TO SCREENSHOT]("http://i36.tinypic.com/ddjlfc.jpg") 
( But be aware it is for testing and if things go wrong its not always as simple to fix things - 
and things can break - Read the Stickies at the top of this thread before anything else [Maverick 10.10 ]("http://ubuntuforums.org/forumdisplay.php?f=385"))
[/COLOR] 
Unless someone else can show you how to get them working ok for LUCID as I still run the 195 in Lucid
which works ok for me.

I did not have to go hunting around for PPA's Maverick just uses the 256.35 as current now.

---

