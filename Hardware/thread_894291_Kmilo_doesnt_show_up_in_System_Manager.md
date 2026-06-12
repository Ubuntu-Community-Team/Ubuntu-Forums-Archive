---
title: "Kmilo doesnt show up in System Manager"
date: 2008-08-19
forum: Hardware
---

### Post by elfstone2 on 2008-08-19
Hello,
i'd like to access my thinkvantage button on my thinkpad with Kubuntu 8.04.
Kmilo is already installed (and seems to work somehow, since I get breghtnessinformation when using the Fn keys, but no sound volume information).

It also seems to be running regarding to the service manager, but i cant access its settings in kcontrol->System Administration, because its simply not there.

How can i fix this?
Greetings,
Thomas

---

### Post by sergiom99 on 2008-08-19
Im not on my laptop now, but i think theres no settings for it. at least no icon in the menu.
try typing kmilo in konsole to see if its bring a settings screen or at least some command line help.

---

### Post by elfstone2 on 2008-08-20
No, kmilo is not found.. so nothing happens. But kmilo is installed, i even uninstalled and reinstalle it. Didnt change anything.

---

### Post by sergiom99 on 2008-08-20
I checked it last night.
Theres no command for it, and theres no menu item either.

It just works.

But if you need to configure special keys/actions, try keytouch. it lets you create your own keyboard layouts and bind special keys.
I've never used it myself though.

---

### Post by elfstone2 on 2008-08-20
Also i have seen screenshots where you can see a milo-button. 
And keytouch is nice to configure, but doesnt do anything either...
i started it with sudo /etc/init.d/keytouch start

---

### Post by sergiom99 on 2008-08-20
I am not sure since I've never used it, but you have to set up your keyboard in the keytouch GUI. Thats the daemon service that you started, now you have to configure your keyboard layout.
A search shows some threads about it:
[http://ubuntuforums.org/search.php?searchid=46632684](http://ubuntuforums.org/search.php?searchid=46632684)

---

