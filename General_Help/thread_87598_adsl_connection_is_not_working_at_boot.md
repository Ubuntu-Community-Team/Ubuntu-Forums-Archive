---
title: "adsl connection is not working at boot"
date: 2005-11-08
forum: General Help
---

### Post by slate on 2005-11-08
Hello!

I use linux since redhat 5. 
I have installed ubuntu 2 days ago.
I configured the adsl connection with pppoeconf. Everything worked fine. 

When I boot up,  the internet connection is not working. Ubuntu time synch doesnt work either.
If I restart networking /etc/init.d/networking restart, then the connection is working ok. But plog doesnt show anything.
I use squid, so I have to restart it, I dont know why, in order to make it work.
I placed squid to /etc/rc2.d/S35squid.


Can anybody tell me, how to solve it?
I tried to place ppp into rc2 but does not help.

Thanks in advance
slate

---

### Post by Confused Fishcake on 2005-11-08
I don't know what to do in your case, but this is what I did. I  had to type "pon ADSL" into terminal to get connected. I wrote "pon ADSL" in a text editor and saved it. I made it excecutable (chmod a+x) then put in in the bootup directory. Hope this helps.

---

### Post by slate on 2005-11-08
Where is the bootup directory?

---

### Post by slate on 2005-11-16
I could not solve this.
If there is some information I shoul provide to get help, please inform me.

---

### Post by argux on 2005-11-17
I Have this problem too. When I first installed Ubuntu and configured the adsl connection, it asked me if I wanted to start the connection at boot time, I said yes and it worked.

Then, my crappy provider went out for a few days and I rerun the configurator to tell it not to start the connection at boot time.

When my crappy line worked again, I rerun the configurator to make it start the connection again, but it didn't work. I've tried many times, but it still doesn't work.

What I do is 'pon dsl-provider' on the console and I get connected, but this is not good enough. What if somebody else turns the computer on and has no access to sudo?

---

