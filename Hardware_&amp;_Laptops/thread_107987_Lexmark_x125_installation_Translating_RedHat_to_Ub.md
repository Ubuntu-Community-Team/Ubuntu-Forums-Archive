---
title: "Lexmark x125 installation: Translating RedHat to Ubuntu"
date: 2005-12-24
forum: Hardware &amp; Laptops
---

### Post by Dr. E on 2005-12-24
Ubuntu correctly identified my Lexmark 125. I found the PPD files for my printer on linuxprinters.org and installed them. On linuxprinters.org it gives these special instructions for installing my printer, but it is for Red Hat users:


Because the driver needs to read status codes from the printer, this driver requires special setup which will be shown here for Red Hat systems, on other distributions it should work in a similar way. For Queue type, select Locally-connected, click "Custom Device" and specify /dev/null as the device. If you don't specify /dev/null, nothing will happen when you print because the driver won't be able to connect directly to the printer since the resource will be in use. If your printer has locked up in the past, you may need to unplug it from the power outlet and plug it back in before this driver will work. If your printer is not connected to /dev/usb/lp0, you can specify a different device using the driver options.



Could someone please indicate how to achieve this in Ubuntu?

---

### Post by JDoza on 2006-01-12
I'm interested as well. My X125 won't print also.

---

### Post by tagra123 on 2006-03-13
How To Install Lexmark X125 on UBUNTU:

There may be a better way but my printer is now printing. See notes at end of this post. I found this to work by trial and error.

Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal  using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

cd Desktop
mkdir prndriver
cd prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd src
make                    (ignore warnings you may see here)
sudo make install

*****
close the terminal
*****     

*******
Open your Printers by  using the menu (System-Printing)

Click on New Printer

STEP 1
Even though this is a local printer we will set it up as a network printer using LPD by entering the information below.

Choose Network Printer
Select UNIX Printer (LPD)

HOST:                localhost
Queue Type:      /dev/null

Click on the Forward button.

STEP 2 
Specify your printer by using the information below.
Select Lexmark as the manufacturer
Select X125 as the model
Select drv_x125(recommended) as the driver

Click on the Apply button

The printers window should now have the x125 listed as  your printer.

Right click on the printer and select properties.
Click on the Advanced tab.

Make sure your device is /dev/usb/lp0

Click on Print Test Page and the printer should print.


NOTES:

BUG?
I've noticed that once the document is printed I have to cancel the job manually in the "X125" window. 

To open that window form the menu (System-Printers) then double-click on the X125 printer.

To Cancel a completed print job that is still displaying as printing:
Right-click on the print job and choose cancel.  

If anyone knows how to get this to remove a completed job automatically please post

Output:

The output is not perfect but I'm going to check the settings and see if a newer driver is ready.


I hope this helps anyone having trouble getting this printer to print. Post a message I'll check back at least once a week.

---

### Post by tagra123 on 2006-04-04
How To Install Lexmark X125 on UBUNTU:

There may be a better way but my printer is now printing. See notes at end of this post. I found this to work by trial and error.

Download the X125-drv-0.2.3.tar.gz driver from: [http://sourceforge.net/projects/x125-linux/](http://sourceforge.net/projects/x125-linux/)

Select save to Deskop.

INSTALLING THE DRIVER

*****
Open your terminal using the menu (Applications-Accessories-Terminal)
*****

Type in the following commands:

cd Desktop
mkdir prndriver
cd prndriver
mv ./x125-drv-0.2.3.tar.gz ./prndriver/x125-drv-0.2.3.tar.gz

cd prndriver
tar -xvzf x125-drv-0.2.3.tar.gz

cd src
make (ignore warnings you may see here)
sudo make install

*****
close the terminal
*****

*******
Open your Printers by using the menu (System-Printing)

Click on New Printer

STEP 1
Even though this is a local printer we will set it up as a network printer using LPD by entering the information below.

Choose Network Printer
Select UNIX Printer (LPD)

HOST: localhost
Queue Type: /dev/null

Click on the Forward button.

STEP 2
Specify your printer by using the information below.
Select Lexmark as the manufacturer
Select X125 as the model
Select drv_x125(recommended) as the driver

Click on the Apply button

The printers window should now have the x125 listed as your printer.

Right click on the printer and select properties.
Click on the Advanced tab.

Make sure your device is /dev/usb/lp0

Click on Print Test Page and the printer should print.


NOTES:

BUG?
I've noticed that once the document is printed I have to cancel the job manually in the "X125" window.

To open that window form the menu (System-Printers) then double-click on the X125 printer.

To Cancel a completed print job that is still displaying as printing:
Right-click on the print job and choose cancel.

If anyone knows how to get this to remove a completed job automatically please post

Output:

The output is not perfect but I'm going to check the settings and see if a newer driver is ready.


I hope this helps anyone having trouble getting this printer to print. Post a message I'll check back at least once a week.



Tom Again.  

Here's a followup to my previous HOW TO INSTALL X125 On UBUNTU:

It now prints without having to manually cancel each print job.

Since the last posting KDE Desktop KUBUNTU is installed along with Gnome on my UBUNTU setup. I'm not sure if this installed any additional drivers, so I'm mentioning it.

Next

From a terminal type in:

First make a backup:
sudo cp /etc/cups/printers.conf /etc/cups/printers.conf.bak4x125

Next open the file to edit:
sudo gedit /etc/cups/printers.conf
 
If you've followed the steps above you should have an X125 section. 

Delete the X123 section and replace it with the following.
 
<DefaultPrinter X125> 
Info X125 
Location usb://Lexmark/X125 
DeviceURI file:///dev/null 
State Idle 
Accepting Yes 
JobSheets none none 
QuotaPeriod 0 
PageLimit 0 
KLimit 0 
</Printer> 


Save the file.



Reboot.

It works on UBUNTU and KUBUNTU.


Hope it helps. Tom -- tagra

---

### Post by LPent on 2006-07-07
I followed these instructions to the letter, 8 times. twice I even reinstalled Ubuntu fresh. It just doesn't work for me.
I keep getting a Printing:job-printing message followed by a foomatic error.
I tried several other drivers as well (ones that come with ubuntu and the 2 that can be found on Lexmarks site), the best I got so far was using the Z55 which gave me a Printing:job-printing followed by a ready. But unfortunatly without a print-out. I tried all the tricks I could find, like unplugging the printer (both USB and power), changing the config file etc. etc.
I have a nasty feeling I am missing something. Please help.

---

