---
title: "Tutorial: HOWTO Install Brother DCP-8110DN Laser Printer on Ubuntu"
date: 2013-10-26
forum: Hardware
---

### Post by Bjorg on 2013-10-26
As continuation of my efforts to install Brother DCP-8110DN Laser Printer on Ubuntu, finally I made it, so I want to share with you all how I did it.

This is how I have done it.

With the help of this page: [http://www.conocetupc.cl/te-ayudamos-ubuntu-faq/25-sobre-ubuntu/41-instalando-impresora-brother-dcp-j125.html](http://www.conocetupc.cl/te-ayudamos-ubuntu-faq/25-sobre-ubuntu/41-instalando-impresora-brother-dcp-j125.html)

And with the official instructions, This web page takes you to the download page of the drivers and to the instructions.: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-8110DN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-8110DN) 

Brother's cupswrapper driver page for my printer: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Brother's LPR driver install page for my printer: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

I am installing this printer on Ubuntu 13.10 just a week after 13.10 was released. The drivers that Ubuntu tries to install by default, from the gutenprint project, fail. So I have to do it manually. Possibly if Ubuntu polishes and fixes the default installation method it may work, as it was working by default in Ubuntu 13.04.

I am connecting to the printer via USB. I am later version of this tutorial I will explain how to connect via LAN.

I download these two files from the mentioned Brother's pages.

```
dcp8110dnlpr-3.0.0-1.i386.deb 
dcp8110dncupswrapper-3.0.0-1.i386.deb
```

In theory can choose to install either the CUPS one or the LPR one. But it seems that if you choose to install the CUPS one, you have to install first the LPR one and then the CUPS one. And this is what I am going to describe, how to install both in order to get the CUPS driver to work. I am choosing CUPS as it is more modern.

Procedure: 
1) Install Apparmor utils (with sudo agt-get install apparmor-utils or with the Ubuntu software centre)

```
sudo agt-get install apparmor-utils
```

2) Let's tell Apparmor (aa) not to complain (aa-complain) about CUPS (cupsd package)

```
sudo aa-complain cupsd
```

3) Let's create a directory necessary for the installation. But in my case Ubuntu replied that the directory was already present.

```
sudo mkdir /usr/share/cups/model
```

4) Let's install some utilites for the scanner (that I will describe how to install later in a second, expanded version of this tutorial)

```
sudo apt-get install sane-utils tcsh
```

5) Let's install the LPR driver (of course you need to navigate with the command line to the folder where you have donwloaded the driver file) (Quick tip: Use "cd" to navigate in the command line, example "cd Documents" to go to a subfolder called Document inside your present folder, or "cd .." to go to an upper folder)

```
sudo dpkg -i --force-all dcp8110dnlpr-3.0.0-1.i386.deb
```

6) Let's install cupswrapper driver

```
sudo dpkg -i --force-all dcp8110dncupswrapper-3.0.0-1.i386.deb
```

7) Let's check if the LPR driver and cupswrapper driver are installed

```
dpkg  -l  |  grep  Brother
```

This is the output I get in my computer for this command:

> ii  dcp8110dcupswrapper                       3.0.0-1                                 i386         Brother DCP-8110D CUPS wrapper driver
ii  dcp8110dncupswrapper                      3.0.0-1                                 i386         Brother DCP-8110DN CUPS wrapper driver
ii  dcp8110dnlpr                              3.0.0-1                                 i386         Brother DCP-8110DN LPR driver
ii  printer-driver-ptouch                     1.3-6                                   i386         printer driver Brother P-touch label printers

8) I am connecting to the printer via USB. Now let's check via the CUPS interface if the printer is present. Open a browser and go to:

```
http://localhost:631/printers
```

Following the official instructions we should

  >   Check if the Device URI of your printer is "usb://Brother/(your printer's model name)"

    If the device URI is different from the example above, please go to "Modify Printer" of your printer to select proper device and driver How to do this: Click on the printer's name; you are sent to another page, that should display the URI in the "Connexion" area.

The output I get from the CUPS interface in my computer is:

>     usb://Brother/DCP-8110DN?serial=E70745A3N358848

Also as a side note, in my case, the first time I printed a page a very first and unsolicited page was printed saying that I had installed the wrong driver, but I know I did everything correctly. Also this page has not appeared again:

In my computer the printing works well.

---

