---
title: "new to Ubunto and installing printer"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by dewman on 2007-03-05
ok d/led the pipslite .rpm package for my epson rx580 printer trying to use alien to convert to .deb. The package is on the desktop.so i used this command in the terminal window

sudo alien -d --scripts pipslite-cups-1.0.0-1.i386.rpm
also used this

sudo alien pipslite-cups-1.0.0-1.i386.rpm


keeps telling me it cannot find the file

Anyone help with this?
Completely new to Ubunto so if someone could be gentle and walk me trough this step by step.

Thanks
John

---

### Post by dewman on 2007-03-05
Ok figured out the file needed to be in the home directory
and got it to convert to deb and install using these 2 commands

sudo alien --scripts --to-deb *.rpm
sudo dpkg -i pipslite-cups-1.0.0-2_i386.deb

now I cannot get the pipslite-install file to run to make the ppd file, either in a terminal window or by double clicking it.
I double click it , it just sits there if i run it in a terminal window using this command

start /usr/local/EPAva/LITE/pipslite-install (enter)
bash: Start: command not found


Anyone have any ideas?

Thanks John

---

### Post by dewman on 2007-03-06
ok getting closer got pipslite-install to run by using this command

./pipslite-install

but comes up saying it needs to make a ppd file to register to cups and to make sure the printer is connected to the computer and turned on.

well the printer is connected to a windows computer across the room so I found a long usb cable and connected it.
device manager finds it but pipslite-install won't lite up the continue button


Help
John

Ps forgot to mention I had to install libgtk package before pipslite-install would run

---

### Post by dewman on 2007-03-06
ok got it installed had to run setup and tell it the the port it was on /dev/usblp0 instead of /dev/usb/lp0

ran install with this cammand

sudo ./setup

then ./pipslite-install found the printer and continue button lit and created the ppd file

and was able to install the printer under network/windows printer (smb)

Then used install driver and went to the usr/shared/cups/model directory and selected the eksprx580.ppd file then the rx580 showed up in the epson list of printers.

Can't say whether it will print a test page cause my 2 week old printer is out of ink in one of the 6 cartridges epson is sending me 6 new cartridges should have them tomorrow .

hopefully this will help someone else get theres going


John

---

### Post by dewman on 2007-03-07
Got the ink cartridge today and it started printing the Ubuntu test page as soon as it was in.

Thats something how it will print from The Ubuntu machine but not from the Vista machine over the network.

And Epson was no help with Vista.

---

### Post by Brigitte Seib on 2008-03-30
Hi John,
I managed to install my RX580 following your instructions. 
However I cannot get the pipslite-install to connect to my RX580 and therefore not generate the special PPD for my RX580.
What setup did you run to change the printer port?
Please let me know

Did you get the scanner part of the RX580 to work as well?

I am using CUPS and I am  on Feisty 7.04 Ubuntu

My printer is recognized and I managed to print a testpage however with the default ppd I am stuck with A4 page format and very few paper options. So I need to be able to install the special ppd. The A4 paper is the worst since I am in Canada and use Letter size paper.
please let me know

Thank you
Brigitte

---

### Post by Brigitte Seib on 2008-03-30
Hi John,
I found what you meant with running setup ..it is the setup in /usr/share/pipslite 

I had to do the same you did i.e. change the PrinterDevicePath from /dev/usb/lp0
to
/dev/usblp0
since I connected the RX580 to my USB#1 port

I have an HP laser connected to my USB#2 port

I did a reboot to simply ensure that all services restarted after this I could run
/usr/bin/pipslite-install 
and it connected to the printer and generated 
/usr/share/cups/model/eksprx580.ppd

I changed the configuration of the printer and printed a testpage on Letter paper

thank you for documenting what you did 
it  was great to get the printer to work

Now I need to get the scanner to work .. did you get it to work?
Brigitte

---

