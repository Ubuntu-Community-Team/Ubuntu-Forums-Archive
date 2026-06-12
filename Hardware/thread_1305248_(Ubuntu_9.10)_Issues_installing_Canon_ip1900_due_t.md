---
title: "(Ubuntu 9.10) Issues installing Canon ip1900 due to libcupsys2 superseded by libcups2"
date: 2009-10-29
forum: Hardware
---

### Post by Edgar Ilaga on 2009-10-29
In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
> 
$ dpkg-deb -x *cnijfilter-common_3.00-1_i386.deb* **common**
$ dpkg-deb --control *cnijfilter-common_3.00-1_i386.deb*
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
> 
$ cd DEBIAN
$ gedit control
5. In the file that opens, look for the line
> 
Depends: libc6 (>= 2.3.4-1), libcupsys2 (>= 1.2.1), libpopt0 (>= 1.7)
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
> 
$ dpkg -b **common** *cnijfilter-common_3.00-1_i386.deb*
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out!

---

### Post by dorkdork777 on 2009-10-30
Fantastic! Thanks :) any chance you could share the finished .debs with us? (Or would that be illegal, I'm not really sure)

---

### Post by Xero Xenith on 2009-10-30
Nice guide, but did you try just installing the [dummy package from Jaunty]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")?

---

### Post by headmower on 2009-10-31
Will the method stated by Edgar Ilaga work for cnijfilter-common_2.90-1_i386.deb and cnijfilter-ip2600series_2.90-1_i386.deb also???  Is there an easier solution? Thanks in advance.

---

### Post by mrfotheringham on 2009-10-31
[B]Great Help!

[/B]However could you clarify stage 6 pls

Cheers

---

### Post by uniomni on 2009-10-31
Thank you very much for the guide. My PIXMA MP630 works with Ubuntu 9.10
I'll be happy to share the resulting deps, but unsure where would be a good place to put them. 
Suggestions please

Ole

---

### Post by Edgar Ilaga on 2009-10-31
@dorkdork777
I hope that I was able to help you out. As for redistributing the finished .debs, I'd be toeing a very thin legal line regarding redistribution of modified .deb files without being able to give the license as well. I hope that Canon can clear this out.

@Xero Xenith
I haven't tried that, so I can't give you a definitive answer there. The rationale in changing the dependencies of the .deb instead of installing a transitional/dummy package is one of security for me, however - I like to make sure that every package I install can be accounted for.

@headmower
If the dependency is just libcupsys2, I don't see why the method I suggested won't work.

@mrfotheringham
Thanks for pointing that out. Executing the commands in 3. will produce 2 folders in the same location. When repackaging the driver, DEBIAN needs to be a subfolder of common. Thus, you would need to move DEBIAN into common prior to executing dpkg to build the .deb file. Hope this clears things out.

@uniomni
If you used my guide, glad the steps I outlined worked for you. Again, best to consult the license you downloaded the files under before uploading the modified .debs. Disclaimer: I am not a lawyer. :)

---

### Post by Xero Xenith on 2009-10-31
I've just finished installing my Canon MP600R - the Jaunty dummy libcupsys2 passed through any checks fine, and the printer is now working perfectly without having to follow the above. I'd be interested to know if it works for anyone else - could someone test?

---

### Post by robegea on 2009-10-31
> **Xero Xenith said:**
> I've just finished installing my Canon MP600R - the Jaunty dummy libcupsys2 passed through any checks fine, and the printer is now working perfectly without having to follow the above. I'd be interested to know if it works for anyone else - could someone test?
Finish to install my ip2600.
Got the drivers from [Canon Europe]("http://software.canon-europe.com/software/0034312.asp/") and the libcupsys2 package from [Package.Ubuntu]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download").
Installation order:
1. libcupsys2_1.3.9-17ubuntu3.1_all.deb
2. cnijfilter-common_2.90-1_i386.deb
3. cnijfilter-ip2600series_2.90-1_i386.deb
Then i used CUPS to setup the printer. Work well

---

### Post by Edgar Ilaga on 2009-10-31
I guess that would work as well, though I'd have to caution you against doing that. libcupsys2_1.3.9-17ubuntu3.1_all.deb has a published vulnerability as per [http://www.linuxsecurity.com/content/view/149025](http://www.linuxsecurity.com/content/view/149025) - and no, that package isn't a transitional or dummy package.

Given the information on hand, I personally would still recommend changing the dependency on libcupsys2 to libcups2 until a proper transitional package gets released on the Ubuntu repos.

---

### Post by mrfotheringham on 2009-10-31
[B]Long winded and didn,t work

[/B]Fixing something which aint broke. See this thread for sound and clear solution
 				 				**Re: Canon Pixma iP1900 series** 			
 			 			 		   		 		 		Hi. I've installed, properly this printer, after a while. I'm a Kubuntu Intrepid User. Greetings from Guatemala.

If you have troubles installing this printer, delete all references/tries/fails/etc related to this printer. Let's do it as we just brought from the store knowing all we need to know.

Turn off the printer (and/or unplug if necesary/wanted).

You have to download the drivers in canon-europe's site. The drivers are at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp). 
Find under "Operating System > Linux" and download "Debian Linux Printer Driver (3.0)".
Download to a folder (it's own folder) anywhere (better desktop). Then, let's go to konsole (or equivalent).

First we must install libcupsys2 with the following order:
$ sudo apt-get install libcupsys2
Next go to folder we used to download the driver:
$ cd /path/to/your/folder
Next we need to untar the dowloaded file
$ tar -xf iP1900_debian_printer.tar
Now we will have 3 files on this folder (+ original tar downloaded file).
(In my case I've untargz the "tar.gz" file inside, but don't think that this is necessary, how ever if you wanted or need to doit:
$ tar xvzf cnijfilter-common-3.00-1.tar.gz)
Then let's install:
$ sudo dpkg -i *deb
This will install the two deb packages included in the downloaded tar file that will install the proper drivers in the computer database.

Now that are installed, exit the konsole and then let's go to CUPS web manager in our favorite browser (firefox rocks) to [http://127.0.0.1:631]("http://127.0.0.1:631/")

In the page go to Admin and find the button that says "Find new printer" and then follow the assistant. 

Hope this helps someone. If you have troubles finding out what to download, this is the file my browser reports as downloaded:
[http://software.canon-europe.com/fil...an_printer.tar]("http://software.canon-europe.com/files/soft31335/software/iP1900_debian_printer.tar")

Feed back with comments.

Mario Soto
mariosoto [at sign here] cancuen [dot here] net
 		                   		  		  		  		  		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7039987") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7039987")

---

### Post by headmower on 2009-10-31
Cannot install libcupsys2, the terminal says libcup2 is replacing libcupsys2. When i downloaded the driver for canonip2600 from the site in europe it contains 4 files and I am rather confused as how to complete the process that Edgar did for the ip1900 driver. Any help at this point is appreciated as I'll have to go back to 9.04 if all else fails. Thanks in advance

---

### Post by Edgar Ilaga on 2009-10-31
@mrfotheringham
Hi, the instructions I provided are *specifically* for Ubuntu 9.10 where, as headmower observed as well, libcupsys2 has been replaced by libcups2. That is why I said in my original post
> In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2Releases before Karmic still have libcupsys2 in the official repository. Karmic doesn't have it. I hope this clears out any misconceptions.

@headmower
Hi. In which part are you having difficulties? I'll be happy to help you out.

I took a look at the package ip2600.tgz from the Canon website, and saw the 4 files you mentioned. Specifically, cnijfilter-common-2.90-1.tar.gz, cnijfilter-common-2.90-1_i386.deb, cnijfilter-ip2600series_2.90-1_i386.deb, and guideip2600series-pd-2.90-1_en.tar.gz. Of these four, *cnijfilter-common-2.90-1_i386.deb *and* cnijfilter-ip2600series_2.90-1_i386.deb* are the files you would want to modify (since these are the driver files) See attachment 1 to see the files in the ip2600_debian.tgz after extraction.

Next, I executed the commands in step 3. See attachment 2 for the output. Notice that there are two new folders - common and DEBIAN. Later on, you'll need to cut and paste DEBIAN into the common folder - but let's not worry ourselves with that until later on.

Now, you want to edit the control file that manages the dependencies of the package. Navigate to the DEBIAN folder and use gedit to open the control file. The highlighted line is what you want to change - see the libcupsys2 over there? Go ahead and change it to libcups2. (ref. attachment 3)

When you're done with that, cut and paste the DEBIAN folder into  common. Navigate back to the ip2600 folder. This time, use "dpkg -b **common** *cnijfilter-common-2.90-1_i386.deb" *to create the final .deb file. You may need to move the original .deb to another location before doing this step though, if you want to have a backup of your original file. If all goes well, you should see the output in attachment 4. Once you're done with that, double click the deb file to start up GDebi, and you should be halfway done.

Repeat the steps above with the other file, *cnijfilter-ip2600series_2.90-1_i386.deb*, substituting the file names you used originally with this one. You might want to use **ip2600 **as the folder name instead of **common** too.

If you have additional questions, feel free to post them here.

---

### Post by headmower on 2009-11-01
this is what I mean, I/m a greenhorn with the terminal. I was trying step three and I've included an attachment.

---

### Post by headmower on 2009-11-01
the attachments are where?????????????????? here is another attachment regarding my last reply.

---

### Post by Edgar Ilaga on 2009-11-01
> **headmower said:**
> this is what I mean, I/m a greenhorn with the terminal. I was trying step three and I've included an attachment.

I see what's the problem here. You're trying to enter the two commands at the same time. If that is the case, please use && to connect the commands. An example of this is seen below, if I were to combine the two extraction commands on the same line:
> $ dpkg-deb -x *cnijfilter-common_3.00-1_i386.deb* **common** && dpkg-deb --control *cnijfilter-common_3.00-1_i386.deb*

In your case, you will want to use the following line:
> $ dpkg-deb -x *cnijfilter-common_2.90-1_i386.deb* **common** && dpkg-deb --control *cnijfilter-common_2.90-1_i386.deb*

---

### Post by headmower on 2009-11-01
Hello Edgar,  I was able to alter the packages and use debinstaller but get error messages when testing printer. I've included attachment showing the error messages and attachments of the opened files that were changed.

---

### Post by Edgar Ilaga on 2009-11-01
> **headmower said:**
> Hello Edgar,  I was able to alter the packages and use debinstaller but get error messages when testing printer. I've included attachment showing the error messages and attachments of the opened files that were changed.

It's a permission error. Seems like there's a bug filed regarding that. Here's the fix:
> $ sudo chown -cR root /usr/lib/cups/filter

---

### Post by headmower on 2009-11-02
Edgar,  my printer now works. Many thanks for the great help!!!!

---

### Post by Machinista on 2009-11-02
Thank you Edgar; also worked for my iP1800 (using iP1900 drivers)

---

### Post by booksnmore4you on 2009-11-02
@[Edgar Ilaga]("http://swiss.ubuntuforums.org/member.php?u=890253")

Thank you VERY much for the guidance in solving this issue.  I'm up and running with my Canon ip2600. :popcorn: :KS:KS:KS:KS:KS

---

### Post by Shtrk on 2009-11-03
I do all the stuff, but when I thray to make .deb at the end, I got this
'control directory has bad permissions 770 (must be >=0755 and <=0775)'

what shuld I do?
thx

---

### Post by tantos on 2009-11-07
Thank you Edgar Ilaga, this tutorial can be used by Canon PIXMA iP1800 series too.

---

### Post by neviander on 2009-11-10
I had Jaunty Jackelope installed for 3 days AND had just gotten my ip1800 printing on it when I decided to upgrade to the latest, greatest 9.10 Karmic Koala, then....no more printer >:(  

I used this link  [http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/](http://www.blogternals.com/2009/07/09/canon-ip1800-ubuntu/)  to get the ip1800 up and running on 9.04 and it claims to work on 9.10 also, but it does not for me.

I'm running an AMD 64 X2 3800+ so all this i386 stuff is frustrating me.  Is there an easy way to use the existing instructions and force AMD 64 architecture?  Anybody, please, this has turned into a 3 day, after work frustration fest.

---

### Post by gamblr2355 on 2009-11-11
> **Edgar Ilaga said:**
> In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
5. In the file that opens, look for the line
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out!

I have tryed to do everything you have here and when I type the commands in the terminal is keeps saying there is no directory, how do I go about creating a directory for this? Thank you for all help

---

### Post by jaygo on 2009-11-12
thanks edgar! This got my canon mf4150 working.

---

### Post by crazy ivan on 2009-11-12
Hey Edgar, thanks for the lucid post.. The installation worked fine applying the procedure to the two .deb files of the **Canon pixma ip4600** driver (note: you have to delete the "common" directory, before executing the same operations with the second .deb package).

Now I had a bizarre problem: 

1) I can't change from Gutenprint to the Canon driver in the printer configuration
> I go to the the cups interface on [http://127.0.0.1:631/]("http://127.0.0.1:631/") and add it ther

2) Now it's in the printers where I can't reselect the Gutenprint driver and it won't print !!, always issuing the error message 

```
 'cups-insecure-filter' 
```

> Found the solution in [http://ubuntuforums.org/showthread.php?t=1313291]("http://ubuntuforums.org/showthread.php?t=1313291") and executed the following commands

```

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

```

NOW everything works great!! Thanks Edgar, thanks Linux community.. (Unfortunately I begin to loath system updates just like the old guys :-k)

---

### Post by fhyusran on 2009-11-12
Hi Edgar,

I failed to do your instruction for the second file (cnijfileter-ip1900series_3.00-1_i386.deb), eventhoug I have changed the control file:

Package: cnijfilter-ip1900series
Version: 3.00-1
Section: graphics
Priority: optional
Architecture: i386
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libcups2 (>= 1.2.1), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.10.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.12.3), libpng12-0 (>= 1.2.8rel), libpopt0 (>= 1.7), libtiff4, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxml2 (>= 2.6.24), libxrandr2, libxrender1, cnijfilter-common (>= 3.00)
Installed-Size: 8764
Maintainer: Canon Inc. <sup-debian@list.canon.co.jp>
Source: cnijfilter-common
Description: IJ Printer Driver for Linux.
 This IJ Printer Driver provides printing functions for Canon Inkjet
 printers operating under the CUPS (Common UNIX Printing System) environment.

The error message was Failed to satisfy all dependencies (broken cache).

Can you help me please?  How did you do yours, headmower?

Thanks for your attentions.

Fadly

---

### Post by DanInKtown on 2009-11-13
I'm using Ubuntu 9.10.

I tried Edgar's procedure (see #1 above) twice.

cnijfilter-common_3.00-1i386.deb installed.

cnijfilter-ip1900series_3.00-1_i386.deb did NOT install. The attempted installation yieldedd the following:

QUOTE

Error: Dependency is not satisfiable: cnijfilter-common (>=3.00)

ENDQUOTE

Is there a way I can fix the problem?

---

### Post by kio_http on 2009-11-13
Will try later on pixma 1800

---

### Post by fhyusran on 2009-11-16
I solved my problem.  Just follow [http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

Fadly

---

### Post by neviander on 2009-11-17
[http://tantos.web.id/blogs/how-to-ka...-ip1800-ip1900](http://tantos.web.id/blogs/how-to-ka...-ip1800-ip1900)

worked for me as well.  For those using an AMD64 system, use:

sudo dpkg -i --force architecture cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i --force architecture cnijfilter-ip1900series_3.00-1_i386.deb

---

### Post by space_agent on 2009-11-18
Thanks a lot for this solution Edgar. You're great! I was already thinking of changing to Debian Sid where the driver for my mp630 installs perfectly.

---

### Post by redorb on 2009-11-20
Just installed MF4690PL using the method described initially. Only the common file needed to be patched. Haven't tested the printer yet, but it installed nicely. Thanks!

---

### Post by LequidMetal on 2009-11-24
Installed the mp140 series drivers using this method . Apply this method on the 2 cjnifilter files . The other 2 scangear files dont require any changes as they dont depend on libcupsys2/cups2 .
Great tut Thanks !

---

### Post by jolfig on 2009-12-02
Thank you very much.
My printer Canon Pixma iP1900 working fine in my notebook Lenovo 3000 N200 with Ubuntu 9.10 Karmic Koala AMD64
Your fine work is a great help for me.

Jose Luis Figueroa

---

### Post by robert_edgar on 2009-12-03
> **neviander said:**
> [http://tantos.web.id/blogs/how-to-ka...-ip1800-ip1900](http://tantos.web.id/blogs/how-to-ka...-ip1800-ip1900)

worked for me as well.  For those using an AMD64 system, use:

sudo dpkg -i --force architecture cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i --force architecture cnijfilter-ip1900series_3.00-1_i386.deb

Thanks a lot neviander this worked like a dream for me. :D

---

### Post by rrkrr on 2009-12-04
Can't make this work with amd64 and ip1800 with karmic.  Printer shows up on list of printers, but does nothing when sent a job.

Worked fine under jaunty after similar driver install.

Link to "tantos...." gives "Page not found" error this morning.

Has anyone else succeeded with amd64 and ip1800 combination?

---

### Post by rrkrr on 2009-12-05
Took another stab at installing for Karmic on AMD64 with Canon ip1800 printer, using Edgar's instructions at:
[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

Now the printer does print, but only in grayscale.  Is anyone else having this problem?

---

### Post by rrkrr on 2009-12-06
Yes, well, it helps to install a new color ink cartridge .

- Had to connect printer to a windows machine to determine that the ink was low.  Is it practical to activate this useful feature in the linux driver, or are there proprietary issues?

Thanks to all who developed the fix and posted how-tos. Canon Pixma ip1800 is now printing well here in karmic amd64.

---

### Post by dublea on 2009-12-14
I've attempted your fix.  I get all the way to the last step.  I use this command
```
$ dpkg -b common cndrvcups-common_1.90-1_i386.deb
```
And this is what happens. 
```
dpkg-deb: failed to open package info file `common/DEBIAN/control' for reading: No such file or directory
```
The DEBIAN folder has been copied and it contains the 'control' file.

I have a Canon MF4150.  I see someone else was able to get this to work.  Any advice would help.

---

### Post by Chrisco66 on 2009-12-17
Ok, I tried the procedure 4 times now.  It seems to install all the created files correctly, but then I get a fault saying insecure filter.  The computer always sees the printer and identifies it correctly, but now it acts like there is no driver installed.  It keeps trying to go online to find one.  We all know that wont work. After the first failure, I rechecked my work, and it all seemed right.  After the second failure I decided to start from scratch.  Same result for both attempts.  Computer sees printer but will not print.  Third attempt, it acts like the driver is not there and continues to ask for a driver. Fourth attempt, now it says insecure filter.  Whatever that means--lol.  If anyone want to send me the completed debs that made your printer work, I would appreciate it.   I must be doing something wrong because the solution has worked for so many others.  BTW thanks to Edgar for figuring this thing out, even if I cant follow instructions--lol

---

### Post by cmarslett on 2009-12-17
Thanks again, Edgar, that was a quick and easy explanation of how to fix the issue by myself.

With the file name changed (cndrvcups-common_1.90-1_i386.deb instead of cnijfilter-common_3.00-1_i386.deb) I got my MF4270 working as well as it ever did!=D>

---

### Post by HeinzVoerbakje on 2010-01-06
I had the same problem, but partially solved it with the steps described in this thread. However, one error remains:

ERROR:
Printer 'Canon-iP2600-series' requires the 'pstocanonij' program but it is not currently installed.  Please install it before using this printer.

However, this file is present in /usr/lib/cups/filter, with permissions set to Root:Root

Who can help me get my printer to work?

Thanks, HeinzVoerbakje

---

### Post by Azati Prime on 2010-01-09
I followed your instructions for my ip2600 (using the proper drivers of course) and since I have a 64-bit system I had to use
```
sudo dpkg -i --force architecture cnijfilter-common_3.00-1_i386.deb
```

Everything seemed to work fine and when I plugged my printer in I got a message that the printer had installed fine.  When I went to print a test page I got an error that the job was stopped because the scheduler could not execute a filter.  The printer has a status message.
> Printer 'iP2600-series': 'cups-insecure-filter'.

Any ideas?

---

### Post by vyszard on 2010-01-13
> **Shtrk said:**
> I do all the stuff, but when I thray to make .deb at the end, I got this
'control directory has bad permissions 770 (must be >=0755 and <=0775)'

what shuld I do?
thx

@Edgar Ilaga:

Seconded this. I had the same problem when I tried to install driver for MP145. What should I do?

---

### Post by psywho on 2010-01-14
thx a lot man, solved it just fine. 

> **Edgar Ilaga said:**
> In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
5. In the file that opens, look for the line
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out!

---

### Post by warfie on 2010-02-08
Hi people,

Ubuntu 9.10 AMD64 (first time to try 64bit)
I've been fighting with this for an hour or so following all the suggestions in this thread... Finally decided to give it a rest for a while before I went and did something stupid like installing Winslow.

So while I was taking a break I installed the latest Skype for Linux beta and I noticed that while it was installing it loaded some 'lib32' packages...

Once that was finished I got licupsys2 from [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download) and reinstalled the standard Canon drivers with the --force switch:

sudo dpkg -i --force architecture cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i --force architecture cnijfilter-ip1900series_3.00-1_i386.deb

and it worked perfectly!

I hope this helps someone...

---

### Post by Azati Prime on 2010-02-12
> **warfie said:**
> Hi people,

Ubuntu 9.10 AMD64 (first time to try 64bit)
I've been fighting with this for an hour or so following all the suggestions in this thread... Finally decided to give it a rest for a while before I went and did something stupid like installing Winslow.

So while I was taking a break I installed the latest Skype for Linux beta and I noticed that while it was installing it loaded some 'lib32' packages...

Once that was finished I got licupsys2 from [http://packages.ubuntu.com/jaunty/all/libcupsys2/download](http://packages.ubuntu.com/jaunty/all/libcupsys2/download) and reinstalled the standard Canon drivers with the --force switch:

sudo dpkg -i --force architecture cnijfilter-common_3.00-1_i386.deb
sudo dpkg -i --force architecture cnijfilter-ip1900series_3.00-1_i386.deb

and it worked perfectly!

I hope this helps someone...


Nope.  I still get the same errors.  :-( Looks like I'll be doing my printing on windows still.

EDIT: I spoke too soon.  There's a fix here that worked perfectly for me.  [http://ubuntuforums.org/showthread.php?t=1313291](http://ubuntuforums.org/showthread.php?t=1313291)

---

### Post by bigred1 on 2010-02-22
[This]("http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900") worked for me.

---

### Post by ahrojm on 2010-02-27
This also worked for me: [http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

for an ip1800 printer.

Thank you very much.

---

### Post by Ian D on 2010-03-08
Many thanks Edgar for your guide - I just used it to install my Canon iP4600 on Ubuntu 9.10 32bit. I also needed to put ```
sudo chown -cR root /usr/lib/cups/filter
``` into Terminal to stop the error messages coming up, as headmower had to. Many thanks for the advice! About time Canon updated the drivers on their site though...?

The only issue now is that the driver only seems to be able to print 600dpi, with no draft or high quality, or even black & white options available. In fact, it doesn't seem to alert when ink cartridges are getting low either... is there something else that needs to be enabled? Very glad to at least be able to print though. Hopefully there's another driver lurking around that will allow me to print borderless without having to boot into Windows!

---

### Post by nuchdog on 2010-03-08
I also had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

in addition to what Ian said above.

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF

---

### Post by nuchdog on 2010-03-08
double posted some how..

---

### Post by Sematary on 2010-03-15
> **Xero Xenith said:**
> Nice guide, but did you try just installing the [dummy package from Jaunty]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download")?

I want to thank you from the bottom of my heart for posting this. I tried EVERYTHING to get my ip2600 to work over the network (connected to a Windows7 machine) but THIS worked. THANK YOU!

---

### Post by trinetra on 2010-04-06
> **rrkrr said:**
> Took another stab at installing for Karmic on AMD64 with Canon ip1800 printer, using Edgar's instructions at:
[http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900](http://tantos.web.id/blogs/how-to-karmic-koala-and-canon-pixma-ip1800-ip1900)

Now the printer does print, but only in grayscale.  Is anyone else having this problem?
This worked instantly. Thanks a lot.

---

### Post by yrnajraven on 2010-04-19
What helped me upon installing my iP1980 canon pixma printer were:

I. Firstly, make sure that the printer is shut off. then, follow the guide in the first post of this thread,. 
II. Delete the non-working printer in your Printer Configuration (System -> Administration -> Printing)
III. Follow these commands:

> sudo chown -hR root/usr/lib/cups/filter
sudo chown -hR root/usr/lib/cups/backend
sudo chgrp -hR root/usr/lib/cups/filter
sudo chgrp -hR root/usr/lib/cups/backend

IV. Then, power on the printer and go to Printer Configuration and let it detect the printer.. 

THanks to my fellow pinoy for sharing the guide.. and for those who shared the terminal codes, i found them at the General Help section..

---

### Post by shifin on 2010-05-22
I've tried Edgar's instructions until step 6. Then I faced the same problem as @dubela in post #41.


After I typed this command in terminal:

```
dpkg -b common cnijfilter-common_2.80-1_i386.deb
```

This was the error I got:

```
dpkg-deb: failed to open package info file `common/DEBIAN/control' for reading: No such file or directory
```

I've checked the directory /common/DEBIAN and the file "control" is there. I tried to open the file without any problem. Yet I can't create the deb file. What should I do?

---

### Post by cakranet_UNIS_tangerang on 2010-05-28
Hi, I just upgrade my internet cafe server from 9.10 to Ubuntu 10.04 and try to install Canon IP1900 printer. I tried information here and it works well for me.

First follow Edgar's post to rebuild .deb files using libcups2.

After that I get problem can not execute filter. Then I do Crazy Ivan's post :

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Now I can install the printer. Thanks All.

---

### Post by mindy on 2010-06-24
Thanks Edgar for the detailed instructions! It worked for the common file, but I had the same problems in installation as DanInKtown for the ip1900series file. Please help!

> **DanInKtown said:**
> I'm using Ubuntu 9.10.

I tried Edgar's procedure (see #1 above) twice.

cnijfilter-common_3.00-1i386.deb installed.

cnijfilter-ip1900series_3.00-1_i386.deb did NOT install. The attempted installation yieldedd the following:

QUOTE

Error: Dependency is not satisfiable: cnijfilter-common (>=3.00)

ENDQUOTE

Is there a way I can fix the problem?

---

### Post by mindy on 2010-06-24
So finally the ip1900 series file installed properly all of a sudden, and I tried printing but there was an error executing filter. I tried the instructions here, but this is what I got: 
mins@mins:~$ sudo chown -hR root/usr/lib/cups/filter
chown: missing operand after `root/usr/lib/cups/filter'
Try `chown --help' for more information.

What do I do now? I am lost!

> **yrnajraven said:**
> What helped me upon installing my iP1980 canon pixma printer were:

I. Firstly, make sure that the printer is shut off. then, follow the guide in the first post of this thread,. 
II. Delete the non-working printer in your Printer Configuration (System -> Administration -> Printing)
III. Follow these commands:



IV. Then, power on the printer and go to Printer Configuration and let it detect the printer.. 

THanks to my fellow pinoy for sharing the guide.. and for those who shared the terminal codes, i found them at the General Help section..

---

### Post by mayur.shetye on 2010-07-11
Thanks a lot .......U rock!   :KS:KS:KS:KS:KS

---

### Post by whiteman on 2010-12-19
Look I have spent three days, installing, reinstalling, going from 9.04 to Lynx....messing up my configs, getting wierd error messages. I even tried to reinstall windowze!! I have been w/Ubuntu since 8.04. But Jaunty was the last one that allowed my canon mp470 to even be found. It was invisible.
UNTIL
I installed a thing called Turboprint.
turboprint 2.17_i386.deb to be exact. IT WORKED. Dont know about the sharing yet, but Im happy just to see my canon prtr on the desktop again. Like I said I dont know about that cupsys, libcupsys debate. I think thats the crux of the whole thing, except I never could get Karmic to work either. In fact all I could do with that was sign on in Failsafe. It wouldnt allow me to login.
So anyway..turbo works for me...now anyway.

---

### Post by phoenyo on 2010-12-22
Thanks! it works for me in Canon iP 1900 printer. :)

---

### Post by togarika on 2011-01-06
thanks

---

### Post by sipper6221 on 2011-01-25
Hy Edgar .....

I have to say THANK YOU for this perfect Tutorial..   You have done  a great work... My PRINTER WORKS because of YOU ....

THX

---

### Post by deadlytackler on 2011-02-02
> **Edgar Ilaga said:**
> In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
5. In the file that opens, look for the line
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out!

Dear Edgar,
Me and three other fellows in this thread are having same problem> till 6th point evertthing is fine but then it showing erroe message here is what it's saying:-

deadlytackler@deadlytackler-desktop:~$ cd /home/deadlytackler/Downloads/common
deadlytackler@deadlytackler-desktop:~/Downloads/common$ dpkg -b common cnijfilter-common_2.80-1_i386.deb
dpkg-deb: failed to open package info file `common/DEBIAN/control' for reading: No such file or directory
y

but file is there somehow terminal is not recognising.

HELP!!!!!!!!

---

### Post by this_costs_more_cell_bill on 2011-02-16
> **Xero Xenith said:**
> I've just finished installing my Canon MP600R - the Jaunty dummy libcupsys2 passed through any checks fine, and the printer is now working perfectly without having to follow the above. I'd be interested to know if it works for anyone else - could someone test?
Jaunty dummy libcupsys2 is not available anymore - at least I couldn't open a valid page from any Jaunty link.
So you either use the libcupsys2 from [http://packages.ubuntu.com/dapper/libcupsys2](http://packages.ubuntu.com/dapper/libcupsys2) with its security problem, either do Edgar Ilaga steps above.

---

### Post by this_costs_more_cell_bill on 2011-02-17
> **deadlytackler said:**
> Dear Edgar,
Me and three other fellows in this thread are having same problem> till 6th point evertthing is fine but then it showing erroe message here is what it's saying:-

deadlytackler@deadlytackler-desktop:~$ cd /home/deadlytackler/Downloads/common
deadlytackler@deadlytackler-desktop:~/Downloads/common$ dpkg -b common cnijfilter-common_2.80-1_i386.deb
dpkg-deb: failed to open package info file `common/DEBIAN/control' for reading: No such file or directory
y

but file is there somehow terminal is not recognising.

HELP!!!!!!!!
I guess you resolved it somehow (in 5 months) but for the sake of this thread really being [SOLVED]:
1) you should assure the whole DEBIAN folder you copied has Read right available for everybody:
[B]chmod -R 444 /home/deadlytackler/Downloads/common/DEBIAN
[/B]2) you should better do these installation operations using root rights (**sudo **in Ubuntu):[B]
sudo dpkg -b common cnijfilter-common_2.80-1_i386.deb

Anyway, thanks to [/B][B]Edgar Ilaga, I was able to write a general tutorial for all CANON printers, here, where I added dome steps Edgar didn't talk about:
[http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon](http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon)
[/B]

---

### Post by irishhermit on 2011-03-12
Thanks Edgar,

I got my Canon IP2600 working on Ubuntu 10.04 LTS.  I did have to change the permissions to root at the end.  Your tutorial rocks!

Tom Gosse

---

### Post by enieffak on 2011-05-03
> **this_costs_more_cell_bill said:**
> I guess you resolved it somehow (in 5 months) but for the sake of this thread really being [SOLVED]:
1) you should assure the whole DEBIAN folder you copied has Read right available for everybody:
[B]chmod -R 444 /home/deadlytackler/Downloads/common/DEBIAN
[/B]2) you should better do these installation operations using root rights (**sudo **in Ubuntu):[B]
sudo dpkg -b common cnijfilter-common_2.80-1_i386.deb

Anyway, thanks to [/B][B]Edgar Ilaga, I was able to right a general tutorial for all CANON printers, here, where I added dome steps Edgar didn't talk about:
[http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon](http://ubuntuforums.org/showthread.php?t=1689097&highlight=canon)
[/B]



Is this still valid for Ubuntu 11.04 amd64?

If I enter > sudo cp DEBIAN/ common/ 
I get > cp: omitting directory `DEBIAN/'.

---

### Post by zylmurbafi on 2011-05-18
Hi Edgar
Trying to instal the PIXMA 4600 with Ubuntu 10.10
Followed your initial instructions, changing all to ip4600 series and the libcupsys2 references to libcps2.
Created OK both common and ip4600 .deb files and both installed OK.
Then picked the (new) ip4600 from the list of drivers.

Doesn't work. 
I have discovered two error messages:

At Printing/server/settings/Problems? [Printing Troubleshooter] it says: Filter"/usr/lib/cups/filter/pstocanonij" for printer "ip4600" not ownded by root.

When I submit a Test page the printing stops immediately warning: Stopping job because the scheduler could not execute a filter.

I would v much appreciate your comments
Franz

---

### Post by klian87 on 2011-08-24
[QUOTE=Edgar Ilaga;8191956]In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
5. In the file that opens, look for the line
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out
this is amazing but if it fails to print & say "cups insecure filter"
type it in terminal
$ sudo chown root:root /usr/lib/cups/filter/pstocanonij.

---

### Post by chinner459 on 2011-09-18
> **Edgar Ilaga said:**
> In the Ubuntu 9.04 release,  cnijfilter-common_3.00-1_i386.deb file depended on libcupsys2. Now, I've just learned that 9.10 scrapped libcupsys2 in favor of libcups2, which is causing broken dependency issues in Ubuntu due to missing symbolic links, as I've been told. Any idea as to how I can resolve this? Any help appreciated. Thanks!

Update: Just finished resolving the issues stated here. Here's what I did:
1. Download Debian drivers over at [http://software.canon-europe.com/products/0010647.asp](http://software.canon-europe.com/products/0010647.asp)
2. Extract the file (*iP1900_debian_printer.ta*r) to desktop; there should be 3 files produced from there. *cnijfilter-common_3.00-1_i386.deb*; *cnijfilter-ip1900series_3.00-1_i386.deb*; and *common_3.00-1.tar.gz*
3. We'll first repackage the common .deb. Open up a terminal window and navigate to your desktop. There, type the following commands:
4. You should now see two new folders - **common** and **DEBIAN**. What we need to do is to change the file *control* in **DEBIAN** to reflect libcups2. So go ahead and type:
5. In the file that opens, look for the line
and change *libcupsys2* to *libcups2*. Save the file.
6. Now, copy the entire** DEBIAN** folder into **common**. We now need to repackage these into a .deb. So, open up a new terminal, navigate to where **common** is, and go ahead and type in the terminal:
and double-click on the resulting .deb file to install the file.
7. Do steps 1-6  for *cnijfilter-ip1900series_3.00-1_i386.deb, *with the exception that you should type in  *cnijfilter-ip1900series_3.00-1_i386.deb *and substitute **ip1900** for **common** wherever it appears above.

Hope this helps you all out!
I have been trying to solve this problem for the Canon iP4600 as the download file seems to be the same.  I have had a modicum of success but every time it fails at the re-packaging stage. I have added a screen shot showing all stages of this in the hope you can help this poor soul.

---

### Post by iivanoff on 2011-12-05
Thanks Edgar, great post! I now run my ip3600 smoothly on 64bit Ubuntu 11.04. Just to note that only changing the libcupsys2 to libcups2 dependancy ref did not help. After trying to install the deb file, there were still dependencies issues and I had to completely remove all of them in the control file. Cheers.

---

### Post by sams0n on 2011-12-25
Thanks Edgar for making my printer works in Ubuntu.

For those who is not familiar with the command line or who wants to save all the troubles modifying the deb files, here you can download the modified version directly.

[https://skydrive.live.com/redir.aspx?cid=3f4cf8fc74f13a9a&resid=3F4CF8FC74F13A9A!489&parid=root]("https://skydrive.live.com/redir.aspx?cid=3f4cf8fc74f13a9a&resid=3F4CF8FC74F13A9A!489&parid=root")


It should fix your problem, I tested it on Ubuntu 11.10.

Don't forget to run the following command in terminal after installing both deb packages.


```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

---

### Post by Bryan55 on 2012-02-04
This way is so easy

> No more fooling around with making any files.

This site shows you how to do the ppa route and install what you need no matter x86 or x64.

[http://www.ubuntubuzz.com/2011/06/do...er-driver.html](http://www.ubuntubuzz.com/2011/06/do...er-driver.html)

---

### Post by edmund085 on 2012-07-31
after 4 hours of finishing this.... and successfully worked... I cried!!!!!!!!

---

### Post by enieffak on 2012-07-31
> **edmund085 said:**
> after 4 hours of finishing this.... and successfully worked... I cried!!!!!!!!

Congratulations. :)

As I can relate to your experience I will make sure not to buy things that don't work well either out-of-the-box or with little effort.

---

### Post by ikem.krueger on 2012-08-28
> **crazy ivan said:**
> ```

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

```
You can reduce that to:
```

sudo chown -R root:root /usr/lib/cups/backend
sudo chown -R root:root /usr/lib/cups/filter

```

---

