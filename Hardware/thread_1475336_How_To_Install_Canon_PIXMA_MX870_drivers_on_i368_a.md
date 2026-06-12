---
title: "How To: Install Canon PIXMA MX870 drivers on i368 and 64bit ubuntu"
date: 2010-05-06
forum: Hardware
---

### Post by thewump on 2010-05-06
UPDATED FOR SCANNER DRIVER TOO.

This took a while and I didn't find the information elsewhere, so thought I'd throw the information here in case anyone else is looking for it!

**1) PRINTING**
Firstly, get the 32 bit printer drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html)

Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf cnij*
cd cnij*

```

Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```

and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```

and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```

Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```

and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```


**2) SCANNING**
Thanks to others in this thread for doing the groundwork on scanning too.  The process is very similar.  I think for 386 installs of Ubuntu it should "just work".

Download the scanner driver from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html]()


Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf scan*
cd scan*

```

Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```

and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```

and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```

Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```

and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```

Now.. You've just installed drivers AND a scanner app.  To use the scanner app you have to run it.  Hit ALT-F2 to pull up the run command and type "scangearmp".  You should see a dialog box about scanners (first time it might say "NOT FOUND" but if you follow your nose, it will find the scanner and add it to the available list.  To make life easier, make a launcher on your desktop for scangearmp for future use.


K

---

### Post by CiscoPenguin on 2010-05-06
Thank You!!

I learned the hard way that 64 bit print drivers are a pain in the neck.

---

### Post by dadasfx on 2010-06-17
Hi. This driver is for 9.10 now and I cant instal it :( I am running 10.04 (32bit).  What can I do?

[[IMG]http://img571.imageshack.us/img571/6264/snmekobrazovky.th.png[/IMG]]("http://img571.imageshack.us/i/snmekobrazovky.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by IceDoE on 2010-07-21
I think I have the same problem as dadasfx. When I try to ./install.sh it tells me:
"An error occurred. The package management system cannot be identified."

---

### Post by thewump on 2010-07-21
.. then I don't think you are doing this step propery:

    ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

See the help above. All the lines except C_system="deb" need a "#" in front of them so they are ignored.

K

---

### Post by rbosaz on 2010-07-25
Thank you for the instructions.

In case it is not obvious, you can install the scangearmp driver following the same instructions, but first you need to download the 32 bit drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html)

After you install the drivers run the scangearmp in terminal, update your scanner list and you should be all set.

---

### Post by IceDoE on 2010-07-27
After some searching, I also found that TurboPrint for Linux gets it working pretty easily. I just downloaded the trial version and it set it up, and it seems I don't need to keep the program around after it does the initial setup either so hopefully no worries about needing to buy the program after the trial period.

---

### Post by RadioZEK on 2010-07-27
Thanks a bunch for this informative post!  I just ordered an MX870 Sunday evening so I'll be needing to install the drivers soon.  I'm very inexperienced at Ubuntu and really appreciate your help, especially considering that I'm running the 64-bit version which apparently is much more complicated than the 32-bit version.  I'll let you know if I have any troubles.

---

### Post by IceDoE on 2010-08-03
Alright so TurboPrint helps get the printer going. 

However, I cannot use the scanner wirelessly using turboprint it seems, and Simple Scan does not detect the scanner (I presume because its a wireless, networked scanner). 

I don't know if the wireless scanner works using the drivers from canon, as those are 9.10 drivers and don't seem to work with 10.04 which I have.

---

### Post by jimmoor on 2010-08-20
:popcorn: Thanks for your research. The directions are very accurate and my MX870 is working like a charm on Ubantu!! Thanks

---

### Post by IceDoE on 2010-08-26
hey, switched to the driver fix you provided for this 10.04 machine. Works and Scanner installed too. 

However, I still can't seem to use the scanner wirelessly. Simple scan at least can't detect a scanner, but I'm not sure its setup to look for a network one.

---

### Post by irenicwanderer on 2010-09-15
The 32bit install was a snap. Thank you [rbosaz]("http://ubuntuforums.org/member.php?u=1118294") and [thewump]("http://ubuntuforums.org/member.php?u=207638")!

---

### Post by Samushighwind on 2010-09-15
Hey, thanks, I'm running 64 bit and the printer works great

I used the same method for this scanner driver:

[http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html)

However upon running the shell file I got this message:

```
==================================================

ScanGear MP Ver.1.50-1 for Linux
Copyright CANON INC. 2007-2010
All Rights Reserved.

==================================================
An error occurred. A necessary package could not be found in the proper location.

```

Any ideas?

---

### Post by tinfoilhat on 2010-10-01
Excellent.  Thanks.  Did the trick no issues.

---

### Post by CelticWhisper on 2010-10-01
I'm having problems scanning even over USB, running Lucid amd64.  I run scangearmp (with and without root privileges, makes no difference) and while it seems to recognize that a scanner or scanner driver is present (the window shows "Canon MX870 series (libusb:001:005)" in a drop-down menu), clicking "Update Scanner List" results in a bouncing progress bar that just stays there.

Is updating the scanner list supposed to take an obscenely long time?  I left it for as long as 10 minutes solid but nothing happened.

Printing works fine so I know the USB connection is good.

---

### Post by digitaria on 2010-10-03
Hi

The instructions worked for me on i386, 10.04, but for a Pixma MX350.  Thanks!

I had to comment the same lines in the install.sh script - the instructions suggest this will only be necessary on 64 bit, but before commenting out that portion of the script, I got 

"An error occurred. The package management system cannot be identified."

---

### Post by akish on 2010-10-11
Thanks a lot for the advice everyone.  I had no problems installing the driver and getting it to work.  I didn't even have to modify any of the code.  Thanks!

---

### Post by lokawa on 2010-10-17
Thanks for this information.  I was able to download both the printer and scanner drives.  Printer works fine, but "Simple Scan" does not find the scanner.

I had to add the printer.

How do I add the scanner?

Lokawa

---

### Post by owensky on 2010-10-18
Hi,

I'm installing my Canon PIXMA IP2700 using the procedure outlined above and the guide from Canon

I got stucked in the registering printer name part
I get the following message (see attached image)

Any help is appreciated. I'm using Ubuntu 10

Owen

---

### Post by k3vmcd on 2010-10-31
I'm stuck on getting the scanner to work as well.

Following the install guide I was able to get the printer up and running on a 64bit desktop and 32bit laptop running Ubuntu 10.10, but the scanner driver did not want to cooperate.  I attempted a wireless connection first, but then tried a USB hookup to be sure the driver was the issue and not the connection.

It appears that the scanner driver install is crashing while running "ldconfig".  Could this be because the driver is written for 9.04?

My current workaround is to leave a media card in the printer to which I save scans and then access them over my network and copy them to my computer.  The minor problem I've run into is that Ubuntu keeps telling me the file contains no data.  Although after I copy the file over it opens up perfectly.  I successfully tested a .jpg scan, but my .pdf test has gotten me nowhere so far, Ubuntu insists that the file contains no data.  Yet, if I plug the memory card into the computer's slot, the same .pdf file opens immediately.  So I don't know what is going on there.

If anybody has any more ideas, please let me know.

---

### Post by 21sdstny on 2010-10-31
Has anyone tried this with PIXMA MX350 on Ubuntu 10.10.

I have tried with the drivers from canon but receiving the same error as stated in this thread.  Can I apply the same logic here with this driver and version of Ubuntu.

Many thanks
PS newbie to Ubuntu - tried other Linux distros but find Ubuntu the easiest to follow.

---

### Post by digitaria on 2010-10-31
> **21sdstny said:**
> Has anyone tried this with PIXMA MX350 on Ubuntu 10.10.

I have tried with the drivers from canon but receiving the same error as stated in this thread.  Can I apply the same logic here with this driver and version of Ubuntu.

Many thanks
PS newbie to Ubuntu - tried other Linux distros but find Ubuntu the easiest to follow.

See [_my previous post_]("http://ubuntuforums.org/showpost.php?p=9919990&postcount=16").  I imagine the same will apply on 10.10.

---

### Post by GenePayne on 2010-11-13
Thanks for the driver installation info! I did the 32-bit install for my Canon MX870, but like someone else in this thread, I had to make the modification to the install.sh to prevent it from detecting rpm on my system to avoid the error message:
> An error occurred. The package management system cannot be identified.

After that install was smooth and printing is great. I haven't gotten to the scanner part yet but it looks like I'll have to connect direct to USB for that.

---

### Post by taterhunter on 2010-12-01
> **IceDoE said:**
> 
However, I still can't seem to use the scanner wirelessly. Simple scan at least can't detect a scanner, but I'm not sure its setup to look for a network one.

I'm having the same problem.  The driver install instructions worked like a charm (THANKS!) and I can print wirelessly fine, but no love on the scanning.  Did anybody ever find a solution to this (that doesn't involve shuttling an SD card between the scanner and computer?)

Thanks in advance.  I don't know what I'd do without the "community".

---

### Post by jwaclawsky on 2010-12-05
> **thewump said:**
> This took a while and I didn't find the information elsewhere, so thought I'd throw the information here in case anyone else is looking for it!

Firstly, get the 32 bit drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html)

Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf cnij*
cd cnij*

```

Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```

and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```

and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```

Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```

and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```

K

I have an 32 bit system and got the 32 bit drivers from Asia. Thanks! your advice (quoted in this response) worked great for my Cannon MX870 for printing. However, I am unable to get the scanner working. Is this driver only for printing? 

I am using Ubuntu 10.04 and connected with an Ethernet cable to a Linksys wireless router. The wireless router is connected to the Cannon MX870 both by wireless and by an ethernet connection. The printer prints fine. But Simple scan returns a message "No scanners detected". I tried with Xsane and got "no devices available". Can anyone tell me if the driver I installed has scanner support or some way to get the scanner installed? 
Many thanks

---

### Post by IcarusR on 2010-12-07
> Can anyone tell me if the driver I installed has scanner support or some way to get the scanner installed? 

If you followed the instructions in post 1 then this is what you installed...
> MX870 series IJ Printer Driver Ver. 3.30 for Linux (debian Packagearchive)

Read earlier posts & look for link to download scangear.

---

### Post by RafikiSanchez on 2010-12-28
Hi, when I make the required changes and run that script, I keep getting "bad for loop variable" errors. the for loop was in the format:

```
for (( i=0;i<$variable;i++))
```

I changed this loop to a while loop in the format:

```
i=0
while [ $i<$variable ]; do
  this
  i=`expr $i + 1`
done
```

in 3 places. This got rid of the for loop error, but I still can't get it the install to run correctly. It begins to execute install.sh like its going to work, then dies unexpectedly here:

```
#=========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]2

Searching for printers...
install.sh: 1683: Bad substitution

```

Any idea why this could be happening? I'm VERY new to this, but I'm a veteran web developer. If whoever reads this needs to see the loops I editted, please let me know and I can provide them. Thanks in advance!

---

### Post by RafikiSanchez on 2010-12-28
Hi, I got the printer working by using the 'add a printer' GUI, but I'd still like to know why the install.sh script wasn't running out of curiosity.. Thanks guys.

---

### Post by Alejandro Castanaza on 2010-12-28
About Simple Scan not finding the scanner: look in the GIMP. The Canon Scangear installs in the GIMP, when it was standard in 9.04.
Please tell me if this works, if it does, I will install it in my new 64bit Ubuntu, since yesterday I found that it does not install due to the different platform.

---

### Post by RafikiSanchez on 2010-12-28
To use scanner once you've followed the instructions above to install it with this download:

[http://software.canon-europe.com/software/0038683.asp?model=]("http://software.canon-europe.com/software/0038683.asp?model=")

and this file:

```
scangearmp-mx870series-1.50-1-i386-deb.tar.gz
```

Open the ScanGear program with:

```
alt + F2
scangearmp
```

or from the terminal:
```
scangearmp &
```

It comes up first with "unable to find scanner," or something to that effect.
Click "Update Scanner List" and it should find your mx870, networked or usb, if its on. You have to scan documents from the ScanGear application, at least on mine, it won't automatically work from the scanner.

Let me know if this helps anyone.

---

### Post by shammydog on 2010-12-29
Nice writeup, thank you.  I am running 32 bit 10.04 and had to comment out the install.sh to force C_system=deb per the instructions for 64 bit.  Otherwise installed perfectly.

---

### Post by xhenxhe on 2010-12-29
> **rbosaz said:**
> Thank you for the instructions.

In case it is not obvious, you can install the scangearmp driver following the same instructions, but first you need to download the 32 bit drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html)

After you install the drivers run the scangearmp in terminal, update your scanner list and you should be all set.

AWESOME! Thank you, thank you.

---

### Post by davidanderica on 2010-12-30
After using your installation instructions, 32-bit version on Ubuntu 10.10 on 64-bit system, commenting out as you said etc. printing wireless repeatedly failed, for days. As a last ditch effort before throwing my printer at my notebook and then against the wall ](*,), anyways my hostname was the default when I set my install up, in my case it was way to long.  So...

So uninstall the driver, ... 
```
sudo cnijfilter-mx870series-pkgconfig.sh --uninstall 
```

Rename to something shorter 
```
sudo gedit /etc/hostname
``` and save

Install again
```
sudo ./install.sh 
```

Thank you for your instructions sir.

---

### Post by teranine on 2011-01-01
Running Ubuntu 10.10 64 bit.  Downloaded the 32bit drivers and commented out or changed lines of code in the install.sh file as instructed.  When I run the install.sh script, it processes the deb files just fine but does not see the printer on the network.  Here's the command line:

```

chris@yuriko:~/projects/cnijfilter-mx870series-3.30-1-i386-deb$ ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 145975 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.30-1 (using .../cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.30-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-mx870series_3.30-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 145975 files and directories currently installed.)
Preparing to replace cnijfilter-mx870series 3.30-1 (using .../cnijfilter-mx870series_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-mx870series ...
Setting up cnijfilter-mx870series (3.30-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...
sudo: unable to execute /usr/lib/cups/backend/cnijusb: No such file or directory


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0]

```

What is this error message:

```

sudo: unable to execute /usr/lib/cups/backend/cnijusb: No such file or directory

```

My mx870 printer is connected to my wifi router and is working fine with my wife's laptop (running windows 7) as she is able to print to it wirelessly.  I can also print to it wirelessly via VirtualBox / WinXP.

Please help :)

---

### Post by Tigerkermit on 2011-01-04
I am using LTS 10.04 on a  64 bit system.
Following the instructions, I could install the printer driver and the scan driver !
Thank you very much !! ):P

However the SCAN does only work by using ALT + F2 and entering 'scangearmp'

with any other Scan program it does not work !

Has anyone an idea ? :confused:

---

### Post by Alejandro Castanaza on 2011-01-04
Hi. Thank you very much.
I followed the instructions and my printer is working ok wirelessly in my ubuntu 10.10 64bit.
However, the scanner installs, but when I try to run scangear, it outputs this:

scangearmp: error while loading shared libraries: libgimp-2.0.so.0: cannot open shared object file: No such file or directory


(I installed gimp because of the libgimp-2.0 module. Before installing gimp the install script failed because of said library missing.)
Also, mine is a Canon Pixma MP560. the driver is the scangearmp 1.40.
Please help.

---

### Post by Tigerkermit on 2011-01-06
Just I like to remind you to be very carefull with installing libraries. I just killed my entire Ubuntu due to installation of glib library which was said to be missed.
I am sure it was my own fault but if you are not well known to Linux be careful.

---

### Post by Tigerkermit on 2011-01-06
Hi,
I just tried to install on the Ubuntu 10.10 64 bist system as I did before with the 10,04 LTS
However, I have now the same problem as 'teranine'.

By executing the install.sh I get :

Searching for printers...
sudo: unable to execute /usr/lib/cups/backend/cnijusb: Datei oder Verzeichnis nicht gefunden


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0]

Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

This repead endless.

The printer is wokring with USB.

Any idea ?

---

### Post by thewump on 2011-01-06
Hmm.  I have a newer machine I can try an install with.  I'll try and get back to you later today.

Keith

---

### Post by Tigerkermit on 2011-01-06
Hello Keith,
thanks for your investigations.
I just recognized that I also can not print from USB.
The printer was detected and installed as USB printer when I did add with the printer tool.
However when I start a print job it shows that job is on hold.
When I run a diagnosis I get 
/usr/lib/cups/filter/pstocanonij failed

I get a long list with the debug tool.
Hear jsut the first lines which may help ?

age 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest MX870-series (default)>,
 'cups_instance': None,
 'cups_queue': 'MX870-series',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):

Thanks for any advise.
Ralph

---

### Post by skellam on 2011-01-06
Just wanted to say thank!!  I have Ubuntu 64 bit and I followed your directions and it worked the first time....  Saved me a lot of work.

---

### Post by negotiation on 2011-01-06
Tx, **printer** working great networked wirelessly on 10.04 32bit. Just double clicked on 'install.sh' and chose to 'run in terminal', and then proceeded to find printer to complete adding a new printer in:>System >Administration > Printing >Add (i.e. printer setup).

**Scanner** also works using '_scangearmp_' command wirelessly - BUT only 1 page at a time, requiring that you lift the lid, place each page face down onto the scanner glass. Looks like scangearmp software doesn't allow you to use the scanners auto page feeder, which means you won't be able to scan multiple documents. Haven't tried USB.
scangearmp software creates larger size files than XSane software. Sadly XSane doesn't detect the networked printer. (but likely will detect via USB)

---

### Post by Walther -FI- on 2011-01-08
Hello,

Just wanted to bump in - I have Canon Pixma MG5150 and got the driver working with the same hacks. This howto should be made more generous and more easily available.

---

### Post by Alejandro Castanaza on 2011-01-09
I myself am also thankful for the instructions, as I have already posted, I'm also printing wirelessly in my Ubuntu 10.10 64bit.
Has anyone have any success installing scangearmp to ubuntu 10.10 64bit?
If so how?
I followed the same instructions as for the printer driver but it does not work.
Please help.

---

### Post by NathanPowel on 2011-01-20
I just installed my MX870 with a wired ethernet connection and got it to work as both a printer and a scanner using these directions.  I will point out, from experience, that it is important to use the install.sh script that comes with the drivers and to use the drivers packaged as .deb and not try to use alien to convert the .rpm packaged drivers.  Also, the install script won't properly run some important post-install configuration if the drivers were already manually installed with dpkg.

Also, it's not immediately obvious in ScanGear, but the program does have options to use the document feeder (though I haven't tried it yet).  I don't have it in front of me, but somewhere on the main window of ScanGear is an option menu labeled something like 'Document Source', which has entries like 'Document ADF' which should use the automatic document feeder.

I haven't got Simple Scan to recognize the scanner yet though.

---

### Post by teranine on 2011-01-20
> **IceDoE said:**
> After some searching, I also found that TurboPrint for Linux gets it working pretty easily. I just downloaded the trial version and it set it up, and it seems I don't need to keep the program around after it does the initial setup either so hopefully no worries about needing to buy the program after the trial period.

I could not get the script to work for me on ubuntu 10.10 64 bit. followed the directions exactly as described. 

However, installing the trial version of TurboPrint worked really well. it was quick and easy. I uninstalled the trial program and naturally had to reinstall the printer as TurboPrint disabled or removed it. but the drivers for wifi printing were still there. been printing wirelessly since my last post without issues.

---

### Post by thewump on 2011-01-23
Hi All, 

To keep everything in one place, I've edited the original / top post to reflect what people have found works for scanning.  Works great for me. 

For those who have had weird issues and problems, I don't know what to say.. I'm not at the level of expertise to help out. Sorry!

Keith

---

### Post by Tigerkermit on 2011-01-24
Hello,
did anyone succeeded to send a FAX using the PIXMA out of any Linux application ?
I guess there is a special FAX driver needed.
 
Thanka for any hints in advance.

---

### Post by TMRadMan on 2011-01-25
> **thewump said:**
> Hi All, 

To keep everything in one place, I've edited the original / top post to reflect what people have found works for scanning.  Works great for me. 

For those who have had weird issues and problems, I don't know what to say.. I'm not at the level of expertise to help out. Sorry!

Keith

Keith, this worked great for me on 10.10, thanks. 

I sent a note to Canon support that they should be setting their drivers up to handle amd64 architecture and hopefully somebody reads it, knows whom to pass it on to, passes it on, and somebody does something about it.  That may need a lot of hope.
Cheers.

---

### Post by thewump on 2011-01-25
> **TMRadMan said:**
> Keith, this worked great for me on 10.10, thanks. 

I sent a note to Canon support that they should be setting their drivers up to handle amd64 architecture and hopefully somebody reads it, knows whom to pass it on to, passes it on, and somebody does something about it.  That may need a lot of hope.
Cheers.

Yeah, or at the very least make these drivers available on the US servers!

Just in case, I'm going to keep a copy. They might do something dickish like remove them from Asia.

K

---

### Post by ada-m on 2011-02-04
Just got one today and it worked great on 10.04 64.  Thanks a lot!!

---

### Post by Tigerkermit on 2011-02-05
Can anyone tell me if the FAX function is working ?
So far I was not able to send a FAX from any application.

Many thanks.

---

### Post by teesmaarkhan on 2011-02-12
Hi thewump,

Your post was very clear on hacking the shell script to get the install of the canon printer to work. I was able to get the printer working .:D.

But, following similar instructions on the scanner seems to have issues. The 'scangearmp' doesnot find the scanner. Anything stupid that I am not getting here?

---

### Post by emiller12345 on 2011-02-19
I too am trying to get the scanner to work via a network connection on an i386 computer.  I suspect that is might be an issue of 'USB vs Network'. I don't know for sure, but I was wondering if anyone has been successful in scanning documents over a network. Even running scangearmp from gimp didn't work for me.

---

### Post by needweb on 2011-02-20
What's up brothers. I just bought this aio mp50 and have been trying to get it running. I came across this post and it did not work for me, so I am going to post what did.


Download the drivers from here:

[http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux)

The two you will need are: (One is for the printer the other the scanner) 
[MP250 series IJ Printer Driver Ver. 3.40 for Linux (debian **...**]("http://support-au.canon.com.au/contents/AU/EN/0100236101.html")
[MP250 series ScanGear MP Ver. 1.60 for Linux (debian **...**]("http://support-au.canon.com.au/contents/AU/EN/0100237401.html")

1> If you have not by now, unplug your printer from your pc.
2> Open your terminal and type, " sudo apt-get install -f " (it will ask for you root password so type it). close the terminal.
3> Go to your Downloads folder and unzip it. ( click on the places menu, click on Downloads, when you get there right click on your two files and click Extract Here)
4> It will make two folders one with the printer drivers and the other with the scanner drivers.  
5> Double click one of the folders. Double click the folder Packages.
6> You will now see 4 files /deb packages. Two are for 64-bit and the other two 32-bit.  
7> Double click on the common file / deb package for your version. ( it will say common in the name). The package manager will load. click the install button. click close when it is done.
8> Double click on the other file / deb package for your version.  The package manager will load. click the install button. click close when it is done.

repeat steps 3-8 on the other folder.

I hope this helps.

---

### Post by needweb on 2011-02-20
Oh plug your printer in. It will detect your printer and scanner and now it works.

---

### Post by Maxlite on 2011-02-20
I can't believe what I've just done!  I searched three days to find a post like this and another day getting my mx870 to print, scan and copy.  And now I find this Canon link [http://software.canon-europe.com/software/0038683.asp](http://software.canon-europe.com/software/0038683.asp) that has the print & scan package.  I haven't installed it yet, but I will as soon as I remove the stuff I've done that is posted here.  Let's go see what happens.

---

### Post by gilf on 2011-03-07
Uh, hate to bring this up with everybody happy with this printer and the Canon drivers, but are you guys all printing RGB only at 600 dpi?

Are you seeing grayscale or B+W, and alternate printer resolutions in CUPS printer options. Or in applications?

If not, I fear we are only using the small color ink tanks to print B&W, rather than the larger black pigment tank. even for text. That will mean megabucks in ink support, as well as reduced text quality and permanence.

I'm not as concerned about the resolution issue yet, though that would be next in importance.

Maybe I'm wrong -- what are you finding with your setup?

---

### Post by thewump on 2011-03-07
> **gilf said:**
> Uh, hate to bring this up with everybody happy with this printer and the Canon drivers, but are you guys all printing RGB only at 600 dpi?

Are you seeing grayscale or B+W, and alternate printer resolutions in CUPS printer options. Or in applications?

If not, I fear we are only using the small color ink tanks to print B&W, rather than the larger black pigment tank. even for text. That will mean megabucks in ink support, as well as reduced text quality and permanence.

I'm not as concerned about the resolution issue yet, though that would be next in importance.

Maybe I'm wrong -- what are you finding with your setup?

Hey Glif, I understand what you are saying but have no idea how to check if what you fear is true. Can you elaborate?  I don't see any printer settings for such things - is it supposed to be automatic?

K

---

### Post by thewump on 2011-03-07
> **Maxlite said:**
> I can't believe what I've just done!  I searched three days to find a post like this and another day getting my mx870 to print, scan and copy.  And now I find this Canon link [http://software.canon-europe.com/software/0038683.asp](http://software.canon-europe.com/software/0038683.asp) that has the print & scan package.  I haven't installed it yet, but I will as soon as I remove the stuff I've done that is posted here.  Let's go see what happens.

Maxlite. Before going through all the effort of uninstalling, I've had a quick scan of what this contains. It's great that there is an installable DEB file here, but looking at the source I think this is exactly the same stuff that we've been downloading from asia. Same install.sh with the same version.

This deb file is therefore great for anyone who has 32bit 386 version but for 64bit this thread is still valid.

Next person who comes along though:

Download from:

[http://software.canon-europe.com/software/0038683.asp](http://software.canon-europe.com/software/0038683.asp)

32bit?  Click the DEB file.

64bit?
sudo dpkg --force-architecture -i <filename>.deb

and report back please.

Thanks

K

---

### Post by gilf on 2011-03-07
> **thewump said:**
> Hey Glif, I understand what you are saying but have no idea how to check if what you fear is true. Can you elaborate?  I don't see any printer settings for such things - is it supposed to be automatic?
K

Hey, thewump, it's possible that the printer itself is somehow able to make the mental switch between B&W text and RGB graphics/photos, I'm not familiar with the internal operation of the MX870 firmware. I suppose it could. 

But generally in the past on most printers, this exists as a user controlled setting you can alter in a dialog through the Print function in any particular application, Like Open Office Write, for instance.

Also in some cases you would like to print a B&W version of a color photo or color document to save color ink. So the ability to specify is usually present in most printer drivers. These get passed on to CUPS, and to applications. I'm afraid that this choice is not present in the Canon driver for this printer.

One way to check it out is to open CUPS by typing localhost:631 in your browser. Then go to the manage printers section and click on the MX870's printer's Options (or "Configure Printer) depending on your version of CUPS (not Modify printer). This will show you what options are available.

I don't see much there on mine. When I click on the drop down for "Color Model" there is only "RGB" and for resolution, there is only "600DPI".

By contrast most other brand printers drivers include grayscale, B&W, various resolution modes and possibly a number of other printer color adjustment controls.

I guess one other way of telling if text uses a mixed ink black from the small tanks, or real pigment black from the main tank is to see how fast the color ink tanks are used up vs. the black ink tank. 

Do remember, all tanks are used for head cleaning (a major usage of ink) so even if black is not being used on text printout, some black will be used up by normal printer operation. It wouldn't appear as *no* usage of the black therefore. 

If you are performing many color ink changes and just a few black tank changes, this might be what is happening. You are just using up the black for head cleaning.

On the other hand if you are changing all tanks at roughly the similar interval (for everyday mixed text use), then I guess the printer is able to distinguish and to use pigment black for text automatically.

It still would be important to be able to specify B&W as a default, even for photos, and color only when asked for, unless you do a lot of color work. Pigment black is much cheaper. Color should last a long time that way unless you do a lot of color printing.

Thanks for this thread BTW, this has nothing to do with the assistance you've given in getting the MX870 to print at all in Linux. Very helpful. This problem, if it exists, is part of the Canon driver itself.

---

### Post by thewump on 2011-03-07
Interesting.. Port 631 is VERY interesting.. thanks for that snippet of info.

So I don't have enough data locally to work this out. I have two color printers configured, and the other Xerox has:

Output Color:	Color or Grayscale.

and then our lovely MX870 doesn't have this field, but has 

Color Mode: RGB
Resolution: 600dpi

like you say.. So, I concur with you that nothing is really clear.  I'm not at home but tonight I'll look at the printer settings through it's UI screen and see what is there that might be missing, or fire up a windows VM and see what that driver offers.. ugh!

Can't find a decent manual online. There is only a light "getting started" pdf, and the manual is either an exe or dmg.

Good times ;-)

K

---

### Post by LeeBruce on 2011-03-12
Hi,
I have exactly the same annoying problem, the CUPS web interface (and evince print options as well, for example) shows only 600dpi and RGB. It's incredible there's no option to print grayscale.
However, there is a workaround, even if it is quite ugly (I do not know how this affects ink consumption):
Ubuntu menu: system - admin - print
right click on the printer, properties
job properties

At the very end, you can add custom options. Add 'CNGrayscale' and set it to TRUE.
Unfortunately, this does not add an option you can choose when you print something, but will just force your MX870 to print in grayscale.
You can then duplicate the printer changing the name (say, adding 'color') and setting the same option to false, to have a "new" printer that prints with colors.

So the grayscale printing it is actually available, it is just that for some damn reason this is not reachable from the existing cups interface.

If somebody knows a better solution to this problem, please let us know.
Thanks

---

### Post by teddyp on 2011-03-20
> **thewump said:**
> Maxlite. Before going through all the effort of uninstalling, I've had a quick scan of what this contains. It's great that there is an installable DEB file here, but looking at the source I think this is exactly the same stuff that we've been downloading from asia. Same install.sh with the same version.

This deb file is therefore great for anyone who has 32bit 386 version but for 64bit this thread is still valid.

Next person who comes along though:

Download from:

[http://software.canon-europe.com/software/0038683.asp](http://software.canon-europe.com/software/0038683.asp)

32bit?  Click the DEB file.

64bit?
sudo dpkg --force-architecture -i <filename>.deb

and report back please.

Thanks

K

I really want to thank you for this. I found this post a few months ago and tried the solution from the OP and never got it to work for some reason. Nothing ever happened when I printed. I just saw this today, grabbed the file, installed it and I'm printing again. Seriously, thanks.

Oh yeah... forgot this- Linux The-MAN 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux
running mint 10

---

### Post by awr on 2011-03-30
> **thewump said:**
> 
Next person who comes along though:

Download from:

[http://software.canon-europe.com/software/0038683.asp](http://software.canon-europe.com/software/0038683.asp)

32bit?  Click the DEB file.

64bit?
sudo dpkg --force-architecture -i <filename>.deb

and report back please.
K

Ok, so downloaded the software and installed the deb packages with the line above.  All seemed to work ok, although there wasn't anything to indicate success.  Checked Ubuntu Software Centre but couldn't find the packages either.  Despite this, opened up System/Administration/Printers, selected Add and selected Canon-MX870.  Drivers were automatically found (presumably because I installed them).  Printing works fine although the printer properties only allow 600dpi and Ink/Toner levels are not reported.

Ubuntu 10.10 64bit

---

### Post by khschulz on 2011-03-30
How can I install the PIXMA MX870 with 11.04 64bit?

I tried the instruction but get the following errors:


==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 198459 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using .../cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

---

### Post by noteviljoe on 2011-03-30
I was thinking about getting the Canon PIXMA MX885 (which just seems to be a slightly updated version of the MX870)

The companies page seems to suggest that there are drivers [http://software.canon-europe.com/products/0011008.asp](http://software.canon-europe.com/products/0011008.asp)

Would I have to follow the same instructions as at the beginning of this thread to install these?

It looks like a nice printer but reluctant to shell out all that dosh till I've got confirmation that it works with ubuntu.

P.s: Also I was planning to upgrade to 11.04 when it comes out,is it likely that the drivers will work just as well with that?

---

### Post by Statik on 2011-04-29
I have the same trouble as khschulz. I just upgraded to 11.04 and I get the same error.

Any help greatly appreciated.

Statik

---

### Post by m0r on 2011-04-29
+1
I'm currently experimenting with --ignore-depends=libc6,libcupsys2,libpopt0, but I don't seem to be able to get it to work. Going to sleep now. I will update this post in case of success. (unlikely)

---

### Post by Obnoticus on 2011-04-29
I'm having the same problem with the installation process as well. It worked perfectly in Maverick, but after the clean reinstall to Natty this error pops up when I run the modified install.sh

---

### Post by selcho on 2011-05-01
:PHi,
I was having exact same experience attempting to install Canon pixma mp560 on ubuntu 11.04 64bit. Came across this post at [http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098) and modified barna's beautifully explicit instructions to suit my circumstances.
After trying various edits of the control script I finally re-compiled the four printer and scanner .deb files without any Depends line at all and was able to install the printer and scanner with dpkg -i --force-architecture  without complaint.
Obviously not an ideal solution but printer and scanner are working flawlessly.
Hope this helps.

---

### Post by craig.pennington on 2011-05-01
> **selcho said:**
> :PHi,
I was having exact same experience attempting to install Canon pixma mp560 on ubuntu 11.04 64bit. Came across this post at [http://ubuntuforums.org/showthread.php?t=1427098](http://ubuntuforums.org/showthread.php?t=1427098) and modified barna's beautifully explicit instructions to suit my circumstances.


Thanks! Also have ubuntu 11.04 x86_64, but with the MX870. I ended up deleting the dependency line in both deb files and it worked to get printing going using the regular install. I got lucky in that I had already installed the print driver with an earlier incarnation, so I was moderately certain that I had the deps satisfied.

---

### Post by Obnoticus on 2011-05-01
> **craig.pennington said:**
> Thanks! Also have ubuntu 11.04 x86_64, but with the MX870. I ended up deleting the dependency line in both deb files and it worked to get printing going using the regular install. I got lucky in that I had already installed the print driver with an earlier incarnation, so I was moderately certain that I had the deps satisfied.

Can you explain how did you go about using the regular install.sh file to install the driver? I followed the instructions in the previous poster's link and still could not get the damn script file to work

---

### Post by Statik on 2011-05-01
I have managed to use the procedures mentioned to get the mx870 installed in 11.04 AMD64. There are 3 files you need to edit.
Firstly, the install.sh file must be edited according to this thread: [http://ubuntuforums.org/showthread.php?t=1475336]("http://ubuntuforums.org/showthread.php?t=1475336")

Then you need to follow the procedure in this current thread to remove the depends from the two deb files. You can use either download link but, one thread gets you all the mx870 files, including the scanner files, and the other only gets the printer driver.

I'm going to try getting the scanner to work now.

Statik

---

### Post by adonix on 2011-05-01
Thank you for posting this. You're instructions were really good to follow and my printer works like charm.

---

### Post by Statik on 2011-05-01
Well, I've stripped the dependancies out of the two scanner deb files, modified the install.sh script and ran the install. Everything went fine. No errors. The scanner is even properly recognized in xane. However, scanning doesn't work. Trying the scangearmp program from the terminal allowed me to select the printer properly but then it failed out with pages of errors:
```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed

(scangearmp:23078): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gio/modules/libgiobamf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiobamf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so

(scangearmp:23078): Gtk-WARNING **: Error loading theme icon 'process-stop' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (scangearmp:23078): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(scangearmp:23078): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(scangearmp:23078): Gtk-WARNING **: Error loading theme icon 'process-stop' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (scangearmp:23078): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(scangearmp:23078): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(scangearmp:23078): Gtk-WARNING **: Error loading theme icon 'process-stop' for stock: Unable to load image-loading module: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: /usr/lib/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so: wrong ELF class: ELFCLASS64

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (scangearmp:23078): CRITICAL **: murrine_style_draw_render_icon: assertion `base_pixbuf != NULL' failed

(scangearmp:23078): Gtk-CRITICAL **: IA__gtk_style_render_icon: assertion `pixbuf != NULL' failed

(scangearmp:23078): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

```

Not sure where to go with this just yet. I'll look again after I finish my finals.

Statik

---

### Post by selcho on 2011-05-02
hi,
Reference: [http://ubuntuforums.org/showthread.php?t=870424](http://ubuntuforums.org/showthread.php?t=870424)
I had an error initially "Error during CMS conversion, could not open scanner ICM profile " which was fixed with uncheck "Preferences / Enable color management." 
Try un-installing then re-installing xsane xsane-common sane sane-utils libsane-hpaio simple-scan libsane after deleting ~/.sane folder.
I also installed libsane-extras which provides additional backends should this be necessary.
Running scangearmp program in a terminal also still gives me the ELf error. :~$ scangearmp 
scangearmp: error while loading shared libraries: libgimpmath-2.0.so.0: wrong ELF class: ELFCLASS64 but xsane and simple-scan work perfectly.
Hope this helps.

---

### Post by Obnoticus on 2011-05-09
> **Statik said:**
> I have managed to use the procedures mentioned to get the mx870 installed in 11.04 AMD64. There are 3 files you need to edit.
Firstly, the install.sh file must be edited according to this thread: [http://ubuntuforums.org/showthread.php?t=1475336]("http://ubuntuforums.org/showthread.php?t=1475336")

Then you need to follow the procedure in this current thread to remove the depends from the two deb files. You can use either download link but, one thread gets you all the mx870 files, including the scanner files, and the other only gets the printer driver.

I'm going to try getting the scanner to work now.

Statik

Your instructions are perfect. The printer works just fine now. Thank you Sir

---

### Post by Keydir on 2011-05-13
Hi everyone. I'm new to ubuntu (and linux for that matter). I've installed ubuntu 11.04 64bit and after having success in installing all the drivers for all the components of my x64 rig (i7), there is still one thing that I cannot seem to  be able to fix. And that is, my canon pixma mx350 multifunction printer. I've tried all the things that were mentioned in this thread and others. I got stuck because the two *.deb corresponding to the printer drivers keep asking for the following dependencies.

The files are: **cnijfilter-common_3.30-1_i386.deb** and **cnijfilter-mx350series_3.30-1_i386.deb**

The dependencies are:[B]

libc6 (>= 2.3.4-1)
libcupsys2 (>= 1.2.1) | libcups2
libpopt0 (>= 1.7)[/B]

I've tried different solutions which seemed to have worked out for many people.

Last ones are:

1. Trying to edit the install.sh so that it forces the architecture (--force-architecture) that comes with the drivers and editing the two *.deb so that they ignore those dependencies. Everything works as told, but when I try to install them, they keep asking for the same dependencies.

2. As instructed here: [http://ubuntuforums.org/showthread.php?t=1305248](http://ubuntuforums.org/showthread.php?t=1305248) 

Editing the two *.deb in order to change the dependencies since there was a change in nomenclature some time ago (libcupsys2 now is libcups2, right?). For this, I followed the tutorial there but it is for another canon printer, and an older version of Ubuntu. Because of this, there were some differences in dependencies lists of the *.deb files. However I moved on and changed as told, but only the dependencies in question. After doing all that they still asked for those same dependencies.

3. Trying to install dummy packages... Didn't work either.

Conclusion:

I'm still lost and I don't seem to find the answer to this problem. At least I want to report this situation to help to tie knots with others who are in the same position. Again, I'm just taking the first steps to move to Ubuntu and linux. I'm new and much of what I did doesn't make any sense for now but I'm feeling adventurous =D.

I apologize for not giving more links to the places where I got the information.

Thank you and regards!

---

### Post by Jack Russell on 2011-05-17
For what it is worth, I followed the instructions here, and got the printer working.  One additional step that might be required - I needed to install the package "ia32-libs" as it was not installed by default.    Without this some of the utility programs (like /usr/bin/cnijnetprn) couldn't run as there were missing shared libraries.

Unpacking the .deb file and removing the dependencies involves a few manual steps.  I wrote a shell script to do this:

```
if [ -d foo ];
then
    rm -rf foo
fi

mkdir foo
cd foo
ar x ../$1

#
# Next unpack control.
#
mkdir control
cd control
gzip -d -c ../control.tar.gz | tar xf -

cat control | grep -v Depends: > control2
rm control
mv control2 control

tar cf - ./ > ../control2.tar
cd ..
mv control.tar.gz control.tar.gz.old
mv control2.tar control.tar
gzip control.tar

#cp ../$1 ../$1.orig
ar r ../$1 control.tar.gz
echo "Fixed $1"

```

And then a 2nd script

```
./fixdeb.sh cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
./fixdeb.sh cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-mx870series_3.30-1_i386.deb

./fixdeb.sh scangearmp-mx870series-1.50-1-i386-deb/packages/scangearmp-common_1.50-1_i386.deb
./fixdeb.sh scangearmp-mx870series-1.50-1-i386-deb/packages/scangearmp-mx870series_1.50-1_i386.deb

```

which handles each of the 4 .deb files.

---

### Post by theprisoner6 on 2011-05-19
> **thewump said:**
> UPDATED FOR SCANNER DRIVER TOO.

This took a while and I didn't find the information elsewhere, so thought I'd throw the information here in case anyone else is looking for it!

**1) PRINTING**
Firstly, get the 32 bit printer drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html)

Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf cnij*
cd cnij*

```Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```
**2) SCANNING**
Thanks to others in this thread for doing the groundwork on scanning too.  The process is very similar.  I think for 386 installs of Ubuntu it should "just work".

Download the scanner driver from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html](http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html)


Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf scan*
cd scan*

```Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```Now.. You've just installed drivers AND a scanner app.  To use the scanner app you have to run it.  Hit ALT-F2 to pull up the run command and type "scangearmp".  You should see a dialog box about scanners (first time it might say "NOT FOUND" but if you follow your nose, it will find the scanner and add it to the available list.  To make life easier, make a launcher on your desktop for scangearmp for future use.


K

One slight issue for me in both the printer and scanner install script was that I had to ensure that the line C_arch64="amd64" was NOT commented out. Otherwise, I received the following error:
[FONT=Courier New]
An error occurred. A necessary package could not be found in the proper location.[/FONT]

I think this is because it does not know which actual package to use without this variable. Other than that, your suggestions worked like a charm!

---

### Post by ontwowheels on 2011-05-24
> **theprisoner6 said:**
> One slight issue for me in both the printer and scanner install script was that I had to ensure that the line C_arch64="amd64" was NOT commented out. Otherwise, I received the following error:
[FONT=Courier New]
An error occurred. A necessary package could not be found in the proper location.[/FONT]

I think this is because it does not know which actual package to use without this variable. Other than that, your suggestions worked like a charm!

Were you able to get this to work on Ubuntu 11.04 64 bit?  I get the following errors:
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):

---

### Post by GenePayne on 2011-05-29
I have gotten the Canon MX870 linux drivers to work for 64-bit 11.04 Ubuntu. I had 3 problems to get through to get it to work on my system: 1) libc6/libcupsys2/libpopt0 dependency issues, 2) "package management system cannot be identified" problem, and 3) 64-bit vs. 32-bit issue.
I created a script that combined bits of different posts to fix these 3 problems in one install. Thanks to thewump and Jack Russell (whose script I borrowed heavily from).

STEPS:
1. Download the drivers from the link below (but do not unpack)
[HTML]http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html[/HTML]

2. Open a text editor window
```
gedit modify_ps_drivers.sh &
```

3. Paste the contents of the follwoing script into the gedit window
```

#!/bin/bash

function doFix
{
  echo -n "At $(pwd), fixing $1... "
  if [ -d foo ]; then
    rm -rf foo
  fi
  mkdir foo
  cd foo
  ar x ../$1
  # Next unpack control.
  mkdir control
  cd control
  gzip -d -c ../control.tar.gz | tar xf - 
  cat control | grep -v Depends: > control2
  rm control
  mv control2 control
  tar cf - ./ > ../control2.tar
  cd ..
  mv control.tar.gz control.tar.gz.old
  mv control2.tar control.tar
  gzip control.tar
  ar r ../$1 control.tar.gz
  cd ..
  if [ -d foo ]; then
    rm -rf foo
  fi
  echo " fixed."
}

function extractFilenameFromPath
{
  fullPath=$1
  lengthPath=${#fullPath}
  i=$lengthPath
  filename="$fullPath"

  while [ $i -gt 0 ]; do
    if [ "${fullPath:i:1}" = "/" ]; then
      break
    else
      filename="${fullPath:i:lengthPath-i}"
    fi
  let i--
  done
  echo "$filename"
}

### MAIN
#Check for zenity first
a=$(zenity --version)
err=$?
if [ $err -ne 0 ]; then
  echo "Error: zenity needs to be installed to use this script. Type sudo apt-get install zenity."; echo
  exit
fi
printer=$(zenity --file-selection --title "Select printer driver tar.gz file")
scanner=$(zenity --file-selection --title "Select scanner driver tar.gz file")
tar xzf $printer
tar xzf $scanner
printer=$(extractFilenameFromPath $printer)
scanner=$(extractFilenameFromPath $scanner)
printerLen=${#printer}
scannerLen=${#scanner}
printer=${printer:0:printerLen-7}
scanner=${scanner:0:scannerLen-7}
printerLs=$(ls $printer/packages)
printerDeb1=$(echo "$printerLs" | head -n 1)
printerDeb2=$(echo "$printerLs" | head -n 2 | tail -n 1)
scannerLs=$(ls $scanner/packages)
scannerDeb1=$(echo "$scannerLs" | head -n 1)
scannerDeb2=$(echo "$scannerLs" | head -n 2 | tail -n 1)
#echo $printer, $printerDeb1, $printerDeb2
#echo $scanner, $scannerDeb1, $scannerDeb2
cd $printer/packages
doFix $printerDeb1
doFix $printerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
cd $scanner/packages
doFix $scannerDeb1
doFix $scannerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
echo
echo "Run the install.sh script in $printer to install printer driver, and the install.sh script in $scanner to install the scanner driver."
```

4. Save the file wherever you want and quit gedit

5. Make sure the file is executable
```
chmod a+x modify_ps_drivers.sh
```

6. Run the script above which will modify the driver install scripts (it will prompt you for the location of the downloads)
```
./modify_ps_drivers.sh
```

7. Install the printer driver
```
cnijfilter-mx870series-3.30-1-i386-deb/install.sh
```

8. Install the scanner driver
```
scangearmp-mx870series-1.50-1-i386-deb/install.sh
```


Optional: create a shortcut icon in start/unity menu for the canon scanner software, which gets installed into /usr/bin/scangearmp

---

### Post by agm642 on 2011-05-30
Hello
I'm trying to install an MP640, which has an identical driver packaging format, and running your script gives me this output:
```
./modify_ps_drivers.sh: line 44: /home/argy/tbin/extractFilenameFromPath.s: No such file or directory
./modify_ps_drivers.sh: line 45: /home/argy/tbin/extractFilenameFromPath.s: No such file or directory
./modify_ps_drivers.sh: line 48: printerLen-7: substring expression < 0
./modify_ps_drivers.sh: line 49: scannerLen-7: substring expression < 0
ls: cannot access /packages: No such file or directory
ls: cannot access /packages: No such file or directory
./modify_ps_drivers.sh: line 58: cd: /packages: No such file or directory
At /home/argy/Downloads, fixing ... ar: ../: File format not recognized
gzip: ../control.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
cat: control: No such file or directory
rm: cannot remove `control': No such file or directory
mv: cannot stat `control.tar.gz': No such file or directory
ar: ../: File format not recognized
 fixed.
At /home/argy/Downloads, fixing ... ar: ../: File format not recognized
gzip: ../control.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
cat: control: No such file or directory
rm: cannot remove `control': No such file or directory
mv: cannot stat `control.tar.gz': No such file or directory
ar: ../: File format not recognized
 fixed.
sed: can't read install.sh: No such file or directory
sed: can't read install.sh: No such file or directory
./modify_ps_drivers.sh: line 67: cd: /packages: No such file or directory
At /home, fixing ... mkdir: cannot create directory `foo': Permission denied
./modify_ps_drivers.sh: line 10: cd: foo: No such file or directory
ar: ../: File format not recognized
mkdir: cannot create directory `control': Permission denied
./modify_ps_drivers.sh: line 14: cd: control: No such file or directory
gzip: ../control.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
./modify_ps_drivers.sh: line 16: control2: Permission denied
cat: control: No such file or directory
rm: cannot remove `control': No such file or directory
mv: cannot stat `control2': No such file or directory
./modify_ps_drivers.sh: line 19: ../control2.tar: Permission denied
mv: cannot stat `control.tar.gz': No such file or directory
mv: cannot stat `control2.tar': No such file or directory
gzip: control.tar: No such file or directory
ar: ../: File format not recognized
 fixed.
At /, fixing ... mkdir: cannot create directory `foo': Permission denied
./modify_ps_drivers.sh: line 10: cd: foo: No such file or directory
ar: ../: File format not recognized
mkdir: cannot create directory `control': Permission denied
./modify_ps_drivers.sh: line 14: cd: control: No such file or directory
gzip: ../control.tar.gz: No such file or directory
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
./modify_ps_drivers.sh: line 16: control2: Permission denied
cat: control: No such file or directory
rm: cannot remove `control': No such file or directory
mv: cannot stat `control2': No such file or directory
./modify_ps_drivers.sh: line 19: ../control2.tar: Permission denied
mv: cannot stat `control.tar.gz': No such file or directory
mv: cannot stat `control2.tar': No such file or directory
gzip: control.tar: No such file or directory
ar: ../: File format not recognized
 fixed.
sed: can't read install.sh: No such file or directory
sed: can't read install.sh: No such file or directory

Run the install.sh script in  to install printer driver, and the install.sh script in  to install the scanner driver.

```
Running it on the MX870 drivers gives me the same result... Any ideas?
Thanks a lot.

---

### Post by GenePayne on 2011-05-30
> **agm642 said:**
> Hello
I'm trying to install an MP640, which has an identical driver packaging format, and running your script gives me this output:

...........

Running it on the MX870 drivers gives me the same result... Any ideas?
Thanks a lot.

Sorry, my mistake. I just fixed the script in my original post above (under step 3 of my May 29 2011 post).

Please start over at step 2 of the instructions, and let me know if there's still a problem.

---

### Post by agm642 on 2011-05-31
Alright, now you're positively my personal deity :) Worked like a charm, thanks a lot! :)

---

### Post by spoiled-tv on 2011-06-02
> **GenePayne said:**
> I have gotten the Canon MX870 linux drivers to work for 64-bit 11.04 Ubuntu. I had 3 problems to get through to get it to work on my system: 1) libc6/libcupsys2/libpopt0 dependency issues, 2) "package management system cannot be identified" problem, and 3) 64-bit vs. 32-bit issue.
I created a script that combined bits of different posts to fix these 3 problems in one install. Thanks to thewump and Jack Russell (whose script I borrowed heavily from).

STEPS:
1. Download the drivers from
[HTML]http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html[/HTML]2. Open a text editor window
```
gedit modify_ps_drivers.sh &
```3. Paste the contents of the follwoing script into the gedit window
```

#!/bin/bash

function doFix
{
  echo -n "At $(pwd), fixing $1... "
  if [ -d foo ]; then
    rm -rf foo
  fi
  mkdir foo
  cd foo
  ar x ../$1
  # Next unpack control.
  mkdir control
  cd control
  gzip -d -c ../control.tar.gz | tar xf - 
  cat control | grep -v Depends: > control2
  rm control
  mv control2 control
  tar cf - ./ > ../control2.tar
  cd ..
  mv control.tar.gz control.tar.gz.old
  mv control2.tar control.tar
  gzip control.tar
  ar r ../$1 control.tar.gz
  cd ..
  if [ -d foo ]; then
    rm -rf foo
  fi
  echo " fixed."
}

function extractFilenameFromPath
{
  fullPath=$1
  lengthPath=${#fullPath}
  i=$lengthPath
  filename="$fullPath"

  while [ $i -gt 0 ]; do
    if [ "${fullPath:i:1}" = "/" ]; then
      break
    else
      filename="${fullPath:i:lengthPath-i}"
    fi
  let i--
  done
  echo "$filename"
}

### MAIN
#Check for zenity first
a=$(zenity --version)
err=$?
if [ $err -ne 0 ]; then
  echo "Error: zenity needs to be installed to use this script. Type sudo apt-get install zenity."; echo
  exit
fi
printer=$(zenity --file-selection --title "Select printer driver tar.gz file")
scanner=$(zenity --file-selection --title "Select scanner driver tar.gz file")
tar xzf $printer
tar xzf $scanner
printer=$(extractFilenameFromPath $printer)
scanner=$(extractFilenameFromPath $scanner)
printerLen=${#printer}
scannerLen=${#scanner}
printer=${printer:0:printerLen-7}
scanner=${scanner:0:scannerLen-7}
printerLs=$(ls $printer/packages)
printerDeb1=$(echo "$printerLs" | head -n 1)
printerDeb2=$(echo "$printerLs" | head -n 2 | tail -n 1)
scannerLs=$(ls $scanner/packages)
scannerDeb1=$(echo "$scannerLs" | head -n 1)
scannerDeb2=$(echo "$scannerLs" | head -n 2 | tail -n 1)
#echo $printer, $printerDeb1, $printerDeb2
#echo $scanner, $scannerDeb1, $scannerDeb2
cd $printer/packages
doFix $printerDeb1
doFix $printerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
cd $scanner/packages
doFix $scannerDeb1
doFix $scannerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
echo
echo "Run the install.sh script in $printer to install printer driver, and the install.sh script in $scanner to install the scanner driver."
```4. Save the file and quit gedit

5. Make sure the file is executable
```
chmod a+x modify_ps_drivers.sh
```6. Run the script above which will modify the driver install scripts
```
./modify_ps_drivers.sh
```7. Install the printer driver
```
cnijfilter-mx870series-3.30-1-i386-deb/install.sh
```8. Install the scanner driver
```
scangearmp-mx870series-1.50-1-i386-deb/install.sh
```
Optional: create a shortcut icon in start/unity menu for the canon scanner software, which gets installed into /usr/bin/scangearmp


I have an MX350, I followed these instructions and it installed (11.04 64bit). When I print the printing application says "Processing" under status, I hear the rollers moving but it doesnt take any paper or move the ink. The status then goes to complete though nothing happened. I can print from other computers in the house.

---

### Post by Samushighwind on 2011-06-06
GenePayne, I used your script and everything ran smoothly up to the point where it asked me to register the printer and it couldn't find it.  This could be my fault entirely, but is there any chance it isn't?

I'll keep trying to figure out the problem in case it's all me.

---

### Post by GenePayne on 2011-06-07
> **Samushighwind said:**
> GenePayne, I used your script and everything ran smoothly up to the point where it asked me to register the printer and it couldn't find it.  This could be my fault entirely, but is there any chance it isn't?

I'll keep trying to figure out the problem in case it's all me.

I suggest searching through the output of the script to make sure there aren't any error messages anywhere in the middle (even if it says "Run the install.sh script..." at the end).

If you can post all of the output of the script and the subsequent attempt to install the driver, I'll take a look at it.

---

### Post by Samushighwind on 2011-06-07
here:

> ==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
[sudo] password for ben: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 134300 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using .../cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
Setting up cnijfilter-common:i386 (3.30-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-mx870series_3.30-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 134300 files and directories currently installed.)
Preparing to replace cnijfilter-mx870series:i386 3.30-1 (using .../cnijfilter-mx870series_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-mx870series:i386 ...
Setting up cnijfilter-mx870series:i386 (3.30-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...
/usr/lib/cups/backend/cnijusb: error while loading shared libraries: libcups.so.2: wrong ELF class: ELFCLASS64


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
Currently selected:[0] Update
Enter the value. [0]


also I successfully installed the scanner driver, but now... I'm guessing this is because the printer can't be detected, but attempting to execute /usr/bin/whatever it's called seems to do nothing.

---

### Post by GenePayne on 2011-06-07
> **Samushighwind said:**
> here:



also I successfully installed the scanner driver, but now... I'm guessing this is because the printer can't be detected, but attempting to execute /usr/bin/whatever it's called seems to do nothing.

I don't know why it isn't working. It looks to me like the modification script I wrote is at least getting you to the install.
I don't remember if I got this error that you had:
/usr/lib/cups/backend/cnijusb: error while loading shared libraries: libcups.so.2: wrong ELF class: ELFCLASS64

Maybe that had something to do with it. It looks like the install script uses cups to find the printer (line 461 of install.sh), and your error has to do with libcups.
You might get more information by running the script in debug mode
```
bash -x ./install.sh
```


If that doesn't work, maybe you could try what looks like a different driver. I saw the following link posted elsewhere in this forum, but I didn't try it because I had already gotten the drivers from the canon-asia site to work.
[HTML]http://software.canon-europe.com/software/0038683.asp?model=[/HTML]

---

### Post by Samushighwind on 2011-06-07
One potentially awkward thing about the way I have the printer set up is that every computer, including my desktop, connects to it wirelessly.  It's a fairly straightforward setup process on Windows, of course, but I do know I have set up the printer successfully on Ubuntu 10.04.  I used the instructions in the original post for that, but they didn't work this time, so I used your post.

As far as getting the printer connected, I don't remember what I did.  I think it was hooked up wirelessly at the time, but I'm not sure.  Is yours connected wirelessly?

---

### Post by GenePayne on 2011-06-07
> **Samushighwind said:**
> One potentially awkward thing about the way I have the printer set up is that every computer, including my desktop, connects to it wirelessly.  It's a fairly straightforward setup process on Windows, of course, but I do know I have set up the printer successfully on Ubuntu 10.04.  I used the instructions in the original post for that, but they didn't work this time, so I used your post.

As far as getting the printer connected, I don't remember what I did.  I think it was hooked up wirelessly at the time, but I'm not sure.  Is yours connected wirelessly?

Yes, I connect to mine wirelessly. I just had it turned-on when I got to the portion of the install where it finds the printer.

I also had mine running before in Ubuntu 10.04 32-bit. When I installed it in Ubuntu 11.04 64-bit, I had a few other issues, which is why I wrote the script.

So are you saying you have multiple computers on a WLAN network connecting to the printer? Are any of them on and connected to it while you're trying to do the driver install for Ubuntu 11.04? I'm just wondering if it's possible that another machine is somehow staking a claim on the printer while your driver install is trying to do the same.

---

### Post by Samushighwind on 2011-06-07
Well printing works fine when I'm on Windows, so I'm guessing no.

Do you know a way I could connect to it using the System Settings->Printing dialog?

I also found this: [http://ubuntuforums.org/showthread.php?t=435940](http://ubuntuforums.org/showthread.php?t=435940) But I don't know what it means I should do.

---

### Post by Samushighwind on 2011-06-07
I just did it using the method in the first post for my laptop running 10.04.  It worked fine and the difference I suppose was that instead of throwing the 64-bit-related problem when it tried to search for printers, it asked if I wanted to use USB or Network and it worked from there.

What's the difference between your modified install.sh and the one the first post would have you create?

---

### Post by BSD_dad on 2011-07-08
Post #83 worked on VPCEG11FX, 11.04. Original 64 bit mod didn't for some reason. Thanks!

---

### Post by digitiser on 2011-07-13
> **GenePayne said:**
> I have gotten the Canon MX870 linux drivers to work for 64-bit 11.04 Ubuntu...

I can confirm that this works flawlessly for my Canon MP560 on Linux Mint 11 as well.

Thanks!

---

### Post by Andyvan on 2011-07-23
I was just trying to install on 10.10 64-bit, and was stuck at the registration prompt.  The fix for me was to install the 32-bit libraries:

 sudo apt-get install ia32-libs

Once I did that, everything (both scanner and printer) worked fine.

---

### Post by ktook on 2011-07-28
:D Thanks for all the research and documenting that was needed to put together this "How To:".  The install went perfectly.  Now I am just one more step to not needing Windows (Win7).  Plus after having used many HP Ink Jet printers, this MX870 is the greatest of all. _** Again, thanks [thewump]("http://ubuntuforums.org/member.php?u=207638")**_

---

### Post by pmorrone on 2011-08-07
> **GenePayne said:**
> Sorry, my mistake. I just fixed the script in my original post above (under step 3 of my May 29 2011 post).

Please start over at step 2 of the instructions, and let me know if there's still a problem.

GenePayne,

Thanks for putting up these posts.  I tried to run the process as you have laid out but I received the same errors as the previous poster on May 30th 2011; [agm642]("http://ubuntuforums.org/member.php?u=39642").  can't read install.sh.  I used the post that you had edited under point 3.  Is there something else I should have done?

---

### Post by pmorrone on 2011-08-07
> **IceDoE said:**
> Alright so TurboPrint helps get the printer going. 

However, I cannot use the scanner wirelessly using turboprint it seems, and Simple Scan does not detect the scanner (I presume because its a wireless, networked scanner). 

I don't know if the wireless scanner works using the drivers from canon, as those are 9.10 drivers and don't seem to work with 10.04 which I have.

IceDoE,

Did you ever get the scanner working with TurboPrint or any other solution?

Thanks,

Phil

---

### Post by GenePayne on 2011-08-08
> **pmorrone said:**
> GenePayne,

Thanks for putting up these posts.  I tried to run the process as you have laid out but I received the same errors as the previous poster on May 30th 2011; [agm642]("http://ubuntuforums.org/member.php?u=39642").  can't read install.sh.  I used the post that you had edited under point 3.  Is there something else I should have done?

pmorrone,

Can you post the exact output that you get when you run the script, just like agm642 did in post #84 of this thread? That will help me to figure out exactly what is going wrong.

---

### Post by pmorrone on 2011-08-08
> **GenePayne said:**
> pmorrone,

Can you post the exact output that you get when you run the script, just like agm642 did in post #84 of this thread? That will help me to figure out exactly what is going wrong.

GenePayne,

Thanks much for responding back to my inquiry.  I was able to get the script to run and extract the cnijfilter-mx870series-3.30-1-i386-deb and scangearmp-mx870series-1.50-1-i386-deb to the home folder and ran the install files for both.  The printer file opened up, registered the printer and worked fine, even was able to print a test page; I now can see the printer under the printing app.  However, when I ran the scanner install file it started up in the terminal and asked for my sudo password, ran for a moment and then the terminal just closed.  I would have posted the output but the terminal closed.

Is there something else I should have done? Is there a scanner utility that I need to run afterwards to use the scanner that I am unaware of?

---

### Post by GenePayne on 2011-08-08
> **pmorrone said:**
> ...However, when I ran the scanner install file it started up in the terminal and asked for my sudo password, ran for a moment and then the terminal just closed.  I would have posted the output but the terminal closed.

Is there something else I should have done? Is there a scanner utility that I need to run afterwards to use the scanner that I am unaware of?

I'm glad the printer part worked. To figure out why the scanner install didn't work, the output will be needed.
Are you running the install.sh script by clicking on its icon in a file browser? If so, I would do the following instead. Open a terminal window (select terminal from the menu/launcher), then type:
```
cd ~/Downloads/scangearmp-mx870series-1.50-1-i386-deb
```
to get to the directory containing the scanner install script [COLOR="Red"](note that the '~/Downloads' is an example path. Replace this part of the path with the actual location of the scangearmp-mx870series-1.50-1-i386-deb directory on your system)[/COLOR]. Then type:
```
sudo ./install.sh
```
The scanner install will probably crash on you again but it shouldn't close the terminal window when it does. Hopefully there will be error output that you can post.

---

### Post by pmorrone on 2011-08-08
> **GenePayne said:**
> I'm glad the printer part worked. To figure out why the scanner install didn't work, the output will be needed.
Are you running the install.sh script by clicking on its icon in a file browser? If so, I would do the following instead. Open a terminal window (select terminal from the menu/launcher), then type:
```
cd ~/Downloads/scangearmp-mx870series-1.50-1-i386-deb
```to get to the directory containing the scanner install script [COLOR=Red](note that the '~/Downloads' is an example path. Replace this part of the path with the actual location of the scangearmp-mx870series-1.50-1-i386-deb directory on your system)[/COLOR]. Then type:
```
sudo ./install.sh
```The scanner install will probably crash on you again but it shouldn't close the terminal window when it does. Hopefully there will be error output that you can post.

GenePayne,

Thanks again for responding to my inquiry.  I followed your instructions and received the following message.  It says that the install completed and left me at the prompt but I cannot find any app to run a scan and the simple scan doesn't seem to connect or find any devices.

Thanks

phil@ubuntu:~$ cd ~/Downloads/scangearmp-mx870series-1.50-1-i386-deb
phil@ubuntu:~/Downloads/scangearmp-mx870series-1.50-1-i386-deb$ sudo ./install.sh
[sudo] password for phil: 
==================================================

ScanGear MP Ver.1.50-1 for Linux
Copyright CANON INC. 2007-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/scangearmp-common_1.50-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 168936 files and directories currently installed.)
Preparing to replace scangearmp-common:i386 1.50-1 (using .../scangearmp-common_1.50-1_i386.deb) ...
Unpacking replacement scangearmp-common:i386 ...
Setting up scangearmp-common:i386 (1.50-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG ./packages/scangearmp-mx870series_1.50-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 168936 files and directories currently installed.)
Preparing to replace scangearmp-mx870series:i386 1.50-1 (using .../scangearmp-mx870series_1.50-1_i386.deb) ...
Unpacking replacement scangearmp-mx870series:i386 ...
Setting up scangearmp-mx870series:i386 (1.50-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Installation has been completed.
phil@ubuntu:~/Downloads/scangearmp-mx870series-1.50-1-i386-deb$

---

### Post by slavinzing56 on 2011-08-08
Hi, I got the  printer working by using the 'add a printer' GUI, but I'd still like to  know why the install.sh script wasn't running out of curiosity.. Thanks  guys.

---

### Post by GenePayne on 2011-08-08
pmorrone,

It looks like your install worked. It should have installed a program called scangearmp (probably in /usr/bin). This is the only program I use for scanning with the Canon MX870. Others may have had success with getting it to work on other scanning programs, I don't know. It works well and does everything I need to do, anyway.

I can't remember if there is an icon that is automatically added in the ubuntu start menu or unity launcher (depending on what ubuntu version you're running). I think I created my own entry in the unity launcher.

If you type 'scangearmp' in a terminal, it should run.

---

### Post by pmorrone on 2011-08-08
> **GenePayne said:**
> pmorrone,

It looks like your install worked. It should have installed a program called scangearmp (probably in /usr/bin). This is the only program I use for scanning with the Canon MX870. Others may have had success with getting it to work on other scanning programs, I don't know. It works well and does everything I need to do, anyway.

I can't remember if there is an icon that is automatically added in the ubuntu start menu or unity launcher (depending on what ubuntu version you're running). I think I created my own entry in the unity launcher.

If you type 'scangearmp' in a terminal, it should run.

GenePayne,

Worked perfectly.  Sorry for the trouble; very new to Linux but really enjoying it.  Thanks again for your help.

---

### Post by qupfer on 2011-08-11
Hi, 
i tried to install my mx870 printer and have one problem. 
I uses the "modify driver script" and after that, the printer install.sh worked but i can't find my printer in the network.
The scanner install worked without any errors and with the "simple scan" program, i can scan a page. 
But a scangearmp app isn't installed ```

henning@Henning-Think:~$ scan   *(2x tab)*
scangearmp                           scanimage
scangearmp-mx870series-pkgconfig.sh  
henning@Henning-Think:~$ scangearmp
bash: /usr/bin/scangearmp: Datei oder Verzeichnis nicht gefunden *(means: File or directory not found )*
henning@Henning-Think:~$ 

```Any ideas how to install the printer and the canon scan application? Should i try the setup from the asia site (i used the europe/German one)?
Hope you understood my problem :)

EDIT: i forgot: i'm using a new install of ubuntu 11.04 64bit. MY Notebook is connectet wireless, the printer wired.

And i didn't understand this: Ubuntu finds the entry scangearmp in /usr/bin but if i try to start, my pc did not find it anymore?
```

henning@Henning-Think:~$ sudo find /* -name scangearmp
/usr/share/scangearmp
/usr/bin/scangearmp
henning@Henning-Think:~$ /usr/bin/scangearmp 
bash: /usr/bin/scangearmp: Datei oder Verzeichnis nicht gefunden (german for: File or Directory not found)
henning@Henning-Think:~$ 

```

---

### Post by Radar Rider on 2011-09-16
Running 11.04 64-bit. Have an HP 5850 that was working fine, but cartridge prices are getting ridiculous, so I figured I'd consolidate to the family's MX870. 

I got these errors using the modified install.sh:

fjb@jnatty-64:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb$ sudo ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 238349 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using .../cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386
fjb@jnatty-64:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb$ 


I'm a bit temporally challenged, and I seem to actually have all the dependencies satisfied according to Synaptic, so I tried the TurboPrint trick (thank you, all), and printing over my local wired network to the WLAN-connected 870 upstairs works fine. Will try to get the scanner working next and report back. 

Also, regarding scanning. Our 870 is USB-connected to my wife's late-model OSX iMac, and even with the official Canon software, network printing and definitely scanning are worthlessly unstable, in my experience. Printing's great on USB for that machine, but not scanning. I have capitulated to using an SD card in the 870, scanning to PDF, and then spinning around in the chair and putting the SD card in the iMac. So I think Canon has some software issues in general there, based on my experience, and digging through Apple and Canon forums.

---

### Post by Tommmi on 2011-09-23
I got my MX870 and everything works fine. Everything... except the access of the memory card via network. I don't want to use the scanning-drivers, but putting documents in the document feeder and being able to access the pdfs on the memorycard via network would be fine.

Via the control panel on its webserver you can allow the printer to make the memory card accessible via samba. The files are listed in nautilus but unfortunately I can't really read them: They are downloaded - but all programs are not able to show them. Any experiences or ideas?

Thank you!

---

### Post by thinkingbeyondthesquare on 2011-10-01
Hi Team

I have used the script suggestions at the beginning of this thread which executed without error (well beside a warning message about the wrong architecture but the script installed anyway)

I have the scanner working - so thats great. However the printer isnt there, even if I manually install it the driver isnt in the list. 

I'm running 11.04 with the Pixma MX870

(I'm also trying Ubuntu from Madriva Linux - RPM distribution)

So any ideas?

Cheers

Mark

---

### Post by NathanBrauer on 2011-10-24
Whoot!  Easiest setup EVER!  Worked wonders (when directions are followed) on Ubuntu 11.10 64 bit over Wifi.  Thanks a million!

One clarification you should make for more advanced users like me: I expected that I had to put your shell script in a specific place in relation to the downloaded files + I wasn't sure if I should unpack the downloaded files or not.  So you should simply include the following so things are clear:

Add to #1: "Do not unpack."
Change #4: "Save the file anywhere you wish and quit gedit."
Add to #6: "Script will prompt you for the location of the downloads."

Thanks again for making this so easy!

> **GenePayne said:**
> I have gotten the Canon MX870 linux drivers to work for 64-bit 11.04 Ubuntu. I had 3 problems to get through to get it to work on my system: 1) libc6/libcupsys2/libpopt0 dependency issues, 2) "package management system cannot be identified" problem, and 3) 64-bit vs. 32-bit issue.
I created a script that combined bits of different posts to fix these 3 problems in one install. Thanks to thewump and Jack Russell (whose script I borrowed heavily from).

STEPS:
1. Download the drivers from
[HTML]http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html[/HTML]

2. Open a text editor window
```
gedit modify_ps_drivers.sh &
```

3. Paste the contents of the follwoing script into the gedit window
```

#!/bin/bash

function doFix
{
  echo -n "At $(pwd), fixing $1... "
  if [ -d foo ]; then
    rm -rf foo
  fi
  mkdir foo
  cd foo
  ar x ../$1
  # Next unpack control.
  mkdir control
  cd control
  gzip -d -c ../control.tar.gz | tar xf - 
  cat control | grep -v Depends: > control2
  rm control
  mv control2 control
  tar cf - ./ > ../control2.tar
  cd ..
  mv control.tar.gz control.tar.gz.old
  mv control2.tar control.tar
  gzip control.tar
  ar r ../$1 control.tar.gz
  cd ..
  if [ -d foo ]; then
    rm -rf foo
  fi
  echo " fixed."
}

function extractFilenameFromPath
{
  fullPath=$1
  lengthPath=${#fullPath}
  i=$lengthPath
  filename="$fullPath"

  while [ $i -gt 0 ]; do
    if [ "${fullPath:i:1}" = "/" ]; then
      break
    else
      filename="${fullPath:i:lengthPath-i}"
    fi
  let i--
  done
  echo "$filename"
}

### MAIN
#Check for zenity first
a=$(zenity --version)
err=$?
if [ $err -ne 0 ]; then
  echo "Error: zenity needs to be installed to use this script. Type sudo apt-get install zenity."; echo
  exit
fi
printer=$(zenity --file-selection --title "Select printer driver tar.gz file")
scanner=$(zenity --file-selection --title "Select scanner driver tar.gz file")
tar xzf $printer
tar xzf $scanner
printer=$(extractFilenameFromPath $printer)
scanner=$(extractFilenameFromPath $scanner)
printerLen=${#printer}
scannerLen=${#scanner}
printer=${printer:0:printerLen-7}
scanner=${scanner:0:scannerLen-7}
printerLs=$(ls $printer/packages)
printerDeb1=$(echo "$printerLs" | head -n 1)
printerDeb2=$(echo "$printerLs" | head -n 2 | tail -n 1)
scannerLs=$(ls $scanner/packages)
scannerDeb1=$(echo "$scannerLs" | head -n 1)
scannerDeb2=$(echo "$scannerLs" | head -n 2 | tail -n 1)
#echo $printer, $printerDeb1, $printerDeb2
#echo $scanner, $scannerDeb1, $scannerDeb2
cd $printer/packages
doFix $printerDeb1
doFix $printerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
cd $scanner/packages
doFix $scannerDeb1
doFix $scannerDeb2
cd ..
#Fix rpm response so it doesn't get the wrong version
sed -i 's/c_system_rpm=$?/c_system_rpm=1/g' install.sh
#Add '--force-architecture' to install command for 64-bit
sed -i 's/sudo dpkg -iG/sudo dpkg --force-architecture -iG/g' install.sh
cd ..
echo
echo "Run the install.sh script in $printer to install printer driver, and the install.sh script in $scanner to install the scanner driver."
```

4. Save the file and quit gedit

5. Make sure the file is executable
```
chmod a+x modify_ps_drivers.sh
```

6. Run the script above which will modify the driver install scripts
```
./modify_ps_drivers.sh
```

7. Install the printer driver
```
cnijfilter-mx870series-3.30-1-i386-deb/install.sh
```

8. Install the scanner driver
```
scangearmp-mx870series-1.50-1-i386-deb/install.sh
```


Optional: create a shortcut icon in start/unity menu for the canon scanner software, which gets installed into /usr/bin/scangearmp

---

### Post by Samushighwind on 2011-10-24
sorry didn't mean to post

---

### Post by GenePayne on 2011-10-25
> **NathanBrauer said:**
> Whoot!  Easiest setup EVER!  Worked wonders (when directions are followed) on Ubuntu 11.10 64 bit over Wifi.  Thanks a million!

One clarification you should make for more advanced users like me: I expected that I had to put your shell script in a specific place in relation to the downloaded files + I wasn't sure if I should unpack the downloaded files or not.  So you should simply include the following so things are clear:

Add to #1: "Do not unpack."
Change #4: "Save the file anywhere you wish and quit gedit."
Add to #6: "Script will prompt you for the location of the downloads."

Thanks again for making this so easy!

Modified the original post with these changes. Thanks for the feedback, glad it worked!

---

### Post by ravor on 2011-11-07
"An error occurred. The package management system cannot be identified."
 I have had the same probem in Fedora and now I updated the file to work for me but I get 
```


./install.sh
./install.sh: line 1681: syntax error: unexpected end of file

```
As I am a little unexperienced at scripting, I would appreciate your help.

---

### Post by GenePayne on 2011-11-07
> **ravor said:**
> "An error occurred. The package management system cannot be identified."
 I have had the same probem in Fedora and now I updated the file to work for me but I get 
```


./install.sh
./install.sh: line 1681: syntax error: unexpected end of file

```
As I am a little unexperienced at scripting, I would appreciate your help.

The install.sh file that you attached differs from mine in that it has some lines commented-out (1239 - 1250, and then at the last line 1680). This results in an imbalanced if statement condition (at line 1238 ) causing your unexpected EOF error.

---

### Post by ravor on 2011-11-08
> **GenePayne said:**
> The install.sh file that you attached differs from mine in that it has some lines commented-out (1239 - 1250, and then at the last line 1680). This results in an imbalanced if statement condition (at line 1238 ) causing your unexpected EOF error.

Oh, yes, of course it works now, thanks!

---

### Post by NathanBrauer on 2011-11-10
> **GenePayne said:**
> Modified the original post with these changes. Thanks for the feedback, glad it worked!

Glad to help! :)

I just noticed one problem though.  Anyone know how to print in grayscale only?

This is all I have:
[IMG]http://dl.dropbox.com/u/4115701/Screenshots/PrintFirst.png[/IMG]
[IMG]http://dl.dropbox.com/u/4115701/Screenshots/PrintSecond.png[/IMG]
[IMG]http://dl.dropbox.com/u/4115701/Screenshots/PrintThird.png[/IMG]
[IMG]http://dl.dropbox.com/u/4115701/Screenshots/PrintFourth.png[/IMG]

---

### Post by WhyDoINeedToRegister? on 2011-11-16
I ran into the "The package management system cannot be identified" error with both the printer and scanner drivers for the Canon PIXMA MG8100 series found here:[INDENT][http://software.canon-europe.com/products/0010881.asp](http://software.canon-europe.com/products/0010881.asp)
[/INDENT]I am trying to use an MG8120 with 64-bit Ubuntu 11.04. I'm not sure why the original poster, *thewump*, used such a crude modification of the [FONT=Courier New]install.sh[/FONT] script. The problem with Canon's script is bad logic that can be fixed properly. Their script fails because they think it is an error condition if the system has _both_ the [FONT=Courier New]rpm[/FONT] and [FONT=Courier New]dpkg[/FONT] package manager binaries functionally available. Obviously there is nothing wrong with having two package managers installed and Ubuntu 11.04 falls afoul of this. I've attached a patch for [FONT=Courier New]install.sh[/FONT] that resolves the dilemma of which to use with a bias for [FONT=Courier New]dpkg[/FONT], and it doesn't rely on forcing architecture. Although the patch was made for the [FONT=Courier New]install.sh[/FONT] found in [FONT=Courier New]cnijfilter-mg8100series-3.40-1-deb[/FONT], I was able to use the same patch file as is for the script in [FONT=Courier New]scangearmp-mg8100series-1.60-1-deb[/FONT] as well. This solved the problem for me and I suspect/hope it will for other PIXMA driver installs too, although I haven't tried it with any other GNU/Linux distributions.

One would think that after all this time, that Canon would clue in that their installation scripts are all broken, at least for the most widely used GNU/Linux distribution in the world. Apparently Canon doesn't test its Linux driver installs. If someone in the know could point the correct Canon folk at this thread, I'm sure we'd all appreciate them fixing this.

I wasn't sure if embedded tab characters would survive posting my patch as a code element in this forum, which is why I attached the patch as a file. For the casual reader, here is the patch as a code element, but you should prefer the attached file if you actually want to feed it to your system's [FONT=Courier New]patch[/FONT] utility:

```

--- install.sh.original    2011-11-15 23:49:14.872663855 -0800
+++ install.sh    2011-11-16 03:04:23.082665351 -0800
@@ -1252,20 +1252,18 @@
     dpkg --version 1> /dev/null 2>&1
     c_system_deb=$?
 
-    ## rpm and deb are error, or rpm and deb are no error, is error ##
-    if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
+    ## Use deb if supported, else rpm if supported, else error ##
+    if [ $c_system_deb = 0 ]; then
+        C_system="deb"
+        C_arch32="i386"
+        C_arch64="amd64"
+    elif [ $c_system_rpm = 0 ]; then
+        C_system="rpm"
+        C_arch32="i386"
+        C_arch64="x86_64"
+    else
         printf "$L_INST_COM_01_02"
         return $C_ERR_CODE
-    else
-        if test $c_system_rpm -eq 0; then
-            C_system="rpm"
-            C_arch32="i386"
-            C_arch64="x86_64"
-        else
-            C_system="deb"
-            C_arch32="i386"
-            C_arch64="amd64"
-        fi
     fi
     
     return 0

```

---

### Post by NathanBrauer on 2011-11-16
What's wrong with the solution here?
[http://ubuntuforums.org/showthread.php?p=10878776#post10878776](http://ubuntuforums.org/showthread.php?p=10878776#post10878776)

> **WhyDoINeedToRegister? said:**
> I ran into the "The package management system cannot be identified" error with both the printer and scanner drivers for the Canon PIXMA MG8100 series found here:[INDENT][http://software.canon-europe.com/products/0010881.asp](http://software.canon-europe.com/products/0010881.asp)
[/INDENT]I am trying to use an MG8120 with 64-bit Ubuntu 11.04. I'm not sure why the original poster, *thewump*, used such a crude modification of the [FONT=Courier New]install.sh[/FONT] script. The problem with Canon's script is bad logic that can be fixed properly. Their script fails because they think it is an error condition if the system has _both_ the [FONT=Courier New]rpm[/FONT] and [FONT=Courier New]dpkg[/FONT] package manager binaries functionally available. Obviously there is nothing wrong with having two package managers installed and Ubuntu 11.04 falls afoul of this. I've attached a patch for [FONT=Courier New]install.sh[/FONT] that resolves the dilemma of which to use with a bias for [FONT=Courier New]dpkg[/FONT], and it doesn't rely on forcing architecture. Although the patch was made for the [FONT=Courier New]install.sh[/FONT] found in [FONT=Courier New]cnijfilter-mg8100series-3.40-1-deb[/FONT], I was able to use the same patch file as is for the script in [FONT=Courier New]scangearmp-mg8100series-1.60-1-deb[/FONT] as well. This solved the problem for me and I suspect/hope it will for other PIXMA driver installs too, although I haven't tried it with any other GNU/Linux distributions.

One would think that after all this time, that Canon would clue in that their installation scripts are all broken, at least for the most widely used GNU/Linux distribution in the world. Apparently Canon doesn't test its Linux driver installs. If someone in the know could point the correct Canon folk at this thread, I'm sure we'd all appreciate them fixing this.

I wasn't sure if embedded tab characters would survive posting my patch as a code element in this forum, which is why I attached the patch as a file. For the casual reader, here is the patch as a code element, but you should prefer the attached file if you actually want to feed it to your system's [FONT=Courier New]patch[/FONT] utility:

```

--- install.sh.original    2011-11-15 23:49:14.872663855 -0800
+++ install.sh    2011-11-16 03:04:23.082665351 -0800
@@ -1252,20 +1252,18 @@
     dpkg --version 1> /dev/null 2>&1
     c_system_deb=$?
 
-    ## rpm and deb are error, or rpm and deb are no error, is error ##
-    if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
+    ## Use deb if supported, else rpm if supported, else error ##
+    if [ $c_system_deb = 0 ]; then
+        C_system="deb"
+        C_arch32="i386"
+        C_arch64="amd64"
+    elif [ $c_system_rpm = 0 ]; then
+        C_system="rpm"
+        C_arch32="i386"
+        C_arch64="x86_64"
+    else
         printf "$L_INST_COM_01_02"
         return $C_ERR_CODE
-    else
-        if test $c_system_rpm -eq 0; then
-            C_system="rpm"
-            C_arch32="i386"
-            C_arch64="x86_64"
-        else
-            C_system="deb"
-            C_arch32="i386"
-            C_arch64="amd64"
-        fi
     fi
     
     return 0

```

---

### Post by WhyDoINeedToRegister? on 2011-11-17
> **NathanBrauer said:**
> What's wrong with the solution here?
[http://ubuntuforums.org/showthread.php?p=10878776#post10878776](http://ubuntuforums.org/showthread.php?p=10878776#post10878776)

:rolleyes: Trolling, right?

---

### Post by M!SF!TS on 2011-11-22
It don't work. It worked in ubuntu 11.04
But now it don't work in ubuntu 11.10

This gets really annoying.



```
myself@Ubuntu-Linux:~/Downloads$ tar -xvf cnij*
cnijfilter-mx870series-3.30-1-i386-deb/
cnijfilter-mx870series-3.30-1-i386-deb/packages/
cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-mx870series_3.30-1_i386.deb
cnijfilter-mx870series-3.30-1-i386-deb/resources/
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_zh_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_ja_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_fr_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/install.sh
myself@Ubuntu-Linux:~/Downloads$ cd cnij*
myself@Ubuntu-Linux:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb$ ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.
```

I am on ubuntu 11.10 i368
Anyone know of anything that works?
I already tried this:
[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
```

```
sudo apt-get install cnijfilter-mx870series
```

And it don't work either.

---

### Post by mrojas73 on 2011-11-24
> **NathanBrauer said:**
> Whoot!  Easiest setup EVER!  Worked wonders (when directions are followed) on Ubuntu 11.10 64 bit over Wifi.  Thanks a million!

One clarification you should make for more advanced users like me: I expected that I had to put your shell script in a specific place in relation to the downloaded files + I wasn't sure if I should unpack the downloaded files or not.  So you should simply include the following so things are clear:

Add to #1: "Do not unpack."
Change #4: "Save the file anywhere you wish and quit gedit."
Add to #6: "Script will prompt you for the location of the downloads."

Thanks again for making this so easy!

Just ran the installer on 9.10 and worked like a charm, no need to use the script.  Thank you for the link, I didn't know they had native drivers for Linux now.

---

### Post by M!SF!TS on 2011-11-28
For anyone struggling with getting your Canon MX870 driver working or there wireless internet working in Ubuntu 11.10

I found that this works:

***_Install linux kernel 3.1 (stable)_***


Open the terminal and run these two commands for both 32-bit and 64-bit versions of Ubuntu 11.10/11.04:

**wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb)**

**sudo dpkg -i linux-headers-3.1.0-030100_3.1.0-030100.201110241006_all.deb**



***_Ubuntu (32-bit)_***



For Ubuntu 11.10/11.04 (32-bit), run these commands:

**wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb)**

**sudo dpkg -i linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb**

**wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb)**

**sudo dpkg -i linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_i386.deb**



***_Ubuntu (64-bit)_***



For Ubuntu 11.10/11.04 (64-bit), issue these commands:

**wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb)**

**sudo dpkg -i linux-headers-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb**

**wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb)**

**sudo dpkg -i linux-image-3.1.0-030100-generic_3.1.0-030100.201110241006_amd64.deb**

----------------------------------------------------------------------------------------------------

Now reboot now your system, then open the terminal and run this command to check your Kernel version:

uname -r

The output returned will be something like this:

~$ uname -r
3.1.0-030100-generic

That's it!

(Taken from here: [http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html](http://www.upubuntu.com/2011/11/how-to-install-kernel-31-on-ubuntu.html))


Now you can just follow the directions in the ***first*** page of this thread for both the Printer and Scanner. In either 32bit or 64bit Ubuntu 11.10

:)

---

### Post by GCT on 2011-12-15
Thanks so much for all the hard work guys!  I'm 99% of the way there I think, but I can't seem to detect my printer on the network (it's on the wireless) when I get to that part of the script.  Has anyone figured out a way around that?  I'm running Xubuntu 11.10.

---

### Post by Statik on 2011-12-16
Are you sure your printer is on the network? With my router, I setup a DHCP assignment for the printer, giving it a specific IP based on its MAC and I could see in the maintenance panel that it had received that IP. I could then ping the IP from my laptop. From there, it was easily detected.

Statik

---

### Post by teranine on 2012-01-06
I've recently upgraded from 10.10 -> 11.10.  Turbo Print still works and I got my MX870 printing within 2 minutes.  Very easy install and setup.  They are not freeware but I will definitely purchase the software this time around.  For anyone that doesn't want to purchase the software, just install it to get the driver then uninstall after 30 days free trial.  This is a headache-free solution to what has been posted here so far.

---

### Post by francos3 on 2012-01-17
> **thewump said:**
> UPDATED FOR SCANNER DRIVER TOO.

This took a while and I didn't find the information elsewhere, so thought I'd throw the information here in case anyone else is looking for it!

**1) PRINTING**
Firstly, get the 32 bit printer drivers from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html](http://support-sg.canon-asia.com/contents/SG/EN/0100272302.html)

Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf cnij*
cd cnij*

```

Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```

and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```

and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```

Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```

and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```


**2) SCANNING**
Thanks to others in this thread for doing the groundwork on scanning too.  The process is very similar.  I think for 386 installs of Ubuntu it should "just work".

Download the scanner driver from Asia:

[http://support-sg.canon-asia.com/contents/SG/EN/0100273002.html]()


Download is at the bottom of that page.

After you download it, untar the file and get into the directory that it creates

```

tar -xvf scan*
cd scan*

```

Now.. if you have a 32 bit / i386 system you are good to go!

```

./install.sh

```

and follow your nose.

If you are using 64 bit though it's more tricky.  The 32 bit deb file itself works fine on 64bit machines, but the stuff in the install script does all the hard work of actually getting the printer set up, so the thing to do is hack the install.sh file to force it to ignore the architecture.

open the file with your favorite editor and find the block:

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
               printf "$L_INST_COM_01_02"
               return $C_ERR_CODE
        else
               if test $c_system_rpm -eq 0; then
                       C_system="rpm"
               else
                        C_system="deb"
               fi
        fi


```

and comment out the logic so all that is left is C_system="deb"

```

        ## rpm and deb are error, or rpm and deb are no error, is error ##
        #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
        #       printf "$L_INST_COM_01_02"
        #       return $C_ERR_CODE
        #else
        #       if test $c_system_rpm -eq 0; then
        #               C_system="rpm"
        #       else
                        C_system="deb"
        #       fi
        #fi

```

Now search for:

```

C_FUNC_show_and_exec "sudo dpkg -iG $c_fpath_pkg_name"

```

and change it to

```

C_FUNC_show_and_exec "sudo dpkg --force-architecture -iG $c_fpath_pkg_name"

```

to force it to ignore the architecture.. 

You're done!

Run with

```
./install
```

Now.. You've just installed drivers AND a scanner app.  To use the scanner app you have to run it.  Hit ALT-F2 to pull up the run command and type "scangearmp".  You should see a dialog box about scanners (first time it might say "NOT FOUND" but if you follow your nose, it will find the scanner and add it to the available list.  To make life easier, make a launcher on your desktop for scangearmp for future use.


K
just got a Canon MX885(updated version of MX870) to work for Ubunutu 11.10 with a amd64 architecture.  Folow the instructions as begining of thread but note that now the install script has added two new lines to the first block of logic which needs to be comented:
C_arch32="i386"
C_arch64="amd64"

In my case since I am using amd64 I left the arch64 line uncomented.  Note that if both arch lines are comented install script does not work, it complains about deb files missing.

Thanks a lot to "thewump", I was afraid I was not going to be able to use this printer with ubuntu.
Cheers

---

### Post by teranine on 2012-01-23
I spent a half hour trying to install scangear by following the instructions given above exactly.  I'm running 11.10 64bit and ran into a dependency error involving libusb-dev after running install.sh.  So I made sure I had the latest libusb-dev and retried.  Still no luck.

Then I tried installing scangear through the Ubuntu Software Center by searching for "scangear".  I first installed the scangearmp-common package (not the i386 version) and that installed without any issues.  Then I located the package specific to my printer/scanner (mx870), which is "scangearmp-mx870series" (again not the i386 version).  Installed without any issues as well.  Went to the command line and typed scangearmp to run and yup it's installed and scans perfectly.  This approach took less than a minute.  The scangearmp version reported in the About dialog is 1.70.  

So, give the software center a try :)

For people still having printing issues on 11.10 64bit systems, this blog post seemed to help out a lot of people:

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

I was able to successfully install the driver (cnijfilter-mx870series) although I had it working previously using TurboPrint.

---

### Post by AKADAP on 2012-02-04
> **teranine said:**
> 
Then I tried installing scangear through the Ubuntu Software Center by searching for "scangear".

Opening "Ubuntu Software Center" and typing "scangear" gets me "No items match "scangear"
Synaptic Package Manager also finds nothing.

Is there a PPA you have installed you are not telling us about?

---

### Post by teranine on 2012-02-09
Yes, here's the PPA:


```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update

```

Sorry it took a while to reply back.  Check out this [[COLOR="Blue"]page[/COLOR]]("http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html") for more details.

Once I added the PPA, I was able to find scangear in software sources.

---

### Post by @lpha on 2012-02-13
> **GenePayne said:**
> I have gotten the Canon MX870 linux drivers to work for 64-bit 11.04 Ubuntu. I had 3 problems to get through to get it to work on my system: 1) libc6/libcupsys2/libpopt0 dependency issues, 2) &quot;package management system cannot be identified&quot; problem, and 3) 64-bit vs. 32-bit issue.
I created a script that combined bits of different posts to fix these 3 problems in one install. Thanks to thewump and Jack Russell (whose script I borrowed heavily from).


 I tried your instructions and the printer drivers couldn't install because of dependency issues. it said libpopt0 was not installed even though it is. checked it multiple times in synaptic to make sure. What am I doing wrong? Please help.

---

### Post by GenePayne on 2012-02-13
> **@lpha said:**
> I tried your instructions and the printer drivers couldn't install because of dependency issues. it said libpopt0 was not installed even though it is. checked it multiple times in synaptic to make sure. What am I doing wrong? Please help.

I would recommend trying the instructions at this link first (posted by teranine above #130):
[HTML]http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html[/HTML]

I haven't tried it myself, but it may be a smoother way of doing the install.

---

### Post by @lpha on 2012-02-13
> **GenePayne said:**
> I would recommend trying the instructions at this link first (posted by teranine above #130):
[HTML]http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html[/HTML]I haven't tried it myself, but it may be a smoother way of doing the install.

  thank you. that worked, except I don't know where to go from there. The printer won't show up on my network. How can I check if the drivers were properly installed? The scanner works fine, but printing doesn't.   edit: one more thing. cngpijmon-MX870 (canon status monitor) says "unknown printer." Any ideas?

---

### Post by GenePayne on 2012-02-13
> **@lpha said:**
> thank you. that worked, except I don't know where to go from there. The printer won't show up on my network. How can I check if the drivers were properly installed? The scanner works fine, but printing doesn't.   edit: one more thing. cngpijmon-MX870 (canon status monitor) says "unknown printer." Any ideas?

Were there any error messages during the printer portion of the install? Did the install try to find your printer, and then prompt you to select from a list? Are you connecting to your printer via Wi-Fi or USB?

---

### Post by astrophoenix on 2012-02-14
after you install the driver and you want to configure the printer in cups, add a new printer and use lpd://hostname/default as the uri. 

I came up with this by port-scanning the printer and discovering that port 515 was open which is the lpd port. it works.

---

### Post by @lpha on 2012-02-15
> **GenePayne said:**
> Were there any error messages during the printer portion of the install? Did the install try to find your printer, and then prompt you to select from a list? Are you connecting to your printer via Wi-Fi or USB?

 No errors. I remember selecting from a list back when I compiled on 10.xx ...now, this time when installing through a ppa, it didnt guide me through that process.  It's connected over wifi. To get the scanner running, i ran scangear in the terminal. is there a program i can run to set the printer up? And did you use CUPS, at all? I don't remember having to mess with that.

---

### Post by GenePayne on 2012-02-16
> **@lpha said:**
> No errors. I remember selecting from a list back when I compiled on 10.xx ...now, this time when installing through a ppa, it didnt guide me through that process.  It's connected over wifi. To get the scanner running, i ran scangear in the terminal. is there a program i can run to set the printer up? And did you use CUPS, at all? I don't remember having to mess with that.

I haven't tried this method of installing through a ppa, so I can't offer much help. No, I didn't have to use CUPS before. If you haven't already done so, I would try astrophoenix's post (#137) to use CUPS to connect to the printer.

---

### Post by @lpha on 2012-02-16
Finally got it to work! Thank you, astrophoenix & GenePayne. Astrophoenix: were you able to get IPP to work with your printer? What are the limitations for LDP? 



Here is what I did for those absolutely new to CUPS or those having issues after installing the ppa drivers and not being able to print:  
1) visit this local CUPS address page to configure your printer - [http://localhost:631/](http://localhost:631/) 
2) navigate to Administration -> add printer -> then enter your system username and password into the prompt 
3) select the 'LPD/LPR Host or Printer' radio button ..click continue 
4) in the connection iput box, enter this:  lpd://hostname/queue  (where the hostname is replaced with your printer's ip address....easy). To find the ip address, go into your router and look for it OR get it directly from your printer ( Setup -> device settings -> LAN settings -> Confirm LAN settings -> WLAN setting list -> then scroll down) 
5) almost there .... give your printer a name. 
6) Select Canon under 'printer make' then model (in our case, pixma mx870) 
7) the rest should be as obvious as the steps just described.
8) you're pretty much finished now. print a test page and give yourself a hug if all goes well.

---

### Post by AKADAP on 2012-02-18
I just got this printer and have both the printer and scanner working without installing any drivers (ubuntu 11.10). I just had to tell the scanner drive & the printer driver the IP address (Bonjour did not work for autodiscovering the printer).

Is there any advantage to installing the Canon driver downloadable directly from Canon?

Is there an advantage to the Canon driver in the PPA?

Is there an advantage to using the Turboprint driver? (I have a license left over from a broken i9900)?

Which is best?

---

### Post by AKADAP on 2012-02-18
I can answer some of my own questions now.
I installed the PPA.
The printer is now automatically discovered.
The test print colors are more saturated, and the dither pattern is much finer.
The driver that comes with Ubuntu 11.10 only allows a max 600 dpi resolution, The PPA driver allows up to 9600 dpi.
Both use color inks in their grey scale, but the PPA actually looks grey, the default driver looks a bit pink in the lighter shades of grey.
Default drivers have no way of monitoring ink. PPA has cngpijmonmx870 tool to monitor ink levels and printer status.

I'm rather annoyed that the manual for this printer that comes on disk is an EXE file that does not run under wine (brings up the 1st page than has a fatal error). I had to boot an old windows 2000 machine that I'm trying to retire to view the manual. I was then able to print the manual to a PDF file, and it came out smaller than the EXE, so I was able to transfer it to my Linux box and read it there.

I also find it odd that the printer can scan to pdf, and print pdf files from its memory card, but it is not a postscript printer.

Has anyone figured out how to send faxs from the computer using this printer? Seems wastefull to have to print out a page only to scan it back into the same device to fax it. I tried installing eFax, but that seems to only want to talk to fax modems.

Scangearmp won't work because it wants the i386 version of appmenu-gtk that can't be simultaniously installed with the 64 bit version. (many "wrong ELF class: ELFCLASS64" errors)

---

### Post by AKADAP on 2012-02-18
I have now installed TurboPrint.

With the PPA I can not print 2 sided. I have selected 2 sided printing every where possible, but it always prints single sided.

With TurboPrint, 2 sided printing works.

With the PPA, the printer clips on the left 1.4 mm from the edge, 3.7 mm from the right, and does not clip the top or bottom when I print a PDF that fills most of a page.
TurboPrint scales the image slightly larger, and clips the left at 2.5mm, the right at 2.6mm and the bottom at 1.9mm and the top is not clipped @1.2mm
edit: I found the scaling difference was an option in evance to shrink the printout to the available area (in this they both failed because both were cropped) With this option turned off, both printed the same correct size image with slightly differen cropping margins.

I found this site: [http://incompetech.com/graphpaper/](http://incompetech.com/graphpaper/) and generated graph paper with a 1/10 inch grid.
The TurboPrint driver is more accurate at scaling. (as accurate as I could measure with a vernier caliper).

The test print on TurboPrint looks about the same as the PPA with the exeptions that Cyan Majenta and Yelow look a bit pailer at 100%.

---

### Post by baumisch on 2012-02-19
Hi, this thread confuses me somehow :(

Is it possible to scan with 11.10 x64 with the duplex ADF on the Computer directly?

I tried a bit of the fixes here, being stuck with scangear-i386 dependencies :(

I just want to scan duplex to PDF on my PC, not on the printer itself,

regards, Chistian

---

### Post by AKADAP on 2012-02-19
> **baumisch said:**
> Hi, this thread confuses me somehow :(

Is it possible to scan with 11.10 x64 with the duplex ADF on the Computer directly?

I tried a bit of the fixes here, being stuck with scangear-i386 dependencies :(

I just want to scan duplex to PDF on my PC, not on the printer itself,

regards, Chistian

I don't think so.
With the built in sane driver, you can scan from the ADF, but only the 1st page.
I can't get the scangear stuff to work since it wants the 32 bit stuff which currently can't coexist with the 64 bit stuff.
From what I've read, this gets fixed in 3.1 of the kernel.

I think the solution for now is to do your duplex scanning locally on the scanner to a memory card, and then move the memory card to the PC.

As far as I can tell, there are no fax driver nor memory card drivers for this printer yet. It's a pitty the memory card was not done in a standard way (samba or some other standard) so that it did not need drivers.

---

### Post by @lpha on 2012-02-23
> **AKADAP said:**
> 
The driver that comes with Ubuntu 11.10 only allows a max 600 dpi resolution, The PPA driver allows up to 9600 dpi.

Default drivers have no way of monitoring ink. PPA has cngpijmonmx870 tool to monitor ink levels and printer status.


Hmm... how were you able to switch to 9600 dpi? I only get up to 600 with the ppa! I'm doing something wrong.

---

### Post by AKADAP on 2012-02-24
> **@lpha said:**
> Hmm... how were you able to switch to 9600 dpi? I only get up to 600 with the ppa! I'm doing something wrong.

When you installed the printer, did you use the system-config-printer tool to set up the printer?

Did you select "Network Printer" and find the "Canon MX870(userdefinedprinternamehere.local)" in the list?

I currently have all three printer drivers set up so I can easily see what works on each one.

Currently Evince has trouble centering the print on the page, and I'm not sure if the problem is the driver or evince. It is probably evince because the problem occures on all three drivers.

---

### Post by @lpha on 2012-02-24
> **AKADAP said:**
> When you installed the printer, did you use the system-config-printer tool to set up the printer?

Did you select "Network Printer" and find the "Canon MX870(userdefinedprinternamehere.local)" in the list?

I currently have all three printer drivers set up so I can easily see what works on each one.

Currently Evince has trouble centering the print on the page, and I'm not sure if the problem is the driver or evince. It is probably evince because the problem occures on all three drivers.

Thank you.
That worked, all right...
The problem was that I didn't know which tool to use after installing the drivers, and system-config-printer was just what I needed. 

and about evince..i did notice that. I'll try printing through LibreOffice or another program to see if the problem really is evince. Just give me some time to refill my ink cartridges (don't really feel like getting messy right now).

---

### Post by AKADAP on 2012-03-07
After a suggested work around from someone at TurboPrint, I got a slightly modified version of the work around to work printing on Evance.

Evance has a bug where the "Auto Rotate and Center" fails to do the "Center" part of its job.

TurboPrint has the scaling set to 100% on its default 8.5x11 paper setting, so Evance does not scale to fit printable area when printing 8.5x11 
documents.

The suggested work around was to create a custom page size (8.5 x 11 with scaling set to 90%) and turn on "Auto Rotate and Center". This got the page scaled, but it was still shoved in the upper left corner of the page, and the left edge clipped.
I added a shift of 0.43 from the left, and 0.5 from the top to the custom paper size, and even though the print preview still showed the document shoved in the upper left corner of the page, when printed, it was properly centered.

---

### Post by kamiller42 on 2012-03-14
The Michael Gruz PPA is really nice. I now have two MX870 drivers. Michael's is nice. I have tools to control the printer.

I cannot get my scanner to work. It used to work but I think a kernel update broke it. How can I get it working again? Should Michael's driver support scanning? If it does, is it conflicting with my old one?

When I run scanimage -T, I get the following...
[pixma] bjnp_open_tcp: Can not connect to scanner: Connection refused
scanimage: open of device pixma:MX870_000000EECC8F failed: Invalid argument

FYI, I am using Ubuntu 11.10 64-bit and the MX870 is networked.

---

### Post by AKADAP on 2012-03-15
> **kamiller42 said:**
> The Michael Gruz PPA is really nice. I now have two MX870 drivers. Michael's is nice. I have tools to control the printer.

I cannot get my scanner to work. It used to work but I think a kernel update broke it. How can I get it working again? Should Michael's driver support scanning? If it does, is it conflicting with my old one?

When I run scanimage -T, I get the following...
[pixma] bjnp_open_tcp: Can not connect to scanner: Connection refused
scanimage: open of device pixma:MX870_000000EECC8F failed: Invalid argument

FYI, I am using Ubuntu 11.10 64-bit and the MX870 is networked.

Linux treats scanners completely separately from printers, so the printer driver has no effect on the scanner.

Do you allow the printer to automatically get its IP address? If so, its address may have changed.

If you edited the /etc/sane.d/pixma.conf file to add the IP address, you will have to edit it again to put the new value in.

If your are trying to run scangear on a 64 bit system, that currently is broken (some have done some changes to their systems to make it work, you will have to read their posts as I have not done this myself).

---

### Post by crocefisso on 2012-04-10
User friendly installation of canon drivers on i368 or 64bit ubuntu can be done easily by adding the folowing repository (I tested it for my mx870 on ubuntu 64bit by installing cnijfilter-mx870series for printing and scangearmp-mx870series for scanning, and it works like a charm): 

```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update

```

---

### Post by dumdidum on 2012-04-27
I just read over the last two pages of this thread and there wasn't anything yet on the setup under 12.04.

I'm trying to get my MX870 (which is networked via WiFi) working under 12.04 64-bit. Any pointers would be much appreciated.

---

### Post by crocefisso on 2012-04-27
If I'm not mistaken, you can install 32bits apps/drivers transparantly on 12.04 64bits.

---

### Post by AKADAP on 2012-04-28
The michael-gruz PPA does not seem to support 12.04 yet. When I try to update, I get this error message:
```
W:Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/michael-gruz/canon/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by AKADAP on 2012-04-28
> **AKADAP said:**
> 
I can't get the scangear stuff to work since it wants the 32 bit stuff which currently can't coexist with the 64 bit stuff.
From what I've read, this gets fixed in 3.1 of the kernel.


I can confirm that scangear is now working under 12.04. Well, running at least, so far I've only done a scan preview, but before it wasn't even running.

---

### Post by Tigerkermit on 2012-05-02
Hi, since I have installed 12.04 LTS I can not print anymore with my MX870. Neither on USB nor via WiFi.
I tried to reinstall the 64 driver as described which did work fine until 11.04.
Now I get the error message :
[COLOR=Blue]==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
(Lese Datenbank ... 360993 Dateien und Verzeichnisse sind derzeit installiert.)
Vorbereitung zum Ersetzen von cnijfilter-common:i386 3.30-1 (durch .../cnijfilter-common_3.30-1_i386.deb) ...
Ersatz für cnijfilter-common:i386 wird entpackt ...
dpkg: Abhängigkeitsprobleme verhindern Konfiguration von cnijfilter-common:i386:
 cnijfilter-common:i386 hängt ab von libpopt0 (>= 1.7).
dpkg: Fehler beim Bearbeiten von cnijfilter-common:i386 (--install):
 Abhängigkeitsprobleme - verbleibt unkonfiguriert
Trigger für libc-bin werden verarbeitet ...
ldconfig deferred processing now taking place
Fehler traten auf beim Bearbeiten von:
 cnijfilter-common:i386
[/COLOR]It seems ther is some dependency problem with libpopt0 ??

Anyone any idea ?

If I use CUPS for installation, I can sometime print one page but after that the next print job stops and does not start anymore ?

Thanks for your help !

---

### Post by dumdidum on 2012-05-05
So, I have my MX870 running as a WiFi networked printer in Precise 64-bit.

I was able to configure it by going to system settings -> printing -> add -> network printer -> find network printer where i searched for the MX870 after providing its IP address. (Note I am using Ubuntu in German, I hope I translated everything correctly.)

A driver for the MX870 is available in the list of available drivers. The driver was added just fine. Upon trying to print a test page, the printer was looking for paper from the rear tray only. But after changing the paper source setting from "Automatic Paper Source Switching" to "Cassette", it printed the test page as well as other print jobs just fine.

However, one problem remains. Printing is extremely slow. Every page takes about five times as long as it did in Lucid with the manually installed Canon driver.

Any suggestions for fixing the printing speed issue?

---

### Post by ray field on 2012-05-09
> **dumdidum said:**
> Any suggestions for fixing the printing speed issue?

not the answer you were looking for I'm sure, but my solution to the dreadful performance of my Canon MP530 under Precise is to ditch it in favor of an HP. the only way this printer is usable under Linux is by booting Lucid, where its performance has never been very good. I've got one set of ink cartridges to go and once I've gone through that, I'm done with Canon printers forever.

---

### Post by AKADAP on 2012-05-09
> **ray field said:**
> not the answer you were looking for I'm sure, but my solution to the dreadful performance of my Canon MP530 under Precise is to ditch it in favor of an HP. the only way this printer is usable under Linux is by booting Lucid, where its performance has never been very good. I've got one set of ink cartridges to go and once I've gone through that, I'm done with Canon printers forever.

I'm using the turboprint drivers, and not noticing a slowdown under 12.04. I havn't tried the other drivers since I upgraded though.

---

### Post by GenePayne on 2012-05-17
I was also able to get my Canon MX870 installed and working in 12.04 64-bit using the standard ubuntu add printer method (system settings -> Printing -> Add -> Printer -> Find Network Printer).

Much easier now that the driver is included with ubuntu!

---

### Post by oogabubchub on 2012-05-22
I was having problems with my MX870 after upgrading to 12.04 from 11.10. The printer would be recognized and would receive print jobs, but it would do nothing after displaying the message "Processing" on the LCD screen.

I originally had the printer working under 11.10 with the michael gruz ppa, but this no longer worked in 12.04 and attempting to install from Ubuntu's Printing manager didn't work either.

Finally, I found a michael gruz ppa that has been updated for 12.04:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

I first removed the old driver with Synaptic Package Manager, then added the new one:

```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-mx870series
```

After doing this, installing the printer with the Printing manager worked.

---

### Post by Samushighwind on 2012-05-22
I can confirm that if you are starting from scratch on 12.04, installing the printer is easy by using the printer manager.  After supplying the IP address of the printer, I selected "PASSTHRU" when prompted with several options, and it worked correctly.  I had originally selected "" and that failed to work correctly.

I can also confirm the scanner install listed in the first post still works perfectly, and that Ubuntu's included "Simple Scan" software will work with the scanner, if that is preferred to the software which comes with the scanner.  I personally prefer Simple Scan, but the Canon software provides more advanced settings.

---

### Post by ray field on 2012-05-23
> **oogabubchub said:**
> I was having problems with my MX870 after upgrading to 12.04 from 11.10. The printer would be recognized and would receive print jobs, but it would do nothing after displaying the message "Processing" on the LCD screen.

I originally had the printer working under 11.10 with the michael gruz ppa, but this no longer worked in 12.04 and attempting to install from Ubuntu's Printing manager didn't work either.

Finally, I found a michael gruz ppa that has been updated for 12.04:
[https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages](https://code.launchpad.net/~michael-gruz/+archive/canon-trunk/+packages)

I first removed the old driver with Synaptic Package Manager, then added the new one:

```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-mx870series
```

After doing this, installing the printer with the Printing manager worked.

I was having the very same problem with the MP530, and this seems to work for me as well. fingers crossed it holds!

---

### Post by Samushighwind on 2012-06-06
Anyone had success in making the printer work at faster than a glacial pace?  I've been able to print, which is great, but I have to wait forever.

---

### Post by qxzn on 2012-07-03
> **Samushighwind said:**
> GenePayne, I used your script and everything ran smoothly up to the point where it asked me to register the printer and it couldn't find it.  This could be my fault entirely, but is there any chance it isn't?

I'll keep trying to figure out the problem in case it's all me.

I had the same problem. I worked around it by:

1. finish installing scangearmp
2. run scangearmp
3. select "rescan", at which point my device was found
4. close scangearmp
5. finish the printer install manually using these instructions (basically, find the device with cnijnetprn and then install it with lpadmin): [http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux](http://linux.wikia.com/wiki/Getting_Canon_PIXMA_to_work_on_Linux)

---

### Post by Welly Wu on 2012-07-06
I recently purchased a brand new System76 Lemur Ultra laptop and I have a Canon PIXMA MX870 multi-function printer, scanner, and copier. I connect it using a Category 5e cable to my Verizon FIOS fiber optic MI424WR 802.11 B/G router and switch. I tried to add the IP address, but it keeps saying that no printer was found. I switched to 802.11 G Wi-Fi and I entered in the IP address and it still does not work. I did add and install the Michael Gruz Canon-Trunk PPA and I added the MX870 series device driver. I do have port 631 over both TCP and UDP to permit traffic to go out.

Why can't I add my printer? How do I add my printer so that I can print?

Please help.

---

### Post by Bhakti108 on 2012-12-03
Hi

I was having problems getting my Pixma MG6250 installed, until I found this thread. Weird thing is though, uname =m returns i686 whichas far as I know is 32 bit, but the install scripts would not work without doing the hack mentioned on page 1, once I did that all went well. 

However scangear was a diferent issue. see my thread [http://ubuntuforums.org/showthread.php?t=2089373http://](http://ubuntuforums.org/showthread.php?t=2089373http://)
 for the issue and the solution. 

Basically I had to leave 2 lines uncommented in the install scrip otherwise I got a heap or errors. Maybe this can help someone esle that is getting stuck. I hope so. 
[]("http://ubuntuforums.org/showthread.php?t=2089373http://")

---

### Post by Bhakti108 on 2012-12-03
Hi

I was having problems getting my Pixma MG6250 installed, until I found this thread. Weird thing is though, uname =m returns i686 whichas far as I know is 32 bit, but the install scripts would not work without doing the hack mentioned on page 1, once I did that all went well. 

However scangear was a diferent issue. see my thread [http://ubuntuforums.org/showthread.php?t=2089373http://](http://ubuntuforums.org/showthread.php?t=2089373http://)
 for the issue and the solution. 

Basically I had to leave 2 lines uncommented in the install script otherwise I got a heap of errors. Maybe this can help someone else that is getting stuck. I hope so. 
[]("http://ubuntuforums.org/showthread.php?t=2089373http://")

---

### Post by Welly Wu on 2012-12-03
I got it to work now. I can print to my Canon PIXMA MX870 printer using ipp protocol. Solved!

---

### Post by Welly Wu on 2012-12-18
I upgraded to Ubuntu 12.10 64 bit and it does not print again. I set GUFW to allow the CUPS service to print and I installed apparmor-profiles and I set the usr.sbin.cupsd to enforce this profile. I added port 631 in CUPS. It's not printing. When I viewed the attributes during a print job, it keeps saying that the printer is not connected. I also set the usr.sbin.cupsd profile to complain mode and it still does not print.

I had this problem when I upgraded from Ubuntu 11.10 64 bit to Ubuntu 12.04 LTS. Every time I upgrade to a newer Ubuntu version, printing does not work.

Can someone help me to figure out how to solve this problem so that I can print?

---

### Post by pdc on 2012-12-21
I am wondering if you have the Canon drivers installed ......

.... you can test that with 

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter[/COLOR]

......if you don't get an answer here .......

how about go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100272302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100272302.html)

and download [COLOR="SeaGreen"]MX870 series IJ Printer Driver Ver. 3.30 for Linux (debian Packagearchive)[/COLOR] to your Downloads directory ......it comes down as [COLOR="SeaGreen"]cnijfilter-mx870series-3.30-1-i386-deb.tar.gz[/COLOR]

can I suggest some commands? ..that you can copy and paste into a terminal ...

> [COLOR="Red"]cd Downloads[/COLOR].hit the Enter key ... each time ..

> [COLOR="Red"]tar -zxvf cnijfilter-mx870series-3.30-1-i386-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd cnijfilter-mx870series-3.30-1-i386-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

for the scanner go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100273002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100273002.html)

and download [COLOR="SeaGreen"]MX870 series ScanGear MP Ver. 1.50 for Linux (debian Packagearchive)[/COLOR]

that comes in as [COLOR="SeaGreen"]scangearmp-mx870series-1.50-1-i386-deb.tar.gz[/COLOR]

---

### Post by Welly Wu on 2012-12-21
I re-installed Ubuntu 12.04.1 64 bit Long Term Service and I modified the install.sh file as instructed on the first post. It works. I just printed a page from Google News. This does not work with Ubuntu 12.10 64 bit for some reason. This is solved yet again.

---

### Post by Samushighwind on 2013-01-02
hi,

running Linux Mint 14 now, but basically it's Ubuntu 12.10 64-bit.

I am attempting to install the same way as before.  unfortunately it's now telling me I have an unmet libpopt0:i386 dependency.  The fixes on the front page didn't solve this.  How can I force the architecture for dpkg on this?

EDIT: ha, nevermind.  fixed.  I guess I just installed the i386 version after apt asked me if I wanted to and it all worked.

---

### Post by jakev3 on 2013-05-14
does this work with 13.04? i was able to do everything up to the "run with ./install". how do you do this?

---

### Post by pdc on 2013-05-14
> [COLOR="#EE82EE"] i was able to do everything up to the "run with ./install"[/COLOR]


perhaps you tell us exactly what you did, to help us understand .......

try ....................

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

.........after copying and pasting the earlier commands .....................

---

### Post by jakev3 on 2013-05-15
thats the command i tried.

tar -xvf cnij* cd cnij*
when i run this i get "cannot open: no such file or directory. tar error not recoverable exiting now."
i already made all of the changes to the install.sh i just need help with the commands.

thanks

---

### Post by pdc on 2013-05-15
well Jake let's establish a few things; you have an MX870 and you want to install the printer driver on Ubuntu 13.04 

the latest version is 3.30 from here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MX876&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MX876&menu=download&filter=0&tagname=g_os&g_os=Linux)

the problem is: there are only 32bit debian packages;

and you have just installed a 64bit system?

---

### Post by jakev3 on 2013-05-15
> **pdc said:**
> well Jake let's establish a few things; you have an MX870 and you want to install the printer driver on Ubuntu 13.04 

the latest version is 3.30 from here

[http://support-asia.canon-asia.com/P/search?model=PIXMA+MX876&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MX876&menu=download&filter=0&tagname=g_os&g_os=Linux)

the problem is: there are only 32bit debian packages;

and you have just installed a 64bit system?

Correct. Because there is only a 32bit package I followed the "how to" on changing the 32 bit script to work with a 64 bit system.

---

### Post by pdc on 2013-05-15
OK;

this has become a huge thread;

...........I think it is a waste of time editing the script; .....that is diverting you away from what you need to do;

as you can simply install the two debian packages 

you need to install the COMMON package first and then the MX870 package

......the bigger issue with installing 32bit packages on a 64bit system: is that the packages look for /usr/lib instead of what your system has which is /usr/lib64

......so one can issue a series of what are called symbolic links ..to tell the system the correct place to look 

..it seems best to set those up: before installing the driver; 

> [COLOR="#FF0000"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and 

> [COLOR="#FF0000"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

should be good

if I suggest some commands to install the two packages .....????

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mx870series-3.30-1-i386-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mx870series-3.30-1-i386-deb/packages[/COLOR]

if you then issue the command

> [COLOR="#FF0000"]ls[/COLOR] ........it asks the system to list what is in that directory ....it should be [COLOR="#008000"]cnijfilter-common_3.30-1_i386.deb[/COLOR] and [COLOR="#008000"]cnijfilter-mx870series_3.30-1_i386.deb[/COLOR]

.........if so, then install with 

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-common_3.30-1_i386.deb[/COLOR]

and then 

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-mx870series_3.30-1_i386.deb[/COLOR]

.........that should install the driver; you can check with 

> [COLOR="#FF0000"]sudo dpkg -l | grep cnijfilter[/COLOR]

---

### Post by jakev3 on 2013-05-15
pdc thank you so much. its nice to actually understand how this work instead of just being told commands.

---

### Post by pdc on 2013-05-15
so the MX870 is working for you Jake?

---

### Post by joletus on 2013-10-26
Thanks for these tips!

I had success with 64-bit xubuntu 13.04. I edited the install.sh as directed and run it.
I had to accept installing few additional i386 packages that the driver was dependent on.

Sorry I have Finnish version installed so there are few messages from apt-get in Finnish, but you will get their translations (to your own language) by running the same commands ;)
Here is raw copy of what I did... and had immediately successful printing experience! :KS

Thanks a lot!

I did the same with scanner, and installation seemed to go well... I haven't tested scanning yet though, but I will still include what happened also with the scan installation.

Here is how the installation went:

```

pjo@xubuntu:~/installations/MyUbuntu$ ls
cnijfilter-mx870series-3.30-1-i386-deb
cnijfilter-mx870series-3.30-1-i386-deb.tar.gz
scangearmp-mx870series-1.50-1-i386-deb.tar.gz
pjo@xubuntu:~/installations/MyUbuntu$ tar -xvzf cnijfilter-mx870series-3.30-1-i386-deb.tar.gz 
cnijfilter-mx870series-3.30-1-i386-deb/
cnijfilter-mx870series-3.30-1-i386-deb/packages/
cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-common_3.30-1_i386.deb
cnijfilter-mx870series-3.30-1-i386-deb/packages/cnijfilter-mx870series_3.30-1_i386.deb
cnijfilter-mx870series-3.30-1-i386-deb/resources/
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_zh_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_ja_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/resources/printer_fr_utf8.lc
cnijfilter-mx870series-3.30-1-i386-deb/install.sh
pjo@xubuntu:~/installations/MyUbuntu$ cd cnijfilter-mx870series-3.30-1-i386-deb/
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ vi install.sh 
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ ./install.sh 
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
[sudo] password for pjo: 
Selecting previously unselected package cnijfilter-common.
(Luetaan tietokantaa... 240611 files and directories currently installed.)
Puretaan pakettia cnijfilter-common (.../cnijfilter-common_3.30-1_i386.deb)...
dpkg: dependency problems prevent configuration of cnijfilter-common:
 cnijfilter-common riippuu paketista libpopt0 (>= 1.7).

dpkg: error processing cnijfilter-common (--install):
 riippuvuusongelmia - jätetään asetukset säätämättä
Käsittelyssä tapahtui liian monta virhettä:
 cnijfilter-common
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ sudo apt-get install libpop0
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
E: Pakettia libpop0 ei löydy
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ sudo apt-get install libpopt0
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
libpopt0 on jo uusin versio.
Saatat haluta suorittaa "apt-get -f install" korjaamaan nämä:
Näillä paketeilla on tyydyttämättömiä riippuvuuksia:
 cnijfilter-common:i386 : Riippuvuudet: libpopt0:i386 (>= 1.7) mutta ei ole merkitty asennettavaksi
E: Kaikkia riippuvuuksia ei ole tyydytetty. Kokeile "apt-get -f install" ilmanpaketteja (tai ratkaise itse).
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ apt-get -f install
E: Lukkotiedostoa /var/lib/dpkg/lock ei voitu avata - open (13: Lupa evätty)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ sudo apt-get -f install
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
Korjataan riippuvuuksia... Valmis
Seuraavat ylimääräiset paketit on merkitty asennettaviksi:
  libpopt0:i386
Seuraavat UUDET paketit asennetaan:
  libpopt0:i386
0 päivitetty, 1 uutta asennusta, 0 poistettavaa ja 15 päivittämätöntä.
1 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 29,4 kt.
Toiminnon jälkeen käytetään 131 k t lisää levytilaa.
Haluatko jatkaa [K/e]? k
Nouda:1 http://fi.archive.ubuntu.com/ubuntu/ raring/main libpopt0 i386 1.16-7ubuntu3 [29,4 kB]
Noudettiin 29,4 kt ajassa 0s (498 kt/s)
Selecting previously unselected package libpopt0:i386.
(Luetaan tietokantaa... 240627 files and directories currently installed.)
Puretaan pakettia libpopt0:i386 (.../libpopt0_1.16-7ubuntu3_i386.deb)...
Tehdään asetuksia: libpopt0:i386 (1.16-7ubuntu3) ...
Tehdään asetuksia: cnijfilter-common (3.30-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ ./install.sh 
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
(Luetaan tietokantaa... 240629 files and directories currently installed.)
Valmistellaan paketin cnijfilter-common 3.30-1 vaihtamista (käyttäen pakettia .../cnijfilter-common_3.30-1_i386.deb)...
Puretaan korvaavaa cnijfilter-common-pakettia...
Tehdään asetuksia: cnijfilter-common (3.30-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-mx870series_3.30-1_i386.deb
Selecting previously unselected package cnijfilter-mx870series.
(Luetaan tietokantaa... 240629 files and directories currently installed.)
Puretaan pakettia cnijfilter-mx870series (.../cnijfilter-mx870series_3.30-1_i386.deb)...
dpkg: dependency problems prevent configuration of cnijfilter-mx870series:
 cnijfilter-mx870series riippuu paketista libatk1.0-0 (>= 1.9.0).
 cnijfilter-mx870series riippuu paketista libcairo2 (>= 1.0.2-2).
 cnijfilter-mx870series riippuu paketista libgtk2.0-0 (>= 2.8.0).
 cnijfilter-mx870series riippuu paketista libpango1.0-0 (>= 1.12.3).
 cnijfilter-mx870series riippuu paketista libtiff4.
 cnijfilter-mx870series riippuu paketista libxcursor1 (>> 1.1.2).
 cnijfilter-mx870series riippuu paketista libxinerama1.
 cnijfilter-mx870series riippuu paketista libxrandr2.

dpkg: error processing cnijfilter-mx870series (--install):
 riippuvuusongelmia - jätetään asetukset säätämättä
Käsittelyssä tapahtui liian monta virhettä:
 cnijfilter-mx870series
Command executed = sudo dpkg -P cnijfilter-common
(Luetaan tietokantaa... 240828 files and directories currently installed.)
Poistetaan pakettia cnijfilter-common...
Poistetaan asetustiedostoineen paketti cnijfilter-common...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ sudo apt-get install libatk1.0-0
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
libatk1.0-0 on jo uusin versio.
Saatat haluta suorittaa "apt-get -f install" korjaamaan nämä:
Näillä paketeilla on tyydyttämättömiä riippuvuuksia:
 cnijfilter-mx870series:i386 : Riippuvuudet: libatk1.0-0:i386 (>= 1.9.0) mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libcairo2:i386 (>= 1.0.2-2) mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libgtk2.0-0:i386 (>= 2.8.0) mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libpango1.0-0:i386 (>= 1.12.3) mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libtiff4:i386 mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libxcursor1:i386 (> 1.1.2) mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libxinerama1:i386 mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: libxrandr2:i386 mutta ei ole merkitty asennettavaksi
                               Riippuvuudet: cnijfilter-common:i386 (>= 3.30) mutta ei ole asennuskelpoinen
E: Kaikkia riippuvuuksia ei ole tyydytetty. Kokeile "apt-get -f install" ilmanpaketteja (tai ratkaise itse).
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ sudo apt-get -f install
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
Korjataan riippuvuuksia... Valmis
Seuraavat paketit on alun perin asennettu automaattisesti, eikä niitä enää tarvita:
  libatk1.0-0:i386 libcairo2:i386 libgdk-pixbuf2.0-0:i386 libgtk2.0-0:i386
  libharfbuzz0:i386 libjasper1:i386 libpango1.0-0:i386 libpixman-1-0:i386
  libpopt0:i386 libtiff4:i386 libxcb-render0:i386 libxcb-shm0:i386
  libxcomposite1:i386 libxcursor1:i386 libxft2:i386 libxinerama1:i386
  libxrandr2:i386
Use 'apt-get autoremove' to remove them.
Seuraavat ylimääräiset paketit on merkitty asennettaviksi:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libgtk2.0-0:i386 libharfbuzz0:i386 libicu48:i386 libjasper1:i386
  libpango1.0-0:i386 libpixman-1-0:i386 libthai0:i386 libtiff4:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxrandr2:i386
Ehdotetut paketit:
  librsvg2-common:i386 gvfs:i386 libjasper-runtime:i386 ttf-baekmuk:i386
  ttf-arphic-gbsn00lp:i386 ttf-arphic-bsmi00lp:i386 ttf-arphic-gkai00mp:i386
  ttf-arphic-bkai00mp:i386
Seuraavat paketit POISTETAAN:
  cnijfilter-mx870series:i386
Seuraavat UUDET paketit asennetaan:
  libatk1.0-0:i386 libcairo2:i386 libdatrie1:i386 libgdk-pixbuf2.0-0:i386
  libgtk2.0-0:i386 libharfbuzz0:i386 libicu48:i386 libjasper1:i386
  libpango1.0-0:i386 libpixman-1-0:i386 libthai0:i386 libtiff4:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcomposite1:i386 libxcursor1:i386
  libxft2:i386 libxinerama1:i386 libxrandr2:i386
0 päivitetty, 19 uutta asennusta, 1 poistettavaa ja 15 päivittämätöntä.
1 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 8 548 kt.
Toiminnon jälkeen käytetään 27,1 M t lisää levytilaa.
Haluatko jatkaa [K/e]? k
Nouda:1 http://fi.archive.ubuntu.com/ubuntu/ raring/main libatk1.0-0 i386 2.8.0-1 [49,0 kB]
Nouda:2 http://fi.archive.ubuntu.com/ubuntu/ raring/main libpixman-1-0 i386 0.28.2-0ubuntu1 [250 kB]
Nouda:3 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libxcb-render0 i386 1.8.1-2ubuntu2.1 [14,2 kB]
Nouda:4 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libxcb-shm0 i386 1.8.1-2ubuntu2.1 [5 748 B]
Nouda:5 http://fi.archive.ubuntu.com/ubuntu/ raring/main libcairo2 i386 1.12.14-0ubuntu1 [643 kB]
Nouda:6 http://fi.archive.ubuntu.com/ubuntu/ raring/main libdatrie1 i386 0.2.6-1 [16,9 kB]
Nouda:7 http://fi.archive.ubuntu.com/ubuntu/ raring/main libjasper1 i386 1.900.1-14 [154 kB]
Nouda:8 http://fi.archive.ubuntu.com/ubuntu/ raring/main libgdk-pixbuf2.0-0 i386 2.28.0-0ubuntu1 [157 kB]
Nouda:9 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libicu48 i386 4.8.1.1-12ubuntu0.1 [4 771 kB]
Nouda:10 http://fi.archive.ubuntu.com/ubuntu/ raring/main libharfbuzz0 i386 0.9.13-1 [270 kB]
Nouda:11 http://fi.archive.ubuntu.com/ubuntu/ raring/main libthai0 i386 0.1.19-1 [17,6 kB]
Nouda:12 http://fi.archive.ubuntu.com/ubuntu/ raring/main libxft2 i386 2.3.1-1 [43,2 kB]
Nouda:13 http://fi.archive.ubuntu.com/ubuntu/ raring/main libpango1.0-0 i386 1.32.5-0ubuntu1 [234 kB]
Nouda:14 http://fi.archive.ubuntu.com/ubuntu/ raring/main libxcomposite1 i386 1:0.4.3-2build2 [7 664 B]
Nouda:15 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libxcursor1 i386 1:1.1.13-1ubuntu0.13.04.1 [23,8 kB]
Nouda:16 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libxinerama1 i386 2:1.1.2-1ubuntu0.13.04.1 [8 230 B]
Nouda:17 http://fi.archive.ubuntu.com/ubuntu/ raring-updates/main libxrandr2 i386 2:1.4.0-1ubuntu1.1 [19,2 kB]
Nouda:18 http://fi.archive.ubuntu.com/ubuntu/ raring/main libgtk2.0-0 i386 2.24.17-0ubuntu2 [1 719 kB]
Nouda:19 http://fi.archive.ubuntu.com/ubuntu/ raring/universe libtiff4 i386 3.9.7-0ubuntu1 [144 kB]
Noudettiin 8 548 kt ajassa 7s (1 204 kt/s)                                     
(Luetaan tietokantaa... 240813 files and directories currently installed.)
Poistetaan pakettia cnijfilter-mx870series...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Selecting previously unselected package libatk1.0-0:i386.
(Luetaan tietokantaa... 240613 files and directories currently installed.)
Puretaan pakettia libatk1.0-0:i386 (.../libatk1.0-0_2.8.0-1_i386.deb)...
Selecting previously unselected package libpixman-1-0:i386.
Puretaan pakettia libpixman-1-0:i386 (.../libpixman-1-0_0.28.2-0ubuntu1_i386.deb)...
Selecting previously unselected package libxcb-render0:i386.
Puretaan pakettia libxcb-render0:i386 (.../libxcb-render0_1.8.1-2ubuntu2.1_i386.deb)...
Selecting previously unselected package libxcb-shm0:i386.
Puretaan pakettia libxcb-shm0:i386 (.../libxcb-shm0_1.8.1-2ubuntu2.1_i386.deb)...
Selecting previously unselected package libcairo2:i386.
Puretaan pakettia libcairo2:i386 (.../libcairo2_1.12.14-0ubuntu1_i386.deb)...
Selecting previously unselected package libdatrie1:i386.
Puretaan pakettia libdatrie1:i386 (.../libdatrie1_0.2.6-1_i386.deb)...
Selecting previously unselected package libjasper1:i386.
Puretaan pakettia libjasper1:i386 (.../libjasper1_1.900.1-14_i386.deb)...
Selecting previously unselected package libgdk-pixbuf2.0-0:i386.
Puretaan pakettia libgdk-pixbuf2.0-0:i386 (.../libgdk-pixbuf2.0-0_2.28.0-0ubuntu1_i386.deb)...
Selecting previously unselected package libicu48:i386.
Puretaan pakettia libicu48:i386 (.../libicu48_4.8.1.1-12ubuntu0.1_i386.deb)...
Selecting previously unselected package libharfbuzz0:i386.
Puretaan pakettia libharfbuzz0:i386 (.../libharfbuzz0_0.9.13-1_i386.deb)...
Selecting previously unselected package libthai0:i386.
Puretaan pakettia libthai0:i386 (.../libthai0_0.1.19-1_i386.deb)...
Selecting previously unselected package libxft2:i386.
Puretaan pakettia libxft2:i386 (.../libxft2_2.3.1-1_i386.deb)...
Selecting previously unselected package libpango1.0-0:i386.
Puretaan pakettia libpango1.0-0:i386 (.../libpango1.0-0_1.32.5-0ubuntu1_i386.deb)...
Selecting previously unselected package libxcomposite1:i386.
Puretaan pakettia libxcomposite1:i386 (.../libxcomposite1_1%3a0.4.3-2build2_i386.deb)...
Selecting previously unselected package libxcursor1:i386.
Puretaan pakettia libxcursor1:i386 (.../libxcursor1_1%3a1.1.13-1ubuntu0.13.04.1_i386.deb)...
Selecting previously unselected package libxinerama1:i386.
Puretaan pakettia libxinerama1:i386 (.../libxinerama1_2%3a1.1.2-1ubuntu0.13.04.1_i386.deb)...
Selecting previously unselected package libxrandr2:i386.
Puretaan pakettia libxrandr2:i386 (.../libxrandr2_2%3a1.4.0-1ubuntu1.1_i386.deb)...
Selecting previously unselected package libgtk2.0-0:i386.
Puretaan pakettia libgtk2.0-0:i386 (.../libgtk2.0-0_2.24.17-0ubuntu2_i386.deb)...
Selecting previously unselected package libtiff4:i386.
Puretaan pakettia libtiff4:i386 (.../libtiff4_3.9.7-0ubuntu1_i386.deb)...
Tehdään asetuksia: libatk1.0-0:i386 (2.8.0-1) ...
Tehdään asetuksia: libpixman-1-0:i386 (0.28.2-0ubuntu1) ...
Tehdään asetuksia: libxcb-render0:i386 (1.8.1-2ubuntu2.1) ...
Tehdään asetuksia: libxcb-shm0:i386 (1.8.1-2ubuntu2.1) ...
Tehdään asetuksia: libcairo2:i386 (1.12.14-0ubuntu1) ...
Tehdään asetuksia: libdatrie1:i386 (0.2.6-1) ...
Tehdään asetuksia: libjasper1:i386 (1.900.1-14) ...
Tehdään asetuksia: libgdk-pixbuf2.0-0:i386 (2.28.0-0ubuntu1) ...
Tehdään asetuksia: libicu48:i386 (4.8.1.1-12ubuntu0.1) ...
Tehdään asetuksia: libharfbuzz0:i386 (0.9.13-1) ...
Tehdään asetuksia: libthai0:i386 (0.1.19-1) ...
Tehdään asetuksia: libxft2:i386 (2.3.1-1) ...
Tehdään asetuksia: libpango1.0-0:i386 (1.32.5-0ubuntu1) ...
Tehdään asetuksia: libxcomposite1:i386 (1:0.4.3-2build2) ...
Tehdään asetuksia: libxcursor1:i386 (1:1.1.13-1ubuntu0.13.04.1) ...
Tehdään asetuksia: libxinerama1:i386 (2:1.1.2-1ubuntu0.13.04.1) ...
Tehdään asetuksia: libxrandr2:i386 (2:1.4.0-1ubuntu1.1) ...
Tehdään asetuksia: libgtk2.0-0:i386 (2.24.17-0ubuntu2) ...
Tehdään asetuksia: libtiff4:i386 (3.9.7-0ubuntu1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$ ./install.sh 
==================================================

Canon Inkjet Printer Driver Ver.3.30-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-common_3.30-1_i386.deb
Selecting previously unselected package cnijfilter-common.
(Luetaan tietokantaa... 240730 files and directories currently installed.)
Puretaan pakettia cnijfilter-common (.../cnijfilter-common_3.30-1_i386.deb)...
Tehdään asetuksia: cnijfilter-common (3.30-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG ./packages/cnijfilter-mx870series_3.30-1_i386.deb
Selecting previously unselected package cnijfilter-mx870series.
(Luetaan tietokantaa... 240746 files and directories currently installed.)
Puretaan pakettia cnijfilter-mx870series (.../cnijfilter-mx870series_3.30-1_i386.deb)...
Tehdään asetuksia: cnijfilter-mx870series (3.30-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

#=========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]2

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Target printers detected (MAC address  IP address)
1) Canon MX870 series (00-1E-8F-92-0F-A3 192.168.1.6)
-----------------------------------------------------------
Currently selected:[1] Canon MX870 series (00-1E-8F-92-0F-A3 192.168.1.6)
Enter the value. [1]

#=========================================================#
#  Register Printer
#=========================================================#
Enter the printer name.[MX870LAN]
Command executed = sudo /usr/sbin/lpadmin -p MX870LAN -m canonmx870.ppd -v cnijnet:/00-1E-8F-92-0F-A3 -E

#=========================================================#
#  Set as Default Printer
#=========================================================#
Do you want to set this printer as the default printer?
Enter [y] for Yes or [n] for No.[y]y

#=========================================================#
Installation has been completed.
Printer Name : MX870LAN
Select this printer name for printing.
#=========================================================#
pjo@xubuntu:~/installations/MyUbuntu/cnijfilter-mx870series-3.30-1-i386-deb$

```

Scanner installation complained less:

```

pjo@xubuntu:~/installations/MyUbuntu$ cd scangearmp-mx870series-1.50-1-i386-deb/pjo@xubuntu:~/installations/MyUbuntu/scangearmp-mx870series-1.50-1-i386-deb$ ls
install.sh  packages  resources
pjo@xubuntu:~/installations/MyUbuntu/scangearmp-mx870series-1.50-1-i386-deb$ vi install.sh 
pjo@xubuntu:~/installations/MyUbuntu/scangearmp-mx870series-1.50-1-i386-deb$ ./install.sh 
==================================================

ScanGear MP Ver.1.50-1 for Linux
Copyright CANON INC. 2007-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/scangearmp-common_1.50-1_i386.deb
[sudo] password for pjo: 
Selecting previously unselected package scangearmp-common.
(Luetaan tietokantaa... 240946 files and directories currently installed.)
Puretaan pakettia scangearmp-common (.../scangearmp-common_1.50-1_i386.deb)...
dpkg: dependency problems prevent configuration of scangearmp-common:
 scangearmp-common riippuu paketista libusb-0.1-4 (>= 2:0.1.10a).

dpkg: error processing scangearmp-common (--install):
 riippuvuusongelmia - jätetään asetukset säätämättä
Käsittelyssä tapahtui liian monta virhettä:
 scangearmp-common
pjo@xubuntu:~/installations/MyUbuntu/scangearmp-mx870series-1.50-1-i386-deb$ sudo apt-get -f install
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
Korjataan riippuvuuksia... Valmis
Seuraavat ylimääräiset paketit on merkitty asennettaviksi:
  libusb-0.1-4:i386
Seuraavat UUDET paketit asennetaan:
  libusb-0.1-4:i386
0 päivitetty, 1 uutta asennusta, 0 poistettavaa ja 15 päivittämätöntä.
1 ei asennettu kokonaan tai poistettiin.
Noudettavaa arkistoa 17,5 kt.
Toiminnon jälkeen käytetään 73,7 k t lisää levytilaa.
Haluatko jatkaa [K/e]? k
Nouda:1 http://fi.archive.ubuntu.com/ubuntu/ raring/main libusb-0.1-4 i386 2:0.1.12-23+nmu1ubuntu1 [17,5 kB]
Noudettiin 17,5 kt ajassa 0s (400 kt/s)
Selecting previously unselected package libusb-0.1-4:i386.
(Luetaan tietokantaa... 240993 files and directories currently installed.)
Puretaan pakettia libusb-0.1-4:i386 (.../libusb-0.1-4_2%3a0.1.12-23+nmu1ubuntu1_i386.deb)...
Tehdään asetuksia: libusb-0.1-4:i386 (2:0.1.12-23+nmu1ubuntu1) ...
Tehdään asetuksia: scangearmp-common (1.50-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
pjo@xubuntu:~/installations/MyUbuntu/scangearmp-mx870series-1.50-1-i386-deb$ ./install.sh 
==================================================

ScanGear MP Ver.1.50-1 for Linux
Copyright CANON INC. 2007-2010
All Rights Reserved.

==================================================
Command executed = sudo dpkg --force-architecture -iG ./packages/scangearmp-common_1.50-1_i386.deb
(Luetaan tietokantaa... 240995 files and directories currently installed.)
Valmistellaan paketin scangearmp-common 1.50-1 vaihtamista (käyttäen pakettia .../scangearmp-common_1.50-1_i386.deb)...
Puretaan korvaavaa scangearmp-common-pakettia...
Tehdään asetuksia: scangearmp-common (1.50-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Command executed = sudo dpkg --force-architecture -iG ./packages/scangearmp-mx870series_1.50-1_i386.deb
Selecting previously unselected package scangearmp-mx870series.
(Luetaan tietokantaa... 240995 files and directories currently installed.)
Puretaan pakettia scangearmp-mx870series (.../scangearmp-mx870series_1.50-1_i386.deb)...
Tehdään asetuksia: scangearmp-mx870series (1.50-1) ...
Suoritetaan kohteen libc-bin liipaisimia...
ldconfig deferred processing now taking place
Installation has been completed.

```

---

### Post by glenn2310 on 2014-05-30
Hi, I finaly got my MX870 to work on Xubuntu 64Bit 14.04 and Ubuntu 64Bit 14.04. see link -->[http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/#comment-318635](http://linuxg.net/how-to-install-drivers-for-canon-printers-pixma-mx-series-on-ubuntu-14-0413-1013-0412-1012-04-linux-mint-16151413-pear-os-87-and-elementary-os-0-2/#comment-318635)
Regards

---

### Post by kit4 on 2014-07-04
I'm trying to install wirelessly on several i368 and 64bit systems all with Ubuntu 14.04

I keep getting the error message

> dependency problems prevent configuration of cnijfilter-mx870series:
 cnijfilter-mx870series depends on libtiff4.


I downloaded and installed libtiff4 but it is still happening.

---

### Post by pdc on 2014-07-04
and what does > [COLOR="#FF0000"]dpkg -l | grep libtiff4[/COLOR]

give please kit if you copy and paste the command into a terminal please?

---

### Post by kit4 on 2014-07-04
Hi pdc, thanks for the reply

it gives this
> ii  libtiff4:amd64                                              3.9.7-2ubuntu1                                      amd64        Tag Image File Format (TIFF) library (old version)


---

### Post by Fred T on 2014-07-29
I was following the steps given by PDC in post #180. I'm running Ubuntu 14.04 on an i386 64 bit.

I got errors in the steps after listing the directory.
>                          $ ls 
 cnijfilter-common_3.30-1_i386.deb  cnijfilter-mx870series_3.30-1_i386.deb 
 fred@upstairs:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb/packages
 $ sudo dpkg -i cnijfilter-common_3.30-1_i386.deb 
 dpkg: warning: downgrading cnijfilter-common from 3.90-76~ubuntu14.04.1 to 3.30-1 
 (Reading database ... 195457 files and directories currently installed.) 
 Preparing to unpack cnijfilter-common_3.30-1_i386.deb ... 
 Unpacking cnijfilter-common (3.30-1) over (3.90-76~ubuntu14.04.1) ... 
 Setting up cnijfilter-common (3.30-1) ... 
 Processing triggers for libc-bin (2.19-0ubuntu6) ... 
 Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
 Processing triggers for desktop-file-utils (0.22-1ubuntu1) ... 
 Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ... 
 Rebuilding /usr/share/applications/bamf-2.index... 
 Processing triggers for mime-support (3.54ubuntu1) ... 
 fred@upstairs:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb/packages$ sudo dpkg -i cnijfilter-mx870series_3.30-1_i386.deb 
 dpkg: warning: downgrading cnijfilter-mx870series from 3.90-76~ubuntu14.04.1 to 3.30-1 
 (Reading database ... 195450 files and directories currently installed.) 
 Preparing to unpack cnijfilter-mx870series_3.30-1_i386.deb ... 
 Unpacking cnijfilter-mx870series (3.30-1) over (3.90-76~ubuntu14.04.1) ... 
 dpkg: dependency problems prevent configuration of cnijfilter-mx870series: 
  cnijfilter-mx870series depends on libtiff4; however: 
  
 dpkg: error processing package cnijfilter-mx870series (--install): 
  dependency problems - leaving unconfigured 
 Processing triggers for libc-bin (2.19-0ubuntu6) ... 
 Errors were encountered while processing: 
  cnijfilter-mx870series 
 fred@upstairs:~/Downloads/cnijfilter-mx870series-3.30-1-i386-deb/packages$  
  

Where did I go wrong? It's been too many years since I was a UNIX operator.
TIA

---

### Post by pdc on 2014-07-29
when I see > downgrading cnijfilter-common from 3.90-76~ubuntu14.04.1 to 3.30-1 

........it makes me think you already have cnijfilter-common 3.90-76~ubuntu14.04.1 installed; and that you are attempting to further install cnijfilter-common 3.30-1 

________________

often forum postings are like poker: you can't see the cards in the other guy's hands .......... do you want to tell us a little more about your system and what you have done etc

______________

> i386 64 bit.

.........now some folks would call that "hedging your bets":  ................ hopefully you have a 386 system as that would match your printer ............... something that is worth remembering as one forges ahead installing the latest, brightest, shinyiest, fastest, buggiest ................

_________________


Canon provides an install script in the 870 package; it takes care of the install; the point behind the posts around #180 were .....how to do a more manual install of what is needed.............. most should be able to run the install script alone ..................

____________________

often one is best to start a new thread: go on; you're important; start a new thread; old, old, long threads get messy ..................

---

### Post by madridsito on 2015-05-11
I did that and it works fine (Ubuntu 12.04.5 LTS 32bits)

## rpm and deb are error, or rpm and deb are no error, is error ##
    #if [ $c_system_rpm = 0 -a $c_system_deb = 0 ] || [ $c_system_rpm != 0 -a $c_system_deb != 0 ]; then
    #    printf "$L_INST_COM_01_02"
    #    return $C_ERR_CODE
    #else
    #    if test $c_system_rpm -eq 0; then
    #        C_system="rpm"
            C_arch32="i386"
            C_arch64="x86_64"
    #    else
            C_system="deb"
            C_arch32="i386"
            C_arch64="amd64"
    #    fi
    #fi

---

