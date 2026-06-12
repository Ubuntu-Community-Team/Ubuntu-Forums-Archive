---
title: "Syncing Nokia E61 mobile with kontact?"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by akvik on 2006-06-27
Hi,

Has anyone succeeded in syncing the Nokia E61 mobile with ubuntu? Any kind of information on this topic would be great. I have tried with multisynk but with no luck. I think the phone is not compliant with the Irmc standard.

Anyone?

:-)

Update:

I noticed that dmesg reported ttyACM0 as the device for my Nokia E61, and when I configured kmobiletools with /dev/ttyACM0 I got to send SMS through the phone! Awesome!

I use the cable to connect with the phone, using "PC Suite" as the connection type.

---

### Post by raydekok on 2006-08-05
ok that's working but i also want to sync but nothing will work. how can i sync my adresses???

---

### Post by akvik on 2006-08-07
I haven't made any additional efforts than the mail above, I simply changed back to Outlook again. To sync my calendar every day is a very important feature for me, and until that is possible to do with Kontact, I need to use another program, unfortunately.

:-)

---

### Post by piepre on 2006-09-05
Since yesterday I have also the Nokia E61. I'll try to sync with Kontact in the next days :)

---

### Post by akvik on 2006-09-19
Hi,

I have found a (reasonably) nice workaround that I am very happy with! Since the Nokia Smartphones for the moment only syncs with Outlook I think we have to live with that. 

But then there's RemoteCalendar. It's a plugin for outlook that imports a remote iCalendar (.ics) from a location on the net. It works with Google Calendar as well.

Here's how I use it with Thunderbird (through Lightning or Sunbird) on Linux:
Export the .ics file of your calendar (or publish it, if your server supports WebDAV).
Subscribe to the same calendar from RemoteCalendar in Outlook, and then sync the phone with Nokia PC suite.

It's a bit awkward, I know, but this makes me able to work with linux, and sync my phone on a PC I have at work. I think you can have several calendar into one as well.

:-)

Have an alternative  way of syncing your Nokia Smartphone with Linux calendars/addressbooks? Let us know!

---

### Post by darkghost on 2006-10-18
I also own a Nokia E61. BT file transfer works easy and well, no sync with kmobiletools at the moment.... any news ? Apparently no luck searching infos with google right now...

Andrew

---

### Post by akvik on 2006-10-18
Nope, I haven't seen anything concerning the syncing of e-series phones with a productivity suite for Linux.

I still use the workaround, since I also access a PC with outlook :-(

---

### Post by raydekok on 2006-10-22
[www.zyb.com](www.zyb.com) here you can sync your e61. the handy of is that it is onlien so you can check everything online. i hope there will be a sync way with googleagenda.

---

### Post by akvik on 2006-10-22
Zyb looks really nice! Good tip.

Worked like a charm. The only thing that i couldn't do was to import a .ics file into zyb, and then onwards to the phone. But that is only useful if you share calendars with others, and are continously updated.

---

### Post by mjfleck2000 on 2007-01-10
[QUOTE=akvik;1187823]Hi,

Has anyone succeeded in syncing the Nokia E61 mobile with ubuntu? Any kind of information on this topic would be great. 

I have the Nokia E62 which is suppose to be ALMOST the same thing but without the wifi capability.

Using bluetooth:
I have full syncing  between the E62 and Kontact for Calendar, Address Book and Todos.  I can use the file transfer program in KDE to send/receive files from/to my computer and the E62.

Using the usb cable I did transfer files E62<-->computer.  The sync config file had a bluetooth/usb option.  I wanted to use bluetooth so I didn't try the usb cable option.

For file transfer using bluetooth, I mainly used this thread:
[http://www.ubuntuforums.org/showthread.php?t=34740](http://www.ubuntuforums.org/showthread.php?t=34740)

For Sync I used this thread:
[http://ubuntuforums.org/showthread.php?t=260676](http://ubuntuforums.org/showthread.php?t=260676)

I changed evo2-sync to kdepim-sync and I used channel 14 for the Nokia.

It works very well.  

Mike

---

### Post by popophobia on 2007-11-12
Did anyone notice that multisync fail to sync the occurence of some events, especially if they have exceptions?

---

