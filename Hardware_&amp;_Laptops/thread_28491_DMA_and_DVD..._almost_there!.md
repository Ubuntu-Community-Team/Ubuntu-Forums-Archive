---
title: "DMA and DVD... almost there!"
date: 2005-04-20
forum: Hardware &amp; Laptops
---

### Post by markyp on 2005-04-20
Hello all - wonder if anyone can help?

I've spent the last week sorting my 2 x DVD drives (hda / hdb), neither of which had DMA enabled. I've edited my hdparm.conf (uncommented the relevant section), added a line dedicated to my via chipset at the top of /etc/modules... and I'm inches from the finishing line.

The script telling hda to boot with DMA enabled now works (even though the messages during boot tell me that it can't find hda!). But when I add a refence to hdb to hdparm.conf, the boot process freezes half way through.

I can activate DMA on the second drive once I've logged in (hdparm /dev/hdb), and it works. But I can't understand for the life of me why the addition of the exact same script that enables hda for hdb is causing the whole show to lock up. 

I'd be grateful for any help / guidance anyone could lend. 

Thanks in advance.

markyp

---

### Post by soul_rebel on 2005-04-21
i am having a similar situation on my laptop. hdb is not found when hdparm is fired on boot. I simply removed that section from hdparm.conf and found that dma was still on!

another solution can be to move the script later in the process

---

### Post by Miggy on 2005-04-21
Hi,

I had a similar problem and already discussed it under the following link:

[http://www.ubuntuforums.org/showthread.php?t=25499&highlight=hdparm.conf](http://www.ubuntuforums.org/showthread.php?t=25499&highlight=hdparm.conf) 

Perhaps this can help
Miggy

---

### Post by markyp on 2005-04-21
Thanks for your help... I'll give it a go.

markyp

---

### Post by nehalem on 2005-04-21
I never had this issue and I'm not sure why...

I mean I just changed my hdparm.conf and it worked. 

Isn't the issue involving bootup dependancies and stuff and if so why would it effect some and not others.

---

### Post by dusu on 2005-04-21
Hi,
being not so experimented in linux, I followed another route that I found there 
[http://www.ubuntuforums.org/showthread.php?p=126561](http://www.ubuntuforums.org/showthread.php?p=126561)
the idea is to add some lines
```
hdparm -d1 /dev/hda
hdparm -d1 /dev/hdb
```
in the end of the file /etc/init.d/bootmisc.sh
maybe it can help someone...

---

### Post by markyp on 2005-04-22
Thanks for the replies. One thing: do I add the entries to /etc/init.d/bootmisc.sh *and* keep the uncommented entry in hdparm./conf?

It would be great if at soe stage someone would write a complete walkthrough for this one - from my days scouring the forums, there's some brilliant advice... but it's all in different places. There will be a person out there who's cracked this, and is emminently qualified to write an ABC guide.

Again, many thanks.

markyp

---

### Post by dusu on 2005-04-22
[QUOTE=markyp]Thanks for the replies. One thing: do I add the entries to /etc/init.d/bootmisc.sh *and* keep the uncommented entry in hdparm./conf?

It would be great if at soe stage someone would write a complete walkthrough for this one - from my days scouring the forums, there's some brilliant advice... but it's all in different places. There will be a person out there who's cracked this, and is emminently qualified to write an ABC guide.

Again, many thanks.

markyp[/QUOTE]

Hi,
I've only modified the /etc/init.d/bootmisc.sh file, but I did not touch the default hdparm.conf file.
And yes, it would be good to find a howto on this !

---

