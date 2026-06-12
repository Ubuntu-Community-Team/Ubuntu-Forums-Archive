---
title: "Wrong Graphics Driver no login"
date: 2008-12-01
forum: Hardware
---

### Post by sbooder on 2008-12-01
Hi All,
         I foolishly loaded completely the wrong drivers for my ATI card and now can not login to 8.10, it freezes just before the username box comes up during boot.

I have tried looking for solutions on the forum, and did come across this:

```
sudo dpkg-reconfigure --phigh xserver-xorg
```

but I get the message Error 32 unknown command.

I entered the code after hitting 'C' at the kernel options screen.

I also tried entering the command at the shell prompt, but was asked for my root maintenance password, which dose not appear to be the same as my logon password.

Please someone tell me what the hell I am doing wrong!

Many thanks,

Simon.

---

### Post by taurus on 2008-12-01
Boot into recovery mode from GRUB menu and pick the option to fix your X server.

---

### Post by sbooder on 2008-12-01
done that with no results.  I have tried all the options in recovery mode, with no joy.

---

### Post by taurus on 2008-12-01
I guess you can boot into recovery mode and at the prompt, try running the command in your OP then.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by sbooder on 2008-12-01
> **taurus said:**
>  try running the command in your OP then.

I am not sure I know what OP is, and If you mean the prompt option in recovery mode, I get asked for my root maintenance password, which I do not know.

Sorry for being such a idiot, but I still find linux a foreign language.

---

