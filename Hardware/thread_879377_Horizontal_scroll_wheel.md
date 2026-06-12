---
title: "Horizontal scroll wheel"
date: 2008-08-03
forum: Hardware
---

### Post by niglch on 2008-08-03
I just got a new USB mouse made by General Electric which seems to be working well out of the box. I'm only having a couple issues. The first is that the horizontal scroll wheel doesn't seem to be doing anything and it's something I would really like to have for editing spreadsheets or text files. Also, the forward and back buttons work in Firefox but are reversed (the forward button goes back and the back button goes forward). Is there any way to enable these mouse functions?

---

### Post by niglch on 2008-08-04
I tried typing "xev | grep button" to test my mouse. It seems that the vertical scroll wheel isn't being picked up. The left, middle, and right buttons are detected as buttons 1, 2, and 3, the vertical scroll wheel is detected as buttons 4 and 5, and the two thumb buttons are detected as buttons 8 and 9. I guess the vertical scroll wheel is supposed to be 6 and 7 but nothing happens when I move the wheel in the event tester.

---

