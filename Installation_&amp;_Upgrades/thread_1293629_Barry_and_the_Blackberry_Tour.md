---
title: "Barry and the Blackberry Tour"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by iamgeniusrnti on 2009-10-17
Firstly, I wanted to  say hi as a new member to the forum.

I have been using Linux for about a week now and loving it.  Most of the problems I come into I was able to solve using this site and google.  I have also spent the last month reading before I installed it so I have a little idea of what is going on LOL!

But before I can completely delete windows and use Linux 24/7 I need to be able to sync my blackberry Tour.

WHen I run barrybackup, I was getting a command table error which I thought was resolved by doing this: sudo cp /lib/udev/rules.d/10-blackberry.rules /lib/udev/rules.d/65-blackberry.rules.  But that made things worse.

Currently, when I run btool -l, it finds the device so long as I put the BB in Mass Storage mode.  If I don't answer the question at all, it will find the device.  But if I use btool -t, it can't list the databases.

If I run barrybackup, it finds the BB and the BB tries to connect but then I get:

Desktop: error getting command table
Sent packet:
    00000000: 06 00 0a 00 40 00 00 01 00 00                    ....@.....

Response packet:

Sent packet:
    00000000: 00 00 08 00 0b 06 00 08                          ........

Response packet:

And if I run msynctool --sync Blackberry, I get this:
Member 1 of type barry-sync had an error while connecting: (-110, No error): Timeout in usb_bulk_read
Deadlock potential - avoiding evil bug!

How do I get this thing to communicate?!?

---

### Post by iamgeniusrnti on 2009-10-17
WOOT!  Got it!  I found the .16 update and manually installed the debian packages.  Worked like a charm!

---

