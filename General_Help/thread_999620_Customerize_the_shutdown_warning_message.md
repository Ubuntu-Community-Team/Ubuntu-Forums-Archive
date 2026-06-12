---
title: "Customerize the shutdown warning message"
date: 2008-12-02
forum: General Help
---

### Post by siuchi on 2008-12-02
Is there anyway to customerize the shutdown warning message and if there any command that you send message to all shell?

Thanks
Chi

---

### Post by Vishal Agarwal on 2008-12-02
what do u mean by sending message ?

---

### Post by binbash on 2008-12-02
you can write what you want with shutdown command.Man shutdown

---

### Post by siuchi on 2008-12-02
> **Vishal Agarwal said:**
> what do u mean by sending message ?

When using shutdown command, all terminal(not sure if i'm using the right terms) would receive a message saying that "The system is going down for maintenance".

I am wondering if any command can do the same that i can broadcast a message to all terminal or shell???

Thanks

---

### Post by techboywi on 2008-12-02
Yes, you can use the following

To broadcast a message to all users:
```
wall 
Your message here

```
Then hit cntrl-D.  You need to enter the word all alone on a line, then your message, followed by the enter key, and then cntrl-D.

Shutdown works similarly:
```
 shutdown -r 5 Going down cuz I feel like it!!!
```

---

