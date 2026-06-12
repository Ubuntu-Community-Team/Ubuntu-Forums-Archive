---
title: "Brother DCP-115C/DCP-330C"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by _asc_ on 2007-01-10
Hello!

I want to get a new multifunctional printer. I have narrowed it down to the Brother DCP-115C and the Brother DCP-330C.

From the Brother Linux driver page, I have seen that you have to use the driver for the Brother MFC-210C and I have also found an installation guide on these forums. So it seems that the DCP-115C is working with Ubuntu. The DCP-330C has its own driver and should therefor work as well.

My questions are:

(1) Are there any drawbacks in using the MFC-210C driver for the DCP-115C or is this really an optimal solution? 

(2) Is the DCP-330C the better solution for Linux because it has its own driver?

(3) To DCP-115C and DCP-330C users: What is you experience with the printer?

---

### Post by Chilli Bob on 2007-02-24
I've just spent about 5 hours trying to install a DCP-115C (which has been a great little unit running under Win98), and it still won't print. I have followed the How-To exactly. The printer is showing in System-Administration-Printing as a MFC210C, (this is the driver the Brother site says to install) but it won't print. It gives no error message, the job just sits in the print queue. When I try to load the Xsane i get the error dialog

 "Failed to open device 'brother2:bus1;dev1':
Error during device I/O"

Can anyone advise?

---

### Post by ziggykg on 2007-04-20
I had a DCP-330C running in Edgy using a HOWTO.  It run well but not yet able to get the scanner to work (good thing I've got a Windows VMWare installation).  Yet to test on Feisty.

[Update]
I've now got the DCP-330C printer to work in Feisty using Brother's CUPS driver and following this [HOWTO]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html").  Please note that I used only the CUPS driver and not the LPR one.

---

### Post by Kynan on 2007-04-22
> The printer is showing in System-Administration-Printing as a MFC210C, (this is the driver the Brother site says to install) but it won't print. It gives no error message, the job just sits in the print queue.

That is the exactly the same thing that happens with my dcp-115c. I managed to get it working in Edgy using this driver but since updating to Feisty i can no longer use this driver for some reason.
I followed the instructions [http://ubuntuforums.org/showthread.php?t=105703](http://ubuntuforums.org/showthread.php?t=105703) to the letter and it didnt work, so i then uninstalled them using synaptic and tried installing it using GDebi (installing lpr driver first and cups after and tried again stll the same result, it just sits in the print queue. I did notice however that i cannot change the print size and some other options usually available.
Any ideas?
and will they ever make a proper driver for this cheap common printer because id much like to ditch windows and just use ubuntu however i need windows to print.

---

### Post by slasherx2 on 2007-10-15
I managed to get this printer working in 7.04, however I recently upgraded to the gutsy beta and it broke it :(

Does anyone know of a guide for gutsy yet to get this printer to work?

---

### Post by wankel on 2008-01-09
For about half a year I also got a DCP-330C. 

It has cost me days of headaches to find out how to set it up for the first time. Reading through dozens of threads in English, German, Dutch, French and a few Scandinavian languages that I can not understand too well.

In the end it worked out in another way than I found so far, or maybe I missed the point in some threads.

Since it has been a while, I can not give a to the point howto, but it worked for me to install as root in a csh shell. The printer was not connected at that point (because I read numerous advices to turn off the printer).

(sudo aptitude install csh ; I ran as root via "su -" ; I got the password for root by doing "sudo passwd" to change the initial root password; after su - and giving the password, you're root. Be careful! Then I gave "csh" to change to a csh shell, and used dpkg to install the packages)

That way I got it to work on Feisty (2 systems). The upgrade to Gutsy broke one of them (??), Some time later, after some updates via apt and installing the driver again, it started working. 

That way it also worked on a clean install of Gutsy.

Hope this pointer helps!

---

