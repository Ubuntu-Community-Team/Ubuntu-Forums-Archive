---
title: "S.O.S. I'm Kindly Requesting Assistance With A Terminal Command..."
date: 2008-11-15
forum: General Help
---

### Post by Unixilandia0110 on 2008-11-15
Greetings to all. I recently installed Ubuntu Home Studio onto an older Dell Dimension 4300 Desktop, and was careful recording the password and user name used. All went well during the install, except when I tried to log in. The machine would not take my password, but instead opened up this prompt: root@ubuntu:~#  
    ??? I tried a few things including my password, but to no avail What command should I input there? Any assistance would be greatly appreciated. Warm regards to all here. Thank you.

---

### Post by oldos2er on 2008-11-15
According to this, root@ubuntu:~#, you're logged in as root.

---

### Post by wildrussian on 2008-11-15
Im not a linux wiz but that means that you are already logged in as  root. Did you not install the desktop environment?

---

### Post by Unixilandia0110 on 2008-11-15
Thank you both for this info. Yes, I installed as Desktop, and if I'm already logged in as root, how do I get the system to run? Thanking you both for your assistance!

---

### Post by Unixilandia0110 on 2008-11-15
For WildRussian: During the install for Home Studio (Ubuntu), I selected the type of programs I wanted to use, and I checked off: "Desktop", However I'm not sure now if I need to "activate" or "jump start" the actual running install of that desktop with some type of Terminal Command. (?)
    I've been using Ubuntu on this older Compaq Presario 2100 laptop for about 15 months, and it has truly been an awesome experience, I'm not looking back to M.S. XP. I see Linux as a sort "VIAGRA" O.S. for older computers, it energizes them, and gives them more power, stability, and "Satisfaction Is Guaranteed", or your M.S. Window Headaches Back! :) The Best part is you NEVER SEE BLUE! :)
     I'm staying with Linux, in fact the reason I installed Home Studio on the Dell Dimension 4300 desktop is to practice with some 25 or so Linux distros I've downloaded and burned to cd, or dvd over the last few months. I want to learn more about Linux! I intend to get books or videos relating to the terminal or command line, but for now, I just want to be able to use the Dell with Home Studio to get to know the distros. Thanking you all in advance for your generous help!
P.S. THanking ODOS2ER (Ms. Ann as well!)

---

### Post by amauk on 2008-11-15
when you say "The machine would not take my password"
bear in mind the password prompt will not echo back anything you type (either readable characters or asterisks)

This is a security measure so noone can guess your password (Ie. see the number of characters)

If you get a user@machine: prompt, you are logged in

---

### Post by oldos2er on 2008-11-15
I don't know anything about Ubuntu Home Studio; but you don't want to be permanently logged in as root on any Linux distro.

---

### Post by amauk on 2008-11-15
> **oldos2er said:**
> I don't know anything about Ubuntu Home Studio; but you don't want to be permanently logged in as root on any Linux distro.
a few distros (particularly light-weight ones) work this way when first installing

they'll install the bear minimum and dump you into single user mode (Ie. one user - root).  From there, there's a post install process to setup users, extra programs, possibly a GUI etc.

not that elegant (and largely a throwback from floppy disk installs), but it does save space on the install medium

---

### Post by |Porsche on 2008-11-15
Did you try:

```
gnome-session
```
 at the prompt?

---

### Post by wildrussian on 2008-11-15
Im not sure if this works for Ubuntu but try typing startx when you get that root login.

---

### Post by Unixilandia0110 on 2008-11-15
I'd like to thank Amauk, OldOS2er, WildRussian, and Littlebat, and Porsche for their input regarding my query, I'll try your good suggestions. Many thanks, and I hope your all enjoying your weekend. People here are very knowlegable and friendly, that always helps. "It's nice to be important, but it's more important to be nice"! Warm regards to all....Unixilandia0110

---

