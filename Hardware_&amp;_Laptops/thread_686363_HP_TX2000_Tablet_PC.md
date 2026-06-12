---
title: "HP TX2000 Tablet PC"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by Spitphire on 2008-02-03
Anyone out there have any experience with this particular tablet and ubuntu?

I'm considering buying it, would like to see if there are any known **serious** problems.. any comments are helpful...

Thanks,

---

### Post by Murphy2712 on 2008-02-15
Hi,

I just bought it and it's a wonderfull tablet :)
I'm using Debian and there's no serious problems but several ones !
I think it's because this laptop is really new and provide new hardware not yet supported by the kernel (at least the one I use : 2.6.22-3).

Problems :
- I tried to configure touchscreen with no luck
- Wifi worked once ... now it can scan APs but not connect to them :confused:

Works fine :
- dual core cpu
- graphic display (driver nv and nvidia)
- touchpad
- sound & microphone
- ethernet

Don't know (not tested) :
- webcam
- fingerprint reader
- cards reader

I'm waiting for next kernel !
I'll try some other linux to see if I have the same problems... (ubuntu, ...)

---

### Post by unterfuhrer on 2008-02-15
Cardreader works out of box with ubuntu 7.10

---

### Post by Spitphire on 2008-02-15
Hmm... intresting your wifi problem def. sounds fixable... good luck..

Anyone able to get the touch screen working? 

Also, are there any linux based handwriting recogniation programs out there? Something i could scribble some notes in..

---

### Post by MoridinBG on 2008-02-15
Regarding the touchscreen apps, I use xournal for notebook and CellWriter for inputing text.
Xournal is wonderful application, similar to Windows Journal with some nice features like intelligent moving a block of text, which turns out to be priceless at class. I even could successfully replace the paper notebooks with the tablet at school.

CellWriter recognises handwriting and can be used to enter text, anywhere a keyboard can. It is important to note that it recognises separate characters entered in cells. This helps for really high recognition rate, but slight speed of writing penalty.

Regarding the touchscreen issue. Is it wacom tablet? If yes, then it's matter of uncommenting several lines in xorg.conf.

---

### Post by TorchlightJay on 2008-02-15
unfortunately, if you do lspci on this, you'll learn that wacom is on the USB bus. 

Looking at the linuxwacom documentation, there is no support yet for Wacom USB based Tablet PCs at this moment. The news isn't all bad though, I have done some research and it seems that tx2000z is not the first USB tablet PC to come out lately and under the developer's communications, they are already working on it. With the next two releases of Linux Wacom (I'd imagine) and it'll be working. I'd say about the same time Hardy Heron comes out.

---

### Post by Murphy2712 on 2008-02-16
I got wifi working again :) ... on my FON-spot only.
For the others wifi spots it did not connect !

iwconfig wlan0 essid xxx (3 spots tested)
=> iwconfig wlan0 reports no association.
dhclient wlan0 don't found anything

iwconfig wlan0 essid FON_MURPHY
iwconfig wlan0 reports FON_MURPHY association
dhclient wlan0 works...

@ TorchlightJay
How did you install wifi ? (and webcam, fingerprint)
Do you have a good sound quality ?
Do you use 32 or 64 bits kernel ?
Could you post : cat /proc/bus/usb/devices ?

---

### Post by akkas on 2008-03-09
Hi
I also bought tx2000. It is superb!!!
I tried to install ubutu but I am not succeed. Could someone please give me a guide line how to install.

Thanks in advance.

---

### Post by kblcuk on 2008-03-09
Same here.. :(
First time is just stuck in a couple of minutes after I selected the install in the boot screen.
Second time it rebooted while loading some printer drivers (or so...)
Third time there was some error message which I couldn't read because it disappeared immediately.

So now I'm downloading Hardy beta 6 to see whether new kernel helps or not.. :-/

---

### Post by pAt84 on 2008-03-10
Well, as with all HP notebooks load the LiveCD and the Ubuntu install with the following boot options

**noapic irqpoll noirqdebug**

Let me know if this helps you.

Pat

---

### Post by kblcuk on 2008-03-11
okay, hardy worked for me, I even didn't had to use the boot options offered by pAt84.

Problems so far:
* no sound.
The thing seems to be working, but the "mute" led is orange (like "no sound"), event though everything possible is unmuted (alsamixer, etc). the button itself works, and shows whether sound is muted or not, but no sound anyway. Tried reinstalling alsa drivers - no luck. :(

* Wacom touchscreen - since it is assigned to a usb-port, probably we'll just have to wait for a driver to come. :-/

* Wireless - there is Broadcom BCM 4328 card, which has no drivers (surprise). I'm currently on [this guide]("http://www.micahcarrick.com/11-04-2007/ubuntu-d830-install-notes.html#4"), downloading the driver from Dell site - since the original .exe from HP site cannot be extracted.
Hope that helps.

yeah, and there is also some *Smart Common Input Method* application, that constantly switches my layout to some suahili-thaiwanese-whatever other language. very disturbing. :(
Hope it won't be on by default in the final release

**upd: **
sound worked after reboot - seems like I forgot to do that after inserting the snd-hda-intel module...
wireless still doesn't - it is even not listed in the Network Manager. :-/

**upd2:**
now wireless works - with the help of [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")
also, I've used the older driver version (number 5, not 6).
So now only the wacom doesn't work. Apart from that - I can freely destroy the Vista partition now. :-D

---

### Post by pAt84 on 2008-03-12
Hardy really seems to be a catcher on this Tablet.

However, just for those who dont want to install beta software: To get my sound working on my tx2050eg I had to download the newest alsa and compile it myself. This also made the jack-sensing work nicely. That is also true for the ndiswrapper to work nicely. Be sure to use the version 5 driver as mentioned above, release 6 will not work.

Pat

---

### Post by unterfuhrer on 2008-03-12
I don get it.. IF you are using Alpha 6 what driver shuld you use to get the ndiswrapper and wireless to work? I dont understand what driver 5 or driver 6.

---

### Post by kblcuk on 2008-03-13
> **unterfuhrer said:**
> I don get it.. IF you are using Alpha 6 what driver shuld you use to get the ndiswrapper and wireless to work? I dont understand what driver 5 or driver 6.
I just followed [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").
They have all the links to the required drivers.
hope that helps. (:

---

### Post by kblcuk on 2008-03-16
Okay, here we go again.
I had to reinstall the whole thing after libc6 crash couple of days ago (the fix for it worked, but instead I started to get some weird messages about hardware errors... so after couple of days I gave up)

Anyway, still same issues.

Audio-issue was resolved quite easy, by adding this to /etc/modprobe.d/alsa-base
```

options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0

```

however, the wireless doesnt work at all.
I've installed ndiswrapper, and drivers.
```

~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
[/quote]

However, it just doesn't scan the wlan0 or whatever
> 
~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

so I have no idea what else can I do... /-:


**upd:** okay, I've found [this guide]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257"), where it was said that Hardy users have to blacklist the new hardy driver (ssb)

so after these steps:
[quote]
1) Add the new hardy driver to the blacklist (/etc/modprobe.d/blacklist):
```
blacklist ssb
```2) Add these lines to the etc/rc.local file.
```
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ohci_hcd
```


everything works. Apart from that touchscreen.. Still, yippie. :)

---

### Post by unterfuhrer on 2008-03-24
kblcuk, Does all the buttons work? I'm thinking of those at the bottom right och the screen , fn+F4 and the colorchanging on the mute buttom. I can't find any solutions on that in ubuntu gutsy.

I also have problem with the sound, after compiling new alsa drivers and adding 
```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```
to the /etc/modprobe.d/alsa-base the speakers works but not the headphon jack, (mic works) and my last trouble the webcam.

Is the anyone the knows a howto get it to work in gutsy?

---

### Post by kblcuk on 2008-03-25
> **unterfuhrer said:**
> kblcuk, Does all the buttons work? I'm thinking of those at the bottom right och the screen , fn+F4 and the colorchanging on the mute buttom. I can't find any solutions on that in ubuntu gutsy.?

Hi!
Yeah, fn+f7-f8 change the brightness, etc.
But I'm currently in Hardy, so I don't know whether they worked in Gutsy.
Alse, the play-pause-stop- buttons on the bottom right of the screen work in any player for me..

---

### Post by unterfuhrer on 2008-03-25
Now i have it up and runing with hardy, the what dosent work is:
Webcam fingerprintreader and the fact that the cpu scaling randomly selects the speed to 1.6 or 2.0 Ghz

---

### Post by kblcuk on 2008-03-27
okay, more problems... /-:

1. The bluetooth seems to malfunction - whenever I try to connect to it with my mobile, it just never sees the invintation.. :(

2. For some reason, usb mouse is not detected anymore - when I plug it in, nothing happens (even the light in the mouse doesn't light up).

---

### Post by Murphy2712 on 2008-04-02
> **kblcuk said:**
> okay, more problems... /-:

1. The bluetooth seems to malfunction - whenever I try to connect to it with my mobile, it just never sees the invintation.. :(

2. For some reason, usb mouse is not detected anymore - when I plug it in, nothing happens (even the light in the mouse doesn't light up).

For the bluetooth, I've no problem communicating with my gps.

For the usb, I've this problem but not always ! The usb port doesn't seem to scan new devices, so if my mouse is connected at startup it's working fine but if I disconnect it and just reconnect it... nothing ! (but sometimes it works...) I think the mouse problem is the same for any usb device. I've not found any solution except reboot and keep it (usb device like mouse) connected.
I think it's due to the kernel that does not know correctly this new hardware (many USB errors in logs) ... waiting for 2.6.24.1+ kernel.

I just installed the webcam and with Skype it works very fine !
Mini-tuto for the webcam on Debian :
apt-get install linux-uvc-source
cd /usr/src
tar xvf linux-uvc.tar.bz2
cd modules/linux-uvc/
make
make install
modprobe uvcvideo
=> Enjoy with Skype :)
Bonus : add "uvcvideo" (without quotes) in /etc/modules for autoloading video module

Sound OK except jacks.
Wifi OK and with automatic WPA :)
_Using Debian Lenny/Unstable_

---

### Post by gjakuipers on 2008-04-03
Hello unterfuhrer,

is the touchscreen working? how did you do that?


> **unterfuhrer said:**
> Now i have it up and runing with hardy, the what dosent work is:
Webcam fingerprintreader and the fact that the cpu scaling randomly selects the speed to 1.6 or 2.0 Ghz

---

### Post by unterfuhrer on 2008-04-03
sorry gjakuipers, it don't work for me, I just forgott to wright that...

---

### Post by big dizzle on 2008-04-07
plz post if anyone gets the touchscreen working or comes across a thread that has a successful howto!  i am going to get one of these and would like to use linux on it, but it looks like i am going to be stuck using cygwin (i don't want to use windows, but i cant justify the extra money for the laptop over other laptops if i'm not going to use the tablet functionality) :(

---

### Post by Pyroman[FO] on 2008-04-11
So it looks like the latest linuxwacom release supports USB tablet devices, has anyone configured the tx2000z with these new (7.9-9) drivers yet?  I have them installed but can't seem to get my xorg configuration right.

---

### Post by TomtheWombat on 2008-04-13
That touch screen addition is for serial tablets still.  (mostly the Lenovo multitouch screen.)

Luckily, a patch is being worked on specifically for our laptop.  (Thank HP for rock bottom prices.)

Bugtracker:
[http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127?](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127?)

Discussion:
[http://sourceforge.net/mailarchive/forum.php?thread_name=4b5e638b0804090734t490442e8jc44da60df301e580%40mail.gmail.com&forum_name=linuxwacom-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=4b5e638b0804090734t490442e8jc44da60df301e580%40mail.gmail.com&forum_name=linuxwacom-devel)

I haven't had the time to monkey-fart with it this weekend.  I wish you luck! :popcorn:

---

### Post by Umby on 2008-04-14
Hi,
I've HP TX2025el, i'm probing various versions of Kubuntu in this pc and the touchscreen works (not well) in Dapper 6.06 with kernel 2.6.15: 
this is the response of "cat /proc/bus/usb/devices"
[snip ]
T:   Bus=02 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#=  6 Sbd=12 MxCh= 0
D:   Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs= 1
P:   Vendor:0056a ProdID=0093 Rev= 2.44
S.   Manifactured=Tablet
S:   Product=ISD-V4
C:* #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr= 0mA
I:    If#= 0 Alt= 0 #EPs= 1 Cls=03(HID ) Sub=01 Prot=02 Driver=usbhid
E:   Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=7ms
I:    If#= 1 Alt= 0 #EPs= 1 Cls=03(HID ) Sub=00 Prot=00 Driver=usbhid
E:   Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=8ms
[snip ]
in other versions and another kernel the voice "Driver" has "(none)" and the touchscreen not work.

sorry for my dreadful english ;)))

---

### Post by tuxhero007 on 2008-04-17
There is a patch to get wacom usb tablet.
Here you can find a patched wacom kernel module source.
[http://tuxhero.com/?p=5](http://tuxhero.com/?p=5)

---

### Post by gjakuipers on 2008-04-17
can you give some information how to install this?

---

### Post by TomtheWombat on 2008-04-17
[http://ubuntuforums.org/showthread.php?p=4715731#post4715731](http://ubuntuforums.org/showthread.php?p=4715731#post4715731)

---

### Post by pieterdekker on 2008-04-19
How did you all managed to get the sound work properly?

My sounds works partially. For example the startup tune from ubuntu works, but when I receive an e-mail in Thunderbird i got a system beep. And also the sound on/off button on the tx2000 has an orange color, should be blue right? 

And also my headphones jack input (both) won't work either, I got no sound on my headphones, only on my speakers. Even when I put in headphones I hear sound on my speakers.

Sorry for my bad English. I hope someone can help me with this one.

---

### Post by TomtheWombat on 2008-04-19
[http://ubuntuforums.org/showpost.php?p=4411351&postcount=1](http://ubuntuforums.org/showpost.php?p=4411351&postcount=1)

There is a section there on what to add to /etc/modprobe.d/alsa

---

### Post by pieterdekker on 2008-04-20
I've followed the instructions, added the extra line in alsa-base, but the problem still exists. Also after restarting ubuntu.

---

### Post by TomtheWombat on 2008-04-20
your mute button is blue now correct?  Just go into the volume control and turn up the headphone volume.

---

### Post by pieterdekker on 2008-04-20
No, that's the problem, my mute button is still orange...

---

### Post by unterfuhrer on 2008-04-21
do you use the latest ALSA drivers and firmware?

---

### Post by M42 on 2008-04-21
I got my Thunderbird sound to work by going into the options menu and selecting a different sound file.  The default beep had been automatically selected.  This was after I got a blue light on the Mute button.

---

### Post by Kalibur on 2008-04-22
I just got myself a tx2000z So if anyone want to test something am willing to put mine on the line.  Just contact me and am on it:KS

---

### Post by Jiiprah on 2008-04-26
I was planning o buying a tx2000 **if** it worked in Ubuntu.

Does this help at all? It's for USB tablets. Isn't the tablet for the tx2000 use an internal usb connection?

[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

I hope you guys get it working.

---

### Post by Jiiprah on 2008-04-26
Oh and another thing...

does the remote work?

---

### Post by jeust on 2008-04-27
hello guys! is anyone working with the final 8.04 version of ubuntu?


I can't get the wireless to work :\ 

I've followed the guidelines above supplied by kblcuk (thanks man :)) but it still doesn't work...

> 
Code:

~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)


However, it just doesn't scan the wlan0 or whatever
> 
~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



I'm here and i did the next steps but i'm still in the same spot... 


In the [ WifiDocs/Driver/bcm43xx/Feisty No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-9192b3c227e128044894727c4b85a57abee8a0c9) what was your 2nd step?

Mine was Step 2d. 


i will try to reinstall ndiswrapper and drivers...

maybe i should try another version of the kernel. :\

i'm also following [this](http://ubuntuforums.org/showthread.php?t=708726&highlight=tx2000) post... 


cheers

---

### Post by ricankevo on 2008-04-27
I to just purchased a TX2000 and love it so far still trying to get everything setup. 

Two questions for you guys:

Has anyone got the fingerprint reader to work on the amd64 version i haven't been able to find anything?

When the screensaver comes on after about 10 mins the screen will go to sleep once that happens it locks up and I have to reboot?

Any help is much appreciated this thread has really helped me out.

---

### Post by TomtheWombat on 2008-04-27
> **Jiiprah said:**
> Oh and another thing...

does the remote work?

Yes the computer automagicly translate all remote buttons into multimedia key presses.  Perhaps not ideal, but it works without any hassle.

---

### Post by TomtheWombat on 2008-04-27
> **ricankevo said:**
> I to just purchased a TX2000 and love it so far still trying to get everything setup. 

Two questions for you guys:

Has anyone got the fingerprint reader to work on the amd64 version i haven't been able to find anything?

When the screensaver comes on after about 10 mins the screen will go to sleep once that happens it locks up and I have to reboot?

Any help is much appreciated this thread has really helped me out.

I haven't tried the fingerprint reader yet.  I would rather have the webcam working.  (Mine locks up whenever i try to disconnect from the device.)

In order to get back after the backlight turns off, do ctrl+alt+f1 and then ctrl+alt+f7.  Laptop manufacturers get to weird up the hardware and usually require their own drivers.  (ie. you can't use nvidias drivers in windows you have to use HPs.)  Hence the linux nvidia driver is a bit screwy, and who knows if it will ever be fixed.  I would like to see power throttling on the GPU.  Save me a few pennies and battery power.

---

### Post by ricankevo on 2008-04-27
Thanks for the reply!

I didn't have any issues with the webcam it just worked. I've only used it twice though with a program called "cheese" its like OS X's photo booth.

---

### Post by unterfuhrer on 2008-04-28
> **ricankevo said:**
> I to just purchased a TX2000 and love it so far still trying to get everything setup. 

Two questions for you guys:

Has anyone got the fingerprint reader to work on the amd64 version i haven't been able to find anything?

When the screensaver comes on after about 10 mins the screen will go to sleep once that happens it locks up and I have to reboot?

Any help is much appreciated this thread has really helped me out.

fingerprint reader works with fprint ([http://reactivated.net/fprint/wiki/Main_Page](http://reactivated.net/fprint/wiki/Main_Page)), easy to set up and use.

---

### Post by r32inc on 2008-04-29
hello everyone, quick question do any of you get a lock up once your tx2000's suspends or hibernates when it tries to wake up? For some reason my computer just locks out and all i get is a blank black screen for some reason. And i'm forced to hold the power to restart computer.

---

### Post by ricankevo on 2008-04-29
r32inc.........I had the same issue TomtheWobat pointed me in the right direction here is what he said to do:

"In order to get back after the backlight turns off, do ctrl+alt+f1 and then ctrl+alt+f7. Laptop manufacturers get to weird up the hardware and usually require their own drivers. (ie. you can't use nvidias drivers in windows you have to use HPs.) Hence the linux nvidia driver is a bit screwy, and who knows if it will ever be fixed. I would like to see power throttling on the GPU. Save me a few pennies and battery power."

---

### Post by r32inc on 2008-04-29
@ricankevo
Sorry i forgot yo mention that i tried that and i still get the same thing keeps happening.  I put the computer into subspend mode or hibirnation and then i press the space bar or power button to wake it back up and my LCD screen gets no image then i press and hold ctr + alt and f1 then ctr + alt and f7 and yet nothing happens. maybe im doing something wrong? 

I'm very much new to ubuntu hopefully its just a dumb mistake in my part somewhere.

thanks again for the help guys ^_^

---

### Post by r32inc on 2008-04-29
@ricankevo
Sorry i forgot yo mention that i tried that and i still get the same thing keeps happening.  I put the computer into subspend mode or hibernation and then i press the space bar or power button to wake it back up and my LCD screen gets no image then i press and hold ctr + alt and f1 then ctr + alt and f7 and yet nothing happens. maybe im doing something wrong? 

I'm very much new to ubuntu hopefully its just a dumb mistake in my part somewhere.

thanks again for the help guys

---

### Post by TomtheWombat on 2008-04-29
r32.. I'm not sure exactly what the problem is.  I think it is in the nvidia drivers again, though.  I have suspended my laptop twice, and both times the file system was corrupted and I had to reinstall.  (That was 2 or 3 weeks ago on Hardy beta, though.)  Eventually I'm going to install to another partition and try some things out with/without the nvidia drivers enabled.

---

### Post by r32inc on 2008-04-29
@TomtheWombat

Thanks for the reply TomtheWombat

I just reinstalled ubuntu-8.04-alternate-amd64 and once i first entered the desktop ( for the first time just after intial install) without installing any drivers or anything i put the computer into suspend ( clicking the power icon in the top right corner and chosing suspend ) and the computer suspends but when hit any key it wakes up and the same thing happens the screen is black with no image (i know the LCD is on though i can see the black backlight).  When i reboot via holding the power button for 5 seconds i get this error when the " GRUB loader " loads:


GRUB Loading stage1.5.


GRUB loading, please wait...
Error 17
_

And it just stays there. Any ideas as to whats going? I'm dual booting with vista 64bit Ultimate if that makes any difference. I don't know what other information i should include...

upd

I reinstalled again and did the same thing and i got the same thing happen again.

---

### Post by Jiiprah on 2008-04-29
I would use 32 bit Ubuntu Hardy.

---

### Post by r32inc on 2008-04-29
I just reinstalled using ubuntu-8.04-alternate-i386 and still having the same problem after i put the laptop to suspend or hibirnate. The laptop wakes up when i press any key or the on button and the LCD is still black with no image (i didn't put the nvidia drivers yet ethier nor any other drivers).

---

### Post by jeust on 2008-04-29
thanks for all the support guys...

really moving

---

### Post by teras on 2008-05-04
I have (by chance) tried an old live version of ubuntu... and surprise! the pen worked.
Not the touch screen though. So probably this was just a basic mouse-emulation mode.
Probably it doesn't worth to look forward on this issue, if there is a proper solution underway, but I report it here anyways.

---

### Post by Kalibur on 2008-05-04
> **teras said:**
> I have (by chance) tried an old live version of ubuntu... and surprise! the pen worked.
Not the touch screen though. So probably this was just a basic mouse-emulation mode.
Probably it doesn't worth to look forward on this issue, if there is a proper solution underway, but I report it here anyways.

Hold up hold up What do you mean the pen worked but not the touch screen expand on that point please. And which version of ubuntu is this, because am think one could just copy the config files from there and put them in hardy or gutsy you know a bit like I do for xorg.conf and nvidia drivers.
Please more info on this I dont wanna become a vista dependant

---

### Post by TomtheWombat on 2008-05-04
Working digitizer and touch screen instructions here:

[http://ubuntuforums.org/showpost.php?p=4715731&postcount=27](http://ubuntuforums.org/showpost.php?p=4715731&postcount=27)

You need to recompile the kernel module.

---

### Post by teras on 2008-05-05
> **Kalibur said:**
> Hold up hold up What do you mean the pen worked but not the touch screen expand on that point please. And which version of ubuntu is this, because am think one could just copy the config files from there and put them in hardy or gutsy you know a bit like I do for xorg.conf and nvidia drivers.
Please more info on this I dont wanna become a vista dependant

It's Kubuntu 6.10 (DVD version) which happened to be around when I was downloading Ubuntu 8.04, so I gave it a try. What I mean is that the pointer moved around with the pen stick, and I was able to click (although the movement needed calibration somehow), but the usage of touch screen (like with the finger) is not working.

Anyway, as I saw today, there is already a nice solution, so I'll give it a try.


EDIT:
The method mentioned above WORKS!!
Thank you

---

### Post by wabre on 2008-05-08
Could you guys please point out which version you are using? I mean, not only 8.04 but if it's the desktop i386 live version, the alternate or the amd64 versions. That would help a lot finding out in the first place which  version to use best...I suppose desktop i386 8.04 is the best solution.

---

### Post by teras on 2008-05-11
> **wabre said:**
> Could you guys please point out which version you are using? I mean, not only 8.04 but if it's the desktop i386 live version, the alternate or the amd64 versions. That would help a lot finding out in the first place which  version to use best...I suppose desktop i386 8.04 is the best solution.

I am using amd64 version, with no complaints!

---

### Post by usafwilson on 2008-05-16
Alright.. hasn't been a post here in four days!

I have the same laptop and am having the same issues.

I have no sound as well as no wireless.

I'm not even going to bother with the touchpad support.. that's why I kept Vista on my machine.. for OneNote!

---

### Post by unterfuhrer on 2008-05-28
Have anyone solvd the problem that you have to press the ctrl+alt+F1 and ctrl+alt+F7 to start the screen from sleepingmode?

---

### Post by MurDoK on 2008-06-01
Hello all!

I also own a Tx2000es. I have installed ubuntu Hardy 32bits and the most of things currently working.

Here is my contribution:
Installing skype I noticed that the microphone wasn't working properly. I don't know why since some people says that it works without modifying anything.
If I tried to record something using gnome-sound-recorder all that I heard was white noise.

First make sure in your volume preferences you have chosen ATAPI Mic as 'Input Source' (add this option, by default is not shown).
If it doesn't work yet, here[1] is the solution.
You simply do:
"sudo alsa force-unload; sudo modprobe snd-hda-intel"

And it starts working.


Some minor bugs that I think nobody has solved yet:
-If you disable and enable the touchpad (clicking twice the button), then gnome help center is launched :confused:
-Although volume is muted, the button light is always blue.
-Sometimes volume is too low for me. At least is lower than when you are running windows vista.
-Hibernate and sleep.
-I can't do cpu scaling unless the laptop is connected to the current. (anyone else??)
-gksu and fingerprint (but let's leave it since it's due the integration of fingerprint, pam, and gksu) 
-The two bottom buttons of the screen. They don't even send an event (run xev).
-I have also noticed that under windows vista, if you connect your headphones, then a popup window shows a message saying that you have connected your headphones. How to detect that under ubuntu?

It would be a good idea to create a wiki page about that issues in Tx series, as many of them as related.

That's all for now. Thanks to all who have also contributed in this thread :D.

[1]: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/192382")

---

### Post by freshboi_toti on 2008-06-09
does any1 have a solution to d slimtype dvd problem.......my    tx2000 ain't finding d cd drive it's saying code 10(error). somn bout drivers couldn't b loaded......y'all need 2 help me b4 i lose my mind.

---

### Post by wire604 on 2008-06-11
> **TomtheWombat said:**
> [http://ubuntuforums.org/showthread.php?p=4715731#post4715731](http://ubuntuforums.org/showthread.php?p=4715731#post4715731)

Hello This didnt work out for me... can anyone help me out with that please ?

Let me know what i should provide !

thanks

---

### Post by M42 on 2008-06-11
> **wire604 said:**
> Hello This didnt work out for me... can anyone help me out with that please ?

Let me know what i should provide !

thanks

Did you edit this line to indicate the current kernel that you have installed? 

sudo cp src/2.6.24/wacom.ko /lib/modules/2.6.24-16-generic/kernel/drivers/input/tablet/wacom.ko

You will need to make that modification I believe.  Since I am using 2.6.24-18 I had to change the 16 to 18.

---

### Post by northtownheatre on 2008-06-13
Does anyone know why the wireless isn't working?
I am also having troubles running compiz.

I have the amd Turion 64x2 and am running Hardy 64bit.

---

### Post by wire604 on 2008-06-15
> **wire604 said:**
> Hello This didnt work out for me... can anyone help me out with that please ?

Let me know what i should provide !

thanks

HEHE i got it working :)

---

### Post by siennalizard on 2008-06-26
Hi USAFWilson,

I direct you (and others here) to my growing HOWTO for this laptop series. It discusses things like sound (easy fix) and using ndiswrapper to enable the wireless.

Take a look and post there if you're still having problems:

[http://ubuntuforums.org/showthread.php?p=5261821](http://ubuntuforums.org/showthread.php?p=5261821)

Cheers,
J.

---

### Post by FatherDale on 2008-07-10
> **kblcuk said:**
> I just followed [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff").
They have all the links to the required drivers.
hope that helps. (:

This worked like a charm on my TX2110US. Thank you, sam-bristolwireless, for the knowledge, and thanks to kblcuk for the link!

---

### Post by Murphy2712 on 2008-07-10
Does someone has wireless working with a 64bits kernel ?
I tried several drivers but no one works.

---

### Post by tagno25 on 2008-07-11
I cannot get my tx2000 to even boot Ubuntu 8.04 Hardy Desktop edition

---

### Post by Murphy2712 on 2008-07-12
> **tagno25 said:**
> I cannot get my tx2000 to even boot Ubuntu 8.04 Hardy Desktop edition

Have you tried :

> **pAt84 said:**
> Well, as with all HP notebooks load the LiveCD and the Ubuntu install with the following boot options

**noapic irqpoll noirqdebug**

?

---

### Post by tagno25 on 2008-07-12
> **Murphy2712 said:**
> Have you tried :



?

when I do that it says the CPU or HDD has passed the temperature threshold and is at 60C and then shuts down. to not have it do that I have to use "acpi=off", which I do not want to have to do.

---

### Post by tC_Crazy on 2008-07-17
tagno, do you have the tx2000 or the tx2500? The 2500 has known problems with thermal shutdown, and a workaround without using acpi=off here: [http://ubuntuforums.org/showthread.php?t=845911](http://ubuntuforums.org/showthread.php?t=845911). It may also work for the 2000.

---

