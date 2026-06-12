---
title: "Lack of support for Dell Photo All-in-One Printer 962"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by arunsub on 2005-10-17
I bought a Dell Photo All-in-One Printer 962 2 days back. When i tried to add a new printer, it recognised the Dell AIO 962, but when i went to driver's section, I got only 2 printer models listed under DELL and nothing for AIO 962. Does anyone know where and how to get the driver for this printer?

---

### Post by arunsub on 2005-10-17
no one knows where to get the driver?

---

### Post by ecobuntu on 2005-10-17
[http://www.finebushpeople.net/index.php?option=content&task=view&id=65&Itemid=98/](http://www.finebushpeople.net/index.php?option=content&task=view&id=65&Itemid=98/)

This is worth a try.  I know that Lexmark makes Dell printers.  I have a Dell All In One 920 and this driver works.  It will probably work for you as well.  Cause it's probably a Z600 series printer.

---

### Post by arunsub on 2005-10-18
Thankk you. I'll give that a try. :)

---

### Post by arunsub on 2005-10-18
I tried as per the instructions given on the link. After rebooting, I found the Z600 driver under Lexmark, so adter selecting the printer from the first screen, i pressed next and selected Lexmark and Z600 driver that i installed and created the new printer. I then tried to prin a test page and it didn't work. The job said printing, but nothing happened. I waited for a min or two and cancelled the job. Any idea how to make it work?

---

### Post by arunsub on 2005-10-18
I found out from Google group that Dell AIO 962 printer is Lexmark X7170. [Here]("http://groups.google.com/group/comp.periphs.printers/browse_thread/thread/3a8246d8713ec959/35795cfb76edc101?lnk=st&q=dell+962+printer+driver+for+linux&rnum=1&hl=en#35795cfb76edc101") is the link. I downloaded the driver from Lexmark site for Redhat. I then untarred it and ran ./configure. I got the following error when i entered make. 

making all in include
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/include'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/include'making all in sanei
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/sanei'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/sanei'
making all in lexmark
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/lexmark'
g++  -DPATH_SANE_CONFIG_DIR=/usr/local/etc/sane.d         -DPATH_SANE_DATA_DIR=/usr/local/share           -DV_MAJOR=1 -DV_MINOR=0  -c -o llpddk.o llpddk.cpp
llpddk.cpp:47:37: error: lexmark-H/scannerdevice.h: No such file or directory
In file included from llpddk.cpp:51:
saneportmonitor.h:51:35: error: lexmark-H/portmonitor.h: No such file or directory
In file included from llpddk.cpp:52:
scanerrorcommunicator.h:47:42: error: lexmark-H/scanerrorinterface.h: No such file or directory
saneportmonitor.h:55: error: expected class-name before ‘{’ token
saneportmonitor.h:62: error: ‘PM_Error’ does not name a type
saneportmonitor.h:63: error: ‘PM_Error’ does not name a type
saneportmonitor.h:71: error: ‘PM_Error’ does not name a type
saneportmonitor.h:73: error: ‘PM_Error’ does not name a type
saneportmonitor.h:75: error: ‘PM_Error’ does not name a type
saneportmonitor.h:78: error: ‘PM_Error’ does not name a type
saneportmonitor.h:80: error: ‘PM_Error’ does not name a type
scanerrorcommunicator.h:49: error: expected class-name before ‘{’ token
scanerrorcommunicator.h:54: error: ‘ScanErrorInterface’ has not been declared
scanerrorcommunicator.h:54: error: ‘ScannerError’ has not been declared
scanerrorcommunicator.h:55: error: ‘ScanErrorInterface’ has not been declared
scanerrorcommunicator.h:55: error: ‘UserDecision’ does not name a type
llpddk.cpp:56: error: expected constructor, destructor, or type conversion before ‘*’ token
llpddk.cpp: In function ‘SANE_Status llpddk_init()’:
llpddk.cpp:74: error: ‘sd’ was not declared in this scope
llpddk.cpp:74: error: expected type-specifier before ‘ScannerDevice’
llpddk.cpp:74: error: expected `;' before ‘ScannerDevice’
llpddk.cpp: In function ‘void llpddk_attach_matching_devices(const char*, SANE_Status (*)(const char*))’:
llpddk.cpp:90: error: ‘class SanePortMonitor’ has no member named ‘PM_AttachDevice’
llpddk.cpp: In function ‘void llpddk_destroy()’:
llpddk.cpp:99: error: ‘sd’ was not declared in this scope
llpddk.cpp:100: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
llpddk.cpp: In function ‘SANE_Status llpddk_open_device(const SANE_Char*)’:
llpddk.cpp:114: error: ‘PortMonitor’ has not been declared
llpddk.cpp:114: error: ‘PM_Error’ was not declared in this scope
llpddk.cpp:114: error: expected `;' before ‘pmerr’
llpddk.cpp:116: error: ‘pmerr’ was not declared in this scope
llpddk.cpp:116: error: ‘class SanePortMonitor’ has no member named ‘PM_SetDeviceName’
llpddk.cpp:117: error: ‘PortMonitor’ has not been declared
llpddk.cpp:117: error: ‘PM_ERR_SUCCESS’ was not declared in this scope
llpddk.cpp:120: error: ‘class SanePortMonitor’ has no member named ‘PM_Open’
llpddk.cpp:121: error: ‘PortMonitor’ has not been declared
llpddk.cpp:121: error: ‘PM_ERR_SUCCESS’ was not declared in this scope
llpddk.cpp: In function ‘void llpddk_close_device()’:
llpddk.cpp:130: error: ‘class SanePortMonitor’ has no member named ‘PM_Close’
llpddk.cpp: In function ‘SANE_Status llpddk_start_scan(Option_Value*)’:
llpddk.cpp:138: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:138: error: ‘SD_ErrCode’ was not declared in this scope
llpddk.cpp:138: error: expected `;' before ‘sderr’
llpddk.cpp:139: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:139: error: ‘SD_ScanProp’ was not declared in this scope
llpddk.cpp:139: error: expected `;' before ‘sdprop’
llpddk.cpp:142: error: ‘sdprop’ was not declared in this scope
llpddk.cpp:142: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:142: error: ‘SD_EIGHT_BPC’ was not declared in this scope
llpddk.cpp:145: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:145: error: ‘SD_RGB_CHANNEL’ was not declared in this scope
llpddk.cpp:148: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:148: error: ‘SD_MONO_CHANNEL’ was not declared in this scope
llpddk.cpp:151: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:151: error: ‘SD_ERROR_DIFFUSION’ was not declared in this scope
llpddk.cpp:153: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:153: error: ‘SD_THRESHOLD’ was not declared in this scope
llpddk.cpp:157: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:157: error: ‘SD_PHOTO’ was not declared in this scope
llpddk.cpp:159: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:159: error: ‘SD_TEXT_DOCUMENT’ was not declared in this scope
llpddk.cpp:161: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:161: error: ‘SD_MIXED’ was not declared in this scope
llpddk.cpp:164: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:164: error: ‘SD_UNCOMPRESSED’ was not declared in this scope
llpddk.cpp:170: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:170: error: ‘SD_75_DPI’ was not declared in this scope
llpddk.cpp:173: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:173: error: ‘SD_100_DPI’ was not declared in this scope
llpddk.cpp:176: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:176: error: ‘SD_150_DPI’ was not declared in this scope
llpddk.cpp:179: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:179: error: ‘SD_300_DPI’ was not declared in this scope
llpddk.cpp:182: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:182: error: ‘SD_600_DPI’ was not declared in this scope
llpddk.cpp:185: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:185: error: ‘SD_1200_DPI’ was not declared in this scope
llpddk.cpp:188: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:188: error: ‘SD_2400_DPI’ was not declared in this scope
llpddk.cpp:191: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:191: error: ‘SD_4800_DPI’ was not declared in this scope
llpddk.cpp:194: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:194: error: ‘SD_9600_DPI’ was not declared in this scope
llpddk.cpp:197: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:197: error: ‘SD_19200_DPI’ was not declared in this scope
llpddk.cpp:200: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:240: error: ‘sderr’ was not declared in this scope
llpddk.cpp:240: error: ‘sd’ was not declared in this scope
llpddk.cpp:241: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:241: error: ‘SD_OK’ was not declared in this scope
llpddk.cpp: In function ‘long int llpddk_read_scan_data(SANE_Byte*, SANE_Int, int*)’:
llpddk.cpp:252: error: ‘sd’ was not declared in this scope
llpddk.cpp: In function ‘SANE_Status llpddk_abort_scan()’:
llpddk.cpp:261: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:261: error: ‘SD_ErrCode’ was not declared in this scope
llpddk.cpp:261: error: expected `;' before ‘sderr’
llpddk.cpp:264: error: ‘sderr’ was not declared in this scope
llpddk.cpp:264: error: ‘sd’ was not declared in this scope
llpddk.cpp:265: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:265: error: ‘SD_OK’ was not declared in this scope
llpddk.cpp: In function ‘SANE_Status llpddk_end_scan()’:
llpddk.cpp:274: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:274: error: ‘SD_ErrCode’ was not declared in this scope
llpddk.cpp:274: error: expected `;' before ‘sderr’
llpddk.cpp:277: error: ‘sderr’ was not declared in this scope
llpddk.cpp:277: error: ‘sd’ was not declared in this scope
llpddk.cpp:278: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:278: error: ‘SD_OK’ was not declared in this scope
llpddk.cpp: In function ‘SANE_Status llpddk_get_adf_status(unsigned char*)’:
llpddk.cpp:287: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:287: error: ‘SD_ErrCode’ was not declared in this scope
llpddk.cpp:287: error: expected `;' before ‘sderr’
llpddk.cpp:290: error: ‘sderr’ was not declared in this scope
llpddk.cpp:290: error: ‘sd’ was not declared in this scope
llpddk.cpp:293: error: ‘ScannerDevice’ has not been declared
llpddk.cpp:293: error: ‘SD_OK’ was not declared in this scope
llpddk.cpp: In function ‘void llpddk_report_error(int)’:
llpddk.cpp:302: error: ‘ScanErrorInterface’ has not been declared
llpddk.cpp:302: error: ‘ScannerError’ was not declared in this scope
make[1]: *** [llpddk.o] Error 1
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/lexmark'make: *** [all-recursive] Error 1

I then did sudo make install and got the following:
making install in include
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/include'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/include'making install in sanei
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/sanei'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/sanei'
making install in lexmark
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/lexmark'
make[1]: Nothing to be done for `install'.
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/lexmark'making install in backend
make[1]: Entering directory `/home/prabha/Download/X7170SampleSANE-1.0-1/backend'
../mkinstalldirs /usr/local/lib /usr/local/lib/sane /usr/local/etc/sane.d
installing libsane-lexmark.la in /usr/local/lib/sane/libsane-lexmark.la...
libtool: install: `libsane-lexmark.la' is not a valid libtool archive
Try `libtool --help --mode=install' for more information.
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/prabha/Download/X7170SampleSANE-1.0-1/backend'make: *** [install-recursive] Error 1

Any idea?

---

### Post by arunsub on 2005-10-25
I got the driver for Lexmark X7170 from this link.
[http://www.lexmark.com/US/products/info/linux/licenseX7170_rev2.html](http://www.lexmark.com/US/products/info/linux/licenseX7170_rev2.html)

I ran alien filename as normal user (not as root). I then got the deb file. I then issued
$sudo dpkg -i x7170llpddk_2.0-5_i386.deb
(Reading database ... 95758 files and directories currently installed.)
Preparing to replace x7170llpddk 2.0-5 (using x7170llpddk_2.0-5_i386.deb) ...
Unpacking replacement x7170llpddk ...
Setting up x7170llpddk (2.0-5) ...
$

I then rebooted the system. When I went to add printer, I didn't see the driver under either Dell or Lexmark. I would appreciate if someone can help me.

---

### Post by LinuxWiz83 on 2005-10-26
I would like to see this get resolved as well because i have the same make and model that i bought last christmas time. If this gets resolved i can move to Ubuntu Linux completely meaning no more windows except when i am doing my online training which is in cold fusion but i can use Win4Lin for that.

---

### Post by Vcount on 2006-07-04
I wish I could help with this issue, but I'd just like to chime in and say that I'm in the same boat as the rest of you.  I'll be interested to see if anyone solves it.   

If I am able to get this printer working, I'd also be free to go to an all-ubuntu OS.

---

### Post by arunsub on 2006-07-05
I didn't find solution till now.

---

### Post by elementadiobam on 2006-09-29
> **arunsub said:**
> I didn't find solution till now.
What you found a solution?

---

### Post by arunsub on 2006-09-29
No I couldn't get it to work.

---

### Post by snowdonkey on 2007-02-07
I'm having the same problem with my Lexmark X7170 printer.  At [http://www.linuxprinting.org/printer_list.cgi?make=Lexmark](http://www.linuxprinting.org/printer_list.cgi?make=Lexmark) the X7170 model is listed as a "paperweight," so I guess any attempts to make it work are futile. 

I found that page via a thread at linuxquestons.org, here:
[http://www.linuxquestions.org/questions/showthread.php?t=517169](http://www.linuxquestions.org/questions/showthread.php?t=517169)

---

### Post by ramjet_1953 on 2007-02-07
Try this link.

It is a very complete site for printers that have actually been tested under Unix and Linux.

[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

Regards,
Roger 8)

---

### Post by arunsub on 2007-02-08
X7170 is not there in that list.

---

