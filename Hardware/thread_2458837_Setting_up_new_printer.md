---
title: "Setting up new printer"
date: 2021-03-04
forum: Hardware
---

### Post by acefromspace on 2021-03-04
Trying to get the new HP printer to work.
Using Ubuntu 16.04, HP OfficeJet Pro 8020 printer and hplip 3.20.5
Everything seems to be fine (including system detecting printer, hplip newer version installed, printer is listed as needing 3.19 or higher... using 3.20.5) It is connected by USB cable. Did hp-setup (using terminal) and everything went smooth.
Printer is not responding and gives message  "finish setup". Did HP diagnostic tool and this is what it shows:
Checking for Configured Queues....
warning: Fail to read ppd=/etc/cups/ppd/HP-Fax-4.ppd file
warning: Insufficient permission to access file /etc/cups/ppd/HP-Fax-4.ppd
warning: Could not complete Queue(s) configuration check
hplip shows print que sent, printed and completed but printer doesn't respond. I suspect it has not installed the driver but it actually lists the printer and shows ink status (all full of course)
Is this some kind of permission issue? did I install hplip in the wrong place? Missing dependencies?
I am going to do fresh install of Ubuntu 20 soon (16 is going to expire soon) would that help? My understanding is the driver(s) are includied with hplip.

---

### Post by acefromspace on 2021-03-04
BTW... don't need Fax to work (just print and scan)

---

### Post by TheFu on 2021-03-04
```
warning: Fail to read ppd=/etc/cups/ppd/HP-Fax-4.ppd file
warning: Insufficient permission to access file /etc/cups/ppd/HP-Fax-4.ppd
```
Permissions. Fix this first. Appears only *read* is needed.

---

### Post by acefromspace on 2021-03-05
So it does seem to be permission issue?

---

### Post by Impavidus on 2021-03-05
> **acefromspace said:**
> So it does seem to be permission issue?
It looks like it.

> **acefromspace said:**
> 
I am going to do fresh install of Ubuntu 20 soon (16 is going to expire soon) would that help? My understanding is the driver(s) are includied with hplip.
Ubuntu 20.04 comes with hplip 3.20.3, so there would be no need to manually install a more recent version. One thing fewer that can go wrong. BTW, there are several packages for a full hplip: hplip, hplip-data, hplip-doc, hplip-gui. Did you upgrade all of them?

---

### Post by TheFu on 2021-03-05
> **acefromspace said:**
> So it does seem to be permission issue?

Something is complaining that it can't read a file - twice.  It isn't saying that the file doesn't exist or any of the 50 other errors. It says it cannot read it. This is trivial to correct when you understand Unix permissions and can see what the current permissions, owner, group, is today - like you can.  

If you don't know what to do, that means you'll need a little understanding of Unix permissions to fix it.  [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is a tutorial. that probably covers 90% of what users need to know and 80% of what an admin needs to know.

If you would like more specific help, post the output from **ls -al** for the file and the parent directory. We need both, since both impact whether a process can read a file.  It would also be helpful if you could post the userid that the process runs under.  Linux is multi-user. Every process runs with a specific userid. That userid determines the level of access it has to any directory and files.

BTW, here's what that directory looks like for my 20.04 system:
```
$ ll /etc/cups/ppd/
total 44
drwxr-xr-x 2 root lp  4096 Jan  3 13:13 ./
drwxr-xr-x 5 root lp  4096 Mar  5 00:00 ../
-rw-r----- 1 root lp 12328 May  2  2020 laser.ppd
-rw-r----- 1 root lp 19898 Jan  3 13:13 MFC240C.ppd
```
I have 2 printers. They are physically connected to another system on the network, but printing from this desktop works fine.

---

### Post by slickymaster on 2021-03-05
*Thread moved to **Hardware**.*

---

### Post by acefromspace on 2021-03-05
I have basic understanding of how permissions work (I also know how to use terminal to fix this but it's been awhile and my memory is not good... 60 years old)
This is the tutorial I used to install hplip:
[https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index](https://developers.hp.com/hp-linux-imaging-and-printing/install/install/index)
I will try to fix this (for now... just to use the printer and see how it works) but going to do fresh install of Ubuntu 20 very soon so all is well. Good to know I don't have to install hplip again :)
The very first step of the install says cd Desktop (change directory) I may have messed that up... that might explain the permission issues. I'll be honest, years ago I really tried to learn more about Linux and using terminal then got spoiled by Ubuntu... everything seemed easy and I got lazy.
Now I am having to re-learn things.

---

### Post by acefromspace on 2021-03-05
Thank you for moving this thread to the hardware forum.
On a side note, my son installed Ubuntu 16 on this computer (it's my mother's desktop... she is 81 years old) He doesn't like Unity so changed it to the old style. I love Unity (had a little trouble getting used to it at first but really like it now)
Now I have to teach mom to use it (what's that saying... "teach an old dog new tricks")

---

### Post by brian_p on 2021-03-05
> **acefromspace said:**
> Trying to get the new HP printer to work.
Using Ubuntu 16.04, HP OfficeJet Pro 8020 printer and hplip 3.20.5

Ubuntu 16.04? Printing technology has moved on considerably since then. You want to stay with 16.04 with a modern printer and pass on the benefits? Your choice, then. My help stops here.

> Everything seems to be fine (including system detecting printer, hplip newer16.04 version installed, printer is listed as needing 3.19 or higher... using 3.20.5) It is connected by USB cable. Did hp-setup (using terminal) and everything went smooth.
Printer is not responding and gives message  "finish setup". Did HP diagnostic tool and this is what it shows:
Checking for Configured Queues....
warning: Fail to read ppd=/etc/cups/ppd/HP-Fax-4.ppd file
warning: Insufficient permission to access file /etc/cups/ppd/HP-Fax-4.ppd
warning: Could not complete Queue(s) configuration check
hplip shows print que sent, printed and completed but printer doesn't respond. I suspect it has not installed the driver but it actually lists the printer and shows ink status (all full of course)
Is this some kind of permission issue? did I install hplip in the wrong place? Missing dependencies?
I am going to do fresh install of Ubuntu 20 soon (16 is going to expire soon) would that help? My understanding is the driver(s) are includied with hplip.

There is no permission issue.

---

### Post by acefromspace on 2021-03-05
"[COLOR=#000000]Ubuntu 16.04? Printing technology has moved on considerably since then. You want to stay with 16.04 with a modern printer and pass on the benefits? Your choice, then. My help stops here."
First off... it's not my computer (it's my 81 year old mother's) She has to approve everything I do and is not computer savvy (and very stubborn) so don't blame me.
No permission issue? So others are wrong about this? And yet you offer no explanation or advice on how to resolve this. Thanks for nothing I guess.
[/COLOR]

---

### Post by acefromspace on 2021-03-05
BTW, mother prints mostly text files and crossword puzzles... how much printer technology does that require? I am allowed to use the computer and printer and would like to print images (I'm very into photography) so yes, it would be nice to have full functions available, but right now I just need to get it working for her. I did mention doing a fresh install of Ubuntu 20 very soon. Is this brian guy always this rude?

---

### Post by acefromspace on 2021-03-05
I quoted this from the install tutorial... "[COLOR=#333333][FONT=HPSimplifiedLight]These instructions assume that the hplip-3.21.2.run file was downloaded to your Desktop directory. You may have to adjust the 'cd' command based on where your web browser saved the file on your system."
Not sure if this matters but I may have messed up (hey, I did admit I'm out of practice with using terminal) I'm actually wondering if I still have the older version (3.16) on here. Doesn't matter... fresh install of Ubuntu and problem solved.[/FONT][/COLOR]

---

### Post by brian_p on 2021-03-05
There you go. An up to date Ubuntu works wonders! And, no permission issues :D.

(A PPD is only readable by a process with root privilege. This is by design. The installing HPLIP  process does not have root privileges. The warning message is perfectly normal and very common, as can be verified with a search).

---

### Post by rsteinmetz70112 on 2021-03-06
Nobody should be installing 16.04 it will be EOL soon.
Installing hplip from the hp's websites is not necessarily adapted to Ubuntu.
My suggestion is to install 20.04 LTS and try again. 
As an alternate you could do-release-upgrade to 18.04 then again to 20.04

If you insist on 16.04 please provide an list /etc/cups/ppd

---

### Post by acefromspace on 2021-03-08
Thank you all (even brian) I don't do upgrades... prefer fresh install... 20.04 LTS

---

### Post by brian_p on 2021-03-08
> **acefromspace said:**
> Thank you all (even brian) I don't do upgrades... prefer fresh install... 20.04 LTS

Thank you for the mention, acefromspace. I was probably a bit grumpy at the time I wrote what I did. However, it was intended to invite you to consider the situation. A user really does get more for their money with printing on 20.04. 20.10 provides even better value for USB connected printers.

---

### Post by acefromspace on 2021-03-11
I did a fresh install of Ubuntu 20.04 then did update (I like to do that after install but don't think it matters either way)
Turned on printer and went to Printer and it showed (it actually shows two... I think one is considered the FAX part)  I chose the first one listed as default printer (may have chose the wrong one?) Will check that again.
How do I check that hplip is installed? Someone mentioned doing list/ect/cups/ppd in terminal. Do I need to do sudo for that? Please give me a specific command for this.
Should I consider connecting the printer through network instead of USB?

---

### Post by acefromspace on 2021-03-11
Do I need to run hpsetup (in terminal)? If so, do I do I do this using sudo?

---

### Post by brian_p on 2021-03-11
> **acefromspace said:**
> 
Should I consider connecting the printer through network instead of USB?

Definitely. All **modern** network-capable printers work in that way with 20.04.

---

### Post by acefromspace on 2021-03-11
I have never done this before. I have a network cable. So after I connect it, what's next (I know I am asking for someone to "hold my hand" and walk me through this)
I got back into settings/printer and brought up a thing that shows "Install PPD file" Should I try this first?
I have two kinds of network cables (forgot the terms but they are wired differently depending on the use) My son is the network guru so might wait and have him do that for me.

---

### Post by acefromspace on 2021-03-11
Removed printer(s)... disconnected USB, connected network cable. Talked to my son... he is going to do the rest for me. He said "too easy dad" (he took some college courses... CISCO networking)
Will I also be able to scan? Don't care about Fax.

---

### Post by acefromspace on 2021-03-11
My son had a long hard day at work so didn't show... but he told me how to do this. Turned on printer... it recognized the network connection and showed info (like the IP address) Went to computer settings/printer... there it was (and said ready)
Printed test page... worked. Opened a text file and printed... worked. Opened an image and printed... worked. Too easy! I like the computer interface too. Marking this as solved (just pretend I added 10 smiley faces)

---

