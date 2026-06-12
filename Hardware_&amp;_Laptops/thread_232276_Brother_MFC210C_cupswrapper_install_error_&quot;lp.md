---
title: "Brother MFC210C cupswrapper install error &quot;lpadmin: Unable to copy PPD&quot;"
date: 2006-08-08
forum: Hardware &amp; Laptops
---

### Post by ningsean on 2006-08-08
My brother MFC210C was working a couple of days ago, but after I did an upgrade, it does not work anymore. I tried to reinstall the driver and the cups wrapper following the intructions here ([http://ubuntuforums.org/showthread.php?t=105703)](http://ubuntuforums.org/showthread.php?t=105703)), where I got the printer worked last time. The LPR driver installation went fine, but when I tried to install the wrapper, I got the following error

```
(Reading database ... 118580 files and directories currently installed.)
Preparing to replace cupswrappermfc210c 1.0.0-1 (using cupswrappermfc210c_1.0.0-1_i386.deb) ...
Restarting Common Unix Printing System: cupsd.
Unpacking replacement cupswrappermfc210c ...
Setting up cupswrappermfc210c (1.0.0-1) ...
rm -f /usr/lib/cups/filter/brlpdwrapperMFC210C
Restarting Common Unix Printing System: cupsd.
lpadmin: Unable to copy PPD file!

```

I tried to chmod for all files in /usr/share/cups/model and /etc/cups/ppd, but it did not work.

Anybody please give me some ideas?

Thanks a lot!!

---

### Post by ningsean on 2006-08-10
Problem solved.
I looked into /var/log/cups/error_log and find the following error:
```
E [10/Aug/2006:14:13:30 -0500] CUPS-Delete-Printer: Unauthorized
E [10/Aug/2006:14:13:34 -0500] CUPS-Add-Modify-Printer: Unauthorized
E [10/Aug/2006:14:13:34 -0500] [cups-driverd] Unable to open "/usr/share/ppd/brmfc210c_cups.ppd" - No such file or directory
E [10/Aug/2006:14:13:34 -0500] copy_model: empty PPD file!
E [10/Aug/2006:14:13:34 -0500] PID 10465 (/usr/lib/cups/daemon/cups-driverd) stopped with status 1!

```

So I did the following
```
cp /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd/
```

Everything works now!

---

### Post by orsula on 2006-10-31
I followed your steps but nothing happened. Still getting "receiving Data" on the MFC210 but no printing. I had the same errors you had in  /var/log/cups/error_log .

Would you have any ideas?
WHen I open the printer's properties, I have nothing under the advanced tab or the paper tab. Did yo uhave that too at some point?

---

### Post by bad_friday on 2006-11-29
I'I'm using debian. I've had a similar problem. Then I've made a
     > ln -s /u/share/cups/model/brmfc210c_cups.ppd/usr/share/ppd/brmfc210c_cups.ppd 
and then I had to make
     > chmod g+w and o+w /tmp
this solved my problem

---

### Post by livinginx on 2007-01-03
I am running Edgy with an MFC-420CN, this is my update:

Ran in to the can't copy ppd error like above, so I did
```
cp /usr/share/cups/model/brmfc420cn_cups.ppd /usr/share/ppd/
```

Then, I was still running into issues.  Funny thing, I went into the system > admin > printers  screen and removed the 420cn, added new printer graphically and it worked.  I am using the CUPSWrapper, but have it set up LPR as I am have it networked for ease of use. :-D

---

### Post by Martin Olof Andersson on 2007-03-10
Wonderful post. I got my Brother Network Printer working. I did almost the same thing in Suse about a year ago but forgot how to do so it was nice to find clear instructions.

---

### Post by Venzor on 2007-03-17
This is a FAQ from Brother for Edgy, which covers this exact topic

[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#60)

Following these directions solved my problem ^_^

---

### Post by Bwakas on 2007-04-02
using ubuntu edgy       I have a very similar problem. i have a Brother DCP-115c i have installed MFC210  as instructed on the Brother website - but when i try to print the print is sent to the printer but nothing happens thereafter. I have trolled through the forum for a suitable solution but nothing so far - please help i am almost giving up on ubuntu!  Ps very new to linux

---

### Post by alanandhispc on 2007-04-05
i have a dcp-115c too, i got it working by doing after following brothers guide:

sudo cp /usr/share/cups/model/brmfc210c_cups.ppd /usr/share/ppd/
sudo chmod g+w /tmp
chmod o+w /tmp
sudo /etc/init.d/cups restart

that way, i was then able to set the paper size and print quality.

Hope this helps

---

