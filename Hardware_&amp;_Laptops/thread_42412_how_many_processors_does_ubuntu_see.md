---
title: "how many processors does ubuntu see?"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by banditti on 2005-06-17
what command can I use to see how many processors ubuntu sees?

---

### Post by SGC on 2005-06-17
The number of processes:
```

ps ax | wc -l | tr -d " "

```

The running Processes:
```

ps ax

```

---

### Post by banditti on 2005-06-17
Thank you for the reply, but i think you gave me how to check processes, not processors.

---

### Post by desdinova on 2005-06-17
Use Gnome System Monitor - Click Resources -> then see how many cpu's that sees - have you installed the SMP kernel?

---

### Post by SGC on 2005-06-17
[QUOTE=banditti]Thank you for the reply, but i think you gave me how to check processes, not processors.[/QUOTE]
 Sorry I didn't realize that.

---

### Post by banditti on 2005-06-18
Is there a way to do it from the command line?

---

### Post by GTvulse on 2005-06-18
[QUOTE=banditti]Is there a way to do it from the command line?[/QUOTE]
 ```
lshw
```

If you want a more detailed report, use lshal.

---

