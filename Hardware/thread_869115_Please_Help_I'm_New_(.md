---
title: "Please Help I'm New :("
date: 2008-07-24
forum: Hardware
---

### Post by AdZr on 2008-07-24
Alright people ive just installed Ubuntu and to be honest i havent got a clue what im doing, although ive just installed a few programs.

The thing im stuck on is that i think my gfx card on my laptop i dont think the drivers are installed, so what i did was i went onto the makers website and downloaded the driver for linux but i just dont have a clue on how to install it as everytime i try i get errors :( 

Thanks in advance for any help

heres a screenshot of my problem :)

[http://img178.imageshack.us/img178/9497/screenshotbu7.png](http://img178.imageshack.us/img178/9497/screenshotbu7.png)

---

### Post by Jordanwb on 2008-07-24
Try putting "sudo" (minus quotes) before the "sh S3G..." command. When you downloaded the file, what format was it in? .tar.gz or .tar.bz2?

---

### Post by Kevbert on 2008-07-24
Why don't you think your graphics drivers are installed ?  If it's due to the fact that you can't run compiz (for the rotating cube), that's not due to a driver error as compiz will not run on the Via S3 display card (it's not currently supported).  
You haven't got gawk installed.  You can get this if you want via the terminal by entering
```
sudo apt-get install gawk
```

---

### Post by AdZr on 2008-07-24
still no good :(

cadam@adam-laptop:~$ cd Desktop
adam@adam-laptop:~/Desktop$ dir
Downloads  RN_Linux_EN.txt		 Screenshot.png
Readme	   S3G-Linux-x86-2.0.16-pkg.run  wine.png
adam@adam-laptop:~/Desktop$ sudo sh S3G-Linux-x86-2.0.16-pkg.run
[sudo] password for adam: 
Verifying archive integrity... All good.
Uncompressing S3 Accelerated Graphics Driver for Linux-x86 2.0.16.............................................................................
./setup.sh: 14: gawk: not found
./setup.sh: 14: gawk: not found
./setup.sh: 15: gawk: not found
./setup.sh: 15: gawk: not found
./setup.sh: 753: dialog: not found
adam@adam-laptop:~/Desktop$

---

### Post by evets25 on 2008-07-24
First to answer your question, you probably need to put "sudo" in front of your command so that it can run as root (administrator). Secondly, you're doing it wrong. :P Installing the driver, that is. Well, ok, perhaps not "wrong" persay, but it will make your life a lot easier if you use a script like "envy" (sudo apt-get install envy) for installing graphics drivers called envy, or use ubuntu's restricted drivers manager (recommended) to install the drivers (System -> administration -> restricted drivers, or something like that). 

If you really want, you CAN install that package you downloaded from the company's website, but that means that next time you do a kernel update, your graphics driver won't work and will have to be install the hard way from a recovery console... Just a warning. :)

---

### Post by AdZr on 2008-07-24
> **Kevbert said:**
> Why don't you think your graphics drivers are installed ?  If it's due to the fact that you can't run compiz (for the rotating cube), that's not due to a driver error as compiz will not run on the Via S3 display card (it's not currently supported).  
You haven't got gawk installed.  You can get this if you want via the terminal by entering
```
sudo apt-get install gawk
```

well sometimes pictures & text go all funny and when i first boot up i get all lines everywhere for about 20 secs then it goes back to normal, thats why i thought there was somethink wrong and under screen resalution it says monitor unknown

also just tryed what you said and got this

adam@adam-laptop:~/Desktop$ sudo apt-get install gawk
[sudo] password for adam: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by AdZr on 2008-07-24
> **evets25 said:**
> First to answer your question, you probably need to put "sudo" in front of your command so that it can run as root (administrator). Secondly, you're doing it wrong. :P Installing the driver, that is. Well, ok, perhaps not "wrong" persay, but it will make your life a lot easier if you use a script like "envy" (sudo apt-get install envy) for installing graphics drivers called envy, or use ubuntu's restricted drivers manager (recommended) to install the drivers (System -> administration -> restricted drivers, or something like that). 

If you really want, you CAN install that package you downloaded from the company's website, but that means that next time you do a kernel update, your graphics driver won't work and will have to be install the hard way from a recovery console... Just a warning. :)

cant do 'sudo apt-get install envy' as it comes up with
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

also cant find restricted drivers manager :(

---

### Post by Kevbert on 2008-07-24
In terminal please enter
```
sudo dpkg --configure -a
``` and post the response here.
While you're at it, in terminal, enter
```
sudo apt-get install -f
```
in case you have any damaged software packages.
gawk is a package that your display card drivers need.  So if everything comes up fine you'll need to install it (see my previous post).

---

### Post by tarasin on 2008-07-24
I suggest you do nothing until you have had a chance to read up on Ubuntu. 
Try these:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

[https://help.ubuntu.com/]("https://help.ubuntu.com/")

Everything can be resolved in time.

---

### Post by AdZr on 2008-07-24
> **Kevbert said:**
> In terminal please enter
```
sudo dpkg --configure -a
``` and post the response here.
While you're at it, in terminal, enter
```
sudo apt-get install -f
```
in case you have any damaged software packages.
gawk is a package that your display card drivers need.  So if everything comes up fine you'll need to install it (see my previous post).

adam@adam-laptop:~$ sudo dpkg --configure -a
[sudo] password for adam: 
Setting up java-common (0.28ubuntu3) ...

Setting up odbcinst1debian1 (2.2.11-16build1) ...

Setting up unixodbc (2.2.11-16build1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
adam@adam-laptop:~$ 


now i just did the second one and it went fine but then it goes to a blue screen saying configuring java but i cant get past that

---

### Post by Kevbert on 2008-07-24
If it's the configuring java screen isn't there a yes highlighted at the bottom of the screen ?  If so just press the return key.

---

### Post by AdZr on 2008-07-24
yer an ok key but i cant get past that :(

---

### Post by AdZr on 2008-07-24
omg im so thick lol done it now all i needed to do was press tab until it highlighted it

---

### Post by Kevbert on 2008-07-24
I'm trying to do this from memory (I haven't installed java in months).  Can you select Yes or OK with the left mouse key (I think if you select one or other it is highlighted in red). If the window just closes and nothing happens we may have to try this from a different angle.  
Close terminal and run up Synaptic via System-Administration-Synaptic Package Manager.  Now click on Custom filters and then select Broken.  You may have to hit reload to display the Java package.  Note the name of the program.  Now right-click on the name and select 'Mark for Complete removal'.  Now click on Apply and remove the package.  Next you're going to install the package again.  Make sure All is selected on the left-hand side and click on Search.  In the box that's displayed enter the name of the Java package you noted previously.  Right-click on the program name when it appears in the main Synaptic Window and select Mark for Installation and then select Apply.

---

### Post by Kevbert on 2008-07-24
Crossed posts.  Now you need to install gawk.

---

### Post by AdZr on 2008-07-24
ive installed gawk :)

---

### Post by Kevbert on 2008-07-24
It seems you also need dialog
```
sudo apt-get install dialog
```
and now finally (hopefully) you can install the driver program with
```
sudo sh S3G-Linux-x86-2.0.16-pkg.run
```

---

### Post by AdZr on 2008-07-24
you are the man :) we've got further but now this

[http://img171.imageshack.us/img171/7533/screenshotvo7.png](http://img171.imageshack.us/img171/7533/screenshotvo7.png)

---

### Post by AdZr on 2008-07-24
Right to be honest i dont even think thats the right driver now i think its VIA chrome 9

the laptop is a 
Medion MIM 2210

also i cant enable destop effects

[https://www.medionshop.co.uk/?et_cid=1&et_lid=1&partnerID=107975596](https://www.medionshop.co.uk/?et_cid=1&et_lid=1&partnerID=107975596)

---

### Post by AdZr on 2008-07-24
bump

---

### Post by overdrank on 2008-07-24
> **AdZr said:**
> bump

Hi and yes the VIA chrome 9 are not supported well for the desktop effects and 3d in general.
You may look here
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by issih on 2008-07-24
Via's own drivers can be found here:

[http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

I think some people have mangaged to get compiz running on them, but I wouldn't swear to it

Hope that helps

---

### Post by AdZr on 2008-07-24
> **overdrank said:**
> Hi and yes the VIA chrome 9 are not supported well for the desktop effects and 3d in general.
You may look here
[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

shame :( that means i cant do the cool stuff like burn desktop n stuff :(

---

### Post by overdrank on 2008-07-24
> **AdZr said:**
> shame :( that means i cant do the cool stuff like burn desktop n stuff :(

By no means are we saying that, it just may includes some work. You may also look at adding a additional graphics card as the VIA graphics are usually built on board.

---

### Post by Kevbert on 2008-07-25
To find out what video card you have open terminal and type
```
lspci
```
and post the output here.
As I suggested before, it's unlikely that you can run advanced desktop effects (compiz) with your video card especially if it's the S3.  If we can the driver working we'll have a look at that.

---

### Post by AdZr on 2008-07-25
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
06:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)
ubuntu@ubuntu:~$ 


also last night i restarted and as i booted up the screen went black and a message saying that i cant find drivers for my gfx card & monitor :( so it wont load no more, im on live atm

---

### Post by Kevbert on 2008-07-25
Have you tried booting into recovery mode ?   If you can do this, you may be able to set the display up, using the command below if you open terminal.
If when you boot normally you get a prompt (either $ or #) try entering the following command:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Enter your log-on password when prompted.  The command will try to set up your display and may ask you a load of questions.
If this does not work it may be worth re-installing Ubuntu.  Regardless of this please take a look at the link posted by Overdrank in post #21.

---

### Post by AdZr on 2008-07-25
> **Kevbert said:**
> .  Regardless of this please take a look at the link posted by Overdrank in post #21.

yeah i did that and got this

ubuntu@ubuntu:~$  sudo apt-get install xserver-xorg-video-openchrome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-openchrome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
ubuntu@ubuntu:~$ 

and then i rebooted and it messed everythink up :(

ill try what you said brb

---

### Post by Kevbert on 2008-07-25
If the last command didn't work there's one more thing you can try.
You need to get to the prompt again ($ or #).  Enter the following:
```
sudo nano /etc/X11/xorg.conf
```
Using the cursor keys you need to get to the point that says
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection
```
This is my display driver.  You need to change the Driver to "vesa".  That would replace "nvidia" in the example above.  Next select Ctrl+X and Y and enter to save the file.
Now hit Ctrl+Alt+Del to reboot the PC.  If this does not work a re-install is your best bet.

---

### Post by AdZr on 2008-07-25
Right :( i had a few problems so i re-installed ubuntu and first and second boot all i got was a blank screen but third boot worked fine :D what should i do know as i dont want it to go wrong again :(

---

### Post by AdZr on 2008-07-25
also just tryed that and this was there i didnt edit it

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"

---

### Post by Kevbert on 2008-07-25
It looks like that's possibly the best driver, but if you're still getting the problems with the unstable display, check all your wired connections are OK and then try using the card at a different resolution and refresh rate.  To do this go to System-Preferences-Screen Resolution and just change one item at a time.  You may have to reboot to see if you've cured the problem for each change in setting.  If the problem only occurs at first boot (when the PC is cold) you may have a hardware problem or a loose connection somewhere.

---

### Post by AdZr on 2008-07-25
> **Kevbert said:**
> It looks like that's possibly the best driver, but if you're still getting the problems with the unstable display, check all your wired connections are OK and then try using the card at a different resolution and refresh rate.  To do this go to System-Preferences-Screen Resolution and just change one item at a time.  You may have to reboot to see if you've cured the problem for each change in setting.  If the problem only occurs at first boot (when the PC is cold) you may have a hardware problem or a loose connection somewhere.


yer im still getting the problems at start-up but im not too bothered about that, but i cant change my screen resalution or refresh rate :( also im using a laptop so i cant really check the connections

---

### Post by AdZr on 2008-07-25
got another problem now, i think i might have to go back to winblows :(

[http://img514.imageshack.us/img514/7832/screenshotdn2.png](http://img514.imageshack.us/img514/7832/screenshotdn2.png)

[IMG]http://img514.imageshack.us/img514/7832/screenshotdn2.png[/IMG]

---

### Post by AdZr on 2008-07-25
Right, ive finally installed the right driver for my gfx and it seems to be working alright, although i still cant enable desktop effects & cario-dock wont load :(

---

### Post by AdZr on 2008-07-25
cant get desktop effects to work 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. Chrome9 HC IGP (rev 01)
 Driver in use:         via
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Detected driver is not on the whitelist. 

Would you like to know more? (Y/n) y

 Your driver is not known (most probably not able) to work with Compiz.
 See [http://wiki.compiz-fusion.org/Hardware](http://wiki.compiz-fusion.org/Hardware) for details. 


:(

---

### Post by overdrank on 2008-07-25
AdZr please do not create more threads on the same issue. I believe your were well assisted in the original thread and I have merged. Thanks :)

---

### Post by AdZr on 2008-07-25
> **overdrank said:**
> AdZr please do not create more threads on the same issue. I believe your were well assisted in the original thread and I have merged. Thanks :)

sorry i just though as there was a section for it i might get more help in there :)

---

### Post by Kevbert on 2008-07-26
Desktop effects which are also know as compiz and compiz-fusion will not work with Via S3 (and now you've confirmed S9) display cards.  If you want compiz to work the card would have to be Intel, ATI or nVidia.  Most other cards are not supported.
I haven't tried cairo dock so can't comment.

---

