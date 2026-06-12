---
title: "accessing windows files in ubunto"
date: 2008-10-12
forum: General Help
---

### Post by DLF44 on 2008-10-12
ive installed ubuntu so when i boot up i can choose between windows and ubunto. Im wondering if i can access the files in the windows half of the hardrive while in ubuntu? Or would i have to back them all up and re-install them in ubuntu.

---

### Post by igorel on 2008-10-12
You can access any files!
the files in partitation where your Windows is (and not Ubuntu) is on:
"Places" >> "Home Folder" >> "Media"
and the files in partitation where your Ubuntu is (and not Windows) is on:
"Places" >> "Home Folder" >> "File System" >> "Host"

:)

---

### Post by DLF44 on 2008-10-13
thanx very much

now my next question would be...
since i am able to boot either windows or ubuntu when i turn on my computer, how do i fully install ubuntu and not have to choose it each time?

and in doing so, does this get rid of windows completely?
and if so, can i export my files into ubuntu? or would i have to back them up and re intall them in ubuntu?

---

### Post by igorel on 2008-10-13
> **DLF44 said:**
> thanx very much

now my next question would be...
since i am able to boot either windows or ubuntu when i turn on my computer, how do i fully install ubuntu and not have to choose it each time?

and in doing so, does this get rid of windows completely?
and if so, can i export my files into ubuntu? or would i have to back them up and re intall them in ubuntu?

Well... Thoese questions are already answerd on this forum!
You just have to search for them :P

You can do anything that you askd...
1. You can just put ubuntu to load witouth choosing (but still have Windows)
2. You can get rid off Windows
3. You can back-ub files and again instal new OS (Just ubuntu Linux (no need for Wubi))

---

### Post by DLF44 on 2008-10-13
alright thanx for the help, 
i wasnt able to find in other forums.

so how would i go about booting ubuntu automatically without having to choose.

and then if i do that, does reorganizing my files in ubuntu affect them in windows?

---

### Post by Zakhafr on 2008-10-14
> **DLF44 said:**
> 
so how would i go about booting ubuntu automatically without having to choose.

It depends if you have Windows XP or Vista.
On Vista you have to download EasyBCD and use it.
On XP you edit your boot.ini to make Ubuntu the default O.S.

Search the forums with keywords EasyBCD or Boot.ini, and you'll most certainly find plenty details on how to do so.

For you second question, if in Ubuntu you copy/move/delete file on what you call "the windows part" of the system, of course you would see that from Windows. That's how it is possible to share files :)

If you stay "in the Ubuntu part", Windows will see nothing because does not know (natively) how to read Linux formated disks.

---

