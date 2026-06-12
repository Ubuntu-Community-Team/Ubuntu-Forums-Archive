---
title: "Uncorrected errors in Ubuntu 17.04 when I try to install / dual boot another OS"
date: 2017-07-31
forum: Hardware
---

### Post by afz12 on 2017-07-31
I have a HP Envy notebook running Ubuntu 17.04 and everything works fine. However when I make a USB pen to install another OS alongside Ubuntu I eventually get an error message "... uncorrected errors, fix these to proceed..." and of course the installation stops. Afterwards I reboot and  things seem to work fine.

This occurs with any OS - the current one I tried was Mint 18.2 but this OS works fine dual booting on another slightly older notebook. Therefore this is a problem with this notebook using Ubuntu 17.04 and definitely not anything related to other hardware or other OS.

I have checked the notebook disk using its DOS utility - complete tests no errors. Also the Ubuntu recovery options all return no errors.

I suspect if I completely install an OS it will work as it has done in the past. However installing any other OS alongside this one (and some previous ones) consistently fails.

Are there other diagnostics I can try on its hard drive? Is there some setting that is persistent and wrong? When Ubuntu 17.10 is ready I'd like to dual boot this but it won't work due to "uncorrected errors". What could these errors be? 

I have run other OS in Virtualbox all work fine, including Mint 18.2 - this also dual boots in a slightly older notebook so I don't think the OS is faulty. Any suggestions are welcome of course :p.

---

### Post by BenginM on 2017-08-01
Hiya , so you get this error when installing these OSs on the same partition ! you may want to preform a filesystem check fsck from recover mode on that partition you're trying to install on .

---

### Post by afz12 on 2017-08-02
Hi BenginM

I have checked using the Ubuntu utility - no change. Also the same procedure works fine on another slightly older notebook (HP dv6). Previously, dual or triple boot has been no problem. The setup procedure can be set to install another OS alongside the previous one and resize the disk - all goes well until the final phase and then I get this error message - quite confusing.

---

