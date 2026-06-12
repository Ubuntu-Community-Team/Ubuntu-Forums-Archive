---
title: "Brother Printer is not printing"
date: 2010-02-24
forum: Hardware
---

### Post by Ladyglutter on 2010-02-24
I purchased a new Brother MFC-495CW printer after seeing that Brother did indeed have Linux drivers.  I followed the instructions on the site and set up the printer according to the manufacturer's instructions.  I'm having two problems:

1.  Generally speaking, the print service does not work.  I have had to reinstall CUPS three times (pretty much after startup) for printing services to even be active.  When I do reinstall CUPS, it can see the printer, and I can try to print something.  If I do not reinstall CUPS, trying to load of the print service can take several (>10) minutes to load, and then shows no printers.

2.  When I print something the printer says "receiving data" and then it... just doesn't print the data.  I've networked this printer to an XP machine, and it has been able to print.

Now there are a few things that I noticed when I was following Brother's instructions.  I downloaded both files, as indicated by the manufacturer, but when I installed them, they didn't seem to be for the 495.  When setting things up, the closest "recommended driver" was for the 4**6**5.  I triple checked the download, and it repeats.  I did have a little trouble finding the 64 bit drivers at all.  I'm still not convinced that they actually are 64-bit.

I'm running 9.10 64 bit, Kernel 2.6.31-19-generic, GNOME 2.28.16 on an HP pavilion quad core AMD Phenom 9850 with 6 GB of RAM.  

Any advice?

---

### Post by robmf23 on 2010-02-24
It looks like you're following Brother's instructions, but did you try just the usual Ubuntu printer setup process? I would try deleting the configuration you currently have and just plugging the printer back in, go to System -> Admin -> Printing. Click "new." Find your printer and follow through the steps when prompted. Hopefully, Ubuntu will automatically install everything for you. 

Hope this helps. :P

---

### Post by Ladyglutter on 2010-02-24
When I go follow the prompts for selecting a new printer, the printer is found, and it searches for downloadable drivers, but finds nothing.  It gives me a list from a database, or I can select a ppd (which I don't know about) or search for a file, which give me nothing to search.  I try to link to the mfc495cwlpr-1.1.2-1i386.rpm file Brother instructs me to download, but this isn't what Ubuntu is wanting at this point.  The driver database does not contain my printer.  I'm at a loss.

---

### Post by sgosnell on 2010-02-24
.rpm is a Fedora/Mandriva/SuSE installation file, and what you need is a .deb file.  You can install alien and convert the .rpm to a .deb, but there should be .deb files available from Brother.

Did you read and follow the instructions on [this page](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html), which details the things you need to do before installing the driver.  It has specifics for both Ubuntu in general, and for the 64-bit version.  If you don't do all that, you may not get good results.

---

### Post by robmf23 on 2010-02-24
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW)

There's a link to the .deb file I believe you need.

---

### Post by Ladyglutter on 2010-02-24
Okay - I've looked for the .deb, and I looked at those instructions.  Those instructions are what I followed earlier (a few days back), and I didn't have any issues, as far as I know.  

I'm looking at the installation instructions, and to be honest, I'm really not sure just which file I'm suppose to be trying to use as the printer driver.  The .deb are for 32-bit architecture and I have to force it to open, and then I have several files I don't recognize.

I appreciate the patient advice, but I'm getting a lot of errors.  I'm going to clean things up and start from scratch, running through the whole process once again.  I'm not really sure why this has to be so complex.  Any further advice would be greatly appreciated.

---
*Update*

Okay, I just followed all of the steps sqosnell indicated, and had done so previously.  Everything checks out.

I am unsure just how I'm supposed to "#4 Install the driver", from this robmf23's link.  I keep receiving this message in the terminal:

desktop:~$ dpkg -i --force-all mfc495lpr-1.1.2-1.i386.deb
dpkg: operation requires read/write access to dpkg status area

What does that mean.  I'm sorry for asking neophyte questions.  I'm pretty new to this.

---

### Post by plucky on 2010-02-24
> desktop:~$ dpkg -i --force-all mfc495lpr-1.1.2-1.i386.deb
dpkg: operation requires read/write access to dpkg status area

What does that mean. I'm sorry for asking neophyte questions. I'm pretty new to this. 


You have to use **sudo** before the dpkg command.
```
sudo dpkg -i --force-all mfc495lpr-1.1.2-1.i386.deb
```

It will ask for your password,which it won't echo,just type it and press enter.

Good Luck

---

### Post by Ladyglutter on 2010-02-24
Ah, of course - 

*tries it out*

Hrm... I am getting another error now, which suggests that I'm supposed to do something prior to this command, though I'm not sure what that is.  Here is the error:

dpkg: error processing mfc495lpr-1.1.2-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc495lpr-1.1.2-1.i386.deb


Any ideas?

---

### Post by plucky on 2010-02-24
> dpkg: error processing mfc495lpr-1.1.2-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
mfc495lpr-1.1.2-1.i386.deb


You are not in the correct directory.

You can either open Nautilus and navigate to where the .deb file resides and double click on it to install.

Or ```
cd <directory where .deb resides>
``` and then run sudo command.


Good Luck

---

### Post by sgosnell on 2010-02-24
You did everything, including ```
# Pre-required Procedure (2)
    Related distributions
    Ubuntu8.04/8.04.1, Ubuntu8.10, Ubuntu9.04
    Related products/drivers
    cupswrapper printer/PC-FAX drivers
    Requirement
    1. "sudo aa-complain cupsd" command is required before the installation.
    2. "sudo mkdir /usr/share/cups/model" command (as it is) is required before the installation. 
```
```
# Pre-required Procedure (4)
    Related distributions
    Debian, Ubuntu
    Related products/drivers
    printer/PC-FAX drivers
    Requirement (superuser authorization is required to run the command) 
    "mkdir /var/spool/lpd" command is required if the folder does not exist. 
``````
# Pre-required Procedure (5)
    Related distributions
    Debian 64 bit version, Ubuntu 64 bit version
    Related products/drivers
    printer/PC-FAX drivers
    Requirement
    ia32-libs or lib32stdc++ is required to be installed. 
``` all that?  It should install, once you get to the right directory.  

If you buy a brand-new printer model, you're not likely to see the drivers already installed in the OS, regardless of what the OS is.  It may take some work to get it going, but it shouldn't be too difficult.  And in the bargain, you learned something, no?

---

### Post by Ladyglutter on 2010-02-25
Moving to the correct directory did it.  Thank you all so much!

---

### Post by 45-70 on 2010-04-28
I am having the same issue with directory.  I have the 2 .deb files in my home/ryan directory but when I type "cd /home/ryan" I get nothing.  If I type "cd /home" I get moved to the home directory but cannot change to my directory.  Hell I would move the files to the home directory if it would let me.  Why can't I just cut and paste the files to the home directory?

Thanks

Ryan

---

### Post by wojox on 2010-04-28
Just open your terminal and type **ls**

---

### Post by 45-70 on 2010-04-28
Ok I typed ls

ryan@Toshiba-laptop:~$ ls
Desktop    examples.desktop                      Music     Templates
Documents  mfc495cwcupswrapper-1.1.2-2.i386.deb  Pictures  Videos
Downloads  mfc495cwlpr-1.1.2-1.i386.deb          Public


now what

Ryan

---

### Post by 45-70 on 2010-04-28
I think I finally got it.

thanks to wojox


Ryan

---

### Post by wojox on 2010-04-28
Step 1 Create lpr drive:
------------------------

```
sudo mkdir /var/spool/lpd
```

Step 2 Install lpr driver:
--------------------------

```
sudo dpkg -i --force-all mfc495cwlpr-1.1.2-1.i386.deb
```

Step 3 Create the model dir:
----------------------------

```
sudo mkdir /usr/share/cups/model
```

Step 4 Install wrapper:
-----------------------

```
sudo dpkg -i --force-all mfc495cwcupswrapper-1.1.2-2.i386.deb
```

Step 5 Add printer:
-------------------

Go to System > Admin > Printing. Delete printer and have it search for a new one.

---

