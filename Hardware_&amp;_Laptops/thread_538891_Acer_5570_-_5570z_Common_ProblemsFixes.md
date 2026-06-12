---
title: "Acer 5570 - 5570z Common Problems/Fixes"
date: 2007-08-30
forum: Hardware &amp; Laptops
---

### Post by mrfr0g on 2007-08-30
I just recently purchased an Acer Aspire 5570z notebook computer, and my love of Ubuntu on my desktop pushed me to install it on the notebook as well. Like most people I did run in to a few snags, such as wireless support, or sound issues. I'd like to dedicate this thread to pulling together the fixes for this specific model, and share some of the problems, and fixes to them.

Please note, these are fixes for Fiesty Fawn 7.04

Wireless:
I had alot of issues with finding out how to get my wireless to work, an lspci showed me the card was there, but didn't know what it was

Ethernet Controller: Atheros Communications, Inc. Unknown device 001c (rev 01)

For some people the wireless on this model works straight out of the box, for me it wasn't so easy. I did find a fix for it on another thread, which I will link here;

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

Sound:
My sound worked straight out of the box, the trick is, turning your surround sound volume up. That is the control for your front speakers. You can do this by double clicking the sound icon.
Open the "Edit" menu, and choose "Preferences". 
Check "Surround" and press the close button.
Unmute the Surround by clicking on the speaker icon below it, and turn it up.

/***** Edit: Thanks to kodiakcb for the following: *****/

The sound, as stated above, works by using the surround mixer. I like to use the volume controls provided on the keyboard which seemed to only control the main volume which didn't work. I have found a solution to this:

Simply add this line -

options snd-hda-intel model=acer probe_mask=1

to file:
/etc/modprobe.d/alsa-base

reboot and your keyboard volume controls will control the speaker volume.

Resolution:
My specifications tell me that my resolution can be bigger then 1024x768, and so does my common sense. The only fix I was able to find for this is, to install the package, 915resolution. 

In the command line type;

sudo apt-get install 915resolution

Once it is installed, perform a soft restart by, CTRL+ALT+BACKSPACE, you will now see your new 1280x800 widescreen resolution.

Bluetooth:
My model 5570z has the bluetooth button, but is not installed. Thanks to Acer for letting me know that. Since I don't have Bluetooth, I don't have a fix for it.

---

### Post by axylone on 2007-08-30
Thanks for compiling this information!
I also recently bought a 5570-2997.

A Hint to anyone who is getting errors when trying to install ndiswrapper for the Atheros card:  Remember to apt-get install build-essential.  If you don't you can't compile ndiswrapper (assuming you downloaded the source).

As for bluetooth - I was really confused when Windows didn't show any bluetooth cards, etc.  Good design by Acer for putting a bluetooth symbol on the laptop and not explicity listing the technical specs of the exact model in the manual.

---

### Post by raycosm on 2007-08-30
Are the middle buttons scrolling for you? I'm using Kubuntu Feisty and only up and down work, and instead of scrolling, up is left click and down is right click. They worked under Fedora 7, although left and right worked as back/forward buttons.

---

### Post by mrfr0g on 2007-08-30
I had no idea what they were supposed to be used for, but mine act just like yours. I'll so some research on it and post back.

---

### Post by mrfr0g on 2007-08-30
Not sure about the left and right buttons, but this got my top and bottom buttons scrolling

[http://ubuntuforums.org/showthread.php?t=298765&highlight=Aspire+Four+way+buttons](http://ubuntuforums.org/showthread.php?t=298765&highlight=Aspire+Four+way+buttons)

---

### Post by kodiakcb on 2007-09-11
I was perplexed by the bluetooth thing also.  However, thanks to this design it is easy to add internal bluetooth.  I have found aftermarket BT modules for Acer on ebay.  I have ordered one for $29 and I will let you know how well it works. 

As for the wireless,  the above link worked perfectly.  If you would like to change the wireless adapter instead, it is installed in a Mini PCI Express slot (or mini PCI-E).  It would be simple to change.

The above link for the touchpad also worked great for me.  Now I can scroll with the touchpad.

:guitar:

Later
KC

---

### Post by mrfr0g on 2007-09-12
I hadnt considered installing an after market bluetooth device. Please definitely tell me how well it works for you. 

A note on a different topic, I downloaded and installed the beta 7.10. It seems they have made the screen resolution and touch pad buttons work right out of box, which is nice.

---

### Post by kodiakcb on 2007-09-13
The sound,as stated above, works by using the surround mixer.  I like to use the volume controls provided on the keyboard which seemed to only control the main volume which didn't work.  I have found a solution to this:

Simply add this line -

options snd-hda-intel model=acer probe_mask=1

to file:
/etc/modprobe.d/alsa-base

reboot and your keyboard volume controls will control the speaker volume.

Later,
KC:KS

---

### Post by Alfred_McGee on 2007-09-13
Yes, the above link will work beautifully to get the wifi card running in an Acer 5570z, and with a much more informative interface than in Windoze. Thanks for the pointers on turning up the sound!

---

### Post by mrfr0g on 2007-09-13
Nice tip for the keyboard sound, I've been looking for that for awhile. I hope you don't mind but I added that to the post.

---

### Post by kodiakcb on 2007-09-14
That's cool.  That's what I submitted it for.  FYI I hosed up my Feisty install trying to get DVD playback and the hotkeys working so I had to reinstall.  I decided to give Gutsy Gibbon a try.  Many things work OTB.  Resolution just needs to be changed and rebooted.  Volume control can be designated under Pref>Sounds.  Hotkeys work (email and browser and most FN keys).  Touchpad works including touch scrolling and the four way scroll button.  Acpi seems to work better.

It loaded a restricted driver for the wireless but I still couldn't get it to work.  So I installed ndiswrapper as before.

Before anyone decides to go this route, keep in mind that it is still in developement.  It can be a little flaky but then again so was Feisty.  If you do decide to install from disc, grab the alternative install.  The live install kept locking up on me.  I lost video half way through the alternative install but it continued anyway without a problem.

Good luck,
KC

---

### Post by kodiakcb on 2007-09-15
Good News! The bluetooth module works like a charm.  You just open the memory compartment, plug in the module, reassemble and boot up.   The switch and light work and Ubuntu (at least Gutsy) recognized it automatically. Search Ebay for item 180160042639.

Later,

KC:popcorn:

---

### Post by mattlezeay on 2007-09-19
I have gotten all of the things working from this forum except the sound adjustment with the keyboard. I have tried the sound edit but it still does not work. Is there a certain place in the file I need to put the line?

---

### Post by Denikin on 2007-09-24
How about the Acer Orbicam webcam that comes installed in the notebook? Have people managed to get that one working?

I tried the gspca module driver, but that didn't work. Not sure if it's because I don't have the right model webcam, (I don't, mine is a 09b-something, instead of a 0896) but, the module won't load. I type the command to load the module and it doesn't do anyting at all.

So, I'm wondering if anyone else knows of a different way to get it to work, or if anyone's gotten the specific model I have to work.

Thanks.

---

### Post by Alfred_McGee on 2007-09-25
The posting explaining how to turn on the speakers at the start of this thread is good, but now my headphone jack seems not to work. My headphones crackle if I plug them into the mic jack, or the other jack next to it, but if I plug them into the headphone jack, there is no sound at all, and sound keeps coming out of the speakers. The Acer 5570z has very wimpy speakers, so it would be nice to have this feature working!

EDIT: Solved problem by upgrading to Hardy

---

### Post by mrfr0g on 2007-09-27
That's strange. My headphone speakers didnt react that way at all.

I am currently using 7.10, and I find that the more updates that come out for it, the better that I like it, and the more that it supports this laptop.

As I am not a Linux expert by any means, my suggestion is to upgrade.

---

### Post by urangela on 2007-11-30
Sorry for drifting off topic, but I have never seen so many others in one place, who like me are running Ubuntu on an acer 5570z. I was hoping someone might have gotten jack to work ( and play nice with alsa), without hanging constantly. I have been trying unsuccessfuly, to get Ubuntustudio and it's attendant software to run properly. I guess I was really hoping that some other 5570z users might be trying to do the same thing/ have made more progress than me.

---

### Post by nimbus2000 on 2007-12-01
Hi everyone
Just joined the ubuntu users community and started with gutsy gibbon. Have an Acer 5570Z and there are quite a few threads dealing with installation issues on this particular machine. Have been able to sort out quite a few issues from posts here thanks to you guys. Only the wireless remains. Following the posts here i have installed NDIswrapper and the windows driver for the AR5007EG controller. My machine recognises my wireless network. It even conects to the network through WEP (The graph on the top right hand corner shows the strength of the signal. Thats about it. Firefox simply refuses to connect. Pinging doesnt work and to top it all if i use roaming mode it prompts me for the passkey every 3 minutes or so. can someone help please.
bye

---

### Post by nimbus2000 on 2007-12-02
hurray its working.
after a lot of reading i uninstalled network manager and installed WICD instead. wonderful. it connects.

---

### Post by Alfred_McGee on 2007-12-20
Though I'd hate to have my fellow 5570z users think I am passé, I looked into activating my dialup modem. According to scanModem, it has chipset      0x11c11040     which is NOT supported under Linux at the moment.

---

### Post by HughR on 2008-01-05
I just stumbled on this thread.  I wish I'd seen it earlier.

Have a look at this page that I created last year: [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5570-2792](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5570-2792)

It would be great if folks added information to it.

---

### Post by braddcadd on 2008-01-10
Well, My sound was really low.  It worked fine with headphones but the speakers could definitely be louder.  So I followed two different links:

[http://ubuntuforums.org/showthread.php?t=362980](http://ubuntuforums.org/showthread.php?t=362980)
[http://www.burghardt.pl/2007/11/debian-gnulinux-on-acer-aspire-5102wlmi/](http://www.burghardt.pl/2007/11/debian-gnulinux-on-acer-aspire-5102wlmi/)

And now it is louder but there is a crackling sound over everything I play.  At this point, I'd be happy to have it the way it was.  Any ideas how to remove the crackle?

I have an Acer5570z
HDA Intel (HDA mizer)
RealTec ALC883

dmesg says:
[   17.128000] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...


Thanks for any help,
Brad

---

### Post by braddcadd on 2008-01-12
Fixed it with this link:
[https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360](https://help.ubuntu.com/community/SoundTroubleshooting#head-d8ad2bdeea082f749845b766aa82831110042360)

---

