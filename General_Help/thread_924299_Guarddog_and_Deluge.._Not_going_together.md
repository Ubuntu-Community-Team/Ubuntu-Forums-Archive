---
title: "Guarddog and Deluge.. Not going together"
date: 2008-09-19
forum: General Help
---

### Post by patsymcox on 2008-09-19
I have installed guarddog. Great firewall. 

But it doesn't work well with deluge.

I have selected Bitorrent Peer and Tracker on both local and internet zones, as well as I have added the protocol I have selected in Deluge settings (which is 34454). 

But Deluge uploads, but no download. 

How to get these two apps ( Guarddog and Deluge) work together as friends?

Thanks

---

### Post by lovinglinux on 2008-09-19
I know you are trying all firewall interfaces out there, so does Deluge works properly with Firestarter only? If it does, then you have a bad configuration in Guarddog. If it doesn't, then you probably haven't configured your router properly to forward the port required for incoming connections (unless you have a bad Firestarter configuration too).

Don't mix Guarddog and Firestarter, because both are only GUI's to iptables, so they usually override each other settings. Sometimes, when trying two different firewall gui's you can introduce a blocking rule that is not properly wiped by the other gui, resulting in unwanted blocked ports or services.

I would recommend sticking with Firestarter and use [[COLOR="DarkRed"]**Moblock/Mobloquer**[/COLOR]]("http://moblock-deb.sourceforge.net/") for additional security. I use them with Deluge and I'm very pleased with this combination. Guarddog was a little bit too much for me, even being former Windows/ComodoFirewall experienced user.

---

### Post by patsymcox on 2008-09-19
Thanks for the info, I'll stick with Firestarter, But you know something about BASIC configuration of firestarter? I need HTTP,HTTPS,Yahoo chat and torrents.

Is there any default configuration there? I am a geek about setting rules for firewall, and I dont find much help configuring Firestarter.

Thanks

---

### Post by lovinglinux on 2008-09-19
[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by patsymcox on 2008-09-19
I think default policy will suffice.

Thanks dude.

---

### Post by patsymcox on 2008-09-19
Did you seen this post?

[http://ubuntuforums.org/showthread.php?t=854311&highlight=moblock](http://ubuntuforums.org/showthread.php?t=854311&highlight=moblock)

---

### Post by lovinglinux on 2008-09-19
> **patsymcox said:**
> Did you seen this post?

[http://ubuntuforums.org/showthread.php?t=854311&highlight=moblock](http://ubuntuforums.org/showthread.php?t=854311&highlight=moblock)

Yep, is old news. Not a big deal once you understand how it works. All you have to do is restart Moblock every time you touch Firestarter configuration. That's why I keep "Apply policy immediately" unchecked in Firestarter. Therefore, any changes will only take effect after hitting "Apply Policy" button and I know I have to restart Moblock. Besides, Mobloquer has a tool to check if it's rules are configured above all others (requirement) and I usually test it with a known blocked IP address to see see if it is blocking properly.

---

