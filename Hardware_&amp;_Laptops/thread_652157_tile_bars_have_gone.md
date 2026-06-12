---
title: "tile bars have gone"
date: 2007-12-28
forum: Hardware &amp; Laptops
---

### Post by matthew91 on 2007-12-28
I have just installed the sound for my laptop. I have a lenovo 3000 n200, To install the sound i followed the steps on this page: [https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769B2G]("https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N200_0769B2G")
After i successfully installed the sound i had some updates to download so i downloaded then i thought it would be best to restart my computer, When i get back in i have realized that the title bars have gone. This means i am unable to move around my windows and it really annoys me, I now know that it is when i have compiz effects disabled the title bars come back. I was just wondering if it will be possible to run compiz with the title bars? i really want to show it off. Compiz was working fine before i installed the sound.

I am NOT Very technical at all really jsut to say ;).

(ps sorry for spelling mistake in title)

Thanks

---

### Post by CazperII on 2007-12-28
This sounds like a window manager problem. You can try to resolve this by installing Emerald. This is a commonly used window manager with Compiz. Emerald includes many themes. 


Just open up a console, type in 

```
sudo apt-get install emerald
```

Next restart X (ctrl-alt-backspace)

And finally you can choose the theme in System -> preferences -> Emerald theme manager


Hope this helps

Grts

---

### Post by matthew91 on 2007-12-29
I have installed emerald but i have no idea about how to enable the theme (yes i am a complete noob)

EDIT: All of a sudden the title bars came back but they are transparent :S and they only come back if the window is not maximized but sometimes they disappear again for no reason

---

### Post by CazperII on 2007-12-29
Just open system-> preferences -> Emerald Theme manager and select a theme from the list. If there are no themes installed goto the repositories tab and click "fetch GPL'd themes"

If for some reason Emerald doesn't start when logging in, you could test it by opening a console and typing:

```
sudo emerald --replace
```

---

### Post by matthew91 on 2007-12-29
> **CazperII said:**
> Just open system-> preferences -> Emerald Theme manager and select a theme from the list. If there are no themes installed goto the repositories tab and click "fetch GPL'd themes"

If for some reason Emerald doesn't start when logging in, you could test it by opening a console and typing:

```
sudo emerald --replace
```

That is weird. When i type that into the terminal it works and the title bars come back but when you close down terminal the title bars go away again. is this suppose to happen?

---

### Post by Gigamo on 2007-12-29
> **matthew91 said:**
> That is weird. When i type that into the terminal it works and the title bars come back but when you close down terminal the title bars go away again. is this suppose to happen?

Go to System -> Preferences -> Sessions, and add a new startup item (in the first of three tabs) named Emerald, and where it says Command: you enter the ```
emerald --replace
``` thingy. Then do a CTRL-ALT-BACKSPACE and log back in to see if it works.

---

### Post by CazperII on 2007-12-29
If emerald doesn't start up when you login you need to add emerald to the session

System -> preferences -> sessions

The click "add" 

Name: Emerald
Command emerald --replace 

click "ok","close"

Then logout and log back in, and emerald should load every time you login

---

### Post by matthew91 on 2008-01-01
Thanks everyone

The problem has been solved :)

thanks to everyone who helped :)

---

