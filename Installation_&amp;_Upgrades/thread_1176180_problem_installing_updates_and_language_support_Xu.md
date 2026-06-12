---
title: "problem installing updates and language support Xubuntu Jaunty Jackalope sony  Vaio"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-06-02
hello all

as explained in this thread

[http://ubuntuforums.org/showthread.php?t=1173045&page=2](http://ubuntuforums.org/showthread.php?t=1173045&page=2)

i'm having issues installing updates and japanese and french language support on **Xubuntu Jaunty Jackalope** a japanese sony Vaio (VGN-FS21B)

i get the following 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i was advised to do a


sudo dpkg --configure -a

and get, after password confirmation :


Processing triggers for shared-mime-info ...
Setting up gnome-user-guide (2.26.0+svn20090323ubuntu5) ...

Processing triggers for man-db ...
dpkg: dependency problems prevent configuration of openoffice.org-help-en-us:
 openoffice.org-help-en-us depends on openoffice.org-writer | language-support-translations-en; however:
  Package openoffice.org-writer is not installed.
  Package language-support-translations-en is not installed.
dpkg: error processing openoffice.org-help-en-us (--configure):
 dependency problems - leaving unconfigured
Setting up hunspell-en-us (20070829-2ubuntu1) ...

Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up openoffice.org-l10n-common (1:3.0.1-9ubuntu2) ...
Setting up evolution-documentation-en (2.26.1-0ubuntu1) ...

Setting up gimp-help-common (2.4.1-1) ...
Setting up gimp-help-en (2.4.1-1) ...

Setting up gnome-user-guide-en (2.26.0+svn20090323ubuntu5) ...

Setting up openoffice.org-style-human (1:3.0.1-9ubuntu3) ...
Setting up language-pack-gnome-en (1:9.04+20090413) ...
Setting up openoffice.org-common (1:3.0.1-9ubuntu3) ...

Setting up language-pack-gnome-en-base (1:9.04+20090413) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Errors were encountered while processing:
 openoffice.org-help-en-us

----------

being quite clueless about all this i'm wondering what can be done fix this dpkg issue so that i can install language supportm updates, and basic software / codecs.

thanks in advance for your help

ben

---

### Post by bjaz on 2009-06-02
ok, a little update, this finally worked.
what i'm struggling with now is getting the japanese input SCIM / ime working, with this japanese keyboard.

---

### Post by bjaz on 2009-09-01
i'm still having a slight issue with this,  nothing too problematic but still annoying.

the computer is a japanese one, and needs to have a japanese keyboard (qwerty).
yet my wife uses xubuntu in french. we have both japanese and french language support, and the keyboard is either french (azerty), making do with the qwerty keyboard, or japanese.

the problem we're having is that the keyboard *always* switches back to french AZERTY upon start up. the password has to be inserted in azerty (not easy on a qwerty keyboard), whereas we would like it to always stay in QWERTY (japanese keyboard), and only switch it back to azerty when we're writing in french. but somehow, despite having played with the settings, it seems that since the OS is in french, it will not accept remaining in qwerty on startup.

hope this is not too confusing, the computer has a japanese qwerty keyboard, xubuntu is in french, and french and japanese language support is enable. But we would need it to *always* stay in qwerty, apart when we write in french on it.

thanks in advance for your help

ben

---

