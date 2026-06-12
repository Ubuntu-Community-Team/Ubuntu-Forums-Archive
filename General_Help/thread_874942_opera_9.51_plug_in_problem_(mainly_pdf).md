---
title: "opera 9.51 plug in problem (mainly pdf)"
date: 2008-07-30
forum: General Help
---

### Post by Claus7 on 2008-07-30
Hello,

I experienced a lot of problems with pdf documents using the opera web browser mainly in gutsy. I could not open pdf documents. I faced errors and the result was either a grey screen or a white screen with unrecognised characters.

In order to solve this problem I did the following:
i) I opened a terminal and typed :
```
locate nppdf.so
```
The result was :
> [COLOR="DarkRed"]/opt/Adobe/Reader8/Browser/intellinux/nppdf.so[/COLOR]
/usr/lib/mozilla/plugins/nppdf.so
[COLOR="#8b0000"]/usr/lib/firefox/plugins/nppdf.so[/COLOR]
/root/.mozilla/plugins/nppdf.so
ii)I went to Tools->Preferences->Advanced->Content->Plug-in Options...
There I clicked the "path new", deleting all the other paths. I chose two paths, the ones I have with colour above. After that I was able to open any pdf file.
In Tools->Preferences->Advanced->Downloads, if I choose "application pdf" and then "Edit" I get :
Use plug-in
/opt/Adobe/Reader8/Browser/intellinux/nppdf.so

EDIT: With everyday use I found out that using in application pdf the acroread plugin and hitting the refresh button the pdfs open better.

Regards!

---

