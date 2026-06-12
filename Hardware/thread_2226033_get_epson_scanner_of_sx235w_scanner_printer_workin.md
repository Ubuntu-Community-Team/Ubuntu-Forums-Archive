---
title: "get epson scanner of sx235w scanner printer working on ubuntu 12.04"
date: 2014-05-24
forum: Hardware
---

### Post by andrea33 on 2014-05-24
Hey all! I just switched from ubuntu 10.03 to 12.04. My scanner (part of the scanner printer combination sx235w by Epson) does not work anymore. I downloaded the .deb plug from the epson download center. When opening that file in the software center, trying to execute it, it says this:
dependency is not satisfiable iscan (>=2.29.3)
I looked it up, it seems to mean that this plugin is not supported by ubuntu 12.04 (which seems to be too old for that plugin). How do I fix this? I tried to install the package for windows and running it through Wine, but that did not help. Thanks for the input and the help, I hope we will manage! Andrea

---

### Post by sammiev on 2014-05-24
> **andrea33 said:**
> Hey all! I just switched from ubuntu 10.03 to 12.04. My scanner (part of the scanner printer combination sx235w by Epson) does not work anymore. I downloaded the .deb plug from the epson download center. When opening that file in the software center, trying to execute it, it says this:
dependency is not satisfiable iscan (>=2.29.3)
I looked it up, it seems to mean that this plugin is not supported by ubuntu 12.04 (which seems to be too old for that plugin). How do I fix this? I tried to install the package for windows and running it through Wine, but that did not help. Thanks for the input and the help, I hope we will manage! Andrea

Try [these]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX"). and enter "sx235w" under product name.

---

### Post by pdc on 2014-05-25
Hi Andrea;

you don't tell us if you have 32 or 64bit: is it a usb cable from scanner to computer?

Epson say you need 2 things: all installed in the order:

1) data package: iscan-data_1.28.0-2_all.deb (bottom of list from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=27729&DSCCHK=dad2cb5b45435c09005b7aca852ad8acb85329f5) )

2) iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb or iscan_2.29.3-1~usb0.1.ltdl7_i386.deb 

an optional extra is iscan-network-nt_1.1.1-1_amd64.deb or iscan-network-nt_1.1.1-1_i386.deb from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=24993&DSCCHK=fd5cb71b1b7dcca4b2eba38afa9631e914a5e10f)

is that what you did?

---

### Post by andrea33 on 2014-05-25
Hey! This is exactly the site I used before to get the plugins.

---

### Post by andrea33 on 2014-05-25
Hey! Sorry! I have the 64 bit. There is a usb cable to connect the computer to the scanner. And indeed, the .deb files that you give, I have tried them all ;-)

---

### Post by andrea33 on 2014-05-25
So the data package ( nr. 1) gives no problem and gets installed, but the nr. 2 keeps on giving this "[COLOR=#000000]*dependency is not satisfiable' message :(*[/COLOR]

---

### Post by pdc on 2014-05-25
in a terminal what does

> dpkg -l | grep iscan give if you paste this command please;

If you downloaded the iscan_2.29.3-1~usb0.1.ltdl7_i386.deb to your Downloads directory, I wonder if you explore a command line install; to see what error messages are displayed in the terminal: 

so if you issued the commands

> [COLOR="#FF0000"]cd Downloads[/COLOR]  (hit the enter key)   

> [COLOR="#FF0000"]ls[/COLOR]           (just to see the file *listed* to see it is really there)

> [COLOR="#FF0000"]sudo dpkg -i iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb[/COLOR]

(I get the sense from here [http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA](http://www.sane-project.org/lists/sane-backends-external.html#S-EPKOWA) that your device might just work with xsane: it does not, is that correct?)

---

### Post by andrea33 on 2014-05-25
Hey! Unfortunately Xsane also does not recognize it :( This is the outcome of the first command line you gave me to type into terminal:
[COLOR=#000000][I]unknown option
Now I have to feeling I typed the command wrong. Are there spaces in it? I typed dpkg -l/grep iscan 
Sorry if I am being stupid, I am no programmer or expert, I just like ubuntu a lot...
BTW: I checked in terminal and indeed, the file is there for sure.[/I][/COLOR]

---

### Post by pdc on 2014-05-25
if copy and paste these types of commands: use the top line of the terminal; ie start at File with the mouse and move to Edit and down to Paste

> [COLOR="#FF0000"]dpkg -l | grep iscan[/COLOR] 

there is what is called a pipe symbol in the command; it is shift \ on the keyboard;

---

### Post by andrea33 on 2014-05-26
OK! This worked, thanks.
This is the outcome of that command in terminal
andrea@andrea-UX32A:~$ dpkg -l | grep iscan
ii  iscan-data                                 1.28.0-2                               Image Scan! for Linux data files
What is next? Thanks so much!

---

### Post by pdc on 2014-05-26
so my understanding was your system would not install iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb and it said 

so in post #7 above, I was suggesting the commands to run the install in a terminal; and that should print out error messages; detailing why it can't do what you asked it to do; and why it can't do what you asked;

so if you go back to post 37; give the suggestions there a whirl; and if you can copy the error message from the terminal: use the top line: ie use the mouse; select the text; and then go to top line and move from file along to edit and down to copy .....................

we can try and understand what your system is getting stuck on .............

---

