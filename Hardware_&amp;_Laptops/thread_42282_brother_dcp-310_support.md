---
title: "brother dcp-310 support"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by dninja on 2005-06-16
I have just bought a Brother DCP-310 printer/scanner/copier and am trying to get it working under Ubuntu. I have it plugged into the network and don't have a USB cable to try any USB based tests.

I have found the debian cups drivers on the ([brother](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperdcp310cn_1.0.0-1_i386.deb&lang=English_cups) site and tried to install that but there are differences between the debian and ubuntu installs/setups of cups.

If I convert the .dev to a tar and look into it the following file is the only useful looking one:
-rwxrwxrwx root/root    100916 2005-02-02 05:05:18 ./usr/local/Brother/cupswrapper/cupswrapperDCP310CN-1.0.0

Can anyone suggest what I can do with this file to install it by hand?

Also, does anyone know if I can access the scanner from linux, especially as it is over the network? You can register your PC with the scanner so that when you press the scan button it asks where to send the data to. It would be nice to get that sent straight into GIMP. The spec on the box says that it supports TWAIN and WIA, does that help?

Lastly, if I get all that sorted, its default network name is BRN_6B4DE7 which I believe BIND doesn't like as it has an underscore in it, does anyone know if this is true?

Loads of questions, probably not enough info, please ask for more.

---

### Post by dninja on 2005-06-18
Kind of getting somewhere...

I found that the file in the debian package is a script which creates to files, the ppd and a filter.

I have placed the ppd and the filter in the right places and I've used cups admin and the web interface to try to get cups to talk to the printer.

No luck. I even ran ethereal to watch network traffic to see if anything was being sent when i tried to send a test page, nothing!

The printer has the following ports open:

21/tcp   open     ftp
23/tcp   open     telnet
515/tcp  open     printer
9100/tcp filtered jetdirect

so I am using the connection string socket://192.168.0.20:9100 to try to use the jetdirect method. Nothing.

I can telnet straight to port 9100 and send data so I am on the right lines.

The following is a dump from my cups error log.

d [18/Jun/2005:23:42:38 +0100] AcceptClient(lis=0x808b338) 0 NumClients = 0
D [18/Jun/2005:23:42:38 +0100] AcceptClient: 4 from localhost:631.
d [18/Jun/2005:23:42:38 +0100] AcceptClient: Adding fd 4 to InputSet...
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4, used=0, file=-1
D [18/Jun/2005:23:42:38 +0100] ReadClient: 4 POST / HTTP/1.1
d [18/Jun/2005:23:42:38 +0100] decode_auth(0xb7bf9008): Authorization string = ""
d [18/Jun/2005:23:42:38 +0100] decode_auth: 4 username=""
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: con->uri = "/"
d [18/Jun/2005:23:42:38 +0100] FindBest: uri = "/"...
d [18/Jun/2005:23:42:38 +0100] FindBest: Location / Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /jobs Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /admin Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: best = "/"
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: auth = 0, satisfy=0...
d [18/Jun/2005:23:42:38 +0100] POST /
d [18/Jun/2005:23:42:38 +0100] CONTENT_TYPE = application/ipp
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4 con->data_encoding = length, con->data_remaining = 137, con->file = -1
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest(0xb7bf9008[4]): operation_id = 4002
d [18/Jun/2005:23:42:38 +0100] get_printers(0xb7bf9008[4], 0)
d [18/Jun/2005:23:42:38 +0100] add_printer_state_reasons(0xb7bf9008[4], 0x8095e80[DeskJet])
d [18/Jun/2005:23:42:38 +0100] add_queued_job_count(0xb7bf9008[4], 0x8095e80[DeskJet])
d [18/Jun/2005:23:42:38 +0100] copy_attrs(0x80bc848, 0x8092b68, 0x80bb870, 0)
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bc848, 0x8092cc8[printer-name,4,42])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bc848, 0x8092ed8[job-sheets-default,4,42])
d [18/Jun/2005:23:42:38 +0100] copy_attrs(0x80bc848, 0x8092640, 0x80bb870, 0)
D [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: 4 status_code=1
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: Adding fd 4 to OutputSet...
d [18/Jun/2005:23:42:38 +0100] WriteClient: Removing fd 4 from OutputSet...
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4, used=0, file=-1
D [18/Jun/2005:23:42:38 +0100] ReadClient: 4 POST / HTTP/1.1
d [18/Jun/2005:23:42:38 +0100] decode_auth(0xb7bf9008): Authorization string = ""
d [18/Jun/2005:23:42:38 +0100] decode_auth: 4 username=""
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: con->uri = "/"
d [18/Jun/2005:23:42:38 +0100] FindBest: uri = "/"...
d [18/Jun/2005:23:42:38 +0100] FindBest: Location / Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /jobs Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /admin Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: best = "/"
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: auth = 0, satisfy=0...
d [18/Jun/2005:23:42:38 +0100] POST /
d [18/Jun/2005:23:42:38 +0100] CONTENT_TYPE = application/ipp
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4 con->data_encoding = length, con->data_remaining = 137, con->file = -1
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest(0xb7bf9008[4]): operation_id = 4005
d [18/Jun/2005:23:42:38 +0100] get_printers(0xb7bf9008[4], 1)
D [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: 4 status_code=1
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: Adding fd 4 to OutputSet...
d [18/Jun/2005:23:42:38 +0100] WriteClient: Removing fd 4 from OutputSet...
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4, used=0, file=-1
D [18/Jun/2005:23:42:38 +0100] ReadClient: 4 POST / HTTP/1.1
d [18/Jun/2005:23:42:38 +0100] decode_auth(0xb7bf9008): Authorization string = ""
d [18/Jun/2005:23:42:38 +0100] decode_auth: 4 username=""
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: con->uri = "/"
d [18/Jun/2005:23:42:38 +0100] FindBest: uri = "/"...
d [18/Jun/2005:23:42:38 +0100] FindBest: Location / Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /jobs Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: Location /admin Limit 7f
d [18/Jun/2005:23:42:38 +0100] FindBest: best = "/"
d [18/Jun/2005:23:42:38 +0100] IsAuthorized: auth = 0, satisfy=0...
d [18/Jun/2005:23:42:38 +0100] POST /
d [18/Jun/2005:23:42:38 +0100] CONTENT_TYPE = application/ipp
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4 con->data_encoding = length, con->data_remaining = 77, con->file = -1
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest(0xb7bf9008[4]): operation_id = 4001
d [18/Jun/2005:23:42:38 +0100] get_default(0xb7bf9008[4])
d [18/Jun/2005:23:42:38 +0100] copy_attrs(0x80bbd58, 0x8092b68, (nil), 0)
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092b90[printer-uri-supported,4,45])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092c00[uri-authentication-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092c70[uri-security-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092cc8[printer-name,4,42])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092d18[printer-location,4,41])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092d68[printer-info,4,41])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092db8[printer-more-info,4,45])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092e20[job-quota-period,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092e60[job-k-limit,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092e98[job-page-limit,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092ed8[job-sheets-default,4,42])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092f40[device-uri,4,45])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80a3dd0[color-supported,4,22])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80a41e0[pages-per-minute,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80a4408[printer-make-and-model,4,41])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8092f98[media-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80ac438[media-default,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8094ec0[finishings-supported,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80a9fc8[finishings-default,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80aa1b0[printer-type,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attrs(0x80bbd58, 0x8092640, (nil), 0)
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096f20[pdl-override-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096ac0[ipp-versions-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x808f748[operations-supported,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096db0[multiple-document-jobs-supported,4,22])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096d88[multiple-operation-time-out,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096880[multiple-document-handling-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096c40[charset-configured,4,47])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096490[charset-supported,4,47])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096c00[natural-language-configured,4,48])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096bc0[generated-natural-language-supported,4,48])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096b78[document-format-default,4,49])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096928[document-format-supported,4,80000049])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x808f6d8[compression-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096b30[job-priority-supported,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x80968c0[job-priority-default,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096858[copies-supported,4,33])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096800[copies-default,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096450[page-ranges-supported,4,22])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096c88[number-up-supported,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096428[number-up-default,4,21])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096d40[orientation-requested-supported,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x808f8c8[orientation-requested-default,4,23])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096e00[job-hold-until-supported,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x808f6b0[job-hold-until-default,4,44])
d [18/Jun/2005:23:42:38 +0100] copy_attribute(0x80bbd58, 0x8096f78[job-sheets-supported,4,42])
D [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: 4 status_code=0
d [18/Jun/2005:23:42:38 +0100] ProcessIPPRequest: Adding fd 4 to OutputSet...
d [18/Jun/2005:23:42:38 +0100] WriteClient: Removing fd 4 from OutputSet...
d [18/Jun/2005:23:42:38 +0100] ReadClient: 4, used=0, file=-1
d [18/Jun/2005:23:42:38 +0100] ReadClient: httpGets returned EOF...
D [18/Jun/2005:23:42:38 +0100] CloseClient: 4
d [18/Jun/2005:23:42:38 +0100] CloseClient: Removing fd 4 from InputSet and OutputSet...
d [18/Jun/2005:23:42:39 +0100] select_timeout: 11 seconds to process active jobs
d [18/Jun/2005:23:42:42 +0100] AcceptClient(lis=0x808b338) 0 NumClients = 0
D [18/Jun/2005:23:42:42 +0100] AcceptClient: 4 from localhost:631.
d [18/Jun/2005:23:42:42 +0100] AcceptClient: Adding fd 4 to InputSet...
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4, used=0, file=-1
D [18/Jun/2005:23:42:42 +0100] ReadClient: 4 POST /printers/DeskJet HTTP/1.1
d [18/Jun/2005:23:42:42 +0100] decode_auth(0xb7bf9008): Authorization string = ""
d [18/Jun/2005:23:42:42 +0100] decode_auth: 4 username=""
d [18/Jun/2005:23:42:42 +0100] IsAuthorized: con->uri = "/printers/DeskJet"
d [18/Jun/2005:23:42:42 +0100] FindBest: uri = "/printers/DeskJet"...
d [18/Jun/2005:23:42:42 +0100] FindBest: Location / Limit 7f
d [18/Jun/2005:23:42:42 +0100] FindBest: Location /jobs Limit 7f
d [18/Jun/2005:23:42:42 +0100] FindBest: Location /admin Limit 7f
d [18/Jun/2005:23:42:42 +0100] FindBest: best = "/"
d [18/Jun/2005:23:42:42 +0100] IsAuthorized: auth = 0, satisfy=0...
d [18/Jun/2005:23:42:42 +0100] POST /printers/DeskJet
d [18/Jun/2005:23:42:42 +0100] CONTENT_TYPE = application/ipp
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4 con->data_encoding = length, con->data_remaining = 289, con->file = -1
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4 REQUEST /var/spool/cups/00000001=6
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4 writing 12 bytes to 6
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4 Closing data file 6, size = 12.
d [18/Jun/2005:23:42:42 +0100] ProcessIPPRequest(0xb7bf9008[4]): operation_id = 0002
d [18/Jun/2005:23:42:42 +0100] ProcessIPPRequest: URI="ipp://localhost:631/printers/DeskJet"
d [18/Jun/2005:23:42:42 +0100] print_job(0xb7bf9008[4], ipp://localhost:631/printers/DeskJet)
D [18/Jun/2005:23:42:42 +0100] print_job: auto-typing file...
D [18/Jun/2005:23:42:42 +0100] print_job: request file type is text/plain.
d [18/Jun/2005:23:42:42 +0100] check_quotas(0xb7bf9008[4], 0x8095e80[DeskJet])
D [18/Jun/2005:23:42:42 +0100] check_quotas: requesting-user-name = 'root'
D [18/Jun/2005:23:42:42 +0100] print_job: requesting-user-name = 'root'
I [18/Jun/2005:23:42:42 +0100] Adding start banner page "classified" to job 5.
d [18/Jun/2005:23:42:42 +0100] copy_banner(0xb7bf9008[4], 0x80bbd80[5], classified)
d [18/Jun/2005:23:42:42 +0100] add_file(con=0xb7bf9008[4], job=5, filetype=application/postscript, compression=0)
d [18/Jun/2005:23:42:42 +0100] add_file(con=0xb7bf9008[4], job=5, filetype=text/plain, compression=0)
I [18/Jun/2005:23:42:42 +0100] Adding end banner page "secret" to job 5.
d [18/Jun/2005:23:42:42 +0100] copy_banner(0xb7bf9008[4], 0x80bbd80[5], secret)
d [18/Jun/2005:23:42:42 +0100] add_file(con=0xb7bf9008[4], job=5, filetype=application/postscript, compression=0)
I [18/Jun/2005:23:42:42 +0100] Job 5 queued on 'DeskJet' by 'root'.
D [18/Jun/2005:23:42:42 +0100] Job 5 hold_until = 0
d [18/Jun/2005:23:42:42 +0100] SaveJob: Closing file 6...
d [18/Jun/2005:23:42:42 +0100] add_job_state_reasons(0xb7bf9008[4], 5)
D [18/Jun/2005:23:42:42 +0100] ProcessIPPRequest: 4 status_code=0
d [18/Jun/2005:23:42:42 +0100] ProcessIPPRequest: Adding fd 4 to OutputSet...
d [18/Jun/2005:23:42:42 +0100] WriteClient: Removing fd 4 from OutputSet...
d [18/Jun/2005:23:42:42 +0100] ReadClient: 4, used=0, file=-1
d [18/Jun/2005:23:42:42 +0100] ReadClient: httpGets returned EOF...
D [18/Jun/2005:23:42:42 +0100] CloseClient: 4
d [18/Jun/2005:23:42:42 +0100] CloseClient: Removing fd 4 from InputSet and OutputSet...


Someone must be able to make a guess at my mistake!

Just to prove it isn't the printer, windows prints fine!

---

### Post by inoxllor on 2007-05-13
Here is the PPD file if you need it.

I've managed to install my DCP310 using the guide provided here:

[**Brother Linux Driver Site**]("http://solutions.brother.com/linux/en_us/index.html")
*Download the LPR and the CUPS drivers for Debian*.

Also don't forget to install CSH via synaptics manager.

-- 
Best Regards

---

### Post by dninja on 2007-05-13
Thanks for this, I've been meaning to get back to it for ages. I managed to get scanning working without too much trouble but then didn't have time to carry on with printing. I've been lazy and using a vmware windows box to do it all so far!

---

### Post by inoxllor on 2007-06-29
To install the Brother DCP-310 scanner do this:
**sudo apt-get install xsane**

then
**lsusb**
in my case it retuns:
> Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 04f9:016b Brother Industries, Ltd 
Bus 003 Device 002: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


so I enter this command
**sudo chmod 666 /proc/bus/usb/003/003 ** 
*to give access to Bus 003 Device 003 => Brother Printer!*

then run xsane and you should get your scanner working :D

---

### Post by Sofie on 2007-10-05
I am very new.

I cant seem to install my brother dcp-340cw. 

I do not know if I am a deb? or a  "Red Hat / Mandriva (Mandrake) / SuSE / FedoraCore User"?

---

### Post by dninja on 2007-10-05
As ubuntu is based on debian you'd be a deb. I'm not sure if you can just install debian packages and can't test it as I'm not running ubuntu at the moment.

If you can't then I'd go for unpacking the deb file and doing a manual install, if you need to know how to do that shout.

---

### Post by Sofie on 2007-10-06
Oh I dont understand that?

Manual install? How? what?
I am very new.

I think I should install driver for 
- WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g (Atheros)
- Brother DCP-340cw
and the program Xsane?

---

### Post by dninja on 2007-10-06
> **Sofie said:**
> Oh I dont understand that?

Manual install? How? what?
I am very new.

I think I should install driver for 
- WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g (Atheros)
- Brother DCP-340cw
and the program Xsane?

The first driver you mention is for your wireless card, that is nothing to do with scanning or printing so I'd leave that for now if you are trying to get the printer working.

If you want to know how to install a deb file, this page gives you instructions on how to do it. As it warns, you may get some problems but with something as simple as these drivers it should work:

[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

I'm surprised that no one has created an ubuntu package for this driver yet. Anyone fancy doing it?

---

### Post by Matthaeus on 2007-10-11
> # For AMD64 bit users:
Our CUPS drivers and CUPS wrapper drivers have been developed and optimised for 32 bit Linux distributions, a list of which can be found here:
[http://solutions.brother.com/linux/sol/printer/linux/linux_config_list2.html](http://solutions.brother.com/linux/sol/printer/linux/linux_config_list2.html)

However, if you are using an AMD64 bit distribution, we recommend you try copying the file named "brlpdwrapper" from /usr/lib/cups/filter to /usr/lib64/cups/filter.

I am trying to setup a DCP-130c on a feisty fawn 64 bit install. 
I can't see the file (brlpdwrapper).  Do i have to install something before i can see this file?

I have setup another printer on a ubuntu 7.1 install following the brother sites guide, but it was 32bit.....

Thanks, Matt.

---

