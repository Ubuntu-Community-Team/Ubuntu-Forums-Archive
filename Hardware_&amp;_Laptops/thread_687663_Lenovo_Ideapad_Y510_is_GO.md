---
title: "Lenovo Ideapad Y510 is GO"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by wyth on 2008-02-04
A little while ago I was posting and asking about the Lenovo Y410 when it seemed like my old Gateway was about to bite it.

Leonovo/IBM has always been fairly Linux friendly, but one complaint with the Y410's was that the sound never worked. ([here]("http://ubuntuforums.org/showthread.php?t=611153&highlight=Y410"), [here]("http://ubuntuforums.org/showthread.php?t=511058&highlight=Y410"))

Yesterday my old Gateway bit it.  In between then and now, Lenovo released a new version of their Ideapad, the Y510, and lucky me, there were a couple of can't-miss rebates from Office Depot, and I snagged the machine.

About the first thing I did was wipe off the Vista partition, and with a live Ubuntu CD, I'm resizing/partitioning the 250 GB drive.  At least on the live CD, I can happily say not only did the wireless connect to my WPA2 network flawlessly, but the sound works brilliantly.  The media controls built into the keyboard also work -- something I never had on my Gateway.  

It's a rugged machine with a rough, textured lid (it's scored to seem textured like fabric and make it less susceptible to scratching).  It comes with a 1.3 megapixel camera built into the 15.4 1280x800 WXGA screen, there's lots of USB 2.0 ports and a firewire port, a 1.6 Ghz dual core Intel processor, 2 GB DDR2 ram, and it's about 6 pounds.  Plenty for Linux.

I'll post some more when everything's installed.  I know Lenovo will start shipping machines with Suse pre-installed, so things should work fairly well out of the box.  There are quite a few features that were meant to work with Vista, like face recognition for security, but my university doesn't recommend or use Vista, I have no use for Vista, and when I first booted the machine, it was annoyingly slow.  Off it went.  

One minor complaint: I really like the keyboard -- great action on it -- but I find the touchpad's buttons a bit mushy.  I may look into that, but if that becomes the only issue with this computer, a travel mouse is no big deal.

---

### Post by ghandi69_ on 2008-02-04
Saawweeeeet!

---

### Post by mschap on 2008-02-04
I would love to hear as soon as possible how well this installs and works.  I would like to buy one of these tomorrow and do the same thing - install Ubuntu.

Thanks

Michael

---

### Post by wyth on 2008-02-05
I've set up about everything I need so far on the Y510, and so far I have no real complaints.  

The sound is working, although it's not rich; I understand there are some work-arounds, but I've not had time to look into them.  Headphones sound pretty good.

Also, compiz is blacklisted because the Intel gfx card breaks Xv video with compiz enabled.  There's a few work-arounds for this as well, but it should be fixed by October.  [This ThinkWiki page goes over the details]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_on_a_ThinkPad_R61"). 

I'm still getting used to the keyboard, but this is mainly due to having to hammer on my old keyboard -- it takes a bit to get used to the light touch required.  There is also no center scroll wheel for the touchpad, nor is there that little IBM nipple on the ThinkPads; but you can scroll alongside the touchpad just fine.

For the price, this is a pretty nice machine.  It's fairly light for a wide screen (again, I may be a bad judge because my previous laptop was a behemoth). I was planning on getting an ultra portable, but when my old one broke, I had to get something fast, and I think I got more than I hoped for.  This may change in a few weeks, but Lenovo has a reputation for building solid machines, so I'm not too worried.

---

### Post by staciedaisy on 2008-02-05
i just bought this machine an hour ago! the price was unbeatable for the product!! Just wondering if you had any luck with getting the camera working...i haven't messed with it yet just curious!

thanks!

---

### Post by wyth on 2008-02-07
I've not had any luck yet with the camera, although I just started researching it this morning.  It's recognized as a Lenovo Easy Camera with uvcvideo installed (according the [a message printout from here]("http://bbs.archlinux.org/viewtopic.php?pid=327347#p327347")).  

As for uvc, follow [this guide]("https://help.ubuntu.com/community/UVC?highlight=%28uvc%29").

I also got the multimedia functions across the top working by installing the latest alsa drivers, as according to [this page]("https://help.ubuntu.com/community/SoundTroubleshooting").

I still need to reboot and see if the camera is picked up, but I have a couple beagles itching to get out and enjoy some sun while it lasts.

---

### Post by militem on 2008-02-08
I am in the same boat.  I saw the OD deal and I bit.  The laptop is perfect for what I need.  I'm glad you were able to connect flawlessly from the live CD, but I unfortunately am still not able to connect.  It prompts me for my passphrase, I enter it, but it still does not connect.  Is anyone else having this problem?
BTW, this is my first install of linux.  What do I have to do to wipe vista?  Thanks

---

### Post by miggys on 2008-02-09
wyth, and anybody else using the lenovo y510, are you succesful with speaker/headphone situation? ie. when you plug in your headphones do your speakers turn off?  Further, would you consider your speakers loud enough under linux?  

thanks

---

### Post by jamesyp on 2008-02-10
I've got Gutsy 7.10 running on a two day old ideapad y510.  Sound was working right from installation, but I have the reported problem where headphones don't mute the internal speakers.  I've tried almost everything on [this page]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") (which is related to general problems with sound, not specifically the headphone problem).  I've done everything except compile a new kernel, which I don't really feel should be necessary.

I've found some workarounds for other laptops with the same intel sound chip,  Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03), but so far nothing has worked specifically for my Lenovo.

Any help with this will be deeply, deeply appreciated.

---

### Post by wyth on 2008-02-11
**For sound issues:**  I went through the process on [this page]("https://help.ubuntu.com/community/SoundTroubleshooting") -- not that big a deal -- and sound works great.  No headphone issues.

**Wireless:** This sounds maybe like an issue with the router itself rather than the connections.  What kind of security is on it (WEP, WPA1, WPA2?), and have you tried renaming the connection?  [This page]("https://wiki.ubuntu.com/?action=fullsearch&context=180&value=wireless&titlesearch=Titles") is a repository of Ubuntu wireless pages; look near the bottom for networking, router, and troubleshooting issues.

---

### Post by jamesyp on 2008-02-13
I removed, purged, and then reinstalled all the alsa drivers, and my headphones still don't mute the internal speakers, which pretty much ruins my laptop for use in libraries and whatnot.  At least if I'm listening to music, which is pretty much always.

I'm going to try changing kernel versions.  Been trying to avoid that.  If anybody can think of something that wasn't on that page I linked in my previous post, or what wyth just linked in the sound section of his recent post, I'd like to hear it.

---

### Post by wyth on 2008-02-13
The page I linked to ([here]("https://help.ubuntu.com/community/HdaIntelSoundHowto")) works without issue.  The only possible issue is you may have to compile the new drivers again with a kernel upgrade.

But I'm having glorious sound out of my machine, and no headphone issues besides my usb headset not being picked up (but I think that's a separate issue).

---

### Post by Linux Convert on 2008-02-14
WYTH - Thank you for all of your assistance thus far regarding this notebook.  I too purchased this notebook with the sole intentions to run linux on it.  However, as with everyone else on this thread,  I too am having problems with the webcam and issues with the audio.  I have followed both of your links directing me to the solutions for the audio, however, I still cannot solve the issue of the speakers NOT muting when inserting headphones. 

Additionly, you have claimed to have gotten the top multimedia buttons to work.  So have I thanks to the link you have provided.  My questions is - were you able to provied the correct functions for all of the multimedia buttons or just the basic stop/forward/backward/pause/play/and mute?  Those are the only buttons I have been able to map and add functions to.  

Last, WYTH, would you be able to provide in your own words or presentations on how you were able to resolve the audio issue?  As my name states, I m a recent Linux Convert and still very much overwhelmed by the amount of computer "mumbo jumbo" I do not know.  That and following the links you have provided just did not do it for me.  SInce you were able to fix the issue using the same computer.  I am seeking your assistance in this matter.  Thank You!

---

### Post by wyth on 2008-02-14
Okay, I'm just basically reposting what is already on [this Ubuntu help page]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), but maybe it'll make a difference.  As for the multimedia keys, I've only used the play-stop-ff-etc., and mute.  I didn't even try the rest; haven't had time to look into it.

First, you need to make sure you have the right stuff installed:
```
sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`
```Next get the latest ALSA drivers, and stow them away in some directory.[LIST]
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/")
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-lib]("ftp://ftp.alsa-project.org/pub/lib/")
[*] [[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/u-www.png[/IMG] alsa-utils]("ftp://ftp.alsa-project.org/pub/utils/")[/LIST]Next step is to create a directory for the files and copy the tar.bz2 files to that directory:

```
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2
```Next, compile and install:[LIST]
[*] Compile and install alsa-driver[/LIST]```
cd alsa-driver* 
sudo ./configure --with-cards=hda-intel 
sudo make 
sudo make install
```[LIST]
[*] Compile and install alsa-lib[/LIST]```
cd ../alsa-lib* 
sudo ./configure 
sudo make 
sudo make install
```[LIST]
[*] Compile and install alsa-utils[/LIST]```
cd ../alsa-utils* 
sudo ./configure 
sudo make 
sudo make install
```Next find out what sound card you're using:

```
cat /proc/asound/card0/codec#* | grep Codec
```The Y510 uses RealTek ALC888, so look for that.  

Next you can check the ALSA-Configuration for specifics on the sound card.  I couldn't find the file, but that may be because I had a kernel update.  The guide says the file is at 
```
/usr/src/KERNEL_VERSION/Documentation/sound/alsa/ALSA-Configuration.txt
```But I found it at 
```
/usr/src/alsa/alsa-driver-1.0.16/alsa-kernel/Documentation/ALSA-Configuration.txt
```I saw three options -- I'm not sure if one will work better than the other at this point.  The three options are:

&#8227; lenovo-101e    Lenovo 101E
&#8227; lenovo-nb0763    Lenovo NB0763
&#8227; lenovo-ms7195-dig Lenovo MS7195

Next to tell alsa-base what to do:
```
sudo nano /etc/modprobe.d/alsa-base
```at the end of that file, add:
```
options snd-hda-intel model=MODEL
```For model=MODEL, use one of the three options from above:[INDENT]&#8227; options snd-hda-intel model=lenovo-101e

OR

&#8227; options snd-hda-intel model=lenovo-nb0763

OR

&#8227; options snd-hda-intel model=lenovo-ms7195-dig

**EDIT: gomez_in_the_south [reports]("http://ubuntuforums.org/showpost.php?p=4427198&postcount=20") that the following worked:**
```
options snd-hda-intel model=lenovo-ms7195-dig
```
[/INDENT]Reboot and see if it's working.  I thought a kernel update may break it and require re-compiling.  This happened to a friend of mine running a 64 bit machine.  I had a kernel update today, and the sound is still working as it should.

---

### Post by Kilbasar on 2008-02-16
thank you wyth! you've saved me a lot of time and effort. i just installed Ubuntu on my shiny new Y510, and you've helped me work out some of the initial kinks. for anyone wanting to fix up audio, i strongly recommend reading the page wyth linked to. after following the basic directions (which wyth copied here), i rebooted, and had no sound. dmesg had errors about unknown symbols. if you run into this problem, the answer is on that page as well, although it doesn't have the actual commands you use, so here they are. this is assuming you configured/installed from /usr/src/alsa.

```
sudo su
cd /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/
mv snd-hda-intel.ko snd-hda-intel.ko.bak
ln -s /lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
cd /usr/src/alsa/alsa-driver-1.0.16rc2/modules
cp * /lib/modules/2.6.22-14-generic/kernel/sound/
depmod -a
```

and then reboot. also, by default, the volume for "Speaker" was all the way down, so I had to turn that up in the mixer before I had sound (double-click the volume tray icon)

---

### Post by BBHoss on 2008-02-18
I can confirm that downloading/compiling the newest alsa fixes the headphone problem.  However, I am still getting NO BASS from the subwoofer in the system.  Anyone have any ideas on how to remedy this.  This is one of the best features on this laptop, but it currently on works in Vi$ta!

---

### Post by wyth on 2008-02-18
I'm glad this is working out for people.  On the Lenovo pages, some people were asking about the multimedia keys along the top.  There's the play/pause/stop/etc. keys on the right that also switch over to a number of equalizer keys.  On the left, there's a mute, a "user define" utility, and a Dolby stereo key.

The play/pause/stop/etc. keys work, and the mute key works.  The equalizer keys do not work, and I believe this is because there isn't any standard equalizer in Gnome -- if there were, you could probably map the keys, if not automatically, then through Keytouch.  I haven't managed to get the Dolby thing to work -- not sure if it will or won't, and haven't had time to look into it  The "user define" utility must be for personal settings -- again, dependent on having an equalizer that isn't there in Gnome.

But the sound is generally fine on my machine, although no subwoofer.

---

### Post by Zetheroo on 2008-02-26
I'll be getting my IdeaPad Y510 very soon... 
I hope we can get everything working.... :KS

---

### Post by gomez_in_the_south on 2008-02-26
I had followed the instructions on the general Soundcard instructions page without success. Thanks wyth for the detailed instructions which solved my headphone/muting problem.

And yeah, getting the subwoofer to work would be great.

---

### Post by gomez_in_the_south on 2008-02-29
After a little searching and experimenting I managed to get the subwoofer to work. 

First, I followed the instructions in wyth's previous post and in the config file: 
```
sudo nano /etc/modprobe.d/alsa-base
```
I added this as the last line:
```
options snd-hda-intel model=lenovo-ms7195-dig
```
After a restart there is a new option in the volume control called LFE. This controls the volume for the subwoofer on my Y510.

Wyth said in his previous post:
> 
 I saw three options -- I'm not sure if one will work better than the other at this point. The three options are:
 
1. &#8227; lenovo-101e Lenovo 101E
2. &#8227; lenovo-nb0763 Lenovo NB0763
3. &#8227; lenovo-ms7195-dig Lenovo MS7195

So in the end it was #3 that worked best for me, solving both the headphone muting and subwoofer problems. Hopefully this works for everyone else too.

---

### Post by Zetheroo on 2008-03-01
Has anyone had any luck with the webcam? I don't care about the VeriFace feature... just ordinary webcaming.

---

### Post by wyth on 2008-03-02
Gomez, good find.  I just did this and have some beautiful sound.  I'm going to post this up at the Lenovo forums as well.

---

### Post by Kilbasar on 2008-03-04
Yup, subwoofer works! Good call! Now to get that pesky webcam working... :)

---

### Post by militem on 2008-03-04
Hi
I got tripped up on the first step.  I entered:

sudo aptitude install build-essential libncurses-dev gettext linux-headers-`uname -r`

And it said

matt@matt-laptop:~$ sudo aptitude install build-essential libncurses-dev gettext linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "linux-headers-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
matt@matt-laptop:~$ 

Any ideas?

---

### Post by wyth on 2008-03-04
You run uname -r to find out what kernel your running, and whatever it says, that's what you replace in 'uname -r'.  You won't find an application in the repositories called uname -r.

---

### Post by Kilbasar on 2008-03-04
I've noticed that the LFE (subwoofer) and Center channels do not get muted automatically when headphones are plugged in. Probably nothing to be done about that.

---

### Post by wyth on 2008-03-04
You need to add the following to /etc/modules:

```
snd-hwdep
snd-hda-intel
```That should do it on reboot.  It's a separate issue.  If that doesn't work, check [here]("http://ubuntuforums.org/showthread.php?t=646056").

---

### Post by Zetheroo on 2008-03-07
Cool,
thanks Wyth for all your help here.
I got the Subwoofer working and when I plug in headphones all the speakers go mute as they should!

SUPER! Now we need to work on getting the webcam to work.

Is there a specific reason why its not working?

---

### Post by wyth on 2008-03-08
I can't say for sure why the webcam doesn't work, but I know this isn't the only case of that happening.  A lot of people have trouble with external webcams, let alone internal.  I'm wondering if anyone has gotten a Lenovo with Suse preinstalled, and if those come with working webcams.  All we need are the correct drivers and the right software.  The problem is, which are which...

---

### Post by Zetheroo on 2008-03-08
Hey, I am wondering why it is that I am not getting as much loudness out of my Y510 as I get out of my T60.
All the speakers including the woofer are working, but when it comes to raw volume it seems to be a bit shy.

I have pushed up all the volume controls that make a difference, but it still does not get as loud as it gets in Vista. :(

---

### Post by Zetheroo on 2008-03-08
Hi again,
I don't know if this is any help ... but I think the camera in the IdeaPad Y510 is a BisonC07 chipset. 

I found the .inf file for this device:   [http://driveragent.com/archive/13516/3-0-3?q=bisonc07&PHPSESSID=evfjjc34c5kvgjgurnedkgual4]("http://driveragent.com/archive/13516/3-0-3?q=bisonc07&PHPSESSID=evfjjc34c5kvgjgurnedkgual4")

By the way, the webcam is working in Skype but the image is upside-down.

---

### Post by bwood on 2008-03-09
I too got the y510 at od -- great deal.  I found on the lenovo forums that the webcam will work with cheese, however like skype the image is upside down.  great laptop all in all just trying to decide whether i want to keep some space for xp or vista

---

### Post by wyth on 2008-03-12
So today I installed Cheese, and it picked up the webcam.  The image was upside-down, but under the effects, I just clicked the vertical swap effect, and I was right-side up.

So it seems things are coming along.  I know Cheese will be standard in Gnome 2.22.

---

### Post by Zetheroo on 2008-03-13
That's cool.... I just wish Skype had the same feature...

Is there a command which can be manually inserted into the file that controls the webcam and skype which will tell it to flip the image automatically?

---

### Post by stinger30au on 2008-03-13
im so glad that this laptop works well in ubuntu. I ordered a Y510-300 with 4 gig of ram, xp pro , and 500 gig hdd.

when it arrives i will set it up to dual boot between xp and ubuntu.
im thinking about cutting the hdd in half. give 250 to xp, and 250 to ubuntu.

then cut the 250 in half again and give myself an extra logical drive.
this way i install all my programs / os to drive c: and save data to drive d:
if i want to format c: and start agian, i dont have to worry about back as its on a seperate partition.

same with the 250 gig for ubuntu. the 250 in half. have a partiton for os & programs and a partition for all my data.

makes like real easy to upgrade o/s

it will be here in 4 weeks!!!   yee-haw!!!:guitar:

---

### Post by Zetheroo on 2008-03-13
I finally got Compiz running with Video Playback working as well.  :)

---

### Post by HunterThomson on 2008-03-22
I just can't figure out how to exit the menu I come to after the comand 

sudo nano /etc/modprobe.d/alsa-base

and adding

options snd-hda-intel model=lenovo-ms7195-dig

at the end. I tried to type ^X but it did not do anything and if I just restart or close the terminal it don't save. What do I do?

---

### Post by HunterThomson on 2008-03-22
never mind I go t it... I will not jump the gun next time.... Got everything:)
Mahalo everyone...:KS

---

### Post by daehenoc on 2008-03-26
Hi all,

I am assisting a friend spec a laptop to replace her old Dell that has died a horrible death on her and I'm looking at the Lenovo Y510-200 (Australia) as a replacement.  I took the 7.10 LiveCD to the Dick Smith near me and booted it up - it was great but I wasn't sure if the Intel 4965 AGN card was working - it didn't detect any wireless networks when the Y510-100 beside it did detect one - are there any problems with the 4965 chipset in Ubuntu?

Thanks!

---

### Post by wyth on 2008-03-26
I haven't had too much trouble with that card. It requires the proprietary driver; that may be why it wasn't working on the live cd.  You'd need to get into Restricted Drivers Manager and enable the driver for the chip, and that should do it.

I like this laptop quite a bit, but here's a couple things to consider:

1.) The screen will scrape against the keyboard when closed.  To avoid scratches, might want to get a little microfiber cloth and place it over the keys when closing the machine.

2.) I'm finding the keyboard isn't always all that responsive.  I thought this was just me getting used to typing on this machine (I'm a fast typer), but in the past few weeks I'm seeing that's not the case.  I'll hit a letter, and I'm paying attention to how I'm typing and KNOW I hit the key, but the key doesn't register.  This often occurs in clusters, where it'll miss a few keys not in a row, but near each other.

3.) There's an issue with Compiz on this particular gfx card.  It's easy enough to work around it, but just know that certain programs won't work all that well and may need some setting adjustment (VLC, Miro, Google Earth).  This may not be so much of an issue with Hardy Heron, since Gnome 2.22 is including some Compiz-like features as default without having to run Compiz.  If you're not completely sold on compositing (i.e. you really use your machine just for work and don't want too much getting in the way), you/she should be fine.

---

### Post by daehenoc on 2008-03-26
Hi wyth,

Excellent, thanks for the tip on the keyboard - I'll pass that along to the user.  They are picking the laptop up this morning (in fact, they should be at the shop now!) and I'll be installing Ubuntu on it today.

I don't know how fast they type, hopefully that won't be a huge issue, and I'm pretty sure they don't know what compiz is, let alone use compositing :p

Cheers,
Greg

---

### Post by daehenoc on 2008-03-27
OK, I am making this post on the nice shiny Y510-200.  It has the 4965 AG/N wireless chipset in it which worked just fine after a Synaptics update.  This revision has an NVidia 8400M GS video card which works fine with Compiz :)

However, I can't get Totem to play a DVD movie at all - even after I've installed libdvdcss2.  I can get it playing in MPlayer, but can't actually access the menu - nothing happens when I click on any part of the DVD menu??

---

### Post by HunterThomson on 2008-03-28
I am new to linux so I am still having trouble understanding how everything is setup, so hang with me on this one.
:confused:

I followed all the directions on page 2 and all my speakers "were" working even the sub woofer. But after I got home and turned on my computer again only the front two speakers were working. I tried to reinstall everything but no luck. Only error after error (I fix one error only to get a new one when I try again) when I try to make the alsa-driver. When I first installed all the alsa stuff and restarted all the speakers were working not even muted and never needed to do that step to fix the problem if you have no sound after following the alsa-* configure and install stuff. So I thought "well maby I'll try that now that I have tried everything ells with no luck". But, when I typed 
cp * /lib/modules/2.6.22-14-generic/kernel/sound/
in the termanal it said no such file or directory is there. I knew that it di exist and at that location so I tryed it with out the star and then it told me no destination file was given after cp * /lib/modules/2.6.22-14-generic/kernel/sound/ so I tried 

cp /lib/modules/2.6.22-14-generic/kernel/sound/ depmod -a

I got no error so I restarted the computer. Now, I have no sound at all and when I try to open the alsamixergui it tells me "alsamixer: function snd_cti_open failed for defalt: no such file or directory" and if I click on the volume controller in the bar it tels me "No volume control GStreamer plugins and/or devices found"

What did I do?How can I fix it? I am thinking about just reinstalling Ubuntu from the CD alredy it will probaly be faster the to back track and fix this problem.

Is there a program that I can make a sys recover for ubuntu linux with so if I do somthing stupid like this agin I can just restore it to the set up I had before I broke it? Like evil windows has.

Is it bad for my hard drive to reformat it a lot? I have reformatted it 4 times now in two weeks ( two times to TRY and get fedora to work but fedora sucks i.e. a brand new download CD needed like 10 hr of downloading of security updates at 10kb/s I hate fedora)

Mahalo

---

### Post by HunterThomson on 2008-03-29
To anyone ells new to linux and coding "Check everything one 'n' where it should not have been cost me 8hr's of trying to fix the problem"

---

### Post by HunterThomson on 2008-03-29
WTF!!!!!!
Why am I having so many problems???? I finally got the sound working again and sure enough when I restarted my computer only the speakers by the screen are working !!!!!!!!!!!!!
Am I the only one having this problem? I don't see anyone els having it. I read every link and did everything I could.I even reinstalled from the CD? what do I do now? What is going wrong? It seems like the only thing I have done with this computer is try and get the sound to work. I must have spent 30hr+ doing nothing but.
HELP any ideas...

---

### Post by wyth on 2008-03-31
[SIZE=3]A few things here:[/SIZE]

** First**, this is a bit of an older thread at this point.  It seems like your problem is related to your sound not coming up on reboot, which is different than not having sound installed at all.  You might want to start a new thread to see if anyone else has had that problem or has already fixed that issue.  (Hint: When you start a new thread, the forum software will present you with a number of posts that have similar key words as the title of your post.  Just by starting a thread, you may see some other threads that already answer your question.)
[B]
Second[/B], if you're new to all this, one tip for getting help is to trace back over the steps and explicitly show which one is failing for you and any errors that appear.  I'm not sure if you even know what step is failing, but I'm also not sure which guide you're following (I originally linked to a few, and eventually just posted the steps).  If you don't know what step is failing, the only thing to do is to debug -- go over the steps again, note what you're doing in each step, and note when unexpected info is returned after a step.  But no one can peek at your computer as you're working on it and tell you why you're having so many (or any) problems.  (I was new to this stuff a few years back too, and the one thing I've learned with it is how to logically work back through steps when something doesn't seem to work; 99% of the time that leads me to a solution without any emotional strife, and the 1% of the time it doesn't, it usually leads to a bug with a driver or software or something that just needs upgrading.)
[B]
That said[/B], it sounds like you may not be adding your sound card to the modules being loaded at boot.  I explained how do to this in the [step-by-step post here]("http://ubuntuforums.org/showpost.php?p=4329171&postcount=14").  Adding the module is near the bottom, but just to be safe, you might want to work through the steps again.  If that doesn't do it, try posting a new thread, because it seems no one on this thread is having that problem and therefor may not know the best solution.

**Lastly**, 8.04 is about out and will have a number of software updates that may address some of these issues.  I've had a steady problem 7.10 locking up on me (not just on the Lenovo), and am updating to the beta today to see if that solves anything.  It may solve some of your issues, but again, if you're new, you may want to wait to upgrade until a few weeks *after* the new one has been released.  (That way any new bugs get ironed out in the updates and you won't be faced with too many frustrations.)

---

### Post by wyth on 2008-03-31
I upgraded to 8.04 today and had to rebuild the alsa-drivers.  I followed the guide I posted earlier.  

I can report that not only do the speakers work, but they sound better than they did before.  I'm listening to Groove Salad right now, and it's never sounded so rich.  Be sure to enable Surround, Center and LFE in the volume control preferences.

---

### Post by HunterThomson on 2008-04-03
I am more new to forum pages then anything...

 I followed your steps to the T + the edit at the bottom of the page for the sub to work. This last time only the sub doesn't work, hardware sound keys, I have LEF in ALSA mixer(not muted) + other new things(not muted), ALSA mixer has REALTEK A888, speakers mute on headphones, and sound is better out of the speakers. I also think it is something is startup that needs to be fixed or it's just the alsa mixer.... I'll look around better, stick to posting on the noobs pages and poke around. That is the fun of linux anyway.;)

---

### Post by HunterThomson on 2008-04-03
also, I am using the 64OS....matter???

---

### Post by HunterThomson on 2008-04-08
?

---

### Post by wyth on 2008-04-09
> **HunterThomson said:**
> also, I am using the 64OS....matter???


If you're using a 64 bit machine, that very well make a difference.  That's a different set-up than I have, and I know 64 bit set-ups aren't widely supported outside of servers.  A friend of mine has a 64 bit machine that needs the new ALSA drivers and has also had trouble with it.

But if you have a Lenovo Y510, that's a 32 bit machine.  I'm not even sure if the 64 bit operating system would run on a 32 bit machine, or if it would if it would run correctly.

---

### Post by HunterThomson on 2008-04-10
I fixed the problem.

(Quick note on 64 32... How is it a 32? It has an intell core 2 duo T5550 1.83Ghz x86-64bit processor and that is what makes it a 64bit box, the possessor. I know they install the 32bit window$ but that doesn't meen it is a 32bit box that is just for software/firmware compatibility and maybe it is cheaper. Many many 64bit boxes are pre-installed with 32bit window$. This was one reason I made the leap to Linux because it has supported 64bit possessors log before window$ did... but now we are off topic)

FIX,  install the BootUp-Manager and check ALSA for start on boot or do it from the command line. Also, make sure you have the channel mode set to '6" in the alsa mixer.

FIX, I installed the 64bit Ubuntu 8.04 beta and the desk top extra effects work out of box. No need to trouble yourself with all that stuff to get them to work anymore.:guitar:

NEW Y510 PROBLEM for 8.04 KDE and Gnome, The screen is dimmed all the way on start up and also after I start VLC player. I have to turn it backup again.

And a big MAHALO to wyth for all the help:) could not have done it with out you.
P.S. KDE4 is vary Vi$ta wanabe[-( and sucks.

---

### Post by HunterThomson on 2008-04-10
You sure you don't have an intel core 2 duo T5450 1.6Ghz??? Even so the Pentium duel core is a X86-64..... If you want to know for sure, Check your hardware specks and see if the processor supports the x86-64 instructions set. Get the most out of your hardware that is what Linux is Half about. Also, my books say that the generic Linux kernel Ubuntu and most/all distro's installs doesn't have multi-threading enabled. You have to recompile the kernel to get even more power out of your hardware.:mrgreen:But I am having problems installing drivers so I will leave the kernel alone for now... Smiley mister green out-):P

---

### Post by wyth on 2008-04-11
I need to double-check my info, but I believe some 32 bit chips can support some 64 bit features, but it doesn't make them a full-on 64 bit chip that can run the full 64 bit instruction set.

Also, the brightness is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/211948").  You can get around this in the meantime by going into the gconf editor, navigating to /apps/gnome-power-manager/backlight and un-tick "enable" (might want to do the samein /apps/gnome-power-manager/ambient).  That worked for me for a while, but after some recent updates, mine's working alright, except the fn-up-arrow and fn-down-arrow keys are reversed.

---

### Post by HunterThomson on 2008-04-11
Ya,  that was my first thought but I don't have any brightness related things in power management on this 8.04. Just dim when idle and that is not checked. 

Broken- I just got a update and now the desktop effects won't work( I knew I should not have updated the compiz)

None of the consumer CPU's are real 64bit chips. They are all just two (or 4 or 3) 32bit chips  in the same die. AMD wrote the x86-64 instructions set for the first duel core processor the Athlon 64 (they call it AMD 64). Which is exactly two 32bit AMD Athlon chips stuck together. Intel just coped the instruction set for there Pentium Duel core. That is why AMD 64 works for intel 64 x86-64 and I think intel was who wrote SSE. So, you are right nobody has a true 64bit box but all duel core processors, I know of, support the full x86-64 instruction set because that is what x86-64 was written for, Two x86 processors working together.

"Intel 64 is Intel's implementation of x86-64. It is used in newer versions of Pentium 4, Pentium D, Pentium Extreme Edition, Celeron D, Xeon, and Pentium Dual-Core processors, and in all versions of the Core 2 processors." -Wikipedia- [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

After further looking I guess Core 2 Duo are "Real" 64bit processors not just two 32bit. And, Ya as far as I can tell your Pentium Duel core Mobile processes supports intel 64 x86-64....

---

### Post by danes on 2008-04-16
Hi everyone... I'm coming late to the lenovo's party...

well, I need you're help. I followed Wyth's instructions in order to activate my sound... ir works, but I still have the headphone issue. Whe I plug my headphones LFE and center speakers don't mute.

Also, when I mute LFE, Center, I don't get any sound from Surround speaker, even when other speakers are unmute.

I'd appreciate any help. Best Regards.

```
# lsmod | grep snd
snd_seq_oss            31616  0 
snd_seq_midi_event      6656  1 snd_seq_oss
snd_seq                49232  4 snd_seq_oss,snd_seq_midi_event
snd_seq_device          7052  2 snd_seq_oss,snd_seq
snd_pcm_oss            38304  0 
snd_mixer_oss          14976  1 snd_pcm_oss
snd_hda_intel         338072  5 
snd_pcm                68612  3 snd_pcm_oss,snd_hda_intel
snd_timer              19972  3 snd_seq,snd_pcm
snd_page_alloc          8200  2 snd_hda_intel,snd_pcm
snd_hwdep               7684  1 snd_hda_intel
snd                    47908  17 snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_intel,snd_pcm,snd_timer,snd_hwdep
soundcore               6496  1 snd

```

```
# lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by wyth on 2008-04-16
When you mute Center and LFE, you're also muting surround.  And those have to be muted in order to get total silence when headphones are plugged in.

That's just one of the quirks with this machine -- the hardware is still fairly new, and the drivers, I think, need to catch up some.

---

### Post by danes on 2008-04-16
I see Wyth... thx for your fast answer...

So, Don't I have to add any extra setup in my .asoundrc in order to get my surround 5.1 or 4.1...? like this page

[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

ttable stuff?

thnx

---

### Post by wyth on 2008-04-17
> **danes said:**
> So, Don't I have to add any extra setup in my .asoundrc in order to get my surround 5.1 or 4.1...? like this page

[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml]("http://www.cse.ohio-state.edu/%7Ebondhugu/alsamch.shtml")

ttable stuff?

thnx

You can try.  I've not seen that page before.  I'm on 8.04 Beta, and don't have any real issues (great sound when I enable center and lfe).  I'll look into it, though, and if I get it to work, I'll add something to the original tutorial.

Nice find.

---

### Post by danes on 2008-04-17
I made a google search about "alsa surround" and found many alsa howto about surround and finally I was playing around with ttable stuff I found this config for .asoundrc

```
pcm.51to40
{
        type route
        slave.pcm surround51
        slave.channels 6

        # Front and rear, at 75% of original signal strength
        ttable.0.0 0.75
        ttable.1.1 0.75

        ttable.2.0 0.20
        ttable.2.3 0.80
        ttable.3.1 0.20
        ttable.3.3 0.80

        # Center channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.4.2 0.375
        ttable.4.2 0.375

        # LFE channel routing (routed to front-left and front-right),
        # 6dB gaindrop (gain half of main channels) per channel
        ttable.5.5 0.75
        ttable.5.2 0.2
        ttable.5.5 0.75
        ttable.5.2 0.2
}
```

in a config ttable.x.y z, where 'x' is the new speaker, 'y' is the native speaker (#0 is front left, #1 front right, #2 center speaker, #3 the rear left speaker(LFE), #4 the rear right speaker (LFE)), if we assign twice the same new speaker (twice 'x' like ttable.5.y1 z1 and ttable.5.y2 z2) we will get the y1+y2 speaker gaining z1+z2 routing to the LFE speaker (#5) {last 4 lines in the .asoundrc}

I hope to be clear.

and tested it with
```
# speaker-test -c 6 -D 51to40 -t wav
```

ESD must be disabled in gnome-audio-settings

This all I get... hope you can find something else, I'm not good with alsa. Finally, I think we have a built in 4.1 surround system. 4 speakers (front left, front right, rear left, rear right) and the subwoofer (LFE)... but we want a 5.1 surround... (front left, front right, center, rear left, rear right) + Subwoofer (LFE).

best regards.

---

### Post by polluxx on 2008-04-17
Wyth, thanks heaps for your soundcard tute, that's fantastic work. I recently purchased a Y510 200 as well, and coming from Debian I am really impressed about Ubuntu's hardware configuration.

Still, there's a few questions/comments:

1. After a Hardy update, the sub stopped working. I checked everything and the module is running with MODEL option lenovo-ms7195-dig. Surround, Center and LFE are enabled. Hardy currently supplies ALSA version 1.0.16, so there should be no need to manually compile the ALSA modules. Do you know what could have happened there, the sub was working normally before.

2. No problems with the webcam, it is automatically picked up in Cheese, right orientation, fantastic.

3. I'm currently playing around with suspend/hibernate, which seem to be working on and off. Experienced the white screen a few times after waking up. USWSUSP seems to be working better if it comes to hibernation.

Cheers.

---

### Post by TeeAhr1 on 2008-04-18
Just bought one off newegg, mostly due to the great content of this thread, thank you all for helping me buy my laptop!

First thoughts:

I am having keyboard problems, big time. Keyboard mapping to the mouse sporadically, or jumping up to a prior text box in the middle of typing (kind of irritating when it's my password), or just plain missing keystrokes. I'm pretty fast, and it's when I go fast that it seems to puke, but not always even when I'm going fast. If anyone has any ideas on this, please let me know, this is killing me.

As others have noted, I can't adjust the brightness. I run KDE, so the gconf tip doesn't really help.

Have others tried sleep and suspend yet? I have not.

Other than these couple things (the keyboard's a biggie, though), I'm totally in love. Great wireless reception, I really like the style of the chassis and the weighted lid. Very glad I bought a trackball mouse to go with it, the touchpad does suck. This is maybe the fourth time I've turned it on, but I'm extremely happy with it so far.

---

### Post by wyth on 2008-04-18
polluxx, did you do a clean install of 8.04?  Maybe I need to do that to get the camera working.  I don't have the sub either, and I recompiled ALSA with the upgrade, but Center and LFE work.

TeeAhr1: I know what you mean about the typing, I had the same problem when I first got the machine and wrote about that issue on the Lenovo boards.

What's happening is the touchpad is pretty sensitive and picks up random bumps from the hand/thumb while typing.  This can move the cursor into some other place and screw up your typing.

One fix is this: 

First check that you have xserver-xorg-input-synaptics installed (you shoud).


Then go to System > Preferences > Sessions and add a new startup program.  Call it what you want, but under Command, put 
```
syndaemon -i .5 -d
```You can change .5 to whatever you want.  That's the length of buffer time (half a second) between typing and when the touchpad will accept any input after typing.  

So if you're typing and have that setting entered, it'll take half a second after you stop typing before the touchpad will accept any taps, etc.

This helped me quite a bit.  Adjust that number to find what works for you.  You'll need to restart X for it to take effect, but with it in the startup programs, it'll start with boot.

---

### Post by polluxx on 2008-04-18
Yes. Clean install from a Beta Live CD.
Still no (re)working subwoofer. Center, Surround and LFE are enabled, they don't seem to have any effect though, disabling has no consequences. Up to date Hardy packages.

After some more testing re hibernate/suspend: I basically followed the advice in [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"):
1. In /etc/X11/xorg.conf add ```
Option  "NvAGP"  "1"

```
2. In /etc/default/acpi-support set ```
SAVE_VBE_STATE=false
POST_VIDEO=true
```
**Note:** This is different from above link: Setting POST_VIDEO=false breaks Suspend on my y510 200 with nvidia 8400m gs.
3. In /etc/modprobe.d/blacklist blacklist the following modules
```
blacklist intel_agp
blacklist agpgart

```

With these settings both Hibernate (S4) and Standby (S3) work flawlessly.

---

### Post by HunterThomson on 2008-04-19
In KDE you can adjust the brightness by holding down the "Fn" key and pressing the Down Arrow key. This is also good for Gnome so the brightness applet doesn't take up space.

If you have LEF and Surround un-muted and turned all the way up with no effect then go to ALSA Mixer/Options/Chanel Mode and set to 6ch instead of 2ch. Should work then.
Also, polluxx one of the updates is a new kernel version. After I got it the volume keys stopped working and no longer mutes on headphones. I bet you have to reinstall the drivers with the new kernel but I will leave well enough alone. I have had enough problems getting the all the speakers working. However, after all this messing around/reading/looking through the file system and setting up Xubuntu on a friends virus ridden now ex-window$ box, I now feel at home with Linux and hate getting on a window$ box.

Thanks polluxx I will check that out and try different settings to get suspend/hibernate working with my intel x3100 GPU.

Now if we could fix the problem with the screen being dimmed all the way on boot/VLC/Game startup. There was no problem with ether of these in Gusty.

---

### Post by HunterThomson on 2008-04-19
wyth- page 4
"This may not be so much of an issue with Hardy Heron, since Gnome 2.22 is including some Compiz-like features as default without having to run Compiz."

This is true, I loved them and then I got a Compiz update and the settings went away and the GUI I used to a just the settings was removed and is no longer in Add/Remove. Do you know how I can get it back???

---

### Post by polluxx on 2008-04-19
HunterThomson: Setting Channel Mode to 6ch does not have any effect on my machine (nor does setting it to 4ch for that matter). So still no sub.

I never experienced any problems with the volume keys, updating to a newer kernel version during the Hardy update didn't create any problems. Also, the sound always mutes when headphones are plugged in.

Furthermore, there are no problems with the screen brightness getting dimmed during boot or VLC startup on my machine.

---

### Post by HunterThomson on 2008-04-19
Really..... Hum.... That is really good to know.... Wow, no problems with the brightness.... I am going to compile my own kernel today so I'll see what happens after that. All that broke after a kernel update.

Have you made sure alsa is starting on startup. Other then that the problem is over my head at the moment.

---

### Post by polluxx on 2008-04-20
HunterThomson: Yes, ALSA is started during startup. Well, I guess there is nothing else to do for the moment then. Thanks for your help anyways.
Re screen brightness, the only issue that I have on my machine is that the keys for decreasing and increasing the screen brightness seem to be reversed. Only minor flaw really.

---

### Post by HunterThomson on 2008-04-20
Well you could still try to RE install the OS. It is really amazing how every time I install Ubuntu different things are broken in different ways and vice versa.

Also, as far as I could find my problem with the Dim on boot is a bug with the Kernel for AMD64. Are you running the 64bit? The brightness buttons are reversed on my box too. I just installed 7.10 and am going to upgrade to 8.04 when it is released and see what happens then. I am thinking about installing Xubuntu in my free space or just the desktop package in synaptic. I just installed it on my friends desktop with 256RAM and it is running grate, almost as fast as my laptop with 8times the ram and more then three times the processing power. The one thing I like is that XFCE seems to have desktop effects built in or something and looks grate on his intel GPU.

---

### Post by polluxx on 2008-04-20
I might consider reinstalling after the final Hardy has come out, however, as I started off with a clean Beta Hardy live CD, I don't see how reinstalling (and updating the system successively) would solve any issues.

My notebook is running the 32bit version, I somehow don't quite trust the 64bit versions (yet), there still seem to be too many issues with various hardware components. But that's just my two cents.

---

### Post by mawzi on 2008-04-20
Hi, 

sorry in advance for my bad English and my lack of IT acknowledgment. 
I came here to find help since i just bought a lenovo Y510. I installed an Ubuntu 7.10 - Gutsy Gibbon with Gnome 2.20.1.

did anyone found a solution for the webcam in messenger softwares? 
I used Cheese with success but Kopete does not work with the webcam.

i just would like to chat with my family & friends through MSN and Yahoo Instant messenger protocol.

many thanks to everybody for your precious help. :KS
mawzi

---

### Post by HunterThomson on 2008-04-20
I have had no problem with the web cam on my 64bit..8.04. The picture was right side up in Cheese AND Skype. I have not tried Skype on Gusty 7.10 64bit. Nor, have i tried the program you are talking about. Dose Skype work fine on 32bit 8.04 Hardy?

---

### Post by mawzi on 2008-04-20
hi, 

i installed cheese tonight and the webcam is upside down... but when i add an effect (vertical mirror) the image is ok. 

actually, in kopete, i can see my image in the device general settings, but upside down too. and i don't see anyoption to change this in kopete. 
but maybe in another way. 

i test tomorrow with amsn the webcam. tonight, it is too late in france to find an active contact in my buddy list! 

thank you again and to tomorrow

---

### Post by HunterThomson on 2008-04-20
Well upside down is not too big of a problem I guess... Hope it works out for you or someone finds a fix for the 32bit OS.

---

### Post by girlfromhell on 2008-04-26
Somewhat of an intro post here.  I got myself a Y510 back when office depot had the special. Actually, I had my parents pick one up for me and I got it from them when I went home for visit.  Best $600 I think I have EVER spent.  I would probably get blocked for life if went on a rant about how much I deteste Vista, so I took the leap last night and absolutely love Ubuntu.  Still have a bit of tweaking to do yet, but I can't believe I waited 2 months to do this.

Wow.  Just Wow.

---

### Post by TeeAhr1 on 2008-04-27
Okay, here's my post-8.04-release post. First, hearty thanks to everyone who hacked out the sound issues, this thing absolutely sings. I've never had such good sound on a laptop.

I've got nothing going with the function keys at all in KDE4 except home, end, and numlock. I use cmus, music player of the gods, so I didn't even try play/pause etc., but brightness and volume do not work. The volume key on the right also does nothing. I do have gnome installed as well, haven't tried it over there.

Wyth, thanks a ton for the tip on the touchpad, you've saved my sanity. Does anyone know a way I can automatically turn off the touchpad when my usb mouse is detected? Barring that, manually?

All in all, I'm thrilled with it. Thanks to everyone who's contributed to this thread so far.

---

### Post by wyth on 2008-04-27
> **TeeAhr1 said:**
> Wyth, thanks a ton for the tip on the touchpad, you've saved my sanity. Does anyone know a way I can automatically turn off the touchpad when my usb mouse is detected? Barring that, manually?

Have a look at your F8 key; if you click Fn+F8, it'll shut off the touchpad while your USB mouse is plugged in.  (The USB mouse will still work.)

I think it might be worth it to let Lenovo know that there's a growing number of happy Ubuntu campers on their hardware.  They just started supporting Suse; I wonder how difficult it would be for them to at least provide a little configuration aid for other linux users.

---

### Post by TeeAhr1 on 2008-04-28
> **wyth said:**
> Have a look at your F8 key; if you click Fn+F8, it'll shut off the touchpad while your USB mouse is plugged in.  (The USB mouse will still work.)

I think it might be worth it to let Lenovo know that there's a growing number of happy Ubuntu campers on their hardware.  They just started supporting Suse; I wonder how difficult it would be for them to at least provide a little configuration aid for other linux users.

So you're saying "don't give up on the fn keys?" :) Thx, that worked. Also, I confirm that the brightness/volume fn keys do work in Gnome (with the brightness up/down reversed as someone else noted), but not in KDE4. I have submitted a bug [here]("https://bugs.launchpad.net/ubuntu/+source/kubuntu-kde4-meta/+bug/223643").

(looking over my problem list) Well, that pretty much covers it for me. I haven't tried the webcam (because I have no interest), but aside from that and the mentioned KDE4 problem, I'm set. Have I mentioned yet how grateful I am to y'all? You rock, guys!

When I find the time, I'm going to figure out how to map the multimedia keys to cmus. If anyone's interested I will post my results.

---

### Post by wyth on 2008-05-02
I don't think this was posted before, but if anyone is looking for a way to keep from bumping the touchpad while typing, [check out syndaemon]("http://ubuntuforums.org/showthread.php?t=271052&highlight=syndaemon").

This is already configured in, just not turned on by default.  Set it up in your Session startup programs, and it'll help with things.  I was messing with my config files and lost that without realizing it, and it was making typing dadgum chore.

---

### Post by hunting_bears on 2008-05-03
Hi everybody, I just wanted to say thanks for all the time you guys put into this thread. I'm a _complete_ noob to linux (I had to use google to find the terminal) and after 5 grueling hours I finally got my sound to work right.... at least I learned a lot on the way. So thanks again.

---

### Post by arvast on 2008-05-03
This thread is just what I needed!

I had been trying to find out how to fix my sound for a long time now and the options people gave me was to file a bug report, which obviously would have been stupid :KS

Although I am having some troubly with my Y510, and I dont know if its related to the computer at all but maybe; My brightness buttons are inverted D: and so is brightness. Dim makes lighter and setting light settings to max makes it really dark D:

Otherwise I really love this computer. Slimmed down windows to a 20gb partition for a few games. The rest for sweet sweet ubuntu :)

---

### Post by TeeAhr1 on 2008-05-04
> **polluxx said:**
> Yes. Clean install from a Beta Live CD.
Still no (re)working subwoofer. Center, Surround and LFE are enabled, they don't seem to have any effect though, disabling has no consequences. Up to date Hardy packages.

After some more testing re hibernate/suspend: I basically followed the advice in [https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"):
1. In /etc/X11/xorg.conf add ```
Option  "NvAGP"  "1"

```
2. In /etc/default/acpi-support set ```
SAVE_VBE_STATE=false
POST_VIDEO=true
```
**Note:** This is different from above link: Setting POST_VIDEO=false breaks Suspend on my y510 200 with nvidia 8400m gs.
3. In /etc/modprobe.d/blacklist blacklist the following modules
```
blacklist intel_agp
blacklist agpgart

```

With these settings both Hibernate (S4) and Standby (S3) work flawlessly.

You've got an nvidia chip in your? I've got the intel chip, and blacklisting intel-agp puts my in restricted graphics mode.

---

### Post by Zetheroo on 2008-05-04
I recently installed Hardy on my Y510 and noticed something very strange...

the screen dims when it should brighten up and brightens up when it should dim. Something is very mixed up.

Also the webcam image is still upside-down in Cheese and the subwoofer is not working out of the box....

Do I need to install new alsa drivers still?....

Please help...

---

### Post by arvast on 2008-05-04
> **Zetheroo said:**
> the screen dims when it should brighten up and brightens up when it should dim. Something is very mixed up.

I have the exact same problem. Brightness buttons are inverted as well as power settings. Which kind of sucks when youre trying to save battery =P

Im looking forward to find or hear an answer about this!

---

### Post by Zetheroo on 2008-05-04
The slightly ridiculous thing about the brightness and dimness issue is that in Gutsy this was not an issue -- so as far as I can see Hardy has not made anything work that was not working before, but instead has added to the already present list of hardware/software glitches....:(

Update: Here is another Hardy Heron glitch .... the SD Card Reader does not read the data on my SD cards anymore!?!? What gives?

---

### Post by arvast on 2008-05-05
I just tested the Webcam with aMSN 0.97 and it works great :KS

I dont understand what the issue was ^^;

---

### Post by wyth on 2008-05-05
> **arvast said:**
> I just tested the Webcam with aMSN 0.97 and it works great :KS

I dont understand what the issue was ^^;

I'm not sure what your image looks like; mine is working better, but not great.  Here's an image of my beagle on Cheese.  Note the weird image quality and the upside-down-ness, which happens on Skype as well.

---

### Post by arvast on 2008-05-05
Weird =/

Mine is working fine just as if I was running it in windows. Im going to try with skype too. Not that I could tell you what Ive done differently but still ._.

---

### Post by polluxx on 2008-05-06
> **Zetheroo said:**
> The slightly ridiculous thing about the brightness and dimness issue is that in Gutsy this was not an issue -- so as far as I can see Hardy has not made anything work that was not working before, but instead has added to the already present list of hardware/software glitches....:(

Update: Here is another Hardy Heron glitch .... the SD Card Reader does not read the data on my SD cards anymore!?!? What gives?

The brightness/dimness situation can hardly be called an issue, if you are so annoyed with it, just manually change the corresponding scripts in /etc/apci/ that handle those key events.

@Arvast: I don't know the "power settings" you are referring to and which are supposedly inverted. However, same thing as with the brightness buttons applies here as well, you could always change the apci event scripts yourself. I don't know how that situation prevents you from saving battery.

Furthermore, my SD Card Reader works absolutely flawlessly, and I'm also running Hardy here.

So far, everything (!) and every single hardware component works without any problems (thanks to wyth and this thread), i.e. Subwoofer, Camera etc. as well as Suspend and Hibernate. It's absolutely fantastic.

---

### Post by Zetheroo on 2008-05-06
polluxx: The issue is that in Hardy Heron the brightness/dimness issue was non-existent -- generally a new release of anything is supposed to be an improvement.

- Brightness/Dimness
I would love to be able to fix this issue by manually fiddling around with scripts and whatnot ... but I for one am not clued in on what exactly I would need to look for and edit. So if you could help me with step-by-step instructions I would be glad to try that out.
It would seem to me to be very obvious that if the system were brightening the screen when it should be dimming it that the battery life would be effected -- I don't know why this would be hard to understand!?

- Webcam
I would like to confirm with you that the webcam is working (without tweaking) in Cheese and Skype. If this is not the case please and you have only gotten it working with tweaking please divulge further.

- SubWoofer
I too got the Subwoofer to work at one stage in Gutsy, however after a restart of the machine the SubWoofer and the two center speakers ceased to function. From then on the sound performance was erratic and never fully functioning.
At this point I have 4 of 5 speakers working -- the SubWoofer being the 5th -- so I am a bit hesitant to fiddle with ALSA as last time I lost more funtionality than I initially had.


Any advise would be appreciated.

Thanks

---

### Post by wyth on 2008-05-06
I've been looking into

[LIST]
[*]/etc/acpi/events/
[*]/etc/acpi/thinkpad-brightness-up.sh
[*]/etc/acpi/thinkpad-brightness-down.sh
[*]/usr/share/acpi-support/key-constants
[/LIST]
and I've not found anything in particular that would refer to the brightness buttons on an IdeaPad.

I still have Gutsy installed on another machine, so I might poke around in that and see if there's any significant differences in some of these config files.  (It's storming now and I'm not plugging that machine in -- already replaced one motherboard.)

What arvast is talking about, with regard to power issues, is that with the brightness calls reversed, when you're on battery the screen will auto-brighten instead of auto-dim.  It's not just that the buttons are reversed; the behavior is as well.  

So I'm thinking about a clean install to see if that makes a difference.  But I noticed recently that the IdeaPads are [being sold with different configurations now]("http://shop.lenovo.com/SEUILibrary/controller/e/web/LenovoPortal/en_US/special-offers.workflow:find-config?category-id=1EEC64E5FB8342ADBD9807711D829D48&ifacet=0&filter=Product%20Family_2") -- Nvidia cards and other little changes.  That may change some of what we're talking about in this thread; some people may have a little bit different hardware, which changes what works and what doesn't work for them.

---

### Post by Hammondman on 2008-05-06
Hi guys,

sorry for a VERY newbie question.. but I just installed Ubuntu on my Y510 and I'm trying to follow the steps the Wyth laid out for getting the Alsa audio drivers going. I can't get further than the unzipping.  When I try to compile it says that the compiler can't make executable files.  What should i do?

Thanks!

---

### Post by wyth on 2008-05-06
Hammondman, do you have the compile tools installed?  

First step is, in the terminal,
```
 sudo aptitude install build-essential
```Those are the tools you need to compile any program.  

If that's not already installed, do that and then see if you can get on to the next steps.  If there's still a problem, check back in.

---

### Post by polluxx on 2008-05-06
> **Zetheroo said:**
> polluxx: The issue is that in Hardy Heron the brightness/dimness issue was non-existent -- generally a new release of anything is supposed to be an improvement.

- Brightness/Dimness
I would love to be able to fix this issue by manually fiddling around with scripts and whatnot ... but I for one am not clued in on what exactly I would need to look for and edit. So if you could help me with step-by-step instructions I would be glad to try that out.
It would seem to me to be very obvious that if the system were brightening the screen when it should be dimming it that the battery life would be effected -- I don't know why this would be hard to understand!?

- Webcam
I would like to confirm with you that the webcam is working (without tweaking) in Cheese and Skype. If this is not the case please and you have only gotten it working with tweaking please divulge further.

- SubWoofer
I too got the Subwoofer to work at one stage in Gutsy, however after a restart of the machine the SubWoofer and the two center speakers ceased to function. From then on the sound performance was erratic and never fully functioning.
At this point I have 4 of 5 speakers working -- the SubWoofer being the 5th -- so I am a bit hesitant to fiddle with ALSA as last time I lost more funtionality than I initially had.


Any advise would be appreciated.

Thanks

Of course it is evident that a lower screen brightness results in a longer battery life. However the fact that once you have switched from AC to battery power the screen brightness gets automatically readjusted (dimmed that is in my case at least) shows that the gnome-power-manager handles this ACPI event properly (if it's activated in the g-p-m preferences at least) and helps prolonging the battery life. This has nothing to do with the brightness/dimness keys being inverted. Again, in my case only the buttons are reversed, not the behaviour, as wyth put it.

After a bit of research and fiddling, I came up with the following two substitute scripts for /etc/acpi/video_brightnessdown.sh
```

#!/bin/bash
path=/proc/acpi/video/VGA/LCDD/brightness
currentlevel=`grep 'current:' $path | awk '{print $2}'`
if [ $currentlevel != 0 ]; then
    level=$(($currentlevel-1))
    echo -n $level > $path
fi

```
and /etc/acpi/video_brightnessup.sh
```

#!/bin/bash
path=/proc/acpi/video/VGA/LCDD/brightness
currentlevel=`grep 'current:' $path | awk '{print $2}'`
if [ $currentlevel != 10 ]; then
    level=$(($currentlevel+1))
    echo -n $level > $path
fi

```
Now, interestingly enough, this does **not work** via the ACPI+HAL chain. Manually executing them produces the desired effects, however in combination with the Fn+up/down keys it does not. acpi_listen gives the proper event, /var/log/acpid states the proper execution of the scripts video_brightness{down,up}.sh and lshal -m also reports the key event. 
A bit of research shows some similar (but not identical) problems with Gutsy before, resulting in a few bug reports.

One more interesting thing is that /proc/acpi/video/VGA/LCDD/brightness states 10 different brightness levels, out of which only 8 can be accessed via the Fn keys. Brightness 9 and 10 can only be set by manually executing video_brightnessup.sh (or echo'ing a value of 9 or 10 respectively to /proc/acpi/video/VGA/LCDD/brightness) and indeed results in an even brighter screen.
Other than that, I'm at a loss here.

2. Webcam
The Webcam on my machine Y510 200 with GeForce Card was indeed working out of the box for both Skype and Cheese. No upside-down image and no tweaking.

3. Subwoofer
Following closely wyth's instructions all speakers are working. I did not recompile the ALSA drivers, since Hardy already comes with the newest version 1.0.16. Unmuting Center and LFE eventually resulted in a working Sub. That's all.

---

### Post by Zetheroo on 2008-05-06
polluxx: Thank you for your insight into these issues.

The brightness/dimness information you gave sounds good, however I would need something a little more "step-by-step" as I am not an advanced Linux user ... yet ... hehe

So with the webcam it seems that its an issue with the graphics chipset and not the actual webcam itself, if you say that with the Nvidia Graphics you are getting a good webcam experience out-of-the-box!?

UPDATE: polluxx: having looked over your past postings it seemed to me that you never really got the Sub to work!? -- or did you finally get it working!? -- if so what exactly did you do?

wyth: Could you summarize what needs to be done by someone with Hardy on their Ideapad Y510 to get the sound working to its full potential? Maybe you have already done that and I just overlooked it!?

---

### Post by polluxx on 2008-05-06
@Zetheroo: 
1. Let me know if you need any more detailed information re the brightness/dimness keys, I'm happy to help out as good as I can.
However, I don't think this can be resolved very easily, as the scripts in /etc/acpi/ seem to be ignored, and there seems to be some hardcoded routines that take care of those particular key events. Reading through some of the older bug reports (which may or may not be related to this) the situation is all but trivial, with ACPI, HAL and on top of that the gnome-power-manager having their fair share in making everything less transparent.
So far I believe this might actually be an issue with HAL rather than ACPI.

2. Indeed the webcam issue seems to be related to the graphics card, again here with a Geforce 8600 GS it worked out-of-the-box.

3. Re the subwoofer: I'm afraid I can't be of much help here, as I don't quite understand why it suddenly started working. Again, I basically followed wyth's steps:

 - in /etc/modprobe.d/alsa-base add a line
```

options snd-hda-intel model=lenovo-ms7195-dig

```

 - unmute Center and LFE in the Mixer as these (both) control the volume of the Subwoofer

 - if the speakers won't mute if headphones are plugged in, add the following to /etc/modules
```

snd-hwdep
snd-hda-intel

```

I think after the last Hardy update my sub suddenly started working, that's all I can say. No manual ALSA driver update was involved.

---

### Post by wyth on 2008-05-07
pollux, that's some great research you dug up.  I've been pretty busy with work and haven't had a chance to look into this any more, but I'm curious if you did a clean install.

I'm also curious if anyone installed the 64-bit version on the IdeaPad, and if so, how tht's been.

---

### Post by Hammondman on 2008-05-07
Hi Wyth,

Thanks, duh!  I obviously missed that important step... but i do need to 'check back in now'  again forgive my newness...

When I do the 'sudo make' step for the first drivers it just goes looking for a directory named 'Driver' and says error a crapload of times.  How do I get it to find it.  It's all there and extracted in the directory I'm in... the ./configure step worked...

root@adam-laptop:/home/adam/Driver Pack/alsa-d river-1.0.16# sudo make
find: /home/adam/Driver: No such file or directory
find: Pack: No such file or directory
find: /home/adam/Driver: No such file or directory
find: Pack/alsa-driver-1.0.16: No such file or directory
 etc...


Thanks

---

### Post by Hammondman on 2008-05-08
ooops, sorry, I seemed to have sorted it out

---

### Post by Zetheroo on 2008-05-08
Ok... so I got the SD card working and the Subwoofer as well.

The SD card filesystem needed to be repaired, which I did with Gparted.

Need the webcam .... :(

UPDATE: After rebooting the Sub is no longer working. -- like before.... what to do?

---

### Post by wyth on 2008-05-09
Open your sound preferences (double-click the volume control in the top panel) and check if Center and LFE are muted.  That's one thing with all this, or rather two things:

[LIST=1]
[*]Center and LFE seem to always start muted
[*]Plugging in headphones mutes all speakers *except* Center and LFE (You'll need to mute them again)
[/LIST]

---

### Post by Zetheroo on 2008-05-09
Just to clarify what I did from a to z:

1) In the file /etc/modprobe.d/alsa-base I added this line

options snd-hda-intel model=lenovo-ms7195-dig

then I saved the file and restarted the machine.

2) Upon rebooting I saw I had a few more options in the Sound preferences dialog, two of which were LFE and Center. I proceeded to select the two so that they showed in my volume control panel, un-muted them both and raised the volume to max.
Then I played an audio file and found to my joy that the sound was much richer than before. I muted and un-muted LFE and Center multiple times to check the difference of sound -- and what a diff!

3) With the LFE and Center um-muted and raised to max volume I restarted the machine again and then played the same song. The sound was noticeably weaker so I checked the sound panel and everything was as it should be with the LFE and Center both un-muted and volumes raised.
I muted and un-muted LFE and Center but nothing changed.



So this is what happened with Gutsy as well. It worked the first time but after the next reboot never worked again.

Any ideas? :confused:

UPDATE: I am wondering if the issue with the IntelX3100/webcam hardware could be reported as a bug? -- or is it not right for that!?

---

### Post by wyth on 2008-05-10
Just noticed I was asked some questions I didn't answer.

I just did a clean install: am still having the same camera issue, and need to set up alsa again.  Those weren't worked out. 

I'm buried in work at the moment, and will respond more in full when I get the chance.  Some of my original instructions were for Gutsy, and yeah, things have changed.

---

### Post by arvast on 2008-05-10
Anyone got working S-Video? =/

---

### Post by Hammondman on 2008-05-14
I got this off the realtek site with their driver packages... (attatched readme.txt)  

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

I've been trying to follow the process but I can't find this file..

"Edit your /etc/modules.conf or conf.modules depending on the distribution"


Have you guys seen this process?  What do you think?  Any thoughts/help?

---

### Post by Hammondman on 2008-05-14
Also, wyth, you mentioned there were some simple workarounds to get compiz working...

when I started using compositing it was working just great, now it's on and off, at the beginning of a session I will just get blank spaces in all my windows etc. during all of the effects, then sometimes it will kick in and start working perfectly for some reason.  Any advice?

---

### Post by pwtico on 2008-05-15
My Lenovo Y510 arrived yesterday and I immediately installed Ubuntu 8.04 64-bit on a dual boot with Vista.

Here's a report on issues encountered with the 64 bit install:

--Webcam worked out of the box. Image was right-side-up in Cheese and Skype.

--I went through Wyth's instructions for updating the ALSA drivers to 1.0.16 before realizing that 8.04 already has the latest drivers.  Oh well. I encountered exactly the same issue described by Zetheroo.  The woofer (LFE and Center) worked at first, but after re-booting they stopped working, even though they are un-muted and have raised volume in ALSA mixer.  Anybody has any ideas on how to address this?  I've added 

snd-hwdep
snd-hda-intel

to the /etc/modules, but still no luck.

--I installed the ubuntu-restricted-extras media codecs, installed VLC and MPlayer, but still can't get a DVD to play.  Is this a 64-bit issue?  I'm still very new at Ubuntu, so I'm not sure where to go on this one.

--The Fn brightness buttons are reversed, but otherwise work.

--The media buttons work, except for the equalizer buttons.

Otherwise everything has worked amazingly well right out of the box.  This is a really solid and cool-looking machine.
__________________
Lenovo Y510 | Ubuntu 8.04 64 bit | 1.6 GHz Core 2 Duo T5450 | 2 gig RAM | Intel X3100 gfx | 250GB 5400 RPM hard drive.

---

### Post by pwtico on 2008-05-15
Never mind the DVD issue--I installed the medibuntu repos and w64codecs, and now Totem and VLC work just fine.

And I got the sound working!  Just did a fresh install of 8.04 and followed the instructions above.

---

### Post by HunterThomson on 2008-05-16
> **pwtico said:**
> My Lenovo Y510 arrived yesterday and I immediately installed Ubuntu 8.04 64-bit on a dual boot with Vista.

Here's a report on issues encountered with the 64 bit install:

--Webcam worked out of the box. Image was right-side-up in Cheese and Skype.

--I went through Wyth's instructions for updating the ALSA drivers to 1.0.16 before realizing that 8.04 already has the latest drivers.  Oh well. I encountered exactly the same issue described by Zetheroo.  The woofer (LFE and Center) worked at first, but after re-booting they stopped working, even though they are un-muted and have raised volume in ALSA mixer.  Anybody has any ideas on how to address this?  I've added 

snd-hwdep
snd-hda-intel

to the /etc/modules, but still no luck.

--I installed the ubuntu-restricted-extras media codecs, installed VLC and MPlayer, but still can't get a DVD to play.  Is this a 64-bit issue?  I'm still very new at Ubuntu, so I'm not sure where to go on this one.

--The Fn brightness buttons are reversed, but otherwise work.

--The media buttons work, except for the equalizer buttons.

Otherwise everything has worked amazingly well right out of the box.  This is a really solid and cool-looking machine.
__________________
Lenovo Y510 | Ubuntu 8.04 64 bit | 1.6 GHz Core 2 Duo T5450 | 2 gig RAM | Intel X3100 gfx | 250GB 5400 RPM hard drive.

To fix the sound problem on restart-------

Open the ALSA Mixer and click through the tabs till you see the Chanals option and set it to "6ch" That one confused me for the longest. It is so simple and the sound did work on initial reboot.

The brightness buttons reverse thing is a porblem with a lot of laptops. 

Is you screen all the way dim on boot?

I had a lot of problems with 8.04 i.e. dim on boot, was prity much the only one that rely got on my nerves. Although, wyth did tell me that his 32bit didn't have a that problem. However, I don't think downgrading to a 32bit OS is a fare trade so I am back on 7.10 now. AND, that bug is confirmed and assigned to a programmer to fix, last I checked. I also remember a lot of annoying permission stuff, like a lot more stuff you needed to be root for.

---

### Post by Zetheroo on 2008-05-17
The thing about the brightness/dimness issue that is most annoying is the fact that the screen dims when it should brighten and brightens when it should dim.
This means that when you are battery power your screen brightens to max automatically instead of dimming. Likewise when you are operating on AC power the screen dims automatically. 
This is really annoying!!! -- Glad to know that its being looked into...

pwtico: Do you have a Y510 with Nvidia graphics?

HunterThomson: I will try changing the channel on the sound panel... 

Hammondman: Compiz worked out-of-the-box for me with Hardy -- been pretty stable...

UPDATE: HunterThomson -- that fixed it!!! Thanks a million!

---

### Post by HunterThomson on 2008-05-17
> **Zetheroo said:**
> The thing about the brightness/dimness issue that is most annoying is the fact that the screen dims when it should brighten and brightens when it should dim.
This means that when you are battery power your screen brightens to max automatically instead of dimming. Likewise when you are operating on AC power the screen dims automatically. 
This is really annoying!!! -- Glad to know that its being looked into...

pwtico: Do you have a Y510 with Nvidia graphics?

HunterThomson: I will try changing the channel on the sound panel... 

Hammondman: Compiz worked out-of-the-box for me with Hardy -- been pretty stable...

UPDATE: HunterThomson -- that fixed it!!! Thanks a million!

:guitar::guitar:
YA! That one took me like three weeks.....

I felt like a fool after I figured it out. WYTH even said to check all the stings I just didn't even notice that setting. I have come a long way now though. I fell at home in Ubuntu and can't stand window$ now:)

As for the dim thing.... That bug I just can't handled. Even after I turn the brightness back up it is still never as bright as it is in Gusty. I am sticking with Gusty 7.10 until it is fixed. HOWEVER, I keep telling myself I am going to compel my own Kernel but never do. If you compile the Kernel version that is in this version of Ubuntu and use it in 8.04 you will not have the dim problem. That bug is in the Kernel according to launchpad and it is in all 64bit distors that use the newer Kernel. Makes scents that it is a Kernel bug. The Kernel controls the hardware.

---

### Post by pwtico on 2008-05-17
> **Zetheroo said:**
> The thing about the brightness/dimness issue that is most annoying is the fact that the screen dims when it should brighten and brightens when it should dim.
This means that when you are battery power your screen brightens to max automatically instead of dimming. Likewise when you are operating on AC power the screen dims automatically. 
This is really annoying!!! -- Glad to know that its being looked into...

pwtico: Do you have a Y510 with Nvidia graphics?

HunterThomson: I will try changing the channel on the sound panel... 

Hammondman: Compiz worked out-of-the-box for me with Hardy -- been pretty stable...

UPDATE: HunterThomson -- that fixed it!!! Thanks a million!
No-- I have the Intel X3100 integrated graphics.

The screen is all the way dim on boot, which is annoying, but I think I'll live with it for now.

---

### Post by Zetheroo on 2008-05-18
pwtico: you have the X3100 Intel Graphics and your webcam is working properly????? 

How can this be?
:confused:

---

### Post by JSuresh on 2008-05-19
Hi, I've tried ubuntu 8.04 on an old hp laptop, and I'd like to turn my ideapad into a linuxbox, but I'm scared of some of the problems that have been discussed.

Just wondering, what are the final problems that have not been solved with putting hardy on the y510? (e.g. screen dimness, etc.)

---

### Post by pwtico on 2008-05-19
It seems the webcam works with the 64-bit 8.04, but not the 32-bit.  With my 64-bit system, the webcam worked out-of-the-box with Cheese and Skype.

Jsuresh--the only remaining issue I have is the reversed screen brightness issue.  The integrated Intel graphics card has some issues with Google Earth and Miro, but this is a documented issue that is not limited to the Y510.

---

### Post by wyth on 2008-05-19
Hey y'all,

Here's something that may help with the brightness issue.  It won't change the reversed buttons, but it helps set some brightness settings right.

In Gconf, you'll want to go to 

/apps/gnome-power-manager/backlight

In there you'll see a number of different settings.  Since the settings are all backwards, just change the numbers to the opposite end of the spectrum.

I've attached a screengrab of what I set mine at, and it works pretty well.

---

### Post by snktagarwal on 2008-05-22
Hey pple out there..... i installed the ALSA drivers..... but was unable to get the sound working after restart..... but when i ran gstreamer... i got test sound for ALSA under ALC883 analog and NOT default.... but i am a newbie so have no idea what that alsalink device="hw:1,0" means to the system.... also my Movie Player has failed to respond to the device.... ny ideas how we can debug with gstreamer properties????

---

### Post by HunterThomson on 2008-05-23
> **snktagarwal said:**
> Hey pple out there..... i installed the ALSA drivers..... but was unable to get the sound working after restart..... but when i ran gstreamer... i got test sound for ALSA under ALC883 analog and NOT default.... but i am a newbie so have no idea what that alsalink device="hw:1,0" means to the system.... also my Movie Player has failed to respond to the device.... ny ideas how we can debug with gstreamer properties????

If you don't have LEF and such in the mixer then click on settings and configure or whatever and then go through the list and check all the boxes. Then in the mixer you should see all of the volume bars. Unmute LEF etc... and turn up all the volume to the top on all. Then click on the switches TAB and select ch6 in the channels settings. Also, tick the box for IEC958 in the switches TAB.

---

### Post by HunterThomson on 2008-05-23
> **wyth said:**
> Hey y'all,

Here's something that may help with the brightness issue.  It won't change the reversed buttons, but it helps set some brightness settings right.

In Gconf, you'll want to go to 

/apps/gnome-power-manager/backlight

In there you'll see a number of different settings.  Since the settings are all backwards, just change the numbers to the opposite end of the spectrum.

I've attached a screengrab of what I set mine at, and it works pretty well.

Hey, Mahalo WYTH. Dose this really fix the problems? The thing that really pissed me off was that whenever I turned on VLC player or a game the brightness turned down. If I here that this works I think I will upgrade to Hardy 8.04.... I have been looking into Gentoo lately. This has been a grate help to learn Linux. Ubuntu is almost to EZ. With Gentoo one has to set up everything so he/she knows how it is all set up and works together. However, I guess I can just set up Ubuntu.

((FYI JSuresh:This is only a problem with 8.04. There is no problem with brightness on 7.10))

---

### Post by dbera on 2008-05-23
Here is my investigation and workaround:

- acpi video module is screwed up
/sys/devices/virtual/backlight/acpi_video1/*brightness values are all reversed. It should be 8 for brightest but it actually is 0 for brightest.

- adding "options video no_automatic_changes=0" to /etc/modprobe.d/options make kernel handle all the brightness changes

- of course now with both kernel and software (kde/gnome power managers) handling brightness changes, it will be a mess, so find guidance-power-manager/powermanage.py and disable the method adjustBrightness (this disables software controlling of brightness)

- enabling kernel control has another benefit: the brightness switch also works in console mode, or before login

- since the acpi values are fundamentally reversed, the default brightness levels after booting, after login and after logout will be set to '8' which is sadly the dimmest value for Y510. So, use rc.local and .kde/Autostart scripts to force the right brightness levels.

Thanks to all the previous persons who gave me the lead to this diagnosis.

---

### Post by Imre Mehesz on 2008-05-23
hello,

I just got this laptop and after 15 minutes of playing with Vista I installed Ubuntu 8.04 on it. I'm loving it! awesome! everything worked out of the box. (brightness backwards , though . etc.... ) but my biggest concern is the web camera...

has anybody had any luck to make the webcam thing to work finally?

!!! Linux rulZ !!!

thanks
iM

---

### Post by HunterThomson on 2008-05-24
> **Imre Mehesz said:**
> hello,

I just got this laptop and after 15 minutes of playing with Vista I installed Ubuntu 8.04 on it. I'm loving it! awesome! everything worked out of the box. (brightness backwards , though . etc.... ) but my biggest concern is the web camera...

has anybody had any luck to make the webcam thing to work finally?

!!! Linux rulZ !!!

thanks
iM

You can install the 64bit Ubuntu and then you will have no web cam problems.

---

### Post by HunterThomson on 2008-05-24
> **dbera said:**
> Here is my investigation and workaround:

- acpi video module is screwed up
/sys/devices/virtual/backlight/acpi_video1/*brightness values are all reversed. It should be 8 for brightest but it actually is 0 for brightest.

- adding "options video no_automatic_changes=0" to /etc/modprobe.d/options make kernel handle all the brightness changes

- of course now with both kernel and software (kde/gnome power managers) handling brightness changes, it will be a mess, so find guidance-power-manager/powermanage.py and disable the method adjustBrightness (this disables software controlling of brightness)

- enabling kernel control has another benefit: the brightness switch also works in console mode, or before login

- since the acpi values are fundamentally reversed, the default brightness levels after booting, after login and after logout will be set to '8' which is sadly the dimmest value for Y510. So, use rc.local and .kde/Autostart scripts to force the right brightness levels.

Thanks to all the previous persons who gave me the lead to this diagnosis.

So, this works... for real? I don't want to upgrade until I get ,reiteration, confirmation. 

Good, work by the way. I knew it was just a madder of diving into .config files and changing settings. I find it hard to pull my self away form illegally downloaded movies though.

---

### Post by snktagarwal on 2008-05-24
just see this page if woofers are not workin' out [http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)

---

### Post by dbera on 2008-05-24
> **HunterThomson said:**
> So, this works... for real? I don't 
want to upgrade until I get ,reiteration, confirmation.

As I said, the acpi driver is messed up. So applications which directly use acpi interface will do it reverse (e.g. kaffeine will dim when asked to play a movie). What we (users) _can_ control is the brightness levels after bootup, after login, when the up/down is pressed etc. These are mostly scripts or commands, so setting the brightness in those scripts can work as a valid workaround.

If someone is not bothered by the default brightness levels and only worried about the up-down reversal, then an even easier workaround is to just swap 101 and 212 (XF86LaunchD and XF86LaunchE) in system ubuntu.xmodmap and the up-down keys will work as expected.

Edit: Oh ... and my past experience about Ubuntu with respect to getting bugs fixed is not very good. If someone knows how to get bugs fixed, please see that the acpi video interface backlight levels for ideapad y510 is fixed to be in the correct order. You can just check the /sys/devices/virtual/backlight/acpi_video1/brightness that the brightness levels are reversed. I think its a bug in acpi.

---

### Post by dbera on 2008-05-24
And now a little bit of sound related update. This is with a fresh Hardy install.

Add to /etc/modprobe.d/alsa-base (without quotes):
"options snd_hda_intel model=3stack-6ch"

The model should be 3stack-6ch and not lenovo-ms7195-dig if you care about all the 6 channels.

Reboot (generally there is a way to restart alsa but rebooting is safer).

After reboot, go to console mode (ctrl-alt-f2), login, then open alsamixer. unmute PCM, Master, Surround, LFE and Center and crank them up for testing. Then test using,

$ speaker-test -Dplug:surround51 -c6 -twav
you should hear distinct sounds on all the 6 channels.

If success, login to KDE/Gnome and enjoy.

---

### Post by HunterThomson on 2008-05-24
Well... it's Linux right? 

There has to be a way to switch the acpi that was used in 7.10 with the one used in 8.04....

Bugs are reported on launchpad

---

### Post by Imre Mehesz on 2008-05-24
hello,

thanks for the advice. it's working now, however it is upside-down. (btw, it's very interesting that everything seems to be backwards with lenovo, i mean the brightness and the video) 

maybe I'm doing something wrong? is there a workaround for the webcam?

thank you again,
iM

---

### Post by dbera on 2008-05-25
> **HunterThomson said:**
> Well... it's Linux right? 
There has to be a way to switch the acpi that was used in 7.10 with the one used in 8.04....

If you are willing to understand and edit source and compile kernel, then there should be a way yes. I am not, so unless the package is fixed, its not fixed for me.


> Bugs are reported on launchpad

Reporting is easy, but somehow it takes longer for the bugs to be fixed, even acknowledged, than other distributions. Thats my experience. If someone wants to file a bug, please go ahead and do so. Maybe it will get fixed by 8.04.1

---

### Post by HunterThomson on 2008-05-25
> **dbera said:**
> If you are willing to understand and edit source and compile kernel, then there should be a way yes. I am not, so unless the package is fixed, its not fixed for me.

Well... Sounds like a rewarding experience.... I think I'll spend some time and at lest find out what it would take to do it.  Certainly a better use of time then watching movies:)


[/QUOTE]Reporting is easy, but somehow it takes longer for the bugs to be fixed, even acknowledged, than other distributions. Thats my experience. If someone wants to file a bug, please go ahead and do so. Maybe it will get fixed by 8.04.1[/QUOTE]

OK, have never done it. Although I find it vary strange that things brake in updates and upgrades i.e. brightness and at one point in the 8.04 Beta Compiz worked with the intel GPU with no problem.

---

### Post by polluxx on 2008-05-26
Re dbera's extensive brightness/dimness research:

> 
- since the acpi values are fundamentally reversed, the default brightness levels after booting, after login and after logout will be set to '8' which is sadly the dimmest value for Y510. So, use rc.local and .kde/Autostart scripts to force the right brightness levels.


I'm not so sure whether the values are simply reversed. Both 
```

/sys/devices/virtual/backlight/acpi_video1/brightness
/sys/devices/virtual/backlight/acpi_video1/actual_brightness

```
give a value of 0 after login, which is obviously incorrect. However
```

/sys/devices/virtual/backlight/acpi_video1/max_brightness

``` 
gives a value of 8, which is "sort of" correct: The reason why it is not quite correct is that, 
```

 /proc/acpi/video/VGA/LCDD/brightness

```
gives a maximum value of 10, which if one types
```

echo 10 > /proc/acpi/video/VGA/LCDD/brightness

```
indeed results in an even brighter screen. So no reversal of brightness levels in this case.


> 
If someone is not bothered by the default brightness levels and only worried about the up-down reversal, then an even easier workaround is to just swap 101 and 212 (XF86LaunchD and XF86LaunchE) in system ubuntu.xmodmap and the up-down keys will work as expected.


I don't think changing anything with xmodmap will result in reversed brightness buttons: I fiddled around with the acpi scripts in /etc/acpi/events/video_brightness*, swapping the scipts associated with the individual key events did not result in proper behaviour of the brightness/dimness keys. For some reason, those scripts (even though they seem to be executed according to acpi_listen) seem to be ignored. 
My opinion right now is that those key events are hardwired (and therefor do natively work in the text consoles) and are being taken care of in Xorg via the proprietary nvidia drivers. This apparently is also the case for many of the Thinkpad Notebooks.
Also, how would you go ahead and "swap" the keys for brightness up/down with xmodmap: On my machine according to xev the keys [Fn]+[Up] and [Fn]+[down] correspond to keycode 101 and 212 (as dbera stated). However xmodmap doesn't map those events to any keysyms. So my question is, which keysyms from /usr/share/X11/XKeysymDB are you mapping to those codes?


> 
- enabling kernel control has another benefit: the brightness switch also works in console mode, or before login

Even without "no_automatic_changes=0" parameter, the brightness keys do work from within the VTs. This again indicates that the brightness control is hardwired, and does not listen to acpi key events.


Also, and just for the record: The upside-down webcam issue can **not** be solely attributed to the 32bit version. I am running the Hardy 32bit version, and my webcam worked out of the box, no upside-down image or tweaks.

---

### Post by dbera on 2008-05-26
> I'm not so sure whether the values are simply reversed. Both 
```

/sys/devices/virtual/backlight/acpi_video1/brightness
/sys/devices/virtual/backlight/acpi_video1/actual_brightness

```
give a value of 0 after login, which is obviously incorrect. However
```

/sys/devices/virtual/backlight/acpi_video1/max_brightness

``` 
gives a value of 8, which is "sort of" correct

The max value is correct but not the brightness value exported by sysfs. The latter is reversed.

> 
I don't think changing anything with xmodmap will result in reversed brightness buttons

I didnt use this approach so I could only guess. I claim that swapping 101 and 212 in ubuntu.xmodmap (I forgot where that file is right now) would work.

> I fiddled around with the acpi scripts in /etc/acpi/events/video_brightness*, swapping the scipts associated with the individual key events did not result in proper behaviour of the brightness/dimness keys. For some reason, those scripts (even though they seem to be executed according to acpi_listen) seem to be ignored. 


This is how the events happen:
press key ->
XF86LaunchE/D is generated (verified by xev) ->
(forgot this part) guidance-power-manager receives the dcop signal ->
powermanage.py sets the brightness using HAL org.freedesktop.Hal.Device.LaptopPanel ($lshal)

Its all in software. So I am guessing that swapping the keysyms in ubuntu.xmodmap will send the reverse dcop signals which should fix the reversal.

> My opinion right now is that those key events are hardwired (and therefor do natively work in the text consoles) and are being taken care of in Xorg via the proprietary nvidia drivers. This apparently is also the case for many of the Thinkpad Notebooks.
...Even without "no_automatic_changes=0" parameter, the brightness keys do work from within the VTs. This again indicates that the brightness control is hardwired, and does not listen to acpi key events.


Interesting. I have the intel video card based ideapad and on that by default the brightness switch does not work in vt before login (didnt test after login, it might work if kdesktop is running). If I add the "no_..." parameter _and_ disable power-manager to not adjust brightness, then everything works perfectly.

It could be that things are different for the NVidia based ideapads.

---

### Post by polluxx on 2008-05-26
> 
The max value is correct but not the brightness value exported by sysfs. The latter is reversed.

That is incorrect. The maximum brightness value as given in the sysfs corresponds to the true maximum brightness, as can be easily verified by echoing a value of 10 to
```

/sys/devices/virtual/backlight/acpi_video1/max_brightness

```
This, as I aldready pointed out, does result in a brighter screen (at least on my machine).

> 
This is how the events happen:
press key ->
XF86LaunchE/D is generated (verified by xev) ->
(forgot this part) guidance-power-manager receives the dcop signal ->
powermanage.py sets the brightness using HAL org.freedesktop.Hal.Device.LaptopPanel ($lshal)

Read: This is how events happen on KDE. The situation is different with Gnome, as D-Bus takes over DCOP's responsibilites. But as I pointed out already, on the event of a key being pressed, xev, acpi_listen and lshal -m recognize the event correctly and state the proper execution of the particular acpi scripts. So there is no problem there.

However, changing (or swapping) those scripts, does not change anything. That is why I believe changing keyboard mappings won't do a thing.
Again, those two keys (brightness up/down) might be hardwired, resulting in working keys during boot (which is the case on my nvidia 8600m gs y510) and apparently what seemed to be the case for a lot of thinkpads in the past.

---

### Post by dbera on 2008-05-26
> However, changing (or swapping) those scripts, does not change anything. That is why I believe changing keyboard mappings won't do a thing.
Again, those two keys (brightness up/down) might be hardwired, resulting in working keys during boot (which is the case on my nvidia 8600m gs y510) and apparently what seemed to be the case for a lot of thinkpads in the past.

In KDE it is not acpi controlled, but userspace controlled via guidance-power-manager. I read its 2 source python files to figure out what is happening. I might be wrong, but Ubuntu might also be using userspace gnome-power-manager to control the brightness; the acpi scripts would be useless in that case. The evidence for this is, the keys are registered correctly, (in KDE at least) the software gets the correct dcop/dbus call, (from the source file) the correct HAL method is called to set the brightness but due to 0 being 8 and 8 being 0, just the opposite thing happens.

The NVidia based ones seem to act differently (also it might be gnome too). If anyone using KDE on an Intel based Y510 requires detail steps, then I can provide them.

---

### Post by polluxx on 2008-05-26
Another question re the sound card issues:

> 
And now a little bit of sound related update. This is with a fresh Hardy install.

Add to /etc/modprobe.d/alsa-base (without quotes):
"options snd_hda_intel model=3stack-6ch"

The model should be 3stack-6ch and not lenovo-ms7195-dig if you care about all the 6 channels.

After the change to model=3stack-6ch, I'm unable to get the speakers to mute when using headphones. 
With the lenovo-ms7195-dig option I had to manually switch of Center and LFE (which corresponded to the subwoofer) when using headphones, the other speakers did mute automatically. Now with the 3stack-6ch model regardless of which channel I manually switch off the speakers never mute.

Dbera, could you tell me whether you experienced the same problem, and if not, what you did to get them muting.

---

### Post by Lenny_955 on 2008-05-27
Hi everyone, and thank you for these posts. I have a Y510 laptop, with nvidia 8400 inside. And I do have the same problem with brightness. Not a big issue, bug thanx anyway.

I do have another problem, with the "fan control".
lmsensors do not seem to detect any usable fan to monitor. The module "fan" is loaded, but no dataare displayed concerning any fan.

As a result (or rather : I think it's related) : the fan is always on, but not fast. Not fast enough fo cool the video card when using it, and too much when the laptop is nearly idle.

Has anyone observed the same phenomenon ?

---

### Post by wyth on 2008-05-27
Can I just say you guys rock?  I've been very busy with some other work since the end of the semester (I'm a grad student), and have only had time to follow this thread, but not enough to really implement much of what you've found.  I'm amazed at what you've come up with so far, and I want to take what you've done here back to the Lenovo forums and let their people know.  (I posted over there about how well Gutsy worked on the Y510, and one of the Lenovo people wrote me back asking for some more updates -- maybe, just maybe, if enough can be reported back, they'd consider some support for Ubuntu, since the Thinkpads now support Suse.)

I recently did a clean install and had sound issues.  I know someone reported earlier that Hardy came with a new enough ALSA driver and they didn't have download and compile, but I couldn't get that to work.  However, going through the same process I posted earlier (downloading and compiling), and setting the channel options to 6ch, oh wow does it sound nice.

I'm looking forward to working out the dimness issue, and maybe hopefully someday the camera issue.  My sense is the Y510 could be a fantastic little Ubuntu machine, if not for just a few easily tweaked issues; but it also seems it's up to the community to get those issues ironed out (and I'm okay with that).

---

### Post by dbera on 2008-05-27
> **polluxx said:**
> 
After the change to model=3stack-6ch, I'm unable to get the speakers to mute when using headphones. 
With the lenovo-ms7195-dig option I had to manually switch of Center and LFE (which corresponded to the subwoofer) when using headphones, the other speakers did mute automatically. Now with the 3stack-6ch model regardless of which channel I manually switch off the speakers never mute.

Dbera, could you tell me whether you experienced the same problem, and if not, what you did to get them muting.

Good point. They don't mute :confused:
The ms7195-dig model was using only 4 channels (I think they were skipping the rear channels) so I used the 3stack-6ch model to watch a 5.1 dolby DVD. But I never noticed that the headphone jacks do not mute the speakers.

We might need a hybrid of ms7195 and 6ch to get this completely fixed :-)

Edit: Spotted this launchpad bug for headphone not muting for Realtek codecs. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109838](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/109838)

---

### Post by astranberg on 2008-05-28
Folks thought I might jump in here, I just got my new y510, the nvidia 8600 model.  Seems to have all of the same issues you folks have been beating down.  Inverted video, reversed controls for screen dimming, and very low speaker volume which I guess may be the lack of a sub woofer. Other than that runs perfect!   Wanted to shout out a big thanks to the folks that have been putting the research into this.  I've just tried adding "options snd-hda-intel model=3stack-6ch" to alsa-base however the sounds is still only about 60% of what I get when I boot into vista listening to the same cd.  I also set alsamixer to max on all sliders for speakers master/pcm/front/surround/center/lfe and pc speaker, and configured for 6ch above chanel. I should mention this is the 64bit ubuntu 8.04 version. Anything I missed that should be set?

---

### Post by Zetheroo on 2008-05-28
Has anyone formally reported any Ideapad related bugs in launchpad?

---

### Post by Gruu on 2008-05-28
First off, thanks to everyone for this amazing thread - you guys rock! My laptop now has better sound than my desktop ;).

I'm having some problems with Hibernating, and I don't think I have an nvidia card (see lspci output below). Here's some output that might help:

This is the output of dmesg after a successful hibernate/resume (it's kind of big, so I put it on pastebin):

[http://pastebin.com/mf212da2](http://pastebin.com/mf212da2)

And this is the output after an unsuccessful hibernate:

[http://pastebin.com/m2edf3b72](http://pastebin.com/m2edf3b72)

Also, both times when I came back, my wireless didn't work properly, but toggling the physical on/off switch fixed it up nicely.

Here's the output of lspci:

```

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

Thanks!!

P.S. Is there an easy way to tell how old stuff in dmesg is? I'm never sure how much I need to save/post.

---

### Post by wyth on 2008-05-28
> **astranberg said:**
> I've just tried adding "options snd-hda-intel model=3stack-6ch" to alsa-base however the sounds is still only about 60% of what I get when I boot into vista listening to the same cd.  I also set alsamixer to max on all sliders for speakers master/pcm/front/surround/center/lfe and pc speaker, and configured for 6ch above chanel. I should mention this is the 64bit ubuntu 8.04 version. Anything I missed that should be set?

I don't know if this will help you or not, but after I did a clean install, I had to download and compile the latest ALSA drivers to get full sound.  I don't have Vista installed (I'm not dual booting), so I'm not sure if it's equal to what that gets you, but it is pretty full sound.

---

### Post by wyth on 2008-05-28
> **Gruu said:**
> I'm having some problems with Hibernating, and I don't think I have an nvidia card (see lspci output below).

Gruu, what's happening when you try to hibernate?  It looks like you have the same system I have, and I'm not having trouble (that I know of). Let us know what you see happening when you come out of hibernation, and we'll take it from there.  It might be a simple config file tweak; I remember reading up on them, but don't think I needed to enable it.

---

### Post by polluxx on 2008-05-28
> 
I'm having some problems with Hibernating, and I don't think I have an nvidia card (see lspci output below). Here's some output that might help:

This is the output of dmesg after a successful hibernate/resume (it's kind of big, so I put it on pastebin):

[http://pastebin.com/mf212da2](http://pastebin.com/mf212da2)

And this is the output after an unsuccessful hibernate:

[http://pastebin.com/m2edf3b72](http://pastebin.com/m2edf3b72)

Also, both times when I came back, my wireless didn't work properly, but toggling the physical on/off switch fixed it up nicely.

Could you also post
```

cat /etc/default/acpi-support

```

Btw, both dmesg files state
```

PM: Resume from disk failed

```
which is also the case on my machine with (nearly always) working hibernate/suspend. Quite odd.

Also, for the case of hibernate+resume failing, does your machine still boot? Dmesg states a filesystem recovery, so does that mean your notebook still boots up, however ignores the swap image?

[Edit] Also, can I assume your webcam is not working properly?

---

### Post by Gruu on 2008-05-29
Half the time, when I turn the computer back on after hibernating, it boots normally (as if I had shut it down) instead of resuming. When it works, 

Here's acpi-support:

```

$ cat /etc/default/acpi-support 

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12
```

I haven't tried to get the webcam working since I wouldn't really use it. Would the steps to fix the webcam help the hibernate problem?

Also, my wireless doesn't seem to work at all now when I come out of hibernation...it doesn't detect all the networks that are here, and it doesn't seem to be able to connect to my preferred network.

Thanks again!

---

### Post by polluxx on 2008-05-29
> 
Half the time, when I turn the computer back on after hibernating, it boots normally (as if I had shut it down) instead of resuming. When it works,

Your previous dmesg states
```

[ 1006.552733 ] PM: suspend-to-disk mode set to 'platform'

```
so I am a bit puzzled, as your acpi-support sets
```

HIBERNATE_MODE=shutdown

```
(and not "platform"), and which seems to be ignored. I checked my machine after a hibernate+resume, same thing. However, on my machine hibernation works very stable. (There seems to be a bug report on that issue already).

The only difference between your acpi-support and mine is the following entry
```

SAVE_VBE_STATE=false

```
which defaults to true, as is the case on your machine. It might be worth changing that value and reporting back on the results.

Also, to summarize, my experience with the whole Suspend/Hibernate process is pretty much as follows:

1. Suspend (to RAM) seems to be generally less stable, maybe 1 out of 10 resume instances result in a dark screen, with the LEDs on. The only way out is a hard reset. Other than that, it works flawlessly, with the tweaks described in the next section.

2. Hibernate is more stable, I followed basically the instructions on [[COLOR="Blue"]_this page_[/COLOR]]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"), with the only (but important) difference, that I had to set (keep)
```

POST_VIDEO=true

```
otherwise suspend would not work (hibernate seemed to be unaffected).

3. I also tried the userspace suspend uswsusp, which is supported by the routines in pm-utils. However it seems that s2ram has been discontinued and replaced by s2both, which is basically a (long) suspend+hibernate shutdown, followed by a (short) resume from a RAM image (or from the swap partition if your battery runs flat during the sleep mode). It's definitely safer but also slower than a normal suspend. Hibernate (s2disk) worked pretty much out of the bocks, no quirks, hooks, tweaks necessary. Might be worth giving it a shot as well and seeing how it compares.


Also, the reason why I mentioned the webcam was more out of curiousity, since dmesg states
```

uvcvideo: Found UVC 1.00 device Lenovo Easy Camera (5986:0200)
uvcvideo: Failed to query (1) UVC control 2 (unit 0) : -110 (exp. 26).
Failed to initialize the device (-5)

```
So I expect the camera to not work properly on your machine, which is odd since the model (5986:0200) is listed as fully supported on the [[COLOR="Blue"]_UVC video page_[/COLOR]]("http://linux-uvc.berlios.de"). My camera with deviceID 046d:09b6 is not even listed, however works without upsidedown troubles.

Re your wireless issue: Include your wireless module (on my machine it is iwl4965) in the file /usr/lib/pm-utils/defaults as
```

SUSPEND_MODULES="iwl4965"

```
and see if that changes anything.

---

### Post by astranberg on 2008-05-29
Anyone else attempted the xen kernel on the y510 laptop?  I managed to get the kernel working, nvidia drivers seem to be complicated but it works with out the acceleration.  I haven't seen an obvious way to enable VT which seems to be a requirement to get windows running under xen.  Any advice/suggestions?

Thanks
-A

---

### Post by astranberg on 2008-05-29
Well I just answered by own question according to [http://www.intel.com/products/processor_number/chart/core2duo.htm](http://www.intel.com/products/processor_number/chart/core2duo.htm) the t5550 does not support VT!  Wonder if its too late to send this back and get the y710? I can't believe I over looked that, guess I will go back to vmware.

-Aaron


> **astranberg said:**
> Anyone else attempted the xen kernel on the y510 laptop?  I managed to get the kernel working, nvidia drivers seem to be complicated but it works with out the acceleration.  I haven't seen an obvious way to enable VT which seems to be a requirement to get windows running under xen.  Any advice/suggestions?

Thanks
-A

---

### Post by polluxx on 2008-05-30
Has anyone else looked into this issue:
[[COLOR="Blue"]_Test If Your Laptop Drive Is Going To Die Prematurely - Please Read All Laptop Users_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=795327&highlight=y510"). The Y510 is also listed as an affected machine.

There is a lot of information on the net, for ubuntu you can read [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=591503") and [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5031046").

I read about it yesterday, tested the load_cycle_count and also found that thecount on my harddrive increases by about 2 per minute.

I have never heard about this issue being (apparently) so severe before, and I've been using various Linux distribution over the last couple of years.

Did anyone attempt to fix this on their Y510 machines?

---

### Post by Gruu on 2008-05-30
polluxx:

First I just tried modifying VBE_STATE, but that didn't seem to help. Now, when I try to hibernate, it just hangs (screen is black, but it doesn't turn off...I've waited for >5 minutes with no luck). I have to manually power down and restart, and when I restart, there's no attempt to resume. I used to have this problem a lot back in Gutsy; that's when I gave up on hibernating.

Here's dmesg after that happens:

[http://pastebin.com/m160a363f](http://pastebin.com/m160a363f)

Adding the "NvAGP" "1" option to xorg.conf didn't help either, but I don't think I have an nvidia card (see lspci above). 

Any suggestions? Thanks again for all the help.

---

### Post by polluxx on 2008-05-31
@Gruu:

Ok, so if you set
```

SAVE_VBE_STATE=true

```
you're stuck again with the erratic (original) resume behaviour?
You could also try setting
```

POST_VIDEO=true

```
although, on my machine that seemed to screw up suspend to RAM.

Another option would be to install the uswsusp package (which is supported by pm-utils), and check whether s2disk is more stable.

If that fails too, you might considering patching your kernel to include suspend2 (it's called tuxonice now I think). I was running hibernate via suspend2 for years very successfully and stable on my old Debian machine, it's probably one of the most stable hibernate methods, imho. The only hassle would be that you'd need to (re)compile your kernel (which is actually quite easy on Debian machines + derivatives).

---

### Post by arvast on 2008-05-31
This thread has made my life so much easier :)

Sound is working better and sounds better than ever before, webcam and all is going great too. The brightness problem is somewhat under controll, not that big of a deal ^^

BUT!

I noticed that I have major graphics problems :/ I have Intel 965GMA but cant even play Tux Racer (its my 3D test program :P) usually desktop blinks into game and/or its really laggy.

I looked around a little bit but I cant find much, is it a bug? Or do I have to compile my own drivers?

Also I cant get s-video working, so if anyone knows how to do this that would be great :D

---

### Post by Zetheroo on 2008-06-02
Sorry if this is just repetitive ... but could someone spell out what has been the best workaround for he brightness/dimness issue with the function keys and the screen dimming when video playback has begun?

Thanks:KS

---

### Post by arvast on 2008-06-02
> **Zetheroo said:**
> the screen dimming when video playback has begun?

Thanks:KS

I have noticed that VLC and mplayer both dims. But totem player doesnt :D

Its not the best player. But its the best workaround so far.. for me ._.

---

### Post by Blaque on 2008-06-02
> **polluxx said:**
> Has anyone else looked into this issue:
[[COLOR="Blue"]_Test If Your Laptop Drive Is Going To Die Prematurely - Please Read All Laptop Users_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=795327&highlight=y510"). The Y510 is also listed as an affected machine.

There is a lot of information on the net, for ubuntu you can read [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=591503") and [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5031046").

I read about it yesterday, tested the load_cycle_count and also found that thecount on my harddrive increases by about 2 per minute.

I have never heard about this issue being (apparently) so severe before, and I've been using various Linux distribution over the last couple of years.

Did anyone attempt to fix this on their Y510 machines?

I fixed it using the following post.

[http://ubuntuforums.org/showpost.php?p=4897802&postcount=842]("http://ubuntuforums.org/showpost.php?p=4897802&postcount=842")

However I understand that this solution makes it easier for your hard disk to be damaged by a bump or fall. I've read as much as I could and don't see an idea fix for it yet.

---

### Post by Zetheroo on 2008-06-02
> **polluxx said:**
> Has anyone else looked into this issue:
[[COLOR="Blue"]_Test If Your Laptop Drive Is Going To Die Prematurely - Please Read All Laptop Users_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=795327&highlight=y510"). The Y510 is also listed as an affected machine.

There is a lot of information on the net, for ubuntu you can read [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=591503") and [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5031046").

I read about it yesterday, tested the load_cycle_count and also found that thecount on my harddrive increases by about 2 per minute.

I have never heard about this issue being (apparently) so severe before, and I've been using various Linux distribution over the last couple of years.

Did anyone attempt to fix this on their Y510 machines?

Thanks for giving us a heads-up about this. I had heard of this issue before when running Gutsy and fixed it there.

Now I did the test on both my IdeaPad Y510 and T60 Thinkpad to find out if I was effected, and sure enough both were clocking about 120 - 150 cycles every 15 min.

I repaired it on both machines (running Hardy) with the following fix:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14")

---

### Post by Hammondman on 2008-06-03
Ok, sweet I did the "options snd_hda_intel model=3stack-6ch" and finally have all channels going.  But headphones... when I put them in they don't mute ANY of the channels. I have to mute everything manually, but then I don't get any sound in the headphones!  Anybody figured this out yet?

Thanks!

---

### Post by dbera on 2008-06-03
> **Hammondman said:**
> Ok, sweet I did the "options snd_hda_intel model=3stack-6ch" and finally have all channels going.  But headphones... when I put them in they don't mute ANY of the channels. I have to mute everything manually, but then I don't get any sound in the headphones!  Anybody figured this out yet?

AFAIK, no. There are lots of bugs opened about "jack sense" for realtek cards/alsa in general. You either use 3stack-ch and get 5.1 audio but loose jack sense or use the lenovo-ms... model and get jack sense but loose the 5.1 audio (the 3rd option is to file a bug with alsa but I havent had the time to file a bug and provide the necessary information :-).

---

### Post by HunterThomson on 2008-06-05
> **Zetheroo said:**
> Thanks for giving us a heads-up about this. I had heard of this issue before when running Gutsy and fixed it there.

Now I did the test on both my IdeaPad Y510 and T60 Thinkpad to find out if I was effected, and sure enough both were clocking about 120 - 150 cycles every 15 min.

I repaired it on both machines (running Hardy) with the following fix:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14")

Just to speed up the learning prosses for everyone. 

Your hdd has a arm that moves and reads data.. This arm has a ramp that it parks on to protect your hdd form you shaking it and that arm hitting the disk. The hatattchi hdd time to park is way to short.

The cycal count is how "they" judge the age of your harddrive.
The cycal decreses by 1 every time the arm unparks.

I read about this for a long time. The "FIX" you are talking about is not a fix. What you are doing is stopping the harddirve form seating. This is also not just a problem with Linux it is a problem with Hatatchi. That first thread quoted is now marked SOLVED so I would check the last 10 pages for the  fix. What they were trying to do was lengthen the time to seat.

---

### Post by HunterThomson on 2008-06-05
As for the not suspending thing. I have no problem with my 7.10:).... Well between that and the dim problem I am staying with Ubuntu 7.10... I would suggest the same to all of you.. But hay it is your computer:)

---

### Post by Zetheroo on 2008-06-06
> **HunterThomson said:**
> Just to speed up the learning prosses for everyone. 

Your hdd has a arm that moves and reads data.. This arm has a ramp that it parks on to protect your hdd form you shaking it and that arm hitting the disk. The hatattchi hdd time to park is way to short.

The cycal count is how "they" judge the age of your harddrive.
The cycal decreses by 1 every time the arm unparks.

I read about this for a long time. The "FIX" you are talking about is not a fix. What you are doing is stopping the harddirve form seating. This is also not just a problem with Linux it is a problem with Hatatchi. That first thread quoted is now marked SOLVED so I would check the last 10 pages for the  fix. What they were trying to do was lengthen the time to seat.

I am well aware of how this hdd parking system works (or is supposed to work).. but thanks for the review.
I recently found out that GNU/Linux does NOT work with the technique implemented by ThinkVantage and other laptop brand name utils which allow the head to be parked whenever there is a jolt or sudden jerky movement. So this was quite a striking realization to me... and definitely a con in my books for using Linux in a mobile environment.

I have now implemented a different fix which I have placed on my website ([LINK]("http://fsrc.freehostia.com/hddcyclecount.html")).

This works better, but still nowhere as good as the ThinkVantage tools.

---

### Post by astranberg on 2008-06-07
So I have re-read this forum several times now and it seems that some folks have over come this upside down webcam issue, but I keep overlooking the fix.  I am on 64bit 8.04 with the nvidia graphics chip set, whats the secret to correcting this one, other than the flip video button in cheese :)

By the way my sounds is now working great with LFE and surround thanks to Wyth and others on here!

Thanks!

---

### Post by Zetheroo on 2008-06-07
From what I have gathered the issue with the webcam has not been "solved", instead it seems that on a case-by-case basis some people have had it working from the start, whereas others do not.

:KS

---

### Post by HunterThomson on 2008-06-07
> **astranberg said:**
> So I have re-read this forum several times now and it seems that some folks have over come this upside down webcam issue, but I keep overlooking the fix.  I am on 64bit 8.04 with the nvidia graphics chip set, whats the secret to correcting this one, other than the flip video button in cheese :)

By the way my sounds is now working great with LFE and surround thanks to Wyth and others on here!

Thanks!

Ya, I don't know what the deal is with the web cam thing:confused:

It works fine with my computer. I don't do anything. It "Just Works" upright and everything. At first I thought it was because I use the 64bit and everyone ells was using the 32bit. But I guess if you are on 64bit and the cam is upside-down then I just don't know. 

I also thought that the dim was only problem with the 64bit 8.04 because Wyth said he is on 32bit 8.04 and doesn't have a dim problem:confused: But others with 32bit do...

---

### Post by ec10415 on 2008-06-09
thank you wyth n gomez...got everything up n running on my lenovo y510.. webcam is working with cheese and skype..no inverted screen problems..i'm on gutsy..:) i installed hardy on another desktop computer but encountered a problem and did the workaround..so that is up and running..planning on sticking to gutsy for now on my lenovo..:)

---

### Post by astranberg on 2008-06-16
Hey Folks,
   Thought I might try posting this here since you have all been so helpful.  Since XEN isn't supported by the t5550 processor I have turned back to vmware server.  Now I am seeing extremely frequent x crashes when switching between vmware console and the desktop or other applications such as firefox.  This seems to be much more frequent when I have more than 1 VM running at a time.  If one of the guru's on here can glance at the dmesg output below and point me in the right direction I would be most grateful.

y510 - ubuntu 64bit 8.04 - 4GB mem, nvidia card, nvidia driver

[  471.807878] CPU0 attaching sched-domain:
[  471.808070]  domain 0: span 03
[  471.808294]   groups: 01 02
[  471.808500]   domain 1: span 03
[  471.808712]    groups: 03
[  471.808896] CPU1 attaching sched-domain:
[  471.809080]  domain 0: span 03
[  471.809258]   groups: 02 01
[  471.809464]   domain 1: span 03
[  471.809666]    groups: 03
[  472.888769] Monitor-Mwait will be used to enter C-2 state
[  535.768347] vmmon: Had to deallocate locked 87237 pages from vm driver ffff81010b4b0000
[  535.778826] vmmon: Had to deallocate AWE 4702 pages from vm driver ffff81010b4b0000
[  535.901454] vmmon: Had to deallocate locked 122244 pages from vm driver ffff81013716e000
[  535.910124] vmmon: Had to deallocate AWE 5142 pages from vm driver ffff81013716e000
[  535.924554] /dev/vmmon[7042]: host clock rate change request 83 -> 0
[  535.941573] vmmon: Had to deallocate locked 89380 pages from vm driver ffff810114ebc000
[  535.950717] vmmon: Had to deallocate AWE 5086 pages from vm driver ffff810114ebc000

---

### Post by wyth on 2008-06-16
I don't know if this will be of any help (because I just started doing some virtual machine work myself this past week), but I had no luck with vmware.  Virtualbox, however works great.  There's no problem with setup, very little adjustment afterwards, it's lighter/smaller, and less of a hit on the cpu.

The open source virtualbox is in the repositories under virtualbox-ose.  However, it comes a little limited -- like getting USB keys to work. Sun Microsystems just bought the virtualbox company, and they provide a full-featured deb of virtualbox for 8.04.

For general info on VirtualBox, see the [Ubuntu Community Help page here]("https://help.ubuntu.com/community/VirtualBox")
For help getting USB to work, see [here]("http://danmarner.blogspot.com/2008/06/installing-virtualbox-162-on-ubuntu-804.html")
For the Sun download, see [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by Zetheroo on 2008-06-17
Indeed, Wyth, VirtualBox is where its at with VM's in Ubuntu Hardy. I have been using the Sun xVM version and it has been an absolute breeze to use, with USB and all....

for all those interested in the Sun xVM release : [LINK]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

### Post by astranberg on 2008-06-19
Interesting info on Virtualbox, thanks for the suggestion I am downloading it now.  On my vmware server crash issue, it seems to be related to the nvidia driver.  When I disable the driver my system is once again rock solid.  I did some research and saw a few people suggesting that I role back the driver to an earlier version to correct the issue.  I think I will try out VirtualBox and see if the crashes persist before I role back (I hate going backwards) .

-Aaron

---

### Post by Vinchester on 2008-06-21
Hi guys, I'm the new kid on the block :popcorn:

I recently bought Y510 with GF8600, and so far have been very happy with it minus the overly glossy screen. I'm yet trying to find my way around Ubuntu. (I downloaded drivers but how can I install them???) here's my finding so far,

-I use Cheese and my cam is 100% working. not upside-down or anything.
-the very common sound&brightness issues are there :(

I'm studying how terminal works to get things done, but am somewhat intimidated by the notion of typing too many lines of code in it.

---

### Post by HunterThomson on 2008-06-22
> **Vinchester said:**
> Hi guys, I'm the new kid on the block :popcorn:

I recently bought Y510 with GF8600, and so far have been very happy with it minus the overly glossy screen. I'm yet trying to find my way around Ubuntu. (I downloaded drivers but how can I install them???) here's my finding so far,

-I use Cheese and my cam is 100% working. not upside-down or anything.
-the very common sound&brightness issues are there :(

I'm studying how terminal works to get things done, but am somewhat intimidated by the notion of typing too many lines of code in it.

Aloha,

Don't worry about the terminal... You will learn as you go but having the "Linux Phrasebook" around has helped me out a lot and only $15.

For the sound...The guide on page 2 works (cut and past) and look for my posts in the last 5-6 pages for what settings to change in the sound mixer GUI.

((Really, You already have the new alsa-driver/lib/utils installed so all you need to do is type this in the terminal:

sudo nano /etc/modprobe.d/alsa-base

then add this to the end of the file:

options snd-hda-intel model=lenovo-ms7195-dig

{hold ctrl and press X to exit then Y to save}

restart

The adjust the setting in the sound mixer GUI>> look at my posts here))

The only fix that I know of for the brightness is to use Gusty 7.10 instead of the new Hardy 8.04. But the chose is up to you... 7.10 is secure and supported but 8.04 has the newer Gnome/KDE and other programs.

---

### Post by HunterThomson on 2008-06-22
_**Arch Linux x86-64 Is A GO**_

I installed Archlinux yesterday here is Hard Ware support info:

Intel GPU works out of box

Intel Wireless works out of box

BroadCom Ethernet works out of box

Back Light >>> NO Problem with dim:)

Sound works after adding 

options snd-hda-intel model=lenovo-ms7195-dig

to /etc/modprobe.conf


The hardware media buttons are not working but they will when I set them up:)

Have not tried the web cam but I am under the impression that everything works because you install and set up whatever you want however you want.

All in all, none of the problems like I had with Ubuntu and best of all it is a "rolling distro" I am through with distro upgrades braking things and if a program up grade brakes something I can just roll that one program/lib back:) However, Don't use if you are new to Linux. Use Ubuntu and then move to Arch:)

---

### Post by loopyoyo on 2008-06-27
just checking to see if anyone has came up with a solution to getting the headphone auto-sense working with "options snd-hda-intel model= 3stack-6ch". it would be awesome to have this working correctly with 6 channels and headphones being muted automaticaly!

---

### Post by HunterThomson on 2008-07-02
> **loopyoyo said:**
> just checking to see if anyone has came up with a solution to getting the headphone auto-sense working with "options snd-hda-intel model= 3stack-6ch". it would be awesome to have this working correctly with 6 channels and headphones being muted automaticaly!

You could just write a bash script to do it. Would not be hard... Maybe I will wright it this weekend:)

---

### Post by HunterThomson on 2008-07-02
Well I jumped the gun on the no backlight problems with Arch Linux....

NOT as bad as Ubuntu. On boot it dims as soon as udev loads..... BUT it only dims one click on VLC start. With Ubuntu it dimed all the way. Also, after the VLC one click dim I can just use fn+up and the screen gose that one more click brighter so it is full bright. ON Ubuntu 8.04 it would never become as bright as it should be. Also, Ubuntu dimed on shutdown Arch dose not do that.

However, I have narrowed down what I think the problem mite be.

KERNEL for sure. The backlight levels are reverced and set to 8 not 10 as max. If I run xbacklight = 0.0% it sets it to the same level it dose when I start VLC ((one click to low Ubuntu8.04 MAX brightness)) and if I xbacklight = 100% it dims all the way. 

First, I messed up and installed a bunch of backlight stuff I don't need i.e. Acer, HP, Thinkpad backlight.... So, I will get that crap out and see what happens. Then I will find a command that works and make a bashscript to set the backlight where it needs to be at boot. Won't fix the VLC though.... Well, I could edit VLC so my script runs whenever I run VLC... or like write a scrip to start VLC "THEN" run my scrip to set the backlight... Then put that in my menu list.... I had 

#!/bin/bash

xbacklight = 0.0% 

Starting at boot after KDM but it didn't work... Maybe I needed to set a delay??? Or some thing.. Maybe I just slipt a "." where it should not have been or spelled it wrong... I'll try that agin but it dosn't really solve the problem anyway ((one click to low)) I am thinking I'll try editing the brightness file to "10" insted of "8"

Any thoughts???

---

### Post by dbera on 2008-07-03
> **HunterThomson said:**
> You could just write a bash script to do it. Would not be hard... Maybe I will wright it this weekend:)

I actually doubt you can write a script. The jack auto-sense support needs to be added to alsa. I dont have the time to follow up with necessary information but a bug report with alsa should get this fixed quickly. Jack sense problem with snd-hda-intel is nothing new if you scan alsa bugzilla but they do get fixed quickly if you supply them the information.

---

### Post by HunterThomson on 2008-07-04
> **dbera said:**
> I actually doubt you can write a script. The jack auto-sense support needs to be added to alsa. I dont have the time to follow up with necessary information but a bug report with alsa should get this fixed quickly. Jack sense problem with snd-hda-intel is nothing new if you scan alsa bugzilla but they do get fixed quickly if you supply them the information.

Well my thinking was...
When the headphones are pluged in most speakers mute.... So, the os senses a change and I am sure a value in some file changes when that happens.... So, I would write a script to check that value of the file or state of some dev every 1sec and when that state or value changes the script would run the comands to mute all the speakers. Then when the script senses the file or dev changs to the value or state that it is in when there is no headphons pluged in it would run the comands to set the vlume back up.

This would be a vary ugly and raw way to solve the problem but I don't see why it could not be done?????

Edit: Or insted of looking for a headphone file something.... It could just check one of the volumes that dose mute like "front" every sec or two... And when that one mutes the script will run amixer comands to mute the rest of the speakers. And raze them back up......

So, ya you can write a script to do it you just have to think out of the box:)

---

### Post by miggys on 2008-07-04
I think the real issue is that in 3stack model, to have the headphones on, Front channel needs to be on and if Front channel is on, then the speakers (or just some of them) are also on.  Or at least that is what I have noticed.

If the issue was simply a matter of muting the proper channels it would be no problem.  In fact, that's how I do it using the lenovo mode.  I really don't notice any difference in 3stack vs lenovo if I have Center Surround and LFE turned on.  Whenever I want to use my headphones I just run a script to mute those 3 channels which I have affixed to a simple key binding. 

If you feel you have to use 3stack, one option--though probably not to attractive--would be to write a script (to be run as root) to change the options in the modprobe file and reload the snd-hda-intel module.  Of course to unload the module you cannot be running anything that depends on it and if you use a DE, like gnome or kde, my guess is that you will have to exit X in order to modprobe -r snd-hda-intel.

---

### Post by HunterThomson on 2008-07-04
> **miggys said:**
> I think the real issue is that in 3stack model, to have the headphones on, Front channel needs to be on and if Front channel is on, then the speakers (or just some of them) are also on.  Or at least that is what I have noticed.

If the issue was simply a matter of muting the proper channels it would be no problem.  In fact, that's how I do it using the lenovo mode.  I really don't notice any difference in 3stack vs lenovo if I have Center Surround and LFE turned on.  Whenever I want to use my headphones I just run a script to mute those 3 channels which I have affixed to a simple key binding. 

If you feel you have to use 3stack, one option--though probably not to attractive--would be to write a script (to be run as root) to change the options in the modprobe file and reload the snd-hda-intel module.  Of course to unload the module you cannot be running anything that depends on it and if you use a DE, like gnome or kde, my guess is that you will have to exit X in order to modprobe -r snd-hda-intel.

Aw yes a key binding would be ez.... I have never used the stack 3 I just figured it was the same problem encounted with the lenovo mode of just needing to mute a few channels like LEF.

---

### Post by HunterThomson on 2008-07-04
_**HDD Load_Cycal_Count**_

Well, The whay I fixed it was to intall the laptop-mode-tools module. I set the Power Saving mode to 254 on AC and 144 on Battery. I also have it set it to not park for 15min's on AC and to pre-cache 3MB. It now dosen't wright to the HDD every 5 sec's for the ext3 jurnaling filesystem. It can now wate 15min. There are a bunch of optoions. I think this is a good way to do it. Look into it if your interested.

---

### Post by HunterThomson on 2008-07-04
OK, _"This dosn't work look below. After a lot of trying things rc.d, Autostart, Xsession.d, permitions... I got something to work"_

Thanks to "dbera" I have soved the brightness problem (for the mostpart).

Here is what I did.

wrote this script:

#!/bin/bash
# Set backlight to 10
echo 10 > /proc/acpi/video/VGA/LCDD/brightness

---------
mv brightscript /etc/rc.local ((now brightness dosen't change when udev starts))
---------
chown (my user name):wheel /proc/acpi/video/VGA/LCDD/brightness
---------
made a application link to the script and added 
bright.desktop to /home/(user name)/.kde/Autostart
---------

Now the brightness dosen't change when udev loads... Then dims on loginscreen. Then gets bright on desktop start. This is good enugh for me screen is max bright on desktop start. I take back what I said about the Kernel...I was wrong. Also, I would like to add that in Archlinux the brightness keys are not reversed. All is still well with my laptop after the new kernel 2.6.25.10 kernel upgrade today:)


EDIT: well this did not work.... After a full reboot /proc/acpi/video/VGA/LCDD/brightness is owned by root agin.... I have tryed to just make the script owned by root:root but no go...

---

### Post by dbera on 2008-07-08
> **HunterThomson said:**
> 
EDIT: well this did not work.... After a full reboot /proc/acpi/video/VGA/LCDD/brightness is owned by root agin.... I have tryed to just make the script owned by root:root but no go...


root:root will not work. You want to setuid the script to root; however setuid scripts are dangerous and some shells/distros/whatever disable setuid scripts.

Try the /sys/devices/virtual/backlight/acpi_video1/ interface instead of the /proc interface. If that does not work for you, then use Xsession.d scripts to run set the brightness before login and after logout. Xsession.d scripts are run as root.

---

### Post by Zetheroo on 2008-07-16
There was someone who posted saying that they had installed Hardy 64bit and their webcam was still not working. So it seems that it is still a case by case basis thing ... nothing is certain regarding the webcam.

In relation to the dimming/brightness issue there seems to be no straight forward solution ... is this correct?

And with the sound ... I get sound from the two center speakers when having the earphones plugged in. I recall there being mention about this somewhere in the thread, but could not for the life of me go through all these pages looking for it.... my eyes ... my eyes .... 

I think it would be great if someone could compile all the research put into this thread and post it somewhere ... and then update it from time to time as new stuff comes out... :KS

---

### Post by HunterThomson on 2008-07-17
> **Zetheroo said:**
> I think it would be great if someone could compile all the research put into this thread and post it somewhere ... and then update it from time to time as new stuff comes out... :KS

**_Lenovo Ideapad Y510 is Go Summary, Linux Compatibility List_**

Well, here is a half*** shot. I will update this and add new sections as needed.

_**Web cam**_= mite be upside down.... Best bet with the 64Bit vertion.

_**Backlight**_= Page 14-15... Ubuntu8.04 is a big deal to me, dim all the way on boot, dim VLC/media player start, and dim on Game start. NO problems with Ubuntu7.10. Vary few problems with Archlinux, only dim on boot and one click dim on VLC/media player start. You can set a hot key to turn up the backlight for you. Also, it has been reported that totem media player dosen't cause the screen to dim. Also, the backlight keys on Ubuntu8.04 are upside down. In Archlinux the backlight keys work as they should. The sad part is that in Ubuntu8.04 or Archlinux the screen will never be a bright as is should be. We still have some work to do:neutral:
_(See my strange workaround for KDE bright on startup below:-k)_.
 

_**HDD Load_Cycal_Count**_= Page 16-17...Install Laptop-mode-tools and set the powersaveing setting to 254 on AC and Bat... Read up on Laptop-mode-tools there are a lot of options.

**_Sound_**= Page 2.... some speakers will not mute when headphones are pluged in. You will have to mute them in the alsamixer or you would write a script or set a hot key to do it for you.

_**Hibernation**_= Page 15-16...will not work with Ubuntu8.04... works with 7.10... works with Archlinux.

_**Suspend to ram**_= Page 15-16...will not work with Ubuntu8.04...works with 7.10... works with Archlinux

_**Secreen resolution**_= Ubuntu7.10((don't know about 8.04)) sees it as a 1024x768. IT IS NOT! it is 1280x800 and Archlinux sees it this way and you will get the full 1280x800 with out any configuring.((I have Xorg as my WM and KDE as my DE))

**_BIOS Update_**=Page 20... There is a "CRITICAL BIOS UPDATE" for all the Ideapad laptops. Lenovo only lets you download a .exe for Vi$ta. You mite want to do that before you install Linux. However you can update the BIOS in Linux look at P20 for the links and stuff.

_**CD/DVD**_ Just Works... No problems at all.

_**Multi Card Reader**_ Well the SD cards work I have not tried MMC or MS.....

_**VGA Port**_I don't know.... PM me if you know.

_**S-Video Port**_I don't konw.... PM me if you know.

_**RJ-45 Ethernet**_Just Works...No problems at all.

**_WiFi_**Just Works... No problems at all.

**_Media Buttons_**Just Works in Ubuntu. They are recognized in Archlinux but I have not mapped them to anything yet.

---

### Post by dbjohnso67 on 2008-07-19
Just a shout out to everyone on this thread!
After reading the entire thread first I was able to make all aspects
of my y710 work in ubunto hardy!

thanks a ton to all!!

mostly happy to have all 5 speakers working great!!!

:guitar:

---

### Post by HunterThomson on 2008-07-19
**_Backlight Bright on Startup Workaround:-k_**

Well, I have a "working" workaround for KDE to set the backlight to max bright after login. I will try to keep it short asuming you know how to do some things like write scrips but still long enugh to ask the right questions if you don't. If you would like more info tell me and I will edit this. Thank you agin to dbera for the core comand=D>

_First_ write this script:

#!/bin/bash

echo 10 > /proc/acpi/video/VGA/LCDD/brightness

_name it_ 'brightscript",chmod 755 and put it in /usr/bin

_Then_ edit visudo, add this line under "# Same thing without password":

myusername ALL=(root) NOPASSWD: /usr/bin/brightscript

_Then_ write this script:

#!/bin/bash
# run brightscript with the sudo comand

sudo brightscript

_name it_ "sbright", chmod 755 and move it to /usr/bin

_Then_ right click the desktop and slect create new/Link to application, name it sbright, under the "application" tab in the "command" space put sbright. In "work path" space put /usr/bin. Then in the "add" select shell script. Then in the "advanced options" check the box "run in terminal". Then say OK. 

_Then in_ the shell "cd Desktop" then type:

chown username:wheel sbright.desktop 
((in ubuntu it would be, chown username:username sbright.desktop ))

_Then_ right click the sbright.desktop Icon and go to "properties" then in the "permitions" tab check the box "Is Executable". The OK.

_Then in_ the shell "cd Desktop" and type:

sudo mv sbright.desktop ~/.kde/Autostart

_And you are done_. Now after login the "sbright" script will run which will run the "brightscript" script with "sudo" before it and it will not need to have the password typed in because you edited the sudoers file\\:D/ The thing with the edited sudoers file is that you still have to type sudo for the program to run but it just dosn't ask for a password. This is why you need a script to run a script. I like this workaround it has a lot going on and gets around a lot of the permitions stuff. If you think I should do anything a diferent way let me know. This of corse only works for KDE. In order to do this in Gnome you would have to find the equielant to the Autostart file and how to put stuff in there to run.

---

### Post by sombertattoo on 2008-07-19
Wow.....I'm closely watching this thread and based on the detail here, I think I'm going to dive in and buy one.....thanks!!! :guitar:

---

### Post by HunterThomson on 2008-07-20
Ya, buy one:) I did a lot of reading about laptops before I got this and I really like it. ((Hint newegg.com)) From what I read Lenovo dose a lot for the Open Sorce comunity. I also got the one with the intel GPU, Ya it sucks but I don't game, so all my hardware is running on open drivers. Intel also dose a lot for Open Sorce. For the spec's it is really one of the best deals. Asus has some good prices but from what I read there costomer service is horable. ~$1,000 Asus laptops are not as good of quality as Lenovo from what I "read" but I have never had one. Lenovo ThinkPad is the best though but if you wach a lot of movies like me you will like the Ideapad better for the $.... But a "magnesium frame" and "Shock mounted HDD" has a nice ring to it, Get the ThinkPad if you have the $$$.

---

### Post by brandn on 2008-07-20
ok i have two questions for you guys, i recently bought one of these and love it but im still having some trouble with a few things.

hunterthompson - im also running archlinux, were you able to get the subwoofer working?  i tried following the instructions in this thread but i cant find the alsa conf files in archlinux.

my second question is if anybody has gotten KVM working on the Y510.  i know that the processor should support it but i can't load the kvm-intel module, i think the problem might be its not supported by the BIOS

---

### Post by wyth on 2008-07-20
I can't speak to anyone's immediate problems, but I'm doing some checking into a few things.

Lenovo recently started selling machines with Suse pre-installed.  So in the interest of experimentation, I grabbed a live CD of the latest OpenSuse 11.0, and am checking some things out.

Here's what I can report so far:

[LIST]
[*]The backlight issue is still an issue.  In fact it's a little worse --you set your brightness, and it reverts to what it was.  In gconf you can change it, but again, it's the opposite of what it should be, so 0% actually yields 100% brightness.
[*]Cheese didn't pick up my camera at all
[*]Couldn't tell if the sound worked or not -- need to get something to play on it first.  I should have just grabbed my mp3 player, but instead...
[*]I'm making a test partition and I'm going to install OpenSuse 11.0 and try it out; if it takes care of some of these issues, I'll see what I can track
[*]If that doesn't work, I may give Linux Mint a try on the same test partition
[*]Last, I can report that I generally just don't care for Suse's setup.  Seems needlessly complicated in some ares, but I think that just comes from my comfort with Synaptic and the way the configuration works.  Just not a big fan of a configuration center, Yast, and their menu, which seems to take a bit longer to actually get to an app
[/LIST]
I'll be looking to see the subwoofer works, if plugging in headphones actually mutes the speakers (and sound can be heard through the headphones), if the camera works, and if the backlight works.  

Anything else I should look for?

---

### Post by wyth on 2008-07-20
From the Lenovo forums, it looks like these machines [were also having backlight issues on XP]("http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&thread.id=102&view=by_date_ascending&page=2") (at least with the hotkeys for brightness).  Interesting.  A BIOS update took care of their issues.  Anyone tried to update their BIOS?  That always scares the bejeebus out of me on Linux.

As I'm making my partition with a few-month-old version of gparted on a live cd, I can report that it picks up the backlight settings just fine, up-arrows and down-arrows work appropriately for making the screen brighter and dimmer, and it gives me all ten steps.  I'm really curious what changed in these newer distros, and why it took a step back.  If I was smarter, I'd figure out what the settings were in the gparted live cd and set my Ubuntu to that, and let everyone know how to do it.  

I'm also curious about something else: Early on in the thread, we found that ***options snd-hda-intel model=lenovo-ms7195-dig*** in the ***alsa-base*** file got us full sound, and since then I've also used one of the 6ch ones with success.  

There have been a few updates since this thread began, and I'm having the same headphones issue as others: I plug in my headphones, and the front speaker doesn't mute.  If I mute it, I also lose sound in my headphones.

I'm wondering if some other option in ***alsa-base*** would take care of this hassle.

---

### Post by brandn on 2008-07-20
could you please post the contents of your alsa-base config file?

---

### Post by HunterThomson on 2008-07-21
> **brandn said:**
> 
hunterthompson - im also running archlinux, were you able to get the subwoofer working?  i tried following the instructions in this thread but i cant find the alsa conf files in archlinux.

You don't really have to do any of that stuff in archlinux. Don't edit the rc.conf file. The only thing you do in there is !Bang out ALSA. It will only give you error's. 

All you have to do is this; 

pacman -S alsa alsa-lib alsa-utils

And add;

options snd-hda-intel model=lenovo-ms7195-dig

To the end of,

/etc/modprobe.conf

Well it is the only thing is there because archlinux dosn't use that file normaly. All, my speakers are working well.

[http://bbs.archlinux.org/viewtopic.php?id=50606](http://bbs.archlinux.org/viewtopic.php?id=50606)

I eddited my half*** summery with this but I fell like saying it agin. Aw, yes... when you mute the front speakers the sound in the headphones gose down... That sucks. As for the 10 step brightness key.. In Archlinux the brightness keys work as they should. Also, I only get 6 steps. and I just installed KDE utils package for SuperKaramba and it also installed this GUI brightness thing that pops up when I change the brightness.. I tells me the screen is at 67%. That seeems true. Also, the screen only dims that one step when VLC starts the first time you start VLC. Then you can close it and start it agin and it will not dim the screen... I find that strange. But, 67% is fine for me.. My UpTime is reading 11h:58m so this mite be better for my eyes;) I'll spend some time in the config files next weekend. By the way the back light on BackTrack3 final is not dim on boot how ever it is only as bright as it is in Archlinux and only has 6 steps with the Fn+up/down and like Archlinux the keys are not reversed. The only ones found with locate backlight are these.

/lib/modules/2.6.21.5/kernel/drivers/video/backlight
/lib/modules/2.6.21.5/kernel/drivers/video/backlight/lcd.ko
/usr/include/linux/backlight.h
/usr/libexec/hald-addon-macbook-backlight
/usr/libexec/hald-addon-macbookpro-backlight
/usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi

I attached a copy of /usr/include/linux/backlight.h
_________________________________________________________

Hum, Ya, your right there is a BIOS update for the Y510 and the rest of the Lenovo Y's. They say it is a "CRITICAL UPDATE" yet they only let you download a .exe for Wincrap Vi$ta. I selected vary unsatisfid in the box and told them to suply a BIOS updater for Linux. They are vary vage about what the problem is..."To eliminate a potential source of unexpected system behavior." I guess it has to do with RAM. I would like to try that. But I would have to partition my harddirve and install Vista...Arg. Would suck though if something whent wrong... I'd have a vary nice coaster a cuple RAM sticks and a spare HDD. I'd fell saffer to wipe my HDD install Vista only the do the udate then re-partiton and restore my Archlinux with Partimage on SystemRescue Live CD.

[http://consumersupport.lenovo.com/lenovo/hints/2414/895.html](http://consumersupport.lenovo.com/lenovo/hints/2414/895.html)

[http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=706](http://forums.lenovo.com/lnv/board/message?board.id=ideaPad&message.id=706)

[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by wyth on 2008-07-21
> **HunterThomson said:**
> Hum, Ya, your right there is a BIOS update for the Y510 and the rest of the Lenovo Y's. They say it is a "CRITICAL UPDATE" yet they only let you download a .exe for Wincrap Vi$ta. I selected vary unsatisfid in the box and told them to suply a BIOS updater for Linux. They are vary vage about what the problem is..."To eliminate a potential source of unexpected system behavior."

I don't recall exactly what the BIOS update was for, but it addressed the backlight issue in XP.  It There is a way to update the BIOS in Linux, and I managed to do it, but it's tricky.  Search on here -- there are all kinds of confusing instructions about how easy it really is.  

The .exe file just unzips the .rom file to the C: drive.  If you have Wine or something, you can grab it, and I think some archivers will open it.

Now I take no responsibility for this if anything happens to your machine, but I got the .rom out of the .exe and attached it to this message.

**EDIT**
[This HOW-TO page goes over updating BIOS from a thumbdrive]("http://ubuntuforums.org/showthread.php?t=694513").  I don't recall if this is what I did or not -- I updated a few months back.  But it may come in handy.

And by the way, why is there a </div> inserted at the end of every single post I write after I post it?  Is that happening to anyone else?

---

### Post by evets25 on 2008-07-21
First, I just want to thank wyth for all his help in this thread. In deciding to buy a laptop, it was mostly this thread that convinced me to go with the y510 (that and the fact that it was on sale :P). 

Anywho, I've had my laptop for about 3 weeks now, and I'm pretty happy with it. It was a pain compiling alsa-base and all that in order to get sound working (see earlier in the thread) but at least I have all the speakers working now. I have the usual minor problems with my laptop that others have mentioned, (brightness buttons reversed, sound not fully muted when headphones plugged in, webcam upside-down, etc.) but sometimes when I'm feeling adventerous I'll skim the rest of this thread and figure out their fixes. I remember reading about them, I'm just too lazy to do it at the moment. :D At any rate, these minor problems all sound like things that will get fixed in the next version of ubuntu, since it will have newer versions of everything (like alsa-base, and restricted-drivers), which probably alredy have the fixes in them. 

Overall, I'm very happy with the laptop, and I recommend it to anyone looking to buy a good linux-compatible laptop.

here's a quick summary of the hardware compatibility for me:
 
**sound**: works, with several minor issues, needs newer version of ALSA compiled
**graphics**: Intel, therefore it Just Works(tm). No hunting down special drivers, or even using the restricted drivers manager.
**SD card reader**: works
**Wireless**: works
**DVDrw drive**: works, reading and writing CDs and DVDs.
**webcam**: works, but the image is upside-down (which is easily corrected in most programs that use the webcam like skype and cheese)
**touch-sensitive hotkeys**: some work, some don't (the important ones, like pause, next track, mute, etc. all work.)
**suspend**: works.
**hibernate**: not tested. 
**touchpad**: works (scroll-wheel on the left side of the touchpad works too)

Anywho, if you browse the rest of this thread, you'll see this is all nothing new, I just thought I'd post it here again for any new-comers, like I was. 

I find it does tend to run a little hot, especially while using the graphics card or charging the battery. I have a temperature monitor applet, and it reports a temperature between 45 and 50 degrees Celsius during normal light usage. 

Oh and did I mention it's oh-so-sexy? <3 :D Everyone always says "wow!" when I open it up, and comment on the cool texture on the outside of the case and the sexy orange glowy-buttons. I can't help it, I'm in love okay? :D

---

### Post by HunterThomson on 2008-07-22
Hey you got another star form me wyth:) Thankyou for the BIOS update update:P I will read read read read and read some more about that before I flash my BIOS though.

Is idle 45-50C and working 50-60C Hot??? I would not know 50C is 120F dosen't sound hot. I just installed lm_sensors and the only thing it found was Core 0 and Core 1 Temp. I know the HDD has a temp sensor too but it didn't find it. I also have the System Temp but I don't know what it is the temp of though??? All seem to read about' the same all the time.

---

### Post by wyth on 2008-07-24
Quick update:

Trying out OpenSuse didn't really reveal anything new for those few small, consistent issues.  Neither did LinuxMint.  

But here's what I know with the sound.

Early on in the thread, lenovo-ms7195-dig was suggested.  Later on in the thread, 3stack-6ch was suggested.  

I'm not sure what other people's experience has been, because since 8.04.1 I've removed the alsa drivers I compiled and used the ones in the repository.  I was on the 3stack-6ch model, and experiencing the headphones issue -- I'd plug in my headphones and the speakers wouldn't cut out.

(alsa-driver-1.0.17 is [available on the ALSA site]("http://www.alsa-project.org/main/index.php/Main_Page"), but here have been some problems getting it compiled.  I couldn't make it happen, so I don't know if it addresses any of these issues.)

So I've been going through the various models and trying a few out.  Just using lenovo or auto yielded the same result -- next to nothing -- and lenovo-nb0763 was useless.  However, going back to lenovo-ms7195-dig got me back full sound, and no speakers when I plug in the headphones *if* I mute Center and LFE.  

I'm not sure if some of the other 3ch or 6ch models, or the acer, medion, targa, haier, hp, dell, or mitac would do any better.  Is there a quick way to change the model in /etc/modprobe.d/alsa-base and have it take effect without rebooting?  If so, it'd be a lot easier to test the models.  I've tried restarting alsasound, but that didn't work.

**Other question:** Since the last kernel update, has anyone noticed the screen automatically dimming whenever video plays?  Any video -- totem, vlc, avidemux, youtube, etc.  

**Corollary question:** Has anyone tried out anything but the generic kernel?</div>

---

### Post by HunterThomson on 2008-07-24
I compiled my own kernel but there are somany options.... It didn't work and I gave up. However, that really seems like the way to go. Like the Kernel that I am running right now is only compiled for plane x86_64 but if you compile the Kernel yourself you can select Core 2 Duo. There are a lot of options that you can use that are a lot better then the ones selected in the genaric Kernel. Like security options for RAM to hinder Buffer Over Flow attacks.

As for the dim on video play.... I alwas got that with the new Ubuntu even the Ubuntu8.04 Beta.

---

