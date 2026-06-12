---
title: "Can anyone help me with this TFT? DVI Cable help needed."
date: 2008-11-12
forum: Hardware
---

### Post by BigSilly on 2008-11-12
I've been given an Acer AL1521 TFT monitor with DVI-D input that I'd like to get working with Ubuntu. I have a Geforce 6200 256Mb graphics card also, which says DVI-I.


I've tried removing the Nvidia drivers from Synaptic before I started. I was using a VGA CRT before with them already set up, so I removed them altogether. Then I typed into a terminal ```
sudo dpkg-reconfigure xserver-xorg
``` and turned off the system. I connected the monitor using [this cable]("http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=330284329759&ssPageName=ADME:B:EOIBSA:UK:11"), then restarted the system. It's fine at this point. I then install the drivers again from Synaptic afresh (though I notice I haven't been prompted, and there's no entry for them in Hardware Drivers), and restart X as prompted. As soon as it gets to the GDM the screen goes crazy. The monitor is flashing up "Input not supported", and what display I can see is completely garbled.

What have I done wrong here, and what should I do to fix it? I'm using the VGA lead at the moment and it's OK, but is Ubuntu not compatible with DVI cables? Have I bought the wrong thing?

Your help much appreciated.

---

### Post by doug1212 on 2008-11-12
Hi,
I've used the nvidia settings tool (as root) to set X.
I think DVI input is the way to go as it's digital all the way.

Good luck,
Doug.

---

### Post by BigSilly on 2008-11-12
> **doug1212 said:**
> Hi,
I've used the nvidia settings tool (as root) to set X.
I think DVI input is the way to go as it's digital all the way.

Good luck,
Doug.

Thanks for your reply. I hope you're right!

What settings do I need to make as root here to get this to work properly? Your help here really gratefully received.

---

### Post by doug1212 on 2008-11-12
I was quite luck with my viewsonic as it was detected ok and I just hit the save to X configuration button then then restarted xserver.
The thing is LCD panels only have one native resolution and if it ain't right they though a wobbly.
Doug.

---

### Post by BigSilly on 2008-11-12
Can anyone help me then with this, or am I doomed to CRT headaches!

It's resolution is 1024x768, which is exactly the same as my CRT, so I don't think it's the resolution it's having trouble with. Rather, it's when I install the Nvidia driver again that it goes wonky.

Halp!

---

### Post by doug1212 on 2008-11-12
This may be a bug just been reading the nvidia howto, check out the trouble shooting section:

[HTML]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia[/HTML]

[HTML]https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/82312[/HTML]

---

### Post by BigSilly on 2008-11-12
I can't get this going, so I'm back on the CRT. I don't know what it wants, and without knowing fully what I should do I've disconnected it for now. I tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` reset eveything back to scratch, and re-installed the drivers again, but it just gives me a shocking resolution that I cannot manually change. It doesn't even recognise my Nvidia card!

Bizarrely, I thought I'd give my Mandriva 2009 Live CD a shot, and it worked with it just fine. I had to manually select the "Force DVI" option in the Hardware settings, but the resolution and screen looked fantastic after that for the short while I used it.

Pity I can't get on with Mandy 2009. Ah well.

---

### Post by BigSilly on 2008-11-14
Bumping this up in the hope that someone will be able to help. I've spent God knows how long now messing about with this, and still cannot get a proper display with DVI.

Basically -

Acer AL1521 TFT via **VGA** + Nvidia 6200 + proprietary drivers (177) = fine. Monitor and card both seem to be recognised correctly. 3D OK.

Conversely -

Acer AL1521 TFT via **DVI** + Nvidia 6200 + proprietary drivers (177) = incorrect resolution (640x480 rather than proper 1024x768 ), and no options anywhere to change it. Monitor and graphics card don't seem to be recognised correctly, and nvidia-settings has no higher res available.

What's the likely cause here, and is there a way to fix it? I've tried a load of Google and forum solutions, such as manually editing Xorg.conf and even going back to Hardy, but so far nothing has worked. The monitor is pretty old (2002). Is it just not up to the task? Is there a "Force DVI" option in Ubuntu as there is in Mandriva?

Thanks in advance.

---

### Post by starcannon on 2008-11-14
I have a few old Nfren 15" TFT monitors that I have to take care of, on those monitors I had to set up custom modelines; I used this utility to do that for me:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

I'll post the link to my solution for that monitor, it should help you do the same and show you where to put the newly generated modeline and associated entries in the xorg.conf:
[http://ubuntuforums.org/showthread.php?t=956823&highlight=nfren](http://ubuntuforums.org/showthread.php?t=956823&highlight=nfren)

Your monitor may be a bit different, but the method *should* work the same.

GL and keep us posted on your progress

---

### Post by BigSilly on 2008-11-14
OK, I'll give this a go. Thanks for your help. I'm using the VGA lead at the moment, and the xorg.conf looks very busy, but when I put the DVI in, it looks very bare! This is what I got based on the booklet that came with the monitor. Does any of that look right?

```
Modeline "1024x768@75i" 37.20 1024 1056 1192 1224 768 785 790 807 interlace
```

I'll plug in the DVI lead in and give it a shot if you think that looks OK.

How come Ubuntu/Nvidia driver doesn't set this up automatically though? Is this the same for Windows users?

---

### Post by starcannon on 2008-11-14
Don't know if its the same for windows users, I haven't used windows for anything but gaming (and even that has only been a bit this month) for several years, I keep windows around in a virtual box, but thats not the same thing.

If its already installed you could backup your xorg.conf and with your dvi cable plugged in then from a command line run 
```
sudo nvidia-xconfig
```
Reboot and see if that fixes you.
If nvidia-xconfig is not installed already you can find it in the System>Administration>Synaptic Package Manager, install it then run it as mentioned above.

---

### Post by BigSilly on 2008-11-14
Trouble is, installing nvidia-xconfig wants to remove the Nvidia driver! Is this usual? Still, I'll give it a go. Thanks for your time.

---

### Post by starcannon on 2008-11-14
woah wait
Is that running a legacy driver?

---

### Post by BigSilly on 2008-11-14
No, I'm currently using Hardy to try this after removing Intrepid, and it's using nvidia-glx-new, which on Hardy is version 169 I believe.

---

### Post by starcannon on 2008-11-14
Okay well if your running the "new" drivers you should be golden to go ahead with installing the nvidia-xconfig and letting it do what it needs to. If not no worries, I'm pretty good with nvidia on both hardy and intrepid, so one way or another we should be able to get you running, not sure why dvi is being such a pita, I've not had dvi be a specific issue on my monitors that use it.

---

### Post by BigSilly on 2008-11-14
OK, I've booted back in, but I'm still getting a poor resolution, though oddly the xorg.conf is more fully featured this time around. It seems to feature the monitor and the card, plus a load of screen resoltions. One thing I noticed before was that it was very bare.

However, it's now saying the driver isn't enabled, which of course it isn't. Am I OK to go ahead and enable it?

BTW, thanks so much for all your assistance here. I cannot for the life of me understand why this is such a pain, but if we can't get it working then I'm going back to the CRT! I'm sure you'll agree here - life's too short! :biggrin:

---

### Post by starcannon on 2008-11-14
aye go ahead and enable it.

Lol and whatever makes you happiest; though, I'm sure we can sort it out and shouldn't need to resort to a crt :)

---

### Post by BigSilly on 2008-11-14
OK, installed the driver again, and rebooted. The nvidia-settings prompted me to run nvidia-xconfig, which I did, then I restarted again. When it got back to the log in, all I got was a dead screen and just the Ubuntu alert sound to put in my password to log in. Couldn't see a thing.

Have you any idea what could be causing this? I have a feeling that this monitor is just a piece of crap! Could it just not be up to the task of DVI, in spite of the connections?

---

### Post by starcannon on 2008-11-14
I'm thinking now would be a great time to put those modelines you created in their proper places, thats what my next try would be. Use the Nfren example post I linked as a model of where and what to put in your xorg.conf along with your custom modeline.

If that doesn't work, and your still game, I have another trick up my sleeve, but its gonna require a bit of cli work, and a printer.

---

### Post by BigSilly on 2008-11-14
I can't thank you enough for your time. I really can't. Thank you so, so much. That you gave me your time and effort out of your own free time is something I am very grateful for, and I hope I can give it back someday.

Sadly, editing the xorg.conf with the modeline just resulted in the black screen again. 

I've been at this for a few days now, and I think I have to just call it a day before my family walk out on me. :) However, I'm not going back to Windows or anything reactionary like that, and I'm not leaving Ubuntu either. I'll probably try all this again when the next Ubuntu comes out with hopefully an improved Nvidia driver, or better yet I'll just buy a new flatscreen. I can't imagine why I'm having such a problem here, but I just can't commit any more time to it. I'll admit defeat gracefully, but be back to try again in the future.

My thanks again, and thanks also for your incredibly kind offer of extra help outside of the forums. That is the true spirit of open source software, and you have my complete respect. I have no doubt you could have sorted it given the time.

Take care, and I hope to see you around the forums in the future.

---

