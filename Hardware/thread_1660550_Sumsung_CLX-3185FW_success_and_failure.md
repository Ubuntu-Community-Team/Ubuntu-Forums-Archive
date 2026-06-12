---
title: "Sumsung CLX-3185FW: success and failure"
date: 2011-01-05
forum: Hardware
---

### Post by fabzzap on 2011-01-05
I tried to install the USB printer/scanner Samsung CLX-3185FW on my 64-bit Ubuntu 10.10 system.

The printer was easy: the Foomatic printer driver for the CLX-3175 works.

The scanner was less straightforward. The drivers downoaded from Samsung's official site have all sort of problems with 32- and 64-bit libraries, and they copy files all over the place.  Browsing the forums, someone was reporting success with other models and the Sane backend xerox_mfp. Actually, /etc/sane.d/xerox_mfp.conf already contained the lines

#Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342a

So, following the forums' advice, I modified /etc/sane.d/xerox_mfp.conf by adding 

#Samsung CLX-3185FW
usb 0x04e8 0x343d

and /lib/udev/rules.d/40-libsane.rules by adding

# Samsung CLX-3185FW
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

And yet, no success: sane-find-scanner could see the scanner but scanimage -L or simple-scan couldn't.

Then, launching the command

SANE_DEBUG_XEROX_MFP=1 scanimage -L

the output was more descriptive

[sanei_debug] Setting debug level of xerox_mfp to 1.
[xerox_mfp] dev_open: sanei_usb_open(libusb:001:003): Access to resource has been denied

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

(note that lsusb listed the device as
Bus 001 Device 003: ID 04e8:343d Samsung Electronics Co., Ltd 
).

The workaround is to launch scanimage -L and simple-scan with sudo: in that case, the scanner works. But is there a way to let normal users, or even the user controlling the console at that time, use the scanner?

---

### Post by fabzzap on 2011-01-08
For some reasons, there was no group "scanner" in the system.

System->Administration->Users and groups->Manage groups, I added a group named "scanner" and added my account to it, then logged out and in again.

---

### Post by kem on 2011-01-11
I just installed CLX-3185 on Maverick and everything went smooth except the final step. In particular, I followed install guide ...
1) I installed all required applications (xsane, ghostscript)
2) started install script in terminal as root (using sudo)
3) Next - Next -Next

The installation wizard crashed in the very last step and even shut down the Ubuntu. However,  after restart everything worked very well including scanner. Maybe this description will help to somebody.

Cheers

---

### Post by kubug on 2011-04-08
I recently installed this printer for my parents on Ubuntu 10.10.

Samsung made it a pretty easy install. Download the drivers and utilities here:

[http://www.samsung.com/hk_en/consumer/computer-peripherals/printers-multifunction/color-laser-multifunction-printers-faxes/CLX-3185FW/XSS/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/hk_en/consumer/computer-peripherals/printers-multifunction/color-laser-multifunction-printers-faxes/CLX-3185FW/XSS/index.idx?pagetype=prd_detail&tab=support)

And follow this guide step-by-step (it's easy and detailed):

[http://skp.samsungcsportal.com/integrated/popup/FaqDetailPopup.jsp?cdsite=hk_en&seq=297862](http://skp.samsungcsportal.com/integrated/popup/FaqDetailPopup.jsp?cdsite=hk_en&seq=297862)

---

### Post by kubug on 2011-04-08
Sorry fabzzap,

I didn't notice the top part of your comment when you mention that you DID try to use the drivers from Samsung. Sorry you had trouble. My parents Ubuntu was 32 bit, so maybe that's why I had no issues.

---

### Post by kem on 2011-04-10
> **kubug said:**
>  My parents Ubuntu was 32 bit, so maybe that's why I had no issues.

I installed it on 64 bit machine. Seems to be working as well.

---

### Post by fabzzap on 2011-05-18
After upgrade to 11.04, things stopped working. After a little head-banging, I found out (by reading the last lines of the file /lib/udev/rules.d/40-libsane.rules) that udev uses the command /bin/setfacl to grant access to the device, but it was not installed!

sudo apt-get install acl

solved

---

### Post by yamushk on 2011-10-19
Once I installed the driver - I lost the wireless internet connection. I couldn't get the wireless connection to the printer work, but the wireless connection to the internet (from the computer) didn't work either.
Only solution was to uninstall driver. Did anyone experience this problem as well?
Miriam

---

### Post by DrMark666 on 2011-10-30
Ubuntu 11.10 + CLX-3185:

Unified driver from Samsung installed, but no go for scanner. I had a little fun finding the printer initially, but it found it itself after a while.

Edit xerox_mfp.conf, add the Samsung lines:
#Samsung CLX-3185
usb 0x04e8 0x343d

Added myself to scanner group, and all was well.

Unity - I have yet to find the GUI user/group editor in this mess, and it didn't appear after a gnome install, so I did the group addition by
usermod -a -G scanner mark
from a terminal (as root, again)

---

### Post by Antaeus50 on 2011-11-20
I have a Samsung CLX-3185. I have a printing problem. Some characters print as ,,, or "
So on my prints I see text like: Wr"te all "ords you ,know. In stead of: Write all words you know.
Who knows how to fix this.
I'm not a linux specialist, so please tell me step for step what to do.

---

### Post by TheSurak on 2011-12-30
Hello, Antaeus50, this could be data communication error. Are you using a good USB 2.0 cable?

---

### Post by TheSurak on 2011-12-30
As fabzzap said, printer works with foomatic for CLX-3175. For those who don't understand what this means, simply turn on the printer, connect it through a good USB 2.0 cable and it is detected. Then (for Kubuntu at least) go to configurations -> printers -> add new printer -> choose samsung -> choose clx-3175 -> choose the recommended driver.

I am using Kubuntu Oneiric 11.10.

Now I'm going to the scanner part, then will try to print through wi-fi.

BTW setting up wireless connection is VERY easy with a modern router. Simply press the button on your router then press WPS button in the CLX-3185FW for 2 seconds. Piece of cake.

---

### Post by baltas125 on 2012-02-11
**Instructions how to set-up samsung CLX-3185FW**
After executing instructions I have successfully installed CLX-3185FW over the network. It prints and scans over the network.
I have made it on Ubuntu 11.10,  32bit;

Before installing you MUST REMOVE any other previously installed drivers for Samsung.
Originally taken from: [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html)

Step 1 (edit sources):
sudo gedit /etc/apt/sources.list
Add lines:
#samsung drivers
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

Step 2 (install authentication key) :
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -

Step 3 (update sources):
sudo apt-get update

Step 4 (install packages):
Open ubuntu software center and install one by one all packaged that start with " samsungmfp-", excepting:
 - first install packages which do not have the word "legacy";
 - do not install packages which offer you to remove any other packages;
 - Do not install "samsungmfp-parallel" it should only be installed if your printer is actually connected via a parallel port;

Step 5a (check if you are in lp group):
Run in Terminal:
cat /etc/group | grep lp

If your accaunt name is next to lp, everything is ok, else add yourself to lp group, e.g. execute Step 5b.

Step 5b (add yourself into lp group if needed)
sudo usermod -a -G lp USERNAME

( more information about groups: [http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/))

That's it! Now you can search for your printer in network and add it as clx-3180 series and it will work.

P.S. Previously I have made some changes to some files. But I do not know if it has any impact. 
If you have executed the five step above and still no luck, try making those changes:
/etc/sane.d/xerox_mfp.conf 
lines added:
#Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342a

/etc/sane.d/xerox_mfp.conf 
lines added: 
#Samsung CLX-3185FW
usb 0x04e8 0x343d

/lib/udev/rules.d/40-libsane.rules 
lines added:
# Samsung CLX-3185FW
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

---

### Post by adelich on 2012-04-03
I've installed using the above instructions. everything is perfectly working. But i can not get, how to make the "scan to pc"  button working. Could anybody help me, please?

---

### Post by DRanged on 2012-06-30
> **adelich said:**
> I've installed using the above instructions. everything is perfectly working. But i can not get, how to make the "scan to pc"  button working. Could anybody help me, please?

You can only initiate a scan FROM your PC, especially if you hooked the printer up via network. Scan to PC might work if you have hooked it up via usb to your PC.

Kind regards
DRanged

---

