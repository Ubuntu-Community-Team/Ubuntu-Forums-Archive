---
title: "Brother MFC-9120CN Network Printer"
date: 2012-09-19
forum: Hardware
---

### Post by JLUbunt on 2012-09-19
Hello I installed Ubuntu 12.04 LTS on my HP ML110G6 computer. I have a network printer Brother MFC-9120 connected to the network. Let Ubuntu search and install the printer. It does not work.  When I go to the printer icon it gives the message processing - not connected?  The printer is connected and switched on.  I have not been able to fix it for sometime now.  On the same computer someone who knows what he is doing installed Linux Susi. The printer works on that.  I'm trying to fly solo so installed Ubuntu. Hopefully I'll get there. 
I looked on the Brother website it mentions Linux 12.04 see below. I don't know if I am a rpm user or a dpkg user.  Maybe if you can help I'd get it to work.  :D


**I'm using a Linux 64 bit edition. Can I use the Brother Linux printer drivers?** 
Yes. Brother printer drivers are created and optimized for 32 bit version of Linux,
 but those can be used for 64 bit Linux also. Some additional steps are required.

**For rpm users:**
**1.** Install the standard C library for 32bit applications (e.g. glibc.i686(Fedora), libstdc++ for 32bit(openSUSE))
**2.** Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
**Command1: mkdir /usr/lib/cups**
**Command2: mkdir /usr/lib/cups/filter**

2-2. Create /usr/share/cups/model if it does not exist
**Command: mkdir /usr/share/cups/model**

**3.** Install the drivers.

**4.** Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
**Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter**



**For dpkg users:**
**1.** Install the standard c library for 32bit applications (e.g. lib32stdc++6(Debian) or ia32-libs(Ubuntu))
**2.** Create some folders if it is required
2-1. Create /usr/lib/cups/filter if it does not exist.
**Command1: mkdir /usr/lib/cups**
**Command2: mkdir /usr/lib/cups/filter**

2-2. Create /usr/share/cups/model if it does not exist
**Command: mkdir /usr/share/cups/model**

**3.** Install the drivers using "--force-architecture" or "--force-all"option.

**4.** Copy brlpdwrapperXXX files under /usr/lib/cups/filter/ to /usr/lib64/cups/filter/
**Command: cp /usr/lib/cups/filter/brlpdwrapper* /usr/lib64/cups/filter**

**5.** Copy libbrXXXX files under /usr/lib/ to /usr/lib32/ if /usr/lib32 exists.
**Command : cp /usr/lib/libbr* /usr/lib32/**

---

### Post by kurt18947 on 2012-09-19
Brother has a script which has worked quite well for me.  Little manual configuration necessary.  Here is a thread with Brother's web site address and other useful stuff :

[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

I downloaded and attached the installer script - post #4.  Brother uses a 'unconventional' to me means to download it.  I have had the best luck with assigning a static I.P. to the printer and using HP 'Jetdirect' protocol, e.g. Device URI=http://i.p. address.  The installer script will list a bunch of different network connection options,  I get about 17 counting USB.

---

### Post by JLUbunt on 2012-09-20
> **kurt18947 said:**
> Brother has a script which has worked quite well for me.  Little manual configuration necessary.  Here is a thread with Brother's web site address and other useful stuff :

[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

I downloaded and attached the installer script - post #4.  Brother uses a 'unconventional' to me means to download it.  I have had the best luck with assigning a static I.P. to the printer and using HP 'Jetdirect' protocol, e.g. Device URI=http://i.p. address.  The installer script will list a bunch of different network connection options,  I get about 17 counting USB.
Thanks Kurt. I have heard that it is better to set a static IP address. I have found out how to obtain the IP address from the printer but do not know how to set the address. My knowledge of how to set up machines is. In your example " Device URI=http://i.p. address" Do I just type this command into the Terminal? I do not know what the Device URI is.  Is this something that would be the same for all Brother MFC-9120 printers.  If you know of a step by step guide I could read to learn how to do this I'd be very grateful.
Thanks again.

---

### Post by kurt18947 on 2012-09-20
> **JLUbunt said:**
> Thanks Kurt. I have heard that it is better to set a static IP address. I have found out how to obtain the IP address from the printer but do not know how to set the address. My knowledge of how to set up machines is. In your example " Device URI=http://i.p. address" Do I just type this command into the Terminal? I do not know what the Device URI is.  Is this something that would be the same for all Brother MFC-9120 printers.  If you know of a step by step guide I could read to learn how to do this I'd be very grateful.
Thanks again.

Here are pubs that may be helpful to you:

[http://welcome.solutions.brother.com/bsc/public/us/us/en/doc/manual_index.html?reg=us&c=us&lang=en&prod=mfc9120cn_all&dlid=&flang=English&type2=-1](http://welcome.solutions.brother.com/bsc/public/us/us/en/doc/manual_index.html?reg=us&c=us&lang=en&prod=mfc9120cn_all&dlid=&flang=English&type2=-1)

The network manual, page 52 talks about how to use the control panel on the machine  to assign a static i.p. address.    To change the device URI you need to get to printer properties.  In most Ubuntu versions, I just right-click on the printer icon and left-click 'properties'.  The installer script should do this when it asks about connections.  Select i.p. address (or however it's phrased) then enter the assigned address.  

I think you must use a static i.p. address on the printer when using the JetDirect/socket:// protocol because you're telling the O.S. to print to a certain i.p. address.  If the i.p. address assigned to the printer changes, it'd be the equivalent of moving and not doing change-of-address notifications.  Your mail will keep going to your old address until you notify those that send you mail of your new address.

---

### Post by JLUbunt on 2012-09-22
Hi Kurt I downloaded the script you suggested. It is quite long. I do not know how to run it. Do I cut and paste it into the terminal? I've been doing some reading about using the Terminal and setting the static IP address and have identified the IP address (and other data) from a report from the printer but have not found out how /where to enter it.
Making slow progress!
Thanks

---

### Post by kurt18947 on 2012-09-23
> **JLUbunt said:**
> Hi Kurt I downloaded the script you suggested. It is quite long. I do not know how to run it. Do I cut and paste it into the terminal? I've been doing some reading about using the Terminal and setting the static IP address and have identified the IP address (and other data) from a report from the printer but have not found out how /where to enter it.
Making slow progress!
Thanks

I found the method of saving the script sort of counterintuitive which is why I posted the saved archive.   Once you have the archive saved to an account with SUDO privileges, navigate to the folder/directory where the file  "linux-brprinter-installer-1.0.4-1" is stored.  Open a terminal and type "sudo bash linux-brprinter-installer-1.0.4-1" and press 'enter'.  The script should start, ask you for the printer model, ask you to agree with a couple license agreements and run.  I used caps for the printer model e.g. MFC-9120CN.  You will be asked to select the connection from a list with several choices.

I've found knowing how to run a bash script useful for other hardware devices as well.  Realtek for one supplies their linux Wifi drivers as a bash script.  The benefit to manufacturers is that one bash script will run on most modern linux distros.  It really isn't that hard once you learn how as is the case with a great many things.

---

### Post by JLUbunt on 2012-09-25
Hi Kurt The bash script command worked well and unpacked and let me use the installer.  I typed in (CAPS)
 the Model name MFC-9120CN
 Then answered will you supply the device URI n
It did not work I looked at the printers in the control section and after experimenting found 2 drivers and deleted the top one and successfully printed the test page.  I thought all was well as I had not got this far before.  I tried printing a LibreOffice doc but failed. I re ran the install program 3 times and have not been able to get the printer to work. I'm up to 31 attempts. I turned off the printer exited out of Ubuntu then turned on the printer and computer again. It printed 3 more test pages. But still does not work on anything else.  
The problem seems to be that it picks up the Ubuntu driver which looks in the wrong place for the printer. I thought I looked at settings etc and thought that one looked promising was dnssd://Brother-MFC-9120CN-CUPS as this looked like the new driver but this did not work.  I do not know what a URI is but think that if I could find the appropriate one for my system I might be able to enter it manually.  
Sorry to keep bothering you.  Should I register it as a bug as it looks like there is something wrong with the way Ubuntu sets up when it tries to load my printer? I use Windows 7 on the same network an checked the printer is still working.

Thanks Jeff

---

### Post by kurt18947 on 2012-09-26
H
Yes, I've had problems with a networked printer using a usb:// address which obviously won't work.  Can you find the 'printing' app?  The one that has icons for installed printers?  Right-clicking on the printer icon and left-clicking on 'properties' should bring up a window with a few boxes.  One of them should be 'device URI'.  Change that as you wish.

I've seen reference to the problem with Libre Office but don't recall the resolution.  I've not experienced it myself.  If you're able to print a test page via Ubuntu I'd think you have a usable network connection.

---

### Post by JLUbunt on 2012-09-27
Thanks Kurt for all of your help. I'm going to have another look at all of the advice you have provided over the week end. I should have more time and hopefully think more clearly. I do get a bit frustrated and probably rush it.  As there was no important info on the system I reinstalled it to erase anything I might have inadvertently done.  I also plan to rerun the installation program and be systematic about checking it it see if it is fixed. 

When it is fixed an working I think it would be useful to register teh issue so the developers can amend the default connections.

Thanks again.
Jeff

---

