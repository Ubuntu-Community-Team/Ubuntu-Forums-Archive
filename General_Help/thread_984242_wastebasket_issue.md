---
title: "wastebasket issue"
date: 2008-11-16
forum: General Help
---

### Post by beercz on 2008-11-16
Hi all

Apologies if this has been addressed elsewhere, I have searched extensively to no avail.

Mods, please merge threads if necessary.

I have a strange problem concerning my wastebasket.

Irrespective of whether I have items in the waste basket or not, it seems that when I open the wastebasket, gnome completely freezes for about 2 minutes.

Then I can use some of the other applications (firefox for example), but I cannot user the Applications, Places or System menus, nor can I click on any of the icons on the panel to launch any application.

I cannot use the waste basket at all, including any of the menu items.  I also notice that my workspace switcher "shrinks" - each workspace window is about a quarter of it's normal size.

The only way I can close wastebasket is to force it closed (by clicking on the X on the top right of the window) and then I am asked to wait or force close.  I force it.

Then everything returns to normal, except for the wastebasket.

I have checked the permissions and owner on ~/.local/shared/Trash:

> sudo chown -R ian ~/.local/shared/Trash
sudo chmod -R 700 ~/.local/shared/TrashI have even deleted the Trash folder and recreated the tree:

> sudo rm -rf ~/.local/shared/Trash
mkdir ~/.local/shared/Trash
mkdir ~/.local/shared/Trash/files
mkdir ~/.local/shared/Trash/infoThe problem still persists and I don't know what to do next.

I have temporarily removed the wastebasket icon from my panel, and I am not running compiz.

Anyone else experience this?  Anyone able to fix this or at least point me in the right direction? 

Thanks in advance.

---

