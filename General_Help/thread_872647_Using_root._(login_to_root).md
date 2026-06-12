---
title: "Using root. (login to root?)"
date: 2008-07-28
forum: General Help
---

### Post by alex199020 on 2008-07-28
Im trying to install some Nvidia drivers and it says i need to be the root user. Having only just begun using linux im having trouble "becoming" the root user. 
I've tryed "su" in the terminal and it asks for a pass but i can't type it unless i press enter and then i have a limited time. 
I've tryed "su root" and again it asks for pass and i can't type it in till i press enter. 
I've also tryed "su <password>" and it comes up with "unknown id: <password>" 
I tryed loging in as the root from the log in but it says i can't from that screen. 

Help is appriciated, Thanks!

---

### Post by 505 on 2008-07-28
If you want to become the root user type 'sudo su' and press enter. Then enter *your* user password. You can use 'sudo' for any command that must be run a root, e.g. 'sudo install_nvidia_driver' will execute 'install_nvidia_driver' as root.

Please note that when you type your password it will not show feedback (no *'s for example). Just type the password and press enter. This is an extra security feature so no one can see how long you password is.

---

### Post by jonian_g on 2008-07-28
You don't have to install the nvidia drivers manualy. To get the latest drivers open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System tools>EnvyNG and install the driver only with a few clicks.

---

### Post by coffeecat on 2008-07-28
> **jonian_g said:**
> You don't have to install the nvidia drivers manualy. 

Agreed. And there's an even simpler way. Are you using Ubuntu/gnome? Go to System > Administration > Restricted Drivers (or something like that - I'm in Mandriva atm and going from memory). One click should install the nvidia driver automatically for you.

About root in Ubuntu. Here's a useful link for you:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Worth adding to your bookmarks. And reading! :wink:

---

### Post by DarinB on 2008-07-28
you can do it with gui but get out once you are done

in terminal
gksudo nautilus

---

### Post by jonian_g on 2008-07-28
> **coffeecat said:**
> Agreed. And there's an even simpler way. Are you using Ubuntu/gnome? Go to System > Administration > Restricted Drivers (or something like that - I'm in Mandriva atm and going from memory). One click should install the nvidia driver automatically for you.

This way you don't get the latest driver but if you have a gpu older that 8 series you don't need the latest driver.

---

### Post by alex199020 on 2008-07-28
I think that should sort it. Will try it when i get back from work. Thanks for the help :D

---

### Post by coffeecat on 2008-07-28
> **jonian_g said:**
> This way you don't get the latest driver but if you have a gpu older that 8 series you don't need the latest driver.

Thanks for the clarification.

---

### Post by jonian_g on 2008-07-28
Cheers

---

### Post by northern lights on 2008-07-28
> **DarinB said:**
> gksudo nautilus
Although I'd generally advise against opening a filemanager as root, if it must be done, nautilus should be opened as such ```
gksu 'nautilus --no-desktop'
```Since nautilus also draws the desktop running "gksu nautilus" will result in having root's desktop drawn.

---

### Post by DarinB on 2008-07-28
please explain a little more?????
no desktop

---

### Post by northern lights on 2008-07-28
> **DarinB said:**
> please explain a little more?????
no desktop

The application 'nautilus' is not just a filemanager but, in gnome environments also responsible for drawing the desktop to the root (don't confuse with superuser) of the screen.

When you run it with 'gksu', you do not only gain root privileges, but also open the application with root's (here i mean the superuser) preferences. Hence, the root's desktop will be drawn.

Since you generally can't login from the root account and thus you also can't have changed the root's preferences, incidentally the brownish Heron wallpaper should show up again, for instance. Obviously you wont notice if you haven't customized your desktop at all since the Ubuntu installation.

To avoid this from happening, 'nautilus' can be started with the "--no-desktop" flag.

---

### Post by alex199020 on 2008-07-31
> **jonian_g said:**
> You don't have to install the nvidia drivers manualy. To get the latest drivers open a terminal and type:

```
sudo apt-get install envyng-gtk
```

Then go to Applications>System tools>EnvyNG and install the driver only with a few clicks.

I did this but i keeps saying 

> alex@alex-desktop:~$ sudo apt-get install envyng-gtk
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng-gtk


I can't find it in synaptic either. Is there a simple solution or should i just find a download and install it manually?
Thanks

---

### Post by RuleMaker on 2008-07-31
It probably happens because you have disabled you repos. Go to System->Administration->Software Sources->Ubuntu software (tab) and make sure that all options are checked.
Then in terminal type:
```
sudo apt-get update
```
And finally install drivers:
```
sudo apt-get install envyng-gtk
```

---

### Post by alex199020 on 2008-07-31
Well everything was checked. Maybe it was the update as i have some waiting to download. Thanks for the help :D Should be 90% linux anyday now :D

---

### Post by billgoldberg on 2008-07-31
> **northern lights said:**
> Although I'd generally advise against opening a filemanager as root, if it must be done, nautilus should be opened as such ```
gksu 'nautilus --no-desktop'
```Since nautilus also draws the desktop running "gksu nautilus" will result in having root's desktop drawn.

True.

Try doing 'gksudo nautilus' or even 'nautilus' in fluxbox.

---

### Post by caljohnsmith on 2008-07-31
> **northern lights said:**
> The application 'nautilus' is not just a filemanager but, in gnome environments also responsible for drawing the desktop to the root (don't confuse with superuser) of the screen.

When you run it with 'gksu', you do not only gain root privileges, but also open the application with root's (here i mean the superuser) preferences. Hence, the root's desktop will be drawn.

Since you generally can't login from the root account and thus you also can't have changed the root's preferences, incidentally the brownish Heron wallpaper should show up again, for instance. Obviously you wont notice if you haven't customized your desktop at all since the Ubuntu installation.

To avoid this from happening, 'nautilus' can be started with the "--no-desktop" flag.
I've never noticed this behavior before with "gksu nautilus", and even though I understand what you are saying, I tried it out just now to see for myself; my wallpaper is not the default brown themed picture, and when I ran "gksu nautilus" my desktop didn't change at all, including the icons on my desktop (and since some of the icons are files in my ~/Desktop directory, it seems my desktop was not changed to /root/Desktop). 

In the nautilus man page, it says:
```
--no-desktop
Do not manage the desktop — ignore the preference set in the preferences dialog.
```
And when I go to Edit > Preferences in Nautilus, I don't see anything about changing the wallpaper. So am I missing something here?

---

