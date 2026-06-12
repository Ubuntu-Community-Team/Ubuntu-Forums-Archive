---
title: "UT2004 installation-how it worked on my T42"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by Flandry on 2005-11-01
So i've had some ins and outs with Kubuntu since trying it out on my new IBM/Lenova T42. Mine is a model 2374 outfitted with a Pentium Mobile 1.7 GHz Dotham processor, 512MB PC2700 DDR RAM, the Radeon 9600 Mobile with 64MB RAM and the higher 1400x1050 resolution 14.1" LCD. One of the reasons i got this particular model of T4x is because the 9600 Mobile is the best 3D acceleration you can get in the Thinkpad T-series, and the ability to run UT2004 and other OpenGL programs on my laptop with decent performance was one of my purchasing criteria. The only possibly higher-performing option is the T42p or T43p with the FireGL T2 professional solution, which as near as i can tell is basically a "street legal" 9600 Mobile with 128 MB RAM (twice the RAM!). If you have a lowly x300 or Radeon 7500 Mobile, you may find your UT2004 experience limited, at best. If you have one of the T43s with the Intel integrated "solutions", weep quietly into your beverage while the rest of us install UT2004.

I may post another thread detailing how i got everything working (and everything i have tried on it DOES work--amazing--and with very little extra tweaking!), but this is about installing UT2004. 

First of all, make sure you have the fglrx driver installed. That is the proprietary driver from ATI for their graphics chips. If your laptop has an nVidia chip, then you will NOT want to install fglrx. ;) The radeon driver that is installed by default with (k)ubuntu is not 3d accelerated, and therefore is unsuitable for playing UT2004. I used instructions found by googling for T42 ubuntu, but it's fairly simple and the instructions are found here, as well. You basically use Adept/Synaptic to install the fglrx driver, and then modify your modules and your xorg.conf file to reflect that change. I'm too lazy to look up the detailed procedure to write here...do a search. Once the accelerated drivers are properly working (glxgears is typically how one tests this.  Type glxgears -iacknowledgethatthistoolisnotabenchmarkg and you should get numbers over 1500 FPS or so), you are ready to install UT2004. Remember that you have to reboot to start the new display driver. 

Second, you will probably NOT be able to install UT2004 from the CD directly. I believe that this is because CDs are mounted as noexec by default in (k)ubuntu, but that's just a guess. So you'll need to copy the linux_installer.sh file from the CD to your root or home partition (probably as su): 

sudo cp /media/cdrom0/linux_installer.sh / 

Yes, i copied it right to root. So sue me. 

Finally, run the install script: 

cd / sudo linux_installer.sh 

The simple install menus will walk you through the CDs, and also give the option to install the SDL source (i didn't select that option). I recommend you carefully clean off each CD before putting it in, because the optical drive in my TP is very finicky, and the first time i installed it failed at the very end of the fourth CD (crashing the install program). Not pretty. However, i simply started over with no ill effects. In order to eject the CD, you'll need to navigate up a directory level in the Konqueror window that automatically opens with the CD listing in it, and then right click on the CD icon and select "eject". When you're done, download the linux patch from the official site and install it. That will require de-archiving the patch into the UT2004 director (which if you accept the default is /usr/local/games/ut2004). It may be easiest to use ark to decompress the files onto your desktop and then copy them over as super user, so they can overwrite the files as needed. cd into the directory you decompressed the files into, and then type: 

sudo cp -r * /usr/local/games/ut2004 

And that should be it (the patch seems to include the ECE content). Fire up ut2004 by typing ut2004, and you're off! You don't need the CD in the drive to play. 

Appendix: 1400x1050 resolution for high-res laptops 

As i mentioned, my TP is of the higher-resolution variety, with a native resolution of 1400x1050. This is definitely pushing the limits of the Radeon 9600 Mobile, but in WindowsXP i was pleasantly surprised to find that i could run at that resolution in UT2004 and still have smoother, better performance than my aging desktop. YMMV, especially if you're used to playing on modern desktop hardware. It's a relative thing: to go from 15-25 fps to 25-30 fps is a nice step, and feels incredibly smooth, but going from a more sane 40fps to an admittedly less competitive 25-30 fps will drive you out of your friggin' gourd.

But i digress.  In order to make the game run at 1400x1050, you need to alter the ut2004.ini file found in your home directory (it's hidden in a dot directory called .ut2004/System), which will probably not be there until after you run ut2004 once. I made a backup of the original file, and then changed each instance of 800 and 600 for horizontal and vertical resolution (typically under headings like "full screen" to 1400 and 1050. Unfortunately, for some reason i'm only getting a fps of around 7-16 (according to the stat fps command typed in the console of ut2004) in Torlan and some other Onslaught levels, although i must say it doesn't seem that slow in actual play (ie it's actually playable). It's much less jerky than under windows, and that smoothness probably has a lot to do with the higher apparent speed. I attribute it to linux better managing memory and paging, as windows seems to have page to/from disk a lot just when something blows up or someone starts shooting me, which are, of course, bad times for the game to start jumping around. I know that there were performance issues in older fglrx drivers specifically in Onslaught, but i believe the current drivers in the repository (8.16.20) are not subject to that problem.  One thing those drivers lack that the newest drivers available from ATI have (8.18.8 at present) is PowerPlay.  That is ATI's name for the power saving functionality that shuts down areas of the chip that are not in use to decrease heat production and power consumption.  That feature would be nice, as the fan spins up and down a lot when gaming in linux, whereas i've never heard it on high in Windows.  I've not heard if performance is better or not.  However, [this massive thread](http://ubuntuforums.org/showthread.php?t=76116&highlight=fgl_glxgears) details the howto and issues installing those drivers.  I haven't yet gotten up the ambition to risk b0rking my system trying to install those drivers, and have yet to wade through the threads on optimizing 3D performance, but will post here when i have any progress to report. 

Anyway, i have some more tweaking to do. I may try running at half native resolution (700x525), which would, of course, suck. But it would be less damaging to my in-game ego. I also plan on adding 1GB more RAM soon. 

Good luck!

---

### Post by Flandry on 2005-11-07
Well it turns out that the ATI OpenGL drivers are just so bad that tweaking may not be enough to get suitable performance at the native resolution.  By benching with utbench [(see this thread)]("http://ubuntuforums.org/showthread.php?t=49329") i was disappointed to find that while i get a fairly playable framerate in WindowsXP, the poor optimization of the OpenGL drivers by ATI lead to an initial framerate of around 13.1 in utbench in Kubuntu.  By turning off trilinear filtering i get 0.5 fps more;  changing world detail From high to normal nets another 0.75 fps;  turning decals off gained 2.5 fps--but that's still only 16.8.  Ugh.  By disabling sound (not in the program, but on the command line) the fps jumped to 19.5.  Almost decent...but crippling without audible cues.  At 800x600 a much nicer 24 fps is achieved, but it's ugly as sin.  1024x768 runs at 21 fps.

[SIZE="2"]Free FPS[/SIZE]

I compromised on the sound issue.  It turns out if you change the number of channels (in the ut2004.ini file) to 16 from 32, you get about 50% of the increase of turning off sound, without losing all those important audible cues.  So after tweaking, i decided to stick for the time being with 1400x1050, which now runs at 18.3 fps in utbench.  Not ideal, but playable for someone coming from an ancient desktop.  It sure is tempting to reboot into WXP to get the extra 30-50% fps the ATI DirectX drivers can nab.  That's just not the way it's supposed to be.  There's nothing inherently better about DirectX, ATI has just been lazy; and believe me, i wanted to find a Thinkpad T with an Nvidia card.  They're just not available.  I really don't understand why a company that promoted linux as an OS, and otherwise provides a laptop as incredibly amenable to running linux, has given their business to a company like ATI that has a proven record of NOT supporting linux as well as their competition.

---

