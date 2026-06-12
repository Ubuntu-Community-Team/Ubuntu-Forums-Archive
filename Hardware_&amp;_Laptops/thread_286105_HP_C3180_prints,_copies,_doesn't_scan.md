---
title: "HP C3180 prints, copies, doesn't scan"
date: 2006-10-27
forum: Hardware &amp; Laptops
---

### Post by cyberb0b on 2006-10-27
So I got a new HP C3180 printer, scanner, copier, built-in memory card reader thingy.  I plugged it into my Dapper Drake Desktop and:

1) Printing works great
2) When a memory card is inserted it pops up on the desktop
3) Launched xsane to scan, and it didn't work

Does anyone know what I need to do to get the scanner recognized?  I know xsane works because I used it on this machine with other scanners.  It still recognizes my TV tuner as an input, and I can "scan" in a picture from the tuner.  But not from the C3180.

Thanks

---

### Post by klytu on 2006-10-28
> **cyberb0b said:**
> So I got a new HP C3180 printer, scanner, copier, built-in memory card reader thingy.  I plugged it into my Dapper Drake Desktop and:

1) Printing works great
2) When a memory card is inserted it pops up on the desktop
3) Launched xsane to scan, and it didn't work

Does anyone know what I need to do to get the scanner recognized?  I know xsane works because I used it on this machine with other scanners.  It still recognizes my TV tuner as an input, and I can "scan" in a picture from the tuner.  But not from the C3180.

Thanks

I recently purchased the HP C3180 as well, but I have it connected to a Windows box so I haven't tried scanning directly with Ubuntu. I can also print perfectly via the network from Ubuntu to the C3180. I tried scanning after booting the Windows box with a Knoppix 3.7 live CD, but I couldn't get scanning working with xsane. With Knoppix running:

```
scanimage -L
```

didn't detect the scanner, but

```
sane-find-scanner
```

yielded: 

> found USB scanner (vendor=0x03f0 [HP], product=0x5611, [Photosmart C3100 Series]) at libusb:001:004

which is very encouraging.

The sane scanning backend is supposedly included in HPLIP. According to the [HPLIP website]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html") the C3100 series is supported for both scanning and printing with HPLIP version 1.6.6, but I think the version of HPLIP used in Dapper is 0.9.7, which might not yet support the C3100 series for scanning. 

I have a suggestion. Try this:

```
sudo gedit /etc/sane.d/dll.conf
```

Look for a line containing hpaio. If it already exists and is uncommented, just close the file and skip to the last paragraph of this post. If it is commented (#hpaio), uncomment it by removing the # and save the file. If a line with hpaio doesn't exist, add hpaio to the end of the file and save the file. Then do:

```
sudo /etc/init.d/hplip restart
```

Confirm you can still print, then try scanning again. 

If scanning still doesn't work (I suspect it won't), try downloading and installing the latest version of HPLIP from the HPLIP website in the link above, edit your /etc/sane.d/dll.conf file again as above to confirm it contains hpaio, and try scanning. Please post back whether or not this helps. If you can't get it working, when I get time I'll roll up my sleeves, disconnect my C3180 from my Windows box, connect it to my Linux box and try it to get it working myself!

---

### Post by cyberb0b on 2006-10-29
Here is what happened with my Dapper machine:

```
sane-find-scanner
```

found the scanner.

```
sudo gedit /etc/sane.d/dll.conf
```

This file does not have hpaio in it at all.  Which probably means the version of hplip in Dapper does not have the hpaio driver.  I tried adding hpaio to the end of the list and did:

```
sudo /etc/init.d/hplip restart
```

Printing and everything still works.  No scanning.  If I have time later I'll try getting a newer version of HPLIP that contains the hpaio driver.

---

### Post by cyberb0b on 2006-10-29
Woo I can scan! Here is what I did in Dapper:

1) Download hplip 1.6.10 tar.gz from the bottom of [this page]("http://hplip.sourceforge.net/downloads.html").
2) Extract and run ./configure, which of course has many dependencies
3) In synaptics, install lsb (Linux standard base), libsnmp9, python2.4-dev, and a few others in order to get ./configure to not get errors
4) make
5) sudo make install
6) sudo gedit /etc/sane.d/dll.conf and make sure hpaio is in there
7) restart

And whammy! Scanning works.  Thanks klytu for your help.

---

### Post by klytu on 2006-10-29
> **cyberb0b said:**
> Woo I can scan! Here is what I did in Dapper:

1) Download hplip 1.6.10 tar.gz from the bottom of [this page]("http://hplip.sourceforge.net/downloads.html").
2) Extract and run ./configure, which of course has many dependencies
3) In synaptics, install lsb (Linux standard base), libsnmp9, python2.4-dev, and a few others in order to get ./configure to not get errors
4) make
5) sudo make install
6) sudo gedit /etc/sane.d/dll.conf and make sure hpaio is in there
7) restart

And whammy! Scanning works.  Thanks klytu for your help.

Excellent!! Glad my suggestion was helpful to you. Thanks for posting back your results; this will probably be useful to many folks - me especially since I have the same model!

---

### Post by petersjm on 2006-12-16
Sweet Hallelujah! Thank you, thank you, thank you! I've been struggling to get scanning working on the C3180. I tried what Klytu suggested (and what Cyberb0b said worked for him). I opened the dll.conf and hpaio was already there (I had already installed 1.6.10), and it wasn't even commented out. So I just did a restart and now it works! I just hope I don't have to restart it every time I switch my PC on! :D
Thanks again to you both! This was a great help!

---

### Post by yigal.weinstein on 2007-01-25
[COLOR="Red"]_**EDGY USERS - READ FIRST - DO NOT DO ABOVE**_[/COLOR]


Not to rain on the success of those above me but Ubuntu comes with HPLIP installed by default and is therefore with only a little prodding ready to scan and print with the HP Photosmart C3180.  I know because it took 20 minutes for me to set up the hardware, set up the software, scan in an image and print it for the first time.  

1.  run hp-setup in a terminal:
```
sudo hp-setup
```
go through the discovery process answer all of the questions with the defaults.

2. display and setup HPLIP in System ---> Preferences ---> HPLIP Toolbox:
To use HPLIP in a Default Ubuntu installation go to your gnome-panel System ---> Preferences ---> Menu Layout.  Click on the System Menu Items and select the subcategory Preferences.
If confused look at the 1st picture.

My HPLIP has a check mark next to it but by default it is not check marked.  Please put a check mark next to it to see it in System ---> Preferences.

The package python-qt3 needs to be installed for HPLIP Toolbox to be used.  So using a terminal
```
aptitude install python-qt3
```
or Synaptic - your choice to install this package.

3. Open up HPLIP Toolbox it is a nice, a little ugly, but nice interface for printing and scanning.  You should be ready for printing and scanning.

---

### Post by scrooge_74 on 2007-02-07
I can say that  the instructions given by cyberb0b do work beautiful, I now have a working printer scanner

---

### Post by yigal.weinstein on 2007-02-07
scrooge_74,

My only interest was to express that by default and using no sources other than the official Edgy repositories the C3180 printer works for printing, copying, and scanning.

If you want to build stuff from scratch then I think this is truly up to you, but you don't have to, to make your printer work.

---

### Post by scrooge_74 on 2007-02-07
> **yigal.weinstein said:**
> scrooge_74,

My only interest was to express that by default and using no sources other than the official Edgy repositories the C3180 printer works for printing, copying, and scanning.

If you want to build stuff from scratch then I think this is truly up to you, but you don't have to, to make your printer work.

My dear yigal:

if you notice on the info of those having to compile the drivers you will notice that we are using Dapper and not Edgy.   Since we are less fortunate at this time we need to compile drivers for this device.

In reallity is not very hard once you follow the instructions and are not affraid of using apt-get  config and make
:guitar:

---

### Post by helliewm on 2007-02-22
These instructions work brilliant for Edgy first time. Brilliant thank you. I have just bought myself the HP C3180.

Thanks :) :) 

Helen

---

### Post by klytu on 2007-04-22
Installed Fiesty that was released a couple of days ago on a spare hard drive this weekend for testing purposes. HP C3180 works for both printing and scanning for me right ¨out-of-the-box¨.

---

### Post by rlutker on 2007-05-29
Thanks for the help,
I'm running ubuntu dapper and I am able to scan and print with the c3180.  Thank goodness hp puts out drivers for their products.  I will never buy a Lexmark again.  I would like to note that I was not able to scan with their newest driver.  If you using a photosmart c3180 use the hplip-1.6.10. I found the above replies by Cyberb0b and yigal.Weinstein both very helpful.

---

### Post by TheWizzard on 2007-07-30
> **klytu said:**
> I recently purchased the HP C3180 as well, but I have it connected to a Windows box so I haven't tried scanning directly with Ubuntu. I can also print perfectly via the network from Ubuntu to the C3180. I tried scanning after booting the Windows box with a Knoppix 3.7 live CD, but I couldn't get scanning working with xsane. With Knoppix running:

```
scanimage -L
```

didn't detect the scanner, but

```
sane-find-scanner
```

yielded: 



which is very encouraging.

The sane scanning backend is supposedly included in HPLIP. According to the [HPLIP website]("http://hplip.sourceforge.net/supported_devices/inkjet_aio.html") the C3100 series is supported for both scanning and printing with HPLIP version 1.6.6, but I think the version of HPLIP used in Dapper is 0.9.7, which might not yet support the C3100 series for scanning. 

I have a suggestion. Try this:

```
sudo gedit /etc/sane.d/dll.conf
```

Look for a line containing hpaio. If it already exists and is uncommented, just close the file and skip to the last paragraph of this post. If it is commented (#hpaio), uncomment it by removing the # and save the file. If a line with hpaio doesn't exist, add hpaio to the end of the file and save the file. Then do:

```
sudo /etc/init.d/hplip restart
```

Confirm you can still print, then try scanning again. 

If scanning still doesn't work (I suspect it won't), try downloading and installing the latest version of HPLIP from the HPLIP website in the link above, edit your /etc/sane.d/dll.conf file again as above to confirm it contains hpaio, and try scanning. Please post back whether or not this helps. If you can't get it working, when I get time I'll roll up my sleeves, disconnect my C3180 from my Windows box, connect it to my Linux box and try it to get it working myself!

updating the software worked like a charm. thanks!

---

### Post by HumbleGod on 2007-11-29
Just here to confirm that with Feisty, you can choose the HPLIP driver (it gave me two C3180 driver recommendations, I chose the one that had HPLIP listed), and it Just Works--printing, scanning, everything. Gotta love this printer!

---

### Post by El Viejo Lobo on 2008-03-23
> **yigal.weinstein said:**
> [COLOR="Red"]_**EDGY USERS - READ FIRST - DO NOT DO ABOVE**_[/COLOR]


Not to rain on the success of those above me but Ubuntu comes with HPLIP installed by default and is therefore with only a little prodding ready to scan and print with the HP Photosmart C3180.  I know because it took 20 minutes for me to set up the hardware, set up the software, scan in an image and print it for the first time.  

1.  run hp-setup in a terminal:
```
sudo hp-setup
```
go through the discovery process answer all of the questions with the defaults.

2. display and setup HPLIP in System ---> Preferences ---> HPLIP Toolbox:
To use HPLIP in a Default Ubuntu installation go to your gnome-panel System ---> Preferences ---> Menu Layout.  Click on the System Menu Items and select the subcategory Preferences.
If confused look at the 1st picture.

My HPLIP has a check mark next to it but by default it is not check marked.  Please put a check mark next to it to see it in System ---> Preferences.

The package python-qt3 needs to be installed for HPLIP Toolbox to be used.  So using a terminal
```
aptitude install python-qt3
```
or Synaptic - your choice to install this package.

3. Open up HPLIP Toolbox it is a nice, a little ugly, but nice interface for printing and scanning.  You should be ready for printing and scanning.

It dose not work for  me with Gusty Gibbon. What I have to do? Thanks.

---

### Post by 11hjpphty76lkjj on 2008-03-24
El Viejo Lobo,

Can you be specific as to what is the problem you are encountering?

Thanks!

Aaron

---

### Post by El Viejo Lobo on 2008-03-24
Dear kalosaurusrex

I can not make hplip 2.8.2 install it self. I did it in the past (feisty) what I am missing to make it work again?

---

### Post by 11hjpphty76lkjj on 2008-03-24
What's the error you are having when you install hplip?

Ubuntu is well supported.  You can follow the directions here;

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

A

---

### Post by klytu on 2008-03-24
> **El Viejo Lobo said:**
> Dear kalosaurusrex

I can not make hplip 2.8.2 install it self. I did it in the past (feisty) what I am missing to make it work again?

FYI, this model works for me from the Gutsy Live CD without installing any additional drivers. Works for both printing and scanning. Is there a specific reason you that want or need to install hplip 2.8.2?

EDIT: OK. I installed HPLIP using Add/Remove from the Applications menu of the Gutsy Live CD and I understand why you would like to install it. It has a lot of nice features and ways to use the device in a simple GUI. As kalosaurusrex asked, please do post what error messages you get and we'll try to help. But printing and scanning should still work fine for you even without HPLIP.

---

### Post by El Viejo Lobo on 2008-03-25
I really do not know way this time it does not work. attached are the screenshot of the errors I got.
thanks.:(

---

