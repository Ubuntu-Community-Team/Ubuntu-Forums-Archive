---
title: "Installing Brother printer driver."
date: 2015-04-28
forum: Hardware
---

### Post by ozark_hillbilly on 2015-04-28
I am trying to install a printer driver off the support.brother.com website for my new HL-L2360DW. I currently have the printer connected through an Ethernet cable to my router.
The Network configuration of the printer has been printed out and everything looks OK; the link status is OK.

***************************************************
Brother site instructions [[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559]](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559]) :

Download LPR driver.
 
Login as a superuser ( or use "sudo" option if required).
 
Install the driver.
Turn on the printer and connect the usb, network or parallel cable.
Go to the directory where the driver is.
Install LPR driver.The install process may take some time. Please wait until it is complete. 

Command  :  dpkg -i --force-all  (lpr-drivername)

Check if the LPR driver is installed.
Command  :  dpkg -l  |  grep  Brother

****************************************************************
I downloaded the file: hll2360dlpr-3.2.0-1.i386.deb.
When I click on that file in my Downloads folder Archive Manager invokes with the information shown on the attached screenshot image.

I am unsure what the "lpr-drivername" is supposed to be. 

Any help is greatly appreciated or if there is a simpler way to do this.

---

### Post by ozark_hillbilly on 2015-04-28
OK, I got this thing to work using a generic install, with a generic (local) driver, under ADD+ printer [System Settings-Printers]. I would really like to use the drivers created for this specific printer though.

---

### Post by Bucky Ball on 2015-04-29
You need the cups and the lpr drivers from what I can remember.

---

### Post by SeijiSensei on 2015-04-29
Start here: [http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en&content=dl](http://support.brother.com/g/b/productsearch.aspx?c=us&lang=en&content=dl)

Navigate to your printer, and you'll see a page asking you to pick an operating system.  Choose Linux and .deb, then press Search.  You should see the "Driver Install Tool" at the top of the list of offered software.  If you download that and run it as instructed, you should end up with the correct drivers.

---

### Post by ozark_hillbilly on 2015-04-30
I did what you suggested. But I do not know the name of the (lpr-drivername).

To run: Command : dpkg -i --force-all (lpr-drivername) I need to know the name. My attached thumbnail screenshot in the original post shows the download but I am unsure of the driver name.

---

### Post by Bucky Ball on 2015-04-30
dnssd://Brother%20HL-2270DW%20series._pdl-datastream._tcp.local/

That's what I have for my wireless Brother printer URI, if it is of any help, which it won't be unless you have the correct drivers installed. As I mentioned previously, install the CUPS driver, open a browser, go to 'localhost:631' (put that in the address bar of the browser). You should be able to install the driver via CUPS (add printer) and that should be pretty much it. That's what I generally do nowdays when this situation arises. 

Once you have the correct driver installed and have added the driver via CUPS interface, check 'Printers' and see if your printer appears there. Remind me: are you just trying to install drivers or are you wanting to use the printer's wireless function?

Hopefully there is something of help there. I'll have a closer look at the thread once I've caught my breath. Been a busy day and I have only just sat down with a cuppa ... (at 01:15am). The night/morning is but a pup! ;)

The link in your first post is down at the moment so hard to check exactly what they have available, but from memory, it was a CUPS, an LPR and an automagic one that installs both for you. My printer how-to you PMed about may hold a few clues. If there's anything there you need some tips with, just ask (on this thread, naturally ;)).

Have faith, you will get there in the end! It took me ages the first time, and I put together a set up for my friend who was starting uni with the same printer and couldn't get wireless going (and she is running the exact same study hybrid custom mini-install as I am). Also, my how-to was for a HL-2270DW, not the same model as yours, not sure if they'd be any major differences, though.

PS: Just a thought. Try plugging it in with a USB cable to your Ubuntu box then go to Printer> Add Printer and go through the motions and see if the driver is there in the default list when you get to that bit, but you may have already done all this ... you could try the same in CUPS (localhost:631) possibly with the same result.

---

### Post by SeijiSensei on 2015-05-01
> **ozark_hillbilly said:**
> I did what you suggested. But I do not know the name of the (lpr-drivername).
When I ran the utility with the command:
```
sudo linux-brprinter-installer-2.0.0-1
```
all I had to do was enter the printer's model number and confirm the steps that followed.

---

### Post by ozark_hillbilly on 2015-05-03
Bucky Ball,

I already had CUPS installed according to what Synaptic Package Mgr told me.
I entered the localhost:631 and got the CUPS page. After going into the Enter Printer function it asked for my Brother model but it was not shown in the list of available printers. What now?
see attachment of screenshot on CUPS page....

---

### Post by SeijiSensei on 2015-05-03
Pick one that has a model number close to yours.  When I used this method, I had to choose the HL-3070CDW driver from the CUPS list even though I have a 3170CDW.  Worked fine.  In fact, I think it probably doesn't matter a whole lot which exact model you pick.  The printer control language should work with pretty much all of them.

---

### Post by Bucky Ball on 2015-05-04
If CUPS is not showing the correct driver you don't have it installed (or have it installed incorrectly). Once the driver is installed it should show up in that list.

Just a note: The correct driver, when installed, possibly won't show up in the list in the correct alphabetical place or where you think it should be (with the other drivers in that series). If you are sure you have the LPR and CUPS drivers installed, have a thorough look for it in cups. Make sure it isn't last on the driver list or stuck somewhere else on the list you wouldn't expect.

Also, check 'Printing> Add Printer' and have a look at the list of drivers it gives there. Still no sign?

PS: It MAY matter what driver you pick. It did with mine. I was using the wrong driver and could print, but other functionality was limited. 

PPS: I am talking about installing the CUPS driver from HP, not the generic cups that comes with Ubuntu (that is what gives you the cups pages, etc., not a driver, as such).

---

### Post by pdc on 2015-05-04
Hi Ozark;
_____________

so to get a printer working you usually need 3 steps:

1) establish a connection
2) install drivers
3) register the printer on your system 

________


if I was suggesting to someone how to install their Brother HL-L2360DW

I would go here as suggested [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128)

and the problem is that with the Brother laser printers, the install tool that they offer is only available for the inkjet series; 

so you need to install 

1) the lpr driver from here [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559)

and 

2) after that the CUPS driver from here [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101917_000&flang=4&type3=561](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101917_000&flang=4&type3=561)

........ as has been suggested, when you click to download, ubuntu should leap in and offer to install what you are selecting to download.........if it does..............accept that kind offer ..............

________

then you need to tell your system all about this new printer: a good way should be to click on the PRINTERS option from the ubuntu menu; and ADD a new printer ..........if the lpr and then cups drivers went in ok, it should find the HL-L2360DW

_____________

you can check the drivers were installed ok by pasting this command into a terminal ```
dpkg -l | grep Brother
```             .............. please ask how to do that if you don't know .............

---

### Post by SeijiSensei on 2015-05-04
> **pdc said:**
> the install tool that they offer is only available for the inkjet series
I have a "laser-class" printer, and the install tool worked for that as well.

---

### Post by kurt18947 on 2015-05-04
Here are a few steps/tricks I use to manipulate Brother printers. My Brothers are Multi-function inkjets and find the installer script works quite well. If I choose to not use the installer, I find the below still works on Ubuntu-Gnome. I don't know for sure it'll work with Unity but suspect it will.

1) install from the repositories 'system-config-printer'. This was used prior to Gnome 3 and still works on Ubuntu-Gnome, Xubuntu and comes preinstalled on other distros. This app gives more information and flexibility than the default 'printers' app in Gnome3/Unity. 'Dumbing-down' is not always useful IMO. I installed a desktop launcher for it.

2) This may be retro and no longer required but I assign a static I.P. to my printers. This is pretty simple for me because I have a numeric keypad on my machines. I assume there's a way to assign a static I.P. to machines without keypads but I don't know what it is. Brother offers a .pdf with network install instructions and tips. It does take a bit of hunting.

3) Yes you need to install the .lpt driver before the .cups driver. Once both drivers are installed without hiccups, I type <alt>+f2 then system-config-printer. This opens a window.  The title will be something like 'Printers - localhost'. 

4)Click 'Server' -> New -> Printer -> New. A new window will open titled 'New Printer'. At this point you could either select 'Enter Device URI" and enter the I.P. address you assigned or select 'find networked printer' and follow the prompts.

5) Again this may no longer be required but it has been very reliable and I tend to stay with what has worked. I right-click the now-installed printer and click 'properties'. If the Device URI doesn't say 'socket://xxx.xxx.xxx.xxx:9100' I change it so it does. The x's are the assigned I.P. address, :9100 is the port. 

I believe this sort of mimics HP JetDirect install. Brother printers seem to hew pretty closely to HP standards. I've read where people couldn't find a linux Brother printer driver for a Brother laser and used an HP laser printer driver instead. It worked but today I doubt there's any need with Brother offering linux drivers for most if not all their machines.

I hope this is of some help to you and other searchers.

---

### Post by ozark_hillbilly on 2015-05-06
I appreciate the help thus far but I don't think anyone is listening to what I am saying.

After I download these files from the Brother support site:

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101916_000&flang=4&type3=559)

[http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101917_000&flang=4&type3=561](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2360dw_us&os=128&dlid=dlf101917_000&flang=4&type3=561)

I have two .deb files in my Downloads folder; these can be seen with the attached screenshot that used Archive Manager to view them:

hll2360dlpr-3.2.0-1.i386.deb

hll2360dcupswrapper-3.2.0-1.i386.deb

******************************************************************************************************8

Then I am supposed to:

"Go to the directory where the driver is.
Install LPR driver.The install process may take some time. Please wait until it is complete." 

Command : dpkg -i --force-all (lpr-drivername)

**Where is the directory location to find the driver? **

**What is the lpr-drivername to use at the end of the command line: dpkg -i --force-all ?**

Without knowing the correct directory to access or the lpr-drivername I cannot proceed as Ubuntu did not automatically 
offer to install this stuff or maybe it did and I just don't realize that.

*************************************************************************************************

Check if the LPR driver is installed.
Command : dpkg -l | grep Brother

I do have this Terminal info as a result of executing the grep Brother:

ed@ed-G41MT-S2PT:~$ dpkg -l | grep Brother
ii  printer-driver-ptouch                                 1.3-8                                               i386         printer driver Brother P-touch label 

Perhaps I am being "clear as mud" again.....  ;)

---

### Post by pdc on 2015-05-06
Hi Ozark;

let's see if we can get this going for you; thanks for the results of > dpkg -l | grep Brother .........to me, that shows the Brother drivers are not installed; and also you are adept at using a terminal: great

_____________-

so you very helpfully tell us the two packages you need to install are in your Downloads folder: thanks for that;

so if you issue the command in a terminal: (ie open terminal and paste command in)

```
cd Downloads
```

.................then that command  "gets us inside" the Downloads directory; which is where we need to be to "light the fuse" on the two driver packages ...............

__________

then to install the lpr ```
sudo dpkg -i --force-all hll2360dlpr-3.2.0-1.i386.deb
```            .............so I have just taken the command you quoted.....added sudo in front of it ....and pasted the name of the driver you helpfully quote after that ........to get that command ......

________

so for the cupswrapper driver ........ same format

```
sudo dpkg -i --force-all hll2360dcupswrapper-3.2.0-1.i386.deb
```

__________

so that is the drivers installed; now to register it .........if you paste this command into a terminal ```
system-config-printer
``` and when that box opens, click on the ADD ....and get it to search........make sure the brother is powered up and connected .....it should find it and configure it and there should be a "print a test page" button ?? ............

........how are we doing?

---

### Post by Bucky Ball on 2015-05-07
.deb files only need to be double clicked to install. And you didn't notice that on the download page I linked to there is another download apart from the lpr and cups drivers. The Installer, which does all the installing for you. 

Bottom line: double click the lpr .deb. It will install, probably using SCentre or gdebi. Once done, double click the cups .deb. Install. Reboot, add printer ...

You don't need to use a terminal at all for .deb files, unless you want to install them that way.

---

### Post by kurt18947 on 2015-05-08
> **Bucky Ball said:**
> .deb files only need to be double clicked to install. And you didn't notice that on the download page I linked to there is another download apart from the lpr and cups drivers. The Installer, which does all the installing for you. 

Bottom line: double click the lpr .deb. It will install, probably using SCentre or gdebi. Once done, double click the cups .deb. Install. Reboot, add printer ...

You don't need to use a terminal at all for .deb files, unless you want to install them that way.

At one point some years ago there was a need to use the terminal install. The drivers were 32 bit and wouldn't install on 64 bit systems without 'force-all' being included. I suspect that has since been addressed. One of the beauties of the installer script is that at least some of the 'tricks' are taken care of without user intervention.

I have found one glitch in Brother's installers. There are two currently - 1.x, a link to which is found in the linux printer FAQ section of their web site and 2.x found in different locations. I have found 1.x will not run on Ubuntu Gnome & XFCE 14.04, 2.x runs fine. I wonder if Brother deprecated 1.x without removing it? Or it may be something with my machines. Nice thing (or not depending on your situation) is that 1.x will not install the scanner on multi-function machines. 2.x will unless you decline the scanner license agreement halfway through the install process.

---

### Post by ozark_hillbilly on 2015-05-09
Okay, I went with Bucky Ball's recommendation and double-clicked the .deb files and rebooted.

I went to System Settings and Printer install/add. Attached is the screen shot asking where I want to source the drivers after it looked "here and there" for what is available. Should it have found the local drivers after double-clicking the .deb files prior to the reboot?

Looking at the screenshot which driver source choice is recommended?

If I go to the 'Local Driver' option and select Brother (manufacturer)  the resulting list of printer models does not include my specific model (HL-L2360dw); no HL-L drivers are listed. Should the .deb downloads have installed my model drivers during the .deb install?

Maybe things are not quite as *muddy* as they were.....  :confused:

---

### Post by Bucky Ball on 2015-05-10
> **ozark_hillbilly said:**
> 

If I go to the 'Local Driver' option and select Brother (manufacturer)  the resulting list of printer models does not include my specific model (HL-L2360dw); no HL-L drivers are listed. Should the .deb downloads have installed my model drivers during the .deb install?



Firstly, yes, after installing the .debs the driver for your model should be available in Local Drivers> Brother. Did you look through the entire list of Brother? When you add drivers manually they don't always end up on that list where you would expect. Could be close to the end of the list.

You did install the correct .debs for your model and not another? Just checking. But you say there are no HL- drivers available so guessing not ...

Have you tried in the CUPS interface, open a web browser and put 'localhost:631' in the address bar. Log in with your Ubuntu user and pw.

---

### Post by pdc on 2015-05-10
you might just like to check the drivers were installed ok with ```
dpkg -l | grep hll2360d
``` and you might check your system is seeing your printer with ```
/usr/sbin/lpinfo -v
```

---

### Post by dgtorpedo on 2015-05-10
When I installed my HL2135-W I needed the package [FONT=courier new]apparmor-utils[/FONT] (you can find it in Synaptic).
Before to install my drivers I gave the commands:
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
```

Then downloaded the [FONT=courier new]LPR[/FONT] and [FONT=courier new]CUPSwrapper[/FONT] drivers (I used the generic drivers and in your case you can get the drivers for your printer from here [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128)).

After that:
1) I turned on my printer and connected with the USB cable;
2) I opened a terminal in the foleder where i downloaded the drivers and gave the commands (remember to change the driver names):
[FONT=courier new]sudo dpkg -i --force-all hl2130lpr-2.1.0-1.i386.deb
sudo dpkg -i --force-all cupswrapperHL2130-2.0.4-2.i386.deb[/FONT]
3) I checked the installation with:
[FONT=courier new]dpkg -l | grep Brother[/FONT]

The wifi configuration was very difficult but not impossible.

Please, bear in mind that these steps are for HL2135-W. If you want to try them I'm not sure they will work for you but I see that for many models it's a common practice.

---

### Post by ozark_hillbilly on 2015-05-10
Here's the terminal results:

ed@ed-G41MT-S2PT:~$ dpkg -l | grep hll2360d


ed@ed-G41MT-S2PT:~$ /usr/sbin/lpinfo -v
network lpd
network socket
network ipp
network ipps
network https
serial serial:/dev/ttyS0?baud=115200
network http
network ipp14
network smb
direct parallel:/dev/lp0
direct hp
direct hpfax
network dnssd://Brother%20HL-L2360D%20series._ipp._tcp.local/
network dnssd://Brother%20HL-L2360D%20series._printer._tcp.local/
network lpd://BRN30055C4E8D4D/BINARY_P1
ed@ed-G41MT-S2PT:~$ 


The first command returned no data (or errors).

---

### Post by ozark_hillbilly on 2015-05-10
Bucky Ball,

I selected my specific Brother printer model off the support website and downloaded those. When I mentioned there was no HL-L drivers available I was referring to the Brother models listing that is presented during the printer setup/add function under System Settings. Attached is a screenshot of the CUPS Localhost:631 page.

Ed

---

### Post by Bucky Ball on 2015-05-10
On your screenshot, you can click the highlighted printer or the box with 'Administration' and then 'Modify' and look for the driver. See if it finds the right one (cos the one you got definitely isn't it ;)).

---

### Post by ozark_hillbilly on 2015-05-10
Looked for the correct driver using Admin/Modify but the listing of available printers still does not contain my particular model. I am beginning to believe that the .deb files I downloaded off the Brother support site do not include my specific printer model driver. It is fairly new on the market and perhaps they have not updated the support site yet. Hell, I dunno.....   ](*,)

---

### Post by kurt18947 on 2015-05-10
> **ozark_hillbilly said:**
> Looked for the correct driver using Admin/Modify but the listing of available printers still does not contain my particular model. I am beginning to believe that the .deb files I downloaded off the Brother support site do not include my specific printer model driver. It is fairly new on the market and perhaps they have not updated the support site yet. Hell, I dunno.....   ](*,)

It appears that the correct drivers are available here:

[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2360dw_us&os=128)

It's too bad you're having such a time. I wonder if your machine is having issues like an earlier Brother laser printer - 2270DW? - I don't recall the exact model but Brother issued a patch and later I think revised packages to address installation problems. I wonder why they offer generic LPR & CUPS drivers as well as 'regular' LPR & CUPS drivers.

---

### Post by Bucky Ball on 2015-05-11
> **kurt18947 said:**
> 

It's too bad you're having such a time. I wonder if your machine is having issues like an earlier Brother laser printer - 2270DW? 

I have that printer. Never had an issue. Set one up for a friend. Same. Maybe I got them after the fix-up. Great printer either way.

---

### Post by pdc on 2015-05-11
so ozark; you are getting lots of advice: my tuppenhapennyworth; 

I would just say to you that if your printer is the HL-L2360dw and from ```
dpkg -l | grep hll2360d
``` if you get nothing back, that to me means those drivers are not installed; 

so you need those installed and you either 

1) do the command line stuff I mentioned in post #15; 
2) or try right-clicking on the lpr file; and select "install with software center.." or whatever install options appears.........and then do the same for the cupswrapper file
3) or double-click as I think you have already tried........lpr and then cupswrapper

..................the lpinfo command shows 1) that your computer "sees" the printer and impressively 2) that you are quite happy and proficient at using a terminal whenever you need to use it.

---

### Post by kurt18947 on 2015-05-11
> **Bucky Ball said:**
> I have that printer. Never had an issue. Set one up for a friend. Same. Maybe I got them after the fix-up. Great printer either way.

I'm not certain about the model, I just recall that one Brother laser model generated more than its fair share of traffic here. I presume your paper feed mechanism has behaved itself? I retired an MFC-7820N after less than 7000 copies due to paper feed jams. It was always a failure to feed from the tray. It'd pick up a sheet but 'wouldn't make the turn'. Feeding via the bypass works perfectly. That model had a recall on the paper tray, we got a 'new & improved' paper tray but no better.

---

### Post by Bucky Ball on 2015-05-11
No, must have been a different model to mine. No paper tray problem. No problems at all (touch wood!). ;)

HL-2270DW

---

### Post by ozark_hillbilly on 2015-05-11
@ PDC

I decided to try your suggestion of using 'Software Center' and install the driver files. When attempting to install the first .deb file/package I got an error saying "the package was of bad quality."  ???
Attached are the screenshots giving the warning information. Should I ignore the warning and continue with the install?

This is getting screwier w/ each passing day..... [-o<

---

### Post by Bucky Ball on 2015-05-11
That is mighty odd. Just wondering if the driver version is not compatible with the OS release ... :-k

* Scratch that: the release date of the driver is 04/02/2015, so pretty new, but if you're on 15.04 ... there has been no driver released since 15.04 was ...

---

### Post by ozark_hillbilly on 2015-05-12
@ Bucky Ball

I stay with major releases and still have 14.04 Ubuntu....

---

### Post by pdc on 2015-05-12
Hi ozark; ............re the rpm and alien comments .......... as you know, alien converts rpm packages to deb packages. I had heard that in Japan that rpm had become the established format in the early days...........and has stayed..........so maybe...just maybe..these packages are written as rpm and all of them are converted to deb with alien; Epson and Brother and Canon all have their home base in Japan. Earlier drivers from Epson used to be rpm only in a number of cases. 

______________

if software centre baulks, can I suggest that as you are fluent on the terminal, that you go back to post #15 and try the commands there; just paste them in one and one and see how it all goes; the first command (cd Downloads) is needed to get you inside your Downloads directory

---

### Post by ozark_hillbilly on 2015-05-14
@pdc

I can install the drivers w/ Software Center it just asks if I want to continue with the installation despite the Warning Message about the bad quality of the package. I am unsure if it wise or not to continue w/ install.

---

### Post by Bucky Ball on 2015-05-14
That could be a quirk of SCentre as the app is not officially tested and approved. Try with straight gdebi. Install that from the SCentre, but you probably already have it, right click on the .deb file and 'open with'. Choose 'gdebi'. Same complaint?

---

### Post by ozark_hillbilly on 2015-05-14
@ Bucky Ball

Shazaaam!!

Going the route of installing gdebi and right clicking on the .deb files and using gdebi seems to have been the trick!! No errors/warnings....

Terminal output:

ed@ed-G41MT-S2PT:~$ dpkg -l | grep Brother
ii  hll2360dcupswrapper                                   3.2.0-1                                             i386         Brother HL-L2360D CUPS wrapper driver
ii  hll2360dlpr                                           3.2.0-1                                             i386         Brother HL-L2360D LPR driver
ii  printer-driver-ptouch                                 1.3-8                                               i386         printer driver Brother P-touch label printers
ed@ed-G41MT-S2PT:~$ 

See attached for browser- localhost:631 output....

If everything looks OK to you fellas then I think we can close this thread. Is there anything else I need to do "setup-wise?"

Thanks everyone!!!!!

Ed

---

### Post by pdc on 2015-05-14
well Ed; that was easy wasn't it? .............. gdebi 1; software center 0 

glad all is working; enjoy

---

### Post by ozark_hillbilly on 2015-05-15
@ pdc

This driver install is typical for the likes of me. If something can get screwed up or not act as expected I seem to find how to make that happen. :lolflag:

Thread is resolved.

---

### Post by Bucky Ball on 2015-05-15
Excellent news. We got there. Congratulations on your persistence. ;)

If everything is printing correctly, then you're good to go. Enjoy!

---

