---
title: "TC/ICP local network printer installation"
date: 2011-03-25
forum: Hardware
---

### Post by Anacleto85 on 2011-03-25
Hi,

I'm a PhD student and I have installed Ubuntu on my pc, within my University Departemant office. In our department we have a local network printer.

Well, I have add this printer as local, with an IP code, I see it when I should print a document, or other, but I can't print because the printer does not see my personal code. However, I have not found where can I insert it. 
The installation guide tells about a TC/ICP printer add on Windows, but I don't found nothing similar when I try to add a printer with Ubuntu System -Administrator - Printing.

If someone can help I will be very gratified, because I am enthusiastic of Ubuntu and I would not use Windows no more!!!

Thanks in advance

Best regard

Anacleto

---

### Post by dandnsmith on 2011-03-25
> but I can't print because the printer does not see my personal code
Sounds like there is some security/cost control in effect.
Do you have any idea what the department is using for this, as you may need a special front-end interface to tell the printer?

HTH

---

### Post by Anacleto85 on 2011-03-25
This I don't know.
But when one add a print on Ubuntu, what is the equivalent of TC/ICP?

---

### Post by wildscribe on 2011-03-25
As dandnsmith suggested, you should ask the IT department if you need a security code to use the printer. If that is the case you might have some problems. I have found that most printer security programs are only written for Mac and Windows, but hopefully it is not the case here.

Here are a couple troubleshooting experiments you might try. 

Open Terminal (found in Applications > Accessories > Terminal) and try pinging the IP address for the printer. Like $ ping 192.168.xx.xx and see if you get a response. If you don't get a reply, it's a network issue.

If it asks for "TCP/IP" add the IP address for the printer. (Note you can usually get the printers IP address by pushing the start button a few times or if there is a Windows computer already configured to use it, go to settings and get the printer's IP address from there. 

You can also try to connect to the printer using manual mode. Go to System > Administration > Printing and click on "Add" and then choose "LDP/LPR Printer" and once the window pops up, type the IP address in the Host window. 

Ubuntu generally does a great job finding printers on its own.

---

### Post by Anacleto85 on 2011-03-28
> **wildscribe said:**
> As dandnsmith suggested, you should ask the IT department if you need a security code to use the printer. 

I already know that I need a password to use the printer, indeed I already have one that I have used to print when I'm on Windows.

> **wildscribe said:**
> 
You can also try to connect to the printer using manual mode. Go to System > Administration > Printing and click on "Add" and then choose "LDP/LPR Printer" and once the window pops up, type the IP address in the Host window.


I have already do this, indeed I can "see" the printer when I try to print some document. However, when I send the printing the printer do not print (sorry for repetition:D).

The problem is that, while in Windows when I go to the properties of the printer I can found a place to put my personal password, here in Ubuntu printer's properties I can set anything but not my personal password!!!

---

### Post by Anacleto85 on 2011-03-28
I have just checked the properties of the printer form windows, and there an authentication button is present, after that you can introduce your account and password. Indeed, I have remembered that when I have installed the printer on windows my lecturer give me the driver for the printer.

In your opinion, something is possible. At worst, I can continue to print from windows sheltered.

Thanks a lot for your attention. 
:)

---

