---
title: "Joomla Installation"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by steedhappens on 2009-07-21
Hi People, I'm having trouble with my Joomla Installation. My setup files are in Home/Steed/Steedhappens. How do I point my browser to this folder?

---

### Post by az on 2009-07-21
> **steedhappens said:**
> Hi People, I'm having trouble with my Joomla Installation. My setup files are in Home/Steed/Steedhappens. How do I point my browser to this folder?

Change the DocumentRoot in /etc/apache2/sites-enabled/default

Then restart apache2 to make the changes take effect.

---

### Post by steedhappens on 2009-07-22
:confused: Thanks AZ, I tried that but I still won't get the Joomla Installation page as described in their manual. What am I not doing right?

---

### Post by az on 2009-07-22
> **steedhappens said:**
> :confused: Thanks AZ, I tried that but I still won't get the Joomla Installation page as described in their manual. What am I not doing right?

What do you see?  Do you have the rest of the LAMP stack installed?

---

