---
title: "Problems with ThinkFinger on Lenovo T61"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by jancogo on 2008-01-22
I just installed Ubuntu 7.10 on my new T61 and I am having some problems with the fingerprint reader. I have followed the guide at [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger) and everything works out except for saving of the .bir files that is generated.

When I try to do a tf-tool --acquire I get to swipe my finger three times and then it says:

Storing data (/tmp/test.bir)...Could not acquire fingerprint (communication with fingerprint reader failed)

Does anyone have any hints or might have had the same problem?

---

### Post by jgreer1969 on 2008-02-23
~$ sudo tf-tool --acquire
Password or swipe finger: 

ThinkFinger 0.3 ([http://thinkfinger.sourceforge.net/](http://thinkfinger.sourceforge.net/))
Copyright (C) 2006, 2007 Timo Hoenig <thoenig@suse.de>

Initializing... done.
Please swipe your finger (successful swipes 3/3, failed swipes: 0)... done.
Storing data (/tmp/test.bir)...Could not acquire fingerprint (communication with fingerprint reader failed).

[B]-Have you received any responses to your question??  
-I have a IBM Thinkpad T42
-:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  [/B]

---

