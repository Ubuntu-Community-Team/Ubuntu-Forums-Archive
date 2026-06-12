---
title: "Newly-installed Brother MFC printer is hokey - weird"
date: 2012-09-10
forum: Hardware
---

### Post by Catlike on 2012-09-10
Following many instructional posts here and elsewhere, and tearing my hair out, I finally got my new printer sort of working.

It is a Brother MFC-J425W printer/scanner. 
I have connected it via USB cable.

The computer sees the printer OK. 
I downloaded the drivers at 

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J425W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J425W)

and got a "tool" from Brother, to unzip and install them, at

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

Much tribulation, but I got (I think) the drivers installed. (Maybe not properly -- as results below attest.)

I try to print a page, and the printer makes promising noises, then stops and makes a sound like a falling artillery shell. I check the print queue and see the job listed and the staus is (this is weird) "Held". If I click on the print job line, then click "Release", the job continues. However, this results in a page on which the text is chopped off in mid-line.

I found (by accident) that if I just wait a long time, the print job resumes of its own accord. It just spat out a document I sent to queue 10 minutes ago. Then it decided to print a second copy. These copies were complete -- not chopped off.

Why does the print job get "Held" for 10 or more minutes? 

How to fix this?

Thanks.

---

### Post by pdc on 2012-09-10
I wonder if you paste this

[http://localhost:631/printers/](http://localhost:631/printers/)

into a browser page: it opens CUPS on your system; is the printer driver installed?

good that you used the installer

[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.4-1.gz&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.4-1.gz&lang=English_lpr)

I had got the impression from others that it worked well; 

> Much tribulation, but I got (I think) the drivers installed

can you expand on all this.........what problems.......

...........did the installer search for and download the needed drivers; by itself?

Ubuntu provide guidance on debugging printing problems

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

if you want to work through this ........

---

### Post by Catlike on 2012-09-11
> **pdc said:**
> I wonder if you paste this

[http://localhost:631/printers/](http://localhost:631/printers/)

into a browser page: it opens CUPS on your system; is the printer driver installed?



The CUPS page does show this: 
[&#9660; Queue Name &#9660;]("http://localhost:631/printers/?QUERY=&WHICH_JOBS=&FIRST=%7BFIRST%7D&ORDER=dec")DescriptionLocationMake and ModelStatus    [Brother-MFC-J425W]("http://localhost:631/printers/Brother-MFC-J425W")Brother MFC-J425Wgreg-GT5628Brother DCP-110C CUPS v1.1Idle  [MFCJ425W]("http://localhost:631/printers/MFCJ425W")MFCJ425W
Brother MFC-J425W CUPSIdle
Apparently, I installed it twice. I don't think that's a problem in itself, as I have set one of them -- the second one -- as default, and that's the one the print job always goes to, unless I specify otherwise.

> **pdc said:**
> ...........did the installer search for and download the needed drivers; by itself?
Yes.
Thank you.

---

### Post by Catlike on 2012-09-11
> **pdc said:**
> Ubuntu provide guidance on debugging printing problems

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

if you want to work through this ........

On the above-linked web page, the first thing for USB-connected printer is make sure it's connected, and it is. The second thing they say is to open the terminal and run "lsmod | grep usb" to see that the USB kernels (?) are loaded. I got this feedback:
[B]usblp                  17885  0 
snd_usb_audio         101566  1 
snd_usbmidi_lib        24603  1 snd_usb_audio
snd_hwdep              13276  2 snd_hda_codec,snd_usb_audio
snd_pcm                80845  4 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_rawmidi            25424  2 snd_usbmidi_lib,snd_seq_midi
snd                    62064  22 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
usbhid                 41906  0 
hid                    77367  1 usbhid
usb_storage            39646  1 [/B]

Does this all mean "Yes, the USB kernels are installed"?
What is a USB kernel?
Thank you.

---

### Post by pdc on 2012-09-12
I think I would tend to move on to the next steps...

> **Unplug the USB printer cable from your computer and enter this command**:

$ tail -f /var/log/syslog 

**Reconnect the USB printer cabl**e, you should see some messages appearing.
*Press Ctrl-C to stop the logging*.

Check whether the printer gets correctly detected by the USB subsystem and determine its USB vendor/product IDs and the USB bus and device addresses:

$ lsusb

Note: The USB bus and device addresses change if you turn off or unplug the printer. Please re-run this command if needed.

**Check whether the device files for the printer get created and the ownerships** ("root lp") **and permissions** (non-HP: "crw-rw-r--", HP: "crw-rw-r--+") **are correctly set**:
$ ls -l /dev/usb/lp* /dev/bus/usb/*/*

---

### Post by Catlike on 2012-09-12
Thank you. I disconnected the printer USB cable, then re-connected. Here are the last few messages that were logged:
"Sep 12 18:01:16 greg-GT5628 udev-configure-printer: URI of detected printer: usb://Brother/MFC-J425W?serial=BROF2F320777, normalized: brother mfc j425w serial brof2f320777
Sep 12 18:01:16 greg-GT5628 udev-configure-printer: Queue ipp://localhost:631/printers/MFCJ425W has matching device URI
Sep 12 18:01:16 greg-GT5628 udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/MFCJ425W
^C"

When I entered the command "$ lsusb" , I got these results:
"Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 002 Device 006: ID 04f9:028f Brother Industries, Ltd 
Bus 002 Device 005: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 003 Device 002: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 005 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 007 Device 002: ID 0461:4d16 Primax Electronics, Ltd "

I guess this tells me that the printer is on Bus 002, and it is Device 6. 
I entered the command "$ ls -l /dev/usb/lp* /dev/bus/usb/*/ ", the resulting messages were:
"crw-rw-r-- 1 root root 189,   0 Sep 12 12:57 /dev/bus/usb/001/001
crw-rw-r-- 1 root root 189, 128 Sep 12 12:57 /dev/bus/usb/002/001
crw-rw-r-- 1 root root 189, 129 Sep 12 12:57 /dev/bus/usb/002/002
crw-rw-r-- 1 root root 189, 132 Sep 12 12:57 /dev/bus/usb/002/005
crw-rw-r-- 1 root lp   189, 133 Sep 12 18:01 /dev/bus/usb/002/006
crw-rw-r-- 1 root root 189, 256 Sep 12 12:57 /dev/bus/usb/003/001
crw-rw-r-- 1 root root 189, 257 Sep 12 12:57 /dev/bus/usb/003/002
crw-rw-r-- 1 root root 189, 384 Sep 12 12:57 /dev/bus/usb/004/001
crw-rw-r-- 1 root root 189, 512 Sep 12 12:57 /dev/bus/usb/005/001
crw-rw-r-- 1 root root 189, 513 Sep 12 12:57 /dev/bus/usb/005/002
crw-rw-r-- 1 root root 189, 640 Sep 12 12:57 /dev/bus/usb/006/001
crw-rw-r-- 1 root root 189, 768 Sep 12 12:57 /dev/bus/usb/007/001
crw-rw-r-- 1 root root 189, 769 Sep 12 12:57 /dev/bus/usb/007/002
crw-rw-r-- 1 root root 189, 896 Sep 12 12:57 /dev/bus/usb/008/001
crw-rw---- 1 root lp   180,   0 Sep 12 18:01 /dev/usb/lp0 "

So there is the ownership and I see permissions as listed for non-HP. (No idea why the last line is different.) 
I will move on to the next steps.

---

### Post by Catlike on 2012-09-12
On the printer de-bugging page, the next steps (and my results) are as follow.

"Determine the printer's device ID strings: 
 $ sudo usb_printerid /dev/usb/lp0 
 $ sudo usb_printerid /dev/usb/lp1"

For the first command, I got back:
"GET_DEVICE_ID string:
MFG:Brother;CMD:HBP,BRPJL,URF;MDL:MFC-J425W;CLS:PRINTER;CID:Brother IJ Type2;URF:SRGB24,W8,CP1,IS1-7,MT1-8-11,OB0,PQ4,RS300,OFU0; "

(What does this tell me?)

For the second command, I got back:
"Error: No such file or directory: can't open '/dev/usb/lp1' "

(Aha! Is this the problem?)

Finally, there is the command: 
"Find out if your printer gets detected by CUPS: 
 $ lpinfo -v "

Result:
"network https
network http
network ipp14
network ipp
direct cnijusb:/dev/usb/lp0
network ipps
network beh
network lpd
network socket
direct scsi
direct hp
direct hpfax
direct usb://Brother/MFC-J425W?serial=BROF2F320777
network smb
network dnssd://Canon%20MX860%20series%20(00.1e.8f.76.16.14)%20%40%20Desktop._ipp._tcp.local/cups
network cnijnet:/00-1E-8F-76-16-14 "

It's mysterious, but I *think* it's saying it detects the printer via CUPS. Yes?

Thank you.

---

### Post by Catlike on 2012-09-12
I do not know what the heck changed, but the printer is working properly now. Just running all those diagnostics must have, um, poked something loose. 

Should I consider this solved?  Is this set of steps useful to someone else?

---

