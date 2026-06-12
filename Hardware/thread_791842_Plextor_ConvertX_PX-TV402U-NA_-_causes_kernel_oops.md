---
title: "Plextor ConvertX PX-TV402U-NA - causes kernel oops"
date: 2008-05-12
forum: Hardware
---

### Post by jnorth on 2008-05-12
**[SIZE=4][COLOR=Red]Please note:[/COLOR][/SIZE]**
[B]
[SIZE=2][COLOR=Red]Thanks to jelle[/COLOR][/SIZE] in posts starting here [http://ubuntuforums.org/showthread.php?p=6661524#post6661524](http://ubuntuforums.org/showthread.php?p=6661524#post6661524) - this is running on Intrepid.  See the original posting below the line for instructions on past Ubuntu versions.

For full copy/paste instructions to [SIZE=2][COLOR=Red]install on Intrepid[/COLOR][/SIZE], start at this post: [http://ubuntuforums.org/showthread.php?p=6781890#post6781890](http://ubuntuforums.org/showthread.php?p=6781890#post6781890)

I am running this as of 17 May 2008 on kernel 2.6.27-14-generic[/B]   

======================================================
NOTICE!!!  I believe this may be resolved (at least it works no on my box, though on a slightly older kernel.  See post 4 for more)

BTW - I have searched :)  I've spent 2 weeks so far on this device trying to get it to work, with several reinstalls.

EDIT:  Don't worry about the rule/forum announcement on having me run commands on my box.  I'm a perfectly capable and discerning Linux user, and this box is a non-critical one at this point as I have no valuable data on it yet (and have already reloaded several times in the past 2 weeks!).

Without further ado, the details.  Any assistance or hints are appreciated, no matter what!

I have a **Plextor ConvertX PX-TV402U-NA** that I am(was) using with an **Apple MacMini Intel coreduo** as a MythTV box.  Up until a couple weeks ago, I had Gutsy installed and running perfectly with this setup, with the exception of a known issue getting the apple IR device to work.  I upgraded to Hardy to fix the IR issue (it did!), but now am having problems with the TV capture.  Additionally, I have attempted these same instructions on a Sony Vaio (VGN-SZ220) with the exact same results (just differing lsmod's etc), so I know it's not the Macmini's fault :)

Relevant details are below (I've linked to files on my server rather than paste all this in the forum to make it easier to read and comprehend.)

This device worked properly on 7.10 and previous with the patched files from _[COLOR=Blue][Nikosapi's site]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver")[/COLOR]_.  This site has instructions and claims to work on hardy, but no luck so far.  If I can get it working I'll try to get the wiki updated!  The section with Ubuntu-specific details is _[COLOR=Blue][here]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy.2FHardy")[/COLOR]_.

**System details:** (fresh install of Mythbuntu 8.04 - but I have also tried vanilla Ubuntu)
See the output of my _[COLOR=Blue][lsmod before installation here.]("http://mirror.point808.com/go7007troubleshooting/lsmod%20before.txt")[/COLOR]_```
jnorth@mc01:~$ uname -a
Linux mc01 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux
```I ran through the installation as instructed, and attached the output of the _[COLOR=Blue][make command here]("http://mirror.point808.com/go7007troubleshooting/make%20ouput.txt")[/COLOR]_, and the _[COLOR=Blue][make install command here]("http://mirror.point808.com/go7007troubleshooting/make%20install%20ouput.txt")[/COLOR]_.

So, once installed per the directions, with no major errors, I follow the test procedure with the following results:```
jnorth@mc01:~$ gorecord -input 0 -duration 20 test-video.avi
Unable to read /sys/bus/usb/drivers/go7007: No such file or directory
Is the go7007-usb kernel module loaded?
```Sure - no problem, according to the instructions I should manually load the firmware this time:```
jnorth@mc01:~$ sudo /usr/sbin/go7007_firmware_load
ERROR: Make sure usbfs|usbdevfs is mounted on /proc/bus/usb
```Again, no worries - the instructions have a fix for that:```
jnorth@mc01:~$ cp /etc/init.d/mountdevsubfs.sh ~/Desktop/
jnorth@mc01:~$ cd wis-go7007-linux-0.9.8-2
jnorth@mc01:~/wis-go7007-linux-0.9.8-2$ wd=`pwd`; sudo patch -d /etc/init.d -p0 -i "$wd"/patches/mountdevsubfs.sh-usbfs.patch
patching file mountdevsubfs.sh
jnorth@mc01:~/wis-go7007-linux-0.9.8-2$ sudo /etc/init.d/mountdevsubfs.sh start
jnorth@mc01:~/wis-go7007-linux-0.9.8-2$
```Let's try loading the firmware again:```
jnorth@mc01:~$ sudo /usr/sbin/go7007_firmware_load
Firmware loaded successfully!
```Awesome - we're golden now right?  Not quite - I tried a short test record with no luck:```
jnorth@mc01:~$ gorecord -input 0 -duration 20 test-video.avi
Driver loaded but no GO7007 devices found.
Is the device connected properly?
```Ok - I'm intermediate to advanced on most things Linux, so I'll snoop around.  I pull _[COLOR=Blue][dmesg for the firmware load here]("http://mirror.point808.com/go7007troubleshooting/kernel%20oops.txt")[/COLOR]_, and another _[COLOR=Blue][lsmod after the load here]("http://mirror.point808.com/go7007troubleshooting/lsmod%20after.txt")[/COLOR]_.  lsusb just hangs after the attempted firmware load.

I've done a lot of other stuff too, but nothing relevant that I see.  If you have something that I should pull that you think might help me troubleshoot, I am all ears (and hands - more than willing to do whatever it takes to get this device working again!)

Darn, so close.  I've been through all sorts of searches and old sites trying to find a working fix for this with no luck.

This thing worked like a charm on 7.10, but lirc wouldn't work (appleir/macmini driver problems with making the hiddev0 device and using it) so I wiped it out and reinstalled a fresh Hardy, and here is where I am stuck.

I'm "this close" to having the perfect MythTv setup using my MacMini.

Any ideas from you pro's?  I'd greatly appreciate any advice, even if it means reinstalling from scratch - I don't have everything loaded back on this machine yet so I can afford to muck around with it.

---

### Post by jnorth on 2008-05-13
Update - I was browsing around on launchpad and finally found some other people with this issue.  Bug report is located [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/201098")

Looks like the solution for now it to just downgrade the kernel - bummer.  I updated the launchpad report in an effort to keep it open until resolution.

---

### Post by Call Me Ben on 2008-05-13
J,

I'm running into the exact same problem and my proposed solution was to recompile the kernel with ALSA enabled (since that's where the oops is generated).

I'll let you know if that works at all.

Ben

---

### Post by jnorth on 2008-05-13
YES!!! Thanks to comments in that bug report I was able to get this going.  These are the steps I took AFTER going through the first post above.  Should be able to copy/paste the code blocks here for the most part.  If you haven't yet gone through the above post you can do it during the second section of code below to fix the usbfs and all that stuff.

```
cd $HOME
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-headers-2.6.24-1-686_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-headers-2.6.24-1-common_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-image-2.6.24-1-686_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-kbuild-2.6/linux-kbuild-2.6.24_2.6.24-1_i386.deb
wget http://ftp.de.debian.org/debian/pool/main/l/linux-2.6/linux-2.6_2.6.24.orig.tar.gz
sudo apt-get install gcc-4.1
sudo apt-get -f install
sudo dpkg -i linux-image-2.6.24-1-686_2.6.24-6_i386.deb linux-headers-2.6.24-1-686_2.6.24-6_i386.deb linux-headers-2.6.24-1-common_2.6.24-6_i386.deb linux-kbuild-2.6.24_2.6.24-1_i386.deb linux-headers-2.6.24-1-686_2.6.24-6_i386.deb 
sudo reboot

```
IMPORTANT!!! UNPLUG your Plextor device before it boots back up!  When the computer comes back up, hit escape to go into the grub menu and be sure to go down and select the kernel you just installed (2.6.24-1) and NOT the default 2.6.24-16 or -17.

Now, once you are back up, more steps, we're going to rebuild the modules...
```
wget http://nikosapi.org/software/WIS_Go7007/wis-go7007-linux-0.9.8-2.tar.bz2
tar -xjvf wis-go7007-linux-0.9.8-2.tar.bz2
cd wis-go7007-linux-0.9.8-2
make
sudo make install USE_UDEV=y

```

Now - cross your fingers and plug your Plextor back in.  Run a dmesg and you should see that it successfuly loaded.  Run the test record program just to verify, and viola! (at least for me :)).

Hope this helps!

EDIT: I was so happy to get this up I forgot to note that you'll need to clean up your old kernels and put a hold on the version so you don't accidentally break it during regular updates.

To do so, run the following:```
sudo apt-get remove linux-image-generic linux-generic linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic linux-image-2.6.24-16-generic linux-image-generic linux-restricted-modules-2.6.24-16-generic linux-restricted-modules-common linux-restricted-modules-generic linux-source-2.6.24 linux-ubuntu-modules-2.6.24-16-generic linux-headers-2.6.24-17 linux-headers-2.6.24-17-generic linux-image-2.6.24-17-generic linux-image-generic linux-restricted-modules-2.6.24-17-generic
sudo rm -r /lib/modules/2.6.24-16-generic/
sudo rm -r /lib/modules/2.6.24-17-generic/
sudo rm -r /usr/src/linux-headers-2.6.24-16-generic/
sudo rm -r /usr/src/linux-headers-2.6.24-17-generic/
sudo rm -r /usr/src/linux-source-2.6.24/
sudo rm -r /usr/src/linux
sudo apt-get autoremove
sudo update-grub
```

And that should do it.  Let me know if I missed anything.

EDIT2:

Dangit!  Forgot to lock down the kernel version so you don't break it.
Easiest (GUI) method is to open Synaptic package manager and pin the kernel version.  You could also edit your /etc/apt/preference file.
In synaptic though, do a search for "linux-image-2.6.24-1-686".  Highlight it, and from the "Package" menu, choose "Lock Version".

I think that's it now.

---

### Post by jnorth on 2008-05-13
> **Call Me Ben said:**
> J,

I'm running into the exact same problem and my proposed solution was to recompile the kernel with ALSA enabled (since that's where the oops is generated).

I'll let you know if that works at all.

Ben

Hey I cross-posted on you just now, I was so happy to see this thing working again that I had to post what I did to resolve it.

Let me know how your story goes if you go the recompiling way, I was trying to avoid that but had just come home from work planning to try it when I found this other solution.  I don't mind running an older kernel for the moment until the new gets fixed.

---

### Post by sullyt on 2008-05-16
Hey,  thanks for the information.   I have exactly the same issue.   Sadly, the Plextor ConvertX is poorly support with Linux.   I've had an issue with every upgrade over the last 3 years.     That said, the unit is rock solid once it recognized by Linux.    MPEG4 hardware compression is great and I believe this is the only unit that does this (at least the only USB unit).

Did you try out any of the other Kernel at the Debian FTP site?   Did you try compiling your own?    I am asking out of curiosity.   The solution you put out there gets the TV402U working.   However, I lost lirc and NVIDIA because I need to add new Kernel modules for each.   Perhaps, this weekend I will have time to resolve this issue and add an update to this page.   

/Cheers

---

### Post by sullyt on 2008-05-16
Tried to get the NVIDIA driver to work with the 2.6.24.1 kernel and having some difficulties.   There does not seem to be a Debian package for the NVIDIA modules for this Kernel.  (I may not be familiar enough with Debian respository).   I got the commercial version of the NVIDIA driver and compiled it against the headers.  Everything compiled fine but the driver did not load.   I do not understand Ubuntu's restrict driver architecture.

Any ideas?

---

### Post by sullyt on 2008-05-16
Okay, took another approach and decided to find out the root cause.   Checked the config-2.6.24-16-generic file in Ubuntu and # CONFIG_SND is not set.   I have no idea why it off. 

I  will recompile the Kernel this weekend with this SND options turned on and see what happens.

-Cheers

---

### Post by bwilson on 2008-05-25
I'm using the Plextor TV402U in Gutsy PPC. I installed the patched driver from [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver). This page was immensely helpful.

Everything works OK -- except for one annoying detail. When I boot up with the TV402U powered on and connected the driver doesn't load. If I do a disconnect/connect cycle of either the USB or power cable then the driver loads and all is well. D'oh!

Any ideas?

Thanks.

---

### Post by Call Me Ben on 2008-05-26
Finally got around to rebuilding the kernel. WHAT A PAIN!

But in the end adding the CONFIG_SND (and OSS MIXER directives) worked wonders. I did have to rebuild Lirc too.

Now the only problem I see is that after changing channels the left side of the screen is garbled.

Ben

---

### Post by wzf851005 on 2008-05-27
These patterns are based on different foot type, weight, Speed, training programmes, gender and skill level design. These different styles, different prices and multi-purpose products, attracting hundreds of thousands of jogging, making them feel that [nike shoes](http://www.bestbuynike.com) is to provide the most complete variety of running shoes manufacturers, millions of range of ability Running to have that belief.   First-generation jordan shoes uppers, there is a conspicuous "Chachi basketball" signs in the use of trapeze signs ago, the first generation and second generation Chachi Jordan basketball shoes are used as signs. First-generation[jordan shoes](http://www.pickyourjordan.com) appeared in 1985, 1994 and 2001 NIKE companies produced twice again this shoes. For the classic colors with a red, black, and compared with black. [Air Jordans](http://www.oknike.com), published in 1991, jordan shoes91-92 season Zhanxue because jordan shoesin the Barcelona Olympic Games 92 wearing this pair of 7 and winning the title, the seventh generation in jordan shoesin the series, it is particularly valuable. 7 and the shape of the shadow of some six generations, the biggest feature is particularly color.  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.

---

### Post by jnorth on 2008-05-27
> **Call Me Ben said:**
> Finally got around to rebuilding the kernel. WHAT A PAIN!

But in the end adding the CONFIG_SND (and OSS MIXER directives) worked wonders. I did have to rebuild Lirc too.

Now the only problem I see is that after changing channels the left side of the screen is garbled.

Ben

Good to know, but odd.  Is it a big chunk of the screen or just small?  I ask because I have about a 2-pixel line across the top of the screen that is garbled on mine, but it is only a minor annoyance at this point.  The thrill of actually being able to pause live tv is worth it (never had a tivo :).

---

### Post by Call Me Ben on 2008-05-27
I thought I locked up the kernel packages but I must of missed something. Doing the upgrade last night totally fouled things up. The device still loads but no video and TONS of USB errors. I may just downgrade to get this thing working. I'm knew to mythbuntu. Who do we ask to enable ALSA and the two OSS directives in the next kernel upgrade?

Ben

---

### Post by cchi on 2008-06-14
There has been some kernel updates since this issue has been commented on last.  Has anyone been brave and tried it on a fresh install, or do we have to keep using the old kernel for now?

---

### Post by Verlager on 2008-06-21
I have two Plextor ConvertX units which are now useless. Can anyone recommend a USB or PCI card video capture device which works with Ubuntu Hardy Heron 8.04?

---

### Post by jnorth on 2008-06-23
> **Verlager said:**
> I have two Plextor ConvertX units which are now useless. Can anyone recommend a USB or PCI card video capture device which works with Ubuntu Hardy Heron 8.04?

Whatcha want for em? :)

Seriously, they will work, you just have to pin the kernel so you don't accidentally upgrade it.  I'm testing each time new versions come out to see when it starts working again.  My MythTV box is running great on Hardy, with everything except for the kernel up to date, and have not seen any issues at all.

---

### Post by jnorth on 2008-06-23
> **cchi said:**
> There has been some kernel updates since this issue has been commented on last. Has anyone been brave and tried it on a fresh install, or do we have to keep using the old kernel for now?

I tried, no luck.  I plug in a usb drive and install to it each time i see significant updates to test, but so far, no change.

---

### Post by sf_basilix on 2008-09-08
> **jnorth said:**
> YES!!! Thanks to comments in that bug report I was able to get this going.  These are the steps I took AFTER going through the first post above.  Should be able to copy/paste the code blocks here for the most part.  If you haven't yet gone through the above post you can do it during the second section of code below to fix the usbfs and all that stuff.

```
cd $HOME
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-headers-2.6.24-1-686_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-headers-2.6.24-1-common_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-2.6/linux-image-2.6.24-1-686_2.6.24-6_i386.deb
wget http://ftp.debian.org/debian/pool/main/l/linux-kbuild-2.6/linux-kbuild-2.6.24_2.6.24-1_i386.deb
wget http://ftp.de.debian.org/debian/pool/main/l/linux-2.6/linux-2.6_2.6.24.orig.tar.gz
sudo apt-get install gcc-4.1
sudo apt-get -f install
sudo dpkg -i linux-image-2.6.24-1-686_2.6.24-6_i386.deb linux-headers-2.6.24-1-686_2.6.24-6_i386.deb linux-headers-2.6.24-1-common_2.6.24-6_i386.deb linux-kbuild-2.6.24_2.6.24-1_i386.deb linux-headers-2.6.24-1-686_2.6.24-6_i386.deb 
sudo reboot

```
IMPORTANT!!! UNPLUG your Plextor device before it boots back up!  When the computer comes back up, hit escape to go into the grub menu and be sure to go down and select the kernel you just installed (2.6.24-1) and NOT the default 2.6.24-16 or -17.


OK - so I've just installed mythbuntu 8.04 and I'm trying your method above, however it no longer seems to work as I cannot locate 2.6.24-1 of anything.

Does anyone know where to grab this version of the files?  If its no longer download-able then these convertx devices just became very expensive doorstops.  ARGH! :confused:

---

### Post by sf_basilix on 2008-09-09
Well, I tried my best with mythbuntu.  It worked great with the last version, but 8.04 just wouldn't let me get my plextor convertx up and running, so I tried an alternative and it worked!!

Sorry to say this guys, but I did move to MythDora 5.  Installation was very smooth and I was able to even install software raid during the setup - something you can't quite do yet in Mythbuntu (at least not through the GUI).  After installing, I followed the instructions on [this website (click here)]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver") ([http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver)) under the Fedora Core install section.  It compiled great and video is working - no more split screen when I change channels.

To the Mythbuntu folks - I have to say great job on the interface - I think you're heading in a great direction and look forward to your next version to see if it will allow me to compile the plextor drivers again.  Until then, I am forced to use Mythdora.  I hope others out there who are struggling with this on Ubuntu will find this link and realize that the plextor isn't dead yet...

Thanks to all.

---

### Post by jnorth on 2008-11-04
Well, as of Intrepid's release, this issue is still not resolved.  I upgraded to Intrepid and installed the driver from nikosapi's site with no luck.

Issues this time around:

[LIST=1]
[*]Compilation failed - fixed using patch from bottom of [nikosapi talk page]("http://nikosapi.org/wiki/index.php/Talk:WIS_Go7007_Linux_driver")
[*]Module insert problem - attempting kernel compile to enable CONFIG_SND but I need the restricted drivers, and so have not completed this yet.  I would prefer to use the correct headers and build specifically from them, but unfortunately the linux-ubuntu-modules (lum) packages do not exist in Intrepid.
[/LIST]
So, back to where we started...

---

### Post by jnorth on 2008-11-04
For reference, here is the output of the attempt at loading the module:```
jnorth@mc01:~$ sudo modprobe go7007_usb
[sudo] password for jnorth: 
WARNING: Error inserting go7007 (/lib/modules/2.6.27-7-generic/extra/go7007.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting go7007_usb (/lib/modules/2.6.27-7-generic/extra/go7007-usb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
jnorth@mc01:~$ 

```

And here is what happens in syslog when that command is run:```
Nov  4 12:06:09 mc01 kernel: [141357.090146] go7007: disagrees about version of symbol video_devdata
Nov  4 12:06:09 mc01 kernel: [141357.090161] go7007: Unknown symbol video_devdata
Nov  4 12:06:09 mc01 kernel: [141357.090848] go7007: disagrees about version of symbol video_unregister_device
Nov  4 12:06:09 mc01 kernel: [141357.090854] go7007: Unknown symbol video_unregister_device
Nov  4 12:06:09 mc01 kernel: [141357.091209] go7007: disagrees about version of symbol video_device_alloc
Nov  4 12:06:09 mc01 kernel: [141357.091214] go7007: Unknown symbol video_device_alloc
Nov  4 12:06:09 mc01 kernel: [141357.091389] go7007: disagrees about version of symbol video_register_device
Nov  4 12:06:09 mc01 kernel: [141357.091394] go7007: Unknown symbol video_register_device
Nov  4 12:06:09 mc01 kernel: [141357.092035] go7007: disagrees about version of symbol video_usercopy
Nov  4 12:06:09 mc01 kernel: [141357.092044] go7007: Unknown symbol video_usercopy
Nov  4 12:06:09 mc01 kernel: [141357.092219] go7007: disagrees about version of symbol video_device_release
Nov  4 12:06:09 mc01 kernel: [141357.092227] go7007: Unknown symbol video_device_release
Nov  4 12:06:09 mc01 kernel: [141357.119743] go7007_usb: Unknown symbol go7007_read_addr
Nov  4 12:06:09 mc01 kernel: [141357.120277] go7007_usb: Unknown symbol go7007_remove
Nov  4 12:06:09 mc01 kernel: [141357.121179] go7007_usb: Unknown symbol go7007_boot_encoder
Nov  4 12:06:09 mc01 kernel: [141357.121716] go7007_usb: Unknown symbol go7007_parse_video_stream
Nov  4 12:06:09 mc01 kernel: [141357.122597] go7007_usb: Unknown symbol go7007_register_encoder
Nov  4 12:06:09 mc01 kernel: [141357.122826] go7007_usb: Unknown symbol go7007_alloc
Nov  4 12:06:09 mc01 kernel: [141357.123054] go7007_usb: Unknown symbol go7007_read_interrupt

```

---

### Post by mixersoft on 2009-01-24
I followed the instructions here, [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver")
and built the G07007 driver after applying all the patches found here, [http://home.comcast.net/~bender647/go7007/]("http://home.comcast.net/~bender647/go7007/").

Gorecord is working fine, and after configuring a recording profile (forgot to the first time), I can also tune a station and record video in mythbuntu.

However, I get no audio. CORRECTION: the audio is there, but the volume is very low.

Now I'm trying to recompile the kernel for sound according the the instructions here, [LIST]
[*] [http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy.2FHardy]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Dapper.2FEdgy.2FFeisty.2FGutsy.2FHardy")
[*] [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")
[*] [https://bugs.launchpad.net/ubuntu/+bug/204578/comments/4]("https://bugs.launchpad.net/ubuntu/+bug/204578/comments/4")
[/LIST]

The problem I get is the Intrepid no longer provides LUM headers, and when I try to reconfigure the kernel using make menuconfig, I see

```

--- Open Sound System (DEPRECATED)   
    --- OSS sound modules                       
 
```

and I don't see these choices

```

Now select the following
   <M> Advanced Linux Sound Architecture
   <M> Sequencer support
   <M> Sequencer dummy client
   <M> OSS Mixer API
   <M> OSS PCM (digital audio) API

        [*] OSS PCM (digital audio) API - Include plugin system

        [*] OSS Sequencer API
   <M> RTC Timer support

        [*] Use RTC as default sequencer timer
        [ ] Dynamic device file minor numbers

        [*] Support old ALSA API

        [*] Verbose procfs contents
        [ ] Verbose printk
        [ ] Debug

```

What do I do now?

---

### Post by mixersoft on 2009-01-25
It turns out, there is audio, but the volume is just real low. 

To recap, mythbuntu works with the ConvertX on Intrepid 8.10, but the volume is just real low on all the ConvertX recorded videos. I can play a video imported by MythDVD and the audio comes out just fine, so I know my system is working normally.


Maybe I don't have to recompile the kernel, but I'm still not sure how to fix things. will continue to search the forums.

---

### Post by jnorth on 2009-01-26
Awesome - I'm going to have to try this again when I get home.  I had finally sprung for a pcHDTV card to install in an old desktop to use as a dedicated backend/nfs box and have been using that for now, but I'd love to get this box working again as I think it did a better job with the SD channels.

As far as the low volume, have you changed it in recording profiles?  I'm sure that I had this problem at one point, but I went to (I think, going on memory here) Utilities>Setup>TV Settings>Recording Profiles and selecting the profile for the Plextor.  Then edit each of the listed profiles there on the 4th screen change the volume slider all the way to 100%.

Hope that helps!

---

### Post by mixersoft on 2009-01-27
> **jnorth said:**
> 

As far as the low volume, have you changed it in recording profiles?  I'm sure that I had this problem at one point, but I went to (I think, going on memory here) Utilities>Setup>TV Settings>Recording Profiles and selecting the profile for the Plextor.  Then edit each of the listed profiles there on the 4th screen change the volume slider all the way to 100%.

Hope that helps!

Done that. everything is at 100%, but still no volume. I seem to recall a post on modifying the wis Go7007 driver by writing new register values -- this was for an earlier version of ubuntu. But I can't find that anymore.

Can someone tell me if I need to try to recompile the kernel to fix this?

---

### Post by studout on 2009-01-31
mixersoft;

Does the volume problem exist with gorecord/mplayer also, or just mythtv?  Knowing that might be helpful in narrowing down where the problem is.

---

### Post by mixersoft on 2009-01-31
> **studout said:**
> 
Does the volume problem exist with gorecord/mplayer also, or just mythtv?  Knowing that might be helpful in narrowing down where the problem is.



Good point. The volume of the audio is a problem both in gorecord AND mplayer.

---

### Post by studout on 2009-01-31
I'm sorry, I'm still not quite clear..
The sound level is a problem with grecord AND mplayer, ***_AND_*** MythTV ??

I'm running Intrepid, and reading up on this topic before I get to work getting my convertx running.

---

### Post by mixersoft on 2009-02-01
> **studout said:**
> I'm sorry, I'm still not quite clear..
The sound level is a problem with grecord AND mplayer, ***_AND_*** MythTV ??


yes.

---

### Post by jelle on 2009-02-02
Perhaps my personal efforts to get it working on Ubuntu Jaunty (9.04) can help. Details here:

[http://go7007.imploder.org/](http://go7007.imploder.org/)

---

### Post by jnorth on 2009-02-02
> **jelle said:**
> Perhaps my personal efforts to get it working on Ubuntu Jaunty (9.04) can help. Details here:

[http://go7007.imploder.org/](http://go7007.imploder.org/)

Cool - I'm still on Intrepid(2.6-27-11) at the moment, any chance it would work on my kernel?

---

### Post by jelle on 2009-02-02
I don't know, you'd have to try... I just looked at what it needed to be compatible with the 2.6.28 that comes with ubuntu jaunty... I didn't look if things were different or the same with 2.6.27... It may work, or it may need a small change somewhere.

---

### Post by jnorth on 2009-02-02
Cool.  I just tried on a clean install with no luck.  Trying to track down the errors now to see if I can figure them out.

You think if maybe I upgrade my kernel it would help?  Or do you see anything obvious from the below make error (struct video device has no member named num)that I could try?  Looks like you have more experience coding than I do :)

```
jnorth@mc02:~/Desktop/temp/wis-go7007-linux-0.9.8-3$ make

***** Using kernel source in /usr/src/linux-headers-2.6.27-11-generic *****

make modules -C /usr/src/linux-headers-2.6.27-11-generic M=/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.o
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.c: In function &#8216;go7007_v4l2_init&#8217;:
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.c:1943: error: &#8216;struct video_device&#8217; has no member named &#8216;num&#8217;
make[2]: *** [/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.o] Error 1
make[1]: *** [_module_/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
```EDIT:  Thought I'd take a look at the code where the error is and so far nothing clicks or turns up for me on google...

Old code (nikosapi) vs new code (jelle) in kernel/go7007-v4l2.c```
   1498         }
   1499         video_set_drvdata(go->video_dev, go);
   1500         ++go->ref_count;
   1501 
   1502         return 0;
   1503 }


   1939         }
   1940         video_set_drvdata(go->video_dev, go);
   1941         ++go->ref_count;
   1942         printk(KERN_INFO "%s: registered device video%d [v4l2]\n",
   1943                go->video_dev->name, go->video_dev->num);
   1944 
   1945         return 0;
   1946 }

```

---

### Post by jelle on 2009-02-02
I found a machine with 2.6.27 where I can try a compile. That struct member 'num' isn't used anywhere else, so it's probably harmless to remove it from the printk: If you make those lines (kernel/go7007-v4l2.c around line 1943) look like this, it should compile.

```
        printk(KERN_INFO "%s: registered device [v4l2]\n",
               go->video_dev->name);

```

Maybe that's all it needs (maybe not... of course always be prepared for kernel oopses or worse...)

---

### Post by jnorth on 2009-02-02
Well, that looked much better, the only errors were ```
make modules -C /usr/src/linux-headers-2.6.27-11-generic M=/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.o
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.c:1096: warning: &#8216;vidioc_enum_framesizes&#8217; defined but not used
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-v4l2.c:1117: warning: &#8216;vidioc_enum_frameintervals&#8217; defined but not used
  CC [M]  /home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-driver.o
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-driver.c: In function &#8216;init_i2c_module&#8217;:
/home/jnorth/Desktop/temp/wis-go7007-linux-0.9.8-3/kernel/go7007-driver.c:228: warning: format not a string literal and no format arguments

```After installing and running go7007_firmware_load, it seems to have worked, but it brings me back to the alsa node not found error.

I'm downloading the daily jaunty build currently, I've half a mind to try it tomorrow.  I don't have any problems with it being an alpha release if this works :)

By the way, really appreciate you dropping by with the suggestions, I noticed you're new to the forum at least, so that's pretty cool!

EDIT - yep, I'm going to leave jaunty downloading and call it a night.  I'll give Jaunty a try tomorrow and see what luck I have, before coming back to this.

---

### Post by jelle on 2009-02-03
If that alsa message is 'Unable to find associated ALSA device node' from gorecord, then that is because gorecord (in apps/gorecord.c) does some searching around in /sys to find the audio device that comes from the same driver, but that logic is probably flawed for recent kernels (at least it doesn't work on my 2.6.28 )... on my wordpress page I show the gorecord command I used myself. 

I found which device to use by doing this:

```
$ ls -ld /sys/class/sound/pcmC*
lrwxrwxrwx 1 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC0D0c -> ../../devices/pci0000:00/0000:00:14.5/sound/card0/pcmC0D0c
lrwxrwxrwx 1 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC0D0p -> ../../devices/pci0000:00/0000:00:14.5/sound/card0/pcmC0D0p
lrwxrwxrwx 1 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC1D0c -> ../../devices/pci0000:00/0000:00:14.6/sound/card1/pcmC1D0c
lrwxrwxrwx 1 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC1D0p -> ../../devices/pci0000:00/0000:00:14.6/sound/card1/pcmC1D0p
lrwxrwxrwx 1 root root 0 2009-02-03 00:50 /sys/class/sound/pcmC2D0c -> ../../devices/pci0000:00/0000:00:13.2/usb3/3-3/3-3:1.0/sound/card2/pcmC2D0c
$ ls -ld /sys/class/sound/pcmC*/device/dsp*
drwxr-xr-x 3 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC0D0c/device/dsp
drwxr-xr-x 3 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC0D0p/device/dsp
drwxr-xr-x 3 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC1D0c/device/dsp1
drwxr-xr-x 3 root root 0 2009-02-02 03:38 /sys/class/sound/pcmC1D0p/device/dsp1
drwxr-xr-x 3 root root 0 2009-02-02 03:47 /sys/class/sound/pcmC2D0c/device/dsp2

```

and then using the usb device (dsp2 in my case), because there is only one audio device from a driver on a usb bus on my laptop with the plextor plugged in (and it's the one that goes away when I unplug it)...

---

### Post by jelle on 2009-02-03
I made a new version that includes that compile fix for 2.6.27, and (I think) I fixed the audio device detection for gorecord (was quite trivial).

Get it here: [http://go7007.imploder.org/](http://go7007.imploder.org/)

---

### Post by jnorth on 2009-02-03
sweet.  i'm at work now and have done this via ssh, restarted usb by rmmod-ing and modprobing usbcore, and gorecord is working.  i've just scheduled a show in mythtv to check out that functionality, but seems great so far!

---

### Post by jnorth on 2009-02-03
So far it seems to be working!

---

### Post by jelle on 2009-02-03
That is great.

---

### Post by studout on 2009-02-07
Success!

Using the tarball from jelle at [http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2](http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2) and the instructions for Ubuntu at
[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver) I was able to compile and install
the driver for my ConvertX on Ubuntu 8.10 with kernel 2.6.27-7-generic.

As predicted at the wiki, usbfs was not mounted and this prevented the ConvertX from being recognized.
The copy of mountdevsubfs.sh that comes with 8.10 is not compatible with the patch provided in the tarball.
I was able to mount usbfs manually using the command ```
sudo mount -t usbfs none /proc/bus/usb
``` and then replugged the ConvertX.  The output of dmesg shows that it was recognized, and I am able to record video streams with it using gorecord.

jelle, Thank you very much :)
And thanks to everyone else that made this work!

---

### Post by drinfomike on 2009-02-08
I have also been successful in getting my ConvertX M402U to work on Intrepid using the procedure described by studout.

"Using the tarball from jelle at [http://go7007.imploder.org/wp-conten...x-098-4tar.bz2](http://go7007.imploder.org/wp-conten...x-098-4tar.bz2) and the instructions for Ubuntu at
[http://nikosapi.org/wiki/index.php/W...7_Linux_driver](http://nikosapi.org/wiki/index.php/W...7_Linux_driver) I was able to compile and install
the driver for my ConvertX on Ubuntu 8.10 with kernel 2.6.27-7-generic."

gorecord successfully records video and audio. 

Thanks jelle and all who contributed to the solution!:D

---

### Post by bigabe75 on 2009-02-19
I don't feel like I'm new to Linux... but I guess I'm new enough to working with drivers and such.  I'm getting stumped here.

Using 8.10, current kernel is 2.6.27-11-generic

Using the 0.9.8-4 driver from jelle, I am unable to run the 'make' command.  I get a whole bunch of errors.

```

root@mythtv:~/wis-go7007-linux-0.9.8-4# make

***** Using kernel source in /usr/src/linux-headers-2.6.27-11-generic *****

make modules -C /usr/src/linux-headers-2.6.27-11-generic M=/root/wis-go7007-linux-0.9.8-4/kernel
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.o
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:32:24: error: sound/core.h: No such file or directory
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:33:23: error: sound/pcm.h: No such file or directory
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:34:27: error: sound/initval.h: No such file or directory
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:38: error: ‘SNDRV_CARDS’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:38: error: ‘SNDRV_DEFAULT_IDX’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:39: error: ‘SNDRV_DEFAULT_STR’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:40: error: ‘SNDRV_DEFAULT_ENABLE_PNP’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:42: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:42: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:42: error: size of array ‘type name’ is negative
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:43: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:43: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:43: error: size of array ‘type name’ is negative
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:44: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:44: warning: type defaults to ‘int’ in declaration of ‘type name’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:44: error: size of array ‘type name’ is negative
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:60: error: variable ‘go7007_snd_capture_hw’ has initializer but incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:61: error: unknown field ‘info’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:61: error: ‘SNDRV_PCM_INFO_MMAP’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:62: error: ‘SNDRV_PCM_INFO_INTERLEAVED’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:63: error: ‘SNDRV_PCM_INFO_BLOCK_TRANSFER’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:64: error: ‘SNDRV_PCM_INFO_MMAP_VALID’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:64: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:64: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:65: error: unknown field ‘formats’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:65: error: ‘SNDRV_PCM_FMTBIT_S16_LE’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:65: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:65: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:66: error: unknown field ‘rates’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:66: error: ‘SNDRV_PCM_RATE_48000’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:66: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:66: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:67: error: unknown field ‘rate_min’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:67: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:67: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:68: error: unknown field ‘rate_max’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:68: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:68: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:69: error: unknown field ‘channels_min’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:69: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:69: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:70: error: unknown field ‘channels_max’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:70: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:70: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:71: error: unknown field ‘buffer_bytes_max’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:71: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:71: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:72: error: unknown field ‘period_bytes_min’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:72: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:72: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:73: error: unknown field ‘period_bytes_max’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:73: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:73: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:74: error: unknown field ‘periods_min’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:74: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:74: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:75: error: unknown field ‘periods_max’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:75: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:75: warning: (near initialization for ‘go7007_snd_capture_hw’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘parse_audio_stream_data’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:81: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:82: error: implicit declaration of function ‘bytes_to_frames’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:86: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:87: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:90: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:91: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:93: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:93: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:98: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:98: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:101: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:105: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:108: error: implicit declaration of function ‘snd_pcm_period_elapsed’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: At top level:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:112: warning: ‘struct snd_pcm_hw_params’ declared inside parameter list
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:112: warning: its scope is only this definition or declaration, which is probably not what you want
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_hw_params’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:114: error: implicit declaration of function ‘snd_pcm_substream_chip’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:114: warning: initialization makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:117: error: implicit declaration of function ‘params_buffer_bytes’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:118: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:119: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:120: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:121: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:122: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:124: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_hw_free’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:131: warning: initialization makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:134: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:135: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:136: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_capture_open’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:142: warning: initialization makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:150: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_capture_close’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:160: warning: initialization makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_pcm_trigger’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:174: warning: initialization makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:178: error: ‘SNDRV_PCM_TRIGGER_START’ undeclared (first use in this function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:178: error: (Each undeclared identifier is reported only once
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:178: error: for each function it appears in.)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:183: error: ‘SNDRV_PCM_TRIGGER_STOP’ undeclared (first use in this function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: At top level:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:192: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘go7007_snd_pcm_pointer’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_pcm_page’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:203: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: At top level:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:206: error: variable ‘go7007_snd_capture_ops’ has initializer but incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:207: error: unknown field ‘open’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:207: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:207: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:208: error: unknown field ‘close’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:208: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:208: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:209: error: unknown field ‘ioctl’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:209: error: ‘snd_pcm_lib_ioctl’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:209: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:209: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:210: error: unknown field ‘hw_params’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:210: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:210: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:211: error: unknown field ‘hw_free’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:211: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:211: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:212: error: unknown field ‘prepare’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:212: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:212: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:213: error: unknown field ‘trigger’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:213: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:213: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:214: error: unknown field ‘pointer’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:214: error: ‘go7007_snd_pcm_pointer’ undeclared here (not in a function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:214: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:214: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:215: error: unknown field ‘page’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:215: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:215: warning: (near initialization for ‘go7007_snd_capture_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:218: warning: ‘struct snd_device’ declared inside parameter list
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_free’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:220: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: At top level:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:229: error: variable ‘go7007_snd_device_ops’ has initializer but incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:230: error: unknown field ‘dev_free’ specified in initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:230: warning: excess elements in struct initializer
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:230: warning: (near initialization for ‘go7007_snd_device_ops’)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_init’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:251: error: implicit declaration of function ‘snd_card_new’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:251: warning: assignment makes pointer from integer without a cast
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:256: error: implicit declaration of function ‘snd_device_new’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:256: error: ‘SNDRV_DEV_LOWLEVEL’ undeclared (first use in this function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:262: error: implicit declaration of function ‘snd_card_set_dev’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:263: error: implicit declaration of function ‘snd_pcm_new’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:265: error: implicit declaration of function ‘snd_card_free’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:269: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:269: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:270: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:270: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:271: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:271: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:272: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:274: error: dereferencing pointer to incomplete type
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:275: error: implicit declaration of function ‘snd_pcm_set_ops’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:275: error: ‘SNDRV_PCM_STREAM_CAPTURE’ undeclared (first use in this function)
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:278: error: implicit declaration of function ‘snd_card_register’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c: In function ‘go7007_snd_remove’:
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:298: error: implicit declaration of function ‘snd_card_disconnect’
/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.c:299: error: implicit declaration of function ‘snd_card_free_when_closed’
make[2]: *** [/root/wis-go7007-linux-0.9.8-4/kernel/snd-go7007.o] Error 1
make[1]: *** [_module_/root/wis-go7007-linux-0.9.8-4/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2


```

Thanks for any help you folks can give.

---

### Post by jnorth on 2009-02-20
I'm about to reinstall my frontend in the next 30 minutes and will try to check it out then.

---

### Post by bigabe75 on 2009-02-21
> **jnorth said:**
> I'm about to reinstall my frontend in the next 30 minutes and will try to check it out then.

Thanks...I just got it compiled... will continue the rest of the howto.  Following another thread  ([this one]("http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver#Ubuntu_Hardy_with_kernel_.3C.3D_2.6.46-17"))I had renamed the /usr/src/linux-headers-2.6.27-11-generic/include/sound to sound-blacklisted, so the make was failing.  

I did that before I found jelle's newer driver.  Hopefully, now that I have it compiled the rest will go smoothly.

---

### Post by jnorth on 2009-02-22
Cool - I ran into some major issues with lirc (which is why I was reinstalling to start with) that took longer than I though.
Just for kicks here's what I did just now on a clean install - current system is:```
2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686 GNU/Linux
```
[LIST]
[*]Install some packages needed:```
sudo apt-get install linux-headers-generic fxload libncurses5-dev
```
[*]Download Jelle's drivers, extract, and go to dir:```
wget http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2
mv wis-go7007-linux-098-4tar.bz2 wis-go7007-linux-098-4.tar.bz2
tar -jxvf wis-go7007-linux-098-4.tar.bz2 
cd wis-go7007-linux-0.9.8-4/
```
[*]Make and install:```
make
sudo make install
```
[*]Fix usbfs by adding a line to fstab (subsitute vi with nano or gedit if you prefer those)(BE CAREFUL!)```
sudo vi /etc/fstab
``` and add this line```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
[*]Reboot!  (Yeah I know you can load without rebooting but for new users this is easier, plus, it will test to ensure it comes back up later down the road on other reboots)
[/LIST]
***If*** all went well, on reboot you should be able to do a ls -l /dev/video* and see a new device listed - congratulations.  If you don't, well, post here and we'll see what we can do - but I think Jelle's the man on this one for getting this driver going!

Good luck!

---

### Post by mixersoft on 2009-03-05
> **studout said:**
> Success!

Using the tarball from jelle at [http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2](http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2) and the instructions for Ubuntu at
[http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver](http://nikosapi.org/wiki/index.php/WIS_Go7007_Linux_driver) I was able to compile and install
the driver for my ConvertX on Ubuntu 8.10 with kernel 2.6.27-7-generic.


I'm using 2.6.27-11 and followed the instructions using the jelle tarball. USB loads fine, and I get video but still no audio -- or the audio is VERY faint. 

Here is what I see from my dmesg:

```

[  929.406148] usb 5-6: configuration #1 chosen from 1 choice
[  929.553162] Linux video capture interface: v2.00
[  929.568258] go7007-usb: probing new GO7007 USB board
[  929.568268] firmware: requesting go7007fw.bin
[  929.853188] go7007: registering new Plextor PX-TV402U-NA
[  929.872465] wis-saa7115: initializing SAA7115 at address 32 on WIS GO7007SB EZ-USB
[  929.947964] wis-uda1342: initializing UDA1342 at address 26 on WIS GO7007SB EZ-USB
[  929.962151] wis-sony-tuner: initializing tuner at address 96 on WIS GO7007SB EZ-USB
[  929.962191] wis-sony-tuner: type set to 202 (Sony NTSC (BTF-PB463Z))
[  929.962649] go7007: registered device [v4l2]
[  929.962681] usbcore: registered new interface driver go7007
[  935.312332] go7007: unsupported ioctl -1069263324
...
[  935.321370] go7007: unsupported ioctl -1069263324
[  935.345086] wis-sony-tuner: tuning to frequency 67.2500 (VHF_L)
[  935.388105] firmware: requesting go7007tv.bin
[  940.586654] firmware: requesting go7007fw.bin


```

Any thoughts? or should I try a different version of the Kerne?

---

### Post by jelle on 2009-03-05
The dmesg looks the same as it does on mine.

I just made a little test recording on that same frequency (ntsc channel 4), using "sudo gorecord -input 2 -tvchan -ntsc-cable:4 -bitrate 1500 -duration 30 capture.avi" and the sound in it is fine.

So, I don't know... but maybe try this:

Maybe you could check if the audio device it's using makes sense. Gorecord prints 'using audio device /dev/dspN', where /dev/dspN should be a device that doesn't exist on your system if you don't have the go7007 plugged into the usb...

Or maybe it's your playback program, or something else in the playback (mixer settings, audio cables, etc)? Perhaps your playback program, or audio card output (spdif?) doesn't like it that the audio is sampled at 48KHz, or that the .avi has the audio in it in uncompressed PCM format?

Maybe it's the tv channel, try a different channel? Check to make sure the cable signal is good?

Good luck ;-)

---

### Post by mixersoft on 2009-03-06
Jelle, 

You are fantastic. The problem was simple, using ntsc-bcast I get video but no sound. change it to ntsc-cable and it works.

many thanks

---

### Post by heyjonathan on 2009-04-07
I was able to get this working correctly about two weeks ago by following the above instructions.  Things were working fine - lots of recording through MythTV - but today things stopped working.

I think the problem started when Ubuntu released an upgrade to the 2.6.27-11-generic kernel.  

My /var/log/unattended-upgrades/unattended-upgrades.log mentions that linux-headers-2.6.27-11, linux-libc-dev, linux-headers-2.6.27-11-generic, and linux-image-2.6.27-11-generic were updated.  

I'm pretty confident this is the problem, because things were recording fine this afternoon, and when I got home and saw the "Restart Required" icon and rebooted, the driver failed to load.

Output of dmesg | grep "7007"
[   13.317696] snd_go7007: disagrees about version of symbol snd_pcm_new
[   13.317761] snd_go7007: Unknown symbol snd_pcm_new
[   13.317883] snd_go7007: disagrees about version of symbol snd_card_register
[   13.317943] snd_go7007: Unknown symbol snd_card_register
[   13.318056] snd_go7007: disagrees about version of symbol snd_card_free
[   13.318116] snd_go7007: Unknown symbol snd_card_free
[   13.318250] snd_go7007: disagrees about version of symbol snd_pcm_lib_ioctl
[   13.318310] snd_go7007: Unknown symbol snd_pcm_lib_ioctl
[   13.318455] snd_go7007: disagrees about version of symbol snd_card_free_when_closed
[   13.318524] snd_go7007: Unknown symbol snd_card_free_when_closed
[   13.318640] snd_go7007: disagrees about version of symbol snd_pcm_set_ops
[   13.318700] snd_go7007: Unknown symbol snd_pcm_set_ops
[   13.318817] snd_go7007: disagrees about version of symbol snd_device_new
[   13.318877] snd_go7007: Unknown symbol snd_device_new
[   13.318995] snd_go7007: disagrees about version of symbol snd_card_disconnect
[   13.319054] snd_go7007: Unknown symbol snd_card_disconnect
[   13.319204] snd_go7007: no symbol version for snd_card_create
[   13.319262] snd_go7007: Unknown symbol snd_card_create
[   13.319376] snd_go7007: disagrees about version of symbol snd_pcm_period_elapsed
[   13.319444] snd_go7007: Unknown symbol snd_pcm_period_elapsed
[   13.483174] go7007: Unknown symbol go7007_snd_remove
[   13.483544] go7007: Unknown symbol go7007_snd_init
[   13.916876] go7007_usb: Unknown symbol go7007_read_addr
[   13.917100] go7007_usb: Unknown symbol go7007_remove
[   13.917422] go7007_usb: Unknown symbol go7007_boot_encoder
[   13.917639] go7007_usb: Unknown symbol go7007_parse_video_stream
[   13.917962] go7007_usb: Unknown symbol go7007_register_encoder
[   13.918087] go7007_usb: Unknown symbol go7007_alloc
[   13.918210] go7007_usb: Unknown symbol go7007_read_interrupt

/var/log/syslog has similar messages.

I thought perhaps I would just need to recompile the driver against the new headers, so I tried that.  Running make and sudo make install against Jelle's drivers seemed to complete successfully, but rebooting did not solve the problem.

Perhaps related, my sound also stopped working with this kernel upgrade.  However, I was able to re-install my alsa drivers (I'm using alsa-driver-1.0.19, which is not yet available in the Ubuntu repositories), and that at least fixed the sound issue.

I'm not a newbie, but neither am I much of a programmer - I can read code, but rarely do I create my own.  I'm very much open to suggestions on where to look to nail down what exactly is the problem.

Thanks in advance to anyone with ideas.

Jonathan

---

### Post by jelle on 2009-04-08
"disagrees about version of symbol snd_pcm_new"

Sounds like a versioning mismatch, so probably the driver doesn't match the kernel... 

I wouldn't be surprised if the dependencies were not complete, so that you need to do a 'make clean', or maybe even start from a freshly untarred source before rebuilding the driver.

---

### Post by hugha on 2009-04-25
I am a "less than experienced Linux user".  I am gradually trying to move away from Windows.

I have been using SageTV with a Plextor convertx PX Tv402 Win XP for some time and its works hands free flawlessly.

I got a good deal on another Plextor TV402. My hope was to use it on my Ubuntu box with the Linux version of Sage Tv.

I am now running 9.04. Where are we at this point in trying to get the Plextor box to work without constant tinkering.

It sounds like in some of the latest posts that although some have got it working that it is "iffy" at best. Do some of the latest posts showing how do a working installation apply for 9.04.

I am not the sharpest technical programmer type user (Caution: windows user) so I am trying to get a grasp on the step by step to have a go at it.

Thanks for your patience:)

---

### Post by jnorth on 2009-04-26
I haven't yet tried on 9.04 but I did just install a vm instance of 9.04 for testing and will try to see how this is working with the latest version.

As far as the driver being "iffy" on intrepid and earlier versions though, I have not had any issues, works perfectly for me, so know that if jaunty doesn't work, you can always use intrepid or earlier.

Will _try_ to update tomorrow evening when I have had a chance to try the latest...

---

### Post by heyjonathan on 2009-04-28
I've been messing with this off and on for the past few weeks.  You may recall that everything was working great for me on Hardy, and for a bit with Intrepid, but stopped after an automatic kernel upgrade.  Beginning with that upgrade, I started having issues.

I wasn't able to get things working with Intrepid, but with Jaunty being released, I figured I'd give that a try - after all, there isn't much point in fixing Intrepid just to turn around and upgrade in a week or two - so I've installed a fresh version of Jaunty.

Anyway, all this to say that, using the 0.9.8.4 driver and the directions mentioned most recently in this thread, everything compiled and installed fine.

I didn't want to have to restart the computer after installing the driver (lazy, I guess), but was able to activate it with

sudo modprobe go7007-usb
sudo /etc/init.d/udev restart

and then connecting the device.  Since then, I've checked that the device loads properly on reboot.

I wish we could create a package for this driver - but I don't know how to make a package that will somehow recompile when the kernel changes.

Anyway, thanks to everyone who's put effort into making this work.  I still consider my plextor the easiest way to capture non-hd tv - so much so that I'm looking for another one (or two!) to use.

Jonathan

---

### Post by jnorth on 2009-05-06
Yeah just a confirmation that jelle's source is still working with 9.04.  Obviously you'll still need to build to suit your new kernel, can't just upgrade.

But - clean install is working fine for me.

---

### Post by jelle on 2009-05-19
I noticed myself that the devices can be unreliable if there are certain other USB devices on the same USB bus. I once had a usb ir-blaster on the same bus (or was it a USB cable to a UPS, I forgot), and with it it would not always work right, but without that, it would work fine all the time. Some mainboard have multiple USB buses, so on those you can work around that by using a different USB plug.

Repeating the link: [http://go7007.imploder.org](http://go7007.imploder.org)

---

### Post by studout on 2009-07-26
Hi,
I've been using the convertx successfully for a while now.
However, I have noticed that when I'm recording (at least from the tuner)
that it has fluctuating tint problems, and compression artifacts.

This happens over that course of about 5 seconds; it will transition from
a slight red hue to green.  Then jump to red, and slowly transition green
again. At the same time, it will get lightly multi-colored rectangular
compression artifacts around sharp edges like white text on dark
background, or the annoying bug/logo that networks put in the lower right
corner of the screen, and then become crisp again, and then repeat the
cycle.

Does anyone else have this problem?
This is not untenable, but it is noticeable, and certainly
detracts from the overall quality of the process.

Here's the command I'm using..
```
gorecord -bitrate 4000 -input 2 -tvchan ntsc-cable:70
-duration 7230 -width 720 -height 576 -brightness 128
-contrast 64 -saturation 64 -hue 0 filename.avi
```

I thought that the problem might be with the AGC, but explicitly setting
the values did not fix the problem.

Other things I notice...
It absolutely refuses to capture all 525 NTSC lines.. maximally capturing
the middle 480.
Also; during some more abrupt video transitions, it will lose vsync and I
can see the scan lines between frames/fields, and the captioning in the
middle of the space between them.

I'm not so much looking for trouble shooting help, but more interested
in seeing if anyone has these problems also, and if anyone might know
exactly what is wrong and should be fixed.

I expect to upgrade to Jaunty soon, and will report back with the results.

Also; when I install a new machine, the first thing I do is disable auto
update features.  Regression errors and reverse-incompatibility are
extremely common.  Once you have it installed and it's working, just leave
it alone.  Letting the auto updater install new packages is a
time-bomb waiting to kill your machine; as we can see.

Take Care,
studout

---

### Post by jnorth on 2009-07-27
I get results very similar to yours the first 2-3 seconds of a new recording, but then all is normal throughout the remainder no matter how long or short, or what commands I add.  Sorry...

---

### Post by roguegeer on 2009-09-02
Howdy, trying to compile on my 64bit system (installed using the server disc and then desktop installed afterwards). I run into a seemingly simple problem:


```

me@mine:~/wis-go7007-linux-0.9.8-4$ make

***** Using kernel source in /lib/modules/2.6.28-15-server/build *****

make modules -C /lib/modules/2.6.28-15-server/build M=/home/wbrooke/wis-go7007-linux-0.9.8-4/kernel
make[1]: Entering directory `/lib/modules/2.6.28-15-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.28-15-server/build'
make: *** [all] Error 2

```

is there any chance I can get it to build under that kernel? 

cheers.

---

### Post by fnemec on 2009-09-07
Hi guys, 

just to ley you know. With this fix I was able to successfully compile and execute gorecord on my Fedora 10, too . Strangely, I have to reboot first in order to start capturing. I hope this help someone running on the same problem. 

Thanks, Nemec

---

### Post by jelle on 2009-10-03
FYI, for Ubuntu karmic (9.10), or other distro's with Linux kernel 2.6.31, you'll need another updated version. I made a 0.9.8-5 version for that, details here:

[http://go7007.imploder.org/](http://go7007.imploder.org/)

---

### Post by bakelitedoorbell on 2009-10-21
Are there known issues with compiling this driver on 64bit Jaunty?  Or should there be no difference between the results on 32bit and 64bit?

---

### Post by Shockwav on 2009-11-08
Mythbuntu 9.10 with Myth 0.22 and I get this after “sudo make install” of driver wis-go7007-linux-0.9.8-5 and a reboot.

mythbox@mythbox:~$ lsusb
Bus 002 Device 003: ID 093b:a004 Plextor Corp. ConvertX TV402U XLOADER

No /dev/video device exists. “sudo mount -t usbfs none /proc/bus/usb” works and this is the result
mythbox@mythbox:~$ lsusb
Bus 002 Device 005: ID 093b:a104 Plextor Corp. ConvertX PX-TV402U/NA

I added “ACTION==”add”, ATTRS{idVendor}==”093b”, ATTRS{idProduct}==”a104&#8243;, RUN+=”/usr/sbin/go7007_firmware_load”" to /etc/udev/rules.d/91-wis-ezusb.rules and I am now able to set up the device.

It does not appear to survive a reboot and I have to “sudo mount -t usbfs none /proc/bus/usb” to reacquire the device.

I’m also getting the “green screen” from the device as it connects and if I change channels it goes black, then kicks out with an “Unrecoverable recorder error”

Any ideas? Device works fine in Mythdora 4.

---

### Post by macris on 2009-11-14
i experienced the same thing as shockwave half a year ago: got an error when zapping in mythtv in combination with the PX TV402U from plextor. i also got the error / problem when i chaned channels. looked a bit into some logging and made a simple work-around. i am not used to proposing code patches, but see my patch-dump below in go7007-v4l2.c. it adds a few lines. maybe the patch can be added in the next release of [http://go7007.imploder.org/](http://go7007.imploder.org/)

basically mythtv does two calls to the driver to resetting/change some formatting stuff (changing PAL to PAL, etc) and that the driver can’t handle this (not supported). actually it is not functional for mythtv to reset/change these settings as they are initially set and will never really change, so it is ok to ignore the unsupported calls and simply go ahead. this is what the patch does.

hope this works for you, guys!

— go7007-v4l2.c 2009-11-14 09:37:34.766370474 +0100
+++ ../../go7007-v4l2.c 2009-09-13 06:49:34.000000000 +0200
@@ -1740,12 +1740,6 @@
}
#endif
default:
- if( (int)cmd == -1073457625 || (int)cmd == 1074288152 )
- {
- printk(KERN_DEBUG “go7007: MR caught unsupported ioctl %d\n”, cmd);
- return 0;
- }
-
printk(KERN_DEBUG “go7007: unsupported ioctl %d\n”, cmd);
return -ENOIOCTLCMD;
}

---

### Post by studout on 2010-02-27
I have the convertx partially working under Ubuntu 9.10 (kernel; 2.6.31-17-generic-pae)
I did not see a concise list of commands to use for getting it running.
I decided to post what I eventually used.
```

sudo apt-get install linux-headers-generic fxload libncurses5-dev
wget http://go7007.imploder.org/wp-content/uploads/2009/11/wis-go7007-linux-098-5b.tgz
tar -zxf wis-go7007-linux-098-5b.tgz 
cd wis-go7007-linux-0.9.8-5/
make
sudo make install
*### plug convertx into computer ###*
sudo ./go7007_firmware_load 
gorecord -input 0 -duration 30 test.avi

```
Thanks again to jelle and all the others that made this possible.
The problem comes in when gorecord sporadically freezes.
I can use Crtl-C to kill it, and then it prints the message
```
VIDIOC_STREAMOFF: Input/output error
```
to the console, and then I get my prompt back.
I can immediately restart it and it seems to record normally after that.
I don't instantly know about the freeze, so by the time I kill it and restart, it's hard to say how much time has passed.
So far this has happened three times.  Once at about 24m, then at 1h 26m, and again at 1h 45m.

The convertx never had any error like this under 8.10, from when I originally posted here, until the point when I plugged it into the computer running 9.10

---

### Post by jelle on 2010-02-27
I'm using it myself on a 2.6.31-11-generic-pae kernel from ubuntu, and have almost no problems in my mythtv setup using a bunch of these plextor tv402u's. 

I say almost no problems, because about maybe three times per year I get a usb error (some urb timeout in the kernel log), and from that moment on one of the plextors isn't working anymore while the others still work fine. A powerycle of the plextor then isn't enough to fix it, nor is reloading the driver. I usually just reboot the whole system when I see that, including powercycling the plextors. It really doesn't happen very often considering I have a total of 7 of these devices on the machine, and they are pretty busy (no I don't watch that much tv, most of it gets deleted unwatched, it's just really nice to have a wide choice of programming available on-demand). So, either the go7007 driver (or the usb driver?) probably doesn't always handle usb timeouts correctly, or maybe the cause of that problem is in the firmware. It seems to be triggered during the firmware upload. I don't know much more about it.

One thing that you could look at is the other devices on the usb bus: I've had some problems in the past when the USB bus that the plextor was on also had another device on it, and it apparently was interfering. It was an older usb 1.1 device in my case, and when I moved it to a different usb bus (some of the usb connectors on that mainboard were on a different usb bus), the problem went away.

Other things you could check are: Maybe your plextor is getting too hot, or maybe its power supply isn't working as well as it should.

---

### Post by studout on 2010-02-27
Thank you for the pointers.
I will report back if there are any remarkable changes.

---

### Post by mlord on 2010-11-26
I have just (today) picked up one of these great tuners, for eventual use with MythTV.

I've built the out of tree driver on kernel 2.6.36 (the one in staging craps out, so pass on that).  The out-of-tree one works fine, giving great video/audio recordings from the tuner with gorecord.

But.. Mythtv (0.24) gets only the picture, no audio.  I've got the OSS emulation module loaded, and the correct /dev/dsp2 audio device set up in myth, but no sound.

Strange.  Any ideas ?

---

### Post by mlord on 2010-11-26
Okay.. this is weird.

See, I have a second (main) MythTV system, running 2.6.36 and Mythtv-0.23.1-fixes.  On that system, the out-of-tree driver builds/runs mostly fine, with both video and audio in Mythtv!

One difference, is that on that system, there are /dev/vbi[1-2] devices.. including one for the ConnectX USB tuner.  But not on the other (newer) MythTV box.

Still sorting through things, but the Good News(tm) is that this driver still works even on 2.6.32, 2.6.35, and 2.6.36 kernels on the Mythtv-0.23.1-fixes system.

Cheers

---

### Post by mlord on 2010-11-27
Okay, got it all sorted.  Pilot error.  :)

The original system was having issues because I hadn't rebuilt the kernel there without the staging drivers configured.  As soon as I reconfigured/rebuilt the 2.6.36 kernel without the go7007 staging drivers, all was working well.  With Mythtv-0.24, even.

Well, almost all.. on both systems, channel-changing in "live tv" fails -- but it does work fine for back-to-back recordings, so well enough for me!

Cheers

---

### Post by felinoel on 2012-12-17
> **jnorth said:**
> Cool - I ran into some major issues with lirc (which is why I was reinstalling to start with) that took longer than I though.
Just for kicks here's what I did just now on a clean install - current system is:```
2.6.27-12-generic #1 SMP Thu Feb 5 09:26:35 UTC 2009 i686 GNU/Linux
```
[LIST]
[*]Install some packages needed:```
sudo apt-get install linux-headers-generic fxload libncurses5-dev
```
[*]Download Jelle's drivers, extract, and go to dir:```
wget http://go7007.imploder.org/wp-content/uploads/2009/02/wis-go7007-linux-098-4tar.bz2
mv wis-go7007-linux-098-4tar.bz2 wis-go7007-linux-098-4.tar.bz2
tar -jxvf wis-go7007-linux-098-4.tar.bz2 
cd wis-go7007-linux-0.9.8-4/
```
[*]Make and install:```
make
sudo make install
```
[*]Fix usbfs by adding a line to fstab (subsitute vi with nano or gedit if you prefer those)(BE CAREFUL!)```
sudo vi /etc/fstab
``` and add this line```
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
```
[*]Reboot!  (Yeah I know you can load without rebooting but for new users this is easier, plus, it will test to ensure it comes back up later down the road on other reboots)
[/LIST]
***If*** all went well, on reboot you should be able to do a ls -l /dev/video* and see a new device listed - congratulations.  If you don't, well, post here and we'll see what we can do - but I think Jelle's the man on this one for getting this driver going!

Good luck!This doesn't work, does anyone have something that does?

---

