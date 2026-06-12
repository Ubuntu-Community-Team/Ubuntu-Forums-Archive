---
title: "Keyboard problem"
date: 2011-04-27
forum: Hardware
---

### Post by thunderbirdje on 2011-04-27
Hi everyone,

Since last week I have a strange keyboard behavior problem on my laptop.

Sometimes none of the keys work anymore. This include the touchpad and mouse buttons. The external connected mouse still works: you can move the pointer and left click. However the taskbar doesn't open: like clicking the ubuntu logo or ever other menu item (you can see the hovering change in the menu's) nor the 'shutdown' button.

After a while I noticed that this behavior starts when I press the enable/disable button on the touchpad or plug out the external mouse. Both events trigger the above behavior.

It's very annoying because the the only solution is to press and hold the power button and reboot the laptop.

Hope someone can help me (maybe I can even reinstall some packages?).

Thank you!

> Ubuntu version 10.10
Gnome version 2.32.0 / Build Date 9/27/2010

---

### Post by KegHead on 2011-04-27
Hi!

Have you gone to:

system...preferences...mouse

KegHead

---

### Post by thunderbirdje on 2011-04-27
> **KegHead said:**
> Hi!

Have you gone to:

system...preferences...mouse

KegHead
@KegHead: Yes, everything normal there, no fancy things set up. Maybe it's interesting to know when the keyboard doesn't work nor can click any of the taskbar's menu open I still can launch programs from shortcuts or click on like the menu File of OpenOffice Writer is open... :-) So the behavior is rather selective (like Gnome-related?)

---

### Post by KegHead on 2011-04-27
Hi!

I just updated my gnome.

sudo apt-get update

sudo apt-get install gnome

Maybe this will help you1

KegHead

---

### Post by thunderbirdje on 2011-04-27
Thank you so far KegHead.

I seems to have broken packages. I know there are a lot of fixes 'on the internet' but I rather feel safe to ask (given that I've already have the keyboard situation ;-))

```
~$ sudo apt-get install gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages

```

Edit: the Update Manager pops up as well showing 44 updates... I didn't press anything (yet ;-))

---

### Post by KegHead on 2011-04-27
Hi!

The updates will help you and are safe.

KegHead

---

### Post by Blasphemist on 2011-04-27
This may or may not have anything to do with your original issue but, to fix the broken packages you can run synaptic package manager, edit menu, fix broken packages.

---

### Post by thunderbirdje on 2011-04-28
@KegHead & Blasphemist: Thank you for your advice. I will test it out and keep you up to date! :D

---

### Post by thunderbirdje on 2011-04-28
Bad news: problem still exists

@KegHead: I've tried "sudo apt-get update" & "_sudo apt-get install gnome_. Same error message: "The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
_E: Broken packages_"

Then I tried "**Synaptic Package manager**" (did a reload) and Synaptic is saying: **0 broken packages.**

I've no idea why. Checked it twice.

If it narrow the search: on the login screen works everything perfect, when I turn of the touchpad or on, or unplug the external mouse the keyboard still works. I am also able to enable the touchpad again and use it to move the mouse cursor.

---

### Post by KegHead on 2011-04-28
Hi!

Try:

sudo apt-get update

sudo apt-get install gnome -f

KegHead

---

### Post by thunderbirdje on 2011-04-28
Hi KegHead,

"apt-get" seems still to complain about the broken packages:

```
~$ sudo apt-get install gnome -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome : Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages
```

---

### Post by KegHead on 2011-04-28
Hmm,

Try;

sudo apt-get update

sudo aptitude install gnome -f

KegHead

---

### Post by Blasphemist on 2011-04-28
Quite strange. It seems like it is a stretch to link gnome to your issue with the keyboard but you've done good to be able to notice what has just been done when this happens.

Swfdec-mozilla is a dummy package for transition to browser-plugin-gnash, a flash media player plugin. I see in synaptic that it can be safely removed when browser-plugin-gnash is installed.

Do you have firefox installed? Do you have the gnash plugin installed? I'd install them if you don't now.

[http://en.wikipedia.org/wiki/Gnash](http://en.wikipedia.org/wiki/Gnash)

---

### Post by thunderbirdje on 2011-04-29
> **Blasphemist said:**
> Quite strange. It seems like it is a stretch to link gnome to your issue with the keyboard but you've done good to be able to notice what has just been done when this happens.

Swfdec-mozilla is a dummy package for transition to browser-plugin-gnash, a flash media player plugin. I see in synaptic that it can be safely removed when browser-plugin-gnash is installed.

Do you have firefox installed? Do you have the gnash plugin installed? I'd install them if you don't now.

[http://en.wikipedia.org/wiki/Gnash](http://en.wikipedia.org/wiki/Gnash)

@Blasphemist: thank you so much, I'll check it out.

In meanwhile I discovered it was [a bug in 10.04 which still exists in 10.10 (link)]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404")

By trying [one of the comments (link)]("https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/542404/comments/4") although I kept to end up in the same broken package loop (swfdec-mozilla <-> epiphany-extensions) the strange behavior of the keyboard seems to be disappeared while the broken package still remains.

Hence I still can't install the package "gnome", "gnome-desktop-environment" is installed, is this ok as well?

I will test the keyboard/mouse more these days and keep this post up to date. :)

Thank you for the testing compliment ;-)

---

