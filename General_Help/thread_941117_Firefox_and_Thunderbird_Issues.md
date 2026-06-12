---
title: "Firefox and Thunderbird Issues"
date: 2008-10-07
forum: General Help
---

### Post by jdoge13 on 2008-10-07
I updated my computer this morning (as frequently happens on ubuntu) and noticed no changes to thunderbird or firefox.  However, when I came back this afternoon I noticed that my firefox now doesn't display text and my thunderbird will not open for more than five seconds without closing itself (it seems to operate fine while its open though: it retrieves emails and shows them as being new).  I've tried reinstalling both, and I've tried uninstalling both and reinstalling both.  Any suggestions?  I'm running ubuntu 8.04, Firefox 3.0.3, and my thunderbird doesn't stay open long enough for me to check.

---

### Post by christianvaldes on 2008-10-07
run them from a terminal
what are the errors?

---

### Post by jdoge13 on 2008-10-07
I'm sorry, I'm not a linux power user.  How exactly do I do that?

---

### Post by christianvaldes on 2008-10-07
Applications  -->  Accessoriess ---  Terminal

type in 

firefox

you can try the same for...

thunderbird  in a different terminal console

hope this helps

---

### Post by jdoge13 on 2008-10-07
I fixed the problems I had a problem with msttcorefonts.  Thanks a bunch!

---

### Post by christianvaldes on 2008-10-07
Where did you configure that?

Did it tell you in the console or did you configure it within the program?

---

### Post by jdoge13 on 2008-10-10
I went through the terminal and it game me this error:
(gecko:14232): Pango-WARNING **: failed to create cairo scaled font, expect ugly output.  the offending font is 'Tahome Bold 9.599609373'

and the same again except with Segoe UI

I am again having the same issue, however reinstalling msttcorefonts package is no longer solving the issue.  I don't even have the tahoma font, why is it looking for that?

I've tried putting the tahoma font into my /fonts/msttcorefonts/ directory, however it claims that I "don't have permission" to do that.

---

### Post by jdoge13 on 2008-10-17
Update:  I figured out that I have to copy the fonts Tahoma and Segoe UI back into my fonts directory everytime I update my computer(the weird part is they have to have a different capitalization every time I do it) or even open synaptic package manager.  Any suggestions?

---

### Post by jdoge13 on 2008-10-22
I found a solution to this problem for anybody else having it.  I copied fonts from my windows computer over to my linux computer, however the files were configured not to give any programs access to them.  So I changed the permissions of the files and copied them back over and the problem fixed itself.

---

