---
title: "Canon scanner and 12.04"
date: 2012-04-29
forum: Hardware
---

### Post by kurt18947 on 2012-04-29
There have been problems scanning with Precise reported.  I have a Brother MFD scanning after performing tweaks on Brother's site.  Today I tried a Canon Canoscan 8800F which has worked 'out of the box' with previous Ubuntu distros.  I loaded 12.04 and powered up the scanner.  It scanned about half a page and stopped, then gave a 'scanner communication error'.  Closing and restarting resulted in a 'scanner not found' error.  Hmmm.  Checked Users and Groups.  That account was authorized to use scanners.  While I was thinking a 'new updates available' message popped up.  Went ahead and updated, I know it updated the kernel but don't know what else.  I restarted as requested and magic, the scanner is now recognized and functions.  So for anyone having scanner problems, it might be worthwhile to power the scanner up then check for updates.  The Canoscan 8800F works 'out of the box' with 11.10 64 bit.

---

### Post by Fincer on 2012-04-29
I had similar problems earlier with Canoscan Lide 210 while Precise was still on beta/alpha stage. I have Kubuntu installation.

However, I found out that the problem was related to Skanlite, a light program used to scan documents. Since there was no way to get my scanner working with Skanlite, I forcefully installed Xsane. Xsane worked but I still preferred Skanlite because of its' simplicity. A few months passed by and it was yesterday that I found out that Skanlite is finally working again. With Kubuntu 11.10, Skanlite worked all the time. Precise was totally another thing.

So, which programs have you tried when attempting to scan? If you've not already done, give Xsane a try as a temporary solution (it will probably save you from many headaches).

---

### Post by kurt18947 on 2012-04-30
> **Fincer said:**
> I had similar problems earlier with Canoscan Lide 210 while Precise was still on beta/alpha stage. I have Kubuntu installation.

However, I found out that the problem was related to Skanlite, a light program used to scan documents. Since there was no way to get my scanner working with Skanlite, I forcefully installed Xsane. Xsane worked but I still preferred Skanlite because of its' simplicity. A few months passed by and it was yesterday that I found out that Skanlite is finally working again. With Kubuntu 11.10, Skanlite worked all the time. Precise was totally another thing.

So, which programs have you tried when attempting to scan? If you've not already done, give Xsane a try as a temporary solution (it will probably save you from many headaches).

I'm using gnome/gnome-shell.  I tried Simple Scan & Xsane.  Both failed initially and both started working after the update so in my case I don't think it was an app problem but rather a system problem. A scanning application I've grown fond of for creating .pdf archives is gscan2pdf, found in the repos.

---

