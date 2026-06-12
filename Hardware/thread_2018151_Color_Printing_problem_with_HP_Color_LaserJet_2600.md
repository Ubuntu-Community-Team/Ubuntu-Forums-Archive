---
title: "Color Printing problem with HP Color LaserJet 2600n"
date: 2012-07-06
forum: Hardware
---

### Post by omiazad on 2012-07-06
Hi
I have a HP Color LaserJet 2600n on my network and printing is working fine since I have installed and using Ubuntu. Today I went to print a color document and found it's not printing in color.

Do you know any solution for this issue?

Regards
Omi

---

### Post by aniruddha.adhikary on 2012-07-16
Try installing "hplip-gui" and configuring printer options from their. Of course,  remove your printer from the "Printers" list before you do so.

---

### Post by omiazad on 2012-07-16
> **aniruddha.adhikary said:**
> Try installing "hplip-gui" and configuring printer options from their. Of course,  remove your printer from the "Printers" list before you do so.

Tried that. I can select color, but the output comes mono :(

---

### Post by ashickur.noor on 2012-07-17
Which kernel you are using?

---

### Post by omiazad on 2012-07-17
> **ashickur.noor said:**
> Which kernel you are using?
I don't know. How to check?

I'm on Ubuntu 12.04

---

### Post by Shadius on 2012-07-17
> **omiazad said:**
> I don't know. How to check?

I'm on Ubuntu 12.04

Run this code in Terminal:
```
uname -a
```

To open the Terminal, click on it from the Launcher or use keyboard shortcut ***Ctrl+Alt+T***.

---

### Post by omiazad on 2012-07-17
> **Shadius said:**
> Run this code in Terminal:
```
uname -a
```To open the Terminal, click on it from the Launcher or use keyboard shortcut ***Ctrl+Alt+T***.

Why?

You must understand the complication by the description I provided above. If you cannot, then you cannot reach end users. It's Ubuntu 12.04 and now the geeks should understand what is the things running behind, right?

---

### Post by Shadius on 2012-07-17
> **omiazad said:**
> Why?

You must understand the complication by the description I provided above. If you cannot, then you cannot reach end users. It's Ubuntu 12.04 and now the geeks should understand what is the things running behind, right?

You asked how to check what kernel you're using. I provided the answer. Whether you run the code to find out what you asked is your choice.

---

### Post by omiazad on 2012-07-17
> **Shadius said:**
> You asked how to check what kernel you're using. I provided the answer. Whether you run the code to find out what you asked is your choice.

Thanks a lot.

---

### Post by ethanay on 2012-10-02
> **omiazad said:**
> Thanks a lot.

Your comment seems to be to be a bit sarcastic and of bad taste.  I'm sorry you are experiencing issues with printing.  I found my way to this thread because I am experiencing issues with the same printer (there is apparently no driver in Lubuntu 12.04 by default??).

To answer your question, the version of Ubuntu only gives us a range of kernels that your system might be using.  In order to best help you, we need to know how up-to-date your system is, and the easiest way to tell is to see what kernel you are using and compare that version with teh most up-to-date version.  If you are using an older kernel, our first instructions will probably be to guide you through the update process.

Good luck!

---

