---
title: "sending commands to ubuntu via email"
date: 2008-10-10
forum: General Help
---

### Post by mrmooge88 on 2008-10-10
I sometimes forget to turn off my computer and find that I will not be able to access it for awhile. I've found out that I can send and receive emails from my phone. I'd like to be able to send an email, with a prearranged unique number in the body for security purposes, to my computer to have it run a shutdown script if and only if the number in the email matches the number it has. It would be nice to eventually have my computer send me emails when other certain events occur such as updates in rss feeds. I was able to set something similar up in Vista using a Mozilla Thunderbird plugin, but I would rather see what other options are available.

---

### Post by bionnaki on 2008-10-10
can you use ssh on your phone?

---

### Post by mrmooge88 on 2008-10-10
No. I know that makes a bit of a security flaw to the whole idea, which is why I use a unique number in the email. It gives me a little bit of protection, but not much. The worst someone could do is shutdown my computer.

Each unique number will only be used once. Then the next time I access my computer I will change it to a new one.

---

### Post by Titan8990 on 2008-10-10
Just let it run 24/7. No harm in it.

---

### Post by koenn on 2008-10-10
I imagine you could do something like

Set up a mail server or a mail client that drops messages in a specific directory, eg /var/mail/something
set up a program that watches the content of this directory (eg dnotify), and let it execute a script when a file is added to /var/mail/something
let the script
```
    grep the files for your secret number
    if grep is succesfull, then 
        delete the file
        execute a shutdown
```

It sounds like a bad idea alltogether.
shutdown needs to be executed as root, so you'll need workarounds for that, which might eventually allow anyone, with or without knowledge of your secret number, to shutdown your PC at will.

It's probably better to learn to shutdown your PC when you want it shutdown, set a screensaver with password for those times you leave it on, and look if powersave modes can be configured to suspend when inactive and prompt for a password when resuming.

---

### Post by Barriehie on 2008-10-10
I've got a line in my cron file that shuts mine down 20 min. after I've left for work.  Works like a charm!

Barrie

---

### Post by Sam on 2008-10-10
> **Barriehie said:**
> I've got a line in my cron file that shuts mine down 20 min. after I've left for work.  Works like a charm!

Barrie

You don't make a lot of extra hours, don't you ? ;)

---

