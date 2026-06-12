---
title: "FL Studio 5 via WINE"
date: 2005-12-01
forum: General Help
---

### Post by detyabozhye on 2005-12-01
I finally got FL Studio 5 installed using the latest version of WINE, but it gives me an error that I can't really read when I try to launch it, I tried running it from the terminal and this is what I got:
```
fixme:wave:DSD_CreateSecondaryBuffer (0x7fe0aab8,0x7e0664c0,18008,0,0x7fe0b014,0x7fe0b124,0x7fe0aff0): stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
fixme:richedit:RichEditANSIWndProc EM_EXLIMITTEXT: stub
err:ntdll:RtlpWaitForCriticalSection section 0x7dffee3c "?" wait timed out in thread 000d, blocked by 0009, retrying (60 sec)

```
Any ideas?

---

### Post by detyabozhye on 2005-12-02
Ok, I got it working, but it eats my CPU and RAM like crazy!

---

### Post by arphe_el on 2005-12-02
Dear Detyabozhye,

Hello!

please share to us the procedures on how you install the wine? a step by step would be very helpful for us. 

Thank you and GODspeed!

---

### Post by detyabozhye on 2005-12-02
First I went to [http://winehq.org](http://winehq.org) , then I clicked on download, then ubuntu, then I added that line in there to my repositories, went in senaptic package manager, searched for wine, marked wine and libwine for installation, installed it, from the terminal ran wine, it did the initial setup, then I installed my apps, including FL Studio, I had to change it to emulate Windows 98 (by merging this file with the virtual registry: [http://www.kievinfo.com/2/ie6_overrides.reg](http://www.kievinfo.com/2/ie6_overrides.reg)) when I tried to install MSIE 6 SP1, then FL Studio would launch, but as I said before, it gives me problems.

---

