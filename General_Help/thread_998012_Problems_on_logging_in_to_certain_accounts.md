---
title: "Problems on logging in to certain accounts"
date: 2008-11-30
forum: General Help
---

### Post by Ezlo4 on 2008-11-30
Okay, so I'm currently facing a bit of an issue on logging in. I can log in to my account but my mother's account won't log in at all. As soon as she tries logging in, the computer screen will turn brownish-orange (the Ubuntu colors) but then turn white. The screen doesn't seem frozen because I can still move the mouse cursor, but it doesn't go to the account's desktop. 

Also, I logged in as root and the same thing happened. Help will be greatly appreciated. Oh, and I tried creating two new accounts (one desktop user and one admin) and they both got the same result: a white screen.

Can someone please help me?

---

### Post by Ezlo4 on 2008-11-30
Bump. I seriously need help.

---

### Post by glennph93 on 2008-12-11
This is a problem for me also, on one of three accounts. I'm assuming it's a gnome setting but not sure what to do.

---

### Post by sydbat on 2008-12-11
Sounds like it might be a graphics card issue. What graphics card are you using? ATI? Nvidea?

---

### Post by glennph93 on 2008-12-11
I figured it out. On the one account that wasn't working compiz was enabled. I turned it off on my other accounts(conflicts with too much) and didn't really notice the problem. So to turn it off on the bad account with the white screen only, I did an Alt+F2 to bring up the run dialog(which I couldn't see) and ran the following command.```
metacity --replace
```
This worked ok, but I'm not sure why my ati graphics card(freedom hating driver) is not enabled anymore(this is what really caused the problem). I tried enabling it through the restricted manager and rebooted and it's still disabled.
Also if this is Ezlo4 problem(I think it is) why are new accounts enabled with compiz on without the proper graphics?

---

