---
title: "Memory Card not detected in Ubuntu 14.04"
date: 2015-08-25
forum: Hardware
---

### Post by eMshsWE on 2015-08-25
Hello,

I have a Hp Pavillion dm4 Laptop and I have only Ubuntu 14.04 64 bit running on it. The 4GB Toshiba memory card of my Canon Camera is not being detected. I have removed and reinsterted it multiple times but no effect, it just doesnt get detected.

Could someone please help me out?

---

### Post by sudodus on 2015-08-25
What kind of card it it (specification)?

How do you connect it? Via the camera and USB or via a card reader?

Does it work
- in the camera (with the camera)?
- in another computer?
- with another operating system?

Please post the output of the following command lines

```
lsusb
```

```
sudo lsblk -fm
```

---

### Post by ajgreeny on 2015-08-25
I assume you are using a card-reader, so with the card inserted in the reader, open a terminal and run ```
sudo parted -l
```then post back the output here in code tags please (See my signature for a code-tags how-to).

This will show us if the system is detecting the card but for some reason it is not mounting.

---

### Post by eMshsWE on 2015-08-26
I noticed that if I press the memory card a little further into the slot, then it gets detected.

So I will mark this thread as solved.

---

