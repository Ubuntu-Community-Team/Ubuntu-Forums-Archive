---
title: "Epson TM T88IV receipt printer very slow"
date: 2014-04-17
forum: Hardware
---

### Post by ck234 on 2014-04-17
Hello,
   I am trying to install the Epson TM T88IV receipt printer on an Ubuntu Server.  I have managed to install it via cups, but it is printing very slowly.  This printer will print receipts in under 1 sec on windows machines.  Steps so far:

1. Plugged printer into serial port on back of server.
2. Verified port by running "dmseg | grep tty".  In my case the printer was at "/dev/ttyS0".
3. Made this port writable "chmod 0777 /dev/ttyS0".
4. Checked the baud rate of the port "stty < /dev/ttyS0".  In my case 9600.  However, should you need to change run: "sudo stty -f /dev/ttyS0 9600".
5. Checked the Epson printer baud by holding down "feed" button when turning on.  The printer operates at 9600.
6. Checked the printer could work from CLI = "sudo echo "Hello World" >> /dev/ttyS0".  It printed a single line at good speed.
7. Fired up cups (localhost:631)
8. Added the printer via the cups web interface.  When prompted for the ppd, I used the thermal rastermount ppd downloaded from the Epson website.
9. Entered maintenance section of the cups website and asked the printer to print a test page, which it did, but it took 60 seconds.

So, the speed is far too slow for a work environment.  I have messed around with the "printer default settings" in cups, but to no avail.  I think I am missing something in the cups config.  With some searches, I think it may have something to do with spooling, but I am not sure how to change this.  Any help appreciated.

Thank you.

---

### Post by coldraven on 2014-04-17
Sorry but it has been many years since I used to hook up printers to Unix machines.
It might be worth checking if the Epson is using hardware or software flow control.
For hardware you need to use the CTS and RTS pins of the serial port. 
For hardware flow control you need more than just three wires connected.
Buy a tester and check the LEDs and the wiring of the serial cable.
You can buy one on various sites, they look like this: [http://www.ecrater.co.uk/p/14937945/rs232-rs-232-serial-db9-interface?gps=1](http://www.ecrater.co.uk/p/14937945/rs232-rs-232-serial-db9-interface?gps=1)

---

