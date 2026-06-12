---
title: "How to check the SMART status of my storage-drive on my Ubuntu-linux box?"
date: 2019-05-10
forum: Hardware
---

### Post by dilbert_one on 2019-05-10
dear community, 



How to check the SMART status of my storage-drive on my Ubuntu-linux box?

well i have got issues with a notebook. Several installs and each time the machine does not run propperly.  i  think i have to runs a SMART-Test. 


background: S.M.A.R.T. (Self-Monitoring, Analysis, and Reporting Technology) is told to be a great test: The Smart-status is very very useful in determining the health of the storage drive,  furtermore it can especially be more useful for hard disks and backup drives because of a failure in those means imminent loss of data. well to sume it up: The SMART report consists of critical parameters that gives you a direct indication of the expected life left in the hard disk and so you can accordingly have the option to make or to take a decision to backup data and replace the hard disk. 


the hurry up and short tests: Checks the electrical and mechanical performance as well as the read performance of the disk. the tests might also include a test of buffer RAM, a read/write circuitry test, or a test of the read/write head elements. And not to forget the mechanical test is even better - it does include seeking and servo on data tracks. besides this the scans small parts of the drive's surface. Checks the list of pending sectors that may have read errors, and it usually takes under two minutes.

Long/extended: A longer and more thorough version of the short self-test, scanning the entire disk surface with no time limit. This test usually takes several hours, depending on the read/write speed of the drive and its size.
The most  intriguing and coolest thing is the Conveyance: a hurry up and very very quick test to identify damage incurred during transporting of the device from the drive manufacturer to the computer manufacturer. in earlier  times it only  was available on ATA drives, and it usually takes several minutes up to half an hour.

How to run the test 

on console or 
somehow else 

can apply it with 


sudo smartctl -a /dev/sda

---

### Post by jeremy31 on 2019-05-10
Find the Disks GUI program and do ctrl + s and that should bring up SMART

---

