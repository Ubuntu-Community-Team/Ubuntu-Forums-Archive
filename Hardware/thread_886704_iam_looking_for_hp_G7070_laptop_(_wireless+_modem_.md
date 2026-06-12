---
title: "iam looking for hp G7070 laptop ( wireless+ modem ) drivers"
date: 2008-08-11
forum: Hardware
---

### Post by Cold zero on 2008-08-11
Hello there ,

Can any one help me to find any linux drivers for these hardwares

1. hp G7070 laptop | HDAUDIO Soft Data Fax Modem with SmartCP
2. hp G7070 laptop | Atheros AR5007 802.11b/g WiFi Adapter
3. hp G7070 laptop | Realtek RTL8139/810x Family Fast Ethernet NIC


iam using ubuntu 7.

witing ur help ,

---

### Post by Bucky Ball on 2008-08-11
Why 7? (which would be Ubuntu Gutsy 7.10 probably). The newer version, Hardy Heron 8.04 may fix some of you problems more easily, though.

For the Realtek wireless card (among other things), you could try here;

> [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?action=fullsearch&context=180&value=atheros&titlesearch=Titles](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?action=fullsearch&context=180&value=atheros&titlesearch=Titles)

---

### Post by Cold zero on 2008-08-11
can u help me more ?

give me direct link please , 

thank u so

---

### Post by Bucky Ball on 2008-08-12
Not sure what languages you speak, but there are a whole lot of links on this page;

[http://au.altavista.com/web/results?itag=ody&q=hp+g7070+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=hp+g7070+ubuntu&kgs=0&kls=0)

Mostly not in english so not sure how helpful. This much I can tell you; the atheros uses madwifi to run, realtek looks like it uses ndiswrapper.  Both of these softwares use windoze drivers (the ones you will find in your windoze install). You need to do a bit of research on these two in relation to your particular wireless cards.

It is not quite as easy as a direct link to get these things going (linux is not ubuntu and the reason for the workarounds is some manufacturers don't make available Linux drivers making life difficult).

As I say, Hardy 8.04 may make the task easier, but for the moment, have a look where I suggest and let me know how you go. Google for instance;

 'Realtek RTL8139 ubuntu Gutsy'

etc, and see what you come up with.

Bit busy but will check back later and look a bit more when I have some time tonight. Good luck :)

* This could get you started for the Atheros:

[http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

---

### Post by Cold zero on 2008-08-12
thank bro , 

i have fixed it by this topic

[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)

===============================


but i have now some problim's

i have upgradeto 8.4, but after that when install the upgrade became to end its stop .. :mad:

now whin iam try to login with my user.. it's logged but gave me orange screen without any thing alse.. and take alot of time without any response ..

what the problim here ?

---

### Post by Bucky Ball on 2008-08-13
does it log you in eventually or just hang?

---

### Post by Cold zero on 2008-08-13
i have wait about 7-10 min .

but still hang 

after i logged into the os ,

i have only an orange background ,

then i test to see if the keyboard working by press the print screen key , and it's gave me the snapshot window ..

could u help me to fix the problim please ?

thank u so much

---

### Post by Bucky Ball on 2008-08-13
Boot into the recovery kernel (select the kernel at boot below the normal one - it will have 'recovery' at the end). Try and write down any errors it throws and post them here if you could. :)

When you are booted in at the moment on the orange screen, what happens when you right click with your mouse? Are you getting a menu of options or nothing?

---

