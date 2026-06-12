---
title: "Sync for Nokia N70 or other S60 series?"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by tripuz on 2006-12-18
Hi,
I've been trying for several hours to sync my new N70 phone with the addressbook on my (K)ubuntu box, first with Kitchensync and Kontact in KDE, then with Multisync (Opensync) via msynctool and Evolution in Gnome, but couldn't get any result. In KDE the sync won't find my phone, while in Gnome I managed to turn the phone in Sync mode via bluetooth, but then nothing happens.
I was wondering if anyone managed to find out how to complete the sync in Ubuntu with this phone or with other similar phones and if you have some suggestions about this :-) 
Thanks in advance!

---

### Post by Steve H on 2007-03-25
I'm having similar problems trying this. I have just installed Opensync through Synaptic and now none of the commands listed on OpenSync site work. all i've managed is osynctest, which gave the following reply:

--config <filename>     Set the config file to use
--type <object type>    Sets the objtype to test
--empty Only deleta all data. Do not test


huh?! but on the website it says it is msync........help! what have i done wrong?!?!?! I have a Nokia N70 and a Compaq IPAQ that i want to sync with Evolution, is that possible??

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I´ve managed to get it working look [_here_]("http://ubuntuforums.org/showthread.php?t=446724"):

---

### Post by bertsimons on 2008-05-14
after a lot of hours trying I succedded to sync my n70 with kontact using kitchensync.

after some trial and error I found out that in my case the best way to succeed was:

1. set my phone to factory defaults, so empty calendar, notes, contacts and memos.
2. add group member kdedesktop and syncml-obex client to a new group.
3. close kitchensync and manually edit the syncml-obex-client.conf in:
/home/yourname/.opensync-0.22/group1/2 (or1) depending which groupmember you added first.

in syncml-obex-client.conf replace the content with:

<config>
<username></username>
<password></password>
<type>2</type>
<bluetooth_address>xx:xx:xx:xx:xx</bluetooth_address>
<bluetooth_channel>11</bluetooth_channel>
<interface>0</interface>
<version>1</version>
<identifier>PC Suite</identifier>
<wbxml>1</wbxml>
<recvLimit>10000</recvLimit>
<maxObjSize>50</maxObjSize>
<usestringtable>0</usestringtable>
<onlyLocaltime>1</onlyLocaltime>
<onlyreplace>0</onlyreplace>
<contact_db>Contacts</contact_db>
<calendar_db>Calendar</calendar_db>
<note_db>Notes</note_db>
</config>


note that I added:<onlyLocaltime>1</onlyLocaltime>
this is not a standard configurable field of kitchensync and gets deleted if you configure trough kytchensync, that's why the manual edit. If I don't add it I get a lot of duplicate entries in my phonebook etc..

using your bluetooth address and channell
can be found by command in terminal:

 sdptool browse

look for channel number under: Service Name: SyncMLClient

---

