---
title: "Boot.ini"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by loosescrew on 2009-07-25
Hello, I tried to install ubuntu via wubi. It ran all night and d/led @ 1.4G. This morning the d/l was complete and i had wubi reboot box to finish installation. After reboot comp went right back to xp. wubi never came back up.I believe that i should start the process over. I removed ubuntu from add'remove, but ubuntu still shows in boot.ini. Is there a tool to remove the boot.ini. I would like to start fresh. Thanks joe

---

### Post by yyylv on 2009-07-25
If the boot.ini entry is only thing left, then you could edit boot.ini file by notepad (and delete all remaining references to ubuntu)(it usually has 2 entries). (boot.ini is readonly and system, before editing remove readonly attribute, or you will not be able to save changes).

I installed ubuntu by wubi long time ago, so do not remember for sure, but documentation seems to suggest, that ubuntu installed by wubi will not be the default OS, you have to select it at startup.

---

### Post by loosescrew on 2009-07-25
yyylv, I appreciate the reply. I don't get any option to select ubuntu at startup. Comp goes straight to xp. I was under the impression that after reboot wubi would run again to finish installation. That doesn't happen. Ubuntu,is listed in add/remove, and in program files. What should I try next to boot into ubuntu ? Thanks Joe

---

### Post by yyylv on 2009-07-25
After reboot, there should be an option to start ubuntu, in windows boot menu. After selecting it (if it is possible), installation should continue.

BTW, if computer goes straight to XP, after installing ubuntu, what does boot.ini says?

(it should not go straight to XP, it should show boot menu (for 10 or 30 seconds)).

---

### Post by loosescrew on 2009-07-25
yyylv, boot.ini =C:\wubildr.mbr = "Ubuntu" I get no boot menu, comp goes straight to xp. Thanks Joe

---

### Post by yyylv on 2009-07-25
This cannot be content of actual boot.ini, for example mine is:
> [boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP c" /NOEXECUTE=OPTIN /FASTDETECT
c:\wubildr.mbr="Ubuntu"
This includes 3 OS (2 windows and ubuntu).

Also boot.ini starts with [boot loader] and has timeout=something (if it is 0, then boot menu is not shown).

---

### Post by loosescrew on 2009-07-25
Sorry yyylv, here is the full list. There is no timeout listed.

[boot loader]
default=multi(0)disk(0)rdick(0)partion(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partion(2)WINDOWS(2)="microsoft windows xp edition"/fastdetect/Noexecute=op
C:\Wubildr.mbr = "Ubuntu"
Thanks Joe

---

### Post by yyylv on 2009-07-25
If you want to remove ubuntu entry from boot.ini, then in this case it would be enough to delete row "C:\Wubildr.mbr = "Ubuntu"".

I do not remember encountering boot.ini without timeout entry, but it seems, that it is possible. (probably it continues as if it was timeout=0). Timeout value can also be changed without editing boot.ini file derectly, it is at My computer/properties (in right click menu) /advanced/Startup and recovery [settings]/Time to display list of operating systems.

---

### Post by loosescrew on 2009-07-25
yyylv, I added timeout=30 to boot.ini. I now get the option to boot into ubuntu. But I get the error message that (i believe)hall.dll.file missing unable to load windows. So i guess that i will uninstall and try again another time. Can you please tell me how to remove the ubuntu option from the boot.ini. Thanks for your help. Joe

---

### Post by yyylv on 2009-07-25
As i said, just delete row containing "C:\Wubildr.mbr = "Ubuntu"".

---

### Post by loosescrew on 2009-07-25
unfortunately yyylv, I don't know how to delete that line.Thanks Joe

---

### Post by yyylv on 2009-07-25
Open that file in notepad and delete (it is just text). Before editing, remove readonly file atribute (otherwise you will not be able to save changes).

---

### Post by loosescrew on 2009-07-25
ok, yyylv, I certainly appreciate your help. Tanks again Joe

---

### Post by loosescrew on 2009-07-25
Just a quick update. Being used to windows and the viruses associated with it.I'm in the habit of sending all my downloads to a folder (my documents) titled download. That way I can scan folder for any possible virus before installing any programs. I set my d\l to go directly into C\ and then set comp to give me a boot option at startup.Ubuntu, installed without any problems. I would like to thank yyylv,for all the help. I hope this may help some of the people out there getting the error message- Windows could not start because the following file is missing or corrupt <Windows Root>\system 32\hal.dll. Thanks again,Joe

---

