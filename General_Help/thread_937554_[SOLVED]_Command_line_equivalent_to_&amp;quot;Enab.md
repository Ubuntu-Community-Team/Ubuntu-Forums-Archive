---
title: "[SOLVED] Command line equivalent to &amp;quot;Enable Wireless&amp;quot;"
date: 2008-10-04
forum: General Help
---

### Post by weasello on 2008-10-04
Hey there,

Using Gnome/Ubuntu (Hardy) I have a wireless logo on the top right. By right clicking on it I can select "Enable Wireless" to either engage or disengage it. I am doing this quite frequently and am hoping to automate this in a script. What is the command-line equivalent to clicking this button?

I tried toying with ifup and ifdown but they seem to disable the Network Manager's ability to see the wifi card altogether, as if it bumps it to manual mode only or something.

---

### Post by iponeverything on 2008-10-04
Download this: Cnetworkmanager is a command-line client for NetworkManager -

[http://repo.or.cz/w/cnetworkmanager.git?a=blob_plain;f=cnetworkmanager;hb=HEAD](http://repo.or.cz/w/cnetworkmanager.git?a=blob_plain;f=cnetworkmanager;hb=HEAD)

save it as /usr/bin/cnetworkmanager and change the perms to 755.

Then run:

cnetworkmanager --wifi=false
cnetworkmanager --wifi=true

ref: [http://mvidner.blogspot.com/search/label/NetworkManager](http://mvidner.blogspot.com/search/label/NetworkManager)

---

### Post by ghostdog74 on 2008-10-04
> **weasello said:**
> Hey there,

Using Gnome/Ubuntu (Hardy) I have a wireless logo on the top right. By right clicking on it I can select "Enable Wireless" to either engage or disengage it. I am doing this quite frequently and am hoping to automate this in a script. What is the command-line equivalent to clicking this button?

I tried toying with ifup and ifdown but they seem to disable the Network Manager's ability to see the wifi card altogether, as if it bumps it to manual mode only or something.

man iwconfig

---

### Post by weasello on 2008-10-04
Perfect! Installing the command line version did exactly what I wanted. Thanks so much.

---

