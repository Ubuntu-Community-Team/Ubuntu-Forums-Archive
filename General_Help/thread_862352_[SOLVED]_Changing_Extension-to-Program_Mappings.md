---
title: "[SOLVED] Changing Extension-to-Program Mappings"
date: 2008-07-17
forum: General Help
---

### Post by Jesdisciple on 2008-07-17
When I went to open a TXT file by double-clicking it, I expected to see it in Wine Notepad.  When Ubuntu said, in essence, "I don't know what to do with this," I went to Open with Other Application and specified notepad.exe (which Wine already knows as its territory).

Now Ubuntu wants to open *all* text-based files with Notepad, but I don't need that.  How can I make Gedit the default for extension-less text files and Notepad the default for TXT files?

Thanks!

P.S. I assume the distinction is necessary because of platform-dependent encodings and newlines?  I don't know because a related Wine problem makes Notepad not work anyway for now.

---

### Post by Vitamin-Carrot on 2008-07-17
I think you should have been able to open with open office wihout wine in the first place it should be a case of reaccosiating the file type to the application needed

---

### Post by Jesdisciple on 2008-07-18
> **Vitamin-Carrot said:**
> I think you should have been able to open with open office wihout wine in the first placeToo bad I didn't think of that.

> **Vitamin-Carrot said:**
> it should be a case of reaccosiating the file type to the application neededAnd how would I do that?

---

### Post by Potatoj316 on 2008-07-18
Why do you want to use wine notepad?

---

### Post by danwood76 on 2008-07-18
Yeah notepad is poor in comparisong to gedit.

Gedit will open and recognise the difference between DOS and UNIX line returns and so on so I would just use gedit for all text files.

Obviously if you go to open a UNIX text file in notepad it will come out funny as it doesnt understand single carriage returns but theres always wordpad in windows which is clever enough to understand UNIX text files.

---

### Post by Jesdisciple on 2008-07-18
> **Potatoj316 said:**
> Why do you want to use wine notepad?Because I thought it was the proper thing to use for TXT.

> **danwood76 said:**
> Yeah notepad is poor in comparisong to gedit.

Gedit will open and recognise the difference between DOS and UNIX line returns and so on so I would just use gedit for all text files.

Obviously if you go to open a UNIX text file in notepad it will come out funny as it doesnt understand single carriage returns but theres always wordpad in windows which is clever enough to understand UNIX text files.OK, thanks for the pointers.

Now can I please find out how to reassociate the file type like I asked at the first?

---

### Post by danwood76 on 2008-07-18
Sorry twas a little off topic.

If you right click the file you want to change and click properties, select the 'Open With' tab and select the default app you want to open it with.

---

### Post by Jesdisciple on 2008-07-18
Since I'd already done that, I went one step further to Open with Other Application and it worked.

BTW, that wasn't specifically to you Dan; both quoted comments frustrated me - yours a bit less than the other, which was redundant.

Thanks!

---

