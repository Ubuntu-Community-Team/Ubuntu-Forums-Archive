---
title: "Porting to Ubuntu from Windows"
date: 2005-10-09
forum: Hardware &amp; Laptops
---

### Post by lifeperfecti0n on 2005-10-09
Hi all,
   I started using Ubuntu a few months baq...n i must say im :D bout it. However there r certain problems im facing wich prevent me from deleting win XP completely much as I would like to do so!
1. Games run very slow (even those designed for Linux). I tried boson (a state-of-the -art strategy game) n it advised me to enable Direct 3D Rendering. I don't know how on earth I could do this.
2. I have an USB Infrared Adapter (MA-660) and I don't know how to use it in ubuntu. As a matter of fact, I don't know how to work USB's at ALL in ubuntu. Please help! 
3. I want to decrease the start-up time for ubuntu. How can I configure some services not to b started on boot (esp. the clock synchronisation it takes almost 30 secs!)
I will b grateful for ur assistance

System Specs:
Intel D815EGEW Desktop Board
Pentium 1.0 Ghz Processor
Built in sound card n gpu
i don't no nythin bout usb's but i hv 2 slots does this help?:???: 

If all of these probs r solved I would never hv to use XP again...how exciting!!!

P.S. I heard about Cedega/WineX...it emulates directx...frm where could I get a binary?

---

### Post by Zeroedout on 2005-10-09
[quote=lifeperfecti0n]Hi all,
   I started using Ubuntu a few months baq...n i must say im :D bout it. However there r certain problems im facing wich prevent me from deleting win XP completely much as I would like to do so!
1. Games run very slow (even those designed for Linux). I tried boson (a state-of-the -art strategy game) n it advised me to enable Direct 3D Rendering. I don't know how on earth I could do this.
2. I have an USB Infrared Adapter (MA-660) and I don't know how to use it in ubuntu. As a matter of fact, I don't know how to work USB's at ALL in ubuntu. Please help! 
3. I want to decrease the start-up time for ubuntu. How can I configure some services not to b started on boot (esp. the clock synchronisation it takes almost 30 secs!)
I will b grateful for ur assistance

System Specs:
Intel D815EGEW Desktop Board
Pentium 1.0 Ghz Processor
Built in sound card n gpu
i don't no nythin bout usb's but i hv 2 slots does this help?:???: 

If all of these probs r solved I would never hv to use XP again...how exciting!!!

P.S. I heard about Cedega/WineX...it emulates directx...frm where could I get a binary?[/quote]

For your first point, you need to know which video card you have. If you have an ATI card, grab their linux drivers, if you got an Nvidia card, grab thiers. (tons of guids/how-to's on the forums to help you with installation).

Point two, go to Synaptic (System ----> administration ----> Synaptic Package Manager) add all the repositories (within synaptic, hit setting ---> repositories, hit add, check all the boxes) then hit reload, this will add all the packages available, then hit search, select name and description, search for IRDA (stand for InfraRedDatA or something like that), and grab those packages, that should help with using infra red.

point three, I'm not 100% sure on how to disable that, however, if you right click the clock, hit adjust time and date, then uncheck the box that says syncronize with ntp servers periodically, that should do it. If you want to increase the overall snapiness, read the prelink how to, search for it in the forum, that REALLY helped for me. 

As for Cedega/wineX, the official website is [www.transgaming.com](www.transgaming.com) it can be really good if the games you play are supported, but you do need to pay for cedega. Personally i would never buy an app i couldnt try first, so search around for a torrent or soemthing for cedega, i'm sure you'll find, i dont think it would be appropriate to provide a link as that would technically be illeagle, however, look for torrent of the .deb and that will easily install. Else, try dx9wine, it's quite excellent, and does the job (besides it's free (both freedom and beer)). There is a really nice script that downloads the latest version of it and installs it, but i can't remember where i found that, search around for it though. If you just wanna run windows apps, grab wine for the repos. Winesetuptk is supposed to be nice graphical interface to wine, i'm told xwine is quite good too. 
Good luck getting everything working, some things can be a bit tedious, however, it feels great when everything works. Look at the ubuntu wiki, they have guids for doing virtually EVERYTHING you could possibly want to do.

---

### Post by lifeperfecti0n on 2005-10-10
Hi,
Thanx for the quick reply..i must say I was thinking ma problem would get buried underneath heaps of other problems...ok ur suggestions r great...but u didn't say anything about 'Direct 3D Rendering' for my video card (Intel i815)
I will try out those alcohol versions n report baq :smile:

---

### Post by wylfing on 2005-10-10
The part about synchronizing the clock, that's handled by the /etc/init.d/ntpdate script. The Gnome "service" that syncs the clock also runs this script when it does its work, but disabling the Gnome clock syncing won't disable the sync at startup time.

Generally, all startup activities are controlled by the scripts found in /etc/init.d. These scripts are called from the directories /etc/rc0.d through /etc/rc6.d, and including /etc/rcS.d. Now, the "right" way to add and remove these scripts is with the [FONT="Courier New"][COLOR="DimGray"]update-rc.d[/COLOR][/FONT] command. However, this is not really a good manual solution when you simply want to tweak what gets started and what doesn't.

So, the thing to do is find the link to the script that is being executed. In this case, doing [FONT="Courier New"][COLOR="DimGray"]slocate ntpdate[/COLOR][/FONT] works fine. What we're looking for are the links that start with S and two numbers, like we see in /etc/rcS.d/S51ntpdate. This is what makes the startup sync run. So we rename the file like so: [FONT="Courier New"][COLOR="DimGray"]sudo mv /etc/rcS.d/S51ntpdate /etc/rcS.d/disabled.S51ntpdate[/COLOR][/FONT]. Now the clock sync will no longer run at startup time.

You can still sync the clock any time you want by choosing System > Administration > Time and Date from the main toolbar. There is a big Syncronize button that you can press to run a one-time sync.

---

### Post by lifeperfecti0n on 2005-10-11
ok thanx 4 ur help i got it done :)  I installed sysvconfig via synaptic n configured all the services thru it. Linux is gr8 when u get something done!:D 
btw is ny d3d driver available 4 ma intel i815 graphix card?? i read somewhere dat only nvidia n ati r supported is it true? dats 2 baad!:( 
ny developers out dere I need support for ma660 in irda-utils (ma600 is supported but dat driver doesn't work 4 ma660...im sure it vil after a few minor adjustments...)
i vil b greatful 4 ur help
Thanx all 4 ur help on ntpdate!

---

### Post by lifeperfecti0n on 2005-10-11
hey i checked those wines u gave me n i hv discovered dat nothin can b compiled frm source in my ubuntu..i downloaded a patch 4 wine called dx9wine but dunno how to apply it (i think it vil already b applied in the latest version of wine which is installed on my system...vil it?)
Given dat I install winex (dats quite far-fetched since I don't possess a credit card) vil it support d3d rnderin on intel i815...im skeptical bout dis...
btw upon attempting to download winex frm cvs i discovered dat cvs doesn't work...it says host not found...is dere ny way I can assign a static ip 4 cvs since I m behind a dratted ISA server? Infact not even apt-get works on bash...im sure da problem vil go if I somehow tell bash to connect thru a static ip...:???:

---

### Post by Dalinux on 2005-11-17
Hi, I have i855GM display adapter and DRI works fine. Evrything you gotta do is this :

If you have got a Xorg, than you need compile kernel and add in character devices support of dri and add i810 ad module and VERY IMPORTANT add i915 to the kernel not as module ... Than i810 si module which you need to use in your xorg.conf .. You will get /dev/dri/card0 and card1, don't forgot that this devices HAVE TO be accessed by normaln user for writing :)

Otherwise if you have got XFree86, than you have to compile to kernel driver i830 not i915 ...

Good Luck .. and .. If you know something new about MA660, than I'd like to know what to do with that :)

---

