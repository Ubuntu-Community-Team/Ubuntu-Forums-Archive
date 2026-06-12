---
title: "list of application instaled"
date: 2008-10-18
forum: General Help
---

### Post by charanpreethu on 2008-10-18
how can i get the list of application that i have installed???

---

### Post by bodhi.zazen on 2008-10-18
```
sudo dpkg -l
```

Or to save this to a file

```
sudo dpkg -l > installed.txt
```

---

### Post by Yellow Pasque on 2008-10-18
The following command will list your installed packages:
```
dpkg --list
```

---

