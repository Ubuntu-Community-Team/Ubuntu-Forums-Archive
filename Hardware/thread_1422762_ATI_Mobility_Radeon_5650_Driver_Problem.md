---
title: "ATI Mobility Radeon 5650 Driver Problem"
date: 2010-03-05
forum: Hardware
---

### Post by Robster2 on 2010-03-05
Ubuntu 9.10  Acer Aspire 5740G Notebook.  ATI Mobility Radeon 5650

This is a weird one.  I installed ubuntu 9.10  it detected Wifi everything and suggested I install the ATI/AMD proprietary FGLRX graphic driver.

Well every thing appears to work fine. Got the Compiz cube rotating,  The effects for opening windows tried them all worked fine.

Except there is this watermark on the corner of the screen that says "AMD Unsupported hardware".

Interestingly ATI Catalyst control center has appeared in the menus.  Changing the settings does not appear to do anything.
There is an Administration menu that appears to not run.

The AMD website does not appear to have a Linux driver for this video card.  

Should I leave the current driver, remove the current driver and live without the eye candy, try and wrap the windows driver or do something else.

---

### Post by v.cecchetto on 2010-03-06
I think you can look here for the watermark question:
[http://ubuntuforums.org/showpost.php?p=8230858&postcount=17](http://ubuntuforums.org/showpost.php?p=8230858&postcount=17)

---

### Post by swamisant on 2010-03-06
I have same issue. It seems that ATI has not released any driver for this Mobility Radeon HD 5650 card or in fact 5*** series.

@Robster2 Have you tried Dual monitor setup? If yes was that working.

---

### Post by markbuntu on 2010-03-06
Usually support for the card is not quite complete for things like the Catalyst Control Center amdcccle and some of the functions may not be controllable yet but the driver is substantially complete if you see the watermark. You can try opening CCC from a terminal with

sudo amdcccle

alernatively you can use aticonfig command to make changes

aticonfig --help

You can keep that driver if it is working OK for you and get the next one when it is released. Be sure to remove the old driver before installing the new one. Use the removal script at usr/share/ati/fglrx-uninstall.sh

---

### Post by Robster2 on 2010-03-07
> **v.cecchetto said:**
> I think you can look here for the watermark question:
[http://ubuntuforums.org/showpost.php?p=8230858&postcount=17](http://ubuntuforums.org/showpost.php?p=8230858&postcount=17)

Worked like a dream - Thanks!!

---

### Post by Robster2 on 2010-03-07
> **swamisant said:**
> I have same issue. It seems that ATI has not released any driver for this Mobility Radeon HD 5650 card or in fact 5*** series.

@Robster2 Have you tried Dual monitor setup? If yes was that working.

Looking at display in the preferences menu says "monitor unknown"

---

### Post by Robster2 on 2010-03-07
Thanks to everyone for your replies.

---

### Post by just for fun on 2010-03-07
But the driver works fine, apart from the logo problem? I'm asking because I want to buy a notebook with a 5650 graphik chip.

excuse my bad English :!:

just for fun

---

### Post by Robster2 on 2010-03-08
> **just for fun said:**
> But the driver works fine, apart from the logo problem? I'm asking because I want to buy a notebook with a 5650 graphik chip.
just for fun

Yes it works fine - Go for it.  If something is wrong I can't find it.

How to remove watermark reposted from BaffledMollusc

> Right click on the desktop and choose Create Document -> Empty File
Call it something like "remove_watermark.sh"
Double click on the file you've created to open it in the text editor
Paste the following text into the text editor

```

#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done

```

Save the file and close the text editor
Right click on the desktop icon you've created and choose "Properties->Permissions"
Tick the box "allow executing file as program"
Close the properties dialog
Open a terminal (Applications -> Accessories -> Terminal)
Type the following two lines into the terminal, pressing enter after each line

cd Desktop
sudo sh remove_watermark.sh

Now enter your login password when prompted

Finally log out and back in and the watermark will hopefully be gone!

---

### Post by v.cecchetto on 2010-03-09
Yes the driver works good for me too :)

---

### Post by Cuppa-Chino on 2010-03-17
can I ask which exact driver this is? the fglrx from the repo or the 10.2 from the amd website? thanks

---

### Post by krazyito65 on 2010-03-27
Hello. I am about to try this fix and I am sure it should work.. but i have another problem other than the watermark.. when i install the driver i get the watermark and i get lines going across my screen.. usually only happens when i move a window.. or sometimes the mouse. pretty much when ever i use it in general.. The same exact thing happend in Windows 7, but i was able to fix the problem by downloading a driver from the ATI site instead of my manufacturer.

Here are my specs:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834101222](http://www.newegg.com/Product/Product.aspx?Item=N82E16834101222)
(i just bought this computer recently)

i will now proceed with the watermark removal fix. if it does not fix the problem iwth the lines  i will keep this post up. if it does fix it, i will edit and say so.

EDIT: Well the watermark IS gone. so that is good news! but unfortunately the lines still flicker across the screen as i use it.
And help please?

---

### Post by Jazzinghen on 2010-03-30
I've got the same problem as krazyito65. Also I have problems with gradients, they are shown with banding effect, as if I'm using a 16bit color depth.

I don't think that removing a watermark counts as a real fix, it's only a small patch. My Xorg server can't recognize my screen so it can't set the right colorspace.

---

### Post by tosk on 2010-04-08
According to AMD, all driver support for the Mobility Radeon line is the responsibility of the OEM.

Source: [http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx](http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx)

However, as others have reported, you can use the fglrx driver and it should work for the most part, except for the watermark. But you can remove the watermark using the fix listed above in the thread.

I have a Dell Studio 1749 with a Mobility Radeon 5650 1GB and the fglrx driver worked for me. My max resolution of 1600x900 (16:9) was supported and everything appeared to work as it should.

---

### Post by ultiva on 2010-04-08
> **tosk said:**
> According to AMD, all driver support for the Mobility Radeon line is the responsibility of the OEM.

Source: [http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx](http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx)

However, as others have reported, you can use the fglrx driver and it should work for the most part, except for the watermark. But you can remove the watermark using the fix listed above in the thread.

I have a Dell Studio 1749 with a Mobility Radeon 5650 1GB and the fglrx driver worked for me. My max resolution of 1600x900 (16:9) was supported and everything appeared to work as it should.

Great, I've been looking especially for laptop with AMD graphics, because on my father's old laptop with X700 radeon everything works including 3D on opensource drivers. I'm really disappointed and if that gradients are not fixed I'll never buy anything from AMD, because that means AMD mobility graphics are not supported under linux. If you look into amd catalyst 10.3 release notes for linux and windows on ati.amd.com you can see that windows driver supports mobility radeon hd 5XXX series and linux driver doesn't.

Ps. My max resolution 1366x768 also is detected correctly and everything else works except that colours that look like 16 bit colour depth. In my opinion it's not caused by undetected display. It look like not complete driver support for card.

EDIT:
OK, here's the way how to correct those fckn gradients. It worked on my Vaio - Ubuntu 9.10 32bit.
1. Install fglrx driver from Ubuntu repo - standard install
2. Install latest driver from ati.amd.com for linux using AMD installator (while previous driver is installed)
3. Use patch to remove watermark
4. VIOLA even my display is now detected as "Laptop" NOT "UNKNOWN"

Ps2. AMD webpage says that Sony Vaio is not supported by generic AMD driver. However look like this particular model VPC-EB1S1E is supported coz everything now works as it should (besides watermark ofcourse).

---

### Post by Cuppa-Chino on 2010-04-10
> **ultiva said:**
> Great, I've been looking especially for laptop with AMD graphics, because on my father's old laptop with X700 radeon everything works including 3D on opensource drivers. I'm really disappointed and if that gradients are not fixed I'll never buy anything from AMD, because that means AMD mobility graphics are not supported under linux. If you look into amd catalyst 10.3 release notes for linux and windows on ati.amd.com you can see that windows driver supports mobility radeon hd 5XXX series and linux driver doesn't.

Ps. My max resolution 1366x768 also is detected correctly and everything else works except that colours that look like 16 bit colour depth. In my opinion it's not caused by undetected display. It look like not complete driver support for card.

EDIT:
OK, here's the way how to correct those fckn gradients. It worked on my Vaio - Ubuntu 9.10 32bit.
1. Install fglrx driver from Ubuntu repo - standard install
2. Install latest driver from ati.amd.com for linux using AMD installator (while previous driver is installed)
3. Use patch to remove watermark
4. VIOLA even my display is now detected as "Laptop" NOT "UNKNOWN"

Ps2. AMD webpage says that Sony Vaio is not supported by generic AMD driver. However look like this particular model VPC-EB1S1E is supported coz everything now works as it should (besides watermark ofcourse).

just to confirm you have a vaio E-series VPCEB1se1 (European model ?), with hd ready display and you managed to get it work under 9.10, if so I recommend you do not upgrade to lucid directly as a lot of us have tried getting it to work on lucid with no success.

could you be so kind as to post your xorg.conf & you Xorg.0.log so I can see it and check if there is anything I can learn for my attempts to get it to work on 10.04

thanks, I would really really appreciate it

---

### Post by ultiva on 2010-04-10
Yes, I have VPC-EB1S1E/WI (white). It's European model I suppose because I've bought it in my local RTV store.

Display 1366x768 - HD ready

Here are my screenshots with display settings (screens are in my native language, sorry - but everything should be understandable)
[http://sonylaptop.sikorski.org.pl/scr1.png](http://sonylaptop.sikorski.org.pl/scr1.png)
[http://sonylaptop.sikorski.org.pl/scr2.png](http://sonylaptop.sikorski.org.pl/scr2.png)

One more which is little more "gradiented" - to show colours
[http://sonylaptop.sikorski.org.pl/scr3.png](http://sonylaptop.sikorski.org.pl/scr3.png)

And my Xorg files
[http://sonylaptop.sikorski.org.pl/xorg.conf](http://sonylaptop.sikorski.org.pl/xorg.conf)
[http://sonylaptop.sikorski.org.pl/Xorg.0.log](http://sonylaptop.sikorski.org.pl/Xorg.0.log)

I was hoping to repeat all this steps on 10.04 when final version is available, because I treat this install as battlefield test platform for learning new hardware :) It works quite stable now and pretty everything works (except wifi errors in dmesg on madwifi driver and sound not starting automagically during bootup - I must do the trick with hdaverb manually) There is quite a mess done with the kernel :) And hmmm.. little "rm -rf *" accidentaly done in home dir hehehe, but that seem to patch itselt after reboot.

If U say that 10.04 is more resistant, maybe it would be better to compile alsa with patches for the sound and leave it that way :)

---

### Post by Cuppa-Chino on 2010-04-10
very interesting and very helpful, a BIG THANK YOU FIRST

 -- hmm mine always crashes at the ddc stage 
```
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): Finished Initialize PPLIB!
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
==> SEGFAULTS HERE

```

then segfault and I am not the only one, it looks like it reads the EDID data in your case, now I hate having to ask another favour or question but do you still have your windows partition and if so what do you read from the EDID stream there? 

I read in the [nv-forums]("http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22") about a similar issue on sony's with nvidia card and how the person used [softMCCS]("http://www.entechtaiwan.com/lib/softmccs.shtm") to generate an EDID bin file

I have done this and my display is supposedly made by Microsoft! (when I boot into windows next time will post it) the analysis from softMCCS shows that my display does NOT support DDC, it looks like yours seemingly does -- or the configuration catalyst 10.1/2/3 plus Xorg 1.6 does.

hmm more digging to be done...

so this is my ddc log from softMCCS:
```
21:54:12.01939...*******************************************
21:54:12.0203A...Found device on ATI Mobility Radeon HD 5650
21:54:12.0203B...Monitor ID = Microsoft MS_0025 (MS_0025.n/a)
21:54:12.0203C...Raw EDID = 00FFFFFFFFFFFF00367F2500000000000413010380221378F2CE50A3574C99260F5054000000010101010101010101010101010101011A36809A7038224019335B0054BE100000001A3680C4713858404B96ED0054BE10000000000000000000000000000000000000000000000000000000000000000000000000000000000A
21:54:12.5913D...Error: failed to obtain driver output mask - FFFFFFFF
21:54:12.5923E...Error: failed to obtain capabilities string length from OS
21:54:13.1693F...Error: failed to obtain driver output mask - FFFFFFFF
21:54:13.17140...Error: failed to obtain capabilities string length from OS
21:54:13.83641...Error: failed to obtain driver output mask - FFFFFFFF
21:54:13.83742...Error: failed to obtain capabilities string length from OS
21:54:14.60243...Error: failed to obtain driver output mask - FFFFFFFF
21:54:14.60344...Error: failed to obtain capabilities string length from OS
21:54:14.60345...MS_0025 on ATI Mobility Radeon HD 5650 does not respond to DDC/CI
21:54:14.60346...*******************************************
21:54:14.60447...Software monitor enumeration
21:54:14.60448...Monitor #1: Microsoft MS_0025
21:54:14.60449.............. Hardware ID: 0x0000
21:54:14.6064A.............. Device handle: 0x00010001
21:54:14.6064B.............. Device number: 0
21:54:14.6074C.............. Device name: \\.\DISPLAY1
21:54:14.6074D.............. Device string: ATI Mobility Radeon HD 5650
21:54:14.6074E.............. Device ID: PCI\VEN_1002&DEV_68C1&SUBSYS_9071104D&REV_00
21:54:14.6074F.............. Device flags: 0x00000005
21:54:14.60850.............. Device driver: atiumd64 8.14.10.708
21:54:14.60851.............. Monitor name: \\.\DISPLAY1\Monitor0
21:54:14.60852.............. Monitor string: Digital Flat Panel (1920x1080 60Hz)
21:54:14.60853.............. Monitor flags: 0x00000003
21:54:14.60954.............. Coordinates: 0,0,1920,1080
21:54:15.60955...Finished monitor enumeration, total elapsed time = 6411 ms
21:54:15.60956...Number of monitors enumerated = 1 total, 0 DDC/CI
21:54:15.60957...\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
```

---

### Post by ultiva on 2010-04-10
I've installed this software.
Here's what it says:

Manufacturer name: Sony SNY05FA
Product code: SNY05FA
Manufactured: 2009 ISO week 4
EDID version: 1.3
Input type: Digital
Prefered timing: 1366x768 at 60Hz
Extension blocks: 0
Raw data: [many strange numbers here] ;)
DDC/CI: not supported [marked red]

This program looks little scary I must say... like it's capable of sending laptop into space :) Tell me what else info from that stuff you need.

Here's my log:
```

22:22:23.5343F...*******************************************
22:22:23.53440...Found device on ATI Mobility Radeon HD 5600/5700 Series
22:22:23.53441...Monitor ID = Sony SNY05FA (SNY05FA.n/a)
22:22:23.53442...Raw EDID = 00FFFFFFFFFFFF004DD9FA05000000000413010380221378F2CE50A3574C99260F505400000001010101010101010101010101010101201C56AE50000C301D3A240054BE100000006E155630500008300810120054BE10000000000000000000000000000000000000000000000000000000000000000000000000000000007B
22:22:24.09643...Error: failed to obtain driver output mask - FFFFFFFF
22:22:24.09644...Error: failed to obtain capabilities string length from OS
22:22:24.76745...Error: failed to obtain driver output mask - FFFFFFFF
22:22:24.76746...Error: failed to obtain capabilities string length from OS
22:22:25.56247...Error: failed to obtain driver output mask - FFFFFFFF
22:22:25.56248...Error: failed to obtain capabilities string length from OS
22:22:26.45249...Error: failed to obtain driver output mask - FFFFFFFF
22:22:26.4524A...Error: failed to obtain capabilities string length from OS
22:22:26.4524B...SNY05FA on ATI Mobility Radeon HD 5600/5700 Series does not respond to DDC/CI
22:22:26.4524C...*******************************************
22:22:26.4524D...Software monitor enumeration
22:22:26.4524E...Monitor #1: Sony SNY05FA
22:22:26.4524F.............. Hardware ID: 0x0000
22:22:26.45250.............. Device handle: 0x00010001
22:22:26.45251.............. Device number: 0
22:22:26.45252.............. Device name: \\.\DISPLAY1
22:22:26.45253.............. Device string: ATI Mobility Radeon HD 5600/5700 Series
22:22:26.45254.............. Device ID: PCI\VEN_1002&DEV_68C1&SUBSYS_9071104D&REV_00
22:22:26.45255.............. Device flags: 0x00000005
22:22:26.45256.............. Device driver: atiu9p64 8.14.1.6099
22:22:26.45257.............. Monitor name: \\.\DISPLAY1\Monitor0
22:22:26.45258.............. Monitor string: Generic PnP Monitor
22:22:26.45259.............. Monitor flags: 0x00000003
22:22:26.4525A.............. Coordinates: 0,0,1366,768
22:22:27.4665B...Finished monitor enumeration, total elapsed time = 7987 ms
22:22:27.4665C...Number of monitors enumerated = 1 total, 0 DDC/CI
22:22:27.4665D...\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
22:26:00.4035E...*******************************************

```

---

### Post by Cuppa-Chino on 2010-04-10
sorry took so long but finally got the screenshots of the output together:

from looking at your output there seems to be 1 MONITOR / 0 DDC just like mine so that means that your display also does not send back the info....

this makes me a lot more optimistic as to a fix, because if your 9.10 U with Xorg 1.6 and Cat 1.3 can run with that output then the bug should be fixable!

dude you have been a great help!

btw two of the screenshots were taken from Powerstrip also by entech and you can see how the screen is defined as 1920x1080 in one section and 640x480 in another as the tool cannot get any data from the display!

---

### Post by Wanas on 2010-05-06
Can any one help me if this GPU (ATI Mobility Radeon 5650) works fine with the HD videos (720p & 1080i) on ubuntu ? I'm planing to buy this laptop (Acer Aspire AS5740G-6979) with this GPU. 

Or should I go with nvidia for the vdpau support ?

I am HD videos Addicted !!

---

### Post by krazyito65 on 2010-05-06
> **krazyito65 said:**
> Hello. I am about to try this fix and I am sure it should work.. but i have another problem other than the watermark.. when i install the driver i get the watermark and i get lines going across my screen.. usually only happens when i move a window.. or sometimes the mouse. pretty much when ever i use it in general.. The same exact thing happend in Windows 7, but i was able to fix the problem by downloading a driver from the ATI site instead of my manufacturer.

Here are my specs:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16834101222](http://www.newegg.com/Product/Product.aspx?Item=N82E16834101222)
(i just bought this computer recently)

i will now proceed with the watermark removal fix. if it does not fix the problem iwth the lines  i will keep this post up. if it does fix it, i will edit and say so.

EDIT: Well the watermark IS gone. so that is good news! but unfortunately the lines still flicker across the screen as i use it.
And help please?


Well It looks like doing a fresh install of Lucid Lynx fixed it =D. not sure what happened but im glad i can use it without the constant flickering of lines.

---

### Post by wuschelkoppbw on 2010-05-08
The fglrx driver is not working with my system!? I have also a ati 5650 and after I installed the driver and rebooted the system i only got a black screen ... i have a acer 3820TG ... 
i think i'm not able to install the driver from amd-source witch was given above. am i the only one with this kind of problem? ... or does somebody have an idea to solve it?
thx and please excuse my bad english ;)

---

### Post by hoyab on 2010-05-16
wuschelkoppbw, I have the same issue with the 5650 on 10.04 (x86_64).
I've tried several solutions suggested on various forums, but still just get the black screen on restarting X.
Since this card is not officially supported in the latest ATI Catalyst driver, I assume we have to wait until it is.  I'm not sure if that is on the horizon, but am interested to hear if anyone has any additional knowledge or suggestions.

---

### Post by Welly Wu on 2010-07-24
ATI released an updated ATI Catalyst 10.6 proprietary Linux x86 display driver on 06/16/2010. I wonder if installing it on Ubuntu GNU/Linux 10.04 LTS will suffice and it does not require the watermark patch. I plan on purchasing an Acer Aspire AS7551G-5821 notebook PC and doing a dual boot setup with Microsoft Windows 7 Professional x64 and Ubuntu 10.04 LTS x64.

Has anyone checked out this out on their computer? Thank you.

---

### Post by Yellow Pasque on 2010-07-24
THere is a workaround for the watermark issue here, or you could just use the guide to install the latest Catalyst. Make sure you remove the old one first (also note that Catalyst 10-7 should be out this week): [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

---

### Post by Welly Wu on 2010-07-28
AMD/ATI released 10.7 of their Catalyst package for x64 bit Linux machines on July 26th, 2010 this week.

I plan on purchasing either the Acer Aspire AS7551G-5821 or Lenovo Ideapad Y560-06462EU early next week. If I do get the Acer Aspire, then I think it will be fully compatible with 10.04 LTS right out of the box according to my ongoing research.

In any event, I will let you guys know how it goes since both PCs use ATI GPUs.

---

### Post by mexicanseaf00d on 2010-08-01
The Mobility HD5650 is not listed in the 10.7 release notes! The ATI HP directs me there, but i do not dare to install it - all other ATI drivers gave me black screen on my HP DV7 notebook :(

---

### Post by weiteh on 2010-08-01
I am having the same problem. After installing the driver provided by AMD for ATI Radeon 5650 Mobility HD, after reboot I am getting a blank screen. The documentation does not specify the video card as a supported model. Any else found a work around for this?
Also how do I revert the video driver to the default without a fresh install of the entire distro?

---

### Post by mexicanseaf00d on 2010-08-01
> **weiteh said:**
> 
Also how do I revert the video driver to the default without a fresh install of the entire distro?

Because even Grub/Recovery Mode went black blank on me I had to press 'e' to edit the startup line in grub, put 'nomodeset' above the last line (after the *** ro * etc, cant remember exactly. Sometimes there is 'vga=791' or similar written, replace it with nomodeset)

Then I logged into root shell and removed the drivers with ATI's own uninstaller (see documentation) or with 'sudo apt-get remove fglrx'

I dont know if it has to be done, but i also ran 'Xreset' in /etc/init.d/X11, just to be sure. After the reboot it worked alright again

---

### Post by weiteh on 2010-08-01
> **mexicanseaf00d said:**
> Because even Grub/Recovery Mode went black blank on me I had to press 'e' to edit the startup line in grub, put 'nomodeset' above the last line (after the *** ro * etc, cant remember exactly. Sometimes there is 'vga=791' or similar written, replace it with nomodeset)

Then I logged into root shell and removed the drivers with ATI's own uninstaller (see documentation) or with 'sudo apt-get remove fglrx'

I dont know if it has to be done, but i also ran 'Xreset' in /etc/init.d/X11, just to be sure. After the reboot it worked alright again

Yes, it did the magic of reverting video driver to the default driver with nomodeset. Now I am back to the original problem! :-)

---

### Post by mexicanseaf00d on 2010-08-01
I believe that the bigger part of the blackscreen problem is the 'switchable display device' thing on my notebook - which cant be turned off in bios (thank you, HP)

As far as I can decypher in the X-errorlogs after the driver installation, the driver demands that the discrete card is activated alone. 

If you have a NB, maybe setting your ATI card as primary in BIOS can help your problem?

---

### Post by weiteh on 2010-08-05
> **mexicanseaf00d said:**
> I believe that the bigger part of the blackscreen problem is the 'switchable display device' thing on my notebook - which cant be turned off in bios (thank you, HP)

As far as I can decypher in the X-errorlogs after the driver installation, the driver demands that the discrete card is activated alone. 

If you have a NB, maybe setting your ATI card as primary in BIOS can help your problem?

Has anyone found a workaround for this yet? I keep getting the blank screen trying boot with CD... 
My HP bios also doesn't let me choose the primary video card either. 
May I ask how did you get to the x-errorlogs to identify that setup in the BIOS is the root cause of the problem?

---

### Post by roberto.pierpaoli on 2010-08-19
Maybe I am making a stupid question but... why is this thread marked as SOLVED?... The closing post make it seems still open...

---

### Post by mexicanseaf00d on 2010-08-19
> **roberto.pierpaoli said:**
> Maybe I am making a stupid question but... why is this thread marked as SOLVED?... The closing post make it seems still open...

Because OP's Problem appears to be solved.

I sort of hijacked this thread because above mentioned drivers did not work for me

---

### Post by webdevbrian on 2010-11-13
Just tried it with my DV7 4070-US (5650 ATI), same issue even with the latest x64 10-10 update... Stuck on a black screen an had to resort to my phone to search google, and this thread popped up :S

---

### Post by Confusered on 2010-12-01
Hi, I have a 5650m too, and I can't get it working. I have tried the proprietary drivers and also the open source drivers, which don't seem to work. From the previous threads, it seems like this card isn't supported on Lucid and Maverick yet, but has anyone tried it on Karmic? Thanks.

---

### Post by TweFoju on 2010-12-29
Guys, mind if i join?

so i am using HP Pavilion DV6Z with 5650

i installed the latest Catalyst which is the 10.11 for LINUX 64 bit

but it still detects my Onboard VGA ( the HD4200 ) Instead of the 5650

how can i tell it to read the 5650 instead of the HD 4200?

thanks!

---

### Post by qwer995 on 2011-01-01
> **TweFoju said:**
> Guys, mind if i join?

so i am using HP Pavilion DV6Z with 5650

i installed the latest Catalyst which is the 10.11 for LINUX 64 bit

but it still detects my Onboard VGA ( the HD4200 ) Instead of the 5650

how can i tell it to read the 5650 instead of the HD 4200?

thanks!

I have the same problem too !

---

### Post by Yellow Pasque on 2011-01-01
For those with switchable graphics (2 different GPU's), you're not going to be able to use the 5650. It's simply not supported under Linux at the moment. The best thing you can do is write the system vendors and tell them to put some kind of switch in the BIOS that allows you to turn off the integrated GPU. It's probably not going to happen though..

---

### Post by tonyget on 2011-02-02
Same problem with ATI 5650. All drivers give me the black screen and I have to work without any 3D (no games, no compiz, etc...)

How can we know if the developers are planning to release a driver for this card? and if so, when? I mean, how can I know if I just threw money away buying this ... card or do I have to wait until I get enough money to buy a different one?

---

### Post by Niels_D on 2011-02-04
On my Sony VAIO with 5650 card, the fglrx drivers and the CCC work fine.
I don't see why this should be a problem.

---

### Post by s3Pol on 2011-07-14
Hello,


Niels_D, can you test your HDMI Port?
I have the fglrx driver and ccc installed and the port don't detect the monitor with hdmi cable.
I already test 2 hdmi cables...


01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series] (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 144a
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	Memory at c4400000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 4000 [size=256]
	Expansion ROM at c4440000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon


xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)

---

