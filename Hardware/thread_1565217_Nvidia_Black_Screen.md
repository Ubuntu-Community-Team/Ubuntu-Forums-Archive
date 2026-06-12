---
title: "Nvidia Black Screen"
date: 2010-08-31
forum: Hardware
---

### Post by eGelor on 2010-08-31
Hello. I'm reading a long time posts about how to fix my nvidia drivers. I test almost everything. Grub and nomodeset.
Blacklists. Manual installations. Now i'm having lucid 10.04.
2.6.32.24 linux kernel. No xserver-xorg-nv ,xserver-xorg-all.
I have install nvidia-common,nvidia-current, nvidia-settings, nvidia-current-modaliases. no other nvidia drivers. 
My xorg file is ok. 
I'm running X with "vesa" drivers, when i change to nvidia, i take a black screen.
my card is nvidia 9200m GS.
Please help!:confused:

---

### Post by realzippy on 2010-08-31
Can you post the log file that

```
sudo nvidia-bug-report.sh

```
creates in your home folder?

---

### Post by mahan66 on 2010-08-31
Hi everybody,
I have a problem with my graphic card in ubuntu 10.04.
after ubuntu 10.04 installed, upgrade hardware warn me that 2 updates of my graphic card is avilable. 

my graphic card : Geforce 9300 GS
my laptop : vaio Z570N

when I get this 2 update and activate them, i restart the computer. when it starts, everything I see is a black screen, and I had to turn off laptop fysically!!

I install Ubuntu 4 times and this problem continued. this resolution make my eyes bored. also without this graphic updates I cant use compiz utilities.

could any one help me?

---

### Post by eGelor on 2010-08-31
> Can you post the log file that

Attached.

---

### Post by eGelor on 2010-08-31
> mahan66  I see is a black screen, and I had to turn off laptop fysically!!

I got this problem 3 months now. I'm not the expert but there are several thing that you can do and solve your problem.


first tell as if you can boot to X mode.
if yes go to your xorg file.> sudo nano /etc/X11/xorg.conf

Change driver to "nv" and reboot. you'll fix reso but no compiz.

if you got nvdia drivers load up and your xorg with nvidia driver load. go to you grub conf.> sudo nano /etc/default/grub and change that line to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

don't forget to update your grub by> sudo update-grub2
if you are luck enough maybe your problem will fixed up.

---

### Post by realzippy on 2010-08-31
*Option         "CustomEDID" "DFP-0: /proc/acpi/video/VGA/LCD/EDID"*
have you edited this to your xorg.conf?

---

### Post by eGelor on 2010-08-31
,

---

### Post by eGelor on 2010-08-31
> **realzippy said:**
> *Option         "CustomEDID" "DFP-0: /proc/acpi/video/VGA/LCD/EDID"*
have you edited this to your xorg.conf?

i put this.
>  Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/VGA/LCD/EDID"


---

### Post by realzippy on 2010-08-31
,,,so you have some edid file in
/proc/acpi/video/VGA/LCD/EDID ???

---

### Post by eGelor on 2010-08-31
> **realzippy said:**
> ,,,so you have some edid file in
/proc/acpi/video/VGA/LCD/EDID ???

cat EDID file gives me <not supported>

---

### Post by realzippy on 2010-08-31
Your xorg.conf file is made by nvidia.
Those 2 lines choose DFP-0 as display and its monitor information from /proc/acpi/video/VGA/LCD/EDID.
If this file or DFP-0 not exists when nvidia is running,it might be bad... ;black screen?
No idea where this is from? 



Have you manually changed nvidia to "vesa"?

---

### Post by eGelor on 2010-08-31
> **realzippy said:**
> Your xorg.conf file is made by nvidia.
Those 2 lines choose DFP-0 as display and its monitor information from /proc/acpi/video/VGA/LCD/EDID.
If this file or DFP-0 not exists when nvidia is running,it might be bad... ;black screen?
No idea where this is from? 



Have you manually changed nvidia to "vesa"?

yes i manually change nvidia to vesa to login to X.
but i test my xorg file and without this form.
i can >  sudo nvidia-xconfig
if you wish.

---

### Post by realzippy on 2010-08-31
*sudo nvidia-xconfig *

should only work after installing the nvidia-driver,
Delete this current xorg.conf file and install the nvidia-driver,where you have to reboot.If black-screen again,run from shell *sudo nvidia-bug-report.sh*,edit "vesa" again, and 
post the new file;so we can see what happens when the nvidia-driver attempts to load.

---

### Post by eGelor on 2010-08-31
> **realzippy said:**
> *sudo nvidia-xconfig *

should only work after installing the nvidia-driver,
Delete this current xorg.conf file and install the nvidia-driver,where you have to reboot.If black-screen again,run from shell *sudo nvidia-bug-report.sh*,edit "vesa" again, and 
post the new file;so we can see what happens when the nvidia-driver attempts to load.

ok i'm coming back .
i'm back. i did what you said so i'm posting nvidia-bug-report.

---

### Post by eGelor on 2010-08-31
> post the new file;so we can see what happens when the nvidia-driver attempts to load.
Attached

i had forget in the black list this files now i change it.
# blacklist vga16fb
# blacklist nouveau
# blacklist rivafb
# blacklist nvidiafb
# blacklist rivatv

---

### Post by realzippy on 2010-08-31
You not seem to have nvidia installed.How did you try?

BTW,won't be online next hours...

---

### Post by eGelor on 2010-08-31
> **realzippy said:**
> You not seem to have nvidia installed.How did you try?

BTW,won't be online next hours...

i doing again.

---

### Post by eGelor on 2010-08-31
I'll be waiting for your next post.THANK You!
Thats the  right one. sorry.
 Now i'm without xorg file.

---

### Post by realzippy on 2010-09-01
*How* do you try to install the nvidia-graphics driver?
System/Administration/Hardware Drivers?
If so,what does it say now?No drivers installed?


P.S.
Yes,no xorg.conf....nvidia should create one  (your old one is still in the bugreport if you want it back..)

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> *How* do you try to install the nvidia-graphics driver?
System/Administration/Hardware Drivers?
If so,what does it say now?No drivers installed?

yes i install from System/Administration/Hardware Drivers.
now says nvidia-current is activated and currently in use.


P.S.
Yes,no xorg.conf....nvidia should create one  (your old one is still in the bugreport if you want it back..)
yes i know.

---

### Post by realzippy on 2010-09-01
[I]now says nvidia-current is activated and currently in use.
[/I]

if this is true,now run:

```
sudo nvidia-xconfig
```

(creates new xorg.conf)
and reboot.
What happens?

Edit:
..hope you are at lunch and not at BSOD...

---

### Post by eGelor on 2010-09-01
> (creates new xorg.conf)
and reboot.
What happens?


Black Screen. i boot with vesa driver. my screen cut at two parts. then reboot and now with vesa drivers ok.
What should i do?

---

### Post by realzippy on 2010-09-01
When you boot with "nvidia" and the black screen comes up,can
you drop to shell by pressing:

Alt+Ctrl+F2  ?

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> When you boot with "nvidia" and the black screen comes up,can
you drop to shell by pressing:

Alt+Ctrl+F2  ?

yes.Alt+Ctrl+F1.

---

### Post by realzippy on 2010-09-01
...and if you log in and run:```
startx
```

any errormessage?

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> ...and if you log in and run:```
startx
```

any errormessage?

i'll check now to be true.

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> ...and if you log in and run:```
startx
```

any errormessage?
No errors only Black Screen.

---

### Post by eGelor on 2010-09-01
this is my xorg file right now,with vesa load.

---

### Post by realzippy on 2010-09-01
Just saw again post #14.Did you edit the blacklist file?Can you post it?

When running "vesa",run the "xrandr" command in terminal and post the output.

Since this are last ideas  (and you seem to have tested lots of things in the past:
mysterious EDID lines in xorg.conf;blacklisting) what about a fresh install (to ensure a vanilla system)?
Takes 20 minutes...
Not that I am tired,but you might be...  ;-)

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> Just saw again post #14.Did you edit the blacklist file?Can you post it?

When running "vesa",run the "xrandr" command in terminal and post the output.

Since this are last ideas  (and you seem to have tested lots of things in the past:
mysterious EDID lines in xorg.conf;blacklisting) what about a fresh install (to ensure a vanilla system)?
Takes 20 minutes...
Not that I am tired,but you might be...  ;-)

but now i'm on a fresh install.
No i stop black list. i make the blacklist again but i'm sure no luck. THANK YOU VERY MACH realzippy.

---

### Post by eGelor on 2010-09-01
> When running "vesa",run the "xrandr" command in terminal and post the output.
$ xrandr
Screen 0: minimum 320 x 400, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720        0.0* 
   800x600         0.0  
   640x480        60.0  
   640x400         0.0  
   320x400         0.0

---

### Post by realzippy on 2010-09-01
> **eGelor said:**
> this is my xorg file right now,with vesa load.

The file is fine,only the 
*HorizSync       28.0 - 33.0*

is low.Which monitor do you have connected?

---

### Post by eGelor on 2010-09-01
my blacklist files 
at the end is the nvidia ask to blacklist.
i going for a reboot and i'm back for a cold bath.
i hope this to work i'm off.

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> The file is fine,only the 
*HorizSync       28.0 - 33.0*

is low.Which monitor do you have connected?

i don't now about the monitor.
i now only that my compaq presario cq60 has no details about his monitor.
> HorizSync 28.0 - 33.0
What are u suggesting about that?

---

### Post by realzippy on 2010-09-01
...nah,it is enough for 15" display.
Edit: To find out [here.]("http://ubuntuforums.org/showpost.php?p=4864241&postcount=11")
Have you ever tested

*Option "ModeValidation" "NoTotalSizeCheck"*

in "Device" section?

with "nvidia" enabled?

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> ...nah,it is enough for 15" display.
> Edit: To find out [here.]("http://ubuntuforums.org/showpost.php?p=4864241&postcount=11")
Have you ever tested

Section "Device" Option "ModeValidation" "NoTotalSizeCheck"

with "nvidia" enabled?


I'll test it now the Option. and reposting.
> Edit: To find out [here.]("http://ubuntuforums.org/showpost.php?p=4864241&postcount=11")
Have you ever tested
sudo ddcprobe | grep monitorrange
doesn't give me nothing.


realzippy you are the Man. thanx a lot lot lot.

---

### Post by eGelor on 2010-09-01
> Section "Device" Option "ModeValidation" "NoTotalSizeCheck"

Nothing changed Black Screen again.
so um hopeless.:confused:

---

### Post by realzippy on 2010-09-01
sorry,me too.
vanilla install?

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> sorry,me too.
vanilla install?
yes i change to default now.
Maybe i'll open a new thread at night.
I request your friendship in this forum.
hope you be fine. Eugene.

---

### Post by realzippy on 2010-09-01
[I]sudo ddcprobe | grep monitorrange
doesn't give me nothing.
[/I]


Me too.
But to check the Horizontal Sync you could
also run:

```
gtf 1280 720 60
```

---

### Post by eGelor on 2010-09-01
> **realzippy said:**
> [I]sudo ddcprobe | grep monitorrange
doesn't give me nothing.
[/I]


Me too.
But to check the Horizontal Sync you could
also run:

```
gtf 1280 720 60
```
i'll check it when i go back home . 
i'm in a friends mac .
i thing that the problem is on my monitor .

---

### Post by wildblaze on 2010-10-03
I have the same problem with my Toshiba Qosmio laptop. 2 drivers are avalible to install but both of them would give me a random blackscreen like 1 minute after I log in. I just have enough time to uninstall the driver before I get blackscreened. I had this problem before with the drivers when I used windows, The problem was that the newer drivers cause the problem so I never updated them and used the original driver that came with the laptop. 
 
I am a new user of ubuntu so I dont know how to put an older Nivida driver on to the laptop to see if it will work. I would really be thankful if someone could tell me how to do it or even find the older version of the driver.
 
I have a Nividia 9200M GS in the laptop.

---

### Post by eGelor on 2010-10-05
Today i test my driver again for many hours. My skills on terminal get stronger.
Besically i read the [Binary drivers how to Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") .
Install with wine the softMCCS and extract an edid.bin file that i paste it in my /etc/X11/ dir.
Chance my xorg.conf with the Options 
 Option         "CustomEDID" "DFP-0: /etc/X11/edid.bin"
        Option         "ConnectedMonitor" "DFP-0"
Under Screen Section.
Unfortunatly nvidia current , 173 , 180 , 96 drivers didn't work with my Compaq Presario CQ60 and 9200m GS nvidia card.

---

### Post by fillintheblanks on 2010-10-14
I get a black screen when booting with the nvidia proprietary driver. Its annoying as F. It boots into desktop just fine but it takes like between 2 and 5 minutes for the display to activate. It doesn't do this with the Nv driver just the proprietary one. ](*,)

---

### Post by eGelor on 2010-10-30
i set puredyne linux. 
nvidia black screen again.
searching.

---

### Post by eGelor on 2010-11-26
Hello again. 
I´m running Puredyne now but the system is Debian compatible and ubuntu karmic. I still have a problem with my screen. It black.
The second screen i plugin is a View Sonic and works correctlly, exept resolution. View sonic my system mark it as Screen 0 CRT-0 and my Philips LG the main screen as DFP-0. Nvidia loads both screens but my DFP-0 screen is black. When i try to Twien View CRT-0 View Sonic make waves and DFP-0 still black but not Closed.
Please HELP.

---

