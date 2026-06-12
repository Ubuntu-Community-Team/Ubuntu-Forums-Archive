---
title: "ATI mobility Radeon HD 5470"
date: 2010-03-15
forum: Hardware
---

### Post by tornio on 2010-03-15
Good morning,

I have a new asus laptop and I have installed ubuntu KArmic.
The problem is that there is no driver for the ATI mobility radeon HD5470
and the graphic is so bad!

On amd-ati website I have found the catalyst driver version 10.2 but
it seems not to be the correct solution.

Do you have any suggestion?
If there is not the driver for ubuntu, do you think we have to wait
for a long time?

Thanks in advance
Regards.

---

### Post by birdmanuk on 2010-03-15
Hello, I too have the same GPU in my new Sony Vaio. Luckily the screen resolution is OK for the moment, but it would be nice to have the correct driver, so I can enable compiz etc.

My post - [http://ubuntuforums.org/showthread.php?t=1428465&highlight=ATI+Mobility+Radeon+HD+5470](http://ubuntuforums.org/showthread.php?t=1428465&highlight=ATI+Mobility+Radeon+HD+5470)

Let's hope there is a driver in Lucid :-)

---

### Post by crypto2600 on 2010-03-15
Hey there guys. I had the exact same problem.
I got the ASUS K72JR-A1 (amazing laptop). I kept reading the forums until I realized the pattern that was fixing the issue.

There is something off about *Catalyst 10.2* and I could never get it to work. Here are the steps that fixed it (going to get into detail for new users):

[LIST]
[COLOR="Red"][*]EDIT: First **sudo update-pciids**[/COLOR]

[*]Then go and download Catalyst 10.1 from ati.com. This can be done here - [http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx)

[*]**chmod +x ati-driver-installer-10-1-x86.x86_64.run**

[*]**sudo ./ati-driver-installer-10-1-x86.x86_64.run**

[*]If you don't have jockey installed (the proprietary hardware manager) **sudo apt-get install jockey-common**.

[*]then **sudo jockey-text -l** which should list your adapter. In my case the first column said "xorg:fglrx"

[*]**sudo jockey-text -e xorg:fglrx** When you restart after this step, you will get an irritating "AMD unsupported hardware" (stupid AMD, can't see a REAL reason they even did that aside from the fact that they got crap for brains).

[*]The fix for the watermark is to create a file (e.g. "wm.sh") and paste the quoted text below:

> #!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6
}'); do
echo found $x
sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 

[*]Then **chmod +x wm.sh**

[*]Followed by **sudo ./wm.sh**

[*]Restart your box and you are good. Compiz should work at this stage. The Catalyst control center should be functional as well.
[/LIST]

**IMPORTANT: ** After you do this, and if you are using Gnome, your Ethernet (that worked perfectly before) might screw up and there is apparently a fix for it (I use KDE because it's BETTER) and I don't have the problem. If I boot into Gnome, it doesn't work. And let's hope that ATI releases proper mobility support in Catalyst 10.3 as promised. Though Sony and a few other snobby companies have opted out of having their hardware support (for what reason? no fscking clue).

Link for Ethernet fix for ubuntu was somewhere around the forum and i can't seem to find it again.

If this works for you, or there are issue, post back here and I'll get the email notification and try to help

UPDATE: You might have to run **sudo update-pciids** before you start these steps

---

### Post by zeusave on 2010-03-26
Amazing solution, thank you very much, it works flawless on Catalyst 10.3 form my Asus N61JQ.

---

### Post by crypto2600 on 2010-03-26
> **zeusave said:**
> Amazing solution, thank you very much, it works flawless on Catalyst 10.3 form my Asus N61JQ.

You are welcome. It baffles me that there is HT 5000 support for windoze in C10.3,  but for some reason the parallel Linux driver had that left out.

ATI didn't get any better with AMD buying it.

---

### Post by karatchov on 2010-03-29
this doesent seems to work with 10.3 on Ubuntu 10.04 beta
the closed source driver is loaded automatically after install, but aticonfig reports unsupported card, and compiz fails to start.

mplayer also crash when I choose opengl output ...

I'll try with 10.1 and report back

---

### Post by karatchov on 2010-03-29
Just an update:
10.3 seems in fact to fix this problem.
For ubuntu 10.04 beta users, you should install the fglrx package.
to see if everything is going ok, run the command fgrlxinfo
If you got a segmentation error, "sudo aticonfig --initial" should help

finally, if you cant find the AMD configuration control center, you can find it here:
/usr/lib/fglrx/bin/amdcccle

I got these information from various forums, they helped me, and I hope they will help you ...

---

### Post by madmaniac on 2010-03-30
Thanks!!! You are a life saver! The solution works GREAT

---

### Post by timuckun on 2010-03-31
> **karatchov said:**
> Just an update:
10.3 seems in fact to fix this problem.
For ubuntu 10.04 beta users, you should install the fglrx package.
to see if everything is going ok, run the command fgrlxinfo
If you got a segmentation error, "sudo aticonfig --initial" should help

finally, if you cant find the AMD configuration control center, you can find it here:
/usr/lib/fglrx/bin/amdcccle

I got these information from various forums, they helped me, and I hope they will help you ...


Where did you find the ati mobility radeon 5470 drivers? They only list the 4000 series under mobility section.

---

### Post by Balian on 2010-04-01
@crypto
Thank you sir you rock, I spent hours trying to get 10-2 to work after reinstalling ubuntu on my wifes acer laptop.:guitar:

> Where did you find the ati mobility radeon 5470 drivers? They only list the 4000 series under mobility section.     I followed Crypto's ATI link in his first dot point and got the 10-1 drivers they work beautifully with the mobility radeon 5470.

Edit:
I've since tried to upgrade the ATI drivers on my laptop because I wanted to use dual screens and catalyst was not working, I've got a mobility radeon 4650 so thought the 10-3 drivers would help me out, how wrong was I, catalyst still didn't work and my display was God awefully rubbish so I tried the 10-1 drivers and everything works perfectly (oh and I didn't get the annoying watermark either), I'm really starting to wonder about ATI/AMD.

---

### Post by crypto2600 on 2010-04-05
The anticipated support for mobility HD 5xxx in 10.3 never happened for Linux, though it was added for the windows drivers for some reason... I guess "**A**dvanced **T**urd **I**mplementations" is laying that over for 10.4

Either way, this doc will work with 10.3 the same exact way. You will need to patch the watermark.

---

### Post by crypto2600 on 2010-04-05
> **timuckun said:**
> Where did you find the ati mobility radeon 5470 drivers? They only list the 4000 series under mobility section.

You can't. You need to download the one listed for mobiity HD 4000 and install it. If you follow the steps exactly, it should work and you will end up with a watermark that can be patched out.

---

### Post by timuckun on 2010-04-05
> **crypto2600 said:**
> You can't. You need to download the one listed for mobiity HD 4000 and install it. If you follow the steps exactly, it should work and you will end up with a watermark that can be patched out.

I installed the open sourced drivers and they mostly work. I can't get the equivalent of "twinview" for some reason.

The worst thing about the open sourced drivers is the need to reboot your machine every time you make a change to the config and the requirement to run the config tool as root.

---

### Post by crypto2600 on 2010-04-05
> **timuckun said:**
> I installed the open sourced drivers and they mostly work. I can't get the equivalent of "twinview" for some reason.

The worst thing about the open sourced drivers is the need to reboot your machine every time you make a change to the config and the requirement to run the config tool as root.

Best support for Xinerama will be with the proprietary drivers. just install them and you'll be good to go.

---

### Post by Kocka on 2010-04-10
I use Lucid and Catalyst 10.3. It thinks my Mobility Radeon HD 5470 has 128MB of RAM instead of 1024MB. Is this just because this hardware is not supported yet?

Thanks!

---

### Post by crypto2600 on 2010-04-10
> **Kocka said:**
> I use Lucid and Catalyst 10.3. It thinks my Mobility Radeon HD 5470 has 128MB of RAM instead of 1024MB. Is this just because this hardware is not supported yet?

Thanks!

Who knows? Though i would suspect the unsupported device issue is part of it.

---

### Post by vujmar on 2010-04-12
hi! 

I have the same laptop, as crypto2600, but nothing shows up int jockey. if I open the program in administration which showed on my old laptop some unsupported hardwares, doesnt show anything either. 
Any ideas?

---

### Post by crypto2600 on 2010-04-12
> **vujmar said:**
> hi! 

I have the same laptop, as crypto2600, but nothing shows up int jockey. if I open the program in administration which showed on my old laptop some unsupported hardwares, doesnt show anything either. 
Any ideas?

This is still the case after you install 10.1 or 10.3? Try:

```
sudo update-pciids
```

---

### Post by vujmar on 2010-04-13
Thanks for the answer, I repeated a few steps, now it works correctly, but I have the same 128 mb issue as someone in a previous message :S
Anyway, my main problem was the resolution, now it's solved.
Thanks for the solution, best regards

---

### Post by hai2lp on 2010-05-01
it's is working on ubuntu karmic edition but after do some update...
but unfortunately it's not working on ubuntu 10.04 LTS version

Any idea ? please help

---

### Post by Tom Tiger on 2010-05-02
At present it works (radeon 4850)  but no compiz.... still no clue why.

---

### Post by pumax on 2010-05-02
I  would like to buy a notebook with that video card but  I'm not sure  that it works fine on linux ubuntu 10.04 or 9.10.
@hai2lp: What did you do in order to make it works on 9.10? Is 3D acceleration enabled on your system? compiz?
thank you very much!!

---

### Post by hai2lp on 2010-05-03
[@pumax]("http://ubuntuforums.org/member.php?u=1065358")
Surely it's work fine with Ubuntu 9.10 Karmic edition
Do apt-get update and upgrade first 
And exactly follow the step on crypto post  [http://ubuntuforums.org/showthread.php?t=1430357](http://ubuntuforums.org/showthread.php?t=1430357)
All visual capability are working including compiz too...

But the bad thing is after i try on Ubuntu 10.04 LTS compiz still did not work, and graphics became slower. Scrolling started  to lag too much and dragging windows is very slow

---

### Post by dkartik on 2010-05-05
So, if I was to downgrade to 9.10, and install the driver this way, would the 3D acceleration work?  Right now, I can only use basic Compiz Effects, and gaming just flat out doesn't work.

---

### Post by timuckun on 2010-05-06
> **pumax said:**
> I  would like to buy a notebook with that video card but  I'm not sure  that it works fine on linux ubuntu 10.04 or 9.10.
@hai2lp: What did you do in order to make it works on 9.10? Is 3D acceleration enabled on your system? compiz?
thank you very much!!

I would avoid this card until AMD or Ubuntu provides better drivers.

---

### Post by pumax on 2010-05-06
@dkartik: Which driver has you installed?
Is the voice value "Direct Rendering" set to "yes"?

---

### Post by dkartik on 2010-05-07
@pumax: I have installed the default driver from the lucid repository.  Looking at my xorg.conf (which I'm assuming is where I enable that option) I don't see it listed there.  I'll attach a copy of my xorg.conf below, and see if that gives you any more insight to my problem.

I apologize for my sluggishness, it's been a couple of years now since I had my own shiny machine to mess around with linux on, so my ability to know what to look for has diminished greatly.

```

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Device"
        Identifier  "Default Device"
        Driver      "fglrx"
EndSection

Section "Screen"
        Identifier "Default Screen"
        DefaultDepth     24
EndSection

```

---

### Post by pumax on 2010-05-08
I think that 3D acceleration is enabled automatically if the driver supports it!
Try to see if it is enabled in this way:
Open the Terminal and type:
glxinfo | grep direct
see the voice:
direct rendering (it may be yes or not)

Games don't work well...ok...: Have you tried flat out?
What can't you enable on compiz?
Does vga out work (external monitor)?
Other problems?

I read somewhere that people are able to run compiz without problem after driver installation from ubuntu: administration->hardware driver. 

I'not able to help you with configuration file :( i'm sorry.

---

### Post by Triple-H on 2010-05-08
Ubuntu 10.04 finally supports ATI Mobility 5470. I made a fresh install yesterday. Today, it showed me a message that I needed to activate some amd/ati drivers. I hit OK, then it installed some files and requested a reboot.

After reboot, Compiz was fully functional, and all effects work very smoothly.

Ubuntu rocks!

---

### Post by hai2lp on 2010-05-08
Are u sure Triple-H ???

Eventually after a week i'm waiting for this ,,,,

I don't know whats wrong with ubuntu 10.04 , why they not using the same  setting for this ATI 5470 coz it's work nicely on karmic 9.10 ,,,

So did u just do activate on hardware drivers ? that's it ?
No other setting or configuration ? 

Aight' then let me try

:guitar:

---

### Post by Elkimo on 2010-05-21
Hi,

I would also like to know if this card (ATI Mobility Radeon™ HD5470) is now Just Working™ with Ubuntu 10.04.

I'm considering to buy a laptop with this videocard, and since I'm quite new to Ubuntu, I really need it to work without a lot of trouble. Compiz is not 100% required, but I do want an acceptable screen resolution.

If installing the propretary drivers (the ones suggested by Ubuntu) is all I will need to do, then that would be really great.

Thanks

---

### Post by Rackstar on 2010-05-21
> **Elkimo said:**
> Hi,

I would also like to know if this card (ATI Mobility Radeon™ HD5470) is now Just Working™ with Ubuntu 10.04.

I'm considering to buy a laptop with this videocard, and since I'm quite new to Ubuntu, I really need it to work without a lot of trouble. Compiz is not 100% required, but I do want an acceptable screen resolution.

If installing the propretary drivers (the ones suggested by Ubuntu) is all I will need to do, then that would be really great.

Thanks

It worked out of the box for me. Some trouble setting up dual displays, but it worked out OK.

---

### Post by phidia on 2010-05-21
> **Rackstar said:**
> It worked out of the box for me. Some trouble setting up dual displays, but it worked out OK.

Hi, I'm interested in this gpu/video card too-with the sony vaio E-series laptops. Rackstar your profile says you are using Karmic, perhaps you just haven't updated your profile but do you have the HD 5470 working fully in 10.4 Lucid Lynx?

---

### Post by Rackstar on 2010-05-21
> **phidia said:**
> Hi, I'm interested in this gpu/video card too-with the sony vaio E-series laptops. Rackstar your profile says you are using Karmic, perhaps you just haven't updated your profile but do you have the HD 5470 working fully in 10.4 Lucid Lynx?

Yes, I'm using Lucid, never tried it on Karmic, but I read that it doesn't work with Karmic.

Today I fixed the switching between displays, and I'm really happy with the result. It's my first ATI graphics chip on Ubuntu, and I'm very very pleased.

---

### Post by Elkimo on 2010-05-21
Ok, thank you so much for your help, just to be clear, you just did a normal install of 10.04 (32 or 64 bit?), and you didn't alter anything manually (like an xorg file or something like that)?

---

### Post by Rackstar on 2010-05-21
I just did a clean install of Ubuntu 10.04, activated the restricted driver. I only needed a fix to get the shortcut running to automatically switch displays, but I think this is a Dell issue.

---

### Post by Northern Mike on 2010-05-23
I just loaded a Dell 1558 core i7, 5470 card, activated ATI driver that popped up in restricted hardware drivers, black screen at boot up and it hangs there.

---

### Post by Northern Mike on 2010-05-23
Can't edit my above post, Solved.  Tried rebooting a couple times, loaded second try.   Icons on the panel were wrong, no power button etc.   Removed driver, rebooted, reinstalled driver, rebooted, success.  Urban terror looks good.

---

### Post by Elkimo on 2010-05-25
A little off-topic:

would that Dell laptop you've bought happen to be this one (Dutch link): 
[http://configure2.euro.dell.com/dellstore/config.aspx?b=&c=nl&cs=nldhs1&kc=HDP&l=nl&m_30=321942&oc=N0055802&rbc=N0055802&s=dhs]("http://configure2.euro.dell.com/dellstore/config.aspx?b=&c=nl&cs=nldhs1&kc=HDP&l=nl&m_30=321942&oc=N0055802&rbc=N0055802&s=dhs")

because that's the one I'm looking at. If it is, would you recommend it to me? Does everything else work correctly out of the box?

On-topic:

So you've installed the propretary driver that was suggested by Ubuntu, you got a blank screen, deleted the driver, rebooted and reinstalled the same driver (from that driver-application in "system" - "administration"?), and then it worked? Or did you download a different driver?

---

### Post by timpaton on 2010-06-14
> **Northern Mike said:**
> Can't edit my above post, Solved.  Tried rebooting a couple times, loaded second try.

No such luck here.

I'm installing on a MSI A6205 (i5, ATI HD5470). Rebooting with the fglrx driver enabled gives me a blank screen.

The system is still working in the background - it shuts down cleanly with a ctrl-alt-del - but I can't do anything because I can't see :-(

Multiple reboots and it's still doing the same.

Any ideas of how I can fix it?

tim

---

### Post by Wistful on 2010-06-14
> **timpaton said:**
> No such luck here.

Try booting in the recovery mode an run the following commands (try the first one then restart if it works, good, no need to run the second one! if not try the second one, restart, if still not working, read the links provided as *this*):
> sudo dpkg-reconfigure xserver-xorg or > dpkg-reconfigure -phigh xserver-xorg

Some additional information can be found [here]("http://ubuntuforums.org/showthread.php?t=690760")

READTHIS-> [this]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html") and [this]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/") or [this]("http://linux.dipin.info/2010/05/fix-ubuntu-1004-lucid-lynx-black-screen.html") maybe it will solve the problem. 

From my personal experience what I can tell is that I have this graphics card and I'm using the ATI proprietary drivers, but I don't have any problem whatsoever using it on a Acer Aspire 5741G

---

### Post by coliv_aja on 2010-06-14
Hi i'm new on Linux.
i bought ASUS A42JR i5 ATI HD 5470 ...
I'm download ati catalyst 10.5 for linux from [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx"), on release note its support series 5400(include 5470). see ss

[IMG]http://web19.twitpic.com/img/115596251-2704c03b877aebc0e92eec5691521bb4.4c168a40-scaled.jpg[/IMG]

succesfully install this ati catalyst, on catalyst control center its detected, but ubuntu vga still no driver.
and windows effect disable, its mean driver not succesfully installed ?

i have message on windows effect about x configuration.
what the "x configuration" ?
i'm use KDE

sorry i'm fresh on linux.

---

### Post by Elkimo on 2010-06-18
Coliv, is there a particular reason why you manually downloaded the driver? 

If you go to 'system' 'administration' 'drivers', Ubuntu should automatically suggest the drivers for the HD5470, and when you hit 'activate' the driver should be automatically downloaded, installed and configured for you. This way, there is little you can do wrong, if you manually install the driver, the odds you accidentally mess something up are greater.

For the record, I have an H5470 too, and I have no problems at all with it. I installed the drivers using the method described above.

---

### Post by timuckun on 2010-06-18
> **Elkimo said:**
> Coliv, is there a particular reason why you manually downloaded the driver? 


For the record, I have an H5470 too, and I have no problems at all with it. I installed the drivers using the method described above.

Does that driver update itself automatically and is there a way to check the version of it?

I notice that the ATI site has a driver date of 6/16/10 and so it's very new. I hope ubuntu updates their drivers because I have been having some problems with my mobility radeon 5470.  I would also like a decent way to display two different resolutions on two different monitors and be able to move windows from one to the other.

---

### Post by Elkimo on 2010-06-18
I'm not 100% sure about it, but I don't think those drivers are updated, since drivers are a very essential part of your operating system, and they (ubuntu) don't want to risk regressions by updating them. The latest drivers will probably only be added to the next version of Ubuntu.

The version of you driver you can check by going to 'system' 'preferences' 'ATI Catalyst Control Center', and then go to the section 'information'.

About dualscreens, I personally haven't had much luck with setting mine up, but I'm hardly an expert. I'm relatively new to Ubuntu myself, so I can't really help you with that.

---

### Post by timuckun on 2010-06-18
> **Elkimo said:**
> 
The version of you driver you can check by going to 'system' 'preferences' 'ATI Catalyst Control Center', and then go to the section 'information'.



I don't think they use the same versioning standard. The ATI web site says they are at 10.6. ATI catalyst I have says 8.73.

That's very far  behind considering this is lucid.

---

### Post by coliv_aja on 2010-06-18
> **Elkimo said:**
> Coliv, is there a particular reason why you manually downloaded the driver? 

If you go to 'system' 'administration' 'drivers', Ubuntu should automatically suggest the drivers for the HD5470, and when you hit 'activate' the driver should be automatically downloaded, installed and configured for you. This way, there is little you can do wrong, if you manually install the driver, the odds you accidentally mess something up are greater.

For the record, I have an H5470 too, and I have no problems at all with it. I installed the drivers using the method described above.

First, i'm installed Kubuntu, there's not available hardware administration like ubuntu(gnome). so i don't know what can i do to get driver, so i'm going to ati web and i get that's driver latest ati catalyst with support hd 5470, so i'm installed that.
and so far so good its not problem with this, its propriethy driver right?, and its like ubuntu do, ubuntu automatically install pr0priethy driver, but wrong version of will you get,.
if you install driver automatically you get HD 5000 version riht ?
but i have been installed the latest ati catalyst, its hd 5400, maybe some feature will not work, because basically that ubuntu automatically install propriethy driver not yet supported hd 5470, maybe next ubuntu version have the new driver. i think maybe ubuntu developer throught hd 5000 have similar hardware with 5470.

conclusions, ubuntu hardware administration do same propriethy driver from ati also. just different version,
and so far so good, no problemo :guitar:

---

### Post by coliv_aja on 2010-06-18
> **timuckun said:**
> I don't think they use the same versioning standard. The ATI web site says they are at 10.6. ATI catalyst I have says 8.73.

That's very far  behind considering this is lucid.

no, its different ati catalyst version with driver version. ati catalyst version just version of ati driver suite, not different what version tou have, there same driver for certain driver.
new version of ati catalyst just added new product of them. so inside ati catalyst have same driver of certain product.

---

### Post by coliv_aja on 2010-06-18
hey any body have asus a42jr like me, i cant't hear sound with output jack,
i'm just can used internal speaker. its bad, couse my internal speaker not good.
what can i do for fix its,
please help me.

---

### Post by Yellow Pasque on 2010-06-18
> **timuckun said:**
> I don't think they use the same versioning standard. The ATI web site says they are at 10.6. ATI catalyst I have says 8.73.

That's very far  behind considering this is lucid.
Catalyst 10-6 = 8.741

---

### Post by drlinux on 2010-07-25
> **timpaton said:**
> No such luck here.

I'm installing on a MSI A6205 (i5, ATI HD5470). Rebooting with the fglrx driver enabled gives me a blank screen.



tim

Have you got this all sorted or are there ongoing issues? I have just bought an MSI A6205 and was about to install Ubuntu 10.04 onto it.

---

### Post by timpaton on 2010-07-31
> **drlinux said:**
> Have you got this all sorted or are there ongoing issues? I have just bought an MSI A6205 and was about to install Ubuntu 10.04 onto it.

Honestly, I can't remember this problem :oops:

I'm currently running Linux Mint (a modified Ubuntu) on this MSI, and - well, it works. Not sure what graphics drivers I'm running (or how much of the GPU's capabilities are enabled) - I'm a long-term noob and don't do much graphics-intensive stuff.

tim

---

### Post by timpaton on 2010-08-02
Now you've reminded me... yeah, it still doesn't work. I've been using the generic drivers, because the ATI ones don't work.

One thing that might help you find a solution (I've just started searching) is that our A6205 seems to be branded as a CX620 in other markets... and there are lots of people finding this same problem with their CX620.

So far the best lead I've found is somebody saying "it's a really simple fix, I've already posted it in another thread, use the search function" (and the search function on that forum hasn't found me anything yet, except for the same thread...).

Good luck... now I'm back on the search, I'll post here if I find a solution.

tim

---

### Post by Mitch87 on 2010-08-02
hi
im running Ubuntu 10.04 on the Aspire 5738G with uses the ATI RADEON HD 4570.
compiz and all the 3D graphics works well if your using the new 10.7 ATI driver. as long as you use the admin catalyst and tweak the 3D graphics. 4

the only problem i am having now is the colour. for some reason the ATI driver will only set the colours to 16-bit... but i want to run a program that requires 32-bit colour. so if anyone has any ideas as to how to fix this.. please.. let me know.

---

### Post by Engine_number_9 on 2010-09-06
I've bought a new laptop with a radeon HD 5470 card and installed Ubuntu 10.04 alongside Windows 7. The installation went fine until I installed the restricted driver with the restricted drivers manager.
After installing the restricted driver the screen goes black after Grub. When I press the power button in order to close down the system the shut down screen appears.

Does anyone know what's wrong and can anyone get the HD 5470 working in 10.04?

---

### Post by Yellow Pasque on 2010-09-06
> **Engine_number_9 said:**
> I've bought a new laptop with a radeon HD 5470 card and installed Ubuntu 10.04 alongside Windows 7. The installation went fine until I installed the restricted driver with the restricted drivers manager.
After installing the restricted driver the screen goes black after Grub. When I press the power button in order to close down the system the shut down screen appears.

Does anyone know what's wrong and can anyone get the HD 5470 working in 10.04?
Boot to recovery mode and remove the driver:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Now install the driver from AMD's website using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

---

### Post by Engine_number_9 on 2010-09-07
> **Temüjin said:**
> Boot to recovery mode and remove the driver:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```
Now install the driver from AMD's website using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_the_drivers_manually)

Thanks for the reply. I've made a reinstall and tried to install the drivers manually following the guide in the link. This does not solve the problem. After installing the driver the screen goes black upon booting, and remains black until I press the power button and the shut down screen is showed.

Any suggestions?

---

### Post by timuckun on 2010-09-13
> **Engine_number_9 said:**
> Thanks for the reply. I've made a reinstall and tried to install the drivers manually following the guide in the link. This does not solve the problem. After installing the driver the screen goes black upon booting, and remains black until I press the power button and the shut down screen is showed.

Any suggestions?

The instructions on the page you linked to do not work for building the packages.

You get the following error.

dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib/libQtGui.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libfglrx_gamma.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/fglrx_xgamma debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.FVOYW7'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.ZGX0kK


A quick googling shows many people reporting this error but no answer that I could find.

after running the installer manually everything seems to be OK except the information panel says it's running catalyst 10.6 and not 10.8.

Is there another way to tell what version you are running?

---

### Post by Wistful on 2010-09-28
The latest version of the ATI proprietary drivers may NOT work with Ubuntu 10.04 LTS use the version provided in repositories.

---

### Post by mikekola on 2010-10-08
Any news regarding HD 5470 chipset?
Hope we can expect some new info once 10.10 is out there.

I'm planning to get one of Asus' laptops soon and would really like to see it working out of the box with 10.10

According to the info on [www.ati.com](www.ati.com) , the latest 10.9 version of drivers does support the whole 5400 series.

I'd appreciate some new information from those of you who have it working already and some new reports of 10.10 compatibility.

Thanks
Michael

---

### Post by om~namas~ganga on 2010-10-29
Hello guys, I am new to this thread but not new on this ATI nightmare... 

I am happy to announce that ATI released 10.10 driver: 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)

Please let me know hot it works for you, I am trying it just after writing this lines...

---

### Post by tech-hero on 2010-11-15
> **om~namas~ganga said:**
> Hello guys, I am new to this thread but not new on this ATI nightmare... 
 
I am happy to announce that ATI released 10.10 driver: 
 
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)
 
Please let me know hot it works for you, I am trying it just after writing this lines...
 
 
I also wanna know if HD4750 is now working with the new driver. im just new with ubuntu, and i wanna know its full capabilities!

---

### Post by xycris on 2010-11-15
> **om~namas~ganga said:**
> Hello guys, I am new to this thread but not new on this ATI nightmare... 

I am happy to announce that ATI released 10.10 driver: 

[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English)

Please let me know hot it works for you, I am trying it just after writing this lines...

hi om~namas~ganga, have you tried this new catalyst version on a 10.10 maverick meerkat? hope you can post your feedback so i can now move on from my 9.10 system.

thanks in advance!

---

### Post by pol90 on 2010-11-19
> **xycris said:**
> hi om~namas~ganga, have you tried this new catalyst version on a 10.10 maverick meerkat? hope you can post your feedback so i can now move on from my 9.10 system.

thanks in advance!
I've been trying to get them working on ubuntu 10.10 and I'm getting a black screen after boot too. They work flawlessly on fxxking windows...

---

### Post by ravemjr on 2010-11-25
I just bought my laptop today, and installed 10.10 on it, but it seems that both the restricted drivers and the ones from the ati website crash my X server.

Any idea as to what to do in order to get them to work?

---

### Post by tech-hero on 2010-11-29
> **ravemjr said:**
> I just bought my laptop today, and installed 10.10 on it, but it seems that both the restricted drivers and the ones from the ati website crash my X server.

Any idea as to what to do in order to get them to work?

i've got mine working. installed from the third party driver.

it installed the ATI catalyst. so far no problem encountered.im using UBUNTU 10.04 LTS.

---

### Post by avary on 2010-11-30
hello, 

i was running kubuntu 10.04 with open source drivers, i did upgrade to 10.10 and installed ATI drivers (ATI Catalyst&#8482; 10.11 Proprietary Linux x86 Display Driver) .. now it is working except when change smplayer to full screen it is very laggy. also with firefox, scrolling is no smooth . 
im thinking reverting back to opensource drivers at 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

anyone got smiliar problem ? how to fix it ?

---

### Post by icegood on 2010-11-30
So, what drivers all of you use for ati?
For my case ubunu x64 10.11 driver sucks :(

---

### Post by icegood on 2010-11-30
I mean, we need voting

---

### Post by Fixman on 2010-12-13
Thanks.

---

### Post by marcello950 on 2010-12-19
hi there..i would like some advice from someone who tried the ati radeon hd5470..my notebook is asus x52j series,i3 250m,4gb ram,ubuntu 10.10 and obviously hd radeon 5470.
so my question was..:)
how can i get the grafic card to work on ubuntu like it does on windows 7?
it's not the same guys,ubuntu 10.10 is wonderful but it seems it doesnt reach windows performance about the grafic card,
can someone tell me his experience?
thank you guys

---

### Post by zbluebird on 2010-12-28
hello,

im using an acer aspire 4745g with ATI mobility radeon hd 5470.

had the same problem when I installed the "ATI/AMD proprietary FGLRX graphics driver"... gnome interface just doesn't load at all when system is restarted and will user will be stuck in the command line.

Any advice on how to make the graphics card work?

Thanks.

---

### Post by riyasmp on 2011-01-05
hi guys

I recently baught a hp dv-6 3150sa laptop which uses ATI mobilty readon HD 5470 graphics9switchable with intel HD GMA). after partitioning i could install ubuntu 10.10 without any problems. 

on first restart ubuntu recomnded ATM/AMD proprietary FGLRX graphics driver which i installed straight away. on my next reboot it showed grub and while on choosing ubuntu it went to the command mode. I had to reinstall ubuntu to get back the genome desktop.

i havent installed that driver again but my compiz is working. but i can see that computer is heating up quiet a lot compared to windows.

guys can any one help me telling, have i got the right graphics driver now? or do i have to try re installing the fglrx thing once again.

tx

---

### Post by ansary on 2011-01-08
[SIZE=4]im using ubuntu 10.10 and installed the ATI driver, but when i rebooted my laptap, the gnome desktop disappeared..




[/SIZE]

---

### Post by riyasmp on 2011-01-08
> **ansary said:**
> [SIZE=4]im using ubuntu 10.10 and installed the ATI driver, but when i rebooted my laptap, the gnome desktop disappeared..




[/SIZE]y


hi i had the same problem. I don know if you have a hybrid graphics one. I did a search on this issue and i cannot find a fix on this one so far. I installed a Uubuntu contro centre and switcheroo programes. the switcheroo is switching the cards manually. but it ssems ATI hasnt got right driver. when u install fglrx straight away what happens is on reboot fglrx takes control which is pointed to intel chip (the low power one) by default. and then blank screen.


correct me if i am wrong.

what all i need is the ATI to work on ubuntu i don mind about switching the cards at the moment i can wait

---

### Post by riyasmp on 2011-01-08
> **crypto2600 said:**
> Hey there guys. I had the exact same problem.
I got the ASUS K72JR-A1 (amazing laptop). I kept reading the forums until I realized the pattern that was fixing the issue.

There is something off about *Catalyst 10.2* and I could never get it to work. Here are the steps that fixed it (going to get into detail for new users):

[LIST]
[COLOR="Red"][*]EDIT: First **sudo update-pciids**[/COLOR]

[*]Then go and download Catalyst 10.1 from ati.com. This can be done here - [http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx)

[*]**chmod +x ati-driver-installer-10-1-x86.x86_64.run**

[*]**sudo ./ati-driver-installer-10-1-x86.x86_64.run**

[*]If you don't have jockey installed (the proprietary hardware manager) **sudo apt-get install jockey-common**.

[*]then **sudo jockey-text -l** which should list your adapter. In my case the first column said "xorg:fglrx"

[*]**sudo jockey-text -e xorg:fglrx** When you restart after this step, you will get an irritating "AMD unsupported hardware" (stupid AMD, can't see a REAL reason they even did that aside from the fact that they got crap for brains).

[*]The fix for the watermark is to create a file (e.g. "wm.sh") and paste the quoted text below:



[*]Then **chmod +x wm.sh**

[*]Followed by **sudo ./wm.sh**

[*]Restart your box and you are good. Compiz should work at this stage. The Catalyst control center should be functional as well.
[/LIST]

**IMPORTANT: ** After you do this, and if you are using Gnome, your Ethernet (that worked perfectly before) might screw up and there is apparently a fix for it (I use KDE because it's BETTER) and I don't have the problem. If I boot into Gnome, it doesn't work. And let's hope that ATI releases proper mobility support in Catalyst 10.3 as promised. Though Sony and a few other snobby companies have opted out of having their hardware support (for what reason? no fscking clue).

Link for Ethernet fix for ubuntu was somewhere around the forum and i can't seem to find it again.

If this works for you, or there are issue, post back here and I'll get the email notification and try to help

UPDATE: You might have to run **sudo update-pciids** before you start these steps

I know this is a quiet old post. still giving a try if any one can give me a helping hand. i am using hp dv6 3150sa with ATI radeon HD 5470 graphics switchable with intel HD GMA. i tried installing the catalyst 10.12 from the site. on giving the last command

ri@oc:~$ sudo jockey-text -e xorg:fglrx
[sudo] password for ri

Searching for available drivers...

SystemError: installArchives() failed

 I m using ubuntu 10.10 64bit.

i doublecheked vga swinitching under UCC. when i switch to high perfomance the compiz is disabled and ATI card is not specified. when i switch back to low perfomance intel is dsplayed and compiz is back.

any help would be appreciated

regards

---

### Post by crunkyboy on 2011-01-17
Greetings guys, I have been using Ubuntu for quite a long time and 2 years ago I migrated to Arch and was using it as my primary distro. Recently I bought a new notebook (HP g62 with hybrid graphics Intel and ATi mobility Radeon HD 5470) and have serious issues to get this lappy working on Arch. I've pissed my self for real with this and installed Ubuntu 10.10 to see if I can use it on my brand new lap (cause I just simply hate M*C**S*FT crap). Everything went fine with the installation, I did manage to enable vga_switcheroo but once I installed the proprietary ATi drivers I can't seem too boot my Ubuntu anymore.

Should I use some opensource drivers like xf86-video-ati or something? 

Please, if someone can help me on this so I can get my brand new lappy working on GNU/Linux ...

Thanks.

---

### Post by Yellow Pasque on 2011-01-17
> **crunkyboy said:**
> Greetings guys, I have been using Ubuntu for quite a long time and 2 years ago I migrated to Arch and was using it as my primary distro. Recently I bought a new notebook (HP g62 with hybrid graphics Intel and ATi mobility Radeon HD 5470) and have serious issues to get this lappy working on Arch. I've pissed my self for real with this and installed Ubuntu 10.10 to see if I can use it on my brand new lap (cause I just simply hate M*C**S*FT crap). Everything went fine with the installation, I did manage to enable vga_switcheroo but once I installed the proprietary ATi drivers I can't seem too boot my Ubuntu anymore.

Should I use some opensource drivers like xf86-video-ati or something? 

Please, if someone can help me on this so I can get my brand new lappy working on GNU/Linux ...

Thanks.
Either revert to open-source drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
or disable the Intel IGP if your BIOS has such an option.

---

### Post by crunkyboy on 2011-01-17
> **Temüjin said:**
> Either revert to open-source drivers: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)
or disable the Intel IGP if your BIOS has such an option.

Thanks man, I`ll try that as soon as I get home (less than 2 hours). The BIOS does not have any option regarding graphics and HP don't give a f**k about launching an updated ver. of the BIOS. THe latest available poweroff's my screen leds. Anyhow, I hope the open source drivers will work so I can use linux OS on my brand new notebook. 

Another issue that I`m sure it will not work either are the Fn keys, but I can workaround that, just hope that I can poweroff the Ati card so my battery life will be satisfying.

Respect

---

### Post by Yellow Pasque on 2011-01-17
Good luck. [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

---

### Post by drazgo on 2011-01-24
So there is actually no solution for installing Catalyst on ubuntu 10.10 at the moment? Am I right?

---

### Post by Yellow Pasque on 2011-01-24
> **drazgo said:**
> So there is actually no solution for installing Catalyst on ubuntu 10.10 at the moment? Am I right?
The install guide is here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
Catalyst doesn't work with hybrid/switchable graphics though.

---

### Post by drazgo on 2011-01-24
> **Temüjin said:**
> The install guide is here: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)
Catalyst doesn't work with hybrid/switchable graphics though.

Oh like that, guess that'll be my problem. Any chance of knowing when it'll support switcheable graphics?

---

### Post by Yellow Pasque on 2011-01-24
> **drazgo said:**
> Oh like that, guess that'll be my problem. Any chance of knowing when it'll support switcheable graphics?
AFAIK, ATI has no plans to support it under Linux .

---

### Post by drazgo on 2011-01-25
> **Temüjin said:**
> AFAIK, ATI has no plans to support it under Linux .

What a shame! Thanks anyway mate.

---

### Post by SillyDragon on 2011-01-25
Hello, I'm new to Ubuntu and could use some help.
If I am running Ubuntu in VMware Player 3 as a Virtual Machine can I still get the driver to work?
I have an HD5770 and have gone through most of the guide on how to install the driver but instead of it listing xorg:fglrx, it states this: kmod:vmci - VMware Virtual Machine Communication Interface (Free, Enabled, In use)
Any information would be useful, 
Thanks

Edit: Nevermind, I found out through a forum that VMware doesn't support Visual Effects, therefore none of this will work from my understanding.

---

### Post by timuckun on 2011-02-03
Hey All.

Something very strange happened to me and I am hoping somebody can help me with getting my laptop back in order.

I have a Asus K42jr with a ATI Mobility Radeon 5470 on it. I had the proprietary drivers running on it.

Today I used it like normal and when I got home and plugged it into my second monitor X didn't come up.  I just got a blank screen with nothing on it.  I tried several times and nothing. 

I booted it up safe graphics mode and went to the ATI site and used the instructions on the wiki there to install the latest drivers. The drivers did not install for some reason.

I used to instructions there to purge all the ATI drivers and to re-install the default drivers and was able to get my system back up but.....


There is a purple line on the left edge of my external monitor and the font rendering seems fuzzier. I did not have these problems with the proprietary driver.

I tried installing the proprietary driver again but the app does not give me an option to enable them. The screen for the additional drivers app is blank.

Compiz does not work.

fglrx is not installed and I am afraid to install it at this point.

I booted into windows on this laptop and everything seems to be working fine, it reports no problems at all so I am pretty sure the hardware is working OK.

Any clues would be much appreciated.

I installed fglrx and then enabled the propritary drivers and it came back up without the line and with better font rendering.

I still have no clue what happened and why it would not boot up before.

---

### Post by locer on 2011-02-26
Hello. I have the same laptop as the author of the post, can not put a driver on the same video card, my OS kernel 2.6.35.25.
 Just pop up error when entering the command to start the driver:
[http://i1.fastpic.ru/big/2011/0226/8f/6415518c27ec183ec9bb86e5e0ee958f.png](http://i1.fastpic.ru/big/2011/0226/8f/6415518c27ec183ec9bb86e5e0ee958f.png)
 Here's a link to the picture.
 Sorry for the English language, worked as an interpreter because I am Russian by nationality.

---

### Post by m3kkaton on 2011-03-18
> **crypto2600 said:**
> Hey there guys. I had the exact same problem.
I got the ASUS K72JR-A1 (amazing laptop). I kept reading the forums until I realized the pattern that was fixing the issue.

There is something off about *Catalyst 10.2* and I could never get it to work. Here are the steps that fixed it (going to get into detail for new users):

[LIST]
[*][COLOR=Red][/COLOR][COLOR=Red]
[*]EDIT: First **sudo update-pciids**[/COLOR]
[*]Then go and download Catalyst 10.1 from ati.com. This can be done here - [http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/10-1/Pages/radeon_linux.aspx)
[*]**chmod +x ati-driver-installer-10-1-x86.x86_64.run**
[*]**sudo ./ati-driver-installer-10-1-x86.x86_64.run**
[*]If you don't have jockey installed (the proprietary hardware manager) **sudo apt-get install jockey-common**.
[*]then **sudo jockey-text -l** which should list your adapter. In my case the first column said "xorg:fglrx"
[*]**sudo jockey-text -e xorg:fglrx** When you restart after this step, you will get an irritating "AMD unsupported hardware" (stupid AMD, can't see a REAL reason they even did that aside from the fact that they got crap for brains).
[*]The fix for the watermark is to create a file (e.g. "wm.sh") and paste the quoted text below:
[*]Then **chmod +x wm.sh**
[*]Followed by **sudo ./wm.sh**
[*]Restart your box and you are good. Compiz should work at this stage. The Catalyst control center should be functional as well.
[/LIST]

**IMPORTANT: ** After you do this, and if you are using Gnome, your Ethernet (that worked perfectly before) might screw up and there is apparently a fix for it (I use KDE because it's BETTER) and I don't have the problem. If I boot into Gnome, it doesn't work. And let's hope that ATI releases proper mobility support in Catalyst 10.3 as promised. Though Sony and a few other snobby companies have opted out of having their hardware support (for what reason? no fscking clue).

Link for Ethernet fix for ubuntu was somewhere around the forum and i can't seem to find it again.

If this works for you, or there are issue, post back here and I'll get the email notification and try to help

UPDATE: You might have to run **sudo update-pciids** before you start these steps

Hi guys!

Trying to follow these steps an error seem to do not allow the command added at the terminal ([COLOR=Blue]**sudo jockey-text -e xorg:fglrx**[/COLOR]) continue with the following step.

I'm a very beginner Ubuntu user and I'm trying to activate compiz effects.
I'm running Ubuntu 10.04 x64 in an ASUS x52dr laptop.
CPU: AMD Athlon II x2 P320 x 2.1 Ghz
Graphics: ATI Mobility Radeon HD 5470 1GB
Memory: 3GB

The terminal shows:
*"Lo sentimos, la instalación de este controlador falló."*
"We are sorry, the instalation of this controlator failed."

"Revise el archivo de registro para ver más detalles: /var/log/jockey.log"
"Check the registry file to see more details: /var/log/jockey.log"

The jockey.log is the following:
```


2011-03-18 13:21:18,640 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0>
2011-03-18 13:21:18,642 DEBUG: reading modalias file /lib/modules/2.6.32-29-generic/modules.alias
2011-03-18 13:21:18,759 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2011-03-18 13:21:18,760 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-03-18 13:21:18,798 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2011-03-18 13:21:18,799 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2011-03-18 13:21:18,802 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2011-03-18 13:21:18,804 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2011-03-18 13:21:18,807 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-03-18 13:21:19,071 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-03-18 13:21:19,076 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2011-03-18 13:21:19,090 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2011-03-18 13:21:19,091 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2011-03-18 13:21:19,092 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2011-03-18 13:21:19,101 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2011-03-18 13:21:19,103 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2011-03-18 13:21:19,103 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2011-03-18 13:21:19,104 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2011-03-18 13:21:19,116 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-18 13:21:19,118 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2011-03-18 13:21:19,135 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2011-03-18 13:21:19,136 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2011-03-18 13:21:19,162 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2011-03-18 13:21:19,164 DEBUG: Firmware for DVB cards not available
2011-03-18 13:21:19,164 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2011-03-18 13:21:19,179 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2011-03-18 13:21:19,180 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2011-03-18 13:21:19,197 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-18 13:21:19,205 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2011-03-18 13:21:19,207 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2011-03-18 13:21:19,224 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-18 13:21:19,225 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2011-03-18 13:21:19,234 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2011-03-18 13:21:19,236 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2011-03-18 13:21:19,252 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2011-03-18 13:21:19,253 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2011-03-18 13:21:19,280 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2011-03-18 13:21:19,281 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2011-03-18 13:21:19,292 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2011-03-18 13:21:19,293 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2011-03-18 13:21:19,293 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2011-03-18 13:21:19,313 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2011-03-18 13:21:19,334 DEBUG: Software modem not available
2011-03-18 13:21:19,335 DEBUG: all custom handlers loaded
2011-03-18 13:21:19,335 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-18 13:21:19,336 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-18 13:21:19,462 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-18 13:21:19,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-18 13:21:19,463 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d0000AA68sv00001043sd00001BF2bc04sc03i00')
2011-03-18 13:21:19,766 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,766 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'platform:asus_laptop')
2011-03-18 13:21:19,767 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000197Bd00000250sv00001043sd00001905bc02sc00i00')
2011-03-18 13:21:19,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jme', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,770 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k71,72,73,8C,94,96,98,A3,A4,A5,A6,A9,D4,D7,E2,E3,E5,E6,EC,EE,14A,174,ramlsfw')
2011-03-18 13:21:19,770 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-18 13:21:19,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'platform:regulatory')
2011-03-18 13:21:19,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-18 13:21:19,771 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd00001BF2bc06sc00i00')
2011-03-18 13:21:19,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000197Bd00002384sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:19,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:ETD0001:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-03-18 13:21:19,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-18 13:21:19,786 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d000068E0sv00001043sd00001BF2bc03sc00i00')
2011-03-18 13:21:19,794 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-18 13:21:19,925 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-18 13:21:19,797 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver)
2011-03-18 13:21:19,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'vga16fb', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000197Bd00002383sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:19,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'jmb38x_ms', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,926 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-18 13:21:19,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:19,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000011B3bc04sc03i00')
2011-03-18 13:21:19,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,932 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,932 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:19,933 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'usb:v13D3p5130d1211dcEFdsc02dp01ic0Eisc02ip00')
2011-03-18 13:21:19,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2011-03-18 13:21:19,963 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,963 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0003v13D3p5130e1211-e0,1,kD4,ramlsfw')
2011-03-18 13:21:19,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-03-18 13:21:19,964 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-18 13:21:19,964 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-03-18 13:21:19,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_piix4', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-03-18 13:21:19,968 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-18 13:21:19,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrK52Dr.211:bd08/18/2010:svnASUSTeKComputerInc.:pnK52Dr:pvr1.0:rvnASUSTeKComputerInc.:rnK52Dr:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2011-03-18 13:21:19,982 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:19,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-18 13:21:19,983 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00001313bc06sc01i00')
2011-03-18 13:21:19,986 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-18 13:21:19,987 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-18 13:21:19,987 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-18 13:21:19,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:19,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000197Bd00002382sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:19,988 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,988 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:19,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'amd64_edac_mod', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-03-18 13:21:19,989 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:19,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-03-18 13:21:19,989 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2011-03-18 13:21:20,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ath9k', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-18 13:21:20,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-18 13:21:20,001 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-18 13:21:20,001 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'usb:v13D3p5130d1211dcEFdsc02dp01ic0Eisc01ip00')
2011-03-18 13:21:20,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'uvcvideo', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,002 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'platform:pcspkr')
2011-03-18 13:21:20,002 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,003 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,003 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-03-18 13:21:20,006 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v0000197Bd00002381sv00001043sd00001A07bc08sc05i01')
2011-03-18 13:21:20,007 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,007 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sdhci_pci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,007 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00001313bc0Csc03i20')
2011-03-18 13:21:20,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-18 13:21:20,020 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'input:b0011v0002p0005e0063-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-03-18 13:21:20,021 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,021 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'pci:v00001002d00004391sv00001043sd00001313bc01sc06i01')
2011-03-18 13:21:20,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,025 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ahci', 'jockey_handler': 'KernelModuleHandler'}
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x1ffdcb0> about HardwareID('modalias', 'acpi:device:')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0B00:')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0C01:')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d0000AA68sv00001043sd00001BF2bc04sc03i00')
2011-03-18 13:21:20,025 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'platform:asus_laptop')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000197Bd00000250sv00001043sd00001905bc02sc00i00')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k71,72,73,8C,94,96,98,A3,A4,A5,A6,A9,D4,D7,E2,E3,E5,E6,EC,EE,14A,174,ramlsfw')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0800:')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'platform:regulatory')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00009601sv00001043sd00001BF2bc06sc00i00')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000197Bd00002384sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:ETD0001:SYN0A00:SYN0002:PNP0F03:PNP0F13:PNP0F12:')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0C02:')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d000068E0sv00001043sd00001BF2bc03sc00i00')
2011-03-18 13:21:20,026 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000197Bd00002383sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0C04:')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00001200sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d00004383sv00001043sd000011B3bc04sc03i00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00001203sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'usb:v13D3p5130d1211dcEFdsc02dp01ic0Eisc02ip00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0001v10ECp0269e0001-e0,12,kramls1,2,fw')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0003v13D3p5130e1211-e0,1,kD4,ramlsfw')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d00004385sv00000000sd00000000bc0Csc05i00')
2011-03-18 13:21:20,027 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:LNXTHERM:')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'dmi:bvnAmericanMegatrendsInc.:bvrK52Dr.211:bd08/18/2010:svnASUSTeKComputerInc.:pnK52Dr:pvr1.0:rvnASUSTeKComputerInc.:rnK52Dr:rvr1.0:cvnASUSTeKComputerInc.:ct10:cvr1.0:')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00001201sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0000:')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d0000439Dsv00001043sd00001313bc06sc01i00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00001204sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000197Bd00002382sv00001043sd00001A07bc08sc80i00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001022d00001202sv00000000sd00000000bc06sc00i00')
2011-03-18 13:21:20,028 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000168Cd0000002Bsv00001A3Bsd00001089bc02sc80i00')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0200:')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:PNP0100:')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'usb:v13D3p5130d1211dcEFdsc02dp01ic0Eisc01ip00')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'platform:pcspkr')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d00004384sv00000000sd00000000bc06sc04i01')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v0000197Bd00002381sv00001043sd00001A07bc08sc05i01')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d00004396sv00001043sd00001313bc0Csc03i20')
2011-03-18 13:21:20,029 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2011-03-18 13:21:20,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'input:b0011v0002p0005e0063-e0,1,2,k110,111,112,r0,1,8,amlsfw')
2011-03-18 13:21:20,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'pci:v00001002d00004391sv00001043sd00001313bc01sc06i01')
2011-03-18 13:21:20,030 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x2707098> about HardwareID('modalias', 'acpi:device:')
2011-03-18 13:21:20,156 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-18 13:21:20,407 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2011-03-18 13:21:20,409 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2011-03-18 13:21:20,409 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2011-03-18 13:21:30,057 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2011-03-18 13:21:30,185 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches


```Could you please help me?:confused:
Thanks in advance! From Argentina.):P

---

### Post by Yellow Pasque on 2011-03-18
Do not use those instructions. Build packages the proper way: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide)

---

### Post by puregutsxc on 2011-03-19
Hi, I did what crypto2600 said to do to get my graphics working, and now it says my package system is broken. I ran the synaptic package pair thing and it gave me this.

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

can anyone help? I'm kinda new to ubuntu and dont really know what to do.

---

### Post by Yellow Pasque on 2011-03-20
> **puregutsxc said:**
> E: Sub-process /usr/bin/dpkg returned an error code (1) can anyone help? I'm kinda new to ubuntu and dont really know what to do.
```
export FORCE_ATI_UNINSTALL="yes"
```
and then run the commands in: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by 4ebees on 2012-03-06
> **crypto2600 said:**
> Hey there guys. I had the exact same problem.
I got the ASUS K72JR-A1 (amazing laptop). I kept reading the forums until I realized the pattern that was fixing the issue.

There is something off about *Catalyst 10.2* and I could never get it to work. Here are the steps that fixed it (going to get into detail for new users):

...

MATE!!

I have to say that this was a perfect solution. I know you posted more than a year ago, but who cares?

I was gifted some two year old dual core machines for my kids. They had series 5000 ATI cards in them:

01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cedar PRO [Radeon HD 5450]

I normally use stock or Nvidia cards and am not often stuck for a solution.

I found a world of pain trying to get 3D to work on them properly, until I found your post. 

Seriously easy to follow.  I didn't need the watermark fix because for some reason it just didn't appear.

Soooo, I just wanted to say a great big thank you. I'm immensely appreciate and so are my kids.):P

---

### Post by An6r3w on 2012-06-24
Hy there so is the Ati Mobility 5470 HD working in ubunt, I tried this and that and it still didn't work for me, which version of ubuntu and the driver are you using, I have an Asus K52JE, 3D graphics didn't work for me...

---

### Post by Feathers McGraw on 2013-04-07
It took me hours to resolve this, but I **finally found a solution**, so I'll quickly summarise my findings for the benefit of anyone who uncovers this thread through google like I did.

The **ATI Radeon HD 5470** graphics card *does* work with the open source driver, but will likely make your laptop run 25C hotter than it does in Windows (try programs like CPUID hardware monitor in windows / Psensor in Ubuntu to check this yourself if you like). For me, this took the graphics card up to 80C+ when idle and made the laptop too hot to touch.

To bring the temperature down you need to use a different graphics driver. Here's where the fun begins...

There are two main desktop environments for ubuntu: UNITY and KDE. If you download "standard" ubuntu from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) then you'll get UNITY. If you download "Kubuntu" from [http://www.kubuntu.org/getkubuntu](http://www.kubuntu.org/getkubuntu) you'll get KDE. It is also apparently possible to install KDE after booting Gnome and vice versa...but I haven't tried it, and that's another thread.

Both Unity and KDE are great. If I had the choice, I don't know which I'd choose but the important thing is:

**_*UNITY is incompatible with the proprietary fglrx driver for the ATI Radeon HD 5470 graphics card*_**.

You need this driver. I'm unaware of any other driver that works and keeps the heat at a manageable level ...which basically means you can't use UNITY, and you'll have to use KDE.

SO. To business...

EDIT: this definitely works on 12.04 LTS, but may work on other versions too.

1. Install Kubuntu.
2. Remove any existing fglrx drivers and their settings:
```
sudo apt-get remove --purge fglrx*
```
3. Install the required driver:
```
sudo apt-get install fglrx fglrx-amdcccle
```
4. Configure the driver
```
sudo aticonfig --initial
```
5. **Reboot**
6. To get full hardware acceleration:
```
sudo apt-get install xvba-va-driver libva-glx1 libva-egl1 vainfo
```
7. Enjoy Ubuntu!

Thanks to QIII for providing a version of this solution on another thread.:-)

---

### Post by An6r3w on 2013-04-07
Hi, thx for the reply, i got rid of Ubuntu but will try this sollution when i get the chance, i would really like to revert to Ubuntu, hope this sollution will work for me 2.

---

### Post by Feathers McGraw on 2013-04-10
> **An6r3w said:**
> Hi, thx for the reply, i got rid of Ubuntu but will try this sollution when i get the chance, i would really like to revert to Ubuntu, hope this sollution will work for me 2.

You're welcome, friend. I was almost at the point of giving up myself...almost!

I have loads of coursework coming up and was at the point where if I couldn't get it working reliably before then I'd have to sack it off until after graduation, and miss the chance to learn by doing work with it, if you get what I mean...

---

### Post by Feathers McGraw on 2013-09-22
Just in case it's useful for anyone else stumbling across this thread, I found a better solution with the help of some folks at [Kubuntu Forums]("http://www.kubuntuforums.net").

I've written it up at the link below, but basically the solution is switching off an unused graphics card.

[http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/](http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/)

Hope this is useful to someone.

Feathers

---

