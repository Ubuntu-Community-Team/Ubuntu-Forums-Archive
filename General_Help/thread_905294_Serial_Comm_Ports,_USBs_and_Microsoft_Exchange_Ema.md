---
title: "Serial Comm Ports, USBs and Microsoft Exchange Email"
date: 2008-08-30
forum: General Help
---

### Post by HyperUniverse on 2008-08-30
Hi,
I am new to Linux, and I just installed Ubuntu on my pc at work.
I have no ideea how to connect my devices to the comm port, or USB.
"DEVICES"  I mean lots of different electronics that I need to interact with at my work place. (I am an electronic engineer)
I know how to do that in WinXP, and they work OK.
Since I have installed Ubuntu, I can not find any control/configuration for serial comm ports.
The problem is that long ago, when I tested a faulty unit connected to my comm1, it blew up the comm1. So then I went in Windows and reassigned another comm port as comm1.
There is no option in my devices to change the comm port, they are using comm1.
So, where do I go in Ubuntu to reassign another comm as comm1?
Also I have an USB to SerialComm adapter. I have installed the windows driver using Wine, but where do I go to see how many comm port do I have in my machine, so I can reasign it to what I need?
Is there something similar to "DEVICE MANAGER" from windows in Ubuntu?
Another problem I have is access to my email account that is on an Exchange Server 2003.
I have read a lot about how to access it using Evolution, but I am still not able to do it. It always tells me the URL is wrong.
Is there a way to find out the OWA URL of my server? (I am not the administrator of our work network, and I can not ask him). Or it may be possible that our server does not use an OWA URL?
Is there any other email client program out there I can use it with our exchange server? Or is it possible to setup my email account in windows to redirect all my emails automatically to another email address (hotmai...), and if I send emails from (hotmail...) can the recipient see there are comming from my old email address from our exchange server?

I am sorry to say that if I can not solve these 2 problems (comm port and email) then I am back to winxp, which I started hateing it.

Thanks,

---

### Post by jacktar on 2008-09-05
I would also like to use a USB to Serial adapter but apart from Windows it only has Red Hat drivers. Can Red Hat drivers be converted for Ubuntu ?

---

### Post by timcredible on 2008-09-05
to access a serial port, use kermit (ckermit or gkermit in synaptic) and connect to /dev/ttyS0 for COM1, /dev/ttyS1 for COM2, etc.  since they're all just mount points, yes, you can re-assign the mount points.

evolution works with exchange, and you can find out your owa from your windows outlook client, look at the info on your account.  although, check to see if your exchange admin has setup the web access to exchange, then you can just use your browser to access your email.

---

