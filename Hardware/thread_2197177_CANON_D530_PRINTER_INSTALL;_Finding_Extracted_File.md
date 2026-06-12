---
title: "CANON D530 PRINTER INSTALL; Finding Extracted Files"
date: 2014-01-02
forum: Hardware
---

### Post by SpikeLS6 on 2014-01-02
Found Canon recommended Driver File on their European Site. I Downloaded and extracted it, then installed it. I can not find the file anywhere to direct the "Add Printer, Printer - Localhost" function to the file.  The Printer - Localhost Screen Device URI: says it is at "CNUSB:/dev/usb", but once I navigate there in Terminal, nothing shows up. I have looked in the /etc and /dev folders, but nothing is there regarding the driver file. 

How can I use the Find, Locate, or Whereis commands to fine the file? Any other suggestions?

Spike

---

### Post by varunendra on 2014-01-05
Maybe look at the installation script, or give us the link to the driver so we can examine it, to see which files it creates/copies and where.

---

### Post by SpikeLS6 on 2014-01-06
"I will be glad to provide assistance.  A Linux driver can be downloaded from the Canon USA website at this address:

 ["http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_d530#DriversAndSoftware]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_d530#DriversAndSoftware")"

  1.  Verify that the correct operating system is automatically  detected.  If not, click on the drop-down arrow, scroll down to the  bottom and click on Linux.

  2.  Click on Drivers.

  3.  Click on the File Description link for UFR II Printer Driver for Linux Version 2.70.  
 You will also see a Disclaimer at the bottom.  Review the disclaimer and click I Agree - Begin Download.

 Note:  Clicking I Decline - Go Back will take you back to the available downloads list.  

 Please let me know if you need further assistance regarding your imageCLASS D530.

 Thank you for choosing Canon."

This is the email I received from Canon locating the correct driver.

Thank you for your help.

Spike

---

### Post by varunendra on 2014-01-07
I'm sorry. 73 MB is too large size for my gprs connection which is currently limited at 2.5 KB/s (unbelievable, but that's what I get 28 days a month). I'm afraid you'll have to find and post the installation scripts yourself, unless someone else with a fast internet connection can analyse the package and post back relevant info for us here.

A typical approach to find the installation files is to start with the file that you started the installation with (open it on text editor and read what it does), then check other scripts it calls and see what other scripts they in turn call and what do they all create/copy and where. Usually it is just a conditional combination of three-four scripts in a driver installation package. But I can't predict how complex it may get with a 73 MB package.

Alternatively, you can use easy to use search programs like "SearchMonkey" (sudo apt-get install searchmonkey) to search files modified within a particular date range (it works like a gui frontend to **grep** and **find** combined). Although I'm not sure 'date modified' criteria would give you the desired results.

---

### Post by SpikeLS6 on 2014-01-10
Went through the downloaded Canon file in a Text Editor to see the files that came in. I could not identify anything that would start it, or where the files were put once extracted & installed. I do not know how to make up a "script", so I am dead in the water with it. When I need a back up printer, I guess I will have to close Ubuntu and bring up Windows. Windows runs, with the included CD, all the functions with no problems.

Thank you for the help. Tough nut to crack when Canon does not really support Linux.

Spike

---

### Post by varunendra on 2014-01-10
Going back to your first post -
> **SpikeLS6 said:**
> I Downloaded and extracted it, **then installed it**.

Maybe tell us 'How' you installed it ? How you started the installation etc. We can take it from there.

I'm assuming that the 73 MB package is a 'Source' package which needs to be compiled then installed. If so, just give me the first file that started the installation, and I should be able to ask you for the exact other files (with their relative paths) that it might have used to proceed the installation.

Lengthy, but possible approach if you wish to try it. :)

---

### Post by SpikeLS6 on 2014-01-11
Yes, I would love to follow you along to see if we can get it working. I am in uncharted waters.

I first downloaded the recommended Canon Driver File: ["http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_d530#DriversAndSoftware]("http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/imageclass_series/imageclass_d530#DriversAndSoftware")". I opened the "/home/michael/Downloads/Canon D530 Drivers/Linux_UFRII_PrinterDriver_V270_us_EN.tar.gz" file in Archive Manager and clicked EXTRACT.

Then I drilled down the extracted "Linix_UFRII_PrinterDriver_V270_us_EN, to 32-bit Driver, to Debian, then opened the "cndrivcups_common__2.70-1_i386.deb, again I think, in Archive Manager to install it.

When I bring up "PRINTERS, Local Host" from Search your Computer, I ADDED the Generic-PCL-Laser printer that was there. I double clicked the ICON for Properties. In the Properties, I have:
   Description:        Canon D530
   Location:             Michael-Desktop-E
   Device URI:         cnusb:/dev/usb/
   Make & Model:    Canon D530/D560 UFRII LT ver.2.7
   Printer State:       Idle

A test page will not print, but the screens say that the job was submitted and gives a job number.

I did find the Canon D530/D560 UFRII LT ver.2.7 this time by checking each individual entry under Canon. Still submits the print job, but nothing prints.

Is this enough to get started?

Spike

---

### Post by varunendra on 2014-01-13
.deb files are installer packages themselves. By default they open (and get installed) with Package Managers, not Archive Manager. Although you may choose to open it with your Archive Manager.

What was the .deb file's size? If not too large, can you attach it here? Else take a look at its contents (by opening it with Archive Manager). Apart from the "DEBIAN" folder in it, usually its contents are located in the same directory structure as they would be placed while installing. Just extract the "controls" file from the "DEBIAN" folder inside the .deb package. This is a simple text file that 'Controls' the installation process of a .deb package. Post it back if posting the whole .deb file is not possible (due to large size).

By the way, if you found your printer model and are still unable to use it, I doubt I can help anymore, but let's just see what the .deb package you got has to offer.

---

### Post by SpikeLS6 on 2014-01-14
You are correct; I did Install the file with GDebi Package Manager. It gave no errors once finished.

The Extraction produced two .deb files with the following file sizes:
Canon D530 Drivers/Linux_UFRII_PrinterDriver_V270_us_EN/32-bit_Driver/Debian/cndrvcups-common_2.70-1_i386.deb - 1.5 MB Archive
Canon D530 Drivers/Linux_UFRII_PrinterDriver_V270_us_EN/32-bit_Driver/Debian/cndrvcups-ufr2-us_2.70-1_i386.deb - 13.3 MB Archive

Can you be a little more specific on finding the "Controls" file from the "DEBIAN" folder inside the .deb package? I have tried to locate it, but can not find it.

If the smaller 1.5 MB .deb file is postable, how can I do that?

One step at a time, and thank you again for the help.

Spike

---

### Post by SpikeLS6 on 2014-01-14
This is new. While in the Printer - Localhost screen, I noticed that the printer properties screen showed the Printer not connected. I turned it on and the Printer State advised that it was activating, then reported that "Processing - Unable to open USB device "cnusb:/dev/usb/": Is a directory"

The Device URI is indeed "cnusb:/dev/usb/"

Does this help any?

Spike

---

### Post by varunendra on 2014-01-15
> **SpikeLS6 said:**
> Can you be a little more specific on finding the "Controls" file from the "DEBIAN" folder inside the .deb package? I have tried to locate it, but can not find it.

If you can open the .deb file on the archive manager, you should see that directory among the contents of the .deb file. As far as I know, it is an essential component of .deb packages. It (the "DEBIAN" directory inside the .deb file) must have at least two files inside it - control and md5sums. Besides these two, there may be other files that describe any additional actions while installing the .deb package.

Anyway, regardless of above, if the packages installed without error, I don't think fiddling with them is going to help. What may help is probably this thread and the suggestions in it : [http://ubuntuforums.org/showthread.php?t=1427330](http://ubuntuforums.org/showthread.php?t=1427330)

It is an old thread but seems quite relevant to your current problem. A quick question after reading the first post in the above thread - Is your Ubuntu installation 64 bit? If yes, I think this is the root of the problem (quoted from post #7 in above thread) -
> 64bit systems look in /usr/lib64

canon is a default 32 bit install so puts stuff in /usr/lib

Accordingly you may have to create a symbolic link to the actual directory where the drivers are installed. I'm not sure if the exact command suggested in post #80 will work or not *(since it is meant for a driver package which used to contain only rpm packages, while you seem to have gotten ready to install .deb files in it)*, but if unsure of the actual location of the installed drivers, trying that won't hurt -
```
ln -s /usr/lib /usr/lib64
```

Since the initial posts in the thread are old, not everything described in them would be applicable to your installation. Just take a quick look through the thread and see if you can find a post that is close to your exact situation and offers any help.

**PS:**
If you can't open the .deb packages on the Archive Manager by default, you can Right-click it > Open with other application... > "Show other applications" > "Archive Manager" > "Select" button.

By opening it on archive manager, you can browse the directory structure of the .deb file. Its contents will be copied to exactly same locations in the Ubuntu installation as they are placed inside the archive (except the "DEBIAN" folder, which is just an additional folder inside the .deb packages that holds the information and instructions for installation). Please confirm you can open it on Archive Manager or not, and if yes, post back the name of the contents of its "DEBIAN" folder. Do the same with the 2nd .deb file.

**PPS:**
Sorry if most of above sounds too complex and/or vague. I'm overworked at the moment and it is really hard to focus and be absolutely clear on everything. I'm relying quite a lot on your own ability to search and pick relevant information and post the details here.

---

### Post by SpikeLS6 on 2014-01-17
I went through the link you sent from the Ubuntu Forums, but could not find anything in the directories I was looking for as far as installed Canon files. Noteing what someone said in the link that all Canon drives are in 32-bit format, I went back and re-installed the 32-bit Deb file from the Canon DEB folder. I brought up the Printer - Localhost screen and re-setup the printer properties. I found several new things in the Device URI: and the Make & Model: choices. I put in the correct items for my D530 printer and was able to successfully print a Test Page. I went into the PC and successfully printed an email from Thunderbird, a Calc spreadsheet, and a Text Document from Open Office. The printer balked at a file from Gedit. I will have to play with some settings, I guess. That seems to solved my Ubuntu Printing problem, so I will show this Thread as [SOLVED].

I see there is a different solution in the link regarding the scan function. I will work on that in the future. As least my printer works.

Thank you for your help!

Spike

---

