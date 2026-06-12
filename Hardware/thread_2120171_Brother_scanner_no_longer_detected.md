---
title: "Brother scanner no longer detected"
date: 2013-02-25
forum: Hardware
---

### Post by newb85 on 2013-02-25
I'm a little baffled with this problem.  I had my Brother MFC-3360C (ancient, I know...) all set up and working, including scanning for normal users and the scan-key-tool.  It's been a couple months since I used it to scan something.  Now, it seems my machine no longer seems to recognize the scanner.  Whereas XSane and Simple Scan let me choose between the Brother and a wireless HP, now they both default to the HP.

It's not a matter of connection, because it still prints just fine.  I've checked that the libsane rules file still includes the line for Brothers, and removed and reinstalled the scanner and skey drivers.  Anyone know a good way to troubleshoot this?

---

### Post by offgridguy on 2013-02-25
Just wondering, have you done an update in the meantime?

---

### Post by newb85 on 2013-02-25
Plenty of updates, but no upgrade.

---

### Post by offgridguy on 2013-02-25
I know I have read some threads with this issue, still searching.

---

### Post by newb85 on 2013-04-29
I've found a solution, an I'm sorry to say, it's one I've found before.  If only my memory worked a little better...

It's on [Brother's scanner FAQ page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html"), in the section titled "I'm using Ubuntu 11.10 or higher. I cannot scan from my Brother Machine."

It looks like this only applies to 64-bit systems.  Also, it looks like installing certain updates reverts this fix (so it has to be fixed again).  A simple bash script makes re-fixing much quicker.  

I'm considering making that script a startup process (so when future updates break it, a simple log-out log-in will fix it).  Not sure if it's possible to make a command requiring sudo into a startup process, though.

---

### Post by kurt18947 on 2013-04-29
It's good to know that updates can undo that fix, I'd never have guessed that.  Thank you.  This is not exclusively a Brother issue, I've seen the same problem and solution applied to other brand machines.  One site speculated that the problem arose when using alien to convert .rpm to .deb.  And yes, it's only 64 bit.

---

