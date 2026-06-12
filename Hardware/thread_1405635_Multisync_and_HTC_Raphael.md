---
title: "Multisync and HTC Raphael"
date: 2010-02-12
forum: Hardware
---

### Post by naiku on 2010-02-12
I am trying to use Multisync to synchronise mail, contacts etc between Evolution and my HTC Raphael smart phone. I followed a guide, and when I click the "Search for Units" button it finds my phone. But, when I click on the "Test Connection" button it says "Connection failed"

If I start a sync manually, it just sits saying "Searching for client"

What am I doing wrong? I managed to pair the laptop and phone together via Bluetooth. 

Is it also possible to use a USB cable instead of Bluetooth? 

Thanks.

---

### Post by naiku on 2010-02-13
Anyone? I have spent hours searching reading about Synce, Multisync, etc and getting nowhere. I now have Synce recognising the phone when I plug it in, but now any time I try to open multisync it closes right away.

---

### Post by naiku on 2010-02-13
Ok, so now I am getting the following when I try to open Multisync:

user@my-laptop:~$ multisync
plugin_API_version
short_name
long_name
plugin_init
Segmentation fault

Which I can not find any solutions for, this is enough to make me consider switching back to Windows XP. Something that is very important to me is being able to sync calendar with my laptop.

---

### Post by zjaak on 2010-05-05
Hey this is a really simple one.

Goto ~/.multisync and remove or backup all files within this folder. When the folder is empty start multisync. It should start now.

Sorry for the late reaction BTW, becuase my father was having this problem just now, and i also couldn't find a solution on Internet. So I found this solution.

I think it's one of the Plugins that make the app crash, because it crashes after plugin_init. 

This could also work, edit ~/.multisync/syncpair and change:

remoteclient = plugin
localclient = plugin

to 

remoteclient = 
localclient = 

could make the app start also, but I haven't tested it.

---

