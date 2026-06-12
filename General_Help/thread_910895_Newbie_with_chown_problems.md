---
title: "Newbie with chown problems"
date: 2008-09-05
forum: General Help
---

### Post by awatoobi on 2008-09-05
In a fit to delete a few folders I change ownership of everthing from root to my user. 

$ sudo chown dogfood /.

I get a "operation not permitted" warning when I try to change the ownership back to root. Am I screwed or can is there a way to change the ownership back?

Any help would be gratefully recieved.
-Chris

---

### Post by aloshbennett on 2008-09-05
Good thing you didnt do it recursively.

Try
> chown root /

and 
> sudo chown root /
if the first one fails

---

### Post by bigbrovar on 2008-09-05
> Good thing you didnt do it recursively.

Try
Quote:
chown root /
and
Quote:
sudo chown root /
if the first one fails 

if that works for u ..u should remember not to use chown lightly especially when deaaling with the root (/) .. and u dont have to change ownership of a file/folder in other to remove it .. one easy way is to run ```
gksu nautilus
``` in terminal .. this would open nautilus in admin mode and allow u to delete stuffs are root .. u can also install a package from synaptic called **nautilus-gksu**  which would allow u to right click on a folder and choose open as admin allowing you to open the folder has root .. hope that helps .. sorry for my English ..

Nautilus is the default file manager for Ubuntu

---

