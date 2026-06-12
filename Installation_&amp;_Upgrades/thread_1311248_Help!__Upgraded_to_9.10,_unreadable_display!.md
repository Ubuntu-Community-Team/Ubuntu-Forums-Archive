---
title: "Help!  Upgraded to 9.10, unreadable display!"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by hughh on 2009-11-02
[IMG]http://ubuntuforums.org/e:%5CMy%20Documents%5Cubuntu%209.10%20screen%20shot.png[/IMG]After upgrading from 9.04 to 9.10, I am unable to read most stuff on the display.  Am I missing a font or something?

[IMG]http://img.photobucket.com/albums/v280/hughh/ubuntu910screenshot.png[/IMG]

Any help or suggestions would be most welcome!

---

### Post by ManiacDan on 2009-11-02
When you're on the login menu about to enter your password, check the bottom of the screen to see if you have the correct language selected.  You may have a non-latin language selected, which would display those error characters without the appropriate language pack.

-Dan

---

### Post by hughh on 2009-11-02
Everything on the login screen is made up of the same error characters!

---

### Post by ManiacDan on 2009-11-02
Hrm...That IS a problem.  When I booted into 9.1 for the first time it asked me to download a language pack.  Try guessing at the "next" button.

-Dan

---

### Post by hughh on 2009-11-02
Still not having any luck.  I stumbled into installing an English language pack, but that didn't help.  I get a login screen with a login window in the middle.  It displays a monitor icon, under which are six unreadable characters:



("KARMIC"?). Below this there's a icon of the upper part of a human body with some characters to the right of it:



(the exact right number for my full name) and another set of characters on a separate line below it:



There is a red power button icon in the lower right corner.  Clicking it gives me four options:






I think these are "SUSPEND", "HIBERNATE", "RESTART" and "SHUT DOWN" respectively.  Immediately to the left of this icon is 20 characters of unreadable text:



Immediate to the left of this text is an blue icon with a Michelangelo-style human being.  When I click on it, I get a dialog box titled 



with a menu of eight check-box options:

__
__
__
__
__
__
__
__

(should be a total of 55 characters for the sixth option) and a button marked

__

("START"?)

Check the first option gives me a keyboard window in the upper left corner of the display.  Clicking the third option turns the right half of the display into a magnified version of the display with a cursor arrow in the center.  I can move the magnified version around with my mouse and select & deselect items by position the items under the magnified cursor arrow and clicking the left mouse key.

Will any of these options help me get started?

For the first few times when I logged in, I got what appeared to be choices for "LANGUAGE", "KEYBOARD" and "SESSIONS" (I'm guessing this based on what I see in [this image]("http://www.ubuntugeek.com/images/u910/17.png")), but now all I'm getting is a naked 80x24 terminal sessions.  (By naked, I mean no border for increasing the size, no buttons for maximizing, minimizing or closing the window, etc.)  I'm not sure if this is a helpful step or a step in the wrong direction.

:(

---

### Post by ManiacDan on 2009-11-02
Maybe [this]("http://www.linuxnewbieguide.org/userfiles/gdm-menus-3.png") will help.

-Dan

---

### Post by hughh on 2009-11-02
Yes, I already looked at that.  It doesn't seem to help.   :(

---

### Post by Dougie187 on 2009-11-02
Not sure if this would help or not, but you could try it anyways.

At the login screen, instead of trying to log in, press CTRL+ALT+F1, this will drop you to a terminal, so log in here, and then type
```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install lang-support-en
```

I would have thought this package would have been installed by default, but maybe something went wrong with your upgrade.

---

### Post by hughh on 2009-11-02
I assume you meant:

```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install lang_uage_-support-en
```But it didn't help.  Still getting unreadable text.

---

### Post by Dougie187 on 2009-11-02
> **hughh said:**
> I assume you meant:

```
sudo apt-get update 
sudo apt-get upgrade
sudo apt-get install lang_uage_-support-en
```But it didn't help.  Still getting unreadable text.

Did it do anything? and yeah, the package is language, sorry.

You could try these packages if it tried to install, but I don't know if it will really do anything. If you want to see if it's installed, it should say something like package is already installed at the end of the ```
sudo apt-get install *packagename*
```
or you could do
```
apt-cache policy *packagename*
```
So, here are the package names.
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base

If those don't work, and noone else has any ideas, I would personally recommend a fresh install, because you did an upgrade to get to this point right?

---

### Post by hughh on 2009-11-03
> **Dougie187 said:**
> Did it do anything? and yeah, the package is language, sorry.

No, they and the packages listed below were already installed.

> **Dougie187 said:**
> You could try these packages if it tried to install, but I don't know if it will really do anything. If you want to see if it's installed, it should say something like package is already installed at the end of the ```
sudo apt-get install *packagename*
```or you could do
```
apt-cache policy *packagename*
```So, here are the package names.
language-pack-en
language-pack-en-base
language-pack-gnome-en
language-pack-gnome-en-base

If those don't work, and noone else has any ideas, I would personally recommend a fresh install, because you did an upgrade to get to this point right?

Yes, I did do an upgrade, from 9.04.  I'm not quite ready to do a fresh install.  Apparently one of my login options is to login to the KDE desktop.  When I do so, I generally don't see these unreadable characters, though I do see some.  I'm assuming therefore, that I have a Gnome problem.  I'm thinking maybe if I burn a CD with 9.10 and boot from it, I can figure out what's wrong.

I appreciate the help from both of you and welcome any other suggestions your or others may have.

---

### Post by ManiacDan on 2009-11-04
You can boot to a liveCD, enter a terminal, mount your existing ubuntu partition, chroot to it, then update/verify all your packages to see if anything is missing.  THat might be your best option.

Why do you have both gnome and kde installed?

-Dan

---

### Post by hughh on 2009-11-04
> **ManiacDan said:**
> You can boot to a liveCD, enter a terminal, mount your existing ubuntu partition, chroot to it, then update/verify all your packages to see if anything is missing.  THat might be your best option.

Yeah, that's exactly what I did.  Eventually I realized that many of my font files were only readable by root.  When I chmod'ed them to be readable by all, that did the trick!  Now I can read EVERYTHING.

> **ManiacDan said:**
> Why do you have both gnome and kde installed?

Certain applications I want to run only run under one or the other.

---

### Post by hughh on 2009-11-05
> **hughh said:**
> 
[quote=ManiacDan;8240942]Why do you have both gnome and kde installed?
Certain applications I want to run only run under one or the other.[/quote]

Actually, this is not true.  My applications all pretty much run under either, of course.  Upon further reflection, I'd say I installed both because I wanted to be familiar with both GUIs.

---

### Post by ManiacDan on 2009-11-05
It took me nearly a minute to figure out you were disagreeing with YOURSELF.

Anyway, good for you for trying to learn both environments, but keep in mind that two Gnome installs can be as different as Mac and Windows because of the ridiculous plugins they have.  I would stick with the one you like the best so you don't have the possibility of two desktop environments causing this kind of trouble.

-Dan

---

