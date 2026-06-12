---
title: "AMD (ATI) Catalyst 11.1 for linux now out HD6xxx HD6850"
date: 2011-01-27
forum: Hardware
---

### Post by BrokeMahPC on 2011-01-27
AMD (ATI) Catalyst 11.1 for linux now out with a listing for HD6xxx series cards.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I guess this means my HD6850 is now supported in Linux - anyone tried the driver yet?
Not sure about other cards as there is nothing in the release notes apart from install instructions

Also there were lots of xorg updates plus a kernel update for Ubuntu 10.10 over the last few days.

Does anyone know if we can activate the administration - hardware drivers yet? Or is the only option to download the above?

edit--------------------
HD 6xxx are not officially supported with this driver - you still get the watermark.
on the wiki:
[B]Cards in this group are unsupported as of Catalyst 10-12. The  Catalyst  driver may run on these cards, but it is not guaranteed (and  you will be  stuck with an "Unsupported Hardware" watermark unless you  hack the  control file). Full open source support is forthcoming in  Linux kernel  2.6.38.
[/B][B]* CAICOS      Radeon HD 6350
* TURKS       Radeon HD 6670
* BARTS       Radeon HD 6850/6870
* CAYMAN      Radeon HD 6950/6970[/B]
Natty Narwal will ship with 2.6.38 in AprilIt's at RC2 stage in the repos.

---

### Post by artemeas on 2011-01-29
I have something that I can't understand...

sudo sh /usr/share/ati/fglrx-uninstall.sh

all done. double check. no aticonfig, no amdcccle on my system.

then reboot

after reboot no awn-transparency, no desktop effects so it means catalyst is uninstalled.

sudo sh ./ati-driver-installer-11-1-x86.x86_64.run

it tells me 812 going to be installed. I choose automatic, after 1 minute I get Catalyst was installed successful. 

reboot. effects are back. I start amdcccle and it tells me:

Catalyst Version: 10.12
Driver Packaging Version 8.801-101125a-109596C-ATI
2D Driver Version: 8.81.5
Catalyst Control Center Version: 2.13
RandR Version: 1.3

But I do not have 10.12 installer anymore. I start 11.1 and it tells me in console that it's a 812, so 11.1.

But why it still shows 10.12 after reboot.
Fglrx was uninstalled correctly, because right after *-uninstall*.sh script finishes, there are no ati* or amdcccle files on my system.

---

### Post by Yellow Pasque on 2011-01-29
Make sure you completely remove the old Catalyst driver and double-check that nothing remains in /etc/ati
Install the driver using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

---

### Post by artemeas on 2011-01-30
> **Temüjin said:**
> Make sure you completely remove the old Catalyst driver and double-check that nothing remains in /etc/ati
Install the driver using this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)

thanks deleting /etc/ati helped.

but in amdcccle now is no string about catalyst version..
it tells only: 
-Software
 Drivaer Packaging Version 8.812-110104a-111995C-ATI
 2D Driver Version 8.81.5
 Catalyst Control Center Version 2.13
 RandR Version 1.3

---

### Post by xvart on 2011-01-30
I have this working sort of, the auto install did nothing meaningful, but the auto allows you to create distro specific install files. I did this then ran "sudo dpkg -i *.deb". this seems to have done said trick of installing the drivers properly. 

I also just dropped this over the auto install, I didn't bother removing anything. 

I did an aticonfig --initial to build the xorg.conf

I have compiz effects and stuff working fine, just the dual screen thing gives 2 separate X windows, I wanted 1 big expanse, no idea on that yet.

The graphical "ATI Catalyst Control Center" was dropping the new xorg.conf files in my home directory so every new config I tried came out the same as the current one as it would :(.

When copied across they do as advertised.

---

### Post by DealReal on 2011-01-31
> **BrokeMahPC said:**
> AMD (ATI) Catalyst 11.1 for linux now out with a listing for HD6xxx series cards.

edit--------------------
HD 6xxx are not officially supported with this driver - you still get the watermark.
on the wiki:
[B]Cards in this group are unsupported as of Catalyst 10-12. The  Catalyst  driver may run on these cards, but it is not guaranteed (and  you will be  stuck with an "Unsupported Hardware" watermark unless you  hack the  control file). Full open source support is forthcoming in  Linux kernel  2.6.38.
[/B][B]* CAICOS      Radeon HD 6350
* TURKS       Radeon HD 6670
* BARTS       Radeon HD 6850/6870
* CAYMAN      Radeon HD 6950/6970[/B]
Natty Narwal will ship with 2.6.38 in AprilIt's at RC2 stage in the repos.

That still says Catalyst 10-12.
I can't get mine to work in Mint 10. I've tried both from the website and from the Proprietary Drivers option. The website ones cause my system to crash before login with the watermark. The Proprietary ones just don't do anything and I can't start aticonfig.

---

### Post by BrokeMahPC on 2011-01-31
> **DealReal said:**
> That still says Catalyst 10-12.
I can't get mine to work in Mint 10. I've tried both from the website and from the Proprietary Drivers option. The website ones cause my system to crash before login with the watermark. The Proprietary ones just don't do anything and I can't start aticonfig.

Well I tried to install Catalyst 1.11 - when I tried to run aticonfig it returned - "No supported hardware found"
As above it also dropped most of the config and deb files into my home folder! Ubuntu crashed to a tty upon restart  so I'm not sure what level of support they are offering 6xxx cards but it's no use without some detailed install instructions.

Hopefully the Wiki will catch up soon!

---

### Post by BrokeMahPC on 2011-01-31
> **xvart said:**
> I have this working sort of, the auto install did nothing meaningful, but the auto allows you to create distro specific install files. I did this then ran "sudo dpkg -i *.deb". this seems to have done said trick of installing the drivers properly. 

I also just dropped this over the auto install, I didn't bother removing anything. 

I did an aticonfig --initial to build the xorg.conf

I have compiz effects and stuff working fine, just the dual screen thing gives 2 separate X windows, I wanted 1 big expanse, no idea on that yet.

The graphical "ATI Catalyst Control Center" was dropping the new xorg.conf files in my home directory so every new config I tried came out the same as the current one as it would :(.

When copied across they do as advertised.

OK I get that too - the .deb files created by Catalyst 1.11 all turn up in my Home folder - did you copy them to etc/ati ?

---

### Post by BrokeMahPC on 2011-01-31
I get as far as Aticonfig --initial and:
"aticonfig: No supported adapters detected"

looks like it's back to windows for me - I have spent hours researching this and trying half a dozen methods and 2 complete reinstalls. All for a driver!

---

### Post by Yellow Pasque on 2011-01-31
> **BrokeMahPC said:**
> looks like it's back to windows for me - I have spent hours researching this and trying half a dozen methods and 2 complete reinstalls. All for a driver!
Patience...

---

### Post by mbutash on 2011-02-02
I'm just now trying to get these working on a newly purchased 5870 eyefinity 6 card with 4 monitors under 9.04 64bit ubuntu.  Thus far I can only get them to work as 4 individual x sessions (performance seems crappy with 3d, no drag between, with/without compiz) or one big xinerama (no compiz, crappy performance).  For the life of me I can't seem to figure out how to composite across all 4 monitors, and it seems like it's really not an option as drivers only reference xinerama.  Anyone done this with full compositing/effects?  I tried turning on overlays on xinerama-enabled display and seemed like it wanted to work, but began tiling the display so bad it was unusable.  I'm really not going to be happy as I just replaced a pair of nvidia cards that worked mostly great short of compiz/compositing, as generally speaking nothing behaves right so far with the gargantuan 5870.  Especially when they're now toting the fact that supposed the linux drivers support eyefinity.  Xinerama doesn't qualify in my opinion as this loses compositing ability.  Argh...

---

### Post by 0004tom on 2011-02-04
I've just upgraded my fglrx driver to 11.01 with my HD6850 and I still get the unsupoprted hardware watermark. But it runs fine, compiz 3d games and such.

What I find funny is if you go the the ati/amd site to download the drivers in the drop down menu for the linux driver you see HD6xxx series. But yet I still got the watermark.

The watermark can be removed, but thats not the point.

---

### Post by hamiltenor on 2011-02-05
Like everyone else, I'm still waiting for driver support for my XFX Radeon HD 6850. I really just want full resolution, too much to ask for?

---

### Post by Heuamöbe on 2011-02-05
@hamiltenor:
This Thread :[http://ubuntuforums.org/showthread.php?t=1614444&page=10](http://ubuntuforums.org/showthread.php?t=1614444&page=10)
and this wiki:[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually)
helped me.

@0004tom: If you know a way to get rid of the watermark please tell me ;)

---

### Post by 0004tom on 2011-02-05
> **hamiltenor said:**
> Like everyone else, I'm still waiting for driver support for my XFX Radeon HD 6850. I really just want full resolution, too much to ask for?

Even tho the 6xxx series are not support they use the 5xxx series drivers, both on linux and on windows, So I don't see why your unable to get a correct resolution, I have a 3 screen eyefinity setup on my HD6850.

> **Heuamöbe said:**
> @0004tom: If you know a way to get rid of the watermark please tell me ;)

```
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```

The code comes from the archlinux wiki for catalyst.

[https://wiki.archlinux.org/index.php/ATI_Catalyst#Radeon_HD_6870_and_fglrx_10.10](https://wiki.archlinux.org/index.php/ATI_Catalyst#Radeon_HD_6870_and_fglrx_10.10)

---

### Post by soma_thug on 2011-02-05
hi all

---

### Post by Heuamöbe on 2011-02-05
> **0004tom said:**
> 
```
#!/bin/sh
DRIVER=/usr/lib/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done
```The code comes from the archlinux wiki for catalyst.

[https://wiki.archlinux.org/index.php/ATI_Catalyst#Radeon_HD_6870_and_fglrx_10.10](https://wiki.archlinux.org/index.php/ATI_Catalyst#Radeon_HD_6870_and_fglrx_10.10)


Actually, I tried this one and it did not work with Catalyst 11.1...

---

### Post by 0004tom on 2011-02-05
I guess it must me Arch specific then, I used the code not 2 hours ago, and the water marks we're gone, after killing xorg.

---

### Post by help_me123 on 2011-02-05
I tried using the script to remove the watermark but it did not work too.

Can someone who managed to remove their watermark post his /usr/lib/xorg/modules/drivers/fglrx_drv.so? I want to try to replace my file with a successfully hacked one.

---

### Post by lobo_cobra on 2011-02-06
I propose you go with Catalyst 10.10 and remove there the watermark. I have an ASUS EAH6850 and by applying the installation howto marked in the links that you see in this thread, I was able to make it run with 3 Monitor...

-> 2x1280 1x1920 Monitors

Compiz works very good and The watermark can be removed with the script mentioned above. As 11.1. does not represent any advantage on 10.1 on Ubuntu, go for 10.1 version of catalyst until ATI fully supports the 6850 chip.My 3 monitors are fully working with the right resolution and the watermark is gone. Just follow the links in this tread.


BTW... I connected the 3 Monitors by DVI and displayport with an active adapter. It does not work if you connect with HDMI port. And it took me a while to learn that old monitors can not be connected (even with active displayport adapter) to the 6850 display port on the graphic card . Therefore you need to connect the newest monitor to the display port and the old ones to the DVI ports, and all works perfect as it should.

---

### Post by 0004tom on 2011-02-06
> **lobo_cobra said:**
> As 11.1. does not represent any advantage on 10.1 on Ubuntu, go for 10.1 version of catalyst until ATI fully supports the 6850 chip.

How about about 20 changes to the driver? and the tear free desktop option now found in the 11.01 driver?

---

### Post by 0004tom on 2011-02-06
> **lobo_cobra said:**
> As 11.1. does not represent any advantage on 10.1 on Ubuntu, go for 10.1 version of catalyst until ATI fully supports the 6850 chip.My 3 monitors are fully working with the right resolution and the watermark is gone. Just follow the links in this tread.

How about about 20 changes to the driver? and the tear free desktop option now found in the 11.01 driver?

How can you 3 monitors running on the 10.1 catatyst driver, when support for this wasn't introduced till the 10.7 driver?

---

### Post by x86Daddy on 2011-02-07
> **Heuamöbe said:**
> Actually, I tried this one and it did not work with Catalyst 11.1...
I did a quick search in /usr for all instances of fglrx_drv.so... **There is another**.

Alter the script ever so slightly:
```
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
```My Watermark is gone.  I'm running 10.10 on the new Acer Aspire One 522.  All is good.

---

### Post by kubug on 2011-02-10
> **x86Daddy said:**
> I did a quick search in /usr for all instances of fglrx_drv.so... **There is another**.

x86Daddy's suggestion worked like a charm.

In a terminal type this:

```
nano fixwatermark.sh
```

Paste the following into it: 

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 

```

```
chmod +x fixwatermark.sh
```

```
sudo sh fixwatermark.sh
```

Log out and back in. Ta da!

---

### Post by osro on 2011-02-11
Hello,

I'm running into quite some problems installing that Catalyst Center. I have a Gigabyte HD6850 graphics card. It won't install. I have had some "black screens", tried almost everything that i found in different threads.

I'm a complete noob. Just started since last week with Ubuntu. First time Linux. Don't understand the terminal syntax, so i'm just typing what i find on forums. Lots of the threads concern previous versions of Ubuntu. So... 

I've read this thread. But now I don't seem to manage to install the Catalyst Control Center 10-10 or 10-1. Ubuntu 10.10 only shows the latest drivers in the package manager. I've tried to get that local package (created with the run file for Catalyst 10-10) into the package manager, but I don't find it. Only the files for the latest drivers.

Can someone give this noob** a complete walk through** for installing my HD6850 on Ubuntu 10.10 64 bit? Even where I can get the proper file to install. Now I've been getting it here: [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

I'm about to give up on Ubuntu. In fact yesterday i did... but was forced to reinstall cause that miserable Grub thingy kept booting, making it impossible to access Windows. If this works out I'm planning to convert to Linux. But so far my patience has been tested, very much so.

---

### Post by kubug on 2011-02-11
> **osro said:**
> Hello,

I'm running into quite some problems installing that Catalyst Center. I have a Gigabyte HD6850 graphics card. It won't install. I have had some "black screens", tried almost everything that i found in different threads.

I'm a complete noob. Just started since last week with Ubuntu. First time Linux. Don't understand the terminal syntax, so i'm just typing what i find on forums. Lots of the threads concern previous versions of Ubuntu. So... 

I've read this thread. But now I don't seem to manage to install the Catalyst Control Center 10-10 or 10-1. Ubuntu 10.10 only shows the latest drivers in the package manager. I've tried to get that local package (created with the run file for Catalyst 10-10) into the package manager, but I don't find it. Only the files for the latest drivers.

Can someone give this noob** a complete walk through** for installing my HD6850 on Ubuntu 10.10 64 bit? Even where I can get the proper file to install. Now I've been getting it here: [http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

I'm about to give up on Ubuntu. In fact yesterday i did... but was forced to reinstall cause that miserable Grub thingy kept booting, making it impossible to access Windows. If this works out I'm planning to convert to Linux. But so far my patience has been tested, very much so.

First of all, congrats for coming here and posting your issue. Most people would just turf the whole thing and go back to Windows. Linux is different for sure, and there is a learning curve.

Anyways, here is what I would suggest you do. First, uninstall any driver from ATI you installed. ATI (AMD) has a pretty sad installer that does not detect whether you already got the driver installed or not. So you need to purge the system first:

So go here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually")

And go down to the "Removing Catalyst/fglrx" section and follow the information. Some/most of the commands will either return an error or say that nothing was installed. Just move to the next one. 

Once finished, you can be pretty confident that it's all gone. 

Next, since it's all with a GUI from here (noob friendly) I would suggest installing Ubuntu-Tweak. Go here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Just click on the download and install with the software center.

Once installed, start it under Applications->System->Ubuntu Tweak. (I am going by memory here, since I don't have my Ubuntu machine in front of me). 

On the left menu select "Source Center". It will ask you to update, just say yes. The click on the "Unlock" button in the bottom right hand corner. Now you will need your user password.

After entering in the password, scroll the right window to the bottom and you should see the 'X-Updates' source. Click on the box in front. 

What you have done now is you have added the Repository for the latest drivers for Intel, ATI and nVidia. There is a command line way to have done this, but since I find Ubuntu Tweak handy for newcomers, I wanted you to try it this way.

Now on top panel click on 'System->Administration->Update Manager'.

In the new window, click 'Check'. Let it update. Then close the window, even though you may have updates to run. You can run them later.

Now click on 'System->Administration->Additional Drivers' and it should find the ATI driver for your card from the new repository we just installed.

Let it install the driver and then reboot. You will now have the watermark in the bottom right. Just follow the instructions above to remove that.

Just for your information, nVidia is still a better choice of Video card for linux currently. ATI is getting better, but I found it still easier with nVidia. Just my 2 cents.

---

### Post by quadproc on 2011-02-11
> **BrokeMahPC said:**
> 

I guess this means my HD6850 is now supported in Linux - anyone tried the driver yet?

About a month ago I tried the ATI 11.1 driver with this system which runs a pair of HD4870 cards - no problems with the graphics subsystem.

I uninstalled the fglrx driver because I discovered a bug in the default open source driver and I want to test out any fixes that may come along for that driver, so I am not presently running fglrx.

quadproc

---

### Post by osro on 2011-02-12
Thx Kubug. I reïnstalled Ubuntu this morning and did what you proposed. Everything worked well, meaning everything still works. But The Additional Drivers don't find any drivers. 

I've uninstalled Catalyst/fglrx with the wiki. Everything seemed to work, maybe one thing: 
$ sudo dpkg-reconfigure xserver-xorg
[FONT=Verdana]
this didn't do anything, just gave me a new line in the terminal. Maybe it is supposed to?

Then I did everything as you proposed. Installed the Ubuntu Tweak and checked the box with X-updates. Did the updates in the updatemanager (he found them).
But then Additional Drivers suggests no drivers to install.

Any ideas? I proly missed s'thing.

[/FONT]

---

### Post by quadproc on 2011-02-12
> **osro said:**
> But The Additional Drivers don't find any drivers. 

There are several ways to find out what driver is actually in use even though Additional Drivers doesn't know:

1. Run the _hardinfo_ program from a terminal - this program is available through Synaptic if it isn't already installed on your system. Select Display, scroll down to OpenGL, and look at the Renderer entry.

2. If you have an xorg.conf file located in /etc/X11 then look in that file for a line which contains Driver.

3. If the driver has been successfully installed then running _fglrxinfo_ will produce meaningful results.

There are some other methods also but the above should be sufficient.

In the past, I have found that the Additional Drivers utility does not correctly report the driver in use so I no longer try to use that utility.  Also, that utility did not give me a choice of which driver to use; sometimes I will need the latest driver and sometimes I will need an earlier version, and I need to be able to specify which one gets installed.  So I do not use the Additional Drivers utility.

quadproc

---

### Post by osro on 2011-02-13
> **quadproc said:**
> 

In the past, I have found that the Additional Drivers utility does not correctly report the driver in use so I no longer try to use that utility.  Also, that utility did not give me a choice of which driver to use; sometimes I will need the latest driver and sometimes I will need an earlier version, and I need to be able to specify which one gets installed.  So I do not use the Additional Drivers utility.

quadproc

What do you use. The hardinfo utility told me what I already know. That nothing is installed. This is some info from the report that may be usefull (or not).

Computer
Processor    8x Intel(R) Core(TM) i7 CPU 950 @ 3.07GHz
Memory    12328MB (612MB used)
Operating System    Ubuntu 10.10
User Name    root (root)
Date/Time    Sun 13 Feb 2011 12:27:58 PM CET
Display
Resolution    1600x1200 pixels
OpenGL Renderer    Unknown
X11 Vendor    The X.Org Foundation

OpenGL
Vendor    Unknown
Renderer    Unknown
Version    Unknown
Direct Rendering    No


My screen should normally be 1920x1200 @ 60Hz. Is it possible to get some detailed instructions to install my driver? In "noob-speak".

Thx for your patience.

---

### Post by osro on 2011-02-13
kubug an quadproc. Thanx for the aid. I figured out what i did wrong. apparently I need fglrx-modialises installed. I had uninstalled it together with the drivers and such. I'll try to remove that watermark now. Thx again!

---

### Post by whizz on 2011-02-13
I've got an HD6870, just followed the Wiki-page, and it seems to work (eventually ;) ), however, in the Information-tab it says
Catalyst™ Version: 10.10

Shouldn't that be 11.1? Or are they referring the Ubuntu version? Or is the linux-driver just that old? :confused:

It does say Driver Packaging Version: 8.783-101005a-106925C-ATI,

which seems the newest though... I guess it's allright, but can someone please confirm that? :)

---

### Post by 0004tom on 2011-02-13
> **whizz said:**
> I've got an HD6870, just followed the Wiki-page, and it seems to work (eventually ;) ), however, in the Information-tab it says
Catalyst™ Version: 10.10

Shouldn't that be 11.1? Or are they referring the Ubuntu version? Or is the linux-driver just that old? :confused:

It does say Driver Packaging Version: 8.783-101005a-106925C-ATI,

which seems the newest though... I guess it's allright, but can someone please confirm that? :)

[https://wiki.archlinux.org/index.php/ATI_Catalyst#Amdcccle_is_showing_different_catalyst.27s_version](https://wiki.archlinux.org/index.php/ATI_Catalyst#Amdcccle_is_showing_different_catalyst.27s_version)

> It's because information about version is stored in /etc/ati/amdpcsdb file. This file is created while first run of X/DE by freshly installed catalyst, and later it's not updated. Solution: kill your X/DE, then remove /etc/ati/amdpcsdb, restart your X/DE, and then set up amdcccle.

Your driver version it the same as mine however.

---

### Post by quadproc on 2011-02-13
> **osro said:**
> What do you use. 

My screen should normally be 1920x1200 @ 60Hz. Is it possible to get some detailed instructions to install my driver? In "noob-speak".

osro's question relates to how I install ATI drivers.  He seems to have gotten his setup running now so he probably doesn't need this answer any more, but someone may find it useful.

I make a directory for the purpose of keeping and installing the driver.  I go to the ATI site and put in the particulars for my hardware, then I choose which of the available drivers I want.  I download that driver package; the download is now about 120 MB!  Once downloaded, I move the file into the directory and cd to it.

Then I do a
```
sudo sh <a_long_string_id>.run --keep --install
```The file will unpack itself and then will fire up an ATI installation window.  I follow the instructions there and I answer the questions for the simple and automatic install.  The window will seem to freeze when it is mostly finished; don't worry, it just takes a while.

At this time you need to do a reboot.  If the graphics are not working correctly then you may need to do an
```
aticonfig --initial -f
```This will cause a minimal new xorg.conf file to be created so you probably should first copy the old one to some safe place, in case you need it later.

The --keep option tells the installer to leave behind all of the files that it used during the install.  You can examine these if you like.  You do not need to keep them around; the driver will work fine without them.  If you have no interest in those files then you could omit the --keep option from the .run line.

Another thing that you can do is to use the --listpkg option on the .run file:
```
sh <a_long_string_id>.run --listpkg
```This will check the file for integrity and then will report on which OS versions are compatible with the driver.

quadproc

---

### Post by kubug on 2011-02-15
@osro: I am sorry. I was away over the weekend to a salesmeeting. Super busy. But I am glad you got it working after all. 

For future installs/upgrades I would suggest letting the install create *.deb files you then install. This is because when it comes time to upgrade to the next version of ubuntu, you may have issues with the video drivers. However, if you installed it via .deb the upgrade will simply uninstall and reinstall the latest drivers automatically for you. 

Enjoy your Linux install.

P.S.: Just to throw you a curve ball, the 11.2 driver was released recently.

---

### Post by janthonywj on 2011-02-16
I'm seeking help with Catalyst 11.2. I just finished my new build and have three monitors going with a ATI 5770 powering it. Works fine having it set up with a desktop three monitors wide, but it doesn't seem to be "Eyefinity". It is implemented differently in that maximizing a window only maximizes to that particular display. Fine for productivity, but not for gaming or watching movies with the three monitors in portrait or something of that nature... 

I also wanted to see if I could manually maximize a window to the full three monitors, it will do to, and it will span all three to some extent, but there seems to be a breaking limit where X crashes and restarts the desktop. 

I have seen that Windoze users have to group their monitors, and I don't have that option in Catalyst CC. Is this a change from 11.1 to 11.2? I'm new to the high end video cards and such, so how to I get Eyefinity to work?

---

### Post by Veld on 2011-02-17
For some reason, the Catalyst Control Center (Administrative) doesn't open.

---

### Post by kubug on 2011-02-17
> **Veld said:**
> For some reason, the Catalyst Control Center (Administrative) doesn't open.

Check to see if the driver installed correctly:

```
fglrxinfo
```

If you feel you installed it correctly, try starting it from the command line:

```
sudo amdcccle 
```

Chances are it will spit out a segfault of sorts. Post back here with results.

---

### Post by kubug on 2011-02-17
> **janthonywj said:**
> I'm seeking help with Catalyst 11.2. I just finished my new build and have three monitors going with a ATI 5770 powering it. Works fine having it set up with a desktop three monitors wide, but it doesn't seem to be "Eyefinity". It is implemented differently in that maximizing a window only maximizes to that particular display. Fine for productivity, but not for gaming or watching movies with the three monitors in portrait or something of that nature... 

I also wanted to see if I could manually maximize a window to the full three monitors, it will do to, and it will span all three to some extent, but there seems to be a breaking limit where X crashes and restarts the desktop. 

I have seen that Windoze users have to group their monitors, and I don't have that option in Catalyst CC. Is this a change from 11.1 to 11.2? I'm new to the high end video cards and such, so how to I get Eyefinity to work?

I am sure you already started your own thread on this question (since it's not related to the original question of this thread) and you are just looking for more information. *hint hint*

From what I can tell from my work colleagues setup (he has a 6850 on three monitors) Eyefinity in linux is dodgy at best. It works ok in Windows (but I am not convinced as to it's usefulness). 

Also, you may have to turn 'Desktop Effects' off, since compiz can't handle windows bigger than 4096 px (as far as I can remember). 

I can try to see what we can get going on our setup here. No promises, since it is a work setup and we don't play games or watch videos here (well, not ALL the time anyways).

---

### Post by janthonywj on 2011-02-17
> **kubug said:**
> I am sure you already started your own thread on this question (since it's not related to the original question of this thread) and you are just looking for more information. *hint hint*

I haven't started a new thread yet, but I should. I posted in another thread about 11.1 drivers, but I'm currently using 11.2, so yeah, I should start a new one soon. I like to do my part and keep that to a minimum.

> **kubug said:**
> Also, you may have to turn 'Desktop Effects' off, since compiz can't handle windows bigger than 4096 px (as far as I can remember).

That's good to know. I'll bet that is the reason for the crash after making a window too big. I'm going to experiment with that some, maybe I can make a script that turns off Compiz or desktop effects before starting a game or app that I want to span monitors, and turn it on after close.

I have more questions, but I'll let this thread die. Thank you for your reply Kubug.

---

### Post by tealson on 2011-02-19
Can anyone running with the driver tell me if the fan speed control is working? 
I would like to buy the "MSI R6850 Cyclone 1GD5 Power Edition/OC" and would love to control the speed of the fan because my system is absolutely quite.

---

### Post by Veld on 2011-02-20
> **kubug said:**
> Check to see if the driver installed correctly:

```
fglrxinfo
```

If you feel you installed it correctly, try starting it from the command line:

```
sudo amdcccle 
```

Chances are it will spit out a segfault of sorts. Post back here with results.

No problem starting it from the command line. I wonder why it doesn't pop up from the menu. ~_~

---

### Post by macclepg on 2011-03-13
[http://askubuntu.com/questions/30067/eye-infinity-across-3-displays-with-a-radeon-6800]("http://askubuntu.com/questions/30067/eye-infinity-across-3-displays-with-a-radeon-6800")

---

### Post by racrbilly67 on 2011-03-14
> **kubug said:**
> First of all, congrats for coming here and posting your issue. Most people would just turf the whole thing and go back to Windows. Linux is different for sure, and there is a learning curve.

Anyways, here is what I would suggest you do. First, uninstall any driver from ATI you installed. ATI (AMD) has a pretty sad installer that does not detect whether you already got the driver installed or not. So you need to purge the system first:

So go here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually")

And go down to the "Removing Catalyst/fglrx" section and follow the information. Some/most of the commands will either return an error or say that nothing was installed. Just move to the next one. 

Once finished, you can be pretty confident that it's all gone. 

Next, since it's all with a GUI from here (noob friendly) I would suggest installing Ubuntu-Tweak. Go here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Just click on the download and install with the software center.

Once installed, start it under Applications->System->Ubuntu Tweak. (I am going by memory here, since I don't have my Ubuntu machine in front of me). 

On the left menu select "Source Center". It will ask you to update, just say yes. The click on the "Unlock" button in the bottom right hand corner. Now you will need your user password.

After entering in the password, scroll the right window to the bottom and you should see the 'X-Updates' source. Click on the box in front. 

What you have done now is you have added the Repository for the latest drivers for Intel, ATI and nVidia. There is a command line way to have done this, but since I find Ubuntu Tweak handy for newcomers, I wanted you to try it this way.

Now on top panel click on 'System->Administration->Update Manager'.

In the new window, click 'Check'. Let it update. Then close the window, even though you may have updates to run. You can run them later.

Now click on 'System->Administration->Additional Drivers' and it should find the ATI driver for your card from the new repository we just installed.

Let it install the driver and then reboot. You will now have the watermark in the bottom right. Just follow the instructions above to remove that.

Just for your information, nVidia is still a better choice of Video card for linux currently. ATI is getting better, but I found it still easier with nVidia. Just my 2 cents.

Just wanted to say that this method worked like a charm with my 6950. Thanks, kubug!

---

### Post by kshep92 on 2011-09-03
That solution to remove the watermark worked like a charm. You, sir are a life saver. thank you SO MUCH!

---

### Post by bcschmerker on 2011-09-11
> **kubug said:**
> ...Anyways, here is what I would suggest you do. First, uninstall any driver from ATI you installed. ATI (AMD) has a pretty sad installer that does not detect whether you already got the driver installed or not. So you need to purge the system first:

So go here:

[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Installing_the_drivers_manually")

And go down to the "Removing Catalyst/fglrx" section and follow the information. Some/most of the commands will either return an error or say that nothing was installed. Just move to the next one. 

Once finished, you can be pretty confident that it's all gone. 

Next, since it's all with a GUI from here (noob friendly) I would suggest installing Ubuntu-Tweak. Go here:

[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Just click on the download and install with the software center.

Once installed, start it under Applications->System->Ubuntu Tweak. (I am going by memory here, since I don't have my Ubuntu machine in front of me). 

On the left menu select "Source Center". It will ask you to update, just say yes. The click on the "Unlock" button in the bottom right hand corner. Now you will need your user password.

After entering in the password, scroll the right window to the bottom and you should see the 'X-Updates' source. Click on the box in front. 

What you have done now is you have added the Repository for the latest drivers for Intel, ATI and nVidia. There is a command line way to have done this, but since I find Ubuntu Tweak handy for newcomers, I wanted you to try it this way.

Now on top panel click on 'System->Administration->Update Manager'.

In the new window, click 'Check'. Let it update. Then close the window, even though you may have updates to run. You can run them later.

Now click on 'System->Administration->Additional Drivers' and it should find the ATI driver for your card from the new repository we just installed.

Let it install the driver and then reboot. You will now have the watermark in the bottom right. Just follow the instructions above to remove that....Thanks for a HOWTO on installing a 6000-Series video display adapter on an Ubuntu® box.  I have an [Asus® EAH6850DC/2DIS/1GD5 PCI-Express x16 VDA](http://www.asus.com/) (Barts Pro GPU), along with an [Antec® TPQ-850 power supply unit](http://www.antec.com/), to divert to my hybrid Everex® with its all-AMD®-equipped Gigabyte® mobo (plus a Creative Laboratories® SB0350 to replace the mobo's bad planar Realtek® ALC-883 audio chip); so far I have been using the X.org Radeon HD driver (package: xserver-xorg-radeonhd) for the planar HD 3200 (which uses an R600-series GPU rather than the Barts Pro in the EAH6850DC), so I've a little less work than the original asker this Thread.

The aforementioned Everex® running 10.04.3-LTS as of 11 September 2011, I anticipated having to upgrade to the 2.6.38-generic Kernel, per Advance Micro Devices'® recommendations for Catalyst Control Center, LinUX Edition (packages: fglrx-amdccccle, fglrx-modaliases).  I being used to adding APT Repositories from GNOME Terminal, would:
```
gksudo -S add-apt-repository ppa:ubuntu-x-swat/x-updates
```
set this PPA in Synaptic, as I estimate the case to be from previous PPA adds?  (For unknown reasons, sudo is out of sync with gksudo in terms of account data my system, as of 11 September 2011.)

**Update:**  Looks it; will see how Kernel 2.6.38-generic runs directly prior to proceeding with the install.

**Update 2:**  Reverted to stock video, as the BIOS on the MA78GM-S2HP cannot properly control the Barts Pro GPU on the EAH6850DC during power-on self test.  Currently considering whether to go to a Gigabyte® PCI-Express x16 VDA using an R700-series GPU.

---

### Post by fcomstoc on 2011-10-25
Hey there,
I just finished building my dream desktop and the video card that i bought is the MSI ATI HD 6950, I just finished installing ubuntu 11.10 on it and I can't seem to get the 3 monitors to work on it. I have 3 1280x1024 monitors and I have tried reinstalling the drivers the OS and pretty much everything several times and the ATI config program will not set it up. The only config that works is all 3 with the same image. Does anyone know how to get this to work with 3 monitors Thanks

---

### Post by Zmorf on 2011-10-29
I got the same problem, using ASUS Radeon hd 6950 with a quad 1920*1080 screen setup. 

Only manage to get mirror screen working, catalyst only crashes when im pressing "Ok"

---

### Post by bcschmerker on 2011-12-08
> **fcomstoc said:**
> Hey there,
I just finished building my dream desktop and the video card that i bought is the MSI ATI HD 6950, I just finished installing ubuntu 11.10 on it and I can't seem to get the 3 monitors to work on it. I have 3 1280x1024 monitors and I have tried reinstalling the drivers the OS and pretty much everything several times and the ATI config program will not set it up. The only config that works is all 3 with the same image. Does anyone know how to get this to work with 3 monitors Thanks[Advance Micro Devices®](http://www.amd.com/) has yet to catch up with the [LinUX Kernel Project](http://www.kernel.org/) on drivers for Kernels 3.0-up; the Catalyst&#8482; driver and settings application (packages: fglrx, fglrx-amdcccle) run properly with Kernel 2.6.38 at latest.  I updated my 10.04.4-LTS installation to Kernel 3.0.0.14 (package: linux-image-generic-pae-lts-backport-oneiric) on 5 December 2011 and had to switch back to a Hewlett-Packard® HP 2009m from a Polaroid® flatscreen TV unit I was testing with Catalyst&#8482; (as the aforementioned Polaroid has only a 1700x990px LCD run on 1080i/25 and/or 1080i/30 signal, which the X.org drivers (packages: xserver-xorg-video-ati, xserver-xorg-video-radeon, xserver-xorg-video-radeonhd) cannot handle properly as of 7 December 2011 due to the out-of-image issue common to TVs in computer applications).

---

### Post by don_page on 2012-01-02
> **kubug said:**
> x86Daddy's suggestion worked like a charm.

In a terminal type this:

```
nano fixwatermark.sh
```

Paste the following into it: 

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 

```

```
chmod +x fixwatermark.sh
```

```
sudo sh fixwatermark.sh
```

Log out and back in. Ta da!

thanks..  
this step is work on my HD 6470M Asus K43BY AMD E350 ...
finally the watermark is gone...

---

### Post by alphaamanitin on 2012-02-13
Okay, same issues Asus EAH6850 here.  Problem, cannot even get an install going with ubuntu.  Try booting kernal in nomodeset and if drops to live terminal.  Fedora x64 will install, but boots to terminal and the fedora forums are not that helpful honestly.  

And why is it that once upon a time, Ubuntu 11.04 AMD64 iso, unpacked via WinRAR onto a USB drive would boot into Unity, but now nothing boots into ANY desktop manager correctly??  So, how do I get Ubuntu installed to even begin installing the drivers?

Have kubuntu 11.10 startx error log if that will help.

AlphaA

---

### Post by kubug on 2012-02-14
> **alphaamanitin said:**
> Okay, same issues Asus EAH6850 here.  Problem, cannot even get an install going with ubuntu.  Try booting kernal in nomodeset and if drops to live terminal.  Fedora x64 will install, but boots to terminal and the fedora forums are not that helpful honestly.  

And why is it that once upon a time, Ubuntu 11.04 AMD64 iso, unpacked via WinRAR onto a USB drive would boot into Unity, but now nothing boots into ANY desktop manager correctly??  So, how do I get Ubuntu installed to even begin installing the drivers?

Have kubuntu 11.10 startx error log if that will help.

AlphaA

Hi there,

I just finished installing Ubuntu 11.10, on a 6850, and had no issues whatsoever. 

The RadeonHD drivers got me to Unity, and from there I installed the latest AMD drivers from their website.

Just give these instructions a go: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

These are the ones I used to get this working with my dual displays.

---

### Post by alphaamanitin on 2012-02-14
> **kubug said:**
> Hi there,

I just finished installing Ubuntu 11.10, on a 6850, and had no issues whatsoever. 

The RadeonHD drivers got me to Unity, and from there I installed the latest AMD drivers from their website.

Just give these instructions a go: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

These are the ones I used to get this working with my dual displays.

Again, though that is all for systems that are installed and working, but have graphical errors.  I cannot get the system to install.  I need to find a installation disk with the drivers on it that will install.  Perhaps a Kubuntu x64 DVD will have them.  I will search.

AlphaA

---

### Post by kubug on 2012-02-14
> **alphaamanitin said:**
> Again, though that is all for systems that are installed and working, but have graphical errors.  I cannot get the system to install.  I need to find a installation disk with the drivers on it that will install.  Perhaps a Kubuntu x64 DVD will have them.  I will search.

AlphaA

Are you using 11.10 (Ubuntu)?? I wonder if the product ID of your card is not recognized, and that's why it doesn't load the RadeonHD driver for you on start up (this is merely a guess).

Are you sure it's the video driver that is causing the drop to terminal? What does 'dmesg' tell at that point?

---

### Post by alphaamanitin on 2012-02-14
> **kubug said:**
> Are you using 11.10 (Ubuntu)?? I wonder if the product ID of your card is not recognized, and that's why it doesn't load the RadeonHD driver for you on start up (this is merely a guess).

Are you sure it's the video driver that is causing the drop to terminal? What does 'dmesg' tell at that point?

The weird thing is, 10.04 LTS on USB and 11.04 used to boot into live mode.  Sometimes it would boot into the desktop fine (about 20% of boot attempts), other times it would have the graphical errors.  

Not sure what dmesg says, will have to test, but when I do startx what I get for an error is that KES is not enabled.  ```
[   128.220] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[   128.222] X Protocol Version 11, Revision 0
[   128.222] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   128.223] Current Operating System: Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[   128.223] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/efi/boot/bootx64.efi boot=casper nomodeset
[   128.224] Build Date: 29 September 2011  02:45:13AM
[   128.224] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[   128.225] Current version of pixman: 0.22.2
[   128.226]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   128.227] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   128.229] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 13 21:55:09 2012
[   128.230] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   128.231] (==) No Layout section.  Using the first Screen section.
[   128.231] (==) No screen section available. Using defaults.
[   128.231] (**) |-->Screen "Default Screen Section" (0)
[   128.231] (**) |   |-->Monitor "<default monitor>"
[   128.231] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   128.231] (==) Automatically adding devices
[   128.231] (==) Automatically enabling devices
[   128.231] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   128.231]     Entry deleted from font path.
[   128.231] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   128.231]     Entry deleted from font path.
[   128.231] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   128.231]     Entry deleted from font path.
[   128.231] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   128.231]     Entry deleted from font path.
[   128.231] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   128.231]     Entry deleted from font path.
[   128.231] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   128.231] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   128.231] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   128.231] (II) Loader magic: 0x7e0220
[   128.231] (II) Module ABI versions:
[   128.231]     X.Org ANSI C Emulation: 0.4
[   128.231]     X.Org Video Driver: 10.0
[   128.231]     X.Org XInput driver : 12.3
[   128.231]     X.Org Server Extension : 5.0
[   128.232] (--) PCI:*(0:1:0:0) 1002:6739:1043:03b4 rev 0, Mem @ 0xd0000000/268435456, 0xfea20000/131072, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   128.232] (II) Open ACPI successful (/var/run/acpid.socket)
[   128.232] (II) LoadModule: "extmod"
[   128.232] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   128.232] (II) Module extmod: vendor="X.Org Foundation"
[   128.232]     compiled for 1.10.4, module version = 1.0.0
[   128.232]     Module class: X.Org Server Extension
[   128.232]     ABI class: X.Org Server Extension, version 5.0
[   128.232] (II) Loading extension MIT-SCREEN-SAVER
[   128.232] (II) Loading extension XFree86-VidModeExtension
[   128.232] (II) Loading extension XFree86-DGA
[   128.232] (II) Loading extension DPMS
[   128.232] (II) Loading extension XVideo
[   128.232] (II) Loading extension XVideo-MotionCompensation
[   128.232] (II) Loading extension X-Resource
[   128.232] (II) LoadModule: "dbe"
[   128.232] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   128.232] (II) Module dbe: vendor="X.Org Foundation"
[   128.232]     compiled for 1.10.4, module version = 1.0.0
[   128.232]     Module class: X.Org Server Extension
[   128.232]     ABI class: X.Org Server Extension, version 5.0
[   128.232] (II) Loading extension DOUBLE-BUFFER
[   128.232] (II) LoadModule: "glx"
[   128.233] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   128.233] (II) Module glx: vendor="X.Org Foundation"
[   128.233]     compiled for 1.10.4, module version = 1.0.0
[   128.233]     ABI class: X.Org Server Extension, version 5.0
[   128.233] (==) AIGLX enabled
[   128.233] (II) Loading extension GLX
[   128.233] (II) LoadModule: "record"
[   128.233] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   128.233] (II) Module record: vendor="X.Org Foundation"
[   128.233]     compiled for 1.10.4, module version = 1.13.0
[   128.233]     Module class: X.Org Server Extension
[   128.233]     ABI class: X.Org Server Extension, version 5.0
[   128.233] (II) Loading extension RECORD
[   128.233] (II) LoadModule: "dri"
[   128.233] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   128.233] (II) Module dri: vendor="X.Org Foundation"
[   128.233]     compiled for 1.10.4, module version = 1.0.0
[   128.233]     ABI class: X.Org Server Extension, version 5.0
[   128.233] (II) Loading extension XFree86-DRI
[   128.233] (II) LoadModule: "dri2"
[   128.233] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   128.233] (II) Module dri2: vendor="X.Org Foundation"
[   128.233]     compiled for 1.10.4, module version = 1.2.0
[   128.233]     ABI class: X.Org Server Extension, version 5.0
[   128.233] (II) Loading extension DRI2
[   128.233] (==) Matched fglrx as autoconfigured driver 0
[   128.233] (==) Matched ati as autoconfigured driver 1
[   128.233] (==) Matched vesa as autoconfigured driver 2
[   128.233] (==) Matched fbdev as autoconfigured driver 3
[   128.233] (==) Assigned the driver to the xf86ConfigLayout
[   128.233] (II) LoadModule: "fglrx"
[   128.233] (WW) Warning, couldn't open module fglrx
[   128.233] (II) UnloadModule: "fglrx"
[   128.233] (II) Unloading fglrx
[   128.233] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   128.234] (II) LoadModule: "ati"
[   128.234] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   128.234] (II) Module ati: vendor="X.Org Foundation"
[   128.234]     compiled for 1.10.2.902, module version = 6.14.99
[   128.234]     Module class: X.Org Video Driver
[   128.234]     ABI class: X.Org Video Driver, version 10.0
[   128.234] (II) LoadModule: "radeon"
[   128.234] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   128.234] (II) Module radeon: vendor="X.Org Foundation"
[   128.234]     compiled for 1.10.2.902, module version = 6.14.99
[   128.235]     Module class: X.Org Video Driver
[   128.235]     ABI class: X.Org Video Driver, version 10.0
[   128.235] (II) LoadModule: "vesa"
[   128.235] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   128.235] (II) Module vesa: vendor="X.Org Foundation"
[   128.235]     compiled for 1.10.2, module version = 2.3.0
[   128.235]     Module class: X.Org Video Driver
[   128.235]     ABI class: X.Org Video Driver, version 10.0
[   128.235] (II) LoadModule: "fbdev"
[   128.235] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   128.235] (II) Module fbdev: vendor="X.Org Foundation"
[   128.235]     compiled for 1.10.0, module version = 0.4.2
[   128.235]     ABI class: X.Org Video Driver, version 10.0
[   128.235] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
    ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
    ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS
[   128.235] (II) VESA: driver for VESA chipsets: vesa
[   128.235] (II) FBDEV: driver for framebuffer: fbdev
[   128.235] (--) using VT number 8

[   128.238] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   128.238] (II) [KMS] drm report modesetting isn't supported.
[   128.238] (WW) Falling back to old probe method for vesa
[   128.238] (WW) Falling back to old probe method for fbdev
[   128.238] (II) Loading sub module "fbdevhw"
[   128.238] (II) LoadModule: "fbdevhw"
[   128.238] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   128.238] (II) Module fbdevhw: vendor="X.Org Foundation"
[   128.238]     compiled for 1.10.4, module version = 0.0.2
[   128.238]     ABI class: X.Org Video Driver, version 10.0
[   128.238] (II) RADEON(0): TOTO SAYS 00000000fea20000
[   128.238] (II) RADEON(0): MMIO registers at 0x00000000fea20000: size 128KB
[   128.238] (II) RADEON(0): PCI bus 1 card 0 func 0
[   128.238] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   128.238] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   128.238] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   128.238] (==) RADEON(0): Default visual is TrueColor
[   128.238] (II) Loading sub module "vgahw"
[   128.238] (II) LoadModule: "vgahw"
[   128.238] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   128.238] (II) Module vgahw: vendor="X.Org Foundation"
[   128.238]     compiled for 1.10.4, module version = 0.1.0
[   128.238]     ABI class: X.Org Video Driver, version 10.0
[   128.238] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[   128.238] (==) RADEON(0): RGB weight 888
[   128.239] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   128.239] (--) RADEON(0): Chipset: "AMD Radeon HD 6800 Series" (ChipID = 0x6739)
[   128.239] (EE) RADEON(0): Chipset: "AMD Radeon HD 6800 Series" (ChipID = 0x6739) requires KMS
[   128.239] (II) UnloadModule: "radeon"
[   128.239] (II) Unloading radeon
[   128.239] (II) UnloadModule: "vgahw"
[   128.239] (II) Unloading vgahw
[   128.239] (EE) Screen(s) found, but none have a usable configuration.
[   128.239] 
Fatal server error:
[   128.239] no screens found
[   128.239] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   128.239] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   128.239] 
[   128.243]  ddxSigGiveUp: Closing log

```

There is the xorg log.  I am really not 100% sure what is going on or how to fix it.  I wonder if it might be a bug int he kernal as it fails across distributions and I believe different kernals.  As far as I can tell, it *should* be supported in the kernals I am currently using in Fedora 16 AMD64 and Kubuntu AMD64 11.10. 

AlphaA

---

### Post by kubug on 2012-02-14
Sounds like you are not alone with your issue. Check this thread out: [http://ubuntuforums.org/showthread.php?p=11641004#post11641004]("http://ubuntuforums.org/showthread.php?p=11641004#post11641004")

I guess you could get X to run by typing 'startx'. ANd the follow the guide I gave you to install the latest drivers (via making .deb packages, not letting the installer do it for you).

---

### Post by kubug on 2012-02-14
> **Zmorf said:**
> I got the same problem, using ASUS Radeon hd 6950 with a quad 1920*1080 screen setup. 

Only manage to get mirror screen working, catalyst only crashes when im pressing "Ok"

Have you tried running the amd console via a terminal?

In terminal:
```
sudo amdcccle
```

That solved the issue for me with the crash. I also then checked to see if the program wrote anything into /etc/X11/xorg.conf.

---

### Post by alphaamanitin on 2012-02-14
I'll try that when I get home, didn't know you could do that.

AlphaA

---

### Post by kubug on 2012-02-14
It's worth a try. Also, have you tried to run Ubuntu 11.10 from a 'freshly' made USB stick or CD?

---

### Post by alphaamanitin on 2012-02-14
Yeah, I just downloaded 11.10 about 2 days ago, still fails.  Will keep trying though.

AlphaA

---

### Post by Yellow Pasque on 2012-02-14
You can try the alternate install cd, or try booting with xforcevesa option.

---

### Post by alphaamanitin on 2012-02-14
> **Temüjin said:**
> You can try the alternate install cd, or try booting with xforcevesa option.

'xforcevesa' give graphical errors rendering the display worthless.

AlphaA

---

### Post by jonnyboysmithy on 2012-02-14
I've emailed AMD via the support on their site.
Hopefully they'll acknowledge the problem and help me fix it or release a patch (I don't think its just a few people having this issue).
I could use the open source driver but then my laptop battery doesn't last long and it runs really hot and loud.
I'll let you know if I get a solution.

---

### Post by jonnyboysmithy on 2012-02-15
Okay I got it working!!

Ok so I'll just post what I did to make it work for me.
The details:

First purge the current driver:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```Then change to your driver directory AND force install. YES! I said force install.
I know force is not recommended but I tried plenty times and the only time it worked was with force.:confused:
So:
```
cd <your driver location> ##for me its /home/jotham/catalyst12-1/## 
sudo ./amd-driver-installer-12-1-x86.x86_64.run  --force
```Install everything default, well that worked for me so thats what I'll recommend.

Someone had a problem with initramfs not being updated so to make sure I did:```

sudo update-initramfs -u
```Run
```
sudo aticonfig --initial
```to make a configuration for your hardware with your new driver.
Restart and thats it!
Before I restarted I decided to switch to eco graphics:
```
sudo aticonfig --px-igpu
```Anyway that worked for me.:D:D:D

 Good luck!

---

### Post by jonnyboysmithy on 2012-02-15
After some experimentation it seems the critical step for me was to switch to eco graphics before restarting after I installed the driver.
After installing the driver you need to configure it with aticonfig:
```
sudo aticonfig --initial
```
And after that tell it to use the power save graphics:
```
sudo aticonfig --px-igpu
```
Then restart. For me that prevents it from getting a scrambled splash screen.

---

