---
title: "Main Menu missing options"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Sivan on 2009-04-28
Why is Shut Down, Log Out and Lock Screen not a part of the Main Menu anymore? I want to have a few icons on my menu bar. having those items taken out of the menu bar means I have to add another item to the panel just so I can log out or shut down my computer.

---

### Post by Partyboi2 on 2009-04-29
Hi, if you are using Jaunty they should be listed under 'System'

---

### Post by Sivan on 2009-05-02
I am using Jaunty. The issue is that if you do a new install, not an upgrade, there is no shutdown, log out or lock screen icons on the Main Menu. This is not the default menu that is installed on a new install. I use the main menu and remove the default menu as I do not like the Applications, Places and System menu on the task tray all the time.

---

### Post by TODDMAN on 2009-05-28
Anybody have a fix yet?

---

### Post by richbl on 2009-06-01
> **TODDMAN said:**
> Anybody have a fix yet?

I can repro this case as well.

On a clean install, the main menu is different than an upgrade (from Ibex, 8.10).

The upgrade appears to be missing all menu items below the System menu.

rich

---

### Post by merlinus on 2009-06-01
I have a red icon at the right of my upper taskbar.  It has a dropdown menu with the choices you are wanting.

---

### Post by richbl on 2009-06-01
> **merlinus said:**
> I have a red icon at the right of my upper taskbar.  It has a dropdown menu with the choices you are wanting.

Thanks for the response.

However, the issue in question is that there *appears* to be different behaviors with the Main Menu when upgrading vs. a clean install.

rich

---

### Post by TODDMAN on 2009-06-02
> **merlinus said:**
> I have a red icon at the right of my upper taskbar.  It has a dropdown menu with the choices you are wanting.

You're missing the point, we want it or the option to have shut down & log off in the main menu. I don't always use a mouse, keyboard is faster.

---

### Post by richbl on 2009-06-10
> **richbl said:**
> I can repro this case as well.

On a clean install, the main menu is different than an upgrade (from Ibex, 8.10).

The upgrade appears to be missing all menu items below the System menu.

rich

Well, in my specific case, **I was able to resolve the issue**.

Turns out that when the User Switcher applet is added, it surreptitiously tinkered with the menu bar.

Not sure if this is a new "feature" in Jaunty, but it most certainly is bad interface design: never alter something without first asking the user.

And in this specific case, while I understand the intended logic, it is faulty logic as there is not a 1:1 correlation in feature set between appliances, nor is there any evident affordance that the two appliances are related.

rich

---

### Post by TODDMAN on 2009-07-19
has anybody been able to fix this?

---

