---
title: "problem with synaptic package manager"
date: 2008-08-12
forum: General Help
---

### Post by rohas on 2008-08-12
Hi everyone
i have one problem with synaptic package manager as also with update manager. The problem occurred after i run update manager and during the download of the packages my laptop turned off (battery). After i plugged it to a/c update manager refuses to open and when i opened synaptic package manager the following error came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i run sudo dpkg --configure -a from terminal and i had the following error

dpkg: parse error, in file `/var/lib/dpkg/updates/0175' near line 1:
 field name `/usr/share/fonts/truetype/thai/Garuda-Oblique.ttf' must be followed by colon


any ideas ??

Thanks in advance

---

### Post by SunnyRabbiera on 2008-08-12
That is unusual indeed.
Try a restart?

---

### Post by rohas on 2008-08-12
of course...i tried this twice :(
no luck

---

### Post by Mgiacchetti on 2008-08-12
> **rohas said:**
> Hi everyone
i have one problem with synaptic package manager as also with update manager. The problem occurred after i run update manager and during the download of the packages my laptop turned off (battery). After i plugged it to a/c update manager refuses to open and when i opened synaptic package manager the following error came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i run sudo dpkg --configure -a from terminal and i had the following error

dpkg: parse error, in file `/var/lib/dpkg/updates/0175' near line 1:
 field name `/usr/share/fonts/truetype/thai/Garuda-Oblique.ttf' must be followed by colon


any ideas ??

Thanks in advance

i would 
```

sudo cp /var/lib/dpkg/updates/0175 ~
gksudo gedit /var/lib/dpkg/updates/0175
```
and add a colon  :  to that line save and try again.

if it dont work just copy it back from ~ to updates

---

### Post by rohas on 2008-08-12
fix the colon problem and now the problem is

dpkg: parse error, in file '/var/lib/dpkg/updates/0175' near line 4: missing package name


is there a way to "remove" all the updates that i have done during my laptop went off from battery so that system doesn't know that updates must be installed!

---

### Post by rohas on 2008-08-13
any ideas for clearing the updates that are downloaded and are corrupted ?

---

### Post by Mgiacchetti on 2008-08-13
have you looked at line 4 to see what it may be talking about??  if it seems ok, comment it out?

#

---

### Post by rohas on 2008-08-13
i have the following in 0175
```

/usr/share/fonts/truetype/thai/Garuda-Oblique.ttf: --FontName Garuda-Oblique --Family Garuda --Encoding Unicode --Location English Thai --Charset ISO8859-1 ISO8859-11 TIS620 ISO10646-1 --UniCharset ISO8859-1 ISO8859-11 TIS620 --GeneralFamily SansSerif --Weight Medium --Width Variable --Shape NoSerif Oblique --Foundry TLWG --Priority 20
/usr/share/fonts/truetype/thai/Purisa.ttf: --FontName Purisa --Family Purisa --Encoding Unicode --Location English Thai --Charset ISO8859-11 TIS620 ISO10646-1 --UniCharset ISO8859-11 TIS620 --GeneralFamily SansSerif --Weight Medium --Width Variable --Shape Upright --Foundry TLWG --Priority 20
/usr/share/fonts/truetype/ttf-mgopen/MgOpenCosmeticaBold.ttf: --Family MgOpenCosmetica --FontName MgOpenCosmetica-Bold --Encoding Unicode --Location English --Charset ISO10646-1 --UniCharset ISO8859-1 ISO8859-7 --Direction Horizontal --GeneralFamily SansSerif --Weight Bold --Width Variable --Shape NoSerif Upright --F
```

---

### Post by Mgiacchetti on 2008-08-13
so there is no line 4?

I would go to the end of line three and hold the Delete key (not backspace) then save and try

---

### Post by rohas on 2008-08-13
it didn't help :((
it's end of file at that point.
i believe only solution is to erase all updates and told update manager to download them again...but i don't know what to delete so that update manager "thinks" that no update is downloaded.

---

