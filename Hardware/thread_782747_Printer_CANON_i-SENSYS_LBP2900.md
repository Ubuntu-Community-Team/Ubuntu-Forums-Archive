---
title: "Printer CANON i-SENSYS LBP2900"
date: 2008-05-05
forum: Hardware
---

### Post by anpu1 on 2008-05-05
Hello!

I updated Ubuntu 7.10 to 8.04 and i have a problem. my printer CANON i-SENSYS LBP2900 is recognised in lsusb but when i want to print a document or pdf file it says error while printing and nothing happens! I had the same problem in ubuntu 7.10 and i hoped that in 8.04 it will be fixed but its not!!

please help to fix this cause i have to print documents :)

tnx!

Anpu

---

### Post by silvanus2005 on 2008-05-13
Take a look there:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)
You can download the newest Canon drivers for Linux from:
[http://software.canon-europe.com/products/0010419.asp](http://software.canon-europe.com/products/0010419.asp)
Let me know if it`s working. I will switch back to Windows untill the Ubuntu will recognize my Canon LBP 3000 printer and my scanner Canoscan Lide 90 out of the box.

---

### Post by silvanus2005 on 2008-05-14
Yesterday I installed Mandriva Spring 2008, I installed the drivers from Canon and my printer it`s working just fine. You should give it a try:)

---

### Post by anpu1 on 2008-05-19
> silvanus2005:
Take a look there:
[https://help.ubuntu.com/community/Ha...Canon_LBP_2900](https://help.ubuntu.com/community/Ha...Canon_LBP_2900)
You can download the newest Canon drivers for Linux from:
[http://software.canon-europe.com/products/0010419.asp](http://software.canon-europe.com/products/0010419.asp)
Let me know if it`s working. I will switch back to Windows untill the Ubuntu will recognize my Canon LBP 3000 printer and my scanner Canoscan Lide 90 out of the box.

this doesn't help me because i don't have ccpd file and i don't know how to create it! rooky i know :P

any help?

---

### Post by dungat on 2008-05-19
can you help me setup driver printer canon lbp2900 os ubuntu7.04.chip set intel x32.thanks

---

### Post by silvanus2005 on 2008-05-21
Take a look there:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

---

### Post by silvanus2005 on 2008-05-21
Today I have made a fresh install of Kubuntu 8.04, I also have installed the drivers provided by Canon and my Canon LBP3000 it„s working perfectly.

---

### Post by anpu1 on 2008-05-30
Hello again!

I installed ubuntu 8.04 everything work OK but the only thing i can't install is printer! Any ideas for ubuntu 8.04 and canon i-sensys lbp2900?

---

### Post by silvanus2005 on 2008-05-31
All you have to do it`s to follow the steps described in the link I posted above, and you should not have any problem. What can be so hard?

---

### Post by begemot. on 2008-06-06
I've had installed Canon 2900 at once as easy, as it wrote in many HowTo's, including Ubuntu-wiki, BUT now i got Canon i-SENSYS LBP2900B and it's not working in my Ubuntu 8.04.

---

### Post by silvanus2005 on 2008-06-07
Do you want to say that your printer appears in System-Administration-Printers but you can not print with it?

---

### Post by dungat on 2008-06-11
I've had installed Canon 2900 (cable usb to PC)("silvanus2005"  Take a look there:
[https://help.ubuntu.com/community/Ha...Canon_LBP_2900)...ok.but](https://help.ubuntu.com/community/Ha...Canon_LBP_2900)...ok.but) printer  it's not working.help me.thanks

---

### Post by anpu1 on 2008-06-11
silvanus2005 yes thats right!!! I'll try to install printer like dungat says!! and i'll report back!!

---

### Post by anpu1 on 2008-06-11
hehe ok it's not working anyways!!

if i make lsusb in terminal the computer sees the printer even in default printer tehere is LBP2900 installed but the printing job does not go thrue!! one time i even tryed to leave it for 3 houres but nothing came out of the printer :D

any ideas

---

### Post by dungat on 2008-06-11
installed Canon 2900  for ubuntu erro root@user-desktop:/usr/share/ppd# sudo /usr/sbin/ccpdadmin -p [printer model] -o /dev/usblp0

 [printer can't find in CUPS Spooler Entry!!
hepl me????? thanks

---

### Post by dungat on 2008-06-11
installed Canon 2900 for ubuntu erro root@user-desktop:/usr/share/ppd# sudo /usr/sbin/ccpdadmin -p [printer model] -o /dev/usblp0

[printer can't find in CUPS Spooler Entry!!
hepl me????? thanks

---

### Post by dungat on 2008-06-12
:( huhu help me!!!!.intall canon lbp 2900 for ubuntu.
thanks

---

### Post by silvanus2005 on 2008-06-19
[http://software.canon-europe.com/software/0028622.asp?model=](http://software.canon-europe.com/software/0028622.asp?model=)
download the drivers from Canon, install them following the instructions, and you printer should work. I did that for my Canon LBP 3000 and I have no problem. 
And one more thing - download also the instructions from Canon and follow them carefully, and your printer will work.

---

### Post by karl3 on 2008-06-27
lbp 3000 =/= lbp 2900 i-sensys

drivers v. 1.60 don't seem to be ok, so you need to install older v. 1.30 (to be found @ [ftp://download.canon.jp/pub/driver/lasershot/linux/](ftp://download.canon.jp/pub/driver/lasershot/linux/) ).

-> just follow the instructions from: [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900)

and use **v. 1.30 drivers** ... ok, it's not perfect, but at least it works...

solution found @ [http://www.linux.hr/modules/newbb/viewtopic.php?topic_id=1805&viewmode=flat&order=ASC&start=10&PHPSESSID=e7a50af93e6c0fbba487c36ec20473e5](http://www.linux.hr/modules/newbb/viewtopic.php?topic_id=1805&viewmode=flat&order=ASC&start=10&PHPSESSID=e7a50af93e6c0fbba487c36ec20473e5)

---

### Post by anpu1 on 2008-07-04
OOOOOOOK!

now i still can't install this damn printer on this comp.!!!! I'm starting to thing that the priter and the comp. are playing games with ME!!!

I mean what the hell???

ok any more ideas?

---

### Post by anpu1 on 2008-07-05
hello all!

Now i managed to print some pages but the thing is that when click to print nothing happens! and when i restart the computer the printer starts to work and prints the page i wanted to print before!

So when i understood what is going on i tried to print two documents! ok nothing happend but when i restarteed the printer printed only the first document i selected! the other document is pending!

so anyone plz help!! i'm a little lost here! its like the aliens are in my comp. LOL

tnx

---

### Post by anpu1 on 2008-07-15
anythign anyone? any ideas? plz HELP!!

---

### Post by Cotopaxi on 2008-07-16
First one question: is the printer connected as a USB printer or as a network printer?

My system is kubuntu, so you will have to try to translate my instructions to Ubuntu.

Do one check: go to System Settings>Printer and click on "Add new Printer/Class". Click yourself forward to the screen, where you do the "Backend Selection".

In this window you should be able to select: "Local Printer (parallel, serial, USB)". CAN YOU SELECT this option, or is it grayed out?

If this option IS grayed out, go to this link:

[http://kubuntuforums.net/forums/index.php?topic=3089184.0](http://kubuntuforums.net/forums/index.php?topic=3089184.0)

and follow the instructions in the second post of tomstrong. These instructions helped me to get my printer up and running after 4 weeks without printing!

Good luck!

---

### Post by dangis on 2008-10-26
I had the same problem with my CANON i-SENSYS LBP2900

"can’t find in CUPS Spooler Entry"

my mistake was writing LB2900 instead of LBP2900

/usr/sbin/lpadmin -p LB2900 -m CNCUPSLBP2900CAPTK.ppd -v ccp:/var/ccpd/fifo0 -E
so check your syntax!

This post helped me: 
[http://linuxforum.ru/index.php?showtopic=46085&st=0&p=454451&#entry454451](http://linuxforum.ru/index.php?showtopic=46085&st=0&p=454451&#entry454451)

---

