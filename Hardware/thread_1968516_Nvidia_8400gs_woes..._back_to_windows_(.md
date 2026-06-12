---
title: "Nvidia 8400gs woes... back to windows :("
date: 2012-04-29
forum: Hardware
---

### Post by fredphoesh on 2012-04-29
Hello guys,

For about 10 days I have been struggling to get my computer to recognise the resolution of my monitor, but alas, Ubuntu does not make this easy, and after reading hours upon hours of forum posts, trying all sorts of things, drivers from ubuntu, drivers from nvidia, terminal after terminal entering all sorts of code which makes no sense to me, things have gone from bad (1024x786) to worse (640x480) and I have re-installed my system 3x to get back to where I was as it seems there is no (easy) way to UN install drivers in ubuntu.

Im really frustrated as I had tried linux years ago and really like the idea, but the amount of messing about one has to do when things are not "just working" is a massive learning curve, and it has got easier since I last tried, but it has a very long way to go before it is as easy as windows... just installing programs requires entering code sometimes... unacceptable imo... one HAS to be able to just download, double click, done.

Anyhow, I cannot get the 8400gs to display at the correct 1280x1024, editing the [COLOR=#000000][FONT=Arial]/etc/X11/xorg.conf file did not help and downloading and installing the driver from Nvidia was a nightmare, it would not let me upgrade as nvidia xserver was running (duh! it should stop it running automatially and just get on with the upgrade)... so I booted to terminal by pressing ctrl-alt-f1 and installed from there, and now I cannot get the bad resolution back, only the even worse one!

lordy, tail is between my legs... the uphill battle has been lost it seems :(

Mark.
[/FONT][/COLOR]

---

### Post by coffeecat on 2012-04-29
@fredphoesh, your post sounds more like a rant than a plea for help, but I can tell you that the nvidia 8400GS works just fine for me, and has done so for the last few Ubuntu releases. Installing the proprietary driver is as trivial as a couple of mouse clicks in the Additional Drivers utility. No further configuration is usually necessary.

It sounds as though you made two mistakes: downloading the driver directly from the nvidia website, and possibly following a poor howto that you found somewhere on the internet.

If you really want help, post back. Getting that particular card working should be simple. If you do post again, what version of Ubuntu were you trying?

---

### Post by Onesimus on 2012-04-29
Or your problems could be a result of the fact that Nvidia have yet to release graphics drivers (96 and 173) for Ubuntu 12.04.  These drivers have dependency problems and won't install.  I don't know which driver your card requires.

I guess we just have to wait until they release them.

---

### Post by coffeecat on 2012-04-29
> **Onesimus said:**
> Or your problems could be a result of the fact that Nvidia have yet to release graphics drivers (96 and 173) for Ubuntu 12.04. 

My 8400GS is working fine with the nvidia-current - 294.40 - repository driver in 12.04. It doesn't seem to need either of the older drivers.

---

### Post by fredphoesh on 2012-04-29
Hello guys, and thanks for the various replies.

I think the problem is that ubuntu will not allow the user to set any resolution that the user wants... so if the monitor is not recognised by ubuntu (as is the case with mine) it gives lower res options.

I'm used to windows where I can test out whatever res the CARD is capable of, and if the display does not like it, it will revert in 10 secs or something...

The problem isnt so much 8400gs as it is the torture a newbie has to go through to do something that is quite simple in windows....

Now I cannot even get back to (lousy) 1024x786 because I installed Nvidia drivers from the Nvidia website for linux, for 32 bit... and followed instructions there.

A rant, yes, partially, I was looking forwards to the experience, but its become a massive series of failures to make it work.

The only way I know how to fix it is to re-install the entire system again.

Anyhoo, your help and concern is appreciated,

tx
Mark.

---

### Post by kurt18947 on 2012-04-29
> **coffeecat said:**
> My 8400GS is working fine with the nvidia-current - 294.40 - repository driver in 12.04. It doesn't seem to need either of the older drivers.

My Nvidia 8400GS  experience mirrors coffeecat's.  Find additional drivers, find nvidia, click 'use current', restart, done.  That might be 4 clicks :).  If I want to change display settings, there should be an nvidia app somewhere in applications or settings.  I have a choice of at least 10 resolutions.

---

### Post by MonkeyPaw on 2012-04-29
> **fredphoesh said:**
> Hello guys, and thanks for the various replies.

I think the problem is that ubuntu will not allow the user to set any resolution that the user wants... so if the monitor is not recognised by ubuntu (as is the case with mine) it gives lower res options.

I'm used to windows where I can test out whatever res the CARD is capable of, and if the display does not like it, it will revert in 10 secs or something...

The problem isnt so much 8400gs as it is the torture a newbie has to go through to do something that is quite simple in windows....

Now I cannot even get back to (lousy) 1024x786 because I installed Nvidia drivers from the Nvidia website for linux, for 32 bit... and followed instructions there.

A rant, yes, partially, I was looking forwards to the experience, but its become a massive series of failures to make it work.

The only way I know how to fix it is to re-install the entire system again.

Anyhoo, your help and concern is appreciated,

tx
Mark.

Sorry that this has been an ordeal, but your experience does not sound typical. On install, Ubuntu should detect your monitor's native resolution use the open source drivers. Once Ubuntu is installed, you can go to System Settings-->Additional drivers and use the recommended proprietary drivers. Ubuntu downloads them, and installs them. I'm not a Windows hater by any means, and I personally don't find MS's way any easier.

I may have missed it, but what version of Ubuntu are you using?  In any event, there is an option to change resolution once you are at the GUI. It's under "Displays."

---

### Post by fredphoesh on 2012-04-29
> **MonkeyPaw said:**
> Sorry that this has been an ordeal, but your experience does not sound typical. On install, Ubuntu should detect your monitor's native resolution use the open source drivers. Once Ubuntu is installed, you can go to System Settings-->Additional drivers and use the recommended proprietary drivers. Ubuntu downloads them, and installs them. I'm not a Windows hater by any means, and I personally don't find MS's way any easier.

I may have missed it, but what version of Ubuntu are you using?  In any event, there is an option to change resolution once you are at the GUI. It's under "Displays."

Hi there MonkeyPaw,

In the last 10 days I stated off on 11.04, then 11.10, and now 12.04, all with the same issue, and each time I installed the Recommended Drivers using the Additional Drivers application - after the default resolution for my monitor was not found.

It seems ubuntu only shows you the resolutions it knows are fine with that monitor, but with an unknown monitor, it gives me two or three low res options...

The closest I (think) I got to a solution was to change the /etc/X11/xorg.conf file by finding out on the web the Horizontal and Vertical sync/refresh numbers for my specific monitor, then doing sudo gymnastics to try to change the code in the file, then reboot... but it did not work. (this code stuff is waaaay more challenging than GUI in windows!)

 Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "CRT-0"
    [COLOR=#000000][FONT=Arial]HorizSync 24 - 80[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
     VertRefresh 50 - 75[/FONT][/COLOR]
   EndSection

Now I have messed things up by installing what is "recommended" by additional drivers, and by installing the official drivers from the manufacturer's website!!

Pretty shocking IMO... and as i mentioned, ive had to start fresh 3x this week!

I don't know what else to try... would Mint or another Linux deal with this differently perhaps?

Tx guys,
Mark.

---

### Post by ahallubuntu on 2012-04-29
Sounds like the monitor is your problem, not the Nvidia card.

What make/model of monitor are you using?

I have seen cases where Ubuntu could not correctly detect the monitor and would therefore not allow me to set any resolution beyond a few defaults.

There are ways to set the monitor in xorg.conf but I have not done this with a recent release of Ubuntu.  (Plus, I dumped that one troublesome monitor and all of my current hardware is recognized just fine by Ubuntu.)

---

### Post by kelvin spratt on 2012-04-29
The main problem is with jockey not removing Nouveau correctly, manually remove it. 
also Ubuntu does not load Nvidia till after you are logged to use the so called start up screen. I used gksu Nvidia-settings to get set my card then made sure it was the same in system settings display and no it does not recognise  my hdmi display Arch/slackware/etc does. so when the resulution is right the login screen has the shakes.
You can of course install in init vi the terminal but ubuntu makes it tricky to do it that way.

---

### Post by fredphoesh on 2012-04-29
> **ahallubuntu said:**
> 
There are ways to set the monitor in xorg.conf but I have not done this with a recent release of Ubuntu.  (Plus, I dumped that one troublesome monitor and all of my current hardware is recognized just fine by Ubuntu.)

Hi ahallubuntu,
Yeah, ubuntu on my HTPC (asrock 330ht) runs at 1920x1080 (though at the moment Im getting an error message about not being able to run xbmc because my graphics driver will not allow 3d graphics or something... but this is a different matter)

but on windows, I merely right mouse click on the desktop, and change to whatever resolution I want... and windows does not recognise my monitor either, calls it Generic NON-PnP monitor...

It's a 19 inch neovo F-419... but all I want to do is go get ubuntu to output 1280x1024... it seems completely impossible, or incredibly difficult at least.

Any xorg.conf pros out there?
tx
Mark

---

### Post by Bandit on 2012-04-29
Try reconfiguring xorg and following the questions to the best of your ability. This should set it up as it would have from the begenning. From terminal use:

> $ sudo dpkg-reconfigure xserver-xorg

**NOTE** I havent tested this on 12.04 yet.. But I wouldnt give bad advice intentionally. But if mine went down hill its the first thing I would try.

---

### Post by ahallubuntu on 2012-04-29
Unfortunately, Ubuntu handles monitors differently than Windows does.

I am not using 12.04 presently (I've only played with the live CD briefly).  I can tell you what worked for me in 11.04 recently, though, to fix the display resolution of a server to 1024x768.  You can try this if you want (but replace 1024x768 and maybe the monitor refresh).  Maybe it will work for you.

More terminal stuff:

```
cd /usr/lib/X11/xorg.conf.d

#if there's already a 04-xorg.conf
sudo cp -p 04-xorg.conf 04-xorg.conf.orig

sudo gedit 04-xorg.conf

```

Here's a generic xorg.conf file I used for 04-xorg.conf:


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver			    "vesa"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option			 "DPMS"
	HorizSync		 47.82
	VertRefresh		 59.92
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		   Depth		24
  	   	   Modes		"1024x768" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen			 "Default Screen"
EndSection

```

Replace 1024x768 with 1280x1024.
I don't know the correct HorizSync and VertRefresh rates for your monitor, but the defaults above may work.  You'll probably want a color depth of 32 not 24 as well.

Then...restart gdm:

```

sudo service gdm restart

```

DISCLAIMER: this could totally mess up your display, so be prepared to back out of it in the following way: restart the computer, hold down the Shift key if you need to get a Grub menu...and choose Recovery Mode from the Grub menu (before booting of Ubuntu starts), then dump into a root shell and replace 04-xorg.conf with 04-xorg.conf.orig that you copied in the beginning - or if that file did not originally exist, delete the new one and restart.

---

### Post by Bandit on 2012-04-29
> **ahallubuntu said:**
> Unfortunately, Ubuntu handles monitors differently than Windows does...............
DISCLAIMER: this could totally mess up your display, so be prepared to back out of it in the following way: restart the computer, hold down the Shift key if you need to get a Grub menu...and choose Recovery Mode from the Grub menu (before booting of Ubuntu starts), then dump into a root shell and replace 04-xorg.conf with 04-xorg.conf.orig that you copied in the beginning - or if that file did not originally exist, delete the new one and restart.

Yes it could and no one should need to manually edit xserver.conf / xorg.conf these days. We used to back 10 years ago and had to manually input mode line to get anything better then 640x480. But these days everything is automated and messing around with the config file can do more harm then good. Follow my method above.

---

### Post by SeijiSensei on 2012-04-29
First, did you try using the NVIDIA X Server Settings application? It's under Settings in my Kubuntu menu. Does it offer you any other resolutions besides the ones you've tried?

If that doesn't help, try opening a Terminal and running the command "sudo nvidia-xconfig" then logout and reboot.  Any better?  Any more resolutions added to the list in the Server Settings options?

---

### Post by fredphoesh on 2012-04-29
> **Bandit said:**
> Try reconfiguring xorg and following the questions to the best of your ability. This should set it up as it would have from the begenning. From terminal use:



**NOTE** I havent tested this on 12.04 yet.. But I wouldnt give bad advice intentionally. But if mine went down hill its the first thing I would try.


Hi Bandit
I tried that, entered my sudo password, got no errors no confirmation, so I rebooted, and still set to 640x480...

---

### Post by Bandit on 2012-04-29
> **SeijiSensei said:**
> First, did you try using the NVIDIA X Server Settings application? It's under Settings in my Kubuntu menu. Does it offer you any other resolutions besides the ones you've tried?

If that doesn't help, try opening a Terminal and running the command "sudo nvidia-xconfig" then logout and reboot.  Any better?  Any more resolutions added to the list in the Server Settings options?

Agreed.. I suggest this after the OP has ran $sudo dpkg-reconfigure xserver-xorg and corrected the messed up xorg.conf file.

---

### Post by ahallubuntu on 2012-04-29
> **Bandit said:**
> no one should need to manually edit xserver.conf / xorg.conf these days. We used to back 10 years ago and had to manually input mode line to get anything better then 640x480. But these days everything is automated and messing around with the config file can do more harm then good. Follow my method above.

No one should have to edit xorg.conf anymore - I agree.  It's a shame I have had to recently in a few cases when nothing else would work.  Unfortunately, some hardware just doesn't play well with Linux, and sometimes hacks are required - just look at all the hacks people must do to get wireless cards working.

OP has already tried a lot of things, and apparently the graphics card works great for people with different monitors.  It really sounds to me like a monitor issue not an Nvidia issue.  But let him try your suggestion first.  Then, if that doesn't work, try mine.  I explained to him how to back out of it pretty easily.

If the OP had a different monitor that had good Linux support, like other posters in this thread who have easy success with the same graphics card, he would never have even needed to post this thread in the first place.

---

### Post by Bandit on 2012-04-29
> **fredphoesh said:**
> Hi Bandit
I tried that, entered my sudo password, got no errors no confirmation, so I rebooted, and still set to 640x480...

Follow Seiji's recogmendation. The Nvidia XServer Settings program should overide any buildt in Unity/Gnome/KDE settings. Hopefully this can fix it. 

My daughter has an old PPC Mac I have to reconfigure the xorg config to get it to show. Chances are you may just have a crazy aftermarket monitor.

---

### Post by Bandit on 2012-04-29
> **ahallubuntu said:**
> No one should have to edit xorg.conf anymore - I agree.  It's a shame I have had to recently in a few cases when nothing else would work.  Unfortunately, some hardware just doesn't play well with Linux, and sometimes hacks are required - just look at all the hacks people must do to get wireless cards working.

OP has already tried a lot of things, and apparently the graphics card works great for people with different monitors.  It really sounds to me like a monitor issue not an Nvidia issue.  But let him try your suggestion first.  Then, if that doesn't work, try mine.  I explained to him how to back out of it pretty easily.

If the OP had a different monitor that had good Linux support, like other posters in this thread who have easy success with the same graphics card, he would never have even needed to post this thread in the first place.

Very true, just hate to send anyone in without proper training. I remember totally screwing mine up a hundred times it seems and the frustraition it cuased me back then. Then again it was 1998 and I had a 19" MagInnovision-from-hell monitor.. :lolflag:

---

### Post by fredphoesh on 2012-04-29
> **SeijiSensei said:**
> First, did you try using the NVIDIA X Server Settings application? It's under Settings in my Kubuntu menu. Does it offer you any other resolutions besides the ones you've tried?

If that doesn't help, try opening a Terminal and running the command "sudo nvidia-xconfig" then logout and reboot.  Any better?  Any more resolutions added to the list in the Server Settings options?

Hi
Yes, usually it offers 1024x786 as the highest, but now it has 640x480 as the highest!!

i just tried sudo nvidia-xconfig and rebooted but that did nothing... 

I still get an error message when I boot up to ubuntu

"Could not apply thed stored configruation for monitors.
None of the selected modes were compatible with the possible modes
Trying modes for CRTC 351
CRTC 351: trying mode 640x480@50Hz with output at 1024x768@50Hz (pass0)
CRTC 351: trying mode 320x240@51Hz with output at 1024x768@50Hz (pass0)
CRTC 351: trying mode 640x480@50Hz with output at 1024x768@50Hz (pass1)
CRTC 351: trying mode 320x240@51Hz with output at 1024x768@50Hz (pass1)

I need to get back to 1024x768 as it was before I tried to fix the problem!

Mark.

---

### Post by fredphoesh on 2012-04-29
Hi there
ahallubuntu, I may have to try this torturous route! THANKS for all the info though.
I think my xorg.conf file is messed anyway, as I edited it previously... so that is whats probably causing me to not even have the 1024x768 now... 640x480 is horrific!
tx
Mark.

> **ahallubuntu said:**
> Unfortunately, Ubuntu handles monitors differently than Windows does.

I am not using 12.04 presently (I've only played with the live CD briefly).  I can tell you what worked for me in 11.04 recently, though, to fix the display resolution of a server to 1024x768.  You can try this if you want (but replace 1024x768 and maybe the monitor refresh).  Maybe it will work for you.

More terminal stuff:

```
cd /usr/lib/X11/xorg.conf.d

#if there's already a 04-xorg.conf
sudo cp -p 04-xorg.conf 04-xorg.conf.orig

sudo gedit 04-xorg.conf

```Here's a generic xorg.conf file I used for 04-xorg.conf:


```
Section "Device"
    Identifier    "Configured Video Device"
    Driver                "vesa"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option             "DPMS"
    HorizSync         47.82
    VertRefresh         59.92
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
           Depth        24
                Modes        "1024x768" 
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen             "Default Screen"
EndSection

```Replace 1024x768 with 1280x1024.
I don't know the correct HorizSync and VertRefresh rates for your monitor, but the defaults above may work.  You'll probably want a color depth of 32 not 24 as well.

Then...restart gdm:

```

sudo service gdm restart

```DISCLAIMER: this could totally mess up your display, so be prepared to back out of it in the following way: restart the computer, hold down the Shift key if you need to get a Grub menu...and choose Recovery Mode from the Grub menu (before booting of Ubuntu starts), then dump into a root shell and replace 04-xorg.conf with 04-xorg.conf.orig that you copied in the beginning - or if that file did not originally exist, delete the new one and restart.

---

### Post by ahallubuntu on 2012-04-29
In 11.04, I found that the exact file "xorg.conf" was not used and always overwritten when I rebooted, which is why I needed to use the one in xorg.conf.d as I noted.

If you want, you can try the method I posted with the exact file and 1024x768 first and see if that works - then try the higher resolution.

---

### Post by fredphoesh on 2012-04-29
> **ahallubuntu said:**
> In 11.04, I found that the exact file "xorg.conf" was not used and always overwritten when I rebooted, which is why I needed to use the one in xorg.conf.d as I noted.

If you want, you can try the method I posted with the exact file and 1024x768 first and see if that works - then try the higher resolution.

Hi,
Thanks! I am busy trying your method...
my system says no such file or directory, but I can sudo gedit xorg.conf.d...
it is blank at the moment.
should I try paste your code, modified with the correct vertical/horizontal numbers?
i see you write yours with a full stop, not a space dash space Like i had them previously!
Mine are
[FONT=&quot]HorizSync 24.80[/FONT]  [FONT=&quot]VertRefresh 50.75[/FONT]
[FONT=&quot]Thanks![/FONT]
[FONT=&quot]Mark.
[/FONT]

---

### Post by ahallubuntu on 2012-04-29
xorg.conf.d is a DIRECTORY not a file.  If you don't have that directory already, my method will not work at all.  As 12.04 is probably different than 11.04 I am not that surprised.

If however you mean you are editing the 04-xorg.conf file INSIDE the directory xorg.conf.d , then it may work as I described.

---

### Post by fredphoesh on 2012-04-29
> **ahallubuntu said:**
> In 11.04, I found that the exact file "xorg.conf" was not used and always overwritten when I rebooted, which is why I needed to use the one in xorg.conf.d as I noted.

If you want, you can try the method I posted with the exact file and 1024x768 first and see if that works - then try the higher resolution.


YESSSSSSSSSSSSSSSSSSSSSSSSSS!!!!!!!!!!!!!!!!!!!!!!!


Impatience is a bit of a problem for me, so I copied and pasted your (modified, see pasted below) code into both xorg.conf.d and xorg.conf
Both were in the usr folder, not the etc folder like I had previously tried... so unfortunately I do not know which one worked as I did both and rebooted.

But for the fist time I HAVE 1280x1024
Friggin yeah!
Thanks for all the help all...
NICE to be able to see a crisp image.
Cheers,
Mark.

Section "Device"
    Identifier    "Configured Video Device"
    Driver                "vesa"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option             "DPMS"
    HorizSync         24.80
    VertRefresh         50.75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    32
    SubSection "Display"
           Depth        32
                Modes        "1280x1024" 
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen             "Default Screen"
EndSection

---

### Post by ahallubuntu on 2012-04-29
It's a shame you had to go through this mess.  Note that if you ever change monitors, you will probably need to blow away this file and revert to get the correct resolution for the new monitor...

---

### Post by fredphoesh on 2012-04-29
> **ahallubuntu said:**
> xorg.conf.d is a DIRECTORY not a file.  If you don't have that directory already, my method will not work at all.  As 12.04 is probably different than 11.04 I am not that surprised.

If however you mean you are editing the 04-xorg.conf file INSIDE the directory xorg.conf.d , then it may work as I described.

Hi
I did not do anything to a file called 04-xorg.conf, only xorg.conf and xorg.conf.d (I must have inadvertently CREATED a file by the name of xorg.conf.d as there is now one in the X11 folder!)

It works now though... i will restart again to make sure.
thanks again
Mark

---

### Post by fredphoesh on 2012-04-29
> **ahallubuntu said:**
> It's a shame you had to go through this mess.  Note that if you ever change monitors, you will probably need to blow away this file and revert to get the correct resolution for the new monitor...

Yeah, I was thinking of that... but if I deleted the file, surely that would mess things up badly, or would ubuntu sort out a new file once it recognises the new monitor?

cheers,
Mark.

---

### Post by coffeecat on 2012-04-29
> **fredphoesh said:**
> Yeah, I was thinking of that... but if I deleted the file, surely that would mess things up badly, or would ubuntu sort out a new file once it recognises the new monitor?

No new file. In fact it's the xserver that looks in /etc/X11, but that's splitting hairs.

The xserver autoconfigures things like video output as the system boots up. In your case the monitor is probably putting out bad (or no) EDID data. If you create an /etc/X11/xorg.conf file, any contents will override any autoconfigured settings. Then it scans the contents of the /etc/X11/xorg.conf.d/ folder (which should be a folder and not a file) and any files there with configuration options will override the auto-settings too.

Most people don't need xorg.conf and associated files, or if they are using a proprietary video driver, the minimal contents will be generated automatically for them. Having to manually edit these files means that you have been very unlucky with your choice of hardware.

---

