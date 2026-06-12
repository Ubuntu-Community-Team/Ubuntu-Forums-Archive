---
title: "Screen Resolution not cooperating"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by GmAz on 2007-10-23
Ok, I have a Gateway M255E laptop with integrated Intel video (950 chipset).  I know it runs 1280x800 and 1280x768 resolution since its a widescreen, but 7.10 won't let me run those.  Though they are an option for me to select, the Test button isn't useable and when I hit Okay, it tells me to logout and log back in.  When I do this, the resolution is still at 800x600.  I can get 1024x768, but I would like my wide screen.  Thanks!:KS

---

### Post by GmAz on 2007-10-23
Never mind.  I finally figured out how to get the 915resolution patch to install.  Actually, in finally figured out how to get it period.  Sorry, I am new to linux.  Put it off for sooo long, and finally heard that Gutsy is that much better.  We'll see I guess.  I also guess that no longer playing PC games helps too.  Anywho, the 915resolution patch worked great.  Got my resolution how I like it, got compiz to work too and its fun.  Anywho, if anyone else reads this and needs the 915resolution patch and has no idea how to do it, do this in the terminal:

sudo apt-get install 915resolution

Let it work its magic.  After it installs, which takes seconds, change your resolution in the System > Administration > Screens and Graphics settings, apply the settings and logout/login.  Worked great for me!  :KS

---

