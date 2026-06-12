---
title: "How to: Install printers with avasys and pips"
date: 2009-08-05
forum: Hardware
---

### Post by ClarkePeters on 2009-08-05
I recently posted installation instructions for my Epson Stylus T21 but realized that these instructions should work for just about any printer.
If your having trouble installing printers, probably because the drivers are new or not available in the default printing setup, then try these steps below, only, change the printer name to your printer.

:: from my previous post:

[COLOR="Orange"]WARNING: this method may break your package/update manager, scroll to the bottom of this post for more details.[/COLOR]


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
Scroll Down to "Download yourPrinter.... for Ubuntu"

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
type "./" before the file name and change the extension from .tgz to .install
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


========================================
WARNING:

After installation, I got a warning saying I needed to do a partial update or something.

DON'T DO IT!  If you do, you'll lose your printer and won't be able to reinstall it.

The warning may or may not disable your package manager (not tested yet).

If you want to do an upgrade, uninstall your printer first, then do your upgrade.

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

### Post by Pablo12 on 2009-08-10
Hi,
 
I've tried this but it only adds as a generic text and will not print.  If the printer is in the list i.e. T21 with the generic ppd I can browse to the T21 ppd in /etc/cups/ppd but it will not let me add it as it always keeps the generic one.
 
If I remove the printer from the list the ppd for the T21 also disappears as well.
 
Did you get any errors when you installed as it as I got; cannot create path to uninstall-ss21.sh
 
Any ideas
 
Thanks
Pablo

---

### Post by Pablo12 on 2009-08-11
Sorry ignore my post!!
 
I was using a Dell and it has a custom version of Ubuntu on it.  Installed a full version and it worked perfectly.
 
Regards
Pablo

---

