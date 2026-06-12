---
title: "Connect to Brother MFC-490CW Wirelessly"
date: 2008-11-28
forum: General Help
---

### Post by monsieurdozier on 2008-11-28
I just installed a MFC-490CW All in One Printer on my wireless network and I'm trying to connect to it through my Ubuntu Laptop.

I can find all kinds of documentation to set it up through a USB port.  But how can I set up my printer on Ubuntu through the wireless network.

I can detect it with no ease, it's just finding and using the right drivers.

Ubuntu 8.04.

-Monsieur Dozier

---

### Post by plucky on 2008-11-28
Your printer drivers are not packaged in synaptic,so you will have to download them from the [Brother website](http://solutions.brother.com/linux/en_us/index.html).

You will need the .deb packages for the LPR and Cupswrapper drivers.The website also has installation instructions.


Good Luck

---

### Post by monsieurdozier on 2008-11-29
I have the lpr driver setup as far as I can tell, but this is what I get when I try to set up the cups driver.

sudo dpkg -i --force-all --force-architecture cupsdriver.deb
(Reading database ... 144989 files and directories currently installed.)
Preparing to replace cupswrappermfc5440cn 1.0.2-3 (using cupsdriver.deb) ...
Unpacking replacement cupswrappermfc5440cn ...
Setting up cupswrappermfc5440cn (1.0.2-3) ...

 ****** ERROR: csh is required. ******

These are the instructions that I am following.

[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

-Monsieur Dozier


SOLVED

Had to install tcsh.  Works just fine.

---

### Post by narcoclepsy on 2008-11-30
I have the same printer, Ubuntu 8.1 and I am having some trouble... do you have your printer set up as static, dhcp, or bootp? I think therein lies my problem. Please advise- Thanks-

---

### Post by scottac on 2008-12-11
> **monsieurdozier said:**
> I 

SOLVED

Had to install tcsh.  Works just fine.

very new to linux...  What is tcsh?

---

### Post by plucky on 2008-12-12
> **scottac said:**
> very new to linux...  What is tcsh?

> TENEX C Shell, an enhanced version of Berkeley csh
The TENEX C Shell is an enhanced version of the Berkeley Unix C shell.
It includes all features of 4.4BSD C shell, plus a command-line editor,
programmable word completion, spelling correction and more. The tcsh
homepage can be found at [http://www.tcsh.org/Home](http://www.tcsh.org/Home).

Homepage: [http://www.tcsh.org/](http://www.tcsh.org/)

To install it open a terminal and ```
sudo apt-get install tcsh
```

Or use the **Synaptic Package Manager**

Good Luck

---

### Post by PakeJow on 2011-09-17
ubuntu is a humbling experience...
so ive been digging around for the past hour trying to get my MFC-490cw to print wirelessly, and ive installed(successfully i think) all the correct drivers. but the "printers" menu is telling me "it may not be connected" and it isnt printing any test pages,
so anyone have the free few minutes to help out a poor newbie?

thanks,

Pake.

---

