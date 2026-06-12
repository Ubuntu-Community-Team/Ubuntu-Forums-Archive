---
title: "Canon Powershot SD400"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by lewindha on 2005-06-29
Hello All

I have recently downloaded Ubuntu and I think it's great.  I've already gotten it working with my iPod.  Open Office is great.  There are a couple of things keeping me from trashing Windows XP.

1.  I recently purchased a Canon Powershot SD400 digital Elph camera.  When I plug it in, Ubuntu doesn't recognize it.  Has anyone had any success with this particular camera?  I have gthumb installed and tried using gphoto2 also.  Nothing works so far.  Can anyone help me here, please?

2.  This is probably not the forum for this question, but I buy a good bit of music from the iTunes music store.  Is there any way to access this store from Linux?

Thanks
I really appreciate the work on Ubuntu and the community is unbelievable, so keep up the good work.  I hope to contribute once I get a handle on everything.

---

### Post by crispingatiesa on 2005-06-29
does the camera connect trough USB? If yes, check /media/USB (or similar) 

If  still doesn't show do:

tail -f /var/log/messages

after connecting the camera and post the results

---

### Post by lewindha on 2005-06-29
Here is the result of the tail command:

```

:/$ tail -f /var/log/messages
Jun 29 18:51:09 localhost -- MARK --
Jun 29 19:11:09 localhost -- MARK --
Jun 29 19:31:09 localhost -- MARK --
Jun 29 19:51:09 localhost -- MARK --
Jun 29 20:11:09 localhost -- MARK --
Jun 29 20:31:10 localhost -- MARK --
Jun 29 20:51:10 localhost -- MARK --
Jun 29 21:11:10 localhost -- MARK --
Jun 29 21:25:10 localhost kernel: usb 4-6: new high speed USB device using ehci_ hcd and address 4
Jun 29 21:25:11 localhost usb.agent[24764]:      libgphoto2: loaded successfully

```

---

### Post by lewindha on 2005-06-29
Thanks for the help!!!

I figured it out.

Just ran:

ghoto2 --auto-detect

Found the right port and imported from there.

---

### Post by Jimmy Joe on 2007-07-08
I have been having difficulties getting my Canon PowerShot sd400 to connect to my Linux. :confused:  I am using edubuntu feisty fawn 7.04.  I have only used linux for a couple of days, so I am still facing a bit of a learning curve.  I ran the tail command in my terminal window per crispingatiesa's suggestion to the previous post.  This is what I got:

:~$ tail -f /var/log/messages
Jul  8 18:59:12 Edubuntu -- MARK --
Jul  8 19:19:12 Edubuntu -- MARK --
Jul  8 19:39:12 Edubuntu -- MARK --
Jul  8 19:59:12 Edubuntu -- MARK --
Jul  8 20:19:13 Edubuntu -- MARK --
Jul  8 20:28:43 Edubuntu kernel: [190157.419389] usb 4-1: new high speed USB device using ehci_hcd and address 13
Jul  8 20:28:55 Edubuntu kernel: [190169.254687] usb 4-1: new high speed USB device using ehci_hcd and address 15
Jul  8 20:29:07 Edubuntu kernel: [190181.090013] usb 4-1: new high speed USB device using ehci_hcd and address 17
Jul  8 20:29:19 Edubuntu kernel: [190193.181102] usb 4-1: new high speed USB device using ehci_hcd and address 19
Jul  8 20:29:31 Edubuntu kernel: [190205.016401] usb 4-1: new high speed USB device using ehci_hcd and address 21
Jul  8 20:29:43 Edubuntu kernel: [190216.851706] usb 4-1: new high speed USB device using ehci_hcd and address 23
Jul  8 20:29:54 Edubuntu kernel: [190228.686997] usb 4-1: new high speed USB device using ehci_hcd and address 25
Jul  8 20:30:06 Edubuntu kernel: [190240.522299] usb 4-1: new high speed USB device using ehci_hcd and address 27
Jul  8 20:30:18 Edubuntu kernel: [190252.357600] usb 4-1: new high speed USB device using ehci_hcd and address 29
Jul  8 20:30:30 Edubuntu kernel: [190264.200890] usb 4-1: new high speed USB device using ehci_hcd and address 31
Jul  8 20:30:42 Edubuntu kernel: [190276.036187] usb 4-1: new high speed USB device using ehci_hcd and address 33
Jul  8 20:30:54 Edubuntu kernel: [190287.871490] usb 4-1: new high speed USB device using ehci_hcd and address 35
Jul  8 20:31:06 Edubuntu kernel: [190299.706788] usb 4-1: new high speed USB device using ehci_hcd and address 37
Jul  8 20:31:17 Edubuntu kernel: [190311.542087] usb 4-1: new high speed USB device using ehci_hcd and address 39
Jul  8 20:31:29 Edubuntu kernel: [190323.377387] usb 4-1: new high speed USB device using ehci_hcd and address 41
Jul  8 20:31:41 Edubuntu kernel: [190335.468508] usb 4-1: new high speed USB device using ehci_hcd and address 43
Jul  8 20:31:53 Edubuntu kernel: [190347.303799] usb 4-1: new high speed USB device using ehci_hcd and address 45
Jul  8 20:32:05 Edubuntu kernel: [190359.139098] usb 4-1: new high speed USB device using ehci_hcd and address 47
Jul  8 20:32:17 Edubuntu kernel: [190370.974408] usb 4-1: new high speed USB device using ehci_hcd and address 49
Jul  8 20:32:29 Edubuntu kernel: [190382.809700] usb 4-1: new high speed USB device using ehci_hcd and address 51
Jul  8 20:32:41 Edubuntu kernel: [190394.644998] usb 4-1: new high speed USB device using ehci_hcd and address 53
Jul  8 20:32:53 Edubuntu kernel: [190406.736109] usb 4-1: new high speed USB device using ehci_hcd and address 55
Jul  8 20:33:04 Edubuntu kernel: [190418.571411] usb 4-1: new high speed USB device using ehci_hcd and address 57


It kept going like this for some time, so I stopped the process.  It seems the address number kept going up by 2's.  I'm hoping someone can help me.  Also, I don't know how to tell which port my camera is connected to, or how to change it like lewindha did.  Any help would be appreciated.

---

### Post by Kymac on 2008-07-01
I'm sorry, but I have a similiar problem.  I also have a Canon Powershot SD400, and am using Xubuntu.  I would like to know if someone could please help me with this.  

I used the gphoto2 --auto-detect, and got this (how do I import?)

```
kymac@family-desktop:~$ gphoto2 --auto-detect
Model                          Port                                            
----------------------------------------------------------
Canon Digital IXUS 50 (PTP mode) usb:   
```

I ran the tail thing, and it came up with a message like this.


```
kymac@family-desktop:~$ tail -f /var/log/messages
Jul  1 11:35:43 family-desktop kernel: [352428.179693] usb 5-8: new high speed USB device using ehci_hcd and address 8
Jul  1 11:35:43 family-desktop kernel: [352428.329857] usb 5-8: configuration #1 chosen from 1 choice
Jul  1 11:37:09 family-desktop gnome-power-manager: (ron) Power Manager is already running in this session.
Jul  1 11:38:39 family-desktop kernel: [352604.311485] usb 5-8: USB disconnect, address 8
Jul  1 11:47:52 family-desktop kernel: [353156.198101] usb 5-8: new high speed USB device using ehci_hcd and address 9
Jul  1 11:47:52 family-desktop kernel: [353156.348212] usb 5-8: configuration #1 chosen from 1 choice
Jul  1 11:52:52 family-desktop kernel: [353455.314516] usb 5-8: USB disconnect, address 9
Jul  1 11:53:27 family-desktop gnome-power-manager: (kymac) Power Manager is already running in this session.
Jul  1 12:01:32 family-desktop kernel: [353974.726173] usb 5-8: new high speed USB device using ehci_hcd and address 10
Jul  1 12:01:32 family-desktop kernel: [353974.876265] usb 5-8: configuration #1 chosen from 1 choice

```

---

