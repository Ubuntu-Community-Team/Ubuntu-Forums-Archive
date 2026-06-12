---
title: "How to execute writing into terminal by icon"
date: 2008-07-14
forum: General Help
---

### Post by Terrum on 2008-07-14
Hi, Simple question.
How do you put writing into the terminal by double-clicking a shortcut on the desktop? (Like a windows batch file)

---

### Post by ghost_ryder35 on 2008-07-14
create a file like click
```

vi /home/username/Desktop/click

```
```

rdesktop -g 1111x1111 whatever.com
[I]save it
[/I]
```
```

chmod +x /home/username/click

```
save it to the desktop
double click it and click run in terminal

---

### Post by tuxxy on 2008-07-14
Hi,

To run a command place your chosen icon on the desktop as you wish, right click the icon goto properties > launcher and enter your chosen file or command.

---

### Post by Terrum on 2008-07-14
> **tuxxy said:**
> Hi,

To run an app place your chosen icon on the desktop as you wish, right click the icon goto properties > launcher and enter your chosen command.

Thanks, But i know how to create one. I just wanted to know how to make it opens up terminal and make it put writing in it like a windows batch file.

> **ghost_ryder35 said:**
> create a file like click
```

vi /home/username/Desktop/click

```
```

rdesktop -g 1111x1111 whatever.com
[I]save it
[/I]
```
```

chmod +x /home/username/click

```
save it to the desktop
double click it and click run in terminal

I'm pretty bad at unix/ubuntu, But i will try this and reply if this works or if it's how i want it. Thanks alot.

---

### Post by ghost_ryder35 on 2008-07-14
> **Terrum said:**
> Thanks, But i know how to create one. I just wanted to know how to make it opens up terminal and make it put writing in it like a windows batch file.



I'm pretty bad at unix/ubuntu, But i will try this and reply if this works or if it's how i want it. Thanks alot.
you probally wont like "vi" then
if you want to learn to use it follow the link in my sig.... otherwise you can replace the word "vi" with "gedit"

f.y.i what tuxxy said would work if you wanted to execute a command to say refernce your script (it would also get rid of the window prompt that asks if you want to run in terminal or display etc...)  all you would do is follow his directions and then for the command u would have a location like
```

/home/username/click

```

---

### Post by tuxxy on 2008-07-14
Thankyou ghost_ryder, you saved me explaining it :)

---

### Post by ghost_ryder35 on 2008-07-14
> **tuxxy said:**
> Thankyou ghost_ryder, you saved me explaining it :)
:guitar:

---

