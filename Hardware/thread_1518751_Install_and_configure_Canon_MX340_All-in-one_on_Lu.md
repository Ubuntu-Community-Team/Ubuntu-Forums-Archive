---
title: "Install and configure Canon MX340 All-in-one on Lucid 64 bit"
date: 2010-06-27
forum: Hardware
---

### Post by Cypher2 on 2010-06-27
Hello everyone!

Thought I'd share my success in installing and configuring my new MX340 printer on Lucid 64 bit.

As we all know or heard of, Canon does support linux .deb and .rpm driver packages but only for the 32 bit platforms.

I hearby declare that any thread claiming that the 32 bit modules installed on a 64 bit machine do not work is most probably a mishap on behalf of the user who tried installing without any clue of what they were doing.

After this, you will have full wireless functionnality and scanning capabilities :)

So here we go:

1 - Open you printer box, unwrap and set it up wherever you desire as long as it's in range of your network router/hub or wireless router/modem. Plug the power cord in and light it up.

2 - Go to this link 

[http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux)

and download the MX340 Series Printer drivers and ScanGear MP debian packages. You will notice that they are provided as tar.gz archives - once loaded, extract them to a working directory of your choice.

You will notice that upon extraction, the folder hierarchy is as follows for both archives: 

'FOLDER NAME' > packages|resources|install.sh

We will be working within the "packages" folder as it is the one containing the deb archives.

3 - Back to the printer: it should now be ON, and ready to be configured.

On the printer's button and configuration panel, press the MENU key 3 times until it displays the DEVICE SETTINGS menu. From now on, use the left and right arrows under the LCD display to navigate through all sub-menus that will follow.

3A - Press the right arrow once to select sub-menu LAN SETTINGS, press OK.

WLAN active/inactive - Press OK, switch status to active with arrow keys, Press OK.

You will now automatically exit back to the following sub-menu: WIRELESS LAN SETUP, press OK.

You are now on EASY SETUP option, press OK.

Your MX340 will now begin scanning for WLAN access points. It should show the strongest signal first, which would normally correspond to you modem/router. If not, use the arrows to cycle through the access point name entries until you find the desired name, press OK, confirm selection by pressing OK again.

If your router/modem is encrypted with a password (which it normally should), the printer will ask for it - enter it via the number input panel on the right, press OK. The LCD should Display "CONNECTING..." as a status message and it should not take more than 5 seconds to do so. Press OK to confirm status "CONNECTED".

3B - You now exit to sub-menu PRINT LAN DETAILS, skip it with right arrow to sub-menu OTHER SETTINGS, press OK.

You will now be on sub-sub-menu entry SET PRINTER NAME, Press OK.
I have set mine to simply show MX340, you can do so with the number entry pad as described earlier for the password entry, Press OK.

You are now on IPv4/V6 sub-sub-menu, Press OK. Select IPv4 with arrow buttons, press OK and confirm the AUTO SETUP option and interruption message by pressing OK again. Keep IPsec setting inactive by pressing OK. The status message should show "SETTING..."

You are now on WSD SETTING sub-sub-menu, press right arrow button to skip to ENTER SERVICE NAME, press OK. You can modify the service name to be shorter by erasing the hardware adress that follows the whole string for the service name to simply become Canon MX340 (the hardware address and hexadecimal tag will still be visible under the printer settings option upon setup in Ubuntu. Press OK to confirm entry.

You are now on LPR SERV. Advertising sub-sub-menu, press OK to enter and switch to ON, press OK to confirm.

You can now go back to the main LCD status menu by pressing the BACK button until reaching it.

YOUR PRINTER IS NOW FULLY CONFIGURED TO BE DETECTED BY UBUNTU VIA THE PRINTER SETTINGS MANAGER.

4 - Now, go back to your machine and enter the "packages" folder for the CNIJFILTER archive you've extracted earlier. Open a terminal window in that folder via right click menu (if you have the scripts already downloaded and set up in Nautilus, or you can simply use the good old "cd" command as follows:

"cd 'FOLDER NAME'/packages"

You can verify that you are indeed in the desired folder by the pressing "ls" and reading out the contents of the folder via the terminal.

4A - Now that we are in the desired folder, you will enter this command as follows and provide your superuser password when prompted by the terminal:

"sudo dpkg -i --force-all *.deb"

Do not worry about any error message that the terminal would display as it mostly refers to the architecture of the package being i386 and not amd64 - the packages will still extract and install perfectly fine.

THE FILTER AND DRIVER MODULES FOR THE MX 340 ARE NOW INSTALLED.

4B - Repeat step 4A, but this time you will use the "packages folder contained with the SCANGEARMP folder you've previously extracted.

THE SCANGEARMP SCANNING MODULE/APPLICATION IS NOW INSTALLED. (You can find it within /usr/bin/ as scangearmp).

5 - Close all your open windows and head to the "Printing" menu from System > Administration.

Press the ADD button (marked with a green cross icon), the "New Printer" window should now appear.

Press on the "[+] Network Printer" sub-menu, then press "Find Nework Printer", press the "Find and wait for the manager to finish scanning.

You should now see two entries for the MX340, the first one being the default printer module hardware address with the hexadecimal hardware ID, and the second the LPD entry with the printer's IP adress using DNS as backend to access the printer.

Click on the second entry (DNS with IP adress version) and press the forward button. The "Searching for drivers" window should appear and then pass directly to the "Describe Printer" dialog. 

If it did go as described, it means that the drivers were indeed successfully integrated to Ubuntu and that the system picked them up and configured the printer to use them.

Name you printer as you wish for it to appear within your system's dialogs. Press the "Apply" button to finalize.

If you wish, you can print the Ubuntu test page to make sure it does receive jobs.

The icon for the printer must not show any error status exclamation emblem ( /!\ ).

To access your printer via other remote systems and be able to print, press "Server" in the main window menu bar and go to "Settings". Check all first three options and apply, The printer should show up on the network browser of other machines and their respective printing dialogs within 30 seconds to a minute delay.

YOUR MX340 IS NOW READY TO PRINT ANY DOCUMENT FROM ANY LOCATION WITHIN YOUR NETWORK.

6 - We will now add a launcher/menu entry to be able to scan with the MX340 as the SANE library does not seem to recognize the scanner hardware for this model as of yet.

On your desktop, right-click and select "Create Launcher..."

Fill labels as follows:
_____________________________________________________________
Name: ScanGear MP
Command: scangearmp
Comment: Canon MP/MX Series scanning utility
_____________________________________________________________

You can set the scanner.svg icon to be used by simply clicking on the springy launcher icon and browsing to /usr/share/icons/gnome/scalable/devices and selecting scanner.svg Press OK when done, a launcher should now appear on your desktop.

If you prefer having a normal menu entry for it, you can set it up by right-clicking on the Ubuntu Applications panel icon and selecting "Edit Menus", navigate to "Graphics". Press the "New Item" button and follow the steps  previously described to create a custom launcher.


ENJOY!

---

### Post by nullvariable on 2010-08-09
This **worked great for me** but sometimes it just sits in the linux printer queue for an hour and suddenly prints. Any suggestions?

---

### Post by CasPol on 2010-09-22
Found the drivers, but wrong architecture, anyone know if amd46 is avaialble anywhere?

---

### Post by tvigouroux on 2010-10-01
> **CasPol said:**
> Found the drivers, but wrong architecture, anyone know if amd46 is avaialble anywhere?

There aren't drivers for amd64, but if you follow Cypher2's procedure it works with the i386 drivers.

---

### Post by tora201 on 2010-10-04
Nice post. Thanks. Works with mx-350 in 10.10 64 as well. Actually I had done this a while back but forgotten how. Alzheimer's.

---

### Post by CasPol on 2010-10-26
Tried Cypher2 solution, does not work at all.

Any other suggestions?

---

### Post by CasPol on 2010-10-26
After: sudo dpkg -i --force-all *.deb

I get: 

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

I have :[COLOR="DarkRed"] cnijfilter-mx340series-3.30-1-i386-deb.tar.gz[/COLOR] in my "downloads folder".

Can someone please explain me step by step what to do, I do not understan the instructions from Cypher2

THNX



no idea what to do next.

---

### Post by Cypher2 on 2010-12-06
you need to extract the contents and the run the dpkg command within each subfolder containing a .deb archive.

It was clearly specified in the how to... follow the steps!

---

### Post by tybrownintn on 2011-02-12
I had a great deal of trouble following these directions.  Please talk slowly for the differently abled.

First off, I could not even figure out how to use the number pad to enter letters, so I was kinda stuck.  

Secondly, I had already set this printer up on a wireless network under Windows 7.  I am attempting to get it to work under Ubuntu because that is the main sticking point for switching over entirely.  I had not realized how difficult getting printers to work would be.

My printer, as I said, is on the network. I have installed the drivers successfully.  (I just double clicked on the deb packages but I suppose some like using the terminal.)  

But as I follow the steps, what I see on the led differs from the steps as outlined.  

I navigated on the printer to Print LAN settings, which I did do.  Hit the right arrow and got to "other settings".
I hit OK and get SET PRINTER NAME.  Since I am rather dense, I have no idea how to use the number pad for letters so I just leave the default.  I hit OK.

Then I am on IPv4/IPv6. I press OK.

I do not need to use arrow buttons to get to IPv4 because it already displays that. (actually it says *IPv4, but only other option is IPv6) I hit OK

I get the following message:  communication may be disabled press ok to continue.

I press OK.  This is what the HOW TO says next:
> 
 Keep IPsec setting inactive by pressing OK. The status message should show "SETTING..."

I have no idea what this means.  When I hit OK it drops me to "AUTO SETUP".  No mention of IPsec, no mention of "SETTING". 

I assume that this is because the machine was already configured for Windows.  To make things more confusing I had used the "easy connect" button or whatever it is called on the Cisco Router rather than manually entering the WEP code into the printer.  I don't know what that does.  

So, assuming I have not just disabled the connection somehow, I attempted to find the computer via add printers.  

The HOW TO said to hit "find" but it asks for a HOST.  I tried find without entering anything.  I tried it by entering the IP and I tried it by entering the mac address as the person who posted the screenshots shows.  It never detected the printer.  

My questions for whoever may have read this far: since I had a successful connection in WIndows, can I just circumvent those setup steps?  If so, any idea why it is not detecting the printer on the wireless.  If not, can someone help me sort out why the steps I followed diverge from the HOW TO?  Thanks.

---

### Post by pweyandt on 2011-03-03
I just set up the  MX350 on my 64 bit machine.  
Thanks Cypher2! Awesome instructions.  
You get 5 stars! :KS :KS :KS :KS :KS
Here is a link to the Cannon PIXMA MX350 All in one.
[http://software.canon-europe.com/software/0038682.asp?model=](http://software.canon-europe.com/software/0038682.asp?model=)

---

### Post by webale on 2011-04-27
[SIZE=2]**Hi there.**[/SIZE]

[SIZE=2]I'm more or less a Newbie to Linux, but even i was able to follow the detailed instruction.
What should i say, it works.:D

I just installed Xubuntu 11.04 on my Acer Aspire 7745G and had troubles because the 32bit driver i found refuses to work.
So, thanx a lot Cypher2 for the instruction and pweyandt for the download link.[/SIZE]

---

### Post by corrytonapple on 2011-05-21
I get a "No Printer Found" error.  I am using 11.04.  Should it still work?

---

### Post by hsmcdonald on 2011-05-29
Thanks for the instructions, attached is a screenshot of how the printer appears for me after the network setup then using the add printer dialog.

---

### Post by BarakNaveh on 2011-08-11
Thank you for the instructions! It helped me set up the MX350.

I don't like the ScanGear program provided by Canon. Is there a way to get the scanner to work with other programs such as 'Simple Scan'?

---

### Post by ossgrouch on 2011-09-06
I finally got my Canon MX340 to work through WiFi in 11.04 Natty Narwhal by going a different route, printing through CUPS. Michael Gruz has made printer and scanner drivers available for for several Canon Printers, -ip, -ix, -mg, -mp, -mx, -pixmaip, -pixus series printers. Check page [https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/~michael-gruz/+archive/canon") for instructions on how to add his PPA to your software sources, then you can install the drivers from your Package Manager (Ubuntu software center, Synaptic package manager, Kpackage etc.)
Make sure ia32-libs are installed first (I had that problem), cups, and I also installed gutenprint, believing it is needed for cups to work with GIMP. Then select and install cnijfilter-common and cnijfilter-[your printer] and you should be able to add the Canon printer to ubuntu's printers (in Ubuntu: Applications - Themes&Tweaks - Printing:  Add printer)
To run the scanner you can use xsane (and probably simple scan too, or other scanner application), use your package manager to install scangearmp-[your printer], start scan application and let it search for the scanner. It worked for me.

---

### Post by gmc on 2011-10-16
Awesome! Just wanted to say Thanks for pointing out that PPA. After fooling around a bit I managed to get my MX350 working in 11.10

G

---

### Post by TomWildy on 2011-11-21
Thanks for this.  I was in a world of pain (well, not printing actually) and your exemplary item has solved my problem and taught me a bit more about Linux

Thanks

---

### Post by tybrownintn on 2011-11-30
My luck...the list of drivers skips from mp610 to mp 630.  I tried the 610 driver but got this message which I think is independent of whether I have the right driver...as it shows up as soon as I open up add printers:

> FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.

Currently I don't have a firewall installed on this new install of Ubuntu 11.10.  I'm using the Gnome shell if that makes a difference.

---

### Post by tybrownintn on 2011-12-04
Apparently my issue is now listed as a known bug. But no action on it yet.

[https://bugs.launchpad.net/ubuntu/+bug/879377]("https://bugs.launchpad.net/ubuntu/+bug/879377")

Googling the error message gets lots of hits and the bug report confirms that it affects multiple users.  

I will try Linux Mint and see if it works there.

---

### Post by Docaltmed on 2011-12-12
> **tybrownintn said:**
> My luck...the list of drivers skips from mp610 to mp 630.  I tried the 610 driver but got this message which I think is independent of whether I have the right driver...as it shows up as soon as I open up add printers:



Currently I don't have a firewall installed on this new install of Ubuntu 11.10.  I'm using the Gnome shell if that makes a difference.

Yeah, that's a Gnome Shell bug. Easiest thing to do is to log out of gnome shell, log in under Unity, and use the printer gui there to install it. That's what I did, it works fine. When you go back to gnome shell, the printer will be already installed and waiting for you.

---

### Post by tybrownintn on 2011-12-13
I didn't get any error messages in Unity but it did not detect the printer at all, which is often my experience.  I wish installing printers were not so difficult in Linux. Difficult for me, at least.

---

### Post by scda1234 on 2012-02-10
I tried everything I could find here and else to get my canon pixma mx340 working with ubuntu 11.4 it was easy with the earlier versions of Ubuntu.  Not so much any more was about toss Linux out the door after 3 years and go back what works windows. Then I found turbo print for Linux. Turbo Linux has several hundred drivers for Linux built in you can get either 32 bit or 64 bit versions from them. Bad thing is its not free or open source 30 day free trial and 30 bucks to buy. Any way itworks great and its very easy to install. Check it out at,


[http://www.zedonet.com/en_p_turboprint_download_uni.phtml?arch=1](http://www.zedonet.com/en_p_turboprint_download_uni.phtml?arch=1)

---

### Post by rue1341 on 2012-02-28
For Ubuntu 11.10 64bit

Just seen this thread but you need to have a look at the thread below and try the points  which worked for me  (page 5 has the 64bit drivers)

[http://ubuntuforums.org/showthread.php?t=1518425](http://ubuntuforums.org/showthread.php?t=1518425)

Many thanks to Cypher2, bota87 and Marseille, I have finally got my MX340 to print by USB & wireless.

I my experience you need to:-

Set the printer up according to Cypher2's instructions (page 1)

Then use bota87's packages and Cypher2's method of installing them.

BUT first check you have "ia32-libs" and "ia32-libs-multiarch:i386" packages install on your system, it did not work for me without them.

Also it may help to re-boot.

One very happy man

---

