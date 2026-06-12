---
title: "Undo sed commands"
date: 2008-07-27
forum: General Help
---

### Post by intosamadhi on 2008-07-27
How do I undo the following code:

sudo ln -s /usr/lib32 /usr/l32
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/lib/usr\/l32/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8
sudo ln -s /usr/lib32 /usr/l3232

I know I can just rm the link but not sure what to do about the sed lines

---

### Post by spiderbatdad on 2008-07-27
sudo sed -i -e 's/usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders/g' /usr\/lib/usr\/l32
sudo sed -i -e 's/usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8/g' /usr\/lib/usr\/l32 

just a guess!

---

### Post by Azguz Bloodfist on 2008-07-27
> **spiderbatdad said:**
> sudo sed -i -e 's/usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders/g' /usr\/lib/usr\/l32
sudo sed -i -e 's/usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8/g' /usr\/lib/usr\/l32 


That's completely wrong!

You want to type
sudo sed -i -e 's/usr\/l32/usr\/lib/g' /usr/lib32/gtk-2.0/2.10.0/loader-files.d/libgtk2.0-0.loaders
sudo sed -i -e 's/usr\/l32/usr\/lib/g' /usr/lib32/libgdk_pixbuf-2.0.so.0.1200.8w

However if either of the input files originally contained /usr/l32 then they will also be changed to /usr/lib. I guess that is unlikely, but it may be impossible to undo a sed substitution depending on the contents of the file.

---

