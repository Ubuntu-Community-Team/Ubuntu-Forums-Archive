---
title: "HP Colorlaserjet CP1515n Colour toner not showing in status"
date: 2008-06-30
forum: Hardware
---

### Post by Col-1023 on 2008-06-30
I've used the automatic installer from the Hplip site to install hplip 2.8.6

I've installed my HP cp1515n printer on the network, and its been recognised by my ubuntu 7.10 box as HP Color LaserJet cp1515n Foomatic/hpijs, hpijs 2.8.6, and I've printed text and photos from it, so it works well.

When I go into accessories/HP Device Manager, and check supplies, only the BLACK toner is showing.

Since this is a colour printer with black, cyan, magneta & yellow toners, how do get the status of the other toners?

I've looked and cant find HP Toolbox, so is the HP Device Manager the new toolbox?

Any help appreciated.

TIA

---

### Post by Col-1023 on 2008-07-01
An additional question is how many watts of power does the cp1515n use while in "powersave mode"?

---

### Post by Col-1023 on 2008-07-02
Any ideas.

---

### Post by Col-1023 on 2008-07-03
bump

---

### Post by Col-1023 on 2008-07-04
anyone

---

### Post by jeromedavies on 2008-08-29
This may not be the answer you were looking for, but most (if not all) HP networked printers have a built in webserver that can provide a wide range of info about the printer including supplies status.

All you should need to do is use Firefox to http:\\[IP Address of printer]

This certianly works with my HP LaserJet 1320n

hope this helps.

---

### Post by fballem on 2008-08-29
The website works. The not showing colour may be a bug. The bug may be filed on launchpad (link: [https://launchpad.net/hplip](https://launchpad.net/hplip))

Hope this helps

---

### Post by Col-1023 on 2008-10-27
Thank you JeromeDavies, your post really helped.

I haven't checked this post for ages, so once I saw your suggesgtion, I tried it and it worked.

I logged into my printers ip address and up came the page with it's status and ink levels, all 4 of them.

---

### Post by Sciamano on 2008-11-29
Hi Col-1023,
I'm interested in the same printer. Could you tell me if you are satisfied with it? How is print quality?
Thanks a lot!

---

