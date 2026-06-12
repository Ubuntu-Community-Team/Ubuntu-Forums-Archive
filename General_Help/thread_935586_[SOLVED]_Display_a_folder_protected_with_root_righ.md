---
title: "[SOLVED] Display a folder protected with root rights !!!!"
date: 2008-10-01
forum: General Help
---

### Post by cyberbrain_12 on 2008-10-01
Hi everyone,
I've created a file under root session called Pictures...with root rights
```
chmod 600 Pictures
```

and logged on as normal user..tried to access it but i can't display the
folder on the current session...I've tried this :
```
su -
Password: [....]
nautilus Pictures &
```

So my question how can i redirect the display of any program (here nautilus),
which executed with root rights to the current session !!

Got this from a forum but it doesn't work !!!
```
su - USER_A -c "xauth add `xauth list :0.0`; DISPLAY=:0.0 program-you-wish-to-launch"
```

---

### Post by cyberbrain_12 on 2008-10-01
```
su - -c "exec env DISPLAY='$DISPLAY' \
                  XAUTHORITY='${XAUTHORITY-$HOME/.Xauthority}' \
                   Here the command to run"
```


Tricky...i found it [here]("http://www.linux.com/base/ldp/howto/Remote-X-Apps-7.htmlt")

Best regards...!:D

---

