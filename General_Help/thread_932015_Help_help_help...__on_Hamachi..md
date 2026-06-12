---
title: "Help help help...  on Hamachi."
date: 2008-09-27
forum: General Help
---

### Post by jkc2103 on 2008-09-27
PLEASE help me on this... hear me out..
I have installed hamachi and I have gone up in the readme till 
here.

Run 'hamachi join <network>' to join the network

Im quite confused on that part and down.. here is the rest. 

Run 'hamachi login' to put the daemon online and to create an account.

	Run 'hamachi join <network>' to join the network.

	Run 'hamachi go-online <network>' to go online in the network.

	Run 'hamachi list' to list network members and their status.


BUT when i run into trying to do Hamachi start. It says its locked .. this is what it says.

Cannot access lock file /home/jo/.hamachi//.lock

AND. the folders arent locked?

can anybody please help me??? im lost.

---

### Post by jkc2103 on 2008-09-27
please anybody?

---

### Post by cyb3rkn19ht on 2010-01-14
See if hamachi is running, if it is stop it. That should remove the lock file. Otherwise go to  /home/jo/.hamachi/ and delete the lock file.
I had this same error when I started hamachi as root and then tried to start it again as a user.

---

