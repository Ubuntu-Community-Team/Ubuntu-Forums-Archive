---
title: "Guide to Toshiba Satellite A135-S7403"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by styyle14 on 2008-02-17
[SIZE=4]**Guide to Toshiba Satellite A135-S7403**[/SIZE]

This is meant to be a guide covering my setup of my Toshiba Satellite A135-S403 with Ubuntu Gutsy 7.10 32-bit.  I'm not sure if these patches also work on the 64-bit system.  I purchased this laptop from Best Buy from the day after Thanksgiving sale.  It came bundled with the Canon PIXMA MP210.  The main points to be covered in this guide:

-Setup Graphics Card
-Setup Wireless Internet
-Setup Audio (includes functionality for headphones/speakers)
-Setup Printer that came bundled with laptop

This guide assumes basic understanding of how to use programs in Ubuntu, as well as basic terminal commands.  I will try to include all necessary code.

[SIZE=3]**Graphics Card:**[/SIZE]
After the initial setup of Ubuntu, I didn't have basic 3D graphics capabilities (necessary for 3D games and Compiz). To fix this problem, I found that xorg.conf needed to be changed in order to use the correct driver for my graphics card.  Running "lspci" in the terminal defined my graphics card as "00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller".  To choose the correct driver, I first tried simply editing it under: System>Administration>Screens and Graphics.  This resulted in a complete failure of Ubuntu by disabling all all visual capabilities.  After some research, I found the following solution:
To edit xorg.conf run this in terminal:

> sudo gedit /etc/X11/xorg.conf

This should display the file for editing.  To fix the graphics card problem, I changed the graphics card driver manually by editing this section of the file:

> Section "Device"
    Identifier    "Generic Video Card"
    Driver        "Vesa"
    BusID        "PCI:0:2:0"

to read:

> Section "Device"
    Identifier    "Generic Video Card"
    Driver        "i810"
    BusID        "PCI:0:2:0"

After restarting my computer, I had full 3D graphics capabilities!!!

[SIZE=3]**Wireless Internet:**[/SIZE]
The internal wireless card that comes built into the laptop is the Atheros AR5007EG.  It is incorrectly identified by "lspci" as "AR5006". In order to connect to the wireless internet router located at my house, I did lots of work to find the solution to having my wireless card be run under the proper driver.  Many sites noted the use of Ndiswrapper.  I personally never was able to successfully have this program work on my computer.  After some research along different lines, I encountered a solution that seems to work better.  Madwifi seems to be the best solution for this wireless card as of early 2008.  Updates and new information about my solution can be found at this website:
[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

To apply this fix I did the following:
Downloaded these 2 files and placed them in my home folder:
[http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz](http://snapshots.madwifi.org/madwifi-ng/madwifi-ng-r2756-20071018.tar.gz)
[http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw](http://madwifi.org/attachment/ticket/1679/madwifi-ng-0933.ar2425.20071130.i386.patch?format=raw)

I then used Nautilus' context menu to extract the .tar.gz file to my home folder.  I then copied the patch file into the newly extracted folder.  As described on the site I listed above, I then patched the source code (what was in the .tar.gz file). The code I used to patch it was:

> cd madwifi-ng-r2756-20071018/
patch -p0 < madwifi-ng-0933.ar2425.20071130.i386.patch

The output should be several (about 10 or less lines).  Then I ran the commands:

> make
sudo make install

Don't run "make" as root, but be sure to do so for "make install".  If this doesn't work for you, you may need to run "sudo apt-get install build-essentials" to get the proper capabilities.

If all of that went successfully, you then need blacklist the default Ubuntu restricted driver.  Go to System>Administration>Restricted Drivers Manager.  Uncheck: Atheros Harware Access Layer (HAL).  To blacklist it so that it doesn't load anymore, run this command in the terminal:

> sudo gedit /etc/modprobe.d/blacklist

Simply add a new line to the bottom that reads: "blacklist ath_pci".  Restart your laptop.  If everything went correctly, run:

> sudo modprobe ath_pci

The effects should be seen almost immediately (look to the upper right of your screen at the network manager applet, click on it and you should see a wireless internet section).  I tried to get wicid to accept this fix, yet it was unable to get past certain steps of talking with my router.  To ensure that this fix runs every time your computer starts up, edit your modules file by the command:

> sudo gedit /etc/modules

Simply add a new line to the bottom that says "ath_pci"

[SIZE=3]**Audio:**[/SIZE]
As I, and hopefully you, have noticed, the laptop does not have the ability to use the laptops speakers after the initial setup.  The device is defined by "lspci" as "00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)".  To fix this problem, open your alsa-base file through the command:

> sudo gedit /etc/modprobe.d/alsa-base

To add audio functionality, add this line "options snd-hda-intel model=lenovo" to the bottom of the file (or anywhere within the file, as long as it is its own line).  Restart your computer and you should be able to hear and control the built in speakers on your laptop.  Many other guides for this or similar laptops cite using the code "options snd-hda-intel model=3stack".  This works for you built in speakers, but if you ever intend to hook headphones up to your laptop, the internal speaker will play along with your headphones.  To have your laptop detect your headphones and mute the internal speakers when the headphone jack is inserted, be sure that "3stack" is instead "lenovo".

[SIZE=3]**Printer - Canon PIXMA MP210:**[/SIZE]
When you first try to get the printer that came bundled with the laptop to work, you may notice something funny: it didn't come with the proper cord to hook it up to your laptop.  You have to go and buy one for it.  The type of chord you want to get is a "USB to parallel printer cable".  These can be found at almost all general stores.  I got mine from Walgreens for 11$, I wouldn't recommend paying more than 20$ for the cord. The cord plugs into the back of the printer in a kind of hard to find spot, but its back there.  Ubuntu comes with a built in printer manager called CUPS.  Your printer information and queue can be found through firefox at this address "http://localhost:631/jobs/".  To get your specific printer to work with Ubuntu, you need the proper Linux driver.  I couldn't find one at the US canon website, but the Australian has the one you are looking for.  Go to the url: 

[http://canon.com.au/drivers/default.aspx](http://canon.com.au/drivers/default.aspx)

Choose All-in-One Printers>All-in-One Printers>PIXMA 210 - Everyday, then choose driver downloads,     
IJ Printer Driver Ver. 2.80 for Linux(debian Package for the MP210 series), then check the box at the bottom and download the driver.
Open the driver with gdebi and install it.  Restart your laptop and plug in the printer.  You should now be able to see it in "http://localhost:631/jobs/".  To use its scanner function, use Gimp and choose File>Acquire>ScanGear MP.
[B]
Hope this helps you with you linux experience on this laptop,
Styyle14[/B]

---

### Post by K.Mandla on 2008-02-19
Moved to Hardware and Laptops.

Edit: Thread title edited at the request of the OPer.

---

### Post by netgooroo on 2008-05-13
Thanks bunches for this...  I was wondering why my sound wasn't working right. Now I'm good to go..  :)

---

