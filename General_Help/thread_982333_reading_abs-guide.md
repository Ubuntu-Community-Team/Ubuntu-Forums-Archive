---
title: "reading abs-guide"
date: 2008-11-14
forum: General Help
---

### Post by bluesguy@xmission.com on 2008-11-14
Hi,
I downloaded a package via synaptic called'abs-guide' which said in the description it was a tutorial on Advanced Bash-Scripting Guide.

I cannot find it to start the tutorial. I have searched everywhere I can think of. synaptic indicates that I have installed it.
Where is it?
How do I access it?

Thanks,

---

### Post by geirha on 2008-11-14
Right click the package in synaptic and select properties, then look at the installed files tab to see where it installed it. In the terminal you can get the same list with ```
dpkg -L abs-guide
```

---

### Post by Fixman on 2008-11-14
Have you tried looking into

```
 /usr/share/doc/abs-guide 
```

---

### Post by bluesguy@xmission.com on 2008-11-14
Thanks!, the dpkg -L abs-guide gave a big list of files and where they were installed. I copied the line "/usr/share/doc/abs-guide/html/index.html" and pasted it into firefox browser and I can now read it offline too.

---

### Post by TeXtonyx on 2008-11-14
> **bluesguy@xmission.com said:**
> Hi,
I downloaded a package via synaptic called'abs-guide' which said in the description it was a tutorial on Advanced Bash-Scripting Guide.

I cannot find it to start the tutorial. I have searched everywhere I can think of. synaptic indicates that I have installed it.
Where is it?
How do I access it?

Thanks,

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

This website contains quite a few good resources and abs-guide
is listed first. I like the .pdf format but with Firefox for
instance, you can "save page as" and know where it winds up,
after loading this option: HTML  (read online, single file, 2.1M)

---

