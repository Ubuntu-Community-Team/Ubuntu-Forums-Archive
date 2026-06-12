---
title: "emacs goes Goth (white on black)"
date: 2008-08-24
forum: General Help
---

### Post by David J Bush on 2008-08-24
Yesterday, emacs was working just fine for me. My preferred text color scheme is black text on a cornsilk1 background. Today, when I started emacs up, I briefly see the cornsilk1 background, then it changes to white letters on a black background. The only change I made which I can remember was to install some emacs related packages, but I'm not sure which, probably emacs-goodies-el and some others. So, today I deleted every emacs enhancement package I could find. I make the assumption that every such package would be listed under the "editors" category within Aptitude. Here are all the emacs related packages I still have installed:

emacs
emacs22
emacs22-bin-common
emacs22-common
emacs22-el
emacsen-common
emacs21
emacs21-bin-common
emacs21-common
emacs22-gtk

After deleting the enhancement packages I did a cold restart, turned the machine completely off and back on again.

This is what my ~/.emacs file looks like:

(add-to-list 'load-path "~/elisp")

(and
      (require 'centered-cursor-mode)
      (global-centered-cursor-mode +1))
(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(blink-cursor-mode nil)
 '(foreground-color black)
 '(background-color cornsilk1)
 '(inhibit-default-init +1))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 )

I invoke emacs with the following command:

emacs -fn -schumacher-clean-medium-r-normal--0-0-75-75-c-0-iso8859-10 -g 120x75+200 -fg black -bg cornsilk1

The schumacher font loads just fine, and the window geometry is correct, but the background is still black.

I should add that the first time this happened, everything locked up, I could not reboot, I had to turn the machine off.

I am running Hardy 32-bit on a dual core amd64 machine.

Any suggestions would be appreciated!

David

---

### Post by coffeecat on 2008-08-24
I have no experience of emacs. So...

Have you enabled compiz and has your gnome panel also gone peculiar? If so, try pressing super+M.
[B]
A[/B]pologies for what is probably a silly suggestion because, if this is your problem, it would have affected all apps.

---

### Post by David J Bush on 2008-08-24
I appreciate the suggestion, but I don't have any compiz package installed. I use KDE. I guess I should have mentioned that, sorry.

I found the problem! It was the package **emacs-extra** which I had installed. I don't even know what that package is supposed to do in the first place. I removed it and emacs is now looking all sunny and cheerful again. I'm so happy.

---

