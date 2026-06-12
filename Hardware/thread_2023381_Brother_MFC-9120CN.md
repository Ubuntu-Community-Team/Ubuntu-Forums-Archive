---
title: "Brother MFC-9120CN"
date: 2012-07-12
forum: Hardware
---

### Post by cmcanulty on 2012-07-12
Im am trying to get our networked MFC installed in Ubuntu 12.04. 2 problems I can't get it  to scan. I can get it to print after hours of tweaking and so many tutorials I don't think I could ever duplicate it and I have 10 computers to go!Also I cannot get to printer properties at all to troubleshoot. I am attaching screenshots of the printer window and the menu to show printing properties is nowhere to be found. I need help badly. The library puts up with me using Ubuntu on our public machines but stuff has to work This is ridiculously hard. I am not an expert.Well the menu disappears when I click screenshot but believe me no printers is on list.I am using classic version no effects of 12.04.

---

### Post by jmfal on 2012-07-12
Click on the printer you want to checkout and right click and click on properties

---

### Post by irv on 2012-07-12
I was looking for drivers for a Brother's printer at the chapel, and I ran across a couple of webpages. I don't know it they will help, but here they are:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html")

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html")

---

### Post by cmcanulty on 2012-07-12
I have all the drivers installed and I can print to it but not scan.I am attaching a screenshot of the printers and nothing happens on right click. I know excactly what you mean as it used to work that way

---

### Post by irv on 2012-07-12
> **cmcanulty said:**
> I have all the drivers installed and I can print to it but not scan.I am attaching a screenshot of the printers and nothing happens on right click. I know excactly what you mean as it used to work that way

Is there anything under options?

---

### Post by cmcanulty on 2012-07-12
Just this. It drives me crazy that they took out so many configurations lately or made them impossible to find.

---

### Post by irv on 2012-07-12
> **cmcanulty said:**
> Just this. It drives me crazy that they took out so many configurations lately or made them impossible to find.

I would say, there's nothing under Options. This is what drives me crazy, the Hardware Manufactures don't do a good job of supporting us Linux users. They just take for granted that everyone uses Windows or Mac. I wish they would wake up.
Good Luck on getting this going. Hopefully there is someone out here who has overcome this problem or someone has an idea what to try next.

---

### Post by jmfal on 2012-07-12
Try clicking on "librarian" or "guest",  then hold mouse over that one and right click.

I know it sounds stupid, but sometimes thats what you have to do

---

### Post by cmcanulty on 2012-07-12
I'm sorry I don't get I click on librarian then click on what ? System settings doesn't show any properties for any printer anymore and yet I know the HP mprinter we have has a lot of options.Other threads say click on librarian or user then printers but printers isn't in that menu.Printer properties just seems to be gone, this is a major hassle.

---

### Post by jmfal on 2012-07-12
I'm sorry for not being so clear

Click on librarian in options section to highlight it

Then hold pointer over librarian (highlighted area) and right click

This should bring up more options

---

### Post by cmcanulty on 2012-07-13
No it doesn't on my home laptop (same model) printers is listed under the login button top far rt and by going there I see the printers and can rt cl for properties but in the library laptops no printers are in that menu. So I somehow have to add printers to that menu, any ideas?

---

### Post by jmfal on 2012-07-13
I understand what you need,

All info I found say to hook printer to laptop and it will automatically detect, you say it wont. I looked for ways to add manually--no luck.

Are you running a print server??

---

### Post by cmcanulty on 2012-07-14
No it is a network printer and I can see it and print to it over the network but I can't scan This is a library no print server.

---

### Post by jmfal on 2012-07-14
There are some scanning utilities in synaptic but non are for a specific printer

Do a quick search of "scanner" in synaptic   

 I have simple-scan and sane-utilities installed  for my hp f2480.

---

### Post by cmcanulty on 2012-07-14
I have installed all scanning pkgs and tweaked o end but still won't scan

---

### Post by jmfal on 2012-07-14
Are you using cups and samba

There are some conflicts between the two, just use cups

---

### Post by jmfal on 2012-07-14
CM take a look at this

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

---

### Post by cmcanulty on 2012-07-14
I am not using samba as I am not interacting with windows it is ethernet cabled to wall and on network as I  have said I can print to it but not scan

---

