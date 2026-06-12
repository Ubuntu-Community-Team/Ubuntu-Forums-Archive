---
title: "[ivtv] Hauppage pvr-500 won't work"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by Boxed on 2005-09-11
Hi all, 
I've been working for weeks now trying to get my Hauppage pvr-500 card to work. 
Right now i really don't know why the card won't work, according to the dmesg output the ivtv driver succesfully detects 2 wintv pvr-150 cards. When i look for devices in /dev/ i find a video0 and a video1 device, perfect!
But why does tvtime tell me "Cannot open capture device /dev/video0" ?

I have followed these 2 tutorials:
[http://www.cs.rit.edu/~css8044/?q=ivtv](http://www.cs.rit.edu/~css8044/?q=ivtv)
[http://www.abarbaccia.com/content/view/19/31/](http://www.abarbaccia.com/content/view/19/31/)

I have added these 3 lines in my /etc/modprobe.d/aliases :
alias char-major-81 videodev
alias char-major-81-0 ivtv
alias char-major-81-1 ivtv

and added "ivtv" to /etc/modules.


here is the output i get from dmesg:
```
boxed@boxed:~$ dmesg | grep ivtv
ivtv: ==================== START INIT IVTV ====================
ivtv: version 0.3.7 (h) loading
ivtv: Linux version: 2.6.10-5-386 preempt 386 gcc-3.3
ivtv: In case of problems please include the debug info
ivtv: between the START INIT IVTV and END INIT IVTV lines when
ivtv: mailing the ivtv-devel mailinglist.
ivtv: Autodetected WinTV PVR 150 card (iTVC16 based)
ivtv: Unreasonably low latency timer, setting to 64 (was 32)
ivtv: i2c attach to card #0 ok [client=tveeprom[50], addr=50]
tuner: chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
ivtv: i2c attach to card #0 ok [client=(tuner unset), addr=60]
tuner: chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
ivtv: i2c attach to card #0 ok [client=(tuner unset), addr=61]
ivtv: i2c attach to card #0 ok [client=cx25840[50], addr=44]
ivtv: i2c attach to card #0 ok [client=wm8775[50], addr=1b]
ivtv: i2c attach to card #0 ok [client=tda9887, addr=43]
ivtv: Detected a TEA5767 radio tuner. Enabling radio support.
ivtv: Encoder revision: 0x02040011
ivtv: Create DMA encoder MPEG stream: 0 x 32768 buffers (0KB total)
ivtv: Create DMA encoder YUV stream: 0 x 12960 buffers (0KB total)
ivtv: Create DMA encoder VBI stream: 0 x 26208 buffers (0KB total)
ivtv: Create DMA encoder PCM audio stream: 0 x 4608 buffers (0KB total)
ivtv: Create encoder radio stream
tuner: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4)) by ivtv i2c driver #0
ivtv: Initialized WinTV PVR 150, card #0
ivtv: ======================  NEXT CARD  ======================
ivtv: Autodetected WinTV PVR 150 card (iTVC16 based)
ivtv: Unreasonably low latency timer, setting to 64 (was 32)
ivtv: i2c attach to card #1 ok [client=tveeprom[50], addr=50]
tuner: chip found at addr 0xc2 i2c-bus ivtv i2c driver #1
ivtv: i2c attach to card #1 ok [client=(tuner unset), addr=61]
ivtv: i2c attach to card #1 ok [client=cx25840[50], addr=44]
ivtv: i2c attach to card #1 ok [client=wm8775[50], addr=1b]
ivtv: i2c attach to card #1 ok [client=tda9887, addr=43]
ivtv: Encoder revision: 0x02040011
ivtv: Create DMA encoder MPEG stream: 0 x 32768 buffers (0KB total)
ivtv: Create DMA encoder YUV stream: 0 x 12960 buffers (0KB total)
ivtv: Create DMA encoder VBI stream: 0 x 26208 buffers (0KB total)
ivtv: Create DMA encoder PCM audio stream: 0 x 4608 buffers (0KB total)
ivtv: Create encoder radio stream
tuner: type set to 56 (Philips PAL/SECAM multi (FQ1216AME MK4)) by ivtv i2c driver #1
ivtv: Initialized WinTV PVR 150, card #1
ivtv: ====================  END INIT IVTV  ====================
boxed@boxed:~$    
``` 

Could someone give me a hint where to look now?

Cheers, Richard

---

### Post by Boxed on 2005-09-13
Bump!

The must be someone here who can tell why i can't get a tv image...

---

### Post by Boxed on 2005-09-14
Ok, i've got a little bit further.

I have changed the inpuut to tuner0 with the command: ivtvctl -d /dev/video0 -p 6
And changed the permissions to /dev/video0 & /dev/video1 to 666.

I can get a noisy signal by copying /dev/video0 to a video file and running it with vlc.

But still tvtime tells me "Cannot open capture device /dev/video0".
When i run tvtime in the console it tells me:
Running tvtime 0.9.15.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /root/.tvtime/tvtime.xml
videoinput: Card failed to allocate capture buffers: Invalid argument

the command "ivtvctl -d /dev/video1 -I" tells me:
ioctl: VIDEO_STATUS = Bad 
Which looks like a 'bad' thing to me, allthough i don't exactly know what it thinks is bad.

Any hints?

---

### Post by Boxed on 2005-09-15
Well, nobody is replying but since i've got a bit further i might as well write it here so someone else can solve this problem.

The tv-card gives me a tv image now, only not in tvtime or xawtv. The reason being tvtime and xawtv are software for normal tv cards and the hauppage 150 or 500 are mpeg2 encoding cards. So when you want to see a tv image i'll need to use a sort of mediaplayer or tv software that can decode a mpeg2 stream.

So i get get the video now, offcourse audio doesn't work just yet.

Stay tuned for the latest updates!

---

### Post by Bekker on 2005-09-17
Aaah, I'm busy trying to get my pvr-150 to work. I've just reached the same point, and now I'm also stuck. 
So I can't help you, but I thought it would be nice for you to know you're not alone. Once I find a sollution I'll post it here off course, I'll also check regularly here to see wheather you made some progress  ;-)

---

### Post by Boxed on 2005-09-18
Nice, to know there're more people having problems with ivtv.
So you can get a image but without sound?

---

### Post by Bekker on 2005-09-18
Hi,
I've still got some problems with my image. Somehow I'm not capable of finding a channel, the only thing I get is snow. So are you getting any "real" television? How are you setting the frequency? I've tried "ivtvctl -r <freq>" (frequency in MHz) and it says it changes frequency but there's nothing but snow where there's supposed to be a channel.
Have you considerd using Mythtv? I'm not sure about using it myself because I first want to solve this problem, but it looks like a good program.

Cheers

---

### Post by Boxed on 2005-09-18
The ivtv developers included a little tool you can use if you want to change the channel. It's called ptune-ui.pl and it's located in the "utils" directory or if you did a "make install" it should be in your path. 

If you use xine for video playback use the command:
"ptune-ui.pl -d /dev/vdeo0 & cat /dev/video0 | xine stdin://mpeg2 &"

to start ptune-ui and view the video stream, or u can use mplayer:
"ptune-ui.pl -d /dev/vdeo0 & cat /dev/video0 | mplayer -vo xv - &"

Using this command line i can get a clear video image, still without sound though.

---

### Post by Bekker on 2005-09-18
Thanks! I'm still having some trouble with this, but your help got me a little further. First of all the module/driver is still giving some trouble, probarly because I'm using a VIA KT600 motherboard. Secondly ptune-ui.pl gives some trouble with the channels I choose, but I think I can work this out soon. 

I've conducted a little experiment to try and hear sound. I've hooked a analog camera up to my cards composit connection, and then tuned in to composit 0. I didn't really expect to hear something because of your story, but it worked! This offcourse doesn't mean that it will also work for the tuner...

I'll be tinkering a little more tomorrow.

---

### Post by BrainEmindless on 2005-09-18
I am new to linux and would appreciate suggestions when installing my PVR-350. I have a few years of experience with windows and no experience with unix or linux.

---

### Post by Boxed on 2005-09-19
Hi BrainEmindless, i should look up a tutorial that shows how to install the pvr-350. In the top post there are 2 links to tutorials covering a pvr-150/500 install but since the pvr-350 is a bit different the installation procedure will also be a bit different.

---

### Post by Bekker on 2005-09-19
Hi Brain, welcome to the Linux world! Boxed is right about your card being totally different. but I think you can also use ivtv. 
The main page is here: [http://ivtv.writeme.ch/tiki-index.php](http://ivtv.writeme.ch/tiki-index.php)

With this: [http://ivtv.writeme.ch/tiki-index.php?page=IvyTvHowTo](http://ivtv.writeme.ch/tiki-index.php?page=IvyTvHowTo)
and this: [http://ivtv.writeme.ch/tiki-index.php?page=KubuntuHowTo](http://ivtv.writeme.ch/tiki-index.php?page=KubuntuHowTo)
combined you'll hopefully be capable of installing it. I believe to have understood that you can normally use tvtime with the pvr-350, use: "sudo apt-get install tvtime" to install it.

Good luck.

---

### Post by n1x0r on 2005-09-30
it seems we are all in the same boat. When ordered my Hauppauge PVR150mce i dug around a good deal for recc h/w for this type of thing.
I'm a little suprised by the degree of difficulty i've encountered, especially as compared to people who've chosen different h/w. 
the revelation that this is strickly a tv-mpeg card was very enlightening, but I'm not quite there yet. BTW Boxed, kudos for your stick-to-it-ness!!
I've not been able to stream video from the /dev/video0 device. Also, where is the ptune-ui script... I think i must have missed out on that one somehow.
thx!!!!

---

### Post by Boxed on 2005-10-01
Hi n1x0r, ptune is supplied in the ivtv package in the utils dir. When you follow the tutorials you should run into this dir, you have to compile and install these utils as root. Then you should be able to tune the card to a channel.
I know it's not gonna help you guys, but my card suddenly began giving me sound and i didn't do anything to it for a week :confused: ...... very weird all this.

---

### Post by n1x0r on 2005-10-02
Hi Boxed,
Thanks for responding. I've found ptune.pl and ptune-ui.pl just where you said. I thought it sounded familiar :-)
Only problem is they don't work when i try to run them. I've followed through the steps of several tutorials (this one being the best!!) and am able to produce scrabbly-jarble output in mpeg format... w00t!
I feel that the ability to tune is the final step I need to make my PVR150mce usable... unfortuneately both ptune.pl and ptune-ui.pl are currently useless to me.
Would you mind taking a look at this output? I'm afraid it doesn't mean much to me...
Thanks!!
my perl version
```
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# perl -v | head -2
This is perl, v5.8.4 built for x86_64-linux-thread-multi

```
my errout from ptune.pl
```

root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune.pl
Can't locate Video/Frequencies.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./ptune.pl line 8.
BEGIN failed--compilation aborted at ./ptune.pl line 8.

```
the errout from ptune-ui.pl
```

root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune-ui.pl
Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./ptune-ui.pl line 4.
BEGIN failed--compilation aborted at ./ptune-ui.pl line 4.
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils#            

```
I'm going to try to track this down inside the scripts, though I don't know much (or any) perl :-D 
Any suggestions?
thx!

---

### Post by n1x0r on 2005-10-02
fyi...

the "Can't locate Tk.pm in @INC" error
- resolved: w/ package **perl-tk** avail via apt/universe

the "Can't locate Video/Frequencies.pm in @INC" error 
- I was able to fix this w/ package **libvideo-capture-v4l-perl** available via apt/universe 

However,  when run it now produces this error...
```
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune-ui.pl
Video::Frequencies version 0.03 required--this is only version 0.01 at ./ptune-ui.pl line 9.
BEGIN failed--compilation aborted at ./ptune-ui.pl line 9.

```

I've located the module at CPAN and found that even there it is still version 0.01 ([http://search.cpan.org/~mlehmann/Video-Capture-V4l-0.225/Frequencies.pm](http://search.cpan.org/~mlehmann/Video-Capture-V4l-0.225/Frequencies.pm)) 

Since a newer version doesn't seem to exist, and the info it exports seems fairly static I decided to circumvent the version chech by editing the script itself- (located at /usr/lib/perl5/Video/Frequencies.pm) 
and changed the version string from

"$VERSION = 0.01;"  --> "$VERSION = 0.03;" 

------------------------
Now I'm getting a new error...

check this out...
```
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune.pl
Can't locate Video/ivtv.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at ./ptune.pl line 9.
BEGIN failed--compilation aborted at ./ptune.pl line 9.

```

I can't find this file, or even any info about it anywhere!
I know I am missing something...

Any ideas?

Thx v much for your help!!

---

### Post by n1x0r on 2005-10-02
got it from here:
[http://packages.debian.org/unstable/perl/libvideo-ivtv-perl](http://packages.debian.org/unstable/perl/libvideo-ivtv-perl)
and a quick 
```
root@ganymede:~/downloads/ivtv/deps# dpkg -i libvideo-ivtv-perl_0.13-3_amd64.deb
dpkg: status database area is locked by another process
root@ganymede:~/downloads/ivtv/deps# dpkg -i libvideo-ivtv-perl_0.13-3_amd64.deb
Selecting previously deselected package libvideo-ivtv-perl.
(Reading database ... 145443 files and directories currently installed.)
Unpacking libvideo-ivtv-perl (from libvideo-ivtv-perl_0.13-3_amd64.deb) ...
Setting up libvideo-ivtv-perl (0.13-3) ...
root@ganymede:~/downloads/ivtv/deps# find / | grep -i ivtv.pm
/usr/lib/perl5/Video/ivtv.pm
root@ganymede:~/downloads/ivtv/deps# ../ivtv-0.2.0-rc3k/utils/ptune-ui.pl

```
w00t!! 
so ptune, and ptune-ui work fine now...
Oops!! spoke to soon! 
It seems it fails on channel change, heres an example of the errors..
```
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune.pl -c 14
Ch.14: 121250 1940
Error:  setFrequency(1940) failed!
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune.pl -c 71
Ch.71: 505250 8084
Error:  setFrequency(8084) failed!
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils# ./ptune.pl -c 43
Ch.43: 337250 5396
Error:  setFrequency(5396) failed!
root@ganymede:~/downloads/ivtv/ivtv-0.2.0-rc3k/utils#  
```
any ideas why this may be? I'm wondering if perhaps I do have an outdated Video::Frequencies module. 
Very frustrating yet exciting! I'll check in later fellows, be well all. 
thanks!

---

### Post by fserve on 2005-10-02
i have a playtvpro bt878...

i can see the tv, but not listen anything :/
i see that u have the same problem, any progress?

i use TVTime and 'modprobe bttv card=37 tuner=2 radio=1' ...

---

### Post by Boxed on 2005-10-03
I got my ivtv and frequencies from ivtv at sourceforge. 

Did you install ivtv and libvideo-ivtv-perl from this debain source? I have no idea about the versions of all these packages.

---

### Post by Boxed on 2005-10-03
@ fserve, i think it's a good idea to keep this topic to the PVR-500 and PVR-150 cards. Since there are so many different cards available that i don't know anything about.

I can recommend to try some different versions of the ivtv driver from the stable and unstable branch. There are differences between the versions that can cause sound to work or stop working.

---

### Post by fserve on 2005-10-03
sorry :/

i use the bttv driver, ivtv dont is for my hardware.

by the way thanks.

---

