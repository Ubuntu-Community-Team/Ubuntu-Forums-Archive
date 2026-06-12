---
title: "Dia CAD problem(s)"
date: 2008-08-03
forum: General Help
---

### Post by arvevans on 2008-08-03
The drawing program "dia" appears to have some problems.  User provided configurations do not work and Sheets and Objects screen persists when it is not wanted.

When I launch "dia" it always brings up the "Sheets and Objects" editing screen, even though I don't want to edit Sheets and Objects files.

User customized configuration options (page size, page orientation, etc.) do not stay across subsequent invocations of the program.

[INDENT]arv@arv-desktop:~$ which dia
/usr/bin/dia
arv@arv-desktop:~$ dia
sys:1: GtkWarning: Unable to parse accelerator '<control>10' for action 'FileRecent_9'
sys:1: GtkWarning: Unable to parse accelerator '<control>11' for action 'FileRecent_10'
sys:1: GtkWarning: Unable to parse accelerator '<control>12' for action 'FileRecent_11'
sys:1: GtkWarning: Unable to parse accelerator '<control>13' for action 'FileRecent_12'
sys:1: GtkWarning: Unable to parse accelerator '<control>14' for action 'FileRecent_13'
sys:1: GtkWarning: Unable to parse accelerator '<control>15' for action 'FileRecent_14'
sys:1: GtkWarning: Unable to parse accelerator '<control>16' for action 'FileRecent_15'
[/INDENT]

This seems to indicate that dia is having trouble using some history file, but I cannot find which one is the problem.  A couple of years ago I used dia extensively on SUSE with no problems, but have never been able to make it work properly on Ubuntu with the Gnome desktop.

Are there any "dia experts" out there who can get me started toward solving these problems with this otherwise interesting and very usable program?

I am running dia with Ubuntu 8.04 (64 bit) Gnome on a dual-core AMD-64 with 1 GB RAM

Arv
_._

---

### Post by arvevans on 2008-08-21
Still broken...
Is it that I am the only one using Dia, or is it that the problem is not fixable?
_._

---

### Post by arvevans on 2008-12-14
Now running Ubuntu 8.10, and the problem is still a problem.

[LIST=1]
[*]It seems that the prior session "Preferences" setup in dia is being ignored when the program is launched.

[*]Once you have accessed the "Sheets and Objects" page, it always comes up when you launch dia, and has to be killed before you can procede with using dia.
[/LIST]

Screenshot showing the problem(s):
[IMG]http://arvid.evans.googlepages.com/Dia_CAD_Problem_Screenshot.png/Dia_CAD_Problem_Screenshot-large.png[/IMG]

---

### Post by arvevans on 2008-12-29
Bump

---

