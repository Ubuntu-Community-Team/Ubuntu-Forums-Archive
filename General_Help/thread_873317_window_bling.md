---
title: "window bling"
date: 2008-07-28
forum: General Help
---

### Post by gamelord12 on 2008-07-28
How do I make my window title bars semi-transparent like Vista, or maybe somewhat shiny as well?  I'm using GNOME on a pre-installed Ubuntu Dell laptop.

---

### Post by gamelord12 on 2008-07-29
There is a way to do this with Compiz-Fusion or something, right?

---

### Post by SunnyRabbiera on 2008-07-29
Yes Compiz might help here, your card should allow you to have effects and such though you may need tweaking here and there.
Compiz is preinstalled if you are using the latest Ubuntu.
There is also something called emerald that will allow you to have transparent window boarders and such.

---

### Post by tuxxy on 2008-07-29
Install emerald, open terminal and type

```
sudo apt-get install emerald
```

Next command is to replace metacity with emerald, you could add this command to your system > prefs > sessions so you dont have to run it at every log in.

```

emerald --replace
```

Now donload the vista theme from [Gnome-look]("http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=102") and finally install and select the theme by moving the downloaded theme folder to your **/home/your-username/.emerald/themes** folder then open** system > prefs > emerald** and select your glass theme :)

---

