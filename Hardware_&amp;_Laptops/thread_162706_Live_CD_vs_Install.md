---
title: "Live CD vs Install"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by mrpositive on 2006-04-19
Any suggestions as to why a Netgear Card (WG511U) works with the Live CD without any configuration and after doing the install, can only get it to run with ndiswrapper???

---

### Post by vltakacs on 2006-04-20
Breezer Live CD also works with Mac Mini but could not start it with Ubuntu installedon it. Could not handle the video card at all.

:???:

Viktor L. Takacs

---

### Post by az on 2006-04-20
[QUOTE=mrpositive]Any suggestions as to why a Netgear Card (WG511U) works with the Live CD without any configuration and after doing the install, can only get it to run with ndiswrapper???[/QUOTE]
You did the espresso install and upon reboot, you didn't have wireless?

Did you try to configure wireless the same way?


Boot the live cd and post the output of

dmesg

Do the same for your installed system.  Post them as attachments, please...

---

### Post by mrpositive on 2006-04-24
[QUOTE=azz]You did the espresso install and upon reboot, you didn't have wireless?

Did you try to configure wireless the same way?


Boot the live cd and post the output of

dmesg

Do the same for your installed system.  Post them as attachments, please...[/QUOTE]

So let me tell you what I did.  In getting a little frustrated, I switch out HDD and just ran SuSE.  

After reading your post and several others, I did a reinstall of the OS, but the difference this time, I used LVM for the partitions, booted up, checked network connections and it showed the ath0!?!?  Very odd, but it works.  Why the first time it did not, I will leave up to the experts.  I am sure that I will figure it out sometime, but right now, I am just glad that it is working.

Thank you for your response and willingness to help, as you are an Azzet to the community!!

Kirk

---

