---
title: "Compatibility issues?  Anyone tell me?"
date: 2009-01-09
forum: Hardware
---

### Post by dBuster on 2009-01-09
I have had my old gateway laptop on its last leg and I went and bought a new Compaq CQ60 laptop, really nice although I can not get Ubuntu to boot the live cd and get me to a desktop!  Okay, I can get the 8.10 32 bit version but it is slow and choppy.  I would rather run the 64bit 8.04.x version!  

The following are the specs on the laptop, if anyone sees anything that might prevent me from being able to boot please let me know.  When I boot the 8.04.1 cd it gets the progress bar to the third block and then stops with the capslock light blinking at me and does not go any further...

The Specs:
```
Product Name            CQ60-215DX
Product Number 	        NB276UA#ABA
Microprocessor 	        2.00 GHz AMD Athlon X2 QL-62 Dual-Core Processor
Microprocessor Cache 	1MB L2 Cache
Memory 	                2048MB
Memory Max 	        4096MB
Video Graphics 	        NVIDIA GeForce 8200M
Video Memory 	        Up to 895MB
Hard Drive 	        250GB (5400RPM)
Multimedia Drive 	SuperMulti 8X DVD±R/RW with Double Layer Support
Display  	        15.6" Diagonal High Definition HP BrightView Display (1366x768)
Fax/Modem 	        High speed 56k modem
Network Card 	        Integrated 10/100 Ethernet LAN
Wireless Connectivity 	802.11b/g WLAN
Sound 	                Altec Lansing speakers
Keyboard 	        101-key compatible
Pointing Device 	Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad
```

Processor specs:
```
Processor       AMD Athlon™ X2 Dual-Core Processors for Notebooks
Model 	                QL-62
OPN Tray 	        AMQL62DAM22GG
OPN PIB 	        N/A
Operating Mode 32 Bit 	Yes
Operating Mode 64 Bit 	Yes
Frequency (MHz) 	2000
System Bus Speed (MHz) 	3600
Wattage          	25 W
L2 Cache Size 	        1000
Process Technology 	65nm SOI
Package/Infrastructure Socket 	S1
```

From what I can see there I do have a 64bit system so what is the issue?  What am I missing?  I have tried the safe graphics mode and same results occur...

Thanks in advance.

Booted using the [ctrl][alt][F1] to see verbose the boot and the following occured:

```
[  113.978568]
[  113.978569] HARDWARE ERROR
[  113.978570] CPU 0: Machine check exception:  4 Bank  4: b600000000070f0f
[  113.978825] TSC 35134dc47c  ADDR 900000c2004001
[  113.978076] This is not a software problem!
[  113.979042] Run through mcelog --ascii to decode and contact your hardware vendor
[  113.979130] Kernel panic - not syncing: Machine check
```

---

### Post by swornbrother on 2009-01-15
I'm having a duplicate problem with the same model, Compaq Presario CQ60-215DX.  It hangs on the third block of the progress bar during the Intrepid 64-bit livecd boot.

Ubuntu Studio Intrepid 64-bit will install, because it's text-based, but when I went to boot into the OS after installing, it hangs at the same spot.

Also, I tried the Jaunty Alpha 2 release, and it fixes this problem, but it's slow and choppy.

Tomorrow, I'll be trying Intrepid 32-bit, and we'll go from there.  If it works I'm sure going to miss my ext4 filesystem on jaunty :(

---

### Post by swornbrother on 2009-01-16
Ok, I think I've figured out why it's slow and choppy under 32-bit.  You need to latest NVIDIA driver.

I went to NVIDIA.com, downloaded the latest .run file from their linux download page, hit alt-ctl-f1, became root, ran "killall gdm" to stop the Xserver, ran "su sh NVIDIA-Linux-x86-180.22.pkg1.run" then ran "sudo gdm" (to restart the Xserver).  It ran perfectly, and now it's snappy.

I haven't tried it on Intrepid 32-bit yet, but I suspect it will work, since Linux Mint is built off of Intrepid.

Now I just need to get the wireless going :(

---

### Post by dBuster on 2009-01-17
> **swornbrother said:**
> I'm having a duplicate problem with the same model, Compaq Presario CQ60-215DX.  It hangs on the third block of the progress bar during the Intrepid 64-bit livecd boot.

Ubuntu Studio Intrepid 64-bit will install, because it's text-based, but when I went to boot into the OS after installing, it hangs at the same spot.

Also, I tried the Jaunty Alpha 2 release, and it fixes this problem, but it's slow and choppy.

Tomorrow, I'll be trying Intrepid 32-bit, and we'll go from there.  If it works I'm sure going to miss my ext4 filesystem on jaunty :(

Was the Jaunty you tried the 64bit or 32bit?  I am downloading now the 64bit Alpha3 and will give that a shot. 

Had to reload the whole laptop to factory settings since windows hosed the mbr with resizing the partition...  Yeah go figure, now you know why you want Ubuntu vs vista...  

I just wish it wasn't this difficult but in the end the rewards sure outweigh the troubles!!!

As far as the wireless goes, did you try the latest madwifi drivers?  I have seen many notes that they work.  Just a thought...  I do not remember if I got the wireless working with the livecd of 9.04 alpha2 or not but I could swear I did.  Without to many problems either...  hmmm wish I could remember with all the other problems I have been having.

---

### Post by swornbrother on 2009-01-17
Jaunty Alpha 3 64-bit worked for me, except I couldn't use the latest Nvidia drivers (as they're not yet supported under Xorg1.6.)

It runs somewhat stably on Intrepid 32-bit, however I'm having problems with Compiz/Nvidia, after installing the latest Nvidia drivers (maybe it's because I install them from source, then reinstalled them as .debs?)

As for wireless, at this point I'm at a loss.  Ubuntu recognizes them as Atheros, even though it's supposed to be a Broadcom chip.  I haven't yet tried the latest Madwifis, but will give them a shot.

Ndiswrapper wouldn't work because they don't offer XP wireless drivers, ugh..

This computer would be perfect if it would just work!

Please let me know if you find a solution for wireless or choppy Nvidia stuff.

Cheers,
Chris

---

### Post by swornbrother on 2009-01-17
MADWIFI WORKS!

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

That tutorial saved my many, many headaches.

Now, I just need to figure out what's wrong with my Compiz/Nvidia..

---

### Post by dBuster on 2009-01-18
> **swornbrother said:**
> MADWIFI WORKS!

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

That tutorial saved my many, many headaches.

Now, I just need to figure out what's wrong with my Compiz/Nvidia..

So was it the first page of the tutorial that worked for you or was there some other info needed as well?  I am going to print or save the particular page for the madwifi before I try and install.

Hey, speaking of install, when you booted the alpha3 did you have to run any special extra commands or just normally?

Also, were there any issues encountered what so ever?

---

### Post by dBuster on 2009-01-18
So I have installed and got the wifi working without any problems then I tried to install the nvidia display drivers and thats when things went sour.

I had to stop the x server in order to install the drivers and now I can not get back into the x server!  I get the terminal only.

What could be done to get it fired back up?  How do you roll back the nvidia drivers?

---

### Post by swornbrother on 2009-01-18
The latest Nvidia drivers are NOT compatible with Xorg1.6 on Jaunty, but I hear there's a temporary workaround until the drivers catch up.  It involves modifying your Xorg.conf file:

> 
Section "ServerFlags"
     Option   "IgnoreABI"     "True"
EndSection


Check [http://ubuntuforums.org/showthread.php?t=1026512](http://ubuntuforums.org/showthread.php?t=1026512) for more information on that.

The Nvidia binary driver comes with an Uninstall function:

> 
sudo sh NVIDIA-Linux-x86_64-180.22-pkg2.run --uninstall


I'm to take a jab at Jaunty 64-bit again today, and will repost any new findings...

---

### Post by swornbrother on 2009-01-18
Jaunty Alpha 3 64-bit with Nvidia 180 drivers works!  I used the

> 
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection 


xorg.conf workaround and it worked flawlessly.  Compiz even works, with graphics settings maxed out.

It looks like I'll be using this as my "stable" installation, even though it's alpha.  I think I'll just not update it until Jaunty is stable.

---

### Post by swornbrother on 2009-01-18
Ok, I can confirm wireless works "out of the box" under Jaunty 64-bit, the only thing I had to do was go into Hardware Drivers, DEactivate support for Atheros chipsets, and restart.

---

### Post by dBuster on 2009-01-18
> **swornbrother said:**
> Jaunty Alpha 3 64-bit with Nvidia 180 drivers works!  I used the



xorg.conf workaround and it worked flawlessly.  Compiz even works, with graphics settings maxed out.

It looks like I'll be using this as my "stable" installation, even though it's alpha.  I think I'll just not update it until Jaunty is stable.

This is so AWESOME!!!  I have true speed video as well as the correct resolution!!!

The next item to tackle before trying to get java and flash going will be to get the bluetooth working correctly and have my MS mouse 5000 to work...  It sees it but it will not connect it.  

Plus the little thing of the wireless showing it on at the little button and not glow orange like it is...  Where is the blue....

---

### Post by dBuster on 2009-01-18
> **dBuster said:**
> This is so AWESOME!!!  I have true speed video as well as the correct resolution!!!

The next item to tackle before trying to get java and flash going will be to get the bluetooth working correctly and have my MS mouse 5000 to work...  It sees it but it will not connect it.  

Plus the little thing of the wireless showing it on at the little button and not glow orange like it is...  Where is the blue....

Okay I can pair the mouse and the bluetooth however the mouse does not function...  hmmm I see also there is a bug report with Intrepid about the bluetooth not working... argh!!!  I suppose it carried over to Jaunty as well.

---

### Post by swornbrother on 2009-01-18
dBuster, not sure about bluetooth.  I don't have any bluetooth devices yet.

The fn keys are not allowing me to change the brightness setting, though they do work for all other fn functions.

Perhaps it has something to do with the Nvidia workaround?

I also can't access the volume control interface.

ntfs-3g isn't allowing me to mount my Vista partition either..

Do you share any of these issues?

Also, If you're having any problems loading the wireless drivers on Windows, check this thread I started here:  [http://ubuntuforums.org/showthread.php?t=1042722](http://ubuntuforums.org/showthread.php?t=1042722)   It seems HP/Compaq listed the wrong drivers and specifications for this model on their support page.  It is mostly definitely an Atheros chipset that we're using, NOT Broadcom.

---

### Post by dBuster on 2009-01-19
> **swornbrother said:**
> dBuster, not sure about bluetooth.  I don't have any bluetooth devices yet.

The fn keys are not allowing me to change the brightness setting, though they do work for all other fn functions.

Perhaps it has something to do with the Nvidia workaround?

I also can't access the volume control interface.

ntfs-3g isn't allowing me to mount my Vista partition either..

Do you share any of these issues?

Also, If you're having any problems loading the wireless drivers on Windows, check this thread I started here:  [http://ubuntuforums.org/showthread.php?t=1042722](http://ubuntuforums.org/showthread.php?t=1042722)   It seems HP/Compaq listed the wrong drivers and specifications for this model on their support page.  It is mostly definitely an Atheros chipset that we're using, NOT Broadcom.

I do not have any brightness issues at the moment and the next time I boot into it I will check that out but if I were a gambling man I would say definitely from the work around.

I noticed also how I couldn't see the vista partition either.  thought nothing of it at first.  You sure that the ntfs-3g installed?  I know things like the screenlets did not.   

The only thing I can confirm is that the fn key to control the volume is working for me!  Have you gotten the wireless button to glow blue or is yours still orange??

---

### Post by swornbrother on 2009-01-22
Ok, I managed to find a temporary fix for the ntfs-3g issue in this thread:

[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443)

Today, I just booted in and my wireless wouldn't start up!  There was a crash report from Jockey, and I tried rebooting--still didn't fix it.  So I went into Hardware Drivers, ENABLED support for Atheros drivers, and it worked.  This seems to be a fix of some sort, if this happens to you, but I wouldn't try it unless your wireless won't start, because it might break it.

Also, if you're having problems with mounting shared folders over the network under nautilus, try smb4k, it worked for me.

---

### Post by dBuster on 2009-01-24
Well things are progressing.  I did lose my touchpad earlier but I got it back now.  Still trying to get the bluetooth to work.  I can see the mouse but I can not get it to pair up.  Tried even adding the mac address into the settings and it still will not pair.

I think I am going to look at the work around for 8.10 and see if that will work with 9.04...  At least I am hoping there is a work around.

As far as the fN key and changing the sound and brightness I have had no problems. 

I do have to start firefox though from the terminal as I get an error about firefox already running and when I try to kill it the pid changes on me and does not kill the bugger.  Even went as far as removing and then reinstalling firefox and same result.  I do however have the latest flash and java working without any hitches which is something I could not get to work on the old laptop with 8.04!!!

---

### Post by dBuster on 2009-01-24
Bluetooth mouse is now working!!!

Had to run the following:

```
sudo apt-get install bluez-compat
```

and then once that was installed I ran
```

sudo hidd --search
```

It found the mouse and then it paired up!!!  I now have mouse!!

---

### Post by dBuster on 2009-01-26
> **swornbrother said:**
> Ok, I managed to find a temporary fix for the ntfs-3g issue in this thread:

[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443)

Today, I just booted in and my wireless wouldn't start up!  There was a crash report from Jockey, and I tried rebooting--still didn't fix it.  So I went into Hardware Drivers, ENABLED support for Atheros drivers, and it worked.  This seems to be a fix of some sort, if this happens to you, but I wouldn't try it unless your wireless won't start, because it might break it.

Also, if you're having problems with mounting shared folders over the network under nautilus, try smb4k, it worked for me.

Thanks for the NTFS fix!  Worked like a charm!  Reading my Vista partition like a champ now!!!  Wahoo!!!

Any other issues we may have experienced we should put together here as a guide to the many who it seems are buying the CQ60-xxx and having issues!  What do you think?  Put together the best or leave it as is?  

Any ideas on the wifi button issue of it not changing to blue like vista does when the wifi is on?  since it is working as I am online now.  ;)

---

### Post by swornbrother on 2009-01-26
Sounds like a stellar idea.  I do hope this thread has helped some people out, but a guide would be even better.

As for that pesky wireless button, I've been trying for a couple days to figure it out, and still haven't a clue.  

Upon finding this article,

[http://madwifi-project.org/wiki/UserDocs/EnableLEDs](http://madwifi-project.org/wiki/UserDocs/EnableLEDs)

I thought all my problems would be solved, but following the instructions didn't lead me anywhere.  These are the commands they provided:

> sysctl -w dev.wifi0.ledpin=1
sysctl -w dev.wifi0.softled=1


but these LEDs they're referencing don't seem to exist.  Maybe there is something I'm missing..?

It's really important to get this going, not only does it extend our battery life, but turning off the wireless is the only way I can get JACK to run smoothly without XRUNS, as far as I know.

Any thoughts on this?

---

### Post by dBuster on 2009-01-27
> **swornbrother said:**
> Sounds like a stellar idea.  I do hope this thread has helped some people out, but a guide would be even better.

As for that pesky wireless button, I've been trying for a couple days to figure it out, and still haven't a clue.  

Upon finding this article,

[http://madwifi-project.org/wiki/UserDocs/EnableLEDs](http://madwifi-project.org/wiki/UserDocs/EnableLEDs)

I thought all my problems would be solved, but following the instructions didn't lead me anywhere.  These are the commands they provided:



but these LEDs they're referencing don't seem to exist.  Maybe there is something I'm missing..?

It's really important to get this going, not only does it extend our battery life, but turning off the wireless is the only way I can get JACK to run smoothly without XRUNS, as far as I know.

Any thoughts on this?


When you say JACK to run are you referring to any application?  I have yet to turn my wifi off and have no issues with any applications and errors.  

I even have the latest 64bit versions of flash and java running smoothly!  The only issue I have with java though is a common and not just this laptop, the sound disappearing and I have tried everything I could find in the forums.

I will have to dig deeper on the wifi issue.  Battery life is important!!!  I think I can turn it off software wise though.  hmm wonder if I did that and then turned it back on if the LED would change then.  Interesting  I never tried that yet.  Will have to when I get a chance again tomorrow.

---

### Post by dBuster on 2009-01-28
ARGH!!!  Morning updates today some 80 plus have now taken out my sound output device!!!  Ubuntu sees the sound card when I do a lspci -l however it will not function with the device.

I do know that the morning update updated pulseaudio and many others and when it was finished it asked to restart and I did but it continued to ask that until I actually went to the shutdown/restart and not just click on the update manager restart icon.  

ARGH!!!  I should not have updated!!!  Everything else has been able to be worked out lets hope through a collective this one as well.

---

### Post by dBuster on 2009-02-13
Here is a new one...

Okay am I missing something?  When I hibernate the laptop the bluetooth upon waking up asks, as soon as I turn the mouse on, to authorize the connection.  When I reboot it doesn't do that.  Is there a configuration I may be missing???  Any ideas?

---

### Post by dBuster on 2009-02-14
Got some screen shots now of what is happening...

[IMG]http://ubuntuforums.org/picture.php?albumid=917&pictureid=3207[/IMG]

Then it prompts me for the following and notice I have always checkmarked and it doesn't work like it should...

[IMG]http://ubuntuforums.org/picture.php?albumid=917&pictureid=3208[/IMG]

---

### Post by swornbrother on 2009-02-14
I think I had a problem with Pulseaudio not working after an update, but updating again fixed it.

I can verify that it's fixed in the latest daily build of Jaunty (as of 2/14.)

Also, the blue LED still will not light up, but the wireless button does now work in that same build, maybe alpha 4 too.

As for the bluetooth issues, I wish I could help, but I'm lost on that...

---

### Post by dBuster on 2009-02-14
Not wanting to try and touch the wifi button...  But you say it works as it should with turning on and off the wifi?!  Great to know.  Just wish the light would reflect that it is on or off....

As far as the bluetooth goes, I submitted a bug report about it.  We shall see on that one.  

Also I asked if we could get the title of this posting changed to something along the lines of "Compaq CQ60 - Jaunty 64bit - Tips and Tricks"  So others that have the same laptop might see it before posting a new topic which we have covered in our trials and tribulations...

---

### Post by brandonmpace on 2009-04-10
Has anyone tried a clean install of the beta on this laptop? 
The CQ60-215DX
My fiancee's mom bought it for her for graduation and I need to know if 9.04 is going to work well on it. She gets it near the end of May, more than a month after release.

She really loves open source software, especially Linux. I don't want her to have to put up with vista at any point for any period of time and she doesn't want to either.
So what's the status?  Has anyone running Jaunty bothered to click System>Administration>Hardware Testing  and sent off a report to let the developers know that this hardware needs to be supported?

Thanks in advance :)
               -Brandon M. Pace

---

### Post by dBuster on 2009-04-10
> **brandonmpace said:**
> Has anyone tried a clean install of the beta on this laptop? 
The CQ60-215DX
My fiancee's mom bought it for her for graduation and I need to know if 9.04 is going to work well on it. She gets it near the end of May, more than a month after release.

She really loves open source software, especially Linux. I don't want her to have to put up with vista at any point for any period of time and she doesn't want to either.
So what's the status?  Has anyone running Jaunty bothered to click System>Administration>Hardware Testing  and sent off a report to let the developers know that this hardware needs to be supported?

Thanks in advance :)
               -Brandon M. Pace


Not sure if the Beta will install clean or not.  I do know that the Alpha 2 installed and there were some work around issues involved but right now the Beta is super super super stable and I am loving it!  So much better than the vista that came preloaded!!!  I am sure the beta will have updates to apply since there were lots of them since the beta release, but it appears that many of the issues that were encountered here in this thread have been resolved.

Hope that helps!

---

### Post by RabidWeezle on 2009-04-21
Tommorow I am picking up this laptop since bestbuy has it down to 430 dollars :D I downloaded last night the Jaunty AMD64 Release canidate and we'll see how it installs. I'll post back with how it does/doesn't work. Hopefully I will have better luck than I had on the Compaq I bought my wife last year. I'll most likely be doing an XP64/Ubuntu dual boot if jaunty works without too much hassle :D

edit: I also thought I would mention I downloaded the alternative install cd.

---

### Post by dBuster on 2009-04-23
As far as the dual boot goes, no problems encountered here.  I kept the Vista that came preloaded and then installed the early Alpha of Jaunty onto a 90gig partition.  

I rarely boot into Vista although when I do there are no issues going to or coming from Vista.  

Jaunty final should install without any issues and it should run quite well.  Might have an issue at first with the nVidia drivers and possibly the atheros wifi.  One thing to note, the wifi button next to the power button will not change to the customary blue as it does in windows when the Ubuntu wifi is working.  Frustrating yes, show stopping no.  Wish I could get the color to change so I know but none of the tricks I have searched for have worked...  If you find out please pm me or reply here and share it....

---

### Post by RabidWeezle on 2009-04-25
Good news! Did the dual boot thing using the alternate install cd of the stable release of Ubuntu Jaunty and it worked like a charm. Of course I had to:

```

//ctrl+alt+f1 [twice]
//(login)
sudo /etc/init.d/gdm stop (a couple times to make sure it was dead)
sudo apt-get update
sudo apt-get install build-essential links2
links2 www.nvidia.com
//(download the 64 bit driver latest release)
sudo sh <name of nvidia binary I download>
//(it will complain about not recognising the kernel and you just have it build it for your kernel - that's why you need build-essential - also have it automatically do your xorg.conf for you, it may say some error, but it actually works just fine, I also included the 32 bit libs when it asked for 32bit compatibility)
sudo reboot now

```
now when you bring ubuntu back up it should show that purdy nvidia splash screen.
Now DON'T select alternative mad wifi on the hardware list, the wifi just works out of the box :D along with sound. and all. Happy computing. Cheers to the jaunty team and this thread for helping me get it working

---

### Post by danloz on 2009-04-27
Same system picked up for a couple of bucks refurbed.  

Fresh install of the non X64 version (just keeping it simple, last time I did this with a different system) I had hella problems with X64.  Out of the box, everything (sound, wifi [atheros], keyboard, trackpad, etc.) works.  

Only issue:  Graphics card was chunking hard.  Everything came out choppy.  Scrolling through a web page was delayed and quite frustrating.  Resolution:  

-Via Add/Remove installed the NVIDIA X server thing and the 173 drivers
-Via the hardware manager, installed/activated the 180 drivers.  Problem resolved.    

Although, bad news is when I booted over to Vista, it did some sort of fix it which reduced my ubuntu partition to like 2 gigs.  I'm going to burn the current ubuntu partition, make some space again and reinstall.  I might even go over to the dark side and run Kubuntu cuz it looks sexy.

---

### Post by danloz on 2009-04-27
Actually, side note:  after I did the big update, I couldn't use the forums anymore.  Login button and reply button were seemingly non-functional in ffx.  Since I already knew I was going to toast the install, I didn't bother investigating it further.  Is there something quirky going on with that?  Or is it just a random issue?

---

