---
title: "Asus Zenbook Prime UX31A and UX32VD"
date: 2012-06-18
forum: Hardware
---

### Post by chicgeek on 2012-06-18
Has anyone gotten their paws on the new Ivy Bridge models of the Zenbook? I believe there were issues with battery life and suspend on the Sandy bridge models, though I'm not sure if these could be fixed manually or not.

I'm particularly interested to see if ubuntu will play well with graphics switching for the Zenbook UX32VD-DB71. If not, I'll likely opt for the Zenbook Prime UX31a-DB71.

[LIST]
[*]**Ubuntu on older Zenbook models:**
[http://ubuntuforums.org/showthread.php?t=1870893](http://ubuntuforums.org/showthread.php?t=1870893)
[*]**Asus Zenbook on Ubuntu help**
[https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook)
[*]**Spec comparison of different models**
[http://forum.notebookreview.com/asus/659073-ivy-bridge-zenbook-fhd-ips-screen-ux21a-ux31a-ux32a-ux32vd-56.html#post8622617](http://forum.notebookreview.com/asus/659073-ivy-bridge-zenbook-fhd-ips-screen-ux21a-ux31a-ux32a-ux32vd-56.html#post8622617)
[/LIST]

---

### Post by pchokola on 2012-06-18
I am also interested on running Linux on this notebook (Ubuntu, Fedora and CentOS). I am looking at either this notebook or the Lenovo X230.
 
If someone gets their hands on one I would like to know if the Nvidia graphics can be disabled in BIOS so it runs on the Intel 4000 chip only. That way worst case scenario I could run Windows using Nvidia and Linux running Intel.
 
After Linus Torvalds gave Nvidia the finger last week I am not too "optimistic of optimus" running on Linux any time soon!

---

### Post by bweber on 2012-06-20
i own one. Most fn-keys dont work. NVidia isnt working. Bumblebee pm works. but pm isnt that good at all

---

### Post by chicgeek on 2012-06-20
> **bweber said:**
> i own one. Most fn-keys dont work. NVidia isnt working. Bumblebee pm works. but pm isnt that good at all

Check the links I posted above. I think there's a pretty common config fix for the fn buttons. Can you let us know if they work after this?

What's PM? Also, since you mentioned nvidia, it sounds like you have the UX32VD, correct?

Thanks in advance!

---

### Post by bweber on 2012-06-25
pm = powermanagement. 
Yes I've the UX32VD. I didn't get the fn-keys working yet. The mentioned links didn't help me yet...

---

### Post by dr.frankinfurter on 2012-06-25
Bweber, how is everything else working? I'm really interested in putting Linux on this thing.

---

### Post by quack on 2012-06-27
nexero's DKMS package here: [http://ubuntuforums.org/showthread.php?p=12054636#post12054636](http://ubuntuforums.org/showthread.php?p=12054636#post12054636) gave me mostly working function keys (UX32VD, Ubuntu 12.04). No screen brightness keys yet though.

---

### Post by x_O on 2012-06-27
If asus could imagine how many developers they may have when they will provide good Ubuntu support for those machines. This perfect stuff for most of us. 

[LIST]
[*]small - easy to grab and go to meeting, conference
[*]powerful - gets **** done,
[*]battery - at least in Windows from what i see. In perfect scenario you wouldn't be part of plug race 
[*]screen - not glossy finally for good sake what is wrong with people those days
[*] possibility to replace **** inside, comes with crap but you can easily replace to SSD and 10 GB  
[/LIST]

Most will go with Macbook Air/13" Pro **again** with Xcode and we will pretend this is Linux. I'm only one who see that niche? 

I would say that I can volunteer to work for free to any company that will finally wrap any Linux to developer laptop machine. 

sorry for offtopic :)

---

### Post by screemo on 2012-06-28
> **x_O said:**
> If asus could imagine how many developers they may have when they will provide good Ubuntu support for those machines. This perfect stuff for most of us. 

[LIST]
[*]small - easy to grab and go to meeting, conference
[*]powerful - gets **** done,
[*]battery - at least in Windows from what i see. In perfect scenario you wouldn't be part of plug race 
[*]screen - not glossy finally for good sake what is wrong with people those days
[*] possibility to replace **** inside, comes with crap but you can easily replace to SSD and 10 GB  
[/LIST]

Most will go with Macbook Air/13" Pro **again** with Xcode and we will pretend this is Linux. I'm only one who see that niche? 

I would say that I can volunteer to work for free to any company that will finally wrap any Linux to developer laptop machine. 

sorry for offtopic :)

I can definitely relate to that :)

Irritates me that they dont use a little time atleast providing a blob/src you can load as a module for these models.

---

### Post by x_O on 2012-06-28
And I forgot to mention that I don't give a **** if laptop price is 500 or 2000$ this is my toolbox I really need good one. 

And I really like Linux, kind of got use to it. Apple philosophy takes **** out of me, but I have to admit they've done a lot for laptops in general. They've setup bar quite high.

---

### Post by arjmage on 2012-06-30
I see a lot of like-minded folks on this thread, and I can confirm a few things:

The Zenbook Prime is a sexy, fast and handy machine. The screen is excellent, and visible easily even outside on the balcony in bright sunlight. The keyboard is good, backlighting, etc. Sound is nicely tonal, and doesn't screech in either direction for normal volumes.

I bought the UX31A with i7 processor, 4Gb Ram. My unit runs Linux Mint 13, with the cinnamon interface, in case that matters. It's a wrapper around the Ubuntu 12.04 release. Before I shell out the 1000+ euros, I took a ubuntu liveboot usb to the store and confirmed that most things work -- and the same things do not work as listed in [this wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") I have updated some entries in that wiki to reflect this.

Using the fix, most function keys do work. The touchpad usage is bearable, until a proper fix comes our way.

However, a serious problem in such a machine is the poor battery life. After 100% charge on the battery, with the brightness set at 50%, I unplug the charger and the immediate number is 3 hours battery remaining. That is hardly acceptable.

I have tried the Power Optimization tricks listed in the wiki above, and also enabled ALPM. My first tests were hardly promising: I've added an entry for [wiki here]("https://wiki.ubuntu.com/Kernel/PowerManagementALPM").

Looking for suggestions on what to try to improve the abysmal battery performance.

---

### Post by screemo on 2012-06-30
Anyone got a working patch for the quantal kernel ? - the above seems only to work on precise kernels.

Also is there instructions on how to install the nvidia driver without it conflicting with the intel/bumblebee combo ?

Any help appreciated :D

---

### Post by bzhb on 2012-07-01
A small script to hack around the backlight function keys problem:[]("http://https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight")
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight)

---

### Post by screemo on 2012-07-01
> **bzhb said:**
> A small script to hack around the backlight function keys problem:[]("http://https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight")
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_backlight)

Thanks for the tip - I tried it, and the neither the intel_backlight or acpi_video0 has any effect. 

Did anyone get the Fn-keys patch to work on the quantal kernel (3.5.x) ?

---

### Post by bzhb on 2012-07-01
> **screemo said:**
> Thanks for the tip - I tried it, and the neither the intel_backlight or acpi_video0 has any effect. 
Really ? It is probably because Arch linux has a more recent kernel (3.4.4). At least it is working fine on my UX31A on Arch. 

You should look at this [http://ubuntuforums.org/showpost.php?p=12065100&postcount=67](http://ubuntuforums.org/showpost.php?p=12065100&postcount=67)

---

### Post by screemo on 2012-07-02
> **bzhb said:**
> Really ? It is probably because Arch linux has a more recent kernel (3.4.4). At least it is working fine on my UX31A on Arch. 

You should look at this [http://ubuntuforums.org/showpost.php?p=12065100&postcount=67](http://ubuntuforums.org/showpost.php?p=12065100&postcount=67)

Thanks I will check it out :)

I can confirm it works on kernel 3.2.0, but I get strange lockups sometimes I didn't see on 3.5rc kernel - think I will move to that, and maybe adapt the patch when quantal becomes more stable.

Anyone noticed that hotkey on the A-key - is that for automatic keyboard backlight or the screen ?

---

### Post by 9rift on 2012-07-02
Hi,
I'm interested by that ultrabook too :)
I just have one question to the people who have them: can we disable nvidia chips on the bios ? 
It can be a nice try to save power if it exist :)

Thanks,

---

### Post by screemo on 2012-07-03
> **9rift said:**
> Hi,
I'm interested by that ultrabook too :)
I just have one question to the people who have them: can we disable nvidia chips on the bios ? 
It can be a nice try to save power if it exist :)

Thanks,

From what found, the bumblebee project has a bbswitch command for turning the card on/off (see [https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)).

I purchased my ux32 mainly because of the possibility to exchange hdd and add memory - the nvidia card is of no use to me.

However if something can save further battery it would be nice know :)

EDIT: appears that just installing bumblebee should give you an immediate benefit - it disables the discrete graphics completely when not in use (will use if you run optirun <application>).

[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

---

### Post by 9rift on 2012-07-03
> **screemo said:**
> From what found, the bumblebee project has a bbswitch command for turning the card on/off (see [https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ](https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ)).

I purchased my ux32 mainly because of the possibility to exchange hdd and add memory - the nvidia card is of no use to me.

However if something can save further battery it would be nice know :)

EDIT: appears that just installing bumblebee should give you an immediate benefit - it disables the discrete graphics completely when not in use (will use if you run optirun <application>).

[https://launchpad.net/~bumblebee/+archive/stable]("https://launchpad.net/%7Ebumblebee/+archive/stable")

That should do the trick, but have you tested it ?
I'm curious about difference of the battery between the nvidia chip on and off

---

### Post by mbleigh on 2012-07-03
I've managed to get Ubuntu up and running on my UX31A. By upgrading to the Quantal kernel the trackpad is working better, I've got the Fn keys working all right, but I can't seem to get the Ubuntu bootloader to take over from Windows.

I've reinstalled about a dozen times but nothing seems to make a difference. Whatever the installation process is doing, it's not making grub the default bootloader. Right now the only way for me to boot into Ubuntu is to have a bootable USB key attached.

Can anyone help?

---

### Post by dancat on 2012-07-04
> **mbleigh said:**
> I've managed to get Ubuntu up and running on my UX31A. By upgrading to the Quantal kernel the trackpad is working better, I've got the Fn keys working all right, but I can't seem to get the Ubuntu bootloader to take over from Windows.

I've reinstalled about a dozen times but nothing seems to make a difference. Whatever the installation process is doing, it's not making grub the default bootloader. Right now the only way for me to boot into Ubuntu is to have a bootable USB key attached.

Can anyone help?

If you used the 'advanced/manual' way of partitioning and did not let the installer to recreate everything, you have to make sure that you have created a uefi partition larger than 200Mb and after that you specified the grubloader to be installed on /dev/sda (automatically is set to /dev/sdb for a reason i do not really understand).

What i did to fix this was to create the uefi partition using gparted and after that follow this instructions to reinstall grub: [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

---

### Post by Sam1994 on 2012-07-04
I really want to get one of these for uni to put Linux on. TBH was looking more at Debian because I feel Ubuntu has gone downhill with Unity (I'm not trying to start an argument here), but I prefer idea of package freshness in Ubuntu now anyway.
 
after the DKMS packages etc what is battery life like now? Some guys say UX31A is churning a good 6hrs out, yet someone in this thread said 3hrs on UX32VD. I want to buy a UX32VD, because, I too, want the extra RAM for big compiles and virtualisation, the HDD because a lot of IO during my makes and I want the portability. I don't want a Windows machine, an OSX machine, I want a linux machine..
 
Are you guys getting same battery life with ux32vd as people with ux31a are getting or does discrete GPU and spinning HDD take that down?

---

### Post by 9rift on 2012-07-04
> **Sam1994 said:**
> I really want to get one of these for uni to put Linux on. TBH was looking more at Debian because I feel Ubuntu has gone downhill with Unity (I'm not trying to start an argument here), but I prefer idea of package freshness in Ubuntu now anyway.
 
after the DKMS packages etc what is battery life like now? Some guys say UX31A is churning a good 6hrs out, yet someone in this thread said 3hrs on UX32VD. I want to buy a UX32VD, because, I too, want the extra RAM for big compiles and virtualisation, the HDD because a lot of IO during my makes and I want the portability. I don't want a Windows machine, an OSX machine, I want a linux machine..
 
Are you guys getting same battery life with ux32vd as people with ux31a are getting or does discrete GPU and spinning HDD take that down?

People says about 4h30 
> 
   Depends heavily on what you call “normal use”, and how bright you want your screen backlight. 
   But about 4:30h are realistic under a moderate load like “doing some web-surfing via WLAN”. 
        


source on comment : [http://www.linlap.com/wiki/asus+ux32vd?&#comment_af381a27fcc7b3c737b71e75cad3651c](http://www.linlap.com/wiki/asus+ux32vd?&#comment_af381a27fcc7b3c737b71e75cad3651c)

---

### Post by Sam1994 on 2012-07-04
thanks for that. I wonder if with some powertop output and kernel hacking it can be 5 1/2 - 6 hours. I think by upgrading to SSD it will go up too.
 
it would be nice if GPU had a driver that worked as I want VDPAU for 1080p h264 accelaration

---

### Post by screemo on 2012-07-08
> **dancat said:**
> If you used the 'advanced/manual' way of partitioning and did not let the installer to recreate everything, you have to make sure that you have created a uefi partition larger than 200Mb and after that you specified the grubloader to be installed on /dev/sda (automatically is set to /dev/sdb for a reason i do not really understand).

What i did to fix this was to create the uefi partition using gparted and after that follow this instructions to reinstall grub: [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

Did you fix the brighness up/down by creating a script, or is it working like automatically?

---

### Post by screemo on 2012-07-08
> **9rift said:**
> That should do the trick, but have you tested it ?
I'm curious about difference of the battery between the nvidia chip on and off

Didn't notice anything significantly - however I have no before/after numbers to tell you - just installed everything that might be needed.

---

### Post by screemo on 2012-07-08
> **bzhb said:**
> Really ? It is probably because Arch linux has a more recent kernel (3.4.4). At least it is working fine on my UX31A on Arch. 

You should look at this [http://ubuntuforums.org/showpost.php?p=12065100&postcount=67](http://ubuntuforums.org/showpost.php?p=12065100&postcount=67)

I have attached the patch for the quantal (3.5.x) kernel if anyone needs it.

It works the same as on the precise (3.2.x) - but without random lockups (this is due to some old stuff in the kernel it seems).

There's no deb for it, since I imagine the kernel will still be updated a few times on quantal, so instructions is this:

0) install quantal kernel headers
1) tar zxvf asus-wmi.tar.gz to /usr/src/
2) sudo dkms build -m asus-wmi -v 999.01
3) sudo dkms install -m asus-wmi -v 999.01

Reboot - and then Fn keys for audio, keyboard backlight should work.

---

### Post by dancat on 2012-07-09
> **screemo said:**
> Did you fix the brighness up/down by creating a script, or is it working like automatically?

I did not fixed them yet, but xrandr --output eDP1 --brightness <value> works, so probably a script can be created. Right now, i am setting the brightness in a script that also changes the dispaly DPI whenever the user logins or HDMI events are triggered, so i am not bothered by the issue anymore.

---

### Post by screemo on 2012-07-09
> **dancat said:**
> I did not fixed them yet, but xrandr --output eDP1 --brightness <value> works, so probably a script can be created. Right now, i am setting the brightness in a script that also changes the dispaly DPI whenever the user logins or HDMI events are triggered, so i am not bothered by the issue anymore.

Is it something you are willing to share ?

How about the dpi, does it work reliably with dialogs and all ?

---

### Post by 9rift on 2012-07-09
> **screemo said:**
> Is it something you are willing to share ?

How about the dpi, does it work reliably with dialogs and all ?

It's better to use xbacklight -set <value> i think

---

### Post by screemo on 2012-07-09
Just for information - the bumlebee ppa for precise works excellent with the latest quantal development version (as of 2012-07-09).

Install:

1) add-apt-repository ppa:bumblebee/stable
2) replace quantal with precise in /etc/apt/sources.list.d/bumblebee-stable-quantal.list
3) apt-get install bumblebee

DKMS build for bbswitch and nvidia_current should succeeed.

4) reboot

---

### Post by screemo on 2012-07-09
> **9rift said:**
> It's better to use xbacklight -set <value> i think

Xbacklight seems to work great - just need to figure out how make the Fn+brightness up/down to emit and event...

Any clues?

---

### Post by screemo on 2012-07-09
> **screemo said:**
> Just for information - the bumlebee ppa for precise works excellent with the latest quantal development version (as of 2012-07-09).

Install:

1) add-apt-repository ppa:bumblebee/stable
2) replace quantal with precise in /etc/apt/sources.list.d/bumblebee-stable-quantal.list
3) apt-get install bumblebee

DKMS build for bbswitch and nvidia_current should succeeed.

4) reboot

If you encounter problems with desktop effects afterwards, just remove the nvidia-current package

---

### Post by 9rift on 2012-07-10
> **screemo said:**
> Xbacklight seems to work great - just need to figure out how make the Fn+brightness up/down to emit and event...

Any clues?

I havent received my UX32VD yet :p !
Maybe you can try this : [http://forum.notebookreview.com/showthread.php?t=194717](http://forum.notebookreview.com/showthread.php?t=194717)

Cheers

---

### Post by screemo on 2012-07-10
> **9rift said:**
> I havent received my UX32VD yet :p !
Maybe you can try this : [http://forum.notebookreview.com/showthread.php?t=194717](http://forum.notebookreview.com/showthread.php?t=194717)

Cheers

You are in for at treat then :)

I already tried the xev method, but its not giving _any_ output. Thought about hacking the asus-wmi, and/or possibly dumping some information from the windows driver.

Still thinking about the options :)

---

### Post by quack on 2012-07-12
I upgraded my UX32VD's kernel to 3.3 (still running Ubuntu 12.04) and it seems (touch wood!) to have stopped the random total lockups I was getting a couple of times per day previously. I did lose the function keys for volume & keyboard brightness though. I miss them, but a fancy laptop that crashes every hour or two is less useful than a plainer laptop that works all day.

xbacklight doesn't do anything for me (returns silently if I don't specify a display, errors if I do), but xrandr --brightness works great - thanks. (Just a note for others: the brightness value should be between 0 and 1... it's kinda painful if you try 30 like I did LOL)

I see from the documentation though that 'xrandr --brightness' is a software thing & xbacklight's recommended as 9rift mentioned. I guess that means it's just altering the colour of the pixels. This appears to be proven by setting it to 0... at that point I can see backlight bleeding, so obviously the backlight is still on.

I wonder what the system settings brightness slider's doing? Is that controlling the backlight or just changing my pixel colours?

---

### Post by screemo on 2012-07-12
> **quack said:**
> I upgraded my UX32VD's kernel to 3.3 (still running Ubuntu 12.04) and it seems (touch wood!) to have stopped the random total lockups I was getting a couple of times per day previously. I did lose the function keys for volume & keyboard brightness though. I miss them, but a fancy laptop that crashes every hour or two is less useful than a plainer laptop that works all day.

xbacklight doesn't do anything for me (returns silently if I don't specify a display, errors if I do), but xrandr --brightness works great - thanks. (Just a note for others: the brightness value should be between 0 and 1... it's kinda painful if you try 30 like I did LOL)

I see from the documentation though that 'xrandr --brightness' is a software thing & xbacklight's recommended as 9rift mentioned. I guess that means it's just altering the colour of the pixels. This appears to be proven by setting it to 0... at that point I can see backlight bleeding, so obviously the backlight is still on.

I wonder what the system settings brightness slider's doing? Is that controlling the backlight or just changing my pixel colours?

You can switch to quantal kernel, and use my patch above - it will get the Fn keys working again. Although the brightness controls is still MIA.

Both xbacklight and xrand method dims my display as intended, but it might just alter the pixel color - dont know :)

---

### Post by bambam23 on 2012-07-12
hi,

i'm currently on quantal kernel and almost very satisfied with the overall performance of the device. :-)

Except for wifi. i really have issues connecting to the AP if its set to b/g/n with auto-channel selection. if i set it to b/g with fixed channel (one which is not in use in my neighbourhood) it connects but the connection itself is kind of unstable (download speed varies a lot, even if my device is the only one connected and the very same download is totally stable via ethernet). i tested that behaviour with 3.2 3.4 3.5 rc4-rc6. can anyone confirm such issues, or give me a hint on how to solve it?

---

### Post by screemo on 2012-07-12
> **bambam23 said:**
> hi,

i'm currently on quantal kernel and almost very satisfied with the overall performance of the device. :-)

Except for wifi. i really have issues connecting to the AP if its set to b/g/n with auto-channel selection. if i set it to b/g with fixed channel (one which is not in use in my neighbourhood) it connects but the connection itself is kind of unstable (download speed varies a lot, even if my device is the only one connected and the very same download is totally stable via ethernet). i tested that behaviour with 3.2 3.4 3.5 rc4-rc6. can anyone confirm such issues, or give me a hint on how to solve it?

I have the same experience - looking at the forums, I found some references to the N channel having issues:

[http://askubuntu.com/questions/73523/wireless-internet-connection-so-slow-after-upgrade-to-11-10](http://askubuntu.com/questions/73523/wireless-internet-connection-so-slow-after-upgrade-to-11-10)

I implemented the fix here on mine, and seems to have improved the issue a bit. Can you possibly test also ?

Looks like this is more relevant: [http://ubuntuforums.org/showthread.php?t=1985103&page=5](http://ubuntuforums.org/showthread.php?t=1985103&page=5)

---

### Post by bambam23 on 2012-07-12
@screemo: thanks for the information. i'll try it once i'm back from work. there's also a hint that disabling ipv6 might increase wifi performance. 

i'll report afterwards ...

---

### Post by quack on 2012-07-13
> **screemo said:**
> You can switch to quantal kernel, and use my patch above - it will get the Fn keys working again. Although the brightness controls is still MIA.

Both xbacklight and xrand method dims my display as intended, but it might just alter the pixel color - dont know :)


Thanks for the prod. I went with 3.3 because I'd initially tried 3.4 and it wouldn't boot... but I suspect now that that must have been something I did wrong.

Installed 3.5.0rc6 and your Fn keys patch and now appear to have the best of both worlds.

Still nothing from xbacklight though. Odd. Even "xbacklight -get" returns nothing. Wonder what I've forgotten to do.

Setting brightness to zero & looking at the screen in a dark room should tell you whether it's off or just a screen of black pixels.

---

### Post by screemo on 2012-07-13
> **quack said:**
> Thanks for the prod. I went with 3.3 because I'd initially tried 3.4 and it wouldn't boot... but I suspect now that that must have been something I did wrong.

Installed 3.5.0rc6 and your Fn keys patch and now appear to have the best of both worlds.

Still nothing from xbacklight though. Odd. Even "xbacklight -get" returns nothing. Wonder what I've forgotten to do.

Setting brightness to zero & looking at the screen in a dark room should tell you whether it's off or just a screen of black pixels.

Glad to hear more stuff is working :) - I will try to see what I did for the xbacklight to work - I remember I started off with xrandr:

xrandr --output eDP1 --brightness 0.5

dmesg:
```

[    0.000000] e820: BIOS-provided physical RAM map:
[    1.501753] pci 0000:00:02.0: Boot video device
[    3.962522] ACPI Warning: _BQC returned an invalid level (20120320/video-480)
[    3.962716] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    3.962750] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/LNXVIDEO:00/input/input4
[    3.964761] ACPI Warning: _BQC returned an invalid level (20120320/video-480)
[    3.967526] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    3.967558] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5
[   12.297130] asus_wmi: Backlight controlled by ACPI video driver
[   12.409550] Linux video capture interface: v2.00
[   12.414039] uvcvideo: Found UVC 1.00 device USB2.0 HD UVC WebCam (04f2:b330)
[   12.428658] usbcore: registered new interface driver uvcvideo
[   12.428661] USB Video Class driver (1.1.1)

```

/etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nmi_watchdog=0 apparmor=0"

/sys:
```

./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/type
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/control
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/async
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_enabled
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_active_kids
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_active_time
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/autosuspend_delay_ms
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_status
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_usage
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/power/runtime_suspended_time
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/bl_power
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/max_brightness
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/device
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/subsystem
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/uevent
./devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/actual_brightness

```

Maybe the above will help to troubleshoot :)

---

### Post by peter rus on 2012-07-13
Hello,

I have just bought a UX32VD.

I have installed ubuntu 12.04. By default the functionbuttons did not work. (except wifi toggling and screentoggling) I did not test closing the lid nor really listened to the fan.

Then I installed the xorg-edgers repository packages (using a dist-upgrade, that seemed right to me), the buttons still did not work and the fan was whirring constantly (the device is hotter that it would be when running windows). Also when closing the lid the device would not wake up again. (and the fan was kept active). xbacklight nor xrandr work for changing the backlight.

I then proceeded to install the quantal kernel by downloading the latest stable packages from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/)

They would not install as nvidia kernel modules where being rebuilt, which failed.

What would be currently the best configuration (the one screemo uses?) and is the quantal kernel still relevant as 12.04 currently uses a 3.5.0-4 kernel.

If you feel I am missing any points or resources, please point me in their direction.

**edit:** When using the ubuntu default 3.5.0-4 kernel, closing the lid does no properly suspend the device, as stated above, pressing the Fn+F1 does however (fan, keyboard backlight, screen turn off). Pressing the powerbutton does not wake the device up though.

**edit2:** Installed this kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/)
patched it with this: [http://ubuntuforums.org/showpost.php?p=12086401&postcount=27](http://ubuntuforums.org/showpost.php?p=12086401&postcount=27) and having the xorg-edgers repository enabled **the functionbuttons work (without screen brightness) and closing the lid properly suspends the machine it does not wake up however (it does wake up, but not the screen**

**edit3:** Cpu frequency scaling seems to work (it throttles between 800 and 1700 mhz), cant seem to reach turbomode though, no idea how that is activated though.

---

### Post by LudoTW on 2012-07-13
Hello,

This is my first message on the ubuntu forum, and my first test with ubuntu. Well it is not working well for me on the UX32VD. I installed the 32bit which is the one labeled recommended from the download page. I wanted to install it on the SSD. I got rid of windows. And the result is that none of the SSD and the HDD were visible from the BIOS boot options. So, the UX32vd couldn't boot unless a USB was plugged in.
Both HDD and SSD were perfectly visible from the live ubuntu running on my USB.

Now I am going to try to reinstall the 64bits version. Did any one installed it on the SSD? With which partitioning?
Where should the bootloader installed?

This is what I had:
[SIZE=2]On sda:
/dev/sda1 type /biosgrub 100MB
/dev/sda2 type swap 4GB
/dev/sda3 type ext4 : /home

And on sdb:
/dev/sdb1 type /biosgrub 100MB
/dev/sdb2 type ext4 /boot 100MB
/dev/sdb3 type ext4 for my root  /  20GB

And I chose sdb for the device for the bootloader installation from the  dropdown menu:
/dev/sdb ATA sandisk SSD i100

(or should I chose /dev/sdb1 or /dev/sdb2?)

Any help, at this time of the night (1h30 here) would be nice, but I am exhausted now.

Ludo
[/SIZE]

---

### Post by peter rus on 2012-07-13
Hi Ludo,

I am currently running ubuntu entirely from my SSD. You might want to read up on how UEFI works (just as I had to do ;)

what you need to do (this will make your windows installation unbootable, but you did not seem to care about that).

use Unetbootin to create a bootable usb containing 12.04 Live 64-bits (only 64 bits works when using UEFI) (Unetbootin should download it for you)

When booting, press ESC, you should be presented with a bootmenu. Choose the UEFI <your usb stick name> entry. You should see a black/white grub menu with 3 options, select the first, press 'e', change the part where it says 'splash quiet' in 'nomodeset' and press F10. Ubuntu should boot.

Using gparted (from the livecd) create the following on your ssd:

A new **GPT** partition table containing the following (in this order)

a 200mb fat32 partition with the 'boot' flag (and only that flag) set
a ext4 partition for your root filesystem
a 8gb swap partition (twice the size of your ram)

The mount the 200mb partition on your **HDD** not your ssd, and copy everything in that (one folder called EFI containing subfolders) to the 200mb partition on your SSD. You have now moved EFI's support files (what would classicly reside in your master boot record on MBR systems, but this might get a bit too technical) to your SSD.

Proceed with installing, ubuntu (because it is booted in UEFI mode) should now compile a grub efi-program which is installed in that 200mb partition on your SSD.

When you reboot now and press ESC again, there should be at least one 'ubuntu' entry. If there are multiple, try them all, you can use the System Setup menu (F2) to remove entries.

**Edit:** I see you tried to use a biosgrub partition, you do NOT need this

---

### Post by screemo on 2012-07-13
> **peter rus said:**
> Hello,

I have just bought a UX32VD.

I have installed ubuntu 12.04. By default the functionbuttons did not work. (except wifi toggling and screentoggling) I did not test closing the lid nor really listened to the fan.

Then I installed the xorg-edgers repository packages (using a dist-upgrade, that seemed right to me), the buttons still did not work and the fan was whirring constantly (the device is hotter that it would be when running windows). Also when closing the lid the device would not wake up again. (and the fan was kept active). xbacklight nor xrandr work for changing the backlight.

I then proceeded to install the quantal kernel by downloading the latest stable packages from: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.4.4-quantal/)

They would not install as nvidia kernel modules where being rebuilt, which failed.

What would be currently the best configuration (the one screemo uses?) and is the quantal kernel still relevant as 12.04 currently uses a 3.5.0-4 kernel.

If you feel I am missing any points or resources, please point me in their direction.

**edit:** When using the ubuntu default 3.5.0-4 kernel, closing the lid does no properly suspend the device, as stated above, pressing the Fn+F1 does however (fan, keyboard backlight, screen turn off). Pressing the powerbutton does not wake the device up though.

**edit2:** Installed this kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-rc6-quantal/)
patched it with this: [http://ubuntuforums.org/showpost.php?p=12086401&postcount=27](http://ubuntuforums.org/showpost.php?p=12086401&postcount=27) and having the xorg-edgers repository enabled **the functionbuttons work (without screen brightness) and closing the lid properly suspends the machine it does not wake up however (it does wake up, but not the screen**

I had no problems with the suspend/resume (in 12.04 + quantal kernel backport), but in the meantime I switched to quantal development because alot of the subsystems has better support for the laptop.

You dont happen to have an external mouse or other stuff attached that might prevent the laptop from entering sleepmode ?

Only problem I've seen with the resume process is that the background wallpaper is missing (black background). Maybe this is related to the shared framebuffer on optimus - I have no clue.

btw: the Trendnet Gbit TU2-ETG v2.0R (atrix based, like original dongle) works flawlessly on the kernel, giving 60-70mb/sec (should be around 80-100, but still way better than 100mbit).

---

### Post by screemo on 2012-07-13
> **LudoTW said:**
> Hello,

This is my first message on the ubuntu forum, and my first test with ubuntu. Well it is not working well for me on the UX32VD. I installed the 32bit which is the one labeled recommended from the download page. I wanted to install it on the SSD. I got rid of windows. And the result is that none of the SSD and the HDD were visible from the BIOS boot options. So, the UX32vd couldn't boot unless a USB was plugged in.
Both HDD and SSD were perfectly visible from the live ubuntu running on my USB.

Now I am going to try to reinstall the 64bits version. Did any one installed it on the SSD? With which partitioning?
Where should the bootloader installed?

This is what I had:
[SIZE=2]On sda:
/dev/sda1 type /biosgrub 100MB
/dev/sda2 type swap 4GB
/dev/sda3 type ext4 : /home

And on sdb:
/dev/sdb1 type /biosgrub 100MB
/dev/sdb2 type ext4 /boot 100MB
/dev/sdb3 type ext4 for my root  /  20GB

And I chose sdb for the device for the bootloader installation from the  dropdown menu:
/dev/sdb ATA sandisk SSD i100

(or should I chose /dev/sdb1 or /dev/sdb2?)

Any help, at this time of the night (1h30 here) would be nice, but I am exhausted now.

Ludo
[/SIZE]

If possible just install a SSD instead (they are really cheap now). Install a 64bit ubuntu on that, and switch to the quantal backport kernel + updated asus-wmi. It should give you a decent system.

---

### Post by screemo on 2012-07-13
Do any of you guys have a decent configuration for the Elan touchpad in the UX32VD ? 

I have experimented but nothing really gives me a good palmdetection...

Also I think its a mess with the xinput / synclient / utouch - anyone found a good outline of how it fits together ?

I know some of them clash and will fire events twice if set up the same, but short of that I have no experience with them.

---

### Post by screemo on 2012-07-13
Just updated from bios 206 to 207 - works fine (should fix some unneeded spinup of the fans:

[http://nbtsd.asustreiber.de/BIOS/UX32VDAS.207.zip](http://nbtsd.asustreiber.de/BIOS/UX32VDAS.207.zip)

Originally from here:

[http://forum.notebookreview.com/asus/659073-ivy-bridge-zenbook-fhd-ips-screen-ux21a-ux31a-ux32a-ux32vd-229.html](http://forum.notebookreview.com/asus/659073-ivy-bridge-zenbook-fhd-ips-screen-ux21a-ux31a-ux32a-ux32vd-229.html)

---

### Post by dancat on 2012-07-13
> **screemo said:**
> Is it something you are willing to share ?

How about the dpi, does it work reliably with dialogs and all ?


Sure, it is not my work, i have just take it from the internet and adapted it.

```

#!/bin/sh
#
# Monitor Toggle
# The following script toggles between the internal monitor and an external monitor.
#
# Version 1.3
# Export Xauthority and display
USERID="$(cat /var/run/ConsoleKit/database | grep -B 6 is_active=true | grep uid= | cut -f 2 -d '=')"
USER="$(grep $USERID /etc/passwd | cut -f 1 -d ':')"
# USER="$(who | grep :0\) | cut -f 1 -d ' ')"
export XAUTHORITY=/home/$USER/.Xauthority
export DISPLAY=:0
########### Settings ###########
# Use 'xrandr' to find these
DP="DP1"
VGA="VGA1"
HDMI="HDMI1"
INTERNAL_DISPLAY="eDP1"
# Check /sys/class/drm for the exact location
DP_STATUS="$(cat /sys/class/drm/card0-DP-1/status)"
VGA_STATUS="$(cat /sys/class/drm/card0-VGA-1/status)"
HDMI_STATUS="$(cat /sys/class/drm/card0-HDMI-A-1/status)"
# Backlight settings
BACKLIGHT_BATTERY=15
BACKLIGHT_AC=50
# Do no change!
EXTERNAL_DISPLAY=""
# Check to see if the external display is connected
if [ "${DP_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$DP
fi
if [ "${VGA_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$VGA
fi
if [ "${HDMI_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$HDMI
fi
# The external display is connected
if [ "$EXTERNAL_DISPLAY" != "" ]; then
# Set the display settings
  xrandr --output $INTERNAL_DISPLAY --off        # Turn off internal display
  xrandr --output $EXTERNAL_DISPLAY --auto     # Turn on external display
# Set the DPI 
# External monitor definitions:
# physical screen size from xrandr (xorg detection isn't right)
  em_ds_h=$(xrandr | grep $EXTERNAL_DISPLAY | rev | cut -d " " -f 3 | rev | sed 's/mm//')
  em_ds_v=$(xrandr | grep $EXTERNAL_DISPLAY | rev | cut -d " " -f 1 | rev | sed 's/mm//')
  em_ds="$em_ds_h"x"$em_ds_v"

  xrandr --output $EXTERNAL_DISPLAY --fbmm $em_ds
# The external display is not connected
else
# Restore internal display
  if [ "$EXTERNAL_DISPLAY" != "" ]; then
    xrandr --output $EXTERNAL_DISPLAY --off        # Turn off internal display
  fi
  xrandr --output $INTERNAL_DISPLAY --auto
# Set the DPI
# Internal Monitor definition
  im_ds_h=$(xrandr | grep $INTERNAL_DISPLAY | rev | cut -d " " -f 3 | rev | sed 's/mm//')
im_ds_v=$(xrandr | grep $INTERNAL_DISPLAY | rev | cut -d " " -f 1 | rev | sed 's/mm//')
  im_ds="$im_ds_h"x"$im_ds_v"
  xrandr --output $INTERNAL_DISPLAY --fbmm $im_ds
fi
exit 0

```

If you want this to be executed every time when you plug in or out HDMI you will have to create a rule for udev (in /etc/udev/rules) that looks like this:

```

cat /etc/udev/rules.d/99-hdmi.rules 
SUBSYSTEM=="drm", ACTION=="change", RUN+="/usr/local/bin/screendpi"

```

You need of course to change the script path to wherever you created the script.

---

### Post by screemo on 2012-07-13
> **dancat said:**
> Sure, it is not my work, i have just take it from the internet and adapted it.

```

#!/bin/sh
#
# Monitor Toggle
# The following script toggles between the internal monitor and an external monitor.
#
# Version 1.3
# Export Xauthority and display
USERID="$(cat /var/run/ConsoleKit/database | grep -B 6 is_active=true | grep uid= | cut -f 2 -d '=')"
USER="$(grep $USERID /etc/passwd | cut -f 1 -d ':')"
# USER="$(who | grep :0\) | cut -f 1 -d ' ')"
export XAUTHORITY=/home/$USER/.Xauthority
export DISPLAY=:0
########### Settings ###########
# Use 'xrandr' to find these
DP="DP1"
VGA="VGA1"
HDMI="HDMI1"
INTERNAL_DISPLAY="eDP1"
# Check /sys/class/drm for the exact location
DP_STATUS="$(cat /sys/class/drm/card0-DP-1/status)"
VGA_STATUS="$(cat /sys/class/drm/card0-VGA-1/status)"
HDMI_STATUS="$(cat /sys/class/drm/card0-HDMI-A-1/status)"
# Backlight settings
BACKLIGHT_BATTERY=15
BACKLIGHT_AC=50
# Do no change!
EXTERNAL_DISPLAY=""
# Check to see if the external display is connected
if [ "${DP_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$DP
fi
if [ "${VGA_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$VGA
fi
if [ "${HDMI_STATUS}" = connected ]; then
 EXTERNAL_DISPLAY=$HDMI
fi
# The external display is connected
if [ "$EXTERNAL_DISPLAY" != "" ]; then
# Set the display settings
  xrandr --output $INTERNAL_DISPLAY --off        # Turn off internal display
  xrandr --output $EXTERNAL_DISPLAY --auto     # Turn on external display
# Set the DPI 
# External monitor definitions:
# physical screen size from xrandr (xorg detection isn't right)
  em_ds_h=$(xrandr | grep $EXTERNAL_DISPLAY | rev | cut -d " " -f 3 | rev | sed 's/mm//')
  em_ds_v=$(xrandr | grep $EXTERNAL_DISPLAY | rev | cut -d " " -f 1 | rev | sed 's/mm//')
  em_ds="$em_ds_h"x"$em_ds_v"

  xrandr --output $EXTERNAL_DISPLAY --fbmm $em_ds
# The external display is not connected
else
# Restore internal display
  if [ "$EXTERNAL_DISPLAY" != "" ]; then
    xrandr --output $EXTERNAL_DISPLAY --off        # Turn off internal display
  fi
  xrandr --output $INTERNAL_DISPLAY --auto
# Set the DPI
# Internal Monitor definition
  im_ds_h=$(xrandr | grep $INTERNAL_DISPLAY | rev | cut -d " " -f 3 | rev | sed 's/mm//')
im_ds_v=$(xrandr | grep $INTERNAL_DISPLAY | rev | cut -d " " -f 1 | rev | sed 's/mm//')
  im_ds="$im_ds_h"x"$im_ds_v"
  xrandr --output $INTERNAL_DISPLAY --fbmm $im_ds
fi
exit 0

```

If you want this to be executed every time when you plug in or out HDMI you will have to create a rule for udev (in /etc/udev/rules) that looks like this:

```

cat /etc/udev/rules.d/99-hdmi.rules 
SUBSYSTEM=="drm", ACTION=="change", RUN+="/usr/local/bin/screendpi"

```

You need of course to change the script path to wherever you created the script.

Thanks I will try it out :)

---

### Post by LudoTW on 2012-07-13
Hi Peter, all,

Thank you for your advices. I have few questions though:

> **peter rus said:**
> 
I am currently running ubuntu entirely from my SSD.


With a /home on the HDD?

> 
 You might want to read up on how UEFI works (just as I had to do ;)
Yes :), I have begun:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

> 
what you need to do (this will make your windows installation unbootable, but you did not seem to care about that).
So you don't have any more the option to boot windows, or you used another method to be able to boot windows?

> 
Using gparted (from the livecd) create the following on your ssd:
A new **GPT** partition table containing the following (in this order)
a 200mb fat32 partition with the 'boot' flag (and only that flag) set
a ext4 partition for your root filesystem
a 8gb swap partition (twice the size of your ram)
I read somewhere that it wasn't a good idea to have the swap on the SSD. I  didn't find out why but I suppose it will stress the SSD a lot. What do  you think? On the other hand many linuxes are installed on SSD and I never heard about any issue. Or is that this particular soldered-on SSD which wouldn't be good for a swap?

> 
The mount the 200mb partition on your **HDD** not your ssd, and copy everything in that (one folder called EFI containing subfolders) to the 200mb partition on your SSD. You have now moved EFI's support files (what would classicly reside in your master boot record on MBR systems, but this might get a bit too technical) to your SSD.
Here I got lost. To which point should I mount the SSD 200mb partition? Simply /dev/sda? And what is the "evertyhing" you mention about?

Ludo

---

### Post by peter rus on 2012-07-14
> **LudoTW said:**
> 
With a /home on the HDD?


That is my plan in the future, but currently the HDD is occupied with windows (which still boots by selecting it from the UEFI 'bios' bootmenu)

> **LudoTW said:**
> 
I read somewhere that it wasn't a good idea to have the swap on the SSD. I  didn't find out why but I suppose it will stress the SSD a lot. What do  you think? On the other hand many linuxes are installed on SSD and I never heard about any issue. Or is that this particular soldered-on SSD which wouldn't be good for a swap?


Good point indeed, although the device has 4gb of ram so shouldn't have to do too much swapping, I am not sure what the expected lifespan of the SDD is but if it breaks within your waranty you can't replace it, so it wouldn't be a bad idea to be careful with it ;) I might move swap to the HDD when I set up my home partition.

> **LudoTW said:**
> 
Here I got lost. To which point should I mount the SSD 200mb partition? Simply /dev/sda? And what is the "evertyhing" you mention about?


I simply made two mountpoints in my home directory called 'a' and 'b', something more descriptive like 'HDD-EFI' and 'SDD-EFI' might be a bit more helpful though. However when you have the factory default 
efi partition on the HDD ubuntu should properly install to that, automaticly. This did not work in my case as I forgot to boot in UEFI mode, so it might in your case.

**Edit:** Note that I am doing all this while running the livecd ;) on your installed system the efi partition which ubuntu booted from is automaticly mounted at /boot/efi, this might also happen on the livecd, but it can't do any harm to mount something twice

**Edit 2:** About the home partition: a home partition on such a small SDD is useless of course, but currently I am first trying to focus on gettin a stable system running

---

### Post by LudoTW on 2012-07-14
I have no network device (no wireless no BT) at all after updating to kernel 3.4.4 following these instructions:

[how to install 3.4.4 in ubuntu 12.04]("http://www.thelinuxgeeks.info/how-to-install-linux-3-4-4-quantal-kernel-in-ubuntu-12-10-2/2/")
Why is it so?
Or should I actually compile the kernel as mentioned at the bottom of [this page]("https://help.ubuntu.com/community/AsusZenbook")?

Peter, Thanks for all these good pieces of information.

In the meantime I have reinstalled windows (using backups i had made) on the HDD, and ubuntu 12.04 on the SSD with swap there as you did. So may change that too someday :)

---

### Post by 9rift on 2012-07-14
Hi guys,
As i said, i ordered that ultrabook and just got is yesterday :)
I'm here, but actually i never run ubuntu... but i'am on this forum because sometimes i get really useful informa tion because of your big users database.
I'm more a Fedora user, and actually, everytihng (expect keyboard backlight) work fine out of the box.

I installed Fedora on the 32GB SSD, i only created a 20GB for /, no swap(because 4GB of RAM is too big for my usage, and SSD disk dont like too much R/W) and a 12GB for my home
I have to say, **blacklight != brightness** !!

For the wifi you will need : iwlwifi last firmware
source: [http://www.linlap.com/wiki/asus+ux32v](http://www.linlap.com/wiki/asus+ux32v)

I comiled and used bbswitch to disable the nvidia discret card, and all is ok

If you got other thing not working on your ubuntu, tell me, i will investigate why that's working for me !
cheers !

---

### Post by liveag on 2012-07-14
Had everything (except for display backlight keys) working on Ubuntu Precise with the 3.5 kernel from the xorg-edgers repo.
Now I've switched to Arch (kernel 3.4.4-3), and none of the keys are working.
According to the wiki page they should, weirdly. I'm wary of upgrading my kernel because of possible incompatibilities with the modules, dunno what to do now.
(No, I won't install Ubuntu again. I don't really like it. It was just the only thing that worked in the beginning)

---

### Post by peter rus on 2012-07-15
I have currently installed the latest development version of quantal. With the asus-wmi patch all functionbuttons work (except brightness of course). Wifitoggling might give a kernal panic. 

Bumblebee to turn off the discrete GPU, battery life is still far from optimal.

VGA Output works as expected, HDMI not however, I am using nvidia-current

**Edit** Vga does not work after all, might have to with the fact that I am not using nouveau, will test now.

**Edit2:** @Screemo, palm detection is indeed not working, quite a must if you ask me ;)

**Edit 3:** In case people have no files in /sys/class/drm/ (or only a 'version' file), you are probably using nouveau, you will need the nvidia drivers. On ubuntu 12.04 + xorg-edgers/x-swat + **mainline** quantal 3.5 rc6/7, these do not seem to work on my UX32VD

---

### Post by peter rus on 2012-07-15
> **screemo said:**
> Thanks I will try it out :)

My /sys/class/drm/ folder only contains 'version'. Does this have to do with the fact that I am not using nouveau?. Also nvidia-settings reports that I am not using nvidia drivers. the nvidia module is loaded however when I look at lsmod

**Edit: Warning: I see people (including myself) upgrading to 'mainline' kernels, these are NOT the same as the kernels included in the ubuntu distributions, if you want a quantal kernel, you should probably get it from the quantal repository. Mainline kernels are unmodified kernels, so no ubuntu patches (which you might just need to use nvidia drivers for example) . This might just be the cause for a lot of my troubles. I will report later.**

---

### Post by peter rus on 2012-07-15
> **liveag said:**
> Had everything (except for display backlight keys) working on Ubuntu Precise with the 3.5 kernel from the xorg-edgers repo.
Now I've switched to Arch (kernel 3.4.4-3), and none of the keys are working.
According to the wiki page they should, weirdly. I'm wary of upgrading my kernel because of possible incompatibilities with the modules, dunno what to do now.
(No, I won't install Ubuntu again. I don't really like it. It was just the only thing that worked in the beginning)

I am afraid you are now in the hands of the Arch forum (which is not a bad thing perse)

---

### Post by peter rus on 2012-07-15
Installing the current quantal development build + asus-wmi patch + bumblebee get the following working:

* VGA
* all functionbuttons F1-F12 function buttons except F5 and F6
* suspend and resume
* brightness changing
* USB Ethernet adapter

The following does not work:

* Actually using the discrete GPU for 3D rendering (No-one has been able to do that yet, it seems)
* HDMI (cat /sys/class/drm/card0-HDMI-A-1/status keeps reporting 'disconnecting')
* Changing brightness through F5 and F6
* Wifi statusled (it often gives the opposite status), but it seems controllable through the drivers, so thats a good start.
* Changing touchpad sensitivy, Acceleration does work though

Taking into account that bumblebee should turns off the nvidia card the system consumes around 16Watts at maximum brightness. Will try to tune this further with instructions on the wiki ([https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime))

**Edit: ** After enabling ALPM ([https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)) and adding the following to the kernel parameters: pcie_aspm=force drm.vblankoffdelay=1 the system pulls only 10-11 Watts. A fair improvement. I did not use 'i915.semaphores=1' because this gave me a nice kernel panic at every boot.

A description of this parameter:

> Semaphores are not enabled by default on all generation of graphics cards. Enablement of semaphores solves several stability issues on Ivy Bridge graphics cards, such as GPU hangs, and improved stability and performance on Sandy Bridge generation of graphics cards. The drawbacks are occasional stability issues on some systems with VTd enabled. Semaphores can be enabled manualy via the i915.semaphores=1 kernel parameter. 

All of this was tested at 100% brightness with both bluetooth and wifi radio on

Seems like something desirable! (source: intellinuxgraphics.org/2011Q4.html)

Some powertop tunables:

[http://i.imgur.com/CXzTu.png](http://i.imgur.com/CXzTu.png)

**Edit 2:**I disabled the NMI watchdog with nmi_watchdog=0 as per powertop's suggestion. Any thoughts on how to permanently accomplish the other suggestions powertop gives?

**Edit 3:** When plugging in a HDMI cable i get the following in syslog:

> Jul 16 03:59:26 host kernel: [ 1739.736042] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 155
Jul 16 03:59:26 host kernel: [ 1739.736050] Raw EDID:
Jul 16 03:59:26 host kernel: [ 1739.736054]  	00 ff ff ff ff ff ff 00 4c 2d d2 07 38 34 30 30
Jul 16 03:59:26 host kernel: [ 1739.736059]  	24 15 01 03 80 30 1b 78 2a 90 c1 a2 59 55 9c 27
Jul 16 03:59:26 host kernel: [ 1739.736062]  	0e 50 54 bf ef 80 71 4f 81 00 81 40 81 80 95 00
Jul 16 03:59:26 host kernel: [ 1739.736065]  	95 0f a9 40 b3 00 02 3a 80 18 71 38 2d 40 58 2c
Jul 16 03:59:26 host kernel: [ 1739.736068]  	ff ff ff ff ff ff ff ff 01 1d 00 72 51 d0 1e 20
Jul 16 03:59:26 host kernel: [ 1739.736071]  	6e 28 55 00 dd 0c 11 00 00 1e 00 00 00 fd 00 32
Jul 16 03:59:26 host kernel: [ 1739.736073]  	4b 1f 51 11 00 0a 20 20 20 20 20 20 00 00 00 fc
Jul 16 03:59:26 host kernel: [ 1739.736076]  	00 53 4d 53 32 32 41 33 35 30 48 0a 20 20 01 e1
Jul 16 03:59:26 host kernel: [ 1739.736085] i915 0000:00:02.0: HDMI-A-1: EDID block 0 invalid.


This might be a bug, but as I am running alpha software, would there possibly be any place to report this?

I understand something goes wrong with the handshake between my monitor and the graphics card, might try this on another monitor.

**If there are any developers in need of testing, please contact me**

---

### Post by screemo on 2012-07-16
> **peter rus said:**
> Installing the current quantal development build + asus-wmi patch + bumblebee get the following working:

* VGA
* all functionbuttons F1-F12 function buttons except F5 and F6
* suspend and resume
* brightness changing
* USB Ethernet adapter

The following does not work:

* Actually using the discrete GPU for 3D rendering (No-one has been able to do that yet, it seems)
* HDMI (cat /sys/class/drm/card0-HDMI-A-1/status keeps reporting 'disconnecting')
* Changing brightness through F5 and F6
* Wifi statusled (it often gives the opposite status), but it seems controllable through the drivers, so thats a good start.
* Changing touchpad sensitivy, Acceleration does work though

Taking into account that bumblebee should turns off the nvidia card the system consumes around 16Watts at maximum brightness. Will try to tune this further with instructions on the wiki ([https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime))

**Edit: ** After enabling ALPM ([https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)) and adding the following to the kernel parameters: pcie_aspm=force drm.vblankoffdelay=1 the system pulls only 10-11 Watts. A fair improvement. I did not use 'i915.semaphores=1' because this gave me a nice kernel panic at every boot.

A description of this parameter:



All of this was tested at 100% brightness with both bluetooth and wifi radio on

Seems like something desirable! (source: intellinuxgraphics.org/2011Q4.html)

Some powertop tunables:

[http://i.imgur.com/CXzTu.png](http://i.imgur.com/CXzTu.png)

**Edit 2:** Re-adding i915.semaphores=1 now works, for some reason I get o more kernel panics, furthermore I disabled the NMI watchdog with nmi_watchdog=0 as per powertop's suggestion. Any thoughts on how to permanently accomplish the other suggestions powertop gives?

**Edit 3:** When plugging in a HDMI cable i get the following in syslog:



This might be a bug, but as I am running alpha software, would there possibly be any place to report this?

I understand something goes wrong with the handshake between my monitor and the graphics card, might try this on another monitor.

**If there are any developers in need of testing, please contact me**

I just tried plugging HDMI to my Benq 24fpw, it works but only on 1080p resolution. 

I just used the "display-thing" in gnome (uses xrandr i think) 

Don't you get any output?

---

### Post by peter rus on 2012-07-16
> **screemo said:**
> I just tried plugging HDMI to my Benq 24fpw, it works but only on 1080p resolution. 

I just used the "display-thing" in gnome (uses xrandr i think) 

Don't you get any output?

On my Samsung monitor (Not near it right now, will post type later) I get these EDID errors, so it might be a quirk related to that monitor (it works on windows and OSX though). I have a Sony Bravia KDL-26U2000 TV here which detects a PC is connected (and ubuntu also detects the monitor) but then displays nothing.

---

### Post by x_O on 2012-07-16
> **bambam23 said:**
> 
Except for wifi. i really have issues connecting to the AP if its set to b/g/n with auto-channel selection. if i set it to b/g with fixed channel

Any new ideas how to overcome this issue? I've tried to setup 11n_disable=1 but sadly didn't work.

---

### Post by peter rus on 2012-07-16
For those having problems with white menus in the tray:

[http://ubuntuforums.org/showpost.php?p=12105784&postcount=3](http://ubuntuforums.org/showpost.php?p=12105784&postcount=3)

---

### Post by screemo on 2012-07-16
> **peter rus said:**
> I have currently installed the latest development version of quantal. With the asus-wmi patch all functionbuttons work (except brightness of course). Wifitoggling might give a kernal panic. 

Bumblebee to turn off the discrete GPU, battery life is still far from optimal.

VGA Output works as expected, HDMI not however, I am using nvidia-current

**Edit** Vga does not work after all, might have to with the fact that I am not using nouveau, will test now.

**Edit2:** @Screemo, palm detection is indeed not working, quite a must if you ask me ;)

**Edit 3:** In case people have no files in /sys/class/drm/ (or only a 'version' file), you are probably using nouveau, you will need the nvidia drivers. On ubuntu 12.04 + xorg-edgers/x-swat + **mainline** quantal 3.5 rc6/7, these do not seem to work on my UX32VD

It seems like this fixes some of the palm detection:

xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 100

Apparently the gpointing-device-settings app does not support lowerimg them so much its noticable on the Elan touchpad.

Found the tip here: [http://superuser.com/questions/277427/making-synaptics-palm-detection-work-under-ubuntu-11-04](http://superuser.com/questions/277427/making-synaptics-palm-detection-work-under-ubuntu-11-04)


EDIT: xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 1 seems alot more effective

source: [http://ubuntuguide.net/multi-touch-ubuntu-12-04-hp](http://ubuntuguide.net/multi-touch-ubuntu-12-04-hp)

---

### Post by peter rus on 2012-07-16
> **screemo said:**
> It seems like this fixes some of the palm detection:

xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 100

Apparently the gpointing-device-settings app does not support lowerimg them so much its noticable on the Elan touchpad.

Found the tip here: [http://superuser.com/questions/277427/making-synaptics-palm-detection-work-under-ubuntu-11-04](http://superuser.com/questions/277427/making-synaptics-palm-detection-work-under-ubuntu-11-04)


EDIT: xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 1 seems alot more effective

source: [http://ubuntuguide.net/multi-touch-ubuntu-12-04-hp](http://ubuntuguide.net/multi-touch-ubuntu-12-04-hp)

I can confirm this works, however, scrolling is still possible when a palm is detected.

Are you able to use 3 finger gestures? and things like pinch and zoom?

I am currently experiencing odd behaviour: When I scroll using 2 fingers (which works fine by the way) and I accidentally touch the touchpad with a third finger my current focused window becomes un-maximized.

---

### Post by peter rus on 2012-07-16
Got it! In addition to screemo's command you will need synclient PalmDetect=1

So to enable proper palmdetection:

> 
synclient PalmDetect=1
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 1 


This is probably not preserved over reboots

We should seriously think about updating the wiki with all our findings ;)

Furtermore, I wonder if these things should be reported as bugs somewhere. Anyone with a definitive answer on that?

I can say, that in the short time I have tested the palmdetection it works absolutely proper!

---

### Post by asiandub on 2012-07-16
> 
We should seriously think about updating the wiki with all our findings ;)

Yes please. It would save people like me the time to go through each and every post of this thread to extract the maybe-valuable information.

---

### Post by bambam23 on 2012-07-17
> **x_O said:**
> Any new ideas how to overcome this issue? I've tried to setup 11n_disable=1 but sadly didn't work.

sorry for my late report. for me disabling n networks is working really good, i'm getting almost the entire bandwidth possible in b/g networks, respectivly to the encryption overhead.

---

### Post by x_O on 2012-07-17
> **bambam23 said:**
> sorry for my late report. for me disabling n networks is working really good, i'm getting almost the entire bandwidth possible in b/g networks, respectivly to the encryption overhead.

This may be really different issue, but i did this bit. Didn't work. 

```
sudo rmmod iwlwifi && sudo modprobe iwlwifi 11n_disable=1
```

this what I've got (AP is not manageable by me) 

```

Cell 24 - Address: 01:1b:1e:26:2b:85
       Channel:60
       Frequency:5.3 GHz (Channel 60)
       Quality=52/70  Signal level=-58 dBm  
       Encryption key:off
       ESSID:"NetworkAP"
       Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                 36 Mb/s; 48 Mb/s; 54 Mb/s
       Mode:Master
       Extra:tsf=000000931740a591
       Extra: Last beacon: 2056ms ago
```

---

### Post by screemo on 2012-07-17
> **peter rus said:**
> Got it! In addition to screemo's command you will need synclient PalmDetect=1

So to enable proper palmdetection:



This is probably not preserved over reboots

We should seriously think about updating the wiki with all our findings ;)

Furtermore, I wonder if these things should be reported as bugs somewhere. Anyone with a definitive answer on that?

I can say, that in the short time I have tested the palmdetection it works absolutely proper!

Cool, I will try this :)

PS: to preserve over reboots, just add the lines to ~/.xsessionrc

---

### Post by SveinT on 2012-07-17
Until the brightness Fn buttons work, I can highly recommend indicator-brightness. Works perfectly (you can use mouse scrollwheel when hovering the indicator).

[http://codevanrohde.nl/wordpress/?p=128](http://codevanrohde.nl/wordpress/?p=128)

---

### Post by peter rus on 2012-07-17
I found a 'better' way to persist the palmdetection settings.

1. create a new file in /usr/share/X11/xorg.conf.d/ called '52-asus-zenbook-synaptics.conf'
2. Paste the following in it
```

# Example xorg.conf.d snippet that assigns the touchpad driver
# to all touchpads. See xorg.conf.d(5) for more information on
# InputClass.
# DO NOT EDIT THIS FILE, your distribution will likely overwrite
# it when updating. Copy (and rename) this file into
# /etc/X11/xorg.conf.d first.
# Additional options may be added in the form of
#   Option "OptionName" "value"
#
Section "InputClass"
        Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
# This option is recommend on all Linux systems using evdev, but cannot be
# enabled by default. See the following link for details:
# http://who-t.blogspot.com/2010/11/how-to-ignore-configuration-errors.html
      MatchDevicePath "/dev/input/event*"
	Option      "CircularScrolling"          "on"
	Option      "CircScrollTrigger"          "0"
	Option      "PalmDetect"                 "on"
	Option "PalmMinWidth" "4"
	Option "PalmMinZ" "1"
EndSection

Section "InputClass"
        Identifier "touchpad ignore duplicates"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/mouse*"
        Option "Ignore" "on"
EndSection

# This option enables the bottom right corner to be a right button on
# non-synaptics clickpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Default clickpad buttons"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
EndSection

# This option disables software buttons on Apple touchpads.
# This option is only interpreted by clickpads.
Section "InputClass"
        Identifier "Disable clickpad buttons on Apple touchpads"
        MatchProduct "Apple|bcm5974"
        MatchDriver "synaptics"
        Option "SoftButtonAreas" "0 0 0 0 0 0 0 0"
EndSection

```

3. save it, reboot, and you should have:

* Palmdetection
* Circular scrolling (a personal preference of mine, google it ;)

---

### Post by peter rus on 2012-07-17
> **SveinT said:**
> Until the brightness Fn buttons work, I can highly recommend indicator-brightness. Works perfectly (you can use mouse scrollwheel when hovering the indicator).

[http://codevanrohde.nl/wordpress/?p=128](http://codevanrohde.nl/wordpress/?p=128)

The script (and its updated version) fails with 

```
** (gsd-backlight-helper:3487): WARNING **: failed to find any devices

** (gsd-backlight-helper:3489): WARNING **: failed to find any devices
Traceback (most recent call last):
  File "/usr/bin/indicator-brightness", line 93, in <module>
    create_menu(ind)
  File "/usr/bin/indicator-brightness", line 60, in create_menu
    curr_brightness = get_curr_brightness()
  File "/usr/bin/indicator-brightness", line 38, in get_curr_brightness
    curr_brightness = int(p.communicate()[0])
ValueError: invalid literal for int() with base 10: ''

```

---

### Post by peter rus on 2012-07-17
Again no files (except 'version') in /sys/class/drm and the system won't boot properly (hangs on a purple screen) unless I start the recovery mode and then resume boot (which sometimes gives a 'swapper' related stacktrace.

---

### Post by bambam23 on 2012-07-18
> **x_O said:**
> This may be really different issue, but i did this bit. Didn't work. 

```
sudo rmmod iwlwifi && sudo modprobe iwlwifi 11n_disable=1
```

this what I've got (AP is not manageable by me) 

```

Cell 24 - Address: 01:1b:1e:26:2b:85
       Channel:60
       Frequency:5.3 GHz (Channel 60)
       Quality=52/70  Signal level=-58 dBm  
       Encryption key:off
       ESSID:"NetworkAP"
       Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                 36 Mb/s; 48 Mb/s; 54 Mb/s
       Mode:Master
       Extra:tsf=000000931740a591
       Extra: Last beacon: 2056ms ago
```

yes, this really seems to be a totally different case, cause i'm on 2.4GHz band only, and i've never tried the 5Ghz one. i don't know, if disabling n on a 5GHz band is a good idea at all. maybe there's someone else here, who can help you out with a 5GHz AP!?

---

### Post by peter rus on 2012-07-18
> **bambam23 said:**
> yes, this really seems to be a totally different case, cause i'm on 2.4GHz band only, and i've never tried the 5Ghz one. i don't know, if disabling n on a 5GHz band is a good idea at all. maybe there's someone else here, who can help you out with a 5GHz AP!?

I am not entirely following this, but I am connected to a N accesspoint and this seems to work properly

---

### Post by peter rus on 2012-07-18
**Warning: You might nog want to update when running quantal, doing so has removed my ability to change brightness**

Something in quantal probably broke.

**Edit:** Suspend/resume is also defective, which always seems to happen in conjuction with brightness being defective. Using xorg-edgers makes no difference.

---

### Post by maroony on 2012-07-18
> 
synclient PalmDetect=1
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Palm Dimensions" 4 1


This works pretty good, but for me the following works a bit better:

```

killall syndaemon
syndaemon -i 1.7 -d -t
```

That mean's that all clicks are disabled for 1.7 seconds. Maybe the best setting is a combination of both.

Btw, I'm using kernel 3.4.4 (mainline-kernel).

---

### Post by peter rus on 2012-07-19
@ Maroony, will try that later, but first:

I have tracked down the source of my system not booting and the kernel panics:

the asus-wmi patch ([http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719))

When I boot, the process hangs forever in the dotted ubuntu splash. When I boot in recovery mode however, and then choose 'resume boot' everything works fine. This might have to do with some race condition occuring, but thats up to the programmers ;)

When I booted through the recovery mode method the asus-wmi module works (I can use the functionbuttons) but for some reason this also prevents DRM from properly loading, and thus /sys/class/drm/ is not populated, which in turn means you can not use external monitors, waking from suspend does not work (screen stays black, with no way to turn it back on) and setting the brightness of the screen is not possible through the gnome-settings or xbacklight/xrandr. The intel_backlight utility hoewever still works. 

I am booting from an SSD so people using the HDD as root might not have this problem. If you want to remove the patched asus-wmi module, run the following:

```
sudo dkms remove asus-wmi/999.01 --all
```

I added some entries to the wiki: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27)

**Furthermore: also see my entry on nomodeset, when I boot using nomodeset I get exactly the same issues as described above.** I also updated the wiki about it: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=29&rev1=28](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=29&rev1=28)

---

### Post by SveinT on 2012-07-19
I can confirm the suspend problem (on Quantal).

Running the 3.5.0-5 kernel, I sometimes have the 40 sec hang at login, sometimes not. Haven't been able to track down why. Suspend seems to work when there is only a short interval (<10min?) between use. For longer periods the screen is just black, but fans are spinning, and a cold reboot is necessary (tried various Fn keys and changing tty).

Brightness works 100% the time here using the mentioned indicator.

Is there somewhere we can report these findings?

---

### Post by peter rus on 2012-07-19
> **SveinT said:**
> I can confirm the suspend problem (on Quantal).

Running the 3.5.0-5 kernel, I sometimes have the 40 sec hang at login, sometimes not. Haven't been able to track down why. Suspend seems to work when there is only a short interval (<10min?) between use. For longer periods the screen is just black, but fans are spinning, and a cold reboot is necessary (tried various Fn keys and changing tty).

Brightness works 100% the time here using the mentioned indicator.

Is there somewhere we can report these findings?

Probably send a mail to the mailinglist I linked earlier ([http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)). Not sure though, I have never really filed anything against the kernel.

The problems you describe do exactly match the issues I have.

---

### Post by screemo on 2012-07-20
> **peter rus said:**
> Probably send a mail to the mailinglist I linked earlier ([http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)). Not sure though, I have never really filed anything against the kernel.

The problems you describe do exactly match the issues I have.

I dont have problems with suspend on quantal, had it suspended most of a day, and woke up fine after. The only issue is that the wallpaper is not restored (get a black screen). Everything else is working though.

Are you having some extra usb-devices plugged in that may cause it not to wake up maybe ?

---

### Post by SveinT on 2012-07-20
> **screemo said:**
> I dont have problems with suspend on quantal, had it suspended most of a day, and woke up fine after. The only issue is that the wallpaper is not restored (get a black screen). Everything else is working though.

Are you having some extra usb-devices plugged in that may cause it not to wake up maybe ?

What kernel are you running?

I only have a wireless mouse dongle, I'll try without later, but I don't have high hopes...

---

### Post by screemo on 2012-07-20
> **SveinT said:**
> What kernel are you running?

I only have a wireless mouse dongle, I'll try without later, but I don't have high hopes...

I'm talking about suspend to ram btw, haven't tried suspend to disk at all.

---

### Post by SveinT on 2012-07-20
> **screemo said:**
> I'm talking about suspend to ram btw, haven't tried suspend to disk at all.

Not much point in hibernation when suspend battery life is so good.

Are you running the latest kernel (3.5.0-5)? Are you using any extra repos (for instance xorg-edgers)?

---

### Post by screemo on 2012-07-20
> **SveinT said:**
> Not much point in hibernation when suspend battery life is so good.

Are you running the latest kernel (3.5.0-5)? Are you using any extra repos (for instance xorg-edgers)?

Just realized I had 3.5.0-4 - but I have installed 3.5.0-5 now and could suspend it briefly(~5min). I will leave it overnight and wake it up tommorow. Be back with the results.

Sorry for the confusion :)

This is the repos I have (nothing fancy) :

bumblebee-stable-quantal.list
medibuntu.list
trebelnik-stefina-multisystem-quantal.list
webapps-preview-quantal.list

---

### Post by screemo on 2012-07-20
> **peter rus said:**
> @ Maroony, will try that later, but first:

I have tracked down the source of my system not booting and the kernel panics:

the asus-wmi patch ([http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719))

When I boot, the process hangs forever in the dotted ubuntu splash. When I boot in recovery mode however, and then choose 'resume boot' everything works fine. This might have to do with some race condition occuring, but thats up to the programmers ;)

When I booted through the recovery mode method the asus-wmi module works (I can use the functionbuttons) but for some reason this also prevents DRM from properly loading, and thus /sys/class/drm/ is not populated, which in turn means you can not use external monitors, waking from suspend does not work (screen stays black, with no way to turn it back on) and setting the brightness of the screen is not possible through the gnome-settings or xbacklight/xrandr. The intel_backlight utility hoewever still works. 

I am booting from an SSD so people using the HDD as root might not have this problem. If you want to remove the patched asus-wmi module, run the following:

```
sudo dkms remove asus-wmi/999.01 --all
```

I added some entries to the wiki: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=28&rev1=27)

**Furthermore: also see my entry on nomodeset, when I boot using nomodeset I get exactly the same issues as described above.** I also updated the wiki about it: [https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=29&rev1=28](https://help.ubuntu.com/community/AsusZenbookPrime?action=diff&rev2=29&rev1=28)

Ah - could you try the to add rootdelay=<secs> , I've seen this work somewhere else where disk timing was an issue (a longshot I know..).

---

### Post by MartinMorrison on 2012-07-20
Hi,

Just installed the latest Ubuntu on my Zenbook Prime. The worst problem i'm having is my wifi internet is really slow. I've used 3  different laptops on this network wifi and the Zenbook is always much slower. Sometimes it speeds up for 1-2 mins but it always drops back to almost no pages loading. It isn't reconnecting/disconnecting from the network and it has the same wireless signal strength as the other laptops - any ideas at how I can fix this? I basically cant use the internet on it.

---

### Post by screemo on 2012-07-20
> **MartinMorrison said:**
> Hi,

Just installed the latest Ubuntu on my Zenbook Prime. The worst problem i'm having is my wifi internet is really slow. I've used 3  different laptops on this network wifi and the Zenbook is always much slower. Sometimes it speeds up for 1-2 mins but it always drops back to almost no pages loading. It isn't reconnecting/disconnecting from the network and it has the same wireless signal strength as the other laptops - any ideas at how I can fix this? I basically cant use the internet on it.

Please try this from a terminal:

# sudo rmmod iwlwifi && modprobe iwlwifi 11n_disable=1

If it works for you, make the changes permanent this way:

# sudo vi /etc/modprobe.d/iwlwifi-disable11n.conf

Add this to the file, and save it (:wq)
```

options iwlwifi 11n_disable=1

```

---

### Post by screemo on 2012-07-21
> **peter rus said:**
> Probably send a mail to the mailinglist I linked earlier ([http://comments.gmane.org/gmane.linux.kernel/1315719](http://comments.gmane.org/gmane.linux.kernel/1315719)). Not sure though, I have never really filed anything against the kernel.

The problems you describe do exactly match the issues I have.

I can confirm that the 3.5.0-5 cant suspend properly, had to forcibly turn off the computer and start it again.

I will see if I can report this on launchpad.

EDIT: Reported this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380), please comment if you have more details.

---

### Post by MartinMorrison on 2012-07-21
> **screemo said:**
> Please try this from a terminal:

# sudo rmmod iwlwifi && modprobe iwlwifi 11n_disable=1

If it works for you, make the changes permanent this way:

# sudo vi /etc/modprobe.d/iwlwifi-disable11n.conf

Add this to the file, and save it (:wq)
```

options iwlwifi 11n_disable=1

```

Hi thanks. When I try that I get a FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.kob): Operation not permitted 

If I try a second time I get ERROR: Module iwlwifi does not exist in /proc/modules

Oh and now my laptop doesn't pick up any wireless networks since running that command so internet is completely broke...

---

### Post by Chubbs[] on 2012-07-21
Is there any update or a fix to the launcher icons disappearing after enabling the edgers repos?

Any ideas on what is causing this? I would love to help but I am a complete linux noob, I could submit some debugging info if needed.

---

### Post by SveinT on 2012-07-22
> **'Chubbs[] said:**
> Is there any update or a fix to the launcher icons disappearing after enabling the edgers repos?

Any ideas on what is causing this? I would love to help but I am a complete linux noob, I could submit some debugging info if needed.

As stated in the PPA, they're already aware of it and the cause (something in MESA?), so you will just have to wait for them to sort it out.

---

### Post by screemo on 2012-07-22
> **MartinMorrison said:**
> Hi thanks. When I try that I get a FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-25-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.kob): Operation not permitted 

If I try a second time I get ERROR: Module iwlwifi does not exist in /proc/modules

Oh and now my laptop doesn't pick up any wireless networks since running that command so internet is completely broke...

sorry, my mistake you can execute them one at a time instead:

# sudo rmmod iwlwifi
# sudo modprobe iwlwifi 11n_disable=0

---

### Post by peter rus on 2012-07-24
> **SveinT said:**
> As stated in the PPA, they're already aware of it and the cause (something in MESA?), so you will just have to wait for them to sort it out.

In the meantime you can use the unity-2d session (in the login screen, click the ubuntu icon near your username)

---

### Post by peter rus on 2012-07-24
> **screemo said:**
> I can confirm that the 3.5.0-5 cant suspend properly, had to forcibly turn off the computer and start it again.

I will see if I can report this on launchpad.

EDIT: Reported this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380), please comment if you have more details.

There is an option in the bios that allows you to disable deep sleep powersaving. Try disabling this and see if this works. Might want to add that info to the bugreport. I am on 12.04 now with xorg-edgers repo's. Might add to the bugreport.

I am currently trying this now, and see if makes any difference.

** Edit: linux (3.5.0-6.6) quantal-proposed should have this fixed (source [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027828))** not sure yet what to install to test it.

---

### Post by peter rus on 2012-07-24
> **screemo said:**
> I can confirm that the 3.5.0-5 cant suspend properly, had to forcibly turn off the computer and start it again.

I will see if I can report this on launchpad.

EDIT: Reported this bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1027380), please comment if you have more details.

How did you install the proposed kernel?

Edit: You're on quantal probably, just enabled quantal-proposed

**Edit: restored my quantal installation, enabled quantal-proposed and the laptop woke up fine after a 10 minute suspend, will leave it suspended tonight as the final test**

---

### Post by kaefert66014235 on 2012-07-25
I'm using the kernel [3.5.0-030500]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/linux-image-3.5.0-030500-generic_3.5.0-030500.201207211835_amd64.deb") on my UX32VD and suspension and brightness control via panel-applets works fine.

I also tried to hibernate via running "pm-hibernate" but this did not work, had to force shutdown after a failed start following hibernation.

This bug described [here]("https://help.ubuntu.com/community/AsusZenbookPrime") 
> a. The Zenbook hangs at the login screen for a very long time when you start the computer on battery (This does not happen when you start it with the AC plug connected). 
Doesn't happen for me. Boots very quick from the 24gb SSD and also no hanging at the login screen no matter if I have attached power or not.

What I do not understand is this how this patch to enable all those fn keys should work. do I need to do something with kernel sources and build a kernel myself?

Especially I would love to have the possibility to control the keyboard elumination.


What worked out of the box for me:
-) Wifi
-) LAN-Adapter (have only tried 100mbit, need to try out to connect to my gbit switch)
-) HDMI & VGA-Adapter (but sometimes messes up X beyond repair except by a reboot) (and also when connected external screen during boot internal one doesn't show and can't be enabled)
-) SDHC-Card-Reader (does not support SDXC according to asus, but will try it when I get my hands on one)

---

### Post by peter rus on 2012-07-25
> **kaefert66014235 said:**
> I'm using the kernel [3.5.0-030500]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.5-quantal/linux-image-3.5.0-030500-generic_3.5.0-030500.201207211835_amd64.deb") on my UX32VD and suspension and brightness control via panel-applets works fine.

I also tried to hibernate via running "pm-hibernate" but this did not work, had to force shutdown after a failed start following hibernation.

This bug described [here]("https://help.ubuntu.com/community/AsusZenbookPrime") 

Doesn't happen for me. Boots very quick from the 24gb SSD and also no hanging at the login screen no matter if I have attached power or not.

What I do not understand is this how this patch to enable all those fn keys should work. do I need to do something with kernel sources and build a kernel myself?

Especially I would love to have the possibility to control the keyboard elumination.


What worked out of the box for me:
-) Wifi
-) LAN-Adapter (have only tried 100mbit, need to try out to connect to my gbit switch)
-) HDMI & VGA-Adapter (but sometimes messes up X beyond repair except by a reboot) (and also when connected external screen during boot internal one doesn't show and can't be enabled)
-) SDHC-Card-Reader (does not support SDXC according to asus, but will try it when I get my hands on one)

You probably shouldn't use a mainline kernel, as the wiki states: 

> Do mainline kernel builds include Ubuntu specific drivers?
By definition the mainline kernel builds are made from virgin unaltered mainline kernel sources and therefore do not, and should not, include any Ubuntu patches or drivers. There are also no binary drivers for these kernels.

Yesterday a fix for the suspend issues has been released in the quantal-proposed repository, this means that when you are running quantal, enabling this repository in software sources and then installing all updates gives gives you this fixed kernel.

** You might also find it in the xorg-edgers repository, have a look :)**

---

### Post by peter rus on 2012-07-25
Running the the latest release of Quantal, with quantal-proposed enabled:

Suspends works
Asus-wmi works (hotkeys) (see a few pages back on how to install them, use the dkms build/install method, not the .deb)

switching wifi still gives kernel panics

---

### Post by kaefert66014235 on 2012-07-25
> **peter rus said:**
> You probably shouldn't use a mainline kernel, as the wiki states..
oh, okey, didn't see that.

Well I'm using Linux Mint 13 with Cinnamon.

> **peter rus said:**
> Yesterday a fix for the suspend issues has been released in the quantal-proposed repository, this means that when you are running quantal, enabling this repository in software sources and then installing all updates gives gives you this fixed kernel.

** You might also find it in the xorg-edgers repository, have a look :)**

could you give more details about this kernel, whats its version string? I just got an updated kernel from xorg-edgers with the version "3.5.0-6 generic"

But I don't have any issues with suspending with my "3.5.0-030500-generic" kernel. The only serious problem that I would like to solve is that all most of those fn keys don't work.

---

### Post by peter rus on 2012-07-25
> **kaefert66014235 said:**
> oh, okey, didn't see that.

Well I'm using Linux Mint 13 with Cinnamon.



could you give more details about this kernel, whats its version string? I just got an updated kernel from xorg-edgers with the version "3.5.0-6 generic"

But I don't have any issues with suspending with my "3.5.0-030500-generic" kernel. The only serious problem that I would like to solve is that all most of those fn keys don't work.

[http://ubuntuforums.org/showpost.php?p=12086401&postcount=27](http://ubuntuforums.org/showpost.php?p=12086401&postcount=27)

Beware however, this is a piece of source pulled from a forum, the updated asus-wmi should be somewhere in the kernel tree but I have no idea where as this currently goes beyond my knowledge. It works on my quantal installation, but I have had a lot of trouble with it previously (causing kernel panics, infinite bootloops because of kernel oopses underneath the splashbootscreen (so you wont notice them)

---

### Post by kaefert66014235 on 2012-07-25
> **screemo said:**
> ...
0) install quantal kernel headers
1) tar zxvf asus-wmi.tar.gz to /usr/src/
2) sudo dkms build -m asus-wmi -v 999.01
3) sudo dkms install -m asus-wmi -v 999.01

Reboot - and then Fn keys for audio, keyboard backlight should work.

Thanks man! worked for me on linux mint 13 with the 3.5.0-6-generic kernel from the xorg-edgers

btw. what should fn+space and fn+c do?

and another question: our processor is sold with a "Turbo boost to 3.0GHz" label, can we use this? I am using this applet [http://cinnamon-spices.linuxmint.com/applets/view/70](http://cinnamon-spices.linuxmint.com/applets/view/70) which lets me control the processor speed between 800mhz and 1.9ghz --> it also has the buttons for up to 2.4 ghz but they don't work.

UPDATE: found this: [http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)
which gives a really nice view of the processor state, and shows that turbo boost is working.
this (which I guess is used by my cpu freq applet) doesn't show the turbo boosting: "grep MHz /proc/cpuinfo"
Also showing the turbo boost at work does this: sudo modprobe msr ; sudo turbostat

UPDATE2: strange somehow, with cinnamon nearly all of my fn buttons worked, but now I switched to mate, since cinnamon has an awful support for multiple monitors, and now the keys for the keyboard elumination brightness don't work anymore. UPDATE3: on the Mate desktop also the function to suspend on closing the lid doesn't work. Pressing fn+F1 does work also in Mate.

UPDATE4: I found that after waking from suspension my zenbook believes he is still connected to my wifi, and doesn't automatically reconnect. I have to manually disconnect wifi and reconnect it again to have a connection again.

---

### Post by screemo on 2012-07-27
> **kaefert66014235 said:**
> Thanks man! worked for me on linux mint 13 with the 3.5.0-6-generic kernel from the xorg-edgers

btw. what should fn+space and fn+c do?

and another question: our processor is sold with a "Turbo boost to 3.0GHz" label, can we use this? I am using this applet [http://cinnamon-spices.linuxmint.com/applets/view/70](http://cinnamon-spices.linuxmint.com/applets/view/70) which lets me control the processor speed between 800mhz and 1.9ghz --> it also has the buttons for up to 2.4 ghz but they don't work.

UPDATE: found this: [http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)
which gives a really nice view of the processor state, and shows that turbo boost is working.
this (which I guess is used by my cpu freq applet) doesn't show the turbo boosting: "grep MHz /proc/cpuinfo"
Also showing the turbo boost at work does this: sudo modprobe msr ; sudo turbostat

UPDATE2: strange somehow, with cinnamon nearly all of my fn buttons worked, but now I switched to mate, since cinnamon has an awful support for multiple monitors, and now the keys for the keyboard elumination brightness don't work anymore. UPDATE3: on the Mate desktop also the function to suspend on closing the lid doesn't work. Pressing fn+F1 does work also in Mate.

UPDATE4: I found that after waking from suspension my zenbook believes he is still connected to my wifi, and doesn't automatically reconnect. I have to manually disconnect wifi and reconnect it again to have a connection again.

You should try quantal as base, I don't have any problems with wifi (or other things) after wakeup. 

Well just the occasionally black wallpaper, but I can live with that :-)

---

### Post by kaefert66014235 on 2012-07-27
> **screemo said:**
> You should try quantal as base, I don't have any problems with wifi (or other things) after wakeup. 

Well just the occasionally black wallpaper, but I can live with that :-)

well.. the thing is that I really cannot stand this unity stuff.. cinnamon and also mate are just incredible much better. At least for people who are not using / interested in tablets.

---

### Post by screemo on 2012-07-27
> **kaefert66014235 said:**
> well.. the thing is that I really cannot stand this unity stuff.. cinnamon and also mate are just incredible much better. At least for people who are not using / interested in tablets.

Ah yes its a matter of preference ofcourse, .. I havent been able to find anything on mint 14 yet (except for some blogs posts), so only solution right now is probably using the backported quantal kernel, and what it can provide.

Possibly the networkmanager widget for cinnamon/mate is trailing behind the latest gnome. I found that the newest (from quantal) has a much better support for 3g dongles, and also reconnect on bad wireless AP's.

I wonder if you could tap into the latest cinnamon/mate beta/unstable repo and add that to mint 13 ?

---

### Post by kaefert66014235 on 2012-07-27
> **screemo said:**
> Ah yes its a matter of preference ofcourse, .. I havent been able to find anything on mint 14 yet (except for some blogs posts), so only solution right now is probably using the backported quantal kernel, and what it can provide.

Possibly the networkmanager widget for cinnamon/mate is trailing behind the latest gnome. I found that the newest (from quantal) has a much better support for 3g dongles, and also reconnect on bad wireless AP's.

I wonder if you could tap into the latest cinnamon/mate beta/unstable repo and add that to mint 13 ?

hmm, maybe I'm gonna try quantal.. One thing, since you're running ubuntu 12.10 alpha, could you try for me if it works well with a multiple monitor setup? Thats the one reason for which I switched to Mate and didn't stay with cinnamon, and with cinnamon everything else (but the screen brightness control fn+f5&f6) worked which also doesn't work with ubuntu 12.10 alpha if I read that correctly.

---

### Post by nichomerri on 2012-07-27
Hey guys, thank you so much for this thread! Lots of great info in here. I, being new to these newfangled hybrid graphics (I have an Asus UX32VD), have one or two questions: will the nvidia card draw ANY power if no drivers are installed? 'dpkg -l | grep nvidia' returns nothing, so am I safe in supposing that there is nothing else I can do to save power on that end?

powertop reports average power consumption (at 50% brightness) of about 14-15 watts, which sounds high. Anyone else getting lower values?

---

### Post by kaefert66014235 on 2012-07-28
hi there!
strangly powertop only gives me info about wakes per second, and nothing about watts and power. I googled a bit and found that the info is there:

```
kaefert@Ultrablech ~ $ cat /sys/class/power_supply/BAT0/uevent
POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_STATUS=Discharging
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_CYCLE_COUNT=0
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=7400000
POWER_SUPPLY_VOLTAGE_NOW=7982000
POWER_SUPPLY_POWER_NOW=16380000
POWER_SUPPLY_ENERGY_FULL_DESIGN=45640000
POWER_SUPPLY_ENERGY_FULL=44611000
POWER_SUPPLY_ENERGY_NOW=39459000
POWER_SUPPLY_MODEL_NAME=UX32-65
POWER_SUPPLY_MANUFACTURER=ASUSTeK
POWER_SUPPLY_SERIAL_NUMBER=
```

now I think the value of POWER_NOW gives me the current ampere, and together with the POWER_SUPPLY_VOLTAGE_NOW I should be able to calculate watts, but therefore I would need to know the scales of these values.. I tried to find scales by comparing this:
POWER_SUPPLY_ENERGY_FULL_DESIGN=45640000 with the specs from asus which state 48 Whrs Battery but this doesn't seem to add up (scale 950833.33333 ?!)

UPDATE: So the specs say we have 48Wh and somewhere else I found written that the battery of the UX32VD has 6 cells and 6570mAh.
If I did the math correctly then our battery should have 7.3 Volts according to the combination of those specs. Which now that I think about also fits with the default ~ 1.2 Volts per cell. Now the variable POWER_SUPPLY_VOLTAGE_MIN_DESIGN is 7400000 which I guess is to mean 7.4 Volts, therefore its unit is µV.

So if I accept this scale (micro) also for the energy and the power variables, that would mean that these tools want to say that my battery has by design only 45.64 Wh (******* advertising/marketing jerks) and in truth (two days after I bought this unit) only 44.611 Wh

And If you're saying you get 14-15 Watts then I guess with my "micro" scale those POWER_SUPPLY_POWER_NOW=16380000 are probably 16.38 Watts.. First I thought I would get a current out of those statistics, but now that I think about what "POWER" does mean in an electrical context it actually makes more sense that I directly get the watts

---

### Post by SveinT on 2012-07-28
> **kaefert66014235 said:**
> hi there!
strangly powertop only gives me info about wakes per second, and nothing about watts and power. 

Are you running on AC? I believe you have to disconnect the computer from AC, as the power consumption is measured by battery power draw.

EDIT:
Never mind, didn't see the "Discharging" in there. Mine displays battery draw fine in powertop, but not when using AC. At 50% brightness I get from 12.4-14.5W.

---

### Post by kaefert66014235 on 2012-07-28
> **SveinT said:**
> Are you running on AC? I believe you have to disconnect the computer from AC, as the power consumption is measured by battery power draw.

EDIT:
Never mind, didn't see the "Discharging" in there. Mine displays battery draw fine in powertop, but not when using AC. At 50% brightness I get from 12.4-14.5W.

could you post the output of this:
cat /sys/class/power_supply/BAT0/uevent

maybe this will tell me why it doesn't work for me with powertop.

I've wrote up a little script that prints me the interesting info every 10 seconds

---

### Post by SveinT on 2012-07-28
> **kaefert66014235 said:**
> could you post the output of this:
cat /sys/class/power_supply/BAT0/uevent

maybe this will tell me why it doesn't work for me with powertop.

I've wrote up a little script that prints me the interesting info every 10 seconds

```

POWER_SUPPLY_NAME=BAT0
POWER_SUPPLY_STATUS=Discharging
POWER_SUPPLY_PRESENT=1
POWER_SUPPLY_TECHNOLOGY=Li-ion
POWER_SUPPLY_CYCLE_COUNT=0
POWER_SUPPLY_VOLTAGE_MIN_DESIGN=7400000
POWER_SUPPLY_VOLTAGE_NOW=7338000
POWER_SUPPLY_POWER_NOW=12957000
POWER_SUPPLY_ENERGY_FULL_DESIGN=45640000
POWER_SUPPLY_ENERGY_FULL=44128000
POWER_SUPPLY_ENERGY_NOW=23660000
POWER_SUPPLY_MODEL_NAME=UX32-65
POWER_SUPPLY_MANUFACTURER=ASUSTeK
POWER_SUPPLY_SERIAL_NUMBER= 

```

POWER_SUPPLY_POWER_NOW seems to show the same power usage shown in powertop as you suspected.

---

### Post by kaefert66014235 on 2012-07-28
> **SveinT said:**
>  ...
POWER_SUPPLY_POWER_NOW seems to show the same power usage shown in powertop as you suspected.

Hmm, interesting. So it seems the problem is with the powertop included in linux mint 13, or I am simply to stupid to see those stats inside powertop. would you mind uploading a screenshot how powertop should look like? and/or maybe your version? I seem to have PowerTOP 1.97 beta 1 which it prints when I try to run it without root permissions

---

### Post by SveinT on 2012-07-29
> **kaefert66014235 said:**
> Hmm, interesting. So it seems the problem is with the powertop included in linux mint 13, or I am simply to stupid to see those stats inside powertop. would you mind uploading a screenshot how powertop should look like? and/or maybe your version? I seem to have PowerTOP 1.97 beta 1 which it prints when I try to run it without root permissions

Sure:

[IMG]https://dl.dropbox.com/u/100344/powertop.png[/IMG]
[IMG]https://dl.dropbox.com/u/100344/powertop2.png[/IMG]

I didn't really notice the second figure under "Device stats" before. Seems a bit less than the reported battery drain. I'm not sure which figure to trust...



Over to something else, my fan seem to be spinning all the time (although at a low speed), is this normal? It will speed up when under heavy load, so there is some control at least...
CPU/System temperatures are around 50C. The wiki states that fan sensors work, but it certainly doesn't on my system.

---

### Post by peter rus on 2012-07-29
On 12.04 I had to compile the latest version of powertop myself, as the repository is stuck somewhere at 1.99 and I need 2+, powertop 2 also displays the used Wattage

---

### Post by kaefert66014235 on 2012-07-29
thanks for the screenshots. Now that I knew that there's a newer version of powertop, i just searched for powertop 2 and found this:
[https://01.org/powertop/sites/default/files/downloads/powertop-2.0.tar.bz2](https://01.org/powertop/sites/default/files/downloads/powertop-2.0.tar.bz2)

Downloading, extracting, cd into extracted folder
sudo apt-get install build-essential libncurses5-dev libpci-dev libnl-dev
./configure
./make
src/powertop

and there I had the same watt outputs as you

---

### Post by screemo on 2012-08-02
Anyone having success with the asus_wmi module and quantal kernel 3.5.0-7 ?

Loading the module gives no errors, and no output in the dmeg... :(

---

### Post by screemo on 2012-08-03
> **screemo said:**
> Anyone having success with the asus_wmi module and quantal kernel 3.5.0-7 ?

Loading the module gives no errors, and no output in the dmeg... :(

Just tried compiling 3.6-rc1 kernel, and keyboard backlight + screen brigthness works using the following /sys paths:

```


values from 0-3:

# echo "0"> /sys/class/leds/asus\:\:kbd_backlight/brightness

values from 0-4296 (0 will turn the screen off - you been warned ):

#echo "1000"> /sys/class/backlight/intel_backlight/brightness


```

I can see the asus-wmi module is radically different from the previous kernel (3.5), so I'm going to see if I can make the keys work.

EDIT: appears that all keys send their respective codes except for the *annoying* brightness up/down - however no patches seem to be needed.

---

### Post by tobiasb on 2012-08-03
Hey :) I was wondering if anyone here knows how to fix the problem with the screen going blank everytime I turn on or close the lid of my ux32a? It starts working when I open and close the lid a few times. I am running ubuntu 12.04 and I would prefer not to use the new unsupported alpha because my girlfriend is going to use this computer. any help would be much apprechiated :D

---

### Post by screemo on 2012-08-03
> **tobiasb said:**
> Hey :) I was wondering if anyone here knows how to fix the problem with the screen going blank everytime I turn on or close the lid of my ux32a? It starts working when I open and close the lid a few times. I am running ubuntu 12.04 and I would prefer not to use the new unsupported alpha because my girlfriend is going to use this computer. any help would be much apprechiated :D

Your best option is probably using the backported quantal kernel - it fixes the suspend/resume problems.

[http://unbrokenspectrum.wordpress.com/2012/07/12/test-quantal-kernels-on-precise/](http://unbrokenspectrum.wordpress.com/2012/07/12/test-quantal-kernels-on-precise/) should get you started.

Being on quantal, i can say its pretty stable for an alpha version - no big problems at all (just dont dist-upgrade if it means alot of packages end up being removed - just a hint ;)

---

### Post by oogabubchub on 2012-08-04
I seem to have screwed some stuff up when setting up my ubuntu dual boot. Would anyone happen to have a copy of the EFI related stuff on the Recovery partition?

---

### Post by Bozoo on 2012-08-06
Hi, 

I check for enabling ALPM on a UX32A, but on wiki page i don't see if it's work fine. 

Anybody try it ? If yes can you comfirm it's thats work fine :)

Thx

bios info : UX32A.206
kernel info : 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

**Edit :**

I tested and that's work fine

Power before ALPM enabled : 11.71 W, &#963;=0.21
Power after ALPM enabled : 11.10 W, &#963;=0.35

---

### Post by Tuxdude on 2012-08-09
Has anyone here been able to get HDMI audio to be working ? I've not installed Ubuntu on this machine yet, but I'm going to right now. On openSUSE I see that the HDMI audio device is not being listed in the output of **aplay -l** or in the sound settings. Although I see the **Pantherpoint HDMI audio** being listed under **/proc/asound/card0/codec#3**

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7918000 irq 48

$ cat /proc/asound/card0/codec#3 
Codec: Intel PantherPoint HDMI
Address: 3
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862806
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560010: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="HDMI/DP,pcm=3 Jack", index=0, device=0
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560020: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x80]
  Pincap 0x09000094: OUT Detect HBR HDMI DP
  Pin Default 0x58560030: [N/A] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x3, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
```

---

### Post by madmack on 2012-08-09
> **Tuxdude said:**
> Has anyone here been able to get HDMI audio to be working ? I've not installed Ubuntu on this machine yet, but I'm going to right now. On openSUSE I see that the HDMI audio device is not being listed in the output of **aplay -l** or in the sound settings. Although I see the **Pantherpoint HDMI audio** being listed under **/proc/asound/card0/codec#3**

...



works fine here:

```


$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

---

### Post by kaefert66014235 on 2012-08-09
looks for me the same as for madmack with linux mint 13

---

### Post by varaha on 2012-08-10
I have two potentially connected problems with my UX32A, which is supposedly identical to UX31A except it has a smaller ssd & a 500gb hdd. I can't boot without nomodeset or i915.modeset=0 in GRUB (I get a blank screen), and I can't change the brightness using any of the discussed methods (indicator-brightness, xrandr, or /sys/class/backlight).

Under /sys/class/backlight I have acpi_video0, whereas others seem to have intel. If I use acpi_backlight=vendor in GRUB, under /sys/class/backlight I get something beginning with asus (which I have failed to write down, but I can check this if it matters) . For both, I can manipulate the contents of the actual_brightness file using echo, but they have no effect on the screen brightness.

I'm running 12.04, and I've tested three kernels (current default kernel, 3.4.6, and 3.5.0-9), none of which allowed me to change brightness. When I boot to windows I am able to change brightness however, so I know the unit is not faulty.

Does anyone have any ideas, or has anyone encountered anything similar?

---

### Post by MirdautasVras on 2012-08-10
Hi everyone!
So, yesterday I got a new Asus UX32VD-R400V, which I was eager to get Ubuntu running on. Well, about 24h later, I've got it running. I thought I'd share my thoughts on what worked, what didn't work, and what took me about 8hours to figure out.

**A working install of Ubuntu 12.04 64-bit to the Asus Zenbook UX32VD**

First important notice: I tried installing from a Xubuntu 12.04 live usb. This did not work, and caused me hours of frustration. It seems this distribution wasn't packaged with an EFI-aware kernel. If the usb does not boot from the UEFI:-prefixed option in the Laptop boot selection screen, I don't think you'll get a bootable installation, unless you remove the EFI partition completely and install GRUB there, or something.

Second important notice: After installing this way, I can't boot windows 7 from grub. However, by pressing escape as the computer boots, to get into the boot device chooser, I can still choose the windows startup manager, and get into windows 7 just fine.

[LIST]
[*]So, first off I wrote a live USB of Ubuntu 12.04 64-bit to a USB memory, using [Pendrive Linux's Universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").

[*]Next, I booted the laptop and pressed ESC to get the boot menu to appear. Next, I selected the UEFI: USB Drive option. It is important to get the laptop to boot the USB drive in UEFI mode (by choosing the option preceded by "UEFI: "), so that the installer recognizes that the laptop uses UEFI.

[*]If everything works out, this boots a menu where you can choose to boot the live usb, install Ubuntu or exit. I went with booting the Live usb.

[*]After the live Ubuntu session had started, I started the installation program from the left side bar (after connecting to my wifi, to get updates for the installation).

[*]Next, the partitioning options. I went with installing / to the SSD found at /dev/sdb. This SSD has 32GB of space. The 500GB main drive (/dev/sda) has a number of partitions. /dev/sda1 is the EFI boot partition, which I did not want to harm. The rest of the HD was occupied mostly by a number of Windows partitions. One was the main OS disk (with a size of about 130GB, if I recall correctly). One is a "Data" drive, which was almost empty, and had a space of about 200GB. Finally, there was a recovery partition, which was used up to about 12GB, and had a total size of 24GB. I went with the following partitioning:
	I shrunk the partition where the OS was installed to 80GB.
	I removed the DATA partition.
	I left the Recovery partition untouched (in case it might be used in the future for any recovery).
Next up, I divided the new free space into three partitions. 

First, and first on the disk, I put a 353GB ext4 partition. Next, I put a 36GB ext4 partition. Finally, I put 4GB of SWAP. On the ext4 partitions, I mounted /home and /usr/local.

This gave me the following partitions:
/dev/sda1 EFI partition 200MB
/dev/sda2 Unknown/unused space 134MB 
/dev/sda3 Windows 7 drive 80GB
/dev/sda4 /home 353GB
/dev/sda6 /usr/local 36GB
/dev/sda7 linux-swap 4GB
/dev/sda5 Microsoft windows recovery environment 27GB

/dev/sdb1 / 32GB

After deciding on these partitions, I choose to put the bootloader in /dev/sda. This was important, since the 500GB HD is the disk that is booted first by the laptop BIOS. This boot disk order cannot be changed in the UX32VD bios. Therefore, the boot loader must be set to /dev/sda

[*]Next, I went through the rest of the installer normally, and could reboot.

[*]After rebooting, GRUB2 came up instead of the Windows loading screen, and I could start Ubuntu. I could also start Windows 7 from that menu.

[*]Once I was logged in, most things worked. However, none of the function keys did. Therefore, I installed the Quantal 3.5.0.9 kernel from the ubuntu-x-swat/q-lts-backports ppa. However, this did not suffice either. I also had to patch the asus-wmi file using the instructions from [http://ubuntuforums.org/showpost.php?p=12057336&postcount=49](http://ubuntuforums.org/showpost.php?p=12057336&postcount=49). Afterwards, all function keys except those for the screen backlight worked.

[*]I installed xbacklight to control the backlight in some way.

[*]I also installed bumblebee from the bumblebee ppa. This worked all right, and bbswitch indicated that the Nvidia GPU was turned off. However, optirun does not work (I cannot use the Nvidia GPU). I think this is related to Kernel 3.5 not working with bumblebee.
[/LIST]

This is basically what I did to get Ubuntu 12.04 working on my UX32VD. 

My biggest mistake was using a live usb which wasn't able to recognize UEFI. I spent hours trying to get a new UEFI entry into the UEFI boot manager, before eventually giving up and just installing Ubuntu in UEFI mode, instead of Xubuntu.

As for what works, I haven't tested much extensively. I do know that 
*The HDMI port works for video and audio

**What doesn't work**
[LIST]
[*]The Nvidia GPU does not work (at least with Bumblebee)
(Trying to run "optirun firefox" crashes X completely)
[*]Right clicking by clicking on the lower right hand side of the touchpad does not work (right clicks work by two-finger pressing)
[*]The computer stalls at the login screen for about 30s after booting if the power is not connected (As has been mentioned previously in this thread)
[*]The suspend is finicky. If the computer hasn't been given enough time to suspend, the computer will not start up properly. The keyboard backlight will start up, but the screen stays black. Perhaps related to this, the bootup can stall on the "Loading ubuntu"/dots boot up screen, after such problems have occurred. Starting in recovery mode, and then starting normally (Which seems to "clean" the boot or something), seems to let the computer boot.
[*]Sometimes after these problems (perhaps also unrelated to other problems), the backlight cannot be changed with xbacklight. xrandr gives an error message about not being able to detect the gamma level, just showing one resolution (the fullHD one). Getting a clean reboot fixes that problem.
[*]I can't boot windows 7 from grub, but I can if I boot it via the BIOS boot device chooser.
[/LIST]

---

### Post by screemo on 2012-08-11
> **MirdautasVras said:**
> Hi everyone!
So, yesterday I got a new Asus UX32VD-R400V, which I was eager to get Ubuntu running on. Well, about 24h later, I've got it running. I thought I'd share my thoughts on what worked, what didn't work, and what took me about 8hours to figure out.

**A working install of Ubuntu 12.04 64-bit to the Asus Zenbook UX32VD**

First important notice: I tried installing from a Xubuntu 12.04 live usb. This did not work, and caused me hours of frustration. It seems this distribution wasn't packaged with an EFI-aware kernel. If the usb does not boot from the UEFI:-prefixed option in the Laptop boot selection screen, I don't think you'll get a bootable installation, unless you remove the EFI partition completely and install GRUB there, or something.

[LIST]
[*]So, first off I wrote a live USB of Ubuntu 12.04 64-bit to a USB memory, using [Pendrive Linux's Universal USB installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/").

[*]Next, I booted the laptop and pressed ESC to get the boot menu to appear. Next, I selected the UEFI: USB Drive option. It is important to get the laptop to boot the USB drive in UEFI mode (by choosing the option preceded by "UEFI: "), so that the installer recognizes that the laptop uses UEFI.

[*]If everything works out, this boots a menu where you can choose to boot the live usb, install Ubuntu or exit. I went with booting the Live usb.

[*]After the live Ubuntu session had started, I started the installation program from the left side bar (after connecting to my wifi, to get updates for the installation).

[*]Next, the partitioning options. I went with installing / to the SSD found at /dev/sdb. This SSD has 32GB of space. The 500GB main drive (/dev/sda) has a number of partitions. /dev/sda1 is the EFI boot partition, which I did not want to harm. The rest of the HD was occupied mostly by a number of Windows partitions. One was the main OS disk (with a size of about 130GB, if I recall correctly). One is a "Data" drive, which was almost empty, and had a space of about 200GB. Finally, there was a recovery partition, which was used up to about 12GB, and had a total size of 24GB. I went with the following partitioning:
	I shrunk the partition where the OS was installed to 80GB.
	I removed the DATA partition.
	I left the Recovery partition untouched (in case it might be used in the future for any recovery).
Next up, I divided the new free space into three partitions. 

First, and first on the disk, I put a 353GB ext4 partition. Next, I put a 36GB ext4 partition. Finally, I put 4GB of SWAP. On the ext4 partitions, I mounted /home and /usr/local.

This gave me the following partitions:
/dev/sda1 EFI partition 200MB
/dev/sda2 Unknown/unused space 134MB 
/dev/sda3 Windows 7 drive 80GB
/dev/sda4 /home 353GB
/dev/sda6 /usr/local 36GB
/dev/sda7 linux-swap 4GB
/dev/sda5 Microsoft windows recovery environment 27GB

/dev/sdb1 / 32GB

After deciding on these partitions, I choose to put the bootloader in /dev/sda. This was important, since the 500GB HD is the disk that is booted first by the laptop BIOS. This boot disk order cannot be changed in the UX32VD bios. Therefore, the boot loader must be set to /dev/sda

[*]Next, I went through the rest of the installer normally, and could reboot.

[*]After rebooting, GRUB2 came up instead of the Windows loading screen, and I could start Ubuntu. I could also start Windows 7 from that menu.

[*]Once I was logged in, most things worked. However, none of the function keys did. Therefore, I installed the Quantal 3.5.0.9 kernel from the ubuntu-x-swat/q-lts-backports ppa. However, this did not suffice either. I also had to patch the asus-wmi file using the instructions from [http://ubuntuforums.org/showpost.php?p=12057336&postcount=49](http://ubuntuforums.org/showpost.php?p=12057336&postcount=49). Afterwards, all function keys except those for the screen backlight worked.

[*]I installed xbacklight to control the backlight in some way.

[*]I also installed bumblebee from the bumblebee ppa. This worked all right, and bbswitch indicated that the Nvidia GPU was turned off. However, optirun does not work (I cannot use the Nvidia GPU). I think this is related to Kernel 3.5 not working with bumblebee.
[/LIST]

This is basically what I did to get Ubuntu 12.04 working on my UX32VD. 

My biggest mistake was using a live usb which wasn't able to recognize UEFI. I spent hours trying to get a new UEFI entry into the UEFI boot manager, before eventually giving up and just installing Ubuntu in UEFI mode, instead of Xubuntu.

As for what works, I haven't tested much extensively. I do know that 
*The HDMI port works for video and audio

**What doesn't work**
[LIST]
[*]The Nvidia GPU does not work (at least with Bumblebee)
(Trying to run "optirun firefox" crashes X completely)
[*]Right clicking by clicking on the lower right hand side of the touchpad does not work (right clicks work by two-finger pressing)
[*]The computer stalls at the login screen for about 30s after booting if the power is not connected (As has been mentioned previously in this thread)
[*]The suspend is finicky. If the computer hasn't been given enough time to suspend, the computer will not start up properly. The keyboard backlight will start up, but the screen stays black. Perhaps related to this, the bootup can stall on the "Loading ubuntu"/dots boot up screen, after such problems have occurred. Starting in recovery mode, and then starting normally (Which seems to "clean" the boot or something), seems to let the computer boot.
[*]Sometimes after these problems (perhaps also unrelated to other problems), the backlight cannot be changed with xbacklight. xrandr gives an error message about not being able to detect the gamma level, just showing one resolution (the fullHD one). Getting a clean reboot fixes that problem.
[/LIST]

I just switched to the 3.6-rc1 kernel, there the suspend/resume, and hotkeys work out of the box (brightness on Fn keys still mia).

On current Ubuntu 12.10 (all packages updated today):

* Rightclick in the lower half touchpad works
* Bumblebee still doesnt work
* login screen doesn't stall
* resume makes background picture disappear, but it will come back if you reapply wallpaper (or use something like Wallch to rotate them anyways)

---

### Post by stucki on 2012-08-14
> **SveinT said:**
> As stated in the PPA, they're already aware of it and the cause (something in MESA?), so you will just have to wait for them to sort it out.

This is fixed with the updates from this morning.

Additionally, the problem with hanging login screen when on battery is also fixed now.

Great!

---

### Post by astromatt on 2012-08-14
hi,
I have a UX31a with Ubuntu 12.04 installed. I've managed to get almost everything working but i'm having a few issues when connecting to an external screen using the HDMI port.
Firstly, if i boot up with it connected then it will boot up using the external screen but the laptop screen is blank.  Nothing i do can bring the laptop screen up.  I've tried disconnecting the HDMI connector to see if it would switch back but nothing happens.

If i boot up not connected to the external screen and connect later everything is fine if the displays are mirrored.  However, if i uncheck mirroring then after a minute the task bars disappear and the the computer goes into a semi freeze state.  Things that are running continue but you cannot do anything else.

Any suggestions would be extremely welcome
Cheers

---

### Post by kaefert66014235 on 2012-08-14
> **astromatt said:**
> hi,
I have a UX31a with Ubuntu 12.04 installed. I've managed to get almost everything working but i'm having a few issues when connecting to an external screen using the HDMI port.
Firstly, if i boot up with it connected then it will boot up using the external screen but the laptop screen is blank.  Nothing i do can bring the laptop screen up.  I've tried disconnecting the HDMI connector to see if it would switch back but nothing happens.

If i boot up not connected to the external screen and connect later everything is fine if the displays are mirrored.  However, if i uncheck mirroring then after a minute the task bars disappear and the the computer goes into a semi freeze state.  Things that are running continue but you cannot do anything else.

Any suggestions would be extremely welcome
Cheers

I have a UX32VD running Linux Mint 13, and the first problem is the same for me, the second problem does not exist for me, at least not with mate (gnome2), cinnamon (gnome3) also has problems here.

---

### Post by maroony on 2012-08-14
The second problem does not exist for me. I'm using ubuntu 12.04 with kernel 3.4.4 and unity.

---

### Post by ambidextrvs on 2012-08-17
Hi,

I had a problem for the last couple of days. I was on ubuntu 12.10 with kernel 3.5-8 and suddenly one day (without performing system updates or tweaks) I wasn't being able to get to the login screen. The screen was off and the caps-lock led was blinking.
I had to remove the asus_wmi_0.2 to get it working.
Then I updated to Kernel 3.6-rc1 and everything seemed to be working ok yesterday, but today it didn't boot correctly again. I was only able to get to the login screen by going to recovery mode and then proceeding to normal boot.
I thought it was a graphics problem since the Nvidia card is not being recognized so I did this:
[http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743](http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743)

This fixed the issue for me, although I'm not sure exactly what happened. Could somebody give me some pointers on how to debug booting issues like this?

Also, does anybody got the Nvidia 620m working?

Thanks,

Update 1: it turns out that my issue wasn't fixed. Apparently something gets corrupted between boots and it gets fixed momentarily by updating the grub file. I don't know how to get the boot log for this issue but I was able to capture a 'screen-shot' of the kernel-panic. Any help would be very appreciated.

[IMG]http://ubuntuone.com/7NNvVGAQXWLRW4wuB5Ao4w[/IMG]

---

### Post by MirdautasVras on 2012-08-19
My computer hasn't shown the first problem (that of just showing a black screen). However, it has stopped loading on the Ubuntu splash screen (where the "loading" bar (I've got the Xubuntu splash) goes from left to right) several times. I think it's related to some kind of graphics issue, because after restarting in recovery mode, and doing a normal start, it boots up properly, but running not the right Ivy Bridge GPU driver, but some kind of general VESA-like driver. It hasn't got proper acceleration, and runs glxspheres at 20fps instead of 60fps. It also runs the Unity 2d environment. I have to reboot again to get it back to normal. I think I have the very latest Nvidia and mesa drivers, but that hasn't fixed the problem for me.

And no, the Nvidia card does not work when using Bumblebee ("optirun firefox", for example). It complains of not being able to load a driver for the card.

> **ambidextrvs said:**
> Hi,

I had a problem for the last couple of days. I was on ubuntu 12.10 with kernel 3.5-8 and suddenly one day (without performing system updates or tweaks) I wasn't being able to get to the login screen. The screen was off and the caps-lock led was blinking.
I had to remove the asus_wmi_0.2 to get it working.
Then I updated to Kernel 3.6-rc1 and everything seemed to be working ok yesterday, but today it didn't boot correctly again. I was only able to get to the login screen by going to recovery mode and then proceeding to normal boot.
I thought it was a graphics problem since the Nvidia card is not being recognized so I did this:
[http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743](http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743)

This fixed the issue for me, although I'm not sure exactly what happened. Could somebody give me some pointers on how to debug booting issues like this?

Also, does anybody got the Nvidia 620m working?

Thanks,

Update 1: it turns out that my issue wasn't fixed. Apparently something gets corrupted between boots and it gets fixed momentarily by updating the grub file. I don't know how to get the boot log for this issue but I was able to capture a 'screen-shot' of the kernel-panic. Any help would be very appreciated.


---

### Post by ambidextrvs on 2012-08-20
Hi, I've been trying to fix my issues with no success. I re-installed my system using the following partitioning.
```

ssd:
  24GB / 
hdd:
  496GB /home
    4GB swap

```

I installed ubuntu 12.10 with kernel 3.5.0-6 then I updated to 3.5.0-10 and everything was working perfectly except for the fn-keys.

Today I updated to kernel 3.5.0-11 where the fn-keys are working but it started to fail when booting. I'm only able to get in if I go through recovery mode first or pressing 'e' in the grub menu, set the gfxmode to text and remove "quiet splash".
This is the screen where I get stuck:
[IMG]http://ubuntuone.com/5qMF3QPsqWkS7qWDdLWCto[/IMG]

I'm guessing the fn-keys kernel module introduces some issue at booting time but I have no idea how to fix it. Any help would be appreciated. Thanks.

---

### Post by kaefert66014235 on 2012-08-22
In the last days (I'm guessing because of updates) the USB-System of my UX32VD crashed quite often - meaning it did not respond to connecting of a new usb-device, which could only be fixed through rebooting.

I thought maybe the xorg-edgers ppa was at fault, and since I wasn't able to purge the ppa correctly, I reinstalled my linux mint 13 (based on ubuntu 12.04) - however, even a clean fresh install without the xorg-edgers ppa but with all other upgrades installed had the same problem, even worse, I started to get regular complete freezes, that leave the notebook completly unresponsive, both over network and also locally through mouse & keyboard. alt+print+r also doesn't release the keyboard to switch to a tty - completly frozen.
Another problem of the reinstall, this dkms patch to make the (most) fn keys work as they should does only do as it should on every other boot. so around 50% of the time the fn-keys don't work for me now.

Does somebody have a ubuntu working better as that at the moment, and if so, how did you achieve that?

---

### Post by screemo on 2012-08-22
> **kaefert66014235 said:**
> In the last days (I'm guessing because of updates) the USB-System of my UX32VD crashed quite often - meaning it did not respond to connecting of a new usb-device, which could only be fixed through rebooting.

I thought maybe the xorg-edgers ppa was at fault, and since I wasn't able to purge the ppa correctly, I reinstalled my linux mint 13 (based on ubuntu 12.04) - however, even a clean fresh install without the xorg-edgers ppa but with all other upgrades installed had the same problem, even worse, I started to get regular complete freezes, that leave the notebook completly unresponsive, both over network and also locally through mouse & keyboard. alt+print+r also doesn't release the keyboard to switch to a tty - completly frozen.
Another problem of the reinstall, this dkms patch to make the (most) fn keys work as they should does only do as it should on every other boot. so around 50% of the time the fn-keys don't work for me now.

Does somebody have a ubuntu working better as that at the moment, and if so, how did you achieve that?

I run quantal on mine right now, and it works as it should. Also Fn-keys works (using the asus_wmi deb). Using 3g usb modems works fine also. Tried a few logitech mice aswell with no problems.

I dont have anything but standard quantal repo's and medibuntu enabled.

PS: suspend, wireless on/off and backlight works.

---

### Post by screemo on 2012-08-22
> **ambidextrvs said:**
> Hi, I've been trying to fix my issues with no success. I re-installed my system using the following partitioning.
```

ssd:
  24GB / 
hdd:
  496GB /home
    4GB swap

```

I installed ubuntu 12.10 with kernel 3.5.0-6 then I updated to 3.5.0-10 and everything was working perfectly except for the fn-keys.

Today I updated to kernel 3.5.0-11 where the fn-keys are working but it started to fail when booting. I'm only able to get in if I go through recovery mode first or pressing 'e' in the grub menu, set the gfxmode to text and remove "quiet splash".
This is the screen where I get stuck:
[IMG]http://ubuntuone.com/5qMF3QPsqWkS7qWDdLWCto[/IMG]

I'm guessing the fn-keys kernel module introduces some issue at booting time but I have no idea how to fix it. Any help would be appreciated. Thanks.

Boot in recovery mode, and sudo dpkg -P asus-wmi-dkms. then reinstall the package.

Sometimes I find that dkms doesn't sync with the kernel updates.

btw. my kernel parameters are:

```

linux   /boot/vmlinuz-3.5.0-11-generic root=UUID=ab91c99c-1fb6-4f11-a6e0-a0e425cf6114 ro   crashkernel=384M-2G:64M,2G-:128M quiet splash nmi_watchdog=0 apparmor=0 pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 $vt_handoff

```

---

### Post by kaefert66014235 on 2012-08-23
> **screemo said:**
> I run quantal on mine right now, and it works as it should. Also Fn-keys works (using the asus_wmi deb). Using 3g usb modems works fine also. Tried a few logitech mice aswell with no problems.

I dont have anything but standard quantal repo's and medibuntu enabled.

PS: suspend, wireless on/off and backlight works.

Okey, so I'm guessing you mean the 12.10 alpha3 from here:
[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3)

by "backlight works", do you mean fn+F5 and fn+F6 works?!
or do you mean by an applet or a manually set key combination that runs some script?
suspend and wireless on/off work for me also with linux mint 13 ~ 12.04 with the kernel ultrablech 3.2.0-29-generic #46-Ubuntu

about the asus_wmi deb, do you use 0.2 or 999.01? the wiki says you should use 999.01 by default and 0.2 only when also using the xorg-edgers repo, but the 999.01 gave me some errors therefore I used the 0.2

---

### Post by screemo on 2012-08-23
> **kaefert66014235 said:**
> Okey, so I'm guessing you mean the 12.10 alpha3 from here:
[https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3](https://wiki.ubuntu.com/QuantalQuetzal/TechnicalOverview/Alpha3)

by "backlight works", do you mean fn+F5 and fn+F6 works?!
or do you mean by an applet or a manually set key combination that runs some script?
suspend and wireless on/off work for me also with linux mint 13 ~ 12.04 with the kernel ultrablech 3.2.0-29-generic #46-Ubuntu

about the asus_wmi deb, do you use 0.2 or 999.01? the wiki says you should use 999.01 by default and 0.2 only when also using the xorg-edgers repo, but the 999.01 gave me some errors therefore I used the 0.2

I'm using alpha3 with latest updates as of today. The asus-wmi deb is the 0.2 version and works fine on 3.5.x kernels - I believe the wiki is slightly out of date on that.

I can use xbacklight to change it, unfortunately the fn+f5/f6 is still mia ;(

the asus-wmi I use is attached.

---

### Post by kaefert66014235 on 2012-08-23
okey, thanks for the info screemo. I now installed myself ubuntu 12.10 alpha3 and it works quite well, as long as you don't add "nomodeset" to the bootoptions. With "nomodeset" the screen flickers extremly and doesn't correctly draw the unity desktop.

whats very buggy is the window placement in unity when you use virtual desktops / workspaces. skype often magically moves itself to the first workspace, and on the workspace below the first one windows always slide down to the bottom of the workspace (sounds strange, but thats what I observe..)

and the performance of moving windows between workspaces is extreeeemly low. it takes like a second (and my zenbook has been upgraded to 10gb ram and a ssd with more than 500mb/s read/write speeds.) with linux mint I never saw any performance problems anywhere..

and the usb bug seems to be present here also. it is only visible by using usb 3.0 devices, so probably thats why I'm the only one experiencing it, since those are not that popular yet. however, it seems that with ubuntu 12.10 I now can recover from usb-system crashes without rebooting, just by disconnecting and reconnecting usb devices.

---

### Post by ambidextrvs on 2012-08-23
> **screemo said:**
> I'm using alpha3 with latest updates as of today. The asus-wmi deb is the 0.2 version and works fine on 3.5.x kernels - I believe the wiki is slightly out of date on that.

I can use xbacklight to change it, unfortunately the fn+f5/f6 is still mia ;(

the asus-wmi I use is attached.

Do you have ubuntu installed on the ssd or the hdd?
I tried removing the asus-wmi-dkms from kernel 3.5.0-11 but it says that the package isn't installed. It makes sense because I never installed the module via dkms. I just updated the kernel from 3.5.0-10 to 3.5.0-11.
Then I tried installing the asus-wmi deb 0.2 on the 3.5.0-10 kernel and everything went fine in the first reboot. However, once I turned off the computer and boot up again  I got stuck in the booting process.
So I booted in recovery mode, I choose 'normal boot' and I removed the asus-wmi kernel module which fixed my booting issue.
I believe this is associated with the behavior described on post #80 ([http://ubuntuforums.org/showpost.php?p=12114657&postcount=80](http://ubuntuforums.org/showpost.php?p=12114657&postcount=80))
Maybe there is a 'race condition' going on.

Should I file this as a bug?

---

### Post by kaefert66014235 on 2012-08-23
I've written myself a brightness script that uses the much finer controlable interface at /sys/class/backlight/intel_backlight/brightness which can go in very fine steps to complete darkness. Only bad thing about is that you need root permissions to access it. I've bound the keycombination strg+F6 to gksu ~/brightness-mod.sh 1 for increasing and strg+F5 to gksu ~/brightness-mod.sh 0 for decreasing brightness

To not have to enter the password every time you use it, I've followed this guide: [http://embraceubuntu.com/2006/01/25/make-sudogksudo-remember-passwords/](http://embraceubuntu.com/2006/01/25/make-sudogksudo-remember-passwords/)

You'll find the script attached if somebody might be interested.
If you don't like the gnome-shell notifications just out-comment line 63 of the script

UPDATE: Modified the script to first use the gnome interface for the steps 0 to 10, and only if you want to go below 0 which is not supported by the gnome interface, the script will use the intel_backlight interface

---

### Post by kaefert66014235 on 2012-08-25
okey, so about this issue that I was seeing (ubuntu 12.10 alpha3 with updates), that the ui is getting sluggish when moving windows between workspaces with strg+alt+shift+arrowkey (more sluggish the bigger & more complex the window, so browser window is the worst, simple texteditor or terminal works much better) is connected with the compiz plugin that you can find @ ccsm -> window managment -> place windows.

After disabling that plugin the moving of windows between workspaces works fine.

Another bug that I also only observe with that plugin enabled is that sometimes already opened windows get moved randomly to the bottom of the screen or get moved to another workspace (mostly the workspace on the far left)

---

### Post by borjaxvalencia on 2012-08-25
Hello. I have configured my own kernel, patching asus_wmi, and scripting brighness, and everythink is perefect now on my ux31a (i5, 128gb, hd+). Only one thing doesn't work righ: If I put an external hdmi monitor, if I turn off the internal monitor, the external only shows a red uniform across the screen, and I must to wait a few secodns and configuration get revert.
Any idea?
I

---

### Post by ambidextrvs on 2012-08-28
Hi, I just wanted to refer anybody having issues booting when using kernel >= 3.5.0-11 or when installing the asus-wmi kernel module, to this bug:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883)

---

### Post by danieleds on 2012-08-30
Thanks guys!

For those of you who are running Ubuntu 12.04 (edit: or 12.10 too), here's how I got Optimus (bumblebee) fully working on my UX32VD: [http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/](http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/)

Hope it helps!

---

### Post by kaefert66014235 on 2012-08-30
> **danieleds said:**
> Thanks guys!

For those of you who are running Ubuntu 12.04, here's how I got Optimus (bumblebee) fully working on my UX32VD: [http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/](http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/)

Hope it helps!

thanks for the link! Running 12.10 but it worked almosted the same (only had to manually change the second of those two ppas to distro  "precise" since this ppa is not yet configured for 12.10

---

### Post by danieleds on 2012-08-30
> **kaefert66014235 said:**
> thanks for the link! Running 12.10 but it worked almosted the same (only had to manually change the second of those two ppas to distro  "precise" since this ppa is not yet configured for 12.10
Thanks for the info, I updated the article to include 12.10 users ;)

---

### Post by ambidextrvs on 2012-08-30
> **danieleds said:**
> Thanks for the info, I updated the article to include 12.10 users ;)

Thanks! I was able to successfully install it on 12.10 too without the ubuntu-x-swat/x-update ppa.

---

### Post by mertvye on 2012-08-31
Hello,

I'm thinking of buying one of this, concretely UX31A with i5 processor, but I can't find how long the battery lasts in Ubuntu in normal conditions (browsing, Libreoffice, Latex, HTML editing, ...).

Could you please shed some light on this?

Thank you.

---

### Post by Tuxdude on 2012-08-31
> **mertvye said:**
> Hello,

I'm thinking of buying one of this, concretely UX31A with i5 processor, but I can't find how long the battery lasts in Ubuntu in normal conditions (browsing, Libreoffice, Latex, HTML editing, ...).

Could you please shed some light on this?

Thank you.

I have a UX32VD and it lasts a little over 3 hours on battery at 25% screen brightness.

---

### Post by screemo on 2012-08-31
> **mertvye said:**
> Hello,

I'm thinking of buying one of this, concretely UX31A with i5 processor, but I can't find how long the battery lasts in Ubuntu in normal conditions (browsing, Libreoffice, Latex, HTML editing, ...).

Could you please shed some light on this?

Thank you.

You can easily get 4 hours of battery, even more with jupiter or similar installed, it does very good on saving battery.

I have an UX32VD, so if you plan to upgrade the ssd or memory later, go get one of these instead - just a hint.

---

### Post by mertvye on 2012-09-01
> **screemo said:**
> You can easily get 4 hours of battery, even more with jupiter or similar installed, it does very good on saving battery.

I have an UX32VD, so if you plan to upgrade the ssd or memory later, go get one of these instead - just a hint.

Your comment together with the one provided by @TuxDude make me doubt about it. 

In any case I would go only for the ux31a (or the MBA) as I don't need the NVidia card and the extra weight while power consumption is an issue.

More inputs on this?

Thank you!

---

### Post by madmack on 2012-09-01
> **mertvye said:**
> Your comment together with the one provided by @TuxDude make me doubt about it. 

In any case I would go only for the ux31a (or the MBA) as I don't need the NVidia card and the extra weight while power consumption is an issue.

More inputs on this?

Thank you!

ux31a here. running arch linux (kernel v3.5.3) and can second the "easily get 4hr" with casual browsing and reading/typing.

My battery's power consumption sits at about 7-8 W which is better than my luck with any of my other recent laptops. I can push it to 6hr I believe although I haven't tried it.

good stuff in terms of battery consumption. :)

i also didn't need the second nvidia gpu. the integrated one is more than capable of playing 1080p content on my TV via HDMI using va-api. That's I'll need a GPU for.

---

### Post by screemo on 2012-09-01
> **madmack said:**
> ux31a here. running arch linux (kernel v3.5.3) and can second the "easily get 4hr" with casual browsing and reading/typing.

My battery's power consumption sits at about 7-8 W which is better than my luck with any of my other recent laptops. I can push it to 6hr I believe although I haven't tried it.

good stuff in terms of battery consumption. :)

i also didn't need the second nvidia gpu. the integrated one is more than capable of playing 1080p content on my TV via HDMI using va-api. That's I'll need a GPU for.

I also didn't need the gpu,  but I liked the better possibilities for upgrades. The performance/size of the ssd and amount of memory didn't impress me with ux31a,  

But it all depends on what you need of course. :-)

---

### Post by kaefert66014235 on 2012-09-17
Hi there!

I am running Ubuntu 12.10 on my UX32VD and am having big issues with my desktop with the updates that came over the last weeks (see [http://ubuntuforums.org/showthread.php?t=2058752](http://ubuntuforums.org/showthread.php?t=2058752) )

Has anybody else problems like these? What are you running on your UX32VD machines? I'm undecided what to do next, either set up a fresh ubuntu 12.10 beta1 installation or going back to linux mint 13 with cinnamon and give them another try.

---

### Post by screemo on 2012-09-17
> **kaefert66014235 said:**
> Hi there!

I am running Ubuntu 12.10 on my UX32VD and am having big issues with my desktop with the updates that came over the last weeks (see [http://ubuntuforums.org/showthread.php?t=2058752](http://ubuntuforums.org/showthread.php?t=2058752) )

Has anybody else problems like these? What are you running on your UX32VD machines? I'm undecided what to do next, either set up a fresh ubuntu 12.10 beta1 installation or going back to linux mint 13 with cinnamon and give them another try.

I have my UX32VD running right here on latest updates (from last night), no problems except for the messaging-applet not containing any entries (which I can live with).

I suggest you try with a fresh profile (ie. a new user on the same machine to see if you can get a working desktop). Sounds like a local issue to me atleast. I will be happy to help further.

---

### Post by kaefert66014235 on 2012-09-17
> **screemo said:**
> I have my UX32VD running right here on latest updates (from last night), no problems except for the messaging-applet not containing any entries (which I can live with).

I suggest you try with a fresh profile (ie. a new user on the same machine to see if you can get a working desktop). Sounds like a local issue to me atleast. I will be happy to help further.

tried that already, created a new user and logged in with it, but it looks the same. I also removed most of the packages I installed through ppas but that also did not have any effect. I guess I will have to do a fresh install...

---

### Post by screemo on 2012-09-17
> **kaefert66014235 said:**
> tried that already, created a new user and logged in with it, but it looks the same. I also removed most of the packages I installed through ppas but that also did not have any effect. I guess I will have to do a fresh install...

I imagine you already tried apt-get install ubuntu-desktop ?

Sometimes it helped to pull in needed dependencies for me.

Else, yes - a reinstall :(

---

### Post by kaefert66014235 on 2012-09-17
> **screemo said:**
> I imagine you already tried apt-get install ubuntu-desktop ?

Sometimes it helped to pull in needed dependencies for me.

Else, yes - a reinstall :(

Oh my god!!!! I LOVE YOU MAN! that was it!
Most of my bugs are gone now!

I would have thought that ubuntu-desktop will be installed by default when I install from a default ubuntu image (not server but desktop image..)

UPDATE: one of the more anoying bugs thats still left is that when I use the alt+ mouse button2 key combination from the "resize window" compiz plugin, then compiz crashes and restarts.

UPDATE2: I've documented the list of bugs that I still experience after this great fix from screemo again over at the other thread, could somebody look at it and comment if you're also seeing those?
[http://ubuntuforums.org/showthread.php?p=12244005#post12244005](http://ubuntuforums.org/showthread.php?p=12244005#post12244005)

---

### Post by screemo on 2012-09-17
> **kaefert66014235 said:**
> Oh my god!!!! I LOVE YOU MAN! that was it!
Most of my bugs are gone now!

I would have thought that ubuntu-desktop will be installed by default when I install from a default ubuntu image (not server but desktop image..)

UPDATE: one of the more anoying bugs thats still left is that when I use the alt+ mouse button2 key combination from the "resize window" compiz plugin, then compiz crashes and restarts.

UPDATE2: I've documented the list of bugs that I still experience after this great fix from screemo again over at the other thread, could somebody look at it and comment if you're also seeing those?
[http://ubuntuforums.org/showthread.php?p=12244005#post12244005](http://ubuntuforums.org/showthread.php?p=12244005#post12244005)

Glad to help :) - it has tricked me more than a few times :)

Please try to reset your unity settings (type 'unity --reset' in a terminal without sudo)

Reset compiz aswell:

rm -rf ~/.config/compiz-1/compizconfig/*

---

### Post by kaefert66014235 on 2012-09-17
> **screemo said:**
> Glad to help :) - it has tricked me more than a few times :)

Please try to reset your unity settings (type 'unity --reset' in a terminal without sudo)

Reset compiz aswell:

rm -rf ~/.config/compiz-1/compizconfig/*

hmm, those two don't seem to have any effect on the bugs left.

---

### Post by powersurge360 on 2012-09-19
I'm thinking about getting this laptop and was wondering about compatibility. I've looked at the official AsusZenbookPrime page, but some of the stuff there seems to be outdated and I've combed through this forum, but I'm having a hard time keeping straight what currently doesn't work with this model.

Is anyone able/willing to give me a short-list of what still doesn't work with 12.04? What about with the 12.10 release that releases next month (I've noticed that some people are running 12.10 betas in this thread).

Just a short-list will be fine, and maybe if there is a solution note that there is one (I can likely find the solution myself).

---

### Post by kaefert66014235 on 2012-09-20
I've observed yesterday evening that with the latest updates that my power consumption is really a lot less then it was before (when idle).

With quite low display backlight and without doing anything on the machine I get down to 9,5 Watt. 

Last week the lowest I could get was about 14 Watt.

The worst thing for the power consumption is to switch between workspaces, and also afterwards as long as you keep strg+alt pressed which keeps the workspaces overview visible in the middle of the screen - that makes compiz take really a lot of cpu power and that gets the power consumption up to 20 watts.

---

### Post by danieleds on 2012-09-22
> **powersurge360 said:**
> I'm thinking about getting this laptop and was wondering about compatibility. I've looked at the official AsusZenbookPrime page, but some of the stuff there seems to be outdated and I've combed through this forum, but I'm having a hard time keeping straight what currently doesn't work with this model.

Is anyone able/willing to give me a short-list of what still doesn't work with 12.04? What about with the 12.10 release that releases next month (I've noticed that some people are running 12.10 betas in this thread).

Just a short-list will be fine, and maybe if there is a solution note that there is one (I can likely find the solution myself).
the only things without a solution are the ambient light sensor and the F5/F6 keys to change screen brightness

---

### Post by kaefert66014235 on 2012-09-22
has anybody with an UX32VD tried to use a 3G-modem with his notebook? It produces crashes and freezes for me, but with a modem that works fine on other linux machines (0af0:6971). and it both happens with Ubuntu 12.10 and linux mint 13 (=12.04)

---

### Post by kyosaku on 2012-09-25
Had problems with usb modeswitching when I tried hooking up my old 3G Huawei 122 on any of the usb 3.0 ports of my UX32vd-r400v.  These problems resolved after installing and using Sakis3g ([http://www.sakis3g.org/](http://www.sakis3g.org/)).  

On the other hand, I did experience a few crashes on Ubuntu 12.04 trying to copy gigs of files from an external USB-Drive to my hard drive while working on the desktop in parallel.  Crash was really bad: no ctrl-alt-f1 or alt-sysrq-REISUB response and had to do a "hard shut down".  Otherwise the system seems stable.

---

### Post by kaefert66014235 on 2012-09-26
> **kyosaku said:**
> Had problems with usb modeswitching when I tried hooking up my old 3G Huawei 122 on any of the usb 3.0 ports of my UX32vd-r400v.  These problems resolved after installing and using Sakis3g ([http://www.sakis3g.org/](http://www.sakis3g.org/)).  

On the other hand, I did experience a few crashes on Ubuntu 12.04 trying to copy gigs of files from an external USB-Drive to my hard drive while working on the desktop in parallel.  Crash was really bad: no ctrl-alt-f1 or alt-sysrq-REISUB response and had to do a "hard shut down".  Otherwise the system seems stable.

I tried to get my 3g modem to work a few times yesterday evening, but either if it got recognised and listed in my "lsusb" output, then the system froze within 2 minutes and I need to hardreset. And the other times when it didn't freeze my system, it was never listed in the lsusb output and therefore didn't work.

The thing with freezes on using usb disks I can also confirm, but this is very rare, most of the time usb disks work quite well, although sometimes with one particular usb-disk of mine always gets disconnected and remounted afterwards.

---

### Post by diego851 on 2012-09-26
hi everybody, 
I have an ux32vd-r4002v, I have ubuntu 12.04 on it and it works well but I would like to upgrade the kernel or upgrade to quantal to resolve some issues..u know what i'm talking about.

So, I don't know why when I upgrade the kernel or install 12.10, the computer don't boot anymore... or better, it boots only if I use the old kernel (3.2.0) or the first time i try to boot the new kernel after i booted with 3.2.0.

If I alternate kernels it quite always boot, if i boot 2 times with new kernel i receive a blank screen after the grub screen. If I try recovery mode it desn't boot.

I installed the root directory in dev\sdb (the 32 gb ssd).

Has anyone the same problems or any suggest?

---

### Post by yelloBeans on 2012-09-27
Hello 

I am new into Ubuntu and owner of ux32vd.

I just finished installing v12.04.

However before continuing finding and updating drivers, I need to figure out this problem which I hope some of you here are able to help me with.

My fan, the one my right hand is spinning constantly due to heat but with me doing nothing on my computer. Waited for 10 min to check up if there were some workload to finish up but with no help. On windows 7 it runs quietly with no fans spinning during idle(45c).

Anyone might help me up, cause I do not like that it runs hot at idle??

---

### Post by oKtosiTe on 2012-09-28
> **screemo said:**
> Thanks I will check it out :)

I can confirm it works on kernel 3.2.0, but I get strange lockups sometimes I didn't see on 3.5rc kernel - think I will move to that, and maybe adapt the patch when quantal becomes more stable.

Anyone noticed that hotkey on the A-key - is that for automatic keyboard backlight or the screen ?

It is supposed to toggle the ambient light sensor. Just tested it on Windows.

---

### Post by touser on 2012-09-29
HI everyone,

I just picked up a UX31A and have pretty much everything i care about working well. The one big hangup i have left is multitouch gestures. Has anyone had any success setting up 2 or 3 finger swipes for back/forward in we browsers/file managers etc. And a 3 or 4 finger up or down swipe for the compiz expose equivalent? Coming from using OS X laptops i find it impossible to use a laptop without these basic gestures anymore. It seems touchegg is capable of this, has anyone had success with it on 12.04 or 12.10?  Thanks!

---

### Post by kaefert66014235 on 2012-09-30
> **touser said:**
> HI everyone,

I just picked up a UX31A and have pretty much everything i care about working well. The one big hangup i have left is multitouch gestures. Has anyone had any success setting up 2 or 3 finger swipes for back/forward in we browsers/file managers etc. And a 3 or 4 finger up or down swipe for the compiz expose equivalent? Coming from using OS X laptops i find it impossible to use a laptop without these basic gestures anymore. It seems touchegg is capable of this, has anyone had success with it on 12.04 or 12.10?  Thanks!

Well I am using Ubuntu 12.10 and I have experienced that there are a lot of default touchpad gestures:

-) 2 finger tap: right mouse click
-) 2 finger movement: scroll
-) 3 finger tap: activate buttons to move and resize the window more easily
-) 3 finger movement: move the current window
-) 4 fingers movement to the right: show the unity bar on the left
-) 4 fingers movement to the left: hide the unity bar on the left
-) 4 fingers tap: does the same as the windows button: show the unity starter (or hide it if its already there)

But I have no idea if there is some easy way to configure these gestures.

---

### Post by cbrand0 on 2012-09-30
Hi there,

I just installed the current Quantal version on my UX32VD. The only thing really annoying me is that the fan goes constantly even though the machine just idles. Any hints what I can do about this? I am using bios version 211, maybe version 206 or 207 handle this better?

---

### Post by diego851 on 2012-09-30
Hi, is there anyone who has ubuntu 12.10 or 12.04 with a newer kernel on a UX32VD-R4002V (i7 processor)?

If I install a never kernel than 3.2.0 linux won't boot on my machine, and I need it cause i have to install bumblebee to use a CFD (OpenFOAM) software for my thesis!!

Can anyone help please?

Thanks a lot,

Diego.

---

### Post by cbrand0 on 2012-09-30
Hi diego851,

I have the exact same machine. Mine boots with the latest 12.10 version and mine boots just fine. With 12.04 I had awkward problems while booting. Sometimes it wouldn't boot without a usb mouse connected, sometimes it helped to connect an external monitor via hdmi. I don't know which boot option you chose, but with my machine "quiet splash" worked better than "nomodeset" in the /etc/default/grub config.

---

### Post by diego851 on 2012-09-30
Thanks Cbrand0,

I didn't change anything in /etc/default/grub config, i've never had problems with 12.04 and with 12.10, can't find a way to boot.

I've done a new try today installing today's "dayli build" with a fresh install but it don't boot. Blank screen after grub page.


It boots only in recovery mode, do you have any suggest for me?

---

### Post by Tuxdude on 2012-10-03
For folks booting Ubuntu (or actually any 3.5+ kernel) off an SSD and have not disabled the asus-wmi module, you'll be seeing the kernel panics (the ones with the caps lock key flashing).

I've found a workaround which seems to work for me. Type this in a terminal:```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/blacklist-btusb.conf
echo "/sbin/modprobe btusb" | sudo tee /etc/rc.local
```

This basically disables btusb during the modprobe stage in the bootup, and insteads inserts the module at the very end of the bootup.

FYI - btusb is a Bluetooth USB module, which seems to be having a race condition in timing when booting off SSD causing kernel panics.

Let me know if this works or does not work for you.

All I could find was based on the info in the bug report #1041883, one of the folks mentioned about the asus_wmi_rfkill_init() function which seems to be handing the RFKILL switch i.e Fn+F2 key (for Wifi, BT, 3G, etc.). So I tried disabling few modules during the bootup corresponding to these and finally found out a very highly likely module causing the problem.

More info here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883/comments/112](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883/comments/112)

---

### Post by diego851 on 2012-10-03
> **Tuxdude said:**
> For folks booting Ubuntu (or actually any 3.5+ kernel) off an SSD and have not disabled the asus-wmi module, you'll be seeing the kernel panics (the ones with the caps lock key flashing).

I've found a workaround which seems to work for me. Type this in a terminal:```
echo "blacklist btusb" | sudo tee /etc/blacklist-btusb.conf
echo "/sbin/modprobe btusb" | sudo tee /etc/rc.local
```

This basically disables btusb during the modprobe stage in the bootup, and insteads inserts the module at the very end of the bootup.

FYI - btusb is a Bluetooth USB module, which seems to be having a race condition in timing when booting off SSD causing kernel panics.

Let me know if this works or does not work for you.

All I could find was based on the info in the bug report #1041883, one of the folks mentioned about the asus_wmi_rfkill_init() function which seems to be handing the RFKILL switch i.e Fn+F2 key (for Wifi, BT, 3G, etc.). So I tried disabling few modules during the bootup corresponding to these and finally found out a very highly likely module causing the problem.

More info here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883/comments/112](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1041883/comments/112)


Thanks a lot anyway but it didn't work:(

---

### Post by Tuxdude on 2012-10-03
> **diego851 said:**
> Thanks a lot anyway but it didn't work:(

Just to confirm, could you try disabling Bluetooth in the BIOS ?

Press F12 during bootup and I believe the setting is Located Under Advanced Settings menu.

---

### Post by Tuxdude on 2012-10-04
There was a typo in the previous set of commands - it should instead be:

```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/blacklist-btusb.conf
echo "/sbin/modprobe btusb" | sudo tee /etc/rc.local
```

In other words, the file blacklist-btusb.conf should be inside the /etc/modprobe.d directory and not just /etc

---

### Post by diego851 on 2012-10-06
> **Tuxdude said:**
> There was a typo in the previous set of commands - it should instead be:

```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/blacklist-btusb.conf
echo "/sbin/modprobe btusb" | sudo tee /etc/rc.local
```

In other words, the file blacklist-btusb.conf should be inside the /etc/modprobe.d directory and not just /etc

I thank you for your help but i can't anymore try your suggestion for now cause i reinstalled Quantal on the hard disk and now boots without problems! But i'm interested in using the ssd, it was very faster than the HD; I will let you know when I will try it!
thanks again

---

### Post by Tuxdude on 2012-10-07
BTW, does anyone know if the iwlwifi and Wireless-N mode issue has been fixed in the Quantal kernel ?

With 54 Mbps G-mode the effective throughput is low especially when I want to transfer data over the network between devices in my home network :|

---

### Post by kaefert66014235 on 2012-10-07
> **Tuxdude said:**
> BTW, does anyone know if the iwlwifi and Wireless-N mode issue has been fixed in the Quantal kernel ?

With 54 Mbps G-mode the effective throughput is low especially when I want to transfer data over the network between devices in my home network :|

I am running quantal with latest updates, and the wifi-n doesn't look like fixeed to me, I have timespans of multiple seconds where no information is exchanged when using an n wifi

---

### Post by screemo on 2012-10-07
> **kaefert66014235 said:**
> I am running quantal with latest updates, and the wifi-n doesn't look like fixeed to me, I have timespans of multiple seconds where no information is exchanged when using an n wifi

I think this issue has gotten a whole lot better, I seldom have any problems. Before this would happen all the time, and G was the only stable wireless to use.

---

### Post by Tuxdude on 2012-10-07
Since the issue is not Ubuntu centric, but rather a problem with the upstream kernel and iwlwifi driver - I tried with openSUSE 12.2 running a 3.6 kernel and I observed that although the connection looks stable - the "Tx Excessive Retries" and "Invalid Misc" counters keeps increasing rapidly.

@screemo - Is that what you experience as well ?

---

### Post by nhart12 on 2012-10-09
Hello all, Im hoping for some help with the function f5+f6 keys. 

I have gotten them working by using the script here:
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_Backlight_Method_2](https://wiki.archlinux.org/index.php/ASUS_Zenbook_Prime_UX31A#Screen_Backlight_Method_2)

But the problem is that when I go to adjust brightness up it is extremely slow when doing so, but brightness down behaves just as expected..

Also I was wondering if there were better drivers for the trackpad available? because the multi-touch gestures can sometimes be unpredictable..

I am running 12.1 and other than that everything seems to work perfectly out of the box..

---

### Post by wild_oscar on 2012-10-14
Hi,

I'm considering buying a UX31A (even though the 4GB of ram might be short for Java programming). 

One of the interesting features announced is the very fast sleep-to-wake time of these ultrabooks. In ubuntu, does this work, or is it just in Windows? ie:

1) What is the average start-up time?
2) Do you power off or hibernate/suspend? What's the wake-up time?

---

### Post by Tuxdude on 2012-10-14
> **wild_oscar said:**
> Hi,

I'm considering buying a UX31A (even though the 4GB of ram might be short for Java programming). 

One of the interesting features announced is the very fast sleep-to-wake time of these ultrabooks. In ubuntu, does this work, or is it just in Windows? ie:

1) What is the average start-up time?
2) Do you power off or hibernate/suspend? What's the wake-up time?

The under 8-second resume for Ultrabooks is done by using the 32-GB SSD to store the paging file and load it back into memory while resuming from hibernate.

I didn't find this feature much useful - since I installed 2 different distros - openSUSE and Ubuntu on the SSD. A cold boot takes less than 15 seconds - which is good enough for me :) If you boot off the regular hard drive it would be longer for sure.

I suspend my UX32VD often. Though it loses roughly 1% battery every hour in 'suspend' mode - which is quite high. Not sure if others see the same results as me in this regard.

---

### Post by wonghang on 2012-10-15
Hi all,

I got a new Asus Zenbook UX32VD last week and successfully installed ubuntu 12.04.
Everything works fine. Except for the nvidia GPU. I followed the guide on the internet and this thread, installed bumblebee and latest driver of nvidia. optirun works fine.
However, I got exactly the same problem similar to ambidextrvs:

> **ambidextrvs said:**
> Hi,
I had a problem for the last couple of days. I was on ubuntu 12.10 with kernel 3.5-8 and suddenly one day (without performing system updates or tweaks) I wasn't being able to get to the login screen. The screen was off and the caps-lock led was blinking.


I also tried the kernel command line:

[http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743](http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743)

But does not work for me.
I also tried for "nomodeset"

Now, I can only get to the login screen by switching the driver of X server into fbdev. But I lost the desktop effect.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "fbdev"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
EndSection
```

Any idea on getting the Intel Ivy Bridge GPU works again?
Thanks.

I am running:

```
# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
# uname -r -i -o
3.2.0-32-generic-pae i386 GNU/Linux
# lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Panther Point Thermal Management Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 1140 (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

```

---

### Post by danieleds on 2012-10-15
@[wonghang]("http://ubuntuforums.org/member.php?u=1003556"): you have a 32-bit kernel for any particular reason?

---

### Post by screemo on 2012-10-15
> **wonghang said:**
> Hi all,

I got a new Asus Zenbook UX32VD last week and successfully installed ubuntu 12.04.
Everything works fine. Except for the nvidia GPU. I followed the guide on the internet and this thread, installed bumblebee and latest driver of nvidia. optirun works fine.
However, I got exactly the same problem similar to ambidextrvs:



I also tried the kernel command line:

[http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743](http://askubuntu.com/questions/169440/distorted-graphics-problem/169743#169743)

But does not work for me.
I also tried for "nomodeset"

Now, I can only get to the login screen by switching the driver of X server into fbdev. But I lost the desktop effect.

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "fbdev"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
EndSection
```

Any idea on getting the Intel Ivy Bridge GPU works again?
Thanks.

I am running:

```
# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
# uname -r -i -o
3.2.0-32-generic-pae i386 GNU/Linux
# lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Device 0153 (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation Panther Point Thermal Management Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation Device 1140 (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)

```

The capslock blinking error is related to a race condition on bt-usb, if I boot with a nano usb-receiver it will almost always crash. Remove the usb-receiver and it will boot normally again.

[http://ubuntuforums.org/showthread.php?t=2005999&page=19](http://ubuntuforums.org/showthread.php?t=2005999&page=19)

You should also switch to ubuntu 12.10 64bit (will add native support for most hotkeys, working usb network adapter, et al.), and forget about optimus for now - there are some work going on to support this in the binary driver going forward.

[http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html](http://www.pcworld.com/article/261874/coming_soon_to_linux_nvidia_optimus_graphics_support.html)
[http://www.phoronix.com/scan.php?page=news_item&px=MTE5MDY](http://www.phoronix.com/scan.php?page=news_item&px=MTE5MDY)

---

### Post by wonghang on 2012-10-15
So, I will get my video card (intel one) working if I switch to 64 bits kernel? or I may get the video card work by blacklisting bt-usb?

I got nvidia working with bumblebee.
I used the computer mainly for working, and I require my GPU to work as I will write program using CUDA. 

One of the reason that I used 32bits kernel is that I had bad experience when using java applet when I was using lucid 64 bits. (And isn't on the ubuntu website that 32 bits is recommended for desktop?)

---

### Post by screemo on 2012-10-16
> **wonghang said:**
> So, I will get my video card (intel one) working if I switch to 64 bits kernel? or I may get the video card work by blacklisting bt-usb?

I got nvidia working with bumblebee.
I used the computer mainly for working, and I require my GPU to work as I will write program using CUDA. 

One of the reason that I used 32bits kernel is that I had bad experience when using java applet when I was using lucid 64 bits. (And isn't on the ubuntu website that 32 bits is recommended for desktop?)

Ok, I wasn't aware that you needed the dedicated GPU that much - I mainly chose the UX32VD for the expandability over UX31A. 

I know bumblebee has problems on quantal, so I would not advise you to move to that at the moment. The situation for the java plugin on 64bit has improved much, so there's really no difference between them (for a long period the java plugin wasn't available in 64bit java for linux).

Blacklisting bt-usb was just to avoid the caps-lock/crash when you boot.

To get the intel video driver working again, maybe you should try the xorg-edgers repo to get the newest graphics drivers for it ?

Also the 3.5.x kernel series has better support for Ivy bridge (except for bumblebee afaik).

So I guess you're a little in limbo-land at the moment, with things improving but not really ready yet.

---

### Post by kaefert66014235 on 2012-10-16
I'm running Ubuntu 12.10 64bit Version, and for me the guide for installing bumblebee worked, however I rarely use it since the performance gain doesn't feel that big, but the power consumption increases by 10 Watts.

```

user@Machine:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
239 frames in 5.0 seconds = 47.650 FPS
260 frames in 5.0 seconds = 51.842 FPS
250 frames in 5.0 seconds = 49.999 FPS
255 frames in 5.0 seconds = 50.829 FPS
242 frames in 5.0 seconds = 48.242 FPS
^C
user@Machine:~$ 
user@Machine:~$ optirun glxgears
1480 frames in 5.0 seconds = 295.075 FPS
1549 frames in 5.0 seconds = 307.470 FPS
1665 frames in 5.0 seconds = 330.982 FPS
1396 frames in 5.0 seconds = 277.128 FPS
1535 frames in 5.0 seconds = 306.568 FPS
^C[23298.624081] [WARN]Received Interrupt signal.
user@Machine:~$ 

```

---

### Post by screemo on 2012-10-16
> **kaefert66014235 said:**
> I'm running Ubuntu 12.10 64bit Version, and for me the guide for installing bumblebee worked, however I rarely use it since the performance gain doesn't feel that big, but the power consumption increases by 10 Watts.

```

user@Machine:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
239 frames in 5.0 seconds = 47.650 FPS
260 frames in 5.0 seconds = 51.842 FPS
250 frames in 5.0 seconds = 49.999 FPS
255 frames in 5.0 seconds = 50.829 FPS
242 frames in 5.0 seconds = 48.242 FPS
^C
user@Machine:~$ 
user@Machine:~$ optirun glxgears
1480 frames in 5.0 seconds = 295.075 FPS
1549 frames in 5.0 seconds = 307.470 FPS
1665 frames in 5.0 seconds = 330.982 FPS
1396 frames in 5.0 seconds = 277.128 FPS
1535 frames in 5.0 seconds = 306.568 FPS
^C[23298.624081] [WARN]Received Interrupt signal.
user@Machine:~$ 

```

What kernel are you using in 12.04 ?

---

### Post by kaefert66014235 on 2012-10-16
> **screemo said:**
> What kernel are you using in 12.04 ?

If you're talking to me, which I tink since you quoted my post, I'm running 12.10, and the kernel is just what I got by default from the upgrades:

Linux Machinename 3.5.2-030502-generic #201208151151 SMP Wed Aug 15 15:52:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by screemo on 2012-10-16
> **kaefert66014235 said:**
> If you're talking to me, which I tink since you quoted my post, I'm running 12.10, and the kernel is just what I got by default from the upgrades:

Linux Machinename 3.5.2-030502-generic #201208151151 SMP Wed Aug 15 15:52:12 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Sorry, I was talking to you :) - could you please share the instructions for bumblebee on 12.10 ? I have tried it for a month ago without success ;(

---

### Post by kaefert66014235 on 2012-10-16
> **screemo said:**
> Sorry, I was talking to you :) - could you please share the instructions for bumblebee on 12.10 ? I have tried it for a month ago without success ;(

hmmm, well its already about a month ago that I set this up, but I will try to find the place from where I took the instructions for it, wait a few minutes

UPDATE: here it is:
[http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/](http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/)

Though you can leave out this repository: ppa:ubuntu-x-swat/x-updates - it doesn't seem to be required

---

### Post by screemo on 2012-10-16
> **kaefert66014235 said:**
> hmmm, well its already about a month ago that I set this up, but I will try to find the place from where I took the instructions for it, wait a few minutes

UPDATE: here it is:
[http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/](http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/)

Though you can leave out this repository: ppa:ubuntu-x-swat/x-updates - it doesn't seem to be required

Ah, There's some extra steps in this guide compared to what I tried - thanks a bunch for the info :)

@wonghang - this might be the way for you to get all things working (newer xorg/intel, and bumblebee).

---

### Post by screemo on 2012-10-16
> **screemo said:**
> Ah, There's some extra steps in this guide compared to what I tried - thanks a bunch for the info :)

@wonghang - this might be the way for you to get all things working (newer xorg/intel, and bumblebee).

Wow, it works :)

However speed is nothing to brag about:

```

sfs@sfs-laptop:~$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xb8
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
60.158367 frames/sec - 67.136738 Mpixels/sec
60.065217 frames/sec - 67.032783 Mpixels/sec
^C
sfs@sfs-laptop:~$ optirun glxspheres 
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 620M/PCIe/SSE2
84.314517 frames/sec - 94.095002 Mpixels/sec
87.914984 frames/sec - 98.113122 Mpixels/sec
^C[ 1254.324329] [WARN]Received Interrupt signal.

```

---

### Post by kaefert66014235 on 2012-10-16
> **screemo said:**
> Wow, it works :)

However speed is nothing to brag about: ...

yep, I told you so.. It just uses huge amounts of power (10 Watts extra) but performance wise it doesn't improve that much compared to the intel graphics

update: you seem to get much better performance than I do, but maybe the reason is that I'm currently running with 2 extra monitors connected, total 3 monitors, aranged in 2 rows and 2 columns, therefore 4k virtual desktop size.

```

user@Machine:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0xb8
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
30.763001 frames/sec - 34.331509 Mpixels/sec
34.325968 frames/sec - 38.307781 Mpixels/sec
31.801142 frames/sec - 35.490075 Mpixels/sec
32.488114 frames/sec - 36.256735 Mpixels/sec
35.933369 frames/sec - 40.101640 Mpixels/sec
38.615648 frames/sec - 43.095064 Mpixels/sec
39.105916 frames/sec - 43.642202 Mpixels/sec
38.113216 frames/sec - 42.534349 Mpixels/sec

user@Machine:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 620M/PCIe/SSE2
46.954801 frames/sec - 52.401557 Mpixels/sec
54.079394 frames/sec - 60.352603 Mpixels/sec
54.493972 frames/sec - 60.815272 Mpixels/sec
59.928638 frames/sec - 66.880360 Mpixels/sec
60.984530 frames/sec - 68.058735 Mpixels/sec
59.748090 frames/sec - 66.678869 Mpixels/sec
58.746089 frames/sec - 65.560636 Mpixels/sec
60.489176 frames/sec - 67.505921 Mpixels/sec
62.087975 frames/sec - 69.290180 Mpixels/sec
61.089511 frames/sec - 68.175894 Mpixels/sec
59.929330 frames/sec - 66.881133 Mpixels/sec
59.922131 frames/sec - 66.873098 Mpixels/sec
63.072084 frames/sec - 70.388445 Mpixels/sec
59.808048 frames/sec - 66.745781 Mpixels/sec
61.613387 frames/sec - 68.760540 Mpixels/sec
user@Machine:~$ 

```

---

### Post by screemo on 2012-10-16
> **kaefert66014235 said:**
> yep, I told you so.. It just uses huge amounts of power (10 Watts extra) but performance wise it doesn't improve that much compared to the intel graphics

update: you seem to get much better performance than I do, but maybe the reason is that I'm currently running with 2 extra monitors connected, total 3 monitors, aranged in 2 rows and 2 columns, therefore 4k virtual desktop size.

```

user@Machine:~$ glxspheres
Polygons in scene: 62464
Visual ID of window: 0xb8
Context is Direct
OpenGL Renderer: Mesa DRI Intel(R) Ivybridge Mobile 
30.763001 frames/sec - 34.331509 Mpixels/sec
34.325968 frames/sec - 38.307781 Mpixels/sec
31.801142 frames/sec - 35.490075 Mpixels/sec
32.488114 frames/sec - 36.256735 Mpixels/sec
35.933369 frames/sec - 40.101640 Mpixels/sec
38.615648 frames/sec - 43.095064 Mpixels/sec
39.105916 frames/sec - 43.642202 Mpixels/sec
38.113216 frames/sec - 42.534349 Mpixels/sec

user@Machine:~$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 620M/PCIe/SSE2
46.954801 frames/sec - 52.401557 Mpixels/sec
54.079394 frames/sec - 60.352603 Mpixels/sec
54.493972 frames/sec - 60.815272 Mpixels/sec
59.928638 frames/sec - 66.880360 Mpixels/sec
60.984530 frames/sec - 68.058735 Mpixels/sec
59.748090 frames/sec - 66.678869 Mpixels/sec
58.746089 frames/sec - 65.560636 Mpixels/sec
60.489176 frames/sec - 67.505921 Mpixels/sec
62.087975 frames/sec - 69.290180 Mpixels/sec
61.089511 frames/sec - 68.175894 Mpixels/sec
59.929330 frames/sec - 66.881133 Mpixels/sec
59.922131 frames/sec - 66.873098 Mpixels/sec
63.072084 frames/sec - 70.388445 Mpixels/sec
59.808048 frames/sec - 66.745781 Mpixels/sec
61.613387 frames/sec - 68.760540 Mpixels/sec
user@Machine:~$ 

```

But now it works, so I guess that will prove useful someday - thanks for your time, and maybe @wonghang will be able to work on CUDA now :)

---

### Post by wonghang on 2012-10-16
> **screemo said:**
> 
So I guess you're a little in limbo-land at the moment, with things improving but not really ready yet.

Thank you very much for your help. I will stay and wait for latest driver release.

However, I also discovered that if I run
gfxpayload=text
when booting the kernel. I will get blank screen even if I used fbdev for my xserver. Just an information :P

---

### Post by wonghang on 2012-10-16
> **kaefert66014235 said:**
> I'm running Ubuntu 12.10 64bit Version, and for me the guide for installing bumblebee worked, however I rarely use it since the performance gain doesn't feel that big, but the power consumption increases by 10 Watts.


sorry...how do you measure the power consumption? there is a command / tool on linux for that?

---

### Post by wonghang on 2012-10-16
> **screemo said:**
> Ah, There's some extra steps in this guide compared to what I tried - thanks a bunch for the info :)

@wonghang - this might be the way for you to get all things working (newer xorg/intel, and bumblebee).

I got bumblebee working by using latest nvidia driver 

```
NVRM: loading NVIDIA UNIX x86 Kernel Module  304.51  Tue Sep 18 17:36:24 PDT 2012
```

But xorg/intel failure suddenly two days ago.

---

### Post by danieleds on 2012-10-16
> **wonghang said:**
> sorry...how do you measure the power consumption? there is a command / tool on linux for that?
if on 12.10, you can use powertop

---

### Post by xicosm on 2012-10-19
Hello!

I just received my Zenbook UX32A and wanted to ask if anyone replaced the standard drive with an ssd.

I'm considering either use the internal 24G ssd as the / install point for Ubuntu then the standard drive to be mounted as /home or replace the drive with a ssd.

If I do replace the drive with a ssd, could I use the internal ssd for the same purpouse windows does? (which I believe is just so you can sleep/wake up real quick).

Cheers

---

### Post by kaefert66014235 on 2012-10-20
> **xicosm said:**
> Hello!

I just received my Zenbook UX32A and wanted to ask if anyone replaced the standard drive with an ssd.

I'm considering either use the internal 24G ssd as the / install point for Ubuntu then the standard drive to be mounted as /home or replace the drive with a ssd.

If I do replace the drive with a ssd, could I use the internal ssd for the same purpouse windows does? (which I believe is just so you can sleep/wake up real quick).

Cheers

I replaced the disk with a ssd, because the internal ssd has really bad write performance. Benchmark:

[http://kaefert.is-a-geek.org/mediawiki/index.php/File:Asus_Zenbook_UX32VD_-_24GB_SSD_Performance.png](http://kaefert.is-a-geek.org/mediawiki/index.php/File:Asus_Zenbook_UX32VD_-_24GB_SSD_Performance.png)

---

### Post by xicosm on 2012-10-20
Thanks!

So, are you using the internal SSD for anything?

---

### Post by kaefert66014235 on 2012-10-20
well, for testing new distros without distroying my main one ;)

---

### Post by screemo on 2012-10-21
> **xicosm said:**
> Hello!

I just received my Zenbook UX32A and wanted to ask if anyone replaced the standard drive with an ssd.

I'm considering either use the internal 24G ssd as the / install point for Ubuntu then the standard drive to be mounted as /home or replace the drive with a ssd.

If I do replace the drive with a ssd, could I use the internal ssd for the same purpouse windows does? (which I believe is just so you can sleep/wake up real quick).

Cheers

Keep it simple - forget about that internal SSD, and just install everything on a SSD that replaces the standard HDD. 

The internal SSD is slow/small, and it isn't worth the extra work to install anything on it.. 

(thats just my opinion though ;)

EDIT: windows does nothing special besides writing the hibernate file to the internal ssd.

---

### Post by xicosm on 2012-10-22
Thanks!

Will probably do that.

---

### Post by rjma on 2012-10-22
Hi, I need some help.

I've installed Ubuntu in my Zenbook, with Windows, and I've run boot-repair so I can access Ubuntu and windoes without problems, but now I need to make a recovery on windows, and when starting my pc and pressing F9 the recovery doesn't start, it jumos right to GRUB. What should I do? I've ran boot-repair again but still the same.

Please help!

---

### Post by kaefert66014235 on 2012-10-23
the only thing that runs before grub, is the bios. the chance to enter windows recovery comes after you've told grub to boot windows

---

### Post by danieleds on 2012-10-23
> **rjma said:**
> Hi, I need some help.

I've installed Ubuntu in my Zenbook, with Windows, and I've run boot-repair so I can access Ubuntu and windoes without problems, but now I need to make a recovery on windows, and when starting my pc and pressing F9 the recovery doesn't start, it jumos right to GRUB. What should I do? I've ran boot-repair again but still the same.

Please help!
Are you sure you didn't delete the recovery partition on /dev/sda?

---

### Post by rjma on 2012-10-23
> **danieleds said:**
> Are you sure you didn't delete the recovery partition on /dev/sda?

Yes, I'm sure. It appears in GParted.

---

### Post by pasisti on 2012-10-25
I'm having some big trouble with UX32VD (non-FHD model) and ubuntu 12.10. It seems to have something to do with the display or graphics, long explanation follows:

At first I tried to use a LiveUSB (works on my other computer) but it got stuck to a black screen after choosing "Try without installing". Then I tried to use the nomodeset-option but it got stuck in a few different places: 
 - Check battery state
 - Starting crash report submission daemon
 - Stopping acronymous (something, I don't remember)

Then I tried the install option. The black screen is still there but I heard the Ubuntu sound! Finally I tried to use my TV via HDMI to see if it would work and it did. I could see the installation menu and install the OS this way. I thought that maybe this could be fixed with updates or drivers after installing. I installed Ubuntu 12.10 using the UEFI mode on LiveUsb and the basic install option for dual boot with Windows 7.

After installing, I could use the OS well with my TV monitor. I installed all the updates and restarted without external monitor.. Then came the black screen again! And after restarting again I couldn't use the external monitor either. And no ubuntu sound at all, so the OS was not starting.

I reinstalled from the USB with my TV as monitor many times and the result was always the same: It works well if I use the external monitor but the first time I try to boot with the internal monitor it messes up the OS so that it won't boot anymore. I used mostly the "Remove existing Ubuntu 12.10 and install," but one time I tried the one that only repairs the OS (no difference). Here are the different ways I tried:
 - No updates whatsoever
 - Only updates and no Nvidia drivers
 - Updates and Nvidia drivers
 - Updates and bumblebee drivers

None of them works. Of course I tried rebooting with the external monitor once before disconnecting to see that the updates are OK in the first place. This is strange as everything else within Ubuntu works (sound, trackpad, unity, webcam etc) but the internal display doesn't and booting with it screws up the OS install. I tried the Display settings but it didn't recognize the internal display at all.

One time the internal display worked in mirroring mode. I have to admit that I don't know what I did differently as it was the first boot after the evening when I decided to give up. Even this time trying to boot without the external monitor ended up messing the OS.

Sorry for the long post, I wanted to fully explain this situation.

Any ideas or explanations? :)


PS. Also, to boot in Windows I have to go through BIOS. If I try to boot via GRUB it says "invalid EFI filepath." If I put the windows partition as first in boot order it skips GRUB and boots normally so this is not so crucial at this point.

---

### Post by xicosm on 2012-10-25
try running the 12.10 live cd with "try ubuntu without installing" without making any changes to parameters.

Let the boot run for a few seconds and when you think it has finished, like not having any activity on your usb or HD, try using Fn function for volume up/down to test if you can hear the sounds ... at that point ubuntu has booted.

Now, put the laptop to sleep, Fn + F1 (or closing the display lid).

Bring it back on (open the laptop or press power button).

You should be able to see the screen now and install ubuntu.

I have to do that (sleep/wake up) every time I reboot it =\.

I also have some problems with usb connections (external keyboard/mouse or even a usb drive) and are only solved with the slepp/wake up process.

---

### Post by kaefert66014235 on 2012-10-25
those problems sound really strange to me.. I am also running ubuntu 12.10 on the UX32VD and the only problem I have with montors is that I need to boot with no external monitor connected, otherwise the internal monitor is completly disabled and cannot be re-enabled by any configuration tool.

---

### Post by xicosm on 2012-10-25
> **kaefert66014235 said:**
> those problems sound really strange to me.. I am also running ubuntu 12.10 on the UX32VD and the only problem I have with montors is that I need to boot with no external monitor connected, otherwise the internal monitor is completly disabled and cannot be re-enabled by any configuration tool.

Did you update from 12.04 or did a fresh 12.10 install?

---

### Post by kaefert66014235 on 2012-10-25
> **xicosm said:**
> Did you update from 12.04 or did a fresh 12.10 install?

fresh install to 12.10 alpha2 and updated ever since

---

### Post by pasisti on 2012-10-25
> **xicosm said:**
> try running the 12.10 live cd with "try ubuntu without installing" without making any changes to parameters.

Let the boot run for a few seconds and when you think it has finished, like not having any activity on your usb or HD, try using Fn function for volume up/down to test if you can hear the sounds ... at that point ubuntu has booted.

Now, put the laptop to sleep, Fn + F1 (or closing the display lid).

Bring it back on (open the laptop or press power button).

You should be able to see the screen now and install ubuntu.

I have to do that (sleep/wake up) every time I reboot it =\.

I also have some problems with usb connections (external keyboard/mouse or even a usb drive) and are only solved with the slepp/wake up process.

Thank you very much! This worked and I'm typing this happily on my UX32VD using Ubuntu 12.10 :)

I don't know why but the ubuntu sound didn't come earlier. This time though when I booted up I heard it and after returning from sleep I saw the login screen. I had seen this advice before and I think I tried it but well, magic is magic!

Is this a known problem and is there a way to fix this? I mean it's great to have this working but still..

---

### Post by pasisti on 2012-10-25
> **pasisti said:**
> Thank you very much! This worked and I'm typing this happily on my UX32VD using Ubuntu 12.10 :)

I don't know why but the ubuntu sound didn't come earlier. This time though when I booted up I heard it and after returning from sleep I saw the login screen. I had seen this advice before and I think I tried it but well, magic is magic!

Is this a known problem and is there a way to fix this? I mean it's great to have this working but still..

It worked at first.. I used everything (video, music, wlan, java, flash, gwibber etc) perfectly, but then on the second boot; no sound, no display and the Fn+F1 (or closing lid) doesn't work. I didn't make any modifications to anything, just installed vlc player and dropbox and browsed the net.

---

### Post by xicosm on 2012-10-25
My laptop is actually the UX32A ... with the main difference being that my display is rubbish and no nvidia graphics card.

Maybe the nvidia driver could have something to do with it

---

### Post by Fallen Guru on 2012-10-25
An UEFI-install of 12.10 beta 2 worked like a charm on my UX32VD (BIOS 2.11), but there's still a number of annoying problems remaining:

1) The trackpad doesn't work at all well. It's much too sensitive for tap-to-click and when I try to use the hardware click I'm liable to jerk the pointer in a random direction in the process, missing my target entirely. How one is supposed to middle-click or click-and-drag with the right button, I've no idea.
Can this be fixed in software or is the trackpad just not for me?

2) The fans are too loud. They hardly ever turn off, if at all. On the flip side they don't seem to speed up much under load, either. Still, I wouldn't want to take it into a library or classroom as it is, and that's the intended primary use cases.
Maybe power management isn't working a hundred percent because I'm getting a lot of "package power limit" messages, even on idle load.
Does anyone know of a way to fix this or implement custom fan control? I'd happily sacrifice a ton of performance if the fans could stay off.

3) The power consumption is too high. I can't seem to push it below 8.5W (powertop), even with BT and Wifi off and display brightness at minimum. The nVidia CPU is diabled at boot via bbswitch, though it doesn't seem to make much of a difference either way. Allegedly Windows stays below 6W in a much less frugal configuration. When all's said and done I might get 5h out of it, given the specs I'd hoped for 7-8. What figures (watts and/or hours) are you all getting?

4) Brightness doesn't stay put. I don't mind the hotkeys not working for now, I can set brightness in a terminal just as well, but the fact that it resets to a (too bright) default every few minutes is quite irritating.

---

### Post by pasisti on 2012-10-25
I think I have this worked out!

When I put the ubuntu partition as the boot option #1 in BIOS, nothing works. But if I put the windows partition as the option #1, I can enter BIOS during boot and start ubuntu from there. This way I still have to use the Fn+F1 trick but beyond that everything works!

So, the question is, have I installed this properly? I selected the UEFI-mode in BIOS when I installed but was there something after that that needed special work?

---

### Post by screemo on 2012-10-25
> **Fallen Guru said:**
> An UEFI-install of 12.10 beta 2 worked like a charm on my UX32VD (BIOS 2.11), but there's still a number of annoying problems remaining:

1) The trackpad doesn't work at all well. It's much too sensitive for tap-to-click and when I try to use the hardware click I'm liable to jerk the pointer in a random direction in the process, missing my target entirely. How one is supposed to middle-click or click-and-drag with the right button, I've no idea.
Can this be fixed in software or is the trackpad just not for me?

2) The fans are too loud. They hardly ever turn off, if at all. On the flip side they don't seem to speed up much under load, either. Still, I wouldn't want to take it into a library or classroom as it is, and that's the intended primary use cases.
Maybe power management isn't working a hundred percent because I'm getting a lot of "package power limit" messages, even on idle load.
Does anyone know of a way to fix this or implement custom fan control? I'd happily sacrifice a ton of performance if the fans could stay off.

3) The power consumption is too high. I can't seem to push it below 8.5W (powertop), even with BT and Wifi off and display brightness at minimum. The nVidia CPU is diabled at boot via bbswitch, though it doesn't seem to make much of a difference either way. Allegedly Windows stays below 6W in a much less frugal configuration. When all's said and done I might get 5h out of it, given the specs I'd hoped for 7-8. What figures (watts and/or hours) are you all getting?

4) Brightness doesn't stay put. I don't mind the hotkeys not working for now, I can set brightness in a terminal just as well, but the fact that it resets to a (too bright) default every few minutes is quite irritating.

Could you try to add this to your boot parameters in /etc/default/grub, and update-grub afterwards ?

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4 pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1
```

Maybe it will help on the power management.

My touchpad is working rather well, dont know if I got accustomed to it - here's my settings: [http://i.imgur.com/xIzih.png](http://i.imgur.com/xIzih.png)

The fans is not running all the time in mine, I have upgraded to the latest 2.11 bios, and I know that there were some fan related fixes in 2.09.

---

### Post by kaefert66014235 on 2012-10-26
omg, you truly get down to 8,5 watts with Ubuntu 12.10? I found it incredible to get down to 12 watts, in the times of the alpha2 release when I bought my UX32VD the lowest I could get was 19 watts... I never looked at the windows power usage, I didn't even know that windows is capable of telling you the watts it takes out of the battery. Only thing I can tell about windows that it was horrible slow with all that bloatware.

To be honest, I also think that the battery time is quite horrible small with max 3 hours that I can currently get.

about the trackpad, I think its a fail on design and driver level, on windows it worked better. But I managed to get around with it by not removing the finger from the tochpad before clicking, just move to the button you wanna click on and directly press down when you reached it (hopefully you're over the area on the touchpad that can be pressed down ;))

I don't see a problem with the fans, the only time they are really loud when you turn the device on - during the bios tests.

the brightness thing resetting I have sometimes too, but mostly only when connecting or disconnecting the power, otherwise they stay mostly put. I think I disabled the brighness management in some gnome config utilty.

---

### Post by Linuxisfast on 2012-10-26
> **madmack said:**
> ux31a here. running arch linux (kernel v3.5.3) and can second the "easily get 4hr" with casual browsing and reading/typing.

My battery's power consumption sits at about 7-8 W which is better than my luck with any of my other recent laptops. I can push it to 6hr I believe although I haven't tried it.

good stuff in terms of battery consumption. :)

i also didn't need the second nvidia gpu. the integrated one is more than capable of playing 1080p content on my TV via HDMI using va-api. That's I'll need a GPU for.

I have similarly specced icore5 Intel HD3000 ASUS K53E which with Jupiter installed easily gives me 4.5 hours of surfing, typing and some conversion work.

---

### Post by TommyDelVed on 2012-10-26
Hallo!
I have a lot of problems with the install of Ubuntu (12.04 32 / 12.10 32 64) on ux32vd r3001v :(
I don't see anything during the installation, my screen is always black.
But, sometime I listen the tipical sound of ubuntu (drum), but I the screen..

Can someone help me?

Thank


p.s. sorry for my awful english.

---

### Post by danieleds on 2012-10-26
> **kaefert66014235 said:**
> To be honest, I also think that the battery time is quite horrible small with max 3 hours that I can currently get.
Max 3 hours?
I get 5 hours or more with full screen brightness and wireless enabled.
I keep bluetooth disabled when I'm not using it, and most importantly I configured bumblebee. This really makes the difference, because it turns off the nvidia card when not used.

---

### Post by kaefert66014235 on 2012-10-26
yes I configured bumblebee too, when I use optirun to start some application the power usage jumps up by 10 watts, but even without the nvidia card I am usally around 15 Watts. I also have bluetooth turned off, since I never use it.

---

### Post by Fallen Guru on 2012-10-26
Interesting that the power usage should be all over the board. What I did to get to 8,5W:
- kernel cmd line: pcie_aspm=force nmi_watchdog=0
- BT off in BIOS (I don't use it)
- nVidia card switched off via bbswitch
- card reader and asus_wmi module unloaded (both seem to be polling -> lots of wakeups)
- screen brightness at minimum
- all powertop recommendations implemented
- kb illumination off
- Wifi off
Obviously the machine is not very usable in this state but I wanted to know how far it could go, the answer being, not very far, really, for Ivy Bridge.
The 6W comparison figure was pulled out of a review, I've never booted Windows on this.

Say, does your fan control behave differently when on battery vs when plugged in?

---

### Post by kaefert66014235 on 2012-10-26
Fallen Guru:
Well, considering the hassle you have made yourself to get to 8,5 watts my 11 watts don't sound that bad.

I hardly ever notice the fans of my UX32VD. Only when booting, they shortly turn up to full speed, and if the device resides on a textile underground, like on the bed, then of course it gets warm after some time and the fans spin faster. But not on the table and also not when I'm sitting on a couch and the notebooks resides in my lap.

---

### Post by Fallen Guru on 2012-10-28
I've got the battery tamed now, it seems: nearly 8h in idle and it looks like I might actually get 5h under a medium workload. The funny thing is, it isn't consistent. Sometimes power drain pretty much stays under 7W, sometimes the exact same configuration will struggle to stay below double ...
It's pretty much the same for fan control and CPU frequency scaling. When it works it's great but sometimes things just refuse to settle down. No obvious causes like runaway processes (in top or powertop).

Next stop, Wifi. The syncs are in the 60-70 Mb/s range, I certainly haven't seeen more than 130 Mb/s, it's the same for the 2.4 and 5 GHz bands. The access point, an ahem Airport Express is supposed to be able to go up to 300 Mb/s sync speed. Real speed is ~15 Mb/s, and that's in a good mood ... Do I have a defective Wifi module, borked settings ...? How's your Wifi performance?

---

### Post by kaefert66014235 on 2012-10-29
could you share details about what you did to get that kind of battery performance? My usage is not going below 11 Watts, and when I'm doing some easy stuff like browsing and watching pdfs I only reach about 2,5 hours. Really bad for the battery seems to be the switching between workspaces (compiz takes 70% of one cpu core for the time of switching, which makes the battery usage go up from 12 to 22 watts).

About 802.11n performance - When I put both the laptop and my router in a very isolated place, only a few inches appart, with the right angle, I managed to reach about 120MBit/s = 15mbytes/s real performance (iperf), but even then with strange pauses of up to 2 seconds of no data.

But in a more realistic setup, the router on an exposed position (I have around 20 to 30 visible wifi networks in the vecinity) I only get 1/3rd of that and less, so 5mbytes per second maximum.

---

### Post by Mobidoy on 2012-10-29
I have noticed that while in grub (was trying to boot in command line) the f5 and f6 function keys are working, if it can help solving it !

---

### Post by mehl on 2012-10-31
So, I finally have a "stable" version working.

I've tried Ubuntu 3.2.0-17  (pointer issue), 3.5.0-30 (network issues) and am currently running on the latest test version (3.7.0-rc3) which seems fairly stable.  Network works as expected and the "reboot without screen" issue is kind of gone (I have not tested this very thorough though).

My only issue now is function keys (yup, all of them except the turn-of-screen button). Any idea of where to begin? :-P

---

### Post by niXel on 2012-11-02
Does anybody knows the corresponding bug tickets in launchpad for UX31A (or VD)?
I am unable to find the bug tickets for the keyboard- or display-brightness-bugs.

Sometimes I am able to switch the keyboard brightness, sometimes not. And does anybody here also have the problem that booting with connected monitor on hdmi or even some connected usb devices does not work?

---

### Post by xicosm on 2012-11-02
> **niXel said:**
> Does anybody knows the corresponding bug tickets in launchpad for UX31A (or VD)?
I am unable to find the bug tickets for the keyboard- or display-brightness-bugs.

Sometimes I am able to switch the keyboard brightness, sometimes not. And does anybody here also have the problem that booting with connected monitor on hdmi or even some connected usb devices does not work?

I have problems with connected usb devices ... what I have to do is put to sleep and wake up to get it working.

---

### Post by MirdautasVras on 2012-11-03
> **niXel said:**
> Does anybody knows the corresponding bug tickets in launchpad for UX31A (or VD)?
I am unable to find the bug tickets for the keyboard- or display-brightness-bugs.

Sometimes I am able to switch the keyboard brightness, sometimes not. And does anybody here also have the problem that booting with connected monitor on hdmi or even some connected usb devices does not work?

This is apparently a general bug in the linux kernel, which is caused by some code not being initialized/not being read. The bug has apparently been fixed in Linux Kernel 3.7rc1: [https://bugs.freedesktop.org/show_bug.cgi?id=45452]("https://bugs.freedesktop.org/show_bug.cgi?id=45452")

This means that it should work in 13.04 [http://www.phoronix.com/scan.php?page=news_item&px=MTIxODg]("http://www.phoronix.com/scan.php?page=news_item&px=MTIxODg")

---

### Post by screemo on 2012-11-05
> **mehl said:**
> So, I finally have a "stable" version working.

I've tried Ubuntu 3.2.0-17  (pointer issue), 3.5.0-30 (network issues) and am currently running on the latest test version (3.7.0-rc3) which seems fairly stable.  Network works as expected and the "reboot without screen" issue is kind of gone (I have not tested this very thorough though).

My only issue now is function keys (yup, all of them except the turn-of-screen button). Any idea of where to begin? :-P

I use 3.6.5-030605 and it works great so far (albeit without brightness keys). I tried 3.7.0-rc4, but it introduces other problems like flickering screen, not always wanting to boot etc.

UPDATE: today it appears that the 3.7.0-030700rc4-generic works really well - including all keys (except for brightness).

---

### Post by niXel on 2012-11-05
> **MirdautasVras said:**
> [&#8230;] The bug has apparently been fixed in Linux Kernel 3.7rc1: [https://bugs.freedesktop.org/show_bug.cgi?id=45452]("https://bugs.freedesktop.org/show_bug.cgi?id=45452")

Thank you very much for that info. Are there any bug reports for the issues concerning the sometimes not changeable keyboard backlight brightness?

---

### Post by mehl on 2012-11-06
> **screemo said:**
> I use 3.6.5-030605 and it works great so far (albeit without brightness keys). I tried 3.7.0-rc4, but it introduces other problems like flickering screen, not always wanting to boot etc.

UPDATE: today it appears that the 3.7.0-030700rc4-generic works really well - including all keys (except for brightness).

Ah, nice. I will try that one out as soon as I get home. :-)

---

### Post by Fallen Guru on 2012-11-06
> **kaefert66014235 said:**
> could you share details about what you did to get that kind of battery performance?

Only two things that aren't in the Wiki:
1. bbswitch doesn't work 100%
Manually turning off the nVidia card (echo OFF | sudo tee /proc/acpi/bbswitch) works but loading the module with Load_state=0 via /etc/modules does not. The card will read as off but in fact be still on. That's why my numbers were so erratic. My guess is that something later in the boot process turns it back on again, but, whatever, echo OFF >/proc/acpi/bbswitch in /etc/rc.local fixes that.

2. The card reader driver is broken (in that it uses a lot of power) - I've blacklisted it.

Battery runtime is comparable with Windows now.

Wifi still sucks, though, I can't seem to get more than 2 MB/s, regardless of sync speed. It's the same under Windows, though ...

---

### Post by screemo on 2012-11-07
> **Fallen Guru said:**
> Only two things that aren't in the Wiki:
1. bbswitch doesn't work 100%
Manually turning off the nVidia card (echo OFF | sudo tee /proc/acpi/bbswitch) works but loading the module with Load_state=0 via /etc/modules does not. The card will read as off but in fact be still on. That's why my numbers were so erratic. My guess is that something later in the boot process turns it back on again, but, whatever, echo OFF >/proc/acpi/bbswitch in /etc/rc.local fixes that.

2. The card reader driver is broken (in that it uses a lot of power) - I've blacklisted it.

Battery runtime is comparable with Windows now.

Wifi still sucks, though, I can't seem to get more than 2 MB/s, regardless of sync speed. It's the same under Windows, though ...

Do you mind sharing that blacklist for the cardreader?

btw, I did a speedtest, and think the wifi has definitely improved. Any chance you're just running on G, because those 2mb matches the max speed of that pretty much..

[http://www.speedtest.net/result/2292931726.png](http://www.speedtest.net/result/2292931726.png)

I've tried from my nas using ftp over wireless, and get a constant 5-6mb/s on an iso file.

EDIT: I'm on N using an Asus N66U router set to defaults.

---

### Post by Fallen Guru on 2012-11-08
> **screemo said:**
> Do you mind sharing that blacklist for the cardreader?
Just put the line "blacklist rts5139" somewhere in /etc/modprobe.d/, it doesn't really matter which file as long as the name ends in .conf. I created a new "blacklist-cardreader.conf" for the purpose. You can still modprobe the module manually when you need the card reader.

> **screemo said:**
> I did a speedtest, and think the wifi has definitely improved. Any chance you're just running on G,
Good idea, but that isn't it. I'm getting sync speeds in the 100-140 Mb/s range on 2.4 GHz N (5 GHz is actually a little worse), but only 2 MB/s net bandwidth. There's maybe two or three other APs visible, their bands don't even overlap.

---

### Post by victorbrca on 2012-11-22
Anyone here upgraded the Ux32vd to a full SSD? I can't get grub to come up on boot.

Where would you put the bootloader, in the new ssd (sda) or the ssdi (sdb)? How about the uefi partition? 

Here's how I had it laid out:

SSD (sda) 
1- 300mb - Windows (I'm guessing uefi) 
2- 60gb - windows 8
3- 60gb - ntfs
4- 20gb - /
5- +/-100gb - /home

SSDi (sdb) 
1- 6gb - swap
2- 18gb - ntfs

---

### Post by screemo on 2012-11-23
> **victorbrca said:**
> Anyone here upgraded the Ux32vd to a full SSD? I can't get grub to come up on boot.

Where would you put the bootloader, in the new ssd (sda) or the ssdi (sdb)? How about the uefi partition? 

Here's how I had it laid out:

SSD (sda) 
1- 300mb - Windows (I'm guessing uefi) 
2- 60gb - windows 8
3- 60gb - ntfs
4- 20gb - /
5- +/-100gb - /home

SSDi (sdb) 
1- 6gb - swap
2- 18gb - ntfs

I only put in a SSD, and installed everything on that (never touched the internal one), and it worked.

ssd:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   996302797   498151367+  83  Linux
/dev/sda2       996303105  1000215215     1956055+  82  Linux swap / Solaris

ssdi:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


I think your layout should be possible, although you seem to complicate it with alot of partitions (I would have one per OS).

---

### Post by wonghang on 2012-11-23
Hi all,

Previously, I got the problem that my screen will become blank after the boot and I figured it out that if I use "fbdev" instead of "intel", I can see the screen.

I upgraded the kernel to 3.2.0-33-generic-pae recently and hope to see if I could use "intel" driver again.

I removed my xorg.conf and hope that it will use intel driver.
However, I found that my computer is now always using "fbdev".
If I specify "intel" in /etc/X11/xorg.conf, I will get a failsafe screen:

```

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
EndSection

```

Any idea to resolve this problem? I am quite suffered by the brightness problem. I know that I can only do this by using intel driver.

For nvidia (bumblebee) things, I can get it work:

```

$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xfc
Context is Direct
OpenGL Renderer: Gallium 0.4 on llvmpipe (LLVM 0x301)
7.731623 frames/sec - 7.483778 Mpixels/sec

$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 620M/PCIe/SSE2
107.486518 frames/sec - 104.040930 Mpixels/sec

```

Thank in advance. 

P.S. I have tried to use those kernel argument, but the xserver seems to be fail to detect the intel chip.
P.S.2 I also tried to "apt-get purge xserver-xorg-video-intel" and install it again.

---

### Post by Fallen Guru on 2012-11-23
> **victorbrca said:**
> Anyone here upgraded the Ux32vd to a full SSD? I can't get grub to come up on boot.

You need an UEFI partition. That's a small (couple hundred MB) FAT32 partition at the start of a GPT-partitioned disk with the "boot" flag set. It's shared between all OS' on the system. ASUS' default install has that on the HDD, so if you swap that out, you'll need a new one. You can create it either manually or in the the Quantal installer ("Use as ..."). I put mine on the iSDD but either will work.

Oh, and forget the swap. Just upgrade it to 10GB of RAM while you're at it.

---

### Post by victorbrca on 2012-11-23
> **screemo said:**
> I only put in a SSD, and installed everything on that (never touched the internal one), and it worked.

ssd:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   996302797   498151367+  83  Linux
/dev/sda2       996303105  1000215215     1956055+  82  Linux swap / Solaris

ssdi:
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT


I think your layout should be possible, although you seem to complicate it with alot of partitions (I would have one per OS).

> **Fallen Guru said:**
> You need an UEFI partition. That's a small (couple hundred MB) FAT32 partition at the start of a GPT-partitioned disk with the "boot" flag set. It's shared between all OS' on the system. ASUS' default install has that on the HDD, so if you swap that out, you'll need a new one. You can create it either manually or in the the Quantal installer ("Use as ..."). I put mine on the iSDD but either will work.

Oh, and forget the swap. Just upgrade it to 10GB of RAM while you're at it.


Thanks for the reply guys... I was going to create a new UEFI partition, but I decided to give boot-fix a shot. This is what worked for me...

Booted into the USB (both Windows and Ubuntu were already installed), added boot-fix repo then installed it. Ran boot-fix with the "Recommended Repair" option. The GUI was showing messages that it was trying to fix boot in sda3 (that's where I had my "/" partition), however when it prompted me where to install GRUB I selected "sda". 


Vic.

---

### Post by victorbrca on 2012-11-23
Another question... did anyone with 12.10 on UX32VD follow the instructions in "[https://help.ubuntu.com/community/AsusZenbookPrime]("https://help.ubuntu.com/community/AsusZenbookPrime")"? I did the power, SSD options and brightness option, but I was not sure if others are really needed with 12.10. 

Thanks.

---

### Post by virx on 2012-11-25
I am trying to make my zenbook to dualboot win7+ubuntu 12.10. Win7 is installed but ubuntu installer cannot detect it. Also looks like installer DVD does not boot in UEFI mode (message: Secure boot not enabled...). I have tryed UEFI boot device (portable DVD device). Am I doing something wrong?

---

### Post by ohyran on 2012-11-25
Ok I've tried to search through this thread as best Ive could to find an answer to my perhaps rather specific problem. 
The laptop monitor is black. It works but the second I login and pass from the Grub menu it just goes first black-on (kinda shiny but nothing appears) and then black-completely-off. By hooking up an external monitor I can use it but I can not for the life of me figure out why it refuses to accept the laptop monitor.

I checked Xrandr and from what this is what I got

> Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
VGA1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 250mm
   1600x900       60.0*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.0     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


Now this is of course with the external monitor plugged in. I've tried toggling the FN+f8 button (does noting), Ive tried removing "quiet splash", changing it for "nomodeset" and adding "nomodeset" in grub. Nothing works.

So I'm stumped :)

This is an ux32vd and I should mention that I have xubuntu 12.10 64-bit on it. 

Anyone have any good ideas what to try next?

---

### Post by screemo on 2012-11-26
> **wonghang said:**
> Hi all,

Previously, I got the problem that my screen will become blank after the boot and I figured it out that if I use "fbdev" instead of "intel", I can see the screen.

I upgraded the kernel to 3.2.0-33-generic-pae recently and hope to see if I could use "intel" driver again.

I removed my xorg.conf and hope that it will use intel driver.
However, I found that my computer is now always using "fbdev".
If I specify "intel" in /etc/X11/xorg.conf, I will get a failsafe screen:

```

Section "Device"
	Identifier  "Card0"
	Driver      "intel"
EndSection

```

Any idea to resolve this problem? I am quite suffered by the brightness problem. I know that I can only do this by using intel driver.

For nvidia (bumblebee) things, I can get it work:

```

$ glxspheres 
Polygons in scene: 62464
Visual ID of window: 0xfc
Context is Direct
OpenGL Renderer: Gallium 0.4 on llvmpipe (LLVM 0x301)
7.731623 frames/sec - 7.483778 Mpixels/sec

$ optirun glxspheres
Polygons in scene: 62464
Visual ID of window: 0x21
Context is Direct
OpenGL Renderer: GeForce GT 620M/PCIe/SSE2
107.486518 frames/sec - 104.040930 Mpixels/sec

```

Thank in advance. 

P.S. I have tried to use those kernel argument, but the xserver seems to be fail to detect the intel chip.
P.S.2 I also tried to "apt-get purge xserver-xorg-video-intel" and install it again.

You should upgrade your kernel to 3.5 series (and to ubuntu 12.10)-
Also here's how to set up bumblebee: [http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/](http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/)

---

### Post by ohyran on 2012-11-26
Ok so I found some more weird stuff out. If I connect the external monitor during the grub-screen I get the option to switch between screens after it boots into the OS. The laptop screen is still dead/black but there at least exists an option that, when you press it creates an overlayed duplicate on the external monitor. 

Xrandr then gives the following 

> Screen 0: minimum 320 x 200, current 1600 x 900, maximum 8192 x 8192
eDP1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1600x900+0+0 (normal left inverted right x axis y axis) 443mm x 250mm
   1600x900       60.0*+
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.0     70.1     60.0  
   1024x576       60.0  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)

And using one of the dual-screen managers (dont remember which, I can happily switch between screens... only not IRL, still the same monitor. :/ )

I think I'm going a little bit unhinged here mentally so if anyone has any little hint what it can be, dont be shy.

**EDIT**: I managed to get the screen going by adding "i915.modeset=0" last in the Linux-line in Grub. But then the boot just froze halfway through... one step forward, two steps back

**EDIT 2**: By adding both "i915.modeset=0" and exchanging "quiet" in the "quiet splash" part with "verbose text" I could log in to the OS but only in text... and text based OS cannot see my frustrated tears

So the problem remains that I can only boot into the system with an external monitor - where I can force the boot screen to show me some graphicson the laptops monitor with the i915.modeset=0 command for some reason it freezes completely UNLESS I force it to give me a textprompt with "verbose text"... what the hell is going on? Is there anything I can do? At this point I'm contemplating hiring an exorcist or something...

---

### Post by virx on 2012-11-27
Now I have read all 26 pages of this topic and people seemed to be able to dual-boot windows and ubuntu with UEFI on 12.04 or 12.10 beta.

If I install windows first then ubuntu 12.10 installer cannot detect windows. If I install ubuntu first, then windows installer does not allow to install to the same disk. I have installed new SSD instead of HDD and would like to use it for dual-boot.

If I create partition table with GParted first (like shown in many tutorials), still windows does not want to use this disk.

When booting from DVD or USB in UEFI mode at first I can see "Secure boot not enabled" message. I am using latest BIOS. 

Does anybody have any ideas what to do next?

---

### Post by ohyran on 2012-11-27
Virx: first of, Welcome to Hell ;)

I really am not sure about this but a large chunk of my problems started when I updated to the latest Bios too (212). I have had Ubuntu installed before, screen working and all (you can see my insane rantings above on my current situation) but after various mishaps, all my fault btw, I had to reinstall. At the same time a friend of min suggested upgrading Bios too.

Now I am in no way sure - but it may be the common culprit here, or it may be that I am trying to find a good culprit. But I get the same "Secure boot not enabled" message just before Grub.

Like I said, not much help - but perhaps something?

Also I found this it may not do you any real good but I thought I should try it out later and it might help with your problems
[http://webent.altervista.org/2012/09/16/how-to-install-ubuntu-linux-12-04-or-newer-on-the-zenbook-ux32vd/](http://webent.altervista.org/2012/09/16/how-to-install-ubuntu-linux-12-04-or-newer-on-the-zenbook-ux32vd/)

---

### Post by virx on 2012-11-28
thx ohyran,
My BIOS is also
Version 212
VBIOS Version 2137.I14UX3.006
EC Version 204U140001

I am going to let the notebook be used for few days, then try instructions from that article.

---

### Post by oogabubchub on 2012-11-28
What battery life are you guys getting running Ubuntu on the UX32VD?

Looking at this page ([http://www.linlap.com/asus_ux32vd](http://www.linlap.com/asus_ux32vd)) it's saying to expect 4-4.5 hours, but I'm only getting around 2-2.5 hours. Something is definitely wrong here.

---

### Post by ohyran on 2012-11-29
After some random fumbling I've managed to get it going. The Xubuntu installation sticks, it has yet not totally crashed and the boot doesn't freeze up completely. 

I can't swear what I did is what is required, whether its a combination or if its just black magic or something - but from what I can remember I lacked a xorg.conf file. At first I thought it had something to do with it being a intel graphics thing and that Nvidia kept the drivers hidden for when bumblebee started but that was just me.

So I used "sudo Xorg -configure" which told me that the server was already active for display 0 so I had to run "sudo stop lightdm" which soundly kicked me into some text-thing and from there copy the newly created file xorg.conf.new into /etc/X11/xorg.conf. This left me with a new but kinda empty xorg.conf file (since my screen still isn't recognized and runs on some weird resolution 1028x700-something).

I also disabled a power saving option in the Bios. I have no idea if this helped in any way - when I get the nerves for it I'll enable it again and see what happens.

I probably did allot of other things. But anyway now I can get it to start by adding nomodeset in grub (something that didn't work before). Not a blessed clue why that is though.

But that leaves me with the basicly empty xorg.conf file. Can someone please post a copy of theirs (if they have a Asus UX32VD without the Full HD screen) so I can see what differs and if I can change it. For the moment all attempts to change anything resolution-wise just ends with it telling me it doesn't now the gamma or something...

_**The final Edit:**_
Screw this. Every other computer in the house runs Linux. For those of you who found this thread by googling the subject. Please please please remember to **never mess with the factory partition**. Have a back up so that if it fails (chances are good it will) you can restore windows at least.
And listen carefully to what some people claim in the forums: many seem to think that if they got the computer running in Vesa thats the same as "it working". Its not. That's like claiming a Lamborghini is running without gas when youre pushing it down the road.

---

### Post by crypto178 on 2012-12-04
After my previous laptop died after almost 5 years of loyal (ubuntu powered) service, I recently acquired an UX32VD and installed ubuntu 12.10 on it. Information from the wiki and these forums was invaluable, so thank you all who contributed.

Typing this post on Chromium, WiFi on, Bluetooth off, usb mouse plugged in and minimum screen brightness, battery reports around 4 hours of remaining power. Oscillating between 8 and 12W in powertop. This changes to about 3h20 of remaining battery life from a near full charge while watching video. 

Current unresolved issues : 
- Touchpad multi-touch gestures don't work : no two-finger scroll.
- Even when relatively idle, the laptop heats up to about 50°C, then the fan kicks in for a short while (not very loudly), brings back the temperature to about 46°C, after which it heats up again, etc. 
- In Gnome Shell and Cinnamon, I'm getting very noticeable screen tearing when playing videos. This problem is completely absent with Unity. Funnily, I had the exact opposite problem with my previous laptop, where Unity had video tearing but not Shell/Cinnamon.

I wiped windows clean very shortly after booting up for the first time, so I'm not sure if some of these behaviors are flaws of the machine or ubuntu-specific.

If it might help anybody, and for my own future reference, I'll post a recap of everything I did (might be out of order) :

- Booted the installation from an USB key with Ubuntu 12.10 amd64 (F2 key for boot menu if I recall correctly)
- Deleted all partitions but the EFI one (as I'm unsure of what exactly is its purpose, I preferred to leave it alone).
- Chose a custom partition set up with / on the SSD (sdb), and /home (as well as /var, /tmp, /opt and swap) on the HDD (sda).
- Ran all the updates after installation.
- Followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=12359126&postcount=21") to install a new kernel that solved the nonfunctional brightness keys. There are other workarounds listed on the wiki, but they didn't work for me and/or didn't seem to have the proper max brightness.
- Followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=12210923&postcount=231") to solve the hard drive clicking sound problem.
- Followed the wiki recommendations on optimizing the SSD (adding discard,noatime,nodiratime to the /etc/fstab options)
- As recommended on the wiki, followed instructions from [this article]("http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/") to install Bumblebee.
- Followed the instructions from [this post]("http://ubuntuforums.org/showpost.php?p=12340897&postcount=248") to turn off the Nvidia card at boot. 
- Followed the instructions from [this post]("http://ubuntuforums.org/showpost.php?p=12343324&postcount=250") to blacklist the card reader driver, in order to save battery power (I'm not using it).
- Added xorg-edgers PPA in the hope of fixing the touchpad multi-touch, which it didn't, but it seemed to solve the occasional black screen or kernel panic at boot I previously encountered (completely unsure about this).

---

### Post by SveinT on 2012-12-05
Nice that you got everything setup nicely.

As for the harddrive clicking sound (I was the one who wrote that post), the set options on resume-from-suspend doesn't seem to work properly here. I have to re-set it in terminal. Does it work on yours?

Another suggestion is to move the home folder to the SSD, and either create some folders (like Music, Downloads, Files etc) on another partition, then symlink these from your home folder. Or mount the old home as a subfolder of the new home dir. The advantage of doing this is that frequently accessed files like settings etc will be on the SSD, while larger files can be kept on the HD. This allows the hard drive to be able to spin down more frequently, and should save some power (and it makes the computer completely silent :-) ). Seems to work well on my setup, and the setup isn't that hard (but it may screw up your system if you don't know what you are doing) Just create a home/username folder on the root partition, log out and login to terminal as root, copy the important files from your current home folder there (make sure permissions remain to your user), then edit fstab accordingly.

-EDIT- A wise thing to do is take a backup of the fstab, and copy, not move, the home folder. Then you can delete the files when everything is working, or revert back if not.

---

### Post by screemo on 2012-12-09
> **crypto178 said:**
> After my previous laptop died after almost 5 years of loyal (ubuntu powered) service, I recently acquired an UX32VD and installed ubuntu 12.10 on it. Information from the wiki and these forums was invaluable, so thank you all who contributed.

Typing this post on Chromium, WiFi on, Bluetooth off, usb mouse plugged in and minimum screen brightness, battery reports around 4 hours of remaining power. Oscillating between 8 and 12W in powertop. This changes to about 3h20 of remaining battery life from a near full charge while watching video. 

Current unresolved issues : 
- Touchpad multi-touch gestures don't work : no two-finger scroll.
- Even when relatively idle, the laptop heats up to about 50°C, then the fan kicks in for a short while (not very loudly), brings back the temperature to about 46°C, after which it heats up again, etc. 
- In Gnome Shell and Cinnamon, I'm getting very noticeable screen tearing when playing videos. This problem is completely absent with Unity. Funnily, I had the exact opposite problem with my previous laptop, where Unity had video tearing but not Shell/Cinnamon.

I wiped windows clean very shortly after booting up for the first time, so I'm not sure if some of these behaviors are flaws of the machine or ubuntu-specific.

If it might help anybody, and for my own future reference, I'll post a recap of everything I did (might be out of order) :

- Booted the installation from an USB key with Ubuntu 12.10 amd64 (F2 key for boot menu if I recall correctly)
- Deleted all partitions but the EFI one (as I'm unsure of what exactly is its purpose, I preferred to leave it alone).
- Chose a custom partition set up with / on the SSD (sdb), and /home (as well as /var, /tmp, /opt and swap) on the HDD (sda).
- Ran all the updates after installation.
- Followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=12359126&postcount=21") to install a new kernel that solved the nonfunctional brightness keys. There are other workarounds listed on the wiki, but they didn't work for me and/or didn't seem to have the proper max brightness.
- Followed the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=12210923&postcount=231") to solve the hard drive clicking sound problem.
- Followed the wiki recommendations on optimizing the SSD (adding discard,noatime,nodiratime to the /etc/fstab options)
- As recommended on the wiki, followed instructions from [this article]("http://webent.altervista.org/2012/08/30/how-to-get-the-nvidia-optimus-working-on-zenbook-ux32vd-ubuntu-12-04/") to install Bumblebee.
- Followed the instructions from [this post]("http://ubuntuforums.org/showpost.php?p=12340897&postcount=248") to turn off the Nvidia card at boot. 
- Followed the instructions from [this post]("http://ubuntuforums.org/showpost.php?p=12343324&postcount=250") to blacklist the card reader driver, in order to save battery power (I'm not using it).
- Added xorg-edgers PPA in the hope of fixing the touchpad multi-touch, which it didn't, but it seemed to solve the occasional black screen or kernel panic at boot I previously encountered (completely unsure about this).

I'm on 212, and have multitouch (2 finger scroll, 3 finger move windows, 2 finger tap to rightclick etc.).

My temperature is around 46 degrees also, but doesn't heat up - my thought is that it might be the internal harddrive adding that extra heat ? (im using a SSD). 

Powertop reports 10.5 - 12.5 watts (I havent disabled the nvidia card).

I'm on kernel 3.6.9-030609-generic now, and its quite stable.

```
kernel cmdline: pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0
```

Only thing left is X not always starting up correctly - sometimes takes a few reboots / kill X, restart lightdm to bring it up. Looks like some race condition to me.

---

### Post by crypto178 on 2012-12-11
> **SveinT said:**
> Nice that you got everything setup nicely.

As for the harddrive clicking sound (I was the one who wrote that post), the set options on resume-from-suspend doesn't seem to work properly here. I have to re-set it in terminal. Does it work on yours?


I haven't had this issue, it seems to be working for me.

Actually I was typing this response after resuming from suspend when the laptop abruptly shut down. Oops. Seems like there is an issue there. In any case, I don't use suspend very often but I'll do more testing.

> **screemo said:**
> I'm on 212, and have multitouch (2 finger scroll, 3 finger move windows, 2 finger tap to rightclick etc.).

My temperature is around 46 degrees also, but doesn't heat up - my thought is that it might be the internal harddrive adding that extra heat ? (im using a SSD). 

Powertop reports 10.5 - 12.5 watts (I havent disabled the nvidia card).

I'm on kernel 3.6.9-030609-generic now, and its quite stable.

```
kernel cmdline: pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0
```

Only thing left is X not always starting up correctly - sometimes takes a few reboots / kill X, restart lightdm to bring it up. Looks like some race condition to me.

Thanks for the information, I'll try some tweaking to get the touchpad working right.

And yes, I do also encounter the problem of X not starting up correctly from time to time, I'm hoping/assuming it'll get sorted out in future updates :)

---

### Post by chnry on 2012-12-12
> **xicosm said:**
> I have problems with connected usb devices ... what I have to do is put to sleep and wake up to get it working.

I do also had this kind of problem.
i solved it changing bios option.
i don't remember the option, but only 2 are refering to usb, so it should be easy to try.

---

### Post by crypto178 on 2012-12-13
Sorted out the touchpad problem, turned out to be a really simple matter of tweaking the settings a little bit.
Adding xorg-edgers to software sources as suggested on the wiki enabled four-finger gestures. To enable two-finger scrolling and three-finger gestures :
I went to system settings > mouse/touchpad settings, and enabled two finger scrolling in the options.
Then, I ran
synclient ClickFinger3=0
synclient TapButton3=0  
to enable three-finger gestures.
(and set these to run at session startup)
I think this might only be relevant to Unity users.

---

### Post by instant on 2012-12-15
Hi guys!

I recently installed Kubuntu, just for the hell of it and I feel as if nothing really works as it should on my UX32VD.

Had Ubuntu installed earlier and installed the 3.7.0.4-generic kernel, after that, all hell broke loose which is why I installed Kubuntu.

Well, on to my real problem. I feel as if my computer gets A LOT hotter now than earlier, the fans run at full speed and the sensors-command show 59C. On top of that the graphics are really large, all the text, everything from the login prompt to the text in the title-bars is very large, something like 24pt.

I have tried the 3.7.0.999-generic kernel and the 3.6.9-030609 kernel, both with the same heating and graphics issues.

Added the xorg-edgers ppa to try update graphics drivers but to no avail.

When checking the dmesg I see a line stating:
```
init: udev-fallback-graphics main process (373) terminated with status 1
```

which, well, doesn't feel right.

So does anyone else have any experience dealing with these kinds of issues? And does anyone know what the most reliable way is to check the temperature?

---

### Post by xicosm on 2012-12-27
I don't know if I installed an update that caused this but I cannot get my laptop to sleep anymore, consequently not able to access anything.

Anyone had this problem that could suggest anything?

---

### Post by screemo on 2012-12-27
> **instant said:**
> Hi guys!

I recently installed Kubuntu, just for the hell of it and I feel as if nothing really works as it should on my UX32VD.

Had Ubuntu installed earlier and installed the 3.7.0.4-generic kernel, after that, all hell broke loose which is why I installed Kubuntu.

Well, on to my real problem. I feel as if my computer gets A LOT hotter now than earlier, the fans run at full speed and the sensors-command show 59C. On top of that the graphics are really large, all the text, everything from the login prompt to the text in the title-bars is very large, something like 24pt.

I have tried the 3.7.0.999-generic kernel and the 3.6.9-030609 kernel, both with the same heating and graphics issues.

Added the xorg-edgers ppa to try update graphics drivers but to no avail.

When checking the dmesg I see a line stating:
```
init: udev-fallback-graphics main process (373) terminated with status 1
```

which, well, doesn't feel right.

So does anyone else have any experience dealing with these kinds of issues? And does anyone know what the most reliable way is to check the temperature?

I've had a similar problem - for me it was related to nouveau vs bbswitch/bumblebeed/nvidia-current(from xorg-edgers).

Solution was to get rid of it all, and install these versions:

```

ii  bbswitch-dkms                             0.4.2-2~quantalppa1                        all          Interface for toggling the power on nVidia Optimus video cards
ii  bumblebee                                 3.0.1-3~quantalppa2                        amd64        nVidia Optimus support
ii  bumblebee-nvidia                          3.0.1-3~quantalppa2                        amd64        nVidia Optimus support using the proprietary NVIDIA driver
ii  nvidia-current                            304.51.really.304.43-0ubuntu2              amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library

```

Kernel 3.7.0-7-generic, on raring.

---

### Post by Rubadubdub on 2012-12-28
Hi everybody,

I just finished my migration from my old Lenovo T61 (graphics-card died) to my new UX32VD. And thanks to this tread I managed to install it to my liking.

The only thing really bothering me was the banding, but I managed to fix that as well.

For those looking to fix the banding, adding the following ppa and upgrade to the new packages is what fix everything for me:
```
ppa:xorg-edgers/ppa

```
so from a terminal:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

:D

---

### Post by Rubadubdub on 2012-12-29
Update to my last message:
Everything seems to work like it should, no (24 bit colour) banding to be seen, all fn brightness keys are working including on screen notifications, no black screen on start, ... -> except (always an exception :() when I disconnect the power en reconnect it I get an kernel panic and the asus freezes.

Any suggestions what I can do to fix this?
(Kernel 3.7.0-7-generic)

---

### Post by screemo on 2012-12-31
> **Rubadubdub said:**
> Update to my last message:
Everything seems to work like it should, no (24 bit colour) banding to be seen, all fn brightness keys are working including on screen notifications, no black screen on start, ... -> except (always an exception :() when I disconnect the power en reconnect it I get an kernel panic and the asus freezes.

Any suggestions what I can do to fix this?
(Kernel 3.7.0-7-generic)

So brightness up/down is working for real now? 

Regarding the freeze, do you get any useful information from dmesg?
(I'm running the same kernel on raring and don't see this issue)

Btw, do you have any issues with usb devices on your system? Mine are rarely recognised (almost never) and dmesg shows nothing about the usb device has been inserted..


EDIT: I can confirm that Fn+brightness up/down works now !

EDIT2: USB devices are working again after I set USB XHCI to DISABLED in the bios. Previously the would only work if they were inserted prior to boot.

---

### Post by Rubadubdub on 2013-01-15
sorry for the late reply/update.

Well the problem with my laptop freezing when re-plugging the power left me no choice. I ditched the xorg-edgers ppa. 

I went back to kernel 3.5.0-22 and I must say that I am glad because now the only thing not working are the brightness keys.

What is working is:
[LIST]
[*]No more banding
[*]primusrun & optirun running like a charm
[*]usb devices working with power plugged in and on battery
[*]connecting detaching external monitor via mini vga with no problems
[*]longer battery life 5-6 hours
[*] no problem connecting power when computer is running (with kernel 3.7 everytime a kernel panic)
[/LIST]

And for what's not working (the brightness keys) a workable sollution. I am running Gnome Shell and I added the following extension:
[https://extensions.gnome.org/extension/231/brightness-control/]("https://extensions.gnome.org/extension/231/brightness-control/")

I enabled Intel SNA acceleration:
[http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html]("http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html")

I also installed Bumblebee and Primus and the Nvidia Experimental drivers 310: 
[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")
[http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results]("http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results")
[http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html]("http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html")

So for now I am a happy camper.

---

### Post by screemo on 2013-01-15
> **Rubadubdub said:**
> sorry for the late reply/update.

Well the problem with my laptop freezing when re-plugging the power left me no choice. I ditched the xorg-edgers ppa. 

I went back to kernel 3.5.0-22 and I must say that I am glad because now the only thing not working are the brightness keys.

What is working is:
[LIST]
[*]No more banding
[*]primusrun & optirun running like a charm
[*]usb devices working with power plugged in and on battery
[*]connecting detaching external monitor via mini vga with no problems
[*]longer battery life 5-6 hours
[*] no problem connecting power when computer is running (with kernel 3.7 everytime a kernel panic)
[/LIST]

And for what's not working (the brightness keys) a workable sollution. I am running Gnome Shell and I added the following extension:
[https://extensions.gnome.org/extension/231/brightness-control/]("https://extensions.gnome.org/extension/231/brightness-control/")

I enabled Intel SNA acceleration:
[http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html]("http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html")

I also installed Bumblebee and Primus and the Nvidia Experimental drivers 310: 
[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")
[http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results]("http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results")
[http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html]("http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html")

So for now I am a happy camper.

Thanks for the reply - I have since upgraded to 13.04 where all the xorg edgers stuff + kernel 3.8 w/brightness support is default.

I dont use the nvidia gpu because its not really that fast, and games are not my thing - I had to try though, but bumblebee and friends didn't really play well on 13.04 (yet) :p

I got around 4 hours on battery which is something that could be improved though - do you know if actively disabling the gpu makes a difference?

EDIT: forgot I had disabled pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0 in /etc/default/grub - that should make battery life better I think.

---

### Post by instant on 2013-01-16
> **screemo said:**
> Thanks for the reply - I have since upgraded to 13.04 where all the xorg edgers stuff + kernel 3.8 w/brightness support is default.

I dont use the nvidia gpu because its not really that fast, and games are not my thing - I had to try though, but bumblebee and friends didn't really play well on 13.04 (yet) :p

I got around 4 hours on battery which is something that could be improved though - do you know if actively disabling the gpu makes a difference?

EDIT: forgot I had disabled pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0 in /etc/default/grub - that should make battery life better I think.

Hi! 

Don't believe that you would get ~4 hours of battery time if the discrete graphics card wasn't already disabled, that being said I get about the same battery time running 3.7.0.7-generic with the Nvidia switched of through bbswitch. 

I also believe the grub-parameters do add some battery-time, no huge amounts but still. I use the same parameters. 

How is the temperature on your laptop? Mine is idling at around 60-65C with AC and I think it is a bit lower running on battery. I usually check the sensors command a couple of times per day.

I'm not really sure whether or not that is normal, I'd really like it to be lower so that the fans could shutdown now and then.

I have read a couple of forum posts both regarding Ubuntu and Arch and it seems that in some cases the UX32VD can go as low as 7-8W in consumption and thus also lowering the temperature to somewhere around 50C.

Any ideas?:p

---

### Post by Rubadubdub on 2013-01-17
Right now my laptop is running on battery and temp is 40° celsius.

Fyi, my grub line is:
quiet splash pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1

---

### Post by screemo on 2013-01-17
> **instant said:**
> Hi! 

Don't believe that you would get ~4 hours of battery time if the discrete graphics card wasn't already disabled, that being said I get about the same battery time running 3.7.0.7-generic with the Nvidia switched of through bbswitch. 

I also believe the grub-parameters do add some battery-time, no huge amounts but still. I use the same parameters. 

How is the temperature on your laptop? Mine is idling at around 60-65C with AC and I think it is a bit lower running on battery. I usually check the sensors command a couple of times per day.

I'm not really sure whether or not that is normal, I'd really like it to be lower so that the fans could shutdown now and then.

I have read a couple of forum posts both regarding Ubuntu and Arch and it seems that in some cases the UX32VD can go as low as 7-8W in consumption and thus also lowering the temperature to somewhere around 50C.

Any ideas?:p

I just did a sensors test here, and on AC its the following:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +108.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +53.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +56.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +54.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +55.0°C  (high = +87.0°C, crit = +105.0°C)

Battery:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +51.0°C  (crit = +108.0°C)

asus-isa-0000
Adapter: ISA adapter
temp1:        +51.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +51.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +49.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +50.0°C  (high = +87.0°C, crit = +105.0°C)

---

### Post by wonghang on 2013-01-17
> **screemo said:**
> You should upgrade your kernel to 3.5 series (and to ubuntu 12.10)-
Also here's how to set up bumblebee: [http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/](http://www.ivegotavirus.com/how-to-fix-bumblebee-on-ubuntu-12-10/)

I just tried to use kernel 3.5 using:

```
sudo apt-get install linux-image-generic-lts-quantal

```

The version that I get is linux-image-3.5.0-21-generic

Then, the system will be hang when xserver start, here is the error that I found in /var/log/kern.log

```
Jan 17 19:23:17 (hostname) kernel: [    2.489917] Pid: 178, comm: modprobe Not tainted 3.5.0-21-generic #32~precise1-Ubuntu ASUSTeK COMPUTER INC. 
UX32VD/UX32VD
Jan 17 19:23:17 (hostname) kernel: [    2.489927] EIP: 0060:[<c15e063a>] EFLAGS: 00010246 CPU: 3
Jan 17 19:23:17 (hostname) kernel: [    2.489934] EIP is at __mutex_lock_slowpath+0x8a/0x120
Jan 17 19:23:17 (hostname) kernel: [    2.489939] EAX: 00000000 EBX: f6358e48 ECX: f6358e50 EDX: f600fe44
Jan 17 19:23:17 (hostname) kernel: [    2.489944] ESI: f6358e4c EDI: 00000000 EBP: f600fe5c ESP: f600fe38
Jan 17 19:23:17 (hostname) kernel: [    2.489949]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 17 19:23:17 (hostname) kernel: [    2.489954] CR0: 80050033 CR2: b7539450 CR3: 367b7000 CR4: 001407f0
Jan 17 19:23:17 (hostname) kernel: [    2.489959] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
Jan 17 19:23:17 (hostname) kernel: [    2.489964] DR6: ffff0ff0 DR7: 00000400
Jan 17 19:23:17 (hostname) kernel: [    2.489968] Process modprobe (pid: 178, ti=f600e000 task=f61db2c0 task.ti=f600e000)
Jan 17 19:23:17 (hostname) kernel: [    2.489974] Stack:
Jan 17 19:23:17 (hostname) kernel: [    2.489977]  00000000 f6358e50 f61db2c0 f6358e50 00000000 c19cd263 f6358e48 f6358c00
Jan 17 19:23:17 (hostname) kernel: [    2.489989]  f6358e48 f600fe6c c15e0324 00000000 f6358c00 f600fe90 f85dae73 00000000
Jan 17 19:23:17 (hostname) kernel: [    2.490001]  00000000 f84ed005 f600fe90 f6358c00 f85fd000 ffffffea f600fe9c f85a1ddb
Jan 17 19:23:17 (hostname) kernel: [    2.490012] Call Trace:
Jan 17 19:23:17 (hostname) kernel: [    2.490019]  [<c15e0324>] mutex_lock+0x24/0x40
Jan 17 19:23:17 (hostname) kernel: [    2.490050]  [<f85dae73>] intel_fb_restore_mode+0x23/0xa0 [i915]
Jan 17 19:23:17 (hostname) kernel: [    2.490073]  [<f85a1ddb>] i915_driver_lastclose+0x2b/0x50 [i915]
Jan 17 19:23:17 (hostname) kernel: [    2.490088]  [<f84cc155>] drm_lastclose+0x45/0x2b0 [drm]
Jan 17 19:23:17 (hostname) kernel: [    2.490104]  [<f84d1b50>] drm_fill_in_dev+0x110/0x180 [drm]
Jan 17 19:23:17 (hostname) kernel: [    2.490119]  [<f84d3ccf>] drm_get_pci_dev+0xaf/0x290 [drm]
Jan 17 19:23:17 (hostname) kernel: [    2.490132]  [<f84d3f7b>] drm_pci_init+0xcb/0x110 [drm]
Jan 17 19:23:17 (hostname) kernel: [    2.490151]  [<f849b05e>] i915_init+0x5e/0x60 [i915]
Jan 17 19:23:17 (hostname) kernel: [    2.490158]  [<c1003034>] do_one_initcall+0x34/0x170
Jan 17 19:23:17 (hostname) kernel: [    2.490164]  [<f849b000>] ? 0xf849afff
Jan 17 19:23:17 (hostname) kernel: [    2.490171]  [<c10a4e7d>] sys_init_module+0xad/0x210
Jan 17 19:23:17 (hostname) kernel: [    2.490178]  [<c15e955f>] sysenter_do_call+0x12/0x28
Jan 17 19:23:17 (hostname) kernel: [    2.490183] Code: 20 63 7f bd 90 8d 74 26 00 8d 73 04 89 f0 e8 9e 1b 00 00 8d 43 08 89 45 e0 8b 43 0c 8d 55 e8 8b 4d e0 89 53 0c 89 45 ec 89 4d e8 <89> 10 8b 45 e4 ba ff ff ff ff 89 45 f0 89 d0 87 03 83 f8 01 74 
Jan 17 19:23:17 (hostname) kernel: [    2.490239] EIP: [<c15e063a>] __mutex_lock_slowpath+0x8a/0x120 SS:ESP 0068:f600fe38
Jan 17 19:23:17 (hostname) kernel: [    2.490248] CR2: 0000000000000000
Jan 17 19:23:17 (hostname) kernel: [    2.490253] ---[ end trace 53e0e0b44e9a1d67 ]---
Jan 17 19:23:17 (hostname) kernel: [    2.530497] Refined TSC clocksource calibration: 1696.146 MHz.


```

...any idea to solve?

---

### Post by csierra on 2013-01-24
> **Rubadubdub said:**
> sorry for the late reply/update.

Well the problem with my laptop freezing when re-plugging the power left me no choice. I ditched the xorg-edgers ppa. 

I went back to kernel 3.5.0-22 and I must say that I am glad because now the only thing not working are the brightness keys.

What is working is:
[LIST]
[*]No more banding
[*]primusrun & optirun running like a charm
[*]usb devices working with power plugged in and on battery
[*]connecting detaching external monitor via mini vga with no problems
[*]longer battery life 5-6 hours
[*] no problem connecting power when computer is running (with kernel 3.7 everytime a kernel panic)
[/LIST]

And for what's not working (the brightness keys) a workable sollution. I am running Gnome Shell and I added the following extension:
[https://extensions.gnome.org/extension/231/brightness-control/](https://extensions.gnome.org/extension/231/brightness-control/)

I enabled Intel SNA acceleration:
[http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html](http://www.webupd8.org/2012/10/how-to-enable-intel-sna-acceleration-in.html)

I also installed Bumblebee and Primus and the Nvidia Experimental drivers 310: 
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results](http://www.webupd8.org/2012/11/primus-better-performance-and-less.html#uds-search-results)
[http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html](http://www.webupd8.org/2012/12/use-nvidia-experimental-drivers-310.html)

So for now I am a happy camper.

Hi... I am using Ubuntu 12.10 with my UX32VD without problems using kernel 3.5.0-18. After ubuntu updated the kernel my modules are not loaded automatically anymore. If I manually choose kernel 3.5.0-18 it works quite all right as you describe, but only with this kernel. 

Is there anything I might have missed to get it working in newer versions of Ubuntu kernel?

Thanks in advance

---

### Post by demontager on 2013-02-21
I can't get bumbelbee working with kernels above 3.6 (which are raring) The reason to install raring kernel is to get Fn keys working. The full log is here [http://pastebin.com/8vf77BUc](http://pastebin.com/8vf77BUc)
The main problem focused on missed apport module 
```

 File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.7.0-030700-generic (x86_64)


```

---

### Post by peter rus on 2013-02-21
It works great for me, when using the current xorg-edgers kernel.

---

### Post by demontager on 2013-02-21
Do you mean this one ?

[http://www.ubuntuupdates.org/ppa/xorg-edgers](http://www.ubuntuupdates.org/ppa/xorg-edgers)

```

sudo add-apt-repository ppa:xorg-edgers/ppa 
sudo apt-get update
sudo apt-get install <package name>

```

How about Bumblebee did you touch some settings ?
It still not work for me on 3.8
```

 uname -r
3.8.0-030800-generic
dem@dem-UX32VD:~$ optirun firefox
[   64.813612] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver

[   64.813691] [ERROR]Aborting because fallback start is disabled.

```

---

### Post by demontager on 2013-02-21
Seems like won't work for now   [http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/linux-image-3.7.0-5-generic](http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/linux-image-3.7.0-5-generic)

---

### Post by peter rus on 2013-02-21
> **demontager said:**
> Seems like won't work for now   [http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/linux-image-3.7.0-5-generic](http://www.ubuntuupdates.org/package/xorg-edgers/quantal/main/base/linux-image-3.7.0-5-generic)

On what information do you base that?

I am running: 
Linux host 3.7.0-7-generic #15-Ubuntu SMP Sat Dec 15 16:34:25 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

(which I got through xorg-edgers)

The reason your installation of bumblebee doesn't work is probably because it can't load the 'nvidia' module ;)

try to do a 
```

dpkg-reconfigure nvidia-current

```

DKMS ([http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)) will then try to recompile the module (or least some abstraction layer, as the module itself is closed-source, don't pin me down here ;) ) for your current kernel. If it fails with some kind of 'not supported' message DKMS does not support you current kernel (the case on most mainline kernels, correct me if wrong). The xorg-edgers kernelmodule should compile fine though. 

Then retry

---

### Post by demontager on 2013-02-22
**peter_rus**,
It based on information from xorg-edgers repository where kernel has been removed. If you still able to install from there, how is it possible ?
Ok, I got Bumbelbee working on 3.6.3 quantal mainline kernel
```

dem@dem-UX32VD:~$ uname -r
3.6.3-030603-generic
dem@dem-UX32VD:~$ optirun glxgears
3297 frames in 5.0 seconds = 659.367 FPS
3318 frames in 5.0 seconds = 663.464 FPS
3326 frames in 5.0 seconds = 665.136 FPS
3327 frames in 5.0 seconds = 665.310 FPS

```

So, I have also screen brightness control working, but not keyboard backlight. I may swith off it like so -
```

 echo 0 | sudo tee /sys/class/leds/asus\:\:kbd_backlight/brightness 


```
 Solution to get it working by installing this [http://www.linlap.com/asus_ux32vd](http://www.linlap.com/asus_ux32vd)  (comment from Alec) -
```

sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update && sudo apt-get install dkms
sudo dpkg -i ~/Downloads/asus-wmi-dkms_0.2_all.deb
sudo reboot

```
Just cause volume control not operational.

---

### Post by olanod on 2013-03-15
Hello, I had kernel 3.5 using indicator-brightness to adjust brightness and updated to 3.8.3 to fix several issues including brightness keys but now neither of them work and now I'm stuck with 100% brightness level.

---

### Post by Wolfgang Griech on 2013-04-04
Hi,
am just using out-of-the-box kubuntu 12.10 64bit on an UX31A, BIOS 218, and about everything is working properly, even now the fn-f5+f6 for screen brighness control, found a simple fix for it on another thread here, [http://ubuntuforums.org/showthread.php?t=2006790&page=5](http://ubuntuforums.org/showthread.php?t=2006790&page=5) post #47:

[h=2]UX31A -- A simple way to fix the brightness Fn keys[/h][COLOR=#000000][INDENT]This does not involve changing the kernel. 
I tested it with precise, using both the standard 3.2 kernel, or the upgraded 3.5 kernel.

Change kernel command lines in /etc/default/grub as follows

[FONT=courier new]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4 pcie_aspm=force nmi_watchdog=0"
GRUB_CMDLINE_LINUX='acpi_osi="!Windows 2006" acpi_osi="!Windows 2009" acpi_osi="!Windows 2012"'
[/FONT]
Then run [FONT=courier new]update-grub[/FONT].

After rebooting, the screen brightness function keys work.[/INDENT]
[/COLOR]

---

### Post by Wolfgang Griech on 2013-04-04
..and just to give an idea how low power consumption could be under kubuntu 12.10 64-bit on an i7 UX31A, here a screen shot of today, after applying about all what was said here in this thread and in the appropriate wiki [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime), average power consumption dropped below 5.5 W, of course BT and Wifi off, and screen at minimum brightness, and kbd backlite turned off, and ALPM activated:

[ATTACH=CONFIG]240936[/ATTACH]

---

### Post by babooka on 2013-04-13
I am trying to install 12.10 on my new ux32vd, however after grub menu, the screen is black and nothing is happening.

I have tried using "nomodeset," with the same results.

ps; I am booting off of the external dvd drive

Update: nevermind, needed to disable "SecureBoot" in BIOS

---

### Post by raidflex on 2013-04-24
Is there anyway to get the Ambient light sensor to work for the screen brightness on the Asus UX32VD with Ubuntu 13.04? I can use the function keys to do it, but it was nice when I had Windows 8 on the laptop that it would automatically adjust the screen brightness.

---

### Post by Wolfgang Griech on 2013-04-26
today my system got upgraded to kubuntu 13.04. Basically everything worked, except the fn keys, just f5+f6 still did it. After some short investigation it showed up that

/sys/class/leds/asus::kbd_backlight/

was completely missing. After some searching I figured out I had to uninstall the asus-wmi-dkms package I needed before on 12.10 according to recommendations here. So I did:

sudo dpkg -r asus-wmi-dkms

and after a reboot all fn keys worked again (probably reloading the asus_wmi module would have done the same..). Just for completeness how my /etc/default/grub looks like:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rootfstype=ext4 add_efi_memmap i915.i915_enable_rc6=1 pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 nmi_watchdog=0"
GRUB_CMDLINE_LINUX='acpi_osi="!Windows 2006" acpi_osi="!Windows 2009" acpi_osi="!Windows 2012"'

---

### Post by k-o-x on 2013-04-28
I just installed Ubuntu 13.04 (GNOME edition) from scratch on my UX32VD and everything works out of the box, except for the ambient light sensor (and of course I needed Bumblebee to enable/disable the discrete GPU). Thanks a lot to the community for their work on supporting hardware. The experience with this zenbook is close to perfection !

I've seen people having problems with Fn-F5/F6, and [the wiki]("https://help.ubuntu.com/community/AsusZenbookPrime") states that it doesn't work, but I dind't have any problems with them (even Fn-F3/F4 work for the keyboard backlight, which was a very pleasant surprise). Doesn't this problem affect only upgrades from 12.10 ?

I still have some questions about power management, as it is not really clear to me what the various fixes from the wiki do:
- Are all kernel parameters still needed ? I couldn't see any difference when adding them (actually, drm.vblankoffdelay=1 prevented X.org form starting)
- Is the PCI udev power management script still useful ?
- Does TLP conflict with those, or does it perform a completely different job ?

---

### Post by AsusLappy on 2013-05-02
Alright the above post seems promising, but after skimming several sites on the ux31a running ubuntu I'm a little confused. So what doesn't work out of the box in 13.04?

[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
This site states right off the bat that nearly everything works out of the box, but then seems to outline things that still don't work. What is the ambient light sensor? Because apparently that doesn't work. Does the keyboard backlight not work after suspend? Can you not right click or click and drag? These issues have fixes on that site making me wonder if they work in 13.04. And finally, how is power management, do I still need to edit some files?

---

### Post by raxman on 2013-05-02
I installed Linux Mint 14 on my ASUS UX31A with no problems.  There are some things to do to improve it I think but I have not tried any of them yet because it works so well.  Well actually, I think the webcam is often too dark but I think that could be fixed

[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
"
Ubuntu recognizes the camera out of the box. If you  find video too dark when using video-conferencing apps (eg. Skype,  Google Hangouts) install and run **guvcview** and adjust your brightness, contrast and gamma settings. 

sudo apt-get install guvcviewIf this option doesn't work you can also try entering 

uvcdynctrl -s "Exposure, Auto Priority" 1in the shell while Skype is running, to boost your gamma settings."

---

### Post by k-o-x on 2013-05-06
The ambient light sensor is used (when using Windows) to automatically adjust keyboard/LCD backlight to ambient light.

I don't know the difference between UX31A and UX32VD but I had no problems with the touchpad or backlight. And about power management, I installed TLP and added some kernel parameters as stated in the wiki, and everything seems fine. I had to install Bumblebee to turn off the nvidia GPU when not using it, but I don't know if the UX31A has a discrete GPU.

No problems either with Fn keys, Bluetooth, Wifi, USB 3 or the webcam.

---

### Post by AsusLappy on 2013-05-13
Woo I've been rocking 13.04-Gnome on the ux31a for a week now and it's a dream machine. Everything worked out of the box, but i'm curious, does anyone use additional drivers? Is it beneficial? Possible? Because none are listed in the additional drivers tab.

Also I do have two minor quirks with this setup. Lack of dpi scaling :/ I can set default zooms and larger text and stuff, but it's not a true solution because chrome tabs are still tiny slivers, window buttons are tiny, etc. :/ And the trackpad driver could be better.

---

### Post by Linuxisfast on 2013-05-31
If its showing additional drivers, my recommendation would be to install them for better performance.

---

### Post by revscafe on 2013-06-06
peter rus, you are AWESOME!!! This also works on ASUS Q500A without any modifications to the instructions (refering to post #73). Now to dig around for touchscreen support.

---

### Post by 2xyo on 2013-06-15
Edit : 
I'm just an idiot :-) : I'have accidently lock my touchpad with the fn key..

---

### Post by k-o-x on 2013-06-29
Just a fair bit of a warning for those tempted by the gnome3-staging PPA on raring, at least when using gnome-shell (not tested with unity): there are some issues at least with the UX32VD. The two main issues I found were the following:
- Wifi and Bluetooth are disabled when resuming from suspend to ram/disk (Shell applet says "not available", using rfkill does not help, and they only become available after a reboot)
- Shutdown, reboot, suspend, hibernate and close session do not work when called from the Shell user menu. They kill gnome-settings-daemon (the main visible effect is that icon, gtk and shell themes revert to the default ones) but don't do anything else. It works from command line though (and you may want to create launcher for PM commands).

These problems seem to come from gnome-settings-daemon and I have reported bugs about them.

---

### Post by Dave231153 on 2013-06-30
I have an AsusK55 and I have got Ubuntu 13.04 in a dual system with Windows 8. This computer is Ivybridge and everything works really well, the hardest thing was working out how to get my install of Ubuntu to work, when I worked it out I wrote a tutorial and put on this forum, Matt moved it to the tutorials section.

---

### Post by praveen2600 on 2013-08-11
I was trying some power saving options on UX32VD as suggested on [https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations](https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations).
I added 
pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1in /etc/defualt/grub

But here is output of my update-grub command 

/usr/sbin/grub-mkconfig: 36: /etc/default/grub: drm.vblankoffdelay=1: not found

Any idea what is going wrong?

---

### Post by wapko on 2013-09-06
just as a heads up.. 
i installed ubuntu on my ux32vd's internal ssd. and after 4 months the internal ssd died. sent it in for repair and they replaced the motherboard. im no longer using the internal ssd for anything. when it was dead the whole computer was excruciatingly slow. took 2 minutes just to enter bios. 11 minutes to boot windows. it started with a lot of DMA READ errors. and then it died. 
you have been warned. :)

i had trim and snazzy ssd stuff enabled. but if you have some insight. please go ahead ;)

---

### Post by Linuxisfast on 2013-09-06
With the Zenbook I just add acpios=Windows 2012 as described in the Wiki, enable ssd trim and that takes care of my brightness and ssd issues. I use the latest Ubuntu 12.04.3 LTS which adds nvidia optimus support right during install and it works swell. For power savings nothing works like TLP from [www.linrunner.de](www.linrunner.de)

---

### Post by rpavelu on 2013-09-10
> **praveen2600 said:**
> I was trying some power saving options on UX32VD as suggested on [https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations](https://help.ubuntu.com/community/AsusZenbookPrime#Power_Saving_Optimizations).
I added 
pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1in /etc/defualt/grub

But here is output of my update-grub command 

/usr/sbin/grub-mkconfig: 36: /etc/default/grub: drm.vblankoffdelay=1: not found

Any idea what is going wrong?

Same here :(

---

### Post by kyosaku on 2013-10-09
> **wapko said:**
> just as a heads up.. 
i installed ubuntu on my ux32vd's internal ssd. and after 4 months the internal ssd died. sent it in for repair and they replaced the motherboard. im no longer using the internal ssd for anything. when it was dead the whole computer was excruciatingly slow. took 2 minutes just to enter bios. 11 minutes to boot windows. it started with a lot of DMA READ errors. and then it died. 
you have been warned. :)

i had trim and snazzy ssd stuff enabled. but if you have some insight. please go ahead ;)

Hi there,

I have the same setup as you do, Ubuntu running on internal SSD and trim enabled.  But I am curious, what do you mean by "snazzy ssd stuff" you set up ?
Thanks for your reply

---

