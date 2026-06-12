---
title: "Problems printing to Brother HL-L2300D (Ubuntu 20.04.3 LTS)"
date: 2021-11-04
forum: Hardware
---

### Post by aj34 on 2021-11-04
Are there known printing issues with Ubuntu 20.04.3 LTS?

Would appreciate help with an irritating printer problem. Since I installed Ubuntu 20.04.3 LTS earlier this year, I've had an intermittent printer issue that I don't understand. Sometimes, everything prints just fine on my USB-connected Brother HL-L2300D printer whereas at other times, the printer produces no output yet it's printing light flashes (in the same way it does when it actually outputs a printed page) yet does not print (i.e. printer remains silent and doesn't attempt to draw the paper in). When this happens, Ubuntu informs me that printing has completed and, subsequently, there is no document in the printer queue. Often, I uninstall/remove the printer when this happens, turn the printer off and on again then reinstall the printer. Sometimes this does the trick, sometimes it doesn't.

This printing issue has occurred at various times in the past few months under different conditions and I can't identify any common conditions in the way I'm attempting to print. Yesterday, I successfully printed off a few sheets, one after another,   when printing inexplicably ceased even though I had changed no settings -  other than to select portrait rather than landscape (as if that should  make any difference). At other times, printing refuses when I attempt to print after I've just booted the PC.

It's tempting to suspect a printer problem but the Brother HL-L2300D prints consistently well when using Windows 10 (dual boot PC) but as I don't get on with Windows, I prefer to use Ubuntu.
PS My knowledge of computer software is minimal so I won't understand much jargon. Thanks for your consideration.

---

### Post by oldfred on 2021-11-05
Are you using USB or WiFi to connect to printer?

My Brother HL_L2390DW has both and I think it gets confused. The only issue I have is that I think it tries using WiFi and should be using the USB connection. I seem to have to change printer as several are shown in list of printers. My wife needs the WiFi to print from her iPad, but my Desktop is directly connected with USB.

I did see that the USB driver ippusbxd has been updated to ipp-usb in newer versions of Ubuntu but my 20.04 still uses the old driver & newer is not available.

---

### Post by aj34 on 2021-11-06
Thanks for your reply.

The HL-L2300D is a basic model and doesn't have wifi or a wired Ethernet connection - just plain old USB into PC.

The difficulty with intermittent problems that appear (apparently) at random is that it's almost impossible to identify the cause - let alone effect a solution.

Shame, Ubuntu looked so promising and seemed more logical than Windows but it looks like I'll have to stick with Windows after all.

---

### Post by yancek on 2021-11-06
The link below gives some information on using a terminal to print as well as how to get detailed information on your printer(s)

[https://www.networkworld.com/article/3373502/printing-from-the-linux-command-line.html](https://www.networkworld.com/article/3373502/printing-from-the-linux-command-line.html)

Take a look at the YouTube video at the link below which explains printing from a terminal which should simply things and hopefully clarify things for you.

[https://www.youtube.com/watch?v=1ksoS1pbJM8](https://www.youtube.com/watch?v=1ksoS1pbJM8)

---

### Post by brian_p on 2021-11-06
I'll try a long shot. Please give ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

---

### Post by kurt18947 on 2021-11-06
I have two Brother machines, both ethernet connected. I tend to use Brother's drivers, the automatically installed ones seem to often have niggles. I've had very good success with the Brother installer.
I seem to recall some glitches with 20.04 and USB printing but don't recall any details. Here's Brother's page for your printer:

[https://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=hll2300d_us_eu_ase](https://support.brother.com/g/b/downloadtop.aspx?c=us_ot&lang=en&prod=hll2300d_us_eu_ase)


to keep things neat, I download the driver to it's own subfolder. The install process will drop one or more .deb files in the folder where the download is located. This is more of an issue with all-in-ones with scanner support

Ignore most of the FAQs, they've  long been superseded in Ubuntu.

---

### Post by brian_p on 2021-11-07
> **brian_p said:**
> I'll try a long shot. Please give ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

No need to be frightened of this command. It simply tells us whether your device is capable of using the IPP-over-USB protocol. You don't want to know? All well and good.

---

### Post by SeijiSensei on 2021-11-08
Try using the "Driver Install Tool" available at [https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128).

---

### Post by aj34 on 2021-11-11
Thanks very much for your replies, folks. Much appreciated.

I hadn't realised I received more replies - can I get email notification of thread replies/responses like I do for other forums I use?

Unfortunately, I don't understand some of your replies but I've attempted to follow the instructions I could manage. I tried typing the "code" into the terminal (is this the same thing as "command line"?) provided by brian_p and got the following result:

rfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 

...along with four identical error-type lines that said that something couldn't be done (sorry, forget exact wording). This was with the printer turned on and USB connected to PC. With printer turned off, I just got the four lines of error-type code.

Means absolutely nothing to me (and I don't understand "IPP-over-USB protocol " either). Perhaps this result means something to someone?

I then accessed links provided by yancek in post#4. Sorry, but I really don't get the point of these. I don't intend to print using terminal. Perhaps I've missed the point?

Finally, I tried out the Brother download suggested by kurt18947 and SeijiSensei. I downloaded the Brother driver install tool into a folder yet I can't access it using the terminal command: cd Xxxxxx (were Xxxxxx is the folder name) as instructed in the Brother instructions (I get the response: "folder couldn't be found"). Would appreciate advice on this.

Just to re-emphasize - I am a novice at this stuff.

Thanks again for your assistance (and patience!)

---

### Post by brian_p on 2021-11-11
> **aj34 said:**
> 

Unfortunately, I don't understand some of your replies but I've attempted to follow the instructions I could manage. I tried typing the "code" into the terminal (is this the same thing as "command line"?) provided by brian_p and got the following result:

rfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 

...along with four identical error-type lines that said that something couldn't be done (sorry, forget exact wording). This was with the printer turned on and USB connected to PC. With printer turned off, I just got the four lines of error-type code.

Thanks. However, the idea I had in mind will not work.
> 
Means absolutely nothing to me (and I don't understand "IPP-over-USB protocol " either). Perhaps this result means something to someone?


See [https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting).

---

### Post by aj34 on 2021-11-17
[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)

Thanks for the link, Brian. Had a quick look-see and realised this will take me some time to digest because there are so many terms, and concepts, I'm unfamiliar with. May have the time to investigate further in a week or so, meanwhile I'll stick with Windows OS for printing. Regards.

---

### Post by UrBob on 2021-12-04
Running the Brother installer.
In the following, lines beginning with $ are the terminal commands that I input. You will need to type everything after the $ into your terminal and then hit the Enter/Return key.
e.g. [FONT=system]dave@ubuntu20vm-desk:~$ cd Downloads[/FONT]
[FONT=system]dave@ubuntu20vm-desk:[/FONT] is who I am logged in as, on what machine (it's a virtual machine which is why the 'vm' in the domain).
[FONT=system]~$[/FONT] is the prompt, where ~ indicates the home folder.
[FONT=system]cd Downloads[/FONT] is the command to change to the Downloads folder. The prompt then changes to
[FONT=system]dave@ubuntu20vm-desk:~/Downloads$[/FONT]
I have not included all the output.

Visit [https://support.brother.com/g/b/productsearch.aspx?c=gb&lang=en&content=dl](https://support.brother.com/g/b/productsearch.aspx?c=gb&lang=en&content=dl) and use the search box to select your printer model.
Next page select Linux and deb. This will take you to the Downloads page proper.
Select 'Driver Install Tool' then accept the agreement.
Select to Save the download in the pop-up dialog.
Brother provides some helpful instructions, although they are not always as clear as I would like.

The key combination <ctrl><alt>t will open a new terminal in your home folder, and hopefully your download went into the Downloads folder in your home folder. Note that file and folder names are case sensitive in Linux.
Replace HL-3150CDW with the model of your printer when following the instructions.
[COLOR=#4E9A06][B]
dave@ubuntu20vm-desk[/B][/COLOR]:[COLOR=#3465A4]**~**[/COLOR]$ cd Downloads[COLOR=#4E9A06][B]
dave@ubuntu20vm-desk[/B][/COLOR]:[COLOR=#3465A4]**~/Downloads**[/COLOR]$ ls
[COLOR=#CC0000]**linux-brprinter-installer-2.2.3-1.gz**[/COLOR]   [COLOR=#3465A4]**STG-backups-FF-87.0**[/COLOR]     [COLOR=#3465A4]**STG-backups-FF-92.0**[/COLOR]
 [COLOR=#3465A4]**node-v14.16.0-linux-x64**[/COLOR]                [COLOR=#3465A4]**STG-backups-FF-88.0.1**[/COLOR]   [COLOR=#3465A4]**STG-backups-FF-93.0**[/COLOR]
 [COLOR=#CC0000]**node-v14.16.0-linux-x64.tar.xz**[/COLOR]         [COLOR=#3465A4]**STG-backups-FF-89.0.1**[/COLOR]   [COLOR=#3465A4]**STG-backups-FF-94.0**[/COLOR]
[COLOR=#4E9A06]**dave@ubuntu20vm-desk**[/COLOR]:[COLOR=#3465A4]**~/Downloads**[/COLOR]$ gunzip linux-brprinter-installer-*.*.*-*.gz
[COLOR=#4E9A06]**dave@ubuntu20vm-desk**[/COLOR]:[COLOR=#3465A4]**~/Downloads**[/COLOR]$ ls
linux-brprinter-installer-2.2.3-1   [COLOR=#3465A4]**STG-backups-FF-87.0**[/COLOR]     [COLOR=#3465A4]**STG-backups-FF-92.0**[/COLOR]
 [COLOR=#3465A4]**node-v14.16.0-linux-x64**[/COLOR]             [COLOR=#3465A4]**STG-backups-FF-88.0.1**[/COLOR]   [COLOR=#3465A4]**STG-backups-FF-93.0**[/COLOR]
 [COLOR=#CC0000]**node-v14.16.0-linux-x64.tar.xz**[/COLOR]      [COLOR=#3465A4]**STG-backups-FF-89.0.1**[/COLOR]   [COLOR=#3465A4]**STG-backups-FF-94.0**[/COLOR]
[COLOR=#4E9A06]**dave@ubuntu20vm-desk**[/COLOR]:[COLOR=#3465A4]**~/Downloads**[/COLOR]$ sudo bash linux-brprinter-installer-*.*.*-* HL-3150CDW
[sudo] password for dave: 
[COLOR=#3465A4]**You are going to install following packages.**[/COLOR]
[COLOR=#3465A4]**   hl3150cdwlpr-1.1.2-1.i386.deb**[/COLOR]
[COLOR=#3465A4]**   hl3150cdwcupswrapper-1.1.4-0.i386.deb**[/COLOR]
[COLOR=#CC0000]**OK? [y/N] ->y**[/COLOR]

You now get to accept the License Agreements. There were two when I did this, one for each of the packages to be downloaded.
After a bit of text rolling up the screen, don't panic at any warnings, I did the following (my printer is networked and has a specified IP address). Skip down for USB devices like the HL-L2300D.

Restarting cups (via systemctl): cups.service.
lpadmin -p HL3150CDW -E -v dnssd://Brother%20HL-3150CDW%20series._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-30055c6f6985 -P /usr/share/cups/model/Brother/brother_hl3150cdw_printer_en.ppd
lpadmin: Printer drivers are deprecated and will stop working in a future version of CUPS.
#
[COLOR=#CC0000]**Will you specify the Device URI? [Y/n] ->y**[/COLOR]


[COLOR=#3465A4]**0: ipp**[/COLOR]
[COLOR=#3465A4]**1: beh**[/COLOR]
[COLOR=#3465A4]**2: cups-brf:/**[/COLOR]
[COLOR=#3465A4]**3: https**[/COLOR]
[COLOR=#3465A4]**4: http**[/COLOR]
[COLOR=#3465A4]**5: ipps**[/COLOR]
[COLOR=#3465A4]**6: lpd**[/COLOR]
[COLOR=#3465A4]**7: socket**[/COLOR]
[COLOR=#3465A4]**8: hp**[/COLOR]
[COLOR=#3465A4]**9: hpfax**[/COLOR]
[COLOR=#3465A4]**10: dnssd://Brother%20HL-3150CDW%20series._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-30055c6f6985**[/COLOR]
[COLOR=#3465A4]**11: lpd://BRN30055C6F6985/BINARY_P1**[/COLOR]
[COLOR=#3465A4]**12: ipp://Brother%20HL-3150CDW%20series._ipp._tcp.local/**[/COLOR]
[COLOR=#3465A4]**13 (I): Specify IP address.**[/COLOR]
[COLOR=#3465A4]**14 (A): Auto. (dnssd://Brother%20HL-3150CDW%20series._ipp._tcp.local/?uuid=e3248000-80ce-11db-8000-30055c6f6985)**[/COLOR]

[COLOR=#CC0000]**select the number of destination Device URI. ->13**[/COLOR]

[COLOR=#CC0000]** enter IP address ->192.168.0.105**[/COLOR]
[COLOR=#3465A4]**lpadmin -p HL3150CDW -v socket://192.168.0.105 -E**[/COLOR]
[COLOR=#CC0000]**Test Print? [y/N] ->y**[/COLOR]

For a **USB** connected printer, e.g. HL-L2300D:
[COLOR=#CC0000]**Will you specify the Device URI? [Y/n] ->n**[/COLOR]

All being well, you should shortly get a test print out of your printer.
Took me less than 10 minutes to install my printer, which included reading the forum thread.

---

### Post by pqwoerituytrueiwoq on 2021-12-04
I have this exact printer at my mom's place hooked up with xubuntu 20.04 i had no issues with it using the driver, i do not print often so maybe i never had the problem?
i have a HL-L2360DW personally cause i wanted a wired network jack (i got sick of HP and the ink not working every time i print cause it is 'old', i swear i never got 10 pages out of a cartrage)

i think i used the driver from brother
[https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128](https://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128)
[COLOR=#000000][FONT=sans-serif]Pretty sure i used the CUPSwrapper printer driver one[/FONT][/COLOR]

i think the driver included with newer release like 21.04 should work better though that driver does not offer the toner saver feature
as of now the driver i can get from brother for my HL_L2360DW does still seem to work on 22.04 (developed branch, released this coming April)

after installing the driver you will find you have 2 printer, the official driver one's name is just the model of the printer (the shorter name)

---

### Post by aj34 on 2022-04-23
Nearly five months on and I'm still getting occasional print refusals but, seeing as you folks were kind enough to give some of your time, thought I'd give an update...

Thanks urBob and [ 						 							]("https://ubuntuforums.org/member.php?u=865458")[[COLOR=#000000]pqwoerituytrueiwoq[/COLOR]]("https://ubuntuforums.org/member.php?u=865458")[COLOR=#000000] for your replies - I thought the thread had finished and only just noticed your posts!

I really don't understand the CUPS thing and my limited knowledge prevents me from understanding any articles on the subject, beyond general layman's explanations. However, I may be able to follow detailed instructions. To that end, I followed urBob's excellent detailed instructions and almost got it right. In fact, I snatched defeat from the jaws of victory. I incorrectly answered "y" to the question: Will you specify the device URI?. I realised my mistake only when I saw the last line which told me to answer "n" for USB connected printer (which the printer is).

So now, my second printer (an old HP Photosmart 8450 - and network connected) seems to think it's my Brother HL-L2300D because it prints instead, even when I specify the Brother as default. Maybe this is because I accidentally set up a networked printer instead of a USB printer? Can I possibly undo the damage I've done? How do I go about that? If I can remove (uninstall?) my mistakes, I should be able to start again, hopefully. Thanks for reading.
[/COLOR]

---

### Post by him610 on 2022-04-23
> Can I possibly undo the damage I've done? How do I go about that?
Yes, you can.
Just go to Settings -> Printers - a window should pop up showing your installed printers. Delete the misconfigured printer then reinstall.

If this addresses your problem, please use Thread Tools to mark this thread as Solved.

---

### Post by aj34 on 2022-04-26
Thanks for your reply. Will do this when I have a few mins. spare then mark thread as solved if successful.

---

### Post by aj34 on 2022-05-28
Hurrah! Success at last. Mind you, that's several weeks I'll never get back.

Thanks to all for your support, much appreciated.

---

