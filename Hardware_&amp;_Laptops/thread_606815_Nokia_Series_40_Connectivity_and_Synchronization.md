---
title: "Nokia Series 40 Connectivity and Synchronization"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by obiwankamote on 2007-11-08
Has anyone tried connecting to a series 40 phone? I have a Nokia 6151 and have been playing around with different stuff but still couldn't get to synchronize the phone. If someone has ideas about this that would be great. Thanks!

---

### Post by Spoker on 2007-12-01
Have you had any luck synchronizing?

---

### Post by obiwankamote on 2007-12-01
sorry no luck so far :( the best I could do was with xgnokii. But the only thing it's capable of with my phone is viewing the address book, and sending messages. It hangs when I try to view the messages.

---

### Post by Spoker on 2007-12-03
Have you tried wammu? I still need to check it out further, but I managed to read my contacts. Maybe you'll have more luck with this program

---

### Post by obiwankamote on 2007-12-03
yup i tried wammu. i did get the contacts to work but i wanted to get the messages and other info as well.

---

### Post by jackcy on 2007-12-14
Wammu is correctly detecting the phone (had to install python-bluez) but todo and calendar can not be synchronized.

---

### Post by Spoker on 2008-04-23
I hope, when Hardy is here (only 20 more minutes to go in my time-zone :-) the included opensync packages will allow me to synchronize my phone.

Keep your fingers crossed. (I have a 5300 nokia)

---

### Post by jens.bergqvist on 2008-04-29
Spoker, have you had any luck with opensync on hardy, yet? 

I've got my Nokia 6500s (Series 40) to partially sync with kdepim using opensync-0.22 with the syncml-obex-client plugin.

My syncml-obex-client.conf file:
[ATTACH]67927[/ATTACH]

Calendar works flawlessly in both directions but Contacts only works in direction from computer to phone. If I edit a contact on the phone and perform a sync the vcard is corrupted on the computer. The corruption is then propagated back to the phone on next sync. **Danger, Will Robinson! Danger!**

Misc:
* I needed to activate authorization in my phone settings and add username/password to syncml-obex-client.conf.
* For some reason I had to sync the phone once using Nokia's official software (in Windows) or the phone would not allow connections.
* Unless I add "--filter-objtype note --filter-objtype todo" to the msynctool command the sync fails.

---

### Post by Spoker on 2008-05-01
Hi, I have upgrade my ubuntu installation, but haven't got to it right now. However, I will report back here with my results when I've gotten the chance to try it out. Thanks for your information. I just want to sync the calendar :-)

One of the problems I encountered, was I didn't know how on what channel to connect to on the phone. I opened another thread on this forum on this here:
[http://ubuntuforums.org/showthread.php?t=771388](http://ubuntuforums.org/showthread.php?t=771388)

I see you connect on channel 11. Is this channel also called: 'syncML client' on your phone? I experienced some problems. I'll look at it again.

---

