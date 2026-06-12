---
title: "TclTk failed after upgrade to 9.10 in XVnc Session"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by jolig on 2009-11-05
Hello,

I am running a machine under ubuntu since 6.10.
This computer is headless & I am using XVnc in order to have multiple resumeable sessions available for different users.

I've done the upgrade from 9.04 to 9.10 yesterday & I am experiencing a big trouble.
One of my application which is running in TclTk is not longer working.
I get the following message :

```
[SIZE=1][FONT=Fixedsys]
Tk initialization failed: Can't find a usable tk.tcl in the following directories: 
    /opt/modelsim/6.5b/linux_x86_64/../tcl/tk8.4 /opt/modelsim/6.5b/linux_x86_64/../tcl/tcl8.4/tk8.4 /opt/modelsim/current/bin/../lib/tk8.4 /opt/modelsim/current/bin/../linux_x86_64/tk8.4 /opt/modelsim/current/bin/lib/tk8.4 /opt/modelsim/current/bin/../library /opt/modelsim/current/bin/library /opt/modelsim/current/bin/tk8.4.14/library /opt/modelsim/current/tk8.4.14/library

/opt/modelsim/6.5b/linux_x86_64/../tcl/tk8.4/tk.tcl: can't access "::tk::Priv.::ffff:127.0.0.1:7": parent namespace doesn't exist
can't access "::tk::Priv.::ffff:127.0.0.1:7": parent namespace doesn't exist
    while executing
"upvar #0 ::tk::Priv.::ffff:127.0.0.1:7 ::tk::Priv"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0 upvar #0 ::tk::Priv.$disp ::tk::Priv"
    (procedure "tk::ScreenChanged" line 9)
    invoked from within
"tk::ScreenChanged [winfo screen .]"
    (file "/opt/modelsim/6.5b/linux_x86_64/../tcl/tk8.4/tk.tcl" line 284)
    invoked from within
"source /opt/modelsim/6.5b/linux_x86_64/../tcl/tk8.4/tk.tcl"
    ("uplevel" body line 1)
    invoked from within
"uplevel #0
[list source $file]"


This probably means that tk wasn't installed properly.[/FONT][/SIZE]
```

The application is not the problem because If I try to run a small Tk script, I get the same kind of error.
I am still able to run the application under the session opened from the computer (not XVnc session).

If anyone has a clue to help me, I am open :)
Thanks in advance !


[SOLVED !]
Some tools use a broken tcl/tk opensource library (such as mentor modelsim).
A fix has been suggested by Tristan Schmelcher to the maintainers ([http://sourceforge.net/mailarchive/message.php?msg_name=268895540912061058l60228248u483940a5c2737cca%40mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_name=268895540912061058l60228248u483940a5c2737cca%40mail.gmail.com))
-> Open the tk.tcl file and apply the following patch :
```

--- tk.tcl.8.5	2009-12-06 19:14:10.000000000 +0100
+++ tk.tcl.new	2009-12-06 19:19:04.000000000 +0100
@@ -248,7 +248,14 @@
 	set disp $screen
     }
 
-    uplevel #0 upvar #0 ::tk::Priv.$disp ::tk::Priv
+    # disp can legally contain "::", so we have to create the portion up to
+    # the last :: as a namespace.
+    set var_name ::tk::Priv.${disp}
+    set x [string last :: $var_name]
+    set namespace_name [string range $var_name 0 [expr {$x - 1}]]
+    namespace eval $namespace_name {}
+
+    uplevel #0 upvar #0 $var_name ::tk::Priv
     variable ::tk::Priv
     global tcl_platform

```

---

### Post by jolig on 2009-11-06
Nobody has any idea ?

---

### Post by jolig on 2009-11-23
:(

---

### Post by Tristan Schmelcher on 2009-12-06
I actually ran into the exact same problem today! Was using ModelSim-Altera over XVnc and I encountered this and found your post by googling. I did some digging and managed to solve the problem. It's a bug in the open-source Tk library that ModelSim uses. I fixed the bug and sent the Tk developers a patch: [http://sourceforge.net/mailarchive/message.php?msg_name=268895540912061058l60228248u483940a5c2737cca%40mail.gmail.com](http://sourceforge.net/mailarchive/message.php?msg_name=268895540912061058l60228248u483940a5c2737cca%40mail.gmail.com). If you're familiar with the "patch" program you can apply it yourself to the tk.tcl file and things should then work.

---

### Post by jolig on 2009-12-07
It worked, thank you tristan !
(It was for moldesim yes ;))

I'll update the topic in order to let people having the fix.

Cheers,

Guillaume

---

### Post by jolig on 2010-02-09
Here is the patch
```

--- tk.tcl.8.5	2009-12-06 19:14:10.000000000 +0100
+++ tk.tcl.new	2009-12-06 19:19:04.000000000 +0100
@@ -248,7 +248,14 @@
 	set disp $screen
     }
 
-    uplevel #0 upvar #0 ::tk::Priv.$disp ::tk::Priv
+    # disp can legally contain "::", so we have to create the portion up to
+    # the last :: as a namespace.
+    set var_name ::tk::Priv.${disp}
+    set x [string last :: $var_name]
+    set namespace_name [string range $var_name 0 [expr {$x - 1}]]
+    namespace eval $namespace_name {}
+
+    uplevel #0 upvar #0 $var_name ::tk::Priv
     variable ::tk::Priv
     global tcl_platform
 

```

---

