---
title: "Feature &quot;Always on top&quot; does not work correctly with Compton!"
date: 2016-03-15
forum: Hardware
---

### Post by Yashalta on 2016-03-15
[COLOR=#000000][FONT=Arial]I configure the compton.conf that if exists inactive window/s it is become a transparent.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Also I have a function "Always on top", this function does not work correctly with Compton! Because Compton make the window transparent like inactive window, even if the function "Always on top" is ON! The function "Always on top" works well without Compton! [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I think to me need to make an exception for Compton like "Do not make the window transparent if enabled function "Always on top"![/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Please, HELP!!![/FONT][/COLOR]



[COLOR=#000000][FONT=Arial]Lubuntu 15.10[/FONT][/COLOR]

---

### Post by Yashalta on 2016-04-08
read here [https://www.linux.org.ru/forum/general/12437023?lastmod=1458220509142#comment-12439066](https://www.linux.org.ru/forum/general/12437023?lastmod=1458220509142#comment-12439066)
Or if it briefly:
**opacity-rule = ["99:_NET_WM_STATE@:a *= 'ABOVE'"]**

---

