---
title: "unable to change screen brightness in ubuntu 11.04"
date: 2011-05-06
forum: Hardware
---

### Post by gireeshkkm on 2011-05-06
I am using Acer aspire 5738. And  I am unable to change the screen brightness using  Fn key in my 11.04.
I faced this problem in 10.10 also. Till 10.04 I can fix this problem by adding '*nomodeset acpi_backlight = vendor*' into grub. 
But  from 10.10 it is not working. Is there any way to fix this issue?

---

### Post by Quaxo76 on 2011-05-07
I have the same problem. Laptop is HP Compaq 6735s. At the GRUB screen I can change brightness using the soft keys; after Ubuntu loads, I can't anymore.

---

### Post by tomsa on 2011-05-10
I have the same problem on a Toshiba Satelite L305D-S5882 laptop. Fn+f6/f7 keys have no effect.  In 10.10 and 10.04, I was able to use the gnome screen brightness applet.  I can also do that in 11.04 if I am am in an Ubuntu classic session.  I can't find any way to change the brightness using Unity.  I was having no major issues with Unity until then.  That's a major concern if I can't dim the screen to conserve battery power or for use in low light.  I would love to see some sort of workaround/applet become available, I just don't have the coding skills to contribute.  I will gladly be a tester though!

---

### Post by tamalatamala on 2011-05-10
Same problem here, using kubuntu on HP6735b. I can not adjust brightness at all, neither using fn keys nor from system settings menu.

---

### Post by Marchosius on 2011-05-10
Same problem with samsung RV510. fn keys don't adjust brightness.

---

### Post by tamalatamala on 2011-05-10
I take it back. I shut my computer down, then turned it on again. When Grub appeared, I tried adjusting the screen brightness and it worked. And, surprisingly, it works in Kubuntu 11.04 as well (using fn keys).

---

### Post by tamalatamala on 2011-05-15
Ok, few days later I can say in my case adjusting screen brightness in kubuntu works whenever I turn on my computer while being plugged in, and almost never when I turn it on running on battery. In that case I can not adjust brightness at all.

---

### Post by Guskuma on 2011-05-17
Same here, on MacBook MC207.
I press the button and then the bar shows the brightness level, but nothing change.

I'm also having a problem with the audio driver, the sound is very low.

---

### Post by zionLobo on 2011-05-17
this command worked for me:
echo 0 > /sys/class/backlight/acpi_video0/brightness         for low brightness
OR
echo 6 > /sys/class/backlight/acpi_video0/brightness        for increased brightness.

---

### Post by Dale61 on 2011-05-18
It works on my Acer 5745G.  I press the Fn + left/right arrow.  Left arrow reduces brightness / right arrow increases.

---

### Post by jetthe on 2011-05-19
Same problem here with an FujitsuSiemens U9200. Previously using Gnome's brightness applet has been the solution but in Unity(-2D) I've resorted to using the Power management tab of UbuntuTweak ([http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)), not exactly the perfect solution.

I can use fn+F8 to lower the brightness but fn+F9 only make the screen flicker.

Do you know about any open bugs regarding the problems with the fn-keys?

---

### Post by Guskuma on 2011-05-23
For those who has MB with the nvidia 9400m I found the solution!

You just have to add a line in the xorg.conf

sudo gedit /etc/X11/xorg.conf

And then find the Section "Device" and add the bold line.

Section "Device"
 Identifier	"Default Device"
 Option	 "NoLogo"	 "True"
 **Option "RegistryDwords"	"EnableBrightnessControl=1"**
EndSection

And now your brightness control is working! :D

But maybe you have the same graphic card and then the problem is the keyboard or something like that.

---

### Post by Lablasco on 2011-05-24
Had the same problem on a MacBook (6,1) after activating the NVIDIA accelerated graphics driver.
 Adding a line in the xorg.conf solved the problem:

> **Guskuma said:**
> sudo gedit /etc/X11/xorg.conf

And then find the Section "Device" and add the bold line.

Section "Device"
 Identifier    "Default Device"
 Option     "NoLogo"     "True"
 **Option "RegistryDwords"    "EnableBrightnessControl=1"**
EndSection


Thank you Guskuma :)

---

### Post by fselles on 2011-05-28
Will this work on a Samsung R780 running 10.10?

Sam

---

### Post by JoWi on 2011-06-12
For HP 6735s, please refer also to this thread: [http://ubuntuforums.org/showthread.php?t=1748468](http://ubuntuforums.org/showthread.php?t=1748468)

---

### Post by SirVenom on 2011-07-06
I have a Samsung MP-Q430.

When I try to change the brightness (FN + L or R arrow key), the brightness meter (for lack of a better term) comes up and changes, but the brightness itself does not change.

Also, if I start the computer unplugged, the brightness is intolerably low, and does not change even when I plug it in.

I tried Lablasco's hack, but I haven't rebooted my computer yet. I doubt that it will work, since my computer *thinks* it is letting me change the brightness already, but I'll edit this post as soon as it reboots.

Edit: No change. Still doesn't work.

I have subscribed to this thread.

---

### Post by Col Matrix on 2011-07-06
Hi everyone,

I'm having similar problems as described by SirVenom and others. I can't adjust the screen brightness - using the function keys brings up the popup bar which (supposedly) indicates the screen brightness going up or down. However, the actual screen brightness doesn't change. If I use the sliders in Gnome Power Manager, or Ubuntu Tweak to adjust the brightness, again...the brightness doesn't change.

It's as if Ubuntu reads my instructions to change the brightness, but doesn't pass the message onto the screen.

I should also add that if I boot up when on battery power, the brightness is reduced compared to when I'm running on AC power. However, connecting/disconnecting the AC supply after booting up doesn't change the brightness.

The other function keys on my laptop work fine - e.g. for controlling the sound and turning wi-fi on/off.

I'm running Ubuntu Natty, on a Packard Bell EasyNote Tj68. Graphics card Intel GMA 4500M integrated graphics processor.

Any help would be appreciated!

---

### Post by SirVenom on 2011-07-18
I don't know the rules about bumping, despite my attempts to find them. If I am breaking a rule, can someone direct me to the relevant (and probably incredibly obvious and impossible to miss) thread to find it?

I still have this problem. Does anyone have any suggestions for fixing it?

---

### Post by Zigzags on 2011-07-30
I Just installed Ubuntu 11.04 Natty on a White Macbook Core Duo and experienced the same brightness issues. Here was my fix for the Macbook 3,1.

You can check your Macbook version with:

sudo dmidecode -s system-product-name

And in Synaptic Package Manager , System Settings->Synaptic Package Manager 

Search for "pommed" and install (I installed the additional packages as well)

Enjoy

"pommed handles the hotkeys found on the Apple MacBook Pro, MacBook Air,
MacBook, PowerBook and iBook laptops and adjusts the LCD backlight, sound
volume, keyboard backlight or ejects the CD-ROM drive accordingly.

pommed also monitors the ambient light sensors to automatically
light up the keyboard backlight on machines that support it."

---

### Post by tptgeek on 2011-08-19
I'm experiencing the same issue on a Toshiba Satellite. Reading around, I discovered a thread that stated that one should modify part of the /etc/default/grub file and insert 'nomodeset acpi_backlight=vendor' to the 'GRUB_CMDLINE_LINUX_DEFAULT' line. It seems to have worked for several people, however it hasn't worked for me yet, and has only crashed unity once I rebooted.

---

### Post by marvin.engl on 2011-08-20
I have an Acer Aspire One with the horrible Poulsbo chipset and the substandard Intel EMGB drivers installed.

The "change your brightness while Grub displays" works for me. I can change the brightness before Grub boots into Ubuntu 11.04, but not once 11.04 has booted. 

Give it a try ... not ideal, but at least it works.

---

### Post by gregor171 on 2011-08-24
This was also mine problem. I have HP EliteBook 8560p with graphics AMD Radeon. Update of graphics drivers (manualy) worked for me. 

However there is 
Kmenu>Applications>System>AdditionalDrivers 

but would not update because ob VirtualBox Guest Adidtions. Might. 

Update drivers:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by andrei90 on 2011-08-24
Greetings,

I had the same problem. It solved after I tried this:

1. sudo gedit /etc/default/grub
2. Change the line GRUB_CMDLINE_LINUX="" into
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
3. sudo update-grub
4. Restart your linux

Thanks to this [lad]("http://livinginjava.blogspot.com/2010/11/ubuntu-1010-brightness-problem-in-acer.html")

---

### Post by vinayshukla86 on 2011-08-24
i am unable to control brightness on my hp 630

---

### Post by Basher101 on 2011-08-24
> Greetings,

 I had the same problem. It solved after I tried this:

 1. sudo gedit /etc/default/grub
 2. Change the line GRUB_CMDLINE_LINUX="" into
 GRUB_CMDLINE_LINUX="acpi_osi=Linux"
 3. sudo update-grub
 4. Restart your linux
yes that ***should*** fix it. If you applied that and your brightness still doesnt work, try editing your rc.local file. Open a terminal and type ```
sudo gedit /etc/rc.local
```and add ***_above the exit0_*** the line ```
setpci -s 00:02.0 F4.B=00
```

---

### Post by sklpr on 2011-08-25
I have the same problem as well HP G6 series laptop  Radeon graphics.. !

---

### Post by Kirstine on 2011-08-29
> **Basher101 said:**
> yes that ***should*** fix it. If you applied that and your brightness still doesnt work, try editing your rc.local file. Open a terminal and type ```
sudo gedit /etc/rc.local
```and add ***_above the exit0_*** the line ```
setpci -s 00:02.0 F4.B=00
```

when i try out the command it says in the rc.local file that 

"# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing."

how do i edit the rc.local?

---

### Post by nachiappantce on 2011-09-04
Hi All,
I have a Lenovo V570 and installed Ubuntu Natty recently, the Fn key is not working so I am not able to change the brightness, and xorg.conf file is also missing in /etx/X11 folder, how should i create a new xorg.conf file ?

---

### Post by sanjayjohny on 2011-09-18
i m using   lenovo Z570 and ubuntu 11.04.... I m unable to change screen brightness using function keys.. i tried gdccontrol but failed....Please help          :-(

---

### Post by seiffs on 2011-09-20
> **Guskuma said:**
> For those who has MB with the nvidia 9400m I found the solution!

You just have to add a line in the xorg.conf

sudo gedit /etc/X11/xorg.conf

And then find the Section "Device" and add the bold line.

Section "Device"
 Identifier	"Default Device"
 Option	 "NoLogo"	 "True"
 **Option "RegistryDwords"	"EnableBrightnessControl=1"**
EndSection

And now your brightness control is working! :D

But maybe you have the same graphic card and then the problem is the keyboard or something like that.

Thank you! worked on MBP5.5 + oneiric beta.

---

### Post by 1luquillo on 2011-09-20
Hello sklpr,

I also have an HP g6 with a radeon graphics card.  I installed a dual boot using kubuntu.  I cannot get fglrx to load and am restricted to the vga resolution.  How did you install?

Thanks

---

### Post by sanjayjohny on 2011-09-21
i think u should install nvidia drivers.Then u can see xorg.conf in in/etc/X11..

---

### Post by Kirstine on 2011-10-03
> **Kirstine said:**
> when i try out the command it says in the rc.local file that 

"# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing."

how do i edit the rc.local?

mine says the same!

---

### Post by tomsa on 2011-10-05
For what it's worth...

I have been trying other Desktop Environments over the past few weeks just for kicks on my Mint 11 install- I am able to change my screen brightness in the power settings within KDE.  I wasn't able to do so in GNOME or XFCE.  I am quickly becoming a fan of KDE too, because my fan doesn't run full speed while I play video, despite what everyone says about it being resource hungry.

Going to try LXDE next week, and see what happens.

---

### Post by sairam2000 on 2011-10-16
even 11.10 continues to have this issue. i have a lenovo ideapad Y450 and had found a solution browsing net when i had 11.04. Now i have installed 11.10 & cannot find solution.

---

### Post by netuntu on 2011-10-23
Hi i made this from Guskuma in my Ubuntu 11.10 64 bits!! and it works! on my Lenovo T510.

Hope this help!!
---------------------------------------------------------------------------
Re: unable to change screen brightness in ubuntu 11.04
For those who has MB with the nvidia 9400m I found the solution!

You just have to add a line in the xorg.conf

sudo gedit /etc/X11/xorg.conf

And then find the Section "Device" and add the bold line.

Section "Device"
Identifier "Default Device"
Option "NoLogo" "True"
**Option "RegistryDwords" "EnableBrightnessControl=1"**
EndSection

And now your brightness control is working!

But maybe you have the same graphic card and then the problem is the keyboard or something like that.

---

### Post by sairam2000 on 2011-10-24
> **netuntu said:**
> 
You just have to add a line in the xorg.conf

sudo gedit /etc/X11/xorg.conf

No such file exists

---

### Post by simormate on 2011-10-25
I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot

---

### Post by mikrowelle on 2011-10-30
[COLOR=DarkRed]EDIT: Now that I deleted the changes in the rc.local file and removed the acpi_backlight=vendor from the grub file it suddenly works. Well, it does not work 100%. If I set the brightness below a certain level I'm not able to increase it anymore. But I'm happy for now.. :D[/COLOR]

I've got the same problem, I'm using a Samsung R510 with Xubuntu 11.10. I hope I didn't post in the wrong topic as the title says Ubuntu 11.04. But as the problems sounded pretty similar to mine I thought it would be stupid to open a new thread for it.

Tried adding ```
"Option "RegistryDwords"    "EnableBrightnessControl=1"
``` to the xorg.conf - afterwards the Fn+Up/Down made the brightness control show up but the screen brightness didn't change at all. (from [THIS]("http://ubuntuforums.org/showpost.php?p=10854985&postcount=12") post)

After that I tried changing the ```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
``` in the grub config (or whatever file that was). Also tried the both variants with only acpi_osi=Linux and only acpi_backlight=vendor. All three didn't work, and afterwards the brightness plugin on my panel said "No device found". (From [THIS]("http://ubuntuforums.org/showpost.php?p=11391840&postcount=38") post)

Also tried fixing it by editing /etc/rc.local and adding ```
setpci -s 00:02.0 F4.B=00
``` to it. Didn't do anything either. And yes, it was executable (which is pretty odd because it says it does nothing by default yet after checking, it turned out the executable bit in fact was turned on by default). (from [THIS]("http://ubuntuforums.org/showpost.php?p=11182693&postcount=25") post)


Any advice? :D

---

### Post by Kirstine on 2011-10-31
> **simormate said:**
> I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot


This works work me as well. Ive got an asus UL80V with graphic card nvidia 210M and upgraded to 11.10 64

:)

---

### Post by Inst on 2012-01-05
> **simormate said:**
> 
The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```Find the following line:
```
GRUB_CMDLINE_LINUX=""
```Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```2.
Now Run
```
sudo update-grub
```3. Reboot


Worked on my Acer Aspire 5750, Fn+ left/right arrow keys adjust the brightness now, however the icon that used to appear on the screen when I did so in the past no longer appears, also the option to adjust brightness disappeared from power management settings too. Thanks anyway, at least it works now.

---

### Post by sairam2000 on 2012-01-06
> **simormate said:**
> I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```Find the following line:
```
GRUB_CMDLINE_LINUX=""
```Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```2.
Now Run
```
sudo update-grub
```3. Reboot
Thanks a lot simormate! This is the beauty of Linux and open source society. I have issues now and then. But when I reach out, some one gives me a solution. Your solution solved the issue.
> **sairam2000 said:**
> even 11.10 continues to have this issue. i  have a lenovo ideapad Y450 and had found a solution browsing net when i  had 11.04. Now i have installed 11.10 & cannot find  solution.

---

### Post by mohammad110 on 2012-01-06
> **sairam2000 said:**
> Thanks a lot simormate! This is the beauty of Linux and open source society. I have issues now and then. But when I reach out, some one gives me a solution. Your solution solved the issue.

Hi
i have a ideapad Y450 but this solution doesn't work for me.
please send to me your grub file. perhaps i changed mistakenly this file.
Of course now than already when using Fn for change brightness, i can't reduce that's ! but however i never successful to change.
thank's

---

### Post by grylos on 2012-01-25
> **simormate said:**
> I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```Find the following line:
```
GRUB_CMDLINE_LINUX=""
```Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```2.
Now Run
```
sudo update-grub
```3. Reboot

Great!!! This worked for me also!! Many thanks!
HP Pavilion g6

---

### Post by aatje92 on 2012-08-15
> **simormate said:**
> I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot

Thanks a bunch for this! Was having enough trouble as it is with ubuntu on my optimus "powered" laptop, this made my life a little easier. Rock on:guitar:

---

### Post by woolfie on 2012-08-16
Thanks simormate. That solution worked for me too. (Samsung laptop with Intel GM45 chipset).

> **simormate said:**
> I have a Fujitsu-Siemens Esprimo Mobile M9400. Graphic driver is Intel GMA X3100. Whenever I wanted to increase brightness, using Fn+F9 made the brightness indicator appear, but brightness did not increase. However, it worked downwards with Fn+F8. I did not have a /etc/X11/xorg.conf file as several of you.

The following solution worked for me:

1.
Run the following command in Terminal:
```
sudo gedit /etc/default/grub
```

Find the following line:
```
GRUB_CMDLINE_LINUX=""
```

Change it to the following:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

2.
Now Run
```
sudo update-grub
```

3. Reboot

---

### Post by Stephen Wayne Hamilton on 2013-01-23
First I would like to apologize for thread necromancy, but this issue is starting to bother me.

I'm running Ubuntu 12.10 x64. This is an ASUS G75VW gaming laptop. It took a few days for me to notice I couldn't adjust the brightness, and I would like to be able to dim it down when on battery so I can get 2 to 2.5 hrs of life out of this battery-murdering monster. I can do it just fine in Windows 7/8 and I get above average battery life for a gaming laptop, have actually noticed that it is shorter in Ubuntu than in Windows.

But anyway, my NVIDIA drivers are installed (nvidia-current-updates), and so are all applicable updates from Canonical. I can attempt to adjust the brightness up or down in Unity (or KDE and XFCE for that matter), and the slider will move but the brightness won't change. I have tried several of the fixes (editing various text config files) in this topic and nothing works.

So what else can I try?

Thanks for any help!

---

### Post by Macoy Villalobos on 2013-04-25
Wow thanks a lot it works at my packard bell enns11hr. although the display indicator is gone. It doesn't matter, at least It works. . :D

---

### Post by gregor171 on 2013-05-16
Brightness controls are working out of the box with Kubuntu 13.04!

---

### Post by oldos2er on 2013-05-16
Old thread closed. If anyone is still experiencing this issue with a newer version of Ubuntu, please start a new thread.

---

