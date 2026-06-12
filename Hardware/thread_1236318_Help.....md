---
title: "Help...."
date: 2009-08-10
forum: Hardware
---

### Post by AmerNewbieInDE on 2009-08-10
Hello, i gotta a little problem with my network and seems no one in the networking section can or will help.

The support i got there got my card to work, but for every reboot, i must reenter the code to get my card to connect to the network.

i have the intel 5100AGN, connecting to a wpa/psk2 network. i downloaded the firmware file, put it into the /lib/firmware/ folder.

then everytime i reboot, i must enter 

sudo modprobe -r iwlagn

sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

My question, how do i get this to work automatically when i restart the notebook.

---

### Post by overdrank on 2009-08-10
It appeared to me that Codename was helping you with your issue. Please do not create multiple threads on the same issue. Duplicate [here]("http://ubuntuforums.org/showthread.php?t=1235023&page=2"). Thread closed

---

