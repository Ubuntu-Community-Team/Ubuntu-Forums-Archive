---
title: "How to enter BIOS on a mini PC with AMD processor?"
date: 2021-07-28
forum: Hardware
---

### Post by tahitiwibble on 2021-07-28
Greetings one and all.

It seemed like a good idea but now I'm having regrets.

I couldn't afford to replace my laptop with a new one so went for a "TOPTON Mini PC AMD Ryzen R5 3550H R7 2700U Vega 10 Graphic 2*DDR4 M.2 NVMe" and asked that the store install Ubuntu for me. Well they did, but now they can't remember the password that they used when they created the 'USER' account so I can't do a thing. Neither can they explain to me how to enter the BIOS so that I be able to reinstall Ubuntu on my own.

Can anyone PLEASE help me with how to enter the BIOS?

Many, many thanks in advance!

All the best, Martin

---

### Post by ajgreeny on 2021-07-28
Do you see a grub menu at boot or does it boot straight to Ubuntu?
You should be able to get to the grub menu if it does not appear by default, but how you do that will depend on whether the computer uses legacy BIOS or UEFI.

If BIOS you need to hold Shift just after pressing the power button, if UEFI, which is much more likely, you need to continually tap Esc also at the same time, just after pressing the power button.

If, or maybe I should say when the grub menu appears select the Advanced section with cursor button and from that choose Recovery mode.
Once in recovery mode follow the instructions at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword) very carefully and you should be able to reset your user password.

---

### Post by tahitiwibble on 2021-07-28
Thank you AJ, some hope at last. No grub menu and probably UEFI, but I am just supposing things. I will try all your suggestions and let you know.

---

### Post by tea for one on 2021-07-28
Also, assuming Ubuntu is in UEFI mode and you can reach the grub menu, you will find an option to access the UEFI set-up.

---

### Post by oldfred on 2021-07-28
If UEFI, you press escape key between vendor's UEFI/BIOS screen & when grub should appear. Often have to try several times or press escape multiple times to get it to work.
Most systems use del or f2 for directly access to UEFI from UEFI/BIOS screen. Many show keys on screen for just a few seconds.

Is it Ubuntu user account or UEFI account passwords you need.

---

### Post by tahitiwibble on 2021-07-29
I am so grateful to you guys trying to help me out here! Huge thanks!

Unfortuntely:

In between time the vendor of this thing got back to me and gave me the password ......... they also said "Press F1, F2, ESC or DELETE to enter the BIOS".

So, I eventually got into the system with ssaid password and was upset to see that they had installed Ubuntu 19 something and then went for an update to LTS version 20.04 (I would never have tried to do an update from the desktop but figured that as this is a brand new machine 'why not'). All went well untill the restart and now the machine freezes at various stages of the boot procedure. Sometimes I will have time to get to the desktop and sometimes never get past the already frozen login screen. I have restarted the computer hundreds of times with just about every possible key combination trying to get into the BIOS/UEFI hundreds of times to no avail. This is starting to affect me in an evil way. I don't know what to try next.

I have never got to the vendor's UEFI/BIOS screen. I have never yet seen the grub menu.

> **ajgreeny said:**
>  if UEFI, which is much more likely, you need to continually tap Esc also at the same time, just after pressing the power button.

AJ, did you mean to press the power button and then **hold** 'shift' and continually tap 'ESC' ....... simultaneously?

> **tea for one said:**
> Also, assuming Ubuntu is in UEFI mode and you can reach the grub menu, you will find an option to access the UEFI set-up.

You can't imagine how I long to set eyes on the grub menu; this has been nearly two days of trial and error now.

> **oldfred said:**
> If UEFI, you press escape key between vendor's UEFI/BIOS screen & when grub should appear. Often have to try several times or press escape multiple times to get it to work.
Most systems use del or f2 for directly access to UEFI from UEFI/BIOS screen. Many show keys on screen for just a few seconds.

Is it Ubuntu user account or UEFI account passwords you need.

Being a brand new box I can only suppose that this is UEFI. I am going to try all the variations on the key combination theme that you suggest. I just don't understand why I see no vendor's UEFI/BIOS screen.

---

### Post by tea for one on 2021-07-29
Here is another suggestion, assuming you have a USB stick with Ubuntu (or similar) prepared as an installation device:-

Open the case
Remove the hard drive(s)
Plug in your installation media
Power on the PC
Boot into a [COLOR="#0000FF"]live[/COLOR] session
Open a terminal and enter
```
sudo systemctl reboot --firmware-setup
```
This command should reboot to the UEFI set-up.

---

### Post by tahitiwibble on 2021-07-29
Thank you tea for one. I have a feeling that this might do the job, although not before tomorrow. It's past midnight and these poor old bones are weary. I will let you know how things went after the intervention. Peace to you.

---

### Post by cryptearth on 2021-07-30
If the uefi is locked down by a password (although there's no reason why but as all I was able to find about the device is from AliExpress it's a way to scam unexperienced users) you could try to clear the cmos by detaching the backup battery which should clear it. Also as it clears out all customized data the system should force-prompt to enter uefi on next boot anyway.
Also: Did the freeze already happened before you started to tinker around or did it only start after you did something yourself?

---

### Post by tahitiwibble on 2021-07-30
> **cryptearth said:**
> If the uefi is locked down by a password (although there's no reason why but as all I was able to find about the device is from AliExpress it's a way to scam unexperienced users) you could try to clear the cmos by detaching the backup battery which should clear it. Also as it clears out all customized data the system should force-prompt to enter uefi on next boot anyway.
Also: Did the freeze already happened before you started to tinker around or did it only start after you did something yourself?

Hey cryptearth thanks for the 2 cents. In a nut shell; after 24 hours of messaging them I eventually got the password from the vendor and got Ubuntu 19.?? up and running (you'd have thought they might send the password in the box with the PC). 

So I wanted to update the system to 20.04 and that's when everything fell apart. I would never have updated in that manner but thought "well it's a virgin system so what could go wrong!?" also I was never able to get into the BIOS/UEFI to boot from a USB stick. The update seemed to have gone OK but on reboot the freeze happened. The weird thing is that if I hit F1 on the boot procedure I can sometimes see the boot procedure scrolling on the command-line-type screen and I can sometimes even get to the desktop before it freezes again. The update just didn't go the way it could/should have.

I got so demoralised by 48 hours of total frustration that I haven't looked at the thing since yesterday but am going to dismantle it this afternoon and try what 'tea for one' suggested, I will also disconnect the backup battery (if there is one). When I took the box out of the packaging I thought they'd missed out the 512 SSD that I bought but there is 512 gigs of storage somewhere, I just hope that it's not soldered onto the motherboard.

BTW I got a message a few minutes ago from the vendor saying "Press DELETE to enter the BIOS" which doesn't work. At least they're being a little more specific because the other day it was "Press F1, F2 ESC or DELETE to enter the BIOS". You'd think that the people who supposedly built the machine might now exactly what is needed.

---

### Post by cryptearth on 2021-07-31
Wow, that's quite a story. Sorry I seem to have missed some important points in your previous posts so you had to re-type it ...
From as far as I understand your situation to me it looks more like someone just grabbed some parts of the shelf, stuck them together in a way to fit your order and somehow installed the requested OS (although strange it was such an old version).
As for the in-place upgrade: Well, from my personal experience Linux based OSs seem to handle it quite well if one go the long incremental route. So, upgrading from a 19.04 or 19.10 should to 20.04 LTS should had been fine - I'm curious what happens these random hang ups. Could be some software issue causing "random" stuff due to multi-core execution in a not-so-predictable order - but also could be some hardware limitations. Hopefully you not get a somewhat-defective unit.
About try to enter the uefi/bios: Funny enough that's still something not officially standardized yet (at least to my knowledge) - so enter the system firmware can be done in a variety of ways. Many board manufactures seem to have agreed upon to at least support DEL as one of the hotkeys - at it was the most used back in the AT era before modern ATX took over. But it can also be pretty much anything ranging from more familiar keys like the F1-F12 keys (often F1 or F2 or anything F8-F12) to some weird key-combinations with any of the modifiers (ALT, CTRL, SHIFT). ESC to enter the firmware is rather untypical and is often used to get from the graphical logo to a more traditional text base boot screen (also TAB is sometimes used for that). It could also be not be able to be done from a keyboard but maybe require some hardware switch hidden in the box on the board itself.
But I agree with you - the staff should know how to access the bios or uefi firmware of a device they sold to you. Also: Not including some default password for a OS that requires a password (to my knowledge it's only possible to set up auto-logon - but not to remove the password entirely as on windows) is ... well, let's just say: Someone seem to had a bad day.

From what I get is you seem to get at least from the initial power up to the bootloader which then in turn at least tries to boot the OS. So, yea, open the case and taking out the storage (if not soldered) should at least confuse the system to no longer be able to boot which should give you some way to access the firmware. There's also a chance that it could be hard to detach the cmos-battery. Guessing from pictures I was able to find on the net by searching for what you have given us in your initial post suggest it's not a socketed one but should just hanging in their loosely with the wires terminated into a two-pin connector. Just detaching it for a few seconds should be enough to clear out the cmos which then should result in the system to halt on a cold boot with some text like "blah blah blah press <some key> to enter setup". Although not ideal as you have to deal with re-setting all the settings correctly (which may require some tries) it should be at least some almost guaranteed way to get a force-prompt.

It's always hard to analyze from far away. Just as an example I have a PC-Engines APU2 for some years now (can't remember the correct model - there'Re already at least one or maybe even two newer generations of it) - and it uses coreboot as its bios/uefi. To enter it's rather small set of settings I have to connect via serial and catch it right when I plug in the power. Luckly I only need to do that stunt if I have to change some very basic firmware setting. For anything else there'Re plenty of small tools available for the distro I run on it. So, yea, I know how it can steal a whole week of tinkering around and not getting any progress.

---

### Post by oldfred on 2021-07-31
If you can boot the Ubuntu live installer (or any current flavor), run this:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Since UEFI system, be sure to boot in UEFI mode. Of if live installer created by Rufus, be sure to create installer in UEFI/gpt mode.

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Many of us like different flavors of Ubuntu. Best to just try with live installer.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

### Post by tahitiwibble on 2021-07-31
Is anybody out there??? I mean right at this very minute because I am FINALLY running 20.04 on a live session from a USB drive and have no SSD or backup battery (both disconnected for testing purposes).

Is there anything that I can try in the Terminal to ensure being able to boot back up once I have reinstalled the SSD and reconnected the CMOS battery?

I want to know if I can hook the SSD back up while the PC is powered on?

---

### Post by tahitiwibble on 2021-07-31
This is what I'm using here

[https://photos.app.goo.gl/oTRiExyd5n5xt8687](https://photos.app.goo.gl/oTRiExyd5n5xt8687)

[https://photos.app.goo.gl/6iumojkHU8EiVBRm9](https://photos.app.goo.gl/6iumojkHU8EiVBRm9)

---

### Post by MAFoElffen on 2021-07-31
Okay... I read your PM request for help and have read through this... for clarity... You did get 19.10 up and running, then did a release upgrade to 20.04... And then was having problems from there after the reboot?

While waiting for an answer, looking through the links of what you are running.

---

### Post by tahitiwibble on 2021-07-31
Correct, nothing worked correctly after reboot. After being given the correct password by the vendor 19.10 functioned without a hitch ....... only after upgrading to 20.04 did everything erratically freeze up

Having Googled being able to reconnect an internal SSD, or not, I find that answer to be a resounding NO! I risk losing the mother board.

Right now the only componants that are powered up are the motherboard, the live USB drive and the wifi card ........... neither 512gb SSD nor CMOS backup battery connected.

---

### Post by MAFoElffen on 2021-07-31
Why are those now powered on? Because you couldn't get into the BIOS on the board unless they were disconnected? (I just breezed over the posts...)

Not sure what that would gain you if you needed to correct your install...

Let me back up a bit with where you are now... You said you installed ___ now many versions. Since you have, how sentimental are you with what is there currently? Can you now get into the BIOS when powering up? You've done a few things, so are not totally in the dark now right?

I can see that PC came from China and has no documentation. LOL

---

### Post by MAFoElffen on 2021-07-31
Why are those now powered on? Because you couldn't get into the BIOS on the board unless they were disconnected? (I just breezed over the posts...)

Not sure what that would gain you if you needed to correct your install...

Let me back up a bit with where you are now... You said you installed ___ now many versions. Since you have, how sentimental are you with what is there currently? Can you now get into the BIOS when powering up? You've done a few things, so are not totally in the dark now right?

EDIT: I went back and read. TeaForOne asked you to do that to boot to the USB and enter a command that might have forced it to boot to the UEFI BIOS. Did It? Someone else asked you to disconnect the CMOS Battery to clear the Settings to default, like a Password...

---

### Post by tahitiwibble on 2021-07-31
> **MAFoElffen said:**
> Why are those now powered on? Because you couldn't get into the BIOS on the board unless they were disconnected? (I just breezed over the posts...)

I'm using the PC at the moment, that's why I say they are the only things powered up. With the backup battery and the internal SSD connected the machine tries to boot up into 20.04 and freezes like yesterday. I have never been able to get into the BIOS yet.

---

### Post by MAFoElffen on 2021-07-31
EDITTED. Saw your post, and you still cannot get into your UEFI BIOS... Didn't they tell you that it was the <DEL> key and gave you the password?

Does it boot to the USB before the SSD? I'm assuming so, because it first came with Windows and you installed Ubuntu 19.10, right?

---

### Post by MAFoElffen on 2021-07-31
And when it tries to boot to 20.04, what does it do exactly.? What do you see?

---

### Post by tahitiwibble on 2021-07-31
> **MAFoElffen said:**
> EDITTED. Saw your post, and you still cannot get into your UEFI BIOS... Didn't they tell you that it was the <DEL> key and gave you the password?

Does it boot to the USB before the SSD?

It came with 19.10 pre-installed as I had requested.

I have never seen the BIOS/UEFI, ever. Yes they did say to use the DEL key but it didn't have any affect whatever. The password allowed me to boot up with 19.10 and it was after the update to 20.04 that nothing worked any more. By some quirk in the universe about 1.5 hours ago with no SSD and no battery attached the thing booted up with my live USB stick.

---

### Post by tahitiwibble on 2021-07-31
Should I ....

```
sudo systemctl reboot --firmware-setup
```

..... as 'tea for one' suggested?

---

### Post by MAFoElffen on 2021-07-31
Yes... LOL. Switching between this thread and your PM's...
[https://www.freedesktop.org/software/systemd/man/systemctl.html#--firmware-setup](https://www.freedesktop.org/software/systemd/man/systemctl.html#--firmware-setup)

And change the boot order to boot from USB first... And since you are no longer using Windows, turn secureboot off.

---

### Post by tahitiwibble on 2021-07-31
> **MAFoElffen said:**
> And when it tries to boot to 20.04, what does it do exactly.? What do you see?

Since my update it just froze at various time during boot. Nothing to see other than a black screen and then sometimes the Ubuntu welcome screen and then sometimes I was able to put my new password in and proceed for a few seconds until another freeze.

---

### Post by oldfred on 2021-07-31
Many UEFI have a setting called fast boot, that is different than Windows fast start up.
Fast boot in UEFI assumes no system changes, so UEFI does not update info on hard drive for operating system to use. When changing system, you need fast boot off. And if fast boot is on, you often do not have enough time to press the key to get into UEFI as it immediately boots.

Sometimes just a total cold boot or full power shutdown. You have to remove all power and even hold power switch to make sure system is fully drained. Then it should do one normal boot where you just have a bit of time to press correct key to get into UEFI. Your del key?

Sometimes you have to remove coin battery which is used for system to remember settings to force it to turn the full start up and give you just enough time to get into UEFI with del key.

But full UEFI reset, requires you to redo the settings you changed to allow Ubuntu to be installed. 
Since you did not do those settings, best if you can get into system without full reset.
But typically settings include changing drive to AHCI from RAID or Intel RST, turning off fast boot. 
Many turn off UEFI Secure Boot to avoid some issues. (may need it later, but then may have to update grub, kernel & drivers to signed versions).
   Some do not call it UEFI Secure Boot, but "Windows" or "Other". My older system says you have to use "Other" for Windows 7 (as it does not support UEFI Secure Boot). Or that is really the Secure Boot setting.
You only want UEFI boot mode, do not turn on or use any Legacy/BIOS/CSM mode settings.

---

### Post by MAFoElffen on 2021-07-31
Additional to what oldfrd said, also, unplug the pwer cable from the power supply... Look back at the power supply. Take a quarter and short out, between the three pins, via pairs at a time. This will discharge the capacitors.

---

### Post by MAFoElffen on 2021-07-31
> **tahitiwibble said:**
> Since my update it just froze at various time during boot. Nothing to see other than a black screen and then sometimes the Ubuntu welcome screen and then sometimes I was able to put my new password in and proceed for a few seconds until another freeze.

A black screen is still good. I'll explain after you try what I and oldfred suggested. What you are describing "now" is that the kernel and system is booting, that it is that the graphics layer is not coming up... Yet.

Every detail you divulge tells us more info...

---

### Post by tahitiwibble on 2021-08-01
Alright Gentlemen. Huge thanks to you both/all. I'm loosing light of day and will have to resume tomorrow morning. I'm just so hesitant to turn this thing off now that I have an up and running computer. 

What will be the result of : -

```
sudo systemctl reboot --firmware-setup
```

OK got it! Thanks for that link MAF, it looks as if it could be useful down the line.

PROFUSE thanks again to you guys! =d>

---

### Post by MAFoElffen on 2021-08-01
While you are running look at the link in my last few posts... It gives Linusx the same capabilities of Windows 8.x on, in that it will reboot to your UEFI BIOS Setup screen. Then you can make the changes me and oldfred recommended you change to.

LOL> But you're install is working and not all gone. (See my last post.) I'll wait for that until you try that first... PM me and tell me what time to be online,,, I will get back and watch for you whenever you say. I am PST timezone.

---

### Post by MAFoElffen on 2021-08-01
While we are waiting, for tomorrow, writing this as s scratch pad for notes for tomorrow.

Your APU requires Kernel 5.2.x and later. It also requires Mesa drivers be installed. On Ubuntu Kernels, it runs best if we add the "nolapic-timer" boot parameter. 

Ubuntu 20.04 will install and run to a secureboot on. But you installed with 19.10, so you may have to generate new secureboot keys to sign the kernel enaable DKMS updating for it to work, if you couldn't turn secureboot off in the UEFI BIOS,,, If you can turn it off, that will be much easier.

After you make those changes to the UEFI BIOS, save those changes... Then you will need to take a picture of this, or write it down, so you have something to follow.


After reading and recording these instructions somehow...

You will power down and put your computer back together. Both the CMOS battery and your SSD.

Make a decision whether you are have any attachment to the install you did. 

If this was a brand new install and have no attachment, and if you couldn't for some reason change just the secure boot setting off... The reboot to the USB and install 20.04 as clean and fresh (new). That will, install with DKMS and a digitally signed kernel. If given the choice of HWE aor general, supposedly your CPU/APU runs better on the General version of the kernel. Be sure to check the box to 3rd Party Packages when you are installing.

If you have connections to the your install... It is salvageable. After you boot up to your SSD and gets to a black screen... Press <Cntrl><Alt><F4>... That should get you to a TTY Virtual terminal. That alone tells you the System booted successfully and the other Graphics session just failed. From there...
```
sudo apt update
sudo apt full-upgrade
dmesg | grep -i amdgpu # record the output of this somewhere
sudo apt install mesa-utills
fgxinfo | grep -i mesa # record the info from this somewhere
sudo nano /etc/defaults/grub

```
Go down to the line that contains "quiet splash" and add, inside the quotation marks, add "nolapic-timer" like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic-timer"
```
Then Press <Cntrl><O>, then <Entrer>, Then <Cntrl><X>...
When it retruns to the commandline
```
sudo update-grub
sudo reboot
```
That shouild get that going... Crossed fingers.

---

### Post by tahitiwibble on 2021-08-01
> **cryptearth said:**
> It could also be not be able to be done from a keyboard but maybe require some hardware switch hidden in the box on the board itself.

I wonder about that possibility. I opened the box up and found that there is only one jumper switch on the motherboard and I hesitate to change the position.

> **cryptearth said:**
> From what I get is you seem to get at least from the initial power up to the bootloader which then in turn at least tries to boot the OS. So, yea, open the case and taking out the storage (if not soldered) should at least confuse the system to no longer be able to boot which should give you some way to access the firmware. There's also a chance that it could be hard to detach the cmos-battery. Guessing from pictures I was able to find on the net by searching for what you have given us in your initial post suggest it's not a socketed one but should just hanging in their loosely with the wires terminated into a two-pin connector. Just detaching it for a few seconds should be enough to clear out the cmos which then should result in the system to halt on a cold boot with some text like "blah blah blah press <some key> to enter setup". Although not ideal as you have to deal with re-setting all the settings correctly (which may require some tries) it should be at least some almost guaranteed way to get a force-prompt.

I did what you suggested and disconnected the internal SSD and the CMOS battery. With a live Ubuntu 20.04 USB stick it boots up just fine and dandy. Foolishly I didn't try to boot it without the USB stick connected, I'll do that tomorrow and see what happens. Yeah you were right, the battery just dangles in the case but all least it had an accessible plug.

> **cryptearth said:**
> So, yea, I know how it can steal a whole week of tinkering around and not getting any progress.

Day 4 here LOL. I had this kind of thing happened once a long time ago. Right now I must be on about the 6,745th key combination on boot but the damned thing ain't gonna beat me LOL.

I'm grateful for your help.

---

### Post by tahitiwibble on 2021-08-01
> **oldfred said:**
> If you can boot the Ubuntu live installer (or any current flavor), run this:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Since UEFI system, be sure to boot in UEFI mode. Of if live installer created by Rufus, be sure to create installer in UEFI/gpt mode.

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Many of us like different flavors of Ubuntu. Best to just try with live installer.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

OldFred, please forgive me. I looked at your response and my brain went into a kind of helter-skelter mode. I now see the rhyme and reason behind your instructions and will apply myself to a follow up tomorrow. I appreciate your assistance!

---

### Post by MAFoElffen on 2021-08-01
FYI... LOL... That was 17-18 posts back. Just saying.

---

### Post by MAFoElffen on 2021-08-02
Putting everything back together... Then boot without the USB Key. Let it get to where it is totally black graphi9cal, or at the login screen. Before the graphics locks up... Switch over to a virtuall tty session <Cntrl><Alt><F4>. Log in with your credentials.

Run blkid to list the filesystems of your system
```
sudo blkid | grep -i vfat
```

Mount the EFI partition found inthe last step
```
sudo mount -t vfat /dev/sda1 -o rw
```

Remove the directory and all files within the ubuntu directory
```
rm -rf /ubuntu
```
Reboot. The Grub will be gone, and you should be able to boot back up with your USB key... Because it will go to your SSD in the boot order, fail, then go to your USB.

Then you will be able to do a fresh install from your USB...

---

### Post by tahitiwibble on 2021-08-02
So I just typed ctrl alt F4 about 6 times and realized that I was using the wrong keyboard LOL

But hey ........ EUREKA I have what apppears to be progress

---

### Post by tahitiwibble on 2021-08-02
The rejoicing was short lived, here is a link to what I have on the screen.

[https://photos.app.goo.gl/mAdAp4pmGtybNbyB6](https://photos.app.goo.gl/mAdAp4pmGtybNbyB6)

---

### Post by MAFoElffen on 2021-08-02
I think that hardware error is related to having to add the "nolapic-timer" boot aprameterto your linux boot line... Go back to this post:
[https://ubuntuforums.org/showthread.php?t=2465291&p=14051209#post14051209](https://ubuntuforums.org/showthread.php?t=2465291&p=14051209#post14051209)

And during one of your tries, follow the instructions to try to add that in...

---

### Post by tahitiwibble on 2021-08-02
I'm losing hope. The screen just freezes at the stage shown in that image which I linked to.

It's so frustrating to see everything function from a USB drive when there's no SSD attached. I'm wondering what would happen if I took a 2.5" drive out of an external HDD that I have and put that into the box?

---

### Post by oldfred on 2021-08-02
Many systems have needed UEFI update. Does your vendor have an update on its support page?
And most SSDs even new, also have firmware updates which can solve issues.
I have a Samsung NVMe SSD and the update was a bootable ISO. Looked very old school, text menu & one choice just for my model.

You just about have to have a way into UEFI/BIOS.
Grub menu has a reboot to UEFI entry, different than the sudo systemctl reboot --firmware-setup entry.
As soon as you start booting press down arrow, as soon as grub has control it will recognize key entries and even if menu does not appear will change entry to how many presses you make.

Also can you boot recovery mode? It uses nomodeset entry to not use graphics.

---

### Post by MAFoElffen on 2021-08-02
Well. heck...

Lets go through what we have tried... 

You can't get to the Grub Menu, which you give you access to the Recovery Environment, where you would have at the least, a root command prompt. Or at the last menu option of a Grub Menu installed on UEFI, an option to Boot into the UEFI Settings Environment...

You've now tried multiple ways to get into the UEFI BIOS Settings, and they have all failed. If you could have, then you could turn off secureboot, fast boot and change the boot order. WE have deducted that the boot order is currently set to SSD, then USB... 

So currently, you cannot boot from a USB, unless the SSD is not working, or is not present... 

The installation on the SSD is working only to a point... It is working only enough to boot the kernel to a login, then has problems. The problems now identified and not just with the graphics...So you don't have enough of a system to repair the  installed system, nor to cripple the SSD enough that it is not bookable. If you could have crippled the SSD by removing the boot loader, then it would fail-over to USB to boot... 

We have deducted that the install on the SSD is corrupted... If the SSD is not there, then if it does boot from the USB and Ubuntu 20.04 runs just great, with no problems. It seems to run stable, with no problems. That tells us, the system on your SSD has problems. So we know, that if it did install correctly, you would be good.

From there we discussed trying a different storage disk. I'm not there and cannot see it. There are no doc's for this "Mini PC". It's just taunted as the cheapest "Mini PC" in the world... A very cheap Chinese "budget" device. Only sold by Ali Express. So it is made somewhere in China. Ali Express say's it is shipped with a User Manual. There is almost nothing about it, or it's specifications anywhere online... At least, not in English.

You asked if a regular 2.5" SSD would work... Well, that is a loaded question and it all depends on the interface and connection... I don't think an SSD with a SATA Interface will work,  only because with all the offerings of different config's sold for this, I only see M2 and NMIE SSD's, with were not a SATA type connection, right? You asked this because you are a bit remote, in location, so if it is not local, it would take at least 4 weeks to get "anything." 

I mean, it might not hurt to try and see if it does, but make sure the SSD is not bootable before connecting it to it, so it fall over to the USB key.

So to use a different  SSD, if the connection were different, you may need an adapter. You also thought about just buying another new NMIE SSD, to install to... That part would not be found locally to you, which would be over a month for you to get. Which brings it back to... Whatever you do has to make sense, and be part of a plan... And the plan should include what has been learned so far, so that you are not dead-ended for the future...

Anything you buy is going to take at least a month for you to get. I feel that your best investment would be to get a USB3 Hub (powered) and a USB to NMIE adapter for your current drive. That would give you the capability to Boot from your USB LiveCD Key (with the SSD removed), then to safely be able to add your SSD, via plugging in the USB adapter, to reinstall to. I believe that investment would still be cheaper than buying another SSD. And still leave options to you for future reuse.

I think planning for the future, that you should add a reserved 10GB partition, formatted as EXT4 to copy an ISO image file to. Then add a loopback menu item to the Boot Menu to be able to boot to it, as a Fall-back Recovery Option. Also re-configuring the Grub Menu, so it always displays, at least for a few seconds. I think this experience has some lessons learned that you don't want to get trapped into again. That way, if you want to add the Boot-Repair ISO (or more) to it as recovery utilities, you can... If you have room reserved in that ISO partition to copy them to...

In the meanwhile, with the SSD removed, you can use Ubuntu from the USB key. 

You can continue to work the support from where you bought it from to try to get into your UEFI BIOS Settings... Eventually, and realistically, you are going to need the ability to be able to get into your UEFI settings. In my search over the past 2-Days, I have seen a bit on Mini PC's where other people cannot get into their own BIOS Setting Screens, even from people at Universities, so I think we might start to see this more for them, for Budget integrated/embedded devices.

---

### Post by tea for one on 2021-08-02
@tahitiwibble - Did you try my suggestion in post 10?

I note your comment in post 33, which implies that you still haven't tried it?

---

### Post by MAFoElffen on 2021-08-02
@Tea For One:

Yes he did try it... He was finally able to try that last night. Look at my last post. That was supervised via PM's and over Skype... A lot of things have happened now, behind the scenes, since then. 

Seems that his EFI BIOS is NOT Window's Compliant, in that respect, so that Systemd systemctl command "does not" work...

---

### Post by tea for one on 2021-08-02
@MAFoElffen - I didn't realise that there were efforts being made behind the scenes.

I had hoped that my suggestion had been put on the back-burner while other avenues were explored, but, alas, it was not to be..........

---

### Post by tea for one on 2021-08-02
@MAFoElffen and @tahitiwibble

I have discovered another little surprising twist today.

When you tried my suggestion to reboot to UEFI set-up via a live session, does the following output look familiar:-

```
sudo systemctl reboot --firmware-setup
Cannot indicate to EFI to boot into setup mode: Firmware does not support boot into firmware
```

You would receive this failure message if you originally booted the [COLOR="#0000FF"]live[/COLOR] session in [COLOR="#FF0000"]Legacy[/COLOR] mode.

Can you confirm that the live session was in [COLOR="#0000FF"]UEFI[/COLOR] mode?

---

### Post by MAFoElffen on 2021-08-02
@Tea For One:

Yes... If he could just get to a grub meun or shell, he could have just gotten to a grub command prompt and entered: fwsetup ... which for grub, would have booted tothe EFI Setup. But it wouldn't. No matter hard he tried.

---

### Post by MAFoElffen on 2021-08-02
@Tea For One... Form his USB Key... He could confirm that via 
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

Then if BIOS, maybe he could create another LiveCD USB key that is UEFI boot only...

---

### Post by tahitiwibble on 2021-08-02
> **MAFoElffen said:**
> 
I think planning for the future, that you should add a reserved 10GB partition, formatted as EXT4 to copy an ISO image file to. Then add a loopback menu item to the Boot Menu to be able to boot to it, as a Fall-back Recovery Option. Also re-configuring the Grub Menu, so it always displays, at least for a few seconds. I think this experience has some lessons learned that you don't want to get trapped into again. That way, if you want to add the Boot-Repair ISO (or more) to it as recovery utilities, you can... If you have room reserved in that ISO partition to copy them to...

In the meanwhile, with the SSD removed, you can use Ubuntu from the USB key. 

You can continue to work the support from where you bought it from to try to get into your UEFI BIOS Settings... Eventually, and realistically, you are going to need the ability to be able to get into your UEFI settings. In my search over the past 2-Days, I have seen a bit on Mini PC's where other people cannot get into their own BIOS Setting Screens, even from people at Universities, so I think we might start to see this more for them, for Budget integrated/embedded devices.

Yes Sir, your appraisal and summary of the situation in post #47 is absolutely spot on!

The 'User Manual' which arrived in the same box as the PC is worthless to say the very least. 

It contains various images (spread over 4 x 9" square pages) of the Windows 10 OS and basic advice to novice users about Flight Mode, Cortana, Sleep/restart/shutdown and Security Management. There is also a section entitled BIOS - Setting & Bootmanager; I quote - "Press and hold "ESC" button of keyboard and switch on the device(Press power button ).A screen with the different options will appear. Use option "SCU" for BIOS setting and"Boot Manager" for operating system boot option." There is a troubleshooting section which mentions issues with Windows only.

If all else fails and we never get this sorted out it did come with a SATA cable. I would remove the SSD from the PC and then install an old fat 32 formatted 2.5" HDD on which I would hopefully be able to create a 20gig "/" partition and divide the rest of the space between a partition for "/home" and the third for various data.

I've been hounding the vendor every day since the 27th July with no success at all.

A quote which I've kept for a long time now &#8220;Create top-grade quality walk on the vogue point&#8221; - Chinese snooker table manufacturer LOL

---

### Post by tahitiwibble on 2021-08-02
> **tea for one said:**
> 
```
sudo systemctl reboot --firmware-setup
Cannot indicate to EFI to boot into setup mode: Firmware does not support boot into firmware
```

You would receive this failure message if you originally booted the [COLOR="#0000FF"]live[/COLOR] session in [COLOR="#FF0000"]Legacy[/COLOR] mode.

Can you confirm that the live session was in [COLOR="#0000FF"]UEFI[/COLOR] mode?

I never saw the code that you mention above. I'm not sure how to recognise whether or not the live session was Legacy or UEFI ..... all I can say is that the PC boots OK with a live 20.04 USB key provided that the SSD is [COLOR="#FF0000"]not[/COLOR] attached.

---

### Post by oldfred on 2021-08-02
Did we ever see what brand the SSD is?
Many SSD need firmware update.
And those vendors have their own site with firmware updates.

---

### Post by tahitiwibble on 2021-08-02
I am trying to post images but with no success :confused:

[IMG]https://photos.app.goo.gl/K5b9neDDQRtPgak67[/IMG]

These are its innards [https://photos.app.goo.gl/oTRiExyd5n5xt8687](https://photos.app.goo.gl/oTRiExyd5n5xt8687) [https://photos.app.goo.gl/6iumojkHU8EiVBRm9](https://photos.app.goo.gl/6iumojkHU8EiVBRm9)

---

### Post by tahitiwibble on 2021-08-02
I have discovered something new today. All componants installed i.e. SSD, RAM etc

1/ Power on
2/ Hurriedly hit "Power Off" on the Ubuntu purple splash/welcome screen
3/ Hurriedly hit "Restart" on the Power Off dialogue box
4/ Tap tap tap tap DELETE key

This procedure has shownn me various procedures on the black boot? log? and I'd like to show you images of the screens if it would be of any use!?

Here are the links:- 

[https://photos.app.goo.gl/iuTT1Hz9MX9vmYYh9](https://photos.app.goo.gl/iuTT1Hz9MX9vmYYh9) 

[https://photos.app.goo.gl/G5qZ1YMUo8rAZddq7](https://photos.app.goo.gl/G5qZ1YMUo8rAZddq7) 

[https://photos.app.goo.gl/NEGytp1xSV3ze3Ui9](https://photos.app.goo.gl/NEGytp1xSV3ze3Ui9) 

[https://photos.app.goo.gl/waY5DMq2Xatw52Gr8](https://photos.app.goo.gl/waY5DMq2Xatw52Gr8) 

[https://photos.app.goo.gl/ej5xedYy6Usor1tUA](https://photos.app.goo.gl/ej5xedYy6Usor1tUA)

---

### Post by oldfred on 2021-08-02
If you use the Forum's Go Advanced editor, you can use the paperclip icon to attach screenshots. Post #4 , also no larger than1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

It looks like NVM express is a standard but could be any of various brands. 
[https://nvmexpress.org/portfolio_category/ssd/](https://nvmexpress.org/portfolio_category/ssd/)
Cannot see details. Does it show a brand and model?

---

### Post by tahitiwibble on 2021-08-03
I see 3 components on the SSD

1 silver in colour which I suppose is the controller, marked

2102
SM2263XT G AC
TB7H03.00
CH      24N

and what I presume would be the 2 x 256gb chips that are marked

29F02T2ANCTJ1
190527   E5 
and vertically is written HX5F1

Also marked on the NVM sticker which I had peeled off is marked "M.2 Solid State Drive 512GB"

So apparently one of these:-

[https://nvmexpress.org/portfolio-items/toshiba-xg5-client-nvme-m-2-2280-ssds%e2%80%8b/]("https://nvmexpress.org/portfolio-items/toshiba-xg5-client-nvme-m-2-2280-ssds%e2%80%8b/")

[https://nvmexpress.org/portfolio-items/mte662t-mte662t-i-m-2-ssd/]("https://nvmexpress.org/portfolio-items/mte662t-mte662t-i-m-2-ssd/")

On the underside of the SSD ccard I see SM2263XT_BGA132X4_M2_V01_6L_R0426

---

### Post by tahitiwibble on 2021-08-03
@oldfred there is nothing that I have found on this page that is identical to what I have

[https://nvmexpress.org/compliance/]("https://nvmexpress.org/compliance/")

I would have expected them to show somewhere 'Toshiba' or Transcend' if mine is genuine.

---

### Post by tea for one on 2021-08-03
> **tahitiwibble said:**
> I never saw the code that you mention above. I'm not sure how to recognise whether or not the live session was Legacy or UEFI ..... all I can say is that the PC boots OK with a live 20.04 USB key provided that the SSD is [COLOR="#FF0000"]not[/COLOR] attached.

As mentioned in post 53 by MAFoElffen, when you are in a [COLOR="#0000FF"]live[/COLOR] session, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```
The response will be either UEFI or BIOS

---

### Post by tahitiwibble on 2021-08-03
> **tea for one said:**
> ```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

The result is UEFI

The link below goes to a video of what happens when I 'catch' DELETE when booting from a 20.04 USB drive. This is only possible when I have removed the SSD from the computer.

[https://photos.app.goo.gl/KBSWJuK4j6mPXWYh6](https://photos.app.goo.gl/KBSWJuK4j6mPXWYh6)

Sorry for the audio.

[COLOR="#FF0000"]Also[/COLOR] hitting any of the keys EXCEPT the normal alphabet allows me to switch between the process shown in the video and the Ubuntu "Checking Disk" screen.

---

### Post by oldfred on 2021-08-03
Did a Google search on SM2263XT which looks like the model number of your SSD.
Every page was Chinese and Google translate did not do the best job.
[https://translate.google.com/translate?hl=en&sl=zh-CN&u=https://post.smzdm.com/p/aoo8nxzm/&prev=search&pto=aue](https://translate.google.com/translate?hl=en&sl=zh-CN&u=https://post.smzdm.com/p/aoo8nxzm/&prev=search&pto=aue)

Scrolling text is the boot process which also is saved in log file.
That normally is not shown when quiet splash are on linux line in grub.
But recovery mode or second line in grub menu uses nomodeset and shows all the boot process as it also removes quiet splash.

---

### Post by tahitiwibble on 2021-08-03
Yes I did some research also and found what appears to be the same SSD as I have. I wonder why they felt like they had to rebadge it though?

[https://bbs.szgalaxy.com/topic/30c6d64f-c024-4335-98e9-b4d552d9c242/83501daa-19a4-40e6-ba67-a27bfe10014d.html](https://bbs.szgalaxy.com/topic/30c6d64f-c024-4335-98e9-b4d552d9c242/83501daa-19a4-40e6-ba67-a27bfe10014d.html)

[https://www.sohu.com/a/418866766_491494](https://www.sohu.com/a/418866766_491494)

[https://www.163.com/dy/article/FMMEGHHG0511D04U.html#](https://www.163.com/dy/article/FMMEGHHG0511D04U.html#)

---

### Post by MAFoElffen on 2021-08-04
Of the type I mentioned... [https://www.amazon.com/SSK-Aluminum-Enclosure-Adapter-External/dp/B07MNFH1PX/ref=sr_1_6?dchild=1&keywords=ssd+m.2+heatsink+enclosure&qid=1628063302&s=electronics&sr=1-6](https://www.amazon.com/SSK-Aluminum-Enclosure-Adapter-External/dp/B07MNFH1PX/ref=sr_1_6?dchild=1&keywords=ssd+m.2+heatsink+enclosure&qid=1628063302&s=electronics&sr=1-6)

The one I have eyes on for myself... On my own wishlist.

That way, you could boot to the USB key with the LiveCD environment (with your SSD not installed) and when in the Environment. Then with your SSD in the Adapter, safely plug in your SSD (via USB) and do what is needed to remove grub from the SSD or remove all partitions, so it is fresh...

Then everything can be shut down, and reassembled. SSD would failover to the USB Key to Install on the (then) internal SSD.

---

### Post by MAFoElffen on 2021-08-04
What perplexes me, is that when an Ubuntu LTS Install image is created to a USB Key (or Burned to a DVD)... 

If created to boot as Legacy BIOS boot, then the initial screen is like this: [https://www.itzgeek.com/wp-content/uploads/2020/04/Ubuntu-20.04-Initial-Screen.png](https://www.itzgeek.com/wp-content/uploads/2020/04/Ubuntu-20.04-Initial-Screen.png)

If created to boot as UEFI BIOS boot, then the initial screen is like this: [https://ubuntuforums.org/attachment.php?attachmentid=288918&d=1628065146](https://ubuntuforums.org/attachment.php?attachmentid=288918&d=1628065146)  (Same as attachment)

Note- If created to boot as both, the mode it boots as is one of those two screens, indicating the mode it booted as.

...Which that second (UEFI) initial screen is a Grub menu. Notice the last option on that menu, which gives the user the ability to go into the UEFI BIOS to make changes to the BIOS Settings, before the install. The same can be done from a Grub Boot Menu on an UEFI BIOS machine, by pressing <C> at the Grub menu to get to a Grub command prompt, typing: fwsetup<Enter>

It will then just go to the BIOS setup screen, straight from Grub... Those two versions of initial screens are mandatory and are there (specifically) to give the user installing a chance to interact with things to make any needed adjustments and such... Before the LiveCD Environment starts.

You have confirmed that it is booting the LiveCD USB key as UEFI... DO you *not *get this initial screen as a Grub menu like the attachment when it boots from the LiveCD USB key?

---

### Post by tea for one on 2021-08-04
> **MAFoElffen said:**
> You have confirmed that it is booting the LiveCD USB key as UEFI... DO you *not *get this initial screen as a Grub menu like the attachment when it boots from the LiveCD USB key?

Yes, very good observation.
I am equally as perplexed as you and very interested in the progress of this thread.

A quick internet search of the PC yielded this description:-
> TOPTON Mini PC AMD Ryzen R5 3550H R7 2700U Vega 10 Graphic 2*DDR4 M.2 NVMe Gaming Computer Windows 10 4K HTPC HDMI2.0 DP AC WiFi

If Windows 10 is mentioned, then the UEFI firmware should be standard issue (and accessible from the Grub menu in the live environment)?

---

### Post by oldfred on 2021-08-04
You do not now get the purple BIOS screen with the newest Ubuntu.
Ubuntu 20.10 Groovy Gorilla - Grub used for both BIOS & UEFI

The purple screen was from a syslinux boot loader.

Do not know if grub has different colors for BIOS & UEFI, but it will be grub menu.

---

### Post by MAFoElffen on 2021-08-04
@oldfred

I tested an Ubuntu 21.04 ISO on Two VM's- Legacy (1) and UEFI (2). 
 
[LIST=1]
[*]If it boots as Legacy, you get a Grub Menu that does not have a menu option to go to the Firmware settings. If you drop to the Grub CLI and enter "fwsetup", it will get a "Command not found." 
[*]If it boots as UEFI, then the Grub Menu does have the "UEFI Firmware Settings" menu option and if you drop into the Grub CLI, you can use fwsetup to get to it. 
[/LIST]
 That seems to be a visual and functional difference at that point,, whether it has used grub-pc for legacy or grub-efi for UEFI. At least for Debian Branch. RHEL Branch does not add an UEFI Firmware Settings" menu item at all. On them, if it is UEFI, you have to go to the CLI (or add it as a custom menu item manually).

---

### Post by tahitiwibble on 2021-08-05
> **MAFoElffen said:**
> Of the type I mentioned... [https://www.amazon.com/SSK-Aluminum-Enclosure-Adapter-External/dp/B07MNFH1PX/ref=sr_1_6?dchild=1&keywords=ssd+m.2+heatsink+enclosure&qid=1628063302&s=electronics&sr=1-6](https://www.amazon.com/SSK-Aluminum-Enclosure-Adapter-External/dp/B07MNFH1PX/ref=sr_1_6?dchild=1&keywords=ssd+m.2+heatsink+enclosure&qid=1628063302&s=electronics&sr=1-6)

The one I have eyes on for myself... On my own wishlist.

That way, you could boot to the USB key with the LiveCD environment (with your SSD not installed) and when in the Environment. Then with your SSD in the Adapter, safely plug in your SSD (via USB) and do what is needed to remove grub from the SSD or remove all partitions, so it is fresh...

Then everything can be shut down, and reassembled. SSD would failover to the USB Key to Install on the (then) internal SSD.


I would have already done this if I could beg, borrow or steal an adapter such as you show. Alas.

---

### Post by tahitiwibble on 2021-08-05
> **MAFoElffen said:**
>  You have confirmed that it is booting the LiveCD USB key as UEFI... DO you *not *get this initial screen as a Grub menu like the attachment when it boots from the LiveCD USB key?

The command that you guys asked me to run in terminal came back **absolutely** as "EUFI".

I made a couple of videos and I apologise for the poor lighting and quality (my wife and granddaughter are both within ear shot and hate me using bright lights late at night) the first one shows booting the computer with the corrupted SSD installed.

[https://photos.app.goo.gl/PBxUoNT9FME9GykD7](https://photos.app.goo.gl/PBxUoNT9FME9GykD7)

This second one was booting the live USB with no SSD

[https://photos.app.goo.gl/ZBrZjM7vWXmJKdCZ8](https://photos.app.goo.gl/ZBrZjM7vWXmJKdCZ8)

Both times simply powered on with no interference from yours truly.

---

### Post by tahitiwibble on 2021-08-05
> **MAFoElffen said:**
> DO you *not *get this initial screen as a Grub menu like the attachment when it boots from the LiveCD USB key?

Negative

---

### Post by tahitiwibble on 2021-08-05
> **tea for one said:**
> Yes, very good observation.
I am equally as perplexed as you and very interested in the progress of this thread.

A quick internet search of the PC yielded this description:-


If Windows 10 is mentioned, then the UEFI firmware should be standard issue (and accessible from the Grub menu in the live environment)?

The exact machine that I bought with the 8GB DDR4 512GB NVMe option and the Ryzen 5 3550H processor is in the link below. I asked for Ubuntu to be preinstalled and they put on version 19.1

[https://www.aliexpress.com/item/4001271665728.html?spm=a2g0s.9042311.0.0.1cec4c4dxp9mQH]("https://www.aliexpress.com/item/4001271665728.html?spm=a2g0s.9042311.0.0.1cec4c4dxp9mQH")

---

### Post by tea for one on 2021-08-05
I studied your videos as best as I could - they were a bit small to see exactly what is happening.

It looks like there is a blank dialogue box before the 2 minute disk check occurs.

The live session grub menu should appear before the disk check.

Also, it appeared that you were using a live USB with Ubuntu 20.04 (Focal Fossa) - is that correct?

As you have new hardware, I am wondering if 21.04 would yield the grub menu in a live session?

---

### Post by oldfred on 2021-08-05
If you press escape key, right after computer starts, after vendor's UEFI screen but before grub normally would appear, do you get grub menu?
And then can you boot the second (or third if sub menu) recovery mode entry? That adds nomodeset as boot parameter, so you boot into terminal without gui.

---

### Post by MAFoElffen on 2021-08-05
I viewed both videos... "Quiet Boot" is turned on...  He doesn't get the First Panel of his USB Boot media, which may be from how he created the media(?)

Here's what has been said previously:

By the Vendor- That on boot, use the <DEL> Key to get to the BIOS Setup. That would imply that it is AMI BIOS or similar. With the newest version of the AMI BIOS, press <DEL> or <ESC> to enter the BIOS Setup. The <TAB> key will toggle the Quiet Boot" off to display the Post Messages. F8 is the hotkey for the EFI Boot menu...

But if nothing is connected to the device at all, meaning no SSD, and No USB device, then there should be 1-2 devices left for it to boot from... The NIC and UEFI Firmware... Unhooking both those may be enough for it to stall, looking for those two missing devices, to get into an EFI booot menu... Or not. But might be worth a try.

But here's a caveat that I thought of while watching those two videos... It reminds me of several of mine, that have AMI BIOS... At the initial start of POST- It init's the Northbridge... CPU, APU, MEM, Then it transitions to the Southbridge with the USB bus/devices, PCI Bus, NIC's, other Ports. (In that order...) Note that the Northbridge in current, is no longer on the motherboard. It is inside the CPU, so the path to it is now ls almost nothing.

On mine, on the first boot (after the first power on), the USB Keyboard isn't always recognized in time "to hear" if I'm pressing hotkeys to try to get into the BIOS Setup or to pull up the EFI Boot Menu... So **"if"** I plan on using the EFI Boot Menu or need to get into the UEFI BIOS Setup... on mine, I just let it try to boot the first time, and in those first few seconds of POST, press <Cntrl><Alt><Del> once, maybe a few times, to let it cycle a reboot a few times... Then press the <Del> key to get in. Notice that I didn't say power on and off, but rather do/cause a reset. Something about the board still being powered  on, and cycling, causes this condition.

The reason I can see that on mine, is that I have Quiet Boot turned off, and I have an RGB LED lit keyboard, so I can see when it is trying to initialize the keyboard, and see the timing of the onscreen POST messages... He doesn't. have those indicators.

Something about the second or later POSTs (after the initial POST)... Lets the Keyboard initialize the Keyboard faster, for it to start recognizing keys (better)...

I know that may sound a bit "quarky"... I'm trying to describe something, that happens in a matter of mere seconds... and the timing has to be just right. There is only about a 1-2 second window there, that it waits for that Hotkey. If I look in my BIOS, the default wait time setting for that is only 1 second.

Past that, start hitting the <Left-Shift> key to try to get the Grub Menu...

The suggestion to upgrade to 21.04??? He "IS" running stable on a  20.04.2 LTS LiveCD USB image... That points that the installed image on  his SSD has problems. Not that 20.04.2 itself is the problem. And he "is" running stable on that LiveCD environment without any nomodeset or any other boot parameter options... Running Ubuntu isn't his big problem. Being able to boot from USB, then install to his SSD is his challenge and problem. 

Why? Back to the original chief complaint... He can't get into his BIOS Setup to change anything, such as his boot order...

---

### Post by MAFoElffen on 2021-08-05
Wasn't there a Grub Boot Image (as a rescue disk) at one time? I was thinking that there  was. Something that he can burn to one of his "other" USB keys (he has  multiple now). That he can boot to, get to a Grub Command Prompt, to  boot into his UEFI BIOS. 

If not, I can create an image for  him... I mean, I used to create custom Distro's. It's not hard. I could  then share it with him, to try. 

But if it is already out there... He  could just download to try.

Let me do a quick search on that... [https://www.supergrubdisk.org/](https://www.supergrubdisk.org/)

EDIT: It has a Boot to UEFI Firmware Settings...

---

### Post by tahitiwibble on 2021-08-05
> **tea for one said:**
> I studied your videos as best as I could - they were a bit small to see exactly what is happening.

It looks like there is a blank dialogue box before the 2 minute disk check occurs.

That is a dialog box saying that the screeen resolution is wrong; but it is. Yeah sorry for the quality of the videos.

> **tea for one said:**
> The live session grub menu should appear before the disk check.

No, I have never seen the grub menu since these shenanigans started. The USB key boot defaults to the desktop like in the video with no SSD connected.

> **tea for one said:**
> Also, it appeared that you were using a live USB with Ubuntu 20.04 (Focal Fossa) - is that correct?

As you have new hardware, I am wondering if 21.04 would yield the grub menu in a live session?

Correct about 20.04 on the USB. I'm downloading 21.01 right now and will test.

---

### Post by tahitiwibble on 2021-08-05
> **oldfred said:**
> If you press escape key, right after computer starts, after vendor's UEFI screen but before grub normally would appear, do you get grub menu?

I have never seen either the vendor's UEFI screen or the grub menu. When I booted the computer up for the first time it was already installed with Ubuntu 19.1 and I immediately tried to upgrade the system to 20.04. That's when it all came falling down.

---

### Post by tahitiwibble on 2021-08-05
> **MAFoElffen said:**
> I viewed both videos... "Quiet Boot" is turned on...  He doesn't get the First Panel of his USB Boot media, which may be from how he created the media(?) [COLOR="#0000FF"]The USB boot media was created with Rufus from "ubuntu-20.04.1-desktop-amd64" disk image.[/COLOR]

Here's what has been said previously:

By the Vendor- That on boot, use the <DEL> Key to get to the BIOS Setup. That would imply that it is AMI BIOS or similar. With the newest version of the AMI BIOS, press <DEL> or <ESC> to enter the BIOS Setup. The <TAB> key will toggle the Quiet Boot" off to display the Post Messages. F8 is the hotkey for the EFI Boot menu... [https://we.tl/t-VhdBg0ViWB]("https://we.tl/t-VhdBg0ViWB") [COLOR="#0000FF"]this is the how-to the vendor sent me. Note that he restarts from Windows which I never had on the computer.[/COLOR]

But if nothing is connected to the device at all, meaning no SSD, and No USB device, then there should be 1-2 devices left for it to boot from... The NIC and UEFI Firmware... Unhooking both those may be enough for it to stall, looking for those two missing devices, to get into an EFI booot menu... Or not. But might be worth a try. [COLOR="#0000FF"]The only things that I can take off the motherboard is the RAM, the wifi/bluetooth card, the backup battery and the fan unit. There is one red jumper switch over 3 pins and therefore 2 possible permutations.
[/COLOR]
But here's a caveat that I thought of while watching those two videos... It reminds me of several of mine, that have AMI BIOS... At the initial start of POST- It init's the Northbridge... CPU, APU, MEM, Then it transitions to the Southbridge with the USB bus/devices, PCI Bus, NIC's, other Ports. (In that order...) Note that the Northbridge in current, is no longer on the motherboard. It is inside the CPU, so the path to it is now ls almost nothing.

On mine, on the first boot (after the first power on), the USB Keyboard isn't always recognized in time "to hear" if I'm pressing hotkeys to try to get into the BIOS Setup or to pull up the EFI Boot Menu... So **"if"** I plan on using the EFI Boot Menu or need to get into the UEFI BIOS Setup... on mine, I just let it try to boot the first time, and in those first few seconds of POST, press <Cntrl><Alt><Del> once, maybe a few times, to let it cycle a reboot a few times... Then press the <Del> key to get in. Notice that I didn't say power on and off, but rather do/cause a reset. Something about the board still being powered  on, and cycling, causes this condition.

The reason I can see that on mine, is that I have Quiet Boot turned off, and I have an RGB LED lit keyboard, so I can see when it is trying to initialize the keyboard, and see the timing of the onscreen POST messages... He doesn't. have those indicators.

Something about the second or later POSTs (after the initial POST)... Lets the Keyboard initialize the Keyboard faster, for it to start recognizing keys (better)...

I know that may sound a bit "quarky"... I'm trying to describe something, that happens in a matter of mere seconds... and the timing has to be just right. There is only about a 1-2 second window there, that it waits for that Hotkey. If I look in my BIOS, the default wait time setting for that is only 1 second.

Past that, start hitting the <Left-Shift> key to try to get the Grub Menu...

The suggestion to upgrade to 21.04??? He "IS" running stable on a  20.04.2 LTS LiveCD USB image... That points that the installed image on  his SSD has problems. Not that 20.04.2 itself is the problem. And he "is" running stable on that LiveCD environment without any nomodeset or any other boot parameter options... Running Ubuntu isn't his big problem. Being able to boot from USB, then install to his SSD is his challenge and problem. 

Why? Back to the original chief complaint... He can't get into his BIOS Setup to change anything, such as his boot order...

z

---

### Post by tahitiwibble on 2021-08-05
> **MAFoElffen said:**
> Wasn't there a Grub Boot Image (as a rescue disk) at one time? I was thinking that there  was. Something that he can burn to one of his "other" USB keys (he has  multiple now). That he can boot to, get to a Grub Command Prompt, to  boot into his UEFI BIOS. 

If not, I can create an image for  him... I mean, I used to create custom Distro's. It's not hard. I could  then share it with him, to try. 

But if it is already out there... He  could just download to try.

Let me do a quick search on that... [https://www.supergrubdisk.org/](https://www.supergrubdisk.org/)

EDIT: It has a Boot to UEFI Firmware Settings...

I'm trying to digest the information on the supergrubdisk site. It looks scary although very intersting.

---

### Post by bobunderwood99 on 2021-08-05
> The 'User Manual' which arrived in the same box as the PC is worthless to say the very least. 

It contains various images (spread over 4 x 9" square pages) of the  Windows 10 OS and basic advice to novice users about Flight Mode,  Cortana, Sleep/restart/shutdown and Security Management. There is also a  section entitled BIOS - Setting & Bootmanager; I quote - "Press and  hold "ESC" button of keyboard and switch on the device(Press power  button ).A screen with the different options will appear. Use option  "SCU" for BIOS setting and"Boot Manager" for operating system boot  option." There is a troubleshooting section which mentions issues with  Windows only.

Have you tried holding down ESC then pressing the Power button (from powered down)?

---

### Post by MAFoElffen on 2021-08-06
> **tahitiwibble said:**
> I'm trying to digest the information on the supergrubdisk site. It looks scary although very intersting.

All you would need it for is to boot from, then using the option on that, to boot into the UEFI BIOS Setting Menu of your computer... Yes, it would be mass overkilss, just to do that. But You can't seem to do it manually so... LOL

This may help you get there... to change at least the boot order. So that your USB is first and SSD second in the order.

---

### Post by tahitiwibble on 2021-08-06
> **MAFoElffen said:**
> This may help you get there... to change at least the boot order. So that your USB is first and SSD second in the order.

I just tried the live USB supergrubstick and it wouldn't boot up for some reason. I tried 2 different pen drives and burning the image with both Rufus and Etcher and no go :(

---

### Post by tahitiwibble on 2021-08-06
> **bobunderwood99 said:**
> Have you tried holding down ESC then pressing the Power button (from powered down)?

I have yes, that and a thousand other variations of key combinations.

---

### Post by tahitiwibble on 2021-08-06
I'm losing hope ladies and/or gentlemen. I can't thank you enough for all the help that you've proffered.

I'm backing up all that I have on a 1 TB SATA external HDD to anything that's lying around and available, then I'm going to format it, take it out of the case, and then I'm going to install it in this here junk PC and try to install Ubuntu on it from a live USB stick. I just hope that the BIOS/UEFI is going to allow it!

---

### Post by tea for one on 2021-08-06
Another suggestion - although a bit bizarre:-

Remove internal ssd
Boot into live session
Install to a [COLOR="#0000FF"]second[/COLOR] USB device larger than, say, 16GB
Full installation with user account
Double check that you that you have installed in [COLOR="#0000FF"]UEFI mode[/COLOR]
Ensure that [COLOR="#0000FF"]Grub will be visible[/COLOR] when installed USB is booted
Power off when done
Remove live USB
Boot USB with user account

Does Grub appear?

Edit: I wrote this before seeing your post 81 - similar idea

---

### Post by bobunderwood99 on 2021-08-06
> **tahitiwibble said:**
> I have yes, that and a thousand other variations of key combinations.

Does it have a PS/2 port? If so, can you try a PS/2 keyboard?

---

### Post by MAFoElffen on 2021-08-06
> **bobunderwood99 said:**
> Does it have a PS/2 port? If so, can you try a PS/2 keyboard?
Thank you for your enthusiasm. If you read posts from the thread, you would see that it is a very new Mini PC (Post #1 and many other posts have the model and specs), that only has USB... 

Many things have been tried, which you are now repeating. Please read the posts from the thread. Maybe you might see something that hasn't been suggested yet, or have a fresh perspective(?)

---

### Post by MAFoElffen on 2021-08-06
I have another idea. It goes along with "Tea For One"... If he uses one of his USB Keys, and installed to it as a USB storage device as USB Storage, Ensures it installs as UEFI... Install from the Try Desktop... Also it would need to install as a minimal install. That would still leave run, but this would be for a persistent toolset. Then before the reboot, goes back to the desktop...

At that point, (or after a reboot to the LiveCD USB) then he can mount the system of the Installed system on that USB Media... and change the Grub menu to always display (type=Menu, instead of hidden) then update Grub...

Then when he boots from that, he would have an UEFI Grub menu to get into his UEFI Firmware Setup... To change the boot order, for him to be able to boot from USB, with his SSD installed/connected.

Not understanding why this still does not boot from that SuperGrub USB, or any other USB media besides the Ubuntu LiveCD... The above may not boot... Just as another External Drive may not work. Easier to find out if it will temporarily do it to a USB key that an External Drive.

My other concern of connecting an external drive, if it is SATA, rather than SSD, without connecting to an externally powered USB Hub, is that the current draw may be to much for that Mini PC... I mentioned that it doesn't have conventional power supply right? And that (my guess, because he didn't confirm) it looks like the power supply to it is external... So the current would be going through the board to the external source...  (Such as to a tablet, notebook or laptop.) Non of the options of this say anything except SSD internally, which would be far less of a current draw. Am I the only one concerned about that? Just being cautious for his investment.
###
EDIT: I'm going to test this here, with 21.04, a few different ways, to a USB key, and see what might be easiest for him. Maybe as (1) With Rufus as persistent LiveCD... (2) as installed as a USB Storage device.

---

### Post by MAFoElffen on 2021-08-07
Well, heck... LOL. 
Test, #1. I created a LiveCD image using Rufus,  using the Ubuntu 21.04 Desktop LiveCD ISO and set to GPT partition, EFI  boot, 4GB persistence... When burning with the currently new version of  Rufus, it gives a message saying that Grub2 version on the ISO is older  than the Version in Rufus, so I selected the newer version of Grub2...  On booting an UEFI system with it, the Grub Menu displays, but the UEFI  Firmware Setup menu item is not there. Dropping down to a Grub Command  prompt, I can enter "fwsetup" and it does boot to the UEFI BIOS Firmware  Settings page of the computer. Booting of the system, I see that the  Timeout is set to 10 seconds and type as hidden. Since it is a live  environment, even with persistence, you cannot update Grub Settings.

Test  2: It is possible. The installer, without workarounds, says it's not  possible to install to a USB Flash Drive... but if you trick it, it  does. I installed it as if it was a GPT/EFI system. And it booted fine,  but...

It is not really a workable solution "performance wise".  With current USB Flash Drive spec's, even if I used USB3.1, for the USB  Flash drive itself, the effective read speed of the drive was 60mbs and  the write speed was 30mbs. _It was torture_. I could change and  save anything as if it was any other drive, but the performance of it  was not anything I would recommend to anyone.

It reminded me that  there is still a need to create a LiveCD of a Text-Based minimal Linux  System that runs on minimal resources, or to create an image based  system like that of RaspPi, that is a compressed image... which both load  th compressed image into a RAM Disk, to run from, and the later uses a  pivot on shutdown, that saves the persistence of any changes the  compressed system image. (notes to myself) That is how the LiveCD and  that image gets it's performance, as usable. Avoiding the Read/write  limitations of USB Flash drives, except when needed.

Lessons  Learned: Test #1 worked to be able to get into the UEFI Firmware  Settings (manually, from the Grub CLI), if using Rufus to create the  media with those options... See attached photo.

---

### Post by tea for one on 2021-08-07
> **MAFoElffen said:**
> On booting an UEFI system with it, the Grub Menu displays, but the UEFI  Firmware Setup menu item is not there. 

Prompted by your research, I thought that I would also experiment.

Using Rufus 3.15 in Windows 10
My ISO is **xubuntu-21.04-core-amd64.iso** from [https://unit193.net/xubuntu/core/](https://unit193.net/xubuntu/core/) (It is quite small and quick to [COLOR="#000080"]burn[/COLOR] to a USB drive)
Live system booted and UEFI Firmware Settings was available in the Grub menu (line5)
Clicking on UEFI Firmware Settings took me to the UEFI Set-Up as expected.

I successfully tested on two devices:-
Intel NUCi3BEH Desktop (2019 model)
HP Stream 11.6" Netbook (2016 vintage)

It's a bit baffling why your result was different to mine.............?
I cannot believe that it was the different ISO?

---

### Post by tea for one on 2021-08-07
@MAFoElffen

I was very curious why our [COLOR="#0000FF"]live usb[/COLOR] results were different, so I conducted a couple of more tests.

Using Rufus 3.15 in Windows 10
This time using Ubuntu 21.04 Desktop ISO

Select persistence - UEFI Firmware Setup menu item is [COLOR="#FF0000"]missing[/COLOR] in Grub
Do not select persistence - UEFI Firmware Settings was [COLOR="#0000FF"]available[/COLOR] in Grub

I wonder if this is just Rufus?

If you have some free time, can you double check?

---

### Post by tahitiwibble on 2021-08-07
@oldfred @MAFoElffen @tea for one

Good morning/afternoon/evening to you sirs,

I have salvaged a SATA 1 Tb HDD which is installed in my wonderful Chinese mini PC.

I have installed Ubuntu 20.04 from my USB drive.

Debrief to come.

---

### Post by tahitiwibble on 2021-08-07
> **MAFoElffen said:**
> My other concern of connecting an external drive, if it is SATA, rather than SSD, without connecting to an externally powered USB Hub, is that the current draw may be to much for that Mini PC... I mentioned that it doesn't have conventional power supply right? And that (my guess, because he didn't confirm) it looks like the power supply to it is external... So the current would be going through the board to the external source...  (Such as to a tablet, notebook or laptop.) Non of the options of this say anything except SSD internally, which would be far less of a current draw. Am I the only one concerned about that? Just being cautious for his investment.

Sorry for not getting back to you about the power supply. It is an external brick putting out 19v @3.42A.

It's running, as I type this, the PC with an internal SATA HDD.

---

### Post by oldfred on 2021-08-07
Is hard drive seen by installer?
I have an adapter SATA to USB for an old SSD. It worked well for SSD, but power was only from USB port and was not enough to power up an old HDD.

UEFI systems need an ESP - efi system partition. And should use gpt partitioning.
You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting. If drive is MBR partitioned & has data change to gpt will erase all data on drive.

Depending on size of external drive 100 to 500MB for ESP,  and if not large just one ext4 partition for / (root). If larger drive then  30 to 50GB or more for / and rest for /home and/or data partition(s).  Installer defaults to swap file unless swap partition found. Some still suggest a swap partition of 4.1GB and put it at end or far right on drive. Have ESP as first or far left when viewed with gparted. / & /home then can be in middle.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tea for one on 2021-08-08
> **tahitiwibble said:**
> I have salvaged a SATA 1 Tb HDD which is installed in my wonderful Chinese mini PC.

I have installed Ubuntu 20.04 from my USB drive.

That's good news 

Can you reach your UEFI firmware via the Grub menu?

Alternatively, from your installed system, does this command execute correctly?
```
sudo systemctl reboot --firmware-setup
```

---

### Post by Akeo on 2021-08-09
> **tea for one said:**
> Using Rufus 3.15 in Windows 10
This time using Ubuntu 21.04 Desktop ISO

Select persistence - UEFI Firmware Setup menu item is [COLOR=#FF0000]missing[/COLOR] in Grub
Do not select persistence - UEFI Firmware Settings was [COLOR=#0000FF]available[/COLOR] in Grub

I wonder if this is just Rufus?

Rufus dev here.

That's quite an interesting and surprising find, which I have been able to replicate.

Now, whereas I don't have the full explanation for it, I can at least tell you where the problem lies, by advising you to perform the following test.

1. On a drive created by Rufus (in GPT/UEFI mode please), locate the file [FONT=courier new]boot/grub/grub.cfg[/FONT]. This the the config text file that decides whether the *UEFI Firmware Settings* option should appear or not
2. In that file, notice that the [FONT=courier new]menuentry 'UEFI Firmware Settings' { ... }[/FONT] section is guarded by the condition [FONT=courier new]if [ "$grub_platform" = "efi" ]; then[/FONT] where the [FONT=courier new]$grub_platform [/FONT]variable being tested is the output of the [FONT=courier new]grub_platform[/FONT] GRUB command being invoked at the previous line.
3. If you comment the [FONT=courier new]if[/FONT], [FONT=courier new]else[/FONT], [FONT=courier new]fi[/FONT] lines, by adding a [FONT=courier new]#[/FONT] at the beginning of each line, and test the USB again, you will see that the *UEFI Firmware Settings* option now appears
4. This means that, for some reason, on a GPT drive that is booted in pure EFI mode (since you can't boot anything GPT in legacy mode), the [FONT=courier new]grub_platform[/FONT] command somehow does **not** detect that the system was booted in EFI mode.

So it seems to me that there is some kind of issue with [FONT=courier new]grub_platform[/FONT] that makes it confused when it sees a EFI drive with a persistent partition that was created by a utility like Rufus, and leads it to fail to detect that the platform is EFI. Considering that, when you create the drive in Rufus without the persistent partition, the output of [FONT=courier new]grub_platform[/FONT] is correct, I hope you can also agree that the issue is unlikely to be due to Rufus somehow altering the GRUB bootloaders (which I can tell you we do **not** do at all for a drive created for UEFI targets, but I don't mind healthy scepticism), and whereas we do alter [FONT=courier new]grub.cfg[/FONT] to add the [FONT=courier new]persistent[/FONT] and remove the [FONT=courier new]maybe-ubiquity[/FONT] kernel options (which Rufus is **very explicit about in its log**), another simple test, which I obviously performed just in case, will also demonstrate that these changes have nothing do with [FONT=courier new]grub_platform[/FONT] failing to detect EFI boot. And at any rate, even if that was the case, having [FONT=courier new]grub_platform[/FONT] confused by a change with the kernel options would still be a GRUB bug, as it should logically have no incidence on the EFI/non-EFI detection.

Now, the interesting thing is that, if you just create an extra partition manually, [FONT=courier new]grub_platform[/FONT] still seems to properly detect EFI mode, so it's not just a matter of that module being confused by a mere extra partition. And if you delete the Rufus created persistent partition, [FONT=courier new]grub_platform[/FONT] still fails to detect EFI mode, so there's something really peculiar about the way it's going to work or fail

Still, I guess someone will have to log a GRUB bug, because it sure doesn't look to me like [FONT=courier new]grub_platform[/FONT] should fail to report that the platform was booted in EFI mode with the conditions above, and yet this is what we see happening...

---

### Post by Akeo on 2021-08-09
Ah shoot, spoke too soon.

This is actually a Rufus bug where our kernel option editing of lines starting with [FONT=courier new]linux...[/FONT] is a bit too greedy and ends up removing the [FONT=courier new]linux16 /boot/memtest86+.bin[/FONT] from the

[FONT=courier new]else
menuentry 'Test memory' {
    linux16 /boot/memtest86+.bin
}
fi[/FONT]

 section of [FONT=courier new]grub.cfg[/FONT] altogether.

That's a major bug from Rufus right here. Ouch! :icon_frown:

And for some weird reason, if you happen to have an empty [FONT=courier new]menuentry[/FONT] in an [FONT=courier new]else[/FONT] section of a [FONT=courier new]grub.cfg[/FONT], then only that [FONT=courier new]else[/FONT] gets executed regardless of whether the if condition was true or not.

This explains all the weird behaviours we've been observing above. At any rate, I'll make sure to get that issue fixed for the next version of Rufus.

---

### Post by tahitiwibble on 2021-08-17
> **oldfred said:**
> Is hard drive seen by installer?
I have an adapter SATA to USB for an old SSD. It worked well for SSD, but power was only from USB port and was not enough to power up an old HDD.

UEFI systems need an ESP - efi system partition. And should use gpt partitioning.
You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting. If drive is MBR partitioned & has data change to gpt will erase all data on drive.

Depending on size of external drive 100 to 500MB for ESP,  and if not large just one ext4 partition for / (root). If larger drive then  30 to 50GB or more for / and rest for /home and/or data partition(s).  Installer defaults to swap file unless swap partition found. Some still suggest a swap partition of 4.1GB and put it at end or far right on drive. Have ESP as first or far left when viewed with gparted. / & /home then can be in middle.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Apologies for disappearing oldfrend, I became so frustrated that I abandoned the 'recovery operation'. I am going to try to digest and act upon your suggestions and will keep you informed.

---

### Post by tahitiwibble on 2021-08-17
> **tea for one said:**
> That's good news 

Can you reach your UEFI firmware via the Grub menu?

Alternatively, from your installed system, does this command execute correctly?
```
sudo systemctl reboot --firmware-setup
```

Apologies to you also tea for one for disappearing, I still have never been able to get to or even see any trace of the grub menu EVER. I will try your command/code and post the results.

---

### Post by tahitiwibble on 2021-08-17
> **tea for one said:**
> ```
sudo systemctl reboot --firmware-setup
```

So that is a negative. The result was a frozen kind-of-backlighted-obviously-funtioning black screen and nothing more.

---

### Post by tea for one on 2021-08-17
While you are logged in to your [COLOR="#0000FF"]installed[/COLOR] system, can you show us the output of:-

```
 [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy" 
```

---

### Post by tahitiwibble on 2021-08-17
```
uefi
```

---

### Post by tea for one on 2021-08-17
> **tahitiwibble said:**
> So that is a negative. The result was a frozen kind-of-backlighted-obviously-funtioning black screen and nothing more.

Having completely established that you have a UEFI system, the command [COLOR="#0000FF"]sudo systemctl reboot --firmware-setup[/COLOR] tries to function but does not display the UEFI/BIOS set-up.

If the screen is **obviously functioning**, then something else is being obstructive.

I wish I could offer more assistance but I'm stumped at the moment.

---

### Post by bobunderwood99 on 2021-08-20
At this point, I submit your motherboard is flawed. Either a hardware fault or your BIOS firmware is corrupt. I'd contact the vendor or manufacturer [http://www.toptonminipc.com/ ]("http://www.toptonminipc.com/")to get what's needed to reflash the BIOS (or return the system).

---

