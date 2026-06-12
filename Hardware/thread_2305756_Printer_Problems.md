---
title: "Printer Problems"
date: 2015-12-08
forum: Hardware
---

### Post by shane_faulkinbury2 on 2015-12-08
Okay here's the problem,  I have three printers and the main one I use is a Brother MFC-J475DW which is connected via usb which is my main printer and is out of ink.  I also have two network printers which are an HP Officejet 66000 which only prints emails and a Brother MFC-495CW.  I have System Settings installed and when I open it, it sees the Brother MFC-J475DW and the HP Officejet 6600.  However it does not see the other Brother.  I've gone to Brother and downloaded and installed the driver, but my PC still doesn't see it.  What could be the problem?  I'm using Ubuntu 15.10.

This is what I get when trying to install the driver.

---

### Post by weatherman2 on 2015-12-09
Brother provides a script to install the drivers for your printer.  Try downloading that and running it instead of using dpkg to install.  The script is called "linux-brprinter-installer-2.0.0-1" - easy to find on Brother's website.

---

### Post by shane_faulkinbury2 on 2015-12-09
I have that file also and when I double click on it, it wants to extract.  I extract it and this is what I get.  I do not know what to do from here.

---

### Post by howefield on 2015-12-09
From the folder that you extracted the file to.. try

```
sh linux-brpinter-installer-2.0.0-1
```

---

### Post by shane_faulkinbury2 on 2015-12-09
This is what I get when I try that!

---

### Post by howefield on 2015-12-09
Presumably you have the extracted file in the Downloads folder ?

Just had a look at the Brother driver page for that model, there are instructions on  the download page.

---

### Post by shane_faulkinbury2 on 2015-12-09
Sorry, I just saw I had to be root!  Done and installing now.  Will update on how it went.

I wonder how I get the printers IP?

I connect to my router and search for active devices and find 11 active and the only one I know is my PC!

---

### Post by howefield on 2015-12-09
> **shane_faulkinbury2 said:**
> I wonder how I get the printers IP?!

If the printer is installed correctly, you could try going to localhost:631 in your web browser, and details of you printer including connection information should be in the printers tab.

---

### Post by shane_faulkinbury2 on 2015-12-09
This is all I see !

Come on guys!  I really need to get this network printer going!  :confused:

---

### Post by gifford on 2015-12-10
Go to your router and get the list of connected devices, the Brother printer should start with BRN, get the ip address associated with it.

---

### Post by shane_faulkinbury2 on 2015-12-10
I finally got the .deb file and installed and then I go to print this page and nothing comes out of the printer!

Thanks Gifford, I see two BRW (e\which I do have two network Brother printers, but no BRN!

Finally, it was one of the BRW's just had to change the IP in System Settings!  :D

---

