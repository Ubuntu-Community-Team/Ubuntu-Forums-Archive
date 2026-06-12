---
title: "Dell Inspirion 8200 ATI Issue"
date: 2010-02-06
forum: Hardware
---

### Post by Havenbrook on 2010-02-06
[B]
1)Version Of Ubuntu : 9.10

2)Type Of Hardware: Dell Inspirion 8200, ATI 64mb graphics, 512mb ram. 1.8ghz single core processor

3)Hardware Maker: Dell

4)Hardware Model: 8200

[/B]I am very new to ubuntu. I just installed it last night to my laptop and it seems to work ok, the mouse is alittle touchy. Additionally i installed AWN and all the updates. I can not drag icons to the AWN dock bar (like firefox or pidgin it just doesn't accept them) i am also unable to change my background and things seem slightly slow and didn't seem to install any drivers to it. I do not know how to check this either. Any help would be appreciated :) thanx

*the laptop has the ATI standard video card and im assuming this is a issue with drivers*

---

### Post by derekmbarnes on 2010-02-07
Use this to check for drivers:

```
lspci -v | less
```

Should be under "Graphics controller" or something similar. Depending on your ATI model you'll probably want the FGLRX driver; should be under "Driver Updates" or something (apologies for the ambiguity, I haven't used the system in a few weeks.)

---

### Post by Havenbrook on 2010-02-07
can you tell me how to use that. like i said im new to ubuntu (or any linux platform for that matter) do i need to type this in the terminal? not quite sure what to do with it

---

### Post by derekmbarnes on 2010-02-15
Yes, you open Terminal and enter the command. You should also try [Ubuntu Documentation]("https://help.ubuntu.com/community") when looking for answers; the information provided there can be more useful and reliable than the forums.

---

