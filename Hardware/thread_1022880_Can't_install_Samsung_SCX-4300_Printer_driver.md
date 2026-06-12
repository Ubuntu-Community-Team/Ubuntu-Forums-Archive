---
title: "Can't install Samsung SCX-4300 Printer driver"
date: 2008-12-27
forum: Hardware
---

### Post by alrofaee on 2008-12-27
Hello everybody

I bought the Samsung SCX-4300 Printer and I couldn't install the driver successfully. I got some errors of my installation. Please, any help?:confused:

---

### Post by alrofaee on 2008-12-28
Please, any one can solve my problem?

---

### Post by yahs on 2008-12-28
I have a scx-4100 which installs fine (thanks to Tweedledee on Tutorials & Tips - HOWTO Install Samsung Unified Printer Driver). On the samsung web site under download there is a file "Unified Linux Driver (ver.2.00.97)" which shows for scx-4100 and scx-4200 but not for scx-4300 so I presume there is a linux file supplied with the printer. If you check out the above link and have a similar file you should be okay. If you need help, then I can explain how I got my printer to print and scan under hardy.

---

### Post by alrofaee on 2008-12-29
> **yahs said:**
> I have a scx-4100 which installs fine (thanks to Tweedledee on Tutorials & Tips - HOWTO Install Samsung Unified Printer Driver). On the samsung web site under download there is a file "Unified Linux Driver (ver.2.00.97)" which shows for scx-4100 and scx-4200 but not for scx-4300 so I presume there is a linux file supplied with the printer. If you check out the above link and have a similar file you should be okay. If you need help, then I can explain how I got my printer to print and scan under hardy.

Thank you my friend to provide your assist to me, but could you please explain how to install the driver from the scratch? I have the CD that comes with the printer.

Regards

---

### Post by yahs on 2008-12-30
Can you tell me about the driver on the cd. Samsung unified drivers on the web end with tar.gz. does your driver have this extension?

As far as I understand all Samsung Multifunction printers use the Unified Linux Driver. I have a SCX-4100 and I downloaded from the samsung site. Scx-4200 uses it but no driver appears for scx-4300. Reading reviews of samsung printers (4200 and 4300)there does not seem to be much difference between them so maybe the 4200 driver will work.

Once you have your file, Save it (on the desktop or in Home folder) and extract it by right clicking on the file and selecting “extract here”. A folder names cdroot will appear. You might need to set permissions, but if you just want to try first, open a terminal and go to the directory where you extracted the file (cd Desktop/cdroot/ or cd home/cdroot).
Under cdroot there is a directory  Linux go into this directory and then type this command 

sudo ./install.ch (the dot and the / are needed). If all goes well the samsung installer will take over and you should be able to print.

Let me know how you get on as I had to do a lot more to get my printer and scanner working

---

### Post by alrofaee on 2008-12-30
when I provided the PPD file for my printer, I got a message: Stooped - Filter "rastertosamsungspl" for printer "SCX-3400 - Series" not avalible: No such file or directory.

Then I tried to install the filter "rastertosamsungspl", there is nothing happened. That's mean couln't install this filter.

---

### Post by yahs on 2008-12-30
Not sure what you mean when you say "when I provided the PPD file for my printer," How did you provide it? what is the name of the file you are providing?

---

### Post by apillai on 2008-12-31
> **alrofaee said:**
> when I provided the PPD file for my printer, I got a message: Stooped - Filter "rastertosamsungspl" for printer "SCX-3400 - Series" not avalible: No such file or directory.

Then I tried to install the filter "rastertosamsungspl", there is nothing happened. That's mean couln't install this filter.

I was able to configure SCX 4300 with the steps mentioned at Volatile Yard (vyvy) [http://www.vyvy.org/main/node/146](http://www.vyvy.org/main/node/146). yahs also mentions this in answer to your question. I can summarize the steps for Ubuntu 8.04 on a Dell Inspiron (Pentium Duo Core 32 bit) with SCX 4300  connected to a USB port, since there are minor variations from the steps by vyvy:

(a) Enable /proc/bus/usb/ and support as suggested - this is critical for your scanner and printer to work. (Strictly speaking, without this fix, you might get printing up, but never the scanning)

(b) Download and install the printer driver from Samsung as suggested. Dont worry that there is no special downloadable for SCX 4300, use their 2.00.97 Unified Linux Driver - this is available from the downloads section for SCX 4200. As of 30-Dec-08, the url was [http://downloadcenter.samsung.com/content/DR/200810/20081028145509765/UnifiedLinuxDriver.tar.gz](http://downloadcenter.samsung.com/content/DR/200810/20081028145509765/UnifiedLinuxDriver.tar.gz)

(c) Setup the printer configuration as suggested using the Samsung Config Manager (You will see this as icon on your desktop). Choose SCX 4200 as the printer driver from the installed Samsung printer drivers, since there are no special drivers available for SCX 4300. If the system prompts you to replace or overwrite the PPD file, ask it to replace the PPD file - avoid overwriting. The choice of device URI as MFP USB Port #0, i.e., mfp:/dev/mfp/4 is critical (for your scanner to work). 

Alternatively, you can configure printer from Ubuntu --> Administration --> Printing and choose Samsung SCX 4200 as the driver and mfp:/dev/mfp/4 as the device uri.

(d) Fix the scanner driver as suggested. You can find a README inside the zip file from Jacobo Tarrio which explains how to safely replace usr/lib/libmfp.so.1.0.1 by verifying the md5sum. Do not forget to add yourself  to group lp, logout and login again - otherwise XSane will continue to crash. You could reboot the machine instead of a logout/login.

By this time, you should be able to print and scan from your Ubuntu system. Hope this helps. If you are technically inclined, vyvy's post tells you accurately why the installation is so long winded.

-apillai

---

### Post by Obsolete Zero on 2009-03-06
hey,

I recently bought the SCX-4300 and am running the ubuntu 8.10 kernel.

My problem is, apperently a new installer has been made as the printer is now recognized as scx-4300 and is using scx-4300 drivers.

The path from that other website now says: version not recognized, don't change it.

However xsane doesn't support the scx-4300 drivers. Does anyone have a clue which scanning program does support this mfp? the mfp:/dev/mfp/4 is also not accepted for some reason........

it keeps restoring the printer to URI:

usb://Samsung/SCX-4300%20Series

anyone have a clue?

---

### Post by yahs on 2009-03-07
Hi 
Hope this is useful

I have a scx4100 working (print & scan) on Ubuntu 8.04 since June2008, which I installed thanks to this link ( HOWTO Install Samsung Unified Printer Driver by Tweedledee)
I have just installed 8.10 on a separate partition and did a printer installation as follows.

The original installation file is no longer available (I searched for scx4100 on the Samsung Download site), so I downloaded and installed latest UnifiedLinuxDriver.tar.gz and extracted to desktop.

Changed directory to cdroot/Linux
sudo ./install.sh

The GUI installer failed but I got this message

GUI mode installer execution failed, proceeding in text mode
****  Running text mode install
****  Press Enter to continue or q and then Enter to quit: 

**** Non-priviliged users found:
nobody sk
****  Are you going to use USB-connected devices ?
****  If yes, users allowed to scan or manage printers should be added to lp
****  group. The list of non-privileged users proposed for addition is shown above.
****  Press y and then Enter to add users or Enter to leave lp group intact: y

****  Print drivers for the following device models available:
CLP-300splc CLP-310splc CLP-350ps CLP-500splc CLP-510splc CLP-550ps CLP-600splc CLP-610splc CLP-650ps CLP-660ps CLP-770ps CLX-216xsplc CLX-3160splc CLX-3170splc CLX-6200ps CLX-6240ps CLX-8380ps mfp560 mfp750 ML-1450ps ML-1510spl2 ML-1520spl2 ML-1610spl2 ML-1630spl2 ML-1630wspl2 ML-1640spl2 ML-1710spl2 ML-1740spl2 ML-1750spl2 ML-2010spl2 ML-2150ps ML-2150spl2 ML-2240spl2 ML-2245spl2 ML-2250spl2 ML-2510spl2 ML-2550ps ML-2550Sps ML-2550Sspl2 ML-2560ps ML-2570ps ML-2850ps ML-2855ps ML-3050spl2 ML-3470ps ML-3560spl2 ML-4050DMVps ML-4050ps ML-4550ps ML-6060ps ML-7300ps ML-8x00ps scx4100 scx4200 scx4300 scx4500 scx4500w scx4725 scx4x16 scx4x20 scx4x21 scx4x24 scx4x26 scx4x28ps scx5312f scx5635ps scx5835ps scx5x30 scx6x20PCL scx6x20 scx6x20PS scx6x22ps scx6x45ps scx6x55ps sf531p
****  Please enter model to install and press Enter: scx4100
INFO: Installing MFP port and SANE backend libraries ...
INFO: Installing GUI lpr ...
INFO: Fixing file ownership and permissions ...
INFO: Registering SANE backend ...
INFO: Registering CUPS printer ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
INFO: CUPS restart OK
INFO: Creating menu entries ...
INFO: Adding users to lp group ...
INFO: Finishing installation ...
****  Text mode install finished

The Samsung Unified Driver Icon appeared on the Desktop and 2 printers appeared (SCX-4100 Series) and (scx4100)
The SCX-4100 Series was found by Ubuntu before downloading Printer Driver and uses URI:usb://Samsung/SCX-4100%20Series.
The scx4100 was installed by Downloaded printer driver and uses URI:mfp:/dev/mfp.4

Scanner appears on sfmp:SAMSUNG SCX-4100 Series on USB:0

I can use either printer (I have now deleted scx4100) and I can scan using either Samsung Unified Utility or Xsane or Gimp.

The installation was the easiest one I've done so far, the original one on Ubuntu 804 was a pain

SCX4300 appears in the list so selecting that will (hopefully) work as well as it does for my scx4100

---

### Post by Obsolete Zero on 2009-03-08
hi yahs,

thanks for the tip, i guess we had the same install. the only problem i have is that xsane apperently does not support the newer scx-4300 mfp. :(

So i use the Samsung scan util instead! it works :)

---

