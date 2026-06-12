---
title: "Lubuntu 14.04 LTS with Apollo p 1200 printer-Vol.2(original is closed)"
date: 2017-02-12
forum: Hardware
---

### Post by q123q on 2017-02-12
Hi All,

I've had a post about the same problem, but that is closed, so I can not post there.
[https://ubuntuforums.org/showthread.php?t=2242570](https://ubuntuforums.org/showthread.php?t=2242570)

The problem:my printer does not work.The new task is appears in the printing queue,  but its gone after half a second.The printer is recognised by the  Lubuntu.It is in the printers list.

Op system: Lubuntu 16.04 LTS  32bit
Printer: Apollo P 1200

Installed the PPD file, the printer appears where is should do, but does not work.It does worked for few months, then it stoped working again.I've reinstalled the driver,and after few attempts it usually started working.But it is so cr@p that every 2-3 months I have to do this.Now I installed 10 times still not working.
I know nothing about when updates upgrades were done.I am not use this PC.It should not effect anyways.Comparing to Windows XP, in 2017 this still has a lot of little bugs in it.
Any help welcome.

---

### Post by Autodave on 2017-02-12
I feel your pain. Unfortunately, Linux drivers do not always work because someone has to actually sit down and write one: the printer suppliers for the most part do not write drivers for Ubuntu. And to make it worse, printer drivers are a lot like printer ink cartridges: manufacturers seem to make every new printer with new cartridges and drivers.

If there are more Apollo drivers listed, you can always try a different one: I have had success with that before. Sometimes 2 or 3 tries, but if you have a few minutes to experiment it might be worth your time.

---

### Post by pdc on 2017-02-12
so I wondered if you had looked on the Open Printing site; as it is a great source of information and support for printing in linux;

your printer gets a mention: [http://www.openprinting.org/printer/Apollo/Apollo-P-1200](http://www.openprinting.org/printer/Apollo/Apollo-P-1200)

they say it should work perfectly with what they call the pcl3 driver; .......... so this would be where you got the pcl3 driver from? [http://www.openprinting.org/driver/pcl3](http://www.openprinting.org/driver/pcl3)

I see they say that "**Apollo is a subsidiary of HP, selling HP designs in a new casin**g."

Can we ask you about you set up the system to use the ppd file please: do you access it from CUPS? [http://localhost:631/](http://localhost:631/)

---

### Post by q123q on 2017-02-17
Hi All,

thanks for the answers, but the openprinting driver does not work.I've tried the newest,and the oldest too.With the old one it says:'Filter error' and with the new one it disappears  from the printing queue without any action.
I think I'll need to buy an Ubuntu friendly printer.
Could you give me somebody a suggestion which are the most Ubuntu friendly printers today?

Thanks

---

### Post by q123q on 2017-02-17
I was watching Youtube videos about how to install a printer on Lubuntu.I noticed that the printer should appear in the device list during install.My one didn't. Then I went to the 'System Information' tab and looked for the printer there. I saw under the 'Printer stat' that it is trying to connect.So there was no connection.So I pulled out the paralel cable,and disassembled the plug.Then back again.Used the screws to secure it tight at the back of the PC. 
After that it appeared during the installation process device list. 
And voila! It works!

Thank you all for the help.I hope it will work, and won't stop again.

---

### Post by pdc on 2017-02-17
well done; glad it works, and it sort of vindicates the open-source driver;

_____________

thinking back after you have solved things ......... for anyone following in the future .............

Ubuntu provide a how-to for when printers seem to play up: [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

if yours is a parallel connection they talk of the commands to check parallel ports but I guess the best command would be > [COLOR="#FF0000"]lpinfo -v[/COLOR]       ....... which is **Find out if your printer gets detected by CUPS**: a useful command for us all 

so very well done to get it all working and enjoy

---

