---
title: "Stuck at &quot;Sun&quot; EULA on terminal"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by OxentroT on 2009-05-06
I have ran a few commands in my quest to get my apt- instalation and download attempts to run properly. I would paste said actions carried out within my terminal but it seems that I am stuck at a 'package configuration screen, configuring sun-java-6' unable to type or advance in any way.

Here is a summary of my actions entered into the terminal in order to address a 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem issue:
I ran:

```
sudo dpkg --configure -a
```

then

```
sudo apt-get update
followed by
sudo apt-get upgrade
```

According to the person who posted the technique I was supposed to be prompted for password after the first command. I was not, but everything seemed to run okay until I arrived to the sun configuration within my terminal.

---

### Post by kpkeerthi on 2009-05-06
Can you post a screenshot of 'sun configuration' screen ? (You should be able to scroll down and click on the OK button to accept the license agreement, if that is what you mean by 'configuration screen')

---

### Post by ibuclaw on 2009-05-06
Do the **Tab** and **Arrow-keys** work?

To memory, the arrow keys initially control the curses scrollbar, and you press tab to switch to the "**Accept**" or "**Decline**" buttons.

Regards
Iain

---

### Post by OxentroT on 2009-05-06
Thankyou for the responses to my issue.

[IMG]http://i730.photobucket.com/albums/ww309/oxentrot/sunfig.jpg[/IMG]

Here is a scrn shot. This is the bottom of the config I am able to scroll up and down and nothing else. It also seems that there is still a package manager running, would this be it? Is there a ways to view any package manager that may be running in the background?

---

### Post by Partyboi2 on 2009-05-06
Hi, you should be able to press the 'Tab' key which will highlight the 'ok', then you can  press enter to accept.

---

### Post by OxentroT on 2009-05-06
YES! Thankyou! I am now palming my forehead over yet another over-looked common sense should-have-know-to-do thing.
sometimes I think I have no business at this keyboard.
TAB worked of course and all is well with the Java.

Thankyou all for the help!
:-o

---

### Post by Partyboi2 on 2009-05-06
> **OxentroT said:**
> YES! Thankyou! I am now palming my forehead over yet another over-looked common sense should-have-know-to-do thing.
sometimes I think I have no business at this keyboard.
TAB worked of course and all is well with the Java.

Thankyou all for the help!
:-o
We all have those moments :P

---

### Post by sisco311 on 2009-05-06
Wow, the CLI interface is still the default. :(

Why not the Gnome one?
```
sudo dpkg-reconfigure -f gnome debconf
```

---

