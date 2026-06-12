---
title: "&quot;Double&quot; Login - CLI+GUI? CLI Resolution after Start"
date: 2008-09-10
forum: General Help
---

### Post by ThorX89 on 2008-09-10
Is there any way to set up a ubuntu system so that with each user there would be bound a console. I mean, everytime I log in/out graphically, it would log me on/off a virtual console as well?

And is there anyway to change the virtual console's resolution after the system has started? I know it before booting the system by setting a vga parameter in grub, but can do it aftewards?

---

### Post by Vivaldi Gloria on 2008-09-10
> **ThorX89 said:**
> Is there any way to set up a ubuntu system so that with each user there would be bound a console. I mean, everytime I log in/out graphically, it would log me on/off a virtual console as well?

Do you want that when you login gnome and press (say) ctrl+alt+F4 then you're already logged in there (tty4) also? If not clarify please.

> And is there anyway to change the virtual console's resolution after the system has started? I know it before booting the system by setting a vga parameter in grub, but can do it aftewards?

I don't know. But you may want to install fbset and look at its man page. It may be the command you are looking for. If you find out how to do it please write it here.

---

