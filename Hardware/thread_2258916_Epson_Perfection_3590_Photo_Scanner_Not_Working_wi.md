---
title: "Epson Perfection 3590 Photo Scanner Not Working with 12.04"
date: 2014-12-31
forum: Hardware
---

### Post by digitography on 2014-12-31
sane and xsane are both installed, neither work.

I have so far tried the following:
sudo mkdir -p /usr/share/sane/snapscan
cd /usr/share/sane/snapscan
sudo wget [http://demonipuch.free.fr/Esfw52.bin](http://demonipuch.free.fr/Esfw52.bin)


open file /etc/sane.d/snapscan.conf with gedit :
Code:
sudo gedit /etc/sane.d/snapscan.conf


and change this line :
firmware /usr/share/sane/snapscan/your-firmwarefile.bin


to :
firmware /usr/share/sane/snapscan/Esfw52.bin


Save and exit.
Reboot.
My user account is in the Scanner group.
The scanner is plugged in and powered and can be seen from doing a 
lsusb
Bus 002 Device 002: ID 04b8:0122 Seiko Epson Corp. Perfection 3590 scanner

sane-find-scanner
returns
found USB scanner (vendor=0x04b8, product=0x0122) at libusb:002:002

So what am I missing here?

All help gratefully received.

---

### Post by slickymaster on 2014-12-31
*Moved to the ***Hardware*** sub-forum*

---

### Post by digitography on 2015-01-01
Thank you, I will do that.
However so far no takers, and I really have no idea where to go from here.
Been googling this issue for a couple of days, still no real answers.

---

### Post by coldraven on 2015-01-01
I have been using the advice on this page for many years for my E P 1670 and it has always worked
[http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)

It obviously uses a different firmware file but the method should be the same but I put the file in /etc/sane.d/
The code below is just for example, don't run it!
```
$ wget http://www.commercialventvac.com/~jeffs/ESFW30.BIN
$ sudo cp ESFW30.BIN /etc/sane.d
```


> Edit /etc/saned.d/snapscan.conf and change the line...

firmware /path/to/your/firmware/file.bin

...to point to /etc/sane.d/ESFW30.BIN




Maybe it does not matter where the firmware file goes as long as the path is correct in the snapscan.conf

---

### Post by Mike_Walsh on 2015-01-02
I don't know if this is of any help:-

[http://manpages.ubuntu.com/manpages/hardy/man4/uscanner.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/uscanner.4.html)

I wouldn't like to say whether the installed kernel drivers actually include this particular module. The manpage would seem to indicate that **uscanner**&#8203; is required for your model to work.


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-01-02
Just a thought; it's a bit of a long shot, I know, but had you considered trying the data and scanner software packages that are currently available for the all-in-ones?

The majority of Epson's all-in-ones need to have printer & scanner packages installed separately. Although there are quite a number of different printer packages available, there appear to be only a couple of data and scanner packages out there, to cover everything they've turned out during the last decade.

I can't see that their scanner technology & software have changed THAT much over the last 10 years.

It's got to be worth a try. ;)


Regards,

Mike.

---

### Post by digitography on 2015-01-05
Thank you for the replies.

Coldraven, that is almost exactly the same as what I have already done. This approach worked in 10.10 but since 12.04 has not (I did not bother with 11.xx)

Mike_Walsh, my scanner is covered by uscanner, however I have not been able to install
sudo apt-get install uscanner simply comes back with not found. It does not appear in Synaptic either.

---

### Post by digitography on 2015-01-06
OK so I have the uscanner file downloaded, how do I use it?

---

### Post by pdc on 2015-01-08
so digitography;

when I go to the Epson linux support page; and enter 3590, it takes me here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15831&DSCCHK=dc314c7561f36b1e0796b28c20038ddc9fc14ff3](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15831&DSCCHK=dc314c7561f36b1e0796b28c20038ddc9fc14ff3)

and it looks as though the only package is for rpm and so for debian (and that means Ubuntu), one would need to download the tar.gz file, so you need the iscan_2.10.0-1.tar.gz

_________________

you can see they provide an instruction manual userg_revG_e.pdf that has many pages; worth a read

______________--

I see the readme in the tar.gz says > A number of non-free plugins are available separately that provide support for the following scanners:

the install instructions seem to be:

cd Downloads
tar -zxvf iscan_2.10.0-1.tar.gz 
cd iscan_2.10.0-1
./configure
make
sudo make install

and one can run iscan from the terminal with ```
iscan
```

______________________________________________________________

the iscan plugin package you need comes from here 

[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15855&DSCCHK=e2557510a6cd86a28b8664a265bc00ebb2615c5b](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=15855&DSCCHK=e2557510a6cd86a28b8664a265bc00ebb2615c5b)

it only seems to come as an rpm package; [COLOR="#0000FF"]iscan-plugin-gt-f520-1.0.0-1.c2.i386.rpm[/COLOR] so one could convert with alien 

if you want advice on that, please ask

---

### Post by digitography on 2015-01-13
PDC thanks for the reply.

I  was fairly sure I had tried that, but thought I would again.
The ./configure appears to finish without any errors, however when I try to "make" 

it fails the final line reads

make: *** [all] Error 2

Which means nothing or very little to me, other than I know it hasn't worked.

---

### Post by digitography on 2015-02-23
Well I finally came back to this issue, after installing 14.04 (clean install).

Still no joy.

However I found a thread somewhere that suggested running 

scanimage -L in a terminal window.

This initialises the scanner

I then ran simple-scan and boom it works.

I tried to create a script that would run scanimage -L before it launched simple-scan

I put a 2 second sleep in between the commands, just incase there were some timing issues.

The script runs fine, but doesn't initialise the scanner.

It's no great hardship to open a terminal and run scanimage -L and at least I now don't have to run a Virtual copy of XP to get around this, however it would be good if I could fix it properly.

---

