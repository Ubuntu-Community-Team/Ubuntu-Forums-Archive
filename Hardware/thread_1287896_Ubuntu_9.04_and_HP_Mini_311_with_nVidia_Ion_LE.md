---
title: "Ubuntu 9.04 and HP Mini 311 with nVidia Ion LE"
date: 2009-10-10
forum: Hardware
---

### Post by JoeMac42 on 2009-10-10
My HP Mini 311 Atom 280/Ion LE Netbook arrived 3 days ago, so obviously I had to try installing Jaunty on it:) The standard 32-bit i386 Ubuntu Jaunty (desktop - not netbook remix) was installed from a Live CD using the HP external USB drive that shipped with the netbook.  I wasn't able to find any information on installing Ubuntu on the new Ion netbooks, so hopefully someone will benefit from this.

Most things seemed to work right out of the box (keyboard, backlighting keys, sound up/down keys, sleep/wake). Wifi did not work and sound was somewhat crippled, working only through the headphones but not through the built in speakers.

The Broadcom 4353 wifi was fixed following the instructions posted here:

[http://art.ubuntuforums.org/showthread.php?t=1263730](http://art.ubuntuforums.org/showthread.php?t=1263730) In summary: 1. Enable the backports repository: Administration > Software Sources > Updates and enable “Unsupported Updates (jaunty-backports)”. 2. Install the linux-backports-modules-jaunty package 3. Install the linux-restricted-modules package 4. Go to System -> Administration -> Hardware Drivers and enable the Broadcom Wireless chipset.

Sound was fixed by upgrading Alsa to version 1.0.21, which was very well documented here: [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

I had difficulty enabling the NVIDIA accelerated graphics driver (version 180) - I could see it listed under the Hardware Drivers menu but could not select it to enable it at first. Updating Jaunty fixed this.

---

### Post by JoeMac42 on 2009-10-10
I spoke a little too soon regarding sleep/wake.  I can initiate suspend by closing the lid or fn+f2, but it immediately wakes up before going completely down and goes to a password prompt.  Hibernate appears to engage and wake fine.  

I installed Skype.  Received video works great with no perceptible dropped frames from a relatively good source (MacBookPro via DSL both directions).  Video sent from the Mini 311 has very noticeable dropped frames but is "serviceable" - it doesn't crash the connection like other netbooks that I've tried with Ubuntu.   Sound in Skype was fine in both directions.

---

### Post by lirchi on 2009-10-11
Confirm the same suspend problem on Compaq mini 311 (the euro version of the hp - i think it is identical)
Any solution ?

---

### Post by lirchi on 2009-10-11
Confirm the same suspend problem on Compaq mini 311 (the HP Euro version), any solution ?

---

### Post by JoeMac42 on 2009-10-12
I found a solution that will work for now.  Neither suspend nor hibernate can adequately shut off the bluetooth.  Fortunately, there is a hardware disconnect (round button, above and to the right of the keyboard).  If you manually power down the bluetooth/wifi, then sleep and hibernate work normally.  I just confirmed that bluetooth/wifi will also reliably power back up by turning the hardware back on either during the resume or after resuming.  This should work should work for now until powering down USB is fixed...

---

### Post by kjacques on 2009-10-12
Hi, I have this machine on order. I am wondering compiz works with the nvidea ion chip and if you have any docks installed? I am using cairo-dock now under virtual box and the animations are very jittery.
 
Thanks,
 
Ken

---

### Post by JoeMac42 on 2009-10-12
compiz appears to be working.  I was considering installing cairo-docs anyway, so I'll give it a try tonight and check back in later.

---

### Post by kjacques on 2009-10-12
Great, thanks Joe for looking into this.

Ken

---

### Post by JoeMac42 on 2009-10-12
Wow, the cairo dock is some fairly nice eye-candy.  I tried one of the OS X themes and it looks and behaves very nicely.  I'm using the glx version of the dock with GPU acceleration.  Remember to set visual effects to something that triggers compiz on (select "normal" or "extra" under >system>appearance>visual effects).  Considerably less ram is used under under "normal".  Things get considerably bogged down if running both the dock and "extra" visual effects.  There is a free SODIMM slot under the back panel, so I should go ahead and add 1GB DDR3 SODIMM and retest.

---

### Post by JoeMac42 on 2009-10-12
Anyone have any idea what the second open slot is next to the hard-drive?  It's not filled with anything on my 311.  It's not for BT/Wifi, so I'm not sure what it is.  It was kind of nice to see HP left an open 204-pin SODIMM slot for RAM upgrade:)

---

### Post by kjacques on 2009-10-13
"I'm using the glx version of the dock with GPU acceleration". Is this a different version than regular cairo dock? Can you point me to where you got it? I've been downloading the stable version from Launchpad. [https://launchpad.net/~cairo-dock-team/+archive/ppa](https://launchpad.net/~cairo-dock-team/+archive/ppa)
 
Is the empty slot for a mobile broadband card? Here is a link to the mini 311 service [manual.]("http://h10025.www1.hp.com/ewfrf/wc/manualCategory?lc=en&dlc=en&cc=us&product=4011352&lang=en&") I think you can actually put a 2 gig ram chip in also. Can't wait for my machine to get here so I can try some of this stuff. Eta is not till the end of the month though... 
 
Ken

---

### Post by JoeMac42 on 2009-10-13
Both GLX and non-GLX flavors install with the standard installation.  You can try each out by going to >Applications>System Tools.  Once I confirmed that the dock worked with GPU acceleration, I stuck a pointer to it under >Sytem>Preferences>Startup Applications>Startup Programs tab>Add with

cairo-dock -o

as the code and then deleted the lower Gnome panel.

I ordered a 2GB DDR3 1066MHz Kingston SODIMM last night from Newegg.  We'll see how it works out.  Thanks for the link to the manual.  I have a spare 3.5" 250 GB SATA that I wanted to try out, but I was having trouble seeing how the HD rails were attached.

---

### Post by kjacques on 2009-10-14
Let me know how the upgraded memory and hard drive swap goes for you.
 
Ken

---

### Post by demonfoo on 2009-10-17
I've installed Karmic on my Mini 311, and so far everything has worked out of the box except for WiFi. I've tried the 'wl' driver included with karmic, the slightly-newer driver downloaded from Broadcom's site, and I've also tried tracking down their Windows drivers and attempting to use them via ndisloader. Using ndisloader always manages to Oops the kernel, and using 'wl' manages to discover networks, but when I try to join them (even the neighbor's open, unencrypted wireless net), I always get:

Oct 16 14:24:01 swordfish wpa_supplicant[959]: CTRL-EVENT-SCAN-RESULTS 
Oct 16 14:24:01 swordfish wpa_supplicant[959]: Trying to associate with 00:1b:63:23:74:1b (SSID='mars' freq=2412 MHz)
Oct 16 14:24:01 swordfish wpa_supplicant[959]: Association request to the driver failed
Oct 16 14:24:06 swordfish wpa_supplicant[959]: Authentication with 00:1b:63:23:74:1b timed out.

It will eventually reprompt me for the network passphrase for my network, or just fail out entirely for an unencrypted network. What can I do to resolve this? I'm liking the unit, but the lack of working WiFi is a real letdown.

---

### Post by kjacques on 2009-10-17
Can't be much help with your problem because I don't yet have my mini. Mine appears to be in Shanghai and is supposed to ship on Monday. Maybe Joe might have some insight.

Ken

---

### Post by kamaboko on 2009-10-17
Hello JoeMac,

I just picked up a mini 311 with the N270.  How is yours running so far?  Can you post a vid on Youtube with a tour of your install and how it's working?  

K

---

### Post by demonfoo on 2009-10-18
It definitely *seems* to be a wpasupplicant issue; I manually associated the WiFi interface with a neighbor's access point that has no encryption, and then ran dhclient against the interface - it acquired an IP, and I'm able to get traffic across it consistently - so the problem definitely appears to be something specific to wpasupplicant, not a driver problem per se.

Edit: I think _[[U]this bug_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404433") [/U]is what's responsible for my problem. I'm attempting to find a way to fix the symbol versions so that I can build the wl driver against the backport module headers.

Edit 2: This does seem to have helped, I've been able to attach to a WiFi network, at least some of the time. Unfortunately I had to do a fair amount of screwing around to make it so that the symbol versions were fixed up to that I could load the wl.ko driver against the lib80211 module from the 'linux-backports-modules-2.6.31-14-generic' package; why is there not a -dev or headers package based on this for this very reason, since it does replace lib80211.ko?

Edit 3: Okay, yes, it's completely fixed; I forgot to add its MAC to the allow list on my access point. Duh.

---

### Post by mocha on 2009-10-19
I'm considering purchasing this netbook for its Nvidia ION VDPAU capabilities.  Can someone that owns it try testing HD media playback with mplayer or xine with VDPAU compiled in?  You should have almost no CPU consumption.  There are some PPAs out there with pre-compiled VDPAU mplayer.  Also, what versions of the nvidia binary driver are you guys using, the Karmic repo version?  Thanks.

---

### Post by demonfoo on 2009-10-19
> **mocha said:**
> I'm considering purchasing this netbook for its Nvidia ION VDPAU capabilities.  Can someone that owns it try testing HD media playback with mplayer or xine with VDPAU compiled in?  You should have almost no CPU consumption.  There are some PPAs out there with pre-compiled VDPAU mplayer.  Also, what versions of the nvidia binary driver are you guys using, the Karmic repo version?  Thanks.

Yes, VDPAU works fine on mine with Karmic; however, there's an additional repo you need to add for VDPAU-enabled xine-lib (mplayer is in mainline karmic, I believe). The CPU usage when playing 720p trailers downloaded from Apple's trailer site is ~18% in Xine, and ~25% in mplayer, with no dropped frames. I'm using the 185 package version supplied with karmic, which so far seems to work perfectly (including HDMI out; haven't tried VGA out yet, but I'm guessing it's the same story). The repo I mentioned is:

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

---

### Post by demonfoo on 2009-10-19
Also, on an unrelated note - I've figured out a way to update the BIOS on the Mini 311 (successfully updated mine from the F.02 release build it shipped with to the F.04 release build on the HP web site).

This involved:


[LIST]
[*]Using Wine and a tool called UniExtract to extract the files from the InstallShield installer image provided on the HP site (then extracting the one *inside* that, which actually contains the updater and the Flash ROM image)
[*]Finding the BIOS update tool for the Acer Aspire One netbook (same BIOS vendor, and contains a DOS tool called FLASHIT.EXE that works for this vendor's BIOS)
[*]Assembling a floppy image containing FreeDOS to be loaded with MEMDISK, using HIMEM.SYS + TDSK.EXE (a RAM disk tool which doesn't require EMM386.EXE)
[*]Booting the faux disk with MEMDISK via PXE (FreeDOS got confused when I tried to load it from GRUB on a USB flash disk; it kept hanging up trying to grok it as a hard disk)
[/LIST]
If anyone's terribly interested, I can explain the process in more detail.

Edit: After doing a bit of research, I've discovered why I wasn't able to boot the image via MEMDISK direct from GRUB2; seems that "linux16" and "initrd16" directives are what I was missing, so I should be able to just update the BIOS direct from GRUB in the future. Even better. Saves the need to PXE boot the silly thing.

Edit 2: I've written a Perl script to use 7zip, unzip, mtools, wine, wget, and a tool called isxunpack to generate a FreeDOS boot floppy for updating the Mini 311's BIOS. Tested in QEMU, so far seems to work as expected (of course not doing the actual ROM flash, but everything up to that point).

---

### Post by mocha on 2009-10-20
This sounds really nice, I've been waiting a long time for a netbook with nvidia ION that I can install Linux on.  So is everything else working OK?  Wireless, sound, input devices, etc?  I wonder how ubuntu netbook remix or crunchbang would run on this.  Do you feel the stock Karmic installation to be slow or struggling along with the Atom processor?  I assume your using Gnome.

---

### Post by demonfoo on 2009-10-20
> **mocha said:**
> This sounds really nice, I've been waiting a long time for a netbook with nvidia ION that I can install Linux on.  So is everything else working OK?  Wireless, sound, input devices, etc?

Everything works 100%. Bluetooth (paired with my BlackBerry 8830), WiFi (after messing with the drivers, the only thing I had trouble with), keyboard, touchpad, all USB ports, card slot (tried with SD and MS/MSPro), HDMI (including audio out), 3D graphics (tried with several Telltale Games titles via Wine), suspend, webcam (works perfectly with the Linux version of Skype). It almost completely worked out of the box, and the WiFi issue appears to be a known thing with karmic.

> **mocha said:**
> I wonder how ubuntu netbook remix or crunchbang would run on this.  Do you feel the stock Karmic installation to be slow or struggling along with the Atom processor?  I assume your using Gnome.

I don't find it to be particularly slow, no, the responsiveness seems reasonable for an Atom CPU. Yes, I'm using the Gnome desktop on mine. Firefox does seem a little slower than on my desktop system (still running Jaunty), but considering I only have 1 GB of RAM in it, and the CPU, it doesn't seem too out of line for what it is. I'm very pleased with it, and if anyone's looking for a netbook with good Linux compatibility, this would be a great choice.

Edit: Keep in mind that I got the unit with the N280 processor (1.66 GHz core speed, 667 MHz FSB), so the N270-based units are probably a bit slower than what I have...

---

### Post by mocha on 2009-10-20
Thanks for the comments.  What about the headphone/mic jack?  Is it a combined type?  Does it work properly?

Where did you purchase yours.  All the ones I see online are N270.

---

### Post by demonfoo on 2009-10-20
> **mocha said:**
> Thanks for the comments.  What about the headphone/mic jack?  Is it a combined type?  Does it work properly?

Hadn't tried it till just now. Yes, it works fine, and yes, it's a combined port - apparently for the headsets with an integrated mic with a 4-conductor 1/8" headphone connector.

> **mocha said:**
>  Where did you purchase yours.  All the ones I see online are N270.

I purchased one direct from HP's web site - I got the N280 with 802.11n and Bluetooth, the stock unit (as you've no doubt noticed) has the N270 and 802.11g without Bluetooth support. It was only an extra $75 for the upgrades I got, so I figured why not...

---

### Post by rvugts on 2009-10-24
I can confirm that Ubuntu 9.04 **Remix** works fine on the HP Mini 311c too.

I installed from a Live CD using a 1GB USB stick.

No special steps were required to make wifi work, it worked right out of the box for me.

Installing the NVIDIA accelerated graphics driver (version 180) is required to be able to use the correct screen resolution and experience decent graphics performance.

The only flaws are the already mentioned suspend and sound problems. As mentioned earlier in this thread, powering down bluetooth/wifi via the on/off button before initiating suspend fixes the suspend problem.

Having used the netbook for only a few days I get the impression that battery life under Ubuntu Remix is not as good as under Windows XP (I have not properly tested this though!). Turning off bluetooth/wifi when not needed makes quite a difference.

I'm very pleased with the Mini + Ubuntu Remix combination. The Mini has a stylish design, but the shiny shell is very sensitive to scratches and collects fingerprints very easily.

Regards,
Rob

---

### Post by dhahn on 2009-10-24
I got my mini 311 yesterday. I tried installing ubuntu-9.10-rc-desktop-i386.iso .

My system would get the initial splashscreen, but when I selected 'run ubuntu without installing' there would be a flash of USB activity and then a blank screen with a blinking cursor. I tried this many times, occasionally it would boot and work perfectly. I was even able to do a full install (thereby wiping XP and no going back).

Booting from the installed 9.10 had the same problem. It would normally just go to a blank screen with a blinking cursor, sometimes I would get grub before the blank screen, rarely it would boot and work.

I tried ubuntu-9.10-rc-netbook-remix-i386.iso with the same results.
MD5 hash was fine. Any suggestions for finding a log of what is happening?

Any ideas?
1) HW problem with the 311.
2) Bad USB stick.
3) Need to update the BIOS.
4) 9.10 not ready (I'll try 9.04 next). 9.10 worked great, I could use wifi from the live boot.
5) ???????

---

### Post by dhahn on 2009-10-24
My problem (boot to blank screen) seems to be related to acpi/grub.
Investigating and I'll post when I've fully debugged.

---

### Post by unsungboxer on 2009-10-24
Thank you everyone for your work on this.  I am ordering my HP 311 right now, and hope to load ubuntu 9.10 the moment it hits my doorstep.

---

### Post by rvugts on 2009-10-24
I was unable to get the live CD of Remix 9.10 to boot properly. You might be better off installing 9.04 first.

---

### Post by JoeMac42 on 2009-10-24
I just upgraded my mini 311 from Jaunty to Koala.  It took awhile, but pretty much went without a hitch.  Now the fn-f10 and fn-f11 actually work for  turning the sound up and down rather than just "acting" like it did by moving the bar graphic.  Lotus Notes 8.5 broke with Koala, but there are workarounds for the few poor souls like me that need it for enterprise e-mail.

The Kingston memory upgrade worked great.  Everything seems happier with the extra 2GB of RAM.  It's probably completely psychological, but I was occasionally freezing X under Jaunty - so far not at all with Koala.  I realise the beta has 5 more days to go until the public release, but Koala seems like the way to go for the mini 311.

---

### Post by unsungboxer on 2009-10-24
So it sounds like its best to load 9.04 then use update-manager to upgrade to 9.10?

I am so excited to get my 311.  I have been intending on using it as a media center.  Can anyone speak to the performance of:

1.  3D graphics like the ubuntu cube?
2.  the HDMI output using ubuntu
3.  Playback quality of hulu
4.  smoothness of cooliris?

I appreciate the response.

---

### Post by JoeMac42 on 2009-10-24
Sleep now works in Koala without using the hardware shutoff for bluetooth. Resume seems to work fine, too.  Hibernate looks like it is still having trouble shutting bluetooth off, but it does seem to go down eventually.

---

### Post by kjacques on 2009-10-24
Good to hear Joe, Mine came yesterday. So far everything is good with 9.04 except sound. I followed the instructions on page one to get it fixed but must have done something wrong. Will try again tomorrow. Think I'll go for the ram upgrade.

Ken

Update: Sound is now working after redoing instructions on page 1.

---

### Post by rvugts on 2009-10-25
Does sound over speakers work in 9.10?

---

### Post by rvugts on 2009-10-25
I have just completed the upgrade from 9.04 to Ubuntu Remix 9.10. Sound and suspend now work out of the box. Battery life seems better too now. I'm very impressed with the look and feel of 9.10. It is worth the upgrade just for that :)

---

### Post by demonfoo on 2009-10-26
> **unsungboxer said:**
> So it sounds like its best to load 9.04 then use update-manager to upgrade to 9.10?

I am so excited to get my 311.  I have been intending on using it as a media center.  Can anyone speak to the performance of:

1.  3D graphics like the ubuntu cube?

What's this?

> **unsungboxer said:**
>  2.  the HDMI output using ubuntu

I hooked mine up to my Sony XBR8, and enabled TwinView via the nVidia settings app; VDPAU-accelerated video playback to the TV worked just fine, no glitches or slowdowns. No restarts required.

> **unsungboxer said:**
> 4.  smoothness of cooliris?

Don't know, going to have to check this out.

Edit: It does seem that it works alright, but it's a bit choppy. I'll have to try it on my Ubuntu desktop box and see how the two compare.

---

### Post by kjacques on 2009-10-26
I have a question about the ion cpu. How do I know if a video is being passed to it as supposed to the cpu handling the task. I downloaded a 720p quiktime video and it mplayer installed the various codecs it needed but the video was very choppy and unwatchible. Is there a preference I need to set in mplayer? 
 
I saw the post about VDPAU and added this repository. 
 
deb [[COLOR=#444444]http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu") karmic main
 
What do I need to download? I tried sudo apt-get install VDPAU but it said package does not exist.
 
Thanks,
 
Ken

---

### Post by demonfoo on 2009-10-26
> **kjacques said:**
> I have a question about the ion cpu. How do I know if a video is being passed to it as supposed to the cpu handling the task. I downloaded a 720p quiktime video and it mplayer installed the various codecs it needed but the video was very choppy and unwatchible. Is there a preference I need to set in mplayer?

Oh mplayer, you're such a card. It thinks it's being smart by forcing the normal (i.e., non-VDPAU) decode path, even though you have VDPAU on your system. Edit your ~/.mplayer/config file, and add these two lines *exactly* as shown (yes, the trailing commas included, they tell it to fall back to defaults if the VDPAU codec paths fail):

```

vo=vdpau,xv,
vc=ffh264vdpau,ffvc1vdpau,ffmpeg12vdpau,

```When you play a video that's accelerated by VDPAU, your CPU usage should drop to ~20-25%, and you should see something like this in the terminal window you ran mplayer from:

```

==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================

```and:

```

VDec: vo config request - 1280 x 688 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 1280x688 => 1280x688 H.264 VDPAU acceleration 

```> **kjacques said:**
> I saw the post about VDPAU and added this repository. 
 
deb [[COLOR=#444444]http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu") karmic main

The mplayer packages in the mainline repositories will do VDPAU, but the xine-lib in mainline karmic won't. If you want to use xine, just install it normally after adding that repository, and it'll "just work". Just select "vdpau" as the output driver in the Xine settings panel, and it'll use it (and fall back to Xv for codecs other than H.264, VC-1 and MPEG-2).

> **kjacques said:**
>  What do I need to download? I tried sudo apt-get install VDPAU but it said package does not exist.

Nothing. As long as you have the native nVidia drivers installed and used on your machine, VDPAU will be enabled automatically.

---

### Post by kjacques on 2009-10-26
Great, thanks for the advice. I'll try this out tonight.
 
Ken

Update: Thanks to demonfoo's great instructions mplayer video's are no longer choppy.

---

### Post by unsungboxer on 2009-10-26
> **demonfoo said:**
>  (Ubuntu Cube) What's this?

I think this girl can explain the cube:  [http://www.youtube.com/watch?v=LGY9cwSjZsU]("http://www.youtube.com/watch?v=LGY9cwSjZsU")

Get:
```
sudo apt-get install compizconfig-settings-manager
```

Run:
```
ccsm
```

Configure:
Genral Options, Desktop Size = Horiz= 4 , Vert= 1
Toggle on Desktop Cube
Toggle on Rotate Cube

:popcorn:

---

### Post by demonfoo on 2009-10-27
> **unsungboxer said:**
> I think this girl can explain the cube:

Okay, I was aware of the rotating-cube desktop transition, but I thought since "Ubuntu cube" was the used phrase, that something else was being referred to. I tried it last night, and it seems reasonably smooth to me, but I did revert to the default switch animation. :)

---

### Post by unsungboxer on 2009-10-27
Please help:

I just got my VZW HP 311.  I am trying to install Ubuntu 9.10 with now luck.  The ubi-console-setup keeps failing.  I am also getting errors about low disk space. I am installing from a 10gb (tried both regular and UNR iso's).

My assumption is that it is trying to install on a smaller partition, but I am not sure how to change this.  I can't even get to the partitioner part of the setup to choose.

Edit(1):  Tried 3 different iso's. Kept running into disk space errors and ubiquity crashes.  Tried installing 9.04 and it went without a hitch.  I will upgrade from 9.04 to 9.10 as others here have.  Seems to be an issue w/ 9.10 iso.

Edit(2):  9.04 doesn't support wifi on the VZW HP 311, had to use direct connection.  Then upgraded to 9.10 with ```
update-manager-d
```

---

### Post by JoeMac42 on 2009-10-27
I've now had a few days with Karmic.  I still see an occasional instance of hibernate or suspend having difficulty powering down bluetooth in Karmic, so I  make a habit of using the hardware switch prior to suspend.  Wifi seems much flakier in Karmic than Jaunty but that doesn't appear to be limited to the mini 311. I sometimes need to reboot in order for the wifi (eth1) to obtain an IP address from DHCP - and never a problem for wired ethernet (eth0).

Cairo dock is _much_ less buggy on the 311 in karmic than in Jaunty.  

I haven't tested it, but battery life does "seem" to be longer in Karmic.  The nVidia 185 graphics driver now properly ID's the Ion chipset - 180 listed it as "unknown" but still seemed to work.  I played a large divx movie over HDMI out to a 24" Dell flat panel with very good image quality and no noticeable dropped frames.  Pretty damn impressive.

---

### Post by unsungboxer on 2009-10-28
After updating from 9.04-9.10 UNR, I get stuck on the boot screen.  It says something about "one or more devices from /etc/FSTAB can't be mounted", then drops to a flashing shell.  Typing in it is nearly impossible.

---

### Post by demonfoo on 2009-10-28
> **JoeMac42 said:**
> I still see an occasional instance of hibernate or suspend having difficulty powering down bluetooth in Karmic, so I  make a habit of using the hardware switch prior to suspend.

I haven't run across this myself, maybe due to different Bluetooth hardware (I think it's integrated with the WiFi board)?

> **JoeMac42 said:**
> Wifi seems much flakier in Karmic than Jaunty but that doesn't appear to be limited to the mini 311.

I haven't used Jaunty on anything with WiFi, so I don't have a point of comparison there.

> **JoeMac42 said:**
> I sometimes need to reboot in order for the wifi (eth1) to obtain an IP address from DHCP - and never a problem for wired ethernet (eth0).

Did you get the 802.11g or n wireless? What driver are you using? I've not had this problem on mine (802.11n wireless, Broadcom wl driver), though sometimes it takes a few tries to associate to a WPA/WPA2 network.

---

### Post by JoeMac42 on 2009-10-28
I have 802.11n wireless and Broadcom STA wireless driver.  We'll see if this works itself out in the karmic updates.

I also just noticed that the webcam is now broken in skype after upgrading to Karmic - webcam works fine in cheese but not skype and none of the typical libv4l skype hacks seem to work.  Camera light comes on during video test in skype, but no video signal passes through.  

I hate having to dual-boot xp just to skype with video - I was hoping to ditch the 75 GB NTFS partition.  I guess I'll have to put that off for a bit.

---

### Post by demonfoo on 2009-10-28
> **JoeMac42 said:**
> I also just noticed that the webcam is now broken in skype after upgrading to Karmic - webcam works fine in cheese but not skype and none of the typical libv4l skype hacks seem to work.  Camera light comes on during video test in skype, but no video signal passes through.  

I hate having to dual-boot xp just to skype with video - I was hoping to ditch the 75 GB NTFS partition.  I guess I'll have to put that off for a bit.

Erm, the webcam works perfectly for me. What kernel package are you running there?

---

### Post by JoeMac42 on 2009-10-29
2.6.31-14-generic.  Odd thing is that Skype seems to be the only thing the webcam doesn't work in.

---

### Post by kjacques on 2009-10-29
> **JoeMac42 said:**
> 2.6.31-14-generic. Odd thing is that Skype seems to be the only thing the webcam doesn't work in.
 
I was having problems receiving video in Ubuntu 9.04 and it seemed to be related to having Cairo-dock running. I found this thread about it [http://ubuntuforums.org/showthread.php?t=1161113](http://ubuntuforums.org/showthread.php?t=1161113) and added this code to the Skype Launcher in Cairo-Dock
 
export XLIB_SKIP_ARGB_VISUALS=1 && skype
 
Ken

---

### Post by anewman on 2009-10-29
Apparently the ION Le is just a driver crippled Ion full fat. See [http://myhpmini.com/forum/viewtopic.php?f=59&t=2571](http://myhpmini.com/forum/viewtopic.php?f=59&t=2571) for details. I don't know if this information will inform any possible unlocking of DX10 on Ubuntu, or indeed if DX10 makes any difference on Ubuntu. Waiting for the knowledgeable people's input :D

> **unsungboxer said:**
> I think this girl can explain the cube:  [http://www.youtube.com/watch?v=LGY9cwSjZsU]("http://www.youtube.com/watch?v=LGY9cwSjZsU")
:popcorn:
I wish my girlfriend could show me how to use linux :D

---

### Post by demonfoo on 2009-10-29
> **anewman said:**
> Apparently the ION Le is just a driver crippled Ion full fat. See [http://myhpmini.com/forum/viewtopic.php?f=59&t=2571](http://myhpmini.com/forum/viewtopic.php?f=59&t=2571) for details. I don't know if this information will inform any possible unlocking of DX10 on Ubuntu, or indeed if DX10 makes any difference on Ubuntu. Waiting for the knowledgeable people's input :D

A friend and I had posited that it was just a different ROM; I guess this makes it not even that. I don't know if DX9 vs. DX10 will make any difference with their Linux GL drivers or not; I'm not even sure what GL extensions (if any) would apply to the added features, to be honest.

---

### Post by unsungboxer on 2009-10-30
update: using the vzw hp 311, installation and boot work fine.  Wifi works well, just need to go to administration > hardware drivers and enable it.   Webcam works with cheese.  advanced desktop settings work well too.

Next step is to get the vzw gobi chip to work...  vzw version uses the hp un2400 chip, better discussed here:
[http://art.ubuntuforums.org/showthread.php?p=8206747#post8206747]("http://art.ubuntuforums.org/showthread.php?p=8206747#post8206747")

---

### Post by JoeMac42 on 2009-10-30
> **kjacques said:**
> i was having problems receiving video in ubuntu 9.04 and it seemed to be related to having cairo-dock running. I found this thread about it [http://ubuntuforums.org/showthread.php?t=1161113](http://ubuntuforums.org/showthread.php?t=1161113) and added this code to the skype launcher in cairo-dock
 
export xlib_skip_argb_visuals=1 && skype
 
ken

That fixed it!  You rock Ken.  I had a business trip to Asia coming up this weekend - now I can do a video hookup with my family while I'm gone.

---

### Post by kjacques on 2009-10-31
No problem, hope your trip goes well.

---

### Post by thork on 2009-11-02
@dhahn 

Hi,

I have the same problem - blank screen with 9.10 usb-Stick and thought it was due to  problems with installing via usb-stick and ordered an usb-cd rom. Have you yet found a solution to the blank screen / grub-acpi problem? 

Do you have the same problem when installing 9.04 and dist-upgrade to 9.10? Anyone else with problems installing 9.10 with usb-stick or did everyone else installed with 9.04 and dist-upgraded to 9.10?

Right now I have a 311 at home with no os on it and I really don't want to have to install win XP ;)

Many thx in advance & greeeting from germany 

Thorsten


> **dhahn said:**
> I got my mini 311 yesterday. I tried installing ubuntu-9.10-rc-desktop-i386.iso .

My system would get the initial splashscreen, but when I selected 'run ubuntu without installing' there would be a flash of USB activity and then a blank screen with a blinking cursor. I tried this many times, occasionally it would boot and work perfectly. I was even able to do a full install (thereby wiping XP and no going back).

Booting from the installed 9.10 had the same problem. It would normally just go to a blank screen with a blinking cursor, sometimes I would get grub before the blank screen, rarely it would boot and work.

I tried ubuntu-9.10-rc-netbook-remix-i386.iso with the same results.
MD5 hash was fine. Any suggestions for finding a log of what is happening?

Any ideas?
1) HW problem with the 311.
2) Bad USB stick.
3) Need to update the BIOS.
4) 9.10 not ready (I'll try 9.04 next). 9.10 worked great, I could use wifi from the live boot.
5) ???????

---

### Post by jatinps on 2009-11-02
I am planning on buying the hp mini 311 in 2 weeks time, as it seems to be the only netbook priced system capable of outputting 1080p on hdmi. My primary usage is a good light portable capable of playing my HD collection when on the move, as well as outputting HD effortlessly to my panasonic plasma when at home.

I couldn't find any other tiny laptop, capable of doing this.

Obviously the OS of choice is 'not windows' and I already use ubuntu on my office ibm x61s (not supported by corp IT team) :)

This thread was the most encouraging for me to finalize on the hp mini 311 !

---

### Post by thork on 2009-11-02
I just tried to install from an 9.04 usb-stick and after displaying the ubuntu logo I end up at a shell (busybox) ... :( 

I got Bios Version F.02 on my compaq Mini 311c (should be the same hardware as the US hp mini 311. 

Anyone any clue?

Thanks in advance, 
Thorsten

---

### Post by demonfoo on 2009-11-02
> **thork said:**
> I just tried to install from an 9.04 usb-stick and after displaying the ubuntu logo I end up at a shell (busybox) ... :( 

I got Bios Version F.02 on my compaq Mini 311c (should be the same hardware as the US hp mini 311. 

When I installed my Mini 311 with Ubuntu, I didn't really understand how to make use of the usb stick image set, so I just installed GRUB on it, and used the netinst image set to install with; this worked perfectly for me.

Edit: Also, if you want to upgrade your BIOS to the latest once you get Ubuntu on it, use the following script I wrote:

[http://now.ai/files/mini311-biosupdate-builder.pl.gz](http://now.ai/files/mini311-biosupdate-builder.pl.gz)

gunzip it, run the script to generate the image, and follow the instructions at the start of the script to use the generated image.

---

### Post by demonfoo on 2009-11-02
Also, I've tested VGA output with my Mini 311 - it also works perfectly (as expected). I haven't felt like wiring everything up at once to do 3 displays (internal, HDMI, and VGA) all at once - someone let me know if that works. :)

---

### Post by jatinps on 2009-11-03
For those concerned about the differences between HP mini with n280 and n270 - there seems to be no difference between ION and ION-LE
[http://www.nvidia.com/object/picoatom_specifications.html](http://www.nvidia.com/object/picoatom_specifications.html)

Only directx10 support is additional in full ION - is that even relevant to Linux?

---

### Post by kjacques on 2009-11-04
Anybody here using Conky? I need some guidence on getting the load and temp (in Farenheit) for the ion GPU.

---

### Post by thork on 2009-11-04
I now managed to install via cdrom - without any problems (had massive problems with USB-Install). 

Nearly everything worked ootb. The only thing thats missing is display of time remaining with battery (it shows the load in % but not the time). Any ideas?

Thanks in advance!

Thorsten

---

### Post by demonfoo on 2009-11-04
> **kjacques said:**
> Anybody here using Conky? I need some guidence on getting the load and temp (in Farenheit) for the ion GPU.

I don't know how you'd find the load, but the temperature in Celsius can be determined through the nvidia-settings applet. I'm not sure how you'd get that programmatically though...

---

### Post by watchthestars on 2009-11-08
I'm having a heckuvatime getting my Mini 311's bluetooth adapter to work. Karmic will see the adapter prior to installing the Broadcom STA drivers but then.. nothing. I have the BCM4312 b/g variant. Any suggestions?

---

### Post by demonfoo on 2009-11-08
> **watchthestars said:**
> I'm having a heckuvatime getting my Mini 311's bluetooth adapter to work. Karmic will see the adapter prior to installing the Broadcom STA drivers but then.. nothing. I have the BCM4312 b/g variant. Any suggestions?

I'm using the 802.11n version, and I haven't run into this problem. That said, is the RF kill switch activated? Is the indicator behind it blue (wireless enabled) or orange (wireless disabled)? Make sure that wireless is enabled, or the USB endpoint for the Bluetooth HCI device will go bye-bye.

---

### Post by watchthestars on 2009-11-08
> **demonfoo said:**
> I'm using the 802.11n version, and I haven't run into this problem. That said, is the RF kill switch activated? Is the indicator behind it blue (wireless enabled) or orange (wireless disabled)? Make sure that wireless is enabled, or the USB endpoint for the Bluetooth HCI device will go bye-bye.

I think I'm getting a bit closer to successfully running both at the same time. When I remove the STA driver suggested by System > Administration > Hardware Drivers and reboot, bluetooth-applet starts up just fine at login and works just fine. The RF switch is orange at this point and the wifi doesn't function. Pressing the RF switch results in turning off the bluetooth and no change in the color. I then downloaded and compiled the BCM3412 drivers straight from Broadcom and had BT and Wifi until a reboot. I lost the wifi after the reboot, but the BT was still there. Finally, I reinstalled the STA drivers from hardware manager and rebooted. This time BT & Wifi were working... until I hit the RF switch. Both stopped and hitting the switch again resulted in only Wifi coming back up. Running sudo bluetooth-applet results in...

$ sudo bluetooth-applet
** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3

At this point I think it's the RF switch state somehow preventing bluetooth-applet from running. Could I be right?

**Edit:** Solved. I downloaded ndiswrapper and used the windows drivers supplied by HP. Everything works.

---

### Post by djurny on 2009-11-13
just out of curiosity as i'm also looking into getting me a compaq mini311c.. does rmmod'ing at suspend and insmod'ing at resume of all bt related modules help the suspend-resume failure? instead of turning it off manually at suspend?

---

### Post by demonfoo on 2009-11-13
> **djurny said:**
> just out of curiosity as i'm also looking into getting me a compaq mini311c.. does rmmod'ing at suspend and insmod'ing at resume of all bt related modules help the suspend-resume failure? instead of turning it off manually at suspend?

I suspend my Mini 311 all the time without having to unload any drivers. You should definitely run 9.10 at this point.

---

### Post by rjackson1969 on 2009-11-14
HP mini 311.

Having absolutely no luck with installing Ubuntu.

UNR 9.10
After install I get past grub, past splash screen to a blinking cursor constantly flashing asking me to log in which, because it's constantly flashing is all but impossible. This is both installing 9.10 from live thumb drive and from upgrading from 9.04.

UNR 9.04
After install I can boot into it. Everything in the OS is creeping along. I click on something it takes about five to ten seconds to react. Once I open firefox, I can get around inside firefox at a decent pace but if I minimize it, it's like the refresh rate is crap, then I have to wait for the ability to click on anything else in the OS.

I've installed 9.04 & 9.10 from live thumb drives... burned them to CD and installed from usb live CD. Installed 9.04 and then tried to upgrade to 9.10.

Nothing is working. I wish I could just get to where you guys are so at least the system is up. I'm doing a full install for the whole hard drive. No dual booting. I'd like to be on ext4 as and not upgrading to 9.10 using the ext3 system.

---

### Post by mocha on 2009-11-16
I think your upgrade problem is related to this [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917")

If I were you I'd just install the latest 190.42 driver from nvidia's website.

---

### Post by arsenix on 2009-11-17
Has anyone found a fix for the wifi related boot failures?  I just got one of these and basically it boots about 1 out of 10 tries.  I removed the wifi card and it starts up just fine every time.  I kinda want wifi though.

This is with a fresh install of Karmic.  I'm still rooting around to find the cause of the fault, but it seems to crash about 2.5 seconds into the boot process (by the kernel counter).

EDIT: blacklisting b43-pci-bridge and rebuilding the initramfs allows the machine to boot.  I installed the Broadcom STA driver and so far it seem to work fine.


James

---

### Post by watchthestars on 2009-11-17
> **arsenix said:**
> Has anyone found a fix for the wifi related boot failures?  I just got one of these and basically it boots about 1 out of 10 tries.  I removed the wifi card and it starts up just fine every time.  I kinda want wifi though.

This is with a fresh install of Karmic.  I'm still rooting around to find the cause of the fault, but it seems to crash about 2.5 seconds into the boot process (by the kernel counter).

EDIT: blacklisting b43-pci-bridge and rebuilding the initramfs allows the machine to boot.  I installed the Broadcom STA driver and so far it seem to work fine.

James

I had the same problem... and the same solution.

---

### Post by arsenix on 2009-11-19
What 3D apps have folks successfully run on the machine?  I bought it for my young son and have been installing some of his favorite opensource games.  So far I have not had much luck with 3D apps.

  I installed tux racer extreme and scorched3d... both are completely unplayable.  They both run <5fps.  I did install armegetron and it runs great, but its 3d graphics are fairly simple.

  Have others had similar experiences?  I'm running Karmic 32 bit, nvidia 185 driver.  My machine has 1GB of ram (maybe this needs to be bumped up).

James

---

### Post by jcran on 2009-11-19
same problems here. intermittent booting issues.

---

### Post by jcran on 2009-11-19
so... we were able to get the hp311 working by continually booting recovery mode, then using jockey-text -l (to list possible drivers) and jockey-text -e (to enable possible drivers)

---

### Post by watchthestars on 2009-11-19
> **jcran said:**
> so... we were able to get the hp311 working by continually booting recovery mode, then using jockey-text -l (to list possible drivers) and jockey-text -e (to enable possible drivers)

I was having a similar boot problem until I blacklisted the b43 wifi driver that the clean installed defaulted to. I'm currently using ndiswrapper with no problems.

---

### Post by rjackson1969 on 2009-11-20
> **mocha said:**
> I think your upgrade problem is related to this [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/474917)

If I were you I'd just install the latest 190.42 driver from nvidia's website.

Have any instruction to install the driver? I found this website and followed his instructions and got a big fat fail trying to install it on my jaunty install.


[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)


If there are any other sources that do work, I'd sure appreciate it.

---

### Post by mocha on 2009-11-22
> **rjackson1969 said:**
> Have any instruction to install the driver? I found this website and followed his instructions and got a big fat fail trying to install it on my jaunty install.


[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)


If there are any other sources that do work, I'd sure appreciate it.

Basically all you have to do is go to synaptic and uninstall everything that has nvidia in the name, that should remove all of the repo drivers.  Then reboot and you'll get a low resolution, then logout and get a command prompt (Ctrl-Alt-F1), then stop gdm (sudo services gdm stop), then go to the directory with the nvidia .run package and sudo ./packagename, then reboot.  That should take care of it.

---

### Post by JoeMac42 on 2009-11-23
Suspend/resume and hibernate/resume seems to have been fixed in an update, maybe about 3-weeks ago.  I no longer need to shut off the hardware manually.  I just returned from 3-weeks knocking around China, Japan and Korea with the mini 311 running 9.10 without any problems other than occasionally having to reboot to obtain an IP address when encountering a new wifi access point.

---

### Post by amaroKer on 2009-11-23
> **arsenix said:**
> Has anyone found a fix for the wifi related boot failures?  I just got one of these and basically it boots about 1 out of 10 tries.  I removed the wifi card and it starts up just fine every time.  I kinda want wifi though.

This is with a fresh install of Karmic.  I'm still rooting around to find the cause of the fault, but it seems to crash about 2.5 seconds into the boot process (by the kernel counter).

EDIT: blacklisting b43-pci-bridge and rebuilding the initramfs allows the machine to boot.  I installed the Broadcom STA driver and so far it seem to work fine.


James

1. What type of boot failure are you experiencing?  I am getting a flashing text cursor on a black screen.

2. How does one go about rebuilding initramfs?  What does that do?

3. What could I do to begin troubleshooting or diagnose a failed boot?

Logan

---

### Post by anewman on 2009-11-23
> **amaroKer said:**
> 1. What type of boot failure are you experiencing?  I am getting a flashing text cursor on a black screen.

2. How does one go about rebuilding initramfs?  What does that do?

3. What could I do to begin troubleshooting or diagnose a failed boot?

Logan

1. in boot options there's 2 things to disable (can't quite remember their names but acpi lacpi or something like that).

---

### Post by arsenix on 2009-11-23
I tested scorched3d under windows and it plays fine, well over 30fps.  It runs an order of magnitude slower under ubuntu.  Are people having better luck with certain nvidia driver versions on these machines?  I'm using the 185 version that is default under karmic.


James

---

### Post by rjackson1969 on 2009-11-24
Thanks for letting me run you guys around for assistance... turns out it was an I-d-10-T error. I was writing the image to a thumb drive but the thumb drive was 16gigs... I hadn't done enough reading to know that I needed to partition it down to 2gigs or less to burn the image to on the thumb drive. It ended up misfiring my installs even if I got it up and running it ran very badly.

Again sorry for the run-around.

---

### Post by harrisdg on 2009-11-25
I was having similar problems when trying to install 9.10.  The initial boot menu would appear, but would only lead to a blank screen with a blinking cursor no matter what option was chosen.  Installing 9.04 instead worked fine, then upgrading the graphics driver, the 9.04 updates, and upgrading to Karmic and everything seems to be working flawlessly.  Wifi, sound, video, suspend, it all looks great.  

Two quick questions though: 

This machine is replacing an HP mini 1110NR which had a button above the touchpad to disable it.  Does anyone know of an equivalent way to achieve the same thing on this machine with 9.10?  

Secondly, is there an easy way to switch to the classic desktop?  The NBR is great for small screens, but I think the 311 has enough screen real estate to warrant at least trying the classic desktop.  

Thanks!

---

### Post by tdunk on 2009-11-25
Hi

I just installed NVidia ION support for my Asus Eee Top 2002T and it work perfectly.

This is how to do it (32-bit):

Download [http://www.nvidia.com/object/linux_display_ia32_190.42.html](http://www.nvidia.com/object/linux_display_ia32_190.42.html)

Save the file and go to a terminal and cd to the directory where you saved the downloaded file. Then do:

```
sh ./NVIDIA-Linux-x86-190.42-pkg1.run
```

then reboot: sudo reboot

Hope it helps!

Rgds

---

### Post by demonfoo on 2009-11-25
> **tdunk said:**
> Hi

I just installed NVidia ION support for my Asus Eee Top 2002T and it work perfectly

I think that on Ubuntu, you're better off using the 190.42 packages that are part of the vdpau PPA I mentioned earlier in this thread. I've been using them on my Mini 311 with great success, though I never had problems with the 185.xx driver packages either.

---

### Post by demonfoo on 2009-11-25
> **arsenix said:**
> What 3D apps have folks successfully run on the machine?  I bought it for my young son and have been installing some of his favorite opensource games.  So far I have not had much luck with 3D apps.

  I installed tux racer extreme and scorched3d... both are completely unplayable.  They both run <5fps.  I did install armegetron and it runs great, but its 3d graphics are fairly simple.

  Have others had similar experiences?  I'm running Karmic 32 bit, nvidia 185 driver.  My machine has 1GB of ram (maybe this needs to be bumped up).

James

Are you *sure* you were using hardware GL support? If you ran:

```
glxinfo | grep '^direct rendering:'
```

what do you get? You might need to add yourself to the "video" group for hardware GL support to function (the devices don't get ACLs added to them for console users, for some reason). I've run several Linux and Windows 3D games on Ubuntu, with both the 185.xx and 190.42 drivers (Telltale Games titles, American McGee's Alice, Quake 3, Unreal Tournament, Heavy Gear 2, ...) with no problems, so I can say that hardware 3D definitely works.

---

### Post by jatinps on 2009-11-27
is anyone here having problems with sound over hdmi - i have a panny plasma and there is a strange buzzing sound coming over the hdmi audio.

Also i am unable to get a meaningful resolution to work with hdmi display - what settings do people here work with - twinview, separate x, etc?

---

### Post by demonfoo on 2009-12-02
> **jatinps said:**
> is anyone here having problems with sound over hdmi - i have a panny plasma and there is a strange buzzing sound coming over the hdmi audio.

I thought I had a problem like that, but it turned out it was specific to the content I was playing, not the hardware.

> **jatinps said:**
>  Also i am unable to get a meaningful resolution to work with hdmi display - what settings do people here work with - twinview, separate x, etc?

You need to use TwinView for it to work like you expect. With my rig, I have the typical HDTV resolutions available (1920x1080, 1280x720), along with a few others I believe (it's not hooked up right now).

---

### Post by sherbey on 2009-12-03
I'm thinking of purchasing a compaq 311c, in the UK the only version on offer is the 311c-1010SA which is allegedly limited to 1GB of RAM. Has anyone actually got one of these and if so can you confirm that there is a spare (SO)DIMM slot?
 
Has the latest realeases of Karmic fixed the wifi issues or have I got some fiddling to do to get it to work? (1010SA has b/g not n wifi).
 
Nvidia have confirmed that the ION-le works with VDPAU, I'm just concerned that if the 1GB limit is real that VDPAU will choke on 1080i content from my mythtv box - which would be the main reason for getting this little beauty in the first place :p
 
I've got a acer aspire revo which uses the same chipset (well, a non-le ION); getting audio over HDMI required some fiddling and I still get no audio when playing flash videos. Apart from that it's absolutely fantastic, can't fault it for a £150 purchase

---

### Post by demonfoo on 2009-12-03
> **sherbey said:**
> I'm thinking of purchasing a compaq 311c, in the UK the only version on offer is the 311c-1010SA which is allegedly limited to 1GB of RAM. Has anyone actually got one of these and if so can you confirm that there is a spare (SO)DIMM slot?

The HP Mini 311 (which to my understanding is the same as the Compaq version, just different branding) has 1 GB soldered onto the board, along with the SO-DIMM slot (and I've got a 2 GB SO-DIMM in mine, so it's up to a full 3 GB).
 
> **sherbey said:**
> Nvidia have confirmed that the ION-le works with VDPAU

And I can tell you from direct experience that it does as well. :)

> **sherbey said:**
> I'm just concerned that if the 1GB limit is real that VDPAU will choke on 1080i content from my mythtv box

It won't. The default RAM allocation with 1 GB of RAM is somewhere north of 100 MB, so 1080i/p HD decoding should work just fine.

> **sherbey said:**
>  I've got a acer aspire revo which uses the same chipset (well, a non-le ION)

ION and ION LE are *exactly* the same silicon; the only difference (literally) is a different PCI product ID in ROM, and different code in the drivers that keys on the different product ID to disable DX10 functionality. That's all.

> **sherbey said:**
> getting audio over HDMI required some fiddling and I still get no audio when playing flash videos

I've not had any problem with going into the Sound preference panel and switching to the HDMI output method. For digital output with ALSA, I selected the ALSA driver and entered 'hdmi' as the output device, and selected "AC3/DTS pass-through S/PDIF" for "Audio codec family" (in gmplayer).

---

### Post by Paerez on 2009-12-04
Hey guys, just tossing in my experience:

I was able to install 9.10 off a USB stick. BUT I had to make the usb stick from another ubuntu machine (generate usb boot disk). Unetbootin did not work for me.

I had to boot the installer with the "noapic nolapic" options, and I had to remove the "quiet" and "splash" options.

Then, on my first boot, I had to do those options again (add noapic nolapic, remove quiet splash).

Then, I updated via ethernet. When I rebooted to the new kernel, I could use the standard boot options.

Next, I installed dkms and then nvidia's 195 beta drivers direct from their site. DKMS will keep it up to date with my kernel (thanks dell!).

Next, I opened the hardware drivers and activated the broadcom STA driver. Then I had to add "wl" to the end of /etc/modules so it would probe the wireless at boot.

Then I grabbed flash 10.1 beta from adobe's site and popped it into my ~/.mozilla/plugins directory. But it seems that GPU accel is not available for linux yet.

Webcam works with "cheese" out of the box. I don't use skype so I dunno. Haven't tested various video-outs.

---

### Post by JoeMac42 on 2009-12-04
> **sherbey said:**
> I'm thinking of purchasing a compaq 311c, in the UK the only version on offer is the 311c-1010SA which is allegedly limited to 1GB of RAM. Has anyone actually got one of these and if so can you confirm that there is a spare (SO)DIMM slot?

I'm running 3GB in my mini 311 right now.  There is a 1 GB SODIMM soldered to the board and an empty slot for additional RAM.  I installed a 1066MHz 2GB Kingston PC3-8500 SODIMM (P/N KVR1066D3S7/2G) sourced from Newegg.com. Compiz is much happier with the additional RAM to share for graphics.

Joe

---

### Post by smurfgod on 2010-01-11
I got the one from Verizon and mine has 2 gigs of ram. I finally made the switch from Windows to Ubuntu after finding out I could use my phone(Samsung Omnia i910) as a modem without paying for the tethering feature from Verizon.

I did have some trouble with getting Wi-Fi to work but it's working know but I do need my webcam to work. Any help guys??

In my Xorg settings it says I'm using 512 megs of ram..is there a way to drop it down??Or boost it up for that matter??lol

~SMurf

---

### Post by DirtDawg on 2010-01-19
> **Paerez said:**
> Hey guys, just tossing in my experience:

I was able to install 9.10 off a USB stick. BUT I had to make the usb stick from another ubuntu machine (generate usb boot disk). Unetbootin did not work for me.

I had to boot the installer with the "noapic nolapic" options, and I had to remove the "quiet" and "splash" options.

Then, on my first boot, I had to do those options again (add noapic nolapic, remove quiet splash).

Then, I updated via ethernet. When I rebooted to the new kernel, I could use the standard boot options.

Next, I installed dkms and then nvidia's 195 beta drivers direct from their site. DKMS will keep it up to date with my kernel (thanks dell!).

Next, I opened the hardware drivers and activated the broadcom STA driver. Then I had to add "wl" to the end of /etc/modules so it would probe the wireless at boot.

Then I grabbed flash 10.1 beta from adobe's site and popped it into my ~/.mozilla/plugins directory. But it seems that GPU accel is not available for linux yet.

Webcam works with "cheese" out of the box. I don't use skype so I dunno. Haven't tested various video-outs.

Hey, thanks! I couldn't get usb to boot up. Would have not guessed Unetbootin was the problem. Wireless and driver info was spot on as well. Thanks for the helpful post.

---

### Post by hubbub on 2010-01-23
Thanks for the tip.  I was getting the blinking cursor on boot, until I pressed F6 and selected noapic and nolapic.  Installing okay now.

---

### Post by 3ktl on 2010-02-05
Hey I had the same problem. The solution is to install Ubuntu 9.04 then upgrade to 9.10. Works perfectly on my Mini 311-1000NR. Good Luck

---

### Post by airtonix on 2010-02-06
One thing that might not be obvious to less observant owners of a hp mini 311 is that they come in at least twenty different versions. (if not more)

This in itself is not the crazy part, but rather that many problems user A reports might not affect user B (since they don't actually have the same hardware related to the problem).

The chap above me cites problems installing ubuntu 9.10 on a 1000nr.

I also had initial problems installing ubuntu 9.10 however I manipulated the boot parameters as mentioned in some of the previous posts here (add noapic and nolapic, removing quiet and splash).

Others report problems that I do not have.

Point is that not all hp mini 311 are created equal... might be a good idea for anyone providing (omg it werks) statements to also provide the model number.

for the record my hp mini 311 is a 1018tu.

----

Another interesting thing to get working would be sensor readout... having that stuff in conky would be handy

---

### Post by rvugts on 2010-02-15
I have added an extra GB of RAM a few weeks ago, to bring the total to 2GB and have not had issues anymore with hibernate sometimes failing.

---

### Post by CDR Services on 2010-02-16
There is a C4 State in the bios enable\Disable....leave it off!

---

### Post by hfzorman on 2010-05-15
I would like to buy one of those HP Mini 311 but I haven't found a site that says how Ubuntu 10.04 works with it. Have any of you been using Lucid Lynx with these laptops? If you do, then, is graphics performance good? Any Wifi problems? Thanks.

---

### Post by faviobarrio on 2010-05-20
> **hfzorman said:**
> I would like to buy one of those HP Mini 311 but I haven't found a site that says how Ubuntu 10.04 works with it. Have any of you been using Lucid Lynx with these laptops? If you do, then, is graphics performance good? Any Wifi problems? Thanks.

Mine works fine except for the scrolling on the trackpad, a disappearing mobile broadband connection and HDMI output. EVERYTHING else has been without issue. 

My model is the HP Mini 311-1037NR. It has the full Ion and it runs Windows 7. I maxed the RAM to 3GB and upgraded the drive to 500GB 7200 RPM and I dual boot 10.4.

---

### Post by Xmister on 2010-05-23
For me, everything works out of the box, except wifi, and plymouth.
For wifi I had to install the proprietary broadcom driver the hardware drivers tool, plymouth is a bit complicated.
After that I've installed proprietary NVIDIA drivers, so HDMI and VDPAU works too.

I'm using Kubuntu 10.04 and WinXP dual-booting on it.
Two things I'm not happy with:
1. The battery life is less than in XP.
2. The HD movies not as good with VDPAU, as on XP with CUDA. (Slower a bit, and not as clear)

---

### Post by JoeMac42 on 2010-07-11
I have a Mini 311.  I added a SoDIMM to bring it up to 3 GB of RAM (which made a huge difference with Compiz) and I have it set up to dual-boot Ubuntu 10.04 and Windows XP.  I haven't booted XP since last November and I was only keeping it to run Adobe Acrobat Pro for occaisional PDF editing on the road.  Once I found that I could do Acrobat Pro 5.0 via WINE under Ubuntu and that Lotus Notes had a .deb install that could be tweeked to work under Ubuntu, I lost any reason to keep XP around and I will likely reclaim that space on my HD in the near future.  I use the netbook primarily for business travel and as my primary "computer at hand" that I keep in my backpack when I'm not home or at the office.

As for the trackpad, there was a bug report filed on the Alps Glidepoint trackpad in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625") that Chase Douglas has been working on.  Edge scrolling worked for me in Ubuntu 9.04 only because the Synaptics driver didn't recognize the trackpad and it wound working with the default PS/2 driver.  None of the Synaptics preferences were available and Synaptics did not recognize the trackpad.  When the kernel was recompiled for Lucid, Synaptics was "turned on" for the Alps Glidepoint in the Mini 311 and other netbooks/notebooks somewhere around kernel version 2.6.32-19, but then edge scrolling disappeared and none of the advanced configuration features in Synaptics worked on these trackpads.  So, somewhere around the Ubuntu 10.04 2.6.32-22 or 2.6.32.23 kernel version, this was reversed, edge scrolling returned and the more advaced configuration features of Synaptics are turned off for now.  This should get solved eventually since this is a fairly common trackpad and we do need it recognized in Synaptics so that the preferences for the trackpad can be configured by the end user, particularly turning off pad-clicks when typing.

I have never tried an HD movie since I don't have a Blureray drive.  I have tried 720p from DVDs via HDMI to a 24" LCD monitor  and to a 42" LCD TV in Ubuntu 9.10 and 10.04 and I can't tell any difference between Windows and Ubuntu.  I think it is just wicked that when I'm on business travel I can bring an HDMI cable and send a movie to a huge screen in a hotel room from something this small.  Ion just rocks and nVidia has provided decent support for Linux for Ion although the allowable options for running dual monitors in nVidia Xserver Settings could use a bit of work.

---

### Post by HD2 Lucid Lynx on 2010-07-30
> **demonfoo said:**
> Everything works 100%. Bluetooth (paired with my BlackBerry 8830), WiFi (after messing with the drivers, the only thing I had trouble with), keyboard, touchpad, all USB ports, card slot (tried with SD and MS/MSPro), HDMI (including audio out), 3D graphics (tried with several Telltale Games titles via Wine), suspend, webcam (works perfectly with the Linux version of Skype). It almost completely worked out of the box, and the WiFi issue appears to be a known thing with karmic.  

I also have the N280 but I'm running 10.04 Lucid, everything is running smooth as silk, I'm just pulling my hair out trying to get my HDMI to work. After re :Dading your quote I was wondering if you could tell me how to get the HDMI up and running I would greatly appreciate it !

---

### Post by HD2 Lucid Lynx on 2010-07-30
> **hfzorman said:**
> I would like to buy one of those HP Mini 311 but I haven't found a site that says how Ubuntu 10.04 works with it. Have any of you been using Lucid Lynx with these laptops? If you do, then, is graphics performance good? Any Wifi problems? Thanks.

Day of purchase of my 311 I got rid of factory Windows 7 and Installed Lucid Lynx immediately everything works amazing no kinks except for my HDMI port which I know someone knows how to work out. Graphics are amazing no wifi problems all the little nooks and crannies also work. I got my 311 for 390.00 on a wicked deal best money I ever spent, dont even use my Mac anymore.

---

### Post by katrinaaa on 2010-07-30
It's a special topic for me , I get much useful information from it .thanks very much !

---

