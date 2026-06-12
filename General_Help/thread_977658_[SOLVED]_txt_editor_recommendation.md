---
title: "[SOLVED] txt editor recommendation?"
date: 2008-11-10
forum: General Help
---

### Post by firsttimeuser on 2008-11-10
anyone here can recommend a txt editor in ubuntu?

The most needed feature will be regex based text search and highlighting, vi has the power but I really want something which highlights all the search results. 

TIA

---

### Post by IshikawaNakano on 2008-11-10
Try using vim or gvim if you like vi. They have alot more features.
You can use the option *hlsearch* in vim or gvim to highlight seach results.


In command mode type *:set hlsearch*

or

Put the line *set hlsearch* in your *~/.vimrc* or *~/.gvimrc*

---

### Post by cyfur01 on 2008-11-10
kate (KDE Advanced Text Editor) will also do as you wish. It's a little on the heavy side, being a KDE application, but I've enjoyed using it for a fair bit of C programming. 

Hit Ctrl+r to open the find and replace menu, and then you can change the searching preferences between "Plain Text", "Whole Words", "Escape Sequences" and "Regular Expressions", and you can check the "Highlight All" box to highlight all matches. After that, Ctrl+f should remember your preference.

---

### Post by firsttimeuser on 2008-11-10
ah thanks! did not know I can enable highlight in vi

---

