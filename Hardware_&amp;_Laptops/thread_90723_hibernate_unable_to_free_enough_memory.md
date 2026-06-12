---
title: "hibernate: unable to free enough memory"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by Davidov on 2005-11-15
Hello.
I have samsung p28 laptop. When I am trying to do hibernate right after system startup it fails and I get
```
suspend: Unable to free enough memory
```.
But if I do it for second (third, etc.) time it works. 
Anyway my swap partition size is about 500Mb but only ~200 is used (~100 in memory ~100 in swap). Is that really a memory issue?

---

### Post by ispiked on 2005-11-15
How much physical memory do you actually have? I'm pretty sure your swap partition would need to be at least that big for hibernate to work.

---

### Post by Davidov on 2005-11-15
[QUOTE=ispiked]How much physical memory do you actually have? I'm pretty sure your swap partition would need to be at least that big for hibernate to work.[/QUOTE]
I have 256Mb of physical memory and 512Mb of swap.

---

### Post by az on 2005-11-15
Can you look in bugzilla to see if you can find a similar bug?  If there is not one, can you open one about this and then follow up on it?

bugzilla.ubuntu.com

(Nevermind the self-signed certificate)

Also, would you please join the Laptop Testing Team?
[https://wiki.ubuntu.com/LaptopTesting?highlight=%28laptop%29%7C%28testing%29](https://wiki.ubuntu.com/LaptopTesting?highlight=%28laptop%29%7C%28testing%29)
Can you add your model to the page?
[https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=laptop+testing&titlesearch=Titles](https://wiki.ubuntu.com/FrontPage?action=fullsearch&context=180&value=laptop+testing&titlesearch=Titles)

---

