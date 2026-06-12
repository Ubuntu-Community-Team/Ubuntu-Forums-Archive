---
title: "Modem Reset"
date: 2011-02-22
forum: Hardware
---

### Post by dac_bs on 2011-02-22
Dear all,
I'm really new in Ubuntu, I just made the change. But I have a problem with my internet connection. The problem is that after a while using the internet, and downloading some stuff, my modem just disconnect from the router, and its impossible to connect again, even if I see the connection, unless I restart my laptop. 

I have a Dell inspiron 6400, with 4GB RAM, but my house-mate has the same problem, and he is using and HP with different characteristics. The only similarity is that both of us are using Ubuntu. Another thing is that this never happen at the same time, it happen at different time intervals, and some random downloading.

He also had tried with windows  in the same computer and there is no problem(hard to believe that windows works fine for once :P), no disconnection and the modem just works fine. He could disconnect or connect without restarting the computer

Trying to solve it, I have disconnect and connect the router, but it hardly ever works, maybe once in a hundred, so impossible to say it is the router, and if the laptop is restarted then it works always.

I have tried the simple methods to restart my modem 
   ifdown -a
   ifup -a
or 
   ifdown eth0
   ifup eth0
or
   dhclient -r
   dhclient

And some others like turning on and off with the f-Key the modem, and still nothing. Only a complete system restart does the trick.

I don't know if its a saturation of the modem memory or if its that for a moment it got disconnected and cannot restart connection with same key or anything, just please help because this is way too annoying 

Thanks for your help, Cheers
D.

---

