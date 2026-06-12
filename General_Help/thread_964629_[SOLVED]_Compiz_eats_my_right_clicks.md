---
title: "[SOLVED] Compiz eats my right clicks"
date: 2008-10-31
forum: General Help
---

### Post by jazzgossen on 2008-10-31
Since upgrading from 8.04 to 8.10, I have some problems with mouse clicks when using compiz.

At first, I couldn't click any buttons or open any files in Nautilus, although I could resize and move windows. That had to do with compiz' window move plugin, because when I disabled that, I can left-click again (but can't move any windows...). 

But I still can't right-click properly. Whenever I right-click a file in nautilus, for example, I just get the window context menu (with minimize/maximize/always on top, etc) instead of the file context menu (open/unzip/whatever). 

With compiz disabled, it works fine. I've been around in the compiz config manager for a while now, but haven't found anything that solves the problem yet. Does anybody recognize this?

---

### Post by Cammy on 2008-10-31
Make sure none of your compiz plugin bindings are using the right click.  I accidentally set my "Move Window" plugin to use Tab+left click, and found that I couldn't open links in FF in new tabs using that same key combo, so I had to change it.

When I upgraded from 7.04 to 8.04, I noticed that some of my plugin bindings had reverted.  It's worth a check.

---

### Post by jazzgossen on 2008-11-02
I thought I had gone through all the settings, even disabling basically every plugin. But simply clicking the "revert settings to default" in the compiz settings manager fixed the problem.

---

