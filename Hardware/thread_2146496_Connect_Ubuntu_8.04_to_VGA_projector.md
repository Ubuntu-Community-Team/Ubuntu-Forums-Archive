---
title: "Connect Ubuntu 8.04 to VGA projector"
date: 2013-05-18
forum: Hardware
---

### Post by Hekabe on 2013-05-18
Alright, here's my issue. I have a fairly old laptop, a 2006 Dell Latitude D610, running Ubuntu 8.04. I need to connect a projector to it through a VGA connection and use it for presentations. It's in a dock, and the original laptop screen is broken, so it's plugged in through the dock to a DVI monitor. The actual VGA cord is certified working. When I connect the cord to the VGA port, it doesn't autoconnect, and it can't detect it in the monitor settings GUI. Any ideas?

---

### Post by ajgreeny on 2013-05-18
Perhaps there is a function key (Fn) which together with one of the F# switches the graphic output from normal to external.

That is what I have on my old Acer laptop, though I suppose your docking station may mean everything is different on yours.

---

### Post by mörgæs on 2013-05-18
As a first step you should do a fresh install of one of the recent Buntus as a) 8.04 does not receive security updates any more and b) the bug might be fixed in a later release.

---

### Post by Hekabe on 2013-05-18
I'm doing an upgrade to 10.04 as we speak, actually. As for the choice question, I needed an LTS, and 8.04 was the newest distro in which the installer didn't have some error or other (Ubuntu 10.04 installation hung in the middle, twice.) As for the function key idea, I hadn't thought of that.

---

### Post by cortman on 2013-05-18
Actually 10.04 is EOL as well. Use 12.04 for an LTS.
On a laptop that old installing regular Ubuntu is going to be agonizingly slow. Do give Lubuntu (or if you prefer) Xubuntu a try. I'm rather partial to Lubuntu myself.

---

### Post by Hekabe on 2013-05-19
Update on the installation situation. Normal Ubuntu 10.04 installation hung with CPU lockup errors. Since there's about 90 GB worth of files on here I need it'd be a pain to do a clean install of xubuntu 10. 04 from here, so I'm stuck with 8.04 unless there's a way for me to do an upgrade direct from vanilla to Xubuntu. As for the 12.04, no way that would run on a Pentium M.

---

### Post by sudodus on 2013-05-19
> **Hekabe said:**
> Update on the installation situation. Normal Ubuntu 10.04 installation hung with CPU lockup errors. Since there's about 90 GB worth of files on here I need it'd be a pain to do a clean install of xubuntu 10. 04 from here, so I'm stuck with 8.04 unless there's a way for me to do an upgrade direct from vanilla to Xubuntu. [COLOR=#008000]As for the 12.04, no way that would run on a Pentium M[/COLOR].

I run Lubuntu 12.04.2 in an IBM Thinkpad T42 and it runs really well :-)

I have also developed a special work-around, 'Lubuntu-fake-PAE', to make the brand new Lubuntu 13.04 work in laptops with Pentium M and Celeron M CPUs. This way you can run a pae kernel with your Pentium M CPU.

See this link [https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

Anyway, I suggest that you backup all your personal files (documents, pictures, mailbox files ...) and make a fresh install of Lubuntu or Xubuntu. Select the version with some consideration:

- Xubuntu 12.04.2 LTS with end of life April 2015 (with non-pae kernel)

- Lubuntu 12.04 with end of life October 2013 (with non-pae kernel)

- Lubuntu-fake-PAE 13.04 with end of life January 2014, and it can be upgraded to 13.10 after October (or you make a new fresh install).

It is a good idea to have a ***separate data partition*** with all (or most) personal files. This means that the /home directory or partition can be easlly replaced if necessary. Another option is to keep a /home partition and make a fresh install of the root partition (/).

---

### Post by Hekabe on 2013-05-19
I tried installing Xubuntu and Lubuntu 12.04 fresh when I first got the laptop, but neither of them worked, I forget what errors it gave me. I'll try the fake-PAE though, thanks for the tip.

---

### Post by sudodus on 2013-05-19
If you still have the iso files (or CD disks) with Xubuntu and Lubuntu 12.04, please try again and describe the result. It might be easy to solve that problem with some help via this forum.

And I'll be glad to assist you, when you try fake-PAE.

Good luck :-)

---

### Post by sudodus on 2013-05-19
Does your Dell Latitude D610 fit with the following description?

CPU: Pentium M 760 (2.00Ghz w/ 533Mhz FSB)
RAM: 512 MB

according to this link [http://www.notebookreview.com/default.asp?newsID=2268](http://www.notebookreview.com/default.asp?newsID=2268)

In this case the CPU probably has a pae flag, and should be able to run without fake-PAE. But I am not sure about that.

---

