---
title: "Configuration Advice Wanted"
date: 2006-01-08
forum: Installation &amp; Upgrades
---

### Post by UphillSkier on 2006-01-08
I would like some advice on configuring a very small home network using Ubuntu. Please excuse and redirect me if this is the wrong forum.

Currently I am running breezy on a 192 MB Pentium II with dual boot to windows 
I need windows for one or two legacy programs (especially Quicken). I want to buy a new computer, and use it as a desktop linux system while retaining the old windows machine.  I want the windows files accessible from both computers. I also need to support a wireless access point in case someone is trying to use a laptop elsewhere in the house and I would like to be able to add a wired connection to my son's computer running windows XP when he is at home.  (my son is much less of a geek than I am :).  I communicate to the outside via a cable modem.

Anyway, I am looking for advice on how to configure and install this system.  At the moment I think I need the following

cable modem ( have it!)
       | 
externally connected ethernet card on new linux box
       |
some kind of firewall/routing software
        |
internally connected ethernet card on new linux box acting both as desktop 
and samba server
         |
some kind of switch
    |
    |--------  wireless access point
    |     
    | ---------windows 98 machine
    | 
    |-------------port(s) for other machines
   
  
 What I need is the following
1.  advice on configuration - have I got the right idea or is there a better way
to do what I want to do?  Can you help with the details?

2.  pointers to faqs/guides that will help me set this thing up.

Can anyone help?

Thanks 
Andy

---

### Post by Sef on 2006-01-09
1) Can't help you.

2) Section on networking:  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing")  or this:  [http://easylinux.info/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections]("http://easylinux.info/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections")

---

### Post by UphillSkier on 2006-01-09
[QUOTE=Sef]1) Can't help you.

2) Section on networking:  [http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-ing")  or this:  [http://easylinux.info/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections]("http://easylinux.info/wiki/Ubuntu#How_to_activate.2Fdeactivate_network_connections")[/QUOTE]

Thanks.  I had found the starter guide reference but not the easylinux one.  I have also found the index of Network Howtos at 

[http://www.tldp.org/HOWTO/HOWTO-INDEX/networking.html#NETGENERAL]("www.tldp.org/HOWTO/HOWTO-INDEX/networking.html#NETGENERAL")

and the overview howto at [http://www.tldp.org/HOWTO/Networking-Overview-HOWTO.html]("http://www.tldp.org/HOWTO/Networking-Overview-HOWTO.html")


I will work through these but it will take some time :( .  If anyone has shortcut advice on the configuration I sketched I would still appreciate it.

Thanks

---

### Post by Kipper on 2006-01-09
Andy, 

I would say in general terms you have got things right. But I would ask who/why do you need to maintain your exisiting Win98 machine as it is.

It is possible that the win98 machine has enough juice to be converted to your Linux home server and act as your firewall/router/file and print server, assuming it has a m/board you can put at least two and possilbly three NICs in, and a reasonable hard drive size. The one thing Linux is truley excellent for is to get decent performance out of older hardware. You can run this Linux box headless (no monitor) and administer it from your other Linux machine logging via "ssh" and using "vnc" if necessary. You can run Samba on this machine and load the data on it that you wish to share across your LAN. Whether you decide to have these files on FAT32 partition, or not is, up to you. 

Hanging everything off you new machine on which you intend to run Linux does have the minor disadvantage of making your home network susceptible to down-time if you get into tinkering around with the software on it.

I would be tempted to make the new machine dual boot using two hard drives one for windows + backups + data and the other drive for Linux. You might want to mess around with various flavours of linux and keep them all on one disc. You can, of course, do this with only one hard drive. One small gotcha if you take the two hard drive route is that the newer SATA drives are treated like SCSI drives and so have a limit of 16 partitions. Ok, that's plenty for most folk, but you can run out with multiple Linux installs. So perhaps stick to a PATA drive for your Linux only drive.

You can get anyway without the switch/hub if you used a WAP that has a built in swith. In fact a product like the Linksys WRT54G can be used in WAP mode only and has an additional 4 LAN ports.

A possible configuration might be:

Cable Modem
|
|
|
Linux Machine  ---------------------------------- Linux/Windows Box
(combined firewall/router/
samba & print server)
|
|
|
|
|
WAP ------- 4 other LAN ports

In this case the Linux Machine acting as your firewall/router/server has 3 NIC.  One for external connection to the cable modem, one for internal connection to your new Linux/Windows dual boot, and one for connection to your combined wireless AP/switch. 

This will mean your new machine is on a different subnet to the anything connected via the WAP/switch, which you can either view as a security advantage or disadvantage as far as sharing data between the two subnets is concerned. 

This set-up allows for growth and the Linux server can be administered headless from the second Linux box once it is set up. It does offer some security advantages with the wireless subnet separate from the wired part.

Another way to go is to plug your cable modem straight into something like the WRT54G and let this router do your firewalling and provide Internet acccess to all parts of your LAN wired and wireless. This way all your machines will be on the same internal LAN and your new machine can act as a file/printer server for everyone else if you wish.

The second approach is more straightforward to setup, no firewall software to set-up and configure, which can be tricky. Has cheaper running costs, as the cable modem + router will consume far less power than a PC used as dedicated Linux server. But take care the WiFi security, make sure you're using WPA at least. 

One thing has just struck me. Which way round to you want to share your Windows Files?  Old Machine to New, or New Machine to Old? Do you expect to share files when you are logged into Windows on any LAN Machine and/or when logged into Linux/Windows on your new machine only? Do you want the files to appear on a "network drive" or would it be sufficient just to be able to transfer files between machines if and when you need them?

Answers to these question will have some bearing on if you need to run samba at all. For example, if one machine is running Linux and ssh server software, you can log into it and transfer files back and forth securely across your LAN either from another Linux machine with something like gFtp, or from another machine running Windows with something like WinSSH. 

Obviously there is no one way to setup a small home LAN. You'll find lots of ideas floating around the Internet. Growth, security, flexiblity, simplicity, and cost are all factors to throw into the melting pot together with a well worked out set of requirements.

---

### Post by UphillSkier on 2006-01-09
Kipper

Thank you very much for your detailed reply.  I will need time toconsider it carefully.

best wishes
Andy

---

