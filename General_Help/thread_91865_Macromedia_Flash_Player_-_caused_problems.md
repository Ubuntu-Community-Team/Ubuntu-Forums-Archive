---
title: "Macromedia Flash Player - caused problems"
date: 2005-11-18
forum: General Help
---

### Post by Sonishka on 2005-11-18
UBUNTU 5.10 had been recently installed, but there were some problems with flash on the websites, so I had just clicked on the window in order to install Macromedia Flash Player. It was installed properly and installation window said that the installation process had finished. BUT... Now instead of loading the page with the flah in it, the Firefox window is closing, when the flash is observed. What should I do? I am not proficient in programming, I am just a user.. THX for any help..:(

---

### Post by lee575 on 2005-11-18
unninstall it is not very gdgd trust me 

[http://207.44.176.64/~scott108/click.php?user=lee%20a](http://207.44.176.64/~scott108/click.php?user=lee%20a)

this game is new and you dont need macromedia flash

this will also help me in the game  i cannot help this

---

### Post by Sonishka on 2005-11-18
So, what should I do? reinstall Ubuntu ?

---

### Post by lee575 on 2005-11-18
yes 

have you one the game yet send to frieds it is gdgd

[http://207.44.176.64/~scott108/click.php?user=lee%20a](http://207.44.176.64/~scott108/click.php?user=lee%20a)

---

### Post by Sonishka on 2005-11-18
tnx

---

### Post by lee575 on 2005-11-18
have you gone on the game send to your friends it is gdgd

[http://207.44.176.64/~scott108/click.php?user=lee%20a](http://207.44.176.64/~scott108/click.php?user=lee%20a)

---

### Post by Sonishka on 2005-11-18
I am not playing games.. have no time.. but i will recommend to someone who does

---

### Post by lee575 on 2005-11-18
send to many ppl

[http://207.44.176.64/~scott108/click.php?user=lee%20a](http://207.44.176.64/~scott108/click.php?user=lee%20a)

---

### Post by PsychoTrauma on 2005-11-18
Lee575 plese don't spam poeple with links to games.

Sonishka, open a terminal and type:
```
sudo rm /usr/lib/mozilla-firefox/plugins/flashplayer.xpt
```
```
sudo rm /usr/lib/mozilla-firefox/plugins/libflashplayer.so
```
That will remove the flash plugin from firefox.

open firefox and go to [http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.macromedia.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Download the install_flash_player_7_linux.tar.gz file.

Open a terminal and cd to the directory the file was saved to then do:
```
tar -zxvf install_flash_player_7_linux.tar.gz
```
```
cd install_flash_player_7_linux
```
```
sudo ./flashplayer-installer
```

follow the prompts and when it asks you for the firefox directory use:

```
/usr/lib/mozilla-firefox
```

flash should then be installed, you can test it by browsing the flash website.

---

### Post by Sonishka on 2005-11-18
Tnx A Lot

---

### Post by pxgray on 2005-11-18
If that does not work, make sure that you are not using composite rendering in X.  I doubt that you are, since you have to go through some pretty heavy steps to get it enabled, but if you are it causes the exact symptoms that you are talking about.  Also, check out this thread for other possible fixes:

[http://www.ubuntuforums.org/showthread.php?t=89827](http://www.ubuntuforums.org/showthread.php?t=89827)

Hope everything works out for you.  I also had a lot of trouble with Flash, but trust me if you work hard you'll find a way to get it working.

---

### Post by jmooney on 2005-11-26
This wound up working for me:

sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc

Then comment out FIREFOX_DSP="auto" and add the line FIREFOX_DSP="none"

# which /dev/dsp wrapper to use
## FIREFOX_DSP="auto" ## The default setting
##
## This is supposed to fix the problem with Macromedia flash plugin.
FIREFOX_DSP="none" ## Set by Joseph K. Mooney on 11/25/05
## ## Confirmed working on [www.abum.com](www.abum.com)


Of course, your could just change "auto" to "none" but, whenever I modifiy a config file, I like to leave a note to myself explain what I did, when I did it, why I did it, and if it worked.

but suit yourself.

---

### Post by glavspirt on 2005-11-29
What to do if I have two alsa sound cards installed?
The "Flash" sound goes from the first one, I need that it goes from the second.
Any others programs' sounds work fine from second sound card.

---

