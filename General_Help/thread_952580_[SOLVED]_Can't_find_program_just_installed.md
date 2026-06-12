---
title: "[SOLVED] Can't find program just installed?"
date: 2008-10-19
forum: General Help
---

### Post by dhoang417 on 2008-10-19
As the title of this thread says, I just downloaded and installed Prozgui download manager deb packages, but now I can't find the program on my laptop? strange...anyone? Thanks.:)

---

### Post by sancho panza on 2008-10-19
This is an issue that bothers many (and needs fixing), but one way to find it would be to right-click on the Apps button and select Edit menus. This lists all the programs with gui that are installed.

Hope that helps.

---

### Post by shawnrgr on 2008-10-19
```
whereis prozgui
```

some apps don't properly add themselves to the gnome menu. You can right click on applications > edit menu then add it yourself ;)

---

### Post by dhoang417 on 2008-10-19
Tried what you guys told me to, and I don't see it on the Apps edit menu either. Perhaps I didn't install it yet? I'm confused. I know I did.:confused:THis happened to me last time too when I installed SuperKaramba. It never showed up on my system.

I typed in "whereis progui" into the terminal and got this.

prozgui: /usr/bin/prozgui /usr/share/man/man1/prozgui.1.gz

so it is on my laptop?

---

### Post by alzie on 2008-10-19
Right click on "Applications" in the top left corner then you can select "edit menus".

Thanks sancho, I wasn't aware of this either.

---

### Post by dhoang417 on 2008-10-19
> **alzie said:**
> Right click on "Applications" in the top left corner then you can select "edit menus".

Thanks sancho, I wasn't aware of this either.

okay, I figured it out.  It turns out that the link to the .exe file was a different one given to me in the terminal.  

/usr/bin/prozgui

THanks guys.

CHeers!:)

It's working.

---

### Post by shawnrgr on 2008-10-19
> **dhoang417 said:**
> Tried what you guys told me to, and I don't see it on the Apps edit menu either. Perhaps I didn't install it yet? I'm confused. I know I did.:confused:THis happened to me last time too when I installed SuperKaramba. It never showed up on my system.

I typed in "whereis progui" into the terminal and got this.

prozgui: /usr/bin/prozgui /usr/share/man/man1/prozgui.1.gz

so it is on my laptop?

yes, you can launch it from the terminal by just simply typing 'prozgui' or like all of us keeps saying, right click on applications -> edit menu, click on a category, click add program/launcher or whatever it says im not in gnome, then give it a title, the launcher is simply the program name 'prozgui'. save it and close. Its not in the applications menu.

---

### Post by dhoang417 on 2008-10-19
> **shawnrgr said:**
> yes, you can launch it from the terminal by just simply typing 'prozgui' or like all of us keeps saying, right click on applications -> edit menu, click on a category, click add program/launcher or whatever it says im not in gnome, then give it a title, the launcher is simply the program name 'prozgui'. save it and close. Its not in the applications menu.

I wished that it was that easy by just naming it and making it work.  I also had to give the path to the application itself. Can't just give it a name, and automatically make it work.  That's why I said that the path given to me in the terminal was partly misleading.  I physically went into the directory and found the exe file, then I copied the link then placed it into the "edit menu" along with the name of the application which in this case is "prozgui."

---

