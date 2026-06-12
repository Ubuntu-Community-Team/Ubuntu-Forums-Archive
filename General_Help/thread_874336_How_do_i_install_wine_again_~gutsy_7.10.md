---
title: "How do i install wine again ~gutsy 7.10"
date: 2008-07-29
forum: General Help
---

### Post by KEE on 2008-07-29
How do install wine on gusty? there was a nice "how to" but i cant find it anymore =/ the link  was under "how to:Wow with wine" but now i get tons of info and and none are very clear on what to do =/ all i remember is one line of code..

$winecfg

can someone give me the link to the nice "how to" that makes easy to understand by showing each line of code to place on terminal?i =/  please help and thanks in advance =D

---

### Post by iaculallad on 2008-07-29
Add the repository:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Add the repo key:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
Update your sources:

```
sudo apt-get update
```

Download/Install Wine:

```
sudo apt-get install wine
```

This commands are all done in your terminal.

---

### Post by KEE on 2008-07-29
> **iaculallad said:**
> Add the repository:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```

Add the repo key:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
Update your sources:

```
sudo apt-get update
```

Download/Install Wine:

```
sudo apt-get install wine
```

This commands are all done in your terminal.

Thanks again iaculallad =D

---

