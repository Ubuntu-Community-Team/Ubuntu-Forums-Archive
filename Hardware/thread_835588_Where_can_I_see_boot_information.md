---
title: "Where can I see boot information"
date: 2008-06-20
forum: Hardware
---

### Post by mshumer on 2008-06-20
Hello Everyone,
I have Ubuntu 8.04 installed on Sony Vaio R505DL and love it. I would like to make the configuration work better though. I am able to see scrolling text during the boot process but cannot find where, if any, this output is stored. 

Is there a way to capture all the data that scrolls across my screen during the boot process to one file?

Thanks for everything!

---

### Post by likuidkewl on 2008-06-20
Have a look at:
$dmesg | more 
and 
$more(or vim) /var/log/syslog

HTH

---

### Post by sdennie on 2008-06-20
likuidkewl provides good options.  Another way to view logs is to go to System->Administration->System Log.

---

### Post by mshumer on 2008-06-21
Thanks!

---

