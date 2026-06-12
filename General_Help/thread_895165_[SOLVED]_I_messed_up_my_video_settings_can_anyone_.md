---
title: "[SOLVED] I messed up my video settings can anyone help?"
date: 2008-08-19
forum: General Help
---

### Post by stoopidnewb on 2008-08-19
I have hardy heron.  Installed on fresh disk and it works.  When starting up, before i logged in there was a window saying it did not recognize my video card or monitor.  I tried setting it to the radeon option (I have a 1950 pro agp), when I restarted, the resolution was locked at 640 by 480.  Before this happened I had been having trouble trying to get the ati linux drivers to work.  I read the forums and followed directions to no avail.  Then that video card/ monitor screen came up and disaster.  can anyone help please.  How do I get it to recognize my video card and monitor?  I am a complete newb to Ubuntu.  I have an ati radeon x1950pro and a viewsonic VX2245wm.

---

### Post by stoopidnewb on 2008-08-20
ok, so I checked system>administration>harware drivers and the ATI accelerated graphics driver was disabled after I messed with that start up screen thing that showed up before I logged in..  I enabled it and restarted.  Now I have 800x600 as my max resolution.  I noticed ATI catalyst control center is in my applications menu.  When I try to open it, it says "no ATI graphics driver is installed, or the ATI driver is not functioning properly.  Please install the ATI driver appropriate for your hardware or configure using atic...."  The last word is cut-off so I can't read it.  I guess the software got installed but is not working.  Can anyone help or point me towards a Ubuntu teaching website.  I am very new and hate msoft so I want to get this working right but the last time I used a command interface was with dos back in the 80's.  I was born mid 80's so that shows how young I was.

---

### Post by mb_webguy on 2008-08-20
ATI drivers seem to be a bit of a problem on Linux...

Could you post the output of "fglrxinfo"?

---

### Post by rob1101 on 2008-08-20
im no expert but try the command

```
sudo dpkg-reconfigure xserver-xorg
```

I recall it fixed a problem I had a long time ago with one of my old systems which had an ati card.

---

### Post by stoopidnewb on 2008-08-22
ok, so I had to reinstall the operating system because I ended up getting a blank screen after the main ubuntu logo loading bar.  Didn't even get to the login page.  I have been trying several different posts on how to install ati drivers with no success.  One of them blanked the screen but I was able to get to the login screen and run whatever the equivalent of safe mode was and change the settings back.  After that, I tried "Method 2" here [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
everything seemed fine, then window of death and I had to reinstall the entire software as I could find no alternative.  Is there any way to restore back to previous settings when this happens?  Again, I could not even get as far as the login screen.  
running 8.04 Hardy
kernel linux 2.6.24-19-generic
gnome 2.22.3
trying to install x1950 pro drivers

currently I am at a clean install and am skeptical about trying again if I have to keep reinstalling once the blank screen happens

fglrxinfo is "currently not installed" since I did the reinstall.

---

### Post by chkneater on 2008-08-22
Try Envyng, I was having similar driver issues with my NVidia card to work and so far this is the only thing thats been able to fix it.  I had the right files installed, but apparently there are some missing steps that Envyng does to make it work for me at least somewhat better.  Good luck!

---

### Post by stoneage on 2008-08-22
envyNG might be worth a try.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I take it you have tried the drivers in Synaptic?

---

### Post by stoopidnewb on 2008-08-23
I don't know if I have used synaptic.  I havn't done it through synaptic package manager.  I tried looking there after reading your post and could not find it.  I have tried System>administration>hardware drivers and enabled the "ATI accelerated graphics driver"  this did not work.  The rest of the times I did various command line methods via several different sources.  I tried EnvyNG after your suggestion

I have tried everything I know how to try to get these drivers installed and functional.  Tried several different methods from several different sources to no avail  including envyNG.  I have run out of ideas and patience.  Makes me wonder why ATI releases software that does not work.  I know if they don't get it together quick, I will no longer be an ATI/AMD customer.  I don't care if Ubuntu or ATI makes the drivers but, come on, we need something that works.  Everything else seems to work ok except these drivers.  Why is that so much more difficult?  Apparently I am not the only one having these problems with these drivers from searching the forums.    I will just have to put up with low quality video until I consider weather I will pay 200 bucks for Windows and scrap Ubuntu or for an nvidea card.  \

Any one who has an nvidea card that works, can you please tell me which one and what you did to make it work.  preferably comparable or better than my current one.  
currently using
Radeon X1950 pro

BTW if you want to test the ati drivers, use Envy NG didn't work for me just like everything else didn't but at least I didn't have to reinstall the whole system.

If you get a black screen press esc while restarting to get to GRUB menu.

choose the one that says something like safe mode or restore mode

choose repair x drivers

reboot (can do this by simply typing the command: "reboot" with no quotes or spaces)

After I did this I got to my login menu, but logging in normally got me a white screen instead of a black one.

If this happens, restart and go to safe mode under the options in the login menu

open envy ng and select uninstall ATI drivers.  It looks like when it does this, it uninstalls the ATI drivers and reinstalls the original ones that came with Ubuntu that work but don't allow advanced graphics.  This leads me to believe that maybe, if you have this program installed, it may be a useful tool to restore your comp if you try to install the ATI drivers in a different way.  Haven't tried it yet.  At my wits end.

Hope this helps everyone that is going through what I did

---

### Post by stoopidnewb on 2008-11-30
Problem is solved after updating to Intrepid!  Compiz and good graphics work.

---

