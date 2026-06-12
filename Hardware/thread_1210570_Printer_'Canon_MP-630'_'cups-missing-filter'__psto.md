---
title: "Printer 'Canon MP-630': 'cups-missing-filter' / pstocanonij not installed - AMD64"
date: 2009-07-11
forum: Hardware
---

### Post by buzzcook on 2009-07-11
Good evening all

I'm a beginner so please be patient.

I can't get my Canon MP630 working with Ubuntu 9.04, running on AMD64.
I've tried to install the PPD files but get this error message:

Printer 'Canon-MP630' requires the 'pstocanonij' program but it is not currently installed.  Please install it before using this printer.

An entry has been created for Canon MP-630 in System - Administration - Printing. The printing icon appears with a red graphic indicating it's not working, and this is the rollover error message for that printer icon:

Printer 'Canon MP-630': 'cups-missing-filter'

I found a solution to this which apparently relates to this pstocanonij program on 64-bit, but it **hasn't worked for me** (maybe because it seems to be for Suse):

1. _Move file_ (replace '<sourcefolder>' with the correct folder)
mv /<source folder>/pstocanonij /usr/lib64/cups/filter/pstocanonij
2. _Change owner of file_
sudo chown root:root /usr/lib64/cups/filter/pstocanonij
3._ Change access rights_
sudo chmod u+x /usr/lib64/cups/filter/pstocanonij

- on my system, the file is called pstocanonij**.c** anyway ...

I found this fix here (sorry, it's in German, but you can see the commands):
[http://www.linuxforen.de/forums/showthread.php?p=1658576](http://www.linuxforen.de/forums/showthread.php?p=1658576)

Any other ideas out there?

---

### Post by TheLoneHoot on 2009-09-13
I'm a newbie too and haven't been able to figure out where I'm even supposed to install the ppd file.  I extracted it to the desktop, and told the printer installation wizard where to look for it, but then I got the same 'pstocanonij' error message too.

I like the idea of Linux being open source and all, and I like how relatively user-friendly Ubuntu is for a standard Windows user like myself, but this is one of those many things that Ubuntu can't do that Windows can - be intuitive.

I'm sure I'll be told that it's a matter of my being "raised" on windows and just not knowing the Ubuntu environment, etc., but honestly, it's really not as intuitive in matters like this.  I just don't recall ever having issues like I'm having here*, with Windows.  It just doesn't work right out of the box like most windows stuff does.

My other issue is this:  When you ask for help, you often get "Duh!" types of replies - it seems like people want to prove how stupid you are as a newbie, rather than try to help... even in the 'absolute beginner' forums.  I mean look at this question of yours - asked in July of 2009, and here I am more than a month later not able to help, but only able to commiserate.
__
*No sound, printer drivers not found and after finding them not knowing where to install them, flash videos not playing, etc.

---

### Post by Edu16 on 2010-04-04
I don't suppose you resolved your issue did you?  I have the same prob - but for a slightly different model.

BTW - I completely agree with your wider O/S sentiment.  You are bang on the nose.  There is a strong desire to keep LINUX 'mystic' - and to keep out the riff raff.  I was once a programmer - but not in UNIX.  And if I find it tough then the average family out there is excluded from LINUX.  This is, I suspect, the way the LINUX community secretly want it !

---

### Post by buzzcook on 2010-04-05
Hi there

I should have posted the fix I worked out at the time. I've attached it below (at the end of this post), taken from my own notes. The key is to use "force architecture" in the unpack (dpkg statement). Hope it works for you.

BTW, I later downloaded this printer driver, which works much better (far more settings etc.):

[http://www.turboprint.info](http://www.turboprint.info) 

You can download it for a free trial period - well worth the money in my opinion.

Best wishes!


1.    Download tar file, either in browser from Canon site or with command line:     
wget [http://de.software.canon-europe.com/files/soft31301/software/MP630_debian_drivers.tar](http://de.software.canon-europe.com/files/soft31301/software/MP630_debian_drivers.tar) 

 2.    Unpack file:      tar -xvf MP630_debian_drivers.tar          
Two new files appear:      
MP630_debian_printer.tar      
MP630_debian_scangear.tar 

 3.    Unpack the first:    
tar -xvf MP630_debian_printer.tar      
Now you see three files containing the drivers. 
  **3a. Temporary fix,** download this file to avoid problems with libcupsys2: 
[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb)[URL="http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.1_all.deb"]
[/URL]Warning: possible security vulnerability with cups server ... 
 More details on this thread: [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248)   

4.    Install the drivers (---force-architecture is necessary because it's for i386, although it works OK on AMD64):       
a) sudo dpkg -i ---force-architecture cnijfilter-common_3.00-1_i386.deb         
b) sudo dpkg -i ---force-architecture cnijfilter-mp630series_3.00-1_i386.deb     
Now the drivers are installed. It just remains to install the printer.   

5.    From Gnome:      
ystem -> Administration -> Printer       
Should now be automatic &#8211; set this as standard printer.

---

### Post by staun on 2010-07-12
That worked for me! Link to .deb package is broken (easy to find the right one), and --- in your install instruction should be -- (2 dashes)

Thanks!

---

