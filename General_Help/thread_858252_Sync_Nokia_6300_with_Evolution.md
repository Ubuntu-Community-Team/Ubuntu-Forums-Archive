---
title: "Sync Nokia 6300 with Evolution"
date: 2008-07-13
forum: General Help
---

### Post by bob1989898 on 2008-07-13
I have Ubuntu 8.04.1 installed on my Asus Laptop and have set up a working Bluetooth Connection between the Computer and my Nokia 6300. 
This weekend I wanted to sync my Evolution Contacts and my Calendar to my mobile and vice versa via Bluetooth. I used the following HOWTO:

[http://ubuntuforums.org/showthread.php?t=260676&page=17](http://ubuntuforums.org/showthread.php?t=260676&page=17)

I used the graphical Method. I only changed the Bluetooth Channel to 11, as it was written in several other Forums.

My Config for the syncml-obex client under Multisync 0.90 is like this (I just deleted the MAC-Adress for this Post):

<config>
	<bluetooth_address></bluetooth_address>
	<bluetooth_channel>11</bluetooth_channel>
	<interface>0</interface>
	<identifier>PC Suite</identifier>
	<version>1</version>
	<wbxml>1</wbxml>
	<username></username>
	<password></password>
	<type>2</type>
	<usestringtable>1</usestringtable>
	<onlyreplace>0</onlyreplace>
	<recvLimit>0</recvLimit>
	<maxObjSize>0</maxObjSize>
	<contact_db>Contacts</contact_db>
	<calendar_db>Calendar</calendar_db>
	<note_db>Notes</note_db>
</config>

But as soon as I try to sync my phone with Evolution via Terminal, I get the following log:

Synchronizing group "Nokia" 
The previous synchronization was unclean. Slow-syncing
Member 1 of type evo2-sync just connected
received contact dsession
received event dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
Member 1 of type evo2-sync just sent all changes
Member 2 of type syncml-obex-client had an error while getting changes: Request not successfull: 64
Member 1 of type evo2-sync just disconnected
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error synchronizing: Unable to read from one of the members
Pipe closed! Exiting.
bob@bob-laptop:~$ Pipe closed! Exiting.

Does anyone knows a Solution or has a similar problem?

---

### Post by lodder on 2009-03-25
Have you solved the problem ?

---

### Post by jeegiz on 2009-04-13
I have resolved this error by removing "Notes" in this way:

> 	<!--  <note_db>Notes</note_db>-->
	<note_db></note_db>-->


---

