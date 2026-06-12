---
title: "[SOLVED] I cant find opera on my PC"
date: 2008-08-08
forum: General Help
---

### Post by mahela007 on 2008-08-08
hello! I installed opera using the synaptic package manager. I know it is instaled because when i enter "opera" in terminal it runs quite well. However I cant find the launch icon anywhere in the applications menu. what can i do?

---

### Post by Perpetual on 2008-08-08
> **mahela007 said:**
> hello! I installed opera using the synaptic package manager. I know it is instaled because when i enter "opera" in terminal it runs quite well. However I cant find the launch icon anywhere in the applications menu. what can i do?

You could right click on Applications (Gnome-Main-Menu-Bar) and select Edit Menus.  Click New Item...

Name: Opera
Command: /usr/bin/opera

This should add the launcher to your menu.

---

### Post by mahela007 on 2008-08-08
Thanks for your help. However it seemed that a reboot of ubuntu made the icon reappear.

---

### Post by Perpetual on 2008-08-08
> **mahela007 said:**
> Thanks for your help. However it seemed that a reboot of ubuntu made the icon reappear.

I just had that happen with VirtualBox.  No icon until after a reboot.

---

### Post by munkyeetr on 2008-08-08
You can also use the '**which**' command to attempt to locate any files in your $PATH

```

$ which opera
/usr/bin/opera

```

---

### Post by Perpetual on 2008-08-08
> **munkyeetr said:**
> You can also use the '**which**' command to attempt to locate any files in your $PATH

```

$ which opera
/usr/bin/opera

```

Thanks for the tip.

---

