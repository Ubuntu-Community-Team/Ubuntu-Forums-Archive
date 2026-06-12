---
title: "how to configure dial up modem"
date: 2008-07-21
forum: Hardware
---

### Post by jkohler2 on 2008-07-21
I just bought the Official Ubuntu  Book, and it does not show how to configure modems.  I know there are hardware driven modems (usually external) software driven modems (often called winmodems) usually internal, and now there are external USB connected modems.

Nowhere in the book does it show how to configure **any**of those types of modems.  Any help????

John

---

### Post by bigonegotaway on 2008-07-21
This may help:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by lswb on 2008-07-22
Personally I use the pppconfig program. This is started from a terminal by typing "sudo pppconfig" and answering the questions. There is also gnome-ppp and wvdial. You can search for these and other programs using synaptic and just enter the keyword "modem" or maybe dialup, etc.

With a hardware modem, everything should "just work" For a soft modem or winmodem, you may have to do a little research and install a driver. Do you have a specific modem you need to configure?

---

### Post by Henry04 on 2008-07-22
Hi,

I'm in a similar pickle, but with out the book :). I found the following in the help file [I]in Ubuntu:
[/I]
"Identifying your modem

    * Internet and Networks
    * Modems

Most dialup modems are not supported by Ubuntu, but drivers can be found that will enable the use of some such modems. First you need to identify what chipset your dialup modem is:

   1.  Download scanmodem ([http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz)) using a computer with an Internet connection.

   2.  Copy the downloaded file to the Home folder of the computer with the dialup modem you wish to use.

   3.  Open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the following commands, pressing Return after each line:

      				
      gunzip -c scanModem.gz > scanModem 
      chmod +x scanModem
      sudo ./scanModem 
      gedit Modem/ModemData.txt
      		
   4.  A file containing information on the chipsets used by any detected modems should open. Print or save the information.

      			Much more detailed information is available  on the community wiki."

I already know what my modem is... but the computer in Ubuntu apparently does not. That said, I did download the above named scanModem file & it now sits on my Ubuntu desk top... ***I have no idea where the "the Home folder of the computer with the dialup modem you wish to use" is.  ***

This may or may not be of help in obtaining a functional driver, I sure would like to know, as may the original poster for the modem driver question here.  ](*,) 

Thanks for any clues toward this end.

---

### Post by bigonegotaway on 2008-07-24
Is your modem a Winmodem or Hardware modem?

---

### Post by bigonegotaway on 2008-07-24
Check out this link:

[http://en.wikipedia.org/wiki/Winmodem](http://en.wikipedia.org/wiki/Winmodem)

---

### Post by lswb on 2008-07-24
> **Henry04 said:**
> Hi,
I already know what my modem is... but the computer in Ubuntu apparently does not. That said, I did download the above named scanModem file & it now sits on my Ubuntu desk top... ***I have no idea where the "the Home folder of the computer with the dialup modem you wish to use" is.  ***

This may or may not be of help in obtaining a functional driver, I sure would like to know, as may the original poster for the modem driver question here.  ](*,) 

Thanks for any clues toward this end.

That sentence could have been more clearly worded as "copy the file to your home directory in the computer with the dialup modem..."

The Desktop folder is just a subdirectory of your home directory, so to copy it to your home, just open a terminal (the terminal starts with your home directory as the current working directory)  and type the command:

cp Desktop/filename .

(Note the capitalization of Desktop and the dot . at the end of the command. )

Then proceed with the directions you quoted.

---

