---
title: "Brother QL-500 label printer installation"
date: 2010-12-27
forum: Hardware
---

### Post by ipsod on 2010-12-27
I'm trying to install a Brother QL-500 label printer on Ubuntu Studio 10.10.

I tried the install wizard with no luck.  It shows up in the printer list, but won't print.

Tried the top section on this link (in a simulated root shell) with the same results: [http://www.panticz.de/ubuntu_brother_ql-500](http://www.panticz.de/ubuntu_brother_ql-500)

I'm new to Linux - keep it simple, please!

---

### Post by davidmohammed on 2010-12-27
welcome to the forums

there are a three "deb" packages for your QL500 from the brother website - together with instructions on how to install.

suggest visit [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_esp.html") - search for QL 500 and look at the install instructions.

---

### Post by tonywhelan on 2010-12-27
Are you using the Brother Linux printer drivers from their website? [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp1.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp1.html") NOTE that Brother's drivers are ony for 32 bit software, not 64 bit distributions like I have. So if your installation is a 64-bit version, you're out of luck.

I tried installing from the Windows CD via my installed Wine program but the program wouldn't see the printer so wouldn't install the drivers. I also tried a driver I found at [http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/]("http://www.diku.dk/hjemmesider/ansatte/panic/P-touch/") but the 'make' failed with errors - probably its for 32 bit OSs though it doesn't say. 

I doubt that this printer can be made to work on a 64 bit version of Ubuntu, but it should work with the 32 bit Brother drivers.  

Pity the hardware manufacturers don't provide some decent installer software for linux and include it on their CD. 

I will probably just plug the printer into my partner's Windows computer and leave it there - we don't need to use it often so its not a hassle.

Good luck with yours.


Tony

---

### Post by ipsod on 2010-12-27
I'm running 32 bit

Well, I sporked it, maybe because I had already tried to install it and not cleaned up what I'd done previously, or maybe it would've happened anyway.

I followed the guide on brother's site here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp1.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_esp1.html), and on step 4-4 I got this:

sudo dpkg  -i  --force-all ql500cupswrapperinch-1.0.0-1.debian.i386.deb
```

(Reading database ... 
dpkg: warning: files list file for package `ql570cupswrapper' missing, assuming package has no files currently installed.
(Reading database ... 201217 files and directories currently installed.)
Preparing to replace ql500cupswrapperinch 1.0.0-1 (using ql500cupswrapperinch-1.0.0-1.debian.i386.deb) ...
Unpacking replacement ql500cupswrapperinch ...
start: Unknown job: cupsys
dpkg: warning: subprocess old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
start: Unknown job: cupsys
dpkg: error processing ql500cupswrapperinch-1.0.0-1.debian.i386.deb (--install):
 subprocess new post-removal script returned error exit status 1
start: Unknown job: cupsys
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 ql500cupswrapperinch-1.0.0-1.debian.i386.deb

```
Now I can't run synaptic.  When I try, I get this error:
E: The package ql500cupswrapperinch needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by davidmohammed on 2010-12-27
hmmm,
  looks like Brother havent updated stuff for Ubuntu 10.04.

Here is a [guide]("http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html") to fix your package repository so that you can remove the offending package.  Also in the comments there is a failsafe removal method.  Note the warning though.

---

### Post by tonywhelan on 2010-12-27
> **ipsod said:**
> I'm running 32 bit

Well, I sporked it, maybe because I had already tried to install it and not cleaned up what I'd done previously, or maybe it would've happened anyway.
.....
Now I can't run synaptic.  When I try, I get this error:
E: The package ql500cupswrapperinch needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

I don't know why the install failed, but to fix Synaptic I suggest you try cleaning it up:

Go to Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```
See if that resolves Synaptic's problem.

---

### Post by ipsod on 2010-12-27
root@mothership:/usr# apt-get upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ql500cupswrapperinch needs to be reinstalled, but I can't find an archive for it.

```

---

### Post by tonywhelan on 2010-12-27
> **ipsod said:**
> root@mothership:/usr# apt-get upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ql500cupswrapperinch needs to be reinstalled, but I can't find an archive for it.

```


Hmm. The alternative solution posted by davidmohammed seems to be for Debian, I don't think the folder names are the same in Ubuntu. Will have a look ....

---

### Post by tonywhelan on 2010-12-27
> **tonywhelan said:**
> Hmm. The alternative solution posted by davidmohammed seems to be for Debian, I don't think the folder names are the same in Ubuntu. Will have a look ....

I had earlier tried forcing the 32bit deb to install, and now when I run sudo dpkg --configure -a I get a similar error:

```
Setting up ql500cupswrapper (1.0.0-1) ...
ERROR : Brother LPD filter is not installed.
/usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1: 65: cannot create /usr/share/cups/model/brql500.ppd: Directory nonexistent
cp: `/usr/lib/cups/filter/brlpdwrapperql500' and `/usr/lib64/cups/filter/brlpdwrapperql500' are the same file
chmod: cannot access `/usr/local/Brother/PTouch/ql500/inf/brql500rc': No such file or directory
chmod: cannot access `/usr/local/Brother/PTouch/ql500/inf': No such file or directory
cp: cannot stat `/usr/local/Brother/PTouch/ql500/lpd/brusb_ql_lpr': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Bad device-uri "brusb_ql500:/dev/usb"!
/var/lib/dpkg/info/ql500cupswrapper.postinst: 4: /etc/init.d/cupsys: not found
dpkg: error processing ql500cupswrapper (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 ql500cupswrapper
```

When I figure out how to clear it, I'll post the solution, as it should fix yours too.

---

### Post by ipsod on 2010-12-27
> **tonywhelan said:**
> When I figure out how to clear it, I'll post the solution, as it should fix yours too.

Thank you, Tony!

---

### Post by tonywhelan on 2010-12-27
Well this is what I did to fix my error, but of course I'm poking around in the dark so can't guarantee its perfect.

1. In System, Administration, Printers, delete the printer in question. You might also need to browse to [http://localhost:631](http://localhost:631) and delete it in the CUPS printer list if it shows up there.

2. Go into a terminal, then ```
gksudo nautilus
```
which will open Nautilus with root permissions.

3. Use nautilus to go to folder /var/lib/dpkg/info
Be patient, there are a lot of files in there so will take a minute to load the list. Find all of the files that are named "ql500cupswrapper..." and delete them.

4. Go back a level to folder /var/lib/dpkg and open the file called "status" in gEdit. Do a File Save As and called it status.backup. Close, and re-open the file "status" (not the backup copy). Search for "ql500". You should find a paragraph starting with the words "Package: ql500cupswrapper" Delete that section and save the file.

5. Now repeat the process outlined in step 4, but with the file called "available".

You should now be able to go to a terminal and run ```
 sudo dpkg --configure -a

``` without any errors. 

Then try opening Synaptic.

Let us know how you go with it.

---

### Post by ipsod on 2010-12-27
Thank you!  Synaptic is fixed.

Now, do I forfeit or keep trying to get the printer to work?

---

### Post by tonywhelan on 2010-12-27
Glas synaptic is ok again.

The printer install seems likely to fail again and cause more frustration - but depends on how patient you are feeling. I'm giving up the printer issue for now myself; as I said earlier I can cheat by connecting it to my partner's PC :)

---

### Post by ipsod on 2010-12-27
Feeling almost patient enough to reinstall windows.

This is pretty frustrating.

---

### Post by davidmohammed on 2010-12-28
ok - one more try

[this]("http://www.blog.meansofseeing.com/2010/10/03/brother-ql-570-play-nice-ubuntu-10-04/") guy has got the QL 570 working.  You'll see in his blog that he had to tweak one of the deb files you downloaded so that it would install.  I guess that is the key issue for you.

May be you can do something similar - but obviously change the references from QL570 to something else - QL500??

---

### Post by ipsod on 2010-12-28
Thank you, David.

I got it installed using that guide, swapping "570" for "500" everywhere, and it didn't break synaptic, and seems that the computer recognizes the printer, but I still can't get anything to print.

---

### Post by tonywhelan on 2010-12-28
> **ipsod said:**
> Thank you, David.

I got it installed using that guide, swapping "570" for "500" everywhere, and it didn't break synaptic, and seems that the computer recognizes the printer, but I still can't get anything to print.

OK, I set up a fresh build of Ubuntu 10.10 (32 bit) and tried again, using the procedure referred to by davidmohammed and adding a few twists that I found elsewhere incl Brother's FAQ. And it has worked ok. Hopefully the steps listed below include everything that I did (I should have taken better notes).

Note that I used the cupswrapper deb rather than cupswrapperinch as I assumed I should, given that we are metric here, but you can use whichever is appropriate for you.

Before you do anything else, check that your install really did work. 
```
dpkg  -l  |  grep  Brother

```
which should return something like this:

```
ii  ql500cupswrapper      1.0.0-1     Brother CUPS PTouch Printer Definitions

ii  ql500lpr                1.0.0-1           Brother lpr color laser Printer Definitions

```
Note that if one or both lines start with “iF” instead of “ii” then this appears to signify the installation failed to complete correctly. If that's the case for you, please remove the installation completely as per the procedure I outlined in an early post (editing /var/lib/dpkg/info)

If it seems to have installed correctly, jump directly to Step 8 below and see how you go.

Step 1: CUPS versus CUPSYS – the Brother FAQ says:
I'm using Ubuntu8.10 or greater, I received an error message "/etc/init.d/cupsys: not found" during the installation. 

The command to restart the cups is changed from Ubuntu8.10.
Please make a symbolic link.
```
sudo ln -s /etc/init.d/cups /etc/init.d/cupsys
```

Step 2. Custom print – may not be needed but do it anyway
Install psutils from Synaptic –  needed for custom print.

Step 3. Issue ```
sudo aa-complain cupsd

```
Step 4. Create folders with  
```
sudo mkdir /var/spool/lpd
sudo mkdir /usr/share/cups/model
sudo mkdir /usr/share/cups/ql500
```

Step 5. Create a list file by issuing the following:
```
sudo gedit /var/lib/dpkg/info/ql500cupswrapper.list
```
or if using cupswrapperinch, issue this instead:
```
sudo gedit /var/lib/dpkg/info/ql500cupswrapperinch.list
```
(whichever one you use, make sure you stick to that name from here on or you'll break it)

Past the following into the file you just created, and then save it.
./
./usr/
./usr/local/
./usr/local/Brother/
./usr/local/Brother/PTouch/
./usr/local/Brother/PTouch/ql500/
./usr/local/Brother/PTouch/ql500/cupswrapper/
./usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1
./usr/local/Brother/PTouch/ql500/cupswrapper/brcupsconfpt1

Step 6: Run the deb packages from a terminal in the folder where you've stored them.
Firstly: 
```
sudo dpkg  -i  –force-all ql500lpr-1.0.0-1.i386.deb
```
check for any errors – hopefully none.

then 
```
sudo dpkg  -i  –force-all ql500cupswrapper-1.0.0-1.debian.i386.deb
```
or
```
sudo dpkg  -i  –force-all ql500cupswrapperinch-1.0.0-1.debian.i386.deb
```
depending on which you are using. 

Look for errors. Ignore the error about “Bad device-uri "brusb_QL-500):/dev/usb"!" -this is not a problem.

If no other errors, its looking good. However if you get an error about not being able to find **cupsys** then the symbolic link created in step 1 hasn't helped and you need to refer to my footnote below.

Step 7. Check if the installs report as successful:
```
dpkg  -l  |  grep  Brother

```
should return something like this:

```
ii  ql500cupswrapper      1.0.0-1     Brother CUPS PTouch Printer Definitions

ii  ql500lpr                1.0.0-1           Brother lpr color laser Printer Definitions
```

Step 8:  Configure CUPS
Open a web browser and go to "http://localhost:631/printers". 
Click the Printers menu tab, and locate the QL500 printer in the list. Select it, click Administration and select "Modify Printer" from the dropdown.
After a delay you'll get a list of local printer ports to connect to. For some reason I got two - one said Brother USB Printer, the other said Brother QL-500. The second one was the one that worked for me. Select the button beside the desired printer and click Continue, then edit the Description if you want to and press Continue again
You now get a list of printer drivers – it should have the Brother QL-500 CUPS driver in the list. Select it and click the Modify button.

I downloaded the Templates for openoffice from the Brother website and used the one appropriate to my label size to print a test label perfectly.

Footnote:
If cupswrapper installation gives an error about not being able to find cupsys then the symbolic link created in step 1 hasn't helped and you need to edit the cupswrapper deb archive. The file /DEBIAN/postinst need to have the line 
**/etc/init.d/cupsys restart**
changed to
**/etc/init.d/cups restart**

To edit it you will have to extract all the contents of the deb archive (keep folders intact) to a temp folder, do the edit and save it, then re-archive the folders 
```
dpkg -b temp-directory ql500cupswrapper-1.0.0-1.debian.i386.deb
```
or
```
dpkg -b temp-directory ql500cupswrapperinch-1.0.0-1.debian.i386.deb
```
as appropriate.

Hope that helps – let us know.

---

### Post by beerbelly on 2010-12-30
Hi all,

For me, the packages provided by Brother didn't work on 10.10 either. Suprisingly, (after fixing) Synaptic seems to list a 'ptouch-driver' that made my QL-500 work right away, without any pain.

Perhaps it helps.

Jeroen

---

### Post by ipsod on 2011-01-02
> **beerbelly said:**
> Hi all,

For me, the packages provided by Brother didn't work on 10.10 either. Suprisingly, (after fixing) Synaptic seems to list a 'ptouch-driver' that made my QL-500 work right away, without any pain.

Perhaps it helps.

Jeroen

 I was away for the holidays.  This does help, thank you!  Test page prints instantly - will see if paypal label printing works when I have a chance.

---

### Post by beerbelly on 2011-01-03
@Ipsod: glad I could help!

Sure hope it works better for you than it did for me: all drivers seemed to work like a charm, and the test page did indeed come out fine. Unfortunately, I need to print labels from Firefox and that browser has trouble using the right paper size. Even when Print Preview shows the label right, the final print seems to be on A4 paper size, wasting 2 blank labels and printing the third on the bottom half of the label.

If I print to PDF using the Brother driver, I also end up with an A4 sized PDF with the actual label text in the lower left corner.

I'm now printing from VirtualBox, with a WinXP guest. Wasted a few days of searching and trying to get this paper size thing to work first, but without success.

If anyone knows how to deal with printing from Firefox, I'd love to hear it.

---

### Post by skeltonh on 2011-06-01
You have to remove the ql500cups* entries from /var/lib/dpkg/info.

**rm /var/lib/dpkg/info/ql500cups***

Then

**apt-get install**

which will remove the records and clean things up

Then

[B]apt-get update
apt-get upgrade[/B]

to solve everything else

Your CUPS system will need to be checked and a working driver for the QL500 to be installed.  A version is available through the System/Synaptic Package Manager - but it has a LOT of limitations.

I too am in dire need of a fully working QL-500 driver.

---

### Post by skeltonh on 2011-06-01
Sorry for the last post....a bit late #include <grins/sheepish.h>

Trying to rebuild the archive after fixing the cupsys issue.  Got it working otherwise.  Just need to get things back into sync with dpkg/apt-get

---

