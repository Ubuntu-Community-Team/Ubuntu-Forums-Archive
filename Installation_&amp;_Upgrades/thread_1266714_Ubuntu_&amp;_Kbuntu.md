---
title: "Ubuntu &amp; Kbuntu"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by Merrib64 on 2009-09-14
[B]I have installed Ubuntu 9.04 and I like it, but I thought I would like to try Kubuntu so I went to the synaptic package manager and selected Kubuntu for install. It went thru the process and downloaded the needed packages and installed them. When I boot up I am presented with the dual boot option within Kubuntu / Ubuntu start up. Kubuntu starts and I can use it with no problems and shut it down. When I select Gnome and it boots up everything works fine except for the shut down / hibernate etc button is gone so I cannot shut Ubuntu Gnome down short of literally pulling the power cord. How do I get this selection button back on the panel. I hope that I did not make a big mistake. Please help.

Bob
[/B]

---

### Post by earthpigg on 2009-09-14
hi,

what happens if you **log out** of gnome and shut down from there?

---

### Post by running_rabbit07 on 2009-09-14
You may also try adding the shutdown button to your toolbars. To get the add button menu just right click the toolbar where you want the button to be and you will get the pictured menu. See attachment.

---

### Post by Merrib64 on 2009-09-14
> **earthpigg said:**
> hi,

what happens if you **log out** of gnome and shut down from there?


I can't log out of Gnome. The only way is to pull the power cord and that is playing with fire.

Bob

---

### Post by earthpigg on 2009-09-15
> **Merrib64 said:**
> I can't log out of Gnome. The only way is to pull the power cord and that is playing with fire.

Bob

what if you do this:

```
sudo killall Xorg
```

or it may be 

```
sudo killall xorg
```

one of those two. i can't recall cuz im not on ubuntu right now.

---

### Post by running_rabbit07 on 2009-09-15
> **earthpigg said:**
>  i can't recall cuz im not on ubuntu right now.

Shame! J/K

Did the button trick work?

---

### Post by DasEi on 2009-09-15
sudo /etc/init.d/gdm stop 
(also start,restart)

---

### Post by Merrib64 on 2009-09-15
[B]The button trick worked. Sometimes I feel like a idiot. I am my own worst enemy when it comes to computers, even after working with them and software for years. Many thanks for the replies. I appreciate all the help.

Bob[/B]

---

### Post by running_rabbit07 on 2009-09-15
I am glad it worked.

---

