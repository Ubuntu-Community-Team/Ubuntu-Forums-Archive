---
title: "Brother printer slow on linux host, fast under XP guest!"
date: 2008-07-03
forum: Hardware
---

### Post by Ozdemon on 2008-07-03
I have a Brother MFC-8820D laser printer/scanner/fax.  I also have VirtualBox running XP for a couple of Windoze app's that I cannot replace.

Now I have downloaded the latest linux lpr and cups wrapper drivers from the Brother site for the printer.

The problem is that the printer prints about a page every minute or two under Ubuntu, but prints at 16 ppm when printing under XP in the VirtualBox!

So the problem must be the Linux driver (he thinks).  There is nothing wrong with the quality of the print when in Ubuntu, but the strong incentive is to boot into XP just to stop myself screaming.  I don't want to go down that path because sooner or later I will find it easier just to stay in XP.

So far this is the only real drawback of going over to Ubuntu and there are many, many pluses.

I am running 8.04 x 64.

I suspect the slow speed may have something to do with postscript

So the questions for anyone kind enough to consider answering are:
(i) can I replace the proprietary drivers with ANYTHING that will print faster?
(ii) how can I tell what driver my printer is using?
(iii) and for anyone technically minded, and purely out of curiosity, how is it that I can print at rated speed through a virtualbox that somehow must still be sending the signal via Ubuntu, but only print at a snails pace in Ubuntu?
:confused:

P.S. I tried but failed to do a dpkg --force architecture install of the drivers.  I got lpd could not be found and conflicting packages error messages.

---

### Post by Ozdemon on 2008-07-07
Since my last post I have noticed many other posts where people have used Brother drivers but experience very slow printing.  Does anyone know the answer?

---

### Post by Ozdemon on 2008-07-09
Well, after spending a long time on the phone today with a knowledgeable and friendly Brother tech support person I have the following to report:

(1) The BAD NEWS is that the lpr and cups drivers on the Brother site DO NOT work well with Ubuntu 8.04.  The reason is that the file locations have changed in 8.04 so that it takes the Brother software **much **longer to do any given job.  

(2) The GOOD NEWS is that the drivers available thru Synaptic DO work with 8.04.

So if you have the same problem as me then:

(i) Turn off the printer and remove the printer under system/printing.

(ii) Open Synaptic and search for any Brother software.  Then perform complete removal.  If this fails you can try and remove the Brother folder(s)and return to Synaptic and try again.  I wasn't able to, even with expert guidance because of dependency hell.  I had to re-install 8.04 - fortunately I had a separate /home partition :)


(ii) Reboot and go to Synaptic and do another search on Brother.  You should have nothing installed.  Then one at a time click on the cups files until you find your model.  Mark for installation.  It will auto add the correct lpr.

(iii) After installation switch the printer back on.  It should be auto detected. 

Test print speeds and then give a pint of blood.  I already have.

):P

---

### Post by davidryder on 2008-10-03
Wow. I finally got this to work! I followed the steps above, still nothing. So I went into the print dialog and clicked on "Change" next to "Make and model". I selected brother then when it asked me to choose the exact model I scrolled up and saw an entirely new set of drivers. Chose my model and now it flies!

BTW, it shouldn't be necessary to reboot. It wasn't for me. I did however restart the cups daemon just to be sure:

```
sudo /etc/init.d/cupsys restart
```

---

### Post by lucaspr on 2008-10-11
Finally some speed back in the machine! Printing was far too slow.. 

Thanx for this little guide Ozdemon and Davidryder

---

### Post by geomarcomputers on 2009-04-13
I am trying the above technique for a brother-mfc-8220 and ubuntu-8.04
I do not find any mention of mfc-8220 in any of the cups wrappers in synaptic
What can I do ? 
Thanks


> **lucaspr said:**
> Finally some speed back in the machine! Printing was far too slow.. 

Thanx for this little guide Ozdemon and Davidryder

---

### Post by mk6032 on 2009-09-04
I also have this problem. I'm running 9.04 amd64. I have installed a network card in the printer, as well as upgrading it to it's max of 160MB of RAM. I have tried both Ubuntu supplied drivers and the drivers from Brother's website. I can't find anything in the logs to show a problem.

---

### Post by harishcm on 2009-09-14
> **geomarcomputers said:**
> I am trying the above technique for a brother-mfc-8220 and ubuntu-8.04
I do not find any mention of mfc-8220 in any of the cups wrappers in synaptic
What can I do ? 
Thanks

Use the MFC-8500 cups wrapper driver. I finally got the proper printing quality and printing rate using it. It is mentioned in the page below.

[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

---

### Post by gazer22 on 2010-08-23
Updating an old thread.

This worked for me with Ubuntu 10.04 and a Brother HL-2170w printer:

[LIST=1]
[*] completely uninstall all "brother" packages from synaptic
[*] download driver (lpr & cupswrapper) from: 
       [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)
[*] "sudo aa-complain cupsd" (something to do with AppArmor)
[*] ensure that /usr/share/cups/model exists.  Make it if it doesn't.
[*] turn on the printer and connect the USB cable. (may or may not be necessary if you're setting it up as a network printer).
[*] Open the terminal and go to the directory where the drivers are.
[*] Install LPR driver :  "sudo dpkg  -i  --force-all  brhl2170wlpr-2.0.2-1.i386.deb"
[*] Install the cupswrapper driver: "sudo dpkg -i --force-all cupswrapperHL2170W-2.0.2-1.i386.deb"
[*] Check if the LPR driver and cupswrapper driver are installed : "dpkg  -l  |  grep  Brother"
[*] Configure your printer on the cups web interface
  [list]
    [*] Open a web browser and go to [http://localhost:631/printers](http://localhost:631/printers). 
    [*] Click "Modify Printer" and set following parameters.
    [*] Connection : "AppSocket/HP JetDirect"
    [*] Device URI : lpd://(Your printer's IP address)/binary_p1
    [*] Make : Brother
    [*] Model / Provide PPD File : **Choose the correct ppd file from /usr/share/cups/model**
  [/list]
[/list]

This last step is different than given by the Brother website, and makes all the difference.

---

### Post by marbura on 2010-08-26
> This worked for me with Ubuntu 10.04 and a Brother HL-2170w printer:

[LIST=1]
[*] completely uninstall all  "brother" packages from synaptic
[*] download driver (lpr & cupswrapper) from: 
       [http://welcome.solutions.brother.com....html#HL-2170W]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W")
[*] "sudo aa-complain cupsd" (something to do with AppArmor)
[*] ensure that /usr/share/cups/model exists.  Make it if it doesn't.
[*] turn on the printer and connect the USB cable. (may or may not be  necessary if you're setting it up as a network printer).
[*] Open the terminal and go to the directory where the drivers are.
[*] Install LPR driver :  "sudo dpkg  -i  --force-all   brhl2170wlpr-2.0.2-1.i386.deb"
[*] Install the cupswrapper driver: "sudo dpkg -i --force-all  cupswrapperHL2170W-2.0.2-1.i386.deb"
[*] Check if the LPR driver and cupswrapper driver are installed :  "dpkg  -l  |  grep  Brother"
[*] Configure your printer on the cups web interface
[LIST]
[*] Open a web  browser and go to [http://localhost:631/printers](http://localhost:631/printers).
[*] Click "Modify Printer" and set following parameters.
[*] Connection : "AppSocket/HP JetDirect"
[*] Device URI : lpd://(Your printer's IP address)/binary_p1
[*] Make : Brother
[*] Model / Provide PPD File : **Choose the correct ppd file from  /usr/share/cups/model**
[/LIST]
[/LIST]

This last step is different than given by the Brother website, and makes  all the difference. 	

Indeed! I had the same problem (though my printer is Brother DCP-7025, usb connection), and tried your solution and seems to work! =) And it ¡s true: the last step makes all the difference! Thanks!

---

### Post by bfrancom on 2011-08-09
> **gazer22 said:**
> Updating an old thread.

This worked for me with Ubuntu 10.04 and a Brother HL-2170w printer:

[LIST=1]
[*] completely uninstall all "brother" packages from synaptic
[*] download driver (lpr & cupswrapper) from: 
       [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)
[*] "sudo aa-complain cupsd" (something to do with AppArmor)
[*] ensure that /usr/share/cups/model exists.  Make it if it doesn't.
[*] turn on the printer and connect the USB cable. (may or may not be necessary if you're setting it up as a network printer).
[*] Open the terminal and go to the directory where the drivers are.
[*] Install LPR driver :  "sudo dpkg  -i  --force-all  brhl2170wlpr-2.0.2-1.i386.deb"
[*] Install the cupswrapper driver: "sudo dpkg -i --force-all cupswrapperHL2170W-2.0.2-1.i386.deb"
[*] Check if the LPR driver and cupswrapper driver are installed : "dpkg  -l  |  grep  Brother"
[*] Configure your printer on the cups web interface
  [list]
    [*] Open a web browser and go to [http://localhost:631/printers](http://localhost:631/printers). 
    [*] Click "Modify Printer" and set following parameters.
    [*] Connection : "AppSocket/HP JetDirect"
    [*] Device URI : lpd://(Your printer's IP address)/binary_p1
    [*] Make : Brother
    [*] Model / Provide PPD File : **Choose the correct ppd file from /usr/share/cups/model**
  [/list]
[/list]

This last step is different than given by the Brother website, and makes all the difference.

Worked for me as well!!!! Thank you!!!  Ubuntu 11.04, Brother MFC-7840W

---

### Post by zygmurti on 2011-10-12
Have been looking for days before I found this thread. Works for me as well.

I am running ubuntu 11.04 and Brother HL-5380DN. 

Thank you ever so much!

---

### Post by danielesil on 2012-10-06
Just by setting the thing you wrote in Bold everything worked GREAT !!!

Thank you very very much !!!

You just saved my life !!!

You ROCK :guitar: !!!

---

### Post by bfrancom on 2012-12-16
> **bfrancom said:**
> Worked for me as well!!!! Thank you!!!  Ubuntu 11.04, Brother MFC-7840W

Still have to do this in Xubuntu 12.10.
The difference in my case is that the URI used was this format for my network printer:
socket://<IP Address>:9100

---

