---
title: "Total disappointment for my Lenovo 3000 N200:("
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by linuxican on 2007-07-15
Hi all,
I'm totally disappointed with my lenovo N200. I'm really gettig mad. My first problem was the windows Vista on it. So i wiped it off! and everything is like hell after trying to set up a dual boot.
first i was not able to set up windows XP. Then i decided to install ubuntu edgy eft and it worked. but no sound, no ethernet controller and no internet.
So, i'm grounded and i can not work! my job needs a dual boot and I need it. 
suppose that i can handle my job with an ubuntu installation and a connection to our ADSL router. that's all i want.
why nobody own N200 here?:(

---

### Post by egads on 2007-07-21
Hi,
I can certainly understand the frustrations with getting ubuntu to work on the n200 but I cracked it last weekend, here's how.
Installed Feisty amd64 from the alternate install cd (finds the wired ethernet card)
Installed the latest kernel from Gutsy and applied the iwlwifi and mac80211 patches as described here [http://ubuntuforums.org/showthread.php?t=493095](http://ubuntuforums.org/showthread.php?t=493095)
Installed alsa libs, utils and drivers from source adding the realtek6.tar.gz patch to the source of the driver before make installing which is from [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2725) (you will have to register for alsa bugtrack to get it). The easy way to do this is in the post from toolish here [http://ubuntuforums.org/archive/index.php/t-429419.html](http://ubuntuforums.org/archive/index.php/t-429419.html)
Now the only stuff I need to work out how to get responding properly is the sleep and the hibernate, seems to just shutdown!
Good luck!

---

### Post by kchandler on 2007-07-23
You mentioned that you were having trouble installing windows XP.

If the problem is that the Windows XP installation CD does not detect your hard drive it is because it does not contain the necessary drivers for your SATA Controller which hosts your hard drive.

If you go the the Lenovo Support website and look for hard drive drivers and view the readme for Windows XP, it will list the steps you need to take to get the hard drive working.

P.S. If you don't have a floppy drive, I used nLite to include the driver with my XP CD ;) If you fine that the CD is larger than 700mb after including the driver file, just remove some language files you never use from the CD..

If you have never used nLite before it is pretty straightforward.

Good luck.

How much battery life do you guys get on the N200?? I can't seem to get more than 2h 30m... when the battery is rated for 4.5 hours...

---

### Post by KS_japan on 2007-08-02
Could not install Ubuntu 7.04 in N200 with intel 965GM. Even openSUSE 10.2 cannot detect the graphics though it can be installed. Has anyone solved this problem for N200 with intel 965M chip?

---

### Post by kchandler on 2007-08-02
KS_japan, My N200 has the Nvidia 7300 graphics card.. I couldn't get the Live CD to install Ubuntu at all so I used the alternate CD and it worked fine. 

Things that did not work out of the box were 
wireless, audio, fingerprint reader, bluetooth, webcam.

---

### Post by KS_japan on 2007-08-07
kchandler, thanks a lot. I could run webcam after upgrading to gutsy except the audio (though I used some alsa modifications  in the ubuntu forum) and fingerprint reader are still not working (tried two alternative methods). Moreover, the gutsy has the problem with the sudden dimming of the screen which is triggered by some action(?)

---

### Post by piege on 2007-10-12
Bin workin on my new 3000 N200.

Installed the alternate cd for 64bit. 

No problem with wifi,

Sound works but no headphone detection,

Bluetooth works with mouse need to set it for A2DP too

can't get CD/DVD to be mounted

biometrics isn't working 

installed right driver for x3100 and got compiz working fine

---

### Post by chrismyers on 2007-10-24
I have a 3000 N200 with an Nvidia card.

The final release of Gutsy live CD works fine.
[B][SIZE=4][COLOR=Blue]
I'm totally satisfied with it.

[/COLOR][/SIZE][/B][FONT=Tahoma]Grahics work perfectly with the native resolution of 1680x1050 using the open source nv driver - If you want to play with compiz-fusion, the proprietary driver works fine too.

Wireless LAN works perfectly.

Wired LAN works perfectly.
 
Bluetooth works perfectly.

Webcam works perfectly - In Ekiga, set:

    edit>preferences>devices>video devices>V4L2

Sound does not work out-of-the-box, but this is simply fixed by adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo
 
The fingerprint scanner is not recognised, but there are projects such  as bioapi & thinkfinger. I have not had time to try these out yet.[/FONT]

---

### Post by pietermeurs on 2007-10-25
i ordered a lenovo 3000 n200 (t7300 2.0 GHz, 2Gb Ram, with nvidia 7300) too.

Have you tested the suspend and hibernate in Gutsy?

thanks a lot!

by the way, how's the n200 overall performance,...?

---

### Post by chrismyers on 2007-10-26
> **pietermeurs said:**
> i ordered a lenovo 3000 n200 (t7300 2.0 GHz, 2Gb Ram, with nvidia 7300) too.

Have you tested the suspend and hibernate in Gutsy?

thanks a lot!

by the way, how's the n200 overall performance,...?


I just tested suspend & hibernate for you... It doesn't work.

I forgot to mention that the SD card reader doesn't work either.

I should probably amend my statement:

[B][SIZE=4][COLOR=Blue] I'm *almost *totally satisfied with it.

[/COLOR][/SIZE][/B]*If anyone knows of fixes for the above, I'd love to know.*


Overall performance is great. In fact it's total overkill. Just looking at system monitor, it says that its using 200mb of 2gb memory & 0 bytes of the swap.
(OK, I'm not stressing it at the moment).

Cheers.

---

### Post by linuxican on 2007-10-29
Hi,
when i first started this thread, i was so upset about my Lenovo N200 and i was thinkg about changing it. 
Now i'm using my lovely N200 with ubuntu 7.10 installed on it. and it rocks!
of course i can't use my memory card reader on it and it bugs me because i need to switch to windows to get my photos from my camera's SD card.
bluetooth works but most of the time i've got problems connecting other devices.
After all i think we should change the title of this thread.
hibernation also doesn't work and i think power manager is not optimized for this laptop.

---

### Post by piege on 2007-10-30
My SD card reader worked out of the box. 

I would really like to use hibernate and I can't seem to get my cd mounted.

---

### Post by DannyW on 2007-11-04
I've filed a bug report for sound not working by default.

[https://bugs.launchpad.net/ubuntu/+bug/152383](https://bugs.launchpad.net/ubuntu/+bug/152383)

Lets try to get the problems with the laptop noticed!

Has anyone noticed disconnects with the networking? I'm using wicd and connecting to a wireless network and after a while I find myself disconnected and wicd doesn't show any wireless networks, when I know I am in range of them. I fix this by rebooting, it's quite a pain.

Also, many of the Fn buttons do not work for me (F4, F5, F7, F10, F11, F12).

Mute works fine, but volume up and down just seems to toggle the volume between 0% and 11% (the kubuntu volume control doesn't change volume levels, just the onscreen thing saying either 0% or 11%).

I'm using Kubuntu Gutsy.

Thanks,
Danny

---

### Post by davisond on 2007-11-10
My experience with this laptop (the N200) are similar to others in this thread, with one or two others to note:

Sound: ok with the module option shown above

Webcam: works fine with V4L2

Wireless: works out of the box but is not 100% stable.  Wifi driver panics under load occasionally

Hibernate: works IF YOU HAVE ENOUGH SWAP.  2G RAM means 2G swap needed for hibernate.  Note though, that after resuming from hibernate the CPU fan does **not** work.  This is an ACPI problem that I have still not resolved and so the laptop quickly overheats after resuming, forcing a reboot anyway.  Not good at all.

Suspend: suspend itself seems to work fine, but you cannot resume.  Forced power off is the only option when resuming from suspend.  I've tried 3 different suspend mechanisms all with the same result so I'm fairly sure this is a kernel issue.

Screen flicker: using compiz (not tried much without) I get the occasional annoying screen flicker - almost as though power was lost and then quickly restored.

Random reboot: very occasionally, for no consistent reason that I can see, the machine just freezes for 2 seconds and then completely powers off and reboots.  No kernel or debug logs to indicate why.  Again, almost as though power has just been completely severed to the motherboard.  I've had this issue with 2 N200's now and it's probably another kernel issue since colleagues use Vista on the same machine without any of these problems.

---

### Post by piege on 2007-11-10
anyone got their biometrics working??

---

### Post by davisond on 2007-11-10
oy yeah, forgot to mention that.  The hardware is AuthenTec (I think) - i.e. not the same as the ones lenovo use in thinkpads.  Therefore thinkfinger will not work.  There is a very raw, early alpha of some tool that might make it work, but it's not for the faint hearted and might still be impossible at this stage anyway

---

### Post by DannyW on 2007-11-11
There is some info on this page about the fingerprint reader in the N200 (AES2501)

[http://gkall.hobby.nl/authentec.html](http://gkall.hobby.nl/authentec.html)

---

### Post by chrismyers on 2007-11-11
> **DannyW said:**
> There is some info on this page about the fingerprint reader in the N200 (AES2501)


Which page? You seem to have forgotten the link.

---

### Post by DannyW on 2007-11-11
> **chrismyers said:**
> Which page? You seem to have forgotten the link.

Oops! It seems you are right! Thanks, fixed the post. Sorry about that.

---

### Post by pietermeurs on 2007-11-16
I read somewhere (notebookreview.com i guess) that the fan can be somehow annoying. Do you guys have that experience?

---

### Post by chrismyers on 2007-11-17
No the fan is quiet, & whats more the laptop is cool to the touch.

My last laptop used to get so hot that it used to burn my knees so the Lenovo is great.

---

### Post by DannyW on 2007-11-17
I've never been annoyed with my fan.

---

### Post by pietermeurs on 2007-12-04
I've got my Lenovo now for about two weeks and i'm very happy with it. Still some flaws though: the screen flickers and the suspend/hibernate thing.

Just wondering: did any of you installed a special driver for the graphics? When i clicked the visual effects it said it was necessary to install the driver and so it did (automatically). Could this have anything to do with the screen flickering?

The suspend-hibernate thing: when i close my lid, the pc goes in hibernate (the moon-led burns), but i can't wake him up. Anybody ideas?

thanks!!

---

### Post by manishjb on 2007-12-04
I have recently bought lenovo 3000 n 200 and i am having a problem with a webcam....
I duno wat the problem... Most of the times it shows that d web cam is not connected n i hve to restrt the lappy.....
I will be greatful if somebody helps me out......
:confused:

---

### Post by pietermeurs on 2007-12-05
in ekiga, as well as skype, put your settings to V4L2. That should do the trick. Works for me anyway. If you want to use your webcam without skype or ekiga, install cheese. It should work.

---

### Post by manishjb on 2007-12-05
Hey thnkz a lot buddy....
Bt wat if i wana strt my webcam in Yahoo OR MSN???????

---

### Post by manishjb on 2007-12-05
N can u plzzz help me as whr to install cheese????
Plzzzzz

---

### Post by pietermeurs on 2007-12-05
just use synaptic, find cheese and mark it for installation. You can find cheese in your menu (same as terminal, text-editor,...).

goodluck

---

### Post by astr365 on 2007-12-14
> **davisond said:**
> My experience with this laptop (the N200) are similar to others in this thread, with one or two others to note:

Sound: ok with the module option shown above

Webcam: works fine with V4L2

Wireless: works out of the box but is not 100% stable.  Wifi driver panics under load occasionally

Hibernate: works IF YOU HAVE ENOUGH SWAP.  2G RAM means 2G swap needed for hibernate.  Note though, that after resuming from hibernate the CPU fan does **not** work.  This is an ACPI problem that I have still not resolved and so the laptop quickly overheats after resuming, forcing a reboot anyway.  Not good at all.

Suspend: suspend itself seems to work fine, but you cannot resume.  Forced power off is the only option when resuming from suspend.  I've tried 3 different suspend mechanisms all with the same result so I'm fairly sure this is a kernel issue.

Screen flicker: using compiz (not tried much without) I get the occasional annoying screen flicker - almost as though power was lost and then quickly restored.

Random reboot: very occasionally, for no consistent reason that I can see, the machine just freezes for 2 seconds and then completely powers off and reboots.  No kernel or debug logs to indicate why.  Again, almost as though power has just been completely severed to the motherboard.  I've had this issue with 2 N200's now and it's probably another kernel issue since colleagues use Vista on the same machine without any of these problems.

Does anybody else have these random reboots ? I get it about once every 1 - 2 weeks. As far as I can see there is no certain activity I do that leads to the reboot. I haven't found any other forum posts or bugs about that  problem. Apart from tah problem I am very satisfied with the 3000 N200. Sound and screen flickers are gone after I tried the solutions I found here, it is fast and quiet.

---

### Post by chrismyers on 2007-12-15
> **astr365 said:**
> Does anybody else have these random reboots ? I get it about once every 1 - 2 weeks. As far as I can see there is no certain activity I do that leads to the reboot. I haven't found any other forum posts or bugs about that  problem. Apart from tah problem I am very satisfied with the 3000 N200. Sound and screen flickers are gone after I tried the solutions I found here, it is fast and quiet.

Yes, I get them. Apparently it's the Nvidia driver. Try switching back to the nv driver just to prove it.

Hopefully Nvidia will follow ATI & open up their drivers.

---

### Post by gryzzly on 2007-12-17
Bought my lenovo 3000 n200 TY2BRIV, installed Ubuntu 7.10 Gutsy - everything worked out of the box, 
except this issues:
1) sound 
was fixed as describes above here

2)suspend / hibernating
waiting for the hero which will save our batteries

3)fingerprint 
doesnt work, also would be happy to hear about some kind of fix...

4)memory-card reader
doesn't work, which is totally bad, also looking for solution;

5)screensaver (if i put it from the settings)
Just kills everything, that even keyboard doesnt work, so just forced power reset helps

6)screen flickering (if use fullscreen mode for both firefox and opera)
using restricted nVidia driver

Please help if anybody knows. Thanks guys

---

### Post by gryzzly on 2007-12-17
> **astr365 said:**
> Does anybody else have these random reboots ? I get it about once every 1 - 2 weeks. As far as I can see there is no certain activity I do that leads to the reboot. I haven't found any other forum posts or bugs about that  problem. Apart from tah problem I am very satisfied with the 3000 N200. Sound and screen flickers are gone after I tried the solutions I found here, it is fast and quiet.

Also had them like two or three times since bouhgt - in 5 days or so. Annoying thing.

---

### Post by gryzzly on 2007-12-17
About hibernating - it works, but with totally strange visual effects, when it loads, screen make strange kind of flickers. Doesn't look like healthy behavior...

---

### Post by chrismyers on 2007-12-17
> **gryzzly said:**
> Bought my lenovo 3000 n200 TY2BRIV, installed Ubuntu 7.10 Gutsy - everything worked out of the box....

6)screen flickering (if use fullscreen mode for both firefox and opera)
using restricted nVidia driver

Please help if anybody knows. Thanks guys

My screen hasn't flickered for ages. I thought I remembered reconfiguring X & looking through my commandline history confirmed it....

Try this command:

sudo dpkg-reconfigure xserver-xorg

Answer all the questions, remembering to select nvidia as the driver.

Let me know how you get on. :)

---

### Post by gryzzly on 2007-12-18
> **chrismyers said:**
> My screen hasn't flickered for ages. I thought I remembered reconfiguring X & looking through my commandline history confirmed it....

Try this command:

sudo dpkg-reconfigure xserver-xorg

Answer all the questions, remembering to select nvidia as the driver.

Let me know how you get on. :)

that didnt change anything :( also this xorg.conf that i backed up was absolutely same as what i got after reconfigure :(

but this flickering seems to appear in just some special cases...

---

### Post by chrismyers on 2007-12-18
Sorry to hear that it didn't work.

Just out of interest, compare your xorg.conf to mine.

See attachment.

---

### Post by monkeyking on 2007-12-20
I don't have any problems with random reboots, and I'm using the restricted driver.
Butt my wireless seem to stop working, after some time.

I tried doing a dual boot with vista,
but appereantly both of my boot options are the rescue partition,
my menu.lst looks like

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


```

anyone have a clue?

---

### Post by monkeyking on 2007-12-21
Dbl post

---

### Post by gryzzly on 2007-12-21
> **chrismyers said:**
> Sorry to hear that it didn't work.

Just out of interest, compare your xorg.conf to mine.

See attachment.

Ok, here is mine;
actually differences are: 
in Section "Device" u have
```
	Option		"UseFBDev"		"true"
```
which i don't have,
and i have 
```
	Option		"AddARGBVisuals"	"True"
	    Option	    "AddARGBGLXVisuals"	  "True"

```

and u can check out also an attachment here

---

### Post by chrismyers on 2007-12-21
> **monkeyking said:**
> I don't have any problems with random reboots, and I'm using the restricted driver.
Butt my wireless seem to stop working, after some time.

I tried doing a dual boot with vista,
but appereantly both of my boot options are the rescue partition,
my menu.lst looks like

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,1)
savedefault
makeactive
chainloader     +1


```anyone have a clue?

OK.. I think I may be able to help.

Do a:

sudo parted

Then do

print all

(press q then enter to quit.)

This will display something like:

Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  154GB  154GB   primary   ext3         boot 
 2      154GB   160GB  6218MB  extended                    
 5      154GB   160GB  6218MB  logical   linux-swap 

As you can see I wiped my Vista partition, but *you* should be able to see two NTFS partitions.

The smaller one is the recovery partition & the larger NTFS partition is the one you want.

You are looking to change hd0,(x) in menu.lst, where (x) is the NTFS partition -1.

I suspect you need:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Windows Vista/Longhorn (loader)
root            (hd0,2)
savedefault
makeactive
chainloader     +1

I hope I have this correct.

---

### Post by monkeyking on 2007-12-22
```

Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  5893MB  5892MB  primary   ntfs              
 2      5893MB  93,8GB  87,9GB  primary   ntfs         boot 
 3      93,8GB  119GB   25,1GB  primary   ext3              
 4      119GB   120GB   1135MB  extended                    
 5      119GB   120GB   1135MB  logical   linux-swap        

```

I reinstalled vista from the recovery partition,
then I installed easybrcd or something like that.
From there inside vista, I was able to setup the vista boot menu, so my ubuntu is added.

But I don't really understand, how the harddrive is set up.
When I choose the recover menu at boot time it will boot partition1.
But the mbr apperently lies on partition2 ?
Thats strange...

---

### Post by monkeyking on 2007-12-22
> **monkeyking said:**
> 
Butt my wireless seem to stop working, after some time.


There is a bug in the wireless chipset,  
info and solution here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)

---

### Post by monkeyking on 2007-12-22
appearently the sound is only working if onboard modem is enabled

---

### Post by chrismyers on 2007-12-23
> **monkeyking said:**
> 
I reinstalled vista from the recovery partition,
then I installed easybrcd or something like that.
From there inside vista, I was able to setup the vista boot menu, so my ubuntu is added.

But I don't really understand, how the harddrive is set up.
When I choose the recover menu at boot time it will boot partition1.
But the mbr apperently lies on partition2 ?
Thats strange...

I assume you have fixed it now... Good.

I cant help you regarding the Windows bootloader.

Just for your info. If you ever need to repair the Ubuntu Grub bootloader, you need to download SuperGrubDisk from here:
[URL="http://supergrub.forjamari.linex.org/"]
http://supergrub.forjamari.linex.org/[/URL]

Its a doddle to fix the boot with this. It also works as a fix if you have restored from an older version of Norton Ghost.

---

### Post by barbedsaber on 2007-12-25
K, I'm just about to buy a Lenovo 3000 N200, but I need to know that everything will work, what dosn't work out of the box, and what can you change, I just want a simple answer plz.

---

### Post by monkeyking on 2007-12-25
check here for details.
[http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=26&view=by_date_ascending&page=1](http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=26&view=by_date_ascending&page=1)

Out of the box the following will not work
Sound, webcam and fingerprint.
After some tweaking the webcam and sound will work.
But not the fingerprint.

But the fingerprint stuff will not work in vista either check the lenovo forum here for details
[http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=26&view=by_date_ascending&page=1](http://forums.lenovo.com/lnv/board/message?board.id=N_Series_Lenovo_3000&thread.id=26&view=by_date_ascending&page=1)

It's a nice computer thought,
very nice screen with high resolution.
But you might wanna go for the 2 gig memory

---

### Post by barbedsaber on 2007-12-25
thnx heaps for the reply, what about compiz, if you need a driver, can I download it now, because I have unlimieted internet, at the fastest speed you can get in Australis, but only untill 4:00 am tommorow morning, and I don't like the idea of downloading a driver from my 56k connection at home.
(i am staying at my uncles house.)

---

### Post by monkeyking on 2007-12-26
> **barbedsaber said:**
> thnx heaps for the reply, what about compiz, if you need a driver, can I download it now, because I have unlimieted internet, at the fastest speed you can get in Australis, but only untill 4:00 am tommorow morning, and I don't like the idea of downloading a driver from my 56k connection at home.
(i am staying at my uncles house.)

never tried,
but should be possible.

---

### Post by gryzzly on 2007-12-27
> **monkeyking said:**
> There is a bug in the wireless chipset,  
info and solution here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/149214/comments/24)

Hey, but my Lenovo 3000 n200 has Intel 3975ABG wireless chipset (or at least Ubuntu Device Manager says that) - so the solution u linked to is not good for me?

---

### Post by Tharkun007 on 2008-01-13
Hello, Suspend and hibernate now works on my 3000 N200 after upgrading the kernel, by following these steps :
[http://ubuntuforums.org/showthread.php?t=646755](http://ubuntuforums.org/showthread.php?t=646755) . Unfortunately, the wlan doesn't wake up correctly. Maybe this could be easily solved ?
Upgrading solved other issues : Powermizer function now included with the new Nvidia driver, making the fan turn less often. Card Reader works ! Hangs I had with samba transfers disappeared.

A miracle for me !

---

### Post by chrismyers on 2008-01-20
> **Tharkun007 said:**
> Hello, Suspend and hibernate now works on my 3000 N200 after upgrading the kernel, by following...

I followed the steps to upgrade the kernel & all the fixes worked. :)[B]

[SIZE=4][COLOR=Red]HOWEVER: Some time after resuming from hibernate, I found that my laptop was overheating[/COLOR][/SIZE]. :shock:[/B]

I believe that the fans fail to kick in after resuming. A quick reboot forced the fans to work overtime to bring the temp down.

This may be an isolated incident, but I don't want anyone to cook their laptop. Please be aware.

Cheers.

---

### Post by Trebaruna on 2008-01-24
My fiancee bought a 3000 N200 yesterday and I'm trying to sort the odds and ends for Ubuntu.

I'm trying to get hibernate to work (like many others, it seems) but I cannot actually test whether it works: whenever the laptop initiates a hibernate the screen turns white with strange patterns, and the speakers start emitting very loud, very VERY irritating noises. Anyone know how I can prevent that from happening? Neither of these symptoms seem very good for the hardware :(

As a sidenote, when I hadn't got the sound working yet (modem disabled in BIOS), hibernate actually seemed to work! Not sure if the fan worked, though, I don't think it was on for long enough (tried suspend and it failed, so I had to shut it down the brute way).

EDIT: Okay, nevermind most of that stuff. I too installed the Hardy kernel (was a bit reluctant at first, but tried anyway) and indeed, it works! Still a white screen though, when resuming from suspend. It goes away quickly however, so it isn't bothering me too much. Seems unloading the nvidia module doesn't help, and nosplash doesn't do anything for it, either. Cardreader isn't working yet, unfortunately.

---

### Post by astr365 on 2008-01-24
> **chrismyers said:**
> Yes, I get them. Apparently it's the Nvidia driver. Try switching back to the nv driver just to prove it.

Hopefully Nvidia will follow ATI & open up their drivers.
I did not switch the drivers completely but switched off the 3D effects. Since then (last 4 weeks) no reboots whatever I did.

---

### Post by ekano on 2008-02-08
Im about to buy a Lenovo 3000 N200 laptop and after I just read this thread im starting to hesitate a bit. 

I want the laptop to run XP Professional smoothly and I wonder: How well does it work with XP and is there much problems to get it run with XP? It will arrive with Visa so Im gonna have to configure XP on my Lenovo 3000 N200 myself. 

I read something about the machine went overheating and i didnt really understand the circumstances... is that a risk if im gonna install XP instead of Vista? What is "Hibernate", could someone describe this please?

I also heard something about problems with fingerprint-reader. Im not interested in that application. Do I need it to access the computer or is it just a "bonus"?

Im also wondering how much the screen reflects, is it annoying?

Do you guys still recommend it and could you describe how complicated it is to do it?

Thanks!

ekano

---

### Post by chrismyers on 2008-02-08
> **ekano said:**
> Im about to buy a Lenovo 3000 N200 laptop and after I just read this thread im starting to hesitate a bit. 

I want the laptop to run XP Professional smoothly and I wonder: How well does it work with XP and is there much problems to get it run with XP? It will arrive with Visa so Im gonna have to configure XP on my Lenovo 3000 N200 myself. 

I read something about the machine went overheating and i didnt really understand the circumstances... is that a risk if im gonna install XP instead of Vista? What is "Hibernate", could someone describe this please?

I also heard something about problems with fingerprint-reader. Im not interested in that application. Do I need it to access the computer or is it just a "bonus"?

Im also wondering how much the screen reflects, is it annoying?

Do you guys still recommend it and could you describe how complicated it is to do it?

Thanks!

ekano


It's a strange question for the Ubuntu forums, but since we are all nice guys, here goes:

If you get the the Lenovo laptop with Vista Ultimate or Vista Business, you get the option to downgrade to XP for free. Lenovo actually provide XP disks on request. I'm sure that they will charge an admin cost though.

[_Downgrade_]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=VSTA-DWNGRD")

I hope this helps.

---

### Post by staib on 2008-02-09
As an aside, Lenovo UK were kind enough to send me a set of 3 CD's to install everything back to how it was in the beginning. Useful free insurance...  

All I told them (true) was that I had added a dual booting Ubuntu 7.10 but for various reasons could no longer access the DVD (in Ubuntu or Vista) and the 'hidden' recovery partition in Vista was also not accessible. Rather than wade through the technical options they offered to send me the full installation discs.

I am now running 7.10 on one box, Vista on the widescreen laptop, and Xandros on the small Eee PC - the latter is easily the fastest to boot, so get used used a lot...

---

### Post by zarath on 2008-02-09
Hi dudes,

The fingerprint reader works fine for me on my N200, Just check out this page: [https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul](https://www.2030.tk/wiki/Enable_AuthenTec_Fingerprint_Reader_as_PAM_modul)

No probelms with anything so far but I havent tried hibernation yet. Screen and WLAN works perfect. Gonna try the Cisco VPN at the university on monday. I run a dualboot with win xp and ubuntu 7.10.

Good luck.

---

### Post by ekano on 2008-02-09
What is "hibernate"?. Would be happy if someone explained.

---

### Post by zarath on 2008-02-13
Check this if you wanna know what hibernate means:
[http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29](http://en.wikipedia.org/wiki/Hibernate_%28OS_feature%29)

---

### Post by teddylinux on 2008-02-13
dear Chrismeyers,
this made sound work for me too!!!
now even more satysfied with this laptop.
Did you found anything for the fingerprint?
teddylinux.

---

### Post by teddylinux on 2008-02-13
thank you, this solved my sound problem
teddylinux

p.s. found anything for the fingerprint?

---

### Post by moeness86 on 2008-02-13
please somebody write a howto for the fingerprint thing posted above

---

### Post by ekano on 2008-02-15
Hi

Ive got the Lenovo 3000 N200 1.46ghz core duo. I read here that people mention problems regarding the fan. Something about it stops working after reboot and the computer overheats?

I had plans to install win xp on my computer and i saw on lenovos homepage that there are drivers for xp. Do you think it will work to put in XP instead of Vista or will I get the same fan-problem with overheating as a result?

The graphic card is an intel GMA X3100.

Maybe I have missed something in the discussion here, found this site via google. Was this fan-problem only when using Ubuntu or is it the same thing with win XP?

Sorry if I sound like a complete noob.

mvh ekano

---

### Post by chrismyers on 2008-02-15
> **ekano said:**
> Hi

Ive got the Lenovo 3000 N200 1.46ghz core duo. I read here that people mention problems regarding the fan. Something about it stops working after reboot and the computer overheats?

I had plans to install win xp on my computer and i saw on lenovos homepage that there are drivers for xp. Do you think it will work to put in XP instead of Vista or will I get the same fan-problem with overheating as a result?

The graphic card is an intel GMA X3100.

Maybe I have missed something in the discussion here, found this site via google. Was this fan-problem only when using Ubuntu or is it the same thing with win XP?

Sorry if I sound like a complete noob.

mvh ekano

Hi there,

If you are using a Windows environment, you are not affected by problems mentioned on the Ubuntu website.

Ubuntu is a brand of Linux. Linux is not Windows.

A particular kernel version in Linux causes the fan problem after resuming from hibernate (but this kernel has to be manually installed, so its not really a problem).

Ubuntu is a free alternative to Windows. It comes with many applications & is not vulnerable to viruses or spyware unlike Windows. Why not give it a try?

[http://www.ubuntu.com/](http://www.ubuntu.com/)

Cheers,

Chris.

---

### Post by barbedsaber on 2008-02-17
HI again, got my new 3000 n200 a while ago (I have the 15.4inchscreen) am lovnig it except random total freezes while using ff, and a sound thing.

the sound worked out of the box (gutsy) but when I plug headphones in, sound comes out of the headphones, and still comes out of the speakers. if the soloution is to add somthing to a file, do I add it at the end or what. thanks for your help

---

### Post by Ripfox on 2008-02-17
> **ekano said:**
> Hi

Ive got the Lenovo 3000 N200 1.46ghz core duo. I read here that people mention problems regarding the fan. Something about it stops working after reboot and the computer overheats?

I had plans to install win xp on my computer and i saw on lenovos homepage that there are drivers for xp. Do you think it will work to put in XP instead of Vista or will I get the same fan-problem with overheating as a result?

The graphic card is an intel GMA X3100.

Maybe I have missed something in the discussion here, found this site via google. Was this fan-problem only when using Ubuntu or is it the same thing with win XP?

Sorry if I sound like a complete noob.

mvh ekano

Yes, if it helps you, I have had overheating problems with these machines on Ubuntu and XP. It doesn't hurt to ask questions here, so don't get discouraged :)

---

### Post by yoni_m on 2008-02-17
Thanks this is realy a simple fix. It did it for me. :))

---

### Post by ekano on 2008-02-22
> **ripfox said:**
> Yes, if it helps you, I have had overheating problems with these machines on Ubuntu and XP. It doesn't hurt to ask questions here, so don't get discouraged :)

Hi, I have had my Lenovo 3000 N200 for a week now. So far im happy with it. But ive noticed how the fan goes in intervals up and down very often. Have you noticed this also? Read about it in a review [http://www.notebookreview.com/default.asp?newsID=3749&review=Lenovo+N200](http://www.notebookreview.com/default.asp?newsID=3749&review=Lenovo+N200) where it is described as the fan has "ADHD". 

I guess its manufactured that way... or do you think its bad or wrong if it goes up and down like that? This is my first laptop so I dont have any experinces regarding this area.

The machine was pre-installed with Vista and i have tweaked it a little but still its not a very good OS for this machine I can tell. 

I have plans on installing XP (saw on Lenovos homepage that its compitable with XP)  and I have read about it on forums something about that you have to creat a install disc with SATA-drivers. 

Do you think the fan will work unproperly with XP and better as it is now with Vista or is it the machines that has overheating-problems? What consequences has appeared on you computer? How come youve had overheating problems with your Lenovo 3000 N200 you think?

Thanks for help!

mvh Ekano

---

### Post by chrismyers on 2008-02-22
Hi ekano,

Did you know that you may be entitled to downgrade to XP from IBM for a handling fee if your laptop came with Vista Ultimate or Business?

I'm unaware of problems with XP, but using the original manufacturer disks must be step in the right direction to ensure all the correct drivers are loaded.

Check out this link:

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=VSTA-DWNGRD#downgrading](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=VSTA-DWNGRD#downgrading)

P.S. My last post may have appeared a little abrupt (after re-reading it). My apologies, It wasn't my intention.

Cheers. :D

---

### Post by javatyger on 2008-03-14
> **chrismyers said:**
> 
Sound does not work out-of-the-box, but this is simply fixed by adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo
 [/FONT]

OMG!!! THANK-YOU THANK-YOU!!! :guitar: You Rock!!!

I've been looking for this fix for sometime and I finally just came across this!!! THANK-YOU!!!
:KS

---

### Post by Zsola on 2008-03-29
Also Lenovo 3000 N200 user :)

Wlan not worked the first time, but after 2 days it just started working... i reinstalled the whole system (first time linux user :) ) and wlan worked perfectly. (on a side note: it is working better with wifi radar... or just a conicidence...)

Sound card fixed with the:
options snd-hda-intel single_cmd=1 model=lenovo

Webcam working as it should be (although am waiting for Pidgin to come up with video conferencing....)

Didnt tried fingerprint reader and hibernate, but will do that also.

In short: Thank you for the help!!!

---

### Post by simplejordon on 2008-03-30
Pidgin is unlikely to go by conferencings in near future...same as Meebo..I think one must have a software as [http://www.gomeetnow.com](http://www.gomeetnow.com) or if you wanna want freeware then Yugma is good alternative..

---

### Post by LODRazor on 2008-04-04
I too have a Lenovo 3000 n200....

Fixed the sound issue (thanks ChrisMyers)
Don't reall care about the fingerprint issue, don't use it
Card reader still is an issue...I saw on another post about the Lenovo that someone said that the card reader issue was an easy fix, but he did not detail the fix.....has anyone else been able to get their card reader working??
The only other issue I seem to have is the X3100 onboard video, but as it is blacklisted due to driver problems, hopefully it will be fixed with the next release.  My only real problem with the X3100 is not being able to enable Appearance options.  I am wondering if the problem with the driver is that it only will recognize 1mb of video memory.  The x3100 CAN utilize up to 128mb of ram if needed, and it seems to me that the driver is limiting the use of ram to 1mb, thus no Eye Candy in Appearance settings.  Does this make sense?

Anyway....if anyone has a fix for the card reader, please post!!!  Thanks in advance.

---

### Post by chrismyers on 2008-04-06
> Anyway....if anyone has a fix for the card reader, please post!!!  Thanks in advance.The latest version of Ubuntu (Hardy) supports the card reader. It's in beta at the moment (6th April) & is likely to remain in the finished version.

P.S. I still needed to do the sound fix in Hardy beta, but I submitted the 'Hardware Testing' report with the fix. Hopefully this will get noticed.

---

### Post by LODRazor on 2008-04-08
Thanks again, ChrisMeyers.....if the fix will be out at the end of this month, no need for me to install the beta, I can wait.  You would not happen to know if the X1300 will come off the Blacklist with the next update, do you???

---

### Post by LODRazor on 2008-04-09
LOLOLOL....actually....I could not wait!!!  Installed the Hardy beta last night and POOF!!!!  the X1300 video works well!!!!!!  I  now am able to enable all the desktop visual effects.  Plus...previously...I had installed AWN and it would not work at all, nothing.  Now AWN works flawlessly so I have a nice dock on the desktop.  I have not checked to see if the Intel chipset has been officially unblacklisted....I doubt it has....but just for anyone else with the X1300 video chipset...the Hardy beta works and I am assuming that when the stable release comes out at the end of the month, it will also work there.

---

### Post by staib on 2008-04-12
> **LODRazor said:**
>  POOF!!!!  the X1300 video works well!!!!!!  I  now am able to enable all the desktop visual effects... 
That is brilliant news!  This had been the one disappointment for me.  Sound already works, card reader works fine, not sure about the web cam, and I have already forgotten about the finger-print reader.  MS Vista was consigned to the digital bin months ago :)

---

### Post by limbodk on 2008-04-14
[http://www.linlap.com/wiki/Configuring+a+NVIDIA+graphics+chip+for+Ubuntu+7.10](http://www.linlap.com/wiki/Configuring+a+NVIDIA+graphics+chip+for+Ubuntu+7.10)

Used this to fix the graphics settings, works with full prettness options now. i had to use the terminal comands as the gui restricted driver options just crash on me.

[http://www.linlap.com/wiki/Getting+suspend+and+hibernate+working+in+Ubuntu+7.10](http://www.linlap.com/wiki/Getting+suspend+and+hibernate+working+in+Ubuntu+7.10)

This is a link to get the suspend working on the laptop, i got it to work so give it a go. just did up to point 2 didnt need to do point 3 on the list after the restart worked fine.

when i fixed the video drivers it killed the wifi, so plenty of messing about dont remember how i fixed it, to be honest i think it fixed its self after about 5 restarts...

Things work quite well still pretty dodgy in a lot of ways, like the bar at the top has all its icons on the right hand side in a mess. screen wont go to full res, and the net drops a bit.

Oh and the lenovo badge on the front is coming unstuck after a week out of the box!

I am running  Ubuntu 8.04 - the Hardy Heron beta and i did all the updates first.

---

### Post by LODRazor on 2008-04-14
It has been a few days now since I installed the Hardy beta and all the above still work just fine, HOWEVER>>>>>>>there are 2 things that are now broken:

1.  Network Manager has totally disappeared.  I did not uninstall it, I did not remove it, I did not delete it...it is just gone.  I tried reinstalling to no avail.  I posted about it a couple of times in other forum posts with no answer yet.  This has completely stumped me.

2.  GRUB has lost its mind!!!!  Yesterday, upon starting up my laptop, the laptop does it's post and goes to GRUB to start the OS menu (dual boot with XP Pro, XP on 1st partition, Ubuntu on 2nd) and just hangs with the word GRUB on the screen, nothing else.  No text input allowed, no cursor, ctrl+alt+delete does not work, ctrl +alt+f2 does not work, nothing...its just dead...no hd action...nothing.  I read A LOT of forum posts about how to redo GRUB to make it work, even rewriting GRUB to the mbr...nothing worked.

After getting totally pissed off....I reinstalled Gusty...even though it does not correctly drive my video.  If anyone has a clue why these 2 things happened, please post here....I really liked that Hardy fixed some of the issues with this laptop, but did not like that a couple of new even more serious problems showed up.  Thanks in advance.

---

### Post by chrismyers on 2008-04-15
Hi LODRazor. I cant offer any reason why your system got trashed. Remember that you were using a beta though, so some strange things can happen.

Regarding problems with Network-Manager. I managed to fix previous problems by deleting/renaming the networking directory in:

~/.gconf/system/

You MUST reboot after doing this, because I've found that just logging out & back in appears to remember previous settings.

I hope this helps if you get this problem in the future.

---

### Post by LODRazor on 2008-04-15
Thanks again, ChrisMeyers.  I as I stated, I am back running Gusty, and will wait for the STABLE version of Hardy...lololol.  Hopefully, the stable version will have those bugs worked out (crossing his fingers and praying)!!!!

---

### Post by Talkless on 2008-04-25
Hello guys.

Any news about N200 and 8.04 friendship? Has anyone upgraded to stable version? How it is?

---

### Post by TheRingmaster on 2008-04-25
maybe if you would actually specify your problems with hardy we could fix them. This happens every release you know, someone just says how crappy the latest is and walks away.

---

### Post by chrismyers on 2008-04-27
> **Talkless said:**
> 
Any news about N200 and 8.04 friendship? Has anyone upgraded to stable version? How it is?

OK.. Here's a summary:
[B]
[COLOR=Blue]I have a 3000 N200 with an nVidia card.[/COLOR][/B]

The final release of Hardy works great[FONT=Tahoma].

Grahics works with the native resolution of 1680x1050 using the open source nv driver (Though in a noticeably low colour bit depth) - The proprietary driver works great in full colour.

Wireless LAN works perfectly.

Wired LAN works perfectly.
 
Bluetooth works perfectly.

Webcam works perfectly - In Ekiga, set:

    edit>preferences>devices>video devices>V4L2

Sound still does not work out-of-the-box, but this is simply fixed by adding the following to etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo

The SD card reader now works in Hardy.

Sleep mode (lid closed) works in Hardy.

Hibernate (Fn-F12) now works fine in Hardy. *The CPU fan now works after recovering from hibernate.*
 
The fingerprint scanner is not recognized at all.[/FONT]

I hope this helps :o

---

### Post by Talkless on 2008-04-28
> **TheRingmaster said:**
> maybe if you would actually specify your problems with hardy we could fix them. 

I don't have any problem, because I don't have it. I am trying to choos a laptop with as less as possible problems with Ubuntu.

chrismyers summary looks great! Thank you.

---

### Post by Relus on 2008-04-28
Thank you Chrismyers!
Does someone have fixed the problems with the X3100 graphics?

Relus

---

### Post by TheRingmaster on 2008-04-30
> **Talkless said:**
> I don't have any problem, because I don't have it. I am trying to choos a laptop with as less as possible problems with Ubuntu.

chrismyers summary looks great! Thank you.

I was referring to LODrazor above actually.

---

### Post by Th3Doctor on 2008-05-02
Hi,

I'm not new to linux, but i'm new to actually trying to get everything to work on linux (up till now it didn't matter).

I have an N200 installed with Vista Business on top of which i installed the 8.04 release (hardy heron) on a virtual disk - using wubi.

It almost works perfect, out of the box i had support for:
 - Lan
 - Card Reader
 - Bluetooth
 - Graphics (intel 945gm)

What i'm looking for right now is how to make my wireless lan work, and how to check if my webcam is active/installed?

I have updated the wireless drivers with the newest iwlwifi drivers (the 02.05.08 ones) they load just fine but i think the wireless is turned off - as i see no wireless networks and am unable to manually connect to mine (the switch IS set to the on position as i do have bluetooth).

read through MOST of the thread and a bunch of other threads and bug reports, any suggestions on these 2 questions.

thanks in advance :)

---

### Post by gryzzly on 2008-05-04
> **chrismyers said:**
> OK.. Here's a summary:
[B]
[COLOR=Blue]I have a 3000 N200 with an nVidia card.[/COLOR][/B]

The final release of Hardy works great[FONT=Tahoma].

Grahics works with the native resolution of 1680x1050 using the open source nv driver (Though in a noticeably low colour bit depth) - The proprietary driver works great in full colour.

Wireless LAN works perfectly.

Hibernate (Fn-F12) now works fine in Hardy. *The CPU fan now works after recovering from hibernate.*[/FONT]

I hope this helps :o

Hi, Chris. 
Yesterday updated my Feisty to Hardy. After an update didn't get any wi-fi. So I thought maybe it's an upgrade issue (also, I got some problem during an upgrade process - it freezed and I had to hard reset it in the middle of installation process). So today's morning I formatted the hard drive on my lenovo laptop and installed Hardy from desktop installation disk. Installation passed without any problem, but after installation, again, no wi-fi. Sound was fixed as described. Sleep and Hibernate still doesn't work properly. (If i put it to sleep - it wakes up more time than it would boot from shutting down). And hibernate doesn't work at all - after I push Fn + F12 it starts to shout (front mic turns on somehow, on very sensitive mode, so horrible sound is going out of the speakers - this "microphone close to speakers" sound). That is very frustrating (especially since I was waiting for this release so long). 

If anybody knows any possible fixes you will be extremely welcome. Looking forward for help. Thanks

---

### Post by yeleek on 2008-05-05
> **LODRazor said:**
> I too have a Lenovo 3000 n200....

Fixed the sound issue (thanks ChrisMyers)
Don't reall care about the fingerprint issue, don't use it
Card reader still is an issue...I saw on another post about the Lenovo that someone said that the card reader issue was an easy fix, but he did not detail the fix.....has anyone else been able to get their card reader working??
The only other issue I seem to have is the X3100 onboard video, but as it is blacklisted due to driver problems, hopefully it will be fixed with the next release.  My only real problem with the X3100 is not being able to enable Appearance options.  I am wondering if the problem with the driver is that it only will recognize 1mb of video memory.  The x3100 CAN utilize up to 128mb of ram if needed, and it seems to me that the driver is limiting the use of ram to 1mb, thus no Eye Candy in Appearance settings.  Does this make sense?

Anyway....if anyone has a fix for the card reader, please post!!!  Thanks in advance.

Is there a fix for the card reader yet on gutsy?  I tried hardy - too unstable :(  

Thanks

---

### Post by chrismyers on 2008-05-05
> .....again, no wi-fi. Sound was fixed as described. Sleep and Hibernate still doesn't work properly. Oh dear.. It looks like hardware differs even within 3000 N200's.

The full model name of my system is:
[B][COLOR=RoyalBlue]
Lenovo 3000 N200 0769-B4G[/COLOR][/B]

My wireless works perfectly, lspci -v produces:

04:00.0 **Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)**
    Subsystem: Intel Corporation Lenovo ThinkPad T61
    Flags: bus master, fast devsel, latency 0, IRQ 217
    Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: [c8] Power Management version 3
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] Express Endpoint IRQ 0

I'm no expert, but Identifying your hardware is the first step in getting it working.

I would search for 'Intel' '4965' in Linux groups for more help if my card wasn't working.

Cheers.

---

### Post by gryzzly on 2008-05-05
Thank you, man. 
Full name of my model is lenovo 3000 n200 TY2BRIV - it is some differences between some models. And my wi-fi is actually Intel 3945ABG, checked everything I could, still didn't find real solution :( strange, cuz on Feisty everything worked like a clock. Thank you very much for your respond anyway :)

*btw does suspend and hibernate work for you? (I think my problem is that I can't use "nvidia" driver, it writes "not in use", even after I enable it.

---

### Post by Haalle on 2008-05-21
I have a Lenovo 3000 N200 0769-BNG
I am using Hardy Heron stable.
I have not tested the card and fingerprint readers.

Everything works fine except for two things:

1) Sound need chrismyers' fix to work.

2) When I turn the computer on after hibernating, the CPU fan does not work. It results in overheating and eventually the computer suddently turn off. I think it turns off because the CPU gets too hot. When I boot normally and after sleep mode, I don't have the problem. Otherwise hibernating works fine, but it is not much faster than a normal boot, so I just don't use hibernate mode anymore, though it would be nice if somebody has a real fix for the problem. 
I have also experienced the sound problem when I close the lid and when I go to hibernate mode. I think it is due to feeding, because the microphone is too close to the speakers. To avoid the sound, I simply turn off the microphone in Alsamixer.

---

### Post by igb on 2008-07-05
My HP laptop dies last week. There is a good offer on the N200 at the moment at [http://www.laptopsdirect.co.uk/Lenovo_3000_N200_0769_TY2BWUK/version.asp?tref=fpg-Lenovo%203000%20N200]("http://www.laptopsdirect.co.uk/Lenovo_3000_N200_0769_TY2BWUK/version.asp?tref=fpg-Lenovo%203000%20N200")

Looking at the specs this has the Nvidia card, but the specified max res is 1280x800. This isn't a problem for me. However, do you think that this model the same, or very similar to the one described in this thread?

If so it seems that everything like wifi, bluetooth and sound should work OK in Hardy.

Ian.

---

### Post by chrismyers on 2008-07-05
> **igb said:**
> My HP laptop dies last week. There is a good offer on the N200 at the moment at [http://www.laptopsdirect.co.uk/Lenovo_3000_N200_0769_TY2BWUK/version.asp?tref=fpg-Lenovo%203000%20N200](http://www.laptopsdirect.co.uk/Lenovo_3000_N200_0769_TY2BWUK/version.asp?tref=fpg-Lenovo%203000%20N200)

Looking at the specs this has the Nvidia card, but the specified max res is 1280x800. This isn't a problem for me. However, do you think that this model the same, or very similar to the one described in this thread?

If so it seems that everything like wifi, bluetooth and sound should work OK in Hardy.

Ian.

Hi Ian,

In my experience, Hardy works well with my 3000 N200.

I would certainly recommend a Lenovo.

Let's call on others watching this thread to see if they also agree??

---

### Post by igb on 2008-07-08
> **chrismyers said:**
> Hi Ian,

In my experience, Hardy works well with my 3000 N200.

I would certainly recommend a Lenovo.

Let's call on others watching this thread to see if they also agree??

Thanks Chris. I went ahead and ordered one and it arrived this morning. So far everything except the fingerprint reader (not bothered about it) works in Hardy.

The sound worked when I applied the fix to alsa-base. However, the volume is quite low, even after turning up all the outputs using alsamixer.

Also it turns out that my HP notebook expired on the last day of its three year warranty. HP are supposed to be coming today to fit a new motherboard. So I can give the HP to one of my children.

Ian.

---

