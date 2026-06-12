---
title: "Amilo M7400"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by nekr0z on 2006-06-05
Kubuntu installed just good, here is what's working out of the box and what's not:

1. ACPI seems to have issues.
After enabling the energy saving option of the laptop screen, the screen doesn't switch off actually, but simply goes black. The backlight keeps working, so no energy saving is actually done.
Pressing sleep button (Fn+F2) makes laptop go to sleep mode, but waking from sleep mode all I see is black screen, until I switch the power off and boot up again.
Trying to enable hibernation by power off button in KDE control center made laptop to switch off as soon as KDE starts. Having no idea of how to deal with it, I just reinstalled Kubuntu and quit playing with ACPI for a while.

2. External CRT monitor doesn't work at all, whatever I do.
*Solved, the manual is [here]("http://www.ubuntuforums.org/showpost.php?p=1114272&postcount=5").*

3. No complete support for card reader (RS-MMC works with no problems, same for SD, MMC Plus doesn't work, other cards not tested).

4. No support for left panel buttons (programmable), nor for Fn+key combinations (volume up/down, mute and stuff).
Fn+left and Fn+right (brightness up/down) work ok (they seem to be hardware), as well as Fn+F4 (display off).
*Solved, the manual is [here]("http://www.ubuntuforums.org/showpost.php?p=1105038&postcount=4").*

5. WiFi (Intel 2200BG) working if switched on by default in BIOS (which is not good for energy-saving). WiFi button doesn't work at all. WiFi LED doesn't work either.
[I]Found a way to override BIOS settings, details are [here]("http://www.ubuntuforums.org/showpost.php?p=1134099&postcount=7"). WiFi button works with [a little script]("http://www.ubuntuforums.org/showpost.php?p=1143495&postcount=8").
[This]("http://www.ubuntuforums.org/showpost.php?p=1281506&postcount=10") makes the led work.[/I]

6. Touchpad working out of the box, but no scrolling zones or scrolling button work.
*Solved, the manual is right below.*

7. Sound seems to work out of the box.

8. Network works, no issues.

9. Same for USB.

10. Built-in modem works after installing sl-modem-daemon from multiverse.

11. FireWire (aka IEEE-1394) works out of the box.

12. TV-out, PC-card, IR-port not tested so far.

I would highly appreciate any help or ideas on how to make things work [better].

---

### Post by nekr0z on 2006-06-06
Issue 6 solved.

Comment out (put the # in the beginning) every line corresponding wacom in /etc/X11/xorg.conf, then put the following section:> Section "InputDevice"
  Driver	"synaptics"
  Identifier	"touchpad"
  Option	"Device"  	"/dev/psaux"
  Option	"Protocol"	"auto-dev"
  Option	"LeftEdge"      "1700"
  Option	"RightEdge"     "5300"
  Option	"TopEdge"       "1700"
  Option	"BottomEdge"    "4200"
  Option	"FingerLow"	"25"
  Option	"FingerHigh"	"30"
  Option	"MaxTapTime"	"180"
  Option	"MaxTapMove"	"220"
  Option	"VertScrollDelta" "100"
  Option	"MinSpeed"	"0.09"
  Option	"MaxSpeed"	"0.18"
  Option	"AccelFactor"	"0.0015"
  Option	"SHMConfig"	"on"
EndSection and a line in ServerLayout section: > InputDevice    "touchpad"      "AlwaysCore"Working like a dream.

---

### Post by nekr0z on 2006-06-06
Card reader (issue 3) seems to be actually supported in current version of kernel. I only have an MMC Plus card to test, and this card seems to be not yet supported, although it produces some messages in dmesg. More information is at [http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd), but I don't feel like chattering with kernel at my state of Linux-experience... Any reports welcome.

---

### Post by nekr0z on 2006-06-06
Issue 4 solved:

First of all, you need the [acerhk driver]("http://www2.informatik.hu-berlin.de/~tauber/acerhk/"). Download it, unpack, then come down to the directory where the unpacked files are. You need **build-essentials** and **kernel-headers** packages installed to do the following:> make
make install
Now run the driver:> sudo modprobe acerhk

The driver starts working and reporting keycodes of the keys pressed. Now you can have any program to get them and perform some actions. Hotkeys works just good:
> sudo apt-get install hotkeys
Create a configuration file amilom7400.def into /usr/share/hotkeys/, file should read something like this:> <?xml version="1.0"?>

<definition>

  <config model="Fujitsu-Siemens Amilo M7400">

    <Help         keycode="245"/>

    <Mute         keycode="160"/>
    <VolUp        keycode="176" adj="2"/>
    <VolDown      keycode="174" adj="2"/>

    <WiFi	  keycode="147"/>               # Hotkeys doesn't actually have WiFi alias, this is put only for convenience. Change it into something else to work.
    <WebBrowser   keycode="178"/>
    <Email        keycode="236"/>
    <Prog1        keycode="159"/>
    <Prog2        keycode="151"/>

  </config>

  <contributor>
    <name>nekr0z</name>
    <email>nekr0z@mail.ru</email>
  </contributor>

</definition>
Now edit /etc/hotkeys.conf to provide necessary commands (for example, "WebBrowser=firefox"). Add "Kbd=amilom7400" so that the needed config file is used by default.

Run hotkeys from console and here it goes!

---

### Post by nekr0z on 2006-06-08
Well, issue 2 seems solved, at least I could finally get my Compaq P700 CRT work with Amilo M7400 in all possible modes. The most uncomfortable thing is you cannot switch them "on the fly", X server has to be restarted for the changes to apply.


**Mode 1: external (CRT/LCD) or internal (LFP) only**

Change the "Monitor" section in /etc/X11/xorg.conf so that it corresponds to your monitor properly. For the LFP it should be something like this:
> Section "Monitor"
	Identifier	"Notebook LFP"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

And here is a sample of what I use for my Compaq P700:
> Section "Monitor"
	Identifier	"Compaq P700"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-120
	Modeline	"1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814    -HSync +Vsync
EndSection

The "Identifier" field in "Screen" section of xorg.conf should be exactly as in your desired monitor's section (in my example, "Notebook LFP" for LFP and "Compaq P700" for CRT).

Now select the necessary monitor: either put an option in BIOS (to start with external monitor by default or not), or press Fn+F3 to choose monitor at the very beginning of the bootup process. Note that the monitor you choose at this point is the monitor you get to work, no matter what is in xorg.conf, so make sure you have the needed options already in xorg.conf.


**Mode 2: clone screens**

In this examlpe your external LCD/CRT's resolution must not be over 1024×768, as this is the maximum for LFP to operate. Also note that you need your CRT selected at the boot (see previous section) if you desire refresh rates of more than 85Hz.

The "Device" section in /etc/X11/xorg.conf should be like:
> Section "Device"
	Identifier	"Intel 855GME External"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"		"CRT,LFP"
	VideoRam      65536
	Option		"Clone"			"true"
	Screen		0
EndSection
Note that the order of monitors in "MonitorLayout" option doesn't meen anything: Pipe A is assigned to the monitor that is selected on X start, no matter which one is listed first (this seems to be a bug, but so it is).

The "Monitor" section should correspond to your CRT/LCD.


**Mode 3: dual head configuration**

Now you need two "Device" sections in your xorg.conf. Here is an example:
> Section "Device"
	Identifier	"Intel 855GME External"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"		"CRT,LFP"
	VideoRam	65536
	Screen		0
EndSection

Section "Device"
	Identifier	"Intel 855GME Internal"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"MonitorLayout"		"CRT,LFP"
	VideoRam	65536
	Screen		1
EndSection

You need two "Monitor" sections as well, each corresponding to one of the used monitors:
> Section "Monitor"
	Identifier	"Notebook LFP"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Monitor"
	Identifier	"Compaq P700"
	Option		"DPMS"
	HorizSync	30-92
	VertRefresh	50-120
	Modeline	"1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814    -HSync +Vsync
EndSection

Now two "Screen" sections, each binding a monitor to a video device (make sure "Identifier" fields are the same you used in previous sections):
> Section "Screen"
	Identifier	"notebook"
	Device		"Intel 855GME Internal"
	Monitor		"Notebook LFP"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"monitor"
	Device		"Intel 855GME External"
	Monitor		"Compaq P700"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768_100.00"
	EndSubSection
EndSection


And now, finally, you need the following lines is "ServerLayout" section:
> Screen		0 "notebook"
Screen		1 "monitor" RightOf "notebook"
Option           "Xinerama"   "On"  ##This is an option to have Windows-like dual monitor desktop behaviour. OpenGL is not supported in this mode.

Here it goes. For X to start seamlessly with this config, the LFP should be selected on bootup (in this case the "Pipe A" bug works vice versa, I don't know why)!

---

### Post by nekr0z on 2006-06-13
Tested the card reader with RS-MMC: works without any issues. Card is detected whe plugged, opens in Konqueror and can be easily mounted. MMC Plus still not working.

---

### Post by nekr0z on 2006-06-13
Issue 5 partly solved.

Get the latest fsam7400 module [here]("http://linux.zwobbl.de/pub/") (currently, 0.4.0 is the latest available). Unpack the files, go to that directory in console and do:> make
sudo make install
Now do:> sudo modprobe fsam7400 uid=1000 autoload=0
If uid=1000 (1000 is default, you may need to change it to your User ID) is not there, you need superuser rights to do the following. GID is also supported.
> echo 1 > /proc/driver/wireless/radio
will turn the WiFi card on. The same command with 0 instead of 1 turns it off.

You may also want to have this module loaded by default. Just add this line:> fsam7400 uid=1000 autoload=0 radio=0
to your /etc/modules, and you no longer need to modprobe for it every time you reboot. Here radio=0 is used to have WiFi off by default, this is good for energy-saving when running on battery.

---

### Post by nekr0z on 2006-06-15
I have written a little script that makes WiFi button work:
> #!/bin/bash
# This script, which was written by Evgeny "nekr0z" Kuznetsov in 2006
# based on Mute script by Moritz Beller (2004),
# is licensed under the terms of the GPL

WIFI_REPORT=$(cat /proc/driver/wireless/radio | grep radio)

if [ "$WIFI_REPORT" == "  radio state is OFF" ]  ## 2 spaces before the word "radio" here, not one!
then
        echo 1 > /proc/driver/wireless/radio
else
        echo 0 > /proc/driver/wireless/radio
fi

exit 0

This script can be put in /usr/bin with a name like wifi_button.sh, and then you can bind wifi_button.sh to WiFi button in hotkeys.conf.

---

### Post by nekr0z on 2006-07-03
Built-in modem works good after installing sl-modem-daemon package (from multiverse repository).

---

### Post by nekr0z on 2006-07-20
Got WiFi led working!

Edit the /etc/modprobe.d/ipw2200 (create one if it is not there), and put a line in it:```
options ipw2200 led=1
```

---

### Post by berg82 on 2006-08-28
Hello, 

I have an Amilo M7400 and a TFT 19-inches external monitor from Sony. 

Have I understood you correctly if I say that you cant switch between the monitors even in console mode? 

I want to have 1280x1024 on the external monitor and I want to be able to switch between them. 
I often put my laptop in to "Suspend to ram" and then I take it with me to school. What happend if I suspend my laptop to Ram when on my external display and then wake it up when the external display is unpluged?

Best Regards 
Andreas 

> **nekr0z said:**
> Well, issue 2 seems solved, at least I could finally get my Compaq P700 CRT work with Amilo M7400 in all possible modes. The most uncomfortable thing is you cannot switch them "on the fly", X server has to be restarted for the changes to apply.


**Mode 1: external (CRT/LCD) or internal (LFP) only**

Change the "Monitor" section in /etc/X11/xorg.conf so that it corresponds to your monitor properly. For the LFP it should be something like this:


And here is a sample of what I use for my Compaq P700:


The "Identifier" field in "Screen" section of xorg.conf should be exactly as in your desired monitor's section (in my example, "Notebook LFP" for LFP and "Compaq P700" for CRT).

Now select the necessary monitor: either put an option in BIOS (to start with external monitor by default or not), or press Fn+F3 to choose monitor at the very beginning of the bootup process. Note that the monitor you choose at this point is the monitor you get to work, no matter what is in xorg.conf, so make sure you have the needed options already in xorg.conf.


**Mode 2: clone screens**

In this examlpe your external LCD/CRT's resolution must not be over 1024×768, as this is the maximum for LFP to operate. Also note that you need your CRT selected at the boot (see previous section) if you desire refresh rates of more than 85Hz.

The "Device" section in /etc/X11/xorg.conf should be like:

Note that the order of monitors in "MonitorLayout" option doesn't meen anything: Pipe A is assigned to the monitor that is selected on X start, no matter which one is listed first (this seems to be a bug, but so it is).

The "Monitor" section should correspond to your CRT/LCD.


**Mode 3: dual head configuration**

Now you need two "Device" sections in your xorg.conf. Here is an example:


You need two "Monitor" sections as well, each corresponding to one of the used monitors:


Now two "Screen" sections, each binding a monitor to a video device (make sure "Identifier" fields are the same you used in previous sections):


And now, finally, you need the following lines is "ServerLayout" section:


Here it goes. For X to start seamlessly with this config, the LFP should be selected on bootup (in this case the "Pipe A" bug works vice versa, I don't know why)!

---

### Post by nekr0z on 2006-08-28
Well, berg82, you actually can switch **between** the monitors from console (there are i810switch and i855crt packages that do the trick). But if you want to switch from stand-alone to dual-head mode, or from clone-screen to dual-head, forget it — you'll have to restart X :-(

I actually didn't try to get more than 1024×768 resolution on external monitor, you can try and play with xorg.conf, and post here or email me directly, and I'll try to cooperate and help with what I can (I anyway want all the things to work, huh).

And about suspend-to-ram, well, I really have no idea what can happen. As I have already posted here, my M7400 doesn't wake from suspend at all, so I have no chance to try. You can try and post here what you get, so we can try to work it out.

And by the way: if you have any idea on how to get my M7400 to wake from suspend, I would highly appreciate any help!

---

### Post by berg82 on 2006-08-29
Hey, 

ok, Thanx for your help. Im going to play a around with the settings in xorg and try the i855swith. 

The Suspend-to-ram worked out of the box for me. 
The only thing I have configures is the following: 

1. Install the fsam7400 module. You have to rmmod this one before your computer gå into sleep. Put it in your /etc/acpi/sleep.sh script. 

2. Rmmod the ipw2100 module in your sleep.sh 

3. Modprobe those 2 modules in your resume.sh 

It works with these settings for me right after the Dapper installation. 

Earlier I tried to put my computer into sleep mode when running the Kubuntu version. But that failed. Now I run the original Ubuntu version with Gnome instead. 

Let me know if you already have tried this. 

Best Regards 
Andreas

---

### Post by berg82 on 2006-08-29
> **nekr0z said:**
> Well, berg82, you actually can switch **between** the monitors from console (there are i810switch and i855crt packages that do the trick). But if you want to switch from stand-alone to dual-head mode, or from clone-screen to dual-head, forget it — you'll have to restart X :-(

I actually didn't try to get more than 1024×768 resolution on external monitor, you can try and play with xorg.conf, and post here or email me directly, and I'll try to cooperate and help with what I can (I anyway want all the things to work, huh).

And about suspend-to-ram, well, I really have no idea what can happen. As I have already posted here, my M7400 doesn't wake from suspend at all, so I have no chance to try. You can try and post here what you get, so we can try to work it out.

And by the way: if you have any idea on how to get my M7400 to wake from suspend, I would highly appreciate any help!

Im up playing with my monitor settings now. I have new installation of Ubuntu and a clean xorg.conf file. 

I installed the i810switch package and tried the following: 

i810switch lcd on (I booted the computer with the crt plugged and witch the Bios setting Auto. 

Nothing happends when I tried the above command. I am in console mode after I have done a: /etc/init.d/gdm stop 

i810switch crt on and crt off works as a charm. 

Do I need to use the i855crt too? 

When I boot my computer, I can switch between LCD and CRT when I am in the Grub loader menu but then it stops to work. 

Do I have to change the Bios settings and use "LCD only"? 

Best Regards 
Andreas

---

### Post by nekr0z on 2006-08-29
Well, I have all the setiings you mentioned in sleep.sh and resume.sh already, but the picture is still sad: suspend-to-disk works, suspend-to-ram ends in the famous blank-screen-issue.

Maybe the reason is I have originally installed Kubuntu, and migrated to Ubuntu later. If this is the case, I keep on hoping that some update will solve the things up. The same thing was with network-manager: it refused to work in KDE, didn't work in GNOME (altough everybody said I had all the needed configs), and then, all of a sudden, I found it working after some update... Maybe something like this will happen. I hope. Anyway, I'm not going to reinstall, because this M7400 is my production machine, and I don't think that making suspend-to-ram work is worth setting up the whole environment again.

Now about i810switch: on my system it works like a dream, with all options working (I can even switch both displays off and then type the on-switching command blindly). I have «LCD only» option enabled in my BIOS.

As for i855crt, I'm not that advanced as to understand what way can those additional options it provides (compared to i810switch) help me in my environment, or even WTF do that options mean. If you give it a try and make use of it, be sure to post it ;-)

Another useful thing is i810rotate. It doesn't have any options, but works exactly as Fn+F3 (if only I knew the keycode for Fn+F3, I would bind i810rotate to it).

---

### Post by berg82 on 2006-08-29
Ok, 

network-manager doesn't work for me either. I used another tool for managing wireless networks before. But I can´t remember the name of it. I tell you when I find it. 
I have also problem with the FN key. I tried to found out the key-code with "xev" but nothing happened when I hit the Fn-key. 
Im going to try to find a solution for the Fn key and I tell you if I succeed. 

To my i810switch problem. 
I have tried the following: 

1. Start my computer and hit F2 to get into Bios. 
2. Changed monitor setting to: "LCD only" 
3. Booted Linux in "safe mode" or whatever you call it. 
4. At the command promt I tried the following: 
                 - i810switch lcd off 
                   This switched the lcd of. It works! 
         
                 - i810switch lcd on 
                   This also works for me 

If I try:        - i810switch lcd off 
                 - i810switch crt on 
The result is that I can see that the CRT monitor wakes up from sleep mode but I can´t see the console promt.  
When the result is black like above I try to start Gnome manager (X-server)
and then the LCD wakes. Why does the LCD wakes up here and not the CRT? 

I then did a shutdown of X and went back to console mode and tried the following: 

1. i810switch crt off 
2. i810switch lcd off 
3. i855crt on 1280x1024@75 
4. Startx 
And the same thing here. The LCD monitor goes on but nothing happends to my CRT except that it is waking up from sleep. 

Im not sure if I understand exactly how the XServer really works. At this point I haven´t made any changes to my Xorg file. 

If I have the Bios monitor Setting to "Auto": 
Start the computer with the CRT unplugged. everythings work at a resolution  of 1024x768@75. 

If I have the sam Bios settings as above but have the CRT monitor plugged in it works to at a resolution of 1280x1024@75. 

I have also tried the above things in "normal mode", not "save mode". 

Do you have any idea of what goes wrong? Can it be a conflict between my LCD - graphic card - CRT (TFT) monitor? 

Do I have to change something in xorg.conf even if I just want to switch between the monitors in console mode?

---

### Post by berg82 on 2006-08-29
Hello again, 

One thing more, 

When I do do the wollowing: 

1. i810switch lcd off 
2. i855crt on 1280x1024@75 

I get an error: "Creating display mirror on pipe A, Enabling CRT and connecting to pipe A, Xfree connection failed. No XV overlay option available". 

What does it mean? 

/Andreas

---

### Post by nekr0z on 2006-08-30
I don't know, honestly. I'm actually usually very scared when I hear about "overlay" :)))

"Fn" key itself does not produce a keycode, and shouldn't. But the combinations (Fn+F1, Fn+F2, Fn+F11 etc.) do produce a separate keycode each. I just wonder what's the one for Fn+F3.

I haven't tried all these i810switch-acrobatics in text mode, I just use terminal when logged in GNOME. And all works. Your problem may be that X.org, when being initialized, refers more to what's written in xorg.conf that to what's going on right at the moment...

As a matter of fact, I do believe that X.org completely reinitializes video system when starts, so in order to start X.org with different monitor settings you have to tweak xorg.conf. And the console mode... Well, I don't quite understand which way is video system configured in console, except for BIOS setup and Fn+F3 key, so I can only make guesses...

---

### Post by berg82 on 2006-08-31
Hey. 

Thank you for your help. 

It works now in 1024x768 on both monitors. But I want to run 1280x1024 on my external TFT monitor. 
I have heard that it has been som problems with this driver (i810). 

Andreas

---

### Post by nekr0z on 2006-08-31
Do you run clone-screen or dual-head? If it is clone-screen, then I seriously doubt that you can have exactly the same picture on two monitors with different resolution.

---

### Post by berg82 on 2006-08-31
I have tried booth Dual-head and clone but nothing works with resolution 1280x1024. 
I can have a cloned screen with one monitor at 800x600 and one on 1024x768. 

/Andreas

---

### Post by nekr0z on 2006-08-31
I'll give it a try if I have time this weekend, with my bro's CRT that supports resolutions up to 1600×1200 (mine doesn't), and report here.

---

### Post by berg82 on 2006-08-31
I realy apreciate your help! 

Thank you very much!

Andreas

---

### Post by morpher on 2006-10-22
dude i love you, marry me! :D

u saved me alot of browsing and frustration! u rock ^^

---

### Post by DarkN00b on 2006-10-22
It is actually very common for you to have a black screen avter resume-from-suspend. This happens with my HP. If I just type my password (even though the screen is off) and hit enter, everything comes up fine.

---

### Post by nekr0z on 2006-10-22
DarkN00b, I wish I could say the same, but... I can type all the password in the world, but the only way to bring my screen back to life is rebooting.

---

### Post by nekr0z on 2006-10-22
morpher, sorry, dude, I'm comfortable with my girlfriend, but I'm glad this thread helped you. If you ever find anything useful for M7400, that is lacking in this thread, you're welcome to post it here.

---

### Post by morpher on 2006-10-22
aww too bad u have a gf lol... jk ;)

anyway, most of what u said worked for me, except
* the touchpad part, that screwed up my X (it wouldnt start... thank god for xorg.conf backups!), but i dont really care much about it for now, wireless is priority!
*the wireless button script.

the script u made only turns off the radio, it doesnt turn it back on, i dunno why :( i have to echo 1 in console to turn it back on... what did i do wrong?

another thing: whats the code for the hotkey conf i should put on wifi? i have 
```
WiFi=bash /usr/bin/wifi_button.sh
Email=evolution
WebBrowser=firefox
Prog1=et
```
and they all work except WiFi... when i run hotkeys, it says:
> hotkeys: The key command "WiFi" is invalid
and then it doesnt run the script cuz the radio doesnt change...

im sure u noticed im not a pro at all, so try to keep it as simple as u can, for me and other dumb ppl alike :) lol

thanks for even trying!

---

### Post by nekr0z on 2006-10-22
Your problem with Hotkeys is that Hotkeys has a limited number of "names" for buttons, and "WiFi" is not one of them. If you read my example of amilom7400.def carefully, I have commented this issue there.

As for me, I use "Go" instead of "WiFi"

So, to get the thing to work you need to change the line with keycode 147 in /usr/share/hotkeys/amilom7400.def into
```
<Go           keycode="147"/>
```
and in hotkeys.conf, too:
```
Go=/usr/bin/wifi_button.sh
```
(see, no need for "bash" here).

Hope this works for you as it works for me.

Double check the script, because the one I've posted works good for me. I don't know what's wrong with yours. Explicitly check that line starting with "if", it should be exactly as I wrote, including the space after third «"».

Concerning xorg.conf, be sure to have commented out (put # in the beginning) every line about wacom, including those in ServerLayout section that deal with "stylus", "cursor" and "eraser". If you don't succeed, you can just e-mail me your xorg.conf so I can look for errors myself.

And don't be shy to ask questions anyway. The best thing about Linux is the people that help when you're stuck with something ;)

---

### Post by morpher on 2006-10-22
ppl like u :) thank u so much

to name the alias Go instead of WiFi solved the hotkey issue, i had misread ur comment on amilom7400.def ... lol

i still dont know whats different in my script(or pc?) cuz its a simple copy paste from he browser... so, yeah, the space is on that string that says radio is off. :( i think god is pickin on me lol

i have yet to retry the touchpad thing, but ill do it tomorrow :P today ill stick to celebrating my wireless freedom hehe... i think im gonna surf the net on my rooftop. ye... rooftop ^^

PS: could u mail me ur amilom7400.def to m0rph3r_at_gmail_dot_com so i use that? i dunno if the copy-paste got me some weird chars, and... well... u can never be too carefull! lol thanks in advance

---

### Post by nekr0z on 2006-10-23
I surely can mail you my amilom7400.def, as well as the script (and I'll do it in a couple of minutes ;)), but I have come to one deep thought that can help solving your problem today. Just for convenience: could you please post the <b>exact</b> output for
```
cat /proc/driver/wireless/radio
```
on your machine?

---

### Post by morpher on 2006-10-23
```
SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.5.0
  auto-off is ON, auto-load is OFF
  radio state is ON
```

i think its ok on that part :(

---

### Post by nekr0z on 2006-10-23
Yeah, this looks allright. By some reasons, 0.5.0 and 0.5.1 don't make on my system, so I'm stuck to 0.4.0 and cannot reproduce your config...

---

### Post by nekr0z on 2006-10-23
I appeared to have occasionally removed linux-headers... Now I have installed 0.5.1, but there still is no problem with the script...

---

### Post by nekr0z on 2006-10-23
morpher, dude, I emailed you the wrong version of the wifi_button.sh, that's my old non-functioning one. The one that works is the same as posted here in the thread, but there are 2 spaces after the 3rd " in that line, not one. I'll correct that in the thread.

---

### Post by morpher on 2006-10-24
i still cant get it to work :( even with 2 spaces...

i really apreciate ur help, but mb its just some freak sh*t and we cant correct it....

or... is it supposed to NOT work if im connected to a wireless network already? or mb something along those lines?

i think i'll move on to othe stuff now :)

Btw!! i was wondering... what about the infrared, do u have anything on that? ;) (sorry to put some extra things on you, but... well i guess u like it and i could use a hand lol)

again, thanks!

---

### Post by nekr0z on 2006-10-25
I have no other IR-capable device, so I simply have no chance to try. Even all the cellular phones in my family have Bluetooth instead of infrared.

---

### Post by morpher on 2006-10-25
ok ill try to do it myslef and then post it here if i get it right ;)

(ill probably start monday or something, cuz it my bday tomorrow and i have exams saturday and monday, so ill be busy till then...)

---

### Post by Joeboy on 2006-10-28
(message deleted)

---

### Post by nekr0z on 2006-11-02
Tested a card-reader with an SD card today — works like a dream. Same for FireWire: connecting a DV-camera and transferring video went just fine.

---

### Post by nekr0z on 2006-11-13
Guys, I've upgraded to 6.10 today, and I think it's a GOOD idea for everybody. First of all, the card-reader suddenly started reading all the cards I tried to plug in (tried everything available at the store, except for MemorySticks). Then, the video card started to recover when waking from suspend-to-ram, which used to be a real problem for me.

And, as if these two were not enough, Fn+F3 started working like a dream, which allows hotplugging a projector for a presentation, for example.

S-Video still doesn't work though, so I'm already losing patience awaiting for Ubuntu 7.04 ;-)

---

### Post by stefros on 2006-12-12
> **nekr0z said:**
> Got WiFi led working!

Edit the /etc/modprobe.d/ipw2200 (create one if it is not there), and put a line in it:```
options ipw2200 led=1
```


Hello,

it seems to be that some Amilo M 7400 User have the same problem with the right configuration of their WLAN-Card under Ubuntu.

I am also owner of an Amilo M 7400 and my WLAN isn´t working properly with permanently lightening up the WLAN-LED.

If its possible can you create a script for solving this problems, especially when these people - like me - have no big experience in the OS.

Thanks

Stefros

---

### Post by nekr0z on 2006-12-12
Hi, stefros!

I really want all the M7400 guys to get their hardware working in Ubuntu, and this is why this thread was written. I was a starter in Linux when I was writing all this, and I'm just an amateur right now. I would have composed a script to do all the things automatically, but the problem is: I don't know how to write scripts! I'm still just an amateur, you know...

Anyway, I know that at least one guy has set up all the things by doing exactly what's written in this thread (he reported in here), so this guide seems working, at least in Dapper. I myself have set up all in Dapper, and in Edgy as well — using exactly the steps I have written here...

Maybe if you give more information about what your problem is, we could talk it out and see what can be done about it together?

---

### Post by stefros on 2006-12-14
I am using the PRO/Wireless LAN 2100 3B Mini PCI card.

There is no driver for hotkey switches available.

Any suggestion for solving this problem?

---

### Post by stefros on 2006-12-17
I have problems with activating the hotkeys on my Amilo M 7400.

I am using Ubuntu 6.10, have loaded fsam7400 and put a line
in /etc/modules

stefan@stefan-laptop:~$ lsmod
Module                  Size  Used by
fsam7400                7196  0 

My iwconfig report says

stefan@stefan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

What can I do to activate my hotkeys?  

Have I to compile Acer HK ? I cannot get it, caused by damaged/wrong links.

Please help me!

---

### Post by stefros on 2006-12-17
> **nekr0z said:**
> Issue 4 solved:

First of all, you need the [acerhk driver]("http://www2.informatik.hu-berlin.de/~tauber/acerhk/"). Download it, unpack, then come down to the directory where the unpacked files are. You need **build-essentials** and **kernel-headers** packages installed to do the following:
Now run the driver:

The driver starts working and reporting keycodes of the keys pressed. Now you can have any program to get them and perform some actions. Hotkeys works just good:

Create a configuration file amilom7400.def into /usr/share/hotkeys/, file should read something like this:
Now edit /etc/hotkeys.conf to provide necessary commands (for example, "WebBrowser=firefox"). Add "Kbd=amilom7400" so that the needed config file is used by default.

Run hotkeys from console and here it goes!

Hi,

I am working with Ubuntu 6.10 (fsam7400 and ipw2100 modules already included)

I used modprobe ipw2100 & fsam7400 to load the modules.

After this I created configuration file "amilom 7400" and run hotkeys.

After running hotkeys I got the following message:

hotkeys: You must set the keyboard type, use hotkeys -t <type> to set it.

Do you know what I have to do ?

---

### Post by nekr0z on 2006-12-17
As far as I understand what you have written, your WiFi card was ON at the moment you did "iwconfig", which means the problem is not in hotkeys, but in cannecting to the wireless network itself.

What do you get from "cat /proc/driver/wireless/radio"?

---

### Post by stefros on 2006-12-19
> **nekr0z said:**
> As far as I understand what you have written, your WiFi card was ON at the moment you did "iwconfig", which means the problem is not in hotkeys, but in cannecting to the wireless network itself.

What do you get from "cat /proc/driver/wireless/radio"?


Sorry, for my late response.

SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.5.0
  auto-off is ON, auto-load is OFF
  radio state is OFF

The WLAN LED is lightening up permanently. When I am using 
stefan@stefan-laptop:~$ iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

Any idea ?

ppp0      Interface doesn't support scanning.

---

### Post by nekr0z on 2006-12-19
"radio state is OFF" in your output means that your WiFi card is OFF. And the fact you got some output at all means that your driver is working.
```
echo 1 > /proc/driver/wireless/radio
```
should turn the WiFi card ON, and the same line with "0" instead of "1" should turn it back OFF. You can check the output for```
cat /proc/driver/wireless/radio
```again to see if the card has turned ON. Try it and report here, then we will think on about your problem.

---

### Post by stefros on 2006-12-20
Thanks for your support. I appreciate this.

This is the output or your last thread:

stefan@stefan-laptop:~$ echo 1 > /proc/driver/wireless/radio
stefan@stefan-laptop:~$ cat /proc/driver/wireless/radio
SW RF kill switch for Fujitsu Siemens Amilo M 7400, v0.5.0
  auto-off is ON, auto-load is OFF
  radio state is ON
stefan@stefan-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:09:5B:B1:22:9C
                    ESSID:"main"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:68  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 5180ms ago
          Cell 02 - Address: 00:15:0C:F1:AA:89
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:12
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:41  Signal level:0  Noise level:0
                    Extra: Last beacon: 460ms ago
          Cell 03 - Address: 00:13:49:4B:9F:00
                    ESSID:"ArcorWirelessLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 48 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 54 Mb/s
                    Quality:65  Signal level:0  Noise level:0
                    Extra: Last beacon: 604ms ago
          Cell 04 - Address: 00:15:E9:0D:AB:D0
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:4
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:27  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : TKIP CCMP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 4140ms ago
          Cell 05 - Address: 00:09:5B:E7:F5:8E
                    ESSID:"marioworld"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:27  Signal level:0  Noise level:0
                    Extra: Last beacon: 13292ms ago

sit0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.


WLAN is running. But I have still the problem with my WLAN-LED. It is permanently lightening. Can I do nothing to control it?

---

### Post by stefros on 2006-12-20
> **nekr0z said:**
> I have written a little script that makes WiFi button work:


This script can be put in /usr/bin with a name like wifi_button.sh, and then you can bind wifi_button.sh to WiFi button in hotkeys.conf.


I think there is a mistake! You have to bind wifi_button.sh to your amilom7400.def-file.

My Wifi-Button is still not working. Sorry, to ask you again for support!

---

### Post by stefros on 2006-12-20
> **nekr0z said:**
> Your problem with Hotkeys is that Hotkeys has a limited number of "names" for buttons, and "WiFi" is not one of them. If you read my example of amilom7400.def carefully, I have commented this issue there.

As for me, I use "Go" instead of "WiFi"

So, to get the thing to work you need to change the line with keycode 147 in /usr/share/hotkeys/amilom7400.def into
```
<Go           keycode="147"/>
```
and in hotkeys.conf, too:
```
Go=/usr/bin/wifi_button.sh
```
(see, no need for "bash" here).

Hope this works for you as it works for me.

Double check the script, because the one I've posted works good for me. I don't know what's wrong with yours. Explicitly check that line starting with "if", it should be exactly as I wrote, including the space after third «"».

Concerning xorg.conf, be sure to have commented out (put # in the beginning) every line about wacom, including those in ServerLayout section that deal with "stylus", "cursor" and "eraser". If you don't succeed, you can just e-mail me your xorg.conf so I can look for errors myself.

And don't be shy to ask questions anyway. The best thing about Linux is the people that help when you're stuck with something ;)

I have modified and get the folowing error messages, when pressing the buttons:
hotkeys: Cannot launch Go: Permission denied (for WLAN-Button)
(evolution-2.8:8757): e-utils-WARNING **: Plugin 'Bogofilter Ausschuss-Erweiterung' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.8:8757): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:8757): DEBUG: mailto URL program: evolution (for Email-Button)

The firefox-Button is working fine.

Kind regards

Sefan

---

### Post by stefros on 2006-12-20
I will post you my files for checking, if you dont mind:

_**amilom7400.def**_

<?xml version="1.0"?>

<definition>

<config model="Fujitsu-Siemens Amilo M7400">

<Help keycode="245"/>

<Mute keycode="160"/>
<VolUp keycode="176" adj="2"/>
<VolDown keycode="174" adj="2"/>

<Go keycode="147"/> 
<WebBrowser keycode="178"/>
<Email keycode="236"/>
<Prog1 keycode="159"/>
<Prog2 keycode="151"/>

</config>

<contributor>
<name>nekr0z</name>
<email>nekr0z@mail.ru</email>
</contributor>

</definition>


**_HOTKEYS.CONF_**

############################################################
# Global configuration for hotkeys                         #
############################################################

# These are the default values.
# A line starting with # is a comment.

### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
Kbd=amilom7400
# CDROM=/dev/cdrom

# PrevTrack=xmms --rew
# Play=xmms --play-pause
# Stop=xmms --stop
# Pause=xmms --pause
# NextTrack=xmms --fwd
# Rewind=

  WebBrowser=firefox
  Email=Evolution --component=mail
  Calculator=xcalc
# FileManager=gmc
# MyComputer=gmc
# MyDocuments=gmc
# Favorites=gnome-moz-remote --remote=openBookmarks
# Transfer=gtp
# Record=grecord
# Shell=xterm -rv
# ScreenSaver=xscreensaver-command -activate
# NewsReader=mozilla -news
# Communities=mozilla -remote 'openURL(http://slashdot.org)'
# Search=mozilla -remote 'openURL(http://google.com)'
# Idea=mozilla -remote 'openURL(http://sourceforge.net)'
# Shopping=mozilla -remote 'openURL(http://thinkgeek.com)'
# Go=mozilla -remote 'openURL(http://linux.com)'
# Print=lpr
# Rotate=

# osd_font=-arphic-ar pl kaitim big5-bold-i-normal--0-250-0-0-c-0-*-*
### For the color, you can either use the strings in /etc/X11/rgb.txt,
### or use the RGB syntax #RRGGBB, e.g. ##A086FF
# osd_color=LawnGreen
# osd_timeout=3
### osd_position is either 'top' or 'bottom'
# osd_position=bottom
# osd_offset=25
Email=evolution
WebBrowser=firefox
Go=/usr/bin/wifi_button.sh
[U]
**Wifi_button.sh**[/U]

#!/bin/bash
# This script, which was written by Evgeny "nekr0z" Kuznetsov in 2006
# based on Mute script by Moritz Beller (2004),
# is licensed under the terms of the GPL

WIFI_REPORT=$(cat /proc/driver/wireless/radio | grep radio)

if [ "$WIFI_REPORT" == " radio state is OFF" ]
then
echo 1 > /proc/driver/wireless/radio
else
echo 0 > /proc/driver/wireless/radio
fi

exit 0

---

### Post by CassioBunana on 2006-12-30
Hi guys and first of all thank to nekr0z for opening such an useful thread!
I'd like some advice again about crt-out....I've update my Kubuntu to 6.10, but it's still not working!! I've tried to use i810swithc and i855crt too: the former works well but the image is flickering and unstable, the latter gives me stable image but white satured color at every resolution!

So I'd like something between....I followed your advice nekr0Z but system hangs during boot...what to do? I don't need dualhead or clone, at first it's enough to use LFP or my flatTV (connected with VGA cable), no more!

I've tried other advise found on the forum but nothing helped me!

Andrea

---

### Post by nekr0z on 2006-12-30
stefros, sorry for late answer. Everything seems ok in your configs, except for the fact you need two spaces after the third " in the "if..." line of wifi_button.sh. And take a look at this file's permissions, you need the rights to execute it from where it is on your system (which basically means it has to be something "rwxr-xr-x" if owned by root).

As far as I see you WiFi card itself works fine. Try enabling SSID broadcast on your Access Point: Linux has problems connecting to hidden networks.

---

### Post by nekr0z on 2006-12-30
Andrea, I have quit playing with KDE and fallen back to GNOME this summer, so I don't know much about the current Kubuntu issues. In Ubuntu 6.10 the video output can be easily switched via pressing Fn+F3, which works fine for me. Doesn't it work in Kubuntu?

---

### Post by CassioBunana on 2006-12-30
HI nekr0z,
Fn+F3 doesn't seems to work at all...I've found 3 way to get a crt out:

1- using i855crt gives a white satured image;
2- using i810switch gives good colors but flickering image;
3- forcing BIOS to CRT-only output gives good colors and steady image but only during boot splash, after that I get a black screen!

Any other trial to change xorg.conf, following what I found in the forums, results in a black screen...

With GNOME I was able to watch movie but I have problem with wifi and DVD (now solved in KDE)...

For now I don't need dualhead, so I'd like an easy way just to have a crt output to watch pictures and movie on my Flat TV!


Andrea

---

### Post by nekr0z on 2006-12-30
Hello again, Andrea!

I'm sorry to say that, but I'm of a little (or none at all) help here. I have not used KDE on 6.10 (and don't feel like doing it so far), so I have no idea of the particular things that may have changed since 6.06.

All I can say is: the messages about connecting external monitor earlier in this thread were written based on my experience with Kubuntu 6.06, and everything worked as I have described. I don't know what changes should be made for all this to work in 6.10. Maybe Kubuntu users here can give more advice, but I can not, sorry.

Anyway, I wish you to finally set the things up, consider this to be a New Year wish from me (in Russia we usually wish good things on New Year's Day rather than on Christmas as they do in Europe and USA). If (or better to say When) you happen to solve your problem, please take a couple of minutes to report the solution here in this thread for other people who may need it.

My best regards,
nekr0z

---

### Post by CassioBunana on 2007-01-02
Hi everyone!
I finally managed to use my M7400 to watch movies and picture on a flatTV in a quite easy way, following what I found on  [http://intellinuxgraphics.org:](http://intellinuxgraphics.org:)

1- it's just enough to edit the device section in xorg.conf, adding few lines:
          [CENTER]   Option "MonitorLayout" "CRT,LFP"
             Option "Clone" "true"[/CENTER]

2- also in xorg.conf add the following section:

[CENTER]Section "Extensions"
    Option "Composite" "Enable"
EndSection[/CENTER]

3- force BIOS to be in _only-CRT_ mode;

Now, reboot without connecting vga-out cable and log in as usual: from terminal you just need to use i855crt:

[CENTER]sudo i855crt  overlaycrt on 1024x768@60[/CENTER]

where overlaycrt is needed only if you want to watch DVD or DivX.

I hope this might be usefull!

Andrea

---

### Post by nekr0z on 2007-01-02
> I hope this might be usefull!
Sure thing it is! Any information is highly appreciated here!

---

### Post by timohnani on 2007-08-01
Hi guys,

I finally managed to make my WLAN work thanks alot to this thread! One piece of advice. For WLAN the FSAM7400 module is already part of Feisty (7.04). So if your wlan is not working you simply have to start up the module. I am not entirely sure how to do this (I'm a noobie) but once you manage to launch the module it should be ok. 

Alternatively you can do this:
[I]
"You may also want to have this module loaded by default. Just add this line:
Quote:
fsam7400 uid=1000 autoload=0 radio=1
to your /etc/modules, and you no longer need to modprobe for it every time you reboot."
[/I]
After you have done this restart your computer. Then your WLAN should be working. As said above the WLAN radio will be on all the time. Thus you should get your wireless button working. Once you have your button working you should change "radio=1" to "radio=0". That will mean your wlan will be off by default. 

Hope this helps

Timo

---

### Post by timohnani on 2007-08-02
Hi guys,

I tried using the instructions to make the keypad on the touchpad work. However it screwed up everything. Kubuntu loads as usual however the start up screening I could a blank screen with a cursor and the login window never shows up. The only way out is by turning of the computer. 

I will try and undo the changes using recovery mode. but I was wondering whether anybody had any idea about what could be wrong. 

Timo

**Update:** I managed to fix the problem. As mentioned by nekr0z a few posts back, you also have to comment out the "stylus", "cursor" and "eraser" in the "serviceLayout" section.

---

### Post by timohnani on 2007-08-02
Hi guys,

I just want to confirm that the instructions here for turning on and off the WLAN LED works perfectly. The only difference in my case was that instead of using ipw2200 I used ipw2100. Just check to find out which one you have and then use the appropriate one. 

Timo

---

### Post by nekr0z on 2007-08-02
Well I wouldn't say "perfectly", but it works nevertheless.

On my Amilo M7400 (which I changed to Lenovo N100 this week, but Amilo is still on there on my desk) the LED doesn't turn on sometimes, so I have to switch WLAN off and back on to make it shine. But for the most of time — yes, it works...

One more thing to add: on my Amilo both suspend-to-ram and suspend-to-disk (Sleep and Hibernate in Windows terms) stopped working after upgrading to 7.04. I was searching for a new machine anyway, so I didn't get much into the problem, but the problem exists, at least on my laptop...

(Going offtopic: my new Lenovo has problems with suspend-to-ram, too, although suspend-to-disk works good.)

More thihgs to add: IR-port actually works, at least on 7.04, after installing some irda utilities (don't remember the name of the package, sorry). Getting GSM phone to act as a modem via IR appeared to be a piece of cake.

---

### Post by timohnani on 2007-08-02
Hi Nekr0z,

I am having a really hard time trying to get hotkeys to work. Maybe you could have a look and let me know if you find anything. 

Problem 1: 

When I press the WLAN hotkey it tries to turn on (or off) the WLAN but instead I get this error on my console:

timo@timo-laptop:/proc/driver/wireless$ /usr/bin/wifi_button.sh: line 12: /proc/driver/wireless/radio: Permission denied

Do you know what cases this?

Problem 2: 

I am having difficulty assigning programmes to the hotkeys. I got Firefox to work fine. But what exactly do I have to do to get P1 and P2 to work? I want to assign the konsole to P1 and I want to make P2 open konqueror in "home". 

Question:

Don't I have to make arrangements so that the acerhk module loads up each time I start my computer? Doesn't the same apply to the hotkeys programme? Don't I have to arrange to have that started up also?

Here are my files:

**wifi_button.sh**


WIFI_REPORT=$(cat /proc/driver/wireless/radio | grep radio)

if [ "$WIFI_REPORT" == "  radio state is OFF" ]
then
echo 1 > /proc/driver/wireless/radio
else
echo 0 > /proc/driver/wireless/radio
fi

exit 0


**hotkeys.conf**

############################################################
# Global configuration for hotkeys                         #
############################################################

# These are the default values.
# A line starting with # is a comment.

### Specify the default keyboard  (without the .def extension) so you
### don't need to specify -t every time
# Kbd=acerwl
Kbd=amilom7400
# CDROM=/dev/cdrom

# PrevTrack=xmms --rew
# Play=xmms --play-pause
# Stop=xmms --stop
# Pause=xmms --pause
# NextTrack=xmms --fwd
# Rewind=

WebBrowser=firefox
# Email=mozilla -mail
# Calculator=xcalc
# FileManager=gmc
# MyComputer=gmc
# MyDocuments=gmc
# Favorites=gnome-moz-remote --remote=openBookmarks
# Transfer=gtp
# Record=grecord
# Shell=xterm -rv
# ScreenSaver=xscreensaver-command -activate
# NewsReader=mozilla -news
# Communities=mozilla -remote 'openURL([http://slashdot.org](http://slashdot.org))'
# Search=mozilla -remote 'openURL([http://google.com](http://google.com))'
# Idea=mozilla -remote 'openURL([http://sourceforge.net](http://sourceforge.net))'
# Shopping=mozilla -remote 'openURL([http://thinkgeek.com](http://thinkgeek.com))'
# Go=mozilla -remote 'openURL([http://linux.com](http://linux.com))'
# Print=lpr
# Rotate=
Go=/usr/bin/wifi_button.sh
prog1=konsole
# prog2=

# osd_font=-arphic-ar pl kaitim big5-bold-i-normal--0-250-0-0-c-0-*-*
### For the color, you can either use the strings in /etc/X11/rgb.txt,
### or use the RGB syntax #RRGGBB, e.g. ##A086FF
# osd_color=LawnGreen
# osd_timeout=3
### osd_position is either 'top' or 'bottom'
# osd_position=bottom
# osd_offset=25

**amilom7400.def**

<?xml version="1.0"?>

<definition>

<config model="Fujitsu-Siemens Amilo M7400">

<Help keycode="245"/>

<Mute keycode="160"/>
<VolUp keycode="176" adj="2"/>
<VolDown keycode="174" adj="2"/>

<Go keycode="147"/> # Hotkeys doesn't actually have WiFi alias, this is put only for convenience. Change it into something else to work.
<WebBrowser keycode="178"/>
<Email keycode="236"/>
<Prog1 keycode="159"/>
<Prog2 keycode="151"/>

</config>

<contributor>
<name>nekr0z</name>
<email>nekr0z@mail.ru</email>
</contributor>

</definition>

----------------------------------------------------------------------------------------------------------

I would appreciate any help.

Thanks

Timo

---

### Post by nekr0z on 2007-08-02
Hi there, Timo!

Well, let's have a look. As for Problem 1, I suppose this is a permission question. If you do
ls -l /proc/driver/wireless
you probably see that 'radio' file is owned by root/root with rw-r--r-- permissions, which is not good (unless you always plan to switch WLAN as root. I don't remember exactly how I did that, but in my case permissions are rw-rw-rw-, and this allows any user to do the switch. Try to
sudo chmod 666 /proc/driver/wireless/radio
I think this should help.

To Problem 2, the only fault in your config files is that the button is defined as Prog1 in amilom7400.def, but is referred as prog1 in hotkeys.conf. With Linux you should always care about such things, Prog1 and prog1 are not the same! This is why you got Firefox working, but not konsole. Change prog1 into Prog1 in hotkeys.conf and be happy, man.

And finally, an answer to the Question: yes you do, in both cases. acerhk is a kernel module, so simply put a line:
acerhk
in /etc/modules — that's enough to have this module loaded automatically on every bootup. As for hotkeys, it is simply a programme, so you may add it to KDEs autorun system, so that it starts every time you log in. Otherwise, you may want to put it in your ~/.bashrc that is executed every time you log in in terminal, or wherever you feel comfortable to.

---

### Post by timohnani on 2007-08-04
Hi nekr0z,

All your advice helped. All the problems I mentioned now work. Thanks for the help. You were right about the Wlan LED. It doesn't work so perfectly but I can live with that. 

Thanks!!

Timo

---

### Post by timohnani on 2007-08-05
Hi Nekr0z,

Just a couple of problems more. Even though I change the permission of the radio file, everytime I turn on the computer the file has changed back to a restricted permission. I have change the permissions each time when I turn on the computer. I find this a little strange. Any idea why this happens?

I am also trying to associate my email hotkey with thunderbird. But for some reason it doesn't work. What exactly would I have type in the hotkeys file?

Thanks

Timo

---

### Post by nekr0z on 2007-08-05
That's exactly what I was afraid of, when I was talking about changing permissions.

But hey, I've just re-read my own posts in this tread, re-looked in my Amilo, and found that I actually did not allow <b>all</b> users to switch the WLAN on/off, it's actually <b>only me</b> who is allowed to do that. Thus, the permissions are kept as they are, but the file ownership is changed, so that I own the file /proc/driver/wireless/radio, not root.

This is done in /etc/modules, in the line where you load the module, By saying "uid=xxxx" you bestow ownership on that file to the user with UID xxxx (in my case UID is 1000, your mileage may vary).

I prefer Evolution to Thunderbird, so I cannot have a look myself, but you could make a Thunderbird-launching button on a panel, then have a look on this button's properties and see what command is launched when the button is pressed. This command ("firefox" in case of Mozilla Firefox, or "evolution --component=mail" in case of Ximian Evolution) is exactly a command you put in hotkeys.conf.

---

### Post by timohnani on 2007-08-06
Hi Nek0z,

Once again thank you for your help. Your advice fixed the problems. 

I was thinking about the WLAN LED. I was wondering that wouldn't it be possible to add to the wireless button script a small section for the LED. Maybe something to do with the output of cat /proc/driver/wireless/radio ?? 


Timo

---

### Post by nekr0z on 2007-08-06
Hey, Timo. I'm glad you've finally done that, really.

I caught myself on a thought right today, that it would of course be a shame to sell (or just give away) that Amilo, because I've spent quite some time getting all that devices to work in Linux, but then I realised that if you and other people succeeded in getting their Amilos working using this thread, my effort wasn't in vain anyway...

BTW, I've had a brownout at home last Sunday, and during that brownout suddenly found out that after some recent update Amilo is suspending and hibernating correctly again, the only issue being a black screen after wakeup. But if you switch to any virtual console (Ctrl+Alt+F1, for example) the screen turns on and everything works fine (you may then switch back to graphical DE with Ctrl+Alt+F7). That certainly is good news, huh?

As for the wireless LED, I'll think about it as soon as I get back home (I took myself a couple of days' vacation at the seaside, and only took my new laptop, leaving Amilo at home). I don't really think I'll dig something out, because as I have noticed, the LED always goes on normally in network-searching mode (it blinks while searching), but sometimes turns off suddenly as the machine finally finds a network and connects to it. It seems to be some bug in the driver itself, but I'll explore this situation once again. Even if I don't find any workaround, I'll file a bug report at least... ;-)

---

### Post by timohnani on 2007-08-08
Hi Nekr0z,

A little question slightly off topic. The sound quality on my Amilo is really crap. It always has been regardless of whether I use Win or Linux. I was wondering whether you had the same problem i.e. this is just a bad quality of the speakers on this model. 

Timo

---

### Post by nekr0z on 2007-08-08
Hi Timo!

The built-in speakers really are extremely poor, only sufficient for message notifications in Jabber ;-) I always used headphones or external speakers, and then the sound is quite nice (at least as nice as AC'97 can be...), at least I had fun listening to jazz with my Microlab Solo 3 Mk II speakers.

---

### Post by nekr0z on 2007-08-08
As I have expected, there seems to be no solution for a wireless LED currently. I have [filed a bug]("https://bugs.launchpad.net/ubuntu/+bug/131130") on that.

---

### Post by timohnani on 2007-08-09
Ok,

thanks for your effort. Let me know if the bug gets sorted out. 

Timo

---

### Post by Serola on 2007-08-11
Timo, NekrOz, could you please help a newbie,

A week ago I installed Ubuntu 7.04 on Amilo 7400. I have unistalled and reinstalled NetworkManager [http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/) number of times and enabled WLAN in BIOS (or I beleive that I have done so???). Still NetworkManager don't see any WLAN networks around (mine or anyone else's).

I don't know where to start. If I do 'iwconfig' I get:

[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID: off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power: off   
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level:0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

ppp0      no wireless extensions.[/INDENT]

And what comes to 'cat /proc/driver/wireless/radio' mentioned by NekrOz, there's no such directory.

---

### Post by Serola on 2007-08-14
> **timohnani said:**
> 
[I]
"You may also want to have this module loaded by default. Just add this line:
Quote:
fsam7400 uid=1000 autoload=0 radio=1
to your /etc/modules, and you no longer need to modprobe for it every time you reboot."
[/I]
After you have done this restart your computer. Then your WLAN should be working.

Done, but nothing has changed. NetworkManager does not find any wireless networks, even when I know there should be number of WLANs available. I have also manually enabled WLAN in BIOS and as mentioned in my previous message, my laptop seem to have ipw2100, which should be supported by Ubuntu 7.04.

Please, can anyone help me on this?

---

### Post by nekr0z on 2007-08-14
As a matter of fact, it looks like your eth1 works, but the NetworkManager itself isn't connecting to any network. I would dig NetworkManager, not the WLAN card (though the absence of /proc/driver/wireless/radio is weird).

---

### Post by Serola on 2007-08-14
> **nekr0z said:**
> As a matter of fact, it looks like your eth1 works, but the NetworkManager itself isn't connecting to any network. I would dig NetworkManager, not the WLAN card (though the absence of /proc/driver/wireless/radio is weird).

Thank you NekrOz for quick answer :)

If the absence of wireless/radio directory is weird, then the next question is that through which process this directory is created? Is it something that comes with Ubuntu 7.04 installation or what?

---

### Post by nekr0z on 2007-08-14
Well, I'm not that good at kernel modules, but I believe the fsam7400 module itself should generate it. Did you check if it is actually running?

---

### Post by Serola on 2007-08-14
> **nekr0z said:**
> Well, I'm not that good at kernel modules, but I believe the fsam7400 module itself should generate it. Did you check if it is actually running?

That is exactly what I would like to know ;)
How do I check if critical/necessary modules are running or not?

---

### Post by Serola on 2007-08-14
NekrOz, I'm not "at home", so I can't immediatly check if something works on my Ubuntu. I also realized that I have not done that part on your list. So maybe this is not included into Ubuntu 7.04 after all.

Edit: Actually I just recalled that I already tried to install fsam7400. However, 'make' and 'sudo make install' just returned some error (which I will add here as soon as get back to my Ubuntu).

---

### Post by nekr0z on 2007-08-14
Serola, you no longer have to manually compile fsam7400, it is there by default, but it has to be manually turned on (i.e. sudo modprobe fsam7400 or placed in /etc/modules so that it modprobes at the boot time).

---

### Post by Serola on 2007-08-15
'sudo modprobe fsam7400' does nothing, no wireless stations displayed on NetworkManager. 

I already downloaded fsam7400-0.5.1 and tried 'make' and even 'sudo make' but it returned the following:

sami@serola-laptop:~/Lataukset/fsam7400-0.5.1$ sudo make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/sami/Lataukset/fsam7400-0.5.1 modules
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.20-16-generic"
  CC [M]  /home/sami/Lataukset/fsam7400-0.5.1/fsam7400.o
/home/sami/Lataukset/fsam7400-0.5.1/fsam7400.c:31:26: error: linux/config.h: No such file or directory
/home/sami/Lataukset/fsam7400-0.5.1/fsam7400.c: In function ‘fsam_map_memory’:
/home/sami/Lataukset/fsam7400-0.5.1/fsam7400.c:185: warning: implicit declaration of function ‘check_signature’
make[2]: *** [/home/sami/Lataukset/fsam7400-0.5.1/fsam7400.o] Virhe 1
make[1]: *** [_module_/home/sami/Lataukset/fsam7400-0.5.1] Virhe 2
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.20-16-generic"
make: *** [fsam7400.ko] Virhe 2
sami@serola-laptop:~/Lataukset/fsam7400-0.5.1$

Language is Finnish, so 'Virhe' is 'Error' in English.

---

### Post by Serola on 2007-08-15
Suddenly NetworkManager started to work :-D

I think that's because Ubuntu installed some updates automatically.

Correction: Nothing was of course updated automatically. 'sudo modprobe fsam7400' actuly worked, but I didn't notice the change first. So WLAN stations were probed after all and NetworkManger sees them alright.

An other issue was that 'make'-command was not working in my Ubuntu 7.04 probably because 'build-essential' package was not installed.

But like Nekr0z said, I didn't need to install fsam7400 after all since it is already build into Ubuntu 7.04.

---

### Post by BuZZ-dEE on 2007-09-16
I downloaded the fsam-driver from "http://zwobbl.homelinux.net/pub/fsam7400-0.5.1.tgz" and unpacked the source tarball.
Then I have changed "config.h" to "autoconf.h" and added "#include "linux/io.h"" to the top of the file in "fsam7400.c".
Then I have build the kernel module with "make".
Then I have installed the kernel module with "sudo make install".
Then I loaded the driver with "sudo modprobe -r fsam7400 && sudo modprobe fsam7400 radio=1 && cat /sys/bus/pci/drivers/ipw2100/*/rf_kill".
And now the driver is working. ;-)

---

### Post by Ohwii on 2007-10-30
Yeah, this was very helpful!

 Wlan works perfect. 
Thanks to 
serola nekr0z  BuZZ-dee

But I still do not know if sudo mudprobe was why it worked or the changes from BuZZ-dee
but I tried all and it worked.

Cheers 

oh Wii

---

### Post by Ohwii on 2007-10-31
Hi,

there is the new version Ubuntu 7,10. and 

(1)i was wondering if the same applies for the new version and

(2) if any knows how to autostart the wlan, since i always have to do it again. 

cheers, 

Oh wee

---

### Post by nekr0z on 2007-10-31
I sold my Amilo this summer in favour of brand-new Lenovo machine, so I have no idea of how it behaves on 7.10, though the fsam7400 (not activated by default) module is still there in Gutsy, and I suppose the situation has not changed too much. And as far as the laptop keys support is far better in 7.10 than it ever was, I think all those keys (except for WLAN) should be working out of the box. But then again, those are only my speculations, I had no opportunity to test it.

One of my pals (the guy has the very same Amilo M7400) claimed he had some problems with suspend-to-ram on Gutsy, and I don't know if he managed those out. But this was the only problem he reported to me.

And as for the WLAN autostart, as long as you have your fsam7400 module started automatically in /etc/modules, you may put "radio=1" option in that line (instead of "radio=0") to have your WLAN activated at boot time, I guess.

---

### Post by kakao on 2007-11-03
Hi nekroz.

> **nekr0z said:**
> Kubuntu installed just good, here is what's working out of the box and what's not:
...


First of all I have to say how I like Ubuntu and the Ubuntu way and am greatefull how far Ubuntu has brought Linux to desktops so far. Also I have seen and liked how fast it's progressing. But when I read your post dated from summer 2006 I was shocked because obviously amilo7400 is not included in this progress. I when through your list and with a fresh Gutsy install I thought I'd give my amilo7400 right after it's release I have to tick your list, statement by statement. What a shame. Especially amilo7400 seams to miss out on the newly introduced and greatly advertised feature called "Screen and Graphics" and even bullet-prooved-X. That's the thing bugging me most that there is no such thing for amilo7400 as plug'n'play external monitor, yet. But maybe thanks to all these suggestions in this thread (I haven't seen until now) I might be able to set up dual head wich working compiz.

I'll attach my working xorg.conf with an extanded desktop (monitor on the right despite the logic of used options!). But that wouldn't let me use compiz I find very effektive (besides the nice look).

Let me also point those of you [who wouldn't have Ubuntu's usplash during boot]("http://ubuntuforums.org/showthread.php?t=584205") up to a more general thread on that topic that [gives solutions]("http://ubuntuforums.org/showpost.php?p=3687398&postcount=20").

I'll keep you posted on my progress. Hopefully amilo7400 will experience better support in 8.04 LTS!

Cheers.

---

### Post by nekr0z on 2007-11-03
You're certainly right there's too little progress in all those working-out-of-the-box things on laptops (excluding ThinkPads, that is), and this is not only Ubuntu's problem, it looks like nearly every distro suffers from it. And I suppose the situation shall not change fast, on account of laptops having very special combinations of hardware and firmware, and manufacturers providing not too much information (neither drivers). Those very special combinations are very hard for the Community to work on, having to reverse-engineer many things, and the differences between models makes it necessary to develop special drivers or sets of parameters even for different series of the same model sometimes, leave out different models and different manufacturers. The only kind of laptops having decent Linux coverage are IBM/Lenovo ThinkPads, on account of them being very popular among open source software developers, who thus can track bugs effectively.

My bet is the situation stated shall not change until the manufacturers provide explicit information, or at least binary drivers, to community. And I don't think it happens too soon, though Dell's efforts look inspiring.

Considering what was just said, we should admit M7400 has very decent Ubuntu support, though it takes some handwork to get things done. My brand new Lenovo 3000 N100, lacking modem driver at all, having yet-unsolvable problems with sound and STR/STD (not mentioning webcam or fingerprint reader — I'd be astonished if those worked at all), is a bright example of much less enjoyable situation.

---

### Post by kakao on 2007-11-03
Thanks, nekr0z, for bringing that up! You certainly have a point there I haven't taken into account so far.

Cheers.

---

### Post by stefros68 on 2007-11-08
Hi,

I am using Ubuntu 7.10 with Amilo M7400. 

After installing hotkeys via synaptic and creating the sript you described in you post here, editing the hotkeys.conf and amilom7400.def file I started hotkeys via terminal.

Nothing happened. No button is responding. 

What have I done wrong?

Here are the contents of my files:

amilom7400.def[/U][/B]

<?xml version="1.0"?>

<definition>

<config model="Fujitsu-Siemens Amilo M7400">

<Help keycode="245"/>

<Mute keycode="160"/>
<VolUp keycode="176" adj="2"/>
<VolDown keycode="174" adj="2"/>

<Go keycode="147"/> 
<WebBrowser keycode="178"/>
<Email keycode="236"/>
<Prog1 keycode="159"/>
<Prog2 keycode="151"/>

</config>

<contributor>
<name>nekr0z</name>
<email>nekr0z@mail.ru</email>
</contributor>

</definition>

My hotkeys.conf :[/U][/B]

# Stop=xmms --stop
# Pause=xmms --pause
# NextTrack=xmms --fwd
# Rewind=

WebBrowser=firefox
Email=evolution
# Calculator=xcalc
# FileManager=gmc
# MyComputer=gmc

exit 0
# MyDocuments=gmc
# Favorites=gnome-moz-remote --remote=openBookmarks
# Transfer=gtp
# Record=grecord
# Shell=xterm -rv
# ScreenSaver=xscreensaver-command -activate
# NewsReader=mozilla -news
# Communities=mozilla -remote 'openURL([http://slashdot.org](http://slashdot.org))'
# Search=mozilla -remote 'openURL([http://google.com](http://google.com))'
# Idea=mozilla -remote 'openURL([http://sourceforge.net](http://sourceforge.net))'
# Shopping=mozilla -remote 'openURL([http://thinkgeek.com](http://thinkgeek.com))'
# Go=mozilla -remote 'openURL([http://linux.com](http://linux.com))'
# Print=lpr
# Rotate=

# osd_font=-arphic-ar pl kaitim big5-bold-i-normal--0-250-0-0-c-0-*-*
### For the color, you can either use the strings in /etc/X11/rgb.txt,
### or use the RGB syntax #RRGGBB, e.g. ##A086FF
# osd_color=LawnGreen
# osd_timeout=3
### osd_position is either 'top' or 'bottom'
# osd_position=bottom
# osd_offset=25

[B][U]My wifi_button.sh in /usr/bin
[/U][/B]
#!/bin/bash
# This script, which was written by Evgeny "nekr0z" Kuznetsov in 2006
# based on Mute script by Moritz Beller (2004),
# is licensed under the terms of the GPL

WIFI_REPORT=$(cat /proc/driver/wireless/radio | grep radio)

if [ "$WIFI_REPORT" == " radio state is OFF" ]
then
echo 1 > /proc/driver/wireless/radio
else
echo 0 > /proc/driver/wireless/radio
fi

And finally I created the file **_/etc/modprobe.d/ipw220_** with this:

options ipw2200 led=1

After entering hotkeys in terminal I see a splash and this is everything. The softkeys are not working !!!

Any ideas for solving my problems ?

---

### Post by stefros68 on 2007-11-12
**fsam7400 & rfsam are obsolete**


On [http://www.zwobbl.de/2007/11/05/fsam7400-rfsam-are-obsolete/#more-14](http://www.zwobbl.de/2007/11/05/fsam7400-rfsam-are-obsolete/#more-14) there is a discussion about a new module in Ubuntu.

This  module is called wistron_btns and is controlling the WLAN. Do you have experience with this module?

By the way - I changed from Ubuntu 7.10 back to Ubuntu 7.04 due to unknown problems.

---

### Post by nekr0z on 2007-12-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/131130](https://bugs.launchpad.net/ubuntu/+bug/131130) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Quite a long time ago I have reported a bug on Launchpad concerning the wireless LED on Amilo M7400. Now some developer is finally paying attention to [this bugreport]("https://bugs.launchpad.net/ubuntu/+bug/131130") and he wants some additional information. I can't provide this information because I have sold my Amilo and no longer have one.

So if somebody is interested in having that bug fixed, please subscribe to that bugreport and participate.

---

### Post by nekr0z on 2008-02-18
Guys, I have reinstalled Ubuntu onto my old M7400 last weekend (I have given it to my girlfriend half a year ago, now she feels like going Linux-way). This is just a vanilla installation of 7.10, and I have modprobed wistron_btns instead of the old way I have explained in this thread. Buttons work, but Wireless LED doesn't. Should anything else be done for it to work?

---

### Post by batchy on 2008-06-28
The rf switch to turn on my the wireless for my amilo m7400 does not work. I am not able to use the FSAM7400. I am using windows and i am unable to complile the file. Is there a completed solution or an alternative method

Batchy

---

### Post by nekr0z on 2008-06-28
As stefros68 already mentioned a couple of messages above, fsam7400 module is obsolete since Gutsy (as well as acerhk module). Both those modules were replaced by wistron_btns.

---

