---
title: "MSI WInd U210 AMD Ralink WiFi Card HELP!!!"
date: 2009-09-25
forum: Hardware
---

### Post by ryman102990 on 2009-09-25
I just bought a MSI Wind U210 AMD MV-40 ultra-portable laptop.

Everything is working great on this sucker... except for the wireless card.

I believe it is a Ralink RT2860. I have scoured the web for any help but it seems like nothing has fixed my problem.

What I'm asking for is some help on getting this wireless card working using ubuntu. This won't only be helpful to me, it'll be helpful to anyone who purchases one of these machines in the future!

---

### Post by pwbdecker on 2009-09-25
I also have an MSI Wind U210 2GB/250GB.  Do you have the 1GB or the 2GB?  I can't even get 9.04 to boot from USB.  I've tried the Desktop x86 and Netbook Remix images, and they'll boot fine on my EEE PC 1000HE, but on my U210 it boots for a while and then drops into busybox and says this:

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Loading, please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell 


I'm not sure what I should do about this.  Which version of ubuntu are you using?

---

### Post by ryman102990 on 2009-09-25
I got the same exact error when booting all of the versions you tried. I did go back as far as 8.04 and found some success with installing that.

I searched around and found that there are some errors booting 9.04 from usb with some motherboards, and that they are working on it? I think they are at least.

I just can't for the life of me get the wireless to be even recognized.

I have been wanting to attempt to use NDISWrapper but it requires an extracted .exe or something with a .sys file. Every link i have tried to click on has been "error 404"

It seems like everything is a dead end right now...

---

### Post by Odemia on 2009-09-25
> **ryman102990 said:**
> 
I got the same exact error when booting all of the versions you tried. I did go back as far as 8.04 and found some success with installing that.
...
I have been wanting to attempt to use NDISWrapper but it requires an extracted .exe or something with a .sys file. Every link i have tried to click on has been "error 404"


I just started working on getting linux/ubuntu installed on my u210.  9.04 appears to be a no go for me as well.  Good to know it is not just me.

I will try 8.04 later tonight or tomorrow morning.  I have a driver cd with rt2860.sys files on it (came in box with u210).  If I get 8.04 working I will try to ndiswrapper that and report back.

---

### Post by ryman102990 on 2009-09-25
yeah that sounds good. 8.04 should be a pretty easy set up, it didn't have any errors and worked the first try.

definitely let me know how that goes, i'll be trying some stuff too.

the one thing i have heard is that mandriva might have more luck?? i think what i'm going to do is to take mandriva for a spin... i've never used it but hell i'll do anything to avoid vista.

in case anyone is curious about windows 7, i loaded windows 7 x64 onto my 4gb flash drive and installed it in around 15 minutes. it runs real well on this things hardware. wireless works, but the next issue is the webcam and mic...

---

### Post by ryman102990 on 2009-09-25
oh also could post the exact files needed for the drivers on rapidshare or something like that? that would be awesome

---

### Post by Odemia on 2009-09-25
Sorry was running out for dinner.

[http://rapidshare.com/files/294331236/rt2860.zip.html](http://rapidshare.com/files/294331236/rt2860.zip.html)
Should only need the .sys and .inf posted the entire directory any ways.

Now back to installing 8.04.

---

### Post by Odemia on 2009-09-26
Ok posting from u210 over wireless.

I used ndisgtk, and it worked flawlessly.

I had to remove the CD line from /etc/fstab.  It kept trying to mount the usb drive I was using to transfer the .inf and .sys files as a CD until I removed the line.

I am using Ubuntu 8.04 i386 right now, I am planning on using some proprietary .debs that I know don't work on x86_64.  But when I have time I will try making another partition to play around with 64bit installs and upgrading to 9.04.  I have feeling upgrading to 9.04 will be of limited use given the lack of fglrx support for the X1250, but I am curious.

---

### Post by ryman102990 on 2009-09-26
congrats man good job. so you're running the 32bit? 

btw windows 7 is completely functional if you install the xp drivers etc.

---

### Post by Odemia on 2009-09-26
Turns out sound isn't working.  And yes currently using 32-bit.

[http://pastebin.ca/1580505](http://pastebin.ca/1580505)

Looks like there is a driver/library mismatch.  Also have not been able to confirm snd-hda-intel is the right driver to be loading with this chipset.

If I don't get audio working soon I will have to create another thread.

---

### Post by Odemia on 2009-09-26
BTW Just tried to boot from Ubuntu 8.04 x86_64 pendrive.  Got:

```

run_program: '/sbin/modprobe' abnormal exit

```

---

### Post by ryman102990 on 2009-09-27
well i think this might help:

I was reading reviews of this notebook on newegg.com because i was contemplating writing one myself, and stumbled on a review talking about installing ubuntu 9.04. Supposedly, if you remove and reinsert the pendrive while the kernel is loading, it will work. I guess the kernel hitches and that's why you get the error. I'll try it and post my results.

---

### Post by Odemia on 2009-09-27
I tried removing and replacing the usb drive with 9.04 but it didn't work for me.  Maybe I got the timing wrong.

Not sure that 9.04 is a good idea.  The X1250 is not supported by the fglrx used in 9.04 from what I have found.  If you don't care about 3d acceleration radeon hd driver should work fine.

I did get Kubuntu 8.04.2 64 bit to install, I guess the iso I was using before was old (8.04.0).  But now I need 64 bit drivers if I am going to use ndiswrapper.  I didn't find 64 bit drivers but I did find [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) which has linux source code that is supposedly tested with linux kernel up to 2.6.29.  Another idea to try another day.

Also upgrading to 8.10 fixed the version mismatch on my ALSA and audio started working great.

---

### Post by ryman102990 on 2009-09-27
it's after the black screen when you want to remove it. when it starts "loading" with "ubuntu" and the bar scrolling back and forth. remove the usb stick, and put it back in.

so i have ubuntu 9.04 working, and i also have ubuntu 9.10 a6 working. sound works great, the Fn key works with the wireless etc. however, even though the kernel *might* be newer, it seems they still don't have native support for the rt2860. the frustration hasn't ended yet...

---

### Post by ryman102990 on 2009-09-27
Also, I started a group in the forums specifically for this machine. I'm hoping to get a decent group of forum go-ers who buy this laptop to join so we can get a good pool of knowledge and fix this damn problem lol.

Here's the link: [http://ubuntuforums.org/group.php?groupid=636]("http://ubuntuforums.org/group.php?groupid=636")

---

### Post by pwbdecker on 2009-09-30
Hey can I ask you guys, what kind of battery life have you been getting out of your U210s?  I just got mine a week ago, last week it told me I had about 3:30hrs of total battery life and now it's down to about 2:45hrs.  I read some benchmarks online that said they got close to 4:45hrs, which is what I was hoping for.  Less than 3 hours is unacceptable and I'm not sure if the rest of you are getting these numbers or if mine is being whack.  Since I couldn't get a decent version of linux to run I've been running 32bit Windows 7 btw.

---

### Post by pwbdecker on 2009-09-30
Another note of interest, I just discovered this in another forum:

***Side note for those trying to install Ubuntu 9.04. The install will crash with the following error "modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory"
There is an easy fix for this that I have confirmed to work. Remove your USB pendrive/optical drive for a moment and then plug it back in, during the loading process. I removed mine a few seconds after the loading bar started moving back and forth. It then booted without error.

---

### Post by ryman102990 on 2009-10-01
[http://ubuntuforums.org/showthread.php?t=966185](http://ubuntuforums.org/showthread.php?t=966185)

I'm hoping this is the solution. I don't have time do do it right now, but i should have it done by tonight. I'll post back when i get it done, also feel free to try as well

I get ~4 hours or so battery life in windows, 4:30 in linux...

---

### Post by Odemia on 2009-10-02
Yeah I think I am coming in close to ryan.  I don't have a windows partition and I haven't paid too much attension to battery life but based on when I started using the computer last night and when I finished I am getting around 4 hours in Ubuntu 8.10 (basic web browsing, some sompiling, dimmed screen etc.).  I think on the most intensive battery run (doing octave simulations, compiling and running a game in wine) I still got 3 hours.

Hope I get a chance to try out the link over the weekend.  Would be nice to get rid of ndiswrapper.

---

### Post by yoshiki2 on 2009-10-08
once i receive mi wind 210, what ubuntu version should i install 9.04 9.10? and what bugs will i expect?

---

### Post by Odemia on 2009-10-11
> **yoshiki2 said:**
> once i receive mi wind 210, what ubuntu version should i install 9.04 9.10? and what bugs will i expect?

9.10 seems stable and I didn't have any problems with the live cd not wanting to load.  It is really a minor issue to get around if it doesn't want to load so the version shouldn't matter unless you want full 3d acceleration.  If you want 3d acceleration/compiz consider 8.04/8.10 to get fglrx working.

My current issues are wireless and suspend/hibernate.  By wireless I mean I am only able to get ndiswrapper working, so far no luck compiling drivers, find those driver CDs in the box and put them onto a usb drive.  Suspend/hibernate just goes to a black screen with cursor and hangs for me.

---

### Post by ryman102990 on 2009-10-11
Okay so here is my update.

Wireless- I have wireless working fully in Jaunty 9.04. I figured out that you need to install both the rt3090sta driver and the rt2860sta. If you need help with that post and I'll give the instructions on how to do that. I have figured out that this doesn't work with Karmic 9.10. Also, it doesn't work with the 64bit versions. This is only a fix for the i386 architectures.

3D acceleration- Fully functional. I have compiz installed and working 100%.

Sound works great.

With this setup in 9.04, I have everything functional but the webcam and mic. I will be looking into those things later. 

Remember to post with what you need help with.

---

### Post by Odemia on 2009-10-11
Ok been working on compiling drivers this weekend.  I am working on Kubuntu 9.04 i386 fully updated (2.6.28-15-generic), also tried to compile on Kubuntu 9.10 AMD64 (forget the exact kernel) with even less success.

While the windows drivers are rt2860, lspci revealed:
```
Network controller: RaLink Device 3090
```Went and got "2009_0903_RT3090_Linux_STA_v2.2.0.1" drivers from ralink website.  This driver appears to be a variation of the rt2860sta driver (ie the instructions and .dat file refer to rt2860).  Ran:
```
$ sudo apt-get install build-essentials linux-headers-`uname -r`
$ tar -xvzf 2009_0903_RT3090_Linux_STA_v2.2.0.1.tgz
$ cd 2009_0903_RT3090_Linux_STA_v2.2.0.1
```Checked in Makefile that "MODE = STA" and "TARGET = LINUX"
In os/linux/config.mk  checked that 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
Note: That is what the instructions say is necessary for the drivers to work with network manager (which I want).  Then ran
```
$ sudo make && make install
# output attached in output.txt
$ cd os/linux/
$ sudo insmod rt3090sta.ko
$ sudo ifconfig ra0 up
$ ifconfig ra0
ra0       Link encap:Ethernet  HWaddr 00:24:21:cb:41:57
          inet6 addr: fe80::224:21ff:fecb:4157/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:69924 (69.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:16
$ iwconfig ra0
ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
$ sudo iwlist ra0 scanning
# ...abbreviated, picked upa total of 14 cells...
Cell 04 - Address: 00:16:B6:2C:6D:F7                                             
                    Protocol:802.11g                                                       
                    ESSID:"Odemia"                                                      
                    Mode:Managed                                                           
                    Frequency:2.437 GHz (Channel 6)                                        
                    Quality:100/100  Signal level:-31 dBm  Noise level:-115 dBm            
                    Encryption key:on                                                      
                    Bit Rates:54 Mb/s

```Still have not gotten a connection though.  I have been tweaking /etc/Wireless/RT2860STA/RT2860STA.dat without success.

Just downloaded wpa_supplicant-0.6.9.tar.gz.  Going to retry compiling with:
```
# cd wpa_supplicant-x.x
# ./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d

```If you have other suggestions or get it to compile please leave a message.

---

### Post by Odemia on 2009-10-11
Long story short, rt3090sta was enough for me.  Did the exact same thing as listed above (no need for wpa_supplicant) and then remade the network entry in the Network Manager and rebooted.

PS I don't understand the comment about installing both rt2860sta and rt3090sta.  They both use the same internal symbol "RT2860STA" that prevents them from being loaded at the same time.

---

### Post by ryman102990 on 2009-10-11
yeah i realized that after i posted that but i was hoping nobody would notice haha

---

### Post by Odemia on 2009-10-12
Webcam works.  I got it to work by installing "webcam" I was then able to make the webcam appear as "Bus 001 Device 007: ID 5986:02c1 Acer, Inc" in lsusb and show up as /dev/v4l and /dev/video0.

Both Ekiga and VLC can get this video.  I will work on getting the mic to work tomorrow.

---

### Post by ryman102990 on 2009-10-12
awesome! I'm glad we're all working together and getting this thing working! hah

---

### Post by Odemia on 2009-10-12
Builtin mic works with arecord.

```
$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 4: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ alsamixer
```
Note: card 0 device 0 was my mic jack and card 0 device 4 was my built-in mic.
In alsamixer press F4 to display capture settings.  I had to switch "Input Source 1" to "Front Mic" see screenshot.  Also make sure your mic levels are set reasonably.  Then press "escape" to get out.
```
$ arecord -f cd -D hw:0,4 -d 5 test.wav
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
# Make some noise here
$ aplay test.wav
```

---

### Post by ryman102990 on 2009-10-12
alright awesome i followed your code and set up my mic, which isn't the best quality in the world, but it works. then, i downloaded skype. the interesting thing is that the video cam was supported immediately. it already had it set as the default video device and everything. the mic is the problem with skype. I'm not sure if you know how to get that working, but that seems to be beyond me as of right now. Thanks for the help so far man!

---

### Post by Odemia on 2009-10-13
Well Skype uses pulseaudio.  Everything I have done so far is alsa based.  So it is probably a pulse audio problem.

```
$ pactl
...
*** Source #0 ***
Name: alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0.monitor
Driver: modules/module-alsa-sink.c                                  
Sample Specification: s16le 2ch 44100Hz                             
Channel Map: front-left,front-right                                 
Owner Module: 3                                                     
Volume: 0: 100% 1: 100%                                             
Monitor of Sink: alsa_output.pci_1002_4383_sound_card_0_alsa_playback_0
Latency: 0 usec, configured 0 usec                                     
Flags: DECIBEL_VOLUME LATENCY                                          
Properties:                                                            
device.description = "Monitor of HDA ATI SB - ALC888 Analog"           
device.class = "monitor"                                               

*** Source #1 ***
Name: alsa_input.pci_1002_4383_sound_card_0_alsa_capture_0
Driver: modules/module-alsa-source.c                      
Sample Specification: s16le 2ch 44100Hz                   
Channel Map: front-left,front-right                       
Owner Module: 4                                           
Volume: 0:  67% 1:  67%                                   
Monitor of Sink: n/a                                      
Latency: 0 usec, configured 0 usec                        
Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
Properties:                                                        
device.api = "alsa"                                                
device.class = "sound"                                             
alsa.class = "generic"                                             
alsa.subclass = "generic-mix"                                      
alsa.name = "ALC888 Analog"                                        
alsa.id = "ALC888 Analog"                                          
alsa.subdevice = "0"                                               
alsa.subdevice_name = "subdevice #0"                               
alsa.device = "0"                                                  
alsa.card = "0"                                                    
alsa.card_name = "HDA ATI SB"                                      
alsa.long_card_name = "HDA ATI SB at 0xfe7f4000 irq 16"            
device.description = "HDA ATI SB - ALC888 Analog"                  
device.string = "front:0"                                          
device.buffering.buffer_size = "14336"                             
device.buffering.fragment_size = "1792"                            
device.access_mode = "mmap"
...

```

If I am not mistaken this appears to be a similar issue to the alsa problem.  The mic is on card 0 device 4, but only card 0 device 0 is set.  If that is correct I just have to figure out how to add the correct device to the pulse audio server.  That can be tomorrows task.

---

### Post by Odemia on 2009-10-13
Setting "Input Source" to "Front Mic" will get pulse to see the internal mic.  I tested this with Ekiga.  However these solutions require changing between the mic jack and internal mic manually.  Still need a more complete solution that will switch automatically when a mic is pluged in.

---

### Post by omniuni on 2009-10-16
Hey all,

First, I used the DKMS driver here: [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/~markus-tisoft/+archive/rt3090") for Ubuntu Jaunty and it worked perfectly. I've been in touch with Markus over eMail, and we're working on whether or not we can get a Karmic version of the driver working. The Jaunty package does not install on kernel 2.6.31+

Has anyone had any luck with the rt3090 wireless card on Karmic; ndiswrapper or otherwise? Is there a version of the rt2860 that works with Karmic? Everything works for me under Jaunty, but there are many updates in Karmic that I already appreciate, and I want to be able to use it when it is officially released.

Also, perhaps the person who posted the files needed for ndiswrapper before could repost them, the file is no longer available.

---

### Post by Odemia on 2009-10-17
Started using the kubuntu jaunty backports and suspend is working properly now.  I can now use kde4.3 with the rt3090 driver :P

omniuni (and others), is MSI not sending driver CDs with the U210-008US?  Those drivers should really be in the box with the computer.  They were in my U210-009CA box, I thought the only difference would be the keyboard, which has extra symbols so it can be a us english and csa french keyboard.  Anyways retry that link if you still need the drivers.

---

### Post by omniuni on 2009-10-17
Thanks! I've been at school, away from the driver disk. It just so happens I am going home tonight, and I will try that! From what I have read, the rt3090 has native and official support in the upcoming 2.6.32 kernel; it will be nice when I can use that! I'll let you know how it goes.

---

### Post by omniuni on 2009-10-20
[COLOR="SandyBrown"]Hooray! As of 2.6.31-14 ndiswrapper works with the drivers that Odemia mentioned before. I am working on Ubuntu Karmic, and connected to a WPA network, and so far, so good.

Thanks go to Odemia, and this should mean that you can go ahead and update to Karmic without too much worry. There are some really nice updates, including better graphics support for the Radeon that's in the Wind (HDMI works great!).[/COLOR]

EDIT:
It worked last night, but is not working today. Seems to be a problem with NDISwrapper. Still working on it. It connects to unencrypted networks just fine, but not WPA.

---

### Post by omniuni on 2009-10-26
For Ubuntu Karmic, a friend of mine has verified that [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.2.0.1-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.2.0.1-0ubuntu0~ppa1_all.deb) does indeed work, providing wireless support without NDISWrapper.

*Anyone know how to delete my two previous posts? I have been searching for about 5 minutes, and can edit them, but can not figure out how to delete them.

---

### Post by ryman102990 on 2009-10-27
are you sure about this? I would LOOOOVE to install Karmic, but i spent a lot of time setting up jaunty the way i wanted it and would hate to try to update and have to revert back to jaunty just to do the same setup all over again...

---

### Post by t413 on 2009-10-27
Am I sure? Sortof. 

I'm on my Msi wind u210 with the rt3090 working just fine with the updated 2.2.0.1-0ubuntu0~ppa1 package. However there are a few issues: This package builds the module and installs it, however whenever I restart you still need to run sudo modprobe rt3090sta for it to work. Also, I've been able to connect flawlessly to open networks but I'm not sure WPA networks work yet (I couldn't get it to connect to my network last night, but I only tried it once).

It's great to be able to use my laptop again..

-Tim

---

### Post by ryman102990 on 2009-10-27
do you know if it is supported in the 64-bit platform?

---

### Post by t413 on 2009-10-28
Yep. My MSI is x86-64 (U210). 

No update on the lack of WPA support, it still does not work.

---

### Post by imsael on 2009-10-30
Hey guys...I have a msi u210 with Vista installed...And i would soooo much prefer a linux distribution like unbuntu on my netbook...I usually use ubuntu 9.04 on my pc and I love it.

I've read your posts and I'm a bit worried to install ubuntu on my netbook....Would you suggest me to try? Or it's a no go for a casual ubuntu user?

If yes, which ubuntu version would you suggest???

Thanks

Daniel

---

### Post by Odemia on 2009-11-01
I can confirm the PPA works with Kubuntu 9.10 i386 on open networks and  WEP encrypted networks (not sure about WPA haven't tested).  Haven't tried x86-64 yet wither.

Also based on testing the ndiswrapper appears to be what was keeping me from being able to suspend properly.  When I compile from source or use the PPA suspend works fine, but hangs on trying to suspend with ndiswrapper is loaded.

imsael, I would suggest using 9.10 with the PPA to install the wireless drivers.  The PPA is really easy to install, just need a wired connection long enough to run "sudo add-apt-sources ppa:markus-tisoft/rt3090" and install rt3090sta using synaptic or command line.

---

### Post by imsael on 2009-11-02
Just installed karmic 64bits and it works great with the PPA...

I thought it would be more complicated then that with all the post above...Sounds work, energy saver, wifi....And it's much faster then Vista...Thanks a lot fo your help!!!

Daniel

---

### Post by ryman102990 on 2009-11-02
Well it seems like we have found the solution to this issue,so is everyone alright with me marking this as solved?

---

### Post by Odemia on 2009-11-02
+1 for solved

Good to hear the ppa has been confirmed to work with x86_64.  Looking forward to installing 64bit on one of the other partitions soon.

---

### Post by ryman102990 on 2009-11-02
yeah i'm glad to hear that too. I'm interested in finding out how the 64bit version is working out for those who are using it.

---

### Post by imsael on 2009-11-02
Correction.....About tue wi-fi. It will work with WEP security settings....but I haven'T succeed to make it work in WPA or WPA2...

But the rest is fine and works pretty well.....and again......soooo much faster then vista!!

---

### Post by speedbuggy on 2009-11-03
-- ryman102990

9.10 64-bit appears to work just as well as i386 .. WEP works but when I try to connect to my WPA it connects but fails to get an IP .. btw I am using the driver from ppa.launchpad.net/markus-tisoft/ . When I try a static config, I get connected but traffic fails to go anywhere. So the failure seems to be with the WPA connection.

---

### Post by ryman102990 on 2009-11-03
Alright, well it seems that we need to open up a new thread for this problem. I'll post the link here once I have it set up.

---

### Post by ryman102990 on 2009-11-03
Okay, I have started 2 new threads:

For help on WPA connection, I have started a thread here:

[http://ubuntuforums.org/showthread.php?t=1313132]("http://ubuntuforums.org/showthread.php?t=1313132")

I don't know the solution, but hopefully somebody will. Start posting and hopefully something will get done.

For help with the internal mic and webcam, I started a thread here:

[http://ubuntuforums.org/showthread.php?t=1313138]("http://ubuntuforums.org/showthread.php?t=1313138")

Again, don't have any solutions for these problems, but hopefully somebody else will.

---

### Post by pikapika2501 on 2009-11-17
Question, Is there a possibility or is it a "yes" answer that MSI Wind U210's wireless NIC and other peripherals will work automatically after installing ubuntu OS within its future release?

---

### Post by omniuni on 2009-11-17
The card will work automatically once the Kernel is updated to 2.6.32 and above, so future distributions will work out of the box. For Karmic, we are working on creating a PPA to support the card. So far, we have unecrypted and WEP encrypted wireless working. On Ubuntu Jaunty, the package works just fine with all wireless, and everything works pretty much out of the box after installing the driver package.

---

### Post by Odemia on 2009-11-17
Agree with omniuni, and here is some proof it is not just us saying it:
[http://www.phoronix.com/scan.php?page=news_item&px=NzUxOQ](http://www.phoronix.com/scan.php?page=news_item&px=NzUxOQ)

Also the PPA works for Karmic as well as Jaunty.  Also appears to work for both 32 and 64 bit.  Wpa support is the only draw back currently.

---

### Post by mic2damgood on 2009-12-18
Somebody please help me.. I got ubuntu 9.x.x and i can't get my wireless to work at all. I think the drivers for the ralink rt3090 ethernet wifi card are not there. I went to ralink website and they have the drivers there but i don't know how to install them. 
Please i'm new to linux and i am gonna need step by step instructions on how to get these drive installed and my wifi working. If anybody have any questions about my problem my email is [email]mic2damgood@hotmail.com[/email]

---

### Post by omniuni on 2009-12-18
Just use the driver here:

[https://launchpad.net/~markus-tisoft/+archive/rt3090](https://launchpad.net/~markus-tisoft/+archive/rt3090)

As of about 18 hours ago, the PPA was updated and now supports WPA.

---

### Post by mic2damgood on 2009-12-18
> **omniuni said:**
> Just use the driver here:

[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

As of about 18 hours ago, the PPA was updated and now supports WPA.


how do you do it. step by step instructions please

---

### Post by omniuni on 2009-12-18
1. Open a text editor as root:

KDE, Run: ```
kdesudo kate
```
Gnome or XFCE, Run: ```
gksu gedit
```

2. Open the file /etc/apt/sources.list and add to the end of it:
```

#RaLink Driver
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu YOUR_UBUNTU_VERSION_HERE main 
deb-src http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu YOUR_UBUNTU_VERSION_HERE main 
```

Of course, replace YOUR_UBUNTU_VERSION_HERE with "jaunty" or "karmic" etc.

3. From a terminal, run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 86F4C28E
```
```
sudo apt-get update
```
```
sudo apt-get install rt3090-dkms
```

4. You will need to reboot your computer.

Let me know how that works for you.

---

### Post by mic2damgood on 2009-12-18
> **omniuni said:**
> 1. Open a text editor as root:

KDE, Run: ```
kdesudo kate
```Gnome or XFCE, Run: ```
gksu gedit
```2. Open the file /etc/apt/sources.list and add to the end of it:
```

#RaLink Driver
deb http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu YOUR_UBUNTU_VERSION_HERE main 
deb-src http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu YOUR_UBUNTU_VERSION_HERE main 
```Of course, replace YOUR_UBUNTU_VERSION_HERE with "jaunty" or "karmic" etc.

3. From a terminal, run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 86F4C28E
``````
sudo apt-get update
``````
sudo apt-get install rt3090-dkms
```4. You will need to reboot your computer.

Let me know how that works for you.


thanks i'll let you know

---

### Post by mic2damgood on 2009-12-18
i didn't work it gave me the error
: Malformed line 55 in source list /etc/apt/sources.list (dist parse)
mickey-nb@mickey-nb:~$ sudo apt-get install rt3090-dkms
E: Malformed line 55 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
i copied web addrees i'm using the Karmic Koala verision how do i enter in the ubuntu verison?

---

### Post by mic2damgood on 2009-12-18
here is what the source list look like after i put it in :
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
#RaLink Driver
deb [http://ppa.launchpad.net/markus-tisoft/rt3090/karmic](http://ppa.launchpad.net/markus-tisoft/rt3090/karmic) main 
deb-src [http://ppa.launchpad.net/markus-tisoft/rt3090/karmic](http://ppa.launchpad.net/markus-tisoft/rt3090/karmic) main

is this right?

---

### Post by Bistrulli on 2009-12-19
> **mic2damgood said:**
> 
deb [http://ppa.launchpad.net/markus-tisoft/rt3090/karmic](http://ppa.launchpad.net/markus-tisoft/rt3090/karmic) main 
deb-src [http://ppa.launchpad.net/markus-tisoft/rt3090/karmic](http://ppa.launchpad.net/markus-tisoft/rt3090/karmic) main

is this right?

change the lines

    deb [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic]("http://ppa.launchpad.net/markus-tisoft/rt3090/karmic") main 
    deb-src [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu karmic]("http://ppa.launchpad.net/markus-tisoft/rt3090/karmic") main

the rt3090 will be correctly istalled.
i have followed the same procedure  but even if the package rt3090 is succesfully installed it do not  work why?

---

### Post by mic2damgood on 2009-12-19
i followed it too, i can do alot more than i could before i can see other wireless networks including mine and when i try to connect (WEP key)  to it. its keeps asking for the password over and over. i know i input the password correctly. but i don't believe its working.

---

### Post by mic2damgood on 2009-12-19
I got it now!!!! It works just made some adjustment on my network. I'm writing this message from wireless. Thanks u soo much

---

### Post by omniuni on 2009-12-19
Please delete your current wireless network in your network manager, and re-create it, and let me know if that solves your problem.

---

### Post by Odemia on 2009-12-21
FYI, recently had to connect to WPA2 personal network, Markus' seems to have fixed the WPA issues in the PPA.  Using Kubuntu 9.10, Markus' PPA and networkmanager I was able to connect without any issues.

---

### Post by omniuni on 2009-12-21
Yes indeed! I know it's been said before, but lots of thanks to Markus! Their PPA works perfectly now, and it can be considered "100% safe" to upgrade to and use Ubuntu Karmic!

---

### Post by imsael on 2009-12-28
The WPA works fine here too!!! THANKS SOO MUCH!

Daniel

---

### Post by anthonydv07 on 2010-01-25
OMG THANK YOU>>> :KS

:D:popcorn::D:popcorn::KS:popcorn::popcorn:

---

### Post by Alex113 on 2010-03-04
Hi! Can you help me? I have the same problem as **mic2damgood** 	 		. It asks the password over and over. How can I solve it?
Sorry for my bad english((

---

### Post by tim1980 on 2010-03-09
anyone got a deb driver for rt3090 that works in lucid lynx?

---

### Post by demster on 2010-03-26
I put Lucid Lync on my Wind12 U230 (quite similar to U210, but better specs) and when I was looking for the Wifi card (after typing in some code, lspci + something) it said I had Ralink rt3090. I used the method descibed in the previous page and filled in lucid in sources.list. 

When I type: sudo apt-get install rt3090-dkms

It gives:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rt3090

Is it not compatible with Lucid Lynx (yet) or is it another problem?
I hope someone can help me with this :)

---

### Post by omniuni on 2010-03-26
The driver works fine, but you have to download it manually.

To get rt3090 in Lucid Lynx:

1. Go to [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/~markus-tisoft/+archive/rt3090") and locate the link for "View Package Details"

2. Click the link, and expand the package of rt3090 for Karmic. Download rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb.

3. When it downloads, some packagekit install should pop up automatically when you click on it.

For convenience, you can try downloading the package from this link: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb")

---

### Post by demster on 2010-04-04
> **omniuni said:**
> The driver works fine, but you have to download it manually.

To get rt3090 in Lucid Lynx:

1. Go to [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") and locate the link for "View Package Details"

2. Click the link, and expand the package of rt3090 for Karmic. Download rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb.

3. When it downloads, some packagekit install should pop up automatically when you click on it.

For convenience, you can try downloading the package from this link: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

I did what you said and it seems like it almost worked... After I pressed the Install button, it needed to download three more packages, but it failed to download the last one: 

"Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-0ubuntu1_all.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-0ubuntu1_all.deb) 404  Not Found [IP: 213.136.29.211 80]" 

Can I get that package manually and how will I install it then?

Kind regards
-

---

### Post by colorlessprism on 2010-04-04
the last time i upgraded i had to change my download server. when you open update manager there should be a settings tab. in the settings there should be a drop down to change your down load server. i had to choose the US one instead of the one that was fastest. PS i love my Wind

---

### Post by demster on 2010-04-04
Ooooooh yeah!!! I got it working now!

I have: 

MSI Wind12 U230-017NL (dutch version)
Upgraded from 2GB to 4GB
Dual boot: 
-Ubuntu 10.04 LTS Lucid Lynx x64 beta
-Windows 7 Ultimate x64 (not standard)

1. I went here: [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")
2. I clicked "View package details"
3. I downloaded the version for Karmic

When installing this package it said: 
"Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/...buntu1_all.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-0ubuntu1_all.deb")  404  Not Found [IP: 213.136.29.211 80]"

4. I got this package from [http://linux.dell.com/dkms/permalink/](http://linux.dell.com/dkms/permalink/) and found the right deb ([http://linux.dell.com/dkms/permalink/dkms_2.1.1.2-0ubuntu1_all.deb](http://linux.dell.com/dkms/permalink/dkms_2.1.1.2-0ubuntu1_all.deb))
5. I installed this deb
6. I installed the Ralink 3090 driver
7. Reboot and it worked (still don't know how to switch it off though :P)

I hope it works for the rest of you!

Ps. one odd thing though (at least for me): on Windows 7 the touch-pad doesn't support scrolling, but on Ubuntu 10.04 beta it is supported (both vertical and horizontal scrolling!)

**Edit:**
After step 3 I stated:

When installing this package it said: 
"Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/...buntu1_all.deb]("http://nl.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-0ubuntu1_all.deb")   404  Not Found [IP: 213.136.29.211 80]"

This is probably due to the offlineness of the Dutch archive or so. It would probably also have worked if I had changed the Software Sources into "Download from: Sever for United States" (worked for another program).

So after step 3 I could probably just have installed the deb after changing the software sources :P

---

### Post by uaaquarius on 2010-04-19
> **omniuni said:**
> The driver works fine, but you have to download it manually.

To get rt3090 in Lucid Lynx:

1. Go to [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") and locate the link for "View Package Details"

2. Click the link, and expand the package of rt3090 for Karmic. Download rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb.

3. When it downloads, some packagekit install should pop up automatically when you click on it.

For convenience, you can try downloading the package from this link: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

Hi,

I've used your steps to install the driver on my x64 Lucid Lynx. And it works!

Thank you :)

---

### Post by mazziek on 2010-04-29
> **demster said:**
> 
Ps. one odd thing though (at least for me): on Windows 7 the touch-pad doesn't support scrolling, but on Ubuntu 10.04 beta it is supported (both vertical and horizontal scrolling!)



At Win7 You have to download manualy driver from synaptics from this site for ex.: [http://www.synaptics.com/support/drivers](http://www.synaptics.com/support/drivers) & install, after few conf. it should works.

I read in some reviews that touchpad in wind (in my case it's u210) is very similar to touchpad by synaptics, but msi offically wont say that this is true, neither support this driver.

---

### Post by irisblackwater on 2010-05-07
> **omniuni said:**
> The driver works fine, but you have to download it manually.

To get rt3090 in Lucid Lynx:

1. Go to [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090") and locate the link for "View Package Details"

2. Click the link, and expand the package of rt3090 for Karmic. Download rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb.

3. When it downloads, some packagekit install should pop up automatically when you click on it.

For convenience, you can try downloading the package from this link: [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

I just installed the rt3090 driver for ubuntu lucid on my msi wind l210. Can confirm, it works out of the box, no hassles. Thank you to everyone who contributed to this thread.

---

### Post by malibusurfer2 on 2010-05-16
Thanks omniuni!

Additional tips running Ubuntu Netbook Edition 10.04:

1. view package details is on right side of screen.
2. click on triangle on left side of Karmic package to open more info.
3. download rt3090 dkms.2.31.3....deb file or let gdeb pkg installer do it.
4. it takes many minutes, so be patient until it says finished installing.
5. close open programs.
6. restart netbook.

After reboot, click on antenna wireless icon on task bar and enter your wireless router name to connect to the proper wireless router (not your neighbors) and set your security settings (WEP key #1 for example).

Worked perfectly and very easy to do.

MSI Wind L1350-430us dual boot Windows 7 Starter (yes I know, but might be handy for some oddball things). 160GB HD   1GB RAM  - Does anyone know if this can take 2x2GB of RAM or just 2x1GB?

---

### Post by colorlessprism on 2010-05-16
my MSI Wind U123 only has one slot for RAM. i had to get a single stick of 2GB (only supports up to 2GB). newegg suggested i could use two sticks, but after looking around online i found that was not the case. open your wind up and see if you have two slots or just one like me.

---

### Post by gregorydillon on 2010-05-16
hay, this has gotten me frustrated, not sure if this is the right thread.

I install Ubuntu on an MSI Wind model L1350, but I've got problems.  If a cable is connected during install it seems to do an update, although it takes a loooooong time,  and is connected to the world. That happened twice, and  I thought all was good, made some changes and each time after that it would not resolve a web page, but was getting an IP address from my router.   Wireless was not working at all.   Im looking at this forum to try to solve the problems.   .

---

### Post by uaaquarius on 2010-05-17
There is a problem with 2.6.31-21-generic kernel in Ubuntu 9.10.
Namely, the wi-fi does not work after updating kernel to 2.6.31-21-generic :(
It worked fine with 2.6.31-20-generic.
I've noticed following message in /var/log/kern.log:
```
rt3090sta: disagrees about version of symbol module_layout
```Any ideas?

---

### Post by HughR on 2010-05-31
> **uaaquarius said:**
> There is a problem with 2.6.31-21-generic kernel in Ubuntu 9.10.
Namely, the wi-fi does not work after updating kernel to 2.6.31-21-generic :(
It worked fine with 2.6.31-20-generic.
I've noticed following message in /var/log/kern.log:
```
rt3090sta: disagrees about version of symbol module_layout
```Any ideas?

I got to this message by googling for the error.  We hit it on an LG x120 notebook.

Wireless worked before the upgrade due to adding a driver from [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/~markus-tisoft/+archive/rt3090")

I guess that broke when the kernel was upgraded.  I haven't yet tried re-installing that driver to see if that fixes the problem.

---

### Post by uaaquarius on 2010-07-01
Exactly the same problem happened in 10.04 (x64) after updating kernel to 2.6.32-23. It works perfectly if I boot with previous kernel - 2.6.32-22.

---

### Post by ginettob on 2010-07-06
> **uaaquarius said:**
> Exactly the same problem happened in 10.04 (x64) after updating kernel to 2.6.32-23. It works perfectly if I boot with previous kernel - 2.6.32-22.

Try to remove package e reinstall.

sudo apt-get remove rt3090-dkms
sudo apt-get update
sudo apt-get install rt3090-dkms

Sound like windows ... :-( but it works.

Of course you must have markus-tisoft on your repository file ([http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic (works on 10.04 too)

---

### Post by uaaquarius on 2010-07-06
> **ginettob said:**
> Try to remove package e reinstall.

sudo apt-get remove rt3090-dkms
sudo apt-get update
sudo apt-get install rt3090-dkms

Sound like windows ... :-( but it works.

Of course you must have markus-tisoft on your repository file ([http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic (works on 10.04 too)

 Thanks, ginettob, it works :)

---

### Post by Nerdfest on 2010-07-06
I've tried removing the package and the update, but then need to re-install via the deb, as I'm running 64bit and the ppa does not seem to work. The suggested solution does not work in this case though. Any suggestions?

---

### Post by uaaquarius on 2010-07-07
> **Nerdfest said:**
> I've tried removing the package and the update, but then need to re-install via the deb, as I'm running 64bit and the ppa does not seem to work. The suggested solution does not work in this case though. Any suggestions?

Nerdfest, it worked for me. And I rum 10.04 x64-bit.
What I did:

[LIST=1]
[*]```
sudo apt-get remove rt3090-dkms
```
[*]Added following to software sources
**deb  [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu)  karmic main**
[*]```
sudo apt-get update
```
[*]```
sudo apt-get install rt3090-dkms
```
[*]Reboot
[/LIST]

---

### Post by Nerdfest on 2010-07-10
Sorry, I had a type in the ppa name. I did get the remove/install going, but still no joy. The hardware doesn't come up correctly, showing "Hardware not ready" in NetworkManager, and a message in dmesg like "NICLoadFirmware failed, Status[=0x00000001]". I also seem to have problems now in the previous version of the kernel as well, but I think those are specific to WP2. I'll do a restart and check.

---

### Post by Nerdfest on 2010-07-10
Yeah, it seems broken (authentication at least) in the previous version of the kernel after this as well. I see "clocksource unstable" in dmesg. The other things that is strange is that the working installs of RT3090 I had set up the interface ra0, and the ppa sets up wlan0. Don't know if it's relevant.

---

### Post by uaaquarius on 2010-07-10
> **Nerdfest said:**
> Yeah, it seems broken (authentication at least) in the previous version of the kernel after this as well. I see "clocksource unstable" in dmesg. The other things that is strange is that the working installs of RT3090 I had set up the interface ra0, and the ppa sets up wlan0. Don't know if it's relevant.

Hi Nerdfest,
Which version of Ubuntu are you running?
I'm running 10.04 and rt3090 interface is still ra0, not wlan0 as you describe...

---

### Post by Nerdfest on 2010-07-10
> **uaaquarius said:**
> Hi Nerdfest,
Which version of Ubuntu are you running?
I'm running 10.04 and rt3090 interface is still ra0, not wlan0 as you describe...
Running 10.04. Originally it was the change from 2.6.32.22 to 2.6.32.23 kernel change that started the trouble. I eventually returned to the -22 kernel which was working fine, and with the ra0 interface as well. After giving it another try last night, I realized I'd made a typo in the ppa name, but it still didn't fix the problem. It did seem to change the interface from ra0 to wlan0 though. I'm going to try to un-install, re-install again from -22 and see if it fixes it. The only part in -22 that seems broken in the WPA authetication.

---

### Post by Nerdfest on 2010-07-10
After a power-off last night, it came up under -22 as ra0 this morning, and does connect to my networks with WPA. The strange part is that I did a power down last night as well, but I was tired and may have booted under the wrong kernel. It still comes up as wlan0 under the -23 kernel though and will not connect. It actually doesn't seem to like connecting under -22 after a restart either so I'm wondering if the hardware gets into some improperly initialized state. A power-off seems to correct it and it will then connect under -22. 

I hate falling behind on kernel updates, but I don't want to replace the wireless card for a while if I can avoid it (I'm assuming it's a removable card).

---

### Post by uaaquarius on 2010-07-10
I installed the driver under -23 kernel. And it does connect via WPA.

---

### Post by Nerdfest on 2010-07-10
> **uaaquarius said:**
> I installed the driver under -23 kernel. And it does connect via WPA.
I'm actually using WPA2/AES, but I don't think it would make any difference. Any idea what I should look for? Perhaps some reason that the interface comes up has wlan0 is related to the source of the problem?

---

### Post by irisblackwater on 2010-07-13
> **ginettob said:**
> Try to remove package e reinstall.

sudo apt-get remove rt3090-dkms
sudo apt-get update
sudo apt-get install rt3090-dkms

Sound like windows ... :-( but it works.

Of course you must have markus-tisoft on your repository file ([http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic (works on 10.04 too)

Yeah! it works for me. I run ubuntu lucid w/ linux kernel 2.6.32-23-generic on an i686 architecture. Kernel upgrade somehow breaks the wireless driver, but the above steps resolve it.

---

### Post by Nerdfest on 2010-07-25
After trying all the variations of the steps outlines here, I finally got my wireless working, with the -23 and the new -24 kernel updates. It did take compiling manually from the Ralink source on their site (the 2.3.1.4 version). I'll try it again later with the latest 2.3.1.6 version.

---

### Post by LPCapital on 2010-09-09
Super noob here. I installed Ubuntu 10.04 3 days ago and followed the instruction here [http://www.linlap.com/wiki/msi+wind12+u210](http://www.linlap.com/wiki/msi+wind12+u210) on how to set the WiFi card to work. I regularly connect to 3 WiFi: my work (Open), my Nexus One (WPA2-PSK), and my home (WPA2-PSK [AES]).

Everything worked fine till the kernel got update from -21 to -24. Since I could not register to my home network. I could if using the -21, but could not uding the -24

I tried uninstalling and reinstalling the driver as recommended by **ginettob**, but it didn't work.

To fix the issue I had to change the Ubuntu version in *sources.list* from *lucid* to *karmic*: thanks to **ginettob** for the note in his post!!!! Now the WiFi connects to my home network in both kernels...

Bottom line: even if you're running 10.04 I would recommend using the karmic version of the drivers...

Cheers to the community, which now I feel I belong to a bit more... ):P):P):P;);)

---

### Post by Nerdfest on 2010-09-10
Building the driver from the  2.3.1.6 source works nicely as well. Just download it from RALink and follow the instructions.

---

### Post by Nerdfest on 2010-10-03
After the latest kernel patch my wireless broke again. Rebuilding the drivers from source once again corrected the problem but I'm making a note here as to get it to work this time I needed to manually copy the rt3090sta.ko file from the build directory to the /lib/modules/2.6.32-25-generic/updates/dkms directory to make the change permanent. If you're testing the fix and having trouble removing the old driver, disabling networking through NetworkManager and removing the old module with 'rmmod -fv rt2860sta' works nicely.

---

### Post by uaaquarius on 2010-10-05
> **Nerdfest said:**
> After the latest kernel patch my wireless broke again. Rebuilding the drivers from source once again corrected the problem but I'm making a note here as to get it to work this time I needed to manually copy the rt3090sta.ko file from the build directory to the /lib/modules/2.6.32-25-generic/updates/dkms directory to make the change permanent. If you're testing the fix and having trouble removing the old driver, disabling networking through NetworkManager and removing the old module with 'rmmod -fv rt2860sta' works nicely.

Latest kernel patch broke rt3090 driver also for me. As usually I've removed and installed the Markus package again. And the driver works again. As usually :)

---

### Post by Nerdfest on 2010-10-05
> **uaaquarius said:**
> Latest kernel patch broke rt3090 driver also for me. As usually I've removed and installed the Markus package again. And the driver works again. As usually :)
I'm going to try that again next time it breaks ... maybe something has changed. Never even thought of it this time.

---

### Post by hamstermoon on 2010-10-10
Anyone tried Meerkat and seen what it does to the MSI Wind? Does the patch from Markus fix it or are we going to have to wait until he produces a new one (eek!)??

---

### Post by Nerdfest on 2010-10-10
I'm actually just playing with the live boot, and no luck so far. I'm playing with the build from RaLink source though ... I'll try Markus's deb file if I can't get this to work, although I seem to be one of the few that his ppa does not work for.

---

### Post by omniuni on 2010-10-10
I can't guarantee anything, but last time I was playing with Meerkat kernels his .deb was still working fine. I will try a beta soon and have more details then.

---

### Post by Nerdfest on 2010-10-10
No luck with the Markus ppa, the .deb, or building the driver from the RaLink source. Sad potential Maverick user :(

---

### Post by LPCapital on 2010-10-11
I've got it to work again. No more need for Markus driver apparently, which caused an error at startup.

I had to add a few lines in the blacklist.conf file.

In terminal:

[PHP]sudo gedit /etc/modprobe.d/blacklist.conf[/PHP]

At the end add:

[PHP]
#Balcklist RaLink drivers
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib[/PHP]

This solved it for me...

Here's the main link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651778](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/651778)

I haven't noticed instability, but under "Connection Information" the driver shown is rt2860... I'm not sure it makes any difference.

---

### Post by Nerdfest on 2010-10-11
Thanks, I'll try it out next time I boot up Maverick.

---

### Post by omniuni on 2010-10-15
I just upgraded to Maverick, and my Wifi is working just fine. I don't know if it is still using the "markus" driver, but whether it is using that, or an included driver, this wireless card definitely works fine with 10.10.

---

### Post by omniuni on 2010-10-22
OK! I've been running Maverick for a bit now, and I've put together a post with a bunch of useful information for those considering the upgrade.

[http://ubuntuforums.org/showthread.php?p=10012136#post10012136]("http://ubuntuforums.org/showthread.php?p=10012136#post10012136")

Surprisingly, the major problem was the graphics card, not the wireless.

Extra thanks to LPCapital whose suggestion helps get the wireless working on 64 bit.

---

### Post by jur9en on 2010-10-25
For Eee PC (1001HA) and Ubuntu Maverick 10.10, with problems with the wireless card the solution of the Markus-tisoft DKMS worked for me as well.
25-Oct-10. 
I used Markus-tisoft latest build (2010-08-27)                                  for Lucid

It solved also the issue of computer frooze while shutting down or turning of the wireless manually.

See same thread for details;
[http://ubuntuforums.org/showthread.php?p=10012136#post10012136](http://ubuntuforums.org/showthread.php?p=10012136#post10012136)

---

### Post by Nerdfest on 2010-10-31
My U210, booted from a fresh install of Maverick (64 bit), will not connect. It does see wireless adapter, but will not seem to connect. Too bad, as I generally update to the latest release right away and have never run into problems. Maybe I'll break down and try 32 bit.

---

### Post by omniuni on 2010-10-31
Hi Nerdfest,

If you check the thread I put up about this netbook on Maverick, [http://ubuntuforums.org/showthread.php?p=10012136#post10012136]("http://ubuntuforums.org/showthread.php?p=10012136#post10012136"), you'll see wifi is not a problem, but the graphics card is.

Check the thread, and you should be able to make a better decision as to whether you want to upgrade or not.

---

### Post by Nerdfest on 2010-10-31
Thanks Omniumi, I followed the guide (very nicely done, btw). No problems with the graphics (above what I'd already resolved in 10.04) but the wifi just does not seem to work. (I did not actually try a second monitor in 10.10, but I assume disabling modesetting will resolve any issues.) I'll have another bash at it at some point, and if that doesn't work I'll try 32 bit. If that doesn't work i may just spend the $20 an pick up a better PCIe wireless card ... my U210 even has a free slot.

---

### Post by omniuni on 2010-11-01
That's interesting. What is the output of

sudo dpkg-reconfigure rt3090-dkms

?

---

### Post by Nerdfest on 2010-11-01
The output is clean (sorry, at work now on a non-connected machine). I berified that the wireless does work, it just does not want to connect to WPA2. I noticed as well that the module listed is rt2860sta. When I build the drivers myself under 10.04 it is actually listed as rt3090sta. This is not necessarily a problem, just more info. Could there be an unrelated wpa_supplicant problem?

---

### Post by omniuni on 2010-11-01
That is odd. I have no trouble on either of my computers on Maverick (32 and 64 bit) on WPA/WPA2 networks, so I'm going to guess that yes, it must be an unrelated issue.

Just a last bit of advice, make sure that the blacklist is working right.

Good Luck! Let us know what you figure out.

---

### Post by Nerdfest on 2010-12-21
Not sure if it's related to recent kernel changes or something else, but I now have it working. I think the difference may be that I also added a blacklist entry to er2860sta to the list of blacklisted modules.

---

### Post by toph on 2010-12-22
I've found that in 10.10, the wifi issue seems to have been fixed and works out of the box now.

---

### Post by uaaquarius on 2010-12-22
> **toph said:**
> I've found that in 10.10, the wifi issue seems to have been fixed and works out of the box now.
It was broken in 10.10 (amd64) for me.

---

### Post by Nerdfest on 2010-12-22
Me as well (amd64 too), but the Markus-tisoft ppa deb fixed it for me. I'll try doing a manual build of the last version of the driver from RaLink I have. There don't seem to be any versions of the software on the RalinkTech site any more ... I get a 404 for the 3090 file. Good thing I kept a couple of old versions.

---

### Post by toph on 2010-12-23
If the Markus Heberling ppa doesn't solve the problem after installing it, you may want to try this. It worked for me in the past.

[http://ubuntuforums.org/showthread.php?p=9554856#post9554856](http://ubuntuforums.org/showthread.php?p=9554856#post9554856)

---

### Post by Nerdfest on 2010-12-31
OK, after it seems to have stopped working again, but a manual rebuild from the driver source once again fixes the problem. Now I appear to have no audio hardware though ... any ideas how to fix this problem?

---

### Post by Nerdfest on 2011-03-19
The latest kernel update (2.6.35-28) seemed to break the Tisoft 3090-dkms workaround. I couldn't seem to get it to work again (64 bit, as before), but after reading up on a few LaunchPad bugs that have been fixed, I blacklisted the 3090, renamed all the rt3090sta.ko files, and un-blacklisted the rt2800pci module. It seems to work fine now with the default 2800 driver. It does seem to be a bit slower connecting, but it does connect.

---

### Post by omniuni on 2011-03-20
Yes, I can confirm that although the rt3090 module won't build any more, it works just fine with the rt2860 driver packaged with Ubuntu. I've been monitoring the progress on Natty, and it looks like it will work out-of-the-box and 100%. (The graphics are fixed too, based on the xorg-edgers repo, and dri2, and modesetting both work, plus AMD has gotten the blur shader working for extra eye candy with KDE 4.6)

---

### Post by Nerdfest on 2011-03-22
I seem to have a problem now with suspend. As mentioned, I only un-blacklisted the 2800pci entry, not all of them, so tis problem may be related to that. Basically, on suspend, I get a blank screen and a hot CPU ... haven't gone in to debug it yet. I'm going to try un-blacklisting all of the entries and see if the 2860 driver solves the problem.


Does anyone know if the graphics fixes have been back-ported? I've got modesetting disabled so I can use an external monitor, but it causes problems in gnome-desktop. It would be nice to have everything work correctly. I never did get the external monitor working perfectly, even with all of the tips. I get one side of the external screen all scrambled graphics. I tried allocating more space in the Xorg.conf, but was never able to make it go away.

---

### Post by Nerdfest on 2011-03-22
So, leaving the 2860 entry blacklisted, but un-blacklisting all the 2800 and 28xx entries solves the problem ... now suspending successfully.

---

### Post by omniuni on 2011-03-23
> **Nerdfest said:**
> So, leaving the 2860 entry blacklisted, but un-blacklisting all the 2800 and 28xx entries solves the problem ... now suspending successfully.

Good to know that solves the problem. I had briefly tried the Xorg-edgers repository, where the graphics are fixed, but due to it being an unstable repository, it went almost daily from working-and-great to broken-and-useless. For now, I have just been sticking with desktop effects turned off, and it's reliable if nothing else. I can't wait, though, to upgrade and turn on desktop effects again! I also wish I had waited just another few months and gotten the version of the U210 with the RadeonHD graphics instead. :-(

---

### Post by Nerdfest on 2011-03-23
Sorry, got ahead of myself. It does suspend, but it locked up after sitting for a while today. It may have been from a suspend, but it does seem to suspend manually without problem.

I did actually manage to compile the 3090 driver from source myself and it does still seen to work properly, but I was excited to have the 2800 working. Sounds like it's only close at this point.

---

### Post by omniuni on 2011-03-24
If it helps, the only one I have un-blacklisted is "rt2860sta" and I have no problems, except for my computer occasionally disconnecting when not in use for a while, but I think that's more the router than the driver.

```
#Balcklist RaLink drivers
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
#removed following
#blacklist rt2860sta

```

---

### Post by omniuni on 2011-03-24
> **Nerdfest said:**
> Does anyone know if the graphics fixes have been back-ported?

I upgraded to Alpha 3 earlier. Mind you, I'm using KUbuntu, and KDE is already pretty stable, so I make no guarantees when it comes to Ubuntu... but...

Graphics look great! Performance is good, even KWin's directly accelerated Gaussian blur works like a charm.
GLXgears+wobbly Windows+panel with Gaussian Blur = about half CPU usage. (Yes, this is with modesetting/dri2)

Good. Job. Ubuntu. :D

---

