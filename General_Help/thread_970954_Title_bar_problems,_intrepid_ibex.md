---
title: "Title bar problems, intrepid ibex"
date: 2008-11-04
forum: General Help
---

### Post by cash34 on 2008-11-04
my ubuntu has been acting up.
the Windows look messed up (attached picture)
it does that no matter what theme i am using.

notice the pidgin window is okay.
so its just the window in focous that does that.
i dont really know how to explain it so i took a screenshot. 

[IMG]http://i43.photobucket.com/albums/e375/cash34/Screenshot-1-1.png[/IMG]

---

### Post by T-AA on 2008-11-04
Did you already try a different theme?

---

### Post by cash34 on 2008-11-04
> **T-AA said:**
> Did you already try a different theme?

yes.
several.
even the default ubuntu themes do this.

so i m thinking is the Nvidia driver =/
is there a work around?

---

### Post by Ubertakter on 2008-11-05
I also have this bug.  I'm running the proprietary Nvidia drivers (173) on a 7600GS.

---

### Post by Zunino on 2008-11-05
Hi.

The titlebar glitches are being observed by many users. From what I have found so far, it's not completely clear whether the fault lies on Compiz or nVidia drivers. I'd guess Compiz, for I have seen reports of the same issues with owners of different cards. There are [other threads]("http://ubuntuforums.org/showthread.php?t=966894") dealing with the same problem here on the forums at which you might like to have a look.

Regards,

-- 
Zunino

---

### Post by wp-sfo on 2008-11-05
> **cash34 said:**
> my ubuntu has been acting up.
the Windows look messed up (attached picture)
it does that no matter what theme i am using.

notice the pidgin window is okay.
so its just the window in focous that does that.
i dont really know how to explain it so i took a screenshot. 

[IMG]http://i43.photobucket.com/albums/e375/cash34/Screenshot-1-1.png[/IMG]

Very similar problem...

I recently installed 8.10 x64 along with compiz on an HP dv2416 with NVidea drivers.

Somehow, after a couple of days I've COMPLETELY LOST the title bars. New windows can still be opened.  I can minimize or close them down with the bottom panel controls, and I can move them only with an ALT-hand drag.  

I've re-booted, I've made many compiz CCSM changes (probably added problems!) all to no avail.

Any solutions?  My sleek new OS has become a broken down pick-up truck.

Thanks!

---

### Post by wp-sfo on 2008-11-05
Solved!

To answer my own question:

I'm not sure what I might have done to make the Title Bars disappear, but here's what I found to fix it (this is in Ununtu 8.10):

   System -> Preferences -> Appearance -> Visual Effects TAB.

   Click one of None. Normal, or Extra.

That's it.

Somehow, they had ALL become unselected.  
As soon as I restored, in my case, 'EXTRA' the Title Bars poppsed back into view!

Good luck.

---

### Post by Dvorakis on 2008-11-05
I imagine eventually compiz will act up again for the poster above me... I've tried it too, compiz is an excellent program its just not so stable.

---

### Post by Neil_J on 2008-11-05
I'm getting the same problem after upgrading to 8.10.  I'm running the nvidia proprietary drivers, version 177.  Compiz version is 0.7.8.

The fix above didn't work for me.  If someone comes up with a fix, please pass it along..

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=91327&d=1225944295[/IMG]

Edit: Seems to be an NVIDIA driver problem since around version 169.07 (reverting to 169.04 is one workaround, if you're okay with using an old driver/binary).  I'll be waiting for a new driver to be released that actually fixes it.  This site is by far the most helpful: [http://www.nvnews.net/vbulletin/showthread.php?t=104822](http://www.nvnews.net/vbulletin/showthread.php?t=104822)

---

### Post by jimmio on 2008-11-06
I solved this issue by using Emerald. It seems the newest metacity doesn't cooperate with Compiz... z depth glitching.

Emerald window decorator looks nicer and fixes the issue.

---

### Post by NTolerance on 2008-11-06
> **jimmio said:**
> I solved this issue by using Emerald. It seems the newest metacity doesn't cooperate with Compiz... z depth glitching.

Emerald window decorator looks nicer and fixes the issue.

Can Emerald use Metacity themes?  I want to keep my Dust theme titlebar.

What font is the OP using in his/her screenshot?

---

### Post by BeastlyKings on 2008-11-06
I have run into the same problem, switching to metacity fixes the problem for me. But I rather like compiz..
I have a nVidia GeForce 7300LE with the 177 driver.

Hope theres an official fix soon!
-BK

---

### Post by sharkster2007 on 2008-11-06
I have the same problem with Ubuntu 8.10 and my Nvidia 6600GT (Agp) Card, the 3d desktop cube works, but compiz fusion seems to make the window title bars turn white at times (Same prob as Beastlykings screenshots above)when using the either of the Nvidia 173 or Nvidia 177 Drivers with desktop effects enabled.

Also effects like "add fire to windows" in compiz config do not seem to do anything at all when checked.

Any ideas on how to fix this?

PS: I am new to Ubuntu Linux only started using it on 29th October :-)

---

### Post by oedipuss on 2008-11-07
I believe this is a bug with the nvidia drivers.. 

Try setting your gnome-window-decorator titlebar opacity to something other than 100%. Check ubuntu-tweak on how to do this, or you can simply edit the values in gconf-editor. It's in /apps/gwd, fields 'metacity_theme_active_opacity' and 'metacity_theme_opacity'. If you want opaque titlebars, 0.99 works and looks practically the same. 
Note that this doesn't actually fix the bug, it just limits its occurence.

---

### Post by BeastlyKings on 2008-11-07
Ah yes, thanks oedipuss!
Although it didn't fully fix the problem for me, it is definitely more bearable now.

It seems the farther I moved away from 100 (ie. 0.98 0.88 etc.) the less problem there was.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=91539&stc=1&d=1226074841[/IMG]

-BK

---

### Post by Interpreter on 2008-11-08
nVidia....
this bug has been there forever, at the very least before Intrepid:
[http://ubuntuforums.org/showthread.php?t=925460]("http://ubuntuforums.org/showthread.php?t=925460")
[IMG]http://i37.tinypic.com/2ikxy5e.png[/IMG]

---

### Post by NTolerance on 2008-11-08
> **oedipuss said:**
> I believe this is a bug with the nvidia drivers.. 

Try setting your gnome-window-decorator titlebar opacity to something other than 100%. Check ubuntu-tweak on how to do this, or you can simply edit the values in gconf-editor. It's in /apps/gwd, fields 'metacity_theme_active_opacity' and 'metacity_theme_opacity'. If you want opaque titlebars, 0.99 works and looks practically the same. 
Note that this doesn't actually fix the bug, it just limits its occurence.

Thanks a lot.  I haven't tested your fix yet but I've always wondered how to control the opacity of titlebars.  Even the full-blown CCSM doesn't have a setting for this.

---

### Post by Interpreter on 2008-11-08
OK so ehm...launchpad anyone?

---

### Post by alwayshere on 2008-11-08
you could try compiz swithch and see what happens [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by NTolerance on 2008-11-08
> **Interpreter said:**
> OK so ehm...launchpad anyone?

Kinda pointless if it's truly an NVidia bug.  Seems like each and every version of the NVidia drivers have their own set of fixes and regressions.  The 177.80 drivers in Intrepid fixed my Powermizer flickering issues but brought on this titlebar bug.  

In the short term I'd like to see the Restricted Drivers Manager offer a whole bunch of NVidia driver versions so that version-specific bugs can be avoided.  

In the long term the proper solution is probably to get a system with Intel graphics which have open drivers.  Sucks for gaming and all that, but NVidia is really dropping the ball with their proprietary Linux drivers and it's getting old.

---

### Post by jedimasterk on 2008-11-09
Well Windows 7 is coming out and MacOSX Snow Leopard, so their probably getting paid to make Linux look bad by developing bad drivers.

---

### Post by BeastlyKings on 2008-11-09
/conspiracy theory
LOL

---

### Post by oedipuss on 2008-11-10
> **Interpreter said:**
> OK so ehm...launchpad anyone?

That's where I saw the opacity thing in the first place :P
I can't find the link anymore, there are way too many similar bugs =/

---

### Post by BeastlyKings on 2008-11-12
A new driver has been made available in the restricted hardware program, driver V.96.
I have tried this driver, and while it fixes the menubar problem, it breaks my screen resolution.
Your mileage may vary, but for me it caused my screen resolution to drop to 1024x768.
I will be reinstalling the 177 driver. :(
-BK

---

### Post by NTolerance on 2008-11-12
> **BeastlyKings said:**
> A new driver has been made available in the restricted hardware program, driver V.96.
I have tried this driver, and while it fixes the menubar problem, it breaks my screen resolution.
Your mileage may vary, but for me it caused my screen resolution to drop to 1024x768.
I will be reinstalling the 177 driver. :(
-BK

Thanks the heads up.  I've installed that driver and no resolution problems here.  I'm a bit confused by the 9X series of Nvidia drivers.  96 is a long way from 177, what gives?

---

### Post by quickk on 2008-11-13
> 96 is a long way from 177, what gives? 

I was wondering the same thing!

---

### Post by oedipuss on 2008-11-14
It seems at least one of the decoration bugs just got fixed: 

[http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_180_vdpau&num=1)

> 
Other fixes in the NVIDIA 180.06 Linux driver include a window decoration corruption with Compiz on GeForce 6/7 GPUs [...]


Any chance of this beta driver being backported for intrepid ? I don't want to try and install the binary manually, it can mess things up.

---

### Post by simmcrd on 2008-11-14
> **BeastlyKings said:**
> A new driver has been made available in the restricted hardware program, driver V.96.
I have tried this driver, and while it fixes the menubar problem, it breaks my screen resolution.
Your mileage may vary, but for me it caused my screen resolution to drop to 1024x768.
I will be reinstalling the 177 driver. :(
-BK

Since the 8.04->8.10 upgrade I lost window titlebars in gnome and kde (but still have them in enlightenment *(e16)* and blackbox).

I'm still relatively new to the Ubuntu distribution. My "Hardware Drivers" list only ***"NVIDIA ACCELERATED GRAPHICS DRIVER (version 173)"*** and ***"NVIDIA ACCELERATED GRAPHICS DRIVER (version 173)"*** (and an Atheros wireless driver). How do I force v.96 to be displayed?

TIA
Compaq Presario F756NR laptop (F700 Series)
AMD Turion 64 X2 Mobile
Ubunt 8.10 (Intrepid Ibex)

---

### Post by oldnat on 2008-11-23
Workaround in

[https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-177/+bug/269904](https://bugs.launchpad.net/ubuntu/intrepid/+source/nvidia-graphics-drivers-177/+bug/269904)

(changing window border style) made it for me, no problems since.

Nathalie

---

### Post by GH68 on 2008-11-24
I had the problem with disappearing title bars. As already indicated, NVIDIA driver 180.06 might be the solution. It solved my issue completely. I just downloaded from [http://www.nvidia.com/object/linux_d...32_180.06.html]("http://www.nvidia.com/object/linux_d...32_180.06.html") and followed the instructions. Hope it works for others as well.

---

### Post by robwilkerson on 2008-11-25
> **GH68 said:**
> I just downloaded from [http://www.nvidia.com/object/linux_d...32_180.06.html]("http://www.nvidia.com/object/linux_d...32_180.06.html")

Just in case that link doesn't work for anyone else, try

32bit: [http://www.nvidia.com/object/linux_display_ia32_180.06.html]("http://www.nvidia.com/object/linux_display_ia32_180.06.html")

64bit: [http://www.nvidia.com/object/linux_display_amd64_180.06.html]("http://www.nvidia.com/object/linux_display_amd64_180.06.html")

---

### Post by IceReaver75 on 2008-11-25
Just wondering if anyone else is seeing this with the 180 drivers.  I had them installed and everything was working almost perfect but after my computer would be on for about 3-4 hours my xorg was just eating my ram and cpu to a point where i had to restart cause everything slowed down to a crawl.  After a restart I would be good for another 3-4 hours.  

I finally went back to the 96 drivers with the work around for them on the nvidia forums under linux support and everything is working now.  

Just wondering if maybe they maybe fixed the 180 drivers and I should give them another shot or just stick with what I have now with the 96 drivers.  I have the geforce 6200 A-LE card.

---

### Post by Usufruct on 2008-11-25
Yes indeedy folks, I can confirm that my title bar issue was completely fixed by installing the nVidia 180.06 beta driver.  

Close all your programs, and exit X windows by running:

```
sudo /etc/init.d/gdm stop
```

Navigate to the location of your downloaded driver, and run:

```
sudo sh NVIDIA-Linux-x86_64-180.06-pkg2.run
```
(modify the filename for your core, of course)

Follow the on-screen instructions, and when the install completes, you can restart x windows by typing:

```
sudo /etc/init.d/gdm start
```

Good luck.  This worked for me.

---

### Post by TriplePlay2425 on 2008-11-25
> **Usufruct said:**
> Yes indeedy folks, I can confirm that my title bar issue was completely fixed by installing the nVidia 180.06 beta driver.  

Close all your programs, and exit X windows by running:

```
sudo /etc/init.d/gdm stop
```

Navigate to the location of your downloaded driver, and run:

```
sudo sh NVIDIA-Linux-x86_64-180.06-pkg2.run
```
(modify the filename for your core, of course)

Follow the on-screen instructions, and when the install completes, you can restart x windows by typing:

```
sudo /etc/init.d/gdm start
```

Good luck.  This worked for me.

I just tried this and it gave me ANOTHER problem... haha.  My entire screen is shifted to the right by about 15 pixels I'd guess, and the part that is shifted off the screen loops around to the left side of the screen.

I then updated to the 180.08 drivers (probably pretty unstable, but they were worth a shot) and I got the exact same thing.  I'm about to revert back to the 177 drivers, as I can live with the problem with the title bar.  I also tried the 180.06 drivers, but had the same situation as the 180.08 drivers.

I would take a screenshot for you guys, but a screenshot doesn't show it wrapping around.  It looks as it should look, but it wraps around on my monitor (although I'm not surprised it does that way, I just wish I could show you guys, although I think my description is pretty straightforward).  I suppose I could edit the image to show what I mean, but whatever.  I'm lazy  :p

Anyways, I hope they get this stuff fixed... :???:

---

### Post by malfa89 on 2008-12-02
You guys are the best. Problem solved

---

### Post by NTolerance on 2008-12-03
Anyone else here running the version 96 driver from the Restricted Drivers Manager?  It solved my titlebar issues but I think it's causing my guest session to fail.  It won't load the gnome-settings-daemon when I switch to it and I see errors in dmesg:

```
[  144.226563] gnome-settings-[7088]: segfault at 20 ip b3c39b1a sp bf9a1870 error 4 in libGL.so.96.43.09[b3bfb000+71000]
[  144.230538] mixer_applet2[7128]: segfault at 20 ip b444ab1a sp bfaeffa0 error 4 in libGL.so.96.43.09[b440c000+71000]
[  150.405869] gnome-power-man[7154]: segfault at 20 ip b4599b1a sp bff2f0f0 error 4 in libGL.so.96.43.09[b455b000+71000]
[  709.998968] gnome-power-man[8611]: segfault at 20 ip b45acb1a sp bfa40770 error 4 in libGL.so.96.43.09[b456e000+71000]

```

---

### Post by catchagato on 2008-12-12
It gives me a black screen when I type "sudo /etc/init.d/gdm stop" Is there another way to install this driver, or can you please provide an even more "idiot proof" detailed way? Thanks

---

### Post by ansicplusplus on 2008-12-14
Hy,
easiest way for me was to change the appearance (system -> preferences -> appearance) of the window borders from "human" to "human-clearlooks". It's almost the same look but without the titlebar bug.
Yours, ansicplusplus.

---

### Post by ftmichael on 2008-12-14
Human-clearlooks is available as a theme in its own right, but the window border setting for that theme is just Human.  Switching to the Human-clearlooks theme didn't fix the problem for me.

---

### Post by Interpreter on 2008-12-14
Which is different from his approach: set the overall theme to human and then the borders to clearlooks, worked. 

Just a "workaround" for me though so Im looking forward to abit of microsoft on santa-day.

---

