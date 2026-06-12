---
title: "Screen Resolution issues in Hardy"
date: 2008-07-11
forum: General Help
---

### Post by DAE_JA_VOO on 2008-07-11
Hi guys.

I just upgraded one of my rigs to hardy and i'm seriously struggling to get it running a proper screen res. This rig has a Dell 24" monitor, which has a native res of 1920x1200. I installed the monitor in "Screens and Graphics" but setting it to that res just doesn't help.

I'm using onboard graphics. Any help would be greatly appreciated :D

---

### Post by gwoodruff on 2008-07-11
Make sure you have the correct driver for your graphics.

---

### Post by DAE_JA_VOO on 2008-07-11
I do. My board has an Intel 865 chipset, and i have that driver installed.

---

### Post by DAE_JA_VOO on 2008-07-12
Bump

---

### Post by gwoodruff on 2008-07-12
Take a look at 
System/Preferences/Screen Resolution
I think the resolution here will over ride the other setting.

Gary

---

### Post by DAE_JA_VOO on 2008-07-12
> **gwoodruff said:**
> Take a look at 
System/Preferences/Screen Resolution
I think the resolution here will over ride the other setting.

Gary

The thing is, once i change the resolution there, it's like the resolution stays at 1280x1024, but it's HUGE, and i actually "pan" across the whole 1920x1200 space...

---

### Post by brokenLockpick on 2008-07-12
I had to resort to editing the xorg.conf file by hand, I obtained the Vertical and Horizontal refresh specs from the manufacturers website. As soon as I entered them and logged out and back in the GUI menu for screen resolution allowed me to select my desired resolution.

I ran > sudo gedit /etc/X11/xorg.conf
from the terminal (you should back up the unmodified version just in case something goes wrong)

There are some examples of the xorg.conf file that I was able to find to know where to add the specs.

Note: I'm still using the universal drivers because the Nvidia drivers were giving me serious problems

---

### Post by DAE_JA_VOO on 2008-07-12
> **brokenLockpick said:**
> I had to resort to editing the xorg.conf file by hand, I obtained the Vertical and Horizontal refresh specs from the manufacturers website. As soon as I entered them and logged out and back in the GUI menu for screen resolution allowed me to select my desired resolution.

I ran 
from the terminal (you should back up the unmodified version just in case something goes wrong)

There are some examples of the xorg.conf file that I was able to find to know where to add the specs.

Note: I'm still using the universal drivers because the Nvidia drivers were giving me serious problems

Hmmm, i know that this is an option, but that CAN'T be the only way to do this. Seriously... getting Ubuntu to run at a different resolution CAN'T be that complicated. 

Ubuntu 7.10 just WORKED automatically at this res.

---

### Post by brokenLockpick on 2008-07-12
> **DAE_JA_VOO said:**
> Hmmm, i know that this is an option, but that CAN'T be the only way to do this. Seriously... getting Ubuntu to run at a different resolution CAN'T be that complicated. 

Ubuntu 7.10 just WORKED automatically at this res.

Good luck, I'll keep an eye on this thread for the easier way. I'm still extremely new to ubuntu so I'm sure that wasn't the easiest way. I was stuck at 800x600 because for whatever reason my monitor settings weren't auto-detected no matter what I seemed to do.

---

### Post by DAE_JA_VOO on 2008-07-12
This sort of thing really irritates me though. I've been using Ubuntu for about a year now, and this is SO annoying. I tried and tried for ages to get my two 22" monitors working properly in Ubuntu, which ALSO didn't work, and nobody here could help me with that either. 

I'm a die hard Ubuntu fan, but if this is how my experience with the OS is, i'll have to move to something else. I seriously don't have the patience to struggle for days just to get my OS to output the correct frikken screen resolution.

---

### Post by jonlemur on 2008-07-12
I haven't had any issues with my own computer with the resolution, but I'm helping two friends install Ubuntu on their laptops, and neither one is getting a good resolution (about 800x600 instead of 1280x800).  We've tried using the restricted drivers to no avail, and we've tried using the universal drivers, again to no avail.  And System->Preferences->Screen Resolution doesn't give any options higher that 800x600.  Could you post the section of you xorg.conf that deals with the monitor (and anything you think would be relevant) to give me an idea of what I need to edit to manually get things working?

---

### Post by peakshysteria on 2008-07-12
```
sudo displayconfig-gtk
```

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

:)

---

### Post by avtolle on 2008-07-12
Use gksudo or gksu for the displayconfig-gtk command, to be on the safe side.

EDIT: See [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo) for why.

---

### Post by DAE_JA_VOO on 2008-07-12
> **peakshysteria said:**
> ```
sudo displayconfig-gtk
```

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

:)

I've already tried that:

> I installed the monitor in "Screens and Graphics" but setting it to that res just doesn't help.

It just creates the same "pan" effect.

---

### Post by avtolle on 2008-07-12
Are you using the Intel driver (and not, e.g., i831)?

---

### Post by DAE_JA_VOO on 2008-07-12
> **avtolle said:**
> Are you using the Intel driver (and not, e.g., i831)?

I'm using the Intel i810 driver.

---

### Post by avtolle on 2008-07-12
OK; I wonder whether using the Intel driver, which I read is newer and "better" might be the way to go. I don't have any intel graphics on my boxes, and I'm going from memory, but there's been one or two threads recently where a switch to that driver has fixed some problems. Let me see if I can find something quickly (running up against a time problem) and get back to you with something better than memory and "I wonder". :-)

---

### Post by avtolle on 2008-07-12
Not finding anything quickly, and am about "out of time". Take a look at this [https://help.ubuntu.com/community/XORGHardy#Video%20Card%20Driver%20Options](https://help.ubuntu.com/community/XORGHardy#Video%20Card%20Driver%20Options) for suggestions on editing that small part of the /etc/X11/xorg.conf file. Sorry couldn't be of more assistance.

---

### Post by DAE_JA_VOO on 2008-07-13
Bump...

---

### Post by jualin on 2008-07-13
Have you try editing your xorg.conf file?

---

### Post by DAE_JA_VOO on 2008-07-13
Nope, but i shouldn't have to. If Ubuntu is "Linux for human beings" then i'm obviously not human. If Ubuntu is so easy it should be a few clicks of the mouse to fix this, not lines and lines of arb code.

I know that editing xorg can fix this, but i shouldn't have to go through so much effort to fix something as simple as screen res.

---

### Post by jualin on 2008-07-13
I am afraid that in Ubuntu sometimes you will need to do a little tweaking here and there to fix the problems that you are experiencing. Remember that most hardware manufacturers don't release the Linux drivers and therefore developers are forced to create their own configurations scripts to make some of the hardware work. 
I know it sounds complicated and old fashioned but it's easier to edit the xorg.conf file than to play with the GUI (which is pretty limited sometimes). Good luck!

---

### Post by harelb on 2008-07-17
Help!!:confused: 

I had some serious trouble with my monitor, and after trying some of the above ideas, things seem to now be even worse (though it might be due to my having played around too much with the sub-options under GUI...) Summary:

1. I had Ubuntu 6.something working fine, that is fine as far as the monitor

2. Installed version 8 of Ubuntu and suddenly my screen resolution is, well everything is huge, as if it things that my monitor has very low resolution

(within Firefox I can partially remedy this by control+ and control- of course)

I tried the system-->preferences-->screen resolution
This gives me a window with the slightly different name (at the top of the dialogue box/window) of "Monitor Resolution Settings" it only gives me 800x600 (currently set to) and 640-480 at the only two options..ugh..

Then I tried the fancier thing with "gksudo" replacing "sudo" but otherwise as above and was asked for my superuser password and got a GUI interface, a window with titled "Screen Graphics Preferences"

If I try to click on "model" is does not list "Insignia" which is my monitor..and if I try to click on "Detect" it gives me "Plu 'n' Play" for model and "640x480" as resolution..no!

I am able to manually tell it to make Model be "Generic 1280x1024" (which is my guess of what might work..I don't actually remember/know what my old setting was, on ubuntu 6, it just auto detected my monitor and gave me a workable resolution) BUT under resolution it still gives me the same two useless ("bad" 800x600 and "worse" 640x480) options to the right of "Resolution:" even though right above it, itproudly showing that "Generic 280x024" to the immediate right of "Model:"

And things are even worse now: when I did a "switch user" to check how things looked, now I can't even see the login screen right...I just see the Ubuntu circle, then the "U" and then the "b" and the rest of the word "Ubuntu" is to the right of the right side of my screen...:confused: ugh again!

The only way I log in is blindly, typign in my user id and hitting TAB key and typing in the pw..

Can anyone tell me how to undo this turn-to-the-worse, probalby due to my fiddling with Model under the "Screen Graphics Preferences" (which came up when I did "gksudo  displayconfig-gtk"

(I know there is still a third suggestion "sudo gedit /etc/X11/xorg.conf" but I want to first undo the damage I did, figure out if there is a contradiction (there seems to be!) between what I tried telling it with the combination of the first two methods, before moving on to a third (in which case I'd still need to know what to type into my xorg.conf but first outta the present mess..??)

Many thanks in advance for any help..very frustrating...ok hopefully I can log in tomorrow and hear your suggestions..this is getting deperate (I dont' normally use smileys and now look what I'm resorting too..

---

### Post by peakshysteria on 2008-07-17
read the whole thread man.
> **peakshysteria said:**
> ```
sudo displayconfig-gtk
```

And adjust the resolution.

(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

:)

---

### Post by jualin on 2008-07-17
Access the terminal by pressing ALT+CTRL+F2 when you get your log in screen. Log in (everything command line now, no GUI login). And then run the xorg reconfiguration script by typing > sudo dpkg-reconfigure xserver-xorg type your password and follow the instructions on your screen. That should make the trick to restore everything to the condition that it was before. Hope this helps!

---

### Post by peakshysteria on 2008-07-17
In Hardy the command is:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by harelb on 2008-07-17
> **peakshysteria said:**
> read the whole thread man.

Peakhysteria, would you believe I read it several times? I didn't fully understand what you had said ("check the checkbox, then click close, then go to Applications-->Other..." would be necessary to dummy-proof the directions for me, sadly..) but I figured that the gksudo thing was equivalent..and apparently I had figured out correctly :(

Because, while your directions, which I've now followed, are nifty in that I now have a quick shortcut via just Applications-->Other--->ScreensAndGraphics, I get exactly what I got late last night (when I used the "gksudo....[etc].." command, namely I get that dialogue box named "Screen and Graphics Preferences" which I wrote abotu last night, and wrote about my trouble with it..you can read those comments it you want for more detail but more briefly :) here's the summary:

it still only offers me under the drop-menu for "Resolution:" the same two options, low and very-low resolution (the same two sets of numbers, 800x600 and the lower still resolution, I mentioned above) Changing the "Model:" dropbox is neither clear (they don't list my Model) nor seems to be helpful since selecting "Generic 1280x1024" as it still says from last night, still gives me only the 800x600 and lower-still resolutions, I do not get a different Resolution dropbox when the Model dropbox is changed..

and two clues tell me it doesn't work: first, using "switch user" and looking at the messed up login screen, and secondly, clicking the "Test" button from that Screen Graphics Preferences dialogue box I now know exactly what the earlier poster means by "paning"...I can use the mouse to move around the still hugely "zoomed in screen" I get when I use the "test" button..obviously one should see the whole screen normally without having to "pan" like that..

I hope my description is clear..Let me know if you have suggestion..

---

### Post by Pettman on 2008-07-17
I'd start with running xrandr and check the maximum size of the screen (from the x-servers point of view), it may be that the gfx-driver is unable to handle the resolution the original poster wanted:
```
xrandr
```
For me this outputs:
```
pettman@CPPPotkustart:~$ xrandr 
Screen 0: minimum 320 x 200, current 1280 x 800, **[COLOR="Red"]maximum 2624 x 2048[/COLOR]**
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

```The piece in marked with red and bold text is the one you need to check to determine if your gfx-driver can handle your desired resolution.
If the desired resolution is within the maximum resolution the card can handle you will have to add that mode to the display. This is a 3 step operation, first is to make a modeline using gtf:
```
gtf width height refreshrate
```(width, height and refreshrate should be replaced by numbers, if you got a 1280x1024 screen and want to set it to 60 Hz you'd type "gtf 1280 1024 60")
Then you copy the modeline the program outputs (hi-lighted with red in the example)```

  # 1232x987 @ 60.00 Hz (GTF) hsync: 61.32 kHz; pclk: 101.06 MHz
  Modeline "1232x987_60.00"  [COLOR="Red"]101.06  1232 1312 1440 1648  987 988 991 1022  -HSync +Vsync[/COLOR]

```
Insert it into the following:
```
sudo xrandr --newmode name_of_mode modeline
```
[I][SIZE="1"](name_of_mode is the name of the mode you wish to add, I'd recommend widthxheight. modeline is the modeline you got from gtf)[/SIZE]
[/I]Once that has been done you should add the mode to the list of the displays supported modes (name of display can be something like VGA or LVDS):
```
sudo xrandr --addmode name_of_display name_of_mode
```
Once the x-server has been told the display can handle the resolution you should be able to set the mode of the output with:
```
sudo xrandr --output name_of_display --mode name_of_mode
```

---

### Post by harelb on 2008-07-17
Jualin, I did that, and it seems to have worked, thanks..(even though when I was done I rebooted since it wasn't clear how to get out of text only mode..upon reboot I was back in normal mode..)

Peakhysteria, since I'm in Ubuntu 8, should I still run the command again, with "-xphigh" added, even though typing as Jualin suggested ~seems~? to have worked? Anyway I seem to be back to square one, which is better than how things were last night but still would like to get screen resolution to something higher than that 600x800 which is currently the highest options it gives! (must run to a mtg now, will check back around 6pm EST)

P.S. is your name a reference to Peak Oil by any chance?

---

### Post by harelb on 2008-07-18
> **Pettman said:**
> I'd start with running **xrandr** and check the maximum size of the screen (from the x-servers point of view), it may be that the gpu is too slow to handle the resolution the original poster wanted.

I'm trying to follow you..is this simpler than editing the xorg.conf file? (I don't have step by step directions for what to put in there so I'm trying this xrandr instead). My ubuntu knowledge is extremely limited (and what little I remember from 1990s unix/linux doesn't help) After checking on linux.die.net that typing "gtf" won't blow up my computer ;-) I typed

 gtf width height refreshrate

And got this:

 # 0x0 @ 0.00 Hz (GTF) hsync: nan kHz; pclk: nan MHz
  Modeline "0x0_0.00"  nan  0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync


Have no idea what this is telling me my resolution is, or what to set it to..1024 by something? 

Which part, precisely, is the modeline? the second line above? with or without the word Modeline included? Is it exactly this:

"0x0_0.00"  nan  0 -2147483648 -2147483648 -2147483648  0 1 4 1  -HSync +Vsync

or not?

Also I'm not sure what "name_of_mode" stands for? Is it a name I just make up? Same question for "name_of_display"

Finally re: "Once the x-server has been told the display can handle the resolution you should be able to set..." how do I know whether is has bgeen told the display can, or cannot handle it? Or does the third command automatically make sure it's been told display "Can handle the resolution?

I appreciate all the help from you experts, but as DAE_JA_VOO  	
 said this is very frustrating..it's very basic (screen resolution) it worked fine with Ubuntu 6 and all the user does is upgrade using a CD to Ubuntu 8 and suddenly on has to try to understand all this code..I fit's this complicated for someone who's used (text-only) emacs in the 90s, it's certainly not for Jane/John Doe everyday person trying to use it for the first time...anyway, appreciate your explaining this step by step since it's very far from obvious to us non-techies..Thanks,
Harel

---

### Post by Pettman on 2008-07-18
@Harleb: I've edited [my previous post]("http://ubuntuforums.org/showpost.php?p=5405663&postcount=28") to be a bit clearer.
As for using xrandr vs editing the xorg.conf, xrandr is a single session fix but it will allow you to experiment without restarting your xserver and determining if you can achive the resolution you want. Once you've determined if your gfx-driver can handle the resolution you should add the modeline into the apropriet Monitor-section of your xorg.conf.
As for your problem with gtf, it's not a detection tool but an application to generate modelines. You will have to provide the resolution (width and height) and refreshrate.
name_of_mode can be anything but I'd strongly recommend you name the mode <width>x<height> where <width> and <height> are replaced by the widht and heigt of the mode. name_of_display you have to figure out by reading the output of xrandr, if you've only got one monitor connected it should be the one xrander says is connected otherwise you'll have to figure it out somehow else. The "xrandr --addmode" will add the mode to the display, so yes it tells the xserver that that display can handle that resolution.
Also I'd recommend that you read up on [Magic SysRq key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") just in case you manage to crash your system.

---

### Post by harelb on 2008-07-18
Pettman,

Thanks for trying to clear up with red font etc. I've only followed your first step in your edited post, because unfortunately that seems like where the trouble starts. Typing in "xrandr" I got the following:

> 
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
Which is telling me it thinks 800 by 600 is the limit on my screen. I take it "gfx-driver" means graphics driver? Because I'd like to emphasize something I've said previously: before I "upgraded" to Ubuntu 8, I had had Ubuntu 6 (I think it was 6.06) and never, ever, ever had any such problem (see bold part below for what I mean by "never had this")

The fact that just a week or so ago, under ubuntu 6 (and the same computer, the same (yes, only one) monitor), same graphics driver, same EVERYTHINg) it was fine, tells me that,** either I do better than 800 by 600 resolution (more likely, IMO) or (less likely but POSSIBLE, IMO) if I do have 800 by 600 then somehow Ubuntu 6 managed to keep things looking at if I do have decent resolution: I never, ever had these problems and saw the ENTIRE desktop, saw MOST websites fine, not in large letter, NOT having to have a *horizontal* scroll bar appear because the left-to-right "Distance" was so "big"...it looked normal, it worked fine, my left-to-right breadth, for lack of a better term, managed to keep the entire web page in view from left to right...** Then I "upgrade" to Ubuntu 8 and suddenly all these problems appear...all I want is  a working visual display, that's all..Anyway given this background that it worked 100% fine under Ubuntu 6 and now it seems to claim, if I understood it correctly (which is why I ddin't proceed to your other steps) is it is now claiming, "sorry pal, it's all your driver's fault" (which Ubuntu 6 certainly proves is not the case!) what do you think is really going on?

HB

> **Pettman said:**
> @
Also I'd recommend that you read up on [Magic SysRq key]("http://en.wikipedia.org/wiki/Magic_SysRq_key") just in case you manage to crash your system.

I really appreciate the info, but sadly, I can't afford to spend hours learning advanced linux techie stuff, if there's a risk or crashing my system, I'd just as well switch to Ubuntu 7 or Red Hat or Mandrake or... :( But per comments above, it sounds like I'm at a dead end at the end of your first step anyway, it doesn't think I can do better than 600x800 so I didn't even try the other steps..

---

### Post by jaystrum on 2008-07-19
I have this exact same issue.

---

### Post by rated727 on 2008-07-19
> **jualin said:**
> I am afraid that in Ubuntu sometimes you will need to do a little tweaking here and there to fix the problems that you are experiencing. Remember that most hardware manufacturers don't release the Linux drivers and therefore developers are forced to create their own configurations scripts to make some of the hardware work. 
I know it sounds complicated and old fashioned but it's easier to edit the xorg.conf file than to play with the GUI (which is pretty limited sometimes). Good luck!

I'll state emphatically that jualin is 100% correct about this one.  I've been working to get an old 3dfx Voodoo3 card to do something above 800x600 resolution.

When I FINALLY thought I had it all together, Ubuntu started but the monitor showed a "complaint" box that advised me that the Ubuntu driver/monitor combination that had been selected was "out of sync range.  Acceptable vertical frequency range for the monitor is 50-160 Hz.  Ubuntu was trying to use a 43 Hz vert freq. (it counted down 15 seconds then "hibrinated")

To solve this abortion, I had to start Ubuntu in recover mode -- login as root **sudo -s** -- log into the /etc/X11 directory rename the config file **mv xorg.conf xorg.conf_bad **-- rename the last working config file **mv xorg.conf_bak xorg.conf **-- exit -- exit -- conginue with normal boot.  (it started again in 800x600)

Again, start a terminal -- **sudo -s** -- **gedit /etc/X11/xorg.conf_bad** -- erase EVERY line that refers to any freq rate less than 50 (ther were 3) -- save and exit gedit

reverse the renaming process above and reboot.

That is just one example of "a little tweeking".  But, once you get it working, you'll probably agree that it was worth the effort.

---

### Post by harelb on 2008-07-19
Rated rated727,

I will try this..but just one question so I don't screw this up ... by "conginue with normal boot." do you mean: "at this point, after exiting from gedit and the terminal REBOOT your computer again, only in regular (not "Recover" mode)? If not then I don't follow, but hopefully that's what you mean..?

Oh and "reverse the renaming process above" just means not the same two lines typed in, in reverse order, but rather instead reverse the process, which I take it would mean

1. first, "mv xorg.conf_bak xorg.conf"

wait, does one then continue?? by also doing "mv xorg.conf xorg.conf_bak" as the second step?

(Hopefully that'll do it for me. It's a 2006 computer so while I am not familiar with all of my drivers' names, etc (and lesser known manufacturer, Microtel via malmart.com which had Xandros but I didn't like Xandros) so it seems unlikely that the hardware itself lacks reasonably decent graphics and ability to do better than 800x600)

---

### Post by harelb on 2008-07-24
Still no answer? :-(   I'm not trying to prolong this just want to be perfectly clear so I don't screw up my computer..so if Rated727 or else anyone else could answer my 2 questions about his post:

> **harelb said:**
> Rated rated727,

I will try this..but just one question so I don't screw this up ... by "conginue with normal boot." do you mean: "at this point, after exiting from gedit and the terminal REBOOT your computer again, only in regular (not "Recover" mode)? If not then I don't follow, but hopefully that's what you mean..?

Oh and "reverse the renaming process above" just means not the same two lines typed in, in reverse order, but rather instead reverse the process, which I take it would mean

1. first, "mv xorg.conf_bak xorg.conf"

wait, does one then continue?? by also doing "mv xorg.conf xorg.conf_bak" as the second step?

(Hopefully that'll do it for me. It's a 2006 computer so while I am not familiar with all of my drivers' names, etc (and lesser known manufacturer, Microtel via malmart.com which had Xandros but I didn't like Xandros) so it seems unlikely that the hardware itself lacks reasonably decent graphics and ability to do better than 800x600)

Many thanks

---

### Post by inkrypted on 2008-07-24
I have read your post and agree that to change your xorg settings you should not have to learn a bunch of new stuff. Ubuntu 8.04 is supposed to have a built in GUI for editing that file but I have found that it sometimes did not work to my satisfaction here is a project I stumbled upon and helped me alot as I have had your issue in the past.

[http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php)

Good Luck

---

### Post by DAE_JA_VOO on 2008-08-24
This issue has caused me to revert back to 7.10.

It's absurd that a PREVIOUS version of the OS can do whatever res i want it to straight out of the box but Hardy can't.

Has this issue been sorted out yet guys?

---

### Post by peakshysteria on 2008-08-25
This might be the solution for you man: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel) which says: If it only uses 640x480, change the BIOS shared Video Memory from 1MB to 8MB. 

Other things to try (if the above didn't work):
Have you tried to enable hardy-proposed? It might bring along a fix for your onboard driver. If it doesn't work just uncheck it if you don't want it enabled anymore or for different versions.

Also [http://www.deesaster.org/progxorg.php](http://www.deesaster.org/progxorg.php) mentioned above seems like a nice option.

And have you seen this [thread]("http://ubuntuforums.org/showthread.php?t=779743&highlight=intel+845") saying:
> **ghope said:**
> Update. I stumbled onto another post in which the writer said he had the Intel 845 chip and it was blacklisted by Compiz. So, I set System > Preferences > Appearance > Visual Effects to "none" and presto, graphics are peppy again!

I can live with this solution, but it would be nice to have some of the nifty effects without crippling the machine. If I want to achieve this, is my next step to install a more robust graphics card, and is there a hardward compatibility list somewhere that I could reference?

---

