---
title: "Howto: Get the Canon MP210 and MP220 scan-copy-printers to work in Ubuntu Hardy"
date: 2008-10-10
forum: General Help
---

### Post by ezramorris on 2008-10-10
[COLOR="Red"][B][SIZE="3"]Read first: If you're using a recent version of Ubuntu*, ignore the entire post; just follow this red section.[/SIZE]

[LIST=1]
[*]Plug the printer in, and Ubuntu will try and install it, but fail.
[*]Go to 'Printing', either through System>Administration>Printing, or type printing in the home thing.
[*]Click Add, select your printer, and when asked about drivers, leave the default - Select printer from database and Canon.
[*]At the next drivers page choose PIXMA MP220. If MP220 isn't there, try the next lowest number i.e. 210, then 180, then 160.
[/LIST]
Scanning works out of the box, you just need to press the Scan button before.[/B]

* I've only tried this on 11.10, but have read that it works out of the box since 10.04.[/COLOR]

-----For older dists-----

There are various posts and blogs about describing how to get the Canon PIXMA MP* all-in-one printers to work in Linux.

This has been tested on the PIXMA MP220, but the MP210 is very likely to work (since it is actually its drivers we are using), and other printers in the MP range may also work.

1. You can set the printer up, but please don't plug it in to the USB port yet; doing so will make Ubuntu install it as a text-only printer, which is not what we want.

If you did this already (like I did (-: ), unplug it from your computer, then go to System>Administration>Printing, click on your printer in the left hand column, click delete, then OK.

2. Go to [http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP210%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-au.canon.com.au/EN/search?v%3aproject=ABS-EN&binning-state=model%3d%3dPIXMA%20MP210%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&) and download all the drivers you need. Basically, you will need everything that says Debian in the title. There should be four downloads. When I did it, it was the first four listed. [Edit: this link is now dead. Google for the files in step 3 instead. They still seem to be on the support-au.canon.com.au site, but are hard to find.]

3. Double click on each package <in the following order>, and choose to install the package.
--1. cnijfilter-common_2.80-1_i386.deb
--2. cnijfilter-mp210series_2.80-1_i386.deb
--3. scangearmp-common_1.10-1_i386.deb
--4. scangearmp-mp210series_1.10-1_i386.deb

4. Restart your computer.

5. Once you are logged on, plug in your printer and switch it on. Ubuntu should detect your printer, and tell you it used the MP210 driver for it. (This is correct even if you are using the MP220.)

6. Print something to test the printer is set up properly. If scanning works, you can stop here.

[COLOR="Red"]-----Please read the next few posts from this thread before continuing and/or you have problems after this point.-----

**Note: It now seems like you can just press the 'scan' button on the printer, wait for it to switch to scan mode, then scan your document as usual. If this works, you don't need to continue.**[/COLOR]

7. From [http://sourceforge.net/project/showfiles.php?group_id=210977&package_id=253502&release_id=584777](http://sourceforge.net/project/showfiles.php?group_id=210977&package_id=253502&release_id=584777) download the file. It should say something like mp150-0.14.4.tar.bz2 .

8. Open up a terminal (Applications>Accessories>Terminal), and cd to the directory which you saved it to. For example, if you saved it to your desktop, you would type:
```
cd Desktop
```

9. Extract the file by doing:
```
tar -xvjf mp150*.tar.bz2
cd mp150*/
```

10. Compile it by typing:
```
sudo apt-get install build-essential
make NDEBUG=yes
```

11. And check everything is correct:
```
sudo ./scan -x 10 -y 15 -w 51 -h 25 -1 -d 20 -W pixmascan.pnm
```
Your printer should whurr a bit, and there should be some output, but no errors.

12. Install the scanner drivers:
```
ls /usr/lib/sane/libsane-pixma.so.1.0.*
```
Look at the output and bear in mind what is written. For me it said /usr/lib/sane/libsane-pixma.so.1.0.19 but this may be different for you. Replace 1.0.19 below if you got something different.
```
sudo mv /usr/lib/sane/libsane-pixma.so.1.0.19 /usr/lib/sane/libsane-pixma.so.1.0.19.old
sudo cp libsane-pixma.so /usr/lib/sane/libsane-pixma.so.1.0.19
```

13. At this point, only the root user would be able to use the scanner, so we need a few extra steps to allow others to use it. First we need the USB address. Type:
```
lsusb
```
This will list all the usb devices plugged in to your computer. There should be a line ending in "Canon, Inc." (There may be more if you use other Canon products.) It should look something like:
> Bus 006 Device 006: ID 04a9:1722 Canon, Inc.
The important part it the code after ID, in this case 04a9:1722 . You need to keep a record of this number. Either write it down or know how to use scrollback in your terminal.
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
In this file add the following lines:
```
# Canon PIXMA
SYSFS{idVendor}=="[COLOR="RED"]04a9[/COLOR]", SYSFS{idProduct}=="[COLOR="RED"]1722[/COLOR]", MODE="664", GROUP="scanner"
```
Change the bits in red to match up to your ID.

14. Close gedit, and back at the terminal, type:
```
sudo udevcontrol reload_rules
```

Now try your scanner, and see if it works! Note that you must be in the group called 'scanner' to use it.

For example, if you are using GIMP, from the main window, click File>Acquire>XSane>Device Dialog.

Let me know how you get on.

References:
This tutorial is heavily based on the following web pages:
- [http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html](http://mp610.blogspot.com/2008/02/canon-mp210-and-mp520-join-party.html)
- [http://mp610.blogspot.com/2007/11/new-sane-scanner-driver-for-canon-mp610.html](http://mp610.blogspot.com/2007/11/new-sane-scanner-driver-for-canon-mp610.html)
- [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=556980)

---

### Post by kostas4einny on 2008-10-12
hello!I am beginner with ubuntu!I need your help!I I followed your instractions and at the first time the printer works.After i tried to fix the scanner.And now i cant print or scan..I dont know hot to fix it.Now i tried to print but in the desktop says    "Not connected?
         Printer 'MP220_series'may not be connected"

Thanks in advance

---

### Post by ezramorris on 2008-10-12
> **kostas4einny said:**
> hello!I am beginner with ubuntu!I need your help!I I followed your instractions and at the first time the printer works.After i tried to fix the scanner.And now i cant print or scan..I dont know hot to fix it.Now i tried to print but in the desktop says    "Not connected?
         Printer 'MP220_series'may not be connected"

Thanks in advance

Hi,
Welcome to Ubuntu Forums!
Did the printer work after step 6?

---

### Post by kostas4einny on 2008-10-12
Hi,Thanks for the quick answer!Yes the printer worked after step 6.But it doesn't work now.I did something wrong with the scanner.

---

### Post by ezramorris on 2008-10-12
> **kostas4einny said:**
> Hi,Thanks for the quick answer!Yes the printer worked after step 6.But it doesn't work now.I did something wrong with the scanner.

OK, the following steps should take you back to the step 5 state.

1. Unplug your printer from your computer.

2. Go to System>Administration>Printing, select your MP??? printer, then click delete.

3. Open a terminal (Applications>Accessories>Terminal), and type one of the following. If your /etc/udev/rules.d/45-libsane.rules file had stuff in before you added the two PIXMA lines, then:
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
and remove the two lines you added.

Otherwise, if the file was empty to start with, just do:
```
sudo rm /etc/udev/rules.d/45-libsane.rules
```

4. Now type the following lines:
```
sudo mv -f /usr/lib/sane/libsane-pixma.so.1.0.19.old /usr/lib/sane/libsane-pixma.so.1.0.19
sudo apt-get --reinstall install cnijfilter-common cnijfilter-mp210series scangearmp-common scangearmp-mp210series
```

5. Reboot, and after you have logged on, plug in the printer, and it should detect and install it as before.

You should now be able to print. You may still be able to scan, although it will be very primitive. In a terminal, cd to the directory where you downloaded the .tar.gz file, and try using the provided scan utility, for example:
```
cd Desktop/mp150*/
./scan -1 -p A4 ~/image1.pnm
```
(-1 is a one not an el)
All being well, this should create an image called image1.pnm in your home folder, although the quality won't be that great.

In theory, you can use the option -r to select the resolution, eg. -r 300, but when I tried it, it crashed the scanner. If this happens, wait for the program to exit (ie. the terminal will return to username@host:~ or something), unplug the printer, reboot, logon, then plug the scanner back in again.

You can find all the options if you type ./scan --help.

Hope this helps.

---

### Post by kostas4einny on 2008-10-12
Yes!! It print 's now!But i cant scan. I wrote this 
"cd Desktop/mp150*/
./scan -1 -p A4 ~/image1.pnm" in terminal and the answer was
 No supported scanner found!

---

### Post by ezramorris on 2008-10-12
> **kostas4einny said:**
> Yes!! It print 's now!But i cant scan. I wrote this 
"cd Desktop/mp150*/
./scan -1 -p A4 ~/image1.pnm" in terminal and the answer was
 No supported scanner found!

Try putting sudo in front to run it as root, ie.
```
sudo ./scan -1 -p A4 ~/image1.pnm
```

---

### Post by kostas4einny on 2008-10-12
Yes!!! Thank you very much!I appriciate that!It works now!!
I have to last questions.Firstly,this will work if move the folder mp150-0.14.4 ?
Secondly ,do you know how i can save the images to another folder than home/username ?

---

### Post by ezramorris on 2008-10-12
> **kostas4einny said:**
> Yes!!! Thank you very much!I appriciate that!It works now!!
You're welcome.
> **kostas4einny said:**
> I have to last questions.Firstly,this will work if move the folder mp150-0.14.4 ?
Yes. Obviously you will have to cd to that new directory before running ./scan.
> **kostas4einny said:**
> Secondly ,do you know how i can save the images to another folder than home/username ?
Yes. ~ represents /home/yourusername, so just change ~/image1.pnm to the path that you want, but I would suggest putting it somewhere in your home directory.

Be very careful when doing anything with this command. Since you are running as root (via sudo), it means you are basically allowing it to do anything on your system, so in theory you could overwrite some vital file.

---

### Post by FredWiersma on 2008-10-17
> **ezramorris said:**
> There are various posts and blogs about describing how to get the Canon PIXMA MP* all-in-one printers to work in Linux.

This has been tested on the PIXMA MP220, but the MP210 is very likely to work (since it is actually its drivers we are using), and other printers in the MP range may also work.
...

Thanks a lot for this info! The MP220 is printing as we speak :) the scanning part is the next challenge (but not so urgent for now).

Best!
Fred

---

### Post by ezramorris on 2008-10-17
> **FredWiersma said:**
> Thanks a lot for this info! The MP220 is printing as we speak :) the scanning part is the next challenge (but not so urgent for now).

Best!
Fred

Good luck! Both kostas4einny and I have had problems with it. If you give up, do post 5 to get back.

---

### Post by ezramorris on 2008-10-18
> **ezramorris said:**
> Good luck! Both kostas4einny and I have had problems with it. If you give up, do post 5 to get back.

Guys, I got it working!

I had a problem with my webcam in the current linux kernel (2.6.24-21) and someone suggested trying the previous one (2.6.24-19), and it worked. So, I decided to try the scanner again, and guess what? That works to.

I have reported a bug with the webcam, but will add the one about the printer to it as well.

For now, there's a fair chance that if you select the 2.6.24-19 kernel at the boot menu, it might work. If you kept the mp150... folder, just cd to the folder, then follow steps 12 to 14 again, otherwise follow steps 7 to 14.

[COLOR="Red"]Edit:[/COLOR] It stopped working after a reboot, had to go back.

---

### Post by Hampster on 2008-10-21
A thousand thankyou's for your efforts.  I was nearly ready to throw the printer as far as I threw my xp professional disc. 

Scanned my first document using Gimp.  Xsane cant find any devices..  too bad how sad.

May your next wish come true.

Edit...
Found the scanner worked great but no more printing.  please see new thread.  Would appreciate your input.... ta

[http://ubuntuforums.org/showthread.php?t=954450](http://ubuntuforums.org/showthread.php?t=954450)

---

### Post by mad_prince on 2008-10-30
is there driver for 64bit or only for 32bit? I can't find different then i386

---

### Post by ezramorris on 2008-10-30
It appears that if you follow the original steps, then scan, and put everything back, it works fine.

I wrote a script to automate this. It will do the steps, ask you to scan, and when you click OK, it will put everything back.

Please note that I have only tested this on my machine, so use at your own risk.

1. At a terminal, type ```
sudo gedit /usr/local/bin/scanner
```
2. Copy the following text into it.
3. Edit as per instructions in the file. You need to change source, manuf, prod and sofile to match your setup. Now save and exit gedit.
4. ```
sudo chmod +x /usr/local/bin/scanner
```
5. Whenever you want to scan, hit Alt-F2, type ```
gksudo scanner
``` then follow the instructions. You could also make a launcher to save typing this every time.



The script:
```
#!/bin/bash

#Set the path to your source folder:
#Please do not use "~"
source="/home/username/mp150-0.14.4"

#Set your device ID from the output of lsusb here:
#E.g. for "Bus 006 Device 006: ID 04a9:1722 Canon, Inc.", you would set manuf=04a9 and prod=1722
manuf=04a9
prod=1722

#Set your .so file here from the output of ls /usr/lib/sane/libsane-pixma.so.1.0.*
sofile="/usr/lib/sane/libsane-pixma.so.1.0.19"

#Do not edit below this line unless you know what you are doing.
#---------------------------------------------------------------

function error {
  zenity --title="Error" --error --text="An error occured. Please make sure you have set the path correctly in '$0'."
  exit 1
}

if [ $UID -eq 0 ]; then
  cd "$source" || error
  if [ ! -f libsane-pixma.so ]; then
    apt-get install build-essential | tee >(zenity --title="Installing" --progress --pulsate --auto-close --text="Installing build-essential...")
    make NDEBUG=yes || error | tee >(zenity --title="Installing" --progress --pulsate --auto-close --text="Making the driver...")
  fi
  mv "$sofile" "$sofile.old" || error
  cp "libsane-pixma.so" "$sofile" || error
  echo "# Canon PIXMA" > "/etc/udev/rules.d/45-libsane.rules"
  echo "SYSFS{idVendor}==\"$manuf\", SYSFS{idProduct}==\"$prod\", MODE=\"664\", GROUP=\"scanner\"" >> "/etc/udev/rules.d/45-libsane.rules"
  udevcontrol reload_rules
  zenity --title="Ready for scanning" --info --text="Please now scan your documents. Press OK once you have finished."
  rm "/etc/udev/rules.d/45-libsane.rules" || error
  mv -f "$sofile.old" "$sofile" || error
  udevcontrol reload_rules
  /etc/init.d/udev restart | tee >(zenity --title="Nearly there..." --progress --pulsate --auto-close --text="Restarting udev...")
  zenity --title="Done" --info --text="Successfully reverted."

else
  zenity --title="Please run as root." --warning --text="Please run this script as root by doing 'sudo $0' or 'gksudo $0'."
  exit 1
fi
```

---

### Post by ezramorris on 2008-10-30
> **mad_prince said:**
> is there driver for 64bit or only for 32bit? I can't find different then i386

I doubt it, but you could try installing the 32 bit libraries, then running the 32 bit version.

---

### Post by impact on 2008-11-28
> **ezramorris said:**
> Good luck! Both kostas4einny and I have had problems with it. If you give up, do post 5 to get back.

In Ibex scanning is actually quite simple. Once your test page is printed, do not continue with the step 7 of the original guide. Instead, press the large button on the MP220 labelled "scan" and wait till the printer switches itself into scanner mode. Then start Xsane and voila, it will find a new scanner. :)

On a semi-related note, has anyone experienced any problems while printing very large photos?

---

### Post by insyzygy on 2008-11-29
Just out of curiosity. I just installed the drivers for this program and if you run (after installing all the packages from cannon)

```

./scangearmp 

```

it will open a very nicing scanning utility which seems must simplier than what people have been describing. This is with the mp210. It seems people are doing things a much more difficult way?

---

### Post by ezramorris on 2008-12-05
> **impact said:**
> press the large button on the MP220 labelled "scan"

Wow. It actually works like it should...
Cheers

---

### Post by enough! on 2008-12-16
):P Hi there, I'm new to Linex & Ubuntu.... and blond!!! I've tried downloading the drivers... but I get the following error message straight after downloading -  Error: Wrong architecture 'i386'
What does this mean? I can print using the MP180 driver but it does not detect the scanner... and I kind of like using the scanner else I would not have bought the machine.... Please help... and remember, I'm Blond!!!

---

### Post by ezramorris on 2008-12-16
> **enough! said:**
> ):P Hi there, I'm new to Linex & Ubuntu.... and blond!!! I've tried downloading the drivers... but I get the following error message straight after downloading -  Error: Wrong architecture 'i386'
What does this mean? I can print using the MP180 driver but it does not detect the scanner... and I kind of like using the scanner else I would not have bought the machine.... Please help... and remember, I'm Blond!!!

The driver will not work with 64 bit Ubuntu.

If the printer works, have you tried pressing the 'scan' button on the printer before trying to scan?

---

### Post by Brackenn on 2011-03-27
Hi. I was wondering if anyone was still responding to this thread. I'm not very Ubuntu savvy, and I'm trying to follow the instructions at the very top. I'm using 9.10 and trying to make a MP210 scanner-printer work. I can't get past step 3. in step 2 it points you to [http://support-au.canon.com.au/EN/se...os%3d%3dLinux&](http://support-au.canon.com.au/EN/se...os%3d%3dLinux&) , but that gets a "page not found". I did a search and found the files listed in step 3, but when i try to run the first one, I get 
"...Unpacking cnijfilter-common (from .../cnijfilter 2.80-1_i386.deb) ... dpkg: dependency problems prevent configuration of cnijfilter-common: cnijfilter-common depends on libcupsys2 (>= 1.2.1); however: package Libcupsys2 is not installed..."
I'm going around in circles on this, it points to synaptic to take out the broken package. how do I satisfy this Libcupsys2 thing?

Thanks in advance.

---

### Post by dai_bach on 2011-05-09
I can't vouch for how useful this information is, but have you tried the commands
```
sudo apt-get --fix-missing install
```
```
sudo dpkg --configure packagename.deb
```
or 
```
sudo dpkg --configure -a
```
?

These are the standard ways of fixing broken packages.  You could also try doing 
```
sudo apt-get install libcupsys2
```

Good luck!

---

### Post by ezramorris on 2011-10-10
In Oneiric (and possibly some previous dists - I've not tried), you don't need any external packages and the like.

Plug the printer in, and Ubuntu will try and install it, but fail. Go to the printing prefs, click Add, then follow through the steps. I don't think you even need to change anything. Also, scanning works out of the box, you just need to press the Scan button.

I'll update the OP.

---

