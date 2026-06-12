---
title: "Brother HL-2150N network install failed"
date: 2010-02-09
forum: Hardware
---

### Post by mral4000 on 2010-02-09
hey up

just got off the phone from Brother tech support

tried installing the lpr and cups files... no errors showed all the way through and everything seemed to install.  hit the web CP and modified printer to see it on the network but started coming up with errors;

CUPS server error
There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

Status messages: 'Printer HL2150N may not be connected'  :confused:

Thing is I've modified the setting on the web CP to connect it locally through USB and then the printer works fine (so obviously the drivers work)

Cant understand whats wrong and I need this working on the network as there's 3 other machine running ubuntu in the office....

didnt realise it would be this complex - installed a HP laserjet on linux comps in another building the other day - found it straight away and connected. simple.

hope someone can help
cheers

---

### Post by mral4000 on 2010-02-09
Heres a copy of the instructions brother support emailed me
may be useful to others

actually no - for some reason I cant copy and paste it from my email.

I want to like Linux - but it has screwed with our business more than anything!!!

---

### Post by ewvdrijst on 2010-07-13
Try to use the HL-8170N Foomatic/hpijs-pcl5e (or otherHL-8170N) driver. These work fine for mine 2150N.

Or you could try to install the brother drivers.
[HL2150N driver]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2150N")

---

