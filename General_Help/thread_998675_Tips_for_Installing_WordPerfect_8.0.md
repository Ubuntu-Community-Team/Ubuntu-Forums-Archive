---
title: "Tips for Installing WordPerfect 8.0"
date: 2008-12-01
forum: General Help
---

### Post by thenanodude on 2008-12-01
I recently managed to install WordPerfect 8.0 (the "free" version for Linux), and I thought I would share my experience in case any others were interested.  For the record, I am running Ubuntu 8.04 with the xfce desktop on an HP Pavilion laptop with an AMD Turion 64 processor.

First, I found a lot of useful information at [http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/)
Second, this will not be a detailed How-to covering every step and all the possible issues you will face.  Rather, I mostly intend to share a couple of the major issues I ran into, and how I overcame them.  
Finally, you should be able to do the installation without logging in as root.  Just make sure you have permissions for the installation directory.

1. Obtaining the files.

Years ago, corel released a free version of WordPerfect 8 for linux users.  Within a few years, they stopped distributing and supporting the software, but it is still possible to download it from various places.  A list of download sites (several of which no longer work) is available at [http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/)

The program depends on a number of deprecated libraries.  There are a few places where you may find someone has combined them all into one tarball.  Two I found were:

wp8-libs.tgz from [http://www.linux-gatineau.org/wp8/](http://www.linux-gatineau.org/wp8/)
wp8-compat-libs.tgz from [http://www.sci.usq.edu.au/staff/house/wp8/index.html](http://www.sci.usq.edu.au/staff/house/wp8/index.html)

2. Unpack/install the libraries

You will need to create a dedicated directory for the WP8 installation.  I put everything in /usr/local/wp8.  

Unpack the libraries into a dedicated directory.  I used /usr/local/wp8/wp-libs

Add a line with this directory name in "/etc/ld.conf.so".  My ld.conf.so now simply has 2 lines:

   include /etc/ld.so.conf.d/*.conf
   /usr/local/wp8/wp-libs

Run "sudo /sbin/ldconfig"

You can check that you have installed the libraries with "sudo ldconfig -v | grep libc.so.5" This should show a libc of 5.3.12 through 5.4.46.  You can check that you have all the necessary libraries after you install WP (see below) with "ldd [path]/xwp"


3.  Create links to needed files.

WordPerfect tries to load files from non-existent directory:  /usr/X11R6/lib/X11/locale/

These files are now located here: /usr/share/X11/locale/

I created /usr/X11R6/lib/X11/locale and then from that directory did: "ln -s /usr/share/X11/locale/* ."

If you do not do this, and you try to run WordPerfect after installing, you will see the splash screen appear and the program will exit with a Segmentation Fault.


4. Unpack/install WordPerfect 8

Before running "tar" on the WP8 tarball you downloaded, you should be aware that the files will likely be dumped directly into the directory you are in, not into a dedicated directory.  I put everything into /usr/local/wp8. I ended up with 11 tarballs named things like "b_ins00."  You may end up with different names and variations on capitalization.  Some installation instructions on the web tell you to only unpack the first file and run the install program "Runme."  In my case, this did not work, so I had to manually unpack all the tarballs, then answer "yes" to the first question "Runme" asked ("Have you unpacked and unzipped the tarball?")

after unpacking the tarballs, you install the program by running "sh Runme"

note:  see below for how I added printers.  You do not have to add the printers during the installation.

5. Run WordPerfect!

In the directory where you told WP to install itself, you will find the directory "wpbin" and in that, the binary "xwp".  For me, this is now in /usr/local/wp8/wp/wpbin.   You may have to be in this directory to run xwp with "./xwp"

If you have problems at this point, here are a couple of tips:
1. Make sure you have the proper permissions set for the installation direcotry
2. Run "xwp" from within the "wpbin" directory with "./xwp".  Once everything works, you may not have to do this (or you may wish to create a script file), but when first getting everything working, it is helpful to "cd" to the "wpbin" directory.
3. Run "ldd xwp" to make sure WordPerfect can find the deprecated libraries you installed above.
4. You can run "strace xwp" to get a LOT of info when WordPerfect is loading that can help you track down problems.


6. Enter the registration key

Without a registration key, you may only get to run the program for 90 days.  the website [http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/) lists several places to get the key.


7. Adding printers.

One thing I found somewhat tricky was adding printers.  WordPerfect uses it's own printer drivers, but you can bypass them and use CUPS.  Here is how I did it:

run WP in Admin mode:  xwp -adm
In a new document, hit "print"
Choose "Select" in the printer selection dialog, then "Printer Create/Edit"
"Add" a printer with the "Passthru PostScript" driver.  When you hit "OK" this should take you back to the "Printer Create/Edit" box.  

Hit "Setup" -> "Destination" -> "CreateWPApp".  

From the menus, select "Create" -> "Destination"

Enter a name for your printer, hit "OK" and select "Custom Spool Command"

In the Spooler Command box, enter "lpr -oraw -P [PRINTER]"  where PRINTER is the CUPS name of your installed printer.  You can find the name(s) of your printer(s) with "lpstat -d -p"

Click "OK" back through all the boxes, and you should have a working printer.


I saw a few other posts around asking for help on installing WordPerfect, so I hope this is helpful!  Note that I only have done this with the free version of WP 8.0.  If you have the .dep packages for WP 8.1 from the Corel Linux Operating System distribution, the installation may be different.  However, you will likely need to install the deprecated libraries and create the soft links from steps 2 and 3.

---

### Post by editrix on 2008-12-01
Holy Mackerel, if I can get this working it will be the best Xmas present ever! Thanks for this. I won't be trying it until I can get a friend on high speed to download the programs and libraries for me, but prepare yourself for questions in the new year!

---

### Post by thenanodude on 2009-10-07
> Thanks for your installation tips you provided, however I'm still not able to get this to run, and I think it has to do with the permissions. How do I set the proper permissions? I've already tried the command line:

"sudo chmod 777 /usr/local/wp8 -R"

but that didn't work. Please help!


unfortunately I haven't run WordPerfect on my system for a little while, and when I just tried, I ran into problems.  I upgraded to Ubuntu 9.04 not too long ago, and I think the problem may be related.  I will keep trying to figure out what has happened to the WordPerfect installation, but it may take me a little while.

---

### Post by deapthought on 2009-10-21
Thank you for this.  In fact I'm installing Slack 13 from Slack 10.1.  I'd worked out all the library issues for myself over the years, but was thrown by the "Seg. fault" issue on Slack 13.  (BTW, I started using WP 8 on Slack 4 in 1999!).

It now runs (although slightly unconfigurated).  

Curiously, a lot of stuff I used on Slack 10 does not compile from source code on Slack 13, but the binaries copied across work fine without library dependancy problems.  For which I am grateful.

---

### Post by forliberty on 2010-04-29
I have been trying to follow these instructions to install the "free" WP 8 for the past few hours to no avail. I was able to install the needed (old) libraries, but cannot get the WP installation script to run.

I need to be able to run WP for my work as an attorney, as our  firm uses WordPerfect for all of our documents (not my choice!). Ooffice and AbiWord can open WP files (kind of--they don't do very well with pleading paper documents), but cannot save them in WP format. I was running WP 10 under Wine, but it is now broken and seems irreparable. I realize I could use Virtualbox, but I'd rather not set up yet another fake Windows installation if I can avoid it. 

After manually unpacking all the tarballs, their contents are now in three sub-folders: linux, readme, and shared. The files Readme and Runme are in the main folder. When I try "sh Runme" I get, "Please Wait .[: Illegal number: 28-18-generic" This is then followed by a whole string of errors, some of which is pasted below.

Any help would be greatly appreciated. I seem to be running out of options. I have looked at the instructions at [http://home.ubalt.edu/abento/linux/applications/index.html](http://home.ubalt.edu/abento/linux/applications/index.html)
[http://linuxmafia.com/wpfaq/](http://linuxmafia.com/wpfaq/)

But I still can't seem to get it to run. Thanks!!!

I'm running Ubuntu 9.04.

 Percent Complete:  sed: can't read shared/.prlist: No such file or directory
chmod: changing permissions of `/wpbin': Operation not permitted
chmod: changing permissions of `/shbin10': Operation not permitted
chmod: missing operand after `755'
Try `chmod --help' for more information.
chmod: cannot access `/wplib/.wpbuildc': No such file or directory
chmod: cannot access `/wplib/.wpbuildx': No such file or directory
chmod: cannot access `/shbin10/lmgrd': No such file or directory
chmod: cannot access `/shbin10/lmutil': No such file or directory
chmod: cannot access `/shbin10/wplmd8': No such file or directory
chmod: cannot access `/shlib10/bristxt.us': No such file or directory
chmod: cannot access `/shbin10/hyperhelp': No such file or directory
chmod: cannot access `/shbin10/cvt': No such file or directory
chmod: cannot access `/shbin10/cjpeg': No such file or directory
chmod: cannot access `/shbin10/djpeg': No such file or directory
chmod: cannot access `/wpbin/README.1': No such file or directory
chmod: cannot access `/wpbin/README.2': No such file or directory
chmod: cannot access `/wpbin/README.3': No such file or directory
chmod: cannot access `/wpbin/README.4': No such file or directory

---

### Post by srs5694 on 2010-04-30
Your errors look like permissions problems. Try adding "sudo" to the start of the command you used to run the script (e.g., instead of typing "./Runme", type "sudo ./Runme"). This *should* work around permissions problems, but I can't guarantee that the result will be usable. Sadly, my experience is that WP8 for Linux is pretty flaky with recent Linux versions.

Running a Windows version in WINE is another option. I realize you say that your WP10 installation in WINE is now broken, but working on that approach may be the better way to go.

Yet another option would be to run an older version of Linux in a virtual machine (QEMU, VirtualBox, whatever). That'll bypass a lot of issues, and you'll be able to run it from within the virtual machine on your regular desktop by using SSH or various other network access tools. This can help make the program run more seamlessly with your other programs than would be possible with a Windows version in a virtual machine. You can even set the virtual machine to start up minimized whenever the computer boots or whenever you log in, and create a desktop icon that runs WP8 "remotely." All of this will take a fair amount of effort to set up, but the result will be something that will be almost as seamless as a regular local install.

---

### Post by forliberty on 2010-06-23
Thanks for the tips. Running the Runme script as root didn't help, nor did a series of permissions changes I tried. I'm giving up on the Linux version...will try to get it running under wine again, as challenging as that is!

---

### Post by jbh001 on 2010-08-23
I haven't yet been able to get WP 8.0 to install on Ubuntu 10.04. But I was able to get it to install on Ubuntu 8.08.4 LTS and then do the in-place upgrade to Ubuntu 10.04 as described here: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) 

WP 8.0 still seems to work okay after the upgrade to Ubuntu 10.04.

There must have been some libraries that changed after 8.04 that are preventing the WP installer from succeeding.

---

### Post by jbh001 on 2010-08-27
I have posted a fleshed out version of these installation instructions at: [http://www.wpuniverse.com/vb/showthread.php?postid=215127#post215127](http://www.wpuniverse.com/vb/showthread.php?postid=215127#post215127)

---

