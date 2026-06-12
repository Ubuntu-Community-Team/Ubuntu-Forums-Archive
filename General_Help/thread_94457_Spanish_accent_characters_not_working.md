---
title: "Spanish accent characters not working"
date: 2005-11-24
forum: General Help
---

### Post by kairu0 on 2005-11-24
I need to type Spanish accents in Kubuntu, but I can't.

I'm using Kubuntu 5.10 with the following /etc/environment configuration:

LANGUAGE="es_US:es:en:ja_JP.UTF-8"
LC_ALL=es_US
LANG=es_US.UTF-8


In all QT applications I CAN'T to type Spanish accent characters (á é í, etc.) In all GTK applications I CAN type Spanish accent characters.

When I run KDE applications at the konsole, I get no errors. When I run GTK applications from konsole, I get told that my locale is not supported.

I have run "sudo dpkg-reconfigure locale" to install the es_US locale and checked that it exists by reading the locale.gen file.

Can anyone figure out what's wrong with my setup?

---

### Post by kairu0 on 2005-11-26
I have tried with Mepis and have not been able to reproduce this problem. Is this a Kubuntu-specific bug?

---

### Post by tseliot on 2005-11-27
[QUOTE=kairu0]I have tried with Mepis and have not been able to reproduce this problem. Is this a Kubuntu-specific bug?[/QUOTE]
It's not a bug. You have to switch between your keyboard layouts.

Open Konsole and type:
```
kcontrol
```
Click on "Regional & Accessibility"
Click on Keyboard Layout
Then, on the left, click on "Enable keyboard layouts"
Select the languages you need and press the "Add >>" button
Click on Apply
Then close the window.

Look at the system tray (Bottom right of the screen)
You will see a flag representing the keyboard layout related to your language.
Click on it to switch between the layouts you have chosen

---

### Post by kairu0 on 2005-11-27
I know how to use the keyboard layout selector in KDE. I have it set up with USA, JPN, and ESP layouts. I can use the USA and JPN layouts fine. The problem is that when I switch to ESP, most of the keys work (even ñ) but the key that produces the ' accent mark doesn't work. I can use the ESP layout fine in Mepis (also KDE) and Ubuntu.

---

### Post by tseliot on 2005-11-27
[QUOTE=kairu0]I know how to use the keyboard layout selector in KDE. I have it set up with USA, JPN, and ESP layouts. I can use the USA and JPN layouts fine. The problem is that when I switch to ESP, most of the keys work (even ñ) but the key that produces the ' accent mark doesn't work. I can use the ESP layout fine in Mepis (also KDE) and Ubuntu.[/QUOTE]

I haven't tried it in KDE (I'll do it in a minute) but in GNOME it works fine. I use the spanish layout too.

---

### Post by tseliot on 2005-11-27
It works ok in KDE. I have tried both "ñ" and accents e.g. Mérida

---

### Post by kairu0 on 2005-11-27
Hmmm. Well, I'm glad it's working for you! :)

Any idea how I could fix this?

By the way, when I type M&#233;rida, I get M'erida (because the accent key puts out the ' without waiting for the "e". When I type this in gnome using exactly the same keys, I get M&#233;rida.

---

### Post by tseliot on 2005-11-27
[QUOTE=kairu0]Hmmm. Well, I'm glad it's working for you! :)

Any idea how I could fix this?

By the way, when I type Mérida, I get M'erida (because the accent key puts out the ' without waiting for the "e". When I type this in gnome using exactly the same keys, I get Mérida.[/QUOTE]

Perhaps we have different keyboards (mine is Italian) but I put the accent by  pressing the following buttons:
à (which is the button 2 steps right of the L letter) then I type the letter I need to put the accent on.

Do you do it in this way?

---

### Post by kairu0 on 2005-11-27
I type it in exactly the same way. I have a Japanese keyboard, but I still push the key 2 keys to the right of "L", then a vowel.

---

### Post by tseliot on 2005-11-28
[QUOTE=kairu0]I type it in exactly the same way. I have a Japanese keyboard, but I still push the key 2 keys to the right of "L", then a vowel.[/QUOTE]

Make sure your system is up to date or file a bug in the Ubuntu Bugzilla

---

### Post by Topsiho on 2005-11-28
I had the same problem, and pinned it down to a corrupt xkeyboard file.

Installing a newer .deb file I found somewhere for xkeyboard fixed it.
(I deleted it, I am sorry)
Very recently, I think yesterday or the day before that there was also an update for xkeyboard, I forgot the exact name, but search for xkeyboard.

Just try and update the xkeyboard file with synaptic. I can not guarantee succes as I use the .deb file that I found elsewhere.

Gréétz,

Topsiho

---

### Post by kairu0 on 2005-11-28
Now we're getting somewhere! I'll try to pin down an updated .deb of xkeyboard. Thanks both of you!

---

### Post by kairu0 on 2005-12-29
I finally pinned down the problem to my LC_CTYPE environment variable. Setting it to ja_JP.UTF-8, which I thought I needed to use SCIM, broke my accent typing.

---

### Post by koki on 2005-12-29
[QUOTE=kairu0]I type it in exactly the same way. I have a Japanese keyboard, but I still push the key 2 keys to the right of "L", then a vowel.[/QUOTE]

If you have a Japanese (physical) keyboard, then the position of the accent keys and the ñ/Ñ may be different. Try different keys to see if you can find what you are looking for.

I use exactly the same config as you (Japanese IME, US and Esp keyboard layouts), except that I have a US keyboard, and this works fine in Gnome.

PS: Are you using the English version of Ubuntu? Have you tried Ubuntu-ja? It may be a better option for your case.

---

### Post by kairu0 on 2006-01-01
[QUOTE=koki]PS: Are you using the English version of Ubuntu? Have you tried Ubuntu-ja? It may be a better option for your case.[/QUOTE]

I'm actually using the Spanish version of Ubuntu.

The thing is that I have an Ubuntu/Kubuntu dual boot. I have absolutely no problem typing Japanese in Ubuntu because I use UIM. However, in Kubuntu, I cannot get SCIM to work for me. If there was a Kubuntu-ja, I would definitely be using it.

---

### Post by rpseng on 2006-04-21
[QUOTE=kairu0]I type it in exactly the same way. I have a Japanese keyboard, but I still push the key 2 keys to the right of "L", then a vowel.[/QUOTE]
Hi Kairu0,

Same problem here, all applications except the kde based work fine.
On kde apps I get 'e instead of é.
Have you found a solution?

PS. Using dapper beta.

---

