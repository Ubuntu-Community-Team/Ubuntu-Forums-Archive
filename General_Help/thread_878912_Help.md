---
title: "Help"
date: 2008-08-03
forum: General Help
---

### Post by tripozo on 2008-08-03
Hi. I have ctrl buttons broken on my laptop. Some time ago I spilled some tea on the keyboard, so now these buttons are sensitive and function without pressing them. What I do is:

xmodmap -e "add lock = Control_L"
xmodmap -e "add lock = Control_R"
xmodmap -e "add control = Caps_Lock"

Everything works fine till i change the keyboard language or restart the pc. How can I disable them forever, without entering these commands each time i turn on the pc o change the language on the keyboard.

Thanks

---

### Post by rEbyTer on 2008-08-03
If you want to execute those commands every time the GNOME session starts, go to System>Preferences>Sessions.

There you can choose the "Startup programs" tab and specify those 3 commands to execute when your session starts and in which order.

---

### Post by Diabolis on 2008-08-03
Yeah put them in a shell scrip like this:
```
gedit "*script name.sh*"
```

Content:
[PHP]
#!/bin/sh

xmodmap -e "add lock = Control_L"
xmodmap -e "add lock = Control_R"
xmodmap -e "add control = Caps_Lock"
[/PHP]

make it executable:
```
chmod +x "*name of script.sh*"
```

And add it to your sessions.

---

### Post by tripozo on 2008-08-03
hehe. Perfect. Thanks a lot!

---

### Post by rEbyTer on 2008-08-03
> Everything works fine till i change the keyboard language

I think this is not solved.... Are you sure ?

---

### Post by tripozo on 2008-08-03
i've hurried up thinking that it'll work. well, i does not..:/

---

### Post by rEbyTer on 2008-08-03
What is not working ?

---

### Post by Diabolis on 2008-08-03
Does it work if you execute the script by hand? you need to give us more information.

---

### Post by tripozo on 2008-08-03
sorry for waisting your time..i've just noticed that i had put this my post and then copied it to the script. I was mistake.

xmodmap -e "add lock = Control_L"
xmodmap -e "add lock = Control_R"

instead of 

xmodmap -e "remove control = Control_L"
xmodmap -e "remove control = Control_R"

Btw, with sessions manager in gnome everything lauches well. How can I do the same in KDE desktop?

Thanks again ;)

---

### Post by Diabolis on 2008-08-03
[How to autostart applications in KDE]("http://gentoo-wiki.com/HOWTO_Autostart_Programs#KDE")

---

