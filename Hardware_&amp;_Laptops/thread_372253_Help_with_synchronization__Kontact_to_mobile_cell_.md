---
title: "Help with synchronization  Kontact to mobile cell phone"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by robertpolson on 2007-02-27
Please help.

I really need to have my KDE Kontact - Contact and Kalendar synced with my Nokia N73 Symbian phone.

So far I have tried Kmobiletools, but they do not work. I can only connect my phone, but fetching or syncing the address book does not work.

The other 2 options that I thought about are no good:

1) Export ical data to phone as a phole, find some symbian software that can import ical data and do this every time manually which will get annoying.

2) Use services like zyb.com or [https://www.mobical.net](https://www.mobical.net) or goosync 


But then I have to pay for GPRS and giving out all my info sucks.

So it is either Windows Vista or somehow I will sync my Kontact data with my phone.

Please save me from Vista.

---

### Post by ltmon on 2007-02-28
I sync my stuff using OpenSync and a Nokia 6131 over bluetooth.

It's not pretty, because you need a really bleeding-edge recent version of OpenSync.  You can get this with the repositories:
```

deb http://www.in.fh-merseburg.de/~jahn/ edgy main 
deb-src http://www.in.fh-merseburg.de/~jahn/ edgy main

```

The packages you need are:
kitchensync-opensync, libopensync-plugin-kdepim, libopensync-plugin-syncml, libqopensync0, msynctool, opensyncutils.

Also make sure you have a functioning bluetooth stack (although I think it can work over usb/serial instead).

Now when you start Kitchensync, it will be based on an OpenSync backend.  I still find it is less error prone to use the command line tool however (msynctool).

Poke around the OpenSync website for instructions ([http://www.opensync.org/](http://www.opensync.org/)) and see how you go.  Let me know what further help you need.

Cheers,

L.

---

### Post by robertpolson on 2007-02-28
Thank you, this gives me more hope.

The sources should be this:

deb [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) edgy main
deb-src [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) edgy main



Can you please give me specific instructions on how to do the syncing with kitchen sync ?

So far I only got to the point where it asks me for the bluetooth device and the channel.

Using this command:

$ hcitool scan
Scanning ...
00:19:79:DD:FF:4A Nokia 73

I got my Nokia device number.

No idea how to get the channel, I did this:

rfcomm connect 0
Connected /dev/rfcomm0 to 00:19:79:DD:FF:4A on channel 2
Press CTRL-C for hangup


So I assumed that the channel is #2, but when I press sychronize, nothing happens.


I also have this:

Modify the file: /etc/bluetooth/rfcomm.conf
rfcomm0 {
# # Automatically bind the device at startup
bind yes;
#
# # Bluetooth address of the device
device 00:19:79:DD:FF:4A
#
# # RFCOMM channel for the connection
channel 2;
#
# # Description of the connection
comment "Nokia N73";
}


from this guide 

[http://www.lynchconsulting.com.au/blog/index.cfm/2006/12/11/Nokia-N73-Bluetooth-modem-with-Ubuntu-Linux-Howto](http://www.lynchconsulting.com.au/blog/index.cfm/2006/12/11/Nokia-N73-Bluetooth-modem-with-Ubuntu-Linux-Howto)



Please give me step by step instructions.

---

### Post by robertpolson on 2007-02-28
The error that I get is - unable to connect one of the member - Mobile Phone SyncML over OBEX client.

I think I have all the right settings there.

> <?xml version="1.0"?>
<config>
  <!-- (Only for bluetooth) The bluetooth address if the bluetooth mode is selected -->
  <bluetooth_address>00:19:79:DD:FF:4A</bluetooth_address>
  
  <!-- (Only for bluetooth) The bluetooth channel to use. `sdptool browse $MAC` to search for the correct channel -->
  <bluetooth_channel>10</bluetooth_channel>
  
  <!-- (Only for USB) The usb interface number of the SYNCML-SYNC target. use syncml-obex-client -u (you will need access to the USB raw device) to find it. -->
  <interface>0</interface>
  
  <!-- The string that the plugin will use to identify itself. Some devices need a special string here. -->
  <identifier>PC Suite</identifier>
  
  <!-- The syncml version to use: 0 for 1.0, 1 for 1.1 and 2 for 1.2 -->
  <version>2</version>
  
  <!-- if the plugin should use wbxml -->
  <wbxml>1</wbxml>
  
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
  <note_db>Notes</note_db>
</config>


---

### Post by ltmon on 2007-02-28
I pretty much used the sample config for the 6230i over bluetooth taken fromhttp://www.opensync.org/wiki/syncml-guide.  This likely worked for me because I use a series 40 phone, but yours is a series 60. 

According to this: [http://www.wahlau.org/series_60_3rd_edition_nokia_n73_synchronization_with_opensync_under_ubuntu_edgy](http://www.wahlau.org/series_60_3rd_edition_nokia_n73_synchronization_with_opensync_under_ubuntu_edgy) your bluetooth channel should be 13.

Cheers,

L.

---

### Post by robertpolson on 2007-02-28
Are you able to sync your Calendar or just Contacts ?

---

### Post by ltmon on 2007-02-28
I've never really tried the calendar properly, although I did sync a year or more worth timesheets into my phone accidentally once :shock:

Generally speaking I only do contacts.

---

### Post by robertpolson on 2007-02-28
Can you please see if you can get your calendar synced?

Or you will get what I get:

> Member 2 of type kdepim-sync had an error while getting changes: Broken Pipe
Member 2 of type kdepim-sync had an error while disconnecting: Broken Pipe
Member 1 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members
Error while synchronizing: Unable to read from one of the members

I cannot get my contacts synced from kde to my phone.

It just looks like it finds them but they do now show up in the phone.

---

### Post by robertpolson on 2007-03-03
Ok here is the solution that works:

Example of my syncml-obex-client config using multisync-gui program:

> <config> <username></username> <password></password> <type>2</type> <bluetooth_address>00:19:69:DD:FF:4C</bluetooth_address> <bluetooth_channel>10</bluetooth_channel> <interface>0</interface> <version>1</version> <identifier>PC Suite</identifier> <wbxml>1</wbxml> <recvLimit>0</recvLimit> <maxObjSize>0</maxObjSize> <usestringtable>0</usestringtable> <onlyreplace>0</onlyreplace> <contact_db>Contacts</contact_db> <calendar_db>Calendar</calendar_db> <note_db>Notes</note_db> </config>



To find out what channel you need, use this sdptool browse 00:19:69:DD:FF:4C <&#8212; your phone ID

Using this command I sync:

> msynctool --sync test --filter-objtype todo --filter-objtype event --filter-objtype note --slow-sync contact


Work is in progress to make calendar entries sync: [http://www.opensync.org/ticket/449#preview](http://www.opensync.org/ticket/449#preview)

---

