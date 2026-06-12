---
title: "i need some help..."
date: 2008-09-23
forum: General Help
---

### Post by klambert on 2008-09-23
i'm really sorry, i know this is probably in the completely wrong place, but you guys usually offer me good advice and have helped me through some stuff before.  I kind of have a unique problem that no one has encountered before.. But here is where i am at with my linux...somehow (a long time ago) i messed with something and i can no longer access my bios.  On the startup screen i can either press tab to goto a post menu or i can press alt+f2 to go to an ez-flash utility (which i have not figured out yet because it tells me to insert some disk). and then from there it comes up to what im guess is the windows boot manager (its either that or grub because i remember at one point i tryed installing grub but i do not remember if i succesfully did it or not.  Anyway, before a few minutes ago, after the main motherboard startup screen it would go to that boot manager and give me two choices, either windows xp home edition or linux (i dont know why the linux option is on there i have never successfully installed it on this computer).  so i went into a boot.ini file inside my C: drive and took out the linux option, now my computer skips that screen and goes right into windows (though i think it takes it longer than it should, like its thinking about something) other than messing with that i do not know what could have cause me to not be able to pull up my bios, if anyone could help me that would be greatly appreciated.

---

### Post by HittingSmoke on 2008-09-23
> **klambert said:**
> i'm really sorry, i know this is probably in the completely wrong place, but you guys usually offer me good advice and have helped me through some stuff before.  I kind of have a unique problem that no one has encountered before.. But here is where i am at with my linux...somehow (a long time ago) i messed with something and i can no longer access my bios.  On the startup screen i can either press tab to goto a post menu or i can press alt+f2 to go to an ez-flash utility (which i have not figured out yet because it tells me to insert some disk). and then from there it comes up to what im guess is the windows boot manager (its either that or grub because i remember at one point i tryed installing grub but i do not remember if i succesfully did it or not.  Anyway, before a few minutes ago, after the main motherboard startup screen it would go to that boot manager and give me two choices, either windows xp home edition or linux (i dont know why the linux option is on there i have never successfully installed it on this computer).  so i went into a boot.ini file inside my C: drive and took out the linux option, now my computer skips that screen and goes right into windows (though i think it takes it longer than it should, like its thinking about something) other than messing with that i do not know what could have cause me to not be able to pull up my bios, if anyone could help me that would be greatly appreciated.

For the BIOS problem what you need to do is go to your mobo manufacturer's web site and download the appropriate BIOS image for your model. Save that to a floppy disk or (if your board supports it) a flash drive. You'll most likely have to dig up a floppy somewhere. Start the ez-flash program and insert the floppy you saved the BIOS image to. (thats the disk it's asking you for)

It sounds to me like someone did an unsuccessful flash on your BIOS or it became corrupted via other means. DONT, and I cant stress this enough, DONT turn your computer off after inserting the floppy disk with the BIOS on it until it tells you its safe to do so, you could completely hose your mobo and have to either get a new one or order a new chip from the manufacturer provided yours is swappable.

---

### Post by klambert on 2008-09-23
yea this is what im too i had to go dig up an old floppy drive and install it and im about to updatte or flash or whatever to the bios and hopefully that will fix me

---

### Post by klambert on 2008-09-23
ok i tryed that i did everything that asus said to do step by step and i wanna say i have the right bios file but it told me that it doesnt match with the motherboard...any suggestions?

---

### Post by HangMan101 on 2008-09-23
Well lucky you...

Windows boot mangers (or any other manager) has nothing to do with you accessing your BIOS.

if you have some overlay image displayed instead of the memory/disk information. it could be that you have enabled this image overlay within the bios the last time it was accessed.
Many pc manufacturers have this setting on by default(And sometimes disallow disabling). BIOS's then show a key to make the image disappear. 

then all the information should appear and information to enter the BIOS
(like in your case i would try TAB. because that information show is sometimes called "POST menu")

(in case that you have a BIOS with pci/apg support for vga and it test the wrong one first)
you may need to reboot your pc and press the tab key before you can even see something  (just hit the tab key a few times in a row)

---

### Post by klambert on 2008-09-23
ok well here's where im at, i start ujp...i press tab continually  (and it does say press tab for [POST] menu ) and it just ignores me pressing the button

EDIT: every now and then it goes to another screen but only stays there for a second then moves on

---

### Post by HangMan101 on 2008-09-23
likly is that pushing the tab key in your case a 2e time make the image reappear (from your flashing text appearance) try it a bit more carefull with hitting and give it some time to make the image disappear

(if you are sure it responsds to you keyboard)
you could try to make the bios reset (look it up in the manual)
this will make the bios FAIL at boot and load factory defaults.
and report to the user that something is not right at boot (image does not load)

EDIT:
You could also try to preas Pause/break key on the keyboard after you used tab (tricky becouse it will freeze boot and you can make it resume with return key)

---

### Post by klambert on 2008-09-24
appreciate the help, i'm onto trying to load ubuntu

---

### Post by zxscooby on 2008-09-24
delete or f1 can also bring up the bios.

---

