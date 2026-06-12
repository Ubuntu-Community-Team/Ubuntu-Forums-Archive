---
title: "HOWTO: Install Latest Ubuntu on HP AND Compaq Laptops with Drivers"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by EXCiD3 on 2007-10-07
[B]UPDATED:

[/B]The tutorial is finished!!! :guitar: Took a long time to read through all the information about Hardy running on HP and Compaq laptops but I finally finished my tutorial and you can view it here: [http://excid3.pcriot.com/wordpress/?page_id=28](http://excid3.pcriot.com/wordpress/?page_id=28)

Sorry to host it off the forums however due to the length of the post I found it was easier to host it on my personal blog and use javascript to hide the sections of the tutorial you arent viewing to make it much easier to use. Hope it helps!

---

### Post by amvella on 2007-10-16
Hey I am using ubuntu gutsy gibbon beta release. Everythig works for me except the realtek high definition audio. I tried to follow instructions on different threads but nothing helped. If you could find out a way to help me out.. That will be great. Thank You very much in advance

and by the way i am using a hp dv9500t laptop

---

### Post by aldeby on 2007-10-18
amvella, check out this wiki page: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

---

### Post by bfledderjohn on 2007-10-18
I've got an interesting problem after I upgraded to Gutsy..... I am running an HP Pavilion dv6000z and everything seems to work fine UNTIL you unplug the power source OR plug it in.... The backlight of the screen fades out and won't return!  I am dual booting, so I have to boot into Windows to get the backlight back!  When I get back into Gutsy, everything is fine (until I plug or unplug).... Anyone have a solution?  It must be something with power management and the video driver, but how do you fix that... Upon shutdown and startup it still won't come up (the HP splash comes up and then when Grub kicks in the lights go out)...

Thanks!
Bret

---

### Post by emburst on 2007-10-18
> **bfledderjohn said:**
> I've got an interesting problem after I upgraded to Gutsy..... I am running an HP Pavilion dv6000z and everything seems to work fine UNTIL you unplug the power source OR plug it in.... The backlight of the screen fades out and won't return!  I am dual booting, so I have to boot into Windows to get the backlight back!  When I get back into Gutsy, everything is fine (until I plug or unplug).... Anyone have a solution?  It must be something with power management and the video driver, but how do you fix that... Upon shutdown and startup it still won't come up (the HP splash comes up and then when Grub kicks in the lights go out)...

Thanks!
Bret

When you say "fade out" do you mean the screen dims or is it completely black?

---

### Post by bfledderjohn on 2007-10-18
It slowly goes to completely black (you can still vaguely see the outline of the images when you shine a light on it, so I know that the images are still there, just no backlight).

---

### Post by mock_turtle on 2007-10-19
i did what writes on the howto post for feisty, while using feisty ([http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)) but couldnt get my  0×0c45 : 0×62c0 Microdia cam work. so i had to postpone my hopes for the next release (gutsy). now i am using gutsy and did the same things written in the article and installed uvc thing. but it still doesnt work. everything seems o.k but  when it comes to testing in gstreamer-properties/video test i get an error
```
 "Failed to construct test pipeline for 'Video for Linux 2 (v4l2)' "
``` .and when trying to use ekiga i get ```
Error while opening video device USB 2.0 Camera

A moving logo will be transmitted during calls. Notice that you can always transmit a given image or the moving logo by choosing "Picture" as video plugin and "MovingLogo" or "StaticPicture" as device.

Your video driver doesn't support the requested video format.
```  i do not want to wait for the next release, so could someone please help with it?

*yes i did everything written in the article without skipping any step
** i am using hp pavilion 6000 and webcam is "Bus 002 Device 003: ID 0c45:62c0 Microdia"

---

### Post by xcafeus on 2007-10-19
HP Pavillion dv6520ea ...no sound, no fingerprint reader. Compiz asks for GLX when it shouldnt (Intel graphics). These are the major issues I got so far.. HP laptops are very popular and the new design and good built is making them even more - Ubuntu must take this into account.

---

### Post by DRAGONPOWER on 2007-10-19
OS: Ubuntu Gusty 64-bit (7.10)

Hardware: HP Pavilion dv9000(9500 series), dual-core EM64T, 2GB, nvidia 8 series.

Having major install problems with audio alsa stuff which i dont really get. I tries just about all the guides u could possibly find at ubuntuforums and online...still nothing to make audio work. 

Note the HP laptops have this menubar above the keyboard, like a button pad. The volume control is always amber/orange, which in windows would be Mute option. Now i cant get it blue even though i press the button the colour wont change to blue, and the volume stays muted, however doing so a ubuntu overlay appears showing volume control, the vol up and down work fine, but it is like in a muted state>? any fixes for audio ich8?

even tried the realtek linux software, compiling alsa, everything so far ... plz help!

AFAIK intel Centrino is stable in 64-bit, im just adding info as i go right, so u get a good picture... nvidia drivers installed with envy & no problems, fixed login as root user with full access ok...

---

### Post by DRAGONPOWER on 2007-10-19
> **aldeby said:**
> amvella, check out this wiki page: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

tries this a dozen times but still no sound ... :confused:

---

### Post by EXCiD3 on 2007-10-19
DRAGONPOWER, I am currently looking into a fix for this. I have heard both sides of this, for some installing alsa 1.0.15 works, for others it doesnt. If anyone has a solution for this please let me know!

**NOTE: **I will be updating the Howto in the next day or so! Please be patient, there are a lot of things to cover.

---

### Post by BoardDWorld on 2007-10-19
In regards to the built in webcam keep an eye out here:
[http://lsb.blogdns.net/ry5u870/](http://lsb.blogdns.net/ry5u870/)
and here:
[http://www.arakhne.org/spip.php?article50](http://www.arakhne.org/spip.php?article50)

The sound issue is odd, both Feisty and Gutsy have been completely problem free in this area on my DV9224TX.

Has anyone resolved the odd black flicker that happens to the screen every once in a while when compiz is running?

This is my small write-up on how my installation went:
[http://ubuntuforums.org/showthread.php?t=579818](http://ubuntuforums.org/showthread.php?t=579818)

---

### Post by old_salt on 2007-10-19
I helped EXCiD3 on his previous post and will be lending a hand wherever I can. See specs below on the system I'm running.
-----------------------------------------------------------------------------------------------
First off I encourage EVERYONE to ***_please_*** **be patient** while the other repositories come online with all the other goodies. Gutsy had to become an official release before volunteers could rework these apps under Gutsy. You can however install from source if you have an urgent need. If you need a stable system or a lot of extra items then stick with Feisty for another month or so. 
-----------------------------------------------------------------------------------------------
I'm encountering several minor quirks on the install myself. I will try and list a few and some initial workarounds that worked for me. 

BE ADVISED - I'm using Kubuntu 7.10 64bit

---- Installation - You MUST use the noapic option. I also HIGHLY recommend you have a hardwired connection to the Internet during install.(I'm not going to elaborate here.)
---- Immediately adjust your power savings (Battery Icon) by the clock. This should help those with initially dim screens. NOTE: Power options such as Suspend and Hibernate will not work on these machines without major tweaking and sacrifices. It's a kernel thing  and we aren't the only ones affected. Complain to the BIOS makers for providing PnP BIOS's catered to Winblows okay? I don't use these options but others do so ....
---- The restricted drivers for the video and wireless worked flawlessly for me. I have no issues and have better wireless performance than using ndiswrapper.
---- Dolphin, still getting used to it and not sure if I like it or not.
---- I removed App-Armor. Check your dmesg output. AppArmor initializes then shuts down but reserves resources. Until it's explained properly what the purpose of this is, I have no use for a resource hog.
---- Mplayer plugin for Firefox is not available yet so after the restricted drivers install; Xine is the default video plugin. Not a problem except Xine won't scale the window to the video size like Mplayer would so you get video playback scaled to the browser window size. Can you say pixelate?
---- Desktop Search applet - What a joke & resource hog. I removed this. Never had nor understood the need for a dedicated app to search for files I created and saved. 
---- Unlike some posts, I have no USB issues. I lack resources to test the Firewire port.
---- SD Media Reader works fine. 
----Remote Control works fine
---- Bluetooth appears to function properly however I don't have a device to test with. 

Issues:

---- Random Keyboard key repeats - Tweak your keyboard settings under "System Setting"  | Keyboard & Mouse" and set Delay/Rate to 710 &/ 20. Start here and adjust to your style.
---- Still missing "build-essential", "fakeroot" & "debhelper" from base install. Too important in my opinion to not include these. Use apt-get to install.
---- mkisofs is not available. It was rolled into cdrtools some time ago however some editing apps STILL call for mkisofs separately - such laziness!
---- UVC Ricoh webcam - Still an issue!!!  I can't get the drivers to compile properly and unsure when or if anything will be done about it. 
---- Lightscribe - WTF, Can't understand why someone at Canonical hasn't initiated a dialog with LaCie to get this feature working like the RPM based distros have. 
---- Like to never got kwallet to open to store the wireless settings. Once activated it's been working fine since.
---- Desktop - Get new Wallpaper. Love this feature but can't understand why the preview doesn't scale so you can see it? I guess the developer works on a 640x480 screen still. Same holds true for Superkaramba as well.

SOUND
While I have no issues here and all my buttons work on base install, sound to me is faint and lacks quality or some measure of Bass. Vista doesn't sound too much better either however it is noticeably better. I believe maybe this was an HP engineering screw-up as other laptops with lower quality audio features sound better - I expected more from Altec Lansing and HP on this considering this model is marketed as a multimedia desktop replacement. 

OVERALL/OPINION
Put the system under a load and it screams but starting apps after being idle and the system is a dog. I know this sounds weird but I can't explain it any better. Boot up seems quicker however Firefox and Evolution are painful to open and it's the same under Feisty. The system overall isn't as smooth as Feisty in my opinion. Maybe it's because Gutsy was planned or centered around KDE4? 

I won't be setting up Compiz/Beryl (whatever it's called now) until this version stabilizes. Too much is missing from the base install and you can't get the missing pieces just yet to fill in the gaps. We really need more testers and feedback during development stages.

I will wait till things stabilize before proceeding with VMware Server.  

-----------MY PERSONAL INPUT ONLY ---------- 
Personally I think the developers focus should not involve trying to reinvent the wheel with new marketing candy which creates new issues. Someone needs to explain to Marketing their true place & keep them out of development. I'm seeing more and more the U/E/Kubuntu platform moving away from hardware neutrality and becoming biased towards a specific hardware maker. I guess this is to be expected for a while. After 3 versions of Kubuntu now, I'm having more difficulty in getting the OS to run on the HP Platforms. The HP9000 series is a high end system and shouldn't have these issues unlike an ultra cheap (sub $500) no-name brand whatever. I know a lot of folks have submitted their HW configs to developers to assist their efforts. Unfortunately I think the efforts have gone to the bit bucket. Now more then ever the linux community & hardware makers need to come together and establish relationships to the benefit of all.

System:
I'm running the DV9000z AMD Turion64 x2 - 2.2Ghz, 2Gb RAM, 160Gb HD, Matsushita Lightscribe D/L DVD-RW, Bluetooth, nVidia 6500.

---

### Post by BoardDWorld on 2007-10-19
I have just contacted the arakhne.org web master to see if & when he will compile the new driver and opted for testing. Will report back if I have any news.

---

### Post by old_salt on 2007-10-19
Thanks BoardDWorld for your effort. 

INSTALL UPDATE:

If for some reason - whether it happened sliding the laptop in and out of the case or for whatever reason you boot up with the Bluetooth / Wireless switch in the off position; YOU MUST restart "X" or KDE using the "CTRL+ALT+BACKSPACE" method with the switch on in order to obtain an IP Address for your wireless. 

Looks like the concept of "Dynamic" anything is once again by the wayside. After much thought, I'm almost convinced that our hardware is really not even supported past the nVidia Video even though the entire system is nVidia chip based. I among many thought this was a sure thing when it came to Linux.

While it may seem that I post a lot of negative comments, to the contrary. I feel the pain with you with the quirks of the new system. I cutover to Linux cold-turkey 4 yr ago and never looked back. I slip sometimes in letting my emotions show through my posts when I encounter issues that are years old that were supposedly resolved only to find they haven't and it's the same old excuses. While Linux in general is making quantum leaps almost daily, I see too many items falling by the wayside as well. :(

On a positive note - for those who like having the numlock turned on at boot in KDE, I'm happy to say it actually works now. :guitar:

---

### Post by old_salt on 2007-10-19
**_[SIZE="2"]After talking with EXCiD3 - I've recommended we freeze this posting until further notice. [/SIZE]_**

We have spent days in dependency hell trying to get core components downloaded and installed to enable basic compile and build capability to no avail. The stuff just isn't there. With that, we are so VERY DISAPPOINTED with the 7.10 Gutsy release it isn't funny. 

Half of what's available in Feisty isn't available in Gutsy; You can't even obtain the necessary tools to even compile from source to achieve your goals. There's also way way too many hardware related issues that make this release unusable. 

As an I.T. Professional of 20 years with 4 years experience on Linux spanning 5 different distro's, I've never experienced such a disappointment and such frustration. I strongly advise everyone to revert or remain with Feisty. 

In efforts to send a message to the developers of Ubuntu, I would like to see everyone steer clear of and boycott Gutsy to send a message that they missed the boat terribly with this release. About the only plus was the wireless. Being as involved in this community as I have been, I'm absolutely appalled with this release. I can get basic connectivity, do email and browse the web but that's about it. What a joke.[SIZE="2"]**_ I can do more off a basic install of Vista than 2 days of frustration off Gutsy and that's the biggest insult I've ever seen of any Linux Distro._**[/SIZE]

PLEASE PLEASE be patient and stand by. This issue has got to be resolved ASAP!!!!

Tony

---

### Post by EXCiD3 on 2007-10-19
Regarding old_salt's post:
Gutsy is a disappointment. The only thing that is nice to see is the Broadcom driver support. Other than that Gutsy is just a mess. **I STRONGLY ENCOURAGE USE OF FEISTY.** Feisty supported HP/Compaq laptops quite well, with a few exceptions. Gutsy has taken a different route with hardware support and no longer works well with HP/Compaq laptops. **BEWARE when installing Gutsy on your HP laptop.** 

Nvidia graphics support does not work. I have spent hours attempting to configure my dual monitor configuration in Gutsy which took 5 mins to configure in Feisty. Bulletproof X has caused more hassle than it is worth. Any attempt to install the Nvidia graphics driver has worked successfully, but the Nvidia graphics driver is unusable with my setup. I am forced to resort the NV or Vesa drivers. As far as graphics support goes, Gutsy is terrible and should have improved in graphics support instead.

Attempting the installation of Alsa 1.0.15 fails because Gutsy does not provide the tools need to compile from source. Gutsy has taken a step back in usability and I would hate for anyone new to Ubuntu to think otherwise. **PLEASE DO NOT USE GUTSY IF YOU WANT FUNCTIONALITY.** Wait until Gutsy is more mature of an OS before upgrading.

This thread will be frozen until further updates to Gutsy have been made.

---

### Post by PharaohSD on 2007-10-19
I got a custom hp dv9000t and it works like a charm

using 7.10 AMD64

Get automatix2, and it was smooth sailign from then on. gfx/ everything is working*


well except awn-curves....untill that get's fixed

---

### Post by magicman5421 on 2007-10-20
I'm booting off of the live cd (waiting on my new hdd to arrive) and everything works fine. However, due to the scathing comments that 7.10 has been getting, should I switch my install to 7.0.4?
Hardware config:
HP dv9500
intel centrino duo 2ghz
nvidia 8800
2gb ram

Only problem i have been getting consistently is one that was already mentioned, about the wireless switch...Haven't tried much else though other than internet and openoffice...but looking on the bright side, my wireless card was supported out of the...box(cd)?

---

### Post by Kaerper on 2007-10-20
Hello i have a problem on my HP nx 6325 too, Gutsy freeze every time using the battery. If i use the power cable everything! works fine, no freeze nothing. Furthermore Gutsy erstimates the remaining Battery Time but in Feisty i got the accurate value....
I'm sticking with Feisty for now.

---

### Post by dansen926 on 2008-01-24
> **DRAGONPOWER said:**
> tries this a dozen times but still no sound ... :confused:

I've got a solution that you can try (this is also posted at [http://ubuntuforums.org/showthread.php?p=2134325&page=2):](http://ubuntuforums.org/showthread.php?p=2134325&page=2):)

Sound didn't work at first, but I found a workaround thanks to [l-fever]("http://ubuntuforums.org/member.php?u=324798"):
*Note: This involves installing ALSA drivers from source code*
> Basically go to [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") and follow the part where it says to download the latest version of alsa-driver, alsa-lib, and alsa-utils.

Go to [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3104") and download realtek10.tar.gz.
Extract to ../alsa-driver-1.0.14/alsa-kernel/pci/hda/

Follow the compile part of [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again. la

It should work at this point. It did for me anyways. Good luck!


Reboot

Edit /etc/modprobe.d/alsa-base and insert "options snd-hda-intel model=toshiba" at the end of the file.

Reboot again. la

It should work at this point. It did for me anyways. Good luck!

---

### Post by EXCiD3 on 2008-01-24
Just so everyone knows, the 8.04 release of Hardy Heron is coming up and I will be writing a NEW tutorial for HP/Compaq laptops in this thread. Until then we need testers to post their feedback on the alpha/beta releases of hardy. Please try it out and post your feedback here: [http://ubuntuforums.org/showthread.php?t=660384](http://ubuntuforums.org/showthread.php?t=660384)

---

### Post by crosswalker21 on 2008-02-13
I've got Gutsy set up on a Compaq Presario 2200 laptop.  Most everything works fine with a few notable exceptions:

[LIST=1]
[*]Wifi likes to drop my internet connection sporadically, though not very often.  I haven't yet figured out if this is my router, or the driver. (Broadcom bcm43xx)
[*]When playing a DVD, I can hear sound, and, if I click around, use the menus, but there's no picture, no video, nada.
[*]Suspend always results in a forced restart when I try to wake the machine up.
[*]I can't use the vga out as a separate monitor (it's always a display clone, if anything)(Intel 82852/855GM Integrated Graphics)
[*]Audio seems a little prone to peaking out
[/LIST]

This is the first time I've been able to make a distro work for more than a couple of days on my laptop.  Claps for Gutsy =D>

---

### Post by o.besner on 2008-02-14
Hey fellow HP users,

I have an HP DV9417ca Laptop ( part of the DV9000 family, sold in Canada) with :
- Turion TL-56
- Nvidia Go 6150
- Webcam/Microphone
- Broadcom 4321 a/b/g/draft-n  Wireless
- Tv-Out
- a 17 inch 1440x900 screen 
- HP F4180 Printer/Scanner

This should look familiar to alot of Hp users out there. It was a popular deal in Canada, and something equivalent must have been sold in the US/EU. After a couple of days of work, I managed to make EVERYTHING work on Gutsy AMD64.

Live Cd froze. Had to use the -noapic boot parameter (with F6)

What worked after the -noapic:
- Soundcard
- Screen resolution
- nVidia 6150 (with the restricted drivers) (Compiz also worked flawlessly)
- the buttons above the keyboard (blue LED buttons)

And... that's all. Almost reinstalled Vista at that point. Almost. Ubuntu was barely working. 

What was easy to get working:
- The Webcam/Microphone, using this tutorial : [http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393)
- Printing capabilites of the F4180 (Just go in Administration --> Printing. You first have to install HPLIP found in Add/remove software)

What was hard to get working :
- The Wireless card. Very Intense. You CANT USE HP's DRIVER ! It won't work. My roomate has a similar card, similar problem. He taught me the trick : use Dell's driver. Someone did a quick and dirty tutorial to get it working :
 [http://ubuntuforums.org/showthread.php?p=3625678#post3625678](http://ubuntuforums.org/showthread.php?p=3625678#post3625678)

Don't even think about using the bcm43xx tool. I tried so hard and for so long to use it and... yeah. Only works for the 4306, and barely !
Once properly installed, the card will work flawlessly. I can even Hibernate/Suspend !

Next... the Tv-Out.
You have to write it all yourself in your xorg.conf . It's complicated and dangerous. 
There's no good guide for this. I've attached my xorg.conf to this post... Read it, understand it, and then copy it. Replace my fields with your actual values. There is no other way to get it working that I've found. But first, make a backup version of yours. And Triple-check your new xorg.conf before saving anything.  Its location is : /etc/X11/xorg.conf

- The scanning capabilities of the F4180 can only be used if you have the latest HPLIP from the website (hplip.sourceforge.net). To get it working on an AMD-64, you have to manually install every package they say are missing. Read the package description, find the equivalent, then install it (using the synaptic package manager). But even when you're done doing this, it won't work. Because they forgot to mention the most important one : Python-dev for your python version. If you forgot to install the dev version, the installer will fail for unkown reasons halfway through. Also, when running the HPLIP self-extracting/self-installing archive, START IT IN SUDO, even if they say you shouldn't do it. Once your done, the scanner will work with GIMP.

If, like me, you need Skype to communicate with your girlfriend/family/coworkers/hot chick you just met/classmate , follow this guide to get version 2.0 working :
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

I think it's some kind of shady trick... but eh, it works.

To install Google Earth I used Automatix2. Now some people on ubuntuforums.org will tell you that Automatix is the work of the Devil himself. They might be right.I'm a pharmacy student, not a computer technician. But it's, by far, the easiest way to get it working, and I really doubt Google Earth will have any dramatic effects on your installation.

I still have some problems with my usb ports. Sometimes my hard drive will unmount by itself, stuff like that. I heard it's because of the -noapic flag. Maybe using pci=routeirq instead will work better. I'm working on a solution, and if I find anything I'll post it here.

Good luck ! Once done, your laptop will be faster, more stable, and unique than Vista. Everything I posted is for a X64 installation. I heard it's easier if you have a 32-bit install... but I can't say for sure. if you have any questions or if I can help you in any way : o dot besner at gmail dot com.

If anybody knows how to flash the BIOS without having a Windows partition, please let me know. I'd like to give it a try. I've tried with WINE, but it didn't work.

Last thing : here's the link to get Flash working on a 64-bit install. It's a well-documented bug.
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by o.besner on 2008-02-14
As previously documented, the use of noapic irqpoll noirqdebug removes any USB problem.

pci=routeirq has no effect.

---

### Post by EamonR on 2008-02-18
Hi there,

I have a HP Compaq 6715b with Gutsy installed.

The laptop has integrated --EDIT--BLUETOOTH, (I checked, it says so on the site, it shows in the bios, i think it worked on the vista the laptop came with, and it is physically there as I opened the panel on the laptop to make sure since I saw a screenshot of someone finding theirs was actually missing.)

However, I don't think I can find it in the hardware information, and when the bluetooth preferences app is set to display only when adapter is present, it disappears so it thinks the device is not present.

That command (hciconfig dev?) or something similar (can't quite remember what it is, you know the one), shows only "Devices:" and nothing else.

There is no switch I can find anywhere on the laptop to enable bluetooth like there is for the wireless unless I'm totally blind :P

Does anyone have any ideas?


Thanks :)

---

### Post by orduek on 2008-02-18
I have HP500 with mint 4.0 installed (and gutsy on a dual boot).
with Mobile 915GM/GMS/910GML graphic controller.
and 1g RAM.
every now and then then the computer freezes, the skype hangs up my calls etc.
I have a feeling its something to do with my intel graphic driver.
any suggestions?

---

### Post by o.besner on 2008-02-18
EamonR,

of what I could find on the net, "Compaq 6715b" doesn't mean much, since there are many laptops built with this name and having differents parts. To know exactly what you have (in terms of parts), I need the "RMxxxxx" (I have no idea what it is or where to find it. I found this on hp.com . Does it ring a bell ?)

Did you try lspci to know the name of your card ? If it doesn't show up, you'll first have to find out what's your hardware :D because guessing isn't a good idea !

Most Compaq 6715b seems to have the broadcom 4321. In my previous post I've already explained how I configured mine. The trick is to use Dell's driver !

---

### Post by EamonR on 2008-02-19
wow I'm an idiot, i wrote "integrated wireless"  but I actually meant Bluetooth! Sorry! Must have been really tired!

Its the bluetooth that doesnt work :/

---

### Post by crosswalker21 on 2008-02-20
Compaq Presario 2200 with integrated intel graphics:
I finally got secondary monitor support to work by switching drivers in the **Screens and Graphics** manager.
There's still a problem with it though.  Now the logical screen is always bigger than the physical screen (ie. when I move my mouse to the edge of monitor 2, the screen scrolls over that way.  Anyone have any suggestions?

---

### Post by o.besner on 2008-02-20
Well you can always set the proper resolution directly in your xorg.conf file.

sudo gedit /etc/X11/xorg.conf 

Just find your monitor in section "screen" and set the right resolution, both for your laptop screen and tv-out

---

### Post by rocky909 on 2008-02-23
I read ur reading dude...can u pls check my thread for installing 7.10 in my hp dv 6736nr..I cant find soln for this ..
thank u very much in advance

---

### Post by rocky909 on 2008-02-23
here is where i am stucked...
[ATTACH]60563[/ATTACH]

[ATTACH]60564[/ATTACH]

[ATTACH]60565[/ATTACH]

these all photos are in the same window..I gave close view for upper & lower window for ur better watch(pls click to see larger view) I also tried by pressing F6 and ran these command after -- sign

noacpi

as it didnt work then I tried wt this

noacpi nolacpi

then I tried with

noacpi nolacpi noirqpoll nosmp

For ur information, my system is amd turion TL-60,nvidia 7150m,
its hp dv 6736nr.
thank you very much in advancve

---

### Post by Ayuthia on 2008-02-23
> **rocky909 said:**
> here is where i am stucked...
[ATTACH]60563[/ATTACH]

[ATTACH]60564[/ATTACH]

[ATTACH]60565[/ATTACH]

these all photos are in the same window..I gave close view for upper & lower window for ur better watch(pls click to see larger view) I also tried by pressing F6 and ran these command after -- sign

noacpi

as it didnt work then I tried wt this

noacpi nolacpi

then I tried with

noacpi nolacpi noirqpoll nosmp

For ur information, my system is amd turion TL-60,nvidia 7150m,
its hp dv 6736nr.
thank you very much in advancve

You might try using noapic nolapic instead of noacpi nolacpi.  That might help.

Also, do you know if you are using the server edition instead of the desktop edition?  If you are not sure, you can try typing startx and see if any GUI or error messages come up.

---

### Post by CarolinaGirl on 2008-04-06
Pavilion zd8000
Intel P4 - 3.4GHz
2GB Mem
ATI Radeon x600 video
Broadcom 802.1b/g (4318Rev02 maybe?)
Realtec RTL8139/810x Family Fast Ethernet
Who knows who's 1394 Net adapterHP Integrated Bluetooth (PID011d Rev 0017


Doesn't ANYONE have a zd8000 series Hp Pavilion? I get errors about Region 6, 7 and 8 at boot and a password reguest once it gets up. What's up with that?

---

### Post by EXCiD3 on 2008-04-06
> **CarolinaGirl said:**
> Pavilion zd8000
Intel P4 - 3.4GHz
2GB Mem
ATI Radeon x600 video
Broadcom 802.1b/g (4318Rev02 maybe?)
Realtec RTL8139/810x Family Fast Ethernet
Who knows who's 1394 Net adapterHP Integrated Bluetooth (PID011d Rev 0017


Doesn't ANYONE have a zd8000 series Hp Pavilion? I get errors about Region 6, 7 and 8 at boot and a password reguest once it gets up. What's up with that?

Might be of some help: [http://www.iomonkey.com/linux/hp_zd8000/](http://www.iomonkey.com/linux/hp_zd8000/)

---

### Post by CarolinaGirl on 2008-04-06
Wonderful link, and I'm sure I'll find a lot of useful information I can use after I can get the darned thing past the errors. I'm new to linux, so I'm not sure if I need to modify some of the files before I burn the CD, or what. And I STILL don't know what's up with the UserName/PassWord request when I boot from the CD.
Maybe it's just not meant to be...:confused:

---

### Post by EXCiD3 on 2008-04-06
Can you take a picture of the problems and upload it for us to take a look at? I'm not exactly sure what you mean lol

---

### Post by CarolinaGirl on 2008-04-06
You mean like a photograph of the screen? The boot errors flash by so quickly that I can't really read them. Like I said before, they are something about Regions. There are also all kinds of errors that flash by after the first few [OK]'s. Then it comes up to the first Ubuntu load screen. Regardless of whether I select load or load in safe mode, it DOES load, almost cleanly, but it first goes to something about going to the site GTK.org/setuid and something about session less than 10 seconds, then it cycles to the Login screen where it asking me for a Username and Password, which is can't seem to figure out. After a few tries, it goes back to the message about session less than 10 seconds and it all starts again. Things are working because if I go to the "options" thingy and do a restart or shutdown, they both work.

Is there a way to "pause" the load, or maybe turn on a log file when booting from the CD, so I can see/read/copy/photograph the messages?

---

### Post by EXCiD3 on 2008-04-06
Which version of Ubuntu are you using? have you tried Hardy Beta?

---

### Post by CarolinaGirl on 2008-04-06
No, I was trying Goofy Gopher or what ever 7.10 is called. I just finished getting 6.06 and I tried to get Kubuntu 8.04, but MSFT's burned didn't like it. I'll pull that down and let you know how it goes. I tried booting it again and the Region errors are "Bridge" related with some hex at the end. Like I said, they flash by quickly, so it IS a challenge.

---

### Post by rahul_rocks on 2008-04-07
Hi Friends,

I am having HP Pavilion dv 2519 i have installed **[B]Ubuntu 7.10**[/B] on my machine
My graphic card is:
**Mobile GM965/GL960 Integrated Graphics Controller**


By mistake i have changed the graphic card driver. Now my machine is accepting only default vesa drivers. So i am not able to run compiz and all other visual effects in terminal compiz shows result:-

Checking for Xgl: not present.
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present.
Checking for FBConfig: Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
Xlib: extension "GLX" missing on display ":0.0".
not present.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present.
Starting emerald
Xlib: extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Kindly help me to reload the Intel Drivers and run compiz
thanks

---

### Post by manas.pat27 on 2008-04-11
Please Tell the procedure to log on to wireless internet.....
Computer - Compaq F500 Laptop.

I am an absolute beginner...

Donno anything about how to install............... PLS HELP !!!!

---

### Post by o.besner on 2008-04-11
Manas, what is your computer ? can you give us the model ? This way we could know which wireless card you have :D

---

### Post by wribeiro on 2008-04-17
Please help me with my HP Pavilion dv6636, Ubuntu Hardy doesn't recognize my graphics card.
Video Graphics: NVIDIA GeForce Go 7150 (UMA)
Adapter type: NVIDIA MCP67M
Chip type: GeForce 7150M / nForce 630M

Any sugestion?

---

### Post by EXCiD3 on 2008-04-17
> **wribeiro said:**
> Please help me with my HP Pavilion dv6636, Ubuntu Hardy doesn't recognize my graphics card.
Video Graphics: NVIDIA GeForce Go 7150 (UMA)
Adapter type: NVIDIA MCP67M
Chip type: GeForce 7150M / nForce 630M

Any sugestion?

What happens when you boot into Hardy? Do you get to the desktop? Does the xserver fail to start?

---

### Post by wribeiro on 2008-04-17
No, Ubuntu starts, but only with 800x600 resolution, instead of 1280x800.
When I try to activate desktop efects, there is an error message: "DEsktop efects could not be enabled".
Ubuntu is using a wrong driver for my graphics card...

---

### Post by EXCiD3 on 2008-04-17
You need to enable the official nvidia drivers using the Restricted Drivers Manager. Here is a short tutorial on how to install using the RDM. [http://www.michaellarabel.com/?k=blog&i=114](http://www.michaellarabel.com/?k=blog&i=114)

---

### Post by ksbaker on 2008-04-17
I just bought a new compaq laptop (model F756NR) this is a [link]("http://www.bestbuy.com/site/olspage.jsp;jsessionid=0N5HJSOFQ1TAFKC4D3PFAHA?skuId=8648118&productCategoryId=abcat0502001&type=product&tab=1&id=1195598868093#productdetail")
to the best buy webpage describing it.  I am trying to install feisty fawn on it off a cd that came with a book I bought but it will not work.  Has anyone installed ubuntu on a similar computer?  Would you recommend a different distribution of linux to use on this computer that would install easier?  Thanks for any help!    [Also, I used this cd to install it on my IBM thinkpad and it works fine]

---

### Post by EXCiD3 on 2008-04-17
> **ksbaker said:**
> I just bought a new compaq laptop (model F756NR) this is a [link]("http://www.bestbuy.com/site/olspage.jsp;jsessionid=0N5HJSOFQ1TAFKC4D3PFAHA?skuId=8648118&productCategoryId=abcat0502001&type=product&tab=1&id=1195598868093#productdetail")
to the best buy webpage describing it.  I am trying to install feisty fawn on it off a cd that came with a book I bought but it will not work.  Has anyone installed ubuntu on a similar computer?  Would you recommend a different distribution of linux to use on this computer that would install easier?  Thanks for any help!    [Also, I used this cd to install it on my IBM thinkpad and it works fine]

Have you tried following either of these two guides? 
1) [http://ubuntuforums.org/showthread.php?t=512059](http://ubuntuforums.org/showthread.php?t=512059)
2) [http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)

You may also consider using Gutsy or waiting 7 days until the official release of Hardy Heron 8.04. These versions may work better with your laptop. Gutsy is sort of hit and miss with HP/Compaq laptops but Hardy has proved to be more reliable than both Feisty and Gutsy.

---

### Post by ksbaker on 2008-04-17
thank you.  i used the first guide and ubuntu is installed on my laptop now but i don't know how to get into the gui. thanks again for your help.

---

### Post by nickdbliss on 2008-04-18
Hi, i was just going through all the messages here and it was helpful.

I recently installed Ubuntu 7.10 Gutsy on my Hp nx6325. Everything works smoothly (wireless,sound, Graphics, Battery and Ac power switching) just the Fn+ Buttons. I cant increase or decrease my laptop's brightness. Have read so many threads related that and have used my own knowledge into it but its still not working. 

Anyone, who has solved this issue? I would really appreciate your help. Thanks.

Cheers for Linux

---

### Post by nickdbliss on 2008-04-18
Ok i have solved the problem not solved kinda know now how to change the LCD brightness  
It was accidental though lol.Was pressing Ctrl+Alt+F6 then i could change the brightness with normal function keys ie fn+f9 or f10 and again switching back with Ctrl+alt+f7. Also i found it verified at this link  [http://wiki.cchtml.com/index.php/HP](http://wiki.cchtml.com/index.php/HP) 


"...LCD-brightness can only be changed in VT (Ctrl+Alt+F1 -> change brightness -> switch back to X works)...."

Now i have flawless Ubuntu experience. Running great. Yippy hehe. :guitar:

---

### Post by krsnendu on 2008-04-18
> **EamonR said:**
> Hi there,

I have a HP Compaq 6715b with Gutsy installed.

The laptop has integrated --EDIT--BLUETOOTH, (I checked, it says so on the site, it shows in the bios, i think it worked on the vista the laptop came with, and it is physically there as I opened the panel on the laptop to make sure since I saw a screenshot of someone finding theirs was actually missing.)

However, I don't think I can find it in the hardware information, and when the bluetooth preferences app is set to display only when adapter is present, it disappears so it thinks the device is not present.

That command (hciconfig dev?) or something similar (can't quite remember what it is, you know the one), shows only "Devices:" and nothing else.

There is no switch I can find anywhere on the laptop to enable bluetooth like there is for the wireless unless I'm totally blind :P

Does anyone have any ideas?


Thanks :)

I have the same problem on Hardy. Did you get any solution?

BTW My ctrl and fn keys are switched. Any ideas how to fix that?

---

### Post by pitbullcarfc on 2008-05-02
Any one tried ubuntu 8.04 on Compaq F566LA?

---

### Post by marty1011 on 2008-05-04
> **amvella said:**
> Hey I am using ubuntu gutsy gibbon beta release. Everythig works for me except the realtek high definition audio. I tried to follow instructions on different threads but nothing helped. If you could find out a way to help me out.. That will be great. Thank You very much in advance

and by the way i am using a hp dv9500t laptop


There is a link to a website that I used at the end of the thread follow that. 
[http://ubuntuforums.org/showthread.php?t=698937](http://ubuntuforums.org/showthread.php?t=698937)

---

### Post by EXCiD3 on 2008-05-13
I finally finished my new tutorial for Ubuntu 8.04 Hardy Heron on HP and Compaq laptops. You can view it here: [http://excid3.pcriot.com/wordpress/?page_id=28](http://excid3.pcriot.com/wordpress/?page_id=28)

---

### Post by krsnendu on 2008-05-14
BTW My ctrl and fn keys are switched. Any ideas how to fix that?[/QUOTE]

I fixed this with a bios setting.
Also got he Bluetooth fixed by reseting the bios. It seems that if you used windows and disabled bluetooth it changed the bios. The only way to fix it is to reset bios.

---

### Post by EXCiD3 on 2008-05-14
Thats interesting...thanks for the info!

---

