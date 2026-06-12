---
title: "Installing ati drivers isnt user friendly!!!!"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Zireth ZH on 2009-05-17
HOW THE HECK IN THE WORLD I CAN GET TO INSTALL MY DAMN CATALYST DRIVERS 9.4 ON MY UBUNTU 8.04 ????? IVE DONE EVERYTHING I COULD .. IVE BEEN GOOGLING ALL DAY LONG JUST TO GET THE DAMN DRIVERS TO INSTALL.. TONS OF WINDOWS OF INFORMATION.. LOTS OF SUDO THIS AND SUDO THAT AND NOTHING...  SOME OF THE STEPS I COULDNT COMPLETE THEM CUZ ITS NOT STEP BY STEP AND EASY UNDERSTANDING FOR DUMMIES!!! CANT THIS JUST BE CLICK ON THE ICON, NEXT NEXT NEXT AND THATS IT? I DUNNO WHERE U GUYS CAN CHECK MY POSTING HISTORY OR SOMETHING BUT IF U CAN SEE MY POSTS ALL OF THEM ARE RELATED TO FREAKING ATI DRIVERS.. AND NON COULD REALLY HELP ME ON THIS ... PPL JUST COME ANSWER ME WITH (EXAMPLE) SH. SOMETHING AND THATS IT .. NO MORE EXPLANATION... AM I SUPPOSED TO GUESS? OR U GUYS WERE BORN KNOWING LINUX? DAMN.. HOW HARD IS FOR PPL TO JUST READ AND SHARE A LIL SOMETHING ABOUT WHAT U ALREADY KNOW! I BET U WERE IN MY POSITION WHEN U FIRST STARTED RITE? I LOVE UBUNTU BUT IM TIRED OF FREAKING CANT HAVE THE OS RUNNING WITH THE DRIVERS PROPERLY. INSTALLING THIS FRUSTRATES ME.. AND BELIEVE ME IVE BEEN GOOGLING, SUDOING, DOWNLOADING AND RESTARTING ALL THE DAMN DAY AND NIGHT. PLEASE HELP.

Heres what I have and what I did etc.... I downloaded envy ng .. installed the compatible drivers for it.. i wasnt happy at all with the performance. so i decided to download catalyst 9.4.

I uninstalled the previous 8.5 version driver

I downloaded the drivers from amd for my hd 3850, typed sudo sh ./ati-driver-installer-9-4-x86.x86_64.run ... everything went fine.. i did next next next exit.. ok 

Now on my applications menu theres two ati catalyst control center.. i clicked on them and a window says that the catalyst control center for linux failed to start or something.

I tried sudo sh ./ati-driver-installer-9-4-x86.x86_64.run  --buildpkg something like that .. on my home folder the debs appeared and i clicked all of them .. some of them coulda be installed some of them not .. some of them were reinstalled..  nothing worked.. 

I ran perfect world international on wine with the 8.5 drivers but it was damn laggy graphically... 

But seeing all this failure installing the latest driver made me want to go back with the old drivers.. so i uninstalled everything with envy , restarted and instlled the thing again with envy.. 

I did a whole mess befor doing this and cant remember what i did exactly  but before i coulda run the control center and now it just dont do a thing.. i cant run perfect world .. nothing .. no compiz.. and i suppose that my catalyst drivers are not being installed while the envy thing says that everythiing is installed PUAF! 

now.. what do i do?? how do i REVERT WHAT I DID .. GO BACK TO NORMAL AT LEAST? 
AND IF ITS NOT HARD TO ASK HOW DO I INSTALL THIS STEP BY STEP CLEAR EASY AND SIMPLE FOR A DUMB LIKE ME .. NEWBIE .. NOOB HOWEVER U WANT TO CALL ME... 

I DONT NEED THE LINKS.. I GOT ALL THE LINKS IN THE WORLD .. I CANT UNDERSTAND EVERYTHING.. I FOLLOW THE STEPS AND IN SOMEWHERE IN THE STEPS I GET STUCK ...

PLEASE HELP

---

### Post by cariboo on 2009-05-17
Ranting about closed source drivers, isn't going to get you any help here.

It would help if you gave us a few more details, like what version are you using. There is a problem with the latest version of xsever-xorg and ATI drivers.

I would suggest you remove all the changes you have made, remove installed drivers, go to synaptic package manager and remove any mention of the ati drivers, then open an Applications->Accessories-->Terminal and move your current /etc/X11/xorg.conf to a backup:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then restart without an /etc/X11/xorg.conf, you should now be able to install the drivers listed in System-->Administration-->Hardware Drivers

---

### Post by Zireth ZH on 2009-05-17
woot do u mean by what version???.... im using ubuntu 8.04 lts 32 bit ... trying to install ati catalyst 9.4 for my hd 3850... 

if i go to hardware drivers to enable the drivers in there .. it seems to me that it is an old version that is compatible.. or im wrong? i want to install the latest.. not the latest compatible .. i cant play games nor watch a video when compiz is enabled.. games that arent that good in graphics are slow! ..

---

### Post by AFarris01 on 2009-05-23
To clarify for cariboo:
I believe he meant the version of the ATI graphics driver.  you can find that from the 'information' section of the Catylist control center

The problem with videos and games flickering and playing like crap is not the driver's problem...that's actually Compiz's fault.  disable compiz whenever you play games, and you will see a VAST improvement in your performance.  Until DRI2 comes out this won't be fixed (and I've heard rumors that it'll be included in the next Ubuntu release, i.e. Ubuntu 9.10).  Dont worry about what DRI/DRI2 is...just know that it's important, and it's in the process of being upgraded.

For switching off compiz, i recommend using a program called compiz-switch.  [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch) ...basically it's an icon you click before you play a game that turns off compiz, then you click it again to turn it back on.  its very nice, and i even made a little script for it so all i have to do to use it is put another command in the game launcher, before the launch command, so compiz goes off whenever i launch the game, then turns back on when i'm done... I can even post it with instructions if you like.

additionally, the drivers from 'Hardware drivers' are technically 'older,' but they are generally much more stable, and more importantly, they are better supported.  therefore, the are generally your best bet.

However, if you REALLY want to go with the 'latest and greatest,' then downloading the .run file from ATI's website, and installing with that is the right thing to do... just be sure to read their 'installation instructions' throughly so you understand what to do. 

Unfortunately, the issue of the ATI driver install not being 'user friendly' as you put it, is not an issue with Ubuntu, it's a problem with ATI not making their install process more friendly, and not testing better, or directly supporting Ubuntu.  If you want that to change, go send ATI a message...they've got a nice link on the driver download page to 'tell them how they're doing'  rant and rave there...they will be more likely listen to you.  Coming into these forums and screaming and yelling at the **_*Volunteers*_** that work in here trying to help resolve your problems isn't going to help you're case at all.  In fact, all it's going to do is piss people off, and then you get ***no help at all***, which is obviously *bad*.

I understand you're frustration...really I do, I just spent 2 hours last night trying to get the newer ATI drivers for my graphics card to play nice, cause I thought the 'older' drivers were causing some of my games to crash.  turned out though, ATI's newest proprietary driver does not yet support the newest version of X.org, which is shipped with ubuntu Jaunty (9.04) by default... but i didnt find THAT out until I had already F-ed my desktop with it (it doesnt say explicitly that it doesnt work with the new X.org in the install instructions), and i ended up having to spend 20 min in recovery mode to sort it all out.   I'll buy nVidia next time, because they tend to work better under Linux/Ubuntu anyway.  

so to sum up:
-the video problems are Compiz, not ATI.  compiz-switch can help you there
-Use the 'Hardware Drivers' driver that it suggests.  It's not that out of date, and it's better supported
-if you REALLY want to go through ATI's installer, make sure to read their install instructions thoroughly
-Complain to ATI about non-friendly install processes, as they're the ones that can fix it
-Don't yell at the volunteers that are trying to help you, unless you want no help

hope that helps

---

