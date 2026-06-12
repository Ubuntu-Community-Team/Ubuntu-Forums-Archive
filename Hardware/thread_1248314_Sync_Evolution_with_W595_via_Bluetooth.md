---
title: "Sync Evolution with W595 via Bluetooth"
date: 2009-08-24
forum: Hardware
---

### Post by The Foz on 2009-08-24
Has anyone successfully managed to synchronise a Sony Ericsson W595 mobile phone with Evolution, via Bluetooth?

I have 2 mobile phones: a Nokia N95, for private use; and a Sony Ericsson W595, for work.

I used this how-to to get my N95 synchronising with Evolution: [http://ubuntuforums.org/showthread.php?t=705103]("http://ubuntuforums.org/showthread.php?t=705103"). It worked completely without problems.

I then tried to connect my W595, but no luck. The bluetooth connection itself works fine, and I am able to browse the phone memory & memory card. I have set the phone as "trusted" in the Bluetooth Device Manager, and the computer as "authorised" on the phone. I checked that the SyncML channel is 10, and I have entered the correct MAC address in the configuration of Multisync. When I try to synchronise, I get a connection error on the OBEX (phone) connection.

I have tried changing some of the parameters in the configuration of the OBEX SyncML connection. What I currently have is:
```
<?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:23:45:74:B6:E9</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>0</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>0</wbxml>
  
  <!-- The username to use. Leave empty to not require a username -->
  <username></username>
  
  <!-- the password for the username -->
  <password></password>
  
  <!-- sets the connection type to use. 5 means obex over usb, 2 means obex over bluetooth -->
  <type>2</type>
  
  <!-- If wbxml is enabled, defines wether the wbxml should use string tables -->
  <usestringtable>0</usestringtable>
  
  <!-- Never send ADD command, but send REPLACE (not needed normally) -->
  <onlyreplace>0</onlyreplace>

  <!-- Workaround around for mobile phones which only use local timestamps and _no_ UTC timestamps! -->
  <onlyLocaltime>0</onlyLocaltime>
  
  <!-- Sets the maximum allowed size in bytes of incoming messages (some device need this option set). Example: 10000 -->
  <recvLimit>0</recvLimit>
  
  <maxObjSize>0</maxObjSize>
  
  <!-- The name of the contacts db. Must be the same as the phones sends -->
  <contact_db>Contacts</contact_db>
  
  <!-- The name of the calendar db. Must be the same as the phones sends -->
  <calendar_db>Calendar</calendar_db>
  
  <!-- The name of the note db. Must be the same as the phones sends -->
  <note_db></note_db>
</config>

```

If anyone out there managed to get it working, I would appreciate knowing how.

---

### Post by The Foz on 2009-08-26
bump!

---

### Post by calucifer on 2009-12-26
bump a de bump

Yes, I have. Not 5 minutes ago I synced contacts (went the wrong way and wiped all my contacts, but hey, you cant have it all can you :P)

Using syncml and multisync-gui (Not multisync which is a different app altogether)

[LIST]
[*] First off, pair your pc and phone using bluetooth (I use blueman, but I dont think it matters)
[*] Next make sure you have multisync-gui and opensync-plugin-evolution and opensync-plugin-syncml
[*] Open multisync-gui (it's in the accessories folder) and add a new group and choose edit
[*] Add members syncml over obex client and evolution 2.x
[*] click on syncml-obex-client and in the code window is a default configuration. I only needed to add my bluetooth_address and bluetooth_channel - which is 10 by the way
[*] All other setting should be fine
[*] In evo2-sync choose the correct address books, etc
[*] Click close and then refresh to (hopefully) sync your phone
[/LIST]

That's it, bobs your uncles new boyfriend :)

Some extra info, in case you need it
"hcitool scan" - this will scan your bluetooth "network neighbourhood" and find your phone, printing its mac address and name
sdptool browse <mac address> will scan the device associated with <mac address> and report back details on the available services, "OBEX SyncML Client" is the one we want here and it uses channel 10, at least on my phone

---

### Post by snt on 2010-05-09
Hi,

With the last beta version of syncevolution, 1.0 beta 3([http://syncevolution.org/](http://syncevolution.org/)), is possible to synchronize Contacts and Events between Evolution and the W595 via bluetooth. It is really simple to install and configure and has a decent GUI.

In my case, W595 with firmware  R3EG004, the program recognizes contacts with several emails, phone numbers + extra information like birthdays,...

sergio

PD1: Pleas read [_this_]("http://www.estamos.de/blog/2008/11/04/magic-tricks-revealed-how-syncml-works-and-when-it-fails/") before you start.

PD2: mini howto:

The beta 3 version is not (yet)in Lucid. If you want to install it add:

deb [http://downloads.syncevolution.org/apt](http://downloads.syncevolution.org/apt)  unstable main

to your repositories.

Download [_this file_]("http://git.moblin.org/cgit.cgi/syncevolution/plain/test/syncevo-phone-config.py?h=mbc1847"), pair the mobile and the computer  and then type in a terminal:
(The program will remove all your contacts and events  in your handy!!!!back-up  your data before)

```

hcitool scan  # find Mac address, like 00:25:47:C8:E1:23
python syncevo-phone-config.py --bt-address THEMACADDRESSOFYOURMOBILE --advanced --create-config=w595

```

This will create the template for the mobile(Of course, you only have to do it once). 

You can then synchronize by invoking:
```

syncevolution w595

```
or just use the sync-ui tool. 

If you try to synchronize just after you create the template, you may have some communication problems. Just reboot your mobile and try it again__

---

### Post by The Foz on 2010-05-10
Hi snt,

Thanks for your post. It looks very useful. 

I no longer have the W595. It was a work phone, and I don't work for that company anymore. Even so, your information could be very useful if my girlfriend every decides to connect her Sony Ericsson to the computer.

---

