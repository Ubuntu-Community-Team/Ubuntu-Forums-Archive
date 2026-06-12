---
title: "Monitor + printing problem"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by MikkyX on 2007-09-27
Hi all,
Posted these in another thread but I think they got a bit lost being in an older thread 'n all so I hope you don't mind me starting a new thread in a more relevant location. Got a couple of problems still to iron out with my migration to Ubuntu:

1) When I log in my login screen is a little corrupt - I can still see what I'm doing but I think it's trying to display it in a resolution my monitor shouldn't support. This started when I installed the special ATI driver (fglrx?) in order for my widescreen monitor's 1440 x 900 resolution to be installed. Once I have logged in it switches no problem. When I look in the Restricted Drivers manager, there's no tickbox next to the ATI driver in question - is this normal?

2) My brother has a HP Deskjet F300 AIO connected to his Windows XP box and shared. I can connect to and install the printer from my machine via setting it up as a Samba shared printer, and Ubuntu configures it to use the hpjis driver, but when I send a document through to it (including the test page) the printer sits there as if it's about to start printing but never actually does. Any suggestions? I print a lot of letters so this is quite an important point to fix if possible - if not, I can leave them on the network drive (I got read-write working!) and he can print them for me.

---

### Post by MikkyX on 2007-09-28
Updating my own post, but I found a fix for problem one - I ran this command:

aticonfig --resolution 0,1440x900

(or something like that anyway) - and GDM now shows at the correct size.

Still no joy printing though - anyone got any pointers to offer here?

---

### Post by mikeize on 2007-09-28
I also cannot print!  Seems to be good, shows the job as pending, but never prints...  and I can't cancel it either!  Even after rebooting.  This is a fresh install of gutsy beta, btw, but I had the same problem with one of the alpha releases.  Any thoughts?  o yeah, it's a hp psc 1350, if that makes any difference.

-mike

---

### Post by dodgy_pro on 2007-09-30
I had exactly the same problem till 3 minutes ago. Really can't understand how I solved it. I tried twice unintalling and reinstallind the printer (HP Deskjet 5940) and at the third time it started printing! I used the tool found at System --> Administration --> Printing. Try also playing with having the printer on and off.

If somebody figures out what exactly the problem is, please make a reference...

Maybe it is a matter of luck, but it _is_ a bug...

---

### Post by MikkyX on 2007-10-01
dodgy_pro, was that a printer in the same situation as mine? (networked via Samba on a Windows PC)

---

### Post by dodgy_pro on 2007-10-01
> **MikkyX said:**
> dodgy_pro, was that a printer in the same situation as mine? (networked via Samba on a Windows PC)

No, I am sorry. I answered to mikeize's post, as there is indeed such a problem. As far as yours is concerned, I have also heard about it, but know no solution. 

Our problem seems to be linked with the automated installation of printers coming with Gutsy, where the device takes a wrong Device URI. When I installed it "manually", the system gave the printer a URI like "usb://HP/Deskjet....", instead of "hp:/usb/Deskjet...." before, which seams quite strange (and indeed it wouldn't work).

---

