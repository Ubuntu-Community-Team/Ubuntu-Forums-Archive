---
title: "Ubuntu 5.10 Breezy Badger on an IBM Thinkpad 600 Laptop"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by REInvestor on 2005-11-28
It seems like I am not the only one working on getting the latest Ubuntu on one of these old laptops, so I decided to post my findings here for the next newbie (like me) to come along with some “common issues”

First though, I want to explain why this is a good test case for Ubuntu 5.10 and why I specifically wanted to run this distribution.  The Thinkpad 600 is readily available very cheap.  I have put two together off piece parts purchased on eBay for a combined $300.  This lightweight system has 1024x768 resolution and with a new battery could have 4 hours of battery life.  It also supports 256MB extended RAM (which I have on each) making it a functional system for all applications.  It may not be fast in the sense of newer laptops, but it can get the job done.  To the point though, it can be bogged down with too many services running so it should be run with only what is necessary, which partly turned me to Ubuntu.  I have tried many distributions, but so far most of them want to install applications I do not want or need.  Ubuntu, like Debian, does not detect the network card during installation, but unlike Debian, can be installed from only one disk.  Once the system is up it requires some “tweaks”, but it will be functional to help me with my test, which is to determine whether or not I can survive without dreaded windoze.  After years in high tech, I am currently (for the last year) a Real Estate Agent and Mortgage Broker and I need a new Laptop (I have a very functional WinXP desktop I am using for the job now). There are some very specific applications I need.  Some already exist or have a suitable equivalent on Linux, others will required Wine.  But if I can prove on this old laptop it can be done, I will be able to justify spending a lot of money on what I really want, a top of the line Laptop running Linux that I can use for work.

Now, to the installation and problems found.  First, during installation the Linksys PCM200 Ethernet PCMCIA card was not detected, so I just skipped it and went on with the installation.  Everything else went smoothly and after and hour or two I had a functional laptop.  The following issues were found:
1. Display Resolution set to 800x600
2. Ethernet not working
3. No Sound (not a big surprise for anyone that has tried Linux on this laptop before)

The display problem was an easy fix, but it certainly took me a long time to find it.  In System->Preferences->Screen Resolution I only had 800x600 and 640x480.  I googled and found some info for editing /etc/X11/xorg.conf, but nothing I found seemed to work.  Finally I ran “sudo dpkg-reconfigure xserver-xorg” from terminal and attempted to reconfigure X.  I changed everything to no avail until I stumbled upon one of the very last options – default depth.  The instructions say it is safe to use 24bit and it keeps that as the default, but apparently the Thinkpad 600 does not support 1024x768 with millions of colors.  Once I changed this value to 16, I was able to change the screen resolution of the desktop to 1024x768 and troubleshoot the other problems with at least a full screen. 

Note --> I got a little hung up on sudo... there is no root on Ubuntu.  Basically, whatever password you set up for your original user is used with all sudo commands or anytime you open an application that requires root access.  The color depth can be changed without running the configuration script by entering in terminal #sudo gedit /etc/X11/xorg.conf and changing the default depth to 16:
Section "Screen"
	 Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2160 [MagicGraph 128XD]"
	Monitor	"Generic Monitor"
	DefaultDepth	16

The Ethernet not working was an easier bug to fix, but it was even less obvious.  In GRUB, acpi=off must be added to the kernel line.  Edit the file /boot/grub/menu.lst.  This is how mine looks.

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 acpi=off apm=on ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

After adding acpi=off, a supported PCMCIA ethernet card should be found.  I actually did another installation on a second thinkpad and used acpi=off for the installation boot command and it properly detected the card.  I guess knowing what to do before starting help a bit.

The Sound Problem I have still not resolved.  I have had sound working with other distributions on both of my laptops, but can not get it to work with Ubuntu 5.10.  Others have reported success on the 600e and 600X, but I have not found a proper solution for the 600.  Alsaconf is not included in the Alsa-utils, so I installed the latest alsa-utils that does indeed have it.  This does properly find the cs4232 sound device, but it fails loading the module.  I am wondering if this is a kernel issue or not.  If anyone has gotten it to work, please post detailed steps here.

---

### Post by mistergq on 2005-11-29
Reinvestor - I have been working on the sound problem.  My modules are loaded, but no sound.  From what I am reading, there is an issue with 1.0.9 Alsa.  I am trying to install 1.0.10, but I cannot get it to install.  What I would like to do is recompile the kernel with 1.0.10 drivers, but as a newbie, I am not sure exactly how to do that.  I have the Vanilla Kernel running on my laptop.

---

### Post by grumpymole on 2005-12-04
For the sound, see [http://www.ubuntuforums.org/showthread.php?t=94414]("http://www.ubuntuforums.org/showthread.php?t=94414")

Regards

Warren

---

### Post by REInvestor on 2005-12-05
Warren,

This fix does not work for the 600.  The fix for the 600e, when Ubuntu recognizes the wrong driver, is not the same problem.  On the 600, it doesn't find anything.  It seems like adding a modprobe cs4232 0x530...  into a local script or something should work (this worked for DSL).  I tried installing downrev ALSA Utils, which works for 4 other distributions I tried, but that did not work.

If you have any other ideas, we appreciate it.  I noticed you have suggested this link in other threads, but please understand it hasn't worked for those of us with the 600.

---

### Post by grumpymole on 2005-12-08
My experience is all with my 600e.  Sorry.

Regards

Warren

---

### Post by obriente on 2006-01-03
I had lots of trouble getting Ubuntu to run on my 600x.  eventually I found a post that told me to use "acpi=force pci=noacpi" during install or adding it to /boot/grub/menu.lst
that fixed my issues with the pcmcia card and the sound maybe it'll work on the 600 too, i believe they have the same soundcard

---

### Post by gotaserena on 2006-01-04
[QUOTE=obriente]I had lots of trouble getting Ubuntu to run on my 600x.  eventually I found a post that told me to use "acpi=force pci=noacpi" during install or adding it to /boot/grub/menu.lst
that fixed my issues with the pcmcia card and the sound maybe it'll work on the 600 too, i believe they have the same soundcard[/QUOTE]

FWIW I could never get acpi to work on my tp600. I've disabled it (acpi=off) and got the sound card to work. My /etc/modprobe.d/alsa is as follows:

```
alias char-major-116 snd
alias char-major-14 soundcore

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-css
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1
alias sound-slot-2 snd-card-2
alias sound-slot-3 snd-card-3

alias sound snd-card-0
alias snd-card-0 snd-card-cs4236

alias snd-minor-oss-0 snd-card-cs4236
alias snd-minor-oss-1 snd-opl3
alias snd-minor-oss-3 snd-pcm-oss

options snd-cs4236 port=0x530 cport=0x538 mpu_port=-1 fm_port=0x388 irq=5 dma1=1 dma2=0 isapnp=0 sb_port=0x220
```

IFRC there's a howto on alsa webpage, and it helped me a lot when setting this up.

---

### Post by davinci on 2006-01-06
My thinkpad 600 (2645-850) finally works quite fine with Breezy, maybe I can help ..

Sound is working with acpi turned on (after lots of try & error). 
network fully working
acpi itself works, too (cpu temp sensors, sleep states...). 
Sleep (S1) is ok
suspend (S3) loses sound after resume (working on that; maybe i just have to reload modules and restart alsa after resume)
Hibernation is fully working.
Some of the Fn+ buttons work (sleep, hibernation for lidshut), working on others ..

Currently I have a self compiled, fully customized vanilla 2.6.15 kernel, but things have worked with the default 2.6.12-9 kernel too. But boot time is significantly faster with this kernel (minus 30 secs) ...

my boot parameters are:  pci=noacpi pci=usepirqmask vga=790 ro quiet

/etc/modules contains: snd-cs4236

/etc/modprobe.d contains: options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0

Currently working on tpctl .... won't compile with 2.6.15

Hope it helps ....

PS: my first posting here! Hi everybody!

---

### Post by gotaserena on 2006-01-06
Hello, davinci,

Since I've read your post I tried for a few hours to get the sound working with acpi on to no avail. Would you please post your .config file so I could see if I missed something? TIA.

---

### Post by davinci on 2006-01-07
I assume you want the custom kernel config so I've attached it. Notice that I have not activated some options I do not use (Bluetooth,IRDA, Reiser ...). And you probably have to adjust options like "default resume partition" to your config.

I forgot to mention one important point. Turn fast boot !OFF! in the BIOS.

---

### Post by gotaserena on 2006-01-07
thanks a bunch! Now I've just to figure out how to turn the serial port off so I can use the modem and I'll be a happy camper :)

---

### Post by gotaserena on 2006-01-08
Hello, davinci

Thanks to you I could get the sound to work with acpi on, I think you should put this up somewhere and/or write a HOWTO about this. The tp600 is incredibly popular and I bet there are a lot of people around which would love to get the thing to work under linux.

About the modem I unfortunately could not get everything to work as it should. First I couldn't modprobe mwave since the COM1 serial was supported on kernel and I couldn't switch it off to free the IRQ needed by the modem.

Then I proceeded to a custom kernel (well, not that custom: 2.6.14-r10 suspend2 sources from gentoo), in which I used your .config, plus mwave and serial support built as modules. I 've managed to modprobe mwave during boot **before** the serial modules -- the other way around doesn't work. The modem seems to be working fine.

Problem is, when the mwave module is loaded, the sound is gone. Alsa controls are still there, but nothing comes out of the speakers. WAV files are stuck at 00:00. I reckon it's some problem between the mpu-401 midi device and the modem, but /sys/devices/pnp0 shows that the midi is disabled. Logs don't show anything. Hope that someone more knowledgeable will take notice and set out to solve this.

---

### Post by davinci on 2006-01-09
Nice to hear, that you have proceeded in your quest for a perfect setup. ;) Guess we both still have a long way to go ....

Unfortunately I can't help much with the modem as I have a cable connection for the internet. So I never needed to configure it. But have you read the mwave README? Some nice options. Maybe they help to solve the ressource conflict.

mwave_3780i_irq=5/7/10/11/15
        If the dsp irq has not been setup and stored in bios by the
        thinkpad configuration utility then this parameter allows the
        irq used by the dsp to be configured.

  mwave_3780i_io=0x130/0x350/0x0070/0xDB0
        If the dsp io range has not been setup and stored in bios by the
        thinkpad configuration utility then this parameter allows the
        io range used by the dsp to be configured.

  mwave_uart_irq=3/4
        If the mwave's uart irq has not been setup and stored in bios by the
        thinkpad configuration utility then this parameter allows the
        irq used by the mwave uart to be configured.

  mwave_uart_io=0x3f8/0x2f8/0x3E8/0x2E8
        If the uart io range has not been setup and stored in bios by the
        thinkpad configuration utility then this parameter allows the
        io range used by the mwave uart to be configured.

Example to enable the 3780i DSP using ttyS1 resources:

  insmod mwave mwave_3780i_irq=10 mwave_3780i_io=0x0130 mwave_uart_irq=3 mwave_uart_io=0x2f8

Besides, good idea with the HowTo. Will think about it when I have more spare time. And a better setup, hopefully. I'll let you know.

---

### Post by Jackal82 on 2006-02-02
Has anyone had problems with PCMCIA - wlan card and TP 600?

I have huge problems getting my A-Link WL54PC working. The card is supported by Ubuntu and I am able to scan available SSID:s but the lights of my card are not blinking and I cannot get an IP address.

---

### Post by davinci on 2006-02-02
I  tried several days to get a Realtek 8185L based wlancard working. Compiled kernels from 2.6.12 to 2.6.15.1. Used Ndiswrapper and the modules from the rt818x project. The only success was that I could scan access points but not a single ping worked and a I got a lot of kernel oopses. Based on my tests I guess that both drivers failed to activate the radio part.  Oh well.

Then I bought a Atheros based adapter. Compiled the madwifi-ng driver, set up the interface and after 15 minutes everything was working ... 

I think your card is based on the Ralink chip. Try a static address and ping your router.  Do ou use WEP? Correct key? Double check all your settings!

Even better start a new thread with your specific problem and list as much information as possible. lspci, dmesg, iwconfig, /etc/network/interfaces ....

---

### Post by Jackal82 on 2006-02-02
[QUOTE=davinci]I  tried several days to get a Realtek 8185L based wlancard working. Compiled kernels from 2.6.12 to 2.6.15.1. Used Ndiswrapper and the modules from the rt818x project. The only success was that I could scan access points but not a single ping worked and a I got a lot of kernel oopses. Based on my tests I guess that both drivers failed to activate the radio part.  Oh well.

Then I bought a Atheros based adapter. Compiled the madwifi-ng driver, set up the interface and after 15 minutes everything was working ... 

I think your card is based on the Ralink chip. Try a static address and ping your router.  Do ou use WEP? Correct key? Double check all your settings!

Even better start a new thread with your specific problem and list as much information as possible. lspci, dmesg, iwconfig, /etc/network/interfaces ....[/QUOTE]


Ok. I did that --> [http://ubuntuforums.org/showthread.php?t=124937](http://ubuntuforums.org/showthread.php?t=124937)

No, I don't use WEP and settings are ok. Static IP doesn't help either.

---

### Post by Jackal82 on 2006-02-04
[QUOTE=davinci]
Then I bought a Atheros based adapter. Compiled the madwifi-ng driver, set up the interface and after 15 minutes everything was working ... 
....[/QUOTE]

What is your wlan pcmcia card model?

---

### Post by davinci on 2006-02-04
It's a D-Link DWL-G650   rev. 3  (no + !!!!, they use another chip)

---

### Post by mohapi on 2006-02-05
Thanks for this post. I want to try the acpi=off trick on my laptops, and see if it helps with my [PCMCIA issues]("http://ubuntuforums.org/showthread.php?t=125334"). Wish me luck. ;)

---

### Post by mohapi on 2006-02-05
Sort of successful, sort of not. Setting acpi=off allows me to communicate with the CF card reader, but the wireless cards continue to ignore me. :mad: One day I will solve this little puzzle, and I shall dance the victory dance.

---

### Post by Jackal82 on 2006-02-05
[QUOTE=davinci]I  tried several days to get a Realtek 8185L based wlancard working. Compiled kernels from 2.6.12 to 2.6.15.1. Used Ndiswrapper and the modules from the rt818x project. The only success was that I could scan access points but not a single ping worked and a I got a lot of kernel oopses. Based on my tests I guess that both drivers failed to activate the radio part.  Oh well.

Then I bought a Atheros based adapter. Compiled the madwifi-ng driver, set up the interface and after 15 minutes everything was working ... 
....[/QUOTE]

Dude, I have been struggling for several weeks now to get my pcmcia wlan card working without succeeding.

Could you please tell me exactly how do I do that..???

I have Ubuntu Dapper 2.6.15-14-386 with IBM TP 600 and Ralink based card.

---

### Post by Jackal82 on 2006-02-06
Problem solved with this:

[https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig?highlight=%28ralink%29](https://wiki.ubuntu.com/WifiDocs/RalinkRT2500/DriverAndRaconfig?highlight=%28ralink%29)

---

### Post by dbeltr1 on 2006-02-16
I came across a TP 600-2645-85U a friend of mine had given 5 years ago because he received it DOA (It's amazing what you find stored away in a closet). Well, after some tinkering, $56.95 in parts, and wanting to install a Linux OS (Ubuntu). It is up and running. The applications run and respond well (bringing a tear to my eye at one point). 

Needless to say, thank you all for tips and tidbits. I look foward to continued tinkering on this machine using Ubuntu. A bit of nostalgia overwhelmed me while using Ubuntu, as it brought back high school memories of programming way back in the the late 80's.

---

### Post by tts on 2006-03-10
@davinci: i've got the same model of tp and im looking for solution of sound problem for years. would you like to post complete solution for this problem for linux newbie like me?

---

### Post by pablo180 on 2006-03-30
Hi, I'd just like to ask any of you IBM Thinkpad 600 users if any of you have any trouble with speed and Ethernet?

I bought a Belkin USB to Ethernet adapter, which works perfectly, except that it will only run at a top speed of 110K, whether on the internet or the LAN. It only does this on the Thinkpad, on another PC with Breezy it works fine!

Is this something to do with Ethernet on the laptop? Been thinking about getting a PCMCIA card but won't bother if that is the laptop's top speed.

---

### Post by sudoer on 2006-04-19
hi there am newbie using ubuntu with an old thinkpad 600e, i have conflict  with sound and pcmcia my computer just freezes with the pcmcia when i boot with some parmetres pci=noacpi pci=usepirqmask can't manage to work both of them at time...i either have sound and no network or network with no sound !

can anyone explain how to use that script > gz config-2.6.15.txt.gz posted by davinci........ any other solution is welcome. thanks

---

### Post by el duderino on 2006-05-02
Hello Thinkpad 600 users.

I've been trying to work out all the hardware snags on my Gateway Solo 5150.
It was "competition" for the 600. I ended up upgrading my CPU with one pulled from a 600e? MMC-1. 

Anyway I'm having almost the same problems you guys have mentioned. Soundcard is not working. I haven't chased all the links and whatnot yet.
Also having probs with my PCMCIA wifi card. 

Is it normal for a PCMCIA card to be dectected as a PCI? It comes up as a Ralink 2400? The card is a SMC 2635W. Supposed to work well, but I'm driving it so...
I did get it to search for SSIDs. It did find a couple, mine, my neighbors. Still no joy though. 

Just wanted to toss in my two cents and the name of my laptop so that searches would find some relative info on the Solo 5150 probs I've had.

I'll update with my progess when I have some....

---

### Post by bforbarry on 2006-05-03
Newbie here. Following REInvestors instructions, I tried to edit the command line in the GRUB folder, to get my ethernet working, but it won't save it. Says I don't have permission. Is there another work around ? 
thanks.
ibm aptiva P300, 128mb, Dapper

---

### Post by spartan777 on 2006-05-04
Reinvestor: here's a small suggestion for the whole 'root' deal with ubuntu. install the root-nautilus scripts with automatix. they've helped speed up my fixing many, many problems. here's the thread:

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)


the scripts become a part of the right-click menu, so you can edit .conf files or whatever. just be careful not to mess stuff up with root.

---

### Post by zambotti on 2006-05-06
[QUOTE=bforbarry]Newbie here. Following REInvestors instructions, I tried to edit the command line in the GRUB folder, to get my ethernet working, but it won't save it. Says I don't have permission. Is there another work around ? 
thanks.
ibm aptiva P300, 128mb, Dapper[/QUOTE]

I have exactly the same problem.  I can edit, but not save.  How do I get permission?  Thanks.

---

### Post by dzisler on 2006-05-06
Thanks for all the posts, seems like I have ran into all the issues mentioned in the post. I too was a lucky recipient of a TP600. I wanted to try a Linux OS and this was my opportunity. Keep posting, it has sure helped me out. I have just loaded it on the TP600 and I am in the process of trouble shooting it. For the most part the whole process was pretty painless. So, from a newbie to Linux (me) I will keep you posted on the progress if you are interested.

---

### Post by pablo180 on 2006-05-14
[QUOTE=pablo180]Hi, I'd just like to ask any of you IBM Thinkpad 600 users if any of you have any trouble with speed and Ethernet?

I bought a Belkin USB to Ethernet adapter, which works perfectly, except that it will only run at a top speed of 110K, whether on the internet or the LAN. It only does this on the Thinkpad, on another PC with Breezy it works fine!

Is this something to do with Ethernet on the laptop? Been thinking about getting a PCMCIA card but won't bother if that is the laptop's top speed.[/QUOTE]

Found the solution to my problem, and thought that I should post it for the benefit of other users. Quite simple really, I installed Dapper Drake. Now I have full speed Internet and 11Mbps LAN. 

Don't know why the above adapter didn't work properly on the Thinkpad 600 with Breezy, it worked just fine on the PC with Breezy. Maybe it was just some quirk of the drivers and the laptop. 

Anyway if anyone searches; Belkin USB to Ethernet Adaptor and Breezy doesn't work, try Dapper Drake.

---

### Post by dzisler on 2006-05-21
Did you have a sound issue also. Did dapper take care of this? I would be intersted in hearing.

---

### Post by pablo180 on 2006-05-21
[QUOTE=zambotti]I have exactly the same problem.  I can edit, but not save.  How do I get permission?  Thanks.[/QUOTE]

You have to open the file using the terminal, once the terminal is open type:

```
sudo gedit /boot/grub/menu.lst
```

I am not sure the above is the right location but the sudo part is the important bit, sudo stands for (Super User DO) and give you full access to the file.

You can also type this in the terminal;

```
gksudo nautilus
```

That opens a Gnome window that give you full access, which is much easier for moving files around.

---

### Post by pablo180 on 2006-05-21
[QUOTE=dzisler]Did you have a sound issue also. Did dapper take care of this? I would be intersted in hearing.[/QUOTE]

I did have the sound problem (no sound whatsoever) and tried all the fixes I could find but nothing worked. Dapper has the latest version of ALSA (1.0.10) but the problems remained the same, it doesn't detect the sound card at all.

---

### Post by dzisler on 2006-05-25
I will try these things next....time permitting. Also maybe this link will be help
[http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)

---

### Post by chrish91 on 2006-05-29
Hi!

Sorry If to be a nuesence (sp?)' but, I'm new to Ubuntu, and Linux in general.
I have a ThinkPad 600E, and, have the Sound issue. ](*,) 

I don't quite get how to fix it, with all the instructions mentioned, so, could someone be kind enough to possibly post a step-by-step method? :)

Thanks in advance,
Chris.

---

### Post by gotaserena on 2006-06-04
Hi chrish91, one of the solutions that you can find around the forum must work. I suggest you start by modifying the boot options:
# kopt=root=/dev/hda1 ro acpi=off pnpbios=off
and don't forget to update-grub afterwards. Now you can try the alsa modifications suggested here and in other topics. 

For anybody else: I couldn't make sound work with acpi turned on (using davinci's solution) in dapper. But that's another problem altogether.

---

### Post by starpause on 2006-07-25
> **REInvestor said:**
> 
Note --> I got a little hung up on sudo... there is no root on Ubuntu.  Basically, whatever password you set up for your original user is used with all sudo commands or anytime you open an application that requires root access.  The color depth can be changed without running the configuration script by entering in terminal #sudo gedit /etc/X11/xorg.conf and changing the default depth to 16:
Section "Screen"
	 Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2160 [MagicGraph 128XD]"
	Monitor	"Generic Monitor"
	DefaultDepth	16


i chose to edit xorg.conf rather than running the configuration utility. i had to restart my computer to get the higher resolution. is there a slicker way to make those changes take effect?

---

### Post by evenzur.yossi on 2008-02-19
Hi
You seem to have a lot of experience with the 600X, i have one with XP sp2 and i wanted to install Ubuntu 7.10 from a bottable CD, to my amazement the laptop didn't recognize the CD as a  boot installation, other laptops do recognize it, any idea why?

---

