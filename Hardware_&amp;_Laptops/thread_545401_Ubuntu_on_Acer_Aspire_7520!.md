---
title: "Ubuntu on Acer Aspire 7520!"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by Niej on 2007-09-07
Hello people!
I have an Acer Aspire 7520, brand new and I was wondering if anyone knows if ubuntu would work in this computer, or some tips about intallation. It comes with an Nvidia GeForce 7000M and I hear it caused some problems. I would get an image cd of Ubuntu and start trying.
By the way, I need ubuntu and it f* rocks!!!!!! :D)
Thanks!!

---

### Post by beerjen on 2007-09-13
I've tried it and it doesn't work. I have the same acer 7520. 
Live cd doen't boot. Alternate cd with text based install works great until the reboot. The x-server doesn't start. 
Now looking for solutions because I removed Vista. 

If I get it to work, I'll let you know. Please, do the same if you get it to work.

Thanks

---

### Post by pepesz on 2007-09-13
Hi Guys,

I have Aspire 7520 with GeForce 8400M. Once I managed to install kubuntu 7.04 using live dvd and safe mode. I even managed to start nvidia (downloaded from nvidia binary package and installed). Then I did dist-upgrade and that was it. The system doesn't start anymore :(
Did you managed to make some progress with your kubuntu? 

TIA

---

### Post by beerjen on 2007-09-14
Tonight I'm trying with gutsy. If that doesn't work i'm installing vista again. Damn, I hate this

---

### Post by silviuciuca on 2007-09-15
i have the same problem with Aspire 7520 & GeForce 8400M
but i can install and run ubuntu in x on a second monitor conected

---

### Post by silviuciuca on 2007-09-15
to make it work i had to download and install this
[http://people.ubuntu.com/~bryce/Testing/nv_2.1.2-Feisty/xserver-xorg-video-nv_2.1.2-2ubuntu1_i386.deb]("http://people.ubuntu.com/~bryce/Testing/nv_2.1.2-Feisty/xserver-xorg-video-nv_2.1.2-2ubuntu1_i386.deb")


```

wget http://people.ubuntu.com/~bryce/Testing/nv_2.1.2-Feisty/xserver-xorg-video-nv_2.1.2-2ubuntu1_i386.deb
sudo dpkg -i xserver-xorg-video-nv_2.1.2-2ubuntu1_i386.deb

```

---

### Post by beerjen on 2007-09-17
I was able to install 7.04 with the vesa driver. It boots but not with the max resolution. And I still get the bcm43xx error message while installing the system updates.
Wireless doesn't work neither.
Sound didn't work at first but I installed the alsa drivers, utils,... and then it worked but the sound sucks. 

Still a lot of things to fix.. but it works..

Bert

---

### Post by uzerzero on 2007-09-17
I don't have personal experience with Acer laptops running Ubuntu (I do with them running XP, and have hated them for it)

However, one major problem with laptops booting LiveCDs is the ACPI settings conflict with Ubuntu. Try booting with acpi=off and noapic, you might have better luck. Also try adding the live command to the LiveCD bootloader. 

Beerjen: try ```
sudo apt-get remove bcm43xx-fwcutter bcm43xx
``` to stop the updates from trying to install bcm43xx. As for sound, try the OSS sound drivers and the Xine backend. And using the restricted drivers might give you full resolution.

---

### Post by panosg77 on 2007-09-18
Works fine with Gutsy Gibbon. I have managed to configure the following:

(1) Graphics by using the "Restricted Drivers" option (System --> Administration --> Restricted Drivers Management. The good news is that the X Windows System boots normally and the installation is flawless, considering I am using an Alpha version :)

(2) Sound with the drivers from Realtek (sound does not work out of the box). You can download the drivers directly by following [this link]("ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2").

(3) Bluetooth works.

And the following is what I haven't managed to configure yet:

(1) Wireless (does not seem to work at all using madwifi and/or ndiswrapper). Any advice would be appreciated. Most probably the specific Wireless card is not supported yet (the Hardware Abstraction Layer or HAL, reports that the wireless card is of unsupported architecture).[/html] **Got it working. See next post.**

Some folks managed to get that same card working. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=212600&page=3").

(2)ACPI works but partially. Suspend to RAM does not work (screen does not wake up).

What I haven't checked yet:

(1) 4-in-1 card reader (maker Ricoh)

(2) Screen mirroring. I suspect it will work fine since I am using the NVidia drivers.

cat /proc/cpuinfo reports:

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1601.80
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1601.80
clflush size    : 64

```

---

### Post by beerjen on 2007-09-18
Sound is working for me with the alsa drivers.
Ik got the display working through ENVY, manual installation of NVIDIA drivers
Wireless: nothing


And what about the webcam? That doesn't work.

Bert

---

### Post by panosg77 on 2007-09-18
I got wireless working a few minutes ago with ndiswrapper. No luck with madwifi. 

First, I disabled the Hardware Abstraction Layer module by Atheros and then downloaded the XP drivers for the wireless card and used ndiswrapper.

Seems to work fine right now. You can find the XP drivers from Atheros:

[http://www.atheros.cz/download.php?atheros=AR5006EG&system=1](http://www.atheros.cz/download.php?atheros=AR5006EG&system=1)

The page is in Czech but all you have to do is press the "Download" button. Thank God that's in English :)

As far as ndiswrapper is concerned I used Synaptic to install ndiswrapper as well as the frontend (GUI) utility, installed the corresponding *.inf file from the package provided and got it working after a reboot.

At least it works :)

As for the webcam, I really don't know yet. :-/

---

### Post by tombott on 2007-09-18
> **panosg77 said:**
> Works fine with Gutsy Gibbon. I have managed to configure the following:

(1) Graphics by using the "Restricted Drivers" option (System --> Administration --> Restricted Drivers Management. The good news is that the X Windows System boots normally and the installation is flawless, considering I am using an Alpha version :)

(2) Sound with the drivers from Realtek (sound does not work out of the box). You can download the drivers directly by following [this link]("ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2").

(3) Bluetooth works.

And the following is what I haven't managed to configure yet:

(1) Wireless (does not seem to work at all using madwifi and/or ndiswrapper). Any advice would be appreciated. Most probably the specific Wireless card is not supported yet (the Hardware Abstraction Layer or HAL, reports that the wireless card is of unsupported architecture).[/html] **Got it working. See next post.**

Some folks managed to get that same card working. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=212600&page=3").

(2)ACPI works but partially. Suspend to RAM does not work (screen does not wake up).

What I haven't checked yet:

(1) 4-in-1 card reader (maker Ricoh)

(2) Screen mirroring. I suspect it will work fine since I am using the NVidia drivers.

cat /proc/cpuinfo reports:

```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1601.80
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-60
stepping        : 2
cpu MHz         : 800.000
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8legacy ts fid vid ttp tm stc
bogomips        : 1601.80
clflush size    : 64

```

It's nice to hear that progress is being made with Gutsy!
I run Feisty on my Acer Aspire 9500 with no problems but haven't been able to get the Gutsy Live CD to work.

---

### Post by panosg77 on 2007-09-18
> **tombott said:**
> It's nice to hear that progress is being made with Gutsy!
I run Feisty on my Acer Aspire 9500 with no problems but haven't been able to get the Gutsy Live CD to work.

Well it took me some sleepless nights to work my way around Gutsy's bugs (let's not forget that it's still Alpha) and I have to say that I at least managed to configure some of the Aspire's devices. 

Right now I have given up on Gutsy, at least temporarily, in favour of Feisty. I haven't installed it yet, but I will do so :)

All I can say however is that Gutsy Gibbon will be a great release and I believe that by the time it reaches code-freeze you will be able to load it off of the Live CD ;)

BTW, why doesn't it boot with the Tribe 5 CD on your Aspire?

---

### Post by my_linux on 2007-09-18
> **panosg77 said:**
> I got wireless working a few minutes ago with ndiswrapper. No luck with madwifi. 

First, I disabled the Hardware Abstraction Layer module by Atheros and then downloaded the XP drivers for the wireless card and used ndiswrapper.



Hi,

can you please confirm what you mean by the above. As I have managed to get everything working on my 7520 but the wireless.

Thanks

---

### Post by bobonaut on 2007-09-18
Helllo guys,

Actually before starting i would like to say that im new to linux and well im learning :D

I have an acer aspire 7520 and installed dual booted system here wanted to see the cool features in linux and im studying in ict at the moment so linux is a good experience but well lets get to the point

I have installed the Nvidia Drivers with Envy. Tried to install the sound drivers with that file you can find in this thread idk it doesnt work i think i made a mistake and the wireless card is still a problem to me cause i installed the ndiswrapper and it didnt work so just to ask where do i place the xp drivers to install and could you please place a more clear install prosedure :D i would be happy :P and about the sound drivers 

thanks in advance :D

---

### Post by tombott on 2007-09-18
> **panosg77 said:**
> Well it took me some sleepless nights to work my way around Gutsy's bugs (let's not forget that it's still Alpha) and I have to say that I at least managed to configure some of the Aspire's devices. 

Right now I have given up on Gutsy, at least temporarily, in favour of Feisty. I haven't installed it yet, but I will do so :)

All I can say however is that Gutsy Gibbon will be a great release and I believe that by the time it reaches code-freeze you will be able to load it off of the Live CD ;)

BTW, why doesn't it boot with the Tribe 5 CD on your Aspire?

From all I have read about Gutsy so far I am really looking forward to this release.
I think in many ways it will be the Feisty that some people where expecting.

The last build I tried was Tribe 3 and it just locked up my laptop and another 2 pc's.
I downloaded the ISO and tried with an ISO that came with Linux Format magazine.
Very odd, but will wait with baited breath for the 18th of October!

---

### Post by panosg77 on 2007-09-18
> **my_linux said:**
> Hi,

can you please confirm what you mean by the above. As I have managed to get everything working on my 7520 but the wireless.

Thanks

As I wrote I had no luck with madwifi. To disable the Atheros HAL go to:

System --> Administration -->Restricted Drivers Management and click the "Enabled" box to un-tick (deselect) the driver.

Then you have to go to the Synaptic Package Manager and install ndiswrapper. What I did was to install the following packages:

ndiswrapper-common

ndisgtk

ndiswrapper-utils-1.9

After installing these packages, go to the Atheros site and download Atheros's Windows drivers. Unzip the package and install the *.inf driver via System -->Administration -->Windows Wireless drivers. Upon reboot your wireless card will work.

Warning: Using ndiswrapper will slow down your system during boot and you will be presented with the following lines so don't panic:

```
Kinit: name_to_dev_t(/dev/disk/by-uuid/3c7a8f65-b709-494a-92f1-318a38220def)= sda5(8,5)
kinit: No resume image, doing normal boot
```

if the system pauses hit Ctrl+Alt+Del. Don't worry it won't restart the system :D

You can find the fix at the following thread but beware. It disables the wireless card :( If you absolutely need to use wireless then you should go for ndiswrapper until the next version of madwifi.

---

### Post by panosg77 on 2007-09-18
> **bobonaut said:**
> Helllo guys,

Actually before starting i would like to say that im new to linux and well im learning :D

I have an acer aspire 7520 and installed dual booted system here wanted to see the cool features in linux and im studying in ict at the moment so linux is a good experience but well lets get to the point

I have installed the Nvidia Drivers with Envy. Tried to install the sound drivers with that file you can find in this thread idk it doesnt work i think i made a mistake and the wireless card is still a problem to me cause i installed the ndiswrapper and it didnt work so just to ask where do i place the xp drivers to install and could you please place a more clear install prosedure :D i would be happy :P and about the sound drivers 

thanks in advance :D

Regarding the wireless card see my post above.

As for the sound, all you have to do is download the drivers from Realtek or the latest Alsa ones. I opted for the first option. You may find the drivers at:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Direct download link:

[ftp://209.216.61.149/pc/audio/realtek-linux-audiopack-4.06b.tar.bz2](ftp://209.216.61.149/pc/audio/realtek-linux-audiopack-4.06b.tar.bz2)

Download the package to a folder of your choice, untar it, cd to that folder and type:

```
sudo ./install
```

Upon reboot you will have sound :D

If you need more detailed instructions, I'd be happy to help.

---

### Post by panosg77 on 2007-09-18
> **tombott said:**
> From all I have read about Gutsy so far I am really looking forward to this release.
I think in many ways it will be the Feisty that some people where expecting.

The last build I tried was Tribe 3 and it just locked up my laptop and another 2 pc's.
I downloaded the ISO and tried with an ISO that came with Linux Format magazine.
Very odd, but will wait with baited breath for the 18th of October!

Yep, it will be a great release :D Right now it is still unstable, but certainly more stable than Windows :D

---

### Post by bobonaut on 2007-09-18
hmm weird i installed the audio driver but still have no sound is there a way to uninstall it and install it again ?? :S and the pc says no wireless card fount with the ndis program when i accept the xp *.inf file 

maybe its my ubuntu version is there a recommended one that i should use ??

---

### Post by panosg77 on 2007-09-19
That's weird. Which version are you using? Remember that gutsy gibbon is still unstable and should not be used in production machines.

---

### Post by Digz on 2007-09-20
Would people mind if i ask a question thats off topic about the Acer Aspire 7520 as i'm thinking of buying one.

---

### Post by Digz on 2007-09-20
on the Acer 7520 Does the WiFi button on the Easy-launch strip physically and permanently turn off the WiFi or does just it just disable it via windows control panel ?

Thanks

---

### Post by bobonaut on 2007-09-21
Im using Feisty Fawn but i think ill wait till the gutsy gibbon is out cause when i tried the live cd it took the nvidia grafics perfectly :D

---

### Post by panosg77 on 2007-09-21
> **bobonaut said:**
> Im using Feisty Fawn but i think ill wait till the gutsy gibbon is out cause when i tried the live cd it took the nvidia grafics perfectly :D

Gutsy Gibbon will support the NVidia chipset out of the box indeed :) If you can wait then I would advise you to do so. You will still have to set up the sound in Gutsy Gibbon as well since as of the time of writing it doesn't work. 

I will write a complete how-to about installing Feisty Fawn on the Acer 7520G at [my site]("http://support-freesoftware.org") during the weekend most probably ;)

---

### Post by panosg77 on 2007-09-22
Well now I installed Feisty and I don't have wireless! No matter how hard I've tried by installing ndiswrapper, madwifi etc and after having used every single trick in the book, I admit that I am stumped :confused:

Is there anyone out there with an Acer Aspire 7520G with an Atheros ar5bxb63 wireless card that has managed to get wireless working with Ubuntu Feisty?! I've searched the forums and I've been googling it up for 2 days. Nothing seems to work! Any help would be much appreciated.

---

### Post by beerjen on 2007-09-22
I to have feisty installed and no wireless. I have tried it with ndiswrapper but no succes.

---

### Post by panosg77 on 2007-09-23
To my dismay, I found out that this is a known issue:

[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

There is currently no solution. However the madwifi developers and coders are working really hard for a new HAL or ath5k release. 

*Sigh* I guess we'll have to wait too. Damn those proprietary drivers :mad:

---

### Post by Niej on 2007-10-06
Hi Peope!
Thanks for your support on this subject!
But i'm still in deep sh*t
I'm trying to install kubuntu 7.10 and I couldn't start the xserver yet.
I quite lost about this!
If anyone knows something please......HELP
Best Regard to you all
El Niej
:D)

---

### Post by panosg77 on 2007-10-06
Hello Niej,

The X Server should have started automatically. Are you sure that you are trying to install 7.10 and not 7.04? Gutsy Gibbon supports the NVidia 8400 M G chipset found in the Acer 7520G using the NVidia restricted drivers.

---

### Post by cord-factor on 2007-10-07
Hello,
I have the same laptop (Acer 7520), and under the KNOPPIX-5.1 and gentoo-live-2007 seems to be working nothing. I want to install gentoo, but gentoo-livecd-2007 don't determine network card which is important.
lspci shows:
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
:(
I am triing to: ifconfig eth0
but eth0 is the firewire...

Can you tell me module name for network card which is working? (forcedeth - don't working)
and what the kernel version?


ps Sorry for my English.

---

### Post by cord-factor on 2007-10-08
and what the kernel version of "your workin Gutsy Gibbon"?
where can I found it?

---

### Post by Niej on 2007-10-10
Hi panogs77.
actually I have a GeForce 7000M.
Using the secure graphics mode I found the restricted drivers menu, when using Kubuntu 7.10, but after checking the box on Administrator mode it doesn't work, I have no menu afterwards. 
I'm sure that I've got the 7.10 beta release for amd 64 and the xserver didn't work, it couldn't find any screen.
I'll keep looking
Thank you!!
Best Regards

---

### Post by cord-factor on 2007-10-11
> **beerjen said:**
> 
And what about the webcam? That doesn't work.

The linux driver is called linux-uvc or uvcvideo:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

**2All**, what about the ExpressCard(s)?
Is it working? How?

---

### Post by my_linux on 2007-10-16
At a command prompt try sudo dpkg-reconfigure xserver-xorg and select the Vesa driver and set resolution to 1024x768. After this use the restricted installer to install the nvidia driver and then again run sudo dpkg-reconfigure xserver-xorg and select the nvidia driver and set your screen res eg 1440x900 > reboot.

The above is based on the assumption your 7520 is the same as mine ie has a Nvidia graphics system eg 7000m.

---

### Post by cord-factor on 2007-10-17
You use Gusty Gibbon, don't you?
/me tried to install many distros (Suse-10.3, Mandriva-2008, FedoraCore7, DeepStyle...), and soundcard/modem didn't recognize anywere.
Is it really working in Gusty??? :)))))

ps What arch do you use? i386 or x86_64?

---

### Post by my_linux on 2007-10-19
7.10 RC was working ie booting and the Nvidia driver could be installed through restricted driver install.

Unfortunately sound was not working but easily corrected. As yet there is no driver for the Atheros A5700EG card but there may be workarounds using the Windows driver.

Now 7.10 release is out and I have clean installed using the Alternate CD the computer no longer boots fully. There is a stall at an IDE driver and after a while Ubuntu goes to Busybox.

---

### Post by beerjen on 2007-10-19
Everything I want is working now under 7.04. I've been thinking about upgrading to gutsy but I'm going to wait. I'm afraid I'm going to loose my sound, my x config, ... 
The gutsy desktop CD doesn't wotk for me so I don't think a clean install will work either. 

If somebody with the same laptop has done a successful update then maybe I'll consider it. 

Greets
Bert

---

### Post by El Zoido on 2007-10-19
I recently installed Gutsy (earlier distros didn't work) on a friends Aspire 7520G.
Unfortunatly the sound isn`t working.
I tried installing the drivers found in the link yesterday but after starting the installation procedure with "sudo sh install" there are a couple of errors regarding the c compiler.
After restart Ubuntu didn't start the x-server correctly,instead it did quit directly after login.
There was just an error message about the session quitting after less than 10 seconds and thats it.
Being not very experienced we reinstalled Ubuntu (was a fresh install anyway).
Any ideas about what happened?

Furthermore somehow the network settings keep changing. Everytime I configure the DSL connection it works until the next restart, then I have to do it again.
Strange thing is, the settings for the adaptor itself, like IP-configuration (and for the provider) are still there, but the name of the ethernet device seems to change, e.g. from eth1 to eth2 and so on...
This error happened with openSuse as well.

---

### Post by Digz on 2007-10-22
I just bought the Aspire 7520 but when i have a all black screen there is a white haze across the bottom half of the screen being brightest at the bottom and fading away towards the centre , Is it supposed to be like that or have i got a faulty one ?

---

### Post by Niej on 2007-10-23
I'm having the same problem, after installing the 7.10 release, it gets stuck, it doesn't  boot. :(

---

### Post by Digz on 2007-10-25
Anybody else got light bleed across the bottom half of the screen when on a all black screen ?

---

### Post by Digz on 2007-10-29
Can nobody answer my question ?

---

### Post by Digz on 2007-10-31
Can Anybody answer my question as i'm unsure if i need to send my laptop back.

a Black screen for me is more like a dark grey with a white sheen and it doesn't change very much when i turn the brightness down and i'm unsure if it's supposed to be like that being my first laptop.

---

### Post by Niej on 2007-10-31
Halelluya brother!!!
Yes, I have ubunu 7.10 running on my aspire 7520 (nvidia 7000M)!!!!!
Althought it isn't a fully functional installation, because  sometimes it doesn't boot, it is working  now.
Thanks to everybody who helped me out!
Now I can do my job!!
Best Regards

---

### Post by Digz on 2007-11-01
I've just bought an Acer Aspire 7520 Gemstone

When the Laptop is at waist height on your lap or on a table top so your looking slighty down at and angle i have a white haze /sheen across the screen on black backgrounds that looks like light bleed but it doesn't change very much if i turn down the brightness , But if i lift the laptop up to chest height so i'm looking straight into the screen 90% of the white haze / sheen can no longer be seen and the screen looks perfectly black so it seems like it's an optical effect of the way the light is polarized at angles.

does it sound like a fault or are your 7520 the same. ?

---

### Post by mike sumner on 2007-11-02
Hi Guys, I am just about to order a 7520 to replace my dell 6400 which is running gutsy perfectly.  I was just wondering if the gutsy final will now work out of the box or will I have to tweak stuff?  Will it make any difference if I use the 32 or 64 bit version?
Mike

---

### Post by bobbyshafter on 2007-11-02
My Acer Aspire 5570Z works fine with gusty .I had to install kmix to get sound to work.

---

### Post by cord-factor on 2007-11-09
I installed latest alsa-driver (1.0.15) and added the line
*options snd-hda-intel model=acer*
to the bottom of /etc/modprobe.d/alsa-base

Sound doesn't work :(

---

### Post by cord-factor on 2007-11-09
> **cord-factor said:**
> I installed latest alsa-driver (1.0.15) and added the line
*options snd-hda-intel model=acer*
to the bottom of /etc/modprobe.d/alsa-base

Sound doesn't work :(
solved :)

---

### Post by tombott on 2007-11-09
> **cord-factor said:**
> solved :)

Nice result.
Spill the beans then, how did you fix it?
I don't have a 7520 but I am sure your experience in getting this working will help others.

---

### Post by alip on 2007-11-10
hey.... why  acer  aspire 3680  can't  enable  desktop  effect...???

---

### Post by cord-factor on 2007-11-11
> **tombott said:**
> Nice result.
Spill the beans then, how did you fix it?
I don't have a 7520 but I am sure your experience in getting this working will help others.
I use Gentoo. Sound work's for me with alsa-driver-1.0.15 (ALSA_CARDS="hda-intel")

---

### Post by cord-factor on 2007-11-15
2**ALL**, could you show yours #glxgears?
my GeForce 7000M gives out ~1500fps
Is it normal?

---

### Post by tingusa on 2007-11-15
I have been running Ubuntu Studio (Gutsy) for two weeks with very few problems -mostly related to my latter mistake in installing the KDE desktop which does not run well alongside the provided Gnome desktop).  Wireless, NVIDIA card, display resolution, wireless, etc, worked perfectly from the first moment. It is extremely well thought out.

Ubuntu Studio also gives you the choice to not install the multimedia applications.  The Gnome desktop is as friendly and smooth as a Mac, and installing applications via the web is easier than in Windows or Mac.  However, Acer should make it much easier for Linux users... and they would sell more machines...

The Grub (startup loader) works perfectly and gives you the choice to boot on any other operating systems that you may have on your machine.  I tried another five flavours of Linux and nothing compares to this, particularly the installation process (however, when prompted to give your network IP, etc., tell the installer that you will give the details later... or you might never finish the install...)

[www.ubuntustudio.org](www.ubuntustudio.org)

running on Aspire 9423 WSMi

---

### Post by daniel_v83 on 2007-11-26
Hi!

I just cant make the wifi work, 

does anyone know how???

the windows driver solution didn't work...

thanks for your help.

---

### Post by takaratiki on 2007-12-02
I've just finished up configuring my new Acer 7520 (only took a week!). I found that following the instructions linked from the Madwifi compatibility page fixed my wifi problems in short order. [http://docs.google.com/View?docid=dtvgpkz_46fv8dwf](http://docs.google.com/View?docid=dtvgpkz_46fv8dwf)


I've disabled the Atheros HAL driver in System->Admin->Restricted Drivers and am running Ndiswrapper 1.50. My Aspire model is a 7520-5311.

---

### Post by Lapiz on 2007-12-02
> **panosg77 said:**
> Regarding the wireless card see my post above.

As for the sound, all you have to do is download the drivers from Realtek or the latest Alsa ones. I opted for the first option. You may find the drivers at:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Direct download link:

[ftp://209.216.61.149/pc/audio/realtek-linux-audiopack-4.06b.tar.bz2](ftp://209.216.61.149/pc/audio/realtek-linux-audiopack-4.06b.tar.bz2)

Download the package to a folder of your choice, untar it, cd to that folder and type:

```
sudo ./install
```

Upon reboot you will have sound :D

If you need more detailed instructions, I'd be happy to help.

I've done so and everything installes fine, but when i try to execute alsamixer it says ```
alsamixer: function snd_ctl_open failed for default: No such device

```
I've searched out that tool "snddevices" from ALSA can help me, but it seems that i don't have it ```
lapiz@hi:~$ sudo find / -name snddevices
lapiz@hi:~$   
```
What should i do?

---

### Post by cord-factor on 2007-12-02
**Lapiz**,
try to install lates alsa-driver (from [http://www.alsa-project.org/](http://www.alsa-project.org/))
and then add the following line to /etc/modules.d/alsa
options snd-hda-intel model=acer


**takaratiki, Lapiz**
What videocard do you have? (8400 or 7000)
How many fps shows "glxgears"?

---

### Post by panosg77 on 2007-12-02
Hi guys.

I wish I could be of further help but I sold my Acer 7520G about a month ago for a smaller and cheaper Packard Bell BU45 which runs Ubuntu 7.10 flawlessly. Not the best or most trustworthy laptop in the world but hey, everything works and the price was really tempting.

In any case, I'm really sorry that I can't be of more help. As far as I remember and after looking at my notes, my most serious issue was the lack of wi-fi. I had managed to get it working with ndiswarapper though by using the x32 drivers.

---

### Post by Lapiz on 2007-12-02
> **cord-factor said:**
> **Lapiz**,
try to install lates alsa-driver (from [http://www.alsa-project.org/](http://www.alsa-project.org/))
and then add the following line to /etc/modules.d/alsa
options snd-hda-intel model=acer


**takaratiki, Lapiz**
What videocard do you have? (8400 or 7000)
How many fps shows "glxgears"?
I don't have /etc/modules.d dir :confused: . I have /etc/modprobe.d, but there is no "alsa", only "alsa-base", a if i add this string there it changes nothing.



8400:
4320 frames in 5.1 seconds = 848.948 FPS
4320 frames in 5.1 seconds = 849.418 FPS
4320 frames in 5.1 seconds = 847.842 FPS
But i don't shure if driver are work properly =D.

---

### Post by takaratiki on 2007-12-03
I have an 8400 as well, fps as follows:

12165 frames in 5.0 seconds = 2432.953 FPS
12709 frames in 5.0 seconds = 2541.642 FPS
12728 frames in 5.0 seconds = 2545.508 FPS

For what is worth, I couldn't get the audio drivers listed above working at all due to build errors and Realtek's drivers nuking my libasound. Ended up simply using this mentioned by Skweek on a different post:

sudo apt-get install linux-backports-modules-generic

Presto, sound was up on the next reboot.

---

### Post by baxterdog on 2007-12-03
I'm running an Acer Laptop with no problems with 7.10. Had to add surround to get the sound working, but that's it.

---

### Post by Lapiz on 2007-12-03
> **takaratiki said:**
> Ended up simply using this mentioned by Skweek on a different post:
sudo apt-get install linux-backports-modules-generic
Presto, sound was up on the next reboot.
Suddenly, it've helped me too  :) .

---

### Post by cord-factor on 2007-12-03
> **panosg77 said:**
> As far as I remember and after looking at my notes, my most serious issue was the lack of wi-fi. I had managed to get it working with ndiswarapper though by using the x32 drivers.
My system is x86_64
And I have this::
```

localhost # ndiswrapper -l
net5211 : driver installed
        device (168C:001C) present

localhost # iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

localhost # dmesg | grep wlan0
Device driver wlan0 lacks bus and class support for being resumed.
wlan0: ethernet device 00:1c:26:35:f7:bf using serialized NDIS driver: net5211, version: 0x50003, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:001C.5.conf
wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

```
But works it or not i don't know because there are no wifi net around me...

> **Lapiz said:**
> 
8400:
4320 frames in 5.1 seconds = 848.948 FPS
4320 frames in 5.1 seconds = 849.418 FPS
4320 frames in 5.1 seconds = 847.842 FPS
But i don't shure if driver are work properly =D.
show please
$ glxinfo | grep direct

* * * * *
Recently I tried Ubuntu-7.10-x64 Live-CD and sound worked for me by default with acpi=off kernel option.

* * * * *
Does anybody check the "ExpressCard" slot? (i don't have any card of this type)

---

### Post by Lapiz on 2007-12-03
> **cord-factor said:**
> My system is x86_64
show please
$ glxinfo | grep direct

```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
```
As i thought. I'll fix it, but furst  need wifi.



I installes ndiswrapper, but it saying ```
lapiz@hi:~$ sudo ndiswrapper -m
module configuration already contains alias directive

``` And there is nothing about it in dmesg.

---

### Post by cord-factor on 2007-12-04
> **Lapiz said:**
> 
As i thought. I'll fix it, but furst  need wifi..
try latest nvidia driver...

> I installes ndiswrapper, but it saying
show this:
$ lspci && lspci -n
and
$ sudo ndiswrapper -l

---

### Post by Lapiz on 2007-12-04
> **cord-factor said:**
> try latest nvidia driver...


show this:
$ lspci && lspci -n
and
$ sudo ndiswrapper -l
Installed nvidia drivers. Now it's ok.
```
14473 frames in 5.0 seconds = 2894.419 FPS
14803 frames in 5.0 seconds = 2960.439 FPS
14803 frames in 5.0 seconds = 2960.420 FPS
```


```
lapiz@hi:~$ lspci && lspci -n
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0562 (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
00:00.0 0500: 10de:0547 (rev a2)
00:01.0 0601: 10de:0548 (rev a2)
00:01.1 0c05: 10de:0542 (rev a2)
00:01.2 0500: 10de:0541 (rev a2)
00:01.3 0b40: 10de:0543 (rev a2)
00:02.0 0c03: 10de:055e (rev a2)
00:02.1 0c03: 10de:055f (rev a2)
00:04.0 0c03: 10de:055e (rev a2)
00:04.1 0c03: 10de:055f (rev a2)
00:06.0 0101: 10de:0560 (rev a1)
00:07.0 0403: 10de:055c (rev a1)
00:08.0 0604: 10de:0561 (rev a2)
00:09.0 0101: 10de:0550 (rev a2)
00:0a.0 0200: 10de:054c (rev a2)
00:0b.0 0604: 10de:0562 (rev a2)
00:0c.0 0604: 10de:0563 (rev a2)
00:0d.0 0604: 10de:0563 (rev a2)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:04.0 0c00: 1180:0832 (rev 05)
01:04.1 0805: 1180:0822 (rev 22)
01:04.2 0880: 1180:0843 (rev 12)
01:04.3 0880: 1180:0592 (rev 12)
01:04.4 0880: 1180:0852 (rev 12)
02:00.0 0300: 10de:0428 (rev a1)
05:00.0 0200: 168c:001c (rev 01)
lapiz@hi:~$ sudo ndiswrapper -l
[sudo] password for lapiz:
net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
         
```

---

### Post by cord-factor on 2007-12-04
It seems to be ok...
and what's about
$ iwconfig wlan0
and
$ dmesg | grep wlan0
?

---

### Post by Lapiz on 2007-12-05
```
lapiz@hi:~$ iwconfig wlan0
wlan0     No such device

lapiz@hi:~$ dmesg | grep wlan0

```



Network card seems to change her name on every startup =O. And somehow it takes random ip from DCHP on router, but it has to be fixed as it is tied to MAC, in Win it retrieves IP correctly. Can it be helped?

---

### Post by cord-factor on 2007-12-05
> **Lapiz said:**
> ```
lapiz@hi:~$ iwconfig wlan0
wlan0     No such device

lapiz@hi:~$ dmesg | grep wlan0

```

:confused:
$ sudo modprobe ndiswrapper

> **Lapiz said:**
> 
Network card seems to change her name on every startup =O. And somehow it takes random ip from DCHP on router, but it has to be fixed as it is tied to MAC, in Win it retrieves IP correctly. Can it be helped?
[_this_]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")?

---

### Post by Lapiz on 2007-12-05
> **cord-factor said:**
> :confused:
$ sudo modprobe ndiswrapper


[_this_]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/153727")?
Yes! Wi-Fi adapter is now detected. Thank you so much.

That's it, and there is a solution, thank you once more =).

---

### Post by daniel_v83 on 2007-12-05
i have the 7520-5626 with ubuntu 7.10 and i cant fix the wifi,

i have the atheros...

does anyone know how??? the windows drivers dont work for me. =/

thanks for your help

---

### Post by Lapiz on 2007-12-05
Is there any way to use ndiswrapper + WPA-PSK ? 
I've tried this manual : [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/")

but it starting to do something endless and i've to break it with ^C.
```
lapiz@hi:~$ sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=6):
     76 6f 72 74 65 78                                 vortex
PSK (ASCII passphrase) - hexdump_ascii(len=8): [REMOVED]
key_mgmt: 0x2
proto: 0x1
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='vortex'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:00:00:00:00:00
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 919 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:fc:91:7d:e0 ssid='vortex'
Try to find non-WPA AP
Trying to associate with 00:1b:fc:91:7d:e0 (SSID='vortex' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=22
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:1b:fc:91:7d:e0 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 919 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:fc:91:7d:e0 ssid='vortex'
Try to find non-WPA AP
Trying to associate with 00:1b:fc:91:7d:e0 (SSID='vortex' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=22
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:1b:fc:91:7d:e0 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 919 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   skip - blacklisted
1: 00:17:9a:f2:72:77 ssid='LINK' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:13:49:c9:b7:29 ssid='ZyXEL-8408' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   skip - blacklisted
1: 00:17:9a:f2:72:77 ssid='LINK' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:13:49:c9:b7:29 ssid='ZyXEL-8408' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:1b:fc:91:7d:e0 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:fc:91:7d:e0 ssid='vortex'
Try to find non-WPA AP
Trying to associate with 00:1b:fc:91:7d:e0 (SSID='vortex' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=22
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:1b:fc:91:7d:e0 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
Scan timeout - try to get results
Received 919 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1b:fc:91:7d:e0 ssid='vortex' wpa_ie_len=26 rsn_ie_len=22 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1b:fc:91:7d:e0 ssid='vortex'
Try to find non-WPA AP
Trying to associate with 00:1b:fc:91:7d:e0 (SSID='vortex' freq=2412 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: set AP RSN IE - hexdump(len=22): 30 14 01 00 00 0f ac 02 01 00 00 0f ac 02 01 00 00 0f ac 02 00 00
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RSN: Ignored PMKID candidate without preauth flag
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=22
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Removed BSSID 00:1b:fc:91:7d:e0 from blacklist (clear)
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6

```
I just can't understand what's going wrong.

---

### Post by FedeXX on 2007-12-09
Hi guys, I've got the sound working too by adding the line in the alsa-base file....but what about the acer subwoofer? I've got it working in Vista by replacing the installed driver with the realtek one (i wonder if Acer knows that the 7520 series mounts a subwoofer...) but audio still sucks in Linux withous bass enhancement...Any ideas? :guitar:

---

### Post by cord-factor on 2007-12-10
> **FedeXX said:**
> Hi guys, I've got the sound working too by adding the line in the alsa-base file....but what about the acer subwoofer? I've got it working in Vista by replacing the installed driver with the realtek one (i wonder if Acer knows that the 7520 series mounts a subwoofer...) but audio still sucks in Linux withous bass enhancement...Any ideas? :guitar:
good question :-k

---

### Post by Kenzy88 on 2007-12-11
Hi all... i'm trying to install ubuntu on this laptop (well... it's not mine... it's of a friend of mine :P ). I got wifi working with ndiswrapper and sound working with what i read in this forum but i have still a problem. Since when i first installed ubuntu i got some problem on boot. Sometimes on boot it freeze whit  the hard disk writing led saying:
Uniform CD-ROM driver Revision: 3.20
the only thing i can do is pressing ctrl+alt+del and reboot
I don't know if this message is the real problem... i think it's something he do after... anyway....
i tried reading the log and ended up discovering that the kernel doesn't write it when freezeing... i really doesn't have any idea on how to solve this.... any help???

P.S.: this problem it's not related to ndiswrapper or audio because it freeze also after a clean intstall

P.P.S.: i haven't tried compiling the latest kernel yet.

---

### Post by User-007 on 2007-12-14
Hi all 7520 users!!!

Have you succeeded using internet via ethernet connection? My ethernet connection fails.

See thread [http://ubuntuforums.org/showthread.php?t=638811&highlight=7520](http://ubuntuforums.org/showthread.php?t=638811&highlight=7520)

Thx
User JB

---

### Post by cord-factor on 2007-12-16
I don't sure...
Try to rebuild your kernel (>=2.6.20) and add the "forcedeth" not as module.

---

### Post by foppeh on 2007-12-22
How do I do the webcam? That&#347; the last thing I need. It's got uvcvideo driver running, but a program like Cheese says it can find a cam.

For the rest I have it all (screen, audio, wifi, sleep) except bluetooth and cardreader not tested. So if some one needs a hint, please reply (again). I'll try to write a HOWTO, but that&#347; probably not before next year. :)

---

### Post by beerjen on 2007-12-22
how did you do the screen and sound? Today I finaly updated to gutsy and nothing worked afterwards. I've been trying for hours now and still nothing. damn, it's frustrating

Thanks,

Bert

---

### Post by foppeh on 2007-12-22
Screen is the NVidea restricted driver. You found that one I guess. Now go to settings -> Screen and search for the 1440x900 widescreen. Tick the checkbox for widescreen. Go to System -> Preferences -> Screen resolution, and tick the 'Use on this computer' tickbox (I translated back from my Dutch ubuntu, so the English version may be slightly different.)
Sound, go to Synaptic, install Backport (linux-backports-modules)

Reboot and enjoy

---

### Post by cord-factor on 2007-12-23
Audio works with [subwoofer]("http://ubuntuforums.org/showpost.php?p=3919710&postcount=75")?

---

### Post by foppeh on 2007-12-23
Well I have this problem, I do not know when if the subwoofer works or not. I recently downloaded the new driver for my Vista and the sound improved, especially the volume. I have a similar experience with this Ubuntu driver, but it&#347; not like a subwoofer experience. Both sidespeakers are 1.5 Watt, the subwoofer is 3 Watt, I don expect more than what I have now.

Perhaps you can tell me what to expect (name a song ...) and I'll compare Vista with Ubuntu.

---

### Post by Lapiz on 2007-12-23
If you write a completely manula for Wi-Fi it would very-very nice. I weren't able to make it working though i've made wifi card detectable.

---

### Post by foppeh on 2007-12-23
I keep it short here but I'll write an extensive HOWTO lateron.
1) Disable / rermove ndiswrapper
2) Download: [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
This is Madwifi with the driver for AR5007EG patched
3) Follow this manual: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
Do not download the packet as suggested there, but use the one I mentioned in 2)
I ran into two issues. First where it says
```
./madwifi-unload.bash
```
do
```
./madwifi-unload
```
Second more serious. I couldn't compile and got errors.It turned out (this took me two days) that C++ is not installed.So fire up Synaptic and search for G++. With that package installed it should work fine.

One thing to remember. When you installed ndiswrapper you needed to disable madfiwi and some components. I think installing again brings them back, but there maybe traces of the removal left in the blacklist. That's located here: /etc/modprobe.d/blacklist
A fresh install of Ubuntu before you start should prvent issues here.

Good luck

---

### Post by cord-factor on 2007-12-23
> This is Madwifi with the driver for AR5007EG patched

...this driver is only for 32bit

---

### Post by foppeh on 2007-12-23
> **cord-factor said:**
> ...this driver is only for 32bit
Yes
For the 64 bit driver you are confined to ndiswrapper. I never got that working. Perhaps you have more luck.

---

### Post by cdi3d on 2007-12-23
Hi folks,

Got my sound working thanks to the back ports download and got the wifi working thanks to ndiswrapper. 
I have only one problem now. 

Whenever I reboot I have to retype the sudo modprobe ndiswrapper in order for the wifi to pick up a connection. Is there a way to make this happen whenever I boot rather than having me type it?

---

### Post by foppeh on 2007-12-24
> **cdi3d said:**
> Hi folks,

Got my sound working thanks to the back ports download and got the wifi working thanks to ndiswrapper. 
I have only one problem now. 

Whenever I reboot I have to retype the sudo modprobe ndiswrapper in order for the wifi to pick up a connection. Is there a way to make this happen whenever I boot rather than having me type it?
Search ther forum or Google for "startup script".

How did you get ndiswrapper working? I got it so far it the driver was installed, but I couldn't make the step to use it. The advised WCID didn' t see any wireless to connect to, Network Manager didn't show any wireless. Wifiradar nothing either.

It' s similar to my webcam problem: the driver is there, but no show. Cheese says no camera detected.

---

### Post by cord-factor on 2007-12-24
Ndiswrapper (+ XP-64bits drivers) is working on my Gentoo 64bits. See how-to at ndiswrapper homepage.

Webcam is working too. You need linux-uvc driver (version 141)

---

### Post by Lapiz on 2007-12-24
> **foppeh said:**
> I keep it short here but I'll write an extensive HOWTO lateron.
1) Disable / rermove ndiswrapper
2) Download: [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
This is Madwifi with the driver for AR5007EG patched
3) Follow this manual: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
Do not download the packet as suggested there, but use the one I mentioned in 2)
I ran into two issues. First where it says
```
./madwifi-unload.bash
```
do
```
./madwifi-unload
```
Second more serious. I couldn't compile and got errors.It turned out (this took me two days) that C++ is not installed.So fire up Synaptic and search for G++. With that package installed it should work fine.

One thing to remember. When you installed ndiswrapper you needed to disable madfiwi and some components. I think installing again brings them back, but there maybe traces of the removal left in the blacklist. That's located here: /etc/modprobe.d/blacklist
A fresh install of Ubuntu before you start should prvent issues here.

Good luck
Thank you a lot, wifi is finally working. The only thing i have to type ```
lapiz@hi:~$ modprobe ath_pci
lapiz@hi:~$ sudo iwconfig ath0 essid vortex
lapiz@hi:~$ sudo ifconfig ath0 up
lapiz@hi:~$ sudo wpa_supplicant -Bw -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf
lapiz@hi:~$ sudo /etc/init.d/networking restart

```
to get network working. I can add this to Autostart, but i suppose there is a much more correct solution.


Suddenly, another problem. In Windows there is no such loss, where should i dig?
```
--- my.router ping statistics ---
36 packets transmitted, 23 received, 36% packet loss, time 35058ms
rtt min/avg/max/mdev = 0.593/0.701/1.698/0.216 ms 
```

---

### Post by foppeh on 2007-12-24
Hi Lapiz,

Nice job, Can you try hitting the network button in the upper tray or using the network manager from System. The wireless is always available for me,

I had this problem: goto Network manager (under system) and hit the DNS tab for the wireless. There it had the 192.168.x.x (local network) as first DNS server. Of course that doesn't resolve names for internet and this resulted in poor performance (slow internet). I didn 't have a look at the packet loss, but it may (or may not) be the same issue.

---

### Post by FedeXX on 2008-01-03
Still no workarounds to have the subwoofer working? And what about the mmc reader?:confused:

---

### Post by z1nkum on 2008-01-06
> **FedeXX said:**
>  And what about the mmc reader?:confused:
sdhci + mmc-block

---

### Post by FedeXX on 2008-01-09
> **z1nkum said:**
> sdhci + mmc-block

Seems not to be so easy :p Dmesg doesn't show up anything when I insert a card, even with these modules loaded :lolflag:

---

### Post by oli888 on 2008-01-19
Anybody tried this laptop with a Hardy alpha?

---

### Post by akrus on 2008-01-20
// okay, this one resolved.

sudo modprobe ath_pci does nothing :( no WiFi detected...

---

### Post by FedeXX on 2008-01-25
> **oli888 said:**
> Anybody tried this laptop with a Hardy alpha?

I've only tried the hardy's alsa 15... No more alsa-base additional configuration is needed (audio works immediately on a fresh installation) but the subwoofer is still mute. DAAAAAAAAAAAAAAAAAAAAAAAAAAAMNNNNNNNNN!!!!!!!!!!

I need an alsa expert :)

---

### Post by suryam80 on 2008-01-25
Hi tingusa,

       I have an acer aspire 9423 wsmi with a factory installed windows vista. I have not tasted much success installing any distro of linux on this machine. So, I would be extremely grateful if you can describe in detail the processes involved in installing ubuntustudio on this machine.

Cheers.

---

### Post by User-007 on 2008-01-26
Hi!

A have problems configuring sound driver for my Aspire 7520. The output is below:

```


sudo ./install
.....Decompress Driver source v1.0.14-4.06b
.....Decompress ALSA Library source v1.0.14
.....Decompress ALSA Utility v1.0.14
Remove old sound driver
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name...
configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/oole/realtek-linux-audiopack-4.06b/alsa-driver-rt20070820'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/oole/realtek-linux-audiopack-4.06b/alsa-driver-rt20070820'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/oole/realtek-linux-audiopack-4.06b/alsa-driver-rt20070820/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
./install: 40: ./snddevices: not found
Remove old alsa library
Compile ALSA Library.....
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... no
checking for gmsgfmt... :
checking for xgettext... no
checking for msgmerge... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 102: alsaconf: not found


```

Any suggestions?

Thanks
User JB

---

### Post by ChristianDC on 2008-01-28
Try installing build-essential and the curses library.  In a terminal, type:

[B]sudo apt-get install build-essential
sudo apt-get install libncurses5-dev
[/B]

Then try installing the sound driver.  Worked for me!

---

### Post by sliding on 2008-02-03
I got my Aspire running smoothly with openSuse 10.3.
It was the only distro I tried that installed succesfully from the beginning.

I still have to do the wireless network  part, but since I do not have that at home or nearby,
I leave that for later.

Of course like in any message I found on the internet, there was a sound problem.
At first install using the Realtek Alsa driver I installed the complete package with the ./install.sh command.
That raised some errors, but after reboot sound was working.
Shortly after that, there was a kernel update I applied and after reboot  sound did not work anymore
A second unconfigured soundcard was installed.
Trying to modify resulted in a partial XServer crash It lost the background, but the panel kept working.

Re-installing the Realtek Alsa driver, but now only by compiling the driver brought back the sound after
a reboot. A few days later there was an Alsa update. same problem again.
So the latest Alsa does not support this sound card with the snd-hda-intel .
Although sound is working and sounds good over the headphone, the normal sound lacks the subwoover.
It's not enabled. ??Someone knows how to enable it???

So I decided to do a complete new install of openSuse.
This time, with the newer kernel, the installation did go better. With the 1st installation the screen
size settings had to be corrected from standard to wide screen, also after installation of the nvidia graphic driver. On booting the nvidia splash screen did not appear.
With the 2nd install, the wide screen was set correctly and after installing the nvidia driver the result was 
better then before.
Because I do suspect some specific Acer hardware or may be bios is causing these problems,I updated bios v1.05 with the latest v1.1 before that

The problem with the sound remains, it did not work upon install, but only after installing the Realtek driver
and rebooting.
A few days ago there wa another kernel and nvidia driver update. Applying these, resulted in the same sound problem. So a re-install of the Realtek driver was needed to get it back working.

So far the Aspire 7520 seems to be running perfectly, except for the sleeping modes.
Suspending to disk required a cold reboot to get it back running. I did not even try suspend to ram,
but that seems to be troublesome also.

As it works for openSuse, I guess it must be possible for other distro's  to get the Aspire 7520 working.

---

### Post by littlebigman on 2008-02-07
A friend of mine asked me to see if I could help him install the latest Ubuntu on his Acer Aspire 7520. 

There are so many posts on the subject, so I'd just like to know what the status is with:
- video (apparently, it has a NVidia GeForce 7000M)
- sound
- wifi

Bottom line: Should I go ahead, try another distro... or tell him to stay with Windows for a while?

Thank you.

---

### Post by foppeh on 2008-02-07
Hi littlebigman,

I am happy with Ubuntu, but it was a nasty job to set it up. The ACPI (Bios talking to the Operating System_ has major flaws rhat make some features like hibernate not functioning. Do have a look at my blog and decide for yourself if it's worth the troubles: [http://www.blog.hemminga.net/index.php/tutorials/?title=ubuntu-on-acer-aspire-7520](http://www.blog.hemminga.net/index.php/tutorials/?title=ubuntu-on-acer-aspire-7520)

Good luck

---

### Post by littlebigman on 2008-02-08
I'll disable ACPI, then use the AlternateCD to install, and see if a non-Ubuntu expert like me can figure out where to find what to get video + sound + wifi working.

Thanks for the howto.

---

### Post by legionzars on 2008-03-12
Hello people, I'm planning to install Ubuntu 7.10 on my Aspire 7520 but since it's got an athlon 64x2 I wonder if I should install the 64 bits version instead of the 32 bits.

I've been reading that you've managed to get almost all of the devices working but since I'm new to Ubuntu/linux I don't know if these solutions work in both 32 bits and 64 bits.

So everything comes down to What Version of Ubuntu should I install on my 7520?

Thanks in advance.

---

### Post by foppeh on 2008-03-12
Hi legionzars,

Some solutions will not work in the 64 bit version (the WIFI solution with the patch is one of them) but for nearly every problem is a second solution, often that is the one you want for a 64 bit version.
I installed 32 bit and am very pleased with it. So if you have no special need for 64 bit, I will advise you to go that way.

Good luck

---

### Post by legionzars on 2008-03-12
Thanks foppeh,

No special interest, I just was thinking that it could make the laptop go faster but I think I'll stick with the 32 bit.

Taking advantage of this post, I'm planning to dual-boot Ubuntu and Win Xp, I have already installed Xp, when I got rid of Vista and made 3 partitions of my HD, the first and the second are about 60 GB and the third one is about 10 G, so I wonder if I could use one of those (preferably the third one) to install Ubuntu and if by doing this I will need to install Xp again or it's gonna work with the one I have installed already.

---

### Post by foppeh on 2008-03-12
That sounds fine but concider this:
Ubuntu can be installed on the 10Gb, but it wants a /home partition and a /swap partition as well. The .home partition will not be accessable from XP (unless you choose fat as filesystem). So if Ubuntu is going to be important to you 60 + 10 is nice, if not, then make your XP partition larger and keep 10 + 30 (or so) for Ubuntu.

XP cannot be installed on another than the first visible partition. Ubuntu can be installed on every partition. Take great care when the installer asks on what partition it is installing. Do read a FAQ or HOWTO before you install.

Good luck

---

### Post by legionzars on 2008-03-12
Thanks, I think I'll redo the partitions with partition magic.

---

### Post by foppeh on 2008-03-12
> **legionzars said:**
> Thanks, I think I'll redo the partitions with partition magic.
Read a HOWTO or FAQ on installing. Ubuntu comes with GParted, a partition manager. You may want to enlarge the XP partition before you start. Do so with Partition Manager if you feel comfortable with it.

---

### Post by legionzars on 2008-03-13
I installed partition magic but it refused to work, so I think I'll use GParted does it work in Windows? I want to resize my partitions before installing Ubuntu.

I wanted to give Ubuntu a try last night I tried to use the Live option, I had read that sometimes it didn't work, it started and when the visual enviroment showed it sent me a message about the videocard and then sent me back to the line environment. Since I'm new to Ubuntu I didn't know the line to load the visual environment to try other things.

Some time ago I took some classes about Solaris which is unix and since Linux is very similar I wonder if you can point me to a direction or link where I can get some "instructions".

Thanks for the advice, I'll read everything on the FAQ and the HOWTO before trying to install it.

---

### Post by Twitch6000 on 2008-03-13
> **legionzars said:**
> I installed partition magic but it refused to work, so I think I'll use GParted does it work in Windows? I want to resize my partitions before installing Ubuntu.

I wanted to give Ubuntu a try last night I tried to use the Live option, I had read that sometimes it didn't work, it started and when the visual enviroment showed it sent me a message about the videocard and then sent me back to the line environment. Since I'm new to Ubuntu I didn't know the line to load the visual environment to try other things.

Some time ago I took some classes about Solaris which is unix and since Linux is very similar I wonder if you can point me to a direction or link where I can get some "instructions".

Thanks for the advice, I'll read everything on the FAQ and the HOWTO before trying to install it.

Ok I have an acer aspire 9410 so I figured I could help you out :p.Yeah Gparted is the better one to use.It seems to be more user friendly and works.Downside is the partitioning is slow =[.
I will say though with both acer's I have used and the one I own linux ubuntu 7.10 should install just fine :/.

---

### Post by legionzars on 2008-03-14
Last night I made the backup of the info, I downloaded a livecd of Gparted (because Ubuntu livecd never worked) and already gathered around 30 Gbs for Ubuntu. It was still working when I came to work, I hope it's finished when I go for lunch and tomorrow I'll install Ubuntu on it.

EDIT: I remade the partitions I managed to get 80 gigas, I created an NTFS partition of 40 Gbs hoping Windows and Ubuntu can share that partition and I left 40 Gbs for Ubuntu.

---

### Post by legionzars on 2008-03-16
Well, I have been able to install Ubuntu 7.10 sucessfully. I managed to get all of the problems you mentioned fixed.

Now my laptop has a dual-boot with Win xp, the sound, videocard, wireless and webcam are working. Thanks for the help.

---

### Post by foppeh on 2008-03-16
legionzars.

Great. Nice to hear.

Have fiun

---

### Post by legionzars on 2008-03-16
Hey Foppeh, I got a problem with the bluetooth, you got it running? if so what did you do?

Also I have read about the wireless card that you could use it with aircrack which is an application to take WEP keys down, I've been able to change the card to monitor mode but it doesn't receive no packets.

---

