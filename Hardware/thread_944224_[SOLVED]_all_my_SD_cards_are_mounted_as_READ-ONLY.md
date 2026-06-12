---
title: "[SOLVED] all my SD cards are mounted as READ-ONLY"
date: 2008-10-11
forum: Hardware
---

### Post by Dan_Dranath999 on 2008-10-11
i can't write or erase anything in my SD cards anymore! (But can do it using my camera)

I have read in other threads and other forums, it may be a kernel bug... ¿Somebody knows something about it? 

(they are FAT32, so i suppose "changing the permissions" wouldn't help)

---

### Post by Dan_Dranath999 on 2008-10-11
bleeeh-ho!

(I used my camera -Nikon D80- to format the SD Cards. They still are mounted as read-only in both Ubuntu and Windows XP. They just stopped working normal last week)

---

### Post by Sef on 2008-10-12
1) What Ubuntu version are you using?

2) Does the card have a lock on it?

---

### Post by maestrobwh1 on 2008-10-12
Actually I just ran into this as well... so I took the card out of a generic SD card reader, and put in another (kingston) and it became rw in the kinston card reader... go figure.  I have had this happen before and just resorted to reformatting the card, but fortunately I tried this first this time around.

---

### Post by Dan_Dranath999 on 2008-10-12
> **Sef said:**
> 1) What Ubuntu version are you using?

Hardy.

> **Sef said:**
> 2) Does the card have a lock on it?

Nope. They ALL(3 of them) have the lock off. (different brand: PNY, Verbatim and something called pq1)

---

### Post by Dan_Dranath999 on 2008-10-13
news:

I took the SD cards to work. Used an USB Card Reader to check them in Windows XP first. No issues whatsoever. I could write, copy, delete all i wanted, and format them again. Then i mount them in Xubuntu (thru VMWare)

No write/read problems.

I came home. I mount them with my Card Reader.

Read-Only again. (you can see the **ro** option in properties)

Then i plugged an MemoryStick card i had in one of my cameras.

Write enabled on that one. Everything OK.  (rw shows up in properties)

¿What the hell is wrong with my card reader? ¿Do i need to manually change the SD device default mount options? ¿Why suddendly those mount options changed themselves?

---

### Post by Dan_Dranath999 on 2008-10-14
cowabunga!

---

### Post by Dan_Dranath999 on 2008-10-27
got me a new'n'smaller multicard reader for 5 euros. Works better but now i have 1 instead of 3 front-panel USB ports.

The cards work fine, so i suppose my problem was cheap hardware.

---

