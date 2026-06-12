---
title: "Making GTK+-2.0 accessible"
date: 2005-11-29
forum: General Help
---

### Post by jonathanhayward on 2005-11-29
I went to compile [http://jonathanscorner.com/tms/download/tms2_0.tar.gz](http://jonathanscorner.com/tms/download/tms2_0.tar.gz) which uses GTK. I got the error messages below when I tried to compile it (I think the most significant errors are at the top.)

How do I make it so pkg-config will recognize gtk+-2.0 as installed?

gcc -c -g -O2 -Wall `pkg-config --cflags gtk+-2.0` action1.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
In file included from action1.c:9:
tms.h:4012:21: error: gtk/gtk.h: No such file or directory
In file included from action1.c:9:
tms.h:4017: error: syntax error before ‘*’ token
tms.h:4017: warning: type defaults to ‘int’ in declaration of ‘gtk_accelerators’tms.h:4017: warning: data definition has no type or storage class
tms.h:4018: error: syntax error before ‘*’ token
tms.h:4018: warning: type defaults to ‘int’ in declaration of ‘dungeon_targeting_window’
tms.h:4018: warning: type defaults to ‘int’ in declaration of ‘main_window’
tms.h:4018: warning: type defaults to ‘int’ in declaration of ‘message_window_vbox’
tms.h:4018: warning: data definition has no type or storage class
tms.h:4019: error: syntax error before ‘*’ token
tms.h:4019: warning: type defaults to ‘int’ in declaration of ‘master_icons’
tms.h:4019: warning: data definition has no type or storage class
tms.h:4021: error: syntax error before ‘*’ token
tms.h:4021: warning: type defaults to ‘int’ in declaration of ‘bottom_panel’
tms.h:4021: warning: data definition has no type or storage class
tms.h:4022: error: syntax error before ‘*’ token
tms.h:4022: warning: type defaults to ‘int’ in declaration of ‘dungeon_map’
tms.h:4022: warning: data definition has no type or storage class
tms.h:4023: error: syntax error before ‘*’ token
tms.h:4023: warning: type defaults to ‘int’ in declaration of ‘get_main_window_contents’
tms.h:4023: warning: data definition has no type or storage class
tms.h:4024: error: syntax error before ‘*’ token
tms.h:4024: warning: type defaults to ‘int’ in declaration of ‘left_panel’
tms.h:4024: warning: data definition has no type or storage class
tms.h:4030: error: syntax error before ‘*’ token
tms.h:4043: error: syntax error before ‘*’ token
tms.h:4045: error: syntax error before ‘*’ token
tms.h:4054: error: syntax error before ‘*’ token
tms.h:4055: error: syntax error before ‘*’ token
tms.h:4056: error: syntax error before ‘*’ token
tms.h:4057: error: syntax error before ‘*’ token
tms.h:4058: error: syntax error before ‘*’ token
tms.h:4059: error: syntax error before ‘*’ token
tms.h:4059: warning: type defaults to ‘int’ in declaration of ‘left_panel’
tms.h:4059: warning: data definition has no type or storage class
tms.h:4060: error: syntax error before ‘*’ token
tms.h:4060: warning: type defaults to ‘int’ in declaration of ‘load_icon’
tms.h:4060: warning: data definition has no type or storage class
tms.h:4061: error: syntax error before ‘*’ token
tms.h:4061: warning: type defaults to ‘int’ in declaration of ‘lookup_icon’
tms.h:4061: warning: data definition has no type or storage class
tms.h:4062: error: syntax error before ‘*’ token
tms.h:4062: warning: type defaults to ‘int’ in declaration of ‘menu_from_strings’
tms.h:4062: warning: data definition has no type or storage class
tms.h:4233: error: syntax error before ‘tms_idle’
tms.h:4233: warning: type defaults to ‘int’ in declaration of ‘tms_idle’
tms.h:4233: warning: data definition has no type or storage class
tms.h:4234: error: syntax error before ‘menu_item_selected’
tms.h:4234: error: syntax error before ‘data’
tms.h:4234: warning: type defaults to ‘int’ in declaration of ‘menu_item_selected’
tms.h:4234: warning: data definition has no type or storage class
make: *** [action1.o] Error 1

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

---

### Post by SickTwist on 2005-11-29
Make sure that the GTK+ development files are installed:

sudo apt-get install libgtk2.0-dev

---

### Post by jonathanhayward on 2005-12-01
[QUOTE=SickTwist]Make sure that the GTK+ development files are installed:

sudo apt-get install libgtk2.0-dev[/QUOTE]

There were errors when I tried that:

root@inner-sanctum:~/download/xpdf-3.01-linux# sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree... Done
Package libgtk2.0-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgtk2.0-bin
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package libgtk2.0-dev has no installation candidate

jonathan@inner-sanctum:~/mirror/about/awards$ sudo apt-get install libgtk2.0-binPassword:
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-bin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
jonathan@inner-sanctum:~/mirror/about/awards$

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail (gmail.com) account, please tell me!

---

