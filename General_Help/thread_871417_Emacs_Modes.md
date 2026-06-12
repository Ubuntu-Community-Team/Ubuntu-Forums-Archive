---
title: "Emacs Modes"
date: 2008-07-26
forum: General Help
---

### Post by dstein on 2008-07-26
I have an emacs mode called css-mode for editing CSS files. I have the .el file in a directory in my home directory, and I followed the installation instructions. When I open a CSS file in emacs, it automatically enters CSS mode, and everything works. However, unlike the built-in modes, typing
```
M-x css-mode
```does not allow me to enter CSS mode. emacs does not recognize 'css-mode' or 'css' when entered in the mini buffer. Any ideas why or how to change it so it does? Thanks.

---

### Post by gaussian on 2008-07-27
> **dstein said:**
> I have an emacs mode called css-mode for editing CSS files. I have the .el file in a directory in my home directory, and I followed the installation instructions. When I open a CSS file in emacs, it automatically enters CSS mode, and everything works. However, unlike the built-in modes, typing
```
M-x css-mode
```does not allow me to enter CSS mode. emacs does not recognize 'css-mode' or 'css' when entered in the mini buffer. Any ideas why or how to change it so it does? Thanks.

Have not used this mode, but do you have the .el file in your home directory or in your /home/username/.emacs.d directory? I think it should be in the latter

---

### Post by dstein on 2008-07-27
It is in my /home/username/emacs directory, which my .emacs knows to look for using:```
(add-to-list 'load-path "/home/username/emacs")
```
I tried moving it to the .emacs.d directory, which didn't work (even when loading a CSS file). However, I realized that after loading the CSS file, css-mode is then available to be turned on. The CSS mode README had me add the following to the .emacs: ```
(autoload 'css-mode "css-mode")
(setq auto-mode-alist       
      (cons '("\\.css\\'" . css-mode) auto-mode-alist))
```
Is there anything I can add to make css-mode available prior to actually loading a CSS file? Thanks.

---

### Post by gaussian on 2008-07-27
I am really not an emacs expert, but based on my experience with custom modes (mostly AucTeX) I fear the answer is no. Hopefully someone who knows little more can provide more info.

---

