---
title: "[SOLVED] Fresh install on Vaio, no display"
date: 2008-08-13
forum: Hardware
---

### Post by hotrod6657 on 2008-08-13
In an effort to get my parents to migrate towards Linux and away from the soon to be unsupported XP I told them I would install Ubuntu on our old laptop, a Sony Vaio PCG-FX410.

I tried the live CD (7.10) and no go.  I got the first message screen and the progress bar on the splash screen but no desktop.  So i figured maybe i can't run live CD's on this machine and installed Ubuntu via the alternate disk (also 7.10)

Here's my problem.  The install went just fine, on restart everything seemed to work, grub timed out like it should and again i get the progress bar.  But after it's done the screen goes black, not off (you can see that there's light there).  I hear the login tone, and if i ender the username and passord (still with no display) i get the drums and apparently the desktop is running, i just can't see it.  Any ideas?  I forget how much RAM the machine has, at least 512, so the Live Cd should work.

I had a problem like this once with XP and it turned out one of the memory modules wasn't seating right, i guess it's a problem with these when they get old.  I added a shim to push it into place and XP ran well (i checked it right before doing the Ubuntu install)  Any ideas?

Thanks in advance!

hotrod

---

### Post by hotrod6657 on 2008-08-13
i'm running the memory test right now to take care of that theory.  It's going to take a while but i'm open to other ideas while that's running.

---

### Post by hotrod6657 on 2008-08-13
I'm still waiting for the mem test to finish...  I don't think i've ever done one of these before, should it be at 2 hours for just 512 MB of RAM?  No errors so far, but it's not quite finished...

Do you think trying to boot in to the live CD using safe Graphics mode would help?  If so how could i get around the install issue, what changes should i have made during the install?  I was expecting it to tell me i was in low graphics mode or something if that were the case.

**EDIT:**

Okay, i got tired of waiting for the mem test.  I aborted it and tried the live Cd again this time with safe graphics mode.  Success!  That works, just with really low screen space, uses up only a small rectangle in the middle of the screen.  I'm going to try the install again and see if that helps...  Any suggestions?

---

### Post by hotrod6657 on 2008-08-14
Okay, i tried installing in reduced graphics mode, but i didn't have enough usable screen space to do so.  I couldn't see the buttons on the install window, and for some reason, the buttons at the top of the screen were shifted, they weren't where their icons were and i couldn't find the right spot to get to system (i was going to see if there was any way i could get more resolution out of it.

Right now i'm reinstalling it with the alternate CD.  I'm going to see if enabling different resolutions when prompted to do so changes the result.  I wish i was getting some sort of error message with all this, it's weird just having the screen not work.

---

### Post by coffeecat on 2008-08-14
I think we need to ensure that your machine doesn't have some obscure video chipset that's causing the problem. If you're right about the 512Mb RAM, you should have no problems with the live CD. I'm posting from a Sony Vaio VGN-FS215B with 512MB RAM, and I've installed every version of Ubuntu since Dapper on it with the live CDs, and several other distros as well. But I've got the Intel 915G video chipset which is well-supported.

If you do have 512Mb RAM, then I would strongly advise you to see if you can get some live CD or other to run first. If a live CD gives you a good display, then you're almost certain of getting a good display with a hard disc installation. Mucking about with the alternate CD in a situation like this is only likely to lead to frustration and annoyance.

Suggestions: first, can you post more details of the hardware, **particularly** the video chipset. Do you still have Windows on the machine? If so, you should be able to get a lot of there information there.

Second: if you have enough bandwidth, I suggest you download the latest (and get the 8.04.1 version) Ubuntu Hardy Heron (live CD) to try. Also, download some other distro live CDs. Sometimes one will work where another will not. Even if you don't install one, they can be useful for troubleshooting. Mepis, Mandriva and openSUSE all do perfectly good combined live/install CDs.

---

### Post by hotrod6657 on 2008-08-14
okay, well with the alternate CD i did manage to get a viable install.  Problem is the only two resolutions i have are 640 x 480 and 800 x 600.

According to the Device Manager the graphics controller is:  "82815 Chipset Graphics Controller (CGC)"  I'll see if i can't find out more about it.  I do not still have windows installed but i'll see if i can find anything more.  I can't remember the terminal command that would display device information.

I did at one point have PcLinuxOS running on this laptop before, and ran through the live CD too.  It ran really well, but if i'm trying to get my folks used to Linux i don't want to switch distros on them lol.  I'll start downloading 8.04 (I have that running on my desktop but it's 64bit).  

Other than the resolution it seems to run fine right now.  The windows seem to move smoothly and it's reasonably quick.  Maybe a little X configuration?

hotrod

---

### Post by coffeecat on 2008-08-14
That sounds like an old Intel chipset. In order to be sure, the command you couldn't remember is:

```
lspci
```First thing - are you sure the screen can do more than 800x600? If you are, the package 915resolution *might* help. I've never had to use it myself but (from the Synaptic package description):

> resolution modification tool for Intel graphic chipset
915resolution is a tool to modify the video BIOS of the 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.
This modification is necessary to allow the display of certain
graphics resolutions for an Xorg or XFree86 graphics server.I said 'might' because I see that the 815 is not listed there, but it would be worth a try.

---

### Post by hotrod6657 on 2008-08-14
Thank you for that, I'll give that a shot and post the output of lspci as soon as i'm back on that machine.  I've got a really slow DSL connection so the new ISO is taking a while.  And I'm running updates on the Vaio since i wasn't able to have it connected during the install.  As soon as the update is finished I'll install 915resolution and see if it helps.

The monitor will do more than those resolutions.  As it sits now it's 800 x 600 but only uses the middle of the screen, there's about an inch and a half border or black around the whole screen.  In XP it did at least 1024 x 768.  And the screen was full with no black around the borders.

Thanks in advance for helping me out!  I'll post an update when i get to try that program.

hotrod

---

### Post by hotrod6657 on 2008-08-14
Here's the ouput from lspci:
```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:02.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)

```

You're right about being an intel chipset.

**EDIT**

I tried installing 915resolution and it didn't seem to change anything.  I installed it from synaptic and restarted x but same results unfortunately.

---

### Post by coffeecat on 2008-08-14
The only other thing I can suggest, if you're sure that machine is capable of more than 800x600, is to add appropriate lines to the Screen section (I think) of /etc/X11/xorg.conf. Sorry to be so vague, but I'm posting in haste from MacOS, so I'm going from memory of xorg.conf here, and I have to go out soon.

Or you could see if the Hardy live CD copes any better

---

### Post by hotrod6657 on 2008-08-14
I'll give that file editing a shot.  It can't hurt right?  it's not like there's any data to loose.  lol.  I'll also give the hardy CD a shot too when it's done.  I have a linux mint cd that i might try just to see if it works.  I think it would give the same feel as full fledged ubuntu which is all i need.  I remember that Pclinuxos looked a lot different than ubuntu and i don't want to confuse my folks by mixing in too many differences when i finally do migrate the desktop to linux.  Thanks again for taking the time to reply.

---

### Post by hotrod6657 on 2008-08-14
My download of Hardy finally finished.  I'm in the process of installing it.  The live CD part did work much better than on the other CD.  I still don't have full resolution but I think I might have a little more to work with.  After the install I'll try 915resolution again and see if it does anything.  I'll also give editing that file a shot to see if i can't get a few other resolutions options.  I do think that i could get by with just the 800 x 600 if i absolutely have to.  It doesn't look too terrible

---

### Post by hotrod6657 on 2008-08-14
no luck editing the xorg conifg file.  There really wasn't anywhere to add resolutions.  Maybe i'm doomed to have poor resolution on this sony.  It's a bummer because if it worked right it would sure beat XP.  I might hav to convince my folks to dual boot Ubuntu and XP on their desktop for a while to get used to it.  

I just don't want to throw a whole bunch of changes at them only to go back to school in a few days.  I know that would be more trouble than it's worth.  I'll end up getting calls from them every couple of days if something stops working.  

Anyone know how to add resolutions to 8.04?  The xorg config file looked way different than the file did on 7.10.

hotrod

---

### Post by coffeecat on 2008-08-15
> **hotrod6657 said:**
> Anyone know how to add resolutions to 8.04?  The xorg config file looked way different than the file did on 7.10.

With newer versions of the xserver, it does more autodetecting and hence needs a simpler xorg.conf. But when it doesn't autodetect correctly, you put in the lines of code that are needed. At least that's the theory. I don't know whether this will work, but assuming your screen is capable of 1024x768, try this for the Screen section:

```
Section "Screen"

    *Leave in whatever values you have for Identifier, Device and Monitor here*

    DefaultColorDepth 16
    
    Subsection "Display"
        Depth 8
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 15
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 16
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
    
    Subsection "Display"
        Depth 24
        Modes "1024x768" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection
```Leave out the 480x360 and 320x240 resolutions if you want - this was just a quick copy, paste and edit job from an old xorg.conf. Also, you might have to experiment with different values of DefaultColorDepth.

---

### Post by hotrod6657 on 2008-08-15
okay sweet, that's what i needed.  I'll try that right away and see if i have any luck.

Another thing i've noticed is that usually i can restart x with ctrl + alt + backspace but not with the sony.  I don't know if maybe it's keyboard won't recognize those three keys at once or what.

---

### Post by hotrod6657 on 2008-08-15
BOOYAH!  Editing xorg.conf didn't work, the solution was even simpler.

Here's that i did:

```
sudo displayconfig-gtk
```

That opens up the screen and graphics preferences window where you can choose your card and monitor.  Now, i played with the cards a bit because it says under driver that it's not using any and there is a 815 driver listed.  Selecting it and clicking test didn't work so i gave up on that (I've come to find though that the test just doesn't work on that window.  Even not making any changes and keeping the resolution the same gives a gray screen with an x for a cursor.

Then what i did was on the screen page select generic LCD Panel 1024x768.  Pressed Okay, was told to log out.  Did so (apparently control alt backspace only works sometimes for me, i have to press it very fast to get it to work)  Logged back in and viola, the new resolution appeared under resolutions, selected it and we're good to go.  No more black around the edges, looks good.

I might try selecting the 815 driver and logging out to see what happens.  I just don't want to mess up x and have start over... or do i ;)

Thanks for all your help, it kept me going on this on, i'm glad it's solved.  Now where's that mark thread as solved button :)

hotrod

---

