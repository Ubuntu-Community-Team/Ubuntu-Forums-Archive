---
title: "keyboard problem - no rapid character repetition while keeping key pressed down"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by ElMarcel on 2006-04-13
Hello everyone,

As the title says, while keepring a key pressed, I got no rapid character repetition, in any context (gedit, xterm, html text forms...), and only one character is typed on screen

The only way to (temporarily) fix the problem is to restart gdm:
```

sudo /etc/init.d/gdm restart

```

After sometime or some action the problem comes back.

Does anybody know where the problem is?

P.S.: I have a custom kernel... maybe some modules are missing?

---

### Post by oscar on 2006-04-13
System > Preferences > Keyboard
Tick "Key presses repeat when key is held down"
Does this help?

---

### Post by ElMarcel on 2006-05-04
I don't know... I haven't got this problem since my post.
If I will have problems, I'll try
Thanks a lot!!!

---

