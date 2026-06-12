---
title: "Postfix+Spamassassin+ClamAV"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by actigner on 2009-03-07
I am attempting to build an Ubuntu 8.10 server that will employ Postfix as the mail component plus Spamassassin plus ClamAV. I have searched the web for solutions and tried every combination possible but cannot get the email scanning of viruses to work. I can get Spamassassin to function properly but when I add the parameters I've found on the web for ClamAV it causes Postfix to stop sending mail until I remove them. I've also used the testfiles ClamAV supplies to test the functionality. These files are picked up, however, when I do a full system scan using ClamAV so I know they are valid infections. I am also running a version of Postfix (included with ubuntu 8.10) that supposedly has dropped it's requirement to have Amavis included in the mix.

If anyone has a workable solution or documented procedure for my configuration I would appreciate it.

---

