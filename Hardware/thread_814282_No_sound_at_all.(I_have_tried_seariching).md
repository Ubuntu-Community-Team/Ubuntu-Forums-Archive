---
title: "No sound at all.(I have tried seariching)"
date: 2008-05-31
forum: Hardware
---

### Post by Stephen4785 on 2008-05-31
Iv tried searching through old threads and none of the advice has gotten anything fixed. I installed a new hard drive and Intel mother board. Before the new mother board I still did not have sound. And no I didn't install a new mother board with intention of fixing the sound issue. The old mother board had 8 blown capacitors and would shut down for no reason.
 I can watch videos but I hear no sound. No system sounds,no music, nothing. I'm brand new to Ubuntu/Linux so I don't have any idea what to do.
  Thanks
    Stephen

---

### Post by Ripfox on 2008-05-31
Have you tried typing "alsamixer" into a terminal window and checking the sound levels there?

---

### Post by ugm6hr on 2008-05-31
> **Ripfox said:**
> Have you tried typing "alsamixer" into a terminal window and checking the sound levels there?

And maximising (arrow keys) AND unmuting (M) everything.

---

### Post by Stephen4785 on 2008-05-31
All of the levels are up to 100 and nothing is muted.By the way-Im running version 7.10

---

### Post by ugm6hr on 2008-06-01
Post the output from the following:
```
amixer
lspci
lshw -C multimedia
```

---

### Post by CameO73 on 2008-06-01
And, while you're at it, the output from this command:
```
asoundconf list
```

---

### Post by harsh1kumar on 2008-06-01
Which laptop do you have?? I have HP dv 6000 series laptop and the sound didnt worked initially. But then I fixed it. If the laptop is some other try googling something like 'Ubuntu on "Laptop model"'. There are hundereds of tutorials on different laptops which tell how to make Ubuntu running on a particular hardware.:)

---

