---
title: "Trying to set up netgear WG511 pcmia card with Acer TravelMate 220"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by Bhante Santi on 2006-04-09
Hi, I'm trying to set up netgear WG511 pcmia card with Acer TravelMate 220.

I'm trying to follow the How To Page:

[http://www.ubuntuforums.org/showthread.php?t=156228&highlight=netgear+WG511](http://www.ubuntuforums.org/showthread.php?t=156228&highlight=netgear+WG511)

But I don't understand this:

[INDENT]Create a new folder in your home folder, something like WG511 would be good.

Pop the Netgear Windows driver CD into the drive and navigate to the Driver\WINXP folder, select the four files in the folder, copy and paste the files into your new WG511 folder.

[B]Go back to your terminal prompt and move to your home directory:


Code:
cd /home/user$/WG511
Where user$ is your user name.[/B]

Code:
sudo ndiswrapper -i netwg511.inf[/INDENT]

I've created a new folder called WG511 on the desktop and put the 5 files I found in BPIK0007>drivers>WG511>driver into it - there is one called WG511v2.INF, which sounds like what I read somewhere else that I'm supposed to be looking for, right?

This is very basic but I can't actually get the file to run in the terminal.

Why does it say 'cd' in the How To page when I'm supposed to have put the file in a folder in my 'home directory' - that means on the desktop right? I've also tried things like:

home/ desktop/ WG511

and that doesn't work either, what am I doing wrong?

This is my first hour ever trying to use Ubuntu, my only previous experience with programming lingo was with LaTex, and that was a painful struggle.

Can anyone help?

Thankyou,

Bhante Santi.

---

### Post by Bhante Santi on 2006-04-09
Hi again,

well I just found the directory with Desktop/WG511, I'll go back to the How To page and keep trying, I think I may well be back again with more questions soon!

BFN,

Bhante Santi.

---

### Post by Bhante Santi on 2006-04-10
[QUOTE=Bhante Santi]Hi again,

well I just found the directory with Desktop/WG511, I'll go back to the How To page and keep trying, I think I may well be back again with more questions soon!

BFN,

Bhante Santi.[/QUOTE]

OK, next problem, I've tried installing netwg511.inf and netwg511v2.inf and both of them say 'invalid driver', now what?

It also says:

WARNING: /etc/modprobe.d/blacklist line 3: ignoring bad line starting with 'blaclist'
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

Following a previous How To page, the wrong one I found out, I tried adding three lines that sounded like 'blacklist' etc. but I've tried recopying and pasting the original from the CD and it still doesn't work.

Can anyone help?

Thanks, Bhante Santi.

---

