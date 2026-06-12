---
title: "Scan button on Brother DCP-L2550DW does not work &quot;No PC found&quot;"
date: 2020-02-02
forum: Hardware
---

### Post by bingbong6 on 2020-02-02
Also asked on askubuntu.com here:  [https://askubuntu.com/questions/1207647/scan-button-on-brother-dcp-l2550dw-does-not-work-no-pc-found](https://askubuntu.com/questions/1207647/scan-button-on-brother-dcp-l2550dw-does-not-work-no-pc-found)


Ubuntu 18.04

Using this over local wifi network.

When I try to scan using the physical button, it prompts "scan to pc" press OK, then choose "file", then it says "no pc found"

I've installed drivers from the brother site and everything else works. I can scan to file using the Simple Scan software with Ubuntu and it works fine.

I installed the driver for the physical scan button mentioned here [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2550dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2550dw_us&os=128) "Scan-key-tool 64bit (deb package)" and followed the instructions and installed it, but it still doesn't work.

Any suggestions?

---

### Post by CelticWarrior on 2020-02-03
You need to setup some network share before you can use that function. How to do that should be in the user's manual.

---

### Post by bingbong6 on 2020-02-03
The user manual only shows how to set it up via Windows or Mac. It says you need their software. Openprinting says this works "perfect" so there has to be some other solution.

---

### Post by CelticWarrior on 2020-02-03
> **bingbong6 said:**
> The user manual only shows how to set it up via Windows or Mac. It says you need their software. Openprinting says this works "perfect" so there has to be some other solution.

I'm afraid there isn't. The printer must be set in some way, the printer can't guess where it should send the file and, of course, you need to setup a network share somewhere in your LAN also. It seems you expect it happens by magic but magic only exists in fiction.

Either the printer can be configured via a menu or it needs software for that purpose. Brother usually has good support for Linux but that also usually means printing and scanning only, not necessarily network setup. Works "perfect" means printing and scanning, nothing else. The proprietary driver - I believe it's a command line installation - may or may not at some point asks whether you want to setup a local (USB) or a network connected printer (WiFi, Ethernet) and it may or may not follow up a network installation with the setup of some network share where to send the files. 

Some models like [this one]("https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfc9130cw_us&faqid=faq00002979_001") allow configuration via a web browser (OS independent). So, if already configured in your network (meaning: Has an IP address) maybe you could try that?

---

### Post by CelticWarrior on 2020-02-03
Good news (maybe):

Checking the drivers page [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2550dw_us&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=dcpl2550dw_us&os=128) there's actually a tool available - scan-key-tool - that says "with this tool, you can start a scan by the button on the machine". I suggest installing this and then run it. With some "luck" it will do the same as the software for Windows or MacOS. Likely you need to install the scanner driver first.

---

### Post by bingbong6 on 2020-02-03
I've installed that already along with: "linux printer driver". "scanner driver" and the "scanner setting file" (udev rule).

I'm aware that it isn't magic. As far as I'm aware it HAS been configured since every other aspect of this machine communicates over the LAN just fine. I can scan from software within ubuntu and I can send print jobs to the printer successfully. 

Something interesting though, I reinstalled all of those drivers, and perhaps I missed a step somewhere? Because now when I press the scan button on the printer, and select file, instead of saying "no pc found" it tells me to press start, and it then displays "connecting to pc" where it eventually times out.

---

### Post by bingbong6 on 2020-02-03
> **CelticWarrior said:**
> Some models like [this one]("https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfc9130cw_us&faqid=faq00002979_001") allow configuration via a web browser (OS independent). So, if already configured in your network (meaning: Has an IP address) maybe you could try that?

On the printer driver install instructions it does say to go to [http://localhost:631/printers](http://localhost:631/printers) and modify some parameters: 

```

[LIST]
[*]Open a web browser and go to **"http://localhost:631/printers"**.
[*]Click "Modify Printer" and set following parameters.[TABLE]
[TR]
[TD]- "LPD/LPR Host or Printer" or "AppSocket/HP JetDirect"[/TD]
[TD][/TD]
[TD]for Device[/TD]
[/TR]
[TR]
[TD]- lpd://(Your printer's IP address)/binary_p1[/TD]
[TD][/TD]
[TD]for Device URI[/TD]
[/TR]
[TR]
[TD]- Brother[/TD]
[TD][/TD]
[TD]for Make/Manufacturer Selection[/TD]
[/TR]
[TR]
[TD]- Your printer's name[/TD]
[TD][/TD]
[TD]for Model/Driver Selection[/TD]
[/TR]
[/TABLE]
[/LIST]

```

But when I go to "modify printer" it shows an error page:

> 
[COLOR=#000000]**Unauthorized**

Enter your username and password or the root username and password to access this page. If you are using Kerberos authentication, make sure you have a valid Kerberos ticket.[/COLOR]

And I'm not sure where to enter this user or password or where to set it up...

---

### Post by CelticWarrior on 2020-02-03
Try searching for and run the scan-key-tool. It must have a configuration for the network share that you must have available already. I suppose this entry level SOHO printer expects a Windows share type so, if your intended destination is a folder in your Ubuntu PC you need Samba and at least one shared folder before running the scan-key-tool.

---

### Post by bingbong6 on 2020-02-03
as far as I know, you run scan-key-tool via

```

brscan-skey

```

and it runs as a background process. Check to see if it's running via:

```

brscan-skey -l

```

But that yields no results or reaction.

Samba looks like a whole other can of worms. At that point I might just use the Simple Scan to scan from my computer and not use the hardware button. I'm only trying to troubleshoot this for my mother to use on her identical setup, since she would be more comfortable with the physical buttons. 

Frustrating, because it seems as though it should work without having to use an outside program workaround like Samba.

---

### Post by bingbong6 on 2020-02-03
if it helps, here is the output of 'dpkg -l | grep Brother' 

```

ii  brother-udev-rule-type1                                     1.0.2                                                       all          Brother udev rule type 1
ii  brscan-skey                                                 0.2.4-1                                                     amd64        Brother Linux scanner S-KEY tool
ii  brscan4                                                     0.4.8-1                                                     amd64        Brother Scanner Driver
ii  dcpl2550dwpdrv:i386                                         4.0.0-1                                                     i386         Brother DCP-L2550DW printer driver (lpd/cups)
ii  printer-driver-brlaser                                      4-1                                                         amd64        printer driver for (some) Brother laser printers
ii  printer-driver-ptouch                                       1.4.2-3                                                     amd64        printer driver Brother P-touch label printers

```

---

### Post by him610 on 2020-02-05
This was interesting to me because I use a Brother MFC7360n, and I wanted to I could help the OP in some way. While I regularly use Document Scanner (new name for Simple Scan in 20.04) to send scans to my PC, I had never done it from the scan button on the MFC7360n.
There is a page in the manual that provides the steps on how to scan to PC...
1.  Load document
2.  Press Scan
3.  Using Up or Down arrows, select Scan to PC
4.  Press OK
5.  Choose scan mode [FTP | E-mail (Scan to PC) | Image (Scan to PC) | OCR (Scan to PC) | File (Scan to PC)]
6.   Press Start

LCD Panel displays "Connecting to PC"
MFC7360n begins to scan

I chose Image; when it got to the PC it activated GIMP with the scanned image displayed in GIMP. One can modify or save the file in GIMP.

Notes:
On Step 3, my displayed choices were 'Scan to PC' or 'Web Service'. I did not choose Web Service.
There are several networked computers running both Xubuntu and Win10 on my home network.  Network configured with Samba and NFS.
The attached image began as screenshot of the applicable page in the manual. The screenshot was saved to a LibreOffice Doc file, printed from a B&W printer then scanned from the MFC7360n to my PC running Xubuntu 20.04 where it was opened and saved in GIMP.
IMHO, it is a lot easier to use Document Scanner (Simple Scan). It seems more complicated (more steps) using the Scan button on the MFC7360n.

---

### Post by bingbong6 on 2020-02-05
My experience was the same except after step 6 mine says "connecting to PC" and then does nothing and eventually times out.

---

### Post by him610 on 2020-02-05
You have one file that I do not have,
>  brother-udev-rule-type1     1.0.2  
While I have one file that you do not have, 
> cupswrappermfc7360n:i386    2.0.4-2

> My experience was the same except after step 6 mine says "connecting to PC" and then does nothing and eventually times out.
Was it an image file? Do you have GIMP installed?

---

### Post by him610 on 2020-02-05
I ran through the same sequence again - this time with a page of text; selected File (Scan to PC)
Last two steps on the LCD display: 'connecting to PC' followed by 'scanning'
After scanning, it seems to finish.
Don't know if it was successful or not; no application opened like it did scanning an image.
On my computer in my Home directory, there is a new sub-directory, brscan
Inside of ~/brscan are both of the text files I scanned today. 
This is the file name of the most recent scanned file, brscan_2020-02-05-20-50-56.pnm
When I click on brscan_2020-02-05-20-50-56.pnm, it opens with Image Viewer (ristretto)
Maybe yours are in the brscan directory.

---

### Post by plucky on 2020-02-06
> **him610 said:**
> I ran through the same sequence again - this time with a page of text; selected File (Scan to PC)
Last two steps on the LCD display: 'connecting to PC' followed by 'scanning'
After scanning, it seems to finish.
Don't know if it was successful or not; no application opened like it did scanning an image.
On my computer in my Home directory, there is a new sub-directory, brscan
Inside of ~/brscan are both of the text files I scanned today. 
This is the file name of the most recent scanned file, brscan_2020-02-05-20-50-56.pnm
When I click on brscan_2020-02-05-20-50-56.pnm, it opens with Image Viewer (ristretto)
Maybe yours are in the brscan directory.

This procedure worked on my network printer but```
/Desktop$ brscan-skey -l

 DCP-1610W         : brother4:net1;dev0  : 192.168.0.100        Active

``` shows on my PC
I have my printer on a static network address.

Good Luck

---

### Post by him610 on 2020-02-06
Yes, same with mine,
```

$ brscan-skey -l

 MFC-7360N         : brother4:net1;dev0  : 10.0.0.197           Active


```

---

### Post by him610 on 2020-02-06
The DCP-L2550DW seems to be working as it should. There appears to be lack of communication between the scanner and the PC when the communication is initiated from DCP-L2550DW when in 'scan to pc' mode.
Could it be a network issue?
Could it be a firewall?
There is something about the OP's setup that prevents the completion of 'scan to pc'

I wish I could provide more helpful advice, but it is difficult to diagnose and troubleshoot a problem without ever having experienced that same problem.

---

### Post by bingbong6 on 2020-02-06
I do have gimp installed and no it was a printed page of text put into the feed ramp. Just says "connecting to pc" then just disappears and lcd goes back to the home lcd screen. I don't see a brscan folder in my home directory

---

