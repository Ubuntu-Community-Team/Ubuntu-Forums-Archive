---
title: "Ubuntu hardware requirements"
date: 2006-05-12
forum: Hardware &amp; Laptops
---

### Post by thhog on 2006-05-12
Some 25 years ago I was responsible for a couple uf Unix servers delivering office applications to employees in a swedish governmental agency. Today I am retired, helping friends with their various PC (Windows) problems and sometimes helping them with a PC. 

On recommendations from my son (sysadm in a municipal agency) I have installed Ubuntu 5.10 0n a Compaq 733Mhz/128MB/10GB and I am impressed. 

But...

X-Wíndows (Gnome) seems to be as slow and eat as much memory as it did 25 years ago. Trying to find some decent "hardware requirements table" on the Web, I have detected that answers still are given by those with a religious conviction: Microsoft Windows is the DEVILs work and Linux is GODs gift to humanity.

So I would like to have some hints from someone who knows that you can start XP and office applications about twice as fast as Ubuntu: How much extra memory (and ev processor speed) do I need to get even with XP (not to mention 98)?

And please remember: I believe that the extra hardware costs are substantially lower than the Microsoft license costs.

---

### Post by s0cket on 2006-05-12
I'm afraid that 128 megs of RAM is not enough memory for Gnome.  If you want to run a modern desktop environment (e.g. gnome, kde) I recommend at least 512 megs of RAM.

---

### Post by ZylGadis on 2006-05-12
I'd say you need to raise your RAM to 256, or even 512 - and it will fly. Gnome is a memory hog nowadays - less than KDE, but still one. It would also help to change the browser you use - the Firefox that comes with Breezy leaks a bit. Either install Opera, or install the new Firefox (there is a howto around), or install Dapper which comes with the new Firefox.
Alternatively, try XFCE, which is light and snappy (comparative to Gnome). You want to install the xubuntu-desktop package from Synaptic (it will pull everything else it needs), then logout and login to XFCE.
Last but not least, I had a 128MB PC, and Windows XP Service Pack 1 was **much** slower than Gnome.

---

### Post by mips on 2006-05-12
[QUOTE=ZylGadis]Gnome is a memory hog nowadays - less than KDE, but still one.[/QUOTE]

Hehe, prove it ! I tend to disagree.

Try a lighter windows or desktop manager. XFCE, Fluxbox, Window Maker etc will probably give you better results.

---

### Post by thhog on 2006-05-12
Hehe. You can´t. So why are you giving me (and probably many, many others) complete meaning-, use- and wittless aswers?

---

### Post by thhog on 2006-05-12
Do you have any idea about the impact of processor speed? As you can see, I suspect that it is all about memory. On the Gnome home page I read a short article indicating that Gnome professionals were well aware of the problems. Unfortunately they suspected that it was a much deeper problem: The current memory allocation software in Unix/Linux, requiring a total rewrite of malloc() and other kernel interfaces.

---

### Post by mips on 2006-05-12
Edit: Forgot to count to ten before replying. Retracting this post.

---

