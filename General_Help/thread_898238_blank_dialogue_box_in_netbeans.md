---
title: "blank dialogue box in netbeans"
date: 2008-08-23
forum: General Help
---

### Post by mrityunjay on 2008-08-23
I'm facing a strange problem with netbeans.
whenever i launch it with my user account it displays the following in terminal:
(<unknown>:10539): Gtk-WARNING **: Attempting to add a widget with type GtkButton to a GtkComboBoxEntry (need an instance of GtkEntry or of a subclass)

(<unknown>:10539): Gtk-CRITICAL **: gtk_widget_realize: assertion `GTK_WIDGET_ANCHORED (widget) || GTK_IS_INVISIBLE (widget)' failed

(<unknown>:10539): Gtk-CRITICAL **: gtk_paint_box: assertion `style->depth == gdk_drawable_get_depth (window)' failed


and sometimes it also displays a blank dialogue box.

but it runs perfectly if i execute it with 'sudo'.

can anybody tell me how can I get rid of this problem?
thanks

---

### Post by aloshbennett on 2008-08-23
Can you please see what you get when you try these commands?
$which java
$ls -l `which java`

---

### Post by mrityunjay on 2008-08-23
yes
output of 'which java':
 /usr/bin/java

output of 'ls - l `which java`':
 lrwxrwxrwx 1 root root 22 2008-07-24 19:02 /usr/bin/java -> /etc/alternatives/java

---

### Post by aloshbennett on 2008-08-23
Thats using gjc instead of sun java.
If you run 'java' at the command prompt, it would tell you about gnu java compiler.

Prepend the directory containing sun java to the path and lets see how netbeans work :)

---

