---
title: "lost windows password / data retrieval with ubuntu"
date: 2008-09-15
forum: General Help
---

### Post by beginner's love on 2008-09-15
I have a Vaio laptop and decided to put a password which I forgot, and I do not have a password CD-Rom. I can reinstall the Windows Vista OS but I would in that case destroy the personal data (pictures mainly) inside the computer. I tried therefore to start the laptop with ubuntu CD and succeeded but to my surprise it seems that ubuntu cannot see the hard disk because I do not see any of my data when I go to Ubuntu file manager. Do you have an idea of what I could do?:popcorn
Best regards,
Richard

---

### Post by gvartser on 2008-09-15
Check out this tutorial on how to mount a windows partition into your Ubuntu OS.

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

/g

---

### Post by houbysoft.xf.cz on 2008-09-15
> **gvartser said:**
> Check out this tutorial on how to mount a windows partition into your Ubuntu OS.

[http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/](http://www.cyberciti.biz/faq/mounting-windows-partition-onto-ubuntu-linux/)

/g

I may be wrong, but this won't help. It'll sure mount the partition but you won't see your data in here anyway. I have had a similar problem with a friends' laptop. I'm sure there is a way to see the files, but I don't have had much time investigating it, so I just downloaded a copy of ophcrack, burned it under Ubuntu or whatever OS you can boot into, and then I booted from the newly created CD, got the Windows password, and then retrieved all his (friends') files. I suggest you to do the same if the mounting won't help.

Ophcrack is a program for retrieving windows passwords pretty fast, and you can find it here : [http://ophcrack.sourceforge.net/download.php?type=livecd](http://ophcrack.sourceforge.net/download.php?type=livecd).

Download the Vista liveCD and burn it in Ubuntu the same way like you did with the liveCD ("burn iso" or something like that option).

Hope that helps.

---

### Post by Promille on 2008-09-15
You can use this LiveCD to find your Windows password (search in the hashes) Worked for me. Good luck

ophcrack.sourceforge.net

EDIT: I was appearently too late :p

---

### Post by beginner's love on 2008-09-15
> **houbysoft.xf.cz said:**
> I just downloaded a copy of ophcrack, burned it under Ubuntu 

last quote:
Download the Vista liveCD and burn it in Ubuntu the same way like you did with the liveCD ("burn iso" or something like that option).
Hope that helps.

[COLOR="Red"]Thanks a lot for this new hope...
a) I downloaded ophcrack 3.0.1 : is it the right one? (there is also ophcrack liveCD, ophcrack tools, samdump2 and tables as alternative files to download)
b) what do you mean by burn it UNDER UBUNTU?[/COLOR]

[COLOR="red"]c) why do I need vista liveCD? and to burn it under ubuntu?
d) After downloading ophcrack, I received a message from the real-time scan saying that spyware classified as hacking tools were downloaded: PWDUMP. Is it normal (part of ophcrack) or a malware?[/COLOR]

---

### Post by Oldsoldier2003 on 2008-09-15
There is no such thing as a legal Vista live cd. Closing this thread because this discussion is against the CoC. You may repost in the windows discussion area but please make it clear you are only looking for legal solutions.

---

