---
title: "Selected text not copying to xemacs clipboard"
date: 2008-08-22
forum: General Help
---

### Post by mike-g2 on 2008-08-22
Hi,

I'm getting some strange behavior in xemacs-gnome-nomule.  When I select text in Xemacs, it is not inserted into the xemacs clipboard.  

As I understand it there's an xemacs clipboard and a separate X clipboard.
Based on a previous [thread]("http://ubuntuforums.org/showthread.php?t=84378&highlight=xemacs+clipboard&page=2"), I added the following lines to my .xemacs/personal.el file

(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)

I can now paste the highlighted text from xemacs to another app, such as a terminal, but I still can't get get it to paste into xemacs itself.  that hasn't solved the problem.  Has anyone else run into this issue?


Thanks in advance.

Mike

---

