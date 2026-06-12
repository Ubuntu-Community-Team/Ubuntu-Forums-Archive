---
title: "Installing Samsung ML-1865w printer"
date: 2011-08-05
forum: Hardware
---

### Post by ranger_cole on 2011-08-05
Trying to install Samsung ML-1865W in Ubuntu 10.10.  Samsung provides drives but no joy in installing yet.  The driver is a zip file when opened it creates a folder called cd root.  Inside cd root is a folder called Linunx and a file called autorun.  I tried buring this to a cd and running it.  It tries to run the autorunfile but fails.  I tried going into terminal and cd all the way until I am in the Linux Folder at the terminal prompt.  I tried sudo install at terminal prompt but no joy.  There is a file called install.sh in Linux folder. I tried adding the printer via the system>administration>printing but there is no driver found or listed for ML-1865W.  The drivers are on my desktop but can not get them installed.  The printer does show up in printing under network printer as Samsung ML-1865W(ubuntu)  and then again as Samsung ML-1865.

---

### Post by ranger_cole on 2011-08-05
I installed using a ppd file found in the linux>noarch>at_opt>share>ppd>ml-1865wps.ppd.  I then got an error requires the 'rastertosamsungspl' program but it is not currently installed. Please install it before using this printer.

This link fixed that problem:

http://ubuntuforums.org/showthread.php?t=1573718[/url]


Hope this helps someone else!:)

---

### Post by fictivetoast on 2011-08-09
I just got mine up and running with ease using the automated Samsung installed.

**1** Download the 30,8mb Unified Driver zip package onto your desktop from : [http://www.samsung.com/us/support/downloads/ML-1865W/XAA](http://www.samsung.com/us/support/downloads/ML-1865W/XAA) 

**2** Right click on zip file and "extract here" 

**3** Open a terminal window and type :

sudo '/home/YOURUSERNAME/Desktop/cdroot/autorun'

(obviously replacing YOURUSERNAME with your user name to provide the proper path to the autorun file)

**4** Hit enter and follow the QT menu installer steps.

---

### Post by SamuelAdamsH on 2011-08-25
> **fictivetoast said:**
> I just got mine up and running with ease using the automated Samsung installed.

**1** Download the 30,8mb Unified Driver zip package onto your desktop from : [http://www.samsung.com/us/support/downloads/ML-1865W/XAA](http://www.samsung.com/us/support/downloads/ML-1865W/XAA) 

**2** Right click on zip file and "extract here" 

**3** Open a terminal window and type :

sudo '/home/YOURUSERNAME/Desktop/cdroot/autorun'

(obviously replacing YOURUSERNAME with your user name to provide the proper path to the autorun file)

**4** Hit enter and follow the QT menu installer steps.

This worked, with one addition: sudo **sh** '/home/YOURUSERNAME/Desktop/cdroot/autorun'

Adding sh is probabl what OP needed as well. Worked like a charm after that.

Cheers!

---

### Post by omegadeluz on 2011-09-04
I get about 55% complete on the QT menu setup and then my screen goes half blank on the top and I get black and white diagonal stripes on the top half.  The CPU goes unresponsive and I have to restart.  I have tried it several times with same results.  Please Help!

---

### Post by TheConsaw on 2011-09-25
> **SamuelAdamsH said:**
> This worked, with one addition: sudo **sh** '/home/YOURUSERNAME/Desktop/cdroot/autorun'

Adding sh is probabl what OP needed as well. Worked like a charm after that.

Cheers!

sweet, thanks, works great

---

### Post by speedygeo on 2011-09-25
Have you tried the wifi connection?
Is it connected directly to a pc or through a router?
Have you installed more than the simple samsung unified driver?

---

### Post by omegadeluz on 2011-09-25
I have not trying WiFi.  I have only installed the recommended software.  I tried the command line with the extra "sh" and when it was at about 15% installed my laptop rebooted.:(

---

### Post by Tony Flury on 2011-10-01
I have a ML-1865 (note - no w), and I used the download mentioned above, The only printer listed that was eve close to min i the list when i ran that autorun shell script was a 1865wspl - so i installed that.

the test page now generates an internal error message, so i assume that is not the correct driver - so which one should i pick ?

Solved - you have to use the ML-1860 printer driver - not the 1865wspl one

---

### Post by DjMojoRisin69 on 2011-10-03
Was anyone able to get it working with the WiFi? I have it setup with the cable, but can't figure out what I need to do to get it WiFi Enabled.

---

### Post by Kyo555 on 2011-10-14
as for the WiFi, you just have to find out your printers IP, I did this using the router-menu looking for the last device that connected.

then you go to the "unified driver configurator", add a new printer, go to manual select, then enter the printer's IP in ipp://, next select ML1865W and you're done.

---

### Post by Happibun on 2011-11-07
Hi guys,

I'm having an 'interesting' and frustrating afternoon trying to get my Samsung  ML-1865w to play nice.

I've tried sudo '/home/YOURUSERNAME/Desktop/cdroot/autorun', and sudo sh '/home/YOURUSERNAME/Desktop/cdroot/autorun'. The QT installer ran fine for me and I was able to enter what I thought was the right info, but with the USB plugged in to my lappy running 10.04 LTS, printing a test page brings 

> Internal Error - please use the proper driver.

Position : 0x0 (0)
system : h6fw_5.49/xl_op
Line: 180
Version : SPL 5.49 10-20-2010

The lappy tells me everything is fine and the drivers are installed and the printer is ready.

I've not even tried to network it through the WiFi yet, my router isn't seeing it, even when I switch off the WPA.

So....... What am I doing wrong?

Thanks, Jo

---

### Post by Happibun on 2011-11-07
OK, Scratch the above post.

I think I've worked out the problem.

It seems that Tesco put the wrong laser in to the wrong box when selling off it's shop soiled remnants...

Of course I was trying to install the wrong driver.:oops: No wonder I couldn't get the WiFi to see it either.

I'll sidle off now, nothing to see here... ahem..

---

### Post by shortmort37 on 2011-12-21
> **Kyo555 said:**
> as for the WiFi, you just have to find out your printers IP, I did this using the router-menu looking for the last device that connected.

then you go to the "unified driver configurator", add a new printer, go to manual select, then enter the printer's IP in ipp://, next select ML1865W and you're done.

I've got WEP encryption enabled on my wireless network.  Isn't it the case that the printer won't acquire an IP, until the key is defined in the printer?  How do I do that, without disabling encryption?

Dan

---

### Post by DimaKirk on 2012-01-10
> **shortmort37 said:**
> I've got WEP encryption enabled on my wireless network.  Isn't it the case that the printer won't acquire an IP, until the key is defined in the printer?  How do I do that, without disabling encryption?

Dan

Try restart printer.

---

### Post by nigeldodd on 2012-04-11
Mine says just ML-1865 on the top of its case so perhaps it lacks the wifi.

When I plugged the printer in using usb to the 11.10 64 bit computer it was identified and the ML-1860-Series driver loaded. However when I printed using this I got the "Internal Error - please use the proper driver system: h6f2_5.49/xl_op version spl 5.49 10-20-2010" error printed out on paper.

So I downloaded UnifiedLinuxDriver_0.98.tar.gz and uncompressed it.  Then run 
 sudo sh autorun

****  It seems Qt library is not installed, or X display is not accessible.
****  Custom Qt library will be configured for use with this package.
GUI mode installer execution failed, proceeding in text mode
****  Running text mode install
****  Press Enter to continue or q and then Enter to quit: 

**** Non-priviliged users found:
nobody kate liz geoff ed
****  Are you going to use USB-connected devices ?
****  If yes, users allowed to scan or manage printers should be added to lp
****  group. The list of non-privileged users proposed for addition is shown above.
****  Press y and then Enter to add users or Enter to leave lp group intact: 

****  Print drivers for the following device models available:
CLP-300splc CLP-310splc CLP-320splc CLP-340splc CLP-350ps CLP-500splc CLP-510splc CLP-550ps CLP-600splc CLP-610splc CLP-620splc CLP-650ps CLP-660ps CLP-670ps CLP-770ps CLX-216xsplc CLX-3160splc CLX-3170splc CLX-3180splc CLX-3240splc CLX-6200ps CLX-6220ps CLX-6240ps CLX-6250ps CLX-8380ps CLX-8385ps CLX-8385Xps CLX-8540ps CLX-9250ps mfp560 mfp65x mfp750 ML-1450ps ML-1510spl2 ML-1520spl2 ML-1610spl2 ML-1630spl2 ML-1630wspl2 ML-1640spl2 ML-1660spl ML-1710spl2 ML-1740spl2 ML-1750spl2 ML-1860spl ML-1865wspl ML-191xspl2 ML-2010spl2 ML-2150ps ML-2150spl2 ML-2240spl2 ML-2245spl2 ML-2250spl2 ML-2510spl2 ML-2525w ML-2550ps ML-2550Sps ML-2550Sspl2 ML-2560ps ML-2570ps ML-2580spl2 ML-2850ps ML-2853ps ML-2855ps ML-3050spl2 ML-3310spl2 ML-3470ps ML-3475ps ML-3560spl2 ML-3710ps ML-4050DMVps ML-4050ps ML-4055ps ML-451xps ML-4550ps ML-4555ps ML-5510ps ML-6060ps ML-7300ps ML-8850ps ML-8x00ps scx3200 scx4100 scx4200 scx4300 scx4500 scx4500w scx4600 scx4623fw scx4623 scx4725 scx4x16 scx4x20 scx4x21 scx4x24 scx4x25 scx4x26 scx4x28ps scx4x33ps scx5312f scx5635ps scx5835ps scx5835Xps scx5x30 scx6545ps scx6545Xps scx6x20PCL scx6x20 scx6x20PS scx6x22ps scx6x45ps scx6x55ps scx6x55Xps scx8030ps sf531p
****  Please enter model to install and press Enter: 


I tried first ML-1865wspl. The computer did some flashing and logged me out!

Reading the above messages I then tried ML-1860spl


****  Please enter model to install and press Enter:  ML-1860spl
INFO: Restarting udev ...
control: unrecognized option '--reload_rules'
INFO: Installing MFP port and SANE backend libraries ...
cd: 1877: can't cd to /usr/lib64/sane
ln: creating symbolic link `./K07smfpd': File exists
ln: creating symbolic link `./K07smfpd': File exists
ln: creating symbolic link `./K07smfpd': File exists
ln: creating symbolic link `./S93smfpd': File exists
ln: creating symbolic link `./S93smfpd': File exists
ln: creating symbolic link `./S93smfpd': File exists
ln: creating symbolic link `./S93smfpd': File exists
INFO: Installing GUI lpr ...
INFO: Fixing file ownership and permissions ...
INFO: Registering SANE backend ...
INFO: Registering CUPS printer ...
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop cups ; start cups. The restart(8) utility is also available.
cups stop/waiting
cups start/running, process 10409
INFO: CUPS restart OK
INFO: Creating menu entries ...
mkdir: cannot create directory `/proc/Desktop': No such file or directory
chmod: cannot access `/proc/Desktop': No such file or directory
chown: cannot access `/proc/Desktop': No such file or directory
mkdir: cannot create directory `/proc/.gnome-desktop': No such file or directory
chmod: cannot access `/proc/.gnome-desktop': No such file or directory
chown: cannot access `/proc/.gnome-desktop': No such file or directory
INFO: Finishing installation ...
****  Text mode install finished


Now I have three drivers: ML-1860-Series (installed automatically on connecting printer but generating output printed error message) ML-1865wspl and ML-1860spl. None of them work.

Something has appeared on the desktop called Samsung Unified Driver Configuation. It's not a shell script. When I cat it I get:


[Desktop Entry]
Name=Samsung Unified Driver Configurator
Name[C]=Samsung Unified Driver Configurator
Comment=Manage your printers and scanners here
Comment[C]=Manage your printers and scanners here
Type=Application
Exec=/opt/Samsung/mfp/bin/Configurator
Path=/opt/Samsung/mfp/bin
Icon=/opt/Samsung/mfp/share/images/Configurator.png
Terminal=0
TerminalOptions=
X-KDE-SubstituteUID=false
X-KDE-Username=

So what is this supposed to be?

if I go to /opt/Samsung/mfp/bin and execute Configurator I get 

./Configurator
./Configurator: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

I presume the .so is an old shared library no longer present on 11.10.

So, no resolution so far and a definite bad mark for Ubuntu and its general usefulness to ordinary people!

---

### Post by nigeldodd on 2012-04-11
Problem solved ML-1865 on 11.10. Remove all Samsung. Even the one that 11.10 offers without loading the Samsung universal driver must be removed. Then follow
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

thanks to tweeedledee.

---

### Post by stijnblommerde on 2012-05-03
printer ML-1865W 
OS 12.04

1. follow tweedledee: step 1,2,3
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

2. unlock and disable firewall (if enabled)

3. Link printer to modem via WPS (press and hold WPS button on both modem and printer)

4. download driver from Samsung Website. choose unified linux driver.
[http://www.samsung.com/us/support/owners/product/ML-1865W/XAA](http://www.samsung.com/us/support/owners/product/ML-1865W/XAA)

5. extract package to desktop (or any other location)

6. from terminal window: 
sudo sh /home/[username]/Desktop/cdroot/autorun
(Desktop with capital D!)

7. follow on screen instructions: 
- environment components: install anyway (in my case SANE was missing) 
- users in group: no
- disable lpt: yes
- network printer: search

8. log out and log in (to refresh printers listed in programs like libreoffice)

wireless printing works!

---

### Post by Killer Jacker on 2012-06-30
Man...
really you have waste your time to do this post?

logically, people asking here can't configure the wifi via WPS... ¬¬

---

