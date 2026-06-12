---
title: "How to get Nvidia geforce 420M working?"
date: 2010-09-21
forum: Hardware
---

### Post by chris_gs on 2010-09-21
Hi,

I've just got a new Acer Aspire 5742G, its a 64bit system with a Nvidia Geforce gt 420m with 1gb dedicated ram.
I'm trying to get ubuntu lucid, latest version (2.6.32-24) to work on it.  I can only get it to use a maximum resolution of 800x600.
The nvidia driver was originally not availble, so I installed nvidia-current and the hardware drivers tool found and activated the driver.  It didn't make any difference.
The NVIDIA X Server settings tool says I'm not using the nvidia driver and suggests nvidia-xconf
I ran nvidia-xconf and it created an xorg.conf - which produced a blank screen,
I've tried old solutions to that by modifying the xorg.conf and adding display options, all to no avail.

I was wondering if anyone was aware how to get this device working... is one of the older drivers compatible?  I've also tried installing the lastest driver from NVIDIA, the closest of which is the 480m driver, it produces the same effects as nvidia-current.

Has anyone got any ideas out there?

Thanks,
Chris

---

### Post by chris_gs on 2010-09-21
Well, its the old thing... as soon as you ask for help somehow it works by itself? go figure?
Anyway, I managed to fix the problem minutes after I wrote the above post... for anyone else who's struggling... I'm not sure what change, but the process i followed was this:

Download the latest version of the nvidia driver from [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

go to terminal 1 [ctrl]-[alt]-1
log in
then 

sudo service gdm stop
run the downloaded driver via
sudo sh ./NVIDIA-Linux-x86_64-256.53.run   (256.53 was the version of the driver i'm using)

the installer complained on my machine that the distribution provided script failed, did i want to continue, yes.

it asked if i wanted to 32bit compatible opengl installed, yes
then to autoconfig x - yes
it then exits out
type 
"sudo service gdm start"
and voila!  the NVIDIA X Server config tool worked and i could get my max resolution!

strangely i'd done this once before and it didn't work... but it did this time....

Thanks for the help I know I would've got on this form... it's saved my life many times!!!
Chris

---

### Post by z987k on 2010-10-21
fwiw, I just bought the same laptop and 10.10 installs and everything thus far works perfectly.  Nvidia chip is detected and drivers are offered for install.

---

### Post by PhilEvans on 2010-12-03
Out of interest, do either of your systems have a second card as well?
I have a Dell XPS L501x, which has the Nvidia Ge Force GT 420M, and an Intel i915, and I cannot for the life of me get the nvidia drivers to work.

The Ubuntu packaged nvidia modulate doesn't support this card, so like you I downloaded the file you mention, and ran the install as you did. And when I start X (kdm not gdm as I'm using Kubuntu) I just get a blank screen, or get returned to the console. Oddly, the Xorg log file doesn't seem to report errors, the server just doesn't start.

Any ideas?

(PS I can then get X to start by removing my xorg.conf file. In fact, that's just about the only way X will start! Of course, this does not use the nvidia drivers).

---

### Post by jsonder on 2010-12-03
> **z987k said:**
> fwiw, I just bought the same laptop and 10.10 installs and everything thus far works perfectly.  Nvidia chip is detected and drivers are offered for install.

What happened when you installed?  I've installed 10.10-64bit on a Dell XPS L501X and trying to get the nVidia driver to work dumps me to a terminal.

The default ubuntu video control driver is giving me 1366x768 so I can't complain about the resolution.

---

### Post by esteban.feldman on 2010-12-05
Same here with L401X

---

### Post by losphiereth on 2010-12-08
I've got the same problem of PhilEvans with the same laptop model, somebody have already make the graphic card works?

Thank's in advance

---

### Post by tylerwagler on 2010-12-15
I have the same problem on the L501X here... really frustrating.  How about that two finger scroll too?

---

### Post by efflandt on 2010-12-15
If you need the most recent nvidia drivers for Lucid or Maverick (and have not messed around with trying to manually installing them from nvidia.com), you can get them by adding x-swat to your repositories [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Basically do:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

If you have not activated nvidia drivers yet, go to System > Administration > Additional Drivers (or Hardware Drivers in Lucid), "activate" nvidia, and reboot.

If you already activated nvidia earlier, just open Synaptic, type nvidia in Quick search, and reinstall nvidia-current, nvidia-settings, and nvidia-current-modaliases.  Then reboot.

---

### Post by tylerwagler on 2010-12-16
After some reading on the nVidia linux support forums I have found that nvidia has no intention of ever supporting systems with optimus technology. Looks like I just spent $1500 on a laptop I can't use linux on. Yay!!
Post #2 is the winner: [[COLOR=#444444]http://www.nvnews.net/vbulletin/show...77#post2183477[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477")

---

### Post by asdir on 2011-02-02
> **tylerwagler said:**
> After some reading on the nVidia linux support forums I have found that nvidia has no intention of ever supporting systems with optimus technology. Looks like I just spent $1500 on a laptop I can't use linux on. Yay!!
Post #2 is the winner: [[COLOR=#444444]http://www.nvnews.net/vbulletin/show...77#post2183477[/COLOR]]("http://www.nvnews.net/vbulletin/showthread.php?p=2183477#post2183477")

How come then, that the guy who started this thread got his optimus card to work? Is the difference maybe that there is a second card involved whenever it is not working?

---

### Post by realzippy on 2011-02-02
> **asdir said:**
> How come then, that the guy who started this thread got his optimus card to work? Is the difference maybe that there is a second card involved whenever it is not working?

He did not get the nvidia driver to work with hybrid graphics,he must have disabled the intel.
Optimus basics:
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by TuxOfGermany on 2011-02-26
I'd really like getting to know how to disable intel graphics. Anyone knowing a solution?

---

### Post by realzippy on 2011-02-26
...read the above given link.
You need a "switch" in your BIOS,otherwise:
No way.

---

### Post by TuxOfGermany on 2011-02-27
Tanks. So I'm not able to use the Nvidia graphics. I hope someday Acer will publish a BIOS update where we can choose such options.

---

### Post by TuxOfGermany on 2011-03-01
I've contacted Acer about an BIOS update fixing the problem of having no choice to deactivate intel graphics. Their answer was:
> Informationen ob es ein entsprechendes BIOS geben wird, liegen aktuell  noch nicht vor. Sobald es zu diesem Thema konkrete Informationen gibt,  werden diese auf der Acer Webseite [www.acer.de]("https://freemailng0701.web.de/jump.htm?goto=www.acer.de") veröffentlicht. In English: > They can't say if there will be an BIOS update anytime. If it's aviable it will be published on [www.acer.com]("https://freemailng0701.web.de/jump.htm?goto=www.acer.de") If this would help us. But that's typical Acer answer :evil:

---

### Post by T3Ra on 2011-03-11
I am on a Dell L501X ... I have tired installing/activating the NVIDIA drivers both manually (from the .run file) and from the "Additional Drivers" utility.
The drivers seems to have been installed .. but X keeps giving me *"No screen found"* error... the only workaround i found was to remove the     * [COLOR=DarkRed]Driver         "nvidia"[/COLOR]*[COLOR=DarkRed] [/COLOR] from the Xorg Conf  [COLOR=DarkRed]*/etc/X11/xorg.conf*[/COLOR]

I am just not able to dim my screen ,,, and i guess my eyes are about to pop out :P
Please help!

---

### Post by realzippy on 2011-03-11
Welcome!
..please read the "nvidia optimus" links from this thread to get a clue about the problem.You will not be able to use the nvidia-driver,maybe you can [switch off your nvidia card]("http://linux-hybrid-graphics.blogspot.com/2011/02/linux-dell-xps-l501x-switching-nvidia.html") to save battery power.

---

### Post by T3Ra on 2011-03-11
I have tired what realzippy suggested but i am Still not able to dim by screen....

I think (not sure) but i have turned down nvidia .. as suggested here : [https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html](https://lists.launchpad.net/hybrid-graphics-linux/msg00450.html)

My batter usage has come from 2000mW to ~ 1480 mW

But the problem remains ... the screen is just too bright ! 

Suggestions?Fixes?!

---

### Post by realzippy on 2011-03-11
[http://ubuntuforums.org/showthread.php?t=1636959](http://ubuntuforums.org/showthread.php?t=1636959)

Edit:
congrats for 2000mW to ~ 1480 mW;
On my laptop this doesnot work unfortunately...

---

### Post by T3Ra on 2011-03-11
OH!! Thanks a lot mate .. really really helped!!

What i Did to (supposedly) turn off nvidia :
[I]$ git clone [https://github.com/peberlein/acpi_call](https://github.com/peberlein/acpi_call)  
$ cd acpi_call
$ make
$ insmod ./acpi_call.ko
$ ./m11xr2.sh off[/I]

Thats it ... The battery usage really came down!

*$cat /proc/acpi/battery/BAT0/state*
*(from)*
present rate:            1778 mW
*(to)*
present rate:            1236 mW


I am using a 9 cell ... will update this post on with and without nvidia discharge times

---

### Post by iammeagain on 2011-03-12
^ That is what I did here: [http://ubuntuforums.org/showthread.php?t=1703301](http://ubuntuforums.org/showthread.php?t=1703301)

Although you must run it each time you boot. I am using a hack job way to get around that by running a script at login(its on the 2nd page I believe). But if someone can figure out how to load the module into the kernel at boot that would be great. From there we could probably make a simple on/off switch to control the nvidia. Almost giving us manual control of the optimus. Although Idk for sure that linux will make use of the Nvidia at all while it is on.

---

### Post by realzippy on 2011-03-12
The [GUI]("http://digitizor.com/2010/10/09/how-to-switch-between-gpu-in-ubuntu-10-10/") already exists;you have to install GCC...

Load module at boot:
eg:
[http://robbyx.net/blog/?p=190](http://robbyx.net/blog/?p=190)
[I]"Let’s make this a permanent change. First load the module..."
[/I]

---

### Post by iammeagain on 2011-05-02
Got busy so sorry for the late reply. The first link wasn't usable because it appears to be for Ati cards. The second was loads of help though. Thanks a bunch for that one. =D
I was able to revise [a better way]("http://ubuntuforums.org/showpost.php?p=10754116&postcount=25") going about disabling the 420m

---

