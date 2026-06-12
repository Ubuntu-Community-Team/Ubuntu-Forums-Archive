---
title: "[SOLVED] Nvidia Geforce 9800 GT driver question"
date: 2008-09-03
forum: General Help
---

### Post by Holonet on 2008-09-03
I just bought the aforementioned card because my 7600 had a crappy fan and it stopped and fried itself.

Once I got it up and running, I noticed the color correction settings were still in effect, which I had enabled in the previous card, but the restricted drivers (which I had installed for the older card) indicated none in use.  I found on Nvidia's website, that there was a linux 64-bit driver available.  I downloaded it and installed it, and then gnome would not start up.  It came up once screwed up with a low-graphics mode message mostly off the screen, but for the most part, just would try to restart gnome and fail and go back to the prompt.

I thought perhaps there was some corruption or conflict, so I reinstalled Ubuntu (64-bit 8.04).  Everything works now, but it still does not indicate any available restricted drivers...yet there is one on the site.  Perhaps the Ubuntu team knows that it doesn't work properly and that is why it's not there?  Can anyone confirm or deny this?

It seems to be working fine without the restricted driver, but I'm not sure if it's equivalent or better than the Nvidia driver.  If it is, it didn't used to be for my old card.  If anyone could just clear up the fog on this issue, it'd be much appreciated. :popcorn:

---

### Post by Victormd on 2008-09-03
As far as I know, the restricted driver and nvidia driver are equivalent. Generally, the driver off of the nvidia site will generally offer more resources/functionality but all in all, they're pretty much the same (someone please correct me if I'm wrong...).

---

### Post by Holonet on 2008-09-03
Thanks for the reply.  That's good to know, but doesn't really tell me much about my question, which I just realized I should have clarified a bit.

I'm a little confused as to why the one I got from the site which is meant for linux x64 resulted in a non-working mess, as well as why no driver appears in the restricted driver thingamaboo for me to enable when using the 9800.  Furthermore, since that is the same situation I had before, it seems likely to me that the one off the site would screw up again, so if there is reason to believe otherwise, or something else I should do, I'd like to know that before proceeding again and getting a mess.

---

### Post by Victormd on 2008-09-04
Ok... I thought you got it going and just wanted to know the difference... :)

This is a long shot, but I think the 9800 isn't supported by the restricted-driver (as I mentioned, the driver from the Nvidia site will provide more functionality). Why the driver downloaded from the nvidia site did not work, I don't know, it's a fairly straight process to install. Have you tried using Envy to install the driver?

---

### Post by Holonet on 2008-09-04
Update here...  I haven't tried envy, but I don't think I need it.  After reinstalling Ubuntu, I tried again and it seemed to work.  I just had to install the libc so the driver could build its own kernel interface, and the driver then worked fine.  What was wrong before is beyond me.

However, to add a twist on it, right now it works fine, after I install it, but every time I restart the computer, it fails to load the graphics driver (from what I can see) and goes into low graphics mode.  I can get in, reinstall the driver, and it works again, but then I have to do it all over again if I restart the computer.  Restarting X doesn't seem to do it...just restarting the computer itself.

It seems pretty ridiculous to me if my card is not supported by the driver, being it's fairly modern...  In addition, it's the driver that the nvidia site led me to after I input my exact model card; and apparently, nvidia supports linux 64 bit...or pretends to.  In any case...anyone have a clue what's going on?

---

### Post by Holonet on 2008-09-04
I just tried envy for fun, and it gave an error, indicating the card may not be supported by the driver.  Is this possible?  The website made no indication.  This really is unacceptable...  I'm not going back to Windows over it, but this is a fundamental problem.  Is there something to be done about it?

---

### Post by genesis2seven on 2008-09-04
I have this same problem. I just got a new Dell XPS 630 with Dual Nvidia Geforce 9800 GT cards. Tried multiple fresh installs of both 32 bit and 64 bit Ubuntu 8.04. After the install fan is pegged at 100% and no compiz etc. 

I tried installing the nvidia-glx-new driver and that got the fan under control but still no compiz and performance is buggy, performance is subpar to say the least.

I tried going the envy route which afterwards allowed my to briefly enable compiz but then after I enabled dual monitors it went right back to crappy performance and compiz dropped again.

Manually installing the latest driver from the Nvidia site didn't afforded a different outcome either.

This is super frustrating!!!! Nvidia needs to pull it together. If anyone can help it would be GREATLY appreciated. I'm up with dual monitors and the fan under control on the Envy install of the 173.14.12 driver without Compiz but not being able to utilize my new hardware sucks.

The Nvidia site and Envy both provide the 173.14.12 driver. The Ubuntu repositories provide the 169.12.

---

### Post by Holonet on 2008-09-04
I haven't had any problems with the fan and compiz not working at all.  Like I said, right now, the only problem is it all goes kaput when I restart the computer (will try to start gnome and fail and end up in low graphics mode)...but an X restart doesn't cause any problems.

Ditto on the frustrating part though.  The company-made driver which includes this processor, and is meant for the exact system it's used on won't work...totally unacceptable, especially for a fundamental component.

I can still reinstall the driver and it works fine.  Does anyone know what could possibly happen that would cause this--something that happens during a computer restart but not an X restart?

---

### Post by genesis2seven on 2008-09-04
I've found rumors in a few other forums that there is a 177 beta version driver from Nvidia that works much better that two previously listed but haven't found any instructions on install.

---

### Post by Holonet on 2008-09-05
[http://www.nvidia.com/object/linux_display_amd64_177.13.html](http://www.nvidia.com/object/linux_display_amd64_177.13.html)

The driver is right here...though I'm a little confused...  It says it was released in June, as opposed to under 2 weeks ago for the windows versions.  It says beta driver on the nvidia splash screen before gnome starts, but not on the site for the Linux version.  As for installing, it worked for me the exact same way as the standard nvidia driver.  Just stop X:

sudo /etc/init.d/gdm stop

Run the file:  sudo sh nvidiafilewithgratuitousname.run

Then Start X again.

sudo /etc/init.d/gdm start

THat's what I have to do every time I start the computer because...unfortunately for me, this driver behaves exactly the same as the last one.  Curses...curses, I say.  I'm about to reinstall Ubuntu again, just in case that wipes out something the old driver did, which...given my experiences, seems entirely plausible.  Moments like these serve to really irritate me because they remind me of the inadequacies which I thought I had escaped by retiring Windows to the circular file.  Will report back...with better news I hope. ](*,)

---

### Post by Holonet on 2008-09-05
Alright, got the SOB in the back room with no windows, and it's going down.  I did my reinstall of Ubuntu, and immediately after, tried installing the 177 driver.  Then I restarted, and no problem.  I then proceeded to do the software updates which were, of course, available, tried restarting again, and crap....

So unless this issue manifests itself after one restart, then I owe Nvidia an apology...and a booby prize to the devs of whichever package upgrade I find does this on yet another reinstall...

---

### Post by genesis2seven on 2008-09-05
It was the same way for me when I installed the EnvyNG driver. It seemed to work after the initial install but then crashed after I updated and restarted. I don't have to start and stop X server but I am back to very limited functionality. Even right after the EnvyNG install things didn't work even close to par but was better than the driver from the repos.

---

### Post by Holonet on 2008-09-05
Alright, finally have this, I think.  I did the updates one by one and restarted the computer after everyone as a controlled experiment, and the monkey wrench was the linux-headers-2.6.24-19/generic.  I am currently doing an update of everything but those, as well as the linux-image update, to see if I remain in high graphics mode.  I had to reinstall AGAIN before doing this because synaptic wouldn't let me force the version down on those updates.

---

### Post by Holonet on 2008-09-05
Confirmed...I updated everything but the linux kernel image and header files, and the problem is gone.  I'd say this is worth flagging in some fashion...

---

### Post by Holonet on 2008-09-05
Ok another update here.  It seems installing nvidia-glx causes the same problem on my machine.  I was able to fix it by using the original (backed up) xorg.conf file and reinstalling the driver.  In the end, I'm not using the beta driver.  While using it (just before the nvidia-glx mishap), it appeared fine, but I could not enable desktop effects.

In any case, if someone could refer me to just what process I should embark on in order to bring those header files to someone's attention...

---

### Post by alexbird on 2008-09-28
Bump! 

I was just about to buy one of these.  Would really like a painless install ;o)

It is a fanless one, so not bothered about fan behaviour, but I do care about power consumption.  
Also, if I spend GBP 100 and don't get all the desktop bling known to man....

Then again, how often is a kernel update really neccessary?  Is this really going to affect me?

I think I've just written the sort of post that sinks like a lead balloon, but maybe some kind soul will help me.  
I badly need to replace my stinking matrox, which caters for zero bling, zero google earth, etc etc.

---

### Post by netmanny on 2008-10-13
Glad it worked for you. 
:confused:I had try all your suggestions all I get is back to vesa drivers it will not even acknowledge that it has an nvidia 9800 GT card. maybe is my mother board is one of those ta come in the new gateway GT5662 Desktop Computer
# AMD Phenom™ 9500, 64-bit quad core processor

    * Each core operates at 2.2 GHz
    * 2 MB L3 cache
    * 3600 MHz system bus 
ECS MCP61PM-GM AM2 mATX motherboard
# NVIDIA® GeForce® 6150SE chipset
# 4096 MB DDR2, 667 MHz, (PC2-5300) dual channel memory (two 1024 MB and two 1024 MB modules)
# 1000 GB, 7200 RPM, SATA II hard drive
# DVD ±RW, 18X super multi-format dual layer drive with Labelflash™ support
# 15-in-1 high speed digital media manager
# Docking bay for optional Gateway 2.5-inch removable USB hard drive
# Integrated Realtek RTL8201N 10/100 MB LAN
# 56K PCIe Data/Fax modem
# (ATI Radeon™ HD 2400XT video)Upgrade to Nforce NV 9800 GT

I even tried Suggestions from the Nvidia site and forums nothing works all defaults to a crash error or Defaults to Vesa drivers.
:confused:

If some one has any Ideas Please tell.
TIA.

---

### Post by genesis2seven on 2008-10-13
Everything is running fine for my on my XPS 630 with the Nvidia 9800 GT now. I'm running 32bit Ubuntu 8.04. I did a clean install. Let all updates run. Then I installed the nvidia-glx-new driver and the Nvidia control application. Everything works well. Guess some updates just needed to come through. From what I've read in the forums and blogs the newest Nvidia driver will come prepackaged and should auto-recognize in Ubuntu 8.10. I wouldn't feel bad about buying the 9800 GT.

---

### Post by netmanny on 2008-10-13
Yes that is how I solved my problem .. I clean install ubuntu 8.10
and it did setup every thing ok including my HVR 1600
cool
exept I get errors at boot. but as long it works I don't care.
this is the errors for those that like to know.

rio0/input/input1
[    2.135763] fuse init (API version 7.9)
[    2.144650] uvesafb: failed to execute /sbin/v86d
[    2.144723] uvesafb: make sure that the v86d helper is installed and executable
[    2.144800] uvesafb: Getting VBE info block failed (eax=0x4f00, err=-2)
[    2.144877] uvesafb: vbe_init() failed with -22
[    2.144956] uvesafb: probe of uvesafb.0 failed with error -22
13.664309] cx18-0: VBI is not yet supported
 14.154135] cx18-0: Disabled encoder IDX device
 
there is also a usb dev error but I dont have the exact code.
 It all works for me now.
:popcorn::popcorn::)  only 64 bit version works for me the i386 does not work for some reason i installed the 32 bit because of compatibility is not up to par to 64 bit yet. but that did not work so I re installed the amd_64 again.

---

### Post by psypher on 2008-10-16
hey all. also had  major issues with 64bit and 9800 gt. this site helped a lot:
[http://www.jaysonjc.org/ubuntu/installing-nvidia-drivers-on-ubuntu-804-hardy-heron/](http://www.jaysonjc.org/ubuntu/installing-nvidia-drivers-on-ubuntu-804-hardy-heron/)

But i downloaded the latest 177 driver. the key to fixing the low res/failsafe issue on reboot after the install, is to blacklist the nv and nvidia_new modules. as soon as i added that, everthing started working. I don't think it was because I re-installed as I tried that several times. I had to manually edit my xorg.conf afterwards though as it did not seem to detect my screen automatically. So i compared it to my working xorg of another pc (same screen) and everything is perfect. Wow that took almost a whole work day to just install and setup the graphics

---

### Post by jyaan on 2008-10-17
im having same problem with 9800gt ultimate, where the driver works before restarting. but once i reboot/re-power i end up in 800x600 vesa. i tried blacklisting nv and nvidia_new, but that hasn't changed anything. the driver still fails to load automatically. all you did was add 
> 
blacklist nv
blacklist nvidia_new

at the bottom of /etc/modprobe.d/blacklist ?

im hoping to avoid a reinstall, as i have a lot of important things set up at the moment. but at least i have a separate home directory if im left with no other choice. but honestly, if it comes to that ill probably just go back to gentoo. anyways, since intrepid uses the new 2.6.27 kernel and 177.80 is apparently supported, has anyone been able to compile 2.6.27 and get 177.80 working?

---

### Post by jyaan on 2008-10-17
thanks so much for that link psypher. it's actually working now! i never thought i'd see the day... so apparently the blacklist in /etc/default/linux-restricted-modules-common did the trick. i also removed /etc/init.d/nvidia-kernel.

---

### Post by dns-en on 2008-10-23
Im having the same problem 9800 gt the 32 bit drivers wont work at all. Ive tried compiling the new beta driver and tried the repository drivers. They compile and say their installed but it wont load the driver.

---

### Post by juanpecan on 2008-11-09
Needed my Scribus DTP performance to be wayyy increased, so I picked up the 9800 GT (1gb) this morning.

After a day of restarting into low graphics mode, I bit the bullet and upgraded to 8.10 (from 8.04).

Finally was able to install the 177 driver easily...Nvidia x server settings app running, recognizing monitor, and claiming full performance...

AND I AM VERY DISAPPOINTED!

Scribus still runs at a snail's pace, if not worse than before with 8.04 and my integrated video card!

It looks like 8.10 is across-the-board slower! My workflow remains bottlenecked at scrolling through my documents and waiting for text boxes to become ready for editing. $200 for...???!


Would a complete reinstall help or am I stuck wanting to bash my head in with my keyboard while waiting to input a keystroke or mouse click every 40 seconds in Scribus? Do I really have to wait till April for 9.04 and hope it reverses the trend of every new release being slower than what came before?? ****, I feel like I'm back in vista!

I have a 32 bit system. Please tell me something good somebody. Complete reinstall might help?

---

### Post by genesis2seven on 2009-02-21
After experimenting with some less than stable settings this week I decided to wipe my Dell XPS 630 and do a fresh Ubuntu 8.10 install today. I remembered there being a quirk about the NVIDIA driver the first time I installed but couldn't remember what exactly so here's some quick documentation on the problem/solution for anyone else in the same boat.

System:

XPS 630
Dual NVIDA 9800 GT Video Cards
......

I've found the 180.29 driver to perform much better than the currently recommended 177.xx driver. I've also found that at least on my system whether I install manually, through apt-get or even if I use System>Administration>Hardware Drivers to install the 177.xx driver that the X server breaks upon reboot. My step by step is below. This is assuming a fresh install.

1. Download the 180.29 driver from the NVIDIA download page.

2. Purge all NVIDIA packages installed by default.

    $sudo apt-get --purge remove nvidia*

3. Make sure you have build essential installed.

    $sudo apt-get install build-essential

4. Get the PCI number of your graphic(s) cards.

    $sudo lspci | grep VGA

The PCI numbers will be in the ##.##.# format but you will need to add them to your xorg.conf file in the PCI:##:##:# format.

5. Stop the X server

    $sudo /etc/init.d/gdm stop

6. Press Alt+F1 to get a command prompt

7. Run the NVIDIA install utility and make sure you choose yes to the autoconfig option.

    $cd Desktop (or the folder you downloaded the NVIDIA package to.)
    $sudo sh NVIDIA-Linux-x86-180.29.pkg1.run

8. Once the installer completes you need to add the Busid entries for your video cards to the xorg.conf file before you reboot.

    $sudo nano /etc/X11/xorg.conf

    Device
    ....
    Driver "nvidia"
    Busid "PCI:##:##:#"
    ...

If you have multiple cards then copy/paste the Device section and add the second Busid entry.

9. If you have an SLI setup you can also add the line

    Device
    ....
    Driver "nvidia"
    Busid "PCI:##:##:#"
    Option "sli" "auto"
    ...

10. Reboot and you should be in business.

11. Additionally if you're running a duel monitor you'll want to make sure you have the NVIDIA X Server Settings utility installed in System>Preferences>NVIDIA X Server Settings. If you don't then just run

    $sudo apt-get install nvidia-settings

12. You'll need to run the NVIDIA utility with root privileges in order to save any changes you make.

    $sudo nvidia-settings

13. On the X Server Display Configuration screen select the inactive monitor, click the Twinview radio button, click the Ok button, click the Save to X Configuration File, click the Quit button. (Twinview is NVIDIA's proprietary multi-monitor feature. Some people prefer the Seperate X screen option because its not proprietary but you're already using a proprietary driver and I haven't gotten Compiz effects to work with Serperate X screens. If you know how please leave a comment.)

14. Push Ctrl+Alt+Backspace to restart X and you should be up and running with dual monitors.

---

### Post by elaterite on 2009-03-31
I've written a more comprehensive, or alternate version if you perfer, for installing kubuntu-8.04.2-desktop-i386 (Hardy) with a MSI GeForce 9800 GT & NVIDIA 180.44 Drivers (release 3/30/2009). It's an extrapolation from this and several other sources. Follow this link: [http://tinyurl.com/cxsbdu](http://tinyurl.com/cxsbdu) And thanks genesis2seven your post was very helpful!

---

### Post by ccnjim on 2009-06-10
> solution=12. You'll need to run the NVIDIA utility with root privileges in order to save any changes you make.

$sudo nvidia-settingsgenesis2seven
 I can't thank you enough for posting this tidbit.

 I have spent days trying to resolve my save to X configuration file problem.
 This worked instantly!
 I've logged out of X, and restarted and both monitors display as configured. Many thanks! Jim

Ubuntu Jaunty 9.04 x64

---

### Post by Jimbo5584 on 2009-12-02
I really don't understand it, my 9800 GT worked fine up until 9.10 (Karmic) then all of a sudden I was getting stability issues and ended up reinstalling, only to find that the standard synaptics nvidia drivers were causing all sorts of issues.  

Although the drivers do not appear in the hardware driver utility after following the steps described they are working correctly. 

Thank you soo much.

---

### Post by LiquidZero on 2010-10-01
> **Holonet said:**
> [http://www.nvidia.com/object/linux_display_amd64_177.13.html](http://www.nvidia.com/object/linux_display_amd64_177.13.html)

The driver is right here...though I'm a little confused...  It says it was released in June, as opposed to under 2 weeks ago for the windows versions.  It says beta driver on the nvidia splash screen before gnome starts, but not on the site for the Linux version.  As for installing, it worked for me the exact same way as the standard nvidia driver.  Just stop X:

sudo /etc/init.d/gdm stop

Run the file:  sudo sh nvidiafilewithgratuitousname.run

Then Start X again.

sudo /etc/init.d/gdm start

Okay.. so I have tried to stop X, but now I'm getting errors within the installer:

"The Nouveau kernel driver is currently in use by your system.  This driver is incompatible with the NVIDIA driver and must be disabled before proceeding.

For some distrobutions, Noveau can be disabled by adding a file in the modprobe configuration directory.  Would you  like NVIDIA-installer to attempt to create this modprobe file for you?

[yes]

The modprobe configuration file to disable Nouveau, /etc/modprobe.d/nvidia-installer-disable-noubveau.conf has been written."

Here's the problem: Now that this file is created, I don't exactly know what's going on.  Ubuntu froze up on me.  On a reboot, I'm stuck looking at the non-animated image of "ubuntu" with the five red dots underlining the logo.  

The driver I am installing came directly from Nvidia's site for my nVidia 9800 GT pcie 512 graphics adapter.  

Ubuntu Linux Lucid 10.04 LTS 64-bit.

Bear in mind that I have no active internet connection, either.. which probably makes things even more complicated for me.

The driver version is NVIDIA-Linux-x86-64-256.53.run .

---

