---
title: "Few questions from newbie"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by young on 2005-04-24
Hello there,


       I am just getting started with Ubuntu Linux.  I am trying to set up my wireless network, so what I did was to read the guideline on installing DHCP server for automatic IP address configuration.  Here's what I typed in:

   sudo apt-get install dhcp3-server

   and the message ' cannot find dhcp3-server' shows up.  Is there something that I am missing? 

     Another thing that I am wondering is for some reason, I don't seem to be able to save the file 'sources.list' located in etc/apt/ file, after modification.  What could cause this? 

    Your reply would be more than appreciated.  Thank you in advance

                                                                                                   Cheers,

                                                                                                           Young

---

### Post by telmo on 2005-04-24
> 
I am trying to set up my wireless network, so what I did was to read the guideline on installing DHCP server for automatic IP address configuration.

I think the only thing you need to do is to configure the Network settings in System/Administration/Networking.
And select DHCP.

> Another thing that I am wondering is for some reason, I don't seem to be able to save the file 'sources.list' located in etc/apt/ file, after modification. What could cause this?

Have you tried doing it with root previleges?

```
sudo gedit /etc/apt/sources.list
```

---

### Post by young on 2005-04-24
Hello there,

       Thank you very much for your reply.   I actually went to 'networking' section to do some configuation, and made sure that the system would use DHCP for the automatic IP configuration.  When I type in iwconfig on the terminal however, I get the following results:


     lo       no wireless extensions
 
     eth0  no wireless extensions

     eth1    unassociated    ESSID:"young"
                Mode: Managed    Channel=0     Access Point: 00:00:00:00:00:00
                Bit Rate = 0kb/s     Tx-Power = 20 dBm
                RTS thr: off      Fragment thr: off
                Encryption key: off
                Power Management: off

    sit       no wireless extensions


   Am I missing something here?  I even tried to install DHCP server using the command,  sudo apt-get install dhcp3-server  (i even tried aptitude instead of apt-get).  I get a message that 'dhcp3-server cannot be found' or something very similar to that.  Any ideas on this situation?  Thank you again.

 
                                                                                              Sincerely,

                                                                                                           Young

  *P.S.  I also have another problem installing update softwares.  What I mean is, after modifying the file, 'sources.list'   from etc/apt folder, I typed in sudo apt-get (or aptitude) update, and I get this whole bunch of error messages

---

