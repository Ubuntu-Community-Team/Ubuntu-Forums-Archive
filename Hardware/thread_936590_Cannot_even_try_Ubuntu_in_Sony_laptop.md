---
title: "Cannot even try Ubuntu in Sony laptop"
date: 2008-10-02
forum: Hardware
---

### Post by benbuleong on 2008-10-02
Hi guys,

I have recently bought a new model of Sony laptop VGN-FW130N and tried to run Ubuntu on it. To my surprise, it couldn't display the desktop -- once Ubuntu loads (there is the familiar sound), nothing shows up. The screen turns white and slowly fades into black, and then nothing happens. I am guessing that this could be due to the resolution of this new series Sony laptop (16.4" widescreen w/ a resolution of 1600x900)

Now if I cannot even see anything, how can I use or install Ubuntu ? Please advise. Thanks !

---

### Post by cariboo on 2008-10-03
Try starting in safe graphics mode, hit F4 at the menu screen and select safe graphics mode. It sounds like Ubuntu isn't detecting either your graphics adapter or display properly.

Jim

---

### Post by benbuleong on 2008-10-03
> **cariboo907 said:**
> Try starting in safe graphics mode, hit F4 at the menu screen and select safe graphics mode. It sounds like Ubuntu isn't detecting either your graphics adapter or display properly.

Jim

I tried that, but it still doesn't work. Any other ideas ?

---

### Post by Misz on 2008-12-09
I am having the same exact issue. Sony VAIO VGN-FW235J trying to run the 8.10 Live CD.

Any feedback would be greatly appreciated.

Thanks!

---

### Post by benbuleong on 2008-12-10
> **Misz said:**
> I am having the same exact issue. Sony VAIO VGN-FW235J trying to run the 8.10 Live CD.

Any feedback would be greatly appreciated.

Thanks!

Use the latest version of Ubuntu. It solves everything.

---

### Post by dale.novak on 2008-12-10
> **benbuleong said:**
> Use the latest version of Ubuntu. It solves everything.

The lastest version is 8.10.  I have a Sony VGN-FW280J and I also have this problem.  Anyone have a clue on how to get the video right?

---

### Post by Misz on 2008-12-16
I *was* able to get the 8.10 Live CD to work by using F4 to go into alternative setup & choosing graphics safe mode.  It's only 800X600 resolution but this is a start at least...

Thanks

---

### Post by Misz on 2008-12-18
On my Sony VAIO VGN-FW235J I got it working with the 8.10 install CD using the below steps:

1. At the main install menu use F4 to go into alternative setup & choose graphics safe mode & then proceed with the install.

2. Once Ubuntu is installed, download the file: [http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz](http://launchpadlibrarian.net/19868825/intel%20driver%20fix.tar.gz)

3. Once the file is downloaded, extract the Intel folder & you'll find 3 installer packages that all have the .deb extension.  Double click>install each one (for me one of them said reinstall instead of install but I reinstalled it anyway)

4. Once the packages are installed, close everything & open up a terminal window & type 'sudo nano /etc/X11/xorg.conf', find the spot that says the Driver is "vesa" & change it to say the Driver is "intel".  Save the file (ctrl+x).

5. Restart the PC & you should be able to get higher resolutions now

:KS**_BIG THANKS_**:KS to the posters of thread [http://ubuntuforums.org/showthread.php?t=996395&highlight=vaio](http://ubuntuforums.org/showthread.php?t=996395&highlight=vaio) who got it figured out on similar SONY VAIO models.

---

### Post by dale.novak on 2008-12-24
Thanks, I can verify this fix worked on my new Sony Vaio VGN-FW280J!

I am a happy camper.

---

### Post by henmam on 2009-04-09
hi, i have the same model, VGN-FW235J, i will try what Misz did. later report my results.  ;)

---

### Post by ahsanshah on 2009-04-16
Hi,

I was gonna try the steps suggested (installing in SAFE mode and then getting the drivers and changing the xorg.conf) however, when I choose SAFE mode (w LiveCD)..I see a screen where my cursor is repeated all over..I cannot decipher what is on the screen very clearly.  I have a SONY VAIO VGN-140E with a Intel Intel® GM45 Express Chipset (16.4 inches,1600 x 900 resolution)

How can I attempt this fix in thic scenario?  Also, is it possible to replicate this fix using Live CD or I have to install on the HD first?  

Pls advise.

---

### Post by ahsanshah on 2009-04-16
Hi,

I was gonna try the steps suggested (by Misz) (installing in SAFE mode and then getting the drivers and changing the xorg.conf) however, when I choose SAFE mode (w LiveCD)..I see a screen where my cursor is repeated all over..I cannot decipher what is on the screen very clearly. I have a SONY VAIO VGN-140E with a Intel Intel® GM45 Express Chipset (16.4 inches,1600 x 900 resolution)

How can I attempt this fix in thic scenario? Also, is it possible to replicate this fix using Live CD or I have to install on the HD first? 

Pls advise.

---

### Post by Daisuke_Aramaki on 2009-04-16
> **ahsanshah said:**
> Hi,

I was gonna try the steps suggested (installing in SAFE mode and then getting the drivers and changing the xorg.conf) however, when I choose SAFE mode (w LiveCD)..I see a screen where my cursor is repeated all over..I cannot decipher what is on the screen very clearly.  I have a SONY VAIO VGN-140E with a Intel Intel® GM45 Express Chipset (16.4 inches,1600 x 900 resolution)

How can I attempt this fix in thic scenario?  Also, is it possible to replicate this fix using Live CD or I have to install on the HD first?  

Pls advise.


Wait. Is this some followup thread? Why do you have to install in safe mode. Normal install should work fine. A default ubuntu install will get most of the features right. Only when you have cards like nvidia or ati, those drivers need to be installed, which can be done after the main install to change resolution and so on. But intel is supported ok by linux.

---

### Post by ahsanshah on 2009-04-16
If I try to install without SAFE mode..I get a blank greyis/white screen.  I cannot even go to command line via Cntrl-Alt-F1.  This was suppose to be connected to a thread I read with a similar issue.  Basically, I cannot get the display working w the VAIO Intel GM45 Chipset card.  Any thoughts?

---

### Post by geekygirl on 2009-04-17
It must be peculiar to that particular model - my Vaio TT with the Intel 45 chipset (4500MHD graphic chip) worked like a charm (until I decided on playing with Jaunty but thats another story..lol)

I agree - the Intel chipsets have always been very well supported by Linux, and Ubuntu - even in the days of Warty you could get it to run, there were just resolution issues but all that is more than sorted now.

Your chipset isn't getting overly hot or some other factor is it?

:(

---

