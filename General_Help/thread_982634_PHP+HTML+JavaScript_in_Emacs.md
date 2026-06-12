---
title: "PHP+HTML+JavaScript in Emacs"
date: 2008-11-14
forum: General Help
---

### Post by Jesdisciple on 2008-11-14
I just got php-mode installed in Emacs and tried to indent my PHP+HTML.```
Warning (php-indent): 
	Indentation fails badly with mixed HTML and PHP.
	Look for an Emacs Lisp library that supports "multiple
	major modes" like mumamo, mmm-mode or multi-mode.
```I'm going to need heavier work than that...  I usually embed JavaScript in my HTML; depending on several factors, PHP is often thrown in as well.  What Emacs mode can do this best?  I've begun to [install nXhtml]("http://ourcomments.org/Emacs/nXhtml/doc/nxhtml.html#qg") as a foundation for [MuMaMo]("http://www.emacswiki.org/emacs/MuMaMo"), but do I really want to complete that expedition?  (I also wonder what all the other files in that archive I downloaded are for...)

Thanks.  :)

---

### Post by ju2wheels on 2008-11-15
Have you tried php-elisp instead of php-mode?

"Emacs major mode for php supporting syntax highlighting, indentation
and good integration with html-statements."

---

### Post by Jesdisciple on 2008-11-15
I hadn't, but I just installed it via apt-get and it doesn't seem to do anything.  It's not in my /usr/share/emacs/22.2/lisp so I searched for it via Nautilus.  The package apparently made a few folders which Emacs doesn't know about.```
/usr/share/doc/php-elisp
/usr/share/emacs22/site-lisp/php-elisp
/usr/share/emacs/site-lisp/php-elisp
/etc/emacs/site-start.d/50php-elisp.el
/usr/lib/emacsen-common/packages/install/php-elisp
/usr/lib/emacsen-common/packages/remove/php-elisp
/var/lib/dpkg/info/php-elisp.conffiles
/var/lib/dpkg/info/php-elisp.list
/var/lib/dpkg/info/php-elisp.md5sums
/var/lib/dpkg/info/php-elisp.postinst
/var/lib/dpkg/info/php-elisp.prerm
/var/cache/apt/archives/php-elisp_1.4.0-2_all.deb
```But can php-elisp handle JavaScript?

Also, I'm having trouble with nXhtml...  (The xXx represents several control characters which refused to be copied.)```
Debugger entered--Lisp error: (file-error "Cannot open load file" "as-external")
  require(as-external)
  (let* ((util-dir ...) (related-dir ...)) (add-to-list (quote load-path) util-dir) (add-to-list (quote load-path) related-dir) (require (quote as-external)) (load (expand-file-name "nxhtml-loaddefs.el" nxhtml-install-dir)) (unless (fboundp ...) (load ...)) (load-file (expand-file-name "etc/schema/schema-path-patch.el" nxhtml-install-dir)) (rncpp-patch-xhtml-loader) (load (expand-file-name "nxhtml/nxhtml-autoload" nxhtml-install-dir)))
  (if (featurep (quote nxhtml-autostart)) nil (provide (quote nxhtml-autostart)) (when (fboundp ...) (require ...)) (let* (... ...) (add-to-list ... util-dir) (add-to-list ... related-dir) (require ...) (load ...) (unless ... ...) (load-file ...) (rncpp-patch-xhtml-loader) (load ...)))
  (unless (featurep (quote nxhtml-autostart)) (provide (quote nxhtml-autostart)) (when (fboundp ...) (require ...)) (let* (... ...) (add-to-list ... util-dir) (add-to-list ... related-dir) (require ...) (load ...) (unless ... ...) (load-file ...) (rncpp-patch-xhtml-loader) (load ...)))
  eval-buffer(#<buffer  *load*<2>> nil "/usr/share/emacs/22.2/lisp/nxhtml.el" nil t)  ; Reading at buffer position 3027
  load-with-code-conversion("/usr/share/emacs/22.2/lisp/nxhtml.el" "/usr/share/emacs/22.2/lisp/nxhtml.el" nil nil)
  load("/usr/share/emacs/22.2/lisp/nxhtml.el")
  eval-buffer(#<buffer  *load*> nil "/home/chris/.emacs" nil t)  ; Reading at buffer position 664
  load-with-code-conversion("/home/chris/.emacs" "/home/chris/.emacs" t t)
  load("~/.emacs" t t)
  #[nil "xXx" [init-file-user system-type user-init-file-1 user-init-file otherfile source ms-dos "~" "/_emacs" windows-nt directory-files nil "^\\.emacs\\(\\.elc?\\)?$" "~/.emacs" "^_emacs\\(\\.elc?\\)?$" "~/_emacs" vax-vms "sys$login:.emacs" "/.emacs" t load expand-file-name "init" file-name-as-directory "/.emacs.d" file-name-extension "elc" file-name-sans-extension ".el" file-exists-p file-newer-than-file-p message "Warning: %s is newer than %s" sit-for 1 "default" alt inhibit-default-init inhibit-startup-screen] 7]()
  command-line()
  normal-top-level()
```Here's my .emacs:```
(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(tab-always-indent (quote always)))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 )
(autoload 'js2-mode "js2" nil t)
(add-to-list 'auto-mode-alist '("\\.js$" . js2-mode))
(load "/usr/share/emacs/22.2/lisp/nxhtml.el")
```

---

### Post by ju2wheels on 2008-11-15
It might conflict with the php-mode package so I would remove that. Once you do open your php file with emacs and type "ALT+X php-mode" followed by enter.

It should then enable the php-elisp mode package. I havent used it myself for php editing, I just pulled the description off the package info, but if it can handle the html in the php then javascript should be ok as well but I cant tell you for sure.

---

### Post by Jesdisciple on 2008-11-16
Something must have changed since I posted, although I can't think what.  I had already restarted Emacs, but maybe my comp needed a restart.  Now php-elisp/php-mode loads automatically.  I do appreciate the suggestion, but its sense of indentation is pathetic (at least in PHP+HTML, but I get the impression that they are mangled when separated as well).  I'm glad I installed it with apt-get, as that made its removal painless.

So back to my nXhtml troubles...  When Emacs loads I get these messages:```
("/usr/bin/emacs22-gtk")
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 00debian-vars...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...done
Loading debian-ispell...done
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...done
Loading /etc/emacs/site-start.d/50php-elisp.el (source)...done
Loading /etc/emacs/site-start.d/50psvn.el (source)...done
Loading /usr/share/emacs/22.2/lisp/nxhtml.el (source)...
Nxml/Nxhtml Autostart.el loading ...
Loading regexp-opt...done


An error has occurred while loading `/home/chris/.emacs':

File error: Cannot open load file, as-external

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

For information about GNU Emacs and the GNU system, type C-h C-a.
```When I start it with --debug-init as instructed, I get the above error message.

---

### Post by ju2wheels on 2008-11-16
It looks like for some reason its loading both php-elisp and your custom package for nXhtml. I dont know enough about emacs to know if its smart enough to use one or the other, but Id suspect it may be triggering rules for both packages at the same time (which is why I also suggested removing the other php-mode package), but Im just speculating there.

For your second problem, have you ever started emacs using sudo? If you have it probably changed the permissions of your .emacs folder in your home directory. When launching emacs to edit a file, always be sure to use gksudo and not sudo.

If you have used sudo before, then do this to correct the permissions on your .emacs folder:

```

sudo chown -R chris:chris ~/.emacs/

```

---

### Post by Jesdisciple on 2008-11-16
I've already removed php-mode from ~/.emacs, but left it in /usr/share/emacs/22.2/lisp/ for convenience.  Based on my limited experience, I don't think it will do anything without being called.  That's the only place it's been called from because I manually installed it.

I have started it with sudo.  I performed the prescribed command for both ~/.emacs.d/ (a folder) and ~/.emacs (a Lisp file) and saw no changes.  I completely removed php-elisp via Synaptic and these are my new messages:```
("/usr/bin/emacs22-gtk")
Loading 00debian-vars...
No /etc/mailname. Reverting to default...
Loading 00debian-vars...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...
Loading debian-ispell...
Loading /var/cache/dictionaries-common/emacsen-ispell-default.el (source)...done
Loading debian-ispell...done
Loading /var/cache/dictionaries-common/emacsen-ispell-dicts.el (source)...done
Loading /etc/emacs/site-start.d/50dictionaries-common.el (source)...done
Loading /etc/emacs/site-start.d/50psvn.el (source)...done
Loading /usr/share/emacs/22.2/lisp/nxhtml.el (source)...
Nxml/Nxhtml Autostart.el loading ...
Loading regexp-opt...done


An error has occurred while loading `/home/chris/.emacs':

File error: Cannot open load file, as-external

To ensure normal operation, you should investigate and remove the
cause of the error in your initialization file.  Start Emacs with
the `--debug-init' option to view a complete error backtrace.

For information about GNU Emacs and the GNU system, type C-h C-a.
```

```
Debugger entered--Lisp error: (file-error "Cannot open load file" "as-external")
  require(as-external)
  (let* ((util-dir ...) (related-dir ...)) (add-to-list (quote load-path) util-dir) (add-to-list (quote load-path) related-dir) (require (quote as-external)) (load (expand-file-name "nxhtml-loaddefs.el" nxhtml-install-dir)) (unless (fboundp ...) (load ...)) (load-file (expand-file-name "etc/schema/schema-path-patch.el" nxhtml-install-dir)) (rncpp-patch-xhtml-loader) (load (expand-file-name "nxhtml/nxhtml-autoload" nxhtml-install-dir)))
  (if (featurep (quote nxhtml-autostart)) nil (provide (quote nxhtml-autostart)) (when (fboundp ...) (require ...)) (let* (... ...) (add-to-list ... util-dir) (add-to-list ... related-dir) (require ...) (load ...) (unless ... ...) (load-file ...) (rncpp-patch-xhtml-loader) (load ...)))
  (unless (featurep (quote nxhtml-autostart)) (provide (quote nxhtml-autostart)) (when (fboundp ...) (require ...)) (let* (... ...) (add-to-list ... util-dir) (add-to-list ... related-dir) (require ...) (load ...) (unless ... ...) (load-file ...) (rncpp-patch-xhtml-loader) (load ...)))
  eval-buffer(#<buffer  *load*<2>> nil "/usr/share/emacs/22.2/lisp/nxhtml.el" nil t)  ; Reading at buffer position 3027
  load-with-code-conversion("/usr/share/emacs/22.2/lisp/nxhtml.el" "/usr/share/emacs/22.2/lisp/nxhtml.el" nil nil)
  load("/usr/share/emacs/22.2/lisp/nxhtml.el")
  eval-buffer(#<buffer  *load*> nil "/home/chris/.emacs" nil t)  ; Reading at buffer position 664
  load-with-code-conversion("/home/chris/.emacs" "/home/chris/.emacs" t t)
  load("~/.emacs" t t)
  #[nil "xXx" [init-file-user system-type user-init-file-1 user-init-file otherfile source ms-dos "~" "/_emacs" windows-nt directory-files nil "^\\.emacs\\(\\.elc?\\)?$" "~/.emacs" "^_emacs\\(\\.elc?\\)?$" "~/_emacs" vax-vms "sys$login:.emacs" "/.emacs" t load expand-file-name "init" file-name-as-directory "/.emacs.d" file-name-extension "elc" file-name-sans-extension ".el" file-exists-p file-newer-than-file-p message "Warning: %s is newer than %s" sit-for 1 "default" alt inhibit-default-init inhibit-startup-screen] 7]()
  command-line()
  normal-top-level()
```

---

### Post by Jesdisciple on 2008-11-18
(bump)

---

### Post by tad on 2009-01-25
Emacs can't find a file named "as-external.el" or "as-external.elc", as requested by nXhtml. You'll need to add the directory containing this file to your load-path, e.g.

```
(add-to-list 'load-path "/path/to/nxhtml")
```

This should go in your startup file.

May I ask why you are installing third-party elisp packages to the global site-lisp? If you're on a single-user system, I would recommend creating a local lisp repository, e.g. ~/.elisp. That way Apt doesn't muck with it, and you retain the package and your configs across reinstalls. I reserve site-lisp for Ubuntu-packaged elisp programs.

---

### Post by Jesdisciple on 2009-01-25
Fresh eyes are sometimes the missing ingredient for a program, and my hiatus from this problem apparently helped.  But I might have never looked again except for tad's post.  I followed the link to nXhtml's installation instructions in my original post, found readme.txt, and realized that I had shown Emacs the wrong elisp file. I originally added this to my ~/.emacs:```
(load "/usr/share/emacs/22.2/lisp/nxhtml.el")
```but needed this:```
(load "/usr/share/emacs/22.2/nxhtml/autostart.el")
```I fixed that and ran **sudo emacs** and nXhtml is running - finally!> **tad said:**
> May I ask why you are installing third-party elisp packages to the global site-lisp?I have no clue; I'm just imperfectly following instructions with very little idea what they actually do.  (And I only realized how profoundly true that should be after typing it.)

> **tad said:**
> If you're on a single-user system, I would recommend creating a local lisp repository, e.g. ~/.elisp. That way Apt doesn't muck with it, and you retain the package and your configs across reinstalls. I reserve site-lisp for Ubuntu-packaged elisp programs.What files should be placed in that directory?  And how should ~/.emacs be modified to harmonize with that migration?

Thanks immensely!

---

