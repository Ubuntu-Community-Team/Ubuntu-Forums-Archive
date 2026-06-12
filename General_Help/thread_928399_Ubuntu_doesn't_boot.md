---
title: "Ubuntu doesn't boot"
date: 2008-09-23
forum: General Help
---

### Post by iStack245 on 2008-09-23
I have encountered this problem a lot lately. It has never worked. I got Ubuntu to work, it went to the actual Ubuntu desktop screen and did it's set up, then it rebooted, and nothing. A nice little black screen.
-----------------
Help please?

---

### Post by iStack245 on 2008-09-23
Help anyone?

---

### Post by tuxxy on 2008-09-23
What did you do before reboot, anything like installing video drivers for example

---

### Post by iStack245 on 2008-09-23
Nothing just simple installment.

---

### Post by tuxxy on 2008-09-23
When it boots to the black screen, you could try and open a terminal by pressing CTRL + ALT +F1

If you can, then start X with this command

```
startx
```

If it gives an error would be useful to post the output here

---

### Post by iStack245 on 2008-09-24
> **tuxxy said:**
> When it boots to the black screen, you could try and open a terminal by pressing CTRL + ALT +F1

If you can, then start X with this command

```
startx
```

If it gives an error would be useful to post the output here

I hit the keys, and typed in the code. Nothing! Oh I saw something like this in this huge message.

(filesystem=ntfs, error code 15 or 515 [dunno which bad writing])

---

### Post by xeth_delta on 2008-09-24
> **iStack245 said:**
> I hit the keys, and typed in the code. Nothing! Oh I saw something like this in this huge message.

(filesystem=ntfs, error code 15 or 515 [dunno which bad writing])

That, to me, would seem to indicate that the problem is before or at grub loading.

---

