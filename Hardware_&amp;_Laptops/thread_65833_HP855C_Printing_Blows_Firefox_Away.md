---
title: "HP855C: Printing Blows Firefox Away"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by blair on 2005-09-15
I just installed Ubuntu 5.04 and am very happy with it. System specs are P733MHz, 512MB, Integrated i810 video. System is up to date w/ latest patches to the best of my knowledge.

Installed first printer, an HP855C. Ubuntu auto-detects and recommends the hpijs printer driver which is the correct and recommended driver. 

Test text-only page from gEdit printed fine. Printed test page from printer properties and printer queue hung. Had to hit resume job a few times and then it printed fine. I can print a web page from the Ubuntu forum and I can print PDFs, but when I went to print [www.cnn.com](www.cnn.com), several bad things happened:

- job does not print
- job does not show up in print queue
- firefox blows away. just a complete and immediate shutdown. 

Hints on what is going wrong and how to troubleshoot would be appreciated. Are there logs that can be viewed? 

(Suggestions to HP and Ubuntu dev teams: The hpijs driver is used for a significant number of HP printers and HP has significant market share in the consumer printing space. It should work out of the box, and for me it did not. In all fairness, this could be a Firefox problem, but Firefox is the default Ubuntu browser, so I would expect it to work out of the box as well)

thanks.

---

### Post by StonePiano on 2005-09-19
Hi Blair,

Both Firefox and Thunderbird printing are affected by the theme?!?!?!

Click System > Preferences > Theme.
Change your theme to 'Simple'
Then print from Firefox.

If it works, please let me know.

Then you can experiment with other themes.  You may even be able to change back to your chosen theme and it still work, as the theme change seems to straighten out some screwed up configuration.

StonePiano

---

### Post by buldir on 2005-09-23
Yep.  I can confirm this with the mozilla.org tarball 1.0.6 Firefox and the "Glider" theme.  I switched themes...no more FF crashes when printing.

---

### Post by blair on 2005-10-11
Thanks. That helped but not much. I can print simple ASCII using gedit, but everything else chokes. I was able to eke out one web page with graphics and no pictures (e.g. a Ubuntu forum page), but nothing from open office and nothing from a web page with pictures. I get the printing dialog popup,  a progress bar, the dialog closes and the job just sits there in the print queue. Same result if I print a test page from within the print spooler dialog. 

In particular, I can still *consistently* blow away Firefox by trying to print [www.cnn.com](www.cnn.com). If I then check the queue, it is empty. I also tried printing washingtonpost.com and the job just sat in the queue. 

Question: Should it make any difference whether I use a USB cable or a parallel cable? I've read a lot of issues around USB support. Don't think that is an issue here, but have to ask.

---

### Post by blair on 2005-10-12
Status update: After hunting these forums some more, it occurred to me I may be missing some packages. I started pokling around Synaptic and I found the following package description for hpijs in Synaptic:

HP Linux Printing and Imaging - gs IJS driver (hpijs)
This package contains the hpijs binary which provides Ghostscript
with a IJS driver for most inkjet printers and some LaserJet printers
manufactured by HP.

It includes the so-called rss patch, to use pure black ink instead
of composite black in printers that don't do color map conversion
in firmware.

Users of USB and JetDirect HP printers are advised to also install the
hplip package, and use the hp: CUPS backend to send data to the printer.
Selecting any hpijs ppd in CUPS will use hpijs automatically.

Users of parallel-port HP printers are advised to install the hpoj
package, and use it to send the hpijs output to the printer.

HPIJS is meant to be used through the foomatic system (see the
foomatic-filters package).

 Homepage: [http://hpinkjet.sourceforge.net](http://hpinkjet.sourceforge.net)

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

Several of the packages mentioned above were not installed on my machine.  There was of course no way of knowing this and no obvious error message about missing packages. 

I installed all of the packages above and tried again. I deleted the printer and then re-added the printer. Things appear to be much more stable now. I can consistently print from gedit and OpenOffice word. I can also print a test page from within the printer manager window. Still having problems printing from Firefox. Printer goes into pause mode almost immediately, indicating print job is hung or just blows away Firefox completely.

---

### Post by blair on 2005-10-17
Update: After beating my head against the wall on this, and searching high and low for advice, I gave up on Ubuntu and tried PCLinux. Same problem exists in Firefox. Repeatable Firefox crash on print when printing certain web pages, although test pages, OO word processor and simple test pages print fine.

Not only on the HP 855C using the hpijs driver, but on an old HP4L using the ljet4 driver. Thus identical problems 2 different printers, 2 different drivers, two different distros. In fact Ubuntu used Gnome and PC Linux uses KDE, so desktop differences exist as well. 

The commonality here is mozilla engine and of course Firefox itself. 

I also had the same problems using Galeon. I intend to try Epiphany on Ubuntu to see if I have any better luck, but like Galeon, it too requires the Mozilla engine underneath, so I'm not optimistic. But I will try it just to complete the experiment. 

I had no problems using Konqueror on PC Linux, which is KDE-based, so perhaps using Konqueror on Kubuntu may work. I also installed Opera on PC Linux and had no problems at all, with either printer. I intend to install Opera on Ubuntu as well and see what happens. Will let you know what happens. 

Thanks for the assistance to date.

---

### Post by buldir on 2005-10-18
I admire your persistence...I would have bought a different printer! I think the Ubuntu forum mods should dish out points for users who answer their own threads! ;) Seriously, have you tried just the hplip drivers? I could be wrong, but I have read in some threads of people creating more problems having multiple HP driver packages installed. On another topic, I tried Opera and was pretty impressed.

---

### Post by blair on 2005-10-18
You are correct that that is an issue to be aware of. I had already checked out the HPLIP project site on sourceforge.net and they make it clear that for parallel port printers, HPOJ and other packages are incompatible. However HPOJ has been subsumed/obsoleted by HPLIP, which is now pretty much a universal driver for HP printers. Also I am using a USB connection for the printer. I can't get any printing at all on a parallel port connection. For the record, I only have the hpij package installed; hpoj is not currently installed so I know that is not the issue.

As an aside, I forgot to mention that I also tried the cdj850 driver which according to linuxprinting.org is another supported driver for this printer. Same problems. Either refusal to print/printer goes immediately into paused mode, or firefox crash.

---

### Post by blair on 2005-10-18
Epiphany Test Results: Just installed the epiphany and epiphany-extensions packages and tried printing using that browser. 

First test print job on cnn.com: Immediate crash. At least I got an error message here. A lot better than Firefox that just silently goes poof. 

Second test print job on cnn.com: Job just sits in the printer queue. Weird because printer does not go into paused/error mode; It just sits there saying "printing". No error message this time. 

Bye-bye, Epiphany. On to Opera...

---

### Post by David Haas on 2005-10-18
blair--I'm curious to know whether you've tried the other drivers (PPD file) for your HP printer in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. The 3 I see here are:
HP-DeskJet_855C-cdj850.ppd.gz
HP-DeskJet_855C-hpijs.ppd.gz
HP-DeskJet_855C-pcl3.ppd.gz

Sometimes one works better than the others.

David

---

### Post by blair on 2005-10-18
PROBLEM SOLVED !!!!


I dug through dozens of Q&A's on linuxquestions.org and finally found a solution that worked for me (HP855C, USB, hpijs driver, Ubuntu 5.04) thanks to Harishankar (Search that site for for HP PSC 1310 to find the thread):

1. Power printer off 

2. Remove printer from print manager console remove any junk you may have created so far and start fresh

3. Open root terminal. Restart CUPS using /etc/init.d/cupsys restart command to flush all printer settings.

4. Add printer using the print manager Add Printer wizard. Complete and close wizard.

5. Open /etc/cups/printers.conf as root and make the following change:

Original Setting: DeviceURI usb:/</printer manufacturer, e.g. HP>/<Printer name, e.g. HP 850> 

New Setting: DeviceURI usb:/dev/usb/lp0

6. Save and close printers.conf file.

7. As root, restart CUPS using /etc/init.d/cupsys restart command so it reinitializes using the new DeviceURI setting.

8. Power on printer

9. Print


I now have full print access in Firefox, no more crashes, no more print jobs that just sit in the spooler, etc. Other apps printing fine as well. 

I also installed an HP 722C via USB, made the same DeviceURI edit in printers.conf and it too is printing like a champ in all apps. 

I also was having a similar problem with an HP4L on a parallel port. I will move on to that one now


For the record, I did try the cdj850 driver and gimp-print driver prior to finding this solution (these are the recommended drivers on linuxprinting.org site for this printer) and it had no effect, i.e. no improvement on the situation. 

Thanks for everyone's assistance. Hopefully I will be able to reciprocate or help the next person to come along.

---

### Post by blair on 2005-11-27
Status Update: Experimenting with PC Linux OS, I had a similar printing problem on the HP Deskjet 855C but found a different solution: Forcing the print mode to a specific print mode all the time, vice letting the app control it, helped. 

In Ubuntu: Install the printer as normal. After install, open the printer control panel. Select the printer. Right click > properties. In Printer properties dialog, select Advanced tab. In Resolution pick list, change from "Controlled by printout mode" to one of the other modes, e.g .300 dpi. This solved the problem. 

In PCLinux: Open your browser to localhost:631. Remove your printer and re-add in cups. Once added, configure the printer from cups and select a specific print mode, e.g. 300dpi, draft grayscale. Try the different modes supported on your printer and you may fine one that works. Note that the opportunity to define the default print mode like this is not exposed when going into the printer manager via the Ubuntu desktop; I have only seen this particular printer setting control in the cups admin UI. 

Note also that I never got this printer to print at all with a parallel cable and this solution only worked when I switched to a USB cable.

Note also that after a few days, printing mysteriously broke again. Still under investigation.

---

### Post by blair on 2005-12-04
Status update: My solution described in a previous post worked, but not for long. The situation again became unstable. More nights up till 2 AM..... I believe I am finally in good shape here as a result of recent config changes. 

Here's the latest. It is a long story I will try to condense:

- Printer is an HP855C. 
- Linuxprinting.org says that hpij is the optimal driver and it *should* work perfectly. 
- Carefully reviewed hpij package description in Synaptic
- hpijs package indicates users of cups are also advised to install hplip, use HP cups backend, and that hpijs is meant to be used through foomatic.
- Searched Synaptic again and found that hplip and some foomatic packages were not installed. Installed them. 
- Reviewed hplip package description in Synaptic. It mentions the package contains GUI components of the hplip system including hp-toolbox. 
- Did research on hp-toolbox and found it is a GUI-based admin console for HP printers. 
- After installing hplip, ran hp-toolbox in a shell and the GUI tool popped up. I recieved an error message due to undetected printers. I never got my printer to display in the toolbox even after installing in cups and everything working fine. I am speculating that this GUI tool may only be useful for USB printers, not parallel port printers. 
- HP Toolbox error dialog displayed when GUI first opens indicates it will only detect printers instaleld with the hp cups backend. This is one of several references I came across to "installing an hp cups backend". I was never able to find specific instructions and am not sure whether specific configuration steps are required or it happens by magic when the hplip package is installed. 

This is where things started to get really interesting.....

- Each of these packages drops some README docs in their own  /usr/share/doc folder, eg. /usr/share/doc/hpij, /usr/share/doc/hplip, /usr/share/doc/hplip-basic, etc. 

- There are 2 READMEs of note in each folder, one authored by HP and one authored by a Debian developer. The Debian readme file is buried inside a compressed Debian gzip archive, e.g. README.Debian.gz. You need to extract the README.Debian file from the gz file. 

- Both READMEs were full of installation tips and gotchas. Both also contained several useful troubleshooting tips. It is important to appreciate that this info comes from as close to an authoritative source as you are going to find, unlike on forums like these where folks try to help and mean well, but "YMMV" is a given. 

- Examples of nontrivial pieces of information I found include: 1) hplip does not officially support USB ports;  2) the proper PPD is provided in the hplip-PPDs package listed under HP (HPLIP);  3) the hplip startup script must be executed before the cups startup script at bootup time. There was other useful info in these files as well. (Note that Ubuntu uses cupsys, not cups).

- You could see how this would be useful if for example, you have a printer connected via USB, are making assumptions about Ubuntu correctly guessing which PPD file to use; and have no idea whether cupsys or hplip is the first to start at when your PC boots up. The key point is that you wouldn't have even known these were issues you needed to care about if you hadn't found and carefully read this treasure trove of docs. 

- I switched my printer from USB to parallel, theoretically eliminating one problem. 

- I removed and reinstalled the printer using the cups web admin UI (theoretically this also could have been accomplished via the Gnome add printer wizard. Note in particular that when I walked through the install wizard and got to the 'select manufacturer' step, not only was there a manufacturer called 'HP', but also one called 'HP (HPLIP). This would have meant nothing had I not read the comment in the readme file about where to find the "proper PPDs". So I selected the HP/HPLIP manufacturer, not the HP manufacturer. The next step in the wizard is to select the model and driver. Note that the driver options had I selected HP were different than the options that were available to me when I selected HP/HPLIP. I selected the driver for my printer: the 855C

- The cupsys/hplip startup sequence was trickier to solve as I'm a newbie. It took some digging to find the key data and then to interpret it correctly. Basically, the key location you care about is the /etc/rc2.d folder. This is where your init scripts are located. Google on init scripts in order to learn about more this area of your system. 

- In the /etc/rc2.d folder there were the following 2 files of interest: S19cupsys and S19hplip. In brief S=startup script, 19 means start these after startup scripts 1 to 18 and before startup scripts 20 to whatever. The problem is that there are 2 number 19 scripts. Alphabetical order determines which gets loaded first. Thus, the cupsys script loads before the hplip script. Why do you care? Because the HP installation notes in the HP readme file in /usr/share/docs/hplip had an installation caveat that says "the hplip script must start before the cupsys script". Thus this current configuration is clearly not OK. 

- as an aside, I opened a defect with both Ubuntu and Debian development teams so they would be aware of this and hopefully fix it in a future release. 

- There were no S18xyz init scripts in the /etc/rc2.d folder, so I simply renamed S19hplip to S18hplip. So since S18 scripts start before S19 scripts, I have now ensured that hplip loads before cupsys loads. (I could just have easily renamed S19cupsys to S20cupsys and accomplished the same result). 

- A word of caution here: Now that hplip is an installed package, any updates could easily roll back my tweak to the init script and break my printing. If my printing breaks mysteriously, I know I'll have to check the rc2.d folder and see if a S19hplip file mysteriously has reappeared and if so, whack it. 

- Continuing on, I then restarted the machine (it makes me feel better than just restarting services; that just shows you how years of using Windows have made me distrustful of an OS's ability to correctly make a change...).

- End result: Everything prints just fine now with one exception: Firefox still blows away when printing to *selected* web sites, principally CNN.com. Two key points which took a while to dawn on me) are  

- Conclusion 1:  Firefox prints just fine on most sites. Therefore there clearly is no problem with the printer or with the browser's ability to send print jobs to the printer.  The fact that the printing problem is limited to certain sites means it is a site-specific problem, not a generic printing problem. If you've gotten this far, with other apps printing and firefox printing OK on some sites, stop thinking something is wrong with your printer; Focus your attention on the browser itself.   

- Conclusion 2:  When Firefox *does* blow away, nothing is showing up in the printer queue.  If the job got to the queue and then just sat there, I would know there was a printer or print manager problem. But Firefox is blowing away without anything ever making it to the print queue. Thus this is not a printer problem at all; it is simply Firefox blowing up when it tries to create a printable blob of data containing a particular type (or types) of data, and blowing up before it has created a complete blob of data ready to be passed to the print manager. Since Firefox prints fine on certain web sites, this again points to Firefox simply being unable to handle certain types of web content; thus a Firefox problem, not a print problem per se. This may very well be a result of IE specific tags on these web pages and Firefox not handling them when printing.

So I now consider my "printing problem" as solved as it is going to get and will now focus on seeing if I can't improve Firefox's printing situation. I have installed the MS TT Fonts and tried some other things to no avail. It may simply not get any better under I upgrade to a more recent version of Firefox or until CNN and other sites start using W3C compliant HTML tags. I won't hold my breath on the latter....

hopefully this info helps. thanks again to the folks who offered suggestions and advice during this little adventure.

---

### Post by blair on 2005-12-07
The following is the response I received to the bug I opened with Debian:

"...I have verified that the Debian packages in unstable are NOT
subject to the above bug, as cupsys installs at sequence 20 in Debian.

Also, I have verified that the cupsys/hplip load order is relatively
unimportant in the current packages (as it really should be, hplip reloads
cups when it is started in Debian). You could even have done this yourself. Just stop both services, start CUPS, start hplip, and try printing.  All badness you will get is a message in the CUPS logs that can be ignored...."

The implication here is that even though Ubuntu was by default  installing both cupsys and hplip as S19 in rc2.d, and cupsys was loading first, that hplip appears to be actually restarting cupsys as part of the hplip startup process, effectively causing cupsys to end up being loaded after hplip after all.

---

### Post by blair on 2005-12-07
The following is the response I received to the bug I opened with Debian:

"...I have verified that the Debian packages in unstable are NOT
subject to the above bug, as cupsys installs at sequence 20 in Debian.

Also, I have verified that the cupsys/hplip load order is relatively
unimportant in the current packages (as it really should be, hplip reloads
cups when it is started in Debian). You could even have done this yourself. Just stop both services, start CUPS, start hplip, and try printing.  All badness you will get is a message in the CUPS logs that can be ignored...."

The implication here is that even though Ubuntu was by default  installing both cupsys and hplip as S19 in rc2.d, and cupsys was loading first, that hplip appears to be actually restarting cupsys as part of the hplip startup process, effectively causing cupsys to end up being loaded after hplip after all.

---

### Post by mctavish on 2005-12-08
Try disabling java in the firefox preferences. That solved my firefox-print-crash problem.

---

### Post by blair on 2006-06-09
Update: Ubuntu has continued to be either a non-starte or completely unreliable from a printing perspective.  This is on several different PCs, 3 different printers, USB and parallel. I have been experimenting with other distros and found Mepis to work flawlessly. I had hoped Ubuntu 6.06 would improve over 5.10 but this did not happen. 

In frustration I closely compared Mepis to Ubuntu and found several differences, mostly in terms of the config files used by cups.  To make a long story short, the silver bullet is literally to blow away the Ubuntu /etc/cups directory and replace it with the contents of the Mepis /etc/cups directory. Ubuntu now prints like a charm because cups is being properly initialized. Bottom line: Ubuntu's cups config files are junk. 

Specific steps required are:

1. As described in /usr/share/doc/cupsys/README.Debian file, you need to add the user 'cupsys' to the group 'shadow' using this command: sudo adduser cupsys shadow. 

2. If you have not already done so, you need to create a full root account using this command: sudo passwd root.  When prompted, enter your current password (the first user account created on the machine), then the new password for the root account. 

3. Get yourself a copy of Mepis. As root, tar up Mepis /etc/cups directory including all subdirectories, and preserving all paths. On UBuntu, as root, extract the files from the tar and extract to the Ubuntu /etc/cups directory, overwriting all the contents. 

4. Re-boot your machine to restart everything, or simply restart cups itself: 'sudo /etc/init.d/cupsys stop', and then 'sudo /etc/init.d/cupsys start'

You can now open the CUPS web admin interface ([http://localhost:631)](http://localhost:631)), add a printer, authenticate as root using your root password when prompted by CUPS, and install the printer.

---

