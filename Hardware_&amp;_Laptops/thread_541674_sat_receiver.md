---
title: "sat receiver"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by adrarian on 2007-09-02
hi all
 
how to upload/download firmware to sat receivers?:confused:

---

### Post by ddrichardson on 2007-09-03
That's an awful lot to ask without more information! What are you trying to upload, on what distribution, via what kind of connection and to what kinf=d of reciever?

---

### Post by ramjet_1953 on 2007-09-04
Most Satellite receivers have a serial port.

So, if you don't have a serial port on your PC, you may be able to do it with one of the USB to serial converters.

Also to use a USB to serial converter, you will need to un-install the packages brltty and brltty-x11

These are installed by default and are used for Braille displays for the blind.

Your next hurdle will be whether or not your Satellite Receiver manufacturer has released a Linux version of the comms package for your receiver.

Regards,
Roger 8)

---

### Post by [Alsharifi] on 2007-09-04
im guessing u are trying to download a bin file into an FTA receiver?

u need either a com1 port or if u have a newer model like a viewsat ultra u can use usb.

it also requires a Loader program which is exe. so ur prob going to have to give wine a shot.


i ahvent tryed yet,but next time my receiver crashes ill see how this works.

good luck!

---

### Post by chrome307 on 2007-09-04
I own a Technomate 1500Ci+ Super receiver and just use WINE with my Loader and transfer my files over - firmware/channel lists/softcam etc

---

### Post by [Alsharifi] on 2007-09-04
i might try with my viewsat extrema tonight to see if works...

---

### Post by Teva on 2007-11-02
Hey, I have a Viewsat Extreme and I send/receive files to/from it very easily with my desktop using a program called "minicom". However, I have no idea how do it from my laptop using a USB to Serial converter. If anyone knows I would appreciate the info. Anyhow, I can't remember the guy that wrote this and I don't want to take credit for his work so with that said...


First, install the following packages:
Install 'lrzsz' and 'minicom'

Once installed, now do the following:

1. Code:
             'sudo minicom'    you will be prompted to supply root password

2.)Once started, type ctrl-a then type o to enter the options menu. Settings should be as follows, keeping in mind that the paths and filenames will be dependent on your system. ([COLOR="Blue"]Main thing here is your "Download/Upload directory". This is where you'll have to put your bin files.)[/COLOR]
A.) Filenames and paths:
&#9474; A - Download directory : /home/username/
&#9474; B - Upload directory : /home/username/
&#9474; C - Script directory :
&#9474; D - Script program : runscript
&#9474; E - Kermit program :
&#9474; F - Logging options

B.)File transfer protocols:
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; Name Program Name U/D Fu
&#9474; A zmodem /usr/bin/sz -vv -b                   Y U
&#9474; B ymodem /usr/bin/sb -vv                      Y U
&#9474; C xmodem /usr/bin/sx -vv                      Y U
&#9474; D zmodem /usr/bin/rz -vv -b -E                N D
&#9474; E ymodem /usr/bin/rb -vv                       N D
&#9474; F xmodem /usr/bin/rx -vv                       Y D
&#9474; G kermit /usr/bin/kermit -i -l %l -s           Y U
&#9474; H kermit /usr/bin/kermit -i -l %l -r            N D
&#9474; I ascii /usr/bin/ascii-xfr -dsv                   Y U
&#9474; J -
&#9474; K -
&#9474; L -
&#9474; M Zmodem download string activates... D
&#9474; N Use filename selection window...... Yes
&#9474; O Prompt for download directory...... No






C.) Serial Port Setup: For com1 service
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; A - Serial Device : /dev/ttyS0
&#9474; B - Lockfile Location :
&#9474; C - Callin Program :
&#9474; D - Callout Program :
&#9474; E - Bps/Par/Bits : 115200 8N1
&#9474; F - Hardware Flow Control : No
&#9474; G - Software Flow Control : No
&#9474;
&#9474; Change which setting?
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;

All other settings can be left at default for our purposes with this project.Once you have all your settings configured properly, navigate down and highlight to Save setup as dfl and hit enter to save as your default settings.Then Exit.

3.) Now you have minicom configured we can go ahead and send whatever files we need to the unit. Type ctrl-a and then S to start the send process. Select Zmodem from the list and hit Enter. Select the file you wish to send navigating to it and use the space to select and then Enter to start the process.
Turn the viewsat on, with the power switch on the back and the transfer will start.
Once complete, hit ctrl-a and then X to exit.

HAVE FUN!!

---

### Post by broachoski on 2008-02-01
I use minicom to upload files to Viewsat Extreme and Sonicview SV1000 receivers thanks to the above post BUT had to make slight changes.

B.)File transfer protocols:
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; &#9472;&#9472;&#9472;&#9472;&#9472; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;
&#9474; Name Program Name U/D Fu
&#9474; A zmodem /usr/bin/sz -vv -b  Y U

***** I had to omit the Y and U from the line above ******

I am using a cheap USB to Serial (DB9) adapter so had to change 

&#9474; A - Serial Device : /dev/ttyS0

to 
 A -    Serial Device      : /dev/ttyUSB0

I also removed brltty via Synaptic
I also installed setserial and entered the command:
setserial -g /dev/ttyUSB0
though I am not sure if that was needed as that was a previous try at getting things going.

---

### Post by lnxnut on 2008-05-03
Give this program a whirl for ur viewsat.  Works just like the loader for windows.

Have your viewsat serial cable and power plugged in.  
Power off the viewsat.
Select your com port
Open your file (pgm)
Click the 'Connect' button
Turn power to viewsat on from the back, soon as lights come on click the 'Go' button.

---

