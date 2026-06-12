---
title: "Ubuntu on a Toshiba Qosmio X505-Q887"
date: 2010-10-11
forum: Hardware
---

### Post by ImZelkova on 2010-10-11
Hello,
I have attempted to run both 10.04 and 10.10 Beta and 10.10 RC on my laptop, only to have this... error occur.

[IMG]http://imgur.com/8czun.jpg[/IMG]

Ive tried installing, and ive tried running from USB and both end up giving me this screen after the loading bars. Does anyone know what this might mean? I think it might have to do with my video card. (NVIDIA® GeForce® GTS 360M)

Heres a link to its other specs.
[http://us.toshiba.com/computers/laptops/qosmio/X500/X505-Q887](http://us.toshiba.com/computers/laptops/qosmio/X500/X505-Q887)

---

### Post by snafu006 on 2010-10-11
First can you run from a live CD ok ?

---

### Post by SkylinesSuck on 2010-10-12
I get the exact same thing on an x505-875.  I've tried booting off both the 32bit and 64bit cd's.  It'll hit the CD drive for a good long while, show the black "ubuntu" screen with the little dots blinking beneath it, then the maze of death eventually appears.  I think it's some kind of video driver issue.  If I hit the power button, it'll think, then spit back out the cd.  I hit any button, and it shuts down.

---

### Post by SkylinesSuck on 2010-10-12
O yeah, and mine works pretty good with 10.4 32 bit.  It's only when I try running the 10.10 versions of the CD I get this.

---

### Post by snafu006 on 2010-10-12
Ok lets see where did you download from a torrent or from the main download. Are you usig a CD or USB if you are using a CD you might have burned the CD to fast and it has errors. If you got it from a torrent the checksum(data) might have got all messed up.

  So i would try downloading from the main site and if you have a usb drive try that if you dont have and usb drives only cds burn them at a slower speed like 10 or lower see if that works.

---

### Post by SkylinesSuck on 2010-10-12
I downloaded both images from the main site.

---

### Post by snafu006 on 2010-10-12
OK so when your computer starts up you can see the bios load up right? as you do HIT F12 to bring up the Boot screen put in the CD or USB and select the usb or cd. you should see and purple screen come up. if no all so try pulling out the battery and hold the power button for 30sec to reset the bios.

---

### Post by amartz on 2010-10-12
You can assume he has covered the basics. The Qosmio is not the only one having video problems. I have two Acers, an Aspire One netbook, and an Aspire 7745 laptop (I7 cpu). The netbook boots perfectly off the live CD. The laptop has a 50/50 chance of whether it will boot properly, or display it's version of the maze screen posted here. When it works, the first thing it wants is to install proprietary drivers for both the Broadcom wireless, and the ATI graphics card. An update also wants to install a new linux kernel.

---

### Post by vexeel on 2010-10-12
Same problem here...

 [ATTACH]172097[/ATTACH]

I have a Toshiba Qosmio X505-Q888 and I get those weird mazes when I try to install Ubuntu 10.10 Desktop Edition (64 bit) from both a LiveCD or from a USB stick. I tried

```
sudo dpkg-reconfigure xserver-xorg

```as suggested in [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/654178), but it was no good.

---

### Post by ImZelkova on 2010-10-13
At least I am not the only one with this problem.

---

### Post by SkylinesSuck on 2010-10-13
Interesting so many people are having this problem and across different platforms.  Is there any way to report this as an official bug or something?

O, BTW vexeel, what kind of computer do you have?

---

### Post by vexeel on 2010-10-13
It's a Toshiba Qosmio X505-Q888. A friend of mine has the same model and he also has the same problem. This is very disappointing... I cannot even reach the installation menu. I'm not sure if resetting the BIOS will solve the problem (probably not). The weird thing is that I didn't have this problem with 10.04.

---

### Post by chaz572 on 2010-10-20
Confirmed again.  I just got a Toshiba Qosmio X505-Q890, and tried to boot the Ubuntu 10.10 64-bit desktop live CD.  Got the exact same thing.  Tried booting it three times, full power-offs in-between.  Same result all three times.  :(  I'm going to assert that if there's this many of us who are getting the same result on various incarnations of the Qosmio, it's unlikely to be corruption of the CD image we downloaded/burned.  This is smelling more and more like a real driver bug.

Looks like I'm falling back to 10.04.  Thanks to those who report that that's working -- at least I know I've got a viable workaround.

---

### Post by doogieanese on 2010-10-22
just a thought, with a persistant live usb, one could download comile and install the latest, or any revision for that matter, nvidia proprietary driver. thats what i've been running on my x505-Q830 for awhile now, albeit in 10.04.
anyway just a thought for a work around. not like compiles take long with these i7's

---

### Post by Lefaid on 2010-10-30
Yeah I think it is the video card.  I have the same video card in my Asus and ran into the same problem when I tried to install 10.10 on my laptop.  Hopefully they will fix it soon.

---

### Post by vdubhack on 2010-11-03
For a basic install on the x505 is as follows: I have one just FYI

1. boot computer with livecd 
2. when you see it get to the actual booting hit f6
3. select language
4. hit f6 again
5. select nomodeset
6. hit esc
7. install Ubuntu as usual and reboot
8. when you get to the grub boot menu make sure to hit e so you can edit the kernel commands
9. add nomodeset to the kernel args again
10. cntrl X to boot
11. sudo apt-get update && sudo apt-get upgrade
12. reboot
13. Repeat 8-10 again
14. start the restricted drivers program
15. install the restricted driver for the 360m
16. reboot
17. Enjoy Ubuntu

Here is what I have noticed so far, WIFI is crap! it will cause random complete lock ups of your system if you use hyperthreading and big amounts of CPU and Memory :) I have confirmed its that driver alone causing it. Even installing the drivers from realtek will cause the same issues ( I even have a few different pre-release versions from their tech support same results). There are acpi issues some things still are not being detected properly. WATCH THE HEAT! You will eventually find you need to install some PPA's to run more cutting edge versions of things like nvidia and what not. Also the mic sorta works. Oh make sure you edit your sources to include proposed updates as well. Read your logs 

Hope this helps someone and report your bugs. Turn on bug reporting and report stuff, help get support for the x505! I have started a few bug reports already and will be doing some testing with Natty once they have RC1 ready to go.

I will try and check the thread but I just happened across this in a search for something else relating to the laptop :) 
I am on 10.10 64bit with kernel .35-23 NVIDIA 260.19.12


Edit: Oct. 2011
I no longer notice anything requiring a work around except to get the install disk to boot with nomodeset, everything else works for me and on 11.10 with testing repos enabled the kernel is down to very few issues NON of which are a hindrance to the usage of the laptop in anyway.

---

### Post by vdubhack on 2010-11-04
Here are some of the bug reports I have started or joined in on in case you run into the same problems. I have not posted all the issues as of yet still. 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668148](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668148) -- for some of the main ACPI issues so far
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660088](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660088)  -- this will show you the work around to get your sd card reader working properly. If not post here and I will post the steps to do it. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578125](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/578125) -- for the non working microphone 
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/500377)
[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/567016](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/567016) -- one of the many for the wireless issues. 

I think thats it so far.

---

### Post by drdanielfc on 2010-12-01
Same laptop :-)

Boot up and edit your boot arguments. Replace "quiet splash" with "nomodeset" and install. Do the same thing on first boot. Install your nvidia drivers and it should work fine. I'm using mint 10. Ubuntu gave me some issues with theming. SO did mint, but mint works a little better.

---

### Post by vdubhack on 2010-12-01
replacing quiet and splash is not required, just adding nomodeset is enough. What I posted is the bare min you need to do for ubuntu and the easiest way. 

Though I gave up on Ubuntu as their support is just getting absolutely horrid!!!!!!!


Everything but one thing worked out the box with fedora and its a linux wide issue of the pci=no_crs message in dmesg. Fedora even works out of the box with linux graphics drivers. Ubuntu's dev release isnt even that far yet.

---

### Post by drdanielfc on 2010-12-02
> **vdubhack said:**
> replacing quiet and splash is not required, just adding nomodeset is enough. What I posted is the bare min you need to do for ubuntu and the easiest way. 

Though I gave up on Ubuntu as their support is just getting absolutely horrid!!!!!!!


Everything but one thing worked out the box with fedora and its a linux wide issue of the pci=no_crs message in dmesg. Fedora even works out of the box with linux graphics drivers. Ubuntu's dev release isnt even that far yet.

oh wow im sorry i didn't realize that you'd already posted the nomodeset part higher up (stupid me :( ).

I gave up on ubuntu for quite a while (tried Sabayon and o/s) but ended up coming back to mint. Seems to be a bit further along then ubuntu even though its similar.

Edit: do you think you could post the directions for getting sd card reader to work?

---

### Post by zambizzi on 2010-12-18
Is there a workaround for this yet?  I just picked up a Qosmio X505-Q890 and I'd really like to get Ubuntu on it!

---

### Post by SkylinesSuck on 2010-12-26
> **zambizzi said:**
> Is there a workaround for this yet?  I just  picked up a Qosmio X505-Q890 and I'd really like to get Ubuntu on  it!


> **vdubhack said:**
> For a basic install on the x505 is as follows: I have one just FYI

1. boot computer with livecd 
2. when you see it get to the actual booting hit f6
3. select language
4. hit f6 again
5. select nomodeset
6. hit esc
7. install Ubuntu as usual and reboot
8. when you get to the grub boot menu make sure to hit e so you can edit the kernel commands
9. add nomodeset to the kernel args again
10. cntrl X to boot
11. sudo apt-get update && sudo apt-get upgrade
12. reboot
13. Repeat 8-10 again
14. start the restricted drivers program
15. install the restricted driver for the 360m
16. reboot
17. Enjoy Ubuntu



I think I've seen a couple of people running 10.10 on x505's now using the "nomodeset" install.  Unfortunately I'm too newb'ish to understand all of what he posted up and I'm lost after step 8    :(

---

### Post by jadonchristensen on 2011-01-10
Another easy way to install it is to use the Alternate CD. When the installation is done and you get to the grub menu below, select the "recovery mode" option. Then select failsafeX. This should put you in low graphics mode.

Ubuntu, with Linux 2.6.X-generic (recovery mode)

Then just login to Ubuntu and install the Nvidia drivers.
(note: you need to setup your network first to get online)
System > Administration > Additional Drivers

I own the Toshiba Qosmio X505-Q860

I hope this helps.

---

### Post by SkylinesSuck on 2011-01-10
> **jadonchristensen said:**
> Another easy way to install it is to use the Alternate CD. When the installation is done and you get to the grub menu below, select the "recovery mode" option. Then select failsafeX. This should put you in low graphics mode.

Ubuntu, with Linux 2.6.X-generic (recovery mode)

Then just login to Ubuntu and install the Nvidia drivers.
(note: you need to setup your network first to get online)
System > Administration > Additional Drivers

I own the Toshiba Qosmio X505-Q860

I hope this helps.

Posting to you from 10.10 on my X505-875.  Thanks :P

Unfortunatly my microphone that I tried so hard to get working doesn't work again :(  O well, on to try and see what version of alsa I've got and probably recompile that bugger.

---

### Post by jadonchristensen on 2011-01-10
Have any of you gotten the HDMI audio to work on it, if so, please tell us how.

Thank you

---

### Post by SkylinesSuck on 2011-01-10
I had it working under 10.4 by updating alsa to something something something .23 from .21.  Also I updated to the latest realtek drivers.  I can't remember which one did it.  It seems to me it was still funny though--like it would play some sounds over hdmi but not others.  I haven't tested it yet in 10.10, but I'm assuming from your comments it's not going to work.  My mic doesn't work again, but I checked and I do have the latest version of alsa which loaded with 10.10 right off the bat, unlike 10.4.

---

### Post by HalfEmptyHero on 2011-01-11
> **jadonchristensen said:**
> Have any of you gotten the HDMI audio to work on it, if so, please tell us how.

Thank you
I have hdmi audio working, but it was a pain in the but to get. After failing to get it working under Maverick, I downgraded to lucid, compiled the drivers, and then upgraded to maverick. HDMI audio works perfectly now, except for flash, but that's not a big deal to me.

I am still unable to get my mic to work. lidex has been trying to help me get it working, but nothing as of yet. You can follow the progress here: [_http://ubuntuforums.org/showthread.php?t=1564676&page=3&highlight=qosmio_]("http://ubuntuforums.org/showthread.php?t=1564676&page=3&highlight=qosmio")[]("http://ubuntuforums.org/showthread.php?t=1441565&page=2&highlight=qosmio") and hopefully we'll get it working some day.

> 
Unfortunatly my microphone that I tried so hard to get working doesn't work again :sad:  O well, on to try and see what version of alsa I've got and probably recompile that bugger.     I tried many times to compile the alsa drivers on Maverick, and could not succeed. Errors kept popping up. That's why I went back to Lucid and did an upgrade.

---

### Post by quantumtransfer on 2011-02-02
so, the hdmi sound works fine if you install lucid and upgrade? also the post #16 didn't work for me.. trying the alt. installation method.

---

### Post by Adonn on 2011-07-15
Sorry to bump an old thread, but I figured it would be dumb to start a new one...
I have a Qosmio X505-Q887, and have a problem when loading Ubuntu 11.04 ....
It shows the same screen issue as mentioned before me, with the maze of death. I tried the F6 key, but it keeps loading as if it were just a verbose boot sequence.

I dont know much about how to fix this, so any help would be greatly appreciated.

Also, I am trying to install this using a USB stick, as I dont have a way to burn a CD or anything at the moment.

Thanks,
Adonn

---

### Post by jadonchristensen on 2011-07-16
> **Adonn said:**
> Sorry to bump an old thread, but I figured it would be dumb to start a new one...
I have a Qosmio X505-Q887, and have a problem when loading Ubuntu 11.04 ....
It shows the same screen issue as mentioned before me, with the maze of death. I tried the F6 key, but it keeps loading as if it were just a verbose boot sequence.

I dont know much about how to fix this, so any help would be greatly appreciated.

Also, I am trying to install this using a USB stick, as I dont have a way to burn a CD or anything at the moment.

Thanks,
Adonn

1. Use the "Alternate install CD" at the bottom of this page.
[http://ubuntu-releases.cs.umn.edu/11.04/](http://ubuntu-releases.cs.umn.edu/11.04/)

2. After installation is complete and it reboots to the Grub menu, select Recovery mode.

3. In Recovery Mode, choose failsafe graphics.

4. Login to Ubuntu, setup Networking, update, etc.

5. Install Nvidia driver from System > Administration > Additional Drivers

---

### Post by QueSeYo on 2011-11-09
Same story with the latest release.

Guys, do not expect to take control of the desktop without doing the homework first.

That is why MS is upfront.

Sorry to say this but it is the true factual thing.

Business cannot afford men hours and extra payments for things that do not work.

I am back to WIN 7 and even I run MAC OSX Lion from the USB !!!!!

---

### Post by vdubhack on 2011-11-09
> **QueSeYo said:**
> Same story with the latest release.

Guys, do not expect to take control of the desktop without doing the homework first.

That is why MS is upfront.

Sorry to say this but it is the true factual thing.

Business cannot afford men hours and extra payments for things that do not work.

I am back to WIN 7 and even I run MAC OSX Lion from the USB !!!!!

  What in the hell does your response have to do with this thread?? Leave propaganda out of help threads.      

I have already posted how to boot from the install disk in this thread and it works perfectly. All versions of Ubuntu run on this laptop, fedora releases since 14 actually booth into the install DVD with no issues and can actually use the stock video drivers. The most current 3.0 kernel update from Ubuntu Testing solves even more Kernel issues leaving it to just a couple, non of which hinder use in any way. 

How cool you can run a version of Unix on a USB stick, its been done for awhile now as well as booting in a VM and running on non OSX hardware. Stick to the hackintosh and windows forums if you do not want to actually share help in the related subject.

---

### Post by drdanielfc on 2011-11-09
> **QueSeYo said:**
> Same story with the latest release.

Guys, do not expect to take control of the desktop without doing the homework first.

That is why MS is upfront.

Sorry to say this but it is the true factual thing.

Business cannot afford men hours and extra payments for things that do not work.

I am back to WIN 7 and even I run MAC OSX Lion from the USB !!!!!

Just so that new folks to Linux are not turned off when they see this posts, I would like to point out a few things:

1. After the NOMODESET for the install and 1st run, things run flawlessly. I stream 20GB blueray movies over wifi and play them at 1080p on my home tv. Not bad for an extra 15 minutes of research.

2. HDMI audio out works fine for me. Just go to the sound settings and change the output device. Flash works fine as well. I had no need to use extra drivers.

3. Headphones, *external* mic, webcam, and media keys work flawlessly. The internal mic does not work. Yes, this is sad, but certainly not the end of the world.

4. Windows works considerably worse out of the box. The difference is that companies make drivers for Windows, not Linux. Otherwise, I feel Linux is absolutely superior in all aspects.

And a quick question: How much did you pay for that setup? And, is it legal?

---

### Post by vdubhack on 2011-11-09
> **drdanielfc said:**
> The internal mic does not work. Yes, this is sad, but certainly not the end of the world.



What errors do you get for that? I actually have no issues using the internal mic and I have not done any tweaks to get it to work.

---

### Post by LinuxFan999 on 2011-11-09
> **vdubhack said:**
> What in the hell does your response have to do with this thread?? Leave propaganda out of help threads.      

I have already posted how to boot from the install disk in this thread and it works perfectly. All versions of Ubuntu run on this laptop, fedora releases since 14 actually booth into the install DVD with no issues and can actually use the stock video drivers. The most current 3.0 kernel update from Ubuntu Testing solves even more Kernel issues leaving it to just a couple, non of which hinder use in any way. 

How cool you can run a **version of Unix** on a USB stick, its been done for awhile now as well as booting in a VM and running on non OSX hardware. Stick to the hackintosh and windows forums if you do not want to actually share help in the related subject.
Mac OSX actually is not Unix, but is actually based on the Mach microkernel and FreeBSD.
I do think that it is cool to run OSX on non Apple hardware though.

---

### Post by drdanielfc on 2011-11-09
> **LinuxFan999 said:**
> Mac OSX actually is not Unix, but is actually based on the Mach microkernel and FreeBSD.
I do think that it is cool to run OSX on non Apple hardware though.

"Mac OS X .. is a series of Unix-based operating systems]
"http://en.wikipedia.org/wiki/Mac_OS_X"

---

### Post by drdanielfc on 2011-11-09
> **vdubhack said:**
> What errors do you get for that? I actually have no issues using the internal mic and I have not done any tweaks to get it to work.

I have no errors...I just do not get any input from it. Once in a while, though, it will just work for a little while (until reboot?). It's quite strange. I really do not feel like mucking around with ALSA though, especially since I have a small external mic that works fine. Theres also a possibility it is simply a hardware problem. My screen has been flickering alot lately so I need to get the connections fixed on that. The mic is on the screen so I suppose that's a possibility.

---

### Post by LinuxFan999 on 2011-11-09
> **drdanielfc said:**
> "Mac OS X .. is a series of Unix-based operating systems]
"http://en.wikipedia.org/wiki/Mac_OS_X"
Wikipedia is not 100% accuate. If I had an account there, I would change it to "Unix like", since as I said before Mac OSX is not Unix. It is "Unix like"' like Linux and BSD are. The only Unix OSes available today are Solaris and HP-UX. Those are Unix, Mac OSX is not. That same article says that the core of Mac OSX is Darwin, which is Mach+FreeBSD, and neither of those are Unix, so Mac OSX is not Unix. The is also an article about "Unix like" 
OSes, showing 3 types of Unix like Oses, genetic Unix, Trademark Unix, and functional Unix. If Mac OSX was a "genetic Unix", meaning that it is based off of origional code, we could say "Mac OSX is Unix", but it is a "Trademark Unix", which means that it is not based on original code, but meets the Single Unix Specification, which confirms again that Mac OSX is not Unix.

---

