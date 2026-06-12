---
title: "Installing printer driver for Canon Pixma G1000"
date: 2017-04-24
forum: Hardware
---

### Post by droidzoneub on 2017-04-24
First let's get the unpleasantness out of the way. Yes, it's the fault of Canon that they don't release open source or binary drivers for many of their printers. But I ended up buying a Canon anyway before realizing that it didnt have a Linux driver. 

What have I done to solve this?
1. I have tried installing PPDs of models that appeared similiar to the G1000. The printer did not print. There werent any errors in cups. It finished printing according to the printer monitor, but there wasnt any print.
2. I found out that Canon had released OSX drivers, so I tried to "port" the PPD over to Linux. I've uploaded the ppd to [github]("https://github.com/droidzone/canong1000").
[COLOR=#111111][FONT=Ubuntu]
To port this driver, the steps I did include extracting the PPD file from the Mac OSX .dng file by mounting the dng as an iso, inflating a .pkg file, gunziping it etc.  Then I extracted it into a .drv file:

[/FONT][/COLOR]```

ppdi -o canong1000.drv CanonIJG1000series.ppd

```

[COLOR=#111111][FONT=Ubuntu]I then removed osx specific entries including Attribute "APPrinterPreset". I changed filters from MacOSX versions to rastertocanonij and cmdtocanonij2. I then compiled the .ppd with:
[/FONT][/COLOR]```

ppdc canong1000.drv

```[COLOR=#111111][FONT=Ubuntu]

and compiled and installed filters from the c[nijfilter2 source]("https://github.com/dbnicholson/cnijfilter2"). [/FONT][/COLOR]

Added a printer using this ppd, restarted cups.

[COLOR=#111111][FONT=Ubuntu]Unfortunately the error message that cups shows is "filter does not work". On setting the loglevel of cups at debug, I found the following errors:

```

[FONT=Consolas]D [24/Apr/2017:23:22:40 +0530] [Job 38] 4 filters for job:[/FONT]
```[/FONT][/COLOR]```

D [24/Apr/2017:23:22:40 +0530] [Job 38] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
I [24/Apr/2017:23:22:40 +0530] [Job 38] Started filter /usr/lib/cups/filter/bannertopdf (PID 26026)
I [24/Apr/2017:23:22:40 +0530] [Job 38] Started filter /usr/lib/cups/filter/pdftopdf (PID 26027)
I [24/Apr/2017:23:22:40 +0530] [Job 38] Started filter /usr/lib/cups/filter/gstoraster (PID 26028)
I [24/Apr/2017:23:22:40 +0530] [Job 38] Started filter /usr/lib/cups/filter/rastertocanonij (PID 26029)
D [24/Apr/2017:23:22:40 +0530] [Job 38] PID 26029 (/usr/lib/cups/filter/rastertocanonij) stopped with status 255 (Unknown error 155)
D [24/Apr/2017:23:22:40 +0530] [Job 38] PID 26026 (/usr/lib/cups/filter/bannertopdf) exited with no errors.
D [24/Apr/2017:23:22:40 +0530] [Job 38] PID 26027 (/usr/lib/cups/filter/pdftopdf) exited with no errors.
D [24/Apr/2017:23:22:40 +0530] [Job 38] envp[9]=\"PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin\"
D [24/Apr/2017:23:22:40 +0530] [Job 38] PID 26028 (/usr/lib/cups/filter/gstoraster) exited with no errors.
E [24/Apr/2017:23:22:40 +0530] [Job 38] Job stopped due to filter errors; please consult the error_log file for details.
D [24/Apr/2017:23:22:42 +0530] [CGI] envp[9] = "PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin" 
D [24/Apr/2017:23:22:42 +0530] [CGI] cgiSetArray: job_printer_state_message[0]=\"Filter failed\"

```

[COLOR=#111111][FONT=Ubuntu]There were no compiler errors during make of the cups filters. I'm not sure where the error is in the filters, or whether this printer is incompatible with these filters, or whether there is an issue in the ppd file.
How would I proceed to get my printer working in Ubuntu? Please dont comment asking me to request Canon to support it. I've already contacted them through Support and twitter. They dont seem inclined to. Unfortunately I cant exchange this printer and am stuck with it for the next couple of years.

I would very much like your help solving it.
I'm on [/FONT][/COLOR]Linux Mint 18.1 Serena 64 bit.[COLOR=#111111][FONT=Ubuntu]


[/FONT][/COLOR]

---

### Post by pdc on 2017-04-24
sorry to hear of your troubles; I agree their website [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) doesn't offer linux drivers for the G1000 and the G2000, but for the G3000 they offer they offer 32bit and 64bit linux drivers in rpm, debian and source code format; and the same for the G4000

I see the driver they offer for the G3000 is the [COLOR="#0000FF"]cnijfilter2-5.30-1-deb.tar.gz[/COLOR] (file version [COLOR="#0000FF"]5.3[/COLOR]) [http://support-asia.canon-asia.com/contents/ASIA/EN/0100713101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100713101.html) and for the G4000 it is the [COLOR="#008000"]cnijfilter2-5.40-1-deb.tar.gz[/COLOR] (file version [COLOR="#008000"]5.4[/COLOR]) [http://support-asia.canon-asia.com/contents/ASIA/EN/0100839901.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100839901.html)
____________
so the install for the above is
cd Download
tar -zxvf cnijfilter2-5.30-1-deb.tar.gz
cdcnijfilter2-5.30-1-deb
sudo ./install.sh
____________

it seems to me that all recent releases of linux drivers have involved this core **cnijfilter2-5** and for example, for the MG7770 it is the cnijfilter2-5.20-1-deb.tar.gz (file version 5.2) ....... they no longer specify the printer, it is just the cnijfilter2-5

you can find the beginnings of this cnijfilter2-5 driver for the MG6670 in Sept 14 cnijfilter2-5.00-1-deb.tar.gz

___________

I am just wondering if some version of the cnijfilter2-5 would not drive such as the G1000 and G2000; ...... I see it is file version 5.3 for the G3000 and 5.4 for the G4000 so I wonder if it can't deliver what is needed; 

_______
the folks at Turboprint don't list a driver for the G series; [http://zedonet.com/en_p_turboprint_driver.phtml?&mfg=Canon](http://zedonet.com/en_p_turboprint_driver.phtml?&mfg=Canon) but I see the G is only sold in Malaysia and nearby countries?? so maybe it hasn't been launched in Europe; but generally Turboprint can offer drivers

---

### Post by droidzoneub on 2017-04-24
Thank you for the help!
I removed the existing cnijfilter package, edited installed.sh to reflect my model name, ran the installation. Everything went fine. I made a new symlink for the ppd to point to the new ppd installed.

When I started printing, the printer blinked twice and completed the job. No errors, but no print either. This is the cups log: [https://pastebin.com/gW46umy8](https://pastebin.com/gW46umy8)
This is odd-I dont know how to proceed

---

### Post by limpama on 2017-09-28
see [https://blog.droidzone.in/2017/08/07/how-to-install-printers-for-canon-pixma-g2000-on-ubuntu/](https://blog.droidzone.in/2017/08/07/how-to-install-printers-for-canon-pixma-g2000-on-ubuntu/)

You'd better to understand Canon has no mind to support linux driver for g1000. (they recommended g3000 ilo g1000. T..T idiots~! )
I've googled and found that 'turboprint' or 'gutenprint''re only possible way to make print work in my xubuntu system.

Turboprint works perfectly but is not a free-software. (30 days trial may be helpful. but~~)
I've installed gutenprint (I found these packages are already included in Ubuntu packages but it didn't work at all. I don't know the reason. Anyway, I downloaded source packages and did 'make and install' as the blog said above.)

After installing gutenprint, I received a message to g1000 printer registered. And I tried to print out a test-print at printer monitoring console...BUT~!! it failed again,....,if you also received a printer-status-message as '~~ rendering completed~~' and printer's stuck, then check CUPS daemon. In my case, I found that CUPS doesn't have any registered printer, therefore I register g1000. Finally, it worked perfectly.  Try, at web-browser, type address of 'localhost/631' -> go to admin menu -> add printer.

---

### Post by droidzoneub on 2017-09-28
Thanks for sending me my blog as solution. :P
Yup, I solved it with gutenprint. I moved away from g1000 to g2000 which also doesn't have drivers. gutenprint works perfectly for scan, and after working with the dev of sane, now scanning too works perfectly.

---

### Post by widz001 on 2017-11-26
So you got your G1000 working right now? Actually I have the same problem using my raspberry pi as printer server and already installed gutenprint. But still didn't registered yet

---

### Post by pdc on 2017-11-27
and the other option seems to be Turboprint [http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_G1000series](http://www.zedonet.com/en_p_turboprint_driver.phtml?printer=Canon_PIXMA_G1000series) they have been suppliers of very high quality printer drivers since the Amiga days.

---

