---
title: "What gtk engine do I need for this?"
date: 2008-11-20
forum: General Help
---

### Post by Oplix on 2008-11-20
I'm almost certain the reason this theme doesn't look proper is cause I lack the proper engine (that's what it's telling me).

[http://www.gnome-look.org/content/show.php/TechniX?content=79463]("http://www.gnome-look.org/content/show.php/TechniX?content=79463")

That's the theme. I have it installed, except that the taskbars and dropdown menus aren't transparent and show as solid colours with a couple lines going through them.

I've looked up gtk engines and I have murrine, all the ones that come with ubuntu 8.10, and I might have missed one or two, but yeah. I'm sure someone here will know what I'll need to display this properly.

---

### Post by renzokuken on 2008-11-20
make sure you are installing gtk**2**-engines and not the older gtk-engines

all the available engines in the repos are listed here [http://packages.ubuntu.com/search?keywords=gtk2-engines&searchon=names&suite=intrepid&section=all](http://packages.ubuntu.com/search?keywords=gtk2-engines&searchon=names&suite=intrepid&section=all)

you could always just install the lot, but might now be an engine problem, does the theme have a readme that details which engine is required?

---

### Post by Oplix on 2008-11-20
Not that I'm able to find anywhere, no. :confused:

I guess I could try just installing all the engines... Thanks for the link.

---

### Post by binbash on 2008-11-20
The engines are : 

gtk2-engines-clearlooks

gtk2-engines-mist

---

### Post by Oplix on 2008-11-20
As I said, I have mist. I can't find the clearlooks engine though.

When I search it in the synaptic package manager the closest I get is the gtk2-engines package which says it includes clearlooks...

However the GTK theme still wont display properly.

---

