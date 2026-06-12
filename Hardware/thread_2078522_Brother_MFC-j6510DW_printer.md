---
title: "Brother MFC-j6510DW printer"
date: 2012-10-31
forum: Hardware
---

### Post by Holeshole on 2012-10-31
Hi I am an absolute novice and afraid of terminal. I am trying to install a Brother MFC-j6510DW printer in Ubuntu 12.10 but it is not identified. I see on brother support that there is a new driver for Linux but dont know how to download and install. At present it is connected by USB but would like to connect wirelessly. Can anybody please help?

---

### Post by Wim Sturkenboom on 2012-10-31
Please provide a link to the website and download.

Do I understand you correctly that USB is working and you need to get the wifi part going?

---

### Post by Holeshole on 2012-10-31
No printer is not working even with usb cable

---

### Post by newb85 on 2012-10-31
Brother drivers take a little work to install, and the specific steps you need to take depend on you distribution and model.

MFC - implying that your device is both a printer and a scanner.  Get the printer drivers working first, and then move on to the scanner drivers.

Make sure you're starting at the [Brother Drivers for Linux]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html") page, and you're not trying to install drivers for some other OS.  Also, please note that Ubuntu uses dpkg and .deb files, and does *not* use rpm.  (This knowledge will be needed in selecting the right packages and procedures.)

Click the "Printer Driver" link in the Downloads section, and then select your model from the list.  Download both the cupswrapper and lpr drivers for your model.  Below the downloads for your model are links to instructions for both drivers.  Follow both sets of instructions consecutively.

That should get your printer up and running.  If you have any questions/run into problems, post them.  Otherwise, let us know that's working and we can move on to the scanner drivers.

---

### Post by newb85 on 2012-10-31
Actually, before trying the steps in my last post, try this:

From the Dash, pull up "Printing".  Hit "Add".  Select "Network Printer" and wait a few seconds for your printer to appear.  Select your printer and hit "Forward".  

I'm not sure what the steps will exactly be from there, but I'm guessing it will be obvious.  

(I gather installing this way works for newer Brother models.  It does not for my trusty ol' 3360C.)

---

### Post by pdc on 2012-10-31
and Brother now provide an installer script

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.0-1.gz&lang=English_lpr)

that ***should*** recognise your printer and do it all for you .....

---

### Post by newb85 on 2012-11-01
@pdc, could you post a link to the page before the license agreement page?

---

### Post by dwb814 on 2012-11-01
Hi,
The page with the listing of drivers is here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) The direct link for your printer is here:
  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6510DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6510DW) make sure you download the .DEB files for your model.

I don't know whether it will work for you or not, but when I was setting up my wireless printer, I just went to [http://localhost:631/printers](http://localhost:631/printers) clicked on "home" "Adding Printers and Classes" then "Add printer" it will ask for user name and password, which is your Ubuntu user name and pass. The list came up under "discovered network printer" and my printer was listed, no software installed. I selected the first one, walked through, tested it and it was done. I hope you have the same luck!

---

### Post by Holeshole on 2012-11-01
Have managed to download correct printer driver and the printer now works great  - even wirelessly. Many thanks.
Now all I have to do is get the scanner to work - any ideas?:razz:

---

### Post by pdc on 2012-11-01
go here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

second line down ................ scanner driver .............

click ............gives you .............

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html)

........very tricky bit next .........you need to work out which version of brscan your printer uses .............. ugh?? ...looks like brscan4 .......

......then you have to read the instructions......... for scanner-driver and scan-key-tool .......

and as you are using Ubuntu, it uses .deb packages and you need to know if you installed a 32bit or 64bit system;

**_[COLOR="Orange"]the important final piece you seem to need to complete is[/COLOR]_**

...........and I have copied and pasted what is below from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html)

    1. > [COLOR="Red"]sudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

    2. [COLOR="SeaGreen"]Add the following two lines to the **_[COLOR="Magenta"]end of the device list[/COLOR]_**[/COLOR]. (Before the line "
# The following rule will disable ..."):

    *on the other hand .............if there i*s 

               "LABEL="libsane_rules_end"", 

*add the following 2 lines* **[COLOR="Blue"]before[/COLOR]** "LABEL="libsane_rules_end"".

    The lines to be added--------------------------- 


    > [COLOR="Red"]# Brother scanners
    ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR]
     

    3. Restart the OS.

.......let us know if it is hard and how we can help ........

---

### Post by newb85 on 2012-11-01
> **Holeshole said:**
> Have managed to download correct printer driver and the printer now works great  - even wirelessly. Many thanks.

Well done.  Did you set it up using the install script, the Printing Dialog, or the directions on Brother's website?

---

### Post by gunnvor on 2013-06-03
Hi there,

Im now living in Germany and in Amazon [http://www.amazon.de/BROTHER-MFC-J6510DW-250Blatt-Papierkassette-Duplex/dp/B004HG9GPS/ref=sr_1_1?ie=UTF8&qid=1370292351&sr=8-1&keywords=brother+mfc-j6510dw#productDescription](http://www.amazon.de/BROTHER-MFC-J6510DW-250Blatt-Papierkassette-Duplex/dp/B004HG9GPS/ref=sr_1_1?ie=UTF8&qid=1370292351&sr=8-1&keywords=brother+mfc-j6510dw#productDescription) I have found q decent price.

Being on linux and on 13.04 Id like to ask if that printer, with all scanning, copying and faxing capabilities will work or if I should start looking for a HP.

Incidentally, what other brands would you recommend for a linux environment?

cheers

---

### Post by pdc on 2013-06-03
Yes, Brother supply debian package drivers for you

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6510DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6510DW)

one installs the lpr driver first and then the cupswrapper driver afterwards;

instructions on the above link

Brother also supply an installer script

this thread

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527) in post #5 tells you how to do it.....some find that easier as the script should do all for you

___________________________________________________________________________

The scanner side needs separate drivers

the MFC_J6510DW is what is called a brscan4 model so one downloads those deb drivers

You need to tell your system about its newly acquired scanner; after you install the brscan4 drivers

if one **also** downloads [COLOR="#008000"]brother-udev-rule-type1-1.0.0-1.all.deb[/COLOR]

as described here [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04)

---

