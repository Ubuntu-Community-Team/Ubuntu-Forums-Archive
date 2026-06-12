---
title: "[SOLVED] Desktop Lexmark 1300 Printer"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by f37u5g0d on 2007-10-23
When I try and open the "deafault printer" thingy from the System menu it says " CUPS server error:
The CUPS scheduler is not running."

What is the CUPS server / CUPS scheduler?  Why isn't it running?  How can I make it run?  What else do I need to do to get my printer to work?

---

### Post by f37u5g0d on 2007-11-07
When I open "printing" from the administrative menu under system the window opens but I cannot connect to the server "localhost" because of an error during the CUPS operation.  What does all of this mean?  What is the CUPS operation.  Why do I need to connect to a server for a local printer? I was able to connect to the server once but I didn't install my printer because I didn't know where the driver was on my windows partition.

---

### Post by dabl on 2007-11-07
> **f37u5g0d said:**
> 

 I didn't install my printer because I didn't know where the driver was on my windows partition.



Huh?  You're not trying to install a Windows driver on a Linux system, are you?

CUPS is the _C_ommon _U_nix _P_rinting _S_ystem used by Linux:

[http://www.cups.org/](http://www.cups.org/)

Unfortunately, Lexmark printers are very poorly supported in Linux, and a quick check here:

[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

does not indicate that a driver is available for your 1300.  :(

---

### Post by MzHopsing on 2007-11-10
I too have 1300 printer I just bought for my niece, and it won't work with Edubuntu that I put on their puter (since upgrading from ME was too outrageously expensive).  I found on the Lexmark site that they provide a "Linux Driver Kit" in this vicinity here [http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html]("http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html")  But after 20 minutes of reading, I'm STILL not sure if this kit supports the 1300, but it doesn't look good.

What are the options at this point?  Do I have to buy her a different printer?  A different OS?  A high powered rifle???  

Edubuntu looks so great, I hate to yank it over a printer problem.  Any help would be appreciated!! :(

MzHopsing

---

### Post by alladnsane on 2008-01-14
I have tried just about everything and can't get my z1300 to work in Ubuntu.  Lexmark replied to my inquiry saying pretty much too bad.  They have no plans for linux support.  I have quite a few people try to help me in various places to no avail - but thank-you for the efforts.

Was wondering if maybe b/c Mac's are unix based and print using CUPS, whether it would work for someone to install the OSX supported drivers for the z1300 and then provide me with the generated ppd file??   Would this work or would I still need drivers other than the ppd file??

---

### Post by Shampyon on 2008-02-03
Bump. 

I've got myself a z1300 too. I'm lucky enough to have a housemate with a windows-based notebook, so I just get him to print my stuff. I've noticed that a fair few people have made the same mistake we have in purchasing this printer, though.

---

### Post by HermanAB on 2008-02-03
You can set up a Virtual Machine with XP or you can sell the printer on Ebay.

---

