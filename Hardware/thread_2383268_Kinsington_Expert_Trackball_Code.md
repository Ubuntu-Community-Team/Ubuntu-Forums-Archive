---
title: "Kinsington Expert Trackball Code"
date: 2018-01-23
forum: Hardware
---

### Post by th1bill on 2018-01-23
Before I added Studio the left handed mouse option worked.  With Studio, no longer.  I'm running an HP with the AMD A4000 Processor and 12 gig of RAM.  I found some info at ZDNet.  I know the bottom left button 1, the left top is b2, lower right is b3 and the remaining is b4.  So the buttons I need to swap with xmodmap -e are 1 and 3, the two neared myself.  I cannot find an 3extentio to display xmodmap settings so I'm shooting in the dark But if I recall the ZD paper said I would be : xmodmap -e "pointer = 1 8 3 4 5 6 7 9 2"  This reverses my 1 & 3 but turns the 2 from being my middle button into reverse making the 4 button into forward.  The code I came up with is xmodmap -e “pointer = 3  8  1 4 5 6 7 9 2” , am I screwy?

xmodmap -e "pointer = 1 8 3 4 5 6 7 9 2"

xmodmap -e “pointer = 3 8 1 4 5 6 7 9 2”

In advance I want to say thank you to any that might answer.

---

