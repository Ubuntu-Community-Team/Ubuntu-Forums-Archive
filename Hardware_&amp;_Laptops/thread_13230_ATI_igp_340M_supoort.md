---
title: "ATI igp 340M supoort"
date: 2005-01-29
forum: Hardware &amp; Laptops
---

### Post by I_NEED_HELP on 2005-01-29
Does anyone know if the igp 340 m is actually supported by ubuntu or i suppose more likely xfree86 i cant find anything to actually tell me yes or no.  I think it is not supported by xfree but is supported by x.org so if it doesnt work now will it work in hoary hedgehHow can i get the tv out to work?

---

### Post by knappen on 2005-01-31
My IGP 320M works perfectly.

Not what you wanted to hear but anyway :-)

---

### Post by ph00dz on 2005-02-01
I also have a 320M which works perfectly... it throws some kind of "not fully supported" warning during boot, but seems to have been configured just fine. As if by magic.

I had more trouble with the power stuff than the graphics card.

---

### Post by knappen on 2005-02-02
I get the same "not fully supported" but it works fine.

---

### Post by Arktis on 2005-02-02
The issue with the igp 320/330/340 M series is that 3d acceleration isn't supported yet.  Other than that, they work great.  I've got one in my presario which runs faster under xorg than it did under xfree86, but it's still a bummer that I can't run awesome games like bzflag without having to drop all the settings to their lowest and even then still get sluggish performance.

We just gotta wait until they update it for full support.  But yeah, it will work under xfree86 and xorg.

---

### Post by knappen on 2005-02-02
Ah, so it is just the 3D thats not supported.

Havent tried any of the 3d games  yet, good to know. Thanks!

---

### Post by Arktis on 2005-02-03
[http://www.theinquirer.net/?article=21014]("http://www.theinquirer.net/?article=21014")  :D
  
 As you can se from reading the article, 3.0 beta has support for the IGP cards, with 3d acceleration. I'm going to give it a try.
 
 **Edit:** The dang thing broke my system.  I can't get into my desktop now and I can't find the backup config it said it made during the setup.  I'm using a 345 M like the guy in the article.  Grr.  Hope someone else has better luck.  Make a backup of your xorg config or your XFree86 config before you try this.

---

### Post by knappen on 2005-02-03
Ah thats too bad.

I dont think I will give it a go yet :-)

---

