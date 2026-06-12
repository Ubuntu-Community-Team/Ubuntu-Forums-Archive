---
title: "Asus Eee 900"
date: 2008-05-10
forum: Hardware
---

### Post by AJH20 on 2008-05-10
So I got a new EEE 900 ([http://www.play.com/PC/PCs/4-/5429235/Asus-Eee-PC-900-W-Intel-Mobile-1GB-20GB-8-9-Linux-Laptop-Notebook-White/Product.html](http://www.play.com/PC/PCs/4-/5429235/Asus-Eee-PC-900-W-Intel-Mobile-1GB-20GB-8-9-Linux-Laptop-Notebook-White/Product.html)) and immediately got rind of Xandros (it was awfully bad). Got Ubuntu 8.04 on it without too much problems but there is certain things causing problems....

[LIST]
[*]Fn + F1 (Sleep) Doesn't really work (the laptop goes to sleep, but gets stuck on a black page with a million lines of gobble, so it can not be woken, etc)
[*]Fn + F2 (Wifi) Doesn't do anything
[*]Fn + F5 (VGA Output) Doesn't seem to work, but i think i found a fix, just too lazy to sort it right now
[*]Fn + F6 (Task Manager) Innactive
[*]Fn + F7, F8, F9 (Mute, Volume down, Volume up) All innctive
[/LIST]

Can anyone recommend anything for these? Also flash video while in full screen can sometimes be a bit slow... Can anyone recommend anything for this? Although I have a feeling overclocking it a bit will be the only way...

---

### Post by happyisland on 2008-05-10
I don't have any answers for you, but I will be watching this area with interest since I am planning to buy an Eee 900 as soon as they become available in my part of the world. 

One question: does the multitouch trackpad work with all the bells and whistles in Ubuntu?

---

### Post by jordey24 on 2008-05-10
i'm not sure of this because i dont have an asus eee but its maybe because it was configured to xandros,maybe ubuntu has other key combinations...

---

### Post by 77_Chris on 2008-05-10
Maybe this will help you:

[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly")

I'm really interested in how much space of the SSD your installation occupies.

Cheers, Chris

---

### Post by AJH20 on 2008-05-11
> **77_Chris said:**
> Maybe this will help you:

[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly")

I'm really interested in how much space of the SSD your installation occupies.

Cheers, Chris

Well, I have the linux version which has 2 SSD's. One is 15.8GB in size and the other is 4.2GB which I have Ubuntu and Xandros installed to (I was an idiot and didn't format it) which takes up 3.2GB in space. I might reformat and start again in the next few days though... Is there a way in which I can strip down Ubuntu that I can use in windows? Something like Nlite?

Oh and the multitouch works fine from what ive tested so far. I dunno if the "zoom" works though, it didn't work in firefox thats for sure but it could be application dependant.

---

### Post by AJH20 on 2008-05-11
Pah... After about 20 modifications I realised the sound is now not working... This is just getting annoying now. The only thing I want to work is the sound correctly, yet its the only thing that doesn't. Grr!

---

### Post by netcrusher88 on 2008-05-11
Not sure how you want to strip down Ubuntu, but if you're reinstalling anyway you should use Xubuntu - it's recommended for the Eee as XFCE is much lighter than Gnome.

---

### Post by Tomatz on 2008-05-11
I have an eeepc running stock xubuntu gutsy.

Ubuntu is too heavy for the eeepc so in a terminal do this (hopefully you will have enough space):

```
sudo apt-get install xubuntu-desktop
```

Logout then change session to xubuntu (xfce), login.

Then go here:

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

Download the ubuntu eeepc support scripts and run them to get x/ubuntu running on the eeepc correctly.

**Or alternitavly**

Download and install this on your eeepc its a custom version of xubuntu made specifically for the eeepc:

[http://code.google.com/p/eee-ubuntu-support/](http://code.google.com/p/eee-ubuntu-support/)

And yes you can run compiz on it :)

---

### Post by AJH20 on 2008-05-11
What do I do with this .tgz file from google code?

PS: I see youre in Cambridge too. :)

---

### Post by Tomatz on 2008-05-11
The instructions are in the readme in the .tar:


> 0) read the scripts (tweak-gnome.sh, install.sh) to KNOW what they are going to modify

1) setup gnome (nothing dangerous here)

run ./tweak-gnome.sh

2) setup the kernel, modules, wifi, hotkeys, acpi, overclocking...

run sudo ./install.sh [tweaks] 
where the tweaks can be:

modules: install drivers for the eee hardware (work only with the default kernel)
acpi: install acpi/hotkeys scripts
clock: install realclocking scripts (set speed modulation between 600 and 900Mhz)
wifi: install hal scripts to use with madwifi
sound: fix microphone, halt and openal (crackling in games)
init: enable parallelized init, fix hal/dbus precedence
sources: setup software sources (you still need to setup software updates manually)
x11: install xandros video driver for skype 2.0
all: all the above

examples:
sudo ./install.sh modules clock

3) Reboot.

setup your wifi connection and enjoy ubuntu on your eee.



Basically:

Extract the .tar on your **desktop**.

Then in a terminal

```
cd ~/Desktop/eee-ubuntu-support_v0.7 
```

Then in the same terminal

```
sudo ./install.sh all
```

Then

```
sudo ./tweak-gnome.sh
```

Then reboot ;)


P.s 

I grew up in cambridge (chesterton) but now live in letchworth (20 miles down the road) where i have lived for the past 2 years.

All my family and friends are still down there though.

Wish i was on parkers piece right now though lol the weather is lovely.

---

### Post by AJH20 on 2008-05-11
Ok, going to have a little play right now. Thanks for the help.

Ah, I live in Chesterton too! I spent my whole day on Parkers Piece, been stonking today. :)

**Edit:** Ah I just realized it's for Ubuntu 7 (Gutsy Gibbon), so it won't actually work. Reckon it'll be worth rolling back?

---

### Post by Tomatz on 2008-05-11
> **AJH20 said:**
> Ok, going to have a little play right now. Thanks for the help.

Ah, I live in Chesterton too! I spent my whole day on Parkers Piece, been stonking today. :)

**Edit:** Ah I just realized it's for Ubuntu 7 (Gutsy Gibbon), so it won't actually work. Reckon it'll be worth rolling back?


Gutted :(

No better place to be on a sunday afternoon.

As for rolling back. I would just install eeexubuntu it has all the fixes already implimented. Just install and your good to go.

Get it below:

[http://wiki.eeeuser.com/ubuntu:eeexubuntu:home?s=eeexubuntu](http://wiki.eeeuser.com/ubuntu:eeexubuntu:home?s=eeexubuntu)

**Small world though** :)

---

### Post by AJH20 on 2008-05-11
OK, i'll give it a try, but this is going to ruin my resolution I can tell already...

---

### Post by AJH20 on 2008-05-11
OK, managed to get it all working... The look and feel of it is alot better... Couple of little things from Ubuntu missing though, but i prefer this. Just one thing though... No sound at all! Any ideas?

I think its because I have the new 900 model and not 700/701 so it's not actually designed for this...

---

### Post by solitaire on 2008-05-11
Keep us up to date with the Sound problems ;)

I'm thinking of picking one up in a few weeks/months depending on if I get into Uni or not...

The Eee 900 would be better than this ancient laptop (and it won't kill my shoulder / back every time I lug it somewhere!)

---

### Post by AJH20 on 2008-05-11
That is exactly what I use mine for, just carrying around campus. I had a huge on 15.4"  laptop but I never really used it because my PC is much more powerfull with the added bonus of 2*24" monitors ;)

If I can get the sound working, then i'm all sorted. Anyone know of a descent JDE aswell? Something along the lines of jGrasp?

---

### Post by AJH20 on 2008-05-11
[http://forum.eeeuser.com/viewtopic.php?pid=251853](http://forum.eeeuser.com/viewtopic.php?pid=251853)

It would appear I am not the only one with this problem...

---

### Post by 77_Chris on 2008-05-12
Although you switched to eeexubuntu in the meantime, this could still be interesting for you:
[COLOR="Blue"][http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")[/COLOR]

The post shows some ways to clean up an ubuntu installation and to save space.

And this guy claims that sound works on his 900 running Ubuntu 8.04 with the help of a shell-script which can be downloaded from his site:
[COLOR="Blue"][http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/]("http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/")[/COLOR]

I could not test this yet, my 900 is still somewhere on its way from GB to Austria. Perhaps you'll give it a try and post the results here.

Cheers, Chris

---

### Post by AJH20 on 2008-05-12
I did originally have sound working while running Ubuntu 8.04, but after I did a few tweaks in terminal it just stopped working... Im not sure what did it as it took me a while to realise though! I want to stick with EEEXUbuntu for now, hopefully in the next few weeks as more and more people recieve their EEE 900's more fixes will appear.

---

### Post by Tomatz on 2008-05-12
> **AJH20 said:**
> I did originally have sound working while running Ubuntu 8.04, but after I did a few tweaks in terminal it just stopped working... Im not sure what did it as it took me a while to realise though! I want to stick with EEEXUbuntu for now, hopefully in the next few weeks as more and more people recieve their EEE 900's more fixes will appear.


Try opening up "volume control" then click "file" and change the device (e.g. alsa to oss) if you can.

---

### Post by mivo on 2008-05-12
Oh, I didn't realize the 900er model with the 20 GB SSD and the 8.9" display was already out. My German vendor says it'll be in stock in August. Hrm. I pre-ordeted one just a couple days ago.

---

### Post by AJH20 on 2008-05-12
Changed the device from both #default and HDA Intel and nothing... Although the Fn buttons for it seem to be working now (the sliders move when pressed)... Just nothing actually comes out!

---

### Post by AJH20 on 2008-05-12
> **mivo said:**
> Oh, I didn't realize the 900er model with the 20 GB SSD and the 8.9" display was already out. My German vendor says it'll be in stock in August. Hrm. I pre-ordeted one just a couple days ago.

I ordered mine from Play.com and they said it would be released on the 11th May (yesterday). I was a little shocked when it turned up on my door nearly 3 weeks ago.

---

### Post by Tomatz on 2008-05-12
Does the headphone jack work?

---

### Post by decibyte on 2008-05-12
Hey guys


I just brought home a nifty 900 from London and installed Hardy on it.

I followed this guide: [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly) afterwards as #4 (77_Chris) mentioned to get everything work. And it really does. It works like a charm.

It was really easy. Only problem was that wifi stopped working after doing the hotkey stuff. But simply re-running the wifi commands from the beginning of the guide made it work again.

77_Chris: After this clean install it occupies about 2.15 GB. Well... Actually I also installed a few extra programs (vlc, gparted and ccsm).

---

### Post by decibyte on 2008-05-12
Well... I just realized that neither webcam nor microphone works. i'm trying to find some help somewhere.

---

### Post by decibyte on 2008-05-12
Looks like I'm spamming this thread...

For those who've got problems with sound disappearing after fiddling around:

I just ran into the same problem while trying to get the microphone work. Several sites mention that editing /etc/modprobe.d/alsa-base and adding the line "options snd-hda-intel model=3stack-dig" will make the microphone work. That's true. But it also makes my sound disappear. I got no clue what this line actually does, but maybe somebody can tell me (and others) what to do to get both microphone AND sound to work together?

---

### Post by corncob on 2008-05-12
I just got an eee 700 and am looking for the 900 to be available here but how does one get to a terminal window in Xandros?

---

### Post by decibyte on 2008-05-12
corncob, press ctrl+alt+t

---

### Post by 77_Chris on 2008-05-13
> **decibyte said:**
> 
77_Chris: After this clean install it occupies about 2.15 GB. Well... Actually I also installed a few extra programs (vlc, gparted and ccsm).

That sounds great.

I've read somewhere that compiz can cause problems with the cam and that for some prople turning it off temporarily made the webcam run.

Unfortunately I can't remember where I found that. Perhaps a quick search on the web will show some results.

Cheers, Chris

---

### Post by AJH20 on 2008-05-14
> **decibyte said:**
> Looks like I'm spamming this thread...

For those who've got problems with sound disappearing after fiddling around:

I just ran into the same problem while trying to get the microphone work. Several sites mention that editing /etc/modprobe.d/alsa-base and adding the line "options snd-hda-intel model=3stack-dig" will make the microphone work. That's true. But it also makes my sound disappear. I got no clue what this line actually does, but maybe somebody can tell me (and others) what to do to get both microphone AND sound to work together?

Well Im going to get rid of EEEXUbuntu again later and stick Ubuntu 8.04 on here again and try getting it all to work again. I'll let you know how I get on... Would be awesome to get it all working though.

---

### Post by AJH20 on 2008-05-15
Ok, i've given up now. I've been fiddling for days and still can't get everything to work so until a "EEE 900 Ubuntu/Fedora" package becomes available i'm leaving it.

---

### Post by decibyte on 2008-06-09
hey guys

some weeks have passed now... have any of you had any luck with the microphone and webcam issues?

btw: important note to others like me who wonders why the hotkeys and wifi stops working after some time. i returned to this great guide: [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly) - and followed the instructions on how to make hotkeys and wifi work again. and it did. afterwards i noticed that it also says in the guide: "System updates (specifically, new kernels) will reverse these changes." so mark these words: re-run the commands if these things stop working. i've waited more than a week for them to "just work again". a waste of time :)

---

### Post by starcannon on 2008-06-09
[SIZE="4"]**UPDATE**[/SIZE]
Just realized this is for an Eee900, not sure how much of my Eee701/702 experience will help, but look my post over anyway, may be some useful info in it.

I use this script on two 4g's and an 8g, I like it better than the .7 script which I have also used. I also have a 2g but I just run puppeee on it.

[http://code.google.com/p/ubuntu-eee/downloads/list](http://code.google.com/p/ubuntu-eee/downloads/list)

I have not put Hardy 8.04 on an Eee yet, I do know that script pack works great with Gutsy 7.10, it makes everything work perfectly.

If you want to suspend resume with an SDHC card in the MMC socket you will need to custom compile a 2.6.25 kernel for that, I keep meaning to get around to it, but am currently sorting out an xorg.conf file for a cloudbook.

Some other things to look at are some of the various bios revisions and customs available at eeeuser.com, I think the best way to deal with the cpu is to enable it to 900mhz from the bios, the driver method works but is a little flaky and not as stable as the bios method.

---

### Post by starcannon on 2008-06-09
When I have a bunch of custom modules and things I am always sure to uncheck any kernel updates in the update manager, it just makes life easier, if how ever you did upgrade your kernel, you can always go back the the kernel that things worked with, often times it will still be available in the grub menu when you boot, and if you edit your /boot/grub/menu.list file you can even set your working kernel as your default. 

As an aside, I may look into "pinning out" my system at least as far as kernels go, I just haven't done it enough yet to be able to write a tutorial, dig around here and google on "how to pin out ubuntu" or something like that. Pinning lets you freeze your system to a known good working state, and if you do it right you can still get your security updates.

GL


> **decibyte said:**
> hey guys

some weeks have passed now... have any of you had any luck with the microphone and webcam issues?

btw: important note to others like me who wonders why the hotkeys and wifi stops working after some time. i returned to this great guide: [http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly) - and followed the instructions on how to make hotkeys and wifi work again. and it did. afterwards i noticed that it also says in the guide: "System updates (specifically, new kernels) will reverse these changes." so mark these words: re-run the commands if these things stop working. i've waited more than a week for them to "just work again". a waste of time :)

---

### Post by decibyte on 2008-06-09
> **starcannon said:**
> 
I use this script on two 4g's and an 8g, I like it better than the .7 script which I have also used. I also have a 2g but I just run puppeee on it.

[http://code.google.com/p/ubuntu-eee/downloads/list](http://code.google.com/p/ubuntu-eee/downloads/list)

I tried that script on my 900 and **it really screwed my settings**. I used the sound and X11 parts of it, with no luck on the mic and cam issues. **I can't stress that enough: Do not use that script. It's not even maintained anymore.** Instead it ruined my screen resolution, defaulting back to 640x480, and my keyboard settings also seems to have been messed up by it (but I really can't tell, as I've tried so many things to get the resolution back on track). 

> **starcannon said:**
> Some other things to look at are some of the various bios revisions and customs available at eeeuser.com, I think the best way to deal with the cpu is to enable it to 900mhz from the bios, the driver method works but is a little flaky and not as stable as the bios method.

This 900mhz works out of the box on the 900, so don't bother tweaking it.

---

### Post by decibyte on 2008-06-09
Great news!

I just got the webcam to work. Following the instructions in post #12 here: [http://forum.eeeuser.com/viewtopic.php?id=26570](http://forum.eeeuser.com/viewtopic.php?id=26570)

No restart needed. Sweet.

Well, what it says:

1. sudo aptitude install subversion
2. svn co svn://svn.berlios.de/linux-uvc/linux-uvc/trunk linux-uvc
3. cd linux-uvc
4. sudo make
5. sudo make install
6. sudo modprobe -r uvcvideo
7. sudo mv /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko.original
8. sudo cp uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko
9. sudo modprobe uvcvideo

Hope this will work for you guys too.

Now I only need to get the microphone to work.

---

### Post by decibyte on 2008-06-09
Regarding the microphone issue, I've found this one, #6: [http://forum.eeeuser.com/viewtopic.php?id=29307](http://forum.eeeuser.com/viewtopic.php?id=29307)

I don't have any luck. Can anybody get it to work?

---

### Post by starcannon on 2008-06-10
sorry if that script was a set back man :(

other than getting some of the peripherals up how are you liking the 900? It looks sweet, am almost wishing I'd have waited and got that instead of the 8g.

---

### Post by Junzuki on 2008-06-10
Re webcam issues:

In stock OS (Linux on pc900) the webcam is turned off in bios so needs to be turned on there to allow it to work in any new OS.

If you have installed uvcvideo to get webcam working try also guvcview from: [url="http://developer.berlios.de/project/sho … up_id=8179"]

Download the deb file guvcview_0.9.0_i386.deb double click on the file to install with package installer. Its much better than anything else i have found for eee.

No problem running it with compiz.

Re Microphone:

I've been on the trail for days to solve this in 8.04 to the extent yesterday i went back to stock OS just to make sure it was working originally (I wiped and went 8.04 before checking everything worked stock).It was but very poorly, very quit (low gain) loads of static type noise. I reloaded 8.04 and did all the fixes and tried mic again still now output or recording from sound recorder. Then i put a head set in the external ports and it worked perfectly.

I deduce from this that the mic is either faulty (maybe a cable screening problem)or low quality (maybe one way to keep the price down) - solution live without and use a headset or open the box and replace with a better one. Anyone done this?

Otherwise i'm happy with the 900 and running Heron - everything works great bar the mic.

BTW if you want some nice eye candy and free up some screen space try Avant Window Navigator. A good install guide here: 

[url="http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml"]

---

### Post by finny388 on 2008-07-09
[Ubuntu 8.04 (Hardy Heron) on the Asus Eee PC]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly")

What version of EEE is this wiki intended for? Has anyone tried it lately on their 900? I just got mine and I want some flavor of a stable, working Ubuntu version.

A fork of ubuntu just for the eee is very exciting. Reminds me of early apple or commodore/amiga. An affordable device with software tailored for that particular hardware.

---

### Post by postmortemMT on 2008-07-12
Hey guys,

May I introduce myself? I'm Sam Spiteri from Malta and I'm new to the forums.

Its very nice to see such a forum filled with so much solid support.

I recently purchased the Asus 333 900 with Linux Xandros installed and oh boy how much I love it! 

but I'm still a newb when it comes to linux systems.

I was wondering if any of you know of an installation add-on or package which contain useful programs ala a good virus scanner, cc cleaner, anti-spyware, optimization tools etc. etc.

I would greatly appreciate any suggestions to make my laptop a better machine and also learn more about Linux.

Regards And Thanks,
Sam

---

### Post by Tomatz on 2008-07-12
> **postmortemMT said:**
> Hey guys,

May I introduce myself? I'm Sam Spiteri from Malta and I'm new to the forums.

Its very nice to see such a forum filled with so much solid support.

I recently purchased the Asus 333 900 with Linux Xandros installed and oh boy how much I love it! 

but I'm still a newb when it comes to linux systems.

I was wondering if any of you know of an installation add-on or package which contain useful programs ala a good virus scanner, cc cleaner, anti-spyware, optimization tools etc. etc.

I would greatly appreciate any suggestions to make my laptop a better machine and also learn more about Linux.

Regards And Thanks,
Sam

This is going to seem real alien to you but you don't need antivirus, antispyware or anything like ccleaner. There are no real life linux viruses or spyware. Ccleaner or anything like it is needless because of the nature of file management in Linux. Just clear your browser cache in firefox every now and then.

I run compiz fusion on my eeepc openbox/gnome ubuntu install. It looks like this:

[http://www.youtube.com/watch?v=ZzzhEs9XGuE](http://www.youtube.com/watch?v=ZzzhEs9XGuE)

Wow huh...

Bet you thought you needed a much more powerful pc to do that....

Well thats what microsoft want you to believe ;)

---

### Post by postmortemMT on 2008-07-12
> **Tomatz said:**
> This is going to seem real alien to you but you don't need antivirus, antispyware or anything like ccleaner. There are no real life linux viruses or spyware. Ccleaner or anything like it is needless because of the nature of file management in Linux. Just clear your browser cache in firefox every now and then.

I run compiz fusion on my eeepc openbox/gnome ubuntu install. It looks like this:

[http://www.youtube.com/watch?v=ZzzhEs9XGuE](http://www.youtube.com/watch?v=ZzzhEs9XGuE)

Wow huh...

Bet you thought you needed a much more powerful pc to do that....

Well thats what microsoft want you to believe ;)


Hey Man! Cheers for the quick reply :)

To be honest it doesn't seem alien to me because I've known for years that Linux is a very safe OS but I'm so used to mantaining my PC systems daily that it will be weird not mantaining one of my PCs lol. In this case its Alien to me :p and thanks regarding the clear firefox cache tip. 

I'm gonna check out the vid in a few.. might I ask what compiz fusion consist of please? BTW My Asus Eee 900 is with the factory built Linux Xandros OS. I haven't yet made any modifications as I mentioned before I'm still a newb. 

:) thanks again!

EDIT: Just saw the video and lol. microSOFT suxors as always.

---

### Post by Tomatz on 2008-07-12
> **postmortemMT said:**
> Hey Man! Cheers for the quick reply :)

To be honest it doesn't seem alien to me because I've known for years that Linux is a very safe OS but I'm so used to mantaining my PC systems daily that it will be weird not mantaining one of my PCs lol. In this case its Alien to me :p and thanks regarding the clear firefox cache tip. 

I'm gonna check out the vid in a few.. might I ask what compiz fusion consist of please? BTW My Asus Eee 900 is with the factory built Linux Xandros OS. I haven't yet made any modifications as I mentioned before I'm still a newb. 

:) thanks again!

In a nutshell:

Compiz fusion is a 3D (open GL) window manager that you can use to give full 3d effects to the linux desktop. 

To get the most out of your eeepc i would suggest installing ubuntu as the default xandros is crud. The easiest way to do this would be to use a usb cd/dvd drive, just download the eeexubuntu .iso [HERE]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home") and burn it to disc. It is a customised version of ubuntu (or more correctly xubuntu) made specifically for the eeepc and has full hardware compatability.

If you do not have a usb cd/dvd drive there are tutorials to install ubuntu from a usb flash drive (though this can be tricky for a new user).

---

### Post by postmortemMT on 2008-07-12
> **Tomatz said:**
> In a nutshell:

Compiz fusion is a 3D (open GL) window manager that you can use to give full 3d effects to the linux desktop. 

To get the most out of your eeepc i would suggest installing ubuntu as the default xandros is crud. The easiest way to do this would be to use a usb cd/dvd drive, just download the eeexubuntu .iso [HERE]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home") and burn it to disc. It is a customised version of ubuntu (or more correctly xubuntu) made specifically for the eeepc and has full hardware compatability.

If you do not have a usb cd/dvd drive there are tutorials to install ubuntu from a usb flash drive (though this can be tricky for a new user).

Thanks for the intelligent reply mate. To be honest it already passed through my mind to install eeeXubuntu and remove Xandros.

A lot of Asus eee users seem to have done the same and its a much more user friendly and stronger OS from the looks of it.

I'll give it a shot :D and it seems I'm gonna do it the hard way since I don't own an external USB cd\dvd drive. Oh well.. ;)

---

### Post by postmortemMT on 2008-07-12
I've managed to produce a eeeXubuntu bootable USB pendrive and I'm currently trying to install eeexubuntu on my Asus eee 900.

It is constantly telling me the following errors: 

The test of the file system with type ext3 in partition 1 of SCSI2 (0.1.0)(sdb) found uncorrected errors.

If you do not go back to partitioning menu and correct these errors, the partition will be used as is.
______________________________________________

The attempt to mount a file system with type swap in SCS12 (0.0.0)
partition #5 (sda) at none failed.

You may resume partitioning from the partitioning menu.

Those are the errors the installation is giving me. Any ideas how I can sort it out and install eeexubuntu?

Thanks Again Guys,
Sam Spiteri

---

### Post by Tomatz on 2008-07-12
> **postmortemMT said:**
> I've managed to produce a eeeXubuntu bootable USB pendrive and I'm currently trying to install eeexubuntu on my Asus eee 900.

It is constantly telling me the following errors: 

The test of the file system with type ext3 in partition 1 of SCSI2 (0.1.0)(sdb) found uncorrected errors.

If you do not go back to partitioning menu and correct these errors, the partition will be used as is.
______________________________________________

The attempt to mount a file system with type swap in SCS12 (0.0.0)
partition #5 (sda) at none failed.

You may resume partitioning from the partitioning menu.

Those are the errors the installation is giving me. Any ideas how I can sort it out and install eeexubuntu?

Thanks Again Guys,
Sam Spiteri

I would go back to partitioning and set up your disk like this:

Enter manual partitioning and delete all partitions.

Set up your main partition as **EXT2** (NOT 3) and set the mount point to "**/**".

Then create a small partition of about **128mb** and set it to **SWAP** (virtual ram partition).

Done ;)

---

### Post by postmortemMT on 2008-07-12
> **Tomatz said:**
> I would go back to partitioning and set up your disk like this:

Enter manual partitioning and delete all partitions.

Set up your main partition as **EXT2** (NOT 3) and set the mount point to "**/**".

Then create a small partition of about **128mb** and set it to **SWAP** (virtual ram partition).

Done ;)

Thanks for the advice.

Now I'm encountering a new problem.

I had switched off my Asus for a while and now switched it on again, booting from the USB flashdrive.

Now its giving me this error: 

Missing operating system
error 15

and will not continue.

Don't tell me I need to install Asus eee's Xandros back?

EDIT: Solved the problem my self and till now the installation is working ;)

I'll post new results later;)

---

### Post by Tomatz on 2008-07-12
> **postmortemMT said:**
> Thanks for the advice.

Now I'm encountering a new problem.

I had switched off my Asus for a while and now switched it on again, booting from the USB flashdrive.

Now its giving me this error: 

Missing operating system
error 15

and will not continue.

Don't tell me I need to install Asus eee's Xandros back?

EDIT: Solved the problem my self and till now the installation is working ;)

I'll post new results later;)

Ahh cool ;)

Good luck!

---

### Post by postmortemMT on 2008-07-12
> **Tomatz said:**
> Ahh cool ;)

Good luck!

Eureka! I managed to install Xubuntu but with one fault. It seems my 4GB HD is nowhere to be found and I only have my 12gb HD available. Is there a way I can get the 4GB HD back?

BTW: can somebody please tell me any useful\everyday programs I need to install? (example: pdf readers, microsoft office, movie\audio players bla bla etc.)

Again I appreciate the help :)

Regards,
Sam Spiteri

---

### Post by Tomatz on 2008-07-12
Cool ;)

To fix the issue i will need some information from your system. 

Open a terminal and type:

```
sudo fdisk -l
```

Then post the output of that command (here).


Now open a terminal and type:

```
gedit /etc/fstab
```

Now copy the contents of that text (config) file and post it with the output of the other command.

:)

---

### Post by postmortemMT on 2008-07-13
> **Tomatz said:**
> Cool ;)

To fix the issue i will need some information from your system. 

Open a terminal and type:

```
sudo fdisk -l
```

Then post the output of that command (here). 

[http://img137.imageshack.us/img137/9347/dsc03486my1.jpg](http://img137.imageshack.us/img137/9347/dsc03486my1.jpg)

> **Tomatz said:**
> 
Now open a terminal and type:

```
gedit /etc/fstab
``` 

Now copy the contents of that text (config) file and post it with the output of the other command.

:) 

[http://img228.imageshack.us/img228/4569/dsc03488wa7.jpg](http://img228.imageshack.us/img228/4569/dsc03488wa7.jpg)

Those are the outputs I received. 

Thanks again for the help :)

---

### Post by Tomatz on 2008-07-13
> **postmortemMT said:**
> [http://img137.imageshack.us/img137/9347/dsc03486my1.jpg](http://img137.imageshack.us/img137/9347/dsc03486my1.jpg)



[http://img228.imageshack.us/img228/4569/dsc03488wa7.jpg](http://img228.imageshack.us/img228/4569/dsc03488wa7.jpg)

Those are the outputs I received. 

Thanks again for the help :)

Sorry i should have explained better.

First, open a terminal and type:

```
sudo apt-get install gedit
```

This will install **gedit** the gnome text editor

Then run the 2 commands from my previous post. 

**Copy and paste** the output of **sudo fdisk -l** **from the terminal to the forums**.

When you run the second command a config file will open in **gedit** just **copy and paste the text from the file to the forums**.

;)

---

### Post by DagMan on 2008-07-14
> **decibyte said:**
> Looks like I'm spamming this thread...

For those who've got problems with sound disappearing after fiddling around:

I just ran into the same problem while trying to get the microphone work. Several sites mention that editing /etc/modprobe.d/alsa-base and adding the line "options snd-hda-intel model=3stack-dig" will make the microphone work. That's true. But it also makes my sound disappear. I got no clue what this line actually does, but maybe somebody can tell me (and others) what to do to get both microphone AND sound to work together?
model=auto for the 900

---

### Post by gerkin on 2008-08-04
Hi

I have been running a custom version of Hardy on an Eeepc 900 for several weeks, it seems really good

everything seems to work fine out of the box; although the microphone is still a bit flaky

available from:

[http://array.org/ubuntu/index.html](http://array.org/ubuntu/index.html)

---

### Post by cw1925 on 2008-08-04
Does anyone know how to change the settings for what Xandros (I'm assuming that's the default OS) does when you close the screen?  I'm wanting it to not go to Standby Mode, and just stay active.  I've tried everything, but I'm thinking this is a better job for the command-line.

---

### Post by peaz3001 on 2008-08-26
i found a solution for the sound and mic!

maybe its already out there but ive found it myself which makes me proud ;-)

allrighty then

go to ```
/etc/modprobe.d/
``` using ```
sudo nautilus
``` or whatever way you like

2. there you look for a file named **snd-hda-intel**

3. open the file

4. notice this line: ```
options snd-hda-intel model=3stack-dig
``` (thats gonna be easy its the only one probably)

5. change **3stack-dig** to **[COLOR="Red"]auto[/COLOR]**

6. listen to your own recordings on the eee

---

### Post by FrankVdb on 2008-10-15
> **Tomatz said:**
> 
Then create a small partition of about **128mb** and set it to **SWAP** (virtual ram partition).
Done ;)

This is a bad idea for a solid-state disk. You should avoid swapping altogether because this can cause lots of write operations to your disk, which you'll want to avoid since writing to an SSD is much slower than to a conventional hard drive. 

1 gig of RAM memory is more than enough, you're little PC will never go beyond that threshold unless you'll be using it for some heavy multimedia editing. 

Partition your system manually without a swap partition.

The same person also advised to install gedit on a Xubuntu system. That is absolutely not necessary. You can simply use mousepad to edit scripts and files.

---

### Post by Tomatz on 2008-10-16
> **FrankVdb said:**
> This is a bad idea for a solid-state disk. You should avoid swapping altogether because this can cause lots of write operations to your disk, which you'll want to avoid since writing to an SSD is much slower than to a conventional hard drive. 

1 gig of RAM memory is more than enough, you're little PC will never go beyond that threshold unless you'll be using it for some heavy multimedia editing. 

Partition your system manually without a swap partition.

The same person also advised to install gedit on a Xubuntu system. That is absolutely not necessary. You can simply use mousepad to edit scripts and files.


Mine was a 701 (now been ebayed) which only has 512 and as to the excessive read/writes killing the ssd, I weren't planning on keeping it for 5 years ;)


SSD'S ARNT THAT SENSITIVE GUYS!

---

### Post by chenn on 2008-10-18
What is the better option for the eee 900, installing the ubuntu 8.10 in a couple of days or the special eee version?

---

### Post by FrankVdb on 2008-11-02
> **Tomatz said:**
> 
SSD'S ARNT THAT SENSITIVE GUYS!

I didn't say that. I only said you'd want to avoid a lot of write operations to an SSD disk because it will slow down your system considerably.

---

### Post by AJH20 on 2008-12-10
> **chenn said:**
> What is the better option for the eee 900, installing the ubuntu 8.10 in a couple of days or the special eee version?

[http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/)

I've been using this now. New version on 1st Jan 2009...

---

