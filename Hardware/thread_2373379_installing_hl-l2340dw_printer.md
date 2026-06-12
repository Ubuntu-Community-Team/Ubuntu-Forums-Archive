---
title: "installing hl-l2340dw printer"
date: 2017-10-05
forum: Hardware
---

### Post by seekertom on 2017-10-05
I bought this printer because it was advertised as linux compatible. I assumed that meant I could run an install program from the included dvd, but that didn't work.
Sorry, but I keep referencing my previous life in windows, and expected an exe file experience to get the printer recognized.
First, Ubuntu 17 does not list the printer in the add printer list. Following on line hints, I downloaded linux deb pkgs from brother, and an installer.

I tried to follow some web instructions, opened a terminal, entered what I was told, but did not get the final response I was expecting. here is what my terminal looked like...

```
tom@tom-pcfive-MT:~$ cd /tmp
tom@tom-pcfive-MT:/tmp$ sudo su
[sudo] password for tom: 
root@tom-pcfive-MT:/tmp# chmod +x linux-brprinter-installer*
root@tom-pcfive-MT:/tmp# ./linux-brprinter-installer*
root@tom-pcfive-MT:/tmp# ^C
root@tom-pcfive-MT:/tmp#
```

am I missing something or doing something wrong? Hope you can help.
st

Guess you can tell how unskilled I am here.
For now, I'd be happy to be put on the path to learn what I need to know about installing printers in ubuntu.
( I hooked up an old e210 printer, added it with no problems, and all went as expected, with ubuntu having it already listed. Problem was, printer so old it only got out one sheet before the crumbly feed rollers gave out. That's when I bought the new bro. )
thanks fer listnin' .

st

Got it, folks, and thanks. Reason I went astray is because I failed to recognize my downloads folder had a cap D, and of course, when I terminalized, there was an issue of unknown folder. So, Downloads and the rest worked ok.
I re-downloaded the installer, followed those instructions, but included the specific version of the file, rather than using the wildcard *****'s
thanks,
st

---

### Post by gurdenite on 2017-10-05
According to The Linux Foundation [openprinting.org website](http://www.openprinting.org/printer/Brother/Brother-HL-L2340DW) the CUPS driver for the Brother HL-2170W works, so try again with the simple GUI "Add Printer" method and select the HL-2170W from the list.

If there's no joy from that, there's some simpler terminal based instructions [here](https://sites.google.com/site/easylinuxtipsproject/15) which may be helpful.

---

### Post by Bucky Ball on 2017-10-06
Easy enough. [Go here, download the 'Driver Install Tool']("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=hll2340dw_us_eu_as&os=128"). There is a read me file which gives instructions for how to use it included in the download. Follow that. When complete ...

Open 'Printers'. Delete whatever printers you've created then 'Add Printer'. When you get to the part where you select a driver the correct driver for your printer will now be present. Install it and enjoy.

99.9% of newer Brother printers work with Ubuntu. Yours is no different. ;)

(Hint: in your code, why have you cd-ed to /tmp and are trying to do everything from there? Didn't you download the driver tool to 'Downloads'? Did you even download the driver tool yet? You need to extract that and be in the same folder as it is to run the commands.)

(Do not try to follow 'some web instructions' and do disregard the Linux Foundation stuff in this instance (often outdated and lacking detail). Find the 'readme' file in the 'Driver Installer Tool' download and follow that to the letter. Let us know how you go.)

---

### Post by slickymaster on 2017-10-06
*Thread moved to **Hardware**.*

---

### Post by gurdenite on 2017-10-06
> **Bucky Ball said:**
> Find the 'readme' file in the 'Driver Installer Tool'

Do you have instructions for that, because I've been using Linux for over ten years now and I can't find it.

---

### Post by Bucky Ball on 2017-10-06
My mistake. When you agree to the terms to download the Download Installer Tool, you will end up at a screen with the instructions right there on the screen in front of you.

---

### Post by kurt18947 on 2017-10-06
Little bit of a hijack here - sorry but I was impressed.:grin: I have 2 networked printers Brother HL-3170cdw and Samsung SL-M2870. I installed 17.10 on a spare machine. It found both printers and installed them without any prompting, some sort of driverless install. The URI started with ipp/something/something. I did not test much but both machines printed. Didn't test duplexing etc. It doesn't get much easier than that. 

It did seem to take longer from clicking "print" to output, maybe 1 - 1.5 minutes vs. seconds.

---

### Post by pdc on 2017-10-08
thanks for the feedback Kurt: 

as I understand it .............. in 17.04 Ubuntu, Apple airprint compatible was implemented [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) ....... so as I understood it, any recent printer will get recognised and one does not have to install drivers; ........ if airprint compatible ....... but all the manufacturers have been introducing compatiblility for some time now ...........

so for this HL-L2340, on 17.04 onwards, plugging it in should implement what Kurt reports .... the system does it for you. ......... so checking on the appleprint compatible list, the Brother HL-3170cdw is compatible; curiously, the Samsung SL-M2870 is not listed but good it works!

_____________________

so ........... from 17.04 onwards, one should not need to download the Brother installer tool for such as the HL-L2340DW

for anyone wishing to use it, if the Tool is downloaded and saved to the Downloads directory, the commands should be 

[COLOR="#FF0000"]cd Downloads
gunzip linux-brprinter-installer-*.*.*-*.gz
sudo bash linux-brprinter-installer-*.*.*-* HL-L2340DW[/COLOR] (if that is the printer you are installing .....)

---

### Post by kurt18947 on 2017-10-08
> **pdc said:**
> 

so ........... from 17.04 onwards, one should not need to download the Brother installer tool for such as the HL-L2340DW

for anyone wishing to use it, if the Tool is downloaded and saved to the Downloads directory, the commands should be 

[COLOR=#FF0000]cd Downloads
gunzip linux-brprinter-installer-*.*.*-*.gz
sudo bash linux-brprinter-installer-*.*.*-* HL-L2340DW[/COLOR] (if that is the printer you are installing .....)

I've found that putting the script in a folder and running it from that folder convenient. The script downloads .deb files and also creates an uninstall script. Personal preference I create a Brother folder on the original user's desktop. Install related files are all in the same place that way.

---

### Post by Bucky Ball on 2017-10-08
> **pdc said:**
> [COLOR="#FF0000"]cd Downloads
gunzip linux-brprinter-installer-*.*.*-*.gz
sudo bash linux-brprinter-installer-*.*.*-* HL-L2340DW[/COLOR] (if that is the printer you are installing .....)

Misleading, and if you're meaning for people to enter these commands in a terminal verbatim (copy/paste), wrong. They won't work.

'*.*.*-*' in your commands MUST be replaced by the version number of the Brother installer tool you are using or the commands posted will do nothing, apart from throw an error. ;)

* For instance:

```
gunzip linux-brprinter-installer-*.*.*-*.gz
```

... doesn't refer to any existing file, regardless of the directory you're in, unless you are trying to unzip a file called 'linux-brprinter-installer-*.*.*-*', which you are not.

---

### Post by pdc on 2017-10-08
thanks; I took that from the Brother site:

---

### Post by kurt18947 on 2017-10-11
> **Bucky Ball said:**
> Misleading, and if you're meaning for people to enter these commands in a terminal verbatim (copy/paste), wrong. They won't work.

'*.*.*-*' in your commands MUST be replaced by the version number of the Brother installer tool you are using or the commands posted will do nothing, apart from throw an error. ;)

* For instance:

```
gunzip linux-brprinter-installer-*.*.*-*.gz
```

... doesn't refer to any existing file, regardless of the directory you're in, unless you are trying to unzip a file called 'linux-brprinter-installer-*.*.*-*', which you are not.

Typing the first part of the installer file name them [tab] for autocomplete works too, at least in ubuntu-gnome. Autocomplete saves on typos. I run the script without specifying a printer so I'm then prompted for the printer model. I use caps for the letter portion e.g. HL-3170CDW. Slightly different road to the same destination I think.

---

### Post by VMC on 2017-11-22
> **Bucky Ball said:**
> Easy enough. [Go here, download the 'Driver Install Tool']("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=hll2340dw_us_eu_as&os=128"). There is a read me file which gives instructions for how to use it included in the download. Follow that. When complete ...

Open 'Printers'. Delete whatever printers you've created then 'Add Printer'. When you get to the part where you select a driver the correct driver for your printer will now be present. Install it and enjoy.

99.9% of newer Brother printers work with Ubuntu. Yours is no different. ;)

(Hint: in your code, why have you cd-ed to /tmp and are trying to do everything from there? Didn't you download the driver tool to 'Downloads'? Did you even download the driver tool yet? You need to extract that and be in the same folder as it is to run the commands.)

(Do not try to follow 'some web instructions' and do disregard the Linux Foundation stuff in this instance (often outdated and lacking detail). Find the 'readme' file in the 'Driver Installer Tool' download and follow that to the letter. Let us know how you go.)
Surprisingly this worked for my ***Brother HL-L2320D***, for the newest xubuntu-bionic. Somewhere along the line I was referred to download the two 'deb' files, and they worked for Xenial and Artfull, but failed for Bionic. I went through a long and tedious process of configuring CUPS, but no print. I could see the printer lights flashing, but no output.

  That install file creates two printer drivers, one of which doesn't work and is the same one that I have installed all along. Not sure why the two drivers, but at least I know now which one to use. When the install file finishes and asks if I wanted to print a test page, that worked. It didn't say which one it used.

---

