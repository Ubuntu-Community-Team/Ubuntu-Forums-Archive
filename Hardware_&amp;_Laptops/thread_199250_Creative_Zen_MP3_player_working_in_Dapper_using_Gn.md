---
title: "Creative Zen MP3 player working in Dapper using Gnomad"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by msak007 on 2006-06-18
[SIZE=4][SIZE=3][B]Updated 4/9/07
[/B][/SIZE][/SIZE][LIST]
[*][SIZE=4][SIZE=3]** libmtp 0.1.5 released on 3/26/07**[/SIZE][/SIZE][/LIST][INDENT]> **Changlog**: Improved support for setting track meta data on Philips devices. More verbose detection using mtp-detect. New devices in the database. Fixes to account for buggy iRiver firmware when handling ogg files.[/INDENT][LIST]
[*]**[SIZE=3]Added the "--dpkgflags=--force-overwrite" flag to libnjb compilation instructions for Dapper to prevent conflicts and errors when using checkinstall[/SIZE]**
[*]**[SIZE=3]Also added a recommendation to use "make install" in the steps if checkinstall fails to install a pacakage[/SIZE]**[/LIST][SIZE=4][SIZE=3][B] _Current versions of the software:_
[/B]Gnomad - 2.8.10
libnjb - 2.2.5
libmtp - 0.1.5

[/SIZE][/SIZE]Before proceeding, make sure you do not have any packages that conflict. If you have already installed Gnomad from the repositories prior to running this how-to or installed it by previously using this guide, please uninstall it and its dependencies first:

```
sudo aptitude purge gnomad2
``` Also, if you have previously used this how-to to install libmtp, please uninstall the currently installed version before trying to compile the new version to prevent conflicts and errors:
```
sudo aptitude purge libmtp
```[SIZE=6]_**Instructions for Edgy:**_[/SIZE] 

It is no longer necessary to compile everything from source to use Gnomad in Edgy. Unfortunately, the version of Gnomad in the repositories (2.8.3) was not compiled with libmtp, so the app will still have to be compiled from source. libnjb has been updated to 2.2.5 in the repos (latest version), and there is no need to compile libmtp from source unless a new version explicitly supports your device and an older version doesn't, or you are having other issues with communication, transferring files, etc. The repos currently contain libmtp version 0.0.19.

[SIZE=5][U][B]Method 1: Install repository versions
[/B][/U][/SIZE]This method only requires Gnomad to be compiled from source to enable MTP support. 

1. To prepare your system for the installation, you need to install several packages to resolve dependencies. Open a terminal and type:

```
sudo aptitude install build-essential libnjb-dev libmtp-dev libid3tag0-dev libglib2.0-dev libgtk2.0-dev libxml-perl [COLOR=Red]checkinstall[/COLOR]
```Checkinstall is optional but I highly recommend it because it makes .debs and installs them, making uninstallation easier using apt / Syanptic / Adept. If you don't like this method or if at **any** point during the install process you get errors running checkinstall and a package fails to install, you may revert to using the normal "make install" method to install the software.

2. Create a directory to download the needed files to and compile from. If you open the terminal, it should default to your home directory so create the directory there:

```
mkdir gnomad_install
```3. Next, download the latest version of [Gnomad 2.8.10]("http://downloads.sourceforge.net/gnomad2/gnomad2-2.8.10.tar.gz") to the folder you just created:

4. Navigate to the folder where you downloaded the file and extract it:
```
cd gnomad_install
tar -zxvf gnomad2-2.8.10.tar.gz
```5. Navigate to the Gnomad folder to compile it:
```
cd gnomad2-2.8.10
```6. Compile Gnomad:
```
./configure
make
sudo checkinstall
```Hit Enter past all the prompts, and once it has completed Gnomad2 should be installed. It should place an entry in your menu, but if it doesn't start it from a terminal by typing

```
gnomad2
```[SIZE=5][B]_Method 2: Compile from source_
[/B][/SIZE]1. To prepare your system for the installation, you need to install several packages to resolve dependencies. Open a terminal and type

```
sudo aptitude install build-essential libnjb-dev libid3tag0-dev libglib2.0-dev libusb-dev libgtk2.0-dev libxml-perl [COLOR=Red]checkinstall[/COLOR]
```Checkinstall is optional but I highly recommend it because it makes .debs and installs them, making uninstallation easier using apt / Syanptic / Adept.

2. Create a directory to download the needed files to and compile from. If you open the terminal, it should default to your home directory so create the directory there:

```
mkdir gnomad_install
```3.  Download the required packages to the folder you just created:

[libmtp 0.1.5]("http://sourceforge.net/project/downloading.php?groupname=libmtp&filename=libmtp-0.1.5.tar.gz")
[gnomad 2.8.10]("http://downloads.sourceforge.net/gnomad2/gnomad2-2.8.10.tar.gz")

4. Navigate to the folder where you downloaded the files: 

```
cd gnomad_install
```5. Extract both packages: 

```
tar -zxvf libmtp-0.1.5.tar.gz
tar -zxvf gnomad2-2.8.10.tar.gz
```6. Go to the extracted libmtp folder.
```
cd libmtp-0.1.5
```7. Compile libmtp
```
./configure --prefix=/usr
sudo make
sudo checkinstall
```Hit Enter three times, give your package a description, then hit Enter twice. You'll get a confirmation that the package was installed telling you the name of the package, where the package was created, and how to uninstall it. 

There should be a file called [COLOR=Red]libmtp.rules[/COLOR] in the same folder you are currently in. This is an updated udev ruleset that tells the system who can access the devices, and with what permissions. Without this ruleset, you would have to run Gnomad as root every time. It is constantly being updated with new devices with every subsequent release of libmtp, so there should be no need to update it manually.  To copy the file where it needs to go, type ```
sudo bash hotplug.sh
```You should see an output telling you that you have udev, and that the udev ruleset was installed. You'll also get a prompt asking you if you want the old hotplut support, type "n" and hit Enter.

**Note: **Running the "hotplug.sh" script **should** copy the file "libmtp.rules" to where it's supposed to go. If it doesn't, you can simply copy the file manually:
```
sudo cp libmtp.rules /etc/udev/rules.d/
```8. Navigate to the folder where Gnomad was extracted
```
cd ..
cd gnomad2-2.8.10
```9. Compile and install Gnomad
```
./configure
sudo make
sudo checkinstall
```Once again, hit Enter past all prompts to choose default answers, give it a description, and hit Enter two more times to install Gnomad.

9. Restart udev so that the rulesets we copied over earlier will be applied:
```
sudo /etc/init.d/udev restart
```10. Once this has completed, it should place an entry in your menu for Gnomad. If it doesn't start it from a terminal by typing

```
gnomad2
```[SIZE=6]_**Adding the menu entry:**_[/SIZE]

Once you've verified that Gnomad works (using either method), you can take the following steps to add the menu entry. You should still be in the Gnomad directory where you just compiled from.

1. Copy the menu entry file and corresponding icon to their respective locations:
[LEFT]```
sudo cp gnomad2.desktop /usr/share/applications
sudo cp gnomad2-logo.png /usr/share/pixmaps
```[/LEFT]
 
2. Reload your menu and the entry should be there:

- If you're a Gnome user:
 ```
sudo killall gnome-panel 
```- If you're a KDE user:
[LEFT]```
kbuildsycoca --incremental 
```[/LEFT]

Now the menu entry should show up in your Multimedia group.

[SIZE=6]_**Instructions for Dapper:**_[/SIZE]
Dapper requires all 3 components (Gnomad, libnjb, and libmtp) to be compiled from source, so the only option is to compile from source.

1. To prepare your system for the installation, you need to install several packages to resolve dependencies. Open a terminal and type

```
sudo aptitude update
sudo aptitude install build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev checkinstall
```[COLOR=Red]Checkinstall[/COLOR] is optional but I highly recommend it because it makes .debs and installs them, making uninstallation easier using apt / Syanptic / Adept. If you don't like this method or if at **any** point during the install process you get errors running checkinstall and a package fails to install, you may revert to using the normal "make install" method to install the software.

2. Create a directory to download the needed files to and compile from. If you open the terminal, it should default to your home directory so create the directory there:

```
mkdir gnomad_install
```3. Download the required packages to the folder you just created.[URL="http://downloads.sourceforge.net/libmtp/libmtp-0.1.4.tar.gz"]

[/URL][ libmtp 0.1.5]("http://sourceforge.net/project/downloading.php?groupname=libmtp&filename=libmtp-0.1.5.tar.gz")
[libnjb 2.2.5]("http://downloads.sourceforge.net/libnjb/libnjb-2.2.5.tar.gz")
[gnomad 2.8.10]("http://downloads.sourceforge.net/gnomad2/gnomad2-2.8.10.tar.gz")

4. Navigate to the folder where you downloaded the files:

```
cd gnomad_install
```5. Extract all 3 packages:

```
tar -zxvf libmtp-0.1.5.tar.gz
tar -zxvf libnjb-2.2.5.tar.gz
tar -zxvf gnomad2-2.8.10.tar.gz
```6. Go to the extracted libmtp folder.
```
cd libmtp-0.1.5
```7. Compile libmtp
```
./configure --prefix=/usr
sudo make
sudo checkinstall
```Hit Enter three times, give your package a description, then hit Enter twice. You'll get a confirmation that the package was installed telling you the name of the package, where the package was created, and how to uninstall it.

8. There should be a file called libmtp.rules in the same folder you are currently in. This is an updated udev ruleset that tells the system who can access the devices, and with what permissions. Without this ruleset, you would have to run Gnomad as root every time. It is constantly being updated with new devices with every subsequent release of libmtp, so there should be no need to update it. To copy the file where it needs to go, type ```
sudo bash hotplug.sh
```You should see an output telling you that you have udev, and that the udev ruleset was installed. You'll also get a prompt asking you if you want the old hotplug support, type "n" and hit Enter.

Note: Running the "hotplug.sh" script should copy the file "nomad.rules" to where it's supposed to go. If it doesn't, you can simply copy the file manually:
```
sudo cp libmtp.rules /etc/udev/rules.d/
```8. Go to the folder where you extracted libnjb
```
cd ..
cd libnjb-2.2.5
```12. Compile libnjb
```
./configure --prefix=/usr --enable-hotplugging
sudo make
sudo checkinstall --dpkgflags=--force-overwrite
```Just as with libmtp, hit Enter past any of the prompts to choose the default answer, give it a description, then hit Enter two more times to install it.

13. In the libnjb folder, there's another udev ruleset file called nomad.rules. If you're following this how-to then it is most likely because you have an MTP device. This file isn't as critical to you because libnjb has not been updated recently and does not account for any of the newer MTP devices. It does however have some older (non-MTP) devices in it that are not listed in libmtp.rules (libmtp assumes you've already installed libnjb with the corresponding ruleset and reduces redundancy), so it's still a good idea to install the file so you can still use Gnomad if you happen to have one of those devices. The --enable-hotplugging flag passed to libnjb enables hotplug support and creates a script file called "hotplug.sh" to install the udev ruleset. Just as before with lbmtp.rules, to copy nomad.rules file to where it needs to go, type
```
sudo bash hotplug.sh
```Once again you should see an output telling you that you have udev, and that the udev ruleset was installed. You'll also get a prompt asking you if you want the old hotplug support, type "n" and hit Enter.

Note: Just as with "libmtp.rules", running the "hotplug.sh" script should copy the file "nomad.rules" to where it's supposed to go, but some people have had problems with this and the file doesn't copy correctly. If you encounter this situation, simply copy the file manually:
```
sudo cp nomad.rules /etc/udev/rules.d/
```14. Last but not least, go to the folder you extracted Gnomad to to compile it

```
cd ..
cd gnomad2-2.8.10
```15. Compile and install Gnomad
```
./configure
sudo make
sudo checkinstall
```Once again, hit Enter past all prompts to choose default answers, give it a description, and hit Enter two more times to install Gnomad.

16. Restart udev so that the rulesets we copied over earlier will be applied:
```
sudo /etc/init.d/udev restart
```17. At this point all three packages are should have been installed. Start Gnomad by typing

```
gnomad2
```[SIZE=6]_**Adding the menu entry:**_[/SIZE]

Once you've verified that Gnomad works, you can take the following steps to add the menu entry. You should still be in the Gnomad directory where you just compiled from.

1. Copy the menu entry file and corresponding icon to their respective locations:
[LEFT]```
sudo cp gnomad2.desktop /usr/share/applications
sudo cp gnomad2-logo.png /usr/share/pixmaps
```[/LEFT]
 
2. Reload your menu and the entry should be there:

- If you're a Gnome user:
 ```
sudo killall gnome-panel 
```- If you're a KDE user:
[LEFT]```
kbuildsycoca --incremental 
```[/LEFT]

Now the menu entry should show up in your Multimedia group.

---

### Post by msak007 on 2006-06-18
This post is no longer relevant, see post # 1.

---

### Post by wastrel on 2006-06-19
Hey!  Thanks, I bought a Zen Micro today, (not the microphoto) and followed your instructions to install libmtp, libnjb and gnomad2.  

I've got it working now and am hoping the battery charge finishes soon...

My install notes:

I had to apt-get install libusb-dev.

There was no /etc/udev/rules.d/nomad.rules, and I had to run gnomad2 as root.  I did use --enable-hotplugging when building libnjb.

To fix this, so I don't need root to run gnomad2, I created /etc/udev/rules.d/45-libnjb.rules (as root)  and added the lines:

```
 
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libnjb_rules_end"

SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411e", GROUP="plugdev", MODE="0660"
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413c", GROUP="plugdev", MODE="0660"
# Creative Nomad Jukebox Zen MicroPhoto <-- MINE
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", GROUP="plugdev", MODE="0660"

LABEL="libnjb_rules_end"

```

I used the vendor & device ID's from the lsusb entry for my device.  This allows me to launch gnomad2 as my user, & everything seems to be working so far...  I'll update if I run into any problems.

Thanks for your post, it was very helpful!

---

### Post by msak007 on 2006-06-19
I'm glad the how-to helped you! I struggled with it for a long long time and figured I'd  prevent others the frustration. Thanks for letting me know about the dependency issue you ran into as I couldn't remember everything that was needed. I forgot "libusb-dev" (as you mentioned above) and "libgtk2.0-dev". It's kind of hard to backtrack and think of everything when at the time all you can think of is getting it to work not making a how-to :). If I can get a list of all the dependencies / packages needed, maybe I'll revise this and make it a real how-to. 

Now as far as the nomad.rules file, it was supposed to be created by the [COLOR="Red"]--enable-hotplugging[/COLOR] flag according to the installation documentation. Maybe it's broken, but if that doesn't work type this in the console in the same folder you compiled from AFTER you've compiled:

```
sudo sh hotplug.sh
```

You'll get an output telling you that you have udev on the system, and a prompt asking if you want to install the old hotplug support. Type "n" and hit Enter. This will create the nomad.rules file that was supposed to be created during configure in the /etc/udev/rules.d folder. At that point, the file can be edited to add your MP3 player if it's not in the list. Alternatively, you can edit nomad.rules in the source folder before you run the hotplug script, following the other entries for a template, and add your device. Either way you do it it's the same net result. Interestingly, nomad.rules doesn't have any references to "plugdev" or any other groups, but the permissions are set to 666 so anybody can access the devices. Thanks again for letting me know it worked, hopefully others can get use out of it.

---

### Post by patatas21 on 2006-06-20
Does this include Creative Zen Neeon?

---

### Post by msak007 on 2006-06-20
I assume it should. I don't know much about the Neeon, but if it's a newer player then chances are it uses MTP / PlayForSure. If it doesn't, then you really don't need to compile libmtp or Gnomad 2.8.5. The version of Gnomad in the repositories may suffice as the only difference with the newest version is that it supports MTP. You can also grab libnjb5 from the repositories. I couldn't find anything on Creative's page indicating whether or not this is an MTP / PlayForSure MP3 player or not.

---

### Post by wastrel on 2006-06-20
Here's an update after using gnomad2 and my player for a bit.  gnomad2 is working and can talk to my micro; I can transfer music over and edit track info like album, track number etc. 

However, [COLOR="Red"]playlists and data file transfer are not supported with MTP devices[/COLOR].  This is a big downside to me -- I would really like to be able to manage playlists in gnomad2 rather than in the tiny screen on my player.  

Any idea on the status of playlist and data support?  I may try to downgrade my firmware if this isn't on the near horizon.  Is this a gnomad2 or a libmtp or a libnjb issue?  Is there anything I as a user can do to assist in the process?

---

### Post by msak007 on 2006-06-20
I never really paid attention to that feature because I don't use playlists much, I just used it to copy files. Unfortunately that's a limitation explicitly stated on Gnomad's front page:

> 2006-03-22: Gnomad 2.8.3 is released. This version includes MTP support for a select number of Creative devices, provided that libmtp 0.0.2 is properly installed on your system. [COLOR="Red"]Only track transfers work on MTP, no data files or playlists, sorry.[/COLOR] (You might have to run this as root to get it to work with MTP devices.)

I know that sucks but I see it as a minor annoyance, not a major showstopper. libmtp is in its very early stages and is not quite as mature as libnjb, so if I had to guess I'd say the limitation is libmtp, not gnomad or libnjb. I tried kzenexplorer, but that hasn't been updated since last year and doesn't see the player. I'm using KDE so I also tried the njb kio slave for Konqueror - that doesn't work either and doesn't see the player. So at this point in time Gnomad is the only app I know of that will even see these players. I think the only 2 solutions are a.) deal with that limitation and manually edit playlists on the player, or b.) downgrade your firmware to make it fully functional. It's all a matter of personal preference and what your needs and priorities are. I'll deal with it for now and hope it gets better soon.

---

### Post by wastrel on 2006-06-20
You're right it was a limitation of libmtp.  I noticed in the gnomad2 changelog that playlists are now supported in the development version, so I installed gnomad 2.8.6 and libmtp from CVS and can now manage playlists!

edit: s/from/and/

---

### Post by msak007 on 2006-06-21
Well I'm glad you got it worked out without having to downgrade the firmware. I didn't think about a CVS version as I rarely / never use CVS, but it's good to hear that capability is in the works for a future release. I read the changelog and saw that playlist support was added on 6/16. If that's the case, then maybe it was a limitation in gnomad after all. Did you also install a newer (CVS) version of libmtp?

---

### Post by wastrel on 2006-06-21
Yes, I did have to install the CVS version of libmtp - gnomad2 CVS wouldn't compile without it because libmtp0.0.8 didn't have playlist stuff it needed.

So really it was both gnomad2 and libmtp but libmtp needed playlist support before gnomad2 could use it.

---

### Post by Cjattwood on 2006-06-21
Hi all, this is my first post here, and I'm pretty desperate to get my Zen MicroPhoto working, or else I'll most likely have to reinstall Windows. Basically, I've just moved from WIndows to Linux, and kind of need help with all the steps presented here. If the topic parent, or anyone can please help me step by step, that would be incredible. Thanks in advance to any help or advice.

---

### Post by wastrel on 2006-06-21
[QUOTE=Cjattwood]Hi all, this is my first post here, and I'm pretty desperate to get my Zen MicroPhoto working, or else I'll most likely have to reinstall Windows. Basically, I've just moved from WIndows to Linux, and kind of need help with all the steps presented here. If the topic parent, or anyone can please help me step by step, that would be incredible. Thanks in advance to any help or advice.[/QUOTE]

Here's something to get you started.  Give this a try and post here if you run into problems.  You'll need to be able to work at the linux command line - if you're not sure how to do that it's going to be a bit of a learning curve.  

Here's info on using the command line:

[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

First you'll need to get your build environment set up.  Install the compiler and necessary libraries:
```
sudo apt-get install build-essential libgtk2.0-dev libusb-dev libid3tag0-dev libxml-perl
```

Next go to these webpages and download these files (or the most recent version):
[COLOR="DarkSlateGray"]gnomad2-2.8.5.tar.gz[/COLOR] from [http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)
[COLOR="DarkSlateGray"]libnjb-2.2.5.tar.gz[/COLOR] from [http://libnjb.sourceforge.net/](http://libnjb.sourceforge.net/)
[COLOR="DarkSlateGray"]libmtp-0.0.8.tar.gz[/COLOR] from [http://libmtp.sourceforge.net/](http://libmtp.sourceforge.net/)

Extract the files with tar zxvf filename.tar.gz at the command line -- this will create a folder with the filename minus the .tar.gz

Starting with libmtp-0.0.8/ cd (change directory) into the folder, and run these commands one at a time:
```
./configure --prefix=/usr
make
sudo make install
```

Next go to the libnjb-2.2.5 folder and do:
```
./configure --prefix=/usr --enable-hotplugging
make
sudo make install
```

Finally the gnomad2-2.8.5 folder:
```
./configure
make
sudo make install
```

If everything worked you sould now be able to run gnomad2 as root, type sudo gnomad2 at the command line.  

If you get stuck, let us know where.  If you get it working, let us know and well help you fix it so you don't have to run gnomad2 as root.

---

### Post by msak007 on 2006-06-21
First of all welcome to the Forums and to the world of Linux! I made the switch a couple months back and haven't looked back. You'll be much happier with Ubuntu, especially if you can get all your hardware working. wastrel pretty much summed up the installation procedure, but I would suggest one change. The normal "make install" will install the files, but doesn't give you an easy way to uninstall and remove all the files unless an uninstall script is included (it usually isn't). Instead of using "make install", use [COLOR="Red"]"checkinstall"[/COLOR] instead. It makes a .deb (install package) out of the files and installs it, making it easier for you to uninstall later if you want to either through apt or Syanptic / Adept. This will also make for easier reinstallation later if you want to without having to recompile everything, and you can copy the .deb out of the folder you just compiled from to a backup location.

First open a terminal and type:

```
sudo apt-get install checkinstall
```

Then, follow the compile / make procedure wastrel outlined, using

```
sudo checkinstall
```

instead of

```
sudo make install
```

Checkinstall will ask you a few questions, usually you can just hit Enter and choose the default answer. The last thing you have to do is give your package a description (so you know what the package is if you run across it in Syanptic / Adept) and hit Enter, and then it will install. If you have any questions or run into any problems don't hesitate to ask we'll try to help you out.

---

### Post by Brokenrgv on 2006-06-21
thanks again for all this help, i follow these directions step by step and stll have problems when i check install after making in gnomad2's dir i get this error

Copying documentation directory...
/var/tmp/oYJUhAUkXkTIoYTYLhJi/installscript.sh: line 13: 11665 Segmentation faul t      mkdir -p "/usr/share/doc/gnomad2-2.8.5"

****  Installation failed. Aborting package creation.

Cleaning up...OK

what does this mean?

---

### Post by msak007 on 2006-06-22
Just out of curiosity, what version of checkinstall do you have installed? The only thing I could find on that specific error was in [this]("http://ubuntuforums.org/showthread.php?t=107089") thread, and it indicates that an older version of checkinstall had this bug but version 1.6 doesn't. It was posted back in December so I'm not sure how much has changed since then, and I'm not at home right now so I can't verify which version I have installed but I'll check later. The [Ubuntu Packages]("http://packages.ubuntu.com/dapper/admin/checkinstall") site lists the current version in Universe as 1.5.3, and that may be a version that has the bug. First thing I always do is enable extra repositories and update my system, so maybe there's a newer version that isn't in the default Dapper repositories? I used [UbuntuGuide.com]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") as a reference so try enabling the extra repositories (if you haven't done so already) and upgrade everything. Try that and see if it works.

---

### Post by wastrel on 2006-06-22
[QUOTE=Brokenrgv]thanks again for all this help, i follow these directions step by step and stll have problems when i check install after making in gnomad2's dir i get this error

Copying documentation directory...
/var/tmp/oYJUhAUkXkTIoYTYLhJi/installscript.sh: line 13: 11665 Segmentation faul t      mkdir -p "/usr/share/doc/gnomad2-2.8.5"

****  Installation failed. Aborting package creation.

Cleaning up...OK

what does this mean?[/QUOTE]


Since this is a problem with checkinstall you can use my method to install it - "make install".  If you're worried at all about uninstalling I checked & there is an uninstall script for gnomad2 - you can just do make uninstall to remove it.

---

### Post by Cjattwood on 2006-06-22
Thanks so much for your help so far, I'm up to the "make" command for gnomad2, however when I do this I get this message:

"make: *** No targets specified and no makefile found.  Stop."

Any idea what I might be doing wrong? I'm almost there :-D

EDIT: Actually, upon checking ./configure again I get this error message right at the end, don't know if it affects anything or not:

"checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool"

---

### Post by Brokenrgv on 2006-06-22
yep same prob here, itl work one day im sure this gnomad2
Cjattwood check out first page top about installing this it mentions this perl thing thats needed to be installed just tryed it and my god it installed finally to quote
"2. You also need libnjb. I know the repositories have it, but for some reason when I was installing gnomad it couldn't find the pkgconfig file for libnjb. It just didn't exist anwyhere on my hard drive. Easiest solution was just to download and compile from source. Get it here (latest version as of this writing is 2.2.5). The only dependency I ran into here was needing the xml parser, so install "libxml-perl" (will also install the needed parser)."

thank goodness it finally worked connected now to my $500 mp3 player for the first time thanks heaps to all that persisted and helped out explaining this to me :) very happy

dam now im getting segmentation faults when trying to transfer files, transfered one successfully

---

### Post by msak007 on 2006-06-22
Cjattwood, you're missing the package "libxml-perl". Install that and you should be OK when you configure.

Brokenrgv, I'm glad you finally got it working. I was going to suggest just using the normal make install as wastrel suggested if checkinstall failed, but didn't know it had it's own uninstall script so it all works out. You should still try to get checkinstall working though, because not all packages have uninstallers and it's a very useful tool. On that note, I just checked and I have version "1.5.3-3ubuntu2", the same version listed on the packages page so there goes my theory. If you have the same version, the only thing I can suggest is reinstalling. I use it all the time and have never run into that error.

---

### Post by wastrel on 2006-06-22
[QUOTE=Cjattwood]
EDIT: Actually, upon checking ./configure again I get this error message right at the end, don't know if it affects anything or not:

"checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool"[/QUOTE]

Oops!  Sorry, I missed that one (libxml-perl)... I added it to my post above for future reference. :cool:

---

### Post by wastrel on 2006-06-23
gnomad2 version 2.8.6 has been released. 

[http://sourceforge.net/project/showfiles.php?group_id=65573](http://sourceforge.net/project/showfiles.php?group_id=65573)

Edit:  

You'll also need libmtp 0.0.9:

[http://sourceforge.net/project/showfiles.php?group_id=158745](http://sourceforge.net/project/showfiles.php?group_id=158745)

---

### Post by RobNyc on 2006-06-23
I just got a Zen Vision:M yesterday

---

### Post by Cjattwood on 2006-06-23
YES! It worked, thanks for all your help, I love you guys :)

---

### Post by Brokenrgv on 2006-06-23
anyone know how to copy music back out of these devices ?

---

### Post by cbudden on 2006-06-23
[QUOTE=Brokenrgv]anyone know how to copy music back out of these devices ?[/QUOTE]

Just select the music you want on the right, right click and click transfer.

---

### Post by Brokenrgv on 2006-06-23
gees is it that simple, didnt try that thanks :)

---

### Post by Cjattwood on 2006-06-24
Okay, I've just finished making MP3's from my FLAC music collection, and they're all transferred onto the player... it works fantasticly well, and editing files on the Zen MicroPhoto is awesome. Now, I just have one last thing to resolve; not having to run Gnomad2 as root (while it's not a huge inconveniance, I'd like to get it fixed). Can anyone help me with this last step?

---

### Post by electrosoccertux on 2006-06-24
Just in case anyone was having trouble like I was, it seems (in gnomad2-2.8.1 at least) you can't transfer a folder, you have to open the folder and select all the songs and then move it to your Nomad Jukebox.

---

### Post by jinx099 on 2006-06-24
just got this error trying to run gnomad2:

```
error while loading shared libraries: libmtp.so.1: cannot open shared object file: No such file or directory
```

I just compiled and installed libmtp0.0.9 and gnomad2.8.6

EDIT: FIXED!

I just reconfigured my libmtp with the --prefix=/usr
Also got it to run without being root from the second post.  

Thanks a lot guys!

---

### Post by OrganicPanda on 2006-06-24
yay it worked, more and more hardware compatibility everyday, god i love this os

---

### Post by msak007 on 2006-06-24
Glad to hear that more and more people are able to get this working! I never knew that this was something that nobody had written a how-to on so I'm glad to give back for once instead of being the one needing the help :) I know that wastrel already summed it up in one of his posts but I think I'm going to go back to my original post and make this an official how-to to make it easier to find the info in the first post since a lot of people are actually using it. If anybody has any extra tips or things they'd like to add please let me know.

> just got this error trying to run gnomad2:

Code:

error while loading shared libraries: libmtp.so.1: cannot open shared object file: No such file or directory
jinx0999 that's exactly the error I ran into when I first started, which is why I suggested configuring with a --prefix=/usr to avoid having to create symlinks to the files. But I see that you got that figured out now :)

> Now, I just have one last thing to resolve; not having to run Gnomad2 as root (while it's not a huge inconveniance, I'd like to get it fixed). Can anyone help me with this last step?
Cjattwood, getting gnomad to work without root is relatively simple. The reason you're having to run it as root is because your device is not explicitly defined in the udev ruleset, and there's nothing telling the system that a normal user can access it. I put this info in my 2nd post but it was a little scattered because I didn't know what was going on, so I'll sum it up for you here.  I believe you mentioned you have the Zen MicroPhoto, the same one that I was working with. If it is then the output of lsusb should give you something similar to this:

```
 Bus 003 Device 017: ID 041e:413c Creative Technology, Ltd Zen MicroPhoto
```

The most important thing to pay attention to is the device code - in this case 413c. The first thing you need to do is open a terminal and type:

```
 cd /etc/udev/rules.d/
```

If libnjb was compiled correctly with --enable-hotplugging, there should be a file called "[COLOR="Red"]nomad.rules[/COLOR]" in that folder. You're only making a small change, but I always recommend backing everything up before making any changes. The next thing you need to type is

```
sudo cp nomad.rules nomad.rules_backup
sudo pico nomad.rules
```

I prefer pico for a text editor because it's a quick and easy editor, and I can do it within the console. You can substitue your favorite editor in that line to edit the file. Once you open the file, you'll see all the devices defined by default. You can use any of them as templates, but skip ahead to line 57 because that's the one most similar to yours. You'll see a 2 lines that read:

```
# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411e", MODE="666"
```

Copy those 2 lines, and paste them below the 2nd line. Then edit them to be specific to your device

```
# Creative Nomad Jukebox Zen [COLOR="Red"]MicroPhoto[/COLOR]
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="[COLOR="Red"]413c[/COLOR]", MODE="666"
```

Save the file, then restart udev:

```
sudo /etc/init.d/udev restart
```

At that point when your device is plugged in, it'll be accessible by anybody. Gnomad should no longer have to be run as root :) Enojy!

---

### Post by OrganicPanda on 2006-06-25
with reference to:
[QUOTE=msak007]
If libnjb was compiled correctly with --enable-hotplugging, there should be a file called "[COLOR="Red"]nomad.rules[/COLOR]" in that folder. You're only making a small change, but I always recommend backing everything up before making any changes. The next thing you need to type is

```
sudo cp nomad.rules nomad.rules_backup
sudo pico nomad.rules
```
[/QUOTE]

if i havent got a nomad.rules, which i don't, does that mean libnjb was not correctly installed because im sure i passed it '--enable-hotplugging' as directed, anyway thats neither here nor there, is there anyway to maybe remove then replace libnjb? would that work?

edit it turns out i used checkinstall so i removed via synaptec and then tryed again using ./configure --prefix=/usr --enable-hotplugging but i still have no nomad.rules, it's upsetting me .... lol

---

### Post by Cjattwood on 2006-06-25
[QUOTE=OrganicPanda]with reference to:


if i havent got a nomad.rules, which i don't, does that mean libnjb was not correctly installed because im sure i passed it '--enable-hotplugging' as directed, anyway thats neither here nor there, is there anyway to maybe remove then replace libnjb? would that work?[/QUOTE]

I just followed msak007's brilliant help and I also found I did not have nomad.rules. However, all you need to do is open Pico/Gedit/etc and save a file called nomad.rules in the correct folder, and then put in the values that msak007 gave in his previous post, and everything works! Thanks for all your help msak007, you're the best!

---

### Post by OrganicPanda on 2006-06-25
wow thank you Cjattwood that did indeed work, thanks to everyone in this thread, it was very helpful

---

### Post by msak007 on 2006-06-25
You're welcome guys, I just love it when stuff works and people have 1 less reason to boot into the *other* OS ;). As far as nomad.rules goes, I've found that for some reason --enable-hotplugging doesn't always work. Actually, I don't think it works at all :). Anyway if you find that nomad.rules is not in the /etc/udev/rules.d folder, here's what you need to do. Cjattwood was on the right track, but there's an easier and more appropriate way to get the file in the right folder.

First open a terminal and go to the folder that you compiled libnjb from. You'll find nomad.rules in there. Edit it to add your device as mentioned in my previous post. Then, type this:

```
sudo sh hotplug.sh
```

You'll get an output telling you that you have udev, and that the appropriate rules were installed. It'll ask you if you want the old hotplugging support installed as well, simply type "n" and hit Enter. nomad.rules should now be in the rules.d folder with your device already in the list and everything should work the way it's supposed to.

---

### Post by Brokenrgv on 2006-06-26
anyone else have no progress bar happening with transfers just an empty box, it still transfers fine just no visual indication. very small gripe.

---

### Post by ShiftyPowers on 2006-06-27
i am so glad this works....this is awesome, no more booting into windows just to transfer things to my Creative Vision M!!!

---

### Post by msak007 on 2006-06-28
First post has been edited to be a complete step-by-step guide on getting everything compiled and installed. Let me know what you guys think.

---

### Post by advance on 2006-06-28
Hi,
Thanks for the very informative post, I got everything up and running with my Zen Touch 40GB...I ran Gnomad, It recognized the device and scanned the tracks properly, however when I attempted to copy an MP3 to it, I got this message:


advance@nicksbox:~$ gnomad2
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen Touch
Transferring MTP track...
LIBMTP_Update_Track_Metadata(): could not set use count
LIBMTP_Send_Track_From_File_Descriptor: error setting metadata for new track
Error sending file "/tmp/fileKOo1Xt/07 - Assasin.mp3" to MTP device!



And nothing was transferred :(
I did double check that the write protection was off on the device, so that's not it...


***update***
I searched through the libmtp source code for "use count" and found that in libmtp.c there's a spot that says:

```
  // Update use count, set even to zero if desired.
ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount);
    if (ret != 0) {
      printf("LIBMTP_Update_Track_Metadata(): could not set use count\n");
      return -1;
    }

```

well, i assume that the zen touch doesn't keep track of use counts....sooo....
i tweaked the code to read:

```
  // Update use count, set even to zero if desired.
[COLOR="Red"]if (metadata->usecount != 0) {[/COLOR]
  ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount);
    if (ret != 0) {
      printf("LIBMTP_Update_Track_Metadata(): could not set use count\n");
      return -1;
    }
[COLOR="Red"]}[/COLOR]

```


recompiled libmtp and now...voila! the tracks transfer flawlessly :)

---

### Post by dmfrey on 2006-06-28
Thanks for the great how-to.  I was up and running in 15 minutes with my Creative Zen Micro.

---

### Post by msak007 on 2006-06-28
> **advance]
I searched through the libmtp source code for "use count" and found that in libmtp.c there's a spot that says:

```
  // Update use count, set even to zero if desired.
ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount) said:**
> if (metadata->usecount != 0) {[/COLOR]
  ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount);
    if (ret != 0) {
      printf("LIBMTP_Update_Track_Metadata(): could not set use count\n");
      return -1;
    }
[COLOR="Red"]}[/COLOR]

```


recompiled libmtp and now...voila! the tracks transfer flawlessly :)

How in the world did you come up with that? :) I have no idea what "use count" is or what it's for, but I'm glad you got it working. I would've never thought of adding that line. I added it to my libmtp.c, recompiled, and tried again - it didn't seem to affect my device which was already working and I was still able to transfer files. You should email the developer and let him know that the line you added allowed your device to work and see if it can be added to the code.

---

### Post by monomaniacpat on 2006-06-30
Great guide. However, having successfully installed all this the other day under an upgraded breezy>dapper setup, I today tried again and get this error:

```
patrick@patrick:~/downloads/libnjb-2.2.5$ gnomad2
Found non-autodetected device "Creative Zen Micro (MTP mode)" on USB bus...
usb_claim_interface(): Operation not permitted
```

The last time I got it working was using the old HowTo (needing to type sudo out each time). Can you tell me what I'm doing wrong? Here's my nomad.rules:

```
# nomad.rules a udev rules file for NOMAD jukeboxes.
# Put this file in /etc/udev/rules.d
#
# This script sets the mode of the libnjb accessible devices
# to "666" meaning "read and write for everyone", really a security
# risk. Therefore think about it before applying this to your system.
# However since there are so many ways of managing permissions for
# devices we have no better idea.
#
# If you have a desktop user group, set MODE to "660" and tag
# on GROUP="jukebox" after the MODE rule. Subsitute GROUP 
# "jukebox" for a good value for your system, this group should 
# include desktop users (see your /etc/group). 
#
# You can add a RUN="..." attribute to run some arbitrary script
# when the device is plugged in.

# This rule, if enabled, creates a device node in the hierarchy
# /dev/bus/usb. This is already part of Fedora Core but I
# don't know about other distributions. Notice that this will
# require libusb to be patched too, or use libusb-0.1.12 or 
# higher, or it just won't work.
#
# /dev/bus/usb identical to that of /proc/bus/usb. Most distributions
# using udev already has a rule like this.

# ACTION=="add", SUBSYSTEM=="usb_device", \
  PROGRAM="/bin/sh -c 'K=%k; K=$${K#usbdev}; \
  printf bus/usb/%%03i/%%03i $${K%%%%.*} $${K#*.}'", \
  NAME="%c", MODE="0644"

# Old erroneous rule used for debug purposes.
# ACTION=="add", SUBSYSTEM=="usb_device", PROGRAM="/bin/sh -c 'X=%k X=$${X#usbdev} B=$${X%%%%.*} D=$${X#*.}; echo bus/usb/$$B/$$D'", SYMLINK+="%c", RUN="/home/linus/bin/boxplugin %c"

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="nomad_rules_end"

# Creative Nomad Jukebox
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="0222", MODE="666"
# Creative Nomad Jukebox 2
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4100", MODE="666"
# Creative Nomad Jukebox 3
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4101", MODE="666"
# Creative Nomad Jukebox Zen
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4108", MODE="666"
# Creative Nomad Jukebox Zen USB 2.0
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="410b", MODE="666"
# Creative Nomad Jukebox Zen NX
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4109", MODE="666"
# Creative Nomad Jukebox Zen Xtra
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4110", MODE="666"
# Dell Digital Jukebox
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4111", MODE="666"
# Creative Nomad Jukebox Zen Touch
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411b", MODE="666"
# Creative Zen (Zen Micro variant)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411d", MODE="666"
[B]# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", MODE="666"[/B]
# Second Generation Dell Digital Jukebox
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4126", MODE="666"
# Dell Pocket DJ
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4127", MODE="666"
# Creative Zen Sleek
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4136", MODE="666"
# Third Generation Dell Digital Jukebox
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="412f", MODE="666"

LABEL="nomad_rules_end"

```

I'm going to try uninstalling and starting from scratch.

---

### Post by msak007 on 2006-06-30
Hmm that's odd. If the output of lsusb gave you that Vendor / Product ID that you have bolded, then it should work. Where is the nomad.rules file that you posted the contents of? Is it still in the libnjb folder, or did you run the hotplug.sh script to put it in /etc/udev/rules.d?

---

### Post by monomaniacpat on 2006-06-30
I did everything you suggested for a second time and get the same output. I can run it using sudo now, though (perhaps I didn't check last time). Anyway, had a look at the nomad.rules in the location you specified and whilst present, it wasn't edited in the way I had done it... :-?

So I put the right number in and nothing changed... #-o 

[size=0]here's lsusb:

```
patrick@patrick:~/downloads/gnomad2-2.8.6$ lsusb
Bus 001 Device 007: ID 041e:4130 Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 002: ID 045e:00e5 Microsoft Corp.

```

And here's my nomad rules, as found in /etc/udev/rules.d/:

```
# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", MODE="666"
```[/size]

EDIT: working now... I guess the problem was that the hotplug.sh command didn't work :-? Put a note in the first post so that people know the intended destination.

---

### Post by msak007 on 2006-06-30
Thanks, I'll add a note to my instructions. It's weird that it didn't go where it was supposed to go though. The --enable-hotplugging flag creates that script, and when the script is run it's supposed to detect your hotplug system and copy the file appropriately. You did mention that you upgraded from Breezy --> Dapper, so maybe it detected the old hotplug support instead of udev? What was the output of

```
sudo sh hotplug.sh
```? It's supposed to mention udev and ask you if you want the old hotplug support installed after it copies the rules file to the folder. If it didn't, that could be the problem. Delete nomad.rules from /etc/udev/rules.d, run the command above, and check to see if the file was created again.

---

### Post by monomaniacpat on 2006-06-30
I was not running an upgrade when I got it working today. The output was as-expected (asked about old hotplug).

---

### Post by advance on 2006-06-30
i've posted the bug with libmtp.c regarding the use count error on the libmtp page on sourceforge.

---

### Post by oolunchbox on 2006-06-30
I had a little trouble compling libnjb but managed to get it working with libnjb1 from teh repository (on a Zen Touch). Other than that Awesome howto! Thanks!

---

### Post by msak007 on 2006-06-30
[QUOTE=monomaniacpat]I was not running an upgrade when I got it working today. The output was as-expected (asked about old hotplug).
[/QUOTE]

Did you delete nomad.rules from /etc/udev/rules.d before running the script again, and if you did did it reappear when you ran it?

[QUOTE=oolunchbox]I had a little trouble compling libnjb but managed to get it working with libnjb1 from teh repository (on a Zen Touch). Other than that Awesome howto! Thanks![/QUOTE]

That's funny because I had trouble compiling Gnomad with the libnjb from the repositories, which is why I recommended installing it from source. It'd be a lot easier if all you had to comile was libmtp and Gnomad, because there's really nothing new with libnjb as far as I can tell if you compile it from source. If it worked for you with the version from the repositories that's great, but just out of curiosity what kind of problems did you run into? I'd like to know so that I can maybe edit the instructions with possible workarounds for people who run into problems.

---

### Post by TFX360 on 2006-07-01
Hello all,


All works like a charm up to compiling gnomad-2.2.8.6

in gnomad-2.2.8.6
./configure

gnomad2 2.8.6
Configuration :
---------------

 Source code location .: .
 C Preprocessor .......: gcc -E
 C Compiler ...........: gcc -g -O2
 C Linker .............: gcc
 GTK+ version .........: 2.8.18
 libgnomeui version....: NOT USED
 libnjb version........: 2.2.5
 libmtp version........: 0.0.9
 id3tag version........: 0.15.0b
 Install path .........: /usr/local

 Now type 'make' to build gnomad2 2.8.6,
 and then 'make install' for installation.

make (or sudo make, or sudo -i make)
I get the following error/output:

collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/tfx/gnomad2-2.8.6/src'
make: *** [all-recursive] Error 1

Please help, I'm at my wits end here :oops: 

Saw ld standig there tried running sudo ldconfig, get no output...

lsusb:

Bus 001 Device 002: ID 041e:413c Creative Technology, Ltd Zen MicroPhoto
Bus 001 Device 001: ID 0000:0000

Content added in file 45-libnjb.rules:

# Creative Nomad Jukebox Zen MicroPhoto
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413c", GROUP="plugdev", MODE="0660"

Thanks in advance,


TFX.

Running Dapper btw.

---

### Post by ivago on 2006-07-02
Hi,

great howto but I have some questions...

I'm using the Zen Vision M and tried transferring some movies with gnomad2. Now it seems that mpeg files are playing OK while Xvid Divx files seem to create an error claiming the format isn't supported. Altough the same files play flawlessy when transferred via the windows software from creative.

Any ideas why this is happening? I have all codecs installed in dapper but that hasn't probably anything todo with it anyway.

---

### Post by msak007 on 2006-07-03
[QUOTE=TFX360]Hello all,


All works like a charm up to compiling gnomad-2.2.8.6

in gnomad-2.2.8.6
./configure

gnomad2 2.8.6
Configuration :
---------------

 Source code location .: .
 C Preprocessor .......: gcc -E
 C Compiler ...........: gcc -g -O2
 C Linker .............: gcc
 GTK+ version .........: 2.8.18
 libgnomeui version....: NOT USED
 libnjb version........: 2.2.5
 libmtp version........: 0.0.9
 id3tag version........: 0.15.0b
 Install path .........: /usr/local

 Now type 'make' to build gnomad2 2.8.6,
 and then 'make install' for installation.

make (or sudo make, or sudo -i make)
I get the following error/output:

collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/tfx/gnomad2-2.8.6/src'
make: *** [all-recursive] Error 1[/QUOTE]

Well I can't really decipher what that error is about so hopefully someone a little more knowledgeable can help you out there. I do have a few suggestions / questions though. 

1. The "collect2" error is a GCC linking error. Which version of GCC do you have installed? In the terminal type

```
gcc -dumpversion
``` to see which version you have installed. I'm using gcc 4.0.3 (gcc-4.0 from the repos). Did you have problems compiling libnjb and libmtp?

2. Did you make sure you installed all the dependencies from my first post? 

3. If you previously installed Gnomad from the repositories, but then uninstalled it without purging it may have left some files behind. 

I really wish I could help you more but I'm relatively new to Linux in general. Try those suggestions and let me know what happens.

---

### Post by TFX360 on 2006-07-04
[QUOTE=msak007]Well I can't really decipher what that error is about so hopefully someone a little more knowledgeable can help you out there. I do have a few suggestions / questions though. 

1. The "collect2" error is a GCC linking error. Which version of GCC do you have installed? In the terminal type

```
gcc -dumpversion
``` to see which version you have installed. I'm using gcc 4.0.3 (gcc-4.0 from the repos). Did you have problems compiling libnjb and libmtp?

2. Did you make sure you installed all the dependencies from my first post? 

3. If you previously installed Gnomad from the repositories, but then uninstalled it without purging it may have left some files behind. 

I really wish I could help you more but I'm relatively new to Linux in general. Try those suggestions and let me know what happens.[/QUOTE]

________________________________________

Thanks for your reply, was hoping you would.
I'm also quite new to linux, not using but compiling/making.

Thanks for the suggestions.

1. GCC is version 4.0.3 here!

2. I double checked your dependencies, all there.
Is it normal that the libgnomeui isn't used? (See my ./configure in my previous post)

3. I did, will try to uninstall/purge all and try again.


Thanks for the help!


Greetings!


TFX.

---

### Post by Brokenrgv on 2006-07-05
[QUOTE=ivago]Hi,

great howto but I have some questions...

I'm using the Zen Vision M and tried transferring some movies with gnomad2. Now it seems that mpeg files are playing OK while Xvid Divx files seem to create an error claiming the format isn't supported. Altough the same files play flawlessy when transferred via the windows software from creative.

Any ideas why this is happening? I have all codecs installed in dapper but that hasn't probably anything todo with it anyway.[/QUOTE]

i use libmtp-0.0.9 to transfer vids to my ZVM i think theres a thread that teaches you how to go about it, works really good puts the vid in "Video" folder and everything 
link          [http://www.ubuntuforums.org/showthread.php?t=135845](http://www.ubuntuforums.org/showthread.php?t=135845)

---

### Post by devan on 2006-07-06
great howto! quick question for you guys. compiling everything went through without a hitch. when i type in "gnomad2" i get:

```
Autodetected device "Second generation Dell DJ" (VID=041e,PID=412f) is known.
PTP: Opening session
Connected to MTP device.
```

And i think all is fine and dandy. When gnomad2 opens tho, it asks me to choose a device, and the only option is Third Generation Dell DJ. When i choose it and hit OK it says, "Could not open jukebox. usb_set_configuration: Device or resource busy.

Any idea why its wanting me to pick third gen when i have 2nd gen, and it finds it fine when you first start the program?

---

### Post by vladdythephotogeek on 2006-07-06
> **msak007 said:**
> If you have a newer Creative Jukebox / Zen or Dell DJ MP3 player, chances are it is using Micro$oft's new MTP / PlayForSure protocol. When you plug your device into a USB port, you won't get a prompt or window asking you what you want to do. While it is detected as a USB device, it is not automatically mounted as a device to transfer files to because MTP is not natively supported. Fortunately, the MTP specifications are publicly available and some libs were written to interface with the devices. Follow this guide and you'll be able to transfer / edit MP3s and playlists to your Creative Jukebox / Zen using Gnomad (no file data transfer yet, only MP3s).

1. To prepare your system for the installation, you need to install several packages to resolve dependencies. Open a terminal and type

```
sudo apt-get update
sudo apt-get intall build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev [COLOR="Red"]checkinstall[/COLOR]
```

Checkinstall is optional but I highly recommend it because it makes .debs and installs them, making uninstallation easier using apt / Syanptic / Adept.

2. Download the required packages. I find it easy to work from the Desktop but you can choose any folder you want:

[libmtp 0.0.9]("http://prdownloads.sourceforge.net/libmtp/libmtp-0.0.9.tar.gz?download")
[libnjb 2.2.5]("http://prdownloads.sourceforge.net/libnjb/libnjb-2.2.5.tar.gz?download")
[gnomad 2.8.6]("http://prdownloads.sourceforge.net/gnomad2/gnomad2-2.8.6.tar.gz?download")

3. Open a console and navigate to the folder where you downloaded the files (in my case Desktop) 

```
cd Desktop

```

4. Extract all 3 packages: 

```
tar -zxvf libmtp-0.0.9.tar.gz
tar -zxvf libnjb-2.2.5.tar.gz
tar -zxvf gnomad2-2.8.6.tar.gz
```

5. Go to the extracted libmtp folder.
```
cd libmtp-0.0.9
```

6. Compile libmtp
```
./configure --prefix=/usr
sudo make
sudo checkinstall
```

Hit Enter three times, give your package a description, then hit Enter twice. You'll get a confirmation that the package was installed telling you the name of the package, where the package was created, and how to uninstall it. 

7. Go to the folder where you extracted libnjb
```
cd ..
cd libnjb-2.2.5
```

There's a file called [COLOR="Red"]nomad.rules[/COLOR] in the folder. This is the file that will allow udev to grant you access to the device using Gnomad, so you need to make sure your device is explicitly supported. Otherwise, you will have to run Gnomad as root to interface with the device.

8. Type 
```
lsusb
``` and look for your device. You'll see an output similar to this:
```
Bus 003 Device 017: ID 041e:[COLOR="Red"]413c [/COLOR]Creative Technology, Ltd Zen MicroPhoto
```
Note your Product ID (highlighted in red, yours may be different) and jot that down.
 
9. Edit the file to see if your device is supported. I use [COLOR="Red"]pico[/COLOR] because it's quick & easy, but you can substitue your favorite text editor here:
```
sudo [COLOR="Red"]pico[/COLOR] nomad.rules
```

You'll see all the devices supported by default by libnjb. All the entries are pretty much the same with the exception of the Device Name and Product ID. A typical entry will look like this:

```
# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411e", MODE="666"

```

Creative's Vendor ID is [COLOR="Red"]041e[/COLOR], so all devices should be the same and all you need to pay attention to is the "SYSFS{idProduct}=="xxxx" part of that line. Look for a line with the Product ID that matches what you got from the output of lsusb. If your vendor ID output from lsusb is different, you need to replace the Vendor ID as well. Your device may or may not be listed here, so if it is skip to Step 11. Otherwise, continue to Step 10.

10. If your device is not listed, you need to add it to the list to allow anybody to access the device. Otherwise, as I previously stated, you'll have to run Gnomad as root to interface with the device. Simply copy any of the entries already in the file for one of the supported devices, paste the two lines at the end of the file, and modify them to match your device. Example:

I am using a Zen MicroPhoto, so I took the 2 lines that said

```
# Creative Nomad Jukebox Zen Micro
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411e", MODE="666"
```

copied / pasted them at the end of the file, modified them to match my device, and saved the file:

```
# Creative Nomad Jukebox Zen [COLOR="Red"]MicroPhoto[/COLOR]
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="[COLOR="Red"]413c[/COLOR]", MODE="666"
```

11. Compile libnjb
```
./configure --prefix=/usr --enable-hotplugging
sudo make
sudo checkinstall
```

Just as with libmtp, hit Enter past any of the prompts to choose the default answer, give it a description, then hit Enter two more times to install it.

12. The --enable-hotplugging flag passed to libnjb enables hotplug support and creates a script to install the udev ruleset. In the folder where you compiled from (the one you should still currently be in), there should be a file called [COLOR="Red"]hotplug.sh[/COLOR]. To copy nomad.rules file to where it needs to go, type

```
sudo sh hotplug.sh
```

You should see an output telling you that you have udev, and that the udev ruleset was installed. You'll also get a prompt asking you if you want the old hotplut support, type "n" and hit Enter.

13. Last but not least, go to the folder you extracted Gnomad to to compile it

```
cd ..
cd gnomad2-2.8.6
```

14. Compile and install Gnomad
```
./configure
sudo make
sudo checkinstall
```

Once again, hit Enter past all prompts to choose default answers, give it a description, and hit Enter two more times to install Gnomad.

15. At this point all three packages are should have been installed. Start Gnomad by typing

```
gnomad2
```

You can now transfer MP3s and playlists to / from your MP3 player, and edit ID3 tags and playlists right from Gnomad :).

NOTE: AFAIK, KZenExplorer and KIO Zen (KIO::slave for libnjb in KDE) do NOT support MTP, so this is the only way to transfer MP3s / playlists to the MTP devices. If you know otherwise or have gotten yours to work with one of these devices, please let me know.

Thank you for your help with this howto thus far. I have run into a bit of a snag and was hoping you could help me out. 

I have correctly installed (as per your exact instructions) up to the point where you do a ./configure in the gnomad directory.

At this point it fails claiming that I do not have the proper version of libnjb installed. It is saying that it sees version 2.0 when I explicitly downloaded and installed 2.2.5 along with several other packages in which I have verified that the correct version are indeed installed.

the error message is as follows:

checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

Requested 'libnjb >= 2.2.4' but version of libnjb is 2.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I have gotten farther than anytime before in trying to install this software, but this frusteration is about to make me scream.

Any help is greatly appriciated.
Best Regards,
Paul V

---

### Post by msak007 on 2006-07-06
@ devan
I personally don't have a Dell DJ so I'm not sure what you're seeing. What do you mean that Gnomad asks you to choose your device when you start it? When I start Gnomad, it immediately starts scanning the device and shows all the files / folders. Can you maybe get a screenshot of what you see when you start the app?

@ vladdythephotogeek
If you are not having luck getting Gnomad to install because of libnjb, and you've verified that you compiled it with ```
[COLOR="Red"]--prefix=/usr[/COLOR]
``` try adding the flag ```
--libdir=/usr/lib
``` when compiling Gnomad. If that fails, try ```
--with-libnjb-prefix=/usr
```

As a last resort if all that fails, uninstall the libnjb you compiled and try to add the one in the repos, which is currently 2.2.4. There isn't much that has changed with the new version and the only reason I included it in the instructions is because I personally had a problem compiling Gnomad with the libnjb from the repos. Someone else posted here that they had success using that version and didn't by compiling it manually, so if it works for you great. Type

```
sudo apt-get install libnjb-dev
``` which will also install package "libnjb5" (v2.2.4) from the repos. Hope this helps, let me know what happens.

---

### Post by devan on 2006-07-06
heres a screenshot of what it says.

---

### Post by vladdythephotogeek on 2006-07-06
> **msak007 said:**
> @ devan
I personally don't have a Dell DJ so I'm not sure what you're seeing. What do you mean that Gnomad asks you to choose your device when you start it? When I start Gnomad, it immediately starts scanning the device and shows all the files / folders. Can you maybe get a screenshot of what you see when you start the app?

@ vladdythephotogeek
If you are not having luck getting Gnomad to install because of libnjb, and you've verified that you compiled it with ```
[COLOR="Red"]--prefix=/usr[/COLOR]
``` try adding the flag ```
--libdir=/usr/lib
``` when compiling Gnomad. If that fails, try ```
--with-libnjb-prefix=/usr
```

As a last resort if all that fails, uninstall the libnjb you compiled and try to add the one in the repos, which is currently 2.2.4. There isn't much that has changed with the new version and the only reason I included it in the instructions is because I personally had a problem compiling Gnomad with the libnjb from the repos. Someone else posted here that they had success using that version and didn't by compiling it manually, so if it works for you great. Type

```
sudo apt-get install libnjb-dev
``` which will also install package "libnjb5" (v2.2.4) from the repos. Hope this helps, let me know what happens.

Thanks for your quick response.

I tried to do what you said, I verified that I used the --prefix=/usr and such with no luck.

I used the other flag when compiling gnomad with no luck.
I uninstalled libnjb (the one i compiled from source) and installed the apt-get 2.2.4. Gnomad was a no-go.

I'm thinking in one of my previous failed attempts on getting gnomad to work I hosed something up thus giving me these problems.

To be honest, I'm looking at doing a clean wipe and getting a fresh install and make sure I install all of my programs properly as this is frusterating the living daylights out of me.

Gosh, I love this OS, but this is just killing me.
THanks for your help, I really appriciate it.

Best Regards,
Paul V

---

### Post by msak007 on 2006-07-07
I know what you mean, it's frustrating when you're so close and can't get things working. I do have one last suggestion before you decide to format. When uninstalling libnjb, try to purge it by typing

```
 sudo apt-get remove --purge libnjb-2.2.5
``` for the one you installed from source, and whatever the other packages from the repos are (libnjb-dev, libnjb5, libnjb1, etc. - any libnjb packages you installed). If you are using Synaptic, I'm not sure but it should have a purge option. I use Adept (in Kubuntu) and know it has one when I right-click on a package. Purge should remove everything that the package installed, including config files. If you've already uninstalled a package without purging it, reinstall it then purge it. Once all versions of libnjb are uninstalled / purged (both the ones compiled  manually and installed and from the repos), or if you just want to make sure all the .so lib files related to libnjb are removed, navigate to where they're stored ```
 cd /usr/lib
``` and find out if they're still there ```
ls libnjb*
``` and if they are, delete all the libnjb libs  ```
 sudo rm libnjb*
``` Then give it one more shot and try to compile from source again as you did before. Once you've recompiled / reinstalled libnjb 2.2.5, try Gnomad one more time and see if it compiles.

---

### Post by BlackwaterPark on 2006-07-07
> **monomaniacpat said:**
> Great guide. However, having successfully installed all this the other day under an upgraded breezy>dapper setup, I today tried again and get this error:

```
patrick@patrick:~/downloads/libnjb-2.2.5$ gnomad2
Found non-autodetected device "Creative Zen Micro (MTP mode)" on USB bus...
usb_claim_interface(): Operation not permitted
```

The last time I got it working was using the old HowTo (needing to type sudo out each time). Can you tell me what I'm doing wrong? Here's my nomad.rules:

*SNIP*

I'm going to try uninstalling and starting from scratch.

I am seeing the same problem right now - I got it working a while back on my laptop (Dapper), I am going to continue working on it tonight

---

### Post by vladdythephotogeek on 2006-07-07
> **msak007 said:**
> I know what you mean, it's frustrating when you're so close and can't get things working. I do have one last suggestion before you decide to format. When uninstalling libnjb, try to purge it by typing

```
 sudo apt-get remove --purge libnjb-2.2.5
``` for the one you installed from source, and whatever the other packages from the repos are (libnjb-dev, libnjb5, libnjb1, etc. - any libnjb packages you installed). If you are using Synaptic, I'm not sure but it should have a purge option. I use Adept (in Kubuntu) and know it has one when I right-click on a package. Purge should remove everything that the package installed, including config files. If you've already uninstalled a package without purging it, reinstall it then purge it. Once all versions of libnjb are uninstalled / purged (both the ones compiled  manually and installed and from the repos), or if you just want to make sure all the .so lib files related to libnjb are removed, navigate to where they're stored ```
 cd /usr/lib
``` and find out if they're still there ```
ls libnjb*
``` and if they are, delete all the libnjb libs  ```
 sudo rm libnjb*
``` Then give it one more shot and try to compile from source again as you did before. Once you've recompiled / reinstalled libnjb 2.2.5, try Gnomad one more time and see if it compiles.

But alas. It did not work. Time for the reformat.
THanks for your help. Hopefully this will take care of it.

Paul

---

### Post by vladdythephotogeek on 2006-07-07
> **msak007 said:**
> I know what you mean, it's frustrating when you're so close and can't get things working. I do have one last suggestion before you decide to format. When uninstalling libnjb, try to purge it by typing

```
 sudo apt-get remove --purge libnjb-2.2.5
``` for the one you installed from source, and whatever the other packages from the repos are (libnjb-dev, libnjb5, libnjb1, etc. - any libnjb packages you installed). "If you are using Synaptic, I'm not sure but it should have a purge option. I use Adept (in Kubuntu) and know it has one when I right-click on a package. Purge should remove everything that the package installed, including config files. If you've already uninstalled a package without purging it, reinstall it then purge it. Once all versions of libnjb are uninstalled / purged (both the ones compiled  manually and installed and from the repos), or if you just want to make sure all the .so lib files related to libnjb are removed, navigate to where they're stored ```
 cd /usr/lib
``` and find out if they're still there ```
ls libnjb*
``` and if they are, delete all the libnjb libs  ```
 sudo rm libnjb*
``` Then give it one more shot and try to compile from source again as you did before. Once you've recompiled / reinstalled libnjb 2.2.5, try Gnomad one more time and see if it compiles.

Greetings once again.
I tried everything you said and it still wouldn't compile.
So I reformatted. Since then I have used Easy Ubuntu to load some codecs, Skype, fonts etc.

I installed checkinstall, build essential, etc but at this point, my computer REFUSES to load libgtk2.0-dev. It simply refuses to.](*,) 
The exact error is this:

pjv@pjv-desktop:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.17-1ubuntu5) but 2.8.18-0ubuntu2 is to be installed
                 Depends: libglib2.0-dev (>= 2.8.5) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.6.1-2) but it is not going to be installed
E: Broken packages"

Now sure, I've checked to see if I have the most libgtk2.0, which I do.
I have tried to install each of the Depends: *-dev files independently and they all say essentially "You can't, you have to have libgtk2.0-dev first"
It seems to me a circular reference. I've also tried to install this 2.8.17-lubuntu5 but it comes back with the following error:

pjv@pjv-desktop:~$ sudo apt-get install 2.8.17-1ubuntu5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 2.8.17-1ubuntu5
 

I hate saying it, I love Linux and everything I've done with it so far (except this), XP is sitting on my bookshelf looking pretty lonely over there.

Your help has been and always will be greatly appriciated.

---

### Post by msak007 on 2006-07-08
What does your sources.list look like? I've never used EasyUbuntu (I use Automatix myself), so I'm not sure but does it add any extra repos? I've read a couple posts that mention that the compiz repos have a new version of libcairo that won't install in Dapper due to some dependency issues, thus preventing libgtk2.0-dev from installing. If EasyUbuntu adds any extra repos like Automatix does (I always choose to keep my list after running it), that could cause the conflict. The error you posted doesn't mention libcairo specifically so I assume it installed but it could still be a problem. I already checked the  Ubuntu Packages site and it seems those packages you're having a problem installing are in the default repos so something else must be causing the conflict. So here are my suggestions:

1. Look at your sources.list - here is what the original file should look like after a clean install:

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted 
deb http://security.ubuntu.com/ubuntu dapper-security universe 
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
``` 

That's with all the lines uncommented, but some of them are commented out by default. If yours list looks like that, make sure all lines are uncommented to enable universe / backports. If it doesn't, copy / paste that into your sources.list and then do a 

```
sudo apt-get update
sudo apt-get upgrade
``` 
Then try to install libgtk2.0-dev.

2. If that fixed the problem you can stop here, but I would advise you to enable extra repos anyway. If it didn't, then try this. I used [ubuntuguide.org]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") as a guide to enable all the extra repos. Just copy / paste the list from there into your sources.list (back yours up first just in case) then update / upgrade as before and try again.

Here's the post I found with someone having a problem installing libgtk2.0-dev (not exact same issue, but closest I could find) - it has links to other posts discussing the whole problem with libcairo. The suggestion to edit the repos and update didn't resolve it in that case, but that's all I can think of.

[http://www.ubuntuforums.org/showthread.php?t=207935&highlight=libgtk2.0-dev+impossible+situation](http://www.ubuntuforums.org/showthread.php?t=207935&highlight=libgtk2.0-dev+impossible+situation)

Hope this helps and resolves the issue to prevent you from having to go back to XP :).

---

### Post by rockfloyd on 2006-07-15
msak thank you a hell of a lot for making that tutorial. i have a creative nomad jukebox zen xtra and it worked perfectly after completing your instructions. i had been wondering for some time if i could get it to work in ubuntu, but i figured it would be really difficult, so i had just been booting up windows to use it. your tutorial was a huge help. it's posts like this that keep the ubuntu community alive.

---

### Post by TriggerHappyChewie on 2006-07-15
Thanks a lot for the tutorial.
I had this running in Gentoo with my Vision:M, but this tutorial helped me fix the usb not permitted error in Ubuntu.  (The fix was different in Gentoo).

Thanks!

---

### Post by douga on 2006-07-16
Just one more thanks. After following the tutorial, my Vision:M worked the first time.

So thanks.

---

### Post by nwgray on 2006-07-19
Good morning everyone,
   After installing the two lib files, I attempted to configure teh gnomad file and received this error:

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0           gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


I looked thru this thread and didn't see this error listed before so I went in to Synaptics, searched for gnomad and installed gnomad2. I then started it from a terminal and got a USB error. I closed gnomad2, unplugged my Zen Micro, plugged it back in, restarted gnomad2. It nows works great.

thx to everyone for posting. It really helps noobs like me.

---

### Post by Jontom on 2006-07-19
Awesome post :) , the first time ive been able to use my Creative zen touch with linux. Just one problem I can only run as root and the problem is because i cannot get a device name from lsusb, here is the output:

Bus 005 Device 006: ID 041e:4130 Creative Technology, Ltd
Bus 005 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 004: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 T                             ablet
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0c10:0000
Bus 002 Device 003: ID 046e:5520 Behavior Tech. Computer Corp.
Bus 002 Device 001: ID 0000:0000

As you can see there is no name for my device :( 

Ive tried leaving the name as blank in the nomad.rules file but that didnt seem to work. When I run as root I get this name detected in the output :
Creative Zen Micro (MTP mode)

So I put that in as the name in the nomad rules and re-ran sh hotplug.sh (is this enough or do I have to re-make and checkinstall?)

Anyway that still wouldn't work.

Here is the full output when I run as root:

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Autodetected device "Creative Zen Micro (MTP mode)" (VID=041e,PID=4130) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen Micro

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(gnomad2:31735): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

Any ideas?

---

### Post by Jontom on 2006-07-19
Oops disregard my last post someone with the same problem as me seems to have sorted it on pag five will try now!!:)

---

### Post by Jontom on 2006-07-20
Hmm well that didnt work either, I used the name that he used and it made no difference.

---

### Post by bsalt on 2006-07-20
> **advance said:**
> Hi,
Thanks for the very informative post, I got everything up and running with my Zen Touch 40GB...I ran Gnomad, It recognized the device and scanned the tracks properly, however when I attempted to copy an MP3 to it, I got this message:


advance@nicksbox:~$ gnomad2
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen Touch
Transferring MTP track...
LIBMTP_Update_Track_Metadata(): could not set use count
LIBMTP_Send_Track_From_File_Descriptor: error setting metadata for new track
Error sending file "/tmp/fileKOo1Xt/07 - Assasin.mp3" to MTP device!



And nothing was transferred :(
I did double check that the write protection was off on the device, so that's not it...


***update***
I searched through the libmtp source code for "use count" and found that in libmtp.c there's a spot that says:

```
  // Update use count, set even to zero if desired.
ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount);
    if (ret != 0) {
      printf("LIBMTP_Update_Track_Metadata(): could not set use count\n");
      return -1;
    }

```

well, i assume that the zen touch doesn't keep track of use counts....sooo....
i tweaked the code to read:

```
  // Update use count, set even to zero if desired.
[COLOR="Red"]if (metadata->usecount != 0) {[/COLOR]
  ret = LIBMTP_Set_Object_U32(device, metadata->item_id, PTP_OPC_UseCount, metadata->usecount);
    if (ret != 0) {
      printf("LIBMTP_Update_Track_Metadata(): could not set use count\n");
      return -1;
    }
[COLOR="Red"]}[/COLOR]

```


recompiled libmtp and now...voila! the tracks transfer flawlessly :)

thanks, advance! it now works for my zen xtra perfectly!

kudos!

---

### Post by msak007 on 2006-07-20
> **Jontom said:**
> Awesome post :) , the first time ive been able to use my Creative zen touch with linux. Just one problem I can only run as root and the problem is because i cannot get a device name from lsusb, here is the output:

Bus 005 Device 006: ID 041e:4130 Creative Technology, Ltd

The name of the device in the file is irrelevant, as it is in a line that is commented out anyway - it is simply for keeping track of the devices and identifying them when you look at the file. The fact that it's blank in the file or the output of lsusb shouldn't affect the device from working. All you need is your device ID, which you already have from lsusb: **4130**. Make sure that there is an entry in nomad.rules that has that product ID in there.

You said you already edited the file and re-ran the script, but did you check in the folder to see if it's there? If the script ran correctly, nomad.rules should be in **/etc/udev/rules.d/** 

Monomaniacpat posted in the thread a while back about how the script ran for him, but it didn't put the file where it was supposed to. I would check there first to see if the script ran correctly and copied the file there. 
If it did, try to edit it to see if it really copied your changes and that your device is in there. If it didn't, simply copy it there manually. Then restart udev 

```
sudo /etc/init.d/udev restart
``` 
and try again. Let me know how that works for you.

---

### Post by bsalt on 2006-07-20
Sorry, I forgot to thank you as well msak07! Amazing work!

---

### Post by Jontom on 2006-07-21
Right sorted, just had to restart udev.

Excellent im off to play with my music collection.

---

### Post by Aurdal on 2006-07-26
So, I tried this the 3rd time now and now it actually finds and connects to my device, but I when I run gnomad it returns the following:

```
~$ gnomad2

(gnomad2:29916): Gdk-WARNING **: locale not supported by Xlib

(gnomad2:29916): Gdk-WARNING **: cannot set locale modifiers
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
Segmentation fault
~$

```

So, it starts up finds and connects to the device and then exits from a "Segmentation fault" before it let's me do anything.

Any ideas?

---

### Post by msak007 on 2006-07-26
I'm not sure it has anything to do with the device not working, but the error does mention your locale not being supported. What locale do you have selected?

---

### Post by Aurdal on 2006-07-27
What is the locale?

---

### Post by flugheim on 2006-07-27
Hi, i cant install libnjb
> 
(Leser database ... 132778 filer og kataloger er installerte.)
Pakker ut libnjb-2.2.5 (fra .../libnjb-2.2.5_2.2.5-1_i386.deb) ...
dpkg: Feil ved behandling av /home/flugheim/Desktop/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb (--install):
 prøver å skrive over «/usr/lib/libnjb.so.5.1.0», som også finnes i pakken libnjb5
Det oppsto feil ved behandling av:
 /home/flugheim/Desktop/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.

It says something like:
(reading database ......................................)
Packing out libnjb-2.2.5 (from .......................)
dpkg: Error when treating /home/flug....................)
Trying to write over «/usr/lib/libnjb.so.5.1.0», that also exist in the package libnjb5
It occourded an error while treating /home/flugheim/Desktop/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.

How can i fix this?

---

### Post by ParanoidDK on 2006-07-28
First i will like to thank for the great guide this is... And then i was thinking, when we have been making the deb's with checkinstall wont they work on other systems like the one we have been building them on.. if that is the case then i will be more then happy to host the debs on my server... i do already have the ones for an i386 system... i do hope that it may help ppl later on and making it even more easy to install... i am also planing on making an install script that do dl the debs and install it automatic, so we get en total automatic installer.. Let me know if you are up for helping on testing the script.. 

Greetings from Paranoid

An littel update... i have finish an simpel script... and i am going to test it on my gf laptop (That she have been so kind to let me install linux on) the script can be found [HERE.]("http://ubuntu.moonman.se/i386/gnomad_mtp.sh") At the moment it is only good for installing the i386 version but it will be updatet later.

UPDATE 2: I have just testet it on my gf laptop and it is working fine.. i do just need some fine tweaking in the script... and then i recomend for the moment that you make an dir to dl the script to and run it in... To use the script open the consol after you have dl the script and write chmod +x <patch/to/gnomad_mtp.sh> and then cd to the directory that holds the script and run it with ./gnomad_mtp.sh 
If there are any errors please let me knos, or tweak the script just remember to send an updatet version. ParanoidDK <admin@moonman.se>

---

### Post by msak007 on 2006-07-28
Aurdal - locale is what you chose your local language settings to be. It could be that you have a nonstandard locale, or one that XLIB doesn't recognize. I, for example, am using US English. The segmentation fault you're getting, however, may not be related to that error. It could be libusb - are you sure you've installed that?
 
flugheim - You're getting that error because you've installed libnjb5 from the repositories, and trying to install libnjb from source is trying to overwrite the protected file "libnjb.so.5.1.0". Try uninstalling / purging libnjb5, then compiling libnjb again.
 
ParanoidDK - that would be awesome if you could host the files. I have them ready to go and was thinking about suggesting your idea so that people can download the 3 .debs and install them rather than compiling everything. Unfortunately I have nowhere to host the files so if you could fill that void it'd be great. A script could work, I'll help you test it once I get some free time and I'm @ home.

---

### Post by ParanoidDK on 2006-07-28
mark007

The files i have maked on my P2 laptop are already up on my site and i have been working on an better script... Now the script do auto install it all... i will post the contens of the script here just to show that i haven't been making any backdoor... the new script do work with an universal now.. the only thing is i do only have the i386 debs up now... But the new script do work with the command: ./gnomad_mtp.sh i386

```

#!/bin/sh
# install - install a program, script, or datafile

clear
echo "This is the first version of an autoinstaller for gnomad with MTP support"
echo "If you find any bugs in the script please report them to admin@moonman.dk"
echo "At the moment it do only work with i386 but i am planning to make it an "
echo "universial script."
echo "It will use the sources.list that i use so you will get the right programs"
echo "without having to edit your own sources.list and it will reverse the list"
echo "again after the install."
echo "Do you want to install Gnomad2 with MTP support"
read IN
 if [ "$IN" = "y" ] || [ "$IN" = "Y" ]; then
        echo "Continuing..."
    else
        exit 0
fi
clear
echo "----------------------------------------------"
echo "I will now download the editet sorces.list and"
echo "and then backup your own sources.list before, "
echo "copying the new one and do an apt-get update. "
echo "After that is done it will revert to your own "
echo "sources.list."
echo "Do you want to continue with the install"
echo "----------------------------------------------"
read IN
 if [ "$IN" = "y" ] || [ "$IN" = "Y" ]; then
        echo "Continuing..."
    else
        exit 0
fi
clear
wget http://ubuntu.moonman.dk/$1/sources.list
sudo cp /etc/apt/sources.list /etc/apt/sources.list_gnomad
sudo cp sources.list /etc/apt/sources.list
sudo apt-get update
sudo apt-get install libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev
sudo rm /etc/apt/sources.list
sudo /etc/apt/sources.list_gnomad /etc/apt/sources.list
echo "----------------------------------------------"
echo "Done installing the programs we need. Is downloading "
echo "the files needet to continue. "
echo "Do you want to continue with the install"
echo "----------------------------------------------"
read IN
 if [ "$IN" = "y" ] || [ "$IN" = "Y" ]; then
        echo "Continuing..."
    else
        exit 0
fi
clear
wget http://ubuntu.moonman.dk/$1/libmtp-0.0.10_0.0.10-1_i386.deb
wget http://ubuntu.moonman.dk/$1/libnjb-2.2.5_2.2.5-1_i386.deb
wget http://ubuntu.moonman.dk/$1/gnomad2-2.8.6_2.8.6-1_i386
wget http://ubuntu.moonman.dk/$1/nomad.rules
echo "----------------------------------------------"
echo "Starting the install of the programs"
echo "Do you want to continue with the install"
echo "----------------------------------------------"
read IN
 if [ "$IN" = "y" ] || [ "$IN" = "Y" ]; then
        echo "Continuing..."
    else
        exit 0
fi
clear
sudo dpkg -i libmtp-0.0.10_0.0.10-1_i386.deb
sudo dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
sudo dpkg -i gnomad2-2.8.6_2.8.6-1_i386
sudo cp nomad.rules /etc/udev/rules.d/nomad.rules
sudo /etc/init.d/udev restart
echo "----------------------------------------------"
echo "The install is finish, just needing to"
echo "run an apt-get update to finish."
echo "Do you want to continue"
echo "----------------------------------------------"
read IN
 if [ "$IN" = "y" ] || [ "$IN" = "Y" ]; then
        echo "Continuing..."
    else
        exit 0
fi
clear
sudo apt-get update

```

Remember this i just version 0.3 of the script.. and i am open for sugestions... :D And just to link it again... DL it [HERE]("http://ubuntu.moonman.dk/i386/gnomad_mtp.sh")

---

### Post by msak007 on 2006-07-28
Great work, this looks good so far! I do have a few suggestions I can send you, so I'll PM you with those.

EDIT: It looks like the link you posted is invalid. I get a 404 error when trying to download your script. I'll still send you the suggested changes though.

---

### Post by ParanoidDK on 2006-07-29
Found the error in the link.... lol.. i do own 2 domains that do point to the same server... I do just forget that i am usinging the .se domain and not the .dk one.. :P I think i have to fix my vhosts... :D But send away.. i have found an manual and some examples to make an new script with.. There will be an help file in the new script.. this one i have uploadet now is the result off 120 mins "hard work"

The right link is [HERE]("http://ubuntu.moonman.se/i386/gnomad_mtp.sh")

---

### Post by msak007 on 2006-07-29
Ok, I can download the script but now running it gives 404 errors :). The URLs in the script point to "http://ubuntu.moonman.se/$1/", but it should be "http://ubuntu.moonman.se/i386/". Anyway I fixed it in the modified script I'm about to test, I'll send you my changes once I verify it works.

---

### Post by ParanoidDK on 2006-07-29
Like i did point out before.. the script i beeing maked to be an universial script that works on i386/amd64/ia64 and so on and so on... So to run the script use ./gnomad_mtp i386

The variable $1 takes the first word after the script name and inset it where $1 is in the script... so insted of having an script for i386 and one for amd64 and so on, then my ide is when we got all the debs needet ppl can write 

./gnomad_mtp.sh i386 if they have an i386 system or 
./gnomad_mtp amd64 if they have an amd64 system, and so on... if you get my ide.. :D 

Parnaoid

---

### Post by msak007 on 2006-07-29
Oh ok I get it now. I ran it the way you suggested and it worked. I PM'ed you with the changes I made to your script.

---

### Post by ParanoidDK on 2006-07-29
I will look at them right away... and it was not to be grumpy... :D 
But i will take an look at the changes... :D And tnx for beeing an tester... hope you like the script at the moment...

---

### Post by ParanoidDK on 2006-07-29
**msak007:**

Tnx an lot with the help.. i got some new and updatet files online.... The next cpl of days i will be working on an new type og script.. i cant say when it will be out but will send you an link with an beta... 

To the rest out there if you want to help test the script let me know and i will hold you all updatet with the latest beta of the script...

---

### Post by msak007 on 2006-07-29
In order to help ParanoidDK with the script, if anybody has used this how-to successfully but had to modify nomad.rules to get their device working, please post the output of your lsusb so we can use it to make the nomad.rules file that will be installed work for as many people as possible.

---

### Post by darden68 on 2006-07-30
Thx for this howto !
I got my Nomad Zen working. I have a quick question.
When launching gnomad, it takes about 4-5 minutes to scan the music files (4500 files) while it was very fast on Windows.
Is it the same for you ?

Thanks all for your help!

---

### Post by ParanoidDK on 2006-07-30
> **darden68 said:**
> Thx for this howto !
I got my Nomad Zen working. I have a quick question.
When launching gnomad, it takes about 4-5 minutes to scan the music files (4500 files) while it was very fast on Windows.
Is it the same for you ?

Thanks all for your help!

It do the same with mine.. i do think it is the libmtp there is slow there.. i do also think the transfere is slowere then on windows, but i can live with it, when it is becouse i run it in linux.

---

### Post by msak007 on 2006-07-30
> **darden68 said:**
> Thx for this howto !
I got my Nomad Zen working. I have a quick question.
When launching gnomad, it takes about 4-5 minutes to scan the music files (4500 files) while it was very fast on Windows.
Is it the same for you ?

Thanks all for your help!

I can't remember where I read it, but that is a known issue and it's not uncommon for slow load times when you have that many files so it's not a problem you alone are having. I don't have quite that many songs on my player (I don't even think I have that many on my HD lol :)), so I can't comment on the slow load times as it only takes a few seconds to scan the ~100 songs on it at the moment. But I'm glad you got it working, and as ParanoidDK said you should be happy it's working in Linux at all :).

---

### Post by darden68 on 2006-07-31
I'm very happy indeed :)
got rid of Windows 3 weeks ago, thought I would be using Ubuntu for a few days and put back my Windows Ghost image... but the longer I use Ubuntu, the more I think I'll never go back to Microsoft...
and that's mostly thanks to this forum !

---

### Post by ParanoidDK on 2006-07-31
I found an error in the new script mark007... it do not rewert the old sources list anymore, ned i dont remove the files that i download even if you say yes... i will look at it here today and then fix it... :D

---

### Post by msak007 on 2006-07-31
I started the same way :). I didn't completely wipe out my Windows partition though as I was expecting to dual boot for a while. But I started using Kubuntu full time and got pretty used to it, and haven't wanted to go back since. Unfortunately one of the biggest things for me (transferring files to my phone) doesn't work so I have to use Windows for that. Luckily I don't have to transfer files that often so I use it sparingly. Just like you though, without these forums I would've switched back long ago...

---

### Post by Aurdal on 2006-07-31
Is there a way to transfer whole directories with subdirectories and all on to my device?

---

### Post by msak007 on 2006-08-01
Aurdal, I assume that this means you finally got your device working :)? What did the problem end up being...or did you just run the script to install it? Either way at least it's working now. 

Anyway as far as transferring folders, I'm not sure but someone posted earlier in the thread that they had the same problem you're having where they had to transfer the individual files because they couldn't transfer folders. I'll try it out later when I have the player with me and let you know if I have the same problem.

---

### Post by ParanoidDK on 2006-08-02
I cant transfere folders to my zen... But you can use ctrl+a to select all files in an folder... But i can remember if the windows software can transfere full folders, but that is something i can find out..

---

### Post by ricesteam on 2006-08-03
Nice Work! 

Worked the first time I installed it. Smooth.

---

### Post by ichibanMuffin on 2006-08-04
I'm running on an amd64 bit version of ubuntu. I forced installed these libraries and even used the package manager to get it to load, however, gnomad simply will not run, even in sudo. This is the error message I get.

```
gnomad2
gnomad2: error while loading shared libraries: libnjb.so.5: cannot open shared object file: No such file or directory

```

Here is the readout for /usr/lib/ for libnjb:

```
ls -l /usr/lib/libnjb*
-rw-r--r-- 1 root root 375238 2006-04-18 05:46 /usr/lib/libnjb.a
-rw-r--r-- 1 root root    798 2006-04-18 05:46 /usr/lib/libnjb.la
lrwxrwxrwx 1 root root     15 2006-08-03 23:56 /usr/lib/libnjb.so -> libnjb.so.5.1.0
lrwxrwxrwx 1 root root     15 2006-08-03 23:28 /usr/lib/libnjb.so.1 -> libnjb.so.1.0.0
-rw-r--r-- 1 root root 157000 2005-12-14 23:50 /usr/lib/libnjb.so.1.0.0
lrwxrwxrwx 1 root root     15 2006-08-03 22:56 /usr/lib/libnjb.so.5 -> libnjb.so.5.1.0
-rwxr-xr-x 1 root root 466664 2006-08-03 22:56 /usr/lib/libnjb.so.5.1.0

```

Any help getting this to work would be appreciated. The only information I can find concerning that error message was back in 2005 and it states it's a problem because files were installed to /usr/local/lib instead of /usr/lib, which is not true in this case.

---

### Post by ichibanMuffin on 2006-08-04
How wonderful. It fixed itself through recompiling 4 times in a row. First 2 times got errors. 3rd time did not, even though I changed no settings. Wonderous.

---

### Post by Aurdal on 2006-08-04
msak007: I ran the script and got the segmentation fault again, and when I got that same error when i dabbeled with a c tutorial I actually figured out what it was. It had something to do with memory. (But everyone else allready knew that. :p) So I reformatted my Zen and it worked. However I got the segmentation fault again when I tried one specific file so I suppose it was that file being corrupted causing the problem. Anyway it works now! :D

ParanoidDK: I figured that too, but still it would be much easier to select my "music" folder and transfer it with all it's subdirs.

---

### Post by canadianwriterman on 2006-08-04
msak007, this worked absolutely perfectly with my Creative Zen Microphoto, right down to changing to use by a normal user. I can't thank you enough. Doing it from the instructions on the Gnomad site baffled me and the KDE program (forget the name of it now) didn't work at all. Much appreciated.

---

### Post by msak007 on 2006-08-04
Aurdal - I never thought to suggest that it could be a file on your device causing the crash, but then again I guess that makes sense since it was crashing when doing a scan. Either way glad you finally got it working. Maybe the folder transfer will eventually be fixed in a later release of Gnomad.

canadianwriterman - You're welcome :). I know what you mean about the instructions on the Gnomad website...first of all they're CVS instructions, they're outdated (not updated since 2005), and there's no mention of libmtp anywhere on the site (not even as an optional dependency for MTP players). They do a great job of updating the application, but unfortunately the documentation and the rest of the site updates are lacking. I believe the KDE app you're thinking of is KZenExplorer. I also tried it and it didn't work. I put a note at the bottom of my instructions that I tried it and that it doesn't work with MTP players yet. The app hasn't been updated in a while and I really have no idea where that project is at or if it ever will be updated. We're stuck with one app, but at least it works and that's all I care about.

---

### Post by ohgod on 2006-08-09
Thanks so much, guys!  I got my new zen microphoto up and running in no time thanks to this thread.

---

### Post by DJiNN on 2006-08-10
Hey, msak007..... thanks for that. One of the main reasons that i periodically boot into XP is to change the tracks on my Zen Touch.... but after running your script, it worked fine in Gnomad2 (As sudo). Brilliant! 
It's slow, but hey, what do i care..... :)  I'm only using it until i finally get rid of the Zen & get a "Linux Friendly" player at last..... just wish i'd have realised how "Unfriendly" the Zen was before i bought it. 

Anyway, thanks once again...... :)

DJiNN

---

### Post by msak007 on 2006-08-10
Glad you got it working, but I notice you said you got Gnomad working as root (sudo). Did you ever get it running as a normal user? I put the instructions in there on what to do...if you need help with that part let me know.

---

### Post by DJiNN on 2006-08-10
Hello again msak007, thanks for the reply......

No, i didn't even bother with that, just went straight for the Super User...... but having given it a try, i've since found that it really is just too slow for me to use..... it would be quicker to just re-boot, slip into XP and then use the Notmad (Red Chair Software) program for the transfers etc..... 

If there's something that i can do to speed it up (it's running on a USB2 port so should be reasonably fast) then i'll give that a go. It's not the transfers that are slow.... i didn't even get that far, it's reading all the folders etc on the HD..... it takes forever... :)

Anyway, i shall keep checking it out etc & see if there's anything else that i can do to make it right. I still think that you did a sterling job on what you posted etc & thanks for that.

DJiNN

---

### Post by msak007 on 2006-08-10
Unfortunately that's a current limitation of the software...not sure where the bottleneck is (most likely libmtp as MTP is so new), but it does take forever to scan a device if you have a lot of files. As you said the transfers are quick, it's the scanning that's slow. Hopefully it'll get better. I'd be interested to see if someone has a non-MTP device, how long it takes for them to scan the device using Gnomad with the same amount of data that an MTP device has to compare the time and see if it really is MTP. 

Either way, do what you feel is best for you. I only keep ~ 100 songs at a time on my device so it really doesn't take me long to scan it, so I'll continue using Gnomad. At least you're not giving up on Ubuntu completely so it's still OK :)

---

### Post by monomaniacpat on 2006-08-10
Despite being in utter wonderment that this works at all, I am still a little unhappy that I cannot create directories on my Zen. I know it is possible to divide albums by folders, because windows media player created one on the only occasion I have daned to use it. It made subdirectories for Zelda, Wind Waker, Disc 1/2.

How do I get Gnomad to recognise these files, let alone create new ones? The Zelda directory is currently only visible (to me at least) on my Xbox 360 (the only other software I use the device with).

I would use playlists, but the bloody things list in alphabetical order :mad:

---

### Post by DJiNN on 2006-08-10
> **msak007 said:**
> Unfortunately that's a current limitation of the software...not sure where the bottleneck is (most likely libmtp as MTP is so new), but it does take forever to scan a device if you have a lot of files. As you said the transfers are quick, it's the scanning that's slow. Hopefully it'll get better. I'd be interested to see if someone has a non-MTP device, how long it takes for them to scan the device using Gnomad with the same amount of data that an MTP device has to compare the time and see if it really is MTP. 

I thought that it may be that...... I'm not too fussed, because as i said earlier, eventually (asap) i shall get an MP3 player that is "Linux Friendly" & has ogg capability as well..... :)

> Either way, do what you feel is best for you. I only keep ~ 100 songs at a time on my device so it really doesn't take me long to scan it, so I'll continue using Gnomad. At least you're not giving up on Ubuntu completely so it's still OK :)

Absolutely!! I've been using Ubuntu since last November, and apart from the usual learning curve, i LOVE it!! :)  I'll NEVER go back to XP now..... can't see the point, as Ubuntu does everything that i want it to do, and as i come to understand more about how it works (Slowly) i find that i'm able to both "Do more" with it, and change more things. 

Plus, Ubuntu is really improving FAST!! It's amazing just how stable & fast Dapper is....

As for the amount of tracks on the Zen.... Heehee, i could quite easily fill my 20gig drive..... but on average i have about 2 thirds full, so that's probably why it takes so long.

Thanks once again, and keep up the excellent work, it's very much appreciated.

DJiNN

---

### Post by imaiden22 on 2006-08-10
I just need a success story from someone who got this to work wonderfully with a Zen Vision M...just for peace of mind because i'm really considering getting one soon and I know a majority of the zen players have been addressed here but i'm still unsure about the recent updates to support MTP which I believe the Vision M applies to. Thanks in advance

---

### Post by stryderjzw on 2006-08-12
I've just tried it with my Creative Zen Vision:M.  Music transfer worked beautifully.

I was using the script to install Gnomad.  Not any problems yet. I'm still using sudo tho... didn't bother trying the suggestions to use normal user yet.  Maybe later.

---

### Post by bsalt on 2006-08-12
msak007... would you ever be interested in implementing gnomad2 with rhythmbo x? i'm not trying to take you for granted, i was just asking if you had thought it.

oh and thanks again just for the great piece of software that works with this.

---

### Post by slibuntu on 2006-08-25
Hey, i followed the howto, and was delighted to get my Zen Sleek Photo working using "sudo gnomad2". Then when i tried to alter the 45-libnjb.rules file to try get it to work as a normal user, it didn't work, these are the 2 lines i added to the file: 
# Creative Zen Sleek Photo
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413d",GROUP="plugdev", MODE="0660"

I'm getting an error message like this:

Found non-autodetected device "Creative Zen Sleek Photo" on USB bus...
usb_claim_interface(): Operation not permitted

If you could help, i'd be grateful!

---

### Post by msak007 on 2006-08-25
Hey guys sorry it's taken so long to get back to you! 

@ monomaniacpat: I played around with Gnomad and couldn't get it to create a folder in the "Data transfer" view. I then created some folders (both blank and with music in them) and tried to transfer them, no luck. I looked on the bug reports on Gnomad's page, and it seems that there is currently no folder support with Gnomad2 according to [this]("http://sourceforge.net/tracker/index.php?func=detail&aid=1485233&group_id=65573&atid=511470") bug. Read the last reply from "snirkel" (the creator of Gnomad) where he acknowledges that there is no folder support yet. It was filed back in May after Gnomad 2.8.3 with MTP support was released, and the bug hasn't been closed yet so I assume it's still valid. I looked at libmtp again and couldn't find the tools he referenced in the first reply to that bug report, so if you can find something that lets you create folders let me know. As far as the files you're referencing that you can't see, if they were created by your XBOX and placed in folders on the device, that's probably why they're not viewable in Gnomad.

@ DJiNN: I was playing around with the preferences, and saw 2 options you may want to look at. In the "Preferences" tab, uncheck the box for "Read extended metadata from jukebox" and try again. If you're still having problems, you may want to uncheck the box for "Enable turbo mode". I'm not sure what that one does, but it advises to uncheck if you're having problems so it's worth a try. If you try this and it makes a difference in scanning speed for a large amount of data, please let me know and I'll update my first post with this tip.

@ bsalt: Unfortunately I'm not a Gnomad developer, just someone who wanted to share a how-to on getting the devices / software working to help prevent others the frustration I went through trying to get it working with Dapper :). If you have any feature requests I would advise you to go to Gnomad's SourceForge.net [Feature Requests]("http://sourceforge.net/tracker/?group_id=65573&atid=511473") page and submit something there.

@ slibuntu: You probably had libnjb5 from the repositories installed, which put the 45-libnjb.rules file there. If you used the script or the manual install instructions in the first post, I would advise you to uninstall libnjb5 and remove the 45-libnjb.rules file. The one you want to edit (if everything installed correctly) is in the same folder, but it's called "nomad.rules". Let me know if you can't find it, or if you need help editing it.

---

### Post by slibuntu on 2006-08-25
When i try to uninstall libnjb5, it tells me this : 
"The following packages will be REMOVED:
  gnomad2 libnjb-dev libnjb-examples libnjb5"
I don't think i want to uninstall all of this right?

---

### Post by msak007 on 2006-08-25
You don't need libnjb-dev, libnjb-examples, or libnjb5. I'm not sure why it wants to uninstall Gnomad, unless you still have the repo version installed. If that wasn't uninstalled prior to running the script, it's still on the machine and one of the dependencies is libnjb5. I would do what it suggests and uninstall everything, then re-run the script to install everything you need and let me know if you still need help.

P.S. Gnomad 2.8.7 and libmtp 0.0.13 were released today. If you want to try compiling yourself rather than running the script, I'll update the instructions shortly to point to the new files (everything else will stay the same) and you can give that a shot if you want the latest. I'm still waiting on word from ParanoidDK if he's going to update the script and the .debs for the new files.

---

### Post by Silver Streak on 2006-08-26
I just tried the script method - not sure if he's updated it yet, but one thing's for sure, it works. :grin: 

Hopefully, updating packages for this setup won't be a pain.

SS

---

### Post by msak007 on 2006-08-26
I've messaged ParanoidDK to inquire about the status of the script as it hasn't been updated for the new versions, but haven't received a response yet. Updating packages using the manual method requires uninstalling the previously installed packages. It's a pain, but isn't too hard. I'm not sure if ParanoidDK specified dependencies when building the debs to make sure old packages are uninstalled first automatically or not, so I'll have to ask him about that. Either way it's great to hear another success story :)

---

### Post by ParanoidDK on 2006-08-28
UPDATE UPDATE.
I did it before work. Love the new laptop i got.. But the script i now updatet to the new libmtp and the new gnomad builds.

If anyone need me they can reach me at ether rudolf.vang[remove]@dlink.se or admin[remove]@moonman.se
........................................................

i will update the script today when i get home from work.. have just been busy with the work... have been moving from Denmark to northen Sweden to work at D-Link Support... That is also the reason i have been away. I am also looking for the amd64 debs if there are anyone that want to help me with making them.

---

### Post by ernz on 2006-08-28
msak007 - I am a dude and I will gladly have your babies for figuring this out. I have been fiddling like a no0b with terminal for hours now, and just googled "zen microphoto help!!!" and found that autoscript above. Fantastic work! Well done.

---

### Post by msak007 on 2006-08-28
> **ParanoidDK said:**
> UPDATE UPDATE.
I did it before work. Love the new laptop i got.. But the script i now updatet to the new libmtp and the new gnomad builds.
Awesome news, thanks for the update! I had no idea you were moving and appreciate your contributions. Instructions have also been updated to reflect this.

> **ernz said:**
> 
msak007 - I am a dude and I will gladly have your babies for figuring this out. I have been fiddling like a no0b with terminal for hours now, and just googled "zen microphoto help!!!" and found that autoscript above. Fantastic work! Well done. 
You're welcome, thanks for posting another success story. Also, I'm a dude as well so thanks for the offer, but no thanks :). You can thank ParanoidDK for the script though. I wrote the original how-to (the manual, compile from source method), he simply built on that and wrote the script and is hosting the files.

---

### Post by laharrin on 2006-08-28
Many thanks for providing such a well described how-to.

Here is the output of my lsusb:
Bus 004 Device 006: ID 041e:4130 Creative Technology, Ltd

---

### Post by pianoboy3333 on 2006-08-28
I have a very unique problem I reported as a libmtp bug at [http://sourceforge.net/tracker/index.php?func=detail&aid=1548297&group_id=158745&atid=809061](http://sourceforge.net/tracker/index.php?func=detail&aid=1548297&group_id=158745&atid=809061), here it is, I'd gladly appreciate the help:

> 
I have gnomad2 2.8.8 setup with libnjb 2.2.5 and libmtp
0.0.15, and I recieve the following error when
transfering certain files, here is an example of trying
to transfer Flaming from "The Piper at the Gates of Dawn":

LIBMTP_Send_Track_From_File_Descriptor: error setting
metadata for new track
PTP: I/O error
LIBMTP_Delete_Object(): could not delete object
Error sending file "/tmp/fileYNcttY/04. Flaming.mp3" to
MTP device!

This file will fail every single time I try to put it
on my Vision:M, others include I Will from "The Beatles
(white album)" and others I can't think of at midnight,
anyhow, this is anoying me very much, after it crashes
like this, I am not able to do anything else with the
mp3 player. All of my mp3's are ripped with sound
juicer with lame and a bitrate of 192 kbps. The tags
are added/updated with programs using mutagen normally.


---

### Post by linux_help_vampire on 2006-08-29
I got it working fine. 
It starts up and sees the Microphoto, but i cant transfer anything. I ave tried turning off turbo mode but to no avail. 

I have this bit of code, I hope that helps


(gnomad2:8756): Gtk-CRITICAL **: file gtktreeview.c: line 5207 (do_validate_rows): assertion `gtk_tree_model_iter_next (tree_view->priv->model, &iter)' failed.
There is a disparity between the internal view of the GtkTreeView,
and the GtkTreeModel.  This generally means that the model has changed
without letting the view know.  Any display from now on is likely to
be incorrect.

Autodetected device "Creative Zen MicroPhoto" (VID=041e,PID=413c) is known.
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
Could not get device info!
Connection error.
PDE device NULL.
PDE device NULL.
Autodetected device "Creative Zen MicroPhoto" (VID=041e,PID=413c) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen MicroPhoto

(gnomad2:8756): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
Transferring MTP track...

---

### Post by ParanoidDK on 2006-08-29
msak007 I did move up to here at the end of last month... and did need some time to settle... i do still have an update for the script in mind... maby with some Gui but am not sure... and is planning to start to remove the versions numbers from the debs so it will be more easy to upload the debs... no need to reconfigure the script on updates. :) but will keep the system with the versions numbers for now and will keep the old debs on-line also. :)

---

### Post by msak007 on 2006-08-29
Hmm not sure why you guys are having problems...could it be the new version of libmtp? I haven't had any problems yet.

**pianoboy3333** - I saw an error with similar output to yours (not exactly the same) in [post # 40]("http://www.ubuntuforums.org/showpost.php?p=1192215&postcount=40"). You might want to check it out and see if that helps you out (it requires a manual compile). Also, try disabling some of the ID3 / metadata related options under the "Preferences" tab and try again (maybe disable all of them, and enable them one by one if you have success to rule out the one causing the crashes?). The error does indicate an error writing metadata, maybe if you disable those options it won't try. If that fails and you used the script method, try the manual method. Some people have reported erratic behavior with the apps, and recompiling once or twice resolves it for some reason. 

**linux_help_vampire** - I've never seen that error, but I did find [this]("http://www.linuxquestions.org/questions/showthread.php?t=374428") thread  on LinuxQuestions.org with several people having the same exact error. That thread is specific to the MicroPhoto, which is the same device I'm using and have not had these errors or problems. I'll do more testing later (tranferring lots of files to and from the machine) to see if I can duplicate them. In the thread, it seems to be related to specific files for some people or is very random for others. Have you tried other files, and do they all cause the same problem? Does this only happen when going from PC --> MP3 player, or MP3 player --> PC as well? The option that one poster referred to in there is the "Remove all ID3 tags from files transferred to the jukebox" (in the "Preferences" tab) - try disabling it and see if that resolves your issue. One last thing I can suggest, although drastic, is to try and format the player and try again.

---

### Post by imaiden22 on 2006-08-30
alright, im desperate for help now...i'm trying to get libmtp-0.0.16 to work with libnjb-2.2.5 and gnomad2-2.8.8..and using many methods along with the manual compiling method and the scripting method listed here, i've had no succes to getting my creative zen vision: m to work with my ubuntu dapper. running gnomad2 in the terminal...i get the error that it can't find any jukeboxes on usb..and here's the output im getting: 

```
$ sudo gnomad2
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
Could not get device info!
Connection error.
PDE device NULL.

```

i've already tried the fixes listed here to fix this problem as well, such as going into nomad.rules and adding the 2 lines with the vision m product id and the script for moving it to the right location and also the code to move it in case the script fails

all i want is to get music on my vision m, is that so much to ask?

---

### Post by imaiden22 on 2006-08-30
go figure...all I needed to do was a simple reboot, now im enjoying my tunes...I think that might be something to put in the howto perhaps, because I was pulling out my hair and then I though, "hmm, reboot" and whamo, tunes on the vision M...thanks for the guide!!

---

### Post by Metaxa on 2006-08-30
This is my lsusb output for my Zen Vision:M


Bus 004 Device 005: ID 041e:413e Creative Technology, Ltd

Sorry if this info is repeated just adding what was asked.

The guide on teh firs page worked nicely, i'm just wondering why i have to start gnomad from teh terminal instead of the icon in my menu.



Metaxa

---

### Post by msak007 on 2006-08-30
**imaiden22** - Sorry I didn't get to you sooner, I was @ work all day (and went out after work) :). But I see you got the problem resolved anyway. It's odd, that's the same exact error that linux_help_vampire had with his device, only he was using a MicroPhoto. I never suggested a reboot, and I'm not sure exactly what a reboot did in your case. The only thing that requires a restart is udev - my manual methods instruct you to do that, and I'm almost positive the script does that at the end too. If a reboot resolves peoples' issues I'll add that to the instructions.

**Metaxa** - Thanks for the update and posting the output of your lsusb. I'll update the first post and list the devices that require this extra step, and the outputs of lsusb we have so far so people don't keep posting the same info. That way you're going into this process knowing which devices work without extra tweaking, and which devices require that extra step. Also, ParanoidDK can use that info to update the "nomad.rules" file his script installs so that the devices are already in there and no extra tweaking is required. As far as running Gnomad from the terminal, I only suggest that because I don't know how to create a menu entry from the terminal. I use Kubuntu and just edited the menu manually by right-clicking on it and added an entry for the app. If you know of a way to create the menu entry using the terminal, let me know and I'll update the instructions. The script can be modified to also do that part for you. As far as icons go, [this]("http://www.kde-look.org/content/show.php?content=31991") is the one I use. __

I appreciate everybody's help and input into making this how-to better and easier to follow. If anybody else has any suggestions or changes, PM me or post them here and I'll try to accomodate them.

---

### Post by imaiden22 on 2006-08-30
hmm new problem, maybe you can help me out here msak...alright so i can transfer music and the lot, but my current issue is how much i can transfer

here is an example of the output of a successful transfer:

<CODE>
(gnomad2:11873): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
Transferring MTP track...
</CODE>

and here is an example of what happens on the track on which gnomad freezes up, or the usb stops respond, or whatever the problem is:

<CODE>
(gnomad2:11873): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
LIBMTP_Send_Track_From_File_Descriptor: error setting metadata for new track
PTP: I/O error
LIBMTP_Delete_Object(): could not delete object
Error sending file "/tmp/fileviTSxw/08-jacks_mannequin-miss_delaney.mp3" to MTP device!
LIBMTP panic: Found a bad handle, trying to ignore it.
Killed
</CODE>

EDIT: Just to be clear, the problem I'm having is that I can only transfer about 4-6 albums worth of songs, and then it starts giving me the error I listed above, even if that song is the middle of an entire album transfer. Just wanted to make that clear.

thanks in advance mates!

just fyi, I can still transfer music nonetheless, and beggars can't be choosers, but for the initial upload, it's a pain to have to disconnect my vision m from its dock and restart gnomad

---

### Post by watermonkey on 2006-08-31
Hi I recently purchased a Creative Zen Vision M and im having trouble getting songs to transfer on to it. We got gnomad to compile just as in the begining of this thread. When i plug my zen vision m in it is recognised by gnomad and i can see what songs are on there but as soon as i go to transfer a song on there it just hangs and i get this message in the terminal

Transferring MTP track...


And it doesent do anything.... if anybody has any sugestions or a fix it would be greatly apreaciated.

---

### Post by addrock20 on 2006-09-01
This just in: you're a rockstar, msak007. Creative Zen Vision: M going strong. Thanks!

---

### Post by stephane on 2006-09-01
> **watermonkey said:**
> Hi I recently purchased a Creative Zen Vision M and im having trouble getting songs to transfer on to it. We got gnomad to compile just as in the begining of this thread. When i plug my zen vision m in it is recognised by gnomad and i can see what songs are on there but as soon as i go to transfer a song on there it just hangs and i get this message in the terminal

Transferring MTP track...


And it doesent do anything.... if anybody has any sugestions or a fix it would be greatly apreaciated.

I have the exact same problem, gnomad recongnizes the device and can access the files on it but if i try to transfer anything to the ZenMicro, it just hangs, progress bar stays blank and nothing happens. Any help on this would also greatly be appreciated...

---

### Post by addrock20 on 2006-09-01
> **stephane said:**
> I have the exact same problem, gnomad recongnizes the device and can access the files on it but if i try to transfer anything to the ZenMicro, it just hangs, progress bar stays blank and nothing happens. Any help on this would also greatly be appreciated...


I had the same problem w/ my Creative Zen Vision: M.  I initially used the instructions on the first page and ended up in that situation.

However, there is a post on page 2 of this thread by 'wastrel' that details how to grab the source tarballs for the libmtp, libnjb, and gnomad2 from sourceforge and build them. After removing my original install attempts and doing this, I was jet-set ready.

Maybe the original post should be edited to include wastrel's insights.:?:

---

### Post by watermonkey on 2006-09-01
> **addrock20 said:**
> I had the same problem w/ my Creative Zen Vision: M.  I initially used the instructions on the first page and ended up in that situation.

However, there is a post on page 2 of this thread by 'wastrel' that details how to grab the source tarballs for the libmtp, libnjb, and gnomad2 from sourceforge and build them. After removing my original install attempts and doing this, I was jet-set ready.

Maybe the original post should be edited to include wastrel's insights.:?:

Thanks i'll give that a try! :smile:

---

### Post by msak007 on 2006-09-01
> **addrock20 said:**
> However, there is a post on page 2 of this thread by 'wastrel' that details how to grab the source tarballs for the libmtp, libnjb, and gnomad2 from sourceforge and build them. After removing my original install attempts and doing this, I was jet-set ready.
 
Maybe the original post should be edited to include wastrel's insights.:?:
 
**addrock20 **- My first post is exactly that (and always has been) - grabbing the source files from SourceForge (all the links lead to the apps' respective SF download site), extracting them, and compiling them. I just looked at wastrel's post and I'm not sure how that differs from the my first post or what you want me to change - he was simply restating what was already in the initial post at the time. If you're referring to the instructions on using the automated install script (which were at the top of the post for a while but are now at the bottom, below the manual instructions), I didn't write the script or make the .debs. ParanoidDK built those .debs on his machine and wrote the script that installs them. I personally suggest compiling from source for the best results, but some people prefer the script as it's easier. 
 
**stephane **& **watermonkey **- If you guys used the script to install the apps, then I would suggest what addrock20 said and install from source. If that's what you've done and you're still having problems, then start Gnomad from the terminal and post the entire output from the time you start the app to the time you try to transfer a file and it hangs.

---

### Post by watermonkey on 2006-09-02
I used the thing on page two and now it works good! The program locks up for me every once and awhile for me though.

Thanks

---

### Post by watermonkey on 2006-09-03
Once again i'd like to thank you all for your help. Ive gotten all my music transfered to my player. However ive gotten to the point where i want to tranfer my video collection on to it. I have a bunch of videos that i would like to seperate from each other. I'd like to be able to put them in folders in the video section. Is there any way to do this? thanks.

---

### Post by msak007 on 2006-09-03
No problem at all, thanks for your patience and persistence :). Just an FYI, but there are already new versions of Gnomad (2.8.8 ) and libmtp (0.0.16) released - apparently there were sync issues between 2.8.6 / 0.0.13 (the versions you probably have installed now) according to the Gnomad homepage. There's not even a link to libmtp 0.0.13 from their download site anymore. I suspect a lot of the issues reported by you and others in the past few days may be related to the versions released last week, so if you're still having issues I would give the new versions a try (keep the .debs you made from the versions you have now around just as a backup in case you need to revert). My first post has been updated with links to the new versions of Gnomad and libmtp.

Anyway to answer your questions regarding transferring videos, I'm not sure that's implemented yet. There is a data transfer mode, but I'm not sure where all that ends up when it's transferred (I've tried videos and photos). It doesn't recognize the file structure of the device and I can see all that stuff in the same folder / view the music is in on the device, and it won't let me create any folders to put the stuff in.

EDIT: I gave the data transfer another shot with 2.8.8 (I had 2.8.7 before) and it actually saw all the contents of the device (including pictures), only in list format - no folders or other views. I tried another picture (a .jpeg this time - apparently it doesn't like .gifs) and it put it in the list along with the other pictures. When I went to the "Pictures" folder on the device, the picture was there, on its own in the main view (not in one of the 3 sub-folders). So in a way data transfer works, but it doesn't support folders. I found out this device doesn't support videos so I can't help you out there, but if you have a "Videos" folder on your device and you transfer a video it'll probably end up there (as long as it's a supported format).

---

### Post by msak007 on 2006-09-03
I just noticed something interesting while I was reading the ./configure output of libmtp. Apparently there's a "libmtp.rules" file I never noticed before that's included in the libmtp package. It's a udev ruleset that serves the same purpose that "nomad.rules" does, but it is more up to date with all sorts of devices that are MTP-enabled (Creative, Samsung, SanDisk, etc.). I can't recall how far back that file was there (I just looked in the folder for 0.0.13, the only backup I kept, and sure enough the file is there). I see all the Creative devices that people have mentioned here so far listed in that file so apparently the nomad.rules modification isn't necessary any longer because the libmtp devs have already done all the work.  I'll have to update my instructions again to get this all sorted out once I've tried it myself...tomorrow morning *yawn*

EDIT: As promised, the manual instructions have been modified to account for libmtp.rules (albeit a little later than I expected - I like to sleep in :)). No more manually editing nomad.rules - yay! :)

---

### Post by monomaniacpat on 2006-09-03
Just installed again with no problems on a new system. Still no sign of subdir support, but thanks for making this much possible!

---

### Post by ParanoidDK on 2006-09-03
New files again.. Well i will start working on them tonite then. I am planning to have the script up to date tomorrow..

---

### Post by msak007 on 2006-09-03
**monomaniacpat** - It's good to hear it's working for you again (even though it sucks there's still no directory support). Did you ever get the issue with your unrecognized files (the ones you can see on your XBOX and in WMP) sorted out?

**ParanoidDK** - I know it's a pain to keep having to update...they released several versions of both Gnomad and libmtp in one week. Make sure that when you're updating your script to include the libmtp.rules file I mentioned a couple posts back. It has all of the devices mentioned here so far that we've had to modify nomad.rules manually to include. I've already updated the manual instructions in the first post if you want to use that as a reference.

---

### Post by ParanoidDK on 2006-09-03
msak007 i am way ahead of you there. and the script is up to date now, with the libmtp.rules file.

---

### Post by labbi on 2006-09-04
Hi,
i have a little Problem as i'm installing Gnomad2 2.8.8

I use the script Version - it works fine.
But if i start gnomad, in the terminal i see many lines of this error:

LIBMTP panic: Found a bad handle, trying to ignore it.

The list i see after a few minutes, is 8 titles long. But I know that there are many more titles on it (~8100)

I have no idea what for a problem it could be. Before i start to take these script i try to install older versions of gnomad and other programs (example KZenExplorer). I don't hope that this make the problems. 

If you try to help me, wrote it easy, because i am a newbee in Ubuntu. 


And I hope you understand what I mean, because my English is not so good (I would say it is bad). Sometimes, if I don't found the solutionin other Forum , I have to try it here. 

Thanks for help......

---

### Post by msak007 on 2006-09-04
> **labbi said:**
> Hi,
i have a little Problem as i'm installing Gnomad2 2.8.8

I use the script Version - it works fine.
But if i start gnomad, in the terminal i see many lines of this error:

LIBMTP panic: Found a bad handle, trying to ignore it.

The list i see after a few minutes, is 8 titles long. But I know that there are many more titles on it (~8100)

I have no idea what for a problem it could be. Before i start to take these script i try to install older versions of gnomad and other programs (example KZenExplorer). I don't hope that this make the problems.
Well first of all, what device are you using? You say you've tried an older version of Gnomad before trying this method, which may have installed some unneeded or older dependencies. Using Synaptic, uninstall (with the purge option) all unneeded applications first (Gnomad, libnjb, etc.) and anything else you tried first (KZenExplorer). I would uninstall *all* versions of Gnomad, libmtp, and libnjb (even the ones that the script installed) so that you can start over. Once you run it again, start Gnomad from the terminal with your device plugged in and copy / paste the whole output. Once we know what device you're using and you've posted the whole output, we might be able to get a little more info.

---

### Post by labbi on 2006-09-04
sorry 

Device: Creative Zen Xtra 30GB: Firmware 2.10.03 -> MTP-Device (built in HDD 80 GB)
my Workstation:  Ubuntu 6.06

--------- next -----

I have now uninstalled GNomad, Libnjb, Libmtp
KZen is away 
So, I hope that's all, I use Synaptic and a File Explorer to delete

Before I start with a new installation, is there anything I have to delete?

---

### Post by msak007 on 2006-09-04
That should do it. Now just run the script everything to reinstall everything, run Gnomad from the terminal, and post the complete output here if you're still having problems.

---

### Post by labbi on 2006-09-04
and here is the output:

--- start --- output ---

labbi@p266:~$ mkdir gnomad_install
labbi@p266:~$ cd gnomad_install
labbi@p266:~/gnomad_install$ wget [http://ubuntu.moonman.se/i386/gnomad_mtp.sh](http://ubuntu.moonman.se/i386/gnomad_mtp.sh)
--04:06:27--  [http://ubuntu.moonman.se/i386/gnomad_mtp.sh](http://ubuntu.moonman.se/i386/gnomad_mtp.sh)
           => `gnomad_mtp.sh'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 2.177 (2.1K) [text/x-sh]

100%[=================================================================================>] 2.177         --.--K/s

04:06:27 (273.30 KB/s) - »gnomad_mtp.sh« gespeichert [2177/2177]

labbi@p266:~/gnomad_install$ sudo sh gnomad_mtp.sh i386
Password:

This is the first version of an autoinstaller for Gnomad with MTP
support.
If you find any bugs in the script, please report them to
[email]admin@moonman.dk[/email]
At the moment it only works with i386 but I am working on making
it a universal script. This will only work on Dapper.
This installer will download an edited sources.list in order to
install the needed dependencies.
Your original file will be backed up first, and will be restored
once the installation has completed.
Do you want to install Gnomad2 with MTP support? (y/n)
y
Continuing...
--04:06:48--  [http://ubuntu.moonman.se/i386/sources.list](http://ubuntu.moonman.se/i386/sources.list)
           => `sources.list'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 840 [text/plain]

100%[=================================================================================>] 840           --.--K/s

04:06:48 (57.22 MB/s) - »sources.list« gespeichert [840/840]

Hole:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hole:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hole:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hole:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30,9kB]
Hole:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hole:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release [34,8kB]
Hole:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30,9kB]
Hole:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [46,4kB]
Hole:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [23,3kB]
Hole:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Hole:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [4275B]
Hole:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [11,5kB]
Hole:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [974B]
Hole:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [16,1kB]
Hole:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [2253B]
Hole:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Hole:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Hole:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Hole:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Hole:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Hole:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [71,4kB]
Hole:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Hole:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [46,3kB]
Hole:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Hole:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [5292B]
Hole:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Hole:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [9334B]
Hole:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Hole:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [2974B]
Hole:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Hole:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [4891B]
Hole:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [445B]
Es wurden 4656kB in 38s geholt (120kB/s)
Paketlisten werden gelesen... Fertig
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
Lese erweiterte Statusinformationen
Initialisiere Paketstatus... Fertig
Baue Tag-Datenbank... Fertig
Es werden keine Pakete installiert, aktualisiert oder entfernt.
0 Pakete aktualisiert, 0 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
Muss 0B an Archiven herunterladen. Nach dem Entpacken werden 0B zusätzlich belegt sein.
Schreibe erweiterte Statusinformation... Fertig
gnomad_mtp.sh: line 27: libgtk2.0-dev: command not found
--04:07:34--  [http://ubuntu.moonman.se/i386/libmtp_0.0.16-1_i386.deb](http://ubuntu.moonman.se/i386/libmtp_0.0.16-1_i386.deb)
           => `libmtp_0.0.16-1_i386.deb'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 224.318 (219K) [application/x-debian-package]

100%[=================================================================================>] 224.318      121.75K/s

04:07:36 (121.38 KB/s) - »libmtp_0.0.16-1_i386.deb« gespeichert [224318/224318]

--04:07:36--  [http://ubuntu.moonman.se/i386/libnjb-2.2.5_2.2.5-1_i386.deb](http://ubuntu.moonman.se/i386/libnjb-2.2.5_2.2.5-1_i386.deb)
           => `libnjb-2.2.5_2.2.5-1_i386.deb'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 292.354 (286K) [application/x-debian-package]

100%[=================================================================================>] 292.354      121.92K/s

04:07:39 (121.51 KB/s) - »libnjb-2.2.5_2.2.5-1_i386.deb« gespeichert [292354/292354]

--04:07:39--  [http://ubuntu.moonman.se/i386/gnomad2_2.8.8-1_i386.deb](http://ubuntu.moonman.se/i386/gnomad2_2.8.8-1_i386.deb)
           => `gnomad2_2.8.8-1_i386.deb'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 171.792 (168K) [application/x-debian-package]

100%[=================================================================================>] 171.792      121.33K/s

04:07:40 (121.03 KB/s) - »gnomad2_2.8.8-1_i386.deb« gespeichert [171792/171792]

--04:07:40--  [http://ubuntu.moonman.se/i386/libmtp.rules](http://ubuntu.moonman.se/i386/libmtp.rules)
           => `libmtp.rules'
Auflösen des Hostnamen »ubuntu.moonman.se«.... 86.58.130.133
Verbindungsaufbau zu ubuntu.moonman.se|86.58.130.133|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 4.341 (4.2K) [text/plain]

100%[=================================================================================>] 4.341         --.--K/s

04:07:40 (85.29 KB/s) - »libmtp.rules« gespeichert [4341/4341]

----------------------------------------------
Starting install of the programs...
----------------------------------------------
Wähle vormals abgewähltes Paket libmtp.
(Lese Datenbank ... 124097 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libmtp (aus libmtp_0.0.16-1_i386.deb) ...
Richte libmtp ein (0.0.16-1) ...
Wähle vormals abgewähltes Paket libnjb-2.2.5.
(Lese Datenbank ... 124126 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke libnjb-2.2.5 (aus libnjb-2.2.5_2.2.5-1_i386.deb) ...
Richte libnjb-2.2.5 ein (2.2.5-1) ...
Wähle vormals abgewähltes Paket gnomad2.
(Lese Datenbank ... 124166 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke gnomad2 (aus gnomad2_2.8.8-1_i386.deb) ...
Richte gnomad2 ein (2.8.8-1) ...
 * Loading additional hardware drivers...                                                                             [ ok ]
----------------------------------------------
Restoring your original sources.list...
----------------------------------------------
Hole:1 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper Release.gpg [189B]
Hole:2 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security Release.gpg [189B]
Hole:3 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates Release.gpg [189B]
Hole:4 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper Release [34,8kB]
Hole:5 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security Release [30,9kB]
Hole:6 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates Release [30,9kB]
Hole:7 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper/main Packages [619kB]
Hole:8 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper/restricted Packages [4571B]
Hole:9 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper/universe Packages [2458kB]
Hole:10 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper/multiverse Packages [95,2kB]
Hole:11 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security/main Packages [46,4kB]
Hole:12 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security/restricted Packages [4275B]
Hole:13 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security/universe Packages [16,1kB]
Hole:14 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-security/multiverse Packages [2043B]
Hole:15 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates/main Packages [71,4kB]
Hole:16 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates/restricted Packages [14B]
Hole:17 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates/universe Packages [15,4kB]
Hole:18 [http://ftp.inf.tu-dresden.de](http://ftp.inf.tu-dresden.de) dapper-updates/multiverse Packages [866B]
Es wurden 3431kB in 1m1s geholt (56,0kB/s)
Paketlisten werden gelesen... Fertig
----------------------------------------------
The install has completed. Do you want to remove
the downloaded files (y/n)
y
Continuing...
labbi@p266:~/gnomad_install$


--- end --- output ---

now it works. But I formate the HDD in the MP3 Player, too.

I've got this message as i wrote a musicfile to the player:
(gnomad2:10184): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
Transferring MTP track...

I, can see the files at the player...(next test-connect again)

Files all be there after plug-off. The palyer would be mount and umounted.

It look like, that it is working. 
Could it be, that Windows has written something on the HDD that Ubuntu can't read ? Because I go the same installation way as before. 

Ok..thanks for the help, If I have a new question, you would hear about me.  (good night or better good morning :) )

---

### Post by msak007 on 2006-09-04
If I understood that correctly, everything is working OK now? You may have had an older version of a program or something that was conflicting with the install so uninstalling everything and reinstalling may have helped. Formatting the device is always the last thing I recommend (especially when you said you had 8100+ files!), but sometimes that helps too. That one error in there
```
(gnomad2:10184): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
Transferring MTP track...
``` is one that several people reported a couple days ago. I'm not sure if that affects transferring files because you said you were able to transfer files and they were still there when you unplugged the device. Well, I hope it doesn't give you any more problems and you're able to continue using it. If you have any more problems, please ask :).

---

### Post by labbi on 2006-09-05
You understood it correctly. All works fine. I had use the Script-install-way.
I have the suspicion that Windows had written some unknown signs on the HDD and Linux don't know what it should be. 
In GNomad is a Window in German it is called 'Dateiübertragung' (in english it would be ' Filetransfer') and before I reinstall Gnomad, I see there some Signs like 0 or .. or 1 or -1. I think there is a corrupt Filesystem made by Windows. 

..exactly I have 8104 MP3 Files plus the new CD I bought at the weekend :cool:

---

### Post by msak007 on 2006-09-05
Windows does a lot of weird things :) The data transfer mode lets you see everything on the device, not just music, so there could have been some invalid files or filenames on the device that Gnomad couldn't read or set the metadata for. In the long run formatting was probably the best thing to do, but now you have to transfer all 8104 (+ CD) MP3s to your device again :)

---

### Post by labbi on 2006-09-05
> but now you have to transfer all 8104 (+ CD) MP3s to your device again
..and I can also clean up the ID3 Tags in the MP3 Files. Some of them are out of order. :p

---

### Post by Guns90 on 2006-09-06
I'm having a problem configuring gnomad.  The only thing I see that might be wrong is that the config command wants to check for GN and one of the package requirements is libnjb-2.2.5 but it's looking for 2.2.4.  Can anyone help please?  Thanks.

gary@Faith:~/Desktop/gnomad2-2.8.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

gary@Faith:~/Desktop/gnomad2-2.8.8$

---

### Post by ParanoidDK on 2006-09-06
Guns90
have you tryed the scripted installer to see if that works.

---

### Post by Guns90 on 2006-09-06
No, it didn't look like it had been tested and passed inspection.   If it's ready I'll give it a shot, but I've sure spent a lot of time on the source install.  I'm assuming I would have to purge what I've already installed?

---

### Post by ParanoidDK on 2006-09-06
Guns90
I have my self installed with the script on the laptop i am making it on, my work laptop, both with ubuntu and kubuntu and there are some of the users in this tread that is using it also.. and so far there havent been an glitch with it.. Ofcourse it is an work in progress but the last month it have had the same stuff in it, the only thing updatet is the debs it is dl...

---

### Post by msak007 on 2006-09-06
> **Guns90 said:**
> I'm having a problem configuring gnomad. The only thing I see that might be wrong is that the config command wants to check for GN and one of the package requirements is libnjb-2.2.5 but it's looking for 2.2.4...
 
checking for GN... configure: error: Package requirements ( glib-2.0 gthread-2.0 **libnjb >= 2.2.4 **gtk+-2.0 ) were not met:
 
No package 'libnjb' found
 
The >=2.2.4 after libnjb means it's looking for any version after 2.2.4 (greater than or equal to), so 2.2.5 suffices. I assume you've already compiled 2.2.5 because that step is before compiling Gnomad. Did you happen to try installing Gnomad from the repositories before trying to compile it? If you did then that could be the problem. One of Gnomad's dependencies (as you can see) is libnjb, so installing the version in the repos will install linbjb1 or libnjb5 from the repos as well. When you uninstall Gnomad (if you use Synaptic or apt-get instead of aptitude), it doesn't automatically uninstall libnjb with it. While it is technically the same version as the one you're compiling from source (2.2.5), I had problems with it (the same exact error) when I first started and is the reason I suggested compiling manually. See if you still have libnjb5 or libnjb1 installed and uninstall (purge) them, then try again. Or you could try the scripted install as ParanoidDK suggested.

---

### Post by bazmonkey on 2006-09-06
> **imaiden22 said:**
> hmm new problem, maybe you can help me out here msak...alright so i can transfer music and the lot, but my current issue is how much i can transfer

here is an example of the output of a successful transfer:

<CODE>
(gnomad2:11873): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
Transferring MTP track...
</CODE>

and here is an example of what happens on the track on which gnomad freezes up, or the usb stops respond, or whatever the problem is:

<CODE>
(gnomad2:11873): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
LIBMTP_Send_Track_From_File_Descriptor: error setting metadata for new track
PTP: I/O error
LIBMTP_Delete_Object(): could not delete object
Error sending file "/tmp/fileviTSxw/08-jacks_mannequin-miss_delaney.mp3" to MTP device!
LIBMTP panic: Found a bad handle, trying to ignore it.
Killed
</CODE>

I don't know if you're still having this problem, but I was, and I was having it a lot more often than every 4 albums or so.

It went away perfectly for me by switching to libmtp 0.0.17.  Seems that's where the most work needs to be done, and it'd probably be smart to update that as much as possible to stay on top of everything.

But yeah, switch to the new one.  I had the exact same problem, same player.

---

### Post by msak007 on 2006-09-07
> **bazmonkey said:**
> I don't know if you're still having this problem, but I was, and I was having it a lot more often than every 4 albums or so.

It went away perfectly for me by switching to libmtp 0.0.17.  Seems that's where the most work needs to be done, and it'd probably be smart to update that as much as possible to stay on top of everything.

But yeah, switch to the new one.  I had the exact same problem, same player.

What version did you have before that? 0.0.17 was just released today, and a lot of the problems people were having last week were due to 0.0.13-0.0.15, and 0.0.16 was supposed to fix those problems. Either way yeah I definitely agree, libmtp is the one that needs the most work as it is the newest, and upgrading to the newest version is (usually) a good idea.

---

### Post by bazmonkey on 2006-09-07
Well, I had 0.0.16.  Technically, I had 0.0.17 in an effort to make amarok work with MTP stuff, installed 0.0.16 through that script, which sat further ahead in my path (/usr instead of /usr/local), which I removed manually, which made gnomad2 use 0.0.17 and work.

I just got the player this morning, so my sense of time when it comes to the newness of Linux MTP support is way off.  I sorta bought it assuming that someone in Linuxland would've found a way to get it to work, not realizing that hitch-free music transfer just came around, what, today?

---

### Post by Boelcke on 2006-09-08
First off, great work here on both the help, the step-by-step, and the script.  Great community support helps bridge the gap of not running the monopolistic OS.

Help! I just bought a Creative Zen V mp3 player, and ultimately got to this thread.  I upgraded from Breezy to Dapper, successfully ran the script given at the beginning of this thread, and now have Gnomad2 2.8.8-1 and libmpt 0.0.17-1 installed.

The problem is, when I run gnomad (as root, since I too do not have that dnomad.rules file from the script) I'm getting an, "Error - No jukebox found on USB bus."  Argh!

When I run lsusb, my output is:
> Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

So, it appears to not be showing up at all.  Any suggestions on where to go from here to troubleshoot this thing?  I'm not sure what to try next, other than plugging it into an XP box to make sure the hardware is OK.

---

### Post by Boelcke on 2006-09-08
One more piece of info I should include, which I've posted to the libmtp mailing list:

I'm running Ubuntu 6.06, and have libmtp 0.0.17-1 and gnomad2 2.8.8-1. I've also have libusb 0.1-4, which I realize is not the latest and greatest.

Ultimately, when I try and run gnomad, it errors out with an error of,
"No jukeboxes found on USB bus."  When I run lsusb, it fails to list any
devices.  The kernel sees something, because /var/log/messages shows:

Sep  8 23:01:55 localhost kernel: [ 4943.270906] usb 4-2: new high speed
USB device using ehci_hcd and address 6
Sep  8 23:02:07 localhost kernel: [ 4954.918679] usb 4-2: new high speed
USB device using ehci_hcd and address 7

Has anyone had success with libmtp supporting a Zen V?

---

### Post by msak007 on 2006-09-09
I believe you're the first person that's posted in this thread with a Zen V, so hopefully we can figure this out so you won't have to go back to that "monopolistic OS" :). The Gnomad and libmtp sites don't list anything about this device being supported, and neither libmtp.rules or nomad.rules list it so it may be too new. But to address some of your concerns:

1. libusb-0.1-4 is the newest one in the repo, so that's the version most of us have unlesss compiled from source. I don't believe this is the problem but I can't confirm it as you are the first to report using this device.

2. The first output of lsusb you posted simply shows that you have 4 USB hubs, and that no devices are plugged into any of them. If a device is plugged in and detected, it'll have a label and won't be blank.

3. You should have both a nomad.rules and libmtp.rules in your /etc/udev/rules.d folder. The manual instructions include steps to put those files there, and ParanoidDK has informed me that the script has been updated to include libmtp.rules as well as nomad.rules. The problem is that neither file has your device listed. If we could get an output from lsusb, that problem could be resolved easily.

Now as far as things I would try:

1. First make sure the device is on. Please don't take offense as I know this is an obvious step, but the Zen MicroPhoto has a tendency to time out after a while and goes into a sleep mode after which neither Gnomad nor lsusb detect the device and Gnomad gives me errors that the device couldn't be found. I'm not sure if the Zen V is the same (I assume it would be), but I usually have to turn it back on for it to be detected by the machine again.

2. If this does not resolve the issue and lsusb doesn't list anything, I would try a "lsusb -v" to display a complete output of all your USB hubs / ports and any devices plugged in and get a more detailed description. Look for any trace of the device in that output.

3. Possibly upgrade the firmware? You said you just got it, but there was a [firmware update]("http://us.creative.com/support/downloads/download.asp?MainCategory=213&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Windows+XP&region=1&Product_Name=ZEN+V&Product_ID=15283&modelnumber=&driverlang=1033&OS=10&drivertype=4&x=23&y=15") on 8/25 so unless you got it factory direct with a firmware update already applied, chances are you have an older version. Unfortunately this requires a Windows machine to upgrade so hopefully you have access to one.  

4. A last suggestion I could offer is to restart the machine, as some have reported that a simple reboot resolved issues they were having. 

Hope this helps!

---

### Post by Boelcke on 2006-09-09
Wow!  You're faster than most tech-support lines!  ;)

I've tried the reboot, and making sure the power is on.

The firmware I have is 1.05.02, and the latest (you linked to) is 1.07.01.  I'll try that sometime this weekend (the one XP box I have access to at the moment is not SP1, and Creative requires at least Xp SP1 -- don't get me started on the m$ reasons that motivated me to goto linux in the first place).

Thanks for the assistance.  I'll report back later with either success or woes...

---

### Post by Guns90 on 2006-09-09
FYI.  I just wanted to add that this guide does NOT work for the Creative ZEN Nano Plus (1G) player.  I followed the thread twice and I get an error message saying something like 'No Jukebox Found'.  (Maybe that's because I don't have a 'Jukebox', huh?) Anyway, I would also like to pass along that the Creative ZEN Nano Plus DOES work using Rhythmbox at it's default settings; just drag and drop the folders/files.  I did discover though that you  have to enable View>'Show Hidden Files' because when deleting files in the usb disk, the .trash folder is hidden.  I do appreciate everyone providing these guides.  Tahnk you very much.

---

### Post by msak007 on 2006-09-09
> **Guns90 said:**
> FYI.  I just wanted to add that this guide does NOT work for the Creative ZEN Nano Plus (1G) player.  I followed the thread twice and I get an error message saying something like 'No Jukebox Found'.  (Maybe that's because I don't have a 'Jukebox', huh?)

I'm sorry to hear that you couldn't get it working. I'd still like to know what the output of lsusb is for your device though. Did you run Gnomad as a regular user or root? The reason I ask is because the udev rulesets installed by libmtp and libnjb don't have your device listed. I used to have steps in the instructions for editing those rulesets manually to include new devices, but thought that libmtp was comprehensive so I removed those instructions. Maybe I should add them again...

Anyway please post the output that you get from lsusb so we can see if that's the problem and get it working. Even if you get it working and decide you want to use Rhythmbox instead of Gnomad, this will help the how-to become more useful for others who may want to use Gnomad with the Zen Nano Plus.

---

### Post by Guns90 on 2006-09-09
gary@Faith:~$ lsusb
Bus 003 Device 004: ID 041e:4139 Creative Technology, Ltd Zen Nano Plus
Bus 003 Device 002: ID 03f0:c202 Hewlett-Packard
Bus 003 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:008a Microsoft Corp. Wireless Keyboard and Mouse
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
gary@Faith:~$

Appearanatly, that's not the problem.  I'm willing to keep trying if you have any other ideas.  Oh, and I was running Gnomad as a regular user.

---

### Post by Guns90 on 2006-09-09
I just tried it again.  The exact error window says 'No jukeboxes found on USB bus'.

Also, when I was attempting the initial install, I had downloaded the programs to the desktop.  Later I sent them to trash, but when I try to empty  trash I get "/home/gary/...lbs/detect" cannot be deleted because you do not have permissions to modify its parent folder.  I have five folders in the trash bin: gnomad2-2.2.8; libmtp-0.0.16; libnjb-2.2.5; gnomad2-2.2.8.tar.gz; libnjb-2.2.5.tar.gz.  Could you tell me me how empty the trash? :)

I have to go to home depot.  I'll be back in about three hours.  Thanks.

---

### Post by msak007 on 2006-09-09
Great, now that we have the output of lsusb I have a possible solution to your problem. If you were to run Gnomad as sudo, you would most likely find that the device is detected. As I said before, there are rulesets installed that tell udev who has what permissions to what devices. In this case, your device is not explicitly listed in either ruleset (nomad.rules or libmtp.rules), so the system doesn't know that you have access to it and Gnomad can't scan it. So here's what you do:

1. In the terminal, navigate to the udev ruleset folder:
```
cd /etc/udev/rules.d/
``` 
2. Either install method (manual compile or scripted) should have put a file called "libmtp.rules" in that folder. You have to edit it to add your device. I assume you're using Ubuntu (Gnome), so do the following:
```
gksudo gedit libmtp.rules
``` 
You should see all of the devices supported by libmtp that the devs added to the rules. You'll notice that your device isn't in the "Creative" section. This is why Gnomad can't detect the device when you run it as a normal user, so you have to add it. It's as simple as copying /pasting one of the existing entries and modifying it for your device. So in this case let's take the very first entry that says "Creative Zen Vision" and modify that for your purposes. 

3. Copy the lines below and paste them anywhere in the file (preferrably in the Creative section to keep it all together):
```
# Creative Zen Nano Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4139", SYMLINK+="libmtp-%k", MODE="666"
``` 
The first line is commented and so has no effect on the device, it's just a label for identification purposes so I modified it for your device. The  only change that was made to the second line is the "SYSFS{idProduct}==" part. The Creative vendor ID is 041e, so for your device that should have stayed the same. Your product ID is 4139, so that's what we put in there to tell the system which device you're using. 

5. Once you've done that, save and close the file then restart udev so it'll update the hardware list based on the rules:
```
 sudo /etc/init.d/udev restart
``` 
At that point you *should* be able to run Gnomad as a regular user, and it'll find your device and scan it :). I apologize as this was a mistake on my part and I removed those instructions from the first post. I'll go back and modify the instructions to add those steps for users whose devices aren't in there by default.

Now as far as your trash goes, I've run into that problem sometimes where it won't let me delete folders. I believe it's because of the last step of compiling (sudo make install) where the files are locked by root so it won't let you delete them. I normally Shift+Delete and bypass the trashcan and that's when I get the error. If you've already sent it to trash you'll have to delete the files manually. I'm not sure how it is with Gnome, but in KDE you would have to go to "/home/<username>/.local/share/Trash/files" and then delete the files using sudo rm <filename>. I hope this resolves both of your issues, please let me know if the resolutions provided work.

---

### Post by ParanoidDK on 2006-09-09
I will add his device til the rules files on my script right now.. Then i will hope that will help.

---

### Post by maniacmusician on 2006-09-09
This guide didn't work so well for me. I got it to detect my Zen Touch, but that was about the only thing it did right. It took over 15 minutes to load my library (i have 5,000 something songs). When i tried to transfer songs onto the mp3 player, it would start doing it. and after 10, maybe 20 seconds, it would stop. So i thought it was done. I disconnected the mp3 player, and what do you know; they weren't there. This happens for any number of tracks from 1 to 100. any suggestions would be appreciated,

thanks.

---

### Post by Guns90 on 2006-09-09
msak007, I went back and reinstalled it both manually and scripted.  neither one gives me anything differant than I last told you...'Error   No jukebox found...'.

---

### Post by msak007 on 2006-09-09
**maniacmusician** - Some people with large amounts of data have reported this problem before, and I think it's a problem with libmtp currently. In the past I have suggested to them to disable the "Read extended metadata from jukebox" option in the "Preferences" tab to see if that will help. There's a warning right next to it that says this will be slow on newer (I assume MTP) devices, so disabling that option may speed it up a little but nobody has ever posted back saying if that helps them or not. It's worth a shot. 

As far as the app hanging when you're transferring files, this was supposedly fixed with the 0.0.17 version of libmtp. If you run Gnomad from a terminal, is there any output that indicates the app ran into problems or errors while transferring files? The only other user that has reported using this how-to with a Zen Touch posted early on that there was an error referencing "metadata usecount" when transferring files. He fixed it by modifying a few lines in the source and recompiling libmtp and it worked for him. He said that he submitted it as a bug report so it may have already been fixed because a couple new versions of libmtp have been released since then. [Here's]("http://www.ubuntuforums.org/showpost.php?p=1192215&postcount=40") the post just for reference, I would look at it anyway. If all else fails I would post a bug report on the libmtp site (with any terminal output) and see if they can provide some more insight into the problem. 

**Guns90** - If you've done everything I wrote earlier (modified the libmtp.rules file and restarted udev) and it's still not working, then I'm not sure what else the problem could be. Do you get anything starting Gnomad as root with the device plugged in and turned on?

---

### Post by Guns90 on 2006-09-10
Good morning,  

I just tried it again and get the same thing...'(gnomad2:6804): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed' as a terminal response, and a Gnomad2-2.8.1 Window with an Error window on top of it saying "No jukeboxes found on USB bus".  Some things just aren't meant to be, huh?  At least I can still do everything I want in Rhythmbox.  

Oh, I meant to tell you that 'install' is mispelled in the first step. I know, I'm being petty now.

I can't tell you how much I appreciate the effort you've put in to this problem.  If it wasn't for guys like you, Linux would not be growing in popularity.  Thank you very much.

---

### Post by finding_brains on 2006-09-10
lsusb gives :
Bus 001 Device 004: ID 041e:413e Creative Technology, Ltd
Thanks!;))

---

### Post by slibuntu on 2006-09-10
This is a little off topic, i'm delighted with this howto, it got my Zen Sleek Photo working in Gnomad with it, thanks, but i'm wondering how you get it working in Amarok, how do you configure it? Does anyone know?

---

### Post by msak007 on 2006-09-10
> **Guns90 said:**
> I just tried it again and get the same thing...'(gnomad2:6804): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed' as a terminal response, and a **Gnomad2-2.8.1** Window with an Error window on top of it saying "No jukeboxes found on USB bus"
Well I hate to give up before getting something to work but I understand if you've gotten tired of this - most people would've given up long ago. At least you have an alternative with Rhythmbox (I've been trying to get it working with Amarok myself). One thing in your error concerns me though (I've bolded it) - Gnomad2-2.8.1? That's the version in the repos...are you sure you completely uninstalled / purged everything before following this how-to? Unless that's a typo, that's the source of your problems there - that version doesn't support MTP and is the very I started this how-to. Following this guide to install Gnomad should yield a window at the top that says "Gnomad2-2.8.8".

> **Guns90 said:**
> Oh, I meant to tell you that 'install' is mispelled in the first step. I know, I'm being petty now.
Not being petty at all - bad spelling and grammar are pet peeves of mine as well :). I usually don't use spell check, I guess one slipped. Now to go hunt down the mispelled word![/quote]

> **Guns90 said:**
>  I can't tell you how much I appreciate the effort you've put in to this problem.  If it wasn't for guys like you, Linux would not be growing in popularity.  Thank you very much.

 I appreciate the kind words. As much as I've learned since I started using Linux several months back  (I still have a long way to go), this has pretty much been my only contribution to the community aside from getting my brother and sister to start using Kubuntu :). I can't code, so helping others is about the extent of what I can do. I hope this has helped many people who would've otherwise gone back to Windows to use their MP3 players.

> **finding_brains said:**
> 
Bus 001 Device 004: ID 041e:413e Creative Technology, Ltd
Thanks!:wink:)

I assume this means you got it working :)? Unfortunately your lsusb output doesn't specify exactly what device this is. Fortunately someone else posted earlier in the thread that this output is for a Zen Vision:M - is this correct? Please confirm this.

---

### Post by msak007 on 2006-09-10
> **slibuntu said:**
> This is a little off topic, i'm delighted with this howto, it got my Zen Sleek Photo working in Gnomad with it, thanks, but i'm wondering how you get it working in Amarok, how do you configure it? Does anyone know?
I've been wondering the same thing myself. 1.4.2 supported libmtp, but no versions >0.0.12 so it was worthless. 1.4.3 *supposedly* fixed this problem, but I just upgraded the other day and it's still not working. I suppose that it wasn't compiled with that support. You have to compile Amarok with the "--with-libnjb" and "--with-libmtp" flags to get the support, but nobody can tell me if the version in the repos was compiled with these options. I asked [here]("http://www.ubuntuforums.org/showthread.php?t=251775"), but nobody has even attempted a response. I tried compiling compiling manually a couple days ago and ran into errors (not sure of all the dependencies or what flags are needed just yet), so I thought I'd ask about how the version in the repos was compiled before trying again. Guess I'll try again - maybe if I get it working I'll write another how-to :).

---

### Post by Guns90 on 2006-09-10
Well msak007, if you can still see things in my script that are wrong, then I'll hang in there a little longer and try to wip this thing.  I went back and did a purge of gnomad2.  I also went to my home directory and deleted the gnomad_install folder and all of it's contents.  I also went to Synaptic and double-checked that gnomad2, libmtp, and libnjb were not installed.  I started from the beginning and everything was going great until I got to the checkinstall, then I got this...

gary@Faith:~/gnomad_install/gnomad2-2.8.8$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> gnomad2-2.8.8 file for gnomad2
>>

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values:

0 -  Maintainer: [ root@Faith ]
1 -  Summary: [ gnomad2-2.8.8 file for gnomad2 ]
2 -  Name:    [ gnomad2 ]
3 -  Version: [ 2.8.8 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad2-2.8.8 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8/src'
make[2]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gnomad2' '/usr/local/bin/gnomad2'
/usr/bin/install: setting permissions for `/usr/local/bin/gnomad2': No such file or directory
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8/src'
make[1]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8/src'
Making install in doc
make[1]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8/doc'
make[2]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8/doc'
make[1]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8/doc'
Making install in po
make[1]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8/po'
/home/gary/gnomad_install/gnomad2-2.8.8/install-sh -d /usr/local/share/locale
if test -n "ca de es fi fr it nl no pl sco sv"; then \
          linguas="ca de es fi fr it nl no pl sco sv"; \
        else \
          linguas=""; \
        fi; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/gary/gnomad_install/gnomad2-2.8.8/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/gnomad2.mo; \
            echo "installing $lang.gmo as $dir/gnomad2.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/gnomad2.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/gnomad2.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/gnomad2.mo.m; \
            echo "installing $lang.gmo.m as $dir/gnomad2.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/gnomad2.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/gnomad2.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
/usr/bin/install: setting permissions for `/usr/local/share/locale/ca/LC_MESSAGES/gnomad2.mo': No such file or directory
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/de/LC_MESSAGES/gnomad2.mo': No such file or directory
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/es/LC_MESSAGES/gnomad2.mo': No such file or directory
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/fi/LC_MESSAGES/gnomad2.mo': No such file or directory
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/fr/LC_MESSAGES/gnomad2.mo': No such file or directory
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/it/LC_MESSAGES/gnomad2.mo': No such file or directory
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/nl/LC_MESSAGES/gnomad2.mo': No such file or directory
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/no/LC_MESSAGES/gnomad2.mo': No such file or directory
installing no.gmo as /usr/local/share/locale/no/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/pl/LC_MESSAGES/gnomad2.mo': No such file or directory
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/sco/LC_MESSAGES/gnomad2.mo': No such file or directory
installing sco.gmo as /usr/local/share/locale/sco/LC_MESSAGES/gnomad2.mo
/usr/bin/install: setting permissions for `/usr/local/share/locale/sv/LC_MESSAGES/gnomad2.mo': No such file or directory
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gnomad2.mo
make[1]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8/po'
make[1]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8'
make[2]: Entering directory `/home/gary/gnomad_install/gnomad2-2.8.8'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/application-registry" || mkdir -p -- "/usr/local/share/application-registry"
 /usr/bin/install -c -m 644 'gnomad2.applications' '/usr/local/share/application-registry/gnomad2.applications'
/usr/bin/install: setting permissions for `/usr/local/share/application-registry/gnomad2.applications': No such file or directory
test -z "/usr/local/share/applications" || mkdir -p -- "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'gnomad2.desktop' '/usr/local/share/applications/gnomad2.desktop'
/usr/bin/install: setting permissions for `/usr/local/share/applications/gnomad2.desktop': No such file or directory
test -z "/usr/local/share/pixmaps" || mkdir -p -- "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 'gnomad2-logo.png' '/usr/local/share/pixmaps/gnomad2-logo.png'
/usr/bin/install: setting permissions for `/usr/local/share/pixmaps/gnomad2-logo.png': No such file or directory
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/gary/gnomad_install/gnomad2-2.8.8'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

gary@Faith:~/gnomad_install/gnomad2-2.8.8$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                [ ok ]
gary@Faith:~/gnomad_install/gnomad2-2.8.8$ gnomad2
bash: gnomad2: command not found

What do you think?

---

### Post by advance on 2006-09-10
Well, I thought I had everything figured out......

until my sister borrowed my Zen Touch, wiped my songs off of it, and returned it with 2632 of her own songs on it.

so what did i want to do? connect it to my computer and go through the stuff she put on and make it my own again.....but now i'm getting:

```
advance@nicksbox:~$ gnomad2
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
Segmentation fault
advance@nicksbox:~$
```

argh. ](*,)

---

### Post by Brokenrgv on 2006-09-10
thanks again the script is awesome what a time saver thanks heaps :)

---

### Post by robgue on 2006-09-11
i have a zen vision m. I got it working through gnomad2 with the script above which is nice. Of course i'm also waiting for amarok to be compiled with mtp support. Keep us up to date with your progress msak007. maybe another how to... thanks.:)

---

### Post by msak007 on 2006-09-11
**Guns90** - That's it, I'm throwing in the towel! :) Seriously though...I have a few suggestions if you're willing to try but if you uninstalled everything it may be easier at this point to just install the pre-packaged .deb that the script installs rather than compiling manually (if you already installed libnjb and libmtp). Go to the gnomad_install directory and do 
```
wget http://ubuntu.moonman.se/i386/gnomad2_2.8.8-1_i386.deb
sudo dpkg -i gnomad2_2.8.8-1_i386.deb
```That I think would be the easiest solution at this point. If you'd rather try to figure it out then we can try. 

I can't really tell what's going on in the output - alot of errors about missing files and directories and "Nothing to be done" output. When you say you purged Gnomad, libnjb, and libmtp, did you uninstall them using Synaptic or the terminal (apt)? If you're not sure something was completely purged when you uninstalled it, you can issue a 
```
sudo dpkg -r <app name>
``` in the terminal. This will purge any config files that *may* have been left behind if an app wasn't properly or completely purged. libnjb and libmtp don't seem to be causing any problems, so I would try this with gnomad (sudo dpkg -r gnomad2) - you may have not purged it when you uninstalled 2.8.1 and tried to install 2.8.8. Aside from that I really don't know what to tell you.

**Advance** - Does your sister use Windows? The only thing I can think of is that it wrote something on there that can't be read using libmtp - someone had this same issue several days ago and a reformat fixed it. I know it's not the optimal solution if you're going back and forth between OSes but it's all I can think of if it was working before, but not after. Besides...she wiped out all your stuff, wipe out hers :p.

---

### Post by carlosraniery on 2006-09-14
Please people, I'm having problems to do 'make' in gnomad2-2.8.8 directory, when I do ./configure I get these message:
```

Configuration :
---------------

 Source code location .: .
 C Preprocessor .......: gcc -E
 C Compiler ...........: gcc -g -O2
 C Linker .............: gcc
 GTK+ version .........: 2.8.20
 libgnomeui version....: NOT USED
 libnjb version........: 2.2.5
 libmtp version........: 0.0.18
 id3tag version........: 0.15.0b
 Install path .........: /usr/local

 Now type 'make' to build gnomad2 2.8.8,
 and then 'make install' for installation.

```
But when I do 'make' I get a lot of errors
[http://www.inf.ufrgs.br/~crpsantos/downloads/errors.png]("http://www.inf.ufrgs.br/~crpsantos/downloads/errors.png")
Before I installed libmtp-0.0.18 and libnjb-2.2.5

---

### Post by sshyperion on 2006-09-15
Thanks for the step by step instructions!  i think they all worked out although when i try to run gnomad2.1 (gnomad2 doesn't work for me) I get the following:

./gnomad2.1: line 1: .TH: command not found
./gnomad2.1: line 2: .SH: command not found
./gnomad2.1: line 3: gnomad2: command not found

line 3 is the concern of mine and I'm not sure how to resolve this. Any ideas?

---

### Post by redmarshall on 2006-09-16
new to ubuntu.  having issues.  proir to making it an MTP my computer was recognizing my Dell DJ when I listed USB.  (lsusb)  But now it wont recognize it in gnomad2 or when I list usb.  had an error when trying to checkinstall "libnjb-2.2.5"  Screenshot attached.  would this be the reason it does not recognize my dell dj any more?  if it is...what would be the safe way to wipe the old libnjb files so they do not conflict with the new ones I am trying to install.

---

### Post by Spaguettovince on 2006-09-16
Hi every one I'm a very impressed newbie. What a community!
I've been trying to install my Zen jucke box for hours.
I get a message at step 15 (installation of Gnomad)
after the ./configure
I get this

checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

Requested 'libnjb >= 2.2.4' but version of libnjb is 2.0

Yes, I think I installed libnjb 2.0 in a previous attempt and maybe not properly removed. Could any one give a little help concerning this issue?
I really feel close to the goal..
Thanks a lot for help.
Spag

---

### Post by sshyperion on 2006-09-16
ok i've tried installing the program from scratch using hte script code provided in page 1 and the version of gnomad2 was not 2.8.8 (it was 2.8.1) and after reading two pages back or so that the difference apparently was substantial enough to not have things work properly, I got the .deb package for 2.8.8.  Now I have this error message:

gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

I have tried using this command which worked on another similar error for libnjb:

sudo ln -s /usr/local/lib/libmtp.so.3 /usr/lib/libmtp.so.3

and i still get the above error message.  Have I missed something or is it just not destined for me to get this working properly? :p  I had this working two installations of Ubuntu ago (same version) but the permissions to listen to the music transferred from the mp3 player copied to the HD locked me out.

thanks!

---

### Post by Abaddon on 2006-09-16
I'm having the exact same problem as SS Hyperion - with the same error message.

Have tried using the script, and installing the files manually.

Any help greatly appreciated.

Recently installed Dapper ubuntu, with automatix.
Athlon 2700+
1Gb Ram
Separate WXP/Ubuntu Drives.

---

### Post by msak007 on 2006-09-17
Hey guys sorry I haven't been answered any of your posts, been busy the past week. First off I want to start by letting you all know there's a new version of libmtp released today, 0.0.19 - it adds support for the **Creative Zen V**. For those of you using that device (such as Boelcke who posted several pages back) and can't get it working, upgrade to 0.0.19 immediately - the device is now officially supported. Manual instructions have been updated.

**sshyperion** and **Abadon** - The error you're getting is indicative of libmtp not being installed in /usr - I went through that when I first started all this, even creating symlinks didn't work. If you don't pass any options, it installs in /usr/local and Gnomad expects the lib in /usr. Uninstall / purge libmtp, and install it using "--prefix=/usr" and try again.

**Spaguettovince** - Try using Synaptic to search for any libnjb packages installed and uninstall them using the "purge" option. I believe if you right-click on a package you get the option to purge a package which will remove any config files as well. While you're at it, purge any versions of Gnomad and libmtp installed, then start from the beginning.

**redmarshall** - The output clearly indicates that you still have libnjb-dev installed, and the version of libmtp you're trying to install is trying to overwrite a file that belongs to that package. Just like the advice I've given the others, search in Synaptic for any version of libnjb installed (linbj5, libnjb1, libnjb-dev, etc.), purge them, and reinstall libnjb from source.

**carlosraniery** - Are you sure you've installed all the dependencies and that everything is up to date? Your output says that id3tag is at version 0.15.0b. The version I have installed is 0.15.1b. Your output shows a lot of id3 errors so that may have something to do with it. If all else fails, uninstall / purge everything and then try to install using the script so you don't have to compile.

I hope I haven't missed anybody, let me know if you guys have success or if you're still having problems.
__

---

### Post by Spaguettovince on 2006-09-17
Hi Thanks Msak007!
Unfortunately it didn't work it still get the same message after purging all the libraries.
In fact the full message is :
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

Requested 'libnjb >= 2.2.4' but version of libnjb is 2.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
I don't know if it can help...
Thanks again for your time.
Spag

Ps there is a minor spelling mistake at step 1. A S is missing...
sudo aptitude in[COLOR="Red"]S[/COLOR]tall build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev checkinstall

Not so important but disturbing for beginners...

---

### Post by maniacmusician on 2006-09-17
> **msak007 said:**
> **maniacmusician** - Some people with large amounts of data have reported this problem before, and I think it's a problem with libmtp currently. In the past I have suggested to them to disable the "Read extended metadata from jukebox" option in the "Preferences" tab to see if that will help. There's a warning right next to it that says this will be slow on newer (I assume MTP) devices, so disabling that option may speed it up a little but nobody has ever posted back saying if that helps them or not. It's worth a shot. 

As far as the app hanging when you're transferring files, this was supposedly fixed with the 0.0.17 version of libmtp. If you run Gnomad from a terminal, is there any output that indicates the app ran into problems or errors while transferring files? The only other user that has reported using this how-to with a Zen Touch posted early on that there was an error referencing "metadata usecount" when transferring files. He fixed it by modifying a few lines in the source and recompiling libmtp and it worked for him. He said that he submitted it as a bug report so it may have already been fixed because a couple new versions of libmtp have been released since then. [Here's]("http://www.ubuntuforums.org/showpost.php?p=1192215&postcount=40") the post just for reference, I would look at it anyway. If all else fails I would post a bug report on the libmtp site (with any terminal output) and see if they can provide some more insight into the problem. 

The "read extended metadata" option was already unchecked...it's still taking forever to load the songs. It's already been 15 minutes and still nothing. fast forward 10 minutes. It's connected and doesn't report any errors. Ok this is weird...it's working now. [feels ashamed]. I havn't done anything different. But thanks for the post anyways.

Is there possibly any other way to do this? to be honest it's a huge hassle to wait 20 minutes for it to read the data from the player. i deleted my windows partition so I can't go back and use it. and it doesn't work through vmware. I'm surprised that Creative doesn't provide support...they have linux support for some of their products. Oh well.

please let me know if you ever figure out a way to get it to load faster

edit: also, is there any other  advantage to 0.0.19 other than support for that player?

---

### Post by Apotheosis on 2006-09-17
I can not get it to work for anything.  I first tried the auto-intall and that didn't work so I tried your step-by-step instuctions and I had trouble installing Gnomad, with the same exact problem as the  first guy with problems in this thread.  I have tried the fixed you posted to said problem and that didn't seem to work.  I tried installing Gnomad through Synaptic and it said that one of the things you had me install interfered with it.  Now, I just want to give up and uninstall everything, but I can't.  I tried trashing the files I had to download and it told me I didn't have the permission to delete them.  I tried the dpkg like it said in the terminal and it told me I wasn't the superuser.  I tried to beg to differ, but it wouldn't hear it.  Any suggestions?

---

### Post by ntetreau on 2006-09-18
Okay, here's how you can sync your task list and calendar with your Microphoto and maybe other devices.

First, find out the name your device use for the calendar file by using Gnomad2 file transfer tab.  By sorting the files by size (the ics files are very small, ~5000 bytes), you'll quickly find it.  Mine was called 6651416.ics (and the contact file 6651416.vcf).  I believe you can safely leave the original file there or copy it in a safe place but the device somehow can support multiple ics files and uses the last one only.

Now, save your calendar to a iCalendar file (ics).  In Evolution this is done by right-clicking your Personnal calendar and then "Save to Disk".  Use the file name found on the device, for me 6651416.ics .

Then convert the calendar.ics file from unix to dos:

```
unix2dos 6651416.ics
```

Send it to the device in the My Organizer folder:  ```
./libmtp/examples/sendfile -f "My Organizer" -t ics calendar.ics
```

My output:
```
Sending file:
Autodetected device "Creative Zen MicroPhoto" (VID=041e,PID=413c) is known.
PTP: Opening session
Connected to MTP device.
parent_id = 109
Sending file...
Progress: 10858 of 10858 (100%)
PTP: Closing session
OK.
```

Unfortunately, the vcf file type is not yet recognized by libmtp's sendfile but once it is, it should be possible to sync the contacts as well.  Actually, the vcf file from the device can be imported perfectly into an Evolution addressbook.

Another drawback is that Evolution does not merge the tasklist and the calendar into a single ics file.  That means that uploading a calendar file will erase your tasklist and uploading the tasklist (using the same method and file name, 6651416.ics for me) will erase your calendar entries.  If you know a way to merge the two ics files, please let me know!

Nic

---

### Post by HotShot on 2006-09-18
> **sshyperion said:**
> ok i've tried installing the program from scratch using hte script code provided in page 1 and the version of gnomad2 was not 2.8.8 (it was 2.8.1) and after reading two pages back or so that the difference apparently was substantial enough to not have things work properly, I got the .deb package for 2.8.8.  Now I have this error message:

gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

I have tried using this command which worked on another similar error for libnjb:

sudo ln -s /usr/local/lib/libmtp.so.3 /usr/lib/libmtp.so.3

and i still get the above error message.  Have I missed something or is it just not destined for me to get this working properly? :p  I had this working two installations of Ubuntu ago (same version) but the permissions to listen to the music transferred from the mp3 player copied to the HD locked me out.

thanks!

i had this problem after fresh install with the script.
okay, not the best way, but i created a symlink like 

/usr/lib/libmtp.so.3 -> /usr/lib/libmtp.so.2.1.1

and it works for me (zen micro)

---

### Post by MiXor on 2006-09-19
:D That works for me!! Yay! Ubuntu forum rocks!!!

---

### Post by sshyperion on 2006-09-19
> **HotShot said:**
> i had this problem after fresh install with the script.
okay, not the best way, but i created a symlink like 

/usr/lib/libmtp.so.3 -> /usr/lib/libmtp.so.2.1.1

and it works for me (zen micro)

after figuring out how to properly match up the symlink command through mc (midnight commander or whatever) it works. FINALLY!


THANK YOU TO EVERYONE WHO HELPED! ^_^

---

### Post by exkalibur on 2006-09-19
Same issue and solution here too...!But the funny part : Just put a new machine together, one drive is Windows XP and the other one is Unbuntu. Both freshly installed this week. It took maybe 15 minutes to get my zen micro going (gnomad)on Ubuntu but still not on Windows : Had to download over 50 megs of files (driver, media source and jukebox) to finally get it....Go figure :o))

---

### Post by Blankman on 2006-09-20
> **sshyperion said:**
> after figuring out how to properly match up the symlink command through mc (midnight commander or whatever) it works. FINALLY!


THANK YOU TO EVERYONE WHO HELPED! ^_^

I have followed the steps set out by MSAK007 to install Gnomad2.  However, having gone through teh process I have the same response as sshyperion; namely

*gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory*

Since I had the same error, I thought I would try to follow the thread to resolve my problem.  Alas, I was stumped by comments like:

[I]"...I created a symlink like
/usr/lib/libmtp.so.3 -> /usr/lib/libmtp.so.2.1.1"[/I]

I have looked at "what's a symlink?" ([http://www.ubuntuforums.org/showthread.php?t=73096&highlight=symlink)](http://www.ubuntuforums.org/showthread.php?t=73096&highlight=symlink)), but quite frankly simply cannot understand the explanation (I'm pretty new to linux and have found it at times to be rather daunting!!).  That being the case I have no idea how to create a symlink to gettry to get my Creative Zen up and running - this is really frustratin the hell out of me!!  I've tried to follow the thread through, but am just getting in a tangle.  Are you able to help?  Please:
1. can you talk me through setting up a symlink to get Gnomad2 up and running?
2. how did you figure out how to properly match up the symlink command through mc (midnight commander or whatever) - whatever that means?

Thanks

---

### Post by msak007 on 2006-09-20
I find it odd that everybody is having problems with libmtp.so.3 all of a sudden. What versions of Gnomad / libmtp are you guys using? I know that when I previously had libmtp-0.0.16 installed (with Gnomad 2.8.18 ), I had libmtp.so.3. I now have Gnomad 2.8.18 w/ libmtp-0.0.19 installed and no longer have the libmtp.so.3 file, but I don't get the errors when loading the app - it starts up as it always has and scans the device. Can you guys elaborate a little more on your exact steps for installing, and when you started having problems (e.g. was this a first-time install, upgrade from an older version, manual or scripted, etc.)? I guess I could add that step to the instructions in case you encounter it, but I'd like to know if this is a bug that needs to be reported because I'm not having the same issues. Just an FYI, I completely purged / uninstalled Gnomad before installing libmtp-0.0.19, and recompiled Gnomad again (even though it was the same version) after installing libmtp.

---

### Post by Spaguettovince on 2006-09-21
Hi there!
I am sorry to pollute the forum but i still have the problem with libnjb.
Apparently an older version of libnjb is detected when I try to install Gnomad. I tried as much as I could to clean the files (with synaptic) with no success.

I copy a previous message which didn't have a reply. Thanks a lot and have fun!
Spag

Hi Thanks Msak007!
Unfortunately it didn't work it still get the same message after purging all the libraries.
In fact the full message is :
checking for GN... configure: error: Package requirements ( glib-2.0 gthread-2.0 libnjb >= 2.2.4 gtk+-2.0 ) were not met:

Requested 'libnjb >= 2.2.4' but version of libnjb is 2.0

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
I don't know if it can help...
Thanks again for your time.
Spag

Ps there is a minor spelling mistake at step 1. A S is missing...
sudo aptitude inStall build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev checkinstall

Not so important but disturbing for beginners...

---

### Post by HotShot on 2006-09-22
> **Blankman said:**
> 
1. can you talk me through setting up a symlink to get Gnomad2 up and running?
2. how did you figure out how to properly match up the symlink command through mc (midnight commander or whatever) - whatever that means?

Thanks
try this:

1. start mc with "sudo mc".
2. F9
3. go to the File-Menu
4. SymLink
5. Existing Filename is "/usr/lib/libmtp.so.2.1.1"
6. Symbolic link Filename is "/usr/lib/libmtp.so.3"
7. Ok
8. leave mc and start gnomad2

everything without the quotes. sorry for the missing ln-syntax

---

### Post by Spaguettovince on 2006-09-23
Hello!
I found the problem concerning the libnjb version.
The problem was that there was two different libnjb.pc files with different informations in different place of the file system. I removed the one concerning version 2.0. Now ./configure works fine.

Today the problem is similar to the one carlosraniery had a few post ago. Compilation problem. Id3tag is updated to 0.15.1b according to synaptic but I get the following error copiling.
jukebox.c: Dans la fonction «jukebox_discover» :
jukebox.c:763: attention : passing argument 1 of «g_strdup» makes pointer from integer without a cast
jukebox.c: Dans la fonction «jukebox_select» :
jukebox.c:816: erreur: «NJB_TURBO_ON» undeclared (first use in this function)
jukebox.c:816: erreur: (Chaque identificateur non déclaré est rapporté une seule fois
jukebox.c:816: erreur: pour chaque fonction dans laquelle il apparaît.)
jukebox.c:818: erreur: «NJB_TURBO_OFF» undeclared (first use in this function)
make[1]: *** [jukebox.o] Erreur 1
make[1]: quittant le répertoire « /home/vincent/gnomad_install/gnomad2-2.8.8/src »

As usual any help welcome and sorry to bother.
Spag

---

### Post by schwascore on 2006-09-25
Has anyone figured out how to create folders in Gnomad?   Nothing happens when I try to create a new folder.  Additionally, Gnomad can not see folders already on the system.  Is folder support not part of MTP Basic?

I am using a Zen Vision:M and if I can figure this problem out then my player will be 100% functional.

---

### Post by Boelcke on 2006-09-26
Ah, the sweet feeling of success.  Thanks to all who made this possible.

Msak007, as you mentioned, the latest verstion of libmtp (0.0.19) now supports the Creative Zen V, and it worked like a charm.  Just absolutely beautiful.

I uninstalled the old packages with Synaptec.  Then, for good measure, I also did the, "sudo aptitude purge gnomad2." Since the automated script is still on version 18, I did the manual install.  My only problem was that intially, the install of gnomad failed out.  It seems that there was a broken link-file, /usr/local/man.  I guess it was left over somehow from the last installation.  One "sudo rm /usr/local/man" later, and I was able to install gnomad.

Loading music onto it as I type.

---

### Post by Boelcke on 2006-09-26
Please pardon me if this has already been addressed, but, have these packages been suggested for addition to any of the ubuntu repositories?  It would certainly be slick for so many users if the only thing they had to do was click a few items in Synaptic.

---

### Post by Moozacman on 2006-09-27
Okay, all I can say is THANK YOU SO MUCH.  It was driving me crazy that I couldn't get my Dell DJ working, and then I stumbled apon this thread...it appears to be working as Gnomad is scanning my DJ as we speak.  I'm so happy to not have to use my Windows partition to manage my music!

---

### Post by meastp on 2006-09-28
Hi!

I just bought a Creative Zen V Plus 4GB, and now I can't get it to work. I followed the howto.

Log:

```

meastp@dilbert:~$ gnomad2
No MTP devices.
PDE device NULL.

```

I have a handful of external disks, so I tried rebooting without them. I get the same "error".

EDIT:

Ups.. forgot to try running gnomad2 as root.

```

meastp@dilbert:~$ sudo gnomad2
Password:
Autodetected device with VID=041e and PID=4152 is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
Connected to MTP device.
Queried Creative Zen V Plus

```

Success! Thank you!

How can I succeed when running gnomad2 as a regular user?

---

### Post by villindesign on 2006-09-28
This works great for my creative zen microphoto running firmware 1.20.01_0.00.65. Thanks a lot & good work!

---

### Post by Sukarn on 2006-09-30
Its a really long thread, and my question may already have been answered, but it would take really long to look through 22 pages and i have exams coming up so I cannot do that.

I get this when installing libmtp and libjnp. I have done it till checkinstall, but hotplug.sh gives me this. I do not know what this means.
```
~/MyDownloads/tmp/Gnomad/libmtp-0.0.19$ sudo sh hotplug.sh
hotplug.sh: 12: function: not found
hotplug.sh: 32: cannot open : No such file
no
```

Please help me if you know how to fix this.
Manual copying of the two files works but Gnomad2 it is not able to transfer any files from my computer to the device. Copying from device to the computer works fine.

PS: I have a Creative Zen Portable Media Centre (listed in windows as an MTP device)

---

### Post by Angel_V on 2006-09-30
I install gnomade by folowing Script install instructuons and when i try to run gnomade I get the folownig eror

> gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

:confused: :( 

Someone know how to fix it?


TNX :)

---

### Post by ntetreau on 2006-09-30
> **Sukarn said:**
> Its a really long thread, and my question may already have been answered, but it would take really long to look through 22 pages and i have exams coming up so I cannot do that.

I get this when installing libmtp and libjnp. I have done it till checkinstall, but hotplug.sh gives me this. I do not know what this means.
```
~/MyDownloads/tmp/Gnomad/libmtp-0.0.19$ sudo sh hotplug.sh
hotplug.sh: 12: function: not found
hotplug.sh: 32: cannot open : No such file
no
```

Please help me if you know how to fix this.
Manual copying of the two files works but Gnomad2 it is not able to transfer any files from my computer to the device. Copying from device to the computer works fine.

PS: I have a Creative Zen Portable Media Centre (listed in windows as an MTP device)

Try running like this instead:
```
sudo bash hotplug.sh
```
 that should work.

Nic

---

### Post by Kivrin on 2006-10-01
Brilliant, thank you! My MicroPhoto is working perfectly, and the version of Gnomad I have allows me to create and edit playlists.

---

### Post by Brokenrgv on 2006-10-03
I get it working and then sometimes get this, anyone else get this, any fix

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: unexpected async reply (sequence 0x420)!
Xlib: sequence lost (0x1052c > 0x5bb) in reply type 0x1c!

sorry its a zen vision m and im running kubuntu 6.06.1

---

### Post by puppy on 2006-10-04
I get the following error, the same as the above poster (I was following the install script)

"gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory"

Any suggestions? :-k

EDIT - Fixed, I followed post #201 in this thread to resolve the problem  :mrgreen:

---

### Post by Bloch on 2006-10-09
I got this error message too:

> error while loading shared libraries: libmtp.so.3: cannot open shared o bject file: No such file or directory

I installed using the instructions in the first message of this post (using the script to download and install, not the compiling option) (which has been re-editied since the original date)

Can the original poster go the extra mile and edit it again so that new users can install this software? After all the great work in making this it would be a shame for users (see recent posts) to give up in frustration.

---

### Post by cezdeville on 2006-10-11
first of all i'd like to thank you all guys. yesterday i bought myself Creative Zen V, but couldn't predict that it can be so “Linux-unfriendly” (my fault, haven't checked it earlier). fortunately i found any necessary solutions here!
lucky me, i can even start Gnomad2 from Ubuntu menu, i don't have to use terminal at all!

one thing i've noticed struggling with my player: it doesn't work with Ubuntu at the beginning. you'll have to connect it first with computer with WinXp on board. only after updating its own drivers it will mount properly.
at least i think so, i have no other idea why it was not detected by Gnomad2 before (mentioned error 767).

hope it helps someone...

cheers!

---

### Post by Villevee on 2006-10-13
I'm getting desperate with this Zen thing... Im very new to linux, just installed ubuntu 4 days ago. I know I maybe shouldn't get this deep at start but heck; I installed Beryl as my first task in linux.

The problem is as follows:

I'm not able to compile gnome 2.8.8. I get error message that says "No package 'gtk+-2.0' found". Okay... figured out that I need to install that so I downloaded it and all dependencies (glib2, ATK and Pango) from gtk.org. the GLib 2 I built and installed with no problem whatsoever but when installing ATK the error message says:

[FONT="Courier New"]*** 'pkg-config --modversion glib-2.0' returned 2.2.3, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files[/FONT]

When I looked for GLib in Synaptic I found out that my newly installed glib2 was in the list, but there was also different version: libglib2.0-0 version 2.10.3-0ubuntu1!

So I acted according to compiler and tried to uninstall that one. Dialog said that if I uninstalled libglib2.0-0, some dependencies are to be uninstalled too. Well, in the list there was practically every program I'm using and it measured 755 Mb, so I didn't choose that road...

I'm not quite sure what modifying my LD_LIBRARY_PATH means. Can I point the ATK compiler to RIGHT Glib version by doing that? and how to do that anyway...?

I've also tried to install Gnomad2 thru synaptic, there I get version 2.6.1 if I remember right; It just says "no jukebox found in USB port". My zen uses PlaysForSure Firmware and I've installed libmtp and libnjb as described in this guide. Do I really need to build Gnomad2 from source if I want it to work?

I really, really really love the guy who can help me out in this. Cheers, Villevee

-- edit:

When sudo gnomad2 (the version I installed from Synaptic), I get the following error message:

[FONT="Courier New"](gnomad2:10313): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `err or == NULL || *error == NULL' failed[/FONT]

---

### Post by ntetreau on 2006-10-13
Hi Vellevee,
don't worry too much about being new at linux, just keep good backups!  I am not an expert either but I'll try to give you a hand.  Usually, when compiling a program like gnomad2, it will check for dependencies which it needs to run.  When it asks you about a missing dependency, let's say "No package 'gtk+-2.0' found", it usually means it has not found the development package for gtk+. A quick search in synaptics for "gtk+ devel" brings a list of package, one of which is libgtk2.0-devel.  This is surely the one you need.  You will find that after a few sucessfull compiles, you won't be needing to install so many "devel" packages as you will have them already.

Personnaly, I try not to install packages that are found outside the repositories, unless it has been tested and recommended by someone in the forum.  If you compiled something that you'd like to remove, you can usually remove it cleanly with

sudo make uninstall

if I remember well.  Hope this helps, good luck!

Nic

---

### Post by spidernik84 on 2006-10-14
Just bought a Zen V Plus, following your guide allowed me to have a fully functional player under linux, thanks so much :)

Here's the line to be addedd to /etc/udev/rules/45-libnjb.rules to allow gnomad2 access to the player via standard user:

```
# Creative Zen V Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4152", GROUP="plugdev", MODE="0660"
```

Looking further for some integration with nautilus...transfer is kinda slow, even over usb 2.0

---

### Post by agnostic on 2006-10-15
I have got an old Model, the Creative Zen Touch and followed the instructions on how to compile from source. When it came to the point where i should ./configure gnomad2 itself, it showed some errors about missing dependencies, glibc, gtk+-2.0 etc. 

All thats left now is gtk+, which needs the libpango1.0-dev. When i try to install it, it says that libpango1.0-dev depends on "»libpango1.0-0 (=1.12.2-0ubuntu3)«, but »1.12.3-0ubuntu3« is going to be installed". 

Here's my sources.list: 

```
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper universe

deb-src http://at.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

deb http://at.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

#fuer GLX, compiz und Konsorten:
# deb http://automatix.czessi.net/packages dapper stable
# deb http://media.blutkind.org/xgl/ dapper main

#Givre's repository (ntfs-3g & fuse 2.5.3)
# deb http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main
# deb-src http://ntfs-3g.sitesweetsite.info/ubuntu/ dapper main

#Givre's repository (ntfs-3g & fuse 2.5.3)
deb http://flomertens.keo.in/ubuntu/ dapper main
deb-src http://flomertens.keo.in/ubuntu/ dapper main

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

btw, the link to the script (gnomad_mtp.sh) is down!

---

### Post by watermonkey on 2006-10-15
Creating folders on your zen vision m? anyone? how about album art?

Any sugestions would be great

thanks!:)

---

### Post by koholint1000 on 2006-10-16
Will it work with the MicroPhoto?
You see, I have really slow internet; and it'd be a waste of time downloading it if it won't work...

Thanks!

---

### Post by ntetreau on 2006-10-16
Yes, it works perfectly with the Microphoto, that's what I have!

Nic

---

### Post by ParanoidDK on 2006-10-20
Hey all.... My site have been down for an little week now... The reson that my site have been down was becouse an hacker have placed an bot that he was able to steal my accounts with.. And the lack of updates of the script is becouse i lost my coder laptop to an broken harddrive... i have got it up and running again... So with in the next 7 dayes i will have it all up and running again.. 

Greetings from the cold north.
ParanoidDK in the 2 ºC cold sweeden.

---

### Post by koholint1000 on 2006-10-21
Every time i try the manual compilation, i get an error during installing libnjb, aslong the lines of "installing debain package -- failed". I don't know why this is, but it results in me not being able to install gnomad2 (it says it wont bcoz libnjb isnt installed).
:-k 
Also, when i install the scripted instructions, it uns, installs, but wont actually run gnomad2 bcoz it grumbles on about libmtp not being installed properly.
Plz help; i REALLY don't want to have to boot into windows just to put a track or 2 onto my mp3 player.
:confused: 
(its a micro-photo)(and im on ubuntu)
](*,)

(PS, when it finally does start working, I don't hae to boot up the PC with the player connected do i?)

---

### Post by ntetreau on 2006-10-21
Hey Kolo,
sorry to hear you are having problem but there's hope, I have been  enjoying my Microphoto for the last 6 months on ubuntu and you will get it to work as well.  For that though, you may need to provide people with more details about your error, at exactly what point of the installation do you get the "installing debian package --failed"?  Any other error messages?  If it can make your life easier, you could try to skip libnjb, install libmtp and Amarok from the repositories.  Amarok has been working with my Microphoto for months now.  I have yet to check if it does out of the box though as I have been following this thread ([http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn]("http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn")) 
to get a scripted compilation of amarok.  Try first with the repository version of amarok and then with the svn version from the thread.  

By the way, someone else may have provided you with a better solution before then anyway.  But if you go that route, don't forget to "--enable-mtp" during amarok compilation (the script asks you at the beginning for your compilation options).  

Nic

P.S.:  I hear other audio players support it now, Banshee for example.

---

### Post by Nojatron on 2006-10-22
.

---

### Post by surak on 2006-10-23
I tried the scripted version for edgy, but it didn't work.

---

### Post by ntetreau on 2006-10-23
> **surak said:**
> I tried the scripted version for edgy, but it didn't work.

If you need help with the issue you are having you'll  need to add more details, much much more!  Let me guess, you had an error message letting you know you were missing something?  Try to search in synaptics for "-devel" packages that correspond to what the compilation script is complaining that is missing.  I installed it straight after my edgy installation and I did have to install a whole bunch of devel packages, the names of which are given to you as you try to compile!

Nic

---

### Post by sanderman on 2006-10-24
I get these weird errors:

```

The program 'gnomad2' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 1051 error_code 5 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

The program will not start and sometimes it hangs when getting file and track metadata, yes the Zen V is connected to the USB and the USB is working. I don't know what's causing the problem ](*,)

---

### Post by drr422 on 2006-10-26
I tried the from source installation as well, but it didn't work, so then i tried the script install, in which i get this error if i try to run gnomad2:

dustin@dlap:~/gnomad_install$ gnomad2
gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

If anyone can suggest anything, that would be great.

---

### Post by OrganicPanda on 2006-10-26
Hey all great guide, I was struggling compiling gnomad - I was getting this error:

```

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

```

After about 20 minutes of frantic googling I found a package called libxml-parser-perl (in repos) which fixed the problem, :)

---

### Post by Nomer on 2006-10-29
Wow dude, thnx for the howto :D It works for me on my Zen Sleek Photo :D Thnx again

---

### Post by iamnafets on 2006-10-31
Another success after installing from source and some fancy symbolic linking.  Thanks a bunch guys!

---

### Post by andybleaden on 2006-10-31
Well , just come over to Linux within the last 2 weeks and the big disapointment was when I could not use my Creative Zen Extra. Did lots of looking around and founds lots of pages saying it will not work etc becasue I was stupid enough to update all the firmware!

However got my neighbour to help me ( he converted me to Linux) and with a little messing around and then finding this excellent how to guide for Gnomad 2 we cracked ( ok - he cracked it!) . 

A really huge thanks from me and thanks for all the updating and follow advice....just finished reading all the pages and you have been very busy . Cannot wait for the opportunity if someone can help it add folders of music at a time but that can wait for now. 
Its just enough at the moment to know I can update my full jukebox and do not have to reload windoze:)

---

### Post by Haegin on 2006-10-31
How can I transfer video to my creative vision:m - can I use gnomad2 or is there another program I can get for linux?

---

### Post by Lemvigh on 2006-10-31
I tried using the script and everything seemed to work fine, but when I tried to launch gnomad afterwards it said:
gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

I'm not much into this library-thing but i checked /usr/local/lib and it only had libmtp.so.2 and libmtp.so.2.1.1

Any ideas to what I've done wrong?

---

### Post by msak007 on 2006-10-31
Hey guys, I'm still alive! I apologize for not being active lately but I've been really busy and haven't had much of a chance to do anything. I apologize to all those who've had problems and haven't received a response, I'll try to do my best to help when I get a chance. A few things first:

1. I installed (Kubuntu) Edgy on my laptop this past weekend, and was pleasantly surprised when I plugged in my sister's Creative Zen MicroPhoto and was prompted to open the device using my file manager (Konqueror). It detected the device as a camera (mass storage device), but when I opened it using Konqueror I was able to browse the entire contents, including the folders were pictures are stored (I assume the same would apply to video-enabled devices and the videos folder). I checked and saw that libnjb was installed by default, but libmtp wasn't. Not sure what changed (possibly the new kernel or an updated PTP driver?), but I would like confirmation from other users who have done clean installs of Edgy to see if they can confirm this. Unfortunately the only way to view it was using the camera:// kio-slave in Konqueror, and it wasn't actually mounted as a media device in /media so there was no way to browse to it manually without double-clicking on the Desktop icon. I'll work on getting this how-to updated for Edgy when I get a chance as well, but you may not need it if you can manage the device using your file manager (I'd really like confirmation for Nautilus in Ubuntu).

2. In regards to Edgy, I checked the repos and there is some good news - Gnomad 2.8.3 is in there, as well as libmtp 0.0.18. Gnomad 2.8.3 was the first version that supported libmtp and MTP devices, and libmtp 0.0.18 is a somewhat recent version. So unless you have a specific need for installing the absolute latest version of Gnomad or libmtp (for example, a specific device that is not supported with an older version), you may be able to get by using the versions of Gnomad, libmtp, and libnjb in the repos (no more manual installs or scripts, yay!). I'd also like confirmation from users who try this route on a fresh install of Edgy.

That's it for now, I'll try to clean up the how-to and provide new instructions for Edgy for users who want to upgrade or do a fresh install. Please let me know if you've already installed Edgy (new install, not dist-upgrade) and can confirm my experiences listed above.

---

### Post by pseudo_nz on 2006-11-01
> **Lemvigh said:**
> I tried using the script and everything seemed to work fine, but when I tried to launch gnomad afterwards it said:
gnomad2: error while loading shared libraries: libmtp.so.3: cannot open shared object file: No such file or directory

I'm not much into this library-thing but i checked /usr/local/lib and it only had libmtp.so.2 and libmtp.so.2.1.1

Any ideas to what I've done wrong?


I'm still getting the hang of this myself, and after two goes at installing the software, it finally worked, only to get the same error message that you got.

According to other posts on this thread the problem is solved by creating a symlink (like a detour sign) so that when the program looks for so.3 it actually ends up at 2.1.1

I fixed the problem by downloading MC (a text-based file manager) from the repos and then following the instructions in post #208.  All up, it took about five minutes, and now I'm finally getting to play with my new Vision:M.

---

### Post by Nojatron on 2006-11-01
> **msak007 said:**
> Hey guys, I'm still alive! I apologize for not being active lately but I've been really busy and haven't had much of a chance to do anything. I apologize to all those who've had problems and haven't received a response, I'll try to do my best to help when I get a chance. A few things first:

1. I installed (Kubuntu) Edgy on my laptop this past weekend, and was pleasantly surprised when I plugged in my sister's Creative Zen MicroPhoto and was prompted to open the device using my file manager (Konqueror). It detected the device as a camera (mass storage device), but when I opened it using Konqueror I was able to browse the entire contents, including the folders were pictures are stored (I assume the same would apply to video-enabled devices and the videos folder). I checked and saw that libnjb was installed by default, but libmtp wasn't. Not sure what changed (possibly the new kernel or an updated PTP driver?), but I would like confirmation from other users who have done clean installs of Edgy to see if they can confirm this. Unfortunately the only way to view it was using the camera:// kio-slave in Konqueror, and it wasn't actually mounted as a media device in /media so there was no way to browse to it manually without double-clicking on the Desktop icon. I'll work on getting this how-to updated for Edgy when I get a chance as well, but you may not need it if you can manage the device using your file manager (I'd really like confirmation for Nautilus in Ubuntu).

2. In regards to Edgy, I checked the repos and there is some good news - Gnomad 2.8.3 is in there, as well as libmtp 0.0.18. Gnomad 2.8.3 was the first version that supported libmtp and MTP devices, and libmtp 0.0.18 is a somewhat recent version. So unless you have a specific need for installing the absolute latest version of Gnomad or libmtp (for example, a specific device that is not supported with an older version), you may be able to get by using the versions of Gnomad, libmtp, and libnjb in the repos (no more manual installs or scripts, yay!). I'd also like confirmation from users who try this route on a fresh install of Edgy.

That's it for now, I'll try to clean up the how-to and provide new instructions for Edgy for users who want to upgrade or do a fresh install. Please let me know if you've already installed Edgy (new install, not dist-upgrade) and can confirm my experiences listed above.

The version of Gnomad in the Repo's does not work for me, I had to compile a later version. It may work with other MP3 players, but did not with mine (Zen Vision:M).

When I plug in it (without installing anything as well), it does pick it up as a camera but there's not a lot you can do with it. Ubuntu uses gnome-volume-manager by default to open camera's which picks it up as the right device and gives you an option to import it and that's it. That option does not work...

> **Human Prototype said:**
> How can I transfer video to my creative vision:m - can I use gnomad2 or is there another program I can get for linux?

You should be able to click on the Data Transfer tab and move video across from there. Unless I'm missing something it doesn't support directory structures but you should still be able to copy it across.

---

### Post by msak007 on 2006-11-04
> **Nojatron said:**
> The version of Gnomad in the Repo's does not work for me, I had to compile a later version. It may work with other MP3 players, but did not with mine (Zen Vision:M).

Well I spoke too soon. I just tried the version of Gnomad in the repos, and while it is a recent version unfortunately it was *not* compiled with the libmtp option. So even if you have libmtp installed, it won't detect any MTP devices. However, there is good news...

The Edgy repos do carry dev packages for libnjb and libmtp, which Gnomad will pick up when compiling. In otherwords, as I said before unless you have a specific need for compiling a newer version of libmtp (for example specific device support that's not available in older versions), the only thing you have to compile is Gnomad. Everything else you need is available in the repos. I'll update the instructions shortly.

> You should be able to click on the Data Transfer tab and move video across from there. Unless I'm missing something it doesn't support directory structures but you should still be able to copy it across.

That is correct also. Gnomad doesn't support directories, so yes you can transfer videos over but won't be able to put them in specific folders or directories.

---

### Post by Labyrinth on 2006-11-05
Hello!
Thanks for this great thread.

I am having the following problem.

- I`m on edgy
- I want to make my Creative Zen Touch 20GB run with gnomad2
- I followed both possible paths from the original post in this thread, but I`m getting errors from checkinstall.

The following (after ./configure and make worked perfectly):

(errors at the end)

```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@edgy ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ gnomad2 ]
3 -  Version: [ 2.8.9 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad2-2.8.9 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/src'
make[2]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gnomad2' '/usr/local/bin/gnomad2'
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/src'
make[1]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/src'
Making install in doc
make[1]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/doc'
make[2]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/doc'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
make[2]: Für das Ziel »install-data-am« ist nichts zu tun.
make[2]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/doc'
make[1]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/doc'
Making install in po
make[1]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/po'
/home/labyrinth/gnomad_install/gnomad2-2.8.9/install-sh -d /usr/local/share/locale
if test -n "ca de es fi fr it nl no pl sco sv"; then \
          linguas="ca de es fi fr it nl no pl sco sv"; \
        else \
          linguas=""; \
        fi; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/labyrinth/gnomad_install/gnomad2-2.8.9/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/gnomad2.mo; \
            echo "installing $lang.gmo as $dir/gnomad2.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/gnomad2.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/gnomad2.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/gnomad2.mo.m; \
            echo "installing $lang.gmo.m as $dir/gnomad2.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/gnomad2.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/gnomad2.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing ca.gmo as /usr/local/share/locale/ca/LC_MESSAGES/gnomad2.mo
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/gnomad2.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/gnomad2.mo
installing fi.gmo as /usr/local/share/locale/fi/LC_MESSAGES/gnomad2.mo
installing fr.gmo as /usr/local/share/locale/fr/LC_MESSAGES/gnomad2.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/gnomad2.mo
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/gnomad2.mo
installing no.gmo as /usr/local/share/locale/no/LC_MESSAGES/gnomad2.mo
installing pl.gmo as /usr/local/share/locale/pl/LC_MESSAGES/gnomad2.mo
installing sco.gmo as /usr/local/share/locale/sco/LC_MESSAGES/gnomad2.mo
installing sv.gmo as /usr/local/share/locale/sv/LC_MESSAGES/gnomad2.mo
make[1]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9/po'
make[1]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9'
make[2]: Betrete Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9'
make[2]: Für das Ziel »install-exec-am« ist nichts zu tun.
test -z "/usr/local/share/application-registry" || mkdir -p -- "/usr/local/share/application-registry"
 /usr/bin/install -c -m 644 'gnomad2.applications' '/usr/local/share/application-registry/gnomad2.applications'
test -z "/usr/local/share/applications" || mkdir -p -- "/usr/local/share/applications"
 /usr/bin/install -c -m 644 'gnomad2.desktop' '/usr/local/share/applications/gnomad2.desktop'
test -z "/usr/local/share/pixmaps" || mkdir -p -- "/usr/local/share/pixmaps"
 /usr/bin/install -c -m 644 'gnomad2-logo.png' '/usr/local/share/pixmaps/gnomad2-logo.png'
test -z "/usr/local/man/man1" || mkdir -p -- "/usr/local/man/man1"
mkdir: kann Verzeichnis „/usr/local/man“ nicht anlegen: File exists
make[2]: *** [install-man1] Fehler 1
make[2]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/home/labyrinth/gnomad_install/gnomad2-2.8.9'
make: *** [install-recursive] Fehler 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


```

So it says it can`t create /usr/local/man, although the -p after mkdir should prevent this. At least that`s what mkdir --help says.

After that, there is no gnomad2 in /usr/bin. 

Nevertheless, I enter the extracted src folder and start gnomad2 from there.

```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ ./gnomad2
GTK Accessibility Module initialized
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
flush_handles(): LIBMTP panic: Could not get object handles...
Return code: 0x02fd (look this up in ptp.h for an explanation).
Segmentation fault (core dumped)
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ 

```

Before the app closes by itself, a window "Empfange Titel Metadaten" (receiving title meta data) opens for a short time, which stays blank, though.

The mp3 player enters PC mode during that, and does not leave it anymore when the app crashed.

Now, with the mp3 player still in PC mode (so I guess the app can`t create a new session), I type ./gnomad2 again.

```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ ./gnomad2
GTK Accessibility Module initialized

labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ 

```

During that (before the second prompt appeared after several seconds), the small window appears again - but this time not the normal application window. And no task bar entry either.

Now I`m doing it a third time:

- the small window appears and disappears immediately
- the main window opens
- an alert box says it has found no music player at the usb bus.
- I click close on the box and close the app.

Output this time:

```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ ./gnomad2
GTK Accessibility Module initialized
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Could not get device info!
Connection error.
PDE device NULL.
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ 

```

- Okay, so now I unplug the usb cable, which puts the mp3 player back into normal mode.
- I plug it in again. Nothing happens. (mp3 player stays in normal mode.)
- I run ./gnomad2 again.

--> output stops at:
```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ ./gnomad2
GTK Accessibility Module initialized

```

...and the app main window which opened remains unfinishedly drawn. (Grey background, white where the list boxes + one textbox  are later, but no borders or other controls.)

... Now I do the same again. Plug out, plug in, start gnomad2.

This time the main window gets drawn and the Receiving Title Meta Data small window appears again.

After several seconds the app closes again, giving the following output:

```
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ ./gnomad2
GTK Accessibility Module initialized
Autodetected device "Creative Zen Touch (MTP mode)" (VID=041e,PID=4131) is known.
PTP: Opening session
Connected to MTP device.
flush_handles(): LIBMTP panic: Could not get object handles...
Return code: 0x02fd (look this up in ptp.h for an explanation).
Segmentation fault (core dumped)
labyrinth@edgy:~/gnomad_install/gnomad2-2.8.9/src$ 

```

This is the installation with libmtp from the repos and gnomad2 self compiled.

Before that I had both self compiled (and got errors from both when checkinstall was supposed to install them into the system), and I got various other errors. I got 3 of the 4 libmtp2 extension errors (0x02fd to 0x02ff), but reading around in the libmtp sources didn`t get me any further.

Sometimes the gnomad2 main window kept staying open, and I could select the menu items from the second menu, which resulted in the same errors.

Can you please help me somehow?

Thanks in advance - great work you do here!

Regards,
Labyrinth.

---

### Post by hodad on 2006-11-11
Ive tried many different methods from this forum to get my Zen V working over the last month, all to no avail.  Any help would be greatly appreciated!   [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

I have installed Gnomad2, but when I run it, I get
"no jukebox found on USB Bus!"

A few install observations:

I got the following after entering the "sudo apt-get install build-essential ..." commang line:
               *************
dave@dave-desktop:/$ sudo apt-get install build-essential libnjb-dev libmtp-dev libid3tag0-dev libglib2.0-dev libgtk2.0-dev libxn
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package libmtp-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmtp-dev has no installation candidate
              *************

I searched for the libraries listed in the command line, but only found "libnjb2.2.5.tar.gz", which I moved into "gnomad_install" directory (but did nothing else with it).

I did a search for the other lib files listed in the command, but found nothing anywhere in the file system; seems like none of them were installed (?).

I did find a copy of Libmtp, but it was an .rpm file (which I understand can't be installed by Ubuntu).

A few notes on my system:
1. AMD-64 based machine (about 2 years old).
2. I installed "Edgy" OK; only error message was "Checkinstall" not installed during upgrade.
3. Lots of "subdirectory locked" icons on most of the root directories, but assume that these are still accesible to root when doing upgrade processes.
4. Zen V doesn't show up on my file system under "media" or "mount" subdirs.



My Zen V looks cute, but steadfastly refuses to be seen!

---

### Post by hodad on 2006-11-11
Followup info:

Reading thru the listings, I tried a couple of more things:

1. edited "45-libnjb.rules" with gedit and added a line for ...idProduct 4150 ..., as the Zen V is listed ub=nder Ubuntu's Device Manager as 4150. There was no listing for "Creative Zen V" until I entered it.  No result.
2. I installed "Checkinstall" (though I still don't know what it does), and got the following:
              **********
The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

*** No known documentation files were found. The new package
*** won't include a documentation directory.

Please write a description for the package.
End your description with an empty line or EOF.
>> Daves Checkinstall
>>

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "gnomad_install" contains underscores.
*** Warning: dpkg might not like that so I changed
*** Warning: them to dashes.

This package will be built according to these values:

0 -  Maintainer: [ root@dave-desktop ]
1 -  Summary: [ Daves Checkinstall ]
2 -  Name:    [ gnomad-install ]
3 -  Version: [ 20061111 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ gnomad_install ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

          **********

Maybe this will help clarify the situation.

---

### Post by HellSpawn on 2006-11-16
Worked great on 64 bit 6.10 ;) for my Zen Vison:M 30GB .. Thanks...

---

### Post by Labyrinth on 2006-11-19
In reply to #249 (myself):

Okay, the connection problems were on the side of my mp3 player. I tried with wmp afterwards with the same result. 
Now, after rebuilding the music player`s index, it works with wmp and gnomad2, although with the latter one, the initial connecting reading of the players contents took a very long time.

I don`t know anything new about all those build errors, though.

---

### Post by romana on 2006-11-19
HI, I am running edgy, I have a Creative 30gb Zen Vision:M, and I followed the HowTo on the first page for Edgy. I get the same result from either install fully from source, or whether just compiling gnomad2.

i can see device, i can transfer files FROM device, but it falls over if i try to transfer TO device.

i had it working on dapper xubuntu, but did a clean install for edgy ubuntu (various reasons).

error below:

sudo gnomad2
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen Vision:M

(gnomad2:28151): Gtk-CRITICAL **: gtk_accel_label_new: assertion `string != NULL' failed

(gnomad2:28151): Gtk-CRITICAL **: gtk_misc_set_alignment: assertion `GTK_IS_MISC (misc)' failed

(gnomad2:28151): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_WIDGET (widget)' failed

(gnomad2:28151): Gtk-CRITICAL **: gtk_accel_label_set_accel_widget: assertion `GTK_IS_ACCEL_LABEL (accel_label)' failed
Segmentation fault (core dumped)

---

### Post by ghepardo on 2006-11-22
Help plz, I cant install gnomad with the istruction on this post because whe I try to install gtk2.0-dev apt says that depends to broken packages. SO I installed gnomad through apt, but gnomad can't find my creative zen microphoto. Nor amarok can find it.

I can browse its content with konqueror, because is recognized as an usb camera, but I can't tranfer files from/to it.

Someone can Help?

---

### Post by hodad on 2006-11-23
HELP!

Two months and still trying!!!! 

I have a creative zen v, and have been hoping to get it to work.  Have tried practically everything listed in this thread multiple times, but nothing works (see previous messages).  Don't understand the structure of Ubuntu or Linux well enough to make sense of the myriad error messages I get when trying to load libraries needed to get gnomad2 to work, nor where I should find them one they (say that) they have been installed. Maybe I'm too old to understand Linux, since I learned on DOS.

Main problem is that I get "No jukeboxes found on USB bus", even though System-Device Manager" recognizes it.  Even added the proper device to rules.d, but it still isn't seen. 

  Recently tried to load libraries again on my AMD 64 machine, but with each attempt, I get messages about dependency errors, so I try and load the files listed in the error message, only to be confronted with an ever expanding tree list of other dependencies (apparently over a hundred of them). 

Very frustrating !  Too many unknowns for me to proceed. About to give up and go back to windows, though I like the Ubuntu effort, and would like to stay with it!!   Just want to listen to music, but this is hell!! 

Is there some way to make this device work, or do I have to go back to windows? 

Any help would be greatly appreciated!!!!!

---

### Post by ntetreau on 2006-11-23
Hi Hodad, sorry to hear about all your troubles.  I think your device was added very recently to libmtp, and somehow I get the impresion you may not have added it everything needed in the /etc/udev/rules.d/libmtp.rules file.  I am running cvs libmtp and this is what i have in this file for you device:


# Creative Zen Vision
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="666"

You may want to give this a try.  If this doesn't help, you may want to try running cvs libmtp as well.  If you can compile libmtp already, you won't have any problems with cvs.

To download libmtp from cvs from the terminal:

```
sudo apt-get install cvs
```

```
cvs -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp login

```
Press enter at the password prompt then:

```
cvs -z3 -d:pserver:anonymous@libmtp.cvs.sourceforge.net:/cvsroot/libmtp co -P libmtp
```

This will download everything into the libmtp directory, enter it:

```
./autogen.sh
```

This will create the configure script, you may get errors here.
I had to install libtool, autotool, automake1.9, autoconf and m4 . You can search for them in synaptic.

Once you have succesfully ran autogen, you should compile libmtp normally (I had to install libusb-dev for configure to go through):
```

./configure
make 
sudo make install
sudo bash hotplug.sh
```

I press "n" for the hotplug question.

Then, if I plug in my Zen micro, it is instantly recognized and I get a stupid popup asking if I want to import the photos, even if I press ignore, it asks everytime, but hey, at least I can play with my tunes!

I do not use gnomad as amarok does it for me (look for my answer earlier about compiling amarok using a script).

Hope you get your thingy working.

Nic

---

### Post by msak007 on 2006-11-23
> **Labyrinth said:**
> In reply to #249 (myself):

Okay, the connection problems were on the side of my mp3 player. I tried with wmp afterwards with the same result. 
Now, after rebuilding the music player`s index, it works with wmp and gnomad2, although with the latter one, the initial connecting reading of the players contents took a very long time.

I don`t know anything new about all those build errors, though.

Labyrinth, sorry we did not help you out earlier. Were you finally able to compile Gnomad / limbtp (despite any errors)? If you still need help, please let me know.


> **romana said:**
>      HI, I am running edgy, I have a Creative 30gb Zen Vision:M, and I followed the HowTo on the first page for Edgy. I get the same result from either install fully from source, or whether just compiling gnomad2.

i can see device, i can transfer files FROM device, but it falls over if i try to transfer TO device.

i had it working on dapper xubuntu, but did a clean install for edgy ubuntu (various reasons).

romana - Did you compile Gnomad and libmtp from source, or just Gnomad? Please post exactly what you have done (what you installed and which method you followed) so that we can help you out.

> **ghepardo said:**
>  Help plz, I cant install gnomad with the istruction on this post because whe I try to install gtk2.0-dev apt says that depends to broken packages. SO I installed gnomad through apt, but gnomad can't find my creative zen microphoto. Nor amarok can find it.

I can browse its content with konqueror, because is recognized as an usb camera, but I can't tranfer files from/to it.

Someone can Help?
ghepardo, that is the same device I use and I know it works with Gnomad. You can follow Method 1 (only compiling Gnomad from source) as the version of libmtp in the repos does support your device. Installing Gnomad from the repos won't work because it wasn't compiled with MTP support. Please uninstall / purge Gnomad, and post the error you got when trying to install gtk2.0-dev. Once we can get that resolved, you can compile Gnomad.

> **hodad said:**
>      HELP!

Two months and still trying!!!! 

I have a creative zen v, and have been hoping to get it to work. Have tried practically everything listed in this thread multiple times, but nothing works (see previous messages). Don't understand the structure of Ubuntu or Linux well enough to make sense of the myriad error messages I get when trying to load libraries needed to get gnomad2 to work, nor where I should find them one they (say that) they have been installed. Maybe I'm too old to understand Linux, since I learned on DOS.

Main problem is that I get "No jukeboxes found on USB bus", even though System-Device Manager" recognizes it. Even added the proper device to rules.d, but it still isn't seen. 

 Recently tried to load libraries again on my AMD 64 machine, but with each attempt, I get messages about dependency errors, so I try and load the files listed in the error message, only to be confronted with an ever expanding tree list of other dependencies (apparently over a hundred of them). 

Very frustrating ! Too many unknowns for me to proceed. About to give up and go back to windows, though I like the Ubuntu effort, and would like to stay with it!! Just want to listen to music, but this is hell!! 

Is there some way to make this device work, or do I have to go back to windows? 

Any help would be greatly appreciated!!!!!
hodad, I apologize to you as well for not getting an answer to you sooner. Haven't had as much time to troubleshoot lately. Please don't give up yet as we'll attempt to help you get it going...Anyway the main problem with your device is not supported by the version of libmtp in the repos (0.0.18 ) - it was not officially supported until 0.0.19+. So even if you do install libmtp from the repos and compile Gnomad, libmtp still won't recognize the device. So unfortunately in your case, you do have to compile libmtp from source. This is one of those special device circumstances I mentioned in the instructions. I'll make sure to list your device specifically in the instructions so others can realize that problem from the start. Anyway my advice to you would be to completely uninstall / purge everything you installed so far (gnomad, libmtp, any dev packages, all the packages listed in the instructions) and start over again, using Method 2 from the instructions. I don't have nor have ever installed a 64-bit version of Ubuntu, so I'm not sure if that has anything to do with the errors you get. As usual, if you get any errors after you've uninstalled everything and started over please post them and we'll try to help.

---

### Post by hodad on 2006-11-23
Thanks for your reply!  Will try method 2.  Had thought about trying it, but didn't think it would work, as it's more complicated than method 1 (and I figured that the number of errors would be proportionally greater).  If it doesn't work, I'll send error printouts.

Again, thanks!  - hodad

---

### Post by msak007 on 2006-11-23
> **hodad said:**
> Thanks for your reply!  Will try method 2.  Had thought about trying it, but didn't think it would work, as it's more complicated than method 1 (and I figured that the number of errors would be proportionally greater).  If it doesn't work, I'll send error printouts.

Again, thanks!  - hodad
I know it seems intimidating because of more compiling from source, but it's really not hard at all. It's just a few extra steps (fully outlined) to download libmtp, extract it, and go through the configure / make / checkinstall routine you already went through with Gnomad. Once you do that and re-compile Gnomad with a newer version of libmtp already installed, hopefully that should resolve your issues and you'll be able to use your device.

---

### Post by ghepardo on 2006-11-24
Ok i tryed back and now all works with method 1. But, I have a question: isn't possible to see the folder view of the zen content? I only see a big list of all files, I'd like to see folders.

---

### Post by tubasoldier on 2006-11-24
I followed your guide. My microphoto is working great. 

The only issue is that I cant make or move file folders to the thing. that sucks for when i want to put photos on it in a specific folder.

---

### Post by msak007 on 2006-11-24
ghepardo and tubasoldier: Unfortunately, a current limitation of the software is that it does not support folders or folder view. I believe this only applies to MTP devices, so it may be a limitation in libmtp, not Gnomad. If you use the Data Transfer tab to send files over, you will only see a big list. If you move photos over, they will end up in the photo folder on your device. However, they will not be placed in a specific subfolder and you may have to move them manually. It is nothing you did wrong, just a limitation of the software. It works great otherwise, and I'm glad you guys got your devices working. Hopefully this is something that will eventually be corrected.

---

### Post by hodad on 2006-11-24
I tried method two after "purging" Gnomad2.  Here's what I got:

           ************

dave@dave-desktop:~$ sudo apt-get install build-essential libnjb-dev libmtp-dev libid3tag0-dev libglib2.0-dev libusb-dev libgtk2.0-dev libxml-perl checkinstall
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package libmtp-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmtp-dev has no installation candidate
dave@dave-desktop:~$

           ************

---

### Post by hodad on 2006-11-24
Carried on with Method 2 installation in spite of above error message about missing libmtp-dev.   Finished method 2, and ran Gnomad2 from Apps tab, and got the familiar "No Jukeboxes found on USB Bus".  I checked the file "45-libnjb.rules", and it still had my entry from earlier attempts for the Zen V which I had gotten from "System-Administration-Device Manager".  Note that it is recognized by the Device Manager as: /org/freedesktop/Hal/devices/usb_device_41e_4150_A2904C0F0002FA9D.

Hope this helps...

---

### Post by msak007 on 2006-11-24
> **hodad said:**
> I tried method two after "purging" Gnomad2.  Here's what I got:

           ************

dave@dave-desktop:~$ sudo apt-get install build-essential libnjb-dev libmtp-dev libid3tag0-dev libglib2.0-dev libusb-dev libgtk2.0-dev libxml-perl checkinstall
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
Package libmtp-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmtp-dev has no installation candidate
dave@dave-desktop:~$

           ************
Hmm...I think I messed up because being that you're compiling libmtp from source, you'll get all the libs you need and don't need the dev package. Try it without that package and see how it works. But just so we can figure out why you're getting that error, did you enable all the repos (mulitverse, universe, etc.). I was looking at the libmtp-dev package in adept, and it was packaged by MOTU so it's in universe. [Here's]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libmtp&searchon=names&subword=1&version=edgy&release=all") the Ubuntu Packages entry for libmtp and libmtp-dev in Edgy that confirms it.

---

### Post by hodad on 2006-11-25
Don't know what you mean when you refer to a "repo", or enabling them,  but I assume that you are referring to Synaptic download manager.  I did try using Synaptic, but couldn't find most of the libs referred to in the first line of Method 2. I assume from what you say that I can leave them all out , and simply compile libmtp 0.0.21.   


Not clear on precisely how to proceed, but here's how I interpret what you want me to try.  I can't see how it can work though, since I already compiled libmtp 0.0.21. Please forgive my ignorance; but I'm still abit confused (sorry about that).  Also, could all of the junk I downloaded thru Synaptic cause me any grief (i.e., do I need to do any cleanup first?):

1. Leave everything as-is (not purge anything).
2. Download and compile libmtp 0.0.21 as per Method 2.
3. Leave Gnomad2 as-is.
4. Try running Gnomad2 again

On second thought, I think I'll await further instructions before trying the above.

Once again, thanks for your help and your patience!

---

### Post by msak007 on 2006-11-25
Sorry, "repos" is short for "repositories" - those are the installation sources you see in the file /etc/apt/sources.list. That's what tells Ubuntu where to get the list of software available and what to download. By default, the "universe" and "multiverse" repositories are disabled because they're not officially supported. There are plenty of explanations, but for reference you can look at [this]("http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories") page. The screenshot references Dapper, but the same should apply in Edgy. libmtp-dev is in "universe", so the suggestion I made was to make sure you enabled universe in your sources so it would show up when you want to install it. But, as I mentioned before, that's irrelevant because you won't need the package.

Now as far as to how I suggested you proceed. You initially tried Method 1, which entails installing everything from the repositories. As I said before the version of libmtp in the repositories does not support your device so you have to follow Method 2. But libmtp *has* to be compiled / installed before you compile Gnomad so it can detect it at compile time. If you compile Gnomad without libmtp being present first, it won't detect it and won't work with MTP devices. I want you to try the following:

1. Purge everything you already installed (Gnomad, libmtp, anything you pasted from the instructions, etc.). I already assume you did this because that's what I suggested last time, but if you didn't do it now.
2. Follow Method 2 - install all the prerequisite dependencies I've listed (with the exception of libmtp-dev), then download and compile libmtp, and finally download and compile Gnomad.

I appreciate your patience and not giving up, I know it can be frustrating but hopefully you'll get it working soon.

---

### Post by hodad on 2006-11-25
Thanks for clearing it up for me; will try in morning and let you know what happens.

---

### Post by ntetreau on 2006-11-26
hohad, don't forget to run:

sudo bash hotplug.sh

in the libmtp directory after compile, this will install the libtmp.rules file containing the important info on your device.  Since your device is an MTP device, you shouldn't look in libnjb.rules for it but in libmtp.rules.    Actually, I would remove the part your added to the libnjb.rules file if I was you, you wouldn't want your device to be claimed first as a libnjb device.

Nic

---

### Post by hodad on 2006-11-26
Almost there!!!!!!!!

I followed your instructions (thanks to both of you!) and got it to work momentarily.  After repeating method 2 (w exception of libmtp-dev), I entered gnomad2 in command line of the terminal, and it came up and read the "jukebox" contents.  

I exited, and brought up gnomad2 from "Applications" tab on the desktop, only to get the familiar "No jukeboxes on USB Bus" message.  So I went back to the command line prompt and typed gnomad2 (both as myself, and as root).  I got the "No jukeboxes..." message again, and the command line listing was as follows:

         ******************
dave@dave-desktop:~$ gnomad2
No MTP devices.
PDE device NULL.
dave@dave-desktop:~$ sudo gnomad2
This is not a Microsoft MTP descriptor...
Device response to read device property 0xee:
        0000: ea00 000e e59f f8a0 e59f f8a0 e59f f8a0   ................
        0010: e59f f8a0 e59f f8a0 e59f f8a0 e59f f8a0   ................
        0020: 5631 2e30 726f 6d20 6163 6365 7373 2074   V1.0rom access t
        0030: 696d 6520 6973 2037 306e 7320 0000 0000   ime is 70ns ....
        0040: e59f 0880 e3a0 1000 e580 1000 e3a0 0507   ................
        0050: e3a0 1000 e580 1000 e10f 0000 e3c0 00df   ................
        0060: e380 00d3 e129 f000 e59f 085c e3a0 1000   .....).....\....
        0070: e580 1000 eb00 01f2 e3a0 00c8 eb00 0137   ...............7
        0080: eb00 01ea e59f d868 e28f e001 e12f ff1e   .......h...../..
        0090: f001 f8ca 4778 0000 e3a0 0046 eb00 012f   ....Gx.....F.../
        00a0: eb00 01d2 e28f e001 e12f ff1e f001 fb24   ........./.....$
        00b0: 4778 0000 e350 0001 0a00 0007 e28f e001   Gx...P..........
        00c0: e12f ff1e f002 f9f2 4778 0000 eb00 00fd   ./......Gx......
        00d0: e350 0000 0a00 0000 e3a0 f801 eb00 005a   .P.............Z
        00e0: e10f 1000 e14f 2000 e14f                  .....O ..O
No MTP devices.
PDE device NULL.
dave@dave-desktop:~$

              ******************

Must be pretty close at this point; any ideas? 

Thanks - hodad

---

### Post by hodad on 2006-11-26
OOOPS!!

Couldn't find device because it was temporarily unplugged.  In order to see if it transferred any files, i unplugged the Zen and forgot to plug back in before restarting gnomad.  

Appears to work now!  Now I just have to figure out how to enter songs into the playlists and I can put this thing to work. I'll look up gnomad instructions to figure this out, as it didn't work on first try. 

Also, being new to MP3 world, I have to figure out where and how to actually download music (since all of the sites I've looked at seem not to handle linux), but that'll be another thread I guess.

THanks again for you patience and help; hopefully now I can carry on by myself.

---

### Post by FredSambo on 2006-11-26
i just got my zen micro working!

thanks!

---

### Post by msak007 on 2006-11-26
**hodad**: I'm so glad you finally got it working! Persistence (usually) pays off, and in the process I'm sure you learned a thing or two :). Playlist creation and manipulation is not that hard and you can create and edit playlists right from within Gnomad. If you got the device working I'm sure you can figure that part out ;). As far as "downloading" MP3s, well I won't get into that because you can download music legally but you can also download music illegally. You can also encode CDs you own into MP3s and get music that way. How you proceed after this is up to you. And as far as web site support, I'm sure you meant sites that legally sell you music. I'm not sure how many of them are Linux friendly because legally bought music usually has some sort of DRM. I'm sure someone else is more knowledgeable than me on that front because I don't buy music online (I rip / encode CDs I own). I do know that the newest version of Amarok now has an online store called "MagnaTune" integrated, and from what I've read it's an independent artist-friendly music store distributor that doesn't DRM the hell out of their music - in fact it's DRM free. I haven't had a chance to check out any of the artists, but I'm all for stores and distributors that aren't greedy and actually help and benefit the artists. Check out their [mission]("http://magnatune.com/info/mission") and some of the music, you might like it. Anyway I'll make sure to update my instructions to remove libmtp-dev from Method 2, and also insert the little blurb I forgot about running the hotplug script (thanks  ntetreau!). If you have any more questions or problems, please let us know.

**FredSambo**: Thanks for letting me know it helped!

---

### Post by ButteBlues on 2006-11-26
I'm happy to report that under Feisty's Amarok, with the compiled libmtp, once you transfer the rules and reload the hardware rules, that Amarok is working completely with my Creative Zen V! :)

---

### Post by msak007 on 2006-11-26
> **a simple façade said:**
> I'm happy to report that under Feisty's Amarok, with the compiled libmtp, once you transfer the rules and reload the hardware rules, that Amarok is working completely with my Creative Zen V! :)
That's great news! So you're saying that you had to compile libmtp and transfer the rules, then install Amarok from the repos and it worked? Not sure how that would work - it would seem to me that if Amarok was compiled with libmtp that downloading it would also bring along libmtp from the repos as a dependency. Can you clarify a little more? I would try it but I'm not brave enough to jump to Feisty on my production machine that I just installed Edgy on :).

---

### Post by ButteBlues on 2006-11-26
The version of libtmp from the repos is 0.18. It is not working with Amarok 1.4.4.


However, compiling libmtp 0.21, copying the udev rules over, and then installing (or reinstalling or reconfiguring) amarok will have MPT working. :)

And libmtp and libnjb, etc, are only recommended packages IIRC, so they aren't pulled in as dependencies.

Attached are the Amarok-Xine 1.4.4 deb (you'll have to download the amarok deb on your own - it's ~14MB and can't be attached here) on my laptop (the feisty one, but I don't _think_ it has any non-edgy dependencies) and a screenshot.

---

### Post by msak007 on 2006-11-26
Cool. Looking forward to it, I'll test Feisty on my laptop and see how that fares.

---

### Post by hodad on 2006-11-26
I think I'm not yet out of the woods with my Zen V:

When I start Gnomad2, it scans the Zen, and I see the playlists I created two months ago when I first started it up, along with a couple of audiobooks I managed to download to the zen before it stopped cooperating. After Gnomad scans the Zen, I see the playlists as listed on the zen, but can't do anything with them.    When I look in the "Music Transfer" screen, I see CDROM, CDROM0, and ..   on the right side of the screen, I see some songs I loaded off of a cd.  When I right click on a song, and choose "transfer selected", it asks me what playlist to add to, and it seems to do it, but I don't see it show up on the Zen, even after choosing "export playlist".  I see some message boxes flit by on the screen too fast to read.  Can't seem to get gnomad to do anything but scan the Zen.  Doesn't seem to want to download anything from gnomad to the Zen.

When I start gnomad2 under "terminal", I get:

           **********
  dave@dave-desktop:~$ gnomad2
Autodetected device "Creative Zen V" (VID=041e,PID=4150) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen V

(doesn't return to prompt)

           **********
Is gnomad2 still incomplete somehow?  Maybe one of the libs is not there, or wrong version?
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by ButteBlues on 2006-11-27
hodad - Did you install both the repositoried packages AND build the other packages?

---

### Post by urukrama on 2006-11-28
Thank you, msak007, I got it working and am transferring my audio to my Creative Zen Photo Sleek as I write. :D 

I run Dapper, and compiled everything from source. I did have some difficulties installing libnjb. For those with similar difficulties, here is what happened:

When I installed libnjb, it gave me an error, and this log:

```
(Reading database ... 171077 files and directories currently installed.)
Unpacking libnjb-2.2.5 (from .../libnjb-2.2.5_2.2.5-1_i386.deb) ...
dpkg: error processing /home/USERNAME/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb (--install):
 trying to overwrite `/usr/include/libnjb.h', which is also in package libnjb1-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/USERNAME/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb

```

Previously, I had tried to access my Creative Player through Amarok (not the repos version), KZenexplorer, and Neutrino, but neither of them worked. One of these (or more?) required an other version of libnjb. Once I removed that, all went fine.

---

### Post by hodad on 2006-11-29
Sad to say, but I'm afraid that I don't understand fully what you are suggesting. I am following the instructions by rote, as I don't really know, for the most part, what the commands I am entering are doing. I have a fuzzy understanding on some issues,such as what libraries are for, but don't yet know what is meant by a repository.  Also don't understand where things go in the file structure when they are installed (which is quite frustrating!).  I have a vague notion of what happens when you compile code, but not a very deep understanding, having left that sort of thig behind when I learned computing on punch cards back in the stone age.  I did the first line of Method 2 (sudo apt-get install build-essential...), where I downloaded the libraries (except for libmtp.dev), and did the other steps listed, but didn't think I had to "compile" them (?).

Anyhow, specific steps would be appreciated.  THanks in advance :-)

---

### Post by ButteBlues on 2006-11-30
When you downloaded the tar.gz files and then ran the commands in the terminal to build them, you were compiling them. :)

---

### Post by ntetreau on 2006-12-01
hohad, i suspect you device does not have full support yet in libmtp 0.0.21... you could still try to download and install (compile) the development version (cvs version) of libmtp as per my post about a week ago, or else wait a few more days, libmtp 0.1.0 will be released any day now.

Nic

---

### Post by ntetreau on 2006-12-07
Libmtp 0.1.0 is out, there is quite a bit new in this release I think and the vision M has supposedly much better support.  Everyone having problems might want to give it a try!

Nic

By the way, there are a few devices that are singled out in the README:

> It's Not Our Bug!
-----------------

Some MTP devices have strange pecularities. We try to work around
these whenever we can, sometimes we cannot work around it or we 
cannot test your solution.

* The Zen Vision:M (possibly more Creative Zens) has a firmware bug
  that makes it drop the last two characters off a playlist name.
  It is fixed in later firmware.

* The iRiver devices (possibly all of them) cannot handle the 
  enhanced GetObjectPropList MTP command (0x9805) properly. So 
  they have been banned from using it.

* The Samsung Yepp T9 has several strange characteristics, some
  that we've managed to work around. (For example it will return
  multiple PTP packages in a single transaction.)

* Very few devices that implement GetObjectPropList (0x9805) will
  return the entire object list if you request a list for object
  0xffffffffu. (But they should.) So we're currently not using 
  that feature.


---

### Post by le_vainqueur on 2006-12-07
I'm having problems starting with step 5 of method 1 for edgy.  I'm getting the following message:

> brandon@brandon-desktop:~/gnomad_install$ ./configure
bash: ./configure: No such file or directory
brandon@brandon-desktop:~/gnomad_install$ make
make: *** No targets specified and no makefile found.  Stop.
brandon@brandon-desktop:~/gnomad_install$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "gnomad_install" contains underscores.
*** Warning: dpkg might not like that so I changed
*** Warning: them to dashes.

This package will be built according to these values: 

0 -  Maintainer: [ root@brandon-desktop ]
1 -  Summary: [ sudo /etc/init.d/udev restart ]
2 -  Name:    [ gnomad-install ]
3 -  Version: [ 20061207 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad_install ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

brandon@brandon-desktop:~/gnomad_install$ gnomad2
bash: gnomad2: command not found


---

### Post by ntetreau on 2006-12-07
Hi Brandon,
I don't know how to say this but it looks like you have not entered the gnomad-2.8.9 directory before running the ./configure, make, checkinstall commands.  Try again after "cd gnomad-2.8.9", that might very well be fix your problems!  If that doesn't, perhaps you could print here the content of the directory?

Nic

---

### Post by msak007 on 2006-12-08
Sorry for the late update (don't get much free time except for some weekends), but as ntetreau already mentioned libmtp 0.1.0 is out. Here are the release notes from their SourceForge site:
```
Notes: Much improved 0.1.0 version. Much stabler, faster, leaner, cleaner and extended libmtp. This version has a new library interface, libmtp.so.4.
``` If you are currently having problems with your device and transfers, please upgrade to the newest version. The install instructions have been updated accordingly.

> **le_vainqueur said:**
> I'm having problems starting with step 5 of method 1 for edgy.  I'm getting the following message:
**le_vainqueur**: I apologize, that was a huge omission on my part - I completely forgot the step where you actually go into the folder where the Gnomad source files were extracted in the previous step! As ntetreau mentioned, there's 1 extra step in between:
```
cd gnomad2-2.8.9
```Then you can continue compiling per the instructions. I've modified the install instructions to include that step and it is now Step 5 :). Once again I apologize for that, try again and let us know if you run into any problems.

---

### Post by le_vainqueur on 2006-12-09
Everything worked great.  Thanks a lot!

---

### Post by hodad on 2006-12-09
> **hodad said:**
> Sad to say, but I'm afraid that I don't understand fully what you are suggesting. I am following the instructions by rote, as I don't really know, for the most part, what the commands I am entering are doing. I have a fuzzy understanding on some issues,such as what libraries are for, but don't yet know what is meant by a repository.  Also don't understand where things go in the file structure when they are installed (which is quite frustrating!).  I have a vague notion of what happens when you compile code, but not a very deep understanding, having left that sort of thig behind when I learned computing on punch cards back in the stone age.  I did the first line of Method 2 (sudo apt-get install build-essential...), where I downloaded the libraries (except for libmtp.dev), and did the other steps listed, but didn't think I had to "compile" them (?).

Anyhow, specific steps would be appreciated.  THanks in advance :-)

*********Update 12/9:

I typed Purge gnomad2, and the tried reloading all of the libraries and compiling libmtp 0.1.0 as per method 2 and got the following listing and errors at the end of the process when I tried to run gnomad2:

dave@dave-desktop:~/gnomad_install/libmtp-0.1.0$ ls
aclocal.m4    config.status    doc            libmtp_0.1.0-1_amd64.deb  libmtp.usermap  missing
AUTHORS       config.sub       doc-pak        libmtp.fdi                libtool         README
ChangeLog     configure        examples       libmtp.pc                 ltmain.sh       README.windows.txt
config.guess  configure.ac     hotplug.sh     libmtp.pc.in              m4              src
config.h      COPYING          hotplug.sh.in  libmtp.rules              Makefile        stamp-h1
config.h.in   depcomp          INSTALL        libmtp.sh                 Makefile.am     TODO
config.log    description-pak  install-sh     libmtp.sh.in              Makefile.in
dave@dave-desktop:~/gnomad_install/libmtp-0.1.0$ cd .
dave@dave-desktop:~/gnomad_install/libmtp-0.1.0$ cd ..
dave@dave-desktop:~/gnomad_install$ ls
gnomad2-2.8.9  gnomad2-2.8.9.tar.gz  libmtp-0.1.0  libmtp-0.1.0.tar.gz
dave@dave-desktop:~/gnomad_install$ cd gnomad2-2.8.9
dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... yes
checking for gtk+-2.0 >= 2.6.0... checking for TAG... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking id3tag.h usability... yes
checking id3tag.h presence... yes
checking for id3tag.h... yes
checking for MTP... yes
checking libmtp.h usability... yes
checking libmtp.h presence... yes
checking for libmtp.h... yes
checking for intltool >= 0.35.0... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking malloc.h usability... yes
checking malloc.h presence... yes
checking for malloc.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for chdir... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating doc/Makefile
config.status: creating po/Makefile.in
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

gnomad2 2.8.9
Configuration :
---------------

 Source code location .: .
 C Preprocessor .......: gcc -E
 C Compiler ...........: gcc -g -O2
 C Linker .............: gcc
 GTK+ version .........: 2.8.20
 libgnomeui version....: NOT USED
 libnjb version........: 2.2.4
 libmtp version........: 0.1.0
 id3tag version........: 0.15.0b
 Install path .........: /usr/local

 Now type 'make' to build gnomad2 2.8.9,
 and then 'make install' for installation.

dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$ sudo make
Making all in src
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT id3read.o -MD -MP -MF ".deps/id3read.Tpo" -c -o id3read.o id3 read.c; \
        then mv -f ".deps/id3read.Tpo" ".deps/id3read.Po"; else rm -f ".deps/id3read.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT gnomad2.o -MD -MP -MF ".deps/gnomad2.Tpo" -c -o gnomad2.o gno mad2.c; \
        then mv -f ".deps/gnomad2.Tpo" ".deps/gnomad2.Po"; else rm -f ".deps/gnomad2.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT prefs.o -MD -MP -MF ".deps/prefs.Tpo" -c -o prefs.o prefs.c; \
        then mv -f ".deps/prefs.Tpo" ".deps/prefs.Po"; else rm -f ".deps/prefs.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT filenaming.o -MD -MP -MF ".deps/filenaming.Tpo" -c -o filenam ing.o filenaming.c; \
        then mv -f ".deps/filenaming.Tpo" ".deps/filenaming.Po"; else rm -f ".deps/filenaming.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o juk ebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c: In function ‘jb2hd_thread’:
jukebox.c:1854: warning: assignment makes pointer from integer without a cast
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT util.o -MD -MP -MF ".deps/util.Tpo" -c -o util.o util.c; \
        then mv -f ".deps/util.Tpo" ".deps/util.Po"; else rm -f ".deps/util.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT mp3file.o -MD -MP -MF ".deps/mp3file.Tpo" -c -o mp3file.o mp3 file.c; \
        then mv -f ".deps/mp3file.Tpo" ".deps/mp3file.Po"; else rm -f ".deps/mp3file.Tpo"; exit 1; fi
mp3file.c: In function ‘mp3file_get_info’:
mp3file.c:387: warning: assignment makes pointer from integer without a cast
mp3file.c: In function ‘get_track_time’:
mp3file.c:931: warning: initialization makes pointer from integer without a cast
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT editmeta.o -MD -MP -MF ".deps/editmeta.Tpo" -c -o editmeta.o editmeta.c; \
        then mv -f ".deps/editmeta.Tpo" ".deps/editmeta.Po"; else rm -f ".deps/editmeta.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT filesystem.o -MD -MP -MF ".deps/filesystem.Tpo" -c -o filesys tem.o filesystem.c; \
        then mv -f ".deps/filesystem.Tpo" ".deps/filesystem.Po"; else rm -f ".deps/filesystem.Tpo"; exit 1; fi
filesystem.c: In function ‘test_writeable’:
filesystem.c:899: warning: cast to pointer from integer of different size
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT playlists.o -MD -MP -MF ".deps/playlists.Tpo" -c -o playlists .o playlists.c; \
        then mv -f ".deps/playlists.Tpo" ".deps/playlists.Po"; else rm -f ".deps/playlists.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT xfer.o -MD -MP -MF ".deps/xfer.Tpo" -c -o xfer.o xfer.c; \
        then mv -f ".deps/xfer.Tpo" ".deps/xfer.Po"; else rm -f ".deps/xfer.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT data.o -MD -MP -MF ".deps/data.Tpo" -c -o data.o data.c; \
        then mv -f ".deps/data.Tpo" ".deps/data.Po"; else rm -f ".deps/data.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT player.o -MD -MP -MF ".deps/player.Tpo" -c -o player.o player .c; \
        then mv -f ".deps/player.Tpo" ".deps/player.Po"; else rm -f ".deps/player.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT metadata.o -MD -MP -MF ".deps/metadata.Tpo" -c -o metadata.o metadata.c; \
        then mv -f ".deps/metadata.Tpo" ".deps/metadata.Po"; else rm -f ".deps/metadata.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT wmaread.o -MD -MP -MF ".deps/wmaread.Tpo" -c -o wmaread.o wma read.c; \
        then mv -f ".deps/wmaread.Tpo" ".deps/wmaread.Po"; else rm -f ".deps/wmaread.Tpo"; exit 1; fi
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.9\" -DPACKAGE_STRING=\"g nomad2\ 2.8.9\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" - DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.9\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB _H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_ H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_ CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAV E_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDI R=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk- 2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/local/include -DPREFIX=\ "/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMA PSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT wavfile.o -MD -MP -MF ".deps/wavfile.Tpo" -c -o wavfile.o wav file.c; \
        then mv -f ".deps/wavfile.Tpo" ".deps/wavfile.Po"; else rm -f ".deps/wavfile.Tpo"; exit 1; fi
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesys tem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk -x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/local/lib -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/dave/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the u se of `tmpnam' is dangerous, better use `mkstemp'
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
Making all in doc
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/doc'
Making all in po
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/po'
file=`echo ca | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ca.po
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file de.po
file=`echo es | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo fi | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file fi.po
file=`echo fr | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file fr.po
file=`echo it | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo nl | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file nl.po
file=`echo no | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file no.po
file=`echo pl | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file pl.po
file=`echo sco | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file sco.po
file=`echo sv | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file sv.po
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/po'
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9'
LC_ALL=C ./intltool-merge -d -u -c ./po/.intltool-merge-cache ./po gnomad2.desktop.in gnomad2.desktop
Generating and caching the translation database
Merging translations into gnomad2.desktop.
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9'
dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$ make install
Making install in src
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make[2]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gnomad2' '/usr/local/bin/gnomad2'
/usr/bin/install: cannot create regular file `/usr/local/bin/gnomad2': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1
dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$

*********

Any ideas on how to proceed?  THanks

---

### Post by msak007 on 2006-12-09
> **hodad said:**
> *********Update 12/9:

I typed Purge gnomad2, and the tried reloading all of the libraries and compiling libmtp 0.1.0 as per method 2 and got the following listing and errors at the end of the process when I tried to run gnomad2:
....
dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$ **make install**
Making install in src
make[1]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make[2]: Entering directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /usr/bin/install -c 'gnomad2' '/usr/local/bin/gnomad2'
/usr/bin/install: cannot create regular file `/usr/local/bin/gnomad2': **Permission denied**
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/dave/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1
dave@dave-desktop:~/gnomad_install/gnomad2-2.8.9$

*********

Any ideas on how to proceed?  THanks

You're close :). The key is that you forgot "sudo" before make install, and got a permission denied error when it tried creating the appropriate files / directories (I've bolded the relevant output above). Try again with sudo, and see if that does anything for you.

EDIT: I still recommend using checkinstall instead of make install when possible. It makes it so much easier to uninstall when you need to in the future to reinstall or upgrade to a newer version.

---

### Post by hodad on 2006-12-10
I continued from ./configure in gnomad2-2.8.9.

Didn't work, got the following:

dave@dave-desktop:~$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                [ ok ]
dave@dave-desktop:~$ gnomad2
gnomad2: error while loading shared libraries: libmtp.so.4: cannot open shared object file: No such file or directory
dave@dave-desktop:~$

I think I should try to wipe out everything and try again.

Perhaps you can tell me how to go about purging everything that I've done, and I could try the "scripted " install (method two) that you recently updated(?). THis way, hopefully, I can "start clean".

 Please note that I literally do what you say, because I don't fully comprehend how all of the commands work, and don't have as much time as I'd like to research all of them.  Hope I'm not being too much of a pain !

---

### Post by ButteBlues on 2006-12-10
I'll be updating my script shortly and posting a thread for it.

---

### Post by hodad on 2006-12-10
Thanks - I'll be looking for it!

---

### Post by msak007 on 2006-12-10
> **hodad said:**
> I continued from ./configure in gnomad2-2.8.9.

Didn't work, got the following:

dave@dave-desktop:~$ sudo /etc/init.d/udev restart
 * Loading additional hardware drivers...                                [ ok ]
dave@dave-desktop:~$ gnomad2
gnomad2: error while loading shared libraries: libmtp.so.4: cannot open shared object file: No such file or directory
dave@dave-desktop:~$

I think I should try to wipe out everything and try again.

Perhaps you can tell me how to go about purging everything that I've done, and I could try the "scripted " install (method two) that you recently updated(?). THis way, hopefully, I can "start clean".

 Please note that I literally do what you say, because I don't fully comprehend how all of the commands work, and don't have as much time as I'd like to research all of them.  Hope I'm not being too much of a pain !
You most likely did not compile libmtp with the "--prefix=/usr" flag. The file it's looking for must be in /usr/lib/, and if you don't compile libmtp with that flag it won't end up there. You could alternatively create a symlink to it, but the easiest method is just to tell it where to put the file when compiling. I ran into the same error when I recompiled libmtp 0.1.0 because I forgot that step, and doing what I just recommended resolved the issue. Your last output (when you had all the errors compiling Gnomad) did not show anything during the compile stage of libmtp, so it's hard to say if you did or didn't. One way we can find out for sure is if you post the output of the following:
```
ls /usr/lib/libmtp.so.*
```As far as for purging everything, if you installed the software using the checkinstall method then you can easily uninstall / purge it using Synaptic because it was installed as a deb package. Just search for libmtp / Gnomad using Synaptic and choose to uninstall them (I believe there's a purge option in there as well if you right-click). Regarding the scripted install, I have not updated that section in a long time (and am even thinking of removing it completely). ParanoidDK is the one who initially created and hosted the script, but I have not heard from him in forever. If a simple façade creates a script and hosts the files, I will be more than happy to update the instructions to include his script to make it easier for everyone to install.

And finally, you are not being a pain :). At least you are trying and have been persistent, and not simply saying "This sucks it's not working I quit" without giving us any relevant output or errors. As long as you keep trying, we'll keep trying to help you. The commands we're telling you to type aren't that hard to understand really once you do have the time to read up on what they do. I'm a noob myself and only started using Linux in the past year after years of (ab)using Windows (or is it the other way around? :-P). It's a challenge, but it's fun nonetheless to learn all over again. You'll get there eventually.

EDIT: I looked at the instructions again and somehow the --prefix=/usr part was missing from the compile instructions (which is why you probably missed it). I've updated it accordingly - sorry again!

---

### Post by klep on 2006-12-10
hello everyone. 

i have followed this guide and have hit a problem. I am running edgy and followed method one. I followed every instruction without hitch. However there is no link in my menu for gnomad, and when i run gnomad2 from terminal i get this:

root@thomas-ubuntu:/home/thomas/gnomad_install/gnomad2-2.8.9# gnomad2

(gnomad2:9254): Gtk-WARNING **: cannot open display:  




any idea how to fix it? thanks


EDIT: turns out it will throw that error if I run it as root, but not as a normal user. Anyone any idea why (to satisfy my curiosity rather than because i really want to run it as root :) )

---

### Post by c0rd3l1a on 2006-12-10
I have a Creative Zen Vision: M and followed the Dapper Method 1 instructions. Everything went really well. My Zen is synced. However, I can only transfer tracks and not the folders that they are in. Because all of my music is organized in A-Z folders, then subfolders with artist names, sometimes album subfolders, this is a problem for me. Is there anything that I can do to fix this?

Also, I can only run the program if terminal is open. If I close terminal, gnomad2 also quits.

Some possibly related issues:

When I start Gnomad2, I get these messages in terminal: "WARNING: LIBMTP_Get_Tracklisting () is deprecated. WARNING: please update your code to use LIBMTP_Get_Tracklisting_With_Callback (). WARNING: LIBMTP_Get_Filelisting is deprecated. WARNING: please update your code to use LIBMTP_Get_Filelisting_With_Callback ()."

When I did the sudo sh hotplug.sh steps, I got the following messages: "You may need additional setup to get correct permissions on your device. See the INSTALL file for information." Reading the install files did not enlighten me.

---

### Post by hodad on 2006-12-11
MSAK007-
Thanks again for your help.  I'll purge everything tonight and go thru the steps you suggest (got to return to my day job now!)

---

### Post by ntetreau on 2006-12-11
c0rd3l1a, folder options have just been added to libmtp before the 0.1.0 release. You may want to take a look at the mtp-newfolder and mtp-folders commands.  There isn't much documentation on these yet but you may have some chance just trying them.  Also, you may want to take a look at libmtp mailing list on their sourceforge page, there seems to be some questions related to yours.  Good luck,

Nic

---

### Post by msak007 on 2006-12-11
> **klep said:**
> hello everyone. 

i have followed this guide and have hit a problem. I am running edgy and followed method one. I followed every instruction without hitch. However there is no link in my menu for gnomad, and when i run gnomad2 from terminal i get this:

root@thomas-ubuntu:/home/thomas/gnomad_install/gnomad2-2.8.9# gnomad2

(gnomad2:9254): Gtk-WARNING **: cannot open display:  




any idea how to fix it? thanks


EDIT: turns out it will throw that error if I run it as root, but not as a normal user. Anyone any idea why (to satisfy my curiosity rather than because i really want to run it as root :) )
**klep**: If I'm not mistaken, the warning you're getting is due to running an X app as root. Most Ubuntu users don't go out of their way to enable the root account as it is disabled by default. I'm sure you may have your reasons for doing so, but my advice (which you seem to have already done) is to run Gnomad as yourself and use sudo to run apps as "root".

As far as the menu entry, it's funny you mention that because I was just working on updating the instructions to add the menu entry :). Do the following from the Gnomad install directory where you compiled from:

1. Copy the menu entry and corresponding icon to their respective locations:
```
sudo cp gnomad2.desktop /usr/share/applications
sudo cp gnomad2-logo.png /usr/share/pixmaps
```2. Then reload your menu and the entry should be there:

- If you're a Gnome user:
```
sudo killall gnome-panel
```- If you're a KDE user:
```
kbuildsycoca --incremental
```Let me know if that works for you (it works in KDE but I can't test Gnome) and I'll update the instructions accordingly.

**c0rd3l1a**: Unfortunately for the time being, folders support is a known limitation with Gnomad + MTP devices. I wasn't aware that folders were implemented with libmtp 0.1.0 as ntetreau pointed, but I did find the commands in /usr/bin/ (there are numerous MTP commands in that folder). If this was recently implemented with libmtp 0.1.0, then you can bet that a new version of Gnomad will follow soon with those commands / features implemented in the GUI. Also, that prompt you got after running the hotplug command is normal - it's just a warning that your system *may* require additional setup. No additional steps other than the ones I've outlined are required though so you should be all set.

**hodad**: No problem, try it and let us know how it works. Hopefully you have better results this time. I know how much day jobs suck - they get in the way of doing things you really want :).

---

### Post by thunderduck3141 on 2006-12-13
My Zen. which works thanks to your wonderful guide, is afu
i had it as a 4 gig storage device for a while (yeah, u can format within it) and now the partitioning is messed up, is there anyway i can just wipe it clean and start anew

---

### Post by ntetreau on 2006-12-14
Hi Thunderduck3141,
look for a command called something like mtp-format (it should be in your path) and give it a go, a read some wonderful thing about this... well that it actually does what it is supposed to, format!  Let everyone know how it went.

Nic

---

### Post by web250 on 2006-12-15
I'm getting this error, in edgy, using method 1:
```
make[1]: Entering directory `/home/web250/Desktop/Install Files/gnomad_install/gnomad2-2.8.9/po'
/home/web250/Desktop/Install Files/gnomad_install/gnomad2-2.8.9/install-sh -d /usr/local/share/locale
make[1]: /home/web250/Desktop/Install: Command not found
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/web250/Desktop/Install Files/gnomad_install/gnomad2-2.8.9/po'
make: *** [install-recursive] Error 1

```

---

### Post by web250 on 2006-12-15
Hmmm...I apt-get installed the repo version, but it shows up as 2.8.9...and it works! Cool.

---

### Post by hodad on 2006-12-17
MSAK007
I was out of town this week, just getting  back to it...

Progress?!
I did everything as you suggested.  Brought up Gnomad2 from Application drop down, and it scanned my "jukebox" (which I assume is the Zen V).  It listed the "playlists" I luckily managed somehow to create the day I bought the device two months ago (how I managed to create them then, I do not remember).  However, I cannot seem to access these playlists, no matter what I try in Gnomad.

Here are a few things I've tried:
I converted (ripped?) a few tracks from a CD in .ogg format (maybe that's a problem?). Tried to add these to one of the 4 playlists I created thru the Music Transfer tab using "add selected to playlist".  Got a progress bar, so it looked like it worked, however, nothing shows up on the Zen.
A couple other observations:  
1. When i choose "rescan contents" under "Jukebox Library" tab, the "Jukebox Library"  
window blanks out (all files previously listed disappear).
2. Playlists also disappear, and when I try to recreate one, I get error message "could not create playlist".  (maybe I'm having a permissions problem?)
3. Hit "Jukebox Information" under "Jukebox Library" tab, and it kicks me out of gnomad2 and into my desktop.
4. When I restart Gnomad2 again, it rescans the device (which is cabled to the usb port), and reads the playlists I originally created in the Zen 2 months ago (they're still there; permanently it seems).

While awaiting your response, I'll try to find an MP3 music file instead of the .ogg files created when I scanned my music cd.  Seems like I tried before, but the software I was using didn't give me MP3 as a choice (probably a licensing problem?).  Seems like somethings still not right with gnomad, however.

Thanks again - Hodad

*********************************

Found a "test mp3" file, and was able to transfer it to the device!!!   It actually worked!!! 

Now I get to handle my next hurdle: discovering how to actually buy an mp3 music file, and then downloading it to my pc so I can transfer it to the Zen and play it (what a concept!).   I'm shooting for under one month for me to figure out how to accomplish this!!!  My ultimate goal: actually listening to music on my Zen V!

THanks for hanging in there and being so patient with me!  Still have problems with playlists, as well as the errors mentioned above, but I at least got something to work with your help.  Again, Thanks!

---

### Post by cutlerite on 2006-12-17
My install went fine  (to my noobie knowledge)

however I can't access my zen micro, even though the zen says it's "docked."


here's what shows up in the terminal:


Autodetected device "Creative Zen Micro (MTP mode)" (VID=041e,PID=4130) is known.
PTP: Opening session
Could not open session! (Return code 765)
  Try to reset the device.
Could not get device info!
Connection error.
PDE device NULL.
PDE device NULL.
Autodetected device "Creative Zen Micro (MTP mode)" (VID=041e,PID=4130) is known.
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
Could not get device info!
Connection error.
Segmentation fault (core dumped)

---

### Post by msak007 on 2006-12-17
Well it seems that you made some progress, at least you're able to start the app and scan your player now. Regarding your problem with OGG files, unfortunately I don't believe your player supports them. This is from the [Zen V specs page]("http://ca.creative.com/products/products.asp?category=213&subcategory=214&product=15283&nav=technicalSpecifications") on Creative's web site:
> **Audio Playback Format:** MP3, WMA, WAV and Audible
So your best bet might be to find an MP3 or to rip and encode some songs into MP3 to try it out. Regarding the playlists you can't get rid of and other issues you're having, some people have reported erratic behavior if their device was previously used in Windows. You may want to just reformat the device and start anew. I couldn't find anything in any of the manuals on how to format the device, but I did find [this]("http://forums.creative.com/creativelabs/board/message?board.id=dap&message.id=168928") page in Creative's forums. Some of the site admins posted instructions on how to format all of the devices. The Zen V is at the very bottom of the page. Try the second option (**Format (All)**) and make sure you don't format the OS / firmware as that'll ruin your device. Try it and let us know how it works, hopefully that resolves your issues

---

### Post by gerscht on 2006-12-18
Thanks for the great tut,
Works like a beauty with edgy and Zen micro! :D

---

### Post by hodad on 2006-12-19
MSAK007,
Many thanks!  I have finally gotten music onto the ZenV and it sounds great!  Still having trouble with Frostwire firewall (have a question posted;awaiting response), but at least I can access MP3's now in time for xmas.  

Once again - THANKS!

---

### Post by msak007 on 2006-12-19
You finally got it working! That's great news...persistence pays off :). I'm sure you learned a thing or two along the way as well so it's not a total waste of time hehe.  Did you end up formatting the player using those instructions? Anyway I answered your question about the Frostwire issue, check the thread.

---

### Post by hodad on 2006-12-19
Yes, I reset the player using a paper clip gently inserted into the tiny reset hole.  Perhaps that helped; often times when I have this much trouble, there are multiple causes making troubleshooting hard.  See you in the other thread!

---

### Post by koholint1000 on 2006-12-20
> **koholint1000 said:**
> Every time i try the manual compilation, i get an error during installing libnjb, aslong the lines of "installing debain package -- failed". I don't know why this is, but it results in me not being able to install gnomad2 (it says it wont bcoz libnjb isnt installed).
:-k 
Also, when i install the scripted instructions, it uns, installs, but wont actually run gnomad2 bcoz it grumbles on about libmtp not being installed properly.
Plz help; i REALLY don't want to have to boot into windows just to put a track or 2 onto my mp3 player.
:confused: 
(its a micro-photo)(and im on ubuntu)
](*,)

(PS, when it finally does start working, I don't hae to boot up the PC with the player connected do i?)

I got it working!!! :-D 

Fore some strange reason, when I tried to compile libnjb with the flags --prefix=/usr and --enable-hotplugging, the deb file wouldn't install. When I configured it without any flags, it worked, installed, and I am happily transferring music.

:D

---

### Post by tafsen on 2006-12-20
Why isn't this guide in the wiki? :)
It worked fine for me :) No troubles at all with My Zen Sleek

---

### Post by KB3KVQ on 2006-12-20
Awsome how to, it took me a few tries but it was most likely operator error.

tnx 73

---

### Post by msak007 on 2006-12-20
**koholint1000** - I apologize to you as I completely skipped over your post I didn't see it. I'm not sure what happened, I may have seen it and said I'd come back to it later and just got sidetracked and your post got buried in earlier pages. Regardless of the reason I apologize for not providing any assistance earlier, looks like you didn't need any help anyway :). Having to compile libnjb, I assume you're on Dapper? It's very odd that compiling libnjb with the --prefix=/usr flag caused errors when installing. This is usually due to one package overwriting the files in another package and causing a conflict, and uninstalling the currently installed one usually resolves it. Either way I'm glad you finally got it working.

**tafsen** - I've never created a wiki and never really thought about moving this how-to there. I guess that would make sense and make it more accessible to people rather than searching through the forums. I'll look into it. Thanks for letting me know you found it useful.
[B]
KB3KVQ[/B] - Thanks as well for letting me know it helped you, glad I could be of help.

---

### Post by koholint1000 on 2006-12-21
No probs msak007! I am on Dapper, yes. I realised by reading the other posts in the thread that my problem was somewhat "special", in the sense that I couldnt find anyone else with that problem. Curious how it conflicted. Might it be to do with the fact that I have another version of libnjb as you suggested!? No matter. I also got it working with just the switch --enable-hotplugging .

How come sometimes it'll just not send a track? I tried to send the track "Cave" 9from the Links Awakening DX Album; and it just wouldn't have it. It completely fugged up the entire mtp. I had to restart the PC before it would connect again. It even prevented the command mtp-detect from accessing the microphoto. Any ideas Batman?

---

### Post by _atle_ on 2006-12-22
Thank you, finally my zen vision m is usable under ubuntu, 1 step closer to a MS free life. :cool: 

Atle.

---

### Post by Cigar Jack on 2006-12-23
This I thought might be helpful so I'm posting it here.  I was a bit annoyed of being unable to create folders with gnomad2 so i did some digging and found it was fairly easy to do from the command line.

Open a Termindal Window and type **mtp-folders**
This will give you the PIDs so you can create sub folders in the existing folders.

Then run  mtp-newfolder newfoldername PID  to create the folder.

Ugh.. Nevermind... Gnomad2 can't even see already created folders.

---

### Post by msak007 on 2006-12-23
> **koholint1000 said:**
> No probs msak007! I am on Dapper, yes. I realised by reading the other posts in the thread that my problem was somewhat "special", in the sense that I couldnt find anyone else with that problem. Curious how it conflicted. Might it be to do with the fact that I have another version of libnjb as you suggested!? No matter. I also got it working with just the switch --enable-hotplugging .

How come sometimes it'll just not send a track? I tried to send the track "Cave" 9from the Links Awakening DX Album; and it just wouldn't have it. It completely fugged up the entire mtp. I had to restart the PC before it would connect again. It even prevented the command mtp-detect from accessing the microphoto. Any ideas Batman?
Yes if you installed the repo version of libnjb then it will conflict with the files you're trying to install, and it'll error out. Best results can be achieved by removing conflicting packages.

Regarding the issue of you not being able to send a track, some devices still have some bugs and quirks so you may run into issues from time to time. It could also be due to you running and older version of libnjb in the location expected (due to the conflicts already mentioned). Try uninstalling any version of libnjb you have installed and follow the instructions again (recompile libnjb and Gnomad). Also, I don't believe you have to restart the entire machine for it to see the device again. Simply do the following and see if you can use the device again:

1. Close Gnomad (if running) and unplug the device
2. Restart udev
```
sudo /etc/init.d/udev restart
```3. Plug the device back in and start Gnomad backup (or test using mtp-connect).

**Cigar Jack** - Thanks for the tip. There are several new mtp commands that haven't been implemented in Gnomad yet and are not really documented anywhere. I believe the next version of Gnomad (whenever that is) will implement those in the GUI. 

On another note, I've read that the Amarok included in Feisty will be built with MTP support. No idea about Gnomad though. So for those that use Amarok as their music player (as I do), this how-to may become obsolete with the release of Feisty.

---

### Post by zazen666 on 2006-12-24
Hi all, 
I just put Edgy on my computer yesterday and have been trying to get my 60 gig creative zen vision m up and running.
I have followed the above instructions, but as I am very new at all this I thnkin I am making mistakes.
Attempting to start over with removing gnomad2 (as per this posts instructions) I get the following warnings...


Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be automatically REMOVED:
gnomad2{p}
The following packages will be REMOVED:
gnomad2{p}
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 668kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 98542 files and directories currently installed.)
Removing gnomad2 ...
dpkg - warning: while removing gnomad2, directory `/usr/local/share/applications' not empty so not removed.
dpkg - warning: while removing gnomad2, directory `/usr/local/share' not empty so not removed.
dpkg - warning: while removing gnomad2, directory `/usr/local' not empty so not removed.


My question/ issues is the above warnings-what do i need to do and can I proceed despite the warnings?


Next I did a purge of libmpt so that I could start from scratch.
Do I also need to do a purge of Libnjb?

Can anyone offer advice?
Thanks so much-I really need a handholding to get thru this...

---

### Post by msak007 on 2006-12-25
**zazen666** - Welcome to Ubuntu and the forums! The errors that you got are sometimes normal during uninstalling / purging applications. As part of a normal uninstallation, the directory that the software resides in is also removed with it. In this case, you're simply given a warning that the operation couldn't be completed because other files are still in that folder so it can't be deleted. User installed / compiled applications will usually reside in /usr/local/, so another app you installed is probably still in that folder. It should have no bearing on your attempts to compile or install Gnomad.

Regarding your other question, purging Gnomad and libmtp should suffice. The version of libnjb in the Edgy repositories is already at the newest version so there is no need to compile it from source or reinstall it. If you have any other questions or need help please let us know.

---

### Post by zazen666 on 2006-12-25
Thank you so much for your reply! I am so glad to have some help with the process. Like I said, I really like ubuntu so far and wanna learn more about it while getting my ZEN going, but I need some handholding at this point. Could you make comments on the below?

So here is where I am at this point...
First I remove gnomad2 and LIBMTP and here is the rest:

~$ sudo aptitude purge gnomad2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

:~$ sudo aptitude purge libmtp - 0.1.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Badly formed pattern 
Couldn't find package "0.1.0".  However, the following
packages contain "0.1.0" in their name:
  libjack0.100.0-0 libccc-0.1-0-dbg libjack0.100.0-dev libccc-0.1-0 
  liblo10k1-0 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Does this seem ok so far?

Next I will follow your instructions for edgy, method 2, correct?

---

### Post by msak007 on 2006-12-25
No problem, that's what the forums are for. We've all needed help (and still do!) and I myself am still a Linux noob even after 1 year :).

Anyway it looks like Gnomad was purged successfully as it couldn't find it, but when you tried to purge libmtp you put spaces in the name. Linux is very sensitive when it comes to file names and paths - everything is case sensitive (so Libmtp is different than libmtp) and spaces are parsed as special characters. Anything with a space has to have an escape character (a \ before the next word) or be enclosed in quotes. So for example if you had a folder named "Gnomad Install", simply typing "cd Gnomad Install" would error out. You would have to type "cd Gnomad\ Install" or enclose the whole name in quotes, "cd "Gnomad Install"".

Ok sorry for going off on a tangent but I wanted to explain to you why it couldn't find the package named "0.1.0" - when you put that on the end of libmtp without quotes or an escape character, it treated it as a separate package because you put a space between them. Here's a hint - package names will never (and shouldn't) have spaces in them - words / version #s are usually separated by a dash or a period. My advice to you would be to start Synpatic (the program you use to install and uninstall software), and search for Gnomad and libmtp that way. If / when you find the package you're looking for right-clicking on it will give you the option to purge. Sometimes if you're not sure of the package name or really want to make sure it is / isn't there, the GUI interface can make things much easier.

EDIT: Yes, you will follow Method 2 for Edgy. Compiling libmtp from source will give you the best results as it is the newest version.

---

### Post by cptjaben on 2006-12-25
Thanks for the info, this works for my Zen vision: m. Thanks again

---

### Post by zazen666 on 2006-12-25
Thank you very much for the explanation above. That is the kind of help that will let me learn something from my mistakes.

Using synaptic, I was able to remove libmpt.

---

### Post by zazen666 on 2006-12-25
I got it!!
I went ahead a tried it out and its working now( or at least gnomad is finally reconizing it!!)
Thank you very very much for your time post this in the first place and also helping with my individual questions.
cheers

---

### Post by ubunter1 on 2006-12-28
i get this message after trying to install the program from your tutorial.

(Reading database ... 119258 files and directories currently installed.)
Unpacking libnjb (from .../libnjb_2.2.5-1_i386.deb) ...
dpkg: error processing /home/robert/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libnjb.so.5.1.0', which is also in package libnjb5
Errors were encountered while processing:
 /home/robert/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb
/
i noticed that when i plug in my vision m that it charges but doesnt recognize the player through gnomad.
any ideas?,thanks for your help.rob.

---

### Post by Stevoinga on 2006-12-28
Ok....on a fresh load of Dapper, then with all the updates loaded:

I followed all the steps as listed on page 1, but with no success.
So then I read all 30+ pages of the thread.

Loaded libnjb-2.2.4 from the repository.

THEN .....

It worked.

Thanks so much for this thread.......very much a lifesaver.

Cheers

---

### Post by Indref on 2006-12-29
Hullo fellow Ubuntuists.

I'm trying to get my Nomad Creative Zen to chat with my Ubuntu laptop, Dapper Drake.

I followed the thread to the letter, excellent instructions, by the way. I got everything installed, even though I don't fully comprehend what I did. I got the GUI up, simple but nicer than the crap you get on the CD with the player.

Anyhoo, it seems I'm not getting any actual transfer. I tried to first copy a song from player to laptop, and it just hung. This is copied from the console:

```
indref@sefton:~/gnomad_install/gnomad2-2.8.9$ gnomad2
No MTP devices.
This is a PDE device
LIBNJB Panic: tried to access protected track!
LIBNJB panic: chunk_size > remain, going to get whole chunk and see what happens
```

I tried to close the program but got the alert "Cannot close, jukebox is busy!"

Help? :-D

---

### Post by msak007 on 2006-12-29
> **ubunter1 said:**
> i get this message after trying to install the program from your tutorial.

(Reading database ... 119258 files and directories currently installed.)
Unpacking libnjb (from .../libnjb_2.2.5-1_i386.deb) ...
dpkg: error processing /home/robert/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb (--install):
**  trying to overwrite `/usr/lib/libnjb.so.5.1.0', which is also in package libnjb5**
Errors were encountered while processing:
 /home/robert/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb
/
i noticed that when i plug in my vision m that it charges but doesnt recognize the player through gnomad.
any ideas?,thanks for your help.rob.
Rob - you're getting an error because you already have libnjb installed from the repositories, and the package you're trying to install wants to overwrite a protected file that was placed there by libnjb. I've bolded the relevant line from your output above. First you need to uninstall libnjb5, then you can try reinstalling libnjb by compiling it:

1. First uninstall libnjb5
```
sudo aptitude purge libnjb5
```2. Then go back to the directory you extracted libnjb to and were compling in. You don't need to do the ./configure / make steps again, just the last part where you do checkinstall or make install:
```
sudo checkinstall
```Then just follow the instructions from where you left off. If you have any other issues, let us know.

> **Stevoinga said:**
> Ok....on a fresh load of Dapper, then with all the updates loaded:

I followed all the steps as listed on page 1, but with no success.
So then I read all 30+ pages of the thread.

Loaded libnjb-2.2.4 from the repository.

THEN .....

It worked.

Thanks so much for this thread.......very much a lifesaver.

Cheers
**Stevoinga** - Can you tell me what problem you ran into when following the steps (if you remember)? If you're compiling libnjb, you shouldn't need to install it from the repositories. It's not a big deal if you got it working, I'd just like to know what issues you ran into.

**Indref** - I've never seen that specific output, but I do have a couple of questions:

1. When you say you have a Creative Zen, is that the original Zen or one of the Zen derivatives (Micro, MicroPhoto, V, Vision, etc.)?

2. Once you know what Zen you have, see if you can find out what version of the firmware you have on there. The Gnomad output is pretty much saying that you don't have an MTP device, so it would've most likely been detected by the version of Gnomad in the repositories simply by installing libnjb. A lot of the older Zen's can be upgraded to MTP devices by doing a firmware upgrade, so if you've had it for a while chances are you got it before the implementation of MTP and are still using a non-MTP firmware.

3. Are you trying to transfer a protected track? I'm not sure what to make of that last 2 lines of the output, but I can only assume it's trying to transfer a digitally protected track (I could be wrong). I don't know much about how Gnomad or libnjb deal with DRM-ed tracks as I don't buy music online. If possible, see if you can find an unprotected track or rip an MP3 from a CD you have, and then try to transfer it and see what happens.

One other note, libmtp 0.1.1 was just released. I'm not sure what changed as the release notes this time are blank, but I can only assume that they've updated libmtp.rules with newer devices. I've updated the instructions but as usual, but unless you are having major problems and want to try a newer version there is really nothing to warrant an upgrade.

---

### Post by Indref on 2006-12-30
Indref - I've never seen that specific output, but I do have a couple of questions:

1. On the player it says "NOMAD JUKEBOX Zen", the model number is DAP-HD0007. It holds 20GB. 

2. I have next to no idea about the firmware. It says version 1.11.01 on the players GUI. I got the player on eBay and I haven't touched the firmware myself.

3. I was trying to transfer a song from the player back to the laptop. I'll fiddle with it and see what I can get out of it otherwise,

Any other ideas?

-EDIT-

Hmm. I attempted to add songs to the player, and this worked fine. I could also delete songs on the player just fine. But no matter what I do, I can't copy songs from the player.

So I guess this is more of a strange/annoying glitch rather than an outright problem. I don't see the need much to copy songs from the player.

Thanks again for the awesome tutorial. I guess I'll live with it like this unless a solution comes along, no biggie! :D

---

### Post by zazen666 on 2006-12-30
Hello Again,
Thanks again for the helping getting my Zen up and running on Gnomad2.

New Question for you,,,,
I would like to explore my Zen with Amarok, but i cant get it to read my zen. (gnomad2, no problmes). Do I need to do something special to get it working with amarok?
Thanks again

---

### Post by msak007 on 2006-12-30
> **Indref said:**
> Indref - I've never seen that specific output, but I do have a couple of questions:

1. On the player it says "NOMAD JUKEBOX Zen", the model number is DAP-HD0007. It holds 20GB. 

2. I have next to no idea about the firmware. It says version 1.11.01 on the players GUI. I got the player on eBay and I haven't touched the firmware myself.

3. I was trying to transfer a song from the player back to the laptop. I'll fiddle with it and see what I can get out of it otherwise,

Any other ideas?

-EDIT-

Hmm. I attempted to add songs to the player, and this worked fine. I could also delete songs on the player just fine. But no matter what I do, I can't copy songs from the player.

So I guess this is more of a strange/annoying glitch rather than an outright problem. I don't see the need much to copy songs from the player.

Thanks again for the awesome tutorial. I guess I'll live with it like this unless a solution comes along, no biggie! :D

**Indref** - According to Creative's site, the latest firmware for your device is 1.12.02. Not sure if it warrants an upgrade, but it doesn't look like it adds MTP capability. It has to be updated through Windows anyway. You can get the firmware and the details [here]("http://us.creative.com/support/downloads/download.asp?MainCategory=213&nRegionFK=&nCountryFK=&nLanguageFK=&sOSName=Windows+XP&region=1&Product_Name=NOMAD+Jukebox+Zen&Product_ID=117&modelnumber=&driverlang=1033&OS=10&drivertype=0&x=21&y=23"). 

If you're not having any problems transferring the files from your HD to the player, but are getting errors going the other way around, then maybe it's a permission error. Are you transferring the files to a location you don't have write permissions to (for example, some place outside your /home directory)?
> **zazen666 said:**
> Hello Again,
Thanks again for the helping getting my Zen up and running on Gnomad2.

New Question for you,,,,
I would like to explore my Zen with Amarok, but i cant get it to read my zen. (gnomad2, no problmes). Do I need to do something special to get it working with amarok?
Thanks again

**zazen666** - Amarok is not seeing it because, despite Amarok 1.4.4 officially supporting libmtp and MTP devices, the version in the repos was not compiled with MTP support. I've always wondered why, but I saw a bug report the other day with a comment from Brandon Holtsclaw (imbrandon) who is responsible for packaging Amarok for Ubuntu. His explanation was that libmtp was not in the *main* repository so it couldn't be included as a dependency for Amarok. That will change for Feisty however, and Amarok in the repos will be compiled with MTP and support the devices out of the box. He also indicates that it will be backported (to Dapper / Edgy?). If you want to get it working in the meantime, I've seen several How-Tos in the forums on how to compile Amarok Just for reference, [here]("http://bugs.kde.org/show_bug.cgi?id=139247")'s the bug report and Brandon's explanation:

> *------- Additional Comment       [#7]("http://bugs.kde.org/show_bug.cgi?id=139247#c7") From Brandon Holtsclaw        2006-12-28 19:46 -------     *      
note : amarok in edgy was not compiled with MTP support because libmtp dident make it into main untill the feisty release schedule, thus this is not a bug its just not supported atm in edgy, I will backport this soon 

---

### Post by Synethesia on 2006-12-31
I just got a Creative Zen Vision M.  I am also a linux newbie who switched so I wouldn't be tempted by WOW, (and also to make sure that I would learn linux before I needed it in academia).  I am trying to get files onto my MP3 player, but I have been working for hours and been unsucessful.  

I have just updated to edgy (and am running it in gnome), as I thought that may make things easier, however all it did was identify a "camera."  Even though I have gnomad2 installed, it won't detect my "jukebox."  

I went through most of the compliation instructions for libmtp and libnjb, and I tried to do the same for gnomad2, however, I kept on coming up with the error 

-L/usr/local/lib -lmtp -lusb   
jukebox.o: In function `hd2jb_thread':
/home/trillian/Desktop/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/trillian/Desktop/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

Therefore, I just did sudo apt-get gnomad2, which installed it, but it is still being idle.  

also, I am having a hard time with the whole hotplug thing... what is hotplug?  Every time I try to install it, it says

dpkg: regarding hotplug_0.0.20040329-22ubuntu13_all.deb containing hotplug:
 udev conflicts with hotplug

I really want to get this MP3 player working, as I am starting to get frustrated with linux.  I can't seem to master linux think, and I had to give my new (and pink) digital camera to my mother because it contained a CD (I got a fuji finepix Z3).  I don't really want to switch back as the command line stuff is quite nifty, but I would like at least some of the functionality I experienced with windows.  

Thanks!!!

---

### Post by msak007 on 2006-12-31
> **Synethesia said:**
> I just got a Creative Zen Vision M.  I am also a linux newbie who switched so I wouldn't be tempted by WOW, (and also to make sure that I would learn linux before I needed it in academia).  I am trying to get files onto my MP3 player, but I have been working for hours and been unsucessful.  

I have just updated to edgy (and am running it in gnome), as I thought that may make things easier, however all it did was identify a "camera."  Even though I have gnomad2 installed, it won't detect my "jukebox."  

I went through most of the compliation instructions for libmtp and libnjb, and I tried to do the same for gnomad2, however, I kept on coming up with the error 

-L/usr/local/lib -lmtp -lusb   
jukebox.o: In function `hd2jb_thread':
/home/trillian/Desktop/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/trillian/Desktop/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

Therefore, I just did sudo apt-get gnomad2, which installed it, but it is still being idle.  

also, I am having a hard time with the whole hotplug thing... what is hotplug?  Every time I try to install it, it says

dpkg: regarding hotplug_0.0.20040329-22ubuntu13_all.deb containing hotplug:
 udev conflicts with hotplug

I really want to get this MP3 player working, as I am starting to get frustrated with linux.  I can't seem to master linux think, and I had to give my new (and pink) digital camera to my mother because it contained a CD (I got a fuji finepix Z3).  I don't really want to switch back as the command line stuff is quite nifty, but I would like at least some of the functionality I experienced with windows.  

Thanks!!!

**Synethesia** - First of all welcome, and hang in there. I know it can be frustrating at first so we'll try to help as much as possible. I can point out a few things you're having problems with right off the bat and explain why they're not working.

1. You can't use the version of Gnomad from the repositories. It's not compiled with MTP support, so that's why my instructions for Edgy specifically said you can use the version of libmtp and libnjb from the repositories, but you'd have to compile Gnomad manually to pick up libmtp.

2. You don't need to compile libnjb from the repositories if you're running Edgy. The version included in the repos is the latest, all you need when compiling Gnomad is the -dev package for libnjb. If you copy / paste everything I said to install beforehand, you shouldn't run into any issues there.

3. Why are you trying to install hotplug?? That is the old, deprecated hardware detection system. This has since been replaced by udev, which is what Dapper and Edgy both use. They conflict with each other and can't both be installed at the same time, which is why you're getting the error. Not sure where you got the idea that you have to install hotplug, but don't.

Now I have a couple of questions: 

1. Were you trying to use Method 1 (compiling only Gnomad) or Method 2 (compiling both Gnomad *and* libmtp)?
2. Do you still have Gnomad, libmtp, or libnjb from the repositories still installed?

Right now the best thing to do would be to start over. To make things easier, we're going to use a combo of the GUI and the terminal.

1. Open Synaptic, search for all instance of Gnomad, libmtp, and libnjb and purge them. 
2. Then to make sure all their dependencies and unneeded packages are removed, open a terminal and type
```
sudo apt-get autoremove
```

Once you've done that you should be back to where you started. For best results, I'd recommend following Method 2 because you'll get a newer version of libmtp. Follow the instructions verbatim, in order, and you should not run into any issues. If you do, post them here and we'll go from there. 

Regarding your camera, not sure if I can help there but I'm not sure what having a CD included with the camera has to do with anything? It's probably just Fuji's proprietary software they want you to use for transferring photos or the driver you need so Windows can detect it. The camera should be detected by plugging it in, and there are many photo applications available. If you have any specific problems, you can post them in the hardware forum and people should be able to help you out there.

---

### Post by ubunter1 on 2006-12-31
msak007
    i followed your suggestions and i got this- The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:
Done. The new package has been installed and saved to
 /home/robert/gnomad_install/libmtp-0.1.2/libmtp_0.1.2-1_i386.deb
 You can remove it from your system anytime using:
   dpkg -r libmtp
-then i followed thbe next step and continued with the original tutorial and it woudnt let me do it because the packages did not exist.so i uninstalled everything and did it again this is the result.-
========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/robert/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

.ive saved the whole log of the process for future reference.thanks for the help.

---

### Post by Synethesia on 2006-12-31
libmtp and libnjb are not showing up in synaptic, so how do I deinstall them competely.  Also, how do I make sure that all repositories are gone so I can start fresh.  I have autoremove already, but that doesn't seem to help.  

Thanks again....

---

### Post by ubunter1 on 2006-12-31
> **Synethesia said:**
> libmtp and libnjb are not showing up in synaptic, so how do I deinstall them competely.  Also, how do I make sure that all repositories are gone so I can start fresh.  I have autoremove already, but that doesn't seem to help.  

Thanks again....
i tried the, sudo aptitude purge (then libmtp or libnjb),in the terminal. it worked uninstalling them for me.

---

### Post by Synethesia on 2006-12-31
sudo aptitude purge didn't seem to do much of anything... it didn't say that anything was removed...  (it said 33 programs kept though...)  

How can I be *sure* that everything is gone, as I think that is why gnomad is not compiling for me...

---

### Post by ubunter1 on 2006-12-31
i just tryied the beginning of the tutorial that msak007 wrote where it says before installation-
 Current versions of the software:
Gnomad - 2.8.9
libnjb - 2.2.5
libmtp - 0.1.2

Before proceeding, make sure you do not have any packages that conflict. If you have already installed Gnomad from the repositories prior to running this how-to, please uninstall it and its dependencies first:

Code:

sudo aptitude purge gnomad2

Also, if you have previously used this how-to to install Gnomad or libmtp, please uninstall the currently installed version before trying to compile the new version to prevent conflicts and errors.

it worked for me although i havnt been able to get the rest working.good luck though.

---

### Post by Fixxxer on 2007-01-01
I cant' get gnomad2 to compile with the newest libmtp, I had to use an older version (0.0.21). My Zen V Plus works with it  though.

---

### Post by con on 2007-01-01
Installation of gnomad failed with version 0.1.2 of libmtp but it worked with version 0.1.0

---

### Post by msak007 on 2007-01-01
First things first, Happy New Year to everybody!

I've verified a few things regarding the errors encountered recently. First, I've confirmed the compiling errors and it seems that Gnomad won't compile with libmtp0.1.1 or libmtp0.1.2. The output I get is the same I've seen others have:

```
jukebox.o: In function `hd2jb_thread':
/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/motasim/gnomad_install/gnomad2-2.8.9/src'
make: *** [all-recursive] Error 1
```I apologize as I usually test these before updating the instructions, but didn't have the time the past couple of days and around New Year's and such. There were 2 releases back to back, so normally a bug in the first version is fixed if another one is released shortly thereafter within a few days. In this case though it seems to have slipped with both versions. I'll look into it a bit more and see if I can find out what's happening there. The second error is the one encountered when running the hotplug script, namely
```
hotplug.sh: 12: function: not found
hotplug.sh: 32: cannot open : No such file
```This only affects Edgy, and is due to Edgy using dash as a default instead of bash. This is just another example of a script that was written as```
#!/bin/sh
```expecting it to call bash, when it should explicitly call it by being ```
#!/bin/bash
```The easiest thing is to just do a ```
sudo bash hotplug.sh
```I've updated the instructions accordingly to reflect both errors, and for now will recommend sticking with libmtp 0.1.0, which is the last confirmed release that Gnomad compiles properly with, until I can confirm that it has been fixed. If you guys have any other problems or suggestions, please let me know.

---

### Post by bsalt on 2007-01-04
First off, happy belated new year guys!

Also, I LOVE this How-To, it is what kept me from entering the dark side again (Windows).

Hey, I just figured I'd ask this question:

Now that Feisty Fawn will be shipping with Amarok 1.4.4 which will already include MTP support, will there be the same scenario for gnomad2?

I was also wondering if anybody knew of a way (or of a program) that would save the song list of the mp3 player to an external .xml or even a .csv file, to increase load times. I was also wondering if anybody knew if there was talk of any MTP transfer program that contained a button that would automatically synchronize with a directory or music library. That was a great feature in Windows Media Player and it would be cool to see it added in the near future. 


Jonathan

---

### Post by Sefrin on 2007-01-06
I followed this how to to get my Zen V Plus working in Dapper.  It works great and does just what I need.

When installing however I had to restart the process when I realized the first link in the original post links to libmtp-0.1.1 and not libmtp-0.1.0.  I tried completing the install first with 1.1 and got the compile error so I restarted with 1.0 and it worked fine.

Thanks!

---

### Post by ubunter1 on 2007-01-07
so im trying to get this working once again,i admit im new to this and a bit clued out.when using the updated guide and installing libmtp-0.1.0 from the link it provides it downloads but it is not the 0.1.0 ,it downloads as 0.1.1 so when i go to the extracted folder in the terminal command it comes up as this-  robert@robert-desktop:~$ cd libmtp-0.1.0
bash: cd: libmtp-0.1.0: No such file or directory
robert@robert-desktop:~$
is it the link or me? thanks for your time,im willing to go through a bit of a learning tutorial to learn this and understand it so bear with me.rob:-k

---

### Post by Sefrin on 2007-01-07
I used a very technical and brilliant way to download 0.1.0 instead of 0.1.1 (not really, I'm just joking around).  :rolleyes: 

Click on the link that says libmtp-0.1.0 but directs you to libmtp-0.1.1 in error.  Cancel the download.  Then, edit the address to be libmtp-0.1.0 instead and hit enter.  Download that one and then follow the guide.

Hopefully the OP can correct the link soon.

---

### Post by msak007 on 2007-01-07
Sorry guys! The link is wrong, I just realized it because you guys pointed it out. I've been trying to modify the post to update the link and I'm not sure if it's the forums or my internet connection, but it times out when trying to edit a post. ubunter1, you can either follow Sefrin's suggestion or click [here]("http://prdownloads.sourceforge.net/libmtp/libmtp-0.1.0.tar.gz?use_mirror=nchc") to download the correct version until I can modify the first post.

---

### Post by ubunter1 on 2007-01-08
msak007
 thanks for the response.i did it all again and got further than ive gotten before but results came up as this- 
****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
it came up as i was about to start gnomad in the terminal.
i have the whole log saved what can i do now? should i post it?.thanks.
i just want to listen to the doves album-lost souls at work,my old collection is gettin stale.

---

### Post by Synethesia on 2007-01-09
I went back... and recompiled everything following the instructions with libmtp 1.0.0, and I still couldn't compile gnomad2.  

This is the error message I got...  

Making install in src
make[1]: Entering directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/local/lib -lmtp -lusb   
jukebox.o: In function `hd2jb_thread':
/home/trillian/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

What do I do now?  

Thanks...

---

### Post by ali4728 on 2007-01-09
Hi guys, I am trying to get my Zen Microphoto work on Edgy, I installed gnomad2 but when start it I get the following error. Any comments appreciated..

ali@LD-1:~/gnomad_install/gnomad2-2.8.9$ gnomad2
Autodetected device "Creative Zen MicroPhoto" (VID=041e,PID=413c) is known.
usb_claim_interface(): Device or resource busy
Connection error.
PDE device NULL.



ali@LD-1:~$ cat /proc/bus/usb/devices

T:  Bus=05 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=413c Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative Zen MicroPhoto
S:  SerialNumber=01052551BE0390A5
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=usbfs
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=1ms

---

### Post by iat on 2007-01-10
Trying to compile libnjb-2.2.5, I get an error message saying:

Installing Debian package... FAILED!

What should I do?

Thanks in advance

---

### Post by iat on 2007-01-10
I've installed libmtp-0.1.0 instead of libmtp-0.1.2 and everything went well. Thank you folks; now I can upload and download music to my Zen V without any trouble.

---

### Post by ubunter1 on 2007-01-10
it failed for me once again,i got to the part where i was installing and checking gnomad,here is the results.


Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/robert/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

robert@robert-desktop:~/gnomad_install/gnomad2-2.8.9$

thanks for the help.](*,)

---

### Post by ntetreau on 2007-01-10
ubunter1:  Please make sure you are using libmtp 0.1.0 and not 0.1.1 or 0.1.2.  You compile error suggest you might be using the wrong version.

Nic

---

### Post by ubunter1 on 2007-01-11
ok just checked it again made sure all the right versions are in and got this-

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -lmtp -lusb
jukebox.o: In function `hd2jb_thread':/home/robert/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/robert/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by atulprasad on 2007-01-11
Hi.. I have Ubuntu 6.06 on my system.. I recently bought a Creative Zen V,I tried installing gnomad 2.8.9. It is installed but still says that "No jukeboxes found on USB bus"
what could be the problem.. can anybody help.. i have usb 1.1 on my sys and not 2.0... is that an issue? Please let me know

Thanks

---

### Post by vrih on 2007-01-11
I've just bought a zen vision:m and I've tried both methods for getting it to work on edgy. The battery will not charge on my linux computer and the device appears to crash when plugged into the usb port.

It works fine on a windows machine and have had to charge the battery like that. Is there something obvious that I just haven't done?

woops, just needed a firmware update

---

### Post by victor_c26 on 2007-01-11
Anybody had trouble getting a Zen Micro 5GB to work with Gnomad?

Everytime I start Gnomad with the device connected through USB, it keeps crashing Gnomad. I tried opening Gnomad first, and making it rescan for devices, but the same thing happens.

---

### Post by ntetreau on 2007-01-12
atulprasad:  I've you tried following the howto on the first page?

victor_c26:  Could you check try mtp-detect and post the output, also might want to check if there is a firmware update for your device first.

ubunter1:  I'm sorry to insist but I can the exact same error as you do if I try to compile gnomad2 or amarok against libmtp 0.1.1 or 0.1.2.  There were some issues with the download link for a while, perhaps you could try to download the 0.1.0.tar.gz again?

Nic

---

### Post by Synethesia on 2007-01-12
I have tried and tried again to install gnomad and I keep on getting errors.... this is the latest...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/local/lib -lmtp -lusb   
jukebox.o: In function `hd2jb_thread':
/home/trillian/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

I am using libmtp version 0.1.0, I have downloaded it once, then removed it, then downloaded it again.  (I used the link on the site to find the page to search for it.. and then I downloaded the older version from that site...)  

I am following the instructions exactly as perscribed uninstalling gnomad2 and libmtp every time.  I can't seem to figure out what is wrong, and why I can't get it..... this computer is really starting to get on my nerves... and I don't think biologists use linux anyway....  

I have no idea what is going on... however, of I can't get this to work, I am either returning the mp3 player and getting different one, or switching back to microsoft.  Anyone know of any mp3 players that are more linux friendly?  

--Synethesia.

---

### Post by atulprasad on 2007-01-13
Hi faced the same problem:

jukebox.o: In function `flush_usage':jukebox.c:(.text+0x20fa): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status

Can anyone please help :(

---

### Post by ubunter1 on 2007-01-13
> **Synethesia said:**
> I have tried and tried again to install gnomad and I keep on getting errors.... this is the latest...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
gcc  -g -O2   -o gnomad2  id3read.o gnomad2.o prefs.o filenaming.o jukebox.o util.o mp3file.o editmeta.o filesystem.o playlists.o xfer.o data.o player.o metadata.o wmaread.o wavfile.o -pthread -lgthread-2.0 -lnjb -lusb -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0 -lid3tag -lz -L/usr/local/lib -lmtp -lusb   
jukebox.o: In function `hd2jb_thread':
/home/trillian/gnomad_install/gnomad2-2.8.9/src/jukebox.c:2011: warning: the use of `tmpnam' is dangerous, better use `mkstemp'
jukebox.o: In function `flush_usage':
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/trillian/gnomad_install/gnomad2-2.8.9/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

I am using libmtp version 0.1.0, I have downloaded it once, then removed it, then downloaded it again.  (I used the link on the site to find the page to search for it.. and then I downloaded the older version from that site...)  

I am following the instructions exactly as perscribed uninstalling gnomad2 and libmtp every time.  I can't seem to figure out what is wrong, and why I can't get it..... this computer is really starting to get on my nerves... and I don't think biologists use linux anyway....  

I have no idea what is going on... however, of I can't get this to work, I am either returning the mp3 player and getting different one, or switching back to microsoft.  Anyone know of any mp3 players that are more linux friendly?  

--Synethesia.


hi i am facing the same problems as you and am new to linux,my readout from the terminal is the same as yours,as ive taken the exact same steps so maybe this is a common problem between certain computer types and its hardware?
as to your question about mp3 players being more linux friendly i think the problems we have been having would be the same for all companys mp3 players,i just think the linux recognisation for these types of devices is not what it could be yet.i dont want to go back to windows but i have two nagging computer problems and this player is one of them.i think sticking it out on ubuntu is worth it and i think once we learn a bit it will become easier. if i get progress on my installation ill post it here for you to see..i think we can also check the forums at [www.creative.com](www.creative.com) for possible drivers or questions.peace.rob.

---

### Post by Sefrin on 2007-01-13
The only thing I can suggest (no pro here but this worked for me) is that if you mess up or need to start over (I used libmtp.0.1.1 first by accident instead of 0.1.0) do: 

```
sudo aptitude purge gnomad2
sudo aptitude purge libmtp-0.1.1
sudo aptitude purge libnjb-2.5.5
```

Then, start over from scratch.

---

### Post by ubunter1 on 2007-01-13
thanks i will try again today.

---

### Post by atulprasad on 2007-01-13
Hi.. I tried doing that again today but got the same error.. i even tried with gnomad 2.8.8 but of no help..Please somebody suggest a solution...

---

### Post by ntetreau on 2007-01-13
Sorry to hear you are having these compile problems, this is probably due to previous problem with libmtp-0.1.1 or so.  Anyway, we can try something, I compiled libnjb-2.2.5, libmtp-0.1.0 and gnomad-2.8.9 and made .deb files you can try to install.  First time so this may not work!

Nic

If this is a sucess, I'll upload amarok+MTP

---

### Post by atulprasad on 2007-01-13
(gnomad2:19574): Gdk-WARNING **: locale not supported by Xlib

(gnomad2:19574): Gdk-WARNING **: cannot set locale modifiers
PDE device NULL.

This what the output when i ran gnomad2.. Is Zen V not supported??
There was no entry corresponding to my lsusb output in nomad.rules file
so i added one.. did a udev restart

Stll the error is the same : No Jukebox founds on USB bus

Someone please help.. Its been 2 weeks now that i have not been able to set it up..

---

### Post by ubunter1 on 2007-01-13
> **ntetreau said:**
> Sorry to hear you are having these compile problems, this is probably due to previous problem with libmtp-0.1.1 or so.  Anyway, we can try something, I compiled libnjb-2.2.5, libmtp-0.1.0 and gnomad-2.8.9 and made .deb files you can try to install.  First time so this may not work!

Nic

If this is a sucess, I'll upload amarok+MTP

thanks for the reply,i tried installing the first one libmtp and it says i have a newer version and wont let me install it,the other two worked by using the gdebi package installer when i click on the links,i looked in my apps-sound and video-gnomad clicked it but it woudnt popup,so do i need to follow the rest of the steps in the guide or just the ones you listed.rob.

---

### Post by ntetreau on 2007-01-13
You are getting the error about a newer package because you have indeed install 0.1.1 probably.  Do a search in synaptics for libmtp and remove the one you have there, then try installing the deb i provided, run gnomad2 from the terminal to see what errors you get.  If you end up being able to remove the 0.1.1, you wil probably be able to compile your own gnomad2 though.

I told you the deb files were a long shot, this might not work in the end.

Nic

P.S.:  Here's my udev libmtp.rules file (uncompress and saves as libmtp.rules in /usr/udev/rules.d/)
you may need to reboot, maybe not!

---

### Post by ntetreau on 2007-01-13
Ok, the libnjb package I provided didn't work well, you should just install the ones (libnjb and libnjb-dev) provided in Synaptics and everything should/might work!  Don't forget to copy the libmtp.rules file into the udev directory (read my last post).  Good luck.

Nic

---

### Post by ubunter1 on 2007-01-13
> **Sefrin said:**
> The only thing I can suggest (no pro here but this worked for me) is that if you mess up or need to start over (I used libmtp.0.1.1 first by accident instead of 0.1.0) do: 

```
sudo aptitude purge gnomad2
sudo aptitude purge libmtp-0.1.1
sudo aptitude purge libnjb-2.5.5
```

Then, start over from scratch.

> **ntetreau said:**
> You are getting the error about a newer package because you have indeed install 0.1.1 probably.  Do a search in synaptics for libmtp and remove the one you have there, then try installing the deb i provided, run gnomad2 from the terminal to see what errors you get.  If you end up being able to remove the 0.1.1, you wil probably be able to compile your own gnomad2 though.

I told you the deb files were a long shot, this might not work in the end.

Nic

P.S.:  Here's my udev libmtp.rules file (uncompress and saves as libmtp.rules in /usr/udev/rules.d/)
you may need to reboot, maybe not!


sefrin-thanks for the purge tip i did that then tried ntetreaus method it didnt work,so i purged all again then used msak007 tutorial again ang it worked and am transfering as we speak i think the dependencie issues conflicting with each other were the problem and the purge really helped.

ntetreau-id like to see your method work as it was very short and to the point so hopefully someone else will try this and i hope it goes well for them.thanks to all who helped now ive only got a video problem but thats another thread.ill continue to look at this,and learn and see if i can be of help to someone.thanks again

---

### Post by Synethesia on 2007-01-13
I got it to work too... I tried installing your .deb files with dpkg which didn't quite work...  

However, after that I purged anything I could find... and also removed the .rules files from /etc/udev/rules.(something), and started over with the second method on the page as I am running edgy...  and somehow, it worked...  

I guess I am kind of getting the hang of this... yesterday I even got my computer to scroll correctly again--(even though everything now looks like it has been shrunk on my monitor...  and I don't know how to fix it... however, it sure beats that rediculous scrolling...)  

I guess I am getting the hang of this... maybe I don't have to switch back...

--Synethesia

---

### Post by ntetreau on 2007-01-13
Ok, since it didn't work for anyone, I finally removed the deb files, sorry it didn't work.

Nic

---

### Post by msak007 on 2007-01-13
Wow, seems that the new versions of libmtp really hosed everything for a lot of people. I'm sorry you guys have been having all these problems and I haven't had a chance to help anybody out. Nic, I apppreciate all the assistance you've been providing as I know you've been following this thread and contributing to it from the start. As you guys already found out, all these errors were due to the new versions being installed and not completely uninstalled / purged before trying to install an older version. 

> **ubunter1 said:**
> ntetreau-id like to see your method work as it was very short and to the point so hopefully someone else will try this and i hope it goes well for them.thanks to all who helped now ive only got a video problem but thats another thread.ill continue to look at this,and learn and see if i can be of help to someone.thanks again
**ubunter1** - There was actually at one time a scripted install that was provided by a user in the forums. He kept it up to date for a while and hosted the script and all the debs so all you had to do was run a script and it installed everything for you. I even had instructions in my first post for those who wanted the scripted install. Unfortunately, the maintainer stopped updating the packages and the script, and I couldn't get a hold of him so I removed the instructions. I would love to be able to provide some debs or a script for you guys to install, but I don't know how to package deb files. checkinstalled packages really aren't the type of debs you want to give to other people because it's not the proper / best method for mass distribution of debs. Maybe someone more knowledgeable than me in that area can step in and provide those files.

---

### Post by ubunter1 on 2007-01-14
> **msak007 said:**
> Wow, seems that the new versions of libmtp really hosed everything for a lot of people. I'm sorry you guys have been having all these problems and I haven't had a chance to help anybody out. Nic, I apppreciate all the assistance you've been providing as I know you've been following this thread and contributing to it from the start. As you guys already found out, all these errors were due to the new versions being installed and not completely uninstalled / purged before trying to install an older version. 


**ubunter1** - There was actually at one time a scripted install that was provided by a user in the forums. He kept it up to date for a while and hosted the script and all the debs so all you had to do was run a script and it installed everything for you. I even had instructions in my first post for those who wanted the scripted install. Unfortunately, the maintainer stopped updating the packages and the script, and I couldn't get a hold of him so I removed the instructions. I would love to be able to provide some debs or a script for you guys to install, but I don't know how to package deb files. checkinstalled packages really aren't the type of debs you want to give to other people because it's not the proper / best method for mass distribution of debs. Maybe someone more knowledgeable than me in that area can step in and provide those files.

no offence but yours is the method i used to install this program and i thank you very much, every bit of information is needed for me to understand this system.i think all that was needed for me was to flush out the old stuff and implement the new.youve made me understand all this in a new way,.but i like to try different ways as im new to this so i thank all of you who have helped and i wish to have your knowledge on this.peace.rob.

---

### Post by msak007 on 2007-01-14
> **ubunter1 said:**
> no offence but yours is the method i used to install this program and i thank you very much, every bit of information is needed for me to understand this system.i think all that was needed for me was to flush out the old stuff and implement the new.youve made me understand all this in a new way,.but i like to try different ways as im new to this so i thank all of you who have helped and i wish to have your knowledge on this.peace.rob.
No offense taken :) I know this is not the easiest method, but I just wanted to let you know that an easier method was tried once. If I can come up with an easier solution, I'll definitely let you guys know.

---

### Post by scelter on 2007-01-14
Question for msak007:
- first of all thanks for all your work on this subject. The info here has been very helpfull to me.

- now my problem:
I managed to get gnomad2 working, but only with sudo. I want to be able to run it as a regular user, so I followed your instruction 20 pages back in this topic:

```
# Creative Zen Nano Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4139", SYMLINK+="libmtp-%k", MODE="666"
```

I've replaced the idProduct by the correct one (this is 4152) for my device, because I have a zen V plus, but it is not working for me. This is the feedback I got from gnomad2:

```
Autodetected device with VID=041e and PID=4152 is UNKNOWN.
Please report this VID/PID and the device model name etc to the
libmtp development team!
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
Could not get device info!
Connection error.
PDE device NULL.

```

Any thoughts on how to solve this problem.
Thx.

---

### Post by ntetreau on 2007-01-14
Hi Scelter, from the libmtp.rules file in libmtp.0.1.2, the line for your device is:

```
# Creative Zen V Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="6
66"

```

This seems identical to what you have, are you sure it still doesn't work as normal user after a reboot or a restart of udev?

Nic

---

### Post by msak007 on 2007-01-14
**scelter** - All my instructions have been consolidated to the first post so you don't need to hunt through the thread. But I do have a few questions:

1. Which OS are you running (Dapper or Edgy), and if Edgy, which method did you use? 
2. If Edgy, did you follow method 1 or 2?
3. Which file did you edit to add your product, libmtp.rules?

Edit: Sorry, I thought you had the Zen Nano Plus. As Nic stated already, libmtp.rules already has your device in there so you don't need to edit it manually. Installing libmtp 0.1.0 (0.1.1 and 0.1.2 cause Gnomad to error out when compiling) and then running the hotplug script should put the file where it needs to go. I looked through libmtp.rules that's included with libmtp 0.1.0 and your device was supported with that version as well. Answer the questions above and we can go from there.

---

### Post by scelter on 2007-01-14
I decided to start over the installation process using method 2, because I missed the hotplug.sh step in your tutorial.
Now I'm having trouble installing libmtp0.1.0. When I'm trying this:
```
sudo checkinstall
```
I get "Installing Debian package failed".
This is what I get from the log file:
```
(Reading database ... 103548 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.0-1_i386.deb) ...
dpkg: error processing /home/kwinten/Desktop/zen/libmtp-0.1.0/libmtp_0.1.0-1_i38
6.deb (--install):
 trying to overwrite `/usr/bin/mtp-playlists', which is also in package libmtp-d
ev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kwinten/Desktop/zen/libmtp-0.1.0/libmtp_0.1.0-1_i386.deb
```

To answer your questions: I'm using Edgy, method 2. And I created and edited libmtp.rules. (which was a mistake because I missed the hotplug.sh line in your tutorial)

---

### Post by msak007 on 2007-01-14
> **scelter said:**
> I decided to start over the installation process using method 2, because I missed the hotplug.sh step in your tutorial.
Now I'm having trouble installing libmtp0.1.0. When I'm trying this:
```
sudo checkinstall
```I get "Installing Debian package failed".
This is what I get from the log file:
```
(Reading database ... 103548 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.0-1_i386.deb) ...
dpkg: error processing /home/kwinten/Desktop/zen/libmtp-0.1.0/libmtp_0.1.0-1_i38
6.deb (--install):
 **trying to overwrite `/usr/bin/mtp-playlists', which is also in package libmtp-dev**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/kwinten/Desktop/zen/libmtp-0.1.0/libmtp_0.1.0-1_i386.deb
```To answer your questions: I'm using Edgy, method 2. And I created and edited libmtp.rules. (which was a mistake because I missed the hotplug.sh line in your tutorial)
Yeah that hotplug script is what adds the rules file so it's an important step. That's why I wanted to know which method you were using, because the repo method puts the file where it needs to go without having to run a script. To get rid of the error, get rid of libmtp-dev which has a file conflicting with your attempted installation. Just type
```
sudo aptitude purge libmtp-dev
```and then try again. And as usual, if you run into any issues after that let us know.

---

### Post by scelter on 2007-01-15
Ok, everything is working fine now. I guess rushing your tutorial wasn't the best idea ](*,) 
Thx for your quick replies.

Next: getting my subwoofer volume to go up and down together with the master channel ;)

---

### Post by pak33m on 2007-01-15
Hello msak007,

I am a bit late at responding, well, at least since Christmas Day after getting a Creative Zen V.  I wanted to mention that I was able to get Gnomad installed & configured without  error using your detailed How To.  That is just after I made a cappuccino with my new espresso maker that I got for Christmas, too!

I followed your How To from the beginning to end & was done within 15 minutes or less.  If anything I would suggest for those having problems here NOT to skip any of the steps listed.

Also, after creating play lists on my Windows XP PC at work I was able to create & transfer to play lists where I wasn't able to before.

Thank you again for your How To.

---

### Post by ntetreau on 2007-01-16
For those interested, libmtp-0.1.3 is out but still cannot be compiled against by gnomad2.  On a brighter note, amarok svn now compiles fine with libmtp > 0.1.0.  I doubt there is any new functionality although I had some problems with French mp3s before and they transfered fine with the newer libmtp... maybe just lucky!

Nic

---

### Post by adamsjw2 on 2007-01-18
Hi,
Did you get this error when compiling libmtp?

configure: error: I can't find the libusb libraries on your system. You may need to set the LDFLAGS environment variable to include the search path where you have libusb installed before running configure (e.g. setenv LDFLAGS=-L/usr/local/lib)

Ubuntu doesn't use setenv, so I can't get libmtp installed.

Any ideas,
TIA
Jim A

---

### Post by ntetreau on 2007-01-19
hi adamsjw2, you could try installing libusb-dev, see if that works.

Nic

---

### Post by adamsjw2 on 2007-01-19
ntetreau,
Thanks for your quick reply. The compile seemed to go OK now. After installing and running gnomad2, I get this error

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
PDE device NULL.

Any advice? Could it be a permission problem on the device?

Jim A.

---

### Post by ntetreau on 2007-01-19
Hi Jim,
good to hear the compile worked.  What device to do you have?  Is it listed in the file libmtp-0.1.0/libmtp.rules ?  If it is and you copied the libmtp.rules files to the udev directory, it is not a permission problem.  If it is listed and copied, perhaps you can look into upgrading the firmware on your device (windows box needed usually).  If it is not listed, you should head to the libmtp sourceforge discuss list and post there with the info required.  By the way, have you used this device in windows before?  Did it work well?  

Nic

---

### Post by adamsjw2 on 2007-01-19
netreau,
Again, thanks so much for your help.
I have a Zen V, which worked in WinXP without a hitch.
The device is listed in the libmtp.rules file in /etc/udev/.
Still, no luck.
Dmesg recognizes when I plug/unplug as a usbdevice, however gnomad2 still reports "no jukebox found"
I'll see if the folks at sourceforge can help and I'll report back here. Any other ideas would be greatly appreciated.
TIA,
Jim

---

### Post by schwascore on 2007-01-20
Hey all, I was having some trouble and I thought someone here might be able to help.

Running Edgy, I followed the instructions from this post.  Everything worked fine until I tried to compile gnomad2.  Here is the last bit of output from "sudo make":

```
jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/josh/gnomad_install/gnomad2-2.8.9/src'
make: *** [all-recursive] Error 1

```

Looks like it doesn't agree with a certain function call in libmtp, so I tried it with libmtp-0.1.3, which gave the same result.  I have also been helping another individual through this install process and they arrived at the same problem on their machine.

Does anyone know how to fix this?

---

### Post by ntetreau on 2007-01-20
Hi swchascore, your problem is an easy one to fix, you installed the wrong version of libmtp (>0.1.0) so you need to remove it

```
sudo aptitude purge libmtp
```

and recompile libmtp-0.1.0.  Then, gnomad2 will compile without a hitch.

Nic

---

### Post by schwascore on 2007-01-20
Thanks a lot, works fine now.

---

### Post by ntetreau on 2007-01-20
msak007 -- Perhaps it would be a good idea to remove the links to libmtp 0.1.2 in your instructions, this seems to cause some confusion.  What do you think?

Nic

---

### Post by m0rph on 2007-01-21
After much trouble I have found the problem with the guide;

Your link to libmtp 0.1.0. actual downloads libmtp 0.1.1. resulting in the following error 
when trying to compile gnomad2

jukebox.c:(.text+0x2225): undefined reference to `LIBMTP_Get_Storageinfo'
collect2: ld returned 1 exit status
make[1]: *** [gnomad2] Error 1
make[1]: Leaving directory `/home/josh/gnomad_install/gnomad2-2.8.9/src'
make: *** [all-recursive] Error 1

I would like to thank schwascore & ntetreau for there posts above and would like to
advise that to complete this guide you need to download  libmtp 0.1.0.
[http://sourceforge.net/project/downloading.php?group_id=158745&use_mirror=optusnet&filename=libmtp-0.1.0.tar.gz&77126650](http://sourceforge.net/project/downloading.php?group_id=158745&use_mirror=optusnet&filename=libmtp-0.1.0.tar.gz&77126650)

I am now the happy owner of a Creative Zen Vision Micro working on Ubuntu....
Hooooorayyy...............

Now to just get it to work with Amarok :cool:

---

### Post by msak007 on 2007-01-22
> **ntetreau said:**
> msak007 -- Perhaps it would be a good idea to remove the links to libmtp 0.1.2 in your instructions, this seems to cause some confusion.  What do you think?

Nic
Nic - I've been thinking of doing the same but have been out of town the past several days. I've taken your suggestion and removed all download links to libmtp-0.1.2, and all instructions have been updated to reflect only 0.1.0. Hopefully a new version that fixes this issue will be released soon. Thanks again for all the help you've been providing.

> **m0rph said:**
> After much trouble I have found the problem with the guide;

Your link to libmtp 0.1.0. actual downloads libmtp 0.1.1. resulting in the following error 
when trying to compile gnomad2**m0rph** - Sorry for the confusion. I fixed the download link once but apparently it still linked to 0.1.1 for some reason. I placed the download link at the very top of the post where I thought it would be more easily viewable along with an explanation of the current problem, but the instructions all referenced 0.1.2. This has been fixed, and will remain that way until a new version that compiles correctly is released.

---

### Post by msak007 on 2007-01-24
Gnomad 2.8.10 was just released, and supposedly one of the fixes is that it will compile against libmtp-0.1.3. I'll give it a shot and update the instructions accordingly once I'm home from work. If anybody has success compiling both in the meantime, please let me know.

---

### Post by ntetreau on 2007-01-24
Hi msak007,
gnomad2 2.8.10 compiled fine on my system, everything seems to be working as expected.

Nic

---

### Post by msak007 on 2007-01-24
> **ntetreau said:**
> Hi msak007,
gnomad2 2.8.10 compiled fine on my system, everything seems to be working as expected.

Nic
Thanks Nic. I just tried it on my system and am happy to report that Gnomad 2.8.10 compiles successfully against libmtp 0.1.3. I've updated the instructions for the latest versions. Please upgrade if you haven't done so already, the release notes say many bugs have been fixed and I'm sure the latest version of libmtp includes support for many new devices. As usual, if you have any problems installing please let us know.

---

### Post by ButteBlues on 2007-01-26
The latest libmtp is buggin.

It tries to overwrite /usr/bin/gcc.

---

### Post by ntetreau on 2007-01-26
ButteBlues: It tries to overwrite gcc?  What do you base this on?  On my system, it didn't try any of that, in fact here's the listing of the installed files from synaptics:

/usr
/usr/share
/usr/share/doc
/usr/share/doc/libmtp
/usr/share/doc/libmtp/TODO
/usr/share/doc/libmtp/ChangeLog
/usr/share/doc/libmtp/COPYING
/usr/share/doc/libmtp/README
/usr/share/doc/libmtp/AUTHORS
/usr/share/doc/libmtp/INSTALL
/usr/share/doc/libmtp/doc
/usr/share/doc/libmtp/doc/Makefile.in
/usr/share/doc/libmtp/doc/Doxyfile.in
/usr/share/doc/libmtp/doc/examples.h
/usr/share/doc/libmtp/doc/mainpage.h
/usr/share/doc/libmtp/doc/Makefile
/usr/share/doc/libmtp/doc/Doxyfile
/usr/share/doc/libmtp/doc/Makefile.am
/usr/share/doc/libmtp/README.windows.txt
/usr/local
/usr/local/bin
/usr/local/bin/mtp-albumart
/usr/local/bin/mtp-albums
/usr/local/bin/mtp-connect
/usr/local/bin/mtp-detect
/usr/local/bin/mtp-emptyfolders
/usr/local/bin/mtp-files
/usr/local/bin/mtp-folders
/usr/local/bin/mtp-format
/usr/local/bin/mtp-getplaylist
/usr/local/bin/mtp-hotplug
/usr/local/bin/mtp-newplaylist
/usr/local/bin/mtp-playlists
/usr/local/bin/mtp-thumb
/usr/local/bin/mtp-tracks
/usr/local/bin/mtp-trexist
/usr/local/include
/usr/local/include/libmtp.h
/usr/local/lib
/usr/local/lib/libmtp.a
/usr/local/lib/libmtp.la
/usr/local/lib/libmtp.so.5.1.1
/usr/local/lib/pkgconfig
/usr/local/lib/pkgconfig/libmtp.pc
/usr/local/bin/mtp-delfile
/usr/local/bin/mtp-getfile
/usr/local/bin/mtp-newfolder
/usr/local/bin/mtp-sendfile
/usr/local/bin/mtp-sendtr
/usr/local/lib/libmtp.so
/usr/local/lib/libmtp.so.5

Perhaps you could expand a bit?

Nic

---

### Post by ButteBlues on 2007-01-26
I'm not sure what the discrepancy between our builds is, but it the checkinstall tried to overwrite my /usr/bin/gcc.

---

### Post by msak007 on 2007-01-26
No problems here, not sure what limbtp would have to do with gcc and why it would try to overwrite the compiler that compiles it :confused:. Could you maybe post the output that shows this?

---

### Post by Rodneyck on 2007-01-26
Well this failed for me. When I went to compile the libmtp, I got this error message...

"(Reading database ... 141961 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i
386.deb (--install):
 trying to overwrite `/usr/bin/mtp-detect', which is also in package libmtp-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
/var/tmp/lmfJVNrhRhMCJkTCFgTLJ/dpkginstall.log (END)"

---

### Post by msak007 on 2007-01-26
> **Rodneyck said:**
> Well this failed for me. When I went to compile the libmtp, I got this error message...
 
"(Reading database ... 141961 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i
386.deb (--install):
**trying to overwrite `/usr/bin/mtp-detect', which is also in package libmtp-dev**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
/var/tmp/lmfJVNrhRhMCJkTCFgTLJ/dpkginstall.log (END)"
Uninstall libmtp-dev and try again:
```
 
sudo aptitude purge libmtp-dev
```

---

### Post by ENN0 on 2007-01-26
amarok

---

### Post by ButteBlues on 2007-01-26
> **Rodneyck said:**
> Well this failed for me. When I went to compile the libmtp, I got this error message...

"(Reading database ... 141961 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i
386.deb (--install):
 trying to overwrite `/usr/bin/mtp-detect', which is also in package libmtp-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/rodney/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
/var/tmp/lmfJVNrhRhMCJkTCFgTLJ/dpkginstall.log (END)"
I also got this error. Uninstall libmtp2-2 and libmtp-dev, and then I'd get that gcc error afterwards.



> **checkinstall after a successful make]
will@will-laptop:~/libmtp-0.1.3$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@will-laptop ]
1 -  Summary: [ Package created with checkinstall 1.6.1 ]
2 -  Name:    [ libmtp ]
3 -  Version: [ 0.1.3 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libmtp-0.1.3 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/will/libmtp-0.1.3/src'
make[2]: Entering directory `/home/will/libmtp-0.1.3/src'
test -z "/usr/lib" || mkdir -p -- "/usr/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libmtp.la' '/usr/lib/libmtp.la'
/usr/bin/install -c .libs/libmtp.so.5.1.1 /usr/lib/libmtp.so.5.1.1
/usr/bin/install: setting permissions for `/usr/lib/libmtp.so.5.1.1': No such file or directory
(cd /usr/lib && { ln -s -f libmtp.so.5.1.1 libmtp.so.5 || { rm -f libmtp.so.5 && ln -s libmtp.so.5.1.1 libmtp.so.5 said:**
> : Leaving directory `/home/will/libmtp-0.1.3/src'
make[1]: Leaving directory `/home/will/libmtp-0.1.3/src'
Making install in examples
make[1]: Entering directory `/home/will/libmtp-0.1.3/examples'
make[2]: Entering directory `/home/will/libmtp-0.1.3/examples'
test -z "/usr/bin" || mkdir -p -- "/usr/bin"
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'connect' '/usr/bin/mtp-connect'
/usr/bin/install -c .libs/connect /usr/bin/mtp-connect
/usr/bin/install: setting permissions for `/usr/bin/mtp-connect': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'detect' '/usr/bin/mtp-detect'
/usr/bin/install -c .libs/detect /usr/bin/mtp-detect
/usr/bin/install: setting permissions for `/usr/bin/mtp-detect': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'tracks' '/usr/bin/mtp-tracks'
/usr/bin/install -c .libs/tracks /usr/bin/mtp-tracks
/usr/bin/install: setting permissions for `/usr/bin/mtp-tracks': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'files' '/usr/bin/mtp-files'
/usr/bin/install -c .libs/files /usr/bin/mtp-files
/usr/bin/install: setting permissions for `/usr/bin/mtp-files': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'hotplug' '/usr/bin/mtp-hotplug'
/usr/bin/install -c .libs/hotplug /usr/bin/mtp-hotplug
/usr/bin/install: setting permissions for `/usr/bin/mtp-hotplug': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'folders' '/usr/bin/mtp-folders'
/usr/bin/install -c .libs/folders /usr/bin/mtp-folders
/usr/bin/install: setting permissions for `/usr/bin/mtp-folders': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'trexist' '/usr/bin/mtp-trexist'
/usr/bin/install -c .libs/trexist /usr/bin/mtp-trexist
/usr/bin/install: setting permissions for `/usr/bin/mtp-trexist': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'playlists' '/usr/bin/mtp-playlists'
/usr/bin/install -c .libs/playlists /usr/bin/mtp-playlists
/usr/bin/install: setting permissions for `/usr/bin/mtp-playlists': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'getplaylist' '/usr/bin/mtp-getplaylist'
/usr/bin/install -c .libs/getplaylist /usr/bin/mtp-getplaylist
/usr/bin/install: setting permissions for `/usr/bin/mtp-getplaylist': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'format' '/usr/bin/mtp-format'
/usr/bin/install -c .libs/format /usr/bin/mtp-format
/usr/bin/install: setting permissions for `/usr/bin/mtp-format': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'albumart' '/usr/bin/mtp-albumart'
/usr/bin/install -c .libs/albumart /usr/bin/mtp-albumart
/usr/bin/install: setting permissions for `/usr/bin/mtp-albumart': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'albums' '/usr/bin/mtp-albums'
/usr/bin/install -c .libs/albums /usr/bin/mtp-albums
/usr/bin/install: setting permissions for `/usr/bin/mtp-albums': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'newplaylist' '/usr/bin/mtp-newplaylist'
/usr/bin/install -c .libs/newplaylist /usr/bin/mtp-newplaylist
/usr/bin/install: setting permissions for `/usr/bin/mtp-newplaylist': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'emptyfolders' '/usr/bin/mtp-emptyfolders'
/usr/bin/install -c .libs/emptyfolders /usr/bin/mtp-emptyfolders
/usr/bin/install: setting permissions for `/usr/bin/mtp-emptyfolders': No such file or directory
  /bin/bash ../libtool --mode=install /usr/bin/install -c 'thumb' '/usr/bin/mtp-thumb'
/usr/bin/install -c .libs/thumb /usr/bin/mtp-thumb
/usr/bin/install: setting permissions for `/usr/bin/mtp-thumb': No such file or directory
make  install-exec-hook
make[3]: Entering directory `/home/will/libmtp-0.1.3/examples'
ln -f -s mtp-connect /usr/bin/mtp-delfile
ln -f -s mtp-connect /usr/bin/mtp-getfile
ln -f -s mtp-connect /usr/bin/mtp-newfolder
ln -f -s mtp-connect /usr/bin/mtp-sendfile
ln -f -s mtp-connect /usr/bin/mtp-sendtr
make[3]: Leaving directory `/home/will/libmtp-0.1.3/examples'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/will/libmtp-0.1.3/examples'
make[1]: Leaving directory `/home/will/libmtp-0.1.3/examples'
Making install in doc
make[1]: Entering directory `/home/will/libmtp-0.1.3/doc'
doxygen
make[2]: Entering directory `/home/will/libmtp-0.1.3/doc'
make[2]: Nothing to be done for `install-exec-am'.
/usr/bin/install -c -d /usr/share/doc/libmtp-0.1.3/html
/usr/bin/install -c -m 644 html/* /usr/share/doc/libmtp-0.1.3/html
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/annotated.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/delfile_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/detect_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/dir_3267cc0b12a65a8ab69e21c9076a8754.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/dirs.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/doxygen.css': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/doxygen.png': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/examples_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/examples.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/files_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/files.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/folders_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/functions.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/functions_vars.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/getfile_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/getplaylist_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/globals_func.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/globals.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/globals_type.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/gphoto2-endian_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__albums.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__basic.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__files.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__folders.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__internals.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__objects.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__playlists.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__structar.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__tracks.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/group__types.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/hotplug_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/index.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/libmtp_8c.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/libmtp_8h.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/libmtp_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/libptp-stdint_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/libusb-glue_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/mainpage_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/modules.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/newfolder_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/playlists_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/ptp_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/refactortest_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/sendfile_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/sendtr_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__album__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__device__entry__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__devicestorage__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__filesampledata__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__file__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__folder__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__mtpdevice__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__playlist__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/structLIBMTP__track__struct.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/tab_b.gif': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/tab_l.gif': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/tab_r.gif': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/tabs.css': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/tracks_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/trexist_8c-example.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/unicode_8c.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/unicode_8h-source.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/util_8c.html': No such file or directory
/usr/bin/install: setting permissions for `/usr/share/doc/libmtp-0.1.3/html/util_8h-source.html': No such file or directory
make[2]: Leaving directory `/home/will/libmtp-0.1.3/doc'
make[1]: Leaving directory `/home/will/libmtp-0.1.3/doc'
make[1]: Entering directory `/home/will/libmtp-0.1.3'
make[2]: Entering directory `/home/will/libmtp-0.1.3'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/lib/pkgconfig" || mkdir -p -- "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 'libmtp.pc' '/usr/lib/pkgconfig/libmtp.pc'
/usr/bin/install: setting permissions for `/usr/lib/pkgconfig/libmtp.pc': No such file or directory
make[2]: Leaving directory `/home/will/libmtp-0.1.3'
make[1]: Leaving directory `/home/will/libmtp-0.1.3'

======================== Installation successful ==========================

Copying documentation directory...
./
./doc/
./doc/Doxyfile.in
./doc/Makefile.am
./doc/Doxyfile
./doc/Makefile.in
./doc/html/
./doc/html/index.html
./doc/html/group__tracks.html
./doc/html/doxygen.css
./doc/html/group__types.html
./doc/html/libptp-stdint_8h-source.html
./doc/html/structLIBMTP__filesampledata__struct.html
./doc/html/tabs.css
./doc/html/group__structar.html
./doc/html/structLIBMTP__folder__struct.html
./doc/html/functions.html
./doc/html/files.html
./doc/html/libmtp_8h-source.html
./doc/html/structLIBMTP__devicestorage__struct.html
./doc/html/examples_8h-source.html
./doc/html/group__internals.html
./doc/html/detect_8c-example.html
./doc/html/unicode_8c.html
./doc/html/util_8c.html
./doc/html/structLIBMTP__album__struct.html
./doc/html/trexist_8c-example.html
./doc/html/dir_3267cc0b12a65a8ab69e21c9076a8754.html
./doc/html/folders_8c-example.html
./doc/html/getfile_8c-example.html
./doc/html/newfolder_8c-example.html
./doc/html/gphoto2-endian_8h-source.html
./doc/html/tab_r.gif
./doc/html/hotplug_8c-example.html
./doc/html/util_8h-source.html
./doc/html/refactortest_8c-example.html
./doc/html/structLIBMTP__playlist__struct.html
./doc/html/libmtp_8c.html
./doc/html/globals_func.html
./doc/html/group__albums.html
./doc/html/functions_vars.html
./doc/html/structLIBMTP__track__struct.html
./doc/html/ptp_8h-source.html
./doc/html/tab_l.gif
./doc/html/group__basic.html
./doc/html/annotated.html
./doc/html/libusb-glue_8h-source.html
./doc/html/mainpage_8h-source.html
./doc/html/group__objects.html
./doc/html/tracks_8c-example.html
./doc/html/group__playlists.html
./doc/html/doxygen.png
./doc/html/unicode_8h-source.html
./doc/html/examples.html
./doc/html/group__folders.html
./doc/html/globals_type.html
./doc/html/structLIBMTP__mtpdevice__struct.html
./doc/html/libmtp_8h.html
./doc/html/structLIBMTP__device__entry__struct.html
./doc/html/playlists_8c-example.html
./doc/html/getplaylist_8c-example.html
./doc/html/tab_b.gif
./doc/html/delfile_8c-example.html
./doc/html/dirs.html
./doc/html/files_8c-example.html
./doc/html/group__files.html
./doc/html/structLIBMTP__file__struct.html
./doc/html/modules.html
./doc/html/globals.html
./doc/html/sendtr_8c-example.html
./doc/html/sendfile_8c-example.html
./doc/mainpage.h
./doc/latex/
./doc/latex/getplaylist_8c-example.tex
./doc/latex/getfile_8c-example.tex
./doc/latex/sendtr_8c-example.tex
./doc/latex/folders_8c-example.tex
./doc/latex/refactortest_8c-example.tex
./doc/latex/annotated.tex
./doc/latex/group__basic.tex
./doc/latex/libmtp_8c.tex
./doc/latex/structLIBMTP__mtpdevice__struct.tex
./doc/latex/group__albums.tex
./doc/latex/hotplug_8c-example.tex
./doc/latex/playlists_8c-example.tex
./doc/latex/delfile_8c-example.tex
./doc/latex/group__internals.tex
./doc/latex/modules.tex
./doc/latex/files.tex
./doc/latex/unicode_8c.tex
./doc/latex/doxygen.sty
./doc/latex/index.tex
./doc/latex/group__structar.tex
./doc/latex/trexist_8c-example.tex
./doc/latex/dirs.tex
./doc/latex/sendfile_8c-example.tex
./doc/latex/structLIBMTP__devicestorage__struct.tex
./doc/latex/util_8c.tex
./doc/latex/dir_3267cc0b12a65a8ab69e21c9076a8754.tex
./doc/latex/group__files.tex
./doc/latex/group__types.tex
./doc/latex/structLIBMTP__file__struct.tex
./doc/latex/group__tracks.tex
./doc/latex/tracks_8c-example.tex
./doc/latex/group__objects.tex
./doc/latex/examples.tex
./doc/latex/refman.tex
./doc/latex/files_8c-example.tex
./doc/latex/structLIBMTP__device__entry__struct.tex
./doc/latex/newfolder_8c-example.tex
./doc/latex/structLIBMTP__folder__struct.tex
./doc/latex/detect_8c-example.tex
./doc/latex/structLIBMTP__filesampledata__struct.tex
./doc/latex/FreeSans.ttf
./doc/latex/structLIBMTP__playlist__struct.tex
./doc/latex/group__playlists.tex
./doc/latex/group__folders.tex
./doc/latex/structLIBMTP__album__struct.tex
./doc/latex/libmtp_8h.tex
./doc/latex/structLIBMTP__track__struct.tex
./doc/latex/Makefile
./doc/examples.h
./doc/man/
./doc/man/man3/
./doc/man/man3/folders.3
./doc/man/man3/objects.3
./doc/man/man3/tracks.3
./doc/man/man3/types.3
./doc/man/man3/libmtp.h.3
./doc/man/man3/LIBMTP_track_struct.3
./doc/man/man3/util.c.3
./doc/man/man3/LIBMTP_folder_struct.3
./doc/man/man3/files.3
./doc/man/man3/LIBMTP_filesampledata_struct.3
./doc/man/man3/unicode.c.3
./doc/man/man3/LIBMTP_mtpdevice_struct.3
./doc/man/man3/LIBMTP_devicestorage_struct.3
./doc/man/man3/LIBMTP_album_struct.3
./doc/man/man3/LIBMTP_device_entry_struct.3
./doc/man/man3/LIBMTP_file_struct.3
./doc/man/man3/playlists.3
./doc/man/man3/basic.3
./doc/man/man3/albums.3
./doc/man/man3/internals.3
./doc/man/man3/structar.3
./doc/man/man3/_home_will_libmtp-0.1.3_src_.3
./doc/man/man3/libmtp.c.3
./doc/man/man3/LIBMTP_playlist_struct.3
./doc/Makefile
./ChangeLog
./INSTALL
./README.windows.txt
./AUTHORS
./README
./COPYING
./TODO


[quote=dpkg error log]
Selecting previously deselected package libmtp.
(Reading database ... 121844 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/will/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb (--instal
l):
 trying to overwrite `/usr/bin/gcc', which is also in package gcc
Errors were encountered while processing:
 /home/will/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
[/quote]

---

### Post by heyilikeyoursweater on 2007-01-26
I am hopelessly lost... This thread has 40 pages! If anybody can please help me...

---

### Post by Flatwinder on 2007-01-28
Many thanks msak007!!!

Thanks to your great post of instructions that even a newbie like me could follow my Vision M is now working with Ubuntu 6.10 LTS. FANTASTIC!!! I can't thank you enough for removing the last dependency I had for XP.

So GOODBYE, Bill.

NO MORE MICROSOFT for me!  YIPPPPEEEE!!!!

NEVER GOING BACK!!! And Ubuntu is Soooooooo much faster. I love it!

Thanks again and again!!!,

Jim

---

### Post by Flatwinder on 2007-01-28
> **heyilikeyoursweater said:**
> I am hopelessly lost... This thread has 40 pages! If anybody can please help me...



If you follow the detailed step-by-step instructions posted by msak007  I bet you'll have it working in no time. I was having a rough time of it too with my Vision M but thanks to his instructions it's working great now. Hope it helps you as much as it did me. Good luck.

Jim

---

### Post by bsalt on 2007-01-29
Just a heads up, I tried installing gnomad 2.8.10 the easy way (the first option), and it appears it doesn't like the version of libmtp2 in the **EDGY** repo's. So it looks like if people will use gnomad 2.8.10, they must compile libmtp 0.1.13 and compile gnomad 2.8.10 (the second option)

---

### Post by bsalt on 2007-01-30
What are the odds there could be a "Synchronize" button, where a folder and/or sub folders on the computer HDD are all considered a "library" and the list of files is updated and saved to an .xml or .txt file, or whatever type of file. And then the file compares itself to the jukebox, and whatever is missing will be added, and whatever was off will be updated. Is that possible?

---

### Post by ntetreau on 2007-01-30
The odds are good I believe, take a look at this:
[http://www.adebenham.com/mtpsync/](http://www.adebenham.com/mtpsync/)

Let us know if it works well for you.

Nic

---

### Post by oleost on 2007-01-30
Thanx, worked first time, used the compiling from source method, but not using the checkinstall function since I didnt bother to find a source that had it, Im using debian.

---

### Post by bsalt on 2007-01-30
> **ntetreau said:**
> The odds are good I believe, take a look at this:
[http://www.adebenham.com/mtpsync/](http://www.adebenham.com/mtpsync/)

Let us know if it works well for you.

Nic

Thanks, Nic, I'm checking it out now.

---

### Post by NetMatrix on 2007-01-30
Hello all,


    Let me apologize in advance if this is already in here somewhere but I've searched the thread and didn't find it.  Ok here it goes..  followed all the instructions... great how-to :D !!!  but here is what I get in /var/log/messages when I connect the device.  I am trying to use a Zen V.

usb 4-4: new high speed USB device using ehci_hcd and address 8
usb 4-4: configuration #1 chosen from 1 choice

and when running gnomad:

usbfs: process 10594 (gnomad2) did not claim interface 0 before use

    and gnomad says "no jukebox devices found" or something like that.  I've been scouring the internet for a while and no real clue as to what I've missed.

Here is the verification of my installed versions.

$ dpkg -s gnomad2
Package: gnomad2
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 660
Maintainer: root@codemachine
Architecture: i386
Version: 2.8.10-1
Description: gnomad

$ dpkg -s libmtp
Package: libmtp
Status: install ok installed
Priority: extra
Section: checkinstall
Installed-Size: 908
Maintainer: root@codemachine
Architecture: i386
Version: 0.1.3-1
Description: Package created with checkinstall 1.6.0

$ dpkg -s libnjb1
Package: libnjb1
Status: purge ok not-installed
Priority: optional
Section: libs

$ dpkg -s libnjb-dev
Package: libnjb-dev
Status: install ok installed
Priority: optional
Section: libdevel
Installed-Size: 312
Maintainer: John Bovey <jdb@kent.ac.uk>
Architecture: i386
Source: libnjb
Version: 2.2.5-4.1ubuntu1
Depends: libnjb5 (= 2.2.5-4.1ubuntu1), libusb-dev (>> 0.1.7)
Description: Creative Labs Nomad Jukebox library development files
 A library for communicating with the Creative Nomad Jukebox MP3
 player. More information can be found at the libnjb web site:
 [http://sf.net/projects/libnjb/](http://sf.net/projects/libnjb/)
 This package contains the headers and development libraries.

    Info from /dev/bus/usb/devices:

T:  Bus=04 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=4150 Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative Zen V
S:  SerialNumber=F985860E0002FAA9
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=1ms

    Info from lsusb:

Bus 004 Device 008: ID 041e:4150 Creative Technology, Ltd 


   Any suggestions will be welcomed... I don't have any XP machines so I'm hoping I didn't spend all this money for nothing.

---

### Post by bsalt on 2007-01-31
> **ntetreau said:**
> The odds are good I believe, take a look at this:
[http://www.adebenham.com/mtpsync/](http://www.adebenham.com/mtpsync/)

Let us know if it works well for you.

Nic

Ok, so I installed the program - and it looks nice! I tried to connect to my mp3 player with different versions of libmtp, and each time, it had a segfault when trying to read the files on my player. I even reformatted my jukebox to no avail. I guess I'll have to wait for a newer release.

---

### Post by Minyaliel on 2007-01-31
I managed to install it, but...

"Found non-autodetected device "Creative Zen V" on USB bus...
usb_claim_interface(): Operation not permitted
Connection error
PDE device NULL"

What do I do?

---

### Post by NetMatrix on 2007-02-01
Attempted to sync the Zen V in Winblows XP with no luck... Zen V is going back to the store... please disregard my previous post.

---

### Post by bsalt on 2007-02-01
> **NetMatrix said:**
> Attempted to sync the Zen V in Winblows XP with no luck... Zen V is going back to the store... please disregard my previous post.

Before you do, are you **absolutely sure** the firmware on your jukebox is the MTP PlaysForSure? If not, I would guess you would have a harder time connecting in XP without the Creative software. In Ubuntu, however it *is* easier and faster.

---

### Post by shadowfx78 on 2007-02-01
ok i just got a Zen V Plus and have tried to configure it the first 2 ways and i get through the libmtp no problem but when it comes to doing gnomad i get this

jukebox.c:130: error: &#8216;LIBMTP_FILETYPE_AAC&#8217; undeclared here (not in a function)
jukebox.c:131: error: &#8216;LIBMTP_FILETYPE_FLAC&#8217; undeclared here (not in a function)
jukebox.c:132: error: &#8216;LIBMTP_FILETYPE_MP2&#8217; undeclared here (not in a function)
jukebox.c:133: error: &#8216;LIBMTP_FILETYPE_M4A&#8217; undeclared here (not in a function)
jukebox.c:134: error: &#8216;LIBMTP_FILETYPE_DOC&#8217; undeclared here (not in a function)
jukebox.c:135: error: &#8216;LIBMTP_FILETYPE_XML&#8217; undeclared here (not in a function)
jukebox.c:136: error: &#8216;LIBMTP_FILETYPE_XLS&#8217; undeclared here (not in a function)
jukebox.c:137: error: &#8216;LIBMTP_FILETYPE_PPT&#8217; undeclared here (not in a function)
jukebox.c:138: error: &#8216;LIBMTP_FILETYPE_MHT&#8217; undeclared here (not in a function)
jukebox.c:139: error: &#8216;LIBMTP_FILETYPE_JP2&#8217; undeclared here (not in a function)
jukebox.c:140: error: &#8216;LIBMTP_FILETYPE_JPX&#8217; undeclared here (not in a function)
jukebox.c: In function &#8216;flush_usage&#8217;:
jukebox.c:1152: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1153: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1153: error: &#8216;mtp_filetype_description_t&#8217; has no member named &#8216;MaxCapacity&#8217;
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1154: error: &#8216;mtp_filetype_description_t&#8217; has no member named &#8216;FreeSpaceInBytes&#8217;
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function &#8216;scan_thread&#8217;:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/ryan/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

---

### Post by ubunter1 on 2007-02-01
ive been using it for a bit now but has anyone been able to transfer whole folders into your player and not just individual files only?.it takes me a while but still works.im also fearful that if i install the new gnomad that it may not work as before.thanks.

---

### Post by ButteBlues on 2007-02-01
> **ubunter1 said:**
> ive been using it for a bit now but has anyone been able to transfer whole folders into your player and not just individual files only?.it takes me a while but still works.im also fearful that if i install the new gnomad that it may not work as before.thanks.
It's a preference.

Recursive something or other. =)

---

### Post by bsalt on 2007-02-01
> **ubunter1 said:**
> ive been using it for a bit now but has anyone been able to transfer whole folders into your player and not just individual files only?.it takes me a while but still works.im also fearful that if i install the new gnomad that it may not work as before.thanks.

Yeah, if you tell it to scan folders recursively or something, it'll do the trick - I'm in the same boat as you, I've got 250 something folders in my library... and this saves *lotsa* time.

---

### Post by ubunter1 on 2007-02-01
that worked thanks alot.rob.:D

---

### Post by shadowfx78 on 2007-02-02
well i got things working on edgy even easier than all those instructions so if anyone wants to know bout them let me know.

---

### Post by NetMatrix on 2007-02-02
> Posted by bsalt:
Before you do, are you absolutely sure the firmware on your jukebox is the MTP PlaysForSure? If not, I would guess you would have a harder time connecting in XP without the Creative software. In Ubuntu, however it is easier and faster.

Problem is I attempted to upgrade the firmware in XP, but because the system couldn't see the device it couldn't update the firmware.  Thanks though.  I think it was an issue with the device itself.

---

### Post by bsalt on 2007-02-02
Hey, real quick... if I had installed gnomad2 using "sudo make install" rather than checkinstall, what would be the best way for me to remove the app if I no longer want it?

---

### Post by NetMatrix on 2007-02-02
I think you have to take it out piece by piece, but I'm not sure.

---

### Post by ravemjr on 2007-02-02
> **shadowfx78 said:**
> well i got things working on edgy even easier than all those instructions so if anyone wants to know bout them let me know.

I'd like to know it, I just got one too (4GB) and got it working but doesnt detect it. Says no devices found on USB Hub.
I then tried re-doing the steps carefully (I did the initial purging this time), but then I got that same error...so can you please help me, and anyone who might be in the same situation?

---

### Post by ntetreau on 2007-02-02
bsalt, you can try sudo make uninstall and see if that works.  You could also try to install it again with sudo checkinstall (it will reinstall the same files), then sudo aptitute purge gnomad2 will remove it.

Nic

---

### Post by shadowfx78 on 2007-02-02
this was posted on the kubuntu forums by rodneyck and oddly enough the solution is actually from this forum go figure.  these instructions are for kubuntu and amarok so i dont know if they will work for gnomad.

[http://ubuntuforums.org/showpost.php?p=2031283&postcount=18](http://ubuntuforums.org/showpost.php?p=2031283&postcount=18)

Unzip and follow the directories of the zip to place the files in the appropriate folders. Then reboot your computer, plug in and turn on your zen and the MTP option should be present in Amarok. I have a Creative Zen btw and this was the only thing that worked for me.

God Speed and Good luck

---

### Post by AGM on 2007-02-03
> **shadowfx78 said:**
> ok i just got a Zen V Plus and have tried to configure it the first 2 ways and i get through the libmtp no problem but when it comes to doing gnomad i get this

jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/ryan/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.


Hi, I am an italian user and I have the same problem.

```
Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/anton/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/anton/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

Please, help me.

Thanks

---

### Post by ravemjr on 2007-02-03
Thanks for the reply shadow, but I'm using gnome, so I don't think i can use amaroK...
It seems it's not impossible, since I've read somewhere that people got their same mp3 player working with THIS same tutorial. Any ideas?

---

### Post by shadowfx78 on 2007-02-03
You can use amarok just install it from synaptic the only thing it requires is the kdelibs so that shouldnt really matter.

AGM i posted a solution for Amarok on Kubuntu i dont know if it pertains to you but cant hurt to try.

---

### Post by BatPenguin on 2007-02-03
Hey AGM and everybody else with these problems: 

> **AGM said:**
> ```
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/anton/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

I was getting the same error messages trying to run make when using the repos. I solved this simply by doing it the other way (compiling BOTH libmtp and gnomad). Somebody earlier in the forums mentioned that gnomad has problems with the version of libmtp in the repos. So just try compiling both. This solved it for me, works fine now (using Zen V Plus). Hope this helps!

---

### Post by ravemjr on 2007-02-03
Dang...I've a V plus too but when I tried compiling both, this happened:
```
Making all in src
make[1]: Entering directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/src'
Making all in doc
make[1]: Entering directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/doc'
Making all in po
make[1]: Entering directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/po'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10/po'
make[1]: Entering directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10'
LC_ALL=C ./intltool-merge -d -u -c ./po/.intltool-merge-cache ./po gnomad2.desktop.in gnomad2.desktop
Found cached translation database
Merging translations into gnomad2.desktop.
make[1]: Leaving directory `/home/ravemjr/gnomad_install/gnomad2-2.8.10'

```

I also noticed several times that the dbus-Glib was present on the several outputs...but it seems  it wasnt used during the configuration of gnomad...

---

### Post by bsalt on 2007-02-03
I know that when I first tried to install gnomad 2.8.10, I was using libmtp2 from the repo's. But when I installed with libmtp 0.1.3, it was very smooth as an install. But that is just me.

---

### Post by hodad on 2007-02-05
Is Gnomad capable of downloading podcasts to my Creative Zen V?  I don't see anything in Gnomad2 setup that allows one to go to a website and download a podcast.   Maybe this is a multi-part problem, as I cannot even get podcasts to work on the pc itself (using Firefox).  Maybe the new version has the capability?

---

### Post by hodad on 2007-02-05
Just solved one of the above listed problems:  I looked under Applications - Sound and Video  and found Volume control, which I had looked at before, but hadn't noticed that the little speaker icon had a red line through it; clicked on it and, Voila!

Still have the problem of not being able to transfer podcasts to the Creative Zen, though.

---

### Post by davor on 2007-02-06
I'm also getting this message, when I try to compile gnomad from sources. I have read every page on this thread and tried both installing everything from source, and using the repository, but I keep getting the same error message.

```
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’

```

Thanks for your help!

EDIT: I solved this by typing make install in the libmtp-folder, instead of running "make checkinstall". Everything is working fine. Thanks alot!

Truly yours,
Davor Babic

---

### Post by EnigmaticSeraph on 2007-02-08
After wrestling with this since December, I'm getting very tired.  I have a Creative Zen V (2G) player and it just doesn't work.  I'm running Feisty now, but it didn't work in Edgy way back when.  I'm using libmtp 0.1.3 this go around and have installed Gnomad 2.8.10 from source.  No, I have no repository versions of any of the required packages installed, so it's not a conflict issue.  The libmtp rules list my player as well.  I do have libnjb5 installed, but I don't think that makes a difference, seeing as how none of the files are called in a trace.  As for the problem, I get the "No jukeboxes found" message after Gnomad lags for a long time.  I've run in both as root and myself, so it's not a permission issue, it seems.  I get no reading off of the device from lsusb, so it's quite possibly a libmtp issue.  I've scoured this thread and the documentation and can't find what the blazes is going on.  I know other people have had these symptoms, but there's never seemed to be any resolution given. Any suggestions?  I'm all ears...

---

### Post by ButteBlues on 2007-02-08
> **EnigmaticSeraph said:**
> After wrestling with this since December, I'm getting very tired.  I have a Creative Zen V (2G) player and it just doesn't work.  I'm running Feisty now, but it didn't work in Edgy way back when.  I'm using libmtp 0.1.3 this go around and have installed Gnomad 2.8.10 from source.  No, I have no repository versions of any of the required packages installed, so it's not a conflict issue.  The libmtp rules list my player as well.  I do have libnjb5 installed, but I don't think that makes a difference, seeing as how none of the files are called in a trace.  As for the problem, I get the "No jukeboxes found" message after Gnomad lags for a long time.  I've run in both as root and myself, so it's not a permission issue, it seems.  I get no reading off of the device from lsusb, so it's quite possibly a libmtp issue.  I've scoured this thread and the documentation and can't find what the blazes is going on.  I know other people have had these symptoms, but there's never seemed to be any resolution given. Any suggestions?  I'm all ears...
The 1G version works fine here.

---

### Post by shadowfx78 on 2007-02-09
EnigmaticSeraph, are you running Ubuntu or Kubuntu?  I found a way to make it work in Kubuntu if thats what your running.

---

### Post by EnigmaticSeraph on 2007-02-09
Nope, running under Ubuntu.  Were you suggesting Amarok?  I mean, I could simply use it with the KDE libraries, but I'd rather not.  The problem doesn't seem to be with Gnomad, though...

---

### Post by ntetreau on 2007-02-11
EnigmaticSeraph:  Have you tried your player in windows?  Does it work well there?  You might want to make sure you are using the latest firmware as well.  If it works under windows and not under libmtp, I would suggest heading to the libmtp discussion forum and posting there.  There are very responsive.

Nic

---

### Post by flugheim on 2007-02-11
Hi, i cant get gnomad2 to see my Zen Microphoto, even if i run it as root..
Ive tried both to compile all from source and to use the repo install (as described in the first post in this thread).
Im running edgy.
Would be nice to could use my mp3 player with ubuntu :)

Update:
I get this when running from shell (both as root and normal user):
flugheim@flugheim-laptop:~$ gnomad2 
PDE device NULL.

---

### Post by ntetreau on 2007-02-11
Hi flugheim,
can you try to run mtp-detect or and let us know hte output?

Nic

---

### Post by flugheim on 2007-02-11
Here we go:

> 
flugheim@flugheim-laptop:~$ mtp-detect
Found non-autodetected device "Creative Zen MicroPhoto" on USB bus...
PTP: Opening session
Could not open session! (Return code 767)
  Try to reset the device.
Could not get device info!
Connection error.
No devices.



after restart of device:
PTP: Opening session
PTP: Closing session

Update2:
now this comes up:[http://pastebin.ca/350563](http://pastebin.ca/350563)

---

### Post by forcesofhabit on 2007-02-12
I'm getting the same error as davor... it was working fine on my laptop using this method.
Anyone know how to solve this problem?

---

### Post by iSE on 2007-02-13
Since I have the newer Creative Zen Vision:M 60Gb, I thought it probably best to do method 2 to make sure my player is supported with Gnomad2. Does anyone know if it is or not at all?

Anywayz... Upon running ./configure I ran into a problem...
```
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I've tried uninstalling libnjb and reinstalling, and gtk+-2.0 i KNOW i have. However I have been having a few problems getting a gtk2 theme running recently so it may be related. All and any help is GREATLY appreciated.

iSE

---

### Post by ntetreau on 2007-02-13
Hi iSE,
remember that when a configure script complains about something missing, it usually wants the development packages, in your case gtk+-dev and libnjb-dev for example.  You can search for them in synaptic.

Nic

---

### Post by ntetreau on 2007-02-13
flugheim:  Since mtp-detect works, does the rest of gnomad2 works?

forcesofhabit:  davor fixed his problem running sudo make install instead of sudo checkinstall, did you try it?

Nic

---

### Post by Roeler on 2007-02-13
Is it possible to make my creative zen touch work again with amarok after the firmware upgrade ?

---

### Post by msak007 on 2007-02-13
**flugheim** - If I'm not mistaken, I've seen the errors you're getting before and others have resolved them by formatting their player. If you dual-boot Windows, can you test it there to see if it's detected and you can transfer files to it?

**iSE** - As Nic already mentioned, you need the dev packages for gtk and libnjb. If you followed method 2, copying / pasting everything in the instructions should have given you all the packages you need.

**Nic** - I read Davor's post, and it seems his problem was that he typed "*make* checkinstall" instead of just "checkinstall" - that's why he got the error, so he tried "make install" and it worked.

**Roeler** - If you had a player that worked with Amarok before, then after the firwmare upgrade it no longer works, you most likely upgraded to a version of the firmware that makes it an MTP MP3 player. You can get Amarok to work, but it will require recompiling it from source to make it MTP compatible (just like we're doing here with Gnomad). The version of Amarok in the Feisty repos comes with MTP already compiled / enabled.

---

### Post by flugheim on 2007-02-14
ntetreau: yes it does. (I havent discovered anything abnornal atleast)

msak007: Ive already checked, it is detected i windows. I can try to format my player, and see whats happends then

Update: Ive formated the player it didint do it for me.. actually i discovered that it almost every timei connect it to windows the player stops working and i need to take out the battery to restart it..

---

### Post by iSE on 2007-02-14
I followed the instructions as per Method 2, doing everything that it says exactly as it says. I've just done a search for the libnjb-dev package, I have libnjb5 and libnjb5-dev, both of which are version: 2.2.5-4.1ubuntu1.

As for gtk+-dev i could not find any such reference in Synaptic Package Manager. A search for gtk and dev found libgtk2.0-dev which is version 2.10.6-0ubuntu3.1. Even after reinstalling both of these packages I get the same error.

Thankyou for your comments, your help is appreciated. I'm new to Linux, though I'm pretty much an expert on Windows systems. Microsoft ruined the chance they had with Vista (DRM-wise esp) so now I'm givin Linux the best chance it can. I hope to learn as much as I can so i too can help in the future. Any advice (links etc) you can give me on learning how things work in Linux as opposed to Windows would v much be appreciated also.

iSE

---

### Post by msak007 on 2007-02-14
> **iSE said:**
> I followed the instructions as per Method 2, doing everything that it says exactly as it says. I've just done a search for the libnjb-dev package, I have libnjb5 and libnjb5-dev, both of which are version: 2.2.5-4.1ubuntu1.

As for gtk+-dev i could not find any such reference in Synaptic Package Manager. A search for gtk and dev found libgtk2.0-dev which is version 2.10.6-0ubuntu3.1. Even after reinstalling both of these packages I get the same error.

Thankyou for your comments, your help is appreciated. I'm new to Linux, though I'm pretty much an expert on Windows systems. Microsoft ruined the chance they had with Vista (DRM-wise esp) so now I'm givin Linux the best chance it can. I hope to learn as much as I can so i too can help in the future. Any advice (links etc) you can give me on learning how things work in Linux as opposed to Windows would v much be appreciated also.

iSE
First of all welcome, and sorry I should've been a little more clear on the package names - I assumed that you wouldn't need the exact package names since you're copying / pasting. They are indeed libnjb-dev and libgtk2.0-dev, and installing them shouldn't give you the errors you were getting before. Could you post the output of ./configure again? Maybe now that you have those packages, it's getting hung on another dependency.

As far as learning Linux, I've been using it for a little over a year after jumping ship and I'm still learning. It takes time and patience after doing things for so long in Windows. I left M$ way before Vista was launched and before I knew of any DRM schemes they planned to include. My primary motivation was that I was getting sick of all the activation, registration, re-activation, etc., schemes that M$ was putting its customers through to do anything (updates, downloads, installs, etc.). Now that I'm here, I'd never go back even if all that was removed because I know so much more about Open Source / free software and the ethics and ideology behind it. I can PM you later with some links to resources that'll help you out.

---

### Post by ntetreau on 2007-02-15
flugheim:  It seems from your post that either your creative player is defective or your keyboard is!!!

Nic

---

### Post by flugheim on 2007-02-15
I think my player is too :S
(It wasent my keyboard that was broken, only my eyes that read it)
Well thanks for the help :)

---

### Post by iSE on 2007-02-15
Ok, i keep trying and even after i KNOW i had those two packages installed in the first place, yet i still get the following error. Be advised ppl, those not interested get the scrollin fingers to the ready!

```
ise@isemachine:~/gnomad_install/gnomad2-2.8.10$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for pkg-config... /usr/local/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Yet as stated in my previous posts I know I have both of these. And installing the dependencies at the beginning went fine. No problems reported until I run ./configure in the gnomad source folder. I've tried redownloading that also to no avail. Everything is correct according to the instructions at this point. Im thinking about switching to Kubuntu anywayz. Also been having problems with Beryl which Im sure is related to this gtk+-2.0 problem.

If you could PM me msak007 that would be cool thanx. Anyone else with advice is also welcome to PM me.

iSE

---

### Post by EnigmaticSeraph on 2007-02-15
I have returned from my trek over to the libmtp forums.  The fault was not in libmtp, but rather that annoying USB 2.0 issue with certain architectures.  I posted the answer here, in case anyone else has trouble with this:

[https://sourceforge.net/forum/forum.php?thread_id=1671897&forum_id=535191](https://sourceforge.net/forum/forum.php?thread_id=1671897&forum_id=535191) 

Anyway, I have a NEW problem now.  I can access my Zen V and delete files from it, transfer files from it, and whatnot, but I can't access my music folder.  What's happening is that I'll click on my music folder to browse through it so that I can transfer music, and Gnomad will start reading the metadata and then crash with a Segmentation fault at some arbitrary point.  It's not a specific file and the amount of files it gets through before crashing also seems nonspecific.  It also doesn't seem to have anything to do with the Preference options, as I've unset and set them in many,  many combinations and the crash still occurs.  Here's the tail of the -D15 output:

> Getting metadata for: Alexander Pires & Gloria Estefan - Santo Santo.mp3 (27/158)
Getting ID3 info for: Alexander Pires & Gloria Estefan - Santo Santo.mp3
entered mp3file_get_info()
entered get_mp3_info()
Getting info from path...
Processing path: /home/alex/My Music/Alexander Pires & Gloria Estefan - Santo Santo.mp3
Dir: My Music
File: Alexander Pires & Gloria Estefan - Santo Santo
get_artist()
get_title()
get_album()
get_trackno()
Got all info from path...

---- Song metadata -----
Artist:    Alexander Pires & Gloria Estefan
Title:     Alexander Pires & Gloria Estefan - Santo Santo
Album:     (null)
Year:      0
Genre:     (null)
Length:    4:12
Size:      4324933 bytes
Codec:     MP3
Track#:    0
Protected: NO
Filename:  (null)
Path:      /home/alex/My Music/Alexander Pires & Gloria Estefan - Santo Santo.mp3
Folder:    (null)
Getting metadata for: changetheworld_english.mp3 (28/158)
Getting ID3 info for: changetheworld_english.mp3
entered mp3file_get_info()
entered get_mp3_info()
Segmentation fault (core dumped)

It consistently fails at the get_mp3_info() part.  Is anyone here a Gnomad dev?

---

### Post by corq on 2007-02-17
msak007...just wanted to thank you for the detail you put into this, including the anticipated output results...these are the things I consider so spooky when compiling stuff that as a neophyte I typically will avoid doing.

Thanks for your time and effort in writing this up. It is much appreciated.

---

### Post by msak007 on 2007-02-18
> **EnigmaticSeraph said:**
> I have returned from my trek over to the libmtp forums.  The fault was not in libmtp, but rather that annoying USB 2.0 issue with certain architectures.  I posted the answer here, in case anyone else has trouble with this:

[https://sourceforge.net/forum/forum.php?thread_id=1671897&forum_id=535191](https://sourceforge.net/forum/forum.php?thread_id=1671897&forum_id=535191) 

Anyway, I have a NEW problem now.  I can access my Zen V and delete files from it, transfer files from it, and whatnot, but I can't access my music folder.  What's happening is that I'll click on my music folder to browse through it so that I can transfer music, and Gnomad will start reading the metadata and then crash with a Segmentation fault at some arbitrary point.  It's not a specific file and the amount of files it gets through before crashing also seems nonspecific.  It also doesn't seem to have anything to do with the Preference options, as I've unset and set them in many,  many combinations and the crash still occurs.  Here's the tail of the -D15 output:



It consistently fails at the get_mp3_info() part.  Is anyone here a Gnomad dev?
Sorry to hear that you're still having so many problems. I had no idea USB 2.0 was a problem, so thanks for that info. BTW what archs is it a problem on? 

Regarding the Gnomad dev question, unfortunately I am not and I don't think anyone here is. You had good luck on the  libmtp forums, you may want to try the Gnomad forums. One of the libmtp devs (Linus Walleij) is also a Gnomad dev and assigns a majority of the bugs to himself. You can try the Gnomad forums and possibly file a bug report there if you think it is the app at fault. If your music library on the device is not too extensive, I would recommend formatting the device first and then trying to transfer maybe 1 or 2 tracks to test it. It could be hanging on a particular track, as I've seen that in the past. Good luck and keep us posted.

**corq** - Thanks for letting me know it worked for you. I think it's always easier to walk someone through something if you tell them what they should be seeing as output. At least that way the person can determine if they are on the right path based on their output and if it matches what's expected.

---

### Post by EnigmaticSeraph on 2007-02-19
I'm not sure of the architectures and I can't find the original bug, but here is one that is derived from it:  [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/49367)
I'll try the Gnomad forums.  Thank you.  I actually managed to get it somewhat working by wading through its crashes and moving over entire folders that I wanted by linking them elsewhere and selecting them to be iterated through.  By scanning large amounts of metadata, it'll crash.  No matter if it's been a while scanning or not, it seems that it'll simply crash when posed with a large amount, be it near the beginning of scanning or near the end.  If you keep going, though, it eventually scans all of the metadata and keeps it cached.  It is possible that a few specific tracks could be crashing this.  I have some free time now, so I'll fiddle around to see if that is the problem before going to the other forums.

---

### Post by tuxedobuford on 2007-02-20
Here's my output from make

buford@satellite:~/gnomad_install/gnomad2-2.8.10$ make
Making all in src
make[1]: Entering directory `/home/buford/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSIO
N=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://s
ourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gno
mad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STA
T_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -
DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT
_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMA
IN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDI
R=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H
=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I.
-pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-
2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/us
r/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDA
TADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/loca
l/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o
 jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/juk
ebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapa                             city’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpa                             ceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/buford/gnomad_install/gnomad2-2.8.10/src'
make: *** [all-recursive] Error 1
buford@satellite:~/gnomad_install/gnomad2-2.8.10$

Does anyone have any idea why this is happening?

Thanks!

---

### Post by macogw on 2007-02-22
I got Gnomad2 installed from source (to get the newer version than in repos) following [http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250) that HowTo, and I editted /etc/udev/rules.d/45-libnjb.rules to include my mp3 player.  I'm getting the 
PDE device NULL
error when I run Gnomad2 though.  I did mtp-detect and it detected my mp3 player just fine and spit out a whole load of stuff about what formats it supports and everything.  Now, I'm using Feisty, but since I used the same versions (libmtp-0.1.3 and gnomad-2.8.10)as listed in the HowTo I don't think Feisty is part of the problem.  My mp3 player also shows on lsusb (which it had to for me to be able to edit that file to include it, so I guess I don't have to mention this).  Does anyone have any idea why Gnomad2 says it's not there but everything else sees it?

---

### Post by Wartooth on 2007-02-24
I only got as far as attempting to untar the files and wound up getting these errors:

> tar -zxvf libmtp-0.1.3.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
xxxxx@wartooth:~/gnomad_install$ tar -zxvf libnjb-2.2.5.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
xxxxx@wartooth:~/gnomad_install$ tar -zxvf libmtp-0.1.3.tar.gz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors


???  

I tried using the archive manager as well.  What have I done wrong?

---

### Post by toasterofirony on 2007-02-26
> **tuxedobuford said:**
> Here's my output from make

*snip*
jukebox.c:130: error: &#8216;LIBMTP_FILETYPE_AAC&#8217; undeclared here (not in a function)
jukebox.c:131: error: &#8216;LIBMTP_FILETYPE_FLAC&#8217; undeclared here (not in a function)
jukebox.c:132: error: &#8216;LIBMTP_FILETYPE_MP2&#8217; undeclared here (not in a function)
jukebox.c:133: error: &#8216;LIBMTP_FILETYPE_M4A&#8217; undeclared here (not in a function)
jukebox.c:134: error: &#8216;LIBMTP_FILETYPE_DOC&#8217; undeclared here (not in a function)
jukebox.c:135: error: &#8216;LIBMTP_FILETYPE_XML&#8217; undeclared here (not in a function)
jukebox.c:136: error: &#8216;LIBMTP_FILETYPE_XLS&#8217; undeclared here (not in a function)
jukebox.c:137: error: &#8216;LIBMTP_FILETYPE_PPT&#8217; undeclared here (not in a function)
jukebox.c:138: error: &#8216;LIBMTP_FILETYPE_MHT&#8217; undeclared here (not in a function)
jukebox.c:139: error: &#8216;LIBMTP_FILETYPE_JP2&#8217; undeclared here (not in a function)
jukebox.c:140: error: &#8216;LIBMTP_FILETYPE_JPX&#8217; undeclared here (not in a function)
jukebox.c: In function &#8216;flush_usage&#8217;:
jukebox.c:1152: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1153: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1153: error: &#8216;mtp_filetype_description_t&#8217; has no member named &#8216;MaxCapacity&#8217;
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: &#8216;LIBMTP_mtpdevice_t&#8217; has no member named &#8216;storage&#8217;
jukebox.c:1154: error: &#8216;mtp_filetype_description_t&#8217; has no member named &#8216;FreeSpaceInBytes&#8217;
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function &#8216;scan_thread&#8217;:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/buford/gnomad_install/gnomad2-2.8.10/src'
make: *** [all-recursive] Error 1
buford@satellite:~/gnomad_install/gnomad2-2.8.10$

Does anyone have any idea why this is happening?

Thanks!

This is pretty much what just happened to me and I think, though not sure, that it has something to do with having litmtp2 *not* libmtp in the repo - even though with libmtp2 I can mtp-detect my Creative Zen:M, yet Gnomad2 can't see it.

Anyone add some clarity on this one? And if that is the case, how do we get it working again?

[edit] So I checked out the Amarok side of things and the thread in UF quotes the libmtp2 as being a problem for it, too. It's annoying, as I really don't want to start mucking around with effectively downgrading my libmtp and risk borking something else.

I gotta say, peeps, it's making me wish I'd bought an iPod after all :\

---

### Post by Xhosa on 2007-02-26
If you get the errors on make like:

```
*snip*
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
*snip*
```

Follow the 'build from source' instructions - turns out the libmtp supplied with Edgy can cause problems with the Gnomad build and you need libmtp 0.1.3 for it to work.

Also a minor issue I found, I needed to run ./configure --prefix=/usr for both libmtp and gnomad2 else it failed trying to install to the wrong path...

---

### Post by toasterofirony on 2007-02-26
But does that necessitate remove/ purging libmtp2 or can I install it along side?

---

### Post by macogw on 2007-02-26
> **toasterofirony said:**
> This is pretty much what just happened to me and I think, though not sure, that it has something to do with having litmtp2 *not* libmtp in the repo - even though with libmtp2 I can mtp-detect my Creative Zen:M, yet Gnomad2 can't see it.


Same problem here with a ZVM

---

### Post by ntetreau on 2007-02-27
Hi guys, I'm not sure which method of installation you are using but since you are having problems, why not try to purge libmtp you installed from the repositories and compile it instad.  If so, make sure your remove the -dev package as well.

Nic

---

### Post by PsychedelicReaction on 2007-02-27
Hi all. i got a Zen Touch 20 Gb, filled with 16Gb of music and last MTP firmware, is it normal that gnomad2 takes about 5 minutes to build the library every time?

---

### Post by toasterofirony on 2007-02-27
> **ntetreau said:**
> Hi guys, I'm not sure which method of installation you are using but since you are having problems, why not try to purge libmtp you installed from the repositories and compile it instad.  If so, make sure your remove the -dev package as well.

Nic

But this it just it; will getting rid of libmtp2 in favour of libmtp bork anything? 'cause now I have my system stabilised, I'm really not eager to do something that will require a week of fixing stuff because I got clever and buggered up my libs.

---

### Post by Murwiz on 2007-02-27
Hi, I hope someone can help me here. I followed all the steps here to install this from source, but when I start up Gnomad with my Creative Zen Nano Plus plugged in, I get this message:

No jukeboxes found on USB bus

---

### Post by ntetreau on 2007-02-27
toasterofirony:  removing libmtp2 will not bork your system, nothing else than gnomad2 or maybe amarok depending on your ubuntu version depends on it.  Try purging it and you'll see what depends on it.  Anyway, if the compile doesn't fix your problems, you can always just reinstall the repository version.  

Murwiz:  can you run mtp-detect after pluging in your device?  Are you sure you did the libmtp.rules step?

Nic

---

### Post by Murwiz on 2007-02-27
> **ntetreau said:**
> 

Murwiz:  can you run mtp-detect after pluging in your device?  Are you sure you did the libmtp.rules step?

Nic

I did that step, and just now checked on it to make sure the file was properly dated "today" just to make sure. mtp-detect with the Nano plugged in reports "No MTP devices". Even as root.

---

### Post by macogw on 2007-02-27
> **ntetreau said:**
> Hi guys, I'm not sure which method of installation you are using but since you are having problems, why not try to purge libmtp you installed from the repositories and compile it instad.  If so, make sure your remove the -dev package as well.

Nic

I did```
sudo apt-get remove --purge libmtp-dev libmtp2 libmtp5
``` because I kept getting PDE device NULL even though I put it in the file that lists vendor and device ids.  Then I installed libmtp from source, but it says it failed to create the deb, and this is the log:

```
(Reading database ... 151115 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/maco/src/gnomad/libmtp-0.1.3/libmtp_0.1.3-1_i386.de
b (--install):
 trying to overwrite `/usr/bin/gcc', which is also in package gcc
Errors were encountered while processing:
 /home/maco/src/gnomad/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
```

Anyone know what that means?  It does finish making the .deb.  I did ls and it's there.  I tried
```
sudo dpkg -i libmtp_0.1.3.deb
``` (or whatever it is, I used tab after I got it partially typed in), but the same error comes up.  Why's it trying to overwrite gcc?

---

### Post by ntetreau on 2007-02-28
macogw:  other people had this same problem with checkinstall a while ago. I couldn't find what was the solution but i believe you can try this instead:

sudo make install

Murwiz:  might be a stupid question but does you nano work correctly in windows?  You might want to look if there is a newer firmware for it.  Les us know how it goes.

Nic

---

### Post by Murwiz on 2007-02-28
Yes, I was able to connect to the Nano using Windows Media Player on Win2000, and read from it and write to it.

I did neglect to mention that my Ubuntu installation is a 64-bit system: 2.6.15-28-amd64-generic.

---

### Post by ntetreau on 2007-02-28
Hi Murwiz,
it could very well be linked to you running in 64-bits, let's see if anybody else respond to this claim.  In the mean time, to you get anything from lsusb went your device is plugged in?

Nic

---

### Post by Murwiz on 2007-02-28
Yes --

> Bus 005 Device 008: ID 041e:4139 Creative Technology, Ltd Zen Nano Plus


---

### Post by toasterofirony on 2007-02-28
So gnomad will do its thing, but I have one more tiny issue I'm hoping that someone will be able to help me with: is it possible to get gnomad to recursively create folders for the music it ports over? Because having over 4000 tracks dumped into my music folder and having to sort through them is not my idea of a good night in!

---

### Post by depressing drawers on 2007-03-01
Successfully followed the instructions for edgy and seems to work fine, however, when I try and download a track off my Zen touch gnomad crashes without so much as a warning message - Just dumps me out onto the desktop - Any ideas ?

---

### Post by toasterofirony on 2007-03-01
This was a bug for me, too. I think it had something to do with too much metadata being handled at once. I would be able to transfer maybe 100 or so tracks and then it would just die, no warning, no error report.

I'm trying 2.8.11 to see if that makes life easier. Or at the least, more reliable.

---

### Post by dracomordag on 2007-03-04
> **msak007 said:**
> [SIZE=4]7. Compile libmtp
```
./configure --prefix=/usr
sudo make
sudo checkinstall
```Hit Enter three times, give your package a description, then hit Enter twice. You'll get a confirmation that the package was installed telling you the name of the package, where the package was created, and how to uninstall it.

(Reading database ... 158562 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.3-1_i386.deb) ...
dpkg: error processing /home/david/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i3
86.deb (--install):
 trying to overwrite `/usr/bin/mtp-detect', which is also in package libmtp-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/david/gnomad_install/libmtp-0.1.3/libmtp_0.1.3-1_i386.deb
/var/tmp/JZPOeRQhQUHOBDhJTlrXV/dpkginstall.log (END)

---

### Post by dracomordag on 2007-03-04
i found my problem... i had to remove libmtp. i suggest that you put that as step one in the process (there were quite a few other people in this thread who posted this exact problem)

---

### Post by macogw on 2007-03-07
I tried sudo make install too....like 50 times I've tried compiling libmtp, gotten no errors, over and over and nothing's working

interestingly, i just plugged it in and did an lsusb and what was showing up 2 hours ago now doesn't show up.  it says theres nothing in my usb port.  the system log says

new high speed USB device using ehci_hcd and address 18
device not accepting address 18, error -110

what do i do about that?

---

### Post by macogw on 2007-03-07
ok nevermind that.  the mp3 player froze, thats why it wouldnt take the address.  i just recompiled libmtp with the prefix set then removed gnomad then recompiled that too instead of using the repos one and NOW it works...finally

---

### Post by JohnSmith on 2007-03-08
today i got my new creative V zen.. and i didnt know that it doesn't work with ubuntu... 

I tried this and some other how-tos.. but i did not manage to get my player to work!

i did everything like in the how-to , except that i never wrote the "--prefix=/usr" because     
with that in the command line, the installation was impossible !

if i type gnomad2 in terminal i get following output :
gnomad2: error while loading shared libraries: libmtp.so.5: cannot open shared object file: No such file or directory

what did i do wrong .. ?

---

### Post by macogw on 2007-03-08
> **JohnSmith said:**
> today i got my new creative V zen.. and i didnt know that it doesn't work with ubuntu... 

I tried this and some other how-tos.. but i did not manage to get my player to work!

i did everything like in the how-to , except that i never wrote the "--prefix=/usr" because     
with that in the command line, the installation was impossible !

if i type gnomad2 in terminal i get following output :
gnomad2: error while loading shared libraries: libmtp.so.5: cannot open shared object file: No such file or directory

what did i do wrong .. ?

You HAVE to do the --prefix=/usr or else gnomad2 can't get access to the library without sudo.  recompile libmtp with that prefix, but try doing "sudo make install" instead of "sudo checkinstall"

---

### Post by JohnSmith on 2007-03-08
worked ! :KS 

is it normal that the uplink is a bit slow ?
coping one song takes about 10 seconds.. it think my old usbstick was a bit faster..

---

### Post by macogw on 2007-03-08
It takes a few seconds per song on mine, but I don't think it's 10 seconds...

---

### Post by Donshyoku on 2007-03-08
I have a Zen Vision:M... with Windows Media Player, when I MTP transfer, it also transfers the album art.  Does Gnomad do this as well if I sync MTP?

---

### Post by hippykid on 2007-03-11
For anyone else who has the "can't set config #1, error -110" message in dmesg, try updating your device's firmware. I spent about 5 hours today banging my head on the desk and recompiling everything before I got round to trying the firmware update from creative.com! I have a 60 GB Zen Vision:M which had firmware version 1.11.04e - now updated to 1.20.02e and everything appears to be working perfectly (so far!) :)

Linda

---

### Post by dracomordag on 2007-03-11
does anyone know if a Toshiba Gigabeat S will work through this method? (gnomad + mtp, etc.)

---

### Post by ntetreau on 2007-03-12
Donshyoku:  You can try installing amarok with mtp support.  Amarok does transfer the album art with the songs although i don't have a device with this characteristic so i could never try it.

Dragomordag: Your device is a MTP device so if it ever works with Linux, it will be with this method.  So give it a try, compile libmtp at least and run mtp-detect to see if your device is supported.

---

### Post by dracomordag on 2007-03-12
i dont own it yet, but i would very much like to get one.

my sister's Creative Microphoto and my Dell DJ both work perfectly, so hopefully it'd work. I know someone who owns one, so I can get him to test it out ASAP

---

### Post by msak007 on 2007-03-12
> **dracomordag said:**
> does anyone know if a Toshiba Gigabeat S will work through this method? (gnomad + mtp, etc.)
It'll defiinitely work with libmtp, the device is already listed as being supported in libmtp.rules:

```
# Toshiba Gigabeat S
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0010", SYMLINK+="libmtp-%k", MODE="666"
```

Not sure about integration with Gnomad, but I assume it would work. Try it out and let us know, as I'm interested to see if Gnomad will work with devices other than Creative's devices and their derivatives (Dell DJ). I searched the forums to see if anybody had success with it, but didn't find anything conclusive. I did find an online review of the device with this little excerpt:

> Connectivity has both upsides and drawbacks. It's great to see that you can upload photos directly from a digital camera by using the small USB adapter included, thereby taking the PC out of the equation. But the drawback is that the Gigabeat S is married to the Windows operating system, meaning that if you're running Linux or Mac OS, than you've got no way of synching content onto the device.

I'm pretty sure that the author is not aware of projects such as libmtp and Gnomad, and that the same could be said of any other MTP device. Either way if you have access to one or know someone that has one try it out and let us know.

---

### Post by dracomordag on 2007-03-12
> **msak007 said:**
> It'll defiinitely work with libmtp, the device is already listed as being supported in libmtp.rules:

```
# Toshiba Gigabeat S
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0010", SYMLINK+="libmtp-%k", MODE="666"
```

Not sure about integration with Gnomad, but I assume it would work. Try it out and let us know, as I'm interested to see if Gnomad will work with devices other than Creative's devices and their derivatives (Dell DJ). I searched the forums to see if anybody had success with it, but didn't find anything conclusive. I did find an online review of the device with this little excerpt:



I'm pretty sure that the author is not aware of projects such as libmtp and Gnomad, and that the same could be said of any other MTP device. Either way if you have access to one or know someone that has one try it out and let us know.
yea, it was that article that got me worried about purchasing one

but then i remembered that everything is pretty much eventually solved in Linux...

---

### Post by flugheim on 2007-03-13
Hi im trying to install gnomad2 with mtp support with the "repo"-way on edgy (actually Linux MInt Bianca, but it's the same :P ) but i get this one when trying to to "make" on gnomad2: [http://pastebin.ca/393462](http://pastebin.ca/393462)

I cant figure out whats wrong..

---

### Post by ntetreau on 2007-03-13
Hi flugheim, you probably have libmtp-dev installed, check in synaptic, remove it, then try the "compiling"-way making sure to use the --prefix as explained in the how to.  Let us know if you are having problems.

Nic

---

### Post by flugheim on 2007-03-13
Thanks, that did the trick :)

---

### Post by ChrisBatcho on 2007-03-13
I tried this and this is what I got:

```
sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@ComputerComputer ]
1 -  Summary: [ Package created with checkinstall 1.6.0 ]
2 -  Name:    [ gnomad2 ]
3 -  Version: [ 2.8.10 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ gnomad2-2.8.10 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
Making install in src
make[1]: Entering directory `/home/dezmodium/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/dezmodium/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.
```



So then I tried "sudo make install" like someone suggested:
```
sudo make install
Making install in src
make[1]: Entering directory `/home/dezmodium/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/local/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr/local\" -DSYSCONFDIR=\"/usr/local/etc\" -DDATADIR=\"/usr/local/share\" -DLIBDIR=\"/usr/local/lib\" -DPIXMAPSDIR=\""/usr/local/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/dezmodium/gnomad_install/gnomad2-2.8.10/src'
make: *** [install-recursive] Error 1
```

What gives?

---

### Post by msak007 on 2007-03-13
> **ChrisBatcho said:**
> I tried this and this is what I got:
...

So then I tried "sudo make install" like someone suggested:

...

What gives?

Which method are you following (repo version of libmtp or compiling from source), and which version of Ubuntu are you using? Your output looks almost identical to the one flugheim posted a couple posts back.

---

### Post by ntetreau on 2007-03-14
Chrisbatcho, indeed your output seems very similar to many others in this thread, try removing libmtp-dev in synaptic and compiling libmtp from source before compiling gnomad2, that should fix your problem if it's the same as the others.

Nic

---

### Post by S.nazari on 2007-03-14
All the relavant packages are there. 
[ubuntu.alborz.uk.com](ubuntu.alborz.uk.com). 
But I still get this error 
 gnomad2
gnomad2: error while loading shared libraries: libmtp.so.5: cannot open shared object file: No such file or directory

---

### Post by ChrisBatcho on 2007-03-14
> **ntetreau said:**
> Chrisbatcho, indeed your output seems very similar to many others in this thread, try removing libmtp-dev in synaptic and compiling libmtp from source before compiling gnomad2, that should fix your problem if it's the same as the others.

Nic

Ok thanks I will try that as soon as I get my mouse working again. (Posting from windows xp right now :(  )

---

### Post by ntetreau on 2007-03-14
S.nazari:  You probably forgot to use the --prefix=/usr when compiling, go back to the instrustions and follow them closely.  Let us know if you still have problems.

Nic

---

### Post by bails on 2007-03-14
so i tried this and got a couple of errors...
first when i did sudo checkinstall for the installation of libnjb i saw
Enter a number to change any of them or press ENTER to continue:

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package
 which i think is bad.
i looked at the log file and it said:


(Reading database ... 125045 files and directories currently installed.)
Unpacking libnjb-2.2.5 (from .../libnjb-2.2.5_2.2.5-1_i386.deb) ...
dpkg: error processing /home/bailey/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libnjb.so.5.1.0', which is also in package libnjb5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/bailey/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb


then i saw when installiing gnome while ./configure ing i saw:

checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.

i tried to find all these things and couldn't find them... i know that libnjb is needed but i can't seem to be able to install gtk+-2.0
See the pkg-config man page for more details.

thanks in advance for your help

---

### Post by msak007 on 2007-03-14
> **bails said:**
> so i tried this and got a couple of errors...
first when i did sudo checkinstall for the installation of libnjb i saw
Enter a number to change any of them or press ENTER to continue:

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package
 which i think is bad.
i looked at the log file and it said:


(Reading database ... 125045 files and directories currently installed.)
Unpacking libnjb-2.2.5 (from .../libnjb-2.2.5_2.2.5-1_i386.deb) ...
dpkg: error processing /home/bailey/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb (--install):
**  trying to overwrite `/usr/lib/libnjb.so.5.1.0', which is also in package libnjb5**
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/bailey/gnomad_install/libnjb-2.2.5/libnjb-2.2.5_2.2.5-1_i386.deb


then i saw when installiing gnome while ./configure ing i saw:

checking pkg-config is at least version 0.9.0... yes
checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.

i tried to find all these things and couldn't find them... i know that libnjb is needed but i can't seem to be able to install gtk+-2.0
See the pkg-config man page for more details.

thanks in advance for your help
Compiling libnjb failed because you already have libnjb from the repositories installed, and the package you are trying to compile conflicts with it (relevant output bolded in your post). You only need to compile libnjb from source if you're using Dapper, so if you are you first need to get rid of the repository version of libnjb::

```
sudo aptitude purge libnjb
```Once you've done that, you can try reinstalling the libnjb that you compiled. Since it already made the .deb and failed on the installation step, you don't need to recompile or run checkinstall again. Just go to where it created the file and install it:

```
cd /home/bailey/gnomad_install/libnjb-2.2.5/
sudo aptitude dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
```This will satisfy the libnjb dependency when compiling Gnomad. The other thing left is to install install libgtk2.0-dev, so type

```
sudo aptitude install libgtk2.0-dev
```Then try compiling Gnomad again, and you shouldn't get any more errors. Hope that helps, let us know if you have any other issues.

---

### Post by ntetreau on 2007-03-15
Hi all, for those interested, I wrote a short howto to get your mtp device working with rhythmbox (svn).  It is highly experimental so don't expect everything to work yet.  

[http://ubuntuforums.org/showthread.php?p=2303665#post2303665](http://ubuntuforums.org/showthread.php?p=2303665#post2303665)

Help is needed to improve the plugin.  If you are good with hotplugging and HAL, give a hand!

Nic

---

### Post by tw1ggy.ramir3z on 2007-03-16
Can anyone help me? My Philips GoGead HDD085/00 isn't detected by mtp-detect but if i give:

```
lsusb
``` 

I receive:

> twiggy@the-pit:~/Applicazioni/libmtp-0.1.3$ lsusb 
Bus 003 Device 004: ID 0471:014d Philips 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 055f:0006 Mustek Systems, Inc. ScanExpress 1200 UB
Bus 001 Device 001: ID 0000:0000  


I tried whit libmtp 1.3 and 1.4. Now I don't know what I have to do to get Ubuntu mount this player... Thanks in advance...

---

### Post by CaptSaltyJack on 2007-03-16
So, following post #1, method 2 (manual install) worked.  Method 1 failed.

However, gnomad2 is pretty buggy.  I get seg faults when I try to transfer data..it happens randomly.  Music transfer is fine, but data transfer can cause seg faults.

Anyone else experience this?

Ideally, I'd just like to plug in the Zen Vision:M and see it under 'Filesystem'.. and drag/drop files.  Or access it via /media/Zen or something like that.  I don't like these software interfaces.  I don't even use them in WinXP either.

---

### Post by rmx.dave on 2007-03-17
Hello everyone,

First of all, thanks for a great how-to. I was able to install gnomad2 and libmtp no prob. BUT, when I run Gnomad, my MP3 player is not recognized. I have a Zen Vision: M. I had a different vision:m a few weeks ago but I returned it because the hard drive clicked and froze. When I plugged that one in it gave me the "Import Photos" dialog and was recognized and all. Now, when I plug my new Zen in, nothing happens. The device shows up in lsusb:

```

Bus 005 Device 008: ID 041e:413e Creative Technology, Ltd           //this is my Zen
Bus 005 Device 003: ID 0ac8:c002 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 062a:0000 Creative Labs                              //this is just my mouse
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```
When I run gnomad2 from the terminal, this is what she says:
```

Failed to open connection to D-BUS bus
PDE device NULL.

```
Does anyone know how to fix this? I'm such a Linux noob (after 7 months) and it very well could be something simple. I hope it is. 

Thanks a ton,
rmx.dave

EDIT: I have started from scratch, purged all packages...same results. And yes, I've tried different USB ports.

---

### Post by ntetreau on 2007-03-17
rmx.dave:  Did you run the sudo bash hotplug.sh?  From the libmtp.rules file, it seems your device should be completely supported:

# Creative Zen Vision:M
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="666"
.
Perhaps you might want to check if there is an updated firmware that would help



CaptSaltyJack:  What you need then is mtpfs ([http://www.adebenham.com/mtpfs/)](http://www.adebenham.com/mtpfs/)), that will mount your device and will enabled transfers with nautilus.

Nic

---

### Post by rmx.dave on 2007-03-18
Oh my gosh. I don't know what I did wrong the first five times, but now it worked. I think I forgot to double check to see if hotplug.sh did its job and I forgot to restart the udev thing. Either way it now works, thanks a ton for your help. I can finally enjoy this awesome player!

---

### Post by bails on 2007-03-18
> **msak007 said:**
> Compiling libnjb failed because you already have libnjb from the repositories installed, and the package you are trying to compile conflicts with it (relevant output bolded in your post). You only need to compile libnjb from source if you're using Dapper, so if you are you first need to get rid of the repository version of libnjb::

```
sudo aptitude purge libnjb
```Once you've done that, you can try reinstalling the libnjb that you compiled. Since it already made the .deb and failed on the installation step, you don't need to recompile or run checkinstall again. Just go to where it created the file and install it:

```
cd /home/bailey/gnomad_install/libnjb-2.2.5/
sudo aptitude dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
```This will satisfy the libnjb dependency when compiling Gnomad. The other thing left is to install install libgtk2.0-dev, so type

```
sudo aptitude install libgtk2.0-dev
```Then try compiling Gnomad again, and you shouldn't get any more errors. Hope that helps, let us know if you have any other issues.

following your advice i got this :

bailey@idiot-box:~/gnomad_install/libnjb-2.2.5$ sudo aptitude dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
-u and -i may not be specified in command-line mode (eg, with 'install')aptitude 0.4.0
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 upgrade      - Perform a safe upgrade
 dist-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z                 Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends Specify whether or not to treat recommends as
                strong dependencies
 -S fname: Read the aptitude extended status info from fname.
 -u      : Download new package lists on startup.
 -i      : Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.

---

### Post by msak007 on 2007-03-18
> **bails said:**
> following your advice i got this :

bailey@idiot-box:~/gnomad_install/libnjb-2.2.5$ sudo aptitude dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
-u and -i may not be specified in command-line mode (eg, with 'install')aptitude 0.4.0
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):
... 
                  This aptitude does not have Super Cow Powers.

**aptitude** and **dpkg** are 2 separate, independent commands. They cannot be used together, as aptitude is used to install a package from a repository, and dpkg is used to install a local .deb file. So it's either something like *sudo aptitude install <package name>* or *sudo dpkg -i <local .deb>*. In your case, since you already have the deb file locally, you'd do

```
sudo dpkg -i libnjb-2.2.5_2.2.5-1_i386.deb
```

---

### Post by msak007 on 2007-03-18
> **tw1ggy.ramir3z said:**
> Can anyone help me? My Philips GoGead HDD085/00 isn't detected by mtp-detect but if i give:

```
lsusb
```I receive:



I tried whit libmtp 1.3 and 1.4. Now I don't know what I have to do to get Ubuntu mount this player... Thanks in advance...
I don't think your device is supported by libmtp yet. Looking at the most current libmtp.rules file I found no mention of your device and only a handful of Philips devices seem to be currently supported:


>  cat /etc/udev/rules.d/libmtp.rules | grep Philips
# Philips HDD6320
# Philips HDD6320/00 & HDD6330/17
# Philips HDD1630/17
# Philips GoGear Audio
# Philips GoGear SA9200
# Philips PSA235I did find some info on it after a little bit of searching and it does seem to be an MTP player. One thing I can maybe suggest is to modify the rules file to include it, and then see if it's detected. First unplug your device, then try the following:

1. If you ran the setup and the hotplug.sh script properly per the instructions, you should have a file in /etc/udev/rules.d called **libmtp.rules**. Try to modify it and include your device like this:

```
sudo nano /etc/udev/rules.d/libmtp.rules
```2, Paste the following into the file (at the very end if you want) and then hit CTRL+X to save it:

```
# Philips HDD085/00
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="014d", SYMLINK+="libmtp-%k", MODE="666"
```

2. Restart udev so the new rulefile takes effect, then plug it back in and try again:

```
sudo /etc/init.d/udev restart
```Try that and let us know how it works.

---

### Post by Lucas2005 on 2007-03-19
I just want to say thanks to msak007 for this entire thread, i got Gnomad2 working with my Creative Zen M on my Toshiba A105-S4284 with Ubuntu 6.06 LTS.  I followed his first post and then his post number 512 on page 52 to solve libnjb issues. :) 

> **msak007 said:**
> Compiling libnjb failed because you already have libnjb from the repositories installed, and the package you are trying to compile conflicts with it (relevant output bolded in your post). You only need to compile libnjb from source if you're using Dapper, so if you are you first need to get rid of the repository version of libnjb::

Thanks a bunch! :guitar:

---

### Post by bails on 2007-03-19
ok now i've finished installing libnjb 2.2.5 as per your instructions and i was ./configure 'ing the gnomad and i got this now.

checking for GN... configure: error: Package requirements (             glib-2.0                gthread-2.0             libnjb >= 2.2.4                 gtk+-2.0 ) were not met:

No package 'libnjb' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by bails on 2007-03-19
ok forget that last post i got gnomad working. but it doesn't see that my zen v plus is plugged in i got this error too

(gnomad2:21649): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `error == NULL || *error == NULL' failed
Segmentation fault

---

### Post by pingpongboss on 2007-03-20
wow!! thank you so much for the guide. I just want people to know, that under the edgy installation tutorial, I got gnomad2 to work using the compile-from-source method. There seems to be something wrong with the files in the ubuntu repos.

again, thank you!!

---

### Post by pingpongboss on 2007-03-20
followup: gnomad2 would randomly crash when I try to transfer songs from the player to my laptop

when i run it as sudo, it crashes less often. Whenever it does crash, it's always at the end of a file transfer.

weird

---

### Post by macogw on 2007-03-20
> **pingpongboss said:**
> wow!! thank you so much for the guide. I just want people to know, that under the edgy installation tutorial, I got gnomad2 to work using the compile-from-source method. There seems to be something wrong with the files in the ubuntu repos.

again, thank you!!

The ones in the Feisty repo are bad as well.

---

### Post by dracomordag on 2007-03-21
alright, using a Toshiba Gigabeat S, the following happens

upon pluging it in, the Gigabeat registers connection (screen goes blue, says connecting, etc.)
upon opening gnomad 2 2.8.10, it says "gathering metadata" and such
after about 30 seconds, it goes to Scanning Jukebox Library

about 5 minutes later, some tracks start showing up, but it is constantly hanging

eventually, everything loads.

transfers are of moderate speed, but work both ways.



so, all in all... [size=4]IT WORKS![/size] with Toshiba Gigabeat S. I assume that the slowness is a mix of the 60 GB of space on the machine, and the program.

---

### Post by golferpatg on 2007-03-25
I cant get the "sudo make" command to work using the first method described on this forum. Here is what i type and the output. What can i do to fix this?

pat@pat-desktop:~/gnomad_install/gnomad2-2.8.10$ sudo make
Making all in src
make[1]: Entering directory `/home/pat/gnomad_install/gnomad2-2.8.10/src'
if gcc -DPACKAGE_NAME=\"gnomad2\" -DPACKAGE_TARNAME=\"gnomad2\" -DPACKAGE_VERSION=\"2.8.10\" -DPACKAGE_STRING=\"gnomad2\ 2.8.10\" -DPACKAGE_BUGREPORT=\"http://sourceforge.net/tracker/\?func=add\&group_id=65573\&atid=511470\" -DPACKAGE=\"gnomad2\" -DVERSION=\"2.8.10\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_LIBMTP=1 -DGETTEXT_PACKAGE=\"gnomad2\" -DHAVE_LOCALE_H=1 -DHAVE_LC_MESSAGES=1 -DHAVE_BIND_TEXTDOMAIN_CODESET=1 -DHAVE_GETTEXT=1 -DHAVE_DCGETTEXT=1 -DENABLE_NLS=1 -DGNOMADLOCALEDIR=\"/usr/share/locale\" -DHAVE_DIRENT_H=1 -DSTDC_HEADERS=1 -DHAVE_MALLOC_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_FCNTL_H=1 -DHAVE_CHDIR=1  -I. -I. -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -DPREFIX=\"/usr\" -DSYSCONFDIR=\"/usr/etc\" -DDATADIR=\"/usr/share\" -DLIBDIR=\"/usr/lib\" -DPIXMAPSDIR=\""/usr/share/pixmaps"\"    -g -O2 -MT jukebox.o -MD -MP -MF ".deps/jukebox.Tpo" -c -o jukebox.o jukebox.c; \
        then mv -f ".deps/jukebox.Tpo" ".deps/jukebox.Po"; else rm -f ".deps/jukebox.Tpo"; exit 1; fi
jukebox.c:130: error: ‘LIBMTP_FILETYPE_AAC’ undeclared here (not in a function)
jukebox.c:131: error: ‘LIBMTP_FILETYPE_FLAC’ undeclared here (not in a function)
jukebox.c:132: error: ‘LIBMTP_FILETYPE_MP2’ undeclared here (not in a function)
jukebox.c:133: error: ‘LIBMTP_FILETYPE_M4A’ undeclared here (not in a function)
jukebox.c:134: error: ‘LIBMTP_FILETYPE_DOC’ undeclared here (not in a function)
jukebox.c:135: error: ‘LIBMTP_FILETYPE_XML’ undeclared here (not in a function)
jukebox.c:136: error: ‘LIBMTP_FILETYPE_XLS’ undeclared here (not in a function)
jukebox.c:137: error: ‘LIBMTP_FILETYPE_PPT’ undeclared here (not in a function)
jukebox.c:138: error: ‘LIBMTP_FILETYPE_MHT’ undeclared here (not in a function)
jukebox.c:139: error: ‘LIBMTP_FILETYPE_JP2’ undeclared here (not in a function)
jukebox.c:140: error: ‘LIBMTP_FILETYPE_JPX’ undeclared here (not in a function)
jukebox.c: In function ‘flush_usage’:
jukebox.c:1152: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1153: error: ‘mtp_filetype_description_t’ has no member named ‘MaxCapacity’
jukebox.c:1153: warning: assignment makes integer from pointer without a cast
jukebox.c:1154: error: ‘LIBMTP_mtpdevice_t’ has no member named ‘storage’
jukebox.c:1154: error: ‘mtp_filetype_description_t’ has no member named ‘FreeSpaceInBytes’
jukebox.c:1154: warning: assignment makes integer from pointer without a cast
jukebox.c: In function ‘scan_thread’:
jukebox.c:1434: warning: assignment makes pointer from integer without a cast
jukebox.c:1594: warning: assignment makes pointer from integer without a cast
make[1]: *** [jukebox.o] Error 1
make[1]: Leaving directory `/home/pat/gnomad_install/gnomad2-2.8.10/src'
make: *** [all-recursive] Error 1

---

### Post by yoink23 on 2007-03-25
I have a Creative Zen Vision:M, and I'm running the feisty version of gnomad2.  I saw that in 2.6 or something it claimed folder support.  Unfortunately, when I use the right-click menu to add folders it doesn't do so, and the folders that are already on my zen are not visible.  I need this functionality to organize my videos.

Also, would I be able to run the windows only creative software with wine, in order to create folders if need be?

---

### Post by macogw on 2007-03-25
You should be able to click on the folder in Gnomad and hit the "import" arrow

---

### Post by ntetreau on 2007-03-26
golferpatg:   You probably have libmtp-dev installed and conflicting with the libmtp you manually compiled.  Make sure to remove it in synaptic and then try again. 

yoink23:  macogw is right but you can also try mtpfs if you'd prefer a pure nautilus environment to manage your files.  

[http://www.adebenham.com/mtpfs/](http://www.adebenham.com/mtpfs/)

Nic

---

### Post by haelen on 2007-04-01
Hi,

There's probably no one following this thread now, but I've just tried method 1 for Edgy, but when I checked I had the following:

libnjb1 and libmtp2

I checked in the radept manager and libnjb and libmtp are not there.
Needless to say Gnomad2 could not locate a USB bus. :( 

Best,
Tim

---

### Post by ntetreau on 2007-04-01
Hi haelen, try method two, make sure to remove in synaptic any mention of libmtp, libmtp-dev and gnomad2 beforehand.  If I remember well, you need to use sudo make install instead in sudo checkinstall for libmtp.  You can also check this thread to get your MTP device working with the latest rhythmbox but that's slightly more risky:  [http://ubuntuforums.org/showthread.php?t=385371](http://ubuntuforums.org/showthread.php?t=385371)

I'm too lazy to check the first page again, but I use this for libmtp and similar for gnomad2 if you want to use it:

```
wget http://downloads.sourceforge.net/libmtp/libmtp-0.1.3.tar.gz?modtime=1173308515&big_mirror=0

tar -xvzf  libmtp-0.1.3.tar.gz

cd libmtp-0.1.3

./configure --prefix=/usr

make && sudo make install

sudo bash hotplug.sh

mtp-detect
```

---

### Post by haelen on 2007-04-01
Amazing! Method 2 worked perfectly.

I can't thank you (and the thread originator) enough for your efforts. You have provided an answer to a problem which caused my son (whose Zen V player it is) to curse the day this January that I wiped Windows from my HD using the Kubuntu CD-ROM 

If he didn't 'need' Windows to keep in-sync with his IT work at school I might well have made him a convert (or should that be 'konvert' to be korny!)

Tim

---

### Post by msak007 on 2007-04-01
> **haelen said:**
> Hi,

There's probably no one following this thread now, but I've just tried method 1 for Edgy, but when I checked I had the following:

libnjb1 and libmtp2

I checked in the radept manager and libnjb and libmtp are not there.
Needless to say Gnomad2 could not locate a USB bus. :( 

Best,
Tim

This thread is still very active and we all try to help when someone posts a question or a problem. I haven't tried Method 1 (repo version) in a long time, since I first installed Edgy, and I always use Method 2. The how-to really hasn't been updated in a while, aside from updating the links and version #s in the steps to the new versions when they come out, so it may be due for an update. Once Feisty is released, I'll try to triple boot Dapper, Edgy, and Feisty on my non-production laptop and then update the how-to with any necessary changes.

> **ntetreau said:**
> Hi haelen, try method two, make sure to remove in synaptic any mention of libmtp, libmtp-dev and gnomad2 beforehand.  If I remember well, you need to use sudo make install instead in sudo checkinstall for libmtp. 

I still use checkistall and have had no problems whatsoever. Not sure what problems others have had, but it's always worked for me.

> **haelen said:**
> Amazing! Method 2 worked perfectly.

I can't thank you (and the thread originator) enough for your efforts. You have provided an answer to a problem which caused my son (whose Zen V player it is) to curse the day this January that I wiped Windows from my HD using the Kubuntu CD-ROM 

If he didn't 'need' Windows to keep in-sync with his IT work at school I might well have made him a convert (or should that be 'konvert' to be korny!)

Tim

Not a problem, we're all glad to help. Thanks for letting us know it worked for you and hopefully one day your son will be also "konvert" :) (I also use Kubuntu).

---

### Post by pingpongboss on 2007-04-02
> **macogw said:**
> You should be able to click on the folder in Gnomad and hit the "import" arrow

I need to make folders in the zen vision m too, and the import arrow does not work in gnomad2

gnomad version: 2.8.8

---

### Post by haelen on 2007-04-02
Just a thought: When the next version of Ubuntu is announced and installed, is it likely to affect the Gnomad / Zen setup that's already in place?

Thanks,
Tim

---

### Post by macogw on 2007-04-02
> **pingpongboss said:**
> I need to make folders in the zen vision m too, and the import arrow does not work in gnomad2

gnomad version: 2.8.8

I'm using Gnomad2 on Feisty (compiled, the repo ones don't work) and I can click on my "Music" folder, hit the arrow, and have it's entire contents copied over, with the folder hierarchy....theoretically.  Realistically, the amount of data involved crashes Gnomad2 so I only copy over one artist (with album folders under that and mp3s inside those) at a time.

haelen: If you compiled it (which, seeing as Dapper had the last working debs, I'm guessing you did), it won't affect it.  If you used the debs, they might be updated, but I'm pretty sure Feisty and Edgy have the same versions, so nothing would change.

---

### Post by msak007 on 2007-04-02
> **pingpongboss said:**
> I need to make folders in the zen vision m too, and the import arrow does not work in gnomad2

gnomad version: 2.8.8
Check the "Preferences" tab and make sure the option "Recurse into any selected directories when transferring". That'll grab the contents of the folder, as well as any subfolders and their contents.

> **haelen said:**
> Just a thought: When the next version of Ubuntu is announced and installed, is it likely to affect the Gnomad / Zen setup that's already in place?

Thanks,
Tim
Never tried it, I usually format and reinstall rather than dist-upgrading and end up recompiling anyway. Theoretically the versions installed should continue working because they were manually compiled. It's probably better to recompile though, because some of the dependencies that were installed when first compiling will probably have newer versions in Feisty. It's worth a shot though, and if it doesn't work the worst case scenario is you'll have to recompile everything.

---

### Post by pingpongboss on 2007-04-03
freakin god, i finally figured out how to organize my videos under folders in the Creative Zen Vision:M. I've searched everywhere, and couldnt find anywhere that really explained how to do it. Maybe I just was looking in the wrong places. So if what I did was really obvious, please ignore ;_;

Through accident, really, I figured out that I could use the command line mtp-* commands. Here's what I did under Feisty. You need the latest libmtp package (think hte name's actualy libmtp5 or soemthing) and you might need to run the following commands with sudo:

make sure you can already transfer music/photos/videos to your vision m first (I will only show how to make folders and stuff)

connect the zen vision m to your computer, and turn it on.

1. Run:
```
mtp-folders
```
to list all the folders. Make note of the number in front of the folder labeled Video. My number was 108.

2. Make a new folder by running:
```
mtp-connect --newfolder 108/NewName/a
```
where "108" is the number you got from step 1, "NewName" is the name of the subfolder that you're making, and "a" is just something random (lol). I couldn't create folders by just putting "108/NewName/", there had to be something on the end.

3. Check that your new folder is there by running this again:
```
mtp-folders
```
Your newly made folder should be slightly indented under the Video folder. Take note of the number of this new subfolder. Mine was 345469.

4. Transfer a video file into your new subfolder by running:
```
mtp-sendfile /path/to/video/file/source.avi 345469

```
Where "/path/to/video/file/source.avi" is the relative or absolute path to your local video file, and "345469" is the number of the subfolder that you got in step 3. This step will take a while since it is copying the file into your zen vision m. There will be a progress indicator-ish thing that tells you the status of the transfer.

5. After the transfer is complete, check on your zen vision m (it should be "undocked" by now) to see that the video file is indeed in the new subfolder.

6. To password protect the new folder, make sure that you have assigned a 4-digit password and that "Protected Content" is set to "Show" under System-->Player Settings. Go to the Video folder, and click the Menu button while the subfolder you would like to protect is selected. Choose Protect, and the folder icon will now have an eye creeping out at you. Go back to settings and set "Protected Content" to "Hide". Now no one will be the wiser as to what you keep on ur zen vision m ;)

I hope this guide helped the many people who were stuck like me. Hope I saved some of you guys some time. To make a folder under Photos, you could do the same, and just use the Photos directory instead of hte Videos directory.

OR, you could try to compile gnomad2 and use that (haven't tried that to see if it works yet). I had the repos version, and that's why I had to figure all this out.

**EDIT:** I tried compiling gnomad2 2.8.11 and it still does not work. Some said that they got it to work, but I think that they have only succesfully transfered Music and their associated folders, not photos or videos. For photos and videos, you need to use the Data Transfer tab, and in that mode, gnomad2 would not allow me to move/create/copy any folders. As far as I know, using mtp-* is the fastest way to manage folders. MTPfs hasnt worked well for me, since nautilus displays the amount of free space as 0 B and navigating the folders usually have a 10 second to a few minutes of lag. Even the cp command doesnt work when it's mounted under mtpfs.

---

### Post by msak007 on 2007-04-03
> **pingpongboss said:**
> freakin god, i finally figured out how to organize my videos under folders in the Creative Zen Vision:M. I've searched everywhere, and couldnt find anywhere that really explained how to do it. Maybe I just was looking in the wrong places. So if what I did was really obvious, please ignore

...

I tried compiling gnomad2 2.8.11 and it still does not work. Some said that they got it to work, but I think that they have only succesfully transfered Music and their associated folders, not photos or videos. For photos and videos, you need to use the Data Transfer tab, and in that mode, gnomad2 would not allow me to move/create/copy any folders. As far as I know, using mtp-* is the fastest way to manage folders. MTPfs hasnt worked well for me, since nautilus displays the amount of free space as 0 B and navigating the folders usually have a 10 second to a few minutes of lag. Even the cp command doesnt work when it's mounted under mtpfs.

Awesome work! The MicroPhoto I'm using doesn't support video, so I've never had to transfer it or attempted to. The mtp command line tools are cool, but yea like you said unfortunately there's no real documentation for them. Regarding 2.8.11, I have used it to successfully transfer music and photos (in data transfer mode), but the photos just end up in the root picture folder. You can't transfer them to subfolders using Gnomad (it doesn't even see the folders, just lists all the photos in a list), so I'll try using your method and see if I can create photo subfolders and transfers pictures there. I could add your steps to my original post, or if you want you can create a separate how-to and I'll link to it (the latter is probably better for you so you can edit it anytime).

---

### Post by pingpongboss on 2007-04-03
sweet, i'll make another thread if you or others report that my way works 

it'd be glad to know that a whole day's worth of searching and cursing wasnt all for naught ^^

---

### Post by ntetreau on 2007-04-03
Hi all,

since Feisty Fawn will be coming out soon enough and msak007 has already mentionned writing a new howto for Feisty Fawn, I thought perhaps we should test it a little beforehand,

Since I am already running Feisty at the moment, I tried removing completely libmtp, and then reinstalling libmtp5 (0.1.3), libmtp5-dev (0.1.3), gnomad2 (2.8.8), and amarok (1.4.5) from the repositories.

As of this writing, my creative Zen microphoto is recognized by libmtp, recognized and seems to function normally in both gnomad2 and amarok!  I guess others could give it a try but so far, on two different computers, it works.

In that case, I guess the how to could be quite simple, explaining in details what can be done with what software and perhaps how to install the latest versions (gnomad2-2.8.11 and libmtp-0.1.4) and the reasons why someone would want to do this.

Also, we might want to put a description of the capabilities of every option: rhythmbox vs amarok vs mtpfs vs gnomad2?

Anyway, I think this is great news that we have basic support in Feisty without the need for compilation, we should give the users the simplest instructions on how to enable it and use it, then the more experienced users, or those with newer devices, can always compile newer packages.

Ideas?

Nic

---

### Post by ntetreau on 2007-04-03
pingpongboss:  I think it is great you found a way to do this.  May I suggest giving mtpfs a try?  With mtpfs, you can mount the device and use it transparently in nautilus, making folders, copy and pasting files including video as far as I'm concerned.

mtpfs can be installed this way:

```
 
sudo aptitude install libfuse-dev libmad0-dev

wget http://www.adebenham.com/mtpfs/mtpfs-0.3.tar.gz

tar -xvzf mtpfs-0.3.tar.gz

cd mtpfs-0.3

./configure --prefix=/usr && make && sudo checkinstall

```

then create a directory in your home folder (MTPdevice for example), this is where you will mount the mtp device.  Add yourself to the "fuse" group: System > Administration > Users and Groups > Manage Groups > fuse > properties and then your username.  Logout and login.  

From now on, you only need to issue this command in a terminal (you can add a button to the panel as well I guess):

```

mtpfs ~/MTPdevice

```

You should then be able to browse the device in nautilus as if it was a normal folder.  Let us know if that works for what you want ot do!

Nic

---

### Post by pingpongboss on 2007-04-03
> **ntetreau said:**
> pingpongboss:  I think it is great you found a way to do this.  May I suggest giving mtpfs a try?  With mtpfs, you can mount the device and use it transparently in nautilus, making folders, copy and pasting files including video as far as I'm concerned.
Nic

I think I mentioned mtpfs in one of my first posts, and no, it does not work for me. There must be some bug in how mtpfs is implemented. I can browse my folders and see my files (it just has a long lag), and I can also make folders (again, taking up to a few minutes to do). However, nautilus thinks that the device has no more space left and so I cannot move any files into the folders. Copying through nautilus also does not work. The "cp" command seems to work at first - it stays busy for a while and makes the new file inside the folder - but the file is not accessible on the device. Also, none of the files including Music and Photos are readable in nautilus.

I made sure i was part of the FUSE group and that i have read/write permissions on the mount folder. The MTPfs sourceforge page has a single bug report where someone also said that he cannot add files through nautilus. Like the mtp-* commands, i havent found much resources for mtpfs where people actually explained if and how they got it to work. Hopefully mtpfs will get fixed and using that will be so much easier than the mtp-* commands.

---

### Post by ntetreau on 2007-04-03
I am contacting the developing to see if he can offer some help!

Nic

---

### Post by Mrlush123 on 2007-04-05
I get to step 12 and it is not able to install. It fails. This is my log. What can I do?

```
(Reading database ... 90170 files and directories currently installed.)
Unpacking libnjb (from .../libnjb_2.2.5-1_i386.deb) ...
dpkg: error processing /home/john/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb (--install):
 trying to overwrite `/usr/include/libnjb.h', which is also in package libnjb-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/john/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)


```

---

### Post by macogw on 2007-04-05
> **Mrlush123 said:**
> I get to step 12 and it is not able to install. It fails. This is my log. What can I do?

```
(Reading database ... 90170 files and directories currently installed.)
Unpacking libnjb (from .../libnjb_2.2.5-1_i386.deb) ...
dpkg: error processing /home/john/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb (--install):
 trying to overwrite `/usr/include/libnjb.h', which is also in package libnjb-dev
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/john/gnomad_install/libnjb-2.2.5/libnjb_2.2.5-1_i386.deb
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)


```
Don't use checkinstall.  

Can someone please fix the first page? Checkinstall on libnjb DOES NOT WORK!

---

### Post by msak007 on 2007-04-05
> **macogw said:**
> Don't use checkinstall.  

Can someone please fix the first page? Checkinstall on libnjb DOES NOT WORK!

Sorry, I haven't had to compile libnjb from source in a long time, but checkinstall has worked for me *every single time* for everything else. If it fails due to an issue overwriting a file (which is clearly the problem here based on the output)*,* you can always pass it the "--dpkgflags=--force-overwrite" flag (same as dpkg -f) to force an overwrite. I'll put that in there and a recommendation to try make install if it fails. If you have any other recommendations, please let me know.

---

### Post by msak007 on 2007-04-05
> **ntetreau said:**
> Hi all,

since Feisty Fawn will be coming out soon enough and msak007 has already mentionned writing a new howto for Feisty Fawn, I thought perhaps we should test it a little beforehand,

Since I am already running Feisty at the moment, I tried removing completely libmtp, and then reinstalling libmtp5 (0.1.3), libmtp5-dev (0.1.3), gnomad2 (2.8.8), and amarok (1.4.5) from the repositories.

As of this writing, my creative Zen microphoto is recognized by libmtp, recognized and seems to function normally in both gnomad2 and amarok!  I guess others could give it a try but so far, on two different computers, it works.

In that case, I guess the how to could be quite simple, explaining in details what can be done with what software and perhaps how to install the latest versions (gnomad2-2.8.11 and libmtp-0.1.4) and the reasons why someone would want to do this.

Also, we might want to put a description of the capabilities of every option: rhythmbox vs amarok vs mtpfs vs gnomad2?

Anyway, I think this is great news that we have basic support in Feisty without the need for compilation, we should give the users the simplest instructions on how to enable it and use it, then the more experienced users, or those with newer devices, can always compile newer packages.

Ideas?

Nic

> **ntetreau said:**
> I am contacting the developing to see if he can offer some help!

Nic

First of all thanks for taking the initiative to contact the developer of mtpfs. The ideal situation would be to install something like that and have read / write access to a device through the file manager (treat it as a removable disk), with the *option* to use a music app to transfer songs to it if you wanted to go that route. Let us know how that goes.

Regarding Feisty, I'm having an issue I can't resolve with my wireless card on my laptop (hangs on bootup with card inserted, have to insert it after bootup) and when I had the same issue testing Edgy pre-release the only resolution was to format and reinstall. I'll do a fresh install of Feisty Beta this weekend and try everything out, and I'll let you know how I fare with the MicroPhoto as well. The how-to is long enough already with Edgy and Dapper, I wonder if you guys think it'd be a good idea to just add a Feisty section to it since so many people already follow this thread? From what I gather so far, the steps for Feisty should be pretty simple so they won't take a lot of room. A while ago I asked a mod if this forum supported any html "anchors" so that I can link to a section of a post within the same post, but unfortunately it doesn't so you have to wade through the whole thing. Let me know what you think, input is appreciated. Thanks.

---

### Post by VortaX on 2007-04-05
Nice tutorial :) thanks ;)

---

### Post by pingpongboss on 2007-04-06
> **ntetreau said:**
> I am contacting the developing to see if he can offer some help!

Nic

great! mtpfs would be so useful if it works right :)

---

### Post by ipvietnam.com on 2007-04-06
Thanks for nice tut :)

---

### Post by gss6 on 2007-04-10
Feisty makes my gnomad2 work with my Zen Xtra MTP out of the box.

---

### Post by MysterMDD on 2007-04-10
I'm on Feisty and just downloaded Gnomad2 through the terminal (sudo apt-get install gnomad2) and it immediately picked up my Dell DJ and was able to transfer music files to it with absolutely no problems whatsoever.  I absolutely LOVE Ubuntu/Linux and all of the software that has been developed for it.  To all those developers who read this post, keep up the INCREDIBLE work.  It's all, simply put, AMAZING.

---

### Post by Murador on 2007-04-15
Hi!

I'm having troubles getting my Zen Micro to work

I'm on an Ubuntu Edgy 6.10, so I've followed the Method 2 (compile from source) of the How-To, since the first method didn't seem to work.

Now, I'm pretty sure mtp recognizes my device, since I can get the directory tree from mtp-folders and mtp-detect detects my zen.

fact is, Gnomad2 crashes everytime I launch it and have it scan for a device.

here's the output i recieve:
```
**********************************************************************

murador@desktop:~$ gnomad2
LIBMTP_Get_First_Device: No Devices Attached
PDE device NULL.
PDE device NULL.
PTP: Opening session
Queried Creative Zen Micro
*** glibc detected *** gnomad2: double free or corruption (fasttop): 0x0000000000b91450 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b512ea12733]
/lib/libc.so.6(__libc_free+0x84)[0x2b512ea128b4]
gnomad2[0x410a4f]
gnomad2[0x4119ba]
/usr/lib/libglib-2.0.so.0[0x2b512e3e0c04]
/lib/libpthread.so.0[0x2b512e8933ca]
/lib/libc.so.6(__clone+0x6d)[0x2b512ea7155d]
======= Memory map: ========
00400000-00429000 r-xp 00000000 08:02 193040                             /usr/local/bin/gnomad2
00528000-0052a000 rw-p 00028000 08:02 193040                             /usr/local/bin/gnomad2
0052a000-00b9d000 rw-p 0052a000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
40801000-40802000 ---p 40801000 00:00 0 
40802000-41002000 rw-p 40802000 00:00 0 
2aaaaab57000-2aaaaab58000 rw-p 2aaaaab57000 00:00 0 
2aaaaab58000-2aaaaabc4000 r--p 00000000 08:02 36595                      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
2aaaaabc4000-2aaaaabe3000 r--p 00000000 08:02 36597                      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
2aaaaac00000-2aaaaac21000 rw-p 2aaaaac00000 00:00 0 
2aaaaac21000-2aaaaad00000 ---p 2aaaaac21000 00:00 0 
2aaaaad00000-2aaaaad0d000 r-xp 00000000 08:02 2452                       /lib/libgcc_s.so.1
2aaaaad0d000-2aaaaae0c000 ---p 0000d000 08:02 2452                       /lib/libgcc_s.so.1
2aaaaae0c000-2aaaaae0d000 rw-p 0000c000 08:02 2452                       /lib/libgcc_s.so.1
2b512c40c000-2b512c428000 r-xp 00000000 08:02 64689                      /lib/ld-2.4.so
2b512c428000-2b512c42b000 rw-p 2b512c428000 00:00 0 
2b512c42b000-2b512c42c000 r--p 00000000 08:02 10865                      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
2b512c42c000-2b512c433000 r--s 00000000 08:02 2477                       /usr/lib/gconv/gconv-modules.cache
2b512c433000-2b512c434000 r--p 00000000 08:02 10866                      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
2b512c434000-2b512c435000 r--p 00000000 08:02 10871                      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
2b512c435000-2b512c436000 r--p 00000000 08:02 10862                      /usr/lib/locale/en_US.utf8/LC_ADDRESS
2b512c436000-2b512c437000 r--p 00000000 08:02 10868                      /usr/lib/locale/en_US.utf8/LC_NAME
2b512c437000-2b512c438000 r--p 00000000 08:02 10870                      /usr/lib/locale/en_US.utf8/LC_PAPER
2b512c438000-2b512c439000 r--p 00000000 08:02 10873                      /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2b512c439000-2b512c43a000 r--p 00000000 08:02 10867                      /usr/lib/locale/en_US.utf8/LC_MONETARY
2b512c43a000-2b512c511000 r--p 00000000 08:02 10863                      /usr/lib/locale/en_US.utf8/LC_COLLATE
2b512c511000-2b512c512000 r--p 00000000 08:02 10872                      /usr/lib/locale/en_US.utf8/LC_TIME
2b512c512000-2b512c513000 r--p 00000000 08:02 10869                      /usr/lib/locale/en_US.utf8/LC_NUMERIC
2b512c527000-2b512c529000 rw-p 0001b000 08:02 64689                      /lib/ld-2.4.so
2b512c529000-2b512c52d000 r-xp 00000000 08:02 7294                       /usr/lib/libgthread-2.0.so.0.1200.4
2b512c52d000-2b512c62c000 ---p 00004000 08:02 7294                       /usr/lib/libgthread-2.0.so.0.1200.4
2b512c62c000-2b512c62d000 rw-p 00003000 08:02 7294                       /usr/lib/libgthread-2.0.so.0.1200.4
2b512c62d000-2b512c657000 r-xp 00000000 08:02 121518                     /usr/lib/libnjb.so.5.1.0
2b512c657000-2b512c756000 ---p 0002a000 08:02 121518                     /usr/lib/libnjb.so.5.1.0
2b512c756000-2b512c758000 rw-p 00029000 08:02 121518                     /usr/lib/libnjb.so.5.1.0
2b512c758000-2b512c75e000 r-xp 00000000 08:02 2510                       /lib/libusb-0.1.so.4.4.4
2b512c75e000-2b512c85e000 ---p 00006000 08:02 2510                       /lib/libusb-0.1.so.4.4.4
2b512c85e000-2b512c860000 rw-p 00006000 08:02 2510                       /lib/libusb-0.1.so.4.4.4
2b512c860000-2b512cbe6000 r-xp 00000000 08:02 Aborted (core dumped)

```

can anybody help me or should I wait to get my hads on Feisty and its improved support?

Thank You for you help!

---

### Post by pingpongboss on 2007-04-15
did you try running gnomad2 as sudo?

---

### Post by Murador on 2007-04-16
yep, same problem :(

I Can't really figure out why. it seems that i could transfer files from the device to the pc and viceversa from the command line, using mtp-connect, but gnomad refuses to interact with the Zen.

I've even tried to change the usb port, to no avail :(

---

### Post by ntetreau on 2007-04-16
Perhaps you guys should post to the mtp mailing list, or perhaps there is one for gnomad2?

Nic

---

### Post by Murador on 2007-04-16
Good news!

I got it working by installing gnomad-2.8.12. Evidently 2.8.10 had some flaws that prevented it from working correctly.

thanks anyway, and I hope my experience helps whoever is having problems getting it to work

---

### Post by mrwednesday on 2007-04-19
Thanks a lot msak007!!! It worked like a charm! I actually tried once before but it didnt work... But it was because I was a too big n00b... :P Now I came back after using Ubuntu for a month now and it was easy as pie! Once again, thanks! Cheers from Sweden!

---

### Post by haelen on 2007-04-21
I'm thinking of upgrading to 'Feisty' but, having taken so long to get my Zen working under 'Edgy' am not sure if I can risk it yet!

Tim

---

### Post by NegativeSpace on 2007-04-21
> **haelen said:**
> I'm thinking of upgrading to 'Feisty' but, having taken so long to get my Zen working under 'Edgy' am not sure if I can risk it yet!

Tim

Having been previously unable to get my Zen Vision: M working under Ubuntu Edgy, Gnomad picked up my Zen straightaway with Feisty (installed with *apt-get install gnomad2*, dunno if using Add/Remove makes a difference). Which means Ubuntu now pretty much covers everything I need from my OS, so I can, at last, wave Windows good riddance.

---

### Post by zazen666 on 2007-04-22
Hey all,
I just installed xubuntu 7.04 and trying to set up gnomad for my creative Zen vision m.
First I tried to install via add/remove-intalled fine but did't read my zen, so i removed it via add/remove

Next, I tried to install using sudo aptitude install gnomad2-again installed fine but not reading my zen.

Edit:
Now I am trying to complile for source. First I purge, and I get an error that the complie of libmpt failed. When I purge I see this:
marshal@marshal-laptop:~$ sudo aptitude purge libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  skype update-manager update-manager-core 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
marshal@marshal-laptop:~$ sudo aptitude purge libmtp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  skype update-manager update-manager-core 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
marshal@marshal-laptop:~$ 


Is skype interferaing with my purge?
Thanks


Oh, and here is the error I get when trying to compile:

(Reading database ... 94479 files and directories currently installed.)
Unpacking libmtp (from .../libmtp_0.1.5-1_i386.deb) ...
dpkg: error processing /home/marshal/gnomad_install/libmtp-0.1.5/libmtp_0.1.5-1_
i386.deb (--install):
 trying to overwrite `/usr/bin/mtp-detect', which is also in package libmtp5
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/marshal/gnomad_install/libmtp-0.1.5/libmtp_0.1.5-1_i386.deb
/var/tmp/MaDJKNgUTQNQPmnkqPKbj/dpkginstall.log (END)




Final EDIT********
I got it working-I had to use "make install" rather than "checkinstall"
good luck to everyone else!

---

### Post by OU812 on 2007-04-22
I was running vectorlinux 5.8 std gold. I could connect to my creative zen vision player, but could not display the fonts properly. Then I tried zenwalk 4.4.1. I could connect to the device and see the tags properly, but gnomad2 kept crashing. So I finally ended up with fluxbuntu (upgraded to edgy :)  ) and found this thread. The post by wastrel on this page

[http://ubuntuforums.org/showthread.php?t=199250&page=2](http://ubuntuforums.org/showthread.php?t=199250&page=2)

finally worked for me. Thank you very much. Almost completely severed from win32!

Peace Out.

john

---

### Post by zazen666 on 2007-04-22
Actaully, I seems if I have a problem with gnomad2 (even though my post above says it is working.)

It loads up fine, I can transfer music, etc, but when I shut down, it takes a really long time and also, my ZEN gets stuck on "updating" and i have to manually reset it.

Should I try it all over again?

---

### Post by Blueshell on 2007-04-24
I just this evening got a used Creative Zen MicroPhoto 4GB, followed the Dapper instructions on the first page of this thread and bingo, gnomad2 can transfer files to and from the device.

But---it seems to be setting the clock on the Zen to UTC, rather than my local timezone.  I haven't noticed any sort of timezone offset either in gnomad2 or in the Zen UI.  Have I missed something?  (Sure, I can turn off the "set the time" box, but I also don't know how to -set- the time through the Zen UI, so it'll stay on UTC...)

Thanks.

---

### Post by DJiNN on 2007-04-26
Has anyone tried Gnomad2 on Xubuntu Feisty at all? I'm just about to install it on my Ubuntu Feisty machine, but i also use Xubuntu on another machine & it would be great if it worked there also. :)

---

### Post by msak007 on 2007-04-26
Sorry guys I just updated to Feisty this past weekend but was working on getting a few critical things working after the upgrade, so I haven't had time to work on an update for Feisty. Either way, bear with me and I'll update the how-to ASAP. Some people have said that the Feisty version of libmtp / Gnomad work for them, others not. The Feisty repos contain libmtp 0.1.3, so try it first to see if it detects your device as it's pretty recent (only up to 0.1.5 currently).

---

### Post by msak007 on 2007-04-26
> **zazen666 said:**
> Actaully, I seems if I have a problem with gnomad2 (even though my post above says it is working.)

It loads up fine, I can transfer music, etc, but when I shut down, it takes a really long time and also, my ZEN gets stuck on "updating" and i have to manually reset it.

Should I try it all over again?
Not sure if you got libmtp installed, as your first post indicated you were having problems compiling it. The repo version of libmtp is actually called "libmtp5", so uninstall / purge that first and then try to compile it again as it seems it's still installed and conflicting.

---

### Post by macogw on 2007-04-26
> **DJiNN said:**
> Has anyone tried Gnomad2 on Xubuntu Feisty at all? I'm just about to install it on my Ubuntu Feisty machine, but i also use Xubuntu on another machine & it would be great if it worked there also. :)

It should work just fine. The base systems are the same.  The only difference is XFCE/GNOME and XFCE uses GTK just like GNOME so you shouldn't even have to install any GTK libraries like you would with KDE.

---

### Post by soctu on 2007-04-29
I have a creative labs Zen V plus. At first gnomad2 found it and listed directories okay. I transfered a file from the Zen to my Computer no problem. I moved to my mp3 folder on the computer side
and gnomad2 disappeared, poof! What I discovered was that if there was more than one mp3 file in the computer directory of gnomad2 it would disappear. If I set that directory as a home directory
for gnomad2 to read it would not even start. My only fix to get it going was to move the mp3 files out of the directory. I transfered  one file to the Zen V plus no problem..but one file in a directory at 
a time is ridiculous.

any help?

](*,) ](*,) ](*,)

---

### Post by Kosh42 on 2007-04-30
Worked fine for me on Feisty....

Cheers,

Kosh42|EFG

---

### Post by Corubia on 2007-05-01
Greetings everyone.  I have a [COLOR="Red"]Zen Vision:M[/COLOR] that I'm trying to set up.  I'm using feisty and I have both gnomad2 2.8.11 & the required libs.

I installed gnomad2 using the tut here.  Thank you :)!  

Everything seems fine, gnomad2 loads, but it says that it cannot find any jukeboxes on the USB bus.  Once you say ok, the dialog box closes.  I can still look at files on the pc, just not on the zen.

Any sugestions? Maybe I have something configured wrong?

Thanks in advance..
pysdo newbie user :)

Corubia

---

### Post by adamsjw2 on 2007-05-01
In Kubuntu Feisty, I finally have Amarok working. If you enable the MTP plugin, you can probably get it to work with most Zen models. Gnomad works also.

---

### Post by ntetreau on 2007-05-01
Corubia are you on Feisty, if so, just use all the packages from the repos.  What does lsusb outputs in a terminal?

Nic

---

### Post by msak007 on 2007-05-01
> **Corubia said:**
> Greetings everyone.  I have a [COLOR=Red]Zen Vision:M[/COLOR] that I'm trying to set up.  I'm using feisty and I have both gnomad2 2.8.11 & the required libs.

I installed gnomad2 using the tut here.  Thank you :)!  

Everything seems fine, gnomad2 loads, but it says that it cannot find any jukeboxes on the USB bus.  Once you say ok, the dialog box closes.  I can still look at files on the pc, just not on the zen.

Any sugestions? Maybe I have something configured wrong?

Thanks in advance..
pysdo newbie user :)

Corubia
It could be a couple of things. First of all as Nic already asked, are you using Dapper, Edgy, or Feisty? Second of all, do "lsusb" or "mtp-detect" return any info about your player? And lastly, did you make sure to run the hotplug script (sudo bash hotplug.sh) to copy the mtp udev rules over and then restart udev?

> **adamsjw2 said:**
> In Kubuntu Feisty, I finally have Amarok working. If you enable the MTP plugin, you can probably get it to work with most Zen models. Gnomad works also.That's because they finally compiled Amarok with MTP support and included libmtp as a dependency. Previous versions for Edgy and Dapper did not include MTP support. For most people, the Feisty repo version of Gnomad / libmtp will work without the need to compile anything.

---

### Post by macogw on 2007-05-01
> **msak007 said:**
> It could be a couple of things. First of all as Nic already asked, are you using Dapper, Edgy, or Feisty? Second of all, do "lsusb" or "mtp-detect" return any info about your player? And lastly, did you make sure to run the hotplug script (sudo bash hotplug.sh) to copy the mtp udev rules over and then restart udev?

That's because they finally compiled Amarok with MTP support and included libmtp as a dependency. Previous versions for Edgy and Dapper did not include MTP support. For most people, the Feisty repo version of Gnomad / libmtp will work without the need to compile anything.

They said Feisty in the post :p  Gnomad in the Feisty repos didn't work for me.  I don't think it's compiled with MTP support.  The Zen Vision M isn't in the rules file by default either.   At least that was the case as of Herd 4.

---

### Post by Corubia on 2007-05-02
> **msak007 said:**
> It could be a couple of things. First of all as Nic already asked, are you using Dapper, Edgy, or Feisty? Second of all, do "lsusb" or "mtp-detect" return any info about your player? And lastly, did you make sure to run the hotplug script (sudo bash hotplug.sh) to copy the mtp udev rules over and then restart udev?

Ntetreau, Msak007: so sorry to have missed not stating that.  I am using Feisty.

lsusb output:

```
Bus 001 Device 002: ID 041e:413e Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000
```

mtp-detect

```
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Could not get device info!
Connection error.
No devices.

```

I did run the hutplug.sh (sudo bash hotplug.sh).  I got:

```
You seem to have udev on your system. Installing udev rules...
You may need additional setup to get correct permissions on your device.
See the INSTALL file for information.
Do you also want to install the old hotplug support (y/n)?
n

```

I restarted udev and it did not give me any errors...

I still get no jukeboxes found on USB bus. *sigh*

Thanks for the reply and I hope I have not gone the other way now and given too much info :).  Still plugging along....

---

### Post by msak007 on 2007-05-02
> **macogw said:**
> They said Feisty in the post :p Gnomad in the Feisty repos didn't work for me. I don't think it's compiled with MTP support. The Zen Vision M isn't in the rules file by default either. At least that was the case as of Herd 4.
Oops, guess I read the post too fast. My mistake :). I'm at work right now so can't verify if the device is in the files, but Corubia's post after yours shows that mtp-detect sees it.
> **Corubia said:**
> Ntetreau, Msak007: so sorry to have missed not stating that. I am using Feisty.
 
lsusb output:
 
```
Bus 001 Device 002: ID 041e:413e Creative Technology, Ltd
Bus 001 Device 001: ID 0000:0000
```
 
mtp-detect
 
```
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Could not get device info!
Connection error.
No devices.

```
 
I did run the hutplug.sh (sudo bash hotplug.sh). I got:
 
```
You seem to have udev on your system. Installing udev rules...
You may need additional setup to get correct permissions on your device.
See the INSTALL file for information.
Do you also want to install the old hotplug support (y/n)?
n

```
 
I restarted udev and it did not give me any errors...
 
I still get no jukeboxes found on USB bus. *sigh*
 
Thanks for the reply and I hope I have not gone the other way now and given too much info :). Still plugging along....
Don't be sorry, it was my mistake as macocgw already pointed out. You did mention using Feisty I just didn't see it :). It seems that libmtp is properly installed, but the mtp-detect output indicates there's a connection error. It detects the device, it just can't create a connection to it because it can't read any info off of it. Does the device currently have any files on it, or have you previously used it under Windows? I know some people have had problems using Gnomad if they had previously used the device under Windows and a format usually resolved it.

---

### Post by macogw on 2007-05-02
You know, my ZVM came with a bad USB cable that could charge it but wouldn't work for transferring files.  Maybe you got a bad one too?

---

### Post by Corubia on 2007-05-02
> **msak007 said:**
> 
Don't be sorry, it was my mistake as macocgw already pointed out. You did mention using Feisty I just didn't see it :). It seems that libmtp is properly installed, but the mtp-detect output indicates there's a connection error. It detects the device, it just can't create a connection to it because it can't read any info off of it. Does the device currently have any files on it, or have you previously used it under Windows? I know some people have had problems using Gnomad if they had previously used the device under Windows and a format usually resolved it.

Yes, the device does have info on it, and it has been used under Windows.  I to have thought about formating it.  its not like I don't have Backups :)  so that maybe something to try.

macogw: Funny enough, I have changed the usb cable as my original one would not sync, just charge.... hmmm

I'll poke around abit more and let ya know what happens. Thanks!

---

### Post by macogw on 2007-05-02
So Creative just makes s****y cables then?

---

### Post by Corubia on 2007-05-02
Ok, so I did not find anything more one settings, so I went ahead and formated the device.
*sigh* still getting the same error in gnomad.  I tried amarok as well as it looks like a nice app and I use it for mp3 playback.  It tries to connect and then just says it "cannot connect to a MTP device"....


maybe I'm just out of luck.  *does not relish the thought of maintaining a virtual windows for portable devices*  I don't know....  

Thank you.

---

### Post by msak007 on 2007-05-03
> **Corubia said:**
> Ok, so I did not find anything more one settings, so I went ahead and formated the device.
*sigh* still getting the same error in gnomad. I tried amarok as well as it looks like a nice app and I use it for mp3 playback. It tries to connect and then just says it "cannot connect to a MTP device"....
 
 
maybe I'm just out of luck. *does not relish the thought of maintaining a virtual windows for portable devices* I don't know.... 
 
Thank you.
Hmm sorry to hear that didn't work. Just out of curiosity, how did you format it? I found some instructions on Creative's web site on how to format the various devices using "Recovery Mode". Here's the link in case you didn't format it this way:
 
[http://193.95.171.84/SRVS/CGI-BIN/WEBCGI.EXE/,/?St=17,E=0000000000220971541,K=7610,Sxi=5,Kb=ww_english_add,VARSET=ws:http://us.creative.com/,Case=obj(4794](http://193.95.171.84/SRVS/CGI-BIN/WEBCGI.EXE/,/?St=17,E=0000000000220971541,K=7610,Sxi=5,Kb=ww_english_add,VARSET=ws:http://us.creative.com/,Case=obj(4794))
 
If that's how you formatted it, I'll try to think of something else.

---

### Post by ntetreau on 2007-05-03
The latest version of MTPfs is working very well for me, Chris Debenham was kind enough to fix some of the bugs that myself and others in the forum found. 

For those who don't know, MTPfs is a fuse filesystem which mounts your MTP MP3 device in a folder in your home directory (in a folder you choose, as long as you have permissions on it), and enables you to browse it in nautilus.

To use Fuse filesystems, you need to be part of the "fuse" group, System>Administration>Users and Groups>Manage Groups, choose "fuse">Properties and make sure your username is ticked. If it wasn't, tick it then logout and login again.
 
Install:


```

sudo aptitude install fuse-utils checkinstall build-essential

wget http://www.adebenham.com/mtpfs/mtpfs-0.4.tar.gz

tar -xvjf mtpfs-0.4.tar.gz

cd mtpfs-0.4
./configure --prefix=/usr
make && sudo checkinstall

mkdir ~/MTP-player
mtpfs ~/MTP-player

```

You should know be able to browse your device.  

To unmout it:
```
fusermount -u ~/MTP-device
```

What is implemented:
    * Browsing Folders
    * Reading files
    * Writing files
    * Browsing playlists
    * Writing playlists
    * Writing music tracks with metadata

What doesn't work:
You cannot rename folders, thus you need to move the already named folder from your computer (the folder can be filled with files already)
You cannot delete using the "move to the Deleted folder".  To enable real "Delete": in Nautilus Edit>Preferences>Behaviour, then choose "Include a Delete command that bypasses Deleted item folder".

Nic

---

### Post by Bobby Digital on 2007-05-05
When I attempt to compile Gnomad I get this message:

No package 'libnjb' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GN_CFLAGS
and GN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I followed the directions to a "T."  

What did I do wrong?

---

### Post by Bobby Digital on 2007-05-05
I was able to get it working by going back through the instructions.  It was all user error.

---

### Post by pingpongboss on 2007-05-06
the new mtpfs version still gives me around a 2 minute lag everytime i try to do something. If I go into a folder through nautilus (say, the Video folder) then the window becomes unresponsive and blackens out under beryl. Clicking on any file also causes massive lag. :(

---

### Post by ntetreau on 2007-05-07
pingpongboss, sorry to hear it's not working well for you.  I do not have the lag you are describing whe i use it.  I have a Microphoto by the way and I am also running beryl.  Are you sure you are plugged in through a usb 2.0 port?  Just a thought.

Nic

---

### Post by Greenstalk on 2007-05-07
I just got a Zen Micro Photo 4GB and can't get past the "No jukeboxes found on USB bus" error.

I had a previous unit for about two days and that one worked, using gnomad2-2.18.12, libmtp-0.1.5, libnjb-2.2.5 under Ubuntu Dapper, all compiled from source---but that unit had disk problems and so I returned it.

This unit, OTOH, won't ever connect---just the "No jukeboxes" error.  I haven't touched the software.  I've tried different cables.  The unit -does- claim to be "docked"  the instant I start gnomad2, so it's clearly talking, and lsusb finds it.  I've tried booting both the Zen and the laptop several times and nothing has helped.

Is there some other version of something I should be running?  Something else I've overlooked?  This unit is running firmware 1.20.01; unfortunately, I don't recall what firmware the other one was running, except that it was probably a year old since it was about that age and its former owner had never updated it.  (And it could still receive FM, so it wasn't running 1.30, which claims to have broken that.)

---

### Post by jbor7755 on 2007-05-08
I was so glad when I found a thread on this...

Anyway. I will get to my problem. Maybe someone here can help me.

I have just now installed gnomad, libnjb and libmtp in the hope of getting the last piece of my jigsaw in place (so I can loose windows all together).

However when I plug my Zen Vision:M into the USB port the Zen freezes and the computer doesn't think anything is plugged in.

Running lsusb takes a while of waiting straight after the Zen is plugged in and the results show nothing but my USB mouse and printer.

A bit frustrating.

There must be a solution though. Especially with all this collective experience here.

Anyone experienced anything similar?

Cheers

---

### Post by ntetreau on 2007-05-08
Greenstack, on what version on Ubuntu are you running?  Does mtp-detect returns anything?

jbor7755, what version of ubuntu are you running, did you ever try your Vision:M on windows by any chance?  Did it work well?  How did you install gnomad, libnjb, etc.

---

### Post by Greenstalk on 2007-05-08
I'm using Dapper; it's up-to-date except for today's patches (last set were a few weeks ago, IIRC).

mtp-detect gives me::

# mtp-detect
Attempting to connect device(s)
PTP: Opening session
LIBMTP PANIC: Could not open session! (Return code 8194)
  Try to reset the device.
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1686
Detect: There has been an error connecting. Exiting

Gnomad2 gives me the same message, except the "Detect" line is replaced by

LIBMTP_Get_First_Device: Error Connecting
PDE device NULL.

Note that I'm running in a root shell just in case it's a permissions issue somewhere.

The Zen went to its "docked" screen as soon as I did this, and is still there.  (It stays there until I physically unplug it from the USB cable.)

Ideas?

---

### Post by macogw on 2007-05-08
It's panicking because there's nothing there according to it.  If lsusb is blank, mtp-detect will *not* work.  Another person and I on here both got nothing when plugging in with the cable it came with.  Creative's cables, therefore, suck.  Try a new USB cable and see if it works.

---

### Post by Greenstalk on 2007-05-08
I believe I said above that lsusb -does- see the device.  Otherwise I wouldn't have bothered even trying gnomad2 yet.  So if it's the cable, it would have to be some data-dependent issue.

So given that lsusb -does- see it (and I could include here the output of -v if anyone thinks it would help), what now?

---

### Post by Greenstalk on 2007-05-08
Oh, and btw, the behavior is identical with its cable, and with the cable for my GPS (which certainly does work with the GPS).

---

### Post by jbor7755 on 2007-05-08
I have Dapper and the same gnomad, libmtp an libnjb as Greenstalk.  I have used it quite successfully under windows (it has about 6-8GB of wma music on there right now).

gnomad was installed using the technique outlined at the begining of this thread.

---

### Post by Greenstalk on 2007-05-08
jbor7755, are you saying that yours -works- under Dapper in that configuration, or -doesn't-?  It's not clear to me.

---

### Post by jbor7755 on 2007-05-09
It doesn't work.
 As I said above, The Zen freezes when it is plugged in to the USB port and the computer doesn't think anything is there (nothing to transfer to).

I have used it successfully under *windows* which is what it is designed for.

---

### Post by jbor7755 on 2007-05-09
A bit more info for you.
mtp-detect at the promt gives

Attempting to connect device(s)

[long pause here]

no devices could be found

---

### Post by ntetreau on 2007-05-09
Greenstalk, just to make it clearer, mtp-detect would output this if it didn't detect an mtp device:

No MTP devices.
No devices.

So, as you said, your device is well detected, but data transfer does not work.  Have you tried that device under windows?  Call me a sceptic, but I do not believe that using it with your GPS cable is a good test.  Do you have a friend who could lend you their Creative cable?  If it is not the cable, it does feel like something is wrong with the device, I would try to format it but I guess if mtp-detect can connect, mtp-format won't either.

jbor7755, the device should work fine both under windows and linux.  The MTP transport protocol is somewhat open and well documented.  As far as I know, there is no difference between it's implementation under windows and linux.  With that said, I would try it one more time under windows just to make sure it is still working well, transferring and all, I mean I cannot see a good reason why your Zen "freezes" when you plug it in the usb port.  Do you have the latest firmware?

---

### Post by ntetreau on 2007-05-09
jbor7755, just a quick thought, didi you copy the libmtp.rules file as per the turorial?

---

### Post by jbor7755 on 2007-05-09
I do not have the latest firmware. I currently have version 1.11.04. I think the latest is 1.20.something.  I will try that tomorrow when i have a better internet connection.

I checked /etc/udev/rules.d and found both nomad.rules and libmtp.rules files there.
I tried modifying nomad.rules with the device and vendor codes provided for my player in mtp.rules but to no avail.

There must be something seriously wrong with this for it to freeze the Zen.

under windows it docks perfectly.

This is the last thing I need before I can get rid of windows. Aaargh! Such a pain.

---

### Post by ntetreau on 2007-05-09
Updating the firmware will hopefully (probably) fix your problems.  My girlfriend Zen Micro wouldn't work with the 1.11 firmware which was a pain to update since I do not have windows.  It worked fine with the 1.20 series firmware.  My Zen MicroPhoto came preloaded with the 1.20 firmware and worked flawlessly.  

Nic

---

### Post by Greenstalk on 2007-05-09
ntetreau:  I've tried both the cable that came with the Zen (a real Zen cable), and my GPS cable.  No change in behavior.  Do you think I need to try a -third- cable?  (I don't -have- a third cable of this type around, unfortunately.)  And why would a bad -cable- show this when lsusb can see the device?

---

### Post by ntetreau on 2007-05-10
greenstalk, to tell you the truth, this is all guess work, I mean your Zen should pretty much work without problems.  Most people in this thread who were having your kind of problems ended up having a bad cable (many), or a bad device  altogether.  Normally, a reformat fixes thing but since you can't pass command to yours...  did you try it lately in windows?

---

### Post by jbor7755 on 2007-05-10
Eureka!

The firmware upgrade worked. It now detects and I can open gnomad and see all the tracks in my player.

Now for some other questions which came to me. What's a good programme for ripping from CD?
How can you rip to MP3 format or WMA and where do you get codecs?
What can you use for converting file formats?
Can you use a Gracenote type program for artist/album/track recognition?

Thanks for all your help

Prosit

---

### Post by macogw on 2007-05-10
> **jbor7755 said:**
> Eureka!

The firmware upgrade worked. It now detects and I can open gnomad and see all the tracks in my player.

Now for some other questions which came to me. What's a good programme for ripping from CD?
How can you rip to MP3 format or WMA and where do you get codecs?
What can you use for converting file formats?
Can you use a Gracenote type program for artist/album/track recognition?

Thanks for all your help

Prosit

I rip with Banshee, but I think it's just going through Sound Juicer.  If you have mp3 codecs installed, you're good to go.

---

### Post by jbor7755 on 2007-05-10
Correct but I don't have them.  How do I get them for Dapper (I also need AVI codec and libdvdcss)?

---

### Post by Greenstalk on 2007-05-10
jbor7755:  What firmware version are you using now?  1.30 seems to be latest, but its release notes claims that that disables the FM receiver.  (You said you were using 1.11 before?)  I'm using 1.20.01 at the moment and don't know if there are any intermediate versions avaliable.

---

### Post by jbor7755 on 2007-05-10
I just got 1.20.02 and it all appears to work. Though I have not yet transfered anything to it.
This firmware appears to be the latest on the creative site. How do you get a hold of the later ones?
I have read about the 1.30 versions and also a 1.60 (which is supposed to give back the record functionality). But trying the link at the sites that advertise these versions just brings up 1.20.02

---

### Post by ntetreau on 2007-05-11
jbor7755, good to hear the upgrade fixed your problem.  As for all your questions, I use Rhythmbox for most of my music needs.  It uses Sound juicer to rip to variabe bitrate mp3.  To do that, install gstreamer0.10-plugin-bad-multiverse, gstreamer0.10-plugin-ugly-multiverse lame and search/install libid3 in synaptic.  Then, you can start Sound juicer, go to  Edit>Preferences, in ripping profiles, choose Edit profiles>New and enter this
name: CD Quality, MP3
pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
ext: mp3
click active, and close
Then, choose your new mp3 profile in the properties box
This is all done more or less automatically in Feisty

If you want to install the latest and greatest from SVN, then you can add MTP support as well ([follow this thread]("http://ubuntuforums.org/showthread.php?t=385371"))

For your other needs, follow this to learn how to install other [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats#head-99259e1841e1e1262f4f71e0c72d5a51b3fb69e9")

Hopefully, a firmware upgrade will fix Greenstalk problems as well, but you seem to be already using the same one.

---

### Post by monomaniacpat on 2007-05-11
Just installed from src with dapper. Gnomad wouldn't checkinstall the first time because of a make error 1 (if I recall correctly.) But I added the usr prefix and it worked second time.

Is it still not possible to use subdirectories with gnomad!? I hate booting up windows just for this. :'(

---

### Post by pingpongboss on 2007-05-11
yea, i'd really love to have gnomad work with folders on the device

---

### Post by roland on 2007-05-12
Thanks a lot for this guide! Once I tried to install this on my old Breezy system, it was a hell of a job. I finally got it working after spending three hours. This time on Dapper, it only took me about 30 minutes, including compile time... Thanks again!

---

### Post by Murwiz on 2007-05-12
I have run through the how-to at the start of this thread, and everything seemed to execute as expected. When I run Gnomad2, however, I get "No jukeboxes found on USB bus".

When I plug in my Creative Zen Nano Plus, I get a window listing its top level contents like a flash drive.

I am running Dapper Drake; this is a 64-bit installation.

---

### Post by catdriver on 2007-05-12
so we have a way to manipulate files on a Zen, has anyone seen, and could point me to any info as to whether or not these can be initialized* without* using a windoze machine?  I have killed two 'pods, and am looking for a flash solution instead.  It has to speak Ubuntu of course...... If this would be better posted to another location please let me know... 
Thanks, cat

---

### Post by ntetreau on 2007-05-13
murwiz, your device is not seen as an MTP device, which is what it needs to be to work with gnomad2.  You might want to consider if you wouldn't want to keep it that way.  I mean, amarok and rhythmbox can both manage files on your sort of device I believe.  If you'd prefer to use it as an MTP device, you can check in your device settings or look for a firmware update.

catdriver, I am not sure what you mean with your question.  Are you looking to buy a new device?  If so, they are numbers of thread on the forum with the plus and minus of every device out there.  What I can say is that MTP based devices like the Creative ones, all work with ubuntu without the need for windowz (unless you just need to double check that it works well under windowz or you want to upgrade the firmware).

---

### Post by ntetreau on 2007-05-13
pingpongboss, quick question ,did you experience the massive lags your described with earlier versions of mtpfs?  Perhaps this could be communicated  to the developper.

---

### Post by Murwiz on 2007-05-13
> **ntetreau said:**
> murwiz, your device is not seen as an MTP device, which is what it needs to be to work with gnomad2.  You might want to consider if you wouldn't want to keep it that way.  I mean, amarok and rhythmbox can both manage files on your sort of device I believe.  If you'd prefer to use it as an MTP device, you can check in your device settings or look for a firmware update.

Well, so far neither amarok nor rhythmbox can see this device. There's nothing in the Zen's settings that mentions MTP or any similar change in the USB interface.

The only way I've been able to get files onto it is from Win2000 using Media Player, and shoveling the files in from a network drive mounted to my Ubuntu system. Not what I want to do ...

---

### Post by ntetreau on 2007-05-13
Murwiz, didi you look if Creative offers a firmware update for your device, perhaps you could look in its description if it would enable an MTP mode?

---

### Post by catdriver on 2007-05-13
> catdriver, I am not sure what you mean with your question. Are you looking to buy a new device?
yes I am looking to buy a new player, I don't need a run down of each model, I pretty much settled on a Creative, I hate 'pods... The gist of my question is whether or not one can perform the basic set up functions, like formatting the memory media, and installling any system file structure etc,procedures that reqire (usually) the installation disks.. Does one need to do the out of box set up on a windoze box,  will it perform under a wine environment, or can it be done useing native linux tools?  This becomes irrelevant at the current time since I am now suffering through a blown upgrade to 6.10, but that's for sure a topic for another section of this forum.

---

### Post by ntetreau on 2007-05-13
Ok, then, you don't need windowz to get the device going, at least  mine worked like a  charm once you have install the MTP libraries (or drivers if you'd prefers), and a media software like gnomad2, amarok, or ultimately rhythmbox which can be used without much efforts.  As for basic player functions like format for exemple, it can be done from the command line, in a terminal.  Actually, if you'd be to install/upgrade to the latest version Feisty Ubuntu, you would get it to work without even touching the command line.

Nic

---

### Post by Murwiz on 2007-05-13
> **ntetreau said:**
> Murwiz, didi you look if Creative offers a firmware update for your device, perhaps you could look in its description if it would enable an MTP mode?

It appears the only firmware upgrade they have is for ... 

Added Features or Enhancements:

    * Adds FM recording (for players with firmware 1.13.03). 

Fixes:

    * Enables your player to detect downloaded audio tracks after your player is formatted using FAT32 (Windows Vista RC1 and above).

---

### Post by catdriver on 2007-05-14
> **ntetreau said:**
> Ok, then, you don't need windowz to get the device going, at least  mine worked like a  charm once you have install the MTP libraries (or drivers if you'd prefers), and a media software like gnomad2, amarok, or ultimately rhythmbox which can be used without much efforts.  As for basic player functions like format for exemple, it can be done from the command line, in a terminal.  Actually, if you'd be to install/upgrade to the latest version Feisty Ubuntu, you would get it to work without even touching the command line.

Nic
most cool.... I'm a reforming 'pod drone (did I mention that?) and they were a royal pain.  I'm up on 7.04 after dealing with the SATA bug(?) and a blown .iso download.  Seems OK hope the code gets claened up, cause I really need that second CD drive....  AHhhh progress! :lolflag:

---

### Post by macogw on 2007-05-14
SATA bug?  If you're referring to everything being /dev/sd* instead of /dev/hd*, that's a feature, not a bug.  It's part of libata, presumably to make read/write times faster.

---

### Post by catdriver on 2007-05-15
> **macogw said:**
> SATA bug?  If you're referring to everything being /dev/sd* instead of /dev/hd*, that's a feature, not a bug.  It's part of libata, presumably to make read/write times faster.
no I'm refering to the "feature" that only allows my system to boot with one HD and one CD drive... otherwise it hangs and drops to a shell saying "job control shut down" or something to that effect... There are a herd of threads here refering to it, but none have with error message in teh headers so they're a pain to find.... 
this was the most informative thread: [http://ubuntuforums.org/showthread.php?t=442737](http://ubuntuforums.org/showthread.php?t=442737)

---

### Post by catdriver on 2007-05-15
> **ntetreau said:**
> Ok, then, you don't need windowz to get the device going, at least  mine worked like a  charm once you have install the MTP libraries (or drivers if you'd prefers), and a media software like gnomad2, amarok, or ultimately rhythmbox which can be used without much efforts.  As for basic player functions like format for exemple, it can be done from the command line, in a terminal.  Actually, if you'd be to install/upgrade to the latest version Feisty Ubuntu, you would get it to work without even touching the command line.

Nic
and true to your word it doesn't need any setup, but I can't get it recognised in Fiesty 7.04 yet....  I just did a clean install, and nothing yet.  Also the version of Amarock in the repos does not *appear* to work straight away.... but then again till I get my machine to see the player I can't be sure.

1 hour later.... 
1 there  appears to be no mpt support native to 7.04 Feisty, the libraries are not shown to be installed by default when I look at package manager..  The libmtp and libnjb listed in the repos are older than the ones listed at the top of this post.
2 This method does not seem to work for 7.04 Feisty.... I get repeated errors with all three methods.  Compiling gnomad2 doesn't want to work with the old libs in the repository.  Compiling libmtp crashes at checkinstall with a different error each time as it tries to overwrite something valuable...... I'm getting seriously annoyed, because this worked great for Dapper, then foolish me I went for an upgrade to Edgy and that crashed..... so here I sit, shiny player and no native support, and my limited abilities are just that limited.........

5 minutes later.... 

RTFM stooopid...
the stuff in teh repos works fine..... like DUH!
so disregard the ranting.
sometimes the easy way just looks to dam easy.....

---

### Post by adamsjw2 on 2007-05-15
murwiz,
I couldn't get it to work in any version of Kubunutu except fiesty. Then both gnomad2 and amarok both worked. I use amarok exclusively not for my Zen V (MTP) as it also captures podcasts. You need to manually add the device and select the MTP plug-in for Zen, Dell, and other devices.

I haven't tried my Ipod shuffle, but I believe it works just as easily with amarok, as it did on Edgy. There's an amarok plugin for it as  well.

Jim A.

---

### Post by Greenstalk on 2007-05-16
To follow up on the problems I was reporting:  I think the unit itself was bad, and I've returned it.

I had initially tried it in an emulated copy of Windows XP under VMware, only to discover that (a) even the Zen software that comes with the unit still couldn't see it, and (b) the emulated copy kept complaining it couldn't find the driver for the Zen even after I ran the installer disk.

So I tried again on a friend's actual non-emulated XP on a different computer.  (b) was no longer a problem, but (a) still was---the Zen SW couldn't see the device and said "Please connect a Zen player to your computer" or some paraphrase of that.

(This may also explain why its clock was months off---I'm guessing that no computer had been able to connect to it for many, many months, and its owner either gave up trying and tried to pass off bad goods, or never figured it out and blamed his computer; I have no way of knowing since this went through an eBay intermediary.)

I could have tried reformatting it via the magic power-on key combination (which might have also helped its 3-4 minute fsck at power-on), but I decided that I just didn't trust this unit at all and I didn't want to waste yet more time screwing around with it.  So the Linux-side SW was probably working (after all, it worked with a previous player), and this particular device just didn't want to talk to anything, using any software, any computer, and any cable.  (Even though it correctly said "docked" when either gnomad2 or Windows tried to talk to it, and even though lsusb -v dumped a huge amount of information from it---so it's probably some sort scrambled-software issue on the player itself, or maybe a weird corrupted filesystem that causes instant failures; I dunno.)  I couldn't even attempt to download new firmware because Windows wasn't seeing it; perhaps there was a way, but the firmware version it was running -had- worked on the earlier unit I tried.

This makes two out of two bad Zen MicroPhotos for me (first had bad disk blocks that caused lots of reseeks, freezes, and hangs; and the second had the problem I posted about last week), so I'm giving up on the MP's.  Sure, they were both used, but if it's that easy for an old one to develop obscure faults, I'll switch either to a flash-based -something- and/or switch to some brand which doesn't require screwy drivers and which I can just look at as a filesystem (either via a USB connection or by inserting an SD card or something).  If anyone has any suggestions, feel free, though I know this particular thread is devoted to Zens.

---

### Post by ntetreau on 2007-05-18
Sorry to hear about your problems Greenstalk.  I've had better luck with the Creative devices, so far 2 Micro without problems.  Good luck with your next device!

Nic

---

### Post by shewbox on 2007-05-29
I get the following error when trying to build Gnomad:

```
[ben@shewbox:~/sandbox/gnomad2-2.8.10$ make
Making all in src
make[1]: Entering directory `/home/ben/sandbox/gnomad2-2.8.10/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ben/sandbox/gnomad2-2.8.10/src'
Making all in doc
make[1]: Entering directory `/home/ben/sandbox/gnomad2-2.8.10/doc'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/ben/sandbox/gnomad2-2.8.10/doc'
Making all in po
make[1]: Entering directory `/home/ben/sandbox/gnomad2-2.8.10/po'
file=`echo ca | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file ca.po
/bin/sh: -o: not found
make[1]: *** [ca.gmo] Error 127
make[1]: Leaving directory `/home/ben/sandbox/gnomad2-2.8.10/po'
make: *** [all-recursive] Error 1

```

Anyone have any ideas? Thanks.

---

### Post by pingpongboss on 2007-05-29
> **ntetreau said:**
> pingpongboss, quick question ,did you experience the massive lags your described with earlier versions of mtpfs?  Perhaps this could be communicated  to the developper.

hey sorry for answering so late. Yes, i did have the lag, ever since you first mentioned it earlier in the thread. (think it was at the .3 version). there's a small chance that it may be my creative player. When browsing through the pictures on the device, there's always a slight lag for thumbnails and a longer lag for full screen images. Nothing like the lag i get from mtpfs though.

I always thought it was because creative players have a weaker CPU than ipods, but now that I think aobut it, I probably made that up and it might or might not be true.

Can someone with a Creative Zen Vision:M test mtpfs? see how it goes

---

### Post by fivenote on 2007-06-04
I compiled mtpfs 0.5 on Ubuntu feisty and connected my Zen Vision M. I'm able to connect OK, browse directories, but I cannot create or delete directories.

When I try to make a directory I get...

```
mkdir test
mkdir: cannot create directory `test': No such file or directory
```

When I connect to a Windows box, I see it actually created the new directory. What's the deal?

---

### Post by haelen on 2007-06-16
When I plug in my Zen, Kubuntu thinks it's a camera. After mounting the error "The process for the camera://usb:005,002 protocol died unexpectedly"

It has previously been working with Gnomad2  and I can't think what I might have installed recently to make it be detected as a camera - nothing hat I know of.

I've now uninstalled gnomad2 and libmp, but won't be around to re-inmstall them until later to day.

I probably *didn't* need to uninstall them, but panicked!


Thanks,
Tim

---

### Post by bsalt on 2007-06-22
For those of you interested, with the latest release of Rhythmbox, you can use your MTP (PlaysForSure) device in Linux with no problems at all. This is a new feature, but it already performs better than Amarok's new MTP support. 

There is an install how-to here:
[http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html](http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html)

---

### Post by kwilliam on 2007-06-24
What exactly do you *mean* when you say "[Rhythmbox's MTP support] performs better than Amarok's new MTP support"?  Don't they both use libmtp5?  (I'm not arguing for either one here, I'm just puzzled as to how that can be, if they're using the same library.)

---

### Post by bsalt on 2007-06-25
I'm sorry, let me elaborate. They do use the same library, but the way they handle the library is different. I have 12 gb of music on my Creative Zen Xtra. When I plug it in and press connect in Amarok, it sits frozen for quite a long time - long enough for me to manually close the program. When I plugged it into Rhythmbox, Rhythmbox scanned my mp3 player and loaded all my songs up in about 15 seconds, where I had Amarok sitting for longer than a minute and still frozen before I shut it down.

I'm sorry about the confusion kwilliam. You can try it yourself, maybe you'll have better luck, but overall Amarok is slower when a lot of music is on a PlaysForSure device. (Note that it may be different for other people, but with my Zen Xtra with 12 gb of music, Amarok was slower.)

---

### Post by atmartin50 on 2007-06-26
Hi All,

I followed the guide's instructions (although I downloaded version 2.8.8 and made the needed adjustments in the corresponding terminal lines) and successfully downloaded gnomad2, but I got this message at the very end:

> atm@atm-laptop:~$ gnomad2
Found non-autodetected device "Creative Zen Touch (MTP mode)" on USB bus...
usb_claim_interface(): Operation not permitted
Connection error.
PDE device NULL.


When I open the program, it tells me "no jukebox found on USB bus." I have a 40GB Creative Zen Touch. Can anyone help me? Many thanks in advance!

---

### Post by atmartin50 on 2007-06-28
Please disregard the last post.

After upgrading from Edgy to Feisty, Gnomad2 (version 2.8.11) works like a charm!:D File transfers seem a bit on the slow side, but that's not a big problem.

---

### Post by ConsumingFire783 on 2007-07-06
I'm very new to linux.  I'm running 7.04 Xubuntu.  I want to get this program running on my computer.  Can anyone just give me a simple tutorial of how to install the tar.gz file?  I'm thoroughly confused right now.

---

### Post by ntetreau on 2007-07-06
ConsumingFire783:  Since you are running (X)ubuntu 7.04, you can now easily instal the two relevant applications, Gnomad2 and Amarok, using Synaptic [System > Administration > Synaptic ].  Search for both gnomad2 and amarok and install them.  They will show up in your Applications > Sound and Video.  

Nic

---

### Post by originalLBA on 2007-07-10
holy crap that sucked hard.  I am running the i686 kernel and have had no end of trouble with this creative zen v-plus.  the rhythmbox method worked well.  i tried amarok and gnomad both of which would not werk.  finally it docks and i am happy.  the only problem is that when i purged rhythmbox it got rid of the icon for f-spot.  any ideas how to make that come back?

---

### Post by andybleaden on 2007-07-23
> **adamsjw2 said:**
> murwiz,
I couldn't get it to work in any version of Kubunutu except fiesty. Then both gnomad2 and amarok both worked. I use amarok exclusively not for my Zen V (MTP) as it also captures podcasts. You need to manually add the device and select the MTP plug-in for Zen, Dell, and other devices.

I haven't tried my Ipod shuffle, but I believe it works just as easily with amarok, as it did on Edgy. There's an amarok plugin for it as  well.

Jim A.

I just upgraded to feisty and still cannot get amarok to recognise my zen extra AND kubuntu now thinks it is a camera

How did you get amarok to start working?

---

### Post by andybleaden on 2007-07-26
> **andybleaden said:**
> I just upgraded to feisty and still cannot get amarok to recognise my zen extra AND kubuntu now thinks it is a camera

How did you get amarok to start working?

Quick update. I have now got Amarok working (hooray!) but still get the Creative Zen Extra and other mp3 detected as cameras

Any ideas?

---

### Post by markeee on 2007-07-30
i have installed gnomad2 and it works it found my device and lists all the media on t-allowing me to transfer to and from!!

rhythmbox/amarok found no devices =[


a quick question tho-does anyone know how can i lay directly off the device? is it possible to mount it, maybe as like a removable hdd?


thanks

mark

---

### Post by andybleaden on 2007-07-31
it is a shame but it does not sem possible after the mtp software (bug) was installed

It would be so much easier to operate and even to update if it could

---

### Post by ntetreau on 2007-07-31
andybleaden, I also get a popup when my Zen microphoto is plugged in asking to import photos.  This doesn't stop it from working with amarok (you need to set it up in amarok, it actually needs configuration, it's not enough to plug in and open amarok) and in gnomad2.  What do you get when you run mtp-detect?

Nic

---

### Post by andybleaden on 2007-08-06
Yes I can now get it working in Amarok which is great at lastIts just a shame i cannot get it to load up as an external hard drive so I update it easier

Will also try the tip you suggested thanks for that. BTW Has anyone here successfully created playlists for Zen Extra yet with Amarok...is it easy to do ?

---

### Post by vivalaimperio on 2007-09-29
I just bought a Creative ZEN (thats ZEN with nothing following) and I've been trying to connect it to my 7.04 Ubuntu box with Gnomad2, Amarok, Rhythmbox and just about every other player that supports libmtp and libnjb, but none recognize the device.  I've used all three successfully with my Microphoto, but none see the ZEN.  I've checked the hardware on my box and it shows the ZEN when its plugged in as well as the Microphoto, so it has me very confused as to what the problem is.

---

### Post by surfingjoe on 2007-09-29
I'm an absolute NOOB to Linux.  And I must first state that I really like Ubuntu so far.  Easy to install and easy to add software.  However, when i followed the instructions posted on this thread, I kept getting errors.  I tried installing gnomad2 using the different methods.  All without success.

However, Synaptic Package Manager I successfully installed all of the components and I was successful communicating with my Zen Vision M player.

My only complaint is that their isn't an automatic synchronization capability.  It would be beautiful if I could have gnomad2 be able to synchronize all files between what I have on my laptop and what is on the player.

---

### Post by megamania on 2007-09-30
> **surfingjoe said:**
> My only complaint is that their isn't an automatic synchronization capability.  It would be beautiful if I could have gnomad2 be able to synchronize all files between what I have on my laptop and what is on the player.
That's the same complaint I have. I also posted it in a different thread (alternatives to Gnomad), with no solution.

I have a 60gb Nomad and it's unbelievably difficult to keep track of what's in it and what's not...

---

### Post by pingpongboss on 2007-09-30
> **megamania said:**
> That's the same complaint I have. I also posted it in a different thread (alternatives to Gnomad), with no solution.

I have a 60gb Nomad and it's unbelievably difficult to keep track of what's in it and what's not...

That's something I'd kill for.

---

### Post by megamania on 2007-10-01
> **pingpongboss said:**
> That's something I'd kill for.
You'd kill for an alternative to Gnomad, or for a 60gb Zen?

If it's the latter, I got it second hand for 70 dollars... definitely not worth killing for. :-)

---

### Post by ntetreau on 2007-10-01
For syncing, you might want to give MTPSync a look:
[http://www.adebenham.com/mtpsync/](http://www.adebenham.com/mtpsync/)

---

### Post by megamania on 2007-10-01
> **ntetreau said:**
> For syncing, you might want to give MTPSync a look:
[http://www.adebenham.com/mtpsync/](http://www.adebenham.com/mtpsync/)
Thanks. Downloaded and installed it.

It looks interesting, but it doesn't see my Zen Xtra ("no device found" when I hit sync or refresh), which is weird because it is correctly recognized by Gnomad.

Any ideas? I'd really like to give it a try...

---

### Post by Creative2 on 2007-10-07
i have gutsy and zen creative micro with the last firmware...i have read this topic but gnomad say always he doesnt detect nothing..

---

### Post by preciousnightmare on 2007-10-28
I also have Gutsy just installed yesterday and also just installed gnomad2. I couldnt for the life of me get my creative zen to work in xp (some crap about MTP device not working) so I tried it in linux and after install gnomad2, I was able to see my songs, recharge and transfer to/fro my pc. So once again linux saves me from getting pissed off that i can no longer use my zen but now i can!

Oh by the way i didnt follow the instructions on the first page, I just installed gnomad2 in synaptic and magic happened I guess.

---

### Post by jinnan_tonnix on 2007-10-29
Using a Creative Zen Touch with Gutsy...

I had some problems with my Zen and Gnomad (Zen wouldn't 'undock' and had to reset it)

I enabled MTP support in RhythmBox and now RhythmBox syncs nicely with the Zen. :)

---

### Post by MotoBruno on 2007-11-07
I'm using Creative Zen Touch with Gutsy too.
RhythmBox and Gnomad2 are ok with my Zen, but they see only 195 songs.
Why this?

Thanks
Bruno

---

### Post by Aybara on 2007-12-16
I bought a Zen yesterday, but can't get it to work on Gutsy. It recognizes my device when I do an lsusb, and the Zen says it is docked. When I try Gnomad2 or mtp-detect, however, I get the following output:


libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

Any help appreciated :-)

---

### Post by ntetreau on 2007-12-16
> **Aybara said:**
> I bought a Zen yesterday, but can't get it to work on Gutsy. It recognizes my device when I do an lsusb, and the Zen says it is docked. When I try Gnomad2 or mtp-detect, however, I get the following output:


libmtp version: 0.2.1

Attempting to connect device(s)
Device 1 (VID=041e and PID=4157) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1806
Detect: There has been an error connecting. Exiting

Any help appreciated :-)

Your device isn't supported by libmtp 0.2.1 but it is by the 0.2.2 and up.  Unfortunately, higher version number will probably break compatibility with Rhythmbox and all.  I'm not sure of your linux skill levels, but in a nutshell you need to follow the "Install from source"instructions on the first post but make sure to download and install install[ libmtp 0.2]("http://downloads.sourceforge.net/libmtp/libmtp-0.2.2.tar.gz?big_mirror=0") and [gnomad]("http://sourceforge.net/project/showfiles.php?group_id=65573&package_id=63060&release_id=535657").

---

### Post by Aybara on 2007-12-16
I reached the same conclusion a couple of hours ago myself. I have compiled v0.2.4 and compiled Gnomad2 and Amarok afterwards, and now I have it working with amarok at least :-)

Thanks for the reply.

---

### Post by Aybara on 2007-12-17
But not all was good...

The Zen hangs when I use amarok to transfer music to it, and gnomad2 won't transfer to it at all. I tried to enable the mtp-plugin in rhythmbox, but it just says "can't enable plugin".

Bah!

Is it possible to mount the player like a drive? I found something called mtpfs, but I'm not sure how good it is. I'm afraid too really f**k things up, since it's a flash player...

---

### Post by ntetreau on 2007-12-17
What is the output of lsusb?  Can you look up your model number on the libmtp webpage to make sure your specific device is supported?

---

### Post by Aybara on 2007-12-18
The device is supported. It was not in 0.2.1, so I had to compile 0.2.4. Now I can connect and see the contents fine, but it's highly unstable. Unsure if amarok or libmtp is to blame, but like I said it ends up with the creative locking up.

How can I get mtp-support in Rhythmbox?

---

### Post by jsteggy on 2007-12-24
> **pingpongboss said:**
> did you try running gnomad2 as sudo? 
I have the same problem. gomad2 runs but doesn't see my ZEN PLUS except when I run gomad2 as sudo. How or what do I need to do to ruin gomad2 as myself?

Thanks. js

---

### Post by SFAOK on 2007-12-24
Right, sorry I haven't read through people's problem histories but I've just got this working and I have to leave to go home for Christmas really really soon!

I just got my Creative Zen 16GB working. I had to install the very latest libmtp (0.2.4) - this resulted in some flakey behaviour, gnomad2 wouldn't work with it properly. I *could* transfer songs with mtp-connect on the command line but this did not seem to properly send tag information correctly (plus, though the tracks would play, the Zen would have no idea how long the track was or where it was in the track- no seeking in other words!)

However, I installed the latest gnomad2 (2.9.0) and things seems to be going across... Yep, just tested it now, mp3s with tags and seeking ability are all there. Very happy :)

Please note that I'm using gnomad2 to transfer my music across manually, I'm not syncing the mp3 player or anything fancy, I don't need to do that so won't be trying - very sorry.

I may write an update to be included in the first post of this thread if the OP is still around...

I should think that both libmtp and gnomad2 will be in Hardy so this will hopefully improve the matter for the next release.

I'll try and help if people also have the Zen and try libmtp 2.4 and gnomad2 2.9.0 - you'll need to build from source as per the OP. Let me know how you get on! :)

---

### Post by Delporte on 2007-12-25
Just thought I would throw in my 2 pennies....
I came across this post trying to find some info as to why my new Zen 16 gig was so unstable with libmtp.
I'm not running Ubuntu ( I run gentoo) but I am experiencing the same exact lockups under gentoo so at least maybe it isn't a distro specific issue.  The problems I'm experiencing is that the player will not undock and only the reset button will get it back like some of the other posters mentioned.  I was only ever able to transfer 22 files successfully at one time, but that was after several tries.  The problem happens trying to transfer files under amarok or trying to transfer using the fuse/mtpfs package (for the one who was asking about mtpfs, this is the only player i'v had problems with when using mtpfs).  I should point out that the 22 files I finally got  to transfer successfully was done using mtpfs--took like 4 tries to get it to go.  Funny thing is if you mount the player using mtpfs, the folder I put those files in and the files themselves don't show up, it just shows an empty Music folder even though the player itself sees and plays them fine and amarok shows them as being there.  Haven't tried gnomad2 with the zen 16 gig as I decided to try KDE (hadn't used it in a long time, still don't like it near as much as gnome but I haven't had time to switch back).  Also, my zen vision:M and my dad's zen V plus 2G and zen microphoto all work with amarak, mtpfs, and gnomad2 (when I had gnome on previously) with no probs.  maybe a zen/libmtp compatibility issue?  You can disregard this if your worried that i'm running gentoo, but I just thought I would throw my experiences out there since I'm battling the same issues. 

Some other problems I had relating to fuse/mtpfs that I was experiencing were:
I tried to transfer a bunch of files, but it only transfered about 6 of them after spitting out errors telling me that the files already existed, then locked up the player (reset button).  Before I finally got the 22 files to go successfully it would transfer about 6 or 7 of them then tell me that it couldn't read the rest because they didn't exist, even though they did, then the player would lock up (reset button). As of this post I haven't tried the libmtp tools themselves directly but if I get time maybe I'll post my experiences.  Sorry, one more thing.  I tried libmtp 0.2.3 and 0.2.4, amarok 1.4.7 and mtpfs 0.7. The FUSE module is built into my kernel--2.6.22. Again, disregard this post if you want, won't hurt my feelings :).  Just hoping this might help someone figure out whats going on.

Let me know if you care for anymore info about what I have and haven't tried.

Later

---

### Post by Papa-san on 2007-12-26
This doesn't seem right...
```
john@john-laptop:~$ sudo aptitude install build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libatk1.0-dev libc6-dev libcairo2-dev libfreetype6-dev libglib2.0-dev
  libgtk2.0-dev libpango1.0-dev libusb-dev zlib1g-dev

``` (There are a lot of suggested solutions, but in allowing them to run, the 'suggested solution leaves me with no progress...

---

### Post by Papa-san on 2007-12-26
Yeah... This process for Dapper fails in step 1, consistently. 

I have tried it with libmtp-0.1.5 and with the current libmtp-0.2.2

```
john@john-laptop:~$ sudo aptitude install build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev checkinstall
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libatk1.0-dev libc6-dev libcairo2-dev libfreetype6-dev libglib2.0-dev
  libgtk2.0-dev libpango1.0-dev libusb-dev zlib1g-dev
The following NEW packages will be automatically installed:
  cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libexpat1-dev
  libfontconfig1-dev libmudflap0 libmudflap0-dev libpng12-dev
  libstdc++6-4.0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxrandr-dev libxrender-dev linux-kernel-headers x-dev x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev
The following NEW packages will be installed:
  build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libexpat1-dev libfontconfig1-dev libid3tag0-dev libmudflap0
  libmudflap0-dev libpng12-dev libstdc++6-4.0-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  linux-kernel-headers x-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev
0 packages upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.8MB of archives. After unpacking 66.9MB will be used.
The following packages have unmet dependencies:
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.11.4-0ubuntu1) but 1.12.3-0ubuntu1 is installed.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but 2.12.4-0ubuntu1 is installed.
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.12.3-0ubuntu3) but 1.14.5-0ubuntu1 is installed.
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1.2) but 1.2.4-1ubuntu2.1 is installed.
  libusb-dev: Depends: libusb-0.1-4 (= 2:0.1.10a-22ubuntu1) but 2:0.1.12-2 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.20-0ubuntu1.1) but 2.10.6-0ubuntu3.1 is installed.
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3-6ubuntu4) but 1:1.2.3-13ubuntu2 is installed.
  libfreetype6-dev: Depends: libfreetype6 (= 2.1.10-1ubuntu2.4) but 2.2.1-5ubuntu0.2 is installed.
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.5) but 2.4-1ubuntu12.3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.0 [Not Installed]
gcc [Not Installed]
gcc-4.0 [Not Installed]
libatk1.0-dev [Not Installed]
libc6-dev [Not Installed]
libcairo2-dev [Not Installed]
libexpat1-dev [Not Installed]
libfontconfig1-dev [Not Installed]
libfreetype6-dev [Not Installed]
libglib2.0-dev [Not Installed]
libgtk2.0-dev [Not Installed]
libid3tag0-dev [Not Installed]
libmudflap0-dev [Not Installed]
libpango1.0-dev [Not Installed]
libpng12-dev [Not Installed]
libstdc++6-4.0-dev [Not Installed]
libusb-dev [Not Installed]
libxft-dev [Not Installed]
zlib1g-dev [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
john@john-laptop:~$ cd gnomad_install
john@john-laptop:~/gnomad_install$ tar -tar -zxvf libmtp-0.2.2.tar.gz
tar: invalid option -- a
Try `tar --help' or `tar --usage' for more information.
john@john-laptop:~/gnomad_install$ tar -zxvf libmtp-0.2.2.tar.gz
libmtp-0.2.2/
libmtp-0.2.2/config.guess
libmtp-0.2.2/libmtp.pc
libmtp-0.2.2/Makefile.in
libmtp-0.2.2/missing
libmtp-0.2.2/TODO
libmtp-0.2.2/ChangeLog
libmtp-0.2.2/examples/
libmtp-0.2.2/examples/emptyfolders.c
libmtp-0.2.2/examples/sendfile.c
libmtp-0.2.2/examples/newfolder.c
libmtp-0.2.2/examples/newplaylist.c
libmtp-0.2.2/examples/Makefile.in
libmtp-0.2.2/examples/files.c
libmtp-0.2.2/examples/getplaylist.c
libmtp-0.2.2/examples/evolution-sync.sh
libmtp-0.2.2/examples/thumb.c
libmtp-0.2.2/examples/sendtr.c
libmtp-0.2.2/examples/pathutils.c
libmtp-0.2.2/examples/playlists.c
libmtp-0.2.2/examples/common.h
libmtp-0.2.2/examples/tracks.c
libmtp-0.2.2/examples/format.c
libmtp-0.2.2/examples/trexist.c
libmtp-0.2.2/examples/reset.c
libmtp-0.2.2/examples/hotplug.c
libmtp-0.2.2/examples/Makefile.am
libmtp-0.2.2/examples/albums.c
libmtp-0.2.2/examples/detect.c
libmtp-0.2.2/examples/connect.c
libmtp-0.2.2/examples/getfile.c
libmtp-0.2.2/examples/albumart.c
libmtp-0.2.2/examples/delfile.c
libmtp-0.2.2/examples/folders.c
libmtp-0.2.2/examples/pathutils.h
libmtp-0.2.2/AUTHORS
libmtp-0.2.2/README.windows.txt
libmtp-0.2.2/README
libmtp-0.2.2/depcomp
libmtp-0.2.2/configure
libmtp-0.2.2/INSTALL
libmtp-0.2.2/install-sh
libmtp-0.2.2/configure.ac
libmtp-0.2.2/Makefile.am
libmtp-0.2.2/m4/
libmtp-0.2.2/m4/byteorder.m4
libmtp-0.2.2/m4/stdint.m4
libmtp-0.2.2/config.h.in
libmtp-0.2.2/doc/
libmtp-0.2.2/doc/Makefile.in
libmtp-0.2.2/doc/mainpage.h
libmtp-0.2.2/doc/Makefile.am
libmtp-0.2.2/doc/examples.h
libmtp-0.2.2/doc/Doxyfile.in
libmtp-0.2.2/config.sub
libmtp-0.2.2/libmtp.sh.in
libmtp-0.2.2/COPYING
libmtp-0.2.2/ltmain.sh
libmtp-0.2.2/src/
libmtp-0.2.2/src/Makefile.in
libmtp-0.2.2/src/util.c
libmtp-0.2.2/src/libusb-glue.c
libmtp-0.2.2/src/README
libmtp-0.2.2/src/ptp.h
libmtp-0.2.2/src/Makefile.am
libmtp-0.2.2/src/unicode.c
libmtp-0.2.2/src/unicode.h
libmtp-0.2.2/src/util.h
libmtp-0.2.2/src/libmtp.sym
libmtp-0.2.2/src/ptp.c
libmtp-0.2.2/src/libptp-stdint.h
libmtp-0.2.2/src/gphoto2-endian.h
libmtp-0.2.2/src/libmtp.h.in
libmtp-0.2.2/src/ptp-pack.c
libmtp-0.2.2/src/libusb-glue.h
libmtp-0.2.2/src/libmtp.c
libmtp-0.2.2/src/libmtp.h
libmtp-0.2.2/libmtp.pc.in
libmtp-0.2.2/hotplug.sh.in
libmtp-0.2.2/libmtp.sh
libmtp-0.2.2/aclocal.m4
john@john-laptop:~/gnomad_install$ cd libmtp-0.2.2
john@john-laptop:~/gnomad_install/libmtp-0.2.2$ ./configure --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
john@john-laptop:~/gnomad_install/libmtp-0.2.2$ sudo make
make: *** No targets specified and no makefile found.  Stop.
john@john-laptop:~/gnomad_install/libmtp-0.2.2$ sudo checkinstall

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist.
Should I create a default set of package docs?  [y]:

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> gnomad failure #2
>>

*****************************************
**** Debian package creation selected ***
*****************************************
/usr/bin/checkinstall: line 1151: dpkg-architecture: command not found

This package will be built according to these values:

0 -  Maintainer: [ root@john-laptop ]
1 -  Summary: [ gnomad failure #2 ]
2 -  Name:    [ libmtp ]
3 -  Version: [ 0.2.2 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ libmtp-0.2.2 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue:

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

john@john-laptop:~/gnomad_install/libmtp-0.2.2$ sudo bash hotplug.sh
bash: hotplug.sh: No such file or directory
john@john-laptop:~/gnomad_install/libmtp-0.2.2$ sudo cp libmtp.rules /etc/udev/rules.d/
cp: cannot stat `libmtp.rules': No such file or directory
john@john-laptop:~/gnomad_install/libmtp-0.2.2$ sudo aptitude install build-essential libxml-perl libid3tag0-dev libusb-dev libgtk2.0-dev checkinstall
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  libatk1.0-dev libc6-dev libcairo2-dev libfreetype6-dev libglib2.0-dev
  libgtk2.0-dev libpango1.0-dev libusb-dev zlib1g-dev
The following NEW packages will be automatically installed:
  cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0 libexpat1-dev
  libfontconfig1-dev libmudflap0 libmudflap0-dev libpng12-dev
  libstdc++6-4.0-dev libx11-dev libxau-dev libxcursor-dev libxdmcp-dev
  libxext-dev libxfixes-dev libxft-dev libxi-dev libxinerama-dev
  libxrandr-dev libxrender-dev linux-kernel-headers x-dev x11proto-core-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev
The following NEW packages will be installed:
  build-essential cpp cpp-4.0 dpkg-dev g++ g++-4.0 gcc gcc-4.0
  libexpat1-dev libfontconfig1-dev libid3tag0-dev libmudflap0
  libmudflap0-dev libpng12-dev libstdc++6-4.0-dev libx11-dev libxau-dev
  libxcursor-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev
  linux-kernel-headers x-dev x11proto-core-dev x11proto-fixes-dev
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev
  x11proto-xext-dev x11proto-xinerama-dev
0 packages upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 17.8MB of archives. After unpacking 66.9MB will be used.
The following packages have unmet dependencies:
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.11.4-0ubuntu1) but 1.12.3-0ubuntu1 is installed.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.3-0ubuntu1) but 2.12.4-0ubuntu1 is installed.
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.12.3-0ubuntu3) but 1.14.5-0ubuntu1 is installed.
  libcairo2-dev: Depends: libcairo2 (= 1.0.4-0ubuntu1.2) but 1.2.4-1ubuntu2.1 is installed.
  libusb-dev: Depends: libusb-0.1-4 (= 2:0.1.10a-22ubuntu1) but 2:0.1.12-2 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.8.20-0ubuntu1.1) but 2.10.6-0ubuntu3.1 is installed.
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3-6ubuntu4) but 1:1.2.3-13ubuntu2 is installed.
  libfreetype6-dev: Depends: libfreetype6 (= 2.1.10-1ubuntu2.4) but 2.2.1-5ubuntu0.2 is installed.
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.5) but 2.4-1ubuntu12.3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
build-essential [Not Installed]
g++ [Not Installed]
g++-4.0 [Not Installed]
gcc [Not Installed]
gcc-4.0 [Not Installed]
libatk1.0-dev [Not Installed]
libc6-dev [Not Installed]
libcairo2-dev [Not Installed]
libexpat1-dev [Not Installed]
libfontconfig1-dev [Not Installed]
libfreetype6-dev [Not Installed]
libglib2.0-dev [Not Installed]
libgtk2.0-dev [Not Installed]
libid3tag0-dev [Not Installed]
libmudflap0-dev [Not Installed]
libpango1.0-dev [Not Installed]
libpng12-dev [Not Installed]
libstdc++6-4.0-dev [Not Installed]
libusb-dev [Not Installed]
libxft-dev [Not Installed]
zlib1g-dev [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?]

```If I accept the offered solutions, it still fails.

---

### Post by stoian on 2008-01-24
I installed everything as stated in the article, in Dapper, using latest packages from sourceforge.net website.

I have a Zen Micro.

When I run Gnomad2 as a normal user, I get the infamous "**No jukeboxes found on USB bus.**" message.

If I run as superuser (sudo gnomad2) it works ok, but i'd like to solve this problem because i don't want to be running gnomad2 as superuser all the time.

on this site: [http://help.lockergnome.com/linux/USB-Operation-permitted-ftopict488961.html]("http://help.lockergnome.com/linux/USB-Operation-permitted-ftopict488961.html") somebody suggested

"See what happens if you just hookup device without starting gnomad2. Look
in /var/log/messages. The relevant lines will be at the end of file so you
can start console and run
```
tail -f /var/log/messages
```
then connect Zen. Then if device is recognized run gnomad2 first as user and
then as root, and watch what is going on in console."

well, when i run gnomad2 as user, i tail those messages, i get:

```
usb 4-3: new high speed USB device using ehci_hcd and address 2
```

and, when i run as superuser/sudo, i get:

```
usb 4-3: reset high speed USB device using ehci_hcd and address 2
```

See the difference? It's just one word.
In case of a normal user is **"new"**, while as a superuser is **"reset"**.

This must be some clue, if anybody has an idea how to do a "reset" when running as a normal user, please post here.

Thank you.

---

### Post by andrewjoy on 2008-01-25
The steps above are helpful  i have files going to my Vision M just fine.

Has anyone found a way to create directories on the device through Gnomad2?

If i get this little problem sorted i will be a happy bunny.

On another note anyone who has a vision M or any other video player will be happy to know there is a useful program out there to get your files the correct format and resolution for your device. it is called iriverter i used it on windows and was happy to find there was a linux version You can install it though the packet manager or compile it.

[http://iriverter.sourceforge.net/index.shtml](http://iriverter.sourceforge.net/index.shtml)

[http://packages.ubuntu.com/feisty/graphics/iriverte](http://packages.ubuntu.com/feisty/graphics/iriverte)

---

### Post by Kenniej on 2008-03-16
Nice , method 1 worked like a charm ^^

Thnx for the tut sir !!

Grtz
Kenniej

---

### Post by LinuxMonk on 2008-04-13
I guess I'll just have to wait until 8.04 comes out.  I've done everything recommended, and I get the following from gnomad2:

PTP: Opening Session
ptp2/ptp_usb_getdata: detected a broken PTP header, code field insane, expect problems!  (But continuing)
PTP: Sequence number mismatch -771632894 vs expected 1.
LIBTMP PANIC: Unable to read device information on device number 1, trying to continue
LIBMTP_Get_First_Device: Error Connecting
PDE device NULL

I ran lsusb, and got this:

Bus 001  Device 015:  ID  041e:4157 Creative Technology, Ltd
Bus 001  Device 001:  ID  0000:0000

Running Ubuntu 7.10.

*sigh*

---

### Post by Literati on 2008-04-13
> **LinuxMonk said:**
> I guess I'll just have to wait until 8.04 comes out.  I've done everything recommended, and I get the following from gnomad2:

PTP: Opening Session
ptp2/ptp_usb_getdata: detected a broken PTP header, code field insane, expect problems!  (But continuing)
PTP: Sequence number mismatch -771632894 vs expected 1.
LIBTMP PANIC: Unable to read device information on device number 1, trying to continue
LIBMTP_Get_First_Device: Error Connecting
PDE device NULL

I ran lsusb, and got this:

Bus 001  Device 015:  ID  041e:4157 Creative Technology, Ltd
Bus 001  Device 001:  ID  0000:0000

Running Ubuntu 7.10.

*sigh*

try running Gnomad2 as root.

---

### Post by LinuxMonk on 2008-04-13
Did that - no joy.

---

### Post by Literati on 2008-04-13
> **LinuxMonk said:**
> Did that - no joy.

Okay, you'll have to excuse me, but I'm just joining your problem, so I'm not sure what you've gone through. But I literally just got my Zen working, so I feel I can help you.

Do you have Hotplug enabled and libnjb installed with libusb?

---

### Post by LinuxMonk on 2008-04-13
Aha!  I had run the hotplug.sh script, but I don't have libsub.  I'll get that and try again.

Back in a few...

---

### Post by LinuxMonk on 2008-04-13
Erp...correction...I already have libusb...*bleah*

---

### Post by LinuxMonk on 2008-04-14
Things just get better and better - I thought just maybe my laptop had a hardware issue with the Zen, so I moved to my desktop, and went through the steps for Edgy (the first version).  Same sad song:

Device 1 (VID=041e and PID=4157) is UNKNOWN
Please report ...
PTP: Opening session
LIBMTP PANIC: Could not get device info!
LIBMTP PANIC: configure_usb_devices() error code:  7 on line 1806
LIBMTP_Get_First_Device: Error Connecting
PDE device NULL.

Executing lsusb returns this:

Bus 002 Device 006:  ID 041e:4157 Creative Technology, Ltd
Bus 002 Device 001:  ID 0000:0000
Bus 001 Device 001:  ID 0000:0000

As Bill the Cat might say, "Aacckk!"

---

### Post by LinuxMonk on 2008-04-15
Btt

---

### Post by shazzy on 2008-04-26
I wonder if you're having an IRQ conflict?  I had an IRQ conflict when I connected my Zen to my Windows machine.  I'm hoping I won't have that problem with Linux.  I'm not optimistic though since I think IRQ is not an OS issue.  I never really did figure out how to resolve the IRQ conflict.

---

### Post by DeliriousNor on 2008-05-08
I have been using Gnomad 2 with my creative zen vision:m, but I hate the fact that I am not able to sync folders only single files to my mp3-players. The newest version of gnomad2 has support for this. Is there an easy way to get it? Or do you think the current gnomad2 version in hardy will be upgraded?

---

### Post by imopen on 2008-06-19
> **DeliriousNor said:**
> I have been using Gnomad 2 with my creative zen vision:m, but I hate the fact that I am not able to sync folders only single files to my mp3-players. The newest version of gnomad2 has support for this. Is there an easy way to get it? Or do you think the current gnomad2 version in hardy will be upgraded?

[http://ubuntuforums.org/showthread.php?t=695381](http://ubuntuforums.org/showthread.php?t=695381)

there is an archive .tar.gz that include new deb packages to install ;)

---

### Post by frodon on 2008-07-23
BTW anyone tried to run the creative zen software provided with wine ?

---

