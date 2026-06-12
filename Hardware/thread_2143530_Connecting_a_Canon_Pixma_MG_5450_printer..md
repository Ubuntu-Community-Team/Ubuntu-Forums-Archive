---
title: "Connecting a Canon Pixma MG 5450 printer."
date: 2013-05-09
forum: Hardware
---

### Post by rauer on 2013-05-09
As a newcommer to Ubuntu / Linux I need some assistance to install the printer.

I found a link were the procedure was described: [http://forums.linuxmint.com/viewtopic.php?t=123929&f=51](http://forums.linuxmint.com/viewtopic.php?t=123929&f=51)

So I downloaded the file cnijfilter-mg5400series-3.80-1-deb.tar.gz
Extracted it in my down loads folder ( as I have a Danis version this is called "Hentede filer" )
jens@jens-R540-R580-R780-SA41-E452-E852:~$ cd Hentede\ filer
jens@jens-R540-R580-R780-SA41-E452-E852:~/Hentede filer$ cd cnijfilter-mg5400series-3.80-1-deb
jens@jens-R540-R580-R780-SA41-E452-E852:~/Hentede filer/cnijfilter-mg5400series-3.80-1-deb$ ./install.sh

After this I got the following:

#=========================================================#
#  Connection Method
#=========================================================#
 1) USB
 2) Network
Select the connection method.[1]2

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.

Now I wonder if this is because my network is WPA/WPA2 secured and if so how can I connect through the terminal window?

Thanks in Advance

Rauer

---

### Post by pdc on 2013-05-11
You firstly need to connect the printer to your router; 

You can download the pdf instructions that Canon provide from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0300839501.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300839501.html)

If your router has WPS, you can use that method: see the wps.png

......when the router knows the printer is there, then you can re-run the install.sh script ....it should find  the device then

---

