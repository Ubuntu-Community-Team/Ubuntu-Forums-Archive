---
title: "Ubuntu works on Dell XPS M1710 ... almost. Help?"
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by Tristan Schmelcher on 2007-01-07
I wouldn't call myself either a Linux newbie or guru, but I recently had my last straw with Windows and decided to install Ubuntu 6.10 64-bit on a new Dell XPS M1710 laptop. Its hardware is:

Intel Core 2 Duo @ 2GHz
NVIDIA GeForce Go 7900 GS 256MB
Broadcom NetXtreme 5752 Gigabit Ethernet PCI Express
Intel PRO/Wireless 3945ABG Network Connection
Intel SigmaTel High Definition Audio Controller
BIOS rev A03

That all pretty much works right out of the box. For the wireless, I had to go a little farther and follow the (very simple) instructions here: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

(The GeForce is running on the "nv" driver right now, not the one from NVIDIA (haven't tried that yet).)

(The laptop also has a Conexant HDA D110 MDC V.92 modem which does not seem to have been recognized, but I don't care to get that working since I'm almost certainly never going to use it.)

Now for the "almost" part of my post. There are two small problems that I've been unable to resolve. (Btw, I have already tried an apt-get upgrade.)

The first issue is with the mouse. Or, more accurately, _any_ mouse, since it happens with an external mouse too. Basically, the cursor eventually "breaks". It ceases to be able to click on things (even though it can still be moved), and the cursor graphic remains unchanged no matter what I move it over. Bizarrely, the condition can be cleared by Alt+Tab'ing or Ctrl+Alt+Esc'ing. Again, this happens with both the built-in touchpad and external USB mice. It seems to be triggered by clicking too quickly, but only when clicking on an area of the screen that actually responds to clicks (e.g., menus, buttons, etc.).

The second issue is with the keyboard. When auto-repeat is enabled in System->Preferences->Keyboard, keys will occasionally repeat themselves with far less delay and greater speed than that configured. For example, when I wrote the last sentence,  the 'w' in "with" immediately repeated 6 times in the span of an eye-blink, but my auto-repeat settings are entirely sane and usually everything is fine. I tried disabling SpeedStep in the BIOS, thinking that it might be the culprit, but that has no effect. As far as I can tell, only disabling auto-repeat can make the spurious quick repeats go away, but I _want_ auto-repeat. :) I haven't yet tried an external keyboard to see what happens, but I may do so if I can get my hands on one.

If anyone can offer suggestions regarding the above two problems, I'd greatly appreciate it. Both are productivity-stoppers, and if I can't fix them then I will have to switch to something else. I may try Kubuntu in the hope that they are Gnome-related.

---

### Post by Tristan Schmelcher on 2007-01-07
For anyone interested, I also shortly discovered that suspend and closing the lid didn't work. Today I switched to Debian testing (etch) and it has none of the above problems (though setup was not as simple).

---

### Post by chevrier on 2007-01-20
either but with the notsc option, or better upgrade your kernel to the last version.  I use 2.18.6 all right.   rgds,

PS:  I am having sound problems with my xps 1710.  Anyone any ideas?

---

### Post by boldMonkey on 2007-01-31
Hi Tristan
I strongly considering getting a Dell XPS M1710. It will come with the much trumpeted Vista OS which in itself will be interesting but  I have also considered a dual boot linux system. 

Like you I'm not a linux newbie, nor am I a guru but my previous builds (fedora, mandrake and suse) have been on desktops not laptops.  Have you come across any unique problems with your ubunta install on your xps1710?

---

### Post by mac.ryan on 2007-02-03
I got my M1710 yesterday. No problems whatsoever with a standard installation of Edgy (and automatic updates). I still didn't play around much with drivers and other customisations, yet the computer is very usable already.

Be aware that the mediadirect function on this model of dell (the key that gives you an almost instant boot of an application for watching movies, pictures, etc...) interferes with GRUB quite a lot.

Because mediadirect doesn't support OOo docs and ext3 partitions, at the end I simply buldozed it and live happily without, but on some debian forum I found out people having used the NT loader to have the triple boot going.

---

### Post by wataboutbob on 2007-02-25
Hi all!
Just got my M1710 with the 512MB 7950GTX card. I've always loved my Dell XPS and when the old Gen2 gave up after one too many rugged LAN parties, it was a no brainer getting the new one. This one came with the Media Centre Edition and I tell you, that is one *bad* OS especially for gaming.

That said, I'm considering making my first plunge into linux and Ubuntu and its great reading about the almost painless installations from you all. A couple of questions though and I'd really appreciate an answer.

1) Do you feel that there is any advantage in going with the x64 Ubuntu on your laptops? I've got only 1 GB of RAM and in the Windows world, 1 GB makes no difference when using x64 OS.
2) And this one is specifically directed towards the M1710 users - can you guys work at the full native resolution, ie., 1920x1200.... I just love all that screen real-estate and will find it very difficult to use a smaller res.

right, said Fred... looking to hear from anyone.
ta ta

---

### Post by mac.ryan on 2007-02-26
> **wataboutbob said:**
> 1) Do you feel that there is any advantage in going with the x64 Ubuntu on your laptops? I've got only 1 GB of RAM and in the Windows world, 1 GB makes no difference when using x64 OS.

As far as I know the standard generic kernel (2.bla.bla.bla) will automatically recognise the Duo2 and will run in 64 bits, so it would perhaps be more tricky than beneficial to turn the 64 bits off than (but this should be confirmed by somebody more experienced than me, perhaps...)

> 2) And this one is specifically directed towards the M1710 users - can you guys work at the full native resolution, ie., 1920x1200.... I just love all that screen real-estate and will find it very difficult to use a smaller res.

It runs smoothly! (IMO more than under window$). I am playing Tremolous on full res and all graphic options up, and the FPS stays stuck at 90 all the time, even with 52 players connected...

---

### Post by wataboutbob on 2007-02-28
thanks Ryan for the input. I've installed Edgy as a dual boot and I'm loving every minute of trying to figure out this OS. Couple of things yet to figure out - and I can see that a quick search brings out tons of advice on how to fix them - which I'll have to fix given enough time.

Wireless doesn't work - followed the helpful link from Tristan. Everything peachy except that the wireless doesn't connect despite giving the WPA-TKIP passkey.
and Subwoofer doesn't work

Weekend project - getting XGL/Beryl to work.

aaahhhh the joy of learning! :D

---

### Post by mac.ryan on 2007-02-28
> **wataboutbob said:**
> thanks Ryan for the input [...] Weekend project - getting XGL/Beryl to work

There is a problem with the windows decorator there... I described how to work it around here: [http://quasipedia.com/2007/feb/running-ubuntu-dell-xps-m1710](http://quasipedia.com/2007/feb/running-ubuntu-dell-xps-m1710)

If you find out other cool stuff about ubuntu & the m1710 please post it either here or as a comment on my website... :)

...and yes... i am enjoying ubuntu on this machine as never before... :)

---

### Post by dr3am on 2007-03-04
Hi.

I am a complete new to this linux thing.  i have been raised on windows as long as i can remember but i want to change to linux but don't know how.  I have a dell xps m1710 core duo 2gig proc. I am very much interested in putting linux on it.  is there anyone who can give me a step by step instructions on how to get started.  I have downloaded the iso file already. but since i have never worked with linux I would like some helping hand as to what to do and what not to do.
Can someone please help me out.

thanks

---

### Post by mac.ryan on 2007-03-05
> **dr3am said:**
> I would like some helping hand as to what to do and what not to do. Can someone please help me out.

Hello dr3am, as you might already know ([http://www.ubuntu.com/support](http://www.ubuntu.com/support)) there are plenty of options to get help with ubuntu, depending from what you specifically need. You can benefit from a variety of media, ranging from this forum to the commercial support, and passing by interesting possibilities like the IRC channel. All depends from what you need.

Do you need some general "good advices" about linux? Do you have a specific doubt? Are you concerned about a particular feature/software? Are you worried you will stuck with the installation process? Or...

As "preemptive support" I can say a few things:
[LIST=1]
[*]I highly recommend to "play around" a bit with the live CD version of Ubuntu (the installation CD you downloaded the ISO image of), so that you can have a "taste" of it before you begin the installation process. Performances will be limited and not all the features will work, but at least you will be able to get an idea of how ubuntu looks like, before to undergo the installation and configuration process.
[*]If you are concerned about the installation process, I can tell you that it is not much more difficult than posting a message on this forum... Ubuntu is really thought to be user-friendly, and it is pretty successful in this! :)
[*]If the installation is what you want support on, it would be helpful to know some more details on what you want to do:[/LIST][INDENT][LIST]
[*]Are you planning to totally replace Window$ or to have a dual boot system?
[*]Is your system brand new or you have already a lot of stuff installed on it?
[*]If it is a dual-boot system, do you need to access your data from either your systems or this is not important?[/LIST][/INDENT]As you might know, I am a lucky and happy owner of M1710, so I feel to reassure that ubuntu on this machine is just gorgeous! :)

---

### Post by wataboutbob on 2007-03-06
> **mac.ryan said:**
> As you might know, I am a lucky and happy owner of M1710, so I feel to reassure that ubuntu on this machine is just gorgeous! :)

I second that. Almost everything worked after a quick search in the forums here. To enable wireless WPA, follow the link from Tristan's 1st post in this thread. 

I would also suggest reading the following easy guide made at [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

For Beryl to work without too much hassel, I used the guide in the Beryl Wiki. Someone had written a script to take care of downloading the nvidia drivers and for everything else.

Subwoofer, as mentioned by Ryan, was a bit of a pain. But with the newer alsamixer, that was enabled too. Doesn't sound as good as in Windows though. If I can find the thread, I'll post it here. 

For everything else not covered by psychocats, Beryl wiki... you can follow up with this link [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Unofficial_Ubuntu_6.10_.28Edgy_Eft.29_Starter_Guide](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Unofficial_Ubuntu_6.10_.28Edgy_Eft.29_Starter_Guide)

You can also have a look at Ryan's very nice blog for his experience and links when installing Ubuntu on the M1710. Nice read Ryan.

Hope that helps.

---

### Post by mac.ryan on 2007-03-06
> **wataboutbob said:**
> Subwoofer, as mentioned by Ryan, was a bit of a pain. But with the newer alsamixer, that was enabled too. Doesn't sound as good as in Windows though. If I can find the thread, I'll post it here.

I tried that too, but for some strange reason, gnome-alsamixer only allows me to set up the modem sound device (the audio card being simply invisible to it) did you experience the same? How did you fixed in that case?

---

### Post by chevrier on 2007-03-06
yep ubuntu is the way to go.  Safe, FAST, Stable, the only time I use the windows partition is when I need to screw around with my Ipod Shuffle, only because I did not have time to invest in learning how to do it under ubuntu (did not find any immediate doc to follow).

As for wataboutbob's question, I find that 64 runs faster if you want to do computations.  I use my laptop only for matrix computations, and with the ATLAS BLAS, you fly.  Faster than 32.  But you lose flashplayer and a few other things.  It's less "supported" so to speak.  It gets messier with all the libs (you have to worry about 32 and 64 bits now).

Last, I found that using 2.6.18.8 kernel works great, except I still do not have sound!  I must have screwed something up (I have the sound with the Edgy kernel, 2.6.17. something).  did anyone manage to compile the 2.6.20.x kernel?  It has Core2Duo specifities.  I tried with both Edgy's gcc 4.1 and with a self compiled gcc4.3.0, but the compile always crashes in the middle.  I never had problems so far with any of the other kernels.

Thanks for your input!
Thomas

---

### Post by wataboutbob on 2007-04-22
Hello! Just a quick update to say that everything worked just perfectly when installing Feisty Fawn on the XPS M1710. No need for wpasupplicant thingee, no worries about subwoofer and new alsamixer... nothing extra needed.

And the system seems a lot faster during general use too. cheers!

---

### Post by mac.ryan on 2007-04-22
I can confirm that... also with 64 bit version (just in case somebody wonders).

The only annoying thing (but I  haven't looked for a solution yet) is that the master volume control is bound only to the front speakers and not to the LFE (sub-woofer channel). This way nor the small icon in the pane nor the HW front buttons on the laptop behave as they are expected (decreasing the overall volume of the sound), and they just affect the high frequencies.

BTW: I have **exactly** the same specs of the poster above...

---

### Post by mac.ryan on 2007-04-22
The solution to the problem mentioned above is quite easy:
System --> Preference --> Sound --> Default mixer tracks

---

### Post by ThrottledU on 2007-04-24
Hey guys, I need some help here on this

I have a m1710 as well, and want to put 7.04 on it, but when i try to go through the install after booting to the CD, it's running in 800x600 so i can't even see the buttons at the bottom of the windows to click on... how can I install it if I can't see those buttons?  I tried to run the install a couple of times but no dice.

I got edgy working (6.10) and had no issues but on this new feisty, it is not letting me click on buttons or move the screen so that i can SEE the buttons to click them for 'next' or whatever the install process is..  i hope this makes sense...if I could just run at a little higher resolution it would work i'm sure but when booting to the cd it runs at only 800x600 and nothing higher.   

ANy thoughts?

Ubuntu is very nice and i was wanting to get back into it again since I'm done with school now.

Thanks in advance,

---

### Post by mac.ryan on 2007-04-24
The issue is with Feisty not recognising the 9750 GTX (or at least: this is the card on my system). I solved it installing drivers from nVidia website.

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Some other users told me that they got past it simply installing nvidia-glx-new package, but that didn't do the trick for me (I chose to install the 64bit version, though).

---

### Post by ThrottledU on 2007-04-26
ok, but the problem for me is that I haven't actually installed it on the system yet... I am only booting to the live cd and then trying to install from there...  is there another way to install where I will be able to see all of the navigational buttons through the process?

---

### Post by mac.ryan on 2007-04-26
Just use the alternate installation CD. The installation process follows the same pattern, but it is text-based. (I did that one by chance, so I didn't realise at first what was the problem you were describing... sorry!)

---

### Post by ThrottledU on 2007-04-27
ok, i'm gonna grab the installer for the alternate and give it a try....hopefully i can get something working.   I love my laptop and I love ubuntu, I want to get it back on here!

---

### Post by ThrottledU on 2007-04-28
Well, the alternate 64bit version is what i used....working like a charm with beryl and nvidia on my system....cheers.  thanks for the heads up about the alternate install CD.  Long live Ubuntu!

---

### Post by daller on 2007-04-29
> **boldMonkey said:**
> Hi Tristan
I strongly considering getting a Dell XPS M1710. It will come with the much trumpeted Vista OS which in itself will be interesting but  I have also considered a dual boot linux system. 

Like you I'm not a linux newbie, nor am I a guru but my previous builds (fedora, mandrake and suse) have been on desktops not laptops.  Have you come across any unique problems with your ubunta install on your xps1710?

Dell is easily talked into delivering the laptop without Windows!
 - I was offered a €50 discount!

I'm also considering to buy an XPS M1710!
 - The lights are also configurable from linux!

---

### Post by ThrottledU on 2007-04-29
well, i can say this, it runs awesome on my m1710 here now and i'm very much enjoying feisty fawn now.  I now use 4 operating systems..... xp, mac osx, ubuntu and vista... (not much vista just toyed with it, the other 3 are my mains)

mac os is great, xp is great, ubuntu is great...they're all great for different reasons :) 

i am definately liking this version of ubuntu so far, and learning more all the time with it.

---

### Post by Burnspot on 2007-05-04
> **ThrottledU said:**
> Hey guys, I need some help here on this

I have a m1710 as well, and want to put 7.04 on it, but when i try to go through the install after booting to the CD, it's running in 800x600 so i can't even see the buttons at the bottom of the windows to click on... how can I install it if I can't see those buttons?  I tried to run the install a couple of times but no dice.

I got edgy working (6.10) and had no issues but on this new feisty, it is not letting me click on buttons or move the screen so that i can SEE the buttons to click them for 'next' or whatever the install process is..  i hope this makes sense...if I could just run at a little higher resolution it would work i'm sure but when booting to the cd it runs at only 800x600 and nothing higher.   

ANy thoughts?

Ubuntu is very nice and i was wanting to get back into it again since I'm done with school now.

Thanks in advance,

You solved the problem by using the alternate CD, but for the sake of anyone else wondering, just hold down the "alt" key while dragging on the window....you can move the window up enough to see the buttons.

---

### Post by ZombieAcademy on 2007-05-06
This thread inspired me to try Ubuntu again on my XPS m1710 (I had tried Edgy and had no luck with wireless).

Now that I have reinstalled, wireless is not working. I've enabled 'wireless on always' in the BIOS, and the wifi light is on, however no wireless drivers show up in "Restricted Driver Manager" and no wireless device is listed in 'Network Settings'.

Any advice? I've reinstalled earlier versions of Ubuntu countless times trying to get this working, after trying to follow several different tutorials and hosing my install in ways I can't even concieve. That's not hard for me to do, since I am a complete novice at this.

Is it possibly because the wireless card wasn't enabled when I installed? Do I need to reinstall with the card enabled? Or is there some way to get this working without a reinstall?

Thanks in advance.

edit-- I forgot to mention I am running Feisty 32 bit edition, installed from the live DVD image.

---

### Post by daller on 2007-05-06
> **ZombieAcademy said:**
> 
Now that I have reinstalled, wireless is not working.

Please post the output from these commands:

lspci
iwconfig
ifconfig -a
cat /etc/network/interfaces

And maybe try to contact some of the other folks having a m1710? - [https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1710](https://wiki.ubuntu.com/LaptopTestingTeam/DellXPSM1710)

Thank you!

---

### Post by ZombieAcademy on 2007-05-06
Sure thing:
lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7900 GTX (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:15:C5:4F:04:45  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe4f:445/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1358014 (1.2 MiB)  TX bytes:286709 (279.9 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

```

cat /etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

Thanks for your time

---

### Post by daller on 2007-05-07
> **ZombieAcademy said:**
> 
0c:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)
iwconfig


There is the problem!
A broadcom wireless device :(
The only way around this, is using NDISwrapper! (Which may require a little tangling!)

Please see this wiki:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

...and report back with your experience!

---

### Post by Tristan Schmelcher on 2007-05-07
I thought I'd mention that ndiswrapper is not the only option. For Broadcom 43xx cards, Linux does actually have a driver, but the computer needs to load the card with its firmware on every boot and for legal reasons they can't ship the firmware with the driver, so you have to get it manually to "complete" the driver. See this thread for the instructions:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

I followed those instructions to get a Broadcom 43xx wireless device working on another laptop of mine with Feisty 64-bit, and it worked like a charm. I've never set up ndiswrapper, but I imagine that would be more difficult.

---

### Post by ZombieAcademy on 2007-05-08
So, little success on either front.

I went through the entire ndiswrapper installation. I had to try several .inf files from the ndiswrapper list that all had my PCI ID. I finally found one listed under the "D" section for Dell that would install. This was fairly time consuming because they are exe files and I couldn't figure out how to extract them in ubuntu, so I had to boot back into windows to extract the files, then copy them over each time. [edit --found the unzip command in another tutorial, much easier]

Ndiswrapper installed the drivers, but said that no hardware was present. However, I could see a new listing under "wlan0" if I did a iwconfig. I also managed to get a list of surrounding networks so I guess at some level the card worked, although it never showed up as working in ndiswrapper. I couldn't connect to the network though, there wasn't an option for wpa. Grudginly I went through the wpa-supplicant install process, although I am pretty sure I read someone with my exact laptop model explicitly saying they didn't need this as wpa worked "out of the box" with feisty and there was no need for wpa-supplicant. At any rate, no dice. Even though there were no errors with the wpa-supplicant install it would never connect.

I uninstalled ndiswrapper and reverted the /etc/network/interfaces file.

Next I tried the firmware page. That doesn't get anywhere. It unpacks a bunch of files to /lib/firmware but there is absolutely no change to the appearance of the network manager as implied b the tutorial, and wireless is not even an option on a right or left click. The broadcom device still shows up as Unknown even after a reboot. I had a feeling this one wouldn't work because his broadcom card is detected properly at the start of the tutorial and I can't even get that far.

I don't understand how there are people with the same laptop model who experienced no problems "out of the box" with the same version of Ubuntu. :(

-- UPDATE --

So I reinstalled Ubuntu and started over with this tutorial:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

And it worked! I followed it to the letter, including the suggested second reboot. Also I double checked and the dell wireless driver listed in the tutorial is the proper driver for the XPS M1710, even though the walk through is for a different model. So following this tutorial EXACTLY has worked for me, including WPA. Also, even though I am currently submitting this post over wireless, the lspci command still shows the network controller at that address as Broadcom Corporation Unknown Device.

Thanks for the help everyone.

---

### Post by gealvare on 2007-05-24
> **mac.ryan said:**
> The solution to the problem mentioned above is quite easy:
System --> Preference --> Sound --> Default mixer tracks

Awesome mac, I was wondering for the solution of the exact same thing.

---

### Post by black_knight on 2007-06-18
Hey everybody. new guy to the forums and am wanting to install Ubuntu.
I have read most of the posts here but just want to make sure I install it all right.
I have a XPS M1710 with 
2GB RAM
Nvidia 7900 GTX
3945AGB wireless network
Broadcom wired network
Intel Centrino Duo T2500
Basically everything you guys have.
So I know about the graphics driver but are there certain drivers one needs for the rest of the hard ware, and were can one download these, or do the original drivers (ie. processor) work with Ubuntu.:popcorn:

---

### Post by ThrottledU on 2007-06-19
I don't think you'll have much if any problems with your system for install.... your system is pretty default and all of the drivers you should need are right there ready to go.... i say GO FOR IT!   The only issue i've had with my XPS system is getting the nvidia driver to work properly with resolutions from a fresh install... I think I'm using the newest version of nvidia driver but it's working awesome now with some minor tweaks to xorg.config   

I'm using the 7950 though, on my other XPS with the 7900, it worked perfect from the start.    Since you have the 3945 wireless card, you shouldn't have the problems that the broadcom guys are having... the intell works out of the box on every system i've installed it on.

Have fun!

---

### Post by black_knight on 2007-06-19
Sweet
Thanks man.

Will be installing Ubuntu within the next 3 days.\\:D/

---

### Post by FreeSoul on 2007-07-25
I am running Fiesty with a few small problems.
I have an XP dual boot and in windows my mic works but in linux it won't. 
Can someone offer anything to get my mic working? (external)

Under sound preferences, "Devices", "Audio Conferencing" - "sound capture"
is set to STAC92 analog.
I get an error when I set it to digital. None of the other choices (ie. OSS) seem to work.
Clicking the test button does nothing.

Anyone?

Thanks,
FreeSoul

---

### Post by Dead_$partan on 2007-07-25
Might be an idea to try running alsaconf or is it alsaconfig? I cant remember which, might fix it but im not great with this stuff, im usually the one asking the questions :lolflag:

I have an XPS M1710 with feisty and it works like a dream.  Got it with the 7950GTX, the only issue I seem to have noticed so far is that the refresh rate is set to 50Hz and cannot be changed, I havent tried playing about with it as I aint really had the time, any one know if this can be resolved?

Thanks

---

### Post by FreeSoul on 2007-07-25
> **Dead_$partan said:**
> Might be an idea to try running alsaconf or is it alsaconfig? I cant remember which, might fix it but im not great with this stuff, im usually the one asking the questions :lolflag:

I have an XPS M1710 with feisty and it works like a dream.  Got it with the 7950GTX, the only issue I seem to have noticed so far is that the refresh rate is set to 50Hz and cannot be changed, I havent tried playing about with it as I aint really had the time, any one know if this can be resolved?

Thanks

I have the same setup as you. Thanks for the tip. I tried to install the alsa package but had problems with the gui portion, couldn't download. But it might do the trick, I'll try again later.

Regarding the 50HZ thing, I checked and I got the same problem! Anyone?
To be honest I haven't noticed it bothering my eyes much???

---

### Post by Dead_$partan on 2007-07-25
> **FreeSoul said:**
> Regarding the 50HZ thing, I checked and I got the same problem! Anyone? To be honest I haven't noticed it bothering my eyes much???

No I must say it hasnt caused me any problems either, would be nice to get it up to the standard 60Hz though, just because..hehe

Good luck with the sound issue:guitar:

---

### Post by cable8 on 2007-07-28
Is anyone got the S/PDIF out running? (over Dell's special composite cable)
With internal speakers and subwoofer sound works fine so far -  
But even though alsamixer shows an IEC958 switch,  i can't get 
any signal over S/PDIF

any help would be appreciated

---

### Post by black_knight on 2007-08-13
Ubuntu is not readily setup to work with more than one monitor.:(
A lot of patience is involved to setup Ubuntu to accept multiple monitors.

Here should help.
[http://www.plingboot.com/2006/03/01/ubuntu-dual-monitor-support-with-nvidia-2/]("http://www.plingboot.com/2006/03/01/ubuntu-dual-monitor-support-with-nvidia-2/")

---

### Post by Tristan Schmelcher on 2007-08-25
Just thought I'd mention that I finally bought an ExpressCard peripheral (an eSATA-to-ExpressCard adapter), and the slot in this laptop works completely (though I'm actually running Debian Etch/Lenny 2.6.22-1-amd64 right now). However, you have to add "pciehp pciehp_force=1" to /etc/modules to get it to see things that you hotplug.

---

### Post by ronald.higgins on 2007-10-17
> **Dead_$partan said:**
> No I must say it hasnt caused me any problems either, would be nice to get it up to the standard 60Hz though, just because..hehe

Good luck with the sound issue:guitar:

We need to get the Horizontal and Vertical Sync Speeds for the LCD's from Dell.
I havent had much joy getting a response from them (maybe cuz i'm out of warranty now).

Then  we need to enter that info into the xorg.conf.

Anyway, drop them a line as well, and post back here if you get an answer from them.

rH

---

### Post by Dead_$partan on 2007-10-19
Well I work for them so I will see if I can pick someones brains.  maybe the info will be included in the service manual @ support.euro.dell.com

---

### Post by ubuntunewb75 on 2008-01-24
Hi!

Bump to see if anyone has installed Gutsy yet on the 1710?  I'm thinking of waiting for the next LTS (April 2008) before tanking my original Vista install (its just infuriating me at the moment:mad:).

Also, I have 4GB of ram--will I have to run a 64bit version of Ubuntu, or will the 32 work just fine?

---

### Post by Tristan Schmelcher on 2008-01-24
I'm typing this on my M1710 with gutsy right now. Works perfectly, including:

- Media keys (out of the box)
- ExpressCard interface (out of the box, though a bit of work was needed to make my peripheral fully work, an eSATA II adapter)
- SD card reader (out of the box)
- Bluetooth (out of the box, not withstanding the still-horrible UX for Bluetooth on Linux in general)
- My NVIDIA Go 7900 GS with the proprietary drivers (out of the box)
- My Intel 3945 Wireless adapter (out of the box)
- My Broadcom NetXtreme gigabit wired adapter (out of the box)
- The DVD burner (out of the box)
- Anything I'm forgetting?

The internal modem is _not_ recognized, but I'm sure no one cares about that. Also, you can't control the LED settings in Linux, not even with WINE, so make sure you're happy with them before switching.

---

### Post by Tristan Schmelcher on 2008-01-24
Oh, I forgot to answer your other question. I'm pretty sure you can use the 32-bit version and you'll even still be able to use all of your RAM. I'm using the 32-bit version but I only have 2 GB. If you're new to Linux then I strongly recommend the 32-bit version. 64-bit Linux gets even less support from closed-source software companies than 32-bit Linux (much like 64-bit Windows, really), and the procedures to get closed-source 32-bit programs to run properly in the 64-bit version (when even possible) can be very technical. I ran 64-bit Linux back when I used Debian, but it was a pain.

---

### Post by mac.ryan on 2008-01-27
Typing as well from the M1710, with Gutsy 64 bit. In the past it was true that running a 64 bit version was a bit of a pain. Nowadays I would say it is not any more. The very only thing that is not in the repos (because it does not exist) was the flash plugin, but you can easily find how to "ndswrap" the 32 version in gutsy 64.

Unless you have some very very precise reason to use the 32 version I would say: go for 64 and enjoy the extra boost! :)

PS: the only thing that stopped working from Edgy to Gutsy (both 64 bit version) is the composite key (the feature to type with a combination of keys letters with accents).

---

### Post by Tristan Schmelcher on 2008-01-27
Yeah, nspluginwrapper will let you run Flash on 64-bit Linux quite easily (I think in Ubuntu it's literally just a package that you select now), but there are at least a couple other programs that take extra effort on 64-bit. Specifically Skype and the Java plugin for Firefox. (Skype being fairly easy to get working right, and the Java plugin being very complex.) Plus a couple times I've run into bugs in programs that only existed on the 64-bit version. So I usually advise people to go with 32-bit.

Apparently people are working on "multi-arch" support that might lay these problems to rest ...

---

