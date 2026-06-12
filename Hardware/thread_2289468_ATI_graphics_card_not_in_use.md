---
title: "ATI graphics card not in use"
date: 2015-08-04
forum: Hardware
---

### Post by liam25 on 2015-08-04
Inside "About this computer" , it says that my graphics is "Gallium 0.4 on AMD RV620" . 
Seriously don't know what's wrong here ...any help will be appreciated :razz:
I cant find and proprietary driver to use , how do i make my graphic card to work in ubuntu ?

Im using Ubuntu 15.04 , 
ATI Radeon HD 3400 Series
Intel® Core™2 Duo CPU P8400 @ 2.26GHz × 2

---

### Post by dino99 on 2015-08-04
you need to use the open source driver, as that model is too old 

[http://ubuntuforums.org/showthread.php?t=2184451](http://ubuntuforums.org/showthread.php?t=2184451)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by howefield on 2015-08-04
You are likely confined to the open source driver for that card, I might be misremembering but I think anything older than a 5000 series card would not be supported with proprietary drivers in a current version of Ubuntu.

[http://ubuntuforums.org/showthread.php?t=2269080](http://ubuntuforums.org/showthread.php?t=2269080)

---

### Post by Mark Phelps on 2015-08-04
howefield is correct -- AMD dropped support for its HD 2x/3x/4x-series cards years ago.  The last Ubuntu version that had such support was 12.04, and even 12.04.1 was too new for that support.

---

### Post by Yellow Pasque on 2015-08-04
> Seriously don't know what's wrong here

Nothing. The output is correct. Do you actually have any graphics issue(s) or are you just confused by the name?

---

### Post by liam25 on 2015-08-04
> **Temüjin said:**
> Nothing. The output is correct. Do you actually have any graphics issue(s) or are you just confused by the name?

Yea , im just confused by the name .
Everything works fine . Thanks for the reply man ~

---

### Post by howefield on 2015-08-05
> **liam25 said:**
> Yea , im just confused by the name .

Just the name of the open source drivers.

---

### Post by coldraven on 2015-08-05
You are lucky, support for my ATI card stopped after Ubuntu 10.04!

---

### Post by Yellow Pasque on 2015-08-05
> **coldraven said:**
> You are lucky, support for my ATI card stopped after Ubuntu 10.04!

Sighhh... Support was not stopped. Catalyst support was dropped, but it's not a big deal since the open-source driver is generally better for older cards.

---

### Post by poorguy on 2015-08-09
yeah i have a sapphire radeon hd 3870 x2 that i can't get proprietary driver for which isn't good however the open source driver does seem to work pretty well.
i do wish that ati would support their graphics cards better in linux but they just act as though they could care less. which is why i won't buy another ati graphics product.
at least nvidia supports their graphics cards with a proprietary driver if the open source doesn't work right.
i always run the open source driver 1st and if i like it then i will stick with it.

the poorguy

---

### Post by Yellow Pasque on 2015-08-09
> i do wish that ati would support their graphics cards better in linux but they just act as though they could care less.

False. AMD/ATI funds open-source development and hires community devs. 
Anyway... I'm unsubscribing from this thread and I hope it gets closed or moved to recurring discussions soon. The OP's "problem" has been resolved.

---

### Post by QIII on 2015-08-09
Since this was solved and there is no need for further FUD, as Temüjin correctly points out:  closed.

---

