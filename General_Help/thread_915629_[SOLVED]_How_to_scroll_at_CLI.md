---
title: "[SOLVED] How to scroll at CLI?"
date: 2008-09-10
forum: General Help
---

### Post by lakersforce on 2008-09-10
How do you scroll at CLI (bash)? I find that I often find myself having more text on screen that I can read...how do I read the text that has gone past my screen real estate?

please note I wrote CLI and _not_ GUI!

---

### Post by jerome1232 on 2008-09-10
Pipe the output to more or less ie

```
cat ~/reallybigtextfile | less
sudo ./program\ with\ a\ lot\ of\ output | less
```

---

### Post by lakersforce on 2008-09-10
Thanks. I know of more and less.

I was thinking for example when I use ls and there are a lot of files in directory.

---

### Post by NilsHG on 2008-09-10
press shift + page up or page down to scroll up and down in terminal

---

### Post by lakersforce on 2008-09-10
Great. Problem solved!

---

### Post by hyper_ch on 2008-09-10
(1) install screen

(2) run screen

(3) for scrolling then use:  ctrl-a  +  esc

(4) scoll with the arrow keys

(5) exit scrolling mode with pressing "esc" again

--> a short introduction to screen:  [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by lakersforce on 2008-09-10
I was about to ask how I can look at _all_ the files, but *screen* solved my problem.

Thanks.

---

