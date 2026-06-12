---
title: "Can't access USB modem..."
date: 2021-09-14
forum: Hardware
---

### Post by timothybarry on 2021-09-14
I'm unable to connect efax-gtk to a new USRobotics modem using U14.04. When typing *lsusb* in terminal, I get the following line:
[LIST]
[*]Bus 001 Device 003: ID 0baf:0303 U.S. Robotics USR5637 56K Faxmodem
[/LIST]
I have tried a variety of Serial Device options (ttyACM0, ttyUSB0, ttyS0, ttyS1, etc.) in the settings tab of efax-gtk, but I can't seem to connect to that modem.

Any suggestions?

---

### Post by Autodave on 2021-09-14
Am I correct in reading your post that you are running 14.04??  That release is way beyond its end of life (EOL).  No one here is going to be able to help with an old release like that.  Is there a reason why you have not installed 20.04 (long term release (LTR))?  You really need a newer release and at this point, I would suggest a clean install after you back up anything that you need to keep.

---

### Post by timothybarry on 2021-09-15
OK. I will see if that old Dell D620 can handle it and then try again. Thanks for your reply.

---

### Post by Autodave on 2021-09-16
You didn't post any specs, but perhaps you need a lighter distro than Ubuntu: like Xubuntu or Lubuntu.

---

