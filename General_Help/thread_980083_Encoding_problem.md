---
title: "Encoding problem"
date: 2008-11-12
forum: General Help
---

### Post by davidmd on 2008-11-12
Hi everyone
I have just installed 8.10, I had 8.04 but I wanted a new a fresh instalation, so I backed up everything and installed the new version. After that I installed Eclipse to work on a project set the encoding to ISO-8859-1 and the accents in Strings show up as normal, the problem was when I went to Firefox and the accents appear as a "?", I said ok let's check the encoding.... every was ok in Eclipse, so why that happened?. Until now I've done a search trying to change the default enconding of my ubuntu thinking that was the problem, I changed the file /etc/default/locale, there was something like es_CO.UTF-8 and changed to es_CO as I read some other place, I did the same with /etc/environment, then reboot and something happened because I had my ubuntu in Spanish and after that it was in English but the files said it was Spanish, now I don't know what to do.

The question is: how do I change the enconding of ubuntu from utf-8 to iso-8859-1 without changing the language of the system? I'm guessing the problem with eclipse is with the system encoding or something like that.

The output of the command: locale -a is
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
es_AR.utf8
es_BO.utf8
es_CL.utf8
es_CO.utf8
es_CR.utf8
es_DO.utf8
es_EC.utf8
es_ES.utf8
es_GT.utf8
es_HN.utf8
es_MX.utf8
es_NI.utf8
es_PA.utf8
es_PE.utf8
es_PR.utf8
es_PY.utf8
es_SV.utf8
es_US.utf8
es_UY.utf8
es_VE.utf8


Any help is really appreciated

Thanks

PS: I don't write to much in English, I hope you understood me

---

