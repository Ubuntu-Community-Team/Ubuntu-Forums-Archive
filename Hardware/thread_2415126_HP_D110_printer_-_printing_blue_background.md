---
title: "HP D110 printer - printing blue background"
date: 2019-03-20
forum: Hardware
---

### Post by pizzipie on 2019-03-20
Hi 

I run Ubuntu 16.04 on my wife's Dell E6420 laptop, no windows. HP D110 printer.

Recently I installed 'digikam' on this computer. I could not read the  tool tips as the foreground and background color combination made the  text invisible. I then ran 'digikam configuration' and set Miscelaneous  -> Widget style to 'Cleanlooks'. This fixed that problem now I can  read the tool tips.

I believe, at this time, I also was fiddling around with the Firefox settings trying to set font size.

I any case when I now use the printer it prints with a normal black foreground but a** blue** background.

I also have my own Dell E6510 laptop running Ubuntu 16.04, no windows,  same HP D110 printer. I did the digikam configuration and Firefox  fiddling also, at the same time.

When I use the printer with this laptop it operates normally printing with a normal black foreground with white background.

Help getting this resolved is appreciated.

R

---

### Post by jeremy31 on 2019-03-20
Try installing updates and see if that fixes the issue.  It is caused by a faulty update to ghostscript [https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1817308](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/1817308)

---

### Post by pizzipie on 2019-03-20
[SOLVED]

Thanks.

I read the contents of the URL above and updated  (with Synaptic) ghostscript 26 on my wife's Dell  E6420 computer.

Works fine now.

---

