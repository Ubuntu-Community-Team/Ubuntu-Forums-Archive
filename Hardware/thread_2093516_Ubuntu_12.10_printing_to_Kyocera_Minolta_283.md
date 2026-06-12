---
title: "Ubuntu 12.10 printing to Kyocera Minolta 283"
date: 2012-12-11
forum: Hardware
---

### Post by pvanonselen on 2012-12-11
I have a problem printing from my Ubuntu 12.10 install.

Initially printing to a Minolta 283 bizhub hanged the printer for some reason.

I used the linux driver suppied by Konica Minolta.

It workd in 11.10. 

Now I tried to install previous cups 1.5.4 instead. I removed cups 1.6 and manually built 1.5.4 from sources. This broke cups completely as it looked for folders that does not exist any more.

So removed cups and tried to install 1.6 again.

Now I am getting this error:
Unsupported format "application/vnd.cups-banner".

From the cups error log:
Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/KONICA-MINOLTA-bizhub-283) from localhost

How can I fix my cups? Even my printers that was working now does not work.

From forums seems this is an issue with CUPS 1.6. 

By manually installing 1.5.3 by building the source in Ubuntu 12.10 I broke all printing.  How do I reinstall 1.6 from scratch?

---

### Post by kruppe on 2013-01-22
Same thing happened here, system update killed printer. Any help appreciated.

---

