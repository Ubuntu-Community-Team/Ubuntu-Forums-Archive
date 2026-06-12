---
title: "Synaptic not working."
date: 2005-11-21
forum: General Help
---

### Post by btarlinian on 2005-11-21
Hello everyone,

I 've just installed ubuntu breezy (dual-boot with windows) and Synaptic refuses to work. I go to applications ->add programs and click nothing happens. However, when I use apt-get from the terminal everything seems to work fine. What am I doing wrong?

Thanks in advance,

Ben

---

### Post by aysiu on 2005-11-21
What about when you go to System > Administration > Synaptic Package Manager? Or what if you launch this command ```
gksudo synaptic
```? Still no go?

---

### Post by btarlinian on 2005-11-22
[QUOTE=aysiu]What about when you go to System > Administration > Synaptic Package Manager?[/QUOTE]
This doesn't work however, after rebooting, I tried this as well as the add applications choice and it asks me for my password, but after that nothing happens. If I try to get to Synaptic again, through either the add applications or  Synaptic package Manager choice nothing happens.
[QUOTE=aysiu]
Or what if you launch this command ```
gksudo synaptic
```? Still no go?[/QUOTE]
Now here's where it gets interesting. I haven't tried that exact command. However I did some experimenting and found this: 
If I open the terminal, type su, hit enter and then enter the password for root, and then type syanptic synaptic opens fine.
However, I'd rather not have to open the terminal everytime I want to use Syanptic. I'll try gksudo synaptic later today (I'm posting this from a different computer.) Thanks for your help.

---

### Post by btarlinian on 2005-11-26
[QUOTE=aysiu]```
gksudo synaptic
```? Still no go?[/QUOTE]

Nope nothing. I get a password prompt the first time I try it, but after I type in my password (not root password), but if I try it again the command executes in the terminal, but nothing pops up.

After a little more experimentation it seems that sudo doesn't word for anything at all. Maybe it's not a synaptic problem. Anything I want to do with sudo I have to do with su.

Please help and thanks for what you've done so far.

---

### Post by Xian on 2005-11-26
[QUOTE=btarlinian]Maybe it's not a synaptic problem. Anything I want to do with sudo I have to do with su.[/QUOTE]
In that case you will want this command:

$ gksu synaptic

You also need to run 'visudo' as root and fix your sudoers file.

---

### Post by peterthebike on 2005-12-03
[QUOTE=btarlinian]it asks me for my password, but after that nothing happens. If I try to get to Synaptic again, through either the add applications or  Synaptic package Manager choice nothing happens.

Now here's where it gets interesting. I haven't tried that exact command. However I did some experimenting and found this: 
If I open the terminal, type su, hit enter and then enter the password for root, and then type syanptic synaptic opens fine.
[/QUOTE]
I have now got exactly the same error. 

Synaptic has been working fine since I upgraded to Breezy several weeks ago.

Any suggestions? :???:

---

### Post by peterthebike on 2005-12-03
Just found that when I exit Synaptic, I had this in the terminal:
```
(synaptic:9613): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9613): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
```
Don't know if that helps.

---

### Post by peterthebike on 2005-12-05
Fixed problem by using the workaround shown in this bug report [https://launchpad.net/distros/ubuntu/+bug/4738]("https://launchpad.net/distros/ubuntu/+bug/4738")

---

### Post by Gray. on 2005-12-05
I don't see the point in adding the additional user though. Also it isn't really good practice to just tick all boxes and leave it be. 
Maybe you could login as root as suggested in the bug report, then:
System > Administration > Users and Groups
Tick "Show all users and groups"
Then in the "Groups" tab, select the 'sudo' group and click "Properties"
Select your username in the list on the left and Click "Add"
Then click "OK" and then "OK" again.
Hopefully then, you should have sudo privileges.

---

