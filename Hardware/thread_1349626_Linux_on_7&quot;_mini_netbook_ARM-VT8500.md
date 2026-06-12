---
title: "Linux on 7&quot; mini netbook ARM-VT8500 ?"
date: 2009-12-08
forum: Hardware
---

### Post by celem on 2009-12-08
EBay is currently flooded with super cheap tiny laptops that currently sell for around $125 but after Christmas may drop below $100. The are all pre-loaded with WINCE 5.0 or 6.0 but I feel comfortable that they could run some flavor of Linux, maybe xubuntu, if someone figured out to load it. It wont boot from a unetbootin stick - in fact I suspect that there is no BIOS and that the kernel image is factory loaded into the 2GB SSD drive.

Has anyone had any success with loading Linux onto one of these?

My little writeup on the device follows:
----------------
I purchased a small notebook machine direct from Hong-Kong distributor, through eBay. The are commonly listed on eBay as '7" mini netbook'. It is a generic mini-laptop running a WinCE6.0 kernel on a VIA ARM-VT8500 processor.

It is a cute little machine, weighing 1 pound, 5.7 ounces with a 800x480 7" screen, measured diagonally. This machine is absolutely generic with no brand name whatsoever. Installed memory is 128MB. The 2GB Flash Disk has 1.7GB of formatted space, currently with 1.59GB free. Closed, the units deminsions are 8-3/8 inches wide, 5-3/4 deep and 1-1/4 high. When open the unit is about the same size as a standard sheet of printer paper (8.5x11).

It contains MicroSoft  Media Player, Internet Explorer 6, WordPad and MicroSoft Messenger, but also several 3rd-party software packages:
a MicroSoft Office compatible suite by SoftMaker Software GmbH, supporting Word, Excel and PowerPoint formats. 
Other 3rd-part software installed is WinRAR, Foxit PDF Reader, Image Viewer and audio recorder. 
It also contains an email client, nPOP, titled Outlook on the desktop. As delivered, nPOP does not support SSL (needed for gmail and Yahoo-mail) but SSL support can be added by installing three DLL files:
 npopssl.dll from [http://www.nakka.com/soft/npop/download/npopssl/npopssl002arm.zip](http://www.nakka.com/soft/npop/download/npopssl/npopssl002arm.zip)
 libeay32.dll and ssleay32.dll from [http://npopuk.org.uk/2.13/dl/openssl-0.9.8l.tar.gz](http://npopuk.org.uk/2.13/dl/openssl-0.9.8l.tar.gz)

The Internet Explorer browses most sites OK, albeit a bit slowly, but its antiquated java engine fails to support some sites, such as PowerMyPc.com's internet speed test. Also, YouTube doesn't work, complaining that the Flash Player needs to be updated. Yahoo Mail classic works just fine, as does Gmail. According to IronGeek.com, the browser identifies itself as Mozilla/4.0 (compatible; MSIE6.0; Windows NT 5.1)

Although the minimal documentation indicates that the SD slot is just that, an SD slot, in actuality it also supports SDHC.

There are three USB ports. The ones on the side are labeled keyboard and mouse, but they work fine with a USB-stick.

WiFi works just fine with my in-house D-Link router. In addition to built-in WiFi, there is an ethernet port.

This machine has some oddities. There doesn't appear to be a BIOS ROM - thus booting from a unetbootin USB is impossible. The WINCE kernel must be directly loaded into the flash drive at the factory, probably using some external tool. There are no disk drive letters. A plugged-in SD card or USB stick can be accessed by programs, such as WordPad, but they are not mounted on the desktop. There is no resident file explorer, but you can access the SD card or USB stick by opening the "My Computer" icon. Another way to access a SD card or USB stick directly is to access the SD card or USB stick from the command line (RUN->CMD). Another oddity is that every time you turn on the machine, the WiFi is powered off. If you want to use WiFi you must power it on via a desktop icon title "WiFi Power". Obviously this is a power conservation theme. There is a keyboard key with "Z z z" on it, which implys, to me atleast, sleep mode. However, it does nothing. Furthermore, closing the lid does not darken the screen or trigger a sleep or hibernate mode. In fact, in the control panel's Poers section, the sleep and hibernate modes are greyed out. Obviously this machine doesn't support sleep or hibernate mode - possibly due to the missing BIOS and its associated APCI. The keyboard key with "Z z z" is probably generic and intended for a different model, namely one with a BIOS.

In summary, despite its oddities, this little machine would be useful in some situations as a laptop, especially where a larger or more expensive machine was not desirable. I think that it would be useful for keeping a journal while traveling and checking email at public WiFi hotspots. The web browser's slowness and antiquated javascript support and lack of Flash significantly weaken browser functionality, but Google and many other useful sites work just fine.

---

### Post by Fafler on 2009-12-09
You would probably need to put another bootloader on it. Look at the Familiar project. It has been dead for some years, but the mailing list is still active. The aim of the project was to run Linux on CE devices like older iPaq's, but even though most of them was PXA based, i still think those guys might be able to help you.

---

### Post by dimeotane on 2009-12-16
VIA-ARM VT8500 I don't think that will run the usual i386 version of Ubuntu.  There's a quiet a few different versions of these 7 inch screened netbooks from China all with different processors.  Some are ARM, some VIA, other RDC cpu...
Some with <256mb RAM.

I think there's some out there with >256mb ram and a 1GHZ X86 processor. Like [this]("http://www.mobidata.com/en/product/product.php?id=89") one.  That sounds like a good set of specs to me for running the usual Ubuntu.  It is possible to run with less however (like with Xubuntu). 

I sure wish these mini netbooks had a vga out port for doing powerpoint presentations!

I've been reading prices as low as $70 to 80 USD for one of these.

---

### Post by celem on 2009-12-17
I've been thinking of opening mine up to look at the board. I read from a post by someone that did (partially) open it up, that there was a single board inside. I suspect that the variations are slight and that all are based upon the same board design and coming from the same Chinese factory.

I feel strongly that there is no BIOS (to further reduce costs) and that the OS is loaded externally via some debugging tool.

---

### Post by snowpine on 2009-12-17
Yuck, those specs are terrible... even the original 2007 Asus eee had 512mb of ram. :(

---

### Post by celem on 2009-12-17
Yes they are terrible, yet surprisingly it works fairly well. I even loaded an old PowerPoint presentation and, to my great surprise, it loaded and displayed perfectly. I could use this for presentations except there is no external VGA port. The basic office-type applications and email work fine as their processor requirements are small. The MicroSoft IE 6 browser works well but is noticeably slow. When I hit a page with lots of photos and javascript it browser will lock up until it has processed it all.

I can't help but wonder how a really lean Linux distro would work in it.

---

### Post by 00b00nt00 on 2009-12-17
Is there anything here which might help?

[http://www.ubuntu.com/products/whatisubuntu/arm](http://www.ubuntu.com/products/whatisubuntu/arm)

---

### Post by PerChristensen on 2009-12-18
A small precompiled linux image + U-boot bootloader seem to exist HERE:
 
[http://www.arm.com/products/os/linux_download.html](http://www.arm.com/products/os/linux_download.html)
 
Also a free ARM compiler seem to be available HERE:
 
[http://linux.onarm.com/index.php/Main_Page](http://linux.onarm.com/index.php/Main_Page)
 
A (Windows) Burntool to burn "bootloader" and compiled Linux image on mini NB could be?:
 
[http://www.nxp.com/products/microcontrollers/support/software_download/lpc2000/](http://www.nxp.com/products/microcontrollers/support/software_download/lpc2000/)
 
or perhaps better (again Windows app):
 
[http://www.flashmagictool.com/](http://www.flashmagictool.com/)
 
Crosslink ethernet cable between host Linux or Windows box to mini-notebook for establishing connection, and then burn 
1. bootloader at right hex adress
2. then the free Linux image onto mini notebook FLASH-ROM??
 
Also I think it is possible to set up an ARM cross compiler on your running Linux box if you compile a new GCC compiler from source TAR ball and specify " make --with-arm " or something like when compiling.
Perhaps it is then possible to compile f. ex. math.app. Maxima for such a small thing mini notebook??
 
This is just fast notes,but I will happily in Xmas holidays join trying to get something to work (I run Scientific Linux 4.0 - a Redhat Enterprise 4 clone + XP on another PC)
 
For specs of notebook see as of dec. 18:
 
[http://cgi.ebay.co.uk/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ320463454635QQcmdZViewItemQQptZUK_Computing_Laptops_EH?hash=item4a9d1c41ab](http://cgi.ebay.co.uk/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ320463454635QQcmdZViewItemQQptZUK_Computing_Laptops_EH?hash=item4a9d1c41ab)

---

### Post by celem on 2009-12-18
You really did your homework. These links look promising. With the Christmas arrival shipping date past, the prices are dropping. Under $100 e/w shipping is now common ([http://tinyurl.com/y8bv4cf](http://tinyurl.com/y8bv4cf)). I have to proceed carefully - I don't want to brick it.

---

### Post by PerChristensen on 2009-12-19
Hello celem
Perhaps it will only be you and I thinking this way.I have a cross cable somewhere but has to buy a new one as I am not sure which one it is,and I can`t go to the mall at the moment because of heavy snow.
As I see it we should focus on
1. Working burn tool (does a linux tool exist?) 
2. What hex address to burn U-boot bootloader to.
Let us take it easy the next days,hope other interested will join and perhaps in a few days make some sort of progress plan.Sincerely Per

---

### Post by PerChristensen on 2009-12-19
Sorry,my monologue continue.The FlashMagic tool would not recognize the linux kernel binary,and LPC2000 flash utility do not support burning over LAN.
 
As ARM compiled U-boot bootloader,Linux kernel and cramfs Linux filesystem are available (I will go for the ARM926EJ brand) it could be possible to burn a running system with **tftp** command via port 69
 
[http://www.embedian.com/index.php?main_page=ubootdownload](http://www.embedian.com/index.php?main_page=ubootdownload)
 
Notes from ARM homepages say: U-Boot is expected to run from 0x01000000 in memory on ARM boards (Later **[COLOR=#0000ff]RealView[/COLOR]** boards 0x06000000) but the embedian method looks OK.
 
Some fiddling is necessary,and I will later give it a try with crossover cable from Linux machine to mini notebook.
The notebook recognize cabled LAN out of the box when wireless disabled.

---

### Post by celem on 2009-12-20
Reading linux-arm.org confirms my suspicion that an external device is required to load the image. "*Images can be installed into flash using a debugger connected to the board via a JTAG run control device, such ARM RealView ICE units. *"

The VT-8500 is a System On a Chip:

Via Technologies has quietly established a subsidiary called WonderMedia, which is readying a multimedia-capable ARM9-based system-on-chip (SoC). An early version of the “Prizm” SoC, called the VT8500, is available in a Linux-ready NorhTec MicroClient TC thin-client that costs $100, says the company. 

[http://www.linuxdevices.com/news/NS9467479495.html?kc=rss](http://www.linuxdevices.com/news/NS9467479495.html?kc=rss)

---

### Post by PerChristensen on 2009-12-20
Celem,perhaps it was such a board we should be playing with instead!.Or wait until our minibook does come with Linux - the coming "Africa 100$ model" your link point to is just what we both are looking for,so why spend time on a project like this?.
 
Nevermind,because of bad weather and pure ice on the roads I have just been able to focus on buying a couple of christmas presents and get home unharmed,so I still need a crossovercable (and now also a oldfashioned male-male USB cable) to work the Linux way.
 
A small progress: via vt8500 arm processor seems to be identical to the arm926EJ-S processor.
 
On Vista wireless laptop I have enabled telnet + TFTP client (control panel -> programs install/uninstall -> turn windows programs on/of ) + disabled the Windows firewall,and after rebooting with into safe mode with network enabled due to some (antivirus?) issues these clients work well at CMD prompt.
 
WindowsCE also has CMD in the Windows directory.It has (undocumented) ping,and via wireless I can ping back and forth.To check my wireless routers firewall settings / a working port 69 on notebook from Vista I did " telnet xxx.xxx.x.xxx 69 " where x stand for mini notebook IP.When no error in terminal/CMD window everything should be OK.
 
On mini notebook I have copied this TFTP server to the root (the ARM V4I version):
 
[http://tftpce.codeplex.com/Release/ProjectReleases.aspx?ReleaseId=23013](http://tftpce.codeplex.com/Release/ProjectReleases.aspx?ReleaseId=23013)
 
I renamed to TFTP.exe and can then be started from WindowsCE CMD when typing TFTP,or on doubleclick,and will display: server is bound to port 69 waiting for connection.
From Vista you can then do " tftp -i xxx.xxx.x.xxx put c:/kids.gif " or similar (where again x stand for mini notebook IP),and the picture will be transferred to the notebook`s root.I have not figured out to TFTP the other way.
 
As I have understood the main thing is to copy the binaries to memory of notebook and then reboot - have a look at middle section of this article,if you like: 
 
[http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Introduction-to-Das-UBoot-the-universal-open-source-bootloader/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/Introduction-to-Das-UBoot-the-universal-open-source-bootloader/) 
 
Under all circumstances this little thing is nice - the office suite alone is worth the money,and Skype should work also,if installed.Hotspots are everywhere these days,so sit down in your café and pull your office up your pocket.
 
It could be interesting to check if the notebook is recognized as flash drive by Windows if connected with USB cable and the booted up - (or booted up with zzz or another button pressed).

---

### Post by dwinston91 on 2009-12-21
This forum has been very helpful.  I have been trying to find information to do this for the past month or so.  My wife bought two of these mini-notebooks or 7 inch Notebooks as they are called on the box.  Information was very hard to come by.  I come from a Windows background, with the last bit of my Unix work done while I was in college in the 90s.  So I had to do a lot of research.  The main reason I wanted to switch to Linux, was because Adobe Flash is not fully supported on Windows CE 6.0.  The reason my wife got the notebooks, was for my daughters to use to access their favorite web pages which are all Flash sites.  I was able to hack the Windows CE 6.0 R3 to get the correct Dlls for Adobe Flash Lite support (which currently only goes up to Flash 8 and register Flash Lite using the the IE.reg file in WIN CE 6.0 R3.  Since all the sites have been updated to use Flash 9 or above..they can't use them for the purpose they were bought.

Anyway I looked through some of the references you all  posted and noticed the Notes for installing Linux on Arm.  Did you see the notes?  It references a tool that I am now currently trying to find:  Network Flash Utility. [I]"This program enables programming of images into flash using an 
       ethernet connection."[/I] Here is the link to the Notes.  [URL="http://www.linux-arm.org/LinuxReference/LinuxOnARMDev?redirectedfrom=Main.LinuxOnARMDev"]http://www.linux-arm.org/LinuxReference/LinuxOnARMDev?redirectedfrom=Main.LinuxOnARMDev
[/URL]

---

### Post by dwinston91 on 2009-12-21
There is a keyboard key with "Z z z" on it, which implys, to me atleast, sleep mode. However, it does nothing. Furthermore, closing the lid does not darken the screen or trigger a sleep or hibernate mode. In fact, in the control panel's Poers section, the sleep and hibernate modes are greyed out. Obviously this machine doesn't support sleep or hibernate mode - possibly due to the missing BIOS and its associated APCI. The keyboard key with "Z z z" is probably generic and intended for a different model, namely one with a BIOS.

I found out that the Zzz key is actually the Windows Key.  It has the same functionality of the windows key...Try it out.  Zzz key + E   opens Windows Explorer.

---

### Post by doudar on 2009-12-21
My boss just bought one of these for the same reason as the post above - For the kids to play Internet games. He gave it to me to see if I could get linux + flash on it. It's a cute little thing, but it sounds like I'm going to have to tell him the bad news. I can't risk bricking his netbook.

---

### Post by dwinston91 on 2009-12-21
Well if we figure it out maybe we can put up some step by step instructions.

---

### Post by PerChristensen on 2009-12-21
Hello dwinston91 and doudar.
 
Yes,Youtube and facebook is what the kids want - and do not get. 
I too have googled for the Network Flash Utility (NFU) seeming to be part of software ment for the RealView developing boards.These (commercial) boards + the belonging proprietary applications cost something,and the RealView company will probably (and understandable) stick to this utility.
But to ask politely does not cost anything :P.
 
I remember a MP4 player (sunplus game king) looking a bit like a PSP but with camera and emulating NES games:
 
[http://mympxplayer.org/1-vt8674.html?postdays=0&postorder=asc&&start=0](http://mympxplayer.org/1-vt8674.html?postdays=0&postorder=asc&&start=0)
 
When connected via USB to Windows PC and pressing a "combo" when booting the device Windows would ask for the camera drivers,then part of flash ROM was mounted as a drive,and a hidden operating system could be lifted off with a tool found in the downloads/tools section on the site.
Some ARM tools perhaps can be found at the site,I have not looked yet.
 
I guess our ARM chip also support camera / webcam if used in other devices.Also one could search/ask for help at Samsung who perhaps has licensed this processor to company VIA.
Just back from a meeting,will now have a cup of cofee.Talk to you later.

---

### Post by dwinston91 on 2009-12-21
I can actually view some Youtube videos.  Some say it requires Flash 9, but I have watched a few videos on Youtube.  I can also view my Facebook pages as well.  I mentioned how I hacked the WinCE 6.0 R3 Adobe Flash Lite and I am able to view some flash sites.

---

### Post by PerChristensen on 2009-12-22
Indeed this is an amazing gadget as it is.Probably email client nPOP 1.0.9 can be set up to read my yahoo mail, a telnet client PocketPuTTY look promising, an early version 1.21 of the Total Commander for windowsCE also is freeware etc. etc..
Too I read on the net the Firefox community are working on a port of Firefox webbrowser for - yes - Windows CE6!.
 
The youtube mobile site
 
[www.m.youtube.com]("http://www.m.youtube.com")
 
unfortunately on my netbook trigger the Windows media player not supporting youtube mobile .3gp format,and my system hang.If instead the Core player was triggered I think videos would have played ok..
 
dwinston91,could you be kind and give a hint of your hack to get youtube videos working?.
 
I still intend to explore our device a bit more when peace settles in the holidays,but perhaps I should think of this old Bob Dylan tune before pressing the final enter
 
[http://www.youtube.com/watch?v=P1xGTanXvfs](http://www.youtube.com/watch?v=P1xGTanXvfs)
 
Merry Christmas to all.

---

### Post by Fafler on 2009-12-23
Someone should take it apart and look for a JTAG connector. It's the best way to play around with the flash memory, as you can't brick it. Or atleast JTAG makes it a bit harder to do so.

---

### Post by dwinston91 on 2009-12-23
After I realized that Windows CE 6.0 R3 had Adobe Flash Lite Support (which supports websites with Flash 8 , I went [here]("http://www.microsoft.com/downloads/details.aspx?displaylang=en&FamilyID=bc247d88-ddb6-4d4a-a595-8eee3556fe46") to download an evaluation edition of Windows CE 6.0 R3.  Then I used Nero (or any other app that will allow you to extract files from an ISO) and extracted the following files: 

12/01/2009  04:00 AM         1,448,128 flash.dll
09/17/2009  02:03 AM         1,352,192 flashlite_wince.dll
09/17/2009  02:03 AM           121,344 flashsnddec_wince.dll
09/17/2009  02:03 AM            81,408 flashviddec_on2_wince.dll
09/17/2009  02:03 AM            56,832 flashviddec_sorenson_wince.dll
09/17/2009  02:03 AM           337,920 flaxplayer_wince.dll
09/17/2009  02:03 AM             4,096 flax_resources_wince.dll

and I copied the following text from the 0213_ie.reg file, to register the Adobe Flash Lite portion, and created a file called FlashLite.Reg.  

[HKEY_CLASSES_ROOT\AppID]
@=""

[HKEY_CLASSES_ROOT\AppID\{EC5B7C25-899A-479F-B5A8-CA2D2FC74931}]
@="FlaxPlayer_wince"

[HKEY_CLASSES_ROOT\AppID\FlaxPlayer_wince.DLL]
"AppID"="{EC5B7C25-899A-479F-B5A8-CA2D2FC74931}"

[HKEY_CLASSES_ROOT\MacromediaFlashPaper.MacromediaFlashPaper]
@="Macromedia Flash Paper"

[HKEY_CLASSES_ROOT\MacromediaFlashPaper.MacromediaFlashPaper\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"


[HKEY_CLASSES_ROOT\FlashFactory.FlashFactory]
@="Macromedia Flash Factory Object"

[HKEY_CLASSES_ROOT\FlashFactory.FlashFactory\CLSID]
@="{D27CDB70-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\FlashFactory.FlashFactory\CurVer]
@="FlashFactory.FlashFactory.1"

[HKEY_CLASSES_ROOT\FlashFactory.FlashFactory.1]
@="Macromedia Flash Factory Object"

[HKEY_CLASSES_ROOT\FlashFactory.FlashFactory.1\CLSID]
@="{D27CDB70-AE6D-11cf-96B8-444553540000}"


[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash\CurVer]
@="ShockwaveFlash.ShockwaveFlash.8"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.1]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.1\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.3]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.3\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.4]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.4\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.5]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.5\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.6]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.6\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.7]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.7\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.8]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.8\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.9]
@="Shockwave Flash Object"
"EditFlags"=dword:00010000

[HKEY_CLASSES_ROOT\ShockwaveFlash.ShockwaveFlash.9\CLSID]
@="{D27CDB6E-AE6D-11cf-96B8-444553540000}"



[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}]
@="Shockwave Flash Object"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Control]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\EnableFullPage]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\EnableFullPage\.mfp]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\EnableFullPage\.spl]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\EnableFullPage\.swf]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Implemented Categories]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\InprocServer32]
@="\\Windows\\FlaxPlayer_wince.dll"
"ThreadingModel"="Both"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\MiscStatus]
@="0"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\MiscStatus\1]
@="131473"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\ProgID]
@="ShockwaveFlash.ShockwaveFlash.1"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Programmable]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\ToolboxBitmap32]
@="\\Windows\\FlaxPlayer_wince.dll, 1"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\TypeLib]
@="{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\Version]
@="1.0"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB6E-AE6D-11cf-96B8-444553540000}\VersionIndependentProgID]
@="ShockwaveFlash.ShockwaveFlash"


[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}]
@="Macromedia Flash Factory Object"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Control]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Implemented Categories]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Implemented Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Implemented Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\InprocServer32]
@="\\Windows\\FlaxPlayer_wince.dll"
"ThreadingModel"="Both"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\ProgID]
@="FlashFactory.FlashFactory.1"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Programmable]

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\ToolboxBitmap32]
@="\\Windows\\FlaxPlayer_wince.dll, 1"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\TypeLib]
@="{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\Version]
@="1.0"

[HKEY_CLASSES_ROOT\CLSID\{D27CDB70-AE6D-11cf-96B8-444553540000}\VersionIndependentProgID]
@="FlashFactory.FlashFactory"

[HKEY_CLASSES_ROOT\TypeLib\{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}]

[HKEY_CLASSES_ROOT\TypeLib\{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}\1.0]

[HKEY_CLASSES_ROOT\TypeLib\{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}\1.0\0]
@="\\Windows\\FlaxPlayer_wince.dll"

[HKEY_CLASSES_ROOT\TypeLib\{B62F8115-CFCC-4DBB-AE17-FD3DE3110276}\1.0\0\win32]
@="\\Windows\\FlaxPlayer_wince.dll"


[HKEY_CLASSES_ROOT\.spl]
@="ShockwaveFlash.ShockwaveFlash"
"Content Type"="application/futuresplash"

[HKEY_CLASSES_ROOT\.swf]
@="ShockwaveFlash.ShockwaveFlash"
"Content Type"="application/x-shockwave-flash"

[HKEY_CLASSES_ROOT\.mfp]
@="MacromediaFlashPaper.MacromediaFlashPaper"
"Content Type"="application/x-shockwave-flash"

[HKEY_CLASSES_ROOT\.sol]
"Content Type"="text/plain"

[HKEY_CLASSES_ROOT\.sor]
"Content Type"="text/plain"


[HKEY_CLASSES_ROOT\MIME\Database\Content Type\application/futuresplash]
"CLSID"="{D27CDB6E-AE6D-11cf-96B8-444553540000}"
"Extension"=".spl"

[HKEY_CLASSES_ROOT\MIME\Database\Content Type\application/x-shockwave-flash]
"CLSID"="{D27CDB6E-AE6D-11cf-96B8-444553540000}"
"Extension"=".swf"


[HKEY_LOCAL_MACHINE\SOFTWARE]

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe]

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite]

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite\Memory Settings]
"Static Memory(in KB)"=dword:00000032
"Dynamic Memory(in MB)"=dword:00000128

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite\Flash Mime Types]
[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite\Flash Mime Types\Audio]
"midi"="audio/x-midi"
"xmidi"="audio/x-cmidi"
"mp3"="audio/mp3"
"3gpp"="audio/3gpp"

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite\Flash Mime Types\Video]
"avi1"="video/avi"
"avi2"="video/msvideo"
"avi3"="video/x-msvideo"

[HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\FlashLite\Flash Mime Types\Image]
"Jpeg"="image/jpeg"
"Bmp"="image/bmp"
"Gif"="image/gif"


I then copied all of the files above, including the FlashLite.Reg file I created to my device using a USB Drive.  I copied all the files to the Windows directory on my device and then I double clicked the FlashLite.Reg file I created to register Adobe Flash Lite.  After I did that, I could see websites that use Adobe Flash 8.  Some Youtube.com videos can be viewed with Flash 8 support.  There were a few Youtube pages that wouldn't load, but a lot of them did....For now...cause you know they will probably try to go to Flash 10 on everything.  

You will have to search through the ISO to find the files that look like 0123_flash.dll  The files will have four numbers and an _ in front of the names of the files.

---

### Post by dwinston91 on 2009-12-23
This website might also provide a solution depending on the price of the USB stick.  Their MIO Smartbook has the exact same specs as ours.  They provide the OCEAN OS (which is a Linux derivative of Open SUSE Linux)  The Swordfish MOD USB drive contains a bootable version of OCEAN OS.  Check out the specs and what they have to say [here]("http://haleron.com/index.php?option=com_content&view=article&id=48:ocean-os&catid=29:the-art&Itemid=55")

Here is the information on their [MIO Smartbook]("http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27").

---

### Post by celem on 2009-12-23
Green Maraschino 0 Linux may work. a similar, if not identical device is offered by Cherrypal. See:
[Cherrypal]("http://www.linux-netbook.com/cherrypal-africa-the-99-netbook")

---

### Post by PerChristensen on 2009-12-24
Due to bad weather I am stuck and have more time for myself in the holidays than wanted.And also too much time to play with the toy!.
After installing a .cab file with Microsoft GAMEapi`s for WINCE3 my netbook hangs after booting - probably because of overwriting a recent .dll with an older one.
Therefore I have disassembled the netbook.Unfortunately I cannot attach the zip file with pictures of mainboard,processor etc. to the forum as it is around 2 Mb.
 
Amazingly my netbook booted after reassembly,but still hang.If I could mount the device as usb drive I could easily copy the recent version of .dll to the flash drive,also some bootloaders "ping" network a couple of seconds before loading the kernel,and then it is possible aborting boot and connect via LAN.
 
But I`m out for the moment.Great job dwinston91,and keep the momentum,celem!
 
Download of pictures of disassembled netbook from (some limit of monthly download):
 
[http://www.hyfse.com/armVT8500/VIA_VT8500_netbook.zip](http://www.hyfse.com/armVT8500/VIA_VT8500_netbook.zip)

---

### Post by PerChristensen on 2009-12-26
Sitting at computer at family far away from home (and my hanged netbook) I will just save this link 
 
[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm)
 
with tools probably able to reinstall firmware to our book.
 
PS: on the site there are links to some games.Be carefull with GAPI:support software as it was installation of these APIS who made my netbook crash.

---

### Post by illumin8 on 2009-12-27
Ill be following this thread with great interest...

---

### Post by dwinston91 on 2009-12-28
I found this [site]("http://www.friendlyarm.net/downloads") that has a lot of tools and software on it.  Seems to be really interesting.  I have been reading the link from [PerChristensen]("http://ubuntuforums.org/member.php?u=980331") about the machines that are similar to ours.  The only challenge is that the linux machine does not have an ARM processor.  The Windows CE 5.0 machine has the ARM processor.  Now if only the Linux machine had the ARM processor, then I could use the procedures mentioned and the files they provide on their site.  It still provides good information pertaining to reinstalling an image onto these machines.  

I am looking at the [Embeddian]("http://www.embedian.com/index.php?main_page=ubootdownload") site as well.  I tried using the procedure using a linux machine, but the procedure didn't work for me when I tried the minicom part.  After setting up minicom, I didn't see what they said I should see on the screen.  

I am now trying the Embeddian solution using a Windows machine.  Hopefully that procedure will work, since it talked about using the DNW tool, that can be downloaded from the site I mentioned at the top of this post.

---

### Post by celem on 2009-12-28
> **PerChristensen said:**
> ... this link 
 
[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm) with tools probably able to reinstall firmware to our book.


The CnMbook install procedure provides an important clue, namely special pins to short, etc. The CnMbook appears identical to the unit that I purchased on eBay.

---

### Post by celem on 2009-12-28
> **dwinston91 said:**
> ...The only challenge is that the linux machine does not have an ARM processor...

Such devices are on eBay [http://tinyurl.com/yj8ntz8]("http://tinyurl.com/yj8ntz8") but getting Linux on the cheaper ARM units is the challenge.

---

### Post by sleeky24 on 2009-12-28
Hi all,
 
As this seems to be a good discussion topic regarding these mini netbooks I thought I would sign up to register my interest.
 
Some bored Christmas holiday browsing on ebay brought up these laptops and after a bit of bidding I have managed to get myself one delivered for just under $100. Hopefully it will arrive in the next few weeks.
 
**dwinston91 -**
 
With regards to the flash playback, what version of flastlite have you managed to install, is it 3.0 or 3.1, as you have stated flash 8 compatability I would suspect it is flashlite 3.0?
 
I found the following topic on another forum regarding .cab files for flashlite 3.1, which I beleive has flash 9 support which may be more compatible with youtube, etc...
 
[http://forum.xda-developers.com/showthread.php?t=423860](http://forum.xda-developers.com/showthread.php?t=423860)
 
There are links on the thread to download the .cab files however if you do need these please let me know as I have downloaded them in case I need them.
 
The thread itself is regarding windows mobile, however I beleive this should also work ok on CE.
 
As you seem a lot more clued up regarding these things than I would it be possible for you to advise if it would be possible to install flastlite 3.1 on CE using these files?
 
I will be keeping my eye on this thread for all updates regarding these little laptops.
 
Thanks,
Lee.

---

### Post by PerChristensen on 2009-12-29
Very interesting site with ARM related applications your reply point to,dwinston91.
 
As celem say the "silver" CmBook seems identical to his,and also to mine, with the armVT8500 processor.
 
Has anybody heard/seen MSWindows ask for the drivers after following the CmBook recipie?
Is it after install of the drivers possible to access (parts of) the flash rom from a file manager - copy MP4 files directly to ./my documents or similar?
 
As we get more experienced ( and after having learned chinese :) ),dreams are we all can have a windowsCE system image/ backup + a linux system (+ a android?) image on a MSWindows PC,and then burn whatever we want to the book.
 
I belive we in reaching such a goal must be consistent and stick to the hardware specified by celem - our book use Ralink RT 2070 / RT 3070 wireles drivers etc..
As celem say,our book will soon be replaced with something faster and cheaper.I cannot join exploring the hardware before I`m back at my hanged netbook early next year.

---

### Post by dwinston91 on 2009-12-29
The version of Flash Lite that I copied from was Adobe Flash Lite 3.1  As stated on Adobe's website, Adobe Flash Lite 3.1 supports Flash 8 fully.  Flash 9 support is limited a little.  Check here for more information: [http://www.adobe.com/devnet/devices/articles/web_browsability_guidelines.pdf](http://www.adobe.com/devnet/devices/articles/web_browsability_guidelines.pdf) 

Adobe Flash 9 support
Flash Lite 3.1 can broadcast itself as Flash Player 9 compatible to play back any ActionScript 2.0 SWF content, even if the content was authored using Flash 9 technology. ***[COLOR=DarkRed]However, it is based on Flash Player 8, so it does not support ActionScript 3.0, which was introduced with Flash Player 9.[/COLOR]***
Flash Lite 3.1 runtime can be embedded into OEM devices. Most phone and consumer electronic devices do not offer automatic browser upgrades of plug-ins. Many developers incorporate mechanisms (JavaScript functions) in their websites that can detect FLV and SWF content to ensure that visitors are either routed to viewable content&#8212;based on the configuration of the browser that they are using&#8212;or provided with clear instructions on how to correctly install the Flash Player necessary to view the site&#8217;s content.

The basic concept regarding detecting FLV or SWF content is:
1. Check the browser to see if the required plug-in is available. For instance, if content created with Flash 9 technology is present, Flash Player 9 is required for viewing.
2. If the appropriate plug-in is available, the browser is directed to load the web page and the content is displayed.
3. If the required plug-in is not available, the browser is redirected to an alternate website with different content or to a page containing instructions to download the latest Flash Player from Adobe.com.
This &#8220;redirection and subsequent upgrade&#8221; approach works only on desktop systems where such upgradeable players exist. Mobile and device users visiting sites with Flash Player 9 compatible content would be confused by these upgrade instructions. [B][COLOR=DarkRed]As a result, Flash Lite 3.1 broadcasts as Flash Player 9. This means that a website with embedded SWF content is passed to the Flash Lite 3.1 plug-in. Flash Lite 3.1 evaluates the SWF content and either plays it back or displays a user-friendly icon along with a message indicating that the website 
content is not supported by the plug-in embedded in the browser.[/COLOR][/B]

This means that it says to the websites, "Hey I'm Flash 9 compatible"  But if it uses Action Script 3.0, as was introduced in Flash 9, you get a little symbol that shows the Flash 9 symbol..and not the actual content.

---

### Post by dwinston91 on 2009-12-29
I opened up my machine last night and this is my exact board right [here]("http://www.benigntech.com.cn/en/admin/images/upfile/200910613474343216.jpg"): It is made by this company.  [http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192. ]("http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192")

I just wish this company had information like the CnM Book did.

---

### Post by sleeky24 on 2009-12-29
Dwinston91 - thanks for clearing that up for me, once mine arrives I will follow what you did and also try and install flastlite on my unit.

I will also probally open it up at some time to see which board my one has, perhaps we could get a list going of vendors and what board, etc.. the notebooks have?
 
Mine is listed as the same with the via VT8500 however comparing the picture of your board with those of perchristians suggests that there are some differences between vendors chipsets.
 
Thanks,
Lee.

---

### Post by Dr_Narvi on 2009-12-29
Hello Friends

 I have also a Smartbook similar that yours. I also was researching how was possible get flash player and i got my computer got hanged...

 But now I have the solution!!!  To restore the system with the factory settings only follow these steps:  
 [SIZE=3]
 -   [/SIZE]               [SIZE=3][COLOR=black][FONT=Arial]1.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]Copy the file “script” to your SD card. [/FONT][/COLOR][COLOR=red][FONT=Arial](Very important, please don’t copy the whole file “ VT8500 Software” to your SD card.  Just copy the file of “ script” will be OK)[/FONT][/COLOR][COLOR=black][FONT=Arial][/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]2.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]Turn off your netbook, [/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]3.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]Insert the SD card to your netbook.[/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]4.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]Turn on your netbook. Then the software will setup to your netbook Automatically. Usually it will take several minutes completed setup.[/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]5.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]After completed setup. It will show a windows call your turn off the netbook. Then turn off it.[/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]6.[FONT=&quot]   [/FONT][/FONT][/COLOR][COLOR=black][FONT=Arial]Put the SD card out off the netbook.[/FONT][/COLOR][/SIZE]
  [SIZE=3][COLOR=black][FONT=Arial]7.[FONT=&quot]   [/FONT][/FONT][/COLOR][/SIZE][COLOR=black][FONT=Arial][SIZE=3]Then turn on the netbook will be OK.[/SIZE][/FONT][/COLOR]
 

       [http://www.megaupload.com/?d=12PDHAYJ](http://www.megaupload.com/?d=12PDHAYJ)    



       I hope  with this files you can to find out any solution in order to improve the operative system. I had my computer hanged and now works fine!!
       Merry christmas!







[COLOR=black][FONT=Arial][/FONT][/COLOR]

---

### Post by dwinston91 on 2009-12-29
Also one thing that I found out on my machine, was a neat little program called SerialView.exe   It is located in the C:\Windows folder.  It shows a lot of information about your machine.  That is how I found out that Benign was the maker of the board that is in my machine...without opening it up.  

Mine is the BV07_A_8500.  Here is a picture of my board that I took last night.
[IMG]http://www.flickr.com/photos/dwinston91/4225487073/[/IMG][http://www.flickr.com/photos/dwinston91/4225487073/](http://www.flickr.com/photos/dwinston91/4225487073/)
[IMG]http://www.flickr.com/photos/dwinston91/4225487073/[/IMG]
Here is a close-up of the NAND Chip by Samsung: K9GAG08U0M
[http://www.flickr.com/photos/dwinston91/4225525761/](http://www.flickr.com/photos/dwinston91/4225525761/)
[IMG]http://www.flickr.com/photos/dwinston91/4225525761/[/IMG][IMG]http://www.flickr.com/photos/dwinston91/4225525761/[/IMG]
Also, here is the text that I saved from my SerialView.exe program.  I am trying to decipher some of the information in here.

[COLOR=RoyalBlue][B][COLOR=Navy]Windows CE Kernel for ARM (Thumb Enabled) Built on Sep 30 2007 at 22:37:06
+OEMInit
+VT8500OEMInit
VT8500DBGMSG: VT8500OALIntrInit
[VIASOC VT8500] BSP version: 0.91-VT8500OEMInit
-OEMInit
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 0
okey to crc verified, Go...
FMD_Init for board: VT8500_Benign
OALIoCtlShowBootProgress: HWPropList: NoBootProgressBar
FMD!DumpRegKey> Drivers\BuiltIn\NFlash 
        Profile = MSFlash
        IClass :
            {A4E7EDDA-E575-4252-9D6B-4195D48BB865}
        Order = 00000000
        FriendlyName = VIA NAND FLASH Driver (System Disk)
        Dll = flashmdd.dll
        FlashPddDll = via_flashpdd_600.dll
        Prefix = DSK
        BoundaryLeftMB = 00000000
        BoundaryRightMB = 00000180
        Flags = 00001000
OALIoCtlShowBootInformation: HWPropList: NoBootInformation
FMD_Init: g_hNandMutex = 0x01020003, 0
FMD:NAND_WAIT_READY: B2R Status not ready!!
FMD_Init: nand_reset chip 0 OK!
ReadFlashID
FMD_Init: Flash ID is ec d5 14 b6 74
initChipInfo Product ID=SAMSUNG_NF_K9GAG08U0M
Clock=00000000 r/w cycle=12122424
IsBadBlockTBLExisted(block 0x00000fff):Linux Main BBT found:  Bbt0
FMD:Scan_NandFlash: Found Wince TBL pattern=42627430
IsBadBlockTBLExisted(block 0x00000ffe):Linux Mirror BBT found:  1tbB
FMD:Scan_NandFlash: Found Wince TBL pattern=31746242
LoadNandFlashTBL: Use TBL0
GetBadBlockNum: block 0x43c in chip 0 is bad block
GetBadBlockNum: block 0x43d in chip 0 is bad block
LoadNandFlashTBL: Bad Block Num=2
FMD_Init: BoundaryLeft auto set to 128MB
FMD_Init: (Left ~ Right) / Total = (128MB ~ 384MB) / 2048MB !
FMD_Init done: System Disk.
FMD_GetInfo
FMD_GetInfo
BCH_ReadSector: Data ECC  error: startSectorAddr=0x00009830                                     (sector offset in chip is 0x00009830),                                      NFECC_STATUS2_REG value 0x00000401, ERR_POS_REG1 0x000000a2,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x00009849                                     (sector offset in chip is 0x00009849),                                      NFECC_STATUS2_REG value 0x00000301, ERR_POS_REG1 0x00000847,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x0001629d                                     (sector offset in chip is 0x0001629d),                                      NFECC_STATUS2_REG value 0x00000001, ERR_POS_REG1 0x00000732,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x000162d4                                     (sector offset in chip is 0x000162d4),                                      NFECC_STATUS2_REG value 0x00000601, ERR_POS_REG1 0x0000045a,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x000166f9                                     (sector offset in chip is 0x000166f9),                                      NFECC_STATUS2_REG value 0x00000001, ERR_POS_REG1 0x00000180,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x0001308c                                     (sector offset in chip is 0x0001308c),                                      NFECC_STATUS2_REG value 0x00000601, ERR_POS_REG1 0x00000ba1,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x00011668                                     (sector offset in chip is 0x0001166) ,                                      NFECC_STATUS2_REG value 0x00000401, ERR_POS_REG1 0x00000ec3,ERR_POS_REG2 0x00000000
BCH_ReadSector: Data ECC  error: startSectorAddr=0x00010dbd                                     (sector offset in chip is 0x00010dbd),                                      NFECC_STATUS2_REG value 0x00000401, ERR_POS_REG1 0x00000714,ERR_POS_REG2 0x00000000
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 1
BCH_ReadSector:Spare ECC  error: startSectorAddr=0x00013fe5                                (sector offset in chip is 0x00013fe5), NFECC_STATUS2_REG value 0x00000801, ERR_POS_REG1 0x00000006,                                ERR_POS_REG2 0x00000000
FMD_GetInfo
FMD_GetIVT8500DBGMSG: yuzhiwang OSTimer Interrupt 2
nfo
[VT8500] Driver for FEV version: 0.1, Aug 22 2009, 13:29:01[FEV] Driver for VT8500 version: 0.9, Aug 22 2009, 13:29:01[AC97] GpioMask = 0x00000010
***********m_usInputSource = 404 
[PWB] Driver for VT8500 version: 0.9, Sep  8 2009, 10:21:59
Wait for Power Button down....
Backlight Driver Init... Version: 1.04 Board Name: VT8500_Benign
backlight.bltparam.BLTRange.Max = 116
backlight.bltparam.BLTRange.Min = 32
backlight.bltparam.StepLength = 7
backlight.bltparam.period = 127
backlight.bltparam.scalar = 399
backlight.hall = 0
hall.interrupt = 27
No event option set. Will start loading after delay
NDIS.ethernet.ic = 1
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 3
ERROR: OALIoCtlHalGetDeviceInfo: Device doesn't support IOCTL_HAL_GET_DEVICE_INFO::SPI_GETUUID
OALIoCtlShowBootInformation: HWPropList: NoBootInformation
BCH_ReadSector8ata ECC  error: startSectorAddr=0x0000a625                                     (sector offset in chip is 0x0000a625),                                      NFECC_STATUS2_REG value 0x00000601, ERR_POS_REG1 0x000005f4,ERR_POS_REG2 0x00000000
LayMgr.cpp: Layout Manager successfully initialized to  1
ERROR: OALIntrReleaseSysIntr: Invalid sysIntr value 0
ERROR: OALIntrReleaseSysIntr: Invalid sysIntr value 0
[VT8500] Touch Panel No Exist!
Maximum Allowed Error 5:
Time to load the driver
FMD_Init for board: VT8500_Benign
OALIoCtlShowBootProgress: HWPropList: NoBootProgressBar
FMD!DumpRegKey> Drivers\BuiltIn\AsyncBus\NFlash2 
        Order = 000000FF
        Profile = MSFlash2
        IClass :
            {A4E7EDDA-E575-4252-9D6B-4195D48BB865}
        FriendlyName = VIA NAND FLASH Driver (Flash Disk)
        Dll = flashmdd.dll
        FlashPddDll = via_flashpdd_600_2.dll
        Prefix = DSK
        BoundaryLeftMB = 00000180
        BoundaryRightMB = FFFFFFFF
OALIoCtlShowBootInformation: HWPropList: NoBootInformation
FMD_Init: g_hNandMutex = 0x059d000f, 183
FMD:NAND_WAIT_READY: B2R Status not ready!!
FMD_Init: nand_reset chip 0 OK!
ReadFlashID
FMD_Init: Flash ID is ec d5 14 b6 74
initChipInfo Product ID=SAMSUNG_NF_K9GAG08U0M
Clock=00000000 r/w cycle=12122424
IsBadBlockTBLExisted(block 0x00000fff):Linux Main BBT found:  Bbt0
FMD:Scan_NandFlash: Found Wince TBL pattern=42627430
IsBadBlockTBLExisted(block 0x00000ffe):Linux Mirror BBT found:  1tbB
FMD:Scan_NandFlash: Found Wince TBL pattern=31746242
LoadNandFlashTBL: Use TBL0
GetBadBlockNum: block 0x43c in chip 0 is bad block
GetBadBlockNum: block 0x43d in chip 0 is bad block
LoadNandFlashTBL: Bad Block Num=2
FMD_Init: BoundaryRight auto set to 2044MB
FMD_Init: (Left ~ Right) / Total = (384MB ~ 2044MB) / 2048MB !
FMD_Init done: Flash Disk.
FMD_GetInfo
FMD_GetInfo
BCH_ReadSector: Data ECC  error: startSectorAddr=0x00018429                                     (sector offset in chip is 0x00018429),                                      NFECC_STATUS2_REG value 0x00000401, ERR_POS_REG1 0x00000ef4,ERR_POS_REG2 0x00000000
FMD_GetInfo
FMD_GetInfo
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 4
Explorer(V2.0) taskbar thread started.
NDISPWR:: Found adapter [FETCE6B1]
MID Assistant. Version 0.6. 
 LoadSetting: g_dBrightness is 0x5aMID Assistant. Version 0.6. 
 Before OnInitBacklightDialog: g_dBrightness 0x5a
After OnInitBacklightDialog: g_dBrightness 0x5a
OALIoCtlGetKernelVersion
Kernel Version: 1.33
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 5
VT8500DBGMSG: yuzhiwang OSTimer Interrupt 6[/COLOR][/B]
[/COLOR]

---

### Post by celem on 2009-12-29
dwinston91, How did you open it. I tried last night and the screen prevented me from fully removing the keyboard plate and it looked like it needed to be removed before I could release the screen (catch 22). I have attached photos of my partial disassembly.

---

### Post by dwinston91 on 2009-12-30
Celem,  you see those thin paper like connectors(It is made of plastic, but feels really thin)?  You have to carefully remove those from their connections.  There are two of them.  One in the front that is right above your pinky finger on the left. (I removed it from the top..just slide it out and you'll see a blue tab connector..the wire is about 1/4 inch wide).  And then there is the one in the back..I slid this one out  from the bottom.  Once you get it out..mine had a green plastic connector on it.  This should allow you to open the top up freely.

---

### Post by dwinston91 on 2009-12-30
Also, you have to remove the white and black wiring connected in the back, near the screen.  Once you do that, you'll have to remove 4 screws, that connect the screen to the bottom half.  In your picture, two of the screws are just to the right of your thumb, connected to a metal plate.  There are also two more screws like that on the other side.  I found that I didn't need to disconnect the wire on the other side.  I just left it connected.

---

### Post by dwinston91 on 2009-12-30
I am actually in the process of removing it again, because I believe the wider thin connector (with the green tip) is not fully connected, because my space bar, delete key, and arrow keys don't work.  Although all the other keys work fine.  So when you put it back together, be careful to connect that wiring in the back...which I found to be really tricky getting it back in there.

---

### Post by sleeky24 on 2009-12-30
I was just reading through the manual for the cnm book and it says you can sync their device with your windows desktop pc using the rear usb connector and the relevant software from MS has anybody tried this? It then allows you to browse through all the files on the unit.
 
Obviously I don't think this would be possible with a linux machine unless there is some third party software available?
 
Lee.

---

### Post by Dr_Narvi on 2009-12-30
Hello 

 In the files I left to you there is completly all system configuration of ours computers and I think that Its nice way to discover if we can change operative system.  I included mailbox (allow mail POP3..) and you tube player (that allow see youtube videos throught TMCP and works fine) also I installed flash player 7 for PPC and works fine directly on IE but its so slowly.  


PD: Perchristensen, with this method I used you can restore your netbook sure

Regards

---

### Post by celem on 2009-12-30
Hmmm - dwinston91, I did remove the thin cable in the front and didn't bother with the rear cable because it still had slack and didn't seem to be what was holding the keyboard plate in. It seemed to be retained by the screen (drawing attached). I pulled and tugged as hard as I dared and it wouldn't budge from where the gap between the screen and the keyboard plate seemed to too small to permit the keyboard plate to rise sufficiently for removal. I know that you removed yours, so it obviously can be done. I have attached photos of my screen hinge area. Does yours have a larger gap?

By the way, your photo shows how easy it is for the manufacturer to offer different System on a Chip (SOC) varieties, i.e., ARM or MIPS, etc., since the entire system appears to be on the green daughterboard and the blue motherboard, I suspect, only contains logic for the keyboard, screen and I/O.

---

### Post by dwinston91 on 2009-12-30
Did you unhook the plastic piece that hooks around the hinge?  That piece, just to  the left of your drawn white arrow, unhooks from the metal hinge under it.  It seems tight at first, but I opened the screen all the way back, and was able to unhook both pieces on the left and right side.  Also, did you unscrew the four screws I mentioned earlier?

---

### Post by dwinston91 on 2009-12-30
I may also be slowing up a bit, since I got an idea to use my machine and connect to one of my Windows XP Pro machines at home through Remote Desktop.  I used a modified version of the termsrv.dll to allow multiple users to connect through Remote Desktop.  That way one person can be on the actual machine and another person can use the mini notebook to remote into the desktop with a different user.  That way both my children can connect online at the same time with the different machines.  

Here is the directions I used (for those interested in using your machine this way):

[http://alonbilu.wordpress.com/2008/05/17/enabling-multiple-concurrent-remote-sessions-on-windows-xp-sp3-patched-file-included/](http://alonbilu.wordpress.com/2008/05/17/enabling-multiple-concurrent-remote-sessions-on-windows-xp-sp3-patched-file-included/)

Also, using it this way is fast..depending on the speed of your desktop machine.  With all the capabilities of the desktop machine.

---

### Post by celem on 2009-12-30
I'm not sure what you mean by "unhook". If there was a catch, like by the mousepad. I seem to have missed it. Anyway, further attacks on my unit will have to wait until mid-January. Effective Saturday, I will be away until late-January, without Internet access.

I have no functioning Windows machines. There is an XP box in the closet but I don't use it. I have considered putting an RDP client on my ARM laptop, and briefly looked for a compatible client but didn't easily come up with one. Actually, I have poor success in finding compatible programs. I found a couple but most of the programs that I find that say that they are ARM & CE fail. My box has WINCE6 loaded. They also have some German software loaded that can read/write MicroSoft Word, Excel and PowerPoint. This software is "for profit" and I am suspect of the Chinese actually having a distribution license for it.

---

### Post by dwinston91 on 2009-12-30
celem, it looks like you have the same board as I do.  If so, you probably have the same apps in the Windows folder.  Check for a program called cetsc.exe.  It is the RDP client app that lets you connect to a desktop that has Remote Desktop setup on it.  I found this program when I was looking for apps that was on the machine in the Windows folder.

Also, when I decide to go back inside of my machine,  I will try to video it and show how I got into it.

---

### Post by PerChristensen on 2009-12-30
Celem,perhaps dwinston91`s utility is sufficient to give us what needed of information - my guess is our books are all compatible. 
dwinston91,I do not hope you felt offended by my last reply.I misunderstood something and ment we must not start exploring MIPS and other processor familys in celems thread. 
Dr_Narvi - thank you.I`m sure it will work for me.
And sleeky24,If you connect your way perhaps MP4 player tools like FRM Pro 1.2.0.1 and ISP_V5.2 (both in english) will work as Sunplus players with 3052a chip and some Anyka MP4players are based on the same Samsung arm926EJ-S processor as our microcomputer.

---

### Post by dwinston91 on 2009-12-30
PerChristensen, I wasn't offended at all.  I didn't see anything to be offended about.  Even after going back and looking at your reply.  It is all good.  Anyway, I've found a lot of neat programs, while perusing through the Windows folder on my device.  Another one, I found was the Remote Control program that will allow you to use the device as a IR Remote Control.  Very interesting stuff in the Windows folder.

---

### Post by celem on 2009-12-30
Interesting - I do have cetsc.exe. I wonder why they didn't put a link for this useful program into the menu.

---

### Post by dwinston91 on 2009-12-30
These links may be of some assistance.  It deals with the iPAQ 3600 which uses an ARM processor and has Windows CE on it.  The links talk about how to install Linux while you have Windows CE on the system.

**iPAQ dualboot (PocketPC and Linux) **
[http://web.archive.org/web/20041220151520/http://www.iptel-now.de/HOWTO/IPAQ_DUALBOOT/ipaq_dualboot.html](http://web.archive.org/web/20041220151520/http://www.iptel-now.de/HOWTO/IPAQ_DUALBOOT/ipaq_dualboot.html)

[B]
Installing Linux on the Compaq iPAQ with Windows CE[/B]
[http://embedded.centurysoftware.com/docs/nx/iPAQ-linux-new-install.html](http://embedded.centurysoftware.com/docs/nx/iPAQ-linux-new-install.html)

---

### Post by celem on 2009-12-30
Well, my system is semi-bricked! I wasn't even doing anything unusual. I updated the address.lst file on my desktop, put it onto a USB flash stick, plugged it into the USB slot in the rear of the right side, opened up the Windows Explorer, navigated to the USB flash stick to verify that the file could be seen, which it did, then when I clicked up-folder to navigate to WINDOWS, I noticed that all of the files had strange names that looked like parts of a text file. The system was destroyed. 

I can reboot but the only thing there is the core WINCE6 system. Everything else is missing, I cannot even do a RUN->CMD because CMD is gone.

Looks like I will be a early adopter to try installing Linux as the box is pretty useless now for just about anything.

---

### Post by dwinston91 on 2009-12-31
Wow...Sorry to hear that, celem.

---

### Post by Dr_Narvi on 2009-12-31
Dont worry Celem you can restore alll operative system as i explained, I have all files of the software that we have ( I got directly of the manufacturer) Its very easy restore!

 Regards

---

### Post by celem on 2009-12-31
> **Dr_Narvi said:**
> ...I have the solution!!!  To restore the system with the factory settings only follow these steps:...

I tried Dr Narvi's solution in post 36 and now it is worse. The "script" did reload Windows but when I boot everything looks good until the final icon is painted on the desktop, then the screen goes blank. The system is on but with a blanked screen. Apparently the files in the file referenced by Dr Narvi are not fully compatible with my machine.

---

### Post by dwinston91 on 2009-12-31
celem, it looks like you have the same board as mine.  I will try to zip up all my files and see if I can post them.

---

### Post by celem on 2009-12-31
That would be much appreciated. Dr Narvi's SCRIPT is interesting. If I don't do the required reboot, the screen does not blank and I can look around at a lot of interesting stuff that was not in my original load. If I get the box working again I may lift some things from Dr Narvi's load. The sound does not work with this load, so that is another incompatibility.

Rebooting populates the desktop, brings up an hourglass and then permanently blanks the screen.

---

### Post by xaviergo on 2010-01-01
I have one of the last Windows CE computers. This appeared to be a CNM Lifestyle product which web page is hosted at: [http://www.cnmlifestyle.com](http://www.cnmlifestyle.com); go to CNM Silver MBook - 7" in product menu then go in the download section, and after that "system backup/restore".
 
They explain how to restore the windows CE operating system with an active sync cable.
 
Two versions of this product exists: the windows CE one, with an ARM, and the linux one, difficult to find, base on a MIPS processor. As peole say, the linux system is more powerfull. I thik this is mostly because of less RAM needed.
 
No I would also like to get in work on the ARM.
 
When I boot my system, I get a essage "Press F1 key to update system"; but then it asks for a password that I don't know; indead I should ask CNM LifeStyle.
 
Regards,
 
Xavier

---

### Post by celem on 2010-01-01
> **xaviergo said:**
> ...CNM Lifestyle product...They explain how to restore the windows CE operating system with an active sync cable...

I use a 100% Linux environment and can't use their ActiveSync procedure. Additionally, their system is wince5 and my system is wince6. Since Wince has to be present and functional enough to run ActiveSync, I would be mixing wince5 and wince6 files, which would probably end in failure.

The wince6 upgrade script procedure referenced in post 36 by Dr Navi also requires that wince be minimally functional but is accomplished totally within the wince machine. It is easy and works - it just isn't an exact match for my hardware, which appears to made by benigntech as referenced by dwinston91 in post 34. Dwinston91's model number BV07-8500 hardware and mine appear to be identical, with a SOC daughter-board that is soldered to the motherboard. The system owned by PerChristensen appears very similar except that his system's SOC daughter-board inserts into what appears to be a MiniPCI that is on the motherboard. It seems that the case, keyboard, screen, etc., is mostly identical on these systems and probably from the same source, but there are several variations of motherboards, from multiple system integrators.

I think that my best result will come from getting a ZIP file of the files on dwinston91's system and overlaying those files onto Dr Navi's script, which will permit an easy installation. AND if that fails and the system remains as it is, it will motivate me to start earlier with risky attempts to load Linux.

Nonetheless, thank you for your suggestion.

By the way, have you tried the password anyka, as instructed by cnmlifestyle.com's upgrade instructions?

---

### Post by shade_emry on 2010-01-01
OK everyone, i have been following this thread with great intrest, and i've decided to divulge how to unbrick the semi-bricked machines, below is the instructions...
 
NOTE:: this will recover the netbooks that have no boot screen what so ever, apprently the wat the arm processor is set up, their is a built in pieace of code that always cehcks the sd card for boot, so if your gona create a boot device, u need to look at the script as it tells the arm processor how to behave since it lacks a "bios" or like what we are used to. 
 
you can download the program and update it. the netbook will work. This is the update program link: 
[http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
[http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
Please make sure if your netbook CPU is the version of WM8505 or VT8500. 
If your CPU is WM8505, Please download the [http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
 
if your CPU is VT8500. Please download the [http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
If you are not sure. You can download VT8505Software.rar . if the software update failed , you can download other software to try.
 
After you get the software, you need to find a SD card &#65288;memory card or USB memory &#65289;which is more then 512M to copy the software to setup the software.
Please do as follows:
1. Please decompressing files , open the VT8500 or VT8505 folder. Then copy the directory &#8220;script&#8221; to your SD card. 
(Very important, you only need copy the script folder to your SD card. don't include the VT8500 or VT8505 folder.)
2. Turn off your netbook, 
3. Insert the SD card to your netbook.
4. Turn on your netbook. Then the software will setup to your netbook Automatically. Usually it will take several minutes completed setup.
5. After completed setup. It will show a windows call your turn off the netbook. Then turn off it.
6. Put the SD card out of the netbook.
7. Then turn on the netbook and all should be OK.
 
 
I hope this helps, now remember if you wan to do a "u-Disc boot" the arm processor is set up to look (or in most cases) to the back of the notebook for a boot device.
 
Now if someone could be nice enough to copy these files somewhere, like megaupload or rapid share, that would be amazing, i got the feeling these programs will not be at the said links for to long.
 
Also, you can modify the script to install almost any flavor of linux or android that is compatible with ARM processor tech. i don't know exactly how this is done, but my buddy is buying these laptops off of ebay, loading them with the said os'es and selling them locally, ill ask him if he can divulge how he does it.

---

### Post by celem on 2010-01-01
> **shade_emry said:**
> ...i've decided to divulge how to unbrick the semi-bricked machines...
Thank you for offering to help. In my case, it does not work. Your VT8500 script appears to be identical to that of Dr Navi and behaves the same, namely, the "script" reloads wince but when I boot everything looks good until the final icon is painted on the desktop, then the screen goes blank and the system remains on. Thus your provided script isn't compatible with benigntech's model number BV07-8500 hardware that dwinston91 and I have. The VT8505 script will not load. Nonetheless, thank you for posting it. Maybe your buddy has an inside track to the files for a BV07-8500 hardware machine?

> **shade_emry said:**
> ...remember if you wan to do a "u-Disc boot" the arm processor is set up to look (or in most cases) to the back of the notebook for a boot device..
Are you saying that if I insert into the USB slot located on the rear of the machine a bootable ARM Linux on a USB-Flash stick, that it will boot?

> **shade_emry said:**
> ...Also, you can modify the script to install almost any flavor of linux or android that is compatible with ARM processor tech. i don't know exactly how this is done, but my buddy is buying these laptops off of ebay, loading them with the said os'es and selling them locally, ill ask him if he can divulge how he does it.
Now we would all LOVE it if you can pass that information along. Anything would be helpful.

Thank you for jumping into this discussion.

---

### Post by celem on 2010-01-01
I will be away for 2+ weeks, starting tomorrow morning, so don't think that my lack of response is a lack of interest. I'll catch up when I return.

celem

---

### Post by shade_emry on 2010-01-01
Well looks like i learned how to flash these netbooks.
 
It also looks like as shown here, that the script allows writting to the nand directly as shown below..so this is extracted from file scriptcmd from the files posted in the above post, keep in mind this executed on my netbook that was completley bricked, so the netbook indeffinetly looks to the sd card before anything boots. the scriptcmd file can be opened with notepad or nano, whatever your prefrence is.
 
in this case mmc 0, is the sd card .
 
textout 60 250 "2. Upgrading normal mode ..." ffff00
fatload mmc 0 FFFF8 script/normal_nk.nb0
nand writeblob FFFF8 0 ${filesize}
textout 60 280 "......Upgrade normal mode successful!" 00ff00
 
if we note, it allows a direct write to the nand...
 
So taken this all in effect, we have learned how to write to the nand and flash it now, we learned what boot device is first in line. now come creating an android .bin or .nb0 . Seeing that android or even a small handfull of linux distros are out that are coded around the arm processor, we can take these apart and learn how their created. now, anyone know any good links or do i need to learn some more chinese ;)

---

### Post by shade_emry on 2010-01-01
I would assume so, just got off the phone with my buddy, apprently theirs another file availble that he'll have to dig up for your board, sorry about notposting tha one, i'll have him find it if he can.
 
as for the usb, try makeing a bootable sd card, he said something about that as well.

---

### Post by shade_emry on 2010-01-01
celem try double flashing it, i had to do that to get it to work, install it, then do it again, then allow it to boot up put the memory card in it and it should ask if you want to format the flash dsk. the flash disk being the netboks disk.  after that reboot and all should be normal. if not, then we can always hope my bud finds that other file.

---

### Post by celem on 2010-01-01
> **shade_emry said:**
> ..try double flashing it... then allow it to boot up put the memory card in it and it should ask if you want to format the flash dsk. the flash disk being the netboks disk.  after that reboot and all should be normal....

No joy! I did the script load twice, each indicating successful loads, then rebooted with the SD card in a third time but canceled the file load, then rebooted. Same as before. I feel that the load works correctly and my problem is simply hardware incompatibility. I have no sound and something is different in the screen blanking. The SMART BOOK logo when booting is also different - the original load displayed, as I recall, a Windows screen but no brand name - I assume that SMART BOOK is some sort of brand name.

---

### Post by xaviergo on 2010-01-01
Just for your information, on the msdn you can find some information on how to build a windows ce environnement from scratch. Choosing the right processor, etc... But I think that some stuff are brand specific.
 
As far as I am concerned, I have an ARM920 processor, so I don't think the script file will help. The via is a 400 MHz one while the ARM920 is at 266 Mhz.
 
What I found interresting is the "ARM info center" website. There is stuff about the "ARM Firmware Suite", I wonder if the program that asks me to press F1 is part of this software suite.
 
I will be able to give you the password when I get an aswer from the chinese compagny.

---

### Post by celem on 2010-01-01
> **shade_emry said:**
> ...this is extracted from file scriptcmd from the files posted in the above post,...

The scriptcmd file contains some binary data at the start. I am unable to open with a text editor. I can open it with OpenOffice but the saved file will not boot the machine, so OpenOffice altered it in some incompatible way.

I noticed that there was a setenv command after the binary data and wondered if it was needed but not being executed because a new-line didn't preceed it. So, I used a hex-editor and changed the binary 01 preceeding the setenv to a 0A. The boot was no longer recognized, thus the binary data is important. shade_emry, did you successfully edit the scriptcmd file? If so, how did you deal with the leading binary data?

'##V{w&#65533;&#65533;J&#65533;&#65533;S###
########&#65533;_L&#65533;####Script Created by Win32#################setenv lcdparam           1,30000,5,800,480,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000,D811003c|0x2,D811005c&~0x2
setenv board_name         VT8500_PuZhi
setenv TouchIC            0
setenv NoBootProgressBar  0
setenv NoBootInformation  0
setenv battvoltlist       6774,6889,7377,7498,7538,7599,7650,7698,7763,7821,7939
...

---

### Post by shade_emry on 2010-01-01
the screen blinking or blanking is a symptom i had, i fixed it by unplugging the lcd cable to the main board and back in, the no sound i beleve looks to be a problem with the driver that was included with this program, and the smartbook logo is something im unsure about, anyway, ill see if i can talk jacob to posting here, he did something with the script file and built a bianry image containing android more info later!

---

### Post by celem on 2010-01-01
Here is an interesting site:
[http://www.denx.de/wiki/view/DULG/Introduction#Section_2.3.]("http://www.denx.de/wiki/view/DULG/Introduction#Section_2.3.")

This document describes how to use the firmware U-Boot and the operating system Linux in Embedded Power Architecture®, ARM and MIPS Systems.

---

### Post by dwinston91 on 2010-01-01
> **shade_emry said:**
> OK everyone, i have been following this thread with great intrest, and i've decided to divulge how to unbrick the semi-bricked machines, below is the instructions...
 
NOTE:: this will recover the netbooks that have no boot screen what so ever, apprently the wat the arm processor is set up, their is a built in pieace of code that always cehcks the sd card for boot, so if your gona create a boot device, u need to look at the script as it tells the arm processor how to behave since it lacks a "bios" or like what we are used to. 
 
you can download the program and update it. the netbook will work. This is the update program link: 
[http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
[http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
Please make sure if your netbook CPU is the version of WM8505 or VT8500. 
If your CPU is WM8505, Please download the [http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
 
if your CPU is VT8500. Please download the [http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
If you are not sure. You can download VT8505Software.rar . if the software update failed , you can download other software to try.
 
After you get the software, you need to find a SD card &#65288;memory card or USB memory &#65289;which is more then 512M to copy the software to setup the software.
Please do as follows:
1. Please decompressing files , open the VT8500 or VT8505 folder. Then copy the directory “script” to your SD card. 
(Very important, you only need copy the script folder to your SD card. don't include the VT8500 or VT8505 folder.)
2. Turn off your netbook, 
3. Insert the SD card to your netbook.
4. Turn on your netbook. Then the software will setup to your netbook Automatically. Usually it will take several minutes completed setup.
5. After completed setup. It will show a windows call your turn off the netbook. Then turn off it.
6. Put the SD card out of the netbook.
7. Then turn on the netbook and all should be OK.
 
 
I hope this helps, now remember if you wan to do a "u-Disc boot" the arm processor is set up to look (or in most cases) to the back of the notebook for a boot device.
 
Now if someone could be nice enough to copy these files somewhere, like megaupload or rapid share, that would be amazing, i got the feeling these programs will not be at the said links for to long.
 
Also, you can modify the script to install almost any flavor of linux or android that is compatible with ARM processor tech. i don't know exactly how this is done, but my buddy is buying these laptops off of ebay, loading them with the said os'es and selling them locally, ill ask him if he can divulge how he does it.

So it must be an SD card?  Can it be a USB Flash Drive?

---

### Post by dwinston91 on 2010-01-01
celem, I zipped up the folders under My Computer on my machine.  It can be downloaded from here: [http://rapidshare.com/files/329051287/wince_bak.zip.html]("http://rapidshare.com/files/329051287/wince_bak.zip.html")

---

### Post by shade_emry on 2010-01-02
it seems to only like an sd card, correct me if im wrong but thats how jacob here boots all of his stuff onto the flash.

---

### Post by ZCarowick on 2010-01-05
If i've missed something i apologize, but for the majority of you the BIOS password on the netbook should be "ZTK". Caps only as far as i'm aware.

*mostly in response to xaviergo

---

### Post by dwinston91 on 2010-01-05
Then the question would be, for ZCarowick, how would you even bring up a BIOS screen? ie, what keys/key do you press to bring up a BIOS. I haven't found anything on a BIOS for our boards. Some of our boards are by different manufacturers too.

---

### Post by ZCarowick on 2010-01-05
well dwinston91, I'm afraid this information applies only to those of us with the netbook with the type of processor xiavergo is calling arm920. In the case of that netbook, upon booting it says "Press F1 to update" and prompts you to "input password", and "ZTK" suffices to get to a screen which gives the options: 

Format NAND disk, Format XIP disk, Format Flash2 Disk, Update XIP, Update Eboot, and Reboot along with exit.

---

### Post by PerChristensen on 2010-01-05
Reinstalled Windows CE6 on my hanged SmartBook succesfully (with sound and WiFi) via SD card thanks to suggestions by Dr_Narvi and shade_emry :popcorn:.

---

### Post by dwinston91 on 2010-01-05
> **PerChristensen said:**
> Reinstalled Windows CE6 on my hanged SmartBook succesfully (with sound and WiFi) via SD card thanks to suggestions by Dr_Narvi and shade_emry :popcorn:.
 
Congratulations PerChristensen.  I am now trying to figure out how  to run a LiveCD type installation of Linux/Ubuntu from an SD card.

---

### Post by shade_emry on 2010-01-06
my wifi app doesnt seem to load period now, now i gota find the build program, or does anyone know how to make it function correctly?

---

### Post by dwinston91 on 2010-01-06
shade_emry, do you mean the program is not there or that it's just not working correctly?  If it isn't working correctly, maybe you can get a copy of the WiFi app.  I believe a copy is in the zip files I placed on RapidShare, in message #73 above.

---

### Post by dwinston91 on 2010-01-06
> **shade_emry said:**
> OK everyone, i have been following this thread with great intrest, and i've decided to divulge how to unbrick the semi-bricked machines, below is the instructions...
 
NOTE:: this will recover the netbooks that have no boot screen what so ever, apprently the wat the arm processor is set up, their is a built in pieace of code that always cehcks the sd card for boot, so if your gona create a boot device, u need to look at the script as it tells the arm processor how to behave since it lacks a "bios" or like what we are used to. 
 
you can download the program and update it. the netbook will work. This is the update program link: 
[http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
[http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
Please make sure if your netbook CPU is the version of WM8505 or VT8500. 
If your CPU is WM8505, Please download the [http://zeng.h1.28823.cn/VT8505Software.rar](http://zeng.h1.28823.cn/VT8505Software.rar)
 
if your CPU is VT8500. Please download the [http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)
 
If you are not sure. You can download VT8505Software.rar . if the software update failed , you can download other software to try.
 
After you get the software, you need to find a SD card &#65288;memory card or USB memory &#65289;which is more then 512M to copy the software to setup the software.
Please do as follows:
1. Please decompressing files , open the VT8500 or VT8505 folder. Then copy the directory “script” to your SD card. 
(Very important, you only need copy the script folder to your SD card. don't include the VT8500 or VT8505 folder.)
2. Turn off your netbook, 
3. Insert the SD card to your netbook.
4. Turn on your netbook. Then the software will setup to your netbook Automatically. Usually it will take several minutes completed setup.
5. After completed setup. It will show a windows call your turn off the netbook. Then turn off it.
6. Put the SD card out of the netbook.
7. Then turn on the netbook and all should be OK.
 
 
I hope this helps, now remember if you wan to do a "u-Disc boot" the arm processor is set up to look (or in most cases) to the back of the notebook for a boot device.
 
Now if someone could be nice enough to copy these files somewhere, like megaupload or rapid share, that would be amazing, i got the feeling these programs will not be at the said links for to long.
 
Also, you can modify the script to install almost any flavor of linux or android that is compatible with ARM processor tech. i don't know exactly how this is done, but my buddy is buying these laptops off of ebay, loading them with the said os'es and selling them locally, ill ask him if he can divulge how he does it.

Do we know what app created the scriptcmd?  I ask because it looks like it has some binary code in the beginning and I was wondering what created it?  Is it something that can be read by a particular application?

---

### Post by shade_emry on 2010-01-06
> **dwinston91 said:**
> shade_emry, do you mean the program is not there or that it's just not working correctly? If it isn't working correctly, maybe you can get a copy of the WiFi app. I believe a copy is in the zip files I placed on RapidShare, in message #73 above.
 
 
the amount of times it can be dwnloaded has been exceded, can you upload it to megaupload or something?

---

### Post by shade_emry on 2010-01-06
> **dwinston91 said:**
> Do we know what app created the scriptcmd? I ask because it looks like it has some binary code in the beginning and I was wondering what created it? Is it something that can be read by a particular application?
 
 
that binary code i beleve is used by the arm to identify and execute a certain mode, i think i had the utility to build it somewhere, ill see if i can find it.

---

### Post by dwinston91 on 2010-01-06
> **shade_emry said:**
> the amount of times it can be dwnloaded has been exceded, can you upload it to megaupload or something?

I'll have to upload it later..Access is blocked where I am right now (at work).

---

### Post by nextvolume on 2010-01-06
Hello, I have an Alpie Technologie Easypc E700 Wince series 7'' Notebook. It's like your machines. It came with (partly) Italian Windows CE 6.0 which I lost.

You have been very helpful to me, this is like the only place I found on the internet where people are talking about this subject.
That said, the files in VT8500Software.rar worked successfully for me and I've "unbricked" my laptop about three times as of now.

Unluckily the internal mouse and keyboard aren't working because probably I broke a fuse on the motherboard for them while I was trying to fit the keyboard cable back in, USB mouse and keyboard work fine, though.

"scriptcmd" is simply an U-Boot script image, you can do that with the mkimage tool. Our notebooks use a modified version of U-Boot with some non-standard commands (cleanlcd, textout, sdwaitins). Most commands work, like mw (which does memory writes). I was even able to write small images converted to script on the framebuffer with a program I wrote, and they displayed on the screen fine, directly from U-Boot.
I wasn't able to redirect the U-Boot output and input, though. Maybe I have to do saveenv and reboot? I'm afraid to brick my notebook if I do that :/

About running Linux on this machine, I got the Linux kernel for the YF-700 to boot, by remaining only the parts of the script where it loads the kernel and the ramdisk on the flash and where it sets bootcmd and bootargs, and by playing with lcdparam, I changed the 800 and 480 in that variable to 1024 and 768, so I get a cut 1024x768 image on the screen, but the output doesn't appear as garbage and it is fully readable font. Remember to do saveenv as it won't change resolution with lcdinit! It hangs at "irq3: nobody cared" and in (function?) via_ata_interrupt, because this machine doesn't have a SATA controller unlike the YF-700 thin client (based around the VIA VT8500 as well). There are no sources for this kernel, even if Linux is GPL. I contacted Kaser Corp. (the makers of the YF-700) for the sources yesterday, but I've not received any answer yet. If we could recompile the kernel, we would have our nice Linux...

I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.

You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

                                         [Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox

                         


Here is my directory on my webspace about this notebook: [http://tails92.sepwich.com/files/easypc](http://tails92.sepwich.com/files/easypc)

notes.txt contains my note about the machine. There are also VT8500Software.rar, VT8505Software.rar, and dwinston91's wince_bak.zip.

linux_scriptcmd is the script you have to replace scriptcmd with to use the files in busybox-kernel-1.17.1.rar which you can find in the directory of Kaser I told you about.
linux_scriptcmd also sets up the resolution to 1024x768.
There's no risk of bricking of your notebook as Windows CE in VT8500Software.rar will restore just fine - and will restore the screen resolution as well.

P.S: To be clearer, the resolution of the LCD is actually 800x480. We apparently get the video card to output 1024x768 and the screen only displays the first horizontal 800 pixels and the first vertical 480 pixels.

-nextvolume

---

### Post by shade_emry on 2010-01-06
Bravo!
 
we are that much closer! 
 
Anyway, can you post pictures of the guts of yours and how you installed the mouse/keyboard? and a close up image of the ribbon cable, its possible you rubbed off the conductive part of the cable, if you did this, take a number 2 pencil and make a fine trace on the ribbon cable (using a ruler as a staight edge) where the the conductive traces use to be, its very possible you made a small hair crack in the traces where you removed the cable, and its breaking the trace, seeing as how the pencil is conductive it may work, gods only know i've had to do this a bunch before with keyboards that had spilled coke in em :)

---

### Post by shade_emry on 2010-01-06
> **nextvolume said:**
> Hello, I have an Alpie Technologie Easypc E700 Wince series 7'' Notebook. It's like your machines. It came with (partly) Italian Windows CE 6.0 which I lost.
 
You have been very helpful to me, this is like the only place I found on the internet where people are talking about this subject.
That said, the files in VT8500Software.rar worked successfully for me and I've "unbricked" my laptop about three times as of now.
 
Unluckily the internal mouse and keyboard aren't working because probably I broke a fuse on the motherboard for them while I was trying to fit the keyboard cable back in, USB mouse and keyboard work fine, though.
 
"scriptcmd" is simply an U-Boot script image, you can do that with the mkimage tool. Our notebooks use a modified version of U-Boot with some non-standard commands (cleanlcd, textout, sdwaitins). Most commands work, like mw (which does memory writes). I was even able to write small images converted to script on the framebuffer with a program I wrote, and they displayed on the screen fine, directly from U-Boot.
I wasn't able to redirect the U-Boot output and input, though. Maybe I have to do saveenv and reboot? I'm afraid to brick my notebook if I do that :/
 
About running Linux on this machine, I got the Linux kernel for the YF-700 to boot, by remaining only the parts of the script where it loads the kernel and the ramdisk on the flash and where it sets bootcmd and bootargs, and by playing with lcdparam, I changed the 800 and 480 in that variable to 1024 and 768, so I get a cut 1024x768 image on the screen, but the output doesn't appear as garbage and it is fully readable font. Remember to do saveenv as it won't change resolution with lcdinit! It hangs at "irq3: nobody cared" and in (function?) via_ata_interrupt, because this machine doesn't have a SATA controller unlike the YF-700 thin client (based around the VIA VT8500 as well). There are no sources for this kernel, even if Linux is GPL. I contacted Kaser Corp. (the makers of the YF-700) for the sources yesterday, but I've not received any answer yet. If we could recompile the kernel, we would have our nice Linux...
 
I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.
 
You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)
 
[Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox
 
 
 
 
Here is my directory on my webspace about this notebook: [http://tails92.sepwich.com/files/easypc](http://tails92.sepwich.com/files/easypc)
 
notes.txt contains my note about the machine. There are also VT8500Software.rar, VT8505Software.rar, and dwinston91's wince_bak.zip.
 
linux_scriptcmd is the script you have to replace scriptcmd with to use the files in busybox-kernel-1.17.1.rar which you can find in the directory of Kaser I told you about.
linux_scriptcmd also sets up the resolution to 1024x768.
There's no risk of bricking of your notebook as Windows CE in VT8500Software.rar will restore just fine - and will restore the screen resolution as well.
 
P.S: To be clearer, the resolution of the LCD is actually 800x480. We apparently get the video card to output 1024x768 and the screen only displays the first horizontal 800 pixels and the first vertical 480 pixels.
 
-nextvolume
 
THX For providing a working space for the files poseted here!

---

### Post by nextvolume on 2010-01-06
Unluckily I don't have a digital photo camera and I can't take a photo of my board.
I can tell the board's blue and it has the module soldered on it, not removable like PerChristensen's machine.

-nextvolume

---

### Post by shade_emry on 2010-01-06
can you run sereialview under the windows folder on the smartbook and copy paste all the info here?

---

### Post by dwinston91 on 2010-01-06
If the board is blue, it is more than likely like celem and my board..made by Benigntech.  Probably a BV07_A_8500.

---

### Post by dwinston91 on 2010-01-06
> **nextvolume said:**
> Hello, I have an Alpie Technologie Easypc E700 Wince series 7'' Notebook. It's like your machines. It came with (partly) Italian Windows CE 6.0 which I lost.

You have been very helpful to me, this is like the only place I found on the internet where people are talking about this subject.
That said, the files in VT8500Software.rar worked successfully for me and I've "unbricked" my laptop about three times as of now.

Unluckily the internal mouse and keyboard aren't working because probably I broke a fuse on the motherboard for them while I was trying to fit the keyboard cable back in, USB mouse and keyboard work fine, though.

"scriptcmd" is simply an U-Boot script image, you can do that with the mkimage tool. Our notebooks use a modified version of U-Boot with some non-standard commands (cleanlcd, textout, sdwaitins). Most commands work, like mw (which does memory writes). I was even able to write small images converted to script on the framebuffer with a program I wrote, and they displayed on the screen fine, directly from U-Boot.
I wasn't able to redirect the U-Boot output and input, though. Maybe I have to do saveenv and reboot? I'm afraid to brick my notebook if I do that :/

About running Linux on this machine, I got the Linux kernel for the YF-700 to boot, by remaining only the parts of the script where it loads the kernel and the ramdisk on the flash and where it sets bootcmd and bootargs, and by playing with lcdparam, I changed the 800 and 480 in that variable to 1024 and 768, so I get a cut 1024x768 image on the screen, but the output doesn't appear as garbage and it is fully readable font. Remember to do saveenv as it won't change resolution with lcdinit! It hangs at "irq3: nobody cared" and in (function?) via_ata_interrupt, because this machine doesn't have a SATA controller unlike the YF-700 thin client (based around the VIA VT8500 as well). There are no sources for this kernel, even if Linux is GPL. I contacted Kaser Corp. (the makers of the YF-700) for the sources yesterday, but I've not received any answer yet. If we could recompile the kernel, we would have our nice Linux...

I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.

You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

                                         [Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox

                         


Here is my directory on my webspace about this notebook: [http://tails92.sepwich.com/files/easypc](http://tails92.sepwich.com/files/easypc)

notes.txt contains my note about the machine. There are also VT8500Software.rar, VT8505Software.rar, and dwinston91's wince_bak.zip.

linux_scriptcmd is the script you have to replace scriptcmd with to use the files in busybox-kernel-1.17.1.rar which you can find in the directory of Kaser I told you about.
linux_scriptcmd also sets up the resolution to 1024x768.
There's no risk of bricking of your notebook as Windows CE in VT8500Software.rar will restore just fine - and will restore the screen resolution as well.

P.S: To be clearer, the resolution of the LCD is actually 800x480. We apparently get the video card to output 1024x768 and the screen only displays the first horizontal 800 pixels and the first vertical 480 pixels.

-nextvolume

Thanks so much for this information.  This is exactly what we have been looking for.  Especially looking at your notes.  You have a board from Benigntech like in this link:
[http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192](http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192).

Your notes are very helpful.  Now I have to figure out, how to make a LiveCD/LiveSD version so that I can run it from the SD card and still keep Windows CE 6 in tact.

---

### Post by shade_emry on 2010-01-06
> **dwinston91 said:**
> Thanks so much for this information. This is exactly what we have been looking for. Especially looking at your notes. You have a board from Benigntech like in this link:
[http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192](http://www.benigntech.com.cn/en/product.asp?clb=141&slb=192).
 
Your notes are very helpful. Now I have to figure out, how to make a LiveCD/LiveSD version so that I can run it from the SD card and still keep Windows CE 6 in tact.
 
 
Might you be able to post the findings and how to once you get this done bud? also, do you think we can port android over to it? jacob doesn't want to help at all in this because it threatens his bussiness...what a shame someone as good as him cannot help us at all..

---

### Post by shade_emry on 2010-01-06
We need to see the files on a u-boot device some companies are offering..if ebay has one ill see if i can get it and post an image file of that device.

---

### Post by dnharley2591 on 2010-01-06
password for the cnm netbook is ztk

---

### Post by shade_emry on 2010-01-07
> **nextvolume said:**
> Hello, I have an Alpie Technologie Easypc E700 Wince series 7'' Notebook. It's like your machines. It came with (partly) Italian Windows CE 6.0 which I lost.
 
You have been very helpful to me, this is like the only place I found on the internet where people are talking about this subject.
That said, the files in VT8500Software.rar worked successfully for me and I've "unbricked" my laptop about three times as of now.
 
Unluckily the internal mouse and keyboard aren't working because probably I broke a fuse on the motherboard for them while I was trying to fit the keyboard cable back in, USB mouse and keyboard work fine, though.
 
"scriptcmd" is simply an U-Boot script image, you can do that with the mkimage tool. Our notebooks use a modified version of U-Boot with some non-standard commands (cleanlcd, textout, sdwaitins). Most commands work, like mw (which does memory writes). I was even able to write small images converted to script on the framebuffer with a program I wrote, and they displayed on the screen fine, directly from U-Boot.
I wasn't able to redirect the U-Boot output and input, though. Maybe I have to do saveenv and reboot? I'm afraid to brick my notebook if I do that :/
 
About running Linux on this machine, I got the Linux kernel for the YF-700 to boot, by remaining only the parts of the script where it loads the kernel and the ramdisk on the flash and where it sets bootcmd and bootargs, and by playing with lcdparam, I changed the 800 and 480 in that variable to 1024 and 768, so I get a cut 1024x768 image on the screen, but the output doesn't appear as garbage and it is fully readable font. Remember to do saveenv as it won't change resolution with lcdinit! It hangs at "irq3: nobody cared" and in (function?) via_ata_interrupt, because this machine doesn't have a SATA controller unlike the YF-700 thin client (based around the VIA VT8500 as well). There are no sources for this kernel, even if Linux is GPL. I contacted Kaser Corp. (the makers of the YF-700) for the sources yesterday, but I've not received any answer yet. If we could recompile the kernel, we would have our nice Linux...
 
I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.
 
You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)
 
[Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox
 
 
 
 
Here is my directory on my webspace about this notebook: [http://tails92.sepwich.com/files/easypc](http://tails92.sepwich.com/files/easypc)
 
notes.txt contains my note about the machine. There are also VT8500Software.rar, VT8505Software.rar, and dwinston91's wince_bak.zip.
 
linux_scriptcmd is the script you have to replace scriptcmd with to use the files in busybox-kernel-1.17.1.rar which you can find in the directory of Kaser I told you about.
linux_scriptcmd also sets up the resolution to 1024x768.
There's no risk of bricking of your notebook as Windows CE in VT8500Software.rar will restore just fine - and will restore the screen resolution as well.
 
P.S: To be clearer, the resolution of the LCD is actually 800x480. We apparently get the video card to output 1024x768 and the screen only displays the first horizontal 800 pixels and the first vertical 480 pixels.
 
-nextvolume
 
 
also for anyone haveing keyboard/mouse/wifi not starting problems from no where, I found on one of my netbooks as I call em, is that it was due to a bad block in nand (in my case 3) I moved all the hardware to a board with a good nand chip on it and they worked,same exact model. so im assuming this is why it did that, now to see if you have bad blocks, all you have to do is do a clean reboot, goto windows directory, and check a program called seriel view, it'll report the satus of the nand chip if it finds anyting abnormal, however its alot of stuff to read through, its in their somewhere.

---

### Post by dwinston91 on 2010-01-07
> **nextvolume said:**
> Hello, I have an Alpie Technologie Easypc E700 Wince series 7'' Notebook. It's like your machines. It came with (partly) Italian Windows CE 6.0 which I lost.

You have been very helpful to me, this is like the only place I found on the internet where people are talking about this subject.
That said, the files in VT8500Software.rar worked successfully for me and I've "unbricked" my laptop about three times as of now.

Unluckily the internal mouse and keyboard aren't working because probably I broke a fuse on the motherboard for them while I was trying to fit the keyboard cable back in, USB mouse and keyboard work fine, though.

"scriptcmd" is simply an U-Boot script image, you can do that with the mkimage tool. Our notebooks use a modified version of U-Boot with some non-standard commands (cleanlcd, textout, sdwaitins). Most commands work, like mw (which does memory writes). I was even able to write small images converted to script on the framebuffer with a program I wrote, and they displayed on the screen fine, directly from U-Boot.
I wasn't able to redirect the U-Boot output and input, though. Maybe I have to do saveenv and reboot? I'm afraid to brick my notebook if I do that :/

About running Linux on this machine, I got the Linux kernel for the YF-700 to boot, by remaining only the parts of the script where it loads the kernel and the ramdisk on the flash and where it sets bootcmd and bootargs, and by playing with lcdparam, I changed the 800 and 480 in that variable to 1024 and 768, so I get a cut 1024x768 image on the screen, but the output doesn't appear as garbage and it is fully readable font. Remember to do saveenv as it won't change resolution with lcdinit! It hangs at "irq3: nobody cared" and in (function?) via_ata_interrupt, because this machine doesn't have a SATA controller unlike the YF-700 thin client (based around the VIA VT8500 as well). There are no sources for this kernel, even if Linux is GPL. I contacted Kaser Corp. (the makers of the YF-700) for the sources yesterday, but I've not received any answer yet. If we could recompile the kernel, we would have our nice Linux...

I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.

You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

                                         [Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox

                         


Here is my directory on my webspace about this notebook: [http://tails92.sepwich.com/files/easypc](http://tails92.sepwich.com/files/easypc)

notes.txt contains my note about the machine. There are also VT8500Software.rar, VT8505Software.rar, and dwinston91's wince_bak.zip.

linux_scriptcmd is the script you have to replace scriptcmd with to use the files in busybox-kernel-1.17.1.rar which you can find in the directory of Kaser I told you about.
linux_scriptcmd also sets up the resolution to 1024x768.
There's no risk of bricking of your notebook as Windows CE in VT8500Software.rar will restore just fine - and will restore the screen resolution as well.

P.S: To be clearer, the resolution of the LCD is actually 800x480. We apparently get the video card to output 1024x768 and the screen only displays the first horizontal 800 pixels and the first vertical 480 pixels.

-nextvolume

nextvolume, I don't know what I'm doing wrong.  I formatted an SD card on a windows XP Pro machine, as a FAT Partition (Not Fat 32).  I created the scriptcmd with mkimage, by copying the text you had in your Notes file, and placed the resulting scriptcmd file in the root folder.  The only thing I didn't do was create a folder called scripts and place the files there, but all I seem to get is Windows CE 6 booting up.  Please help.  Any suggestions would be great.  I am attempting to create a LiveSD version of Ubuntu for ARM (with the Marvell Dove image file).  Here is my scriptcmd file contents:

setenv lcdparam 1,30000,5,1024,768,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000,D811003c|0x2,D811005c&~0x2
fatload mmc 0 0 /casper/uImage
fatload mmc 0 1000000 /casper/uInitrd
textout 60 132 "Loading LiveSD kernel ..." ffff00
setenv bootcmd mem=512M file=/cdrom/preseed/ubuntu.seed -- boot=casper
bootm 0 1000000

---

### Post by nextvolume on 2010-01-07
You have to put the files in a directory called script that's why it doesn't start up.
And check if you've used mkimage as I documented.

---

### Post by dwinston91 on 2010-01-07
I'll try putting the files in a directory called script.  Yes, I used mkimage to create the scriptcmd file.  The text above is just a plain text copy of the actual script.  Thanks for the quick response too! :)

---

### Post by nextvolume on 2010-01-07
I had edited my last post with these things, but I saw you posted already by the time I had finished editing, so here is the content, so it is more noticeable:

Passing mem=512M to the kernel says to it that your machine has 512MB of RAM, which is not true and will probably lead to an hang-up.

fatload seems to follow this syntax: fatload mmc 0 <memory address> <file>
bootm according to the U-Boot manual is like this: bootm addr [args]

Then you should invert the arguments to the bootm command.
The RAM you write on is safe as it what the other scripts use as well.

I should get a better idea of the memory and then I should program and together an ELF binary of some test just for kicks =P

---

### Post by dwinston91 on 2010-01-07
the mem=512 is in reference to my SD card (2GB), since I am trying to run it completely on the card like a LiveCD version of Ubuntu. The bootm command was modified from the bootm command from the Marvell Dove LiveCD install directions, found here: [https://wiki.ubuntu.com/ARM/MarvellDoveKarmicInstall](https://wiki.ubuntu.com/ARM/MarvellDoveKarmicInstall)

---

### Post by dwinston91 on 2010-01-07
Now we're getting somewhere... :)  The script is actually running now.  I just have to clean it up and figure out the details.  But at least I can see the script working.

---

### Post by sleeky24 on 2010-01-07
Well my netbook turned up today finally! Using it right now actually - cannot wait to see some people runninng linux on these. I will post up the specs of my netbook and the vendor and see iff it the same as others.

---

### Post by dwinston91 on 2010-01-07
nextvolume, what synatx did you use when you printed out environment variables using textout for the following information:

I was able to print the following variables using textout (PARTIAL LIST).
These are their default values:

bootcmd = nand readblob 100000; go 100000
fbaddr = 3800000
stdout = serial
ipaddr = 192.168.1.2
netmask = 255.255.255.0 
NoBootInformation = 1
NoBootProgressBar = 1
Board name: VT8500_Benign
  
I am able to use textout with regular strings.  I just can't seem to find the right syntax for using it with
other commands like printenv.

I tried :  textout 0 0 printenv ffff00
but that didn't work.

---

### Post by PerChristensen on 2010-01-07
Things are taking off thanks to efforts from all,great.
 
Getting my netbook to be mounted via USB cable under MSwindows by crossing pins as described at CNM silver book website only made Windows on hostmachine go down,but my board also is different from pics. of the CNM board.
 
I found a Windows mkimage.exe working OK after adding a cygwin1.dll to the folder.It was possible to copy nonbinary data from Dr_Narvi / shade_emry SD card scriptcmd file to .txt file and with mkimage.exe recompile a working new scriptcmd.
 
Windows users can download at
 
[www.hyfse.com/armVT8500/mkimage-win.zip]("http://www.hyfse.com/armVT8500/mkimage-win.zip")
 
To use unzip in a folder and run from CMD prompt.Man page + a few notes stolen from a developing board site is includet in the zipfile.

---

### Post by nextvolume on 2010-01-08
To print variables with textout you do it like this:
textout 0 0 "${name_of_variable}" ffffff

where name name_of_variable is the name of the variable

@PerChristensen: I don't think the instructions for the Gumstix will work, as at least as I understand it, the machines' memory map is quite different.

---

### Post by dwinston91 on 2010-01-08
Thanks nextvolume, that helps a lot! :)

---

### Post by PerChristensen on 2010-01-08
nextvolume,thank you for joining this thread,your knowledge is of great value.
 
The copy of gumstix note in zipfile was ment as example of syntax more than as example of scriptcmd file to be used on our system.So what it`s all about is that MSwindows users also have a mkimage utility to play with.
 
To clarify:To check if the MSwindows mkimage.exe utility worked I made a script.txt file in the directory where my mkimage.exe reside.The script.txt file only contained the plain text starting from "setenv lcdparam..." copied from the original SD card scriptcmd file (that is with the original u-boot header cut off).
 
As suggested by gumstix I did
 
mkimage -A arm -O linux -T script -C none -a 0 -e 0 -n scriptcmd -d script.txt scriptcmd
 
and a new scriptcmd file with new binary u-boot header popped up in the directory.When copied over the original SD card scriptcmd file located in the SD /script folder it could execute full update of my SmartBook when SD card inserted in the book.
 
The mkimage.exe produced file is 2 183 bytes while original is 2 122 bytes.
 
I have tried to make a bootable SD card with u-boot in root to see if it would override the default bootloader,but with no success.
 
The level of discussion now is above my skills (strings for me is something with Mantovani and his orchestra),but I learn a lot and will continue to contribute when I feel I have something to add.

---

### Post by nextvolume on 2010-01-08
Finally! I found randomly how to work around the via_ata_interrupt issue and I've got Linux up and running on this netbook, from SD card, even. =P
I simply give a fatload command with a very small file as argument and wait a bit.
Hopefully it won't screw up your Windows CE installation, though I've not tested that yet.

It's still a very long way to a decent distribution (which is hard since the kernel is not really for this hardware), but you can telnet to it and play with it a bit.

Here is how you load it:
1) Get the files here, [http://tails92.sepwich.com/files/easypc/easypc_linux.tgz](http://tails92.sepwich.com/files/easypc/easypc_linux.tgz)
2) Put the script directory in the archive on a SD card
3) Put the SD card into the SD card slot into your easy pc notebook.
4) Power on the easy pc notebook
5) Some messages will be printed on the screen when it loads stuff on RAM.
   When the screen blanks and scrambled things begin appearing on the screen,
   reboot.

6) Now your netbook will display a cut 1024x768 image on a 800x480 screen.
    Let Linux boot, and do not power off the system when Booting appears.

7) Now Linux will boot and it will display its messages on the screen.

    Some times there will still be the "via_ata_interrupt" issue, reboot until
    it goes out.

The first time you will do this probably a Kaser Netclient logo will appear on the     screen, and it won't mount anything as root filesystem. It seems that it needs to build the bad blocks table for the NAND flash in the notebook, and that seems to take a while. I recommend to wait around 30 minutes, and then power off your system by pressing the power button.

Now reboot and keep the SD card in it. Do the same thing and now if all goes well you should be able to telnet to local IP 192.168.1.12. Use root as username, and you will receive a shell prompt, you can then play with it.

In [this archive]("http://tails92.sepwich.com/files/easypc/easypc_stuff.tgz") I've included several things, like dmesg, some things from /proc, etc.

Now I think the best solution will be creating a root filesystem from scratch, and I think that unless a way to change the framebuffer resolution is found this system is best used remotely.

To restore the original resolution download [this file]("http://tails92.sepwich.com/files/easypc/scriptcmds/normal_resolution") and replace the scriptcmd file in the script directory on the SD card with it. Then boot with the SD card inserted as usual and follow what appears on the screen.

---

### Post by PerChristensen on 2010-01-08
A huge step forward,and good work,nextvolume:KS.
I get the "via_ata_interrupt" issues on almost every boot.Once booting stopped at RAMDISK: Compressed image found at block 0, and I waited half an hour,but could not come any further.But funny to see a sharp Linux boot sequence on the screen.

---

### Post by sleeky24 on 2010-01-08
I took the battery out of my netbook last night and the main board is green in colour, looks very similar to the CNM Book and also has the two jumpers that are talked about on the CNM book website, so looks like we have three variants so far!
 
Also my unit runs Win CE5.0 not 6.0, same specs as everyone elses machines vt8500 300mhz, 128mb and 2gb storage. Unfortunatly there is no serialview.exe on the system so I cannot provide the details from this. I tried using the serialview.exe from dwinstons files but windows CE responds by saying "this is not a valid windows CE program."
 
I may open the unit up further at the weekend to try and get a manufacture of the board.
 
Lee.

---

### Post by stw89 on 2010-01-08
> **nextvolume said:**
> 
I'd recommend to contact them about that: [http://www.kasernet.com/contact-us](http://www.kasernet.com/contact-us)
The more we are, the better it is. It's GPL anyway, it's a legal obligation.

You can find the Linux I was talking about here: [http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

                                         [Kasernet's Public files]("http://kasernet.livedrive.com/files/") > [Public]("http://kasernet.livedrive.com/files/5244227") > [YF-700]("http://kasernet.livedrive.com/files/5244617") > Firmware > Busybox

                         



Has anyone read through the SDK PDF at - 

[http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

Kasernet's Public files > Public > YF-700 > SDK > YF700 SDK QG.pdf

Why must we log onto the Kaser SDK server to build the kernel? (sdk.kasernet.com)

"Where is the kernel source code
After your login to sdk server (sdk.kasernet.com) with your id and password, you need go to ~/src
to check your own kernel source code"

The PDF references yf700-kernel-1.1.6.tgz

---

### Post by stw89 on 2010-01-09
Ok so the YF700 looks like to have an embedded Linux OS called QRDP (Quick RDP) -

Firmware upgrade details here -
[http://www.youtube.com/watch?v=q93dhTp6hZc](http://www.youtube.com/watch?v=q93dhTp6hZc)

Nextvolume, you have this booting? Does it make any reference to QRDP?

More details at -

[http://www.thinclient.co.th/product/dowload/QuickRDP.pdf](http://www.thinclient.co.th/product/dowload/QuickRDP.pdf)

[http://www.norhtec.com/products/acc/QuickRDP-Specification-080725.doc](http://www.norhtec.com/products/acc/QuickRDP-Specification-080725.doc)

MicroClient TC thin client unit seems to also use VT8500.

---

### Post by nextvolume on 2010-01-09
Yes, the Kaser YF-700 thin client is what I'm already getting the kernel from. I know about the NorhTec as well.

---

### Post by dnharley2591 on 2010-01-09
The password after you push F1 is ztk 
My daughter had deleted all the system files on the cnm mini it has wince5 I followed all instructions on the manufacturer site I bought three different transfer cables and I held tweezers on the specified components on the board and microsoft sync will not recognize the netbook and it does not give me the notice about new hardware so I am finding it to be very difficult to restore this machine is there any other way? I prefer linux on the machine but all I see is system initializing, please wait and it stays there I had it on for 2 days and it wont boot past that I also tried update xip with the sys restore files on a usb flash and eboot nothing seems to work. any suggestions?

---

### Post by dwinston91 on 2010-01-09
nextvolume, what version of U-boot do you have on your machine?  given by the environment variable[COLOR=Sienna]*** ver***[/COLOR]
Mine is U-boot Version: VT8500 U-Boot 1.2.16.1 (Oct 29, 2009 - 00:00:51)

Did you update your U-Boot?

---

### Post by nextvolume on 2010-01-09
It is probably a modified git build of buildroot, as I can't find that version in the [U-Boot FTP site directory]("ftp://ftp.denx.de/pub/u-boot/").
Its base is from two years ago, I think.
The date there is most likely a build date - which, if it is, means they've built these notebooks quite recently!

I will check tomorrow as I prefer not to reboot once I get Linux loaded because it can be tricky to get loading again.

You can surely upgrade your U-Boot, but I don't know how to do so from software yet, and one should actually get a SPI flash programmer or build one for himself (because pre-built they're too expensive) otherwise
if the U-Boot upgrade goes wrong (power goes away, version which doesn't work with the hardware) your notebook will be bricked pretty badly, we don't even have an image dump for U-Boot.
On the other hand, with an SPI programmer, one could do a dump of the SPI flash and if something goes wrong, it's as easy as restoring that dump. It requires you to desolder the SPI flash (that small 8-pin chip on the module with the VT8500, etc.), though.

---

### Post by dwinston91 on 2010-01-09
I was just trying to figure out if the U-boot versions were different, and that was the reason mine didn't get any further than: [COLOR=DarkRed]***Loading kernel...***[/COLOR]

No matter how long I let it sit.

---

### Post by nextvolume on 2010-01-10
My U-Boot version is this:
VT8500 U-Boot 1.2.18.1 (Nov 24 2009 - 12:50:31)

So it's newer than yours - but it might just be the build date.

Also, does it hang when it displays Loading kernel or after it displays Booting?

---

### Post by PrFaas on 2010-01-10
Another 'lurker' coming 'alive' ;)

Very short introduction:
- linuxer since the days of Slackware-3.0
- have some experience with linux-on-arm (Toradex-pxa270)
- not afraid of a soldering iron
- own one of the 'toys' as discussed here :D

I've not (yet) opened 'mine', it's an epc, vt8500@300MHz/128MB-ram/2Gig-flash, wince-6.0 . Seems like nothing special there...
'Mine' was -from-shop missing some 'apps': no nPop :( I've remedied that by now.

I have a few questions to those who've already looked inside:
- what type number of the spi bootprom? I have in the past built a simple (rs-232-port-based) programmer for spi flash proms, and think i could perhaps read/program this one as well. 
- are there *any* signs of rudiments of an rs-232 port on the board? u-boot usually 'talks' via rs-232, and it would be no surprise if that has not been entirely disabled in this machine. An rs-232 buffer using -say- the mic jack connector to 'get outside' could then be added to get 'full control' of u-boot.. 
- has anyone tried to make a script for dhcp/bootp for u-boot? A 'normal' u-boot has support for that. With the Toradex i did most of the development while the arm effectively did a 'netboot'. It's not difficult to set up, and very convenient to try things out. I do not really fancy the idea of doing a zillion re-flashes of the thing before settling on a final linux-install....

---

### Post by dwinston91 on 2010-01-10
> **PrFaas said:**
> Another 'lurker' coming 'alive' ;)

Very short introduction:
- linuxer since the days of Slackware-3.0
- have some experience with linux-on-arm (Toradex-pxa270)
- not afraid of a soldering iron
- own one of the 'toys' as discussed here :D

I've not (yet) opened 'mine', it's an epc, vt8500@300MHz/128MB-ram/2Gig-flash, wince-6.0 . Seems like nothing special there...
'Mine' was -from-shop missing some 'apps': no nPop :( I've remedied that by now.

I have a few questions to those who've already looked inside:
- what type number of the spi bootprom? I have in the past built a simple (rs-232-port-based) programmer for spi flash proms, and think i could perhaps read/program this one as well. 
- are there *any* signs of rudiments of an rs-232 port on the board? u-boot usually 'talks' via rs-232, and it would be no surprise if that has not been entirely disabled in this machine. An rs-232 buffer using -say- the mic jack connector to 'get outside' could then be added to get 'full control' of u-boot.. 
- has anyone tried to make a script for dhcp/bootp for u-boot? A 'normal' u-boot has support for that. With the Toradex i did most of the development while the arm effectively did a 'netboot'. It's not difficult to set up, and very convenient to try things out. I do not really fancy the idea of doing a zillion re-flashes of the thing before settling on a final linux-install....

nextvolume, it stops showing anything after showing: [COLOR=DarkRed]**Loading kernel**[/COLOR].  It doesn't show anything else after that.

 **PrFaas, t**he SPI is a [COLOR=RoyalBlue][B][COLOR=Navy]SAMSUNG_NF_K9GAG08U0M

I haven't seen an RS232 port anywhere.  At least not the traditional type of interface.
I don't have as much experience with u-boot, I am learning on the job here. :)  Do you have any example scripts that you can show how to do what you are talking about?
[/COLOR][/B][/COLOR]

---

### Post by nextvolume on 2010-01-10
Trying to find the RS-232 and JTAG pins was the main reason I disassembled my unit for.
Unluckily I haven't found anything that I could recognize that was linked to them. As a side-note, I found a very useful reset button on the motherboard labeled `SW1`.
I've hacked routers so I know how they should look like and what they're for. I've never done an actual interface, I have very little electronics experience, but as there are schematics on the internet it's more due to lazyness than anything else.

It'd be great if you dumped the ROM from yours so you can just rewrite the SPI in case it gets badly flashed, etc.

---

### Post by PrFaas on 2010-01-10
I've 'taken the plunge', and attempted to open the box. Removing the screws & battery (7.4Volts, 1900mAh text on it) is easy enough. I did also 'get stuck' when attempting to remove the keyboard: I can pry up the kb from the bottom, but not really remove it: the hinges of the display are in the way. The top of the keyboard seems to have two 'hooks' that 'grab' over the display hinges, and i can not pull it forward. I don't think i'd have real problems with the cabling, but the plastic is in the way for now. I saw another user describe the same problem a few pages back.... 

W.r.t. the SPI chip, i can't veryfy, but i have the impression that the answer contained the type number of the 2 Gig 'main/disk' flash rom; i can be mistaken.. my first & main interest would be type number of the 512 kBytes (8-pins...) bootrom. Having a flash-facility and backup copy of that one would -i think- provide an 'insurance policy' against 'bricking' these machines.

w.r.t. netboot-commands for u-boot: i'll check/report tomorrow 'at work': i've got 'the set' for that there. 

For now, and 'from wet memory': it's something like:
- set kernel boot options as parameter of u-boot
- command: dhcp
- command: bootp
- command: bootm <address>

1-st command is to request an IP address using dhcp
2-nd command is to download (via tftp) a bootfile
3-rd command is to actually boot the kernel.

You also have to -when building the kernel- set the kernel-configuration option to have support for a 'root NFS' filesystem. At 'the other end' (meaning a linux workstation) you need a dhcp server, a tftp server and an nfs server. Plus -of course- the entire kernel/config and an nfs-exported filesystem for the 'little one' to use as root filesystem... A bit of a hassle to set up, but then you have your 'little machine' completely booting from the network. Everything (except the messages from u-boot) ends up on the disk of your workstation. Any changes can be made on the filesystem of the 'big brother', and tried out relatively easily. The fun is that u-boot fully supports 'all this'. Dunno if *this* build of u-boot does that though... It *can* be compiled-out ;)

---

### Post by dimeotane on 2010-01-10
Has anyone gotten their hands on a model that has the x86 compatible processor?  Seems to me that could be much easier to get Ubuntu on for about the same price.

---

### Post by dwinston91 on 2010-01-10
**[Building and Debugging ARM [COLOR=highlighttext]Linux[/COLOR] Using ARM Embedded [COLOR=highlighttext]Linux[/COLOR], ARM RealView Development Suite 3.1 and RealView ICE 3.2]("http://infocenter.arm.com/help/advanced/content.jsp?topic=/com.arm.doc.dai0201a/index.html")**

---

### Post by cyknife on 2010-01-10
Hi...

I've followed along since post 70# or so. Purchased one of these  after Christmas for a song (unwanted gift). Neat little boxes. I received a variation of via vt8500@300mhz 128mb 2gb. with the removable SoC. I've included pic links of main board. Has anybody sizzled their power adapter yet? Mine blew after one hour.

[http://i252.photobucket.com/albums/hh39/cyknife/P1000323.jpg](http://i252.photobucket.com/albums/hh39/cyknife/P1000323.jpg)

[http://i252.photobucket.com/albums/hh39/cyknife/P1000324.jpg](http://i252.photobucket.com/albums/hh39/cyknife/P1000324.jpg)


Under wince 6.0 how does one determine the actual cpu speed?

---

### Post by stanwu on 2010-01-10
**[SIZE=2]HI [/SIZE]****Per Christensen**
[SIZE=2]
we got your email, and thanks for your request that we had ask the[/SIZE][SIZE=2] authorize of source code from manufacturer now.

the VT8500 YF-700 thin client (NetClient), this board is more similar as x86 platform:

[/SIZE][FONT=Arial]**[SIZE=4]Hardware Specifications[/SIZE]**[/FONT][FONT=Arial][B][SIZE=4] NetClient

[/SIZE][/B][/FONT][SIZE=2][FONT=Arial]Model[/FONT][/SIZE]
[SIZE=2][FONT=Arial]YF[/FONT][FONT=Arial]-[/FONT][FONT=Arial]700 V[/FONT][FONT=Arial]1.1 support VESA mount
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]CPU[/FONT][/SIZE]
[SIZE=2][FONT=Arial]VT8[/FONT][FONT=Arial]500[/FONT] [FONT=Arial]SoC [/FONT][FONT=Arial]Arm9[/FONT][FONT=Arial] 250-400Mhz[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Memory[/FONT][/SIZE]
[SIZE=2][FONT=Arial]DDR2-400[/FONT] [COLOR=#000000][FONT=Arial]128/256[/FONT][/COLOR][COLOR=#000000][FONT=Arial]MB[/FONT][/COLOR] [FONT=Arial]On-board[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Video [/FONT][FONT=Arial]Capability[/FONT][/SIZE]
[SIZE=2][FONT=Arial]2D Graphic Acceleration (JPEG decoder)
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]VGA[/FONT] [FONT=Arial]Resolution[/FONT][/SIZE]
[SIZE=2][FONT=Arial]1024x[/FONT][FONT=Arial]768[/FONT][FONT=Arial] 16[/FONT][FONT=Arial]-bit C[/FONT][FONT=Arial]olor[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Storage Interface[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- NAND[/FONT] [FONT=Arial]Flash [/FONT][FONT=Arial]1/2/4 [/FONT][FONT=Arial]GB on board[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 4[/FONT][FONT=SimSun]0[/FONT][FONT=Arial]-[/FONT][FONT=Arial]pin IDE x1 support IDE to SATA adapter
[/FONT][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Arial]- [/FONT][/COLOR][COLOR=#000000][FONT=Arial]SD[/FONT][/COLOR][COLOR=#000000][FONT=Arial]/MMC x 1[/FONT][/COLOR][/SIZE]
[SIZE=2][FONT=Arial]LAN[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 10/100[/FONT][FONT=Arial]T[/FONT][FONT=Arial] LAN [/FONT][FONT=Arial]x 1[/FONT][/SIZE]
[SIZE=2][FONT=Arial]WLAN (Optional External USB Dongle)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- IEEE 802.11b/g (USB interface)
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- Infrastructure Mode (Client Mode)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Audio[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- AC97[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Front [/FONT][FONT=Arial]Panel [/FONT][FONT=Arial]I/O[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]Audio x2 (Mic in & Headphone out)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]-[/FONT] [FONT=Arial]SD[/FONT][FONT=Arial]/MMC[/FONT] [FONT=Arial]C[/FONT][FONT=Arial]ard [/FONT][FONT=Arial]R[/FONT][FONT=Arial]eader[/FONT][/SIZE]
[SIZE=2][FONT=Arial]-[/FONT][FONT=Arial] Power Reset Push [/FONT][FONT=Arial]B[/FONT][FONT=Arial]utton[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- Power and [/FONT][FONT=Arial]IDE [/FONT][FONT=Arial]Storage Activity LED[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]USB[/FONT] [FONT=Arial]2.0 [/FONT][FONT=Arial]x 3 - outside x2  inside x1
[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Rear [/FONT][FONT=Arial]Panel [/FONT][FONT=Arial]I/O[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]LAN x1[/FONT][FONT=Arial] with Diagnostic LEDs[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]PS[/FONT][FONT=Arial]/[/FONT][FONT=Arial]2[/FONT][FONT=Arial] x[/FONT][FONT=Arial]2[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]VGA x1[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- Power Input[/FONT][FONT=SimSun]&#65306;[/FONT][FONT=Arial]MINI DIN [/FONT][COLOR=#000000][FONT=Arial]JACK-[/FONT][/COLOR][COLOR=#000000][FONT=Arial]6pin[/FONT][/COLOR][COLOR=#000000][FONT=SimSun]&#65288;[/FONT][/COLOR][COLOR=#000000][FONT=Arial]5[/FONT][/COLOR][COLOR=#000000][FONT=Arial]V/[/FONT][/COLOR][COLOR=#000000][FONT=Arial]3A[/FONT][/COLOR][COLOR=#000000][FONT=SimSun]&#65289;(1-3W)&#65292;[/FONT][/COLOR][/SIZE]
[SIZE=2][FONT=Arial]- Power [/FONT][FONT=Arial]ON/Off [/FONT][FONT=Arial]Switch[/FONT][/SIZE]
[SIZE=2][FONT=Arial]Side Panel I/O[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- 9-PIN Male RS-232 x 1[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- [/FONT][FONT=Arial]USB[/FONT] [FONT=Arial]2.0 [/FONT][FONT=Arial]x 1[/FONT][/SIZE]
[SIZE=2][FONT=Arial]- Internal 40-PIN IDE x 1 (Under Slide Cover)[/FONT][/SIZE]

hardware demo [http://www.youtube.com/watch?v=bGaJ91197ko](http://www.youtube.com/watch?v=bGaJ91197ko)

[SIZE=2]
the platform is the open system that you can install full Debian into NAND flash disk and 100% compatible with pre-build binary code of Debian for ARM[/SIZE]

[SIZE=2]If our manufacturer allow us to support the open souce community that we will full support software of hardware as we could :D


[/SIZE]

---

### Post by PrFaas on 2010-01-11
I've only seen the bottom of my own the board so far, but: 'mine' looks yellow and exactly like the foto from 'cyknife'. Zooming into that foto, is that a set of pins marked 'J17, gnd, RX, TX, +5V' i see? I do have to zoom in until 'almost pixel-resolution'... That does look like a hint of a serial port if ever i saw one ;)

And: an SoC module: very interesting. I did not manage to find any 'connecting' information on the web yet, but:

- if it is a 'custom-off-the-shelf' module, then finding the actual 'maker' of the module could prove very interesting. It is quite possible that a bsp is provided for the module.

- the SODIMM connector (foto top) is very likely to provide access to all relevant bus/Io signals.

Since mr 'cyknife' managed to disassemble his machine to board level: would you be willing to give a hint as to how you got past the snag with the display hinges that got me 'stuck'?

I'm seriously considering to get me a 2-nd one of those machines :D 'Mine' comes from the local 'pots and pans' (cooking utensils, not less) shop, no less..

---

### Post by idiamin on 2010-01-11
Hi, another lurker here.
PrFaas That is Definitely "GND RX TX 5V". Someone hook it up to the serial Port. Here is a cable we can probably make ourselves. hxxp://superdroidrobots.com/shop/item.asp?itemid=335

I know this is not on topic , but has anyone tried X-Lite on Windows CE?

---

### Post by PerChristensen on 2010-01-11
**stanwu**
 
Thank your for kind reply from you at [www.kasercorp.com]("http://www.kasercorp.com")
 
The specifications of the KASER VT8500 YF-700 thin client (NetClient) seem very similar to specifications of the mini netbook talked about in this forum. 
Hardware with CPU + Sound + Port configuration look identical (in addition the netbooks has WiFi Ralink RT 2070/RT 3070).
 
Your YouTube video show the VT8500 YF-700 Netclient`s capability,and it is very interesting what you mention about Debian for ARM. 
I belive it will be to a lot of help if the manufacturer agree in releasing the source used by your NetClient.Otherwise another solution probably can be found.
 
The positive attitude at kasercorp is very appreciated.Users of your compact MP4 players,home entertainment boxes and thin client are to be envyed.
 
On behalf of the thread thank you for reply,and thank you for your time.

---

### Post by cyknife on 2010-01-11
> **PrFaas said:**
> 
Since mr 'cyknife' managed to disassemble his machine to board level: would you be willing to give a hint as to how you got past the snag with the display hinges that got me 'stuck'?

I'm seriously considering to get me a 2-nd one of those machines :D 'Mine' comes from the local 'pots and pans' (cooking utensils, not less) shop, no less..

I disassembled mine as follows:

1 Removed all screws from bottom, batt. cover first (note two longer screws for batt cover and two machine screws mating to keyboard from bottom.)

2 Unplug batt. 

3 Pull the keyboard. It has 4 pressure tabs forward of the row of function keys. Set each tab with a tooth pick etc. lift board and decouple the ribbon cable. 

4 Decouple remaining ribbon cable(s)

5 Separate top cover perimeter from bottom half then gently lift cover. It will pivot about the panel hinges but will snap away harmlessly @45 degree or so. 

6 After that remove one screw in the main board and four screws at the hinge points. Decouple the video and lamp connectors.

7 Lift board from side with two usb ports. Its free.

reassemble reverse

NOTE the two longer screws for the the batt. cover will penetrate the other side if installed without the batt. cover.

---

### Post by dwinston91 on 2010-01-12
Here is another U-boot Reference guide: [http://www.freescale.com/files/32bit/doc/quick_ref_guide/LITE5200BUBPG/LITE5200BUBPG.pdf?fpsp=1](http://www.freescale.com/files/32bit/doc/quick_ref_guide/LITE5200BUBPG/LITE5200BUBPG.pdf?fpsp=1)

---

### Post by PrFaas on 2010-01-12
There was an 'unanswered question' about what has to be set to make u-boot perform a netboot. I've dug into the 'doc' i had at work, and -for the toradex/colibri module- we've used the following u-boot commands to get a netboot:

setenv bootargs "root=/dev/nfs ip=:::::eth0: console=ttyS0,9600n8"
dhcp
bootm

The 1-st command is to prepare the kernel for net-booting, and tell the kernel to use a root-filesystem 'on nfs'. The contents of 'bootargs' is a set of parameters that will be passed to the kernel.

The 2-nd command is to let u-boot request an IP address and a boot-file (the kernel) from the dhcp/tftp server

The 3-rd command is to actually boot the kernel

Note that this is *only* the 'small brother' part of net-booting. The server ('big brother') needs some information to make the entire story work:

- a configured dhcp server
- a kernel file
- a nfs-exported root-filesystem

But: the good news is that -when these commands are 'passed' to u-boot- it will *attempt* to netboot. As you will have seen, there is not a word about over-writing any flash-filesystem, nor is there a 'saveenv' command used on the 'small brother's u-boot, just some instructions to use the network. When you'd monitor the network -with tcpdump for instance- you should 'see' the 'small brother' attempting to get an IP address and boot-info. Without the services installed and configured, that *will* fail, but -if 'small brother' does try to netboot- that shows that the u-boot in the 'small brother' is compiled with support for this operation, and for networking. U-boot is a way more potent bootloader than any BIOS i've ever found on any 'normal' computer. To set up the actual services to perform a successfull netboot is not quite trivial, but only a matter of 'work' :D

I'm going to see if i can 'open' the small machine and connect an oscilloscope to the TX 'pad', to see if u-boot is attempting to 'talk' to the serial port, and -if so- to see what voltage it generates there. I'm assuming that the RX pin will accept the same voltages that it generates on the TX pin. All assuming that these nice 'pins' are indeed the connection to the serial console and that u-boot is actually 'talking' there of course ;)

---

### Post by dwinston91 on 2010-01-12
> **PrFaas said:**
> There was an 'unanswered question' about what has to be set to make u-boot perform a netboot. I've dug into the 'doc' i had at work, and -for the toradex/colibri module- we've used the following u-boot commands to get a netboot:

setenv bootargs "root=/dev/nfs ip=:::::eth0: console=ttyS0,9600n8"
dhcp
bootm

The 1-st command is to prepare the kernel for net-booting, and tell the kernel to use a root-filesystem 'on nfs'. The contents of 'bootargs' is a set of parameters that will be passed to the kernel.

The 2-nd command is to let u-boot request an IP address and a boot-file (the kernel) from the dhcp/tftp server

The 3-rd command is to actually boot the kernel

Note that this is *only* the 'small brother' part of net-booting. The server ('big brother') needs some information to make the entire story work:

- a configured dhcp server
- a kernel file
- a nfs-exported root-filesystem

But: the good news is that -when these commands are 'passed' to u-boot- it will *attempt* to netboot. As you will have seen, there is not a word about over-writing any flash-filesystem, nor is there a 'saveenv' command used on the 'small brother's u-boot, just some instructions to use the network. When you'd monitor the network -with tcpdump for instance- you should 'see' the 'small brother' attempting to get an IP address and boot-info. Without the services installed and configured, that *will* fail, but -if 'small brother' does try to netboot- that shows that the u-boot in the 'small brother' is compiled with support for this operation, and for networking. U-boot is a way more potent bootloader than any BIOS i've ever found on any 'normal' computer. To set up the actual services to perform a successfull netboot is not quite trivial, but only a matter of 'work' :D

I'm going to see if i can 'open' the small machine and connect an oscilloscope to the TX 'pad', to see if u-boot is attempting to 'talk' to the serial port, and -if so- to see what voltage it generates there. I'm assuming that the RX pin will accept the same voltages that it generates on the TX pin. All assuming that these nice 'pins' are indeed the connection to the serial console and that u-boot is actually 'talking' there of course ;)
  
So the entire u-boot script file consists of just these three lines?  Also can you provide some details of how to setup the "big brother machine"?  Like where to put the kernel file and the exported nfs filesystem.  which kernel and nfs filesystem did you use? And are there any additional settings on the dhcp server that need to be setup? or how should I setup tftp?    I know I have lots of questions.:)

---

### Post by corruptbinary on 2010-01-12
Another lurker here, just thought you guys should know that haleron is offering hte same netbook with a choice of win ce or linux for an extra $15....dunno if the source code is included or not...weird.

here is the link, you might need to register to view it:

[http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27]("http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27")

---

### Post by corruptbinary on 2010-01-12
I forgot, I found 2 more devices that seem to be using the same chipset 

1) framechannel - digital picture frame - seems to be runnign linux using openembedded but im not sure
[http://www.thinkingscreen.com/]("http://www.thinkingscreen.com/")

2) MicroClient TC -  by NorhTec a thin client runs Quick RDP embedded linux
[http://www.norhtec.com/products/mctc/index.html]("http://www.norhtec.com/products/mctc/index.html")

hopefully everyone together can figure out a solution!

---

### Post by corruptbinary on 2010-01-12
MontaVista Linux Professional Edition 4.0/5.0 supports our processor, but does not appear to be free or open source ...?

---

### Post by nextvolume on 2010-01-13
It's probably derived from Monta Vista Linux, indeed. If you open up uzImage.bin in an hex editor you can see the string "Montavista Linux" in it.

---

### Post by PerChristensen on 2010-01-13
corruptbinary,great with a helping hand,but unfortuneately the mini netbook I own does not support booting from USB drive.
I made a "Ubuntu rescue remix" bootable USB stick boot my windows laptop,but it did not impress the mini netbook in any way.Also a bootable SD card with the remix did not work.
 
Another subject:
According to the Web the Nokia 770 internet tablet has a 250 MHz Texas Instruments OMAP 1710 ARM compatible CPU (arm926tej core) with 64 megs of available internal flash memory.OS is Linux based Maemo 2006.
 
The source for the Linux Maemo distrbution 2006 used on these Nokias is available from the Maemo site.A brief look at the source of the Maemo 2006 kernel (2.6.16) does not indicate modification of the original kernel source from kernel.org as far as I can see.
 
Source for some Maemo specific apps. exist in the distro (browser,calculator),but otherwise it looks like a full but small Linux distribution.So perhaps an ARM kernel compiled from unmodified kernel.org source (with all modules set to "on" in config) will work,and the "via_ata_interrupt" issue experienced by nextvolume is caused by some WLAN driver problems in the kernel from the KASER YT-700 (supporting USB dongle WiFi)??.
 
A .jffs2 root filesystem is availabel at Maemo,also some Maemo ARM compiled non Linux-standard binaries can be downloaded.Nokia has its own bootloader.
 
nextvolumes SD card boot is elegant,and perhaps a script can prepare "littlebrother" for netboot,as suggested by PrFaas / dwinston91.
 
A lot of non available hardwarespesific information has to be given to u-boot as I see it.Coming week-end I will try setup crosscompiler [http://www.codesourcery.com/gnu_toolchains/arm](http://www.codesourcery.com/gnu_toolchains/arm) and compile kernel 2.6.16,if my Linux system not is outdated.

---

### Post by xmob on 2010-01-13
Registered, just so I can de-lurk.  ;)

I wouldn't bother with Maemo.  It's VERY tailored to Nokia devices (currently using a Nokia N900 here) and there are some closed source components.  A more suitable version might be Mer ([http://wiki.maemo.org/Mer](http://wiki.maemo.org/Mer)).  This is a fully open source distribution.

I have one of the CE5 CnM Books from Maplin.  These seem to be using eboot.  :( However, I have a plan.  I will report back soon.  <booting up ARM toolchain as we speak>

BTW - People need to be aware that these are ARM devices and standard Linux distros WILL NOT ever work as they for x86 devices.

---

### Post by nextvolume on 2010-01-13
It is a common misconception that all you need to make something run on hardware is to supports its processor. While the code will most probably run, it won't do anything meaningful because peripherals are programmed in a different way.
You program peripherals through the memory address paradigm on ARM, and on different SoC platforms you have peripherals for which the memory address you have to communicate them with is located at another place, and they often even have different behaviour.

So we have to wait Kaser to release the source code if we want an out-of-box Linux. Otherwise a port needs to be started (and an hardware technical document needs to be started). You can ..ehm find something about the VIA VT8430 but that's too little for our purposes so it will take a lot of reverse engineering.

---

### Post by corruptbinary on 2010-01-13
But these are system on a chip right? wont all vt8500 program its built in peripherals the same way?  I could be wrong, just asking :)

and it seems montavista is open, but they have a tool for embedded developers to quickly port linux.

---

### Post by corruptbinary on 2010-01-13
The VIA VT8500, is from Wondermedia, a spinoff of VIA, called the wm8510, Prizm.

Im trying to get aa BSP and docs from them.

---

### Post by corruptbinary on 2010-01-13
OK here is all I found out so far.
here is the link for wondermedia, the via spinoff
[http://www.wondermedia.com.tw/index.php?option=com_content&task=view&id=51&Itemid=23]("http://www.wondermedia.com.tw/index.php?option=com_content&task=view&id=51&Itemid=23")

the 8430 appears to be the dual core version of the 8500:
VT8430 multimedia application processor parameter list: 
Dual-core architecture (250MHz ARM926EJ-S + 200MHz DSP) in a more smooth multimedia playback capabilities to support a variety of media hardware decoding    Video: MPEG-1/MPEG-2/MPEG-4/H.264/DIVX/XVID   Audio: MP3/WMA/AAC/AAC + / DTS / Dolby Digital   Image: JPEG * Video Interface: LCD (1024x1024) / TV-Out / CCIR656/601 IO / MPEG2-TS * Audio Interface: I2S / AC97/PCM/SPDIF * Memory, storage support: DDR/DDR2/NAND Flash SPI / LPC Flash for boot ROM IDE I / F SD (SDIO) / CF / MMC / MS * Peripheral Interface: USB 2.0 OTG x 1 & Host x 1 UART/I2C/SPI 10/100 Ethernet MAC * Security Engine: DES/3DES, AES, RC4 * Package: 21x21 PBGA 
VIA VT8430 is designed specifically for multimedia entertainment based on ARM926EJ-S RISC core application processor to support a variety of common audio and video hardware decoding, which is very suitable as personal multimedia device as a whole SoC solutions, such as the PMP (portable multimedia players), in-car entertainment, DMA (digital media partners), etc.. 8430 contains a wealth of peripheral interfaces, can very easily add a variety of external modules to increase product features, such as hard drive, WiFi module, FM modules, mobile TV module, GPS module, infrared remote control module, various types of USB devices, which also specially designed for safe and added a dedicated encryption engine, enabling customers to easily achieve the low cost of data encryption requirements. 
8430 is the VIA entire ARM SoC in a family now has a variety of products based on the 8430 program: GPS navigation systems, multimedia players, handheld mobile TV, BSP package supports standard Linux and Microsoft's WinCE platform. Welcome all kinds of Design House, and are interested in consulting a friend calls come to negotiate. 
VIA Technologies, Inc. The company is an authorized agent, For more detailed information, please call contact. Contact: Mr. Chen Tel: 13751153055 / 0755-82916972 ext: 38 E-mail: [email]JohnnyChen@leadinglight.com.cn[/email]

this site supposedly has a datasheet, but im not about to pay $35 to find out:
[http://www.pudn.com/downloads140/sourcecode/embed/detail606986.html]("http://www.pudn.com/downloads140/sourcecode/embed/detail606986.html")
[http://www.pudn.com/downloads116/doc/detail492254.html]("http://www.pudn.com/downloads116/doc/detail492254.html")

goodluck

---

### Post by nextvolume on 2010-01-13
You can find those datasheets [here](http://tails92.sepwich.com/files/easypc)
It's not very nice of them to close the specs to program our own systems.

---

### Post by corruptbinary on 2010-01-13
Oh excellent nextvolume!

---

### Post by corruptbinary on 2010-01-13
i'm going to be buying another mini netbook,

but id still like linux on this via

---

### Post by PrFaas on 2010-01-13
> **dwinston91 said:**
> So the entire u-boot script file consists of just these three lines?  Also can you provide some details of how to setup the "big brother machine"?  Like where to put the kernel file and the exported nfs filesystem.  which kernel and nfs filesystem did you use? And are there any additional settings on the dhcp server that need to be setup? or how should I setup tftp?    I know I have lots of questions.:)

I feared i would bore you with all too long a monologue ;)

On my example machine, 'three lines' mentioned is indeed all that was needed to get u-boot into 'netboot mode'. Again: this will work *only* if the networking interface and the netboot-supporting code was compiled into the u-boot on the 'small brother'. It would be worth a try.... See below why even without any of the servers active, just making a script with those three lines could be of some use....

W.r.t. the 'big brother', i'll give the example of the configuration for 'my' 'small brother':

You need a dhcp server installed and configured on your network. It would help it that one is the *only* dhcp server: if -for instance- a router on the network is also willing to issue IP addresses to 'any' client, there is quite a chance that the router will provide an IP address to 'small brother', but it is quite unlikely that that router will also provide the rest of the information... That will not result in a successfull netboot. The dhcp server described here will be configured to provide the complete netboot information, a router is usually configured to only provide IP addresses, nameserver adresses and default gateway information. Antoher thing, it is 'best' to use a rather 'quiet' and isolated network for this kind of experiments: for the things we're going to do here, security is *not* assured :D We're also going to 'tcpdump' the network, and on a busy network it will be quite a job to 'pick out' the few interesting network packets from in-between 'the flow' on the network.

A dhcp server is usually configured with the file /etc/dhcpd.conf. For my netbooting of 'small brother' i have the following information in that file:

```

# the colibri: the development board: boot config
host colibri {
 hardware ethernet 00:14:2d:00:0a:d4;
 fixed-address 192.168.0.200;
 option host-name "colibri";
 next-server 192.168.0.1;
 filename "/home/prf/projects/boot/uzImage.bin";
 option root-path "192.168.0.1:/home/prf/projects/rootfs";
}

```

description:

The 'hardware ethernet' is followed by the MAC address of the 'small brother'. I'll explain in a moment how i get my hands on that one. 

The 'fixed-address 192.168.0.200' sets the IP address of 'small brother'. I have used a fixed IP address to make exporting the NFS filesystem easier. It can be any valid and 'free' IP address on the network that the 'small brother' is connected to. 

The 'option host-name "colibri"' is to provide a host-name to the 'small brother'. It *is* extra, and not strictly needed. The 'next-server' is the IP address where 'small brother is going to attempt to get its bootfile from; So: 'next-server' is set to the IP address of 'big brother'.

The 'filename "/home/prf/projects/boot/uzIimage.bin"' contains the path of the kernel file that must be loaded: in my case that is the file '/home/prf/projects/boot/uzImage.bin'. 

The kernel itself is an arm-kernel, pre-processed for use as a netbootable kernel. I'll come back to how to prepare the kernel for that in a moment. The 'option root-path "192.168.0.1:/home/prf/projects/rootfs"' is the path of the root-filesystem. It is a directory that is nfs-exported.

Now to the 'loose ends' of the previous description: 

How to get the MAC address of 'small brother'? I use tcpdump for that. The first thing that 'small brother' does is to broadcast on the network for a dhcp server. It uses the 'broadcast MAC address': ff:ff:ff:ff:ff:ff as destination address (mind you, this is a MAC address, not an IP address..), and its own MAC address as source MAC address. This network packet will show up in tcpdump as a DHCPDISCOVER packet. 

A DHCPDISCOVER in the tcpdump output is the signal that someone is attempting to get an IP address from a dhcp server. On our 'quiet' network, that must be 'small brother' :) So: the '00:14:2d:00:0a:d4' is the MAC address of 'small brother'. You have to copy/paste the address into dhcpd.conf, and restart the dhcpserver to make the dhcp server actually accept this as an address that it will 'service'. 

-intermezzo-
That is also why a 'script-test' using the sdcard method could be interesting: if 'our' u-boot supports netbooting, then this 'DHCPDISCOVER' will show up on the local network, even without an actual dhcp server.
-end intermezzo-
 
The kernel file: (the file '/home/prf/projects/boot/uzImage.bin' of the example): I'm no specialist there, but it is a normally-cross-compiled arm-kernel, the result of the command:

```

make vmlinux

```

of kernel compilation. Note that you will have to have everything 'preset' for cross-compilation when building that kernel. Allow me please to leave the monologue of how to generate and set up a cross-compilation toolset for a 'to be continued' :). That vmlinux file is pre-processed in two steps:

```

arm-linux-objcopy -O binary -R .note -R .comment -S vmlinux linux.bin
gzip linux.bin

```

arm-linux-objcopy is one of the tools from the 'binutils' package of cross-compilation tools... This results in a file linux.bin . Reason for that conversion: I do not know.... That linux.bin is converted to a u-bootable image file with the command:

```

mkimage -A arm -O linux -T kernel -C gzip \
   -a 0x00008000 -e 0x00008000 -n "Linux Kernel Image" \
   -d linux.bin.gz uzImage

```

mkimage sould be more 'known' to you than to me by now: it is the same program that is used to generate the sdcard script files. The resulting file 'image' is the file that must be copied to the directory: '/home/prf/projects/boot' so that the 'small brother can load it. The other options of mkimage, i'm not sure of, i've got them from the 'recipe' of the colibri bsp. The 'uzImage.bin' file should be made world-readable (chmod a+r uzImage.bin). 

Here is where the tftp server comes into play: After getting the response from the dhcp server (which contains the path to the 'uzImage.bin' file), the 'small brother' will attempt to load the 'uzImage.bin' file using tftp. To make that a success, you will need to have a tftp server installed on the 'big brother' machine. You can test if the tftp server works using the command 'tftp localhost'. That is an ftp-like command-line client which uses the tftp protocol and server. Tftp is very limited, it has no 'ls', and needs a full pathname of a file to 'get'...

One note on my Wondermedia WM8505 machine: it has as 'own' default IP address 10.1.8.250, and has a 'built-in' preset IP address for the boot-server of 10.1.8.37 . Meaning: If you set your 'dedicated boot-lan' to have 10.1.8.37 as IP address for the 'big brother' then the preset IP addresses that are set in u-boot of the 'small brother' should be ok already. I did find that -when attempting to tftp my kernel with 192.168.0.1 as address for 'big brother' that the tftp failed.
  
Finally: the root-filesystem. That should be a directory on 'big brother' which contains a directory tree that will form the root-filesystem of 'small brother'. Note that this includes the user-id's and permissions that the 'small brother' will see. You will need to nfs-export the directory tree.

To export the directory tree to nfs-clients (in our case that is 'small brother') you will have to have an nfs server installed and enabled and enter the following line in /etc/exports:

```

/home/prf/projects/rootfs 192.168.0.200(rw,no_root_squash)

```

and restart the nfs server after you've edited that line into /etc/exports.

As for the contents of the exported filesystem, please allow me to keep that for the next 'monologue' :D For now, i'll just mention that it should contain a valid and usable root-filesystem for the 'small brother'.

Is that long enough for one of the 'to be continued' sessions? :)

---

### Post by PrFaas on 2010-01-13
BTW: i've just started the 'backup' machine (let's call it #2) i got today. Source: the same shop i got #1 from, exterior and other information is exactly the same as #1, same box, same price. But: the 'my computer'-> properties results in a slightly different set of information: Processor type is now 'WMT, ARM-WM8505', and the OS is WindowsCE, version 6.00, (build 3122). 

So far, i've also found that the 'player' has acquired a 'skin'; a nicer one than the rather 'bare' one i saw before.... The inside looks like the same yellow pcb i've seen on #1.

No: i've not disassembled #1 yet: i can either write long monologues or handle a screwdriver, but not both at the same time ;)

---

### Post by dwinston91 on 2010-01-13
Thanks so much PrFaas, that information is soooooo helpful. ;)

---

### Post by corruptbinary on 2010-01-13
So far I have emailed just about every company talked about in this thread with no good responses to where the kernel sources are for the yf100, tc, etc... I have also found names of the people who ported the kernel to the via netbook and emailed them with no response.

once they released a product with the linux kernel they have to distribute the source with any changes, right?

---

### Post by nextvolume on 2010-01-14
If a way to disable PATA can be found (and thus the kernel in my easypc_linux.tgz archive boots even when it doesn't manage to mis-detect the PATA controller) it is already useful as a remote testing machine.

It is unlikely far more common than you think to not give out GPL sources. The same thing happens also with a lot of routers.

---

### Post by PrFaas on 2010-01-15
Just a 'fyi': I managed a full disassembly this morning; Will make foto's later on the day. Looks like i have one 'spare' USB-ish set of pads that go to the display unit..., a tsop set of pads on the bottom of the CPU module, something that looks like a serial port set of 'pins' and one 'yet-unknown' chip that is not 'present'.

[update]

After making foto's (~ 65 Mbytes of picture files... I could perhaps upload them somewhere; suggestions are welcome :) ). And a bit of net-searching i think i've got a bit better idea of what hardware is in my system. 'Mine' is one of the yellow/orange boards, with a plug-on CPU module. 


The CPU module contains the CPU (VT8500), plus a DDR2 128 MB (64MBx16) sdram chip. Plus one SO8 chip that appears to be the SPI bootrom that was mentioned before. Sorry, but i have to disagree that the 'big' chip (at the bottom of the mainboard) is *not* the bootrom, but the 2Gig 'disk' chip. 

So far, i've bee able to track down:

- on CPU module:
A3R1GE4CFF: 128 MBytes ddr2 RAM (on CPU module) 
EN25F04-100: 512 Kbyte boot-flash (on CPU module)
VT8500: no datasheet, CPU etc..

At the bottom of the CPU plug-in module there is a set of pads for a tsop chip, unpopulated...

- on mainboard:
SG850G: single USB 2.0 port -> 4 ports 'hub'
VT1613: audio analog front-end
VT8106: MII <-> LAN so-called 'physical interface' chip, 100 MBps

I've been able to grab the datasheets for all but the CPU chips. I've got something 'close' to the 2 Gig 'disk' chip datasheet, but not entirely of the same chip.

The green 'square' module on the mainboard is -i presume- the WiFi... No 'doc' of that one yet..

From following some traces, i get the idea that there should be an USB-connected chip in the display module, presumably to control the backlight (could be interesting... Has anyone already managed to open the display unit?).

So far, so good, now we're in for an oscilloscope session with this gnd/tx/rx/5V pads... Let's see if we'll get some u-boot messages there. First i'll have to partially re-assemble the machine: i need the display moule connected in order to be able to switch the machine on :)

---

### Post by PerChristensen on 2010-01-16
There should be a pic. of disassembled screen with info of WiFi below.
 
Excellent tutorial in post #148 from PrFaas.After setting up the CodeSourcery crosscompiler I now see the complexity of Linux on ARM pointed out by nextvolume.
 
A small comment to PrFaas`s tutorial:
If using CodeSourcery you have to use an "expanded" objcopy command ( look in CodeSourcery /bin ).Also you have to gzip the linux.bin before using mkimage on it.
 
Because of old Linux system I am not able to use newer version than 2007 CodeSourcery + the ARM patched Linux kernel 2.6.24.4.
This setup produce kernels accepting the PrFaas torture,but Images are quite big (3 Mb) - perhaps because embedded linux flag is not set in config.A Versatile board kernel compiled nearly flawless (a few warnings),but do not boot using nextvolumes easypc SD card trick.
When playing with the config one easily get errors when compiling.
 
For the interested I have attatched the Versatile board default kernel config which work.If it can be to any help anybody are welcome to ask for a vmlinux / linux.bin / image + modules of their own brand.

---

### Post by PrFaas on 2010-01-16
If i understand right, the screen unit is kept together by 4 screws that are 'hidden' under the small rubber 'pads' on the front of the display unit?

Another question: one of my two machines 'burned' under 'full sail'; I did not do anything special with it, it was happily running its WinCE-6.0 and then it just went 'lights-out' and never came back. Fortunately i was able to swap it at the shop i bought it from :D 

One thing however: i did notice that the right-hand side of the screen unit of the 'burning' machine was 'hot' ever since i first got it. It was not not extremely hot, but about as warm as the underside of the main unit box at the place of the CPU module. Could anyone report if that is also the case with his/her system? I suspect a 'from-factory' problem with what i now expect is the chip i could see on the picture of the previous post at the right-hand side of the screen.

To be honest, i expected that the backlight voltage converter would be at that location, and never bothered too much that it got hot. I've seen inefficient DC --> LCD backlight voltage converters before.. I've even repaired a few after they burned in bigger laptops than this. Seeing a simple chip there makes me think again. looking again: From the text next to the picture i get the impression that it is the WiFi module that's located there (Ralink-RT-2070, combined with me previously seeing that the connection seems to be an USB link on the main-board...). I'd better think again about that 'odd' module on the mainboard then (i thought it would be the WiFi..). The screen unit is a much better place for a WiFi module than somewhere at he bottom of the box, in between -say- a metal table-top and the mainboard, that i'll agree with any day ;) 

Two other things to remark:

- The gnd/tx/rx/5V pins set on the mainboard has 3.3 volts at the tx pin. That implies a bit of a warning for anyone that wants to connect a rs-232 circuit there: it is very likely that the rx pin should also be 'fed' with 0.0 to 3.3 volts signals. Using a 'standard' rs-232 driver/receiver, with 5.0 Volts output of the receiver might not be a good idea. Most likely, these signals end up directly at the CPU itself, and it could well be that the CPU does not tolerate 'full' 5.0 Volts input signal levels.

- I now no longer have any 'true' VT8500 systems: both the #2 machine and the 'swapped' #1 machine have WM8505 as CPU. I don't think it will make all too much of a difference, but *some* changes are bound to have happened between VT8500 and WM8505.

As an 'edit' & remark to mr. PerChristensen: I do not see the attached kernel config; could it have gone missing? And: i've opted for building (and actually managed to build) a toolchain using the 'crosstool' script-set. I had to make on change to the patches set: allowing it to use the 'gcc (GCC) 4.3.3' of my system as compiler...) I'd love to give building a few kernels a try....

---

### Post by PerChristensen on 2010-01-16
To take the screen apart remove the four small "rubber corks" and unscrew,then use your nails.Leads to loudspeakers are very fragile but relatively long.
 
By second thought I perhaps applied a Versatile vendor specific patch to the kernel.I read somewhere patching for ARM should not longer be necessary.
 
Among other things the patch (from ww.linux-arm.org) set crosscompile environment in makefile to arm and prefix for tools beeing used to arm-none-linux-gnueabi- ,something which can be edited manually.
 
And one has to set PATH to the first /bin directory in the CodeSourcery toolchain.Symbolic links from CodeSourcery gcc etc. in the next /bin in the tree are set by default.
 
The config file dissapeared,I will give it another try.I also attach a pic. of the mysterious chip - looking like something alien,but we are also far out by now;)

---

### Post by moblo on 2010-01-17
Hi there, Im new to this forum and have been watching this thread very closely. I have just ordered one of these netbooks. I have no knowledge of programming or writing kernals/OSs, and I have basic knowledge of hardware, soa lot of what I have learnt is purely from reading this entire thread. I may not be able to help in terms of writing code etc, but I would be interesting in testing things on my netbook for u guys once I get it. 
I love the idea of linux on this baby, and particularly want good divx/music/multimedia support, proper internet with decent flash.java support. I look forward to seeing how this 'project' progresses.
On a side note, I am also keen on hardware customization. The kinds of things I have in mind is integrating usb bluetooth/32gb usb key internally, and also looking into possibly upgrading the ram/nand. Obviousle without the netbook and not having done much research into the components, I accept this may not be possible.
Also, finally, thanks to you guys who are contributing to this thread, cos you put in so much time and effort to come up with solutions for others.

---

### Post by PrFaas on 2010-01-17
Judging from the wiring at the 'back' of the pcb, it seems like our 'mystery chip' has something to do with the keyboard: Pins 17 and 18 of the thing go to the CPU module connector, with very few connections at the top of the board, most seem to 'via' to the bottom, and then to the keyboard connector. No sign of any datasheet of the thing though ;)  HT-95A-1? never heard of the thing.... 

HT however seems related to Holtek semiconductor, so i'm going to have a peek 'over there'. Let's see if 'they' have a credible keyboard scan chip.  

As far as the pins go, it does resemble the HT82K629 (Holtek) keyboard encoder chip. Up and including pins 17/18 for interface with the CPU, a 'strap option' for pin 7 (mini keyboard select), Vdd at pin 15, Gnd at pin 27, RC-reset circuit at pin 28... I might still be a bit 'off' (it could be a big or small brother of the chip i found...), but this does resemble the pinning & function of the 'mystery chip' quite well. 

Assuming that HT82K629 is a 'match', then i'd guess we have one less problem w.r.t. getting the keyboard operational with linux: the HT82K629 supports both USB and PS/2 as interface protocol... Not some obscure undocumented interface protocol, but *the* two standard keyboard interface protocols no less :D

---

### Post by celem on 2010-01-18
> **dwinston91 said:**
> celem, I zipped up the folders under My Computer on my machine.  It can be downloaded from here: [http://rapidshare.com/files/329051287/wince_bak.zip.html]("http://rapidshare.com/files/329051287/wince_bak.zip.html")

dwinston91 - I was away for two weeks and without internet connectivity. The link that you posted is now blocked with a max download reached, so I cannot download the files. Is there anyway that you could repost? Thanks in advance.

Celem

---

### Post by dwinston91 on 2010-01-18
celem, nextvolume put them on his site with his files.  They can be found here:
[http://tails92.sepwich.com/files/easypc/]("http://tails92.sepwich.com/files/easypc/")

It is the one called wince_bak.zip, I believe.

---

### Post by litch84 on 2010-01-18
(FYI)

I've found another variety of these netbooks:
- The EPC branded ones.

[B]Hardware details:

[/B]    **Wireless Chip:**
  CHIP:     RT2070L
  PCB Label:       BL-RT3070-50
   
  **MiniPCI SoC: “P709_CPU_V3”**
  MCU: WonderMedia WM8505
  DDR2-800 128MB: Zentel A3R1GE4CFF
   
  **MOBO: P706_MAIN_V5**
  Sound: VIA VT1613 
Ethernet PHY: VT6103X  USB HUB: GL850G
  ?: HT-95A-1
  RAM/FLASH?: Samsung 943 – K96AG08UOM
   
  **Description / Notes:**
The unit also has a 7" LCD with a ARM926EJ-S based SoC. The Wireless module actually looks like someone ripped it out of a USB 802.11 stick and just wired it directly to a usb port. It sits on the RH side of the LCD screen, just above the speaker.

Wonder Media is actually owned by VIA and I'm guessing the WM8505 is the successor of the VT8500, WM also just released the WM8510, which is one step further again.

The system by default runs WinCE and features the ususal SD card slot, usb ports and inbuilt speakers etc...

I should have taken photo's but the main board (Labelled **P706_MAIN_V5**) But anyway, it has a mini-pci slot with a mini-pci card in it (Labelled **P709_CPU_V3**) it that has the SoC and RAM on board... Interchangable CPU's?

I've also been hacking up the scriptcmd file and trying to boot ANYTHING other than CE, but to no success. I came close to getting some random ARM826 based Thinclient imag to boot but it really doesn't like the integrated LCD.

Will take some photo's soon and will update on U-Boot progress.

---

### Post by lalitgr8 on 2010-01-18
Hi 
I am following this link for last few days and is very interesting and informative. this week I too have brought 7" mini laptop and it will really wonderful to have linux have on this laptop. just waiting for breakthrough to  possible install on my laptop.
BTW, I will like to ask a question. I will really  really appreciate if someone could answer that.
intially I was able to download video from you tube and save it on storage card and then was able to play with core pocket media player ,tcpmp, which came installed on mini laptop. and then tried to install tcpmp flash player plug as I was not sure which version I have to try ie pocketpc, smart phone version for windows ce I tried all and end up messing up  core pocket media player. Now it plays some video but does not play flash video and an error message cone that video codec FLV1is not supported by this player.
Just wondering if any one got an idea that which core pocket media player version will work for arm 8500 processor window ce 300MHZ , 2GB or I will be highly obliged if anyone can post core pocket media player files that they have on their mini laptop so that I will able to fix it. your help will be much appreciated
thanks and regards

---

### Post by PrFaas on 2010-01-19
Some posts back in this thread, there is a link to a restore image (VT8500.rar). If you download that one, un-rar it, and look around, you will find the media player's files.

---

### Post by InterPhase on 2010-01-19
Hi!

I'll also get one of these netbooks in the next few days and it would be really great to actually have a full X and these things, but I know we're far away ;)

Having followed this thread, I wondered if we could work around the via_ata message by passing combined_mode=ide|libata to the kernel.

Could anyone try to do this (setenv bootargs 'combined_mode=ide' OR 'combined_mode=libata'')?

Another possibility would be to let WinCE initialize all the hardware and inject a small loader into a kernel DLL of WinCE, but I think this would be rather complicated....

- InterPhase

---

### Post by InterPhase on 2010-01-19
Well, things look quite good as far as I can see them:
- We got NAND access (see dmesg.txt in the [easypc_stuff.tgz]("http://tails92.sepwich.com/files/easypc/easypc_stuff.tgz"))
- To change the 1024x768 default resolution all we need is either access to the kernel sources or some debugging/reverse engineering skills (which I don't have)
- All peripherals of the VT8500 should be supported by the kernel

What we still need to know in order to run linux on it:
- Where does u-boot usually boot from (mem-addr), so we can flash NAND (for the really brave :D)
- Serial port?
- X drivers?

(well, please correct me if I'm wrong)

- InterPhase

---

### Post by tlk23 on 2010-01-19
Has anyone considered using HaRET for testing?  [http://www.handhelds.org/moin/moin.cgi/HaRET](http://www.handhelds.org/moin/moin.cgi/HaRET) . It seems it would be a lot safer than flashing test versions of linux.  
 
HaRET runs on my ARM-AK7802 netbook (CE 5.0).  Just need a few "minor" details, like the proper memory location to load the linux image.

---

### Post by PerChristensen on 2010-01-19
**InterPhase**
 
I changed nextvolumes easypc linux scriptcmd by making a .txt file like this:
 
setenv bootargs mem=112M root=/dev/ram rw initrd=0x01000000,40960K init=/linuxrc lcdon=1 lcdid=9 lcdbpp=16 lcdpath=GE **combined_mode=ide** setenv lcdparam 
1,30000,5,1024,768,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000,D811003c|0x2,D811005c&~0x2
saveenvtextout 0 0 "Loading kernel" ffffff
fatload mmc 0 0 /script/uzImage.bin
textout 0 20 "Loading ramdisk"fffffffatload mmc 0 1000000 script/myram.gztextout 0 40 "Booting" fffffffatload mmc 0 4000000 /script/scriptcmdsleep 5bootm 0 
 
Made new scriptcmd with 
mkimage -A arm -O linux -T script -C none -a 0 -e 0 -n scriptcmd -d script.txt scriptcmd
 
and booted the easyPC linux from SD /script folder with the new scriptcmd,but nothing new.First boot are with "television snow" stopping,then shutdown + restart again is followed by fastrolling clear text on screen,but stopping at via_ata_interrupt.
Nice with positive thinking:) - you think,I work!
 
And celem,welcome back!

---

### Post by litch84 on 2010-01-20
I've just set up a linux-arm toolchain for compiling a new kernel.

It's compiling right now, fingers crossed!

Also found some random info on ARM and framebuffers, my main priority right now is getting (fresh) kernel support for that LCD... Once that's done everything else will follow with greater ease...

Although I haven't even looked for a JTAG / Serial header, but I cbf hacking up a serial cable and trying.

---

### Post by litch84 on 2010-01-20
> **litch84 said:**
> I've just set up a linux-arm toolchain for compiling a new kernel.

It's compiling right now, fingers crossed!

Also found some random info on ARM and framebuffers, my main priority right now is getting (fresh) kernel support for that LCD... Once that's done everything else will follow with greater ease...

Although I haven't even looked for a JTAG / Serial header, but I cbf hacking up a serial cable and trying.


Build failed, missing symbols.

Trying an earlier kernel 2.6.18.8...

---

### Post by InterPhase on 2010-01-20
> **PerChristensen said:**
> **InterPhase**
 
I changed nextvolumes easypc linux scriptcmd by making a .txt file like this:
 
setenv bootargs mem=112M root=/dev/ram rw initrd=0x01000000,40960K init=/linuxrc lcdon=1 lcdid=9 lcdbpp=16 lcdpath=GE **combined_mode=ide** setenv lcdparam 
1,30000,5,1024,768,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000,D811003c|0x2,D811005c&~0x2
saveenvtextout 0 0 "Loading kernel" ffffff
fatload mmc 0 0 /script/uzImage.bin
textout 0 20 "Loading ramdisk"fffffffatload mmc 0 1000000 script/myram.gztextout 0 40 "Booting" fffffffatload mmc 0 4000000 /script/scriptcmdsleep 5bootm 0 
 
Made new scriptcmd with 
mkimage -A arm -O linux -T script -C none -a 0 -e 0 -n scriptcmd -d script.txt scriptcmd
 
and booted the easyPC linux from SD /script folder with the new scriptcmd,but nothing new.First boot are with "television snow" stopping,then shutdown + restart again is followed by fastrolling clear text on screen,but stopping at via_ata_interrupt.
Nice with positive thinking:) - you think,I work!
 
And celem,welcome back!

Hi PerChristensen!

thanks for trying it out. Could you maybe try to set it to combined_mode=libata (its the 'older' implementation of IDE in the kernel)?

- InterPhase

---

### Post by InterPhase on 2010-01-20
> **litch84 said:**
> Build failed, missing symbols.

Trying an earlier kernel 2.6.18.8...

litch84, what exact symbols are missing?

- InterPhase

---

### Post by litch84 on 2010-01-20
> **InterPhase said:**
> litch84, what exact symbols are missing?

- InterPhase


All good, successfully compiled 2.6.18.8 kernel.

ran mkimage on it to make compatible uzLinux.bin, tho I haven't tested yet because I went looking for a serial header...

Well, I found a header, not sure what exactly it is...

4 pin header, +5V, GND, RX, TX.

USB matches for the 5v power rail / ground but its data pins are usually called D+ and D-
JTAG requires at least 6 pins....
RS232 can do 3-wire TX/RX but there no requirement for the +5v rail?


RX and TX run directly to the CPU card, GND to mainboard ground and +5v comes from the power area where the Batt plugs in...

Any ideas?

---

### Post by litch84 on 2010-01-20
FYI:

[http://www.ekengroup.com/en/product/index.asp](http://www.ekengroup.com/en/product/index.asp)

Original Manufacturer of the P70x boards.

Wonder if they'll email me a datasheet about debugging this damn thing....

---

### Post by PerChristensen on 2010-01-20
**InterPhase**
 
When using your **combined_mode=libata** instead of combined_mode=ide in the scriptcmd **one bypasses the "television snow"** and boot directly into txt mode without having to reboot.
Text roll fast,i can only see txt: probing /dev/something before rolling start and ends some 20 seconds later,with via_ata_interrupt.
 
I have tried to cut off u-boot header of nextvolumes uzImage.bin and then gunzip the original vmlinux, but cannot find out where to cut.Some mkimage tools add 64 byte,others 72 byte.
The u-boot header in uzImage.bin is made with a MontaVista Linux 2.6.10 tool,the hexeditor say.

---

### Post by PrFaas on 2010-01-20
> **litch84 said:**
> 
Well, I found a header, not sure what exactly it is...

4 pin header, +5V, GND, RX, TX.

USB matches for the 5v power rail / ground but its data pins are usually called D+ and D-
JTAG requires at least 6 pins....
RS232 can do 3-wire TX/RX but there no requirement for the +5v rail?


I have the same on my system. My guess: A header for connecting a serial/debug port: I actually have 'high hopes' of finding the u-boot 'console I/O' as low-voltage-RS232 signal on those pins. In my previous experience, the Toradex arm-board, u-boot 'talks/listens' via a serial port. On my system VT8500, the TX was at 3.3 Volts 'at rest' (WinCE booted..), i expect that the RX will also need a 0.0 / 3.3 volts signal (NB: and 5.0 Volts will probably be too much.... ).

NB: i just connected an oscilloscope to the tx pin and powered-up the machine: there is definitely something 'coming out' there that looks like serial communication. Still needs an RS-232 buffer so to see: signal levels seem like 3.3 volts, pulsed to 0.0 volts, as would be normal 'pre-buffer'.

After a few more measurements: looks like 115.2 KBaud: i see ~10 us pulse-width (my 'scope' is not phenomenal: 20 MHz audio-scope...) The 'talking' does not really stop after boot: when the machine is 'operating', i get more 'babbling' when i press the power-button. I'm 'running' with the keyboard removed, so the number of buttons i can press is a bit limited :)

---

### Post by litch84 on 2010-01-20
Hmm, do the levels go from 0 - 3.3v or -3.3 to +3.3 relative to GND?

Might be TTL, which would make sense because of the low volatage.

I've already got a TTL -> RS232 breadboard at home, I'll give it a shot tonight.

---

### Post by PrFaas on 2010-01-20
The 'rest' voltage of tx is 3.3 volts. It 'pulses' to 0.0 Volts...

I'll attempt some ASCII-graphics, but forgive the quality please :)

```

______      ____      _____    __ = 3.3 Volts
      \____/    \____/         __ 
                                  = 0.0 Volts

```
                            
Just hope that 'comes out right' :) The lower line is at 0.0 volts, the upper one at 3.3 Volts. Considering: The CPU is probably generating the signals; The CPU has 3.3 Volts supply (I/O) voltage; The 'usual' signal output for RS232 -before the RS232 buffer chip- is 'high' (our 3.3 V) when no data is transmitted; the start-bit is 'low' (0.0 V). I've repeated myself quite a few times here, hoping the message gets across :)

I'm thinking about either my 'standard' 74HCT14 with 100-Ohm series resistor at the output as RS232 buffer chip, or else let's see if i can get my hands on any of the more modern chips...

getting over-confident now: an attempt at a circuit diagram for an rs232-buffer circuit in ASCII:

```


tx (of board) ----|>o----|||||-----> rs-232 connector txd pin

with ---|>o---- = one of the 6 inverters of the 74HC14

and  ---|||||-- = a 100 Ohm resistor


```

For the receiver, i'd usually take another of the gates of the 74HCT14, with diode/zener/resistors at the input as protection, and -for this case- a voltage divider for 5.0 --> 3.3 Volts conversion at the output. That however is beyond my skill and competence to draw in ASCII....

---

### Post by Matriark TerVel on 2010-01-21
Thanks to all who have contributed to this thread. I've found it most helpful. I came across one of the 7" "smartbooks" today, and, by God, I'm going to run Linux on it if I have to drive myself insane in the process. :P

It would be a really nice gesture if Kaser would release their kernel code to the general public, but alas, I wouldn't look for that to happen any time soon. It would be very likely that if one bought one of their devices, they'd be able to request access to their SDK server, and thus, their kernel code. I would be more than happy to take that step, but the closest store I know of that carries that device is 100 mi. from me, and I don't want to drive 200 mi. just for a bit of code that's only going to help marginally anyway.

I will point out, however, that because they distribute the binary of their kernel to the general public, that they're required (as far as I remember) by the GPL to also give anyone who obtains that binary access to the source code upon request. However, I doubt that appealing to them from a legal standpoint will do much good. :(

That said, I've been messing with their kernel image a bit, and figured I'd contribute a bit of information myself. I may rehash a fact or two, but bear with me.

Here's a quick braindump on extracting the kernel image from the u-boot image:

```

$ mkimage -l uzImage.bin 
Image Name:   MontaVista Linux 2.6.10
Created:      Thu Sep 10 23:53:09 2009
Image Type:   ARM Linux Kernel Image (uncompressed)
Data Size:    1674288 Bytes = 1635.05 kB = 1.60 MB
Load Address: 0x00008000
Entry Point:  0x00008000
$ dd if=uzImage.bin of=zImage skip=64 bs=1 count=1674288

-- Look for gzip magic: 0x1f8b which immediately follows "Done, booting the kernel." ---

$ dd if=zImage of=vmlinux.gz bs=1 skip=12068 count=1662220 ; rm -f zImage
$ file vmlinux.gz 
vmlinux.gz: gzip compressed data, from Unix, last modified: Thu Sep 10 23:53:09 2009, max compression
$ gzip -d vmlinux.gz

```A more interesting fact is that the YF-700 shares similarities with the VT8430. According to the VT8430 datasheet posted in this thread, the memory region D820:0000 - D82F:0000 is used for UART 0. If you disassemble the code in the zImage, you'll find there's a routine that writes messages (e.g. "Uncompressing Linux...") within that region (i.e. to a serial port.) 

Thus, it's possible that the YF-700 (and vicariously, our little smartbooks) share more similarities with that platform. One could infer that the VT8500 is based on the VT8430.
Similarly, one could infer that the mystery port being discussed in the last few posts is indeed a serial port (although you couldn't be sure without actually interfacing with it.)

Eventually, I might try to do a bit of reverse engineering, and hopefully, start writing platform drivers (don't hold me to it.) :P If Kaser would release their code, or if someone would donate a YF-700 to me so that I can go through the proper channels to get access to it, it would save a great deal of time since we know that the CPU and framebuffer (at least) are very similar.

For the interested, here's how to dump the CE Roms (.nb0 files):
```

$ mkdir normal_nk ; wine dumprom.exe normal_nk.nb0 0x80100000 -d normal_nk > normal_nk.txt

```

dumprom.exe can be found at: [http://www.xs4all.nl/~itsme/projects/xda/dumprom.html]("http://www.xs4all.nl/%7Eitsme/projects/xda/dumprom.html")

The ROM images seem to contain most (if not all) of the platform-specific drivers in DLLs. ;)

---

### Post by litch84 on 2010-01-21
By all means good luck with the disassembly; I believe there's methods of torture more appealing!

Kernel 2.6.32.4 has quite a bit of support for AB926EJ-S cores,
- LCD PL011 support (Found in our chips: VT8500, WM8505)
- SD Card reader via AMBA support
- etc...

I'm re-compiling the arm toolchain from:
* [http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html](http://www.kegel.com/crosstool/crosstool-0.43/doc/crosstool-howto.html)

For those who are scared of compiling your own toolchain, you should be. The above link makes the headache into a mild itch at the back of your skull though, it makes it in to 3 easy steps:
1. Download Script
2. Run script relating to your ARCH (demo-arm.sh)
3. Make coffee (EDIT: Took me ~1 hour on a Quad Xeon P4 3.0)

To compile kernel 2.6.38 with gcc >= 4.x you'll need to hack the config file:
./crosstool-0.43/build/arm-unknown-linux-gnu/gcc-4.1.0-glibc-2.3.2/glibc-2.3.2/configure

Line 2275:
    3.[2-9]*|4.[01]*)
 Change to:
    [3-4].[2-9]*|4.[01]*)
 
Once that's done, I'll recompile the new kernel with the new support and see if I can get some LCD console action..

I'd be freakin lucky if it worked the first compile tho, so don't hold your breath.

---

### Post by Matriark TerVel on 2010-01-21
> **litch84 said:**
> By all means good luck with the disassembly; I believe there's methods of torture more appealing!

Kernel 2.6.32.4 has quite a bit of support for AB926EJ-S cores,
- LCD PL011 support (Found in our chips: VT8500, WM8505)
- SD Card reader via AMBA support
- etc...


Some would say it's worse than death, but for a true masochist of an engineer, it can be very rewarding. :evil:

The LCD support would be lifesaver to say the least. Saves me the hassle of reversing it, although I wish we had an external port for UART0. ;)

 What I've determined so far is the bit I mentioned about UART0 in my previous post, and now, I've confirmed that the DRAM controller is consistent with the VT8430.

> **litch84 said:**
> 
Once that's done, I'll recompile the new kernel with the new support and see if I can get some LCD console action..


I look forward to hearing how you fare.

---

### Post by nextvolume on 2010-01-21
Yeah, there are surely many similarities between the VT8430 and the VT8500. Also the RTC chip is the same, I tried writing values to the memory addresses for it with U-Boot before booting CE and it worked, I could set the time to 00:00 and to 23:28 by shifting the values accordingly in a 32-bit word and then writing them.

It's great that you went to disassemble the kernel. I had thought about doing that as well, to see where we have to modify it to make the PATA detection always fail, so at least we will have already a pretty decent remotely controllable Linux. 
Does that routine not do its own checksum on the gzip? If it does the check it's going to take another step. If it doesn't, it's as easy as extracting the image, modifying it, and then compressing it again.

Also, let our voices be heard, go to:
[http://www.viaarena.com/forums/showthread.php?p=250394#post250394](http://www.viaarena.com/forums/showthread.php?p=250394#post250394). 

It's me, just under another nick.

With this C function you should be able to generate the date value, day of week is still missing, though
> unsigned int generate_time_dword(unsigned int sec, unsigned int min, 
    unsigned int hour)
{
    // Day of week setting missing but if the date is 1/1/2000
    // just for testing it is not needed
    unsigned int time_val;
    
    if(sec >= 60 || min >= 60 || hour >= 24)
        return 0xFFFFFFFF; // A value is out of bound, return invalid
                           // value
                   
    time_val = sec - ((sec/10)*10);
    time_val |= (sec/10) << 4;
    time_val |= (min - ((min/10)*10)) << 7;
    time_val |= (min/10) << 11;
    time_val |= (hour - ((hour/10)*10)) << 14;
    time_val |= (hour/10) << 18;               

    return time_val;
}

---

### Post by litch84 on 2010-01-21
Made a TTL -> RS232 converter based on this schem:

[http://sodoityourself.com/max232-serial-level-converter/](http://sodoityourself.com/max232-serial-level-converter/)

Netbook won't switch on if it's connected. Went over my connections 10 times, no worky.

I'm assuming that the circuit detailed above, the caps are too big and draw too much current therefore overloading the rail and it fails to initiate boot.

Even plugging in the header to my circuit after it's booted instantly turn the unit off.

I don't have any .1uF caps lying around so that theory will just have to wait...

Since my area isn't so much electronics, I must ask if there is there a way I could integrate an external +3.3v rail to the MAX232 chip so that it doesn't rely on the netbook's supply?

Therefore proving my theory right/wrong?

---

### Post by nextvolume on 2010-01-21
There are some prebuilt RS232<->TTL circuits which are available on the internet.
Some don't cost much. Maybe you could try using one of those?

---

### Post by Digger Driver on 2010-01-21
> **litch84 said:**
> (FYI)

I've found another variety of these netbooks:
- The EPC branded ones.

[B]Hardware details:

[/B]    **Wireless Chip:**
  CHIP:     RT2070L
  PCB Label:       BL-RT3070-50
   
  **MiniPCI SoC: “P709_CPU_V3”**
  MCU: WonderMedia WM8505
  DDR2-800 128MB: Zentel A3R1GE4CFF
   
  **MOBO: P706_MAIN_V5**
  Sound: VIA VT1613 
Ethernet PHY: VT6103X  USB HUB: GL850G
  ?: HT-95A-1
  RAM/FLASH?: Samsung 943 – K96AG08UOM
   
  **Description / Notes:**
The unit also has a 7" LCD with a ARM926EJ-S based SoC. The Wireless module actually looks like someone ripped it out of a USB 802.11 stick and just wired it directly to a usb port. It sits on the RH side of the LCD screen, just above the speaker.

Wonder Media is actually owned by VIA and I'm guessing the WM8505 is the successor of the VT8500, WM also just released the WM8510, which is one step further again.

The system by default runs WinCE and features the ususal SD card slot, usb ports and inbuilt speakers etc...

I should have taken photo's but the main board (Labelled **P706_MAIN_V5**) But anyway, it has a mini-pci slot with a mini-pci card in it (Labelled **P709_CPU_V3**) it that has the SoC and RAM on board... Interchangable CPU's?

I've also been hacking up the scriptcmd file and trying to boot ANYTHING other than CE, but to no success. I came close to getting some random ARM826 based Thinclient imag to boot but it really doesn't like the integrated LCD.

Will take some photo's soon and will update on U-Boot progress.
Hi Guys, 
I'm hoping you can help me.
I'm trying to fix this smartbook Litch84 has described above and you guys seem to be the only people on the planet that know anything about them.
An old Lady friend of my Mum bought it online from Hong Kong.
When i firsrt started it up it gave the Smartbook Logo and loading OS but it had done that for two days.
I then tried the fix with the VT8500 on the SD card and it started to move but then froze after successfully loading the first 3 bits.
I turned it off and tried again and all i get now is a blank screen.
I know its a little off topic but if any of you Guys can help i would be most gratefull
PS please bear in mind i'm not a Up to your standard of experience so you might have to use baby talk.:D
Cheers.
Digger.

---

### Post by celem on 2010-01-21
> **PrFaas said:**
> ...For the receiver, i'd usually take another of the gates of the 74HCT14, with diode/zener/resistors at the input as protection...

A divider of 12k and 18k resistors yields 3.3v at the junction. Also consider a 74LCX245 buffer which is a 5-volt tolerant device.

---

### Post by litch84 on 2010-01-21
I've just spent nearly 12 hours straight on this; here's what I've done so far (to no avail):
- Managed to find a few resistors and give an approximate 3.3v to my little RS232-TTL converter - No data at all.
- Built a 2.6.34.x kernel with all the support for the SoC - Dead
- Built a 2.6.28.10 kernel with the configs off [www.arm.com](www.arm.com) - Dead
- Various different config options, recompiled kernel, etc...
- Made a RS232 null modem cable with some leads I had lying around, compiled a kernel with USB-Serial support for the chip I had (PL2303) - No data.
- Used RealView-Versatile kernel images from [www.arm.com](www.arm.com) - Dead

[U]@PrFaas:
_You said the TX was normally high (+3.3v) does this need to be inverted before it gets to the MAX232 input?_ It should still spit out garbage if that's the case, shouldn't it?
[/U]

---

### Post by PerChristensen on 2010-01-21
**Matriark TerVel**
 
Pls. check your inbox

---

### Post by Matriark TerVel on 2010-01-21
> **nextvolume said:**
> Yeah, there are surely many similarities between the VT8430 and the VT8500. Also the RTC chip is the same, I tried writing values to the memory addresses for it with U-Boot before booting CE and it worked, I could set the time to 00:00 and to 23:28 by shifting the values accordingly in a 32-bit word and then writing them.

It's great that you went to disassemble the kernel. I had thought about doing that as well, to see where we have to modify it to make the PATA detection always fail, so at least we will have already a pretty decent remotely controllable Linux. 
Does that routine not do its own checksum on the gzip? If it does the check it's going to take another step. If it doesn't, it's as easy as extracting the image, modifying it, and then compressing it again.


I figured if the DRAM controller was similar, the RTC would be as well. You just saved me the time of reversing the RTC driver. ;)

IIRC there's a CRC32 checksum in the zImage, but you can decompress it. You can't just recompress it with gzip without patching the sizes and the CRC. It'd be much more worthwhile, IMHO, to just use mkimage with the uncompressed image if you wanted to create a new u-boot image.

> **nextvolume said:**
> 
Also, let our voices be heard, go to:
[http://www.viaarena.com/forums/showthread.php?p=250394#post250394](http://www.viaarena.com/forums/showthread.php?p=250394#post250394). 

It's me, just under another nick.

With this C function you should be able to generate the date value, day of week is still missing, though

Our voices will be heard indeed (when we have open source platform drivers!) ;) With the VT8500, I wonder why VIA went all tight-lipped, but at any rate, hopefully very soon it won't much matter. :P

@litch84:
The platform is quite different from the Versatile boards (and any other currently supported platform), and thus will need its own platform drivers. There may be a piece of hardware here or there that's supported already, but the core platform won't be just yet. :P

Everyone, also take a moment to thank PerChristensen. He's decided to donate a YF-700 to me, which will make our lives much easier. :) It will save me a tremendous amount of time, and bring us one step closer to having open source platform drivers, and support for our little "smart books."

If and when I get something implemented, I'll setup a new fork at Github. At that time, I'll also setup a site for the project on my domain: [http://hentenaar.com](http://hentenaar.com) :)

---

### Post by PrFaas on 2010-01-21
> **litch84 said:**
> 
[U]@PrFaas:
_You said the TX was normally high (+3.3v) does this need to be inverted before it gets to the MAX232 input?_ It should still spit out garbage if that's the case, shouldn't it?
[/U]

First thing to check would be a simple DC voltage measurement between the gnd and tx pin of your board. I found 3.3 Volts there. If you have one, connect an oscilloscope at those same two pins: i found 3.3 Volts, pulsed to 0.0 Volts, pulse width about 10 us. Pulses happen upon boot of the 'mini', and also -once booted- when i press the power button. 

Next thing: connect your max232 RS232 buffer, but please do not connect the rx pin: a max232 has 5.0 Volts output, and connecting that to the 3.3 Volts input of the CPU is *not* a good idea.... I remember you mentioned that the machine did not repond if you've got that connected, and frankly i'm surprised the CPU chip can survive that kind of input signals.... The rx driver would only be usefull if there is an u-boot 'listening' anyway. Usually, u-boot gives you a chance to 'interrupt' its preconfigured autoboot, and that's where an rs232 input comes into play. When you just want to 'listen' to the communication that's coming out of the 'mini' (my name for these small computers) a tx circuit is enough.

Next: Check on the output of the MAX232: I'm not sure that a max232 is the best chip for the job: it could be that 3.3 Volts is not enough to be seen as 'high' by the max232 :-/ The max232 output should be about -10.0 Volts, pulsed to +10.0 Volts, 'in sync' with the pulses on the tx pin. As far as i know, you'd not need any inversion between the tx signal and the max232: the 'traditional' serial port output signals are also 'high', pulsed to 'low', just like what i've seen here. If that fails, your max232 is probably not a good driver for this application: I have spent a few minutes on looking for another driver chip, (Lineair Techonolgies has some nice 3.3Volts-compatible ones..), but have not decided upon which one to use yet. I think i'll try the 74HCT14 first (the coming weekend..): it is my prefered rs232 driver. The resulting signal -at the rs232 pins- is not entirely conform the rs232 spec, but the 'driver chip' (74HCT14) is high-speed, and about completely zero-power: very nice for this kind of battery-powered system. Besides: the resulting output is very resistant to short-circuit: the 100 Ohms resistor limits the current when the output driver inverter's signal is 'high', and when -as most of the time- the output is ~0.0Volts, there will be about no current at all if you'd 'short' the 'rs232-buffer'. 
I've found that about all inputs of 'normal' rs232 buffers are compatible with this solution, so long as you do not try to drive an all too long cable with the 74HCT14 as rs232 buffer chip.

A next step would be to connect the rs232 signal to a 'kermitted' real rs232 port, check the baudrate, and see if the signals make any sense :)

---

### Post by nextvolume on 2010-01-22
It is great if they're going to give us open source drivers (and if they are, can someone contact me privately?), but if they gave us the specifications it would be better. I don't feel like reversing source codes just to get a small grasp of how the hardware works in case I want to port another OS like NetBSD, etc.

---

### Post by PerChristensen on 2010-01-22
Not to be oversensible,but we must remember technical info on the net is overlooked by people trying to prevent serious crimes to happen and can interfere with investigation.
Our intentions and goals are all to the best of others,and according to open source agreement users of the Linux system is obliged to release the source code for any binary if asked for,I have allways understood.
 
Based on communication regarding the KASER not given here I feel we could have created unnecessary fear with our activity,especially in the light of risen alertness at UK government today.
 
I suggest we relax some days and continue when alertness hopefully has gone to a lower level shortly.Smalltalk should not be a problem,as I see it.
 
I will remove my "avatar" now.

---

### Post by celem on 2010-01-22
> **PerChristensen said:**
> ...we could have created unnecessary fear with our activity...
I will remove my "avatar" now...

Is there a side conversation that I am unaware of? I really don't understand your post? And, is removing your avatar related to this "fear" issue?

---

### Post by corruptbinary on 2010-01-22
and i agree with nextvolume, i would like to have the datasheets/docs for the vt8500/8505, my arm assembly is a little rusty tho.  I would settle for the source tho. actually i would like both...


Matriark TerVel:  i also started on tibasic and extended basic on the ti-99/4a wwaayyy back, i "upgraded" from a 16bit/16k machine to a vic-20 8bit with 5k so i could program in assembly which i couldnt do on the ti unless i bought a expansionbox, disk drive, cartridge,etc...obviously i liek to be able to tinker with stuff i buy...kinda like this netbook!

---

### Post by nextvolume on 2010-01-23
I really don't get you PerChristensen, I don't know what your avatar could do (other than for being Lenin, but I don't think the UK govt wants to bust us for being supposedly "red").
I don't think our rights upset them much either.
PerChristensen, send me an email if there is a side conversation, and I will report back to the community if it has to be done. I don't think following a closed path for something that's our right (namely GPL sources) is a good path to follow. The sources will only make Kaser sell many more products, anyway.

---

### Post by Matriark TerVel on 2010-01-23
> **corruptbinary said:**
> 
Matriark TerVel:  i also started on tibasic and extended basic on the ti-99/4a wwaayyy back, i "upgraded" from a 16bit/16k machine to a vic-20 8bit with 5k so i could program in assembly which i couldnt do on the ti unless i bought a expansionbox, disk drive, cartridge,etc...obviously i liek to be able to tinker with stuff i buy...kinda like this netbook!

It's interesting to hear of someone else who got their start the same place I did. I had the expansion box, and the whole deal. The only peripherals I didn't have were the thermal printer and the TI monitor. :P Nowadays, I only have the console and the speech module.

There's a book called "TI-99/4a Intern" that gives a tremendous amount of insight into the internal workings of the TI, as well as a disassembly of the console roms. :) Have you read it? There is a link to it on my website.

I've always been one to tinker as well, and the "smart book" is no exception. :P

---

### Post by PrFaas on 2010-01-23
Test-report w.r.t. those pesky gnd/tx/rx/5v pads:

I made (or rather re-used/modified) a rs-232 buffer/driver circuit for that. I'll spend some moments on making a circuit diagram of my circuit later, those who have one of the 'orange' boards with those pads can have their own fun :) . I did use an independently-supplied buffer/driver circuit meaning: my 3.3 Volts <-> rs232 circuit has its own supply voltage, i did not use the 5V supplied by the 7" computer. 

So far i can report:

- those pads are the u-boot serial console interface
- they work ok with serial settings 115200,n,8,1
- u-boot of my machine has a 1-second 'window' for interrupting the u-boot, and getting 'manual' control of u-boot.
- 'our' u-boot does have full support for netbooting.

I must mention that i only have wm8505 machines, no via vt8500 anymore (does that mean that i'll have to look for a different 'forum'/thread to report? :) ).

I'll attach the traces, with editing/comment, of an uninterrupted boot/shutdown cycle, as well as one where i've interrupted u-boot's 'good work', and played with u-boot commands and attempts to netboot. I do *not* have any of the servers -as mentioned before- 'in place'. Nor do i have a bootable kernel image, and i've even let -in great contrast to my own advice of the earlier writing- my router provide an IP address. This is just preliminary 'playing' with u-boot, to see if it actually gets 'on-line', little more.

---

### Post by PrFaas on 2010-01-23
oops, i thought i could attach the 2-nd trace later, sorry, but now i have to make two posts :roll:

BTW: any suggestions for an 'easy' program to draw circuit diagrams with? I can offer either kde3 or kde4 as default environment :)

---

### Post by Matriark TerVel on 2010-01-23
> **PrFaas said:**
> oops, i thought i could attach the 2-nd trace later, sorry, but now i have to make two posts :roll:

BTW: any suggestions for an 'easy' program to draw circuit diagrams with? I can offer either kde3 or kde4 as default environment :)

Great work! I figured that was a serial port. :P Now those traces do give us some insight.

I used to use gEDA to draw circuit diagrams, there's an old Linux Journal article at [http://www.linuxjournal.com/article/8438](http://www.linuxjournal.com/article/8438) . You could also use dia I suppose. As for KDE, I'm not familiar with any such programs for KDE, though there may be some. :P

If you get a diagram together, I'd love to see it and build an interface. It would be most helpful, I think. :)

I'll have to see if I can somehow acquire a VT8500 model. One of my clients has a WM8505, and a friend of mine had the VT8500 model but he gave it away the other night (which was rather irritating considering I was planning to use it to test with.) :P

---

### Post by DonutFUN on 2010-01-23
So what ended up happening with this forum? did you get linux on it? and if so do i have to format and redo the hole thing?
 
Sorry I just don't want to read all 20 pages.
 
What i'm hoping for is jsut having Linux on my sd card, have it in when I want to boot into it, and take it out to boot into Windows CE if possable. is it?

---

### Post by Matriark TerVel on 2010-01-23
> **DonutFUN said:**
> So what ended up happening with this forum? did you get linux on it? and if so do i have to format and redo the hole thing?
 
Sorry I just don't want to read all 20 pages.
 
What i'm hoping for is jsut having Linux on my sd card, have it in when I want to boot into it, and take it out to boot into Windows CE if possable. is it?

We're still quite a way away from that, but it will be possible. Relax, and be patient. Hopefully soon it'll be just that simple (that's what I'm aiming for.) :)

---

### Post by DonutFUN on 2010-01-23
allright, thanks for the hasty responce, I'll just keep track of this when I can, good luck to you, and by the way, when you get there what are the odds of me being able to play stuff like Diablo and Half life and star craft? since all of thoes games can run on the specs.

---

### Post by Matriark TerVel on 2010-01-23
> **DonutFUN said:**
> allright, thanks for the hasty responce, I'll just keep track of this when I can, good luck to you, and by the way, when you get there what are the odds of me being able to play stuff like Diablo and Half life and star craft? since all of thoes games can run on the specs.

The chances of playing games like those is quite low, I'm afraid. They just aren't powerful enough (not to mention these are ARM machines, not x86 machines.) :P

---

### Post by PrFaas on 2010-01-24
> **DonutFUN said:**
> So what ended up happening with this forum? did you get linux on it? and if so do i have to format and redo the hole thing?
 
Sorry I just don't want to read all 20 pages.
 
What i'm hoping for is jsut having Linux on my sd card, have it in when I want to boot into it, and take it out to boot into Windows CE if possable. is it?

Quick resume then (feel free to flame mistakes, add if i forget anything :) )

It is not really *one* machine:

+ There are several versions of this machine, that do not appear to differ when looked at from the outside, but that have *some* subtle differences 'inside'. CPU's found so far: VIA-VT8500 and WonderMedia-WM8505; Difference between them are unknow. I've seen only orange boards with 'plug-in' CPU module, but we've also seen reports/fotos of blue boards with the CPU 'fixed' on the board.

The machine seems hardware-wise capable of running linux: 
  
+ arm CPU/System-On-Chip (SoC): mind you *not* x86-compatible, it will *not* run 'default' pc-binaries, applications *will* need a compile for arm. That *does* rule out most apps that are not available in source.
 
+ 128 MB RAM: is enough if you don't do 'anything silly'

+ 2Gig 'disk': idem, potential for expansion with sd-cards and USB 'sticks'

+ WiFi: it has an 'embedded' USB-stick: Ralink-2070, in the display unit, hard-wired to one of the USB ports, power on/off by means of a digital output pin of the CPU.

+ keyboard: appears to have a standard PS/2 controller chip

+ video: nothing really special: seems to be supported by the default arm-video-driver. Some snow has been reported when attempting to show something there, but it's also worked 'good' at times. We know the frame-buffer address.

+ sound: too early to tell...

+ USB: idem, the CPU itself has USB-port(s?), so i'd expect 'in-kernel' support for the ARM-USB.

+ LAN: probably not a real problem: looks like the on-board LAN interface of the arm-cpu is used.

+ SD-card: works ok foor booting/bootloader, can't tell yet if it will work with a linux kernel, but this will probably be ok.

+ touchpad: yet unknown...

+ i've done some net-searching of the 'other' chips on my board, and i've been able to find datasheets of about all of them. Painfully lacking however is the datasheet/interface spec of the CPU: VIA (now WonderMedia) is not willing to provide it. I'll return to that 'later'.

+ This machine is based upon a System-On-Chip (SoC). The bad news: the maker is unwilling to give us a datasheet; Good news: he seems to have used a lot of 'from-arm' 'ip-modules' when 'composing' the  SoC; Most 'from-arm' modules also appear in other arm-chips, and most of them are supported by the kernel.org kernel. We'll see how much of the 'in-SoC' hardware is auto-detected :)

BIOS/bootloader:
 
+ The bootloader is a 'linux-native' one: u-boot. Mine does support netbooting; Something i value for development work.

+ The bootloader is 'hidden' in the 8-pins 512-KBytes SPI chip that is located near the CPU. It is probably loaded into memory by the CPU chip firmware. That means that it will not be very easy to 'brick' these machines: The bootloader is not in the 'main flash', but at a 'safe location'.

+ The bootloader has a mechanism that supports 'hooking': for software updates, it can -before booing into WinCE- load/burn/start programs from an SD-card. That -in theory- should be enough to allow us to make it boot & run linux from an SD-card, without having to 'destroy' the contents of the 'on-board' 2Gig 'disk'

+ Some of 'us' have already managed to use the above-mentioned mechanism to boot (or should i say: half-boot) a linux kernel that was pre-compiled for a slightly different set of hardware. That kernel got into problems when it attempts to access a hard-disk: there is no such thing on this machine (yet? :) ).

Development tools:

+ crosstools as been mentioned: a set of scripts/patches for setting up a compiler for the arm target. NB: i too have a 'home-brew' toolset now. That should allow us to build our own kernels for this machine. Here, however, the lack of clear documentation of the machine's CPU (really an 'all-in-one-chip') might prove troublesome. We know that the CPU is -instructionset-wise- compatible with an ARM-926EJ, but the lack of documentation means we have a bit of 'guess & gamble' work to do to find out how the I/O is 'connected' (inside the CPU chip).

+ i've seen some mention of attempts/ideas to request sources of the GPL-ed software that's inside this machine (u-boot is gpl as far as i know), but no definite results yet.

Feel free to add/correct, but that's -as far as i know- the 'state of the art' at the moment. We're not there yet, but getting closer :D

---

### Post by litch84 on 2010-01-24
PrFaas: Brilliant!

Please post that 3.3v schem, as I'm eager to get this kernel booting properly!

I'd attach the kernel image that I've build but max upload is ~950K and the bin file is 1.4MB...

I'll try upload it to anther site and reference soon.

_+ sound: too early to tell..._
Via based AC97, I've listed the chip in an earlier post.

_+ LAN: probably not a real problem: looks like the on-board LAN interface of the arm-cpu is used._
Also VIA Rhine based

_+ SD-card: works ok foor booting/bootloader, can't tell yet if it will work with a linux kernel, but this will probably be ok._
I'm confident the Linux kernel will pick it up since there's a direct option to compile in SPI based SD Card readers and other flash based devices via AMBA / SPI access.


EDIT:

The latest kernel 2.6.3x has heaps of support directly for the "demo board" SoC as noted in the documentation. Frame buffer integration might take a bit of tweaking but serial console access should be good to go out of the box, since it's unlikely they've changed that from the demo board SoC's to the WM8505...

---

### Post by PerChristensen on 2010-01-24
**celem**
 
Online with credit card I bought a KASER at Educational Resources,Illinois,and asked for shipping to Matriark TerVel in Ohio.I got mail,order will be processed asap.
Nothing hapened,and I called to be sure everything was OK.Had to go through taped interwiew before they asked me to wait - and after several minutes broke the line.A new call to the (obvious nervous) clerck saying "order was in the system" and end of conversation.
 
By now no movement on my account ,and no new mail from Educational Resources neither.
 
For me it look as if Educational Resourses either will not process the order,or I cannot use my credit card overseas.Or there could be another simpler reason.

---

### Post by Matriark TerVel on 2010-01-24
> **PerChristensen said:**
> **celem**
 
Online with credit card I bought a KASER at Educational Resources,Illinois,and asked for shipping to Matriark TerVel in Ohio.I got mail,order will be processed asap.
Nothing hapened,and I called to be sure everything was OK.Had to go through taped interwiew before they asked me to wait - and after several minutes broke the line.A new call to the (obvious nervous) clerck saying "order was in the system" and end of conversation.
 
By now no movement on my account ,and no new mail from Educational Resources neither.
 
For me it look as if Educational Resourses either will not process the order,or I cannot use my credit card overseas.Or there could be another simpler reason.

I've never had a problem using my credit card when I've been overseas (although the 3% conversion fee can be painful.)  I'm certain such a transaction must seem odd to them, as they're probably not used to processing such orders. That might help explain any nervousness on their part, or perhaps they suspect fraud of some sort. You may have to follow up with them a time or two more. But, there's no need to be alarmed. :P

If they won't process the order, that would be discouraging. However, I'm certain there are other retailers that would be willing to do so, assuming of course you're still interested in donating one. :) Fry's Electronics should carry them, but they don't have them SKU'd on their website.

---

### Post by PrFaas on 2010-01-24
Be ready for another long post. :) the circuit diagram & description of the RS232 buffer; I've also attached the 'meat' as a text-file for in case the forum-software 'mangles' the text all too badly...

Oh, and before i forget: no warrany, at your own risk and 'the usual' w.r.t. blasting your little computer to 'kingdom come' :) I've done my best to produce a correct circuit-diagram, but that's all i can promise...


It is going to be ASCII-'art' for the circuit diagram i'm afraid :-/

Fortunately, it is a rather basic circuit, so there is even a chance 
that the result will be understandable. The diagrams are all 
going to be 'left-to-right': the pads of the 'mini' computer at the 
left, the pins of the RS232 connector at the right.

I've attempted to keep the description at about the level of 'my first 
soldering experiment', so all you electronics-tigers please be a little
patient with my 'baby-steps' in the description :)

The basis of the circuit is a simple 74HCT14: a hex schmitt-trigger 
inverter. We'll use only 2 of the 6 inverters in the 'package'. The
chip is quite basic, and can be gotten in both DIL and smd package.

The pin-out of the 74HCT14 is as follows:

```


            as seen from the top of the package

                  +--v--+
          in1    -|     |- 5.0 volts
          out1   -|     |- in4
          in2    -|     |- out4
          out2   -|     |- in5
          in3    -|     |- out5
          out3   -|     |- in6 
          gnd    -|     |- out6
                  +-----+

             pin-out of the 74HCT14
             ----------------------

```

in1 is the input of the first inverter,
out1 is the output of the same inverter

the same applies to in2/out2 etc...

The transmitter buffer is little more than an inverter with a series-
resistor in the output line. The resistor is to limit the current from
the inverter's output in case of short-circuit. 

```


      1/6 74HCT14               100
tx o-------|>o-----------------|||||----------o RS232 RXD (pin 2)


       transmitter buffer
       ------------------


```

The receiver is a little more complicated: the part on the right is to limit the
input voltage range of the inverter to the 0.0 .. 4.7 Volts range. RS232 *could*
have voltage levels between -12.0 and +12.0 Volts and that is a bit too much
for the invterter's input. The diode blocks out the negative voltages, the 10K
resistor limits the current through the 4.7 Volts zener diode. The Zener diode 
itself limits the positive input voltage of the input of the inverter to below 
the 5.0 Volts supply voltage of the inverter. The 330K resistor ensures that the 
input voltage of the inverter drops to 0.0 Volts if no positive input voltage from
the RS232 signal is present.

At the output of the inverter, the 27K/47K resistor divider limits the output 
voltage of the receiver to 3.3 Volts; I found 3.3 Volts at the tx pin of the 
computer and have assumed that i'd better keep the voltage of the signal into the
rx pin to the same 3.3 Volts. The diode over the 27K resistor is a bit of a late
addition: i found on the oscilloscope that the output voltage of the receiver 
-when connected to the rx pad- did not drop low enough. I think there is a 
pull-up resistor at the rx pin, and my rather high-impedance output voltage divider
was unable to pull the rx pin all the way to 0.0 volts. With the extra diode, the 
rx signal is pulled 'low' to about 0.7 Volts. That seems enough to be seen as 'low'
by the rx input. I would have prefered to use a shottky diode, but i have none in 
the house.... :) 

```


              1N4148
         +------|>|------+
         |     27K       |                 10K     1N4148
rx o-----+-----|||||-----+-----o<|---+----|||||-----|<|-----o RS232 
         |     47K                   |   4.7V zener           TXD (pin 3)
         +-----|||||-----+           +-----Z|<|-----+
                         |           |     47K      |
                        ---          +----|||||-----+
                        ///                         |
                                                   ---
                                                   ///


      receiver buffer
      ---------------

legenda:

------|>|------  = diode

------|>o------ = inverter

-----|||||----- = resistor

-----|>|Z------  = zener diode, Z-side is the '+' 

 |
---             = connection to gnd
///


```

A 74HCT14 has 6 inverters in one package. Two of them are used for this circuit. It
is advisabe to connect the inputs of the 4 remaining inverters to either the 5.0 Volts,
or to gnd (makes little difference which one, just so long at they are not kept 
'floating'/unconnected).

The supply voltage of the 74HCT14 can be 'taken' from the gnd/5V pads of the computer 
board. I have not yet tried that myself, but this circuit is vert low-power, so i expect
few problems there.

Remains a few connections of the RS232 connector to make things really work: RS232 has a
few 'control lines' that can be used to 'start/stop' the transmission. Since we have no
equivalent I/O at the computer board, i've interconnected them in such a way that a device
connected at the RS232 port always gets a 'permission to send' at all times. another thing
is that we will have to connect the RS232 GND signal to 'our' gnd signal:
My circuit ends in a 9 'pins' female sub-D mini connector; You'd usually
find the equivalent 'male' counterpart used as an RS232 connector at the
back of a computer.
 
```


RS232 sub-D mini 9-pins female connector pins:

           5 4 3 2 1
         -------------
         \ o o o o o /    as seen when looking 
          \ o o o o /     into the 'holes' of 
           --------       the connector
            9 8 7 6


           1 2 3 4 5
         -------------
         \ o o o o o /    as seen when looking 
          \ o o o o /     at the back (cable side)
           --------       of the connector
            6 7 8 9

pins descriptions:

pin 1 = control signal (DCD), connect to pins 7 and 8
pin 2 = RS232 RXD <-- transmitter circuit output
pin 3 = RS232 TXD --> receiver circuit input
pin 4 = control signal (DTR), connect to pin 6
pin 5 = connect to gnd
pin 6 = control signal (DSR), see pin 4
pin 7 = control signal (RTS), see pin 1
pin 8 = control signal (CTS), see pin 1
pin 9 = control signal (RI), not used


In ASCII-'art':


   +----o RS232 pin 5
   |
  ---
  ///

   +----o RS232 pin 4
   |
   +----o RS232 pin 6

   +----o RS232 pin 1
   |
   +----o RS232 pin 7
   |
   +----o RS232 pin 8

    additional connections at the RS232 sub-D mini 9 connector
    ----------------------------------------------------------

```

I hope that this is enough info to duplicate the circuit... ASCII-'art' is not
the best graphics tool, and if anyone finds the time to make a nice 'png'/'gif'
or whatever of this, i'd be most gratefull :) I did try out a few graphics
programs for 'the same', but found that this was the fastest way for me to get
a description of the circuit. Now, i just hope i've not made too many mistakes :)

NB: i use 'minicom' running on a Linux machine as the 'other end' of the 
communications link.

---

### Post by PerChristensen on 2010-01-24
I will give them a call at Educational and cancel the order if not heard anything from them in next 3-4 days

---

### Post by tlk23 on 2010-01-24
PrFaas,
I'm sure if this fits within your summary or not, but here are some details of my different machine.
 
I think it is a Lan Yu  LY-EB01
 
Same case as the others, but different processor and motherboard.
 
Processor is soldered to the motherboard. The 802.11 wireless nic is a daughter board.  It seems the computer can be delivered with other forms of wireless (3G), hence the easily replaceable nic.
 
System properties (reported by Windows CE)
System:
Microsoft?Windows?CE
Version 5.00 (Build 1400)

Computer
Processor Type: AKARM, ARM926-AKCHIP
Expansion Slots:
Memory 128M

----

System Specs:
Processor: ANYKA AK7802TQ21605
NAND Flash: K9GAG08U0D (2GB)
Ethernet Controller: Davicom DM9008AEP
Wireless NIC: Prolink RT2070L (Realtek RT2870 clone?)


Number on Motherboard: ZT_NT670_V88_FPC_1018

I've attached two pictures of the motherboard

---

### Post by sleeky24 on 2010-01-24
tlk23 - that board looks the same as mine, which I beleive is similar to the one in the 'CMN Book'.
 
Just had a look on the Anyka site (was down the other week) and I beleive this board is this:
[http://www.anyka.com/enProShow.asp?id=87&sortName=Hot-Product&sortFlag=113](http://www.anyka.com/enProShow.asp?id=87&sortName=Hot-Product&sortFlag=113)
 
Perhaps we could request more details on the specific board?

---

### Post by PrFaas on 2010-01-24
So: we now have the colours blue, yellow and green ;)

On a more serious note, a slightly different CPU (another arm-926-like though..) and a different LAN chip... Your LAN-chip appears to be a real/complete ethernet chip. A 10 MBps one for UTP as far as i can see, but it does support 100MBps on fibre network :) 'Mine' is a so-called PHY chip: only the interface from a 4-bits-wide datastream to the UTP interface. In the VT8500/WM8505, the equivalent of 'other half' of the LAN chip is part of the CPU chip. Concluding from that, i'd say that 'your' CPU is really a bit different from the VT8500/WM8505. Other than that, your machine looks really like 'ours' :)

Does your board also show traces of a serial interface? Just curious...

---

### Post by PrFaas on 2010-01-24
> **litch84 said:**
> PrFaas: Brilliant!

Please post that 3.3v schem, as I'm eager to get this kernel booting properly!

I'd attach the kernel image that I've build but max upload is ~950K and the bin file is 1.4MB...


Could you 'post' the kernel '.config' & version number please. That would give some reference as to what you've configured and what you've compiled. A .config should only be a few kbytes, safely below the 'limit'.

---

### Post by celem on 2010-01-24
I was poking around on eBay and found a HongKong company listing a machine very, very similar to our machines. It has the same exterior, 2GB NAND disk and 256MB RAM. It uses an ARM1176JZF-S SoC. But it comes with your choice of **Linux** or Windows. Their price for quantity one is too high but they seem to have a viable Linux ARM kernel.

eBay Listing: 
[http://tinyurl.com/ykqvrny](http://tinyurl.com/ykqvrny)

---

### Post by DonutFUN on 2010-01-24
Hey, I'm sorry if I'm being distracting or just asking stupid questions, but since I do have the software pack of the internet that does reformat it to its system defaults, what do I do do boot off of that without losing all of my stuff, say I set the background to big (which I've done, if you set it to a higher resolution it crashes) and just want to delete the picture without losing other stuff I've put on it, so I just delete the "AutoRun.exe" to make it just boot off of the SD card? or will it just format over it no matter what?

---

### Post by litch84 on 2010-01-24
> **DonutFUN said:**
> Hey, I'm sorry if I'm being distracting or just asking stupid questions, but since I do have the software pack of the internet that does reformat it to its system defaults, what do I do do boot off of that without losing all of my stuff, say I set the background to big (which I've done, if you set it to a higher resolution it crashes) and just want to delete the picture without losing other stuff I've put on it, so I just delete the "AutoRun.exe" to make it just boot off of the SD card? or will it just format over it no matter what?

Inserting the SD card with the default software supplied on it will format the system flash, anything you have saved on the 2GB internal flash will likely remain 'as is'.

Booting in to the thin client Linux thats listed on this site may allow you to access the system partition if you've saved anything on that.. But the process is rather complex to log in remotely, mount the desired partitions and transfer the files via what ever application is available.

Read the previous threads on how to log in to the Linux distro via the network, once you get that far do a:

# cat /proc/partition

This will list the available partition you can mount. One of them will be the drive you saved everything to.

For each entry like /dev/sda1 etc, try:

# mkdir /mnt/sda1
# mount -t vfat -o ro /dev/sda1 /mnt/sda1

If it succeeded, you can change directory to that mount folder and browse:

# cd /mnt/sda1
# dir

Since I haven't bothered booting that linux yet, I can't tell you if it has SCP or TFTP or FTP but one of those application can be used to copy what ever files you wish to keep off the Netbook and on to what ever your using to access it.

---

### Post by litch84 on 2010-01-24
Kernel .config attached.

Kernel version 2.6.28.10 with this patch applied:
* [http://www.arm.com/products/os/linux_download.html](http://www.arm.com/products/os/linux_download.html)
* (File: Patch-2.6.28-arm2.gz, about half way down page)

My config based on the original .config under the above link, section "RealView Versatile PB926/AB926"

Built with: 
* [http://www.codesourcery.com/](http://www.codesourcery.com/) EABI toolchain for ARM 926EJ-S
* (Note: build it from source! Binary installer doesn't help at all)

---

### Post by Matriark TerVel on 2010-01-25
> **PrFaas said:**
> Be ready for another long post. :) the circuit diagram & description of the RS232 buffer; I've also attached the 'meat' as a text-file for in case the forum-software 'mangles' the text all too badly...

Oh, and before i forget: no warrany, at your own risk and 'the usual' w.r.t. blasting your little computer to 'kingdom come' :) I've done my best to produce a correct circuit-diagram, but that's all i can promise...


It is going to be ASCII-'art' for the circuit diagram i'm afraid :-/


Based on your ASCII art, and description I've rendered the following image with gschem. It may be easier for some and/or more difficult for others to follow.

It's been a while since I've used gschem, but I hope it hits the nail on the head. :P

---

### Post by PrFaas on 2010-01-25
Thank you for taking the trouble to convert my ASCII-art to a more decent diagram :)

Only one remark w.r.t your 'schema': i did mention to connect the inputs of the unused inverters to either 5V or gnd; I should perhaps have put that in the diagrams as well :D. The reason for connecting them is that the unused inverters could start to draw quite some current if their inputs are left floating. I'm not *very* sure that is actually needed with the HCT-ttl series, and with a schmitt-trigger input it could even be quite unneeded, but:

- it does no harm
- from my experience with HC and similar C-mos circuits, i found that is is sometimes really needed.....

NB: the worst i've ever seen was with an S-ttl chip, where the chip was completely destroyed, and the only possible reason i could find was that a number of inputs of an unused flipflop on the chip where unconnected. 

The 'meat' of the cirsuit seems ok to me, but i must admit that i've not triple-checked the interconnections of the RS-232 control lines

Oh, and on very close inspection: on my board, the 'order' of the pads for the RS-232 is different from what you indicate on the schema; Could well be that 'what you draw is what you see' on your board, but on 'mine' the pins are gnd, tx,rx,5V in that order, from left to right.

---

### Post by nemezisplk on 2010-01-25
Hi!
Could somebody tell me what type (model) of lcd are in this netbooks.

Thanks!

---

### Post by Nhyckolah on 2010-01-25
Hej hej!

I recently bought the netbook equipped with the ARM-VT8500 and I tried everething you said about how to fix the keyboard/mouse problem but i didn't manage to make it work. Does't anybody know how I can figure out if the problem comes from the keyboard or the motherboard?
By the way I'm also looking forward for a Linux version to be available for our mini netbook.

Thanks;
[IMG]http://www.qtl.co.il/img/copy.png[/IMG]

---

### Post by litch84 on 2010-01-25
> **Nhyckolah said:**
> Hej hej!

I recently bought the netbook equipped with the ARM-VT8500 and I tried everething you said about how to fix the keyboard/mouse problem but i didn't manage to make it work. Does't anybody know how I can figure out if the problem comes from the keyboard or the motherboard?


If the software restore failed,

The keyboard has 3 clips across the top and two screws underneath that hold it in. You could try taking it out and making sure the ribbon connector is properly in it's socket.

The mouse ribbon cable is accessibe via taking all the bottom screws out and unclipping the front of the case. The ribbon cable connect to the mobo just left of center.

Make sure both are in properly, and for the next statement's sake DONT SCRATCH THE CASE!

If still not working, perhaps send back for warranty?

> 
By the way I'm also looking forward for a Linux version to be available for our mini netbook.
Thanks;
[IMG]http://www.qtl.co.il/img/copy.png[/IMG]

Um, that's the purpose of this thread, to find some way of putting Linux on the ARM 926 based SoC Netbooks....

So far PrFaas has managed to get a serial console working, I've compiled several Kernel's that 'support' the demo boards that the CPU's are based on. We're basically waiting on one of us to put the two together and get a Kernel running properly on it.

I'm waiting on parts from the UK for the serial connection, and I beleive PrFaas is getting around to building the Kernel based on the config I've supplied whenever he has the time... Others are trying their attempt at reverse engineering the WinCE kernel and other various paths towards getting a greater understanding of the platform.

We're not far off, once we get a 2.6.x Kernel going, the LCD won't take much with serial debugging and we're well on our way to slapping a filesystem on it and booting X.

---

### Post by litch84 on 2010-01-25
The LCD controller is based on the ARM PL011.

I'll get you the LCD model # soon.

---

### Post by PrFaas on 2010-01-25
I just made an 'odd' observation on my 7" machine: About those gnd/rx/tx/5V pads that work as a serial port/u-boot console: the pad marked with 5V does *not* 'carry' 5 Volts.... I never noticed because i re-used an existing RS-232 interface which has an independent 5.0 Volts supply. The actual supply voltage on the pad marked 5V is *not* 5.0 Volts, but 'only' 3.3 Volts. This does mean that if anyone attempts to copy 'my' RS-232 buffer/driver he/she *is* going to have a little problem: the circuit is designed for 5.0V supply voltage, not for 3.3 Volts. On my board, there *is* a 5.0 Volts (well, i actually measure 5.2 Volts), but the pad marked '5V' is not 'it'. 

I found an actual 5 Volts at the following two locations:
- when looked upon the board in the position where you can see the 2 Gig Flash-ship, the two 'bottom' pins of the USB connectors carry 5 Volts
- There is a small pad marked 5V near the front of the board that also carries 5 Volts....

I'll see if i can 'gimp' something to make some arrows at those locations....

Perhaps it would be easier to attach a 3.3 Volts 'native' RS-232 buffer to only the 'original' pads.... BTW: note to self: *never* blindly believe what is printed on a PCB :)

---

### Post by litch84 on 2010-01-25
> **PrFaas said:**
> I just made an 'odd' observation on my 7" machine: About those gnd/rx/tx/5V pads that work as a serial port/u-boot console: the pad marked with 5V does *not* 'carry' 5 Volts.... I never noticed because i re-used an existing RS-232 interface which has an independent 5.0 Volts supply. The actual supply coltage on the pad marked 5V is *not* 5.0 Volts, but 'only' 3.3 Volts. This does mean that if anyone attempts to copy 'my' RS-232 buffer/driver he/she *is* going to have a little problem: the circuit is designed for 5.0V supply voltage, not for 3.3 Volts. On my board, thet *is* a 5.0 Volts (well, i actually measure 5.2 Volts), but the pad is not 'it'. 

I found an actual 5 Volts at the following two locations:
- when looked upon the board in the position where you can see the 2 Gig Flash-ship, the two 'bottom' pins of the USB connectors carry 5 Volts
- There is a small pad marked 5V near the front of the board that also carries 5 Volts....

I'll see if i can 'gimp' something to make some arrows at those locations....



I have the machine running with the keyboard & touchpad removed at the moment.

I just used the 5v from the USB +ve rail.

---

### Post by Matriark TerVel on 2010-01-25
> **PrFaas said:**
> Thank you for taking the trouble to convert my ASCII-art to a more decent diagram :)

Only one remark w.r.t your 'schema': i did mention to connect the inputs of the unused inverters to either 5V or gnd; I should perhaps have put that in the diagrams as well :D. The reason for connecting them is that the unused inverters could start to draw quite some current if their inputs are left floating.

No problem. :)

Digital Electronics was never my best subject, unfortunately. At times, I wish I would have gotten more into it than I did. :P

> **PrFaas said:**
> 
Oh, and on very close inspection: on my board, the 'order' of the pads for the RS-232 is different from what you indicate on the schema; Could well be that 'what you draw is what you see' on your board, but on 'mine' the pins are gnd, tx,rx,5V in that order, from left to right.

I drew them it what seemed to be the logical order. I don't recall what the order is exactly. 

> **PrFaas said:**
> I just made an 'odd' observation on my 7" machine: About those gnd/rx/tx/5V pads that work as a serial port/u-boot console: the pad marked with 5V does *not* 'carry' 5 Volts.... I never noticed because i re-used an existing RS-232 interface which has an independent 5.0 Volts supply. The actual supply coltage on the pad marked 5V is *not* 5.0 Volts, but 'only' 3.3 Volts.

It's a mystery then why they labeled the pad "5V." :P If it's really 3.3, shouldn't it be possible to get around the need for the independent 5V supply by basing the circuit on an 74LVT14?

---

### Post by PrFaas on 2010-01-25
> **Matriark TerVel said:**
> No problem. :)
It's a mystery then why they labeled the pad "5V." :P If it's really 3.3, shouldn't it be possible to get around the need for the independent 5V supply by basing the circuit on an 74LVT14?

For the receiver, that would make things easier :) No more trouble to limit the output of the inverter to 3.3 Volts. I'm not quite sure if the transmitter would be 'seen' by a normal RS-232 input if the 'high' voltage is only 3.3 Volts, that could be a bit of a problem. Would be worth a try though... 

FYI: 'My' circuit is also not *really* RS-232-conform: the output voltage for 'no signal' should -according to 'spec'- be below -2.7 Volts ... 

Do you have an 74LV14 'around'? You'd have to change the zener diode to a 3.3 Volts one and 'drop' the entire circuit at the output of the receiver inverter (connect directly to the CPU input.. ) A simpler circuit that's for sure :) LV is also a low-power chip, so that should be no problem.

FYI: status: compiling an 'arm' kernel at the moment....

---

### Post by Matriark TerVel on 2010-01-25
> **PrFaas said:**
> 
Do you have an 74LV14 'around'? You'd have to change the zener diode to a 3.3 Volts one and 'drop' the entire circuit at the output of the receiver inverter (connect directly to the CPU input.. ) A simpler circuit that's for sure :) LV is also a low-power chip, so that should be no problem.


I don't have an 74LV14 lying around unfortunately :( If I did, I'd try to build the circuit. ;)

---

### Post by PrFaas on 2010-01-25
> **Matriark TerVel said:**
> I don't have an 74LV14 lying around unfortunately :( If I did, I'd try to build the circuit. ;)

I'll see if i can get a 'ride' on a Farnell order 'at work'. I think i can still suffer the expense of 2.9 Euro's; For 10 of them that is ;) 

I've got my bulky 'external' buffer print working ok for now, but -in the end- i'll want the serial buffer 'inside'. Not only for the experiments: i have some 'use' for a serial port on this machine. 

I do hope we'll be able to at least find the connector pins of the CPU module eventually: the CPU itself is likely to have more than one serial port, and i'd love to have one that u-boot does not 'babble' to.

NB: i had to edit the #148 post a bit: after the objcopy, you still have to 'gzip linux.bin', or else mkimage has no input ;)

And: yes, i've got a kernel compiled, converted and in the tftp directory by now :) Attempting to boot it will be for tomorrow, i guess: for that, i also need to 'hook up' the serial console, isolate the network, 'down' the router..... It is a bit late for all that now...

---

### Post by lauriesherrod on 2010-01-25
I made the terrible mistake of buying one of these from some company in China.  It has WinCE. After about 3 hours the Internet Explorer started with a message "IESAMPLE encountered a serious error and must shut down".  I "chatted" with tech support and they wanted me to send it back to China.  I did - it cost $30 in postage!  It came back and worked another 3 hours and got the same thing again.  This time I convinced them to send me the files to reload the computer.

Now I cannot get that to work.  I extracted the files - its autorun.exe, 3-4 other files, and a folder with subfolders like Windows, Programs, etc.  I put the files on a SD card and tried the autorun.exe and it blew away most of the files on the computer's drive - so many that it could no longer see the SD card.

So I hand copied the files back using a flash drive into folders like \Windows and \System, etc.  I got it back to where it was before - IESAMPLE still giving errors.  I tried booting with the SD card in but that did nothing.  I tried running autorun again and it repeated the same thing.... grrrr....

I tried running the file from a flash drive, same thing.
I tried copying the files and folders to the computer's drive and running the autorun and it did the same thing.

The lovely error I get is "system disk no existed".

The tech support cannot speak English and they keep disconnecting me when I ask questions.

I'm pretty technically competent if anyone can tell me how to load an OS on one of these.  This one has a 2 GB flash memory of some kind - no way I can find to get into anything like BIOS.  It does start up into a bit of Windows.

Thanks!!!

---

### Post by litch84 on 2010-01-25
> **PrFaas said:**
> 
NB: i had to edit the #148 post a bit: after the objcopy, you still have to 'gzip linux.bin', or else mkimage has no input ;)

And: yes, i've got a kernel compiled, converted and in the tftp directory by now :) Attempting to boot it will be for tomorrow, i guess: for that, i also need to 'hook up' the serial console, isolate the network, 'down' the router..... It is a bit late for all that now...

FYI: The objcopy had no effect, I noticed the file size was the same, done a binary comparison of the 'before and after' - no difference.

If you do a 'make ARCH=arm CROSSTOOL=arm-x-whatever-'

It'll make the desired binary under arch/arm/boot/zImage

I'm still a bit hazy on loading address, I've seen some talk that the kernel should be loaded at 0x8000 because it uses the first 32K for paging/other vector based table....

Then again, I've seen other scriptcmd files that load directly to 0x00000000...

Can anyone shed some light?

ALSO:

The MAX232 supports 3.3v _TTL input_ operation - see datasheet:
[http://pdf1.alldatasheet.com/datasheet-pdf/view/27231/TI/MAX232IN.html](http://pdf1.alldatasheet.com/datasheet-pdf/view/27231/TI/MAX232IN.html)

Page 3 under "recommended operating conditions"

---

### Post by litch84 on 2010-01-25
> **lauriesherrod said:**
> 

I'm pretty technically competent if anyone can tell me how to load an OS on one of these.  This one has a 2 GB flash memory of some kind - no way I can find to get into anything like BIOS.  It does start up into a bit of Windows.

Thanks!!!


Format an SD card with FAT32, dump the /script folder 'as is' direct on to the SD card, so it sits like this:

s:\script\

Nothing else is required in the root directory.

Insert the SD card in to the Netbook (While off) and turn it on. It will auto boot from the SD card and reformat/install WinCE - the process takes about 10 minutes.

That should get you back up and going, as for the IE bug - it may be a permanent issue (The OS isn't the most stable).

Good Luck!

---

### Post by wicknix on 2010-01-25
Hey guys. Saw this thread linked from another forum. Not sure if this will help you at all, but i created a userland for the MIPS version of these netbooks. I could offer up a dmesg.txt if need be. Not sure how useful it'd be though being a different kernel and architecture. Or check out this website which has loads of technical info and pictures: 

[http://projects.kwaak.net/twiki/bin/view/Epc700/WebTopicList](http://projects.kwaak.net/twiki/bin/view/Epc700/WebTopicList)

And of course a shameless plug for my mipsel userland:

[http://linuxlaptopforum.ark2webdesign.co.uk/index.php/topic,794.0.html](http://linuxlaptopforum.ark2webdesign.co.uk/index.php/topic,794.0.html)

Cheers.

---

### Post by litch84 on 2010-01-25
OMFG.

Serial now working. Hacked up an ATX power supply and ran the 5v rail off that to the MAX232IN...

Output is same as PrFaas....

Attempting Kernel boot with serial console.

---

### Post by litch84 on 2010-01-26
> **litch84 said:**
> OMFG.

Serial now working. Hacked up an ATX power supply and ran the 5v rail off that to the MAX232IN...

Output is same as PrFaas....

Attempting Kernel boot with serial console.


Game over - forgot to limit the output voltage of the MAX232 and killed it.

Might get another soon if some progress is made elsewhere (I give up).

---

### Post by PrFaas on 2010-01-26
> **litch84 said:**
> Game over - forgot to limit the output voltage of the MAX232 and killed it.

Might get another soon if some progress is made elsewhere (I give up).

Sorry to hear you 'blasted' yours. :sad:  I hope it will serve as a warning to those that are about to attempt a serial console: take care with the voltage you 'feed' into the rx pin....

I was afraid of this kind of thing myself. That is one of the reasons i got two of those machines right from the start.... I do not think i can rely upon my local 'pots & pans' shop to carry a lasting supply of the machines.... Better have a backup in case of accidents. The same is also a reason why i kept the output resistance of 'my' RS-232 buffer quite high-impedant: to limit the current into/out of the CPU of the thing.

---

### Post by PrFaas on 2010-01-26
I'm expecting a bunch of smd 74HCT14 and 74LV14 chips, plus smd zener diodes (3.3 and 4,7 Volts) and 'small-signal' smd diodes tomorrow. I was lucky: one Farnell 'order' was 'on the way out' at my work today. I managed to get a 'ride' (the company pays delivery/order costs, i pay for my components + a small extra) :) 

I added a few mini-usb connectors: they are small enough to fit in edge of the box somewhere, and i guess i can use them to get my serial link(s) to the outside.... As for cables: a 'minor' modification to a standard mini-usb cable should 'do the work': if i cut off the 'normal' USB connector and connect it to a 9-pins sub-D mini, and we're ready to connect 'cleanly' to the outside world....

---

### Post by PerChristensen on 2010-01-26
**Matriark TerVel** 
FYI: regarding thin client.Had a pleasant conversation earlier today with Mark at Educational Resources,and now positive email back.They have had a delay and will put the order in today.

---

### Post by Matriark TerVel on 2010-01-26
> **PerChristensen said:**
> **Matriark TerVel** 
FYI: regarding thin client.Had a pleasant conversation earlier today with Mark at Educational Resources,and now positive email back.They have had a delay and will put the order in today.

That's the best news I've heard all week! ;)

---

### Post by 0vh301 on 2010-01-26
Hi all, 
 
I've got me kinda same thing several months ago. 
 
[http://www.q-media.eu/functions/list.asp?Lid=83&pnav=;2;102;&item=230&lang=en](http://www.q-media.eu/functions/list.asp?Lid=83&pnav=;2;102;&item=230&lang=en)
 
Reading this thread i find much things are the same. In my case its Jade Z228 with an arm926ej-s embedded. It has the same ztk password. System info says Processor Type: AKARM, ARM926-AKCHIP. It runs WinCE 5.
 
I got mine for using it as an sort of mediaplayer connected to my stereo,  streaming music from a network drive, playing internet radio and some basic browsing. WinCE5 with IE6 and coreplayer (TCPMP) does allow me to do all this, but e.g. browsing is very limited with the poor javascript support and non flash support. 
It would be great to be able to take the machine to a higher level with linux.  I'm looking forward to a first bootable linux.

---

### Post by Matriark TerVel on 2010-01-26
> **0vh301 said:**
> Hi all, 
 
I've got me kinda same thing several months ago. 
 
[http://www.q-media.eu/functions/list.asp?Lid=83&pnav=;2;102;&item=230&lang=en](http://www.q-media.eu/functions/list.asp?Lid=83&pnav=;2;102;&item=230&lang=en)
 
Reading this thread i find much things are the same. In my case its Jade Z228 with an arm926ej-s embedded. It has the same ztk password. System info says Processor Type: AKARM, ARM926-AKCHIP. It runs WinCE 5.
 

Welcome to the discussion. :P

This "AKARM" variant could possibly be like the cnmbook models. From doing taking a preliminary look at the "Firmware Upgrade" distribution (for the cnm models: [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SEsupport.htm)), the syntax of the boot configuration seems to be a little different, and the hardware a little different as well. 

We're all hoping that before too long we'll have Linux running on all of these ARM-based models. :)

The MIPS-based models are said to offer Linux as an OS choice already.

---

### Post by moblo on 2010-01-26
I am still following this thread and am thoroughly impressed by the work done by you guys. With limited knowledge about the kind of work you guys are doing, I have some questions. This serial connection you guys are making, Is that to enable you to figure out how the system ticks, or is that a neccessity to instal linux. Also, What kind of linux distro are you guys hoping to get running on these things.

I received mine just under a week ago, and love it. But there are a lot of limitations with its usage. mine does however fully support browsing sites like facebook, and has no problem loading that flash content. Also, it came with a youtube player so I can watch yt vids no problem woth this standalone app. The seller Igot it from threw in a free sd card with the 'script' recovery files to restore the system, so if anyone wants me to upload that, id be happy to.
Many thanks again to you guys!!!

---

### Post by lauriesherrod on 2010-01-26
Thanks SO much!!!  I struggled with this for six weeks - through all kinds of Chinese people who could not speak English and Googling.  This worked and it now works great!  

I would love to switch to some other OS if I can find one with all of the drivers...  But at least I have a functioning netbook now.


> **litch84 said:**
> Format an SD card with FAT32, dump the /script folder 'as is' direct on to the SD card, so it sits like this:

s:\script\

Nothing else is required in the root directory.

Insert the SD card in to the Netbook (While off) and turn it on. It will auto boot from the SD card and reformat/install WinCE - the process takes about 10 minutes.

That should get you back up and going, as for the IE bug - it may be a permanent issue (The OS isn't the most stable).

Good Luck!

---

### Post by PrFaas on 2010-01-27
> **moblo said:**
> This serial connection you guys are making, Is that to enable you to figure out how the system ticks, or is that a neccessity to instal linux. Also, What kind of linux distro are you guys hoping to get running on these things.


My reason for a serial connection is twofold:

- I want to do the development of kenel and 'userland' Linux using a netbooting machine. For that, i have to be able to interrupt the normal bootloader, or else it will load WinCE :) Ever since i saw those gnd/tx/rx/5v pads mentioned, i suspected they would be related to the serial console that i'm used to finding on embedded systems for that precise purpose.

- I want 'my' kernel to pump its boot-messages to the same serial console (for logging/capturing). It may take some tinkering to get the video/lcd operational, and it is very troublesome to do that if you are 'flying blind': no kernel-messages --> no feedback :)

The things mentioned above *could* be done without a serial console (the 'sd-card-trick'), but they would be a bit more difficult. 

Then again, there are two 'unmentioned' reasons: 
- i love to tinker with hardware :) yes: just for fun ...
- i have some use for a serial interface with what i want to do with the machine 'later on': once we have linux fully 'up and running', i'd love to have a (or more..) serial interface to 'hook up' -for instance- some of my microcontroller boards. I'll probably have to start a 'search' for 'the other' serial interfaces: the CPU/SoC reportedly has more than one  (4 is mentioned). The one for u-boot and kernel messages is probably the /dev/ttyS0 one, but i'd expect to be able -once 'under linux'- to be able to find more of them.

---

### Post by litch84 on 2010-01-27
> **PrFaas said:**
> 
The one for u-boot and kernel messages is probably the /dev/ttyS0 one, but i'd expect to be able -once 'under linux'- to be able to find more of them.


According to 2.6.x documentation, the UART port appears as /dev/ttyAMA0....

I've tried ttyS0, ttyAM0 (Previous version of the SoC), and ttyAMA0... Even tried using a USB->Serial adaptor "ttyUSB0". No love.

Either:
a. The kernel crashes before it initialises the serial port
b. The WM8505 has different/altered serial hardware
c. There's multiple serial ports detected and the header we're using is ttyS1 etc...

I'm really hoping it's not 'b' or we're in trouble and it'll be left to the disassemblers to figure out how to get it going which may take some time.

I've sent an email to Via Embedded explaining that WM hasn't replied to my datasheet request, I'd love to hear some response for once...

---

### Post by PrFaas on 2010-01-27
I think it was mr. 'PerChristensen' who managed to boot a kernel for -was it?- a thin client using the sd-card... 'From memory': i think i saw some mention of 4 serial ports being found by the kernel, and reported in the bootlog.... Warning: i've been mistaken before, and i do not know if that was a VT8500 or a WM8505.

---

### Post by litch84 on 2010-01-27
> **PrFaas said:**
> I think it was mr. 'PerChristensen' who managed to boot a kernel for -was it?- a thin client using the sd-card... 'From memory': i think i saw some mention of 4 serial ports being found by the kernel, and reported in the bootlog.... Warning: i've been mistaken before, and i do not know if that was a VT8500 or a WM8505.

Found a dmesg.txt file in some zip file I've gathered while looking for info on these SoC's...

The dmesg.txt was from a kernel built for the VT8610 according to it's version string, but I saw references to the VT8500 most of the way through as well - I'm guessing either it could have been the VT8610 SoC with some hardware similar enough to either be identified as belonging to the VT8500 or it was really the VT8500 which just so happens to be backward compatible with the VT8610 - hence the kernel build.

Never the less, the VT8610, VT8500 and the WM8505 all use the 926EJ-S arm core (ARMv5TEJ)

Your right about the serial devices though....

```

serio: i8042 KBD port at 0xd8008800,0xd8008804 irq 46
ttyS0 at MMIO 0xd8200000 (irq = 32) is a VT8610
ttyS1 at MMIO 0xd82b0000 (irq = 33) is a VT8610
ttyS2 at MMIO 0xd8210000 (irq = 47) is a VT8610
ttyS3 at MMIO 0xd82c0000 (irq = 50) is a VT8610
VT8610 Serial driver v0.74 initialized: ok

```

The dmesg.txt file also details libata and via_sata implying it has a SATA controller and a PCI bus (Which as far as I can see, our's does not have a PCI bus, let-alone a SATA controller). The WM8505 mostly uses SPI for flash i/face and AMBA / Direct IO for other peripherals.

---

### Post by dwinston91 on 2010-01-27
> **lauriesherrod said:**
> 
I'm pretty technically competent if anyone can tell me how to load an OS on one of these.  This one has a 2 GB flash memory of some kind - no way I can find to get into anything like BIOS.  It does start up into a bit of Windows.

Thanks!!!

lauriesherrod, download the VT8500Software.rar file on [http://tails92.sepwich.com/files/easypc/](http://tails92.sepwich.com/files/easypc/)    nextvolume, put the files up so we can download them.    It is a WinCE backup so you can restore your machine with a working Internet Explorer.

Then follow the directions from Post #61 on Page 7, from shade_emry.  He gives directions on how to restore the WinCE OS.

Oh.  I see you have got it working already. Cool.  Then ignore this message. ;)

---

### Post by PrFaas on 2010-01-27
A small update: I put together a small PCB with a serial driver using the 74LV14. It actually works, except for one thing: it fails a loopback test at 115200 baud. 

Meaning: I supplied the circuit from the pads of the netbook. I connected the receiver buffer output directly to the transmitter buffer input, never connecting either of those two to the tx or rx pads. At the 'big brother' computer i run minicom. The idea is that whatever i type at the keyboard is transmitted to the buffer circuit, and -by the buffer circuit- sent back to the 'big brother'. 

At baudrates below 115200 baud i get back what i type. At 115200 baud i get back only junk. Close, but no cigar :) Seems like i really need the 74HCT14... The difference between 5.0 Volts (74HCT14) and 3.3 Volts (74LV14) at the output of the transmitter does make a difference here. A bit of a pity... Now i have to remove the 74LV14 and put the 74HCT14 with output resistors at the receiver buffer output in its place.

[update] I've changed the 74LV14 --> 74HCT14, but now that one too gives me trouble... It looks like the receiver is not working good: the transmitter *does* seem ok... As an extra test: I've run a 'reflash' cycle with the serial console connected. Just to see if that would result in more info about the system's contents. Attached is the ~16 KBytes log of that operation.

It's gotten a bit late: tomorrow: more loopback tests... Silly circuit, worked ok before... Only thing i've changed is that i've added a min-usb connector and USB cable instead of the previous RS-232 cable..

[update 2] Early morning: After some more loopback tests: I've had to update the circuit for the RS-232 buffer/driver: It turns out that the 330K 'pull-down' resistor at the receiver buffer was too 'high'. With a 47K one, the circuit works like a charm. How did i get that 330K: well, from the circuit diagram that i 'always' use for my microcontroller systems. But there the max baudrate is 9600 Baud, and not 115200 :) I've updated both the 'old' post and the attached .txt file. Another thing: this means that the 74LV14 circuit was probably also 'ok', except for the same problem with the 330K resistor. I'm not inclined to build the circuit i have back to the 74LV: this reworking on the PCB gets more oogly with each time i heat it :) I doubt if the pads on the board will survive a 2-nt time that i 'pull' the 14-pads chip from the board. 

Now remains to find a nice place in the box for my 1.5 x 2.5 cm pcb, and to actually cut a hole in the side of the box. Sometime in the day, i'll also try to make a photo of the circuit :)

I'm off to go play with u-boot a bit more: last time, i only looked at the 'printenv'
This does seem to be a very 'complete' u-boot: i just *love* the 'help' command :) 

How about the 'uploadfile' command: 'Tranfer the SPI flash image to the server'. If that works we do not even have to de-solder the SPI chip if we want to make a backup of the SPI for 'unbricking' these machines.

I'll see if i can upload some traces of help-stuff: that could even be helpfull for those of us that stick to 'sd-carding' these machines...

---

### Post by PrFaas on 2010-01-28
I got to the point of attempting to boot kernels today. No success, but some progress for sure. For the description, i'll use the name i've given to the smartbook: 'mini'

I'll attach a log file of the help of u-boot and a few of my attempts. 

What works:
- serial console
- tftp-ing kernels
- dhcp server

What does not work:
1) when i set an IP address for the tftp server other than the default, my tftp fails. I have no mood to start fighting with that at the moment, so i've 'ifconfig-ed' my test network so that my tftp server is at the default IP address for the server as set in the 'mini' machine: 10.1.8.37 .. 

If i do that, then a 'tftpboot' command to u-boot does net-load a kernel into memory of 'mini' at address 0x02000000 . I can also give a 'bootm' command to actually start the kernel. after that, all 'goes blank' for now.

I've tried several load/start addresses for the kernel, i get diffeerent results. For now, i think that the load address should be 0x0000000, but i can change my mind in the blink of an eye...

Going to sleep now: tomorrow is another day :)

---

### Post by Matriark TerVel on 2010-01-28
> **PrFaas said:**
> I got to the point of attempting to boot kernels today. No success, but some progress for sure. For the description, i'll use the name i've given to the smartbook: 'mini'

I'll attach a log file of the help of u-boot and a few of my attempts. 

What works:
- serial console
- tftp-ing kernels
- dhcp server


Your results are encouraging. Loading a kernel over TFTP would be a godsend. I've booted Linux systems using TFTP/NFS in the past, and I find it to be an efficient means of testing. :)

---

### Post by PrFaas on 2010-01-29
Next step for me would be to 'hunt down' that kernel that showed signs of being bootable. So far, i've got a contraption that tries to netboot, but the actual kernel seems to 'hang'. Either my kernels are buggy', the tftp-boot still has problems or i am still doing something wrong. 

I think it was mr. 'PerChristensen' who had a kernel that got into trouble with ata-interrupts. I'd like to see how that responds on 'my contraption'.

It could even be that the kernels i'm booting are happily doing their work, just not showing anything on the console/lcd or the serial port. 

Oh, and i'm going to 'pull' the reset switch to a place where i can easily access it; Power-cycling the machine is not what i like to do all the time...

---

### Post by PerChristensen on 2010-01-29
From SD card boot camp:
 
Like litch84 I have compiled several uzImages from defconfig`s in kernel sourcecode ( sometimes: make vmlinux -> 
objcopy -> gzip -> mkimage , sometimes: make zImage -> mkimage ) for processors at91sam9261,at91sam9263 and 
versatile,but no output to mini-netbook console when SD card booting.
 
Cycles "loading kernel" -> "loading ramdisk" -> "booting", then pause for some seconds and new cycle.
 
Also tried to manually edit resulting .config files by disabling some stuff etc. before building images,but to no help.
 
Precompiled zImages found on the net transformed to uzImages does not work neither ( ex. at [http://www.arm9.net/mini2440-linux.asp](http://www.arm9.net/mini2440-linux.asp) ).
 
It is correct I some time ago made a uzImage found on the net give a bit of output on console before hanging (took a screenshot then,see attached pic.),but rather worthless as neither configuration nor drivers used by this image was available.
 
Next days I will edit a bit more (in the blind) on at91sam9261_defconfig as our mini-netbook processor are very similar to this samsung 926EJ-S used by Atmel.
Editing config files works as answering a multiple choice of 125 questions,so probability of success is small.
 
[http://www.at91.com/project-community/article/products/9-sam9/52-sam9261-s.html](http://www.at91.com/project-community/article/products/9-sam9/52-sam9261-s.html)
 
PS: work in this thread until now has been done according to the GNU license:
 
[http://www.linux.org/info/gnu.html](http://www.linux.org/info/gnu.html)
 
If any objections from anybody,please explain and give feedback in this forum shortly.

---

### Post by PrFaas on 2010-01-29
I'll see then if i can manage to build a kernel 'from scratch'. Last time around, i used a home-grown toolkit built from 'crosstool-0.43'. I used the gcc-4.1.0/glibc-2.3.2 one. One patch was needed to get things built, but the equivalent of that one has been mentioned before in this thread. I've now downloaded the  ghttp://www.codesourcery.com/sgpp/lite/arm toolset, and i'll see if that makes any difference at all...

---

### Post by cbaliko on 2010-01-29
Hi all,
 
I am new to this forum and I have read quite a lot of posts on the **Linux on 7" mini netbook ARM-VT8500 **thread. 
 
I own a 7" Mini Netbook VIA ARM VT8500 300Mhz 128M RAM 2GB Flash Solid State witn WinCe 5.0 myself.However, my OS has terribly crashed and I cant load WinCe 5.0 anymore. It is stuck on the WinCe start screen "System initiliasing". I have read in the thread that there might be people who have the WinCe 5.0 installation files. I wonder if there is way I could download them?
 
The thing is I have got my netbook from a dodgy company in HK. It actually arrived with not getting past the WinCe 5 screen. I thought before sending it back on my expenses, I could try to reistall WinCe 5 myself.
 
I WOULD HIGHLY APPRECIATE YOUR HELP! :)))
 
I dont use  the Ubuntu forum much, but please feel free to email me on baliko (at) gmail (dot) com.
 
THANKS ALOT!
 
Regards from Australia,
 
Christian

---

### Post by litch84 on 2010-01-30
> **cbaliko said:**
> Hi all,
 
  I have read in the thread that there might be people who have the WinCe 5.0 installation files. I wonder if there is way I could download them?
 
 Christian


Christian,

You'll need an SD card and reader for your PC.. 1GB is sufficient, the card and reader should cost ~$20.

The restore file your looking for the file called "VT8500Software.rar" located on page 7.

Instructions on how to perform the recovery can be found at the top of page 24 of this thread.

Good luck.

---

### Post by cbaliko on 2010-01-30
Thanks heaps!
 
You guys doing awesome work in "dissecting" these low-budget netbooks.
 
Again, thanks alot!
 
Christian

---

### Post by PerChristensen on 2010-01-30
Just philosophying in this dark,snowy winter. 
My mini-netbook comes with Win CE 6.0 + Raven Digital calculator (worth $11.95) + Softmaker office for Windows 
mobile (worth $ 79,95),so it is allmost unbelievable to get this small computer for $100 incl. P&P. 
The computers are well suited as entrance to computing for pupils.If I was a schoolmaster I would though think 
twice before buying a set for a class - sometimes things looking to be better than truth indeed is not. 
With Linux equivalents to calculator,spreadsheet,wordprocessor etc. one could be 100% sure legal issues would not matter.
So seen from a commercial perspective I do not understand if anybody would resist porting of Linux to these nice small things.
But just philosophying 8).

---

### Post by cbaliko on 2010-01-30
Hi,
 
I have followd the recovery process from page 7 but without any luck :((
However, I have noticed something a bit strange.
I got my netbook on ebay and there the specs say..
 
Processor Type: VIA ARM 32bit CPU 
Processor Clock Speed :300M Hz 
Processor/Manufacturer :VIA 
Processor Model :VIA-ARM VT8500 
RAM/Technology: DRAM 
RAM Installed Size :128M 
 
When I boot the netbook I get this:
 
Version 1.90
Hardware Version 3.0
CPU: ARM 926EJ-S 248 Mhz
Release: SV122
RAM: 128 M
Video decoder:1
 
I suppose I dont have a VIA-ARM VT8500 since it is telling me the processor is an ARM 926EJ-S 248 Mhz. I have run the recovery stages by downloading the VT8500Software.rar and copying the script folder on to a SD card. I turn on the netbook and nothing happens! It seems like it is not trying to boot from the SD card.
My problem is it gets stuck on the Windows CE 5.0 screen "System Initializing, please wait.."
 
I havent tried the VT8505Software yet, not sure if it would make a difference.
 
Is anyone aware of any other recovery software for a ARM 926EJ-S 248 Mhz ???
Any advice is most appreciated!
 
Thanks,
 
Christian

---

### Post by PrFaas on 2010-01-30
Update report: I'm drawing consistent blanks at the moment: I get to the point that i can attempt to boot a kernel, but nothing on either the serial link or the screen atm. Either i'm building unusable kernels, or loading them at the wrong address or .. or.. I know, this looks bleak up until the moment that one kernel actually boots & 'talks to me', but i see no trace of that up till now.

I've been playing with different toolsets (codesourcery & crosstool-built one), two kernel revisions (1.6.28.10 & patch and 2.6.32.7). I think i need a bit of thinking-time to see if i should use a different approach... So far, this is not really getting me anywhere :)

---

### Post by tlk23 on 2010-01-30
Christian,
Sounds like you have a computer similar to mine.

Do you get the following start up messages?

Version:1.90
 Hardware Version:3.0
 CPU: ARM 926EJ-S 248MHz
 Release SV122
 RAM: 128M
 Video decode:1
  
 Press F1 key to update system
  
 If so, press the F1 key and enter the password ztk

Try option 3 Format Flash2 disk.

This is pretty harmless as it just reformats the "user" area of the  "disk".  With a bit of luck, that will allow your computer to startup.

If not, you are looking at reflashing.  

There is an update procedure at  [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm) that  MIGHT work.  If you don't have the right cable, you MIGHT be able to  find the correct file to use in that package with option 4- Update XIP, in the F1 menu  above.  I have tried neither approach so can't say what the outcome will  be.

Good luck. Let us know if it works.

---

### Post by crowtail7 on 2010-01-30
can you upload it

---

### Post by litch84 on 2010-01-30
> **cbaliko said:**
> Hi,
 
I have followd the recovery process from page 7 but without any luck :((
However, I have noticed something a bit strange.
I got my netbook on ebay and there the specs say..
 
Processor Type: VIA ARM 32bit CPU 
Processor Clock Speed :300M Hz 
Processor/Manufacturer :VIA 
Processor Model :VIA-ARM VT8500 
RAM/Technology: DRAM 
RAM Installed Size :128M 
 
When I boot the netbook I get this:
 
Version 1.90
Hardware Version 3.0
CPU: ARM 926EJ-S 248 Mhz
Release: SV122
RAM: 128 M
Video decoder:1
 

Christian,

The VT8500 (As well as most of the other varieties listed in here) are all ARM 926EJ-S.

It basically means that Via (The maker of your CPU) based it on a design by Arm (Another company), who called the CPU core "926EJ-S", all Via did was change a few things, manufactured the chip and called it something else (VT8500). Just like my netbook has a WM8505 CPU in it. Our netbooks are more or less the same, but my CPU is made by WonderMedia, still utilising the ARM 926EJ-S core.

The 248MHz is concerning, since you "purchased" a 300MHz netbook and it's only running at 248MHz. It maybe an error, and the CPU is actually running at 300MHz, on the other hand they've sold you something its not and I (Personally) would be jumping up and down screaming daylight robbery until they either replaced it with one that ran at 300MHz or refunded my money.

Have you tried re-formatting the card as FAT32?

---

### Post by PrFaas on 2010-01-31
Another day, another try :) According to the strategy of 'when hitting a blank wall, take a step back', i've 'dumped' the contents of the loaded u-boot from RAM. 

The resulting hexdump is too big to upload here (file-limits of attachments), but i now have a 'hexdump' of u-boot as loaded in memory. Currently looking for: an arm disassembler. Reason: i know for a fact that u-boot contains the code for interfacing with both the serial port and the network. I do not think i need a full insight of what all the ~500 KBytes of u-boot does (25% of it is text strings anyway..), but putting my eyes on the I/O addresses used for serial communication -and comparing that to what the kernel thinks of 'the same'- could actually get me a machine that somehow *reports* where the kernel derails.

---

### Post by cbaliko on 2010-01-31
Hi litch84,
 
Thanks for the clarification of VT8500 and ARM 926EJ-S. Makes alot more sense now.
I formatted my SD card in all types of FAT, copied the script folder, nothing works.
Should there be a message on the screen coming up once the netbook reads the SD ?
At the moment I get this:
 
1. (Have inserted my SD)
2. Turn on the netbook
3. Screen shows:
 
Version 1.90
Hardware Version 3.0
CPU: ARM 926EJ-S 248 Mhz
Release: SV122
RAM: 128 M
Video decoder:1

Press F1 key to update system
 
4. If I dont hit F1 I see the Windows CE screen saying "System Initialing, Please wait.." And thats the end of the story.
 
5. If I hit F1, I get
"Please input password:"
 
6. I enter: ztk
 
7. Then I get these options:
 
System upgrade:
1. Format Nand disk
2. Format XIP disk
3. Format Flash2 disk
4. Update XIP
5. Update Eboot
6. Reboot
ESC. Exit
 
I have pretty much tried all options except for 1. I am not sure what XIP is for, but
can somebody explain? I thought Eboot would possibly load from SD or USB. But I am just guessing here....
 
Well, since I bought the netbook on ebay, I cant expect too much. Apparently the company is called JHS Tech Ltd and trade under name bluefly88. Here is a link to the auction [http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=170414421564&ssPageName=ADME:X:RTQ:AU:1123](http://cgi.ebay.com.au/ws/eBayISAPI.dll?ViewItem&item=170414421564&ssPageName=ADME:X:RTQ:AU:1123)
Their customer support sucks. I have requested the files from the manufacturer but
I'll need to wait until next week and see. If that wont work, I'll send it back and ask for a refund.
 
By the way, is there a "safer" place on the net where I could purchase one of these netbooks? I also thought perhaps one that comes with an OS other than wince? 
 
Again, thanks guys for helping me!!!
 
Cheers,
 
Christian

---

### Post by litch84 on 2010-01-31
> **cbaliko said:**
> 

By the way, is there a "safer" place on the net where I could purchase one of these netbooks? I also thought perhaps one that comes with an OS other than wince? 
 
Again, thanks guys for helping me!!!
 
Cheers,
 
Christian

I haven't seen any models of our range (ARM 926EJ-S based) come with anything other than Win CE 5 (VT8500) or Win CE 6 (WM8505)... In the future I hope Linux is an option, but Windows XP, OSX etc... are out of the question even if we could put more RAM in there because of the hardware limitations of the ARM core (Incompatible).

I know of some higher spec'd ARM based netbooks that do have the choice of Linux, these use a few models higher on the ARM based CPU list, and have a lot more peripheral support.

For your continuing issue, I cannot help any further because my model does not have that boot menu. But its the NAND flash you need to format, that's where the Windows CE system files reside, so I'm guessing that option 1 is the go.

As for a "safer" place to purchase, I doubt it... The OEM made these unit specifically to be as cheap as possible, as many as possible, and offer no/little support to the resellers.

---

### Post by vinolus on 2010-01-31
Hi all, 
i am following this thread with high interest. Waiting for 
such a netbook to be shipped soon. I am not experienced at all
in programming or checking out technical things, so i can't really help. Only thing i can do is to search the web and maybe 
add some information.
I found a german website about products using that same cpu
that is discussed here. They provide some linux images for download. Maybe it can be of some use?
[http://www.armbedded.eu/downloads]("http://www.armbedded.eu/downloads")
According to a phonecall i did with UPS that devices are sold alot. Hope with the number of users we can maximise the chance of
running Linux on it.

---

### Post by litch84 on 2010-01-31
> **vinolus said:**
> 
I found a german website about products using that same cpu
that is discussed here. They provide some linux images for download. Maybe it can be of some use?
[http://www.armbedded.eu/downloads](http://www.armbedded.eu/downloads)

running Linux on it.


Good find Vinolus, those test boards use the Amtel variety of the ARM9 CPU, special interest should be directed to the "Panel-Card 70" which has a 7" TFT LCD Screen ([http://www.taskit.de/en/products/panel-card/index.htm](http://www.taskit.de/en/products/panel-card/index.htm)) and linux source code (here: [http://download.armbedded.eu/software/linux-2.6.22-taskit4.tgz](http://download.armbedded.eu/software/linux-2.6.22-taskit4.tgz))

---

### Post by PrFaas on 2010-01-31
> **vinolus said:**
> Hi all, 

<snipped a bit>

download. Maybe it can be of some use?
[http://www.armbedded.eu/downloads]("http://www.armbedded.eu/downloads")
According to a phonecall i did with UPS that devices are sold alot. Hope with the number of users we can maximise the chance of
running Linux on it.

Glad to hear a few things: 

- more users --> more pressure to get linux 'cracked' onto these machines
- some linux from european sources: with source :)

I did try a few of those images: they have a completely different load address: on 'our' machines there is no RAM at 0x21000000, so they will not boot (yes: i did try.... the images can not even be expanded, they get netloaded ok: the *are* mkimage-done image files, their checksum is ok, but the machine crashes when it attempts to uncompress the image).

NB: I'm building an arm-disassembler at the moment, to see if i can find out from the dumped u-boot code where at least the I/O addresses for the serial console are. Also: i did get something boot-and-crashing: a few of the YF700 rar files are *not* password-protected, and the uzImage.bin in those loads at 0x00008000, but they 'panic' quite early in their kernel-boot.

---

### Post by PrFaas on 2010-02-01
Could 'this' (EPC700-400B):

[http://www.tenoneinternational.com/sdp/492669/4/pd-2655820/4816539-1356213/7_Notebook_EPC700-400B.html](http://www.tenoneinternational.com/sdp/492669/4/pd-2655820/4816539-1356213/7_Notebook_EPC700-400B.html)

lead anywhere: 
- 'standard' box
- 7", 128MB-Ram, 1Gig flash
- XScale/marvell/.... CPU (that's 'arm' right?
- Linux.... 

No downloadable stuff though :sad:

---

### Post by litch84 on 2010-02-01
> **PrFaas said:**
> Could 'this' (EPC700-400B):

[http://www.tenoneinternational.com/sdp/492669/4/pd-2655820/4816539-1356213/7_Notebook_EPC700-400B.html](http://www.tenoneinternational.com/sdp/492669/4/pd-2655820/4816539-1356213/7_Notebook_EPC700-400B.html)

lead anywhere: 
- 'standard' box
- 7", 128MB-Ram, 1Gig flash
- XScale/marvell/.... CPU (that's 'arm' right?
- Linux.... 

No downloadable stuff though :sad:

XScale is ARM, but of a new family than ours (ARM9E), XScale is like ARM 10.5

See: [http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores](http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores)

It'd be easier just to buy one of them though... XScale is has much more support than our core re: Linux.

More reading: [http://en.wikipedia.org/wiki/XScale](http://en.wikipedia.org/wiki/XScale)

Didn't know XScale was intel at one point...

---

### Post by PrFaas on 2010-02-01
ref XScale: my 'Toradex' board used an Intel XScale PXA-270 . I have about 3 books of documentation of the thing :) Intel can be said to be many things, but their 'doc' and 'datasheets' are first-class. 

And: unlike some chip-producers 'we' know, they have no reservations w.r.t. telling the world what they've made ;)

---

### Post by chuck3463 on 2010-02-01
Helllo. 
 
An ebay seller claimed the netbook he sold me had an Xburst 400mhz processor on which  I planned to install linux.  What I received was a VT8500 processor running at 248 Mhz.  Until a linux operating system is developed for this machine, I would appreciate any help in resolving an irritating issue with this netbook.  When used wirelessly, if one goes to sites like Ebay mobile, the wireless dies when the hyperlink is clicked for the sign in page or any additional Ebay page.  Other sites have the same issue but this one is the most consistent.  The only way to get wireless connectivity back is to shut down and restart the netbook.  I read on the Microsoft website that it is impossible to reconnect to a WPA wireless connection without restarting the computer so I set up an open WAP.  I can't reconnect to this WAP either without the shut down and startup sequence.  At first, I was able to connect to my workplace wireless network and didn't have the problem so I tried various routers at home.  An old Belkin worked so I thought the problem was resolved.  The next day the problem returned.  I just brought the laptop to work and the problem now shows up here.  I'm stumped.  Any help would be greatly appreciated.  Thanks.  Chuck

---

### Post by vinolus on 2010-02-01
Found another company that runs some kind of linux on our kind of cpu core and
provides some information.
[http://www.deditec.de/en/embedded/prod/ecpu1000/ecpu1100.html]("http://www.deditec.de/en/embedded/prod/ecpu1000/ecpu1100.html")

@chuck Are you talking about WPA security key trouble or 
connecting to net via WAP? 

Greets

---

### Post by corruptbinary on 2010-02-01
This will be my last post.  So far I have linux running on 2 netbooks (netbook and a different arm.)  But, all these links to arm chips will not help at all.  They are not VIA chips and will not be programmed in the same way.  What we need need is either linux source or documentation for the VIA arm chips.  Even then we will need to make a linux machine def to tell it how to work with memory and etc.  I have been working on drivers using the datasheet nextvolume posted HOPING that the 8500 is not too much different...only time will tell. There are TONS of these netbooks and they are using just about every kind of arm chip you can imagine, but they will all be programmed differently and wont help us.  the cheapest seem to be the via and anyka 7802 netbooks which is why im working so hard on this via.  ARMs are pretty easy to program, but the video/audio/clocks/evedrything etc are built into one chip, and unless you know how to program these, then any arm source wont help...

good luck!
if i get this working ill let you know!
(oh and be careful when buying these, there is alot of misinformation/lies/mistranslations?) with the specs of these things!

---

### Post by DonutFUN on 2010-02-01
I'm assuming that the Gentoo that this guy is talking about won't help.
[http://www.linuxforums.org/forum/linux-newbie/120164-linux-arm9-processors.html](http://www.linuxforums.org/forum/linux-newbie/120164-linux-arm9-processors.html)
(not that I even know what that is really, but there trying Linux on an ARM9 so i thought I'd bring it up)
I've only ever ran Linux once for about a month and that's it, so I don't know a lot about it, I just know its more compatible than Windows CE, and has more programs and stuff. But if there is anything that I can do to help just ask, I don't really know what I could do, but I'm willing to help anyways. :D

---

### Post by corruptbinary on 2010-02-01
Just because an arm chip is an arm926ejs doesnt help, getting linux running on arm is not hard, supporting the video, audio, etc is what we need.  we need the source or docs for the VIA arm chips or someone to reverse engineer the yf700 or microclient tc kernels.

anyone can license an arm core, and then they add their own video/audio/etc to it, does that make sense?
you are all welcome to try, i hope you guys figure it out, im gonna stick to the work im doing :)

these of course are my opinions, but i think they are correct

programming this via arm is going to be different than programming the akchip, or the anyka 7802, or the jade z228, etc etc.  there is not one manafacturer making these things either.  even the via arm netbooks have a few different manafacturers.

if i cant get this working, my next plan is to remove the board and try to put an arm cortex dev board inside one of these things!
good luck again!

---

### Post by DonutFUN on 2010-02-01
well I was just thinking that that program might help whatever it is, just trying to help, as i said i don't know a lot about linux

---

### Post by corruptbinary on 2010-02-01
I hope i didnt sound rude, just trying to get the thread back on track :)

and you might be right, the development system may help, but we would still needs/drivers/docs for the 8500.  and it iss expensive to buy as well.

i think it was nextvolume who was bugging VIA for the datasheets on their forum.  I think he is right and that is a good plan of action.  i just didnt want to register on their boasrd, and i think they will just ignore us anyways but if we make enuf of a fuss they might give up :(  than again, they might not want these arm netbooks competing with their x86 netbooks which they are also pushing with their via x86 processors.

---

### Post by DonutFUN on 2010-02-01
No no not rude at all, I'm just trying to help where I can

---

### Post by PrFaas on 2010-02-01
In the chapter of guess & gamble works:

The serial UART appears to be located at: 0xd8200000

Using the u-boot serial console:

```

WMT # mm.b d8200000
d8200000: 3a ? 55
Ud8200001: 00 ? -
d8200000: 3a ? 41
Ad8200001: 00 ? -
d8200000: 3a ? 42
Bd8200001: 00 ? q

```

What i'm doing is the following: mm.b is the command to edit memory, byte-wise. The guessed address 0xd82000000 came from one of the previous posts. Combined with a peek in the kernel source of the arm-mach-versatile board (linux-2.6.32.7/arch/arm/mach-versatile/include/mach/uncompress.h, routine putc), seems like the first byte of an AMBA-UART I/O block is the AMBA_DR (data register). writing the byte 0x55 there results in the 'U' at the next line.

I've also tried a few more characters, and a dump of the registers of the uart:

```


WMT # md.b d8200000 50
d8200000: 3a 00 00 00 0d 00 00 00 07 00 01 00 07 00 00 00    :...............
d8200010: 00 00 00 00 00 00 00 00 41 04 00 00 13 00 00 00    ........A.......
d8200020: 00 00 00 00 00 00 00 00 d8 01 00 00 0a 00 00 00    ................
d8200030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
d8200040: 3a 00 00 00 0d 00 00 00 07 00 01 00 07 00 00 00    :...............

WMT #


```

Looks 'ok' to me. Now to find out where in the whole 'shop' to inform the kernel that this is where it should find its serial console. Oh, and any 'touching' of the address set in that same file (uncompress.h) for the usart ends in an immediate system crash...

---

### Post by corruptbinary on 2010-02-01
PrFaas:

that does appear to be uart 0
d8210000 is uart 2
d82b0000 is uart 1
d82c0000 is uart 3

is this defined in core.c?

---

### Post by PrFaas on 2010-02-01
Could you give a more precise filename please? Never mind, i found it: the define is in:

arch/arm/mach-versatile/include/mach/platform.h:#define VERSATILE_UART0_BASE           0x101F1000       /* Uart 0 */

That's where i'll have to change it methinks :)

---

### Post by corruptbinary on 2010-02-01
yes you are right!
you might also have to setup the clock/rate, but i think it will default to 115k

---

### Post by PrFaas on 2010-02-01
@clockrate: When looking at the define of the defines of the registers, and the contents, from the dump, we might get an idea of what is 'set' there. 

@ other uarts, i'm still checking, but all 3 other addresses you mentioned give a similar pattern when md.b-ed ... mostly 0x00 bytes, with a few exceptions:

```

WMT # md.b d8200000 40
d8200000: 3a 00 00 00 0d 00 00 00 07 00 01 00 07 00 00 00    :...............
d8200010: 00 00 00 00 00 00 00 00 01 04 00 00 13 00 00 00    ................
d8200020: 00 00 00 00 00 00 00 00 d8 01 00 00 0a 00 00 00    ................
d8200030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
WMT # md.b d8210000 40
d8210000: 00 00 00 00 00 00 00 00 00 00 0f 00 00 00 00 00    ................
d8210010: 00 00 00 00 00 00 00 00 00 00 00 00 40 00 00 00    ............@...
d8210020: 00 00 00 00 00 00 00 00 00 00 00 00 0a 00 00 00    ................
d8210030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
WMT # md.b d82b0000 40
d82b0000: 00 00 00 00 00 00 00 00 00 00 0f 00 00 00 00 00    ................
d82b0010: 00 00 00 00 00 00 00 00 00 00 00 00 40 00 00 00    ............@...
d82b0020: 00 00 00 00 00 00 00 00 00 00 00 00 0a 00 00 00    ................
d82b0030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................
WMT # md.b d82c0000 40
d82c0000: 00 00 00 00 00 00 00 00 00 00 0f 00 00 00 00 00    ................
d82c0010: 00 00 00 00 00 00 00 00 00 00 00 00 40 00 00 00    ............@...
d82c0020: 00 00 00 00 00 00 00 00 00 00 00 00 0a 00 00 00    ................
d82c0030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00    ................

```

---

### Post by nextvolume on 2010-02-01
The processor just does calculations, checks for conditions and communicates with peripherals (what reading/writing memory address actually is), it doesn't do anything else.
The peripherals that a platform has do not depend on the processor at all, but they vary.

So for example in VIA's VT-8500 I can find the framebuffer which is at memory address X, which behaves in way Y, but in Atmel's <insert name here> ARM-based SoC I can find the framebuffer at Z, and it behaves in way W. So the code technically runs on both, but it doesn't "talk" with peripherals to give the expected result if it is made for the VT-8500 and runs on the Atmel and vice versa.

A NES game doesn't run on an Apple II and the other way around, even if the processor is similar.

Our chip (the VT-8500) is a System On Chip (SoC). That means that quite a bit of peripherals are actually in the same chip, but they're programmed in the same way as if they were external, anyway. The same goes for PCI. It's not like the one you find in your desktop PC, but you talk with some peripherals as if they were PCI, through the PCI registers.

ARM's business is just licensing CPU cores, on which vendors (eventually) build their platforms around. Vendors like that include VIA, Atmel, NVidia, and even Apple.

So in few words, it is needed to program the drivers (with technical specifications) [preferable] and/or get driver sources for Linux, which talk to the VT-8500 "peripherals" by reading / writing memory addresses accordingly and compile a kernel for the ARM926EJ-S processor at the right base address. Using kernel images for other platforms based on ARM or other System on chips won't go anywhere.
At this point if you were going to do that alchemy, you could disassemble and hack Kaser's kernel for the YF-700. I saw instructions which referred to the memory addresses of the PATA area. Modyfing that code to always fail would get it booting.

I think that we need to pressure VIA to give the community technical specifications for our VT-8500 chip (WM8505, etc. are just slightly different variants). Sources would be good as well if they're cleanly compilable (and not a big mess like these "releases" tend to be), but technical specifications would be always better as they make us completely understand the hardware and thus make us write a better driver. If they gave us both sources and hardware specs, well that would be great on VIA's part.

You can find the topic at VIA Arena in my signature.

---

### Post by PrFaas on 2010-02-01
i know: arm-designs are sold a 'scrambled' vhdl/verlog (don't know which of the two..), including much of the I/O. How they're actually hooked up is up te the chip/SoC desiger.

That's why i started chipping at that uboot dump: the serial port and the LAN interface (probably the interrupt controller too) should be 'there'. That -less than- 512 KBytes hexdump is still *big*, but not quite impossible to 'crack'. I surely agree that a nice datasheet (or mach-wm8505 kernel source dir...) would be way more helpfull :)

And my interest in those 'other' wm8505/vt8500 systems is mostly to see if anyone outside china is selling those little toys with linux pre-installed: my guess is that -if WM and/or via is really unwilling to present a datasheet- any European or USA 'base' might have a little more understanding of the gpl. If 'all would be well in the world', i'd not be disassembling an u-boot hexdump, but i'd be looking at the source of the modified u-boot that those 'gentlemen' are distributing....

---

### Post by ZigBeeGuy on 2010-02-01
I have been following this thread intently, and although I am an enthusiast, I can probably only cheer from the sidelines.

I have been in contact with a rep from hklaptop.com.  I purchased a laptop from them that uses the vm8505 processor.  

I have been told that they use to receive the laptops with Linux 7.0 (presumably Red Hat Linux 7.0), but then they change it to windows ce 6.0 since the version of Linux was quite old.

I will continue to dig for more information with the rep, but I am hoping that this gives other people a clue as to how a newer distribution can be built.

---

### Post by PrFaas on 2010-02-02
ref: hklaptop. I wonder:

- if there is any chance that they also sell those 'lappies' with the linux still installed (and thus should provide 'source' for it..)
- where from they get those linux-ed machines (could we too get one from 'there', same reason)

NB: their 'customer service' www-page is a 'hoot'  :) :
[http://hklaptop.com/services.aspx](http://hklaptop.com/services.aspx) gives a page with:

```

home > products> Customer Service 
123456

```

My guess is that most of the companies that produce these things do so only since relatively recently... 

And: i only found 7" machines on their www-site with a non-WM8505 CPU... 

ref: nextvolume's remarks: 

No offense intended, but it might be  productive to also gently 'knock' on the door of whoever made that u-boot and/or the YF700 kernel: via/wm seems to indicate that 'they' prefer not to release the info we need. If they want to bury their cpu under a mountain of rocks -information-wise- they are of course fee to do so. It is -after all- their CPU/SoC. As for u-boot and/or kernel of YF700, that appears to be a binary distributions of gpl-ed code. It would be better to get the source of that 'the nice way' but *those* guys are -by gpl- *obliged* to provide source of their modifications. Do feel free to correct me if i'm mistaken :) 

Another thing: i do not know if it was 'the YF-folk' or MontaVista who ported linux to this CPU, but if it was montaVista, i expect that *they* -of all folks- are well aware of their gpl-obligation :)

And: if all else fails, then noone can blame us for reverse-engineering the u-boot binary that was provided with the device. It should not be needed, but if analysed, that code should provide a wealth of information about the SoC configuration. We know that that code is used to control a mayor part of the hardware:

- system init (now what may we all find *there*..)
- LCD
- SD-card
- UART(s)
- LAN
- NAND flash
- keyboard (? not quite sure of that....)

I know: there's still plenty hardware a-missing/unaccounted for, but 'having' those devices is a good start. Less 'noble' would be to subject the WinCE kernel/HAL to a similar treatment: that should provide clues as to the rest of the hardware, at the cost of having more binary to 'dig through'.

---

### Post by omrip on 2010-02-02
Hey all
it was such a great 2 hours reading through this thread 
that wanted to say - keep up the good work
hopefully my device will arrive soon so i could join the party!


:p

---

### Post by nextvolume on 2010-02-02
It is a good idea to play also on the "pressure-for-source-code " field.

I remember it was PerChristensen who tried to contact Stan at Kasernet for source code, and he said that Stan told him he was trying to get authorization from the higher-ups. But there has been no answer by Kaser in twenty days. To my understanding, Linux was ported most probably by VIA, as the ASCII art you can find when you log into the telnet session shows the VIA logo.

VIA surely knows about the GPL, do not think for a moment that they do not. They have had their Linux experiences as well, albeit they were far from being roses.

Maybe we can write to the FSF about this? The source code for the firmware of an ISP-branded router I hack were obtained by doing pressure on the company which made the firmware, with help from FSF Europe.

---

### Post by PrFaas on 2010-02-02
And now for something completely different: In a rar archive as downloaded from our friends at kasernet: 

[http://kasernet.livedrive.com/frameset.php?path=/files/](http://kasernet.livedrive.com/frameset.php?path=/files/)

in the browsable 'stuff' there: 

public->yf700->ce->bsp

there are two files:

sln-pbxml-090522.rar
VT8500-090522.rar

The VT8500-whatever.rar, when extracted, contains a directory: VT8500/SRC ... Which -i think- is well worth our attention...

---

### Post by DonutFUN on 2010-02-03
I'm hoping the reason nobody's said anything since that came up is meaning good news, if not I have made an account for the Via Forums, but I'm not exactly sure what I should be saying on the forum, what should I?

---

### Post by xmob on 2010-02-03
A common misconception is that everything that runs on Linux must have the source code released.  That's not true.

Manufactures are not obliged to release the source code for drivers for their hardware.

That's not to say that it's not worth pressuring manufacturers to release source code.

---

### Post by tlk23 on 2010-02-03
PrFaas
I think VT8500/SRC has the answers to pretty much all the questions.  Good find!

---

### Post by nextvolume on 2010-02-03
No, those are the Windows CE drivers. Useful hardware information, but to use those drivers in Linux you'd need to do some major porting effort.

Also, xmob, that's disinformed! The drivers themselves are compiled into the kernel itself, not as modules which use a GPL wrapper. This means that either ship with source code or they are violating the GPL.

---

### Post by xmob on 2010-02-03
I didn't say that the drivers were compiled as modules, or otherwise.

I was pointing out that not everything Linux is open source and/or GPL.  I've been working recently on Sigma SoCs.  Those drivers are kernel modules and closed source.  Especially the XIP stuff.  :(

What I was trying to point out was that going in "feet first" might be a bad idea until the nature of the missing source is understood.  It's better to work WITH manufacturers than AGAINST them.

---

### Post by DonutFUN on 2010-02-03
Hey just a quick question for the people with theirs opened up, where about is the microphone? I know there is one, but I don't know where.

---

### Post by PrFaas on 2010-02-03
On 'mine', it's on the board at the left-middle (close to the red 3.5mm jack plug). I'll gimp a bit of my photos to make an arrow.

But mind: there seems to be a lot of different board out there 'in the wild', so it may well look different on the inside of your machine :) The only thing i found consistent across all those machines is that here appears to be only one company that makes the plastic boxes :) Come to think of it: i may even be mistaken in that ;)

@nextvolume: i know that this is the WinCE BSP :) not a linux bsp. What it does contain however is the (assumed...) complete list of I/O addresses and interrupts of the machine. That should be enough to 'fill in' a lot (my good hope: all, but i expect: enough) of the blanks for making a linux bsp. 

I'm assuming for a minute here that VIA/WM did not build the SoC 'from scratch'. As i've seen, most arm-ish CPU chips are 'composed' of mostly pre-'built' modules (bought 'IP') that are 'strapped' together, much in the way as a normal PC is built togethter from standard components. the difference here being that the building together has been done inside the SoC.

I've done some checking on the uart(s): they are 'standard' arm-uart modules, provided with an I/O address and an interrupt. The baudrate delays are provided, as well as the I/O addresses, a 'names-only' register description and -for some devices- some *very* terse source where the device is used. As far as i've been able to check, the linux standard driver for the same device uses the same registers, with same bits (now that *is* expected: i've not seen the linux kernel developers tending to indulge in idle renaming).

In any case: anything 'strange' that VIA may have done will have to be described in the WinCE bsp for WinCE to be able to use it. 

So: yes there is surely 'work to do', but that can now be done based upon C and/or assembly code from the WinCE bsp, as opposed to reverse-engineering it from a hexdump (i have stopped that self-torture for the moment :) ). 

And: (for nextvolume :) you are most right about that) i'd still like to have a databook form VIA about this SoC for background info... This bsp is a minimal information set, not the 'luxury edition' :) ; It may still leave some 'there be dragons' territory to explore.

---

### Post by DonutFUN on 2010-02-03
Thanks for the picture, and so that pretty much sums up to, there is probably the info in the build.log's in there, but you just need to find it, decode it, and put it into Linux then right? (in layman's terms)

---

### Post by PrFaas on 2010-02-03
Not quite in the buildlogs, but close: the include's are -at the moment- more informative. And: it *is* a lot of work.... Not for nothing did i start with the uarts: they are the least difficult to understand.

I started based on the 'versatile' board, and that may not even be the 'closest' to his VT8500 in the selection of arm-architectures that linux supports. I'm currently doing some 'study' work w.r.t. how to build a minimal bsp. In fact, the answer to the question: what is *really* needed to get *something* to boot... We can always expand to 'the rest' later...

---

### Post by zednatix on 2010-02-03
Has anyone tried a Linux Distribution from Netbooks using this ARM Chip?

I found 3 recovery versions of Linux Distributions at this page:

[http://www.littlelinuxlaptop.com/](http://www.littlelinuxlaptop.com/)  ([http://www.littlelinuxlaptop.com/software](http://www.littlelinuxlaptop.com/software))

The Recovery Images from Elonex ONE and ONE+ Netbooks which are both using this chip could be downloaded here:

[http://www.elonex.co.uk/support/products/lnxone.shtm](http://www.elonex.co.uk/support/products/lnxone.shtm)

Would be nice if someone is encouraged enough to try to install one of these Linux versions on his netbook and report the results here.

I will get mine in a few days...

---

### Post by PrFaas on 2010-02-04
I expect little from those 'elonex'/et.al. images. 

The reason: the cpu for this machine is reportedly: 'EPC 700 Processor: XBurst 400 MHz 32-bit CPU'. 

Feel free to correct me, but as far as i know, the XBurst CPU is a 'MIPS' cpu, and we're dealing with an 'ARM' cpu here. Two completely different beasts. If i'm not mistaken, you might as well attempt to run an x86 kernel on 'our' machines: about zero chance of success :)

The shortest route to get linux installed (and running..) on our machines is still to coax one of the companies who actually makes a linux-running version a machine using this SoC to release the 'bsp' (Board Support Package) for it in source form. 

'They' have a bsp for the SoC... That is why 'they' can build a kernel for the SoC of our machines (kaser does that with the YF700..). 

With the information from the WinCE bsp, we have enough information to give building our own bsp a try. That *will* be a long & difficult road. An interesting and educating one for sure :) One that might end us up with a working bsp. We may fail: the WinCE info is very terse, VIA/WM is unwilling to support us... 

But the galling thing is that the work of building 'our own bsp' is a duplicate of what has already been done.

As a 'just in case': has anyone else downloaded that WinCE bsp?

---

### Post by DonutFUN on 2010-02-04
I've got a copy, I just wanted to take a look, I'm assuming you're asking for just in case the site goes down right?

---

### Post by PrFaas on 2010-02-04
@DonutFUN/'in case the site goes down': Yep :) Or in case the bsp dir and/or .rar file pops out of this universe :) .

As far as i know, it is the best 'map' we have at this moment as to what is going on inside that VT8500 SoC. In such cases, 'keep it safe' is always good advise. A 'backup elsewhere' is the best strategy i know.

---

### Post by zednatix on 2010-02-04
A look on this picture of the Allnet PC703 which uses ARM shows that there should be a version with linux, as you can see on the small screenshots below the main product picture (one left of the windows ce screenshot)

[http://www.pcspezialist-bremen.de/wp-content/uploads/2009/12/pc703-a.jpg](http://www.pcspezialist-bremen.de/wp-content/uploads/2009/12/pc703-a.jpg)

---

### Post by corruptbinary on 2010-02-04
has anyone tried to boot these?

nevermind its too late at night../

---

### Post by dvn3ch on 2010-02-04
Just adding my two-cents (may be of less value judging from the many pages already posted).  I, too, have one of teh "green board" VT8500 netbook with WinCE 5.0.  It has 128mb RAM and 2Gb of "storage".

This may have been covered oh-so-many pages back, but has anyone had the same problem of getting into the "bios" with the magic password and then not being able to do anything but "esc:exit"?  This is the weirdest thing the I have ever seen.  

Someone's post about not really having a bios may be very correct.  However, it begs the question..."Why have it for nothing?".  I was not brave enough to choose the "Format XXX" selections but assumed that they either did not work as the other choices or it _did_ work :sad: and there would be no more...whatever.

---

### Post by litch84 on 2010-02-04
> **PerChristensen said:**
> A small precompiled linux image + U-boot bootloader seem to exist HERE:
 
[http://www.arm.com/products/os/linux_download.html](http://www.arm.com/products/os/linux_download.html)
 
Also a free ARM compiler seem to be available HERE:
 
[http://linux.onarm.com/index.php/Main_Page](http://linux.onarm.com/index.php/Main_Page)
 


Don't bother with the linux images found on the arm website, I've already been through them all. They're designed for the development boards, and would perhaps be very close to what we want but still doesn't get us anywhere. The config file and the source patch should be of interest though, found on the same page.

ARM also recommends the cross-tools found here:
[http://www.codesourcery.com/sgpp/lite/arm/portal/subscription?@template=lite](http://www.codesourcery.com/sgpp/lite/arm/portal/subscription?@template=lite)

---

### Post by DonutFUN on 2010-02-04
Hey, I was just looking at my stuff on this thing, and I realized, I have a device manager, true most off the stuff falls under the "other" category, but still, you can get more information from under there, what dll's and device number or something.
 
go to the wincesoft.de and there's a link to download Mio Pocket tools, and under Mio/autorun/programs (or something) there's the device manager.
If you can't get it then I can try upload it, (I will anyways if it lets me)
 
Just an Idea, I know the drivers are different, but it may give you a bit more info than you have maybe?
(Didn't let me upload it)

---

### Post by Pilotgeek on 2010-02-05
Hey guys, 
Finally signed up for the forums, been watching since day 1 (sorry that I don't have any more n00b quetions for you guys...) Anyways, relating to the device manager post, would the drivers section in the registry help? It lists all the DLL's and some information about the hardware. Also, I may try to contact the company I got my netbook from. It shipped directly from China, but the customer service has been surprisingly good. I may ask if they had any versions of Linux for it at the factory...

Edit: No help from the customer service, they informed me that they have no Linux images at their factory, they only throw CE6 on them.

---

### Post by DonutFUN on 2010-02-05
Ya know, if they've been so helpful for you maybe you should phone them up and ask for the information we need,i think its the data sheet?

---

### Post by stw89 on 2010-02-05
I think I read in one of the posts that some US department stores are carrying these? Is is this legal? Surely every single one of these netbooks are operating pirated CE5/6? Or, are they on 120 day evals?
 
These couldn't even be legally sold in the US right?

---

### Post by idiamin on 2010-02-05
> **stw89 said:**
> I think I read in one of the posts that some US department stores are carrying these? Is is this legal? Surely every single one of these netbooks are operating pirated CE5/6? Or, are they on 120 day evals?
 
These couldn't even be legally sold in the US right?

I Think this goes beyond trying to run *nix on these machines. But yes K-Mart seems to be selling a similar product.

---

### Post by PerChristensen on 2010-02-05
I have now bought a used CNM minibook motherboard online and will replace my "VT8500 board" with this.
 
Some Debian based distros exist for CNM minibook MIPS processor (PSP run on MIPS) and hopefully I will be able to get a few Linux applications for hobby astronomy up running,to accompany my small telescope.
 
It has not been possible to buy a "thin client" and ask for the Linux source code for the client (as far as I remember it should be possible to ask according to online "thin client" pdf leaflets).A transaction was pending on my credit card account but now has vanished / disappeared,so no deal.
 
Life must go on,and if success with apps. running on CNM / VT netbook hybrid I will surely feel myself the owner of a memorable toy / minicomputer :???:. 
 
Paulo in Brazil has sent a PM asking for some details about a blackburned chip near the power inlet on his VT board.I can give this info in a couple of days after swapping motherboards.I cannot see the picture on your link,Paulo,so attach it to a message in this thread,and I will give you the info.

---

### Post by max1024 on 2010-02-05
Hello 2 all.
I have ordered, discussed here smartbook via Ebay, cpu in description just VIA-ARM VT8500. While I was waiting for it I have a few questions, can someone answer me on them. 
1. What is the maximum size of SD card that is supports smartbook? 
2. Can I put 2 operating systems, WinCE and Linux? (although I understand that work on installing linux is still under way). 
3. What about emulation on game consoles SegaMD2, SNES, under WinCE, can someone tried to run, if yes, what emulators need to use? 
4. Can I somehow go to the Internet from WinCE via GPRS? eg connect my phone via data cable (I have a Nokia), or insert the USB-GPRS modem. What about drivers?

---

### Post by DonutFUN on 2010-02-05
About running emulators on these things, you download and install GAPI from wincesoft.de and make sure to enable the emulation because these are not sported buy default, then off of that site there's a link to get MorphGear, and what you do in install that, and get the corresponding Morph Modal for the system you want to emulate, and then you can play most any games from any systems, though they are fairly laggy, it's best to leave the sound off because that makes it lag a lot more than i think its worth.

---

### Post by celem on 2010-02-05
[QUOTE=max1024;8779904]Hello 2 all.
...
2. Can I put 2 operating systems, WinCE and Linux? ...

These units barely hold one OS. Loading two seems downright impossible.

---

### Post by DonutFUN on 2010-02-05
but you (or someone) was saying that the hope was to be able to have CE on the internal memory and load Linux off of an SD card, would that work in the end do you think? or am I going to have to get rid of CE on this thing?

---

### Post by celem on 2010-02-05
My personal goal is to get rid of CE and only have Linux. The 6.0 CE is really, really lame.

---

### Post by DonutFUN on 2010-02-05
Well, I'd prefer to keep both, is that possible? and if not I guess I can deal

---

### Post by illumin8 on 2010-02-05
I keep checking up on this thread about every week or so...
I have almost no embedded experience, so i feel largely a spectator at this point, but this seems to have the potential to either fizzle, or take on a serious life of its own. Would someone with more knowledge be willing to summarize the sticking points, and perhaps how we can be working on those specific points? I may not have much embedded experience, but i have several friends who might be of help if i knew what to ask them specifically.

---

### Post by moblo on 2010-02-05
> **illumin8 said:**
> I keep checking up on this thread about every week or so...
I have almost no embedded experience, so i feel largely a spectator at this point, but this seems to have the potential to either fizzle, or take on a serious life of its own. Would someone with more knowledge be willing to summarize the sticking points, and perhaps how we can be working on those specific points? I may not have much embedded experience, but i have several friends who might be of help if i knew what to ask them specifically.

I think a summary would be great for all of us. I too have pretty much no embedded knowledge and limited linux knowledge. I have been following the thread since post 1, and am very impressed and excited by the progress. But in realistic terms, how close/far are we? What still needs to be overcome? And how feasible is the end product?

On a side question, if we manage to get linux on this baby, how good will it be at media playback? Cos atm, the divx playback os tooo laggy, and other file playback is toooo mediocre to bother with.

---

### Post by illumin8 on 2010-02-05
What I lack in expertise, i can make up for in initiative:)

I posted a rather long and detailed post on the VIA forums requesting the release of a datsheet. I tried to use relevant market examples for the benefits of creating a developer culture around devices, and tried to show them that they have an opportunity.

Perhaps for those of us that cant help technically, we can help by making repeated requests for data from VIA.


[Forum Request for datasheet from VIA]("http://www.viaarena.com/forums/showthread.php?p=250809#post250809")

[Contact list for VIA]("http://www.via.com.tw/en/support/")

---

### Post by omrip on 2010-02-06
Hi all !

I agree with illumin8 and i think all the people who saw this thread should join in on the  data sheet request
only together we can show them the real demand for it

---

### Post by DonutFUN on 2010-02-06
I have joined the VIA data sheet request, hopefully they'll give in soon
 
ya know, i was just thinking there may be a chance that they do have a data sheet, but it has absolutley everything, including things we don't need and they don't want to give us, and they don't have time to remake it so they can give it to us. so maybe a little money for there time? I would donate but I'm unemployed so I have no money, just and thought I wanted to throw out there. of course like 20$ at most, not that we should even need to be discussing this.

---

### Post by max1024 on 2010-02-06
[SIZE=2]So what about using Internet on WinCE/Linux in near future via GPRS? It is very important to me because I have bought smartbook for this, eg connect my phone via data cable (I have a Nokia), or insert the USB-GPRS modem. Is it possible in theory at least?[/SIZE]
[SIZE=2]WinCE is very bad for non english speaking users, there is no cyrilic in CE6.0 at all, as french, german and other languages, linux is more flexible and find adapt to the native language version like Puppy Linux is possible.[/SIZE]

---

### Post by PrFaas on 2010-02-06
I'll have a go at making a 'summary of progress so far'. Do feel free to correct. I will limit my description to the VT8500 (and possibly the WM8505) SoC's, because i have no idea what the differences with the 'other' CPU/SoC's are.

1) Via seems unwilling to provide information. That's bad, bad, bad... I can not really think of a sound reason for that (Intels XScale CPUs are documented 'to the bone', for instance), but that's how it is.

2) the default (kernel.org) kernel has no support for this machine/SoC.

3) We've attempted to boot several of the binary images of kernels that are 'out there'/'in the wild', but they all failed us at some point. 

4) More and more of these machines seem to be 'popping up' all over the place. About all of them run WinCE in some form. Linux versions are 'announced' but have been elusive for now. The ones that actually do run linux seem to be mips-based (400 MHz MIPS processor). The outside/box of those MIPS machines looks just like 'ours', but the 'core' is different. If your goal is to get a machine with 'specs' comparable to 'ours' but running linux 'in no time', getting one of those is 'the way to go'. Elonex already has an active user community for their MIPS-based machines. OTOH, if even *one* of the 'new' machines with VT8500/WM8505 inside runs linux, and if the supplier of it provides 'the basics' for building your own kernel, then we're in business/home free. The same SoC means that we can simply 'rip' the support for the SoC from their support package and have a 'short route' to getting linux running on our machines. Keeping an eye out for VT8500/WM8505-based machines that *do* run linux is still worth the trouble.  

4) 'Kaser' sells a 'thin client' that uses the same VT8500, which is running Linux. I guess that Kaser can not build a linux kernel without a bsp. Conclusion: There *is* a bsp for the chip 'out there' somewhere, but we have no access. Instead of 'bugging' only VIA/WonderMedia itself, i would suggest we also kindly (and *please*: politely..) see if Kaser is willing to provide what comes down to an 'arch/arm/mach-vt8500' directory tree of the linux kernel. 

That pretty much closes 'the way' to get Linux 'up & running' the easy way. So much for the bad news. Now, moving on to the -slightly- more bright side:

1) I have managed to add a working serial console to my system. That shows that the bootloader of the thing is the open-source u-boot. Interesting enough, that bootloader is all set up to load a linux OS. U-boot is however instructed to auto-boot a WinCE kernel. That autoboot can be interrupted, and from there you get a seemingly complete u-boot 'console' into the system. This is a 'window' into the system that can be used to analyze what it does.

2) The machines have a -by now- quite well-understood 'restore/upgrade' mechanism that uses the sd-card interface. Several users (including 'yours truely'..) have already used that to recover a 'damaged' system. This WinCE seems quite capable to getting itself into trouble, and re-flashing the system usually allows recovery. The scripts that are used to recover the system have been analysed, they are 'standard'/extended u-boot scrips. The extensions to a standard u-boot include functions to initialize the display and write strings to the display is various colors. I harp about this because -as i see it- the same mechanism could be used to 'divert' the boot-process to load a linux kernel from the sd-card and direct that kernel to use the sd-card as root filesystem. In other words: if we can compose a working linux kernel with sd-card support, it seems we can also direct the entire machine to run off an sd-card. No need to 'blast' the WinCE off the machine: we could dual-boot the internal flash with an sd-card. Several users have used the mechanism to 'test-boot' linux kernels: the kernels 'stink' for this machine, but they do attempt to boot.

3) We have what appears to be a usable 'toolchain' (gcc/etc..) in the form of the 'CodeSourcery lite' toolchain. This toolchain is capable of compiling applications for the arm CPU that lies underneath this SoC. I've compiled kernels (linux-2.6.32.7 based) for the machine. Those kernels do not actually boot successfully, but i'll come to that in a minute.

4) Our friends a 'Kaser' have a bsp for WinCE-6.0 on their public ftp area. That bsp contains -in source form- quite a lot of information about what is going on inside the VT8500 SoC. How complete that information is is yet to be determined. 

5) About all the 'other' chips (non-VT8500/WM8505) in the machine are well-documented. The keyboard controller took some creativity to find out about, about all of the other chips simply have a datasheet on-line. The last one i 'hunted down' was the little chip on the touchpad: it is a Cypress semiconductor microcontroller. 
  
So much for 'the facts' If that's all you want to know, read no further. Now -as i see it- the road ahead:

I am about to see if i can compose a minimal 'arch/arm/mach-vt8500' directory tree for the machine, based upon the 'defines' found in the kaser WinCE bsp. For most of the hardware, i hope the actual 'missing links' should be not all to difficult to 'set up'.

Consider the following: WinCE -from-shop- is just as unaware of how to handle this SoC as is linux. The WinCE bsp does little more than 'instruct' WinCE how to deal with the precise hardware in the SoC. For some hardware, that may come down to providing a full device driver. Some 'here' have expressed pessimism about building device drivers for all the hardware in the machine. I think that would indeed be madness without active support from VIA/WM. I do however *not* intend to start writing device drivers for the machine's hardware. 

I merely intend to point the existing drivers in the linux kernel towards where the actual hardware is (I/O ports-wise) located. As an equivalent: for a moment, forget all you know about the normal addressing of the I/O of a normal PC. If a linux kernel is to use -for instance- the serial port #1, it must be made aware of a few things:

- what I/O address to expect the device at (I/O space, 0x37F)
- what interrupt it uses (#4)
- what device it is (16C550 for instance)
- clock/baudrate relations (clock = 1.8432 MHz)

In the equivalent: the actual driver for a 16C550 serial port may well be already present in the kernel source, but unless the kernel is also informed of 'the above', it can do nothing with that serial port; It can usually not even 'find' it. For a normal PC, that info is usually so well-known that no-one gives it much thought. Also: -as with PCI cards- a mechanism of 'self-description' is used in PC's so that he kernel can find out about the 'hardware present' in a systematic way by 'discovery'.

With the example of the serial port: For our SoC -i think- we are in a similar situation: There *is* a linux driver for the serial port, but the 'link/address' information is 'missing'. that information is provided as part of a bsp. I've had a 'peek' at other bsp-info for similar 'arm-ish' chips/SoC's, and the 'link info' is usually different from what we've already found for 'our' machines. That explains why we had so little success with binary kernels 'from the wild': those kernels just 'misdirect' the kernel w.r.t. the I/O. From my experiments with the u-boot / interrupted boot process i did find that the machine usually responds to reading/writing 'wrong' I/O addresses with a 'hold and catch fire' action: it stops 'dead', which can only be recovered from with a hardware reset (so: no actual 'fire')

The closest we have to working kernels are the kernels from -again- Kaser, which really do 'get off the ground', but 'crash and burn' soon afterwards. These kernels do report nicely on the serial console.

From observation of the contens of the WinCE bsp, i get the impression that much of the hardware in our machine is 'bought IP': arm is quite willing to -for a price- provide I/O modules that can be 'plugged' into an arm-based SoC. It looks like VIA has made extensive use of those. The good news: for most (all??) of those, the linux kernel already has a standard driver. Those drivers have mostly been written for other arm-ish CPU/SoC's, but they should work just as well for 'ours'. The more standard I/O modules VIA has used (and if those have standard linux drivers..), the easier it is for us to link them up with the  pre-existing linux driver. 

I plan to start out with a kernel that has support for as minimal a set of hardware as possible, and 'work up' from there. I've studied the CPU (arm-926) technical reference manual: the mmu, cache etc.. are described there. That means -i hope- that -if i instruct the kernel to use the correct CPU- i need not worry about those: the support for the CPU itself should take care of those. 

I have to see how much is actually needed for a minimal-hardware-supporting kernel: 

- the memory size and base address for sure:
  base = 0x00000000
  MEM_SIZE = 127M
  nb: why the 127 instead of 128: i dunno: the u-boot bootargs give that number, i do not tend to disagree at this moment. 

- the interrupt controller info: i found quite some info w.r.t. that in the WinCE bsp. Needs some work, but looks promising.

- the system timer: Found most of that info: needs some work...

- The serial port #1 info: found that one :)

- there may be more... I'll have to find out (probably 'the hard way').

That is the info that should give me a kernel that boots, with *very* minimal hardware support. that kernel will -at some moment- get very unhappy because it will *not* be able to find/use a root filesystem... One step at a time. From there on: see if i can get as much hardware as possible 'alive'. there may be drvice driver 'to port' from the WinCE code --> linux drivers, we'll have to see....

Oh, and i will have to find out how to actually 'report' to the kernel build mechanism that there *is* such a thing as an mach-vt8500 . So: i know not how to direct the kernel towards using the bsp i'm about to put together. That information is part of the OSS 'realm of knowledge', but i've been yet unable to get much grip on it. Is there something like a linux bsp HowTo somewhere? Your hints as to how & what is needed inside a bsp in the linux kernel tree are most welcome.

Your comments/remarks on this 'yet another long story' are most welcome: i'd rather be pointed to the 'error of my ways' now than be left to find out later.

Just realizing: this is not a *short* summary. Please forgive my babbling

[edit]
w.r.t. approaching the 'makers' of our little toys politely: Please consider that more than one of them may never have had any exposure to the 'rough & tumble' culture 'out here'. Just to put you in the frame of mind: 

If *you* where to find a mob with torches & pitchforks at your door, i do not presume that your first idea would be that all they really want is to spend a quiet hour in your library to study one of your books :)

[edit2]
Forgot to mention: the bootloader of 'our' machines is u-boot. U-boot is -best of my knowledge- gpl-ed FLOSS. The u-boot on our machines appears to be a modified version of u-boot, concluded from the boot-message: 'U-Boot 1.1.4 (Dec 14 2009 - 18:18:15)'. Standard u-boot has no support for VT8500 that i'm aware of. I was unable to detect any lcd commands in the standard u-boot source code. This u-boot is distributed in binary form to 'us'. We have been provided with neither the source of the u-boot in our machines, nor the 'written offer', nor any other source form of that u-boot.

Again, feel free to comment, but as far as i've understood that is not conform the gpl. Reason for mentioning: the source of that modified u-boot should contain a host of information that could be of help to get linux a-running on this machine: interfaces to LAN, sd-card, video and serial port to mention a few. Unfortunately, we don't even begin to know on what (competent) door to 'knock' with our request for the u-boot source of our machines.
 
I -for one- could go to the'pots & pans' shop where i bought my machines, but i doubt the lady selling them will have the foggiest notion of what i'm talking about :) Looking a bit closer at the boot-messages from u-boot: 

'WMT U-Boot Version : 0.12.01.00.06'

assuming WMT is something like WonderMedia Technologies... a nice door to knock on?

---

### Post by brobison75 on 2010-02-06
> **PrFaas said:**
> I'll have a go at making a 'summary of progress so far'.I'm not even an Ubuntu user, but I registered just to thank you for this post, and illumin8's requesting of it.

Also, I have varying levels of relevant expertise... I'll see if there's anything I can help with.

Again, thanks to everyone for all their work on this.

---

### Post by PrFaas on 2010-02-06
> **brobison75 said:**
> 
I'm not even an Ubuntu user, but I registered just to thank you for this post, and illumin8's requesting of it.


@Ubuntu user: At the risk of being banned: neither am i :) I bumped into one of these little machines a while back, started www-ing for a way to get linux on it, and found that 'the action' was here.

> 
Also, I have varying levels of relevant expertise... I'll see if there's anything I can help with.


Most welcome, i'm sure we can use all the help we can get.

---

### Post by necro666 on 2010-02-06
i found that link regarding the CPU:

[http://www.windowsfordevices.com/c/a/News/Sungworld-netbook/](http://www.windowsfordevices.com/c/a/News/Sungworld-netbook/)

The CPU is said to be similar to the Via VT8500.

"...The SoC appears to support a wide variety of memory types, and WonderMedia touts the Prizm 8510's "low power consumption," though further details weren't offered. Meanwhile, the SoC's "broad operating system compatibility" is said to include Windows CE, **Linux**, and **Android**. "Strong BSP, SDK, and RDK support" is offered for both Windows CE 5.0/6.0 and **MontaVista Linux Professional Edition 4.0/5.0**, the company adds..."


And there is another company working on that topic:

[http://www.norhtec.com/products/mctc/index.html](http://www.norhtec.com/products/mctc/index.html)

---

### Post by wicknix on 2010-02-06
While i own the mips version of these netbooks i think this might be of some use. By the looks of it the Datawind Ubisurfer might just have the kernel and modules you guys are looking for. Here's the output a user posted on littlelinuxlaptop.com's forums:

Here is the output for uname -a:

 Linux ubisurfer2 2.6.21.5-cfs-v19 #423 Tue Nov 17 15:28:50 EST 2009 armv5tejl unknown

 and /proc/cpuinfo:

Processor    : ARM926EJ-S rev 5 (v5l)
BogoMIPS    : 199.47
Features    : swp half fastmult edsp java
CPU implementer    : 0×41
CPU architecture: 5TEJ
CPU variant    : 0×0
CPU part    : 0×926
CPU revision    : 5
Cache type    : write-back
Cache clean    : cp15 c7 ops
Cache lockdown    : format C
Cache format    : Harvard
I size        : 16384
I assoc        : 4
I line length    : 32
I sets        : 128
D size        : 16384
D assoc        : 4
D line length    : 32
D sets        : 128
 Hardware    : SMDK2450
Revision    : 0000
Serial        : 0000000000000000


Taken from: [http://www.littlelinuxlaptop.com/forum/?wpforumaction=viewtopic&t=56.0](http://www.littlelinuxlaptop.com/forum/?wpforumaction=viewtopic&t=56.0)

Cheers.

---

### Post by saundersc01 on 2010-02-06
Since this seems to be the only site on the whole internet (it seems) discussing these laptops, I have a question-I'm running the version of this little netbook with the ARM926 processor and I was just wondering if the netbooks you guys have sort of resets it's memory every time you turn it off...ie, deleting icons off the desktop and them reappearing when the unit gets switched back on or even putting stuff in the documents folder only to have it not be there when power is reapplied.

I apologize if this was not the thread to post a question of this nature, but again, this seems to be the only place around discussing these neat little things.

On another note, you guys seem to be making pretty good progress towards running linux on these things and I'll be following this thread. If for whatever reason you guys need anything because of my particular processor (I don't remember seeing the ARM925 mentioned), let me know what I can do to help. I'm new at netbooks, but I'll do what I can.

Thanks in advance.

---

### Post by wicknix on 2010-02-06
> **saundersc01 said:**
> Since this seems to be the only site on the whole internet (it seems) discussing these laptops, I have a question-I'm running the version of this little netbook with the ARM926 processor and I was just wondering if the netbooks you guys have sort of resets it's memory every time you turn it off...ie, deleting icons off the desktop and them reappearing when the unit gets switched back on or even putting stuff in the documents folder only to have it not be there when power is reapplied.



Check this how-to out to solve that problem. This website also has lots of info on ce5/6 netbooks and software.

[http://www.hpcfactor.com/support/cesd/s/0127.asp](http://www.hpcfactor.com/support/cesd/s/0127.asp)

Cheers.

---

### Post by tonyblews on 2010-02-06
> **wicknix said:**
>  Here's the output a user posted on littlelinuxlaptop.com's forums

That'd be the info off my Ubisurfer then. I'm banging my head against a wall over it. How hard can cross-compiling really be?

---

### Post by wicknix on 2010-02-07
Wouldn't be too hard. Just set up OE (open embedded) and start building packages. OE is quite automated and makes cross compiling a breeze.

You could probably use quite a few prebuilt packages in the debian lenny/sid repositories also. Just extract them and their deps from the .deb files, repack as tarballs and copy over to your system and extract.

Cheers.

---

### Post by DonutFUN on 2010-02-07
Your hitting your head over it? Does that meant that's the information that we've been needing this hole time?

---

### Post by tonyblews on 2010-02-07
> **DonutFUN said:**
> Your hitting your head over it? Does that meant that's the information that we've been needing this hole time?
been registered on here less than an hour. had the device less that 3 weeks. i admit i've not hit my head that much, really ;)

---

### Post by DonutFUN on 2010-02-07
> **tonyblews said:**
> been registered on here less than an hour. had the device less that 3 weeks. i admit i've not hit my head that much, really ;)

I just meant that as in is that finally the information we've been needing?

---

### Post by PrFaas on 2010-02-07
Status update: currently downloading from:

[http://www.ubisurfer.com/html/ubisurfersourcecode.htm](http://www.ubisurfer.com/html/ubisurfersourcecode.htm)

Too soon to tell the results (yet..). I just hope those folks did not present the 'vanilla'/kernel.org source as linux source code :)

After downloading 'their' kernel from 

[http://www.ubisurfer.com/downloads/UbiSurferSourceCode/linux-2.6.21.5.tar.gz](http://www.ubisurfer.com/downloads/UbiSurferSourceCode/linux-2.6.21.5.tar.gz)

and the same version from kernel.org, i compared the output of a tar tvf of both: they are identical.... Bit of a pity: nothing new...

---

### Post by wicknix on 2010-02-07
I was thinking more along the lines of having Tony copy (dd) the kernel from whatever device/partition its on, then copy the /lib/modules and toss them all into a tarball and upload somewhere for you guys to test.

Cheers.

---

### Post by max1024 on 2010-02-07
Hello 2 all, may be this link will be usefull for silving a problem [http://kasernet.livedrive.com/frameset.php?path=/files/5244617](http://kasernet.livedrive.com/frameset.php?path=/files/5244617)

---

### Post by DBAlex on 2010-02-07
> **max1024 said:**
> Hello 2 all, may be this link will be usefull for silving a problem [http://kasernet.livedrive.com/frameset.php?path=/files/5244617](http://kasernet.livedrive.com/frameset.php?path=/files/5244617)

Hey, those files seem to be for:
[http://www.youtube.com/results?search_query=yf700&search_type=&aq=f]("http://www.youtube.com/results?search_query=yf700&search_type=&aq=f")

[http://www.thinclient.co.th/product/dowload/YF700.pdf]("http://www.thinclient.co.th/product/dowload/YF700.pdf")

Also, anyone have any information about this product on eBay: [http://cgi.ebay.co.uk/Netbook-7-WiFi-Windows-Laptop-Notebook-2GB-Mini-K_W0QQitemZ270527070699QQcmdZViewItemQQptZUK_Computing_Laptops_EH?hash=item3efcab81eb]("http://cgi.ebay.co.uk/Netbook-7-WiFi-Windows-Laptop-Notebook-2GB-Mini-K_W0QQitemZ270527070699QQcmdZViewItemQQptZUK_Computing_Laptops_EH?hash=item3efcab81eb")

CPU type is: WMT,ARM-WM8505

Is the ARM-WM8505 the same as the ARM-VT8500?

Not obviously the same CPU, but they are both ARM, so would any Linux than ran on the VT8500 run on the WM8505 too?

Also, ignore anything about Little Linux Laptop (LLL)... Those laptops use a MIPS CPU, this a totally different arch (ARM), although some of the hardware could be similar. (Seems the sound on the netbook I posted is AC97, which sounds promising for driver support!)

Cheers, Alex. :)

---

### Post by tonyblews on 2010-02-07
> **wicknix said:**
> I was thinking more along the lines of having Tony copy (dd) the kernel from whatever device/partition its on, then copy the /lib/modules and toss them all into a tarball and upload somewhere for you guys to test.

Cheers.

more than happy to do it. 

I've chucked what i think are the correct files, plus other bits at:

[http://www.tonyblews.co.uk/ubi/](http://www.tonyblews.co.uk/ubi/)

Let me know if i've balls it up, as I haven't done any proper work with linux since the mid 90s when a 386 running slackware made an acceptable file server.

---

### Post by PerChristensen on 2010-02-07
Tonys info say his hardware is based on SMDK2450
 
[http://www.samsung.com/global/business/semiconductor/mobilesocProductDown.do?userId=pq.wang%40besovideo.com]("http://www.samsung.com/global/business/semiconductor/mobilesocProductDown.do?userId=pq.wang%40besovideo.com")
 
Perhaps his image will,or will not,give a quack on SD treatment.Thank you Tony.

---

### Post by necro666 on 2010-02-07
isn't this just the same device?!
(well it looks like the black/silver version from ebay - hardware specs are similar)

[http://www.cnmlifestyle.com/](http://www.cnmlifestyle.com/)

they offer download of complete linux source code...
(netbook available with linux or win ce)

regards

---

### Post by tonyblews on 2010-02-07
> **necro666 said:**
> isn't this just the same device?!
(well it looks like the black/silver version from ebay - hardware specs are similar)


This is the pit i fell in to when buying the ubisurfer... the processor is different, and i can't get stuff from the littlelinuxlaptops stuff to work on it.

---

### Post by PerChristensen on 2010-02-07
I could not get Tonys linuxrc Image to quack,unfortunately,but this was my try!.I belive Tonys software is developed on a real view board and his processor therefore not "our" VT variant of the samsung 926EJ-S.
 
Some of the netbooks (those displaying a menu when pressing F1) could be different,I do not know,but the do not boot from SD card as far as I remember.
 
necro666,the CNM book come in two editions,the "silver" with ARM 920 processor and the other with MIPS processor;).

---

### Post by stw89 on 2010-02-08
The Kaser yf700 uses MontaVista Linux right?
 
It seems the MontaVista Linux Professional Edition "Preview Kit" (3.1 and above) can be used to compile the kernel. The preview kit no longer seems to be available though.
 
What is MontaVista Linux Professional Edition? And why does it seem to be closed off to the open source community?

---

### Post by vindy_vindy on 2010-02-08
Hi everyone,
There's a highly comprehensive step-by-step guide on cross-compiling and building a linux kernel from a scratch on non-x86 systems:
[http://www.linuxfordevices.com/files/article037/dreamcast-router.pdf](http://www.linuxfordevices.com/files/article037/dreamcast-router.pdf)
Author of this document uses Sega Dreamcast as an example, but most part of the info can be implemented for our case. Hope somebody have time enough to read, understand and try this.

---

### Post by PrFaas on 2010-02-08
Just to let you folks know: mistake not my silence for inactivity. I have a pile of about 2.5 cm of paperworks (@ 4 pages/sheet) to dig through: The printout of the WinCE bsp of te YF-700, some VT8500-ish datasheet, the arm-926 Technical reference manual and i'm 'picking around' in the arch/arm/mach-* subdirectories of the linux kernel source.

The aim is to compose an arch/arm/mach-vt8500 directory that compiles and results in something that will actually boot a kernel on my WM8505 machine(s)... 

If you can 'head me off' by finding more/better info, or by finding a kernel-source that pre-empts my activity, then no-one will be more pleased than i :)

---

### Post by dhay on 2010-02-08
Hi,

I was looking in google and I found this:
[http://www.alibaba.com/product-gs/268983555/laptop_7inch_laptop_VIA_VT8500_ARM926EJ.html](http://www.alibaba.com/product-gs/268983555/laptop_7inch_laptop_VIA_VT8500_ARM926EJ.html) 
--> Here they say that VIA VT8500 == ARM926EJ.

And later I found this new:
[http://www.gadgetfolder.com/sungworld-7-inch-android-mid-1080p-full-hd-video.html](http://www.gadgetfolder.com/sungworld-7-inch-android-mid-1080p-full-hd-video.html)
--> They say that that company will provide that MID, which has an ARM926 processor, with Android.

Do you think we will be able to run android in this notebook with that data?

Regards,

Dhay

---

### Post by PrFaas on 2010-02-08
> **dhay said:**
> Hi,

I was looking in google and I found this:
[http://www.alibaba.com/product-gs/268983555/laptop_7inch_laptop_VIA_VT8500_ARM926EJ.html](http://www.alibaba.com/product-gs/268983555/laptop_7inch_laptop_VIA_VT8500_ARM926EJ.html) 
--> Here they say that VIA VT8500 == ARM926EJ.

And later I found this new:
[http://www.gadgetfolder.com/sungworld-7-inch-android-mid-1080p-full-hd-video.html](http://www.gadgetfolder.com/sungworld-7-inch-android-mid-1080p-full-hd-video.html)
--> They say that that company will provide that MID, which has an ARM926 processor, with Android.

Do you think we will be able to run android in this notebook with that data?

Regards,

Dhay

The observation that arm926 == VT8500 is correct, but incomplete: A VT8500 chip does contain an arm926 CPU as core, but lots & lots of I/O as well. Making a linux kernel for an arm-926 is rather easy, but: unless you also find a way to access that I/O, the kernel you'd build has no way to communicate with the outside world. An 'autistic' kernel is a bit of a bore :)

---

### Post by PrFaas on 2010-02-09
On a slight 'tangent': Does anyone here have an account for a thing that goes by the name of 'pudn'? While scanning for sources, i stubmled upon an url for a set of u-boot sources:

[http://en.pudn.com/downloads93/sourcecode/embed/detail363883_en.html](http://en.pudn.com/downloads93/sourcecode/embed/detail363883_en.html)

the u-boot is seemingly for the VT8430 CPU (quite similar to 'ours'), but the folks 'over there' at pudn want a usercode/passwd before letting me download it. I do not know if that source has anything sensible/relevant inside ;we are *not* interested in yet another mirror of the official u-boot code, are we now :) . The road towards that code was to start google-ing for 'VT8430 linux'. While the VT8430 is *not* our CPU, it does look a lot like 'ours', so presumably we could 'recycle' some of whatever may float to the surface while stirring the pond with VT8430 as stick.

---

### Post by PrFaas on 2010-02-09
At the risk of becoming annoying, the first installment of what may well become a series of 'entries' of what i'm doing about getting linux a-running on the VT8500/WM8505 . If y'all feel that i'm getting over-talkative, please say so. 

My reasons for being so verbose is that some in this thread have mentioned various levels of competence, i think i can -in the end- get somewhere, but i will benefit from feedback on the way.
I have never actually 'built' a lsp (Linux Support Package) for a new 'CPU' before, and i have no doubt that i will stumble into 'blind alleys', 'dead ends' and make other mistakes in my attempts.
 
Also: by being verbose, i can give you all some insight of where and when there is progress, and where and when -i for one- get stuck. 

1) The toolchain i'm using is the CoudeSourcery one, as downloaded & installed from

```

http://www.codesourcery.com/sgpp/lite/arm/portal/package5385/public/arm-none-linux-gnueabi/arm-2009q3-67-arm-none-linux-gnueabi.bin

```

'Arm' itself recommends that one, who am i to disagree :) I've 'run' that (chmod a+x of the file and run it), which seemed to work fine on my system. The install seems ok. I've installed into my home-dir, resulting in a dir $HOME/CodeSourcery/Sourcery_G++_Lite/bin , where all the arm-tools now 'live'. 

the command:

```

arm-none-linux-gnueabi-gcc-4.4.1 --version

```

now gives me:

```

arm-none-linux-gnueabi-gcc-4.4.1 (Sourcery G++ Lite 2009q3-67) 4.4.1

```

I've also set up the vars for kernel corss-compiling:

```

prf[~]$ echo $CROSS_COMPILE
arm-none-linux-gnueabi-
prf[~]$ echo $ARCH
arm

```

and made sure that the $HOME/CodeSourcery/Sourcery_G++_Lite/bin is in my $PATH .

That should 'do it' as far as the toolchain is concerned. By setting these shell-vars i have somewhat 'poisoned' my system: the default setup for the compiler is now to cross-compile for 'arm', and that may get in my way if i want to compile any 'native' apps, but i think i can live with that for the moment.

2) kernel source: i've downloaded & unpacked the 'kernel.org' one for linux-2.6.32.7 . I have no particular reason for going with this 'latest' (at this moment..) version. I think it will not be all too much trouble to 'switch' to another kernel should the need arise.

3) documentation: 

3.1) for now, i'm using the arm-926 technical reference manual, as downloaded from 'arm':

```

http://infocenter.arm.com/help/topic/com.arm.doc.ddi0198d/DDI0198_926_TRM.pdf

```

That gives the description of the 'core' CPU of our machine. From 'that one', i've gotten the idea that the CPU includes the mmu and cache, as well as that setting the correct CPU in our toolchain should get the compiler to have a basic understanding of what assemler instructions to use.

3.2) the WinCE bsp for the YF-700: see some previous post. A set of include files is the most interesting thing i could find there. That bsp is -so it seems- for the VT8500, so that should give us some idea as to how the I/O of our SoC is organized.

3.3) the datasheet of the VT8430: also some previous post: i'll treat the information in that datasheet with some mistrust: it *is* for a different chip than what we have, but some cross-checking already revealed that there are many similarities.

4) My target machine, with operational RS232-line, using minicom at the 'other end'. Also described before. Having that allows me to check with the actual system how it feels about the strange proposals i'm about to send to it. The u-boot autoboot of the 'target' can be interrupted with that serial line, and i can md.b (u-boot command) into the target to check memory values and see if my machine has something sensible at the addresses of which i think that they should contain I/O. 
One note: my target machine is a WM8505 by now. That may result in some differences between what a VT8500 does and what my machine does. I'm sorry: i only have WM8505's now, and i'm not about to buy a 3-rd machine just to get my hands on another VT8500 again. 

5) My development machine has an (USB..) extra LAN card, configured for IP = 10.1.8.37, with tftp server configured: that allows me to download & boot kernels. the same could be done with an sd-card, but this is what i prefer.

4) A ToDo/ToFindOut list. Quite a long list at the moment. 
- Basically, i've added a arch/arm/vt8500 subdir to the linux kernel tree, and played around with the Kconfig file at arch/arm .. The differences between the original and 'mine' -so far- are:
```

> config ARCH_VT8500
>       bool "VT8500/WM8505 based mini laptop"
>       select ARM_AMBA
>       select ARM_VIC
>       select HAVE_CLK
>       select COMMON_CLKDEV
>       select GENERIC_CLOCKEVENTS
>       select ARCH_WANT_OPTIONAL_GPIOLIB
>       help
>               This enables support for the VT8500/WM8505 mini laptops
>

```

That *is* mostly guesswork. It does attempt to 'set up' for configuring 'make menuconfig' for selecting our vt8500 as target machine

- In arch/arm/vt8500, i've got 
-- a Makefile mostly empty
-- a Makefile.boot . interesting, that's whare the boot-address seems to live... I've copied te following into it   
```

   zreladdr-y   := 0x00008000
params_phys-y   := 0x00000100
initrd_phys-y   := 0x00800000

```

The list of other files so far is:

```

.:
total 20
-rw-r--r-- 1 prf users   66 2010-02-07 13:35 Makefile
-rw-r--r-- 1 prf users   85 2010-02-06 17:25 Makefile.boot
-rw-r--r-- 1 prf users   29 2010-02-07 13:36 core.c
drwxr-xr-x 3 prf users   17 2010-02-05 21:21 include

./include:
total 0
drwxr-xr-x 2 prf users 23 2010-02-07 13:27 mach

./include/mach:
total 4
-rw-r--r-- 1 prf users 1584 2010-02-06 15:42 platform.h

```

As you can well imagine: mostly a 'work in progress' :)

That's 'it' for now....

---

### Post by DonutFUN on 2010-02-09
So, (this may be a couple stupid questions) what linux are you trying to get workking on these? is it Ubuntu, or does it just happen to be under this forum? and also, would it be hard (or possable) to get/make a program for windows ce to figure out the I/O's?

---

### Post by PrFaas on 2010-02-09
> **DonutFUN said:**
> So, (this may be a couple stupid questions) what linux are you trying to get workking on these?
is it Ubuntu, or does it just happen to be under this forum?


What i'm doing has -in itself- nothing to do with ubuntu. Should i get a kernel working, then there is very little to stop anyone from compiling/installing an ubuntu making use of the results. All linux distributions share a common kernel (that's *linux*).  

> 
and also, would it be hard (or possable) to get/make a program for windows ce to figure out the I/O's?


I can give only one short answer to that: i do not know :) 

What i do know, is that for such a program, you'd need a development tool-set (compiler/linker etc..) with which you can make WinCE-on-arm applications. For linux, that would be our 'good-ol' gcc and friends. For WinCE, that would probably be some sort of visual studio, with some sort of WinCE 'add-on'.

One reason for being so 'hell-bent' on getting linux to run on these machines is to allow me to run 'my own' applications on the result :) The machine 'as is' has some useful apps on it, but about zero hope of expanding that.

---

### Post by khephren on 2010-02-09
Was looking forward to posting on here, got one for my girlfriend- it arrived this morning.
Thats the end of the good news. It booted to CE6, connected to  WI-FI fine.

That's when it all goes wrong. I put in a 8 gig  HDSC with some movies, (just to test playback) didn't seem to sit right in the slot. The machine hung. I removed the card and reset. Just get a black screen. Went to unbrick using a normal SD, the spring in the slot won't hold the card :(
start and end of my posting on here!

---

### Post by Bill Carr on 2010-02-09
Hi, folks
Linux experience......now 48 hours ! Most of that just trying to install to an ancient Toshiba Portege 3480CT whose methods of boot are.......seemingly almost non-existent.
Anyway, installing via the incumbent WindowsXP I have been totally unable to install via WUPI
although it does seem to try and try ( for hours on end ! ).
The problem is......memory is just 128megs.  That's right......miniscule. So your ARM machine might suffer from the same prob.
Anyway why am I prattling ? Well I did try a copy of EASYPEASY which I suppose you know is the up-to-date way of saying Linux for an EEEPC.
I installed this into a USB stick and surprise,surprise, it ran without a hitch.
You might try the same with your ARM machine. It isn't going to cost you a dime.
UPDATE
Have splashed out on an extra 64meg of RAM for the Portege, so now boasting 192meg, the absolute maximum allowed by this dinosaur, and am watching Ubuntu 9.10 slowly install.
Wish me luck !
Bill Carr

---

### Post by moblo on 2010-02-09
PrFaas, Just to let you know I really appreciate your in depth updates. It gives me a much better idea of the road to linux. I would also like to extend that to all contributing members. Its amazing the kinds of things you guys can do.
THANKS!

---

### Post by max1024 on 2010-02-09
May be [this]("http://www.pdaxrom.org/index.php/Target_architectures") link will be usefull  ;)

---

### Post by PerChristensen on 2010-02-09
I have got feedback from the company where we tried to by a KASER.It is an old item,and it was out of stock.I hope my oversensibility not has harmed anybody (MatriarkTerVel).
Great with others joining this looong thread.I think Tonys zImage is burned into a hidden partition of his device,but as one of our friends said perhaps he can add some apps if downloading debian archives and do some magic.And a cadeau to PrFaas for his hardcore attitude! - I learn alot.

---

### Post by vinceCOOK on 2010-02-09
Hello Forum,

The classic question here.....i'm afraid..

has anybody actually got linux to work with these chinese
via  vt8050 netbooks?

Is it a proper linux....tpyical and similar to other distro's
e.g. Puppy linux?

--------------------------------------------

This may also be useless to you.

Did anybody look at the "familar project" which is a linux
version for the same cpu chip?

Also, did anybody look at the post that mentions using Gentoo
linux with arm chips?

by the way,it is facinating reading the posts...and watching
how involved the subject is. Even experiments with resistors and
hardware. I understand electronics and was surprised how involved this netbook subject is getting. I noticed that you need to know about address details for programming the SoC.

thanks

V.

Vince.

---

### Post by vinceCOOK on 2010-02-09
Tony, littlelinuxlaptop offers you a free new operating system
for the ubi surfer. It is a free version of Linux that they offer.

They infact have 2 of them You can choose. Download it and burn
it onto a bootable flash pen. It should work with your ubi surfer.

it is called Linux 3MX 4.0

Vince.

---

### Post by vinceCOOK on 2010-02-09
Can this help?

The netbook model called "ubi surfer" uses an ARM chip.
It is linux based.

Vince.

---

### Post by digiapb on 2010-02-09
I just wanted to take a quick moment to chime in and say thanks to all who have been working so hard on getting Linux running on these smartbooks. 

Unfortunately, I have no experience in building Linux from scratch or trouble shooting I/O. 

I have been following the thread, and wanted to at least offer encouragement, and thanks.

---

### Post by wicknix on 2010-02-09
> **vinceCOOK said:**
> Tony, littlelinuxlaptop offers you a free new operating system
for the ubi surfer. It is a free version of Linux that they offer.

They infact have 2 of them You can choose. Download it and burn
it onto a bootable flash pen. It should work with your ubi surfer.

it is called Linux 3MX 4.0

Vince.

Actually, i built 3MX, and no, it wont run on his UbiSurfer. 3MX is built for the netbooks with the Ingenic MIPS cpu. The UbiSurfer is ARM based (or at least the newest versions of the UbiSurfer are) which is why i was hoping Tony's files would help out. Also 4.0 isn't the latest release. My latest is Ultra found here: 
[http://linuxlaptopforum.ark2webdesign.co.uk/index.php/topic,794.0.html](http://linuxlaptopforum.ark2webdesign.co.uk/index.php/topic,794.0.html)

> **PerChristensen said:**
> 
Great with others joining this looong thread.I think Tonys zImage is burned into a hidden partition of his device,but as one of our friends said perhaps he can add some apps if downloading debian archives and do some magic.And a cadeau to PrFaas for his hardcore attitude! - I learn alot.

I'm almost certain that is the case. The mips netbooks have 3 or 4 partitions (depending on brand and internel nand size). One holding the bootloader (uboot), one holding the kernel (uImage), and 1 or 2 holding the operating system and/or storage partition. He would need to use dd to make an exact copy of the ubisurfer kernel. The hard part is figuring out which mtdblock it's on. I'm sure it's not the same as my mips Alpha400.

Cheers.

---

### Post by PrFaas on 2010-02-09
> **PerChristensen said:**
> I have got feedback from the company where we tried to by a KASER.It is an old item,and it was out of stock.I hope my oversensibility not has harmed anybody (MatriarkTerVel).
Great with others joining this looong thread.I think Tonys zImage is burned into a hidden partition of his device,but as one of our friends said perhaps he can add some apps if downloading debian archives and do some magic.And a cadeau to PrFaas for his hardcore attitude! - I learn alot.

Just in case you're inclined to give ordering another VT8500/linux 'box' a try :) :

```

http://www.kasercorp.com/productcart/pc/viewPrd.asp?idcategory=17&idproduct=80

```

I had a look at the shipping rates: above & beyond the price of the actual device for my location :lolflag: 

NB: It could be that i'm just 'teasing' you with a pointer to the same device that you did not manage to actually get 'underway' before. I have not so accurately double-checked if this is a different 'source' from the one where you attempted to order one before. If so: please ignore :)

---

### Post by DonutFUN on 2010-02-10
Ya know, I wanted to thank everyone who is hepling with this as well, I got this for christmas, and its pretty much useless 
i wanted a netbook running xp just to play old games at a friends house (half life 1, diablo, starcraft etc.) (not that i'm greedy and expected anything like that for christmas, i've just been telling him that when i get a job I want one, hard to get a job here right now)
so my dad saw this and thought it would be good, for some reason he hates netbook's and is determined there all crap and "don't waste your money on that" and by getting me this probably is trying to proov there crap and convince me to buy a full laptop when i dont want/need one
I've tryed everything imaginable to get just quake or even doom to work on this, nothing, and my last hope is getting Linux, and using a Linux vertion of quake/doom
 
So that's why I've been folowing this thread so intently, I don't know much about linux (but have been messing around with it more now) otherwise I'd offer more help, but anything you think I can do just say so! Or even if you just want to use me as a backup for files that the site may go down of, I do have a copy of the vt8500 bsp because someone said i should keep a copy. But ya, anything i can do just say!!
 
And thanks alot again!

---

### Post by zaphod_2000_de on 2010-02-10
Hi there,
I have been following this thread closely, while my netbook is still on the way from HK to germany. Thanks to all of you who put so much effort into this, it would be great to have this little beast running Linux.
Anyway, today I found a download link for two linux images for this little netbook...they are published, incuding sourcecode, on the following website:

[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7BEsupport.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7BEsupport.htm)

As far as I saw, you can download Linux for two slightly different versions of the netbook (Minibook and** CnMbook)**.

Sourcecode is here:
[http://194.150.201.35/cnmlifestyle/cnmbook/sourcecode.htm](http://194.150.201.35/cnmlifestyle/cnmbook/sourcecode.htm)

A variety of drivers and Patches can be found here:

[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7BEdownloads.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7BEdownloads.htm)

Plus, there is a page about upgrading the kernel. Sorry I cant try any of this stuff, but my netbook is still on its way. Hope it helps, anyway.

kind regards,
zaphod

---

### Post by nextvolume on 2010-02-10
The CnM netbook which ships with Linux preinstalled doesn't even have an ARM cpu, it instead uses a MIPS cpu, so it's totally out of the question.

I downloaded that u-boot archive from pudn and you can download it [here](http://tails92.sepwich.com/files/easypc/source/19854804u-boot-1.1.4.tar.gz)

---

### Post by zaphod_2000_de on 2010-02-10
Hi again,
on this page they say the CmN Silver uses an ARM...

[http://194.150.201.35/cnmlifestyle/cnmbook/cnmbookspecification.htm](http://194.150.201.35/cnmlifestyle/cnmbook/cnmbookspecification.htm)

well, nevermind.....too bad...:(

---

### Post by PrFaas on 2010-02-11
> **zaphod_2000_de said:**
> Hi again,
on this page they say the CmN Silver uses an ARM...

[http://194.150.201.35/cnmlifestyle/cnmbook/cnmbookspecification.htm](http://194.150.201.35/cnmlifestyle/cnmbook/cnmbookspecification.htm)

well, nevermind.....too bad...:(

I checked that www-site: upon closer inspection, you'll see that the linux version uses a 'mips' while the windows version uses an 'arm'. 

Which slowly makes me start to wonder: is there some kind of conspiracy 'out there'? One that dictates that each and every device released with an arm CPU is only delivered with Windows 'Crippled Edition'?

---

### Post by vinceCOOK on 2010-02-11
Hello,

Well listen people....if you know anything about Microsoft. They
sign an agreement witht he hardware makers. Bill gates gets his bootrstrapper into the actual hardware of the companies boards.

The agreement states that "no other" operating system is allowed to be installed on that hardware but windows. The agreement also stipulates that they are not allowed to dual boot either.

not many people know this...it is how microsoft became so wealthy....

"he who owns he bootloader..."

this is just a general comment by me. It is intended as a reply to comments about a concpiracy that only windows is allowed on these "arm" netbooks.

v.

---

### Post by vinceCOOK on 2010-02-11
Hello,

Well listen people....if you know anything about Microsoft. They
sign an agreement with the hardware makers. Bill gates gets his bootrstrapper into the actual hardware of the companies boards.

The agreement states that "no other" operating system is allowed to be installed on that hardware but windows. The agreement also stipulates that they are not allowed to dual boot either.

not many people know this...it is how microsoft became so wealthy....

"he who owns the bootloader..."

this is just a general comment by me. It is intended as a reply to comments about a concpiracy that only windows is allowed on these "arm" netbooks.

v.

---

### Post by vinceCOOK on 2010-02-11
Hello,

Did anybody try the "familar project"

this version of linux is designed for those "arm" cpu chips.
It can be written to a flash pen as a bootable Linux distro.

It was primary written to go onto handheld computers like the
compaq ipaq. 

It was worth a mention because you experts may be able to pull
out needed details from he source code about memory addressing locations. (not sure)

The source code is available.

[http://freshmeat.net/projects/familiar/](http://freshmeat.net/projects/familiar/)

also, mention this again....the "Ubi Surfer" netbook uses "arm" chips and has linux on it.

Vince.

---

### Post by PrFaas on 2010-02-11
> **vinceCOOK said:**
> 
he who owns he bootloader..."


If only that is the case, then we're quite safe... 'Our' bootloader is u-boot:

[http://www.denx.de/wiki/U-Boot](http://www.denx.de/wiki/U-Boot)

From the u-boot 'README':

> 
#
# (C) Copyright 2000 - 2009
# Wolfgang Denk, DENX Software Engineering, [email]wd@denx.de[/email].
#
# See file CREDITS for list of people who contributed to this
# project.
#
# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2 of
# the License, or (at your option) any later version.


---

### Post by vinceCOOK on 2010-02-11
hello forum,

i know that with boootloaders msoft can put code into
the hardware. This is not an issue when a computer is booting
to a hard drive master boot sector. But with netbooks the code
is embedded in the chip.

You say that these machines have u-boot ...is it embedded into
the chip?

i should read back in these forum comments....your saying these
"arm" netbooks already use a linux bootloader called u-boot.

This u-boot could still have been compromised Msoft?. The Msoft company may have accessed that bootloader at design stage?.

What about the "Ubi surfer" netbook machine? it is an "arm' chip
and runs linux...i believe so.

i mention this because it does look to be getting exceedingly complex to try to discover literally "a few" address blocks that you need so you can begin hooking up the SoC. There is mention in these posts of just a few adress blocks being needed. This looks suspect to me.Msoft code is secret. This is the only fact know about Msoft code down there. everybody knows that nobody knows it!

V.

---

### Post by vinceCOOK on 2010-02-11
Hello

[http://www.maplin.co.uk/module.aspx?moduleno=261613](http://www.maplin.co.uk/module.aspx?moduleno=261613)

can you see here....at the bootom of the page.

cpu.....Samsung arm9  400 mghz?

this netbook uses Linux.

can this help you?

Vince.

---

### Post by vinceCOOK on 2010-02-11
Hello

[http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27](http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27)

this netbook mentioned on the forum earlier...

it is the identical cpu chip that concerns this forum....and it
is running linux.

maybe they sell this linux as a boot pen drive?....seperate?

can this help at all?

V.

---

### Post by 2048 on 2010-02-11
Ok, this is what I got out of my U-Boot:

```
VT8500 U-Boot 1.2.19.1 (Dec  4 2009 - 17:14:38)

U-Boot code: 03F80000 -> 03FC4A70  BSS: -> 04000270
dram_region0_cfg_val = 0x00B0015B
RAM Configuration:
Bank #0: 00000000 128 MB
ATA init.
boot from spi flash.
SPI Flash Bank[0]: EON (ID=0x1C3113)
SPI Flash Bank[1]: No SPI Flash
flash:
     Bank0: FF000000 -- FF7FFFFF
     Bank1: FF800000 -- FFFFFFFF
Flash: 16 MB
In:    serial
Out:   serial
Err:   serial
### main_loop entered: bootdelay=10

To get LCD Pannel Information
framebuffer at 0x03800000
lcdparam=1,30000,5,800,480,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000
VT8500 LCD Init
logoaddr: 0x03c00000
logocmd="mw.l D8110200 9c;mw.l D8130054 1;nand readblob 3C00000 7D00000"
NAND FLASH ID: 0xECD514B6
NAND FLASH Name: SAMSUNG_NF_K9GAG08U0M (2048 MB)
find find_bbt fe
block4095 tag=74624230  version =1
block4094 tag=62743142  version =1
bbt table is found
<1> Read Header
Load Image Form NAND Flash
Read NAND Flash OK
Header is 0x0006a036 0x80101000

<2> Read Data
Load Image Form NAND Flash
Read NAND Flash OK
BytePerPixel of logo = 2, BPP of LCD set to LCD_16BPP_565
Logo Size: 473 * 459, LCD Size: 800 * 480
Clean LCD screen
Write logo to framebuffer
lcdpwm=2000,4,24
PWM0: scalar=2000, period=4, duty=24
Enable LCD Backlight using PWM0
excute_extract_op
  LCD op: D8110004 | 4000000
  LCD op: D8110024 | 4000000
  LCD op: D8110044 | 4000000
### main_loop: bootcmd="nand readblob 100000 0;go 100000"
Hit any key to stop autoboot:  0
```


```
bootargs=mem=127M root=dev/ram0 rw initrd=0x01000000,32768K console=ttyS0,115200n8
baudrate=115200
ethaddr=00:40:63:00:00:00
ipaddr=192.168.1.2
serverip=192.168.1.1
netmask=255.255.255.0
bootfile="uzImage.bin"
loadaddr=0x02000000
lcdparam=1,30000,5,800,480,48,40,40,3,29,13,1,D8110004|0x4000000,D8110024|0x4000000,D8110044|0x4000000
board_name=VT8500_Benign
TouchIC=0
NoBootProgressBar=1
NoBootInformation=1
battvoltlist=6774,6889,7377,7498,7538,7599,7650,7698,7763,7821,7939
audio.recordselect=LineIn
audio.gpio=4
bltparam=48,2,6,33,150,0,27
lcdpwm=2000,4,24
EthernetIC=1
safeaddr=4000000
bmpaddr=7D00000
ebootaddr=7E00000
logoaddr=3C00000
fbaddr=3800000
logocmd=mw.l D8110200 9c;mw.l D8130054 1;nand readblob 3C00000 7D00000
bootcmd=nand readblob 100000 0;go 100000
filesize=6A
bootdelay=10
stdin=serial
stdout=serial
stderr=serial
ver=VT8500 U-Boot 1.2.19.1 (Dec  4 2009 - 17:14:38)

Environment size: 886/65532 bytes
```

At first the bootdelay was set to 0, but with a script on sd-card it was set to 10, everything else is just out of the box...

My board is like this: [http://blog.hep-cat.de/?p=6408](http://blog.hep-cat.de/?p=6408), the RS232 can be reached by the 4-holes above the two USB-Ports. This U-Boot supports tftp-boot...

---

### Post by vinceCOOK on 2010-02-11
Hello

My post above mentions the Haleon company who have the "swordfish netbook" running linux.

The web site appears to offer the "swordfish linux" version
for download.

not sure...was looking at it. (it is a variant of ocean linux)

can this help?

Vince.

---

### Post by vinceCOOK on 2010-02-11
hello

is this any help

datawind linux....is the distro

and it's the arm chip

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/datawind-ubisurfer-784464/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/datawind-ubisurfer-784464/)

"ubi surfer" netbook

V.

---

### Post by vinceCOOK on 2010-02-11
Hello

Why does the linux files from page 34 of this forum not help?

The ubi surfer uses the arm chip...and you have a linux kernel
there..... plus other files

would it not just boot from a pen drive as a linux distro?

vince.

---

### Post by kshade on 2010-02-11
Hi,

just got my netbook and tried to boot the thin client firmware nextvolume dug up. I couldn't get it to work, it just launches Windows. The steps are

1) Make a script directory on the SD card (I used an old MMC card, hope that's not the problem. Win CE can access it just fine.)
2) Put the contents of the archive in there
3) Boot the device with the memory card inserted and press F1 during bootup

, right?

> **vinceCOOK said:**
> Why does the linux files from page 34 of this forum not help?

Because there seems to be no way to get the image file or sources.

---

### Post by vinceCOOK on 2010-02-11
Hello

Does anybody know if it is possible to upgrade windows CE 
to the Embedded standard windows which has the full windows API in it

then these netbooks could at least be used effectively...?

windows standard embedded will allow you to install and use
normal win32 software titles.

[http://en.wikipedia.org/wiki/Windows_Embedded](http://en.wikipedia.org/wiki/Windows_Embedded)

windows embedded standard half way down

i have the file

V.

---

### Post by kshade on 2010-02-11
> **vinceCOOK said:**
> Does anybody know if it is possible to upgrade windows CE 
to the Embedded standard windows which has the full windows API in it
It's not possible because our netbooks have ARM processors and the Windows Embedded versions you're interested in only run on x86, or IBM PC Compatibles as we said in the olden days.

Also, please stop spamming :p

---

### Post by pauloh206 on 2010-02-11
Hello friends!

Here in Brazil, now we have two options to buy these netbooks in a ecommerce site:
a) The first, with WindowsCE for R$ 299
b) The second with linux for R$ 499 

The link is:
[http://www.compredachina.com/produtos_secoes.asp?desc=NETBOOK&secp=24](http://www.compredachina.com/produtos_secoes.asp?desc=NETBOOK&secp=24)

I really want to be what distro of linux is used, and want to know if it could not be a great help to run ubuntu on them.

---

### Post by vinceCOOK on 2010-02-11
Hello,

i don't know if you know....but Brazil uses a different windows
to the rest of the globe.

i imagine this will probably have some impact here...

Vince.

---

### Post by tonyblews on 2010-02-11
> **vinceCOOK said:**
> hello

is this any help

datawind linux....is the distro

and it's the arm chip

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/datawind-ubisurfer-784464/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/datawind-ubisurfer-784464/)

"ubi surfer" netbook

V.

Nope, doesn't help at all. None of my posts ever do.

---

### Post by nextvolume on 2010-02-12
Good news. Although not as bright as you would want them to be (as in no sources or technical documentation was released).

I managed to hack Kaser's Linux kernel binary for the YF-700 to make PATA detection always fail, and so that kernel always boots.

I made a "mini" distribution for the EasyPC (the Cherrypal Africa should be the same thing but with another logo printed on it) with some goodies such as HTTP, FTP servers, mpg321, mikmod and Elinks among other programs which you can download at
[http://tails92.sepwich.com/easypc_linux](http://tails92.sepwich.com/easypc_linux)

Read the instructions inside the archive on how to run it. You need an SD card with two partitions (the first, small, in FAT and the second, big, in EXT2) basically.There are some issues... but finally something to really run on our netbooks.

---

### Post by digiapb on 2010-02-12
that's great nextvolume.

As you stated, a binary blob is not ideal, but it is a step forward.

Thanks for working on this project; it is appreciated.

---

### Post by kshade on 2010-02-12
> **nextvolume said:**
> I managed to hack Kaser's Linux kernel binary for the YF-700 to make PATA detection always fail, and so that kernel always boots.
That's pretty cool. Did you compile any of the software yourself? Also, it doesn't seem to work with my Netbook but I only tested it with an old MMC card and a Micro-SD card in an adapter. It just boots into Windows CE. System properties say i has an AKARM ARM926-AK7802-266MHz processor, that's the right one, right?

EDIT: Looks like it's not, damn...

---

### Post by nextvolume on 2010-02-12
As a rule of thumb check the insides of your netbook. If there is a VT8500 chip, then mostly likely it will work (the ones with the VT8500 seem to have compatible U-Boot boot loaders, anyway). Otherwise, it means you have to use something else.

---

### Post by PrFaas on 2010-02-13
@nextvolume: i tried your image: my machine is a WM8505, and from the serial console, i see that it 'hangs' on the 

mw.l 0xd800e400 0x0000018b

That implies that it never gets to the point of actually attempting to boot the kernel. I could dump a console-trace, but i'd guess that does not really provide much more info than what i've decribed here: I see the load of the uzImage.bin and the ramdisk, so: the loading seems to work ok. Could you perhaps explain in human-readable terms what you're trying to do with that mw.l :)

Upon closer inspection: From the datasheet (VT8430) i presume you're attempting to set up the lcd controller. Just FYI/off-topic: on a WM8505 machine even *reading* from those addresses (md.b 0xD800E400 0x400) results in a hang. I assume that would be WM8505-specific, so i really should not/will not complain :) Just assuming that i do not really care for the LCD (i have serial...) at this moment, i assume is could modify your script to leave that out... and see where that ends me up...

Without the mw.l's i get a bit further, but still no kernel boot: 'It' now ends with:

```

Starting kernel ...

Uncompressing Linux... done, booting the kernel.

```

So: no luck on a WM8505 so far.... Small wonder really: i assume that the actual kernel will also attempt to access the LCD controller, and crash & burn right there...

I will *really* have to find out where the LCD controller I/O is located at some point in my platform description.

---

### Post by mikkoj on 2010-02-13
I've the same kind of machine.

Tried to read the whole thread, but maybe I missed something....

Isn't the Ubisurfer quite same as machines we are talking bout? The sources are available on the website. Seems to be too easy so I must be wrong :(

-mikkoj

> **PrFaas said:**
> @nextvolume: i tried your image: my machine is a WM8505, and from the serial console, i see that it 'hangs' on the ...



---

### Post by PrFaas on 2010-02-13
I did have a look at the sources provided for the UbiSurfer: as far as i've been able to detect, they are little more than a mirror of the respective sources from the floss-projects. I'd be more than happy to be proven wrong :)
 
Besides, -from the above- there do seem to be some differences between the VT8500 that's the 'main course' here and the WM8505 that i have. The LCD controller registers seem to be at a different I/O address. 

NB: I did have a VT8500 in the very beginning, but i had to return it 'to shop': it went 'lights-out' for no particular reason. I got a replacement from the kind lady at the shop, but that turned out to be a WM8505-based machine. 

Before the 'light-out' of machine #1, i had already bought a 'backup machine', but that too is a WM8505... I now have 2 WM8505's, no more VT8500.

To anyone who *does* get the image as mentioned in the previous posts to boot: could i bother you to post the results of the commands:

- cat /proc/ioports
- cat /proc/interrupts
- cat /proc/dma
- cat /proc/iomem
- cat /proc/timer_list

Some of them are bound to not match for a WM8505, but they point to how & what the kernel has found w.r.t. basic system resources.

I'm going back to checking the I/O addresses of the basic system stuff like the ostimer, interrupt controller and the like. I had planned to get to the LCD next, but so long as there was a chance that the binary image would boot on my machine, i gave a test-run with that priority... a running kernel can be a source of information, even if it is not available in source form :)

---

### Post by nextvolume on 2010-02-13
Well, those mw.l are 32-bit memory writes to set the LCD Control Registers to switch to the 1024x768 video mode, without messing up lcdparam. I actually dumped them after starting the Xorg shipped on Kaser's official root filesystem. Your hypothesis about the LCD Registers on the WM8505 makes perfect sense, they are probably somewhere else (and might even be different??) and that's why both in the script and in the kernel they make the netbook crash.

Can you do a dump of your WM8505 U-Boot and give it to me? I will try to find where they are. I know you are capable of doing that yourself, but I'm very curious about this and four eyes looking is better than just two. =P

Also, try to disable lcdon (like lcdon=0)? I have never tried to do that myself, but it might help.

---

### Post by vinceCOOK on 2010-02-13
Hello forum,

i was wondering if the Linux operating system Called Ocean Lniux for the HALERON swordfish netbook is of any use?  (it is called Ocean Linux)

The swordfish netbook uses the exact same chip vt8500 as your netbooks and the web site offers the Linux operating system download.  It says that the os has to be put onto a pen drive.


It is called the Ocean Linux operating system. (552 megabyte)

see post 23 of this forum. Page 3. (dwinston).

You can download Ocean Linux from the haleron.com website. You may need to
register for a ree account.

[http://haleron.com/index.php?option=com_phocadownload&view=category&id=3:oceaos32&Itemid=69](http://haleron.com/index.php?option=com_phocadownload&view=category&id=3:oceaos32&Itemid=69)


right click and "save target as" on the left hand link.

thx

Vince.

---

### Post by PrFaas on 2010-02-13
> **nextvolume said:**
> 
Can you do a dump of your WM8505 U-Boot and give it to me? I will try to find where they are. I know you are capable of doing that yourself, but I'm very curious about this and four eyes looking is better than just two. =P


I had already dumped my u-boot :) I was in fact some part 'underway' into making a 'disarm' (arm-disassembler) program and have a peek at what that u-boot was actually doing...

I've uploaded my u-boot 'dump' to the following url:

[http://download.zenwalk.org/people/prfaasse/mini/uboot.l.dump.gz](http://download.zenwalk.org/people/prfaasse/mini/uboot.l.dump.gz)

It is the md.l dump . I also have it as md.b, but for 32-bits instructions, i guess that .l makes more sense. Ah, and now you also have a pointer to the actual lair of 'yours truely' :)

---

### Post by digiapb on 2010-02-13
vinceCOOK, 

I saw that bit back, and thought I had something as well. 

BUT...

"Ocean OS for Netbooks 32 Bit" is for the: Swordfish Net _10 Netbook_ (atom)
If you click the download, it says it is for the 686



Swordfish Mini _7" Smartbook_ Computer (ARM-VT8500) does not appear to have that OS available....

You could push on haleron, and ask them to release the ARM version of Ocean OS, as of this moment, they have not made it available...

---

### Post by vinceCOOK on 2010-02-13
Hello,

you know....the idea of buying the Swordfish Netbook and then extracting the Linux (it may even be a PEN of the Linux) to share it with forum members.....is very common sense.

This thread has many people....if they all chipped in to reach half of the netbooks cost.....it would be just 4 dollars per person. (half the cost is $95...)....paypal)

Order the netbook from Haleron. (Swordfish...Linux version). Then
extract the linux and hand the linux distro out here...

job done. (common sense)

V.

---

### Post by vinceCOOK on 2010-02-13
Yes

[http://www.liliputing.com/2010/01/haleron-swordfish-mini-7-inch-smartbook-now-shipping-for-149.html](http://www.liliputing.com/2010/01/haleron-swordfish-mini-7-inch-smartbook-now-shipping-for-149.html)

the machine

V.

---

### Post by GeekOfComedy on 2010-02-13
I've been following the forum since christmas and thought it would be time to register but is it really true a laptop for like €50: [http://cgi.ebay.ie/New-7-2GB-HD-Mini-Netbook-Notebook-Laptop-WIFI-Windows_W0QQitemZ230428846098QQcmdZViewItemQQptZLaptops_Nov05?hash=item35a6a12812#ht_5243wt_1060](http://cgi.ebay.ie/New-7-2GB-HD-Mini-Netbook-Notebook-Laptop-WIFI-Windows_W0QQitemZ230428846098QQcmdZViewItemQQptZLaptops_Nov05?hash=item35a6a12812#ht_5243wt_1060)   I'd only buy it if we could run linux but if it's a phone chipset didn't somebody develop linux for phones. But how about running android on it. It is based off linux kernel after all and from there build on. Found this from a google search [http://www.mydigitallife.info/2009/04/23/skytone-plans-to-bring-the-worlds-first-android-based-netbook-to-consumer-market/](http://www.mydigitallife.info/2009/04/23/skytone-plans-to-bring-the-worlds-first-android-based-netbook-to-consumer-market/)

---

### Post by DonutFUN on 2010-02-14
so there is a type of Linux working now, I can't remember if i read this right or not, is there an actual windows system, or is it just text, like in windows terms, is windows running or is it just DOS so far? (I'm away from home until tomorrow so I don't have an extra SD Card I can format, let alone a computer that can format into ext2 right now, just windows here)

Either way I'm ecstatic, it show's tremendous process, especially considering the limited resources we have!
Thank you all again!

Possibly upload an image of what the operating system looks like if not to much trouble?

---

### Post by virus101 on 2010-02-14
hi,i'm from china
 
for all I know 
 
the linux versoin netbook with cpu of "[SIZE=2]Jz4740" not "vt8500" [/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2]just google "Alpha 400" for more[/SIZE]
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE]

---

### Post by dhay on 2010-02-14
hi,

I found this page, I don't know if it would be usefull:
[http://infocenter.arm.com/help/index.jsp](http://infocenter.arm.com/help/index.jsp)

In the left menu are the different models available. In addition here I put the programmers model: [http://infocenter.arm.com/help/topic/com.arm.doc.ddi0198e/DDI0198E_arm926ejs_r0p5_trm.pdf](http://infocenter.arm.com/help/topic/com.arm.doc.ddi0198e/DDI0198E_arm926ejs_r0p5_trm.pdf)

I hope it is usefull!

See you!

Edit: If what virus101 is saying is correct and the processor is the Jz4750, here you can find some information about it: [http://www.dingoo-digital.com/downloads/documents/jz4740-datasheet](http://www.dingoo-digital.com/downloads/documents/jz4740-datasheet)

---

### Post by nextvolume on 2010-02-14
No, EasyPC Linux is just command line for now. I will compile X11 soon anyway. -nextvolume

---

### Post by PrFaas on 2010-02-14
Progress report w.r.t. 'hacking' the WM8505: I think i've 'got' the interrupt controller, uart0 and the interrupt controller --> uart0 connection:

Interrupt controller base address = 0xD8140000
uart0 base address = 0xd8200000
Both as in vt8340 datasheet.. I had my doubts about that, some register values of the interrupt controller did look 'odd'.

uart0:
```

uart0 base address = 0xd8200000
uart0 uses interrupt 32
uart0 transmit data register    = 0xd8200000
uart0 receive data register     = 0xd8200004
uart0 interrupt enable register = 0xd8200014 bit0 = txe int

```

interrupt controller
```

base address = 0xD8140000
interrupt enable bytes[0x40] = 0xd8140040 .. 0xd814007f
 --> value 0x08 enables interrupt, 0x00 disables it
interrupt pending: two 32-bits words 0xd8140080 and 0xd8140084
 --> one bit per interrupt

```

The following commands --> u-boot can be used to check if that is the same for VT8500 :)

```

// checked:
// mw.l d8200014 1  --> enable uart 0 txe interrupt
// md.l d8200000 40 --> i see pending interrupt for txe (0xd8200018 = 0x00000401, '1' = txe)
// md.l d8140000 40 --> no interrupt
// mw.b d8140060 08 --> enable the interrupt 32
// md.l d8140000 40 --> see pending interrupt (0xd8140084 = 0x00000001 = pending txe int)
// mw.l d2000014 0  --> disable the interrupt at the uart
// md.l d8140000 40 --> pending interrupt gone.. (0xd8140084 = 0x00000000)
//

``` 

W.r.t. 'the above: Note that the global interrupt enable is 'off' --> we never actually trigger an interrupt service routine (which would probably fail & crash the machine :)

<edit>
From the www: the interrupt vectors table, could be at either 0x00000000 or 0xFFFF0000. They're -it seems- *not* at 0x00000000, so checking at 0xFFFF0000. There they could well be, but -in the process- found another little piece of information:

There appears to be a addressable memory in the range of 0xFFF80000 .. 0xFFFFFFFF... When you think about that, it makes sense: assuming the SoC pre-loads the spi bootflash using internal 'firmware'. If the main 128 Mbytes RAM is at 0x00000000, it could not easily load at that address: it lacks -at that moment- the info for configuring & refreshing the sdram. But: if the SoC itself has some RAM -say 512 kBytes- 'high', then it can load the bootloader into its internal RAM, and work from there. It will be up to u-boot itself to configure the SDRAM, -possibly relocate itself into that RAM- and get 'things a-rolling'.

I also dumped that 'high' memory, might be interesting :) I had assumed that the text from u-boot as to where it found itself (0x03F80000 --> 0x03FB6FAC, from the serial boot-messages) would be where it was loaded, but that seems wrong... 

So far: i can 'tick off' the interrupt controller & uart0 from my 'todo' list. I think that for an actual minimal linux kernel i still need:

- timer: as far i know, linux *really* needs a timer...
- i'd *love* to find the system controller... It should be not so hard to find: the memory size is in some bits there... 
- display (i think i can get away with just bit-banging the fb bytes for now..)
- find out how to 'proclaim' to the kernel that i've 'got this' devices....

Oh, and 'my' minimal kernel is probably *not* (yet..) going to result in many happy faces here: if i can get a full set of boot-messages of a kernel that starts and boots before it becomes very unhappy about not finding any root-filesystem, i'm getting somewhere.... 

Come to think of it, i *could* perhaps link that kernel up with an initrd, but i expect to have little more than a serial port as I/O devices initially :) For later...

---

### Post by mikkoj on 2010-02-14
[QUOTE=Read the instructions inside the archive on how to run it. You need an SD card with two partitions (the first, small, in FAT and the second, big, in EXT2) basically.There are some issues... but finally something to really run on our netbooks.[/QUOTE]

Feel really stupid: why can't I mount the ext2 partition?

1st is fat and mounts automatically. Second is type 83 or "linux". I can not mount it any way. I tried primary, logic and even bootable...
 
I made a directory /mnt/sd2.
I tried to mount
mount /dev/sd2 /mnt/sd2 -t ext2

I get something like invalid filesystem type, bad table (can't remember excactly).

For some reason 2nd partition is not seen by linux. Where am I going wrong and why it's just me so stupid...

- mikkoj

---

### Post by vinceCOOK on 2010-02-14
Hello

does this give any motivatin to the forum....it was an email from haleron about the vt8500 ARM chipset netbook.

The Swordfish Smartbook on the otherhand uses the VIA VT8500 (ARM926EJ-S) Chipset. Unfortunately we do not have the linux version ready for the via processors yet. This will be our Ocean lite OS. We are hoping that it will be completed by the end of the month. Once finished it will be available on the website for download. There is however a linux 2,2 system available. I am not sure who develops it but I will ask our Software engineers if they can post a copy on the new server for download. I know the problenm they had with the generic 2.2 is the programs compatibility issue and drivers issue. That is why we have developed the Ocean Lite. Unfortunately, it is not ready for distribution quite yet, but very colse. Once ready it will be placed on the haleron.com support downloads. I will try to keep a note to advise you of the availabliliy. However, if you have a different set of hardware, it may not work as these smaller versions driversets are hw specific to keep them lite. They are not very scalable. That is due to the policy of Via not to support Linux directly. They rely on the Open Source folks to build with their tools. I am very sorry for the confusion on the initial communications. 

Regards,

Roberto

------------------------------------------------------------

they are saying the "Ocean Lite Linux" will be ready for our netbooks and available for download by the end of the month.

They also mention that there is a Linux 2.2 version which already
appears to boot on these vt8500 chip machines. It is available now but has some issues.

hope this helps...

Vince.

---

### Post by PrFaas on 2010-02-14
> **vinceCOOK said:**
> 
they are saying the "Ocean Lite Linux" will be ready for our netbooks and available for download by the end of the month.


1-st: very good news that the 'wall of silence' seems about to be breached. This 'WinCE-only' thing can only last as long as there is not a single vendor that does otherwise. I just hope that that Haleron Ocean Linux includes a kernel source: If Haleron releases that then 'we all' have source. 

> 
That is due to the policy of Via not to support Linux directly. They rely on the Open Source folks to build with their tools.


2-nd: may i take the occasion to vent a little sneer at the 'policy of via' as mentioned above :) Great work via: refuse to provide a datasheet, that is surely *the* way to get the 'Open Source folks' to provide support for your chips. :frown:

> 
hope this helps...


Well, the haleron www-site is about to get some 'polling', to see what may 'pop up' there :) In other words: it sure does. I won't give up my 'peeking about' in the internals of my WM8505 for now: 
WM8505 is not identical to VT8500, but the two do seem rather similar. And for the VT8500 'true' machines-owners: you just might see your machines 'unchained' soon :)

---

### Post by DonutFUN on 2010-02-14
This is all so awesome, and of course as soon as you guys get *something* booted there's someone else coming out with one, I'm having a really good weekend since I found out that there was finally something, and even better now!
now I just have one question:
is there a possibility that I could just have 1 fat partition with the scripts and put the other stuff onto a fat32 partition instead? the thing is that this is my only big SD card, and I need the space for this thing, and I don't want to loose the space when I'm in windows CE, and I can't afford to buy another one.
:popcorn:

---

### Post by nextvolume on 2010-02-14
Unluckily there is no way to do that as the kernel which is used does not support the FAT filesystem. Your best bet is buying another SD card which does not cost that much (I paid mine 5 euros).

---

### Post by DonutFUN on 2010-02-14
ya, I may do that, or what I may do (tell me if this may be plausible) would I be able to eventualy when we have a fully funtional distro put that as my OS on my laptop, and put windows CE on the SD card? would that work, would you be able to rewrite the uboot command to just boot Crippled-edition off of the SD card, and put Linux as my internal operating system?
The only reason I would want that is so I don't have to carry around an extra SD card, and also I am having trouble getting a job due to the recension and have barley any money, just bus fair to look for a job.(and barley that)

---

### Post by DonutFUN on 2010-02-15
well I'm in a very bad mood now and need some help getting this working please

I tried to boot into an Ubuntu live CD (9.04) and formated my SD card how I needed, but then it wouldn't let me write to the ext2 partition, what do I do? 
I also tried my Kubunu that I had installed and the same thing happened
My main OS is Windows XP, and I don't have any blank CD's to load stuff on.

---

### Post by mikkoj on 2010-02-15
I made the same excursion...
 
You have to 1) make the partion AND 2) format / make filesystem on it:
 
1) cfdisk sda
 
2) mkfs.ext2 /dev/sda2
 
where "sda" is the name of your SD-cards device name (depends on how your linux names the devices)
 
Then you have to moun t it, of course (sda2 is the linux partition now, yours may be something else)
 
3) make mounting directory, for axample
mkdir /mnt/sda2
 
4) mount
mount /dev/sda2/ /mnt/sda2 -t ext2
 
Hopefully I wrote it all right....
 
- mikkoj
> **DonutFUN said:**
> 
 
I tried to boot into an Ubuntu live CD (9.04) and formated my SD card how I needed, but then it wouldn't let me write to the ext2 partition, what do I do? 
.

---

### Post by PrFaas on 2010-02-15
Could any of you who get the VT8500 booting linux with sd-card & modified YF700 kernel please consider answering the questions of my post #396?:

The results from the commands:

- cat /proc/ioports
- cat /proc/interrupts
- cat /proc/dma
- cat /proc/iomem
- cat /proc/timer_list

That kernel does not boot with my WM8505, and i'd really like very much to have that info :)

---

### Post by nextvolume on 2010-02-15
I have dumped those files from the proc filesystem just now, download them [here](http://tails92.sepwich.com/easypc_linux/proc_out.tgz)

I could not find /proc/dma and /proc/timer_list

---

### Post by PrFaas on 2010-02-15
@nextvolume: thanks, most helpfull: 

A bit of a pity that the dma is not entered into /proc: it is a bit elusive... For audio, i think i'd *really* need dma, but for now, i think i can 'do without'.

I am about to start 'tickling' the system timers, and now i know where to expect the interrupt :)

As for iomem: some of them, i'd already found, but the viafb/lcdfb could be why my attempts (yesterday.. ) to bit-bang the screen did not work :) I'll have to have another look at the ranges:

07000000-077fffff : lcdfb
07c00000-07ffffff : viafb

perhaps one of those is the actual screen buffer. I could embark on kernel-building with only the uart and the interrupt controller/system timer, but i do prefer to have screen output as soon as i can get it :)

From the interrupts: looks like the linux 'folks' use ostimer1, i had set my eyes on the timer0 (but: as far as i know timer0 can also be used as watchdog.. perhaps they've reserved timer0 for that...) 

Many things to check out.. I know, i'm 'going slowly', but i do prefer to check things out before attempting to 'launch' a kernel: to boot a kernel would be a 'giant leap forward', but we're in mountainous territory right now :) I have attempted to boot about every kernel proposed/mentioned here, but always ended up at the bottom of the abyss.

---

### Post by DonutFUN on 2010-02-15
I tried, and it didn't work, I may try to install Ubuntu to do it in there, but knowing my luck it won't work either, loaded in the CD it said something about "only the root can do that" or something along those lines

---

### Post by mikkoj on 2010-02-15
> **DonutFUN said:**
> I tried, and it didn't work, I may try to install Ubuntu to do it in there, but knowing my luck it won't work either, loaded in the CD it said something about "only the root can do that" or something along those lines

sudo

---

### Post by mikkoj on 2010-02-15
> **PrFaas said:**
> Many things to check out.. I know, i'm 'going slowly',

Keep on going! I'm waiting for your work and trying to learn something here too. 

-mikkoj, vm8505

---

### Post by DonutFUN on 2010-02-15
I tried sudo as well, still nothing, but I did get it formatted how I needed it in the end, I'll say how in a minuite for anyone else stuck in this position like me, its a little overcomplicated, but if you're as presistant as I am then its not really that out of your way.
But I do have 2 questions: Do they need to be named anything particular at all? I couldn't find anywhere if it did, and also is it FAT16 or FAT32, again, I couldn't find any spasific for that, you just said FAT so I assumbed 16, which didn't work for me. but depending on thoes answers here's what I did: (with a 1Gb SD card)
I booted into a Linux live CD (Mine was Ubuntu 9.04) and loaded up the partition editor and went to the SD card, i created a new partition table that cleared everything, so what I did after that was created an ext2 partition of 500Mb, then I made a FAT16 (might need to be 32, which may have been my problem) partition with what was left (like 498 or something) and pressed apply which set it up like that. Once it was done that I extracted the fatpart onto the FAT16 partition, because I could write onto it. then I took out the SD card, and restarted the computer into my Windows XP.
While in windows XP I had installed a program to allow me to read/write to ext2, but it doesn't let me format to it (that is why i had to do the formatting inside Linux) so I put the card back in, and it only recognizes the ext2 part for some reason, but It does let me write to it it the important thing, so I extracted the ext2 part to it, now I may actually have a corrupted .tgz file because it did come up with some errors at this point, but it did let me write to it, and then put it it.
As I said, it didn't work for me, that may be because I have a corrupted file, it may be because they need to be named and I don't know about that, and also it maybe be because it needs to be FAT32, not 16, and I didn't know that.

That's how I did it, it didn't work for me in the end, but it may just be a small thing, please help if you can.
-Thank you

Edit: it wouldn't let me update the program I used, but its called "Ext2IFS1_1 1a.exe" if you need it.

---

### Post by PerChristensen on 2010-02-15
It does not work for me either - booting stops and cannot decompress,say: compressed image found at block 0 on ext2 filesystem - /linuxrc not found.
The problem with owerwriting files perhaps is because not supporting filepath> 100 characters in Windows and by old Linux tar utility,or corrupt ext2part.tgz?.
Let us hope vinceCOOK will get the Linux :p

---

### Post by DonutFUN on 2010-02-15
well i did what I said up there and it does nothing, it just goes right to wince, that's it.

---

### Post by nextvolume on 2010-02-16
Windows doesn't handle symlinks and permissions correctly that's why you are having these problems. You should extract the files at least from an Unix-like operating system which supports the ext2 filesystem (*BSD should work).

By the way, I did a very stupid thing... when you boot the system, fix these permissions:
```
chmod +s /bin/busybox
chmod g-rwx /etc/shadow*
chmod o-rwx /etc/shadow*

```

Multi user wouldn't actually work correctly without doing that.

---

### Post by lkcl on 2010-02-16
guys,

will you _please_ for god's sake create a wiki page e.g. on handhelds.org or _anywhere_ but blunderbuss-style blast vital and valuable information across 43 low-signal-to-noise ratio forum pages full of "me-too" AOL-style postings?

what you are doing is incredibly, incredibly valuable: reverse-engineering an extremely low-cost ARM-based netbook, so that people who otherwise cannot afford a $200 to $300 portable computer can at least buy one of these devices, and still stand a chance of getting at least something a) free b) fairly modern (webkit-based browser for example such as midori).

to "splat" all the information somewhere into a 43-page-long thread on such a stupid place as ubuntuforums is to do yourselves and the people who could benefit from your work, you are doing them and yourselves an enormous disservice.

create a series of wiki pages, and maintain this utterly valuable information there.

make damn sure that the keywords are entered onto the wiki pages so that google searches "linux ARM vt8500 netbook" come up on high priority with the wiki you're going to start - right now.

take a look at [http://wiki.xda-developers.com](http://wiki.xda-developers.com) to see some examples of how to use wiki pages to work on reverse-engineering, for example look up the UniversalResearch page.

the other thing that is absolutely essential that you do is to create an IRC channel (which you reference in the wiki).

using a forum for "nattering" purposes like this is a complete waste of everybody's time.

let me know the name of the IRC channel (use irc.freenode.net) and i can ask tim rikers to add a logging bot for you.  then, you have a searchable archive which people can read up about.

a good wiki can also maintain the files for you.  how the xxxx is anyone supposed to find the incredibly valuable work you're doing?  how is anyone supposed to replicate what you're doing? how is anyone supposed to contribute, when they cannot find the links to the files, because you haven't indexed them and made them easy to find?

come on, guys, get with the picture.  you're doing work that's enormously beneficial, and you're hiding it behind a smokescreen.  stop it!

l.

---

### Post by nextvolume on 2010-02-16
I agree with you fully, it actually is a bad situation (I am partly to blame as well). I have created a channel called #easypc on Freenode IRC just now if you are interested.

---

### Post by DonutFUN on 2010-02-16
I definitely agree with the Wiki idea, and maybe since this is becoming so popular we should make another thread or something for fans, like the people that just want to say "I got one of these recently too and want to thank you for the work you're doing" and just leave this page up for people with actual ideas, and doing the actual work

And I found out what I was doing wrong, i didn't know it mattered which partition was made first, i was making the ext2 partition before the fat part, so it wasn't loading.

---

### Post by kulapu on 2010-02-16
i have a similar set of hardware to that of dwinston91. i tried installing winCE [http://zeng.h1.28823.cn/VT8500Software.rar](http://zeng.h1.28823.cn/VT8500Software.rar)

i noticed that almost everything works except the sound and wifi. i replaced the wifi app with the one from wince_bak.zip. now it's working. the only remaining problem is the sound. i hope one of these days we can get linux or android work fully in one of these netbooks. i'm sure it would be more useful.

keep up the good work guys. this forum has been very helpful. :D

---

### Post by vinceCOOK on 2010-02-17
Hello,

does Puppy linux install on the vt8500 chip netbooks?

I know Puppy and all it's applications load directly into ram. (pen drive)

Puppy then uses external media to save it's state...

maybe it work?

Vince.

---

### Post by Pilotgeek on 2010-02-17
VinceCook,
Puppy will not run. These netbooks have a very different archetecture from x86. Linux distos typically run well on a wide variety of hardware because PCs all follow the same basic structure. These netbooks, however, are based on an ARM processor with a relatively unknown chipset, so even if we can find a version that will run on an ARM, it most likely will have trouble doing anything useful because the way the processor addresses the hardware is different. This is why we need sources or datasheets, so we can figure out how everything works. Unless the version of Linux was built specifically for the VT8500 chipset, it is almost 100% likely that it will not work on these netbooks. I'm sorry to be a party pooper, but you appear to just be naming off random distros and asking if they will work. Don't suggest Damn Small Linux next, you sound like you're heading there. On the plus side, great find with Haleron releasing a Linux OS for their arm chipset, that sounds promising.

---

### Post by vinceCOOK on 2010-02-17
hello

After reading the last post...hmmmmm  

I don't know about hardware and chips sets...

There was this device that has the same arm chip and runs Linux.

[http://www.noh.ro/blog/](http://www.noh.ro/blog/)

software

[http://forum.xtreamer.net/viewforum.php?f=144](http://forum.xtreamer.net/viewforum.php?f=144)

hope to be of some help.

thx

Vince.

---

### Post by PrFaas on 2010-02-17
> **vinceCOOK said:**
> hello

After reading the last post...hmmmmm  

I don't know about hardware and chips sets...



In this particular device, the hardware *is* for all practical purposes the chipset: The entire device consists of -almost- *one* chip with 
- CPU = arm926EJ-S
- all the I/O
- I/O <-> CPU connections

So: Assuming that you find a kernel (source) for any odd arm-926EJ-S, that helps very, very little. As soon as that kernel is going to do I/O to an I/O address that is not the same as in our VT8500 / WM8505 the machine will crash. So, please when looking for pre-built kernels, sources, whatever, keep in mind that 'it' has to be for a VT8500. Any 'arm926EJ-S' is *not* enough. To give an example: 'nextvolume' has managed to 'tickle' the kernel from kaser to boot on his machine. nextvolume has a VT8500 SoC based machine. I have a WM8505-based machine. The kernel from nextvolume does *not* boot on my machine. I -in the mean time- know that the LCD controller of my WM8505 is at a different I/O address than that of the VT8500. I'm quite sure that nextvolume's kernel will attempt to access the LCD controller. From that i can understand that nextvolume's kernel will *never* boot on my machine. And: *both* my WM8505 and nextvolume's VT8500 use the same arm926EJ-S as CPU of SoC. 

The same applies to any kernel you may find 'out there'/'in the wild': unless that kernel is for the precise device you have as SoC, it will be very unlikely that the kernel will boot at all.


> 
There was this device that has the same arm chip and runs Linux.

[http://www.noh.ro/blog/](http://www.noh.ro/blog/)

software

[http://forum.xtreamer.net/viewforum.php?f=144](http://forum.xtreamer.net/viewforum.php?f=144)

hope to be of some help.

thx

Vince.

You're really trying very hard, but please stop looking for 'only' arm926EJ-S, and look for kernels that are for VT8500. If you *really* want to please me: perhaps include looking for a kernel for WM8505 :)

NB: as you can 'see' from nextvolume's troubles with a kernel that *is* for a VT8500 (the YF700 *does* use 'our' VT8500 as 'all-in-one' chip), even then nextvolume had to modify the kernel to get it to actually run on 'our' machines: In this case, the YF700 kernel attempts to us an IDE disk interface, which is not present on our machines. That ends with an interrupt from the non-connected IDE interface, which he -it seems- managed to 'patch out'. Without that patching, the kernel gets into a loop, and becomes effectively unusable.

Conclusion: 

1) Any (binary of a) kernel has to match our machine very closely: a different set of I/O (aka: not a VT8500) --> the kernel will not work. Best would be the *source* of a kernel for VT8500: that we can configure and compile to exactly match our active & present set of I/O.

2) I do not expect *any* of the 'usual suspects' w.r.t. linux distributions te be usable at all: 'they' are usually for a PC or compatible. In other words: something with an x86 instruction set. We're dealing with an arm here: an arm cannot run x86 instructions. W.r.t. arm-based/arm versions of distributions: see pt. 1 :)

---

### Post by DonutFUN on 2010-02-17
Hey, i was just wondering would it be easy/possible to rewrite the u-boot for the VT8500-software.rar so that it boots off of the SD card, and if so how long would it take/would it be hard?

I screwed up my boot by accident (again), and want to get a couple of files off of the laptop before wiping it clean again.

Thanks

---

### Post by vinceCOOK on 2010-02-17
Hello

Prfaas.....thankyou for your detailed explanation about kernels and chips models

It prooves to me just how accurate the forum needs are. My linux understanding is extremely slim indeed. 

it helps give a better understanding.

V.

---

### Post by omrip on 2010-02-17
Just got [www.easypclinux.com](www.easypclinux.com) and a year's hostings-whos with me for getting the hell outta the ubuntu forums as nice s they are and really getting this thing going?

---

### Post by moblo on 2010-02-17
> **omrip said:**
> Just got [www.easypclinux.com]("http://www.easypclinux.com") and a year's hostings-whos with me for getting the hell outta the ubuntu forums as nice s they are and really getting this thing going?

Im liking the ideas that are floating around at the moment. The website is great as we can have a home for the project. im also liking the idea of the wiki and an irc channel. Being able to have a centralised place for up to date info without having to trawl through 44 pages is excellent. I believe we will have a boom in the number of people talking about these netbooks, I can see them being very popular, especially with linux. Ubuntuforums is not the ideal place.

And again, im amazed at the progress that has been made on this linux project. I have been following this thread since page 1 and have learnt so much.hopefully we can make the final breakthroughs and have a working linux (hopefully sooner rather than later on the wm8505!!!)

---

### Post by idiamin on 2010-02-18
omrip you have 3 posts. I don't think most of the people here are sheep. Maybe if you had some useful information we would jump to your site. You paid for hosting? 


On a side note here is a slashdot article about Ubuntu on Arm. [It might be totally unrelated but nevertheless] 

[http://tech.slashdot.org/story/10/02/18/0318253/Enlightenment-Returns-To-Bring-Ubuntu-To-ARM](http://tech.slashdot.org/story/10/02/18/0318253/Enlightenment-Returns-To-Bring-Ubuntu-To-ARM)

I like the Ubuntu forums, they will be here for more than a year.

---

### Post by gecsek on 2010-02-18
I bought a mini 7" netbook from China. It use Windows CE 6.00.  My Question is, can I use it with Linux? It is possible could you send me a Howto (for for Dummies)?

My netbook is:
Processor Type	VIA ARM 32bit CPU
Processor Clock Speed	300M Hz
Processor/Manufacturer	VIA
Processor Model	VIA-ARM VT8500
[http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c](http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c)

Thanks.

---

### Post by omrip on 2010-02-18
Dear Idiamin

hello :)

to begin with let me just say i wasn't trying to offend anyone by taking this web adress i was merely trying to start a new enviorment for VT/VM based linux operations that will center all things VT/VMArmlinux(the IRC channel,testing kernels,tutorials and so on)hopely helping ppl to start working in a method where we all could contribiute and will summ all the main achivements that we have reached until now.
i did pay for the whole thing -foolishly by thinking that because the lack of my programing abilitiles i will be able to asisst someone by doing some thing else.i have no financial asperations for this project-im doing it only because i think its the right thing to do.

sorry for some english mistakes-it just pissed me off and i had to answer.
O.

---

### Post by DonutFUN on 2010-02-18
hey all, just out of an effort to try and help, I know that there are some things that you said should be kept on as many computers as possible just in case the site's go down, now I have the vt8500 BSP from a while back, and I was just wondering is there anything else I should get, and if so where from, can you supply a link, I know you're working from a certain distribution on Linux right now, so maybe direct me to that just so I can keep a backup just in case as well.

as well I don't mean to be a pester, but is it possible to just boot onto windows CE from an sd card so I may be able to save my files, if not just say so, I just want to know if I should wipe my laptop now of if I should bother waiting, if it'll take a week then never mind, but if its easy please say so I know.

Thanks a lot, and I hope to hear from you soon.

---

### Post by moblo on 2010-02-18
> **idiamin said:**
> omrip you have 3 posts. I don't think most of the people here are sheep. Maybe if you had some useful information we would jump to your site. You paid for hosting? 


On a side note here is a slashdot article about Ubuntu on Arm. [It might be totally unrelated but nevertheless] 

[http://tech.slashdot.org/story/10/02/18/0318253/Enlightenment-Returns-To-Bring-Ubuntu-To-ARM](http://tech.slashdot.org/story/10/02/18/0318253/Enlightenment-Returns-To-Bring-Ubuntu-To-ARM)

I like the Ubuntu forums, they will be here for more than a year.

Very good point. Ubuntu forums will be around for more than a year, and we have no info about the website. But it would be nice to have a dedicated home for the project. Maybe the wiki idea would be good, using this forum for a discussion ground and a wiki for work log updates/overall progress.

> **gecsek said:**
> I bought a mini 7" netbook from China. It use Windows CE 6.00.  My Question is, can I use it with Linux? It is possible could you send me a Howto (for for Dummies)?

My netbook is:
Processor Type    VIA ARM 32bit CPU
Processor Clock Speed    300M Hz
Processor/Manufacturer    VIA
Processor Model    VIA-ARM VT8500
[http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c](http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c)
Thanks.

This whole thread is about getting linux onto these netbooks, and as such we dont have a fully working linux yet. Your best bet is to read through this thread to fully understand where we are at in terms of progress. or at least the last 10 pages or so. there is a lot of good information. If you look back, a user, nextvolume, has managed to creat a kernal for your processor that he managed to boot. try looking through those posts.

---

### Post by PrFaas on 2010-02-18
> **gecsek said:**
> I bought a mini 7" netbook from China. It use Windows CE 6.00.  My Question is, can I use it with Linux? It is possible could you send me a Howto (for for Dummies)?

My netbook is:
Processor Type	VIA ARM 32bit CPU
Processor Clock Speed	300M Hz
Processor/Manufacturer	VIA
Processor Model	VIA-ARM VT8500
[http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c](http://cgi.ebay.com/NEW-7-Mini-Netbook-Laptop-Notebook-WIFI-Windows-2GB-HD_W0QQitemZ170414421564QQcmdZViewItemQQptZAU_comp_laptop?hash=item27ad7db63c)

Thanks.

#1 Welcome to 'the club' :) ; 
#2 you seem to have one of 'the original' VT8500's that are discussed here. Seems like you ordered 'yours' directly from some Chinese re-seller. It seems possible to ask questions at the www-site you ordered from. How about asking if 'they' have a linux version? NB: i have no paypal account, or else i'd ask myself :)
#3 there is a preliminary 'hacked' kernel/root-filesystem that does run: check NextVolume's easypc postings.

---

### Post by Pilotgeek on 2010-02-18
@DonutFun:
It is possible to boot into Windows CE from the SD card, but you have to cancel the format process. I know that for some reason, my install gets corrupted every 30ish boot cycles, so I have to restore it occasionally. The restore process goes like this:
1. Upgrades system files (copies kernel and such to internal flash).
2. Boots up temporary, blank CE system.
3. Formats system partition only (it will never destroy the 2gb storage partition)
4. Copies over programs and settings.
5. Reboot.
 
I usually interrupt it after step 1, when it shows the loading Windows CE screen. This is usually enough to make it boot again from the internal drive. Otherwise, at step 2, it loads a WinCE desktop and a window pops up saying "Format internal flash?". It will give a 3 second timer to cancel before it automatically starts the process.

---

### Post by DonutFUN on 2010-02-18
Alright thanks a lot, I didn't know you could interrupt it like that. :D

---

### Post by Mercel on 2010-02-18
Hi
I had problem with netbook **ARM-VT8500**, when I switched ON, netbook stop working on screen  "*System Initializing*", I try copy VT8500 Software to SD card but netbook don't see it. So I try trick from [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm) I copy xip.nb0 EBOOT.nb0 and nboot128.bin
and now my netbook don't turn ON! I try remove batteries, push RESET button -but no effect.When I turn On I can see horizontal stripes, and Capslock, Numlock are flashing on green color. Pls help me
[I]

[/I]*Sorry for my English*

---

### Post by gecsek on 2010-02-18
Can you give a link, on which working Linux I can to download?

I read the remarks, it with SD card thing would work, if would find good Linux version. I try with VT8500Software.rar, but it is Windows CE.

---

### Post by gecsek on 2010-02-18
The speaker is not work, after I installed VT8500Software.rar file. The jack output work fine. Any idea?

---

### Post by Mercel on 2010-02-19
Can you help me? Now netbook don't read any SD card, and USB dont't work

---

### Post by gecsek on 2010-02-19
Ich habe in meinem Netbook hingeschaut. Vielleicht hilft euch:

EPC PC703
Audio: VIA VT1613
Processor: VT8500 0929CD
Flash: Samsung 949 K9GAG08UOM 7CB0
Network: Pulse H1102NL
USB: GL850A MN2FA01G11
RAM: hynix H5PS1G63EFR
Tochpad: HT5330PX (?)
WiFi: BL-RT-3070-50; Ralink RT20702; P1N0930F0
VT6103X
E316362

Ist es nicht so, dass man nur ein Kernel cross-compilen muss, und das mit U-boot aufspielen lassen?

---

### Post by PrFaas on 2010-02-20
> **gecsek said:**
> 
Ist es nicht so, dass man nur ein Kernel cross-compilen muss, und das mit U-boot aufspielen lassen?

#1: my apologies: i'll respond in English to a post in German :) I can read German good enough, but to write it 'error-free' is beyond my skill

#2: the contents of your machine looks 'standard'/default VT8500-machine

#3: w.r.t. the quoted text: if only it where *so* simple, i'd be running Linux on it right now. Yes, you have to cross-compile a kernel, and boot it by means of u-boot. But: for that you need an appropriate kernel source. 'The one' from kernel.org does not include something like a directory ..../arch/arm/mach-vt8500 . That's where 'our' problems come from: we need a kernel-wise description of the contents of our vt8500 SoC, and possibly a bit of the other chips you mentioned. VIA refuses to disclose how that blasted VT8500 is linked up internally.

---

### Post by gecsek on 2010-02-20
Danke. Ich bin so mit Englisch, wie Du mit Deutsch :D

Also deswegen haben wir noch kein Linux für diese Netbooks. Kann man also ohne der VIA kernel-wise description nicht tun? Man kann nur warten, bis es veröffentlich wird? :cry:

---

### Post by PrFaas on 2010-02-20
A 'matching' kernel source -from 'wherever'- would be an enormous boost, but -speaking for myself only- i do not want to wait for and/or rely on getting that. 

I'm digging around in the few resources that we *do* have, attempting to create enough hardware description from that. I will not make promises: the process is way too labourous and error-prone for that, but i think i'm getting quite close to being able to produce a bootable kernel. 

Mind you: i only mention 'bootable': do not confuse that with a kernel that has full support for the hardware of the little machine. So far, i've managed to 'reverse-engineer' the serial port, the interrupt controller, and i'm playing with the system timer. Unless i mess up somewhere, that should allow me to build a kernel with support for those devices. The result would be a kernel that does boot, but 'talks' only to the serial port. Not spectacular, but a beginning. I have 'clues' w.r.t. many of the other devices in the SoC, but i'd prefer to have something that runs before going deeper into those devices. 

I am afraid that i will have to also disassemble the u-boot binary to get more info. Oh, and 'my' machine is based upon a 'brother chip' of the VT8500: my machines (i have 2) both contain a WM8505 as SoC. The WM8505 is -best guess from me- the first chip that the WonderMedia company released after VIA transfered the 'arm SoC business' to WonderMedia. I did already find a few differences between the VT8500 and the WM8505, but noting that -i hope- matters for the 'serial-only' kernel i described above.

There are some signs that one of the 'folks' (haleron) who make these computers is close to releasing a linux version source/kernel, but so far nothing 'shows'. I'd expect 'the result' here:

[http://www.haleron.com/index.php?option=com_phocadownload&view=category&id=29:ocean-lite-os-for-swordfish-smartbook&Itemid=69](http://www.haleron.com/index.php?option=com_phocadownload&view=category&id=29:ocean-lite-os-for-swordfish-smartbook&Itemid=69)

Other than that: NextVolume has managed to hack a kernel binary for the YF700 thin client to make it boot on VT8500-based machines (which does *not* include my WM8505-based ones).

---

### Post by Mercel on 2010-02-20
Hi
I had problem with netbook **ARM-VT8500**, when I switched ON, netbook stop working on screen  "*System Initializing*", I try copy VT8500 Software to SD card but netbook don't see it. So I try trick from [http://194.150.201.35/cnmlifestyle/c...7SErestore.htm]("http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm") I copy xip.nb0 EBOOT.nb0 and nboot128.bin
and now my netbook don't turn ON! I try remove batteries, push RESET button -but no effect.When I turn On I can see horizontal stripes, and Capslock, Numlock are flashing on green color. Pls help me

---

### Post by gecsek on 2010-02-20
> **Mercel said:**
> Hi
I had problem with netbook **ARM-VT8500**, when I switched ON, netbook stop working on screen  "*System Initializing*", I try copy VT8500 Software to SD card but netbook don't see it. So I try trick from [http://194.150.201.35/cnmlifestyle/c...7SErestore.htm]("http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm") I copy xip.nb0 EBOOT.nb0 and nboot128.bin
and now my netbook don't turn ON! I try remove batteries, push RESET button -but no effect.When I turn On I can see horizontal stripes, and Capslock, Numlock are flashing on green color. Pls help me

Auf der SD Karte muss alle Datei (Files) in script Ordner sein. Die Karte muss mit FAT formattiert werden (ich habe mit FAT32 gemacht).
Batterie darf man nicht entfernen, sonst (meiner Meinung nach) wird es nicht mehr funktionieren.
Versuch es nochmal mit SD Karte und mit VT8500Software.rar!

---

### Post by Mercel on 2010-02-20
I try unpack only script VT8500Software.rar to SD card(FAT32), but no effect. I'm afraid that now my netbook don't read SD card and USB. How I can check if netbook read SD card?

---

### Post by nemetron on 2010-02-20
Hey 
what about ubuntu mobile?
ubuntu mobile from what I know has been compiled for the arm?

---

### Post by DonutFUN on 2010-02-20
:confused:
I  have a fairly large problem, I went to plug in the power and the pin on the inside broke off, I haven't turned it on since just in case the pin (which is loose inside somewhere) is touching and may short circuit something.

What I need to know is, I've tried open the stuff up, and I can't, I kinda need instructions on how to open it up, the screen is in the way, how do I get it out? do I need to take the screen off, and if so, how so? (maybe a how-to video?)

I'm sorry about asking these questions like this, but if you can't tell, i just have really bad luck with this laptop.
:confused:

---

### Post by gecsek on 2010-02-20
[http://www.vpk.bme.hu/~gmweb/netbook/china_netbook_inside.jpg](http://www.vpk.bme.hu/~gmweb/netbook/china_netbook_inside.jpg)
[IMG]http://www.vpk.bme.hu/~gmweb/netbook/china_netbook_inside.jpg[/IMG]

---

### Post by DonutFUN on 2010-02-20
Alright, so I take it that means that I do need to take off the screen, but how do I do it without hurting the rubber things? I don't know how to take it off, can you quickly tell me, I don't just want to take a knife to it or something if theirs an easy way.

---

### Post by Pilotgeek on 2010-02-20
Hey DonutFun,
I had the same thing happen to me, the soldering on the power plugs isn't too great. I did not have to open the screen, but did have to unscrew it from the motherboard. Basically, if you take the lower end of the netbook apart, you can get to to it. If you desperately need, I can make a video on how to take these apart and put it on youtube as it's difficult to explain.

---

### Post by PrFaas on 2010-02-21
@gecsek: nice disassembly instructions :) those pictures are going to be some help for 'folk to come'...

NB: 

ref: 'Batterie nie entfernen', my machine has been running for the last 2 weeks with the battery, the touchpad and the keyboard/top half of the base unit removed :) It does hardly ever go beyond u-boot, interrupt, examine memory/write I/O registers though :)

ref: disassembly: i did not disassemble the screen unit: with a bit of pushing & shoving, you can also push free the two plastic 'hooks' that go over the display hinges. I put the display in the 'leaning 45 degrees backward' position, and used a table knife to push the plastic hooks over the display hinges one by one.

---

### Post by Juspur on 2010-02-21
Nemetron is right. How about Ubuntu Mobile for ARM?

[http://www.ubuntu.com/products/whatisubuntu/arm](http://www.ubuntu.com/products/whatisubuntu/arm)

---

### Post by moblo on 2010-02-21
I think more than ever now, making a wiki page would be great. We have so much good quality information on this thread, including all the dissassebly pics, recovery files and all the progress with regards to known addresses, etc. I dont know how to go about doing this but will gladly help write up, etc.

---

### Post by PrFaas on 2010-02-21
@moblo: i too agree: i've just 'dug' my way through the 'timer shop' of the SoC. It looks a lot like the PXA250: a single 'free-running' counter with compare registers. Some little trickery to generate interrupts from it. Still needed: verification of the interrupt vectors, and then i'm ready to start attempting to build a minimal-hardware supporting kernel (yep: from source :) )

NB: i think i *will* have to 'diverge' from pure VT8500 SoC at some point, but so far, the hardware i'm 'using' is identical for VT8500 and -my SoC- WM8505.

Suggested Wiki 'main entries':

- HowTo recover software troubles
- reports and/or pictures of hardware found 'in the wild'
- What doc do we want/where could we attempt to get it
- hardware 'hacking'
- software status / what software for our machines is found.

Feel -by all means- free to comment.. And: yep, i too have no experience with setting up a 'Wiki', i'll have an 'ask around' :)

---

### Post by digiapb on 2010-02-21
I also agree with the need for the wiki.

I would like a basic list of how to identify each version of the smartbook....

---

### Post by PrFaas on 2010-02-21
> **Mercel said:**
> Hi
I had problem with netbook **ARM-VT8500**, when I switched ON, netbook stop working on screen  "*System Initializing*", I try copy VT8500 Software to SD card but netbook don't see it. So I try trick from [http://194.150.201.35/cnmlifestyle/c...7SErestore.htm]("http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm") I copy xip.nb0 EBOOT.nb0 and nboot128.bin
and now my netbook don't turn ON! I try remove batteries, push RESET button -but no effect.When I turn On I can see horizontal stripes, and Capslock, Numlock are flashing on green color. Pls help me

Perhaps a silly question: are you 'dead sure' you're dealing with a VT8500 machine? I'm asking because:

- that blinking of the LEDS is done probably by the SoC. Idem stripes on the screen. I'd say that something is 'alive' in your machine.

- the WM8505 machines have slightly different hardware, which would probably not be able to run the VT8500 software 'faultlessly'. You'd probably have to use the 'equivalent' WM8505 software for those. There is no way that i know of to see the difference between a VT8500 and a WM8505 machine from the outside: the box is the same. In my case my supplier sells VT8500 and WM8505 machines without knowing the difference.

---

### Post by DonutFUN on 2010-02-21
Pilotgeek, it would be really nice if you did put up a video, I've opened up the bottom half, but i couldn't get it apart, i opened it up like a book kinda, but couldn't get the two pieces of plastic apart because the screen was in the way, I'm assuming there's a trick I don't know about.

Please and thank you for the help.

---

### Post by Mercel on 2010-02-21
> **PrFaas said:**
> Perhaps a silly question: are you 'dead sure' you're dealing with a VT8500 machine? I'm asking because:

- that blinking of the LEDS is done probably by the SoC. Idem stripes on the screen. I'd say that something is 'alive' in your machine.

- the WM8505 machines have slightly different hardware, which would probably not be able to run the VT8500 software 'faultlessly'. You'd probably have to use the 'equivalent' WM8505 software for those. There is no way that i know of to see the difference between a VT8500 and a WM8505 machine from the outside: the box is the same. In my case my supplier sells VT8500 and WM8505 machines without knowing the difference.

I'm not sure, I know that something is 'alive' in my machine, but  I don't know how install WM8505 software, because USB and SD card reader don't work.

---

### Post by ce-vt8500 on 2010-02-22
For those of you wondering about emulation on wince with the vt8500, if found three working emulators for it without morphgear or gapi. running snes nes and gameboy colour on mine now.
pretty decent speed.
 
download em here: [http://ce-vt8500.110mb.com](http://ce-vt8500.110mb.com)

---

### Post by moblo on 2010-02-22
> **ce-vt8500 said:**
> For those of you wondering about emulation on wince with the vt8500, if found three working emulators for it without morphgear or gapi. running snes nes and gameboy colour on mine now.
pretty decent speed.
 
download em here: [http://ce-vt8500.110mb.com](http://ce-vt8500.110mb.com)

Do you mind me asking where you found these? Its just that we dont know how reliable they are. Also, how well do they run? Could you possibly post screenshots? Sorry about being sceptical, its just that I have been doin a lot of research into it and couldnt find much at all.

---

### Post by digiapb on 2010-02-22
> **DonutFUN said:**
> Pilotgeek, it would be really nice if you did put up a video, I've opened up the bottom half, but i couldn't get it apart, i opened it up like a book kinda, but couldn't get the two pieces of plastic apart because the screen was in the way, I'm assuming there's a trick I don't know about.

Please and thank you for the help.

Hey DonutFUN,


I had the same issue this morning when I had to disassemble one of these.

In order to take apart the bottom half of the lappy, you have to remove the screen half. (you don't have to disassemble the screen part, but you do have to remove it)

The kicker is this, after you remove the screws from the bottom, and remove the keyboard; you have to gently remove the top peace of plastic to get to the screws that hold the screen to the motherboard. (those screws are also holding the motherboard to the bottom piece of plastic)

In order to do this, with the keyboard removed, close the screen half to about 45 degrees. now from the back side of the hinged, you will see the seam where the top piece of plastic meets the bottom piece of plastic. Place a very small flathead screw driver in the seam and gently separate the the top and the bottom. while doing this, coax the top plastic up and over the metal hinge one side at a time. there is enough give in the plastic to do this, however be aware that on the other side of the hinges, is the feeds for the LCD, and what I believe is the internal USB for the wifi. 

After popping the top plastic, you can easily get to the four screws that hold the screen half to the motherboard, and the motherboard to the bottom piece of the plastic. 

sorry, I can't make a video for you, But I hope this helps with your disassembly...

---

### Post by DonutFUN on 2010-02-22
well that was kinda what I was trying to avoid, thinking I would damage or snap the hinge plastic, but I got it open, kinda ascetically damaged, but oh well, I didn't think it would fit like that :D
Thanks a lot

---

### Post by MattDog on 2010-02-23
you all do know ther is a linux that is 10MB and  is live cd and has a gui even it is called 
**Tiny Core Linux.**

we can probaly use that very easly as a distro for it it is small

---

### Post by PrFaas on 2010-02-23
> **Mercel said:**
> I'm not sure, I know that something is 'alive' in my machine, but  I don't know how install WM8505 software, because USB and SD card reader don't work.

The basics of restoring the WM8505 are quite the same as for the VT8500. You 'just' have to use a different 'rar' archive. I've downloaded 'mine' from:

[http://tails92.sepwich.com/files/easypc/VT8505Software.rar](http://tails92.sepwich.com/files/easypc/VT8505Software.rar)

That is in effect the 'server' of 'nextvolume'. I have already used that archive on both my WM8505 machines, so i guess that -for a WM8505- the archive should be 'ok'. Do not be dishearted by not seeing any activity from your sd-card and/or USB ports. 

As far as i've been able to determine the boot-sequence of these little beasties is as follows:

- hardware reset
- load the contents of the SPI boot-flash into memory (presumably *inside* the SoC) at address FFF80000 .. FFFFFFFF (512 KBytes), 'top' of the memory range.

NB: that part seems to be controlled by the SoC hardware-only. The 'disk-flash' seems to be not involved in that.

- Start the just-loaded code: the actual code is a version of u-boot.
- u-boot initializes the SDRAM, and relocates itself into the SDRAM
- u-boot writes the logo to the screen. That explains the 'stripes' on your screen: a WM8505 is not the same w.r.t. LCD interface. The u-boot does write to the LCD correctly, but the actual 'bitmap' for the screen may well be different for VT8500 and WM8505.. I still have to find & analyse the WM8505 LCD interface (u-boot knows, i 'just' have to find my HowTo in u-boot's instructions..)

Then comes 'part two' of the booting process:

- u-boot checks if there is an SD-card inserted, and attempts to perform a software-update from there (that's how the actual restore from sd-card works).

Finally 'part 3' of the boot-process:

- if no sdcard is inserted, u-boot loads the WinCE kernel from the 'disk flash', and starts it.
  
Now: supposing you've 'updated' a WM8505 machine using the VT8500 software... That VT8500 software does not match with a WM8505, and it will get into problems. To see it blinking with LEDS, and give other SOS signals is no surprise :)

The good news is that -very probably- the 'first part'/'2-nd part' of the booting process is still 'intact'. The SPI bootflash is likely not affected, and still 'does its work', including the firmware upgrade facility. 

I hope that all you'd have to do to 'get back' your machine is to prepare an SD-card with the correct contents (WM8505.rar, extracted, directory /script put on the card & boot with card inserted..) and your machine will put that archive on the flash-disk and get back to sanity.

I just wished you'd have a serial port on your machine, then you'd be able to double-check that u-boot still gets loaded :) Without it you'll be 'flying blind'...

I'm sorry, but i can give no guarantee that 'the above' procedure will actually work and is correct at all, but i'd say it sure is worth a try.

---

### Post by DonutFUN on 2010-02-23
Hey, i've got this thing opened right up now (except for the screen), and have a fairly details (5 mega pixel, but more importantly a good lens) and I took some good pictures of all of the chips separately, front and back if anyone wants them.

But I was also just wondering while I have it opened, whats what inside this thing? from what I understand the ram, cpu and hard drive are all on that one chip right? but what is what on it? and if now where is the other stuff?

---

### Post by nextvolume on 2010-02-23
I think Mercel bricked his netbook, as one of the bins very probably contains U-Boot. Unluckily there are no dumps of an U-Boot for VT8500 notebooks right now (maybe I will ask someone with serial if he can dump it). Otherwise the SPI chip has to be desoldered and then programmed using a SPI flash programmer with the image of the compatible U-Boot.

VT8500Software.rar doesn't update U-Boot at all, it just changes the logo to the "Smart Book" logo. The logo that is on most netbooks by default is "Windows CE". It is done to somewhat mask U-Boot (that's why the first posts in this topic thought there was no BIOS in these netbooks).

That said, I think this place isn't good anymore for this discussion. It has nothing to do with Ubuntu and it is an overall stupid place. For now, there is the #easypc IRC channel irc.freenode.net, shortly I think there will be a forum, etc.

---

### Post by digiapb on 2010-02-23
Mercel, 

What you describe, sounds a lot like what happened when I inadvertently loaded the vt8500 script, on a vt8505. 

My friend and I got machines at the same time from the same source on the same order, His locked up, so I went to reload the software for him, only to brick it further...

Turns out his was a 8505, and mine is an 8500..... 

Anyway, after setting up the SD card with the correct script, I was able to get his back up and running....

give the 8505 script a run, and see where it goes.

FYI, I had to run the process twice with the 8505 script, this first time took forever to boot, and get past "loading Drivers" , but it did not save the setting until the second go at it....

PS:, yes, this would be better served in a stub in a wiki, rather than the main conversation.

---

### Post by PerChristensen on 2010-02-23
I now have a crosscable and will try to make a "dump" of u-boot from VT8500 coming weekend,if I get a small tutorial of how-to.

---

### Post by pauloh206 on 2010-02-23
I recorded the serial view from my CE netbook.
Can it be useful?

---

### Post by PrFaas on 2010-02-24
> **PerChristensen said:**
> I now have a crosscable and will try to make a "dump" of u-boot from VT8500 coming weekend,if I get a small tutorial of how-to.

Assuming you use 'minicom' as terminal program:

- Interrupt the u-boot autoboot by 'press any key' when the machine boots
- i use ^A z to get minicom's menu, and 'l' to select log-file
- the actual dump is the command:

  md.l FFF80000 20000

  in text: dump 32-bits words from address FFF80000, dump 128K 
  words: effectively 512 KBytes, as 32-bits words. The SPI 
  bootrom is 512 KBytes, but for analysis & disassembly, i 
  found that a dump of 32-bits machine instructions is more 
  convenient.

- close the log-file when the dump finishes.

+ as an 'extra': the machine also reports where it is -i presume- actually running the u-boot code. On my WM8505 machine, that 'comes out' at the serial console as follows during the boot:

```

U-Boot 1.1.4 (Dec 14 2009 - 18:18:15)                                                                                    
WonderMedia Technologies, Inc.                                                                                           
WMT U-Boot Version : 0.12.01.00.06                                                                                       
U-Boot code: 03F80000 -> 03FB6FAC  BSS: -> 04004A6C

```

The words at address 0x03F80000 to 0x03FB6FAC seem to also contain u-boot code. You can dump them with a similar md.l command. I think that the u-boot at 0x03F80000 is a relocated/copied version of the one at 0xFFF80000, but i've not really investigated that yet.

Is that enough as a 'HowTo'?

another question: do you know of an 'arm' disassembler that could be used to process the result?

---

### Post by nextvolume on 2010-02-24
Luckily dumping U-Boot from a VT8500 does not require modifications to the hardware. It's very possible to dump U-Boot from Linux as well, check my page about it [here](http://tails92.sepwich.com/easypc_linux/uboot_dump.html)

You can also see my U-Boot dump for VT8500 netbooks.

---

### Post by Colten on 2010-02-24
My problem is similar to this one. I bought a Delstar DS700 Netbook with the following specs:
(According to box)
Samsung 533Mhz CPU
Windows CE 5.0
128MB RAM
2GB Solid-State Drive
(Also a 4GB SDHC card)

Was trying to see if there was some way I could get linux on this thing. Like yours, it has no BIOS. I saw some posts of others saying they got it running but from what I read those netbooks run ARM processors or something?

EDIT: Oops, googled and found out mine actually IS an ARM processor.

---

### Post by cynos.fr on 2010-02-24
I have read this since the first page, and this topic interests me a lot
may be these links could help:

[Handheld Reverse Engineering Tool]("http://handhelds.org/moin/moin.cgi/HaRET")

[typhoon]("http://vivien.chappelier.free.fr/typhoon/")

[www.linux-mips.org]("http://www.linux-mips.org/linux-vr/booting.html")

---

### Post by PrFaas on 2010-02-24
> **Colten said:**
> My problem is similar to this one.
Was trying to see if there was some way I could get linux on this thing. Like yours, it has no BIOS. I saw some posts of others saying they got it running but from what I read those netbooks run ARM processors or something?

EDIT: Oops, googled and found out mine actually IS an ARM processor.

Looking at my kernel source tree, i find a directory: mach-s3c2440 under arch/arm, assuming that the S3C2440 is the cpu we're refering to in this case, i expect that your CPU is:

1) well-documented
2) supported by the kernel.org kernel source
3) an 'arm' :)

You may still have some 'fun' configuring your kernel, and/or finding the I/O addresses of your machine, but your case should be a bit easier than ours :)

---

### Post by moblo on 2010-02-25
> **cynos.fr said:**
> I have read this since the first page, and this topic interests me a lot
may be these links could help:

[Handheld Reverse Engineering Tool]("http://handhelds.org/moin/moin.cgi/HaRET")

[typhoon]("http://vivien.chappelier.free.fr/typhoon/")

[www.linux-mips.org]("http://www.linux-mips.org/linux-vr/booting.html")

Looking at HaRET, I understand its purpose is "a Linux bootloader which works from Windows CE environment (a-la loadlin  for DOS or older Linexec tool for Windows CE)" and "a tool for accessing the hardware internals of a Windows CE handheld to  help get Linux up and running on it." Would this not help us. I know a user in the past also suggested HaRET to us, but I wonder if it has been overlooked. Have we tried running it in wince on our machines? Could it not help?

---

### Post by james3927 on 2010-02-25
Hi
im kinda new to these forums (have no idea how i registered a year ago) just wondering if anyone can give me a quick summary of where progress is at for this project?

I have a 7" windows CE netbook
AKARM, ARM926-AKC
128MB RAM
password ztk works

ive found out that program s for armv4i seem to work on my one, but id like to get linux running on the thing

also ive noticed that loading webpages (like facebook) is slow and sometimes crashes, is this due to lack of ram or processing power, and if the latter can it reasonably be overclocked?

thanks

---

### Post by radu.moisan on 2010-02-25
> **Mercel said:**
> I'm not sure, I know that something is 'alive' in my machine, but  I don't know how install WM8505 software, because USB and SD card reader don't work.

I think the procedure posted at [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm) is for Anyka SOCs (AK7801/2) and may not be compatible with VT85XX, at least as far I can tell considering information available on the net. One thing is for sure, they are different chips produced by different manufacturers.

---

### Post by radu.moisan on 2010-02-25
> **james3927 said:**
> Hi
im kinda new to these forums (have no idea how i registered a year ago) just wondering if anyone can give me a quick summary of where progress is at for this project?

I have a 7" windows CE netbook
AKARM, ARM926-AKC
128MB RAM
password ztk works

ive found out that program s for armv4i seem to work on my one, but id like to get linux running on the thing

also ive noticed that loading webpages (like facebook) is slow and sometimes crashes, is this due to lack of ram or processing power, and if the latter can it reasonably be overclocked?

thanks

you may look at these guys [http://ubuntuforums.org/showthread.php?t=1371492](http://ubuntuforums.org/showthread.php?t=1371492) . They are dealing with that specific kind of SOC (Anyka). The CPU is running at 248MHz it seems and it's possible as far as the manufacturer says to run at max 266MHz. This could be a interesting quest - OCing it (300 may be satisfying) :P.

---

### Post by radu.moisan on 2010-02-25
Although I was mentioning about OCing I think this kind of devices have certain consequences when changing CPU clock frequency - peripheral clock may change and then some peripheral need their drivers rewritten. Just forget about it at this point ;)

---

### Post by cynos.fr on 2010-02-25
[MandrivARM]("http://www.blogeee.net/2010/02/une-version-de-mandriva-mini-en-developpement-pour-processeurs-arm/")

just wait.

---

### Post by zaphod_2000_de on 2010-02-25
Hi everyone,
this may be a bit OT, but I'd like to share it anyway, might be of some interest to all.

@ Mod: if considered inappropiate, plz delete.

My netbook has arrived some days ago, and it is the AK7802 type, with CE 5.0.
Within the /windows folder lives a directory called www, which prompted me to perform a portscan of the little beast. And voila, a webserver is running on port 80 and 443, with the default document directory 

/windows/www/remoteadmin

HTML documents present in this dir are hosted over the net...so the webserver is actually working. (See attachment, hopefully)

I find this as well amusing and a bit alarming, I will definitely perform an audit of the netbook when it comes online, to see if it "phones home" in any way. On the other hand, the hidden webserver is probably slowing down the device, hence I would like to shut it off anyway.

I would like to know if this "feature" is also present on your VT8500-based machines ? Anyone knows what its originally meant for, and how to kill it ?

Second thing, I want to use my netbook for pentesting mainly, and the Win CE 5.0 on my netbook came without a telnet or ssh client. (BTW, I was surprised to see it DID come with the "net" command, so you can map windows and Samba shares from the console)
Anyway, I spent a day or two searching for relevant software, like port scanners etc.

Here is a short list of Applications which run on my netbook, and possibly on yours too:

PocketPutty        (telnet and ssh client)
HaRET               (tool for loading linux)
NbtstatCE_0.05   (tool for discovering and mapping windows shares)
vncviewer
netcat                (the "swiss army knife" for networking)

I obviously used the ARM versions of the respective apps, most of them originally meant for PocketPC 2002 or 2003.
I installed the apps (some work without installation) on my storage card and can start from there...adding icons to the desktop is also impossible in my version of Windows "Crippled Edition", but the apps survive a reboot.

If anyone has a real port scanner or WLAN sniffer which runs on "our" netbooks, plz post...I would be most interested.

Last but not least: Thanks to all of you, who dedicate their time and expertise to the Linux-on-netbook project; I probably won`t benefit because I have the 7802-variant of the netbook, but its fascinating anyway. Keep it up ! ;) 

best regards,
zaphod

---

### Post by digiapb on 2010-02-25
Hey DonutFUN,

glad to hear you got your lappy open, were you able to resolve the issue with your power pin?

Also, have you had any luck mapping out whats what?

---

### Post by DonutFUN on 2010-02-25
Well, I don't know what's what, but as for getting it working again, I don't have my own sottering iron so I got my dad to help, and well, first time it wasn't sottered, second time it was actualy toutching the pin next to it to, so I kinda fried it a bit, it's weird what's happening though, the charge light doesn't come on, and it always says it's 100% charged, in fact I left it to the point of dying, it didn't warn me, and still said 100%, but it does charge even though the light doesn't come on, I think we fried a sensor or something. it works either way though, even though it thinks its pluged in at all times (it doesn't dim after 1 minuite like it should on battery power, it waits 10).
 
I do still have thoes pictures if you guys want them at any time.

---

### Post by digiapb on 2010-02-25
I am glad to hear you back up and running, too bad about the battery charge bit though....

---

### Post by digiapb on 2010-02-25
I am not sure if this would help, but I found the ARM926EJ-S Technical Reference Manual.

I know that we really want the Via VT8500 SOC Reference Manual, but the ARM926EJ-S info might give information as to how Via set things up when developing the system on chip....

Would it be of use to anyone?

---

### Post by Colten on 2010-02-26
Not sure how helpful this is, if at all, but it appears that my netbook is able to be updated:
[http://tracker2map.com/google_youtube.htm](http://tracker2map.com/google_youtube.htm)
I dont really understand how that works, or if its just a program I run, but it appears it does something to the OS before you run the .exe

---

### Post by litch84 on 2010-02-26
> **digiapb said:**
> I am not sure if this would help, but I found the ARM926EJ-S Technical Reference Manual.

I know that we really want the Via VT8500 SOC Reference Manual, but the ARM926EJ-S info might give information as to how Via set things up when developing the system on chip....

Would it be of use to anyone?

Not particularly, the VT8500 (and with all other variants from other vendors) are based on a "Hardware Reference Design" from ARM.

Basically ARM creates a schematic of their "core" (the ARM926E-J in these cases) with a default example of how the core should interface with I/O devices etc...

The ARM core documentation has information on memory access, available I/O ports and routines to access the ports - as such it does not contain information on what the vendor (eg. VIA) has connected to these ports and how the I/O should be used to 'talk' to such devices.

Each vendor's implementation of the reference design would be very similar - but not close enough to prove 100% compatible for one with a kernel made for another.

[EDIT]

**Continuing my thoughts:**

In fact we're probably going to find some drama of compatibility with kernel builds from board to board, since not only the SoC is made by reference design but these laptop motherboards are also based on a reference design from somewhere (Since i've found multiple OEM's for the same ARM 926EJ-S based 'netbook' product).

Also, the Audio, USB and a couple of other devices are external to the SoC and the I/O may differ between the mobo's - hence providing another hurdle to get over.

The only common elements between the netbooks is the fact they have more or less the same components and they all run on the same core.

The Linux Kernel already has full support for the 926EJ-S core, as does the toolchain to compile it - our issues lie within the vendors implementation of the on-chip devices and interfacing with them from the I/O the core provides.

This perspective leaves us in an awkward position as a data sheet from one vendor (eg VIA) for one chip (VT8500) will not likely allow us to put linux on any other netbook with a SoC made by Alcatel, or even the successor to that modelof SoC (VT8505).

Let us hope that once a data sheet is given up (And it will eventually happen, especially for the VT8500 because it's likely its near end-of-life status since two successors have been released (VT8505 + VT8510) - and then VIA has no reason to keep the datasheet exclusive to 'paying customers' - that the differences are minimal with other chips, but my hopes are dim.

---

### Post by digiapb on 2010-02-26
litch84, 
Thats what I thought, but I figured I would mention it in case someone else would be able to make use of the info.

---

### Post by chuck3463 on 2010-02-26
> **Colten said:**
> Not sure how helpful this is, if at all, but it appears that my netbook is able to be updated:
[http://tracker2map.com/google_youtube.htm](http://tracker2map.com/google_youtube.htm)
I dont really understand how that works, or if its just a program I run, but it appears it does something to the OS before you run the .exe
If you get this upgrade to work, let me know.  I've followed the instructions exactly but my Delstar won't upgrade.   The company ignores my email. Thanks.  Chuck

---

### Post by DonutFUN on 2010-02-26
I've got a bit of good news on the other hand
I myself have downloaded those MorpModule emulators, and they do work, a bit slow, but they work! I dowloaded them quite a while ago and just never thought to mention,  and I got them from a different site.

BUT I also just got MiniVMac working yesterday, if you just go onto the Mini vMac site, and go under ports there is a Windows CE one, I'm using the plus one, THE IMPORTANT THING that I didn't know is that the disk image has to be called "disk1.dsk" (I tried everything I could think of, just not that of course) and then just numerically higher from that, disk2,disk3 etc...
at least there's a bit more we can screw around with until Linux is up and running later.

---

### Post by jgundo on 2010-02-27
QUOTE=nextvolume;8631512]Finally! I found randomly how to work around the via_ata_interrupt issue and I've got Linux up and running on this netbook, from SD card, even. =P
I simply give a fatload command with a very small file as argument and wait a bit.
Hopefully it won't screw up your Windows CE installation, though I've not tested that yet.
 
It's still a very long way to a decent distribution (which is hard since the kernel is not really for this hardware), but you can telnet to it and play with it a bit.
 
Here is how you load it:
1) Get the files here, [http://tails92.sepwich.com/files/easypc/easypc_linux.tgz](http://tails92.sepwich.com/files/easypc/easypc_linux.tgz)
2) Put the script directory in the archive on a SD card
3) Put the SD card into the SD card slot into your easy pc notebook.
4) Power on the easy pc notebook
5) Some messages will be printed on the screen when it loads stuff on RAM.
When the screen blanks and scrambled things begin appearing on the screen,
reboot.
 
6) Now your netbook will display a cut 1024x768 image on a 800x480 screen.
Let Linux boot, and do not power off the system when Booting appears.
 
7) Now Linux will boot and it will display its messages on the screen.
 
Some times there will still be the "via_ata_interrupt" issue, reboot until
it goes out.
 
The first time you will do this probably a Kaser Netclient logo will appear on the screen, and it won't mount anything as root filesystem. It seems that it needs to build the bad blocks table for the NAND flash in the notebook, and that seems to take a while. I recommend to wait around 30 minutes, and then power off your system by pressing the power button.
 
Now reboot and keep the SD card in it. Do the same thing and now if all goes well you should be able to telnet to local IP 192.168.1.12. Use root as username, and you will receive a shell prompt, you can then play with it.
 
In [this archive]("http://tails92.sepwich.com/files/easypc/easypc_stuff.tgz") I've included several things, like dmesg, some things from /proc, etc.
 
Now I think the best solution will be creating a root filesystem from scratch, and I think that unless a way to change the framebuffer resolution is found this system is best used remotely.
 
To restore the original resolution download [this file]("http://tails92.sepwich.com/files/easypc/scriptcmds/normal_resolution") and replace the scriptcmd file in the script directory on the SD card with it. Then boot with the SD card inserted as usual and follow what appears on the screen.[/QUOTE]

 
 
 
Has any one tried this  [http://ubuntuforums.org/showpost.php?p=8631512&postcount=109](http://ubuntuforums.org/showpost.php?p=8631512&postcount=109) 
 
I cant get past the Some times there will still be the "via_ata_interrupt" issue, reboot until it goes out.
 
Any Help would be great... so i hope this is the help everyone needs......... i have a via arm-vt8500

---

### Post by jgundo on 2010-02-27
> **nextvolume said:**
> Finally! I found randomly how to work around the via_ata_interrupt issue and I've got Linux up and running on this netbook, from SD card, even. =P
I simply give a fatload command with a very small file as argument and wait a bit.
Hopefully it won't screw up your Windows CE installation, though I've not tested that yet.
 
It's still a very long way to a decent distribution (which is hard since the kernel is not really for this hardware), but you can telnet to it and play with it a bit.
 
Here is how you load it:
1) Get the files here, [http://tails92.sepwich.com/files/easypc/easypc_linux.tgz](http://tails92.sepwich.com/files/easypc/easypc_linux.tgz)
2) Put the script directory in the archive on a SD card
3) Put the SD card into the SD card slot into your easy pc notebook.
4) Power on the easy pc notebook
5) Some messages will be printed on the screen when it loads stuff on RAM.
When the screen blanks and scrambled things begin appearing on the screen,
reboot.
 
6) Now your netbook will display a cut 1024x768 image on a 800x480 screen.
Let Linux boot, and do not power off the system when Booting appears.
 
7) Now Linux will boot and it will display its messages on the screen.
 
[COLOR=yellow]Some times there will still be the "via_ata_interrupt" issue, reboot until[/COLOR]
[COLOR=yellow]it goes out.[/COLOR]
 
The first time you will do this probably a Kaser Netclient logo will appear on the screen, and it won't mount anything as root filesystem. It seems that it needs to build the bad blocks table for the NAND flash in the notebook, and that seems to take a while. I recommend to wait around 30 minutes, and then power off your system by pressing the power button.
 
Now reboot and keep the SD card in it. Do the same thing and now if all goes well you should be able to telnet to local IP 192.168.1.12. Use root as username, and you will receive a shell prompt, you can then play with it.
 
In [this archive]("http://tails92.sepwich.com/files/easypc/easypc_stuff.tgz") I've included several things, like dmesg, some things from /proc, etc.
 
Now I think the best solution will be creating a root filesystem from scratch, and I think that unless a way to change the framebuffer resolution is found this system is best used remotely.
 
To restore the original resolution download [this file]("http://tails92.sepwich.com/files/easypc/scriptcmds/normal_resolution") and replace the scriptcmd file in the script directory on the SD card with it. Then boot with the SD card inserted as usual and follow what appears on the screen.
 
 
 
I have restarted about 50 tims and im still stuck HELP PLEASE

---

### Post by jgundo on 2010-02-27
I have taken this thing completely apart my board is yellow and its Numbers are 
 
p7O6_main_v2
 
the cpu board is:
 
p7O1_cpu_v5
091030
 
the cpu chip is a 
VIA VT8500 
0929CD
TAIWAN
2JA1009831
 
The dram is a ZENTEL
 
 
Hope this helps

---

### Post by PrFaas on 2010-02-27
> **Colten said:**
> My problem is similar to this one. I bought a Delstar DS700 Netbook with the following specs:
(According to box)
Samsung 533Mhz CPU


FYI: [http://www.fluff.org/ben/linux-26/status.html](http://www.fluff.org/ben/linux-26/status.html)

status Samsung SoC's & linux kernel. May be a bit 'dated' :)

---

### Post by nextvolume on 2010-02-27
jgundo, you should use the Linux here: [http://tails92.sepwich.com/easypc_linux](http://tails92.sepwich.com/easypc_linux)
Despite the name of the archive, they're different. easy pc linux 0.1 has an hacked kernel which should always boot, never gets stuck at via_ata_interrupt and is actually a distribution (and not Kaser's initrd hacked a bit). that's why we need a better resource abot this, looking into old posts you believe to have found something new while you have found something that should not be used anymore.

---

### Post by jgundo on 2010-02-27
> **nextvolume said:**
> jgundo, you should use the Linux here: [http://tails92.sepwich.com/easypc_linux](http://tails92.sepwich.com/easypc_linux)
Despite the name of the archive, they're different. easy pc linux 0.1 has an hacked kernel which should always boot, never gets stuck at via_ata_interrupt and is actually a distribution (and not Kaser's initrd hacked a bit). that's why we need a better resource abot this, looking into old posts you believe to have found something new while you have found something that should not be used anymore.
 
 
I will give this a try when i get home from school today ....... thank you up front for the help....... josh

---

### Post by DonutFUN on 2010-02-27
So i take it that just means this one is a step back from the version that I have, I have the easypc_linus0.1 what is the difference? and what is that normal resolution thing?

---

### Post by dan_dan on 2010-02-27
We are waiting for a new release for Easy PC Linux, version 0.1 works fine. Any date for a new version with X11?

Thanks you everyone, mainly thanks to Nextvolume! 
dan_dan


> **nextvolume said:**
> Finally! I found randomly how to work around the via_ata_interrupt issue and I've got Linux up and running on this netbook, from SD card, even. =P
I simply give a fatload command with a very small file as argument and wait a bit.
Hopefully it won't screw up your Windows CE installation, though I've not tested that yet.

It's still a very long way to a decent distribution (which is hard since the kernel is not really for this hardware), but you can telnet to it and play with it a bit.

Here is how you load it:
1) Get the files here, [http://tails92.sepwich.com/files/easypc/easypc_linux.tgz](http://tails92.sepwich.com/files/easypc/easypc_linux.tgz)
2) Put the script directory in the archive on a SD card
3) Put the SD card into the SD card slot into your easy pc notebook.
4) Power on the easy pc notebook
5) Some messages will be printed on the screen when it loads stuff on RAM.
   When the screen blanks and scrambled things begin appearing on the screen,
   reboot.

6) Now your netbook will display a cut 1024x768 image on a 800x480 screen.
    Let Linux boot, and do not power off the system when Booting appears.

7) Now Linux will boot and it will display its messages on the screen.

    Some times there will still be the "via_ata_interrupt" issue, reboot until
    it goes out.

The first time you will do this probably a Kaser Netclient logo will appear on the     screen, and it won't mount anything as root filesystem. It seems that it needs to build the bad blocks table for the NAND flash in the notebook, and that seems to take a while. I recommend to wait around 30 minutes, and then power off your system by pressing the power button.

Now reboot and keep the SD card in it. Do the same thing and now if all goes well you should be able to telnet to local IP 192.168.1.12. Use root as username, and you will receive a shell prompt, you can then play with it.

In [this archive]("http://tails92.sepwich.com/files/easypc/easypc_stuff.tgz") I've included several things, like dmesg, some things from /proc, etc.

Now I think the best solution will be creating a root filesystem from scratch, and I think that unless a way to change the framebuffer resolution is found this system is best used remotely.

To restore the original resolution download [this file]("http://tails92.sepwich.com/files/easypc/scriptcmds/normal_resolution") and replace the scriptcmd file in the script directory on the SD card with it. Then boot with the SD card inserted as usual and follow what appears on the screen.

---

### Post by jgundo on 2010-02-27
Hello all,

I tried the new vr. but it stops at:

[COLOR=Red]card protected!card-->stat---->0x10*****[/COLOR]

any Ideas?

thanks

---

### Post by jgundo on 2010-02-27
so we are still sitting at the same point of my kids not able to play there flash games im starting to wish i never bought this dang thing!

---

### Post by moblo on 2010-02-28
Just to let you guys know I have created the page [http://easypc.wikia.com/](http://easypc.wikia.com/) as a centre for information. With uni work I do not have the time at the moment to complete all of the pages, but anyone can edit pages on this wiki. I have created a basic theme and pages so that we have a starting point. let me know what you guys think and those of you who are in the know, i would appreciate your help in filling out the pages with the information.
Thanks

---

### Post by PrFaas on 2010-02-28
@moblo: seen & registerd for it... :)

Just FYI/FYA: i've attached a small set of scripts:

1) to disassemble a binary dump of -for instance- a u-boot: mkdis. To disassemble was a bit less trivial than i had guessed. I ended up using objdump (from the arm toolset..), but that needs a bit of pre-processing.

2) very 1 <-> 1 : a small awk script to convert a md.b dump from u-boot itself into such a binary 'blob'. Using that one is as follows:

```

awk -f hex2bin <dumpfile >binaryfile

```

NB: i had to rename both files in order to make the ubuntu forum software accept them at all.... I added a nonsensical .txt extension to the filename. Please remove that one :) mkdis is a simple shell-scrips (make chmod a+x to make it runnable), and hex2bin.awk is an awk script....

---

### Post by nextvolume on 2010-02-28
I uploaded a description of the SPI flash contents and a program I made to show saved U-boot environment variables from Easy PC Linux on my site.
Expect EasyPC Linux 0.2 with X11 in this week

Does Wikia allow to export the SQL database? If it doesn't, then putting content in it is uselsss as it wll be gone if something bad happens.

---

### Post by jgundo on 2010-02-28
> **nextvolume said:**
> I uploaded a description of the SPI flash contents and a program I made to show saved U-boot environment variables from Easy PC Linux on my site.
Expect EasyPC Linux 0.2 with X11 in this week
 
Does Wikia allow to export the SQL database? If it doesn't, then putting content in it is uselsss as it wll be gone if something bad happens.
 
 
Im am so looking foward to this will it suport the VIA ARM- vt8500  i can not waint for this thank you in advance

---

### Post by mikkoj on 2010-03-01
> **jgundo said:**
> Im am so looking foward to this will it suport the VIA ARM- vt8500  i can not waint for this thank you in advance

And I'm for vm8505 :)

---

### Post by nextvolume on 2010-03-01
I have uploaded some documents about the VT8500 which I found on the internet [here]("http://tails92.sepwich.com/files/easypc/datasheets"). Two are about U-boot for the vt8500 and one is the datasheets for the soc itself (it resembles the one for the vt8430). Other than this, I have uploaded the source code for U-Boot for the VT8500.

---

### Post by DonutFUN on 2010-03-01
So is this 0.2 going to have wireless? or at least DHCP so I can use the interwebz?
either way that's awesome! am I still going to need the two different partitions?

---

### Post by mikkoj on 2010-03-01
When waiting for the 0.2, I got into trouble.
I messed my system (vm8505) with ver 0.1. I managed to do recovery. I can not find a way to get wifi working. 
It seems that I'm missing the driver dll for the wifi?
In the Settings -> Network Connections I have
- Make New Connection
- ADSL
- Active sync (which was not originally functional, now it seems to be)
- 3 G Modem
- GETCE6B1 (for wired lan I suppose?)
 Shouldn't there be a dll  (in \Windows) and entry in this window for something like RT2XXX ?
If so, could someone please give the dll needed? Or instructions if I got it all wrong.

Best Regards,
Mikko

- waiting for linux

---

### Post by openanky on 2010-03-02
if you have an mini netbook with cpu of "AKARM 926EJ-S AKCHIP" ,you are lucky. now i have some important document to share for you, yes,it is about BSP and BCPA and all source code, 
you can read it and understand 
HOW to port linux, HOW to burn OS,
HOW to enable H.264, H.263, RMVB hardware video codec,
HOW to increase battery life
.... 
**we open a Project**-**Open Forum** on this page [http://mininetbooks.your-board.com]("http://mininetbooks.your-board.com/") 
 
Happy Play,geeks. [IMG]http://illiweb.com/fa/i/smiles/icon_biggrin.png[/IMG] 
 
[]("http://rapidshare.com/files/357834038/zt-n760_with_ANKY.rar")

---

### Post by nooby_sycophant on 2010-03-02
Hey, Been reading this thread with alot of interest, seems like you people are the only hope for these shoddy netbooks ;). altho not im not programming savvy i have found a site which seems to deal with embedded os's **_[www.embedian.com]("http://www.embedian.com")_** not that it means alot to me, but i had not seen mention of it in this thread and thought it may be of use.

Keep up the good work!

(p.s have a green board arm929, And inside next too the reset button is a place for Another button marked usb_boot, may be pointless but had to ask )

---

### Post by moblo on 2010-03-03
I tried sending an email to WonderMedia technologies to request the wm8505 datasheet, but everytime I try to submit the form, the website tells me I need to fill out all field properly. I have tried everything but it wont let me submit. Could someone else try and let me know what happens. the website is: [http://www.wondermedia.com.tw/](http://www.wondermedia.com.tw/)
Thanks guys.

---

### Post by ndefontenay on 2010-03-03
The answer is Android!

---

### Post by digiapb on 2010-03-03
> **moblo said:**
> I tried sending an email to WonderMedia technologies to request the wm8505 datasheet, but everytime I try to submit the form, the website tells me I need to fill out all field properly. I have tried everything but it wont let me submit. Could someone else try and let me know what happens. the website is: [http://www.wondermedia.com.tw/](http://www.wondermedia.com.tw/)
Thanks guys.

I did the same thing for the 8500, and got the same response they must have some messed up code on the page...

---

### Post by moblo on 2010-03-03
> **digiapb said:**
> I did the same thing for the 8500, and got the same response they must have some messed up code on the page...

I thought as much. VERY annoying. Does anyone know how else I might contact WonderMedia. The only other thing theyve got is a postal address in Taiwan, and somehow I dont think Ill get a response. Googling reveals nothing.

---

### Post by disi on 2010-03-04
The form seems to not do anything.
But they hava a post address on the same page:

WonderMedia Technologies, Inc.
1F, 531, Chung-Cheng Road
Hsin-Tien, Taipei 231
TAIWAN

---

### Post by moblo on 2010-03-04
> **disi said:**
> The form seems to not do anything.
But they hava a post address on the same page:

WonderMedia Technologies, Inc.
1F, 531, Chung-Cheng Road
Hsin-Tien, Taipei 231
TAIWAN

Like I said in my post; I know Im not gonna get a response by post. So it would be a waste of international postage costs.

---

### Post by basisbyte on 2010-03-05
These are just Javascript Popups - turn off Javascript in your Browser and it should be working. 

Btw: I even got one of these Mini-netbooks but mine has a 266Mhz ARM926 Processor - so more like the one of the guy with this new forum. If I understand everything right, big parts of a distribution/kernel /whatever must be changed for every different version of the processor? 

This netbook  is a cute little thingy and very useful, and the price is just great -Would love to see a Linux distribution on these netbooks some day soon. 
I'm thinking about putting a small price money on the first group or person who can deliver a working Linux distribution for these netbooks. So I'm willing to give away 500 Euros to the first one/group who is able to build a fully working Linux distri (at least there should be X11 with some kind of window manager a webbrowser and some working apps like kate).

You can take me by the word - this is my company and the guy on the photo is me

[http://www.klickkraft.at/index.php/kontakt.207.html](http://www.klickkraft.at/index.php/kontakt.207.html)

edit:  not the big photo in the animation, the small below :)

---

### Post by openanky on 2010-03-05
> **basisbyte said:**
> These are just Javascript Popups - turn off Javascript in your Browser and it should be working. 
 
Btw: I even got one of these Mini-netbooks but mine has a 266Mhz ARM926 Processor - so more like the one of the guy with this new forum. If I understand everything right, big parts of a distribution/kernel /whatever must be changed for every different version of the processor? 
 
This netbook is a cute little thingy and very useful, and the price is just great -Would love to see a Linux distribution on these netbooks some day soon. 
I'm thinking about putting a small price money on the first group or person who can deliver a working Linux distribution for these netbooks. So I'm willing to give away 500 Euros to the first one/group who is able to build a fully working Linux distri (at least there should be X11 with some kind of window manager a webbrowser and some working apps like kate).
 
You can take me by the word - this is my company and the guy on the photo is me
 
[http://www.klickkraft.at/index.php/kontakt.207.html](http://www.klickkraft.at/index.php/kontakt.207.html)
 
edit: not the big photo in the animation, the small below :)
 
 
lucky,your cpu look like anyka AK7802,
welcome to open-anyka forum: [http://mininetbooks.your-board.com](http://mininetbooks.your-board.com)
all source code open for you

---

### Post by vicarioux on 2010-03-05
Hello. One user of pdaclub.pl -  nick "uht" make linux pack for vt8500 and vt8505. I don know if it work. Maybe this help. [http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo](http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo)

---

### Post by mikkoj on 2010-03-05
> **openanky said:**
> lucky,your cpu look like anyka AK7802,


Well, I think with clockspeed as only evidence, it can be VT8500, VM8505 or anyka - maybe even something else?

The main thing: for the first time for me, I'm also willing to give something (to the opensource community) to support the development of VM8505 (VT8500) linux distro.

This is a good way to show the gratitude and maybe even to motivate a little to do this.

So, waiting for linux X11 and paypal address :)

-mikkoj

---

### Post by mikkoj on 2010-03-05
> **vicarioux said:**
> Hello. One user of pdaclub.pl -  nick "uht" make linux pack for vt8500 and vt8505. I don know if it work. Maybe this help. [http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo](http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo)

This is a wince -package; vt8500, vm8505 and anyka in same zip-package.

-mikkoj

---

### Post by mikkoj on 2010-03-05
> **mikkoj said:**
> This is a wince -package; vt8500, vm8505 and anyka in same zip-package.

BUT this is the best one! All trhe applications and wifi working straight way! Poland rules :)

-mikkoj

---

### Post by vinceCOOK on 2010-03-06
Hello Forum,

Yes, it is a collective strengh that could perhaps spur
the Linux distro for vt8500 and variants....further.

After looking at all....it simply occurred to me that
it is WAY out of my depth as a computing hobby person...

in that sense it would be good if these types of people
could help out in some added way...

all i can say is i would pay $ for the proper Linux distro
for the vt8500 when it is X11 based and performs in a similar
fashion to any Linux distro...(perhaps a user choice payment amount.....paypal.... when buying it on it's website)

Hope this message is not unhelpful...somehow

V.

---

### Post by MattDog on 2010-03-06
This link [HERE]("http://www.arm.com/community/partners/display_company/rw/company/wondermedia-technologies-inc/") has a contact us button that is different from wonder medias main site i sent a request to buy some and for the data sheet for wm8505

---

### Post by kulapu on 2010-03-06
> **vicarioux said:**
> Hello. One user of pdaclub.pl -  nick "uht" make linux pack for vt8500 and vt8505. I don know if it work. Maybe this help. [http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo](http://www.przeklej.pl/plik/miniht-7cali-zip-000ahi36p6jo)


thank you! this has been very helpful to me. I finally got may internal speakers working again.

\\:D/

---

### Post by moblo on 2010-03-06
> **MattDog said:**
> This link [HERE]("http://www.arm.com/community/partners/display_company/rw/company/wondermedia-technologies-inc/") has a contact us button that is different from wonder medias main site i sent a request to buy some and for the data sheet for wm8505

Thanks a lot!!! I have submitted my request to them and hopefully we can get hold of a datasheet. MattDog, how much luck did you have in getting a response from them? I requested the wm8505 datasheet; lets hope they respond.

---

### Post by nextvolume on 2010-03-06
EasyPC Linux 0.2 has been released and it comes with X11. It still has many issues though. The standard window manager is WindowMaker, but I have also included twm if one wants to be classic. As a plus, I uploaded the kernel "source code" (but a lot of the drivers which make the netbook work are by VIA and are in object-format only, meaning they are closed source :( ) with which you can build a new kernel and the toolchain to use with the sources.

Here is my page: [http://tails92.sepwich.com/easypc_linux](http://tails92.sepwich.com/easypc_linux)

There is no support for the WM8505 yet, only for the VT8500. I think starting a port from scratch is needed, as almost surely VIA won't be giving any help.

Other programs I included are XPaint, NetSurf (graphical web browser) and xv.
The X server used is Xfbdev with some modifications by me to get it to "be" 800x480 while on a 1024x768 framebuffer. In this way it's like it is 800x480 to the user, but the framebuffer is always 1024x768 to the hardware, but just the first 800 and 480 pixels in the two directions are used for the X server.

Xnest and Xvfb were also included.

---

### Post by celem on 2010-03-06
The Polish load doesn't work for my '7" mini netbook e/w VIA ARM-VT8500. The sound works but as soon as it boots the screen goes dark.

---

### Post by PrFaas on 2010-03-06
Is there anyone 'out there' who could help me with the following:

I'm checking I/O regions of my wm8505 machine. I'm using uboot & a serial console to do that. so far, i've found a set of differences between the vt8500 doc and the actual I/O of the wm8505. I've found a few devices 'missing', and i've found a few I/O regions that appear to contain I/O registers that i do not know what they are.

I'm looking for the following:
- someone who has a vt8500-machine + serial console.
- someone willing to make md.l (memory-dump - long words) of some memory regions that are 'missing' on my wm8505.

I'd like a log of the data found there in the regions that are missing on my wm8505 machine, so i can compare if that looks like the dump of my 'new' regions.

Missing on the wm8505 is:

0xD8000000 (memory controller)
0xD8001000 (dma)
0xD8007800 (usb)
0xD8008000 (pata - less needed: we're not going to connect a disk...)
0xD800B000 (mscard - also not really needed i think...)
0xD800E400 (lcd... very interested....)

i'd be much obliged if anyone can make dumps of those regions, for instance:

md.l 0xD8000000 40

that should give a 256 bytes dump of the region that is the system controller on a vt8500. If you can make a log of that dump, i can check if a dump of any of my 'new' regions matches with that....

FYI: i found as 'extra' (not vt8500..) regions on a wm8505:

0xD8000400 .. 0xD80007FF  (DRAM controller)
0xD8001800 .. 0xD8001FFF  (DMA controller)
0xD8007000 .. 0xD80073FF  (USB 2.0 host controller)
0xD8009800 .. 0xD8009BFF  (USB 2.0 device controller)
0xD8260000 .. 0xD826FFFF  (keypad controller)
0xD8370000 .. 0xD837FFFF  (serial 4)
0xD8380000 .. 0xD838FFFF  (serial 5)

There may be more, but that's what i found so far. NB: LCD controller is still 'Undetected'...

---

### Post by MattDog on 2010-03-06
no luck with wonder media just found link last night and in windows ce goto control panel; and system properties to check what kinda cpu instead of dissambling it lol

---

### Post by celem on 2010-03-07
> **MattDog said:**
> This link [HERE]("http://www.arm.com/community/partners/display_company/rw/company/wondermedia-technologies-inc/") has a contact us button that is different from wonder medias main site i sent a request to buy some and for the data sheet for wm8505

Maybe writing would work:
[B]WonderMedia Technologies, Inc.
1F, 531, Chung-Cheng Road
Hsin-Tien, Taipei 231
TAIWAN[/B]

---

### Post by DonutFUN on 2010-03-08
just a couple questions about the progress made so far.
How do you load into the TWM instead of windows maker?
how could I access stuff off of my usb drives? (like how do I get up a file browser?)
and dose it have dhcp for the networking?

And one last one (this may seem stupid), for both the one with X11 and without, how do you shut it down without just holding down the power button?

---

### Post by moblo on 2010-03-09
Speaking of progress, I would like to ask a favour of those in the know. After a chat with nextvolume, I realised, with the help of everyone, we could make progress. I feel with more hands on deck, we could achieve more. So this is what i ask.
 
Could those of you attempting to write linux for these netbooks, please outline what they need or what we need to find in order to make progress. If you could please post specifics of what you need or what is holding you back. Then, would all people reading this thread just spend a little time researching the problems and finding ways in which we could solve them. Different people think in different ways and a different persons perspective could lead the way. With more people, we then have a bigger pool of knowledge, and with more people looking for solutions, the faster we can solve the problems.
 
Im also hoping that more knowledgeable people in the field of writing/porting linuxwould get involved. i have no idea in that field, hence I feel a bit helpless, but with more people, a team could be more efficient, and as a result we could find more viable distros of linux on our machines sooner than we expected. Imagine linux on wm8505 machines!!!
 
Thanks for your time and I hope you can get involved.

---

### Post by PrFaas on 2010-03-09
@moblo: 

Is the 'thing' mentioned in my post #541 specific enough? :) 

I also appreciate any hints i can get w.r.t. how to construct a lsp (Linux Support Package) and/or bsp (Board Support Package) for VT8500/WM8505 . So far, i got enough information (i think..) to make a 'minimal hardware' kernel: I know how the serial port, the operating system timer and the interrupt controller of the VT8500/WM8505 work. WM/VT seem 'the same' w.r.t. those devices, so a kernel that supports those devices should work on both SoC's. 

I'm -at the moment- doing two things: 

- now attempting to get 'more devices' understood/mapped (#541...). 

- I'm doing 'study work' on how to generate a linux-x.y.z/arch/arm/mach-vt8500 directory, and then compile a kernel that supports only a serial port as hardware I/O.

And: if you *really* want to 'knock yourself out': I've got ~ 2.5 MBytes of disassembled u-boot code of the WM8505 u-boot. In there, -i know- is hidden how to control a lot of the WM8505 devices. That code is the result of disassembling the 512 KBytes of the WM8505 SPI bootrom. At 4 bytes per instruction word, and -my estimate- about half of the 512K being actual code, (the rest is text strings & 0x00000000 words..) we have about 64K instructions to 'reverse-comment'. I have a good idea of what should be there: i also have the C-code of the same. Hacking through that code is an activity that is eminently suited to the 'massive parallelism' that we could perform here.

---

### Post by budgetcomputer on 2010-03-09
Prfaas or anyone else:
 
Would it be worth posting your questions to the tech forum at arm.com? 
 
Here's the url:
 
[http://forums.arm.com/](http://forums.arm.com/)

---

### Post by max1024 on 2010-03-09
IS it possible 2 run ANDROID OS on this smartbook? I tried Haret project but unsuccessful :(

---

### Post by moblo on 2010-03-09
With regards to HaRET, is that not a viable path? Its function appears to be what we are looking for-ie: reverse engineering. I quote from their website:

 Handheld Reverse Engineering Tool   
  HaRET is a very useful tool for both end users and developers. Its  purpose is two-fold:  
      
[LIST]
[*]   It is a Linux bootloader which works from Windows CE environment (a-la  loadlin for DOS or older Linexec tool for Windows CE)  
[*]   It is a tool for accessing the hardware internals of a Windows CE  handheld to help get Linux up and running on it.   
[/LIST]

Would this be an area worth looking at? Like I said before, Im not too familiar with software technical info, so I may be way off.

@PrFaas: I just remembered post #541!!! But what I was aiming at, which you fulfilled, was a definitive summary of what needed to be done. I am also hoping that some of the other guys also post similar summaries, and hopefully we can all look at the project from different angles and help the effort.

---

### Post by disi on 2010-03-10
Just to let you know :)

I have the WM8505 and one thing I find interesting, if you boot into Windows CE and run the program c:\windows\serialsomething.exe (I am at work right now), you get the boot log of the kernel and can save it as txt to your sdcard. There is some hardware information in there, e.g. the network cards are realtek.
I built a crosscompile toolchain on my desktop and used the code from orion for Buffalo NAS drives (they have ARMv5TEJ), build myself a kernel.

Currently I learn u-boot :D

I learned how to build a scriptcmd file and the basics for u-boot script, but how the hell do I get it to use the DHCP in my network to boot from tftp server with the kernel I put there? So if someone could help me out there I could test lots of different kernels...
I have no output whatsoever, but I get the LED on the switch to flash while I boot the netbook, so it is trying to do network stuff...

//edit: All I really need is a booting kernel which supports the chip :/ The rest can be build...

---

### Post by nextvolume on 2010-03-10
I tried Haret more than a month ago, and I couldn't get it work because it runs in system mode, thing which is NOT POSSIBLE for a program running on Windows CE 6, but POSSIBLE for a program running on Windows CE 5.

So if one loads Windows CE 5 on VT8500 netbooks (and there seems to be a version of Windows CE 5.0) using it will be possible, otherwise it will just be useless. Back then I also searched if there was a driver + program which could get results similar to Haret. Unluckily I found none.

---

### Post by moblo on 2010-03-10
I recently contacted WonderMedia, and just received a reply. Respect to them for actually responding, but im afraid no luck. Here is the email for your information.

-------------------------------------------------------------------------------------------------------
Hi, *******,

Thank you very much for your interest to our  technology.

I am sorry that our datasheet is not open to public.  Only authorized customers can access the material.

Sorry for the  inconvenience



Best Regards

--------------------------------------------------
Roger  Lin (&#26519;&#20432;&#35488;)
WonderMedia Technologies, Inc. &#23041;&#20449;&#31185;&#38651;
Tel : 02-2218-2250   ext: 7492
E-Mail : **********************

-----Original  Message-----
From: ARM Connected Community [mailto:connected@arm.com]  
Sent: Sunday, March 07, 2010 1:44 AM
To: RogerL Lin
Subject:  WonderMedia Technologies, Inc. has Received a Connected Community  Inquiry - Please respond

The following visitor has requested  contact from your company at your earliest convenience.  Please do not  use this contact information for any marketing/sales/mass-mailing  purpose without their consent.

Visitor Information:
******* ******, Student
Company: n/a
Email: *******************
Telephone  Number: ***********

Address: 

 
 
United Kingdom 
 

Nature of enquiry: Other


Question: 
Hi,
I am  writing to request the datasheed for your wm8505 SoC. I am part of a  community trying to develop linux for netbooks based on your chip, and  without the datasheet, we are unable to progress at the moment. As I'm  sure you are aware, Windows CE is very limiting and linux would unleash  the potential of your chip. I hope you are able to help me in this  matter.
Many Thanks
*******

-------------------------------------------------------------------------
note: I have sensored some info for obvious reasons.

I will reply to them asking if they can provide any information at all, but I think that is unlikely. But still, at least they were decent enough to reply.

---

### Post by disi on 2010-03-10
Did you ask how much?
I mean if they ship it with every chip :) We could just buy one...

---

### Post by celem on 2010-03-10
Of course this begs the question of what does it take to become an "*authorized customer*"? 

It may be as simple as applying to become an "*authorized customer*", or it may take a fulfilled purchase order of some volume. The question needs to be asked of WonderMedia.

---

### Post by moblo on 2010-03-10
> **disi said:**
> Did you ask how much?
I mean if they ship it with every chip :) We could just buy one...

I did reply to them, and in that asked what it would take to become an authorised customer and if it could be bought.

---

### Post by openanky on 2010-03-11
> **celem said:**
> Of course this begs the question of what does it take to become an "*authorized customer*"? 
 
It may be as simple as applying to become an "*authorized customer*", or it may take a fulfilled purchase order of some volume. The question needs to be asked of WonderMedia.
 
"*authorized customer*"? I think it is a reject.
it will spend **big** money to become an "*authorized customer*", why not just sell it on eBay and  exchange for a anyka mininetbook. all BSP source code of anyka has be open in internet. you can get it from [http://mininetbooks.your-board.com](http://mininetbooks.your-board.com). we have a plan port windows mobile 6 to anyka netbook,about linux, Haret has run on it.same type, same price,more challenging than vt8500

---

### Post by nextvolume on 2010-03-11
Ah no, openanky. I like what you've freed on your forums, but to cannibalize the VT8500/WM8505 effort is a very selfish and stupid thing to do. They're different SoCs and need to be handled separately. But not handling one of them is stupid, just because MAYBE one is already handled better.

I made a forum about the subject we talk about [here](http://tinyurl.com/easypc-forum)

---

### Post by openanky on 2010-03-11
hi,*nextvolume*
 
I am sorry , I just hope more linux master like you can lead us to port linux to it. I have two arm netbooks, one vt8500, one ak7802, I have tried to get BSP of vt8500 from my china's friends about two months ago, but nothing because vt8500 was rarely used due to the lack of hardware decoding. I will continue to look for BSP or datasheet of VT8500 if i can contact more friends.
 
I found two netbooks have same hardware except cpu, e.g. WIFI, LCD, SD, USB, LAN, TOUCHPAD, KEYBOARD.... there maybe have some same source code of driver and application software can be shared with two netbooks. we have builded a specialized subforum for vt8500 or other arm machine, if you have some informations about vt8500 to share with us, welcome :[http://mininetbooks.your-board.com/similar-devices-f2/](http://mininetbooks.your-board.com/similar-devices-f2/)
 
Im sorry that you misunderstood&#65292;sorry anyway

---

### Post by seventythree on 2010-03-11
This thread is awesome, I'm seriously tempted to pick one up just to tinker :P

It seems their chip is also used in another product, basically the same thing without the keyboard, plus a touch screen. I would buy one for 75 bucks ;)

[http://www.alibaba.com/product/hk106849921-107188023-0/Cheapest_7_touch_screen_UMPC_MID_Tablet_PC_handhelds_computer_VIA_VT8500_CPU_128M_SDRAM_WIFI_WINDOWS_CE6_0_UMPC_MID.html](http://www.alibaba.com/product/hk106849921-107188023-0/Cheapest_7_touch_screen_UMPC_MID_Tablet_PC_handhelds_computer_VIA_VT8500_CPU_128M_SDRAM_WIFI_WINDOWS_CE6_0_UMPC_MID.html)

edit: Wow, that chip is used in a tonne of products (really just the same one though), possibly why they don't want to release any information, although I don't see how it would hurt their sales 

[http://www.aliexpress.com/wholesale/wholesale-vt8500.html?SortType=price_asc&SortType=y](http://www.aliexpress.com/wholesale/wholesale-vt8500.html?SortType=price_asc&SortType=y)

---

### Post by ltbordo on 2010-03-12
has anyone tried the damn small linux guys to see if they have ported a linux for the vt-8500 or wm8505? Their distro is 50 meg and runs in 128meg of ram so the size is right. maybe someone over there is on this???

john

---

### Post by ltbordo on 2010-03-12
also, please tell me which devices on the netbook are bootable (the SD card or the USBs or both??). I have the vt-8500 2 gig Nand 128M ram.

john

---

### Post by seventythree on 2010-03-12
Just the SD card I believe

---

### Post by gecsek on 2010-03-12
Can anybody send me all Files from an VT-8500 Netbook? There is no Sound on my Netbook, after it was reinstalled the Windows (with VT8500Software.rar).

Thanks

---

### Post by PrFaas on 2010-03-12
This:

[http://sim-tek.en.alibaba.com/product/275036015-200650586/Newest_mini_laptop_7_inch_laptop_with_WiFi_built_in.html](http://sim-tek.en.alibaba.com/product/275036015-200650586/Newest_mini_laptop_7_inch_laptop_with_WiFi_built_in.html)

seems to also offer linux on a vt8500, but no real contact/www info that i could find :-/

---

### Post by ltbordo on 2010-03-12
I replied to a [COLOR=#7D7D7D]**Ms Misy Gao  (Sim-Tek International Group Co., Ltd.) for linux info for the laptop**
[/COLOR]

---

### Post by ltbordo on 2010-03-12
Sim-Tek International Group Co., Ltd.			 		 						 			Street Address:  			Fuqiang Mansion, 62 district of Bao'an, Shenzhen, China			 		 										 			Country/Region:  			Hong Kong			 		 							 				Zip: 				518000				 			 						 			Telephone: 			86-755-61584928			 		 							 				Mobile Phone:  				15899755797				 			 							 				Fax: 				 				86-755-61584929				 			 						 			Website: 					 			   								     [http://www.sim-tek.net]("http://www.sim-tek.net/") 				    																
							 								     [http://sim-tek.en.alibaba.com]("http://sim-tek.en.alibaba.com/")

---

### Post by ltbordo on 2010-03-12
OK here is the scoop from haleron from eric over there. I just skyped them, they have 3 customer guys (2 guys one girl actually) and  2 engineers. They are pulling their hair out working with VIA and wondermedia (just like us!) and VIA/WM is being difficult. Haleron management has given the team 1 more month to port and compile a linux version for this CPU architecture. If they can't get it done by 15 April......they are changing chips (another ARM chip  "miracle" code name??)  They can be reached via skype easily and via [email]info@haleron.com[/email] with some difficulty (eric told me they changed their servers to germany and are having email issues)

---

### Post by dan_dan on 2010-03-12
I'm running Easy Linux 0.2 in my netbooks and work fine. But I have a problem, there is no ethernet adapter, just wireless but don't works.

MVL-GSPI8686
Probe Wlan Card P51
Chiprev is 0xffff
ERROR:  the correct chiprev should be 0x00b
unregistred netdevice
device eth%d/c/6063000 never was registred.

Could anyone please help me with this problem? 

thanks,
Dan_dan
Just a Java coder ;)

---

### Post by LikeUbun on 2010-03-12
I have a freind who works in wondermedia,  maybe he can help your guys.  but I am not engineer, not sure how to discuss with him... pls advice...

---

### Post by mikkoj on 2010-03-12
> **LikeUbun said:**
> I have a freind who works in wondermedia,  maybe he can help your guys.  but I am not engineer, not sure how to discuss with him... pls advice...

We are looking for the datasheet of VT8500 and the datasheet of VM8505.

-mikko

---

### Post by LikeUbun on 2010-03-12
> **mikkoj said:**
> We are looking for the datasheet of VT8500 and the datasheet of VM8505.
 
-mikko
 
 
He said VT8500 will eof soon, now they focus on WM8505, he also said they will have Android system soon, maybe at April.... I will try to ask for datasheet, he wants to know what kind of application and develop for what... is that for ubuntun?

---

### Post by seventythree on 2010-03-13
The goal is to get any flavor of linux to run on the VT8500 based netbooks, that currently run windows CE.

---

### Post by mikkoj on 2010-03-13
> **LikeUbun said:**
> He said VT8500 will eof soon, now they focus on WM8505, he also said they will have Android system soon, maybe at April.... I will try to ask for datasheet, he wants to know what kind of application and develop for what... is that for ubuntun?

People here are just trying to develope a graphical linux for these devices. It can certainly be Ubuntu. But it is not possible at all (and certainly not a part of any distribution), if the developers don't have the information about the processor.

Android is just fine. Even better, if people here could develope a proper linux kernel. Then it wuold be possible to go on and develope for instance an Ubuntu VM8505-port. *EDIT: AND VT8500-port :)*

Applications? The normal ones first: terminal, browser, office apps, light graphics. It would nice to have media player, flash working. I would like to have a very light audio application like 4track... With linux everything would be possible to try. With this WinCE... well, you know.

-mikko

---

### Post by DonutFUN on 2010-03-13
So if their going to be abandoning the VT8500 does that mean their more likely to give up the data we need now? and working at WM, is it the same company? as well I was just wondering, since their porting android, is that to the VT or to the WM?

---

### Post by seventythree on 2010-03-13
I believe Via is a subsidiary of Wondermedia (or the other way around, one or the other :P)

edit: just checked, Wondermedia is the subsidiary of Via

---

### Post by LikeUbun on 2010-03-13
As I know, They will not promote VT8500, now they only have WM8505. of cause, OS is WINCE6.0 now.
 
Android system base on WM8505, it will be MP at 15/April. at that time, it will replace WINCE. 
 
To DonutFun : yes. Wondermedia is the subsidiary of Via. That's why VT to WM. it is the same company.
 
To Mikko: they do porting android by themselves or with 3rd party now. it will be ready at begining of April. I am wondering you can develop linux without BSP.

---

### Post by seventythree on 2010-03-13
That's awesome.

I was also wondering what the difference was between wm8505 and vt8505? Anybody know?

edit: also, hey look a forum :P
[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php)

---

### Post by LikeUbun on 2010-03-13
> **seventythree said:**
> That's awesome.
 
I was also wondering what the difference was between wm8505 and vt8505? Anybody know?
 
No VT8505, only WM8505.  here is from my friend: "WonderMedia is the subsidiary of VIA, was established in Nov,2008.  from then, all VIA ARM CPU changed name from VTxxxx to WMxxxx. "

---

### Post by seventythree on 2010-03-13
Does that mean that vt8505 and wm8505 are the same chip, just one is manufactured before the merger and one after? (ie vt8505 == wm8505 with a different name)

edit: I'm asking because if the companies develop android for the wm8505 and the chips are the same, it should be a pinch to install it on people's vt8505 machines

---

### Post by LikeUbun on 2010-03-13
> **seventythree said:**
> Does that mean that vt8505 and wm8505 are the same chip, just one is manufactured before the merger and one after? (ie vt8505 == wm8505 with a different name)
 
edit: I'm asking because if the companies develop android for the wm8505 and the chips are the same, it should be a pinch to install it on people's vt8505 machines
(also I sent you an email about the data sheet ;)
 
Yes..WM8505 is same as VT8505, it means no VT8505

---

### Post by joshviklef on 2010-03-13
> **LikeUbun said:**
> 
Edit: WM8505 will have android, but 8500 will not. and their next ARM CPU is WM8425 with DSP, will release soon.
[There]("http://tails92.sepwich.com/files/easypc/datasheets/wondermedia%20soc%20product%20roadmap-20090401.pdf") is a roadmap of Wondermedia´s ARMs.

---

### Post by DonutFUN on 2010-03-13
So seeing as you we can now get the VT's information, that means we can completely make a Linux for it now right? with sound and wireless and everything working?
That's awesome! and by the way, I wanted to mention to the one who has been making the linux up to this point, sadly from what I've found at least the toutchpad onboard mouse wasn't working, but it does on CE so I know it isn't broken. Maybe you should check if your's is to check for compatibility afterwords.
and I also wanted to mention that I have emailed this person (forgot his name) and asked for the VT's data sheet, just so then I can hopefully have a backup just in case.

---

### Post by LikeUbun on 2010-03-14
> **DonutFUN said:**
> So seeing as you we can now get the VT's information, that means we can completely make a Linux for it now right? with sound and wireless and everything working?
That's awesome! and by the way, I wanted to mention to the one who has been making the linux up to this point, sadly from what I've found at least the toutchpad onboard mouse wasn't working, but it does on CE so I know it isn't broken. Maybe you should check if your's is to check for compatibility afterwords.
and I also wanted to mention that I have emailed this person (forgot his name) and asked for the VT's data sheet, just so then I can hopefully have a backup just in case.
 
I am here.  :KS

---

### Post by jgundo on 2010-03-14
I am so looking foward to something working right on these things.... great job all and please keep up the good work.

---

### Post by seventythree on 2010-03-14
Here is some interesting information : [http://www.at91.com/linux4sam/bin/view/Linux4SAM/](http://www.at91.com/linux4sam/bin/view/Linux4SAM/)

It seems there is a large community of people developing linux for the at91 atmel SoC range, which runs off the arm926-ej core. This might be useful, but honestly I have no idea

---

### Post by ltbordo on 2010-03-14
missy got back to me with a product sheet. their s0702 netbook (70$ for 1-10 quantity) has the vt-8500 CPU and is almost identical to ours. I have written to her thus 

" *I see the s0702 has linux offered. What type and version of linux? How  much to just order the linux software to evaluate?*"

Those are our two HOT LEADS for linux on these things, the other is haleron working on one before they abandon it on april 15th.

can anyone tell me about the easy linux 0.2 that IS working on these things now?

ltbordo

---

### Post by ltbordo on 2010-03-14
dan dan 

what type of linux is easy linux 0.2 and how do you install it? Are you running it  on a vt-8500?

---

### Post by LikeUbun on 2010-03-14
> **PrFaas said:**
> This:
 
[http://sim-tek.en.alibaba.com/product/275036015-200650586/Newest_mini_laptop_7_inch_laptop_with_WiFi_built_in.html](http://sim-tek.en.alibaba.com/product/275036015-200650586/Newest_mini_laptop_7_inch_laptop_with_WiFi_built_in.html)
 
seems to also offer linux on a vt8500, but no real contact/www info that i could find :-/
 
It's not right message, VT8500 only support wince6.0.

---

### Post by seventythree on 2010-03-14
> **ltbordo said:**
> dan dan 

what type of linux is easy linux 0.2 and how do you install it? Are you running it  on a vt-8500?

Go to nextvolume's site and download the 0.2 easypc linux package : [http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)

The package acts as a live-SD card, you simply have to partition and format your SD card and unpack a couple of .tgz to the appropriate partitions. More detailed instructions are in the package.

It runs linux type linux :P , totally based off the kernel but there is a list of programs pre-installed:
[QUOTE= "readme"]
Contents of the Distribution
-------------
Kernel: Linux 2.6.10_dev-VT8610 (with VIA binary blobs)

C Library: GNU libc 2.3.6 softfloat

User land: (among others, this list is not complete)
           BusyBox 1.16.0
       thttpd 2.25b 29dec2003 (http web server daemon)
       stupid-ftpd 1.5beta (ftp server daemon)
       MikMod 3.2.2-beta1 (music module player)
       ESounD 0.2.41 (for networked audio)
       ELinks 0.11.7 (web browser)
       e2fsck/mke2fs 1.41.9 (ext2 filesystem tools)
       nano 2.2.2 (text editor)
       bash 4.1 (shell)
       Rhapsody 0.28b (IRC chat client)
       mpg321 0.2.11 (MP3 file player)
       ogg123 (vorbis tools 1.2.0) (Ogg Vorbis file player)
       curl 7.20.0 (file downloader)
       dosfsck/mkdosfs 3.0.9 (FAT filesystem tools)
       mtools 4.0.12 (tools to access FAT filesystems)
       X11R7.5 X.Org Xfbdev server with modifications (graphics server)
       WindowMaker 0.92.0 (window manager)
       xterm-255 (X11 terminal emulator)
       NetSurf 2.1 (graphical web browser)
       unrar 3.92 (RAR archive extractor)
       XPaint 2.8.16 (paint program)
       xv 3.10a-jumboFix+Enh 20081216 (image viewer)
[/QUOTE]

@LikeUbun: Clearly it can support linux, since nextvolume has proven it, but no body has been bothered to put the development time into porting it across.

edit:@ltbordo: You might want to email those guys at haleron and point them in this threads direction, might help them with their dev and that can't be a bad thing.

---

### Post by ltbordo on 2010-03-14
thanks **73**! Hope we can get the video and internal touchpad and keuboard figured one day. Nice that its a "live SD!! Went ahead and sent links to Haleron.

ltbordo

---

### Post by takeshi070 on 2010-03-14
Easy linux 0.2 no running WM8505 :(

---

### Post by seventythree on 2010-03-14
It's not meant to, note the thread title, and this quote

[QUOTE="from nextvolume's site"] *THIS RUNS ONLY ON NETBOOKS WHICH ARE SURELY BASED ON THE VT8500 CHIP.*[/QUOTE][I]
It was already capitalized :P

edit: That was a bit harsh, it's because, while the two machines may look the same, their chips are wildly different and time will need to be spent creating a kernel for the wm8505 chip. If we had a pre-compiled kernel for the wm8505 (like we do for the vt8500) it would be much quicker.
[/I]

---

### Post by ltbordo on 2010-03-15
missy at simtek wrote to say we'll have to buy their vt-8500 netbook to evaluate the linux on it...oh well

---

### Post by seventythree on 2010-03-15
Did she specifically say that it's linux running on a vt8500 core? Cause tonnes of their product pages have conflicting information (saying xburst in one part and vt8500 in another, or intel in one and vt8500 in another)

[http://www.aliexpress.com/store/700803/200650586-278625821/7-inch-laptop.html](http://www.aliexpress.com/store/700803/200650586-278625821/7-inch-laptop.html)
[http://www.alibaba.com/product-gs/225889536/7_inch_Laptop_only_69_laptop.html](http://www.alibaba.com/product-gs/225889536/7_inch_Laptop_only_69_laptop.html)

edit: ah check it out, off their official site : [http://www.sim-tek.net/ProductShow.asp?ID=1486](http://www.sim-tek.net/ProductShow.asp?ID=1486)

[quote="sim-tek.net"]
7 inch Digital LCD screen, VGA 800*480 pixels.
- Windows CE 6.0  or Linux
-CPU: VT 8500, AK or XBurst  32-bit Processor 
 --ROM: 1Gb ( 2,4, 8, 16 Gb Optional) 
-RAM: DR 128-256Mb[/quote]

Looks like they just tailor it to suit

---

### Post by ltbordo on 2010-03-15
with her VERY broken written english , its a bit hard to tell. I wish we could just FTP the .iso and try it out as a live SD.

---

### Post by ltbordo on 2010-03-15
I'd like to try easy linux 0.2. How do I partition and install the images on a SD without a card reader? I have a digital camera that takes SD with a mini USB cable. Will that work?

---

### Post by seventythree on 2010-03-15
Possibly, if you can plug the camera into the computer, with the SD card coming up as it's own drive then probably. Otherwise you could try to find some CE software for partitioning drives. I'm a mac guy so I'm lacking in knowledge for anything non mac

---

### Post by LikeUbun on 2010-03-15
> **seventythree said:**
> Possibly, if you can plug the camera into the computer, with the SD card coming up as it's own drive then probably. Otherwise you could try to find some CE software for partitioning drives. I'm a mac guy so I'm lacking in knowledge for anything non mac
 
Sim-tek is not the right manufactory for this product, more like trader. so that's why I said their message is not right. 
I have a VT8500 minibook, maybe I can try it. but find a real manufactory to do should be better.

---

### Post by seventythree on 2010-03-15
ltbordo is talking about the linux version nextversion created, not the version that sim-tek uses (which we don't have a copy of)

---

### Post by LikeUbun on 2010-03-15
For WinCE base on VT8500, they provide a SD card, and i just need plug in, then reboot, it will auto-update. I'd like to try easy linux, but unfortunately, I do not know how to update Easy Linux, somebody tell me?

---

### Post by LikeUbun on 2010-03-15
> **seventythree said:**
> ltbordo is talking about the linux version nextversion created, not the version that sim-tek uses (which we don't have a copy of)
I know what Itbordo talking. but just remenber him that Sim-tek is not the real manufactory for VIA minibook, he can not get the right information from Misy Gao. trust me, I checked that. :)

---

### Post by seventythree on 2010-03-15
1. Go to nextvolume's site and download the easypc 0.2 package : [http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)
2. Extract the package and follow the walk-through in the "writing.txt" file
3. If you don't know how to partition a drive I suggest you google it (or if your running mac os x use disc utility)

---

### Post by LikeUbun on 2010-03-15
> **seventythree said:**
> 1. Go to nextvolume's site and download the easypc 0.2 package : [http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)
2. Extract the package and follow the walk-through in the "writing.txt" file
3. If you don't know how to partition a drive I suggest you google it (or if your running mac os x use disc utility)
 
OK, it is so difficult to me. I need to discuss with my friend who has experience on linux...:(

---

### Post by seventythree on 2010-03-15
When I get mine (hopefully within a week) and I get a chance to play with it I'll do a write up about installing it.

---

### Post by nextvolume on 2010-03-16
The email validation problem on my forum is (mostly fixed now).

The forum is here
[http://tinyurl.com/easypc-forum](http://tinyurl.com/easypc-forum)

---

### Post by disi on 2010-03-17
> **LikeUbun said:**
> As I know, They will not promote VT8500, now they only have WM8505. of cause, OS is WINCE6.0 now.
 
Android system base on WM8505, it will be MP at 15/April. at that time, it will replace WINCE. 
 
To DonutFun : yes. Wondermedia is the subsidiary of Via. That's why VT to WM. it is the same company.
 
To Mikko: they do porting android by themselves or with 3rd party now. it will be ready at begining of April. I am wondering you can develop linux without BSP.

How official is that?
Android has this weird kernel code that is not part of the official Linux kernel. Will they show the configuration or just offer a binary?

---

### Post by LikeUbun on 2010-03-17
> **disi said:**
> How official is that?
Android has this weird kernel code that is not part of the official Linux kernel. Will they show the configuration or just offer a binary?
they will provide the android system. I think it should be a binary. it is not ready now.

---

### Post by chuck3463 on 2010-03-18
> **chuck3463 said:**
> If you get this upgrade to work, let me know.  I've followed the instructions exactly but my Delstar won't upgrade.   The company ignores my email. Thanks.  Chuck
I was finally able to update the Delstar DS700.  Using a 1G or 2G SD card (PNY and Kingston) per Delstar's instructions didn't work.  I ran repair software on a corrupted 512M Sandisk card and formatted it to FAT32.  The update went very smoothly.  Obviously, either the card brand or size is important for the update to work.

I also posted earlier that my CNM netbook would lose wifi connectivity when browsing certain sites.  I resolved this problem by viewing websites through skweezer.com.  

Finally, my CNM netbook won't connect to a pc using active sync.  I have tried a straight through usb cable and I reversed the two data wires with no success.  I've tried multiple pcs.  Any tip would be greatly appreciated.  Thanks.  Chuck

---

### Post by kulapu on 2010-03-18
I have seen a similar UMPC that has a custom Linux version installed. It's Elonex's Onet. maybe this can help.

here's a youtube video link:
[http://www.youtube.com/v/O4bY_sgIX20](http://www.youtube.com/v/O4bY_sgIX20)

---

### Post by ltbordo on 2010-03-18
*When I get mine (hopefully within a week) and I get a chance to play  with it I'll do a write up about installing it.*


thanks 73, keep us posted, I want to try to  do the same thing

ltbordo

---

### Post by PrFaas on 2010-03-21
No offense to ubuntu intended, but i think i'm going to report my wm8505 reverse-engineering findings (and -when appropriate-..) kernel builds in NextVolume's forum, here:

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php)

from now on. 

My reason is that i feel that this forum thread is getting so long that it is difficult to find back 'things' without resorting to google as a 'find pre-processor'.

A forum -with topic-wise subdivision- is -i feel- a better way to keep track of what is what. 

I'll scan 'here' from time to time, and pm-s will result in a notification e-mail to me, so if you have something specific to report you will be able to 'find' me :)

NB: i'm quite a bit 'underway' in parsing the disassembled u-boot i 'grabbed' from my wm8505 machine(s). I 'found' the video framebuffer & video controller registers (i think..), as well as most of the I/O addresses of the other devices in the wm8505 SoC.
I also 'dug out' the command-table, the video configurations table the invaluable 'printf' routine and lots and lots of error strings, so i hope the going will be a bit faster from here on.

---

### Post by PrFaas on 2010-03-24
Just FYI: As far as i can see, "Haleron" seems to have dropped the Linux option for their 7" VT8500 machine from their www-site.

---

### Post by LikeUbun on 2010-03-24
As I can see, WM8505 has Android system, there is a manufactory announce this, find here: [http://www.bluesky86.com/Android.asp?google os](http://www.bluesky86.com/Android.asp?google os)
 
they can provide sample now and I get one, it is smart book as the VT8500. 
 
After testing, My version still has some issues need to be fixed but it can be used for most of application. they promise this androind system can be MP base WM8505 after 2 weeks. 
 
Sounds great for all.

---

### Post by barthezz on 2010-03-24
U are right...But there is something odd about the description.
The software is natively WinCE supported only. IE or WinRAR... Fake Android or fake IE? :)

---

### Post by LikeUbun on 2010-03-24
> **barthezz said:**
> U are right...But there is something odd about the description.
The software is natively WinCE supported only. IE or WinRAR... Fake Android or fake IE? :)
 
en, I never check website, because I get one sample, it run android, that's point.
 
by the way, it is not so comfortable I used to UI of WinCE.  and some functions need enhance such as "back to Home".  I am waiting for their new version android, they said it is fixed.

---

### Post by PrFaas on 2010-03-25
> **LikeUbun said:**
> As I can see, WM8505 has Android system, there is a manufactory announce this, find here: [http://www.bluesky86.com/Android.asp?google os](http://www.bluesky86.com/Android.asp?google os)
 
they can provide sample now and I get one, it is smart book as the VT8500. 
 
After testing, My version still has some issues need to be fixed but it can be used for most of application. they promise this androind system can be MP base WM8505 after 2 weeks. 
 
Sounds great for all.

My apologies, but i have a little trouble understanding your post:

- I saw the www-site, mentioning android as os
- did you get a sample of that machine? If so, how :) How much does it cost? (i also saw 256 MB RAM, i'd love to have that too :) )
- What do you mean with 'can be MP base wm8505 after 2 weeks'?

In any case: great to see that the WinCE-only barrier looks about to be broken :-)

---

### Post by LikeUbun on 2010-03-25
> **PrFaas said:**
> My apologies, but i have a little trouble understanding your post:
 
- I saw the www-site, mentioning android as os
- did you get a sample of that machine? If so, how :) How much does it cost? (i also saw 256 MB RAM, i'd love to have that too :) )
- What do you mean with 'can be MP base wm8505 after 2 weeks'?
 
In any case: great to see that the WinCE-only barrier looks about to be broken :-)
 
Yes, I get one machine, and playing, it is android system, but only 128 MB RAM, a little slow. 
 
cost? it is sample to me, so I really do not know how much. maybe around USD80.00.
 
you are right, they said the final machine will have 256 MB RAM, Android system will have a final version at begin of April. MP time should be that time, i think, maybe later.
 
-LikeUbun
 
PS: I viewed www-site again to find what I missed. seems they correct some data.
I am intersting to that 10.2" laptop, it shows have 256MB. and love to have one. I will contact with them for details.

---

### Post by prof_prevaricador on 2010-03-25
Hi!
I recently bought an ARM-WM8505 Netbook with WinCE and I'm trying without success to install any flavor of linux in it. I already tried Easy PC and 3MX but I can't get the installation to start! I formatted the SD card as FAT16 and copied the files but it still didn't worked... The WinCE script recover files work, but I can't get any linux installation to work! Can anybody help me? Did anyone get a linux working with the ARM WM8505? Thanks

---

### Post by barthezz on 2010-03-26
MS - suxx. :( If I want to add a localization (russian for me), I NEED to rebuild my OS image and to install it to the device. How do U like it? :)
I'm waiting for any usable linux distribution to burn to my little book more and more. :)
What should I start with?

---

### Post by dadwarf on 2010-03-27
Hi,

I need help with my WM8505 (NAND : 2Gb - RAM : 128Mb - BOARD : P706_MAIN_V5).
I bought this [netbook ]("http://www.1010store.com/products/laptop/Mini%20Netbook%207%20inch%20WiFi%20Windows%20CE%206.0.html")from ebay but it never woks :
I just have "Loading Os Image ..." and nothing else ...
I tried to restore with a SD (FAT32 or FAT16 with "VT8505 Software" or "EASYPC LINUX") and it acts like there is no SD inserted ! always "Loading Os Image ..."

I think this kind of netbook need a special tricks to enable SD recovery !
Have you got an idea ?

Thanks
Thierry

---

### Post by barthezz on 2010-03-27
Emmm. The netbook haven't work "from the box", or after some actions U made?
Do U put the correct files to your SD? They are packed to archives several times...

People, who had already installed **easy linux**, is it possible to install some other packages to SD or internal memory, running the LiveSD Linux? I mean, will this updates be saved to some storage and loaded after next Linux bootup without the installation of it one more time?
Thanks.

---

### Post by dadwarf on 2010-03-27
In fact, i bought it for nothing because of this problem !
But i'm sure of one thing : it didn't read the SD card.
Because even with the wrong software something must happens after "Loading OS Image ..." !
Thanks.

---

### Post by dadwarf on 2010-03-27
That was my fault probably ... i tried to format the SD with a Windows XP (instead of OS X) in FAT (16) and ... it works :redface: ... but stupid i'am ... :( ... i was sure it was dead so i tried to boot it without the small card with the wm8505 on it ... 

And now to start the netbook i had to press "power on" few time until the led is on and then press the "reset" button. 

I must had kill a component ... just like a motherboard witch only boot when you manually short the green pin to the ground ...

---

### Post by lexennov on 2010-03-28
All hello, sorry for my english. I'm really need a file battdrvr.dll from original image WM8505 CE 6 (not smart book firmware). I'm  flashing in my WM8505 VT8505Software.rar firmware - and now not correctly determined the level of battery charge.

---

### Post by psycat on 2010-03-29
Hello, All!!!please, sorry for my english... i have problem: after updating firmware on the netbook wm8505 keyboard not working...(before updating it work well) I have download any firmwares from many sites for wm8505(vt8505)(and ask firmware from seller) but after updating problem not resolved. In log of SerialView: warning: parse keypad param failed.. i dont know how was before updating firmware, but this string is Suspicious. Is anyone have same problem? Maybe you now the way to resolve this problem...

And another quastion: were i can find linux for wm8505, if it there?

p.s. sorry for my english....

---

### Post by bregga on 2010-03-30
A little off topic but the reason I am here is i was wondering if anyone has been able to install any programs on theres. .cab files made for arm will not install on mine and no active sync. thats how i found you even if i have to switch to linux which i am not opposed to just to be able to do something with the unit besides what came with it. I have read 90% of this thread and you guys are making more progress than any where else ive seen. I am just starting on linux so not very knowledgeable so i try to read everything i can any good tutorial sites please pm me.
my unit noname smartbook
using serial view has
vt8500 chip 
300 proc speed
128 ram
2g storage

---

### Post by Jolza on 2010-03-31
Hello all.. I don't mean to be a pain, and I am assuming my question has proberly already been asked. But Is it possible to install windows XP on one of these 7" mini netbook ARM-VT8500... 

If so can someone please tell me how to do it

---

### Post by barthezz on 2010-04-01
No such possibility. Because the ARM architecture of the processor.

---

### Post by LikeUbun on 2010-04-01
Bad news, My smart book base 8505 failed after my damage testing:cry:
 
 Good news, I got the new "machine", In fact, it is only test products. but it also android system. I'd like to share with all.
 
By the way, I also got the picture for final product, and it looks so lovely . I am waiting for a real machine.:p:p

---

### Post by PrFaas on 2010-04-02
Is the picture on the left a 'photo frame' with a strapped-on mainboard? Anyway: cool to see something else than WinCE on this kind of machines :)

---

### Post by LikeUbun on 2010-04-03
> **PrFaas said:**
> Is the picture on the left a 'photo frame' with a strapped-on mainboard? Anyway: cool to see something else than WinCE on this kind of machines :)
 
Yes, it looks like a "digital frame", but with touch and android system. I think it should be their test machine. I am trying to get the newest machine, but they do not provide. they said I will get the real 7" MID as the picture No.2 around 20, April.  20 days....so long to wait.

---

### Post by ericanilaru on 2010-04-03
> **mikkoj said:**
> BUT this is the best one! All trhe applications and wifi working straight way! Poland rules :)

-mikkoj



@mikkoj (or anyone else who's used this)

Does this overwrite the wince installation? - or can you go back to wince by ejecting the SD.  The instructions with the .zip tell you how to set up but not how to get back to previous state.:confused:

I really don't want to do anything irreversible.:-s

At the moment I'm still trying to work out whether to get the 8505 or 8500 version  - and I want to be sure I can get a working (preferably 'live') linux distro to suit  the machine before I buy.:p

Thanx all

---

### Post by Tazergnome on 2010-04-04
Ok, so I'm going to be jumping in on this bandwagon. I have an "EPC" WM8505 ARM. I like the hardware, it's just I'm stuck with Winsuck CE. From what I've read people with the WM8500 can boot Linux from an SD card, but people with my architecture are stuck with what they have for now. From the way I understand it it's because we don't have Linux core that runs correctly on the WM8505. I think it is possible to flash ours once we have something to put onto it. (Please correct me if I'm wrong, I WANT to be wrong here.) 

So until there is a solution we need to find a way of using Win CE. First of all, I can't stand the browser. I can't find a way of installing Opera or Mozilla browser though. I would be grateful if someone would direct me to a good Win CE program site. I was hoping [http://www.oldversion.com/](http://www.oldversion.com/) might but I can't find them if they do.

So the good news, turns out there might be a way for the WM8505 crowd to put Android on their rig. Since we have the newer ARM chip the company is still using them to make the new units that will have Android. Hopefully we will be able to flash over our Win CE boxes over to that.  

Thanks to everyone who has contributed so far, this is such a neat piece of hardware and I hope to see good things happen with it.

Peace,
-TG

---

### Post by ericanilaru on 2010-04-04
@TG 

- you may want to take a look at the package Mikkoj tried from Poland, it includes a build for the 8505 ( I think that's what Mikkoj has) see msg #531 for the link, #533 & #534 for susequent comments.  But, I'm not sure if you can revert to wince if it isn't what you're after yet... (see above)

- There is another link there somewhere for an 8505 build, but again - no info on recoverability.

Hope this helps
E

---

### Post by moblo on 2010-04-04
> **ericanilaru said:**
> @TG 

- you may want to take a look at the package Mikkoj tried from Poland, it includes a build for the 8505 ( I think that's what Mikkoj has) see msg #531 for the link, #533 & #534 for susequent comments.  But, I'm not sure if you can revert to wince if it isn't what you're after yet... (see above)

- There is another link there somewhere for an 8505 build, but again - no info on recoverability.

Hope this helps
E

All of the packages you mention are on fact windows ce packages. there is as of yet no useable linux for wm8505 machines. You can always recover your smartbook woth an sd card and the script folder from the wm8505 package. (or vt8500 if that is the hardware yiu have). 

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php?](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php?)
The above link is to the forum where all info regarding linux on these netbooks will now be. your best net is to keep your eyes on that forum. they are making good progress.

Rumour also has it that wondermedia are making an android port for the wm8505 hardware and so we may see that soon.

---

### Post by sirius0 on 2010-04-08
> **dwinston91 said:**
> There is a keyboard key with "Z z z" on it, which implys, to me atleast, sleep mode. However, it does nothing. Furthermore, closing the lid does not darken the screen or trigger a sleep or hibernate mode. In fact, in the control panel's Poers section, the sleep and hibernate modes are greyed out. Obviously this machine doesn't support sleep or hibernate mode - possibly due to the missing BIOS and its associated APCI. The keyboard key with "Z z z" is probably generic and intended for a different model, namely one with a BIOS.

I found out that the Zzz key is actually the Windows Key.  It has the same functionality of the windows key...Try it out.  Zzz key + E   opens Windows Explorer.

A thought I had on this is that the Africa in particular is being sold with Linux as OEM. This could mean that the manufactures have pre-anticipated the next big legal issue from the other OS vendors as the windows key has a registered trade mark on it. Therefore such a key would be inappropriate on a native Linux machine.

---

### Post by LikeUbun on 2010-04-09
[SIZE=6]Good News[/SIZE]
 
[SIZE=4]WM8505 have Android system....[/SIZE]
 
[SIZE=4]I take some pictures by mobile phone, not clear, but it is real android system. share to all.[/SIZE]
 
[SIZE=4]This product comes from here:[/SIZE]
_[COLOR=#810081][http://goldbluesky.en.alibaba.com/product/296962522-200214605/7_inch_Android_netbook_mini_laptop.html](http://goldbluesky.en.alibaba.com/product/296962522-200214605/7_inch_Android_netbook_mini_laptop.html)[]("http://goldbluesky.en.alibaba.com/product/296856205-200214605/manufacturer_supply_mini_laptop_netbook_smartbook_UMPC_MID.html")[/COLOR]_

---

### Post by moblo on 2010-04-09
> **LikeUbun said:**
> [SIZE=6]Good News[/SIZE]
 
[SIZE=4]WM8505 have Android system....[/SIZE]
 
[SIZE=4]I take some pictures by mobile phone, not clear, but it is real android system. share to all.[/SIZE]
 
[SIZE=4]This product comes from here:[/SIZE]
_[COLOR=#810081][http://goldbluesky.en.alibaba.com/product/296962522-200214605/7_inch_Android_netbook_mini_laptop.html](http://goldbluesky.en.alibaba.com/product/296962522-200214605/7_inch_Android_netbook_mini_laptop.html)[/COLOR]_

Is the os installed by sd card? Is it possible to get the os image to instal on all of our wm8505 machines that still have wince?

---

### Post by LikeUbun on 2010-04-09
> **moblo said:**
> Is the os installed by sd card? Is it possible to get the os image to instal on all of our wm8505 machines that still have wince?
 
 
what I get is new machine, I am not sure it can update from wince to this OS.  will check later.

---

### Post by wicknix on 2010-04-10
Nice. I just picked up an O-Digital TinyBook that runs a samsung arm11 cpu @ 667mhz with 256mb ram running WinCE6. The internal hardware seems to be identical to the SmartQ7's which can run CE6, Android or ARM Ubuntu. I'm currently trying to figure out the bootloader so i can boot the SmartQ's Android and Ubuntu from SD card.

At any rate, for people with these various netbooks that linux currently isn't working on yet, i packed up a hefty sized (105mb) zip full of software for WinCE5 and 6. Just extract and copy to an SD/USB stick and run the apps from there, or copy what you want to your device.

Download here: __[http://filefactory.com/file/b40cdc6/n/winCE6freeware.zip](http://filefactory.com/file/b40cdc6/n/winCE6freeware.zip)

Scroll to bottom of page and choose "download now with file factory basic".
It's all freeware/shareware. Nothing illegal included.

Cheers.

---

### Post by Tazergnome on 2010-04-10
I'm almost willing to get one of the android ones if I can find one.

@Wicknix 

Thanks,

---

### Post by LikeUbun on 2010-04-10
> **LikeUbun said:**
> what I get is new machine, I am not sure it can update from wince to this OS. will check later.
 
Tried 2 machines,  one is same with my new mini-book, upgrade android OK from WinCE6, but another one do not work, I thnk maybe its hardware is differrent with the new one.

---

### Post by LikeUbun on 2010-04-10
I find a interesting 10.1" laptop, it also android base on  wm8505, and seems it will MP at end of this month.  does anybody can tell me what's different android with apple?   what I know is android is more open than apple ipad, but the price has huge range. I think 10.1 laptop should be more suitable for me.
 
find here:
[http://www.ebookpc.net/product_view.asp?id=36](http://www.ebookpc.net/product_view.asp?id=36)
 
and I get a picture for this products. looks good

---

### Post by ch4rlii on 2010-04-11
> **LikeUbun said:**
> Tried 2 machines,  one is same with my new mini-book, upgrade android OK from WinCE6, but another one do not work, I thnk maybe its hardware is differrent with the new one.

Hi!
This are great news :)
Could you provide some information about the updated device? I assume it contains a WM8505 chip, but what about RAM, ROM, WiFi and Screensize?
How did you update? Simple copy and run?
Thank you in advance!

---

### Post by LikeUbun on 2010-04-11
> **ch4rlii said:**
> Hi!
This are great news :)
Could you provide some information about the updated device? I assume it contains a WM8505 chip, but what about RAM, ROM, WiFi and Screensize?
How did you update? Simple copy and run?
Thank you in advance!
 
Basically, 7" mini book base WM8505 using same RAM 128M, 2G Nandflash, wifi also should be same. seems if it has another different hardware used will be not work after upgrade.
 
how update? simply, they provide update file, copy to SD card, turn off the machine, plug in SD card, then turn on machine, it will update by itself, and after update, it will show "remove SD card and machine will reboot again",er something like that, then reboot, you can see Android system. that's all

---

### Post by moblo on 2010-04-11
> **LikeUbun said:**
> Basically, 7" mini book base WM8505 using same RAM 128M, 2G Nandflash, wifi also should be same. seems if it has another different hardware used will be not work after upgrade.
 
how update? simply, they provide update file, copy to SD card, turn off the machine, plug in SD card, then turn on machine, it will update by itself, and after update, it will show "remove SD card and machine will reboot again",er something like that, then reboot, you can see Android system. that's all

have u got the the android software to update the netbooks? is it possible to upload it?

---

### Post by Astounder on 2010-04-11
LikeUbun,
 
Would you provide your Android files that I can download, so I can copy them into the SD card and upgrade my 7in EPC ARM8505 Netbook.
 
I prefer Android instead of its orginal Windows CE 6.0
 
Thanks

---

### Post by LikeUbun on 2010-04-12
> **moblo said:**
> have u got the the android software to update the netbooks? is it possible to upload it?
 
yes, I get the update file. It is DEMO system, it can be normal use but will show "DEMO purposely" on the title bar. 
 
I had uplaod to [www.esnips.com]("http://www.esnips.com/") , you can register there and invite me to be your friend. then you can share this files.
 
Plus, I am not sure it will be OK using my files.
 
**PS: How to invite me to be friend at **[**www.esnips.com**]("http://www.esnips.com/")**?**
(1) give me your register email address, i can invite you.
or
(2) after sign in, find "my menu" at right-top before "sign out", click it looking for "firends", then will open a webpage, find "invite friends", click it will popup a new window, input my email address" [EMAIL="likeubun@gmail.com"]likeubun@gmail.com[/EMAIL]" at the blank box below "your friends' email address", and click "Send". system will send a mail to me.

---

### Post by dadwarf on 2010-04-12
@LikeUbun :

Hi, don't you have a simpliest way to share us your android's files ? esnips is overloaded ... :rolleyes:

i really want to try it :-)

Thanks a lot !
Thierry

---

### Post by moblo on 2010-04-12
> **dadwarf said:**
> @LikeUbun :

Hi, don't you have a simpliest way to share us your android's files ? esnips is overloaded ... :rolleyes:

i really want to try it :-)

Thanks a lot !
Thierry

Would it not be possiblt to upload to something like rapidshare or megaupload?
And I very much appreciate you taking the time to upload the files!

edit:
I have registered on esnips, but cannot find the files.

---

### Post by ZeroEfusion on 2010-04-12
Here is a link to the file. Thanks LikeUbun.

[orca.st.usm.edu/~cberry2/android-ARM-8505-Smartbook.zip]("http://orca.st.usm.edu/%7Ecberry2/android-ARM-8505-Smartbook.zip")

---

### Post by captainclaw on 2010-04-12
Didn't work for me.. just booted to CE

Anyone else have any luck?

---

### Post by wicknix on 2010-04-12
How about a netbook with the 8505 chip running android already?

[http://cgi.ebay.com/7-Inch-Netbook-Android-OS-WiFI_W0QQitemZ250613070369QQcmdZViewItemQQptZLaptops_Nov05?hash=item3a59b3fa21](http://cgi.ebay.com/7-Inch-Netbook-Android-OS-WiFI_W0QQitemZ250613070369QQcmdZViewItemQQptZLaptops_Nov05?hash=item3a59b3fa21)

Cheers.

---

### Post by wicknix on 2010-04-13
Actually i'm talking to a guy on IRC. The file linked above works. You just have to partition your SD card. It worked for him.

Cheers.

---

### Post by freddie24 on 2010-04-13
Hello everyone,

I apologize if I could read all 66 pages of this topic, and I wish you a few questions:

1) I should get a Mini Netbook "Via ARM VT8500 (MODEL 901)" and I would ask if I can install Android. (If so, where can I find the system?)

2) On Windows CE, with pre-installed Skype I can make VoIP calls (with microphone) to my contacts or I can use only as a chat?

I thank you in advance,

Greetings

---

### Post by LikeUbun on 2010-04-13
I am sorry for upload files, esnips is not good place to share.
 
Thanks ZeroEfusion. He release a address can download it directly. 
 
Here is the link for Android base WM8505:
 
[[COLOR=#444444]orca.st.usm.edu/~cberry2/android-ARM-8505-Smartbook.zip[/COLOR]]("http://orca.st.usm.edu/~cberry2/android-ARM-8505-Smartbook.zip")

---

### Post by ch4rlii on 2010-04-13
I successfully installed Android on my WM8505 Netbook :)
All necessary information can be found on page 66 of this thread!
But I'm a bit confused. Android can not be compared with a desktop linux. I dont even find a file browser or how to access my usb-disk. But it comes with many language packs and looks great!
Regards

---

### Post by mmanu on 2010-04-13
ok done! thanks likeubun! and now my fiirst question: where are the 2Gb of internal storage?

---

### Post by freddie24 on 2010-04-13
> **freddie24 said:**
> Hello everyone,

I apologize if I could read all 66 pages of this topic, and I wish you a few questions:

1) I should get a Mini Netbook "Via ARM VT8500 (MODEL 901)" and I would ask if I can install Android. (If so, where can I find the system?)

2) On Windows CE, with pre-installed Skype I can make VoIP calls (with microphone) to my contacts or I can use only as a chat?

I thank you in advance,

Greetings

Can you reply Please :(:(:(:(

---

### Post by ch4rlii on 2010-04-13
Hi,
you can install a file explorer to see your system:
[http://andappstore.com/AndroidApplications/apps/AndExplorer](http://andappstore.com/AndroidApplications/apps/AndExplorer)

Other market alternatives:
[http://mobiload.de/android](http://mobiload.de/android) (german)
[http://www.slideme.org/](http://www.slideme.org/)

But as far as I figured, the market app (vendor.apk) is not installed. Did anyone find a compatible market app?

---

### Post by LikeUbun on 2010-04-13
> **ch4rlii said:**
> I successfully installed Android on my WM8505 Netbook :)
All necessary information can be found on page 66 of this thread!
But I'm a bit confused. Android can not be compared with a desktop linux. I dont even find a file browser or how to access my usb-disk. But it comes with many language packs and looks great!
Regards
 
Find one files management Apk for android, install it, then you can have file browser.
 
remember that, most of Apk for android can be installed on this machine.

---

### Post by LikeUbun on 2010-04-13
> **freddie24 said:**
> Hello everyone,
 
I apologize if I could read all 66 pages of this topic, and I wish you a few questions:
 
1) I should get a Mini Netbook "Via ARM VT8500 (MODEL 901)" and I would ask if I can install Android. (If so, where can I find the system?)
 
2) On Windows CE, with pre-installed Skype I can make VoIP calls (with microphone) to my contacts or I can use only as a chat?
 
I thank you in advance,
 
Greetings
 
1.No, you can use android, it is only for WM8505.
2.No, Skype has not windows CE version. maybe you can use MSN to do voice talk.

---

### Post by ch4rlii on 2010-04-13
> **LikeUbun said:**
> 1.No, you can use android, it is only for WM8505.
2.No, Skype has not windows CE version. maybe you can use MSN to do voice talk.
Not completely right!
Actually, my Netbook did come with a Skype App for WinCE6. But I didn't try it.

---

### Post by freddie24 on 2010-04-13
> **ch4rlii said:**
> Not completely right!
Actually, my Netbook did come with a Skype App for WinCE6. But I didn't try it.

Can you try VoIP Call (voice call with microphone) ???

Many thanks

---

### Post by ch4rlii on 2010-04-13
> **freddie24 said:**
> Can you try VoIP Call (voice call with microphone) ???

Many thanks
I'm afraid not :( I already updated to Android :D

---

### Post by captainclaw on 2010-04-13
Still having a problem here.. I can't get it to run - I have 'script' on the root of the SD card with nothing else on it formatted as flash16.

Heres what HaRET says about my system:

> Minimal virtual address: 00010000, maximal virtual address: 7FFFFFFF
Detected machine Generic ARM 926/generic (Plat='Windows CE 5.0' OEM='Anyka AK780
x')
CPU is ARM ARM arch 5TEJ stepping 5 running in system modeIs it the right one? It looks very similar to the ones here.

---

### Post by freddie24 on 2010-04-13
> **ch4rlii said:**
> I'm afraid not :( I already updated to Android :D

With Android it's possible to install Fring (Multi istant messenger : msn, sky, sip , facebook , google talk, etc etc, [www.fring.com](www.fring.com)  )?

---

### Post by LikeUbun on 2010-04-13
> **captainclaw said:**
> Still having a problem here.. I can't get it to run - I have 'script' on the root of the SD card with nothing else on it formatted as flash16.
 
Heres what HaRET says about my system:
 
Is it the right one? It looks very similar to the ones here.
 
Your machine is Anyka, not VIA/WM. it is not the right one.

---

### Post by LikeUbun on 2010-04-13
> **ch4rlii said:**
> Not completely right!
Actually, my Netbook did come with a Skype App for WinCE6. But I didn't try it.
 
As I know, the skype on WinCE6.0 are hacked from mobile version, it is not for windows CE. 
Skype has not Windows CE version, this is official notice from skype. I am definitely sure.

---

### Post by LikeUbun on 2010-04-13
> **freddie24 said:**
> With Android it's possible to install Fring (Multi istant messenger : msn, sky, sip , facebook , google talk, etc etc, [www.fring.com]("http://www.fring.com") )?
 
Yes, it can install fring.

---

### Post by captainclaw on 2010-04-13
> **LikeUbun said:**
> Your machine is Anyka, not VIA/WM. it is not the right one.

Can Linux be installed on Anyka?

---

### Post by LikeUbun on 2010-04-13
> **captainclaw said:**
> Can Linux be installed on Anyka?
 
I do not know.  but this is not for anyka.  what we talk about is VIA/WM 8500/8505

---

### Post by captainclaw on 2010-04-13
Well that's a disappointment and a half..

Thanks anyway.

---

### Post by mmanu on 2010-04-13
so, here are my questions:

1. how to configure the keyboard? azerty?? scroll keys for internet pages?
2. how works the apps manager? remove an app (force stop has no effect)??
3. you can add items on the desktop, but how to remove one? configure the botttom bar?
4. someone has tried a file manager?
5. where is the usb disk?
6. someone reads the chinese characters (in particular those in settings/local&text)?

---

### Post by Pilotgeek on 2010-04-13
Hey guys, successfully installed android on my netbook =). 
Finally I have something to work with on this thing. Anyways, as for a replacement market app, I have not found one. However, it will install apk files that you can find online. 
 
To remove icons on the desktop (move them, etc) click and hold on the icon. This is the "long press" and it is used for many actions. After holding the icon for a few moments, a trash bin will appear at the side of the screen. You can either drag the icon there to delete, or move it around to the dock. Web page scrolling is acomplished by clicking anywhere on the page and dragging. The android interface is really meant for touch screens.
 
File managers are available, but have not tried any yet. I don't know where the internal 2gb of flash went, but I hope it's doing something because losing 2gb is a disappointment. Seeing as these devices don't have much ram, maybe it's being used as swap space?
 
Anyways, it's working great for me, almost as fast as Windows CE but much nicer. The "Demo Purpose Only" has disappeared on my netbook, and never came back. Either i'm lucky, or it's only temporary? Anyways, thanks LikeUbun for the files and ZeroEfusion for hosting them.

---

### Post by mmanu on 2010-04-13
thanks for the long press trick!

i'm quite sure that the 2G are not used as swap, it seems to me that if swap there is, it would be on the "internal device storage" (50M installed, 200M free), but i don't believe it swaps at all.

as for me, the demo propose only has disappeared after the 2nd boot.

it's clearly nicer than CE but a bit slow on starting (it may be better after some clean up)

any clue for my azety keyboard?? and for apps remove (i try the long press quite everywhere :))?

---

### Post by mmanu on 2010-04-13
andexplorer works. and now i see.[URL="http://andappstore.com/AndroidApplications/apps/AndExplorer"]
[/URL]

---

### Post by mmanu on 2010-04-13
ok. it seems that you can't uninstall the defaults apps the easy way, for dl apps the "uninstall" button replaces the "clear data" ones in the manager.

---

### Post by Pilotgeek on 2010-04-13
Okay, if you can get a hold of a file manager, it's possible to delete apps. You have to dig around in the system folder, then apps folder, which will contain all the apk files. From there, it's possible to delete whatever apps you don't need, but it may mess up the system. And yeah, as for the swap file/partition... doesn't seem like it exists or is even needed. The 2gb must just be wasted then. No real problem, I have a 4gb SD card that works. I wonder if there's a way to extend the Android parition to use ALL of the internal memory? Even if there is a way, it really isn't needed, just hate to see all that flash wasted.

---

### Post by mmanu on 2010-04-13
> **Pilotgeek said:**
> Okay, if you can get a hold of a file manager, it's possible to delete apps. You have to dig around in the system folder, then apps folder, which will contain all the apk files. From there, it's possible to delete whatever apps you don't need, but it may mess up the system. 

really clean, indeed.

---

### Post by Pilotgeek on 2010-04-13
Hey mmanu, is yours reading incorrect battery info? Mine always shows 50% battery... I'm wondering if it would be possible to change the threshold at which it changes. In the scriptcmd file, there are two battery environment variables, battmax and battmin. I'm going to see if I can get it to read correctly using those.

---

### Post by mmanu on 2010-04-13
hummm! it may be related to the 3 shutdowns without warning of my netbook this afternoon (black sceen, impossible to reboot). i'm quit sure that the battery level looked ok (50% i'd say).

---

### Post by Pilotgeek on 2010-04-14
I'd have to say that the battery level indicator is one of the major bugs. Fortunately, I have a pretty good feel of how long I can go on a charge so it's possible to ignore this issue. I couldn't edit the scriptcmd because it refused to load if I changed it in any way. If there are 2 things I would want to try to fix, it's the battery issue and lack of internal storage access.

---

### Post by ch4rlii on 2010-04-14
Hi,
these are my thoughts after one day testing Android:
Booting takes longer than CE, but the system seems to be a bit more performant. The system seems useful, more modern and chic :) The battery issue was also present in CE for me.

I expected more from the Apps, but I'm using these right now:
- SCUMMVM [http://sites.google.com/site/scummvmandroid/](http://sites.google.com/site/scummvmandroid/)
- GhostCommander (File Explorer) [http://handheld.softpedia.com/progDownload/Ghost-Commander-Download-94173.html](http://handheld.softpedia.com/progDownload/Ghost-Commander-Download-94173.html)
- OfficeSuite Viewer (Also views PDF files) [http://handheld.softpedia.com/get/Word-Processing-Text-Tools/MobiSystems-OfficeSuite-Android-81826.shtml](http://handheld.softpedia.com/get/Word-Processing-Text-Tools/MobiSystems-OfficeSuite-Android-81826.shtml)
- OperaMini 5 (I only find 4.2 right now, 5 is there, anywhere!) [http://handheld.softpedia.com/get/Internet-Utilities/Browsers/Opera-Mini-for-Android-92867.shtml](http://handheld.softpedia.com/get/Internet-Utilities/Browsers/Opera-Mini-for-Android-92867.shtml)
- SwiFTP

Most games are useless, since the are using only 320*240 pixels and assume an touchscreen.

I'm still searching for:
- the internal 2GB.
- a vending.apk to access the real market (from a v1.5.2 dump?)
- a *good* pdf viewer.
- a picture viewer (where to store the images anyway?).
- a good video player.

Why are SD cards >2GB supported, but not "udisks"? Or am I doing something wrong? 

Any help appreciated!
Regards,
Charly

---

### Post by freddie24 on 2010-04-14
Hello everyone,

In this post I realized that the ARM 8505 processor you can install Linux Android.

But for the Arm VT8500 there any linux version?

If so what?

---

### Post by LikeUbun on 2010-04-14
> **ch4rlii said:**
> Hi,
these are my thoughts after one day testing Android:
Booting takes longer than CE, but the system seems to be a bit more performant. The system seems useful, more modern and chic :) The battery issue was also present in CE for me.
 
I expected more from the Apps, but I'm using these right now:
- SCUMMVM [http://sites.google.com/site/scummvmandroid/](http://sites.google.com/site/scummvmandroid/)
- GhostCommander (File Explorer) [http://handheld.softpedia.com/progDownload/Ghost-Commander-Download-94173.html](http://handheld.softpedia.com/progDownload/Ghost-Commander-Download-94173.html)
- OfficeSuite Viewer (Also views PDF files) [http://handheld.softpedia.com/get/Word-Processing-Text-Tools/MobiSystems-OfficeSuite-Android-81826.shtml](http://handheld.softpedia.com/get/Word-Processing-Text-Tools/MobiSystems-OfficeSuite-Android-81826.shtml)
- OperaMini 5 (I only find 4.2 right now, 5 is there, anywhere!) [http://handheld.softpedia.com/get/Internet-Utilities/Browsers/Opera-Mini-for-Android-92867.shtml](http://handheld.softpedia.com/get/Internet-Utilities/Browsers/Opera-Mini-for-Android-92867.shtml)
- SwiFTP
 
Most games are useless, since the are using only 320*240 pixels and assume an touchscreen.
 
I'm still searching for:
- the internal 2GB.
- a vending.apk to access the real market (from a v1.5.2 dump?)
- a *good* pdf viewer.
- a picture viewer (where to store the images anyway?).
- a good video player.
 
Why are SD cards >2GB supported, but not "udisks"? Or am I doing something wrong? 
 
Any help appreciated!
Regards,
Charly
 
- the internal 2GB.
"ES file explorer" is good choise
 
- a vending.apk to access the real market (from a v1.5.2 dump?)
Not sure
 
- a *good* pdf viewer.
"Documents to Go"
 
- a picture viewer (where to store the images anyway?).
This system intergrate a APP for digital frame, you should find it. 
 
- a good video player.
This system also have a Video player which enhanced performace for WM8505.

---

### Post by LikeUbun on 2010-04-14
> **freddie24 said:**
> Hello everyone,
 
In this post I realized that the ARM 8505 processor you can install Linux Android.
 
But for the Arm VT8500 there any linux version?
 
If so what?
 
NextVolume provide linux for VT8500. you can try EasyPC linux for VT8500. 
 
here is the link:
[http://s0.blackmage.co.uk/~nextvolume/via_arm/viewforum.php?id=3](http://s0.blackmage.co.uk/~nextvolume/via_arm/viewforum.php?id=3)

---

### Post by ch4rlii on 2010-04-14
> **LikeUbun said:**
> 
- the internal 2GB.
"ES file explorer" is good choise
 
I can't write larger files in the filesystem. I tried /system/usr/. What am I doing wrong?

 > **LikeUbun said:**
> 
- a picture viewer (where to store the images anyway?).
This system intergrate a APP for digital frame, you should find it. 
 
It does not find my images, nor allows me to open a folder!?

> **LikeUbun said:**
> 
- a good video player.
This system also have a Video player which enhanced performace for WM8505.

I'm still hoping another player supports more formats...

Thanks :)

---

### Post by slh_uk on 2010-04-14
Hi,

Has anyone managed to get linux to run on one of the Cnmbook Silvers? They don't appear to have uboot. When they boot up there's something calling itself eboot which will give you the option of formatting and updating various flash/spi disks but it won't boot anything from the sd card. The Cnm procedure for updating uses activesync and a rather convoluted process which won't work with Easylinux.

Cheers

---

### Post by mmanu on 2010-04-14
> **Pilotgeek said:**
> I'd have to say that the battery level indicator is one of the major bugs. Fortunately, I have a pretty good feel of how long I can go on a charge so it's possible to ignore this issue. I couldn't edit the scriptcmd because it refused to load if I changed it in any way. If there are 2 things I would want to try to fix, it's the battery issue and lack of internal storage access.

i can't have a working modified script... i've tried to modify the android_fs.tgz, but even when you decoupress & recompress it (in fact i recompress in .tar.gz and then modify by hand into a .tgz, but i'm pretty sure that the pb isn't there), the netbook upgrades well but never starts after the removing of the sd. is there some kind of checksum security anywhere which prevents for any modification of the script? could it be the /script/etc/custkey file ?

if we could modify the script, would it be possible to code for the mounting of the 2Gb? easily? i've some hope after reading the init.rc file, but i don't really know (yet) how to have something much more concrete than hope...

concerning the battery level, i've found a strange comment in the android_fs/init.goldfish.rc line 9:
# fake some battery state
    setprop status.battery.state Slow
    setprop status.battery.level 5
    setprop status.battery.level_raw  50
    setprop status.battery.level_scale 9

how shall  i undestand this "fake"?

---

### Post by LikeUbun on 2010-04-14
> **ch4rlii said:**
> I can't write larger files in the filesystem. I tried /system/usr/. What am I doing wrong?
 
How large?  why you want to write to /system/usr/.?   
 
> **ch4rlii said:**
> It does not find my images, nor allows me to open a folder!?
 
What kind of format about your images?  this APP will select all pictures from SD card or U-disk by itself.  if you just want to view pictures, I think maybe you have to find one APP for pictures view.

---

### Post by ch4rlii on 2010-04-14
Hi,

> **LikeUbun said:**
> 
How large?  why you want to write to /system/usr/.?   
 
I tried to copy a scumm game with 1..1GB to /system/usr. I thought this would be the best place since there is no /home or /localhome. It failed copying after the second file, which was about 96MB. I think this is what also mmanu means with the missing 2GB storage.

 > **LikeUbun said:**
> 
What kind of format about your images?  this APP will select all pictures from SD card or U-disk by itself.  if you just want to view pictures, I think maybe you have to find one APP for pictures view.
Simple, small resolution JPG files stored in /udist/Fotos. Do I have to create a folder called /images or something?

Thanks!

---

### Post by mmanu on 2010-04-14
> **ch4rlii said:**
> Hi,
I tried to copy a scumm game with 1..1GB to /system/usr. I thought this would be the best place since there is no /home or /localhome. It failed copying after the second file, which was about 96MB. I think this is what also mmanu means with the missing 2GB storage.
Thanks!

i don't think so. when you go to your settings/sd card & device storage/ you see the sd card and the internal device storage (where it puts the /) which has 195M of available space after installation (~ 256 - 51.7). it seems to me that that is why you can't copy a 1.1G file!

another related remark: the system seems to mount properly my usb flashdrive but i can't find it with ESfileExplorer.

---

### Post by LikeUbun on 2010-04-14
> **ch4rlii said:**
>  
 
I tried to copy a scumm game with 1..1GB to /system/usr. I thought this would be the best place since there is no /home or /localhome. It failed copying after the second file, which was about 96MB. I think this is what also mmanu means with the missing 2GB storage.!
 
As mmau said, there is no enough space to copy so large files, you shoudl try SD card.
 
 
> **ch4rlii said:**
> Simple, small resolution JPG files stored in /udist/Fotos. Do I have to create a folder called /images or something?

 
it shoud be recognized, you can change to frame mode, and set path to /udit/Fotos, then your images will show.

---

### Post by abrasive on 2010-04-14
For those of you with the VT8505/WM8505 based netbooks, I've rolled up a Debian system around the Android kernel that was released, with drivers or userland tools for everything.
It adds a few things (like a framebuffer console); it will run from SD alone, or if you wish, install to the device NAND.

X11 is not included to keep the download size down, but it's pretty quick to add with apt-get (figure another 25MB or so of downloadables).

You can find the filesystem tarballs and instructions at: [http://bur.st/~abrasive/wm8505_linux/]("http://bur.st/%7Eabrasive/wm8505_linux/")

---

### Post by mmanu on 2010-04-14
i've resolved my azerty issue by brute force in the /system/usr/keylayout directly on the system (no need to modify the installation script).

the pdfviewer document to go, proposed by LikeUbun, seems not to be free for pdf (only for office)... i'm looking elsewhere (multireader does not work, office suite viewer messes the maths formulae, android pdf viewer is really slow & still has pb with the maths ... grrr)

---

### Post by ch4rlii on 2010-04-14
> **abrasive said:**
> 
I've rolled up a Debian system around the Android kernel that was released

Great! :popcorn:
I will give it a try! Could you put your xorg.conf and sources.list in [http://bur.st/~abrasive/wm8505_linux/]("http://bur.st/%7Eabrasive/wm8505_linux/") to have samples?
Are 256MB OK for X11?
Which wm do you suggest?
 Thank you! 

Charly

---

### Post by abrasive on 2010-04-14
> **ch4rlii said:**
> Great! :popcorn:
I will give it a try! Could you put your xorg.conf and sources.list in [http://bur.st/~abrasive/wm8505_linux/]("http://bur.st/%7Eabrasive/wm8505_linux/") to have samples?
Are 256MB OK for X11?
Which wm do you suggest?
 Thank you! 

Charly

There's a sources.list built into the images (it points at ftp.au.debian.org, which you will almost certainly want to change).

256mb is probably a bit of a squeeze for X11 - you won't have much room for anything else, if it fits...

I've uploaded an xorg.conf, will roll it into the next image.

---

### Post by abrasive on 2010-04-14
> **ch4rlii said:**
> 
Which wm do you suggest?


Also, I use dwm. Very lightweight, rather minimal.

---

### Post by dany74q on 2010-04-14
Hello everyone,
I was just about to open a thread about the same issue,I see it is a popular subject around here.
Well - I have bought two 7" nice,little mini-netbooks,they came with windows ce 5.0,
my wish is to install linux on them,thinking something between custom gentoo system and damn-small-linux.
Could`nt keep up with the posts in this thread,anyone can sum me some important info ?
Basically:
how can I make the boot via SD card / Flash - USB ?
What distro those who was successful used for the right drivers ?

Thanks,
Danny.

---

### Post by LikeUbun on 2010-04-14
> **abrasive said:**
> For those of you with the VT8505/WM8505 based netbooks, I've rolled up a Debian system around the Android kernel that was released, with drivers or userland tools for everything.
It adds a few things (like a framebuffer console); it will run from SD alone, or if you wish, install to the device NAND.
 
X11 is not included to keep the download size down, but it's pretty quick to add with apt-get (figure another 25MB or so of downloadables).
 
You can find the filesystem tarballs and instructions at: [http://bur.st/~abrasive/wm8505_linux/](http://bur.st/~abrasive/wm8505_linux/)
 
Hi
 
I need your debian system, could you make a script file to install?  what I mean is copy to SD card, and update like Android system? 
 
Thanks in advance.

---

### Post by abrasive on 2010-04-14
> **LikeUbun said:**
> Hi
 
I need your debian system, could you make a script file to install?  what I mean is copy to SD card, and update like Android system? 
 
Thanks in advance.

There is a boot-script that installs the kernel, then boots from the SD; you then have to copy the userland manually. From the readme in the folder:
```

mount /dev/mtdblock9 /mnt/mtd
cp -xdpr / /mnt/mtd/

```

Do you need a script to automate that?

---

### Post by abrasive on 2010-04-14
> **LikeUbun said:**
> Hi
 
I need your debian system, could you make a script file to install?  what I mean is copy to SD card, and update like Android system? 
 
Thanks in advance.

Did a crufty quick hack to deliver Android-style single-shot install, seems to work fine, uploading it now.

---

### Post by LikeUbun on 2010-04-14
> **abrasive said:**
> Did a crufty quick hack to deliver Android-style single-shot install, seems to work fine, uploading it now.
 
Yes, I want an auto update script file and I want to install to nandflash, not run on SD card. because I have a AP system need run on debian. please help me to build a full package for your debian system. 
I can customize the hardware to use over 256MB memory, over 2G nandflash. 
so, it is very important to me. 
 
further discussion details please email to me: [EMAIL="likeubun@gmail.com"]likeubun@gmail.com[/EMAIL]
 
Thank you very much.

---

### Post by abrasive on 2010-04-14
> **LikeUbun said:**
> Yes, I want an auto update script file and I want to install to nandflash, not run on SD card. because I have a AP system need run on debian. please help me to build a full package for your debian system. 

This Debian roll is specifically for the EasyPC style 7" netbooks - it sets a bunch of bootloader environment (that the Android installer sets too). You'll have to get down and dirty with the bootscripts if not.



New tarballs uploaded. Supports full-auto install.

---

### Post by LikeUbun on 2010-04-14
> **abrasive said:**
> This Debian roll is specifically for the EasyPC style 7" netbooks - it sets a bunch of bootloader environment (that the Android installer sets too). You'll have to get down and dirty with the bootscripts if not..
 
 
I know, I just want to use your system on WM8505. That's all.
 
> **abrasive said:**
> New tarballs uploaded. Supports full-auto install.
 
is that file  named xorg.conf under useful? replace before one?

---

### Post by norseman-has-a-laptop on 2010-04-14
what are the upgrades on it 
like ram and video cards?
hard drive space

---

### Post by abrasive on 2010-04-14
> **LikeUbun said:**
> I know, I just want to use your system on WM8505. That's all.
 

 
is that file  named xorg.conf under useful? replace before one?

no, old now; now it is already in the extpart tarball - you shouldn't need to do anything (other than apt-get the xorg packages).

---

### Post by LikeUbun on 2010-04-14
> **abrasive said:**
> no, old now; now it is already in the extpart tarball - you shouldn't need to do anything (other than apt-get the xorg packages).
 
OK, got it. thanks in advance.

---

### Post by abrasive on 2010-04-14
> **LikeUbun said:**
> 
is that file  named xorg.conf under useful? replace before one?

I was wrong, and debconf just nukes the xorg.conf that comes in the tarball.
So, you still need to put on that xorg.conf after X is installed. Sorry!

---

### Post by ch4rlii on 2010-04-14
Hi,
sorry, I'm still with Android: Do we have an IMEI?
The settings informs about kernel version, mac-adress and such, but I cant find an IMEI. It is needed to register some Apps...

---

### Post by abrasive on 2010-04-14
> **ch4rlii said:**
> Hi,
sorry, I'm still with Android: Do we have an IMEI?
The settings informs about kernel version, mac-adress and such, but I cant find an IMEI. It is needed to register some Apps...

Nope. Not a phone, no IMEI.

---

### Post by Tazergnome on 2010-04-14
So what exactly is this android system that's being passed around for the WM8505? Is it Debian running on the Android kernel?

If someone could detail how to set this up for a newbie I would be grateful. I've never messed with compiling and I'm not sure how to approach installing on something without a bios.

Thanks,
-TG

---

### Post by mmanu on 2010-04-15
for android:
dl the .zip of posts 651 or 656.
unzip
put on a sd card
boot on it.
it's done.

for debian (on the android kernel):
...
wait the feedbacks. :)

---

### Post by abrasive on 2010-04-15
> **Tazergnome said:**
> So what exactly is this android system that's being passed around for the WM8505? Is it Debian running on the Android kernel?

If someone could detail how to set this up for a newbie I would be grateful. I've never messed with compiling and I'm not sure how to approach installing on something without a bios.


The Android system you see around is just that: an Android system.
The Debian system uses the Android kernel and wi-fi driver, but everything else is Debian.

I've further simplified the install-to-device procedure. This is about as simple as it gets!
Instructions:
[http://bur.st/~abrasive/wm8505_linux/INSTALL]("http://bur.st/%7Eabrasive/wm8505_linux/INSTALL")

---

### Post by ch4rlii on 2010-04-15
Hi,
@debian users: Could you post the answer of "free -m" with X11 running?
In Android, the advanced task manager says 44MB free...
I still doubt 128MB are enough for debian.
Thanks!

---

### Post by abrasive on 2010-04-15
> **ch4rlii said:**
> Hi,
@debian users: Could you post the answer of "free -m" with X11 running?
In Android, the advanced task manager says 44MB free...
I still doubt 128MB are enough for debian.
Thanks!

40mb used, 64mb free; that's with X11 and dwm, nothing else.

---

### Post by ch4rlii on 2010-04-15
Thanks! This is pleasant :)

---

### Post by mikkoj on 2010-04-15
No success [IMG]http://s0.blackmage.co.uk/~nextvolume/via_arm/smilies/frown.gif[/IMG] 

Everytime I get this:
**************************

Preparing to install Linux root filesystem...
Attempting to mount SD card:
Can't find SD card, giving up.
sleep 5
exit 0
fi

if [ ! -x /mnt/sd/extpart.tgz ]
then 
echo Cant find ext.part.tgz on SD card!

Please Enter to activate this console

---

### Post by abrasive on 2010-04-15
> **mikkoj said:**
> No success [IMG]http://s0.blackmage.co.uk/~nextvolume/via_arm/smilies/frown.gif[/IMG] 

Everytime I get this:
**************************

Preparing to install Linux root filesystem...
Attempting to mount SD card:
Can't find SD card, giving up.
  Can you enter the console (just hit Enter) and grab the output of the following: ```
 ls /dev/mmcblk0* 
ls /mnt/mmcblk0* 
```  If you find your partition (eg. as mmcblk0p1) you should be able to ```
 mount /dev/mmcblk0p1 /mnt/sd 
mount /dev/mtdblock9 /mnt/mtd 
tar xzf /mnt/sd/extpart.tgz -C /mnt/mtd 
``` which will complete your install.

---

### Post by abrasive on 2010-04-15
> **mikkoj said:**
>  Attempting to mount SD card:
Can't find SD card, giving up.
  Also, make sure the FAT part is partition 1 on the SD card, and that extpart.tgz is copied (not extracted) into its root.

---

### Post by abrasive on 2010-04-15
> **abrasive said:**
>  You can find the filesystem tarballs and instructions at: [http://bur.st/~abrasive/wm8505_linux/]("http://bur.st/%7Eabrasive/wm8505_linux/")  And you can find me in #easypc on Freenode IRC, if you need help... rather than filling up this thread.

---

### Post by chuck3463 on 2010-04-15
> **freddie24 said:**
> Can you try VoIP Call (voice call with microphone) ???
 
Many thanks
 
 
Yes you can.  It works on my Delstar DS700s.  Chuck

---

### Post by mmanu on 2010-04-15
> **abrasive said:**
> And you can find me in #easypc on Freenode IRC, if you need help... rather than filling up this thread.

except that i'm in the same trouble. i was pretty sure that it was a problem with my sd (no pb with android but my ubuntu pc doesn't want to mount it anymore). so... it's not filling that thread for nothing, it's filling it for the community, that is, in our case: me. thanks to let me know the issue...

---

### Post by mmanu on 2010-04-15
> **abrasive said:**
> Can you enter the console (just hit Enter) and grab the output of the following: ```
 ls /dev/mmcblk0* 
ls /mnt/mmcblk0* 
```  If you find your partition (eg. as mmcblk0p1) you should be able to ```
 mount /dev/mmcblk0p1 /mnt/sd 
mount /dev/mtdblock9 /mnt/mtd 
tar xzf /mnt/sd/extpart.tgz -C /mnt/mtd 
``` which will complete your install.

ok for the mount test.
ok for the tar (except some badblocks but it gave me the prompt back)
i shut it down & ... it asks for login & password ... hummmmmm?...

---

### Post by norseman-has-a-laptop on 2010-04-15
cool coool

---

### Post by abrasive on 2010-04-15
> **mmanu said:**
> ok for the mount test.
ok for the tar (except some badblocks but it gave me the prompt back)
i shut it down & ... it asks for login & password ... hummmmmm?...

So you boot without SD, and get to a login prompt? 
The default root account has no password.

---

### Post by abrasive on 2010-04-15
> **mmanu said:**
> ok for the mount test.
ok for the tar (except some badblocks but it gave me the prompt back)
i shut it down & ... it asks for login & password ... hummmmmm?...

Can you also please tell me where you found the SD card partition in the end? Thanks!

---

### Post by mmanu on 2010-04-15
> **abrasive said:**
> So you boot without SD, and get to a login prompt? 
The default root account has no password.

yep!
indeed!

---

### Post by mmanu on 2010-04-15
> **abrasive said:**
> Can you also please tell me where you found the SD card partition in the end? Thanks!

dev/mmcblk0p1 --> /mnt/sd is that what you want to know? that's your code so i must have misunderstood something

that's my first debian and i'm feeling ... hummmm ... naked

---

### Post by abrasive on 2010-04-15
> **mmanu said:**
> dev/mmcblk0p1 --> /mnt/sd is that what you want to know? that's your code so i must have misunderstood something

that's my first debian and i'm feeling ... hummmm ... naked

Odd, the script looks for a filesystem at mmcblk0p1... 

 As for the nudity - it's pretty much a raw debootstrap bare-bones install, with some drivers hiding underneath... get installing some stuff! (meet your new friend apt-get, and your new enemy df)

---

### Post by mmanu on 2010-04-15
i'm trying you're wi-on and it failed to read the wpa_supplicant.conf (it doesn't exist)
wpa_supplicant -B -Dwext -ira0 -c /etc/wpa_supplicant.conf -P /var/run/wpa_supplicant.pid
i've replaced wpa_supplicant.conf by wpa_supplicant/ (not bad: no errors :))

but dhcpdiscover fails systematically ...

---

### Post by abrasive on 2010-04-15
> **mmanu said:**
> i'm trying you're wi-on and it failed to read the wpa_supplicant.conf (it doesn't exist)
wpa_supplicant -B -Dwext -ira0 -c /etc/wpa_supplicant.conf -P /var/run/wpa_supplicant.pid
i've replaced wpa_supplicant.conf by wpa_supplicant/ (not bad: no errors :))

but dhcpdiscover fails systematically ...

 You need to create a wpa_supplicant.conf so it knows which networks to connect to! see 'man wpa_supplicant.conf' for the full version, but you can get by with something like: ```
 network={
    ssid="My Wifi Network"
    psk="super-secret-passphrase"
} 
```  Also, older versions of 'wi-on' are missing a 'sleep 2' between the modprobe and the wpa_supplicant call - the driver takes a while to come up, and gets confused if you try and talk to it too early.

---

### Post by mmanu on 2010-04-15
> **abrasive said:**
> Odd, the script looks for a filesystem at mmcblk0p1... 

 As for the nudity - it's pretty much a raw debootstrap bare-bones install, with some drivers hiding underneath... get installing some stuff! (meet your new friend apt-get, and your new enemy df)

apt-get is an old friend of mine & i haven't got any trouble with df... yet! dhclient is one of my best known enemy and once again he's here for me!!

what's your new extpart.tgz & cursor_fix?

---

### Post by abrasive on 2010-04-15
> **mmanu said:**
> apt-get is an old friend of mine & i haven't got any trouble with df... yet! dhclient is one of my best known enemy and once again he's here for me!!

what's your new extpart.tgz & cursor_fix?

 To paraphrase the FIX notice:  You may have noticed the cursor is invisible by default in the virtual consoles - the WonderMedia framebuffer driver is incomplete. I've hacked the framebuffer-console driver to hook a software cursor into it. This fixes the problem, superseding my previous workarounds (in startup and terminfo). The new extpart merges the fix; to apply it without reinstalling, grab the fix file and `tar xzf cursor_fix.tgz -C /`

---

### Post by dadwarf on 2010-04-15
@abrasive

hi,
thanks a lot for your job, i'm really happy to finally send wince to trash...
could you make a "changelog" for your extpart & fatpart ?
thanks

---

### Post by abrasive on 2010-04-15
> **dadwarf said:**
> @abrasive

hi,
thanks a lot for your job, i'm really happy to finally send wince to trash...
could you make a &quot;changelog&quot; for your extpart & fatpart ?
thanks

I should have started versioning when I first uploaded a changed tarball...
the current version is stable enough I'm going to call it 1.0; expect changelogs from here on.

---

### Post by mmanu on 2010-04-16
ok. wifi works & i'm looking for a windows manager as pretty & as light as the android one.any suggestion?

and maybe if someone has an easy way to configure my azerty keyboard, it'll be nice

---

### Post by abrasive on 2010-04-16
Posted instructions on changing the boot logo, for those who don't like penguins.

[http://bur.st/~abrasive/wm8505_linux/useful/boot-logo/]("http://bur.st/%7Eabrasive/wm8505_linux/useful/boot-logo/")

---

### Post by moblo on 2010-04-16
Hi guys,
Firstly, thanks to abrasive for the debian!
I have a bit of a request; as far as linux goes, i can use it and can do pretty much anything i want on. What I dont know how to do is the whole apt-get, etc and setting things like that up (command line scares me!). My request is this: Would it be possible to have a version that i can install with x11, browser, file manager and things like that. I know i really should be reading up on these things and doing it myself, so that I might actually learn something, but with my uni exams round the corner, i have no spare time and i actually use my netbook at uni. I would be forever greatful if someone could create this. 
At the moment i am using android, and it is a relief from wince. However, it is too much of a touch screen mobile os, and isnt the most comfortable thing to use on our netbooks. 
Many thanks
Moblo

---

### Post by psycat on 2010-04-16
Answer, please: if i update my netbook to android os, postet on this forum, can i then return win ce(android's firmware rewrite u-boot)? thanks

---

### Post by mmanu on 2010-04-16
> **psycat said:**
> Answer, please: if i update my netbook to android os, postet on this forum, can i then return win ce(android's firmware rewrite u-boot)? thanks

you'll never come back.

---

### Post by ch4rlii on 2010-04-16
> **mmanu said:**
> you'll never come back.
Are you sure?
What about the software on page 7:
[http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61](http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61)
I didn't try it, but it should work.
Just read SOME of the pages here and you find some answers....

---

### Post by mmanu on 2010-04-16
> **psycat said:**
> Answer, please: if i update my netbook to android os, postet on this forum, can i then return win ce(android's firmware rewrite u-boot)? thanks
abrasive proposed a debian alternative to android which can boot to a text console, and won't touch any existing install.
i don't know how easy it is to install, i've chosen to install on the device.

---

### Post by mmanu on 2010-04-16
> **ch4rlii said:**
> Are you sure?
What about the software on page 7:
[http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61](http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61)
I didn't try it, but it should work.
Just read SOME of the pages here and you find some answers....

ok. you surely could, but why would you do that? :D

---

### Post by ch4rlii on 2010-04-16
In fact, I think some WinCE Apps are better than what I found for Android so far. The PDF reader for examples automatically opens a document at the page I closed it and provides shortcuts for faster/slower scrolling. I'm still searching for a good Android pdf reader. ScummVM also runs better under WinCE ;)
True, Android is pretty! And the widgets are cool. Also I prefer the browser. But in the moment I'm looking forward to Debian!

---

### Post by mmanu on 2010-04-16
> **ch4rlii said:**
> In fact, I think some WinCE Apps are better than what I found for Android so far. The PDF reader for examples automatically opens a document at the page I closed it and provides shortcuts for faster/slower scrolling. I'm still searching for a good Android pdf reader. ScummVM also runs better under WinCE ;)
True, Android is pretty! And the widgets are cool. Also I prefer the browser. But in the moment I'm looking forward to Debian!

have you tried RepliGo reader for the pdf? the best i've found... i was looking for something which can read math equations without messing them, android-pdf-viewer was the best but it is really really slow. repligo wasn't so good but it was faster & has some interesting functionalities (fit to the text width...)

personally i really didn't like the CE reader...

---

### Post by ch4rlii on 2010-04-16
No, I didn't. Thanks! I will try them.
The CE reader I mentioned was not the original one, but I don't remember the name in the moment.

---

### Post by mmanu on 2010-04-16
ok! lxde looks good. and my azerty is quite what it has to be... 400M used... comes the question of the web browser... any suggestion?

---

### Post by mmanu on 2010-04-16
> **ch4rlii said:**
> Are you sure?
What about the software on page 7:
[http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61](http://ohioloco.ubuntuforums.org/showpost.php?p=8592200&postcount=61)
I didn't try it, but it should work.
Just read SOME of the pages here and you find some answers....

these are just the softs...

---

### Post by mcmasterp on 2010-04-16
this sounds awesome. Thank you to everyone who is working on this.

I just found these devices on ebay and was debating buying 1-2, but if I may ask some questions.


I've lost track, you guys have been able to get debian with a GUI? lxde I heard one guy say. Can we see some screenshots? please. How is software compatibility? I know it is early but how is the speed compared to the regular winCE?

Again screenshots would be awesome. Thank you in advance if you do

---

### Post by mmanu on 2010-04-16
> **mcmasterp said:**
> this sounds awesome. Thank you to everyone who is working on this.

I just found these devices on ebay and was debating buying 1-2, but if I may ask some questions.


I've lost track, you guys have been able to get debian with a GUI? lxde I heard one guy say. Can we see some screenshots? please. How is software compatibility? I know it is early but how is the speed compared to the regular winCE?

Again screenshots would be awesome. Thank you in advance if you do

lxde looked great, indeed, but it has some problem during installation with hal & pcmanfm (not properly installed the 2 times i tried, in the spirit of[ http://ubuntuforums.org/archive/index.php/t-718910.html]("http://ubuntuforums.org/archive/index.php/t-718910.html")) which led to a big mess up when i tried epiphany...

already with X11/lxde the system was a bit slow, 128M for the RAM that's not so much... i'm going to see what can be done with the damn small linux which is developped for that kind of config.

---

### Post by mmanu on 2010-04-17
@abrasive (or someone else) could you tell me if you think something can be done with de dsl stuff here[ ftp://ftp.is.co.za/linux/distributions/damnsmall/current/]("ftp://ftp.is.co.za/linux/distributions/damnsmall/current/") ?

it seems to run on arm as explain in their 1-readme_first.txt. also, the /kernel/linux-2.4.31.tar.gz contains an /arch/arm

i hoped that it would be as simple as putting linux-2.4.31.tar.gz instead of yours extpart.tgz but of course it wasn't, it never goes further than the boot logo (maybe i haven't wait enough)... maybe the /extra_modules are usefull... 

they seem to have fine tuned apps adapted to a 128M RAM system ([http://www.damnsmalllinux.org/applications.html](http://www.damnsmalllinux.org/applications.html)) as their firefox for exemple...

i really want to try that!!

---

### Post by Knightwalker on 2010-04-17
Hi~~ I installed Debian linux according to the 'abrasive's instruction'. Installation process seem to be fine. No error or hang up. At the end of whole installation, asked me to remove the SD card. Well.. I did... Then after the reboot, 'Debian GNU/Linux 5.0 william tty' and 'william login:' showed up. Am I did something wrong? Is there any password to activate Debian linux? or Did I missed somthing?

---

### Post by abrasive on 2010-04-17
> **Knightwalker said:**
> Hi~~ I installed Debian linux according to the 'abrasive's instruction'. Installation process seem to be fine. No error or hang up. At the end of whole installation, asked me to remove the SD card. Well.. I did... Then after the reboot, 'Debian GNU/Linux 5.0 william tty' and 'william login:' showed up. Am I did something wrong? Is there any password to activate Debian linux? or Did I missed somthing?

Default Debian install: root user has blank password.

---

### Post by abrasive on 2010-04-17
> **mmanu said:**
> @abrasive (or someone else) could you tell me if you think something can be done with de dsl stuff here[ ftp://ftp.is.co.za/linux/distributions/damnsmall/current/]("ftp://ftp.is.co.za/linux/distributions/damnsmall/current/") ?

it seems to run on arm as explain in their 1-readme_first.txt. also, the /kernel/linux-2.4.31.tar.gz contains an /arch/arm

i hoped that it would be as simple as putting linux-2.4.31.tar.gz instead of yours extpart.tgz but of course it wasn't, it never goes further than the boot logo (maybe i haven't wait enough)... maybe the /extra_modules are usefull... 

they seem to have fine tuned apps adapted to a 128M RAM system ([http://www.damnsmalllinux.org/applications.html](http://www.damnsmalllinux.org/applications.html)) as their firefox for exemple...

i really want to try that!!

The extpart.tgz contains the root filesystem, not the kernel (the kernel is flashed directly to the device).
You need a userland that supports the ARM EABI; that's why I chose Debian/armel.

---

### Post by mmanu on 2010-04-17
> **Knightwalker said:**
> Hi~~ I installed Debian linux according to the 'abrasive's instruction'. Installation process seem to be fine. No error or hang up. At the end of whole installation, asked me to remove the SD card. Well.. I did... Then after the reboot, 'Debian GNU/Linux 5.0 william tty' and 'william login:' showed up. Am I did something wrong? Is there any password to activate Debian linux? or Did I missed somthing?

i always have the mount pb on install (even with 1.0), it seems that you don't and it's really unfair. anyway, the final point is the same: a running debian. you're at the right place : the root login is password free!

---

### Post by mmanu on 2010-04-17
> **abrasive said:**
> The extpart.tgz contains the root filesystem, not the kernel (the kernel is flashed directly to the device).
You need a userland that supports the ARM EABI; that's why I chose Debian/armel.

so, you're saying that nothing can be done with dsl?

---

### Post by Knightwalker on 2010-04-17
> **abrasive said:**
> Default Debian install: root user has blank password.

After typed in 'root' I got root menu and text prompt showed up. Is it normal? This is my first time to use debian linux and it makes me pretty confusing. 

I'm feel like really dumb *** for linux.

---

### Post by mmanu on 2010-04-17
> **Knightwalker said:**
> After typed in 'root' I got root menu and text prompt showed up. Is it normal? This is my first time to use debian linux and it makes me pretty confusing. 

I'm feel like really dumb *** for linux.

you're okay. i've had the same feeling yesterday. i feel a bit more comfortable now. you can find utilities to enable wifi, apt-get a X server on abrasive's page. after that ... try a windows manager...

---

### Post by Knightwalker on 2010-04-17
> **mmanu said:**
> you're okay. i've had the same feeling yesterday. i feel a bit more comfortable now. you can find utilities to enable wifi, apt-get a X server on abrasive's page. after that ... try a windows manager...


Thanks.. Now I have to working on bunch of words and texts~~ Is it possible way to activation ethernet modem instead of wireless?

---

### Post by mmanu on 2010-04-17
> **Knightwalker said:**
> Thanks.. Now I have to working on bunch of words and texts~~ Is it possible way to activation ethernet modem instead of wireless?

surely... but i don't know how... but abrasive surely knows :)

if you feel really bad with the debian shell stuff, just wait a bit, i'm pretty sure that some complete graphical installation procedure will pop up here soon...

---

### Post by dadwarf on 2010-04-17
To enable ethernet (it is not a modem) connection with dhcp :
```
ifconfig eth0 up
dhclient eth0
```

---

### Post by Knightwalker on 2010-04-17
> **dadwarf said:**
> To enable ethernet (it is not a modem) connection with dhcp :
```
ifconfig eth0 up
dhclient eth0
```
Thanks.. I'm trying to download gnome kernel for debian. Hopely it works.

---

### Post by hypercube81 on 2010-04-17
hi everybody. sorry for my english. my amr-vt8500 don't work. wince don't start. he's still on "loading Device drivers". i've tried to follow the tutorial to restore os image with a sd card but don't read. any suggestion? tanks for the attention.

---

### Post by ELCANYON on 2010-04-17
I have found information on the topic here:


[http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)

---

### Post by hypercube81 on 2010-04-17
> **ELCANYON said:**
> I have found information on the topic here:


[http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)
 about?

---

### Post by kaputnik on 2010-04-18
Hello there,
just chiming in with a successful install of debian on a wm vt 8505 as per instruction provided by abrasive. Also using the wifi on scripts is good but my access point keeps dropping out, solved by turning off then on again the wifi but will look into this later. Have now installed lxde and it runs quite nicely if a bit slow, as expected. Will be trying to get a decent browser and wpa enterprise working (ttls-pap) so i can use my uni lan so i will let you know how its going. If theres any testing you need (abrasive?) then let me know and i will try to help.
thanks for the work so far, got my crappy CE6.0 smartbook into something usable.
kaputnik

---

### Post by mmanu on 2010-04-18
first of all, one collective question: is there really a swap? free -m seems to say no (what's the buffers/cache?). has someone seen something in there? (exept that during the boot one has: activating swap & swapfile...done)

@kaputnik
have you got the config pb with lxde-core - pcmanfm - hal ?
i have the same recurrent pb with the access point, that i "solve" like you...
i guess i've found the good browser, after epiphany, dillo, hv3, iceweasel & kazehakase, the good answer seems to be... midori!
i 've also tried some text-mode browser, really helpful when you want to dl much faster. elinks is not so bad, old school like :)

so, i'm going back finishing my third lxde install (the good one), i can't really deal with minimal wm (fluxbox, dwm, icewm... brrrrr to much config for so few beauty)

---

### Post by abrasive on 2010-04-18
> **mmanu said:**
> first of all, one collective question: is there really a swap? free -m seems to say no (what's the buffers/cache?). has someone seen something in there? (exept that during the boot one has: activating swap & swapfile...done)

Flash memory isn't great swap - writes stress its physical structure, and it wears out.
Since the internal flash isn't replaceable, swapping is not configured by default.

There is a partition in the internal flash that isn't used by the default install, and it's about 300MB - if you want to use internal flash, that might be a reasonable choice. (/dev/mtdblock7)
You can also swap to an SD card, if you aren't going to be using the slot for anything else (/dev/mmcblk0 or /dev/mmcblk0p1).

You will need to use mkswap to prepare the partition or card, and then add an appropriate time to the fstab, for example:
```

/dev/mmcblk0    none    swap    defaults    0 0

```

---

### Post by mmanu on 2010-04-18
> **abrasive said:**
> Flash memory isn't great swap - writes stress its physical structure, and it wears out.
Since the internal flash isn't replaceable, swapping is not configured by default.

There is a partition in the internal flash that isn't used by the default install, and it's about 300MB - if you want to use internal flash, that might be a reasonable choice. (/dev/mtdblock7)
You can also swap to an SD card, if you aren't going to be using the slot for anything else (/dev/mmcblk0 or /dev/mmcblk0p1).

You will need to use mkswap to prepare the partition or card, and then add an appropriate time to the fstab, for example:
```

/dev/mmcblk0    none    swap    defaults    0 0

```

thanks a lot boss!

---

### Post by bernard_m on 2010-04-18
I installed Debian as explained by Abrasive, except that, like for some other persons, SD card wasn't viewed during installation and I had to manually mount it and copy data. Overall it works (I even installed and used epiphany) but there are serious permission problems which make it unusable without using only root account.

I had to change permissions of /, /var/tmp, /var/lock and /tmp (maybe other files need fixing). Even worse I had to add write permissions to /dev/null and other files of /dev. I'm not sure to know what is used to populate /dev : system is not running udev, but /dev file permissions are reseted on reboot.
Also I can't access network (when not logged as root). I used strace on "wget" and strace said "socket(PF_INET, SOCK_DGRAM, IPPROTO_IP) = -1 EACCES (Permission denied)". Do you know to fix these problems?

Another question : any hope to have sound card working?

---

### Post by mmanu on 2010-04-18
if i use mtdblock7 for swap, is there a chance that only this part of the internal flash breaks, leaving the rest of the memory usable? if so, since this part is unused, it seems to me that it's not such a bad choice to use it for a while.

what's about the buffers/cache mem seen in free-m? isn't it a kind of swapping on the internal flash?

does it make sense to use badblocks on flash? on boot, yaffs seems to find some bad blocks...

also, my lxde screensaver can't be configure due to the root pb evoked by bernard_m. the deamon is unable to contact the x server because access control is turn on, it says.

---

### Post by kaputnik on 2010-04-18
> **mmanu said:**
> 

@kaputnik
have you got the config pb with lxde-core - pcmanfm - hal ?
i have the same recurrent pb with the access point, that i "solve" like you...
i guess i've found the good browser, after epiphany, dillo, hv3, iceweasel & kazehakase, the good answer seems to be... midori!
i 've also tried some text-mode browser, really helpful when you want to dl much faster. elinks is not so bad, old school like :)


yeah i get the whole lxde-core - hal etc errors whenever i apt-get packages but it doesnt seem to affect anything noticably, plus "nfc_wait_idle():data area 0th ecc error position is byte555 bit2".
Currently ive got abiword, epdfView, iceweasal and epiphany loaded, with both those browsers loading pages very sluggish, with iceweasel being the worst. would love to get opera on this, which is my next goal after sorting out the wifi stuff.

i didnt think midori could work on the arm chip??
i used lynx but my uni webserver seems to not play nice with all its javascript so its no good. same with elinks.
onwards huh.

---

### Post by mmanu on 2010-04-18
> **kaputnik said:**
> yeah i get the whole lxde-core - hal etc errors whenever i apt-get packages but it doesnt seem to affect anything noticably, plus "nfc_wait_idle():data area 0th ecc error position is byte555 bit2".
Currently ive got abiword, epdfView, iceweasal and epiphany loaded, with both those browsers loading pages very sluggish, with iceweasel being the worst. would love to get opera on this, which is my next goal after sorting out the wifi stuff.

i didnt think midori could work on the arm chip??
i used lynx but my uni webserver seems to not play nice with all its javascript so its no good. same with elinks.
onwards huh.

epiphany works for you? ok, why not... mine wasn't due to the hal pb. it was the main reason i've tried other wm. but i've found a way to get around the hal issue. the lxde-core in main sid can be installed with pcmanfm-nohal which resolves the issue. the sid dep also contains midori for armel & it works really good (around 10 times faster than iceweasel!!). note that the nfc_wait_idle error appears more frequently when the sid deb is enable.

note to myself: cairo-dock wasn't a good idea.

---

### Post by Knightwalker on 2010-04-19
I tried install gnome and KDE onto debian.. 

'apt-get install gnome' 
'apt-get install KDE'

Results weren't so good~ :-(
KDE fired up error messages and gnome seemed to be working, but wasn't fully installed due to size of flash.
Probably 2g was not enough for installation. I will try LXDE.

---

### Post by abrasive on 2010-04-19
> **bernard_m said:**
> Overall it works (I even installed and used epiphany) but there are serious permission problems which make it unusable without using only root account.


I'm totally mystified as to the permission trouble. I noticed this problem when I finally got around to making a non-root account yesterday... Perhaps something built into the Android kernel? The Android boot scripts seem to set up device permissions on every boot.
I can't find any trace of permission games in the Debian boot scripts.

> **bernard_m said:**
> 
Another question : any hope to have sound card working?

It works (you can write to /dev/dsp).
The mixer device, however, seems to have a pretty broken driver. Not much to be done there for software which depends on it... sorry!

---

### Post by ZeroEfusion on 2010-04-19
ok i've tried icewm, lxde, jwm, and fluxbox.

--------------------------------------------------------
window manager:

LXDE was the slowest(in terms of ui responsiveness), while fluxbox seemed to be the fastest of the bunch. Icewm was probably the most useful for newbies. Disabling some of the fancy themes in lxde seemed to speed it up a bit, but not enough.
Fluxbox | Fastest
IceWM | Faster
JWM | Fast
LXDE | Slow 

--------------------------------------------------------
web browser:
I wanted to get dillo to work, but it was not in the repos. Tried lynx and galeon. Galeon was rather slow as i expected and required installation of some gnome libs. Going to look into finding dillo for arm.

--------------------------------------------------------
file manager: 
Tried pcmanfm and discovered the hal error that others have already mentioned.
pcmanfm was slow as to be expected.

Also tried thunar which was slower than pcmanfm.

The "Worker" file manager was the fastest of this bunch.
Wanted to try emlfm? or whatever the one is called in Damn small linux but it was not in the repos. will look for it later.
--------------------------------------------------------
couldn't get sound to work yet. I imagine i would have to get hal working first.
couldn't get pcmanfm, thunar, nor worker to recognize my usb jump drive
--------------------------------------------------------

Overall i think this system is much more responsive/faster than wince and android if you use a lighter window manager like fluxbox or icewm.


I will upload some screenshots when i get a chance.
Anyone had any luck getting sound to work...

---

### Post by kaputnik on 2010-04-19
> **mmanu said:**
> epiphany works for you? ok, why not... mine wasn't due to the hal pb. it was the main reason i've tried other wm. but i've found a way to get around the hal issue. the lxde-core in main sid can be installed with pcmanfm-nohal which resolves the issue. the sid dep also contains midori for armel & it works really good (around 10 times faster than iceweasel!!). note that the nfc_wait_idle error appears more frequently when the sid deb is enable.

note to myself: cairo-dock wasn't a good idea.

fantastic, just got the sid into sources and running midori now, much nicer.
and dumped the lxde for fluxbox, thanks to ZeroEfusion.
now for a wifi manager, maybe kismet
k

---

### Post by mmanu on 2010-04-19
> **kaputnik said:**
> fantastic, just got the sid into sources and running midori now, much nicer.
and dumped the lxde for fluxbox, thanks to ZeroEfusion.
now for a wifi manager, maybe kismet
k

you're welcome (for midori :D). midori is also in the squeeze main, maybe much stable. sid is usefull for the lxde-core compatibility with pcman-nohal, but with fluxbox you don't care. i'll also come back to fluxbox (more peacefully after some screenshots as the one at th end of [http://doc.ubuntu-fr.org/fluxbox](http://doc.ubuntu-fr.org/fluxbox)), if my father in law's wifi let me in... grrrrrr

---

### Post by trauma-d on 2010-04-19
Hi, I've been watching this thread from the very begining but haven't posted any thing because i dont think i'll be any help i love linux but am not very knowledgable of it. i have had one of these 7" mini netbook running windows ce 5 for quite some time now and i appologize in advance for my stupid questions but i cant help but ask cuz i like to learn. i have a few questions:
 
1: how do you tell exactly witch processor you have?
2: is there a place i can download the android your putting on these things?
3: and exactly how do you install it on the system
 
sorry for the dumb questions but im kinda a noobi.
:)
Thanks'
Trauma-D

---

### Post by sius071 on 2010-04-19
I sucessfully installed android on a 8505 netbook but i cannot get the wifi to work i finds the network but wont connect.

---

### Post by Knightwalker on 2010-04-20
I tried several kernels with Debian.
And none of them were succeded.

Here's the how dummy(it's me) installed gnome, KDE, and LXDE.

1. Format the SD with FAT (not 32)
2. extract 'extpart' to the SD card and delete scriptcmd and replace to scriptcmd.install. (Remame scriptcmd.install to scriptcmd)
3. Add 'extfart' to root of the SD card (So script folder and extfart file are placed on the root)
4. Insert sd card to WM8505 netbook
5. Few seconds later, smiling linux penguin showed up and begin installation.
6. After debian installation is done; 'willan login' and I type 'root' for default password.
7. activate ethernt and wifi.
   
    ifconfig eth0 up
    dhclient eth0    <--- for ethernet

     modprobe rt3070sta   <--- for wifi

8. Install xwindow (takes about 15minutes)

    apt-get install xsever-xorg-video-fbdev xfonts-base xinit

-----------------------------------------------------------------------------------------------

E: Directory 'var/log/apt/' missing    <--- showed up.



9. Install gnome, KDE, LXDE

    apt-get install gnome            (For full verion. will not work without extra storage)

    apt-get install gnome-core    (For lite version.)


When installations were done, typed 'startx' to enter gnome.
Results were pretty bad.
Gnome (full version) did enter title screen with mouse moving, but few seconds later back to debian commend prompt
Gnome (minimal version) also did enter title screen, but this time title and error sign and back to debian commend prompt.

    apt-get install kde   (Full version)
    apt-get install kde-core (Minimal version)

After installations were finished, typed 'startkde'
KDE (full version) didn't enter title screen.
For installation of KDE(minimal version), well... What can I say.. Hangs..

    apt-get install lxde (I only tried full version)

But LXDE installation was incomplete with this command.

E: Directory 'var/log/apt/' missing    <---again?
E: Sub-process user/bin/dpkg returned an error code  (1) <-- WTF??

So, I tried gnome, KDE, and LXDE.
None of them work and I don't know the exact problem.

---

### Post by Knightwalker on 2010-04-20
> **trauma-d said:**
> Hi, I've been watching this thread from the very begining but haven't posted any thing because i dont think i'll be any help i love linux but am not very knowledgable of it. i have had one of these 7" mini netbook running windows ce 5 for quite some time now and i appologize in advance for my stupid questions but i cant help but ask cuz i like to learn. i have a few questions:
 
1: how do you tell exactly witch processor you have?
2: is there a place i can download the android your putting on these things?
3: and exactly how do you install it on the system
 
sorry for the dumb questions but im kinda a noobi.
:)
Thanks'
Trauma-D


1: how do you tell exactly witch processor you have? 

- Click on control panel -> system (I presume, your netbook has VT8500)

2: is there a place i can download the android your putting on these things?

- If your system has VT8500 CPU, impossible!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! Anroid only works WM8505

3: and exactly how do you install it on the system

- Well, it's easy.  

download rom -> format your SD card (fat) -> extract rom to SD card (fold name script) -> insert SD card -> wait for installation -> green alien

---

### Post by norseman-has-a-laptop on 2010-04-20
the posts are coming along 

there great i like watching these convos go

---

### Post by bernard_m on 2010-04-20
> **Knightwalker said:**
> 
E: Directory 'var/log/apt/' missing    <--- showed up.

Answer is in Abrasasive's README file : "you may wish to mkdir /var/log/apt". Actually, it's more than recommended to do so before using apt for the first time. Maybe abrasive could upgrade the extpart file.

---

### Post by kaputnik on 2010-04-20
> **mmanu said:**
> you're welcome (for midori :D). midori is also in the squeeze main, maybe much stable. sid is usefull for the lxde-core compatibility with pcman-nohal, but with fluxbox you don't care. i'll also come back to fluxbox (more peacefully after some screenshots as the one at th end of [http://doc.ubuntu-fr.org/fluxbox](http://doc.ubuntu-fr.org/fluxbox)), if my father in law's wifi let me in... grrrrrr

have you had any luck with the wifi drop-out? i read [http://ubuntuforums.org/showthread.php?t=694026](http://ubuntuforums.org/showthread.php?t=694026) that mentioned needing to use RT2870_LinuxSTA_V2.3.0.0 driver as there were problems with the chipset found in the little wifi usb inside, though this may have been fixed in this kernel. Trying kismet i havent been able to get it capture source yet as it isnt recognising either RT3070 or RT2870 (as reported in iwconfig) as  a legal source.

Fluxbox is much nicer but i cant seem to get a terminal window to open up in it, and it would be good to have a cpu meter as its hard to tell if the little netbook is actually doing something or just saying no. Then after this its on to try getting a battery reading too, though i did run it for 2.5 hours on battery before it shutdown, not bad.

---

### Post by trauma-d on 2010-04-21
> **Knightwalker said:**
> 1: how do you tell exactly witch processor you have? 

- Click on control panel -> system (I presume, your netbook has VT8500)


I went to control panel and clicked system and it says "Processor Type: AKARM, ARM926-AK7802-266MHz"

does that mean i have a different processor all together?

-Trauma-D

---

### Post by ch4rlii on 2010-04-21
> **trauma-d said:**
> 
does that mean i have a different processor all together?
-Trauma-D
I'm afraid so. This might be your forum:
[http://mininetbooks.your-board.com/](http://mininetbooks.your-board.com/)

Regards,
Charly

---

### Post by trauma-d on 2010-04-21
> **ch4rlii said:**
> I'm afraid so. This might be your forum:
[http://mininetbooks.your-board.com/](http://mininetbooks.your-board.com/)

Regards,
Charly


Darn! oh well.
Thanks.

-Trauma-D

---

### Post by trauma-d on 2010-04-21
does anyone have any good links on where to go buy one of these things that already has android or some other flavor of linux on it? because i hate windows ce.

thanks,

-Trauma-D

---

### Post by barthezz on 2010-04-21
Fellows, I'm trying to install EasyPC Linux on vt8500, but it doesn't detect my 256Mb SD-card.
It is formatted like this:
1) ext2 - ~200mb contains ext2part contents
2) fat32 - ~40mb from the fatpart.tgz (the script folder must be in the root?)
But wince5 starts like it should be done with no SD card. What's wrong?

---

### Post by mikkoj on 2010-04-21
FAT should be the 1st partition!
Not sure, but the script should be in the first partition normally.


> **barthezz said:**
> 
1) ext2 - ~200mb contains ext2part contents
2) fat32 - ~40mb from the fatpart.tgz (the script folder must be in the root?)
But wince5 starts like it should be done with no SD card. What's wrong?

---

### Post by barthezz on 2010-04-21
New behavior: with the SD it boots until the devices initializing. I mean Battery, SD, SERIAL  etc. list. It thinks of something... think of good OS :) I will walk for ten minutes. If this continues "thinking" I will kill it :)

---

### Post by barthezz on 2010-04-21
News: my netbook stops loading during the boot after it shows the cursor. :( 
What's next?

---

### Post by Tazergnome on 2010-04-22
> **sius071 said:**
> I sucessfully installed android on a 8505 netbook but i cannot get the wifi to work i finds the network but wont connect.

That's strange, I have the same model and while Android is extremely buggy on mine, the wifi worked when I first installed it from SD. So maybe there are other hardware differences? Knowing Chinese "generic" companys I think it's likely since they may have different factorys making these. 

I hope someone can work out some of the bugs with Android on this model. Sometimes it will boot...and sometimes not. It also likes to end programs randomly and freeze all the time.

This is just speculation, so correct me if I'm wrong. I get the feeling that since this is an ARM core without a bios that it handles things completely differently from an X86 system. I noticed that both WinCE and Android behave in the same way when booting up. I almost want to say it's like they are operating closer to root level on these systems. I think that makes since because of the lack of a bios. The operating system has to tell the CPU exactly what to do without the help of a bios as a mediator? I'm guessing this is why each operating system has to be made to work with each specific model of ARM. 

These things fascinate me a bit so I want to learn as much as I can about them. Thanks to everyone who has worked on these.

-TG

---

### Post by kaputnik on 2010-04-22
> **trauma-d said:**
> does anyone have any good links on where to go buy one of these things that already has android or some other flavor of linux on it? because i hate windows ce.

thanks,

-Trauma-D

there is one on ebay at the moment, i asked them about android (they use 1.5) and whether it would work or if they would update to 2.1 and they said their "technical team" is working on it. think it was a bout 50 USD with same in delivery. btw theres about 230 7" netbooks on ebay at the moment too.

---

### Post by trauma-d on 2010-04-22
> **kaputnik said:**
> there is one on ebay at the moment, i asked them about android (they use 1.5) and whether it would work or if they would update to 2.1 and they said their "technical team" is working on it. think it was a bout 50 USD with same in delivery. btw theres about 230 7" netbooks on ebay at the moment too.


Thank you, :D
-Trauma-D

---

### Post by digiapb on 2010-04-22
> **trauma-d said:**
> does anyone have any good links on where to go buy one of these things that already has android or some other flavor of linux on it? because i hate windows ce.

thanks,

-Trauma-D


haleron.com states they are offering them with Android....

however I can not verify if they are shipping them at this time.

[http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27](http://haleron.com/index.php?page=shop.product_details&flypage=flypage.tpl&product_id=11&category_id=2&option=com_virtuemart&Itemid=27&vmcchk=1&Itemid=27)

---

### Post by anjers on 2010-04-22
I'm thinking of buying one of these just so that I can use it for surfing the web and what not. Is it possible to use yahoo on it? Also has anyone had any confirms with getting Ubuntu to work on these things yet? Are they really worth paying $80-98 for one?

---

### Post by Knightwalker on 2010-04-22
> **anjers said:**
> I'm thinking of buying one of these just so that I can use it for surfing the web and what not. Is it possible to use yahoo on it? Also has anyone had any confirms with getting Ubuntu to work on these things yet? Are they really worth paying $80-98 for one?


Hmmm. You can use yahoo and youtube. Also you can check your email and chat with other people online. WM8505 nebtook has everything you need. But it is little tricky to install application on to windows CE 6.0 based WM8505. You cannot use hotsync nor cab installer. In order to use windows CE 6.0 based WM8505, you have to extract cab by using MSCEInfEn unless you will impossible to install programs. Also most window mobile applications do not compatible to windows CE 6.0. Overall, if you want web surfing, some document works and watch video, it's not to bad. Except speed of windows explorer is pretty bad. 
You can also install 1.6 android (Donut). I tried opera mini 5 beta and dolphin brower and they are kick ***. But android OS itself, it is still little buggy to use.

---

### Post by kaputnik on 2010-04-22
> **sius071 said:**
> I sucessfully installed android on a 8505 netbook but i cannot get the wifi to work i finds the network but wont connect.
well im continuing to work on the debian install based on the android port so it probably has the same issues. im on a 8505 smart book too, so i opened it up to have a look at the wifi usb stick thats glued to the side of the lcd, its labeled as BT-RT3070-5D and the chip onboard is a ralink RT2070L. i reckon theres a driver issue here. will try and get this resolved but dont know how much time ive got as uni is bit busy at the moment.

---

### Post by sius071 on 2010-04-23
I dont mean to intrude but i did install android and i also got the wifi to work but my question is can i install any other ROM using the method you described.

---

### Post by kaputnik on 2010-04-23
> **sius071 said:**
> I dont mean to intrude but i did install android and i also got the wifi to work but my question is can i install any other ROM using the method you described.

depending on the chipset you have on your netbook you can follow the guide and work done by abrasive for a debian install thats based on android. think that part starts about page 66 of this thread. with debian you can then install a window manager amongst many other things via the apt-get install method. i think the fluxbox manager is the best as its light and doesnt slow the little netbook down too much. it kinda depends on what you want your netbook to do, me i want pdf and doc viewing, basic compliants browser and a wifi with wpa - ttls/pap for uni, so thats where im headed.

---

### Post by ch4rlii on 2010-04-23
@kaputnik:
Could you give an overview what you've achieved so far?
The wi-on and wi-off scripts prepared by  abrasive do not work for you?
What about sound?
Did you find a lightweight PDF-viewer?
Thank you in advance!
Regards,
Charly

---

### Post by kaputnik on 2010-04-23
> **ch4rlii said:**
> @kaputnik:
Could you give an overview what you've achieved so far?
The wi-on and wi-off scripts prepared by  abrasive do not work for you?
What about sound?
Did you find a lightweight PDF-viewer?
Thank you in advance!
Regards,
Charly

aight, i got an 8505 smartbook off ebay that had win CE6.0 which i booted as a debian as per abrasive's work. then i tried a few window managers and settled on fluxbox as being best, as per a previous post. the browser i use is midori which is via the sid branch of debian and it works quite well too. the pdf viewer is ePDFView and it works but it can be a little slow rendering the pdf to screen. i also have abiword for word docs. 

the wifi on and off scripts work fine for me but the wifi connection drops out after minute or so of inactivity so i need to solve this somehow. at the moment, after boot i enter modprobe rt3070sta and then execute the wifi script. i have the /etc/network/interface file edited to my home wlan ap but eventually i want to get a wifi manager to run it all cos i need to access several different wifi aps. for this i been looking at kismet which doesnt recognise the wifi chip as valid so am about to look into wicd. another thing is that if i have a usb memory stick in the rear usb port then the wifi card drops out, maybe something to do with the usb bus. theres two - one a usb1 and the other a usb2 so im assuming the rear port and wifi run off the usb1 and dont have enough power for two things at once if they draw too much current, wifi sucks amps huh.

i havent even bothered with the sound yet as it isnt vital to what i need this netbook to do. i may end up pulling it apart again to see if theres anything else i can glean from the motherboard. one thing i did notice after the debian install is the the sd card will not serve as a boot device. not concerned yet cos i just mount the sd to a directory after boot up.

---

### Post by ch4rlii on 2010-04-23
Thank you!
> **kaputnik said:**
> one thing i did notice after the debian install is the the sd card will not serve as a boot device.
Does this mean there is no coming back to Android or another OS?
If something goes wrong with the Debian install, the device is bricked?

---

### Post by ericanilaru on 2010-04-23
> **kaputnik said:**
> 
the wifi on and off scripts work fine for me but the wifi connection drops out after minute or so of inactivity so i need to solve this somehow. 

@kaputnik

I know some of the MUD clients eg TT++ can be set up to do something every so often, to stop you being droped by the server whilst reading long descriptions / instructions etc.  - you could prob use this or similar script to get around your inactivity problem.

Hope this useful

E

---

### Post by kaputnik on 2010-04-23
> **ch4rlii said:**
> Thank you!

Does this mean there is no coming back to Android or another OS?
If something goes wrong with the Debian install, the device is bricked?

not too sure on the details but the debian installer over writes the bootloader and the rom so apparently theres no going back via the method that has you just putting an sd card in with whatever OS you fancy. there would be a way to flash it again i suppose but im not interested in that aspect so im not looking into it. Abrasive is the one to ask about this. and theres also the version of debian posted that allows you to just boot to console, not to install but i think thats a moot point if you have already gone for android as that also rewrites the bootloader.

corrected - as abrasive points out later, its still possible to boot from sd card after debian install

---

### Post by anjers on 2010-04-23
Has anyone been successful with Ubuntu to work on these things yet? Are these mini netbooks really worth paying $80-98 for one?

---

### Post by norseman-has-a-laptop on 2010-04-23
if you boot from a usb you can get them to work

---

### Post by dadwarf on 2010-04-23
@anjers

No i think (i have a wm8505) it's a toy for geek...a cheap cheap toy...with mine i can't surf (too slow, have you ever surf on a pda ?) but i can play with a console, nice isn't it ! my iPhone is quicker, have bigger battery life and more applications...so NO, spend 80$ in that kind of product is not a good thing. But wait that's only the begining of a new generation of chinese-low-cost-portable products !

---

### Post by anjers on 2010-04-23
Hmm, Now after you having said that makes me not want to get one. But I would still love to get one as I would only use it for the purpose of checking e-mail, surfing the web and using instant messenger.


It appears the only ones I have found on ebay now are the ones that are running ARM-VT8500 and theres some that say ARM-VT8505 but not many. I found one that has ARM-WM8505 and found one also that has a ARM926-AKCHIP (but it says 266MHZ). Which one would be the best to get?

---

### Post by kaputnik on 2010-04-23
> **norseman-has-a-laptop said:**
> if you boot from a usb you can get them to work
really? i havent looked at that, thanks for the tip.:)

---

### Post by kaputnik on 2010-04-23
> **anjers said:**
> Hmm, Now after you having said that makes me not want to get one. But I would still love to get one as I would only use it for the purpose of checking e-mail, surfing the web and using instant messenger.


It appears the only ones I have found on ebay now are the ones that are running ARM-VT8500 and theres some that say ARM-VT8505 but not many. I found one that has ARM-WM8505 and found one also that has a ARM926-AKCHIP (but it says 266MHZ). Which one would be the best to get?

its all down to what you want to use it for and the form factor that best suits. i needed a proper keyboard, wpa-enterprise compatible wifi, browser, pdf viewer and word doc read/write. all for the least amount of money possible. i could have got an ipod touch but the onscreen keyboard would irritate me as well as the small screen size. the netbook/smartbook are little better than a toy, they low powered and kinda crap but they can work to within a limited scope. 
as for the chipset thats much of a muchness really, there are things compiled only for one or the other. i think the android port is more developed on the 8500 but dont quote me on that ;) but the debian install is good for the 8505. if you do get one be aware that the windows ce OS uses that craptacular Internet explorer 6...

---

### Post by vinceCOOK on 2010-04-23
Hello everybody,

I just wondered what the condition of the Debian for wm8505 netbooks is at?

Does this Debain install easily? and what actually works?

Does the netbook sound work?
Does the wi fi work?
Do the usb sockets accept SD cards and USB devices?
Does video and medai playback work?
Does the web browsing fully support flash (youtube etc)


essentially, does this Debian operate in a similar manner
to other basic Linux distros?

Thanks,

Vince.

---

### Post by abrasive on 2010-04-23
The current Debian installer may render the SD card you are using unbootable as part of the install process - but it does not prevent SD booting in the future! Make a new boot card for whatever you're needing, and it will boot fine.
This means you can always go back from Debian to Android or WinCE with the appropriate installer.

I'm currently working on a full debian-installer port, so you can install to SD or internal Flash using the standard Debian installer.
Still need to find sources for the kernel I am using.

Don't expect Ubuntu. Ever. This thing is too limited to support complicated desktop UI.

And in general: for a fraction of the price of an iPhone, you get a bigger screen, a real keyboard, and most important of all - an open OS!

As an aside to buyers: a lot of WM8505 machines are sold as VT8500 on eBay - but listed with 300MHz clock speed. (I believe the 8500 is specified at 400MHz)

---

### Post by mmanu on 2010-04-24
> **abrasive said:**
> I'm currently working on a full debian-installer port, so you can install to SD or internal Flash using the standard Debian installer.
Still need to find sources for the kernel I am using.

hello,

i've had some troubles when trying some squeeze (or sid) packages (kernel panic on shutdown, freezing when connecting the sd card), for one package installation (essentially midori and deps) or for full squeeze upgrade. now i only run lenny with elinks or links2 browser and it works actually good enough, but i'm a bit anxious for the future. when squeeze will become stable (july?), will these problems come back? is it more safety to change your original sources.list from stable to lenny to avoid such issue?

---

### Post by vinceCOOK on 2010-04-24
Hello

Ok abrasive....

so what *dos* currently work on the Debian offered?

1) does the netbook sound work?
2) does video and mdeia playback work ok?
3) does wi fi work?
4) do the usb sockets take normal usb devices and SD sticks?
5) does the web browser support flash (youtube etc)

any advice will be good.

V

---

### Post by Knightwalker on 2010-04-24
> **abrasive said:**
> The current Debian installer may render the SD card you are using unbootable as part of the install process - but it does not prevent SD booting in the future! Make a new boot card for whatever you're needing, and it will boot fine.
This means you can always go back from Debian to Android or WinCE with the appropriate installer.

I'm currently working on a full debian-installer port, so you can install to SD or internal Flash using the standard Debian installer.
Still need to find sources for the kernel I am using.

Don't expect Ubuntu. Ever. This thing is too limited to support complicated desktop UI.

And in general: for a fraction of the price of an iPhone, you get a bigger screen, a real keyboard, and most important of all - an open OS!

As an aside to buyers: a lot of WM8505 machines are sold as VT8500 on eBay - but listed with 300MHz clock speed. (I believe the 8500 is specified at 400MHz)

Excellant. First of all, I don't care about ubuntu. Running ubuntu at 300Mhz, it should be total nightmare.:(  

If I can play with LXDE with sound, mic and video support, then it's perfect. 

When you build next installer package, please include xwindows, selection screen for LXDE, IceWM or Fluxbox (or others).

---

### Post by sius071 on 2010-04-24
> **abrasive said:**
> For those of you with the VT8505/WM8505 based netbooks, I've rolled up a Debian system around the Android kernel that was released, with drivers or userland tools for everything.
It adds a few things (like a framebuffer console); it will run from SD alone, or if you wish, install to the device NAND.

X11 is not included to keep the download size down, but it's pretty quick to add with apt-get (figure another 25MB or so of downloadables).

You can find the filesystem tarballs and instructions at: [http://bur.st/~abrasive/wm8505_linux/]("http://bur.st/%7Eabrasive/wm8505_linux/")

I tried the link and it is not working please help.

---

### Post by kaputnik on 2010-04-25
> **sius071 said:**
> I tried the link and it is not working please help.
its working for me.
more stuff added today is conky via apt-get. after a bit of a config edit its working nicely within fluxbox to give me ram, cpu and network stats.

may have time for more today but not likely.

---

### Post by mikkoj on 2010-04-25
> **abrasive said:**
> Can you enter the console (just hit Enter) and grab the output of the following: ```
 ls /dev/mmcblk0* 
ls /mnt/mmcblk0* 
```  If you find your partition (eg. as mmcblk0p1) you should be able to ```
 mount /dev/mmcblk0p1 /mnt/sd 
mount /dev/mtdblock9 /mnt/mtd 
tar xzf /mnt/sd/extpart.tgz -C /mnt/mtd 
``` which will complete your install.

This works perfectly!

How can I install it to SD-card, keeping Android? (have been installing both of them lately...:)

---

### Post by barthezz on 2010-04-25
Hi again.
I have just opened my netbook and seen such label on the biggest chip:
ANYKA AK7802TQ21605 FS07L9.
Is it VT8500 or something else?
How can I install Linux on it or other OSs?
When I boot it now, it doesn't complete the boot neither with live SD nor without it.
What should I do?

---

### Post by lucasart on 2010-04-25
> **celem said:**
> 
This machine has some oddities. There doesn't appear to be a BIOS ROM - thus booting from a unetbootin USB is impossible. The WINCE kernel must be directly loaded into the flash drive at the factory.
Such things should be severly boycotted! Wondows is already forced onto most useres who have to pay for it without knowing. And know even after paying for it, you cannot get rid of it: to hell the windows ce bios!
And forget xubuntu, this distro is a real failure. Its goal was to be a lighter ubuntu, but in fact it's just lamer and actually even bulkier in ram!! there's only one lightweight *buntu worth considering, and that's lubuntu.

---

### Post by theonesdg on 2010-04-25
Anyone want to buy a broken one for parts? Seems my SD slot wasn't working (was going to load android) so I opened her up to see if the connection was ok. Put it back together and.. nada.

---

### Post by Knightwalker on 2010-04-26
I tried several WM with abrasive's debian X11 and these are results.

LXDE: Works fine. But extremly slow. Easy to use. One web browsing cause extreme delay.
Xfce : Quite speedy. Default Web browser doesn't work
IceWM: Very fast. Problem is I don't know how to use it.
Fluxbox: Very fast. I totally naked.
Gnome: Couldn't complete installation. (Gnome is too huge to install)
KDE: Same problem.


It seems Xfce is good for linux dummies. But I need to confirm it.

---

### Post by kaputnik on 2010-04-26
> **kaputnik said:**
> its working for me.
more stuff added today is conky via apt-get. after a bit of a config edit its working nicely within fluxbox to give me ram, cpu and network stats.

may have time for more today but not likely.

weel dropped the net stats as they werent that important, but with midori and abiword open i get 71% of ram used which isnt bad considering i get 48% with just fluxbox running. redraw on screen is obviously going to be slow and rather obvious but its manageable if you pretend its 1994....:)

wifi stuff next hopefully.

---

### Post by su8z3ro on 2010-04-26
I have a wince umpc with the wm-8505 processor and i'm trying to install abrasive's debian. every thing works until it reboots the it just sits there with the penguin on the screen with the progress bar running underneath... any ideas? i thought it may have been a bad download so i downloaded again and tried again and am getting the same result.... it's been going for about an hour now.... should it take this long? 
Processor Type:  VIA ARM WM-8505 
Processor Speed:  300 MHz 
Screen Size:  7 inch  
Operating System:  WindowsCE 6.0 
Memory (RAM):  128 MB 
Primary Drive:  NAND Fast Flash 
Hard Drive Capacity:  2 GB 

Thanks,
su8z3ro

---

### Post by Pilotgeek on 2010-04-26
I honestly think that adroid IS the best version of linux to use on these netbooks. It's extremely fast, and I can have multiple internet windows open while playing mp3s. It is very easy to get a terminal emulator runing and rooting android is quite easy. Because android is designed for something with this horrible of hardware, it runs better than any other distro with any other window manager. Just my $0.02.

---

### Post by moblo on 2010-04-26
> **Pilotgeek said:**
> I honestly think that adroid IS the best version of linux to use on these netbooks. It's extremely fast, and I can have multiple internet windows open while playing mp3s. It is very easy to get a terminal emulator runing and rooting android is quite easy. Because android is designed for something with this horrible of hardware, it runs better than any other distro with any other window manager. Just my $0.02.

No doubt android may be the better choice at the moment. i agree, it is optimised for our kind of hardware. But you have to remember that linux is still very new on these machines. Give it time and people will slowly keep building on it, making it more user friendly and efficient. 
On that note, I have somewhat of a request. Would it be possible for someone to package a debian installer with x11 and a few basics to have it up and running. I am not to good with working at comand line. i do intend to learn, but at the moment with uni exams, i dont have much time at the moment. The thing that is most important os to have a frontend for the wifi. I have no idea how to set up and maintain the wifi from command line. 
Thanks

---

### Post by dudesky1325 on 2010-04-27
> **Knightwalker said:**
> I tried several WM with abrasive's debian X11 and these are results.
 
LXDE: Works fine. But extremly slow. Easy to use. One web browsing cause extreme delay.
Xfce : Quite speedy. Default Web browser doesn't work
IceWM: Very fast. Problem is I don't know how to use it.
Fluxbox: Very fast. I totally naked.
Gnome: Couldn't complete installation. (Gnome is too huge to install)
KDE: Same problem.
 
 
It seems Xfce is good for linux dummies. But I need to confirm it.
 
Knightwalker which do you think is better for these little machines? Xfce or LXDE? I did some looking and I like LXDE but  what do you think?

---

### Post by su8z3ro on 2010-04-27
> **su8z3ro said:**
> I have a wince umpc with the wm-8505 processor and i'm trying to install abrasive's debian. every thing works until it reboots the it just sits there with the penguin on the screen with the progress bar running underneath... any ideas? i thought it may have been a bad download so i downloaded again and tried again and am getting the same result.... it's been going for about an hour now.... should it take this long? 
Processor Type:  VIA ARM WM-8505 
Processor Speed:  300 MHz 
Screen Size:  7 inch  
Operating System:  WindowsCE 6.0 
Memory (RAM):  128 MB 
Primary Drive:  NAND Fast Flash 
Hard Drive Capacity:  2 GB 



Thanks,
su8z3ro



Come on.... anyone have any ideas???

---

### Post by styol on 2010-04-27
hey there. long story short i've been following the thread for a week or  two and recently got a WM8505 (spicy red color), been in touch with  abrasive and some other peoples via the IRC room (  irc://irc.freenode.net/#easypc ) and we've been able to A) figure out an  issue that ships with these devices and B) a way to work around it by  using both an SD card AND a USB stick.

If you have been trying to  boot debian live via SD card on a WM8505 and have not been able to,  likely by getting a loader that never finishes loading, then  instructions on a temporary easy work around are to follow. The issue  specifically is that the SD reader itself on the motherboard and/or the  kernel mounts the SD card itself in Read Only mode -- which makes it  impossible for Debian to do its ninja magic and get itself running.  Abrasive thought maybe his SD reader was broken, so he performed a  hardware work around, but both myself and another user in IRC have been  able to verify that this is the case. Have no fear! this totally works:

[B][SIZE=4]How to Live Boot Debian via SD + USB[/SIZE]

[/B]Going  to briefly describe the basic steps required to prepare both an SD card  and a USB flash drive for live booting Debian without installing or  overwriting your nand. Basically, the SD card provides instructions on  what to do and which filesystem to load, and then it loads the debian  filesystem off the USB stick so you can play live. All the packages you  install and changes you make will stick.

You will need to format  your SD card and USB stick much in the same way you previously did,  difference being SD card holds the script directory and is FAT32 while  the USB stick is EXT2 and holds the Debian filesystem. The following  references fdisk specifications.

**SD Card**
Type: b   (WIN95 FAT32)
Size: 32MB
Contents: scripts folder (extracted from  fatpart.tgz or fatpartusb.tgz)

[B]USB flash drive
[/B]Type: 83 (Linux) aka EXT2
Size:  Up to you, but at least 256mb preferably.
Contents: debian  filesystem (extracted from extpart.tgz)

Probably going to skip  describing how to go about formatting, partitioning, and preparing the  SD card and USB stick using linux and fdisk or otherwise, but will  probably end up posting it at some point (if not here, then at the site  we're working on for these devices and linux)

Both partitions (SD  / USB) for use in this should be the 1st and primary  partition #1 -- following instructions will expect that debian  filesystem is at /dev/sda1 which it always is with 1 usb device plugged  in and debian filesystem as first partition. You can adjust as needed  with the manual instructions.

**Manual preparation of cmd / scriptcmd**
If you would like to  do this manually, or need to make adjustments to where the debian fs is  loaded from (perhaps you're using partition 2 and want to make it  /etc/sda1p2 ? ) follow these basic instructions:

[LIST=1]
[*]this  assumes you're using linux
[*]navigate your way into the  /scripts directory on the sd card
[*]edit the *cmd* file  with your favorite editor
[*]change *root=/dev/mmcblk0p2* to *root=/dev/sda1*
[*]add  *rootdelay=10* after *root/dev/sda1*
[*]**should read:***  setenv bootargs mem=112M root=/dev/sda1 rootdelay=10*
[*]now  execute ./make_scriptcmds
[*]place SD in wm8505 and plug USB stick  in
[*]reboot, and voila.. dinner is served
[/LIST]

[B]Download  SD + USB - fatpart.tgz / scriptcmd
[/B]extpart.tgz for the USB stick  is the exact same, but here is a download to the adjusted scriptcmd and  adjusted packaged version, fatpartusb.tgz

[LIST]
[*][fatpartusb.tgz]("http://bento-linux.org/sites/default/files/fatpartusb.tgz")
[*][scriptcmd]("http://bento-linux.org/sites/default/files/scriptcmd")
[/LIST]

The originals:
[http://bur.st/~abrasive/wm8505_linux/1.0/fatpart.tgz]("http://bur.st/%7Eabrasive/wm8505_linux/1.0/fatpart.tgz")
[http://bur.st/~abrasive/wm8505_linux/1.0/extpart.tgz]("http://bur.st/%7Eabrasive/wm8505_linux/1.0/extpart.tgz")


Thank you very much for all your help and hard work abrasive, he's definitely the only reason i was able to figure out how to get it to work in this way :) thanks also to everyone else thats helped me from the IRC room, much appreciated

---

### Post by Knightwalker on 2010-04-28
> **dudesky1325 said:**
> Knightwalker which do you think is better for these little machines? Xfce or LXDE? I did some looking and I like LXDE but  what do you think?

Well, LXDE seems to user friendly and definitely for beginner. But, as I mentioned earlier, it too slow!!!!!!! If you have some kind overclock utility, it may helps. 

Running speed of Xfce is OK. BUT I still couldn't figure out why default browser doesn't work. I may get some result over the weekend.

---

### Post by sius071 on 2010-04-28
Can i do the same with android-ARM-8505-Smartbook file meaning install without erasing or rewriting the entire NAND it was suggested in another forum that install the android os this way would be better. I would like some pointers how the how to, im a beginner forgive me.

---

### Post by sius071 on 2010-04-28
Can the android-ARM-8505-Smartbook file be installed without erasing or rewriting the entire NAND on the 8505?

---

### Post by milki on 2010-04-28
There seems to be a finished Android kernel system for WM8505 chipsets. But then it's keyboard-less and might not work without touchscreeny:

[http://www.linuxfordevices.com/c/a/News/Eken-M001/](http://www.linuxfordevices.com/c/a/News/Eken-M001/)
[http://www.ekengroup.com/en/product/show.asp?id=780](http://www.ekengroup.com/en/product/show.asp?id=780)

---

### Post by barthezz on 2010-04-28
Need help really. 
Tried to restore the firmware using the software from cnmbook.com.
I've done everything shown in the instructions. But now it doesn't boot. Just blinks with 3 right LEDs and nothing else. 
I need help :(

---

### Post by mariociausculo on 2010-04-28
First of all hello to everyone and congratulations. 

The Eken does not only the TP701 

but also [http://www.ekengroup.com/en/product/show.asp?id=770](http://www.ekengroup.com/en/product/show.asp?id=770)

and many others that are studied on this forum!

---

### Post by kaputnik on 2010-04-28
Aight, got a chance to run some more wifi tests on the wm8505 debian install running fluxbox etc. apt-get rutilt which is supposed to run nicely with legacy drivers for ralink chips. running it from within fluxbox is so far giving me a nice UI to make settings and more importantly maintain profiles for different AP. 
Has anyone else got a good wifi manager or success with either rutilt or some other manager?

update - rutilt connects to my home AP and seems to stay connected, no drop out as before. it runs with 52% ram used in fluxbox.
next will try with my uni eduroam wpa-enterprise AP.

---

### Post by dudesky1325 on 2010-04-28
> **Knightwalker said:**
> Well, LXDE seems to user friendly and definitely for beginner. But, as I mentioned earlier, it too slow!!!!!!! If you have some kind overclock utility, it may helps. 

Running speed of Xfce is OK. BUT I still couldn't figure out why default browser doesn't work. I may get some result over the weekend.

I honestly don't care too much about the speed, just getting another OS on the damn thing. I think if you uninstall it and re-download it from somewhere else, it might work, or regular chrome might work. Do you think you could email me the instructions on how you installed it? I'm [email]dudesky1325@yahoo.com[/email]

---

### Post by dudesky1325 on 2010-04-29
What is the stock browser on Xfce Knightwalker?

---

### Post by anjers on 2010-04-29
So I ended up buying one of these because well I am limited to how much I can spend and I really only need it to chat every once in awhile, surf the web and do my exams online. I bought one of the Pink ones :) It says for specs that it is a VT-8500 and has WinCE 6.0  only time will tell though for when I get it. Anyone who has bought theirs off ebay, How long did it take? I am kind of excited to get it. These can't play flash whatsoever correct?

---

### Post by kaputnik on 2010-04-30
> **kaputnik said:**
> 

update - rutilt connects to my home AP and seems to stay connected, no drop out as before. it runs with 52% ram used in fluxbox.
next will try with my uni eduroam wpa-enterprise AP.

now it seems, after reading some forums of course, that the rutilt is only good for the following network encryptions - none, wep, wpapsk or wpa2spk. authentication servers are good with wpa_supplicant, which is what i need for uni work. so if you dont need wpa enterprise then the rutilt is still good for wifi connectivity. but i will have to look into the wpa stuff again.
As an aside, this post is being written on my 8505 using fluxbox, midori and rutilt for wifi :)

---

### Post by Knightwalker on 2010-04-30
> **dudesky1325 said:**
> I honestly don't care too much about the speed, just getting another OS on the damn thing. I think if you uninstall it and re-download it from somewhere else, it might work, or regular chrome might work. Do you think you could email me the instructions on how you installed it? I'm [EMAIL="dudesky1325@yahoo.com"]dudesky1325@yahoo.com[/EMAIL]

Pretty easy.

Download extpart.tgz and fatpart.tgz from abrasasive's website.

Format SD card. (FAT)

Extract fatfart.tgz to SD card and copy extpart.tgz to root of formatted SD card.

Insert SD card.

Wait for installation. (Linux penguin will show up)

After installation, remove SD card.

Boot and probably 30 seconds later "william login" will show up.

Type "root"

Then now you have to make some setup.

In my case, I activated ethernet instead of wifi. 

At root directory, type mkdir var/log/apt (You must make this directory.)

Type 

'ifconfig eth0 auto'
'dhclient eth0'

to activate ethernet. (I prefer cable~~)


If you want to active wifi

Type

'modprobe rt3070sta'

Now install xwindows

Type

'apt-get install xserver-xorg-video-fbdev xfonts-base xinit'

Now you are almost ready to go.

'apt-get install xfce4' for xfce

'apt-get install lxde' for LXDE

LXDE's default browser is Konquer.

I could not figure out xfce default browser. (Maybe default browser section is just default.)

---

### Post by dudesky1325 on 2010-04-30
ok. do you think you could email those instrctions to me?
I'm not very technical so I really hope I dont mess anything up while I do this.
wish me luck!
 
 
Hey do you think you could send me some pictures of what all that stuff looks like, so I know what I'm doing is right

---

### Post by anjers on 2010-05-01
Which one of these netbooks are you able to put linux on? I can't wait to get mine.

---

### Post by dudesky1325 on 2010-05-01
I think I might have done something wrong...
I did everything and it wrote to the hard drive, but now it wont go past the smiling penguin. I tel it sit over night and still nothing. Any ideas?

---

### Post by drakkcoil on 2010-05-01
During the installation on mine it said it couldn't find the SD card, therefore echoed a "Can't find extpart.tgz on SD card!" and dropped to a console that can't do anything. If I reboot mine also sits at the penguin picture with the infinite progress bar.

Any idea why that happened?

I used the scriptcmd.install file like on the INSTALL readme says because the regular scriptcmd sat at a progress bar (no penguin) and never did the NAND writing stuff.

---

### Post by dudesky1325 on 2010-05-01
> **drakkcoil said:**
> During the installation on mine it said it couldn't find the SD card, therefore echoed a "Can't find extpart.tgz on SD card!" and dropped to a console that can't do anything. If I reboot mine also sits at the penguin picture with the infinite progress bar.
 
Any idea why that happened?
 
I used the scriptcmd.install file like on the INSTALL readme says because the regular scriptcmd sat at a progress bar (no penguin) and never did the NAND writing stuff.
 
 
That happened to me too, did you remember to extract expart to the SD card too? and mine has the infinite progress bar and the penguin too

---

### Post by drakkcoil on 2010-05-01
Yep its on there. So I have no idea whats up with that.

---

### Post by dudesky1325 on 2010-05-01
Then I have no clue whats going on either. It installed and everything, its just stuck at the penguin!


Has anyone tried putting the Chrome OS on one of these?

---

### Post by kaputnik on 2010-05-01
> **drakkcoil said:**
> Yep its on there. So I have no idea whats up with that.

when i got that problem it was down to the sd card not being formatted correctly or the install script not being read.

using a windows box i formatted the sd card into FAT
extracted the fatpart to the sd card
copied the extpart to the sd card
in the sdcard, open the scripts folder and rename "scriptcmd.install" to "scriptcmd"
plug the sdcard into the netbook and boot from there.
note that this is to install debian to the netbook, not just to boot from sd card.
hope this helps

---

### Post by pakt on 2010-05-02
@anjers and others who have asked about where WM8505 smartbooks can be bought.

I bought a couple through Aliexpress from China that work well with abrasive's Debian Linux.
They cost US$118.23 each including free shipping worldwide.

Here's a link to the smartbooks I bought:
[http://www.aliexpress.com/product-gs/286817067-netbook-laptop-wholesalers.html](http://www.aliexpress.com/product-gs/286817067-netbook-laptop-wholesalers.html)

Note that I have no connection with the seller. I'm just a satisfied customer.

---

### Post by moblo on 2010-05-02
I am having a similar problem to some other users. I have followed the instructions for installing debian to the wm8505 netbook, but when it gets to mounting the SD card, it echos Can't find extpart.tgz on SD card! and then goes press enter for a console, from which i cant do anything. I read through many different posts for hints. I ave tried a 4gb micro sd, 1gb micro sd and a 256mb full sd card. I have for matted each many times, and trieddifferent combination of files inside the script forlder. (ie: cmd/cmd.instal, scriptcmd/scriptcmd.instal/scriptcmd.orig). I am completely stumped. Any ideas?
Thanks

---

### Post by vinceCOOK on 2010-05-02
Moblo

I was reading that you may have to partition the SD card.

There is a full detailed post in here about how to put
the Debian onto SD card....very detailed.

Vince.

---

### Post by dudesky1325 on 2010-05-02
> **kaputnik said:**
> when i got that problem it was down to the sd card not being formatted correctly or the install script not being read.

using a windows box i formatted the sd card into FAT
extracted the fatpart to the sd card
copied the extpart to the sd card
in the sdcard, open the scripts folder and rename "scriptcmd.install" to "scriptcmd"
plug the sdcard into the netbook and boot from there.
note that this is to install debian to the netbook, not just to boot from sd card.
hope this helps

I have done all of this and it still just stays stuck at the penguin loading screen. Can someone who has done this all the way through make a video so we can all see whats supposed to be happening?

---

### Post by mikkoj on 2010-05-02
> **dudesky1325 said:**
> I have done all of this and it still just stays stuck at the penguin loading screen. Can someone who has done this all the way through make a video so we can all see whats supposed to be happening?

So, I think you have something wrong (yeah, maybe you noticed that already...)

There are two ways of doing it:
1. Sd bootable
a) 1st partiton FAT: there should be the folder "script" (extracted from fatpart.tgz). The folder "script" must be there. 
b) 2nd partition ext2: there should all the folders extracted from extpart.tgz

2. NAND way:
Only one FAT-partion. fatpart.tgz extracted (so folder "scrpt") and the file extpart.tgz

I was very confused with this for a while. Then I had all those problems with mounting. Lucky me, I got all information needed from abrasive :)

---

### Post by moblo on 2010-05-02
> **vinceCOOK said:**
> Moblo

I was reading that you may have to partition the SD card.

There is a full detailed post in here about how to put
the Debian onto SD card....very detailed.

Vince.

Thats for live booting from an sd card. Im trying to instal to nand, in which you need 1 big fat partition.

---

### Post by dudesky1325 on 2010-05-02
> **mikkoj said:**
> So, I think you have something wrong (yeah, maybe you noticed that already...)

There are two ways of doing it:
1. Sd bootable
a) 1st partiton FAT: there should be the folder "script" (extracted from fatpart.tgz). The folder "script" must be there. 
b) 2nd partition ext2: there should all the folders extracted from extpart.tgz

2. NAND way:
Only one FAT-partion. fatpart.tgz extracted (so folder "scrpt") and the file extpart.tgz

I was very confused with this for a while. Then I had all those problems with mounting. Lucky me, I got all information needed from abrasive :)

So all the files and folders have to be in the script folder?

---

### Post by kaputnik on 2010-05-02
> **dudesky1325 said:**
> So all the files and folders have to be in the script folder?
heres another go -
i use a 2gb SD card formatted in winxp as FAT (not FAT 32)
copy and paste the WM8505 debian "extpart.tgz" file into the SDcard
copy and paste the WM8505 debian "fatpart.tgz" file into the SDcard
extract the "fatpart.tgz" file that is now on the SDcard
delete the now unnecessary "fatpart.tgz"

you should now have one folder called "script" and one file called "extpart.tgz" in the SDcard.

open up the script folder and rename the file "scriptcmd.install" to "scriptcmd".

that is all you need to do for the debian install to NAND for a WM8505. If this doesnt work then maybe its a different chipset? One way to be sure is to open the box up and see what chip its using, theres seems to be many variants out there using slightly different cpus.
cross fingers huh.

---

### Post by budgetcomputer on 2010-05-02
My installation is going fine until I get to the part where it's about to install the Linux root filesystem.  Then it says:

Attempting to mount SD card
Can't find SD card giving up
if [ ! -x /mnt/sd/extpart.tgz ]
then echo can't find extpart.tgz on SD card!
Please press enter to activate this console.

Does anyone have any suggestions?  Thanks in advance.

PS: Dudesky you said something about "extracting extpart.tgz".  You're not supposed to extract that file, you're supposed to copy it right?

---

### Post by mikkoj on 2010-05-02
> **budgetcomputer said:**
> ... Then it says:

Attempting to mount SD card
Can't find SD card giving up
if [ ! -x /mnt/sd/extpart.tgz ]
then echo can't find extpart.tgz on SD card!
Please press enter to activate this console.

Does anyone have any suggestions?  Thanks in advance.

PS: Dudesky you said something about "extracting extpart.tgz".  You're not supposed to extract that file, you're supposed to copy it right?

1. Read message **#720** in this thread.
2. PS: extpart.tgz must be 
a) **extracted **to 2nd partition (**ext2**), when running debian on SD card 
b) **copied **to 1st and only **FAT **partition, when installing to NAND.

---

### Post by dudesky1325 on 2010-05-03
> **mikkoj said:**
> 1. Read message **#720** in this thread.
2. PS: extpart.tgz must be 
a) **extracted **to 2nd partition (**ext2**), when running debian on SD card 
b) **copied **to 1st and only **FAT **partition, when installing to NAND.


OK, I'm gunna try it with having only the script folder and the expart file on the SD card. 

Now it keeps failing to get the files. Is this because it lost that one thing you guys kept talking about, what was it called? Anyways after it fails it takes me back to the "wiliam:~#" what do I do!?!?!?!?!?!?!

---

### Post by styol on 2010-05-03
> **dudesky1325 said:**
> OK, I'm gunna try it with having only the script folder and the expart file on the SD card. 

Now it keeps failing to get the files. Is this because it lost that one thing you guys kept talking about, what was it called? Anyways after it fails it takes me back to the "wiliam:~#" what do I do!?!?!?!?!?!?!

on your sd card thats formatted for FAT32 there should be:
/script
/extpart.tgz

theres a file inside the script directory named scriptcmd which is what normally would try to live boot debian off the sd card. make sure that you rename the file scriptcmd.install to scriptcmd to overwrite the live boot scriptcmd (or you can rename the original scriptcmd, but either way scriptcmd.install needs to be named scriptcmd so that it gets executed to run the install). as long as the SD card is 1 single FAT32 partition, and you have a script folder with scriptcmd.install renamed to scriptcmd and the extpart.tgz unextracted in the root of the SD like outlined above, it should erase your nand and install...

then yeah it will ask you for a login, enter root.. and then you reach a prompt like "william:~#" which means you're in. if you are perhaps confused by no graphical interface, its because this is a bare bones debian install and you need to install everything that you may want. refer to the X11 readme or simply do this:
[FONT=monospace]
[/FONT]apt-get install xserver-xorg-video-fbdev xfonts-base xinit

you also may want to place this xorg.config in /etc/X11/xorg.conf
[http://bur.st/~abrasive/wm8505_linux/useful/xorg.conf]("http://bur.st/%7Eabrasive/wm8505_linux/useful/xorg.conf")

after you've installed X11, you may also want to install a window manager such as fluxbox or jwm. you can do this by doing apt-get install fluxbox -- you may also want a web browser such as iceweasel - apt-get install iceweasel -- and a terminal client - apt-get install xterm -- and ssh ability - apt-get install openssh

to actually start X11 the graphical interface, go ahead and type startx and hit enter

hope this has maybe cleared some things up for those of you that may be new to linux, just like i am :)

---

### Post by ch4rlii on 2010-05-03
@Debian users:
Could someone confirm or negate soundcard functionality?
I would like to see ScummVM with sound :)

Did someone stop how long it takes to boot into a wm?

Thank you in advance!

---

### Post by kaputnik on 2010-05-03
> **ch4rlii said:**
> @Debian users:
Could someone confirm or negate soundcard functionality?
I would like to see ScummVM with sound :)

Did someone stop how long it takes to boot into a wm?

Thank you in advance!

just under a minute to boot into fluxbox

---

### Post by su8z3ro on 2010-05-03
i have been trying to get this to install to the nand and after reboot it just sits there with the penguin and a progress bar i would like to try running it from a 2gb sd but when i put the ext2 partition on the card and format it it is not writable even after making it the active partition. so i guess my question is how do you gain access to the second partition on the sd to save the extpart file to it? i would appreciate any help anyone could offer.

su8z3ro

Iam using the latest version of kubuntu and making the partition with gparted.

---

### Post by dudesky1325 on 2010-05-03
> **styol said:**
> on your sd card thats formatted for FAT32 there should be:
/script
/extpart.tgz

theres a file inside the script directory named scriptcmd which is what normally would try to live boot debian off the sd card. make sure that you rename the file scriptcmd.install to scriptcmd to overwrite the live boot scriptcmd (or you can rename the original scriptcmd, but either way scriptcmd.install needs to be named scriptcmd so that it gets executed to run the install). as long as the SD card is 1 single FAT32 partition, and you have a script folder with scriptcmd.install renamed to scriptcmd and the extpart.tgz unextracted in the root of the SD like outlined above, it should erase your nand and install...

then yeah it will ask you for a login, enter root.. and then you reach a prompt like "william:~#" which means you're in. if you are perhaps confused by no graphical interface, its because this is a bare bones debian install and you need to install everything that you may want. refer to the X11 readme or simply do this:
[FONT=monospace]
[/FONT]apt-get install xserver-xorg-video-fbdev xfonts-base xinit

you also may want to place this xorg.config in /etc/X11/xorg.conf
[http://bur.st/~abrasive/wm8505_linux/useful/xorg.conf]("http://bur.st/%7Eabrasive/wm8505_linux/useful/xorg.conf")

after you've installed X11, you may also want to install a window manager such as fluxbox or jwm. you can do this by doing apt-get install fluxbox -- you may also want a web browser such as iceweasel - apt-get install iceweasel -- and a terminal client - apt-get install xterm -- and ssh ability - apt-get install openssh

to actually start X11 the graphical interface, go ahead and type startx and hit enter

hope this has maybe cleared some things up for those of you that may be new to linux, just like i am :)

OK I will be sure to do this. and when I enter startx, I wont have to input all those other commands? It will start up from the desktop?
And how do you put other programs on it?

---

### Post by styol on 2010-05-03
> **dudesky1325 said:**
> OK I will be sure to do this. and when I enter startx, I wont have to input all those other commands? It will start up from the desktop?
And how do you put other programs on it?

well, those commands are basically installing things which is a one time thing. it requires internet connectivity as it downloads and installs stuff. 

startx just gets you into a basic GUI to do other stuff. we will be publishing more information and pre-setup distributions that for instance automatically boot directly into a graphical interface for those that would not prefer the command line experience.

but yeah the easiest way to install new stuff is by using apt-get -- i believe there is also a somewhat graphical interface available called Aptitude Package Manager in administration somewhere i believe. one thing to note is for now need to avoid installing any items that have "udev" as a dependency. check to see what new packages will be installed when you goto install something new and make sure udev's not in there.

honestly for now the probably most user friendly install is probably android if you're not familiar with linux, although the currently available package manager for android didnt really seem to work for me... perhaps i just wasnt able to figure it out

---

### Post by dudesky1325 on 2010-05-03
Alright homies, I tried everything everybody said but it keeps failing to get the files required for set up of the stuff I enter! Do I need to have the SD card when I input the commands?

---

### Post by budgetcomputer on 2010-05-04
> **mikkoj said:**
> 1. Read message **#720** in this thread.
2. PS: extpart.tgz must be 
a) **extracted **to 2nd partition (**ext2**), when running debian on SD card 
b) **copied **to 1st and only **FAT **partition, when installing to NAND.
 
Thanks Mikkoj.  That did the trick although I get some "block xxxxx is bad" messages but maybe that's normal?
 
I followed the instructions to install X11 which seemed to go well but typing startx doesn't do anything.  Is there a directory I need to change to?
 
Thanks in advance for any info.

---

### Post by moblo on 2010-05-05
i have used the solution posted by mikkoj and it appears the  installation problem is now solved. Then, when I boot up everything is  fine. I connect online by using

"ifconfig eth0 auto"
"dhclient  eth0"

Which seems to get me connected. I then type in 

"apt-get  install xserver-xorg-video-fbdev xfonts-base xinit"

Which shows  up loads on lines of text, and then says would you like to continu [Y/n]  to which I type Y and enter.
It then says:

0% [Connecting to  ftp.au.debian.org]

and then keeps starting a new line with  something along the lines of:

Err [http://ftp.au.debian.org](http://ftp.au.debian.org)  stable/main libhal1 0.5.11-8
   Temporary failure resolving  'ftp.au.debian.org'

where the part after stable/main keeps  changing. I have no idea what this means. I am still letting it run and  it just keeps trying to connect then comes up with another error line. I  am not linux savvy, so am not too sure what it means. Am I not  connected online? Or is it a problem retrieving packages? Or maybe a  problem with my debian installation? Any help would be greatly  appreciated.
Many Thanks

EDIT:

So It just finished and  it has a looooooong list of 

"Failed to fetch [http://.](http://.)...     Temporary failure resolving 'ftp.au.debian.org'

and then at the  end it has

"E: Unable to fetch some archives, maybe run apt-get  update or try with --fix-missing?"

and back to "william:~#. I  have no clue what is wrong.

---

### Post by celem on 2010-05-05
.

---

### Post by drewmat7 on 2010-05-05
These Via Cpu netbooks are now on ebay with android this is one us seller with a video
[http://cgi.ebay.com/7-Inch-Netbook-Android-OS-WiFI-/250613070369](http://cgi.ebay.com/7-Inch-Netbook-Android-OS-WiFI-/250613070369)

---

### Post by drewmat7 on 2010-05-05
Try this in google and you will see some Debin guys working with a Arm 11 8.9 laptop
 Chitech CT-PC89E Also a US seller is testing a 8.9 with rdc CPU (X86)WITH EASLYPEASLY and other distros,They say it will be under 200.00 they will have a vid soon..they do have on on the android netbook
[http://www.youtube.com/watch?v=XlGKjjgc54s](http://www.youtube.com/watch?v=XlGKjjgc54s)

---

### Post by dudesky1325 on 2010-05-05
I am having the same problem as moblo. Is it because I need to extract the files from expart and that other zipped file in the script folder and put them all in the script folder? And when I do this does the SD card have to be in the netbook when I try and install all these programs?

I think it will work so I'm going to try, unless someone know what I'm doing wrong and has an answer for me.

---

### Post by yoshiki2 on 2010-05-05
mm if i instal ubuntu linux in one of these machines or buy the cherrypal's africa with ubuntu,... will it be able to play flash? run programs?

---

### Post by Knightwalker on 2010-05-06
> **moblo said:**
> i have used the solution posted by mikkoj and it appears the  installation problem is now solved. Then, when I boot up everything is  fine. I connect online by using

"ifconfig eth0 auto"
"dhclient  eth0"

Which seems to get me connected. I then type in 

"apt-get  install xserver-xorg-video-fbdev xfonts-base xinit"

Which shows  up loads on lines of text, and then says would you like to continu [Y/n]  to which I type Y and enter.
It then says:

0% [Connecting to  ftp.au.debian.org]

and then keeps starting a new line with  something along the lines of:

Err [http://ftp.au.debian.org](http://ftp.au.debian.org)  stable/main libhal1 0.5.11-8
   Temporary failure resolving  'ftp.au.debian.org'

where the part after stable/main keeps  changing. I have no idea what this means. I am still letting it run and  it just keeps trying to connect then comes up with another error line. I  am not linux savvy, so am not too sure what it means. Am I not  connected online? Or is it a problem retrieving packages? Or maybe a  problem with my debian installation? Any help would be greatly  appreciated.
Many Thanks

EDIT:

So It just finished and  it has a looooooong list of 

"Failed to fetch [http://.](http://.)...     Temporary failure resolving 'ftp.au.debian.org'

and then at the  end it has

"E: Unable to fetch some archives, maybe run apt-get  update or try with --fix-missing?"

and back to "william:~#. I  have no clue what is wrong.

That means you messed up your internal flash memory (2g one).

There is two ways to solve this problem.

Hard and easy way.

Hard way is unplug battery from your netbook and by using tweezer or paper clip, reset your flash memory. (I don't recommend this one)

Easy way is download different OS file such as android or windows CE (not another debian X11 start up)to erase whole operation system and then reinstall debian X11.

---

### Post by Knightwalker on 2010-05-06
> **yoshiki2 said:**
> mm if i instal ubuntu linux in one of these machines or buy the cherrypal's africa with ubuntu,... will it be able to play flash? run programs?

I don't think you can't even install ubuntu. (internally) I tried gnome and due to capacity of program, it won't install. I tried KDE and stopped at first screen.

---

### Post by Knightwalker on 2010-05-06
> **budgetcomputer said:**
> Thanks Mikkoj.  That did the trick although I get some "block xxxxx is bad" messages but maybe that's normal?
 
I followed the instructions to install X11 which seemed to go well but typing startx doesn't do anything.  Is there a directory I need to change to?
 
Thanks in advance for any info.

Before you type 'startx', you have to add something such as LXDE, xfce, IceWm, fluxbox, etc

So after you installed xwindows, type 'apt-get install something'

Something can be 'gnome', 'gnome-core', ' LXDE' or 'xfce'

Type something like 'apt-get install LXDE' then type startX.

That should work.

---

### Post by dudesky1325 on 2010-05-06
Is it easy to install the android thing on these netbooks? And if it is will someone please tell me how to do it?

---

### Post by moblo on 2010-05-06
> **Knightwalker said:**
> That means you messed up your internal flash memory (2g one).

There is two ways to solve this problem.

Hard and easy way.

Hard way is unplug battery from your netbook and by using tweezer or paper clip, reset your flash memory. (I don't recommend this one)

Easy way is download different OS file such as android or windows CE (not another debian X11 start up)to erase whole operation system and then reinstall debian X11.

Alright, I have managed to solve my problems. The acttual problem was that I was trying to connect online through my laptop via bridge. I connected directely to my router then typed:
ifconfig eth0 192.168.0.1
dhclient eth0
and that did the trick. I downloaded x11 and lxde and it works perfectely now. I didnt have to add driver fbdev to the device section of xorg.conf; it was already there. I believed it has been fixed. I have also installed iceweasel, which is a nice mobile browser. Very similar in look and feel to firefox, but it is a mobile browser. 
Heres what I need to do now, and Im gonna need help. The first thing I want is a wifi manager. i want to be able to use my machine at uni so need a wifi manager to deal with connections. Can anyone suggest any programs? I also want a media player to play music and movies. 
Where do I look for a list of all the programs that I can install through apt-get? I would like to look through myself and try out different things.

---

### Post by yoshiki2 on 2010-05-06
> **Knightwalker said:**
> I don't think you can't even install ubuntu. (internally) I tried gnome and due to capacity of program, it won't install. I tried KDE and stopped at first screen.
Cherypal is selling withem with ubuntu preinstalled.. or debian.. the pointis that if it can runs flash,..
[http://www.cherrypal.com/secure/product_info.php?products_id=9](http://www.cherrypal.com/secure/product_info.php?products_id=9)
The Cherrypal Africa was designed with developing countries in mind. The Cherrypal Africa is offered with following minimum technical specifications: 400 MHz processor, 128 MB DDR / 2 GB NAND-flash and runs Linux (Ubuntu, or Debian, or Green Maraschino). Here are some more basics: Screen: 7 inch high-resolution TFT .(800 x 480 pixels) LAN:10/100M Ethernet Access WIFI: IEEE 802.11 b/g Ethernet RJ-45 Keyboard: QWERTY 86 keys Mouse&Touch pad:build-in touch panel, set two shortcut key,and support usb port mouse USB Port: USB 2.0 x 1 (aid external memory) USB 1.1 x 2 (aid keyboard & mouse only) External Memory : SD card , U-Disk , USB-HDD Card port: SD / MMC card slot (8GB) Battery: 7.4 V 1800Mha built in Lithium battery 1800MAH Last time:4 HRS Sound effect:build-in realtek sound effect chipset, Built in 2 x 0.5W Built in speaker 1 x microphone Weight:1.2kg Size: 213.5 x 141.8 x 30.8 m

---

### Post by wicknix on 2010-05-06
Beware. The cherrypal doesn't exist. They take your money and send you nothing. 
 
[http://www.mobileread.com/forums/showthread.php?t=69889](http://www.mobileread.com/forums/showthread.php?t=69889)
 
Also type in google "cherrypal scam" for pages and pages of the scam.

---

### Post by dudesky1325 on 2010-05-06
> **moblo said:**
> Alright, I have managed to solve my problems. The acttual problem was that I was trying to connect online through my laptop via bridge. I connected directely to my router then typed:
ifconfig eth0 192.168.0.1
dhclient eth0
and that did the trick. I downloaded x11 and lxde and it works perfectely now. I didnt have to add driver fbdev to the device section of xorg.conf; it was already there. I believed it has been fixed. I have also installed iceweasel, which is a nice mobile browser. Very similar in look and feel to firefox, but it is a mobile browser. 
Heres what I need to do now, and Im gonna need help. The first thing I want is a wifi manager. i want to be able to use my machine at uni so need a wifi manager to deal with connections. Can anyone suggest any programs? I also want a media player to play music and movies. 
Where do I look for a list of all the programs that I can install through apt-get? I would like to look through myself and try out different things.

How do I do this through wifi?

---

### Post by Knightwalker on 2010-05-08
> **yoshiki2 said:**
> Cherypal is selling withem with ubuntu preinstalled.. or debian.. the pointis that if it can runs flash,..
[http://www.cherrypal.com/secure/product_info.php?products_id=9](http://www.cherrypal.com/secure/product_info.php?products_id=9)
The Cherrypal Africa was designed with developing countries in mind. The Cherrypal Africa is offered with following minimum technical specifications: 400 MHz processor, 128 MB DDR / 2 GB NAND-flash and runs Linux (Ubuntu, or Debian, or Green Maraschino). Here are some more basics: Screen: 7 inch high-resolution TFT .(800 x 480 pixels) LAN:10/100M Ethernet Access WIFI: IEEE 802.11 b/g Ethernet RJ-45 Keyboard: QWERTY 86 keys Mouse&Touch pad:build-in touch panel, set two shortcut key,and support usb port mouse USB Port: USB 2.0 x 1 (aid external memory) USB 1.1 x 2 (aid keyboard & mouse only) External Memory : SD card , U-Disk , USB-HDD Card port: SD / MMC card slot (8GB) Battery: 7.4 V 1800Mha built in Lithium battery 1800MAH Last time:4 HRS Sound effect:build-in realtek sound effect chipset, Built in 2 x 0.5W Built in speaker 1 x microphone Weight:1.2kg Size: 213.5 x 141.8 x 30.8 m

Well, I doubt it~~

OK, size of debian  X11 is (not unextracted package) about 200mb, xwinodows is about 300mb,  and gnome is 1.8gb (full version of unextracted package is 1.2gb). 
200+300+1800=2300mb or 2.3gb. It's simple math.. It doesn't fit..

They may optimized packages, but Cherrypal Africa is widely known as fraud.
Fraud can tell anything to steal your money.

---

### Post by dudesky1325 on 2010-05-10
Guys it's still not letting me install anything on it. It keeps doing the ERROR and FAILED stuff. It's very frustrating!!! What do I do?!?!?!?!

---

### Post by oleink on 2010-05-10
> **dudesky1325 said:**
> Is it easy to install the android thing on these netbooks? And if it is will someone please tell me how to do it?

if you google it you can learn all you need to know.  Just type on goolge search "android on netbook"

---

### Post by dudesky1325 on 2010-05-10
> **oleink said:**
> if you google it you can learn all you need to know.  Just type on goolge search "android on netbook"

Would this be better than the debian LXDE? or just the same?

---

### Post by oleink on 2010-05-10
> **dudesky1325 said:**
> Would this be better than the debian LXDE? or just the same?

Thats a good question.  I'd say it'd be better than debian for a netbook.  LXDE and XFCE are small but depending on the netbook.  btw if you didn't say netbook im sorry I missed that cause i came to this post late.  But could you post the specs.  Depending on the age of the hardware you may rather have lxde or xfce

---

### Post by oleink on 2010-05-10
oh ok sorry.  I just saw its a cherrypal africa.  I'd suggest android

---

### Post by dudesky1325 on 2010-05-10
OK. is it possible to install it from an SD?

---

### Post by ch4rlii on 2010-05-11
> **dudesky1325 said:**
> OK. is it possible to install it from an SD?

Yes. All the unformation you need is in THIS thread! RTFM

---

### Post by dudesky1325 on 2010-05-11
ok thanks guys!!!!!

---

### Post by PrFaas on 2010-05-12
@ch4rlii: and with 90 pages of 'tfm' to 'read', you can be quite sure to have sent someone on some chase :)

---

### Post by dudesky1325 on 2010-05-12
I would like to install debian lxde on mine though... can anyone help? Please?

---

### Post by FrankX.190875 on 2010-05-12
Hi All,

Just a quick post... Has anyone considered the MAEMO project as possible GUI or even APP repos'?

Just a thought as there's even a browser, "microb-browser" which can do flash 9 etc. Its built for ARM and is a DEB backbone. Runs on the Nokia N900 (etc).

I only mention it as I was looking to get one of these phones and was looking through the maemo project pages for more info.

Makes some sense if folks are happy to run android may as well look at other ARM mobile os options?

I've got one of these mini netbooks and look forward to getting linux running on it, got it for my lil girls B'day (coming up soon) for her to play on flash sites etc.

Tried the DEB install mentioned above but just got the progress line for AAAAGGGEEES, think it was down to me not renaming the scriptcmd.install file to scriptcmd (duh!).

Anyway, hope this is useful. Maemo project site is [http://maemo.org/]("http://maemo.org/"):)

FX

---

### Post by oleink on 2010-05-12
> **dudesky1325 said:**
> I would like to install debian lxde on mine though... can anyone help? Please?

what exact distro?

---

### Post by styol on 2010-05-13
The original Windows CE 6 operating system installer is now available over at the new Bento Linux site where most of the information from this thread is being documented at, and where new information is also being posted.

Windows CE 6 OS download:
[http://bento-linux.org/wiki/vt8505/wm8505/windows-ce](http://bento-linux.org/wiki/vt8505/wm8505/windows-ce)

Android 1.5 OS download is also now available at:
[http://bento-linux.org/wiki/vt8505/wm8505/android](http://bento-linux.org/wiki/vt8505/wm8505/android)

Also, a lengthy 40 minute disassembly video has been posted at:
[http://bento-linux.org/disassembly-video](http://bento-linux.org/disassembly-video)

---

### Post by pixfix on 2010-05-13
hello
I have this problem. I have uploaded into the netbook new firmware from the site [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm)
and now he can not even turn on. Before going but go but had some problems but I do not. Before I displayed this during boot:
Version 1.90
Hardware Version 3.0
CPU: ARM 926EJ-S 248 MHz
Release: SV122
RAM: 128 M
Video decoder: 1
Now, after I just flashnutí probliknnou diodes on Num Lock, Caps Lock and Scroll Lock, and then nothing happens next:(. I think it may be corrupted boot loader. If someone had the boot loader so I would be grateful for it. Thank you for your advice and the boot loader ... I'm here writing nonsense, so I translated via Google:)

---

### Post by styol on 2010-05-13
> **pixfix said:**
> hello
I have this problem. I have uploaded into the netbook new firmware from the site [http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm)
and now he can not even turn on. Before going but go but had some problems but I do not. Before I displayed this during boot:
Version 1.90
Hardware Version 3.0
CPU: ARM 926EJ-S 248 MHz
Release: SV122
RAM: 128 M
Video decoder: 1
Now, after I just flashnutí probliknnou diodes on Num Lock, Caps Lock and Scroll Lock, and then nothing happens next:(. I think it may be corrupted boot loader. If someone had the boot loader so I would be grateful for it. Thank you for your advice and the boot loader ... I'm here writing nonsense, so I translated via Google:)

sounds like the Anyka AK7802 -- [http://mininetbooks.your-board.com/](http://mininetbooks.your-board.com/)

---

### Post by pixfix on 2010-05-14
Thank you styol :)

---

### Post by dudesky1325 on 2010-05-14
> **oleink said:**
> what exact distro?

Its the debian lenny lxde mentioned earlier in this thread. I think it will only install the programs if I'm connected to ethernet, unless I did something wrong

---

### Post by oleink on 2010-05-15
> **dudesky1325 said:**
> Its the debian lenny lxde mentioned earlier in this thread. I think it will only install the programs if I'm connected to ethernet, unless I did something wrong

Ok cause if you go with puppy or dsl you'll probably be able to get it rather easily

---

### Post by Fusin on 2010-05-15
Hi, introducing myself ;) My nick is Fusin, and I'm tuxing since SLS 0.99 pl6. Long ago. 
My actual goals are Vektor Linux on an old IBM ThinkPad 570E and I try to install Android on an 7" Anika NetBook with WinCE5 which was a false delivery from China. (I ordered a German one, and they sended a french one). In case of these little netbooks, I have 'strange' feelings. The WinCE 'should' be like an PDA (similar to Jornada 720) but it isn't. Also it is not realy a Subnote like they often state. I buyed a second one, this time with WinCE 6 (US keayboard layout) which is useable as mini subnote. I probably let WinCE6 on that one.
So now back to Android :)
I downloaded the file mentioned in a post here earlier. Copied to an SD, and called the 'bios' for update..
Hint: the password is not always ZTK, in case of a french keyboard (like mine) you must use wtk. It's the position of the char that is important, not the printing on the keys ;) Also i used no-caps. 
My problem now is: formating XIP- and Flash2 disk succeeded. Formating nand is hanging since 2 hours..
Display on screen say 'Format Nand disk starting...' and it seem frozen.
Any hint what I can do??
Thanks in advance..

---

### Post by moblo on 2010-05-16
Hi Guys, 
I am loving using Debian on my wm8505 netbook, but at the moment am only connecting  through ethernet. I have managed to use wpa_supplicant, and somehow  managed to connect to my home wifi network. What I really wanted was to  be able to use a gui to get online, for instance with wpa_gui. I need to  be able to connect to my uni wifi, which is primarily where I'll be  using this. I wanted someone to give me a step by step guide on setting  up a wifi gui that lets me connect at home and uni. I need a beginners  guide, im not that linux savvy! When I set up wpa_supplicant, I did  extensive google searching, and thats how I managed to do it, but I  could not get the wpa_gui to work. I think there was a problem with file  paths/locations. Any help would be greatly appreciated. 
Many thanks 
Moblo

---

### Post by idekitu on 2010-05-16
Hello!

i have an wm8505 netbook and i would like to know if i can put android using this:

[http://bento-linux.org/wiki/vt8505/wm8505/android](http://bento-linux.org/wiki/vt8505/wm8505/android)

I am very worried because if i want to come back to win ce 6.0, could i do it without problems or it would be very difficult to go back to win?

Thank you!

---

### Post by Nutrocker on 2010-05-17
Hello everyone! I have bought a netbook that has a **VT8500 300MHz ARM926EJ-S** processor (the one that you've been discussing about) that comes with Windows CE.

I think its corresponding site is the following one:
[http://www.arm.com/products/processors/classic/arm9/arm926.php](http://www.arm.com/products/processors/classic/arm9/arm926.php)

There it says **"The ARM926EJ-S processor features an MMU, allowing for the use of fully featured OS such as Linux, Windows CE, and Symbian."**

I have read several pages of this thread but I don't know about programming so it can get really difficult for me, have you been able to install any Linux distro in this netbook? If so, it would be great if you tell me which one and how can I install it.

Thanks in advance!
Good bye :)


*PD: Excuse me for my English, I'm not a native speaker.*

---

### Post by OwenHell on 2010-05-17
Has any one got there hands on the &quot;7&quot; Google Android WIFI Touch Screen Notebook Netbook&quot; ?? eBay that   it looks sweet very Google intimating Ipad I WANT ONE dose any own one??

---

### Post by TheNewbieGeek on 2010-05-17
Hello I would like to do this to my new netbook that I bought off of Ebay it a arm vt8500. I do not know what most of you are talking about on this post. I am a novice and don't even know linux commands much. But do you think that folowing the advice at bento linux and a little help from the forum I could pull it off? I am a web designer only. I do not want to break my new netbook of course. When will the instructions be complete at Bento Linux? Thanks for the replies.

---

### Post by ch4rlii on 2010-05-18
> **OwenHell said:**
> Has any one got there hands on the &quot;7&quot; Google Android WIFI Touch Screen Notebook Netbook&quot; ?? eBay that   it looks sweet very Google intimating Ipad I WANT ONE dose any own one??

Hi,
you can find a very active forum about this device there:
[http://slatedroid.blitzwerks.co.uk/index.php](http://slatedroid.blitzwerks.co.uk/index.php)

---

### Post by immutable on 2010-05-18
I bought one just recently. They're probably made by the same guys who made the netbooks, Shenzhen. Still waiting for it to come but it looks to be an interesting device to fiddle with. At least Android's more user friendly than Windows CE. :P

---

### Post by SKCheng on 2010-05-18
I got one with RDC x86 CPU, 512M RAM & 8G SSD a few months ago @ Shenzhen China.  Some models come with ARM CPU in the same "standard" netbook case.  This industrial use RDC CPU is based on 486SX with 996Mhz.  I don't think it supports MMX.

To install ANY OS from USB device (include USB CDROM or SD card

>Sometimes I need to change setting at CMOS setup.  Change USB from 2.0 to 1.1.  Or it won't boot from USB.

>I've tried many Linux versions (Ubuntu, Damn Small Linux, Slack, Mandrake, Android, Puppy).  All failed.  Most even failed at boot up.  I think it needs a re-compiled kernel.
See the CPU manufacturer [www.rdc.com.tw]("http://www.rdc.com.tw")  I guess this CPU is similar to Vortex86 used in Gecko's Edubook.  Cuz it shows "Vortex CPU" on Windoze.

>Is there something like "MMX emulator"?  This toy desperately needs one or it freezes whenever any multimedia/flash comes...

---

### Post by anjers on 2010-05-18
im using my netbook, it just come in today. they`re quite small. the person i bought told me they were VT8500 with 5.0 CE and 128M. mines the pink one with black keyboard, and the settings say its CE 6.0 256M and VT8505
 
is this good or bad?

---

### Post by TheNewbieGeek on 2010-05-18
Thanks to the techs who are doing this.

Hello I have been reading this link:

[http://bento-linux.org/wiki/vt8500-easypc-linux](http://bento-linux.org/wiki/vt8500-easypc-linux)

If this is what you have to do then why is thier a disassembly video? Why do you have to disassemble it?

---

### Post by ericanilaru on 2010-05-19
> **oleink said:**
> Ok cause if you go with puppy or dsl you'll probably be able to get it rather easily

I use puppy as my main operating system:); I keep checking their forum and as far as I can tell there is still NO port of puppy for ARM architecture:(, and all mentions of these netbooks say it would be nice, but no-one's working on it.

If you do know / hear of a puppy distro that will run on these please post the link, that would be my personal ideal for these (for obvious reasons).

---

### Post by PrFaas on 2010-05-19
A little cut & paste from:

=========================================================
[http://bento-linux.org/wiki/vt8505/wm8505/android/android-kernel](http://bento-linux.org/wiki/vt8505/wm8505/android/android-kernel)
=========================================================

This has various effects. It mangles a bunch of permissions on startup, including / and /dev/null. It also prevents non-root users from using the network (compiled with CONFIG_ANDROID_PARANOID_NETWORK).

Network workaround
To allow non-root users to use the network:
First, create the aid_inet group:

-------------------------
groupadd -g 3003 aid_inet
-------------------------

You can then give permission for each user to access the network by adding them to the aid_inet group:

----------------------------
usermod -G aid_inet username
----------------------------

=========================================================

I think that is also relevant for the users of the debian-on-WM8505... That debian uses the android kernel (with debian 'userland'.

Having internet/network access *only* as root seems a bit of a backwards approach to network security to me :P

---

### Post by anjers on 2010-05-20
I was wondering if anyone could tell me how to get QQ messenger on these netbooks? The box says it comes with MSN and QQ and I see MSN on my netbook but I do not see QQ at all.

---

### Post by vinceCOOK on 2010-05-21
Hello People,

I don't know if this is any help for wm8505 chip netbooks users.

[http://www43.instantestore.net/merchant26019/pd-ocean-android-operating-system.cfm](http://www43.instantestore.net/merchant26019/pd-ocean-android-operating-system.cfm)

This web link came from the HALERON website where they sell a netbook
with the wm8505 chip.

This appears to be some kind of special OS for those wm8505 netbooks which
allows them to run both Android and a verion of Linux at the same time.

Not sure what it is saying....hope it is of interest and helpful

Did the developers here ever finish the Debian for wm8505?  Did they make the Debian
into a full fledged Linux distro with x11, proper video, proper flash web browser...proper sound and ability to support pluggable USB devices?

thanks,

Vince.

---

### Post by aetaylor47 on 2010-05-21
Here is a consolidation of some posts from here together with more new information. There is continuing development.

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php]("http://s0.blackmage.co.uk/%7Enextvolume/via_arm/index.php")

Debian Lenny is being worked on and apt-get is working via wireless and internet. Not too sure about sound but x is working. New starter so that is a limitation of my review.

---

### Post by vinceCOOK on 2010-05-21
Hello

Yes, the dual boot ANDROID fiel mentioned above does exactly what it says.

It allows wm8050 chip netbook owners to leave windows CE on the machine and then have an ADNROID icon on the windows desktop. When the icon is clicked ANDROID will boot up on the netbook.

It says that it also able to sit on a Linux desktop...however...wm8050 machines can't currently run the OCEAN LINUX that haleron website supply because it is x86 based and not ARM based.

I wondered if this dual boot tool would get around this issue...and somehow allow OCEAN LINUX to be put onto these wm8050 chip netbooks along with android.

Haleron do all this work because they sell the Swordfish smartbook with the wm8050 chip

thanks

Vince.

---

### Post by dudesky1325 on 2010-05-26
> **moblo said:**
> Hi Guys, 
I am loving using Debian on my wm8505 netbook, but at the moment am only connecting  through ethernet. I have managed to use wpa_supplicant, and somehow  managed to connect to my home wifi network. What I really wanted was to  be able to use a gui to get online, for instance with wpa_gui. I need to  be able to connect to my uni wifi, which is primarily where I'll be  using this. I wanted someone to give me a step by step guide on setting  up a wifi gui that lets me connect at home and uni. I need a beginners  guide, im not that linux savvy! When I set up wpa_supplicant, I did  extensive google searching, and thats how I managed to do it, but I  could not get the wpa_gui to work. I think there was a problem with file  paths/locations. Any help would be greatly appreciated. 
Many thanks 
Moblo

Can you post some screen shots so I know what it should look like? Thanks!

I ran into a problem guys, I installed lxde on mine, but now i don't know how to install a graphic interface. I tried "apt-get install..." and it didn't work. Please help.

---

### Post by moblo on 2010-05-27
> **dudesky1325 said:**
> Can you post some screen shots so I know what it should look like? Thanks!

I ran into a problem guys, I installed lxde on mine, but now i don't know how to install a graphic interface. I tried "apt-get install..." and it didn't work. Please help.

lxde is a gui. if you type startx, it should start lxde. the steps in installing the debian, is instal the os, then x11 then a gui, in your case lxde. then once yo start up your laptop andlog in, you type startx. hope that helps.

---

### Post by dudesky1325 on 2010-05-27
> **moblo said:**
> lxde is a gui. if you type startx, it should start lxde. the steps in installing the debian, is instal the os, then x11 then a gui, in your case lxde. then once yo start up your laptop andlog in, you type startx. hope that helps.

OK, I will try it. I don't have to be connected to ethernet to do this right?

---

### Post by moblo on 2010-05-27
> **dudesky1325 said:**
> OK, I will try it. I don't have to be connected to ethernet to do this right?

Once you have x11 and lxde installed, you dont need ethernet. You only need to have the online connection when you are downloading all the software.

---

### Post by dudesky1325 on 2010-05-28
> **moblo said:**
> Once you have x11 and lxde installed, you dont need ethernet. You only need to have the online connection when you are downloading all the software.

I tried and it said something like "bash startx" or "package not found". I don't think I downloaded x11, how was I supposed to do that? I got lxde on it, but I don't think I got x11. Can I get instructions on how to do that? Thanks!

---

### Post by moblo on 2010-05-28
> **dudesky1325 said:**
> I tried and it said something like "bash startx" or "package not found". I don't think I downloaded x11, how was I supposed to do that? I got lxde on it, but I don't think I got x11. Can I get instructions on how to do that? Thanks!

Once ur connected by ethernet online type:
apt-get install xserver-xorg-video-fbdev xfonts-base xinit

that will install x11. then try startx again.

---

### Post by sartrejp on 2010-05-30
Have you seen this? I think this can help [http://www.kwikbyte.com/KB9202.html]("http://www.kwikbyte.com/KB9202.html")
These people are selling a notebook the same but with 64mb ram and a version of Linux, in that link there is some documentation.
I bought one similar but I'm hoping it arrives, comes with WinCE 5.0 so I will be careful to bring the processor to see if I can install any version of linux.
Suerte!

---

### Post by PrFaas on 2010-05-31
@sartrejp: a different processor :) 'our' problem is the VT8500/WM8505 SoC, with little -if any- documentation, so we have no kernel in source form (yet..).

---

### Post by clickkk on 2010-05-31
Hi guys, :)
I have a question about those little 7 inch pc's. Can they run apache server?

---

### Post by dudesky1325 on 2010-06-01
> **moblo said:**
> Once ur connected by ethernet online type:
apt-get install xserver-xorg-video-fbdev xfonts-base xinit

that will install x11. then try startx again.

I did this and it said "err" and "cannot reach server" or something. What do I do!?!?!?!?!?!?!?

---

### Post by vinceCOOK on 2010-06-02
Hello,

Is the Debian for (wm8050 chip) able to be added to?

I looked a Debian lenny and it appears to have hundreds
of tools packaged for ARM chips.

Say you wanted to install an art tool, would it be?

apt get gimp?

is it as simple as this?

thanks

Vince.

---

### Post by dudesky1325 on 2010-06-02
> **vinceCOOK said:**
> Hello,

Is the Debian for (wm8050 chip) able to be added to?

I looked a Debian lenny and it appears to have hundreds
of tools packaged for ARM chips.

Say you wanted to install an art tool, would it be?

apt get gimp?

is it as simple as this?

thanks

Vince.

I just tried that and it didnt work

---

### Post by DonutFUN on 2010-06-02
I'm having trouble with this thing lately, the mouse decides it wont work, i have it plugged in and it'll stop working, and it won't work no matter which port I have it plugged into, but if i plug something else into that port it still works just fine.

any ideas?
its the vt8500 by the way
and it used to work just fine, and I have formatted in since it started and nothing...

---

### Post by dudesky1325 on 2010-06-02
> **moblo said:**
> i have used the solution posted by mikkoj and it appears the  installation problem is now solved. Then, when I boot up everything is  fine. I connect online by using

"ifconfig eth0 auto"
"dhclient  eth0"

Which seems to get me connected. I then type in 

"apt-get  install xserver-xorg-video-fbdev xfonts-base xinit"

Which shows  up loads on lines of text, and then says would you like to continu [Y/n]  to which I type Y and enter.
It then says:

0% [Connecting to  ftp.au.debian.org]

and then keeps starting a new line with  something along the lines of:

Err [http://ftp.au.debian.org](http://ftp.au.debian.org)  stable/main libhal1 0.5.11-8
   Temporary failure resolving  'ftp.au.debian.org'

where the part after stable/main keeps  changing. I have no idea what this means. I am still letting it run and  it just keeps trying to connect then comes up with another error line. I  am not linux savvy, so am not too sure what it means. Am I not  connected online? Or is it a problem retrieving packages? Or maybe a  problem with my debian installation? Any help would be greatly  appreciated.
Many Thanks

EDIT:

So It just finished and  it has a looooooong list of 

"Failed to fetch [http://.](http://.)...     Temporary failure resolving 'ftp.au.debian.org'

and then at the  end it has

"E: Unable to fetch some archives, maybe run apt-get  update or try with --fix-missing?"

and back to "william:~#. I  have no clue what is wrong.

Can someone please answer this because I am having the same problem. I have no idea what I did wrong or how to fix it. Unless someone can help me I am going to try and install Android on mine. Can someone please give me a SIMPLE set of instructions on how to do this? Thank whoever responds to this

---

### Post by vinceCOOK on 2010-06-03
Hello

[http://cgi.ebay.com/Android-7-WiFi-mini-laptop-Netbook-ul-thin-450MHz-2GB-/110537856068?cmd=ViewItem&pt=UK_Computing_Laptops_EH&hash=item19bc91d444](http://cgi.ebay.com/Android-7-WiFi-mini-laptop-Netbook-ul-thin-450MHz-2GB-/110537856068?cmd=ViewItem&pt=UK_Computing_Laptops_EH&hash=item19bc91d444)

ebay is selling netbooks with the VT8500 chip and ADNROID installed on them.

Presumanly, if you could get hold of this Kernel then
the Debian(wm8050) on this forum would work on these vt8500 netbooks?

thanks

Vince.

---

### Post by TheNewbieGeek on 2010-06-03
Hi guys this is kindof sounds like a rhetorical question but I really like linux and want to install it on my netbook that I bought on ebay. I have the wm8505. In the instructions at the website created for this thread it said that I can install windows ce back on my netbook if debian doesn't work properly. In practice are people having good results with installing debian? I love linux but if it's gonna ruin my new netbook forget it and i want to put windows ce back on again. thanks for the replies.

---

### Post by ryannining on 2010-06-04
Hi guys, i just buy a mini notebook 7" from china. Right now i have change the OS from WinCe to Android.

But actually, i cant revent the OS back to WinCE 6.0, when i put the Vt8505 script on SD-Card the installation process stopped with chinesse text. I guess it fail to copy the system files to the devices. After reboot, i can enter the Win Ce, but lots of icon are blank. And i check \windows\ lots of files are missing.

Now i am good with android, but the Internal Flash Disk is not recognized.

Actually its all start because i cant install Mini Opera on Windows CE. It always say Invalid Windows Ce Setup file. And all my CAB from my pocket pc cannot installed too.

---

### Post by My User Name on 2010-06-06
Hello,
 
I am trying to get a serial port on one of these machines. Sorry to post this here, but I have Googled for days looking for a method and this thread has come the closest to talking about a serial port on one of these machines.
 
I have a test instrument device/application that requires a PC serial port, and these mini netbooks would be perfect for my device. I really would like to get a serial port working on these mini net books.
 
I have tried a Prolific brand usb-serial converter cable, but have not been able to install the WinCE drivers. I have tried installing manually and making the entries in the registration file using RegEdit, but I doubt I have made all the correct entries needed. 
 
I have noticed that clicking on the properties of the active sync network under network connections, that there is a listing for com6, and a way to edit the parameters, baud, bit count, stop bits, etc... but there are also network settings and modem settings in the same dialog window. I am wondering if it is possible to make a standard serial port form these settings.
 
Any help, links, anything would be appreciated. Thanks

---

### Post by rpm123 on 2010-06-07
You should try this driver to get RS232 port working. [http://www.yetanotherhomepage.com/j7xx/j7xx.html?/j7xx/software/util/usbdriver.html](http://www.yetanotherhomepage.com/j7xx/j7xx.html?/j7xx/software/util/usbdriver.html)
Instructions are included at web page. Works perfectly in my 7" computer and Prolific USB to RS232 adapter.
Remember to use USB port located on the backside of the computer.

---

### Post by My User Name on 2010-06-07
Thank you for that link. I am more encouraged to know it has been done. Do you have the Chinese generic mini ($100.00 or less) or a name brand?
 
The problem I am having is that I do not get the driver install dialog box when I plug in a USB/serial adapter. So I have no automated driver installation. 
 
Is there a WinCE application that does this that I may be missing, or perhaps my mini is defective. Does anyone else get no responce from WinCE win an unknown USB device is plugged into their mini?

---

### Post by rpm123 on 2010-06-08
I have 7" unbranded Chinese mini laptop with WinCe 5. Price was less than 100$ when I ordered it from China on Janyary 2010.
Ok, it was asking the name of the driver, but after I fixed register values to load driver from \Flash2\ drive it does not ask anything anymore. As I said it works perfectly as COM2:. You might have some kind of hardware issue with your laptop.

---

### Post by PrFaas on 2010-06-09
ref building a serial port:, around page 18 of this 'thread', there is a description of a serial port i built for this device, using only a 3.3 Volts <-> RS232 buffer.

---

### Post by alchark on 2010-06-11
Hi all,

I've just registered to leave a note about my effort to port a recent Linux kernel (v2.6.34 currently) to VT8500. The code is available at Gitorious via [http://gitorious.org/linux-on-via-vt8500/vt8500-kernel]("http://gitorious.org/linux-on-via-vt8500/vt8500-kernel"). It does not use any binary blobs or other VIA's obscure stuff, but is rather written from ground up, trying to follow closely how other kernel code functions.

Currently I have the basic architecture support code working and a serial console initializing. Use "earlyprintk console=ttyS0,115200n8" as boot parameters to see kernel messages on UART0 (interrupts and timers are also functional, to my experience). I would appreciate testing and debugging this extensively, so as to ensure that we have really working and clean code that can be merged upstream.

Also, if anybody has experience with kernel programming, please review the code and let me know if I am missing anything :)

After making sure that existing code is indeed working correctly, the plans are (decreasing priority):
 - Framebuffer driver (display support)
 - USB driver
 - SD/MMC driver
 - Integrated keyboard/touchpad support
 - Integrated AC97 sound support
 - Onboard NAND and SPI flash support
 - Onboard RTC support
 - Onboard Ethernet support (note that WiFi is a USB module)
 - Various optimizations, DMA support etc.

Also, as soon as we get the kernel to at least boot into a ramdisk with a serial console, I would like to contact upstream kernel developers for their feedback (in order to merge the code there).

---

### Post by morefya on 2010-06-16
Hey guys. Just want to say congratulations for all the work that you've accomplished. All the countless hours you've put into this looks like it has really payed off. 

I had a question. Is there a cab installer for linux that will load up on these netbooks? I don't have access to the BIOS so I can't do the SD installs.

Thanks in advance to anybody that can help and thanks again for all the hard work everybody has done.

Edit: Okay so I found a couple cab files for different builds of linux that seem to be okay but I keep getting a "unspecified mtype" error when I try to execute the exe file. Does anybody know how to adjust this. I googled it but the only fix I could find was to set it in a corresponding txt file (which I can't seem to remember the name of) that I don't seem to have. Any ideas?

---

### Post by dudesky1325 on 2010-06-21
Can anyone help me please?
I tried to install debian on my little machine but it did not work I want to put winCE back on it but I am having trouble doing so. does anybody have the winCE I can download? please?

---

### Post by styol on 2010-06-22
> **dudesky1325 said:**
> Can anyone help me please?
I tried to install debian on my little machine but it did not work I want to put winCE back on it but I am having trouble doing so. does anybody have the winCE I can download? please?

[http://bento-linux.org/wiki/vt8505/wm8505/windows-ce](http://bento-linux.org/wiki/vt8505/wm8505/windows-ce)

---

### Post by clickkk on 2010-06-23
Hello,
I think i found good web page which sells same laptops, but with better processor (VIA 8505, 533mhz), more RAMs (256 mb). Also they put better battery (7.4 V 2100Mha built in Lithium, 4hrs instead of 3hrs).

[http://www.cherrypal.com/secure/product_info.php?products_id=13](http://www.cherrypal.com/secure/product_info.php?products_id=13)

Am I correct?

---

### Post by Cemper on 2010-06-26
Hi @ all,
[LEFT]I am new to these WM8505-based netbook stuff, but as I read through parts of this thread, it appeared to me as you were missing documentation of the WM8505. However, I casually stumbled upon [U][this link]("http://tails92.sepwich.com/files/easypc/datasheets/DS_WM8505_071.pdf.gz"). 
[/U]It is the data sheet of the WM8505 that you have been searching for before the official Android kernel for these computers was released. As I didn't read through the whole thread, I don't know for sure whether or whether not you can still make use of it. If not, feel free to just quietly ignore this post ;)

Oh, and sorry for my English, I'm not a native speaker.

Greets[/LEFT]

---

### Post by dudesky1325 on 2010-06-29
Hi guys, its me again. I have finally got something to work on my machine, Android! I was just wondering of it is possible to upgrade the firmware over WiFi? So I'm asking of I can upgrade it like you're able to upgrade the phones. Does anybody know if this will work? And is it also possible to get apps via the app store and if so, how do I get to the app store? Thanks for all the help guys!

---

### Post by bigredlevy on 2010-06-30
> **dudesky1325 said:**
> Hi guys, its me again. I have finally got something to work on my machine, Android!


did you get the touch pad to work properly? It's currently acting as a touch screen would, which isn't handy.
usb mouse works just fine, so the driver is clearly in there somewhere.

---

### Post by dingodong on 2010-06-30
> **dudesky1325 said:**
> Hi guys, its me again. I have finally got something to work on my machine, Android! I was just wondering of it is possible to upgrade the firmware over WiFi? So I'm asking of I can upgrade it like you're able to upgrade the phones. Does anybody know if this will work? And is it also possible to get apps via the app store and if so, how do I get to the app store? Thanks for all the help guys!


How did you get it to run on your netbook ? Is it vt8500 based or wm8505 ?

Thanks

---

### Post by bigredlevy on 2010-07-01
> **dingodong said:**
> How did you get it to run on your netbook ? Is it vt8500 based or wm8505 ?

This is for a 505:
[http://orca.st.usm.edu/%7Ecberry2/android-ARM-8505-Smartbook.zip]("http://orca.st.usm.edu/%7Ecberry2/android-ARM-8505-Smartbook.zip")

copy the "script" folder to a FAT32 formatted SD card.
put the sd card in. boot. follow onscreen prompts.

I've encountered a few problems so far. There is no browser to explore files on the sd card, and the mouse touch pad acts as a touch screen would. usb mouse works fine.

the system is still far superior to WIN-CE.

---

### Post by dudesky1325 on 2010-07-01
My machine is VT8505, that may be why it works for me. The track pad works fine, the buttons works and tapping on the track pad works. I have no clue why it won't work for you guys. did you remember to put the original extract in the script folder? And you can't really explore the SD card through a "my computer" type thing, you have to use the various apps to look for the specific file type you want (ie. music for mp3s, video for mp4s, etc.) I just need to know if you are able to update the firmware like you would an android phone. Hope this helped!

---

### Post by DW210251 on 2010-07-05
> **mmanu said:**
> [COLOR=Red]i've resolved my azerty issue by brute force in the /system/usr/keylayout directly on the system (no need to modify the installation script).[/COLOR]

the pdfviewer document to go, proposed by LikeUbun, seems not to be free for pdf (only for office)... i'm looking elsewhere (multireader does not work, office suite viewer messes the maths formulae, android pdf viewer is really slow & still has pb with the maths ... grrr)

I've got a Jay-Book 9901 ([http://www.jay-tech.de/jaytech/servlet/frontend/](http://www.jay-tech.de/jaytech/servlet/frontend/)) with a German  QWERTZ-keyboard. I've successfully installed ANDROID on this maschine, but I can't figure out, how to change the keyboard mapping to QWERTZ. Can anyone help me out, please?

---

### Post by bigredlevy on 2010-07-05
> **dudesky1325 said:**
> did you remember to put the original extract in the script folder? 
sorry, what are you referring to there?

i have since re-installed CE and back to android 1.5.2. the problem wasn't resolved.

---

### Post by VolcomAmsterdam on 2010-07-05
hi fellow mini netbookers,

after having burning red eyes from all the reading about how to get linux to work on my mini netbook could I just have a confirmation of my findings from someone?

eventually the only really functioning OS for the below mentioned machine that skype, web-browser, email, watching flash videos and listening to radio streams will work smooth is stupid and Ugly Win CE? 

shame, was really hoping I could get some ubuntu distro run on it  ](*,)

correct me if I'm wrong ey?!!  

cheers and thanks for all the interesting info here,

tommy

here we go with the specs of my mini:

Processor type: AK7802Q216 Or VIA 8505 (ARM)

RAM installed size: 256MB

Max resolution: 800x480

Integrated Graphics

Hard Drive Type / Spindle speed: NAND Fast Flash

Hard Drive Capacity 2 GB

Ports: 3 x USB 2.0, 1 x SD card slot, Display, 1 x RJ45

Audio/video: Integrated Quadraphonic speakers, 1 x 1/8" (3.5mm) Headphone/Line out, 1 x 1/8" (3.5mm) Microphone, Input 1 x integrated Microphone

Networking / Data Link Protocol

Wireless connection: WIFI

Wireless Protocol: 802.11 b/g

Operating system: Windows CE 6.0

Pointing device: Trackpad

Power device type: 110-240V AC adaptor

---

### Post by snogot on 2010-07-07
here is the datasheet and all for vt8500

no reason to hate me if it is allready postet

[http://tails92.sepwich.com/easypc_linux/](http://tails92.sepwich.com/easypc_linux/)

edit:

i saw a android 7" smartbook that has android on it....

does someone have bought it?

someone could extract android and then from it the linux kernel....all you need is there to build an ubuntu distro of it.can this sulution be successfull?

---

### Post by DonutFUN on 2010-07-09
Hey, I found a bunch of pdf data sheets about this thing (the vt8500, not the wm8505), i just found them on google so there east to find, but ill repost them here anyways.

and if you read one of them it talks about changing your boot screen, using a bmp and a program called "bmp_array.exe" does anyone have that/know where I can get it?

P.S. the two YF700 ones are different even though they have such a similar name

---

### Post by caveman56 on 2010-07-11
Hey there, all the info is great guys, got an EPC 7 inch smartbook with a wm8505 cpu, installing android and it's running the install, but I was wondering, from the guys who have done it already, how long does it take.  Mine is on the upgrading file-system step and I don't know if it's locked up or just takes awhile, it's been about 30 mins, so not sure what to do,

thanks in advance,

Dave

---

### Post by Timeraner on 2010-07-14
Has anyone considered porting Google Chromium OS to these netbooks? I have a WM8505 and having Windows CE 6.0 is terrible.. :-( this distro is based in the cloud, so that would make the small memory capacity almost irrelevant. The OS already works with ARM...

I am not much of a coder, and have minimal experiences with Linux; most of them bad.

---

### Post by alchark on 2010-07-15
> **Timeraner said:**
> Has anyone considered porting Google Chromium OS to these netbooks?
Porting that boils down to making the Linux kernel work with our hardware and possibly recompiling packages with a correct instruction set. The effort to add kernel support for VT8500/WM8505 is already underway (I am currently fixing some issues with my basic code to merge it upstream by 2.6.36 merge window). Once that works, you could immediately run any suitable distro, including Chromium OS, Meego or whatever else (some further effort may still be required, though).

In fact, there is some possibility of success with existing binary-only kernels, too.

And don't be that optimistic about Chromium OS and its memory requirements: currently on my x86_64 machine, Chromium-dev uses 156 megabytes of memory with only 2 tabs, according to about:memory ;)

---

### Post by Timeraner on 2010-07-15
> And don't be that optimistic about Chromium OS and its memory requirements: currently on my x86_64 machine, Chromium-dev uses 156 megabytes of memory with only 2 tabs, according to about:memory ;)
Well, couldn't Linux support Virtual Memory? It could use the built in flash, or even an add-on memory stick. :) Regardless, I'm surprised that these cheap little things have so much potential; I'll have to buy my own! Currently I only have my sister's •pink• WM8505.. Eh, it's a project. She never uses it anyways...

---

### Post by alchark on 2010-07-16
> **Timeraner said:**
> Well, couldn't Linux support Virtual Memory? It could use the built in flash, or even an add-on memory stick. :)
You probably mean paging (swapping), which is not exactly the same thing ;) You can use swap (and you probably will, with only 128MB), but it slows down the system and kills flash quickly. Of course, if you have a pack of disposable fast SD cards or USB flash drives, that's not an issue :)

---

### Post by Timeraner on 2010-07-16
> **alchark said:**
> You probably mean paging (swapping), which is not exactly the same thing ;) You can use swap (and you probably will, with only 128MB), but it slows down the system and kills flash quickly. Of course, if you have a pack of disposable fast SD cards or USB flash drives, that's not an issue :)


Yeah, that's it. It's called virtual memory on Windows, but I now recall that Linux calls it swapping. =P Hey, I have a Wuala account, the free online data storage thing. It allows you to mount the space as a drive; that could be used, online storage. o.o

---

### Post by wkt on 2010-07-18
[SIZE=3]I have the netbook from China with 8505 pocessor now since two weeks and I am very satisfied - also with the WinCE system.[/SIZE]
[SIZE=3]Now I was also successful in booting the Debian system ( of course without destroying the GOOD working programs on the machine ). I was very surprised that the connection to WLAN worked immediately. I also installed successfully the MUTT program which ran on the ARM architecture - very impressive.[/SIZE]
[SIZE=3]Now I want to go on and install further software on the SD card ( perhaps I also will try to have the extpart on a larger USB stick as described in this thread ) but I am new to Debian and don't know the names of the packages.[/SIZE]
 
[SIZE=3]Just now I work with the windows manager fluxbox ( if I remember the name correctly ) and I want to try LXDE, or even gnome or KDE.[/SIZE]
 
[SIZE=3]I would like have a table of names fo the relevant programs for the mentioned WMs as the fluxbox programs are intolerable - no competitors to the WinCE programs !!![/SIZE]
 
[SIZE=3]What I am searching for :[/SIZE]
[SIZE=3]1. Browser ( now iceweasel, tolerable though slow )[/SIZE]
[SIZE=3]2. EMail Client ( read and send mails )[/SIZE]
[SIZE=3]3. PDF Reader[/SIZE]
[SIZE=3]4. Editor ( now nano, intolerable, deprecated... )[/SIZE]
[SIZE=3]5. Explorer/Filemanager ( now mmc, intolerable )[/SIZE]
[SIZE=3]6. Video Player[/SIZE]
[SIZE=3]This might be the might be the minimum, not to speak of Skype, Messenger, Office package etc.[/SIZE]
 
[SIZE=3]What programs can you recommend and are already available for the ARM architecture ?[/SIZE]
 
[SIZE=3]Thanks for any answers.[/SIZE]

---

### Post by vinceCOOK on 2010-07-22
hello

---

### Post by vinceCOOK on 2010-07-22
Hello Forum,

I believe there may finally be an extra answer to putting LINUX onto your chinese netbooks.

People have already managed to get ANGSTROM LINUX working on wm8050 netbooks.

However, ANGSTROM can run on any ARM based chip.

i find this webpage which describes how to install ANGSTROM LINUX
from within the windows CE desktop.

[http://www.linuxtogo.org/gowiki/WinCeQuickInstall](http://www.linuxtogo.org/gowiki/WinCeQuickInstall)

It describes how you can make the install become a FULLY FUNCTIONAL LINUX by following the.... 

"installing using a loopback image" method.

This should result in ANGSTROM LINUX working on all chinese ARM CHIP netbooks.  (vt8500 and wm8050 etc)

Angstrom comes with hundreds of applications ready to install such as GIMP, VLC player and OPEN OFFICE.

Also people, you may like to try PORTABLE UBUNTU for your netbook. Download it and directly execute it from the windows CE desktop. This is a full version of UBUNTU that runs from within windows. The version you need to download is the UNO version. YOu may also need to go into the config file and find the line about RAM and reduce it to 90 or smaller.

THIS MAY NOT WORK because UBUNTU is x86 archictecture and not ARM based..... but it is worth a try.

[http://sourceforge.net/projects/portableubuntu/files/](http://sourceforge.net/projects/portableubuntu/files/) (450 meg EXE file)

actually creating a specific version of angstrom for yourself is desribed in detail on this link here...

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php)

but for the time bieng you can use the "installing using a loopback image" method.

hope this helps everybody,

Vince.

---

### Post by vinceCOOK on 2010-07-22
Hello again,

The ANGSTROM post preceding this assumes that you have an IMAG FILE ready for your netbook.

This is what it appears to be saying.

Creating this image file for wm8050 machines was described here

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php)

so i imagine that it is also possible to create an image file
for vt8500 machines?

thanks

Vince.

---

### Post by vinceCOOK on 2010-07-22
Hello,

The previuos 2 posts describe Angstrom Linux.

I believe that the "preview first" method of install should
work directly from the windows CE desktop. Download
the EXE file and double click it.

This may work on all chinese netbooks.

This kind of linux is called a LIVE linux and it's fully funtional to the point where you can even install extra Linux tools from the angstrom repository, 

However, everything is LOST when you reboot the netbook. So you must save any important work like wordprocessing files or anything.

It should give you a taste of Linux on your netbook.

hope this helps people

Vince.

---

### Post by vinceCOOK on 2010-07-22
Hello

This is the details on how they made an Angstrom image for wm8050 machines.

it appears that you need to know what BOARD is inside your netbook. 

The option mini2440 in buidling Angstrom image describes the type of BOARD
that your netbook has.

[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=41](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=41)

i imagine the vt8500 machines will have similar BOARDS to wm8050 machines.

You have a choice of boards when you are making the image at the Angstrom
website.

hope this is not off topic or incorrect and that it helps people

V.

---

### Post by vinceCOOK on 2010-07-23
Hello Forum,

Sorry but the previous posts about Angstrom Linux won't work.

You need to have the "HARET bootloader" running in windows CE but it's incompatible with windows CE 6.0.

[http://www.linuxtogo.org/gowiki/WinCeQuickInstall](http://www.linuxtogo.org/gowiki/WinCeQuickInstall)

However, somebody told me that making the Angstrom Linux image
as described here....

[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=41](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=41)


...may work on vt8500 machines as long as it only contains "programs" and not the wm8050 kernel.

i am not sure exactly what he means by that comment so i am reading further.

thanks

Vince.

---

### Post by alchark on 2010-07-24
> **vinceCOOK said:**
> ...may work on vt8500 machines as long as it only contains "programs" and not the wm8050 kernel.

i am not sure exactly what he means by that comment so i am reading further.
Vince, as I posted above, you can run any modern Linux distro (including Angstrom or anything else that supports ARM instruction set, like Gentoo or Debian) once you get a recent Linux kernel for your hardware. And the latter is the problem, as for WM8505 all that we have is an ugly binary Chinese Android kernel (version 2.6.29). For VT8500 there is an ultra-old Chinese binary archive with verstion 2.6.10 (that's really ancient and precludes use of modern distros due to a number of problems) and some semi-open archive of 2.6.18, which I did not really try to build yet.

The kernel is what abstracts away all the hardware differences within a given architecture, and our hardware is quite different from other ARM-based boards. So, to get anything working, we need suitable kernels first. On WM8505 you can probably run Angstrom with the Android kernel, but there may be some issues due to Android changes in it (I am not sure).

---

### Post by ibsrom on 2010-07-24
Hello everybody,

Fascinating scientific work done here, I read all, and want to thank everybody for their wonderful work.

I have a UBISURFER DW-SB02, has a green board with the DW-SB02 name, 128 MB, 1 GB flash, 7" TFT 800x600.
Has ARM926EJ-S rev 5, SMDK2450, 199 MIPS.  *think is a S3c2450.*
Has SIM with GPRS internet acces, and a dialer/embedded proprietary browser for GPRS connect/browsing, very slow and with disabilities, poor him
It has a Debian, Linux kernel 2.3.21.5-cfs-v19, gcc 4.2.2, 17 nov 2009, on it.
It has a gnome , I think... I can not see and configure the desktop, nothing appears on it, only a My Documents, wich does not open, it does not show what I save on.
It has an Iceweasel browser (very bad this release).
Has a very simple WiFi manager.
Ethernet is not configurable, it is 10BaseT, and it is not connecting.
It has no apt-get.

NOW: It does not boot from anything. 
Do you know if it can boot, and how? And a viable other OS for it?
Do you need me to save files from it and upload for you? If you tell me how, I will.
Can please anybody help me also with a little bit of info, advice?

Keep up the good work, everybody

---

### Post by alchark on 2010-07-24
ibsrom, could you post a link to where your device is sold? I have not seen such configurations yet, could be interesting (with proper software, of course) :)
As for your other opportunities, please provide some more information. For a start, post the contents of (decreasing priority): /proc/mtd, /proc/cpuinfo, /proc/partitions, /proc/mounts, /proc/iomem, /proc/interrupts and whatever else you consider useful :)

UPD: Seems to cost over 100 GBP... Could be better at this price! And where do all those guys get SUCH old kernels?..

---

### Post by ibsrom on 2010-07-24
alchark:
/proc/mtd; permission denied (I don't know how to have root access)
/proc/cpuinfo : permission denied
/proc/partitions : the same
/proc/interrupts : also
If you tell me what to do, I will.
I bought this in London in april, from a computer fair, 80 Pounds after bargaining.
Do you have any ideas regarding my questions? How to upgrade the kernel, the Firefox Iceweasel browser, gnome, how to have access at gnome system configuration? Are you aware of any bott key combination that will allow me to configure the boot or boot from SD or USB?

---

### Post by alchark on 2010-07-24
> **ibsrom said:**
> Do you have any ideas regarding my questions? How to upgrade the kernel, the Firefox Iceweasel browser, gnome, how to have access at gnome system configuration? Are you aware of any bott key combination that will allow me to configure the boot or boot from SD or USB?
Without root access that's going to be much harder... I would try accessing the serial console somehow to see the bootloader messages. It could even provide a command prompt there to override the boot sequence or reflash the firmware.

Or you could try to hack yourself root access, of course :) Can you read /etc/passwd and have you got /etc/shadow? Have you tried sudo?

---

### Post by ibsrom on 2010-07-24
sudo not found
su -l works
/etc/passwd line 1 to 15: not found
/etc/shadow/ permission denied

---

### Post by alchark on 2010-07-25
> **ibsrom said:**
> su -l works
Presumingly, you still can't get to a root shell with that, though :) Well, you have at least two ways: either try to find some insecurity in your current configuration (like a privileged daemon that you could (ab)use) or go the "hardware way", i.e. find UART and/or JTAG on your board and use those to execute your own code. 

For the latter, you would at least need a multimeter and a serial dongle with TTL voltage. I use a cheap Chinese USB cable for some old mobile phone that has a box in the middle with a PL2303 usb-to-serial chip. The onboard serial port most probably consists of 4 pins (or soldering points), one being ground, one +5V/+3.3V power supply and the remaining two being TTL-level Rx and Tx. Power may be missing, then you will have only 3 pins. You might also see two parallel leads going from Rx and Tx straight to the main chip. Ground is typically connected to any shieldings inside the case, so you can find it with a multimeter (short-circuit testing). So, you just connect your serial dongle's ground to the board's ground, open a terminal on the host PC (`busybox microcom -s 115200 /dev/ttyUSB0` or similar) and use the dongle's Rx input to find a pin that prints characters when the device powers up. That one would be the board's serial Tx.

---

### Post by PrFaas on 2010-07-27
In minor addition to the previous post; a little recommendation:

Try to measure the voltage on the TxD pin before you connect anything to the RxD pin. If you find 3.3 Volts on the TxD pin, then take care to not expose the RxD pin to more than 3.3 Volts too.

The reason for mentioning: If the connection of your RxD signal is directly into the CPU/SoC chip (as is the case with my machine..), it is most probable that the maximum voltage on the RxD pin is also 3.3 Volts. If that is so, then you would probably 'kill' the CPU/SoC chip if you'd 'feed' 5.0 Volts into the RxD pin.

Somewhere in this thread (around 'page 13' probably), there is -i think-  a mention of one proud owner of a VT8500/WM8505 machine who got burned by that mistake....

---

### Post by ibsrom on 2010-07-27
@alchark, prfaas:
Thank you very much for your support.
I suspect that firmware update can be done through a little USB on the back, like in PPC and smartphone case. I will try this first, I found some software, SDK, something like that, for building the firmware for this CPU.
The Linux on it is at least lame. I have a HTC HERMES, and I fonud a lot of firmwares made by lots of guys, and a lot of programs for, and I am very pleased with the windoze 6.1-6.5 I currently use with it.

---

### Post by Dosfish on 2010-08-01
I'm pretty sure the ubisurfer is a different SOC than the vt8500 and wm8505.

---

### Post by ibsrom on 2010-08-01
Yes, it has S3C2450, based on arm926ej-s, v5.
Now it is frozen in the bootscreen, after I installed manually some shared libraries for synaptic and aptitude, and I was replacing a libc shortcut with the file itself, it was frozen in linux, hardware reset, and now only bootscreen.
I wrote to the datawind techsupport, waiting to see if they provide me with firmware and method.
I opened it and it has no hard switches and appears not to have jtag, but a miniUSB near the processor, witch I suspect is the way flashing is performed.

---

### Post by Tavicu on 2010-08-09
Hello

I want to buy one of this: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170517933617](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170517933617)


I want to ask you if i could install ubuntu or another os on it ... thank you!

---

### Post by barthezz on 2010-08-09
Check this out, guys. [http://www.alibaba.com/product-gs/235461918/7_inch_netbook_PCBA_Motherboard.html](http://www.alibaba.com/product-gs/235461918/7_inch_netbook_PCBA_Motherboard.html)
I tried to speak to Ebenda managers - they don't reply.

---

### Post by Max399 on 2010-08-09
Hello everyone, sorry if im asking this question for the 100th time (I did read about 20 pages, but i couldnt read all the topic), but i just want to know if its Yes or No (You'we done a lot of researches so i dont know the anwser), is it possible to install unix on this netbook (Debian, Ubuntu or any other)?
Cause i was thinking of ordering it, just the WinCE that doesent suit me.

---

### Post by alchark on 2010-08-10
> **Max399 said:**
> i just want to know if its Yes or No
Yes;) If you get a WM8505, you are more lucky, as there is a nearly complete kernel source archive for 2.6.29-android released by VIA, see [http://lists.gpl-violations.org/pipermail/legal/2010-July/002204.html](http://lists.gpl-violations.org/pipermail/legal/2010-July/002204.html)

VT8500 would need work.

> **barthezz said:**
> Check this out, guys. [http://www.alibaba.com/product-gs/235461918/7_inch_netbook_PCBA_Motherboard.html](http://www.alibaba.com/product-gs/235461918/7_inch_netbook_PCBA_Motherboard.html)
I tried to speak to Ebenda managers - they don't reply.
It should most probably fit into our cases, but quite likely there will be problems with the LCD panel, keyboard and touchpad, as they may be different. And frankly, I'd rather get a cheap "ordinary" x86 netbook instead of bothering with these :)

---

### Post by Max399 on 2010-08-10
[sutpid_question]
Installing Unix on it, putting Apache on it and use as a little Server? Doesent use too much power, silent. :p
[/sutpid_question]

---

### Post by staylor29a11 on 2010-08-17
I have a easypc e700 series netbook with an arm926 processor, i am trying my best to fix this, it won't boot with vt8500 microsoft windows ce firmware, I can't get it to install windows again because it won't boot with the files from the script folder. 

I have also tried to use easypc linux, i cannot write an ext2 partition from my windows xp desktop. I can boot easypc linux from a full fat32 partition, but it stalls and won't boot. 

I don't know the first thing about a soc or solid state drive, i know x86 really well. I think that these are more difficult to deal with. I wish i never seen the little thing to tell you the truth.

I would like to be able to use android, but it is so confusing to me to compile anything since it's not x86. I appreciate any input that you would like to give. I know a little ubuntu but not any of the other stuff that you have here. Thanks so much for any information, and God bless

---

### Post by norseman-has-a-laptop on 2010-08-18
im going to buy a 9" dell insperon from my uncle here soon:p

---

### Post by celem on 2010-08-18
> **Tavicu said:**
> Hello

I want to buy one of this: [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170517933617](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170517933617)


I want to ask you if i could install ubuntu or another os on it ... thank you!

I have one of these. The Android on it runs much, Much, MUCH better than the netbooks being discussed here. It isn't a speed deamon but good for email and web browsing, but no YouTube (No Flash). Its big issue is battery life. I only get about an hour, at most.

---

### Post by Bobi-bay on 2010-08-19
Hi guys,

I'm reading this amazing and informative Thread for a few days now. after i manage to install **Android V1.5 on my WM 8505**
I was looking for other guys here that have experienced problems like i did on Android os [ARM wm 8505 7" Netbook from China].

Although it was already been talked about dozens of pages before, I really want to know if anyone manage to overcome this problems. And this Post maybe could help newcomers that found this Thread on Google but was pretty lost trying to get info' out of it.

These are my problems and Conclusions from reading this big Thread: 

1. **Red text message "For Demo Purpose only"** on the top left bar: Although some people said this MSG was gone after several reboots, I was unable to find the reason for it, or why some people have it and some don't. (Is there any limitations because of it?)

2. **A missing "Android -MARKET"** icon. Although there are some Alternatives (like [slideme.org/] and manual Apt install) I still don't know why this version lacks the ability to get into Android Market.

3. **Missing Internal 2 GB space**. Got to realize that Unfortunately this is hopeless, the Android OS basically ran over the Internal flash memory, Leaving me only 199 MB internal free memory. (in other words -> go get a big SD from Ebay)

4. **Unable to access USB flash memory** (DiskOnKey). This problem is probably one of the annoying one out there. When inserting the USB flash memory device, the "U-disk" Icon is shown on the left top bar, but there is no way to get to it! after a bit of a search, i realized Non of the "File explorers" apps cant get to it too. Well, Sucks.

5. **a Problematic Mouse Pad**. Well, I'm sure most of you wont bother this one. But this to me is the Worst part, the problem is that the Netbook Mouse pad isn't Function as a regular mouse pad that controls your cursor. It's actually function as kind of a touch screen joystick that moves pages on the desktop. This is totally Useless. When inserting a normal USB mouse there's No problem. 
I real needed this Pad to work Like a normal Mouse. This is the reason i bought the Nbook in the first place - its portability. Now i have to carry a little mouse with me all day? 

I guess some of you experienced those problems. If there's a way to fix the Mouse Pad I would consider staying with this OS because i really like its simplicity. [not even the missing market, missing 2 GB memory or Missing U-disk broke my spirit, but the Nonfunctional Mouse pad surly did].

You are more then welcome to add some of your problem with this Android OS , although i think I covered the main ones.

Please Let me know if you have some solutions... Before Changing back to CE or getting into the Non-friendly (for guys like me) world of Linux. 

Thanks!
Bobi.

*sorry for some wording mistakes. English is not my Native language.

---

### Post by scu-ba-de-buntu on 2010-08-21
This is quite the thread.

Is the Augen E-Go 7" Netbook the same as these? It seems to have AKARM ARM926-AK7802(248MHz). Has anyone gotten Linux on this netbook? That would be sweet. Also, has anyone here been able to back it up as a factory default image? If not, if someone could point me in the right direction, I will do it. I want to be able to dual boot but don't want a brick.

It is from:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834320001](http://www.newegg.com/Product/Product.aspx?Item=N82E16834320001)


Thanks!

---

### Post by celem on 2010-08-21
It looks physically similar - same case, at least. If you can return it - do so. That is my advice.

---

### Post by Bobi-bay on 2010-08-22
hi scu-ba-de-buntu,

The Case is exactlly the same, and Hardware seems not as good. How much for intl.shipping from this site?

About Returning to Factory image
Download this script for wm8505
 
[http://rapidshare.com/files/327848203/8505.rar](http://rapidshare.com/files/327848203/8505.rar)

this is the original Script image of win CE 6. 
after installing thru SD, Win ce will boot and automaticlly install English. Then reboot- and you are set.


Did any one experience the problems i've posted here two days ago?
Anyone mange to solve the NonFunctionall Mouse Pad on Android 1.5?

Thanx

---

### Post by smart734 on 2010-08-22
Hello, at the first, sorry for my english, because I`m czech.
 
Please help, I`m laic and I need to get ubuntu 10.04 on the netbook AMR-WM8505. I need it, because on the windows is PocketWord, but it isnt working on my PC. I need linux very quikly to school. Thanks.

---

### Post by DonutFUN on 2010-08-22
I'm sorry [smart734]("http://ubuntuforums.org/member.php?u=1135003") But that's actually out of the question, it has an ARM processor not an X86 so there is no **Ubuntu** for it right now.
But on another hand you are quite lucky you got the WM8505 and not the VT8500 like me, there is a **Dibian** for it, or an **Android** for it, if you go a little further back in this thread you will find the links to install it and also the instructions on how to install it

Good luck

---

### Post by scu-ba-de-buntu on 2010-08-22
#1000  :D

> **celem said:**
> It looks physically similar - same case, at least. If you can return it - do so. That is my advice.

I haven't even got it in the mail yet :P I think it will be here Tuesday morning. I'm not sure if I can just return it.

> **Bobi-bay said:**
> hi scu-ba-de-buntu,

The Case is exactlly the same, and Hardware seems not as good. How much for intl.shipping from this site?

About Returning to Factory image
Download this script for wm8505
 
[http://rapidshare.com/files/327848203/8505.rar](http://rapidshare.com/files/327848203/8505.rar)

this is the original Script image of win CE 6. 
after installing thru SD, Win ce will boot and automaticlly install English. Then reboot- and you are set.


Did any one experience the problems i've posted here two days ago?
Anyone mange to solve the NonFunctionall Mouse Pad on Android 1.5?

Thanx

It was $76 at the end of everything.

Since I posted that I have found out that the SoC on my netbook's board is made by Anyka and model AK7802.

Apparently / Supposedly there are backups of drivers with this as well as FULL specifications for the hardware over at [http://mininetbooks.your-board.com/]("http://mininetbooks.your-board.com/"). Interestingly though there is BS about becoming a "Knight" there before you are given ANY useful information. :-k
I want to THANK EVERYONE on this forum for not derailing over to that forum when openanyka told you guys to stop and work on stuff over there. On that note, anyone here have the AK7802 specs? I really want to port linux / install it if someone has figured it out.




> **smart734 said:**
> Hello, at the first, sorry for my english, because I`m czech.
 
Please help, I`m laic and I need to get ubuntu 10.04 on the netbook AMR-WM8505. I need it, because on the windows is PocketWord, but it isnt working on my PC. I need linux very quikly to school. Thanks.

I'm not sure, but I remember reading that ARM9-WM8505 is the same as VT8505. The source is out there as DonutFUN said though. You will need a SD card to install linux. You should note that Ubuntu is based on Debian, and therefore its not too different once you have a X Windows server running.

Alternatively, or also, there are other WinCE text editors. I don't remember where I found it, but there is a Zip of about 300mb of free Tools and Utilities for WinCE floating around on the forums either from this thread or from the Anyka one located [here]("http://mininetbooks.your-board.com/"). Also, what do you mean it doesn't work with your pc? Can you email yourself the files?

Maybe that helps?

---

### Post by aminux on 2010-08-23
> **DonutFUN said:**
> I'm sorry [smart734]("http://ubuntuforums.org/member.php?u=1135003") But that's actually out of the question, it has an ARM processor not an X86 so there is no **Ubuntu** for it right now.
But on another hand you are quite lucky you got the WM8505 and not the VT8500 like me, there is a **Dibian** for it, or an **Android** for it, if you go a little further back in this thread you will find the links to install it and also the instructions on how to install it

Good luck

 I have such un 8505 based chinese 7&quot; netbook and have been rather successful at installing it, though I did not found it in this thread but instead by googling 'linux 8505' or 'linux ARM'.  What is odd is that this debian can't know anything with the built-in 2 Gb storage. lshw clearly shows it is not known from the system. Has anyone be successful at it?

---

### Post by aminux on 2010-08-25
to complete my previous post, I found my debian for ARM 8505 here:  [http://bur.st/~abrasive/wm8505_linux/](http://bur.st/~abrasive/wm8505_linux/)

---

### Post by DonutFUN on 2010-08-25
Hey, if anyone has a broken one of these their willing to either give away or sell for cheep please email me at [EMAIL="geronazzo_nicholas@ymail.com"]geronazzo_nicholas@ymail.com[/EMAIL].
I have one but the battery sensor is broken, so not only does it not tell me when its charging, or how much charge is in (always says 100%), it also kills itsself slowy over a couple of days, it i leave it unpluged, even it im not using it, it dies on its owen and wont turn on at all after like 2 days. its rather annoying
 
so if you have one with like, a broken screen, or keyboard or anything, and are willing to sell for cheep please contact me
 
**HAS TO BE VT8500 BY THE WAY** (just capsed so everyone reads)

---

### Post by scu-ba-de-buntu on 2010-08-26
Ok, so my netbook came in the mail. It doesn't have the F1 option. Any ideas? I want to make a backup of it. And then start working on porting linux to it. :)

> **DonutFUN said:**
> ... the battery sensor is broken ... 
**HAS TO BE VT8500 BY THE WAY**...

@DonutFUN: What is wrong with it exactly? People in this thread are fairly good at EE. Maybe take some pics of the netbook's sensor?

---

### Post by Bobi-bay on 2010-08-26
Hi guys,  

Does any one knows if there is an option of installing Android Apk's on SDcard ? 

My 200MB of internal space got almost totally full and the system is getting to slow!!

I know there are some "Apps-to-SD" guids that suitable for Linux. Is there a way to do that on Android 1.5 OS (WM8505)?

Do you also experience a Laggy OS after installing a lot of apps on the internal memory?

And Is there a way to UNinstall Build-in Apps? (Like dialer)

---

### Post by DonutFUN on 2010-08-26
Its not a problem that can be fixed, the power adapter broke off inside it, and when i was getting it sottered back on two of the points were touching, and it fried the sensor so it always says its 100% full and just kills itself over time

---

### Post by dodo410 on 2010-08-29
In the Android 1.52 
[http://orca.st.usm.edu/~cberry2/android-ARM-8505-Smartbook.zip](http://orca.st.usm.edu/~cberry2/android-ARM-8505-Smartbook.zip) 
 
Can I use the Russian keyboard, and typing in Russian?   :)

---

### Post by Bobi-bay on 2010-08-29
HI DODO410

The answer is YES. you can add Language & keyboard support for the Android 1.5 here: 
[http://code.google.com/p/softkeyboard/](http://code.google.com/p/softkeyboard/)
I Did that with My Wm8505 on Android 1.5 os.

the Developer wrote : "supporting lots of languages: English, Hebrew, Russian, Arabic, Lao, Bulgarian, Swiss, German, Swedish, Spanish, Catalan, Belorussian, Portuguese, Ukrainian and many more." 

First install the SoftKeyboard.APK and only then the SoftKeyBoard Russian Language Pack.

Regardsless of this Lang'Pack you will need to add Fonts manually, [http://code.google.com/p/softkeyboard/wiki/InstallFonts](http://code.google.com/p/softkeyboard/wiki/InstallFonts)

Transfer the Fonts files into System/Fonts and replce the existing ones.

Then go to settings and put SoftKeyboard as deafult. 

*In thw WIKI tab you will find step by step guides.

Let me know if you managed to do this.

Boby

---

### Post by DonutFUN on 2010-09-01
so I wanted to know some stuff about the serial port you guys found, i dont know a lot og the techno speech so i was just going to ask it simply:
when you say its a serial port does that mean the old com port? (almost looks like an inverted VGA monitor port)
and if so how the heck do you translate it (what pins connect to what of the 4 spots); can you just put a com port onto thins thing, i have a program on my pda (its old and plugs into com) that suposidly monitors serial info and stuuufff)

I just kinda want to know what happened without having to read 20 pages, just to not understand what you did in the end anyways

---

### Post by Pezbacon on 2010-09-01
Please I have a question of this netbooks, I bougth a 7" netbook with VIA ARM-920 266 Mhz processor and 256 mb of ram but I can't find a linux for this tipe of processor, can anyone help me with a link? or the distribuition for wm-8505 and vt-8500 can be installed in my netbook?

Thanks.

---

### Post by PrFaas on 2010-09-02
Could anyone point me where '

[http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php)

has moved to?

Could well be that i've missed the announcement that it has moved, or that there is something 'nasty' between 'me' and the site, but i get 'no contact' with it from 'here'; My error message is:

An error occurred while loading [http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php:](http://s0.blackmage.co.uk/~nextvolume/via_arm/index.php:)
Could not connect to host s0.blackmage.co.uk.

---

### Post by nextvolume on 2010-09-02
blackmage.co.uk didn't appear very reliable so I moved the forums to another server back in May. Until some time ago when blackmage.co.uk had not changed their servers' operating system yet I had a working redirection to the new location:

[http://devio.us/~nextvolume/via_arm](http://devio.us/~nextvolume/via_arm)

tinyurl.com/easypc-forum should be not used anymore (I tried to make the tinyurl admin change the redirection, but he did not want to despite me giving him proof)

Go to the place on devio.us... [www.bento-linux.org](www.bento-linux.org) (or the #easypc IRC channel on FreeNode) is the stablest place you're going to get when you want a link to the forums (in case they move again, hehe).

---

### Post by kirbyparufo on 2010-09-02
> **Pezbacon said:**
> Please I have a question of this netbooks, I bougth a 7" netbook with VIA ARM-920 266 Mhz processor and 256 mb of ram but I can't find a linux for this tipe of processor, can anyone help me with a link? or the distribuition for wm-8505 and vt-8500 can be installed in my netbook?

Thanks.

I can't provide any links, if they exist, but I can tell you that there is no way the distros for WM-8505 or VT-8500 will work on your processor. In fact, they'll probably brick your system if you attempt to use them, so be careful.

---

### Post by mstation on 2010-09-04
> **abrasive said:**
> Can you enter the console (just hit Enter) and grab the output of the following: ```
 ls /dev/mmcblk0* 
ls /mnt/mmcblk0* 
```  If you find your partition (eg. as mmcblk0p1) you should be able to ```
 mount /dev/mmcblk0p1 /mnt/sd 
mount /dev/mtdblock9 /mnt/mtd 
tar xzf /mnt/sd/extpart.tgz -C /mnt/mtd 
``` which will complete your install.

hello.. just a quick question..

when i mount /dev/mtdblock9 /mnt/mtd i get this:

yaffs: dev is 32505865 name is "mtdblock9"
yaffs: passed flags ""
yaffs: Attempting MTD mount on 31.9, "mtdblock9"
yaffs: auto selecting yaff2
block 3475 is bad
block 3476 is bad
block 3477 is bad
block 3478 is bad
yaffs_read_super: isCheckpointed 0

and i can't procede with the extracting of the extpart.tgz

---

### Post by elMagnate on 2010-09-04
Hello.

I was looking about the extra-cheap minilaptop/smartbook of $40 here[http://cgi.ebay.com/7-Mini-Laptop-Netbook-Computer-Notebook-WIFI-WindowsCE_W0QQitemZ130384943952QQcategoryZ177QQcmdZViewItemQQ_trksidZp4340.m8QQ_trkparmsZalgo%3DMW%26its%3DC%26itu%3DUCC%26otn%3D5%26ps%3D63%26clkid%3D7517514838564124049#ht_6321wt_1137]("http://cgi.ebay.com/7-Mini-Laptop-Netbook-Computer-Notebook-WIFI-WindowsCE_W0QQitemZ130384943952QQcategoryZ177QQcmdZViewItemQQ_trksidZp4340.m8QQ_trkparmsZalgo%3DMW%26its%3DC%26itu%3DUCC%26otn%3D5%26ps%3D63%26clkid%3D7517514838564124049#ht_6321wt_1137"). That directed me to this post of the ubuntu forums. I'm i bit lost with these staff.

With that smartbook can i install anything apart of windows CE? The ARM processor matches with the requirments. Can i install Android or just bento/easypc linux distro? Can i install google chrome OS or Ubuntu netbook remix? Can i actualize android 1.5 to a newer version?

Thank you in advance.

---

### Post by vinceCOOK on 2010-09-06
Hello

[www.bento-linux.org](www.bento-linux.org)

can anybody get this website working?...the FORUM link does nothing.

thanks

Vince.

---

### Post by lokirx706 on 2010-09-14
> **mstation said:**
> hello.. just a quick question..

when i mount /dev/mtdblock9 /mnt/mtd i get this:

yaffs: dev is 32505865 name is "mtdblock9"
yaffs: passed flags ""
yaffs: Attempting MTD mount on 31.9, "mtdblock9"
yaffs: auto selecting yaff2
block 3475 is bad
block 3476 is bad
block 3477 is bad
block 3478 is bad
yaffs_read_super: isCheckpointed 0

and i can't procede with the extracting of the extpart.tgz


I have the same problem, I have to manually mount the SD card every time because it cannot find it. I also have gotten to a point where I can extract the contents of extpart.tgz however I get outputs of

"tar: short read"
"tar: invalid tar magic"
"Segmentation fault"
and other times it actually reads but aborts before finishing the memory map.

I have yet to complete the install.... Any help is much appreciated!

---

### Post by Karasik on 2010-09-16
Join the previous message. The problem with the archive section for ext. Please give a working archive. Thanks in advance.

---

### Post by fauxhawk18 on 2010-09-20
> **lokirx706 said:**
> I have the same problem, I have to manually mount the SD card every time because it cannot find it. I also have gotten to a point where I can extract the contents of extpart.tgz however I get outputs of

"tar: short read"
"tar: invalid tar magic"
"Segmentation fault"
and other times it actually reads but aborts before finishing the memory map.

I have yet to complete the install.... Any help is much appreciated!

ok, i registered just for this. i Have read every page and entry since page one, and thought to add this. I was having problems installing this linux, it would tell be the sd card could not be found. Couldnt find anything helping me. So i tried locking the sd card with the lock switch on the side, and that worked, let me install right away

---

### Post by PrFaas on 2010-09-24
Ref previous post: a bit of a silly question... 

Can you *write* to the sd-card now? 

My reason for asking is the following: An SD-card 'connector' (the thing you stuff your SD-card into) has two switches. One is normally used to detect *if* the card is present, the other is normally used to detect the state of the write-protect switch.

I'm slowly getting the notion that -in the driver and/or hardware- these two switches might have gotten 'swapped'. 

That would explain why -with write-protect- the card is detected, and with write-enable the card is not detected. Assuming that to be the case, I'm curious what the interpretation of the switch that is normally the card-detect (now write-protect) will be...

---

### Post by abrasive on 2010-09-24
> **PrFaas said:**
> 
I'm slowly getting the notion that -in the driver and/or hardware- these two switches might have gotten 'swapped'. 

My easypc had the SD write bug - but detected cards fine.
I think one of the motherboard revisions connects the SD shield (switch case) to the wrong potential, so the sense line ends up always high. I fixed it on mine by removing the feed resistor and grounding the case/common.
I didn't think to try flipping the switch to WP - which would leave the line floating, IIRC... hopefully there is a pull-up/down on it somewhere else! Having reversed the logic level in software vs. hardware seems most likely...

---

### Post by DonutFUN on 2010-09-27
So I found something Kind of interesting out tonight, I have two VT8500 (neither are wm's or 05's) and even though they are the same, they are both different, there is one micro chip that on one is on the little removeable (Ram type) card, and on the other its sottered to teh board, and its obvious that it can be put in either spot on either, ill post pictures to show you what chip and where I'm talking about

I hope its obvious which chip I'm talking about

---

### Post by DonutFUN on 2010-09-27
So I asked a while ago and no one answered as to how I could go about hooking up to the serial on my laptop, i was jsut browsing the web and found this
[http://wm8505.blogspot.com/](http://wm8505.blogspot.com/)
is that how I would go about it? with a usb? and I thought I had heard someone say something earlier about not using 5V, using 3?
 
Please asnwer I want to know, I uave a friend thats really good at sottering that I only get to see about once very 2-3 months and If that is right id like to get him to do it now, instead of having to wait till like december.
 
Thanks

---

### Post by nastiro on 2010-09-27
> **DonutFUN said:**
> So I asked a while ago and no one answered as to how I could go about hooking up to the serial on my laptop, i was jsut browsing the web and found this
[http://wm8505.blogspot.com/](http://wm8505.blogspot.com/)
is that how I would go about it? with a usb? and I thought I had heard someone say something earlier about not using 5V, using 3?
 
Please asnwer I want to know, I uave a friend thats really good at sottering that I only get to see about once very 2-3 months and If that is right id like to get him to do it now, instead of having to wait till like december.
 
Thanks

 I have a vt-8500 but have yet to hook up a serial. That Link you provided looks about right.  You should be able to confirm the power requirements by searching through the forum.

---

### Post by PrFaas on 2010-09-29
> **DonutFUN said:**
> So I asked a while ago and no one answered as to how I could go about hooking up to the serial on my laptop, i was jsut browsing the web and found this
[http://wm8505.blogspot.com/](http://wm8505.blogspot.com/)
is that how I would go about it? with a usb? and I thought I had heard someone say something earlier about not using 5V, using 3?
 
Please asnwer I want to know, I uave a friend thats really good at sottering that I only get to see about once very 2-3 months and If that is right id like to get him to do it now, instead of having to wait till like december.
 
Thanks

'my' activities start around post #128 ('page 13'), and 'about post #175 and 'onwards' i describe the serial port i connected to my machine. The ASCII drawing in post #177 is primitive, but that *is* what i've now got connected to my machine. Post #155 mentions the fact that the four 'pads' marked gnd, tx, rx and 5V are the ground, txd, rxd and (no mistake..) 3.3 Volts supply pads that can be used to hook up a serial port. The default baudrate is 115200 BAUD, 8 bits, no parity. The pad on the board is marked 5V, but actually supplies only 3.3 Volts, and the serial interface must accept/generate no more that 3.3 Volts at the tx(d) and rx(d) pads. Post #202 (page 21) has the complete circuit diagram as 'ascii art'. In post #217 (page 22) mr.       #217 Matriark TerVel has made a picture version of the circuit. In post #223 the situation with the Vcc (5.0 Volts) for genrating the supply voltage for an 'internal' RS232 buffer is again discussed. At post #248, i have my serial console (finally) completely working.

Hope that provides enough guidance in the forest of posts.... Good luck, and please *never* put 5.0 Volts on the rx pin: that would destroy your CPU ;-) (see post #234)

---

### Post by DonutFUN on 2010-09-29
OK, never mind what I was asking then, I thought it was simple wire to wire connection, I didn't know there needed to be resisters and all that jazz, so never mind then

---

### Post by SteffenBaier on 2010-09-30
> **alchark said:**
> ibsrom, could you post a link to where your device is sold? I have not seen such configurations yet, could be interesting (with proper software, of course) :)
As for your other opportunities, please provide some more information. For a start, post the contents of (decreasing priority): /proc/mtd, /proc/cpuinfo, /proc/partitions, /proc/mounts, /proc/iomem, /proc/interrupts and whatever else you consider useful :)
 
UPD: Seems to cost over 100 GBP... Could be better at this price! And where do all those guys get SUCH old kernels?..
 
The Unit is also known/sold as a Delstar DS700
 
I got the same unit and it seems Ibsrom done something wrong:
**cat /proc/mtd**
dev:    size   erasesize  name
mtd0: 00040000 00040000 "Bootloader"
mtd1: 001c0000 00040000 "Kernel"
mtd2: 3f400000 00040000 "Root - YAFFS2/Datawind"
mtd3: 00a00000 00040000 "File System"
 
**cat /proc/cpuinfo**
Processor : ARM926EJ-S rev 5 (v5l)
BogoMIPS : 199.47
Features : swp half fastmult edsp java 
CPU implementer : 0x41
CPU architecture: 5TEJ
CPU variant : 0x0
CPU part : 0x926
CPU revision : 5
Cache type : write-back
Cache clean : cp15 c7 ops
Cache lockdown : format C
Cache format : Harvard
I size  : 16384
I assoc  : 4
I line length : 32
I sets  : 128
D size  : 16384
D assoc  : 4
D line length : 32
D sets  : 128
Hardware : SMDK2450
Revision : 0000
Serial  : 0000000000000000
 
**cat /proc/partitions** 
major minor  #blocks  name
  31     0        256 mtdblock0
  31     1       1792 mtdblock1
  31     2    1036288 mtdblock2
  31     3      10240 mtdblock3
 254     0     501248 mmcblk0
 254     1     128488 mmcblk0p1
 254     2     369495 mmcblk0p2
 
**cat /proc/mounts**     
rootfs / rootfs rw 0 0
/dev/root / yaffs2 rw 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw 0 0
tmpfs /tmp tmpfs rw 0 0
/dev/mmc1 /mnt/sd vfat rw,sync,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
 
[B]cat /proc/iomem 
[/B]20000000-3fffffff : smc911x
  30000000-33ffffff : System RAM
    30084000-30375fff : Kernel text
    30376000-303c723e : Kernel data
  38000000-3bffffff : System RAM
49000000-490fffff : s3c2410-ohci
  49000000-490fffff : ohci_hcd
49800000-498fffff : s3c2410-usbgadget
4a800000-4a801000 : s3c-hsmmc.1
  4a800000-4a801000 : s3c-hsmmc
4ac00000-4ac01000 : s3c-hsmmc.0
  4ac00000-4ac01000 : s3c-hsmmc
4b800000-4b802000 : s3c-ide.0
4c800000-4c8fffff : s3c-lcd
4d800000-4d8fffff : s3c-camif
4e000000-4e0fffff : s3c2410-nand
  4e000000-4e0fffff : s3c-nand
50000000-50003fff : s3c2440-uart.0
  50000000-500000ff : s3c2440-uart
50004000-50007fff : s3c2440-uart.1
  50004000-500040ff : s3c2440-uart
50008000-5000bfff : s3c2440-uart.2
  50008000-500080ff : s3c2440-uart
52000000-520fffff : s3c-spi.0
  52000000-520fffff : s3c-spi
53000000-53000fff : s3c2410-wdt
  53000000-53000fff : s3c2410-wdt
54000000-54000fff : s3c2410-i2c
  54000000-54000fff : s3c2410-i2c
55000000-55000fff : s3c2410-iis
57005000-570050ff : s3c2410-rtc
  57005000-570050ff : s3c2410-rtc
58000000-58000fff : s3c2410-adc
70100000-70100fff : onenand
f0300000-f03fffff : s3c-lcd
 
[B]cat /proc/interrupts 
[/B]           CPU0
 17:          1    s3c-ext0  s3c-hsmmc
 30:     175416         s3c  S3C2410 Timer Tick
 36:        123         s3c  s3c-hsmmc
 37:          7         s3c  s3c-hsmmc
 38:        150         s3c  s3c-spi
 42:     532558         s3c  ohci_hcd:usb1
 43:      96045         s3c  s3c2410-i2c
 48:          0     s3c-ext  enc28j60
 51:          1     s3c-ext  power_button
 52:         73     s3c-ext  dw-keypad
 53:        104     s3c-ext  dw-keypad
 54:         48     s3c-ext  dw-keypad
 55:         17     s3c-ext  dw-keypad
 56:         71     s3c-ext  dw-keypad
 57:         26     s3c-ext  dw-keypad
 58:         15     s3c-ext  dw-keypad
 59:         11     s3c-ext  dw-keypad
 73:          0   s3c-uart1  s3c2440-uart
 74:       3160   s3c-uart1  s3c2440-uart
 86:      57524           -  s3c-lcd
 97:          0           -  s3c2410-wdt
 98:          0           -  AC97
Err:          0

---

### Post by SteffenBaier on 2010-09-30
> **alchark said:**
>  Can you read /etc/passwd and have you got /etc/shadow? Have you tried sudo?
 
**passwd:**
 
```
root::0:0:root:/root:/bin/sh
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:100:sync:/bin:/bin/sync
mail:x:8:8:mail:/var/spool/mail:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
operator:x:37:37:Operator:/var:/bin/sh
sshd:x:103:99:Operator:/var:/bin/sh
nobody:x:99:99:nobody:/home:/bin/sh
default:x:1000:1000:Default non-root user:/home/default:/bin/sh
geveno:x:1001:1001:Linux User,,,:/home/geveno:/bin/sh
sshd:x:2:2:sshd:/sbin:
```
 
**shadow:**
```
root:$1$GR8b9sj8$Ing16n6h6awasaMQOOAH5/:10933:0:99999:7:::
bin:*:10933:0:99999:7:::
daemon:*:10933:0:99999:7:::
adm:*:10933:0:99999:7:::
lp:*:10933:0:99999:7:::
sync:*:10933:0:99999:7:::
shutdown:*:10933:0:99999:7:::
halt:*:10933:0:99999:7:::
uucp:*:10933:0:99999:7:::
operator:*:10933:0:99999:7:::
nobody:*:10933:0:99999:7:::
default::10933:0:99999:7:::
geveno:$1$d0G3xTY8$IITzv8p9ejGKA4A/cKFtj0:0:0:99999:7:::
```

---

### Post by PrFaas on 2010-09-30
> **DonutFUN said:**
> So I found something Kind of interesting out tonight, I have two VT8500 (neither are wm's or 05's) and even though they are the same, they are both different, there is one micro chip that on one is on the little removeable (Ram type) card, and on the other its sottered to teh board, and its obvious that it can be put in either spot on either, ill post pictures to show you what chip and where I'm talking about

I hope its obvious which chip I'm talking about

As far as i've been able to determine, the chip you're referring to is the 2 GigaBytes 'disk' (flash-disk) chip. Interesting to know that both are used sometimes. I don't know if there will be any difference between them: I've been thinking about putting a 2-nd 'disk'-chip on the 'spare' location in an attempt to increase the 'disk-space' of the machines....

---

### Post by alchark on 2010-10-01
> **SteffenBaier said:**
> **cat /proc/cpuinfo**
Processor : ARM926EJ-S rev 5 (v5l)
BogoMIPS : 199.47
Features : swp half fastmult edsp java 
CPU implementer : 0x41
CPU architecture: 5TEJ
CPU variant : 0x0
CPU part : 0x926
CPU revision : 5
Cache type : write-back
Cache clean : cp15 c7 ops
Cache lockdown : format C
Cache format : Harvard
I size  : 16384
I assoc  : 4
I line length : 32
I sets  : 128
D size  : 16384
D assoc  : 4
D line length : 32
D sets  : 128
Hardware : SMDK2450
Revision : 0000
Serial  : 0000000000000000

So the hardware seems to be a standard Samsung platform. You could use just any recent kernel and select ARCH_S3C2410 in configuration to make it work. Have you managed to get root access? Probably yes, as you are reading /etc/shadow :) If so, then just try to dump and examine the contents of mtd0 and mtd1 to get an idea of what kind of kernel image your bootloader expects and flash an appropriate replacement to mtd1.

However, I would strongly advise to get serial/telnet access to the bootloader before replacing the kernel/rootfs and JTAG before touching the bootloader itself.

Upd: Also note the fact that unpatched upstream kernels do not support YAFFS2, so you would need to take care about your root FS as well.

---

### Post by SteffenBaier on 2010-10-01
> **alchark said:**
> So the hardware seems to be a standard Samsung platform. You could use just any recent kernel and select ARCH_S3C2410 in configuration to make it work. Have you managed to get root access? Probably yes, as you are reading /etc/shadow :) If so, then just try to dump and examine the contents of mtd0 and mtd1 to get an idea of what kind of kernel image your bootloader expects and flash an appropriate replacement to mtd1.
 
However, I would strongly advise to get serial/telnet access to the bootloader before replacing the kernel/rootfs and JTAG before touching the bootloader itself.
 
Upd: Also note the fact that unpatched upstream kernels do not support YAFFS2, so you would need to take care about your root FS as well.
 
Sorry Dude, but I am not a Linux Guru ;-) Is just wanted to share the Information so maybe someone else has an Idea... The Booting of the SD Card via the script folder as on the other Units seems not to work , at least not with their Data on it ..
 
THX
 
Steff
 
PS: Yes, the shell has root access

---

### Post by alchark on 2010-10-01
> **SteffenBaier said:**
> Sorry Dude, but I am not a Linux Guru ;-) Is just wanted to share the Information so maybe someone else has an Idea... The Booting of the SD Card via the script folder as on the other Units seems not to work , at least not with their Data on it ..
 
THX
 
Steff
 
PS: Yes, the shell has root access
It will not boot, as the kernels that you were most probably trying to put on the card are for different hardware. In ARM world this is checked very early in kernel initialization process, so it will not even show you any error message except over serial console (if the configuration allows).

Furthermore, all of this scriptcmd stuff is only suitable for the U-boot bootloader, and your machine may well use something else (and thus need different tricks).

Anyway, thanks for the info :)

---

### Post by SteffenBaier on 2010-10-01
> **alchark said:**
>  
Furthermore, all of this scriptcmd stuff is only suitable for the U-boot bootloader, and your machine may well use something else (and thus need different tricks).
 
Anyway, thanks for the info :)
 
Is there any way to access the Bootloader once the machine is running to gather this data?
 
Steff

---

### Post by DonutFUN on 2010-10-01
> **PrFaas said:**
> As far as i've been able to determine, the chip you're referring to is the 2 GigaBytes 'disk' (flash-disk) chip. Interesting to know that both are used sometimes. I don't know if there will be any difference between them: I've been thinking about putting a 2-nd 'disk'-chip on the 'spare' location in an attempt to increase the 'disk-space' of the machines....


I don't think I said it the way I should have, what I was saying was on one it was on the board, on the other it was on the chip, and I did try to trade the two ram type removable chips, but it didn't work to mix-match either way sadly.

---

### Post by DonutFUN on 2010-10-02
On a completely unrelated subject, for some of you who have read this for a while may have a read my posts earlier about how my battery sencor is fried, and because of that the batter drains itself over a day or so if not plugged ing, so I was thinking i could put a switch on the batteries wire to stop it from doing that, but what I want to know is if I do that, would it hurt it for me to leave it off while plugged into the power adapter? or say if I take out the battery would it hurt it to have it pluged in with no battery?
 
Thanks
-DonutFUN

---

### Post by alchark on 2010-10-02
> **SteffenBaier said:**
> Is there any way to access the Bootloader once the machine is running to gather this data?
The bootloader shuts down after starting the kernel. You can, however, dump the contents of mtd0 and examine the image with hexdump or strings to get an idea what it is.

---

### Post by DonutFUN on 2010-10-09
so, no one answered and I wanted to add something
If i take the battery out and just have it plugged in to the wall will it hurt?
and aslo will it hurt it at all if i take out/put a switch to cut the power to the wifi?

---

### Post by alchark on 2010-10-10
> **DonutFUN said:**
> so, no one answered and I wanted to add something
If i take the battery out and just have it plugged in to the wall will it hurt?
and aslo will it hurt it at all if i take out/put a switch to cut the power to the wifi?
In principle, it should be ok, especially if you leave the device on (to maintain some load). However, some power converters suffer when powered up without load, so you'd better check whether any chips get overheated or something. Removing wifi should be perfectly fine, as it's no more than a USB dongle taken out of its case and attached inside your device.

Note also that your battery discharge issue needs not be a result of any specific hardware fault. These SoC's just do not really cut all the power when OS requests a shutdown (at least RTC remains powered up, and some other parts may also do).

---

### Post by DonutFUN on 2010-10-10
Ok, Thank you for the info

---

### Post by WendyB on 2010-10-11
I have a EasyPC E700 with VT8500 chip. I tried the Linux version for this CPU but al I get is a black screen partly with white lines.

I have managed to open it and made pictures:
[http://www.savage-elve.net/pub/pic_344004.JPG](http://www.savage-elve.net/pub/pic_344004.JPG)
[http://www.savage-elve.net/pub/pic_344005.JPG](http://www.savage-elve.net/pub/pic_344005.JPG)
[http://www.savage-elve.net/pub/pic_344006.JPG](http://www.savage-elve.net/pub/pic_344006.JPG)

(I also asked the same question on the Nextvolume forums, but this thread seems to more alive)

---

### Post by lemonjoe on 2010-10-12
Hello.
I'm install Debian for the netbook (wm8505) but i can't use GSM/GPRS/EDGE/3G-modem with this system. For my opinion, module usbserial isn't work in that system (in kernel).
Say me, please, how to run the modem in debian? What you need to do?
[COLOR=#000000]Sorry for my english, I'm not a native speaker.[/COLOR]

---

### Post by alchark on 2010-10-12
> **WendyB said:**
> I have a EasyPC E700 with VT8500 chip. I tried the Linux version for this CPU but al I get is a black screen partly with white lines.

I have managed to open it and made pictures:
[http://www.savage-elve.net/pub/pic_344004.JPG](http://www.savage-elve.net/pub/pic_344004.JPG)
[http://www.savage-elve.net/pub/pic_344005.JPG](http://www.savage-elve.net/pub/pic_344005.JPG)
[http://www.savage-elve.net/pub/pic_344006.JPG](http://www.savage-elve.net/pub/pic_344006.JPG)

(I also asked the same question on the Nextvolume forums, but this thread seems to more alive)
The board is identical to mine, so it could be expected to work :)

Which Linux did you try? Current open-source development is being done at [http://gitorious.org/linux-on-via-vt8500/vt8500-kernel](http://gitorious.org/linux-on-via-vt8500/vt8500-kernel) (or at least it's the only place I know of:)), while the only vendor-provided kernel is the blobbed 2.6.10 that Nextvolume has made available. You may also consult this Google Group for some info: [http://groups.google.com/group/vt8500-wm8505-linux-kernel](http://groups.google.com/group/vt8500-wm8505-linux-kernel)

If you're using Nextvolume's EasyPC distribution as-is, then you might just be too impatient, as it took quite some time to boot when I tried it (seeming to have hung up).

---

### Post by DonutFUN on 2010-10-15
I was wondering, I've heard people say when they got these they had wce5 instead of 6 ce6, does anyone here have an installer for windows ce 5 for the vt8500, I'm curious to try it if someone does for some programs I'm trying to get running.

---

### Post by WendyB on 2010-10-15
> **alchark said:**
> The board is identical to mine, so it could be expected to work :)

Which Linux did you try? Current open-source development is being done at [http://gitorious.org/linux-on-via-vt8500/vt8500-kernel](http://gitorious.org/linux-on-via-vt8500/vt8500-kernel) (or at least it's the only place I know of:)), while the only vendor-provided kernel is the blobbed 2.6.10 that Nextvolume has made available. You may also consult this Google Group for some info: [http://groups.google.com/group/vt8500-wm8505-linux-kernel](http://groups.google.com/group/vt8500-wm8505-linux-kernel)

If you're using Nextvolume's EasyPC distribution as-is, then you might just be too impatient, as it took quite some time to boot when I tried it (seeming to have hung up).
He, thanks for the resources. I will have a look at it.

I'm using Nextvolumes kernel. What do you mean with patient? I mean 5 minutes or so? Or longer?

---

### Post by alchark on 2010-10-17
> **WendyB said:**
> He, thanks for the resources. I will have a look at it.
 
I'm using Nextvolumes kernel. What do you mean with patient? I mean 5 minutes or so? Or longer?
5-10 minutes should have been enough, probably... You may try to play a bit with the kernel cmdline in scriptcmd and/or get a serial console to see what is going on.
 
The strange stripes in the lower part of the screen are drawn by the bootloader with Nextvolume's stock scriptcmd (namely, the mw.l commands at the end). If the screen then blanks, it should imply that the kernel has reinitialized LCD controller registers. You might have some problems with the root fs afterwards, which would prevent it from finishing the boot.

---

### Post by alchark on 2010-10-17
> **lemonjoe said:**
> Hello.
I'm install Debian for the netbook (wm8505) but i can't use GSM/GPRS/EDGE/3G-modem with this system. For my opinion, module usbserial isn't work in that system (in kernel).
Say me, please, how to run the modem in debian? What you need to do?
[COLOR=#000000]Sorry for my english, I'm not a native speaker.[/COLOR]
As soon as you have sources of your kernel version downloaded and unpacked,  getting it to work is in no way different on WM8505 from the good old x86 or whatever else. You'll need to either recompile the kernel image with the required drivers built in or compile them as modules and use `make modules_install`. For the latter option you need to follow your stock kernel configuration as closely as possible, otherwise the modules may fail to load.
 
Compiling a kernel on the device itself would take ages though, so you should consider getting a cross-toolchain for ARMv5 on x86 (e.g. from CodeSourcery) and compiling the kernel on your PC with `make ARCH=arm CROSS_COMPILE=/path_to_toolchain_bins/arm-eabi-` or similar.

---

### Post by DonutFUN on 2010-10-19
They've started porting Ubuntu to ARM!!!!
[http://www.linuxfordevices.com/c/a/News/Ubuntu-ported-to-ARM/](http://www.linuxfordevices.com/c/a/News/Ubuntu-ported-to-ARM/)

---

### Post by WendyB on 2010-10-22
> **WendyB said:**
> I have a EasyPC E700 with VT8500 chip. I tried the Linux version for this CPU but al I get is a black screen partly with white lines.

I have managed to open it and made pictures:
[http://www.savage-elve.net/pub/pic_344004.JPG](http://www.savage-elve.net/pub/pic_344004.JPG)
[http://www.savage-elve.net/pub/pic_344005.JPG](http://www.savage-elve.net/pub/pic_344005.JPG)
[http://www.savage-elve.net/pub/pic_344006.JPG](http://www.savage-elve.net/pub/pic_344006.JPG)

(I also asked the same question on the Nextvolume forums, but this thread seems to more alive)

I wrote down some numbers which might be difficult to read on the pictures:
BV07_A_LED_V2.0
2009-03-24
E 316362

s/n BV07-A-8500V1 
3094907943

BV07_A_8500_IO_V1.3
2009.09.26

some of the chips on the board:

VIA VT8500

Samsung 940

VIA VT1613

Pulse H1102NL

VIA VT6103x

GL850A

---

### Post by thi_santos on 2010-10-25
[LEFT][SIZE=4]Hello I have the card and the VIA VT8500 BV07_A_8500_IO_V1.3.[/SIZE]
[SIZE=4]I want a favor from someone in the forum that has the same pc that even with my windows CE installed. I want to copy the Windows folder and send me by mail because I need it to re-install the system is not working because the wifi and sound. I have this folder as the original drives.[/SIZE]
[SIZE=4]Who could do this for me my email is[/SIZE]
[SIZE=4]thiago@tecpontintas.com.br or [EMAIL="garmin_gps@hotmail.com"]garmin_gps@hotmail.com[/EMAIL].[/SIZE]
[SIZE=4]sorry my English is that I am Brazilian and I speak only Portuguese.[/SIZE]
[SIZE=4]Thanks

[/SIZE]If you can not someone get me those original files from windows, possesses some tutorial here explaining how to install Linux in 8500? because I do not have much knowledge on the subject
[/LEFT]

---

### Post by dario_ on 2010-10-27
> **alchark said:**
> 
The strange stripes in the lower part of the screen are drawn by the bootloader with Nextvolume's stock scriptcmd (namely, the mw.l commands at the end). If the screen then blanks, it should imply that the kernel has reinitialized LCD controller registers. You might have some problems with the root fs afterwards, which would prevent it from finishing the boot.

Hello,

I have the last problem you described. The boot sequences freezes at last, while opening the initial console...

I copy the last lines I see:

Waiting 10sec before mounting root device...
VFS: Mounted root (ext2 filesystem) readonly.
Freeing init memory: 112K
Warning: unable to open an initial console.
Kernel panic - not syncing: No init found.  Try passing init= option to kernel.

I'm really new to Linux, I don't know how to solve this, i hope someone can [COLOR=#000000]magnanimously help me :). 
[/COLOR][COLOR=#000000]Thanks in advance[/COLOR]!
[COLOR=#000000]
[/COLOR]

---

### Post by alchark on 2010-10-28
> **dario_ said:**
> Hello,

I have the last problem you described. The boot sequences freezes at last, while opening the initial console...

I copy the last lines I see:

Waiting 10sec before mounting root device...
VFS: Mounted root (ext2 filesystem) readonly.
Freeing init memory: 112K
Warning: unable to open an initial console.
Kernel panic - not syncing: No init found.  Try passing init= option to kernel.

I'm really new to Linux, I don't know how to solve this, i hope someone can [COLOR=#000000]magnanimously help me :). 
[/COLOR][COLOR=#000000]Thanks in advance[/COLOR]!
[COLOR=#000000]
[/COLOR]
So, your root filesystem layout is somehow broken (or you are trying to use some wrong partition, not the one where your crucial boot files are). If you wish to use Nextvolume's distribution, you have to unpack the ext2part archive to the second partition on the SD card, pre-formatting that as ext2. It seems that the format is correct, as it at least mounts, but your files are not there. Make sure that the dev/, bin/, proc/, sys/, sbin/, lib/ etc folders appear in the root of your second partition.

---

### Post by dario_ on 2010-10-28
> **alchark said:**
> So, your root filesystem layout is somehow broken (or you are trying to use some wrong partition, not the one where your crucial boot files are). If you wish to use Nextvolume's distribution, you have to unpack the ext2part archive to the second partition on the SD card, pre-formatting that as ext2. It seems that the format is correct, as it at least mounts, but your files are not there. Make sure that the dev/, bin/, proc/, sys/, sbin/, lib/ etc folders appear in the root of your second partition.

Thank you, I tried unpacking the archive under Puppy Linux instead of Ubuntu, and at last I logged in Easypc Linux :P! perhaps the last time I unpacked as non-root user, I don't know... so, thanks again!

Now I've an other problem: once inside i can't do anything![COLOR=#000000] [/COLOR]Commands  such as "free" and "cd /..." work, but "ifconfig", "udhcpc",  "route add default gw 192.168 ...", all reply:
 
"sh: ifconfig: not found"

and similar.
XEmacs starts if launched from the menu of BusyBox, not if launched from xterm ...
So, I can't do really anything! I'd like to have a lan-internet connection working, and apt-get to install something like Lxde, if possible... is somehow possible?

---

### Post by alchark on 2010-10-29
> **dario_ said:**
> perhaps the last time I unpacked as non-root user, I don't know... so, thanks again!
Yes, that was important, as device nodes can only be created by root, and some permissions cannot be preserved by unpacking as a normal user. Also, it is advisable to use '-p' option to tar to ensure correct permissions.

> **dario_ said:**
> 
Now I've an other problem: once inside i can't do anything![COLOR=#000000] [/COLOR]Commands  such as "free" and "cd /..." work, but "ifconfig", "udhcpc",  "route add default gw 192.168 ...", all reply:
 
"sh: ifconfig: not found"

and similar.
XEmacs starts if launched from the menu of BusyBox, not if launched from xterm ...
So, I can't do really anything! I'd like to have a lan-internet connection working, and apt-get to install something like Lxde, if possible... is somehow possible?
Actually, your options are quite limited by the veeeeeeery old kernel version released by VIA. It does not support ARM EABI, so there are problems with getting floating-point code to work. Further, it is too old for any reasonable version of udev, etc. So, you have to struggle hard and compile the required packages yourself (and will fail quite often). Try the Debian ARM port, though (NOT armel: that one is for EABI), but I'd be surprised if it worked :)

If you can afford using a USB drive as a root fs for now and only WiFi for networking, then you should probably consider testing our [development kernel version]("http://gitorious.org/linux-on-via-vt8500/vt8500-kernel");) At least, it supports modern userspaces.

---

### Post by dario_ on 2010-10-29
> **alchark said:**
> Actually, your options are quite limited by the veeeeeeery old kernel version released by VIA. It does not support ARM EABI, so there are problems with getting floating-point code to work. Further, it is too old for any reasonable version of udev, etc. So, you have to struggle hard and compile the required packages yourself (and will fail quite often). Try the Debian ARM port, though (NOT armel: that one is for EABI), but I'd be surprised if it worked :)

If you can afford using a USB drive as a root fs for now and only WiFi for networking, then you should probably consider testing our [development kernel version]("http://gitorious.org/linux-on-via-vt8500/vt8500-kernel");) At least, it supports modern userspaces.

Thanks for the explication. Yes, I'd like to try the development kernel, I downloaded from the source tree but I'm not able to: I can barely unpack a folder :) Could you help me? Some kind of god will reward you for your [COLOR=#000000]courtesy[/COLOR], sure!:P

---

### Post by alchark on 2010-10-29
> **dario_ said:**
> Thanks for the explication. Yes, I'd like to try the development kernel, I downloaded from the source tree but I'm not able to: I can barely unpack a folder :) Could you help me? Some kind of god will reward you for your [COLOR=#000000]courtesy[/COLOR], sure!:P
I've started writing down the instructions in the [project's Wiki]("http://gitorious.org/linux-on-via-vt8500/pages/Home"), you may check those out.

---

### Post by arievanleyen on 2010-11-02
I have experience with Linux for about 20 years but my knowledge is just users-knowledge. Apart from that I have thourough knowledge of programming in C++, Pascal and Forth.

On my netbook I have installed the Linux version that is distributed on your site. I have played around with it, installed a desktop manager, wifi and a script to update the hardware clock through ntp.

There are two things that I am missing though and that is the battery status and audio. These seem not to be implemented yet and I would like to try to get it working.

So I have downloaded the kernel sources and would like first of all to compile these and see if I get a working kernel on my netbook. However, how do I compile it? I remember that in the beginning years of Linux it had to be done through 'make config' - 'make modules' - 'make install'.

I have extracted the archive and ended up with 2 directories: 'common' and 'via_obj.arm_v5t-2629.01'. The last directory contains some compiled drivers and the first one the kernel. 
But how to proceed afterwards? When I open a terminal and go to the common folder and enter 'make config' I end up with an error.

Does anybody ever tried to compile these sources and how did they do it?

---

### Post by alchark on 2010-11-03
> **arievanleyen said:**
> There are two things that I am missing though and that is the battery status and audio. These seem not to be implemented yet and I would like to try to get it working.
You are right, these are missing from VIA's sources. Audio is there, but the object file is compiled with a wrong ABI, so it won't link with the rest of the kernel.

> **arievanleyen said:**
> So I have downloaded the kernel sources and would like first of all to compile these and see if I get a working kernel on my netbook. However, how do I compile it? I remember that in the beginning years of Linux it had to be done through 'make config' - 'make modules' - 'make install'.

I have extracted the archive and ended up with 2 directories: 'common' and 'via_obj.arm_v5t-2629.01'. The last directory contains some compiled drivers and the first one the kernel. 
But how to proceed afterwards? When I open a terminal and go to the common folder and enter 'make config' I end up with an error.

Does anybody ever tried to compile these sources and how did they do it?
It can be compiled using the [toolchain provided by nextvolume]("http://tails92.sepwich.com/easypc_linux/armv5t-softfloat-linux-gnu-toolchain.tgz"). You would then issue something along the lines of ```
export ARCH=arm
export CROSS_COMPILE=/path/to/armv5t-softfloat-linux-gnu-
make menuconfig
make -j8 uImage modules
```

Note, however, that VIA's kernel is too old for any real use with modern software. Your programming efforts could probably be better directed towards an up-to-date kernel tree, so you may wish to consider [this project]("http://gitorious.org/linux-on-via-vt8500") instead. There's also a Wiki page with some basic building instructions.

NB: One can still use nextvolume's distro with a modern kernel (with appropriate configuration options), but not vice versa.

---

### Post by dario_ on 2010-11-03
Hi,
i'm sorry for having answered so in late. I tried to download the sources and compile with the nextvolume's toolchain you provided. I tried also to follow the wiki, but is too difficult for my competences. I'll try again when i'll have time enough to spend about it..

> On my netbook I have installed the Linux version that is distributed on  your site. I have played around with it, installed a desktop manager,  wifi and a script to update the hardware clock through ntp.

Can I have the address of this site? I'll try that too.
Thanks for all :)

---

### Post by memz on 2010-11-04
Hello!

I realize this might be a bit offtopic, but considering there seem to be a lot of 7" chinese netbook users here, I hope I'll get more feedback here than anywhere else.
After looking around I read there seem to be problems with the battery and the lifespan of these devices. 
What are your experiences with the battery - did it die quickly or does it still work? What about the netbook -  does it boot normaly or is it somehow corrupted?

Thank you. I am considering about ordering one frome dealextreme and just wanted to know this before actually buying it and installing linux. :)

---

### Post by Jenn Gee on 2010-11-08
Hello, I have one of these mini notebooks, and I am having a hard time trying to get online with the wifi.  Any suggestions?

---

### Post by waclavr on 2010-11-12
Hello I am having problems instaling enything in my mini laptop 7'' 2gb flash drive CPU: via 8505.
I tried to replace  WinCE to Android but something went  wrong. I was looking in google for solutions but none of them does not  help. So far I managed to get back to the factory settings  (all in  Chinese, no wifi, etc) I think the problem is that when you install  WinCE 6.0 system it is getting ready to format Flash Disk, a error pops  up "FormatVolume () fails" and "System Disk existed no" 

Does anyone have any solution?

---

### Post by WendyB on 2010-11-30
I have finally managed to compile the kernel from the gitorious site according to the instructions on the same site.
I have combined it with Nextvolumes distro. I had to change several nodes in /dev by hand and change the root to sda1 (USB-stick) but now it works
even X starts up (after 5 minutes or so)

biggest problem is that ethernet isn't working
and the touchpad neither

I don't know if there's a driver for internet and which I have to select

i tried Gentoo one time, but it gave me immediately a kernel panic. I will try that later

---

### Post by alchark on 2010-12-02
> **WendyB said:**
> I have finally managed to compile the kernel from the gitorious site according to the instructions on the same site.
I have combined it with Nextvolumes distro. I had to change several nodes in /dev by hand and change the root to sda1 (USB-stick) but now it works
even X starts up (after 5 minutes or so)

biggest problem is that ethernet isn't working
and the touchpad neither

I don't know if there's a driver for internet and which I have to select

i tried Gentoo one time, but it gave me immediately a kernel panic. I will try that later

WiFi should somehow work (it's a Ralink RT2870 USB stick typically, so look at that driver. You'll also need the correct firmware). Ethernet is missing, true.

My touchpad works with just standard PS/2 drivers (VT8500 here) - just make sure to select i8042 support and the relevant drivers for input. You may also have some hardware differences, though.

PS: Just checked the timing: my device gets into a working (and even usable!) KDE 4.5 desktop in the same 5 minutes with a Gentoo build ;) With dash as a shell it's somewhat faster. LXDE is a lot faster. I could upload my binary packages somewhere if needed.

How did you manage to crash the kernel from userspace? :)

---

### Post by alchark on 2010-12-02
Just in case, I've uploaded the binary packages for my Gentoo build here: [http://gentoo.alchark.ru/packages/armv5tel/](http://gentoo.alchark.ru/packages/armv5tel/)

Make sure to mask Qt 4.7, as it contains a bug in harfbuzz that makes it segfault on ARM every time it tries to display a TrueType font (read: always).

---

### Post by WendyB on 2010-12-02
> **alchark said:**
> WiFi should somehow work (it's a Ralink RT2870 USB stick typically, so look at that driver. You'll also need the correct firmware). Ethernet is missing, true.

My touchpad works with just standard PS/2 drivers (VT8500 here) - just make sure to select i8042 support and the relevant drivers for input. You may also have some hardware differences, though.

PS: Just checked the timing: my device gets into a working (and even usable!) KDE 4.5 desktop in the same 5 minutes with a Gentoo build ;) With dash as a shell it's somewhat faster. LXDE is a lot faster. I could upload my binary packages somewhere if needed.

How did you manage to crash the kernel from userspace? :)
I will try that Ralink driver, thanks
The touchpad didn't work on Nextvolume's distro, but i don't know yet about my latest creation, because I haven't yet installed X

SD cards aren't working from Linux, yet? Or am I missing something.

How I crashed userspace? Well, simple: The kernel didn't support EABI and I wanted to boot from the arm5tel Gentoo stage3 ;)
So, matter of CPU instruction set.
Nextvlume's distro did without out it.

Is there a way to find all the used chipsets, either by list on internet or using software tools ?

right now I'm using the gcc of the arm distro in a chroot environment using the binfmt_misc Linux module. This is quite slow, is this the most efficient way ?

For me this is a nice project to learn about cross-compiling and embedded Linux

---

### Post by dapegon on 2010-12-03
That's a large thread!

But very interesting, and useful too. Sadly, I couldn't managed to install anything in my [netbook]("http://www.prixton.com/prixtonjoomla/index.php?option=com_content&view=article&id=31:netbook-smart&catid=27:mini-portatiles&Itemid=41"). I've tried debian, android and wince...

DEBIAN*
It was difficult, but thanks to this thread I finally managed to get to the "Erase SD Card" message. Unfortunately, It will not boot on reboot (?)

ANDROID
Installer goes swiftly, with no problem at all. But... it will not boot on reboot (?)

WINCE
Installer doesn't go further than the first wince desktop, in chinese, returning a "FormatVolume() fails" and a "System Disk no existed" messages instead of installing the system (?)

I'm struck. Looking for extra information... maybe a diferent proccesor, I don't know (wince says that's a WMT ARM-WM8505)

Any help would be very appreciated...

PD: In the end, I did not find any solution, so I returned the machine :(

---

### Post by WendyB on 2010-12-05
I can't figure out how to make the network working.
The device (whether eth0, wlan0 or ra0) isn't in /dev
lsusb doesn't show any devices (except for 3 expected devices: root-hub, hub and usb-stick)


if I have a a working Gentoo install I will put it in a zip for anyone to download and to try

---

### Post by alchark on 2010-12-07
> **WendyB said:**
> I can't figure out how to make the network working.
The device (whether eth0, wlan0 or ra0) isn't in /dev
lsusb doesn't show any devices (except for 3 expected devices: root-hub, hub and usb-stick)

Try to enable some of the GPIO pins. On my device power to the WiFi part is physically triggered by GPIO3, yours may be different.

---

### Post by Enee on 2010-12-07
Hai all in linux red hart is oly most of them using y y 

-------------------------------------------
[URL="http://www.**************************"]
[/URL]

---

### Post by WendyB on 2010-12-07
> **alchark said:**
> Try to enable some of the GPIO pins. On my device power to the WiFi part is physically triggered by GPIO3, yours may be different.
Many thanks, that was exactly the clue, I Needed. Now I can continue. :cool:

---

### Post by cthriftfl on 2010-12-10
> **abrasive said:**
> My easypc had the SD write bug - but detected cards fine.
I think one of the motherboard revisions connects the SD shield (switch case) to the wrong potential, so the sense line ends up always high. I fixed it on mine by removing the feed resistor and grounding the case/common.
I didn't think to try flipping the switch to WP - which would leave the line floating, IIRC... hopefully there is a pull-up/down on it somewhere else! Having reversed the logic level in software vs. hardware seems most likely...

Does anyone know which resistor Abrasive is referring to here?  The behavior I see in my WM8505 leads me to believe that I have a similar problem and can't write the the card.  This would be an easy fix if that's the case.

---

### Post by gymophett on 2010-12-14
So, I got my sister one of these for Christmas and I tried to put Android on it. It says the install goes fine, then it says to restart it and it just sits there.. I think this is where I mess up. I hold the off button until it turns off, then turn it back on, but only have a black screen. What am I doing wrong?

---

### Post by SpiK369 on 2010-12-19
New Kernel for internet key.
Kernel installed Linux armbook 2.6.29-00236-g4f8dbbb-dirty #22 Wed Apr 7 14:15:24 CST 2010 armv5tejl GNU/Linux

now I'm try to compile a new kernel with usb driver for modem (internet key)

but after finish I obtain a uImage file and not uzImage.bin I perform the following step:

1) mount /dev/mmcblk0p1 /mnt/sd
2) cp /usr/src/linux-on-via-vt8500-vt8500-kernel-vt8500/arch/arm/boot/uImage  /mnt/sd/script/uzImage.bin
3) reboot

but nothing black screen.

Can I help me to fix this problem.


thx in advanced

---

### Post by WendyB on 2010-12-20
Maybe this one works
(I'm still experimenting with the kernel config)

don't forget to install the kernel modules, not just only the uImage


I'm almost finished with my mostly working Gentoo install

---

### Post by alchark on 2010-12-20
> **WendyB said:**
> I'm almost finished with my mostly working Gentoo install
If you need advice, please ask. After all, I've already accomplished that, and you can even use my binary packages to relieve quite some pain without losing all of the satisfaction of installing a Gentoo system :)

---

### Post by SpiK369 on 2010-12-20
Thanks a lot for your response.

For the source file you suggest to use this: [http://tails92.sepwich.com/easypc_linux/linux-2.6.10-mv-vt8500.tar.gz](http://tails92.sepwich.com/easypc_linux/linux-2.6.10-mv-vt8500.tar.gz) or the other similar to vanilla.

thanks

Spike.

---

### Post by WendyB on 2010-12-20
Sorry, no.
The config I posted is for this kernel:
[http://gitorious.org/linux-on-via-vt8500](http://gitorious.org/linux-on-via-vt8500)

I got the black screen too on the kernel you mentioned

---

### Post by SpiK369 on 2010-12-21
Summary:

1) source kernel: v2.6.35-vt8500.tgz

2) use config file: kernel-easypc.config.zip 

3) make ARCH=arm CROSS_COMPILE=/usr/bin/arm-linux-gnueabi- uImage

4) make ARCH=arm CROSS_COMPILE=/usr/bin/arm-linux-gnueabi- modules

5) make ARCH=arm CROSS_COMPILE=/usr/bin/arm-linux-gnueabi- modules_install
    now i have the modules in /lib/modules/2.6.37-rc6-easypc

Now, i want to boot ONLY from SD card whithout flash internal flashsystem (i want preserve wince):

I have sd with two partition  fat and ext2, I can use easypc-linux-0.2.tar.gz that contain fatpart.tgz and ext2part.tgz files? 

If yes, why in the ext2part.tgz the file linuxrc is empty? How can create new one with my new kernel? And in sd fat partition is only necessary to overwrite the file uzImage.bin with my kernel linux-on-via-vt8500-vt8500-kernel/arch/arm/boot/uImage?

I need to copy the file modules /lib/modules/2.6.37-rc6-easypc in sd ext2 partition /lib/modules ?

Finally if I need the initramdisk how can create it and where a must copy in the sd ext2 partition? 

Thank in advanced

SpiK369

---

### Post by WendyB on 2010-12-21
You can read basic install instructions here:
[http://gitorious.org/linux-on-via-vt8500/pages/Home](http://gitorious.org/linux-on-via-vt8500/pages/Home)

I have used a Gentoo Linux distro for the other files.

This kernel doesn't yet support SD-cards (as far as I know) so after loading the kernel image it can't find the SD-card anymore. Therefore the Linux filesystem should be on a USB-stick which is spupported
kernelparameters, including bootdevice and initrd are defined in the scriptcmd file.

I think you can load an initrd file, either by changing the kernel commandline or using the kernel config option

And yes, copying the /lib/modules/2.6.xxxxx  directory to the USB-stick should do it

---

### Post by WendyB on 2010-12-21
> **alchark said:**
> If you need advice, please ask. After all, I've already accomplished that, and you can even use my binary packages to relieve quite some pain without losing all of the satisfaction of installing a Gentoo system :)
Thanks for your offer.
I'm still trying to make the wireless with WPA working.
I'm using the rt3070 driver from the Ralink site, changed the source code according to the readme and the Gentoo wiki. It runs, it works, but somehow it doesn't want to authorize with the AP

---

### Post by alchark on 2010-12-21
> **WendyB said:**
> Thanks for your offer.
I'm still trying to make the wireless with WPA working.
I'm using the rt3070 driver from the Ralink site, changed the source code according to the readme and the Gentoo wiki. It runs, it works, but somehow it doesn't want to authorize with the AP
I personally use the in-kernel driver (rt2800usb). It behaves quite strangely, but still it is somewhat usable (at least it authenticates fine, and with some patience you can download stuff over the link).

rt3070 from Ralink site is in bad shape. Its equivalent in staging is at least cleaned up a bit by the community, but still it breaks every now and then with new changes to the rest of the kernel, so I gave up on that.

PS You may also wish to try out compat-wireless, as there are some massive improvements scheduled for 2.6.38, which are not part of the kernel sources at Gitorious.

---

### Post by gymophett on 2010-12-24
Does no-one know how to get Android to work?
People seem to have gotten it working quite easily. It installs for me off of the SD card. I remove the card, and it says to reboot, so I hold the power off button, then turn it back on to a black screen..
Can someone please help ASAP? Christmas is tomorrow and it's for my sister. ):

---

### Post by gymophett on 2010-12-25
Okay, I can't get Android on it, but does anyone have the WinCE link?
I am looking through this thread but have yet to find it.

---

### Post by murr4y on 2010-12-25
Does anyone know if you can install Linux/Android on those netbooks with the "mw8505" processor with 600mhz?
I actually don't know if that's a typo there but there seem to be some tablets with that processor.

---

### Post by agashka on 2010-12-25
Hey guys I've been trying to get Android working on my EasyPC E700 (ARM926 - WM VT8500) I've downloaded the package from page 66, copied the script folder to the FAT formatted SD card, but once I start my netbook, it hangs to the "Windows CE loading" screen. Any tips to get rid of WIN CE asap?

---

### Post by banderkin80 on 2010-12-27
I have 8505 device with WinCE 6  with spanish language inside and this is terrible!!!
I think so. There is only one problem with installing Android on ours 7'' devices. After the inserting SD card with script we have nothing (all instructions at [https://sites.google.com/site/gyplace/home/informatica/how-to-install-android-on-smartbook-smartmedia-wm8505-and](https://sites.google.com/site/gyplace/home/informatica/how-to-install-android-on-smartbook-smartmedia-wm8505-and) done), just WinCE loading. Tell me, for dummy russian guy who solved this???!!! And sorry 4 my english

---

### Post by plymouthHemi on 2010-12-27
Hi everybody.

I have a mini netbook too, same as mentioned on this thread.
When i working to installation Debian Armel, I erased u-boot part on serial flash (EEON  F40-100GCP). Device doesn't boot any more. But when i connect with serial port, i can see w-loader result messages. Here is the w-load output:

```
WonderMedia Technologies, Inc.
W-Load Version : 0.17.00.00
ethaddr............found
```
That's all folks

Few month ago, I saw an article and picture about jtag-port for vt8505. But i can not find again.
Does anyone know where is the jtag pins? Does anyone have experience to use jtag on that?

Thanks ~ Fatih.

---

### Post by banderkin80 on 2010-12-28
> **dwinston91 said:**
> Also one thing that I found out on my machine, was a neat little program called SerialView.exe   It is located in the C:\Windows folder.  It shows a lot of information about your machine.  That is how I found out that Benign was the maker of the board that is in my machine...without opening it up.  

[COLOR=RoyalBlue]
[/COLOR]
  I had not this file in windows folder, but i copied it from one of the images from net. i'm starting it and saw the blank window without any info about system

---

### Post by WendyB on 2010-12-29
> **alchark said:**
> I personally use the in-kernel driver (rt2800usb). It behaves quite strangely, but still it is somewhat usable (at least it authenticates fine, and with some patience you can download stuff over the link).

rt3070 from Ralink site is in bad shape. Its equivalent in staging is at least cleaned up a bit by the community, but still it breaks every now and then with new changes to the rest of the kernel, so I gave up on that.

PS You may also wish to try out compat-wireless, as there are some massive improvements scheduled for 2.6.38, which are not part of the kernel sources at Gitorious.
I have tried all of your options. The in-kernel 3070sta driver doesn't support wpa_supplicant or iwpriv
the 2x00usb drivers don't work at all.
so I ended up again with the Ralink driver from the manufacturer.

It all seems to be memory related. I have cleaned up the system from unneeded services (like consolekit, networkmanager and policykit) and completely uninstalled networkmanager en wpa_supplicant. now it works quite reliable.

Before, when I did this:
ifconfig ra0 up
 I got this in syslog:

```
Dec 27 22:42:10 easypc rc-scripts: net.ra0 is not allowed to be hotplugged
Dec 27 22:42:23 easypc klogd: Allocate 8192 memory for BA reordering
Dec 27 22:42:23 easypc klogd: MAC_CSR0  [ Ver:Rev=0x30700201]
Dec 27 22:42:24 easypc klogd: <=== RtmpAsicLoadFirmware (status=0)
Dec 27 22:42:24 easypc klogd: --> RTMPAllocTxRxRingMemory
Dec 27 22:42:24 easypc klogd: --> NICInitTransmit
Dec 27 22:42:24 easypc klogd: ifconfig: page allocation failure. order:6, mode:0x20
Dec 27 22:42:24 easypc klogd: [<c002f7f8>] (unwind_backtrace+0x0/0xf4) from [<c0086aec>] (__alloc_pages_nodemask+0x4dc/0x59c)
Dec 27 22:42:24 easypc klogd: [<c0086aec>] (__alloc_pages_nodemask+0x4dc/0x59c) from [<c0030250>] (__dma_alloc+0x88/0x27c)
Dec 27 22:42:24 easypc klogd: [<c0030250>] (__dma_alloc+0x88/0x27c) from [<c00304c0>] (dma_alloc_coherent+0x50/0x5c)
Dec 27 22:42:24 easypc klogd: [<c00304c0>] (dma_alloc_coherent+0x50/0x5c) from [<bf344e04>] (RTMPAllocUsbBulkBufStruct+0x44/0xb0 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf344e04>] (RTMPAllocUsbBulkBufStruct+0x44/0xb0 [rt3370sta]) from [<bf344f1c>] (NICInitTransmit+0xac/0x4f8 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf344f1c>] (NICInitTransmit+0xac/0x4f8 [rt3370sta]) from [<bf3454fc>] (RTMPAllocTxRxRingMemory+0x40/0xc8 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf3454fc>] (RTMPAllocTxRxRingMemory+0x40/0xc8 [rt3370sta]) from [<bf333964>] (rt28xx_init+0xe4/0x610 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf333964>] (rt28xx_init+0xe4/0x610 [rt3370sta]) from [<bf340e78>] (rt28xx_open+0x3c/0xe4 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf340e78>] (rt28xx_open+0x3c/0xe4 [rt3370sta]) from [<bf341250>] (MainVirtualIF_open+0xec/0x160 [rt3370sta])
Dec 27 22:42:24 easypc klogd: [<bf341250>] (MainVirtualIF_open+0xec/0x160 [rt3370sta]) from [<c0247098>] (__dev_open+0xb0/0x100)
Dec 27 22:42:24 easypc klogd: [<c0247098>] (__dev_open+0xb0/0x100) from [<c0243b5c>] (__dev_change_flags+0x78/0x13c)
Dec 27 22:42:24 easypc klogd: [<c0243b5c>] (__dev_change_flags+0x78/0x13c) from [<c0246fb0>] (dev_change_flags+0x10/0x48)
Dec 27 22:42:24 easypc klogd: [<c0246fb0>] (dev_change_flags+0x10/0x48) from [<c029895c>] (devinet_ioctl+0x6e0/0x7c0)
Dec 27 22:42:24 easypc klogd: [<c029895c>] (devinet_ioctl+0x6e0/0x7c0) from [<c02335fc>] (sock_ioctl+0x74/0x26c)
Dec 27 22:42:24 easypc klogd: [<c02335fc>] (sock_ioctl+0x74/0x26c) from [<c00bd178>] (do_vfs_ioctl+0x7c/0x62c)
Dec 27 22:42:24 easypc klogd: [<c00bd178>] (do_vfs_ioctl+0x7c/0x62c) from [<c00bd760>] (sys_ioctl+0x38/0x60)
Dec 27 22:42:24 easypc klogd: [<c00bd760>] (sys_ioctl+0x38/0x60) from [<c0029dc0>] (ret_fast_syscall+0x0/0x2c)
Dec 27 22:42:24 easypc klogd: Mem-info:
Dec 27 22:42:24 easypc klogd: Normal per-cpu:
Dec 27 22:42:24 easypc klogd: CPU    0: hi:   18, btch:   3 usd:  17
Dec 27 22:42:24 easypc klogd: active_anon:59 inactive_anon:687 isolated_anon:2
Dec 27 22:42:24 easypc klogd:  active_file:1268 inactive_file:2775 isolated_file:24
Dec 27 22:42:24 easypc klogd:  unevictable:0 dirty:13 writeback:20 unstable:0
Dec 27 22:42:24 easypc klogd:  free:6745 slab_reclaimable:353 slab_unreclaimable:935
Dec 27 22:42:24 easypc klogd:  mapped:644 shmem:1 pagetables:121 bounce:0
Dec 27 22:42:24 easypc klogd: Normal free:26980kB min:1016kB low:1268kB high:1524kB active_anon:236kB inactive_anon:2748kB active_file:5072kB inactive_file:11100kB unevictable:0kB isolated(anon):8kB isolated(file):96kB present:65024kB mlocked:0kB dirty:52kB writeback:80kB mapped:2576kB shmem:4kB slab_reclaimable:1412kB slab_unreclaimable:3740kB kernel_stack:928kB pagetables:484kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:26 all_unreclaimable? no
Dec 27 22:42:24 easypc klogd: lowmem_reserve[]: 0 0
Dec 27 22:42:24 easypc klogd: Normal: 1961*4kB 1112*8kB 322*16kB 57*32kB 15*64kB 16*128kB 1*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 26980kB
Dec 27 22:42:24 easypc klogd: 4518 total pagecache pages
Dec 27 22:42:24 easypc klogd: 463 pages in swap cache
Dec 27 22:42:24 easypc klogd: Swap cache stats: add 19659, delete 19196, find 5580/7864
Dec 27 22:42:24 easypc klogd: Free swap  = 98516kB
Dec 27 22:42:24 easypc klogd: Total swap = 102396kB
Dec 27 22:42:24 easypc klogd: 16384 pages of RAM
Dec 27 22:42:24 easypc klogd: 7011 free pages
Dec 27 22:42:24 easypc klogd: 2147 reserved pages
Dec 27 22:42:24 easypc klogd: 1288 slab pages
Dec 27 22:42:24 easypc klogd: 1742 pages shared
Dec 27 22:42:24 easypc klogd: 460 pages swap cached
Dec 27 22:42:24 easypc klogd: <-- ERROR in Alloc Bulk buffer for HTTxContext!
Dec 27 22:42:24 easypc klogd: <-- RTMPAllocTxRxRingMemory, Status=3
Dec 27 22:42:24 easypc klogd: ERROR!!! RTMPAllocTxRxMemory failed, Status[=0x00000003]
Dec 27 22:42:24 easypc klogd: ---> RTMPFreeTxRxRingMemory
Dec 27 22:42:24 easypc klogd: <--- RTMPFreeTxRxRingMemory
Dec 27 22:42:24 easypc klogd: !!! rt28xx Initialized fail !!!
Dec 27 22:42:24 easypc klogd: rt28xx_open return fail!
```

---

### Post by BrooksEakin on 2010-12-30
So, I have tried to install numerous operating systems on my WM8508 machine, and all have been unsuccessful.

Debian: can't find extpart.tgz (and yes, I tried Abrasive's suggestion in post #720. When I try "mount /dev/mtdblock9 /mnt/mtd" I'm given an error message saying that mtdblock9 doesn't exist)

Android: numerous builds, when it says to remove SD card and reboot, I am rebooted to a blank screen.

WinCE: the "system disk no existed!" error

It's possible that I've done something wrong here, but I've been at this for days with numerous SD cards, and I've still had no luck. Is there any really obvious thing I've just been messing up all this time, or is it possible that I have a defective machine?

---

### Post by dario_ on 2010-12-30
> **WendyB said:**
> I have tried all of your options. The in-kernel 3070sta driver doesn't support wpa_supplicant or iwpriv
the 2x00usb drivers don't work at all.
so I ended up again with the Ralink driver from the manufacturer.

It all seems to be memory related. I have cleaned up the system from unneeded services (like consolekit, networkmanager and policykit) and completely uninstalled networkmanager en wpa_supplicant. now it works quite reliable.



Can I ask you if you think to share your distro, when working?
It would very usefull, for all us that can't make it ourselves!
Thank you, have a good time

---

### Post by WendyB on 2010-12-30
> **dario_ said:**
> Can I ask you if you think to share your distro, when working?
It would very usefull, for all us that can't make it ourselves!
Thank you, have a good time
Yes, that's my plan.
I even made a Trac project for it, already:
[http://trac.freya-webtechniek.nl/trac/Linux_VT8500](http://trac.freya-webtechniek.nl/trac/Linux_VT8500)

I hope to have a first release by the end of the week, or maybe first half of next week.

I'm just looking for a place to host a 500MB+ file. To start I will host it on some filesharing service.

---

### Post by WendyB on 2011-01-02
Here it is:

Hopefully all went well regarding permissions, device files and usernames
If not, please inform me.

Read the included readme before, please.

[http://www.filedropper.com/easypc-gentoo-wendy-preleasetar](http://www.filedropper.com/easypc-gentoo-wendy-preleasetar)

or even better:
[http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList](http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList)

---

### Post by Joe of loath on 2011-01-03
> **WendyB said:**
> 
I'm just looking for a place to host a 500MB+ file. To start I will host it on some filesharing service.

Create a dropbox account and put it in the 'public' folder :)

I won one of these on ebay today dead cheap as it was faulty. I got it for £36 (~55 USD) posted, as apparently it won't charge. Not a problem for me, I race radio controlled cars, so have a house full of batteries just waiting to go in, and power supplies + chargers to charge the battery it came with.

Anyway, I'm hoping to stick Debian on it. For those running Debian, what software are you running RE window manage/Desktop environment, file browser, music player etc. I know it's only got enough memory to run one of these at a time, but I have loads of old boxes, so I'm used to it.

---

### Post by omrip on 2011-01-06
Hey Wendy

*What is the size of the.bz2 file - every time I try to download it hangs on diffrent sizes-and I can't extract even the readme file
*once I got the full archive-whats next - what do I do?

---

### Post by WendyB on 2011-01-06
> **omrip said:**
> Hey Wendy

*What is the size of the.bz2 file - every time I try to download it hangs on diffrent sizes-and I can't extract even the readme file
*once I got the full archive-whats next - what do I do?
Hi omrip,

The filesize is 500MB. I will look for other ways to upload the file, like dropbox or maybe torrent

If you can't download, drop me a pb with your email and I will send it.

If you have the archive you have to extract one included file to an sd card and the other archive (WHILE BEING ROOT!) to a USB stick

edit:

try the dropboxlink:
[http://dl.dropbox.com/u/18154481/easypc-gentoo-wendy-prelease.tar.bz2](http://dl.dropbox.com/u/18154481/easypc-gentoo-wendy-prelease.tar.bz2)

---

### Post by emostarxd on 2011-01-08
How to upload this disto to the netbook?
VT8500 (~240mhz) version doesn't boot from SD card.
It has bootloader (F1) with password 'zte' and I have only erase options...:(

---

### Post by WendyB on 2011-01-11
> **emostarxd said:**
> How to upload this disto to the netbook?
VT8500 (~240mhz) version doesn't boot from SD card.
It has bootloader (F1) with password 'zte' and I have only erase options...:(
Have a look here: [http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/InstallingThisLinux](http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/InstallingThisLinux)

---

### Post by DonutFUN on 2011-01-13
Hey Wendy

I've tried to install it and it just comes up with the "Smart book" screen. and stops, no loading bar, no text, nothing don't know why

Also I was thinking the other version of Linux for the VT8500  that is still incomplete (easypcliinux 0.2 and 0.1), I think he sopped making it, but it does work with the SD card, so you could get the driver from there probably, and it does have the Ethernet working I think.

Just thought I'd give my input
Thanks for working on this
-DonutFUN

---

### Post by Blazr on 2011-01-16
.

---

### Post by Joe of loath on 2011-01-16
Linux yes (posting from Debian on my WM8505 netbook), flash no. these netbooks don't have the grunt to decode AVIs, let alone flash video, even ignoring the lack of decent flash player for  Linux+arm.

---

### Post by zeveroth on 2011-01-19
So I have the via wm8505 smartbook from sylvania. I installed a android 1.6 os. My only problem for the most part is that it only stays on when the poewr adapter is plugged in. As soon as I unplug it, it shuts down thinking that there is no battery life. The smart book was working fine, if you consider wince and it's super crappy overall preformance "fine", before I installed the android os. I did this b\c my daughter could not use facebook options well on wince and some other internet stuff she uses on the desktop. Android seems to eliminate all her problems, but has killed the idea of portability. Any way to fix this would be great.

As a note: I have read that the power issue has something to do with the OS thinking that is is supporting a touch screen. Seeing this is not a touch screen smart book, is there any way to fix this?

---

### Post by zeveroth on 2011-01-19
sorry double post.

---

### Post by zeveroth on 2011-01-21
So I am guessing this is a dead thread? 2 days and no response from anyone?

---

### Post by abrasive on 2011-01-21
Unless you can dig into the android FS and find whatever code is responsible for low-battery shutdown - or find a different Android variant that reads battery differently - there's not much to be done. Many of the netbook style machines don't actually sense battery in any meaningful way. I guess another option, if you're electronically inclined, would be to try and locate and rip up the charger sense line. Wouldn't recommend it...  PS. I'm amazed this thread even still exists, after over 1 year and 1100 posts... Why doesn't anyone use the Wiki (bento-linux.org) and forums ([http://devio.us/~nextvolume/via_arm/](http://devio.us/~nextvolume/via_arm/)) that sprung up to help?

---

### Post by DonutFUN on 2011-01-21
It's not a dead thread, it is updated every at least 2 weeks or so I'd say.
I don't know anything about your problem otherwise I'd help

---

### Post by dario_ on 2011-01-24
> **DonutFUN said:**
> Hey Wendy

I've tried to install it and it just comes up with the "Smart book" screen. and stops, no loading bar, no text, nothing don't know why


I notice the same issue on my vt8500 netbook, WendyB, maybe something wrong in the script?
I also report that there is a SD/MMC card driver ready for use at 

[http://groups.google.com/group/vt8500-wm8505-linux-kernel/browse_thread/thread/6f83acbcd4aaafef](http://groups.google.com/group/vt8500-wm8505-linux-kernel/browse_thread/thread/6f83acbcd4aaafef)

but i suspect it's only for wm8505.... it needs to be tested on vt8500. Can it be useful?

---

### Post by WendyB on 2011-01-24
I was very busy last week

The version I'm working now at least should support both VT8500 and WM8505 and different screen resolutions.

So, if you get a black screen my guesses are:

[LIST]
[*]Your netbook is a wm8505
[*]your netbook has different resolution (not 800x480)
[*]the bootloader has trouble reading the kernel image from SD card (SD card is SDHC, or wrongly formatted/partitioned)
[/LIST]

---

### Post by WendyB on 2011-01-24
> **abrasive said:**
> Unless you can dig into the android FS and find whatever code is responsible for low-battery shutdown - or find a different Android variant that reads battery differently - there's not much to be done. Many of the netbook style machines don't actually sense battery in any meaningful way. I guess another option, if you're electronically inclined, would be to try and locate and rip up the charger sense line. Wouldn't recommend it...  PS. I'm amazed this thread even still exists, after over 1 year and 1100 posts... Why doesn't anyone use the Wiki (bento-linux.org) and forums ([http://devio.us/~nextvolume/via_arm/]("http://devio.us/%7Enextvolume/via_arm/")) that sprung up to help?
You're right. This thread is not the most convenient place to discuss this thing, but the other forum isn't very often updated.

---

### Post by zeveroth on 2011-01-24
Thanks for teh help everyone. I will dig deeper and If I come up with anything useful, I will post it back on here. I just wish someone other than me had this problem. lol

EDIT: So I may have found a solution to my power problem with the android 1.6 os that I installed on my smart book.

```
http://sites.google.com/site/gyplace/home/informatica/how-to-install-android-on-smartbook-smartmedia-wm8505-and
```

I am confused on how to comment the files as the post describes. A quick skim through and you will see what I am talking about.

---

### Post by Gemma22 on 2011-01-30
Hello,

and sorry if this has already been answered, I have searched this thread and not found a solution.

I have an EPC WM8505 netbook running windowsCE, I was wondering if it is possible to use a 3g dongle on this model, I have tried various but due to lack of drivers for CE have had no sucess, I was wondering if there is a flavour of Linux I can install onto this machine which will enable me to use my 3g modem dongle?

Many thanks

Gemma

---

### Post by WendyB on 2011-02-02
> **Gemma22 said:**
> Hello,

and sorry if this has already been answered, I have searched this thread and not found a solution.

I have an EPC WM8505 netbook running windowsCE, I was wondering if it is possible to use a 3g dongle on this model, I have tried various but due to lack of drivers for CE have had no sucess, I was wondering if there is a flavour of Linux I can install onto this machine which will enable me to use my 3g modem dongle?

Many thanks

Gemma
You might try the Linux I'm currently working on. There are several drivers for USB-dongles in it. I'm almost finished and almost ready to put it online.

---

### Post by WendyB on 2011-02-02
Finished my Gentoo install for EPC VT8500
A complete release with Midori webbrowser, Claws email, Pidgin messenger etc.
Kernel should support VT8500 and WM8505 and different resolutions (you have to change some files for the resolutions)

Download:
[http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList](http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList)

---

### Post by DonutFUN on 2011-02-03
I don't know what I'm doing wrong, but I can't get that version of Linux to work.
I have a VT8500 and all that happens is that it turns on and displays the "Smart Book" screen, where the loading bar usually shows up, and nothing happens.
Just to double check what I did was:
Put the script folder with all 4 files on a fat32 sd card (256MB)
and then i partitioned a 3.7 gig Usb Drive
First part was ext3  3.6 Gb
Second part was the swap at 133.35 Mb (I thought you said that 100 was enough, so I thought I'd try that)
then I just dragged the files from the archive manager to the ext3 part.

---

### Post by WendyB on 2011-02-03
> **DonutFUN said:**
> I don't know what I'm doing wrong, but I can't get that version of Linux to work.
I have a VT8500 and all that happens is that it turns on and displays the "Smart Book" screen, where the loading bar usually shows up, and nothing happens.
Just to double check what I did was:
Put the script folder with all 4 files on a fat32 sd card (256MB)
and then i partitioned a 3.7 gig Usb Drive
First part was ext3  3.6 Gb
Second part was the swap at 133.35 Mb (I thought you said that 100 was enough, so I thought I'd try that)
then I just dragged the files from the archive manager to the ext3 part.
Mhhz, even without a proper USB-stick it should boot the kernel until it reaches the point where it tries to mount the root fs.
(i once tried to boot without the USB-stick and it waited until I inserted the USB-stic and went on happily)
If it stalls at this point it appears to be unable to load the kernel image, or the kernel is crashing in a very early state.
Maybe you have hardware which is slightly different from what I have.

By the way, you have to extract all the files being root onto the USB-stick, otherwise permissions are messed up.
as root:
cd /where/your/usb/root/is
tar -xjvp -f /where/the/archive/is/file.tar.bz2

maybe you could try extracting the SD card files as well, being root. I see now that I have archived them as being my local user.

---

### Post by DonutFUN on 2011-02-03
I actually did do them as the root, so the permissions should have been good, and as for the sd card I had to do it on my other computer with XP because for some reason it doesn't let me, it has an error come up saying the permissions are wrong for some reason.

---

### Post by emostarxd on 2011-02-15
Hi,

I have downloaded the Gentoo for EPC VT8500, but netbook can't start the install from SD card...
When I push the Power button, I see the message (Press F1 to update the system) with password "ztk" and this menu have only the options to format NAND flash.
Please help me to boot this linux on my EPC (VT8500, ~240 mhz, 128 RAM. 2 gb NAND)

---

### Post by WendyB on 2011-02-16
> **emostarxd said:**
> Hi,

I have downloaded the Gentoo for EPC VT8500, but netbook can't start the install from SD card...
When I push the Power button, I see the message (Press F1 to update the system) with password "ztk" and this menu have only the options to format NAND flash.
Please help me to boot this linux on my EPC (VT8500, ~240 mhz, 128 RAM. 2 gb NAND)
It shouldn't try to install, only to boot from SD-card and then the USB-stick.
Maybe you have a different BIOS?

---

### Post by WendyB on 2011-02-16
> **DonutFUN said:**
> I actually did do them as the root, so the permissions should have been good, and as for the sd card I had to do it on my other computer with XP because for some reason it doesn't let me, it has an error come up saying the permissions are wrong for some reason.
I recently uploaded a slightly different version where the permissions should be fixed

---

### Post by alchark on 2011-02-16
ZTE is a completely different processor manufacturer from VIA/WonderMedia, so you have an incompatible machine (your vendor has probably misspecified the processor, as it happens in China).

---

### Post by emostarxd on 2011-02-17
alchark, so what should I do in this case? I need the Linux installed on my EPC but without Linux this netbook is a junk.
Sorry for my bad English :)

---

### Post by alchark on 2011-02-17
I don't really know anything regarding Linux on ZTE machines. Look around, maybe you'll find something. If you find register descriptions, you could try to port the latest kernel yourself;-)

---

### Post by justsomeguy11 on 2011-02-25
hello there everyone...let me start off by appoligizing for my noobiness !!! lol....here is my sistuation...
 
i recently picked up one of these mini netbooks...when i got it home all it did when i fired it up was show a very dull black screen..you could barley tell it even turned on because the screen was so dull....nothing happend after that ! absolutly nothing at all....it charged fine and doesn't have a low or dead battery..now let me also say that i am NOT a programmer or very effecient with programming knowledge..i do however have a androice epad that i've been playing with and have been reading up on the past few months in order to actually make good use of the device, so i know the terms like rooting and firmware, kernells and stuff like that even though i haven't been able to physically try them...ok getting off topic already ! lol....
 
is there a way i can get this thing up and running again? i've tried to read through this forum (this is the only place i've been able to find any kind of support for this product )..
 
i tried to put a sd card into the device as well as a usb stick but neither showed anything when i turned it on...so i'm thinking that the OS got wipped or erased or soemthing....now after reading though this thread it seems like i can attach the device to my comp and can put a kernell? on it..or a new bootloader or something? i just don't know where to start !!!:confused:
 
there is info on the first page but it is from 2009 so i'm not sure if there's more up to date info out there or new files and stuff to try to put on the device? when i plug it into my comp, should the comp see it as another drive? or is there a proggy i have to install in order to even see the device?
 
i know i'm asking alot and again i appoligize for my stupidness !! but any help would be sooooo appreciated ! i'm at a totall loss with this thing, i have also opened it up to see if i could find any kind of maker because it's so generic there is absolutly NO manafacture name on it anywhere...the only thing i could really see when i opened it up was a samsung chip on the MOBO..
 
if there is any kind of info that i have to supply in order to make sure i put the right files on it just let me know and i'll post it. but like i said there's not alot of info on this thing..but it's still opened up so if i need some kind of chip id number or something just let me know and i'll take a look...i just want to see some kind results because from the time i bought this (off the local classifieds ads) and the guy i bought it from said " yup it works great the battery is just dead)....figures that the 1 time i don't check something out is the 1 time i get ripped off !!!! but that's my own stupidness once again isn't it !!! lol.....
 
but again before i ramble more and more thank you for any and all assistance i can get on this thing. i would love to get it up and running and see what i can do with it..
 
thanks everyone !!!!!!
 
justsomeguy11

---

### Post by experx on 2011-02-26
> **emostarxd said:**
> Hi,

I have downloaded the Gentoo for EPC VT8500, but netbook can't start the install from SD card...
When I push the Power button, I see the message (Press F1 to update the system) with password "ztk" and this menu have only the options to format NAND flash.
Please help me to boot this linux on my EPC (VT8500, ~240 mhz, 128 RAM. 2 gb NAND)

Hi,

Did you get a solution or workaround on how to flash or load linux on these kind of netbooks ? I tried all options except format but it fails. Please post if you got a solution.

---

### Post by justsomeguy11 on 2011-02-26
man i can't even see the F1 message....can't boot from sd card or a usb stick...i also tried to hook up to my computer via. the network cord..still nothing...was hoping that i would be able to see the mini netbook that way at least...but couldn't even get to that..i don't know how the hell i'm going to be able to get it to boot from anything in order to restore the OS...i am sooooo lost here ~~~~
 
** when i took apart the device i seen a chip that had this on it :
 
samsung 
K9GAG08UOM
PCB0
 
then on the MOBO up in the corner it said this :
 
P701_main V8
100324
 
i hope this info is revelent to getting this beast up and running !!
 
thanks guys

---

### Post by emostarxd on 2011-02-27
I think we need to find a method how to install the U-boot to ZTK VT8500 devices with F1 msg on startup. This will allow to install any distributives using SD card and scriptcmd.
I think this can be done only via USB cable.

---

### Post by justsomeguy11 on 2011-02-28
> **emostarxd said:**
> I think we need to find a method how to install the U-boot to ZTK VT8500 devices with F1 msg on startup. This will allow to install any distributives using SD card and scriptcmd.
I think this can be done only via USB cable.
 
how do you get the computer to reconigize the device with a usb cable? is there some kind of proggy or something you have to install in order to see it? i'm really stuck here trying to get this device to even see something so i can get some kind of OS on this damn thing !!

---

### Post by emostarxd on 2011-03-01
I saw the some utilites from China developers, this utils was created for USB connect. Also the USB connection need to eject the EPC battery and enable the jumper on the motherboard. I can't find the link to this manual but it's exist on this topic.

---

### Post by justsomeguy11 on 2011-03-01
> **emostarxd said:**
> I saw the some utilites from China developers, this utils was created for USB connect. Also the USB connection need to eject the EPC battery and enable the jumper on the motherboard. I can't find the link to this manual but it's exist on this topic.
 
i'll have to look around and see if i can find that utility...if anyone out there has the link please please share !!!
 
also i never seen any kind of jumper on the mobo ! hopefully it isn't on the bottom side of it. because there is some kind of ribbon on the top of the mobo that doesn't look like it disconnects very easily. it goes from the mobo at the bottom of it under the keyboard and attaches to some kind of plastic piece that is at the bottom of the mobo...i'll have to inspect this tonight when i get home and see if i can find that jumper. at this point i will try anything to get this sucker going ! all i get is the dreaded faded black screen ! no F1 message or anything, that is why i'm thinking the OS got wipped out or something got so crupted that nothing works ...
 
if anyone else has any kind of idea how to get this damn thing up and running please please please share !!! like i said i only get the faded black screen. i tried to boot from usb stick as well as SD card....but the device didn't read either one of them and just acted the same with them in as it did without anything in it. 
 
i'm a very newbie here and can't find my way aroudn the site very well yet (because i'm not sure what any of this is) !!lol.....so if anyone can link that manual or help me out I would be sooo appreciative !!!!!
 
thanks everyone !!!!!
 
 
justsomeguy11

---

### Post by justsomeguy11 on 2011-03-01
ive tried to search this site for that usb proggy but still cant navigate my way around very well.....at least i managed to find this site though !! like i said this is the 1st place i've even found people talking about these mini netbooks to support them ! if anyone else found any other sites out there can you pm me them or link them here please...cause i really need to get this thing going...

---

### Post by emostarxd on 2011-03-02
I have found this manual:
[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm)

---

### Post by justsomeguy11 on 2011-03-02
> **emostarxd said:**
> I have found this manual:
[http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm](http://194.150.201.35/cnmlifestyle/cnmbook/CnMNB7SErestore.htm)
 
 
THANK YOU VERY VERY MUCH EMOSTARXD !!!!!!!!!! 
 
this looks very promising to try that's for sure..can't wait until tonight to give it a shot. i will post back my results. 
 
one quick question though...do you think any usb cable will work? or is there some kind of special adaptor you have to use ? i'd think that just a normal usb to usb cable should work right? when i got the device the guy never gave me anyting besides the ac plug ...
 
AGAIN THANK YOU SO MUCH !!!!!! :D:D:D
 
justsomeguy11

---

### Post by emostarxd on 2011-03-02
>  use a pair of tweezers or the bared ends of a cable tie to short the component 
This will allow to connect via any USB-to-USB cable.
Please try and let me know. I can't find this cable on any shop and I have ordered its production from the service master.

---

### Post by justsomeguy11 on 2011-03-04
> **emostarxd said:**
> This will allow to connect via any USB-to-USB cable.
Please try and let me know. I can't find this cable on any shop and I have ordered its production from the service master.
 
just wanted to give an update...i thought i had one of these cables kickin around in my box of messy cables but didn't ...gonna pick one up tonight or tomorrow morning and give this a try this weekend FOR SURE....so i'll post back my results....(hopefully they will be good results)....
 
cheers..
 
justsomeguy11

---

### Post by PerChristensen on 2011-03-08
Hi emostarxd and justsomeguy11
Together with Celem,Winston91,Nextvolume,PrFaas and many others many months ago we tried to find the partition (of many,probably) on the Via VT8500 where to burn a new boot-loader and therefrom find where to install a linux distribution.Unfortunately there seem not to exist a "lift-off" tool for the VT8500 like the chinese tool for the different ZTK Samsung brand you are talking about.I guess you will find a partition for the boot-loader,a (hidden?) partition for the kernel and another for the file system on your machines,perhaps even more partitions.If you succsede in lifting off and burning back on your Anyka machines with the chinese tool I will be impressed.Good luck
PS: There is much confusion around processors on these small books.The CNM books linked to above is to the "silver" windows CE edition,another linux CNM version use a different chip I vaguely remember,but I may be wrong.

---

### Post by justsomeguy11 on 2011-03-08
> **PerChristensen said:**
> Hi emostarxd and justsomeguy11
Together with Celem,Winston91,Nextvolume,PrFaas and many others many months ago we tried to find the partition (of many,probably) on the Via VT8500 where to burn a new boot-loader and therefrom find where to install a linux distribution.Unfortunately there seem not to exist a "lift-off" tool for the VT8500 like the chinese tool for the different ZTK Samsung brand you are talking about.I guess you will find a partition for the boot-loader,a (hidden?) partition for the kernel and another for the file system on your machines,perhaps even more partitions.If you succsede in lifting off and burning back on your Anyka machines with the chinese tool I will be impressed.Good luck
PS: There is much confusion around processors on these small books.The CNM books linked to above is to the "silver" windows CE edition,another linux CNM version use a different chip I vaguely remember,but I may be wrong.
 
i finally got my hands on a usb to usb transfer cable....was a real pain trying to track one down...well hopefully i'll at least be able to read this device...
 
you say we will find a partition (hidden)..what do ya mean by that? seems like you've done your homework on these things...any tips you can give in regards to at least getting the thing back up in running condition? i'm not looking at doing anything fancy with it (at the moment)...i just want to start by getting back to a state where it can be used, and then test different things after i can at least get into the damn thing..
 
are you saying you couldnt get to the kernel? is that why you said "hidden"? or did you find only part of it?
 
there seems to be more then just confusion around the processors..seems to be alot of confussion around the whole device. i'm thinking it's because the device is not that popular. and also that there's not a lot to it is there...just another little chineese toy that got over marketed and confused people as to what it can do so people bought it...
 
i bought it just for something to screw around with and see if i could get it going since when i got this it was in a bricked state and i was bored...now instead of being bored i'm pulling my hair out ! lol...but since you seemed to have screwed around with these alot more then me and tips and advice as to some steps would be great !!
 
thanks buddy...

---

### Post by PerChristensen on 2011-03-09
I am afraid I only can help with these two links:
 
A brasilian site with links to VT8500 + VT8505 restore software
[http://www.netbookce.tk/forum/viewtopic.php?f=2&t=2](http://www.netbookce.tk/forum/viewtopic.php?f=2&t=2)
 
Anyka Forum 
[http://mininetbooks.your-board.com/](http://mininetbooks.your-board.com/)
 
If processor is VIA ARM the first link should help in restoring.The second link goes to forum for netbooks with another brand of ARM processor (CNM book "silver" etc.)

---

### Post by bornagainpenguin on 2011-03-09
I hate to be *that* guy, but this is a 114 page thread on this subject, which covers quite a bit of ground.  Could anyone whose been doing this for awhile post an update for those of us coming in late?  I mean something simple explaining what hardware is known to be supported in Linux, which desktops are recommended, and generally whether it is practical to get one of these and seek to install Linux on them?

If Android is recommended, what are the options with apps?  I have an Android tablet so I might be able to get some apps from there to run on one of these but generally that is heavily dependent on which revision of the system you're using and at last look I think someone said only Android 1.6 was supported?  Is that right?

What are the options with regards to WinCE on these (yes, I know I know...) is it possible to convert them to Windows Mobile devices and hopefully access more apps that way?

I have a friend who has one and he's been quite disappointed with his as is, if I manage to get it from him to work with it I'd like to have some idea of what is known to be possible before I waste a lot of my time duplicating what is already done.

Thanks!

--bornagainpenguin

---

### Post by justsomeguy11 on 2011-03-10
> **PerChristensen said:**
> I am afraid I only can help with these two links:
 
A brasilian site with links to VT8500 + VT8505 restore software
[http://www.netbookce.tk/forum/viewtopic.php?f=2&t=2](http://www.netbookce.tk/forum/viewtopic.php?f=2&t=2)
 
Anyka Forum 
[http://mininetbooks.your-board.com/](http://mininetbooks.your-board.com/)
 
If processor is VIA ARM the first link should help in restoring.The second link goes to forum for netbooks with another brand of ARM processor (CNM book "silver" etc.)
 
awesome links !!! thank you very much !! i just had to totally take the mobo out of the unit and flip it to find out that it is a WM8505...so at least now i know what i'm dealing with. the second link is great for any beginners (like me) who want to read up on these devices since there isn't very many forums out there i've found on this thing..one thing i can't figure out is when the instructions say you have to jump the certain pins i can't find anywhere the name/number of the pins your suppose to jump..there is a picture of them but its not clear enough to read, and on my unit there's alot to choose from. but there is nothing like master/slave pins or pogo pins type things...mostly just little things sodered on the mobo (sorry for my lack of proper explanation of the things sodered on the mobo). 
 
however first i am going to try the SD card thing and see how that works before i try this jumper thing !! will post back results as i go...i know i was supposed to do this the other weekend but things came up and i can only do this once in awhile and only little things at a time..lol....
 
 
***update***
 
so i've gotten a little bit ahead now. i downloaded 2 different files from that link above (thanks again). 1 was the 8505 and the 2nd was the vt8505..the 2nd one has gotten me the progress. i've managed to get it to step 3 of upgrading..which is safe mode. it says upgrade safe mode sucessfull....then it's just hanging..but this is a step forward at least !!! i tried to upgrade it 2 times in a row now but it keeps hanging at the same spot. i'm going to try some more tomorrow evening and see what else i can get it to do...gotta get some sleep now..
 
.O 1 dumbass thing i did...i tried a couple times but nothing was happening at first when i put the SD card in...until i flipped it upside down..then it worked ! wierd that you have to put the sd card in upside down !! in any device i've used sd cards in they will only go in one way, try to put them in wrong and they usually just don't fit...well that wasn't the case here and you should have seen the big smile on this guy's face when i saw that screen pop up with something other then just black lines and saw actual words come across it and it start to upgrade !!!!
 
anyway, i'll post more results tomorrow...its a bonus that i haven't had to use the jump method with usb-usb yet...
 
cheers

---

### Post by justsomeguy11 on 2011-03-12
i've been getting so frustrated with this damn thing i think i gotta put it aside for a bit before i smash the damn thing ! 
 
 
]i've download about 6 or 7 different versions of wm8505 files , including 2 or 
3 androids, sylvania's,and afew unnamed ones'..all giving the same results. all  freezing up in the same place..,right afterit says sucessful safe mode upgrade...the androids freeze after awhile as well...i've never gotten to any screen where is says to reboot the device..always freezes up way before that point...man i just don't know what else to try or to do !!! i'm at a totall loss here..i've read about a million different threads thanks to the link above..but still nothing !!! FML ~

---

### Post by justsomeguy11 on 2011-03-15
I hate this device. love the challenge...but am starting to get very fustrated
 
does no one have any ideas, hints, tips or advice out there !!!???!!! lmao...guess the support for this device is pretty much non-existent huh...
 
has anyone ever gotten this device to boot properly by doing the usb-usb way?

---

### Post by vinceCOOK on 2011-03-26
Hello, 

I don't know if you know but you can now get a FREE Ubuntu Linux desktop computer........ in the cloud. 

amazon web services. 

It is free for the year and comes with a 1.2 ghz cpu and 700 ram and hard drive space. You have over 30 thousand 
software titles you can install and it remembers it's state on power down.  (micro instance)

So you can use any VT8500 or wm8050 machine with windows CE on it
Windows CE comes with REMOTE DESKTOP which will allow you to dial
into the FREEcloud Linux machine.

That's it.....you have Linux on your low cost netbook for FREE. 


Windows CE comes with REMOTE DESKTOP ready to go. So these chinese laptops will work right away for getting 
you into a linux computer easily and free over ethernet or WI FI. 

These free cloud computers from Amazon are excellent...been using it for many months...you are allowed to use it 24 hours per day for the whole year for FREE. Also you will find that surfing the web and FLASH works perfect and is FAST on the cloud computer. Faster than any slate or laptop. 

Just go to amazon web services....watch the youtube video about how you open a free account with a pre-pay credit card from the corner store. Then start a Linux machine up. 

To choose your Linux machine just click LAUNCH INSTANCE and then select PUBLIC AMI's and type "desktop" into the search and choose EBS as the type. 

You will see Ubuntu Linux desktop versions are all listed  i386........use one of those recent examples.  (Lucid) 

Currently Amazon are NOT supporting SOUND. They are working on getting sound going on The ubunut cloud machines. 

Thanks. 

So in summary, any Slate or laptop can quite happily act as a windows or Linux computer by simply using a free cloud computer. It will work wellfor FLASH and tonnes of free Linux software. 

Vince.

---

### Post by mails65 on 2011-04-14
This a great knowledge base, i have come to understand the basics of this evil device, many thanks. Still it seems i cant get my 7"mini laptop to boot from the sd card. I insert the SD card, in which the android-ARM-8505-Smartbook file is copied, i power on the laptop and then:
pocket CMD v 6.00
storage card\MassProduction.bat:File not found

This is what i get, and then it just boots to wince. Have i got it all wrong? Can someone please help, im not so experienced with all these :( thanks in advance :)

---

### Post by justsomeguy11 on 2011-04-20
justa bump to see if anyone has any updates or progress......
 
cheers everyone

---

### Post by heartburnkid on 2011-04-24
Playing with my mom's Sylvania WM8505-based smartbook, and I think I might have borked it... I tried to install the Android image on page 66 of this thread, and the install seemed to go fine; however, after the reboot, the screen stayed black for upwards of 5 minutes.  So, I downloaded the WinCE rom from Sylvania's website, and tried to flash back to that; again, the install went fine, and it booted into a live WinCE install, but when I tried to reboot the machine, nothing.  Just a black screen.

Anybody have any ideas?

---

### Post by Joe of loath on 2011-04-25
If you leave it and let it boot, can you ping it from the network? Mine failed, but I noticed the caps lock keys made the LEDs flash, so I typed in what I needed to log in and connect to the network, and I could ping it and ssh in.

---

### Post by heartburnkid on 2011-04-25
Afraid not.  It doesn't even seem to be touching my router; no sign of it on the active clients list or on the DHCP leases.

---

### Post by Joe of loath on 2011-04-25
Tried booting Debian from SD card?

---

### Post by PrFaas on 2011-04-26
> **PerChristensen said:**
> Hi emostarxd and justsomeguy11
Together with Celem,Winston91,Nextvolume,PrFaas and many others many months ago we tried to find the partition (of many,probably) on the Via VT8500 where to burn a new boot-loader and therefrom find where to install a linux distribution.Unfortunately there seem not to exist a "lift-off" tool for the VT8500 like the chinese tool for the different ZTK Samsung brand you are talking about.I guess you will find a partition for the boot-loader,a (hidden?) partition for the kernel and another for the file system on your machines,perhaps even more partitions.If you succsede in lifting off and burning back on your Anyka machines with the chinese tool I will be impressed.Good luck
PS: There is much confusion around processors on these small books.The CNM books linked to above is to the "silver" windows CE edition,another linux CNM version use a different chip I vaguely remember,but I may be wrong.

Sorry for the late reply... As far as i've been able to find out the bootloader is loaded from the 8-pins 'serial prom' that is located close to the actual CPU/SoC. In my case, the CPU and the serial prom are both located on a small 'plug-in' board on the machine's main board. It seems possible to 'blast' the contents of that serial prom when doing an 'incompatible' upgrade. In theory, it should be possible to de-solder the serial prom from the CPU board, and re-flash it. I presume there is some JTAG way to do that, but lacking 'doc' of that, de-soldering and re-flashing the prom seems the only way. For the DIY-er there are two obstacles:

1) to build a serial-prom programmer: the interface of the serial prom is an SPI interface, so it would not be all too difficult to trap together something for that. For smaller proms than this (93cx6 types..) i made something like that in the past, including a program to read/write those small serial (flash-)proms. The difference is that the proms i had where DIL, and this is an SO-8 package (meaning: it is smaller, and i have no chip socket for SO-8 ). You'd have to solder the chip into the programmer or else program the chip 'in-circuit'... The latter seems 'tricky' to me: one mistake and you burn your CPU chip. I have the datasheet of the serial boot-prom chip: it is a dead-common 512Kx8 SPI serial prom; nothing *really* special: Farnell has them for a few 'bucks'...

2) to obtain a binary file of the 'correct' serial-boot-prom for your machine. Only if you are *really* sure you have a correct boot-image-file for the exact computer you have is there any chance of success. 

NB: one thing that irks me is that the serial prom *has* a write-protect input, and that that pin has not been used to provide for *some* protection of the boot-prom's contents... A simple pull-up resistor & 'jumper' could have made the boot-prom 'bullet-proof... Well, against accidental over-writes that is...

---

### Post by justsomeguy11 on 2011-04-26
> **PrFaas said:**
> Sorry for the late reply... As far as i've been able to find out the bootloader is loaded from the 8-pins 'serial prom' that is located close to the actual CPU/SoC. In my case, the CPU and the serial prom are both located on a small 'plug-in' board on the machine's main board. It seems possible to 'blast' the contents of that serial prom when doing an 'incompatible' upgrade. In theory, it should be possible to de-solder the serial prom from the CPU board, and re-flash it. I presume there is some JTAG way to do that, but lacking 'doc' of that, de-soldering and re-flashing the prom seems the only way. For the DIY-er there are two obstacles:
 
1) to build a serial-prom programmer: the interface of the serial prom is an SPI interface, so it would not be all too difficult to trap together something for that. For smaller proms than this (93cx6 types..) i made something like that in the past, including a program to read/write those small serial (flash-)proms. The difference is that the proms i had where DIL, and this is an SO-8 package (meaning: it is smaller, and i have no chip socket for SO-8 ). You'd have to solder the chip into the programmer or else program the chip 'in-circuit'... The latter seems 'tricky' to me: one mistake and you burn your CPU chip. I have the datasheet of the serial boot-prom chip: it is a dead-common 512Kx8 SPI serial prom; nothing *really* special: Farnell has them for a few 'bucks'...
 
2) to obtain a binary file of the 'correct' serial-boot-prom for your machine. Only if you are *really* sure you have a correct boot-image-file for the exact computer you have is there any chance of success. 
 
NB: one thing that irks me is that the serial prom *has* a write-protect input, and that that pin has not been used to provide for *some* protection of the boot-prom's contents... A simple pull-up resistor & 'jumper' could have made the boot-prom 'bullet-proof... Well, against accidental over-writes that is...
 
thank you very much for that info !!! unfortunatly i don't have skills anywhere close to what is described here. on top of that i got this unit for 40 bucks from someone (because of the fact that he screwed it up) so i guess i should have just bought a case of beer instead of this toy..lol...but it was a great learning experience reading up on this stuff that's for sure~ maybe one day someone will conquer this machine and i'll be able to get it going. 
 
it's just a pisser that the way everyone describs how to get these things going with the sd card won't work for me (but that's normally my luck that nothing is ever easy)..
 
it's still boggles me though why it's freezing up on safe mode/normal mode when booting from the sd card. no matter what file i put on it does that ! then just stays on the logo when rebooted....i was really hopeing that my kid would be able to use this and have her "own" laptop...(she's only 5)....lol....
 
thanks again guys...it's all greatly appreciated and i love to hear everybody's new ideas...

---

### Post by OooBuntuRox on 2011-04-27
> **heartburnkid said:**
> Playing with my mom's Sylvania WM8505-based smartbook, and I think I might have borked it... I tried to install the Android image on page 66 of this thread, and the install seemed to go fine; however, after the reboot, the screen stayed black for upwards of 5 minutes.  So, I downloaded the WinCE rom from Sylvania's website, and tried to flash back to that; again, the install went fine, and it booted into a live WinCE install, but when I tried to reboot the machine, nothing.  Just a black screen.

Anybody have any ideas?

Hi,

It sounds like we have the same sylvania smartbook. I want ubuntu on it. No, it won't boot from an sd card with linux netbook. I also installed android on an e-reader. I didn't like android. I can switch it back, but I like the sylvania clam-shell better so I'm not bothering with the e-reader.

So you want ideas? Not sure if this will help you any but here is what I noticed with the sylvania: You have to have an SD card formatted in fat32. Then put windows ce on the root of the sd card. You of course, have to take the compressed file from [www.digitalgadgets.com]("http://www.digitalgadgets.com") [sylvania website], expand it into a folder, find the script folder and copy the script folder to the root of your SD card. (It was the same way with the android install on the e-reader.) Ok, with the smartbook turned off, insert the sd card, power up the smartbook and that should flash the unit. After the unit boots to windows ce, I powerd the unit off and removed the sd card. When I powerd up again, i just gave it a few minutes to start and it eventually did. The first boot after a flash seems to take longer.

Is that how you tried it too?

So to install Ubuntu, we need someone to code ubuntu into the same format with a script folder for the root of a fat32 SD card. Personally, I'm not sure how that works. But I sure would like to have it on this sylvania smartbook.

Best of luck to you, OooBuntuRox :guitar:

---

### Post by Joe of loath on 2011-04-27
No way you'll get any form of Ubuntu you recognise onto these: See how much memory you're using. Lubuntu uses around 90mb at idle, Ubuntu around 256.

The machine has 128mb of memory, so Lubuntu will use most of it, and Ubuntu won't run at all. Debian with Fluxbox uses around 30mb.

---

### Post by heartburnkid on 2011-04-27
> **OooBuntuRox said:**
> Hi,

It sounds like we have the same sylvania smartbook. I want ubuntu on it. No, it won't boot from an sd card with linux netbook. I also installed android on an e-reader. I didn't like android. I can switch it back, but I like the sylvania clam-shell better so I'm not bothering with the e-reader.

So you want ideas? Not sure if this will help you any but here is what I noticed with the sylvania: You have to have an SD card formatted in fat32. Then put windows ce on the root of the sd card. You of course, have to take the compressed file from [www.digitalgadgets.com]("http://www.digitalgadgets.com") [sylvania website], expand it into a folder, find the script folder and copy the script folder to the root of your SD card. (It was the same way with the android install on the e-reader.) Ok, with the smartbook turned off, insert the sd card, power up the smartbook and that should flash the unit. After the unit boots to windows ce, I powerd the unit off and removed the sd card. When I powerd up again, i just gave it a few minutes to start and it eventually did. The first boot after a flash seems to take longer.

Is that how you tried it too?

So to install Ubuntu, we need someone to code ubuntu into the same format with a script folder for the root of a fat32 SD card. Personally, I'm not sure how that works. But I sure would like to have it on this sylvania smartbook.

Best of luck to you, OooBuntuRox :guitar:

I doubt it'd make a difference, but my SD card is formatted as FAT16.  I'll go ahead and try it with a FAT32-formatted card.

EDIT: Nope, the FAT32-formatted card made no difference.  How long are you talking about leaving it up to boot?  Because I've gone as long as a half an hour with nothing to show for it...

---

### Post by OooBuntuRox on 2011-04-27
> **Joe of loath said:**
> No way you'll get any form of Ubuntu you recognise onto these: See how much memory you're using. Lubuntu uses around 90mb at idle, Ubuntu around 256.
 
The machine has 128mb of memory, so Lubuntu will use most of it, and Ubuntu won't run at all. Debian with Fluxbox uses around 30mb.
 
thank you. I sort of knew it was too big. but i am also heard that someone is working on a version of linux for mobile devices and that would work well on this ubit. this is more like a PDA than a notebook.
 
Being that there are so many versions of linux I thought that someone might jump in and mention a version of LINUX that would work. There are versions of LINUX for embedded systems. But I am of course searching for something open source.
 
Perhaps if enough people ask, Linus T will consider writing a version of Ubuntu for mobile devices. The size alone won`t get Linux on these embedded systems. It will have to be ib te correct code format too.
 
Thanks very much for your comments. ):P 
 
Does anyone know how much memory windows CE actually requires to run?

---

### Post by OooBuntuRox on 2011-04-27
> **heartburnkid said:**
> I doubt it'd make a difference, but my SD card is formatted as FAT16. I'll go ahead and try it with a FAT32-formatted card.
 
EDIT: Nope, the FAT32-formatted card made no difference. How long are you talking about leaving it up to boot? Because I've gone as long as a half an hour with nothing to show for it...
 
try this link:
[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=177](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=177)
 
let us know how you make out.
 
OooBuntuRox :guitar:

---

### Post by heartburnkid on 2011-05-01
Finally had a chance to take another crack at this.  The files on the link you provided didn't really help; however, after snooping around that forum, I did find [this](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=167&page=1).  This works, and my mom's smartbook is now running Android 2.1!

Thanks, OooBuntuRox!

**EDIT**:  OK, apparently it's not 2.1, it's 1.6 skinned to look like 2.1.  Still, it works!

---

### Post by philcolbourn on 2011-05-02
> **tonyblews said:**
> This is the pit i fell in to when buying the ubisurfer... the processor is different, and i can't get stuff from the littlelinuxlaptops stuff to work on it.

what is the cpu in the ubisurfer 7?

---

### Post by OooBuntuRox on 2011-05-06
> **heartburnkid said:**
> Finally had a chance to take another crack at this.  The files on the link you provided didn't really help; however, after snooping around that forum, I did find [this]("http://devio.us/%7Enextvolume/via_arm/viewtopic.php?id=4&t_id=167&page=1").  This works, and my mom's smartbook is now running Android 2.1!

Thanks, OooBuntuRox!

**EDIT**:  OK, apparently it's not 2.1, it's 1.6 skinned to look like 2.1.  Still, it works!

You're welcome.

Glad to hear you got somewhere. So the link I sent basically said that once you get android to work, you can then install wince again. There was plenty of info to poke around in on that site.

I'll bet that when you try to install linux it formats the smartbook internal memory to something other than fat. Once that happens, the smartbook probably chokes and can't read the partition.

You may also be able to take a bricked smartbook and run a usb cable from a pc to the smartbook. The smartbook might pop up as a drive. If it does, you could try formatting the partiton as fat32 and see if you can reload winCE from your SD card the usual way with a script folder on the sd card, etc.

I'm glad that you have something you can at least use. I didn't like android and would still like to get some form of linux (Ubuntu mobile? !!!) on my smartbook. If not, I have my eye on and acer netbook for $198. Just like the CVS smartbook, it will be hard to get your hands on one for that price.

The lowest I can find one in stock is $235 before tax and shipping. Not worth it to me. Maybe I'll hunt for a book and learn how to program embedded systems/ arm processors.

Good luck to you.

I have some links to images for the 8505. If I come across them, I'll post them/ edit this message.

OoobuntuRox, :guitar:
[B]
Woops:[/B] I just noticed this at the same site we've been discussing. Perhaps a few people will want to play around with the info there. If not, I'll eventually get to poking around with it. It sounds like you can run a version of linux right from and SD card by creating 2 partitions. I think thats what it was driving at. But I only glanced at it.

---

### Post by Fallingwater on 2011-05-15
I got linked to this thread from a DealExtreme post.
I've seen several of these small netbooks [on sale on DX]("http://s.dealextreme.com/search/windows+ce+netbook") (and eBay, but DX usually sells them cheaper - about &#8364;60), but their operating system puts them squarely into wordprocessor territory - in that they aren't really good for anything else. Can Linux actually be ran on them, and if so how? I'm ok with non-Ubuntu distros (in fact I tend to prefer Debian - no offense!), as long as **some** flavour of it can run. 
I understand this question has probably been answered in this thread, but it's 116 pages long, which makes it hard to figure it out on my own without taking many hours to read through it all.

Thanks :)

---

### Post by Joe of loath on 2011-05-15
There was a website on it, but it seems to have gone offline :(

However, this forum may be of use [http://devio.us/~nextvolume/via_arm/index.php](http://devio.us/~nextvolume/via_arm/index.php)

---

### Post by Fallingwater on 2011-05-16
But, has nobody managed to install Linux here?

How about Android?

---

### Post by Joe of loath on 2011-05-17
I have Debian on mine :D However, I broke it trying to install Android, so now it's headless.

---

### Post by SoSammy on 2011-05-26
>  ... Go to the place on devio.us... [www.bento-linux.org]("http://www.bento-linux.org") (or the #easypc IRC channel on FreeNode) is the stablest place you're going to get when you want a link to the forums (in case they move again, hehe).  Sigh.  I dutifully saved a link to that site and waited to get my hands on one of these machines.  I have one now, and the site appears to be gone.    If the info and images from bento-linux.org are mirrored somewhere, I would greatly appreciate a link.  Googleing finds some things on download sites, but I don't know what they are out of the excellent context provided on the bento-linux.org site.  TIA,  SoSammy 

--UpDate--
Ok, found a good instructions here:
[http://blogold.chinaunix.net/u3/110913/showart.php?id=2367230](http://blogold.chinaunix.net/u3/110913/showart.php?id=2367230) 

 ... which references files here: 
[http://bur.st/%7Eabrasive/wm8505_linux/1.0/](http://bur.st/%7Eabrasive/wm8505_linux/1.0/) 

... and if that source vanishes, the files are also here: 
[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/) 

There are some very basic instructions in abrasive's files too.

---

### Post by Fallingwater on 2011-05-30
> **Joe of loath said:**
> I have Debian on mine
Fantastic. How did you load it on your computer? Did you follow a guide, and if so, which one?
Thanks :)

---

### Post by Joe of loath on 2011-05-30
I followed a guide, it was on bento-linux.org...

I could mess about with my install if you want, get it as close to vanilla as possible and clonezilla + upload it to my server for you?

---

### Post by X-Windows on 2011-06-04
Jumping on board here, got one of these cheep netbooks running Debian and IceWM right now. After some searching around there appear to be two types of these, models with NAND and models that use USB. I spent about 4 days trying to get past the "Loading filesystem" freeze during normal Debian installation. Eventually found a great site [here]("http://www.cheap-hack.com/home/en/computer-science/wm8505/debian-installation.html") that shows how to install Debian on one of these "no NAND" devices. Basically install android and use its boot loader to launch Debian.

I've made a few posts as "Don" in the comments there, i couldn't get my device to connect to any secured wifi ap's. Posted my wpa_supplicant.conf file for anyone else with this problem (works for unsecured networks).

Everything is working (albeit a little slow), except the sound. I can get sound out of the android install but not under debian, lspci shows no sound card. Does anyone know if it is possible to use whatever driver android uses and install that to debian? Would be very much appreciated.

---

### Post by Joe of loath on 2011-06-04
Can you boot from SD just by extracting the fatpart and extpart to a fat32 and ext2 partition on the SD, respectively? That's how I did it, then installed X and fluxbox on top of that. Was just about usable with netsurf as the browser :p

---

### Post by Fallingwater on 2011-06-04
> **Joe of loath said:**
> I followed a guide, it was on bento-linux.org...

I could mess about with my install if you want, get it as close to vanilla as possible and clonezilla + upload it to my server for you?
Wow, thanks, but I don't yet have one of these... I'm thinking of getting one because I love cheap Linux-running devices, but I'm still trying to figure out what netbook can run what OS...

X-Windows: by USB you mean their internal memory is in fact a USB mass storage device? While the NAND netbooks just have a normal flash memory drive?

---

### Post by Joe of loath on 2011-06-04
No need for me to mes around with mine, looks like someone mirrored the files :D [http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/)

---

### Post by X-Windows on 2011-06-04
> **Joe of loath said:**
> Can you boot from SD just by extracting the fatpart and extpart to a fat32 and ext2 partition on the SD, respectively? That's how I did it, then installed X and fluxbox on top of that. Was just about usable with netsurf as the browser :p
 
With mine, every time I tried to use a double partition SD card it would fail to see the ext partition. The only way I could get it to work was by installing from a single fat32 partition.

FallingWaters: Yes, I believe that is how these devices are made, I couldn't see a usb card when I took mine apart (granted I wasn't looking for it at the time), but if your model has trouble installing any of the debians, try the method gyppe used in my above link. I believe as soon as you get to a useable root terminal you can install whatever you want (although I have no experience with this).

Also, if you are looking for something more supported, I would defiantly go with an eePC. Better hardware support and a good bit speedier than these 7" netbooks (which are about as powerfull as a smartphone).

Joe of Loath: does the sound work on your netbook? Do you know what the sound card is or how to install drivers for it?

---

### Post by Joe of loath on 2011-06-04
I never tried the sound under Linux, but AFAIK it's just a slightly messed around AC97. People got it to work, but only using OSS, and it wasn't terribly stable.

Your netbook seemed to have the worst of both worlds. I couldn't install to mine, as I had an internal USB drive, but I could boot from SD card no trouble.

Mine got nuked when I tried to install android. I need to use a serial console to rebuild the uboot, because somehow the android install killed the lcdinit part of the boot sequence. The netbook boots, but the screen is blank.

---

### Post by X-Windows on 2011-06-04
Would be great to get sound working on this, would be a decent little device then.

I'm sure you already tried everything but I can upload the script file that boots mine into debian root terminal if you think it might help. Also heard that reinstalling windows can fix the uboot.

---

### Post by Joe of loath on 2011-06-04
I can boot Debian, and SSH in fine, but the LCD won't fire up. Installing Windows might work, but it will have to be an unattended install, because I can't see what's going on :p

---

### Post by abrasive on 2011-06-05
> **Joe of loath said:**
> I can boot Debian, and SSH in fine, but the LCD won't fire up. Installing Windows might work, but it will have to be an unattended install, because I can't see what's going on :p

Try using [this kernel]("http://bur.st/%7Eabrasive/uzImage.bin") instead. It's built from projectgus' tree, with my latest patches - which should make the display work on all 8505 machines, and has a large number of other bugfixes and improvements over the original bento-linux release.

---

### Post by Fallingwater on 2011-06-11
How about installing Debian on [_this netbook_]("http://www.dealextreme.com/p/7-tft-lcd-windows-ce-6-0-via8650-cpu-wifi-umpc-netbook-green-349-79mhz-2gb-3xusb-sd-lan-70902") or [_this one_]("http://www.dealextreme.com/p/7-0-tft-lcd-android-2-2-via-8650-cpu-wifi-umpc-netbook-black-349-79mhz-2gb-3-usb-sd-lan-70760") (they seem almost the same, except the black Android one can use 32GB SD cards while the other is apparently limited to 16)? Their 350MHz 8650 CPU should be a bit faster than the 8500 netbooks and they have twice the RAM (256MB).

Also, if I were to install Android instead, is there a limit to what version I can install?

---

### Post by Joe of loath on 2011-06-11
Now, they look identical to mine, but the SoC appears to be different. I guess you'd need to have one in front of you to know.

---

### Post by justsomeguy11 on 2011-06-14
> **justsomeguy11 said:**
>  
 
 
. i downloaded 2 different files from that link above (thanks again). 1 was the 8505 and the 2nd was the vt8505..the 2nd one has gotten me the progress. i've managed to get it to step 3 of upgrading..which is safe mode. it says upgrade safe mode sucessfull....then it's just hanging..but this is a step forward at least !!! i tried to upgrade it 2 times in a row now but it keeps hanging at the same spot.cheers
 
 
> **abrasive said:**
> Try using [this kernel]("http://bur.st/%7Eabrasive/uzImage.bin") instead. It's built from projectgus' tree, with my latest patches - which should make the display work on all 8505 machines, and has a large number of other bugfixes and improvements over the original bento-linux release.
 
just wondering if this will work with my sistuation quoted above? no matter what file i've tried to put on my machine it ALWAYS does the exact same thing and freezes at the exact same spot...hopefully this file will work although i have given up all hopes of seeing this machine actually boot up and become useable :(

---

### Post by franvalmo on 2011-06-15
> **mmanu said:**
> ok for the mount test.
ok for the tar (except some badblocks but it gave me the prompt back)
i shut it down & ... it asks for login & password ... hummmmmm?...
hello, and thanks in advence. I found as answer of my epc minilaptop -just when I try t install linux debian - the flllowing message: ... Can't find extpart.tgz on SD card. I push ENTER and in console I write: 
# ls /dev/mmsblk0*
 /dev/mmcblk0   /dev/mmcblk0p1
then I try to mount ...
# mount /dev/mmcblk0p1 /mnt/sd
mount: mounting /dev/mmcblk0p1 on /mnt/sd failed. Device or resource busy
.. What supposed am I to do? Help and Thanks in advance

---

### Post by abrasive on 2011-06-15
> **franvalmo said:**
> hello, and thanks in advence. I found as answer of my epc minilaptop -just when I try t install linux debian - the flllowing message: ... Can't find extpart.tgz on SD card. I push ENTER and in console I write: 
# ls /dev/mmsblk0*
 /dev/mmcblk0   /dev/mmcblk0p1
then I try to mount ...
# mount /dev/mmcblk0p1 /mnt/sd
mount: mounting /dev/mmcblk0p1 on /mnt/sd failed. Device or resource busy
.. What supposed am I to do? Help and Thanks in advance

It looks like mmcblk0p1 is already mounted... and it can't find 'extpart.tgz' on it! Did you remember to copy that on to the card?

---

### Post by franvalmo on 2011-06-20
And Would you be so kind to up this files somwhere else not bento what is down, please, I´ve been looking for that for many days without good result. I 've been looking for information about how to mount linux on wm8505 and in mine not goes as well as I'm expecting. Please up it and notice the link.
franvalmo or email me [email]infosiaco@gmail.com[/email]

 
> **styol said:**
> hey there. long story short i've been following the thread for a week or  two and recently got a WM8505 (spicy red color), been in touch with  abrasive and some other peoples via the IRC room (  irc://irc.freenode.net/#easypc ) and we've been able to A) figure out an  issue that ships with these devices and B) a way to work around it by  using both an SD card AND a USB stick.

If you have been trying to  boot debian live via SD card on a WM8505 and have not been able to,  likely by getting a loader that never finishes loading, then  instructions on a temporary easy work around are to follow. The issue  specifically is that the SD reader itself on the motherboard and/or the  kernel mounts the SD card itself in Read Only mode -- which makes it  impossible for Debian to do its ninja magic and get itself running.  Abrasive thought maybe his SD reader was broken, so he performed a  hardware work around, but both myself and another user in IRC have been  able to verify that this is the case. Have no fear! this totally works:

[B][SIZE=4]How to Live Boot Debian via SD + USB[/SIZE]

[/B]Going  to briefly describe the basic steps required to prepare both an SD card  and a USB flash drive for live booting Debian without installing or  overwriting your nand. Basically, the SD card provides instructions on  what to do and which filesystem to load, and then it loads the debian  filesystem off the USB stick so you can play live. All the packages you  install and changes you make will stick.

You will need to format  your SD card and USB stick much in the same way you previously did,  difference being SD card holds the script directory and is FAT32 while  the USB stick is EXT2 and holds the Debian filesystem. The following  references fdisk specifications.

**SD Card**
Type: b   (WIN95 FAT32)
Size: 32MB
Contents: scripts folder (extracted from  fatpart.tgz or fatpartusb.tgz)

[B]USB flash drive
[/B]Type: 83 (Linux) aka EXT2
Size:  Up to you, but at least 256mb preferably.
Contents: debian  filesystem (extracted from extpart.tgz)

Probably going to skip  describing how to go about formatting, partitioning, and preparing the  SD card and USB stick using linux and fdisk or otherwise, but will  probably end up posting it at some point (if not here, then at the site  we're working on for these devices and linux)

Both partitions (SD  / USB) for use in this should be the 1st and primary  partition #1 -- following instructions will expect that debian  filesystem is at /dev/sda1 which it always is with 1 usb device plugged  in and debian filesystem as first partition. You can adjust as needed  with the manual instructions.

**Manual preparation of cmd / scriptcmd**
If you would like to  do this manually, or need to make adjustments to where the debian fs is  loaded from (perhaps you're using partition 2 and want to make it  /etc/sda1p2 ? ) follow these basic instructions:

[LIST=1]
[*]this  assumes you're using linux
[*]navigate your way into the  /scripts directory on the sd card
[*]edit the *cmd* file  with your favorite editor
[*]change *root=/dev/mmcblk0p2* to *root=/dev/sda1*
[*]add  *rootdelay=10* after *root/dev/sda1*
[*]**should read:***  setenv bootargs mem=112M root=/dev/sda1 rootdelay=10*
[*]now  execute ./make_scriptcmds
[*]place SD in wm8505 and plug USB stick  in
[*]reboot, and voila.. dinner is served
[/LIST]

[B]Download  SD + USB - fatpart.tgz / scriptcmd
[/B]extpart.tgz for the USB stick  is the exact same, but here is a download to the adjusted scriptcmd and  adjusted packaged version, fatpartusb.tgz

[LIST]
[*][fatpartusb.tgz]("http://bento-linux.org/sites/default/files/fatpartusb.tgz")
[*][scriptcmd]("http://bento-linux.org/sites/default/files/scriptcmd")
[/LIST]

The originals:
[http://bur.st/~abrasive/wm8505_linux/1.0/fatpart.tgz]("http://bur.st/%7Eabrasive/wm8505_linux/1.0/fatpart.tgz")
[http://bur.st/~abrasive/wm8505_linux/1.0/extpart.tgz]("http://bur.st/%7Eabrasive/wm8505_linux/1.0/extpart.tgz")


Thank you very much for all your help and hard work abrasive, he's definitely the only reason i was able to figure out how to get it to work in this way :) thanks also to everyone else thats helped me from the IRC room, much appreciated

---

### Post by Joe of loath on 2011-06-20
What you quoted answers all your questions - it explains what to do, and has working links for the files you need.

---

### Post by jamespoo on 2011-06-21
i read around there was an 3.1 android for this device ive put 2.2 on mine but cant find 3.1 i did find a link on mediafire but it was dead

---

### Post by Joe of loath on 2011-06-21
3.x are tablet-oriented releases, they won't be great on a netbook like this.

---

### Post by jamespoo on 2011-06-21
here is android 2.2 work on my 2.2 just format sd card and copy file to root of sd put in the netbook sd slot turn on install and your done this is the only one that has worked for me all others after install gave me black screen 

[http://www.cheap-hack.com/files/wm8505/android/UNGoogle_0.3.7_wm8505_V2_mod.zip](http://www.cheap-hack.com/files/wm8505/android/UNGoogle_0.3.7_wm8505_V2_mod.zip)

---

### Post by akq on 2011-06-25
Hey guys,
I have read almost all of posts here, but I still don't know what to do.. I have a 7" netbook with VT8500 - it seems that's the same as in first post. The problem is, when I download any of system mentioned here and prepare SD Card with Fat32 and Script folder, my computer doesn't recognize it while booting and loads Windows CE. I guess that is something wrong with a boot loader, but i don't know how to change or install it - there is no bios nor any setup. Do you know any sites with step by step intructions how to resolve my problem? Or anyone of You know how to help me?

---

### Post by scu-ba-de-buntu on 2011-06-25
> **akq said:**
> Hey guys,
I have read almost all of posts here, but I still don't know what to do.. I have a 7" netbook with VT8500 - it seems that's the same as in first post. The problem is, when I download any of system mentioned here and prepare SD Card with Fat32 and Script folder, my computer doesn't recognize it while booting and loads Windows CE. I guess that is something wrong with a boot loader, but i don't know how to change or install it - there is no bios nor any setup. Do you know any sites with step by step intructions how to resolve my problem? Or anyone of You know how to help me?

you need to tell the firmware where to pull data from. Try hitting F1 or that zzz/f1 button. its been a while so i don't remember which one gets you to firmware. then there may be a password ztr or something.

---

### Post by akq on 2011-06-25
@scu-ba-de-buntu:

I have tried it many times - there is no key that cause any reaction during system boot. My netbook doesn't show any information how to enter firmware setup, Windows CE starts at once. It completely ignores SD card with script folder. Do you have any idea?

---

### Post by scu-ba-de-buntu on 2011-06-28
Are you sure it is a VIA? what is its brand/labeling?

You should still be able to write to it with something. You may have to connect something on the inside however.

---

### Post by jagotu on 2011-07-07
Hello. I bought one of these (on the box it says "Ez book"). I was playing with it and now it stays on "Loading device drivers...". But if I put some script on SD card and put it into laptop, it does nothing. It just normally tries to boot wince and stays on loading drivers. I don't have any message before wireless book screen appears. No press F1, no machine info, just nothing. Is there any way to fix it?

---

### Post by Thanitos on 2011-07-24
Hello everyone. I have been following this topic for a very long time waiting for someone to post a file I could use with my China made mini netbook from ebay, with an ARM WM8505 300 MHz processor and an 800*480 7" screen. I have tried COUNTLESS Linux and Android files but to no avail, I have also lost the Windows CE 6.0 Script folder I have saved. Does anyone have an Android or Linux Script folder to work with my set up and a windows CE file to revert this machine to factory?

---

### Post by WendyB on 2011-07-25
I'm almost finished with a new version Gentoo 'distro' which I have tested on a VT8500 BV7.
Other hardware might work, but I have never tested it.

In my version the netbook should at least do something when inserting the SD-card with the scriptcmd directory

If you use my version and end up with a garbled display or stalled boot-process then that's good news: it works (almost).;)

Here are the former versions for download:
[http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList](http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList)

passwd for root is 'easypc12'

---

### Post by Cheetles4 on 2011-07-25
Hey, I'm completely new to the whole Linux thing. I understand basic Linux terms and stuff, but otherwise I'm a complete noob. 

Anyway, the thread is quite interesting because of it's potential applications. I have found a mini netbook that runs android 2.2 native with an 800mhz Via arm 8650. Is there a Linux distro that I can run on it?

I want to know since if I can download a Linux distro there is a possibility to run small games like Starcraft, or quake or even Half Life on the netbook, thus transforming it into a tiny gaming device. I would also like to know if this is possible. Thanks

---

### Post by justsomeguy11 on 2011-07-27
> **WendyB said:**
> I'm almost finished with a new version Gentoo 'distro' which I have tested on a VT8500 BV7.
Other hardware might work, but I have never tested it.
 
In my version the netbook should at least do something when inserting the SD-card with the scriptcmd directory
 
If you use my version and end up with a garbled display or stalled boot-process then that's good news: it works (almost).;)
 
Here are the former versions for download:
[http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList](http://trac.freya-webtechniek.nl/trac/Linux_VT8500/wiki/DownloadList)
 
passwd for root is 'easypc12'
 
can you PLEASE PLEASE PLEASE PLEASE and once more PLEASE do something for the WM8505 as well....lol....i seem to be in the group of people that CANNOT do anything with it ! it always just hangs when trying to load ANYTHING into it. and if i shut it off because of the hanging and it boots back up it just hangs on the logo screen. and boy o boy i've tried EVERY different script out there, and they all do the exact same damn thing......NOTHING...lol....all i can do is sit back and keep watching these sites for someone to finally fix this crazy *** problem ... and no one seems to know why these units won't load the scripts (or whatever the OS is called). of if someone does know i've never been able to get an answer why....so i BEG of you to do a WM8505 as well.lol...i bought the unit from the classifieds for my 5 year old to have her own laptop..but when i got it home and plugged it in all i had was a black screen so i've never even been able to use it..lol...i currently have it ripped apart (which was the only way i was able to find out it was a WM8505) because these chinesse clones are horrible when your trying to find a model # or anything like that..
 
anyways, thanks for hopefully helpin a dude out !!!! lol
 
cheers,

---

### Post by Thanitos on 2011-07-27
> **justsomeguy11 said:**
> can you PLEASE PLEASE PLEASE PLEASE and once more PLEASE do something for the WM8505 as well....lol....i seem to be in the group of people that CANNOT do anything with it ! it always just hangs when trying to load ANYTHING into it. and if i shut it off because of the hanging and it boots back up it just hangs on the logo screen. and boy o boy i've tried EVERY different script out there, and they all do the exact same damn thing......NOTHING...lol....all i can do is sit back and keep watching these sites for someone to finally fix this crazy *** problem ... and no one seems to know why these units won't load the scripts (or whatever the OS is called). of if someone does know i've never been able to get an answer why....so i BEG of you to do a WM8505 as well.lol...i bought the unit from the classifieds for my 5 year old to have her own laptop..but when i got it home and plugged it in all i had was a black screen so i've never even been able to use it..lol...i currently have it ripped apart (which was the only way i was able to find out it was a WM8505) because these chinesse clones are horrible when your trying to find a model # or anything like that..
 
anyways, thanks for hopefully helpin a dude out !!!! lol
 
cheers,

Not only that but windows CE 6 on these things is just horrible, it just seems like a fat and over sized OS for these things and I would love to get Linux on it because frankly I'm starting to grow on Linux over Windows. 'Sadly Windows looks at his large space capacity shrinking beneeth his feet as Linux slowly consumes all that is Windows.' 

I have tried almost all the methods for the ARM8505 and I just get stuck at installing or booting or what have you. The one that requires Fat 32 and EXT2 just wont find the Extpart.tgz file no matter how I place it on the SD card and in Ubuntu the card gets locked and I need root permission to put anything on and I am not THAT skilled (or skilled at all for that matter) with ubuntu

---

### Post by jl2 on 2011-07-30
TPB has a torrent for wm8505. I found that via blekko, second page of results, or thereabouts.
[https://thepiratebay.org/torrent/6019823/7__Mini_Netbook_WM8505_%28ce6.0_android__linux%29](https://thepiratebay.org/torrent/6019823/7__Mini_Netbook_WM8505_%28ce6.0_android__linux%29)
There is also projectgus which, if I remember, has a fair bit on the 8505 netbooks.
I cant help any further than that, because .. mine is 8500.

---

### Post by deaddonky on 2011-08-02
I've just came into ownership of* [this]("http://www.amazon.co.uk/Archos-501540-Arnova-Samsung-533MHz/dp/B003I7CNNE")* netbook. However, it seems to be a branded version:

[http://www.menqgroup.com/products/pro/E102a.asp](http://www.menqgroup.com/products/pro/E102a.asp)  

It has a samsung s3c2450 533mhz, 128mb RAM and 2gb flash.  It has a 10 inch screen, 3 USB ports, microphone and headphone jacks, and an sdcard port.  The Operating system is Windows CE 6.  

I've been following this thread with interest, but there there is much to read. It is my hope that I can boot a working Linux on my machine. However, what would be needed in order for this to happen? Any help on this would be really appreciated.  

Thanks, 
Mark

---

### Post by vinceCOOK on 2011-08-02
Hi JL2

This appears to be the only working LINK for getting hold of the "easyPC linux 0.2" operating system for netbooks.

Non of the other links work from this forum.

Also, long google searches and other forums revealed no
way of getting hold of "easyPC linux 0.2"

So thanks for that

Vince.



> **jl2 said:**
> TPB has a torrent for wm8505. I found that via blekko, second page of results, or thereabouts.
[https://thepiratebay.org/torrent/6019823/7__Mini_Netbook_WM8505_%28ce6.0_android__linux%29](https://thepiratebay.org/torrent/6019823/7__Mini_Netbook_WM8505_%28ce6.0_android__linux%29)
There is also projectgus which, if I remember, has a fair bit on the 8505 netbooks.
I cant help any further than that, because .. mine is 8500.

---

### Post by vinceCOOK on 2011-08-02
hello

yes. Your link also has the ANGSTROM LINUX operating system
for the wm8050 chip machines. That is real handy.

"mini2440simpleX11GnomeMatchbox-image-mini2440"

(that is the operating system file above....it's a Linux
Operating system)

Vince.

---

### Post by vinceCOOK on 2011-08-02
Hello

your link also helps by mentioning "daupara" under Linux
operating systems

I searched that word above and it brings you to the proper
FULL Debian Linux with x11 and fluxbox ....for wm8050 chip
machines.

here is that operating system file for download.

[http://www.daupara.de/wm8505_linux/extpart.tgz](http://www.daupara.de/wm8505_linux/extpart.tgz)

Basically, your link shows FOUR versions of linux for these
netbooks. There is infact a FIFTH version now which is free
and is based on Gentoo and works on vt8500 chip machines.

The best Linux for the wm8050 machines is what i have listed
above here.

I wonder if this Debian Linux above will work on wm8650 chip
machines. It's a faster newer chip inside netbooks

Thanks

Vince.

---

### Post by vinceCOOK on 2011-08-02
Hello

i have found so much about these netbooks today.

You can now run Android 2.2 Froyo on the wm8050 machine.

This android has full proper flash support in the web browser.

All the details about this android version are at

[http://projectgus.com/2010/11/froyo-android-2-2-alpha-hack-for-eken-m001/](http://projectgus.com/2010/11/froyo-android-2-2-alpha-hack-for-eken-m001/)

it also works on SLATES containing the wm8050 chip.

There are, infact, lots of Debian linux builds for the chinese
slates with wm8050 chips.

Vince.

---

### Post by Spider-Web on 2011-08-06
Well, after spending 2 hours scrolling and digging here's interesting link, i guess it was not mentioned before. It installs Debian on arm wmt8505, so with proper will you may make it install Ubuntu as well. Good Luck all
 
uh oh [http://blog.chinaunix.net/space.php?uid=23225855&do=blog&cuid=2367230](http://blog.chinaunix.net/space.php?uid=23225855&do=blog&cuid=2367230)

---

### Post by GreatGeak on 2011-09-23
Hello gents.
I recently purchased one of these fancy little netbooks, and I kind of wanted to join in the fight.

For every OS/Update/flash I attempt, I seem to get an error message like massproduction.bat not found. This appears when the command prompt comes up, before the operating system even loads.

It's frustrating because everything that works for everyone else, does not seem to work for me.

Here's the processing info:
Processor
 
[LIST]
[*]Processor Type: VIA ARM 32bit CPU
[*]Processor Clock Speed: 266M Hz
[*]Processor/Manufacturer: VIA
[*]Processor Model: VIA-ARM 920
[/LIST]

---

### Post by pierreyy on 2011-10-31
im in desperate need of help!




[http://ubuntuforums.org/showthread.php?p=11412547#post11412547](http://ubuntuforums.org/showthread.php?p=11412547#post11412547)



please check it out!  thanks in advance!

---

### Post by nadimvirus on 2011-12-07
> **dwinston91 said:**
> So it must be an SD card? Can it be a USB Flash Drive?
 
ple can u help me i cant download this file but i want this file ple help

---

### Post by nadimvirus on 2011-12-07
> **dwinston91 said:**
> So it must be an SD card? Can it be a USB Flash Drive?
 sir i m wating 4your reply

---

### Post by jl2 on 2011-12-22
nadimvirus::
Kid, dwinston91 has not posted for 9 months. So if you want that file, you have to tell us what its name is.

---

### Post by dervxerox on 2011-12-27
I've managed to get my netbook to boot linux thanks to WendyB's instructions but as my touchpad is busted (doesn't work in Wince either) I'm unable to test the GUI. How do I persuade my usb mouse to work?

---

### Post by ghostship on 2012-01-27
> **vinceCOOK said:**
> Hello

your link also helps by mentioning "daupara" under Linux
operating systems

I searched that word above and it brings you to the proper
FULL Debian Linux with x11 and fluxbox ....for wm8050 chip
machines.

here is that operating system file for download.

[http://www.daupara.de/wm8505_linux/extpart.tgz](http://www.daupara.de/wm8505_linux/extpart.tgz)

Basically, your link shows FOUR versions of linux for these
netbooks. There is infact a FIFTH version now which is free
and is based on Gentoo and works on vt8500 chip machines.

The best Linux for the wm8050 machines is what i have listed
above here.

I wonder if this Debian Linux above will work on wm8650 chip
machines. It's a faster newer chip inside netbooks

Thanks

Vince.

Hello everybody,

after hours of work i finally managed to boot this Distribution posted in the Link above.
Now I don't know the Login data. Please could somebody post Login and password?

Thanks to everybody.

---

### Post by jl2 on 2012-02-08
root/toor
[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=27](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=27)
If that does not work, search for passwordless login, and change /etc/passwd /etc/shadow on the SD card

---

### Post by dudesky1325 on 2012-03-22
Hey guys, I recently dusted off my mini crap book because while browsing the android maarket on my phone, I found multiple apps that install linux flavors to phones. The requirements match that of our little netbooks so if youre able to install the new 2.2 version that has been made available to us (at bentolinux.org or earlier in this thread) then you should be able to use this app that installs linux inside android. I have yet to try but I will be back as soon as I do, good luck!

---

### Post by JMichaelAnderson on 2012-05-06
Just bought a Sylvania Smartbook, SYNET07WICV, after reading the comments below concerning this product and Linux, is there any new news on how to erase windows and replace with ubuntu?

Michael

---

### Post by OooBuntuRox on 2012-06-08
> **Spider-Web said:**
> Well, after spending 2 hours scrolling and digging here's interesting link, i guess it was not mentioned before. It installs Debian on arm wmt8505, so with proper will you may make it install Ubuntu as well. Good Luck all
 
uh oh [http://blog.chinaunix.net/space.php?uid=23225855&do=blog&cuid=2367230](http://blog.chinaunix.net/space.php?uid=23225855&do=blog&cuid=2367230)


I am getting a 404/ not found error on this link. I'm also a bit skeptical about clicking on a blind link to china unix. Lots of malware and hacking over there. No?

---

### Post by OooBuntuRox on 2012-06-08
> **JMichaelAnderson said:**
> Just bought a Sylvania Smartbook, SYNET07WICV, after reading the comments below concerning this product and Linux, is there any new news on how to erase windows and replace with ubuntu?

Michael

I haven't succeeded with it yet. I did read an article some time back that claimed the newer versions of Ubuntu would include ARM versions in Ubuntu.

---

### Post by OooBuntuRox on 2012-06-19
> **OooBuntuRox said:**
> I haven't succeeded with it yet. I did read an article some time back that claimed the newer versions of Ubuntu would include ARM versions in Ubuntu.

Additional Comment: I was able to load Android 2.2 along the way but there are many icons that don't function. I'm not very impressed or interested in using Android.

Is it possible to take advantage of the Android installation and use it's layout to install Linux over it?

Thanks, OoobuntuRox :guitar:

UPDATE: I found the links below. Some look like they have promising info but they are talking about extracting a tar.z file. I'm lost there. I haven't work with tar files. Can someone try this out and pitch in with the rest of resolving this? They instructions say you can install debian. That may be close enough. Once that is done, maybe ubuntu can be substituted. I am also wondering about a distro called DSL (dam small linux). Maybe that offer a solution too.


[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/INSTALL](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/INSTALL)

**WM8505 Debian - abrasive <abrasive@axdf.net> april 2010**
How to INSTALL to your WM8505 based netbook: WARNING - this will destroy all user data - no warranty is given as to whether it will work, make your hair catch fire, or melt the screen off your netbook!  1. Create a single, large FAT partition. 2. Extract the 'fatpart.tgz' archive to the partition 3. in the 'script' folder so created, replace 'scriptcmd' with 'scriptcmd.install' 4. copy 'extpart.tgz' into the root  When you are done, there should be 1 folder (script) and 1 file (extpart.tgz) in the root of the SD card. Boot from the card, wait a while. It will ask you to remove the card, at which point it will reboot into your new Debian install!


[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/README](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/README)

[B]WM8505 Debian - abrasive <abrasive@axdf.net> april 2010
[/B]Creating a bootable SD card:     You need at least a 256MB card. 1. Format the card with partitions:     1. FAT (32MB will do)     2. EXT2  (rest of the card) 2. extract fatpart and extpart to the FAT and EXT2 partitions, resp.  Card will boot to a text console, and won't touch any existing install (eg. WinCE).   Handy notes: to reduce console spam on tty1, run dmesg -n 1  to enable wifi, modprobe rt3070sta to disable,     rmmod rt3070sta (see also wi-on and wi-off scripts under 'useful')  sound is untested in this release  the kernel sets the system time from the RTC, but not vice versa; the driver interface is unknown     configure the time with 'date' and use /sbin/wmt-rtc --sys2hw  release includes apt-get, you should set up /etc/apt/sources.list for a local mirror you may wish to mkdir /var/log/apt wpa_supplicant is included also.  mtd(block)7 is a small (~300mb) flash partition; mtd9 is the rest of flash (~1.7gb)  X11 works fine; if you have a large enough card.  apt-get install xserver-xorg-video-fbdev xfonts-base xinit and your favourite wm. the package scripts get the X conf wrong, you need to add:     Driver "fbdev" to the Device section in /etc/X11/xorg.conf (a working xorg.conf is under 'useful')

[http://projectgus.com/files/abrasive_mirror/wm8505_linux/useful/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/useful/)


**_MISC links:_**

[http://www.linuxquestions.org/questions/programming-9/linux-on-arm-processor-756154/](http://www.linuxquestions.org/questions/programming-9/linux-on-arm-processor-756154/)

[http://www.armedslack.org/](http://www.armedslack.org/)

[http://www.armedslack.org/doku.php?id=installation](http://www.armedslack.org/doku.php?id=installation)

[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=193]("http://devio.us/%7Enextvolume/via_arm/viewtopic.php?id=4&t_id=193")

[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/)

[http://www.linuxquestions.org/questions/linux-embedded-78/compile-code-for-arm-processor-703336/](http://www.linuxquestions.org/questions/linux-embedded-78/compile-code-for-arm-processor-703336/)


**[COLOR=SeaGreen]Updating to include Instructions on extracting Tar files[/COLOR]**
_**Extracting Tar Files:**_

[http://www.unix.com/unix-dummies-questions-answers/5692-extracting-tar-file.html](http://www.unix.com/unix-dummies-questions-answers/5692-extracting-tar-file.html)

in order to extract a tar file use the command

tar - xvf filename

and to zip it give

tar -cvf filename

---

### Post by iggybeans on 2012-06-26
I have a friend who has a functioning Debian distro that uses an Android kernel.
He's supposed to send me a copy of his SD card.

---

### Post by OooBuntuRox on 2012-07-01
> **iggybeans said:**
> I have a friend who has a functioning Debian distro that uses an Android kernel.
He's supposed to send me a copy of his SD card.

Is it something you can share? I have the WM8505 not the VT8505. I wonder if it will work.


I have the Bento version working about half way. Bento boots up to the point where it searches for the SD card then just sits there with the progress bar scrolling.

OooBuntuRox :guitar:

---

### Post by jl2 on 2012-07-03
SD card has to be R/W Some of these books are upside down & you have to set it RO WM is another name for VT

---

### Post by OooBuntuRox on 2012-07-04
> **jl2 said:**
> SD card has to be R/W Some of these books are upside down & you have to set it RO WM is another name for VT

Yeah, the card is W/R and I was sure to leave the lock tab off. I figured that the os would try to write temp files to the sd card. Yes, the card slot is upside down. RO? Are you saying it needs to be locked to avoid disk writes?

Regarding VT vs WM, I am surprised to hear that they are the same. One site I went to made a big deal out of making sure you have the correct image and weather you had VT or WM. It had easylinux listed for VT and Bento Linux listed for WM. I opened the CMD file and I am wondering if the reason it doesn't boot is because the search path isn't set correctly. I'm not sure how to verify what my actual SD device path is though. I think it may be flash3 or similar. even if it is, I'm not sure how to update linux. Do I have to do a built as part of any updates? Or, can I update the cmd file like DOS autoexec.bat and config files?

It seems that most people have there sd boot cards working about 50 to 75% of the way. 

have to go. OooBuntuRox, :guitar:

So what do you say Iggybeans. any chance you can share that working image of the sd card?

---

### Post by jl2 on 2012-07-07
Some boards have a bug, and  you have to set your SD card RO to make it RW...
Also, if you crash or poweroff you might need to run e2fsck on the card (sda2) before it will boot. That sounds like what is happening to you.

If you want droid, try modroid if you can find it. It was on Megaupload. 

The problem is not Via or WonderMedia, the problem re easy & bento is the CPU .
When it boots, and you are on the net, apt-get update followed by apt-get upgrade It is debian. Expect the first upgrade to be biggish.

---

### Post by OooBuntuRox on 2012-07-07
> **jl2 said:**
> Some boards have a bug, and  you have to set your SD card RO to make it RW...
Also, if you crash or poweroff you might need to run e2fsck on the card (sda2) before it will boot. That sounds like what is happening to you.

If you want droid, try modroid if you can find it. It was on Megaupload. 

The problem is not Via or WonderMedia, the problem re easy & bento is the CPU .
When it boots, and you are on the net, apt-get update followed by apt-get upgrade It is debian. Expect the first upgrade to be biggish.

Thanks for your help.

I looked into modroid. people are complaining that it knocks out the wifi. I don't want to loose wifi. It also seems that an 8605 and 8705 have been released since this 8505 So its getting harder to find people devoted to working on them. a few sites are now closed and simply say "DON'T BUY ONE".

I came across an interesting site called: [http://www.yourwarrantyisvoid.com](http://www.yourwarrantyisvoid.com)

It has a section on the hardware internals. I'm going to ad the links to the long list that I have gathered so far. When I get it all figured out,  hope to edit and drop the extraneous information.

Regarding bento Linux, There may be a few things with the SD card I am using.  I partitioned an 8gb SD card with a few 2 GB partitions. I may drop to a smaller card to see if it helps. Each time the card hangs, I do a full format and set t up again. I may have a swap area on it. I have since heard that can cause problems. So I have to remove it if it's there. But the configuartion of linux I am using may be affecting the image too. I am going to try a different Linux box (basic, no security, etc) and start from scratch. 

Thanks, OooBuntuRox :guitar:

---

### Post by OooBuntuRox on 2012-07-07
> **OooBuntuRox said:**
> Additional Comment: I was able to load Android 2.2 along the way but there are many icons that don't function. I'm not very impressed or interested in using Android.

Is it possible to take advantage of the Android installation and use it's layout to install Linux over it?

Thanks, OoobuntuRox :guitar:

UPDATE: I found the links below. Some look like they have promising info but they are talking about extracting a tar.z file. I'm lost there. I haven't work with tar files. Can someone try this out and pitch in with the rest of resolving this? They instructions say you can install debian. That may be close enough. Once that is done, maybe ubuntu can be substituted. I am also wondering about a distro called DSL (dam small linux). Maybe that offer a solution too.


[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/INSTALL](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/INSTALL)

**WM8505 Debian - abrasive <abrasive@axdf.net> april 2010**
How to INSTALL to your WM8505 based netbook: WARNING - this will destroy all user data - no warranty is given as to whether it will work, make your hair catch fire, or melt the screen off your netbook!  1. Create a single, large FAT partition. 2. Extract the 'fatpart.tgz' archive to the partition 3. in the 'script' folder so created, replace 'scriptcmd' with 'scriptcmd.install' 4. copy 'extpart.tgz' into the root  When you are done, there should be 1 folder (script) and 1 file (extpart.tgz) in the root of the SD card. Boot from the card, wait a while. It will ask you to remove the card, at which point it will reboot into your new Debian install!


[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/README](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/README)

[B]WM8505 Debian - abrasive <abrasive@axdf.net> april 2010
[/B]Creating a bootable SD card:     You need at least a 256MB card. 1. Format the card with partitions:     1. FAT (32MB will do)     2. EXT2  (rest of the card) 2. extract fatpart and extpart to the FAT and EXT2 partitions, resp.  Card will boot to a text console, and won't touch any existing install (eg. WinCE).   Handy notes: to reduce console spam on tty1, run dmesg -n 1  to enable wifi, modprobe rt3070sta to disable,     rmmod rt3070sta (see also wi-on and wi-off scripts under 'useful')  sound is untested in this release  the kernel sets the system time from the RTC, but not vice versa; the driver interface is unknown     configure the time with 'date' and use /sbin/wmt-rtc --sys2hw  release includes apt-get, you should set up /etc/apt/sources.list for a local mirror you may wish to mkdir /var/log/apt wpa_supplicant is included also.  mtd(block)7 is a small (~300mb) flash partition; mtd9 is the rest of flash (~1.7gb)  X11 works fine; if you have a large enough card.  apt-get install xserver-xorg-video-fbdev xfonts-base xinit and your favourite wm. the package scripts get the X conf wrong, you need to add:     Driver "fbdev" to the Device section in /etc/X11/xorg.conf (a working xorg.conf is under 'useful')

[http://projectgus.com/files/abrasive_mirror/wm8505_linux/useful/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/useful/)


**_MISC links:_**

[http://www.linuxquestions.org/questions/programming-9/linux-on-arm-processor-756154/](http://www.linuxquestions.org/questions/programming-9/linux-on-arm-processor-756154/)

[http://www.armedslack.org/](http://www.armedslack.org/)

[http://www.armedslack.org/doku.php?id=installation](http://www.armedslack.org/doku.php?id=installation)

[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=193]("http://devio.us/%7Enextvolume/via_arm/viewtopic.php?id=4&t_id=193")

[http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/)

[http://www.linuxquestions.org/questions/linux-embedded-78/compile-code-for-arm-processor-703336/](http://www.linuxquestions.org/questions/linux-embedded-78/compile-code-for-arm-processor-703336/)


**[COLOR=SeaGreen]Updating to include Instructions on extracting Tar files[/COLOR]**
_**Extracting Tar Files:**_

[http://www.unix.com/unix-dummies-questions-answers/5692-extracting-tar-file.html](http://www.unix.com/unix-dummies-questions-answers/5692-extracting-tar-file.html)

in order to extract a tar file use the command

tar - xvf filename

and to zip it give

tar -cvf filename


[B][COLOR=SeaGreen]Updating to include links to hardware information and more Bento Linux info:

[COLOR=Black]Interesting articles from a site called: [COLOR=SeaGreen]your warranty is void .com

[/COLOR][/COLOR][/COLOR][COLOR=SeaGreen][COLOR=Black][COLOR=SeaGreen][COLOR=Black]Hardware Inside the box! : [/COLOR][/COLOR][/COLOR][/COLOR][/B]
[http://www.yourwarrantyisvoid.com/2011/01/08/hardware-pr0n-sylvania-netbook-from-cvs/](http://www.yourwarrantyisvoid.com/2011/01/08/hardware-pr0n-sylvania-netbook-from-cvs/)
[B]
Comments on Windows CE or Linux:[/B] 
[http://www.yourwarrantyisvoid.com/2011/07/25/cvs-netbook-revisited/](http://www.yourwarrantyisvoid.com/2011/07/25/cvs-netbook-revisited/)

OooBuntuRox, :guitar:

Update: I think my problem is that I am incorrectly or unsuccessfully extracting my compressed files. I am getting the script folder in the fat partition without trouble but I am using windows7 and 7Zip (or P7Zip) to do that. When I use Linux to extract my ext files I am getting an error. I think it is due to file permissions. I keep getting an error. The files appear to extract but I don't think they are writing to the disk correctly. There are error messages with each file.

---

### Post by jl2 on 2012-07-08
"Dont buy one" is good advice. I got a Tosh TE2100 for a lot (75%) less. However there is the thrill of the chase to consider.
Make 2 directories, one 30 or 40MB fat, the other a big linux, ext2 or 3 or 4, does not matter.
unpack the fatpart, copy the extpart (I hope my recall is correct) into/onto the small FAT dir.
Insert into SD slot. power on. away you go.
If you get your script dir, then things are working up to that point.
That way you do not risk your UBOOT or anything else inside the WM rom. 
Then install whatever you need. stay away from gnome. It will cripple  your netbook. That leaves openbox & lxde & icewm & jwm. wicd  for your network. and disable syslog.  your other friend is mc
** I am using a modroid wifi driver in my Abrasive-Debian install ** It  works so I dont know what they are talking about. ** i just checked on a  modroid netbook, and wifi works **
Sound crashes the system. I even try a usb sound dongle, still crashes. Apart from that, it works.
To extract a tar file tar -xf tarfile.tar  To uncompress it add z,j, or J  depending on how it was compressed.  tar -zxf tarfile..gz :: -jxf  tarfile.bz2  :: -Jxf tarfile.xz
What sort of error? like no space left on device? or permission  denied???? no space means you are on sda1, not sda2. permission meas you  have to be root.

---

### Post by jl2 on 2012-07-08
you have to be root otherwise you get permission denied, or operation not permitted when you do tar -zxf extpart.tgz
in fact i remember now, root is necessary to give the correct permisisons to the files. Otherwise it will not work.

---

### Post by OooBuntuRox on 2012-07-15
> **americanman28 said:**
> These things suck

:grin: Yup. I thought there would be hardware hacks to stack memory, etc. A year later, Nope!  Still a paperweight. I like the size and the weight. I got it to work  fine with CE6 (stock OS). Well, fine as far as connecting o wifi,  checking email. But it is a dog for browsing the net, youtubing, etc.

Like Tim Taylors son (of tool-time) used to say: You might as well throw  it up against the wall now and save yourself a lot of headaches.

---

### Post by OooBuntuRox on 2012-07-15
> **jl2 said:**
> you have to be root otherwise you get permission denied, or operation not permitted when you do tar -zxf extpart.tgz
in fact i remember now, root is necessary to give the correct permisisons to the files. Otherwise it will not work.

I was trying to extract it using the gui. I looked for an as admin option. I was avoiding the command line because I knew I'd screw up the path. Is there an easy way to sudo in the gui?

Also Ubuntu has encryption installed. I wasn't sure if that might be affecting it.

---

### Post by OooBuntuRox on 2012-07-15
> **jl2 said:**
> "Dont buy one" is good advice. I got a Tosh TE2100 for a lot (75%) less. 

[COLOR=Blue]I know. I got a used lappy for $25. Its the weight and no spinning hd platters that I like on the smartbook. Flip it any which way you want while using the smartbook.[/COLOR]

However there is the thrill of the chase to consider.

[COLOR=Blue]Thats about what it boils down to. I thought I'd learn or gain something from it. Aside from learning patience, I haven't learned much from it.[/COLOR]

Make 2 directories, one 30 or 40MB fat, the other a big linux, ext2 or 3 or 4, does not matter.

[COLOR=Blue]directories or partitions? I think you mean partitions. Thanks. I may have given up on it. A lot of people put them back to stock from what I see. I wouldn't have mind android on it if you could work with it easier. A lot of icons were locked to the desktop and didn't work either.[/COLOR]

unpack the fatpart, copy the extpart (I hope my recall is correct) into/onto the small FAT dir.
Insert into SD slot. power on. away you go.
If you get your script dir, then things are working up to that point.
That way you do not risk your UBOOT or anything else inside the WM rom. 
Then install whatever you need. stay away from gnome.
[COLOR=Blue]
...less and less reason for me to pursue this..[/COLOR]

It will cripple  your netbook. That leaves openbox & lxde & icewm & jwm. wicd  for your network. and disable syslog.  your other friend is mc
** I am using a modroid wifi driver in my Abrasive-Debian install ** It  works so I dont know what they are talking about. ** i just checked on a  modroid netbook, and wifi works **
[COLOR=Blue]
...beyond my current abilities. I wouldn't know where to begin.[/COLOR]

Sound crashes the system. I even try a usb sound dongle, still crashes. Apart from that, it works.
To extract a tar file tar -xf tarfile.tar  To uncompress it add z,j, or J  depending on how it was compressed.  tar -zxf tarfile..gz :: -jxf  tarfile.bz2  :: -Jxf tarfile.xz
What sort of error? like no space left on device? or permission  denied???? no space means you are on sda1, not sda2. permission meas you  have to be root.

[COLOR=Blue]I think it was probably permissions or similar. I was extracting them with the gui on one box, ten copying the files to the sd card. But I am certain the errors occurred during the extract. I went back and looked/ tried it several times.

Now I see there is an WM8650 out there. And one of these Sylvanias that comes stock with Android on it.

I may come back to it at a later time... or just get something different that is still light. I played with pandigital, then got rid of it. I may have settled on a netbook for now.
[/COLOR]
[COLOR=Blue]Thanks everyone. OooBuntuRox [/COLOR]:guitar:

---

### Post by nick1221 on 2012-08-28
Is there an operating system that would work on my computer with a WM8505 processer? A link to the download with instructions would be perfect. Because I can't seem to find one.

---

### Post by karamel4e on 2012-09-01
Hello,

):P  My first post. I have one of these netbooks - Jay Tech UMPC 9901 with WinCE installed. Following the instructions in this threat I am trying to put some other OS on it. I decided to start with the live Debian (not to break the windows for now). I managed to start it with an SD card only (not the USB). It is working fine. It drops me to the "wiliam" prompt. What I'd like to do now is install X11. Unfortunately, I do not know how to configure the network adapters in CLI. I've done this once or twice in ubuntu previously but most of the commands are "command not found". Not sure what to do now. In this threat, it is said to use "modprobe rt3070sta" to enable wifi. When I write this I get no error message. 

In other words, could you please tell me how to connect to internet?

 Thanks

---

### Post by sdse78 on 2012-09-09
> **nick1221 said:**
> Is there an operating system that would work on my computer with a WM8505 processer? A link to the download with instructions would be perfect. Because I can't seem to find one.

I'm looking for the same thing myself. Abrasive if you're still on the forum could you please offer up some help. 

I found your files here. [http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/](http://projectgus.com/files/abrasive_mirror/wm8505_linux/1.0/)

However, when I format my SD card FAT it seems it cannot be found.

I get this message "Can't find extpart.tgz on SD card!"

It's there so what is the problem? Why can't it read the file?

---

### Post by jl2 on 2012-09-10
[http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=12&page=1](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=12&page=1)
search wondermedia abarasive
you have to be root.
my card has a small fat part, with a script directory, and a big ext part which has the OS . i also have a swap part, and another ext part for keeping some files which might be useful in the future, if we have a big flash crash.

---

### Post by sdse78 on 2012-09-14
> **jl2 said:**
> [http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=12&page=1](http://devio.us/~nextvolume/via_arm/viewtopic.php?id=4&t_id=12&page=1)
search wondermedia abarasive
you have to be root.
my card has a small fat part, with a script directory, and a big ext part which has the OS . i also have a swap part, and another ext part for keeping some files which might be useful in the future, if we have a big flash crash.

Hi! Thanks so much for posting. Everything I try doesn't seem to work. Did you get it to work for yourself? If so, can you tell me how you did it minus abrasive's method. I've tried his and it does not work. I'm almost thinking it's not possible for it to work on my machine. :shock:

I have a red Sylvania Smartbook.

[http://www.sylvaniacomputers.com/product.php?id_product=41]("http://www.sylvaniacomputers.com/product.php?id_product=41")

---

### Post by xorgnak on 2012-11-12
I have one, and it's currently running abrasive debian.  I use it without X11, but it's apparently possible.  There are a few issues to be dealt with, but it's great.  It's small enough to almost fit in my pocket, and with aplay or cmus it makes an excellent mp3 player.  I recommend one to anyone.  And honestly, I'd be happy to have the community.

---

### Post by HiRez_L on 2013-01-16
If anyone is still interested in these, Newegg has them on sale for 30 bucks.  I'm thinking of picking one up, so I can work on debian on it.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16834684003&Tpk=synet07526](http://www.newegg.com/Product/Product.aspx?Item=N82E16834684003&Tpk=synet07526)

---

