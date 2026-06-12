---
title: "Toshiba Satellite A35 Winmodem now Working!!!!"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by HairyDave on 2006-04-06
:D 

Finally, after a month of ](*,) , I have got the blasted winmodem working.

So happy, and greatly relieved!!

I was just about to give up with Ubuntu .... glad I persisted as I think it's one of the best distros i've come across!

:D

---

### Post by aderio on 2006-04-07
Congratulations!  How about sharing your experiences.:KS

---

### Post by aderio on 2006-04-07
Congratulations!  How about sharing your experiences.:KS

---

### Post by HairyDave on 2006-04-08
OK,

Well I first installed the 'make' function through Synaptic Package Manager.
Then I D/L scanModem and ran scanModem, it advised on D/L 'SLMODEMD.gcc3'

I D/L and installed 'BreezyGCC_3.4_i386.tar.gz' and 'SLMODEMD.gcc3' from: [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

next I used:  
$ sudo modprobe snd_intel8x0m
$ sudo slmodemd --alsa -c UK modem:1
Password:
SmartLink Soft Modem: version 2.9.11 Jan 19 2006 21:19:22
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `modem:1' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

Next go to ->System ->Administration ->Networking and setup the modem connection to reflect the modem device output from above: i.e I used '/dev/ttySL0'.

Open another terminal window and run wvdial: $ sudo wvdial
(make sure you alter the config file from the default before running the command!) 

then change the network connection in the top right of the desktop to ppp0.

This worked for me, if anyone knows a simpler way then please let me know.

Dave

---

