---
title: "How to install printer 32bit printer drivers"
date: 2011-03-15
forum: Hardware
---

### Post by sc4s2cg on 2011-03-15
I finally made the switch to Ubuntu over the weekend, now the only thing I use Windows for is Office 2010, and SimCity.

We have a home server (fedora) that has the Brother HL2270 DW printer connected to it, and our household sends print jobs to it. Problem is, Brother only has 32 bit drivers for Ubuntu. Is there a way to install these to my 64 bit Ubuntu? If not, is there anyway to print to that printer using a makeshift driver? I don't need anything fancy, just a way to print on the printer and an option to print front and back.

I am pretty new to Linux, but can use the terminal and know the very basics (cd, sudo, etc. commands).

---

### Post by Mark_in_Hollywood on 2011-03-15
This is all I could find.

[http://www.linuxquestions.org/questions/linux-hardware-18/need-help-getting-brother-hl-2270dw-printer-to-work-with-ubuntu-10-04-a-848196/](http://www.linuxquestions.org/questions/linux-hardware-18/need-help-getting-brother-hl-2270dw-printer-to-work-with-ubuntu-10-04-a-848196/)

According to Brother, the printer will work under 64-bit, please see:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/evaluation.html)

If you want to be walked through this, I will try to help. You will need to Private Message me, so we can set a day and time. If you use Skype that would be helpful.

---

### Post by sc4s2cg on 2011-03-25
Thank you for the link, it was very helpful.

I was able to install the driver successfully using Brother's tutorial.

What I did:

1. [Install]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2270DW") cups and lpr .deb drivers
2. Follow these [instructions]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html") to install drivers
3. System -> Administration -> Printing
4. Add -> Network Printer -> Windows Printer via SAMBA [Despite my server being Fedora 12]
5. Input info, including share password.

And now it works like a charm. Key thing for me was, I didn't add the printer as a windows printer, and instead used the "Find Network Printer" option. Even though the printer was found, it wouldn't print. The SAMBA option worked perfectly.

---

