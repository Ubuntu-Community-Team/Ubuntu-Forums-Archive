---
title: "Where can i veiw my hardware? Is there a device manager??"
date: 2008-06-08
forum: Hardware
---

### Post by RedTooth on 2008-06-08
I want to see what kind of wireless card i have.

---

### Post by robertchahine on 2008-06-08
try this in a terminal

```
lspci
```

---

### Post by ibutho on 2008-06-08
One option is Applications -> Accessories -> Terminal
```
sudo lshw -C network
```
another
```
sudo lspci | grep -i net
```
If you prefer a GUI, you can run hal-device-manager.

---

