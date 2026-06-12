---
title: "Radeon Driver on a Mobility Radeon 9600 Pro"
date: 2010-07-01
forum: Hardware
---

### Post by shrumhead on 2010-07-01
I followed the instructions found [here]("https://help.ubuntu.com/community/RadeonDriver") on installing the open source Radeon Driver for my Dell Inspiron 8600's Mobility Radeon 9600Pro.  The installation went smoothly... all of the tests listed in the installation guide came back exactly what they were supposed to and I can use full effects with no slowdown w/ compiz effects.

Now that all sounds well and good but I just have a few minor issues that aren't so big as to want to put XP back on the laptop (especially when I'm having so much fun with Linux!) but I figured I'd bring them up here just in case they were simple fixes =D  

The first issue is that when I go to switch my Visual Effects settings (in the Appearance window) from either "None" or "Normal" to "Extra", it always works but before the "Extra" setting takes effect it always does a "Searching for available drivers" which takes a good 15-20 seconds.  Again... not that big a deal but on my PC it never does a "searching for available drivers" when changing to the "Extra" setting, it simply makes the change.... which makes me wonder if I did something wrong or didn't do something.  In case it matters I'm using KMS.  I have it loading @ grub and when I made the change grub is loading at a much higher resolution so I'm just going to assume its loading correctly. 

Second issue I have should probably be in the Wine section but it ties into the first issue with the drivers so I figured it was appropriate for here.  I installed my old copy of Baldur's Gate 2 to have something to do during the downtimes at work.  I didn't think it would be an issue running it seeing as how all the compiz effects work without any issues but I am having some trouble with it.  For those unfamiliar with the game, its very old, I think it came out in the year 2000 and has the option for 3d acceleration or not.  I do believe it uses openGL by default.  

Before you start the game you can configure and test the settings and I'm at a loss!  The wine AppDB says it should be completely compatible but when I try to run it in full screen it just tears into incomprehensible shapes and lines... when I run it in windowed mode I can at least see the menu clearly but the mouse flickers non-stop and every time the menu has to do an animation (when you click one of its options), it just lags out for about 30 seconds before completing the animation.  I can't even imagine what trying to load into the game would be like.  At first I thought it might be a problem with wine accessing the game but it only lags when there's any sort of animation on the screen so I assumed it had to do with the driver.

EDIT:: To better explain my thought process... I assumed that perhaps the game/wine isn't correctly finding the installed RadeonDriver because even in changing my appearance settings it has to do a thorough search for the driver.... maybe its not "on the surface" but something that has to be "loaded up"?

Any help or explanation about these 2 very minor issues would be greatly appreciated =D  TY!

---

