---
title: "canon mx479 scanner not found"
date: 2016-07-26
forum: Hardware
---

### Post by matt18 on 2016-07-26
Ello. I have an interesting issue. I have a canon mx479 printer/scanner. The funny thing is, the printer works just fine when printing off of ubuntu, but i can not scan at all. I try to open many scanner utils and none of them can even find the scanner. 

i have installed the driver from canon themselves and still no go. 

thanks

---

### Post by weatherman2 on 2016-07-26
Did you try scangearmp from Canon?

Try getting it and installing it from here:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100587102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100587102.html)

Extract it, then in a terminal type:

```

cd Downloads
cd scangearmp-mx470series-2.30-1-deb
sh ./install.sh

```

(Follow the prompts)

Then run "scangearmp" to launch it and scan.

---

### Post by matt18 on 2016-07-27
> **weatherman2 said:**
> Did you try scangearmp from Canon?

Try getting it and installing it from here:

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100587102.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100587102.html)

Extract it, then in a terminal type:

```

cd Downloads
cd scangearmp-mx470series-2.30-1-deb
sh ./install.sh

```

(Follow the prompts)

Then run "scangearmp" to launch it and scan.

I juat tried it and it still says same thing... No scanners detected.

EDIT. i tried again and this time i hit search for scanner and it found mine haha

thanks. hopefully it will work after a restart. i hope i dont have to keep searching for it. haha. I tried so many drivers its not funny. all from canon themselves.

---

### Post by matt18 on 2016-07-27
So why is it that the official driver i downloaded from canon for linux did not work?

---

### Post by weatherman2 on 2016-07-27
It may not be the driver at all.  It could be that the scanning software you are trying to use (besides Canon's scangearmp) doesn't have it in the list of supported scanners it knows about.

Scangearmp works OK - not great but does the job most of the time for me.

---

