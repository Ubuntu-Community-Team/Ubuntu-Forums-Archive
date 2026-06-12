---
title: "Brother MFC-7860DW"
date: 2011-10-04
forum: Hardware
---

### Post by jaime256 on 2011-10-04
Hi. I'm trying to install the drivers for this all-in-one machine in my Ubuntu 11.04 32 and 64 bit 10.04 but the downloaded drivers apparently are something someone converted from an rpm and the system just tells me what's on the attachment when I try to install it, so I just canceled it. The only way I have been able to get the printer to work is by using the hpjetdirect, but it's using the 7840 drivers. Are the drivers for this machine going to be added to make use of all the features of the-all-in one machines? It's my first all-in-one and I'm still using my old brother laser which has been working great. This one is: [http://www.brother-usa.com/MFC/ModelDetail.aspx?ProductID=MFC7860DW#.TotAZx9VLR1](http://www.brother-usa.com/MFC/ModelDetail.aspx?ProductID=MFC7860DW#.TotAZx9VLR1)

Here's where I downloaded the drivers but they don't work. I also tried on Ubuntu 10.04 and that system just tells me it's the wrong architecture since it's the 64 bit.
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7860DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7860DW)

I'll stick with the jetdirect for now since that's the only one I can get to work for printing, unfortunately these drivers don't support duplex printing which is what I would like to use, darn. I wanted to scan something but the machine says check connection when I press the scan button. I'm not sure if it's just due to not having the software installed anywhere since that's all for windows or something is actually wrong with the machine. I'll be checking that...

---

### Post by Shazaam on 2011-10-04
I ran into the same problem with my MFC-420cn. here is how I fixed it...

!. Scrounged around in Synaptic and found the right drivers. WOO HOO!
2. Uninstalled the drivers that I downloaded from the Brother website.
3. Used Synaptic to install the Brother cupswrapper and lpr drivers (common and extra for both).
4. Went to System/Administration/Printing and added my printer.
Done.

If you want to use the scanner you will have to install the Brother drivers from their site.

---

### Post by jaime256 on 2011-10-04
Thanks for the input. Unfortunately I only see the one for the one you mentioned and nothing else under 10.04. Nothing for any other mfc machine.




> **Shazaam said:**
> I ran into the same problem with my MFC-420cn. here is how I fixed it...

!. Scrounged around in Synaptic and found the right drivers. WOO HOO!
2. Uninstalled the drivers that I downloaded from the Brother website.
3. Used Synaptic to install the Brother cupswrapper and lpr drivers (common and extra for both).
4. Went to System/Administration/Printing and added my printer.
Done.

If you want to use the scanner you will have to install the Brother drivers from their site.

---

### Post by jaime256 on 2011-10-04
I just went ahead and added the mfc-420 driver to see if I would get anything else when I tried to add the printer, but I'm still getting the same thing. They show up but none of the two work if you choose them unfortunately just like before. Only the jetdirect does let me print, but I can't use the duplex printing since I guess those other drivers from the older suggested models didn't support or had this option.

---

### Post by frogotronic on 2011-10-04
You have to follow all the instructions for the install from Brother.  Then it will work.

for LPR [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

for CUPS [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I did this for a wireless HL-3070CW and it worked perfectly

---

### Post by jaime256 on 2011-10-05
I tried this but still doesn't work.

x@x:~$ cd mfc78mfc7860dwlpr-2.1.0-1.i386.deb
bash: cd: mfc78mfc7860dwlpr-2.1.0-1.i386.deb: No such file or directory
x@x:~$ dpkg  -i  --force-all mfcmfc7860dwlpr-2.1.0-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
x@x:~$ sudo dpkg  -i  --force-all mfcmfc7860dwlpr-2.1.0-1.i386.deb
[sudo] password for x: 
dpkg: error processing mfcmfc7860dwlpr-2.1.0-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfcmfc7860dwlpr-2.1.0-1.i386.deb

I also tried just copying and pasting but still no luck.
x@x:~$ dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
x@x:~$ 


> **cement_head said:**
> You have to follow all the instructions for the install from Brother.  Then it will work.

for LPR [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

for CUPS [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I did this for a wireless HL-3070CW and it worked perfectly

---

### Post by jaime256 on 2011-10-05
Okay I saw my mistake on the previous try...now I got this..
x@x:~$ dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
x@x:~$ sudo dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc7860dwlpr.
(Reading database ... 192618 files and directories currently installed.)
Unpacking mfc7860dwlpr (from mfc7860dwlpr-2.1.0-1.i386.deb) ...
Setting up mfc7860dwlpr (2.1.0-1) ...

So I'll go fetch the 64 bit...and see if I can do anything...well I don't see any 64bit this other one still spits out the error that I'm using the wrong one...

---

### Post by frogotronic on 2011-10-05
> **jaime256 said:**
> Okay I saw my mistake on the previous try...now I got this..
x@x:~$ dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
dpkg: operation requires read/write access to dpkg status area
x@x:~$ sudo dpkg -i --force-all mfc7860dwlpr-2.1.0-1.i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc7860dwlpr.
(Reading database ... 192618 files and directories currently installed.)
Unpacking mfc7860dwlpr (from mfc7860dwlpr-2.1.0-1.i386.deb) ...
Setting up mfc7860dwlpr (2.1.0-1) ...

So I'll go fetch the 64 bit...and see if I can do anything...well I don't see any 64bit this other one still spits out the error that I'm using the wrong one...

You can force install the 64 bit, if you have the ia32 libraries installed - they should work without issue.

---

### Post by jaime256 on 2011-10-05
Thanks. I did check and that library was already installed so I just double checked again today and yes they were but that didn't work. I guess I'll wait until next week when the new version of Ubuntu is released and re-install this whole machine and hopefully that will be better, but I won't hold my breath. I'm not liking the way their drivers are set up.

---

### Post by frogotronic on 2011-10-05
Hi,

   I set up a Brother HL3040CN and a HL-3070CW using these instructions and it worked perfectly.

  I did try to shortcut the install on the HL-3040CN and it was a disaster.  I uninstalled the lpr and the cups drivers and then followed the instructions to the letter and it then worked.

  Maybe try uninstalling and then reinstalling.

  Before you start, you'll have to set a root password, not just using sudo for some of the commands.

- CH

---

### Post by jaime256 on 2011-10-09
Well I couldn't wait to re-install the os, so now I installed ubuntu 11.04 64 bit on my computer. I didn't bother to add any of the brother drivers since I still don't like that install, but that's just me. So I did a search for a network printer and it found the AppSocket/JetDirect as well as the brother with some other numbers. I chose the JetDirect as usual since I know that at least lets me print. Although there is no driver specifically for this printer as an option I chose the recommended which is MFC-7840W. I think this was the same one I tried last, can't remember now. In any case I just sent something to the printer, but it took a little bit to print 3 pages. The funny thing is that I've been trying to print on both sides of a page and looking at the options, it's grayed out but after the print came out, I noticed it said it was receiving a fax, which I don't have plugged into a phone line, but still printed the first two pages on both sides and the third on the second page. Pretty neat since I can't choose that option under the properties. Anyway this isn't working the way it should but I just thought I let people know that you can still get a print out of it like this for the time being without hopefully wasting too much paper.

---

### Post by jaime256 on 2011-10-09
I just sent another print out with the "Copy" key pressed, but I still get the getting info or something like that and it takes the same amount of time to print, so it really doesn't matter which of the two buttons is pressed. You can't use the scan button as is so that's not even an option. The good thing is that it still prints on both sides. I thought it was my old printer, but I'm finding out that the browser is the one that sends out a crappy print not the lasers. Some tiny parts get cut off, or at least that's how it's printing. Okay it may also be due to the drivers, I really don't know.

---

### Post by kumoshk on 2012-04-04
I got it to work, but on 32-bit Debian (Squeeze), rather than Ubuntu. I believe there's not a whole lot of difference, except that the alien-converted packages work better on Debian (at least 32-bit Debian).

In my case, I was primarily looking for scanner functionality, but I somehow managed to get both that and the printer to work.

Here's what I had to do, or close enough (not all of it is obvious):

PRINTER

Install the alien deb files from the Brother site. Hopefully the other user posts will let you do it, but if you have Debian 32-bit it should just work like any other package.

1. You might have to install the pre-requisites mentioned on the Brother site and open up port 54925 (choose UDP) on your router's port forwarding. I don't know if they're really required, but I did do those things (well, many of them; I left a few out, like all that making of directories and running aa-complain. See this URL: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)
2. Go to set up a printer and under the network printer part (I'm using a network printer, at work), choose AppSocket/HP JetDirect.
3. Put your printer's IP address into the host (port 9100). Might want to figure it out if you don't know it. You'll need it for the scanner, later on.
4. Select the Brother driver entitled MFC7860DW for CUPS, and choose the recommended one within that (the top one, for me).
5. Print the test page. Worked for me. Printer is done.


SCANNER

Now for the scanner. Your printer driver won't work. You'll need a separate scanner driver. Fortunately, the Brother site actually has one.

1. Go to this link:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

2. Click on Scanner Driver / Scan-Key-Tool

3. Download and install the deb files (brscan4 and scan-key-tool). I got the 32-bit ones, of course.

4. This is the tricky part. There aren't any instructions after that, and it still doesn't work. So, what do you do? Well, I don't know how, but somehow I figured out that brsaneconfig4 was a command-line tool that was just installed and that might help. So, I did some trial and error, and by some miracle eventually I found that the following command effectively set up my scanner:

```
brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.185
```

Replace 192.168.1.185 with your own scanner's IP address (it's the same as the printer's, since it's the same device). The name and model is what the trial and error was on. I don't know if they're supposed to be that, but it works. So, I'm not complaining.

Anyway, then use Simple Scan (simple-scan) and it should find your scanner and be functional. xSane didn't really work too well for me, but I didn't try to get it to work that much on it&#8212;however it did locate my scanner.

Now, hopefully this'll work on Ubuntu 64-bit, since that's what you're all using. I never did like forcing those deb installs, though.

If you convert the RPMs with Ubuntu's alien, will that be any different than if someone using Debian's alien did it?

I haven't set up the fax stuff, yet, but I imagine there's a similar process.

Enjoy. Let me know if it works.

---

### Post by jaime256 on 2012-06-22
Thanks for the info cement head. I finally decided to mess with this again and I think I got this installed. At least the drivers for it. Here's what I did for anyone else trying to figure this out. I'm using Ubuntu 11.10 64bit by the way. Download both files. Then open your terminal and type both of these. just like this unless something has changed, but I was just messing around trying to figure this out and low and behold the new printer was added. The first line if for the driver and the second is for the wrapper, that's it. Just like it says on the page, but sometimes there's more info that makes it confusing. I hope this will help others. I'm attaching the terminal window so you can see what I was doing. I don't do this on a regular basis so I forget and have to keep messing with it. Now I the page option is not grayed out on the new printer, but I'll live both on to see what else has changed, they look pretty close, but it's nice to know it works, or at least it looks like it is. I just did this so we'll see. What worked is towards the end of the picture, but again all you need is to download the two files and type the two lines one at a time on the terminal and you're done.

sudo dpkg  -i  --force-all  mfc7860dwlpr-2.1.0-1.i386.deb
sudo dpkg  -i  --force-all cupswrapperMFC7860DW-2.0.4-2.i386.deb


> **cement_head said:**
> You have to follow all the instructions for the install from Brother.  Then it will work.

for LPR [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

for CUPS [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I did this for a wireless HL-3070CW and it worked perfectly

---

### Post by davidtrounce on 2012-07-05
Jaime,

I followed your tips and managed to install the  packages - the printer now appears in my list of printers. But how do I set it up for wireless? the current URI is usb:/dev/usb/lp0

---

### Post by frogotronic on 2012-07-05
> **davidtrounce said:**
> Jaime,

I followed your tips and managed to install the  packages - the printer now appears in my list of printers. But how do I set it up for wireless? the current URI is usb:/dev/usb/lp0

You need to find out the printer's IP address.  Best to print out the configuration page, then connect to the printer via an ethernet cable.  Then type in the IP address of the printer and you should get the printers HTML administration page(s).  From there you can set all the wireless parameters.

The signon is:

Login: admin
Password: access

- CH

---

### Post by davidtrounce on 2012-07-05
OK. I connected the Brother 7860DW to the wireless Moden (Netcomm NB9WMAXX). Went to system/admin/printing in Ubuntu (10.04 LTS). Add Printer found the Brother Printer: Brother MFC7860DW. Location: BRN001BA9A525BC. Device URI: lpd://BRN001BA9A525BC/BINARY_P1

Tried to print test. Error - unable to locate printer. I enabled it but each time I try and print test it disables it and says it cant find printer.

I found the IP address (report says it is via DHCP). But I do not know what settings I need to configure to get the wireless working.

Drivers are installed:
sudo dpkg  -i  --force-all  mfc7860dwlpr-2.1.0-1.i386.deb
sudo dpkg  -i  --force-all cupswrapperMFC7860DW-2.0.4-2.i386.deb

Any suggestions on what to do next?

Thanks

David.



> **cement_head said:**
> You need to find out the printer's IP address.  Best to print out the configuration page, then connect to the printer via an ethernet cable.  Then type in the IP address of the printer and you should get the printers HTML administration page(s).  From there you can set all the wireless parameters.

The signon is:

Login: admin
Password: access

- CH

---

### Post by frogotronic on 2012-07-05
Ok,  so I set my IP address as 192.168.2.107, you can choose anything like 192.168.2.xxx

Make sure you set the IP as **STATIC** , otherwise you won't be able to find it after a powerfailure.

- CH

---

### Post by davidtrounce on 2012-07-05
Thank you. This seems to have fixed it. No idea what actually changed But thank you, thank you thank you!

David

---

### Post by frogotronic on 2012-07-05
> **davidtrounce said:**
> Thank you. This seems to have fixed it. No idea what actually changed But thank you, thank you thank you!

David

great....

---

### Post by davidtrounce on 2012-07-05
Yes, indeed! this did work for both XSane and Simple Scan. Ubuntu 10.04 LTS 64bit

Thanks!!

> **kumoshk said:**
> I got it to work, but on 32-bit Debian (Squeeze), rather than Ubuntu. I believe there's not a whole lot of difference, except that the alien-converted packages work better on Debian (at least 32-bit Debian).

In my case, I was primarily looking for scanner functionality, but I somehow managed to get both that and the printer to work.

Here's what I had to do, or close enough (not all of it is obvious):

PRINTER

Install the alien deb files from the Brother site. Hopefully the other user posts will let you do it, but if you have Debian 32-bit it should just work like any other package.

1. You might have to install the pre-requisites mentioned on the Brother site and open up port 54925 (choose UDP) on your router's port forwarding. I don't know if they're really required, but I did do those things (well, many of them; I left a few out, like all that making of directories and running aa-complain. See this URL: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)
2. Go to set up a printer and under the network printer part (I'm using a network printer, at work), choose AppSocket/HP JetDirect.
3. Put your printer's IP address into the host (port 9100). Might want to figure it out if you don't know it. You'll need it for the scanner, later on.
4. Select the Brother driver entitled MFC7860DW for CUPS, and choose the recommended one within that (the top one, for me).
5. Print the test page. Worked for me. Printer is done.


SCANNER

Now for the scanner. Your printer driver won't work. You'll need a separate scanner driver. Fortunately, the Brother site actually has one.

1. Go to this link:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

2. Click on Scanner Driver / Scan-Key-Tool

3. Download and install the deb files (brscan4 and scan-key-tool). I got the 32-bit ones, of course.

4. This is the tricky part. There aren't any instructions after that, and it still doesn't work. So, what do you do? Well, I don't know how, but somehow I figured out that brsaneconfig4 was a command-line tool that was just installed and that might help. So, I did some trial and error, and by some miracle eventually I found that the following command effectively set up my scanner:

```
brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.185
```Replace 192.168.1.185 with your own scanner's IP address (it's the same as the printer's, since it's the same device). The name and model is what the trial and error was on. I don't know if they're supposed to be that, but it works. So, I'm not complaining.

Anyway, then use Simple Scan (simple-scan) and it should find your scanner and be functional. xSane didn't really work too well for me, but I didn't try to get it to work that much on it&#8212;however it did locate my scanner.

Now, hopefully this'll work on Ubuntu 64-bit, since that's what you're all using. I never did like forcing those deb installs, though.

If you convert the RPMs with Ubuntu's alien, will that be any different than if someone using Debian's alien did it?

I haven't set up the fax stuff, yet, but I imagine there's a similar process.

Enjoy. Let me know if it works.

---

### Post by Sunrise611 on 2012-12-17
I followed the confusing instructions on the Brother site for installing the printer drivers as best as I could.  I am not sure how to find if I'm missing any of the required dependencies. 

I installed the printer drivers for the MFC7860DW printer (CUPS and LPR) for the Devian pkg 64 bit.   

The printer shows up in the list of printers (the only one).  

When I try to print something, it stalls and the Printer State is: 

**Processing - Waiting for printer to become available.**

Printer Properties are as follows:  

On: **Localhost**

Location: **Blank** - how do I determine this and fill it in or is it okay to leave this blank?

Device URI: **usb:/dev/usb/lp0**

Make and Model: **Brother MFC7860DW for CUPS**

I guess there is a configuration page for the printer but I don't know where to access this and didn't find it in the instructions on Brother's site.  I need to enter the network password for it to work.

---

### Post by frogotronic on 2012-12-17
> **Sunrise611 said:**
> I followed the confusing instructions on the Brother site for installing the printer drivers as best as I could.  I am not sure how to find if I'm missing any of the required dependencies. 

I installed the printer drivers for the MFC7860DW printer (CUPS and LPR) for the Devian pkg 64 bit.   

The printer shows up in the list of printers (the only one).  

When I try to print something, it stalls and the Printer State is: 

**Processing - Waiting for printer to become available.**

Printer Properties are as follows:  

On: **Localhost**

Location: **Blank** - how do I determine this and fill it in or is it okay to leave this blank?

Device URI: **usb:/dev/usb/lp0**

Make and Model: **Brother MFC7860DW for CUPS**

I guess there is a configuration page for the printer but I don't know where to access this and didn't find it in the instructions on Brother's site.  I need to enter the network password for it to work.

Right click on the printer icon and select Properties.  Then go to the connection part and enter the IP address of the printer.  See attached screenshot.

---

### Post by Sunrise611 on 2012-12-18
I thought that worked because when I entered the IP, I was able to print a test page and got excited! 

Then when I tried to print a document, it failed, so I have more work to do.  

I found the Brother network configuration page at [http://localhost:631/printers/](http://localhost:631/printers/) and [http://localhost:631/admin](http://localhost:631/admin).  

The admin section does not show any installed printers but the printers page shows the printer. 

I modified the connection to: lpd://MyURL/binary_p1.  (Of course, the real IP # is where I have MyURL in here.)

Then I checked in Synaptics and it shows that the two printer drivers that were downloaded from Brother's site and installed are "broken".   

Under the dependencies tab, it shows: libc6 (7=2.3.4-1)

According to Brother, I need the following installed:  ia32-libs or lib32stdc++ is required to be installed.

Update:  I was able to install the ia-32 shared libraries through the Software Manager/Repository.  

At first I got a disappointing message that "The package system is broken. Check if you are using 3rd party repositories. If so, disable them since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install-f".

But then it asked me if I wanted to repair the library and I clicked "Yes" and it repaired and installed it.

Then I tested the printer and was able to print documents!  Success!

---

### Post by frogotronic on 2012-12-18
Ok, this is fixable.

Open a terminal.

Try:

```
$ sudo apt-get update
$ sudo apt-get install ia32-libs ia32-libs-multiarch:i386
$ sudo apt-get -f install
```

What does it say?

- CH

---

### Post by Sunrise611 on 2012-12-18
Thanks so much for your quick response.  I will have this for future reference.  

Our messages crossed because I updated my post to reflect that I was able to fix and install the required package from the software repository and now the printer is working!  Whew!

I'm not sure where to make the IP "static" - didn't see that in the configuration settings but that was suggested somewhere in this thread.

---

### Post by frogotronic on 2012-12-18
> **Sunrise611 said:**
> Thanks so much for your quick response.  I will have this for future reference.  

Our messages crossed because I updated my post to reflect that I was able to fix and install the required package from the software repository and now the printer is working!  Whew!

I'm not sure where to make the IP "static" - didn't see that in the configuration settings but that was suggested somewhere in this thread.

Making the IP static is done at the level of the printer.  You don't really have to worry about it except for power cycling (of the printer) or power-outages (same thing).  When the printer powers up, it will look for the first available IP address, which may or may not be the same as the previous one.

To get to the web interface, go to a browser and type [http://xxx.yyy.zzz.###](http://xxx.yyy.zzz.###), where xxx.yyy.zzz.### is the IP of your Brother printer.  The default user-name is &#8220;admin&#8221;, password is &#8220;access&#8221;.  From there you should be able to figure out how to change the IP from DHCP to static.

NB: If you make the Printer IP static, you should block out, blacklist that IP on your router, or your wireless router might accidentally assign that IP to your phone, or something else.  You'll know because all of a sudden you won't be able to print and you won't be able to see your printer on the network.  The alternative choice is to give the printer a really high range IP address.

- CH

---

### Post by Sunrise611 on 2012-12-18
Ouch!  I think I will skip that step and deal with the problem if we lose power.  Luckily, it does not happen too often here.  I am glad that I saw that caveat.

---

### Post by davidtrounce on 2012-12-23
I had to have the following in my printer properties to get it working.

Location: BRN001BA9A525BC

Device URI: lpd://192.168.1.8/BINARY_P1

make and Model: Brother MFC7860DW for CUPS

---

### Post by Sunrise611 on 2012-12-24
Thanks, David!  I have the same settings as you so it really helps to see what you did.

The only thing that I didn't put in was the BRN # in Location but it seemed to work without that.

However, if something happens and it stops working, I will enter that # in the settings.

Next, I will attempt to set up the scanner and get it working.  I installed the drivers from Brother's site using the deb package installer since I couldn't get the command line installation to work.  

Since it is a brscan4 driver (64 bit), I wil try entering the following command line:

**brsaneconfig4  -a  name=MFC-7860DW  model=MFC-7860DW  ip=xx.xx.xx.xx**

I guess I need to type "sudo" first and then enter my admin password before I type the rest.

Then, hopefully, Simple Scan will work.

---

### Post by davidtrounce on 2012-12-25
I also use a 64. To get the Scanner working I installed the two deb packages:


[LIST]
[*]brscan-skey-0.2.3-0.amd64
[*]brscan4-0.4.1-1.amd64
[/LIST]

---

### Post by Sunrise611 on 2012-12-27
Okay, going back to the printer again ... today the printer connection is suddenly not working. It worked fine when I last set it up and tested it out.  It is **Idle - "The printer is unreachable at this time" **now.

I added the BRN # to the Location in Brother's configurations and tried turning everything off and back on again but that did not seem to help.   Just to review, the settings are as follows:

> Location: BRN00... (similar # to David's but a little different and is entered according to my printer's specs)
Device URI: lpd://my-IP-#/binary_p1
make and Model: Brother MFC7860DW for CUPS

I checked the drivers in Synaptics and they seem to be installed properly.  I have the following Brother drivers installed:

> brscan-skey - o.2.4-0 (latest version) - Brother Linux scanner S-KEY tool

cupswrappermfc7860dw:i386 - 2.0.4-2 (latest version) - Brotther MFC7860DW CUPS wrapper driver

mfc6769wlpr:i386 - 2..0-1 (latest version) - Brother MFC-6769DW LPR driver

Maybe the last driver should be removed and is confusing things (the LPR driver)?

Also, when I access the Brother's configuration page, I am not able to access it from my IP # such as [http://my.IP.:631/printer](http://my.IP.:631/printer) but only from [http://localhost:631/printer](http://localhost:631/printer).

So, is the IP suddenly an issue?  (I did not change the IP to 'static' since I was afraid of messing up the printer for my other computer (a Windows system).  I did not want to have to mess with the router's settings.  

Can I alternatively get it to print if I hook it up with an ethernet connection? Would that find the printer automatically or require additional setting changes?

---

### Post by davidtrounce on 2012-12-29
I also had good success using the instructions in this post. [http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997](http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997)

---

### Post by Sunrise611 on 2012-12-29
> **davidtrounce said:**
> I also had good success using the instructions in this post. [http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997](http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997)

I do not know how to change the port forwarding in the router.  Did you do that?

Also, I am afraid to mess with the router's setting because it is a shared printer and the printer is working perfectly in the Windows computer.  I do not want to mess up the Windows computer to get the Ubuntu computer connected to the printer.  That would be crazy and more than I bargained for.

Edited to add:   Interestingly, I noticed that the URL to the local Brother configurations only shows the Ubuntu computer and not the Windows computer, which is working fine (and I'd like to keep it that way).  I'd like to get the Brother printer to work and stay working without messing with the router if possible.

---

### Post by davidtrounce on 2012-12-30
Let us know if it works

---

### Post by Sunrise611 on 2012-12-31
David, no one answered my question about port forwarding.  I am clueless and afraid to mess with my router's settings and mess up the settings for the printer in my Windows computer just to get the printer working in Ubuntu.  So, I did not mess with that.

I tried installing a new printer to see if it would fine my printer automatically and it did and let that guide me.  Now the printer is working but not with the "correct" or recommended settings by Brother.

I installed the found network printer as follows:

App Socket/Jet Direct 
Network Printer via DNS-SD

Then it automatically assigned the following parameters for Device URI and Make & Model:

Device URI: 
dnssd://Brother%20MFC-7860DW._pdl-datastream.tcp.local/

Make & Model:
Brother MFC-7840W-BR-Script3

I downloaded and installed the drivers for the 7860DW printer, not the 7850W, so I don't know why it chose that Make & Model but it is working, even after turning the printer and computer off and on again.

Is there anything wrong or insecure about using these settings as long as they continue to work?   Is a tcp connection insecure?

---

### Post by Kruxoli on 2013-01-15
Hi, I am having a problem using the scanner for my MFC-7860DW.  The printer works fine, but the scanner is a no go.

Both Simple Scan and XSane can "see" the MFC-7860DW, but neither works.

When I open XSane, I have two options:
[LIST=1]
[*]Brother MFC-7860DW MFC-7860DW [brother4:net1;dev0]
[*]Brother MFC-7860DW USB scanner [brother4:bus5;dev1]
[/LIST]

No matter what I choose, I get the following error message:

Error
Failed to open device 'brother4net1;dev0':
Invalid argument

OR

Error
Failed to open device 'brother4bus5;dev1':
Invalid argument

What am I doing wrong?  How can I get this scanner to work?  I've read this thread and followed the directions provided (I downloaded and installed the appropriate 32-bit drivers, and ran the steps listed in terminal).

THANKS!

---

### Post by Sunrise611 on 2013-01-17
I'm a newbie and I have not attempted to install the scanner yet. 

However, my first thought reading about your issue is to question if you are sure that the drivers are properly installed.  

How did you install them?

Did you look in Synaptics under Brother to see what drivers are actually installed to confirm that they were installed properly?

---

### Post by pdc on 2013-01-17
Hi Kruxoli;

you have joined another thread?

the invalid argument issue seems to be around permissions;

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/24946](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/24946)

and there are other Brother posts

eg

[https://wiki.archlinux.org/index.php/Sane](https://wiki.archlinux.org/index.php/Sane)

I have not seen this advice before but the Arch linux website says After you installed the driver you need to run 

> [COLOR="Red"]/usr/local/Brother/sane/setupSaneScan1 -i[/COLOR]

............your MFC device is connected by usb cable to a stand-alone computer, that connects by ..wire/wireless? to a router .. for home use?

_______________________________________________

I can't remember: have you seen post #21 here?

[http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997](http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997)

he talks of the same thing as in the Arch linux post above: 

For network scanners, Brother provides a configuration tool:

$ brsaneconfig4 -a name=<ScannerName> model=<ScannerModel> ip=<ScannerIP>

so in post #21 above one gets

[COLOR="SeaGreen"]brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.185[/COLOR]

---

### Post by Kruxoli on 2013-01-17
> **pdc said:**
> Hi Kruxoli;

you have joined another thread?

the invalid argument issue seems to be around permissions;

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/24946](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/24946)

and there are other Brother posts

eg

[https://wiki.archlinux.org/index.php/Sane](https://wiki.archlinux.org/index.php/Sane)

I have not seen this advice before but the Arch linux website says After you installed the driver you need to run 



............your MFC device is connected by usb cable to a stand-alone computer, that connects by ..wire/wireless? to a router .. for home use?

_______________________________________________

I can't remember: have you seen post #21 here?

[http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997](http://ubuntuforums.org/showthread.php?p=12078997&posted=1#post12078997)

he talks of the same thing as in the Arch linux post above: 

For network scanners, Brother provides a configuration tool:

$ brsaneconfig4 -a name=<ScannerName> model=<ScannerModel> ip=<ScannerIP>

so in post #21 above one gets

[COLOR="SeaGreen"]brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.185[/COLOR]

I ran the script with my devices IP address:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.100
"MFC-7860DW" is already registered.
root@kruxoli-ThinkPad-T60p:/home/kruxoli#

Yeah I posted on two threads, not sure where the help would come from...

---

### Post by Sunrise611 on 2013-03-02
> **Sunrise611 said:**
> David, no one answered my question about port forwarding.  I am clueless and afraid to mess with my router's settings and mess up the settings for the printer in my Windows computer just to get the printer working in Ubuntu.  So, I did not mess with that.

I tried installing a new printer to see if it would fine my printer automatically and it did and let that guide me.  Now the printer is working but not with the "correct" or recommended settings by Brother.

I installed the found network printer as follows:

App Socket/Jet Direct 
Network Printer via DNS-SD

Then it automatically assigned the following parameters for Device URI and Make & Model:

Device URI: 
dnssd://Brother%20MFC-7860DW._pdl-datastream.tcp.local/

Make & Model:
Brother MFC-7840W-BR-Script3

I downloaded and installed the drivers for the 7860DW printer, not the 7850W, so I don't know why it chose that Make & Model but it is working, even after turning the printer and computer off and on again.

Is there anything wrong or insecure about using these settings as long as they continue to work?   Is a tcp connection insecure?


Nobody answered this but it still works so I guess it's okay.

~ Jason

---

### Post by davidtrounce on 2013-03-03
Jason,

This is my opinion - only my opinion. If it is a home network then if it were me I would be happy with the working connection as it is and provided it is fully funvtional I would not change it. I found that my wife's laptop found our printer, installed a generic driver and away it went - no problems. For my laptop i had to go through the process in this thread to get it working. Strange thnig is we are both on same 12.04 Ubuntu and use identical laptops. So, go figure?

Either way, if you have it working I say leave it and go and play tennis.

David

---

### Post by vwood on 2013-04-11
> **Kruxoli said:**
> 
I ran the script with my devices IP address:

root@kruxoli-ThinkPad-T60p:/home/kruxoli# brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.100
"MFC-7860DW" is already registered.
root@kruxoli-ThinkPad-T60p:/home/kruxoli#


To remove the old registration, type

```
brsaneconfig4 -r MFC-7860DW
```

and then you can try again with the correct IP.

---

### Post by brus brother on 2013-11-27
MFC 7860dw
Linux Mint 15
I got the printer to work (or so I thought) and the scanner using kumoshk's special instructions but realized today that I can't duplex print.
This duplex function works perfectly on Windows 7 installed on the same machine (separate HD) so I know it's not the printer.
Has anyone got the duplex to work?

**SOLVED: Not sure why but during initial installation, recommended driver was 7840W. When I changed it to 7860DW cups driver, duplex works as expected. **

---

### Post by brus brother on 2013-12-09
Well I spent an entire morning on the phone with Brother Linux support who confirmed on his machine(s) that the Scan-to button on the MFC7860dw machine scans only the first page from the automatic document feeder. If anyone has had any success, I would appreciate some direction. I am using Mint 15.
The rep said he was kicking it up the ladder to see if a revised brscan-skey tool might be created. I will post back with any updates.

---

### Post by brus brother on 2014-08-20
rickm1945,
Got email notification of your post but I don't see it here.
Anyway, there is a step that is left out of the instructions that I found after much searching. 

Open terminal as su (super user) and insert command line as follows EXCEPT change the ip address to 
whatever your Brother printer ip address is 

brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=192.168.1.185

NOW CHECK IN SIMPLE SCAN TO SEE IF THE SCANNER IS RECOGNIZED
Install X Sane as well. Scanner should show up there as well.
If you need instructions for making the scan key on the machine functional, that is yet another step that I solved by following:
[http://griechenzicken.blogspot.com/2011/02/functionalizing-scan-to-key-of-brother.html#more](http://griechenzicken.blogspot.com/2011/02/functionalizing-scan-to-key-of-brother.html#more)
and
[http://griechenzicken.blogspot.com/2011/03/using-adf-via-scan-to-keys-of-brother.html](http://griechenzicken.blogspot.com/2011/03/using-adf-via-scan-to-keys-of-brother.html)
although I never got it to combine front and back pages...

---

### Post by rickm1945 on 2014-08-21
I have all the drivers installed and the pkg from Brother installed and ran checks to verify install and Scanner is registered.
I pluged in the usb connector in and tried to see if XSane would connect to scanner. It didn't and I got this error message for the wireless:
```
Failed to open device
'brother4.net1;dev0';
Invalid Argument
```

With usb plugged in it did recognize the Scanner. I did not try to connect with usb

when you installed the driver pkg printer which included the scanner driver did you install them with the USB connector plugged in?

---

### Post by brus brother on 2014-08-21
> **rickm1945 said:**
> I have all the drivers installed and the pkg from Brother installed and ran checks to verify install and Scanner is registered.
I pluged in the usb connector in and tried to see if XSane would connect to scanner. It didn't and I got this error message for the wireless:
```
Failed to open device
'brother4.net1;dev0';
Invalid Argument
```

With usb plugged in it did recognize the Scanner. I did not try to connect with usb

when you installed the driver pkg printer which included the scanner driver did you install them with the USB connector plugged in?
Are you in fact trying to setup a MFC7860?
I followed these instructions for my MFC7860DW and even recently used this exact method by modifying the name for a 8710DW and it worked like a charm.
This was done without USB only using the ip adress as outlined below.

Did you follow this step:
Open terminal as su (super user) and insert command line as follows EXCEPT [COLOR="#FF0000"]change the ip address[/COLOR] to
whatever your Brother printer ip address is
brsaneconfig4 -a name=MFC-7860DW model=MFC-7860DW ip=[COLOR="#FF0000"]192.168.1.185[/COLOR]
You should be able to find your printer's ip address by following the sequence on the machine keypad:
Menu
5. Print Reports OK
5. User Settings OK
Start
The ip address is listed under WLAN Enable

---

