---
title: "Can't install drivers for Brother MFC-J6710DW"
date: 2011-05-25
forum: Hardware
---

### Post by FuturistCorporation on 2011-05-25
This printer worked great for me when I was running Mac OSX. I put Ubuntu on my Macbook Pro 3,1 and now I am having trouble installing the driver I need (Brother MFC-J6710DW). The printer setup "wizard" in Ubuntu did not have this model listed in the list of drivers it found for the Brother printer (I guess maybe it's a newer model), so I downloaded the driver directly from the Brother website. The cupswrapper driver was not available for this model so I downloaded the lpr version (a .deb file). When I opened it with Ubuntu Software Center, it told me the file was not accurate or corrupt or inferior or something (don't remember the exact message) and I told it to install anyway. I have restarted my computer, but I still can't get my printer to show up on the list of available printers. Any help would be greatly appreciated.

---

### Post by wojox on 2011-05-25
Both drivers are [here.]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6710DW")

Download and save to your home directory or downloads ( where ever you save things )

Install through the [Command Line]("http://ubuntuforums.org/showthread.php?t=590793"). Start with Step 5.

---

### Post by Objekt on 2011-05-25
What he said.  I have a Brother MFC-7440N and I had to go through pretty much the same procedure.  

I followed the instructions at the Brother website.  They work, but the thread linked to above explains things better and may be more helpful.

---

### Post by FuturistCorporation on 2011-05-25
The command "sudo dpkg -i --force-all mfcj6710dwlp-1.1.1-1.i386.deb"
gives an error message (copied from terminal): 

"dpkg: error processing mfcj6710dwlp-1.1.1-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
 mfcj6710dwlp-1.1.1-1.i386.deb"

The name of my file is 

"mfcj6710dwlpr-1.1.1-1.i386.deb" (copied from file name)

Before I did this command, I did 

"cd Desktop" (where the file is) and "mkdir /var/spool/lpr"

---

### Post by wojox on 2011-05-25
> **FuturistCorporation said:**
> The command "sudo dpkg -i --force-all mfcj6710dwlp-1.1.1-1.i386.deb"
gives an error message (copied from terminal): 

"dpkg: error processing mfcj6710dwlp-1.1.1-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
 mfcj6710dwlp-1.1.1-1.i386.deb"

The name of my file is 

"mfcj6710dwlpr-1.1.1-1.i386.deb" (copied from file name)

Before I did this command, I did 

"cd Desktop" (where the file is) and "mkdir /var/spool/lpr"

What's the output of 

```
ls /var/spool
```

---

### Post by FuturistCorporation on 2011-05-25
> **wojox said:**
> What's the output of 

```
ls /var/spool
```

anacron  cron  cups  libreoffice  lintian  lpd  mail  plymouth

---

### Post by wojox on 2011-05-25
> **FuturistCorporation said:**
> anacron  cron  cups  libreoffice  lintian  [COLOR="Red"]lpd[/COLOR]  mail  plymouth

What's that? It should be lpr.

---

### Post by FuturistCorporation on 2011-05-25
> **wojox said:**
> What's that? It should be lpr.
Honest, that's what it says! I don't even know what I just typed in.

---

### Post by FuturistCorporation on 2011-05-25
I'm guessing it came from this (from the thread you linked me to):

> 
Step 6:
Create the lpd directory. This is the first I have encountered this but in Hardy the directory had to be created. Skip this and move on to Step 7 if you're using Gutsy or below. In terminal Type or Copy & Paste the following command:

Code:

sudo mkdir /var/spool/lpd


I put in the command "sudo mkdir /var/spool/lpr" just to be sure and then redid the problem command, but got the same result.

---

### Post by wojox on 2011-05-25
> **FuturistCorporation said:**
> I'm guessing it came from this (from the thread you linked me to):



I put in the command "sudo mkdir /var/spool/lpr" just to be sure and then redid the problem command, but got the same result.

You're right it should be lpd ( linux print driver )

Try:

```
sudo mkdir /var/spool/lpd/mfcj6710dw
```

```
sudo dpkg -i --force-all ~/Desktop/mfcj6710dwlpr-1.1.1-1.i386.deb
```

---

### Post by FuturistCorporation on 2011-05-26
Great, that installed the driver successfully! Now I am trying to set up this printer so I can use it, and my system doesn't recognize it yet. In the Administration -> Printing menu under add new printer I choose the option to search for the ppd file, but I don't have root access to the folder I just made (I'm the administrator). Is there a way to set up the printer from the terminal now?

---

### Post by wojox on 2011-05-26
How are you connected to the printer (wireless, usb, ...)?

---

### Post by FuturistCorporation on 2011-05-26
Usb

---

### Post by wojox on 2011-05-26
Go back into Administration -> Printing menu and delete any instance of a printer. Then Add printer and let it search. It should recognize it then. There maybe two options for Brothers.

---

### Post by FuturistCorporation on 2011-05-26
Right now I have no printers shown as installed. When I hit "add printer," it recognizes my Brother printer, but when it searches for drivers it apparently does not find any. It then takes me the same screen where it asks me to either select a printer from a database, provide a ppd file or search for a printer driver to download (and none of those options work right now).

---

### Post by FuturistCorporation on 2011-06-10
Apparently the Brother MFC-J6710DW printer is completely incompatible with Natty:

From the Brother website's FAQ:

> 
Q: I can not install printer driver on Ubuntu11.4(64bit)

A: Brother is currently developing a software for your Brother machine which will be released soon.


I'd appreciate a little speed on that, Brother!

---

