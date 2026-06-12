---
title: "Multitouch mouse clicks on the ASUS 1000HE"
date: 2009-10-28
forum: Hardware
---

### Post by portach king on 2009-10-28
Hi guys,
I'm using the Ubuntu NBR 9.10 RC on the Asus 1000HE and absolutely love it.

I have one gripe though. Previously when I would tap the touchpad with two fingers this would act like the middle button of a mouse being clicked (extremely handy opening new tabs in firefox, etc) and tapping with three fingers behaved like right-click. 

I found this to be very intuitive and easy to use, but in 9.10 these have been reversed (ie. 3 finger tap is middle click) which I find confusing and, to be frank, annoying to use. 

How can I change this back? I've installed gsynaptics, but the option isn't there. Would love some help on this issue.

:)

---

### Post by portach king on 2009-10-29
*Bump*

:)

---

### Post by rx8saxman on 2009-10-30
Enter this into the terminal and your multitap buttons should be back to normal.  I had the same issue and it worked for me:
```
synclient TapButton2=2 TapButton3=3
```

---

