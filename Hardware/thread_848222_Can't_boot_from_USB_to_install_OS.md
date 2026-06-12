---
title: "Can't boot from USB to install OS"
date: 2008-07-03
forum: Hardware
---

### Post by karamu on 2008-07-03
Hi,

This is my first post and while not directly a Ubuntu problem, I reckon the people in these forums know their stuff so I am appealling for help.

I recently picked up a nice second hand Hitachi Flora laptop- lovely and small.

It's a little old and not so powerful so I planned to install Xubuntu rather than the Ubunutu I run on my desktop.

Anyway, the problem is that it refuses to boot from the USB CD ROM drive I have. I have accessed the BIOS and there is an option "Enable USB boot"- I have enabled this. I have also changed the boot order so that the CD ROM is first (before the HD).

However, on the boot sequence menu there is a little circle highlighting the hard drive- nothing I press can select the CD ROM so even when it is plugged in the machine attempts to boot from the local drive (which has nothing on it).

Does anyone know how I can get it boot from the USB CD ROM?

For reference the machine is a Hitachi Flora 210W NL3- I don't think it is available outside Japan. I am reasonably computer competent but far from an expert......

---

### Post by logos34 on 2008-07-03
Here's an alternative way to install ubuntu:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

---

### Post by karamu on 2008-07-04
Thanks for the reply but the problem is that I can't get anything to install- the hard drive has nothing on it so I can't even load Windows and install from that. As I said, it's not directly a Ubuntu issue, more of a hardware one I guess, but I reckon people posting in these forums know what they are talking about!

---

### Post by logos34 on 2008-07-04
oh, I had to guess and figured the laptop probably still had windows on it.

If it won't boot from usb cdrom, then it's probably a waste of time trying to boot from usb stick.

I think your only option is a [netboot ]("https://help.ubuntu.com/community/Installation/Netboot")of some sort.  Or take the drive out and hook it up to another machine and install it there, then put it back.  It might work.

---

### Post by ProbablyX on 2008-07-04
Have you checked the BIOS?

On some systems you must manually enable USB booting

---

### Post by logos34 on 2008-07-04
> **ProbablyX said:**
> Have you checked the BIOS?

On some systems you must manually enable USB booting

he said he already did that...that's whats strange, it refuses to boot from the usb-cdrom (though I wonder if he could boot a usb hard disk)...unless the boot cd is the issue (bad iso/burn, not burned as image, etc)

and then there's this:
> 
However, on the boot sequence menu there is a little circle highlighting the hard drive- nothing I press can select the CD ROM so even when it is plugged in the machine attempts to boot from the local drive (which has nothing on it).

maybe that's why he was able to get it second-hand!

---

### Post by StormPCs on 2008-07-05
[http://en.wikipedia.org/wiki/Hitachi_Flora_Prius](http://en.wikipedia.org/wiki/Hitachi_Flora_Prius)

[http://www.beatjapan.org/mirror/www.be.com/support/guides/hitachi_boot.html](http://www.beatjapan.org/mirror/www.be.com/support/guides/hitachi_boot.html)

The above links may help you out.  It's an old laptop so I am not sure you will be able load Linux on it.  The machine came with Win 98 and BeOS.  You may need a BIOS update as well.  Good luck to you.

---

### Post by logos34 on 2008-07-05
omg, it's ancient.  And maybe linux-proof.  

You got your work cut out for you.  Happy hacking.

---

### Post by karamu on 2008-07-05
Thanks a lot for the input.

Actually the Flora machine listed before is not the same as mine, check out:

[http://www.hitachi.co.jp/Prod/comp/OSD/pc/flora/prod/note/flora210wnl3/index.html](http://www.hitachi.co.jp/Prod/comp/OSD/pc/flora/prod/note/flora210wnl3/index.html)

it originally came with Windows XP but my machine was blank....

I figured out what the highlight mark next to my HD is- it's an expander, letting me see the drive type.

And I have enabled USB boot from the BIOS, put the CD-ROM first in the boot sequence, and the CD I am trying to use works fine in my other machine so I am really at a loss as to what is not working- maybe the bargain I found was too good to be true after all. I am thinking of going back to the store (I have a month's gaurantee but my Japanese isn't that good.....)

Any suggestions would be most welcome!!

---

### Post by okamogu on 2008-09-03
> **karamu said:**
> Thanks a lot for the input.

Actually the Flora machine listed before is not the same as mine, check out:

[http://www.hitachi.co.jp/Prod/comp/OSD/pc/flora/prod/note/flora210wnl3/index.html](http://www.hitachi.co.jp/Prod/comp/OSD/pc/flora/prod/note/flora210wnl3/index.html)

it originally came with Windows XP but my machine was blank....

I figured out what the highlight mark next to my HD is- it's an expander, letting me see the drive type.

And I have enabled USB boot from the BIOS, put the CD-ROM first in the boot sequence, and the CD I am trying to use works fine in my other machine so I am really at a loss as to what is not working- maybe the bargain I found was too good to be true after all. I am thinking of going back to the store (I have a month's gaurantee but my Japanese isn't that good.....)

Any suggestions would be most welcome!!

I also have a Hitachi Flora 210W NL3. Small, but slow. Mine came with a Windows installation, but I installed Xubuntu 6.x in parallel. After upgrading to Xubuntu 7.x, it became very slow, basically unusable. Result: I uninstalled Xubuntu and replaced it with Debian4. How did I install it? I used an external CD drive, connected it through the USB port and booted from the Xubuntu or Debian CD. I didn't try out to boot from a USB stick.
Give it a try.
Problem of the Flora 210W is that it only has 256MB and 24MB are shared video memory. Unfortunately, the RAM is not upgradable.
BTW, if you want to install Windows and still have a Windows sticker on the Flora 210W, you can install Windows XP and then enter the license key (on the label). If any problems occur, just call Microsoft and tell them that you picked up a second-hand notebook and have problems with the Windows installation. I also had to call MS as the installed Windows XP was activated with volume license key that was black-listed. I called MS, explained the situation, told them the license key printed on the label and they explained me how to activate Windows. Good luck and keep us posted.

---

### Post by okamogu on 2008-09-03
Oops. Misread your post and assumed that you wanted to boot from a USB stick.

I connected a DVD/CD drive (Plextor) through USB, booted the notebook and pressed F12 during boot-up. Selected CD-ROM as boot device and the Xubuntu/Debian booted w/o any problems.

I'll check it again when I am home and tell you the CD-drive model. Shouldn't be a problem of the drive though.
What kind of external drive did you use? USB-powered? If yes, I am not sure if the Flora can power an external CD drive. FYI, the Plextor DVD/CD drive that I used is a huge monster of external drive which is plugged into mains.

---

### Post by aranur on 2009-01-22
I can confirm this problem. I too bought the said notebook (netbook, rather) and it won't boot from CDROM drive (which is connected via USB). To eliminate the chances that the behaviour is from late powering up of USB, I even tried with CDROM powered over external power cables.

I figure the issue is bios because the shop that I bought it from said they could only boot it from a special CDROM from hitachi which was included in the original package. The said CDROM however is not available for sale. 

My next option is to redo the bios and that won't be a small feat since my knowledge on bios is sketchy at best. I've downloaded Phoenix bios editor but can't find hitachi bios rom file for that line.

I've found a way to dump the bios to a file but can't turn it into a proper rom format which can be edited by the Phoenix editor. Sure installing Linux on the windows partition could work, but my concern is that should the filesystem crash, I'd want to be able to pull data from the harddisk using tools like photorec or something or fix it using a liveCD. 

I'm still hoping.

---

### Post by andrew_awp on 2009-02-19
I can confirm the same problem. I bought it used in China, but appears to be a Japanese only model. 
digging a bit tells me it is a HITACHI FLORA 210W NL3 motherboard with Phoenix (02/07/03) BIOS. I would like to install xbuntu or Gos.
Sure would like to know what those extra ports on the back and side are. i suspect the back is a video, and the side is some kind of propreitary IDE/dock.

by the way, i tried USB-to-IDE adapter, USB-to-SATA, and USB memory stick, and i think USN-toSD/CF card, and none worked.

someone mentioned netboot, and i tried it and it works, but i ran into installation freezing problems when i was installing from remote location.

---

### Post by linux_tech on 2009-02-19
If you can return the machine and get a better one that would be best.
If not then with 256 RAM, maybe consider puppy linux or maybe install xubuntu from alternate cd.  puppy would probably work better though as it has less memory requirements.

---

### Post by andrew_awp on 2009-02-19
i searched and found that my model FLORA 210W NL3 doesnt have a BIOS update, although the NL4 and 6 does.
see:
[http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.hitachi.co.jp%2FProd%2Fcomp%2FOSD%2Fpc%2Fflora%2Fdownload%2Ftype%2Fflora210w_nl.htm&sl=ja&tl=en&history_state0=]("http://translate.google.com/translate?prev=_t&hl=en&ie=UTF-8&u=http%3A%2F%2Fwww.hitachi.co.jp%2FProd%2Fcomp%2FOSD%2Fpc%2Fflora%2Fdownload%2Ftype%2Fflora210w_nl.htm&sl=ja&tl=en&history_state0=")

by the way, they are not all the prius model. there is an interesting thing on wikipedia about being able to activate BeOS on that model.

also, having just downloaded it, using Unetbootin looks really easy, in case you just want to duel-boot with windows.

---

### Post by aranur on 2009-03-05
I'm still trying to install using netbootin. ubuntu and xubuntu went black-screen-of-death on me during boot. Knoppix 6 worked, yet I was having problem installing lvpm to move the installation to a proper ext3 partition. not a surprise considering how knoppix mixes and matches debian repo like nobody's business.

I'm still trying some other distro, at snail pace considering my internet connection. last resort would be Knoppix6 again plus some apt-get fixing.

---

### Post by karamu on 2009-03-06
I am sorry for not coming back to the thread I started- I was kind of pre-occupied with my main desktop dying!!

One of the previous posts talked about installing Xubuntu and then it running really slowly.

Well, I got a dock with the machine (it is the proprietary port on the laft hand side for reference) which plugs in as USB to my desktop- I can then partition and format the drive.

I used Unetbootin to load the Xubuntu 8.04 ISO onto the drive then booted in and installed fine.

The next problem was the screen resolution- it was stuck at 800 * 600 with a black border. I used sudo displayconfig-gtk to force it to display the correct size but it still ran really sluggishly.

I reckon there is something up with the display drivers as the login screen is all messed up with wierd colours, and it runs sooooo slowly. Using sudo top tells me that Xorg consumes a good 60% CPU when the machine is idle! If I launch the graphical system monitor it is basically 100% with nothing running- as you can imagine opening any programs is painful!!

Now that I know the Unetbootin approach works (at least with Xubuntu) I am going to try
[LIST=1]
[*]Install XP
[*]"lightweight" Linux dist- probaly Puppy
[/LIST]
I don't really want to run Windows but if XP goes in OK I will probably set up a dual boot system- not a lot of HDD space on the machine but I only need it for Word docs and some spreadsheets so should be OK (in fact if XP runs sluggishly I might even install 2000 instead- it should run what I need).

I will post my updates.

---

### Post by karamu on 2009-03-06
Oh, and for reference, the CD ROM drive I was trying to use initially was a mains powered one but didn't work.

---

### Post by aranur on 2009-03-06
Ahh.. lucky you for getting that dock. for the display, my dig across the internet tells me that you might want to install xorg-driver-siliconmotion, or some such, that's assuming your's is the same as mine, NL3 with graphic chip Lynx3DM from silicon motion

edit: my debian packages search tells me its xserver-xorg-video-siliconmotion

---

### Post by karamu on 2009-03-06
In the display config utility it gives me the option of the silicon motion lynx 3dm driver (according to the Hitachi website the display adaptor) but when I select it the screen gets all messed up and the colours are ****ed. But thanks for the suggestion, I'll give it a try and report back.

---

### Post by karamu on 2009-03-06
Nope, as I suspected, the package was already installed and the appropriate driver was selected!

It's getting late tonight- gonna try Win XP via Unetbootin tomorrow- given the machine has a Windows sticker on the case I am hoping it will run better- I guess Hitachi weren't too worried about Linux compatibility when they made the machine- I may try Puppy or some other distro as well.....

Will report back my success (or lack of) to this thread pretty soon.

---

### Post by karamu on 2009-03-08
I tried to install Xubuntu 7.10 using the Unetbootin method but hit the same problem- it ran really slowly- unusable!

I decided against trying Windows just yet and am currently installing Puppy- seems to be going OK....... Fingers crossed!!

---

### Post by karamu on 2009-03-10
I now have Puppy Linux installed and running fine (at a decent speed)-it runs office programs fine which is all I really want the machine to do so I'm going to stick with and forget about Xubuntu- shame though I would have preferred to run that as my Linux experience has all been Ubuntu related. Guess I will get to learn how to work with a different distro which is useful and I didn't have to resort to using Windows!!

---

### Post by aranur on 2009-03-15
I tried again sidux through Unetbootin. The problem at boot was resolved by using boot from iso cheat available at grub. From there on, I installed onto the second partition (I divided the 15GB harddisk in half earlier in winxp). 

After updates, trimming locales and unused modules, trying out lxde and xfce, I'm sticking with xfce. It is still a little sluggish. I suppose puppy linux might prove to be better indeed. 

You know, I hope we can stick around and try to compile vanilla kernel specifically for our line of Flora, in case we could cream more performance. I've never compiled any kernel before, for that reason, I'm hoping we could be our own support group. 

On office apps, openoffice3 takes a long time to load. I've uninstalled it installed abiword instead. I browse with firefox3. 

I've been looking for pointers from other netbook kernel projects and perhaps DSL, the 50MB distro. I'm going to try unetbootin again with DSL. 

A point to consider is faster boot by loading udev later with an already populated /dev

---

### Post by karamu on 2009-03-16
I have tried a few different Puplets and while most work, some won't start X (it fails when probing the video hardware).

I have settled for the time being on Boxpup as I don't really like the look of JWM based varieties.

You're right, Ooo 3 takes a loooong time to load so I'll use Abiword and Gnumeric instead. However, I need the Impress presentation software- unless anyone knows of another Powerpoint alternative?

As for setting up some kind of support group/ compiling a dedicated kernel, that is a good idea. I am willing to contribute but I am not a coder and have limited Linux experience. If there is anything I can do to help I am happy to do so- let me know.

Maybe we could make a Puplet specifically for the Flora? I personally prefer Opera on the laptop (Firefox on my desktop of course) as it is a bit lighter on the limited resources of the machine.

---

### Post by aranur on 2009-03-16
The problem with openoffice, if i'm not mistaken, is the fact that it loads on top of java runtime environment. Abiword, pw (pathetic word), gnumeric, are good lightweight replacements. 

as for presentation, there are four options, I believe. 

[LIST=1]
[*]For one, we can create the pages in html for and display using firefox with F11 (fullscreen). Composing the presentation is a heckle though, plus the need to have a lightweight http server running. a browser named midori, I heard, is lightweight and capable of fullscreen.
[*]Two, export our presentation in flash or executable format and run the presentation independently. But this would mean that we can't edit it on our flora.
[*]three, of course, to find a viable lightweight dedicated presentation software.
[*]EDIT: use lightweight pdf editor and fullscreen pdf viewer
[/LIST]

truth be told, I'm no coder myself. some linux tweaking is possible, so i'll start there. brewing a custom kernel might take some learning and a couple of week to get the first running kernel, but after which, we don't need to upgrade the kernel so much since we're not trying to run to latest software on our flora, right?

btw, debian variant has this software modconf which helps us remove redundant modules. I notice some improvement in graphics after installing  efficeon module. glxgears simply showed discoloured gears before and now it spins at 20 to 30 fps. don't know about pups though.

edit:
I notice that some display probing failure due to refresh rate and resolution problem. you might want to add specific mode lines in your xorg.conf to fix them.

---

### Post by karamu on 2009-03-18
I definitely think there is something wrong with the display adapter- I thought I had Puppy running stably but now it has started to fail to launch X windows after booting the linux kernel and modules.

You mentioned editing my XORG conf file- I have heard about this but just how would I do so to tweak the resolution and refresh rates?

---

### Post by aranur on 2009-03-18
If you want to try it, this is the relevant section of your xorg.conf. It might also help if you drop default depth to 16

the following is from my other notebook, but xorg is xorg. just remember to replace the values to what is in your existing xorg.conf

> Section "Screen"
        Identifier "Screen0" #<--replace 
        Monitor         "LVDS" #<-- replace 
        Device  "Ati Xpress 200m" #<--replace 
        DefaultDepth 24 #<-- you might want to default to 16, to be safe
        SubSection      "Display"
                Depth   8
                Modes   "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Depth   16
                Modes   "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection      "Display"
                Depth   24
                Modes   "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

if you have doubts or tried and failed, you can post your xorg.conf and I'll try to see if i can find the problem.

The above however haven't touched on refresh rate. I don't dare play with that yet since I still don't know the exact model and specification of the LCD device.

at this point, I'm having problem adjusting xdm/gdm cos the login screen looks like it was hit by a hurricane.

I started compiling a custom kernel last night, 2.6.28.8, have to postpone completing it since my wife is using the flora today.

EDIT: by the way, xorg.conf is in /etc/X11/
don't forget to cp it to xorg.conf.bak first, in case you mess up the edit. and you can only edit as root or using sudo. what editor does pup use anyway. debians normally have vi by default though my favourite is nano. ask, if in doubt.

---

### Post by karamu on 2009-03-27
Hi again, sorry about the slow reply- been pretty busy with work the past week. Anyway, I have some success- Puppy Linux is working quite happily with the Flora- I figured out that the reason X wasn't launching was because I had made some changes to the file system- ie it wasn't the xorg file.

So, I haven't edited the xorg file myself- when you first run Puppy it has a wizard to set up the x windows driver- I chose the screen resolution manually but it displays fine. The only issue is that the screen does flicker for a few seconds when X is starting but after that it is totally stable.

As for the presentation software- I installed Ooo 3- it is a little slow to launch but actually not that bad. It doesn't run super fast but is perfectly usable. 

How are you getting on with compiling the kernel? Let me know if I can do anything to help.

---

### Post by lindsay7 on 2009-03-27
I did not see that you already had put Puppy on this computer. I thought I was giving you a new opinion.




If you can get it to boot from a usb drive you might consider setting up Puppy Linus or another small distro to boot and run from the usb drive. I have Puppy Linux set up that way and it works fine on an old laptop that I have.  I think it only requires between 50 and 100 megs of ram to run. And My 8 gig usb pendrive gives me room for storage for doc, music, pics, and whatever.

---

### Post by aranur on 2009-04-02
Haven't succeeded in compiling a proper kernel with only the hardware for the Flora. My first attempt end up with unbootable kernel, the second attempt on kernel 2.4 got stuck with module compile. basically trying to come up with both types of kernel for comparison. fortunately i've recently assembled a soon to be fileserver using phenom 4x, 8GB RAM and 1TB of RAID5. in the mean time. I'm gonna use it to compile the said kernels.

---

### Post by aranur on 2009-04-10
Still work in progress.

In the mean time though, check out what I found so far at [http://mridzuan.livejournal.com/6403.html](http://mridzuan.livejournal.com/6403.html)

---

### Post by zander7990 on 2009-08-08
Have you tried checking the settings on the CD drive?  I know the one I have has to be set so it will boot when starting up and then set again when being in use with an OS.

Also got ubuntu 6.04 running on the flora.  Its all running fine and dandy.  The only problem I have ever had was trying to install XP on the machine.  Always get the BSOD right after it loads the installation and prepares to install windows.

Any find that memory bank for adding microDIMM mentioned by mridzuan??

---

### Post by aranur on 2009-09-09
I've running around ebay looking for the said microDIMM and I was very sure that it was the DDR1 pc2700 333MHz 512MB microdimm. the listing by several sellers on ebay even note that it is compatible with flora 210w nl3. I went looking and found a shop in Lowyat Plaza, Kuala Lumpur that have some ram modules that looks just like the pictures i've found on ebay.

unfortunately, when I remove the cover to try the module out, it was way smaller than the socket. it seems like the socket is almost as wide as a normal sodimm, minus the notch, like the common sodimms. back to square one. I've really been hoping to find a ram for a little upgrade. I've even bought a 2.8 inch HDD I'm keeping to replace the current HDD when it fails.

---

### Post by matt.matolcsi on 2009-09-29
Very exciting to find a thread on the Flora 210W NL3. I picked up one of these in Akihabara about three years ago in a fit of exotic laptop lust. 

Although it is too anemic to use daily, it is a gem to travel with and has started conversations that would've never happened otherwise. (The best was when we met the Lonely Planet author for Mongolia whilst sitting in a cafe in Ulaanbaatar.) 

I can confirm that neither USB stick nor CD boot work; However, netboot does. Installing through the docking station also works, but is painfully slow. 

I've ended up creating a fairly customized Gentoo install. The trick to getting useful video performance out of the graphics adapter is to select EXA as the acceleration method, not the default XAA. Haven't tried UXA. 

XFCE is probably too slow, forget GNOME or KDE. I'm using IceWM, which works well enough for what it's supposed to do. For a browser, Konqueror has been the best compromise between graphics and responsiveness. 

Incidentally, the Transmeta virtual-machine implementation is ever-so-slightly buggy. If you compile your own software, you have to target an i486 with mmx extensions, *not* pentium-mmx. This is second-hand from an old Gentoo forum, but these compiler options have never failed for me. 

If anyone is really interested, I can get the notebook out and post the xorg.conf.

---

