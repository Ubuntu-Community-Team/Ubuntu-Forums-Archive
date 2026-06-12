---
title: "[GUIDE] Canon MX700 Printer Install (tested with 9.04, 9.10 Alpha 6)"
date: 2009-09-23
forum: Hardware
---

### Post by Menthu_Rae on 2009-09-23
Apologies if this is the wrong section? I wanted to help out the people from this thread --> [http://ubuntuforums.org/showthread.php?t=571795&page=9](http://ubuntuforums.org/showthread.php?t=571795&page=9) <-- but I can't post in there due to it being in the archive.

Anyway... For those of you who are stuck with the Canon MX700 and can't get it working... this is how I got mine working (**via network**) under Ubuntu 9.04 and 9.10 Alpha 6 (both 64-bit/AMD64):

**Pre-Installation Files:**

You will need these files before we install the printer:

[INDENT]**cnijfilter-common_2.80-1_i386.deb**
--> [http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html)
**cnijfilter-mp520series_2.80-1_i386.deb**
--> [http://support-au.canon.com.au/contents/AU/EN/0100083901.html](http://support-au.canon.com.au/contents/AU/EN/0100083901.html)
**canonmx700.ppd** (rename the .txt part!)
--> [http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424](http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424)
**cups-bjnp-0.5.3.tar.gz**
--> [http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/)[/INDENT]

Now that we've got those... we can install everything!

[INDENT]**EDIT:** *06/11/09* With the apparent renaming of the CUPS packages in Karmic, you may need to do the following:

Open a terminal window and navigate to the directory your deb folders are in... perform the following operations:

```
dpkg-deb -x cnijfilter-common_2.80-1_i386.deb **common**
dpkg-deb --control cnijfilter-common_2.80-1_i386.deb
```

Now change into the DEBIAN/ directory...

```
cd DEBIAN/
gedit control 
```

In gedit, find the following line...

```
Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1), libpopt0 (>= 1.7)
```

and change it to...

```
Depends: libc6 (>= 2.3.4-1), **libcups2** (>= 1.2.1), libpopt0 (>= 1.7)
```

Now we move the entire DEBIAN/ directory into common...

```
cd ..
mv DEBIAN/ common/
```

Now rebuild the package...

```
dpkg -b **common** cnijfilter-common_2.80-1_i386.deb
```

**Now remove the common directory** (_delete it manually_ or rm in the terminal if you know what you're doing...)...

Re-do the steps again but for the *cnijfilter-mp520series_2.80-1_i386.deb*...

```
dpkg-deb -x cnijfilter-mp520series_2.80-1_i386.deb **common**
dpkg-deb --control cnijfilter-mp520series_2.80-1_i386.deb
```

Now change into the DEBIAN/ directory...

```
cd DEBIAN/
gedit control 
```

In gedit, find the following lines...

```
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libcupsys2 (>= 1.2.1), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.10.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.12.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, cnijfilter-common (>= 2.80)
```

and change it to...

```
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), **libcups2** (>= 1.2.1), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.10.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.12.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, cnijfilter-common (>= 2.80)
```

Now we move the entire DEBIAN/ directory into common...

```
cd ..
mv DEBIAN/ common/
```

Now rebuild the package...

```
dpkg -b **common** cnijfilter-mp520series_2.80-1_i386.deb
```

The addition above was tested in a virtual machine and worked fine :) Thanks go out to **Edgar Ilaga** from this thread [ [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248) ]

We can now continue with the rest of the guide...[/INDENT]

**Canon MX700 Installation:**

```
sudo apt-get install libcupsys2 libcupsys2-dev
cd **<downloaded files directory>**
sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb 
sudo dpkg --force-architecture -i cnijfilter-mp520series_2.80-1_i386.deb 
tar xvzf cups-bjnp-0.5.3.tar.gz
cd cups-bjnp-0.5.3/
sudo ./configure --prefix=/usr 
sudo make
./bjnp
sudo make install
```

Note that sudo may not be needed for the 2 of the last 4 steps, but I used it when I installed... if someone can tell me for sure it's not needed, then I'll edit this post. :P

Once that is done, we can now add the printer... **Make sure your printer is turned on.**

```
System > Administration > Printing

New > Printer > Canon MX700 > Forward

Select PPD > **<Select your PPD File>** > Forward

Name it > Done!
```

Print a test page and it should work. :popcorn:

---

### Post by clemsonteric on 2009-10-11
A million thanks for this.  So quick and painless - big kudos for this guide!!!

---

### Post by ashishjain77 on 2009-10-12
Hi,

Tried this on 9.10 (x86) version. On the first set of command where you have to install libcupsys2 and libcupsys2-dev, the system is automatically taking libcups2 and libcups2-dev. The subsequent installs are getting a failure. Below is the log

---------------------------------------------
sudo apt-get install libcupsys2 libcupsys2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libcups2 instead of libcupsys2
libcups2 is already the newest version.
Note, selecting libcups2-dev instead of libcupsys2-dev
libcups2-dev is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cnijfilter-common: Depends: libcupsys2 (>= 1.2.1)
  cnijfilter-mp520series: Depends: libcupsys2 (>= 1.2.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
----------------------------------------------

Any help to get past this step and go onto the other steps would be great.

Thanks,
Ashish:(

---

### Post by plaurentiu on 2009-10-13
Karmic includes CUPS with the new names as libcups2. You need to install a transitional package including the names for the libcupsys2.

For example this: libcupsys2_1.3.9-17ubuntu3.1_all.deb

You can get it from here:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)

---

### Post by roclinus on 2009-10-31
None of most of the above worked for me. I'm not new to computers, just linux. I am really trying to get this to work. I'll be happy if I can get my Canon MX700 multifunction to work.

---

### Post by roclinus on 2009-10-31
Sorry, that should have read did not work for me.:(

---

### Post by Menthu_Rae on 2009-11-05
**EDIT:** OK, everyone having issues - try it with the additional steps above (in the first post, I just edited it!). I just tested it and it worked fine :)

[COLOR="Silver"]Hey guys,

Those of you having issues - is your printer plugged in via USB or Network?

Also just to confirm - you're running 32-bit (x86) versions of 9.10?

If so, I will give it a go in a virtual machine tomorrow and see if anything else needs to be done, and update the guide accordingly.

Some packages may have changed since I wrote/tested it :)[/COLOR]

---

### Post by clemsonteric on 2009-11-08
Confirmed to work with Ubuntu 9.10 64-bit.  Thanks again.

---

### Post by urdrwho on 2009-11-17
Nope.  Can't get it to work for me and getting a lot of error notices.

Gotta get some work done, play time over for the morning.

Errrrr!!!!  How long to get this printer working in Windows.  Put disc in drive, install, drink coffee for the two minutes to install.  Printer working.

How long have I been trying in Ubuntu.  Oh probably about 2 freak'in hours and it still doesn't work.

The first download never installs and gives broken notices.

Second one gives this:

/tmp/canonmx700.ppd-1.txt could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Third one gives this

Error: Dependency is not satisfiable: cnijfilter-common (>= 2.80)

That is all before using the terminal commands.

Thanks for the info but it didn't fly for me.

> **roclinus said:**
> None of most of the above worked for me. I'm not new to computers, just linux. I am really trying to get this to work. I'll be happy if I can get my Canon MX700 multifunction to work.

---

### Post by Menthu_Rae on 2009-11-27
> **urdrwho said:**
> Nope.  Can't get it to work for me and getting a lot of error notices.

Gotta get some work done, play time over for the morning.

Errrrr!!!!  How long to get this printer working in Windows.  Put disc in drive, install, drink coffee for the two minutes to install.  Printer working.

How long have I been trying in Ubuntu.  Oh probably about 2 freak'in hours and it still doesn't work.

The first download never installs and gives broken notices.

Second one gives this:

/tmp/canonmx700.ppd-1.txt could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Third one gives this

Error: Dependency is not satisfiable: cnijfilter-common (>= 2.80)

That is all before using the terminal commands.

Thanks for the info but it didn't fly for me.

Mate, it sounds like you are going about it all wrong... **You shouldn't be trying to open them via GUI** - which is what it sounds like you're doing...

I will send you a private message with my email address and I'm happy to help you out - but please don't rant on that "windows works, why doesn't ubuntu". The fact of the matter is that Canon's support for this printer in Linux is lackluster and that the community has come together to get this printer (and many other Canon models) working.

For comparison, my Brother HL2070N worked out of the box - I just clicked through "next" in the add printer wizard. No need to muck around with anything. If Canon supported their printers properly under Linux, it would be the same trivial affair!

Anyway, I'll PM you my email address now if you still care - my offer for help is there if you want to take it up. :p

---

### Post by wwalkersd on 2009-11-29
Well, I'm having some degree of success on Karmic 9.10.  I've successfully gotten as far as running the command 

sudo ./configure --prefix=/usr

which provides the output
> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking for cupsDoRequest in -lcups... no
configure: error: CUPS library not found


It looks like it's looking for a library in a place it no longer exists.

This may or may not be related to the fact that when I got to the command

sudo apt-get install libcupsys2 libcupsys2-dev

I got the following output:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libcupsys2 is a virtual package provided by:
  libcups2 1.4.1-5ubuntu2.1
You should explicitly select one to install.
E: Package libcupsys2 has no installation candidate


Also, my cups-bjnp is 0.5.4 rather than 0.5.3.

I'd appreciate any help anyone can offer.  Thanks!

---

### Post by Menthu_Rae on 2009-12-10
> **wwalkersd said:**
> Well, I'm having some degree of success on Karmic 9.10.  I've successfully gotten as far as running the command 

sudo ./configure --prefix=/usr

which provides the output


It looks like it's looking for a library in a place it no longer exists.

This may or may not be related to the fact that when I got to the command

sudo apt-get install libcupsys2 libcupsys2-dev

I got the following output:


Also, my cups-bjnp is 0.5.4 rather than 0.5.3.

I'd appreciate any help anyone can offer.  Thanks!

Hey mate, I will take a proper look at it (and test it) for you on the weekend, but for now I think if you try to do:

```
sudo apt-get install libcups2 libcups2-dev
```

>> instead of libcupsys2 and libcupsys2-dev <<

the rest of it should work (fingers crossed). Will check back here tomorrow night with some test results for you. :p

**EDIT:** I haven't tested it, but I'm pretty sure it'll work... let me know if it doesn't and I will spend the time to look at it further :)

---

### Post by wwalkersd on 2009-12-12
Thanks, Menthu_Rae!  Apparently I didn't have libcupsys2-dev.  That got it built, and I set up the printer (chose Canon MX700 Series, showing the IP address, rather than MX700, showing the ethernet address), but I can't print a test page.  I get an error saying 'cups-insecure-filter'.  Does that ring any bells for you?

---

### Post by wwalkersd on 2009-12-12
> **wwalkersd said:**
> Thanks, Menthu_Rae!  Apparently I didn't have libcupsys2-dev.  That got it built, and I set up the printer (chose Canon MX700 Series, showing the IP address, rather than MX700, showing the ethernet address), but I can't print a test page.  I get an error saying 'cups-insecure-filter'.  Does that ring any bells for you?

Update: When I checked the printer state under Printer Properties->Settings, I found a message that complained that the filter /usr/lib/cups/pstocanonij was not owned by root. I fixed that and now I can print! I wonder if I missed a sudo somewhere.

I do notice that the printer state shows "Processing - Failed to read side-channel request!" briefly just as the test page finishes printing. It doesn't seem to affect anything.

---

### Post by roclinus on 2009-12-14
Tried it all with no success. Had a little time to kill so I thought I would give this another shot, anyway it did not work. I am not trying to get it through the GUI. nothing seems to work and unlike some of the other responses I have read in forums, I can't afford a new printer, besides I should not have to buy a different printer as this one is only 2 years old and works without issue on the other OS.

---

### Post by Menthu_Rae on 2009-12-19
> **roclinus said:**
> Tried it all with no success. Had a little time to kill so I thought I would give this another shot, anyway it did not work. I am not trying to get it through the GUI. nothing seems to work and unlike some of the other responses I have read in forums, I can't afford a new printer, besides I should not have to buy a different printer as this one is only 2 years old and works without issue on the other OS.

Hey mate - what is the exact problem you're having? If you want, add me on MSN and I will help you out (have PM'd you my MSN address).

---

### Post by Poogy on 2010-01-15
First, many thanks for this fantastic guide!

I am a Linux newbie, trying to install my MX700 on 9.10 Netbook Remix.
I think I managed to perform all steps successfully (although I did ran into several challenges along the way), and I could see that when I ran the bjnp command the system got my correct printer IP. 
However, when I go to Administration --> printing and try to add a new printer, after searching for printers ends, MX700 does not appear in the list (I only see Other and Network Printer).
I'd be grateful for any assistance or guidance on what could cause this (what step didn't go well in the installation process...)

Thanks in advance!

UPDATE: although the printer didn't show up automatically, I was able to successfully add it manually. After running ./bjnp the input returned the printer address (looks like bjnp://<printer_ip: port>). I added it to the URI in the Other section of the printers, selected the .ppd file and the printer was added.
Next, I got an error message cups-insecure-filter. Following the instructions on post #2 here solved this problem: [http://ubuntuforums.org/showthread.php?t=1313291]("http://ubuntuforums.org/showthread.php?t=1313291")
Following this, test page printed successfully :-)

---

### Post by jeff21 on 2010-01-18
> **Poogy said:**
> First, many thanks for this fantastic guide!

I am a Linux newbie, trying to install my MX700 on 9.10 Netbook Remix.
I think I managed to perform all steps successfully (although I did ran into several challenges along the way), and I could see that when I ran the bjnp command the system got my correct printer IP. 
However, when I go to Administration --> printing and try to add a new printer, after searching for printers ends, MX700 does not appear in the list (I only see Other and Network Printer).
I'd be grateful for any assistance or guidance on what could cause this (what step didn't go well in the installation process...)

Thanks in advance!

UPDATE: although the printer didn't show up automatically, I was able to successfully add it manually. After running ./bjnp the input returned the printer address (looks like bjnp://<printer_ip: port>). I added it to the URI in the Other section of the printers, selected the .ppd file and the printer was added.
Next, I got an error message cups-insecure-filter. Following the instructions on post #2 here solved this problem: [http://ubuntuforums.org/showthread.php?t=1313291](http://ubuntuforums.org/showthread.php?t=1313291)
Following this, test page printed successfully :-)

I also did this and can now print 1/4 of the test page before it stops, waits for about a minute, and then spits out the unfinished test page.  Any idea what might be wrong?

---

### Post by frmdstryr on 2010-02-02
thank you soo much! I've been printing through a virtual machine for about 6 months! Now it works great in ubuntu!

I had to do 3 minor things, I first download and install this
> **plaurentiu said:**
> Karmic includes CUPS with the new names as libcups2. You need to install a transitional package including the names for the libcupsys2.

For example this: libcupsys2_1.3.9-17ubuntu3.1_all.deb

You can get it from here:
[http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download)
 

Then change the version of cups-bjnp 
```

cd <downloaded files directory>
sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb 
sudo dpkg --force-architecture -i cnijfilter-mp520series_2.80-1_i386.deb 
tar xvzf cups-bjnp-0.5.**4**.tar.gz
cd cups-bjnp-0.5.**4**/
sudo ./configure --prefix=/usr 
sudo make
./bjnp
sudo make install

```

 I had the same problem as > Poogy, I get an error saying 'cups-insecure-filter' 

To fix this

```

cd /usr/lib/cups/filter
sudo chown root pstocanonij

```

printed perfect test page!

---

### Post by najevi on 2010-02-11
Thank you for this valuable guide. I wish I understood how you guys are able to figure out such complicated dependencies.

-- March 2011 update --
On a fresh installation of ubuntu 10.10 (Maverick Meerkat) I was seeing an error message: "cups-insecure-filter" when sending a test page to the printer and no job would print.
I learned that some files/directories within /usr/lib were owned by my personal username instead of by root.

So in addition to the above steps I first checked /usr/lib for files/directories not owned by root
```
ls -lR /usr/lib |grep -ive " root " |grep -ive "^$" |grep -ive "^/usr/lib" |grep -ive "^total"
 
```
 That list was small and each file/directory related to a bubble jet printer.

I then changed owner and group to root for all files/directories below /usr/lib
```
sudo chown -hRv root /usr/lib
sudo chgrp -hRv root /usr/lib

```

See also: [cups-insecure-filter]("http://ubuntuforums.org/showthread.php?p=8235367#post8235367")

---

### Post by woo10jw on 2010-02-12
I'm running 9.10 32bit on this machine, kernel 2.6.31.19
my other machine 9.10 64bit if their is any difference to get that one to work. 


I'm a newbee and having a little problem. I followed your steps all the way to here with no problems
CANON MX700 INSTALLATION
sudo apt-get install libcupsys2 libcupsys2-dev
this is my terminal example:

root@HEC:/home/joan/Desktop# sudo apt-get install libcupsys2 libcupsys2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  comerr-dev libcups2-dev libgcrypt11-dev libgnutls-dev libgpg-error-dev
  libgssrpc4 libkadm5srv6 libkdb5-4 libkrb5-dev libtasn1-3-dev zlib1g-dev
Suggested packages:
  libgcrypt11-doc gnutls-doc gnutls-bin guile-gnutls krb5-doc krb5-user
The following NEW packages will be installed:
  comerr-dev libcups2-dev libcupsys2 libcupsys2-dev libgcrypt11-dev
  libgnutls-dev libgpg-error-dev libgssrpc4 libkadm5srv6 libkdb5-4 libkrb5-dev
  libtasn1-3-dev zlib1g-dev
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,988kB of archives.
After this operation, 6,087kB of additional disk space will be used.
Do you want to continue [Y/n]? y   
(answered yes everything proceeded with no errors)

your next step is where I'm confused
cd <downloaded files directories> It said 13 newly installed 
I don't know which & where the directories are located to continue.
could you please help

---

### Post by Menthu_Rae on 2010-02-13
> **woo10jw said:**
> I'm running 9.10 32bit on this machine, kernel 2.6.31.19
my other machine 9.10 64bit if their is any difference to get that one to work. 

<snip>

your next step is where I'm confused
cd <downloaded files directories> It said 13 newly installed 
I don't know which & where the directories are located to continue.
could you please help

Hey mate. If you look at the guide, you'll notice at the top you need some pre-installation files:


> Pre-Installation Files:

You will need these files before we install the printer:


[INDENT]**cnijfilter-common_2.80-1_i386.deb**
--> [http://support-au.canon.com.au/contents/AU/EN/0100083403.html](http://support-au.canon.com.au/contents/AU/EN/0100083403.html)
**cnijfilter-mp520series_2.80-1_i386.deb**
--> [http://support-au.canon.com.au/contents/AU/EN/0100083901.html](http://support-au.canon.com.au/contents/AU/EN/0100083901.html)
**canonmx700.ppd** (rename the .txt part!)
--> [http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424](http://ubuntuforums.org/attachment.php?attachmentid=54929&d=1199213424)
**cups-bjnp-0.5.3.tar.gz**
--> [http://sourceforge.net/projects/cups-bjnp/](http://sourceforge.net/projects/cups-bjnp/)[/INDENT]

Where I said to cd into the downloaded files directory, I'm saying to change directory in terminal to the place that you put these "pre-installation files".

**e.g. ~/Downloads (aka /home/<username>/Downloads)**

So in this case you would:

```
cd ~/Downloads
sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb 
sudo dpkg --force-architecture -i cnijfilter-mp520series_2.80-1_i386.deb 

```

etc etc.

As for your 64-bit machine, there should be no difference since I have put the guide up using the "force-architecture" flag you can see above. This will install the x86 debs despite your OS being x64 (don't worry, it will work fine in this situation). ;) :D

Any more trouble just post back here. Cheers. :popcorn:

---

### Post by bobtoo on 2010-02-20
Hi All,

About 3 weeks ago, I installed a Canon MX700 for 3 computers running both Ubuntu 9.10 & Linux Mint 8 (all 32 bit) over our network using this guide.

All worked fine till today when my wife couldn't print a file from Open office. Something in the updates in the last few days I think.

Anyway, I deleted just the printer & re-installed it with the ppd file & all is fine again. :D

Just thought I would post this in case someone else has the same problem.

---

### Post by dwunz on 2010-04-08
I'm running 9.10 2.6.31-20-generic 32-bit and just went through the steps outlined in this thread.  Everything works great!

I did run into a couple changes that have been hinted at/talked about...
First, I changed the line:
    sudo apt-get install libcupsys2 libcupsys2-dev
to:
    sudo apt-get install libcups2 libcups2-dev

Then, the following 2 lines changed to 0.5.4:

tar xvzf cups-bjnp-0.5.3.tar.gz
cd cups-bjnp-0.5.3/

and finally, the ppd file was buried in ~/Downloads/common/usr/share/ppd/

It took a little while to track it all down, BUT IT WORKS!!

Just wondering if it might be worth while to edit this guide so others may benefit without digging so deep...looks like it hasn't been updated for a while...

THANKS! :guitar:

---

### Post by deelite on 2010-07-23
About 1 year i am trying to completely work with ubuntu, but i never got my mx700 working. So every time i was going back to windows (a nice system too)
. But with your post i got it working so easy and my ubuntu will take a big place in my life.

THANK YOU SO MUCH!

---

### Post by sumoman on 2010-10-10
Menthu-Rae and DWUNZ.  You guys are gods.  I got my MX700 to work by following your instructions to the letter.  Printer works like a charm.  Sheer awesomeness.  Thank you thank you thank you.

---

### Post by frmdstryr on 2010-11-05
Thanks! Got it working for me.

---

### Post by AKnightintheDesert on 2010-12-03
This worked great on Ubuntu 10.10 64bit got it working in about 20min 

A couple of pointers, if you go through the steps of changing the dependencies then you don't have to install the packages at the start of the install just do the following.  

```
cd <downloaded files directory>
sudo dpkg --force-architecture -i cnijfilter-common_2.80-1_i386.deb 
sudo dpkg --force-architecture -i cnijfilter-mp520series_2.80-1_i386.deb 
tar xvzf cups-bjnp-0.5.3.tar.gz
cd cups-bjnp-0.5.3/
sudo ./configure --prefix=/usr 
sudo make
./bjnp
sudo make install
```

Also it should be noted that bjnp binds your printer to an IP address, and though this might go without saying with some, you need to either have a DHCP reservation for your printer or your printer set up using a static IP Address.  Otherwise you will have to redo some or all of this any time your Printers IP address changes.  The IP address can be set using the printers webpage by pointing your browser to the current IP address of your printer.  

Also I installed using the 0.5.5 build of bjnp, it worked fine but there is a file that you have to change owner to root on. Here is the command to fix that:
```
sudo chown root /usr/lib/cups/filter/pstocanonij
```

On a final note If you are looking to use the scanning on this printer, Xsane now auto finds this scanner on the network. Xsane can be installed from the Ubuntu Software Center.

Thanks for the tutorial

---

### Post by gamecraziness on 2011-05-02
I made an easy install script for this, here: [http://ubuntuforums.org/showthread.php?p=10760330#post10760330](http://ubuntuforums.org/showthread.php?p=10760330#post10760330)

Hope this helps!

---

### Post by sleep.tech on 2011-05-16
gamecraziness, thanks, worked like a charm!! awesome work everyone!!

---

### Post by gamecraziness on 2011-05-22
You're welcome. Glad it helped!

---

