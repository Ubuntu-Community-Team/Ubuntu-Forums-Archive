---
title: "Canon PIXMA ip1800 Installation Issue"
date: 2008-07-05
forum: Hardware
---

### Post by Infatuas on 2008-07-05
Hello Everyone,

Well i decided to try an install my printer. I plugged it in it knew what it was but when i was selecting the driver it looks like there is every PIXMA ip**** series printer but mine. I decided to select the closest model which was the ip2000 but sure enough it didn't work. Any ideas on how i can get this working?

---

### Post by prshah on 2008-07-05
> **Infatuas said:**
> 
but when i was selecting the driver it looks like there is every PIXMA ip**** series printer but mine. 


see [http://ubuntuforums.org/showpost.php?p=4846214&postcount=42](http://ubuntuforums.org/showpost.php?p=4846214&postcount=42)

Don't forget to post your thanks (there, I mean) by hitting the blue ribbon/gold star to the bottom right of the message.

---

### Post by SteveDee on 2008-11-04
I've been happily using my iP1800 with Hardy for a few months using the debs by Jerryf (many, many thanks jerry).

But after upgrading to 8.10 it no longer wants to play.

So 2 questions;
1) should it still work with the Hardy drivers on 8.10?
If not 2) has anyone found debs for 8.10?

---

### Post by Naegling23 on 2008-11-05
mine was working fine under hardy, but no longer works in intrepid.  The printer is recognized, it just doesnt print.  Im guessing we need some intrepid drivers for this printer, since its popular, its bound to happen, but this is frustrating loosing a printer after every upgrade.

---

### Post by SteveDee on 2008-11-06
> **Naegling23 said:**
> mine was working fine under hardy, but no longer works in intrepid.  The printer is recognized, it just doesnt print.  Im guessing we need some intrepid drivers for this printer, since its popular, its bound to happen, but this is frustrating loosing a printer after every upgrade.

OK, I've got my iP1800 working on Intrepid 8.10!

If upgraded from 8.04 then:-
download from: [http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20iP1880%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&](http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20iP1880%0Amenu%3d%3dDownload%0Aos%3d%3dLinux&)
the IJ Printer Driver Ver. 2.70 for Linux (rpm Package for iP1800 series) 

As this is an RPM package we need to install Alien to convert it to a deb

In terminal window:-
steve@davis-desktop:~$ sudo apt-get install alien

Remove any packages no longer required:-
steve@davis-desktop:~$ sudo apt-get autoremove

Now convert:-
steve@davis-desktop:~$ sudo alien -k cnijfilter-ip1800series-2.70-1.i386.rpm
(this assumes the rpm is in your Home directory)

You may need to go to System > Administration > Printing
to reconfigure your printer and run Print Test Page

Hope this works for you Naegling23.

If 8.10 is a fresh install (i.e. not an upgrade) you will also need the cnijfilter-common-2.70-1.i386.rpm

Convert & install this in the same way (not tested, as I haven't had to do this).

---

### Post by SteveDee on 2008-11-06
Sorry, missed out the most important line, installing the driver.


Now convert:-
steve@davis-desktop:~$ sudo alien -k cnijfilter-ip1800series-2.70-1.i386.rpm
(this assumes the rpm is in your Home directory)

Now install:-
steve@davis-desktop:~$ sudo dpkg -i cnijfilter-ip1800series_2.70-1_i386.deb

You may need to go to System > Administration > Printing
to reconfigure your printer and run Print Test Page

---

### Post by Naegling23 on 2008-11-06
hmmm, still doesnt seem to be working for me.  I'll try a few things and ill let you know if I get it to work.

---

### Post by Naegling23 on 2008-11-07
nope, cant seem to get this to work, does anyone have any suggestions?

---

### Post by SteveDee on 2008-11-10
This weekend I took a second computer, did a clean install of 8.10 and used my method above to install drivers. I was surprised to find I could not print.

So I did a fresh install of 8.04, applied all the updates and installed the drivers. I could print at this stage. So then I upgraded to 8.10 and added the driver again, now it won't print.

I've wasted hours looking for differences between the printer friendly computer #1 & the non-printing computer#2. I've looked at any .conf that may be printer related. I've checked cups & ghostprint installed packages, but just can't find a difference which fixes the problem.

The only glimmer of hope is that I have a working computer, so its possible, and I'm sure someone out there has the answer.

The system(cups) does recognise that there is a Canon iP1800 connected, and it shows the status (i.e. "idle", "processing" & so on). But the printer won't print!

If anyone has any suggestions re: files to copy from computer #1 to #2 I'll happily give it a try.

---

### Post by N'ko on 2008-11-11
I have gotten the ip1800 working with intrepid!! or at least mostly working.  Here is how I did it.

Download cnijfilter-common_2.70-2_i386.deb and cnijfilter-ip1800_2.70-2_i386-hardy.deb

From here: [http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/](http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/)

cnijfilter-ip1800_2.70-2_i386-hardy.deb will not install because of failure to resolve a dependency.

So now edit the dependencies in cnijfilter-ip1800_2.70-2_i386-hardy.deb so that it will install; using this method: [http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Now you can install your printer as normal under administration-->printing.

After installing the driver, printer prints normally. "Canon Pixma iP1800 series" appears in system-->preferences but does not open when clicked on.  I have not found away to switch the printer to only print in gray-scale.

Update: November 12, 2008
Sorry I forgot about the issue of the package not finding /etc/init.d/cupsys.

It seems that there is a transition in package names, the old name was cupsys and new one is cups.  What I did was create a new file in /etc/init.d and called it "cupsys".  I then copied the contents of /etc/init.d/cups using gedit into my new file called cupsys.  I don't know if it is necessary to copy the contents of "cups" or if a dumpy file is just needed.  

It would be nice if someone with more knowledge could re-package the driver for Intrepid but until then this seems to get the printer working.

---

### Post by Naegling23 on 2008-11-11
N'ko, glad to know you have it working...would it be possible for you to post the edited packages?

---

### Post by N'ko on 2008-11-12
Here are the two files that I use to install ip1800 printer.  The first one I edited the required dependencies so that it would install, the other remains unchanged.


[http://nko.computers.googlepages.com/cnijfilter-ip1800_2.70-2_i386-hardy..deb](http://nko.computers.googlepages.com/cnijfilter-ip1800_2.70-2_i386-hardy..deb)

[http://nko.computers.googlepages.com/cnijfilter-common_2.70-2_i386.deb](http://nko.computers.googlepages.com/cnijfilter-common_2.70-2_i386.deb)

---

### Post by Naegling23 on 2008-11-12
thanks, ill try these out tonight when I get home!

---

### Post by SteveDee on 2008-11-12
> **N'ko said:**
> I have gotten the ip1800 working with intrepid!! or at least mostly working.  Here is how I did it.

Download cnijfilter-common_2.70-2_i386.deb and cnijfilter-ip1800_2.70-2_i386-hardy.deb

From here: [http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/](http://www.gnupanama.com/error-en-canon-ip1300-causa-cups-solucionado/2008/10/20/)

cnijfilter-ip1800_2.70-2_i386-hardy.deb will not install because of failure to resolve a dependency.

So now edit the dependencies in cnijfilter-ip1800_2.70-2_i386-hardy.deb so that it will install; using this method: [http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

Now you can install your printer as normal under administration-->printing.

After installing the driver, printer prints normally. "Canon Pixma iP1800 series" appears in system-->preferences but does not open when clicked on.  I have not found away to switch the printer to only print in gray-scale.

Thanks great! I can now print from my troublesome computer.

Do you have any idea what causes this error when I install your deb:-

Selecting previously deselected package cnijfilter-ip1800series.
(Reading database ... 113457 files and directories currently installed.)
Unpacking cnijfilter-ip1800series (from cnijfilter-ip1800_2.70-2_i386-hardy..deb) ...
Setting up cnijfilter-ip1800series (2.70-2) ...
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
dpkg: error processing cnijfilter-ip1800series (--install):
 subprocess post-installation script returned error exit status 100
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-ip1800series

---

### Post by N'ko on 2008-11-12
Sorry I forgot about the issue of the package not finding /etc/init.d/cupsys.

It seems that there is a transition in package names, the old name was cupsys and new one is cups.  What I did was create a new file in /etc/init.d and called it "cupsys".  I then copied the contents of /etc/init.d/cups using gedit into my new file called cupsys.  I don't know if it is necessary to copy the contents of "cups" or if a dumpy file is just needed.  

It would be nice if someone with more knowledge could re-package the driver for Intrepid but until then this seems to get the printer working.

---

### Post by Naegling23 on 2008-11-12
thanks n'ko, it works!!!!!  Hopefully we can get the option to print greyscale, but at least its a working printer

FYI
open a terminal in the folder /etc/init.d
type the following: sudo cp cups cupsys

then install the two packages listed above.

---

### Post by Reteip on 2008-11-13
Thank you N´ko!!
I spent a couple of long nights trying to figure this out, and I don´t have the skills to edit package files like you do.

Also thanks to Naegling23 for instructions on renaming cups to cupsys.
I then changed it back to cups - in case changed name might negatively effect future cups updates.
I´m not too good in the Terminal, so used another instruction
Press: Alt & F2
Type: gksudo nautilus

This opens nautilus as root (administrator)
I then renamed the file in filesystem /etc/init.d

Cheers!

---

### Post by prshah on 2008-11-13
> **Reteip said:**
> 
Also thanks to Naegling23 for instructions on renaming cups to cupsys.
I then changed it back to cups - in case changed name might negatively effect future cups updates.
I´m not too good in the Terminal, so used another instruction
Press: Alt & F2
Type: gksudo nautilus

This opens nautilus as root (administrator)
I then renamed the file in filesystem /etc/init.d


First off, you should avoid using nautilus as root. 

Secondly, rather than rename the files, why not just create a symbolic (soft) link? That way, both cups and cupsys will work fine for you. To do this, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo ln -s /etc/init.d/cups /etc/init.d/cupsys
``` The effective permissions on the link will be that of the original (target) file.

---

### Post by Reteip on 2008-11-14
Ok, thanks prshah.

I checked and sure enough there is a second file called cupsys.

Cheers

---

### Post by N'ko on 2008-11-14
Gray-scale printing working on IP1800 under Intrepid!! 

I found this link here on how to get the printer to print gray scale.
[http://loginspires.livejournal.com/2033.html](http://loginspires.livejournal.com/2033.html)

You need to edit the postscript printer description file found here:
 /usr/share/cups/model/custom/canonip1800.ppd

Our you can just replace it with mine attached to this post.

Once you change the file you must un-install the printer and re-install the printer in order for the changes to work.  Once you have done that you will find an option in "print properties" under "print options" to print gray-scale.  I also added some more options for output resolutions.  Unfortunately they are all marked "1200" but in reality the first "1200" is 1200x1200 the second 1200x2400 and the third 1200x4800.

Happy printing!

---

### Post by mx32 on 2008-11-20
Hello, I a new linux user. I have read this post but frankly, I got lost. The instructions have been changing as new issues arise. Would some one make a summary with the current instructions to make ip1800 to work on 8.10? Thanks. :confused:

---

### Post by Malta paul on 2008-11-20
Hi,
Just download the to files in post #12.

[http://nko.computers.googlepages.com...386-hardy..deb](http://nko.computers.googlepages.com...386-hardy..deb)

[http://nko.computers.googlepages.com....70-2_i386.deb](http://nko.computers.googlepages.com....70-2_i386.deb)


Then go to the terminal at 'Applications>Accessories>Terminal and past in the line below [Taken from post 18]

sudo ln -s /etc/init.d/cups /etc/init.d/cupsys 

press enter, you will be asked for your password ( Note: when you type it in, it will stay blank)


Now go back to the .deb files you downloaded, right click you mouse, then press 'Install package' Do this with both downloaded files.

Reboot with your printer switched on.

Now you should be able to use your printer :)

---

### Post by mx32 on 2008-11-22
Thanks Paul,
for this easy to follow instructions.
Printer is working as expected.
Regards.

---

### Post by mdille on 2008-12-01
Thanks to Malta paul for your help.  Following your post did the trick.  I've spent way too much time trying to get my ip1800 working.  I've worked in the MS Windows world for years and have been trying out Ubuntu to see if it's an alternative for my computing needs.  I like much of what I see in Ubuntu, but it still amazes me how difficult it is to get various devices to work.  I've also spent a lot of time getting my video card and monitor to work properly.  I can see why many users just give up and go back to Windows.  However, I'll keep plugging away at it.  Thanks again.

---

### Post by SteveDee on 2008-12-02
> **mdille said:**
> Thanks to Malta paul for your help.  Following your post did the trick.  I've spent way too much time trying to get my ip1800 working.  I've worked in the MS Windows world for years and have been trying out Ubuntu to see if it's an alternative for my computing needs.  I like much of what I see in Ubuntu, but it still amazes me how difficult it is to get various devices to work.  I've also spent a lot of time getting my video card and monitor to work properly.  I can see why many users just give up and go back to Windows.  However, I'll keep plugging away at it.  Thanks again.

Hey! Stick with it!

I converted my home computers (and my family) to Ubuntu about 6 months ago, and I honestly believe its a more stable system than the expensive alternatives. The main desktop apps that most people seem to use (in our case; Firefox, Thunderbird, Open Office, Gimp, SMPlayer & Skype) work very well.

Some peripherals are a problem to get going because the manufacturers don't provide the same level of support that they do for Windows. So when my iP1800 eventually dies, I won't be looking to Canon to provide a replacement. That said, its working fine with Linux thanks to the support available from these forums.

Although I've invested a few hours getting the system running the way I want it, my family just use it. I think their main complaint is when they can't access a memory stick after switching users. But I spend far less time sorting out their problems now, than I did when we were running XP.

---

### Post by katrotz on 2009-01-30
thanks gyus, Canon IP1800 worked for me on kubuntu interpid 8.10 after 7 hours on installing x).
actually i crossed all the forums regarding this problem. Mostly there was described the hardy driver instalation, while on interpid it was failing for some dependencies(mainly for libxml1 that i could not install)

now i downloaded the drivers with the dependeces edited and instaled them. the printer works also with colors, not only grayscale :D

just to corect Malta paul´s post, as the links seem to be broken. copy the packages from post #12:

[http://nko.computers.googlepages.com/cnijfilter-ip1800_2.70-2_i386-hardy..deb](http://nko.computers.googlepages.com/cnijfilter-ip1800_2.70-2_i386-hardy..deb)

[http://nko.computers.googlepages.com/cnijfilter-common_2.70-2_i386.deb](http://nko.computers.googlepages.com/cnijfilter-common_2.70-2_i386.deb)

---

### Post by hostilejosh on 2009-03-14
My IP1800 is now working under intrepid with n'ko's drivers and putting a symbolic link for cupsys thank you! wahey!

---

### Post by tooCanad on 2009-03-21
Just came across your post. I went through something similar a while back trying to get the printer to run on 64bit. Just out of curiosity, are you running 32 or 64 bit?

---

### Post by 5ive on 2009-04-04
Canon IP1800 works fantastically on Ubuntu 8.10 (32BIT & 64 BIT). I have not run the printer on Ubuntu 9.04. Does anyone managed to run it on the latest system?

---

### Post by Jerm993 on 2009-04-12
hello all, I've read through all of the posts on this thread as well as others however all i get when i send the test print is Processing-Remote host did not accept data file(1). 
My setup:
I'm running intreped with all of the updates
im trying to share the printer with my desktop and my parents Vista machine
(note: the printer is plugged into the Vista Machine through a usb cable)
I followed mostly these steps, as well as ones found within the forums here-
[http://www.swerdna.net.au/linhowtosambaprint.html](http://www.swerdna.net.au/linhowtosambaprint.html)
and im using Jakes modified Driver for the printer

I'am also fairly new to the ubuntu coding but i think i've got the basics down any and all help i can get would be appreciated;post here or email me at:
[email]Jcc.993@gmail.com[/email]

Thanks, 
Jerm

---

### Post by tstirrat on 2009-04-14
I'm new to Ubuntu and I'm trying to get my ip1800 to work in 8.10 Intrepid. So far, I've downloaded both of the packages posted by Nko and installed one of them. The other one fails to install. This is the error I get:
```
dpkg: dependency problems prevent configuration of cnijfilter-ip1800series:
 cnijfilter-ip1800series depends on libgtk1.2 (>= 1.2.10-4); however:
  Package libgtk1.2 is not installed.
 cnijfilter-ip1800series depends on libxml1 (>= 1:1.8.14-3); however:
  Package libxml1 is not installed.
 cnijfilter-ip1800series depends on cupsys (>= 1.2.8); however:
  Package cupsys is not installed.
dpkg: error processing cnijfilter-ip1800series (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-ip1800series
stirrat@Rally200:~/Desktop$ cd ..
stirrat@Rally200:~$ sudo ln -s /etc/init.d/cups /etc/init.d/cupsys
ln: creating symbolic link `/etc/init.d/cupsys': File exists
stirrat@Rally200:~$ sudo apt get libgtk1.2
sudo: apt: command not found
stirrat@Rally200:~$ man apt
stirrat@Rally200:~$ sudo apt-get libgtk1.2
E: Invalid operation libgtk1.2
stirrat@Rally200:~$ sudo dpkg -i cnijfilter-ip1800_2.70-2_i386-hardy.deb
dpkg: error processing cnijfilter-ip1800_2.70-2_i386-hardy.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-ip1800_2.70-2_i386-hardy.deb
```

I can't find either of the dependency packages on Synaptic. Are they simply outdated?

---

### Post by marijnvdpas on 2009-04-16
hi, pls check:

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP_1800](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP_1800)

this one worked perfectly for me.

---

### Post by Yaka on 2009-04-17
cool trying that now marijnvdpas

---

### Post by 5ive on 2009-04-25
The printer works on my Ubuntu 9.04. Use of this script [http://www.mediafire.com/?dsn21hmzlzy](http://www.mediafire.com/?dsn21hmzlzy) (the script comes from forum.ubuntu.pl)
Installs drivers for 32 & 64 bit Ubuntu.

---

### Post by SteveDee on 2009-04-27
> **5ive said:**
> The printer works on my Ubuntu 9.04. Use of this script [http://www.mediafire.com/?dsn21hmzlzy](http://www.mediafire.com/?dsn21hmzlzy) (the script comes from forum.ubuntu.pl)
Installs drivers for 32 & 64 bit Ubuntu.

Many thanks for this. It saved me some time when doing a fresh install of 9.04.

---

### Post by tantos on 2009-05-07
> **5ive said:**
> The printer works on my Ubuntu 9.04. Use of this script [http://www.mediafire.com/?dsn21hmzlzy](http://www.mediafire.com/?dsn21hmzlzy) (the script comes from forum.ubuntu.pl)
Installs drivers for 32 & 64 bit Ubuntu.

thank you sir:guitar:

---

### Post by mabtifro2 on 2009-05-15
omg thank u thank u thank u thank u thank u thank u

---

### Post by BUKRITYA on 2009-05-25
Sorry to be the only party-pooper...

Stil a no-go for me....

as you can see, mine is a 86_64 system and it warns me of this in the process.
I am running this script line after line, only the X64 part ( after i tried the whole thing) and still no printing in open-office.

Help anyone?? 

```
avi@avi-desktop:~$ uname -m
x86_64
avi@avi-desktop:~$ cd Des
bash: cd: Des: No such file or directory
avi@avi-desktop:~$ cd Desktop/
avi@avi-desktop:~/Desktop$ cd canon_ip1800_u904/
avi@avi-desktop:~/Desktop/canon_ip1800_u904$ sudo apt-get -y install ia32-libs
[sudo] password for avi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
avi@avi-desktop:~/Desktop/canon_ip1800_u904$ cd ./files
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo dpkg -i --force-architecture cnijfilter-common_2.70-2_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 201518 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.70-2 (using cnijfilter-common_2.70-2_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (2.70-2) ...
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo dpkg -i --force-architecture cnijfilter-ip1800series_2.70-2_i386.deb 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 201518 files and directories currently installed.)
Preparing to replace cnijfilter-ip1800series 2.70-2 (using cnijfilter-ip1800series_2.70-2_i386.deb) ...
Unpacking replacement cnijfilter-ip1800series ...
Setting up cnijfilter-ip1800series (2.70-2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo ln -s libpng12.so.0.27.0 /usr/lib32/libpng.so.3
ln: creating symbolic link `/usr/lib32/libpng.so.3': File exists
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo ln -s libtiff.so.4.2.1 /usr/lib32/libtiff.so.3
ln: creating symbolic link `/usr/lib32/libtiff.so.3': File exists
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo cp -p /usr/share/cups/model/canonip1800.ppd /usr/share/cups/model/canonip1800.ppd_backup
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo cp canonip1800.ppd /usr/share/cups/model
avi@avi-desktop:~/Desktop/canon_ip1800_u904/files$ sudo /etc/init.d/cups restart * Restarting Common Unix Printing System: cupsd                         [ OK ] 

```

---

### Post by Edgar Franco on 2009-05-26
> **5ive said:**
> The printer works on my Ubuntu 9.04. Use of this script [http://www.mediafire.com/?dsn21hmzlzy](http://www.mediafire.com/?dsn21hmzlzy) (the script comes from forum.ubuntu.pl)
Installs drivers for 32 & 64 bit Ubuntu.


Thank you.  The script was ok for me.:D

---

### Post by mastapat11 on 2009-06-08
i dont know y everyone else is so lucky, but i can't get this thing to work i'm using ubu8.10 ibex.
the common file installed fine.

i tried the hardy driver and it wouldn't compile. i then edited the deb file to remove the libxml1 dep and it complied. but the /etc/init.d/cupsys file wasn't created. i copied the /etc/init.d/cups file to make it.

with all that done, when i go to select the printer i see the "USB Printer #1 with status readback for Canon IJ", but the model ip1800 still isn't on the list. the 2000 is the smallest # on there.

anybody know what to do next? thanks.

---

### Post by josta7 on 2009-07-05
> **5ive said:**
> The printer works on my Ubuntu 9.04. Use of this script [http://www.mediafire.com/?dsn21hmzlzy](http://www.mediafire.com/?dsn21hmzlzy) (the script comes from forum.ubuntu.pl)
Installs drivers for 32 & 64 bit Ubuntu.

THANK YOU! :biggrin:  You get the :KS for that one, seriously! ):P Much appreciated!

---

### Post by kchristensen516 on 2009-07-07
> **mastapat11 said:**
> i dont know y everyone else is so lucky, but i can't get this thing to work i'm using ubu8.10 ibex.
the common file installed fine.

i tried the hardy driver and it wouldn't compile. i then edited the deb file to remove the libxml1 dep and it complied. but the /etc/init.d/cupsys file wasn't created. i copied the /etc/init.d/cups file to make it.

with all that done, when i go to select the printer i see the "USB Printer #1 with status readback for Canon IJ", but the model ip1800 still isn't on the list. the 2000 is the smallest # on there.

anybody know what to do next? thanks.

When I got the dependency error for libxml1, I installed it from the debian repositories ([http://packages.debian.org/etch/libxml1](http://packages.debian.org/etch/libxml1)) and I was able to get the printer working in 9.04 using the two Hardy deb files ([http://files.getdropbox.com/u/57849/cnijfilter-common_2.70-2_i386.deb](http://files.getdropbox.com/u/57849/cnijfilter-common_2.70-2_i386.deb) and [http://files.getdropbox.com/u/57849/cnijfilter-ip1800_2.70-2_i386-hardy.deb](http://files.getdropbox.com/u/57849/cnijfilter-ip1800_2.70-2_i386-hardy.deb))

---

### Post by gary-prime on 2010-05-11
Here is a good install for 9.04 & 9.10. Worked for me beautifully.

[http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/](http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/)

---

### Post by Reteip on 2010-05-12
Does this work in Lucid (10.04) as well?

If not see these instructions, which worked for me after I upgraded to Lucid. 

For the file downloads go to: 
[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900]("http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900") 

Installation Instructions
This is Canon PIXMA iP1900 Printer Driver for Ubuntu Karmic Koala. (But also for iP1800 and Karmic Koala) 
Installation For iP1800 : 
1. Install cnijfilter-common_3.00-1_i386.deb 
	dpkg -i cnijfilter-common_3.00-1_i386.deb 
2. Install cnijfilter-ip1900series_3.00-1_i386.deb 
	dpkg -i cnijfilter-ip1900series_3.00-1_i386.deb 
3. Plug in your Printer 
4. Select printer driver by choosing Provide PPD file. 
5. Point your PPD file using /usr/share/ppd/ canonip1900for1800.ppd {ignore canonip1900.ppd}
Thanks to Edgar Ilaga ([http://ubuntuforums.org/member.php?u=890253](http://ubuntuforums.org/member.php?u=890253)) 
Regards, 
tantos 
([http://tantos.web.id](http://tantos.web.id))

All the best!

---

### Post by 5ive on 2010-05-22
Installation the script Canon iP1800 for Ubuntu 10.04: [http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_u1004.tar.gz](http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_u1004.tar.gz) (by empitt, forum.ubuntu.pl).

---

### Post by csab on 2010-05-29
Thanks a lot!!! The script works!

---

### Post by 5ive on 2010-06-06
> **csab said:**
> Thanks a lot!!! The script works!
;)

> **5ive said:**
> Installation the script Canon iP1800 for Ubuntu 10.04: [http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_u1004.tar.gz](http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_u1004.tar.gz) (by empitt, forum.ubuntu.pl).
Universal script for all version Ubuntu & Debian: [http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_deb.tar.gz](http://dl.dropbox.com/u/6294587/Ubuntu/canon_ip1800_deb.tar.gz)

---

### Post by jpwong on 2011-02-02
I had the same problem until I found the following page: [http://librarylinux.wordpress.com/2010/07/06/driver-canon-pixma-ip1880-on-ubuntu-10-04-lucid-lynx/](http://librarylinux.wordpress.com/2010/07/06/driver-canon-pixma-ip1880-on-ubuntu-10-04-lucid-lynx/)

BTW, I'm currently using Ubuntu 10.04 Lucid Lynx, and a Canon PIXMA iP1800. Hope this will be of help to someone out there trying to get their printer working properly.

JPW

---

### Post by kummy on 2011-03-12
> **jpwong said:**
> I had the same problem until I found the following page: [http://librarylinux.wordpress.com/2010/07/06/driver-canon-pixma-ip1880-on-ubuntu-10-04-lucid-lynx/](http://librarylinux.wordpress.com/2010/07/06/driver-canon-pixma-ip1880-on-ubuntu-10-04-lucid-lynx/)

BTW, I'm currently using Ubuntu 10.04 Lucid Lynx, and a Canon PIXMA iP1800. Hope this will be of help to someone out there trying to get their printer working properly.

JPW

librarylinux is great.. i did it on my asus ul30a and ubuntu 10.10.. i can print now with my canon pixma iP1800... thanks...

---

### Post by empitt on 2011-03-12
Yet another alternative. Script to install the drivers Canon iP1800 for all the Ubuntu versions: [http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz](http://www.linuxone.pl/download/canon_ip1800_deb.tar.gz)
Installation:
```
sudo ./install.sh
```

---

### Post by WileyGaia on 2011-04-06
> **empitt said:**
> Yet another alternative. Script to install the drivers Canon iP1800 for all the Ubuntu versions: [http://www.toplnx.pl/files/canon_ip1800_deb.tar.gz](http://www.toplnx.pl/files/canon_ip1800_deb.tar.gz)
Installation:
```
sudo ./install.sh
```

Thanks - this worked for me! (lucid)

---

### Post by lupas on 2012-04-30
Is there any solution for 12.04LTS to get this printer working???

---

### Post by Reteip on 2012-05-01
Well after I upgraded to 12.04, did _not_ do a clean install, my 1800 still works fine.
I haven't really changed anything since I wrote my May 12th, 2010 post earlier in this thread.
Maybe you could try the instructions I referred to back then.

---

