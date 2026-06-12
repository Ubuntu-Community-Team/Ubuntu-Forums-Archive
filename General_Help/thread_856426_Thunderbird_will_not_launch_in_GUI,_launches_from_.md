---
title: "Thunderbird will not launch in GUI, launches from command line"
date: 2008-07-11
forum: General Help
---

### Post by support on 2008-07-11
After some searching here and on google, I cannot find anything that resembles my problems...

I have recently upgraded some workstations to Ubuntu 8.04 LTS from Ubuntu 6.06LTS. After upgrading, Thunderbird will not launch from the GUI (either from a shortcut on the panel or from >Applications>Internet>Mozilla Thunderbird Mail/News) but it will launch when you type #thunderbird in a terminal.

I need to have the regular GUI launching mechanisms working as many of my users are not savvy enough to know to launch the program from a terminal. Any ideas?

---

### Post by dracayr on 2008-07-11
will it also launch without being root??

dracayr

---

### Post by avtolle on 2008-07-11
When you right click the icon and select properties, what is shown in the box labeled "command"? Mine shows, IIRC, thunderbird%u.

---

### Post by support on 2008-07-11
dracayr: I do not need to be logged in as root, nor do I need to use sudo to launch Thunderbird from a terminal.

avtolle: Properties lists in the "Command" field, "thunderbird %u".

---

### Post by dracayr on 2008-07-11
> **support said:**
> dracayr: I do not need to be logged in as root, nor do I need to use sudo to launch Thunderbird from a terminal.


In that case I assume you type thunderbird into a terminal, not #thunderbird (as you wrote above), because the '#' char either indicates a root prompt, or a comment...

I use evolution, so I'm not sure, but do you need that %u??

dracayr

---

### Post by support on 2008-07-11
I am here using the # to represent the shell prompt (and in this case, I am not logged in as root), hence I type the following exactly to launch Thunderbird successfully from the terminal:

thunderbird


As for the "%u", it is the default when you create the shortcut from the Applications menu to the Panel. I did not put it there.

---

### Post by dracayr on 2008-07-11
I have absolutely no Idea why it isn't working, but I guess you could try using

bash -c "thunderbird &"

in the Command field

dracayr

---

### Post by support on 2008-07-11
That would work, however, I do not want for my users to have to open a terminal to launch Thunderbird.

---

### Post by dracayr on 2008-07-11
I meant typing 

bash -c "thunderbird &"
in the command field of the properties dialog of the icon. Without opening a terminal.

dracayr

---

### Post by support on 2008-07-11
Unfortunately, inputing the following into the Command field in the properties dialog box on the Launcher Panel icon for Mozilla Thunderbird did not solve the problem:

bash -c "thunderbird &"


Furthermore, this fix needs to be non-user specific. The above would require that each user login and do these commands to get their mail client working which is unacceptable. I need a global fix which applies to all users.

---

