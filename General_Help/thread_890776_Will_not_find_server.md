---
title: "Will not find server"
date: 2008-08-15
forum: General Help
---

### Post by Lawtonka on 2008-08-15
[SIZE="4"][SIZE="7"]I just installed ubuntu 8.04.1 It shows I,m connect to the internet but Firefox can't find server? What did I not do.:confused:

---

### Post by iaculallad on 2008-08-15
> **Lawtonka said:**
> [SIZE="4"][SIZE="7"]I just installed ubuntu 8.04.1 It shows I,m connect to the internet but Firefox can't find server? What did I not do.:confused:

Can you ping the website from your terminal:?

```
ping google.com
```

---

### Post by Lawtonka on 2008-08-15
New to ubuntu not sure what you are asking. can,t get online with ubuntu computer haaving to use my Window XP computer for this search. Can get on with it and also with my grandkids Cee PC wireless laptop. Its a Lunix bassed OS.Still:confused:My be to dumb!!Lawtonka

---

### Post by iaculallad on 2008-08-15
> **Lawtonka said:**
> New to ubuntu not sure what you are asking. can,t get online with ubuntu computer haaving to use my Window XP computer for this search. Can get on with it and also with my grandkids Cee PC wireless laptop. Its a Lunix bassed OS.Still:confused:My be to dumb!!Lawtonka

On the unit that you're using, Click on Application->Accessories->Terminal, that will open your terminal window and try to check if your could ping external sites: type the command below on your terminal:

```
ping google.com
```

and press Enter key. Post whatever displays...

---

### Post by jerome1232 on 2008-08-15
okay try this, on the ubuntu computer open a terminal

Applications>>Accessories>>Terminal
type in or copy 'n paste then paste the results here (in a terminal you have to do shift+ctrl+c and shift+ctrl+v to copy/paste)
```
ping -c 4 google.com
dig google.com
ping -c 4 64.233.167.99
ifconfig
```

---

