---
title: "Vista partition not showing up under &quot;Places&quot;"
date: 2008-08-21
forum: General Help
---

### Post by imthe1onurmom on 2008-08-21
I haven't been able to mount my vista partition since I ran into a problem and had to recover my vista system

now in the boot menu it says....
"Windows Vista Home Premium (recovered)"

is this the problem???

and how can I fix it

can I go back to the original somehow.... please help...it really ticks me off

---

### Post by mr.moch on 2008-08-22
GRUB has nothing do do w/Ubuntu and Wubi itself.  It is a separate file, which is called wubildr.mbr.  Then, in C:\ubuntu\boot\grub (in windows, where C: is your drive), there is a file called menu.lst.  Open it up in notepad, or a text editor and you should be able to rename it to whatever you want.  Like in this case, "Windows Vista Home Premium".  That should rename it.

Your drive is probably mounted.  It should be in the host directory.  Do the following:

1. Alt+F2
2. /host
3. ENTER. 

You should see the hard drive contents.  Hope this helps!

---

### Post by imthe1onurmom on 2008-08-22
thanks so much
this works and it helps alot

I was wondering if you knew why it isn't under "places"
because I know when i had wubi B4 that it was....
but then after i had to recover my vista it no longer works...

I don't "need" it under places anymore but I would like it...
not only that but im one of those ppl that just want to know "why?"

thanks again for your reply...and solving my problem... but if you have anymore info please reply

---

