---
title: "UBUNTU 7.04 Gnome Desktop does not install from Desktop CD"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by Nick1890 on 2007-07-14
On Packard Bell EasyNote E3 laptop UBUNTU LiveCD stops loading as Gnome desktop cannot be installed.
On same laptop KUBUNTU works fine.
Questions:
1. What's the reason?
2. Can I install the Gnome Desktop from within KUBUNTU (or will this result in the same fault rapport)?

---

### Post by merlinus on 2007-07-14
Try this:

```

sudo aptitude update && sudo aptitude install ubuntu-desktop

```-merlin

---

### Post by Nick1890 on 2007-07-14
Merlin, I'm unable to do that as the installation already "hangs" once the UBUNTU bar in the middle of the screen is displayed and a "certain chime" was heard. (The sound check???)

At that specific moment the bar contains 03 icons, the CDROM is continuously accessed but nothing happens. I broke off after 20 minutes.

CD is OK as it installs the whole business on another laptop within 04 minutes.

---

### Post by merlinus on 2007-07-14
Perhaps I am misunderstanding.  I thought you asked about being able to install ubuntu (gnome) from within kubuntu???

-merlin

---

### Post by Nick1890 on 2007-07-14
As loading KUBUNTU from a LiveCd on that same laptop functions 100%, it is my intention -- if NO solution can be found -- to:
1. install KUBUNTU as the sole OS on that laptop.
2. Change the KUbUNTU environment into an UBUNTU one from inside.

Nevertheless, it is a bizar phenomena... 

But that is most probably due to the fact that I am a newbe in the Linux world...

---

### Post by merlinus on 2007-07-14
It may be that the ubuntu live cd has errors, or your download is corrupted, and that is not the case with your kubuntu install cd.

You can check the cd for errors at the opening menu.

-merlin

---

### Post by w4ett on 2007-07-14
The simple answer to your question is yes.  My base installation here is Ubuntu, but I also have the XFCE (Xububtu Environment), KDE (KUbuntu) and Fluxbox on my machine.  All I did was do the base install the used apt-get to install the additional Desktop environments.....Upon login, I select the session I want from the options selection button.

I would surmise that a base install of KUbuntu, followed by sudo apt-get install gnome-desktop will do the same for you.

---

