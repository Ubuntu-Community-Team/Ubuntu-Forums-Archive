---
title: "Dell v515w AIO printer on 11.10"
date: 2011-12-13
forum: Hardware
---

### Post by Lewnick on 2011-12-13
I am running two systems, one is a dell netbook with Ubuntu 10.04 on it. After upgrading from 8.04 my printer would not work, I was able to resolve that part.

My desktop computer however, running Ubuntu 11.10 will not print.
Weird part is, I can print a test page from the Dell Printer Toolbox, but not from the Ubuntu printing application.
Also unable to print from any other software. 

I have installed the printer both through the auto install feature in the OS and also manually. Manual install using the network backend with IP address rather than the USB cord, got me alot closer as I can now print the test page through the Dell Toolbox.

Has anyone else seen this issue? Perhaps solved it?:confused:

---

### Post by CrammitTheFrog on 2011-12-26
I have the same printer and I just got it working.  Dell re-brands their printers from Lexmark.  I had to look at all of their printers to see which one closely resembles mine.  I found that Lexmark Intrepret S405 is almost identical.  You will need to the driver you need.  I have not tried the firmware update, and I'm working on getting the scanner portion working.  I'll let you know if when I get it working.  Here is the link to the driver page from where I downloaded mine from:

[http://support.lexmark.com/index?page=product&locale=EN&productCode=LEXMARK_INTERPRET_S405&segment=SUPPORT&userlocale=EN#4](http://support.lexmark.com/index?page=product&locale=EN&productCode=LEXMARK_INTERPRET_S405&segment=SUPPORT&userlocale=EN#4)

---

### Post by CrammitTheFrog on 2011-12-26
I found another thread that gives instructions on how to install a Lexmark printer, and it's the same thing I had to do.  He is saying that Lexmark doesn't have support to scan over the network yet in Linux, and another person spoke with Lexmark tech support who said the same.  Hopefully, they will update their current drivers to bring full functionality.  Lastly, I tried to perform the firmware update, but the Dell version is not compatible.  I sure that if there is a way re-image the printer so that it will show up as a Lexmark printer to a computer then it may be compatible.

---

### Post by Wolfmage on 2012-01-15
[Quote- Lewnick: I have installed the printer both through the auto install
feature in the OS and also manually. Manual install using the network backend
with IP address rather than the USB cord, got me alot closer as I can now print
the test page through the Dell Toolbox.}
How did you do the IP Install? I am having the same issue you did with test pages not printing.

---

### Post by CrammitTheFrog on 2012-01-16
Wolfmage, your printer should have a IP address like a computer does, and you can find out what it is through the printer menu.  Are you installing the Lexmark driver or the Dell one?  The Dell driver did not work for me.

---

### Post by Wolfmage on 2012-01-19
I have tried to install both the Dell & the Lexmark drivers. Both tell me the same thing: my root(administrative) password is incorrect. I know that it is not incorrect because I have been able to use synaptic & install other programs using my root password.
I tried using Gdebi to install the drivers; when I go to get them in the folder they're in, Gdebi doesn't see them.
I thought about using the terminal but do not know the correct command line to use.

I have printed a test page and a network configuration page via my printer 'Setup. The IP address displays as all zeros. In addition it tells me the wireless signal is unacceptably too weak.
I just installed Ubuntu Studio 10.04 Lucid a about a week ago & am having issues setting up the wireless connection.

---

### Post by CrammitTheFrog on 2012-01-19
The problem with the root password is that Ubuntu doesn't create a root user.  I encountered the same problem, so I ran it through the terminal.  Here is a quick lesson in command line:

```
ls
```
lists the files and folders in your current location

```
cd
```
changes the directory/location

Example:
```
cd /home/*username*/Downloads
```

This will make your Downloads folder your current location, which should be the default place for your downloads.  To run the driver script use:

```
sudo ./*script*
```
sudo gives the command root privileges

Then, it will prompt you for your password.  This should be your password.  You'll have to make it executable if it isn't, then use this command:

```
chmod -x *script*
```
changes the privileges of the file, in this case making it executable

My wifi just worked after I installed 11.10.  Are you using a laptop?  What kind of wifi card are you using?  Use either of these commands to find out:

```
lspci
lspci -v
lspci -vv
```
The 'v's give you more information about each device

---

### Post by Wolfmage on 2012-01-19
Thank you so much. I will try this out some time tomorrow. My mind's a bit fried right now. LOL

---

### Post by Wolfmage on 2012-01-26
I switched to Linux Mint 12(Gnome) and wireless is working great. I am still having issues with the printer.
I've been to Dell and they are quite specific as to which Linux systems their drivers are compatible with. I am headed over to see if I can get the Lexmark driver.
:KS I have, successfully, downloaded the Lexmark drivers. However, I am running into an issue when I get to the step where it asks How will you connect to this printer?
There are 3 choices (1) wireless (2) USB (3) Ethernet
With the first two choices the "Next" button stays grayed out & non-functional even after I have connected the USB to the printer and the computer
With the 3rd choice, there is no Ethernet port on this printer, anywhere. On the back, next to the USB port for the installation cable, there are two phone jacks, neither is an Ethernet port.

I have tried restarting the printer and the netbook to no avail. 
I want to use the WiFi or the USB connection; does anyone know if there is a work around or why this may be occurring?

---

### Post by CrammitTheFrog on 2012-01-26
I set mine up as wireless, but I can't remember the specifics at the moment.  Is your printer connected to the wireless network in your house?  If so, it will have an IP address.  You can find it through the printer's menu.  I had to enter the IP address to get it to install.  I will re-install the driver when I get home to give you more information.

---

### Post by Wolfmage on 2012-01-26
Any input would be welcome; thank you 'Crammit.

The printer has not yet been connected to the wireless router in the house. From what I can see of the installation process the installer was supposed to help with that. 
On a different note, I needed to print something this morning. I plugged in our Main Household printer, an HP F4100 series all-in-1. It installed automatically. Within about 2minutes I was printing what I needed. 
I just wish I'd known that Dell uses Lexmark manufactured printers for their Branding.
I've been working on getting this Dell printer installed on my Dell netbook for well over a week, now, with no success.

---

### Post by CrammitTheFrog on 2012-01-26
I would've like to know that, too. lol  HP printers "agree" with Linux better than others, from what I learned while working on this problem.  Do you get full functionality from your HP all-in-one?  Even after you install the Lexmark drivers, you can only print.  The printer wouldn't recognize my computer when trying to scan a file to it.  If everything works, I may just replace the Dell printer for an HP one.

---

### Post by Wolfmage on 2012-01-27
My roommate has been urging me send the Dell printer back. I think getting an HP may be the only answer. I need the ability to scan and print. If the Lexmark drivers only recognize printing and will not recognize scanning that does me no good.
To answer your question, we use Linux on all of our laptops and computers. So far, it does not matter which distro is being used, we can print and scan with the HP all-in-1. 
I thank you for your assistance, and hope you have a great day.

---

### Post by CrammitTheFrog on 2012-01-27
I found this on Linux-drivers.org in the Printer & Scanner section:

HP Linux Imaging and Printing (HPLIP) - HPLIP is an Hewlett-Packard developed solution for printing, scanning, and faxing with HP inkjet and laser based printers in Linux. Chances are, your Linux system already has the HPLIP software installed. That's because all major Linux distributions regularly pick up the HPLIP software and include it with their distribution installation. However, if it is not installed or you need to upgrade to a newer HPLIP version to support your printer, you've come to the right place. On this website you can download the HPLIP softrware which supports 1,686 HP printers on nearly any Linux distribution available today. You can also find answers to many of your questions within the new knowledge base, or post a question on the Get Help page when you can't find the answer directly.

I'm going to purchase a HP printer and give the Dell printer away.

---

### Post by geoffrian on 2012-02-11
> **Wolfmage said:**
> I switched to Linux Mint 12(Gnome) and wireless is working great. I am still having issues with the printer.
I've been to Dell and they are quite specific as to which Linux systems their drivers are compatible with. I am headed over to see if I can get the Lexmark driver.
:KS I have, successfully, downloaded the Lexmark drivers. However, I am running into an issue when I get to the step where it asks How will you connect to this printer?
There are 3 choices (1) wireless (2) USB (3) Ethernet
With the first two choices the "Next" button stays grayed out & non-functional even after I have connected the USB to the printer and the computer
With the 3rd choice, there is no Ethernet port on this printer, anywhere. On the back, next to the USB port for the installation cable, there are two phone jacks, neither is an Ethernet port.

I have tried restarting the printer and the netbook to no avail. 

I want to use the WiFi or the USB connection; does anyone know if there is a work around or why this may be occurring?

I am having that same frakin problem.  I had an issue in the past when I tried to install the Dell driver after using Ubuntu for a little while.  I mean after I install it and do some upgrades and software install's the .sh file gives me a Lua scripting error and the ONLY remedy I can think of is to reinstall Ubuntu, install the driver first, and then do my updates.  The printer worked perfectly fine until today when I did just that and now, like you, after clicking on USB and then clicking next, it is grayed out and I can not continue... Frustrated to no end.

---

### Post by CrammitTheFrog on 2012-02-13
Geoffrian, what version of Ubuntu are you using?  Dell's driver only works for certain versions.  I was unable to get the Dell driver to work on 11.10, but I was able to get the printer to work using a Lexmark driver.  The scanning function still didn't work, though.  I solved this problem by buying an HP printer.  I have full functionality with it.

---

