---
title: "CD/DVD burner with Lightscribe recommendation"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by tombiz on 2008-01-26
I need to get a new CD/DVD burner (old one broke). I plan on getting one either from Samsung or LITE-ONE.

I was wondering if anyone has these brands with Lightscribe support.

If not, can you recommend a brand wit Lightscribe support that works well with Ubuntu?

---

### Post by kyphi on 2008-01-26
For lightscribe you need two things:

1.  A machine capable of putting it into operation (Samsung or Lit-On are fine).
2.  A programme to run it (a driver).

If you google for "lightscribe for linux" you can find a LaCie driver for Linux.

---

### Post by getglenn on 2008-01-26
i have a lite-on SHM-165H6S and it burns lightscribe discs fine...

i use** lightscribe labelle**r for simple text disc labels [from lightscribe website]

and

**lacie 4L** for graphics [from lacie website]

---

### Post by reiki on 2008-01-27
And Inkscape can help you make nice lightscribe labels AND it can do do curved text pretty easily. I made a template for myself. It should show up as an attachment here. When you install Inkscape (it's in the repositories) you should have a directory called .inkscape inside your home directory. 
Go into the .inkscape directory and create a new directory called templates (if it does not already exist)
Put the attached file into the templates directory you just created.
Restart Inkscape
Choose File -> New and "A_Lightscribe_Disk" should be right at the top of the choices.

If you want to make if globally available you can instead put it into the /usr/share/inkscape/templates directory and it will show up in the list of templates available.... somewhere... not sure how Inkscape orders that template list.

Brief instructions are in a layer of the template.

The results will be the correct size for 4L-gui.

---

