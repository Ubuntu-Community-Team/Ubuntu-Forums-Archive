---
title: "[SOLVED] Ubuntu Update Error"
date: 2008-07-31
forum: General Help
---

### Post by robotman5 on 2008-07-31
all i was doing was install updates then i wanted to change my login screen

then it went to a Black Screen with some Text


now when i try to install Updates i get this error:  E:dpkg was interrupted, you must manually run 'dpkg --configure -a' Can someone Help me? i might have other errors:( and i dont have superuser prillage to do it!

---

### Post by bks on 2008-07-31
> **robotman5 said:**
> run 'dpkg --configure -a' Can someone Help me? i might have other errors:( and i dont have superuser prillage to do it!

Do just want it says, in the terminal (Applications > Accessories > Terminal)

```

sudo dpkg --configure -a

```

*sudo* will give you temporary root permission and the dpkg will correct the error.

---

### Post by decoherence on 2008-07-31
> **robotman5 said:**
> all i was doing was install updates then i wanted to change my login screen

then it went to a Black Screen with some Text


now when i try to install Updates i get this error:  E:dpkg was interrupted, you must manually run 'dpkg --configure -a' Can someone Help me? i might have other errors:( and i dont have superuser prillage to do it!

how were you installing updates without superuser privs?

at the black screen type your username and press enter. then type your password. NOTE nothing will be echoed back to you when you type. Just type the password and press enter.

when the prompt comes up type the following line exactly

```
sudo dpkg --configure -a && sudo apt-get -f install && sudo shutdown -r now
```

This will allow dpkg to finish, try to fix any broken packages then restart your system. Hopefully it'll come back up healthy.

---

### Post by dexter.deepak on 2008-07-31
> **bks said:**
> Do just want it says, in the terminal (Applications > Accessories > Terminal)

```

sudo dpkg -a

```

well it should be sudo dpkg --configure -a

---

### Post by robotman5 on 2008-07-31
ok i typed that now what? i typed what dexter said its install gnome and other stuff

---

### Post by bks on 2008-07-31
> **robotman5 said:**
> ok i typed that now what? 

Try running the update manager again and see if the error is cleared.


> **robotman5 said:**
> i typed what dexter said its install gnome and other stuff

Can you post the output here?

---

### Post by robotman5 on 2008-07-31
THANK YOU Doco its fixed!!!!! :):KS

---

