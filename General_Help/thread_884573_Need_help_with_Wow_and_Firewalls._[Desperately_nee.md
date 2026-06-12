---
title: "Need help with Wow and Firewalls. [Desperately need help!?]"
date: 2008-08-09
forum: General Help
---

### Post by Thyssenkrupp on 2008-08-09
okay, so i just installed WoW and am using the blizzard downloader to patch.

but it says i am behind a firewall??

Help??

Also, can i play without patching? i know you can delete the line in realmlist.wtf but then i think it says 'cannot verify version'


Need help asap.

Thanks in advance!


Jak

---

### Post by jerome1232 on 2008-08-09
a) Are you behind a router?

b) Have you set up any firewalls on Ubuntu (defaults are permissive so you shouldn't be having problems

from [http://www.worldofwarcraft.com/info/faq/blizzarddownloader.html](http://www.worldofwarcraft.com/info/faq/blizzarddownloader.html)

> I'm constantly displaying a "connecting to peers" message.
If you are using a firewall, ports 6112, 3724, and 6881 through 6999 must be open in order for the Blizzard Downloader to connect correctly. If you are using a router, you may also need to set up port forwarding for these ports. Refer to your firewall/router's documentation for instructions on opening ports and setting up port forwarding.

    For more information regarding this error, please check out our "Blizzard Downloader Fails to Connect to Tracker or Peers" page, found at this link:
    [http://eu.blizzard.com/support/article.xml?articleId=19616](http://eu.blizzard.com/support/article.xml?articleId=19616)

    For detailed assistance with configuring common routers for the Blizzard Downloader, visit this page:
    [http://eu.blizzard.com/support/article.xml?articleId=19445](http://eu.blizzard.com/support/article.xml?articleId=19445) 

I'm getting a slow download speed, what can I do to improve it?
If you are using a firewall or router, be sure that ports 6112, 3724, and 6881 through 6999 are open and forwarded to your computer and only your computer. Refer to your firewall/router's documentation for instructions on opening ports and setting up port forwarding. Also, make sure that no other programs that use bandwidth are running while using the Blizzard Downloader. 

---

### Post by Thyssenkrupp on 2008-08-09
Ahhh i see, so what firewalls are installed on ubuntu by defualt?

---

### Post by jerome1232 on 2008-08-09
iptables but it's set to accept all connections by default

---

### Post by nbayiha on 2008-08-09
It's not the firewall of Ubuntu who is blocking Wow.
First you got to check where you leave. Are you in LAN with people or at Home? Who is the one giving you internet ?

---

