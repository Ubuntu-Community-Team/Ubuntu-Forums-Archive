---
title: "Fix Gateway Laptops with Intel 965 and Realtek 8187b"
date: 2008-01-27
forum: Hardware &amp; Laptops
---

### Post by TheDilettante on 2008-01-27
I just bought a Gateway laptop, with an Intel 965 video card and a Realtek 8187b wireless card (why? because it was cheap and I knew Ubuntu would make it sweeet.)  Today I have finally captured all the bugs and wanted to put in one place solutions to problems I see many other Gateway users asking about.  As I am just a newbie, I would have appreciated this kind of collation (and if this many reposts is inappropriate, someone just say so and I'll stop.)

**Intel 965 and Screen Resolution**

For whatever reason, the 965 is quite fussy.  Finally I found AbtZ's answer ([http://ubuntuforums.org/showthread.php?t=610407](http://ubuntuforums.org/showthread.php?t=610407)) and it worked like a charm.  The relevant summation is that in order to fix the problem, you need to edit your xorg.conf (/etc/X11/xorg.conf) and replace

> Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

with

> Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
        Option          "monitor-TV"    "TVOutput" 
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier      "TVOutput"
        Option          "Ignore"        "true"
EndSection 

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800" "1024x768"
	EndSubSection
EndSection

Now you can keep the machine's native resolution of 1280x800.  For whatever reason Ubuntu isn't automatically happy with Gateway's TV-Out ports.

**Realtek 8187b Wifi**

This is the one to which I lost several days.  If anyone finds this useful, thank clayt0njknight, whom I am quoting ([http://ubuntuforums.org/showthread.php?t=633446&page=2](http://ubuntuforums.org/showthread.php?t=633446&page=2)).  

> This notebook contains the Realtek 8187b chipset. Crappy. NDISWRAPPER was the solution for me, sort of.

basic steps i took to get it working:

1.) disable wifi using hotkey (fn+F2).
2.) download latest NDISWRAPPER from repository
3.) download realtek 8187 drivers from realtek's site, or simply do 
    "wget [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)"
4.) extracted zip file
5.) opened terminal, changed to folder containing WinME driver (in this case it was /home/clay/Desktop/rtl8187b/WinME)
6.) input the following:
sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -m
sudo ndiswrapper -ma
sudo ndiswrapper -mi

7.) enable wifi using same hotkey sequence as step 1.
8.) restart machine
9.) left click on network manager at the top of my screen, chose manual configuration.
10.) selected wireless network adapter and clicked properties.
11.) uncheck "enable roaming"
12.) entered ESSID manually
13.) chose DHCP from drop down list in second section of window and click ok.
14.) you should see a little window pop up with a pretty flashing scrollbar that says "changing network adapter."

once that window disappeared, i was able to browse the web wirelessly. took me a month to figure out disabling the adapter upon using ndiswrapper, then configuring my network setup manually does the trick. pain in the *** if you travel a lot, but the good news is if you have it set to "enable roaming" it will find any access points around you, it just won't obtain an IP address from them for you automatically. Realtek is usually pretty good about releasing wireless drivers for linux for their products, but they are really lagging on this one.


So far so good.  And if you don't travel much then you can stop reading now.  I'm a broke college grad, so most of my internet comes from coffee shops, and so I appreciate automation.  Turns out it's easy.  Once you can, in fact, get your wireless, go ahead and get Wicd, a network manager similar to Network Manager.  From [http://wicd.sourceforge.net/download.php:](http://wicd.sourceforge.net/download.php:)

> 
Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) feisty extras 

where feisty is your version of Ubuntu (Dapper, Edgy, Feisty, Gutsy). Then, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. 

Now comes the scary part.  In order to run Wicd, I had to remove Network Manager, meaning that I could possibly cut myself off from the internet completely - significant because I was doing all this network crap in a coffee shop, and could not ask if I could just run some cables to their modem... Anyway, you either sudo apt-get remove, or simply remove Network Manager through Synaptic.  Once it's gone, go to Applications -> Internet -> Wicd.  It should connect you automatically to the nearest unsecured network, or prompt for a password.

If you have been successful so far, then the last step is making Wicd boot on startup.  Again from Wicd's page:

> 
In GNOME, to get the tray icon to automatically appear at boot, go to System > Preferences > Sessions. In the "Startup Programs" tab, click the "New" button. Give it a name ("Wicd" works fine). For the command, enter "/opt/wicd/tray.py".

And if all is well, then from here on you should have a network connection as sharp as your OS.

I am wildly indebted to everyone I've quoted (and everyone on this forum at all, for that matter) and hope this post counts as good thanks to them,  If these strategies helped you, thank their various inventors.  Lastly, any additions are great.  Being an incompetent dilettante I have probably left too much out...

Cheers to Cheap Hardware+Ubuntu!

---

### Post by emergingtechnologies on 2008-02-15
I'm guessing this problem is related to my Gateway screen problem.  My screen works when it is the laptop is plugged it but the screen will not work when it is not plugged in.  Is this the kind of problem that will be solved with Hardy?

---

### Post by tootlet on 2008-02-15
Greetings,
I thought I'd write my saga for triple booting the P-6831FX. I'm a Linux fan but have to use Windows for a couple of applications for my business. I've been looking for a laptop with 17 inch screen, dedicated Nvidia graphics, with enough storage to hold my MP3 collection, 3 OS's and all my necessary applications. I couldn't believe the price I was getting on this machine from BB.

I spent about an hour with [www.blackviper.com](www.blackviper.com) and “tweaked” my services as he directed. I also spent an hour or so removing the bloatware. I tried running pcdecrapifier as I had read that this would take this stuff out but it didn't work for me. This did result in a noticeable improvement in response though I had also gotten rid of the visual effects and selected performance so I'm not sure which lead to the improvement.

From zipzoomfly I ordered a Seagate Momentus 7200.2 ST9160823AS Sata mobile hard drive rated at 3 Gb/s and after fumbling around for 30 minutes installed it. This would take a normal person about 15 minutes following the manual but first I used screws with too large heads, had a heck of a time finding 4 fine threaded screws with the flat heads, had immense help from my cat who decided these 4 screws were just what he needed to play hockey with, etc. Actually very easy install. 

I created the back up disks. (I'm not totally stupid!). Then I installed Ubuntu 7.10 or Gutsy Gibbon if you prefer. I had some trouble with this as the only resolution that it would take is safe mode or 800x600. This put the back, cancel and install buttons out of sight. I had to tab and use the enter key to get it installed. Specifically I hit enter for the English, US querty, enter for the time zone, from there I hit the tab button 3 times to get to next. I used the total disk sdb or the Seagate in this case for my Linux OS.  It installed without difficulty. I had the ethernet port plugged into my network. It uses DHCP and I had a connection after the install. The restricted drivers from Ubuntu didn't work as it claimed I didn't have a supported Nvidia device. Of course I still had 800 x 600 resolution so I installed Envy from:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and it handily installed the Nvidia driver for me.  This chip is too leading edge I'm afraid. I've never tried to use a wireless device with Linux and I had read many horror stories. But I saw a blog about Wi-Fi Radar and installed that. I had to fuss with it a little to get my TKIP security password in the right spot and I had to assign the wireless access device an IP address though my LAN is set up for DHCP. My Smoothwall firewall accepts this without a hiccup and I had a nice wireless connection in under 15 minutes. 

Okay let's turn to Windows. First I used Gparted to set up partitions on sda or the Western Digital 250 Gb hard drive. I wanted 25 for XP, 50 for Vista and the rest I was going to set up as an ext3 partition, install an ext driver in the Windows and use it as storage for all three OS's. I was planning on leaving the recovery partition intact. So much for plans. I managed to muck it up (I always tell myself that is the way I learn). Gparted is relatively easy so it takes a real idiot to f#$k the whole thing and I did it with ease. But I learned from my mistakes and after 30 minutes had my 3 partitions and started the install of XP having heard it was easier to start with XP, then Vista. I used nLite from:
ttp://www.nliteos.com/ to slipstream in XPSRP2, all the security patches, the wireless and the SATA drivers. I got the SATA driver and the driver for the wireless ethernet from the Gateway site for this machine. I couldn't find any other drivers except for the wired Ethernet and this is only because the XP and Vista drivers are the same. More on that later. I installed XP. I managed to get the wireless connection to my LAN, futzed briefly with other drivers and got very frustrated. I could never get the wired Ethernet port to work. Although the Gateway site says they are XP compatible it wouldn't install. I tried it in safe mode and as administrator and I got an error message saying the administrator had prohibited this activity. I don't remember doing that. Since this is an Intel chipset and it is used on an ASUS laptop that can be used with XP I figured I wouldn't have too much trouble getting a chipset driver. Wrong. I did get audio working, I can plug in a thumb drive or external hard drive and read/write it but device manager says there is something not right about it. And I tried [www.laptopvideo2go.com](www.laptopvideo2go.com) but was unable to get a video driver installed for XP. Very discouraging. 

But on to Vista. Vista installed from the recovery disk with no issues. I had downloaded all the drivers from Gateway's website and applied all of them except the video drivers. I was hoping to use laptopvideo2go's but despite inserting the modded .inf file it was no go. I used the one from Gateway's site. Wireless gave me a little trouble as it needs to be “repaired” after each boot and that is a 3 or 4 click process. I had to do that sometimes in XP and it was a two click thing. Progress. I spent another half hour with [www.blackviper.com](www.blackviper.com) getting the services pruned. Then I tried rebooting into Ubuntu to find I had messed up Grub. I attempted to fix it using the Ubuntu liveCD and Knoppix to no avail. So I reinstalled Ubuntu and had to work out while the 186 security patches downloaded....again.  Reinstalled Envy and got the Nvidia driver to work. You have to hand edit (at least I did) the /etc/X11/xorg.conf file with the line: Modes “1440x900” to get that resolution. Looks great though. And Ubuntu is very fast on the 7200 RPM Seagate rated at 3 Gb/s. 

I still have to get XP working to a reasonable level as there is a program I need that won't work on Vista. I may never log into Vista but it is there if I need it. Ubuntu works great so far though I haven't attempted to set up NFS server and client as well as Samba. 

It is a great machine. I was lucky to order it at the $1249 price level but shipping and taxes got it about $1350. Another $150 for the SATA hard drive.....T9300 when I can! I hope you enjoy your Gateway machine. 

Tom

---

