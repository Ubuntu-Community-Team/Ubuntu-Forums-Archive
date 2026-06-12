---
title: "HP Laserjet 1000 does not respond"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by atoll on 2006-02-04
I have installed  ubuntu on a Compaq Evo N400c with a HP Laserjet 1000. If the printer is plugged in via USB when I start the computer, it is recognized as a local printer when I set up a new printer. When I try to print the test page, nothing happens. Am I doing something wrong?

---

### Post by paulmilliken on 2006-06-20
See [http://www.ubuntuforums.org/showthread.php?t=200179&highlight=laserjet+1000]("http://www.ubuntuforums.org/showthread.php?t=200179&highlight=laserjet+1000") for instructions.

Paul

---

### Post by ernetas on 2006-06-21
[QUOTE=paulmilliken]See [http://www.ubuntuforums.org/showthread.php?t=200179&highlight=laserjet+1000]("http://www.ubuntuforums.org/showthread.php?t=200179&highlight=laserjet+1000") for instructions.

Paul[/QUOTE]
I have got the same problem, but it doesn't helps.

I have tried to install the printer on webmin + LPRng, but I get this:> 
Printing test page with command lpr -Psleep \/tmp\/\.webmin\/881216_1_test_print\.cgi ..

Status Information, attempt 1 of 3:
sending job 'root@localhost+854' to sleep@localhost
 connecting to 'localhost', attempt 1
 connected to 'localhost'
 requesting printer sleep@localhost
 sending control file 'cfA854localhost.localdomain' to sleep@localhost
 job 'root@localhost+854' transfer to sleep@localhost failed
  error 'ERROR TRANSFERRING DATA'
  sending str '^B218 cfA854localhost.localdomain' to sleep@localhost
Waiting 10 seconds before retry
Status Information, attempt 2 of 3:
sending job 'root@localhost+854' to sleep@localhost
 connecting to 'localhost', attempt 1
 connected to 'localhost'
 requesting printer sleep@localhost
 sending control file 'cfA854localhost.localdomain' to sleep@localhost
 job 'root@localhost+854' transfer to sleep@localhost failed
  error 'ERROR TRANSFERRING DATA'
  sending str '^B218 cfA854localhost.localdomain' to sleep@localhost
Waiting 10 seconds before retry
sending job 'root@localhost+854' to sleep@localhost
 connecting to 'localhost', attempt 1
 connected to 'localhost'
 requesting printer sleep@localhost
 sending control file 'cfA854localhost.localdomain' to sleep@localhost
 job 'root@localhost+854' transfer to sleep@localhost failed
  error 'ERROR TRANSFERRING DATA'
  sending str '^B218 cfA854localhost.localdomain' to sleep@localhost

.. command failed!

---

### Post by paulmilliken on 2006-06-21
Ernetas,
I see from your avatar that you are using Ubuntu 5.10.  In this case, can you do the following:
1.  Turn your printer off and then back on.
2.  Locate your file called sihp1000.img that you should have downloaded from [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/").
3.  cd to the directory where sihp1000.img is stored.
4.  Type > sudo cat sihp1000.img > /dev/usb/lp0

Does your printer make whirring noises after doing these steps?  If so, the you should be ready to print on Hoary or Breezy.  (It's a little different for Dapper).

Paul

---

### Post by ernetas on 2006-06-22
[QUOTE=paulmilliken]Ernetas,
I see from your avatar that you are using Ubuntu 5.10.  In this case, can you do the following:
1.  Turn your printer off and then back on.
2.  Locate your file called sihp1000.img that you should have downloaded from [http://foo2zjs.rkkda.com/]("http://foo2zjs.rkkda.com/").
3.  cd to the directory where sihp1000.img is stored.
4.  Type 

Does your printer make whirring noises after doing these steps?  If so, the you should be ready to print on Hoary or Breezy.  (It's a little different for Dapper).

Paul[/QUOTE]
Does then I'll can to print over Windows 2000?

---

