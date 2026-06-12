---
title: "[SOLVED] How to get your Epson CX8400 working"
date: 2008-06-10
forum: Hardware
---

### Post by EtniesBMX on 2008-06-10
Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800. 

To make scanning work, go to menu>accesories>terminal, and type:
```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner

---

### Post by docbillias on 2008-07-08
Works fine for scanning with EPSON DX 8450 too. I have some problems using XSane, because it gets stuck or makes partial scans, but GIMP image editor is perfect and fast.

P.S. I was about to start screaming, I couldn't get the scanner work. You saved my nervous system

---

### Post by Hollihock on 2008-08-13
> **EtniesBMX said:**
> Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800. 

To make scanning work, go to menu>accesories>terminal, and type:
```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner
Thank you!  This worked for me.

---

### Post by rp3 on 2008-08-19
> **EtniesBMX said:**
> Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800. 

To make scanning work, go to menu>accesories>terminal, and type:
```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner

For the life of me I can't make this printer work.  I tried the above and nothing happens (at least it doesn't spit out paper :)...

I tried to change the driver to the CX7800 but then the Device URI was wrong, so I copied the "usb://EPSON/Stylus%20CX8400" from the cx8400 as it creates this when that printer is turned on?


I am very confused, going to reboot and see what happens.. Right now my mom can't print on this machine and she is ready to go back to WINBLOWS so I am doing my best to make this work... Just interesting this is so much work when checking the linixprinting.org it says this printer "Mostly Works..."  hmmm

Let you know...

Ok maybe the issue is I installed the PIPSLITE stuff, how do I un-install a .deb package?  So I can start fresh, as I installed ISCAN as well in an attempt to make this all work?

---

### Post by rp3 on 2008-08-19
> **rp3 said:**
> For the life of me I can't make this printer work.  I tried the above and nothing happens (at least it doesn't spit out paper :)...

I tried to change the driver to the CX7800 but then the Device URI was wrong, so I copied the "usb://EPSON/Stylus%20CX8400" from the cx8400 as it creates this when that printer is turned on?


I am very confused, going to reboot and see what happens.. Right now my mom can't print on this machine and she is ready to go back to WINBLOWS so I am doing my best to make this work... Just interesting this is so much work when checking the linixprinting.org it says this printer "Mostly Works..."  hmmm

Let you know...

Ok maybe the issue is I installed the PIPSLITE stuff, how do I un-install a .deb package?  So I can start fresh, as I installed ISCAN as well in an attempt to make this all work?

Ok I removed the PIPSLITE and ISCAN packages and was able to get the scanner to work just fine via the above method.  But now I get a different error when trying to make the printer work by just changing the driver to the CX7800.  At least I am making some headway...

What should the device URI be?  IT comes up as something with the LPT port and that doesnt' work since it is a UBS printer, but then I tried to let it create it self (when you boot it up) and then just changed the driver and it still didn't work.

Stumped here...but I won't give up.  Not yet anyways...

---

### Post by Ethyrdude on 2008-08-23
Yep, works dandy for me too.  Had a hard time trying to find the pipslite-cups file that was supposed to be the fix for this printer, finally gave up and just used the cx7800 driver, don't know if it will scan or not but if I need to scan and I can't, I 'll just use the software built into the printer.

The printer I'm using is plugged into a Windows machine, (both the computer and printer are my son's) and what I did before getting the printer to work was transfer whatever I needed printed into his shared docs folder and have him print it.  Worked for me, I suppose the other work around would have been to try wine, I don't use it for anything else, maybe it will work for printing.  Fortunately, I got the printer to work by using the cx7800 driver (yes, I think this is retarded, why not just give us working drivers for the right printers!!!!) but I've always had this issue with using printers with cups, it's rare where you can actually get the right driver to work with the right printer.

Now this is a case of where we can and should complain to the printer manufacturers, or perhaps the problem is with cups?  In my case, the printer is attached to a windows computer and I had a work-around but others may not have that luxury if their printers don't work and end up with garbage that isn't even worth a package of cheap paper.

---

### Post by mlsquad on 2008-09-01
> **EtniesBMX said:**
> Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800. 

To make scanning work, go to menu>accesories>terminal, and type:
```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner

Thanks.  I just bought this printer/scanner because I found it on a sale ($70) and didn't have the opportunity to check online for compatibility first.  I started getting worried when I got the endless paper print-out and XSane saying it could not find a scanner.  A Google search of *Ubuntu CX8400 scanner* came up with this thread which fixed everything.  Great post.

---

### Post by LeAnnS on 2008-09-01
I am very new to this OS.  I purchased the Everex gpc2 for my son.  It says it's using Ubuntu 7.10.  I'm trying to get my Epson Stylus CX8400 printer to work.  I plugged it in and connected the usb cord, but it will not print.  All of the posts I've found say to go to Menu>System>Administration>Printing, however I can't even find this path.  When I go to the "G", I see Applications/Administration, but no printing information.  The only options there are Hardware Information, Install, Synaptic Package Manager and Update Manager.

This pc did not come with any type of manual.  Where can I find beginner info on this?  I thought this would be a decent, cheap alternative for my son, however now I'm starting to doubt my decision.

Thanks.

---

### Post by mlsquad on 2008-09-02
> **LeAnnS said:**
> I am very new to this OS.  I purchased the Everex gpc2 for my son.  It says it's using Ubuntu 7.10.  I'm trying to get my Epson Stylus CX8400 printer to work.  I plugged it in and connected the usb cord, but it will not print.  All of the posts I've found say to go to Menu>System>Administration>Printing, however I can't even find this path.  When I go to the "G", I see Applications/Administration, but no printing information.  The only options there are Hardware Information, Install, Synaptic Package Manager and Update Manager.

This pc did not come with any type of manual.  Where can I find beginner info on this?  I thought this would be a decent, cheap alternative for my son, however now I'm starting to doubt my decision.

Thanks.The version of Ubuntu that comes with that Everex uses a different windows manager than the normal Ubuntu that most people are using.  I am downloading the version, named gOS, that comes with Everx in the hopes that I can help you.
If you would like to grab the stock Ubuntu than you can grab it at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  You will need a blank CD to burn the download to.

---

### Post by PrestonFrom on 2008-09-06
I've got the printer working now (I think, I just ran out of ink after it printed a test page).  But the scanner is not working. This is what happened in the terminal...

preston@preston-laptop:~$ sudo apt-get install libsane-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libsane-extra
preston@preston-laptop:~$ 

Umm...so, where's the package libsane-extra?  I'm sure this is an obvious question, but I just installed Ubuntu yesterday.  It's great so far! :)

---

### Post by mlsquad on 2008-09-06
> **PrestonFrom said:**
> I've got the printer working now (I think, I just ran out of ink after it printed a test page).  But the scanner is not working. This is what happened in the terminal...

preston@preston-laptop:~$ sudo apt-get install libsane-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libsane-extra
preston@preston-laptop:~$ 

Umm...so, where's the package libsane-extra?  I'm sure this is an obvious question, but I just installed Ubuntu yesterday.  It's great so far! :)
You need to install libsane-extra**s**  Note the s at the end.

---

### Post by Gun_Smoke on 2008-09-06
Maybe I'm getting bad GUI here or something.. But I can't manually select the make and model.. I automatically picks up on the 8400 being connected, I can choose a different driver.  Even when choosing the 7800 as suggested I still can't get it to print.

---

### Post by DemonSpectre on 2008-10-08
Just wanted to confirm that this combination of steps also worked for me.  Both scanning (via XSane) and printing are working great on my CX8400.

Many thanks for the article!

---

### Post by theozzlives on 2008-10-31
> **EtniesBMX said:**
> Default drivers for my Epson CX8400 working weren't working -- my printer kept spitting out blank pages. To make printing work, simply use the driver for the Epson CX7800. That's it.

Go to Menu>System>Administration>Printing

Click "Make and Model" and choose the Epson CX7800. 

To make scanning work, go to menu>accesories>terminal, and type:
```
sudo apt-get install libsane-extra
```

Scanning and printing should now work for you. To scan, you can use the program XSane found here: Menu>Graphics>XSane Image Scanner

ununtu 8.10 returnes E: Couldn't find package libsane-extra

---

### Post by mlsquad on 2008-10-31
> **theozzlives said:**
> ununtu 8.10 returnes E: Couldn't find package libsane-extra

I'm not sure if this will work, but try libsane-extras-dev  It appears that Intrepid no longer has libsane-extras.

---

### Post by theozzlives on 2008-11-03
> **mlsquad said:**
> I'm not sure if this will work, but try libsane-extras-dev  It appears that Intrepid no longer has libsane-extras.

didn't work, I have another scanner could that be it?

---

### Post by mlsquad on 2008-11-03
> **theozzlives said:**
> didn't work, I have another scanner could that be it?Go to System->Administration->Software Sources.  In the "Ubuntu Software" tab make sure the first four options are checked.  Close out and choose to reload.  libsane-extras should now exist.
[FONT="Fixedsys"]sudo aptitude install libsane-extras[/FONT]

---

### Post by theozzlives on 2008-11-03
All checked, still not working!

---

### Post by theozzlives on 2008-11-04
I checked Synaptic, and libsane-extra is already installed yet Xsane doesn't recognize my CX8400 scanner

---

### Post by theozzlives on 2008-11-05
Get Ubuntu 8.10 the printer works great, I just can't get it to scan.

---

### Post by undegaussable on 2009-02-03
I can't get the scanner working in 8.10 either -- and I have libsane-extras installed.  Any ideas?

---

### Post by mlsquad on 2009-02-03
> **undegaussable said:**
> I can't get the scanner working in 8.10 either -- and I have libsane-extras installed.  Any ideas?What happens when you try to scan?  I can scan with a clean install of 8.10.

---

### Post by chosenbeans on 2009-03-27
Yeah I got a clean install of 8.10 with the above drivers. I am no noob at Linux when it comes to most things although this is a friends printer. I might know something about setting up printers but I don't own one so I don't know very much. Xsane won't pick up any devices. Printing is fine although the scanner still fails to be recognized by the system.  

Figured I would post here to give this thread some action again.

Thanks a lot guys :-)

---

### Post by mlsquad on 2009-03-28
I wish I knew how to push you in the right direction, but on 8.10 scanning just worked for me with this printer with no configuration on my side.

---

### Post by nyk on 2009-04-08
[http://ubuntuforums.org/showthread.php?t=568268&page=3](http://ubuntuforums.org/showthread.php?t=568268&page=3)

ewr2san's post worked wonders for me.

---

