---
title: "LaserJet 5L prints a row of garbage on each job"
date: 2008-12-02
forum: General Help
---

### Post by aperomsik on 2008-12-02
Our LaserJet 5L was working fine with Hardy and it was also doing fine with Intrepid until some recent updates. Now the first page of every job has some garbage text on top. Is it just me or do others also have this problem? Any workarounds?

---

### Post by taurus on 2008-12-02
What if you just delete it and reinstall it again?  Would that fix the problem?

---

### Post by aperomsik on 2008-12-03
It fixes the immediate problem -- thanks! -- but the real question is why an update would break a printer queue that was working fine for years. Will it happen again next time there are CUPS updates?

---

### Post by cyrus_the_virus on 2008-12-14
Hi,

I have a similar problem with a HP Laserjet 5. I have had this problem since I started using linux (suse 10.0 to 10.3 and ubuntu 7.04 to 8.10) (it works fine in windows).

With most documents I get a bunch strange characters on top. However, with some documents I get nothing but garbage (so nothing recognisable from the document I wanted to print).

I have installed the printer as a "App Socket / JetDirect" device. De uri I'm using is:
socket://ip-address:2501
For some reason I have to use port 2501 and not the standard port 9100 (I check with a port scanner, no port 9100 is open on my printer)
I tried with all PPD files in ubuntu 8.10.

aperomsik, how did you install the printer? What uri/port and PPD file are you using?

Thanks,
Marty

---

### Post by aperomsik on 2008-12-17
I'm using the one that is specified as "Recommended" in the setup dialog... if I remember correctly it was foomatic+ljet4 .

---

