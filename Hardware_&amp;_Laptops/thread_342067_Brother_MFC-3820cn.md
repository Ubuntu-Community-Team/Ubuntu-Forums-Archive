---
title: "Brother MFC-3820cn"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by Mottq on 2007-01-19
I have intalled the drivers for my network printer and have the proper IP address. I still, however, get no response from the printer. I am a newbie and any help is appreciated .

---

### Post by tgm4883 on 2007-01-19
I had this same problem until I ran across a thread (I forget which one it was) but I did save it locally.

> leonya wrote:
ghostdawg wrote:

***UPDATE*** 

I found the Ubuntu forum's topic about Brothers printers and some say need to create a directory before installing the drivers. 

mkdir /var/spool/lpd 

So, I'll give this a try and see what happens.


I just got the printer to work on Ubuntu Edgy. Took me a couple hours! 

I had to: 
sudo mkdir /var/spool/lpd 
sudo dpkg -i --force-all mfc5440cnlpr-1.0.2-1.i386.deb 
sudo apt-get install csh 
sudo ln -s /etc/init.d/cupsys /etc/init.d/cups 
sudo dpkg -i --force-all cupswrappermfc5440cn_1.0.0-1_i386.deb 
Then opened [http://localhost:631](http://localhost:631), "Manager Printers" 
Should see the MFC5440CN printer, click "Modify Printer" 
Device is "AppSocket/HP JetDirect" 
Device URI is "socket://192.168.15.102" (printer IP) 
Provide PPD file from /usr/share/cups/model/brmfc5440cn_cups.ppd 

It works now (I was ready to give up on it already).


Congratulations! What a lot of work to get the driver installed properly. 

Thanks for the update, jimbo

---

### Post by lothar_m on 2007-01-19
i've installed a dcp-340cw using the brother drivers.

more info here [http://ubuntuforums.org/showthread.php?p=1780918#post1780918]("http://ubuntuforums.org/showthread.php?p=1780918#post1780918")

---

### Post by mrshawk92 on 2007-07-21
> **tgm4883 said:**
> I had this same problem until I ran across a thread (I forget which one it was) but I did save it locally.
You have saved my family's inability to print nightmare.  I am new to Ubuntu and was almost ready to give up trying to use and understand it.  However, the programmer in me had to win and plus I didn't have the money to purchase a new computer easily.  Ubuntu was the answer to a computer that was out of the door.  
My first hurdle was not being able to configure the Internet.  Upgrading to Fiesty Fawn fixed that. Next, the inability to print using my Brother MFC 5540CN.  Thanks soooo very much for this answer. We will be printing soon!  God Bless You! :popcorn::popcorn::KS

---

