---
title: "Deamon to send outside ip to FTP server (anti theft)"
date: 2008-10-30
forum: General Help
---

### Post by boterbram on 2008-10-30
Hi

Because I want to be able to track my laptop in case it gets stolen I would like to have a daemon running which sends especially my outside ip address to a ftp server or something like so I know which network it is using and I can therefore track it (it hasn't got any gps functions).

Any ideas?

gr Bram

PS. I figured it would be possible to write a really simple script to do this, but I just haven't done that before

---

### Post by ju2wheels on 2008-10-30
I dont think thats a safe way to go about that. If you setup an FTP then you will have to setup access priveleges for the laptop to access it meaning you would potentially be leaving your server open to attack if you the person that gets your laptop actually knows what they are doing.

I would recommend this alternative though...

Go to a free domain name site like no-ip.com and register for a free domain name. Then install their domain name ip updater (noip2 in the repository). This daemon will then update the ip of the domain to the ip of the machine and all youll have to do is run nslookup on the domain name to get the ip of your laptop.

The added benefit is that the daemon is always running if they arent logged into an account on the machine, and doesnt leave your ftp vulnerable.

You can configure noip2 to forward the LAN or WAN side IP as well. Although the WAN side IP makes more sense to use in your case.

---

### Post by Portmanteaufu on 2008-10-30
Another alternative would be to send an e-mail containing your external ip address to a webmail account each time you boot / login / whatever. Just make an account like [email]boterbram_ipaddr@gmail.com[/email] (or wherever) and set up the mailing script.

The details for doing this have all been spelled out in [this thread.]("http://ubuntuforums.org/showthread.php?t=961511&highlight=email+ip")

---

### Post by ju2wheels on 2008-10-30
> **Portmanteaufu said:**
> Another alternative would be to send an e-mail containing your external ip address to a webmail account each time you boot / login / whatever. Just make an account like [email]boterbram_ipaddr@gmail.com[/email] (or wherever) and set up the mailing script.

The details for doing this have all been spelled out in [this thread.]("http://ubuntuforums.org/showthread.php?t=961511&highlight=email+ip")

That solution still has the same problem as his initial one, being that it requires the password be put on the laptop. Both ftp and email require that the script/daemon have a user name and pass embedded which is not an ideal solution.

---

### Post by Portmanteaufu on 2008-10-30
> **ju2wheels said:**
> That solution still has the same problem as his initial one, being that it requires the password be put on the laptop. Both ftp and email require that the script/daemon have a user name and pass embedded which is not an ideal solution.

I've implemented this, and it didn't require me to save any passwords anywhere. I did, however, have an SMTP server available on my laptop that accepted incoming connections only from localhost.

---

### Post by boterbram on 2008-10-31
> **ju2wheels said:**
> I dont think thats a safe way to go about that. If you setup an FTP then you will have to setup access priveleges for the laptop to access it meaning you would potentially be leaving your server open to attack if you the person that gets your laptop actually knows what they are doing.

I would recommend this alternative though...

Go to a free domain name site like no-ip.com and register for a free domain name. Then install their domain name ip updater (noip2 in the repository). This daemon will then update the ip of the domain to the ip of the machine and all youll have to do is run nslookup on the domain name to get the ip of your laptop.

The added benefit is that the daemon is always running if they arent logged into an account on the machine, and doesnt leave your ftp vulnerable.

You can configure noip2 to forward the LAN or WAN side IP as well. Although the WAN side IP makes more sense to use in your case.

Thanks a lot! Great thinking, i will give it a try, and if it doesn't work i'll try the other method

Thanks again! Now let's just hope I never need it;)

I installed it now but I cant test if it works because there is no other network to test it with, but ill try when i'm at home

---

