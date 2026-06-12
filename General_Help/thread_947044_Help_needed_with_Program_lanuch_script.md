---
title: "Help needed with Program lanuch script"
date: 2008-10-13
forum: General Help
---

### Post by Lanrat on 2008-10-13
I'm working on writing a script that will launch a program so that it thinks it has a certain MAC address, but the rest of the computer does not. I want it to get this MAC address from a file in my home directory.

This is what I am doing now that is working:
```

MAC_ADDRESS=AA:AA:AA:AA:AA:AA LD_PRELOAD="/home/user/lib/libmacspoof.so.1.0.1" program
```

This is what I want to work:
```

MAC_ADDRESS=$(cat /home/user/mac.txt) LD_PRELOAD="/home/user/lib/libmacspoof.so.1.0.1" program
```

The problem is "$(cat /home/user/mac.txt)" returns a space before the actual MAC address which does not work.

How can I fix this?

Thanks.

---

### Post by linkxs on 2008-10-13
shell script?

---

### Post by Lanrat on 2008-10-13
I'd prefer it be one line, but a shell script will have the same problem/effect.

---

### Post by Lanrat on 2008-10-15
Anyone? this should be really easy.

---

