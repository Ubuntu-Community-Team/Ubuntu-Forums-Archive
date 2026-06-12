---
title: "MX610 Mouse/Thunderbird Help!!"
date: 2010-02-10
forum: Hardware
---

### Post by aglc2005 on 2010-02-10
I have followed the tutorial for getting the Logitech MX610 mouse to work in Ubuntu (I'm currently 9.10). So that is not the problem, my problem is getting thunderbird to issue the command(s) when there is new mail. Can anyone shed some light on the subject. Everything I have found is for Evolution or checkgmail.

---

### Post by lidex on 2010-02-10
What command would that be?

---

### Post by aglc2005 on 2010-02-10
Well if at all possible I would like to use two different. One would be 

```
mx610hack -p /dev/hiddev1
```

When I receive and e-mail and the other would be:

```
mx610hack -o /dev/hiddev1
```

When there are no new e-mails (like when I am done reading them).

Now if I cant execute two separate commands, this here would work:

```
mx610hack -p /dev/hiddev0 && sleep 1.5 && mx610hack -o /dev/hiddev1
```

---

### Post by aglc2005 on 2010-02-16
Bumb, anyone got an answer?

---

