---
title: "How to: Epson Sylus T21 printer Installation with avasys pips"
date: 2009-08-05
forum: Hardware
---

### Post by ClarkePeters on 2009-08-05
WARNING: Ubuntu 8.04 / 8.10. The pips/AVASYS method seems to have a broken pips package, but the printer works perfectly. However, if you do an  update or other install with Synaptic, it will try to fix whatever is broken and this will break your printer driver and your printer will no longer work. Be sure to uninstall your driver before doing any updates or installs with Synaptic, then reinstall. See post #2 for more details. You may also want to check out post #4 for an alternative driver.




****** Original Instructions begin here ******

We're going to use something called pips from AVASYS

This seems like a lot of steps, but its not, because I even included navigating the AVASYS website in the instructions which was probably not necessary. Basically, after downloading the file, the actual installation instructions begin at 
step 7.

1.Go to AVASYS website at:
[http://avasys.jp/hp/menu000000900/hpg000000859.htm](http://avasys.jp/hp/menu000000900/hpg000000859.htm)

2. On the left, go to the menu "Linux Drivers: download"

3. Don't read the page. On the left in the menu go to "Download: inkjet"

4. Don't read the first part at the top, just scroll down till you get to the small bold heading:
    Form for download
    -- then select Epson Stylus S21/T21/T24/T27

5.  Skip the pdf stuff and go to the questionnaire, answer the questions; 

about your system (e.g. distribution: Ubuntu  version: 8.04)

for Connection environment, if you are not sure, then you are probably not on a network so just choose: Print with local printer 

for Location for the product choose: Individual (documents) or Individual (graphic/Image) --I did graphic/image

>> next >>

6. You are on the DOWNLOAD INKJET PRINTER page.
Scroll Down to "Download Epson.... for Ubuntu"

Look down to "Installation File" and download it (you don't want the source file below it)   

(There is also a user manual below called UsersManual.en.txt, you may want to take a look at that but you probably won't need to, if you are a non-techie it might confuse you.)

when the download has finished, open the terminal (that little black computer screen icon under accessories that people use for typing in direct commands to Linux)

note: pay attention to where the file downloads. You can check by going to the download box that pops-up when downloading with FireFox, right click the file and choose "open containing folder". Now you know where your file is.


7. Make sure the printer is off and disconnected. If you have already tried unsuccessfully to get your printer to work, then go to system-->administration-->printing  and delete any profiles of your printer that may already exist (they obviously don't work, so don't be afraid to delete them).

8.a. In terminal, change to the directory of your downloaded pips file, something like:
```
cd /home/myComputer/Desktop
``` or maybe just:

```
cd /home/myComputer
```

8.b. follow the steps below. Use the file name you downloaded where appropriate (for this example it is pips-ss21-ubuntu8.04-3.7.0-CG.tgz).

```
$ sudo bash
```
  
```
# tar xfz pips-ss21-ubuntu8.04-3.7.0-CG.tgz
```

next, replace the "tar xfz" in the previous command with "./" and change the extension from .tgz to .install like the example below.

```
# ./pips-ss21-ubuntu8.04-3.7.0-CG.install
```
the computer will uncompress the file and then ask: 
```
Installation will start.
Do you want to continue? (Yes/No): y

```
type y for yes

at this point a lot of things print, don't worry about it. The last thing you'll see is
```
<Enter>
```
hit enter.

Pips is finished.  
Close your terminal. 

9. Plug in and turn on your printer.

At this point the computer should automatically find and add the printer to your system (a yellow box pops up, says something like:"Epson Stylus T21 printer added"). 

10, Go to system-->administration-->printing.  Click on the printer profile and print a test page and set as default if you like.

---

### Post by ClarkePeters on 2009-08-29
WARNING:

After installation, I got a warning from Synaptic saying I needed to do a partial update or fix broken packages or something.

DON'T DO IT!  If you do, you'll lose your printer and won't be able to reinstall it.



If you want to do an upgrade or install other applications with Synaptic package manager, _uninstall your printer first_, then do your upgrade/install, then re-install your printer.

How to uninstall:
the "ss21" below is the name of your printer, if yours is different, e.g. st21, then replace the ss21 with st21. 

```
/usr/local/EPAva/printer/ss21/uninstall-ss21.sh
```

IF you are not sure what your printer name is, no problem, Use Nautilus and go to the /usr/local/EPAva/printer folder and see what the folder name is--that is the name of your printer. 
OR You can use the terminal, like so:

```
me@me-laptop:~$ [COLOR="Blue"]cd /usr/local/EPAva/printer[/COLOR]
me@me-laptop:/usr/local/EPAva/printer$ [COLOR="Blue"]ls[/COLOR]
[COLOR="RoyalBlue"]ss21 [/COLOR]

```

---

### Post by geertlpa on 2009-11-02
You might be interested to know that this method worked when I installed in Ubuntu 9.40 but after  upgraded, actually new install, to Ubuntu 9.10 Karmic Koala and tried the same procedure it did not work.

The install part takes part as you explain but Once the printer is switched on Ubuntu launches its own procedure to install the printer and it does not recognize the pips install. It even chose the driver for another Epson printer. It works but it is a bit strange that there is always that there are that many differences between different Ubuntu versions.

So an update for Installing an Epson Stylus T21 in 9.10 might be in order.

---

### Post by ClarkePeters on 2009-11-30
Because of the reasons in post #2 above, I found that it was much easier to start again from scratch since I tend to do a LOT of updates and installs.

I uninstalled pips per #2 post instructions, then plugged in my printer and let Ubuntu automatically detect it. Then I added the Epson Stylus C64 driver which so far seems compatible (slow as christmas and not quite as sharp, the colors are off a bit with a hint of yellowish tint -- but for my simple needs, it'll do). 

I had tried many other drivers previous to this (about 16 in all out of the hundreds listed)  but finally came across the C64 quite by accident in another post.


Except for the inconvenience in post #2, the pips driver itself worked flawlessly.

I think we need a wiki dedicated to computer printer drivers compatibility and make it a sticky--would save users a lot of head-aches.

---

### Post by endm on 2009-12-13
I'm using ubuntu 9.10. Unfortunely I installed the pips-ss21, now my Synaptics says I have a broken package but I can't remove it.

The message is E: pips-ss21: el subproceso script pre-removal instalado devolvió el código de salida de error 1

What can I do to remove it? Please Help...

---

### Post by Dmtiriy Isaev on 2009-12-24
Thank you very much for these instructions!

> **ClarkePeters said:**
> WARNING:

After installation, I got a warning from Synaptic saying I needed to do a partial update or fix broken packages or something.

DON'T DO IT!  If you do, you'll lose your printer and won't be able to reinstall it.

If you want to do an upgrade or install other applications with Synaptic package manager, _uninstall your printer first_, then do your upgrade/install, then re-install your printer.

Well, I've got this warning after installing pips-ss21 (Stylus T27) using kernel 2.6.24 and 2.6.28. I didn't like this way of installing/uninstalling and (with help of [runtu forum]("http://forum.runtu.org/index.php?topic=6310")) tried to find the decision.

First, "**sudo dpkg --configure -a**":

```
dpkg: &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1087;&#1086;&#1079;&#1074;&#1086;&#1083;&#1103;&#1102;&#1090; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1080;&#1090;&#1100; &#1087;&#1072;&#1082;&#1077;&#1090; pips-ss21:
 pips-ss21 &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090; &#1086;&#1090; pips-debian4.0 (>= 3.7.0), &#1086;&#1076;&#1085;&#1072;&#1082;&#1086;:
  &#1055;&#1072;&#1082;&#1077;&#1090; pips-debian4.0 &#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;.
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; pips-ss21 (--configure):
 &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1099; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081; -- &#1086;&#1089;&#1090;&#1072;&#1074;&#1083;&#1103;&#1077;&#1084; &#1085;&#1077; &#1085;&#1072;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1085;&#1099;&#1084;
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 pips-ss21
```

(sorry, it's in Russian). Shortly, it means: "**pips-ss21 depends on pips-debian4.0, which is not installed**".

But why debian? Hey, I'm using Ubuntu!.. Well, ok, debian. I've removed the printer and three pips-* modules (i.e. pips-ss21, pips-common and something like pips-ubuntu8.04). Then downloaded and installed pips-ss21-debian4.0-3.7.0-CG.tgz [from the same site]("http://avasys.jp/eng/linux_driver/download/"). And it works! No warnings, no problems with printing, no problems with Synaptic. Great! Thank everybody for this forum! :)

---

