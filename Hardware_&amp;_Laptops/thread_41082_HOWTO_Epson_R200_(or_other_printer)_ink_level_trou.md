---
title: "HOWTO: Epson R200 (or other printer) ink level troubleshooting"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by bahumbug on 2005-06-11
OK, the other day I wanted to print something and found that my R200 wouldn't print.  I realized that the low ink button was blinking so obviously I needed to changed the cartridge.

Problem is:  I HAVE NO IDEA WHAT CARTRIDGE...  normally (when i used to use windows) an epson application just popped up and told me which cartridge i had to replace.  But unfortunately in Linux, I had no idea which one it was.... and replacing all the cartridges would be extremely wasteful...  :???: 

SOOOOO.... I installed MTInk:

:$ **sudo apt-get install mtink**

THAT'S IT! HAHA.. but in order to access it, it complained about having permissions.  So i decided to add it to the gnome menu so it's more accessible:

If you don't have SMEG, you should get it, it helps with adding apps to the menu.. search the forum  :) 

Open up SMEG and under system tools or accessories (or wherever you want to put it) click on New Entry

Then, under name type in Command:
[B]gksudo mtink
press OK[/B]

Now just run it and it should detect your epson printer and now you can check your ink levels.

On a side note,  i don't know if there are better programs out there, but for now, this'll do.  I think I might try libinklevel and gmso or inkblot and compare them, maybe someone else can compare for me??  :-P 

PEACE

**EDIT**
HEHE, just realized that you don't actually need this, but it would be nice to know where your ink levels are.  in the r200 there should be a little plastic pointer when you lift the cover that tells you which ink cartridge is out(if any).

---

### Post by Carandol on 2006-04-16
Wow! The little plastic pointer! Why didn't I notice that before? And there was I thinking the printer was just being annoying and not putting the carriage in the right place to get the cartridge out. 

Still, the software will be useful for telling me which cartridge will run out next...

---

