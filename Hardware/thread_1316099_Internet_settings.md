---
title: "Internet settings"
date: 2009-11-05
forum: Hardware
---

### Post by 4Wheeler on 2009-11-05
I am new to ubuntu 9.04 and am having some annoying issues with Firefox 3.5.3.  On many of the websites that I visit regularly, the text is squished together and many of the words are layered on top of each other, making it difficult to read.  Is there a setting within Firefox that I am missing or something that I need to add within the package manager?  Any help would be appreciated.  Thank you.

---

### Post by bribera on 2009-11-05
You likely need to install the msttcorefonts package. Many websites are designed to display fonts that are packaged with Windows but not Linux; this package makes things look much better.

Try this:

```
sudo apt-get install msttcorefonts
sudo fc-cache -fv
```

---

### Post by 4Wheeler on 2009-11-05
I installed the msttcorefonts package and nothing changed.  The same websites are still having issues.  It is really strange - words overlap on top of each other and I cannot read some sentences on the sites.  Maybe something else might work?

---

### Post by darshana on 2009-11-06
Can you downgrade your Firefox to some older version like Firefox 3.0.13. You can use Synaptic Pacakage Manager

---

### Post by bribera on 2009-11-06
Are you perhaps just zoomed in? Try hitting Ctrl + 0 (that's a Zero, not an Oh) to reset your FF zoom level.

---

### Post by freackout on 2009-11-07
> **bribera said:**
> You likely need to install the msttcorefonts package. Many websites are designed to display fonts that are packaged with Windows but not Linux; this package makes things look much better.

Try this:

```
sudo apt-get install msttcorefonts
sudo fc-cache -fv
```

may be 
sudo apt-get install ttf-liberation 
not 100% sure but try it plz

---

