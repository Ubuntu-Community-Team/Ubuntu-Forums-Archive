---
title: "Nokia N73 mobile and synchronization"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by toon on 2007-02-25
Hello,

I'm having a lot of troubles getting my n73 up and running with linux. The only guide I've found on the internet is about using n73's 3g to connect to the internet. I have no use for this.

I want to be able to send/read text-messages (SMS) on my computer, and sync my contacts/calendar with kontact in KDE. When I saw kmobiletools I was thrilled with joy, sadly it doesn't work very well at all with this phone.

Can anyone point me somewhere, or perhaps help me here?

Thank you for your time.

---

### Post by toon on 2007-02-25
After a bit of looking around, I got opensync up and running, somewhat.

Running it gives this:

received event dsession
received contact dsession
received note dsession
Member 2 of type syncml-obex-client just connected
All clients connected or error
KCrash: Application 'libopensync-kdepim-plugin' crashing...
Member 1 of type kdepim-sync had an error while getting changes: Broken Pipe
Member 1 of type kdepim-sync had an error while disconnecting: Broken Pipe

and then a lot of
Received an entry 245 with data of size 4 from member 2 (syncml-obex-client). Changetype ADDED

and then: 
Member 2 of type syncml-obex-client just sent all changes
Member 2 of type syncml-obex-client just disconnected
All clients have disconnected
The sync failed: Unable to read from one of the members

---

### Post by robertpolson on 2007-02-26
I use Kubuntu and so far no success in getting my phonebook synced.

The only thing I have achieved so far is I managed to connect my nokia phone but kmobile tools does nothing when it fetches sms and address book. It just says that it fetched and I see no data, nor can I move anything to my phone - phone book is full error. Even though I have lots of space in my phonebook.

---

### Post by Nordoelum on 2007-06-08
Link to the 3G connection guide?

---

### Post by kiddyfurby on 2007-07-02
The guide for sync-ing E-series with evolution works for n73
[http://ubuntuforums.org/showthread.php?t=260676](http://ubuntuforums.org/showthread.php?t=260676)

Also, n73 can connect to your network via bluetooth, u can sync like crazy once u are online
[http://ubuntuforums.org/showthread.php?t=471441](http://ubuntuforums.org/showthread.php?t=471441)

---

