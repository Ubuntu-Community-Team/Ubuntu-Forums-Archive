---
title: "dual processor check"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by aliyanage on 2006-10-25
Hi all,

I got an acer aspire 9410 laptop with an 1.60GHz dual processor and would like to find out whether it recognizes the dual processor and whether it works properly is there any command or a way that I can make sure everything is running right?

thanks for your help
aliyanage

---

### Post by Aberrix on 2006-10-25
what kernel are you currently using?

copy and paste in the results of this;

```
uname -a
```

---

### Post by aliyanage on 2006-10-25
Linux ubuntu01 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686 GNU/Linux

this was the result of uname -a

---

### Post by Aberrix on 2006-10-25
It appears you are using the proper kernel and have [SMP]("http://en.wikipedia.org/wiki/Symmetric_multiprocessing"). So you should be good to go as far as having both cores working for you.

---

### Post by aliyanage on 2006-10-25
okay thank you very much, just one more question. I just installed conky and saw that at the display it shows the CPU as 800MHz but before it was 1.60, any clue why this is, shouldn't it show me 1.60?

---

### Post by Aberrix on 2006-10-25
I would ask in [this thread]("http://ubuntuforums.org/showthread.php?t=205865") about conky questions.

However, what does your .conkyrc look like? I might* be able to help.

---

### Post by aliyanage on 2006-10-25
its the same setup as in the thread that you showed me, looks exactly the same and I used the same thread to configure it...

---

### Post by Aberrix on 2006-10-25
Well, I couldn't tell you why it isn't working. I know some other people have had some problems with the freq as well so *shrugs*. I believe it has to the with the variables conky uses and how freq does not have a variable argument.

Just remember with a dual core processor that in your conky you should specify cpu1 or cpu2 to distinguish between the cores. Kind of like this;

```
Core 1: ${cpu cpu1}% ${cpubar cpu1}
${cpugraph cpu1 000000 000000}
Core 2: ${cpu cpu2}% ${cpubar cpu2}
${cpugraph cpu2 000000 000000}
```

[here]("http://conky.sourceforge.net/variables.html") is a link to the conky variables also. Hope that helps some.

---

### Post by aliyanage on 2006-10-25
alright, hey thanks for your help really appreciate your time investment!!!

---

### Post by Aberrix on 2006-10-25
no problem :)

---

