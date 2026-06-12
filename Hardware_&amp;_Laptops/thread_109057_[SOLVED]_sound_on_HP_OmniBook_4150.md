---
title: "[SOLVED] sound on HP OmniBook 4150"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by bernardfrancois on 2005-12-27
Hi,

I'm trying to make the sound on my HP Omnibook 4150 laptop working.
I found more information on this site: [http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html?page=1)

A quote:
> Using The Kernel Modules (OSS/Free)

Following the advice of other 4150 owners, I first set up the OSS/Free sound modules built from the 2.2.19 kernel sources. I configured the audio system by adding these lines to /etc/modules.conf:

alias sound-slot-0 ad1848
options sound dmabuf=1
alias synth0 opl3
options opl3 io=0x388
options ad1848 io=0x530 irq=5 dma=1 dma2=0

This configuration gave me PCM and CD audio, along with the well-known OPL3 FM synthesizer.

So, what I did is creating a file /etc/modprobe.conf (which is the equivalent for /etc/modules.conf on ubuntu - which I found in 'man modprobe' and 'man modprobe.conf') with the contents from the site.

After rebooting, I noticed that the system beep when executing **echo -e '\a'** doesn't work any more, but no other changes occured (the sound still doesn't work).

To ensure you that I have the same audio controller as discussed in the article:
```
ber@ubuntu:~$ lspci | grep audio
0000:01:00.1 Multimedia audio controller: Neomagic Corporation NM2200 [MagicMedia 256AV Audio] (rev 20)

```

Can anyone help me out how I need to make the sound work? I'm unexperienced at installing hardware which wasn't auto-detected. I think I need to replace the Enlightement Sound Daemon by another one, but I don't know how to do this or how to enable and configure it.

It would be great if someone could help me out to have a little more understaning of configuring sound in linux, and to make the sound on my laptop work.

---

### Post by bernardfrancois on 2005-12-27
Some additional console output:

```

ber@ubuntu:~$ alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device
ber@ubuntu:~$ ls -l /dev/dsp
ls: /dev/dsp: No such file or directory

```

It seems that I can't add the volume controll applet to my panel, nothing happens when I try to add it.

If I start mplayer and play a movie (after checking the volume in mplayer) then I don't hear anything.

---

### Post by 1oki on 2006-01-05
I also am having this problem... Its a widespread problem if you google it. I have tried everything that I could find... I have even tried as far as going to a Debian help site in hopes that Ubuntu may co-operate with me... alas no luck... If someone could help with a solution to this issue, that would be great... there are other flavours of Debian kernels out there that work with this sound card, but wont work with Ubuntu...

p.s.
Im a noob to linux... took a few classes in school, so i know the basics... Any help to point me in the right direction would be great! thanks everyone! :D

---

### Post by eddie303 on 2006-01-06
Hello fellow HP 4150/Neomagic users.

I have got the sound working with one way: Installing OSS/Linux from opensound.com. Now it is freely available  for home use for 4 months, after the period ends, you must download it once again and you can use it further (I think that in 4 months will be a new version anyway...) There are drawbacks... It prints a message while loading the module, which takes about 10 seconds, it prints character-by-character. While you install the OSS/Linux package, don't try to test the sound with the autodetected card (It detects Neomagic Magicmedia NM2200), but configure the card manually for driver nm256 - Neomagic Magicmedia 256 NMA2 - otherwise it hangs the computer while probing the module. The sound of games does not work very well (I have no esd installed, Frozen Bubble's sound is just like saying ddddd, and even Heroes 3 has troubles) 
[Here]("http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html") is a way, how to configure the sound with snd-cs4232 module, but it did not work for me, even with good parameters it gave me "No such device", I hope it will work for you, it may be a better solution than OSS/Linux.

Good luck, and please let me know, if anybody of you got thew sound working otherwise on Ubuntu!

Thanks in advance.

---

### Post by bernardfrancois on 2006-01-07
[QUOTE=eddie303]Hello fellow HP 4150/Neomagic users. 
[Here]("http://www.linuxdevcenter.com/pub/a/linux/2002/09/19/linuxlaptop.html") is a way, how to configure the sound with snd-cs4232 module, but it did not work for me, even with good parameters it gave me "No such device", I hope it will work for you, it may be a better solution than OSS/Linux.

Good luck, and please let me know, if anybody of you got thew sound working otherwise on Ubuntu!

Thanks in advance.[/QUOTE]

Lol, its we that should say thanks, you helped us... thanks!

I didn't try OSS/Linux yet, but I have read the page u mentioned (I also put that link in my first post). I didn't understand the information on that page (I didn't understand what to change exactly, and what it would do). Maybe you know which changes to make to use that module?

If I have some time (I'm preparing for exams now), I will try again, or install OSS/Linux drivers.

I'll surely post here what I did.

---

### Post by eddie303 on 2006-01-08
Hello again!

I tried it yesterday one more time, this time with alsaconf. (I copied over the alsaconf script from my gentoo box, because Ubuntu does not include it) It did try all the combinations of ports/IRQs/DMAs and finally it found a combination, and it could load the snd_cs4232 module. It wrote some lines in /etc/modprobe.conf and /etc/modprobe.d/sound, but it did not load the module on the end of the run, because the Ubuntu /etc/init.d/alsa script does not support restarting (I did not look further in the script). I was able to load the snd_cs4232 module manually with the parameters listed by alsaconf in /etc/modprobe.d/sound, it listed the card as cs4231 in /proc/asound/cards but id did not produce any sound at all. The interesting part is that it did load the module with other parameters than the ones set up in the BIOS setup... And even it does not load the module with those parameters.

As for OSS/Linux, installation is much like piece of cake. First you must unload all the sound modules, even soundcore and snd, move out the /lib/modules/2.6.whatever/kernel/sound directory from /lib/modules, otherwise hotplug loads them back and you cannot install OSS, it says it cannot unload sound modules. Execute depmod -a. Launch (as root, of course) the oss-install script (Even better from X), remove the automatically detected Neomagic NM2200, configure the card manually as Neomagic NM256 *NMA2*, review the parameters, and test if it works. Then here is a weak little script written by me, to put in /etc/init.d/oss:

```
#!/bin/bash
# Sound init script for commercial OSS/Linux package
# Created on Christmas, dec. 25. of 2005 by Eddie303
case "$1" in

start)
    echo "Loading OSS/Linux sound modules and enabling sound..."
    /opt/oss/bin/soundon
    ;;

stop)
    echo "Unloading OSS/Linux sound modules and disabling sound..."
    /opt/oss/bin/soundoff
    ;;
restart)
    echo "Restarting OSS/Linux..."
    /opt/oss/bin/soundoff
    /opt/oss/bin/soundon
    ;;
*)
    ;;
esac

```

then link this to the used runlevel's rcx.d. I linked it to /etc/rc2.d/S30oss. First I tried to link it as S99oss, but I had an issue of non-working keyboard in X - I think this can be linked with the message displayed by OSS on startup... Anyway, it works, it is a bit annoying, because I get repeating game sounds, but xmms/mplayer/vlc/xine works great (Of course as great as it can work on a P2/300). If I put the lappy to suspend, when resumed, there will be no sound at all. Maybe it would be good to execute soundoff before putting the machine to suspend ant soundon right after resume. I must try this, but xfce4-panel and xfce-mcs-manager sits on the audio device, and soundoff won't execute. I must write a script which kills these tasks as well and relaunches them on resume :)

As for exams, I will have exams too, but I am not in the mood for learning :( It seems that poor university students have weak old laptops :) I have got mine as a Christmas present from my boss, and as in the whole year of 2005 I was dreaming of a laptop, I am very happy for it. It is not a big deal, P2/300/128MB RAM/6GB HDD, but right enough for now :) I hope there will be even better :)

Good luck for the exams!

Eddie.

---

### Post by eddie303 on 2006-01-13
Update: It works now even with OSS/Free kernel modules shipped with Ubuntu. Just:
```
modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0
```
If it works to you too, then write the line without the modprobe command into /etc/modules. It seems okay, game sounds work now, XMMS works, I did not try yet other things. It has a strange behavior in xfce4-mixer, seems uncontrollable, after you adjust the volume, sliders jump back down...

It still has no sound after suspend-to-ram, even if you reload the module after resume....

Cheers:

Eddie.

---

### Post by bernardfrancois on 2006-01-14
Whooohooo! It works (with the modprobe command).  gmplayer made my laptop to produces some sound.

I realise I've a long way to go and a lot to learn about linux...

How did you come up with the idea to load module *ad1848* ? Are the io/irq/dma settings the one you found experimentally?

Some more info about my laptop (obtained with *lshw*)
```

     *-cpu
          size: 366MHz
          capacity: 433MHz
     *-memory
          size: 320MB
          capacity: 1GB
     *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: Internal
     *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: JDIMM1
             size: 256MB
             configuration: width=32
     *-bank:2
             description: DIMM DRAM Synchronous
             physical id: 2
             slot: JDIMM2
             size: 64MB
             configuration: width=32

```

Seems that I can still upgrade my processor and RAM. I wonder if that internal bank can be used to add more RAM, and if it's possible to change the processor.
But it's good enough for now, I can do everything I want with it (surfing, chatting, programming). I won't use a crappy laptop screen to play games or watch movies. It's my only linux-only computer, so I cherish it :) (I need windows for school).

---

### Post by eddie303 on 2006-01-15
Hello! :)

I am happy, because it works to you too :D The parameters are in fact the ones set up in BIOS setup. I have tried this module earlier, and as I remember, it did not load. As I saw, the ad1848 driver (Which is actually for Analog Devices AD1848, as I know, found on Windows Sound System cards) drives some Crystal-chip based cards too, look at it with dmesg. It says about CS4248. Anyway, it is good that it works.
    Thanks for mentioning the lshw command, I did not know it exists :) But now I will use it. 
As for me, I am a Linux-fanatic since about 2 years, but I have Windows on a 300 MB partition on this little fellow, for the same, school reasons, I must run Foxpro and Borland C on it. Shamefully,  it is in a bad-enough state, it was dropped down several times by the previous owner. As I know, it only has 2 RAM slots (My one was once disassembled into pieces by me, because the lower touchpad buttons did not work, and I have service manual for it, if you need it, anyway you'll find it on [www.eserviceinfo.com](www.eserviceinfo.com)) The CPU is indeed interchangeable, but it is on a proprietary CPU module, and you can change it only with the right Omnibook module. If you find a 400 or 433 MHz CPU for yours, I would purchase your current one :) But I think I will sell this little one, and get something more decent - Like an IBM Thinkpad, with a P3 CPU. I use this little one for pretty much anything, even for movies and old games (Heroes 3 for Linux rocks!). 
Did you try writing the line in /etc/modules? Did it work? :D

---

### Post by bernardfrancois on 2006-01-18
Two exams finished now, it went fine (unix and algorithms). Friday databases, which is more easy, so I have some time now to sleep and to spend on the ubuntu forums :-)

I added the line in the modprobe file, and it works (as expected). Its very nice to have sound now, I did almost forget that this computer is able to produce sound :)

Maybe after the exam's I'll try to learn more about enabling kernel modules.

I've been using linux for three years I think, but it's only since a year that I have abandoned windows (except for some school tasks as mentioned before). I started with FC2, later FC3 (on the same laptop, which was very slow), and then I moved on to Ubuntu. Maybe later I'll try different distributions, but I really like the fact that Ubuntu comes in one CD. I don't need three or more CD's to install outdated software which I won't even use...

---

### Post by eddie303 on 2006-01-23
Hey!

It is fine if you say that Databases is easy to you, I am afraid of SQL :) I am standing poorly with mathematics too.... 
I did try Redhat-based distros too, but I don't like rpm, and I hassled way too much because of dependency problems. I use mostly Ubuntu now, my home computer has Gentoo installed. I like Gentoo too, it was installed in september, 2004, when Ubuntu was just a future plan. The problem with Gentoo is it eats sooo many time taking care of it, while sometimes radical changes in config files are making trouble which you must solve in order to work properly.. If you do not update it regularly, you have a very fast system, but it is impossible to not-upgrade. 
I have tried Debian too, I downloaded Woody once, as it was considered stable, But when I saw, how old are those packages, I said no thanks... Then came a hungarian distribution called UHU Linux, based on Debian package manager, which was pretty good at that time... It is a shame that after about 3 versions we did not see a real upgrade... Enthusiasts make something there, but not really much.
I used Slackware too, but there again, dependency problems, and a lot of compile job, if I wanted something special. When I first read about Patrick Volkerding's decision about leaving Gnome out of Slackware, made me disappointed. Then came Ubuntu Warty, which I did try, then Hoary, which I did use... The things why I do not install Ubuntu on my home computer (I still have it on 3 more, which I use), because I could not manage to get Lirc to work, and I had some problems with gxmame, which I like a lot, as I play old coin-op games emulated.
As for this little one, I would install Gnome, but I think it would not really run it usable. So I will remain at XFCE, and maybe if Enlightenment 17 gets stable, I will use it too.

---

### Post by towner on 2006-04-10
Thank You Eddie303,

Just managed to squeeze a bit of sound from my omnibook as well.

:-D

---

### Post by panth0r on 2006-04-17
Hello, I was wondering which revision of the 4150 all of you have, I have a 4150A with revision 12 of the NeoMagic sound card and it's not yet working, I'll keep you updated if I get better luck.  Thanks for posting a solution to try, though.

EDIT: Also, if there's anything besides modprbe the right driver you did to make it work, please tell me, I'm really desparate.  Thanks again.

---

### Post by bernardfrancois on 2006-04-17
Only a modprobe is enough to load the driver. This doesn't mean you will hear sound, the volume might be muted in alsamixer or on your hardware (press Fn + KeyUp multiple times).

If you still can't get it to work, you might try to follow the [HowToSetupSoundCards-guide at the wiki](https://wiki.ubuntu.com/HowToSetupSoundCards). That's how eddie303 managed to get it to work. You might have to find another driver.

---

### Post by panth0r on 2006-04-17
[QUOTE=bernardfrancois]Only a modprobe is enough to load the driver. This doesn't mean you will hear sound, the volume might be muted in alsamixer or on your hardware (press Fn + KeyUp multiple times).

If you still can't get it to work, you might try to follow the [HowToSetupSoundCards-guide at the wiki](https://wiki.ubuntu.com/HowToSetupSoundCards). That's how eddie303 managed to get it to work. You might have to find another driver.[/QUOTE]
The first paragraph stuff I tried already, thanks though.  Here is the output of alsamixer, by the way:

alsamixer: function snd_ctl_open failed for default: No such file or directory

I'll try the sound card setup, thank you.

---

### Post by panth0r on 2006-04-17
Hello, I tried your suggestion, and I actually think I'm having better luck, I found my sound card to be a CS4237 card, so I tried "sudo modprobe snd-cs4236" because this is the suggested driver, but the following was outputted:

FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.12-9-386/kernel/sound/isa/cs423x/snd-cs4236.ko): No such device
FATAL: Error running install command for snd_cs4236

If I try to modprobe, for example snd-cs4235, I get "module snd_cs4235 not found," so I may be doing better.  I'll try more of ideas (both other's and mine) later on.  Sorry for being such a jerk, by the way (I normally prefer to figure things like this out on my lonesome), but this lacking sound thing is getting on my nerves.  Thank you for any help.

---

### Post by bernardfrancois on 2006-04-25
Lol, you're not a jerk; by posting your questions on the forums and getting them answered you're helping other people who might read this thread in the future.

Did you manage to make it work now? I don't know why that driver doesn't want to get loaded, maybe it's not fully supported and you'll have to re-compile the kernel? I don't know much about this stuff though, never had a problem like that nor recompiled the kernel.

---

### Post by panth0r on 2006-04-28
You're right, bernardfrancois, I've done extensive reading into getting sound to work on that computer and the most feasible advice under the 2.6 kernel was to get a PCMCIA soundcard, if I ever get it working, I'll be sure to post what I did, I'll probably do a lot more work on it over the summer, thanks for replying!

---

### Post by eddie303 on 2006-05-04
Hey!

I came back accidentally, and I see, somebody has the problem I had half a year ago...

Panth0r, look in your BIOS for your soundcard settings (irq,dma,...), and try to load the ad1848 module, my laptop is working with this setting even now. On my machine is loaded like this:

modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0

The parameters listed are the parameters which are in the BIOS setup.
If this does not work, I suggest you to try out the OSS/Linux drivers, as in the first round I've managed to work with them. In neither case will work the sound after a suspend/wake cycle. :(
On the other hand, please let me know somehow if somebody has a non-working laptop like this (i.e. for recycle or dispose) and can send it somehow in Romania, I would be thankful, my one is broken on several places on the backside, and is kept in a piece by glue :( The guy, who owned it before me, apparently was not careful enough and managed to break it in a way, that when I first opened it, I saw even the cooler was broken into pieces. And I have no possibility, to change this machine in the following 1 or 2 years, I will need to use it, as it is.

---

### Post by bernardfrancois on 2006-05-05
[QUOTE=eddie303]
On the other hand, please let me know somehow if somebody has a non-working laptop like this (i.e. for recycle or dispose) and can send it somehow in Romania, ...
...
And I have no possibility, to change this machine in the following 1 or 2 years, I will need to use it, as it is.[/QUOTE]
If it would happen that I don't need mine anymore within one or two years, I'll send it to you.

I also still have another (but broken) toshiba laptop. The only problem is that the female power connector contact is broken. I tried to open it (I hope I didn't do more damage by opening it, it was realy tricky to open), but the female power connector is so unreachable that I gave up after a few hours.
If you would be interested in that laptop, please contact me on yahoo. Note that it's a slightly slower laptop than the omnibook 4150 I have here.

---

### Post by eddie303 on 2006-05-06
Thanks in advance, bernardfracois, I added you on my yahoo messenger cl, I hope we can talk there. 

Now, to be a bit on-topic:
I tried the snd-cs4232 module now, after I have upgraded to Dapper. but still no luck. The ad1848 module still works falwlessly, despite it says in dmesg that it has an IRQ conflict... Yes, maybe because it is an "emulated" MSS card, and ad1848 (which is intended for ISA sound cards) does not know about pci irq sharing?

---

### Post by mellowman on 2007-05-01
Hi Eddie, hi Bernard,

thanks for your much appreciated advice, but it doesn't (yet) work on feisty. Before I used Debian Sarge on my Omnibook 4150 with NeoMagic rev 12 device and with the modules.conf lines (mpu401, ad1848, opl3) recommended earlier in the thread sound worked fine.

But after changing to Feisty 7.04 I can't get sound. The problem is: If I do 

[FONT="Courier New"] modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0 [/FONT]

it says: No such device. If I leave away the irq parameter it says: Invalid argument. If I drop the io parameter it loads but no sound card is detected by Kmix for instance.

If you could help me I would be very glad. A computer without sound is so lonesome, you can't even hear when someone contacts you via IM!

THX in advance,

mellow

---

### Post by mtvoid on 2007-05-09
Hi all
I know I'm not alone in my troubles with sound on the OmniBook 4150... Anyway, I thought of posting instructions to help set up sound on one's Ubuntu system.

There are various ways of getting sound drivers to work successfully, and all suffer from the same problem, of having issues with APM suspend/resume on the system. That's my only grouse with the sound drivers. I had filed a bug report on the ALSA bug tracking system also, you may check it here, where I have put in my observations... [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=234](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=234)

Now on to the instructions:

**Method 1: OSS**
Sound works with the ad1848 driver, as mentioned before in this thread. You need to do:
```
modprobe ad1848 io=0x530 irq=5 dma=1 dma2=0
```
This should get it working

I've heard that the OSS/Linux drivers from opensound.com work perfectly, even allowing for suspend/resume, but the latest v4 of the drivers have dropped support for the ad1848, and an older version I have fails to compile on the newer kernels :( . Anybody has any experience with these drivers?

**Method 2: ALSA**
ALSA can also be used. I know of three drivers that work - snd-cs4231, snd-cs4232 and snd-ad1848. Of these, I would recommend the latter, since the first two screw up suspend (the system will not resume from suspend once you load them). Here are the relevant modprobe lines:

```
modprobe snd-cs4231 port=0x534 irq=5 dma1=1 dma2=0
```

or

```
modprobe snd-cs4232 port=0x534 cport=0x538 mpu_port=-1 fm_port=0x388 irq=5 dma1=1 dma2=0
```

or (**RECOMMENDED**):

```
modprobe snd-ad1848 port=0x534 irq=5 dma1=1
```

Note: You might want to load snd-ad1848-lib before snd-ad1848. For some reason, trying to load snd-ad1848 with module parameters fails if snd-ad1848-lib isn't already loaded. However, doing modprobe snd-ad1848 (without parameters) and then repeating with parameters works!

Finally, some Ubuntu-specific configuration is required before using the above instructions:
Do a 'sudo dpkg-reconfigure linux-sound-base'. Here chose OSS or ALSA according to your preference. What this does is blacklist the ALSA/OSS drivers according to your choice, so they don't get loaded.
If you are using ALSA, you should further blacklist two other modules, snd-nm256 and snd-opl3sa2, else the autodetection will cause these to be loaded, which you don't want. You can simply add these lines to /etc/modprobe.d/blacklist:

```
blacklist snd_nm256
blacklist snd_opl3sa2
```

This should get your sound working. I hope this helps!

---

### Post by bernardfrancois on 2007-05-19
Thanks for the information! For now I'm still using ubuntu 5.04 on the omnibook, but I think I'll upgrade to a newer version soon (within a few months). I'll post something here to let you know whether it worked or not.

---

### Post by billstei on 2007-06-30
I have an Omnibook 900 running Xubuntu which has the same Neomagic 256AV sound chip and was not able to get snd-cs4232 to work (said "No Such Device"), but here is what is now working:

In file /etc/modules added this line:

snd-cs4231

In file /etc/modprobe.d/sound I have:

blacklist snd-nm256
blacklist snd-opl3sa2

alias snd-card-0 snd-cs4231
alias sound-slot-0 snd-cs4231
options snd-cs4231 port=0x534 irq=5 dma1=1 dma2=0

In the BIOS I have the port set to 0x530 but apparently it needs to be spec'ed as 0x534 in the options.  I see in the post above that the blacklisted snd-nm256 is given as snd_nm256 (underscore versus dash).  Will that matter?  Not sure, but I used dashes.

Hope that helps someone,
Bill

---

### Post by bernardfrancois on 2007-10-31
> **bernardfrancois said:**
> Thanks for the information! For now I'm still using ubuntu 5.04 on the omnibook, but I think I'll upgrade to a newer version soon (within a few months). I'll post something here to let you know whether it worked or not.

My omnibook doesn't work any more. I never had a chance to install a higher ubuntu version on it, so I can't tell if it worked out or not.

It actually was a quite robust laptop, it survived after falling down the stairs and accidentally having a glass of wine poured over it (after that glass of wine, I quickly removed the battery to avoid short circuit and turned the laptop upside down).

---

### Post by jaezcurra on 2007-11-02
> **billstei said:**
> I have an Omnibook 900 running Xubuntu which has the same Neomagic 256AV sound chip and was not able to get snd-cs4232 to work (said "No Such Device"), but here is what is now working:

In file /etc/modules added this line:

snd-cs4231

In file /etc/modprobe.d/sound I have:

blacklist snd-nm256
blacklist snd-opl3sa2

alias snd-card-0 snd-cs4231
alias sound-slot-0 snd-cs4231
options snd-cs4231 port=0x534 irq=5 dma1=1 dma2=0

In the BIOS I have the port set to 0x530 but apparently it needs to be spec'ed as 0x534 in the options.  I see in the post above that the blacklisted snd-nm256 is given as snd_nm256 (underscore versus dash).  Will that matter?  Not sure, but I used dashes.

Hope that helps someone,
Bill

I succeeded with a clean Xubuntu 7.10 install on a 1999 HP Omnibook 4150 (Pentium II 300, 128 MB memory and 20 GB disk).  My only issue had been sound and thank to you now it works!!!:)

Thanks again and my suggestion to whom it may concern: just put [SOLVED] before the thread name, so everyone with this problem can find a final solution.

---

### Post by Funk Phenomena on 2008-05-24
Just wanted to say thanks to billstei.  That did the trick for me.  Yeesh, ancient technology, but it works!  Omnibook 900, PII, and 288mb ram.  The hardest part for me was just getting Xubuntu on... ugh... I wound up changing out the cd drive to get it to recognize the disk and even that was after a lot of wtf head scratching.

Thanks again... and to Ubuntuforums.org

---

### Post by fern on 2008-06-23
This problem is not solved at all, never was, and it has been years.

This problem, apparently, was solved by installing another form of Linux, Kubuntu, if I am not mistaken.

Ubuntu still doesn't have sound in the HP OmniBook 4150.

I am not bitter about it, because I have Windows that actually works, but the problem continues.

Fern

---

