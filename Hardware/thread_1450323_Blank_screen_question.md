---
title: "Blank screen question"
date: 2010-04-08
forum: Hardware
---

### Post by 2much2soon on 2010-04-08
I haven't been able to find an answer to this after googling for like 8 hours over the last two nights, so I joined the forum in hope of getting some help.

I installed Ubuntu 9.10 on a new Gateway laptop day before yesterday and am dual booting between Win7 and Ubuntu.

Everything was fine, install and functional-wise, until I made some changes to my xorg.conf file in hopes of getting Ubuntu to display in 1600x900.

(The changes i made to the xorg.conf file were related to the modeline and mode params. I do have a backup of my original xorg.conf file.)

The problem is now, at boot up when I choose to boot into Ubuntu, I get a dark gray screen with a blinking cursor for a few seconds, then the screen goes black completely, and then the screen returns to the dark gray, empty display (with no cursor the second time). And then it just stays like that.

So, I can get into the Grub2 shell, and ls to my /etc/X11/ directory (and cat both my xorg.conf and xorg.conf.bkp files) but what I want to do is overwrite xorg.conf with the backup and hopefully make my blank screen go away.

Is this possible to do in the Grub2 shell? As in, is there some way to overwrite my xorg.conf with the backup?

And is this the right way to solve this problem?

BTW, When I load my install .iso disk, I get the same practical result; I end up at a blank screen.

Thanks for any help.

---

### Post by emanuel.b on 2010-04-09
Did you make sure to install the restricted graphics drivers first?

---

### Post by 2much2soon on 2010-04-09
> **emanuel.b said:**
> Did you make sure to install the restricted graphics drivers first?

I didn't.

But everything was working fine until my ill-advised edits the xorg.conf file, if that helps understand the situation any better...

BTW, I am very new to Linux (but have been a sw developer for quite a few years).

---

### Post by emanuel.b on 2010-04-09
Ok, from the shell, you can edit the file using 'nano'. It's a terminal based text editor. If you remember the changes you made, you should be able to fix the problem...

---

### Post by 2much2soon on 2010-04-09
I may have mis-spoke in regard to the Grub2 shell as my experience is so minimal

What I am referring to is the sh:grub that is accessible from the boot menu when typing the character "c". 

That seems to be the only place I can get to, that I am aware of, to do anything.

If I knew how to get to a terminal where I could enter standard Linux commands I think I could run mv etc/X11/xorg.conf.bkp xorg.conf and be done with it?

---

### Post by emanuel.b on 2010-04-09
If I am not mistaken, their is a recovery mode, where Ubuntu dosen't launch the x-server, but instead goes directly into a terminal. I know it's there, because I once screwed up my computer by installing the wrong graphics card, and I had to un-install it by using the recovery mode...

---

### Post by 2much2soon on 2010-04-09
I have tried booting into recovery mode, without any luck.

When I boot into recovery mode, several pages of textual info scroll down the screen, mostly too fast to read, then I get the blank screen again like in regular boot mode.

---

### Post by emanuel.b on 2010-04-09
Well, if you can't boot into recovery mode, it looks like your only option is to reinstall Ubuntu. I'm sorry. You can back up all you files from your Home folder to a flash drive from the live CD, if needed...

---

### Post by 2much2soon on 2010-04-09
LOL, I tried reinstalling.

I can get to the install screen from my iso CD and click "Install", and then everything goes blank just like when I am trying to boot the OS. I can hear the CD drive chug away for awhile but the screen just stays blank.

I also tried the "demo" on the CD and get the same result.

I looked around at the Grub2 manual but didn't find anything too useful there. They do have a mailing list, though, and I might try that. 

Maybe I am barking up the wrong tree, but there must be a way to overwrite my xorg.conf file with the original, functional commands, from the Grub shell I can get to. 

Was also thinking maybe thinking that the commands to overwrite the xorg.conf file need to be stored in a script and run in that shell? I am hoping some Grub expert has some tricks up their sleeve to pull this off...

---

### Post by emanuel.b on 2010-04-09
Ok, hold up, Did the Ubuntu cd work before you messed up the X.org file?

---

### Post by 2much2soon on 2010-04-09
Yep, everything worked fine. I just couldn't leave well enough alone and had to try getting the resolution a bit prettier...

---

### Post by emanuel.b on 2010-04-09
OK, this is turning into somthing really strange. There is no reason that the messed up installation, should keep you from booting to the live cd. Do you have a monitor laying around? You should plug your laptop into a monitor, then boot from the live cd.

---

### Post by 2much2soon on 2010-04-09
Hey, I really appreciate all the help. I will try this as soon as I can (may be a few days due to other commitments).

Win7 still boots and runs with no display problems, BTW, on the same laptop.

---

### Post by emanuel.b on 2010-04-09
Oh, so you're running a dual boot? Well, if you could find a way, I'd just wipe the Ubuntu partition, then try re-installing it. Sorry I could'nt help you out...

---

### Post by 2much2soon on 2010-04-09
And just so I don't lead anyone astray with the translation of my problem, I can still boot up with the cd, it is just after choosing any of the options (Install, Demo - those aren't the exact strings but you probably get my drift) the screen goes blank just as if I am booting from the hard disk.

---

### Post by 2much2soon on 2010-04-09
Seems like one of the cryptic commands listed in the Grub2 shell may be able to wipe out the partition. You can certainly id the partitions in there...

---

### Post by 23dornot23d on 2010-04-09
Use the Live CD ..... to boot into Ubuntu .....

open a terminal window 

then type in ............

cd /etc/X11/

sudo gedit xorg.conf

and put the xorg.conf back to how it should be ....

or if you know where the copy is and can copy it into the /etc/X11   directory

sudo thunar

snter your password .... it will give you a warning you are running as root and change to a red background

(you are only going to use it for this one thing so its ok)

pick the backup file and rename it to xorg.conf

and put it back into the directory - (altering the xorg.conf should not have messed anything else up)

/etc/X11/

if you are missing gedit or thunar 
type in 
sudo apt-get install gedit
sudo apt-get install thunar

hope one of these methods helps you get back your display

---

### Post by 2much2soon on 2010-04-09
Interesting, I had a similar issue with my first Ubuntu foray a few months ago.

I installed XUbuntu on an old x386 machine with an ancient Nvidia card. When I ran the software update for the Nvidia drivers, I got a similar blank screen problem. 

But in that scenario, I was able to just boot to the cd and reinstall with no problem.

---

### Post by 23dornot23d on 2010-04-09
It should boot from the CD ok as it 

**does not use** the xorg.conf on the hard disk .......

---

### Post by 2much2soon on 2010-04-09
Yes, I would think it would boot from the cd, but it just goes to the blank screen when choosing any options on what I have been referring to as the "cd boot screen". That is the screen that appears when booting from the cd drive and allows you to install Ubuntu, run it as a demo, check memory, etc.

And just so I am being perfectly clear, the cd I am referring is the iso image I downloaded  from the Ubuntu web site and burned to a cd. 

That is what is also referred to as the "Live CD", correct?


I am very new to Linux and am still lost with most of the terminology.

---

### Post by 23dornot23d on 2010-04-09
Ok we will try something else ...
( I know you said its a Gateway computer - but I would like to know what graphics card you have in it )

I booted from the live cd too ..... F4 ...... the function key on the top row allows for different graphic modes
at start-up ....... did you try any of those ..... there is a safe mode ..... from what I remember

We can try this ...... to start with to see if you can open a console  ......... 

basically so we can enter commands in it , similar to the dos prompt in windows .... 

So ....

Boot it up as you would normally ..... until you get to the blank screen ........

and press these keys all together at the same time ......... CTRL + ALT + F1

do you get any text on the screen at all ?  

like a .....

$ 

for instance

_________________________________________

 After re-reading what you wrote in an earlier text and have a feeling what you refer to as the grub2 screen may be the normal 
console screen (what text if any do you have on it) if this is correct and you can get into the etc/X11 directory .........

the command you need is cp ( it stands for copy )

**cp    xorg.conf.backup    xorg.conf**

you could try this as it may give you what you wanted ..... by doing so if you are at a console
  ........ this will overwrite the existing xorg.conf with your backup file ...... 

if that is what it is named  ..... xorg.conf.bkp ...... or was this what you remembered .....
if you renamed it to xorg.conf.bkp then the following is what you need to type ....

cp    xorg.conf.bkp    xorg.conf


as its usually backup ...... here is an example of mine ........ some are also followed by the date that
they were created on too .........


[IMG]http://i40.tinypic.com/1o6ccy.jpg[/IMG]

---

### Post by 2much2soon on 2010-04-09
I have tried combinations of ctrl+alt+F1 with no luck.

The only screen I can access to type the commands into reads (exactly) as follows:

--------------------------------------------------------------------------------------------------------
                                  GNU GRUB version 1.97~beta4
 [ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ESC at any time exits.]

sh:grub
--------------------------------------------------------------------------------------------------------

As far as I can decipher, this is the Grub2 shell. Typical Linux commands like "cp" or "mv" don't run and an error message of "unknown command '<command>'" is returned after entering them.
If you type 'help' at the prompt a long list of supported commands is returned but nothing that appears to do any file manipulation.

---

### Post by 23dornot23d on 2010-04-09
Ok thankyou ..... you confirmed its the grub 

and the graphics card is ?

and what happens when you press F4 after booting the live CD ?

---

### Post by 2much2soon on 2010-04-09
I believe the graphics are integrated/onboard. The processor is an Intel I3.

Oddly, you can run lspci in the Grub shell but it doesn't seem as detailed as I recall when running in Ubuntu. lspci returns and entry for a VGA controller, but no details other than that.

I could log into Win7 and track that down, though, for certain.

I have tried booting in safe graphics mode with the cd, if that is what you are referring to with F4? Same result; blank screen.

BTW, I really appreciate the help. Worst case, I am going to know way more about Grub and the boot process than ever before, LOL.

---

### Post by 23dornot23d on 2010-04-09
F4 - Safe graphics mode .... or a resolution like 800 x 600 .... not sure what other options there were 
but I guess you have tried them all out ........

The way things are ..... if it was my computer ..... 

I would try burning another Distro Linux mint or Mandriva 2010 ....... to a CD

Just to see if they can pick up the graphics card ...... running either one as a live CD

so we are able to get to a console window to work ...... as far as I know it cannot be done from the grub console
 

We need a console of some kind so that we can then restore your original configuration ....... 

I have never known anything like this where it runs ok once then it will not after altering the

xorg,conf ........ if you can burn a CD .....  burn Mandriva 2010 .... to try first ......

I have used Mandriva on laptops with graphic cards that do not pick up in other distros and its worked.

(Linux Mint is based on a Debian UBUNTU mix so will possibly be similar to what we are already seeing ......)

Unless there's anybody else following this that knows of a better or quicker solution ......

Best I can do at the moment ......

---

### Post by 2much2soon on 2010-04-09
I was thinking about this while driving around at lunch time. 

Trying to run the demo shouldn't look at any configured setting on the laptop's hard drive, right? It should be running purely from the environment on the cd? Weird.

First I am going to burn another Ubuntu cd and see what happens with it. In case mine got corrupted somehow between the original, functional install and now.

At the suggestion of the Grub mailing list, I did edit my Grub settings for recovery mode and replaced "splash" and "quiet" with "single" to try to reach a command prompt, but no luck. Had no affect.

---

### Post by 23dornot23d on 2010-04-10
The only time I ever had a similar situation was with a S3 virge video card ,,,,, some Distributions  would pick it up  ,,,, others it would not .....  [http://en.wikipedia.org/wiki/S3_ViRGE](http://en.wikipedia.org/wiki/S3_ViRGE)

VESA [http://en.wikipedia.org/wiki/VESA](http://en.wikipedia.org/wiki/VESA) settings usually work on a lot of cards ..... the easiest and quickest less painful ways for me when I started with linux twenty odd years ago was to find a distribution that worked with my hardware  .......

Usually we use a live CD to let us know if all of the hardware picks up alright .......** if it does not** ..... then maybe that distribution is not the best one for that PC ,,,, but saying that its not necessarily impossible to get them working ....  

You said you altered the xorg,conf which is exactly what I would do ...... but I usually just adjust the resolutions and get my cards working  ...... nowadays I always stick with Nvidia cards ......

Everything is to do with compatibility when we run different LiveCDs it gives us a good feel for LINUX working ok on the computer we have bought  ...... the good thing here is that you have had it working once ..... not sure what resolution it was working at as you did not say .....

But you obviously weren't happy with it ..... otherwise you would not have altered the xorg.conf .....

The bad thing is that it is not working from the live cd using all the different options  ....... burning another CD the same will only help if its a problem with the CD itself - 

and if so should have shown error messages on the screen - but as you say if your screen just goes black you will maybe not know, and seeing we cannot see a log file because you cannot get a terminal up ..... that again is out of the question.

Hopefully a new CD will work and all your problems will be solved ..... if not then you are back to square one ..... then I advise again trying Mandriva or Linux Mint ...... once we can get one Distribution working we can get them all working ........ as we can get to see why one works and another does not ,,,,,,, 

Also I would now like to know what was in the original xorg,conf that got you up and running in the first place.

---

### Post by 2much2soon on 2010-04-10
Alright, I am back, posting from my original install. Yeehaw

I did create another iso cd, booted into demo mode, and restored my original xorg.conf file.

My original iso cd may have been corrupted, or my face maybe should be really red and I just wasn't giving it long enough to start up. 

I had to wait 5+ minutes until I finally got a sorta scrambled display and then the demo mood desktop appeared. I located the correct xorg.conf file and gedit't back to its original configuration.

Now, at some point today I ran across a possible solution for actually getting my 1600x900 resolution functional.

There was a post on this board from someone with the same laptop as mine who posted a link to some information on updating the kernel a couple of revs ahead of what is in the standard 9.10 distro. This seems to be allowing 1600x900 with my HW configuration.

So, do I feel lucky?

Thanks for all the help, that made my first experience at fixing something really great.

---

### Post by 2much2soon on 2010-04-10
this is my original, functional xorg.conf file that is in use now:
---------------------------------------------------------------------
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
--------------------------------------------------------------------

I obviously blew away the ill-advised mode/modeline changes I applied and don't remember them.

---

### Post by 2much2soon on 2010-04-10
1024x768 is the max I can currently select.

My first Linux install was a couple of months ago. I think I surveyed a few distros and Ubuntu seemed to be very popular for ease of use. I didn't really consider HW matching, though. And that did come back to bite me slightly.

I had an old P3 that was previously running Win 98 and was just gathering dust. So I downloaded and burned a cd, installed and away I went. 

I did have a problem when installing the nvidia drivers; I got a similar result with the blank screen. But since the remedy I found for addressing that was extremely convoluted, I just reinstalled and had no problems.

I worked in ms shops for a long time and grew weary of their whole deal. After a layoff, when I had the chance to look at things in a different way, I fell in love with Python and to a lesser degree PHP. And that put me on a path that eventually lead to Linux

---

### Post by 23dornot23d on 2010-04-10
Ok great .... it is using the vesa drivers .....

Thanks for posting it .... if we get more information on your graphics card now maybe you will get a better resolution too ...... xrandr 

type this in a console window .......

xrandr -q 

what does it show you .........

---

### Post by 2much2soon on 2010-04-10
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0

---

### Post by 23dornot23d on 2010-04-10
ok whats making you think that you graphics card can handle 1600 x 900 then ....

does it work in windows at this resolution ,,, and can you get more info from windows on the graphics card

In Windows .... something like ...... ( long time since I used it ........ )

System Information ...... Display Driver ....... ?

or maybe video settings ....

---

### Post by 2much2soon on 2010-04-10
Win7 boots extremely fast (at least for now), about as fast Ubuntu, so I can get out of one and into the other pretty quickly.

Yes, it the resolution is 1600x900 in Win7. 

Officially, it is an Intel GMA HD.

---

### Post by 23dornot23d on 2010-04-10
ok looking here [http://en.wikipedia.org/wiki/Intel_GMA](http://en.wikipedia.org/wiki/Intel_GMA)

There seem to be different types ,,,, the numbers after them identify them better ....
once we know for sure the exact one we are dealing with we can then start narrowing things down a little .....

 Intel GMA HD ( ? xxxx ? )

also if possible ..........

What is the exact model name and processor of your computer ........ 

can you do a screen capture in windows showing as much info as possible and post it .....

I will show you how to go about doing it once you have a screenshot available .... of the information

(upload the screenshot to tinypic ...... and pick the url and past it on here)

---

### Post by mikejeckson on 2010-04-10
Hi...Friend:)
First you create another new fresh CD in bootable mode, and then reinstall it....
And after that i hope your problem should be short-out...

---

### Post by 2much2soon on 2010-04-10
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
**00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)**
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

---

### Post by 2much2soon on 2010-04-10
it is a core i3, well it is labeled as that on the case. But I have heard some shipped with core i5.
I will go back to windows and dig around. 2 days of experience with Win7 doesn't equal 10 with xp. The adm interfaces seem somewhat different.

---

### Post by 23dornot23d on 2010-04-10
> **mikejeckson said:**
> Hi...Friend:)
First you create another new fresh CD in bootable mode, and then reinstall it....
And after that i hope your problem should be short-out...


That might not be such a bad idea after scanning through numerous threads ,,,
this in particular ...  [http://ubuntuforums.org/showthread.php?t=1402612](http://ubuntuforums.org/showthread.php?t=1402612)

go towards the end of it as it is rather long

 the 10.04 version of Ubuntu seems to have better support for the GMA HD


Which version of UBUNTU are you running .... now .... which one did you burn ,,,

here is the link to the latest one ..... 

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Its final completion date is the 29th April 2010 ..... its upto you ,,, 
the final freeze date is in 5 days time - 

You could wait or try it now and update the distro on the final release date .....
to check out the full schedule ,,, its in my links below ....

---

### Post by 2much2soon on 2010-04-10
so I couldn't really find much of use in the Win7 Devices applet.
It is a core i3. Would appear, on the Wiki, to be the one right next to "Mobile" and "Arrandale", the Core I3-3X0M, in the GMA HD section. Doesn't seem to be much there on it in the Linux section, though...

---

### Post by 2much2soon on 2010-04-10
here is the resource I ran across earlier
[link]("http://www.linwik.com/wiki/using+the+intel+arrandale+intel+graphics+media+accelerator+hd+with+ubuntu+9.10")

this probably accomplishes the same thing as moving up to 10.04; kernel upgrade that fixes the resolution issue.
I am currently using 9.10

---

### Post by 23dornot23d on 2010-04-10
Great looks like that should solve the problems .......

you are almost there now ..... :)

Let me know if you get stuck with any part of it .......

or just burn the latest 10.04 ... I have - its a good Distro ...

can always do any additional upgrades later on ......

---

### Post by 2much2soon on 2010-04-10
I may just get 10.04.
I don't have any thing installed on this laptop, app wise. No biggie to upgrade and see what happens. Will let you know how it works out.

---

### Post by 23dornot23d on 2010-04-10
I hope that everything works well for you .... :)

( I prefer to do a clean install ..... and usually in a separate partition - if you have room for it ....
just so that I know it is good with my system and setup - this is just my way of working ...........
ensures that I always have a system to fall back to too ..... if need be ......  )

---

### Post by 2much2soon on 2010-04-10
I just saw this thread while searching on "gateway laptop display" LOL.
 
I did the upgrade to 10.04 earlier today and have been wrestling with it off and on since.
 
The initial upgrade attempt failed to pick up all the packages. I could get to a login screen, which was so dim I could barely see it. After logging in, I got the dreaded blank screen again.
 
I am able to boot into Recovery mode. From there I was able to run the repair packages option.
 
But, I still have no display. Am researching this now. Probably should of done a fresh install instead of the upgrade, based on my current results.
 
If there is any good news, my display in recovery mode looks like 16x9, at least, haha.

---

### Post by 2much2soon on 2010-04-11
suppose the first troubleshooting step is to see if the xserver is actually running or not...

---

### Post by 23dornot23d on 2010-04-11
What do you see when you type ......

startx

after you get the $

you still have the original

xorg.conf file 

posted on here ..... its the vesa mode ....

you should be able to copy it back in the etc/X11 directory 

it may even still be there ?

etc/X11/

that should get your display working again .....

if not the messages shown may help to resolve the display problems .....

---

### Post by 2much2soon on 2010-04-11
since I am in a different physical location right now, I don't have another pc to work from while troubleshooting and easily translate the steps and results I am taking. I will have to go back and carefully document each step I took.
 
But, I did start in recovery mode and from root looked at xorg.conf - it appeared to be the same as what I posted, although I am not 100% sure.
 
This is going to sound uber-dumb, but it is late and I can't remember the command I ran (it seemed logical in the context of the screen results I was getting) but noticed an error related to kernel modesetting. I looked at the specified log file and the exact error in the log is:
 
"(EE) VESA: Kernel modesetting driver in use, refusing to load" 
 
so I am poking around at that, haven't absorbed what I have read so far.

---

### Post by 23dornot23d on 2010-04-12
I would do a clean install on a separate partition ..... thats if it all works ok from the LiveCD 

It will give you a better idea if its going to work ok .... and it will only take 30 mins or so to do ......

I spent days trying to sort out my upgrade problems ....  from 9.04 to 9.10 ....... lesson learned ...

I did eventually get almost everything working .... Nautilus proved to be a pain .... but used Thunar ....

The quick way was to do a clean install ...... 

I never looked back ...... keep moving forwards ... best of luck .... :)

---

### Post by totoff on 2010-04-12
dear all, i've read through this forum with great interest, as i run into trouble with 10.04 on an old toshiba laptop with nvidia graphics. unfortunately i'm very new to ubuntu and not very familiar with the command line ... so i'm seeking a step-by-step-advice on how to get rid of the proprietary nvidia driver that brought me into trouble in order to get back to the build-in driver (noveau?) that has worked fine. here is what happend:

1. installed ubuntu 10.04 from scratch getting rid of win and every data on the hd.
2. worked fine
3. installed the proposed nvidia proprietary driver (nvidia-96?)
4. got a flickering, nearly black screen
5. on reboot i was able to boot in recovery mode. but lacking the knowledge to find the right commands to get back to my former install ...
6. for that reason re-installed from scratch - working fine

i would like to give the proprietary drive a second try but would like to be sure that i can go back without re-installing. so if you have any advice that would be very much appreciated.

best, totoff

---

### Post by 23dornot23d on 2010-04-12
@totoff

If I wanted to test something out .... 

I would create a 20 gig partition ....
load the latest  UBUNTU Distro 10.04 to there ...... then try out the drivers ....

Once that you are sure they work and you are happy with the setup

do the same in your working Environment .....

This is my way and works for me ...... 

I have a few versions of Linux on the same machine ..... and rarely get stuck with something that will not work ..... if it does not work on one - it often works on another.

My main Desktop I keep on a USB Drive ....... it has copies of all my work from the other live desktops ...... a sort of up to date work in progress that I can access from any of the other Distros .......

---

### Post by totoff on 2010-04-12
hi dornot, this is a smart idea! i'm not sure if i'm going to give it a try, as i only have 30gb on hd but the idea is clever.

however, as i'm newbie: may i create a second partition if i already have one and what happens to the existing one? and: how to you transfer your desktop (settings?) to a usb stick?

last but not least, just for the sake of interest: how do i get rid of drivers once installed?

best, totoff

---

### Post by 23dornot23d on 2010-04-12
You would probably be better off getting a USB external hard drive .... 500 Gig ..... you can do lots of things then ..... 
IMHO .... they are good value for money and make life a lot easier.

With 30 Gig ..... 

I would probably be stuck with the one system the same as you  ..... so it is difficult to do similar to me ,,, so unless you get a bigger drive ,,, stick with the one partition. Minimum I usually use is 16 Gig for a Distro ..... I use a lot of applications/programs and they soon fill up my space .....

As for removing the graphic drivers - to be honest - I do not know as I have never had to do that.

Someone else may be able to help with that if you post a fresh question on the forum.

---

### Post by 2much2soon on 2010-04-12
I think I would bite off trying to fix my 10.04 upgrade install if I was at home and could easily refer to the interweb on another workstation. But since I am not at home this week, I think I will burn an iso of 10.04 and try a fresh install. 
On my way to downloading the iso...

---

### Post by 2much2soon on 2010-04-13
Alright, I burned a new 10.04 iso, booted into demo mode with no problems, and then did the install from there.

I now have lovely, 16x9 resolution.

One problem so far, when I first logged into the forums here (with Firefox), the laptop locked up completely. I had to do a hard reboot. But no problem after getting back in, so far.

And, this just in, gmail now works in Firefox for the first time for me on Ubuntu. Cool, except I was getting used to Evolution for mail.

So I guess the fix for a lot of Ubuntu install issues is to use a freshly burned iso disk? It has worked for me with both 9.04 and 10.04...


Once again, thanks to everyone who pitched in on this thread. I had heard about the generosity of the Linux/Ubuntu community and now I am a believer.

---

### Post by 23dornot23d on 2010-04-14
I am very happy everything is working right now .... 

do you want to mark the thread as solved ...

Thank you ..... for the nice comments .... :)

---

