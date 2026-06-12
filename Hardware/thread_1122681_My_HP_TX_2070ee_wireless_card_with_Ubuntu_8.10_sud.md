---
title: "My HP TX 2070ee wireless card with Ubuntu 8.10 suddenly stopped functioning !!!!"
date: 2009-04-11
forum: Hardware
---

### Post by Obituaryfreak on 2009-04-11
Hi I tried not to post a new thread but I couldn't find my answer in the SOMEHOW RELATED posts ,so I`m posting this..
I have an HP 2070ee Tablet with the Interpid installed on it which has been running smoothly for 4 month using its internal wireless card. Its not even listed under the connection list in Network Settings and yet not connected in the lspci with the following result:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
---------
Here is my uname -a output : 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
---------
and iwconfig output:
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.
---------
The funny thing is it doesn't even exit when I left click on the two monitors.
I checked the HP web site for the Broadcom drivers and the featured ones were:Broadcom 802.11 a/b/g WLAN Broadcom 802.11 b/g WLAN Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter
which are supported on my laptop.
---------
Besides I must say that I tried the ndisgtk to install the drivers (bcmwl6.inf),but was of no success it still says Hardware present:No).
Theres even no log in the dmesg output which mentions the ord WIRELESS.](*,)

2 more things which may help
he output of my lshw is :
 *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:21:be:e6:5b:b7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
1st thing is it doesn't show any thing about the wireless card and only shows the Ethernet card
and the 2nd thing is that the ethenet card as you can see is featured in Disabled status which is really freaking me out cuz I`m using my Ethernet connection right now sending you this thread!
please leave me a note because I`m completely nuts at the moment.:shock:

---

### Post by Obituaryfreak on 2009-04-11
I even reinstalled Intrepid but my internal wireless card is not detected 
It sounds like it is broken or something ...
The blue-tooth Icon is still available though :mad:
Uh come on where are the Ubuntu Grus at?

---

### Post by Favux on 2009-04-12
Hi Obituaryfreak,

So you don't have Windows available?  Obviously the easiest way would be to boot into Windows and seeing if the wireless works.  That would rule out a hardware failure in your Broadcom chipset.

Try:
```
lshw -C network
```
If there is no driver listed or it says unclaimed then you don't have a driver installed.

Go back to System>Administration>Hardware Drivers and either activate Broadcom STA wireless driver (wl) or deactivate it reboot and reactivate it.  Then see if the above command shows it.

---

### Post by Obituaryfreak on 2009-04-12
Thanks Favux
I did
echo wl | sudo tee -a /etc/modules
and I guess that fixed it
I guess the wl module needed to be fed to the kernel.
And now when the system boots Its working.
The thing is I upgraded to 9.04 and it automatically fixed it.
But after I restarted the system again there was no wireless...
i rebooted the system 4 times and for the 4th time I could use the wireless
so I doubted that the kernel doesnt seem to load the module in an appropriate way and I fed it to the kernel and now after the restart 
its up and running.
I hope nothing goes wrong cause so far I`m quite confused...
But it is working now....
:guitar:

---

### Post by Favux on 2009-04-12
Hi Obituaryfreak,

Good!  Glad you've got it working.

How is your Wacom working?  Info and advice for Jaunty available here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)
and here:  [http://ubuntuforums.org/showthread.php?t=1090343](http://ubuntuforums.org/showthread.php?t=1090343)

---

### Post by Obituaryfreak on 2009-04-12
thanks dude
thats exactly what I`m trying to do next...
I will give the feed back;)

---

### Post by Obituaryfreak on 2009-04-12
dude what do mean by rt kernel?

---

### Post by Favux on 2009-04-12
The rt is for real time kernel that some music guys need to reduce latency.  Be sure to read the links so you can make the decision on how to go informed.

---

### Post by Obituaryfreak on 2009-04-12
ok thnx 
dude I get an error  here
vahid@RockerGeek:~/Desktop/linuxwacom-0.8.2-2$ sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
cp: cannot stat `./src/2.6.27/wacom.ko': No such file or directory

and I checked and I dont have the following directory : /wacom.ko

---

### Post by Favux on 2009-04-12
Hi Obituaryfreak,

Since you are in Jaunty you probably need to change the "./src/2.6.27/wacom.ko" of the copy command to "./src/2.6.28/wacom.ko".  If that works for you I'll add it to the HOW TO.

Did you remember to make sure that "libhal1-dev" is not installed?  And you're compiling 0.8.3-2 not 0.8.2-2, correct?

---

### Post by Obituaryfreak on 2009-04-12
Hi favux
i got an error again :cp: cannot stat `./src/2.6.28/wacom.ko': No such file or directory

I checked theres not a 2.6.28 directory in there
and inside the 2.6.27 directory I got
drwxr-xr-x  2 vahid vahid   160 2009-04-13 00:11 .
drwxr-xr-x 23 vahid vahid   704 2009-04-13 00:11 ..
-rw-r--r--  1 vahid vahid  1496 2009-04-13 00:11 Makefile
-rwxr-xr-x  1 vahid vahid  1491 2009-01-19 20:58 Makefile.in
-rwxr-xr-x  1 vahid vahid  6019 2009-01-19 20:58 wacom.h
-rwxr-xr-x  1 vahid vahid 15740 2009-01-19 20:58 wacom_sys.c
I hope that helps theres not a wacom.ko in that.
:confused:

---

### Post by Obituaryfreak on 2009-04-12
sorry man for my being confused,
but I`m dong according to the how to
and please tell me how to find which one (0.8.3-2 not 0.8.2-2) is which ..
and I just removed libhal1-dev  
I am so sorry man...

---

### Post by Favux on 2009-04-12
Hi Obituaryfreak,

No worries, just slow down.  Go back through the the HOW TO using 0.8.3-2 instead of 0.8.2-2.  Use the arrow key to go back on the command and change the 2 to a 3.  Then arrow back to the end of the command and enter.  If the copy (cp) command doesn't work change the 7 to an 8, ie 2.6.27 to 2.6.28.  Or copy the commands you need to change to a text editor (gedit) and then copy and paste the edited commands.

And please let me know if you had to change the copy command.

---

### Post by Obituaryfreak on 2009-04-12
if I have understood your point correctly
I`m using linuxwacom-0.8.2-2.tar.bz2 here..which is according to the how to..

---

### Post by Favux on 2009-04-12
Right, but you should be using linuxwacom-0.8.3-2.tar.bz2.  That's what I mean by changing the 0.8.2-2 default in the HOW TO to the 0.8.3-2 development branch that you are trying to install.

---

### Post by Obituaryfreak on 2009-04-12
I`m on it..
ok its done
vahid@RockerGeek:~/Desktop/linuxwacom-0.8.3-2$ sudo cp ./src/2.6.28/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
I compiled and installed linuxwacom-0.8.3-2.tar.bz2 and changed 27 to 28 and yipiiiiiiii there was no error so far...
and guess its time to reboot for the mentioned reasons ...

---

### Post by Favux on 2009-04-12
Hi Obituaryfreak,

Outstanding!

And thanks for letting me know I have to add a modified copy command for Jaunty.

---

### Post by Obituaryfreak on 2009-04-12
ok so far good
my touch screen is working with the first reboot (lucky me ).
it needs the rest of the how to though
cause the pen is auto left clicking...
but so far many tnx for ur kind help
ill continue this tomorrow and let you know about my progress):P
its 2 am and my wife is ready to kill me...8-[

---

### Post by Favux on 2009-04-12
Don't want that.  Let me know how it goes.  Sounds good so far.

---

### Post by Obituaryfreak on 2009-04-13
Hi Favux
The wireless is acting weird again it disappeared ,its not functioning properly since last night I rebooted the system 5 times
just one time it showed the wireless connection,and as I mentioned before
when it comes up with no wireless It means no wireless at all...
I want to know if theres a way to make the system detect and load the module when it boots .
Regards

---

### Post by Favux on 2009-04-13
Hi Obituaryfreak,

Sorry to hear that.  I'm afraid I'm not a wireless guru.  Other than check for "wl" and modprobe it I'd suggest what I did before.  Deactivating Broadcom STA rebooting and reactivating it and see how it does through the next couple of boots.

I dimly remember something about adding or changing a script in /etc/init.d/ both for your situation and for problems with wireless on waking from suspend.  But I won't swear to it.

---

### Post by Obituaryfreak on 2009-04-13
Hi Favux
The output of the modprobe is :
vahid@RockerGeek:~$ modprobe wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
and thats weird too ...

---

### Post by Favux on 2009-04-13
Actually I was about to reply and then I reread it.  It doesn't make any sense to me either.  You're not using ndiswrapper.  That is weird.

---

### Post by Favux on 2009-04-13
Did you ever install ndiswrapper in your struggles?  Did you remove it or black list it?

---

### Post by Obituaryfreak on 2009-04-13
ndsiwrapper is already installed and I haven't removed it...
u got a better idea ,,I will be your hands ,,you just let me know bro

---

### Post by Favux on 2009-04-13
Hi Obituaryfreak,

Well I don't know if its a better idea or not.  But folks with a TX200 aren't using ndiswrapper.  They're using Broadcom STA, the proprietary driver like I am.  Unless you are a purist and object to proprietary drivers.  This may be your problem (using the ndiswrapper driver).

Going back to post #3 where I said go to:   "System>Administration>Hardware Drivers and either activate Broadcom STA wireless driver (wl) or deactivate it reboot and reactivate it."  Anyway if Broadcom STA is there I would remove the ndiswrapper driver and install or activate it.  If it is already activated that may be the problem right there.  Two conflicting drivers.

Got to go.  Later.

---

### Post by Obituaryfreak on 2009-04-13
damn
still nothing I returned to Intrepid and still no wireless

---

### Post by Favux on 2009-04-13
Hi Obituaryfreak,

So you are back in Intrepid.  Using Broadcom STA?  Does anything happen?  I have a TX2000 (TX2110us) also.  With Broadcom STA.  I had problems with it because of my router.  It has a hidden SSID and WPA2.  But I found a work-around for it.

There are a few big wireless threads maintained by wireless gurus.  If you join them they tend to be very helpful.

---

### Post by Obituaryfreak on 2009-04-17
duh
you have no idea ,,,what I`ve been through this week.](*,)](*,)](*,)
to give you an general overview of the current situation :
I`m on Hardy now ,,,,I did the no fluff HOWTO on a fresh Hardy on my notebook
and It  worked like a charm  ......I even tried to make sure to makeit permanent according to the how to!!! but damn after the first reboot ,,,again there was no wireless,,,,and after that nothing could save me but reinstalling the Hardy again and go through the NO FLUFF! procedure and again failure 
Is there a guy who could help me
I really need the wireless card on my laptop
You know whats freaking me out,,,,4 month ago I installed Intrepid on this machine and the wireless was working flawlessly to the point that I did`nt  realize that wireless is one of the issues with my system and the only issue is Screen rotate and the stylus and fantasy stuff like that....
I`d rather use some help b4 moving to a psychologist!!!](*,)](*,)](*,)](*,)

---

### Post by Obituaryfreak on 2009-04-17
tell you what...broadcom STA never appears in my restricted Hardware list,,the only thing which appears is nvidia graphic card driver...

---

### Post by Favux on 2009-04-17
Hi Obituaryfreak,

That's probably a big fat clue if I knew anything about wireless.  Broadcom STA not appearing.  We must have the same wireless chipset.  Does wireless work in Windows?  What Broadcom chipset does Windows say you have?  Which version does Ubuntu say you have?  In System>Administration>Software Sources is Proprietary drivers for devices (restricted) checked?

This thread contains the sum total of what I know about wireless, as miniscule as it is:  [http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)  It's how I got Broadcom in Intrepid to work with my router.

You need to search the forums with "Broadcom" and "wireless" and etc. and find the commands that let you look at your hardware like "lspci".  Then post on one of the active guru threads.  I've seen them walk people through.  You also need to stop version hopping.  Settle on one  version and plug away at it.  It took me at least 6 weeks to discover the solution in the thread above.

---

### Post by Obituaryfreak on 2009-04-17
Hi Favux
Yes download restricted drivers ... is checked
and about the windows I must say that again yes It used to work out of the box for 1 year..and ok I stop changing the versions . 
and about the version ,,this is what is published in the HP web site :
Broadcom 802.11 a/b/g WLAN Broadcom 802.11 b/g WLAN Broadcom 4321AG 802.11a/b/g/draft-n Wi-Fi Adapter Broadcom 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter
and when I got it to work it was detected BCM4312 rev 01.

---

