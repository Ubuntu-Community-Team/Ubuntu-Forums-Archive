---
title: "help with dbase access permissions ?"
date: 2008-11-29
forum: General Help
---

### Post by huongalt on 2008-11-29
Hi All

I get the folloing error when trying to start up mediatomb at boot, it runs if i start it from command line however(I know the config.xml files are stored in 2 places, I have checked these and they are exactly the same)
Im guessing that the db file is locked for some reason- can anyone help me out or at least provide a clue.


2008-11-29 17:05:44    INFO: Loading configuration from: /etc/mediatomb/config.xml
2008-11-29 17:05:44    INFO: Checking configuration...
2008-11-29 17:05:44    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2008-11-29 17:05:44    INFO: Setting metadata import charset to ANSI_X3.4-1968
2008-11-29 17:05:44    INFO: Setting playlist charset to ANSI_X3.4-1968
2008-11-29 17:05:44    INFO: Configuration check succeeded.
2008-11-29 17:05:44   ERROR: Error while accessing sqlite database file (/home/brett/.mediatomb/mediatomb.db): Permission denied

---

### Post by beno1990 on 2008-11-29
In the terminal, type:

```

chmod 777 ~/.mediatomb/mediatomb.db

```

Then try again.

---

### Post by huongalt on 2008-11-29
no joy im afraid, ill give up for the day i think..

---

### Post by huongalt on 2008-12-02
bump 
anyone know what else it could be,,, ?

---

### Post by kornivore on 2010-01-10
did anyone ever come up with an answer to this? I have the exact same prob.

---

### Post by kornivore on 2010-01-10
figured it out. I'm a total noob and was just typing "mediatomb" in terminal instead of "sudo mediatomb"

---

