---
title: "how to open new tab in existing new-terminal"
date: 2008-08-21
forum: General Help
---

### Post by b4nsh33 on 2008-08-21
Hi, what i want to do is to open a new tab in a existing gnome-terminal without using the gnome-terminal menu but a command that opens a terminal, like ssh or telnet, is it posible?

---

### Post by Titan8990 on 2008-08-21
Shift+Ctrl+T? Not sure I fully understand.

---

### Post by jerome1232 on 2008-08-21
> **b4nsh33 said:**
> Hi, what i want to do is to open a new tab in a existing gnome-terminal without using the gnome-terminal menu but a command that opens a terminal, like ssh or telnet, is it posible?

with a command,
```
gnome-terminal -x *app*

for example

gnome-terminal -x ssh user@host
gnome-terminal -x tar cf backup.tar ~/
gnome-terminal -x man gnome-terminal
```

of course if you are using a different terminal emulator, susbitute it's name.

edit: -e also works but if there's a space you have to quote it

```
gnome-terminal -e "ssh user@host" --now-you-can-put-extra-options-here
```

**edit-edit: Looks like I actually didn't even answer your question, you want to open a new tab in current window, the only thing i see is --tab-with-profile-internal-id=internal id, but I can't find a way to determine the internal id of the current window**

---

### Post by b4nsh33 on 2008-08-21
thanks jerome, what  i want is that the 3 commands open in the same windows as tabs, i mean, i run the first one, several minutes later i run the second command and it opens in the same first window as another tab...

---

### Post by hvc123 on 2008-08-21
you should install 'terminator' 
its an excellent gnome-terminal that you right click in the terminal and open a new terminal in the same window

---

