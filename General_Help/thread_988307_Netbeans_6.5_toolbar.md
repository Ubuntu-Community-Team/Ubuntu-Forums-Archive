---
title: "Netbeans 6.5 toolbar"
date: 2008-11-20
forum: General Help
---

### Post by L815 on 2008-11-20
This could be a problem related to netbeans itself, in which I should ask them for support but I figured I should ask here first in case someone knows a solution.

Netbeans 6.5 is out and I decided to install it. Previous versions (6.1) didn't have this problem (this is a fresh ubuntu install btw). 

This is what it looks like [look below]. The toolbar is way too large and setting the option to use "small icons" does not help.

Anyone have any idea?

---

### Post by nikomax on 2008-12-03
Hey there,

I have the same problem, It occurred after I installed a new theme, it may have been the same one as yours actually, the IDE looks almost the same anyway. Does anyone know if this might of caused the problem?

I am looking around as well for a solution but if you find one first can you let me know?

Thanks,

Paul

---

### Post by nikomax on 2008-12-03
Ok!!

I have managed to fix this.

I am certain that that new dark theme that I turned on caused this. 

So I Started by turning Visual effects in Appearance Preferences to none, just in case.

Afterwards I changed back to the Human-Clearlooks theme and Customised it, changing the Controls option to a different set.

After running NetBeans again I saw that the Toolbars had change back to normal apart from the Search Bar.

To fix this I edited this file :: /home/-user-/.netbeans/6.5/config/Toolbars/standard.xml So that the search bar was in the same row.

I don't think it was the visual effects that caused this do I turned them back on and it didn't revert

I hope this helps you if you haven't already fixed this!!

Paul

---

### Post by tezer on 2009-03-28
It might be because of the bug with Dust Theme. The workaround is:
(as found in [https://bugs.launchpad.net/dusttheme/+bug/321993]("https://bugs.launchpad.net/dusttheme/+bug/321993"))

> I changed the following in the gtkrc file in the gtk-2.0 folder from the theme and Netbeans did not have the problem anymore. For some reason the toolbar cannot have a ythickness of 3. The same goes for the extras. I think this is the only workaround for now. The toolbars need to be set to ythickness of 2.

style "wider"
{
 xthickness = 3
 ythickness = 3 -> 2

style "dark-toolbar" = "dark"
{
 xthickness = 3
 ythickness = 3 -> 2

Instead of "dark-toolbar" find any line which has the word 'toolbar' and change as indicated.
I did as described and everything seems to be OK now...

---

### Post by rdrever on 2009-04-22
The workaround fixed my NetBeans toolbar issues with the "New Wave Dark Menus" theme as well.

I had to edit the following file and change ythickness to 2 in two places.

/usr/share/themes/New Wave Dark Menus/gtk-2.0/default-gtkrc

---

### Post by Lukyan on 2009-05-05
Great workaround! :)

---

