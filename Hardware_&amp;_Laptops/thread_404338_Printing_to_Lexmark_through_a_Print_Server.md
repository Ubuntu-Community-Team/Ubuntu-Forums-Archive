---
title: "Printing to Lexmark through a Print Server"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by beilman on 2007-04-08
I have a Lexmark Z605 that i'm trying to print to through a print server that i just bought.  I cannot get Ubuntu to print to it.  When i try to send a test page it acts like it's going, but nothing happens.  I have attached the printer to the computer directly through the USB port on the computer and it prints fine (i had to install the lexmark linux drivers with the help of a different forum).  So therefore i know my issues are with how i'm setting up the networking options for the printer configuration.  I've read a couple different forums that have said to use IPP and a couple others that said to use LPD, but i can't get either to work.  I just don't know where to find the information that needs to go into the fields for either setting.  I have looked on the print server's web interface for the information, but what i'm finding there must not be right because it isnt' working.  under the IPP field i tried ipp://<printserverip>:631/lpt1 but that didn't work.  I've tried many other combinations with no success.  I even tried letting ubuntu find the LAN printer.  It found it, but it didn't work.  Any help would be greatly appreciated.

---

### Post by camorri on 2007-04-08
I had remote printing working to a Lexmark printer. From what you have posted, you need to do two things. On your client, ( the one that does not have the printer),  you will need to add the linux print drivers for you printer. 

The reason is straight forward. Cups processes the file to its printable format locally, and sends the print file to the server. It does not use the drivers on the server to process the file. So until you have the drivers installed and your printer configured on the client, you will not print. 

Second, ```
ipp://<printserverip>:631/lpt1
``` This is not complete. 

The first part is correct, This line should include three fields. The second should be /printers/  exactly. It took me many hours of fusing and fuming to find that in the cups documentation. Just add it, and don't fuss with it. The third field should be the name of the printer as configured on the print server in cups. If you called it lpt1 fine,  but that is a generic name from dos days. So, look in cups on your server and see what name you gave it.

The result should look like this ipp://<printserverip>:631/printers/printername

---

### Post by beilman on 2007-04-08
Thanks a lot for the help although I think maybe i wasn't clear on what hardware I actually have set up.  My print server is just a small box that connects the USB printer to an Eithernet port which is then connected into the network.  There isn't an actual computer server.  The small print server box (a Hawking Technology HPS1U to be exact) has a web interface but very few variables that i can change.  As far as i can tell, there isn't a place to actually change the name of the printer in the print server setup, so lpt1 is just the name it gets also it doesn't use any printer drivers, only the computers printing to the printer have them.  I do have the drivers set up on the ubuntu machine from which i am trying to print.

as for the /printers/ part of the line, i entered that in the ipp field and tried a test page again and once again nothing came out.  it put the print in the queue but the printer didn't print.  After I update the field do i need to restart CUPS to get it to acknowledge the changes?  Thanks

---

### Post by beilman on 2007-04-08
well, if anybody is reading this and having similar problems i got it worked out.  I set the printer up as a LPD printer (the print server accepts this type of interface) and in the Host field i entered the ip address of the print server and in the queue field i entered the port name for the print server.  The queue field (from what i've read) may possibly be able to be changed on other brands of print servers but on mine it is fixed as lpt1.

---

### Post by camorri on 2007-04-09
I'm glad you had success. Thank-you for the clarification. I did not understand just what the print server was after your first post.

---

### Post by Don9307 on 2007-11-09
There is another consideration not mentioned in any of the replies.  While it is true your client PC must have the printer driver loaded in order to have print commands issued from the machine interpreted properly by the printer, it is equally important that the print server you are using be compatible with your printer.  If not, it doesn't matter if you have the correct printer driver on your PC, you aren't going to be able to print.  Case in point: I have a USB printer, a Lexmark X125, for which there is a suitable driver in ubuntu to communicate with the printer; however, checking with the printer OEM (Lexmark) after not having any print success with a particular print server, I was informed that Lexmark does not make any print servers for the model X125, nor is there any known OEM print servers that are compatible with the Lexmark X125.  I was astounded by this revelation.  So, if I want to connect my printer to a print server that is connected to my wireless network to handle multiple PCs (ubuntu and Win) all printing to the same printer through my LAN, then I must purchase a printer that is compatible with a print server, and there must be compatible printer drivers for that printer available in ubuntu- and Win OSes.  So many things to consider.

---

### Post by camorri on 2007-11-10
Since first posting to this thread, I solved my print problems by buying a Brother printer. It came with a linux driver and Windoze driver. I can print to it from winders, or linux, wired or wireless connections. 

Lexmark doesn't show much interest in Linux. Why should I bother with them?

---

