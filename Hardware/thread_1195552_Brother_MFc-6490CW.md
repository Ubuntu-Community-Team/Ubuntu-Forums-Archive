---
title: "Brother MFc-6490CW"
date: 2009-06-23
forum: Hardware
---

### Post by john1970 on 2009-06-23
Hi all,
I am looking for the driver for my Brother printer.  It is a MFC-6490.  The printer is wireless and is detected without any problems but it is not listed in the driver list and I was wondering if anyone knows which printer in the list do I select.  I went to the brother linux website but it does not state anything.  If anyone could help I would really appreciate it.
Thanks
John

---

### Post by duanedesign on 2009-06-23
sorry somehow I double posted :)

see post below.

---

### Post by duanedesign on 2009-06-24
you want the deb, not the rpm. at the bottom of the table there are links to instructions depending  on whether you install the cups or lpr driver. The site recommends CUPS option.

[http://solutions.brother.com/linux/en_us/download_prn.html#MFC-6490CW](http://solutions.brother.com/linux/en_us/download_prn.html#MFC-6490CW)

before installing run
```

sudo aa-complain cupsd

sudo mkdir /usr/share/cups/model
```

Download LPR driver and cupswrapper driver.

Turn on the printer and connect the USB cable.

Open the terminal and go to the directory where the drivers downloaded. On my system for example it would be.

```
cd /home/duanedesign/Desktop/
```

then install lpr driver

```
dpkg  -i  --force-all  --force-architecture  mfc6490cwlpr-1.1.2-2.i386.deb
```

install cupswrapper driver

```
dpkg  -i  --force-all  --force-architecture  mfc6490cwcupswrapper-1.1.2-2.i386.deb
```

that will get you too step 5a. or 5b. at [http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

depending on how your printer is connected determines which one you use.


good luck!!

---

### Post by john1970 on 2009-06-24
Thank you so very much.  That is just what I needed.  I really appreciate your thorough reply.
John

---

### Post by liferules on 2010-01-21
Thanks, worked like a charm!!

Have to say I am really enjoying this printer ... AWESOME ...

---

### Post by ceaxer on 2010-03-24
Hi 

I have a Brother MFC 6490 with an ethernet connection to the router. I can access all the functions (scan fax,print) on windows xp based workstation but can only print from Ubuntu. Is it possible to scan without a direct usb connection? 

If so How? 

Ceaxer

---

### Post by lars-i on 2010-04-10
Hello everybody:

I had problems installing my Brother MFC-6490CW according to the information mentioned above. Maybe because I in the first appoach did not know the prerequesites and first had problems only using LAN and no USB connection.
 
This is the way how it worked at my computer:

- perform all the prerequesites mentioned here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#002)

- perform the real installation mentioned here: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

- (restart the computer)

- create a new printer in the Ubuntu's printer administration (German: "Start-Button > System > Systermverwaltung > Drucken > Create new Printer"

- in the dialog "select device" (? German: "Wähle Gerät"): select "other"(? German: "Sonstiges")

- set the Geräte-URI: input the following: lpd://<defined_IP>/BINARY_P1
  at my network: lpd://192.168.0.4/BINARY_P1

- select the driver that was installed in the previous steps

Now it should work.

With kind regards,
Lars

---

### Post by liferules on 2010-06-15
I take back everything I said. This install worked perfectly in karmac but apparently it is broken in lucid. The drivers install fine but I cannot commandline print (lpr) at all. 

Any suggestions would be appreciated because I desperately need to get muttprint working again.

---

### Post by schaubleschreck on 2010-07-15
Hi Guys,

I was trying to download a driver for my MFC6490 (wireless connection), but I have a different system architecture: amd64. Are there drivers available for me?

Cheers!

---

### Post by jbfaden on 2011-01-24
To answer the previous post, the --force-architecture installs the 32bit on a 64 bit machine:  

[FONT=monospace] [/FONT]dpkg  -i  --force-all  --force-architecture  mfc6490cwcupswrapper-1.1.2-2.i386.deb 

My problem is when I do:
sudo dpkg  -i  --force-all  --force-architecture  mfc6490cwlpr-1.1.2-2.i386.deb

I get:
(Reading database ... 155960 files and directories currently installed.)
Preparing to replace mfc6490cwlpr 1.1.2-2 (using mfc6490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc6490cwlpr ...
Setting up mfc6490cwlpr (1.1.2-2) ...
mkdir: cannot create directory `/var/spool/lpd/mfc6490cw': No such file or directory

I don't have a /var/spool/lpd/ directory.  This is on ubuntu 10.04.

Thanks!

---

