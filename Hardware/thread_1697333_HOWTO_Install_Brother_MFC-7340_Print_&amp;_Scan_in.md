---
title: "HOWTO: Install Brother MFC-7340 Print &amp; Scan in 10.04/10.10"
date: 2011-02-28
forum: Hardware
---

### Post by mechanizedmedic on 2011-02-28
**[COLOR="Red"]EDIT:[/COLOR]** i made a script that replaces this tutorial [HERE]("http://ubuntuforums.org/showpost.php?p=10971645&postcount=21").

the script installs dependencies, downloads the drivers, installs drivers, configures for usb printing and scanning. i have added a fix for 11.04 and 11.10 as well.

######################################

i believe that all of these steps are covered in various places in the [OFFICIAL BROTHER DOCUMENTATION]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html"). i can't take any credit for coming up with this stuff but i wanted to put it all into a fairly simple tutorial. BIG thanks to mdgrech and raywood for posting the previous howtos that helped me figure out my issues in 10.10. this is my first linux tutorial and i've only been using linux for a year so i'm sorry for any inaccuracies! if you see any mistakes or have any improvements let me know and i'll update this post. 


<<< LET'S ROCK 'N' ROLL >>>

[LIST=1]if you're like me and you screwed it up the first time you'll want to start clean. turn off/disconnect the printer then get the list of items you need to remove.
```
dpkg  -l  |  grep  Brother
```
the entries should be something like these (the name just  after "ii")
```
ii  brmfc7340lpr                         2.0.2-1                                           Brother MFC-7340 LPR driver
ii  cupswrappermfc7340                   2.0.2-1                                           Brother MFC7340 CUPS wrapper driver

```
  as long as this is the only Brother product you have drivers   installed for remove all of them.
```
sudo dpkg --purge *entryname*
```


[*]browse to "http://localhost:631/printers" and remove the any entries for your 7340


[*]setup apparmour
```
sudo aa-complain cupsd
```


[*]make required folders
```
sudo mkdir /usr/share/cups/model
```
```
sudo mkdir /var/spool/lpd
```


[*]install scan dependencies 
```
sudo apt-get install sane-utils psutils
```


[*]download the drivers
[LIST]
[*]64 bit
```
wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.amd64.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
```
[*]32 bit
```
wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
```
[/LIST]



[*]install the drivers
[LIST]
[*]64 bit
```
dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.amd64.deb brscan-skey-0.2.1-3.amd64.deb brmfcfaxcups-1.0.0-1.i386.deb
```
[*]32 bit
```
dpkg -i --force-all brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.i386.deb brscan-skey-0.2.1-3.i386.deb brmfcfaxcups-1.0.0-1.i386.deb
```
[/LIST]



[*]verify they are installed. if you had any errors... well, i'm not good enough to be of help. the brother troubleshooting FAQ is [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#141")
```
dpkg  -l  |  grep  Brother
```


[*]turn on and connect your printer. 


[*] CUPS setup
[LIST][*]browse to "http://localhost:631/admin" and click "add printer". 

[*]select the radio button "Brother MFC-7340". continue

[*]enter a location/name if desired and if you would like to share the printer over your network. continue

[*]the next screen should show:
[INDENT]Name: Brother_MFC-7340
Description: Brother MFC-7340
Location: *whateveryouentered*	
Connection: usb://Brother/MFC-7340
Sharing: *whatyouselected*
Make: Brother[/INDENT]


[*]in the pane next to "Model" scroll all the way down and select the first "Brother MFC7340 for CUPS(en)". add printer[/LIST]


[*]if your "connection" in the step above was different than listed go to printers tab->Brother_MFC-7340->administration->modify printer

[INDENT]for usb connection select: usb://Brother/MFC-7340

for network connection set these parameters:
[INDENT]Device: "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect"
Device URI: lpd://*printerIPaddress*/binary_p1
Make/Manufacturer: Brother
Model: MFC-7340[/INDENT]
[/INDENT]

[*]print you up a test page! yeeeeehaw! 


[*]enable normal users to access the scanner.
```
sudo nano /lib/udev/rules.d/40-libsane.rules
```
scroll to the bottom (hold ctrl+v) and add the lines highlighted in red as you see them here.
```
# Dell Dell MFP Laser Printer 1815dn
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5124", ENV{libsane_matched}="yes"
# Dell 1600n
ATTRS{idVendor}=="413c", ATTRS{idProduct}=="5250", ENV{libsane_matched}="yes"
[COLOR="Red"][B]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/B][/COLOR]
# The following rule will disable USB autosuspend for the device
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power/level && echo on $
LABEL="libsane_rules_end"

```


[*]add "brscan-skey" to to your startup list.
Ubuntu: System > Preference > Sessions > Startup Programs
Kubuntu: System Settings > Startup & Shutdown > Autostart


[*]restart your computer


[*]verify that brscan-skey is running
```
brscan-skey
```
output should look something like this
```
MFC-7340          : brother3:bus5;dev1  : USB                  Active

```


[*]on your printer, put a test page on the scanner bed, press scan, arrow down to "scan to file", press start. this should make a new folder in your home directory called "brscan" with the image in it and terminal output should be similar to this.
```
ohblackbetty@bamalam:~$ scan from USB(brother3:bus5;dev1) to /home/ohblackbetty/brscan/brscan.ZxxDtt
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
```

[*]for fax setup perform the following steps
[LIST]
[*]navigate to [http://localhost:631/printers/BRFAX](http://localhost:631/printers/BRFAX)
[*]in the "administration" dropdown select "modify printer"
[*]from the local printers list select "Brother MFC-7340 (Brother MFC-7340)" and hit continue.
[*]change location name and sharing if desired, click continue
[*]select "Brother" for the make of printer and... continue!
[*]choose the driver "Brother BRMFCFAX for CUPS" and click modify printer
[*]if you have a .ps file handy you can fax a test page with this command
```
brpcfax  -o  fax-number=faxnumber  filename
```
[/LIST]
[/LIST]

you should be ready to start using your MFC-7340!


NOTES:[LIST][*] i prefer to use xsane for scanning as it has all of the settings right up front. i tried simplescan and it wasn't, um... simple.
[*]i haven't had a chance to test the networked setup or fax functions but the steps here are pretty much straight from the Brother FAQ. if someone could test the fax operation and report back that would be mega awesome!
[*]i'm a Kubuntu guy but the steps should be the same or very similar for other variants.
[*]if you go into your printer configuration through system settings there should be a "scale to fit" option. this will help with graphical documents like pdf.
[*]if you're good with bash scripting and would like to mess around with that more info is [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn5.html#Inst7")
[*]for FAX capabilities the drivers are [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_pcf.html") installation is [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_pcf1a.html") and usage instructions are [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_pcf2.html").
[*] the official Brother Driver Installation Tool and instructions are available [HERE]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00090"). i didn't use it but it's certainly there if you want it! :)

[/LIST]

---

### Post by AmigoNico on 2011-03-01
Thanks so much for taking the time to write this up.  It worked great for me, with a couple of minor notes.

1. The link to the 64-bit scan driver:

[http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb&lang=English_gpl](http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb&lang=English_gpl)

was broken; but it worked without the query parameter:

[http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb](http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb)

Also, the CUPS interface was a bit different for me.  In particular, it set the connection to

usb:/dev/usb/lp0

and I had to Modify Printer and pick

usb://Brother/MFC-7340

from a list.  After that, she printed!

Thanks again.

---

### Post by mechanizedmedic on 2011-03-05
> **AmigoNico said:**
> Thanks so much for taking the time to write this up.  It worked great for me, with a couple of minor notes.

1. The link to the 64-bit scan driver:

[http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb&lang=English_gpl](http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb&lang=English_gpl)

was broken; but it worked without the query parameter:

[http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb](http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb)

Also, the CUPS interface was a bit different for me.  In particular, it set the connection to

usb:/dev/usb/lp0

and I had to Modify Printer and pick

usb://Brother/MFC-7340

from a list.  After that, she printed!

Thanks again.

thanks for the feedback!

it looks like i forgot to include the modify printer part. woops! i slapped it in there with USB and networked settings. fixed the broken link too.

i also added a link to the Brother Driver Installation Tool in the NOTES section just in case someone wants it.

---

### Post by Qu4rk on 2011-03-24
WOW!  Thanks for taking the time to write this up!  This is great & works perfectly for the printing.  I'm stuck at step 17.  There is no:  System > Preferences > Sessions in Ubuntu 10.10.  Where should I go?

Also, for anyone looking on how to print a test page:

```
1. Go to System > Administration > Printing
2. Right click on your printer and select its properties.
3. Click on the "Print a Test Page" button. You will get a printer test page that includes the Ubuntu logo and eight different color bars. 
```

---

### Post by mechanizedmedic on 2011-04-05
> **Qu4rk said:**
> WOW!  Thanks for taking the time to write this up!  This is great & works perfectly for the printing.  I'm stuck at step 17.  There is no:  System > Preferences > Sessions in Ubuntu 10.10.  Where should I go?

Also, for anyone looking on how to print a test page:

```
1. Go to System > Administration > Printing
2. Right click on your printer and select its properties.
3. Click on the "Print a Test Page" button. You will get a printer test page that includes the Ubuntu logo and eight different color bars. 
```

apologies for the delay... in maverick it should be under System > Preferences > Startup Applications. you can also get "startup manager" from the software center to help administer those changes.

---

### Post by skibler on 2011-04-07
I have an HL-2270DW, and I am not having a lot of success with 64-bit ubuntu. I had 32-bit ubuntu up until a few days ago, and it worked fine with it.

Under 64-bit ubuntu, when I go to install, it gets stuck installing the lp deb:

```

root@deskbuntu:/home/patrick/Desktop/brother# dpkg -i --force-all hl2270dwlpr-2.1.0-1.i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 175700 files and directories currently installed.)
Preparing to replace hl2270dwlpr:i386 2.1.0-1 (using hl2270dwlpr-2.1.0-1.i386.deb) ...
Unpacking replacement hl2270dwlpr:i386 ...
dpkg: dependency problems prevent configuration of hl2270dwlpr:i386:
 hl2270dwlpr:i386 depends on libc6 (>= 2.3.4-1).
dpkg: error processing hl2270dwlpr:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hl2270dwlpr:i386

```

I have the latest ia32-libs and lib32stdc++6 packages already installed.

Does any one have any ideas about how I can proceed here? Thank you!

---

### Post by mechanizedmedic on 2011-04-08
> **skibler said:**
> I have an HL-2270DW, and I am not having a lot of success with 64-bit ubuntu. I had 32-bit ubuntu up until a few days ago, and it worked fine with it.

Under 64-bit ubuntu, when I go to install, it gets stuck installing the lp deb:

```

root@deskbuntu:/home/patrick/Desktop/brother# dpkg -i --force-all hl2270dwlpr-2.1.0-1.i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 175700 files and directories currently installed.)
Preparing to replace hl2270dwlpr:i386 2.1.0-1 (using hl2270dwlpr-2.1.0-1.i386.deb) ...
Unpacking replacement hl2270dwlpr:i386 ...
dpkg: dependency problems prevent configuration of hl2270dwlpr:i386:
 [COLOR="Red"]**[SIZE="3"]hl2270dwlpr:i386 depends on libc6[/SIZE]**[/COLOR] (>= 2.3.4-1).
dpkg: error processing hl2270dwlpr:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hl2270dwlpr:i386

```

I have the latest ia32-libs and lib32stdc++6 packages already installed.

Does any one have any ideas about how I can proceed here? Thank you!

please take the time to read error messages. the data you posted already indicates that libc6 needs to be installed. search for it in the software center or use this terminal command.

```
sudo apt-get install libc6
```

it might help to purge the old driver packages and config files before re-installing. IMHO it's always better to start clean.

---

### Post by skibler on 2011-04-08
> **mechanizedmedic said:**
> please take the time to read error messages. the data you posted already indicates that libc6 needs to be installed. search for it in the software center or use this terminal command.

```
sudo apt-get install libc6
```

it might help to purge the old driver packages and config files before re-installing. IMHO it's always better to start clean.

mechanizedmedic, think about what you are telling me to do. Try *sudo apt-get remove libc6* and see how far you get. libc6 (and libc6-i386, btw) is obviously already installed, because if it wasn't, I would have much larger problems than a bad printer driver.

Thanks for trying to help, I guess.


**edit**:

Turns out that the package files are 'installed', but not 'configured'. A useless distinction to make in this case, since all the 'configuration' does here is run a bash script that was 'installed'. I ran the bash script manually, and the printer driver is magically installed.

Now I just have to get apt to shutup about the unconfigured packages. . .

---

### Post by mechanizedmedic on 2011-04-10
i never instructed that libc6, or any other critical packages, be removed... try reading things a bit more carefully.

you're welcome i guess. ):P

---

### Post by madapiarist on 2011-04-19
@ skibler  Can you give a few more details on where you found and ran these scripts?  I have the same problem with an MFC-7360n complaining about libc6 under 11.04     :confused:

I have a 2070n that is working using the 2060 driver right now.  Scanner works perfectly with x64 driver from Brother.

dpkg  -l  |  grep  Brother
iU  brhl2070nlpr:i386                     2.0.1-1                                    Brother HL-2070N LPR driver
ii  brscan-skey                           0.2.1-3                                    Brother Linux scanner S-KEY tool
ii  brscan4                               0.3.0-2                                    Brother Scanner Driver
iU  cupswrapperdcp1000:i386               1.0.2-1                                    Brother DCP1000 CUPS wrapper driver
iU  cupswrappermfc7360n:i386              2.0.4-2                                    Brother MFC7360N CUPS wrapper driver
ii  dcp1000lpr:i386                       1.1.2-1                                    Brother lpr Printer Definitions
iU  mfc7360nlpr:i386                      2.1.0-1                                    Brother MFC-7360N LPR driver

---

### Post by tom__d on 2011-04-20
Thanks for the tutorial configuring my printer.  I am having lots of fun trying to figure it out.  I am novice.  I don't have the username and password for [http://localhost:631/admin](http://localhost:631/admin).  can someone help me ?   thnks  tom__d

---

### Post by tom__d on 2011-04-20
[QUOTE=tom__d;10700812]Thanks for the tutorial configuring my printer.  I am having lots of fun trying to figure it out.  I am novice.  I don't have the username and password for [http://localhost:631/admin](http://localhost:631/admin).  can someone help me ?   thanks  tom__d

---

### Post by tom__d on 2011-04-21
Here is a driver that will allow you to print.  HP laserjet 8150 n.   tom__d

---

### Post by mageus on 2011-05-03
> **skibler said:**
> Turns out that the package files are 'installed', but not 'configured'... I ran the bash script manually, and the printer driver is magically installed

Can you please clarify?
- Which are the files you refer to as installed but not configured?
- Which bash script did you run?

TIA

---

### Post by skibler on 2011-05-09
> **mechanizedmedic said:**
> i never instructed that libc6, or any other critical packages, be removed... try reading things a bit more carefully.

you're welcome i guess. ):P

I never suggested you did! "libc6 (and libc6-i386, btw) is obviously already installed, because if it wasn't, I would have much larger problems than a bad printer driver." If I didn't have libc6 installed, my system would not be operational at all, let alone my printer.


> **mageus said:**
> Can you please clarify?
- Which are the files you refer to as installed but not configured?
- Which bash script did you run?

TIA

What I was saying is that hl2270dwlpr-2.1.0-1.i386.deb and cupswrapperHL2270DW-2.0.4-2.i386.deb were partially installed by dpkg. The files they contain were installed to my system, but their configuration scripts fail to run.

Since all the configuration scripts do is run a script (one of the files installed to the system), I just ran the script myself, and then viola! When adding a printer, the drivers are available.

Certainly not a perfect solution, as every now and again aptitude reminds me that the packages still need to be configured, but that is all.

Anyway, the script is /usr/local/Brother/Printer/HL2270DW/cupswrapper/cupswrapperHL2270DW-2.0.4

If you look inside, you can see that it actually just generates a PPD file and installs to to the proper place (some one on the gentoo forums pointed this out). Why Brother can't just have the PPD file available for download, I have no idea.

Obviously the path would be different for a different model printer. And all I will promise is that it worked for me!

---

### Post by TragicWarrior on 2011-05-25
I took the information found in various replies of this thread and create a single (very short) howto for getting the x86-64 version of this working.  The deb packages I used and the howto file can be found here:

[http://www.mediafire.com/?gb9jbhh2cghjz](http://www.mediafire.com/?gb9jbhh2cghjz)

Note:  My model is the mfc7360n so you will probably need different pkgs.

Hope this helps others and thanks to the original poster who got this initially figured out.

---

### Post by single29 on 2011-06-01
....since all the 'configuration' does here is run a bash script that was 'installed'. I ran the bash script manually, and the printer driver is magically installed.

Can you show me how to "manually" "configure" the problem of "depends on libc6 (>= 2.3.4-1)"

Thanks.

---

### Post by Gizmoe142 on 2011-06-06
Holly Crap! Thanks so much I have been fighting with this stupid printer and Ubuntu 8.04 for almost a year now, people keep telling me how to make it work and then nothing. Then I decided I might have better  luck with 10.04 and have been struggling with that for a couple days. I was thinking about scrapping linux or the printer or both, Then I stumbled across this thread. Thanks so much I can tell you how much you have helped me. Yeah!:p

---

### Post by mechanizedmedic on 2011-06-13
> **Gizmoe142 said:**
> Holly Crap! Thanks so much I have been fighting with this stupid printer and Ubuntu 8.04 for almost a year now, people keep telling me how to make it work and then nothing. Then I decided I might have better  luck with 10.04 and have been struggling with that for a couple days. I was thinking about scrapping linux or the printer or both, Then I stumbled across this thread. Thanks so much I can tell you how much you have helped me. Yeah!:p

great news! i had a similar experience when i first bought my printer. i eventually found all of the documentation on Brother's site but it's not well organized.

i'm working on a script that will do all of these steps on it's own [HERE.]("http://ubuntuforums.org/showpost.php?p=10882707&postcount=1")

---

### Post by Nullomore on 2011-06-21
I'm a total newbie, and this worked perfectly for me. Thanks so much!

---

### Post by mechanizedmedic on 2011-06-23
the following bash script should work with 32 or 64 bit systems. it is meant to configure the printer for USB/non-shared use. i have not tested it enough for it to be a complete replacement for the main tutorial but it should work fine for most. 

also,steps 11, 14, & 18 are not part of this script. 

EDIT: added some stuff that should aid with 11.04 users.

if you use this please post back with how it went. thanks!

[LIST=1][*]copy/paste the following script into a text file and save it in your home directory as "brothermfc7340.sh"
```
#!/bin/sh
#designed for Ubuntu 10.10 variants
#script_name="brothermfc7340.sh"

# Script must run as root
if [ $(id -u) -ne 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

# make the required directories
mkdir /usr/share/cups/model /var/spool/lpd

#install scan dependancies
apt-get install -y sane-utils psutils

#apparmour in complain model
aa-complain cupsd

#download and install .deb files

if [ $(uname -m) = "x86_64" ]; then
# 64-bit
  apt-get install ia32-libs
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.amd64.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all --force-architecture brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.amd64.deb brscan-skey-0.2.1-3.amd64.deb brmfcfaxcups-1.0.0-1.i386.deb
else
# 32-bit
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all --force-architecture brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.i386.deb brscan-skey-0.2.1-3.i386.deb brmfcfaxcups-1.0.0-1.i386.deb
fi

#stop cups
/etc/init.d/cups stop

#edit cups printers.conf file to add printing and faxing
sed -i '/CUPSD IS RUNNING/a\
<Printer BRFAX>\n
Info BRFAX\n
MakeModel Brother BRMFCFAX for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306719206\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brfaxfilter\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n
<Printer Brother_MFC-7340>\n
Info Brother MFC-7340\n
MakeModel Brother MFC7340 for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306715389\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brlpdwrapperMFC7340\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n' /etc/cups/printers.conf

#start cups
/etc/init.d/cups start

#enable normal user to access the scanner
sed -i '/autosuspend/i\# Brother scanners\nATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"' /lib/udev/rules.d/40-libsane.rules

##If Ubuntu 11.04 or 11.10 run post installation scritps

ver=$(awk '{ if(NR==1) print $2 }' /etc/issue)

if [ $ver = 11.04 -o 11.10 ]  then  echo Ubuntu 11.04 or 11.10 is installed; sleep 2;

  /usr/local/Brother/inf/setupPrintcap MFC7340 -i USB
  /usr/local/Brother/inf/braddprinter -i MFC7340

  if [ -d /usr/lib32 ]
    then ln -s /usr/lib/libbrcomplpr2.so /usr/lib32/libbrcomplpr2.so
  fi

  if [ -e /etc/init.d/lprng ]; then
     /etc/init.d/lprng restart
  elif [ -e /etc/init.d/lpd ]; then
     /etc/init.d/lpd restart
  fi

  if [ ! -e /usr/sbin/pstops ]
    then PSTOPS=`which pstops`
      if [ "`echo $PSTOPS | grep -i cups`" != "" ]
	then PSTOPS=""
      fi
      if [ "$PSTOPS" != "" ]
	then	echo [psconvert2]   >>/usr/local/Brother/inf/brMFC7340func
		echo pstops=$PSTOPS >>/usr/local/Brother/inf/brMFC7340func
      fi
  fi

  if [ -e /bin/sh ]
      then sh /usr/local/Brother/cupswrapper/cupswrapperMFC7340-2.0.2 -i
    elif [ -e /bin/bash ]
      then bash /usr/local/Brother/cupswrapper/cupswrapperMFC7340-2.0.2 -i
    else 	echo ''
	  echo ' ****** ERROR: bash is required. ******'
  fi

  else  echo Ubuntu 11.04 or 11.10 are not installed...
fi
sleep 1
echo ' '
echo Script complete!
echo ' '
sleep 1
echo 'Please report your results to http://ubuntuforums.org/showthread.php?t=1697333'
echo ' '


```

[*]then run the following commands in a terminal
```
sudo chmod 777 brothermfc7340.sh
sudo ./brothermfc7340.sh
```

[/LIST]

---

### Post by kdv666 on 2011-06-28
> What I was saying is that hl2270dwlpr-2.1.0-1.i386.deb and
> cupswrapperHL2270DW-2.0.4-2.i386.deb were partially installed by dpkg.
>The files they contain were installed to my system, but their 
> configuration scripts fail to run.

Many thanks for that suggestion.  I was having the same problem, but the script you found fixes it for me too ( Ubuntu 11.04, 64-bit, MFC-7340 ).  I've been on the phone to Brother to report the problem, so I hope they'll release a general fix.  In the meantime, your idea gets it going fine!

---

### Post by plizzba on 2011-07-27
> **skibler said:**
> Turns out that the package files are 'installed', but not 'configured'. A useless distinction to make in this case, since all the 'configuration' does here is run a bash script that was 'installed'. I ran the bash script manually, and the printer driver is magically installed.

Now I just have to get apt to shutup about the unconfigured packages. . .

I managed to get the printer working in 11.04 in 64 bit following a variant of Skibler's advice. I tried to install brothers drivers "brmfc7340lpr" and "cupswrappermfc7340" and both failed. It would fail to install and then try to remove the packages and then fail to do that. (good job Brother!). It seemed to leave the packages "installed" but not "configured" as Skibler suggests. So, I ran what seemed to be the relevant pieces of the two files:
[LIST]
[*]/var/lib/dpkg/info/brmfc7340lpr.postinst
[*]/var/lib/dpkg/info/cupswrappermfc7340.postinst
[/LIST]
This seems to have added a working printer to my system. 

I guess on the downside, I have two packages which the system thinks are only partly installed.

I'm not sure this is how I would suggest dealing with these problems. Maybe someone smarter than me could repackage brother's driver and make it work without these headaches?

---

### Post by Qu4rk on 2011-07-28
What needs to change about your script to get it to work in 11.04 64 bit?

> **mechanizedmedic said:**
> the following bash script should work with 32 or 64 bit systems. it is meant to configure the printer for USB/non-shared use. i have not tested it enough for it to be a complete replacement for the main tutorial but it should work fine for most. 

also,steps 11, 14, & 18 are not part of this script. 

if you use this please post back with how it went. thanks!

[LIST=1][*]copy/paste the following script into a text file and save it in your home directory as "brothermfc7340.sh"
```
#!/bin/sh
#designed for Ubuntu 10.10 variants
script_name="brothermfc7340.sh"

# Script must run as root
if [ $(id -u) -ne 0 ]; then
        echo "You need to run this script as root."
        echo "Use 'sudo ./$script_name' then enter your password when prompted."
        exit 1
fi

# make the required directories
mkdir /usr/share/cups/model /var/spool/lpd

#install scan dependancies
apt-get install -y sane-utils psutils

#apparmour in complain model
aa-complain cupsd

#download and install .deb files

if [ $(uname -m) = "x86_64" ]; then
# 64-bit
  apt-get install ia32-libs
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brscan3-0.2.11-4.amd64.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.amd64.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all --force-architecture brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.amd64.deb brscan-skey-0.2.1-3.amd64.deb brmfcfaxcups-1.0.0-1.i386.deb
else
# 32-bit
  wget http://www.brother.com/pub/bsc/linux/dlf/brmfc7340lpr-2.0.2-1.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/cupswrapperMFC7340-2.0.2-1.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb http://www.brother.com/pub/bsc/linux/dlf/brscan-skey-0.2.1-3.i386.deb http://pub.brother.com/pub/com/bsc/linux/dlf/brmfcfaxcups-1.0.0-1.i386.deb
  dpkg -i --force-all --force-architecture brmfc7340lpr-2.0.2-1.i386.deb cupswrapperMFC7340-2.0.2-1.i386.deb brscan3-0.2.11-4.i386.deb brscan-skey-0.2.1-3.i386.deb brmfcfaxcups-1.0.0-1.i386.deb
fi

#stop cups
service cups stop

#edit cups printers.conf file to add printing and faxing
sed -i '/CUPSD IS RUNNING/a\
<Printer BRFAX>\n
Info BRFAX\n
MakeModel Brother BRMFCFAX for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306719206\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brfaxfilter\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n
<Printer Brother_MFC-7340>\n
Info Brother MFC-7340\n
MakeModel Brother MFC7340 for CUPS\n
DeviceURI usb://Brother/MFC-7340\n
State Idle\n
StateTime 1306715389\n
Type 8392708\n
Filter application/vnd.cups-raw 0 -\n
Filter application/vnd.cups-postscript 0 brlpdwrapperMFC7340\n
Accepting Yes\n
Shared No\n
JobSheets none none\n
QuotaPeriod 0\n
PageLimit 0\n
KLimit 0\n
OpPolicy default\n
ErrorPolicy retry-job\n
</Printer>\n' /etc/cups/printers.conf

#start cups
service cups start

#enable normal user to access the scanner
sed -i '/autosuspend/i\# Brother scanners\nATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"' /lib/udev/rules.d/40-libsane.rules

```

[*]then run the following commands in a terminal
```
sudo chmod 777 brothermfc7340.sh
sudo ./brothermfc7340.sh
```

[/LIST]

---

### Post by mechanizedmedic on 2011-07-30
> **Qu4rk said:**
> What needs to change about your script to get it to work in 11.04 64 bit?

i believe adding the following bit at the end of my script should take care of things. it's basically the contents of the two scripts (mentioned by others in this thread) with a condition to only run on 11.04.

i'll add this into my post above... and, as always, if someone could test this on a fresh install i would be very grateful!

```
ver=$(awk '{ if(NR==1) print $2 }' /etc/issue)

if [ $ver = 11.04 ]
  then  

  /usr/local/Brother/inf/setupPrintcap MFC7340 -i USB
  /usr/local/Brother/inf/braddprinter -i MFC7340

  if [ -d /usr/lib32 ]
    then ln -s /usr/lib/libbrcomplpr2.so /usr/lib32/libbrcomplpr2.so
  fi

  if [ -e /etc/init.d/lprng ]; then
     /etc/init.d/lprng restart
  elif [ -e /etc/init.d/lpd ]; then
     /etc/init.d/lpd restart
  fi

  if [ ! -e /usr/sbin/pstops ]
    then PSTOPS=`which pstops`
      if [ "`echo $PSTOPS | grep -i cups`" != "" ]
	then PSTOPS=""
      fi
      if [ "$PSTOPS" != "" ]
	then	echo [psconvert2]   >>/usr/local/Brother/inf/brMFC7340func
		echo pstops=$PSTOPS >>/usr/local/Brother/inf/brMFC7340func
      fi
  fi

  if [ -e /bin/sh ]
      then sh /usr/local/Brother/cupswrapper/cupswrapperMFC7340-2.0.2 -i
    elif [ -e /bin/bash ]
      then bash /usr/local/Brother/cupswrapper/cupswrapperMFC7340-2.0.2 -i
    else 	echo ''
	  echo ' ****** ERROR: bash is required. ******'
  fi

  else  echo 

fi
```

---

### Post by shubsagar on 2011-09-01
I have just bought Brother MFC 7360N scanner and printer.Printer I have installed and I followed the intrusction for the scanner,at the end it say that you should add brscan-skey in start up program.I tried to do that but I do not know how to add it.It is asking for the path which I do not know and my scanner is not working.I am using ubuntu 11.04
Can anybody help me
with regards,
Gourik
[EMAIL="gcgoswami@gmail.com"]gcgoswami@gmail.com[/EMAIL]

---

### Post by shubsagar on 2011-09-01
I have just bought Brother MFC 7360N scanner and printer.Printer I have  installed and I followed the intrusction for the scanner,at the end it  say that you should add brscan-skey in start up program.I tried to do  that but I do not know how to add it.It is asking for the path which I  do not know and my scanner is not working.I am using ubuntu 11.04
Can anybody help me
with regards,
Gourik
[EMAIL="gcgoswami@gmail.com"]gcgoswami@gmail.com[/EMAIL]

---

### Post by mechanizedmedic on 2011-09-02
> **shubsagar said:**
> I have just bought Brother MFC 7360N scanner and printer.Printer I have  installed and I followed the intrusction for the scanner,at the end it  say that you should add brscan-skey in start up program.I tried to do  that but I do not know how to add it.It is asking for the path which I  do not know and my scanner is not working.I am using ubuntu 11.04
Can anybody help me
with regards,
Gourik
[EMAIL="gcgoswami@gmail.com"]gcgoswami@gmail.com[/EMAIL]

Go to System -> Preferences -> Startup Applications
Click the "+Add" button
Name: Brother Scan Tool
Command: brscan-skey

That should get you going with the auto-start issue.

Just to be sure, did you install the drivers that are specific to your printer model?

---

### Post by skibler on 2011-09-07
I am not sure what I did (maybe it is a change in 11.10 vs 11.04?), but aptitude is now insisting it fix the two Brother printer packages on my 64-bit system, and it won't let me do any other package operations until I do so. Very annoying, as the only option it gives to fix them is to uninstall them.

I used the script in this thread [http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724) and removed the dependencies on libc6 for both Brother packages. They then both install without error.

---

### Post by mechanizedmedic on 2011-11-27
i recently moved my three computers from Kubuntu 10.04 to Ubuntu 11.10. i found that my script from post #21 works if you change "11.04" to "11.10" in the script. hopefully it works the same for others. :)

---

### Post by nozyczek on 2012-01-13
Anyone got MFC-7360N scanner working under 11.10 64bit?

---

### Post by Qu4rk on 2012-04-30
> **nozyczek said:**
> Anyone got MFC-7360N scanner working under 11.10 64bit?

No, I can't.  Hope the OP responds.  

> brscan-skey

Gives blank results.

---

### Post by nozyczek on 2012-04-30
I guess it is time to try it on 12.04 and start bugging Brother again. Ehhh ...

---

### Post by mechanizedmedic on 2012-07-23
> **Qu4rk said:**
> No, I can't.  Hope the OP responds.  



Gives blank results.
sorry for not maintaining, i've been goofing around on Mint and Arch the last few months.

this might help with the new found scanning issues: [http://welcome.solutions.brother.com/bsc/Public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/Public_s/id/linux/en/faq_scn.html#f00101)

---

