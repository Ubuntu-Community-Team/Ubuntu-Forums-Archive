---
title: "Acer Aspire 8920G"
date: 2008-07-07
forum: Hardware
---

### Post by RussianMan on 2008-07-07
I want to buy a laptop Acer Aspire 8920G
This laptop has a touch panel to manage player, audio system 5.1 and few additional buttons.
I want to know how well this laptop is compatible with Ubuntu 8.04?

Read about it here: [http://www.laptopmag.com/review/laptops/acer-aspire-8920.aspx](http://www.laptopmag.com/review/laptops/acer-aspire-8920.aspx) and [http://review.zdnet.com/laptops/acer-aspire-8920-6048/4505-](http://review.zdnet.com/laptops/acer-aspire-8920-6048/4505-) 3121_16-33024473.html? Tag = ut

Who something already put Ubuntu on this laptop?

---

### Post by rami_say on 2008-07-09
> **RussianMan said:**
> I want to buy a laptop Acer Aspire 8920G
This laptop has a touch panel to manage player, audio system 5.1 and few additional buttons.
I want to know how well this laptop is compatible with Ubuntu 8.04?

Read about it here: [http://www.laptopmag.com/review/laptops/acer-aspire-8920.aspx](http://www.laptopmag.com/review/laptops/acer-aspire-8920.aspx) and [http://review.zdnet.com/laptops/acer-aspire-8920-6048/4505-](http://review.zdnet.com/laptops/acer-aspire-8920-6048/4505-) 3121_16-33024473.html? Tag = ut

Who something already put Ubuntu on this laptop?
i got the aspire 8920, installed ubuntu, graphic card is supported but i couldn't get the sound to work, also the nic is not working, and i didn't try the wireless. if someone fixed the sound please help

---

### Post by glethro on 2008-07-10
i just got the same laptop.. having problems as well 

no sound at all even System beeps
on two resolutions 800x600 and 640x4xx
nd the refresh rate is wrong
media  +  quick launch buttons dont work.. (media i think u might have to write some code for it)

any help would be really appreciated


--EDIT--
Quick launch buttons now working

---

### Post by AJB2K3 on 2008-07-10
Has anyone tryed the i950 graphics driver yet?
May work.
Also see if the acerhk module is installed and working.

---

### Post by Occas on 2008-07-14
I installed 32bit 8.04.1 using wubi in Vista on my new 8920G

No sound but installing the restricted nvidia driver gave me 1920x1080 res so that's one problem I'm glad not to have. Did you try that glethro?

Wireless works flawlessly too...

---

### Post by RussianMan on 2008-07-15
> **Occas said:**
> Wireless works flawlessly too...

Audio and sensory panel working properly?

---

### Post by Occas on 2008-07-15
No, unfortunately. No audio and sensor pad as of yet...

---

### Post by glethro on 2008-07-18
thanks Occas works perfectly except the refresh rate is off.. its at 50 bt on vista its 60-61 :P

has any1 found a solution 2 the sound problem?



--edit-- 
the other thing when i restarted i ended up with 4 ubuntu entries in Grub (on start up) usually theres only 2 ubuntu and the recovery console..

---

### Post by vjkeito on 2008-07-21
> **glethro said:**
> the other thing when i restarted i ended up with 4 ubuntu entries in Grub (on start up) usually theres only 2 ubuntu and the recovery console..

this is because a new kernel version has been installed.  handy to leave the entry in the grub boot list till you've restarted and tested that the new kernel works and nothing is wrong.  you can then safely remove its entry in the grub list if you feel the need, or remove the old kernel entirely using synaptic.

for those who are feeling adventurous the file to edit is /boot/grub/menu.lst though if you don't know what you're doing with it then you can get into trouble fast.  always create backups of important system files before tinkering with them! There's a brief guide on editing [here]("http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/")

apparently just removing the old kernel version using synaptic will remove the entry in the grub boot list anyway, though I haven't tried it myself.

hope that clarifies things a little for you 80)

I am interested in purchasing one of these laptops but will be running ubuntu on it and want to make sure everything is compatible before purchasing.  If someone gets it all going OK I'd be very interested to hear about it

regards
k3ito

---

### Post by jansaell on 2008-07-29
I have had the same problem with sounds on my ACER Aspire 8920, and found 2 ways of solving this. I have them listed on my blog at [http://jan.saell.org/blog/archives/30]("http://jan.saell.org/blog/archives/30").
In short:
Way 1 - remove ALSA and install OSS4 - this works and gives sounds but i had problems with mics on that but playback was ok.

Way 2
[LIST=1]
[*]Upgrade to ALSA 1.0.17 - not totally sure that that's fully required
[*]Set model to acer-aspire in /etc/modprobe.d/alsa-base
[*]Download and compile hda-verb from [here]("ftp://ftp.suse.com/pub/people/tiwai/misc/hda-verb-0.2.tar.bz2")
[*]Copy the compiled program to /usr/local/bin
[*]Run the command (prefably from /etc/rc.local so it will happend every bootup): /usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
And you have to run that as root
[/LIST]
That should give you sound working.

---

### Post by Occas on 2008-07-30
Hey mate!

Thanks heaps for your post, I look forward to having sound!
Now with that, I'm almost a total linux noob so when you say, compile this and copy this and change this I get quite lost.

I guess what I'm used to doing is following the step by step processes that people patiently type out for people like me (like "open console and type xyz, then type this) but the down side of this is that I'm not really learning how to figure stuff out for myself.

So I'll leave it up to you, if you have the patience I would appreciate a bit more detail in exactly how to do some of those steps, but if you want, just tell me to stop being so lazy and figure it out for myself :):):)

I did start the first option, which uninstalled  ALSA, but one of the other modules it wanted to uninstall with it was "ubuntu-desktop" which made me a bit nervous so I bailed out.

Thanks again!

---

### Post by jansaell on 2008-07-30
Ok. More detail:

As i said i think that the install of alsa 1.0.17 is not totally nessesare so go a heard with the rest and try that.

1. Edit /etc/modprobe.d/alsa-base and set the line with:
options snd-hda-intel model=default
to
options snd-hda-intel model=acer-aspire
If you dont have that line at all add it.
2. download the hda-verb file and save it in your home directiry
3. Open a terminl window
4. Unpack the hda-verb file with **tar jxvf hda-verb-0.2.tar.bz2**
5. go into the hda-verb direcgtory in the termninal window (cd hda-verb)
6. Complile it with the command **make**
7. Copy it to /usr/local/bin with **sudo cp hda-verb /usr/local/bin**
8. Edit /etc/rc.local and add the followind line to the file berfore the exit 0 line:
/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
9. test and reboot the machine
hopefully that will give you sound.

Please tell us how it when or even use my bolgs comments.

Jan

---

### Post by Occas on 2008-07-31
You are a ******* genius!!!!!!!!

What country are you in? If I ever come there I'm buying you a beer!

As as side note, I don't know when this happened, but my touch panels for volume, track skip and start/stop/pause, and the selection jog wheel and enter keys are working flawlessly (at the moment i've only used rhythmbox)
The person and back arrow keys are doing nothing though.

Also in this text box the jog wheel is moving the cursor and the enter key creates a new line, like the regular key. Nice!!!

---

### Post by weirdfox on 2008-08-14
Thanks for the pointer, I have an Aspire 6920 which have the same audio hardware (and same bugs).

It helped a lot, the sound quality is far better than it used to be with OSS due to the fact that alsa use more speakers :)

The only problem left is that the headphone jack is not managed and only some speakers are turned off when I manually change the headphone status...
If I find anything whit this bug I'll share it here.

---

### Post by XavierGr on 2008-08-14
Thank you jansaell, works like a charm!

How the hell did you manage to find such solution, I was disappointed at first but then I read your post and all sound problems solved.

Thanks again.

---

### Post by jansaell on 2008-08-17
Thanks XavierGr.

Yes it was a bit hard to find and i got a pointer in some old fedora post on some forums somewhere - and yes - it did take i guess over 1 full week to get the sound to where I think it should be.

Glad it helped you to.

---

### Post by eTiMaGo on 2008-09-20
6920G owner here and still facing problems :( I love this notebook, loads of features for the money, but some of it too cutting-edge :D

I followed all of Jan's instructions (major thanks for the hard work!), but still nothing.

If i go to test the sound in system->preferences->sound I get this error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

Any ideas?

---

### Post by dream_coder on 2008-10-06
7. Copy it to /usr/local/bin with sudp cp hda-verb /usr/local/bin is this meant to be sudo cp? thanks i tried using alsa but couldnt manage to get it working going to try again! (Got it working thank you so much!)

---

### Post by jansaell on 2008-10-14
Thanks for the info - yes - it should be sudo cp in point 7.

Changed that.

---

### Post by greekleo on 2008-10-15
hey guys, 

I re-installed ubuntu last night and just now i tried to enable the sound, i followed the step-by-step guide the first time and it worked nicelly, i just tried it now and i get an error after i tell it to compile 'make' heres the error.

```

gcc -Wall -O2 -g   -c -o hda-verb.o hda-verb.c
hda-verb.c:10:19: error: stdio.h: No such file or directory
hda-verb.c:11:20: error: stdlib.h: No such file or directory
hda-verb.c:12:20: error: string.h: No such file or directory
hda-verb.c:13:19: error: ctype.h: No such file or directory
hda-verb.c:14:20: error: unistd.h: No such file or directory
hda-verb.c:15:23: error: sys/ioctl.h: No such file or directory
hda-verb.c:16:20: error: sys/io.h: No such file or directory
hda-verb.c:17:23: error: sys/types.h: No such file or directory
hda-verb.c:18:23: error: sys/fcntl.h: No such file or directory
hda-verb.c:20:20: error: stdint.h: No such file or directory
hda-verb.c:21: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u8&#8217;
hda-verb.c:22: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u16&#8217;
hda-verb.c:23: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u32&#8217;
hda-verb.c:24: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u64&#8217;
In file included from hda-verb.c:26:
hda_hwdep.h:33: error: expected specifier-qualifier-list before &#8216;u32&#8217;
hda-verb.c: In function &#8216;list_keys&#8217;:
hda-verb.c:198: warning: implicit declaration of function &#8216;strlen&#8217;
hda-verb.c:198: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
hda-verb.c:200: warning: implicit declaration of function &#8216;fprintf&#8217;
hda-verb.c:200: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:200: error: &#8216;stderr&#8217; undeclared (first use in this function)
hda-verb.c:200: error: (Each undeclared identifier is reported only once
hda-verb.c:200: error: for each function it appears in.)
hda-verb.c:204: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:209: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c: In function &#8216;lookup_str&#8217;:
hda-verb.c:216: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
hda-verb.c:218: error: &#8216;NULL&#8217; undeclared (first use in this function)
hda-verb.c:220: warning: implicit declaration of function &#8216;strncmp&#8217;
hda-verb.c:222: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:222: error: &#8216;stderr&#8217; undeclared (first use in this function)
hda-verb.c:229: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c: In function &#8216;strtoupper&#8217;:
hda-verb.c:239: warning: implicit declaration of function &#8216;toupper&#8217;
hda-verb.c: In function &#8216;main&#8217;:
hda-verb.c:250: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:250: error: &#8216;stderr&#8217; undeclared (first use in this function)
hda-verb.c:257: warning: implicit declaration of function &#8216;open&#8217;
hda-verb.c:257: error: &#8216;O_RDWR&#8217; undeclared (first use in this function)
hda-verb.c:259: warning: implicit declaration of function &#8216;perror&#8217;
hda-verb.c:263: warning: implicit declaration of function &#8216;ioctl&#8217;
hda-verb.c:263: warning: implicit declaration of function &#8216;_IOR&#8217;
hda-verb.c:263: error: expected expression before &#8216;int&#8217;
hda-verb.c:265: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:269: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:274: warning: implicit declaration of function &#8216;strtol&#8217;
hda-verb.c:274: error: &#8216;NULL&#8217; undeclared (first use in this function)
hda-verb.c:276: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:280: warning: implicit declaration of function &#8216;isdigit&#8217;
hda-verb.c:288: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:300: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:304: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
hda-verb.c:307: error: &#8216;struct hda_verb_ioctl&#8217; has no member named &#8216;verb&#8217;
hda-verb.c:308: warning: implicit declaration of function &#8216;_IOWR&#8217;
hda-verb.c:308: error: expected expression before &#8216;struct&#8217;
hda-verb.c:310: warning: implicit declaration of function &#8216;printf&#8217;
hda-verb.c:310: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
hda-verb.c:310: error: &#8216;struct hda_verb_ioctl&#8217; has no member named &#8216;res&#8217;
hda-verb.c:311: warning: implicit declaration of function &#8216;close&#8217;
make: *** [hda-verb.o] Error 1


```
help me please i cant live without sound

Edit: I fixed it by installing [http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.18git20080915-1_all.deb](http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.18git20080915-1_all.deb)

but now on my boot menu its added another kernel, the kernel im using now is Ubuntu 8.04.1, kernel 2.6.24-21-generic, but there is another one there called Ubuntu 8.04.1, kernel 2.6.24-19-generic, i cant remember which one got added but all i know is that it wasnt there before i installed this package.

Thanks

---

### Post by khurtsiya on 2008-10-22
Hello guys,

I have 6920G and here is some good tips to tune some hardware [http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637)

But I still can not configure my video adapter. Max resolution is 800x600.

Any ideas will be appreciated!

TIA

Michael

---

### Post by glethro on 2008-10-22
for the video adapter:
all i had to do was enable the restricted drivers. 
i think u do it by
System> admin>hardware drivers

than enable the restricted nividia drivers

---

### Post by kuzniarpawel on 2008-10-22
Has anyone tried 8.10 on aspire 8920. Any improvements with new kernel? What about webcam? Is it working? I'm going to install Ubuntu on my friends aspire and it's going to be his first Linux, don't want to blow it.

---

### Post by kuzniarpawel on 2008-10-24
solution to sound problem doesn't work in Intrepid

/dev/snd/hwC0 is not created anymore

---

### Post by dream_coder on 2008-10-25
yeah this doesnt work on Intrepid x64 either
Webcam works automatically!

---

### Post by rubo77 on 2008-10-26
i`ve got the Acer aspire 8930G

is it all the same with this one?

---

### Post by glethro on 2008-10-27
im using the 8920 and got everything working except for the cine dash controls... i think theres a step missing from the instructions.. 

but sound works fine now

except
1 problem.. theres no mixer.. at least tht ive found so far.. 
how do i control the system volume and unmute or mute things?


all the other instructions seem to work fine for the 8920g.. :D

---

### Post by iykrichie on 2008-10-27
I had to research brands of laptops before purchasing mine, and i finally got Acer Aspire 5720z after everything thing worked on 8.04 except my wifi and webcam. display, nic, sound and card reading is superb by default.

I am still optimistic that my wifi (atheros wireless 5700EG) would be working soon.


............:guitar:

---

### Post by dream_coder on 2008-10-28
Glethro, What version of Ubuntu are you using? Intrepid? x64? or 32bit? and are you using alsa? or OSS4? Thanks.

How did you get sound working?

Cheers mate

---

### Post by lusephur on 2008-10-30
cheers, i agree with the person who said you are owed a beer, at first i thought it wasn't working, but the touch pad for volume was causing some issues, but it's now sorted, 

thank you very very much :)

btw, this was on a 6920g, running 32bit intrepid i386
everything was working out of the box (well apart from the nvidia) and you stopped me looking elsewhere (as in another distro, thinking ubuntu may have messed up- long history with certain issues which other distros never had)

---

### Post by rmoore2112 on 2008-11-01
Intrepid Ibex Upgrade Notes: Acer 8920 - 64 bit

**Sound:**
For some reason the sound stopped working, after upgrade was complete (missing devices in /dev/snd) causing hda-verb to fail
[B]
Fix:[/B]
Assumptions: your sound was working in Hardy Heron via this fix:

[http://jan.saell.org/blog/archives/30](http://jan.saell.org/blog/archives/30)

Upgrade to ALSA drivers to 1.0.18
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=820959](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=820959)

reboot

**Video: ** stopped working after upgrade (tried re-building NVidia driver but received error - not compatible with Xen kernel)

Fix:

sudo apt-get install nvidia-glx-177
sudo nvidia-xconfig
sudo reboot

Enjoy !!:guitar:

---

### Post by rubo77 on 2008-11-04
> **rubo77 said:**
> i`ve got the Acer aspire 8930G

is it all the same with this one?
i tried your installation instructions but it doesent work :(

i use kubuntu 8.10

---

### Post by rmoore2112 on 2008-11-09
> **rubo77 said:**
> i tried your installation instructions but it doesent work :(

i use kubuntu 8.10

I think the 8920 is different.

---

### Post by Max_Might on 2008-11-12
Does the Acer Tuba booster work with the hda-verb fix?
How can i get it working?

//6920/8.10 64bit

---

### Post by costre on 2008-11-13
I just got the sound working with my 8920 running Intrepid! Absolutely awesome :)

Subwoofer or not it's loud enough, and clear enough, for my taste!

I guess you could mess around with "model" in /etc/modprobe.d/alsa-base, perhaps find something with more speakers or what not?

---

### Post by killom on 2008-11-15
Hi, I have an Acer Aspire 8930, the sound works with hda-verb, but I'm searching a way to make the surround 5.1 to work, any ideas? Can hda-verb help to solve this problem??

---

### Post by khurtsiya on 2008-11-15
> **killom said:**
> Hi, I have an Acer Aspire 8930, the sound works with hda-verb, but I'm searching a way to make the surround 5.1 to work, any ideas? Can hda-verb help to solve this problem??
Hello guys!

Can somebody tell me what is hda-werb and where I can download it?

Sinaptyc search do not show any results. 

I want to try it with Aspire 6920G cuz there are low level sound too (

TIA 

Michael

---

### Post by killom on 2008-11-17
> **khurtsiya said:**
> Hello guys!

Can somebody tell me what is hda-werb and where I can download it?

Sinaptyc search do not show any results. 

I want to try it with Aspire 6920G cuz there are low level sound too (

TIA 

Michael

[Read here]("http://jan.saell.org/blog/archives/30")

---

### Post by CJay554 on 2008-12-12
For the acer 6920 I have posted ways to make certain things work (including the sound) go to:
[http://ubuntuforums.org/showthread.php?t=921637](http://ubuntuforums.org/showthread.php?t=921637)

Theres a list of what works, what doesn't work, and what works with modifications.

Cheers! :popcorn:

---

### Post by jspringer on 2008-12-24
Many thanx:)

6920G: it worked for me with hda-verb 0.3 (0.2 was no longer available) on Ubuntu 8.04.1 2.6.24-22 without upgrade of ALSA (don't know what version i have).

---

### Post by bob2098 on 2009-03-08
Don't know if its just something I did wrong, but with:

options snd-hda-intel model=acer-aspire

Headphone mute didn't work, but I have it working after replacing that line with:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

---

### Post by DarwinSurvivor on 2009-03-12
I am having the same problem, but with a 6930

I finally got the subwooffer working by following the steps at the beginning, but the headphones no longer worked (as if I never plugged them in).
I undid everything, but the headphones were still dead.
I then installed the linuxant driver (mentioned earlier) and now the headphones work as well (but don't turn off the main speakers).
Then I tried what the previous poster did and changed my settings to:
 alias snd-card-0 snd-hda-intel
 options snd-hda-intel model=auto
No subwoofer :(
So I changed auto back to default (leaving the alias there) and now I have AMAZING sound (better than previous /w subwooffer), but alas, the headphones don't turn off the main speakers (though I do get sound out of them).

I feel like I'm so close I can TASTE it, I just need the headphones to turn off the main speakers. I can manually mute "front" (speakers) and "side" (subwoofer) and use the headphones, but that's a pain the butt.

Note: in the mixer, "surround" seems to be the headphones :p

If someone knows of a way to check if something is muted (through software) I could write a script to "fake" the headphone insertion. That would be a nice temporary fix, but I would like to have it automatic when the headphones are inserted.


Thanks for getting my subwooffer working (amazing sound by the way).
Any help with the headphones would be greatly appreciated.

---

### Post by tmetro on 2009-06-09
I reported over in this [thread](http://ubuntuforums.org/showpost.php?p=7429366&postcount=304) that the Alsa rebuild script doesn't seem to work for kernel version 2.6.28-12. I only tried it once, so the results aren't conclusive.

Has anyone looked into whether Ubuntu has a mechanism for incorporating the other tweaks mentioned in this thread into the distribution, so future users of this hardware don't have to track down this thread and apply the changes themselves?

I'm not aware of Ubuntu having machine specific packages, though maybe the best solution is getting the Alsa drivers, which already incorporate hardware detection, to do the right thing and eliminate the need for the external tweaks. Has anyone filed a bug with the Alsa project to get that to happen?

As for the Alsa driver itself, can anyone explain why, if upgrading the version of Alsa shipped with 8.10 (1.0.16 I think) to 1.0.18 via the source build script would fix things, then why don't the 9.04 kernels that come with 1.0.18 work "out of the box?" I was surprised to see that building Alsa from source was still necessary. Are there significant compile time options set differently by the build script compared to the stock Ubuntu build? (I'd like to understand this and supply feedback to the Ubuntu devs so I can eventually migrate back to using the stock builds.)

 -Tom

---

### Post by cppdeveloper on 2010-05-20
I have an Acer 8920G with 2 HDDs and BIOS version 1.15, and it works out of the box with Ubuntu Linux 9.10. So these days, Acer 8920G is OK for Ubuntu Linux.

---

### Post by tmetro on 2010-06-12
> **cppdeveloper said:**
> ...it works out of the box with Ubuntu Linux 9.10.

How about the suspend/hybernate features? Does theg display wake up after restart now?

How about the Euro and $ keys (near the arrows)? Do they still not generates scan code?

As of 9.10 it finally seem no longer necessary to build the ALSA driver to get sound. (Of course my config files still have a few setting tweaks put in place in the 8.10 era, so I can prove a fresh install would work.)

 -Tom

---

