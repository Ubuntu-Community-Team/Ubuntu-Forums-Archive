---
title: "Menu problems for Compiz Fusion"
date: 2008-11-10
forum: General Help
---

### Post by Mark Huberty on 2008-11-10
I'm running Ibex with Gnome, Compiz Fusion and Emerald. On several applications (all OpenOffice apps, and Kile) the application menus and all other dropdown menus inside the applications render as blank when Compiz is running. I didn't have this problem before Compiz was activated. 

Anybody else have this problem, or ideas on how to fix it?

Mark

---

### Post by Alan A on 2008-11-11
I'm seeing exactly that problem - when compiz is enabled, the drop-down menus on some apps just show the icons with no text. Actually the text is displayed for a very brief moment before the menu is blanked.

This seems to affect mostly KDE apps?
unfortunately I have not found a solution (other than to disable compiz).

I'm on Ubuntu 8.10 (upgraded from Hardy) and using an older nvidia graphics card with the .96 drivers.

---

### Post by eternalnewbee on 2008-11-11
Hi there.
Maybe you could post a screenshot of the blanked menus?

---

### Post by Whisp3r on 2008-11-11
I'm having the exact same problem.

Here's what they look like:

---

### Post by eternalnewbee on 2008-11-11
> I'm having the exact same problem.

Here's what they look like:
Attached Files
File Type: xcf 	openoffice.xcf (514.9 KB, 0 views)
What is this? I can't open it.
To make a screenshot go to: Main Menu > Accessories > Take Screenshot.

---

### Post by Whisp3r on 2008-11-11
Lets try this again. OpenOffice is the only program effected thus far.

I have tried changing themes, settings in Compiz/Emerald managers, etc. I've checked the OpenOffice 'fix' in work around, and back and forth. No luck yet.

---

### Post by Alan A on 2008-11-11
I have converted Whisp3r's original .xcf to a .png - this shows a dropped-down menu as well. I would do my own screenshot but am not at home at the moment (it would look much like this anyway).

Other apps that are definitely affected in the same way for me are k3b and kdenlive.

---

### Post by eternalnewbee on 2008-11-11
Ok. Go to: **Main Menu > System > Administration > HArdware Drivers**
What do you see? Are there any options?
If there are, you probably want to choose the **recommended** option.

---

### Post by Whisp3r on 2008-11-11
Here it is:

Running Nvidia driver 96, enabled. I tried disabling to see if that fixed it, and it didn't. The only thing thus far I've found that fixes the OO menu problem is using Metacity, instead of Compiz.

---

### Post by Mark Huberty on 2008-11-11
I'm seeing the same behavior as the screenshots uploaded by Whisp3r. Nvidia .96 drivers running on Ibex, with the Gnome desktop with Emerald. 

The same behavior occurs in KDE. Disabling the "Legacy full screen support" option on the "Workarounds" plugin had no effect (this was found to fix earlier OpenOffice/Compiz menu issues). 

Turning off the "Openoffice menu fix" workaround also didn't appear to help.

Right now, it appears native KDE apps (Openoffice, Kile, Kbibtex, K3b) are the only ones affected.

---

### Post by Whisp3r on 2008-11-11
Hey Mark,
 Just wondering; what type of video card are you running? I'm beginning to wonder if its my card (GForce FX with 64mb). I tried everything you did as well, including upgrading OO to 3.0.

---

### Post by Mark Huberty on 2008-11-11
I'm running a GeForce MX 440 AGP 8x. 

Perhaps it's the older video cards that have a problem. The .96 video drivers seem to be the common thread.

---

### Post by kiwi4dguy on 2008-11-11
Got same problem here with opera and amsn under gnome, and I would imagine they won't be the only ones. OO is fine here, seems to be working properly.

I also have a geforce4 mx440se graphics card using the 96 driver.

---

### Post by Whisp3r on 2008-11-11
I have access to another card (256mb) AGP card. I'll swap the machine's cards tomorrow and see what happens.

---

### Post by Mark Huberty on 2008-11-12
By this thread:

[http://ubuntuforums.org/showthread.php?t=978091](http://ubuntuforums.org/showthread.php?t=978091)

It appears that Ibex has issues with the .96 nvidia drivers and legacy support, that cause menu and application button problems.

But that still doesn't seem to explain why some apps (Firefox, native Gnome apps like gedit or evince) work OK, while the KDE apps and OO have problems.

---

### Post by Whisp3r on 2008-11-12
Well, I was going to swap video cards (65MB for 128MB), but ended up finding out that the AGP x4/x8 slot in this box (Linux) is a lot newer then my old box (x4). So no swap. I did LiveCD boot this box, which has the problems, and under LiveCD, OpenOffice menus and the other affects work just fine. Boot off the HD, and OO goes to heck. 

Guess its time to look into getting a new card.

---

### Post by felixnine on 2008-11-12
yeah, weird, i have the same problem, but it's ONLY kde3 apps. the amarok nightlies and other kde4 (qt4?) apps are fine.

---

### Post by IceReaver75 on 2008-11-12
Yeah same problem here with open office.  I have the Nvidia Geforce 6200 A-LE card and if I use the 177 drivers I can't use the human themes or any theme based off the human theme without getting the title bar washout but open office menus work just fine.

If I switch to the 96 drivers I can use the human themes just fine with no washout but all the open office menus are gone.

There just no happy medium with the Nvidia drivers.  You either have to sacifice the human themes or have no open office menus.  I tried to look into the xorg configs of both drivers but they are same.

---

### Post by Malac on 2008-11-13
Same Here on a demo machine just showing them how good Ubuntu is and then open OpenOffice and oops:
[ATTACH]92484[/ATTACH]
All other compiz effects working fine. Switching to metacity shows the menus but is a bit of a pain.

lspci output:```
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
```lshw output:```
           *-display
                description: VGA compatible controller
                product: NV11 [GeForce2 MX/MX 400]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: b2
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-2.0 bus_master cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
```Using 96.43.09 driver according to drivers app

---

### Post by felixnine on 2008-11-13
due to a bunch of other problems with ibex, i went back to hardy. it sucks, but problem solved.

---

### Post by Whisp3r on 2008-11-14
I put 8.04 with Compiz on this box, and OO works just fine. Oh well. We'll see how it all works when I get done building my first computer. :)

---

### Post by mfaust731 on 2008-11-16
I have Ibex with the nvidia 96 driver and have the same thing, however open office works fine here - it is Scribus and google earth that has blank menus>

---

### Post by Alan A on 2008-11-20
I have found a workaround which partially solves this problem for OpenOffice. If I set fonts to Subpixel (System/Preferences/Appearance/Fonts) I get my OpenOffice text and menus back with compiz enabled. Unfortunately other KDE apps are still without text.

I found this at [http://www.nvnews.net/vbulletin/showthread.php?t=122695]("http://www.nvnews.net/vbulletin/showthread.php?t=122695") where the author also suggests making some changes to the xorg.conf file. The xorg.conf changes did not seem to make any difference for me - only the font setting change.

---

### Post by Malac on 2008-11-20
> **Alan A said:**
> I have found a workaround which partially solves this problem for OpenOffice. If I set fonts to Subpixel (System/Preferences/Appearance/Fonts) I get my OpenOffice text and menus back with compiz enabled. Unfortunately other KDE apps are still without text.

I found this at [http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695) where the author also suggests making some changes to the xorg.conf file. The xorg.conf changes did not seem to make any difference for me - only the font setting change.
I can confirm the above workaround works for me in OpenOffice and also the tip for wine.
Make sure you close the QuickStarter if you use it as the changes don't show up until it is restarted.

---

### Post by SocratesTNR on 2008-11-21
Been having problems on OO, Ubuntu 8, NVIDA card (I think - noob).

Turning off anti-aliasing in OO worked although the result isn't pretty.

Sub-pixel thing didn't :-(

---

### Post by jhutton on 2008-11-22
> **Alan A said:**
> I have found a workaround which partially solves this problem for OpenOffice. If I set fonts to Subpixel (System/Preferences/Appearance/Fonts) I get my OpenOffice text and menus back with compiz enabled. Unfortunately other KDE apps are still without text.

I found this at [http://www.nvnews.net/vbulletin/showthread.php?t=122695]("http://www.nvnews.net/vbulletin/showthread.php?t=122695") where the author also suggests making some changes to the xorg.conf file. The xorg.conf changes did not seem to make any difference for me - only the font setting change.

Thanks - these steps fixed it for me.

---

### Post by lemming465 on 2008-11-22
We're discussing this on launchpad as bug [297836]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/297836").  The best workaround so far is to disable Compiz effects using System -> Preferences -> Appearance, Visual Effects = none.  It was not a problem in 7.10 or 8.04, but I'm sticking with 8.10 anyway.

---

### Post by Malac on 2008-11-23
This may have already been said but this is obviously a problem with the nVidia driver 93.46.09 and certain (older??) nVidia cards, as I can confirm this is not an issue at all with one of my machines which has an older ATI card, compiz enabled. OpenOffice, Wine menus are fine also all KDE apps are okay.

Hope this helps in tracking it down.

---

### Post by slei3 on 2008-11-23
most people aren't sure of what they really want in life. I received this letter from a friend on the computer, did what it told me to, and within a week, everything I had wished came true!! Here's an exact copy,

this

really

works!!!!











*************************************************************







1. To yourself, say the name of the only guy or girl you wanna be with 3 times!











*************************************************************











2. Think of something you wanna accomplish within the next week and say it to your self 6 times!!











&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;&#126;































3. If you had 1 wish what would it be? say it to yourself 9 times!!!








-----------------------------------------------------------------------















4. Think of something that you want to happen between you and that 1special person and say it to your self 12 times!!!












--------------------------------------------------------------------















5. Now, heres the hard part! Pick only 1 of these wishes and as you scroll down focus and concentrate on it and think on nothing else but that wish.











* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



*

*



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *



* *







Now make one last &amp; final wish about that one wish that you picked.







After reading this, you have 1 hour to send it out to 15 people, and what you wished for will come true within in one week!







u only get one chance!!!!! Now scroll down and think of your
crush!!!



























































Keep going

down



























Keep going







































Keep

going








































!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!











Did you think of your crush? I hope so, that was your last chance. Now pay very close attention this important message!



Sorry but once read, must be sent. Yes, this is one of those kinda chain letters that everyone hates. This one has been going since 1864 and if you break this chain, you will pay!!!!!! Remember that after hearing these stories.







First Example:



Take Barbra Wallace.. She was a pretty lucky girl, up till she got this same chain letter. She had a crush on the same kid since kindergarden. when she got this mail she didn't pay any attention to it. She just thought, no big deal. And deleted it. The next day her dad got fired and her mom dies in a car crash. If she would have sent the letter none of that would have happened and her mom would be alive.







Second Example:



Try Freddie D. Now Freddie D. was your average nerd. Had glasses, was short and chubby, was in gifted. All the signs of
your total dork. He also received this letter and sent it to 51
people in the hour. Now, like Barbra, he had a crush on a girl since 3rd grade. The next day after sending the chain the girl confessed her love for him ever since 3rd grade. Freddie D. finally had the courage to ask her out, and of course, she had been waiting to yes to that for years. They grew up and
married each other to live happily forever.







Third Example:



Now if you couldn't relate to the others, this'll get ya hooked. Listen to this. A kid named Jordan Johnson was just getting on AOL to check his mail. He was a quiet kid, not that popular but not a geek either. he was just normal. He saw he had mail from his friend. It was this exact letter. Now Jordan Johnsen was a smart kid and he knew what could happen if he didnt pass it on. He simply pulled a few friends from his buddy list and sent it along. The next day, about that same time, he got a phone call. It said he had won the lottery!
then his dad came home and bought him a new bike! His mom bought him Nintendo64 and play station! His grandmother sent him a new computer, and his best friend
gave him tickets to the concert he wanted to go to, Kid Rock and Limp Bizkit! Then he inherited a brand-new tv from his aunt! He was goin' wild! the next day his secret crush asked him out, and they have been going out ever since.







Now, you heard the stories. I know which person i'd rather
be, but thats up to you. I wouldn't wanna end up like Barbra but thats only me. We all want what we cant have but now's ur chance to go out withthat special somebody ur waiting for. Take it or leave it. If you send this to-



1 person- you will lose all luck in ur love life..... forever!!!!!



10 people- your crush will say they like you as a friend...... ONLY!!!!!



15 people- your crush will say they like you



20 people- your crush will ask you out!



25 people- your crush will kiss you!!




35 people or more- All of the above!!



Don't blow it, it's ur chance to shine! Have everything u wanted, and more! Now, complaining cus u dont have any
friends. Well theres an answer 4 everything. It's simple, just go in a chat room, pick some names and send away! but here's the catch..... you only have 1 hourtoReply to &quot;Re: &quot;&#171; back to messageto: &amp;hearts;lisa loves jt always &amp; 4ever&amp;hearts;

[change]
subject:
message: [color] Dark Red Red Orange Brown Yellow Green Olive Cyan Blue Dark Blue Indigo Violet White Black [size] Tiny Small Normal Large Huge
hey that chain message does it really work. and if it does that is awsome

Please wait...




Exclusive Features
See all

Freewebs Help TipsStart your Own Mailing List

Want to keep friends, family, customers and more in the loop about the latest on your site?

You can send event invites, monthly newsletters, product updates and more!

Create a Site Mailing List

---

### Post by LepeKaname on 2008-12-02
Thank you! It solved my problem.

BTW, I also had the NVIDIA MX 400 ... with the 96 driver.

This was my post with screenshots:
[http://ubuntuforums.org/showthread.php?p=6298098](http://ubuntuforums.org/showthread.php?p=6298098)

---

### Post by Eric Qel-Droma on 2008-12-06
I have a GeForce MX 400 as well, and using the nVidia driver, I have either no font or font garbage in Wine whether I have visual effects on or not.

I was thinking of trying the whole workaround posted above, but I'm afraid that my Xorg.conf file is too different from what is posted on the other site.  If I were to change my Xorg.conf to mirror the other one exactly, could that break my system?  Or, if it were wrong, would my system simply revert to the default driver?

Thanks,

Eric

---

### Post by Eric Qel-Droma on 2008-12-06
BTW, the tutorial suggests, that if using Wine, one should "Create a txt (settings.txt) file in fx your home folder containing this:"

What is "fx your home folder"?

---

### Post by LepeKaname on 2008-12-12
1. Create the "settings.txt" in your home directory.
2. Enter this code in that file:

[HKEY_CURRENT_USER\Software\Wine\X11 Driver]
"ClientSideWithRender"="N"

3. $ regedit settings.txt

The idea is to insert that key into your "Windows" registry using the "regedit" WINE command.

So basically you can create it wherever you want and name it as you prefer.

About your xorg.conf I recommend you to make a backup before moving anything. If you have problems with it,you can use mine because it is the same video card:


 Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor0"
        Option          "AllowGLXWithComposite" "True"
        Option          "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth   24
                Modes   "1600x1200" "1280x1024" "1024x768" "800x600"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Vendorname      "NVIDIA Corporation"
        Option "RenderAccel" "0"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/psaux"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "keyboard"
EndSection

Section "ServerLayout"
        Identifier      "Layout0"
  screen 0 "Screen0" 0 0
        Inputdevice     "Keyboard0"     "CoreKeyboard"
        Inputdevice     "Mouse0"        "CorePointer"
EndSection

Section "Module"
        Load            "dbe"
        Load            "extmod"
        Load            "type1"
        Load            "freetype"
        Load            "glx"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Vendorname      "Unknown"
        Modelname       "Unknown"
        Horizsync       30.0    -       110.0
        Vertrefresh     50.0    -       150.0
        Option          "DPMS"
EndSection

Section "Extensions"
        Option          "Composite"     "Enabled"
EndSection

---

### Post by carloshiga on 2009-01-29
I followed the instructions in

[http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

and it fixed the problem for OpenOffice but my aMSN still have the problem. Any idea?

---

### Post by antsu on 2009-03-07
Hi everyone, 
I know this thread is a little old, but I've found something that some of the people that posted here may like to know and I think it can help them. I am running Ubuntu 8.10 Intrepid Ibex with a GeForce 2 MX 400, using the nvidia96 drivers. I was having the same issues with the menus on aMSN, K3B, Amarok and OpenOffice. I did the Wine and subpixel stuff, but they only solved the problem with Wine fonts. So, while searching a way to solve this, I've found the solution that worked perfectly for me.
In your xorg.conf file, under the section "Device", just add the line
```
Option "RenderAccel" "0"
```
Them restart X server (CTRL+ALT+BACKSPACE) and you will have menus on Amarok, K3B, OO, aMSN or whatever :D

ps: sorry if I screwed up something on the writing, I'm not very good in English :(

---

### Post by If I Get Old on 2009-03-31
> **antsu said:**
> Hi everyone, 
I know this thread is a little old, but I've found something that some of the people that posted here may like to know and I think it can help them. I am running Ubuntu 8.10 Intrepid Ibex with a GeForce 2 MX 400, using the nvidia96 drivers. I was having the same issues with the menus on aMSN, K3B, Amarok and OpenOffice. I did the Wine and subpixel stuff, but they only solved the problem with Wine fonts. So, while searching a way to solve this, I've found the solution that worked perfectly for me.
In your xorg.conf file, under the section "Device", just add the line
```
Option "RenderAccel" "0"
```
Them restart X server (CTRL+ALT+BACKSPACE) and you will have menus on Amarok, K3B, OO, aMSN or whatever :D

ps: sorry if I screwed up something on the writing, I'm not very good in English :(
This totally worked for me.  Thank you.  No more metacity --replace when I want to use digikam and then compiz --replace when I'm done.

---

### Post by masque7 on 2009-04-07
> **antsu said:**
> Hi everyone, 
I know this thread is a little old, but I've found something that some of the people that posted here may like to know and I think it can help them. I am running Ubuntu 8.10 Intrepid Ibex with a GeForce 2 MX 400, using the nvidia96 drivers. I was having the same issues with the menus on aMSN, K3B, Amarok and OpenOffice. I did the Wine and subpixel stuff, but they only solved the problem with Wine fonts. So, while searching a way to solve this, I've found the solution that worked perfectly for me.
In your xorg.conf file, under the section &quot;Device&quot;, just add the line
```
Option &quot;RenderAccel&quot; &quot;0&quot;
```Them restart X server (CTRL+ALT+BACKSPACE) and you will have menus on Amarok, K3B, OO, aMSN or whatever :D

ps: sorry if I screwed up something on the writing, I'm not very good in English :(

That worked. However, log back in and my graphics are glitchy and unusable.  System->Prefs->Appearance->Fonts->Sub Pixel worked. GeForce 2 MX 400, Nvidia 96 driver using Metacity, not Compiz.

---

