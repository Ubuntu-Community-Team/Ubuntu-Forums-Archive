---
title: "error when checking disk integrity and running"
date: 2008-09-24
forum: General Help
---

### Post by klambert on 2008-09-24
i get two different error messages the first when checking the the disk integrity it says 
ata1.01:revalidation failed (errno=-5)

then it says something about iprpoll or something, i couldnt get the whole thing it moved on too fast to repearting that same message,  and then when i tryed to run the OS without installing it said the same thing...help me pleeeeeeeeease im sooo anxious to get this up and working

irq 17: nobody cared (try booting with the irqpoll" option) handlers:
...
...
...
Disabling IRQ #17

that was wat it gave me after repeating the first thing a few times

---

### Post by nikgare on 2008-09-24
Accordingto this 
[http://john-hunt.com/2008/07/20/revalidation-failed-errorno-5/](http://john-hunt.com/2008/07/20/revalidation-failed-errorno-5/)

adding **all_generic_ide parameter** to the boot  options may help you

---

### Post by klambert on 2008-09-24
where do i add this, i dont know where my boot options are

---

### Post by klambert on 2008-09-24
still need some help, have no clue what to do

---

### Post by klambert on 2008-09-25
up

---

### Post by nikgare on 2008-09-25
What does "up" mean in this context?

You can either insert the line in the relavent place in the file **/boot/grub/menu.list** or better still, when you machine boots up go into the grub menu and edit the options there.

---

### Post by klambert on 2008-09-26
up is just to get it back onto a reasonable page, my post made it all the way down to page 10 and when i start getting posts that far down i dont seem to get answers.

ok well i really dont know how to get into the grub menu.  im sorry im a total noob at this, but i will play with it some more tomorrow i dont really have time right now, i have a test in 6 hours, and a paper due in 7 hours....so im stressed for time

---

