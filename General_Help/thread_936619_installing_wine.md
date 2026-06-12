---
title: "installing wine"
date: 2008-10-03
forum: General Help
---

### Post by shivkumar_newbie on 2008-10-03
guys,
     Im new to linux.  I wnt to know steps for install wine ?im using ubuntu 8.04 .

---

### Post by DougieFresh4U on 2008-10-03
> **shivkumar_newbie said:**
> guys,
     Im new to linux.  I wnt to know steps for install wine ?im using ubuntu 8.04 .

Applications>Add/Remove
You will find it there, good luck
And welcome  to Ubuntu

---

### Post by geeth on 2008-10-03
Open terminal
apps > accessories > terminal

then run 

```
sudo apt-get install wine
```

---

### Post by iaculallad on 2008-10-03
> **shivkumar_newbie said:**
> guys,
     Im new to linux.  I wnt to know steps for install wine ?im using ubuntu 8.04 .

Drop to your terminal and issue the following commands below.

Add the GPG apt-key:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Add the repository:
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Update your sources.list file:
```
sudo apt-get update 
```

Install wine:
```
sudo apt-get install wine
```

HTH.

---

