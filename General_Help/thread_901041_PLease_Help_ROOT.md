---
title: "PLease Help ROOT"
date: 2008-08-26
forum: General Help
---

### Post by enzodad on 2008-08-26
Hi i finaly ditched Vista :) I installed Las\test version ubuntu.
LOVE IT. but im not a linux expert yet. I cant use apt-get.. also when i typ in sudo wont ask for password and when it does just says incorrect. Is there a way to make it so there is only 1 user(me) as permen root? APt-get is easier to install programs for monkeys like me.

---

### Post by iaculallad on 2008-08-26
> **enzodad said:**
> Hi i finaly ditched Vista :) I installed Las\test version ubuntu.
LOVE IT. but im not a linux expert yet. I cant use apt-get.. also when i typ in sudo wont ask for password and when it does just says incorrect. Is there a way to make it so there is only 1 user(me) as permen root? APt-get is easier to install programs for monkeys like me.

In your terminal:

```
sudo apt-get install blah-blah-application
```

and this command will ask you for your password. Normally, Ubuntu does not echo the characters you input through your keyboard on your display so you just have to type your password and press Enter.

You as permanent root will serve as an "Achilles Heel" for your unit. Thus, Ubuntu disabled the root account as default so you have to issue your privileged password when issuing system commands.

---

