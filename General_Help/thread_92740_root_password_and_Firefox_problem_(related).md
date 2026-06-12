---
title: "root password and Firefox problem (related?)"
date: 2005-11-20
forum: General Help
---

### Post by hanspb on 2005-11-20
I have this weird thing happening on Ubuntu 5.10. There are som updates waiting to be installed. After I click the little red icon, the password dialog pops up just as usual, but when I type the first letter of the password the dialog just disappears, so I am not able to run the update manager. The same happens when I try to run Synaptic. Also when I start Firefox, it quits as soon as the window is drawn.
Both these problems occured at the same time, that was after I had tried to set the Gnome panels to transparent background. I have of course set it back to default settings, but it did not help. Any ideas, anyone?

---

### Post by ecobuntu on 2005-11-20
[QUOTE=hanspb]I have this weird thing happening on Ubuntu 5.10. There are som updates waiting to be installed. After I click the little red icon, the password dialog pops up just as usual, but when I type the first letter of the password the dialog just disappears, so I am not able to run the update manager. The same happens when I try to run Synaptic. Also when I start Firefox, it quits as soon as the window is drawn.
Both these problems occured at the same time, that was after I had tried to set the Gnome panels to transparent background. I have of course set it back to default settings, but it did not help. Any ideas, anyone?[/QUOTE]

Run these programs from the terminal and post the output here.

---

### Post by hanspb on 2005-11-20
The output of Firefox:
```

hpb@dellmaskin:~$ firefox
*** loading the extensions datasource
Memory segmentation fault
hpb@dellmaskin:~$

```
The output of Synaptic:
```

hpb@dellmaskin:~$ sudo synaptic
Password:

(synaptic:9009): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9009): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
hpb@dellmaskin:~$

```
The output of update-manager:
```

hpb@dellmaskin:~$ sudo update-manager
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig

(synaptic:9055): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9055): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9055): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
hpb@dellmaskin:~$

```
Both Synaptic and Update-manager seems to run fine once started. The thing is the password dialog.
Btw, My language is Norwegian, so there will be things that most people in the world don't understand, and I am not too shure about how to translate them.

---

### Post by vDave on 2005-11-20
[QUOTE=hanspb]The output of Firefox:
```

hpb@dellmaskin:~$ firefox
*** loading the extensions datasource
Memory segmentation fault
hpb@dellmaskin:~$

```
The output of Synaptic:
```

hpb@dellmaskin:~$ sudo synaptic
Password:

(synaptic:9009): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9009): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
hpb@dellmaskin:~$

```
The output of update-manager:
```

hpb@dellmaskin:~$ sudo update-manager
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig

(synaptic:9055): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9055): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9055): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold ... Ferdig
hpb@dellmaskin:~$

```
Both Synaptic and Update-manager seems to run fine once started. The thing is the password dialog.
Btw, My language is Norwegian, so there will be things that most people in the world don't understand, and I am not too shure about how to translate them.[/QUOTE]


I had a similar problem when I messed up my GTK libraries.
Specifically, dialog boxes (and firefox) would disappear as soon as I used a gui object, like a text box.

That is why i ended up reinstalling w/ Ubuntu =)

(Sorry, I know this wasn't that helpful)

  -dave-

---

### Post by hanspb on 2005-11-21
I guess I should also note that this happens only when I am logged into my normal user. I have another user for my kids, and there is no problem there.

---

