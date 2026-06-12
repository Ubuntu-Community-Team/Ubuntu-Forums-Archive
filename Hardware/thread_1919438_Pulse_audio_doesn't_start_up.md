---
title: "Pulse audio doesn't start up"
date: 2012-02-02
forum: Hardware
---

### Post by bobman321123 on 2012-02-02
Hello (:
I used a code recently to turn off pulse audio, but I think it deleted the file that starts up pulseaudio when I log in. Now I have to turn it on with ```
pulseaudio -D
``` every time I log in. 
Is there any way I can fix this?
I'm kind of new to this
Thank you (:

---

### Post by jerrrys on 2012-02-04
Should just be able to make it part of your startup software (located in dash).

---

### Post by bobman321123 on 2012-02-04
jerrrys, 
I added the command "pulseaudio -D" to my startup applications, and it failed. 
Anything else I can do?

---

### Post by jerrrys on 2012-02-04
pulseaudio --start

---

### Post by bobman321123 on 2012-02-05
That worked! :) Thank you so much!

---

